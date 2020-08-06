---
title: 计算工具 (计算 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6701a15a7d773a90e48ec39dc976b9ef579c9ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579275"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="a7afb-102">计算工具（“计算”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="a7afb-102">Calculation Tools (Calculations Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="a7afb-103">可以使用多维数据集设计器中的 **“计算”** 选项卡的 **“计算工具”** 窗格，浏览在计算中可用的元数据、函数和模板。</span><span class="sxs-lookup"><span data-stu-id="a7afb-103">Use the **Calculation Tools** pane on the **Calculations** tab in Cube Designer to explore metadata, functions, and templates available for use in calculations.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7afb-104">选项</span><span class="sxs-lookup"><span data-stu-id="a7afb-104">Options</span></span>  
 <span data-ttu-id="a7afb-105">Metadata</span><span class="sxs-lookup"><span data-stu-id="a7afb-105">**Metadata**</span></span>  
 <span data-ttu-id="a7afb-106">显示所选多维数据集的元数据。</span><span class="sxs-lookup"><span data-stu-id="a7afb-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="a7afb-107">将所选元素拖到“脚本编辑器”、“计算成员窗体编辑器”或“命名集窗体编辑器”窗格，可以在窗格中的所选位置包括该元素的多维表达式 (MDX) 语法。</span><span class="sxs-lookup"><span data-stu-id="a7afb-107">Drag a selected element to the Script Editor, Calculated Member Form Editor, or Named Set Form Editor pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="a7afb-108">**函数**</span><span class="sxs-lookup"><span data-stu-id="a7afb-108">**Functions**</span></span>  
 <span data-ttu-id="a7afb-109">显示可用于表达式和条件的函数。</span><span class="sxs-lookup"><span data-stu-id="a7afb-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="a7afb-110">将所选元素拖到 **“脚本编辑器”**、 **“计算成员窗体编辑器”** 或 **“命名集窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="a7afb-110">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-111">在项目模式下， **“计算工具”** 对话框从随 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]提供的名为 MDXFunctions.xml 的 XML 文件中读取有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="a7afb-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a7afb-112">在联机模式下，从实例的 MDSCHEMA_FUNCTIONS 架构行集中检索有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="a7afb-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="a7afb-113">**模板**</span><span class="sxs-lookup"><span data-stu-id="a7afb-113">**Templates**</span></span>  
 <span data-ttu-id="a7afb-114">显示可用于计算成员、命名集和脚本命令的预定义模板。</span><span class="sxs-lookup"><span data-stu-id="a7afb-114">Displays the predefined templates available for calculated members, named sets, and script commands.</span></span>  
  
 <span data-ttu-id="a7afb-115">将所选元素拖到 **“脚本编辑器”**、 **“计算成员窗体编辑器”** 或 **“命名集窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="a7afb-115">Drag a selected element to the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="a7afb-116">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="a7afb-116">Context Menu</span></span>  
 <span data-ttu-id="a7afb-117">右键单击“计算工具”\*\*\*\* 窗格中的元素后，可以从所显示的上下文菜单中访问以下选项：</span><span class="sxs-lookup"><span data-stu-id="a7afb-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="a7afb-118">**复制**</span><span class="sxs-lookup"><span data-stu-id="a7afb-118">**Copy**</span></span>  
 <span data-ttu-id="a7afb-119">选择此选项可将在 **“元数据”** 或 **“函数”** 中选择的元素复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="a7afb-119">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-120"> 如果选择 **“模板”** ，则不会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="a7afb-120">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-121"> 如果无法复制所选成员（如 **“元数据”** 中所显示维度的 **“集”** 文件夹，或 **“函数”** 中所显示函数的函数组文件夹），则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="a7afb-121">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="a7afb-122">**筛选成员**</span><span class="sxs-lookup"><span data-stu-id="a7afb-122">**Filter Members**</span></span>  
 <span data-ttu-id="a7afb-123">选择此选项可显示 **“筛选成员”** 对话框，并筛选为 **“元数据”** 中所选元素显示的成员。</span><span class="sxs-lookup"><span data-stu-id="a7afb-123">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="a7afb-124">有关“筛选成员”\*\*\*\* 对话框的详细信息，请参阅[“筛选成员”对话框（Analysis Services - 多维数据）](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a7afb-124">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-125"> 只有在选择了 **“元数据”** 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="a7afb-125">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-126"> 只有在 **“元数据”** 中选择了属性的级别时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="a7afb-126">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="a7afb-127">**添加模板**</span><span class="sxs-lookup"><span data-stu-id="a7afb-127">**Add Template**</span></span>  
 <span data-ttu-id="a7afb-128">选择此选项可根据所选模板将新的计算成员、命名集或脚本命令添加到多维数据集脚本，并显示该命令相应的“脚本编辑器”\*\*\*\*、“计算成员窗体编辑器”\*\*\*\* 或“命名集窗体编辑器”\*\*\*\*（在窗体视图中），或者在“脚本编辑器”\*\*\*\* 窗格的内容中滚动到多维数据集脚本内该命令的位置（在脚本视图中）。</span><span class="sxs-lookup"><span data-stu-id="a7afb-128">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **Script Editor**, **Calculated Member Form Editor**, or **Named Set Form Editor** as appropriate for that command (in form view) or to scroll the contents of the **Script Editor** pane to the location of the command in the cube script (in script view).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a7afb-129"> 只有在选择了 **“元数据”** 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="a7afb-129">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7afb-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7afb-130">See Also</span></span>  
 <span data-ttu-id="a7afb-131">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-131">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7afb-132">[工具栏 &#40;"计算" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-132">[Toolbar &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7afb-133">[脚本组织程序 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-133">[Script Organizer &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7afb-134">[计算成员窗体编辑器 &#40;计算 "选项卡、多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-134">[Calculated Member Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7afb-135">[命名集窗体编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-135">[Named Set Form Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a7afb-136">[脚本编辑器 &#40;计算 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a7afb-136">[Script Editor &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a7afb-137">多维数据集设计器&#41; &#40;&#40;计算 Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="a7afb-137">Calculations &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
