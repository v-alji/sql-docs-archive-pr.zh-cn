---
title: Microsoft 逻辑回归算法技术参考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- HOLDOUT_PERCENTAGE parameter
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- regression algorithms [Analysis Services]
- HOLDOUT_SEED parameter
ms.assetid: cf32f1f3-153e-476f-91a4-bb834ec7c88d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72597453c9a52b890c822dd7c46aff46bc3ba44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590998"
---
# <a name="microsoft-logistic-regression-algorithm-technical-reference"></a><span data-ttu-id="152ef-102">Microsoft 逻辑回归算法技术参考</span><span class="sxs-lookup"><span data-stu-id="152ef-102">Microsoft Logistic Regression Algorithm Technical Reference</span></span>
  <span data-ttu-id="152ef-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法的一种变体，其中， *HIDDEN_NODE_RATIO* 参数设置为 0。</span><span class="sxs-lookup"><span data-stu-id="152ef-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, where the *HIDDEN_NODE_RATIO* parameter is set to 0.</span></span> <span data-ttu-id="152ef-104">这样设置以后，所创建的神经网络模型就不包含隐藏层，因此等效于逻辑回归。</span><span class="sxs-lookup"><span data-stu-id="152ef-104">This setting will create a neural network model that does not contain a hidden layer, and that therefore is equivalent to logistic regression.</span></span>

## <a name="implementation-of-the-microsoft-logistic-regression-algorithm"></a><span data-ttu-id="152ef-105">Microsoft 逻辑回归算法的实现</span><span class="sxs-lookup"><span data-stu-id="152ef-105">Implementation of the Microsoft Logistic Regression Algorithm</span></span>
 <span data-ttu-id="152ef-106">假定可预测列仅包含两个状态，但您仍希望进行回归分析，以将输入列与可预测列包含特定状态的概率关联起来。</span><span class="sxs-lookup"><span data-stu-id="152ef-106">Suppose the predictable column contains only two states, yet you still want to perform a regression analysis, relating input columns to the probability that the predictable column will contain a specific state.</span></span> <span data-ttu-id="152ef-107">下图展示了将可预测列的状态设置为 1 和 0，计算该列包含特定状态的概率以及对输入变量执行线性回归时将获得的结果。</span><span class="sxs-lookup"><span data-stu-id="152ef-107">The following diagram illustrates the results you will obtain if you assign 1 and 0 to the states of the predictable column, calculate the probability that the column will contain a specific state, and perform a linear regression against an input variable.</span></span>

 <span data-ttu-id="152ef-108">![未能使用线性回归正确建模的数据](../media/logistic-linear-regression.gif "未能使用线性回归正确建模的数据")</span><span class="sxs-lookup"><span data-stu-id="152ef-108">![Poorly modeled data using linear regression](../media/logistic-linear-regression.gif "Poorly modeled data using linear regression")</span></span>

 <span data-ttu-id="152ef-109">X 轴表示输入列的值。</span><span class="sxs-lookup"><span data-stu-id="152ef-109">The x-axis contains values of an input column.</span></span> <span data-ttu-id="152ef-110">Y 轴表示可预测列为某状态或其他状态的概率。</span><span class="sxs-lookup"><span data-stu-id="152ef-110">The y-axis contains the probabilities that the predictable column will be one state or the other.</span></span> <span data-ttu-id="152ef-111">此时的问题是，线性回归无法将该列限制在 0 和 1 之间，即使它们分别是该列的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="152ef-111">The problem with this is that the linear regression does not constrain the column to be between 0 and 1, even though those are the maximum and minimum values of the column.</span></span> <span data-ttu-id="152ef-112">解决此问题的一种方法是进行逻辑回归。</span><span class="sxs-lookup"><span data-stu-id="152ef-112">A way to solve this problem is to perform logistic regression.</span></span> <span data-ttu-id="152ef-113">逻辑回归将创建一条包含最大和最小约束的 S 形曲线，而不是一条直线。</span><span class="sxs-lookup"><span data-stu-id="152ef-113">Instead of creating a straight line, logistic regression analysis creates an "S" shaped curve that contains maximum and minimum constraints.</span></span> <span data-ttu-id="152ef-114">下图展示的是对上例中的数据进行逻辑回归后得到的结果。</span><span class="sxs-lookup"><span data-stu-id="152ef-114">For example, the following diagram illustrates the results you will achieve if you perform a logistic regression against the same data as used for the previous example.</span></span>

 <span data-ttu-id="152ef-115">![使用逻辑回归建模的数据](../media/logistic-regression.gif "使用逻辑回归建模的数据")</span><span class="sxs-lookup"><span data-stu-id="152ef-115">![Data modeled by using logistic regression](../media/logistic-regression.gif "Data modeled by using logistic regression")</span></span>

 <span data-ttu-id="152ef-116">请注意这条曲线是如何始终未能高于 1、低于 0 的。</span><span class="sxs-lookup"><span data-stu-id="152ef-116">Notice how the curve never goes above 1 or below 0.</span></span> <span data-ttu-id="152ef-117">您可以使用逻辑回归来说明哪些输入列对于确定可预测列的状态很重要。</span><span class="sxs-lookup"><span data-stu-id="152ef-117">You can use logistic regression to describe which input columns are important in determining the state of the predictable column.</span></span>

