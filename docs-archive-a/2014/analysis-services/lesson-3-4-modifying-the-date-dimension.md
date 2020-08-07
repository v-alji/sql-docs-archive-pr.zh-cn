---
title: 修改 Date 维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4978e9fe3acd93ddfdca707d2c2353bf171ba12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588134"
---
# <a name="modifying-the-date-dimension"></a><span data-ttu-id="1d3c3-102">修改“日期”维度</span><span class="sxs-lookup"><span data-stu-id="1d3c3-102">Modifying the Date Dimension</span></span>
  <span data-ttu-id="1d3c3-103">在本主题的各任务中，将创建用户定义的层次结构，并更改为“日期”、“月份”、“日历季度”以及“日历半期”等属性显示的成员名称。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-103">In the tasks in this topic, you create a user-defined hierarchy and change the member names that are displayed for the Date, Month, Calendar Quarter, and Calendar Semester attributes.</span></span> <span data-ttu-id="1d3c3-104">还将为属性定义组合键，控制维度成员的排序顺序以及定义属性关系。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-104">You also define composite keys for attributes, control the sort order of dimension members, and define attribute relationships.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="1d3c3-105">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="1d3c3-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="1d3c3-106">可以向数据源视图的表中添加命名计算，命名计算是一个表示为计算列的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-106">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="1d3c3-107">该表达式的显示形式和工作方式类似于表中的列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-107">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="1d3c3-108">通过命名计算，不必修改基础数据源中的表即可扩展数据源视图中现有表的关系架构。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-108">Named calculations enable you to extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="1d3c3-109">有关详细信息，请参阅 [在数据源视图中定义命名计算 (Analysis Services)](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="1d3c3-109">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="1d3c3-110">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="1d3c3-110">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="1d3c3-111">若要打开 **Adventure Works DW 2012** 数据源视图，请在解决方案资源管理器中的“数据源视图”\*\*\*\* 文件夹中双击此视图。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-111">To open the **Adventure Works DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="1d3c3-112">在 "**表**" 窗格底部附近，右键单击 `Date` ，然后单击 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-112">Near the bottom of the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="1d3c3-113">在 "**创建命名计算**" 对话框中，在 `SimpleDate` "**列名称**" 框中键入，然后在 `DATENAME` "**表达式**" 框中键入或复制并粘贴以下语句：</span><span class="sxs-lookup"><span data-stu-id="1d3c3-113">In the **Create Named Calculation** dialog box, type `SimpleDate` in the **Column name** box, and then type or copy and paste the following `DATENAME` statement in the **Expression** box:</span></span>  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     <span data-ttu-id="1d3c3-114">该 `DATENAME` 语句从 FullDateAlternateKey 列中提取年、月和日的值。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-114">The `DATENAME` statement extracts the year, month, and day values from the FullDateAlternateKey column.</span></span> <span data-ttu-id="1d3c3-115">将此新列用作 FullDateAlternateKey 属性的显示名称。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-115">You will use this new column as the displayed name for the FullDateAlternateKey attribute.</span></span>  
  
4.  <span data-ttu-id="1d3c3-116">单击 **"确定**"，然后 `Date` 在 "**表**" 窗格中展开。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-116">Click **OK**, and then expand `Date` in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="1d3c3-117">`SimpleDate`命名计算显示在 Date 表中列的列表中，并带有一个图标指示它是命名计算。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-117">The `SimpleDate` named calculation appears in the list of columns in the Date table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="1d3c3-118">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-118">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="1d3c3-119">在 "**表**" 窗格中，右键单击 `Date` ，然后单击 "**浏览数据**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-119">In the **Tables** pane, right-click `Date`, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="1d3c3-120">滚动到右侧，以查看“浏览 Date 表”\*\*\*\* 视图中的最后一列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-120">Scroll to the right to review the last column in the **Explore Date Table** view.</span></span>  
  
     <span data-ttu-id="1d3c3-121">请注意， `SimpleDate` 列显示在数据源视图中，它从基础数据源中正确地连接多个列的数据，而不修改原始数据源。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-121">Notice that the `SimpleDate` column appears in the data source view, correctly concatenating data from several columns from the underlying data source, without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="1d3c3-122">关闭“浏览 Date 表”\*\*\*\* 视图。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-122">Close the **Explore Date Table** view.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="1d3c3-123">将命名计算用于成员名称</span><span class="sxs-lookup"><span data-stu-id="1d3c3-123">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="1d3c3-124">在数据源视图中创建命名计算后，可以将命名计算用作特性的属性。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-124">After you create a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="1d3c3-125">将命名计算用于成员名称</span><span class="sxs-lookup"><span data-stu-id="1d3c3-125">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="1d3c3-126">打开 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“日期”维度的“维度设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-126">Open **Dimension Designer** for the Date dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="1d3c3-127">为此，请 `Date` 在**解决方案资源管理器**的 "**维度**" 节点中双击维度。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-127">To do this, double-click the `Date` dimension in the **Dimensions** node of **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="1d3c3-128">在“维度结构”\*\*\*\* 选项卡的“属性”\*\*\*\* 窗格中，单击“日期键”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-128">In the **Attributes** pane of the **Dimension Structure** tab, click the **Date Key** attribute.</span></span>  
  
3.  <span data-ttu-id="1d3c3-129">如果未打开“属性”窗口，则打开“属性”窗口，然后单击标题栏上的“自动隐藏”\*\*\*\* 按钮，以便该窗口保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-129">If the Properties window is not open, open the Properties window, and then click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="1d3c3-130">单击窗口底部附近的**NameColumn**属性字段，然后单击省略号的 "浏览 (**...** ") 按钮，以打开 "**名称列**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-130">Click the **NameColumn** property field near the bottom of the window, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
5.  <span data-ttu-id="1d3c3-131">选择 " `SimpleDate` **源列**" 列表底部，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-131">Select `SimpleDate` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="1d3c3-132">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-132">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="1d3c3-133">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="1d3c3-133">Creating a Hierarchy</span></span>  
 <span data-ttu-id="1d3c3-134">通过将属性从“属性”\*\*\*\* 窗格拖至“层次结构”\*\*\*\* 窗格可以创建新的层次结构。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-134">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="1d3c3-135">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="1d3c3-135">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="1d3c3-136">在维度的维度设计器的 "**维度结构**" 选项卡中 `Date` ，将 "**日历年**" 属性从 "**属性**" 窗格拖到 "**层次结构**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-136">In **Dimension Structure** tab of the Dimension Designer for the `Date` dimension, drag the **Calendar Year** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="1d3c3-137">将“日历半期”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖动到“层次结构”\*\*\*\* 窗格中“日历年”\*\*\*\* 级别下方的 \<new level>\*\*\*\* 单元格中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-137">Drag the **Calendar Semester** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Year** level.</span></span>  
  
3.  <span data-ttu-id="1d3c3-138">将“日历季度”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖动到“层次结构”\*\*\*\* 窗格中“日历半期”\*\*\*\* 级别下方的 \<new level>\*\*\*\* 单元格中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-138">Drag the **Calendar Quarter** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Semester** level.</span></span>  
  
4.  <span data-ttu-id="1d3c3-139">将“英语月份名称”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖动到“层次结构”\*\*\*\* 窗格中“日历季度”\*\*\*\* 级别下方的 \<new level>\*\*\*\* 单元格中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-139">Drag the **English Month Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Quarter** level.</span></span>  
  
5.  <span data-ttu-id="1d3c3-140">将“日期键”\*\*\*\* 属性从“属性”\*\*\*\* 窗格拖动到“层次结构”\*\*\*\* 窗格中“英语月份名称”\*\*\*\* 级别下方的 \<new level>\*\*\*\* 单元格中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-140">Drag the **Date Key** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **English Month Name** level.</span></span>  
  
6.  <span data-ttu-id="1d3c3-141">在 "**层次**结构" 窗格中，右键单击 "**层次**结构" 层次结构的标题栏，单击 "**重命名**"，然后键入 `Calendar Date` 。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-141">In the **Hierarchies** pane, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Calendar Date`.</span></span>  
  
7.  <span data-ttu-id="1d3c3-142">使用右键单击上下文菜单，在 `Calendar Date` 层次结构中，将 "**英语月份名称**" 级别重命名为 `Calendar Month` ，然后将 "**日期键**" 级别重命名为 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-142">By using the right-click context menu, in the `Calendar Date` hierarchy, rename the **English Month Name** level to `Calendar Month`, and then rename the **Date Key** level to `Date`.</span></span>  
  
8.  <span data-ttu-id="1d3c3-143">因为不需要使用“完整日期备用键”\*\*\*\* 属性，所以将其从“属性”\*\*\*\* 窗格中删除。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-143">Delete the **Full Date Alternate Key** attribute from the **Attributes** pane because you will not be using it.</span></span> <span data-ttu-id="1d3c3-144">在“删除对象”\*\*\*\* 确认窗口中单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-144">Click **OK** in the **Delete Objects** confirmation window.</span></span>  
  
9. <span data-ttu-id="1d3c3-145">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-145">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="1d3c3-146">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="1d3c3-146">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="1d3c3-147">如果基础数据支持，则应定义属性间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-147">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="1d3c3-148">定义属性关系可加快维度、分区和查询处理的速度。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-148">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="1d3c3-149">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="1d3c3-149">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="1d3c3-150">在维度的**维度设计器**中 `Date` ，单击 "**属性关系**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-150">In the **Dimension Designer** for the `Date` dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="1d3c3-151">在关系图中，右键单击“英语月份名称”\*\*\*\* 属性，然后单击“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-151">In the diagram, right-click the **English Month Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="1d3c3-152">在“创建属性关系”\*\*\*\* 对话框中，“源属性”\*\*\*\* 是“英语月份名称”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-152">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **English Month Name**.</span></span> <span data-ttu-id="1d3c3-153">将“相关属性”设置为“日历季度”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-153">Set the **Related Attribute** to **Calendar Quarter**.</span></span>  
  
4.  <span data-ttu-id="1d3c3-154">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-154">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="1d3c3-155">因为各成员之间的关系不会随时间变化，所以此关系类型为“刚性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-155">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span>  
  
5.  <span data-ttu-id="1d3c3-156">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-156">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="1d3c3-157">在关系图中，右键单击“日历季度”\*\*\*\* 属性，然后单击“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-157">In the diagram, right-click the **Calendar Quarter** attribute, and then click **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="1d3c3-158">在“创建属性关系”对话框中，“源属性”是“日历季度”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-158">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="1d3c3-159">将“相关属性”设置为“日历半期”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-159">Set the **Related Attribute** to **Calendar Semester**.</span></span>  
  
8.  <span data-ttu-id="1d3c3-160">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-160">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="1d3c3-161">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-161">Click **OK**.</span></span>  
  
10. <span data-ttu-id="1d3c3-162">在关系图中，右键单击“日历半期”\*\*\*\* 属性，然后单击“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-162">In the diagram, right-click the **Calendar Semester** attribute, and then click **New Attribute Relationship**.</span></span>  
  
11. <span data-ttu-id="1d3c3-163">在“创建属性关系”对话框中，“源属性”是“日历半期”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="1d3c3-164">将“相关属性”设置为“日历年”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-164">Set the **Related Attribute** to **Calendar Year**.</span></span>  
  
12. <span data-ttu-id="1d3c3-165">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-165">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
13. <span data-ttu-id="1d3c3-166">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="1d3c3-167">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-167">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="providing-unique-dimension-member-names"></a><span data-ttu-id="1d3c3-168">提供唯一的维度成员名称</span><span class="sxs-lookup"><span data-stu-id="1d3c3-168">Providing Unique Dimension Member Names</span></span>  
 <span data-ttu-id="1d3c3-169">在此任务中，将创建由 **EnglishMonthName\*\*\*\*CalendarQuarter** 和 **CalendarSemester** 属性使用的用户友好名称列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-169">In this task, you will create user-friendly name columns that will be used by the **EnglishMonthName**, **CalendarQuarter**, and **CalendarSemester** attributes.</span></span>  
  
#### <a name="to-provide-unique-dimension-member-names"></a><span data-ttu-id="1d3c3-170">提供唯一的维度成员名称</span><span class="sxs-lookup"><span data-stu-id="1d3c3-170">To provide unique dimension member names</span></span>  
  
1.  <span data-ttu-id="1d3c3-171">若要切换到\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012**数据源视图，请在解决方案资源管理器的 "**数据源视图\*\*" 文件夹中双击它。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-171">To switch to the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="1d3c3-172">在 "**表**" 窗格中，右键单击 `Date` ，然后单击 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-172">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="1d3c3-173">在 "**创建命名计算**" 对话框中，在 `MonthName` "**列名称**" 框中键入，然后在 "**表达式**" 框中键入或复制并粘贴以下语句：</span><span class="sxs-lookup"><span data-stu-id="1d3c3-173">In the **Create Named Calculation** dialog box, type `MonthName` in the **Column name** box, and then type or copy and paste the following statement in the **Expression** box:</span></span>  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="1d3c3-174">该语句将表中每月的月份和年份连接成一个新列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-174">The statement concatenates the month and year for each month in the table into a new column.</span></span>  
  
4.  <span data-ttu-id="1d3c3-175">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-175">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1d3c3-176">在 "**表**" 窗格中，右键单击 `Date` ，然后单击 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-176">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="1d3c3-177">在 "**创建命名计算**" 对话框中，在 `CalendarQuarterDesc` "**列名称**" 框中键入，然后在 "**表达式**" 框中键入或复制并粘贴以下 SQL 脚本：</span><span class="sxs-lookup"><span data-stu-id="1d3c3-177">In the **Create Named Calculation** dialog box, type `CalendarQuarterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="1d3c3-178">该 SQL 脚本将表中每季度的日历季度和年份连接成一个新列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-178">This SQL script concatenates the calendar quarter and year for each quarter in the table into a new column.</span></span>  
  
7.  <span data-ttu-id="1d3c3-179">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-179">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="1d3c3-180">在 "**表**" 窗格中，右键单击 `Date` ，然后单击 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-180">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
9. <span data-ttu-id="1d3c3-181">在 "**创建命名计算**" 对话框中，在 `CalendarSemesterDesc` "**列名称**" 框中键入，然后在 "**表达式**" 框中键入或复制并粘贴以下 SQL 脚本：</span><span class="sxs-lookup"><span data-stu-id="1d3c3-181">In the **Create Named Calculation** dialog box, type `CalendarSemesterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     <span data-ttu-id="1d3c3-182">该 SQL 脚本将表中每半期的日历半期和年份连接成一个新列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-182">This SQL script concatenates the calendar semester and year for each semester in the table into a new column.</span></span>  
  
10. <span data-ttu-id="1d3c3-183">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="1d3c3-183">Click **OK.**</span></span>  
  
11. <span data-ttu-id="1d3c3-184">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a><span data-ttu-id="1d3c3-185">定义组合的 KeyColumns 和设置名称列</span><span class="sxs-lookup"><span data-stu-id="1d3c3-185">Defining Composite KeyColumns and Setting the Name Column</span></span>  
 <span data-ttu-id="1d3c3-186">**KeyColumns** 属性中包含表示特性键的一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-186">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="1d3c3-187">在本任务中，将定义组合的 **KeyColumns**。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-187">In this task, you will define composite **KeyColumns**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a><span data-ttu-id="1d3c3-188">为“英语月份名称”属性定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="1d3c3-188">To define composite KeyColumns for the English Month Name attribute</span></span>  
  
1.  <span data-ttu-id="1d3c3-189">打开“日期”维度的“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-189">Open the **Dimension Structure** tab for the Date dimension.</span></span>  
  
2.  <span data-ttu-id="1d3c3-190">在“属性”\*\*\*\* 窗格中，单击“英语月份名称”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-190">In the **Attributes** pane, click the **English Month Name** attribute.</span></span>  
  
3.  <span data-ttu-id="1d3c3-191">在“属性”\*\*\*\* 窗口中，单击 **KeyColumns** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-191">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="1d3c3-192">在 "**键列**" 对话框中，在 "**可用列**" 列表中选择列 " **CalendarYear**"，然后单击 "" **>** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-192">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
5.  <span data-ttu-id="1d3c3-193">现在，**EnglishMonthName** 和 **CalendarYear** 列会显示在“键列”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-193">The **EnglishMonthName** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
6.  <span data-ttu-id="1d3c3-194">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-194">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="1d3c3-195">若要设置 **EnglishMonthName** 特性的 **NameColumn** 属性，请单击“属性”窗口中的 **NameColumn** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-195">To set the **NameColumn** property of the **EnglishMonthName** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
8.  <span data-ttu-id="1d3c3-196">在 "**名称列**" 对话框的 "**源列**" 列表中，选择 `MonthName` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-196">In the **Name Column** dialog box, in the **Source Column** list, select `MonthName`, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="1d3c3-197">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-197">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a><span data-ttu-id="1d3c3-198">为“日历季度”属性定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="1d3c3-198">To define composite KeyColumns for the Calendar Quarter attribute</span></span>  
  
1.  <span data-ttu-id="1d3c3-199">在“属性”\*\*\*\* 窗格中，单击“日历季度”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-199">In the **Attributes** pane, click the **Calendar Quarter** attribute.</span></span>  
  
2.  <span data-ttu-id="1d3c3-200">在“属性”\*\*\*\* 窗口中，单击 **KeyColumns** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-200">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="1d3c3-201">在 "**键列**" 对话框中，在 "**可用列**" 列表中选择列 " **CalendarYear**"，然后单击 "" **>** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-201">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="1d3c3-202">现在，**CalendarQuarter** 和 **CalendarYear** 列会显示在“键列”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-202">The **CalendarQuarter** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="1d3c3-203">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-203">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1d3c3-204">若要设置“日历季度”\*\*\*\* 特性的 **NameColumn** 属性，请单击“属性”窗口的 **NameColumn** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-204">To set the **NameColumn** property of the **Calendar Quarter** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="1d3c3-205">在 "**名称列**" 对话框的 "**源列**" 列表中，选择 `CalendarQuarterDesc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-205">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarQuarterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1d3c3-206">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-206">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a><span data-ttu-id="1d3c3-207">为“日历半期”属性定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="1d3c3-207">To define composite KeyColumns for the Calendar Semester attribute</span></span>  
  
1.  <span data-ttu-id="1d3c3-208">在在“属性”\*\*\*\* 窗格中，单击“日历半期”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-208">In the **Attributes** pane, click the **Calendar Semester** attribute.</span></span>  
  
2.  <span data-ttu-id="1d3c3-209">在“属性”\*\*\*\* 窗口中，单击 **KeyColumns** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-209">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="1d3c3-210">在“键列”\*\*\*\* 对话框的“可用列”\*\*\*\* 列表中，选择 **CalendarYear** 列，然后单击“>”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-210">In the **Key Columns** dialog box, in the **Available Columns** list, select the column, **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="1d3c3-211">现在，**CalendarSemester** 和 **CalendarYear** 列会显示在“键列”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-211">The **CalendarSemester** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="1d3c3-212">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-212">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1d3c3-213">若要设置“日历半期”\*\*\*\* 特性的 **NameColumn** 属性，请单击“属性”窗口的 **NameColumn** 字段，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-213">To set the **NameColumn** property of the **Calendar Semester** attribute, click the **NameColumn** field in the property window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="1d3c3-214">在 "**名称列**" 对话框的 "**源列**" 列表中，选择 `CalendarSemesterDesc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-214">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarSemesterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="1d3c3-215">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-215">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-and-viewing-the-changes"></a><span data-ttu-id="1d3c3-216">部署和查看更改</span><span class="sxs-lookup"><span data-stu-id="1d3c3-216">Deploying and Viewing the Changes</span></span>  
 <span data-ttu-id="1d3c3-217">更改属性和层次结构后，必须部署更改并重新处理相关对象，然后才能查看这些更改。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-217">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-and-view-the-changes"></a><span data-ttu-id="1d3c3-218">部署和查看更改</span><span class="sxs-lookup"><span data-stu-id="1d3c3-218">To deploy and view the changes</span></span>  
  
1.  <span data-ttu-id="1d3c3-219">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-219">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="1d3c3-220">在收到 "**部署成功完成**" 消息后，单击维度的**维度设计**器的 "**浏览器**" 选项卡 `Date` ，然后单击设计器工具栏上的 "重新连接" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-220">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the `Date` dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="1d3c3-221">从“层次结构”\*\*\*\* 列表中选择“日历季度”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-221">Select **Calendar Quarter** from the **Hierarchy** list.</span></span> <span data-ttu-id="1d3c3-222">查看“日历季度”\*\*\*\* 属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-222">Review the members in the **Calendar Quarter** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="1d3c3-223">注意，由于创建了要用作名称的命名计算，因此，“日历季度”\*\*\*\* 属性层次结构的成员名称更明确且更易于使用。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-223">Notice that the names of the members of the **Calendar Quarter** attribute hierarchy are clearer and easier to use because you created a named calculation to use as the name.</span></span> <span data-ttu-id="1d3c3-224">成员现在位于每年每个季度的“日历季度”\*\*\*\* 属性层次结构中。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-224">Members now exist in the **Calendar Quarter** attribute hierarchy for each quarter in each year.</span></span> <span data-ttu-id="1d3c3-225">成员不是按时间顺序排序的。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-225">The members are not sorted in chronological order.</span></span> <span data-ttu-id="1d3c3-226">相反，它们先按季度然后按年份进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-226">Instead they are sorted by quarter and then by year.</span></span> <span data-ttu-id="1d3c3-227">在本主题的下一个任务中，您将修改此行为，以先按年然后按季度对此属性的层次结构成员进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-227">In the next task in this topic, you will modify this behavior to sort the members of this attribute hierarchy by year and then by quarter.</span></span>  
  
4.  <span data-ttu-id="1d3c3-228">查看“英语月份名称”\*\*\*\* 和“日历半期”\*\*\*\* 属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-228">Review the members of the **English Month Name** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="1d3c3-229">注意，这些层次结构的成员也不是按时间顺序排序的。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-229">Notice that the members of these hierarchies are also not sorted in chronological order.</span></span> <span data-ttu-id="1d3c3-230">相反，它们先分别按月或半期然后按年份进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-230">Instead, they are sorted by month or semester, respectively, and then by year.</span></span> <span data-ttu-id="1d3c3-231">在本主题的下一个任务中，您将修改此行为以更改这种排序顺序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-231">In the next task in this topic, you will modify this behavior to change this sort order.</span></span>  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a><span data-ttu-id="1d3c3-232">通过修改组合键成员顺序来更改排序顺序</span><span class="sxs-lookup"><span data-stu-id="1d3c3-232">Changing the Sort Order by Modifying Composite Key Member Order</span></span>  
 <span data-ttu-id="1d3c3-233">在本任务中，您将通过更改组成组合键的键顺序来更改排序顺序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-233">In this task, you will change the sort order by changing the order of the keys that make up the composite key.</span></span>  
  
#### <a name="to-modify-the-composite-key-member-order"></a><span data-ttu-id="1d3c3-234">修改组合键成员顺序</span><span class="sxs-lookup"><span data-stu-id="1d3c3-234">To modify the composite key member order</span></span>  
  
1.  <span data-ttu-id="1d3c3-235">打开维度的维度设计器的 "**维度结构**" 选项卡 `Date` ，然后在 "**属性**" 窗格中选择 "**日历半期**"。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-235">Open the **Dimension Structure** tab of Dimension Designer for the `Date` dimension, and then select **Calendar Semester** in the **Attributes** pane.</span></span>  
  
2.  <span data-ttu-id="1d3c3-236">在“属性”窗口中，查看 **OrderBy** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-236">In the Properties window, review the value for the **OrderBy** property.</span></span> <span data-ttu-id="1d3c3-237">它被设置为“键”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-237">It is set to **Key**.</span></span>  
  
     <span data-ttu-id="1d3c3-238">“日历半期”\*\*\*\* 属性层次结构的成员按其键值进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-238">The members of the **Calendar Semester** attribute hierarchy are sorted by their key value.</span></span> <span data-ttu-id="1d3c3-239">使用组合键，成员键首先基于第一个成员键的值，然后基于第二个成员键的值进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-239">With a composite key, the ordering of the member keys is based first on the value of the first member key, and then on the value of the second member key.</span></span> <span data-ttu-id="1d3c3-240">换言之，“日历半期”\*\*\*\* 属性层次结构的成员首先按半期、然后按年份进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-240">In other words, the members of the **Calendar Semester** attribute hierarchy are sorted first by semester and then by year.</span></span>  
  
3.  <span data-ttu-id="1d3c3-241">在“属性”窗口中，单击省略号浏览按钮 (**...**)，以更改 **KeyColumns** 属性值。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-241">In the Properties window, click the ellipsis browse button (**...**) to change the **KeyColumns** property value.</span></span>  
  
4.  <span data-ttu-id="1d3c3-242">在“键列”\*\*\*\* 对话框的“键列”\*\*\*\* 列表中，验证是否选中了 **CalendarSemester**，然后单击向下箭头以反转该组合键成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-242">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarSemester** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="1d3c3-243">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-243">Click **OK**.</span></span>  
  
     <span data-ttu-id="1d3c3-244">现在，属性层次结构成员首先按年份、然后按半期进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-244">The members of the attribute hierarchy are now sorted first by year and then by semester.</span></span>  
  
5.  <span data-ttu-id="1d3c3-245">在“特性”\*\*\*\* 窗格中，选择“日历季度”\*\*\*\*，然后单击“属性”窗口中 **KeyColumns** 属性的省略号浏览按钮 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-245">Select **Calendar Quarter** in the **Attributes** pane, and then click the ellipsis browse button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
6.  <span data-ttu-id="1d3c3-246">在“键列”\*\*\*\* 对话框的“键列”\*\*\*\* 列表中，验证是否选中了 **CalendarQuarter**，然后单击向下箭头以反转该组合键成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-246">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarQuarter** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="1d3c3-247">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-247">Click **OK**.</span></span>  
  
     <span data-ttu-id="1d3c3-248">现在，属性层次结构成员首先按年份、然后按季度进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-248">The members of the attribute hierarchy are now sorted first by year and then by quarter.</span></span>  
  
7.  <span data-ttu-id="1d3c3-249">在“特性”\*\*\*\* 窗格中，选择“英语月份名称”\*\*\*\*，然后单击“属性”窗口中 **KeyColumns** 属性的省略号按钮 (**...**)。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-249">Select **English Month Name** in the **Attributes** pane, and then click the ellipsis button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
8.  <span data-ttu-id="1d3c3-250">在“键列”\*\*\*\* 对话框的“键列”\*\*\*\* 列表中，验证是否选中了 **EnglishMonthName**，然后单击向下箭头以反转该组合键成员的顺序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-250">In the **Key Columns** list of the **Key Columns** dialog box, verify that **EnglishMonthName** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="1d3c3-251">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-251">Click **OK**.</span></span>  
  
     <span data-ttu-id="1d3c3-252">现在，属性层次结构成员首先按年份、然后按月份进行排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-252">The members of the attribute hierarchy are now sorted first by year and then by month.</span></span>  
  
9. <span data-ttu-id="1d3c3-253">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-253">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span> <span data-ttu-id="1d3c3-254">部署成功完成后，单击维度的维度设计器中的 "**浏览器**" 选项卡 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-254">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the `Date` dimension.</span></span>  
  
10. <span data-ttu-id="1d3c3-255">在“浏览器”\*\*\*\* 项卡的工具栏上，单击“重新连接”按钮。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-255">On the toolbar of the **Browser** tab, click the Reconnect button.</span></span>  
  
11. <span data-ttu-id="1d3c3-256">查看“日历季度”\*\*\*\* 和“日历半期”\*\*\*\* 属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-256">Review the members of the **Calendar Quarter** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="1d3c3-257">注意，这些层次结构的成员现在按时间顺序排序，首先按年份、然后分别按季度或半期排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-257">Notice that the members of these hierarchies are now sorted in chronological order, by year and then by quarter or semester, respectively.</span></span>  
  
12. <span data-ttu-id="1d3c3-258">查看“英语月份名称”\*\*\*\* 属性层次结构的成员。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-258">Review the members of the **English Month Name** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="1d3c3-259">注意，层次结构成员首先按年份然后按月份的字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-259">Notice that the members of the hierarchy are now sorted first by year and then alphabetically by month.</span></span> <span data-ttu-id="1d3c3-260">这是因为“数据源”视图中 EnglishCalendarMonth 列的数据类型是字符串列，它基于基础关系数据库中的 nvarchar 数据类型。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-260">This is because the data type for the EnglishCalendarMonth column in the data source view is a string column, based on the nvarchar data type in the underlying relational database.</span></span> <span data-ttu-id="1d3c3-261">有关如何对每年内的月份按时间顺序进行排序的信息，请参阅 [根据辅助属性对属性成员进行排序](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3c3-261">For information about how to enable the months to be sorted chronologically within each year, see [Sorting Attribute Members Based on a Secondary Attribute](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1d3c3-262">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="1d3c3-262">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1d3c3-263">浏览已部署的多维数据集</span><span class="sxs-lookup"><span data-stu-id="1d3c3-263">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="1d3c3-264">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d3c3-264">See Also</span></span>  
 [<span data-ttu-id="1d3c3-265">多维模型中的维度</span><span class="sxs-lookup"><span data-stu-id="1d3c3-265">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
