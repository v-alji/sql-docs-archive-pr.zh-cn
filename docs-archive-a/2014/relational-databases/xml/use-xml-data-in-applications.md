---
title: 在应用程序中使用 XML 数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dd4f4d2ff3cd61bc33c632f499bfb8e8817f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682754"
---
# <a name="use-xml-data-in-applications"></a><span data-ttu-id="6a131-102">使用 XML 数据应用程序</span><span class="sxs-lookup"><span data-stu-id="6a131-102">Use XML Data in Applications</span></span>
  <span data-ttu-id="6a131-103">本主题介绍在应用程序中使用 `xml` 数据类型时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="6a131-103">This topic describes the options that are available to you for working with the `xml` data type in your application.</span></span> <span data-ttu-id="6a131-104">本主题包括有关下列操作的信息：</span><span class="sxs-lookup"><span data-stu-id="6a131-104">The topic includes information about the following:</span></span>  
  
-   <span data-ttu-id="6a131-105">使用 ADO 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 处理 `xml` 类型列中的 XML</span><span class="sxs-lookup"><span data-stu-id="6a131-105">Handling XML from an `xml` type column by using ADO and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="6a131-106">使用 ADO.NET 处理 `xml` 类型列中的 XML</span><span class="sxs-lookup"><span data-stu-id="6a131-106">Handling XML from an `xml` type column by using ADO.NET</span></span>  
  
-   <span data-ttu-id="6a131-107">使用 ADO.NET 处理参数中的 `xml` 类型</span><span class="sxs-lookup"><span data-stu-id="6a131-107">Handling `xml` type in parameters by using ADO.NET</span></span>  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a><span data-ttu-id="6a131-108">使用 ADO 和 SQL Server Native Client 处理 xml 类型列中的 XML</span><span class="sxs-lookup"><span data-stu-id="6a131-108">Handling XML from an xml Type Column by Using ADO and SQL Server Native Client</span></span>  
 <span data-ttu-id="6a131-109">若要使用 MDAC 组件访问 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中引入的类型和功能，必须在 ADO 连接字符串中设置 DataTypeCompatibility 初始化属性。</span><span class="sxs-lookup"><span data-stu-id="6a131-109">To use MDAC components to access the types and features that were introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must set the DataTypeCompatibility initialization property in the ADO connection string.</span></span>  
  
 <span data-ttu-id="6a131-110">例如，下面的 Visual Basic Scripting Edition (VBScript) 示例显示了在 `Demographics` 示例数据库的 `Sales.Store` 表中查询 `xml` 数据类型列 `AdventureWorks2012` 的结果。</span><span class="sxs-lookup"><span data-stu-id="6a131-110">For example, the following Visual Basic Scripting Edition (VBScript) sample shows the results of querying an `xml` data type column, `Demographics`, in the `Sales.Store` table of the `AdventureWorks2012` sample database.</span></span> <span data-ttu-id="6a131-111">具体来讲，查询将为 `CustomerID` 等于 `3`的行查找此列的实例值。</span><span class="sxs-lookup"><span data-stu-id="6a131-111">Specifically, the query looks for the instance value of this column for the row where the `CustomerID` is equal to `3`.</span></span>  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 <span data-ttu-id="6a131-112">此示例显示了如何设置数据类型兼容性属性。</span><span class="sxs-lookup"><span data-stu-id="6a131-112">This example shows how to set the data type compatibility property.</span></span> <span data-ttu-id="6a131-113">默认情况下，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 时它设置为 0。</span><span class="sxs-lookup"><span data-stu-id="6a131-113">By default, this is set to 0 when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="6a131-114">如果将该值设置为 80，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 访问接口将使 `xml` 和用户定义类型列显示为 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="6a131-114">If you set the value to 80, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider will make `xml` and user-defined type columns appear as [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] data types.</span></span> <span data-ttu-id="6a131-115">结果将分别是 DBTYPE_WSTR 和 DBTYPE_BYTES。</span><span class="sxs-lookup"><span data-stu-id="6a131-115">This would be DBTYPE_WSTR and DBTYPE_BYTES, respectively.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6a131-116">Native Client，并且连接字符串必须通过“`Provider=SQLNCLI11;...`”指定将它用作数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="6a131-116">Native Client must also be installed on the client computer and the connection string must specify it for use as the data provider with "`Provider=SQLNCLI11;...`".</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="6a131-117">测试此示例</span><span class="sxs-lookup"><span data-stu-id="6a131-117">To test this example</span></span>  
  
