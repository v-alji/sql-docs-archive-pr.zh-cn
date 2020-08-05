---
title: 第7课：创建度量值 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: d89ea5c847276c7a34b4fc800d8bed7b9cd8ad34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580970"
---
# <a name="lesson-7-create-measures"></a><span data-ttu-id="4e18d-102">第 7 课：创建度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-102">Lesson 7: Create Measures</span></span>
  <span data-ttu-id="4e18d-103">在本课中，您将创建要包括在您的模型中的度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-103">In this lesson, you will create measures to be included in your model.</span></span> <span data-ttu-id="4e18d-104">与您在前一课中创建的计算列类似，度量值从根本上来说是使用 DAX 公式创建的计算。</span><span class="sxs-lookup"><span data-stu-id="4e18d-104">Similar to the calculated columns you created in the previous lesson, a measure is essentially a calculation created using a DAX formula.</span></span> <span data-ttu-id="4e18d-105">但是，与计算列不同，度量值是基于用户选择的 *筛选器*进行计算的；例如，添加到数据透视表中的“行标签”字段中的特定列或切片器。</span><span class="sxs-lookup"><span data-stu-id="4e18d-105">However, unlike calculated columns, measures are evaluated based on a user selected *filter*; for example, a particular column or slicer added to the Row Labels field in a PivotTable.</span></span>   <span data-ttu-id="4e18d-106">然后，所应用的度量值将计算筛选器中每个单元格的值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-106">A value for each cell in the filter is then calculated by the applied measure.</span></span> <span data-ttu-id="4e18d-107">度量值是功能强大的、灵活的计算，您可以将其包含在几乎所有表格模型中，以便对数值数据执行动态计算。</span><span class="sxs-lookup"><span data-stu-id="4e18d-107">Measures are powerful, flexible calculations that you will want to include in almost all tabular models, to perform dynamic calculations on numerical data.</span></span> <span data-ttu-id="4e18d-108">若要了解详细信息，请参阅[度量值（SSAS 表格）](tabular-models/measures-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="4e18d-108">To learn more, see [Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="4e18d-109">为了创建度量值，您将使用度量值网格。</span><span class="sxs-lookup"><span data-stu-id="4e18d-109">To create measures, you will use the Measure Grid.</span></span> <span data-ttu-id="4e18d-110">默认情况下，每个表都有一个空的度量值网格；但是，您通常不会为每个表创建度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-110">By default, each table has an empty measure grid; however, you typically will not create measures for every table.</span></span> <span data-ttu-id="4e18d-111">在数据视图中时，度量值网格显示在模型设计器中的表下方。</span><span class="sxs-lookup"><span data-stu-id="4e18d-111">The Measure Grid appears below a table in the model designer when in Data View.</span></span> <span data-ttu-id="4e18d-112">若要隐藏或显示表的度量值网格，请单击“表” \*\*\*\* 菜单，然后单击“显示度量值网格” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e18d-112">To hide or show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
 <span data-ttu-id="4e18d-113">可以通过以下方式创建度量值：单击度量值网格中的某个空单元格，并在公式栏中键入一个 DAX 公式。</span><span class="sxs-lookup"><span data-stu-id="4e18d-113">You can create a measure by clicking on an empty cell in the measure grid, and then typing a DAX formula in the formula bar.</span></span> <span data-ttu-id="4e18d-114">当单击 ENTER 以完成公式时，度量值会显示在单元格中。</span><span class="sxs-lookup"><span data-stu-id="4e18d-114">When you click ENTER to complete the formula, the measure will then appear in the cell.</span></span> <span data-ttu-id="4e18d-115">还可以通过以下方式使用标准聚合函数创建度量值：单击某个列，并单击工具栏上的“自动求和”按钮 (**∑**)。</span><span class="sxs-lookup"><span data-stu-id="4e18d-115">You can also create measures using a standard aggregation function by clicking on a column, and then clicking on the AutoSum button (**∑**) on the toolbar.</span></span> <span data-ttu-id="4e18d-116">使用“自动求和”功能创建的度量值将显示在该列正下方的度量值网格单元中，但是可以根据需要移动它们。</span><span class="sxs-lookup"><span data-stu-id="4e18d-116">Measures created using the AutoSum feature will appear in the measure grid cell directly beneath the column, but can be moved if necessary.</span></span>  
  
 <span data-ttu-id="4e18d-117">在本课中，您将通过在编辑栏中输入一个 DAX 公式并使用“自动求和”功能来创建度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-117">In this lesson, you will create measures by both entering a DAX formula in the formula bar and by using the AutoSum feature.</span></span>  
  
 <span data-ttu-id="4e18d-118">学完本课的估计时间： **30 分钟**</span><span class="sxs-lookup"><span data-stu-id="4e18d-118">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e18d-119">先决条件</span><span class="sxs-lookup"><span data-stu-id="4e18d-119">Prerequisites</span></span>  
 <span data-ttu-id="4e18d-120">本主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="4e18d-120">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="4e18d-121">在执行本课程中的任务之前，应该已完成上一课： [第 6 课：创建计算列](lesson-5-create-calculated-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4e18d-121">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 6: Create Calculated Columns](lesson-5-create-calculated-columns.md).</span></span>  
  
## <a name="create-measures"></a><span data-ttu-id="4e18d-122">创建度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-122">Create Measures</span></span>  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a><span data-ttu-id="4e18d-123">在 Date 表中创建 Days Current Quarter to Date 度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-123">To create a Days Current Quarter to Date measure in the Date table</span></span>  
  
1.  <span data-ttu-id="4e18d-124">在模型设计器中，单击“Date”\*\*\*\* 表。</span><span class="sxs-lookup"><span data-stu-id="4e18d-124">In the model designer, click the **Date** table.</span></span>  
  
2.  <span data-ttu-id="4e18d-125">如果表下方尚未显示空的度量值网格，请单击“表”\*\*\*\* 菜单，然后单击“显示度量值网格”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e18d-125">If an empty measure grid does not already appear beneath the table, click on the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
3.  <span data-ttu-id="4e18d-126">在度量值网格中，单击左上角的空单元格。</span><span class="sxs-lookup"><span data-stu-id="4e18d-126">In the measure grid, click the top-left empty cell.</span></span>  
  
4.  <span data-ttu-id="4e18d-127">在表上方的公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="4e18d-127">In the formula bar, above the table, type the following formula:</span></span>  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     <span data-ttu-id="4e18d-128">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="4e18d-128">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="4e18d-129">请注意，左上角的单元格现在包含度量值名称、**度量值 1**，后跟结果**30**。</span><span class="sxs-lookup"><span data-stu-id="4e18d-129">Notice the top-left cell now contains a measure name, **Measure 1**, followed by the result, **30**.</span></span> <span data-ttu-id="4e18d-130">在编辑栏中，度量值名称也位于公式前。</span><span class="sxs-lookup"><span data-stu-id="4e18d-130">The measure name also precedes the formula in the formula bar.</span></span>  
  
5.  <span data-ttu-id="4e18d-131">若要重命名该度量值，请在编辑栏中突出显示名称、**度量值 1**，然后键入 `Days Current Quarter to Date` ，然后按 enter。</span><span class="sxs-lookup"><span data-stu-id="4e18d-131">To rename the measure, in the formula bar, highlight the name, **Measure  1**, then type `Days Current Quarter to Date`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="4e18d-132">在编辑栏中键入公式时，您还可以首先键入度量值名称后跟冒号 (:)，然后输入一个空格，最后输入公式。</span><span class="sxs-lookup"><span data-stu-id="4e18d-132">When typing a formula in the formula bar, you can also first type the measure name followed by a colon (:), followed by a space, and then followed by the formula.</span></span> <span data-ttu-id="4e18d-133">使用此方法，您不必重命名度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-133">Using this method, you do not have to rename the measure.</span></span>  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a><span data-ttu-id="4e18d-134">在 Date 表中创建 Days in Current Quarter 度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-134">To create a Days in Current Quarter measure in the Date table</span></span>  
  
1.  <span data-ttu-id="4e18d-135">当“Date”\*\*\*\* 表在模型设计器中仍处于活动状态时，在度量值网格中，单击刚才创建的度量值下方的空单元。</span><span class="sxs-lookup"><span data-stu-id="4e18d-135">With the **Date** table still active in the model designer, in the measure grid, click the empty cell below the measure you just created.</span></span>  
  
2.  <span data-ttu-id="4e18d-136">在公式栏中，键入以下公式：</span><span class="sxs-lookup"><span data-stu-id="4e18d-136">In the formula bar, type the following formula:</span></span>  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     <span data-ttu-id="4e18d-137">请注意，在此公式中，首先包含了后跟一个冒号 (:) 的度量值名称。</span><span class="sxs-lookup"><span data-stu-id="4e18d-137">Notice in this formula you first included the measure name followed by a colon (:).</span></span>  
  
     <span data-ttu-id="4e18d-138">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="4e18d-138">When you have finished building the formula, press ENTER.</span></span>  
  
 <span data-ttu-id="4e18d-139">在创建不完整期间与上一期间之间的对比率时，公式必须考虑该期间已过时间的比例，并将其与上一期间中的同一时间比例进行比较。</span><span class="sxs-lookup"><span data-stu-id="4e18d-139">When creating a comparison ratio between one incomplete period and the previous period; the formula must take into account the proportion of the period that has elapsed, and compare it to the same proportion in the previous period.</span></span> <span data-ttu-id="4e18d-140">在此情况下，[Days Current Quarter to Date]/[Days in Current Quarter] 给出当前期间中已消逝的比例。</span><span class="sxs-lookup"><span data-stu-id="4e18d-140">In this case, [Days Current Quarter to Date]/[Days in Current Quarter] gives the proportion elapsed in the current period.</span></span>  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a><span data-ttu-id="4e18d-141">在 Internet Sales 表中创建 Internet Distinct Count Sales Order 度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-141">To create an Internet Distinct Count Sales Order measure in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="4e18d-142">在模型设计器中，单击“Internet Sales”\*\*\*\* 表（选项卡）。</span><span class="sxs-lookup"><span data-stu-id="4e18d-142">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
     <span data-ttu-id="4e18d-143">如果尚未显示度量值网格，请右键单击“Internet Sales”\*\*\*\* 表（选项卡），然后单击“显示度量值网格”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e18d-143">If the measure grid does not already appear, right-click the **Internet Sales** table (tab), and then click **Show Measure Grid**.</span></span>  
  
2.  <span data-ttu-id="4e18d-144">单击“Sales Order Number”\*\*\*\* 列标题。</span><span class="sxs-lookup"><span data-stu-id="4e18d-144">Click on the **Sales Order Number** column heading.</span></span>  
  
3.  <span data-ttu-id="4e18d-145">在工具栏上，单击“自动求和”(**∑**) 按钮旁边的向下箭头，然后选择“DistinctCount” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e18d-145">On the toolbar, click the down-arrow next to the AutoSum (**∑**) button, and then select **DistinctCount**.</span></span>  
  
     <span data-ttu-id="4e18d-146">“自动求和”功能会自动使用 DistinctCount 标准聚合公式为所选的列创建一个度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-146">The AutoSum feature automatically creates a measure for the selected column using the DistinctCount standard aggregation formula.</span></span>  
  
     <span data-ttu-id="4e18d-147">请注意，度量值网格中该列之下的顶部单元现包含度量值名称 **Distinct Count Sales Order Number**。</span><span class="sxs-lookup"><span data-stu-id="4e18d-147">Notice the top cell below the column in the measure grid now contains a measure name, **Distinct Count Sales Order Number**.</span></span> <span data-ttu-id="4e18d-148">使用“自动求和”功能创建的度量值将自动放入关联列下方度量值网格中的最顶部单元中。</span><span class="sxs-lookup"><span data-stu-id="4e18d-148">Measures created using the AutoSum feature are automatically placed in the top-most cell in the measure grid below the associated column.</span></span>  
  
4.  <span data-ttu-id="4e18d-149">在度量值网格中，单击新度量值，然后在“属性”\*\*\*\* 窗口的“度量值名称”\*\*\*\* 中，将度量值重命名为 **Internet Distinct Count Sales Order**。</span><span class="sxs-lookup"><span data-stu-id="4e18d-149">In the measure grid, click the new measure, and then in the **Properties** window, in **Measure Name**, rename the measure to **Internet Distinct Count Sales Order**.</span></span>  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a><span data-ttu-id="4e18d-150">在 Internet Sales 表中创建额外的度量值</span><span class="sxs-lookup"><span data-stu-id="4e18d-150">To create additional measures in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="4e18d-151">使用“自动求和”功能创建并命名以下度量值：</span><span class="sxs-lookup"><span data-stu-id="4e18d-151">By using the AutoSum feature, create and name the following measures:</span></span>  
  
    |<span data-ttu-id="4e18d-152">“度量值名称”</span><span class="sxs-lookup"><span data-stu-id="4e18d-152">Measure Name</span></span>|<span data-ttu-id="4e18d-153">列</span><span class="sxs-lookup"><span data-stu-id="4e18d-153">Column</span></span>|<span data-ttu-id="4e18d-154">自动求和 (∑)</span><span class="sxs-lookup"><span data-stu-id="4e18d-154">AutoSum (∑)</span></span>|<span data-ttu-id="4e18d-155">公式</span><span class="sxs-lookup"><span data-stu-id="4e18d-155">Formula</span></span>|  
    |------------------|------------|-------------------|-------------|  
    |<span data-ttu-id="4e18d-156">Internet Order Lines Count</span><span class="sxs-lookup"><span data-stu-id="4e18d-156">Internet Order Lines Count</span></span>|<span data-ttu-id="4e18d-157">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="4e18d-157">Sales Order Line Number</span></span>|<span data-ttu-id="4e18d-158">计数</span><span class="sxs-lookup"><span data-stu-id="4e18d-158">Count</span></span>|<span data-ttu-id="4e18d-159">=COUNT([Sales Order Line Number])</span><span class="sxs-lookup"><span data-stu-id="4e18d-159">=COUNT([Sales Order Line Number])</span></span>|  
    |<span data-ttu-id="4e18d-160">Internet Total Units</span><span class="sxs-lookup"><span data-stu-id="4e18d-160">Internet Total Units</span></span>|<span data-ttu-id="4e18d-161">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="4e18d-161">Order Quantity</span></span>|<span data-ttu-id="4e18d-162">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-162">Sum</span></span>|<span data-ttu-id="4e18d-163">=SUM([Order Quantity])</span><span class="sxs-lookup"><span data-stu-id="4e18d-163">=SUM([Order Quantity])</span></span>|  
    |<span data-ttu-id="4e18d-164">Internet Total Discount Amount</span><span class="sxs-lookup"><span data-stu-id="4e18d-164">Internet Total Discount Amount</span></span>|<span data-ttu-id="4e18d-165">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="4e18d-165">Discount Amount</span></span>|<span data-ttu-id="4e18d-166">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-166">Sum</span></span>|<span data-ttu-id="4e18d-167">=SUM([Discount Amount])</span><span class="sxs-lookup"><span data-stu-id="4e18d-167">=SUM([Discount Amount])</span></span>|  
    |<span data-ttu-id="4e18d-168">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e18d-168">Internet Total Product Cost</span></span>|<span data-ttu-id="4e18d-169">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="4e18d-169">Total Product Cost</span></span>|<span data-ttu-id="4e18d-170">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-170">Sum</span></span>|<span data-ttu-id="4e18d-171">=SUM([Total Product Cost])</span><span class="sxs-lookup"><span data-stu-id="4e18d-171">=SUM([Total Product Cost])</span></span>|  
    |<span data-ttu-id="4e18d-172">Internet Total Sales</span><span class="sxs-lookup"><span data-stu-id="4e18d-172">Internet Total Sales</span></span>|<span data-ttu-id="4e18d-173">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="4e18d-173">Sales Amount</span></span>|<span data-ttu-id="4e18d-174">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-174">Sum</span></span>|<span data-ttu-id="4e18d-175">=SUM([Sales Amount])</span><span class="sxs-lookup"><span data-stu-id="4e18d-175">=SUM([Sales Amount])</span></span>|  
    |<span data-ttu-id="4e18d-176">Internet Total Margin</span><span class="sxs-lookup"><span data-stu-id="4e18d-176">Internet Total Margin</span></span>|<span data-ttu-id="4e18d-177">Margin</span><span class="sxs-lookup"><span data-stu-id="4e18d-177">Margin</span></span>|<span data-ttu-id="4e18d-178">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-178">Sum</span></span>|<span data-ttu-id="4e18d-179">=SUM([Margin])</span><span class="sxs-lookup"><span data-stu-id="4e18d-179">=SUM([Margin])</span></span>|  
    |<span data-ttu-id="4e18d-180">Internet Total Tax Amt</span><span class="sxs-lookup"><span data-stu-id="4e18d-180">Internet Total Tax Amt</span></span>|<span data-ttu-id="4e18d-181">税额</span><span class="sxs-lookup"><span data-stu-id="4e18d-181">Tax Amt</span></span>|<span data-ttu-id="4e18d-182">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-182">Sum</span></span>|<span data-ttu-id="4e18d-183">=SUM([Tax Amt])</span><span class="sxs-lookup"><span data-stu-id="4e18d-183">=SUM([Tax Amt])</span></span>|  
    |<span data-ttu-id="4e18d-184">Internet Total Freight</span><span class="sxs-lookup"><span data-stu-id="4e18d-184">Internet Total Freight</span></span>|<span data-ttu-id="4e18d-185">Freight</span><span class="sxs-lookup"><span data-stu-id="4e18d-185">Freight</span></span>|<span data-ttu-id="4e18d-186">Sum</span><span class="sxs-lookup"><span data-stu-id="4e18d-186">Sum</span></span>|<span data-ttu-id="4e18d-187">=SUM([Freight])</span><span class="sxs-lookup"><span data-stu-id="4e18d-187">=SUM([Freight])</span></span>|  
  
2.  <span data-ttu-id="4e18d-188">通过在度量值网格中单击一个空单元并使用编辑栏，创建并命名以下度量值：</span><span class="sxs-lookup"><span data-stu-id="4e18d-188">By clicking on an empty cell in the measure grid, and by using the formula bar, create and name the following measures:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4e18d-189">您必须按顺序创建下列度量值；后面度量值中的公式引用较早的度量值。</span><span class="sxs-lookup"><span data-stu-id="4e18d-189">You must create the following measures in order; formulas in later measures refer to earlier measures.</span></span>  
  
    |<span data-ttu-id="4e18d-190">“度量值名称”</span><span class="sxs-lookup"><span data-stu-id="4e18d-190">Measure Name</span></span>|<span data-ttu-id="4e18d-191">公式</span><span class="sxs-lookup"><span data-stu-id="4e18d-191">Formula</span></span>|  
    |------------------|-------------|  
    |<span data-ttu-id="4e18d-192">Internet Previous Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="4e18d-192">Internet Previous Quarter Margin</span></span>|<span data-ttu-id="4e18d-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="4e18d-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="4e18d-194">Internet Current Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="4e18d-194">Internet Current Quarter Margin</span></span>|<span data-ttu-id="4e18d-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="4e18d-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span></span>|  
    |<span data-ttu-id="4e18d-196">Internet Previous Quarter Margin Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="4e18d-196">Internet Previous Quarter Margin Proportion to QTD</span></span>|<span data-ttu-id="4e18d-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="4e18d-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
    |<span data-ttu-id="4e18d-198">Internet Previous Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="4e18d-198">Internet Previous Quarter Sales</span></span>|<span data-ttu-id="4e18d-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="4e18d-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="4e18d-200">Internet Current Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="4e18d-200">Internet Current Quarter Sales</span></span>|<span data-ttu-id="4e18d-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="4e18d-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span></span>|  
    |<span data-ttu-id="4e18d-202">Internet Previous Quarter Sales Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="4e18d-202">Internet Previous Quarter Sales Proportion to QTD</span></span>|<span data-ttu-id="4e18d-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="4e18d-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
  
 <span data-ttu-id="4e18d-204">为 Internet Sales 表创建的度量值可用来分析关键的财务数据，如用户选择的筛选器定义的物料的销售、成本和毛利润率。</span><span class="sxs-lookup"><span data-stu-id="4e18d-204">Measures created for the Internet Sales table can be used to analyze critical financial data such as sales, costs, and profit margin for items defined by the user selected filter.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="4e18d-205">下一步</span><span class="sxs-lookup"><span data-stu-id="4e18d-205">Next Step</span></span>  
 <span data-ttu-id="4e18d-206">若要继续学习本教程，请转到下一课： [第 8 课：创建关键绩效指标](lesson-7-create-key-performance-indicators.md)。</span><span class="sxs-lookup"><span data-stu-id="4e18d-206">To continue this tutorial, go to the next lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
  
