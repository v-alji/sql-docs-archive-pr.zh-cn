---
title: 脚本组织程序 (计算 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.scriptorganizerpane.f1
ms.assetid: 92624ca4-de67-4ebd-aab2-8adb527d327e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4ee8ccb491995176dc56da90e4cbf48961e30e98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579103"
---
# <a name="script-organizer-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="7a42d-102">脚本组织程序（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="7a42d-102">Script Organizer (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7a42d-103">可以使用多维数据集设计器中的 **“计算”** 选项卡上的 **“脚本组织程序”** 窗格，访问和重新排序指定多维数据集的多维数据集脚本中包含的计算成员、命名集和脚本命令。</span><span class="sxs-lookup"><span data-stu-id="7a42d-103">Use the **Script Organizer** pane on the **Calculations** tab in Cube Designer to access and reorder the calculated members, named sets, and script commands contained in the cube script for the specified cube.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a42d-104">在窗体视图中不显示此窗格。</span><span class="sxs-lookup"><span data-stu-id="7a42d-104">This pane is not displayed in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a42d-105">选项</span><span class="sxs-lookup"><span data-stu-id="7a42d-105">Options</span></span>  
 <span data-ttu-id="7a42d-106">**步骤**</span><span class="sxs-lookup"><span data-stu-id="7a42d-106">**Step**</span></span>  
 <span data-ttu-id="7a42d-107">显示多维数据集脚本中的计算成员、命名集和脚本命令的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="7a42d-107">Displays the execution order of the calculated members, named sets, and script commands within the cube script.</span></span>  
  
 <span data-ttu-id="7a42d-108">单击 **“工具栏”** 窗格或上下文菜单中的 **“上移”** 或 **“下移”** ，可以更改计算的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="7a42d-108">Click **Move Up** or **Move Down** in the **Toolbar** pane or context menu to change the execution order of the calculations.</span></span>  
  
 <span data-ttu-id="7a42d-109">**Type**</span><span class="sxs-lookup"><span data-stu-id="7a42d-109">**Type**</span></span>  
 <span data-ttu-id="7a42d-110">显示将计算标识为计算成员、命名集或脚本命令的图标。</span><span class="sxs-lookup"><span data-stu-id="7a42d-110">Displays an icon that identifies the calculation as a calculated member, a named set, or a script command.</span></span>  
  
 <span data-ttu-id="7a42d-111">**命令**</span><span class="sxs-lookup"><span data-stu-id="7a42d-111">**Command**</span></span>  
 <span data-ttu-id="7a42d-112">显示命令的名称（对于计算成员和命名集）或计算的第一行（对于脚本命令）。</span><span class="sxs-lookup"><span data-stu-id="7a42d-112">Displays the name of the command (for calculated members and named sets) or the first line of the calculation (for script commands.)</span></span>  
  
 <span data-ttu-id="7a42d-113">选择命令，可以显示适用于该命令的“脚本编辑器”、“计算成员窗体编辑器”或“命名集窗体编辑器”（在窗体视图中），或将“脚本编辑器”窗格的内容滚动到多维数据集脚本中该命令的位置（在脚本视图中）。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7a42d-113">Select a command to display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="7a42d-114">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="7a42d-114">Context Menu</span></span>  
 <span data-ttu-id="7a42d-115">右键单击“脚本组织程序”窗格中的命令后，可以从所显示的上下文菜单中访问以下选项：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="7a42d-115">The following options are available in the context menu displayed by right-clicking a command in the **Script Organizer** pane:</span></span>  
  
|<span data-ttu-id="7a42d-116">选项</span><span class="sxs-lookup"><span data-stu-id="7a42d-116">Option</span></span>|<span data-ttu-id="7a42d-117">定义</span><span class="sxs-lookup"><span data-stu-id="7a42d-117">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="7a42d-118">**新建计算成员**</span><span class="sxs-lookup"><span data-stu-id="7a42d-118">**New Calculated Member**</span></span>|<span data-ttu-id="7a42d-119">选择此项可显示 **计算成员窗体编辑器** 并创建新的计算成员。</span><span class="sxs-lookup"><span data-stu-id="7a42d-119">Select to display the **Calculated Member Form Editor** and create a new calculated member.</span></span> <span data-ttu-id="7a42d-120">有关**计算成员窗体编辑器**的详细信息，请参阅[计算成员窗体编辑器 &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7a42d-120">For more information about the **Calculated Member Form Editor**, see [Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="7a42d-121">**新建命名集**</span><span class="sxs-lookup"><span data-stu-id="7a42d-121">**New Named Set**</span></span>|<span data-ttu-id="7a42d-122">选择此项可显示 **命名集窗体编辑器** 并创建新的命名集。</span><span class="sxs-lookup"><span data-stu-id="7a42d-122">Select to display the **Named Set Form Editor** and create a new named set.</span></span> <span data-ttu-id="7a42d-123">有关**命名集窗体编辑器**的详细信息，请参阅[命名集窗体编辑器 &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7a42d-123">For more information about the **Named Set Form Editor**, see [Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="7a42d-124">**新建脚本命令**</span><span class="sxs-lookup"><span data-stu-id="7a42d-124">**New Script Command**</span></span>|<span data-ttu-id="7a42d-125">选择此项可显示 **脚本编辑器** 并创建新的脚本命令。</span><span class="sxs-lookup"><span data-stu-id="7a42d-125">Select to display the **Script Editor** and create a new script command.</span></span> <span data-ttu-id="7a42d-126">有关 "**脚本编辑器**" 的详细信息，请参阅[脚本编辑器 &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7a42d-126">For more information about the **Script Editor**, see [Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="7a42d-127">**上移**</span><span class="sxs-lookup"><span data-stu-id="7a42d-127">**Move Up**</span></span>|<span data-ttu-id="7a42d-128">选择此项可以将所选计算上移一个位置。</span><span class="sxs-lookup"><span data-stu-id="7a42d-128">Select to move the selected calculation up one place.</span></span><br /><br /> <span data-ttu-id="7a42d-129">注意：如果无法进一步移动所选计算，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="7a42d-129">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="7a42d-130">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="7a42d-130">**Move Down**</span></span>|<span data-ttu-id="7a42d-131">选择此项可以将所选计算下移一个位置。</span><span class="sxs-lookup"><span data-stu-id="7a42d-131">Select to move the selected calculation down one place.</span></span><br /><br /> <span data-ttu-id="7a42d-132">注意：如果无法进一步移动所选计算，将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="7a42d-132">Note: This option is disabled if the selected calculation cannot be moved further.</span></span>|  
|<span data-ttu-id="7a42d-133">**删除**</span><span class="sxs-lookup"><span data-stu-id="7a42d-133">**Delete**</span></span>|<span data-ttu-id="7a42d-134">选择此项将删除所选计算。</span><span class="sxs-lookup"><span data-stu-id="7a42d-134">Select to delete the selected calculation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a42d-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a42d-135">See Also</span></span>  
 <span data-ttu-id="7a42d-136">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7a42d-137">[工具栏 &#40;"计算" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-137">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7a42d-138">[计算工具 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-138">[Calculation Tools &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7a42d-139">[计算成员窗体编辑器 &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-139">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7a42d-140">[命名集窗体编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-140">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7a42d-141">[脚本编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7a42d-141">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7a42d-142">多维数据集设计器&#41; &#40;&#40;计算 Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="7a42d-142">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
