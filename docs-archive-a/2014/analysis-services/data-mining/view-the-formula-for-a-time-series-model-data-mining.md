---
title: 查看时序模型的公式 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
ms.openlocfilehash: eff61c469d34f084e6a0eb11c49a1c37c7cc97c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577068"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a><span data-ttu-id="f4b4d-102">查看时序模型的公式（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="f4b4d-102">View the Formula for a Time Series Model (Data Mining)</span></span>
  <span data-ttu-id="f4b4d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]时序查看器 InData 挖掘设计器提供最简单的方法来查看时序模型中使用的回归公式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series viewer inData Mining Designer provides the easiest way to view the details of the regression equation used in a time series model.</span></span>  
  
 <span data-ttu-id="f4b4d-104">通过查询模型内容可以提取时序模型的回归公式。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-104">You can extract the regression formula for a time series model by querying the model content.</span></span> <span data-ttu-id="f4b4d-105">但是，若要查看完整的 ARTXP 或 ARIMA 公式，建议使用[Microsoft 时序查看器](browse-a-model-using-the-microsoft-time-series-viewer.md)的 "**挖掘图例**"，该图例以可读格式显示所有常量。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-105">However, to view the complete ARTXP or ARIMA formula, we recommend that you use the **Mining Legend** of the [Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md), which presents all the constants in a readable format.</span></span>  
  
 <span data-ttu-id="f4b4d-106">如果创建混合模型，则会在单独的树中创建 ARIMA 和 ARTXP 分析，并且在表示模型的根节点处联接。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-106">If you create a mixed model, the ARIMA and ARTXP analyses are created in separate trees, joined at the root node representing the model.</span></span> <span data-ttu-id="f4b4d-107">RIMA 和 ARTXP 树的结构差异很大。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-107">The structures of the ARIMA and ARTXP trees are very different.</span></span> <span data-ttu-id="f4b4d-108">例如，ARTXP 树实际上是一种树结构，类似决策树，而 ARIMA 树则表示一系列移动平均值。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-108">For example, the ARTXP tree is in fact a tree structure, like a decision tree, whereas the ARIMA tree represents a series of moving averages.</span></span> <span data-ttu-id="f4b4d-109">因此，尽管为方便起见而在一个模型中提供这两种表示形式，但应将它们视为两个独立的模型。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-109">Therefore, although the two representations are presented in one model for convenience, they should be treated as two independent models.</span></span> <span data-ttu-id="f4b4d-110">它们的公式也是完全不同的，因此不能进行组合或比较。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-110">The equations are also completely different and cannot be combined or compared.</span></span>  
  
 <span data-ttu-id="f4b4d-111">你还可以使用[Microsoft 一般内容树查看器](../microsoft-generic-content-tree-viewer-data-mining.md)查看时序模型。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-111">You can also view time series models by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="f4b4d-112">有关时序模型内容的详细信息，请参阅时序模型的[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-112">For more information about the content of a time series model, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a><span data-ttu-id="f4b4d-113">查看时序模型的 ARTXP 回归公式</span><span class="sxs-lookup"><span data-stu-id="f4b4d-113">To view the ARTXP regression formula for a time series model</span></span>  
  
1.  <span data-ttu-id="f4b4d-114">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，选择要查看的时序模型，然后单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-114">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="f4b4d-115">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f4b4d-115">-- or --</span></span>  
  
     <span data-ttu-id="f4b4d-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，选择该时序模型，然后单击 **“挖掘模型查看器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="f4b4d-117">单击“模型”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-117">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="f4b4d-118">如果模型包含多个树，请从“树”\*\*\*\* 下拉列表中选择一个树。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-118">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4b4d-119">您有多个数据序列时，模型将始终包含多个树。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-119">A model will always have multiple trees if you have more than one data series.</span></span> <span data-ttu-id="f4b4d-120">但是，您在 **“时序查看器”** 中看到的树的数目却不像在 [Microsoft 一般内容树查看器](../microsoft-generic-content-tree-viewer-data-mining.md)中所看到的那么多。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-120">However, you will not see as many trees in the **Time Series viewer** as you will see in the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="f4b4d-121">这是因为时序查看器会将每个数据序列的 ARIMA 和 ARTXP 信息结合到单个表示形式中。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-121">That is because the Time Series viewer combines the ARIMA and ARTXP information for each data series into a single representation.</span></span>  
  
4.  <span data-ttu-id="f4b4d-122">单击树中的任一叶节点。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-122">Click any leaf node in the tree.</span></span>  
  
     <span data-ttu-id="f4b4d-123">标记为 **“数据序列”** 的节点始终为叶节点并且可包含公式。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-123">Nodes that are labeled as **Data Series** are always leaf nodes and can contain an equation.</span></span> <span data-ttu-id="f4b4d-124">如果“(全部)”\*\*\*\* 节点没有子节点，则它也可包含一个公式。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-124">If an **(All)** node has no child nodes, it can also contain an equation.</span></span>  
  
5.  <span data-ttu-id="f4b4d-125">如果未显示“挖掘图例”\*\*\*\*，请右键单击该节点，然后选择“显示图例”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-125">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="f4b4d-126">ARTXP 公式将在 **“挖掘图例”** 的前半部分显示为 **“树节点公式”**。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-126">The ARTXP formula is displayed in the first half of the **Mining Legend**, as the **Tree node equation**.</span></span>  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a><span data-ttu-id="f4b4d-127">查看时序模型的 ARIMA 公式</span><span class="sxs-lookup"><span data-stu-id="f4b4d-127">To view the ARIMA formula for a time series model</span></span>  
  
1.  <span data-ttu-id="f4b4d-128">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，选择要查看的时序模型，然后单击 **“浏览”**。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="f4b4d-129">- 或 -</span><span class="sxs-lookup"><span data-stu-id="f4b4d-129">-- or --</span></span>  
  
     <span data-ttu-id="f4b4d-130">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，选择该时序模型，然后单击 **“挖掘模型查看器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-130">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="f4b4d-131">单击“模型”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-131">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="f4b4d-132">如果模型包含多个树，请从“树”\*\*\*\* 下拉列表中选择一个树。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-132">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4b4d-133">当有多个数据序列时，模型将始终包含多个树。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-133">The model will always have multiple trees if you include more than one data series.</span></span>  
  
4.  <span data-ttu-id="f4b4d-134">单击树中的任一叶节点。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-134">Click any node in the tree.</span></span>  
  
     <span data-ttu-id="f4b4d-135">ARIMA 公式将在 **“挖掘图例”** 的后半部分显示为 **“ARIMA 公式”**。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-135">The ARIMA formula is displayed in the second half of the **Mining Legend**, as the **ARIMA equation**.</span></span>  
  
5.  <span data-ttu-id="f4b4d-136">如果未显示“挖掘图例”\*\*\*\*，请右键单击该节点，然后选择“显示图例”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4b4d-136">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b4d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4b4d-137">See Also</span></span>  
 <span data-ttu-id="f4b4d-138">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="f4b4d-138">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="f4b4d-139">[使用 Microsoft 时序查看器浏览模型](browse-a-model-using-the-microsoft-time-series-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="f4b4d-139">[Browse a Model Using the Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md) </span></span>  
 [<span data-ttu-id="f4b4d-140">时序模型查询示例</span><span class="sxs-lookup"><span data-stu-id="f4b4d-140">Time Series Model Query Examples</span></span>](time-series-model-query-examples.md)  
  
  
