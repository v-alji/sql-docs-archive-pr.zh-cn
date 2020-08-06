---
title: 挖掘模型查看器 (的项集选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b99b62b01b196fd62e1ef264e530487018f6a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579153"
---
# <a name="itemsets-tab-mining-model-viewer"></a><span data-ttu-id="17a63-102">“项集”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="17a63-102">Itemsets Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="17a63-103">可以使用 **“项集”** 窗格查看关联规则挖掘模型包含的频繁项集。</span><span class="sxs-lookup"><span data-stu-id="17a63-103">You can use the **Itemsets** pane to view the frequent itemsets that an association rules mining model contains.</span></span> <span data-ttu-id="17a63-104">由于关联模型可包含多个项集，因此，查看器中提供了一些控件，帮助您筛选在查看器中显示的项集。</span><span class="sxs-lookup"><span data-stu-id="17a63-104">Because an association model can contain many itemsets, controls are provided in the viewer to help you filter the itemsets that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="17a63-105">**有关详细信息：** [Microsoft 关联算法](data-mining/microsoft-association-algorithm.md)、[使用 Microsoft 关联规则查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="17a63-105">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="17a63-106">选项</span><span class="sxs-lookup"><span data-stu-id="17a63-106">Options</span></span>  
 <span data-ttu-id="17a63-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="17a63-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="17a63-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="17a63-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="17a63-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="17a63-109">**Mining Model**</span></span>  
 <span data-ttu-id="17a63-110">选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="17a63-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="17a63-111">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="17a63-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="17a63-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="17a63-112">**Viewer**</span></span>  
 <span data-ttu-id="17a63-113">选择用于查看所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="17a63-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="17a63-114">可以对关联模型使用自定义查看器，也可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="17a63-114">You can use either the custom viewer for association models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="17a63-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="17a63-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="17a63-116">**最低支持**</span><span class="sxs-lookup"><span data-stu-id="17a63-116">**Minimum support**</span></span>  
 <span data-ttu-id="17a63-117">更改此值可设置项集要显示在查看器中所必须具有的最低支持。</span><span class="sxs-lookup"><span data-stu-id="17a63-117">Change this value to set the minimum support that an itemset must contain to appear in the viewer.</span></span> <span data-ttu-id="17a63-118">模型将计算您在首次打开它时显示的默认值，但您可以更改该值以查看更多或更少项集。</span><span class="sxs-lookup"><span data-stu-id="17a63-118">The default value that is displayed when you first open the model is calculated by the model, but you can change it to see more or fewer itemsets.</span></span>  
  
 <span data-ttu-id="17a63-119">**最小项集大小**</span><span class="sxs-lookup"><span data-stu-id="17a63-119">**Minimum itemset size**</span></span>  
 <span data-ttu-id="17a63-120">更改此值可设置在查看器中可以显示某个项集之前，必须包含在该项集中的项的最小数目。</span><span class="sxs-lookup"><span data-stu-id="17a63-120">Change this value to set the minimum number of items that must be included in an itemset before the itemset can be displayed in the viewer.</span></span>  
  
 <span data-ttu-id="17a63-121">**筛选项集**</span><span class="sxs-lookup"><span data-stu-id="17a63-121">**Filter Itemset**</span></span>  
 <span data-ttu-id="17a63-122">键入一个字符串值可筛选查看器中显示的项集数。</span><span class="sxs-lookup"><span data-stu-id="17a63-122">Type a string value to filter the number of itemsets that appear in the viewer.</span></span>  
  
 <span data-ttu-id="17a63-123">还可以键入 .NET 正则表达式作为筛选条件。</span><span class="sxs-lookup"><span data-stu-id="17a63-123">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="17a63-124">例如，下面的表达式将返回包含“Road Bottle Cage”的所有项集：</span><span class="sxs-lookup"><span data-stu-id="17a63-124">For example, the following expression returns all itemsets that contain 'Road Bottle Cage':</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 <span data-ttu-id="17a63-125">请注意，您可能需要刷新视图以查看筛选条件应用情况。</span><span class="sxs-lookup"><span data-stu-id="17a63-125">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="17a63-126">还可以启用和禁用 **“显示长名称”** 选项以刷新列表。</span><span class="sxs-lookup"><span data-stu-id="17a63-126">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="17a63-127">默认情况下，筛选条件应用于属性-值组合的完整名称；因此，如果您只查看属性名称，则可能无法明确知道已正确应用筛选条件。</span><span class="sxs-lookup"><span data-stu-id="17a63-127">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="17a63-128">使用 **“显示”** 下拉列表可选择 **“显示属性名称和值”**，并验证是否已正确筛选项集的列表。</span><span class="sxs-lookup"><span data-stu-id="17a63-128">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="17a63-129">**显示**</span><span class="sxs-lookup"><span data-stu-id="17a63-129">**Show**</span></span>  
 <span data-ttu-id="17a63-130">调整项集在查看器中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="17a63-130">Adjust how the itemset is displayed in the viewer.</span></span> <span data-ttu-id="17a63-131">可以选择以下三个选项之一：</span><span class="sxs-lookup"><span data-stu-id="17a63-131">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="17a63-132">显示属性名称和值</span><span class="sxs-lookup"><span data-stu-id="17a63-132">Show attribute name and value</span></span>  
  
-   <span data-ttu-id="17a63-133">仅显示属性值</span><span class="sxs-lookup"><span data-stu-id="17a63-133">Show attribute value only</span></span>  
  
-   <span data-ttu-id="17a63-134">仅显示属性名称</span><span class="sxs-lookup"><span data-stu-id="17a63-134">Show attribute name only</span></span>  
  
 <span data-ttu-id="17a63-135">请注意，此选项不会重新查询模型；它仅筛选所显示的属性或值。</span><span class="sxs-lookup"><span data-stu-id="17a63-135">Note that this option does not requery the model; it only filters the attributes or values that are displayed.</span></span>  
  
 <span data-ttu-id="17a63-136">**“显示长名称”**</span><span class="sxs-lookup"><span data-stu-id="17a63-136">**Show long name**</span></span>  
 <span data-ttu-id="17a63-137">选择此选项可当项集显示在挖掘模型内容中时显示其全名。</span><span class="sxs-lookup"><span data-stu-id="17a63-137">Select this option to display the full name of the itemset as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="17a63-138">**最大行数**</span><span class="sxs-lookup"><span data-stu-id="17a63-138">**Maximum rows**</span></span>  
 <span data-ttu-id="17a63-139">限制查看器中显示的项集数。</span><span class="sxs-lookup"><span data-stu-id="17a63-139">Limit the number of itemsets that are displayed in the viewer.</span></span> <span data-ttu-id="17a63-140">默认情况下，按照支持以降序顺序对项集进行排序，因此，减小此值将限制为仅列出最常用项集。</span><span class="sxs-lookup"><span data-stu-id="17a63-140">By default, itemsets are ordered by support in descending order, so lowering this value restricts the list to the most common itemsets.</span></span>  
  
 <span data-ttu-id="17a63-141">**支持**</span><span class="sxs-lookup"><span data-stu-id="17a63-141">**Support**</span></span>  
 <span data-ttu-id="17a63-142">显示对每个项集的支持。</span><span class="sxs-lookup"><span data-stu-id="17a63-142">Displays the support for each itemset.</span></span>  
  
 <span data-ttu-id="17a63-143">**大小**</span><span class="sxs-lookup"><span data-stu-id="17a63-143">**Size**</span></span>  
 <span data-ttu-id="17a63-144">显示每个项集中包含的项数。</span><span class="sxs-lookup"><span data-stu-id="17a63-144">Displays the number of items that exist in each itemset.</span></span>  
  
 <span data-ttu-id="17a63-145">**项集**</span><span class="sxs-lookup"><span data-stu-id="17a63-145">**Itemset**</span></span>  
 <span data-ttu-id="17a63-146">显示每个项集的说明。</span><span class="sxs-lookup"><span data-stu-id="17a63-146">Displays the description of each itemset.</span></span> <span data-ttu-id="17a63-147">默认情况下，项集将表示为属性及其值的以逗号分隔的列表。</span><span class="sxs-lookup"><span data-stu-id="17a63-147">By default, itemsets are presented as a comma-delimited list of attributes and their values.</span></span> <span data-ttu-id="17a63-148">可以使用 **“显示”** 选项来更改其显示方式。</span><span class="sxs-lookup"><span data-stu-id="17a63-148">You can change the way they are displayed by using the **Show** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a63-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17a63-149">See Also</span></span>  
 <span data-ttu-id="17a63-150">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="17a63-150">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="17a63-151">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="17a63-151">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="17a63-152">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="17a63-152">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
