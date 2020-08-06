---
title: 计算工具 (操作 "选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123fa38ea2decb6af914e93fcefda4508f08545e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579274"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="c5abd-102">计算工具（“操作”选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c5abd-102">Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c5abd-103">可以使用多维数据集设计器中的 **“操作”** 选项卡上的 **“计算工具”** 窗格，浏览在操作、钻取操作和报表操作中可用的元数据、函数和模板。</span><span class="sxs-lookup"><span data-stu-id="c5abd-103">Use the **Calculation Tools** pane on the **Actions** tab in Cube Designer to explore metadata, functions, and templates available for use in actions, drillthrough actions, and report actions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c5abd-104">选项</span><span class="sxs-lookup"><span data-stu-id="c5abd-104">Options</span></span>  
 <span data-ttu-id="c5abd-105">Metadata</span><span class="sxs-lookup"><span data-stu-id="c5abd-105">**Metadata**</span></span>  
 <span data-ttu-id="c5abd-106">显示所选多维数据集的元数据。</span><span class="sxs-lookup"><span data-stu-id="c5abd-106">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="c5abd-107">将所选元素拖到“操作窗体编辑器”\*\*\*\*、“钻取操作窗体编辑器”\*\*\*\* 或“报表操作窗体编辑器”\*\*\*\* 窗格，可以在窗格中的所选位置包括该元素的多维表达式 (MDX) 语法。</span><span class="sxs-lookup"><span data-stu-id="c5abd-107">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="c5abd-108">**函数**</span><span class="sxs-lookup"><span data-stu-id="c5abd-108">**Functions**</span></span>  
 <span data-ttu-id="c5abd-109">显示可用于表达式和条件的函数。</span><span class="sxs-lookup"><span data-stu-id="c5abd-109">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="c5abd-110">将所选元素拖到 **“操作窗体编辑器”**、 **“钻取操作窗体编辑器”** 或 **“报表操作窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="c5abd-110">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5abd-111">在项目模式下， **“计算工具”** 对话框从随 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]提供的名为 MDXFunctions.xml 的 XML 文件中读取有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="c5abd-111">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c5abd-112">在联机模式下，从实例的 MDSCHEMA_FUNCTIONS 架构行集中检索有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="c5abd-112">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="c5abd-113">**模板**</span><span class="sxs-lookup"><span data-stu-id="c5abd-113">**Templates**</span></span>  
 <span data-ttu-id="c5abd-114">显示可用于操作的预定义模板。</span><span class="sxs-lookup"><span data-stu-id="c5abd-114">Displays the predefined templates available for actions.</span></span>  
  
 <span data-ttu-id="c5abd-115">将所选元素拖到 **“操作窗体编辑器”**、 **“钻取操作窗体编辑器”** 或 **“报表操作窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="c5abd-115">Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="c5abd-116">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="c5abd-116">Context Menu</span></span>  
 <span data-ttu-id="c5abd-117">右键单击“计算工具”\*\*\*\* 窗格中的元素后，可以从所显示的上下文菜单中访问以下选项：</span><span class="sxs-lookup"><span data-stu-id="c5abd-117">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
|<span data-ttu-id="c5abd-118">选项</span><span class="sxs-lookup"><span data-stu-id="c5abd-118">Option</span></span>|<span data-ttu-id="c5abd-119">定义</span><span class="sxs-lookup"><span data-stu-id="c5abd-119">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="c5abd-120">**复制**</span><span class="sxs-lookup"><span data-stu-id="c5abd-120">**Copy**</span></span>|<span data-ttu-id="c5abd-121">选择此选项可将在 **“元数据”** 或 **“函数”** 中选择的元素复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="c5abd-121">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span><br /><br /> <span data-ttu-id="c5abd-122">请注意，如果选择 "**模板**"，则不会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="c5abd-122">Note that this option is not displayed if **Templates** is selected.</span></span> <span data-ttu-id="c5abd-123">另请注意，如果无法复制所选成员（例如，在**元数据**中显示维度的 "**集**" 文件夹，或**函数中显示**函数的函数组文件夹），则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="c5abd-123">Also note that this option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>|  
|<span data-ttu-id="c5abd-124">**筛选成员**</span><span class="sxs-lookup"><span data-stu-id="c5abd-124">**Filter Members**</span></span>|<span data-ttu-id="c5abd-125">选择此选项可显示 **“筛选成员”** 对话框，并筛选为 **“元数据”** 中所选元素显示的成员。</span><span class="sxs-lookup"><span data-stu-id="c5abd-125">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="c5abd-126">有关“筛选成员”\*\*\*\* 对话框的详细信息，请参阅[“筛选成员”对话框（Analysis Services - 多维数据）](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c5abd-126">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="c5abd-127">请注意，只有在选择了 "**元数据**" 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="c5abd-127">Note that this option is displayed only if **Metadata** is selected.</span></span> <span data-ttu-id="c5abd-128">另请注意，只有在 "**元数据**" 中选择了属性的级别时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="c5abd-128">Also note that this option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>|  
|<span data-ttu-id="c5abd-129">**添加模板**</span><span class="sxs-lookup"><span data-stu-id="c5abd-129">**Add Template**</span></span>|<span data-ttu-id="c5abd-130">选择此选项可以基于所选模板，将新的操作、钻取操作或报表操作添加到多维数据集，并分别显示 **操作窗体编辑器**、 **钻取操作窗体编辑器**或 **报表操作窗体编辑器**。</span><span class="sxs-lookup"><span data-stu-id="c5abd-130">Select to add a new action, drillthrough action, or report action based on the selected template to the cube and display, respectively, the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor**.</span></span><br /><br /> <span data-ttu-id="c5abd-131">注意：只有在选择了 "**元数据**" 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="c5abd-131">Note: This option is displayed only if **Metadata** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5abd-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5abd-132">See Also</span></span>  
 <span data-ttu-id="c5abd-133">[MDX 脚本编写基础 &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-133">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="c5abd-134">[&#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据的操作&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-134">[Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](actions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c5abd-135">[工具栏 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-135">[Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c5abd-136">[操作管理器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-136">[Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c5abd-137">[操作窗体编辑器 &#40;"操作" 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-137">[Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c5abd-138">[钻取操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c5abd-138">[Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c5abd-139">报表操作窗体编辑器 &#40;操作 "选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="c5abd-139">Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
