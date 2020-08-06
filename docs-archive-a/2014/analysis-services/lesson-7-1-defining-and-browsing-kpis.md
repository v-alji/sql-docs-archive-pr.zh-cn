---
title: 定义和浏览 Kpi |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 648b9a02-1278-4f11-b940-6f0de6a4042d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44febe6c6c5d432f0cdee43e8eaaa3401c54a2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689094"
---
# <a name="defining-and-browsing-kpis"></a><span data-ttu-id="4dfb6-102">定义和浏览 KPI</span><span class="sxs-lookup"><span data-stu-id="4dfb6-102">Defining and Browsing KPIs</span></span>
  <span data-ttu-id="4dfb6-103">若要定义关键绩效指标 (KPI)，应该先定义与 KPI 关联的 KPI 名称和度量值组。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-103">To define key performance indicators (KPIs), you first define a KPI name and the measure group to which the KPI is associated.</span></span> <span data-ttu-id="4dfb6-104">KPI 可以与所有度量值组或与单个度量值组关联。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-104">A KPI can be associated with all measure groups or with a single measure group.</span></span> <span data-ttu-id="4dfb6-105">然后定义以下 KPI 元素：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-105">You then define the following elements of the KPI:</span></span>

-   <span data-ttu-id="4dfb6-106">值表达式</span><span class="sxs-lookup"><span data-stu-id="4dfb6-106">The value expression</span></span>

     <span data-ttu-id="4dfb6-107">值表达式是物理度量值（如销售）、计算度量值（如利润）或使用多维表达式 (MDX) 表达式在 KPI 中定义的计算。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-107">A value expression is a physical measure such as Sales, a calculated measure such as Profit, or a calculation that is defined within the KPI by using a Multidimensional Expressions (MDX) expression.</span></span>

-   <span data-ttu-id="4dfb6-108">目标表达式</span><span class="sxs-lookup"><span data-stu-id="4dfb6-108">The goal expression</span></span>

     <span data-ttu-id="4dfb6-109">目标表达式是值或者是解析为值的 MDX 表达式，它用于定义值表达式所定义的度量值的目标。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-109">A goal expression is a value, or an MDX expression that resolves to a value, that defines the target for the measure that the value expression defines.</span></span> <span data-ttu-id="4dfb6-110">例如，目标表达式可以是公司业务经理希望增加的销售额或利润的数量。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-110">For example, a goal expression could be the amount by which the business managers of a company want to increase sales or profit.</span></span>

-   <span data-ttu-id="4dfb6-111">状态表达式</span><span class="sxs-lookup"><span data-stu-id="4dfb6-111">The status expression</span></span>

     <span data-ttu-id="4dfb6-112">状态表达式是 MDX 表达式， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用它来计算值表达式与目标表达式相比较的当前状态。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-112">A status expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current status of the value expression compared to the goal expression.</span></span> <span data-ttu-id="4dfb6-113">目标表达式的正常取值范围是 -1 到 +1。其中 -1 表示非常差，而 +1 表示非常好。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-113">A goal expression is a normalized value in the range of -1 to +1, where -1 is very bad, and +1 is very good.</span></span> <span data-ttu-id="4dfb6-114">状态表达式会显示图形，以帮助您易于确定值表达式与目标表达式相比较的状态。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-114">The status expression displays a graphic to help you easily determine the status of the value expression compared to the goal expression.</span></span>

-   <span data-ttu-id="4dfb6-115">走向表达式</span><span class="sxs-lookup"><span data-stu-id="4dfb6-115">The trend expression</span></span>

     <span data-ttu-id="4dfb6-116">走向表达式是 MDX 表达式， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用它来计算与目标表达式相比，值表达式的当前走向。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-116">A trend expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current trend of the value expression compared to the goal expression.</span></span> <span data-ttu-id="4dfb6-117">走向表达式可帮助业务用户快速确定值表达式相对于目标表达式，是正在变得更好还是更差。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-117">The trend expression helps the business user to quickly determine whether the value expression is becoming better or worse relative to the goal expression.</span></span> <span data-ttu-id="4dfb6-118">可以将几个图形中的某一个与走向表达式关联，以便帮助业务用户能够快速地了解走向。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-118">You can associate one of several graphics with the trend expression to help business users be able to quickly understand the trend.</span></span>

 <span data-ttu-id="4dfb6-119">除了为 KPI 定义的这些元素以外，还要为 KPI 定义几个属性。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-119">In addition to these elements that you define for a KPI, you also define several properties of a KPI.</span></span> <span data-ttu-id="4dfb6-120">这些属性包括显示文件夹、父 KPI（如果 KPI 是从其他 KPI 计算得到的）、当前时间成员（如果有）、KPI 的权重（如果有）和 KPI 的说明。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-120">These properties include a display folder, a parent KPI if the KPI is computed from other KPIs, the current time member if there is one, the weight of the KPI if it has one, and a description of the KPI.</span></span>

