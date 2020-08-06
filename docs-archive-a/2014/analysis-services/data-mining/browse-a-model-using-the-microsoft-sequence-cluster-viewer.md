---
title: 使用 Microsoft 序列分类查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Sequence Cluster Viewer
- clusters [Analysis Services]
- data mining [Analysis Services], sequences
- discrimination [Analysis Services]
- mining model content, viewing
- mining models [Analysis Services], sequences
- Microsoft Sequence Cluster Viewer
- sequence [Analysis Services]
- transitions [Analysis Services]
ms.assetid: 3ada00aa-da9e-488a-9f53-c3e188f81f84
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6e2c95a08f293dad8793ba5d4367753ae2c6db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591677"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="84009-102">使用 Microsoft 序列分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="84009-102">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>
  <span data-ttu-id="84009-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的序列分类查看器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 显示用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="84009-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span> <span data-ttu-id="84009-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法是用于探析特定数据的顺序分析算法，这些数据所包含的事件可通过以下路径（又称“序列 \*\*”）联系起来。</span><span class="sxs-lookup"><span data-stu-id="84009-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm is a sequence analysis algorithm for use in exploring data that contains events that can be linked by following paths, or *sequences*.</span></span> <span data-ttu-id="84009-105">有关此算法的详细信息，请参阅 [Microsoft 顺序分析和聚类分析算法](microsoft-sequence-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="84009-105">For more information about this algorithm, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84009-106">若要查看有关模型中使用的公式以及所发现的模式的详细信息，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="84009-106">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="84009-107">有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="84009-107">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84009-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器提供了与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分类查看器类似的功能和选项。</span><span class="sxs-lookup"><span data-stu-id="84009-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer provides functionality and options that are similar to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span></span> <span data-ttu-id="84009-109">有关详细信息，请参阅 [使用 Microsoft 分类查看器浏览模型](browse-a-model-using-the-microsoft-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="84009-109">For more information, see [Browse a Model Using the Microsoft Cluster Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="84009-110">查看器选项卡</span><span class="sxs-lookup"><span data-stu-id="84009-110">Viewer Tabs</span></span>  
 <span data-ttu-id="84009-111">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="84009-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="84009-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器提供了以下选项卡，用于浏览顺序分析和聚类分析挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="84009-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer provides the following tabs for use in exploring sequence clustering mining models:</span></span>  
  
-   [<span data-ttu-id="84009-113">分类关系图</span><span class="sxs-lookup"><span data-stu-id="84009-113">Cluster Diagram</span></span>](#BKMK_Diagram)  
  
-   [<span data-ttu-id="84009-114">分类剖面图</span><span class="sxs-lookup"><span data-stu-id="84009-114">Cluster Profiles</span></span>](#BKMK_Profile)  
  
-   [<span data-ttu-id="84009-115">分类特征</span><span class="sxs-lookup"><span data-stu-id="84009-115">Cluster Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="84009-116">分类对比</span><span class="sxs-lookup"><span data-stu-id="84009-116">Cluster Discrimination</span></span>](#BKMK_Discrimination)  
  
-   [<span data-ttu-id="84009-117">分类转换</span><span class="sxs-lookup"><span data-stu-id="84009-117">Cluster Transitions</span></span>](#BKMK_Transitions)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a><span data-ttu-id="84009-118">分类关系图</span><span class="sxs-lookup"><span data-stu-id="84009-118">Cluster Diagram</span></span>  
 <span data-ttu-id="84009-119">**序列分类查看器的** “分类关系图” [!INCLUDE[msCoName](../../includes/msconame-md.md)] 选项卡可显示挖掘模型中的全部分类。</span><span class="sxs-lookup"><span data-stu-id="84009-119">The **Cluster Diagram** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="84009-120">两个分类之间连线的明暗度表示分类的相似程度。</span><span class="sxs-lookup"><span data-stu-id="84009-120">The shading of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="84009-121">如果明暗度较浅或无明暗度，则表示分类的相似程度较低。</span><span class="sxs-lookup"><span data-stu-id="84009-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="84009-122">连线的颜色越深，链接的相似性越强。</span><span class="sxs-lookup"><span data-stu-id="84009-122">As the line becomes darker, the similarity of the links becomes stronger.</span></span> <span data-ttu-id="84009-123">通过调整分类右侧的滑块，可以调整查看器显示的连线数。</span><span class="sxs-lookup"><span data-stu-id="84009-123">You can adjust how many lines the viewer shows by adjusting the slider to the right of the clusters.</span></span> <span data-ttu-id="84009-124">降低滑块将只显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="84009-124">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="84009-125">默认情况下，明暗度代表分类的总体。</span><span class="sxs-lookup"><span data-stu-id="84009-125">By default, the shade represents the population of the cluster.</span></span> <span data-ttu-id="84009-126">通过使用**ShadingVariable**和**state**选项，可以选择明暗度代表的属性和状态对。</span><span class="sxs-lookup"><span data-stu-id="84009-126">By using the **ShadingVariable** and **State** options, you can select which attribute and state pair the shading represents.</span></span> <span data-ttu-id="84009-127">明暗度越深，特定状态所对应的属性分布范围就越大。</span><span class="sxs-lookup"><span data-stu-id="84009-127">The darker the shading, the greater the attribute distribution is for a specific state.</span></span> <span data-ttu-id="84009-128">明暗度越浅，分布范围就越小。</span><span class="sxs-lookup"><span data-stu-id="84009-128">The distribution decreases as the shading gets lighter.</span></span>  
  
 <span data-ttu-id="84009-129">若要重命名某个群集，请右键单击其节点并选择“重命名群集”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84009-129">To rename a cluster, right-click its node and select **Rename Cluster**.</span></span> <span data-ttu-id="84009-130">新名称会在服务器中永久保留。</span><span class="sxs-lookup"><span data-stu-id="84009-130">The new name is persisted to the server.</span></span>  
  
 <span data-ttu-id="84009-131">若要将关系图的可见部分复制到剪贴板，请单击 **“复制图形视图”**。</span><span class="sxs-lookup"><span data-stu-id="84009-131">To copy the visible section of the diagram to the Clipboard, click **Copy Graph View**.</span></span> <span data-ttu-id="84009-132">若要复制完整的关系图，请单击 **“复制整个图形”**。</span><span class="sxs-lookup"><span data-stu-id="84009-132">To copy the complete diagram, click **Copy Entire Graph**.</span></span> <span data-ttu-id="84009-133">使用 **“放大”** 和 **“缩小”** 可以放大或缩小关系图，使用 **“缩放关系图以适应窗口”** 可以适应屏幕大小。</span><span class="sxs-lookup"><span data-stu-id="84009-133">You can also zoom in and out by using **Zoom In** and **Zoom Out**, or you can fit the diagram to the screen by using **Scale Diagram to Fit in Window**.</span></span>  
  
 [<span data-ttu-id="84009-134">返回页首</span><span class="sxs-lookup"><span data-stu-id="84009-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a><span data-ttu-id="84009-135">群集配置文件</span><span class="sxs-lookup"><span data-stu-id="84009-135">Cluster Profiles</span></span>  
 <span data-ttu-id="84009-136">**“分类剖面图”** 选项卡可以提供模型中的算法创建的分类的总体视图。</span><span class="sxs-lookup"><span data-stu-id="84009-136">The **Cluster Profile** tab provides an overall view of the clusters that the algorithm in your model creates.</span></span> <span data-ttu-id="84009-137">网格中 **“总体”** 列后的每一列都代表模型发现的分类。</span><span class="sxs-lookup"><span data-stu-id="84009-137">Each column that follows the **Population** column in the grid represents a cluster that the model discovered.</span></span> <span data-ttu-id="84009-138">\<attribute>Samples 行表示群集中存在的不同数据序列， \<attribute> 行描述了群集包含的所有项及其总体分布。</span><span class="sxs-lookup"><span data-stu-id="84009-138">The \<attribute>.samples row represents different sequences of data that exist in the cluster, and the \<attribute> row describes all the items that the cluster contains and their overall distribution.</span></span>  
  
 <span data-ttu-id="84009-139">通过“直方图条” \*\*\*\* 选项，可以控制直方图中可见的条数。</span><span class="sxs-lookup"><span data-stu-id="84009-139">The **Histogram bars** option controls the number of bars that are visible in the histogram.</span></span> <span data-ttu-id="84009-140">如果存在的图条数多于您选择显示的图条数，则会保留重要性最高的那些图条，其余图条则组合到一个灰色的存储桶内。</span><span class="sxs-lookup"><span data-stu-id="84009-140">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into a gray bucket.</span></span>  
  
 <span data-ttu-id="84009-141">您可以更改分类的默认名称，使名称更具描述性。</span><span class="sxs-lookup"><span data-stu-id="84009-141">You can change the default names of the clusters, to make the names more descriptive.</span></span> <span data-ttu-id="84009-142">右键单击群集的列标题，再选择\*\*\*\*“重命名群集”，即可重命名群集。</span><span class="sxs-lookup"><span data-stu-id="84009-142">Rename a cluster by right-clicking its column heading and selecting **Rename cluster**.</span></span> <span data-ttu-id="84009-143">可以选中 **“隐藏列”** 隐藏分类，也可以通过在查看器中拖动列来将其重新排序。</span><span class="sxs-lookup"><span data-stu-id="84009-143">You can hide clusters by selecting **Hide column**, and you can also drag columns to reorder them in the viewer.</span></span>  
  
 <span data-ttu-id="84009-144">若要打开一个窗口，以便为群集提供更大、更详细的视图，请双击“状态”\*\*\*\* 列中的任一单元格，或双击查看器中的任一直方图。</span><span class="sxs-lookup"><span data-stu-id="84009-144">To open a window that provides a larger, more detailed view of the clusters, double-click either a cell in the **States** column or a histogram in the viewer.</span></span>  
  
 [<span data-ttu-id="84009-145">返回页首</span><span class="sxs-lookup"><span data-stu-id="84009-145">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="84009-146">分类特征</span><span class="sxs-lookup"><span data-stu-id="84009-146">Cluster Characteristics</span></span>  
 <span data-ttu-id="84009-147">若要使用“分类特征” \*\*\*\* 选项卡，请从“分类” \*\*\*\* 列表中选择一个分类。</span><span class="sxs-lookup"><span data-stu-id="84009-147">To use the **Cluster Characteristics** tab, select a cluster from the **Cluster** list.</span></span> <span data-ttu-id="84009-148">选择分类后，可以检查特定分类的组成特征。</span><span class="sxs-lookup"><span data-stu-id="84009-148">After you select a cluster, you can examine the characteristics that make up that specific cluster.</span></span> <span data-ttu-id="84009-149">分类包含的属性列在 **“变量”** 列中，所列属性的状态列在 **“值”** 列中。</span><span class="sxs-lookup"><span data-stu-id="84009-149">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span> <span data-ttu-id="84009-150">属性状态将按重要性顺序列出，重要性由这些状态会出现在分类中的概率表示。</span><span class="sxs-lookup"><span data-stu-id="84009-150">Attribute states are listed in order of importance, described by the probability that they will appear in the cluster.</span></span> <span data-ttu-id="84009-151">概率显示在 **“概率”** 列中。</span><span class="sxs-lookup"><span data-stu-id="84009-151">The probability is shown in the **Probability** column.</span></span>  
  
 [<span data-ttu-id="84009-152">返回页首</span><span class="sxs-lookup"><span data-stu-id="84009-152">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="84009-153">分类对比</span><span class="sxs-lookup"><span data-stu-id="84009-153">Cluster Discrimination</span></span>  
 <span data-ttu-id="84009-154">可以使用 **“分类对比”** 选项卡来比较两个分类的属性，以确定序列中的项所倾向的分类。</span><span class="sxs-lookup"><span data-stu-id="84009-154">You can use the **Cluster Discrimination** tab to compare attributes between two clusters, to determine how items in a sequence favor one cluster over another.</span></span> <span data-ttu-id="84009-155">使用 **“分类 1”** 和 **“分类 2”** 列表选择要比较的分类。</span><span class="sxs-lookup"><span data-stu-id="84009-155">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span> <span data-ttu-id="84009-156">查看器将确定分类之间最为重要的一些差异，并按重要性顺序显示与这些差异关联的属性状态。</span><span class="sxs-lookup"><span data-stu-id="84009-156">The viewer determines the most important differences between the clusters, and displays the attribute states that are associated with the differences, in order of importance.</span></span> <span data-ttu-id="84009-157">属性右侧的条表示属性状态所倾向的分类，条的大小则表示属性状态倾向于相应分类的程度。</span><span class="sxs-lookup"><span data-stu-id="84009-157">A bar to the right of the attribute shows which cluster the state favors, and the size of the bar shows how strongly the state favors the cluster.</span></span>  
  
 [<span data-ttu-id="84009-158">返回页首</span><span class="sxs-lookup"><span data-stu-id="84009-158">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-transitions"></a><a name="BKMK_Transitions"></a><span data-ttu-id="84009-159">群集转换</span><span class="sxs-lookup"><span data-stu-id="84009-159">Cluster Transitions</span></span>  
 <span data-ttu-id="84009-160">在 **“分类转换”** 选项卡中选中一个分类后，可在选中的分类中浏览序列状态之间的转换。</span><span class="sxs-lookup"><span data-stu-id="84009-160">By selecting a cluster on the **Cluster Transitions** tab, you can browse the transitions between sequence states in the selected cluster.</span></span> <span data-ttu-id="84009-161">查看器中的每个节点代表序列列的一个状态。</span><span class="sxs-lookup"><span data-stu-id="84009-161">Each node in the viewer represents a state of the sequence column.</span></span> <span data-ttu-id="84009-162">箭头代表两个状态之间的转换以及与该转换相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="84009-162">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="84009-163">如果转换返回到初始节点，那么会有一个箭头指向该初始节点。</span><span class="sxs-lookup"><span data-stu-id="84009-163">If a transition returns back to the originating node, an arrow can point back to the originating node.</span></span>  
  
 <span data-ttu-id="84009-164">以圆点为起点的箭头代表序列从此节点处开始的概率。</span><span class="sxs-lookup"><span data-stu-id="84009-164">An arrow that originates from a dot represents the probability that the node is the start of a sequence.</span></span> <span data-ttu-id="84009-165">末端指向空值的箭头代表序列至此节点处结束的概率。</span><span class="sxs-lookup"><span data-stu-id="84009-165">An ending edge that leads to a null represents the probability that the node is the end of the sequence.</span></span>  
  
 <span data-ttu-id="84009-166">可以使用位于选项卡左侧的滑块来筛选节点边缘。</span><span class="sxs-lookup"><span data-stu-id="84009-166">You can filter the edge of the nodes by using the slider at the left of the tab.</span></span>  
  
 [<span data-ttu-id="84009-167">返回页首</span><span class="sxs-lookup"><span data-stu-id="84009-167">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="84009-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84009-168">See Also</span></span>  
 <span data-ttu-id="84009-169">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="84009-169">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="84009-170">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="84009-170">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="84009-171">[Microsoft 顺序分析和聚类分析算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="84009-171">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="84009-172">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="84009-172">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="84009-173">[数据挖掘模型查看器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="84009-173">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 [<span data-ttu-id="84009-174">使用 Microsoft 分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="84009-174">Browse a Model Using the Microsoft Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
