---
title: 计算工具 (Kpi 选项卡，多维数据集设计器)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bb8470173b0a413795fb7b5e3213bb50aa8ee43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579273"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="95bf6-102">计算工具（KPI 选项卡，多维数据集设计器）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="95bf6-102">Calculation Tools (KPIs Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="95bf6-103">可以使用多维数据集中的“KPI”\*\*\*\* 选项卡上的“计算工具”\*\*\*\* 窗格，浏览在关键绩效指标 (KPI) 中可用的元数据、函数和模板。</span><span class="sxs-lookup"><span data-stu-id="95bf6-103">Use the **Calculation Tools** pane on the **KPIs** tab in Cube Designer to explore metadata, functions, and templates available for use in Key Performance Indicators (KPIs).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-104">此窗格仅显示在窗体视图中。</span><span class="sxs-lookup"><span data-stu-id="95bf6-104">This pane is displayed only in form view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="95bf6-105">选项</span><span class="sxs-lookup"><span data-stu-id="95bf6-105">Options</span></span>  
 <span data-ttu-id="95bf6-106">Metadata</span><span class="sxs-lookup"><span data-stu-id="95bf6-106">**Metadata**</span></span>  
 <span data-ttu-id="95bf6-107">显示所选多维数据集的元数据。</span><span class="sxs-lookup"><span data-stu-id="95bf6-107">Displays the metadata for the selected cube.</span></span>  
  
 <span data-ttu-id="95bf6-108">将所选元素拖到\*\*\*\*“KPI 窗体编辑器”窗格，可以在窗格中的所选位置包括该元素的多维表达式 (MDX) 语法。</span><span class="sxs-lookup"><span data-stu-id="95bf6-108">Drag a selected element to the **KPI Form Editor** pane to include the Multidimensional Expressions (MDX) syntax for that element at the selected location in the pane.</span></span>  
  
 <span data-ttu-id="95bf6-109">**函数**</span><span class="sxs-lookup"><span data-stu-id="95bf6-109">**Functions**</span></span>  
 <span data-ttu-id="95bf6-110">显示可用于表达式和条件的函数。</span><span class="sxs-lookup"><span data-stu-id="95bf6-110">Displays the functions available for expressions and conditions.</span></span>  
  
 <span data-ttu-id="95bf6-111">将所选元素拖到 **“KPI 窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="95bf6-111">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-112">在项目模式下， **“计算工具”** 对话框从随 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]提供的名为 MDXFunctions.xml 的 XML 文件中读取有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="95bf6-112">In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="95bf6-113">在联机模式下，从实例的 MDSCHEMA_FUNCTIONS 架构行集中检索有关此选项的信息。</span><span class="sxs-lookup"><span data-stu-id="95bf6-113">In online mode, information for this option is retrieved from the MDSCHEMA_FUNCTIONS schema rowset for the instance.</span></span>  
  
 <span data-ttu-id="95bf6-114">**模板**</span><span class="sxs-lookup"><span data-stu-id="95bf6-114">**Templates**</span></span>  
 <span data-ttu-id="95bf6-115">显示可用于 KPI 的预定义模板。</span><span class="sxs-lookup"><span data-stu-id="95bf6-115">Displays the predefined templates available for KPIs.</span></span>  
  
 <span data-ttu-id="95bf6-116">将所选元素拖到 **“KPI 窗体编辑器”** 窗格，可以在窗格中的所选位置包括该元素的 MDX 语法。</span><span class="sxs-lookup"><span data-stu-id="95bf6-116">Drag a selected element to the **KPI Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="95bf6-117">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="95bf6-117">Context Menu</span></span>  
 <span data-ttu-id="95bf6-118">右键单击“计算工具”\*\*\*\* 窗格中的元素后，可以从所显示的上下文菜单中访问以下选项：</span><span class="sxs-lookup"><span data-stu-id="95bf6-118">The following options are available in the context menu displayed by right-clicking an element in the **Calculation Tools** pane:</span></span>  
  
 <span data-ttu-id="95bf6-119">**复制**</span><span class="sxs-lookup"><span data-stu-id="95bf6-119">**Copy**</span></span>  
 <span data-ttu-id="95bf6-120">选择此选项可将在 **“元数据”** 或 **“函数”** 中选择的元素复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="95bf6-120">Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-121"> 如果选择 **“模板”** ，则不会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="95bf6-121">This option is not displayed if **Templates** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-122"> 如果无法复制所选成员（如 **“元数据”** 中所显示维度的 **“集”** 文件夹，或 **“函数”** 中所显示函数的函数组文件夹），则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="95bf6-122">This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.</span></span>  
  
 <span data-ttu-id="95bf6-123">**筛选成员**</span><span class="sxs-lookup"><span data-stu-id="95bf6-123">**Filter Members**</span></span>  
 <span data-ttu-id="95bf6-124">选择此选项可显示 **“筛选成员”** 对话框，并筛选为 **“元数据”** 中所选元素显示的成员。</span><span class="sxs-lookup"><span data-stu-id="95bf6-124">Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**.</span></span> <span data-ttu-id="95bf6-125">有关“筛选成员”\*\*\*\* 对话框的详细信息，请参阅[“筛选成员”对话框（Analysis Services - 多维数据）](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="95bf6-125">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-126"> 只有在选择了 **“元数据”** 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="95bf6-126">This option is displayed only if **Metadata** is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-127"> 只有在 **“元数据”** 中选择了属性的级别时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="95bf6-127">This option is enabled only if a level for an attribute is selected in **Metadata**.</span></span>  
  
 <span data-ttu-id="95bf6-128">**添加模板**</span><span class="sxs-lookup"><span data-stu-id="95bf6-128">**Add Template**</span></span>  
 <span data-ttu-id="95bf6-129">选择此选项可以基于所选模板向多维数据集脚本中添加新的计算成员、命名集或者脚本命令，并以窗体视图显示“KPI 窗体编辑器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="95bf6-129">Select to add a new calculated member, named set, or script command based on the selected template to the cube script and display the **KPI Form Editor** in form view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95bf6-130"> 只有在选择了 **“元数据”** 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="95bf6-130">This option is displayed only if **Metadata** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bf6-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95bf6-131">See Also</span></span>  
 <span data-ttu-id="95bf6-132">[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bf6-132">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="95bf6-133">[&#40;多维数据集设计器的 Kpi&#41; &#40;Analysis Services 多维数据&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bf6-133">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="95bf6-134">[工具栏 &#40;Kpi 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bf6-134">[Toolbar &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="95bf6-135">[KPI 组织程序 &#40;Kpi 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bf6-135">[KPI Organizer &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="95bf6-136">[KPI 窗体编辑器 &#40;Kpi 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bf6-136">[KPI Form Editor &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="95bf6-137">KPI 浏览器 &#40;Kpi 选项卡，多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="95bf6-137">KPI Browser &#40;KPIs Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