> [!NOTE]
>  <span data-ttu-id="4dfb6-121">有关 KPI 的更多示例，请参阅“计算工具”窗格中“模板”选项卡上或 **Adventure Works DW 2012** 示例数据仓库示例中的 KPI 示例。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-121">For more examples of KPIs, see the KPI examples on the Templates tab in the Calculation Tools pane or in the examples in the **Adventure Works DW 2012** sample data warehouse.</span></span> <span data-ttu-id="4dfb6-122">有关如何安装此数据库的详细信息，请参阅 [安装 Analysis Services 多维建模教程的示例数据和项目](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-122">For more information about how to install this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

 <span data-ttu-id="4dfb6-123">在本主题的任务中，您将在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 项目中定义 KPI，然后使用这些 KPI 来浏览 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-123">In the task in this lesson, you define  KPIs in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, and you then browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube by using these KPIs.</span></span> <span data-ttu-id="4dfb6-124">将定义下列 KPI：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-124">You will define the following KPIs:</span></span>

-   <span data-ttu-id="4dfb6-125">分销商收入</span><span class="sxs-lookup"><span data-stu-id="4dfb6-125">Reseller Revenue</span></span>

     <span data-ttu-id="4dfb6-126">此 KPI 用来度量如何将实际的分销商销售额与分销商销售的销售额进行比较、销售额与目标的距离以及达到目标的走向。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-126">This KPI is used to measure how actual reseller sales compare to sales quotas for reseller sales, how close the sales are to the goal, and what the trend is toward reaching the goal.</span></span>

-   <span data-ttu-id="4dfb6-127">产品毛利润率</span><span class="sxs-lookup"><span data-stu-id="4dfb6-127">Product Gross Profit Margin</span></span>

     <span data-ttu-id="4dfb6-128">此 KPI 用来确定每个产品类别的毛利润率与每个产品的指定目标的接近程度，还用来确定达到此目标的趋势。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-128">This KPI is used to determine how close the gross profit margin is for each product category to a specified goal for each product category, and also to determine the trend toward reaching this goal.</span></span>

## <a name="defining-the-reseller-revenue-kpi"></a><span data-ttu-id="4dfb6-129">定义“分销商收入”KPI</span><span class="sxs-lookup"><span data-stu-id="4dfb6-129">Defining the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="4dfb6-130">打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后单击“KPI”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-130">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **KPIs** tab.</span></span>

     <span data-ttu-id="4dfb6-131">**KPI** 选项卡包括几个窗格。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-131">The **KPIs** tab includes several panes.</span></span> <span data-ttu-id="4dfb6-132">在选项卡的左侧是“KPI 组织程序”\*\*\*\* 窗格和“计算工具”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-132">On the left side of the tab are the **KPI Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="4dfb6-133">该选项卡中间的显示窗格包含了在“KPI 组织程序”\*\*\*\* 窗格中选择的 KPI 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-133">The display pane in the middle of the tab contains the details of the KPI that is selected in the **KPI Organizer** pane.</span></span>

     <span data-ttu-id="4dfb6-134">下图显示了多维数据集设计器的“KPI”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-134">The following image shows the **KPIs** tab of Cube Designer.</span></span>

     <span data-ttu-id="4dfb6-135">![多维数据集设计器的 KPI 选项卡](../../2014/tutorials/media/l7-kpi-1.gif "多维数据集设计器的 KPI 选项卡")</span><span class="sxs-lookup"><span data-stu-id="4dfb6-135">![KPIs tab of Cube Designer](../../2014/tutorials/media/l7-kpi-1.gif "KPIs tab of Cube Designer")</span></span>

