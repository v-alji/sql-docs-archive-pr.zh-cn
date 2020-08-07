---
title: 修改 Customer 维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd5c5c47205a89f8429b0b6f0ba55da266d5e811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588733"
---
# <a name="modifying-the-customer-dimension"></a><span data-ttu-id="ec15a-102">修改“客户”维度</span><span class="sxs-lookup"><span data-stu-id="ec15a-102">Modifying the Customer Dimension</span></span>
  <span data-ttu-id="ec15a-103">可以使用许多不同的方式提高多维数据集中的维度的可用性和功能。</span><span class="sxs-lookup"><span data-stu-id="ec15a-103">There are many different ways that you can increase the usability and functionality of the dimensions in a cube.</span></span> <span data-ttu-id="ec15a-104">在本主题的各任务中，您将修改“客户”维度。</span><span class="sxs-lookup"><span data-stu-id="ec15a-104">In the tasks in this topic, you modify the Customer dimension.</span></span>  
  
## <a name="renaming-attributes"></a><span data-ttu-id="ec15a-105">重命名属性</span><span class="sxs-lookup"><span data-stu-id="ec15a-105">Renaming Attributes</span></span>  
 <span data-ttu-id="ec15a-106">可以使用维度设计器的“维度结构”\*\*\*\* 选项卡更改属性名称。</span><span class="sxs-lookup"><span data-stu-id="ec15a-106">You can change attribute names with the **Dimension Structure** tab of Dimension Designer.</span></span>  
  
#### <a name="to-rename-an-attribute"></a><span data-ttu-id="ec15a-107">重命名属性</span><span class="sxs-lookup"><span data-stu-id="ec15a-107">To rename an attribute</span></span>  
  
1.  <span data-ttu-id="ec15a-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，切换到“客户”维度的“维度设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-108">Switch to **Dimension Designer** for the Customer dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ec15a-109">为此，请在解决方案资源管理器的“维度”\*\*\*\* 节点中双击“客户”\*\*\*\* 维度。</span><span class="sxs-lookup"><span data-stu-id="ec15a-109">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ec15a-110">在“属性”\*\*\*\* 窗格中，右键单击“英语国家/地区区域名”\*\*\*\*，然后单击“重命名”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-110">In the **Attributes** pane, right-click **English Country Region Name**, and then click **Rename**.</span></span> <span data-ttu-id="ec15a-111">将属性的名称更改为 `Country-Region` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-111">Change the name of the attribute to `Country-Region`.</span></span>  
  
3.  <span data-ttu-id="ec15a-112">以相同方法更改以下属性的名称：</span><span class="sxs-lookup"><span data-stu-id="ec15a-112">Change the names of the following attributes in the same manner:</span></span>  
  
    -   <span data-ttu-id="ec15a-113">"**英语教育**" 属性-更改为`Education`</span><span class="sxs-lookup"><span data-stu-id="ec15a-113">**English Education** attribute - change to `Education`</span></span>  
  
    -   <span data-ttu-id="ec15a-114">"**英语职业**" 属性-更改为`Occupation`</span><span class="sxs-lookup"><span data-stu-id="ec15a-114">**English Occupation** attribute - change to `Occupation`</span></span>  
  
    -   <span data-ttu-id="ec15a-115">**省自治区名称**属性-更改为`State-Province`</span><span class="sxs-lookup"><span data-stu-id="ec15a-115">**State Province Name** attribute - change to `State-Province`</span></span>  
  
4.  <span data-ttu-id="ec15a-116">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="ec15a-117">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="ec15a-117">Creating a Hierarchy</span></span>  
 <span data-ttu-id="ec15a-118">通过将属性从“属性”\*\*\*\* 窗格拖至“层次结构”\*\*\*\* 窗格可以创建新的层次结构。</span><span class="sxs-lookup"><span data-stu-id="ec15a-118">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="ec15a-119">创建层次结构</span><span class="sxs-lookup"><span data-stu-id="ec15a-119">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="ec15a-120">将 `Country-Region` 属性从 "**属性**" 窗格拖到 "**层次结构**" 窗格中。</span><span class="sxs-lookup"><span data-stu-id="ec15a-120">Drag the `Country-Region` attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="ec15a-121">将 `State-Province` 属性从 "**属性**" 窗格拖到 " **\<new level>** 层次结构" 窗格中的 "**层次结构**" 窗格下的单元中 `Country-Region` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-121">Drag the `State-Province` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `Country-Region` level.</span></span>  
  
