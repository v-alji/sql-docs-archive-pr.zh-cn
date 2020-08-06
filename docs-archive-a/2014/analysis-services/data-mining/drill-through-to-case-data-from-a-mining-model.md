---
title: 从挖掘模型钻取到事例数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74129c44fc92984a767a79c579a495084ae68754
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589960"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a><span data-ttu-id="a98a3-102">从挖掘模型钻取到事例数据</span><span class="sxs-lookup"><span data-stu-id="a98a3-102">Drill Through to Case Data from a Mining Model</span></span>
  <span data-ttu-id="a98a3-103">如果挖掘模型已配置为允许钻取到模型事例，在浏览此模型时，可以检索与用于创建此模型的事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a98a3-103">If a mining model has been configured to let you drill through to model cases, when you browse the model, you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="a98a3-104">此外，如果基础挖掘结构已配置为允许钻取到结构事例，并且您具备相应的权限，则可返回挖掘结构的信息。</span><span class="sxs-lookup"><span data-stu-id="a98a3-104">Moreover, if the underlying mining structure has been configured to allow drillthrough to structure cases, and you have the appropriate permissions, you can return information from the mining structure.</span></span> <span data-ttu-id="a98a3-105">其中可以包括挖掘模型中未包含的列。</span><span class="sxs-lookup"><span data-stu-id="a98a3-105">This can include columns that were not included in the mining model.</span></span>  
  
 <span data-ttu-id="a98a3-106">如果挖掘结构不允许钻取到基础数据，但挖掘模型允许，则可查看模型事例的信息，而无法查看挖掘结构的信息。</span><span class="sxs-lookup"><span data-stu-id="a98a3-106">If the mining structure does not allow you to drill through to the underlying data, but the mining model does, you can view information from the model cases, but not from the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a98a3-107">可以通过将 `AllowDrillthrough` 属性设置为 `True`，向现有的挖掘模型添加钻取功能。</span><span class="sxs-lookup"><span data-stu-id="a98a3-107">You can add the ability to drillthrough on an existing mining model by setting the property `AllowDrillthrough` to `True`.</span></span> <span data-ttu-id="a98a3-108">但是，在启用钻取功能之后，必须先重新处理相应的模型，然后才能查看事例数据。</span><span class="sxs-lookup"><span data-stu-id="a98a3-108">However, after you enable drillthrough, the model must be reprocessed before you can see the case data.</span></span> <span data-ttu-id="a98a3-109">有关详细信息，请参阅 [对挖掘模型启用钻取](enable-drillthrough-for-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a98a3-109">For more information, see [Enable Drillthrough for a Mining Model](enable-drillthrough-for-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="a98a3-110">根据您所使用的查看器的类型，您可以按照下面的方式选择钻取节点：</span><span class="sxs-lookup"><span data-stu-id="a98a3-110">Depending on the type of viewer you are using, you can select the node for drillthrough in the following ways:</span></span>  
  
|<span data-ttu-id="a98a3-111">查看器名称</span><span class="sxs-lookup"><span data-stu-id="a98a3-111">Viewer name</span></span>|<span data-ttu-id="a98a3-112">窗格或选项卡名称</span><span class="sxs-lookup"><span data-stu-id="a98a3-112">Pane or tab name</span></span>|<span data-ttu-id="a98a3-113">选择节点</span><span class="sxs-lookup"><span data-stu-id="a98a3-113">Select node</span></span>|  
|-----------------|----------------------|-----------------|  
|<span data-ttu-id="a98a3-114">**Microsoft 树查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-114">**Microsoft Tree Viewer**</span></span>|<span data-ttu-id="a98a3-115">**决策树**选项卡</span><span class="sxs-lookup"><span data-stu-id="a98a3-115">**Decision Tree** tab</span></span>|<span data-ttu-id="a98a3-116">单击树节点。</span><span class="sxs-lookup"><span data-stu-id="a98a3-116">Click a tree node.</span></span><br /><br /> <span data-ttu-id="a98a3-117">**注意**避免在节点上使用钻取 `All` ，因为可能需要很长时间才能返回结果。</span><span class="sxs-lookup"><span data-stu-id="a98a3-117">**Note** Avoid using drillthrough on the `All` node, because it may take a very long time to return results.</span></span>|  
|<span data-ttu-id="a98a3-118">**Microsoft 分类查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-118">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="a98a3-119">**分类关系图**</span><span class="sxs-lookup"><span data-stu-id="a98a3-119">**Cluster Diagram**</span></span>|<span data-ttu-id="a98a3-120">单击群集节点。</span><span class="sxs-lookup"><span data-stu-id="a98a3-120">Click a cluster node.</span></span>|  
|<span data-ttu-id="a98a3-121">**Microsoft 分类查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-121">**Microsoft Cluster Viewer**</span></span>|<span data-ttu-id="a98a3-122">**分类剖面图**</span><span class="sxs-lookup"><span data-stu-id="a98a3-122">**Cluster Profiles**</span></span>|<span data-ttu-id="a98a3-123">单击分类列中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="a98a3-123">Click anywhere in cluster column.</span></span>|  
|<span data-ttu-id="a98a3-124">**Microsoft 关联查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-124">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="a98a3-125">**规则**选项卡</span><span class="sxs-lookup"><span data-stu-id="a98a3-125">**Rules** tab</span></span>|<span data-ttu-id="a98a3-126">单击包含一组规则的行。</span><span class="sxs-lookup"><span data-stu-id="a98a3-126">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="a98a3-127">**Microsoft 关联查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-127">**Microsoft Association Viewer**</span></span>|<span data-ttu-id="a98a3-128">**“项集”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="a98a3-128">**Itemsets** tab</span></span>|<span data-ttu-id="a98a3-129">单击包含项集的行。</span><span class="sxs-lookup"><span data-stu-id="a98a3-129">Click a row that contains an itemset.</span></span>|  
|<span data-ttu-id="a98a3-130">**Microsoft 顺序分析和聚类分析查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-130">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="a98a3-131">**规则**选项卡</span><span class="sxs-lookup"><span data-stu-id="a98a3-131">**Rules** tab</span></span>|<span data-ttu-id="a98a3-132">单击包含一组规则的行。</span><span class="sxs-lookup"><span data-stu-id="a98a3-132">Click a row that contains a set of rules.</span></span>|  
|<span data-ttu-id="a98a3-133">**Microsoft 顺序分析和聚类分析查看器**</span><span class="sxs-lookup"><span data-stu-id="a98a3-133">**Microsoft Sequence Clustering Viewer**</span></span>|<span data-ttu-id="a98a3-134">**“项集”** 选项卡</span><span class="sxs-lookup"><span data-stu-id="a98a3-134">**Itemsets** tab</span></span>|<span data-ttu-id="a98a3-135">单击包含项集的行。</span><span class="sxs-lookup"><span data-stu-id="a98a3-135">Click a row that contains an itemset.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a98a3-136">某些模型不能使用钻取。</span><span class="sxs-lookup"><span data-stu-id="a98a3-136">Some models cannot use drillthrough.</span></span> <span data-ttu-id="a98a3-137">能否使用钻取取决于创建模型所用的算法。</span><span class="sxs-lookup"><span data-stu-id="a98a3-137">The ability to use drillthrough depends on the algorithm that was used to create the model.</span></span> <span data-ttu-id="a98a3-138">有关支持钻取功能的挖掘模型类型的列表，请参阅 [钻取查询（数据挖掘）](drillthrough-queries-data-mining.md)，向现有的挖掘模型添加钻取功能。</span><span class="sxs-lookup"><span data-stu-id="a98a3-138">For a list of the mining model types that support drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="a98a3-139">查看挖掘模型的钻取数据</span><span class="sxs-lookup"><span data-stu-id="a98a3-139">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="a98a3-140">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含想要的挖掘模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="a98a3-140">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the mining structure that contains the mining model you want.</span></span>  
  
2.  <span data-ttu-id="a98a3-141">在数据挖掘设计器中，单击 **“挖掘模型查看器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a98a3-141">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="a98a3-142">从“挖掘模型”\*\*\*\* 下拉列表中选择模型。</span><span class="sxs-lookup"><span data-stu-id="a98a3-142">Select the model from the **Mining Model** drop-down list.</span></span>  
  
4.  <span data-ttu-id="a98a3-143">从“查看器”\*\*\*\* 下拉列表中选择一个查看器，然后右键单击特定节点。</span><span class="sxs-lookup"><span data-stu-id="a98a3-143">Select a viewer from the **Viewer** drop-down list, and right-click the specific node.</span></span>  
  
5.  <span data-ttu-id="a98a3-144">选择 **“钻取”**，然后选择 **“仅限于模型列”** 或 **“模型和结构列”** 以打开 **“钻取”** 窗口。</span><span class="sxs-lookup"><span data-stu-id="a98a3-144">Select **Drill Through**, and then select either **Models Columns Only**, or **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="a98a3-145">若要将数据复制到剪贴板，请右键单击表中的任何行，并选择“全部复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a98a3-145">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98a3-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a98a3-146">See Also</span></span>  
 [<span data-ttu-id="a98a3-147">钻取查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a98a3-147">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
