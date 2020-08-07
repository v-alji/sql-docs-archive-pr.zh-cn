---
title: 浏览 Naive Bayes 模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a26fa972e1ed50e2f4107026210a5935fcb86d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690932"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a><span data-ttu-id="fa83f-102">浏览 Naive Bayes 模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="fa83f-102">Exploring the Naive Bayes Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="fa83f-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes 算法提供多种方法用于显示自行车购买与输入属性之间的交互。</span><span class="sxs-lookup"><span data-stu-id="fa83f-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm provides several methods for displaying the interaction between bike buying and the input attributes.</span></span>  
  
 <span data-ttu-id="fa83f-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes 查看器提供了以下选项卡，用于浏览 Naive Bayes 挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="fa83f-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes Viewer provides the following tabs for use in exploring Naive Bayes mining models:</span></span>  
  
 
  
##  <a name="dependency-network"></a><a name="DependencyNetwork"></a><span data-ttu-id="fa83f-105">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="fa83f-105">Dependency Network</span></span>  
 <span data-ttu-id="fa83f-106">"**依赖关系网络**" 选项卡的工作方式与树查看器的 "**依赖关系网络**" 选项卡的工作方式相同 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa83f-106">The **Dependency Network** tab works in the same way as the **Dependency Network** tab for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="fa83f-107">查看器中的每个节点代表一个属性，而节点之间的线条代表关系。</span><span class="sxs-lookup"><span data-stu-id="fa83f-107">Each node in the viewer represents an attribute, and the lines between nodes represent relationships.</span></span> <span data-ttu-id="fa83f-108">在查看器中，您可以查看影响可预测属性 Bike Buyer 的状态的所有属性。</span><span class="sxs-lookup"><span data-stu-id="fa83f-108">In the viewer, you can see all the attributes that affect the state of the predictable attribute, Bike Buyer.</span></span>  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="fa83f-109">在“依赖关系网络”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="fa83f-109">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="fa83f-110">可以使用 "**挖掘模型查看器**" 选项卡顶部的 "**挖掘模型**" 列表切换到 `TM_NaiveBayes` 模型。</span><span class="sxs-lookup"><span data-stu-id="fa83f-110">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_NaiveBayes` model.</span></span>  
  
2.  <span data-ttu-id="fa83f-111">使用**查看器**列表切换到**Microsoft Naive Bayes Viewer**。</span><span class="sxs-lookup"><span data-stu-id="fa83f-111">Use the **Viewer** list to switch to **Microsoft Naive Bayes Viewer**.</span></span>  
  
3.  <span data-ttu-id="fa83f-112">单击 `Bike Buyer` 节点以标识其依赖项。</span><span class="sxs-lookup"><span data-stu-id="fa83f-112">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="fa83f-113">粉色阴影指示所有属性都会对自行车购买行为产生影响。</span><span class="sxs-lookup"><span data-stu-id="fa83f-113">The pink shading indicates that all of the attributes have an effect on bike buying.</span></span>  
  
4.  <span data-ttu-id="fa83f-114">调整滑块可标识影响最大的属性。</span><span class="sxs-lookup"><span data-stu-id="fa83f-114">Adjust the slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="fa83f-115">向下滑动滑块时，将只保留对 [Bike Buyer] 列影响最大的属性。</span><span class="sxs-lookup"><span data-stu-id="fa83f-115">As you lower the slider, only the attributes that have the greatest effect on the [Bike Buyer] column remain.</span></span> <span data-ttu-id="fa83f-116">通过调整滑块，可以发现影响最大的几个属性为：拥有汽车的数量、通勤距离以及子女总数。</span><span class="sxs-lookup"><span data-stu-id="fa83f-116">By adjusting the slider, you can discover that a few of the most influential attributes are: number of cars owned, commute distance, and total number of children.</span></span>  
 
  
##  <a name="attribute-profiles"></a><a name="AttributeProfiles"></a><span data-ttu-id="fa83f-117">属性配置文件</span><span class="sxs-lookup"><span data-stu-id="fa83f-117">Attribute Profiles</span></span>  
 <span data-ttu-id="fa83f-118">"**属性配置文件**" 选项卡描述了输入属性的不同状态如何影响可预测属性的结果。</span><span class="sxs-lookup"><span data-stu-id="fa83f-118">The **Attribute Profiles** tab describes how different states of the input attributes affect the outcome of the predictable attribute.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a><span data-ttu-id="fa83f-119">在“属性配置文件”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="fa83f-119">To explore the model in the Attribute Profiles tab</span></span>  
  
1.  <span data-ttu-id="fa83f-120">在 "**可预测**" 框中，验证 `Bike Buyer` 是否已选中。</span><span class="sxs-lookup"><span data-stu-id="fa83f-120">In the **Predictable** box, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="fa83f-121">如果 "**挖掘图例**" 阻止显示**属性配置文件**，请将其移开。</span><span class="sxs-lookup"><span data-stu-id="fa83f-121">If the **Mining Legend** is blocking display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="fa83f-122">在 "**直方图**条" 框中，选择**5**。</span><span class="sxs-lookup"><span data-stu-id="fa83f-122">In the **Histogram** bars box, select **5**.</span></span>  
  
     <span data-ttu-id="fa83f-123">在我们的模型中，任意一个变量的最大状态数均为 5。</span><span class="sxs-lookup"><span data-stu-id="fa83f-123">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
     <span data-ttu-id="fa83f-124">系统会列出影响该可预测属性的状态的属性以及输入属性的每个状态的值及其在该可预测属性的每个状态中的分布。</span><span class="sxs-lookup"><span data-stu-id="fa83f-124">The attributes that affect the state of this predictable attribute are listed together with the values of each state of the input attributes and their distributions in each state of the predictable attribute.</span></span>  
  
