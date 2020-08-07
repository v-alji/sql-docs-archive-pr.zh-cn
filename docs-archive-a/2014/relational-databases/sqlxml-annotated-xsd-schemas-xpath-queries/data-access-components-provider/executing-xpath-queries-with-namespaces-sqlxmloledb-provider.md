---
title: 通过命名空间 (SQLXMLOLEDB 提供程序) 执行 XPath 查询 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- namespaces property
- queries [SQLXML], SQLXMLOLEDB Provider
- XPath queries [SQLXML], namespaces
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- namespaces [SQLXML], XPath queries
ms.assetid: 024a4b7d-435d-47ba-9e80-2c2f640108f5
author: rothja
ms.author: jroth
ms.openlocfilehash: ff692b49a4c32c14655af3a9eb07071dc60ba2a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689809"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxmloledb-provider"></a><span data-ttu-id="2733c-102">执行带命名空间的 XPath 查询（SQLXMLOLEDB 访问接口）</span><span class="sxs-lookup"><span data-stu-id="2733c-102">Executing XPath Queries with Namespaces (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="2733c-103">XPath 查询可以包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="2733c-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="2733c-104">如果架构元素为限定命名空间（即，包含目标命名空间），则针对该架构的 XPath 查询必须指定该命名空间。</span><span class="sxs-lookup"><span data-stu-id="2733c-104">If the schema elements are namespace qualified (that is, if they include a target namespace), XPath queries against the schema must specify this namespace.</span></span>  
  
 <span data-ttu-id="2733c-105">由于 SQLXML 4.0 中不支持使用通配符 (\*)，因此必须使用命名空间前缀来指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="2733c-105">Because using the wildcard character (\*) is not supported in SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="2733c-106">若要解析此前缀，请使用 namespace 属性来指定命名空间绑定。</span><span class="sxs-lookup"><span data-stu-id="2733c-106">To resolve this prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="2733c-107">在下面的示例中，XPath 查询使用通配符指定命名空间 (\*) 和本地名称 ( # A3 和 namespace uri ( # A5 XPath 函数。</span><span class="sxs-lookup"><span data-stu-id="2733c-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="2733c-108">此 XPath 查询将返回其本地名称为 `Contact` 且其命名空间 URI 为 `urn:myschema:Contacts` 的所有元素。</span><span class="sxs-lookup"><span data-stu-id="2733c-108">This XPath query returns all the elements where the local name is `Contact` and the namespace URI is `urn:myschema:Contacts`.</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="2733c-109">在 SQLXML 4.0 中，必须用命名空间前缀来指定此 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="2733c-109">In SQLXML 4.0, this XPath query must be specified with a namespace prefix.</span></span> <span data-ttu-id="2733c-110">例如，`x:Contact`，其中 `x` 为命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="2733c-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="2733c-111">请看以下 XSD 架构：</span><span class="sxs-lookup"><span data-stu-id="2733c-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="2733c-112">由于此架构定义了目标命名空间，因此针对此架构的 XPath 查询（如“Employee”）必须包含该命名空间。</span><span class="sxs-lookup"><span data-stu-id="2733c-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against the schema must include the namespace.</span></span>  
  
 <span data-ttu-id="2733c-113">以下是一个 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 应用程序示例，针对前述 XSD 架构执行 XPath 查询 (x:Employee)。</span><span class="sxs-lookup"><span data-stu-id="2733c-113">This is a sample [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application that executes an XPath query (x:Employee) against the preceding XSD schema.</span></span> <span data-ttu-id="2733c-114">若要解析此前缀，使用 namespace 属性指定命名空间绑定。</span><span class="sxs-lookup"><span data-stu-id="2733c-114">To resolve the prefix, the namespace binding is specified by using the namespaces property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2733c-115">在该代码中，必须在连接字符串中提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="2733c-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="2733c-116">此外，本示例还指定使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) 作为数据访问接口，该访问接口需要安装其他网络客户端软件。</span><span class="sxs-lookup"><span data-stu-id="2733c-116">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="2733c-117">有关详细信息，请参阅[SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="2733c-117">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Private Sub Form_Load()  
    Dim con As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim stm As New ADODB.Stream  
    con.Open "provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
    Set cmd.ActiveConnection = con  
    stm.Open  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    cmd.Properties("Mapping schema") = "C:\DirectoryPath\con-ex.xml"  
    cmd.Properties("namespaces") = "xmlns:x='urn:myschema:Contacts'"  
    '  Debug.Print "Set Command Dialect to DBGUID_XPATH"  
    cmd.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
    cmd.CommandText = "x:Contact"  
    cmd.Execute , , adExecuteStream   
    stm.Position = 0  
    Debug.Print stm.ReadText(adReadAll)  
End Sub  
```  
  
### <a name="to-test-this-application"></a><span data-ttu-id="2733c-118">测试此应用程序</span><span class="sxs-lookup"><span data-stu-id="2733c-118">To test this application</span></span>  
  
1.  <span data-ttu-id="2733c-119">将示例 XSD 架构保存到文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2733c-119">Save the sample XSD schema in a folder.</span></span>  
  
2.  <span data-ttu-id="2733c-120">创建 Visual Basic 可执行项目，并将代码复制到其中。</span><span class="sxs-lookup"><span data-stu-id="2733c-120">Create a Visual Basic executable project, and copy the code into it.</span></span> <span data-ttu-id="2733c-121">根据需要更改指定的目录路径。</span><span class="sxs-lookup"><span data-stu-id="2733c-121">Change the specified directory path as appropriate.</span></span>  
  
3.  <span data-ttu-id="2733c-122">添加以下项目引用：</span><span class="sxs-lookup"><span data-stu-id="2733c-122">Add the following project reference:</span></span>  
  
    ```  
    "Microsoft ActiveX Data Objects 2.8 Library"  
    ```  
  
4.  <span data-ttu-id="2733c-123">执行应用程序。</span><span class="sxs-lookup"><span data-stu-id="2733c-123">Execute the application.</span></span>  
  
 <span data-ttu-id="2733c-124">下面是部分结果：</span><span class="sxs-lookup"><span data-stu-id="2733c-124">This is the partial result:</span></span>  
  
```  
<y0:Employee xmlns:y0="urn:myschema:Contacts"   
             LName="Achong" CID="1" FName="Gustavo"/>  
<y0:Employee xmlns:y0="urn:myschema:Employees"   
             LName="Abel" CID="2" FName="Catherine"/>  
```  
  
 <span data-ttu-id="2733c-125">在 XML 文档中生成的前缀是任意的，但都映射到同一个命名空间。</span><span class="sxs-lookup"><span data-stu-id="2733c-125">The prefixes that are generated in the XML document are arbitrary, but they map to the same namespace.</span></span>  
  
  