3.  <span data-ttu-id="ec15a-122">将 " **City** " 属性从 "**属性**" 窗格拖到 " **\<new level>** **层次结构**" 窗格中的 "层次结构" 窗格下的单元中 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-122">Drag the **City** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `State-Province` level.</span></span>  
  
4.  <span data-ttu-id="ec15a-123">在 "**维度结构**" 选项卡的 "**层次**结构" 窗格中，右键单击 "**层次**结构" 层次结构的标题栏，选择 "**重命名**"，然后键入 `Customer Geography` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-123">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, select **Rename**, and then type `Customer Geography`.</span></span>  
  
     <span data-ttu-id="ec15a-124">层次结构的名称现在为 `Customer Geography` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-124">The name of the hierarchy is now `Customer Geography`.</span></span>  
  
5.  <span data-ttu-id="ec15a-125">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-125">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="ec15a-126">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="ec15a-126">Adding a Named Calculation</span></span>  
 <span data-ttu-id="ec15a-127">可以向数据源视图的表中添加命名计算，命名计算是一个表示为计算列的 SQL 表达式。</span><span class="sxs-lookup"><span data-stu-id="ec15a-127">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="ec15a-128">该表达式的显示形式和工作方式类似于表中的列。</span><span class="sxs-lookup"><span data-stu-id="ec15a-128">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="ec15a-129">通过命名计算，不必修改基础数据源中的表即可扩展数据源视图中现有表的关系架构。</span><span class="sxs-lookup"><span data-stu-id="ec15a-129">Named calculations let you extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="ec15a-130">有关详细信息，请参阅 [在数据源视图中定义命名计算 (Analysis Services)](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="ec15a-130">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="ec15a-131">添加命名计算</span><span class="sxs-lookup"><span data-stu-id="ec15a-131">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="ec15a-132">通过在解决方案资源管理器的 "**数据源视图**" 文件夹中双击\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012\*\*数据源视图，将其打开。</span><span class="sxs-lookup"><span data-stu-id="ec15a-132">Open the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view by double-clicking it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ec15a-133">在左侧的“表”\*\*\*\* 窗格中，右键单击 **Customer**，然后单击“新建命名计算”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-133">In the **Tables** pane on the left, right-click **Customer**, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="ec15a-134">在 "**创建命名计算**" 对话框中，在 `FullName` "**列名称**" 框中键入，然后在 `CASE` "**表达式**" 框中键入或复制并粘贴以下语句：</span><span class="sxs-lookup"><span data-stu-id="ec15a-134">In the **Create Named Calculation** dialog box, type `FullName` in the **Column name** box, and then type or copy and paste the following `CASE` statement in the **Expression** box:</span></span>  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     <span data-ttu-id="ec15a-135">`CASE`语句将**FirstName**、 **MiddleName**和**LastName**列串联为一个列，该列将在 "客户" 维度中用作 "**客户**" 属性的显示名称。</span><span class="sxs-lookup"><span data-stu-id="ec15a-135">The `CASE` statement concatenates the **FirstName**, **MiddleName**, and **LastName** columns into a single column that you will use in the Customer dimension as the displayed name for the **Customer** attribute.</span></span>  
  
4.  <span data-ttu-id="ec15a-136">单击“确定”\*\*\*\*，然后展开“表”\*\*\*\* 窗格中的 **Customer**。</span><span class="sxs-lookup"><span data-stu-id="ec15a-136">Click **OK**, and then expand **Customer** in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="ec15a-137">`FullName`命名计算显示在 Customer 表中的列列表中，并带有一个图标指示它是命名计算。</span><span class="sxs-lookup"><span data-stu-id="ec15a-137">The `FullName` named calculation appears in the list of columns in the Customer table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="ec15a-138">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-138">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="ec15a-139">在“表”\*\*\*\* 窗格中，右键单击 **Customer**，然后单击“浏览数据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-139">In the **Tables** pane, right-click **Customer**, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="ec15a-140">查看“浏览 Customer 表”\*\*\*\* 视图中的最后一列。</span><span class="sxs-lookup"><span data-stu-id="ec15a-140">Review the last column in the **Explore Customer Table** view.</span></span>  
  
     <span data-ttu-id="ec15a-141">请注意， `FullName` 列显示在数据源视图中，它从基础数据源中正确地连接多个列的数据，而不修改原始数据源。</span><span class="sxs-lookup"><span data-stu-id="ec15a-141">Notice that the `FullName` column appears in the data source view, correctly concatenating data from several columns from the underlying data source and without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="ec15a-142">关闭“浏览 Customer 表”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ec15a-142">Close the **Explore Customer Table** tab.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="ec15a-143">将命名计算用于成员名称</span><span class="sxs-lookup"><span data-stu-id="ec15a-143">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="ec15a-144">在数据源视图中创建命名计算后，可以将命名计算用作特性的属性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-144">After you have created a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="ec15a-145">将命名计算用于成员名称</span><span class="sxs-lookup"><span data-stu-id="ec15a-145">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="ec15a-146">切换到“客户”维度的维度设计器。</span><span class="sxs-lookup"><span data-stu-id="ec15a-146">Switch to Dimension Designer for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="ec15a-147">在“维度结构”\*\*\*\* 选项卡的“属性”\*\*\*\* 窗格中，单击“客户键”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-147">In the **Attributes** pane of the **Dimension Structure** tab, click the **Customer Key** attribute.</span></span>  
  
3.  <span data-ttu-id="ec15a-148">打开“属性”窗口并单击标题栏上的“自动隐藏”\*\*\*\* 按钮，以便该窗口保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="ec15a-148">Open the Properties window and click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="ec15a-149">在 "**名称**" 属性字段中，键入 `Full Name` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-149">In the **Name** property field, type `Full Name`.</span></span>  
  
5.  <span data-ttu-id="ec15a-150">单击底部的**NameColumn**属性字段，然后单击 "浏览 () **...** " 按钮以打开 "**名称列**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="ec15a-150">Click in the **NameColumn** property field at the bottom, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
6.  <span data-ttu-id="ec15a-151">选择 " `FullName` **源列**" 列表底部，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="ec15a-151">Select `FullName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ec15a-152">在 "维度结构" 选项卡中，将 `Full Name` 属性从 "**属性**" 窗格拖到 " **\<new level>** **层次**结构" 窗格中 "**城市**" 级别下的单元。</span><span class="sxs-lookup"><span data-stu-id="ec15a-152">In the Dimensions Structure tab, drag the `Full Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **City** level.</span></span>  
  
8.  <span data-ttu-id="ec15a-153">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-153">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-display-folders"></a><span data-ttu-id="ec15a-154">定义显示文件夹</span><span class="sxs-lookup"><span data-stu-id="ec15a-154">Defining Display Folders</span></span>  
 <span data-ttu-id="ec15a-155">可以使用显示文件夹将用户和属性层次结构分组为文件夹结构，以提高可用性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-155">You can use display folders to group user and attribute hierarchies into folder structures to increase usability.</span></span>  
  
#### <a name="to-define-display-folders"></a><span data-ttu-id="ec15a-156">定义显示文件夹</span><span class="sxs-lookup"><span data-stu-id="ec15a-156">To define display folders</span></span>  
  
1.  <span data-ttu-id="ec15a-157">打开“客户”维度的“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ec15a-157">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="ec15a-158">在“属性”\*\*\*\* 窗格中，按住 Ctrl 键的同时单击下列各个属性，将它们选中：</span><span class="sxs-lookup"><span data-stu-id="ec15a-158">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="ec15a-159">**城市**</span><span class="sxs-lookup"><span data-stu-id="ec15a-159">**City**</span></span>  
  
    -   `Country-Region`  
  
    -   <span data-ttu-id="ec15a-160">**邮政编码**</span><span class="sxs-lookup"><span data-stu-id="ec15a-160">**Postal Code**</span></span>  
  
    -   `State-Province`  
  
3.  <span data-ttu-id="ec15a-161">在属性窗口中，单击顶部的**AttributeHierarchyDisplayFolder**属性字段 (可能需要指向它才能看到全名) ，然后键入 `Location` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-161">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top (you might need to point to it to see the full name), and then type `Location`.</span></span>  
  
4.  <span data-ttu-id="ec15a-162">在 "**层次结构**" 窗格中，单击 " `Customer Geography` "，然后在右侧的 "属性窗口中，选择 `Location` 作为**DisplayFolder**属性的值。</span><span class="sxs-lookup"><span data-stu-id="ec15a-162">In the **Hierarchies** pane, click `Customer Geography`, and then in the Properties window on the right, select `Location` as the value of the **DisplayFolder** property.</span></span>  
  
5.  <span data-ttu-id="ec15a-163">在“属性”\*\*\*\* 窗格中，按住 Ctrl 键的同时单击下列各个属性，将它们选中：</span><span class="sxs-lookup"><span data-stu-id="ec15a-163">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="ec15a-164">**上下班路程**</span><span class="sxs-lookup"><span data-stu-id="ec15a-164">**Commute Distance**</span></span>  
  
    -   `Education`  
  
    -   <span data-ttu-id="ec15a-165">**性别**</span><span class="sxs-lookup"><span data-stu-id="ec15a-165">**Gender**</span></span>  
  
    -   <span data-ttu-id="ec15a-166">**House Owner Flag**</span><span class="sxs-lookup"><span data-stu-id="ec15a-166">**House Owner Flag**</span></span>  
  
    -   <span data-ttu-id="ec15a-167">**婚姻状况**</span><span class="sxs-lookup"><span data-stu-id="ec15a-167">**Marital Status**</span></span>  
  
    -   <span data-ttu-id="ec15a-168">**Number Cars Owned**</span><span class="sxs-lookup"><span data-stu-id="ec15a-168">**Number Cars Owned**</span></span>  
  
    -   <span data-ttu-id="ec15a-169">**在家子女数**</span><span class="sxs-lookup"><span data-stu-id="ec15a-169">**Number Children At Home**</span></span>  
  
    -   `Occupation`  
  
    -   <span data-ttu-id="ec15a-170">**Total Children**</span><span class="sxs-lookup"><span data-stu-id="ec15a-170">**Total Children**</span></span>  
  
    -   <span data-ttu-id="ec15a-171">**Yearly Income**</span><span class="sxs-lookup"><span data-stu-id="ec15a-171">**Yearly Income**</span></span>  
  
6.  <span data-ttu-id="ec15a-172">在属性窗口中，单击顶部的 " **AttributeHierarchyDisplayFolder** " 属性字段，然后键入 `Demographic` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-172">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top, and then type `Demographic`.</span></span>  
  
7.  <span data-ttu-id="ec15a-173">在“属性”\*\*\*\* 窗格中，按住 Ctrl 键的同时单击下列各个属性，将它们选中：</span><span class="sxs-lookup"><span data-stu-id="ec15a-173">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="ec15a-174">**电子邮件地址**</span><span class="sxs-lookup"><span data-stu-id="ec15a-174">**Email Address**</span></span>  
  
    -   <span data-ttu-id="ec15a-175">**移动**</span><span class="sxs-lookup"><span data-stu-id="ec15a-175">**Phone**</span></span>  
  
8.  <span data-ttu-id="ec15a-176">在属性窗口中，单击 " **AttributeHierarchyDisplayFolder** " 属性字段，然后键入 `Contacts` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-176">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field and type `Contacts`.</span></span>  
  
9. <span data-ttu-id="ec15a-177">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-177">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns"></a><span data-ttu-id="ec15a-178">定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="ec15a-178">Defining Composite KeyColumns</span></span>  
 <span data-ttu-id="ec15a-179">**KeyColumns** 属性中包含表示特性键的一个或多个列。</span><span class="sxs-lookup"><span data-stu-id="ec15a-179">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="ec15a-180">在本课中，您将创建**城市**和属性的组合键 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-180">In this lesson, you create a composite key for the **City** and `State-Province` attributes.</span></span> <span data-ttu-id="ec15a-181">需要唯一标识属性时，组合键可能会有帮助。</span><span class="sxs-lookup"><span data-stu-id="ec15a-181">Composite keys can be helpful when you need to uniquely identify an attribute.</span></span> <span data-ttu-id="ec15a-182">例如，在本教程的后面部分定义属性关系时， **City**属性必须唯一标识 `State-Province` 属性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-182">For example, when you define attribute relationships later in this tutorial, a **City** attribute must uniquely identify a `State-Province` attribute.</span></span> <span data-ttu-id="ec15a-183">但是，在不同的省/自治区可能有些城市会重名。</span><span class="sxs-lookup"><span data-stu-id="ec15a-183">However, there could be several cities with the same name in different states.</span></span> <span data-ttu-id="ec15a-184">为此，将创建由“市县”\*\*\*\* 属性的 **StateProvinceName** 和 **City**列组成的组合键。</span><span class="sxs-lookup"><span data-stu-id="ec15a-184">For this reason, you will create a composite key that is composed of the **StateProvinceName** and **City** columns for the **City** attribute.</span></span> <span data-ttu-id="ec15a-185">有关详细信息，请参阅 [修改特性的 KeyColumn 属性](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)。</span><span class="sxs-lookup"><span data-stu-id="ec15a-185">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a><span data-ttu-id="ec15a-186">若要为“市县”属性定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="ec15a-186">To define composite KeyColumns for the City attribute</span></span>  
  
1.  <span data-ttu-id="ec15a-187">打开“客户”维度的“维度结构”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="ec15a-187">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="ec15a-188">在“属性”\*\*\*\* 窗格中，单击“市县”\*\*\*\* 属性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-188">In the **Attributes** pane, click the **City** attribute.</span></span>  
  
3.  <span data-ttu-id="ec15a-189">在“属性”\*\*\*\* 窗口中，在靠近底部的 **KeyColumns** 字段中单击，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-189">In the **Properties** window, click in the **KeyColumns** field near the bottom, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="ec15a-190">在“键列”\*\*\*\* 对话框的“可用列”\*\*\*\* 列表中，选择 **StateProvinceName** 列，然后单击 **>** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-190">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **StateProvinceName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="ec15a-191">现在，**City** 和 **StateProvinceName** 列会显示在“键列”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="ec15a-191">The **City** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="ec15a-192">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-192">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="ec15a-193">若要设置“市县”\*\*\*\* 特性的 **NameColumn** 属性，请在“属性”窗口的 **NameColumn** 字段中单击，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-193">To set the **NameColumn** property of the **City** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="ec15a-194">在“名称列” \*\*\*\* 对话框的“源列”\*\*\*\* 列表中，选择 **City**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-194">In the **Name Column** dialog box, in the **Source column** list, select **City**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="ec15a-195">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-195">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a><span data-ttu-id="ec15a-196">为“省/市/自治区”属性定义组合的 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="ec15a-196">To define composite KeyColumns for the State-Province attribute</span></span>  
  
1.  <span data-ttu-id="ec15a-197">确保“客户”维度的“维度结构”\*\*\*\* 选项卡处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="ec15a-197">Make sure the **Dimension Structure** tab for the Customer dimension is open.</span></span>  
  
2.  <span data-ttu-id="ec15a-198">在 "**属性**" 窗格中，单击 `State-Province` 属性。</span><span class="sxs-lookup"><span data-stu-id="ec15a-198">In the **Attributes** pane, click the `State-Province` attribute.</span></span>  
  
3.  <span data-ttu-id="ec15a-199">在“属性”\*\*\*\* 窗口中，在 **KeyColumns** 字段中单击，然后单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-199">In the **Properties** window, click in the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="ec15a-200">在“键列”\*\*\*\* 对话框的“可用列”\*\*\*\* 列表中，选择 **EnglishCountryRegionName** 列，然后单击 **>** 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-200">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **EnglishCountryRegionName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="ec15a-201">现在，**EnglishCountryRegionName** 和 **StateProvinceName** 列会显示在“键列”\*\*\*\* 列表中。</span><span class="sxs-lookup"><span data-stu-id="ec15a-201">The **EnglishCountryRegionName** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="ec15a-202">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-202">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="ec15a-203">若要设置属性的**namecolumn**属性 `State-Province` ，请单击 "属性窗口中的**namecolumn**字段，然后单击" 浏览 (**...**) "按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-203">To set the **NameColumn** property of the `State-Province` attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="ec15a-204">在“名称列”\*\*\*\* 对话框的“源列”\*\*\*\* 列表中，选择 **StateProvinceName**，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-204">In the **Name Column** dialog box, in the **Source column** list, select **StateProvinceName**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="ec15a-205">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-205">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="ec15a-206">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="ec15a-206">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="ec15a-207">如果基础数据支持，则应定义属性间的属性关系。</span><span class="sxs-lookup"><span data-stu-id="ec15a-207">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="ec15a-208">定义属性关系可加快维度、分区和查询处理的速度。</span><span class="sxs-lookup"><span data-stu-id="ec15a-208">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="ec15a-209">有关详细信息，请参阅 [定义属性关系](multidimensional-models/attribute-relationships-define.md) 和 [属性关系](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="ec15a-209">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="ec15a-210">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="ec15a-210">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="ec15a-211">在 "客户" 维度的 "**维度设计器**" 中，单击 "**属性关系**" 选项卡。可能需要等待。</span><span class="sxs-lookup"><span data-stu-id="ec15a-211">In the **Dimension Designer** for the Customer dimension, click the **Attribute Relationships** tab. You might need to wait.</span></span>  
  
2.  <span data-ttu-id="ec15a-212">在关系图中，右键单击“市县”\*\*\*\* 属性，然后单击“新建属性关系”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-212">In the diagram, right-click the **City** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ec15a-213">在“创建属性关系”对话框中，“源属性”是“市县”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-213">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="ec15a-214">将**相关属性**设置为 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-214">Set the **Related Attribute** to `State-Province`.</span></span>  
  
4.  <span data-ttu-id="ec15a-215">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-215">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="ec15a-216">因为各成员之间的关系不会随时间变化，所以此关系类型为“刚性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-216">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span> <span data-ttu-id="ec15a-217">例如，某个市县不太可能成为另一个省/市/自治区的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec15a-217">For example, it would be unusual for a city to become part of a different state or province.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="ec15a-218">在关系图中，右键单击 `State-Province` 属性，然后选择 "**新建属性关系**"。</span><span class="sxs-lookup"><span data-stu-id="ec15a-218">In the diagram, right-click the `State-Province` attribute and then select **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="ec15a-219">在 "**创建属性关系**" 对话框中，"**源属性**" 为 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-219">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `State-Province`.</span></span> <span data-ttu-id="ec15a-220">将**相关属性**设置为 `Country-Region` 。</span><span class="sxs-lookup"><span data-stu-id="ec15a-220">Set the **Related Attribute** to `Country-Region`.</span></span>  
  
8.  <span data-ttu-id="ec15a-221">在“关系类型”列表中，将关系类型设置为“刚性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-221">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="ec15a-222">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-222">Click **OK**.</span></span>  
  
10. <span data-ttu-id="ec15a-223">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-223">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a><span data-ttu-id="ec15a-224">部署更改、处理对象以及查看更改</span><span class="sxs-lookup"><span data-stu-id="ec15a-224">Deploying Changes, Processing the Objects, and Viewing the Changes</span></span>  
 <span data-ttu-id="ec15a-225">更改属性和层次结构后，必须部署更改并重新处理相关对象，然后才能查看这些更改。</span><span class="sxs-lookup"><span data-stu-id="ec15a-225">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a><span data-ttu-id="ec15a-226">部署更改、处理对象以及查看更改</span><span class="sxs-lookup"><span data-stu-id="ec15a-226">To deploy the changes, process the objects, and view the changes</span></span>  
  
1.  <span data-ttu-id="ec15a-227">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-227">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="ec15a-228">在收到“部署成功完成”\*\*\*\* 消息后，单击“客户”维度的维度设计器的“浏览器”\*\*\*\* 选项卡，然后单击设计器工具栏左侧的“重新连接”按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-228">After you receive the **Deployment Completed Successfully** message, click the **Browser** tab of Dimension Designer for the Customer dimension, and then click the Reconnect button on the left side of the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="ec15a-229">验证 `Customer Geography` 是否在 "**层次结构**" 列表中选中，然后在 "浏览器" 窗格中，展开 "**所有**"，展开 "**澳大利亚**"，展开 "**新南威尔士**"，然后展开 " **Coffs Harbour**"。</span><span class="sxs-lookup"><span data-stu-id="ec15a-229">Verify that `Customer Geography` is selected in the **Hierarchy** list, and then in the browser pane, expand **All**, expand **Australia**, expand **New South Wales**, and then expand **Coffs Harbour**.</span></span>  
  
     <span data-ttu-id="ec15a-230">浏览器会将客户显示在市县中。</span><span class="sxs-lookup"><span data-stu-id="ec15a-230">The browser displays the customers in the city.</span></span>  
  
4.  <span data-ttu-id="ec15a-231">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的“多维数据集设计器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-231">Switch to **Cube Designer** for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="ec15a-232">为此，请在“解决方案资源管理器”\*\*\*\* 的“多维数据集”\*\*\*\* 节点中，双击“Analysis Services 教程”\*\*\*\* 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ec15a-232">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="ec15a-233">单击“浏览器”\*\*\*\* 选项卡，然后在设计器的工具栏上单击“重新连接”按钮。</span><span class="sxs-lookup"><span data-stu-id="ec15a-233">Click the **Browser** tab, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
6.  <span data-ttu-id="ec15a-234">在“度量值组”\*\*\*\* 窗格中，展开“客户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ec15a-234">In the **Measure Group** pane, expand **Customer**.</span></span>  
  
     <span data-ttu-id="ec15a-235">注意，“客户”下只出现没有显示文件夹值的显示文件夹和属性，而不显示属性的较长列表。</span><span class="sxs-lookup"><span data-stu-id="ec15a-235">Notice that instead of a long list of attributes, only the display folders and the attributes that do not have display folder values appear underneath Customer.</span></span>  
  
7.  <span data-ttu-id="ec15a-236">在“文件”菜单上，单击“全部保存”。</span><span class="sxs-lookup"><span data-stu-id="ec15a-236">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ec15a-237">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="ec15a-237">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ec15a-238">修改“产品”维度</span><span class="sxs-lookup"><span data-stu-id="ec15a-238">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec15a-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec15a-239">See Also</span></span>  
 <span data-ttu-id="ec15a-240">[维度特性属性参考](multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ec15a-240">[Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="ec15a-241">[从维度中删除属性](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="ec15a-241">[Remove an Attribute from a Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span></span>  
 <span data-ttu-id="ec15a-242">[重命名属性](multidimensional-models/attribute-properties-rename-an-attribute.md) </span><span class="sxs-lookup"><span data-stu-id="ec15a-242">[Rename an Attribute](multidimensional-models/attribute-properties-rename-an-attribute.md) </span></span>  
 [<span data-ttu-id="ec15a-243">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="ec15a-243">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
