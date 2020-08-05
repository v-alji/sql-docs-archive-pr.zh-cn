---
title: 第6课：定义计算 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e0b3f7e925a11146204dc6c55e9ddd6820ecb802
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580972"
---
# <a name="lesson-6-defining-calculations"></a><span data-ttu-id="d2133-102">第 6 课：定义计算</span><span class="sxs-lookup"><span data-stu-id="d2133-102">Lesson 6: Defining Calculations</span></span>
  <span data-ttu-id="d2133-103">在此课程中，将了解如何定义计算（多维表达式 (MDX) 表达式或脚本）。</span><span class="sxs-lookup"><span data-stu-id="d2133-103">In this lesson, you learn to define calculations, which are Multidimensional Expressions (MDX) expressions or scripts.</span></span> <span data-ttu-id="d2133-104">计算功能允许您定义计算成员、命名集并执行其他脚本命令，以扩展 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多维数据集的功能。</span><span class="sxs-lookup"><span data-stu-id="d2133-104">Calculations enable you to define calculated members, named sets, and execute other script commands to extend the capabilities of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span> <span data-ttu-id="d2133-105">例如，您可以运行脚本命令来定义子多维数据集，然后为该子多维数据集中的单元分配计算。</span><span class="sxs-lookup"><span data-stu-id="d2133-105">For example, you can run a script command to define a subcube and then assign a calculation to the cells in the subcube.</span></span>  
  
 <span data-ttu-id="d2133-106">在“多维数据集设计器”中定义新的计算时，会将该计算添加到“多维数据集设计器”的“计算”\*\*\*\* 选项卡上的“脚本组织程序”\*\*\*\* 窗格中，并在“计算表达式”\*\*\*\* 窗格中的计算窗体内显示特定计算类型的字段。</span><span class="sxs-lookup"><span data-stu-id="d2133-106">When you define a new calculation in Cube Designer, the calculation is added to the **Script Organizer** pane of the **Calculations** tab of Cube Designer, and the fields for the particular calculation type are displayed in a calculations form in the **Calculation Expressions** pane.</span></span> <span data-ttu-id="d2133-107">计算将按照它们在“脚本组织程序”\*\*\*\* 窗格中列出的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="d2133-107">Calculations are executed in the order in which they are listed in the **Script Organizer** pane.</span></span> <span data-ttu-id="d2133-108">可以重新排列计算，方法是右键单击特定计算，再选择“上移”\*\*\*\* 或“下移”\*\*\*\*，或者单击特定的计算，再使用“计算”\*\*\*\* 选项卡的工具栏上的“上移”\*\*\*\* 或“下移”\*\*\*\* 图标。</span><span class="sxs-lookup"><span data-stu-id="d2133-108">You can reorder the calculations by right-clicking on a particular calculation and then selecting **Move Up** or **Move Down**, or by clicking a particular calculation and then using the **Move Up** or **Move Down** icons on the toolbar of the **Calculations** tab.</span></span>  
  
 <span data-ttu-id="d2133-109">在“计算”\*\*\*\* 选项卡上，可以添加新的计算，并在“计算表达式”\*\*\*\* 窗格中的下列视图内查看或编辑现有计算：</span><span class="sxs-lookup"><span data-stu-id="d2133-109">On the **Calculations** tab, you can add new calculations and view or edit existing calculations in the following views in the **Calculation Expressions** pane:</span></span>  
  
-   <span data-ttu-id="d2133-110">窗体视图。</span><span class="sxs-lookup"><span data-stu-id="d2133-110">Form view.</span></span> <span data-ttu-id="d2133-111">此视图以图形格式显示单个命令的表达式和属性。</span><span class="sxs-lookup"><span data-stu-id="d2133-111">This view shows the expressions and properties for a single command in a graphical format.</span></span> <span data-ttu-id="d2133-112">编辑 MDX 脚本时，表达式框将填充窗体视图。</span><span class="sxs-lookup"><span data-stu-id="d2133-112">When you edit an MDX script, an expression box fills the Form view.</span></span>  
  
