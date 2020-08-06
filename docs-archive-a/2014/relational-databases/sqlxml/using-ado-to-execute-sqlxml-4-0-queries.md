---
title: 使用 ADO 执行 SQLXML 4.0 查询
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- query testers [SQLXML]
- test scripts
- ADO [SQLXML]
- queries [SQLXML], ADO
- SQLXML, ADO
ms.assetid: 3d54e3bb-7c5f-427e-82f8-1403a54c4f53
author: rothja
ms.author: jroth
ms.openlocfilehash: 169d20b4192e4a5b8e7b32839f2da255fc58d89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687748"
---
# <a name="using-ado-to-execute-sqlxml-40-queries"></a><span data-ttu-id="7b0c3-102">使用 ADO 执行 SQLXML 4.0 查询</span><span class="sxs-lookup"><span data-stu-id="7b0c3-102">Using ADO to Execute SQLXML 4.0 Queries</span></span>
  <span data-ttu-id="7b0c3-103">在 SQLXML 的早期版本中，使用 SQLXML IIS 虚拟目录和 SQLXML ISAPI 筛选器支持基于 HTTP 的查询执行。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-103">In previous versions of SQLXML, HTTP-based query execution was supported using SQLXML IIS virtual directories and the SQLXML ISAPI filter.</span></span> <span data-ttu-id="7b0c3-104">在 SQLXML 4.0 中，由于从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 开始，本机 XML Web 服务提供了类似的重叠功能，因此已删除上述组件。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-104">In SQLXML 4.0, these components have been removed as similar and overlapping functionality is provided with native XML Web services beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="7b0c3-105">或者，您也可以利用在 Microsoft 数据访问组件 (MDAC) 2.6 中首次引入并在后续版本中延续使用的 ActiveX 数据对象 (ADO) 的 SQLXML 扩展来执行查询，并配合使用 SQLXML 4.0 和基于 COM 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-105">As an alternative, you can execute queries and use SQLXML 4.0 with your COM-based applications, by leveraging the SQLXML extensions to ActiveX Data Objects (ADO) that were first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="7b0c3-106">本主题说明了如何将 SQLXML 和 ADO 作为 Visual Basic Scripting Edition (VBScript) 应用程序（带有 .vbs 文件扩展名的脚本）的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-106">This topic demonstrates using SQLXML and ADO as part of a Visual Basic Scripting Edition (VBScript) application (a script with the .vbs file extension).</span></span> <span data-ttu-id="7b0c3-107">本主题还提供了可帮助您重新创建和测试 SQLXML 4.0 文档中的查询示例的初始设置过程。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-107">It provides initial setup procedures to help you recreate and test query samples in the SQLXML 4.0 documentation.</span></span>  
  
## <a name="creating-the-sqlxml-40-test-script"></a><span data-ttu-id="7b0c3-108">创建 SQLXML 4.0 测试脚本</span><span class="sxs-lookup"><span data-stu-id="7b0c3-108">Creating the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="7b0c3-109">在此过程中，您将创建一个 VBScript (.vbs) 文件（即 Sqlxml4test.vbs），利用 ADO 2.6 和更高版本中的 SQLXML ADO 扩展，您可以使用该文件执行 SQLXML 查询。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-109">In this procedure, you create a VBScript (.vbs) file, Sqlxml4test.vbs, which can be used to execute SQLXML queries by leveraging the SQLXML ADO extensions in ADO 2.6 and later.</span></span>  
  
#### <a name="to-create-the-sqlxml-40-query-tester-using-ado-vbscript"></a><span data-ttu-id="7b0c3-110">使用 ADO (VBScript) 创建 SQLXML 4.0 查询测试程序。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-110">To create the SQLXML 4.0 query tester using ADO (VBScript).</span></span>  
  
