---
title: 将 ADO 用于 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: rothja
ms.author: jroth
ms.openlocfilehash: ccd14432aa3541572467a4c651c1f48b1ac957f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692350"
---
# <a name="using-ado-with-sql-server-native-client"></a><span data-ttu-id="0f0bc-102">将 ADO 用于 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="0f0bc-102">Using ADO with SQL Server Native Client</span></span>
  <span data-ttu-id="0f0bc-103">为了充分利用中引入的新功能 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] （例如多个活动结果集） (MARS) 、查询通知、用户定义类型 (udt) 或新的**xml**数据类型，使用 ActiveX 数据对象 (ADO) 的现有应用程序应使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序作为其数据访问接口。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-103">In order to take advantage of new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] such as multiple active result sets (MARS), query notifications, user-defined types (UDTs), or the new **xml** data type, existing applications that use ActiveX Data Objects (ADO) should use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider as their data access provider.</span></span>  
  
 <span data-ttu-id="0f0bc-104">如果不需要使用在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的任何新功能，则不需要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口；您可以继续使用当前数据访问接口（通常是 SQLOLEDB）。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-104">If you do not need to use any of the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], there is no need to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider; you can continue using your current data access provider, which is typically SQLOLEDB.</span></span> <span data-ttu-id="0f0bc-105">如果要增强现有应用程序的功能，并且需要使用在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的新功能，则应当使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-105">If you are enhancing an existing application and you need to use the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you should use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f0bc-106">如果要开发新的应用程序，则建议考虑使用用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 ADO.NET 和 .NET Framework 数据访问接口，而不是使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，以访问最新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本的所有新功能。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-106">If you are developing a new application, it is recommended that you consider using ADO.NET and the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instead of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access all the new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0f0bc-107">有关用于 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的详细信息，请参阅针对 ADO.NET 的 .NET Framework SDK 文档。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-107">For more information about the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see the .NET Framework SDK documentation for ADO.NET.</span></span>  
  
 <span data-ttu-id="0f0bc-108">为了使 ADO 能够使用最新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本的新功能，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口已进行了某些增强，这些增强扩展了 OLE DB 的核心功能。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-108">To enable ADO to use new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], some enhancements have been made to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider which extends the core features of OLE DB.</span></span> <span data-ttu-id="0f0bc-109">借助这些增强功能，ADO 应用程序可使用更新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能，还可使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的两个数据类型（xml 和 udt）   。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-109">These enhancements allow ADO applications to use newer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features and to consume two data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** and **udt**.</span></span> <span data-ttu-id="0f0bc-110">通过这些增强功能，还可探索对 varchar、nvarchar 和 varbinary 数据类型的强化    。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-110">These enhancements also exploit enhancements to the **varchar**, **nvarchar**, and **varbinary** data types.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="0f0bc-111">Native Client 将 SSPROP_INIT_DATATYPECOMPATIBILITY 初始化属性添加到 DBPROPSET_SQLSERVERDBINIT 属性集以供 ADO 应用程序使用，以便以与 ADO 兼容的方式公开新数据类型。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-111">Native Client adds the SSPROP_INIT_DATATYPECOMPATIBILITY initialization property to the DBPROPSET_SQLSERVERDBINIT property set for use by ADO applications so that the new data types are exposed in a way compatible with ADO.</span></span> <span data-ttu-id="0f0bc-112">此外， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序还定义了一个名为的新连接字符串关键字，该关键字 `DataTypeCompatibility` 是在连接字符串中设置的。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-112">In addition, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also defines a new connection string keyword named `DataTypeCompatibility` that is set in the connection string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f0bc-113">现有 ADO 应用程序可以使用 SQLOLEDB 访问接口来访问和更新 XML、UDT 以及大型值文本和二进制字段值。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-113">Existing ADO applications can access and update XML, UDT, and large value text and binary field values using the SQLOLEDB provider.</span></span> <span data-ttu-id="0f0bc-114">新的更大型的 varchar(max)、nvarchar(max) 和 varbinary(max) 数据类型分别作为 ADO 类型 adLongVarChar、adLongVarWChar 和 adLongVarBinary 返回       。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-114">The new larger **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types are returned as the ADO types **adLongVarChar**, **adLongVarWChar** and **adLongVarBinary** respectively.</span></span> <span data-ttu-id="0f0bc-115">XML 列作为 adLongVarChar 返回，而 UDT 列作为 adVarBinary 返回   。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-115">XML columns are returned as **adLongVarChar**, and UDT columns are returned as **adVarBinary**.</span></span> <span data-ttu-id="0f0bc-116">但是，如果使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口 (SQLNCLI11) 而不是 SQLOLEDB，则需要确保将 `DataTypeCompatibility` 关键字设置为“80”，以便新数据类型能正确映射到 ADO 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-116">However, if you use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider (SQLNCLI11) instead of SQLOLEDB, you need to make sure to set the `DataTypeCompatibility` keyword to "80" so that the new data types will map correctly to the ADO data types.</span></span>  
  
