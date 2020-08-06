---
title: 使用查询编辑器编辑 SQLCMD 脚本
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], SQLCMD scripts
- SQLCMD scripts
- modifying scripts
- Query Editor [Database Engine], SQLCMD scripts
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: f77b866d-c330-47c9-9e74-0b8d8dff4b31
author: rothja
ms.author: jroth
ms.openlocfilehash: a3466cfc15ea2f4f0c8de5da42f4a1c24c28a575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587323"
---
# <a name="edit-sqlcmd-scripts-with-query-editor"></a><span data-ttu-id="07eb2-102">使用查询编辑器编辑 SQLCMD 脚本</span><span class="sxs-lookup"><span data-stu-id="07eb2-102">Edit SQLCMD Scripts with Query Editor</span></span>
  <span data-ttu-id="07eb2-103">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查询编辑器，可以将查询作为 SQLCMD 脚本来进行编写和编辑。</span><span class="sxs-lookup"><span data-stu-id="07eb2-103">By using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] you can write and edit queries as SQLCMD scripts.</span></span> <span data-ttu-id="07eb2-104">当必须处理同一脚本中的 Windows 系统命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时，使用的是 SQLCMD 脚本。</span><span class="sxs-lookup"><span data-stu-id="07eb2-104">You use SQLCMD scripts when you have to process Windows System commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the same script.</span></span>  
  
## <a name="sqlcmd-mode"></a><span data-ttu-id="07eb2-105">SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="07eb2-105">SQLCMD Mode</span></span>  
 <span data-ttu-id="07eb2-106">若要使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器编写或编辑 SQLCMD 脚本，您必须启用 SQLCMD 脚本撰写模式。</span><span class="sxs-lookup"><span data-stu-id="07eb2-106">To use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to write or edit SQLCMD scripts, you must enable the SQLCMD scripting mode.</span></span> <span data-ttu-id="07eb2-107">默认情况下，查询编辑器中将不启用 SQLCMD 模式。</span><span class="sxs-lookup"><span data-stu-id="07eb2-107">By default, SQLCMD mode is not enabled in the Query Editor.</span></span> <span data-ttu-id="07eb2-108">可以通过在工具栏中单击 **“SQLCMD 模式”** 图标或从 **“查询”** 菜单中选择 **“SQLCMD 模式”** 来启用脚本撰写模式。</span><span class="sxs-lookup"><span data-stu-id="07eb2-108">You can enable scripting mode by clicking the **SQLCMD Mode** icon in the toolbar or by selecting **SQLCMD Mode** from the **Query** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07eb2-109">启用 SQLCMD 模式将关闭 IntelliSense 和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询编辑器中的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 调试器。</span><span class="sxs-lookup"><span data-stu-id="07eb2-109">Enabling SQLCMD mode turns off IntelliSense and the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="07eb2-110">查询编辑器中的 SQLCMD 脚本可以使用所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本能够使用的功能。</span><span class="sxs-lookup"><span data-stu-id="07eb2-110">SQLCMD scripts in the Query Editor can use the same features that all [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts use.</span></span> <span data-ttu-id="07eb2-111">这些功能包括：</span><span class="sxs-lookup"><span data-stu-id="07eb2-111">These features include the following:</span></span>  
  
-   <span data-ttu-id="07eb2-112">颜色编码</span><span class="sxs-lookup"><span data-stu-id="07eb2-112">Color Coding</span></span>  
  
-   <span data-ttu-id="07eb2-113">执行脚本</span><span class="sxs-lookup"><span data-stu-id="07eb2-113">Executing Scripts</span></span>  
  
-   <span data-ttu-id="07eb2-114">源代码管理</span><span class="sxs-lookup"><span data-stu-id="07eb2-114">Source Control</span></span>  
  
-   <span data-ttu-id="07eb2-115">分析脚本</span><span class="sxs-lookup"><span data-stu-id="07eb2-115">Parsing Scripts</span></span>  
  
-   <span data-ttu-id="07eb2-116">Showplan</span><span class="sxs-lookup"><span data-stu-id="07eb2-116">Showplan</span></span>  
  