1.  <span data-ttu-id="7b0c3-111">复制下面的 VBScript 代码，并将其粘贴到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-111">Copy the VBScript code below, and paste it into a text file.</span></span> <span data-ttu-id="7b0c3-112">将该文件另存为 Sqlxml4test.vbs。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-112">Save the file as Sqlxml4test.vbs.</span></span>  
  
    ```vb
    WScript.Echo "Query process may take a few seconds to complete. Please be patient."  
  
    ' Note that for SQL Server Native Client to be used as the data provider,  
    ' it needs to be installed on the client computer first. Also, SQLXML extensions   
    ' for ADO are used and available in MDAC 2.6 or later.  
  
    'Set script variables.  
    inputFile = "@@FILE_NAME@@"  
    strServer = "@@SERVER_NAME@@"  
    strDatabase = "@@DATABASE_NAME@@"  
    dbGuid = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
    ' Establish ADO connection to SQL Server and   
    ' create an instance of the ADO Command object.  
    Set conn = CreateObject("ADODB.Connection")  
    Set cmd = CreateObject("ADODB.Command")  
    conn.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Server=" & strServer & _  
              ";Database=" & strDatabase & ";Integrated Security=SSPI"  
    Set cmd.ActiveConnection = conn  
  
    ' Create the input stream as an instance of the ADO Stream object.  
    Set inStream = CreateObject("ADODB.Stream")  
    inStream.Open  
    inStream.Charset = "utf-8"  
    inStream.LoadFromFile inputFile  
  
    ' Set ADO Command instance to use input stream.  
    Set cmd.CommandStream = inStream  
  
    ' Set the command dialect.  
    cmd.Dialect = dbGuid  
  
    ' Set a second ADO Stream instance for use as a results stream.   
    Set outStream = CreateObject("ADODB.Stream")  
    outStream.Open  
  
    ' Set dynamic properties used by the SQLXML ADO command instance.   
    cmd.Properties("XML Root").Value = "ROOT"  
    cmd.Properties("Output Encoding").Value = "UTF-8"  
  
    ' Connect the results stream to the command instance and execute the command.  
    cmd.Properties("Output Stream").Value = outStream  
    cmd.Execute , , 1024  
  
    ' Echo cropped/partial results to console.  
    WScript.Echo Left(outStream.ReadText, 1023)  
  
    inStream.Close  
    outStream.Close  
    ```  
  
2.  <span data-ttu-id="7b0c3-113">为尝试测试的示例和测试环境更新以下脚本值。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-113">Update the following script values for the sample you are trying to test and your test environment.</span></span>  
  
    -   <span data-ttu-id="7b0c3-114">查找“`@@FILE_NAME@@`”并将其替换为模板文件的名称。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-114">Find "`@@FILE_NAME@@`" and replace it with the name of your template file.</span></span>  
  
    -   <span data-ttu-id="7b0c3-115">查找“`@@SERVER_NAME@@`”并将其替换为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称（例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在本地运行，则替换为“`(local)`”）。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-115">Find "`@@SERVER_NAME@@`" and replace it with the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (for example, "`(local)`" if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running locally).</span></span>  
  
    -   <span data-ttu-id="7b0c3-116">查找“`@@DATABASE_NAME@@`”并将其替换为数据库名称（例如，“`AdventureWorks2012`”或“`tempdb`”）。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-116">Find "`@@DATABASE_NAME@@`" and replace it with the name of the database (for example, either "`AdventureWorks2012`" or "`tempdb`").</span></span>  
  
     <span data-ttu-id="7b0c3-117">如果尝试在本地计算机上重新创建的示例的特定说明提到了任何其他值，则必须更新这些值。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-117">Update any other values if mentioned in the specific instructions for the example you are attempting to recreate locally on your computer.</span></span>  
  
3.  <span data-ttu-id="7b0c3-118">保存文件并将其关闭。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-118">Save the file and close it.</span></span>  
  
4.  <span data-ttu-id="7b0c3-119">确定已创建作为尝试在本地计算机上重新创建的示例的一部分的所有附加文件，例如 XML 模板或架构。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-119">Verify that you have created any additional files, such as XML templates or schemas that are part of the sample you are attempting to recreate locally on your computer.</span></span> <span data-ttu-id="7b0c3-120">这些文件应位于您保存测试脚本文件 (Sqlxml4test.vbs) 的相同目录中。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-120">These files should be located in the same directory where you have saved the test script file (Sqlxml4test.vbs).</span></span>  
  
