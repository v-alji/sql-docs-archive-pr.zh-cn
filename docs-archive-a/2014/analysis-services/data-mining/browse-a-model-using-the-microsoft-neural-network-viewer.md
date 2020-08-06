---
title: 使用 Microsoft 神经网络查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 77e08955d09b7995e34ac94b75f809a303ca0d2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591680"
---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a><span data-ttu-id="b317e-102">使用 Microsoft 神经网络查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="b317e-102">Browse a Model Using the Microsoft Neural Network Viewer</span></span>
  <span data-ttu-id="b317e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的神经网络查看器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 显示用神经网络算法生成的挖掘模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b317e-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="b317e-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法创建可分析多个输入和输出的分类和回归挖掘模型，它对于开放的分析和浏览十分有用。</span><span class="sxs-lookup"><span data-stu-id="b317e-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates classification and regression mining models that can analyze multiple inputs and outputs, and is very useful for open-ended analyses and exploration.</span></span> <span data-ttu-id="b317e-105">有关此算法的详细信息，请参阅 [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="b317e-105">For more information about this algorithm, see [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md).</span></span>  
  
 <span data-ttu-id="b317e-106">在您使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络查看器浏览某一模型时，通常会选择某个目标属性和状态，然后使用该查看器来查看输入属性是如何影响结果的。</span><span class="sxs-lookup"><span data-stu-id="b317e-106">When you explore a model using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer, you typically pick some target attribute and state, and then use the viewer to see how input attributes affect the outcome</span></span>  
  
 <span data-ttu-id="b317e-107">例如，假设您知道与某一类别的潜在客户相关的以下事实：</span><span class="sxs-lookup"><span data-stu-id="b317e-107">For example, suppose you know these facts about a class of potential customers:</span></span>  
  
-   <span data-ttu-id="b317e-108">中年人（40 至 50 岁）。</span><span class="sxs-lookup"><span data-stu-id="b317e-108">Middle aged (40 to 50 years old).</span></span>  
  
-   <span data-ttu-id="b317e-109">拥有一套住房。</span><span class="sxs-lookup"><span data-stu-id="b317e-109">Owns a home.</span></span>  
  
-   <span data-ttu-id="b317e-110">有两个孩子仍住在家中。</span><span class="sxs-lookup"><span data-stu-id="b317e-110">Has two children who still live at home.</span></span>  
  
 <span data-ttu-id="b317e-111">如何将这些属性与客户将进行购买的可能性相关联？</span><span class="sxs-lookup"><span data-stu-id="b317e-111">How can you correlate these attributes with the likelihood that the customer will make a purchase?</span></span>  
  
 <span data-ttu-id="b317e-112">通过将购买行为用作目标结果来生成一个神经网络模型，您可以浏览针对客户属性（例如高收入）的多个组合，并且发现哪一属性组合最有可能影响购买行为。</span><span class="sxs-lookup"><span data-stu-id="b317e-112">By building a neural network model using purchasing behavior as the target outcome, you can explore multiple combinations on customer attributes, such as high income, and discover which combination of attributes is most likely to influence purchasing behavior.</span></span> <span data-ttu-id="b317e-113">例如，您可能会发现决定因素是到工作单位的距离。</span><span class="sxs-lookup"><span data-stu-id="b317e-113">For example, you might discover that the determining factor is the distance that they commute to work.</span></span>  
  
 <span data-ttu-id="b317e-114">如果您需要更详细的视图信息，例如表示已发现的每个模式的方程式，则可以切换视图并且使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="b317e-114">If you need to more view detailed information, such as the equations that represent each pattern that was discovered, you can switch views and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="b317e-115">有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b317e-115">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="b317e-116">查看器选项卡</span><span class="sxs-lookup"><span data-stu-id="b317e-116">Viewer Tabs</span></span>  
 <span data-ttu-id="b317e-117">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="b317e-117">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="b317e-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络查看器提供以下用于浏览神经网络挖掘模型的选项卡：</span><span class="sxs-lookup"><span data-stu-id="b317e-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer provides the following tabs for use in exploring neural network mining models:</span></span>  
  
