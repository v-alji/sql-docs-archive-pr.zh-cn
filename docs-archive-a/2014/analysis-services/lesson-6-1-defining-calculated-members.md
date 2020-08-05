---
title: 定义计算成员 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 07f13e1c-0b20-4f9e-ad62-c438983f2785
author: minewiskan
ms.author: owend
ms.openlocfilehash: f2a054356613ebf3d4cf825c1fa4c238a5362ec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580979"
---
# <a name="defining-calculated-members"></a><span data-ttu-id="8cae9-102">定义计算成员</span><span class="sxs-lookup"><span data-stu-id="8cae9-102">Defining Calculated Members</span></span>
  <span data-ttu-id="8cae9-103">计算成员是基于多维数据集数据、算术运算符、数字和函数组合定义的维度或度量值组成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-103">Calculated members are members of a dimension or a measure group that are defined based on a combination of cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="8cae9-104">例如，可以创建用于计算多维数据集中的两个物理度量值之和的计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-104">For example, you can create a calculated member that calculates the sum of two physical measures in the cube.</span></span> <span data-ttu-id="8cae9-105">计算成员定义将存储在多维数据集中，但它们的值将在查询时计算。</span><span class="sxs-lookup"><span data-stu-id="8cae9-105">Calculated member definitions are stored in cubes, but their values are calculated at query time.</span></span>  
  
 <span data-ttu-id="8cae9-106">若要创建计算成员，请在多维数据集设计器的“计算”\*\*\*\* 选项卡上使用“新建计算成员”\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="8cae9-106">To create a calculated member, use the **New Calculated Member** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="8cae9-107">您可以在包括度量值维度在内的任意维度中创建计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-107">You can create a calculated member within any dimension, including the measures dimension.</span></span> <span data-ttu-id="8cae9-108">还可以将计算成员放在“计算属性”\*\*\*\* 对话框的显示文件夹内。</span><span class="sxs-lookup"><span data-stu-id="8cae9-108">You can also place a calculated member within a display folder in the **Calculation Properties** dialog box.</span></span> <span data-ttu-id="8cae9-109">有关详细信息，请参阅 [计算](multidimensional-models-olap-logical-cube-objects/calculations.md)、 [多维模型中的计算](multidimensional-models/calculations-in-multidimensional-models.md)和 [创建计算成员](multidimensional-models/create-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="8cae9-109">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md), and [Create Calculated Members](multidimensional-models/create-calculated-members.md).</span></span>  
  
 <span data-ttu-id="8cae9-110">在此主题的任务中，将定义计算度量值，以便让用户查看 Internet 销售、分销商销售和所有销售的毛利润率百分比和销售率。</span><span class="sxs-lookup"><span data-stu-id="8cae9-110">In the tasks in this topic, you define calculated measures to let users view the gross profit margin percentage and sales ratios for Internet sales, reseller sales, and for all sales.</span></span>  
  
## <a name="defining-calculations-to-aggregate-physical-measures"></a><span data-ttu-id="8cae9-111">定义聚合物理度量值的计算</span><span class="sxs-lookup"><span data-stu-id="8cae9-111">Defining Calculations to Aggregate Physical Measures</span></span>  
  
