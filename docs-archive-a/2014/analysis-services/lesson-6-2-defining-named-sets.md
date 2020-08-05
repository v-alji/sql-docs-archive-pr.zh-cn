---
title: 定义命名集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 47254fd3-525f-4c35-b93d-316607652517
author: minewiskan
ms.author: owend
ms.openlocfilehash: e02f4624dc0ec25ee0c3d8950c83550ca3d9ed57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580980"
---
# <a name="defining-named-sets"></a><span data-ttu-id="2291e-102">定义命名集</span><span class="sxs-lookup"><span data-stu-id="2291e-102">Defining Named Sets</span></span>
  <span data-ttu-id="2291e-103">命名集是一个返回一组维度成员的多维表达式 (MDX)。</span><span class="sxs-lookup"><span data-stu-id="2291e-103">A named set is a Multidimensional Expressions (MDX) expression that returns a set of dimension members.</span></span> <span data-ttu-id="2291e-104">可以定义命名集，并将它们另存为多维数据集定义的一部分；还可以在客户端应用程序中创建命名集。</span><span class="sxs-lookup"><span data-stu-id="2291e-104">You can define named sets and save them as part of the cube definition; you can also create named sets in client applications.</span></span> <span data-ttu-id="2291e-105">通过合并多维数据集数据、算术运算符、数字和函数，可以创建命名集。</span><span class="sxs-lookup"><span data-stu-id="2291e-105">You create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="2291e-106">命名集可以由用户在客户端应用程序的 MDX 查询中使用，还可以用来定义子多维数据集中的集合。</span><span class="sxs-lookup"><span data-stu-id="2291e-106">Named sets can be used by users in MDX queries in client applications and can also be used to define sets in subcubes.</span></span> <span data-ttu-id="2291e-107">子多维数据集是交叉联接集的集合，它将多维数据集空间限制为随后语句的定义的子空间。</span><span class="sxs-lookup"><span data-stu-id="2291e-107">A subcube is a collection of crossjoined sets that restricts the cube space to the defined subspace for subsequent statements.</span></span> <span data-ttu-id="2291e-108">定义受限的多维数据集空间是 MDX 脚本的一个基本概念。</span><span class="sxs-lookup"><span data-stu-id="2291e-108">Defining a restricted cube space is a fundamental concept to MDX scripting.</span></span>

 <span data-ttu-id="2291e-109">命名集简化了 MDX 查询，并为复杂、常用的集表达式提供了有用的别名。</span><span class="sxs-lookup"><span data-stu-id="2291e-109">Named sets simplify MDX queries and provide useful aliases for complex, typically used, set expressions.</span></span> <span data-ttu-id="2291e-110">例如，可以定义名为“大型分销商”的命名集，用来包含有最多雇员的“分销商”维度的成员集合。</span><span class="sxs-lookup"><span data-stu-id="2291e-110">For example, you can define a named set called Large Resellers that contains the set of members in the Reseller dimension that have the most employees.</span></span> <span data-ttu-id="2291e-111">然后，最终用户可以在查询中使用“大型分销商”命名集，您也可以使用该命名集来定义子多维数据集中的集合。</span><span class="sxs-lookup"><span data-stu-id="2291e-111">End users could then use the Large Resellers named set in queries, or you could use the named set to define a set in a subcube.</span></span> <span data-ttu-id="2291e-112">命名集定义存储于多维数据集中，但它们的值只存在于内存中。</span><span class="sxs-lookup"><span data-stu-id="2291e-112">Named set definitions are stored in cubes, but their values exist only in memory.</span></span> <span data-ttu-id="2291e-113">若要创建命名集，请使用多维数据集设计器的 **“计算”** 选项卡上的 **“新建命名集”** 命令。</span><span class="sxs-lookup"><span data-stu-id="2291e-113">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="2291e-114">有关详细信息，请参阅 [计算](multidimensional-models-olap-logical-cube-objects/calculations.md)、 [创建命名集](multidimensional-models/create-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="2291e-114">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), [Create Named Sets](multidimensional-models/create-named-sets.md).</span></span>

 <span data-ttu-id="2291e-115">在此主题的任务中，将定义两个命名集：“核心产品”命名集和“大型分销商”命名集。</span><span class="sxs-lookup"><span data-stu-id="2291e-115">In the tasks in this topic, you will define two named sets: a Core Products named set and a Large Resellers named set.</span></span>