1.  <span data-ttu-id="6a131-118">验证客户端计算机上是否安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 以及是否有 MDAC 2.6.0 或更高版本可用。</span><span class="sxs-lookup"><span data-stu-id="6a131-118">Verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed and that MDAC 2.6.0or later is available on the client computer.</span></span>  
  
     <span data-ttu-id="6a131-119">有关详细信息，请参阅 [SQL Server Native Client 编程](../native-client/sql-server-native-client-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="6a131-119">For more information, see [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
2.  <span data-ttu-id="6a131-120">确定安装了 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="6a131-120">Verify that the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
     <span data-ttu-id="6a131-121">此示例需要 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="6a131-121">This example requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
3.  <span data-ttu-id="6a131-122">将本主题前面显示的代码复制并粘贴到文本编辑器或代码编辑器中。</span><span class="sxs-lookup"><span data-stu-id="6a131-122">Copy the code shown previously in this topic and paste the code into your text or code editor.</span></span> <span data-ttu-id="6a131-123">将文件另存为 HandlingXmlDataType.vbs。</span><span class="sxs-lookup"><span data-stu-id="6a131-123">Save the file as HandlingXmlDataType.vbs.</span></span>  
  
4.  <span data-ttu-id="6a131-124">根据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的需要修改脚本并保存更改。</span><span class="sxs-lookup"><span data-stu-id="6a131-124">Modify the script as required for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation and save your changes.</span></span>  
  
     <span data-ttu-id="6a131-125">例如，如果指定了 `MyServer` ，应将其替换为 `(local)` 或安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器的实际名称。</span><span class="sxs-lookup"><span data-stu-id="6a131-125">For example, where `MyServer` is specified, you should replace it with either `(local)` or the actual name of the server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
5.  <span data-ttu-id="6a131-126">运行 HandlingXmlDataType.vbs 并执行脚本。</span><span class="sxs-lookup"><span data-stu-id="6a131-126">Run HandlingXmlDataType.vbs and execute the script.</span></span>  
  
 <span data-ttu-id="6a131-127">结果应与以下示例输出相似：</span><span class="sxs-lookup"><span data-stu-id="6a131-127">The results should be similar to the following sample output:</span></span>  
  
```  
Row 1  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a><span data-ttu-id="6a131-128">使用 ADO.NET 处理 xml 类型列中的 XML</span><span class="sxs-lookup"><span data-stu-id="6a131-128">Handling XML from an xml Type Column by Using ADO.NET</span></span>  
 <span data-ttu-id="6a131-129">若要 `xml` 使用 ADO.NET 和来处理数据类型列中的 XML， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可以使用类的标准行为 `SqlCommand` 。</span><span class="sxs-lookup"><span data-stu-id="6a131-129">To handle XML from an `xml` data type column by using ADO.NET and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] you can use the standard behavior of the `SqlCommand` class.</span></span> <span data-ttu-id="6a131-130">例如，可以按照使用 `xml` 检索任何 SQL 列的相同方法检索 `SqlDataReader` 数据类型列及其值。但是，如果要将 `xml` 数据类型列的内容作为 XML 使用，必须先将这些内容指派给 `XmlReader` 类型。</span><span class="sxs-lookup"><span data-stu-id="6a131-130">For example, an `xml` data type column and its values can be retrieved in the same way any SQL column is retrieved by using a `SqlDataReader`.However, if you want to work with the contents of an `xml` data type column as XML, you will first have to assign the contents to an `XmlReader` type.</span></span>  
  
 <span data-ttu-id="6a131-131">有关详细信息和示例代码，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 文档中的“数据读取器中的 XML 列值”。</span><span class="sxs-lookup"><span data-stu-id="6a131-131">For more information and example code, see "XML Column Values in a Data Reader" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a><span data-ttu-id="6a131-132">使用 ADO.NET 处理参数中的 xml 类型列</span><span class="sxs-lookup"><span data-stu-id="6a131-132">Handling an xml Type Column in Parameters by Using ADO.NET</span></span>  
 <span data-ttu-id="6a131-133">若要处理 ADO.NET 和 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中作为参数传递的 xml 数据类型，可以将参数值作为 `SqlXml` 数据类型的实例来提供。</span><span class="sxs-lookup"><span data-stu-id="6a131-133">To handle an xml data type passed as a parameter in ADO.NET and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can supply the value as an instance of the `SqlXml` data type.</span></span> <span data-ttu-id="6a131-134">这里不涉及任何特殊的处理，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 `xml` 数据类型列可按照与其他列和数据类型（如 `string` 或 `integer`）相同的方式接受参数值。</span><span class="sxs-lookup"><span data-stu-id="6a131-134">No special handling is involved, because `xml` data type columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can accept parameter values in the same way as other columns and data types, such as `string` or `integer`.</span></span>  
  
 <span data-ttu-id="6a131-135">有关详细信息和示例代码，请参阅 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 文档中的“作为命令参数的 XML 值”。</span><span class="sxs-lookup"><span data-stu-id="6a131-135">For more information and example code, see "XML Values as Command Parameters" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a131-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a131-136">See Also</span></span>  
 [<span data-ttu-id="6a131-137">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6a131-137">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