-   <span data-ttu-id="d2133-113">脚本视图。</span><span class="sxs-lookup"><span data-stu-id="d2133-113">Script view.</span></span> <span data-ttu-id="d2133-114">此视图显示代码编辑器中的所有计算脚本，这让您很容易更改计算脚本。</span><span class="sxs-lookup"><span data-stu-id="d2133-114">This view displays all calculation scripts in a code editor, which lets you easily change the calculation scripts.</span></span> <span data-ttu-id="d2133-115">“计算表达式”\*\*\*\* 窗格在“脚本视图中”时，将隐藏“脚本组织程序”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d2133-115">When the **Calculation Expressions** pane is in Script view, the **Script Organizer** is hidden.</span></span> <span data-ttu-id="d2133-116">脚本视图提供了彩色编码、括号匹配、自动完成和 MDX 代码区域。</span><span class="sxs-lookup"><span data-stu-id="d2133-116">The Script view provides color coding, parenthesis matching, auto-complete, and MDX code regions.</span></span> <span data-ttu-id="d2133-117">可以展开或折叠 MDX 代码区域，以使编辑更容易。</span><span class="sxs-lookup"><span data-stu-id="d2133-117">You can expand or collapse the MDX code regions to make editing easier.</span></span>  
  
 <span data-ttu-id="d2133-118">若要在“计算表达式”\*\*\*\* 窗格中的这些视图之间进行切换，请在“计算”\*\*\*\* 选项卡的工具栏上单击“窗体视图”\*\*\*\* 或“脚本视图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d2133-118">To switch between these views in the **Calculation Expressions** pane, click **Form View** or **Script View** on the toolbar of the **Calculations** tab.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2133-119">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在任何计算中检测到语法错误，将不会显示窗体视图，直到在脚本视图中将错误纠正。</span><span class="sxs-lookup"><span data-stu-id="d2133-119">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detects a syntax error in any calculation, the Form view will not display until the error is corrected in the Script view.</span></span>  
  
 <span data-ttu-id="d2133-120">还可以使用商业智能向导，将某些计算添加到多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="d2133-120">You can also use the Business Intelligence Wizard to add certain calculations to a cube.</span></span> <span data-ttu-id="d2133-121">例如，可以使用此向导将时间智能添加到多维数据集中，这意味着为与时间相关的计算（例如，“本期截止到现在”、“移动平均”和“期间到期间”）定义计算成员。</span><span class="sxs-lookup"><span data-stu-id="d2133-121">For example, you can use this wizard to add time intelligence to a cube, which means defining calculated members for time-related calculations such as period-to-date, moving averages, or period over period growth.</span></span> <span data-ttu-id="d2133-122">有关详细信息，请参阅 [使用商业智能向导定义时间智能计算](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d2133-122">For more information, see [Define Time Intelligence Calculations using the Business Intelligence Wizard](multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2133-123">在“计算”\*\*\*\* 选项卡上，计算脚本从 CALCULATE 命令开始。</span><span class="sxs-lookup"><span data-stu-id="d2133-123">On the **Calculations** tab, the calculation script starts with the CALCULATE command.</span></span> <span data-ttu-id="d2133-124">CALCULATE 命令控制多维数据集中的单元的聚合，应当只在需要手动指定多维数据集单元应当如何聚合时，才编辑此命令。</span><span class="sxs-lookup"><span data-stu-id="d2133-124">The CALCULATE command controls the aggregation of the cells in the cube and you should edit this command only if you intend to manually specify how the cube cells should be aggregated.</span></span>  
  
 <span data-ttu-id="d2133-125">有关详细信息，请参阅 [计算](multidimensional-models-olap-logical-cube-objects/calculations.md)和 [多维模型中的计算](multidimensional-models/calculations-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="d2133-125">For more information, see [Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md), and [Calculations in Multidimensional Models](multidimensional-models/calculations-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2133-126">本教程的所有课程中的已完成项目均可以从网上获得。</span><span class="sxs-lookup"><span data-stu-id="d2133-126">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="d2133-127">您可以通过将前一课程的已完成项目作为起始点，跳转到后面的任何课程。</span><span class="sxs-lookup"><span data-stu-id="d2133-127">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="d2133-128">[单击此处](https://go.microsoft.com/fwlink/?LinkID=221866) 可以下载本教程随附的示例项目。</span><span class="sxs-lookup"><span data-stu-id="d2133-128">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="d2133-129">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="d2133-129">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="d2133-130">定义计算成员</span><span class="sxs-lookup"><span data-stu-id="d2133-130">Defining Calculated Members</span></span>](lesson-6-1-defining-calculated-members.md)  
 <span data-ttu-id="d2133-131">在此任务中，将了解定义计算成员。</span><span class="sxs-lookup"><span data-stu-id="d2133-131">In this task, you learn to define calculated members.</span></span>  
  
 [<span data-ttu-id="d2133-132">定义命名集</span><span class="sxs-lookup"><span data-stu-id="d2133-132">Defining Named Sets</span></span>](lesson-6-2-defining-named-sets.md)  
 <span data-ttu-id="d2133-133">在此任务中，将了解定义命名集。</span><span class="sxs-lookup"><span data-stu-id="d2133-133">In this task, you learn to define named sets.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="d2133-134">下一课</span><span class="sxs-lookup"><span data-stu-id="d2133-134">Next Lesson</span></span>  
 [<span data-ttu-id="d2133-135">第 7 课：定义关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="d2133-135">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2133-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2133-136">See Also</span></span>  
 <span data-ttu-id="d2133-137">[Analysis Services 教程方案](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d2133-137">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="d2133-138">[&#40;艾德作品的多维建模教程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d2133-138">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="d2133-139">[创建命名集](multidimensional-models/create-named-sets.md) </span><span class="sxs-lookup"><span data-stu-id="d2133-139">[Create Named Sets](multidimensional-models/create-named-sets.md) </span></span>  
 [<span data-ttu-id="d2133-140">创建计算成员</span><span class="sxs-lookup"><span data-stu-id="d2133-140">Create Calculated Members</span></span>](multidimensional-models/create-calculated-members.md)  
  
  