## <a name="defining-a-core-products-named-set"></a><span data-ttu-id="2291e-116">定义“核心产品”命名集</span><span class="sxs-lookup"><span data-stu-id="2291e-116">Defining a Core Products Named Set</span></span>

1.  <span data-ttu-id="2291e-117">切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器的“计算”\*\*\*\* 选项卡，再单击工具栏上的“窗体视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-117">Switch to the **Calculations** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Form View** on the toolbar.</span></span>

2.  <span data-ttu-id="2291e-118">单击“脚本组织程序”\*\*\*\* 窗格中的“[所有产品的总销售额比率]”\*\*\*\*，然后在“计算”\*\*\*\* 选项卡的工具栏上单击“新建命名集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-118">Click **[Total Sales Ratio to All Products]** in the **Script Organizer** pane, and then click **New Named Set** on the toolbar of the **Calculations** tab.</span></span>

     <span data-ttu-id="2291e-119">在“计算”\*\*\*\* 选项卡上定义新计算时，请记住，计算的解决是按它们出现在“脚本组织程序”\*\*\*\* 窗格中的顺序来进行的。</span><span class="sxs-lookup"><span data-stu-id="2291e-119">When you define a new calculation on the **Calculations** tab, remember that calculations are resolved in the order in which they appear in the **Script Organizer** pane.</span></span> <span data-ttu-id="2291e-120">在创建新计算时该窗格中的焦点确定了计算的执行顺序；新的计算将定义于紧靠有焦点的计算之后。</span><span class="sxs-lookup"><span data-stu-id="2291e-120">Your focus within that pane when you create a new calculation determines the order of the execution of the calculation; a new calculation is defined immediately after the calculation on which you are focused.</span></span>

3.  <span data-ttu-id="2291e-121">在 "**名称**" 框中，将新命名集的名称更改为 `[Core Products]` 。</span><span class="sxs-lookup"><span data-stu-id="2291e-121">In the **Name** box, change the name of the new named set to `[Core Products]`.</span></span>

     <span data-ttu-id="2291e-122">在“脚本组织程序”\*\*\*\* 窗格中，注意用于将命名集与脚本命令或计算成员区分开来的唯一图标。</span><span class="sxs-lookup"><span data-stu-id="2291e-122">In the **Script Organizer** pane, notice the unique icon that differentiates a named set from a script command or a calculated member.</span></span>

4.  <span data-ttu-id="2291e-123">在 "**计算工具**" 窗格的 "**元数据**" 选项卡上，依次展开 "**产品**"、"**类别**" `Members` 和 "**所有产品**"。</span><span class="sxs-lookup"><span data-stu-id="2291e-123">On the **Metadata** tab in the **Calculation Tools** pane, expand **Product**, expand **Category**, expand `Members`, and then expand **All Products**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2291e-124">如果无法在“计算工具”\*\*\*\* 窗格中查看任何元数据，请在工具栏上单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-124">If you cannot view any metadata in the **Calculation Tools** pane, click **Reconnect** on the toolbar.</span></span> <span data-ttu-id="2291e-125">如果该操作失败，则可能必须处理多维数据集，或启动 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="2291e-125">If this does not work, you may have to process the cube or start the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

5.  <span data-ttu-id="2291e-126">将“自行车”\*\*\*\* 拖到“表达式”\*\*\*\* 框中。</span><span class="sxs-lookup"><span data-stu-id="2291e-126">Drag **Bikes** into the **Expression** box.</span></span>

     <span data-ttu-id="2291e-127">现在，您已经创建一组表达式，它将返回“产品”维度内的“自行车”类别中的成员集合。</span><span class="sxs-lookup"><span data-stu-id="2291e-127">You now have created a set expression that will return the set of members that are in the Bike category in the Product dimension.</span></span>

