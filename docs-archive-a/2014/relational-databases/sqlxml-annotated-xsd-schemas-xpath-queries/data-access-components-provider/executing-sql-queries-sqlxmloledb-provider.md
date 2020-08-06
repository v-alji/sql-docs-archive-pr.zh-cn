---
title: " (SQLXMLOLEDB 提供程序) 执行 SQL 查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e2cc87f90700e3b81a5a2ec3dd80f219a9b1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588448"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="d80d4-102">执行 SQL 查询（SQLXMLOLEDB 访问接口）</span><span class="sxs-lookup"><span data-stu-id="d80d4-102">Executing SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="d80d4-103">该示例说明以下特定于 SQLXMLOLEDB 访问接口的属性的用法：</span><span class="sxs-lookup"><span data-stu-id="d80d4-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="d80d4-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="d80d4-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="d80d4-105">xml root</span><span class="sxs-lookup"><span data-stu-id="d80d4-105">xml root</span></span>  
  
 <span data-ttu-id="d80d4-106">在该客户端 ADO 示例应用程序中，在客户端执行了一个简单 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="d80d4-106">In this client-side ADO sample application, a simple SQL query is executed on the client.</span></span> <span data-ttu-id="d80d4-107">由于 ClientSideXML 属性设置为 True，因此将不带 FOR XML 子句的 SELECT 语句发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="d80d4-107">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="d80d4-108">服务器执行该查询并将一个行集返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="d80d4-108">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="d80d4-109">然后客户端对行集应用 FOR XML 转换，并生成 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="d80d4-109">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="d80d4-110">Xml 根属性为生成的 XML 文档提供一个顶级根元素。</span><span class="sxs-lookup"><span data-stu-id="d80d4-110">The xml root property provides the single top-level root element for the XML document that is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d80d4-111">在代码中，必须在连接字符串中提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="d80d4-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="d80d4-112">此外，本示例还指定使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) 作为数据访问接口，该访问接口需要安装其他网络客户端软件。</span><span class="sxs-lookup"><span data-stu-id="d80d4-112">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="d80d4-113">有关详细信息，请参阅[SQL Server Native Client 的系统要求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="d80d4-113">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