2.  <span data-ttu-id="4dfb6-136">在“KPI”\*\*\*\* 选项卡的工具栏上，单击“新建 KPI”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-136">On the toolbar of the **KPIs** tab, click the **New KPI** button.</span></span>

     <span data-ttu-id="4dfb6-137">显示窗格中将出现空白 KPI 模板，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-137">A blank KPI template appears in the display pane, as shown in the following image.</span></span>

     <span data-ttu-id="4dfb6-138">![显示窗格中的空白 KPI 模板](../../2014/tutorials/media/l7-kpi-2.gif "显示窗格中的空白 KPI 模板")</span><span class="sxs-lookup"><span data-stu-id="4dfb6-138">![Blank KPI template in display pane](../../2014/tutorials/media/l7-kpi-2.gif "Blank KPI template in display pane")</span></span>

3.  <span data-ttu-id="4dfb6-139">在 "**名称**" 框中，键入 `Reseller Revenue` ，然后选择 "关联的**度量值组**" 列表中的 "**分销商销售额**"。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-139">In the **Name** box, type `Reseller Revenue`, and then select **Reseller Sales** in the **Associated measure group** list.</span></span>

4.  <span data-ttu-id="4dfb6-140">在“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡上，展开“度量值”\*\*\*\*，再展开“分销商销售”\*\*\*\*，然后将“分销商销售额”\*\*\*\* 度量值拖到“值表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Reseller Sales**, and then drag the **Reseller Sales-Sales Amount** measure to the **Value Expression** box.</span></span>

5.  <span data-ttu-id="4dfb6-141">在“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡上，展开“度量值”\*\*\*\*，再展开“销售配额”\*\*\*\*，再将“销售配额”\*\*\*\* 度量值拖到“目标表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-141">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Sales Quotas**, and then drag the **Sales Amount Quota** measure to the **Goal Expression** box.</span></span>

