---
title: Microsoft Naive Bayes 算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Bayesian classifiers
- algorithms [data mining]
- predictive modeling [Analysis Services]
- classification algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
ms.assetid: 3b53e011-3b1a-4cd1-bdc2-456768ba31b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: f38ba263f4bba9ec09e2f195c3ed16ec8b3a1229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682434"
---
# <a name="microsoft-naive-bayes-algorithm"></a><span data-ttu-id="7c899-102">Microsoft Naive Bayes Algorithm</span><span class="sxs-lookup"><span data-stu-id="7c899-102">Microsoft Naive Bayes Algorithm</span></span>
  <span data-ttu-id="7c899-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Naive Bayes 算法是一种基于 Bayes ' 定理的分类算法，由提供 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以便在预测建模中使用。</span><span class="sxs-lookup"><span data-stu-id="7c899-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm based on Bayes' theorems, and provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="7c899-104">Naïve Bayes 名称中的 Naïve 一词派生自这样一个事实：该算法使用贝叶斯技术，但未将可能存在的依赖关系考虑在内。</span><span class="sxs-lookup"><span data-stu-id="7c899-104">The word naïve in the name Naïve Bayes derives from the fact that the algorithm uses Bayesian techniques but does not take into account dependencies that may exist.</span></span>

 <span data-ttu-id="7c899-105">和其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法相比，此算法所需运算量较少，因而有助于快速生成挖掘模型，从而发现输入列与可预测列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="7c899-105">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="7c899-106">可以使用该算法进行初始数据探测，然后根据该算法的结果使用其他运算量较大、更加精确的算法创建其他挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7c899-106">You can use this algorithm to do initial exploration of data, and then later you can apply the results to create additional mining models with other algorithms that are more computationally intense and more accurate.</span></span>