## <a name="defining-a-large-resellers-named-set"></a><span data-ttu-id="2291e-128">定义“大型分销商”命名集</span><span class="sxs-lookup"><span data-stu-id="2291e-128">Defining a Large Resellers Named Set</span></span>

1.  <span data-ttu-id="2291e-129">右键单击 `[Core Products]` "**脚本组织**程序" 窗格，然后单击 "**新建命名集**"。</span><span class="sxs-lookup"><span data-stu-id="2291e-129">Right-click `[Core Products]` in the **Script Organizer** pane, and then click **New Named Set**.</span></span>

2.  <span data-ttu-id="2291e-130">在 "**名称**" 框中，将此命名集的名称更改为 `[Large Resellers]` 。</span><span class="sxs-lookup"><span data-stu-id="2291e-130">In the **Name** box, change the name of this named set to `[Large Resellers]`.</span></span>

3.  <span data-ttu-id="2291e-131">在 "**表达式**" 框中，键入 `Exists()` 。</span><span class="sxs-lookup"><span data-stu-id="2291e-131">In the **Expression** box, type `Exists()`.</span></span>

     <span data-ttu-id="2291e-132">使用 Exists 函数来从“分销商名称”属性层次结构返回成员集合，而“分销商名称”属性层次结构将与有最大雇员数的“雇员数”属性层次结构中的成员集合相交互。</span><span class="sxs-lookup"><span data-stu-id="2291e-132">You will use the Exists function to return the set of members from the Reseller Name attribute hierarchy that intersects with the set of members in the Number of Employees attribute hierarchy that has the largest number of employees.</span></span>

4.  <span data-ttu-id="2291e-133">在“计算工具”\*\*\*\* 窗格中的“元数据”\*\*\*\* 选项卡上，展开“分销商”\*\*\*\* 维度，再展开“分销商名称”\*\*\*\* 属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="2291e-133">On the **Metadata** tab in the **Calculation Tools** pane, expand the **Reseller** dimension, and then expand the **Reseller Name** attribute hierarchy.</span></span>

5.  <span data-ttu-id="2291e-134">将“分销商名称”\*\*\*\* 级别拖到 Exists 集表达式的括号中。</span><span class="sxs-lookup"><span data-stu-id="2291e-134">Drag the **Reseller Name** level into the parenthesis for the Exists set expression.</span></span>

     <span data-ttu-id="2291e-135">将使用 Members 函数来返回此集合的所有成员。</span><span class="sxs-lookup"><span data-stu-id="2291e-135">You will use the Members function to return all members of this set.</span></span> <span data-ttu-id="2291e-136">有关详细信息，请参阅 [Members (Set) (MDX)](/sql/mdx/members-set-mdx)。</span><span class="sxs-lookup"><span data-stu-id="2291e-136">For more information, see [Members &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/members-set-mdx).</span></span>

6.  <span data-ttu-id="2291e-137">在部分集表达式之后键入句号，再添加 Members 函数。</span><span class="sxs-lookup"><span data-stu-id="2291e-137">After the partial set expression, type a period, and then add the Members function.</span></span> <span data-ttu-id="2291e-138">表达式应该如下显示：</span><span class="sxs-lookup"><span data-stu-id="2291e-138">Your expression should look like the following:</span></span>

    ```
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)
    ```

     <span data-ttu-id="2291e-139">现在，您已定义了 Exists 集表达式的第一个集，接下来您可以添加第二组-"分销商" 维度的成员集，其中包含数量最多的雇员。</span><span class="sxs-lookup"><span data-stu-id="2291e-139">Now that you have defined the first set for the Exists set expression, you are ready to add the second set-the set of members of the Reseller dimension that contains the largest number of employees.</span></span>