## <a name="enable-sqlcmd-scripting-in-query-editor"></a><span data-ttu-id="07eb2-117">在查询编辑器中启用 SQLCMD 脚本撰写</span><span class="sxs-lookup"><span data-stu-id="07eb2-117">Enable SQLCMD Scripting in Query Editor</span></span>  
 <span data-ttu-id="07eb2-118">若要为活动的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口启用 SQLCMD 脚本撰写，请使用以下步骤。</span><span class="sxs-lookup"><span data-stu-id="07eb2-118">To turn SQLCMD scripting on for an active [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, use the following procedure.</span></span>  
  
#### <a name="to-switch-a-database-engine-query-editor-window-to-sqlcmd-mode"></a><span data-ttu-id="07eb2-119">将数据库引擎查询编辑器窗口切换到 SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="07eb2-119">To switch a Database Engine Query Editor window to SQLCMD mode</span></span>  
  
1.  <span data-ttu-id="07eb2-120">在“对象资源管理器”中，右键单击服务器，再单击“新建查询”  以打开新的[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="07eb2-120">In Object Explorer, right-click the server, and then click **New Query**, to open a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
2.  <span data-ttu-id="07eb2-121">在 **“查询”** 菜单中，单击 **“SQLCMD 模式”** 。</span><span class="sxs-lookup"><span data-stu-id="07eb2-121">On the **Query** menu, click **SQLCMD Mode**.</span></span>  
  
     <span data-ttu-id="07eb2-122">查询编辑器将在其上下文中执行 **sqlcmd** 语句。</span><span class="sxs-lookup"><span data-stu-id="07eb2-122">The Query Editor executes **sqlcmd** statements in the context of the Query Editor.</span></span>  
  
3.  <span data-ttu-id="07eb2-123">在 **“SQL 编辑器”** 工具栏的 **“可用数据库”** 列表中，选择 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07eb2-123">On the **SQL Editor** toolbar, in the **Available Databases** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
4.  <span data-ttu-id="07eb2-124">在“查询编辑器”窗口中，键入以下两个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和 `!!DIR` **sqlcmd** 语句：</span><span class="sxs-lookup"><span data-stu-id="07eb2-124">In the Query Editor window, type the following two [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the `!!DIR` **sqlcmd** statement:</span></span>  
  
    ```  
    SELECT DISTINCT Type FROM Sales.SpecialOffer;  
    GO  
    !!DIR  
    GO  
    SELECT ProductCategoryID, Name FROM Production.ProductCategory;  
    GO  
    ```  
  
5.  <span data-ttu-id="07eb2-125">按 F5 执行混合了 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句和 MS-DOS 语句的整个部分。</span><span class="sxs-lookup"><span data-stu-id="07eb2-125">Press F5 to execute the whole section of mixed [!INCLUDE[tsql](../../includes/tsql-md.md)] and MS-DOS statements.</span></span>  
  
     <span data-ttu-id="07eb2-126">请注意第一个和第三个语句产生的两个 SQL 结果窗格。</span><span class="sxs-lookup"><span data-stu-id="07eb2-126">Notice the two SQL result panes from the first and third statements.</span></span>  
  
6.  <span data-ttu-id="07eb2-127">在 **“结果”** 窗格中，单击 **“消息”** 选项卡可以查看所有三个语句产生的消息：</span><span class="sxs-lookup"><span data-stu-id="07eb2-127">In the **Results** pane, click the **Messages** tab to see the messages from all three statements:</span></span>  
  
    -   <span data-ttu-id="07eb2-128">（6 行受影响）</span><span class="sxs-lookup"><span data-stu-id="07eb2-128">(6 row(s) affected)</span></span>  
  
    -   \<The directory information>  
  
    -   <span data-ttu-id="07eb2-129">(4 row(s) affected)</span><span class="sxs-lookup"><span data-stu-id="07eb2-129">(4 row(s) affected)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07eb2-130">从命令行执行 **sqlcmd** 实用工具时，该工具允许与操作系统完全交互。</span><span class="sxs-lookup"><span data-stu-id="07eb2-130">When executed from the command line, the **sqlcmd** utility permits full interaction with the operating system.</span></span> <span data-ttu-id="07eb2-131">在 **“SQLCMD 模式”** 下使用查询编辑器时，必须注意不要执行交互语句。</span><span class="sxs-lookup"><span data-stu-id="07eb2-131">When you use the Query Editor in **SQLCMD Mode**, you must be careful not to execute interactive statements.</span></span> <span data-ttu-id="07eb2-132">查询编辑器无法响应操作系统提示。</span><span class="sxs-lookup"><span data-stu-id="07eb2-132">The Query Editor cannot respond to operating system prompts.</span></span>  
  
 <span data-ttu-id="07eb2-133">有关如何运行 SQLCMD 的详细信息，请参阅 [sqlcmd Utility](../../tools/sqlcmd-utility.md)或学习 SQLCMD 教程。</span><span class="sxs-lookup"><span data-stu-id="07eb2-133">For more information about how to run SQLCMD, see [sqlcmd Utility](../../tools/sqlcmd-utility.md), or take the SQLCMD tutorial.</span></span>  
  
## <a name="enable-sqlcmd-scripting-by-default"></a><span data-ttu-id="07eb2-134">默认启用 SQLCMD 脚本撰写</span><span class="sxs-lookup"><span data-stu-id="07eb2-134">Enable SQLCMD Scripting by Default</span></span>  
 <span data-ttu-id="07eb2-135">若要默认启用 SQLCMD 脚本撰写，请在 **“工具”** 菜单中选择 **“选项”**，展开 **“查询执行”** 和 **SQL Server**，单击 **“常规”** 页面，然后选中 **“默认情况下，在 SQLCMD 模式下打开新查询”** 框。</span><span class="sxs-lookup"><span data-stu-id="07eb2-135">To turn SQLCMD scripting on by default, on the **Tools** menu select **Options**, expand **Query Execution**, and **SQL Server**, click the **General** page, and then check the **By default open new queries in SQLCMD Mode** box.</span></span>  
  
## <a name="writing-and-editing-sqlcmd-scripts"></a><span data-ttu-id="07eb2-136">编写和编辑 SQLCMD 脚本</span><span class="sxs-lookup"><span data-stu-id="07eb2-136">Writing and Editing SQLCMD Scripts</span></span>  
 <span data-ttu-id="07eb2-137">启用脚本撰写模式后，可以编写 SQLCMD 命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="07eb2-137">After enabling scripting mode you may write SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="07eb2-138">下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="07eb2-138">The following rules apply:</span></span>  
  
-   <span data-ttu-id="07eb2-139">SQLCMD 命令必须是一行中的第一个语句。</span><span class="sxs-lookup"><span data-stu-id="07eb2-139">SQLCMD commands must be the first statement on a line.</span></span>  
  
-   <span data-ttu-id="07eb2-140">每行只允许使用一个 SQLCMD 命令。</span><span class="sxs-lookup"><span data-stu-id="07eb2-140">Only one SQLCMD command is permitted on each line.</span></span>  
  
-   <span data-ttu-id="07eb2-141">SQLCMD 命令前可以添加注释或空格。</span><span class="sxs-lookup"><span data-stu-id="07eb2-141">SQLCMD commands can be preceded by comments or white space.</span></span>  
  
-   <span data-ttu-id="07eb2-142">注释字符内的 SQLCMD 命令不会执行。</span><span class="sxs-lookup"><span data-stu-id="07eb2-142">SQLCMD commands within comment characters are not executed.</span></span>  
  
-   <span data-ttu-id="07eb2-143">单行注释字符是两个连字符 (`--)` ，必须位于一行的开头。</span><span class="sxs-lookup"><span data-stu-id="07eb2-143">Single line comment characters are two hyphens (`--)` and must appear at the beginning of a line.</span></span>  
  
-   <span data-ttu-id="07eb2-144">操作系统命令前面必须具有两个感叹号 (`!!`)。</span><span class="sxs-lookup"><span data-stu-id="07eb2-144">Operating system commands must be preceded by two exclamation points (`!!`).</span></span> <span data-ttu-id="07eb2-145">两个感叹号命令使其后的语句通过 `cmd.exe` 命令处理器来执行。</span><span class="sxs-lookup"><span data-stu-id="07eb2-145">The double-exclamation points command causes the statement that follows the exclamation points to be executed using the `cmd.exe` command processor.</span></span> <span data-ttu-id="07eb2-146">`!!` 后面的文本作为一个参数传递到 `cmd.exe`，因此最终的命令行将如此执行： `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`。</span><span class="sxs-lookup"><span data-stu-id="07eb2-146">The text after `!!` is passed in as a parameter to `cmd.exe`, so the final command line will execute as: `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`.</span></span>  
  
-   <span data-ttu-id="07eb2-147">为了清楚地区分 SQLCMD 命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)]，所有的 SQLCMD 命令都需要在前面添加冒号 (`:`)。</span><span class="sxs-lookup"><span data-stu-id="07eb2-147">To make a clear distinction between SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)], all SQLCMD commands, need to be prefixed with a colon (`:`).</span></span>  
  
-   <span data-ttu-id="07eb2-148">`GO` 命令可以直接使用，无需在其前面加 `!!:`</span><span class="sxs-lookup"><span data-stu-id="07eb2-148">The `GO` command may be used without preface, or preceded by `!!:`</span></span>  
  
-   <span data-ttu-id="07eb2-149">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器支持环境变量和定义为 SQLCMD 脚本的一部分的变量，但不支持内置的 SQLCMD 或 **osql** 变量。</span><span class="sxs-lookup"><span data-stu-id="07eb2-149">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports environment variables and variables that are defined as part of a SQLCMD script, but does not support built-in SQLCMD or **osql** variables.</span></span> <span data-ttu-id="07eb2-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 处理的 SQLCMD 变量区分大小写。</span><span class="sxs-lookup"><span data-stu-id="07eb2-150">SQLCMD processing by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is case sensitive for variables.</span></span> <span data-ttu-id="07eb2-151">例如，PRINT '$(COMPUTERNAME)' 会生成正确的结果，而 PRINT '$(ComputerName)' 则返回错误。</span><span class="sxs-lookup"><span data-stu-id="07eb2-151">For example, PRINT '$(COMPUTERNAME)' produces the correct result, but PRINT '$(ComputerName)' returns an error.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="07eb2-152">在常规模式和 SQLCMD 模式下，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient 来执行。</span><span class="sxs-lookup"><span data-stu-id="07eb2-152">uses [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode.</span></span> <span data-ttu-id="07eb2-153">从命令行运行时，SQLCMD 将使用 OLE DB 访问接口。</span><span class="sxs-lookup"><span data-stu-id="07eb2-153">When run from the command line, SQLCMD uses the OLE DB provider.</span></span> <span data-ttu-id="07eb2-154">由于可以应用不同的默认选项，因此在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD 模式下以及在 SQLCMD 实用工具中执行相同的查询时，可能会获得不同的行为。</span><span class="sxs-lookup"><span data-stu-id="07eb2-154">Because different default options may apply, it is possible to get different behavior while executing the same query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD Mode, and in the SQLCMD utility.</span></span>  
  
## <a name="supported-sqlcmd-syntax"></a><span data-ttu-id="07eb2-155">支持的 SQLCMD 语法</span><span class="sxs-lookup"><span data-stu-id="07eb2-155">Supported SQLCMD Syntax</span></span>  
 <span data-ttu-id="07eb2-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器支持以下 SQLCMD 脚本关键字：</span><span class="sxs-lookup"><span data-stu-id="07eb2-156">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following SQLCMD script keywords:</span></span>  
  
 `[!!:]GO[count]`  
  
 `!! <command>`  
  
 `:exit(statement)`  
  
 `:Quit`  
  
 `:r <filename>`  
  
 `:setvar <var> <value>`  
  
 `:connect server[\instance] [-l login_timeout] [-U user [-P password]]`  
  
 `:on error [ignore|exit]`  
  
 `:error <filename>|stderr|stdout`  
  
 `:out <filename>|stderr|stdout`  
  
> [!NOTE]  
>  <span data-ttu-id="07eb2-157">对于 `:error` 和 `:out`， `stderr` 和 `stdout` 将向消息选项卡发送输出。</span><span class="sxs-lookup"><span data-stu-id="07eb2-157">For both `:error` and `:out`, `stderr` and `stdout` send output to the messages tab.</span></span>  
  
 <span data-ttu-id="07eb2-158">查询编辑器不支持上面未列出的 SQLCMD 命令。</span><span class="sxs-lookup"><span data-stu-id="07eb2-158">SQLCMD commands not listed above are not supported in Query Editor.</span></span> <span data-ttu-id="07eb2-159">当执行包含不支持的 SQLCMD 关键字的脚本时，查询编辑器会 \<ignored command*> 为每个不支持的关键字向目标发送一条 "忽略命令 \*" 消息。</span><span class="sxs-lookup"><span data-stu-id="07eb2-159">When a script containing SQLCMD keywords that are not supported is executed, the Query Editor will send an "Ignoring command \*\<ignored command*>" message to the destination for each unsupported keyword.</span></span> <span data-ttu-id="07eb2-160">脚本将成功执行，但同时忽略不支持的命令。</span><span class="sxs-lookup"><span data-stu-id="07eb2-160">The script will execute successfully, but the unsupported commands will be ignored.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="07eb2-161">因为不是从命令行启动 SQLCMD，所以在 SQLCMD 模式下运行查询编辑器时会有一些限制。</span><span class="sxs-lookup"><span data-stu-id="07eb2-161">Because you are not starting SQLCMD from the command line, there are some limitations when running Query Editor in SQLCMD Mode.</span></span> <span data-ttu-id="07eb2-162">不能传入命令行参数（如变量），而且，由于查询编辑器无法响应操作系统提示，因此必须注意不要执行交互语句。</span><span class="sxs-lookup"><span data-stu-id="07eb2-162">You cannot pass in command-line parameters such as variables, and, because the Query Editor does not have the ability to respond to operating system prompts, you must be careful not to execute interactive statements.</span></span>  
  
## <a name="color-coding-in-sqlcmd-scripts"></a><span data-ttu-id="07eb2-163">SQLCMD 脚本中的颜色编码</span><span class="sxs-lookup"><span data-stu-id="07eb2-163">Color Coding in SQLCMD Scripts</span></span>  
 <span data-ttu-id="07eb2-164">启用 SQLCMD 脚本撰写后，脚本将进行颜色编码。</span><span class="sxs-lookup"><span data-stu-id="07eb2-164">With SQLCMD scripting enabled, scripts will be color coded.</span></span> <span data-ttu-id="07eb2-165">[!INCLUDE[tsql](../../includes/tsql-md.md)] 关键字的颜色编码将保持不变。</span><span class="sxs-lookup"><span data-stu-id="07eb2-165">The color coding for [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords will remain the same.</span></span> <span data-ttu-id="07eb2-166">SQLCMD 命令用阴影背景来表示。</span><span class="sxs-lookup"><span data-stu-id="07eb2-166">SQLCMD commands are presented with a shaded background.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07eb2-167">示例</span><span class="sxs-lookup"><span data-stu-id="07eb2-167">Example</span></span>  
 <span data-ttu-id="07eb2-168">下面的示例使用 **sqlcmd** 语句创建名为 testoutput.txt 的输出文件，并将两个 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 语句与一个操作系统命令一起执行（以输出当前目录）。</span><span class="sxs-lookup"><span data-stu-id="07eb2-168">The following example uses a **sqlcmd** statement to create an output file called testoutput.txt, executes two [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements along with one operating system command (to print out the current directory).</span></span> <span data-ttu-id="07eb2-169">结果文件包含 `DIR` 语句的消息输出，后面跟有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的结果输出。</span><span class="sxs-lookup"><span data-stu-id="07eb2-169">The resultant file contains the message output from the `DIR` statement, followed by the results output from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
:out C:\testoutput.txt  
SELECT @@VERSION As 'Server Version'  
!!DIR  
!!:GO  
SELECT @@SERVERNAME AS 'Server Name'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="07eb2-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07eb2-170">See Also</span></span>  
 [<span data-ttu-id="07eb2-171">sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="07eb2-171">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