6.  <span data-ttu-id="4dfb6-142">验证是否在“状态指示器”\*\*\*\* 列表中选中“测量”\*\*\*\*，然后在“状态表达式”\*\*\*\* 框中键入以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-142">Verify that **Gauge** is selected in the **Status indicator** list, and then type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
     When 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.95
       Then 1
     When
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")<.95
       And 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.85
       Then 0
      Else-1
    End
    ```

     <span data-ttu-id="4dfb6-143">此 MDX 表达式为计算目标的完成进度提供基本算法。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-143">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span> <span data-ttu-id="4dfb6-144">在此 MDX 表达式中，如果实际的分销商销售额超过目标的 85%，则用值 0 来填充所选图形。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-144">In this MDX expression, if actual reseller sales are more than 85 percent of the goal, a value of 0 is used to populate the chosen graphic.</span></span> <span data-ttu-id="4dfb6-145">由于测量是选择的图形，因此测量中的指针将位于空和满的中间。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-145">Because a gauge is the chosen graphic, the pointer in the gauge will be half-way between empty and full.</span></span> <span data-ttu-id="4dfb6-146">如果实际的分销商销售额超过了 90%，则测量上的指针将位于空和满之间的四分之三处。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-146">If actual reseller sales are more the 90 percent, the pointer on the gauge will be three-fourths of the way between empty and full.</span></span>

7.  <span data-ttu-id="4dfb6-147">验证是否在“走向指示器”\*\*\*\* 列表中选择了“标准箭头”\*\*\*\*，然后在“走向表达式”\*\*\*\* 框中键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-147">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following expression in the **Trend expression** box:</span></span>

    ```
    Case
     When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
     When  (
      KpiValue("Reseller Revenue") - 
       (KpiValue("Reseller Revenue"), 
        ParallelPeriod
         ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
          /
          (KpiValue ("Reseller Revenue"),
           ParallelPeriod
            ([Date].[Calendar Date].[Calendar Year],1,
             [Date].[Calendar Date].CurrentMember)))
           >=.02
      Then 1
       When(
        KpiValue("Reseller Revenue") - 
         (KpiValue ( "Reseller Revenue" ),
          ParallelPeriod
           ([Date].[Calendar Date].[Calendar Year],1,
            [Date].[Calendar Date].CurrentMember))
           /
            (KpiValue("Reseller Revenue"),
             ParallelPeriod
              ([Date].[Calendar Date].[Calendar Year],1,
                [Date].[Calendar Date].CurrentMember)))
            <=.02
      Then -1
       Else 0
    End
    ```

     <span data-ttu-id="4dfb6-148">此 MDX 表达式为计算预定目标的完成趋势提供基本算法。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-148">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-reseller-revenue-kpi"></a><span data-ttu-id="4dfb6-149">通过使用“分销商收入”KPI 浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="4dfb6-149">Browsing the Cube by Using the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="4dfb6-150">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-150">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="4dfb6-151">成功完成部署后，请在“KPI”\*\*\*\* 选项卡的工具栏上单击“浏览器视图”\*\*\*\* 按钮，然后单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-151">When deployment has successfully completed, on the toolbar of the **KPIs** tab, click the **Browser View** button, and then click **Reconnect**.</span></span>

     <span data-ttu-id="4dfb6-152">状态和走向测量将基于每个维度的默认成员的值，与值和目标的值一起，显示在分销商销售的“KPI 浏览器”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-152">The status and trend gauges are displayed in the **KPI Browser** pane for reseller sales based on the values for the default member of each dimension, together with the value for the value and the goal.</span></span> <span data-ttu-id="4dfb6-153">因为尚未将任何维度的任何其他成员定义为默认成员，所以每个维度的默认成员都是“所有”级别的“所有”成员。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-153">The default member of each dimension is the All member of the All level, because you have not defined any other member of any dimension as the default member.</span></span>

3.  <span data-ttu-id="4dfb6-154">在“筛选器”窗格中，在“维度”\*\*\*\* 列表中选择“销售区域”\*\*\*\*、在“层次结构”\*\*\*\* 列表中选择“销售区域”\*\*\*\*、在“运算符”\*\*\*\* 列表中选择“等于”\*\*\*\*、在“筛选表达式”\*\*\*\* 列表中选中“北美洲”\*\*\*\* 复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-154">In the filter pane, select **Sales Territory** in the **Dimension** list, select **Sales Territories** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **North America** check box in the **Filter Expression** list, and then click **OK**.</span></span>

4.  <span data-ttu-id="4dfb6-155">在“筛选器”\*\*\*\* 窗格的下一行中，依次选择“维度”\*\*\*\* 列表中的“日期”\*\*\*\*、“层次结构”\*\*\*\* 列表中的“日历日期”\*\*\*\*、“运算符”\*\*\*\* 列表中的“等于”\*\*\*\*，并选中“筛选表达式”\*\*\*\* 列表中的“Q3 CY 2007”\*\*\*\* 复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-155">In the next row in the **Filter** pane, select **Date** in the **Dimension** list, select **Calendar Date** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **Q3 CY 2007** check box in the **Filter Expression** list, and then click **OK**.</span></span>

5.  <span data-ttu-id="4dfb6-156">单击“KPI 浏览器”\*\*\*\* 窗格中的任意位置，以更新“分销商收入 KPI”\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-156">Click anywhere in the **KPI Browser** pane to update the values for the **Reseller Revenue KPI**.</span></span>

     <span data-ttu-id="4dfb6-157">请注意，KPI 的“值”\*\*\*\*、“目标”\*\*\*\* 和“状态”\*\*\*\* 部分反映了新时间段的值</span><span class="sxs-lookup"><span data-stu-id="4dfb6-157">Notice that the **Value**, **Goal**, and **Status** sections of the KPI reflect the values for the new time period</span></span>

## <a name="defining-the-product-gross-profit-margin-kpi"></a><span data-ttu-id="4dfb6-158">定义“产品毛利润率 KPI”</span><span class="sxs-lookup"><span data-stu-id="4dfb6-158">Defining the Product Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="4dfb6-159">在“KPI”\*\*\*\* 选项卡的工具栏上单击“窗体视图”\*\*\*\* 按钮，然后单击“新建 KPI”\*\*\*\* 按钮。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-159">Click the **Form View** button on the toolbar of the **KPIs** tab, and then click the **New KPI** button.</span></span>

2.  <span data-ttu-id="4dfb6-160">在 "**名称**" 框中键入 `Product Gross Profit Margin` ，然后验证是否 **\<All>** 出现在 "**关联的度量值组**" 列表中。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-160">In the **Name** box, type `Product Gross Profit Margin`, and then verify that **\<All>** appears in the **Associated measure group** list.</span></span>

3.  <span data-ttu-id="4dfb6-161">在“计算工具”\*\*\*\* 窗格内的“元数据”\*\*\*\* 选项卡中，将“总 GPM”\*\*\*\* 度量值拖到“值表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-161">In the **Metadata** tab in the **Calculation Tools** pane, drag the **Total GPM** measure to the **Value Expression** box.</span></span>

4.  <span data-ttu-id="4dfb6-162">在“目标表达式”\*\*\*\* 框中，键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-162">In the **Goal Expression** box, type the following expression:</span></span>

    ```
    Case
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Accessories]
        Then .40                 
        When [Product].[Category].CurrentMember 
          Is [Product].[Category].[Bikes]
        Then .12                
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Clothing]
        Then .20
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Components]
        Then .10
        Else .12            
    End
    ```

5.  <span data-ttu-id="4dfb6-163">在“状态指示器”\*\*\*\* 列表中，选择“柱状”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-163">In the **Status indicator** list, select **Cylinder**.</span></span>

6.  <span data-ttu-id="4dfb6-164">在“状态表达式”\*\*\*\* 框中键入以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-164">Type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .90
        Then 1
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) <  .90
             And 
             KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .80
        Then 0
        Else -1
    End
    ```

     <span data-ttu-id="4dfb6-165">此 MDX 表达式为计算目标的完成进度提供基本算法。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-165">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span>

