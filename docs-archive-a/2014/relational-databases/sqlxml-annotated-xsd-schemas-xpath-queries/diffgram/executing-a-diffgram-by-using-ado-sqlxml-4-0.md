---
title: 使用 ADO 执行 DiffGram (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b96db25fd46b1ecbbc15c8acd912743e5560f178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587294"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a><span data-ttu-id="14be2-102">使用 ADO 执行 DiffGram (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="14be2-102">Executing a DiffGram by Using ADO (SQLXML 4.0)</span></span>
  <span data-ttu-id="14be2-103">该 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 应用程序使用 ADO 建立与 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的连接，然后执行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="14be2-103">This [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application uses ADO to establish a connection to an instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then executes a DiffGram.</span></span> <span data-ttu-id="14be2-104">在该应用程序中，DiffGram 和 XSD 架构存储在文件中。</span><span class="sxs-lookup"><span data-stu-id="14be2-104">In this application, the DiffGram and the XSD schema are stored in a file.</span></span> <span data-ttu-id="14be2-105">该应用程序从指定的文件加载 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="14be2-105">The application loads the DiffGram from the specified file.</span></span> <span data-ttu-id="14be2-106">可以使用[DiffGram 示例](diffgram-examples-sqlxml-4-0.md)中所述的任何 diffgram (和关联的 XSD 架构) 。</span><span class="sxs-lookup"><span data-stu-id="14be2-106">You can use any of the DiffGrams (and the associated XSD schema) described in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="14be2-107">以下是示例应用程序的过程：</span><span class="sxs-lookup"><span data-stu-id="14be2-107">This is the process for the sample application:</span></span>  
  
-   <span data-ttu-id="14be2-108">**Conn**对象 (**adodb.recordset。连接**) 与在特定服务器上运行的 SQL Server 实例建立连接。</span><span class="sxs-lookup"><span data-stu-id="14be2-108">The **conn** object (**ADODB.Connection**) establishes a connection to a running instance of SQL Server on a specific server.</span></span>  
  
-   <span data-ttu-id="14be2-109">**Cmd**对象 (在已建立的连接上执行**adodb.recordset) 。**</span><span class="sxs-lookup"><span data-stu-id="14be2-109">The **cmd** object (**ADODB.Command**) executes on the established connection.</span></span>  
  
-   <span data-ttu-id="14be2-110">将命令方言设置为 DBGUID_MSSQLXML。</span><span class="sxs-lookup"><span data-stu-id="14be2-110">The command dialect is set to DBGUID_MSSQLXML.</span></span>  
  
-   <span data-ttu-id="14be2-111">DiffGram 将从文件复制到命令流 (**strmIn**) 。</span><span class="sxs-lookup"><span data-stu-id="14be2-111">The DiffGram is copied to the command stream (**strmIn**) from a file.</span></span>  
  
-   <span data-ttu-id="14be2-112">命令的输出流设置为**StrmOut**对象 (**adodb.recordset。流式传输**) 可接收任何返回的数据。</span><span class="sxs-lookup"><span data-stu-id="14be2-112">The command's output stream is set to the **StrmOut** object (**ADODB.Stream**) to receive any returned data.</span></span>  
  
-   <span data-ttu-id="14be2-113">当使用 SQLOLEDB 访问接口时，默认情况下，您将获取 Sqlxmlx.dll 提供的 Microsoft SQLXML 功能。</span><span class="sxs-lookup"><span data-stu-id="14be2-113">When you are using the SQLOLEDB Provider, by default you will get the Microsoft SQLXML functionality provided by Sqlxmlx.dll.</span></span> <span data-ttu-id="14be2-114">若要将 Sqlxml4.dll 与 SQLOLEDB 提供程序一起使用，必须在 SQLOLEDB 提供程序**连接**对象上将**sqlxml Version**属性设置为**sqlxml。**</span><span class="sxs-lookup"><span data-stu-id="14be2-114">To use Sqlxml4.dll with the SQLOLEDB Provider, the **SQLXML Version** property must be set to **SQLXML.4.0** on the SQLOLEDB Provider **Connection** object.</span></span>  
  
-   <span data-ttu-id="14be2-115">执行该命令 (DiffGram)。</span><span class="sxs-lookup"><span data-stu-id="14be2-115">The command (DiffGram) is executed.</span></span>  
  
 <span data-ttu-id="14be2-116">以下代码为示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="14be2-116">The following code is the sample application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="14be2-117">在该代码中，必须在连接字符串中提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="14be2-117">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a><span data-ttu-id="14be2-118">测试 DiffGram</span><span class="sxs-lookup"><span data-stu-id="14be2-118">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="14be2-119">对于计算机上的文件夹，请从[DiffGram 示例](diffgram-examples-sqlxml-4-0.md)中的一个示例复制其中一个 diffgram 和对应的 XSD 架构。</span><span class="sxs-lookup"><span data-stu-id="14be2-119">To a folder on your computer, copy any one of the DiffGrams and the corresponding XSD schema from one of the examples in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="14be2-120">打开 Visual Basic 并创建标准 EXE 项目。</span><span class="sxs-lookup"><span data-stu-id="14be2-120">Open Visual Basic and create a Standard EXE project.</span></span>  
  
3.  <span data-ttu-id="14be2-121">将这些引用添加到项目中：</span><span class="sxs-lookup"><span data-stu-id="14be2-121">Add these references to the project:</span></span>  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  <span data-ttu-id="14be2-122">在 "工具箱" 中，单击 "**命令**按钮"，然后在窗体上绘制一个按钮。</span><span class="sxs-lookup"><span data-stu-id="14be2-122">In the Toolbox, click **CommandButton**, and then draw a button on the form.</span></span>  
  
5.  <span data-ttu-id="14be2-123">双击该按钮编辑代码，并添加本主题中提供的应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="14be2-123">Double-click the button to edit the code, and add the application code that is provided in the topic.</span></span>  
  
6.  <span data-ttu-id="14be2-124">编辑代码以指定 DiffGram 和 XSD 文件名，</span><span class="sxs-lookup"><span data-stu-id="14be2-124">Edit the code to specify the DiffGram and XSD file names.</span></span> <span data-ttu-id="14be2-125">并根据需要编辑连接字符串。</span><span class="sxs-lookup"><span data-stu-id="14be2-125">Also edit the connection string as appropriate.</span></span>  
  
7.  <span data-ttu-id="14be2-126">执行应用程序。</span><span class="sxs-lookup"><span data-stu-id="14be2-126">Execute the application.</span></span> <span data-ttu-id="14be2-127">执行结果取决于您执行的 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="14be2-127">The result of the execution depends on what DiffGram you are executing.</span></span>  
  
  
