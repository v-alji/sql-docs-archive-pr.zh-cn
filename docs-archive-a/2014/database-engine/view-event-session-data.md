---
title: 查看事件会话数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eaeb5fd22b95b8f1056b8dce9e3c7d683b52602f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693440"
---
# <a name="view-event-session-data"></a><span data-ttu-id="cd320-102">查看事件会话数据</span><span class="sxs-lookup"><span data-stu-id="cd320-102">View Event Session Data</span></span>
  <span data-ttu-id="cd320-103">本主题介绍如何使用显示用户界面查看和分析扩展的事件数据：</span><span class="sxs-lookup"><span data-stu-id="cd320-103">This topic describes using the display user interface to see and analyze extended event data:</span></span>  
  
-   <span data-ttu-id="cd320-104">查看目标数据</span><span class="sxs-lookup"><span data-stu-id="cd320-104">View Target Data</span></span>  
  
-   <span data-ttu-id="cd320-105">处理数据</span><span class="sxs-lookup"><span data-stu-id="cd320-105">Working With Data</span></span>  
  
## <a name="view-target-data"></a><span data-ttu-id="cd320-106">查看目标数据</span><span class="sxs-lookup"><span data-stu-id="cd320-106">View Target Data</span></span>  
 <span data-ttu-id="cd320-107">您可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中显示收集到指定目标内的数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-107">You can display the data collected into the specified target within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-target-data"></a><span data-ttu-id="cd320-108">查看目标数据</span><span class="sxs-lookup"><span data-stu-id="cd320-108">View Target Data</span></span>  
 <span data-ttu-id="cd320-109">查看目标数据：</span><span class="sxs-lookup"><span data-stu-id="cd320-109">To view target data:</span></span>  
  
1.  <span data-ttu-id="cd320-110">在对象资源管理器中，依次展开 **“管理”**、 **“扩展事件”** 和 **“会话”**，然后选择一个会话。</span><span class="sxs-lookup"><span data-stu-id="cd320-110">In Object Explorer, expand **Management**, **Extended Events**, **Sessions**, and then a session.</span></span>  
  
2.  <span data-ttu-id="cd320-111">右键单击目标名称，然后单击 **“查看目标数据”** 以显示目标数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-111">Right-click the target name, and then click **View Target Data** to display the target data.</span></span>  
  
     <span data-ttu-id="cd320-112">目标数据窗口将显示在默认视图中并显示目标数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-112">The target data window appears in default view and displays the target data.</span></span>  
  
 <span data-ttu-id="cd320-113">关于查看目标数据的注释：</span><span class="sxs-lookup"><span data-stu-id="cd320-113">Notes on viewing target data:</span></span>  
  
-   <span data-ttu-id="cd320-114">目标数据对于 ETW 目标不可用。</span><span class="sxs-lookup"><span data-stu-id="cd320-114">Target data is not available for the ETW target.</span></span>  
  
-   <span data-ttu-id="cd320-115">若要查看 xml 格式的 ring_buffer 数据，请在目标数据窗口中单击 **“ring_buffer 目标数据”** 链接。</span><span class="sxs-lookup"><span data-stu-id="cd320-115">To view the ring_buffer data in xml format, in the target data window click the **ring_buffer target data** link.</span></span> <span data-ttu-id="cd320-116">ring_buffer.xml 文件将显示在 xml 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="cd320-116">The ring_buffer.xml file appears in the xml editor.</span></span>  
  
