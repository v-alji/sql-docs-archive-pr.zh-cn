---
title: 多维数据集设计器)  ( (Analysis Services 多维数据) 的计算 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.f1
ms.assetid: 46e2fbe2-bb41-4eaa-91f8-eb2bd3b8d00d
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdbc35a8e47557923b90cda4e72280c3cca940dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579903"
---
# <a name="calculations-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="e20e2-102">计算（多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="e20e2-102">Calculations (Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e20e2-103">可以使用多维数据集设计器中的“计算”\*\*\*\* 选项卡查看和编辑计算，包括所选多维数据集的计算成员、命名集和多维表达式 (MDX) 脚本命令。</span><span class="sxs-lookup"><span data-stu-id="e20e2-103">Use the **Calculations** tab in Cube Designer to view and edit calculations, including calculated members, named sets, and Multidimensional Expressions (MDX) script commands for the selected cube.</span></span>  
  
## <a name="form-view-and-script-view"></a><span data-ttu-id="e20e2-104">窗体视图和脚本视图</span><span class="sxs-lookup"><span data-stu-id="e20e2-104">Form View and Script View</span></span>  
 <span data-ttu-id="e20e2-105">在查看或编辑计算时， **“计算”** 选项卡支持两种不同的视图：</span><span class="sxs-lookup"><span data-stu-id="e20e2-105">The **Calculations** tab supports two different views when viewing or editing calculations:</span></span>  
  
-   <span data-ttu-id="e20e2-106">窗体视图</span><span class="sxs-lookup"><span data-stu-id="e20e2-106">Form view</span></span>  
  
     <span data-ttu-id="e20e2-107">此视图显示包含在与多维数据集关联的 MDX 脚本中的计算成员、命名集和脚本命令的结构化视图，并提供窗体编辑器以查看和编辑计算成员和命名集，以及显示可用于多维数据集的元数据、函数和工具。</span><span class="sxs-lookup"><span data-stu-id="e20e2-107">This view displays an organized view of the calculated members, named sets, and script commands contained in the MDX script associated with the cube and provides form editors to view and edit calculated members and named sets, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
-   <span data-ttu-id="e20e2-108">脚本视图</span><span class="sxs-lookup"><span data-stu-id="e20e2-108">Script view</span></span>  
  
     <span data-ttu-id="e20e2-109">对于高级用户，此视图显示与多维数据集关联的整个 MDX 脚本，以及显示可用于多维数据集的元数据、函数和工具。</span><span class="sxs-lookup"><span data-stu-id="e20e2-109">For advanced users, this view displays the entire MDX script associated with the cube, as well as displaying the metadata, functions, and tools available to the cube.</span></span>  
  
## <a name="panes"></a><span data-ttu-id="e20e2-110">窗格</span><span class="sxs-lookup"><span data-stu-id="e20e2-110">Panes</span></span>  
 <span data-ttu-id="e20e2-111">**工具栏**</span><span class="sxs-lookup"><span data-stu-id="e20e2-111">**Toolbar**</span></span>  
 <span data-ttu-id="e20e2-112">使用窗体视图和脚本视图中的工具栏可以执行此选项卡上的常规操作。有关此窗格的详细信息，请参阅[Toolbar &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-112">Use the toolbar in both form view and script view to perform common operations on this tab. For more information about this pane, see [Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e20e2-113">**脚本组织程序**</span><span class="sxs-lookup"><span data-stu-id="e20e2-113">**Script Organizer**</span></span>  
 <span data-ttu-id="e20e2-114">使用窗体视图中的“脚本组织程序”\*\*\*\* 窗格，可以按排序格式显示多维数据集脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="e20e2-114">Use the **Script Organizer** pane in form view to display the contents of the cube script in an ordered format.</span></span> <span data-ttu-id="e20e2-115">有关此窗格的详细信息，请参阅[脚本组织程序（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](script-organizer-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-115">For more information about this pane, see [Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e20e2-116">**计算工具**</span><span class="sxs-lookup"><span data-stu-id="e20e2-116">**Calculation Tools**</span></span>  
 <span data-ttu-id="e20e2-117">使用窗体视图和脚本视图中的“计算工具”\*\*\*\* 窗格，可以显示可用于多维数据集的元数据、函数和工具。</span><span class="sxs-lookup"><span data-stu-id="e20e2-117">Use the **Calculation Tools** pane in both form view and script view to display metadata, functions, and tools available to the cube.</span></span> <span data-ttu-id="e20e2-118">有关此窗格的详细信息，请参阅[计算工具（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-118">For more information about this pane, see [Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e20e2-119">**脚本编辑器**</span><span class="sxs-lookup"><span data-stu-id="e20e2-119">**Script Editor**</span></span>  
 <span data-ttu-id="e20e2-120">使用脚本视图中的“脚本编辑器”\*\*\*\* 窗格可以编辑整个多维数据集脚本，在窗体视图中使用该窗格可以编辑多维数据集脚本中所包含的脚本命令。</span><span class="sxs-lookup"><span data-stu-id="e20e2-120">Use the **Script Editor** pane in script view to edit the entire cube script and in form view to edit script commands contained in the cube script.</span></span> <span data-ttu-id="e20e2-121">有关此窗格的详细信息，请参阅[脚本编辑器（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-121">For more information about this pane, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e20e2-122">**计算成员窗体编辑器**</span><span class="sxs-lookup"><span data-stu-id="e20e2-122">**Calculated Member Form Editor**</span></span>  
 <span data-ttu-id="e20e2-123">使用窗体视图中的“计算成员窗体编辑器”\*\*\*\* 窗格可以编辑多维数据集脚本中的计算成员。</span><span class="sxs-lookup"><span data-stu-id="e20e2-123">Use the **Calculated Member Form Editor** pane in form view to edit calculated members in the cube script.</span></span> <span data-ttu-id="e20e2-124">有关此窗格的详细信息，请参阅[计算成员窗体编辑器（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-124">For more information about this pane, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="e20e2-125">**命名集窗体编辑器**</span><span class="sxs-lookup"><span data-stu-id="e20e2-125">**Named Set Form Editor**</span></span>  
 <span data-ttu-id="e20e2-126">使用窗体视图中的“命名集窗体编辑器”\*\*\*\* 窗格可以编辑多维数据集脚本中的命名集。</span><span class="sxs-lookup"><span data-stu-id="e20e2-126">Use the **Named Set Form Editor** pane in form view to edit named sets in the cube script.</span></span> <span data-ttu-id="e20e2-127">有关此窗格的详细信息，请参阅[命名集窗体编辑器（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e20e2-127">For more information about this pane, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20e2-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e20e2-128">See Also</span></span>  
 <span data-ttu-id="e20e2-129">[多维数据集对象 &#40;Analysis Services 多维数据&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e20e2-129">[Cube Objects &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="e20e2-130">[考虑](multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="e20e2-130">[Calculations](multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 <span data-ttu-id="e20e2-131">[MDX 脚本编写基础 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e20e2-131">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="e20e2-132">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e20e2-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e20e2-133">创建命名集</span><span class="sxs-lookup"><span data-stu-id="e20e2-133">Create Named Sets</span></span>](multidimensional-models/create-named-sets.md)  
  
  