## <a name="example"></a><span data-ttu-id="7c899-107">示例</span><span class="sxs-lookup"><span data-stu-id="7c899-107">Example</span></span>
 <span data-ttu-id="7c899-108">作为正在进行的促销策略，Adventure Works Cycle 公司的市场部已经决定通过发送宣传资料将目标定位为潜在的客户。</span><span class="sxs-lookup"><span data-stu-id="7c899-108">As an ongoing promotional strategy, the marketing department for the Adventure Works Cycle company has decided to target potential customers by mailing out fliers.</span></span> <span data-ttu-id="7c899-109">为了降低成本，他们只向有可能做出反应的客户发送宣传资料。</span><span class="sxs-lookup"><span data-stu-id="7c899-109">To reduce costs, they want to send fliers only to those customers who are likely to respond.</span></span> <span data-ttu-id="7c899-110">该公司将有关客户统计数据以及对上一邮件的反映的信息存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="7c899-110">The company stores information in a database about demographics and response to a previous mailing.</span></span> <span data-ttu-id="7c899-111">他们希望利用这些数据将潜在客户和具备相同特征并曾经购买过公司产品的客户进行对比，以了解年龄和位置等统计数据如何帮助预测客户对促销的响应。</span><span class="sxs-lookup"><span data-stu-id="7c899-111">They want to use this data to see how demographics such as age and location can help predict response to a promotion, by comparing potential customers to customers who have similar characteristics and who have purchased from the company in the past.</span></span> <span data-ttu-id="7c899-112">他们尤其希望找出购买自行车的客户与未购买自行车的客户之间的差别。</span><span class="sxs-lookup"><span data-stu-id="7c899-112">Specifically, they want to see the differences between those customers who bought a bicycle and those customers who did not.</span></span>

 <span data-ttu-id="7c899-113">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法，市场部能够快速预测特定客户群的结果，进而确定最有可能对邮件做出响应的客户。</span><span class="sxs-lookup"><span data-stu-id="7c899-113">By using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm, the marketing department can quickly predict an outcome for a particular customer profile, and can therefore determine which customers are most likely to respond to the fliers.</span></span> <span data-ttu-id="7c899-114">而使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Naive Bayes 查看器，他们还能够以直观的方式专门调查哪些输入列有助于对宣传资料做出积极响应。</span><span class="sxs-lookup"><span data-stu-id="7c899-114">By using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], they can also visually investigate specifically which input columns contribute to positive responses to fliers.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="7c899-115">算法的原理</span><span class="sxs-lookup"><span data-stu-id="7c899-115">How the Algorithm Works</span></span>
 <span data-ttu-id="7c899-116">在给定可预测列的各种可能状态的情况下， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法将计算每个输入列的每种状态的概率。</span><span class="sxs-lookup"><span data-stu-id="7c899-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm calculates the probability of every state of each input column, given each possible state of the predictable column.</span></span>

 <span data-ttu-id="7c899-117">若要了解其工作原理，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] Naive Bayes 查看器（如下图所示）来直观地查看该算法分布状态的方式。</span><span class="sxs-lookup"><span data-stu-id="7c899-117">To understand how this works, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] (as shown in the following graphic) to visually explore how the algorithm distributes states.</span></span>

 <span data-ttu-id="7c899-118">![状态的 Naive bayes 分布](../media/naive-bayes.gif "状态的 Naive bayes 分布")</span><span class="sxs-lookup"><span data-stu-id="7c899-118">![Naive bayes distribution of states](../media/naive-bayes.gif "Naive bayes distribution of states")</span></span>

 <span data-ttu-id="7c899-119">此处， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器可列出数据集中的每个输入列。如果提供了可预测列的每种状态，它还会显示每一列中状态的分布情况。</span><span class="sxs-lookup"><span data-stu-id="7c899-119">Here, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer lists each input column in the dataset, and shows how the states of each column are distributed, given each state of the predictable column.</span></span>

 <span data-ttu-id="7c899-120">您将利用该模型视图来确定对区分可预测列状态具有重要作用的输入列。</span><span class="sxs-lookup"><span data-stu-id="7c899-120">You would use this view of the model to identify the input columns that are important for differentiating between states of the predictable column.</span></span>

 <span data-ttu-id="7c899-121">例如，在此处显示的“Commute Distance”行中，输入值的分布对于购买者和非买者存在明显的不同。</span><span class="sxs-lookup"><span data-stu-id="7c899-121">For example, in the row for Commute Distance shown here, the distribution of input values is visibly different for buyers vs. non-buyers.</span></span> <span data-ttu-id="7c899-122">这表明，“Commute Distance = 0-1 miles”输入可能是一个预测因子。</span><span class="sxs-lookup"><span data-stu-id="7c899-122">What this tells you is that the input, Commute Distance = 0-1 miles, is a potential predictor.</span></span>

 <span data-ttu-id="7c899-123">该查看器还提供了分布的值，这样您便能看到，对于上下班路程为一至二英里的客户，其购买自行车的概率是 0.387，不购买自行车的概率是 0.287。</span><span class="sxs-lookup"><span data-stu-id="7c899-123">The viewer also provides values for the distributions, so you can see that for customers who commute from one to two miles to work, the probability of them buying a bike is 0.387, and the probability that they will not buy a bike is 0.287.</span></span> <span data-ttu-id="7c899-124">在本示例中，该算法使用从诸如上下班路程之类的客户特征得出的数字信息来预测客户是否会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="7c899-124">In this example, the algorithm uses the numeric information, derived from customer characteristics (such as commute distance), to predict whether a customer will buy a bike.</span></span>

 <span data-ttu-id="7c899-125">有关使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器的详细信息，请参阅 [使用 Microsoft Naive Bayes 查看器浏览模型](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-125">For more information about using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, see [Browse a Model Using the Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span>

## <a name="data-required-for-naive-bayes-models"></a><span data-ttu-id="7c899-126">Naive Bayes 模型所需的数据</span><span class="sxs-lookup"><span data-stu-id="7c899-126">Data Required for Naive Bayes Models</span></span>
 <span data-ttu-id="7c899-127">在准备用于定型 Naive Bayes 模型的数据时，应理解算法的要求，其中包括所需要的数据量以及使用数据的方式。</span><span class="sxs-lookup"><span data-stu-id="7c899-127">When you prepare data for use in training a Naive Bayes model, you should understand the requirements for the algorithm, including how much data is needed, and how the data is used.</span></span>

 <span data-ttu-id="7c899-128">Naive Bayes 模型的要求如下：</span><span class="sxs-lookup"><span data-stu-id="7c899-128">The requirements for a Naive Bayes model are as follows:</span></span>

-   <span data-ttu-id="7c899-129">**单键列** 每个模型都必须包含一个用于唯一标识每条记录的数值列或文本列。</span><span class="sxs-lookup"><span data-stu-id="7c899-129">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="7c899-130">不允许复合键。</span><span class="sxs-lookup"><span data-stu-id="7c899-130">Compound keys are not allowed.</span></span>

-   <span data-ttu-id="7c899-131">**输入列**在 Naive Bayes 模型中，所有列都必须是离散或离散化的列。</span><span class="sxs-lookup"><span data-stu-id="7c899-131">**Input columns** In a Naive Bayes model, all columns must be either discrete or discretized columns.</span></span> <span data-ttu-id="7c899-132">有关离散化列的信息，请参阅[数据挖掘&#41;&#40;离散化方法](discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-132">For information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md).</span></span>

     <span data-ttu-id="7c899-133">对于 Naive Bayes 模型，确保输入属性相互独立也很重要。</span><span class="sxs-lookup"><span data-stu-id="7c899-133">For a Naive Bayes model, it is also important to ensure that the input attributes are independent of each other.</span></span> <span data-ttu-id="7c899-134">这在使用该模型进行预测时尤为重要。</span><span class="sxs-lookup"><span data-stu-id="7c899-134">This is particularly important when you use the model for prediction.</span></span>

     <span data-ttu-id="7c899-135">原因在于，如果您使用已密切关联的两列数据，则会导致这些列的影响倍增，从而掩盖影响结果的其他因素。</span><span class="sxs-lookup"><span data-stu-id="7c899-135">The reason is that, if you use two columns of data that are already closely related, the effect would be to multiply the influence of those columns, which can obscure other factors that influence the outcome.</span></span>

     <span data-ttu-id="7c899-136">相反，在浏览模型或数据集时，该算法能够识别各个变量之间的相关性对于标识输入之间的关系会很有用。</span><span class="sxs-lookup"><span data-stu-id="7c899-136">Conversely, the ability of the algorithm to identify correlations among variables is useful when you are exploring a model or dataset, to identify relationships among inputs.</span></span>

-   <span data-ttu-id="7c899-137">**至少有一个可预测列** 可预测属性必须包含离散或离散化值。</span><span class="sxs-lookup"><span data-stu-id="7c899-137">**At least one predictable column** The predictable attribute must contain discrete or discretized values.</span></span>

     <span data-ttu-id="7c899-138">可以将可预测列的值视为输入。</span><span class="sxs-lookup"><span data-stu-id="7c899-138">The values of the predictable column can be treated as inputs.</span></span> <span data-ttu-id="7c899-139">在浏览新数据集时，此操作对于查找列之间的关系会很有用。</span><span class="sxs-lookup"><span data-stu-id="7c899-139">This practice can be useful when you are exploring a new dataset, to find relationships among the columns.</span></span>

## <a name="viewing-the-model"></a><span data-ttu-id="7c899-140">查看模型</span><span class="sxs-lookup"><span data-stu-id="7c899-140">Viewing the Model</span></span>
 <span data-ttu-id="7c899-141">您可以使用 **Microsoft Naive Bayes 查看器**浏览模型。</span><span class="sxs-lookup"><span data-stu-id="7c899-141">To explore the model, you can use the **Microsoft Naive Bayes Viewer**.</span></span> <span data-ttu-id="7c899-142">该查看器显示输入属性与可预测属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="7c899-142">The viewer shows you how the input attributes relate to the predictable attribute.</span></span> <span data-ttu-id="7c899-143">该查看器还提供了每个分类的详细配置文件、将每个分类与其他分类区分开来的属性列表以及整个定型数据集的特征。</span><span class="sxs-lookup"><span data-stu-id="7c899-143">The viewer also provides a detailed profile of each cluster, a list of the attributes that distinguish each cluster from the others, and the characteristics of the entire training data set.</span></span> <span data-ttu-id="7c899-144">有关详细信息，请参阅 [使用 Microsoft Naive Bayes 查看器浏览模型](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-144">For more information, see [Browse a Model Using the Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span>

 <span data-ttu-id="7c899-145">如果希望了解更多详细信息，可在 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)中浏览该模型。</span><span class="sxs-lookup"><span data-stu-id="7c899-145">If you want to know more detail, you can browse the model in the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="7c899-146">有关模型中存储的信息类型的详细信息，请参阅 [Naive Bayes 模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-146">For more information about the type of information stored in the model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span>

## <a name="making-predictions"></a><span data-ttu-id="7c899-147">作出预测</span><span class="sxs-lookup"><span data-stu-id="7c899-147">Making Predictions</span></span>
 <span data-ttu-id="7c899-148">为模型定型后，结果将存储为一组模式，您可以浏览该模型或利用它来作出预测。</span><span class="sxs-lookup"><span data-stu-id="7c899-148">After the model has been trained, the results are stored as a set of patterns, which you can explore or use to make predictions.</span></span>

 <span data-ttu-id="7c899-149">您可以创建查询，以返回有关新数据与可预测属性之间的关系的预测，也可以检索统计信息，以说明该模型发现的相关性。</span><span class="sxs-lookup"><span data-stu-id="7c899-149">You can create queries to return predictions about how new data relates to the predictable attribute, or you can retrieve statistics that describe the correlations found by the model.</span></span>

 <span data-ttu-id="7c899-150">有关如何创建针对数据挖掘模型的查询的信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-150">For information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span> <span data-ttu-id="7c899-151">有关如何使用针对 Naive Bayes 模型的查询的示例，请参阅 [Naive Bayes 模型查询示例](naive-bayes-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="7c899-151">For examples of how to use queries with a Naive Bayes model, see [Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="7c899-152">备注</span><span class="sxs-lookup"><span data-stu-id="7c899-152">Remarks</span></span>

-   <span data-ttu-id="7c899-153">支持使用预测模型标记语言 (PMML) 创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7c899-153">Supports the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="7c899-154">支持钻取。</span><span class="sxs-lookup"><span data-stu-id="7c899-154">Supports drillthrough.</span></span>

-   <span data-ttu-id="7c899-155">不支持创建数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="7c899-155">Does not support the creation of data mining dimensions.</span></span>

-   <span data-ttu-id="7c899-156">支持使用 OLAP 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="7c899-156">Supports the use of OLAP mining models.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c899-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c899-157">See Also</span></span>
 <span data-ttu-id="7c899-158">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) [功能选择 &#40;数据挖掘&#41;](feature-selection-data-mining.md) [Naive Bayes 模型查询示例](naive-bayes-model-query-examples.md) [Naive Bayes 模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md) [Microsoft Naive Bayes 算法技术参考](microsoft-naive-bayes-algorithm-technical-reference.md)</span><span class="sxs-lookup"><span data-stu-id="7c899-158">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md) [Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md) [Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md)</span></span>


