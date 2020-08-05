---
title: 第6课：创建计算列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcebf61955e230c9e61c955683b897026553cb52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580988"
---
# <a name="lesson-6-create-calculated-columns"></a><span data-ttu-id="63157-102">第 6 课：创建计算列</span><span class="sxs-lookup"><span data-stu-id="63157-102">Lesson 6: Create Calculated Columns</span></span>
  <span data-ttu-id="63157-103">在本课中，将通过添加计算列在模型中创建新数据。</span><span class="sxs-lookup"><span data-stu-id="63157-103">In this lesson, you will create new data in your model by adding calculated columns.</span></span> <span data-ttu-id="63157-104">计算列基于模型中的现有数据。</span><span class="sxs-lookup"><span data-stu-id="63157-104">A calculated column is based on data that already exists in the model.</span></span> <span data-ttu-id="63157-105">了解详细信息，请参阅[计算列（SSAS 表格）](tabular-models/ssas-calculated-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="63157-105">To learn more, see [Calculated Columns &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns.md).</span></span>  
  
 <span data-ttu-id="63157-106">将在三个不同的表中创建五个计算列。</span><span class="sxs-lookup"><span data-stu-id="63157-106">You will create five new calculated columns in three different tables.</span></span> <span data-ttu-id="63157-107">步骤对于每个任务略有不同。</span><span class="sxs-lookup"><span data-stu-id="63157-107">The steps are slightly different for each task.</span></span> <span data-ttu-id="63157-108">这是为了说明有多种方法可用来创建新列、对其进行重命名，以及将其放置在表中的各种位置。</span><span class="sxs-lookup"><span data-stu-id="63157-108">This is to show you there are several ways to create new columns, rename them, and place them in various locations in a table.</span></span>  
  
 <span data-ttu-id="63157-109">学完本课的估计时间： **15 分钟**</span><span class="sxs-lookup"><span data-stu-id="63157-109">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63157-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="63157-110">Prerequisites</span></span>  
 <span data-ttu-id="63157-111">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="63157-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="63157-112">在执行本课程中的任务之前，须已完成上一课： [第 5 课：创建关系](lesson-4-create-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="63157-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
## <a name="create-calculated-columns"></a><span data-ttu-id="63157-113">创建计算列</span><span class="sxs-lookup"><span data-stu-id="63157-113">Create Calculated Columns</span></span>  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a><span data-ttu-id="63157-114">在 Date 表中创建 Month Calendar 计算列</span><span class="sxs-lookup"><span data-stu-id="63157-114">Create a Month Calendar calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="63157-115">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“模型”\*\*\*\* 菜单，然后指向“模型视图”\*\*\*\*，再单击“数据视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63157-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Model View**, and then click **Data View**.</span></span>  
  
     <span data-ttu-id="63157-116">只能在数据视图中使用模型设计器创建计算列。</span><span class="sxs-lookup"><span data-stu-id="63157-116">Calculated columns can only be created by using the model designer in Data View.</span></span>  
  
2.  <span data-ttu-id="63157-117">在模型设计器中，单击“Date”\*\*\*\* 表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="63157-117">In the model designer, click the **Date** table (tab).</span></span>  
  
3.  <span data-ttu-id="63157-118">右键单击 "**日历季度**" 列，然后单击 "**插入列**"。</span><span class="sxs-lookup"><span data-stu-id="63157-118">Right-click the **Calendar Quarter** column, and then click **Insert Column**.</span></span>  
  
     <span data-ttu-id="63157-119">名为**CalculatedColumn1**的新列将插入到 "**日历季度**" 列的左侧。</span><span class="sxs-lookup"><span data-stu-id="63157-119">A new column named **CalculatedColumn1** is inserted to the left of the **Calendar Quarter** column.</span></span>  
  
4.  <span data-ttu-id="63157-120">在表上面的编辑栏中，键入以下公式。</span><span class="sxs-lookup"><span data-stu-id="63157-120">In the formula bar above the table, type the following formula.</span></span> <span data-ttu-id="63157-121">“自动完成”可帮助你键入列和表的完全限定名称，并将列出可用的函数。</span><span class="sxs-lookup"><span data-stu-id="63157-121">AutoComplete helps you type the fully qualified names of columns and tables, and lists the functions that are available.</span></span>  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     <span data-ttu-id="63157-122">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="63157-122">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="63157-123">然后，会在计算列中为所有行填充值。</span><span class="sxs-lookup"><span data-stu-id="63157-123">Values are then populated for all the rows in the calculated column.</span></span> <span data-ttu-id="63157-124">如果在表中向下滚动，会看到，根据每行中的数据，各行中的此列可能具有不同的值。</span><span class="sxs-lookup"><span data-stu-id="63157-124">If you scroll down through the table, you will see that rows can have different values for this column, based on the data that is in each row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63157-125">如果收到错误提示，请验证确保公式中的列名与在 [第 3 课：重命名列](rename-columns.md)中更改的列名是否匹配。</span><span class="sxs-lookup"><span data-stu-id="63157-125">If you receive an error, verify the column names in the formula match the column names you changed in [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
5.  <span data-ttu-id="63157-126">将此列重命名为 `Month Calendar` 。</span><span class="sxs-lookup"><span data-stu-id="63157-126">Rename this column to `Month Calendar`.</span></span>  
  
 <span data-ttu-id="63157-127">Month Calendar 计算列提供可排序的月份名称。</span><span class="sxs-lookup"><span data-stu-id="63157-127">The Month Calendar calculated column provides a sortable name for Month.</span></span>  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a><span data-ttu-id="63157-128">在 Date 表中创建 Day of Week 计算列</span><span class="sxs-lookup"><span data-stu-id="63157-128">Create a Day of Week calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="63157-129">在“Date”\*\*\*\* 表仍处于活动状态时，单击“列”\*\*\*\* 菜单，然后单击“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63157-129">With the **Date** table still active, click on the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="63157-130">一个新列添加到表的最右侧。</span><span class="sxs-lookup"><span data-stu-id="63157-130">A new column is added to the far right of the table</span></span>  
  
2.  <span data-ttu-id="63157-131">在公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="63157-131">In the formula bar, type the following formula:</span></span>  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     <span data-ttu-id="63157-132">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="63157-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="63157-133">将列重命名为 `Day of Week` 。</span><span class="sxs-lookup"><span data-stu-id="63157-133">Rename the column to `Day of Week`.</span></span>  
  
4.  <span data-ttu-id="63157-134">单击列标题，然后将此列拖到“Day Name”\*\*\*\* 列与“Day of Month”\*\*\*\* 列之间。</span><span class="sxs-lookup"><span data-stu-id="63157-134">Click on the column heading, and then drag the column between the **Day Name** column and the **Day of Month** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="63157-135">移动表中的列可使表变得更易于浏览。</span><span class="sxs-lookup"><span data-stu-id="63157-135">Moving columns in your table makes it easier to navigate.</span></span>  
  
 <span data-ttu-id="63157-136">Day of Week 计算列为周内的日期提供可排序的名称。</span><span class="sxs-lookup"><span data-stu-id="63157-136">The Day of Week calculated column provides a sortable name for the day of week.</span></span>  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a><span data-ttu-id="63157-137">在 Product 表中创建 Product Subcategory Name 计算列</span><span class="sxs-lookup"><span data-stu-id="63157-137">Create a Product Subcategory Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="63157-138">在模型设计器中，选择“Product”\*\*\*\* 表。</span><span class="sxs-lookup"><span data-stu-id="63157-138">In the model designer, select the **Product** table.</span></span>  
  
2.  <span data-ttu-id="63157-139">滚动到表的最右侧。</span><span class="sxs-lookup"><span data-stu-id="63157-139">Scroll to the far right of the table.</span></span> <span data-ttu-id="63157-140">请注意，最右侧的列名为“添加列”（斜体），单击列标题。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="63157-140">Notice the right-most column is named **Add Column** (italicized), click the column heading.</span></span>  
  
3.  <span data-ttu-id="63157-141">在公式栏中，键入以下公式。</span><span class="sxs-lookup"><span data-stu-id="63157-141">In the formula bar, type the following formula.</span></span>  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     <span data-ttu-id="63157-142">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="63157-142">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="63157-143">将列重命名为 `Product Subcategory Name` 。</span><span class="sxs-lookup"><span data-stu-id="63157-143">Rename the column to `Product Subcategory Name`.</span></span>  
  
 <span data-ttu-id="63157-144">Product Subcategory Name 计算列用于在 Product 表中创建一个层次结构，其中包括来自 Product Subcategory 表中 Product Subcategory Name 列的数据。</span><span class="sxs-lookup"><span data-stu-id="63157-144">The Product Subcategory Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Subcategory Name column in the Product Subcategory table.</span></span> <span data-ttu-id="63157-145">层次结构不能跨多个表。</span><span class="sxs-lookup"><span data-stu-id="63157-145">Hierarchies cannot span more than one table.</span></span> <span data-ttu-id="63157-146">您将在第 7 课中创建层次结构。</span><span class="sxs-lookup"><span data-stu-id="63157-146">You will create hierarchies later in Lesson 7.</span></span>  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a><span data-ttu-id="63157-147">在 Product 表中创建 Product Category Name 计算列</span><span class="sxs-lookup"><span data-stu-id="63157-147">Create a Product Category Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="63157-148">在“Product”\*\*\*\* 表仍处于活动状态时，单击“列”\*\*\*\* 菜单，然后单击“添加列”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63157-148">With the **Product** table still active, click the **Column** menu, and then click **Add Column**.</span></span>  
  
2.  <span data-ttu-id="63157-149">在公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="63157-149">In the formula bar, type the following formula:</span></span>  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     <span data-ttu-id="63157-150">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="63157-150">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="63157-151">将列重命名为 `Product Category Name` 。</span><span class="sxs-lookup"><span data-stu-id="63157-151">Rename the column to `Product Category Name`.</span></span>  
  
 <span data-ttu-id="63157-152">Product Category Name 计算列用于在 Product 表中创建一个层次结构，其中包括来自 Product Category 表中 Product Category Name 列的数据。</span><span class="sxs-lookup"><span data-stu-id="63157-152">The Product Category Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Category Name column in the Product Category table.</span></span> <span data-ttu-id="63157-153">层次结构不能跨多个表。</span><span class="sxs-lookup"><span data-stu-id="63157-153">Hierarchies cannot span more than one table.</span></span>  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a><span data-ttu-id="63157-154">在 Internet Sales 表中创建 Margin 计算列</span><span class="sxs-lookup"><span data-stu-id="63157-154">Create a Margin calculated column in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="63157-155">在模型设计器中，选择“Internet Sales”\*\*\*\* 表。</span><span class="sxs-lookup"><span data-stu-id="63157-155">In the model designer, select the **Internet Sales** table.</span></span>  
  
2.  <span data-ttu-id="63157-156">添加新列。</span><span class="sxs-lookup"><span data-stu-id="63157-156">Add a new column.</span></span>  
  
3.  <span data-ttu-id="63157-157">在公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="63157-157">In the formula bar, type the following formula:</span></span>  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     <span data-ttu-id="63157-158">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="63157-158">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="63157-159">将列重命名为 `Margin` 。</span><span class="sxs-lookup"><span data-stu-id="63157-159">Rename the column to `Margin`.</span></span>  
  
5.  <span data-ttu-id="63157-160">将此列拖到“Sales Amount”\*\*\*\* 列与“Tax Amt”\*\*\*\* 列之间。</span><span class="sxs-lookup"><span data-stu-id="63157-160">Drag the column between the **Sales Amount** column and the **Tax Amt** column.</span></span>  
  
 <span data-ttu-id="63157-161">Margin 计算列用来分析每个（产品）行的毛利润率。</span><span class="sxs-lookup"><span data-stu-id="63157-161">The Margin calculated column is used to analyze profit margins for each (product) row.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="63157-162">下一步</span><span class="sxs-lookup"><span data-stu-id="63157-162">Next Step</span></span>  
 <span data-ttu-id="63157-163">若要继续学习本课程，请转到下一课： [第 7 课：创建度量值](lesson-6-create-measures.md)。</span><span class="sxs-lookup"><span data-stu-id="63157-163">To continue this lesson, go to the next lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
  
