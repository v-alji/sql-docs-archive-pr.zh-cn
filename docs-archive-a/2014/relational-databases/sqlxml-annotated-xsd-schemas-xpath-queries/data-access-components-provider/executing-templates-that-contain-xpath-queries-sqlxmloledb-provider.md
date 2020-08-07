---
title: 正在执行包含 XPath 查询的模板 (SQLXMLOLEDB 提供程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing template files
- Base Path property
- templates [SQLXML], XPath queries
- XPath queries [SQLXML], templates
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
- XML templates [SQLXML]
ms.assetid: 7368c188-607e-459e-8254-8f23352dfa01
author: rothja
ms.author: jroth
ms.openlocfilehash: b3d31c95fe5d4fb1b7dc9a8d039a56b41cdd7349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689813"
---
# <a name="executing-templates-that-contain-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="327ac-102">执行包含 XPath 查询的模板（SQLXMLOLEDB 访问接口）</span><span class="sxs-lookup"><span data-stu-id="327ac-102">Executing Templates That Contain XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="327ac-103">此示例显示如何使用以下 SQLXMLOLEDB 访问接口特定的属性：</span><span class="sxs-lookup"><span data-stu-id="327ac-103">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="327ac-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="327ac-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="327ac-105">基路径</span><span class="sxs-lookup"><span data-stu-id="327ac-105">Base Path</span></span>  
  
-   <span data-ttu-id="327ac-106">映射架构</span><span class="sxs-lookup"><span data-stu-id="327ac-106">Mapping Schema</span></span>  
  
 <span data-ttu-id="327ac-107">在此示例 ADO 应用程序中， (根) 包含 XPath 查询的 XML 模板是)  ( 根据[执行 Xpath 查询 &#40;SQLXMLOLEDB Provider&#41;](executing-xpath-queries-sqlxmloledb-provider.md)中所述的。</span><span class="sxs-lookup"><span data-stu-id="327ac-107">In this sample ADO application, an XML template that consists of an XPath query (root) is specified against the XSD mapping schema (MySchema.xml) that is described in [Executing XPath Queries &#40;SQLXMLOLEDB Provider&#41;](executing-xpath-queries-sqlxmloledb-provider.md).</span></span>  
  
 <span data-ttu-id="327ac-108">"映射架构" 属性提供了用于执行 XPath 查询的 XSD 映射架构。</span><span class="sxs-lookup"><span data-stu-id="327ac-108">The Mapping Schema property provides the XSD mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="327ac-109">"基路径" 属性提供映射架构的文件路径。</span><span class="sxs-lookup"><span data-stu-id="327ac-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="327ac-110">ClientSideXML 属性设置为 True。</span><span class="sxs-lookup"><span data-stu-id="327ac-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="327ac-111">因此，在客户端上生成 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="327ac-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="327ac-112">在应用程序中，可直接指定 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="327ac-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="327ac-113">因此，必须包括方言 {5d531cb2-e6ed-11d2-b252-00c04f681b71}。</span><span class="sxs-lookup"><span data-stu-id="327ac-113">Therefore, the dialect {5d531cb2-e6ed-11d2-b252-00c04f681b71} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="327ac-114">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="327ac-114">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="327ac-115">而且，该示例指定对于需要安装其他网络客户端软件的数据访问接口使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11)。</span><span class="sxs-lookup"><span data-stu-id="327ac-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="327ac-116">有关详细信息，请参阅[SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="327ac-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub Main()  
  
   Dim oTestStream As New ADODB.Stream  
   Dim oTestConnection As New ADODB.Connection  
   Dim oTestCommand As New ADODB.Command  
  
   oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
  
   oTestCommand.ActiveConnection = oTestConnection  
   oTestCommand.Properties("ClientSideXML") = "False"  
  
   oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:xpath-query mapping-schema='mySchema.xml' > " & _  
        "   root " & _  
        "   </sql:xpath-query> " & _  
        " </ROOT> "  
   oTestStream.Open  
   ' You need the dialect if you are executing a template.  
   oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
   oTestCommand.Properties("Output Stream").Value = oTestStream  
   oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\TemplateWithXPath\"  
   oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
   oTestCommand.Properties("Output Encoding") = "utf-8"  
   oTestCommand.Execute , , adExecuteStream  
   oTestStream.Position = 0  
   oTestStream.Charset = "utf-8"  
   Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
  
Sub Form_Load()  
   Main  
End Sub  
```  
  
 <span data-ttu-id="327ac-117">以下是架构：</span><span class="sxs-lookup"><span data-stu-id="327ac-117">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contact'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  
  <xsd:element name='Contact' sql:relation='Person.Contact'>  
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
  
