---
title: 数据库引擎查询编辑器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.tsqlquery.f1
dev_langs:
- TSQL
helpviewer_keywords:
- Query Editor [Database Engine]
- Transact-SQL Editor See Query Editor [Database Engine]
- Database Engine Query Editor See Query Editor [Database Engine]
- Query Editor [Database Engine], Toolbar
- editors [SQL Server Management Studio], Database Engine Query Editor
- Query Editor [Database Engine], Features
- SQL Server Management Studio [SQL Server], Database Engine Query Editor
ms.assetid: 05cfae9b-96d5-4a35-a098-0bc3a548bcfc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dcb4298ec55181ea3c979228e8decf681483f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576620"
---
# <a name="database-engine-query-editor-sql-server-management-studio"></a><span data-ttu-id="a1b85-102">数据库引擎查询编辑器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a1b85-102">Database Engine Query Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a1b85-103">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器可以创建和运行包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的脚本。</span><span class="sxs-lookup"><span data-stu-id="a1b85-103">Use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to create and run scripts containing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="a1b85-104">此编辑器还支持包含 **sqlcmd** 命令的正在运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="a1b85-104">The editor also supports running scripts that contain **sqlcmd** commands.</span></span>  
  
## <a name="transact-sql-f1-help"></a><span data-ttu-id="a1b85-105">Transact-SQL F1 帮助</span><span class="sxs-lookup"><span data-stu-id="a1b85-105">Transact-SQL F1 Help</span></span>  
 <span data-ttu-id="a1b85-106">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器支持当您选择 F1 时将您链接到特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的参考主题。</span><span class="sxs-lookup"><span data-stu-id="a1b85-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports linking you to the reference topic for a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement when you select F1.</span></span> <span data-ttu-id="a1b85-107">为此，突出显示 Transact-SQL 语句的名称，然后选择 F1。</span><span class="sxs-lookup"><span data-stu-id="a1b85-107">To do so, highlight the name of a Transact-SQL statement and then select F1.</span></span> <span data-ttu-id="a1b85-108">接着，帮助搜索引擎将搜索具有与突出显示的字符串匹配的 F1 帮助属性的主题。</span><span class="sxs-lookup"><span data-stu-id="a1b85-108">The help search engine will then search for a topic that has an F1 help attribute that matches the string you highlighted.</span></span>  
  
 <span data-ttu-id="a1b85-109">如果帮助搜索引擎找不到具有与突出显示的字符串完全匹配的 F1 帮助关键字的主题，则无法显示该主题。</span><span class="sxs-lookup"><span data-stu-id="a1b85-109">If the help search engine does not find a topic with an F1 help keyword that exactly matches the string you highlighted, then this topic is displayed.</span></span> <span data-ttu-id="a1b85-110">在这种情况下，有两种方法可以找到所需的帮助：</span><span class="sxs-lookup"><span data-stu-id="a1b85-110">In that case, there are two approaches to finding the help you are looking for:</span></span>  
  
-   <span data-ttu-id="a1b85-111">将您突出显示的编辑器字符串复制并粘贴到 SQL Server 联机丛书的搜索选项卡中，并执行搜索。</span><span class="sxs-lookup"><span data-stu-id="a1b85-111">Copy and paste the editor string you highlighted into the search tab of SQL Server Books Online and do a search.</span></span>  
  
