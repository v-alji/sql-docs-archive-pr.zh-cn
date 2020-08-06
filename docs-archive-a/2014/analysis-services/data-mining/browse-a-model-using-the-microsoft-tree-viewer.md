---
title: 使用 Microsoft 树查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Tree Viewer [Analysis Services]
- predictions [Analysis Services], discrete attributes
- mining model content, viewing
- predictions [Analysis Services], continuous attributes
- mining legend [Analysis Services]
- discrete attributes [Analysis Services]
- Microsoft Decision Trees algorithm [Analysis Services]
- decision tree algorithms [Analysis Services]
- Microsoft Tree Viewer
- decision trees [Analysis Services]
- dependencies [Analysis Services]
- continuous attributes
ms.assetid: 0c96d518-ed20-40b7-8d62-b26ad6244287
author: minewiskan
ms.author: owend
ms.openlocfilehash: cebe1e05435fad453757b4f747ae809f379c410f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591678"
---
# <a name="browse-a-model-using-the-microsoft-tree-viewer"></a><span data-ttu-id="c64d3-102">使用 Microsoft 树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="c64d3-102">Browse a Model Using the Microsoft Tree Viewer</span></span>
  <span data-ttu-id="c64d3-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的树查看器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 显示用决策树算法生成的决策树 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c64d3-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays decision trees that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="c64d3-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法是一种既支持分类又支持回归的混合决策树算法。</span><span class="sxs-lookup"><span data-stu-id="c64d3-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is a hybrid decision tree algorithm that supports both classification and regression.</span></span> <span data-ttu-id="c64d3-105">因此，你可以使用该查看器来查看基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法的模型。</span><span class="sxs-lookup"><span data-stu-id="c64d3-105">Therefore, you can also use this viewer to view models based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="c64d3-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法用于为离散属性和连续属性进行预测性建模。</span><span class="sxs-lookup"><span data-stu-id="c64d3-106">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is used for predictive modeling of both discrete and continuous attributes.</span></span> <span data-ttu-id="c64d3-107">有关此算法的详细信息，请参阅 [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="c64d3-107">For more information about this algorithm, see [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c64d3-108">若要查看有关模型中使用的公式以及所发现的模式的详细信息，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="c64d3-108">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="c64d3-109">有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c64d3-109">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_TabsPanes"></a><span data-ttu-id="c64d3-110">查看器选项卡</span><span class="sxs-lookup"><span data-stu-id="c64d3-110">Viewer Tabs</span></span>  
 <span data-ttu-id="c64d3-111">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="c64d3-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="c64d3-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 树查看器包括以下选项卡和窗格：</span><span class="sxs-lookup"><span data-stu-id="c64d3-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer includes the following tabs and panes:</span></span>  
  
-   [<span data-ttu-id="c64d3-113">决策树</span><span class="sxs-lookup"><span data-stu-id="c64d3-113">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="c64d3-114">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="c64d3-114">Dependency Network</span></span>](#BKMK_DependencyNetwork)  
  
-   [<span data-ttu-id="c64d3-115">挖掘图例</span><span class="sxs-lookup"><span data-stu-id="c64d3-115">Mining Legend</span></span>](#BKMK_MiningLegend)  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="c64d3-116">决策树</span><span class="sxs-lookup"><span data-stu-id="c64d3-116">Decision Tree</span></span>  
 <span data-ttu-id="c64d3-117">生成决策树模型时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将为每个可预测属性生成一个单独的树。</span><span class="sxs-lookup"><span data-stu-id="c64d3-117">When you build a decision tree model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds a separate tree for each predictable attribute.</span></span> <span data-ttu-id="c64d3-118">从查看器的 **“决策树”** 选项卡上的 **“树”** 列表中选择单个树，可查看该树。</span><span class="sxs-lookup"><span data-stu-id="c64d3-118">You can view an individual tree by selecting it from the **Tree** list on the **Decision Tree** tab of the viewer.</span></span>  
  
 <span data-ttu-id="c64d3-119">决策树由一系列拆分组成，最重要的拆分由算法确定，该拆分位于 **“全部”** 节点中查看器的左侧。</span><span class="sxs-lookup"><span data-stu-id="c64d3-119">A decision tree is composed of a series of splits, with the most important split, as determined by the algorithm, at the left of the viewer in the **All** node.</span></span> <span data-ttu-id="c64d3-120">其他拆分出现在右侧。</span><span class="sxs-lookup"><span data-stu-id="c64d3-120">Additional splits occur to the right.</span></span> <span data-ttu-id="c64d3-121">“全部”\*\*\*\* 节点中的拆分最为重要，由于该节点包含了数据集内引起拆分的最充分的条件，因而产生了第一个拆分。</span><span class="sxs-lookup"><span data-stu-id="c64d3-121">The split in the **All** node is most important because it contains the strongest split-causing conditional in the dataset, and therefore it caused the first split.</span></span>  
  
 <span data-ttu-id="c64d3-122">您可以展开或折叠决策树中的各个节点，以显示或隐藏各节点后出现的拆分。</span><span class="sxs-lookup"><span data-stu-id="c64d3-122">You can expand or collapse individual nodes in the tree to show or hide the splits that occur after each node.</span></span> <span data-ttu-id="c64d3-123">您还可以使用 **“决策树”** 选项卡上的选项来设置树的显示方式。</span><span class="sxs-lookup"><span data-stu-id="c64d3-123">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed.</span></span> <span data-ttu-id="c64d3-124">使用 **“显示级别”** 滑块，可以调整树中显示的级别数。</span><span class="sxs-lookup"><span data-stu-id="c64d3-124">Use the **Show Level** slider to adjust the number of levels that are shown in the tree.</span></span> <span data-ttu-id="c64d3-125">使用 **“默认扩展”** 可以设置模型中所有树的默认显示级别数。</span><span class="sxs-lookup"><span data-stu-id="c64d3-125">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
#### <a name="predicting-discrete-attributes"></a><span data-ttu-id="c64d3-126">预测离散属性</span><span class="sxs-lookup"><span data-stu-id="c64d3-126">Predicting Discrete Attributes</span></span>  
 <span data-ttu-id="c64d3-127">如果树是使用离散可预测属性生成的，则查看器将在树的每个节点上显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="c64d3-127">When a tree is built with a discrete predictable attribute, the viewer displays the following on each node in the tree:</span></span>  
  
-   <span data-ttu-id="c64d3-128">导致拆分的条件。</span><span class="sxs-lookup"><span data-stu-id="c64d3-128">The condition that caused the split.</span></span>  
  
-   <span data-ttu-id="c64d3-129">表示可预测属性的状态分布情况的直方图，其中各个状态按使用频率高低进行排列。</span><span class="sxs-lookup"><span data-stu-id="c64d3-129">A histogram that represents the distribution of the states of the predictable attribute, ordered by popularity.</span></span>  
  
 <span data-ttu-id="c64d3-130">可以使用 **“直方图”** 选项来更改在树的直方图中显示的状态数。</span><span class="sxs-lookup"><span data-stu-id="c64d3-130">You can use the **Histogram** option to change the number of states that appear in the histograms in the tree.</span></span> <span data-ttu-id="c64d3-131">如果可预测属性有很多状态，这一功能将非常有用。</span><span class="sxs-lookup"><span data-stu-id="c64d3-131">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="c64d3-132">各种状态按使用频率高低自左到右显示在直方图中；如果选择显示的状态数少于属性的状态总数，则使用频率最低的状态将集中以灰色显示。</span><span class="sxs-lookup"><span data-stu-id="c64d3-132">The states appear in a histogram in order of popularity from left to right; if the number of states that you choose to display is fewer than the total number of states in the attribute, the least popular states are displayed collectively in gray.</span></span> <span data-ttu-id="c64d3-133">若要查看某个节点的各种状态的确切数目，可以将指针停留在该节点上来查看 InfoTip（信息提示），也可以选择该节点以便在 **“挖掘图例”** 中查看其详细信息。</span><span class="sxs-lookup"><span data-stu-id="c64d3-133">To see the exact count for each state for a node, pause the pointer over the node to view an InfoTip, or select the node to view its details in the **Mining Legend**.</span></span>  
  
 <span data-ttu-id="c64d3-134">如果使用 **“后台”** 选项选择了特定属性状态，则各个节点的背景色将表示处于所选状态的事例的密集程度。</span><span class="sxs-lookup"><span data-stu-id="c64d3-134">The background color of each node represents the concentration of cases of the particular attribute state that you select by using the **Background** option.</span></span> <span data-ttu-id="c64d3-135">可以使用此选项来突出显示包含所关注的特定目标的节点。</span><span class="sxs-lookup"><span data-stu-id="c64d3-135">You can use this option to highlight nodes that contain a particular target in which you are interested.</span></span>  
  
#### <a name="predicting-continuous-attributes"></a><span data-ttu-id="c64d3-136">预测连续属性</span><span class="sxs-lookup"><span data-stu-id="c64d3-136">Predicting Continuous Attributes</span></span>  
 <span data-ttu-id="c64d3-137">如果树是使用连续可预测属性生成的，则查看器为树中的每个节点显示一个菱形图，而不是直方图。</span><span class="sxs-lookup"><span data-stu-id="c64d3-137">When a tree is built with a continuous predictable attribute, the viewer displays a diamond chart, instead of a histogram, for each node in the tree.</span></span> <span data-ttu-id="c64d3-138">菱形图有一个表示属性范围的线条。</span><span class="sxs-lookup"><span data-stu-id="c64d3-138">The diamond chart has a line that represents the range of the attribute.</span></span> <span data-ttu-id="c64d3-139">菱形位于节点的中间，其宽度表示该节点处属性的方差。</span><span class="sxs-lookup"><span data-stu-id="c64d3-139">The diamond is located at the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="c64d3-140">菱形越窄，说明该节点生成的预测更为精确。</span><span class="sxs-lookup"><span data-stu-id="c64d3-140">A thinner diamond indicates that the node can create a more accurate prediction.</span></span> <span data-ttu-id="c64d3-141">查看器还显示用于确定节点中的拆分的回归公式。</span><span class="sxs-lookup"><span data-stu-id="c64d3-141">The viewer also displays the regression equation, which is used to determine the split in the node.</span></span>  
  
#### <a name="additional-decision-tree-display-options"></a><span data-ttu-id="c64d3-142">其他决策树显示选项</span><span class="sxs-lookup"><span data-stu-id="c64d3-142">Additional Decision Tree Display Options</span></span>  
 <span data-ttu-id="c64d3-143">为决策树模型启用钻取后，即可访问支持某个节点的定型事例，方法是：右键单击树中的该节点，然后选择“钻取”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c64d3-143">When drill through is enabled for a decision tree model, you can access the training cases that support a node by right-clicking the node in the tree and selecting **Drill Through**.</span></span> <span data-ttu-id="c64d3-144">可以在数据挖掘向导内启用钻取，也可以在 **“挖掘模型”** 选项卡中通过调整挖掘模型的钻取属性来启用钻取。</span><span class="sxs-lookup"><span data-stu-id="c64d3-144">You can enable drill through within the Data Mining Wizard, or by adjusting the drill through property on the mining model in the **Mining Models** tab.</span></span>  
  
 <span data-ttu-id="c64d3-145">可以使用 **“决策树”** 选项卡上的缩放选项来放大或缩小某个树，也可以使用 **“调整为合适大小”** 将整个模型放入查看器的屏幕中。</span><span class="sxs-lookup"><span data-stu-id="c64d3-145">You can use the zoom options on the **Decision Tree** tab to zoom in or out of a tree, or use **Size to Fit** to fit the whole model in the viewer screen.</span></span> <span data-ttu-id="c64d3-146">如果某个树太大而无法将其调整为适合屏幕的大小，则可使用“导航” \*\*\*\* 选项在树中导航。</span><span class="sxs-lookup"><span data-stu-id="c64d3-146">If a tree is too large to be sized to fit the screen, you can use the **Navigation**option to navigate through the tree.</span></span> <span data-ttu-id="c64d3-147">单击 **“导航”** 将打开一个单独的导航窗口，可通过它来选择要显示的模型部分。</span><span class="sxs-lookup"><span data-stu-id="c64d3-147">Clicking **Navigation** opens a separate navigation window that you can use to select sections of the model to display.</span></span>  
  
 <span data-ttu-id="c64d3-148">您还可以将树视图图像复制到剪贴板上，以便可将其粘贴到文档或图像处理软件中。</span><span class="sxs-lookup"><span data-stu-id="c64d3-148">You can also copy the tree view image to the Clipboard, so that you can paste it into documents or into image manipulation software.</span></span> <span data-ttu-id="c64d3-149">可以使用 **“复制图形视图”** 仅复制查看器中树的可见部分，也可以使用 **“复制整个图形”** 来复制树中所有扩展节点。</span><span class="sxs-lookup"><span data-stu-id="c64d3-149">Use **Copy Graph View** to copy only the section of the tree that is visible in the viewer, or use **Copy Entire Graph** to copy all the expanded nodes in the tree.</span></span>  
  
 [<span data-ttu-id="c64d3-150">返回页首</span><span class="sxs-lookup"><span data-stu-id="c64d3-150">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="dependency-network"></a><a name="BKMK_DependencyNetwork"></a><span data-ttu-id="c64d3-151">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="c64d3-151">Dependency Network</span></span>  
 <span data-ttu-id="c64d3-152">**“依赖关系网络”** 显示了模型中的输入属性和可预测属性之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="c64d3-152">The **Dependency Network** displays the dependencies between the input attributes and the predictable attributes in the model.</span></span> <span data-ttu-id="c64d3-153">查看器左侧的滑块可起到与依赖关系强度相联系的筛选器的作用。</span><span class="sxs-lookup"><span data-stu-id="c64d3-153">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="c64d3-154">如果向下拉动滑块，则查看器中只会显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="c64d3-154">If you lower the slider, only the strongest links are shown in the viewer.</span></span>  
  
 <span data-ttu-id="c64d3-155">选择一个节点后，查看器将突出显示该节点特定的依赖项。</span><span class="sxs-lookup"><span data-stu-id="c64d3-155">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="c64d3-156">例如，如果选择一个可预测节点，查看器也将突出显示有助于预测该可预测节点的各个节点。</span><span class="sxs-lookup"><span data-stu-id="c64d3-156">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="c64d3-157">如果查看器包含大量的节点，则可使用 **“查找节点”** 按钮来搜索特定的节点。</span><span class="sxs-lookup"><span data-stu-id="c64d3-157">If the viewer contains numerous nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="c64d3-158">单击 **“查找节点”** 将打开 **“查找节点”** 对话框，可以在该对话框中使用筛选器来搜索和选择特定的节点。</span><span class="sxs-lookup"><span data-stu-id="c64d3-158">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
 <span data-ttu-id="c64d3-159">查看器底部的图例说明了图表中不同颜色代码所代表的依赖关系类型。</span><span class="sxs-lookup"><span data-stu-id="c64d3-159">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="c64d3-160">例如，如果选择一个可预测节点，该节点将呈青绿色，而预测所选节点的节点呈橙色。</span><span class="sxs-lookup"><span data-stu-id="c64d3-160">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="c64d3-161">返回页首</span><span class="sxs-lookup"><span data-stu-id="c64d3-161">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="mining-legend"></a><a name="BKMK_MiningLegend"></a><span data-ttu-id="c64d3-162">挖掘图例</span><span class="sxs-lookup"><span data-stu-id="c64d3-162">Mining Legend</span></span>  
 <span data-ttu-id="c64d3-163">在选中决策树模型中的某个节点时， **“挖掘图例”** 显示下列信息：</span><span class="sxs-lookup"><span data-stu-id="c64d3-163">The **Mining Legend** displays the following information when you select a node in the decision tree model:</span></span>  
  
-   <span data-ttu-id="c64d3-164">节点中按可预测属性的状态划分的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="c64d3-164">The number of cases in the node, broken down by the states of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="c64d3-165">节点的可预测属性的各种事例的概率。</span><span class="sxs-lookup"><span data-stu-id="c64d3-165">The probability of each case of the predictable attribute for the node.</span></span>  
  
-   <span data-ttu-id="c64d3-166">一个直方图，其中包含可预测属性的各种状态的数目。</span><span class="sxs-lookup"><span data-stu-id="c64d3-166">A histogram that includes a count for each state of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="c64d3-167">访问某个特定节点所需的条件，也称为“节点路径 \*\*”。</span><span class="sxs-lookup"><span data-stu-id="c64d3-167">The conditions that are required to reach a specific node, also known as the *node path*.</span></span>  
  
-   <span data-ttu-id="c64d3-168">回归公式（对于线性回归模型）</span><span class="sxs-lookup"><span data-stu-id="c64d3-168">For linear regression models, the regression formula.</span></span>  
  
 <span data-ttu-id="c64d3-169">停靠和使用 **“挖掘图例”** 的方式与解决方案资源管理器的使用方式类似。</span><span class="sxs-lookup"><span data-stu-id="c64d3-169">You can dock and work with the **Mining Legend** in a similar manner as with Solution Explorer.</span></span>  
  
 [<span data-ttu-id="c64d3-170">返回页首</span><span class="sxs-lookup"><span data-stu-id="c64d3-170">Back to Top</span></span>](#BKMK_TabsPanes)  
  
## <a name="see-also"></a><span data-ttu-id="c64d3-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c64d3-171">See Also</span></span>  
 <span data-ttu-id="c64d3-172">[Microsoft 决策树算法](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c64d3-172">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="c64d3-173">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](../mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c64d3-173">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](../mining-model-viewers-data-mining-model-designer.md) </span></span>  
 <span data-ttu-id="c64d3-174">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="c64d3-174">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="c64d3-175">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c64d3-175">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="c64d3-176">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="c64d3-176">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