5.  <span data-ttu-id="7b0c3-121">按照下一部分中如何使用 SQLXML 4.0 测试脚本的说明操作。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-121">Follow the instructions in the next section for how to use the SQLXML 4.0 test script.</span></span>  
  
## <a name="using-the-sqlxml-40-test-script"></a><span data-ttu-id="7b0c3-122">使用 SQLXML 4.0 测试脚本</span><span class="sxs-lookup"><span data-stu-id="7b0c3-122">Using the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="7b0c3-123">以下过程说明如何使用 Sqlxml4test.vbs 文件测试本文档中提供的示例查询。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-123">The following procedure describes how to use the Sqlxml4test.vbs files to test the example queries provided in this documentation.</span></span>  
  
#### <a name="to-use-the-sqlxml-40-query-tester"></a><span data-ttu-id="7b0c3-124">使用 SQLXML 4.0 查询测试程序</span><span class="sxs-lookup"><span data-stu-id="7b0c3-124">To use the SQLXML 4.0 query tester</span></span>  
  
1.  <span data-ttu-id="7b0c3-125">验证是否安装了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7b0c3-125">Verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed, as follows:</span></span>  
  
    1.  <span data-ttu-id="7b0c3-126">从 "**开始**" 菜单中，指向 "**设置**"，然后单击 **"控制面板**"。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-126">From the **Start** menu, point to **Settings**, and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="7b0c3-127">在控制面板中，打开 "**添加或删除程序**"</span><span class="sxs-lookup"><span data-stu-id="7b0c3-127">In Control Panel, open **Add or Remove Programs**</span></span>  
  
    3.  <span data-ttu-id="7b0c3-128">在当前安装的程序列表中，验证列表中是否出现**Microsoft SQL Server Native Client** 。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-128">In the list of currently installed programs, verify that **Microsoft SQL Server Native Client** appears in the list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7b0c3-129">如果需要安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，请参阅[安装 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-129">If you need to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
2.  <span data-ttu-id="7b0c3-130">验证客户端计算机上安装的 MDAC 版本是否为 2.6 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-130">Verify that the version of MDAC installed for the client computer is 2.6 or later.</span></span> <span data-ttu-id="7b0c3-131">如果需要验证 MDAC 版本信息，你可以使用从 Microsoft 网站免费下载提供的 MDAC 组件检查器工具 [https://www.microsoft.com/](https://www.microsoft.com/) 。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-131">If you need to verify MDAC version information, you can use the MDAC Component Checker tool, which is provided as free download from the Microsoft Web site [https://www.microsoft.com/](https://www.microsoft.com/).</span></span> <span data-ttu-id="7b0c3-132">有关详细信息，请在 Microsoft 网站上的 "MDAC 组件检查器" 中进行搜索。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-132">For more information, search on "MDAC Component Checker" on the Microsoft Web site.</span></span>  
  
3.  <span data-ttu-id="7b0c3-133">执行脚本。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-133">Execute the script.</span></span>  
  
     <span data-ttu-id="7b0c3-134">您可以在命令行使用 Cscript.exe 来执行 VBScript 文件，也可以通过双击 Sqlxml4test.vbs 文件调用 Windows 脚本宿主 (WScript.exe) 来执行该文件。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-134">You can execute the VBScript file either at the command line using Cscript.exe or by double-clicking Sqlxml4test.vbs file to invoke the Windows Script Host (WScript.exe).</span></span>  
  
     <span data-ttu-id="7b0c3-135">执行时，脚本应显示一则消息，通知您在返回并显示查询结果作为脚本输出之前，执行此脚本可能需要花费一些时间。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-135">When executed, the script should display a message to alert you that the script might take a few moments to execute before returning and displaying query results as script output.</span></span> <span data-ttu-id="7b0c3-136">显示输出时，请将其内容与示例的预期结果相比较。</span><span class="sxs-lookup"><span data-stu-id="7b0c3-136">When the output appears, compare its contents to the expected results for the sample.</span></span>  
  
  