-   <span data-ttu-id="a1b85-112">仅突出显示 Transact-SQL 语句中可能与应用于主题的 F 帮助关键字匹配的部分，然后再次选择 F1。</span><span class="sxs-lookup"><span data-stu-id="a1b85-112">Highlight only the part of the Transact-SQL statement likely to match an F1 help keyword applied to a topic and select F1 again.</span></span> <span data-ttu-id="a1b85-113">搜索引擎要求突出显示的字符串与分配给主题的 F1 帮助关键字之间完全匹配。</span><span class="sxs-lookup"><span data-stu-id="a1b85-113">The search engine requires an exact match between the string you highlighted and an F1 help keyword assigned to a topic.</span></span> <span data-ttu-id="a1b85-114">如果突出显示的字符串包含对于您的环境是唯一的元素（如列或参数名称），则搜索引擎将不会获得匹配项。</span><span class="sxs-lookup"><span data-stu-id="a1b85-114">If the string you highlighted contains elements unique to your environment, such as column or parameter names, the search engine will not get a match.</span></span> <span data-ttu-id="a1b85-115">要突出显示的字符串的示例包括：</span><span class="sxs-lookup"><span data-stu-id="a1b85-115">Examples of the strings to highlight include:</span></span>  
  
    -   <span data-ttu-id="a1b85-116">Transact-SQL 语句的名称，如 SELECT、CREATE DATABASE 或 BEGIN TRANSACTION。</span><span class="sxs-lookup"><span data-stu-id="a1b85-116">The name of a Transact-SQL statement, such as SELECT, CREATE DATABASE or BEGIN TRANSACTION.</span></span>  
  
    -   <span data-ttu-id="a1b85-117">内置函数的名称，如 SERVERPROPERTY 或 @@VERSION。</span><span class="sxs-lookup"><span data-stu-id="a1b85-117">The name of a built-in function, such as SERVERPROPERTY, or @@VERSION.</span></span>  
  
    -   <span data-ttu-id="a1b85-118">系统存储过程表或视图的名称，如 sys.data_spaces 或 sp_tableoption。</span><span class="sxs-lookup"><span data-stu-id="a1b85-118">The name of a system stored procedure table, or view, such as sys.data_spaces or sp_tableoption.</span></span>  
  
