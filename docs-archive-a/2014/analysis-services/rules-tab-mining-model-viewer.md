---
title: 挖掘模型查看器 (的 "规则" 选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0d86931865fd9352074669de93b14dacfc84537
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579119"
---
# <a name="rules-tab-mining-model-viewer"></a><span data-ttu-id="1e276-102">“规则”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="1e276-102">Rules Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="1e276-103">可以使用关联模型中的 **“规则”** 窗格来查看算法从数据中提取的规则。</span><span class="sxs-lookup"><span data-stu-id="1e276-103">Use the **Rules** pane in an association model to view the rules that the algorithm extracted from the data.</span></span> <span data-ttu-id="1e276-104">规则不仅说明了各项之间相互关联的方式，并且可用于创建建议。</span><span class="sxs-lookup"><span data-stu-id="1e276-104">Rules describe how items are related to each other, and can be used to create recommendations.</span></span>  
  
 <span data-ttu-id="1e276-105">您可以使用查看器中的选项进行筛选以更改查看器中显示的规则数。</span><span class="sxs-lookup"><span data-stu-id="1e276-105">You can use the options in the viewer to filter the number of rules that are displayed in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1e276-106">默认情况下，查看器中仅显示大于 **“最小概率”** 中定义的概率阈值的规则。</span><span class="sxs-lookup"><span data-stu-id="1e276-106">By default, only the rules that are above the probability threshold defined in **Minimum probability** are displayed in the viewer.</span></span> <span data-ttu-id="1e276-107">无法使用查看器减小该值，因为规则输出的概率阈值是在创建模型时确定的。</span><span class="sxs-lookup"><span data-stu-id="1e276-107">You cannot make this value any smaller by using the viewer, because the probability threshold for rule output is determined when the model is created.</span></span> <span data-ttu-id="1e276-108">有关详细信息，请参阅 [Microsoft 关联算法技术参考](data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="1e276-108">For more information, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="1e276-109">**有关详细信息：** [Microsoft 关联算法](data-mining/microsoft-association-algorithm.md)、[使用 Microsoft 关联规则查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="1e276-109">**For More Information:** [Microsoft Association Algorithm](data-mining/microsoft-association-algorithm.md), [Browse a Model Using the Microsoft Association Rules Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e276-110">选项</span><span class="sxs-lookup"><span data-stu-id="1e276-110">Options</span></span>  
 <span data-ttu-id="1e276-111">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="1e276-111">**Refresh viewer content**</span></span>  
 <span data-ttu-id="1e276-112">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e276-112">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="1e276-113">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="1e276-113">**Mining Model**</span></span>  
 <span data-ttu-id="1e276-114">选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="1e276-114">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="1e276-115">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="1e276-115">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="1e276-116">**查看器**</span><span class="sxs-lookup"><span data-stu-id="1e276-116">**Viewer**</span></span>  
 <span data-ttu-id="1e276-117">选择用于查看所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="1e276-117">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="1e276-118">可以对每个挖掘模型使用自定义查看器，也可以使用 **“Microsoft 一般内容树查看器”**。</span><span class="sxs-lookup"><span data-stu-id="1e276-118">You can use the custom viewer for each mining model, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="1e276-119">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="1e276-119">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="1e276-120">**“最小概率”**</span><span class="sxs-lookup"><span data-stu-id="1e276-120">**Minimum probability**</span></span>  
 <span data-ttu-id="1e276-121">更改此值可设置在查看器中显示规则所需的最小概率。</span><span class="sxs-lookup"><span data-stu-id="1e276-121">Change this value to set the minimum probability required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="1e276-122">增大概率值将减少显示的规则的数目。</span><span class="sxs-lookup"><span data-stu-id="1e276-122">Increasing the value for probability will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="1e276-123">**最低重要性**</span><span class="sxs-lookup"><span data-stu-id="1e276-123">**Minimum importance**</span></span>  
 <span data-ttu-id="1e276-124">更改此值可设置在查看器中显示规则所需的最低重要性。</span><span class="sxs-lookup"><span data-stu-id="1e276-124">Change this value to set the minimum importance required for a rule to be displayed in the viewer.</span></span> <span data-ttu-id="1e276-125">增大重要性的值将减少显示的规则的数目。</span><span class="sxs-lookup"><span data-stu-id="1e276-125">Increasing the value for importance will reduce the number of rules that are displayed.</span></span>  
  
 <span data-ttu-id="1e276-126">**筛选规则**</span><span class="sxs-lookup"><span data-stu-id="1e276-126">**Filter Rule**</span></span>  
 <span data-ttu-id="1e276-127">键入一个字符串值可筛选查看器中显示的规则数。</span><span class="sxs-lookup"><span data-stu-id="1e276-127">Type a string value to filter the number of rules that appear in the viewer.</span></span>  
  
 <span data-ttu-id="1e276-128">还可以键入 .NET 正则表达式作为筛选条件。</span><span class="sxs-lookup"><span data-stu-id="1e276-128">You can also type .NET regular expressions as filter criteria.</span></span> <span data-ttu-id="1e276-129">例如，下面的表达式将返回其左侧包含“Road Bottle Cage”的所有规则：</span><span class="sxs-lookup"><span data-stu-id="1e276-129">For example, the following expression returns all rules that contain 'Road Bottle Cage' on the left side of the rule:</span></span>  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 <span data-ttu-id="1e276-130">请注意，您可能需要刷新视图以查看筛选条件应用情况。</span><span class="sxs-lookup"><span data-stu-id="1e276-130">Note that you might need to refresh the view to see the filter criteria apply.</span></span> <span data-ttu-id="1e276-131">还可以启用和禁用 **“显示长名称”** 选项以刷新列表。</span><span class="sxs-lookup"><span data-stu-id="1e276-131">You can also toggle the **Show long name** option on and off to refresh the list.</span></span>  
  
 <span data-ttu-id="1e276-132">默认情况下，筛选条件应用于属性-值组合的完整名称；因此，如果您只查看属性名称，则可能无法明确知道已正确应用筛选条件。</span><span class="sxs-lookup"><span data-stu-id="1e276-132">By default the filter criteria applies to the full name of the attribute-value combination; therefore, if you are viewing the attribute name only, it might not be obvious that the filter criteria has applied correctly.</span></span> <span data-ttu-id="1e276-133">使用 **“显示”** 下拉列表可选择 **“显示属性名称和值”**，并验证是否已正确筛选项集的列表。</span><span class="sxs-lookup"><span data-stu-id="1e276-133">Use the **Show** dropdown list to select **Show attribute name and value**, and verify that the list of itemsets is filtered correctly.</span></span>  
  
 <span data-ttu-id="1e276-134">**显示**</span><span class="sxs-lookup"><span data-stu-id="1e276-134">**Show**</span></span>  
 <span data-ttu-id="1e276-135">调整规则在查看器中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="1e276-135">Adjust the way that the rule is displayed in the viewer.</span></span> <span data-ttu-id="1e276-136">可以选择以下三个选项之一：</span><span class="sxs-lookup"><span data-stu-id="1e276-136">You can select one of the three following options:</span></span>  
  
-   <span data-ttu-id="1e276-137">显示属性名称和值</span><span class="sxs-lookup"><span data-stu-id="1e276-137">Show the attribute name and value</span></span>  
  
-   <span data-ttu-id="1e276-138">仅显示属性值</span><span class="sxs-lookup"><span data-stu-id="1e276-138">Show the attribute value only</span></span>  
  
-   <span data-ttu-id="1e276-139">仅显示属性名称</span><span class="sxs-lookup"><span data-stu-id="1e276-139">Show the attribute name only</span></span>  
  
 <span data-ttu-id="1e276-140">**“显示长名称”**</span><span class="sxs-lookup"><span data-stu-id="1e276-140">**Show long name**</span></span>  
 <span data-ttu-id="1e276-141">当规则显示在挖掘模型内容中时显示其全名。</span><span class="sxs-lookup"><span data-stu-id="1e276-141">Show the full name of the rule as it appears in the mining model content.</span></span>  
  
 <span data-ttu-id="1e276-142">**最大行数**</span><span class="sxs-lookup"><span data-stu-id="1e276-142">**Maximum rows**</span></span>  
 <span data-ttu-id="1e276-143">限制查看器中显示的规则数。</span><span class="sxs-lookup"><span data-stu-id="1e276-143">Limit the number of rules that are displayed in the viewer.</span></span>  
  
 <span data-ttu-id="1e276-144">**概率**</span><span class="sxs-lookup"><span data-stu-id="1e276-144">**Probability**</span></span>  
 <span data-ttu-id="1e276-145">此列将在图表中显示每个规则的概率。</span><span class="sxs-lookup"><span data-stu-id="1e276-145">This column in the chart displays the probability for each rule.</span></span>  
  
 <span data-ttu-id="1e276-146">可以单击列标题来按概率进行排序。</span><span class="sxs-lookup"><span data-stu-id="1e276-146">You can click the column heading to sort by probability.</span></span>  
  
 <span data-ttu-id="1e276-147">**重要性**</span><span class="sxs-lookup"><span data-stu-id="1e276-147">**Importance**</span></span>  
 <span data-ttu-id="1e276-148">此列将在图表中显示每个规则的重要性。</span><span class="sxs-lookup"><span data-stu-id="1e276-148">This column in the chart displays the importance for each rule.</span></span>  
  
 <span data-ttu-id="1e276-149">可以单击列标题来按重要性进行排序。</span><span class="sxs-lookup"><span data-stu-id="1e276-149">You can click the column heading to sort by importance.</span></span>  
  
 <span data-ttu-id="1e276-150">**规则**</span><span class="sxs-lookup"><span data-stu-id="1e276-150">**Rule**</span></span>  
 <span data-ttu-id="1e276-151">此列将在图表中显示每个规则的文本说明，具体取决于使用选项“显示”和“显示长名称”指定的格式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1e276-151">This column in the chart displays the text description for each rule, according to the format specified by using the options, **Show** and **Show long name**.</span></span>  
  
 <span data-ttu-id="1e276-152">可以单击列标题来按规则的文本进行排序。</span><span class="sxs-lookup"><span data-stu-id="1e276-152">You can click the column heading to sort by the text of the rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e276-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e276-153">See Also</span></span>  
 <span data-ttu-id="1e276-154">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="1e276-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="1e276-155">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="1e276-155">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="1e276-156">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="1e276-156">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