7.  <span data-ttu-id="4dfb6-166">验证是否在“走向指示器”\*\*\*\* 列表中选择了“标准箭头”\*\*\*\*，然后在“走向表达式”\*\*\*\* 框中键入以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="4dfb6-166">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following MDX expression in the **Trend expression** box:</span></span>

    ```
    Case
    When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
       When VBA!Abs
        (
          KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            ) /
            (
              KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            )  
          ) <=.02
      Then 0
      When KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[ Calendar Date].[ Calendar Year],
               1,
               [Date].[ Calendar Date].CurrentMember
             )
           ) /
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[Calendar Date].[Calendar Year],
               1,
               [Date].[Calendar Date].CurrentMember
             )
           )  >.02
      Then 1
      Else -1
    End
    ```

     <span data-ttu-id="4dfb6-167">此 MDX 表达式为计算预定目标的完成趋势提供基本算法。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-167">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-total-gross-profit-margin-kpi"></a><span data-ttu-id="4dfb6-168">通过使用“总毛利润率 KPI”浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="4dfb6-168">Browsing the Cube by Using the Total Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="4dfb6-169">在“生成”\*\*\*\* 菜单上，单击“部署 Analysis Services 教程”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-169">On the **Build** menu, click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="4dfb6-170">成功完成部署后，在“KPI”\*\*\*\* 选项卡的工具栏上单击“重新连接”\*\*\*\*，然后单击“浏览器视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-170">When deployment has successfully completed, click **Reconnect** on the toolbar of the **KPIs** tab, and then click **Browser View**.</span></span>

     <span data-ttu-id="4dfb6-171">`Product Gross Profit Margin`此时将显示 kpi，并显示**Q3 CY 2007**和**北美**销售区域的 KPI 值。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-171">The `Product Gross Profit Margin` KPI appears and displays the KPI value for **Q3 CY 2007** and the **North America** sales territory.</span></span>

3.  <span data-ttu-id="4dfb6-172">在“筛选器”\*\*\*\* 窗格中，依次选择“维度”\*\*\*\* 列表中的“产品”\*\*\*\*、“层次结构”\*\*\*\* 列表中的“类别”\*\*\*\*、“运算符”\*\*\*\* 列表中的“等于”\*\*\*\* 和“筛选表达式”\*\*\*\* 列表中的“自行车”\*\*\*\*，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-172">In the **Filter** pane, select **Product** in the **Dimension** list, select **Category** in the **Hierarchy** list, select **Equal** in the **Operator** list, and then select **Bikes** in the **Filter Expression** list, and then click **OK**.</span></span>

     <span data-ttu-id="4dfb6-173">将显示 2007 财年第 3 季度北美洲分销商自行车销售的毛利润率。</span><span class="sxs-lookup"><span data-stu-id="4dfb6-173">The gross profit margin for the sale of Bikes by resellers in North America in Q3 CY 2007 appears.</span></span>

## <a name="next-lesson"></a><span data-ttu-id="4dfb6-174">下一课</span><span class="sxs-lookup"><span data-stu-id="4dfb6-174">Next Lesson</span></span>
 [<span data-ttu-id="4dfb6-175">第 8 课：定义操作</span><span class="sxs-lookup"><span data-stu-id="4dfb6-175">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)