## <a name="enabling-sql-server-native-client-from-ado"></a><span data-ttu-id="0f0bc-117">从 ADO 启用 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="0f0bc-117">Enabling SQL Server Native Client from ADO</span></span>  
 <span data-ttu-id="0f0bc-118">若要启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，ADO 应用程序需要在其连接字符串中实现以下关键字：</span><span class="sxs-lookup"><span data-stu-id="0f0bc-118">To enable the usage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ADO applications will need to implement the following keywords in their connection strings:</span></span>  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 <span data-ttu-id="0f0bc-119">有关 Native Client 中支持的 ADO 连接字符串关键字的详细信息 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，请参阅将[连接字符串关键字用于 SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-119">For more information about the ADO connections string keywords supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="0f0bc-120">下面是一个示例，用于建立完全启用的 ADO 连接字符串，以便与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 一起使用，包括启用 MARS 功能：</span><span class="sxs-lookup"><span data-stu-id="0f0bc-120">The following is an example of establishing an ADO connection string that is fully enabled to work with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, including the enabling of the MARS feature:</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a><span data-ttu-id="0f0bc-121">示例</span><span class="sxs-lookup"><span data-stu-id="0f0bc-121">Examples</span></span>  
 <span data-ttu-id="0f0bc-122">以下各节提供了有关如何将 ADO 与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序一起使用的示例。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-122">The following sections provide examples of how you can use ADO with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="retrieving-xml-column-data"></a><span data-ttu-id="0f0bc-123">检索 XML 列数据</span><span class="sxs-lookup"><span data-stu-id="0f0bc-123">Retrieving XML Column Data</span></span>  
 <span data-ttu-id="0f0bc-124">本例中，使用记录集从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AdventureWorks  示例数据库中的 XML 列检索并显示数据。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-124">In this example, a recordset is used to retrieve and display the data from an XML column in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** sample database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  
  
' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  
  
con.Close  
Set con = Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="0f0bc-125">XML 列不支持记录集筛选。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-125">Recordset filtering is not supported with XML columns.</span></span> <span data-ttu-id="0f0bc-126">如果使用，将返回错误。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-126">If used, an error will be returned.</span></span>  
  
### <a name="retrieving-udt-column-data"></a><span data-ttu-id="0f0bc-127">检索 UDT 列数据</span><span class="sxs-lookup"><span data-stu-id="0f0bc-127">Retrieving UDT Column Data</span></span>  
 <span data-ttu-id="0f0bc-128">在该示例中，使用 Command 对象执行返回 UDT 的 SQL 查询，并更新 UDT 数据，然后将新数据插入数据库中  。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-128">In this example, a **Command** object is used to execute a SQL query that returns a UDT, the UDT data is updated, and then the new data is inserted back into the database.</span></span> <span data-ttu-id="0f0bc-129">该示例假定已在数据库中注册 Point UDT  。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-129">This example assumes that the **Point** UDT has already been registered in the database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  
  
' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  
  
' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  
  
con.Close  
Set con = Nothing  
```  
  
### <a name="enabling-and-using-mars"></a><span data-ttu-id="0f0bc-130">启用和使用 MARS</span><span class="sxs-lookup"><span data-stu-id="0f0bc-130">Enabling and Using MARS</span></span>  
 <span data-ttu-id="0f0bc-131">在此示例中，将构造连接字符串，以便通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序启用 MARS，然后创建两个记录集对象以使用同一连接执行。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-131">In this example, the connection string is constructed to enable MARS through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and then two recordset objects are created to execute using the same connection.</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
  
Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  
  
Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  
  
con.Close  
Set con = Nothing  
```  
  
 <span data-ttu-id="0f0bc-132">在以前的 OLE DB 访问接口版本中，该代码会导致在第二次执行时创建隐式的连接，因为每个单独的连接只能打开一个活动的结果集。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-132">In prior versions of the OLE DB provider, this code would cause an implicit connection to be created on the second execution because only one active set of results could be opened per a single connection.</span></span> <span data-ttu-id="0f0bc-133">由于该隐式连接未加入 OLE DB 连接池，因此这会导致额外的开销。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-133">Because the implicit connection was not pooled in the OLE DB connection pool this would cause additional overhead.</span></span> <span data-ttu-id="0f0bc-134">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序公开的 MARS 功能时，会在一个连接上获得多个活动结果。</span><span class="sxs-lookup"><span data-stu-id="0f0bc-134">With the MARS feature exposed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you get multiple active results on the one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0bc-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f0bc-135">See Also</span></span>  
 [<span data-ttu-id="0f0bc-136">使用 SQL Server Native Client 生成应用程序</span><span class="sxs-lookup"><span data-stu-id="0f0bc-136">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