### <a name="feature-selection"></a><span data-ttu-id="152ef-118">特征选择</span><span class="sxs-lookup"><span data-stu-id="152ef-118">Feature Selection</span></span>
 <span data-ttu-id="152ef-119">所有 Analysis Services 数据挖掘算法均会自动使用功能选择来改善分析效果以及减轻处理工作量。</span><span class="sxs-lookup"><span data-stu-id="152ef-119">Feature selection is used automatically by all Analysis Services data mining algorithms to improve analysis and reduce processing load.</span></span> <span data-ttu-id="152ef-120">逻辑回归模型中用于功能选择的方法由属性的类型确定。</span><span class="sxs-lookup"><span data-stu-id="152ef-120">The method used for feature selection in a logistic regression model depends on the data type of the attribute.</span></span> <span data-ttu-id="152ef-121">由于逻辑回归基于 Microsoft 神经网络算法，因此，其所使用的功能选择方法为适用于神经网络的功能选择方法集的子集。</span><span class="sxs-lookup"><span data-stu-id="152ef-121">Because logistic regression is based on the Microsoft Neural Network algorithm, it uses a subset of the feature selection methods that apply to neural networks.</span></span> <span data-ttu-id="152ef-122">有关详细信息，请参阅[功能选择（数据挖掘）](feature-selection-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="152ef-122">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>

### <a name="scoring-inputs"></a><span data-ttu-id="152ef-123">计分输入</span><span class="sxs-lookup"><span data-stu-id="152ef-123">Scoring Inputs</span></span>
 <span data-ttu-id="152ef-124">在神经网络模型或逻辑回归模型中，“计分”\*\* 表示将数据中的值转换为一组使用同一刻度值的值，从而可相互进行比较。</span><span class="sxs-lookup"><span data-stu-id="152ef-124">*Scoring* in the context of a neural network model or logistic regression model means the process of converting the values that are present in the data into a set of values that use the same scale and therefore can be compared to each other.</span></span> <span data-ttu-id="152ef-125">例如，假设 Income 的输入范围为 0 到 100,000，而 [Number of Children] 的输入范围为 0 到 5。</span><span class="sxs-lookup"><span data-stu-id="152ef-125">For example, suppose the inputs for Income range from 0 to 100,000 whereas the inputs for [Number of Children] range from 0 to 5.</span></span> <span data-ttu-id="152ef-126">您可以使用转换处理来“计分” \*\* 或比较所有输入的重要程度，而不用考虑值之间的差异。</span><span class="sxs-lookup"><span data-stu-id="152ef-126">This conversion process allows you to *score*, or compare, the importance of each input regardless of the difference in values.</span></span>

 <span data-ttu-id="152ef-127">对于定型集中显示的每个状态，模型均会生成一个输入。</span><span class="sxs-lookup"><span data-stu-id="152ef-127">For each state that appears in the training set, the model generates an input.</span></span> <span data-ttu-id="152ef-128">对于离散输入或离散化输入，只要定型集中出现缺失状态，就会创建一个额外的输入，以表示“Missing”状态。</span><span class="sxs-lookup"><span data-stu-id="152ef-128">For discrete or discretized inputs, an additional input is created to represent the Missing state, if the missing state appears at least once in the training set.</span></span> <span data-ttu-id="152ef-129">对于连续输入，至多创建两个节点：一个用于缺失值（如果出现在定型数据中），一个用于现有值，即非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="152ef-129">For continuous inputs, at most two input nodes are created: one for Missing values, if present in the training data, and one input for all existing, or non-null, values.</span></span> <span data-ttu-id="152ef-130">每个输入都使用 z 分数规范化方法（ (x-μ) /StdDev.）缩放为数字格式。</span><span class="sxs-lookup"><span data-stu-id="152ef-130">Each input is scaled to a numeric format using the z-score normalization method, (x - μ)/StdDev.</span></span>

 <span data-ttu-id="152ef-131">在 z-score 规范化过程中，平均值 ( ) 和标准偏差为对整个定型集计算的结果。</span><span class="sxs-lookup"><span data-stu-id="152ef-131">During z-score normalization, the mean (μ) and standard deviation are obtained over the complete training set.</span></span>

 <span data-ttu-id="152ef-132">**连续值**</span><span class="sxs-lookup"><span data-stu-id="152ef-132">**Continuous values**</span></span>

 <span data-ttu-id="152ef-133">存在值： (X-μ) /σ//X 是要编码的实际值) </span><span class="sxs-lookup"><span data-stu-id="152ef-133">Value is present:   (X - μ)/σ // X is the actual value being encoded)</span></span>

 <span data-ttu-id="152ef-134">缺少值：-μ/σ//负 mu 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="152ef-134">Value is absent:    -   μ/σ  // negative mu divided by sigma)</span></span>

 <span data-ttu-id="152ef-135">**离散值**</span><span class="sxs-lookup"><span data-stu-id="152ef-135">**Discrete values**</span></span>

 <span data-ttu-id="152ef-136">μ = p- (之前状态的概率) </span><span class="sxs-lookup"><span data-stu-id="152ef-136">μ = p - (the prior probability of a state)</span></span>

 <span data-ttu-id="152ef-137">StdDev  = sqrt(p(1-p))</span><span class="sxs-lookup"><span data-stu-id="152ef-137">StdDev  = sqrt(p(1-p))</span></span>

 <span data-ttu-id="152ef-138">存在值： (1-μ) /σ// (1 减去 mu) 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="152ef-138">Value is present:     (1 - μ)/σ// (One minus mu) divided by sigma)</span></span>

 <span data-ttu-id="152ef-139">缺少值： (-μ) /σ//负 mu 除以 sigma) </span><span class="sxs-lookup"><span data-stu-id="152ef-139">Value is absent:     (- μ)/σ// negative mu divided by sigma)</span></span>

### <a name="understanding-logistic-regression-coefficients"></a><span data-ttu-id="152ef-140">了解逻辑回归系数</span><span class="sxs-lookup"><span data-stu-id="152ef-140">Understanding Logistic Regression Coefficients</span></span>
 <span data-ttu-id="152ef-141">虽然统计文献中的用于执行逻辑回归的方法互有区别，但一个共同的特征是评估模型的拟合度。</span><span class="sxs-lookup"><span data-stu-id="152ef-141">There are various methods in the statistical literature for performing logistic regression, but an important part of all methods is assessing the fit of the model.</span></span> <span data-ttu-id="152ef-142">其中提供有大量的拟合度统计信息，包括比值比和共变数模式。</span><span class="sxs-lookup"><span data-stu-id="152ef-142">A variety of goodness-to-fit statistics have been proposed, among them odds ratios and covariate patterns.</span></span> <span data-ttu-id="152ef-143">有关如何度量模型的拟合度的讨论已超出本主题范围，但您可以检索模型中的系数的值，并使用它们来设计您自己的拟合度度量标准。</span><span class="sxs-lookup"><span data-stu-id="152ef-143">A discussion of how to measure the fit of a model is beyond the scope of this topic; however, you can retrieve the value of the coefficients in the model and use them to design your own measures of fit.</span></span>

> [!NOTE]
>  <span data-ttu-id="152ef-144">作为逻辑回归模型的一部分而创建为的系数不表示比值比，因此，请不要如此认为。</span><span class="sxs-lookup"><span data-stu-id="152ef-144">The coefficients that are created as part of a logistic regression model do not represent odds ratios and should not be interpreted as such.</span></span>

 <span data-ttu-id="152ef-145">模型图中节点的系数表示节点的输入的加权和。</span><span class="sxs-lookup"><span data-stu-id="152ef-145">The coefficients for each node in the model graph represent a weighted sum of the inputs to that node.</span></span> <span data-ttu-id="152ef-146">在逻辑回归模型中，隐藏层为空；因此，只有一组系数，存储在输出节点中。</span><span class="sxs-lookup"><span data-stu-id="152ef-146">In a logistic regression model, the hidden layer is empty; therefore, there is only one set of coefficients, which is stored in the output nodes.</span></span> <span data-ttu-id="152ef-147">您可以使用下面的查询来检索系数的值：</span><span class="sxs-lookup"><span data-stu-id="152ef-147">You can retrieve the values of the coefficients by using the following query:</span></span>

```
SELECT FLATTENED [NODE_UNIQUE NAME],
(SELECT ATTRIBUTE_NAME< ATTRIBUTE_VALUE
FROM NODE_DISTRIBUTION) AS t
FROM <model name>.CONTENT
WHERE NODE_TYPE = 23
```

 <span data-ttu-id="152ef-148">对于每个输出值，此查询返回系数以及指回相关输入节点的 ID。</span><span class="sxs-lookup"><span data-stu-id="152ef-148">For each output value, this query returns the coefficients and an ID that points back to the related input node.</span></span> <span data-ttu-id="152ef-149">此外，还会返回包含输出和截距的行。</span><span class="sxs-lookup"><span data-stu-id="152ef-149">It also returns a row that contains the value of the output and the intercept.</span></span> <span data-ttu-id="152ef-150">每个输入 X 具有其自己的系数 (Ci) ，但嵌套表还包含 "free" 系数 (Co) ，根据以下公式计算得出：</span><span class="sxs-lookup"><span data-stu-id="152ef-150">Each input X has its own coefficient (Ci), but the nested table also contains a "free" coefficient (Co), calculated according to the following formula:</span></span>

 <span data-ttu-id="152ef-151">F (X) = X1 \* C1 + X2 \* C2 + ... + Xn \* Cn + X0</span><span class="sxs-lookup"><span data-stu-id="152ef-151">F(X) = X1\*C1 + X2\*C2 + ... +Xn\*Cn + X0</span></span>

 <span data-ttu-id="152ef-152">激活：exp(F(X)) / (1 + exp(F(X)) )</span><span class="sxs-lookup"><span data-stu-id="152ef-152">Activation: exp(F(X)) / (1 + exp(F(X)) )</span></span>

 <span data-ttu-id="152ef-153">有关详细信息，请参阅 [逻辑回归模型查询示例](logistic-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="152ef-153">For more information, see [Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md).</span></span>

## <a name="customizing-the-logistic-regression-algorithm"></a><span data-ttu-id="152ef-154">自定义逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="152ef-154">Customizing the Logistic Regression Algorithm</span></span>
 <span data-ttu-id="152ef-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法支持多个参数，这些参数可影响所生成的挖掘模型的行为、性能以及准确性。</span><span class="sxs-lookup"><span data-stu-id="152ef-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] logistic regression algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="152ef-156">您还可以通过对用作输入的列设置建模标志来修改模型。</span><span class="sxs-lookup"><span data-stu-id="152ef-156">You can also modify the behavior of the model by setting modeling flags on the columns used as input.</span></span>

### <a name="setting-algorithm-parameters"></a><span data-ttu-id="152ef-157">设置算法参数</span><span class="sxs-lookup"><span data-stu-id="152ef-157">Setting Algorithm Parameters</span></span>
 <span data-ttu-id="152ef-158">下表介绍可用于 Microsoft 逻辑回归算法的参数。</span><span class="sxs-lookup"><span data-stu-id="152ef-158">The following table describes the parameters that can be used with the Microsoft Logistic Regression algorithm.</span></span>

 <span data-ttu-id="152ef-159">HOLDOUT_PERCENTAGE 指定定型数据中用于计算维持错误的事例的百分比。</span><span class="sxs-lookup"><span data-stu-id="152ef-159">HOLDOUT_PERCENTAGE Specifies the percentage of cases within the training data used to calculate the holdout error.</span></span> <span data-ttu-id="152ef-160">在对挖掘模型定型时，HOLDOUT_PERCENTAGE 被用作停止条件的一部分。</span><span class="sxs-lookup"><span data-stu-id="152ef-160">HOLDOUT_PERCENTAGE is used as part of the stopping criteria while training the mining model.</span></span>

 <span data-ttu-id="152ef-161">默认值为 30。</span><span class="sxs-lookup"><span data-stu-id="152ef-161">The default is 30.</span></span>

 <span data-ttu-id="152ef-162">HOLDOUT_SEED 指定一个数字，以在随机确定维持数据时用来设定伪随机生成器的种子。</span><span class="sxs-lookup"><span data-stu-id="152ef-162">HOLDOUT_SEED Specifies a number to use to seed the pseudo-random generator when randomly determining the holdout data.</span></span> <span data-ttu-id="152ef-163">如果将 HOLDOUT_SEED 设置为 0，则算法将根据挖掘模型的名称生成种子，以保证模型内容在重新处理的过程中保持不变。</span><span class="sxs-lookup"><span data-stu-id="152ef-163">If HOLDOUT_SEED is set to 0, the algorithm generates the seed based on the name of the mining model, to guarantee that the model content remains the same during reprocessing.</span></span>

 <span data-ttu-id="152ef-164">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="152ef-164">The default is 0.</span></span>

 <span data-ttu-id="152ef-165">MAXIMUM_INPUT_ATTRIBUTES 定义算法在调用功能选择之前可以处理的输入属性数。</span><span class="sxs-lookup"><span data-stu-id="152ef-165">MAXIMUM_INPUT_ATTRIBUTES Defines the number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="152ef-166">如果将此值设置为 0，则表示关闭功能选择。</span><span class="sxs-lookup"><span data-stu-id="152ef-166">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="152ef-167">默认值为 255。</span><span class="sxs-lookup"><span data-stu-id="152ef-167">The default is 255.</span></span>

 <span data-ttu-id="152ef-168">MAXIMUM_OUTPUT_ATTRIBUTES 定义算法在调用功能选择之前可以处理的输出属性的数目。</span><span class="sxs-lookup"><span data-stu-id="152ef-168">MAXIMUM_OUTPUT_ATTRIBUTES Defines the number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="152ef-169">如果将此值设置为 0，则表示关闭功能选择。</span><span class="sxs-lookup"><span data-stu-id="152ef-169">Set this value to 0 to turn off feature selection.</span></span>

 <span data-ttu-id="152ef-170">默认值为 255。</span><span class="sxs-lookup"><span data-stu-id="152ef-170">The default is 255.</span></span>

 <span data-ttu-id="152ef-171">MAXIMUM_STATES 指定算法支持的最大属性状态数。</span><span class="sxs-lookup"><span data-stu-id="152ef-171">MAXIMUM_STATES Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="152ef-172">如果属性的状态数大于该最大状态数，算法将使用该属性的最常见状态，同时忽略剩余状态。</span><span class="sxs-lookup"><span data-stu-id="152ef-172">If the number of states that an attribute has is larger than the maximum number of states, the algorithm uses the most popular states of the attribute and ignores the remaining states.</span></span>

 <span data-ttu-id="152ef-173">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="152ef-173">The default is 100.</span></span>

 <span data-ttu-id="152ef-174">SAMPLE_SIZE 指定用于为模型定型的事例数。</span><span class="sxs-lookup"><span data-stu-id="152ef-174">SAMPLE_SIZE Specifies the number of cases to be used to train the model.</span></span> <span data-ttu-id="152ef-175">算法提供程序将使用该数字或不包含在 HOLDOUT_PERCENTAGE 参数指定的维持百分比中的总的事例百分比，取两者中较小值。</span><span class="sxs-lookup"><span data-stu-id="152ef-175">The algorithm provider uses either this number or the percentage of total of cases that are not included in the holdout percentage as specified by the HOLDOUT_PERCENTAGE parameter, whichever value is smaller.</span></span>

 <span data-ttu-id="152ef-176">换言之，如果将 HOLDOUT_PERCENTAGE 设置为 30，则算法将使用该参数的值或等于事例总数百分之七十的值，取两者中较小值。</span><span class="sxs-lookup"><span data-stu-id="152ef-176">In other words, if HOLDOUT_PERCENTAGE is set to 30, the algorithm will use either the value of this parameter, or a value that is equal to 70 percent of the total number of cases, whichever is smaller.</span></span>

 <span data-ttu-id="152ef-177">默认值为 10000。</span><span class="sxs-lookup"><span data-stu-id="152ef-177">The default is 10000.</span></span>

### <a name="modeling-flags"></a><span data-ttu-id="152ef-178">建模标志</span><span class="sxs-lookup"><span data-stu-id="152ef-178">Modeling Flags</span></span>
 <span data-ttu-id="152ef-179">支持以下建模标志与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法配合使用。</span><span class="sxs-lookup"><span data-stu-id="152ef-179">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>

 <span data-ttu-id="152ef-180">NOT NULL 指示列不能包含 NULL。</span><span class="sxs-lookup"><span data-stu-id="152ef-180">NOT NULL Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="152ef-181">如果 Analysis Services 在模型定型过程中遇到 Null 值，将会导致错误。</span><span class="sxs-lookup"><span data-stu-id="152ef-181">An error will result if Analysis Services encounters a null during model training.</span></span>

 <span data-ttu-id="152ef-182">适用于挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="152ef-182">Applies to mining structure columns.</span></span>

 <span data-ttu-id="152ef-183">MODEL_EXISTENCE_ONLY 意味着列将被视为具有两个可能的状态： `Missing` 和 `Existing` 。</span><span class="sxs-lookup"><span data-stu-id="152ef-183">MODEL_EXISTENCE_ONLY Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="152ef-184">Null 表示缺失值。</span><span class="sxs-lookup"><span data-stu-id="152ef-184">A null is a missing value.</span></span>

 <span data-ttu-id="152ef-185">适用于挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="152ef-185">Applies to mining model column.</span></span>

## <a name="requirements"></a><span data-ttu-id="152ef-186">要求</span><span class="sxs-lookup"><span data-stu-id="152ef-186">Requirements</span></span>
 <span data-ttu-id="152ef-187">一个逻辑回归模型必须包含一个键列、输入列和至少一个可预测列。</span><span class="sxs-lookup"><span data-stu-id="152ef-187">A logistic regression model must contain a key column, input columns, and at least one predictable column.</span></span>

### <a name="input-and-predictable-columns"></a><span data-ttu-id="152ef-188">输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="152ef-188">Input and Predictable Columns</span></span>
 <span data-ttu-id="152ef-189">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法支持下表所示的特定输入列内容类型、可预测列内容类型和建模标志。</span><span class="sxs-lookup"><span data-stu-id="152ef-189">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the specific input column content types, predictable column content types, and modeling flags that are listed in the following table.</span></span> <span data-ttu-id="152ef-190">有关内容类型在用于挖掘模型中时的含义的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="152ef-190">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>

|<span data-ttu-id="152ef-191">列</span><span class="sxs-lookup"><span data-stu-id="152ef-191">Column</span></span>|<span data-ttu-id="152ef-192">内容类型</span><span class="sxs-lookup"><span data-stu-id="152ef-192">Content types</span></span>|
|------------|-------------------|
|<span data-ttu-id="152ef-193">输入属性</span><span class="sxs-lookup"><span data-stu-id="152ef-193">Input attribute</span></span>|<span data-ttu-id="152ef-194">Continuous、Discrete、Discretized、Key、Table</span><span class="sxs-lookup"><span data-stu-id="152ef-194">Continuous, Discrete, Discretized, Key, Table</span></span>|
|<span data-ttu-id="152ef-195">可预测属性</span><span class="sxs-lookup"><span data-stu-id="152ef-195">Predictable attribute</span></span>|<span data-ttu-id="152ef-196">Continuous、Discrete、Discretized</span><span class="sxs-lookup"><span data-stu-id="152ef-196">Continuous, Discrete, Discretized</span></span>|

## <a name="see-also"></a><span data-ttu-id="152ef-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="152ef-197">See Also</span></span>
 <span data-ttu-id="152ef-198">[Microsoft 逻辑回归算法](microsoft-logistic-regression-algorithm.md)[线性回归模型查询示例](linear-regression-model-query-examples.md)[逻辑回归模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft 神经网络算法](microsoft-neural-network-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="152ef-198">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) [Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md)</span></span>


