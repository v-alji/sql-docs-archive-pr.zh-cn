---
title: " (SQLXMLOLEDB 提供程序) 执行 XPath 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 667bc8dfd95c37c0a10c0bc68f3007e7d04533e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689814"
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="4dad5-102">执行 XPath 查询（SQLXMLOLEDB 访问接口）</span><span class="sxs-lookup"><span data-stu-id="4dad5-102">Executing XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="4dad5-103">该示例说明以下特定于 SQLXMLOLEDB 访问接口的属性的用法：</span><span class="sxs-lookup"><span data-stu-id="4dad5-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   `ClientSideXML`  
  
-   `Base Path`  
  
-   `Mapping Schema`  
  
 <span data-ttu-id="4dad5-104">在该示例 ADO 应用程序中，根据 XSD 映射架构 (MySchema.xml) 指定了一个 XPath 查询 (root)。</span><span class="sxs-lookup"><span data-stu-id="4dad5-104">In this sample ADO application, an XPath query (root) is specified against an XSD mapping schema (MySchema.xml).</span></span> <span data-ttu-id="4dad5-105">架构包含一个元素，该 **\<Contacts>** 元素具有**ContactID**、 **FirstName**和**LastName**属性。</span><span class="sxs-lookup"><span data-stu-id="4dad5-105">The schema has a **\<Contacts>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span> <span data-ttu-id="4dad5-106">在此架构中，发生默认映射：元素名称映射到同名的表，并且简单类型的属性映射到同名的列。</span><span class="sxs-lookup"><span data-stu-id="4dad5-106">In the schema, default mapping takes place: an element name maps to the table with the same name, and attributes of simple type map to the columns with the same names.</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="4dad5-107">"映射架构" 属性提供了用于执行 XPath 查询的映射架构。</span><span class="sxs-lookup"><span data-stu-id="4dad5-107">The Mapping Schema property provides the mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="4dad5-108">映射架构可以是 XSD 或 XDR 架构。</span><span class="sxs-lookup"><span data-stu-id="4dad5-108">The mapping schema can be an XSD or XDR schema.</span></span> <span data-ttu-id="4dad5-109">"基路径" 属性提供映射架构的文件路径。</span><span class="sxs-lookup"><span data-stu-id="4dad5-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="4dad5-110">ClientSideXML 属性设置为 True。</span><span class="sxs-lookup"><span data-stu-id="4dad5-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="4dad5-111">因此，在客户端上生成 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="4dad5-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="4dad5-112">在应用程序中，可直接指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="4dad5-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="4dad5-113">因此，必须包括 XPath 方言 {ec2a4293-e898-11d2-b1b7-00c04f680c56}。</span><span class="sxs-lookup"><span data-stu-id="4dad5-113">Therefore, the XPath dialect {ec2a4293-e898-11d2-b1b7-00c04f680c56} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dad5-114">在该代码中，必须在连接字符串中提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="4dad5-114">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="4dad5-115">而且，该示例指定对于需要安装其他网络客户端软件的数据访问接口使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11)。</span><span class="sxs-lookup"><span data-stu-id="4dad5-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="4dad5-116">有关详细信息，请参阅[SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="4dad5-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