1.  <span data-ttu-id="8cae9-112">打开 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后单击“计算”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8cae9-112">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="8cae9-113">请注意“计算表达式”\*\*\*\* 窗格和“脚本组织程序”\*\*\*\* 窗格中的默认 CALCULATE 命令。</span><span class="sxs-lookup"><span data-stu-id="8cae9-113">Notice the default CALCULATE command in the **Calculation Expressions** pane and in the **Script Organizer** pane.</span></span> <span data-ttu-id="8cae9-114">此命令指定多维数据集中的度量值应该根据其 AggregateFunction 属性所指定的值进行聚合。</span><span class="sxs-lookup"><span data-stu-id="8cae9-114">This command specifies that the measures in the cube should be aggregated according to the value that is specified by their AggregateFunction properties.</span></span> <span data-ttu-id="8cae9-115">度量值通常会求和，但也可能计数或按其他某种方式进行聚合。</span><span class="sxs-lookup"><span data-stu-id="8cae9-115">Measure values are generally summed, but may also be counted or aggregated in some other manner.</span></span>  
  
     <span data-ttu-id="8cae9-116">下图显示多维数据集设计器的“计算”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="8cae9-116">The following image shows the **Calculations** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="8cae9-117">![多维数据集设计器的“计算”选项卡](../../2014/tutorials/media/l6-calculatedmembers-1.gif "多维数据集设计器的“计算”选项卡")</span><span class="sxs-lookup"><span data-stu-id="8cae9-117">![Calculations tab of Cube Designer](../../2014/tutorials/media/l6-calculatedmembers-1.gif "Calculations tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="8cae9-118">在“计算”\*\*\*\* 选项卡的工具栏上，单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-118">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="8cae9-119">新窗体将出现在“计算表达式”\*\*\*\* 窗格中，可在该窗格内定义这个新计算成员的属性。</span><span class="sxs-lookup"><span data-stu-id="8cae9-119">A new form appears in the **Calculation Expressions** pane within which you define the properties of this new calculated member.</span></span> <span data-ttu-id="8cae9-120">新成员还将出现在“脚本组织程序”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-120">The new member also appears in the **Script Organizer** pane.</span></span>  
  
     <span data-ttu-id="8cae9-121">下图显示单击“新建计算成员”\*\*\*\* 时出现在“计算表达式”\*\*\*\* 窗格中的窗体。</span><span class="sxs-lookup"><span data-stu-id="8cae9-121">The following image shows the form that appears in the **Calculation Expressions** pane when you click **New Calculated Member**.</span></span>  
  
     <span data-ttu-id="8cae9-122">![“计算表达式”窗格窗体](../../2014/tutorials/media/l6-calculatedmembers-02.gif "“计算表达式”窗格窗体")</span><span class="sxs-lookup"><span data-stu-id="8cae9-122">![Calculation Expressions pane form](../../2014/tutorials/media/l6-calculatedmembers-02.gif "Calculation Expressions pane form")</span></span>  
  
3.  <span data-ttu-id="8cae9-123">在 "**名称**" 框中，将计算度量值的名称更改为 `[Total Sales Amount]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-123">In the **Name** box, change the name of the calculated measure to `[Total Sales Amount]`.</span></span>  
  
     <span data-ttu-id="8cae9-124">如果计算成员的名称包含空格，则该计算成员名称必须放在方括号中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-124">If the name of a calculated member contains a space, the calculated member name must be enclosed in square brackets.</span></span>  
  
     <span data-ttu-id="8cae9-125">请注意，在“父层次结构”\*\*\*\* 列表中，默认情况下，将在“Measures”\*\*\*\* 维度中创建新的计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-125">Notice in the **Parent hierarchy** list that, by default, a new calculated member is created in the **Measures** dimension.</span></span> <span data-ttu-id="8cae9-126">通常，度量值维度中的计算成员也称为计算度量值。</span><span class="sxs-lookup"><span data-stu-id="8cae9-126">A calculated member in the Measures dimension is also frequently called a calculated measure.</span></span>  
  
4.  <span data-ttu-id="8cae9-127">在“计算”\*\*\*\* 选项卡的“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡上，依次展开“Measures”\*\*\*\* 和“Internet Sales”\*\*\*\*，查看“Internet Sales”\*\*\*\* 度量值组的元数据。</span><span class="sxs-lookup"><span data-stu-id="8cae9-127">On the **Metadata** tab in the **Calculation Tools** pane of the **Calculations** tab, expand **Measures** and then expand **Internet Sales** to view the metadata for the **Internet Sales** measure group.</span></span>  
  
     <span data-ttu-id="8cae9-128">可以将元数据元素从“计算工具”\*\*\*\* 窗格拖到“表达式”\*\*\*\* 框中，然后添加运算符和其他元素，创建多维表达式 (MDX) 表达式。</span><span class="sxs-lookup"><span data-stu-id="8cae9-128">You can drag metadata elements from the **Calculation Tools** pane into the **Expression** box and then add operators and other elements to create Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="8cae9-129">或者，可以直接在“表达式”\*\*\*\* 框中键入 MDX 表达式。</span><span class="sxs-lookup"><span data-stu-id="8cae9-129">Alternatively, you can type the MDX expression directly into the **Expression** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8cae9-130">如果无法在“计算工具”\*\*\*\* 窗格中查看任何元数据，请在工具栏上单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-130">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="8cae9-131">如果该操作失败，则可能必须处理多维数据集，或启动 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="8cae9-131">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="8cae9-132">将“Internet Sales-Sales Amount”\*\*\*\* 从“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡拖到“计算表达式”\*\*\*\* 窗格中的“表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-132">Drag **Internet Sales-Sales Amount** from the **Metadata** tab in the **Calculation Tools** pane into the **Expression** box in the **Calculation Expressions** pane.</span></span>  
  
6.  <span data-ttu-id="8cae9-133">在“表达式”\*\*\*\* 框中，在 **[Measures].[Internet Sales-Sales Amount]** 后键入加号 (`+`)。</span><span class="sxs-lookup"><span data-stu-id="8cae9-133">In the **Expression** box, type a plus sign (`+`) after **[Measures].[Internet Sales-Sales Amount]**.</span></span>  
  
7.  <span data-ttu-id="8cae9-134">在“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡上，展开“Reseller Sales”\*\*\*\*，然后将“Reseller Sales-Sales Amount”\*\*\*\* 拖到“计算表达式”\*\*\*\* 窗格的“表达式”\*\*\*\* 框中的加号 (+) 后面。</span><span class="sxs-lookup"><span data-stu-id="8cae9-134">On the **Metadata** tab in the **Calculation Tools** pane, expand **Reseller Sales**, and then drag **Reseller Sales-Sales Amount** into the **Expression** box in the **Calculation Expressions** pane after the plus sign (+).</span></span>  
  
8.  <span data-ttu-id="8cae9-135">在 "**格式字符串**" 列表中，选择 **"Currency"。**</span><span class="sxs-lookup"><span data-stu-id="8cae9-135">In the **Format string** list, select **"Currency".**</span></span>  
  
9. <span data-ttu-id="8cae9-136">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-136">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8cae9-137">在“非空行为”\*\*\*\* 列表中指定的度量值将用于解析 MDX 中的 NON EMPTY 查询。</span><span class="sxs-lookup"><span data-stu-id="8cae9-137">The measures you specify in the **Non-empty behavior** list are used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="8cae9-138">在“非空行为”\*\*\*\* 列表中指定一个或多个度量值时，如果所有指定的度量值为空，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将把计算成员视为空。</span><span class="sxs-lookup"><span data-stu-id="8cae9-138">When you specify one or more measures in the **Non-empty behavior** list, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] treats the calculated member as empty if all the specified measures are empty.</span></span> <span data-ttu-id="8cae9-139">如果“非空行为”\*\*\*\* 属性为空白，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 必须对计算成员本身进行计算才能确定成员是否为空。</span><span class="sxs-lookup"><span data-stu-id="8cae9-139">If the **Non-empty behavior** property is blank, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] must evaluate the calculated member itself to determine whether the member is empty.</span></span>  
  
     <span data-ttu-id="8cae9-140">下图显示使用前面步骤中所指定的设置填充的“计算表达式”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="8cae9-140">The following image shows the **Calculation Expressions** pane populated with the settings that you specified in the previous steps.</span></span>  
  
     <span data-ttu-id="8cae9-141">![“填充的计算表达式”窗格](../../2014/tutorials/media/l6-calculatedmembers-03.gif "“填充的计算表达式”窗格")</span><span class="sxs-lookup"><span data-stu-id="8cae9-141">![Populated Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-03.gif "Populated Calculation Expressions pane")</span></span>  
  
10. <span data-ttu-id="8cae9-142">在“计算”\*\*\*\* 选项卡的工具栏上，单击“脚本视图”\*\*\*\*，然后在“计算表达式”\*\*\*\* 窗格中检查计算脚本。</span><span class="sxs-lookup"><span data-stu-id="8cae9-142">On the toolbar of the **Calculations** tab, click **Script View**, and then review the calculation script in the **Calculation Expressions** pane.</span></span>  
  
     <span data-ttu-id="8cae9-143">注意，新的计算将添加到初始 CALCULATE 表达式中；将以分号分隔每个单独的计算。</span><span class="sxs-lookup"><span data-stu-id="8cae9-143">Notice that the new calculation is added to the initial CALCULATE expression; each individual calculation is separated by a semicolon.</span></span> <span data-ttu-id="8cae9-144">另外注意，在计算脚本的开始位置将出现注释。</span><span class="sxs-lookup"><span data-stu-id="8cae9-144">Notice also that a comment appears at the beginning of the calculation script.</span></span> <span data-ttu-id="8cae9-145">在计算组的计算脚本中添加注释是好的做法，这样可以帮助您和其他开发人员理解复杂的计算脚本。</span><span class="sxs-lookup"><span data-stu-id="8cae9-145">Adding comments within the calculation script for groups of calculations is a good practice, to help you and other developers understand complex calculation scripts.</span></span>  
  
11. <span data-ttu-id="8cae9-146">在计算脚本中的 **Calculate;** 命令之后和新添加的计算脚本之前添加一行，然后在脚本中独立的一行上添加以下文本：</span><span class="sxs-lookup"><span data-stu-id="8cae9-146">Add a new line in the calculation script after the **Calculate;** command and before the newly added calculation script, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to aggregate Internet Sales and Reseller Sales measures */  
    ```  
  
     <span data-ttu-id="8cae9-147">下图显示此时在教程中应该出现在“计算表达式”\*\*\*\* 窗格中的计算脚本。</span><span class="sxs-lookup"><span data-stu-id="8cae9-147">The following image shows the calculation scripts as they should appear in the **Calculation Expressions** pane at this point in the tutorial.</span></span>  
  
     <span data-ttu-id="8cae9-148">![“计算表达式”窗格中的脚本](../../2014/tutorials/media/l6-calculatedmembers-04.gif "“计算表达式”窗格中的脚本")</span><span class="sxs-lookup"><span data-stu-id="8cae9-148">![Scripts in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-04.gif "Scripts in Calculation Expressions pane")</span></span>  
  
12. <span data-ttu-id="8cae9-149">在 "**计算**" 选项卡的工具栏上，单击 "**窗体视图**"，确认 `[Total Sales Amount]` 已在 "**脚本组织**程序" 窗格中选择，然后单击 "**新建计算成员**"。</span><span class="sxs-lookup"><span data-stu-id="8cae9-149">On the toolbar of the **Calculations** tab, click **Form View**, verify that `[Total Sales Amount]` is selected in the **Script Organizer** pane, and then click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="8cae9-150">将这个新计算成员的名称更改为 `[Total Product Cost]` ，然后在 "**表达式**" 框中创建以下表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-150">Change the name of this new calculated member to `[Total Product Cost]`, and then create the following expression in the **Expression** box:</span></span>  
  
    ```  
    [Measures].[Internet Sales-Total Product Cost] + [Measures].[Reseller Sales-Total Product Cost]  
    ```  
  
14. <span data-ttu-id="8cae9-151">在“格式字符串”\*\*\*\* 列表中，选择“Currency”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-151">In the **Format string** list, select **"Currency"**.</span></span>  
  
15. <span data-ttu-id="8cae9-152">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Total Product Cost”\*\*\*\* 和“Reseller Sales-Total Product Cost”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-152">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Total Product Cost** and **Reseller Sales-Total Product Cost**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8cae9-153">现已定义两个计算成员，它们都在“脚本组织程序”\*\*\*\* 窗格中显示。</span><span class="sxs-lookup"><span data-stu-id="8cae9-153">You have now defined two calculated members, both of which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="8cae9-154">这些计算成员可以由随后在计算脚本中定义的其他计算来使用。</span><span class="sxs-lookup"><span data-stu-id="8cae9-154">These calculated members can be used by other calculations that you define later in the calculation script.</span></span> <span data-ttu-id="8cae9-155">通过在“脚本组织程序”\*\*\*\* 窗格中选择计算成员，可查看任何计算成员的定义；计算成员的定义将出现在窗体视图内的“计算表达式”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-155">You can view the definition of any calculated member by selecting the calculated member in the **Script Organizer** pane; the definition of the calculated member will appear in the **Calculation Expressions** pane in the Form view.</span></span> <span data-ttu-id="8cae9-156">在部署新定义的计算成员前，这些对象不会出现在“计算工具”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-156">Newly defined calculated members will not appear in the **Calculation Tools** pane until these objects have been deployed.</span></span> <span data-ttu-id="8cae9-157">计算不需要处理。</span><span class="sxs-lookup"><span data-stu-id="8cae9-157">Calculations do not require processing.</span></span>  
  
## <a name="defining-gross-profit-margin-calculations"></a><span data-ttu-id="8cae9-158">定义毛利润率计算</span><span class="sxs-lookup"><span data-stu-id="8cae9-158">Defining Gross Profit Margin Calculations</span></span>  
  
1.  <span data-ttu-id="8cae9-159">验证 `[Total Product Cost]` 是否已在 "**脚本组织**程序" 窗格中选择，然后在 "**计算**" 选项卡的工具栏上单击 "**新建计算成员**"。</span><span class="sxs-lookup"><span data-stu-id="8cae9-159">Verify that `[Total Product Cost]` is selected in the **Script Organizer** pane, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
2.  <span data-ttu-id="8cae9-160">在 "**名称**" 框中，将此新计算度量值的名称更改为 `[Internet GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-160">In the **Name** box, change the name of this new calculated measure to `[Internet GPM]`.</span></span>  
  
3.  <span data-ttu-id="8cae9-161">在“表达式”\*\*\*\* 框中，创建以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-161">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Internet Sales-Sales Amount] -   
    [Measures].[Internet Sales-Total Product Cost]) /  
    [Measures].[Internet Sales-Sales Amount]  
    ```  
  
4.  <span data-ttu-id="8cae9-162">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-162">In the **Format string** list, select **"Percent"**.</span></span>  
  
5.  <span data-ttu-id="8cae9-163">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-163">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8cae9-164">在“计算”\*\*\*\* 选项卡的工具栏上，单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-164">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
7.  <span data-ttu-id="8cae9-165">在 "**名称**" 框中，将此新计算度量值的名称更改为 `[Reseller GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-165">In the **Name** box, change the name of this new calculated measure to `[Reseller GPM]`.</span></span>  
  
8.  <span data-ttu-id="8cae9-166">在“表达式”\*\*\*\* 框中，创建以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-166">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Reseller Sales-Sales Amount] -   
    [Measures].[Reseller Sales-Total Product Cost]) /  
    [Measures].[Reseller Sales-Sales Amount]  
    ```  
  
9. <span data-ttu-id="8cae9-167">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-167">In the **Format string** list, select **"Percent"**.</span></span>  
  
10. <span data-ttu-id="8cae9-168">在“非空行为”\*\*\*\* 列表中，选中“Reseller Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-168">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="8cae9-169">在“计算”\*\*\*\* 选项卡的工具栏上，单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-169">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
12. <span data-ttu-id="8cae9-170">在 "**名称**" 框中，将此计算度量值的名称更改为 `[Total GPM]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-170">In the **Name** box, change the name of this calculated measure to `[Total GPM]`.</span></span>  
  
13. <span data-ttu-id="8cae9-171">在“表达式”\*\*\*\* 框中，创建以下 MDX 表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-171">In the **Expression** box, create the following MDX expression:</span></span>  
  
    ```  
    ([Measures].[Total Sales Amount] -   
    [Measures].[Total Product Cost]) /  
    [Measures].[Total Sales Amount]  
    ```  
  
     <span data-ttu-id="8cae9-172">注意，此计算成员引用了其他计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-172">Notice that this calculated member is referencing other calculated members.</span></span> <span data-ttu-id="8cae9-173">由于此计算成员将在它所引用的计算成员之后进行计算，所以这是有效的计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-173">Because this calculated member will be calculated after the calculated members that it references, this is a valid calculated member.</span></span>  
  
14. <span data-ttu-id="8cae9-174">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-174">In the **Format string** list, select **"Percent"**.</span></span>  
  
15. <span data-ttu-id="8cae9-175">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-175">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="8cae9-176">在“计算”\*\*\*\* 选项卡的工具栏上，单击“脚本视图”\*\*\*\*，然后检查刚才添加到计算脚本中的三个计算。</span><span class="sxs-lookup"><span data-stu-id="8cae9-176">On the toolbar of the **Calculations** tab, click **Script View** and review the three calculations you just added to the calculation script.</span></span>  
  
17. <span data-ttu-id="8cae9-177">在计算脚本中紧靠计算之前添加新行 `[Internet GPM]` ，然后在脚本中将以下文本添加到脚本中：</span><span class="sxs-lookup"><span data-stu-id="8cae9-177">Add a new line in the calculation script immediately before the `[Internet GPM]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate gross profit margin */  
    ```  
  
     <span data-ttu-id="8cae9-178">下图显示有三个新计算的“表达式”\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="8cae9-178">The following image shows the **Expressions** pane with the three new calculations.</span></span>  
  
     <span data-ttu-id="8cae9-179">![“计算表达式”窗格中的新计算](../../2014/tutorials/media/l6-calculatedmembers-05.gif "“计算表达式”窗格中的新计算")</span><span class="sxs-lookup"><span data-stu-id="8cae9-179">![New calculations in Calculation Expressions pane](../../2014/tutorials/media/l6-calculatedmembers-05.gif "New calculations in Calculation Expressions pane")</span></span>  
  
## <a name="defining-the-percent-of-total-calculations"></a><span data-ttu-id="8cae9-180">定义总计计算的百分比</span><span class="sxs-lookup"><span data-stu-id="8cae9-180">Defining the Percent of Total Calculations</span></span>  
  
1.  <span data-ttu-id="8cae9-181">在“计算”\*\*\*\* 选项卡的工具栏上，单击“窗体视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-181">On the toolbar of the **Calculations** tab, click **Form View**.</span></span>  
  
2.  <span data-ttu-id="8cae9-182">在 "**脚本组织**程序" 窗格中，选择 `[Total GPM]` ，然后在 "**计算**" 选项卡的工具栏上单击 "**新建计算成员**"。</span><span class="sxs-lookup"><span data-stu-id="8cae9-182">In the **Script Organizer** pane, select `[Total GPM]`, and then click **New Calculated Member** on the toolbar of the **Calculations** tab.</span></span>  
  
     <span data-ttu-id="8cae9-183">在单击“新建计算成员”\*\*\*\* 之前单击“脚本组织程序”\*\*\*\* 窗格中的最后一个计算成员，可以保证在脚本末尾输入新计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-183">Clicking the final calculated member in the **Script Organizer** pane before you click **New Calculated Member** guarantees that the new calculated member will be entered at the end of the script.</span></span> <span data-ttu-id="8cae9-184">脚本按它们出现在“脚本组织程序”\*\*\*\* 窗格中的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="8cae9-184">Scripts execute in the order that they appear in the **Script Organizer** pane.</span></span>  
  
3.  <span data-ttu-id="8cae9-185">将这个新计算成员的名称更改为 `[Internet Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-185">Change the name of this new calculated member to `[Internet Sales Ratio to All Products]`.</span></span>  
  
4.  <span data-ttu-id="8cae9-186">在“表达式”\*\*\*\* 框中键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-186">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Internet Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Internet Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Internet Sales-Sales Amount] )  
        End  
    ```  
  
     <span data-ttu-id="8cae9-187">此 MDX 表达式将计算每个产品在总计 Internet 销售额中所占的比例。</span><span class="sxs-lookup"><span data-stu-id="8cae9-187">This MDX expression calculates the contribution to total Internet sales of each product.</span></span> <span data-ttu-id="8cae9-188">Case 语句与 IS EMPTY 函数一起确保当产品没有销售额时不会发生被零除错误。</span><span class="sxs-lookup"><span data-stu-id="8cae9-188">The Case statement together with the IS EMPTY function ensures that a divide by zero error does not occur when a product has no sales.</span></span>  
  
5.  <span data-ttu-id="8cae9-189">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-189">In the **Format string** list, select **"Percent"**.</span></span>  
  
6.  <span data-ttu-id="8cae9-190">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-190">In the **Non-empty behavior** list, select the check box for **Internet Sales-Sales Amount**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8cae9-191">在“计算”\*\*\*\* 选项卡的工具栏上，单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-191">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
8.  <span data-ttu-id="8cae9-192">将此计算成员的名称更改为 `[Reseller Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-192">Change the name of this calculated member to `[Reseller Sales Ratio to All Products]`.</span></span>  
  
9. <span data-ttu-id="8cae9-193">在“表达式”\*\*\*\* 框中键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-193">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Reseller Sales-Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Reseller Sales-Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Reseller Sales-Sales Amount] )  
        End  
    ```  
  
10. <span data-ttu-id="8cae9-194">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-194">In the **Format string** list, select **"Percent"**.</span></span>  
  
11. <span data-ttu-id="8cae9-195">在“非空行为”\*\*\*\* 列表中，选中“Reseller Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-195">In the **Non-empty behavior** list, select the check box for **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="8cae9-196">在“计算”\*\*\*\* 选项卡的工具栏上，单击“新建计算成员”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-196">On the toolbar of the **Calculations** tab, click **New Calculated Member**.</span></span>  
  
13. <span data-ttu-id="8cae9-197">将此计算成员的名称更改为 `[Total Sales Ratio to All Products]` 。</span><span class="sxs-lookup"><span data-stu-id="8cae9-197">Change the name of this calculated member to `[Total Sales Ratio to All Products]`.</span></span>  
  
14. <span data-ttu-id="8cae9-198">在“表达式”\*\*\*\* 框中键入以下表达式：</span><span class="sxs-lookup"><span data-stu-id="8cae9-198">Type the following expression in the **Expression** box:</span></span>  
  
    ```  
    Case  
        When IsEmpty( [Measures].[Total Sales Amount] )   
        Then 0  
        Else ( [Product].[Product Categories].CurrentMember,  
               [Measures].[Total Sales Amount]) /  
             ( [Product].[Product Categories].[(All)].[All],   
               [Measures].[Total Sales Amount] )  
        End  
    ```  
  
15. <span data-ttu-id="8cae9-199">在“格式字符串”\*\*\*\* 列表中，选择“Percent”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-199">In the **Format string** list, select **"Percent"**.</span></span>  
  
16. <span data-ttu-id="8cae9-200">在“非空行为”\*\*\*\* 列表中，选中“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 的复选框，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-200">In the **Non-empty behavior** list, select the check boxes for **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="8cae9-201">在“计算”\*\*\*\* 选项卡的工具栏上，单击“脚本视图”\*\*\*\*，然后检查刚才添加到计算脚本中的三个计算。</span><span class="sxs-lookup"><span data-stu-id="8cae9-201">On the toolbar of the **Calculations** tab, click **Script View**, and then review the three calculations that you just added to the calculation script.</span></span>  
  
18. <span data-ttu-id="8cae9-202">在计算脚本中紧靠计算之前添加新行 `[Internet Sales Ratio to All Products]` ，然后在脚本中将以下文本添加到脚本中：</span><span class="sxs-lookup"><span data-stu-id="8cae9-202">Add a new line in the calculation script immediately before the `[Internet Sales Ratio to All Products]` calculation, and then add the following text to the script on its own line:</span></span>  
  
    ```  
    /* Calculations to calculate percentage of product to total product sales */  
    ```  
  
     <span data-ttu-id="8cae9-203">现在总共定义了八个计算成员，位于“窗体”视图中时，这些成员将在“脚本组织程序”\*\*\*\* 窗格中显示。</span><span class="sxs-lookup"><span data-stu-id="8cae9-203">You have now defined a total of eight calculated members, which are visible in the **Script Organizer** pane when you are in Form view.</span></span>  
  
## <a name="browsing-the-new-calculated-members"></a><span data-ttu-id="8cae9-204">浏览新计算成员</span><span class="sxs-lookup"><span data-stu-id="8cae9-204">Browsing the New Calculated Members</span></span>  
  
1.  <span data-ttu-id="8cae9-205">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-205">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="8cae9-206">成功完成部署后，请切换到“浏览器”\*\*\*\* 选项卡，然后单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-206">When deployment has successfully completed, switch to the **Browser** tab, click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="8cae9-207">单击 Excel 图标，然后单击“启用”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8cae9-207">Click the Excel icon, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="8cae9-208">在“数据透视表字段列表”\*\*\*\* 窗格中，展开“值”\*\*\*\* 文件夹，查看“Measures”维度中的新计算成员。</span><span class="sxs-lookup"><span data-stu-id="8cae9-208">In the **PivotTable Field List** pane, expand **Values** folder to view the new calculated members in the Measures dimension.</span></span>  
  
5.  <span data-ttu-id="8cae9-209">将“Total Sales Amount”\*\*\*\* 拖到“值”区域中，然后检查结果。</span><span class="sxs-lookup"><span data-stu-id="8cae9-209">Drag the **Total Sales Amount** to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="8cae9-210">将“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 度量值从“Internet Sales”\*\*\*\* 和“Reseller Sales”\*\*\*\* 度量值组拖到“值”区域中。</span><span class="sxs-lookup"><span data-stu-id="8cae9-210">Drag **Internet Sales-Sales Amount** and **Reseller Sales-Sales Amount** measures from the **Internet Sales** and **Reseller Sales** measure groups to the Values area.</span></span>  
  
     <span data-ttu-id="8cae9-211">请注意，“Total Sales Amount”\*\*\*\* 度量值是“Internet Sales-Sales Amount”\*\*\*\* 度量值与“Reseller Sales-Sales Amount”\*\*\*\* 度量值之和。</span><span class="sxs-lookup"><span data-stu-id="8cae9-211">Notice that the **Total Sales Amount** measure is the sum of the **Internet Sales-Sales Amount** measure and the **Reseller Sales-Sales Amount** measure.</span></span>  
  
6.  <span data-ttu-id="8cae9-212">将“Product Categories”\*\*\*\* 用户定义层次结构添加到“报表筛选器”\*\*\*\* 区域的筛选区域中，然后按“Mountain Bikes”\*\*\*\* 对数据进行筛选。</span><span class="sxs-lookup"><span data-stu-id="8cae9-212">Add the **Product Categories** user-defined hierarchy to the filter area of the **Report Filter** area, and then filter the data by **Mountain Bikes**.</span></span>  
  
     <span data-ttu-id="8cae9-213">请注意，“Total Sales Amount”\*\*\*\* 度量值是基于“Mountain Bikes”\*\*\*\* 的“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 度量值，针对“Mountain Bikes”\*\*\*\* 类别的产品销售额进行计算的。</span><span class="sxs-lookup"><span data-stu-id="8cae9-213">Notice that the **Total Sales Amount** measure is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
7.  <span data-ttu-id="8cae9-214">将“Date.Calendar Date”\*\*\*\* 用户定义层次结构添加到行标签区域，然后检查结果。</span><span class="sxs-lookup"><span data-stu-id="8cae9-214">Add the **Date.Calendar Date** user-defined hierarchy to the Row labels area, and then review the results.</span></span>  
  
     <span data-ttu-id="8cae9-215">请注意，每个日历年的“Total Sales Amount”\*\*\*\* 度量值是基于“Mountain Bikes”\*\*\*\* 的“Internet Sales-Sales Amount”\*\*\*\* 和“Reseller Sales-Sales Amount”\*\*\*\* 度量值，针对“Mountain Bikes”\*\*\*\* 类别的产品销售额进行计算的。</span><span class="sxs-lookup"><span data-stu-id="8cae9-215">Notice that the **Total Sales Amount** measure for each calendar year is calculated for the **Mountain Bikes** category of product sales based on the **Internet Sales-Sales Amount** and the **Reseller Sales-Sales Amount** measures for **Mountain Bikes**.</span></span>  
  
8.  <span data-ttu-id="8cae9-216">将“Total GPM”\*\*\*\*、“Internet GPM”\*\*\*\* 和“Reseller GPM”\*\*\*\* 度量值添加到“值”区域，然后检查结果。</span><span class="sxs-lookup"><span data-stu-id="8cae9-216">Add the **Total GPM**, **Internet GPM**, and **Reseller GPM** measures to the Values area, and then review the results.</span></span>  
  
     <span data-ttu-id="8cae9-217">请注意，分销商销售的毛利润率要比 Internet 销售低很多，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="8cae9-217">Notice that the gross profit margin for reseller sales is significantly lower than for sales over the Internet, as shown in the following image.</span></span>  
  
     <span data-ttu-id="8cae9-218">![显示分销商销售的数据窗格](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "显示分销商销售的数据窗格")</span><span class="sxs-lookup"><span data-stu-id="8cae9-218">![Data pane showing reseller sales](../../2014/tutorials/media/l6-calculatedmembers-7b.gif "Data pane showing reseller sales")</span></span>  
  
9. <span data-ttu-id="8cae9-219">将“Total Sales Ratio to All Products”\*\*\*\*、“Internet Sales Ratio to All Products”\*\*\*\* 和“Reseller Sales Ratio to All Products”\*\*\*\* 度量值添加到“值”区域。</span><span class="sxs-lookup"><span data-stu-id="8cae9-219">Add the **Total Sales Ratio to All Products**, **Internet Sales Ratio to All Products**, and **Reseller Sales Ratio to All Products** measures to the Values area.</span></span>  
  
     <span data-ttu-id="8cae9-220">注意，Internet 销售的山地车销售额在所有产品中所占的比率随时间推移而增长，但在分销商那里却在随时间推移而减少。</span><span class="sxs-lookup"><span data-stu-id="8cae9-220">Notice that the ratio of the sales of mountain bikes to all products has increased over time for Internet sales, but is decreasing over time for reseller sales.</span></span> <span data-ttu-id="8cae9-221">另外注意，通过分销商销售的山地车销售额在所有产品中所占的比率低于通过 Internet 销售完成的该比率。</span><span class="sxs-lookup"><span data-stu-id="8cae9-221">Notice also that the ratio of the sale of mountain bikes to all products is lower from sales through resellers than it is for sales over the Internet.</span></span>  
  
10. <span data-ttu-id="8cae9-222">将筛选器从“Mountain Bikes”\*\*\*\* 更改为“Bikes”\*\*\*\*，然后检查结果。</span><span class="sxs-lookup"><span data-stu-id="8cae9-222">Change the filter from **Mountain Bikes** to **Bikes**, and review the results.</span></span>  
  
     <span data-ttu-id="8cae9-223">注意，通过分销商销售的所有自行车的毛利润率都是负数，这是因为观光自行车和道路自行车都在亏损销售。</span><span class="sxs-lookup"><span data-stu-id="8cae9-223">Notice that the gross profit margin for all bikes sold through resellers is negative, because touring bikes and road bikes are being sold at a loss.</span></span>  
  
11. <span data-ttu-id="8cae9-224">将筛选器更改为“Accessories”\*\*\*\*，然后检查结果。</span><span class="sxs-lookup"><span data-stu-id="8cae9-224">Change the filter to **Accessories**, and then review the results.</span></span>  
  
     <span data-ttu-id="8cae9-225">注意，附件的销售正在随时间而增长，但这些销售只构成总销售额的一小部分。</span><span class="sxs-lookup"><span data-stu-id="8cae9-225">Notice that the sale of accessories is increasing over time, but that these sales make up only a small fraction of total sales.</span></span> <span data-ttu-id="8cae9-226">还要注意的是，附件销售的毛利润率比自行车还高。</span><span class="sxs-lookup"><span data-stu-id="8cae9-226">Notice also that the gross profit margin for sales of accessories is higher than for bikes.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8cae9-227">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="8cae9-227">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8cae9-228">定义命名集</span><span class="sxs-lookup"><span data-stu-id="8cae9-228">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
  
## <a name="see-also"></a><span data-ttu-id="8cae9-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8cae9-229">See Also</span></span>  
 <span data-ttu-id="8cae9-230">[考虑](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="8cae9-230">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="8cae9-231">[多维模型中的计算](multidimensional-models/calculations-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="8cae9-231">[Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="8cae9-232">创建计算成员</span><span class="sxs-lookup"><span data-stu-id="8cae9-232">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
