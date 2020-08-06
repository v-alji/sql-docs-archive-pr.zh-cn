---
title: Microsoft 逻辑回归算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logical regression algorithms [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 3dd54d07-1c3b-4b87-b7f0-b962ed8cf844
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56a1b0b82f82b62e55d0c7fdd528195b5713fcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590994"
---
# <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="c46c1-102">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="c46c1-102">Microsoft Logistic Regression Algorithm</span></span>
  <span data-ttu-id="c46c1-103">逻辑回归是一种众所周知的统计方法，用于对二进制结果建模。</span><span class="sxs-lookup"><span data-stu-id="c46c1-103">Logistic regression is a well-known statistical technique that is used for modeling binary outcomes.</span></span>  
  
 <span data-ttu-id="c46c1-104">通过采用不同的学习方法，可以在统计研究中以各种方式实现逻辑回归。</span><span class="sxs-lookup"><span data-stu-id="c46c1-104">There are various implementations of logistic regression in statistics research, using different learning techniques.</span></span> <span data-ttu-id="c46c1-105">已通过使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法的一种变体来实现 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法。</span><span class="sxs-lookup"><span data-stu-id="c46c1-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm has been implemented by using a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="c46c1-106">虽然此算法与神经网络算法有许多共性，但逻辑回归算法更易于定型。</span><span class="sxs-lookup"><span data-stu-id="c46c1-106">This algorithm shares many of the qualities of neural networks but is easier to train.</span></span>  
  
 <span data-ttu-id="c46c1-107">逻辑回归算法的一大优势是，该算法可采用任何类型的输入，因此非常灵活，并且支持若干不同的分析任务：</span><span class="sxs-lookup"><span data-stu-id="c46c1-107">One advantage of logistic regression is that the algorithm is highly flexible, taking any kind of input, and supports several different analytical tasks:</span></span>  
  
-   <span data-ttu-id="c46c1-108">使用人口统计信息预测相关结果，如某种特定疾病的风险。</span><span class="sxs-lookup"><span data-stu-id="c46c1-108">Use demographics to make predictions about outcomes, such as risk for a certain disease.</span></span>  
  
-   <span data-ttu-id="c46c1-109">浏览并权衡导致结果的因素。</span><span class="sxs-lookup"><span data-stu-id="c46c1-109">Explore and weight the factors that contribute to a result.</span></span> <span data-ttu-id="c46c1-110">例如，查找影响客户反复光顾某一商店的因素。</span><span class="sxs-lookup"><span data-stu-id="c46c1-110">For example, find the factors that influence customers to make a repeat visit to a store.</span></span>  
  
-   <span data-ttu-id="c46c1-111">对文档、电子邮件或具有多个属性的其他对象进行分类。</span><span class="sxs-lookup"><span data-stu-id="c46c1-111">Classify documents, e-mail, or other objects that have many attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c46c1-112">示例</span><span class="sxs-lookup"><span data-stu-id="c46c1-112">Example</span></span>  
 <span data-ttu-id="c46c1-113">设想这样一组人员，他们共享类似的人口统计信息并从 Adventure Works 公司购买产品。</span><span class="sxs-lookup"><span data-stu-id="c46c1-113">Consider a group of people who share similar demographic information and who buy products from the Adventure Works company.</span></span> <span data-ttu-id="c46c1-114">通过对与特定结果（如购买目标产品）相关的数据进行建模，您可以查看人口统计信息对客户购买目标产品的可能性的影响。</span><span class="sxs-lookup"><span data-stu-id="c46c1-114">By modeling the data to relate to a specific outcome, such as purchase of a target product, you can see how the demographic information contributes to someone's likelihood of buying the target product.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="c46c1-115">算法的原理</span><span class="sxs-lookup"><span data-stu-id="c46c1-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="c46c1-116">逻辑回归是一种众所周知的统计方法，用于确定多个因素对一对结果的影响。</span><span class="sxs-lookup"><span data-stu-id="c46c1-116">Logistic regression is a well-known statistical method for determining the contribution of multiple factors to a pair of outcomes.</span></span> <span data-ttu-id="c46c1-117">Microsoft 实现使用修改后的神经网络，对输入和输出之间的关系进行建模。</span><span class="sxs-lookup"><span data-stu-id="c46c1-117">The Microsoft implementation uses a modified neural network to model the relationships between inputs and outputs.</span></span> <span data-ttu-id="c46c1-118">测量每个输入对输出的影响，并权衡不同输入在完成的模型中的作用。</span><span class="sxs-lookup"><span data-stu-id="c46c1-118">The effect of each input on the output is measured, and the various inputs are weighted in the finished model.</span></span> <span data-ttu-id="c46c1-119">名称逻辑回归来自这样一个事实：使用逻辑转换压缩数据曲线，以使极值的影响减至最小。</span><span class="sxs-lookup"><span data-stu-id="c46c1-119">The name logistic regression comes from the fact that the data curve is compressed by using a logistic transformation, to minimize the effect of extreme values.</span></span> <span data-ttu-id="c46c1-120">有关该实现以及如何自定义算法的详细信息，请参阅 [Microsoft 逻辑回归算法技术参考](microsoft-logistic-regression-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c1-120">For more information about the implementation, and how to customize the algorithm, see [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-logistic-regression-models"></a><span data-ttu-id="c46c1-121">逻辑回归模型所需的数据</span><span class="sxs-lookup"><span data-stu-id="c46c1-121">Data Required for Logistic Regression Models</span></span>  
 <span data-ttu-id="c46c1-122">准备用于定型逻辑回归模型的数据时，应理解特定算法的要求，其中包括所需要的数据量以及使用数据的方式。</span><span class="sxs-lookup"><span data-stu-id="c46c1-122">When you prepare data for use in training a logistic regression model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>  
  
 <span data-ttu-id="c46c1-123">逻辑回归模型的要求如下：</span><span class="sxs-lookup"><span data-stu-id="c46c1-123">The requirements for a logistic regression model are as follows:</span></span>  
  
 <span data-ttu-id="c46c1-124">**单键列** 每个模型都必须包含一个用于唯一标识每条记录的数值列或文本列。</span><span class="sxs-lookup"><span data-stu-id="c46c1-124">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="c46c1-125">不允许复合键。</span><span class="sxs-lookup"><span data-stu-id="c46c1-125">Compound keys are not allowed.</span></span>  
  
 <span data-ttu-id="c46c1-126">**输入列** 每个模型都必须至少包含一个输入列，该输入列包含用作分析因素的值。</span><span class="sxs-lookup"><span data-stu-id="c46c1-126">**Input columns** Each model must contain at least one input column that contains the values that are used as factors in analysis.</span></span> <span data-ttu-id="c46c1-127">可以根据需要拥有任意多的输入列，但是具体取决于每个列中值的数量，添加额外列会增加定型模型所需的时间。</span><span class="sxs-lookup"><span data-stu-id="c46c1-127">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>  
  
 <span data-ttu-id="c46c1-128">**至少有一个可预测列** 模型必须至少包含一个可预测列，该预测列可以为任意数据类型，包括连续数值数据。</span><span class="sxs-lookup"><span data-stu-id="c46c1-128">**At least one predictable column** The model must contain at least one predictable column of any data type, including continuous numeric data.</span></span> <span data-ttu-id="c46c1-129">还可以将可预测列的值视为模型的输入，或者将其指定为仅用于预测。</span><span class="sxs-lookup"><span data-stu-id="c46c1-129">The values of the predictable column can also be treated as inputs to the model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="c46c1-130">嵌套表不允许用于可预测列，但是可作为输入使用。</span><span class="sxs-lookup"><span data-stu-id="c46c1-130">Nested tables are not allowed for predictable columns, but can be used as inputs.</span></span>  
  
 <span data-ttu-id="c46c1-131">有关逻辑回归模型支持的内容类型和数据类型的详细信息，请参阅 [Microsoft 逻辑回归算法技术参考](microsoft-logistic-regression-algorithm-technical-reference.md)的“要求”部分。</span><span class="sxs-lookup"><span data-stu-id="c46c1-131">For more detailed information about the content types and data types supported for logistic regression models, see the Requirements section of [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-logistic-regression-model"></a><span data-ttu-id="c46c1-132">查看逻辑回归模型</span><span class="sxs-lookup"><span data-stu-id="c46c1-132">Viewing a Logistic Regression Model</span></span>  
 <span data-ttu-id="c46c1-133">您可以使用 Microsoft 神经网络查看器或 Microsoft 一般内容树查看器浏览模型。</span><span class="sxs-lookup"><span data-stu-id="c46c1-133">To explore the model, you can use the Microsoft Neural Network Viewer, or the Microsoft Generic Content Tree Viewer.</span></span>  
  
 <span data-ttu-id="c46c1-134">使用 Microsoft 神经网络查看器查看模型时，Analysis Services 显示影响特定结果的因素，这些因素按重要性进行排序。</span><span class="sxs-lookup"><span data-stu-id="c46c1-134">When you view the model by using the Microsoft Neural Network Viewer, Analysis Services shows you the factors that contribute to a particular outcome, ranked by their importance.</span></span> <span data-ttu-id="c46c1-135">您可以选择一个属性以及要比较的值。</span><span class="sxs-lookup"><span data-stu-id="c46c1-135">You can choose an attribute and values to compare.</span></span> <span data-ttu-id="c46c1-136">有关详细信息，请参阅 [使用 Microsoft 神经网络查看器浏览模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c1-136">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="c46c1-137">如果希望了解更多信息，您可以使用 Microsoft 一般内容树查看器浏览模型的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c46c1-137">If you want to know more, you can browse the model details by using the Microsoft Generic Content Tree Viewer.</span></span> <span data-ttu-id="c46c1-138">逻辑回归模型的模型内容包含的边际节点显示该模型的所有输入以及可预测属性的子网。</span><span class="sxs-lookup"><span data-stu-id="c46c1-138">The model content for a logistic regression model includes a marginal node that shows you the all the inputs used for the model, and subnetworks for the predictable attributes.</span></span> <span data-ttu-id="c46c1-139">有关详细信息，请参阅 [逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c1-139">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="c46c1-140">创建预测</span><span class="sxs-lookup"><span data-stu-id="c46c1-140">Creating Predictions</span></span>  
 <span data-ttu-id="c46c1-141">定型模型之后，您可以针对模型内容创建查询以获取回归系数和其他详细信息，还可以使用模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="c46c1-141">After the model has been trained, you can create queries against the model content to get the regression coefficients and other details, or you can use the model to make predictions.</span></span>  
  
-   <span data-ttu-id="c46c1-142">有关如何创建针对数据挖掘模型的查询的常规信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c1-142">For general information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
-   <span data-ttu-id="c46c1-143">有关查询逻辑回归模型的示例，请参阅 [聚类分析模型查询示例](clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="c46c1-143">For examples of queries on a logistic regression model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c46c1-144">备注</span><span class="sxs-lookup"><span data-stu-id="c46c1-144">Remarks</span></span>  
  
-   <span data-ttu-id="c46c1-145">不支持钻取，</span><span class="sxs-lookup"><span data-stu-id="c46c1-145">Does not support drillthrough.</span></span> <span data-ttu-id="c46c1-146">这是因为挖掘模型中节点的结构不一定直接与基础数据对应。</span><span class="sxs-lookup"><span data-stu-id="c46c1-146">This is because the structure of nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="c46c1-147">不支持创建数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="c46c1-147">Does not support the creation of data mining dimensions.</span></span>  
  
-   <span data-ttu-id="c46c1-148">支持使用 OLAP 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c46c1-148">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="c46c1-149">不支持使用预测模型标记语言 (PMML) 创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c46c1-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46c1-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c46c1-150">See Also</span></span>  
 <span data-ttu-id="c46c1-151">[&#40;Analysis Services 数据挖掘的逻辑回归模型的挖掘模型内容&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="c46c1-151">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 <span data-ttu-id="c46c1-152">[Microsoft 逻辑回归算法技术参考](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c46c1-152">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="c46c1-153">逻辑回归模型查询示例</span><span class="sxs-lookup"><span data-stu-id="c46c1-153">Logistic Regression Model Query Examples</span></span>](logistic-regression-model-query-examples.md)  
  
  