## <a name="working-with-the-database-engine-query-editor"></a><span data-ttu-id="a1b85-119">使用数据库引擎查询编辑器</span><span class="sxs-lookup"><span data-stu-id="a1b85-119">Working With the Database Engine Query Editor</span></span>  
 <span data-ttu-id="a1b85-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器是在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中实现的四个编辑器之一。</span><span class="sxs-lookup"><span data-stu-id="a1b85-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is one of four editors implemented in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a1b85-121">对于在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中实现的功能以及使用此编辑器可以执行的主要任务的说明，请参阅[查询和文本编辑器 (SQL Server Management Studio)](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b85-121">For a description of the functionality implemented in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the main tasks you can perform using the editor, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="a1b85-122">SQL 编辑器工具栏</span><span class="sxs-lookup"><span data-stu-id="a1b85-122">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="a1b85-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器打开时，SQL 编辑器工具栏上显示以下按钮：</span><span class="sxs-lookup"><span data-stu-id="a1b85-123">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is open, the SQL Editor toolbar appears with the following buttons.</span></span>  
  
 <span data-ttu-id="a1b85-124">**“连接”**</span><span class="sxs-lookup"><span data-stu-id="a1b85-124">**Connect**</span></span>  
 <span data-ttu-id="a1b85-125">打开“连接到服务器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="a1b85-125">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="a1b85-126">此对话框用于建立与服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="a1b85-126">Use this dialog box to establish a connection to a server.</span></span>  
  
 <span data-ttu-id="a1b85-127">**取消**</span><span class="sxs-lookup"><span data-stu-id="a1b85-127">**Disconnect**</span></span>  
 <span data-ttu-id="a1b85-128">断开当前查询编辑器与服务器之间的连接。</span><span class="sxs-lookup"><span data-stu-id="a1b85-128">Disconnects the current Query Editor from the server.</span></span>  
  
 <span data-ttu-id="a1b85-129">**更改连接**</span><span class="sxs-lookup"><span data-stu-id="a1b85-129">**Change Connection**</span></span>  
 <span data-ttu-id="a1b85-130">打开“连接到服务器”  对话框。</span><span class="sxs-lookup"><span data-stu-id="a1b85-130">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="a1b85-131">此对话框用于建立与另一个服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="a1b85-131">Use this dialog box to establish a connection to a different server.</span></span>  
  
 <span data-ttu-id="a1b85-132">**使用当前连接新建查询**</span><span class="sxs-lookup"><span data-stu-id="a1b85-132">**New Query with Current Connection**</span></span>  
 <span data-ttu-id="a1b85-133">打开新的查询编辑器窗口并使用当前查询编辑器窗口的连接信息。</span><span class="sxs-lookup"><span data-stu-id="a1b85-133">Opens a new Query Editor window and uses the connection information from the current Query Editor window.</span></span>  
  
 <span data-ttu-id="a1b85-134">**可用数据库**</span><span class="sxs-lookup"><span data-stu-id="a1b85-134">**Available Databases**</span></span>  
 <span data-ttu-id="a1b85-135">将连接更改到同一服务器上的其他数据库。</span><span class="sxs-lookup"><span data-stu-id="a1b85-135">Change the connection to a different database on the same server.</span></span>  
  
 <span data-ttu-id="a1b85-136">**执行**</span><span class="sxs-lookup"><span data-stu-id="a1b85-136">**Execute**</span></span>  
 <span data-ttu-id="a1b85-137">执行所选的代码，如果没有选择任何代码，则执行查询编辑器中的全部代码。</span><span class="sxs-lookup"><span data-stu-id="a1b85-137">Executes the selected code or, if no code is selected, executes all the code in the Query Editor.</span></span>  
  
 <span data-ttu-id="a1b85-138">**调试**</span><span class="sxs-lookup"><span data-stu-id="a1b85-138">**Debug**</span></span>  
 <span data-ttu-id="a1b85-139">启用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器。</span><span class="sxs-lookup"><span data-stu-id="a1b85-139">Enables the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="a1b85-140">此调试器支持调试操作，例如设置断点、监视变量和单步执行代码。</span><span class="sxs-lookup"><span data-stu-id="a1b85-140">This debugger supports debugging actions such as setting breakpoints, watching variables, and stepping through code.</span></span>  
  
 <span data-ttu-id="a1b85-141">**取消执行查询**</span><span class="sxs-lookup"><span data-stu-id="a1b85-141">**Cancel Executing Query**</span></span>  
 <span data-ttu-id="a1b85-142">向服务器发送取消请求。</span><span class="sxs-lookup"><span data-stu-id="a1b85-142">Sends a cancellation request to the server.</span></span> <span data-ttu-id="a1b85-143">有些查询不能立即取消，而必须等待适当的取消条件。</span><span class="sxs-lookup"><span data-stu-id="a1b85-143">Some queries cannot be canceled immediately, but must wait for a suitable cancellation condition.</span></span> <span data-ttu-id="a1b85-144">取消事务时，在回滚事务期间可能发生延迟。</span><span class="sxs-lookup"><span data-stu-id="a1b85-144">When transactions are canceled, delays might occur while transactions are rolled back.</span></span>  
  
 <span data-ttu-id="a1b85-145">Parse</span><span class="sxs-lookup"><span data-stu-id="a1b85-145">**Parse**</span></span>  
 <span data-ttu-id="a1b85-146">检查所选代码的语法。</span><span class="sxs-lookup"><span data-stu-id="a1b85-146">Check the syntax of the selected code.</span></span> <span data-ttu-id="a1b85-147">如果没有选择任何代码，则检查查询编辑器窗口中全部代码的语法。</span><span class="sxs-lookup"><span data-stu-id="a1b85-147">If no code is selected, checks the syntax of the all code in the Query Editor window.</span></span>  
  
 <span data-ttu-id="a1b85-148">**显示估计的执行计划**</span><span class="sxs-lookup"><span data-stu-id="a1b85-148">**Display Estimated Execution Plan**</span></span>  
 <span data-ttu-id="a1b85-149">从查询处理器中请求查询执行计划而不实际执行查询，并在“执行计划”  窗口中显示该计划。</span><span class="sxs-lookup"><span data-stu-id="a1b85-149">Requests a query execution plan from the query processor without actually executing the query, and displays the plan in the **Execution plan** window.</span></span> <span data-ttu-id="a1b85-150">此计划使用索引统计值作为查询执行的各个部分预期返回的行数估计值。</span><span class="sxs-lookup"><span data-stu-id="a1b85-150">This plan uses index statistics as an estimate of the number of rows that are expected to be returned during each part of the query execution.</span></span> <span data-ttu-id="a1b85-151">实际使用的查询计划可能与估计的执行计划不同。</span><span class="sxs-lookup"><span data-stu-id="a1b85-151">The actual query plan that is used can be different from the estimated execution plan.</span></span> <span data-ttu-id="a1b85-152">如果返回的行数与估计值有明显差距，并且查询处理器更改了执行计划以提高其效率，就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="a1b85-152">This can occur if the number of rows that are returned is significantly different from the estimate, and the query processor changes the plan to be more efficient.</span></span>  
  
 <span data-ttu-id="a1b85-153">**查询选项**</span><span class="sxs-lookup"><span data-stu-id="a1b85-153">**Query Options**</span></span>  
 <span data-ttu-id="a1b85-154">打开“查询选项”  对话框。</span><span class="sxs-lookup"><span data-stu-id="a1b85-154">Opens the **Query Options** dialog box.</span></span> <span data-ttu-id="a1b85-155">此对话框用于配置查询执行和查询结果的默认选项。</span><span class="sxs-lookup"><span data-stu-id="a1b85-155">Use this dialog box to configure the default options for query execution and for query results.</span></span>  
  
 <span data-ttu-id="a1b85-156">**IntelliSense 已启用**</span><span class="sxs-lookup"><span data-stu-id="a1b85-156">**IntelliSense Enabled**</span></span>  
 <span data-ttu-id="a1b85-157">指定 IntelliSense 功能在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器中是否可用。</span><span class="sxs-lookup"><span data-stu-id="a1b85-157">Specifies whether IntelliSense functionality is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="a1b85-158">**包含实际的执行计划**</span><span class="sxs-lookup"><span data-stu-id="a1b85-158">**Include Actual Execution Plan**</span></span>  
 <span data-ttu-id="a1b85-159">执行查询，返回查询结果和用于查询的执行计划。</span><span class="sxs-lookup"><span data-stu-id="a1b85-159">Executes the query, returns the query results, and the execution plan that was used for the query.</span></span> <span data-ttu-id="a1b85-160">这些内容在 **“执行计划”** 窗口中显示为图形查询计划。</span><span class="sxs-lookup"><span data-stu-id="a1b85-160">These appear as a graphical query plan in the **Execution plan** window.</span></span>  
  
 <span data-ttu-id="a1b85-161">**包括客户端统计信息**</span><span class="sxs-lookup"><span data-stu-id="a1b85-161">**Include Client Statistics**</span></span>  
 <span data-ttu-id="a1b85-162">提供一个“客户端统计信息”  窗口，其中包含有关查询、网络数据包以及查询占用时间的统计信息。</span><span class="sxs-lookup"><span data-stu-id="a1b85-162">Includes a **Client Statistics** window that contains statistics about the query and about the network packets, and the elapsed time of the query.</span></span>  
  
 <span data-ttu-id="a1b85-163">**以文本格式显示结果**</span><span class="sxs-lookup"><span data-stu-id="a1b85-163">**Results to Text**</span></span>  
 <span data-ttu-id="a1b85-164">在“结果”  窗口中以文本格式返回查询结果。</span><span class="sxs-lookup"><span data-stu-id="a1b85-164">Returns the query results as text in the **Results** window.</span></span>  
  
 <span data-ttu-id="a1b85-165">**以网格显示结果**</span><span class="sxs-lookup"><span data-stu-id="a1b85-165">**Results to Grid**</span></span>  
 <span data-ttu-id="a1b85-166">在“结果”  窗口中以一个或多个网格的形式返回查询结果。</span><span class="sxs-lookup"><span data-stu-id="a1b85-166">Returns the query results as one or more grids in the **Results** window.</span></span>  
  
 <span data-ttu-id="a1b85-167">**将结果保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a1b85-167">**Results to File**</span></span>  
 <span data-ttu-id="a1b85-168">在执行查询时，“保存结果”  对话框将会打开。</span><span class="sxs-lookup"><span data-stu-id="a1b85-168">When the query executes, the **Save Results** dialog box opens.</span></span> <span data-ttu-id="a1b85-169">在 **“保存于”** 中，选择要将文件保存到的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a1b85-169">In **Save In**, select the folder in which you want to save the file.</span></span> <span data-ttu-id="a1b85-170">在 **“文件名”** 中键入文件名，然后单击 **“保存”** 将查询结果保存为具有 .rpt 扩展名的 **“报表”** 文件。</span><span class="sxs-lookup"><span data-stu-id="a1b85-170">In **File name**, type the name of the file, and then click **Save** to save the query results as a **Report** file that has the .rpt extension.</span></span> <span data-ttu-id="a1b85-171">对于高级选项，请单击“保存”\*\*\*\* 按钮上的向下箭头，再单击“编码保存”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1b85-171">For advanced options, click the down-arrow on the **Save** button, and then click **Save with Encoding**.</span></span>  
  
 <span data-ttu-id="a1b85-172">**注释选定内容**</span><span class="sxs-lookup"><span data-stu-id="a1b85-172">**Comment Selection**</span></span>  
 <span data-ttu-id="a1b85-173">在当前行的开头处添加一个注释运算符 (--)，以对该行进行注释。</span><span class="sxs-lookup"><span data-stu-id="a1b85-173">Makes the current line a comment by adding a comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="a1b85-174">**取消注释选定内容**</span><span class="sxs-lookup"><span data-stu-id="a1b85-174">**Uncomment Selection**</span></span>  
 <span data-ttu-id="a1b85-175">删除当前行开头处的任何注释运算符 (--)，以使该行成为一个活动的源语句。</span><span class="sxs-lookup"><span data-stu-id="a1b85-175">Makes the current line an active source statement by removing any comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="a1b85-176">**减少行缩进**</span><span class="sxs-lookup"><span data-stu-id="a1b85-176">**Decrease Line Indent**</span></span>  
 <span data-ttu-id="a1b85-177">删除行开头处的空格，从而使该行文本向左移动。</span><span class="sxs-lookup"><span data-stu-id="a1b85-177">Moves the text of the line to the left by removing blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="a1b85-178">**增加行缩进**</span><span class="sxs-lookup"><span data-stu-id="a1b85-178">**Increase Line Indent**</span></span>  
 <span data-ttu-id="a1b85-179">在行开头处插入空格，从而使该行文本向右移动。</span><span class="sxs-lookup"><span data-stu-id="a1b85-179">Moves the text of the line to the right by adding blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="a1b85-180">**指定模板参数的值**</span><span class="sxs-lookup"><span data-stu-id="a1b85-180">**Specify Values for Template Parameters**</span></span>  
 <span data-ttu-id="a1b85-181">打开一个对话框，在此对话框中可以指定存储过程或函数中参数的值。</span><span class="sxs-lookup"><span data-stu-id="a1b85-181">Opens a dialog box that you can use to specify values for parameters in stored procedures and functions.</span></span>  
  
 <span data-ttu-id="a1b85-182">通过依次选择 **“视图”** 菜单、 **“工具栏”** 和 **“SQL 编辑器”** ，还可添加 SQL 编辑器工具栏。</span><span class="sxs-lookup"><span data-stu-id="a1b85-182">You can also add the SQL Editor toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **SQL Editor**.</span></span> <span data-ttu-id="a1b85-183">如果在没有打开任何 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口时添加 SQL 编辑器工具栏，则所有按钮都不可用。</span><span class="sxs-lookup"><span data-stu-id="a1b85-183">If you add the SQL Editor toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="a1b85-184">SQL 编辑器工具栏</span><span class="sxs-lookup"><span data-stu-id="a1b85-184">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="a1b85-185">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口打开后，可以通过以下方法添加调试工具栏：在 **“视图”** 菜单上选择 **“工具栏”**，然后选择 **“调试”**。</span><span class="sxs-lookup"><span data-stu-id="a1b85-185">When a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is open, you can add the Debug toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **Debug**.</span></span> <span data-ttu-id="a1b85-186">如果在没有打开任何 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口的情况下添加调试工具栏，则所有按钮都不可用。</span><span class="sxs-lookup"><span data-stu-id="a1b85-186">If you add the Debug toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
 <span data-ttu-id="a1b85-187">**Continue**</span><span class="sxs-lookup"><span data-stu-id="a1b85-187">**Continue**</span></span>  
 <span data-ttu-id="a1b85-188">运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口中的代码，直到遇到断点。</span><span class="sxs-lookup"><span data-stu-id="a1b85-188">Runs the code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window until a breakpoint is encountered.</span></span>  
  
 <span data-ttu-id="a1b85-189">**全部中断**</span><span class="sxs-lookup"><span data-stu-id="a1b85-189">**Break All**</span></span>  
 <span data-ttu-id="a1b85-190">将调试器设置为发生中断时中断调试器附加到的所有进程。</span><span class="sxs-lookup"><span data-stu-id="a1b85-190">Sets the debugger to break all processes to which the debugger is attached when a break occurs.</span></span>  
  
 <span data-ttu-id="a1b85-191">**停止调试**</span><span class="sxs-lookup"><span data-stu-id="a1b85-191">**Stop Debugging**</span></span>  
 <span data-ttu-id="a1b85-192">使选定的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口脱离调试模式，并还原标准执行模式。</span><span class="sxs-lookup"><span data-stu-id="a1b85-192">Takes the selected [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window out of debug mode, and restores the standard execution mode.</span></span>  
  
 <span data-ttu-id="a1b85-193">**显示下一语句**</span><span class="sxs-lookup"><span data-stu-id="a1b85-193">**Show Next Statement**</span></span>  
 <span data-ttu-id="a1b85-194">将光标移动到要执行的下一个语句。</span><span class="sxs-lookup"><span data-stu-id="a1b85-194">Moves the cursor to the next statement to be executed.</span></span>  
  
 <span data-ttu-id="a1b85-195">**逐语句**</span><span class="sxs-lookup"><span data-stu-id="a1b85-195">**Step Into**</span></span>  
 <span data-ttu-id="a1b85-196">运行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="a1b85-196">The next statement is run.</span></span> <span data-ttu-id="a1b85-197">如果该语句调用 Transact-SQL 存储过程、函数或触发器，则调试器会显示一个包含该模块的代码的新“查询编辑器”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="a1b85-197">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the debugger displays a new **Query Editor** window that contains the code of the module.</span></span> <span data-ttu-id="a1b85-198">该窗口处于调试模式，并在模块中的第一个语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="a1b85-198">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="a1b85-199">然后，您可以在模块中移动，例如，设置断点或逐句通过代码。</span><span class="sxs-lookup"><span data-stu-id="a1b85-199">You can then move through the module, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="a1b85-200">**逐过程**</span><span class="sxs-lookup"><span data-stu-id="a1b85-200">**Step Over**</span></span>  
 <span data-ttu-id="a1b85-201">运行下一个语句。</span><span class="sxs-lookup"><span data-stu-id="a1b85-201">The next statement is run.</span></span> <span data-ttu-id="a1b85-202">如果该语句调用了 Transact-SQL 存储过程、函数或触发器，则模块会运行，直到完成运行，并将结果返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="a1b85-202">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the module is run until it finishes and the results are returned to the calling code.</span></span> <span data-ttu-id="a1b85-203">如果确认模块中没有错误，可以逐过程执行。</span><span class="sxs-lookup"><span data-stu-id="a1b85-203">If you are sure there are no errors in the module, you can step over it.</span></span> <span data-ttu-id="a1b85-204">在调用模块的后面的语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="a1b85-204">Execution pauses on the statement that follows the call to the module.</span></span>  
  
 <span data-ttu-id="a1b85-205">**跳出**</span><span class="sxs-lookup"><span data-stu-id="a1b85-205">**Step Out**</span></span>  
 <span data-ttu-id="a1b85-206">后退到下一个最高调用级别（函数、存储过程或触发器）。</span><span class="sxs-lookup"><span data-stu-id="a1b85-206">Step back to the next highest calling level (function, stored procedure, or trigger).</span></span> <span data-ttu-id="a1b85-207">在调用存储过程、函数或触发器的后面的语句上暂停执行。</span><span class="sxs-lookup"><span data-stu-id="a1b85-207">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
 <span data-ttu-id="a1b85-208">**Windows**</span><span class="sxs-lookup"><span data-stu-id="a1b85-208">**Windows**</span></span>  
 <span data-ttu-id="a1b85-209">打开“断点”\*\*\*\* 窗口或“即时”\*\*\*\* 窗口。</span><span class="sxs-lookup"><span data-stu-id="a1b85-209">Opens either the **Breakpoint** window or the **Immediate** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b85-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1b85-210">See Also</span></span>  
 [<span data-ttu-id="a1b85-211">SQL Server Management Studio 键盘快捷键</span><span class="sxs-lookup"><span data-stu-id="a1b85-211">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
