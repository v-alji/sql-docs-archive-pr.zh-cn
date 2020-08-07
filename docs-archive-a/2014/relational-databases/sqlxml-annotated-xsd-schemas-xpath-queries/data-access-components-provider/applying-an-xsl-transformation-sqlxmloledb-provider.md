---
title: " (SQLXMLOLEDB 提供程序) 应用 XSL 转换 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fbb427a95d9f2308bf65724758a4a1563b42575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587735"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a><span data-ttu-id="c5d7d-102">应用 XSL 转换（SQLXMLOLEDB 访问接口）</span><span class="sxs-lookup"><span data-stu-id="c5d7d-102">Applying an XSL Transformation (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="c5d7d-103">在此示例 ADO 应用程序中，将执行 SQL 查询并将 XSL 转换应用到结果。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-103">In this sample ADO application, an SQL query is executed, and an XSL transformation is applied to the result.</span></span> <span data-ttu-id="c5d7d-104">如果将 ClientSideXML 属性设置为 True，则会强制在客户端上处理行集。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-104">Setting the ClientSideXML property to True enforces the processing of the rowset on the client side.</span></span> <span data-ttu-id="c5d7d-105">将命令方言设置为 {5d531cb2-e6ed-11d2-b252-00c04f681b71}，因为在模板中指定 SQL 查询且在执行模板时必须指定此方言。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-105">The command dialect is set to {5d531cb2-e6ed-11d2-b252-00c04f681b71}, because the SQL query is specified in a template and this dialect must be specified when executing a template.</span></span> <span data-ttu-id="c5d7d-106">Xsl 属性指定用于应用转换的 XSL 文件。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-106">The xsl property specifies the XSL file to use to apply the transformation.</span></span> <span data-ttu-id="c5d7d-107">"基路径" 属性的值用于搜索 XSL 文件。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-107">The value of Base Path property is used to search for the XSL file.</span></span> <span data-ttu-id="c5d7d-108">如果指定 xsl 属性的值中的路径，则该路径相对于在 "基路径" 属性中指定的路径。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-108">If you specify a path in the value of the xsl property, the path is relative to the path that is specified in the Base Path property.</span></span>  
  
 <span data-ttu-id="c5d7d-109">此示例显示如何使用以下 SQLXMLOLEDB 访问接口特定的属性：</span><span class="sxs-lookup"><span data-stu-id="c5d7d-109">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="c5d7d-110">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="c5d7d-110">ClientSideXML</span></span>  
  
-   <span data-ttu-id="c5d7d-111">xsl</span><span class="sxs-lookup"><span data-stu-id="c5d7d-111">xsl</span></span>  
  
 <span data-ttu-id="c5d7d-112">在此客户端 ADO 示例应用程序中，在服务器上执行包含一个 SQL 查询的 XML 模板。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-112">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="c5d7d-113">由于 ClientSideXML 属性设置为 True，因此将不带 FOR XML 子句的 SELECT 语句发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-113">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="c5d7d-114">服务器执行该查询并将一个行集返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-114">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="c5d7d-115">客户端然后将 FOR XML 转换应用到该行集并生成 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-115">The client then applies the FOR XML transformation to the rowset and produces the XML document.</span></span>  
  
 <span data-ttu-id="c5d7d-116">在应用程序中指定 xsl 属性;因此，将 XSL 转换应用于在客户端生成的 XML 文档，并且结果是一个两列的表。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-116">The xsl property is specified in the application; therefore, the XSL transformation is applied to the XML document that is generated on the client, and the result is a two-column table.</span></span>  
  
 <span data-ttu-id="c5d7d-117">若要执行模板命令，必须指定 XML 模板方言-{5d531cb2-e6ed-11d2-b252-00c04f681b71}。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-117">To execute the template command, the XML template dialect - {5d531cb2-e6ed-11d2-b252-00c04f681b71} - must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5d7d-118">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-118">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="c5d7d-119">此示例还指定使用数据访问接口的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，这要求安装其他网络客户端软件。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-119">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="c5d7d-120">有关详细信息，请参阅[SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-120">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 <span data-ttu-id="c5d7d-121">紧接着是 XSL 模板。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-121">The XSL template follows.</span></span> <span data-ttu-id="c5d7d-122">应用此 XSL 模板后得到一个包含两列的表。</span><span class="sxs-lookup"><span data-stu-id="c5d7d-122">The result of applying this XSL template is a two-column table.</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
