---
title: 使用 Microsoft Naive Bayes 查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discrimination [Analysis Services]
- naive bayes model [Analysis Services]
- Bayesian classifiers
- mining model content, viewing
- predictive modeling [Analysis Services]
- Naive Bayes Viewer [Analysis Services]
- data mining [Analysis Services], predictive modeling
- Microsoft Naive Bayes Viewer
- histograms [Analysis Services]
- mining models [Analysis Services], predictive modeling
- dependencies [Analysis Services]
ms.assetid: 19743095-63c1-4486-8c1d-2efc143243be
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03469e73d82a389426f91d8757630f50fe78fc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591683"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a><span data-ttu-id="476bd-102">使用 Microsoft Naive Bayes 查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="476bd-102">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>
  <span data-ttu-id="476bd-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的 Naive Bayes 查看器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 显示通过 Naive Bayes 算法生成的挖掘模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="476bd-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="476bd-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法是一种非常适合于针对预测性建模任务进行改编的分类算法。</span><span class="sxs-lookup"><span data-stu-id="476bd-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm that is highly adaptable to predictive modeling tasks.</span></span> <span data-ttu-id="476bd-105">有关此算法的详细信息，请参阅 [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="476bd-105">For more information about this algorithm, see [Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="476bd-106">由于 Naive Bayes 模型的主要用途之一是提供一种快速浏览数据集内数据的方法，因此， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器提供了多种方法来显示可预测属性与输入属性之间的交互。</span><span class="sxs-lookup"><span data-stu-id="476bd-106">Because one of the main purposes of a naive Bayes model is to provide a way to quickly explore the data in a dataset, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides several methods for displaying the interaction between predictable attributes and input attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="476bd-107">如果您想要查看有关模型中使用的公式以及所发现的模式的详细信息，可切换到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="476bd-107">If you want to view detailed information about the equations used in the model and the patterns that were discovered, you can switch to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="476bd-108">有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="476bd-108">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="476bd-109">查看器选项卡</span><span class="sxs-lookup"><span data-stu-id="476bd-109">Viewer Tabs</span></span>  
 <span data-ttu-id="476bd-110">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="476bd-110">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="476bd-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器提供了以下用于浏览数据的选项卡：</span><span class="sxs-lookup"><span data-stu-id="476bd-111">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for exploring data:</span></span>  
  
-   [<span data-ttu-id="476bd-112">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="476bd-112">Dependency Network</span></span>](#BKMK_Dependency)  
  
-   [<span data-ttu-id="476bd-113">属性配置文件</span><span class="sxs-lookup"><span data-stu-id="476bd-113">Attribute Profiles</span></span>](#BKMK_Profiles)  
  
-   [<span data-ttu-id="476bd-114">属性特征</span><span class="sxs-lookup"><span data-stu-id="476bd-114">Attribute Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="476bd-115">属性对比</span><span class="sxs-lookup"><span data-stu-id="476bd-115">Attribute Discrimination</span></span>](#BKMK_Discrimination)  
  
##  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="476bd-116">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="476bd-116">Dependency Network</span></span>  
 <span data-ttu-id="476bd-117">**“依赖关系网络”** 选项卡显示模型中的输入属性与可预测属性之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="476bd-117">The **Dependency Network** tab displays the dependencies between the input attributes and the predictable attributes in a model.</span></span> <span data-ttu-id="476bd-118">查看器左侧的滑块可起到与依赖关系强度相联系的筛选器的作用。</span><span class="sxs-lookup"><span data-stu-id="476bd-118">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="476bd-119">降低滑块将只显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="476bd-119">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="476bd-120">选择一个节点后，查看器将突出显示该节点特定的依赖项。</span><span class="sxs-lookup"><span data-stu-id="476bd-120">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="476bd-121">例如，如果选择一个可预测节点，查看器也将突出显示有助于预测该可预测节点的各个节点。</span><span class="sxs-lookup"><span data-stu-id="476bd-121">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="476bd-122">查看器底部的图例说明了图表中不同颜色代码所代表的依赖关系类型。</span><span class="sxs-lookup"><span data-stu-id="476bd-122">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="476bd-123">例如，如果选择一个可预测节点，该节点将呈青绿色，而预测所选节点的节点呈橙色。</span><span class="sxs-lookup"><span data-stu-id="476bd-123">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="476bd-124">返回页首</span><span class="sxs-lookup"><span data-stu-id="476bd-124">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-profiles"></a><a name="BKMK_Profiles"></a><span data-ttu-id="476bd-125">属性配置文件</span><span class="sxs-lookup"><span data-stu-id="476bd-125">Attribute Profiles</span></span>  
 <span data-ttu-id="476bd-126">**“属性配置文件”** 选项卡在网格中显示直方图。</span><span class="sxs-lookup"><span data-stu-id="476bd-126">The **Attribute Profiles** tab displays histograms in a grid.</span></span> <span data-ttu-id="476bd-127">可以使用此网格将在 **“可预测”** 框中选择的可预测属性与模型中的所有其他属性进行比较。</span><span class="sxs-lookup"><span data-stu-id="476bd-127">You can use this grid to compare the predictable attribute that you select in the **Predictable** box to all other attributes that are in the model.</span></span> <span data-ttu-id="476bd-128">该选项卡中的每一列表示可预测属性的一种状态。</span><span class="sxs-lookup"><span data-stu-id="476bd-128">Each column in the tab represents a state of the predictable attribute.</span></span> <span data-ttu-id="476bd-129">如果可预测属性有很多状态，则可以通过调整 **“直方图条”** 来更改直方图中显示的状态数。</span><span class="sxs-lookup"><span data-stu-id="476bd-129">If the predictable attribute has many states, you can change the number of states that appear in the histogram by adjusting the **Histogram bars**.</span></span> <span data-ttu-id="476bd-130">如果选择的数字小于属性的状态总数，则这些状态按支持顺序列出，且剩余状态收集到一个灰色存储桶中。</span><span class="sxs-lookup"><span data-stu-id="476bd-130">If the number you choose is less than the total number of states in the attribute, the states are listed in order of support, with the remaining states collected into a single gray bucket.</span></span>  
  
 <span data-ttu-id="476bd-131">若要显示一个将直方图的颜色关联到属性状态的挖掘图例，请单击 **“显示图例”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="476bd-131">To display a Mining Legend that relates the colors of the histogram to the states of an attribute, click the **Show Legend** check box.</span></span> <span data-ttu-id="476bd-132">该挖掘图例还显示所选择的每个属性-值对的事例分布情况。</span><span class="sxs-lookup"><span data-stu-id="476bd-132">The Mining Legend also displays the distribution of cases for each attribute-value pair that you select.</span></span>  
  
 <span data-ttu-id="476bd-133">若要将网格内容作为 HTML 表复制到剪贴板，请右键单击“属性配置文件”\*\*\*\* 选项卡并选择“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="476bd-133">To copy the contents of the grid to the Clipboard as an HTML table, right-click the **Attribute Profiles** tab and select **Copy**.</span></span>  
  
 [<span data-ttu-id="476bd-134">返回页首</span><span class="sxs-lookup"><span data-stu-id="476bd-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-characteristics"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="476bd-135">属性特征</span><span class="sxs-lookup"><span data-stu-id="476bd-135">Attribute Characteristics</span></span>  
 <span data-ttu-id="476bd-136">若要使用 **“属性特征”** 选项卡，请从 **“属性”** 列表中选择一个可预测属性，然后从 **“值”** 列表中选择所选属性的状态。</span><span class="sxs-lookup"><span data-stu-id="476bd-136">To use the **Attribute Characteristics** tab, select a predictable attribute from the **Attribute** list and select a state of the selected attribute from the **Value** list.</span></span> <span data-ttu-id="476bd-137">设置这些变量时， **“属性特征”** 选项卡将显示与所选属性的选定事例相关联的属性的状态。</span><span class="sxs-lookup"><span data-stu-id="476bd-137">When you set these variables, the **Attribute Characteristics** tab displays the states of the attributes that are associated with the selected case of the selected attribute.</span></span> <span data-ttu-id="476bd-138">属性按重要性进行排序。</span><span class="sxs-lookup"><span data-stu-id="476bd-138">The attributes are sorted by importance.</span></span>  
  
 [<span data-ttu-id="476bd-139">返回页首</span><span class="sxs-lookup"><span data-stu-id="476bd-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
##  <a name="attribute-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="476bd-140">属性对比</span><span class="sxs-lookup"><span data-stu-id="476bd-140">Attribute Discrimination</span></span>  
 <span data-ttu-id="476bd-141">若要使用 **“属性对比”** 选项卡，请从 **“属性”**、 **“值 1”** 和 **“值 2”** 列表中选择一个可预测属性以及它的两个状态。</span><span class="sxs-lookup"><span data-stu-id="476bd-141">To use the **Attribute Discrimination** tab, select a predictable attribute and two of its states from the **Attribute**, **Value 1**, and **Value 2** lists.</span></span> <span data-ttu-id="476bd-142">然后， **“属性对比”** 选项卡上的网格将在列中显示以下信息：</span><span class="sxs-lookup"><span data-stu-id="476bd-142">The grid on the **Attribute Discrimination** tab then displays the following information in columns:</span></span>  
  
 <span data-ttu-id="476bd-143">**特性**</span><span class="sxs-lookup"><span data-stu-id="476bd-143">**Attribute**</span></span>  
 <span data-ttu-id="476bd-144">列出数据集内的其他属性，这些属性包含一个高度倾向于可预测属性某个状态的状态。</span><span class="sxs-lookup"><span data-stu-id="476bd-144">Lists other attributes in the dataset that contain a state that highly favors one state of the predictable attribute.</span></span>  
  
 <span data-ttu-id="476bd-145">**值**</span><span class="sxs-lookup"><span data-stu-id="476bd-145">**Values**</span></span>  
 <span data-ttu-id="476bd-146">显示“属性”\*\*\*\* 列中某属性的值。</span><span class="sxs-lookup"><span data-stu-id="476bd-146">Shows the value of the attribute in the **Attribute** column.</span></span>  
  
 <span data-ttu-id="476bd-147">**有利\<value 1>**</span><span class="sxs-lookup"><span data-stu-id="476bd-147">**Favors \<value 1>**</span></span>  
 <span data-ttu-id="476bd-148">显示一个彩色条，以指示属性值倾向于“值 1”\*\*\*\* 中显示的可预测属性值的程度。</span><span class="sxs-lookup"><span data-stu-id="476bd-148">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 1**.</span></span>  
  
 <span data-ttu-id="476bd-149">**有利\<value 2>**</span><span class="sxs-lookup"><span data-stu-id="476bd-149">**Favors \<value 2>**</span></span>  
 <span data-ttu-id="476bd-150">显示一个彩色条，以指示属性值倾向于“值 2”\*\*\*\* 中显示的可预测属性值的程度。</span><span class="sxs-lookup"><span data-stu-id="476bd-150">Shows a colored bar that indicates how strongly the attribute value favors the predictable attribute value shown in **Value 2**.</span></span>  
  
 [<span data-ttu-id="476bd-151">返回页首</span><span class="sxs-lookup"><span data-stu-id="476bd-151">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="476bd-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="476bd-152">See Also</span></span>  
 <span data-ttu-id="476bd-153">[Microsoft Naive Bayes 算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="476bd-153">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="476bd-154">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="476bd-154">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="476bd-155">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="476bd-155">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="476bd-156">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="476bd-156">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