7.  <span data-ttu-id="2291e-140">在 "**计算工具**" 窗格的 "**元数据**" 选项卡上，展开 "分销商" 维度中**的员工数**，展开 `Members` ，然后展开 "**所有分销商**"。</span><span class="sxs-lookup"><span data-stu-id="2291e-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the Reseller dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="2291e-141">注意，此属性层次结构的成员没有分组。</span><span class="sxs-lookup"><span data-stu-id="2291e-141">Notice that the members of this attribute hierarchy are not grouped.</span></span>

8.  <span data-ttu-id="2291e-142">打开“分销商”\*\*\*\* 维度设计器，然后在“属性”\*\*\*\* 窗格中单击“雇员数目”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-142">Open Dimension Designer for the **Reseller** dimension, and then click **Number of Employees** in the **Attributes** pane.</span></span>

9. <span data-ttu-id="2291e-143">在属性窗口中，将 `DiscretizationMethod` 属性更改为 "**自动**"，然后将 `DiscretizationBucketCount` 属性更改为 `5` 。</span><span class="sxs-lookup"><span data-stu-id="2291e-143">In the Properties window, change the `DiscretizationMethod` property to **Automatic**, and then change the `DiscretizationBucketCount` property to `5`.</span></span> <span data-ttu-id="2291e-144">有关详细信息，请参阅[对属性成员分组（离散化）](multidimensional-models/attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="2291e-144">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>

10. <span data-ttu-id="2291e-145">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-145">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

11. <span data-ttu-id="2291e-146">成功完成部署后，切换到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教程多维数据集的多维数据集设计器，然后在“计算”\*\*\*\* 选项卡的工具栏上单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-146">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Calculations** tab.</span></span>

12. <span data-ttu-id="2291e-147">在 "**计算工具**" 窗格的 "**元数据**" 选项卡上，展开 "**分销商**" 维度中**的员工数**，展开 `Members` ，然后展开 "**所有分销商**"。</span><span class="sxs-lookup"><span data-stu-id="2291e-147">On the **Metadata** tab in the **Calculation Tools** pane, expand **Number of Employees** in the **Reseller** dimension, expand `Members`, and then expand **All Resellers**.</span></span>

     <span data-ttu-id="2291e-148">请注意，此属性层次结构的成员现在包含在编号为 0 到 4 的五个组中。</span><span class="sxs-lookup"><span data-stu-id="2291e-148">Notice that the members of this attribute hierarchy are now contained in five groups, numbered 0 through 4.</span></span> <span data-ttu-id="2291e-149">若要查看组的编号，请将指针暂停在组上以查看 InfoTip。</span><span class="sxs-lookup"><span data-stu-id="2291e-149">To view the number of a group, pause the pointer over that group to view an InfoTip.</span></span> <span data-ttu-id="2291e-150">对于范围 `2 -17`，InfoTip 应包含 `[Reseller].[Number of Employees].&[0]`。</span><span class="sxs-lookup"><span data-stu-id="2291e-150">For the range `2 -17`, the InfoTip should contain `[Reseller].[Number of Employees].&[0]`.</span></span>

     <span data-ttu-id="2291e-151">此属性层次结构的成员被分组，因为 DiscretizationBucketCount 属性设置为 `5` ，并且 DiscretizationMethod 属性设置为 "**自动**"。</span><span class="sxs-lookup"><span data-stu-id="2291e-151">The members of this attribute hierarchy are grouped because the DiscretizationBucketCount property is set to `5` and the DiscretizationMethod property is set to **Automatic**.</span></span>

13. <span data-ttu-id="2291e-152">在“表达式”\*\*\*\* 框中，在 Exists 集表达式中的 Members 函数之后和右括号之前添加逗号，再将 **83 - 100** 从“元数据”\*\*\*\* 窗格拖放到逗号之后。</span><span class="sxs-lookup"><span data-stu-id="2291e-152">In the **Expression** box, add a comma in the Exists set expression after the Members function and before the closing parenthesis, and then drag **83 - 100** from the **Metadata** pane and position it after the comma.</span></span>

     <span data-ttu-id="2291e-153">现在，将“大型分销商”命名集放在轴上，便已经完成了将会返回与两个指定集合（所有分销商集合和有 83 到 100 名雇员的分销商集合）相交互的成员集合的 Exists 集表达式。</span><span class="sxs-lookup"><span data-stu-id="2291e-153">You have now completed the Exists set expression that will return the set of members that intersects with these two specified sets, the set of all resellers and the set of resellers who have 83 to 100 employees, when the Large Resellers named set is put on an axis.</span></span>

     <span data-ttu-id="2291e-154">下图显示了命名集的 "**计算表达式**" 窗格 `[Large Resellers]` 。</span><span class="sxs-lookup"><span data-stu-id="2291e-154">The following image shows the **Calculation Expressions** pane for the `[Large Resellers]` named set.</span></span>

     <span data-ttu-id="2291e-155">![[大型分销商] 的“计算表达式”窗格](../../2014/tutorials/media/l6-named-set-02.gif "[大型分销商] 的“计算表达式”窗格")</span><span class="sxs-lookup"><span data-stu-id="2291e-155">![Calculation Expressions pane for [Large Resellers]](../../2014/tutorials/media/l6-named-set-02.gif "Calculation Expressions pane for [Large Resellers]")</span></span>

14. <span data-ttu-id="2291e-156">在“计算”\*\*\*\* 选项卡的工具栏上，单击“脚本视图”\*\*\*\*，然后检查刚才添加到计算脚本中的两个命名集。</span><span class="sxs-lookup"><span data-stu-id="2291e-156">On the toolbar of the **Calculations** tab, click **Script View**, and then review the two named sets that you have just added to the calculation script.</span></span>

15. <span data-ttu-id="2291e-157">在计算脚本中紧靠第一个 CREATE SET 命令之前添加新行，然后在脚本中独立的行上添加以下文本：</span><span class="sxs-lookup"><span data-stu-id="2291e-157">Add a new line in the calculation script immediately before the first CREATE SET command, and then add the following text to the script on its own line:</span></span>

    ```
    /* named sets */
    ```

     <span data-ttu-id="2291e-158">现在，已经定义了两个命名集，它们已显示在“脚本组织程序”\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="2291e-158">You have now defined two named sets, which are visible in the **Script Organizer** pane.</span></span> <span data-ttu-id="2291e-159">现在，您可以部署这两个命名集，然后在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 多维数据集中浏览这些度量值。</span><span class="sxs-lookup"><span data-stu-id="2291e-159">You are now ready to deploy these named sets, and then to browse these measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

## <a name="browsing-the-cube-by-using-the-new-named-sets"></a><span data-ttu-id="2291e-160">使用新的命名集浏览多维数据集</span><span class="sxs-lookup"><span data-stu-id="2291e-160">Browsing the Cube by Using the New Named Sets</span></span>

1.  <span data-ttu-id="2291e-161">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的“生成”菜单上，单击“部署 Analysis Services 教程”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-161">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="2291e-162">已成功完成部署后，单击“浏览器”\*\*\*\* 选项卡，再单击“重新连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2291e-162">When deployment has successfully completed, click the **Browser** tab, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="2291e-163">清除数据窗格中的网格。</span><span class="sxs-lookup"><span data-stu-id="2291e-163">Clear the grid in the data pane.</span></span>

4.  <span data-ttu-id="2291e-164">将“分销商销售-销售额”\*\*\*\* 度量值添加到数据区域。</span><span class="sxs-lookup"><span data-stu-id="2291e-164">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

5.  <span data-ttu-id="2291e-165">展开“产品”维度，然后将“类别”和“子类别”添加到行区域中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2291e-165">Expand the Product dimension, and then add Category and Subcategory to the row area, as shown in the following image.</span></span>

     <span data-ttu-id="2291e-166">![Subcategory 属性的成员](../../2014/tutorials/media/l6-named-set-03.gif "Subcategory 属性的成员")</span><span class="sxs-lookup"><span data-stu-id="2291e-166">![Members of the Subcategory attribute](../../2014/tutorials/media/l6-named-set-03.gif "Members of the Subcategory attribute")</span></span>

6.  <span data-ttu-id="2291e-167">在“元数据”\*\*\*\* 窗格的“产品”\*\*\*\* 维度中，将“核心产品”\*\*\*\* 拖到筛选器区域。</span><span class="sxs-lookup"><span data-stu-id="2291e-167">In the **Metadata** pane, in the **Product** dimension, drag **Core Products** to the filter area.</span></span>

     <span data-ttu-id="2291e-168">请注意，只有“类别”\*\*\*\* 属性的“自行车”\*\*\*\* 成员和“自行车”\*\*\*\* 子类别的成员会留在多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="2291e-168">Notice that only the **Bike** member of the **Category** attribute and members of the **Bike** subcategories remain in the cube.</span></span> <span data-ttu-id="2291e-169">因为“核心产品”\*\*\*\* 命名集用于定义子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="2291e-169">This is because the **Core Products** named set is used to define a subcube.</span></span> <span data-ttu-id="2291e-170">此子多维数据集使得它包含的“产品”\*\*\*\* 维度中的“类别”\*\*\*\* 属性的成员仅限于“核心产品”\*\*\*\* 命名集的那些成员，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2291e-170">This subcube limits the members of the **Category** attribute in the **Product** dimension within the subcube to those members of the **Core Product** named set, as shown in the following image.</span></span>

     <span data-ttu-id="2291e-171">![“核心产品”命名集的成员](../../2014/tutorials/media/l6-named-set-04.gif "“核心产品”命名集的成员")</span><span class="sxs-lookup"><span data-stu-id="2291e-171">![Members of the Core Product named set](../../2014/tutorials/media/l6-named-set-04.gif "Members of the Core Product named set")</span></span>

7.  <span data-ttu-id="2291e-172">在“元数据”\*\*\*\* 窗格中，展开“分销商”\*\*\*\*，将“大型分销商”\*\*\*\* 添加到筛选器区域。</span><span class="sxs-lookup"><span data-stu-id="2291e-172">In the **Metadata** pane, expand **Reseller**, add **Large Resellers** to the filter area.</span></span>

     <span data-ttu-id="2291e-173">请注意，“数据”窗格中的“分销商销售额”度量值只显示大型自行车分销商的销售额。</span><span class="sxs-lookup"><span data-stu-id="2291e-173">Notice that the Reseller Sales Amount measure in the Data pane only displays sales amounts for large resellers of bikes.</span></span> <span data-ttu-id="2291e-174">还要注意，“筛选器”窗格现在显示用来定义此特定子多维数据集的两个命名集，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2291e-174">Notice also that the Filter pane now displays the two named sets that are used to define this particular subcube, as shown in the following image.</span></span>

     <span data-ttu-id="2291e-175">![包含两个命名集的筛选器窗格](../../2014/tutorials/media/l6-named-set-05.gif "包含两个命名集的筛选器窗格")</span><span class="sxs-lookup"><span data-stu-id="2291e-175">![Filter pane containing two named sets](../../2014/tutorials/media/l6-named-set-05.gif "Filter pane containing two named sets")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="2291e-176">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2291e-176">Next Task in Lesson</span></span>
 [<span data-ttu-id="2291e-177">第 7 课：定义关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="2291e-177">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)

## <a name="see-also"></a><span data-ttu-id="2291e-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2291e-178">See Also</span></span>
 <span data-ttu-id="2291e-179">[计算](multidimensional-models-olap-logical-cube-objects/calculations.md)[创建命名集](multidimensional-models/create-named-sets.md)</span><span class="sxs-lookup"><span data-stu-id="2291e-179">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) [Create Named Sets](multidimensional-models/create-named-sets.md)</span></span>