4.  <span data-ttu-id="fa83f-125">在 "**属性**" 列中，查找 "**汽车拥有**"。</span><span class="sxs-lookup"><span data-stu-id="fa83f-125">In the **Attributes** column, find **Number Cars Owned**.</span></span>  <span data-ttu-id="fa83f-126">请注意，自行车购买者（标为 1 的列）与非自行车购买者（标为 0 的列）的直方图的差异。</span><span class="sxs-lookup"><span data-stu-id="fa83f-126">Notice the differences in the histograms for bike buyers (column labeled 1) and non-buyers (column labeled 0).</span></span> <span data-ttu-id="fa83f-127">如果一个人拥有的汽车数量为 0 或 1，则此人很有可能会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="fa83f-127">A person with zero or one car is much more likely to buy a bike.</span></span>  
  
5.  <span data-ttu-id="fa83f-128">双击 "自行车购买者" (列中标记为 "1) 列" 的 "**汽车拥有**的单元"。</span><span class="sxs-lookup"><span data-stu-id="fa83f-128">Double-click the **Number Cars Owned** cell in the bike buyer (column labeled 1) column.</span></span>  
  
     <span data-ttu-id="fa83f-129">"**挖掘图例**" 显示更详细的视图。</span><span class="sxs-lookup"><span data-stu-id="fa83f-129">The **Mining Legend** displays a more detailed view.</span></span>  
  
  
##  <a name="attribute-characteristics"></a><a name="AttributeCharacteristics"></a><span data-ttu-id="fa83f-130">属性特征</span><span class="sxs-lookup"><span data-stu-id="fa83f-130">Attribute Characteristics</span></span>  
 <span data-ttu-id="fa83f-131">使用 "**属性特征**" 选项卡，您可以选择属性和值，以查看在选定的值事例中显示其他属性的值的频率。</span><span class="sxs-lookup"><span data-stu-id="fa83f-131">With the **Attribute Characteristics** tab, you can select an attribute and value to see how frequently values for other attributes appear in the selected value cases.</span></span>  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a><span data-ttu-id="fa83f-132">在“属性特征”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="fa83f-132">To explore the model in the Attribute Characteristics tab</span></span>  
  
1.  <span data-ttu-id="fa83f-133">在 "**属性**" 列表中，验证 `Bike Buyer` 是否已选中。</span><span class="sxs-lookup"><span data-stu-id="fa83f-133">In the **Attribute** list, verify that `Bike Buyer` is selected.</span></span>  
  
2.  <span data-ttu-id="fa83f-134">将**值**设置为**1**。</span><span class="sxs-lookup"><span data-stu-id="fa83f-134">Set the **Value** to **1**.</span></span>  
  
     <span data-ttu-id="fa83f-135">在查看器中，您将看到，家中无子女、通勤距离较近和居住在北美洲地区的客户更有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="fa83f-135">In the viewer, you will see that customers who have no children at home, short commutes, and live in the North America region are more likely to buy a bike.</span></span>  
  
  
##  <a name="attribute-discrimination"></a><a name="AttributeDiscrimination"></a><span data-ttu-id="fa83f-136">属性对比</span><span class="sxs-lookup"><span data-stu-id="fa83f-136">Attribute Discrimination</span></span>  
 <span data-ttu-id="fa83f-137">利用 "**属性对比**" 选项卡，您可以调查自行车购买的两个离散值与其他属性值之间的关系。</span><span class="sxs-lookup"><span data-stu-id="fa83f-137">With the **Attribute Discrimination** tab, you can investigate the relationship between two discrete values of bike buying and other attribute values.</span></span> <span data-ttu-id="fa83f-138">由于 `TM_NaiveBayes` 模型只有两种状态：1和0，因此不必对查看器进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="fa83f-138">Because the `TM_NaiveBayes` model has only two states, 1 and 0, you do not have to make any changes to the viewer.</span></span>  
  
 <span data-ttu-id="fa83f-139">在查看器中，您会看到，没有汽车的人一般会购买自行车，而有两辆汽车的人一般不会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="fa83f-139">In the viewer, you can see that people who do not own cars tend to buy bicycles, and people who own two cars tend not to buy bicycles.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fa83f-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fa83f-140">Related Tasks</span></span>  
 <span data-ttu-id="fa83f-141">请参阅以下主题以了解其他挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="fa83f-141">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="fa83f-142">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="fa83f-142">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="fa83f-143">浏览聚类分析模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="fa83f-143">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="fa83f-144">下一课</span><span class="sxs-lookup"><span data-stu-id="fa83f-144">Next Lesson</span></span>  
 [<span data-ttu-id="fa83f-145">第5课：测试模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="fa83f-145">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="fa83f-146">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="fa83f-146">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="fa83f-147">浏览聚类分析模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="fa83f-147">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa83f-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa83f-148">See Also</span></span>  
 <span data-ttu-id="fa83f-149">[使用 Microsoft Naive Bayes 查看器浏览模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="fa83f-149">[Browse a Model Using the Microsoft Naive Bayes Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md) </span></span>  
 <span data-ttu-id="fa83f-150">[挖掘模型查看器 &#40;的属性对比选项卡&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="fa83f-150">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="fa83f-151">[挖掘模型查看器 &#40;"属性配置文件" 选项卡&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="fa83f-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="fa83f-152">[挖掘模型查看器 &#40;"属性特征" 选项卡&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="fa83f-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="fa83f-153">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="fa83f-153">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
