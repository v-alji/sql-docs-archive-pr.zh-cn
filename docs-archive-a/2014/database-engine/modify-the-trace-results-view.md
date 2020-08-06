---
title: 修改跟踪结果视图 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 860a80dc-bac0-4ef0-bf7f-7a9b430d7aa3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 050c8f179742cf3cef6473b03f062390caf195f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578382"
---
# <a name="modify-the-trace-results-view"></a><span data-ttu-id="ea02a-102">修改跟踪结果视图</span><span class="sxs-lookup"><span data-stu-id="ea02a-102">Modify the Trace Results View</span></span>
  <span data-ttu-id="ea02a-103">本主题介绍如何通过执行以下任务修改 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中扩展事件会话的跟踪结果视图。</span><span class="sxs-lookup"><span data-stu-id="ea02a-103">This topic describes how to modify the trace results view of an Extended Events session in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] by performing the following tasks.</span></span>  
  
1.  [<span data-ttu-id="ea02a-104">添加或删除列</span><span class="sxs-lookup"><span data-stu-id="ea02a-104">Add or Remove Columns</span></span>](#AddRemoveColumns)  
  
2.  [<span data-ttu-id="ea02a-105">创建、编辑或删除合并列</span><span class="sxs-lookup"><span data-stu-id="ea02a-105">Create, Edit, or Delete Merged Columns</span></span>](#ChangeColumns)  
  
3.  [<span data-ttu-id="ea02a-106">对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="ea02a-106">Sort the Results</span></span>](#SortResults)  
  
4.  [<span data-ttu-id="ea02a-107">对结果进行分组</span><span class="sxs-lookup"><span data-stu-id="ea02a-107">Group the Results</span></span>](#GroupResults)  
  
5.  [<span data-ttu-id="ea02a-108">聚合结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-108">Aggregate the Results</span></span>](#AggregateResults)  
  
6.  [<span data-ttu-id="ea02a-109">筛选结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-109">Filter the Results</span></span>](#Filter)  
  
7.  [<span data-ttu-id="ea02a-110">在列中搜索文本</span><span class="sxs-lookup"><span data-stu-id="ea02a-110">Search for Text in Columns</span></span>](#Search)  
  
8.  [<span data-ttu-id="ea02a-111">更改显示设置</span><span class="sxs-lookup"><span data-stu-id="ea02a-111">Change the Display Settings</span></span>](#ChangeDisplay)  
  
##  <a name="add-or-remove-columns"></a><a name="AddRemoveColumns"></a><span data-ttu-id="ea02a-112">添加或删除列</span><span class="sxs-lookup"><span data-stu-id="ea02a-112">Add or Remove Columns</span></span>  
  
1.  <span data-ttu-id="ea02a-113">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-113">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-114"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-114">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-115">在跟踪结果窗口中，右键单击列标题，然后选择 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-115">In the trace results window, right-click the column header, and then select **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="ea02a-116">在 **“选择列”** 对话框的 **“可用列”** 部分，选择要添加的列名，然后单击向右箭头。</span><span class="sxs-lookup"><span data-stu-id="ea02a-116">In the **Choose Columns** dialog box, in the **Available columns** section, select the column names you want to add, and then click the right arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-117">默认情况下，列按名称排列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-117">By default, the columns are arranged by name.</span></span> <span data-ttu-id="ea02a-118">若要按事件显示列，请单击 **“按事件排列”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-118">To display the columns by event, click **Arrange by event**.</span></span>  
  
     <span data-ttu-id="ea02a-119">若要删除列，请在 **“所选列”** 部分选择要删除的列，然后单击向左箭头。</span><span class="sxs-lookup"><span data-stu-id="ea02a-119">To remove columns, in the **Selected columns** section, select the columns you want to remove, and click the left arrow.</span></span>  
  
4.  <span data-ttu-id="ea02a-120">在 **“所选列”** 部分，若要更改列排序显示，请分别单击 **“上移”** 或 **“下移”** 。</span><span class="sxs-lookup"><span data-stu-id="ea02a-120">In the **Selected columns** section, to change the column order display, click **Move Up** or **Move Down** respectively.</span></span> <span data-ttu-id="ea02a-121">不能移动多个行。</span><span class="sxs-lookup"><span data-stu-id="ea02a-121">You cannot move multiple rows.</span></span>  
  
5.  <span data-ttu-id="ea02a-122">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ea02a-122">Click **OK**.</span></span>  
  
##  <a name="create-edit-or-delete-merged-columns"></a><a name="ChangeColumns"></a><span data-ttu-id="ea02a-123">创建、编辑或删除合并列</span><span class="sxs-lookup"><span data-stu-id="ea02a-123">Create, Edit, or Delete Merged Columns</span></span>  
  
#### <a name="to-create-merged-columns"></a><span data-ttu-id="ea02a-124">创建合并列</span><span class="sxs-lookup"><span data-stu-id="ea02a-124">To create merged columns</span></span>  
  
1.  <span data-ttu-id="ea02a-125">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-125">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-126"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-126">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-127">在跟踪结果窗口中，右键单击列标题，然后单击 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-127">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="ea02a-128">在 **“选择列”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-128">In the **Choose Columns** dialog box, click **New**.</span></span>  
  
4.  <span data-ttu-id="ea02a-129">在 **“新建合并列”** 对话框的 **“合并列名称”** 框中，输入合并列的名称。</span><span class="sxs-lookup"><span data-stu-id="ea02a-129">In the **New Merged Column** dialog box, in the **Merged column name** box, enter a name for the merged columns.</span></span>  
  
5.  <span data-ttu-id="ea02a-130">在 **“要合并的原始列”** 框中，从下拉列表中选择两个或两个以上的要合并的列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-130">In the **Original columns to merge** box, select two or more columns to merge from the drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-131">扩展事件仅只支持合并最多 5 个列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-131">Extended Events only supports merging up to five columns.</span></span>  
  
6.  <span data-ttu-id="ea02a-132">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ea02a-132">Click **OK**.</span></span>  
  
#### <a name="to-edit-merged-columns"></a><span data-ttu-id="ea02a-133">编辑合并列</span><span class="sxs-lookup"><span data-stu-id="ea02a-133">To edit merged columns</span></span>  
  
1.  <span data-ttu-id="ea02a-134">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-134">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-135"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-135">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-136">在跟踪结果窗口中，右键单击列标题，然后单击 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-136">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="ea02a-137">在 **“选择列”** 对话框中，单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-137">In the **Choose Columns** dialog box, click **Edit**.</span></span>  
  
4.  <span data-ttu-id="ea02a-138">若要更改合并列的名称，请在 **“新建合并列”** 对话框的 **“合并列名称”** 框中，输入新名称。</span><span class="sxs-lookup"><span data-stu-id="ea02a-138">To change the name of the merged column, in the **New Merged Column** dialog box, in the **Merged column name** box, enter the new name.</span></span>  
  
     <span data-ttu-id="ea02a-139">若要更改要合并的列，请在 **“要合并的原始列”** 框中，从下拉列表中选择要合并的列，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-139">To change the columns you want to merge, in the **Original columns to merge** box, select the columns you want to merge from the drop-down list, and then click **OK**.</span></span>  
  
#### <a name="to-delete-merged-columns"></a><span data-ttu-id="ea02a-140">删除合并列</span><span class="sxs-lookup"><span data-stu-id="ea02a-140">To delete merged columns</span></span>  
  
1.  <span data-ttu-id="ea02a-141">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-141">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-142"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-142">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-143">在跟踪结果窗口中，右键单击列标题，然后单击 **“选择列”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-143">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
3.  <span data-ttu-id="ea02a-144">在 **“选择列”** 对话框中，选择要删除的合并列的名称，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-144">In the **Choose Columns** dialog box, select the name of the merged column you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="sort-the-results"></a><a name="SortResults"></a><span data-ttu-id="ea02a-145">对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="ea02a-145">Sort the Results</span></span>  
  
#### <a name="to-sort-the-results-in-ascending-or-descending-order"></a><span data-ttu-id="ea02a-146">按升序或降序对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="ea02a-146">To sort the results in ascending or descending order</span></span>  
  
-   <span data-ttu-id="ea02a-147">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-147">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-148"> 还可以右键单击会话名称，选择 **“查看实时数据”**，然后单击工具栏上的 **“停止数据反馈”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-148">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
-   <span data-ttu-id="ea02a-149">在跟踪结果窗口中，右键单击要排序的列标题。</span><span class="sxs-lookup"><span data-stu-id="ea02a-149">In the trace results window, right-click the column heading you want to sort.</span></span> <span data-ttu-id="ea02a-150">单击 **“升序排序”** 或 **“降序排序”** 可以分别按升序或降序对列进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea02a-150">Click **Sort Ascending** or **Sort Descending** to sort the column in ascending or descending order respectively.</span></span>  
  
     <span data-ttu-id="ea02a-151">如果已对列进行分组，则对某个列进行排序将只对组中的数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea02a-151">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
##  <a name="group-results"></a><a name="GroupResults"></a><span data-ttu-id="ea02a-152">组结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-152">Group Results</span></span>  
  
#### <a name="to-group-the-results-by-a-single-column"></a><span data-ttu-id="ea02a-153">按单个列对结果进行分组</span><span class="sxs-lookup"><span data-stu-id="ea02a-153">To group the results by a single column</span></span>  
  
1.  <span data-ttu-id="ea02a-154">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-154">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-155"> 还可以右键单击会话名称，选择 **“查看实时数据”**，然后单击扩展事件工具栏上的 **“停止数据反馈”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-155">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the Extended Events toolbar.</span></span>  
  
2.  <span data-ttu-id="ea02a-156">在跟踪结果窗口中，右键单击要分组的列标题，然后单击 **“按此列分组”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-156">In the trace results window, right-click the column header you want to group, and then click **Group By This Column**.</span></span>  
  
#### <a name="to-group-the-results-by-multiple-columns"></a><span data-ttu-id="ea02a-157">按多个列对结果进行分组</span><span class="sxs-lookup"><span data-stu-id="ea02a-157">To group the results by multiple columns</span></span>  
  
1.  <span data-ttu-id="ea02a-158">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-158">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-159"> 还可以右键单击会话名称，选择 **“查看实时数据”**，然后单击工具栏上的 **“停止数据反馈”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-159">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
2.  <span data-ttu-id="ea02a-160">单击扩展事件工具栏上的 **“分组”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-160">Click the **Grouping** button on the Extended Events toolbar.</span></span>  
  
3.  <span data-ttu-id="ea02a-161">在 **“分组”** 对话框的 **“可用列”** 框中，选择要分组的列，然后单击向右箭头。</span><span class="sxs-lookup"><span data-stu-id="ea02a-161">In the **Grouping** dialog box, in the **Available columns** box, select the columns you want to group, and then click the right arrow.</span></span>  
  
     <span data-ttu-id="ea02a-162">若要更改分组顺序，请在 **“列分组依据”** 部分，单击向上箭头或向下箭头。</span><span class="sxs-lookup"><span data-stu-id="ea02a-162">To change the grouping order, in the **Columns grouped on** section, click the up or down arrows.</span></span>  
  
     <span data-ttu-id="ea02a-163">若要从分组中删除列，请在 **“列分组依据”** 框中，选择要删除的列，然后单击向左箭头。</span><span class="sxs-lookup"><span data-stu-id="ea02a-163">To remove columns from the grouping, in the **Columns grouped on** box, select the columns you want to remove and then click the left arrow.</span></span>  
  
4.  <span data-ttu-id="ea02a-164">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ea02a-164">Click **OK**.</span></span>  
  
##  <a name="aggregate-results"></a><a name="AggregateResults"></a><span data-ttu-id="ea02a-165">聚合结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-165">Aggregate Results</span></span>  
 <span data-ttu-id="ea02a-166">扩展事件支持五个聚合函数：</span><span class="sxs-lookup"><span data-stu-id="ea02a-166">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="ea02a-167">Sum</span><span class="sxs-lookup"><span data-stu-id="ea02a-167">Sum</span></span>  
  
-   <span data-ttu-id="ea02a-168">Min</span><span class="sxs-lookup"><span data-stu-id="ea02a-168">Min</span></span>  
  
-   <span data-ttu-id="ea02a-169">Max</span><span class="sxs-lookup"><span data-stu-id="ea02a-169">Max</span></span>  
  
-   <span data-ttu-id="ea02a-170">平均值</span><span class="sxs-lookup"><span data-stu-id="ea02a-170">Average</span></span>  
  
-   <span data-ttu-id="ea02a-171">计数</span><span class="sxs-lookup"><span data-stu-id="ea02a-171">Count</span></span>  
  
 <span data-ttu-id="ea02a-172">Sum、Min、Max 和 Average 只能用于可用数值列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-172">Sum, Min,  Max, and Average can only be used with available numeric columns.</span></span> <span data-ttu-id="ea02a-173">count 是组中所选列存在的非 null 值的数量。</span><span class="sxs-lookup"><span data-stu-id="ea02a-173">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
#### <a name="to-aggregate-results"></a><span data-ttu-id="ea02a-174">聚合结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-174">To aggregate results</span></span>  
  
1.  <span data-ttu-id="ea02a-175">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-175">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-176"> 还可以右键单击会话名称，选择 **“查看实时数据”**，然后单击工具栏上的 **“停止数据反馈”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-176">You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-177">由于聚合是对组运行的，因此，您必须先对结果进行分组，然后才能执行聚合。</span><span class="sxs-lookup"><span data-stu-id="ea02a-177">Aggregation is run against a group, so you must group the results before you can perform the aggregation.</span></span>  
  
2.  <span data-ttu-id="ea02a-178">在扩展事件工具栏上，单击 **“聚合”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-178">On the Extended Events toolbar, click the **Aggregate** button.</span></span>  
  
     <span data-ttu-id="ea02a-179">**聚合** 对话框随即出现，其中显示可用于聚合的列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-179">The **Aggregation** dialog box appears displaying the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="ea02a-180">在 **“聚合类型”** 下，从下拉列表中选择聚合对应的列的方式。</span><span class="sxs-lookup"><span data-stu-id="ea02a-180">Under **Aggregation Type**, select how you want to aggregate the corresponding column from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="ea02a-181">在 **“聚合排序依据”** 框中，从下拉列表中选择要作为排序依据的列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-181">In the **Sort aggregation by** box, select the column you want to sort by from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="ea02a-182">选择 **“升序”** 选项以按升序对聚合结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea02a-182">Select the **In ascending order** option to sort the aggregation result in ascending order.</span></span>  
  
6.  <span data-ttu-id="ea02a-183">选择 **“降序”** 选项以按降序对聚合结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="ea02a-183">Select the **In descending order** option to sort the aggregation result in descending order.</span></span>  
  
7.  <span data-ttu-id="ea02a-184">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="ea02a-184">Click **OK**.</span></span>  
  
##  <a name="filter-results"></a><a name="Filter"></a><span data-ttu-id="ea02a-185">筛选结果</span><span class="sxs-lookup"><span data-stu-id="ea02a-185">Filter Results</span></span>  
 <span data-ttu-id="ea02a-186">您可以应用筛选器以缩小跟踪窗口中显示的跟踪结果的范围。</span><span class="sxs-lookup"><span data-stu-id="ea02a-186">You can apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="ea02a-187">显示筛选器包括时间筛选器和高级筛选器。</span><span class="sxs-lookup"><span data-stu-id="ea02a-187">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="ea02a-188">您可以使用时间筛选器按事件时间戳筛选跟踪结果，也可以使用高级筛选器通过事件字段和操作构造筛选条件。</span><span class="sxs-lookup"><span data-stu-id="ea02a-188">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="ea02a-189">时间筛选器和高级筛选器之间存在逻辑与关系。</span><span class="sxs-lookup"><span data-stu-id="ea02a-189">There is an logical AND relationship between the Time and Advanced Filters.</span></span>  
  
#### <a name="to-create-a-filter"></a><span data-ttu-id="ea02a-190">创建筛选器</span><span class="sxs-lookup"><span data-stu-id="ea02a-190">To create a filter</span></span>  
  
1.  <span data-ttu-id="ea02a-191">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-191">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-192"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-192">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-193">在跟踪结果窗口中选择要筛选的结果，然后在扩展事件工具栏上单击 **“筛选器”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-193">In the trace results window, select the results you want to filter, and then on the Extended Events toolbar, click the **Filters** button.</span></span>  
  
3.  <span data-ttu-id="ea02a-194">在 **“筛选器”** 对话框中，选择 **“设置时间筛选器”** 以通过拖动滑动条设置时间线来设置时间筛选器。</span><span class="sxs-lookup"><span data-stu-id="ea02a-194">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars to set the timeline.</span></span> <span data-ttu-id="ea02a-195">请注意，在移动滑动条时，时间框会显示相应的时间值。</span><span class="sxs-lookup"><span data-stu-id="ea02a-195">Note that when you move the slider bars, the time box displays the time value accordingly.</span></span> <span data-ttu-id="ea02a-196">您还可以在时间框中输入时间或从下拉列表中选择时间。</span><span class="sxs-lookup"><span data-stu-id="ea02a-196">You can also enter the time in the time boxes, or you select it from the drop-down list.</span></span> <span data-ttu-id="ea02a-197">请注意，在输入时间时，左侧时间滑块将相应地移动。</span><span class="sxs-lookup"><span data-stu-id="ea02a-197">Note that when you enter the time, the left time slider will move accordingly.</span></span>  
  
4.  <span data-ttu-id="ea02a-198">在 **“其他筛选器”** 部分中，应用筛选条件，然后单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-198">In the **Additional Filters** section, apply your filter criteria, and then click **Apply**.</span></span> <span data-ttu-id="ea02a-199">创建完筛选器后，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-199">When your finished created the filter, click **OK**.</span></span>  
  
 <span data-ttu-id="ea02a-200">特殊情况是当事件字段与操作具有相同名称时。</span><span class="sxs-lookup"><span data-stu-id="ea02a-200">A special situation is when an event field has the same name as an action.</span></span> <span data-ttu-id="ea02a-201">这样的示例为 session_id。</span><span class="sxs-lookup"><span data-stu-id="ea02a-201">An example of this would be session_id.</span></span> <span data-ttu-id="ea02a-202">有几个包含 session_id 字段的事件，您还可以添加 session_id 操作。</span><span class="sxs-lookup"><span data-stu-id="ea02a-202">There are several events that include a session_id field and you could also add the session_id action.</span></span> <span data-ttu-id="ea02a-203">收集这些信息，但是扩展事件探查器显示网格使用以下逻辑。</span><span class="sxs-lookup"><span data-stu-id="ea02a-203">Both pieces of information are collected, but the Extended Events profiler display grid uses the following logic.</span></span>  
  
-   <span data-ttu-id="ea02a-204">只有列（此情况下为 session_id）的一个副本显示在显示网格中。</span><span class="sxs-lookup"><span data-stu-id="ea02a-204">Only one copy of the column (session_id in this case) is shown in the grid display.</span></span>  
  
-   <span data-ttu-id="ea02a-205">如果数据中同时存在字段和操作，则显示字段值。</span><span class="sxs-lookup"><span data-stu-id="ea02a-205">If both fields and action exist in the data, the field value is shown.</span></span>  
  
-   <span data-ttu-id="ea02a-206">如果数据中只存在字段或操作，则显示字段或操作。</span><span class="sxs-lookup"><span data-stu-id="ea02a-206">If only field or action is exists in the data, the field or action is displayed.</span></span>  
  
-   <span data-ttu-id="ea02a-207">如果操作和字段都不存在，则显示 NULL。</span><span class="sxs-lookup"><span data-stu-id="ea02a-207">If neither action nor field exists, display NULL.</span></span>  
  
##  <a name="search-for-text-in-columns"></a><a name="Search"></a><span data-ttu-id="ea02a-208">在列中搜索文本</span><span class="sxs-lookup"><span data-stu-id="ea02a-208">Search for Text in Columns</span></span>  
  
1.  <span data-ttu-id="ea02a-209">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-209">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-210"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-210">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-211">在扩展事件工具栏上，单击 **“查找”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ea02a-211">On the Extended Events toolbar, click the **Find** button.</span></span>  
  
3.  <span data-ttu-id="ea02a-212">在 **“在扩展事件中查找”** 对话框的 **“查找内容”** 框中，输入要搜索的文本。</span><span class="sxs-lookup"><span data-stu-id="ea02a-212">In the **Find in Extended Events** dialog box, in the **Find what** box, enter the text you want to search for.</span></span>  
  
     <span data-ttu-id="ea02a-213">可以从下拉列表中选择最近搜索过的 20 个字符串之一。</span><span class="sxs-lookup"><span data-stu-id="ea02a-213">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="ea02a-214">在 **“查找范围”** 框中，从下拉列表中选择要搜索指定文本的位置。</span><span class="sxs-lookup"><span data-stu-id="ea02a-214">In the **Look in** box, select the location in which to search for the specified text from the drop-down list.</span></span> <span data-ttu-id="ea02a-215">使用以下选项进行搜索：</span><span class="sxs-lookup"><span data-stu-id="ea02a-215">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="ea02a-216">**表列**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-216">**Table Columns**.</span></span> <span data-ttu-id="ea02a-217">使用此选项可在跟踪窗口中搜索所有可见列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-217">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="ea02a-218">**详细信息**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-218">**Details**.</span></span> <span data-ttu-id="ea02a-219">使用此选项可搜索在打开 "**在扩展事件中查找**" 对话框之前已选择的跟踪窗口中 (升级和未升级) 的所有列。</span><span class="sxs-lookup"><span data-stu-id="ea02a-219">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="ea02a-220">**\<Event column name>**.</span><span class="sxs-lookup"><span data-stu-id="ea02a-220">**\<Event column name>**.</span></span> <span data-ttu-id="ea02a-221">使用此选项可在下拉列表的特定事件列中进行搜索。</span><span class="sxs-lookup"><span data-stu-id="ea02a-221">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="ea02a-222">使用以下选项可指定所需的定义搜索的方式：</span><span class="sxs-lookup"><span data-stu-id="ea02a-222">Use the following options to specify how you want to define the search:</span></span>  
  
    1.  <span data-ttu-id="ea02a-223">**区分大小写**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-223">**Match case**.</span></span> <span data-ttu-id="ea02a-224">使用此选项可显示与 **“查找内容”** 框中输入文本的内容和大小写均匹配的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-224">Use this option to display the search results for the text you entered in the **Find what** box that are matched both by content and by case.</span></span>  
  
    2.  <span data-ttu-id="ea02a-225">**全字匹配**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-225">**Match whole word**.</span></span> <span data-ttu-id="ea02a-226">使用此选项可仅显示与输入文本完全匹配的搜索结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-226">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    3.  <span data-ttu-id="ea02a-227">**向上搜索**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-227">**Search up**.</span></span> <span data-ttu-id="ea02a-228">使用此选项可从光标位置向结果开头搜索。</span><span class="sxs-lookup"><span data-stu-id="ea02a-228">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    4.  <span data-ttu-id="ea02a-229">**使用**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-229">**Use**.</span></span> <span data-ttu-id="ea02a-230">使用此选项可解释 "**查找内容**" 框中输入的特殊字符和正则表达式。</span><span class="sxs-lookup"><span data-stu-id="ea02a-230">Use this option to interpret the special characters and the regular expressions you entered in the **Find what** box.</span></span> <span data-ttu-id="ea02a-231">特殊字符包括通配符 (\*) 和 (?)，用于表示一个或多个字符。</span><span class="sxs-lookup"><span data-stu-id="ea02a-231">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="ea02a-232">正则表达式是用于定义搜索文本的模式的特殊表示法。</span><span class="sxs-lookup"><span data-stu-id="ea02a-232">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
6.  <span data-ttu-id="ea02a-233">单击 **“查找下一个”** 可搜索在 **“查找内容”** 框中输入的下一个文本。</span><span class="sxs-lookup"><span data-stu-id="ea02a-233">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
##  <a name="change-the-display-settings"></a><a name="ChangeDisplay"></a><span data-ttu-id="ea02a-234">更改显示设置</span><span class="sxs-lookup"><span data-stu-id="ea02a-234">Change the Display Settings</span></span>  
 <span data-ttu-id="ea02a-235">您可以将跟踪结果的列信息（列顺序、合并列和列宽）和筛选器信息保存到扩展事件显示设置文件（.viewsetting 文件）中。</span><span class="sxs-lookup"><span data-stu-id="ea02a-235">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="ea02a-236">在保存该文件后，您可以将其应用于跟踪结果中以便更改视图。</span><span class="sxs-lookup"><span data-stu-id="ea02a-236">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
#### <a name="to-change-the-display-settings"></a><span data-ttu-id="ea02a-237">更改显示设置</span><span class="sxs-lookup"><span data-stu-id="ea02a-237">To change the display settings</span></span>  
  
1.  <span data-ttu-id="ea02a-238">打开一个 .XEL 文件以便查看跟踪结果。</span><span class="sxs-lookup"><span data-stu-id="ea02a-238">Open a .XEL file to view the trace results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea02a-239"> 您还可以右键单击会话名称，然后选择 **“查看实时数据”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-239">You can also right click the session name, and then select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="ea02a-240">在跟踪结果窗口中的扩展事件工具栏或菜单上，选择 **“显示设置”**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-240">In the trace results window, on the Extended Events toolbar or menu, select **Display Settings**.</span></span>  
  
3.  <span data-ttu-id="ea02a-241">从下拉列表中选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="ea02a-241">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="ea02a-242">**另存为**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-242">**Save as**.</span></span> <span data-ttu-id="ea02a-243">将跟踪结果的列和筛选器信息保存到 .viewsetting 文件中。</span><span class="sxs-lookup"><span data-stu-id="ea02a-243">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="ea02a-244">**打开**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-244">**Open**.</span></span> <span data-ttu-id="ea02a-245">打开现有的 .viewsetting 文件。</span><span class="sxs-lookup"><span data-stu-id="ea02a-245">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="ea02a-246">**打开最近的**。</span><span class="sxs-lookup"><span data-stu-id="ea02a-246">**Open recent**.</span></span> <span data-ttu-id="ea02a-247">打开最近保存的 .viewsetting 文件。</span><span class="sxs-lookup"><span data-stu-id="ea02a-247">Open a recently saved .viewsetting file.</span></span>  
  
  