-   [<span data-ttu-id="b317e-119">输入</span><span class="sxs-lookup"><span data-stu-id="b317e-119">Inputs</span></span>](#BKMK_Inputs)  
  
-   [<span data-ttu-id="b317e-120">输出</span><span class="sxs-lookup"><span data-stu-id="b317e-120">Outputs</span></span>](#BKMK_Outputs)  
  
-   [<span data-ttu-id="b317e-121">变量</span><span class="sxs-lookup"><span data-stu-id="b317e-121">Variables</span></span>](#BKMK_Characteristics)  
  
###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="b317e-122">输入</span><span class="sxs-lookup"><span data-stu-id="b317e-122">Inputs</span></span>  
 <span data-ttu-id="b317e-123">使用 **“输入”** 选项卡可以选择模型用作输入的属性及属性值。</span><span class="sxs-lookup"><span data-stu-id="b317e-123">Use the **Inputs** tab to choose the attributes and values that the model used as inputs.</span></span> <span data-ttu-id="b317e-124">该查看器打开时，默认设置是包含所有属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-124">By default, the viewer opens with all attributes included.</span></span> <span data-ttu-id="b317e-125">在此默认视图中，模型将选择哪些属性值是要显示的最重要的属性值。</span><span class="sxs-lookup"><span data-stu-id="b317e-125">In this default view, the model chooses which attribute values are the most important to display.</span></span>  
  
 <span data-ttu-id="b317e-126">若要选择输入属性，请在“输入”\*\*\*\* 网格的“属性”\*\*\*\* 列内部单击，再从下拉列表中选择一个属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-126">To select an input attribute, click inside the **Attribute** column of the **Input** grid, and select an attribute from the drop-down list.</span></span> <span data-ttu-id="b317e-127">（该列表中只包含在该模型中包含的属性。）</span><span class="sxs-lookup"><span data-stu-id="b317e-127">(Only attributes that are included in the model are included in the list.)</span></span>  
  
 <span data-ttu-id="b317e-128">第一个非重复值出现在 **“值”** 列下。</span><span class="sxs-lookup"><span data-stu-id="b317e-128">The first distinct value appears under the **Value** column.</span></span> <span data-ttu-id="b317e-129">单击默认值将显示一个包含关联属性的所有可能状态的列表。</span><span class="sxs-lookup"><span data-stu-id="b317e-129">Clicking the default value reveals a list that contains all the possible states of the associated attribute.</span></span> <span data-ttu-id="b317e-130">可以选择要调查的状态。</span><span class="sxs-lookup"><span data-stu-id="b317e-130">You can select the state that you want to investigate.</span></span> <span data-ttu-id="b317e-131">可以根据需要选择多个属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-131">You can select as many attributes as you want.</span></span>  
  
 [<span data-ttu-id="b317e-132">返回页首</span><span class="sxs-lookup"><span data-stu-id="b317e-132">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="b317e-133">输出</span><span class="sxs-lookup"><span data-stu-id="b317e-133">Outputs</span></span>  
 <span data-ttu-id="b317e-134">使用 **“输出”** 选项卡可以选择要调查的结果属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-134">Use the **Outputs** tab to choose the outcome attribute to investigate.</span></span> <span data-ttu-id="b317e-135">您可以选择任何两个结果状态来进行比较，并且假定在创建模型时列已定义为可预测属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-135">You can choose any two outcome states to compare, assuming the columns were defined as predictable attributes when the model was created.</span></span>  
  
 <span data-ttu-id="b317e-136">使用 **OutputAttribute** 列表选择一个属性。</span><span class="sxs-lookup"><span data-stu-id="b317e-136">Use the **OutputAttribute** list to select an attribute.</span></span> <span data-ttu-id="b317e-137">然后，可以从 **“值 1”** 和 **“值 2”** 列表中选择两个与该属性关联的状态。</span><span class="sxs-lookup"><span data-stu-id="b317e-137">You can then select two states that are associated with the attribute from the **Value 1** and **Value 2** lists.</span></span> <span data-ttu-id="b317e-138">输出属性的这两个状态将在 **“变量”** 窗格中进行比较。</span><span class="sxs-lookup"><span data-stu-id="b317e-138">These two states of the output attribute will be compared in the **Variables** pane.</span></span>  
  
 [<span data-ttu-id="b317e-139">返回页首</span><span class="sxs-lookup"><span data-stu-id="b317e-139">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="variables"></a><a name="BKMK_Characteristics"></a><span data-ttu-id="b317e-140">变化</span><span class="sxs-lookup"><span data-stu-id="b317e-140">Variables</span></span>  
 <span data-ttu-id="b317e-141">“变量”\*\*\*\* 选项卡中的网格包含下列各列：“Attribute”\*\*\*\*、“Value”\*\*\*\*、“Favors [value 1]”\*\*\*\* 和 “Favors [value 2]”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b317e-141">The grid in the **Variables** tab contains the following columns: **Attribute**, **Value**, **Favors [value 1]**, and **Favors [value 2]**.</span></span> <span data-ttu-id="b317e-142">默认情况下，这些列按“Favors [value 1]”\*\*\*\* 强度进行排序。</span><span class="sxs-lookup"><span data-stu-id="b317e-142">By default, the columns are sorted by the strength of **Favors [value 1]**.</span></span> <span data-ttu-id="b317e-143">单击列标题将更改所选列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="b317e-143">Clicking a column heading changes the sort order to the selected column.</span></span>  
  
 <span data-ttu-id="b317e-144">属性右侧的条表示指定输入属性状态所倾向的输出属性状态。</span><span class="sxs-lookup"><span data-stu-id="b317e-144">A bar to the right of the attribute shows which state of the output attribute the specified input attribute state favors.</span></span> <span data-ttu-id="b317e-145">条的大小则表示输出状态倾向于输入状态的程度。</span><span class="sxs-lookup"><span data-stu-id="b317e-145">The size of the bar shows how strongly the output state favors the input state.</span></span>  
  
 [<span data-ttu-id="b317e-146">返回页首</span><span class="sxs-lookup"><span data-stu-id="b317e-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="b317e-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b317e-147">See Also</span></span>  
 <span data-ttu-id="b317e-148">[Microsoft 神经网络算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="b317e-148">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="b317e-149">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b317e-149">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="b317e-150">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b317e-150">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="b317e-151">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b317e-151">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="b317e-152">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="b317e-152">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