-   <span data-ttu-id="cd320-117">对于 event_file 目标，请使用以下方法之一查看文件目标数据（.XEL 文件）：</span><span class="sxs-lookup"><span data-stu-id="cd320-117">For an event_file target, view the file target data (.XEL file) using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="cd320-118">使用打开的文件 > [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd320-118">Use File -> Open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>
    
    -   <span data-ttu-id="cd320-119">将文件拖放到中 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd320-119">Drag and drop the file into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> 
    
    -   <span data-ttu-id="cd320-120">双击 .XEL 文件。</span><span class="sxs-lookup"><span data-stu-id="cd320-120">Double click the .XEL file.</span></span>  
    
    -   <span data-ttu-id="cd320-121">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，右键单击正在运行的扩展事件会话，然后选择“查看目标数据”。</span><span class="sxs-lookup"><span data-stu-id="cd320-121">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right click on a running Extended Events session and select View Target Data.</span></span> 
    
    -   <span data-ttu-id="cd320-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd320-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>
    
    -   <span data-ttu-id="cd320-123">使用[SQLServer 模块](https://www.powershellgallery.com/packages/SqlServer.XEvent)中的 Powershell SQLXevent。</span><span class="sxs-lookup"><span data-stu-id="cd320-123">Use Powershell Read-SQLXevent in [SQLServer.XEvent module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
    
    -   <span data-ttu-id="cd320-124">使用[XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite)以编程方式使用 XEvents。</span><span class="sxs-lookup"><span data-stu-id="cd320-124">Programmatically consume XEvents by using the [XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite).</span></span>
    
    -   <span data-ttu-id="cd320-125">你可以查看多个。.XEL 文件，方法是从文件 > 打开 "菜单中选择"**合并扩展事件文件**"。</span><span class="sxs-lookup"><span data-stu-id="cd320-125">You can view more than one .XEL file by selecting **Merge Extended Event Files** from the File -> Open menu.</span></span>

### <a name="watching-live-data"></a><span data-ttu-id="cd320-126">查看实时数据</span><span class="sxs-lookup"><span data-stu-id="cd320-126">Watching Live Data</span></span>  
 <span data-ttu-id="cd320-127">您可以查看正在捕获的实时数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-127">You can watch live data as it is being captured.</span></span>  
  
-   <span data-ttu-id="cd320-128">在对象资源管理器中，依次展开 "**管理**"、"**扩展事件**" 和 "**会话**" 节点。</span><span class="sxs-lookup"><span data-stu-id="cd320-128">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  

-   <span data-ttu-id="cd320-129">右键单击该会话名称，然后单击 **“查看实时数据”** 以开始显示跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-129">Right-click the session name and then click **Watch Live Data** to start displaying the tracing data.</span></span>  
  
     <span data-ttu-id="cd320-130">默认显示 **“事件名称”** 和 **“时间戳”** 列。</span><span class="sxs-lookup"><span data-stu-id="cd320-130">The default display columns are **Event Name** and **TimeStamp**.</span></span>  
  
     <span data-ttu-id="cd320-131">若要将其他列添加到跟踪窗口，请单击扩展事件工具栏上的 **“选择列”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cd320-131">To add additional columns to the trace window, click the **Choose Columns** button on the Extended Events toolbar.</span></span> <span data-ttu-id="cd320-132">**“详细信息”** 选项卡显示所选事件的所有事件详细信息。</span><span class="sxs-lookup"><span data-stu-id="cd320-132">The **Details** tab shows all of the event details for the selected event.</span></span>  
  
     <span data-ttu-id="cd320-133">事件通常在大约 30 秒后显示。</span><span class="sxs-lookup"><span data-stu-id="cd320-133">Events are usually displayed in approximately 30 seconds.</span></span> <span data-ttu-id="cd320-134">如果要更改滞后期，可以在 **“新建会话”** 对话框的 **“高级”** 页中更改 **“最大调度滞后时间”** 。</span><span class="sxs-lookup"><span data-stu-id="cd320-134">If you want to change the latency period, you can change the **Maximum dispatch latency** on the **Advanced** page of the of the **New Session** dialog.</span></span>  
     
-    <span data-ttu-id="cd320-135">可以通过[SqlServer PowerShell 模块](https://www.powershellgallery.com/packages/SqlServer.XEvent)对实时数据进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="cd320-135">Live data can be streamed by the [SqlServer.XEvent PowerShell module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
     
### <a name="to-refresh-target-data"></a><span data-ttu-id="cd320-136">刷新目标数据</span><span class="sxs-lookup"><span data-stu-id="cd320-136">To Refresh Target Data</span></span>  
 <span data-ttu-id="cd320-137">event_files 目标不支持刷新目标数据：</span><span class="sxs-lookup"><span data-stu-id="cd320-137">Refreshing target data is not supported for event_files targets:</span></span>  
  
1.  <span data-ttu-id="cd320-138">若要自动刷新目标数据，请右键单击目标数据，选择 **“刷新间隔”**，然后从间隔列表中选择刷新间隔。</span><span class="sxs-lookup"><span data-stu-id="cd320-138">To refresh the target data automatically, right click the target data, select **Refresh Interval**, and then select the refresh interval from the interval list.</span></span>  
  
2.  <span data-ttu-id="cd320-139">若要暂停和继续自动刷新，请右键单击目标数据，然后选择 **“暂停”** 或 **“继续”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-139">To pause and resume the automatic refresh, right-click the target data and then select **Pause** or **Resume**.</span></span>  
  
3.  <span data-ttu-id="cd320-140">若要手动刷新目标数据，请右键单击目标数据，然后选择 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-140">To refresh the target data manually, right click the target data, and then select **Refresh**.</span></span>  
  
## <a name="working-with-data"></a><span data-ttu-id="cd320-141">处理数据</span><span class="sxs-lookup"><span data-stu-id="cd320-141">Working With Data</span></span>  
 <span data-ttu-id="cd320-142">您可以使用扩展事件用户界面的分析能力找出问题。</span><span class="sxs-lookup"><span data-stu-id="cd320-142">You can use the analysis capabilities of the Extended Events user interface to identify problems.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="cd320-143">“详细信息”窗格</span><span class="sxs-lookup"><span data-stu-id="cd320-143">Details Pane</span></span>  
 <span data-ttu-id="cd320-144">**“详细信息”** 窗格显示选定事件的所有列，包括字段和操作。</span><span class="sxs-lookup"><span data-stu-id="cd320-144">The **Details** pane shows all the columns for the selected event, including fields and actions.</span></span> <span data-ttu-id="cd320-145">通过在 **“详细信息”** 窗格中右键单击某一行，再选择 **“显示表中的列”**，可以向目标数据表添加列。</span><span class="sxs-lookup"><span data-stu-id="cd320-145">You can add a column to the target data table by right-clicking a row in the **Details** pane and selecting **Show Column in Table**.</span></span>  
  
### <a name="create-modify-or-delete-merged-columns"></a><span data-ttu-id="cd320-146">创建、修改或删除合并列</span><span class="sxs-lookup"><span data-stu-id="cd320-146">Create, Modify, or Delete Merged Columns</span></span>  
 <span data-ttu-id="cd320-147">合并列允许您将要显示的一组字段合并到一列中。</span><span class="sxs-lookup"><span data-stu-id="cd320-147">A merged column allows you to combine a set of fields to be displayed in a single column.</span></span> <span data-ttu-id="cd320-148">合并列将依据各字段添加到字段列表中的顺序从第一个非 NULL 字段开始显示数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-148">The merged column will show the data from the first non-NULL field based on the order they are added to the field list.</span></span> <span data-ttu-id="cd320-149">这类似于您在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler 中看到的数据，其中的特定列可能根据事件显示不同的数据（最常见的例子是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler 中的 TextData 字段）。</span><span class="sxs-lookup"><span data-stu-id="cd320-149">This is similar to what you see in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, where a specific column may show different data depending on the event (the most common example of this is the TextData field in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler).</span></span> <span data-ttu-id="cd320-150">例如，您可以将 sql_statement_completed 事件中的 statement 字段和 sql_batch_completed 事件中的 batch_text 字段合并到名为 myStatement 的字段中。</span><span class="sxs-lookup"><span data-stu-id="cd320-150">For an example, you could merge the statement and batch_text fields from the sql_statement_completed and sql_batch_completed events, respectively, into a field named myStatement.</span></span> <span data-ttu-id="cd320-151">在表中显示 myStatement 列时，它将显示所关联事件的相应数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-151">When you display the myStatement column in the table it will show the appropriate data for the associated event.</span></span>  
  
 <span data-ttu-id="cd320-152">您可以创建、修改或删除合并列：</span><span class="sxs-lookup"><span data-stu-id="cd320-152">You can create, modify, or delete merged columns:</span></span>  
  
1.  <span data-ttu-id="cd320-153">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-153">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-154"> (你还可以右键单击会话名称，然后选择 "**查看实时数据**"。 ) </span><span class="sxs-lookup"><span data-stu-id="cd320-154">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="cd320-155">在跟踪结果窗口中，右键单击列标题，然后单击 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-155">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
 <span data-ttu-id="cd320-156">若要创建合并列，请单击 **“选择列”** 对话框中的 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="cd320-156">To create a merged column, click **New** in the **Choose Columns** dialog box.</span></span>  <span data-ttu-id="cd320-157">在 **“新建合并列”** 对话框中，为该合并列命名并选择要纳入合并列的原始列。</span><span class="sxs-lookup"><span data-stu-id="cd320-157">In the **New Merged Column** dialog, name the merged column and select the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="cd320-158">若要编辑合并列，请在 **“选择列”** 对话框中选择某个合并列，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-158">To edit a merged column, select a merged column in the **Choose Columns** dialog and click **Edit**.</span></span> <span data-ttu-id="cd320-159">在 **“编辑合并列”** 对话框中，重命名该合并列或修改要纳入该合并列的原始列。</span><span class="sxs-lookup"><span data-stu-id="cd320-159">In the **Edit Merged Column** dialog, rename the merged column or modify the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="cd320-160">若要删除合并列，请在 **“选择列”** 对话框中选择某一合并列，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-160">To delete a merged column, select a merged column in the **Choose Columns** dialog and click **Delete**.</span></span>  
  
### <a name="filter-results"></a><span data-ttu-id="cd320-161">筛选结果</span><span class="sxs-lookup"><span data-stu-id="cd320-161">Filter Results</span></span>  
 <span data-ttu-id="cd320-162">您可以查看跟踪结果，然后应用筛选器以缩小跟踪窗口中显示的跟踪结果的范围。</span><span class="sxs-lookup"><span data-stu-id="cd320-162">You can view trace results, and then apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="cd320-163">显示筛选器包括时间筛选器和高级筛选器。</span><span class="sxs-lookup"><span data-stu-id="cd320-163">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="cd320-164">您可以使用时间筛选器按事件时间戳筛选跟踪结果，也可以使用高级筛选器通过事件字段和操作构造筛选条件。</span><span class="sxs-lookup"><span data-stu-id="cd320-164">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="cd320-165">时间筛选器和高级筛选器之间存在“and”关系。</span><span class="sxs-lookup"><span data-stu-id="cd320-165">There is an "and" relationship between the time and advanced filters.</span></span>  
  
 <span data-ttu-id="cd320-166">若要创建筛选器，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cd320-166">To create a filter:</span></span>  
  
1.  <span data-ttu-id="cd320-167">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-167">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-168"> (你还可以右键单击会话名称，然后选择 "**查看实时数据**"。 ) </span><span class="sxs-lookup"><span data-stu-id="cd320-168">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="cd320-169">在跟踪结果窗口中选择要筛选的结果，然后在 **“扩展事件”** 工具栏上单击 **“筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-169">In the trace results window, select the results you want to filter, and then on the **Extended Events** toolbar, click **Filters**.</span></span>  
  
3.  <span data-ttu-id="cd320-170">在 **“筛选器”** 对话框中，选择 **“设置时间筛选器”** 以通过拖动滑动条或在编辑框中修改时间来设置时间筛选器。</span><span class="sxs-lookup"><span data-stu-id="cd320-170">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars or modifying the time in the edit box.</span></span>  
  
4.  <span data-ttu-id="cd320-171">在 "**其他筛选器**" 部分中，应用筛选条件，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="cd320-171">In the **Additional filters** section, apply your filter criteria, and then click **Apply**.</span></span>  
  
### <a name="sort-results"></a><span data-ttu-id="cd320-172">对结果排序</span><span class="sxs-lookup"><span data-stu-id="cd320-172">Sort Results</span></span>  
 <span data-ttu-id="cd320-173">按升序或降序对结果排序：</span><span class="sxs-lookup"><span data-stu-id="cd320-173">To sort results either in ascending or descending order:</span></span>  
  
1.  <span data-ttu-id="cd320-174">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-174">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-175"> (你还可以右键单击会话名称，选择 "**查看实时数据**"，然后单击工具栏上的 "**停止数据馈送**" 按钮。 ) </span><span class="sxs-lookup"><span data-stu-id="cd320-175">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="cd320-176">在跟踪结果窗口中，右键单击要排序的列标题，然后单击 **“升序排序”** 或 **“降序排序”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-176">In the trace results window, right-click the column heading you want to sort and click **Sort Ascending** or **Sort Descending**.</span></span>  
  
 <span data-ttu-id="cd320-177">还可以单击列标题以反转排序顺序。</span><span class="sxs-lookup"><span data-stu-id="cd320-177">You can also click the column header to reverse the sort order.</span></span>  
  
 <span data-ttu-id="cd320-178">如果已对列进行分组，则对某个列进行排序将只对组中的数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="cd320-178">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
### <a name="group-results"></a><span data-ttu-id="cd320-179">对结果进行分组</span><span class="sxs-lookup"><span data-stu-id="cd320-179">Group Results</span></span>  
 <span data-ttu-id="cd320-180">分组的结果等效于 [!INCLUDE[tsql](../includes/tsql-md.md)] 中 `GROUP BY` 子句的功能。</span><span class="sxs-lookup"><span data-stu-id="cd320-180">Grouped results are equivalent to the functionality of the `GROUP BY` clause in [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="cd320-181">目标数据表将显示组合在一起的数据，允许您展开和折叠数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-181">The target data table will show the data grouped together, allowing you to expand and collapse the data.</span></span>  
  
 <span data-ttu-id="cd320-182">您必须先对数据进行分组，之后才能聚合数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-182">You must group data before you can aggregate it.</span></span> <span data-ttu-id="cd320-183">例如，您可以基于 query_hash 值进行分组，然后按持续时间降序排序，获取每个组的平均持续时间，然后对聚合结果降序排序。</span><span class="sxs-lookup"><span data-stu-id="cd320-183">For example, you can group on the query_hash value, sort descending by duration, get the average duration for each group, and then sort descending on the aggregation.</span></span>  <span data-ttu-id="cd320-184">这将生成一个列表，显示从最长到最短的平均持续时间排序的唯一语句列表。</span><span class="sxs-lookup"><span data-stu-id="cd320-184">This will produce a list that shows the list of unique statements from longest to shortest average duration.</span></span> <span data-ttu-id="cd320-185">展开顶部分组后，您会看到该特定查询按最长到最短持续时间排序的各次执行情况。</span><span class="sxs-lookup"><span data-stu-id="cd320-185">When you expand the top group you will see the individual executions of that specific query sorted from longest to shortest.</span></span>  
  
 <span data-ttu-id="cd320-186">您可以按一列或多列对结果分组。</span><span class="sxs-lookup"><span data-stu-id="cd320-186">You can group results by a single column or by multiple columns.</span></span>  
  
 <span data-ttu-id="cd320-187">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-187">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-188"> (你还可以右键单击会话名称，选择 "**查看实时数据**"，然后单击工具栏上的 "**停止数据馈送**" 按钮。 ) </span><span class="sxs-lookup"><span data-stu-id="cd320-188">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
 <span data-ttu-id="cd320-189">若要按一列对结果分组，请右键单击跟踪结果窗口中的列标题，然后单击 **“按此列分组”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-189">To group results by a single column, right-click the column heading in the trace results window, and click **Group by this Column**.</span></span> <span data-ttu-id="cd320-190">若要撤消该分组，选择其中某一行，然后单击 **“删除所有分组”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-190">To undo the grouping, select one of the rows and click **Remove All Groupings**.</span></span>  
  
 <span data-ttu-id="cd320-191">若要按多个列对结果分组，请单击 **“扩展事件”** 工具栏上的 **“分组”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cd320-191">To group results by a multiple columns, click the **Grouping** button on the **Extended Events** toolbar.</span></span> <span data-ttu-id="cd320-192">在 **“分组”** 对话框的 **“可用列”** 框中，选择要分组的列，然后将其移入 **“列分组依据”** 框。</span><span class="sxs-lookup"><span data-stu-id="cd320-192">In the **Available columns** box of the **Grouping** dialog, select the columns you want to group, and move them into the **Columns grouped on** box.</span></span> <span data-ttu-id="cd320-193">若要更改 **“列分组依据”** 框中的顺序，请单击向上箭头或向下箭头。</span><span class="sxs-lookup"><span data-stu-id="cd320-193">To change the order in the **Columns grouped on** box, click the up or down arrows.</span></span>  
  
### <a name="aggregate-results"></a><span data-ttu-id="cd320-194">聚合结果</span><span class="sxs-lookup"><span data-stu-id="cd320-194">Aggregate Results</span></span>  
 <span data-ttu-id="cd320-195">您可以查看跟踪结果，然后通过聚合结果中的列来进一步分析事件数据。</span><span class="sxs-lookup"><span data-stu-id="cd320-195">You can view the trace results, and then further analyze your event data by aggregating columns in your results.</span></span> <span data-ttu-id="cd320-196">扩展事件支持五个聚合函数：</span><span class="sxs-lookup"><span data-stu-id="cd320-196">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="cd320-197">sum</span><span class="sxs-lookup"><span data-stu-id="cd320-197">sum</span></span>  
  
-   <span data-ttu-id="cd320-198">分钟</span><span class="sxs-lookup"><span data-stu-id="cd320-198">min</span></span>  
  
-   <span data-ttu-id="cd320-199">max</span><span class="sxs-lookup"><span data-stu-id="cd320-199">max</span></span>  
  
-   <span data-ttu-id="cd320-200">average</span><span class="sxs-lookup"><span data-stu-id="cd320-200">average</span></span>  
  
-   <span data-ttu-id="cd320-201">计数</span><span class="sxs-lookup"><span data-stu-id="cd320-201">count</span></span>  
  
 <span data-ttu-id="cd320-202">sum、min、max 和 average 只能用于数值列。</span><span class="sxs-lookup"><span data-stu-id="cd320-202">Sum, min, max, and average can only be used with numeric columns.</span></span> <span data-ttu-id="cd320-203">count 是组中所选列存在的非 null 值的数量。</span><span class="sxs-lookup"><span data-stu-id="cd320-203">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
 <span data-ttu-id="cd320-204">由于聚合针对组执行，因此，您必须先对结果进行分组，然后才能执行聚合。</span><span class="sxs-lookup"><span data-stu-id="cd320-204">Aggregation is performed on a group, so you must group the results before you can perform the aggregation.</span></span> <span data-ttu-id="cd320-205">聚合结果：</span><span class="sxs-lookup"><span data-stu-id="cd320-205">To aggregate results:</span></span>  
  
1.  <span data-ttu-id="cd320-206">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-206">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-207"> (你还可以右键单击会话名称，选择 "**查看实时数据**"，然后单击工具栏上的 "**停止数据馈送**" 按钮。 ) </span><span class="sxs-lookup"><span data-stu-id="cd320-207">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="cd320-208">在 **“扩展事件”** 工具栏上，单击 **“聚合”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cd320-208">On the **Extended Events** toolbar, click the **Aggregation** button.</span></span> <span data-ttu-id="cd320-209">“聚合”对话框将显示可用于聚合的列。</span><span class="sxs-lookup"><span data-stu-id="cd320-209">The Aggregation dialog box will display the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="cd320-210">在 **“聚合类型”** 列中，选择聚合类型。</span><span class="sxs-lookup"><span data-stu-id="cd320-210">In the **Aggregation Type** column, select the aggregation type.</span></span>  
  
4.  <span data-ttu-id="cd320-211">在 **“聚合排序依据”** 框中，选择排序列。</span><span class="sxs-lookup"><span data-stu-id="cd320-211">In the **Sort aggregation by** box, select the sort column.</span></span> <span data-ttu-id="cd320-212">然后选择升序或降序。</span><span class="sxs-lookup"><span data-stu-id="cd320-212">Then select ascending or descending order.</span></span>  
  
### <a name="search-for-text-in-columns"></a><span data-ttu-id="cd320-213">在列中搜索文本</span><span class="sxs-lookup"><span data-stu-id="cd320-213">Search for Text in Columns</span></span>  
 <span data-ttu-id="cd320-214">您可以在列中搜索文本：</span><span class="sxs-lookup"><span data-stu-id="cd320-214">You can search for text in columns:</span></span>  
  
1.  <span data-ttu-id="cd320-215">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-215">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-216">（您还可以右键单击会话名称，然后选择 **“查看实时数据”**。）</span><span class="sxs-lookup"><span data-stu-id="cd320-216">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="cd320-217">单击 **“扩展事件”** 工具栏上的 **“查找”** 。</span><span class="sxs-lookup"><span data-stu-id="cd320-217">Click **Find** on the **Extended Events** toolbar.</span></span>  
  
3.  <span data-ttu-id="cd320-218">在 **“在扩展事件中查找”** 对话框的 **“查找内容”** 框中，输入搜索文本。</span><span class="sxs-lookup"><span data-stu-id="cd320-218">In the **Find what** box of the **Find in Extended Events** dialog box, enter the search text.</span></span> <span data-ttu-id="cd320-219">可以从下拉列表中选择最近搜索过的 20 个字符串之一。</span><span class="sxs-lookup"><span data-stu-id="cd320-219">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="cd320-220">在 **“查找范围”** 框中，选择要在其中搜索指定文本的位置。</span><span class="sxs-lookup"><span data-stu-id="cd320-220">In the **Look in** box, select the location to search for the specified text.</span></span> <span data-ttu-id="cd320-221">使用以下选项进行搜索：</span><span class="sxs-lookup"><span data-stu-id="cd320-221">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="cd320-222">表列。</span><span class="sxs-lookup"><span data-stu-id="cd320-222">Table Columns.</span></span> <span data-ttu-id="cd320-223">使用此选项可在跟踪窗口中搜索所有可见列。</span><span class="sxs-lookup"><span data-stu-id="cd320-223">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="cd320-224">详细信息。</span><span class="sxs-lookup"><span data-stu-id="cd320-224">Details.</span></span> <span data-ttu-id="cd320-225">使用此选项可搜索在打开 "**在扩展事件中查找**" 对话框之前已选择的跟踪窗口中 (升级和未升级) 的所有列。</span><span class="sxs-lookup"><span data-stu-id="cd320-225">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="cd320-226">*Event_column_name*。</span><span class="sxs-lookup"><span data-stu-id="cd320-226">*Event_column_name*.</span></span> <span data-ttu-id="cd320-227">使用此选项可在下拉列表的特定事件列中进行搜索。</span><span class="sxs-lookup"><span data-stu-id="cd320-227">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="cd320-228">使用以下选项可指定所需的定义搜索的方式：</span><span class="sxs-lookup"><span data-stu-id="cd320-228">Use the following options to specify how you want to define the search:</span></span>  
  
    -   <span data-ttu-id="cd320-229">匹配大小写。</span><span class="sxs-lookup"><span data-stu-id="cd320-229">Match case.</span></span> <span data-ttu-id="cd320-230">使用此选项可显示与“查找内容”框中输入文本的内容和大小写均匹配的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-230">Use this option to display the search results for the text you entered in the Find what box that are matched both by content and by case.</span></span>  
  
    -   <span data-ttu-id="cd320-231">全字匹配。</span><span class="sxs-lookup"><span data-stu-id="cd320-231">Match whole word.</span></span> <span data-ttu-id="cd320-232">使用此选项可仅显示与输入文本完全匹配的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-232">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    -   <span data-ttu-id="cd320-233">向上搜索。</span><span class="sxs-lookup"><span data-stu-id="cd320-233">Search up.</span></span> <span data-ttu-id="cd320-234">使用此选项可从光标位置向结果开头搜索。</span><span class="sxs-lookup"><span data-stu-id="cd320-234">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    -   <span data-ttu-id="cd320-235">使用。</span><span class="sxs-lookup"><span data-stu-id="cd320-235">Use.</span></span> <span data-ttu-id="cd320-236">使用此选项可解释“查找内容”框中输入的特殊字符和正则表达式。</span><span class="sxs-lookup"><span data-stu-id="cd320-236">Use this option to interpret the special characters and the regular expressions you entered in the Find what box.</span></span> <span data-ttu-id="cd320-237">特殊字符包括通配符 (\*) 和 (?)，用于表示一个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="cd320-237">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="cd320-238">正则表达式是用于定义搜索文本的模式的特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="cd320-238">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
    -   <span data-ttu-id="cd320-239">单击 **“查找下一个”** 可搜索在 **“查找内容”** 框中输入的下一个文本。</span><span class="sxs-lookup"><span data-stu-id="cd320-239">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="cd320-240">书签</span><span class="sxs-lookup"><span data-stu-id="cd320-240">Bookmarks</span></span>  
 <span data-ttu-id="cd320-241">为了便于返回到某一行，您可以对目标数据中的一个或多个行添加书签。</span><span class="sxs-lookup"><span data-stu-id="cd320-241">To make it easier to return to a row, you can bookmark one or more row(s) in the target data.</span></span> <span data-ttu-id="cd320-242">右键单击某一行可更改书签。</span><span class="sxs-lookup"><span data-stu-id="cd320-242">Right click on a row to change the bookmark.</span></span> <span data-ttu-id="cd320-243">使用 **“扩展事件”** 工具栏上的上一个按钮和下一个按钮可导航到带有书签的行。</span><span class="sxs-lookup"><span data-stu-id="cd320-243">Use the previous and next buttons on the **Extended Events** toolbar to navigate to bookmarked rows.</span></span>  
  
### <a name="change-display-settings"></a><span data-ttu-id="cd320-244">更改显示设置</span><span class="sxs-lookup"><span data-stu-id="cd320-244">Change Display Settings</span></span>  
 <span data-ttu-id="cd320-245">您可以将跟踪结果的列信息（列顺序、合并列和列宽）和筛选器信息保存到扩展事件显示设置文件（.viewsetting 文件）中。</span><span class="sxs-lookup"><span data-stu-id="cd320-245">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="cd320-246">在保存该文件后，您可以将其应用于跟踪结果中以便更改视图。</span><span class="sxs-lookup"><span data-stu-id="cd320-246">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
 <span data-ttu-id="cd320-247">更改显示设置：</span><span class="sxs-lookup"><span data-stu-id="cd320-247">To change the display settings:</span></span>  
  
1.  <span data-ttu-id="cd320-248">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="cd320-248">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="cd320-249">（您还可以右键单击会话名称，然后选择 **“查看实时数据”**。）</span><span class="sxs-lookup"><span data-stu-id="cd320-249">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="cd320-250">在 **“扩展事件”** 工具栏上，选择 **“显示设置”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-250">On the **Extended Events** toolbar, select **Display Settings**.</span></span> <span data-ttu-id="cd320-251">从下拉列表中选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="cd320-251">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="cd320-252">另存为。</span><span class="sxs-lookup"><span data-stu-id="cd320-252">Save as.</span></span> <span data-ttu-id="cd320-253">将跟踪结果的列和筛选器信息保存到 .viewsetting 文件中。</span><span class="sxs-lookup"><span data-stu-id="cd320-253">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="cd320-254">打开。</span><span class="sxs-lookup"><span data-stu-id="cd320-254">Open.</span></span> <span data-ttu-id="cd320-255">打开现有的 .viewsetting 文件。</span><span class="sxs-lookup"><span data-stu-id="cd320-255">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="cd320-256">打开最近的。</span><span class="sxs-lookup"><span data-stu-id="cd320-256">Open recent.</span></span> <span data-ttu-id="cd320-257">打开最近保存的 .viewsetting 文件。</span><span class="sxs-lookup"><span data-stu-id="cd320-257">Open a recently saved .viewsetting file.</span></span>  
  
### <a name="copy-or-export-trace-results"></a><span data-ttu-id="cd320-258">复制或导出跟踪结果</span><span class="sxs-lookup"><span data-stu-id="cd320-258">Copy or Export Trace Results</span></span>  
 <span data-ttu-id="cd320-259">可以将单元、行和详细信息从跟踪结果复制到所选行。</span><span class="sxs-lookup"><span data-stu-id="cd320-259">You can copy cells, rows, and details to selected rows from your trace results.</span></span> <span data-ttu-id="cd320-260">还可以将跟踪结果导出到以下对象：</span><span class="sxs-lookup"><span data-stu-id="cd320-260">You can also export your trace results to the following:</span></span>  
  
-   <span data-ttu-id="cd320-261">.XEL 文件</span><span class="sxs-lookup"><span data-stu-id="cd320-261">.XEL file</span></span>  
  
-   <span data-ttu-id="cd320-262">表</span><span class="sxs-lookup"><span data-stu-id="cd320-262">table</span></span>  
  
-   <span data-ttu-id="cd320-263">.CSV 文件</span><span class="sxs-lookup"><span data-stu-id="cd320-263">.CSV file</span></span>  
  
 <span data-ttu-id="cd320-264">若要复制跟踪结果，请选择某个单元格、一行或多行，右键单击并选择 **“复制”** ，然后选择 **“单元格”**、 **“行”** 或 **“详细信息”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-264">To copy trace results, select a cell, row, or rows, right click, select **Copy** and then **Cell**, **Row**, or **Details**.</span></span> <span data-ttu-id="cd320-265">扩展事件最多支持复制 1000 行。</span><span class="sxs-lookup"><span data-stu-id="cd320-265">Extended Events supports copying up to a maximum of 1000 rows.</span></span>  
  
 <span data-ttu-id="cd320-266">通过从 **的** “扩展事件” **菜单选项中选择** “导出到” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，您可以将跟踪结果导出到 .XEL 文件、表或 .CSV 文件。</span><span class="sxs-lookup"><span data-stu-id="cd320-266">You can export trace results to a .XEL file, table, or .CSV file by selecting **Export to** from the **Extended Events** menu option in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a><span data-ttu-id="cd320-267">查看死锁图和查询计划</span><span class="sxs-lookup"><span data-stu-id="cd320-267">View a Deadlock Graph and Query Plans</span></span>  
 <span data-ttu-id="cd320-268">可以查看“详细信息”窗格中的 **xml_deadlock_report** 死锁图，帮助解决死锁问题。</span><span class="sxs-lookup"><span data-stu-id="cd320-268">You can view the deadlock graph for **xml_deadlock_report** in the Details pane to help you troubleshoot deadlocks.</span></span> <span data-ttu-id="cd320-269">还可以查看以下事件的查询计划图：</span><span class="sxs-lookup"><span data-stu-id="cd320-269">You can also view query plan graphs for the following events:</span></span>  
  
-   <span data-ttu-id="cd320-270">query_post_compilation_showplan</span><span class="sxs-lookup"><span data-stu-id="cd320-270">query_post_compilation_showplan</span></span>  
  
-   <span data-ttu-id="cd320-271">query_pre_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="cd320-271">query_pre_execution_showplan</span></span>  
  
-   <span data-ttu-id="cd320-272">query_post_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="cd320-272">query_post_execution_showplan</span></span>  
  
 <span data-ttu-id="cd320-273">查看死锁图：</span><span class="sxs-lookup"><span data-stu-id="cd320-273">To view the deadlock graph:</span></span>  
  
-   <span data-ttu-id="cd320-274">在对象资源管理器中，依次展开 "**管理**"、"**扩展事件**" 和 "**会话**" 节点。</span><span class="sxs-lookup"><span data-stu-id="cd320-274">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
-   <span data-ttu-id="cd320-275">右键单击包含要查看的配置死锁事件的会话，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-275">Right-click the session that contains the configured deadlock event that you want to view, and select **Watch Live Data**.</span></span>  
  
-   <span data-ttu-id="cd320-276">选择死锁事件并在“详细信息”窗格的 **“死锁”** 选项卡上查看相关图形。</span><span class="sxs-lookup"><span data-stu-id="cd320-276">Select the deadlock event and view the graph on the **Deadlock** tab in the Details pane.</span></span>  
  
 <span data-ttu-id="cd320-277">查看查询计划图：</span><span class="sxs-lookup"><span data-stu-id="cd320-277">To view query plan graphs:</span></span>  
  
1.  <span data-ttu-id="cd320-278">在对象资源管理器中，依次展开 "**管理**"、"**扩展事件**" 和 "**会话**" 节点。</span><span class="sxs-lookup"><span data-stu-id="cd320-278">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="cd320-279">右键单击包含要查看的查询计划图的会话（例如 query_post_compilation_showplan），然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="cd320-279">Right-click the session that contains the query plan graph that you want to view (for example, query_post_compilation_showplan), and then select **Watch Live Data**.</span></span>  
  
3.  <span data-ttu-id="cd320-280">选择查询计划图事件（例如 query_post_compilation_showplan）并在“详细信息”窗格的 **“查询计划”** 选项卡查看相关图形。</span><span class="sxs-lookup"><span data-stu-id="cd320-280">Select the query plan graph event (for example, query_post_compilation_showplan) and view the graph on the **Query plan** tab in the Details pane.</span></span>  
  
  
