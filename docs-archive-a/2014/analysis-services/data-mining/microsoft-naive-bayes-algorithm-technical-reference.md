---
title: Microsoft Naive Bayes 算法技术参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_DEPENDENCY_PROBABILITY parameter
- MAXIMUM_INPUT_ATTRIBUTES parameter
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- MAXIMUM_OUTPUT_ATTRIBUTES parameter
- MAXIMUM_STATES parameter
ms.assetid: a4cd47fe-2127-4930-b18f-3edd17ee9a65
author: minewiskan
ms.author: owend
ms.openlocfilehash: b03f77f1e7299ef073f0e01775d879ee0ce57f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590996"
---
# <a name="microsoft-naive-bayes-algorithm-technical-reference"></a><span data-ttu-id="73f46-102">Microsoft Naive Bayes 算法技术参考</span><span class="sxs-lookup"><span data-stu-id="73f46-102">Microsoft Naive Bayes Algorithm Technical Reference</span></span>
  <span data-ttu-id="73f46-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]Naive Bayes 算法是提供的一种分类算法， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用于预测建模。</span><span class="sxs-lookup"><span data-stu-id="73f46-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="73f46-104">该算法计算输入列与可预测列之间的条件概率，并假定列相互独立。</span><span class="sxs-lookup"><span data-stu-id="73f46-104">The algorithm calculates the conditional probability between input and predictable columns, and assumes that the columns are independent.</span></span> <span data-ttu-id="73f46-105">由于此独立性假设，所以取名为 Naive Bayes。</span><span class="sxs-lookup"><span data-stu-id="73f46-105">This assumption of independence leads to the name Naive Bayes.</span></span>  
  
## <a name="implementation-of-the-microsoft-naive-bayes-algorithm"></a><span data-ttu-id="73f46-106">Microsoft Naive Bayes 算法的实现</span><span class="sxs-lookup"><span data-stu-id="73f46-106">Implementation of the Microsoft Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="73f46-107">和其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法相比，此算法所需运算量较少，因而有助于快速生成挖掘模型，从而发现输入列与可预测列之间的关系。</span><span class="sxs-lookup"><span data-stu-id="73f46-107">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="73f46-108">此算法会考虑每对输入属性值和输出属性值。</span><span class="sxs-lookup"><span data-stu-id="73f46-108">The algorithm considers each pair of input attribute values and output attribute values.</span></span>  
  
 <span data-ttu-id="73f46-109">有关贝叶斯定理的数学性质的说明不属于本文档的讨论范围；有关详细信息，请参阅 Microsoft Research 文章，标题为： [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029)（了解 Bayesian 网络：知识和统计数据的组合）。</span><span class="sxs-lookup"><span data-stu-id="73f46-109">A description of the mathematical properties of Bayes Theorem is beyond the scope of this documentation; for more information, see the paper by Microsoft Research titled [Learning Bayesian Networks: The Combination of Knowledge and Statistical Data](https://go.microsoft.com/fwlink/?LinkId=207029).</span></span>  
  
 <span data-ttu-id="73f46-110">有关如何调整所有模型中的概率以解释可能的缺失值的说明，请参阅[缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="73f46-110">For a description of how probabilities in all models are adjusted to account for potential missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="73f46-111">特征选择</span><span class="sxs-lookup"><span data-stu-id="73f46-111">Feature Selection</span></span>  
 <span data-ttu-id="73f46-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法会自动执行功能选择，以限制生成模型时要考虑的值的数量。</span><span class="sxs-lookup"><span data-stu-id="73f46-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm performs automatic feature selection to limit the number of values that are considered when building the model.</span></span> <span data-ttu-id="73f46-113">有关详细信息，请参阅[功能选择（数据挖掘）](feature-selection-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="73f46-113">For more information, see [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>  
  
|<span data-ttu-id="73f46-114">算法</span><span class="sxs-lookup"><span data-stu-id="73f46-114">Algorithm</span></span>|<span data-ttu-id="73f46-115">分析方法</span><span class="sxs-lookup"><span data-stu-id="73f46-115">Method of analysis</span></span>|<span data-ttu-id="73f46-116">注释</span><span class="sxs-lookup"><span data-stu-id="73f46-116">Comments</span></span>|  
|---------------|------------------------|--------------|  
|<span data-ttu-id="73f46-117">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="73f46-117">Naive Bayes</span></span>|<span data-ttu-id="73f46-118">Shannon 平均信息量</span><span class="sxs-lookup"><span data-stu-id="73f46-118">Shannon's Entropy</span></span><br /><br /> <span data-ttu-id="73f46-119">Bayesian with K2 Prior</span><span class="sxs-lookup"><span data-stu-id="73f46-119">Bayesian with K2 Prior</span></span><br /><br /> <span data-ttu-id="73f46-120">使用统一先验的 Bayesian Dirichlet（默认）</span><span class="sxs-lookup"><span data-stu-id="73f46-120">Bayesian Dirichlet with uniform prior (default)</span></span>|<span data-ttu-id="73f46-121">Naive Bayes 仅接受离散或离散化的属性，因此它不能使用兴趣性分数。</span><span class="sxs-lookup"><span data-stu-id="73f46-121">Naive Bayes only accepts discrete or discretized attributes; therefore, it cannot use the interestingness score.</span></span>|  
  
 <span data-ttu-id="73f46-122">该算法的设计目的是最小化处理时间，并高效地选择最为重要的属性；但您可以通过设置下面的参数来控制其所用的数据：</span><span class="sxs-lookup"><span data-stu-id="73f46-122">The algorithm is designed to minimize processing time and efficiently select the attributes that have the greatest importance; however, you can control the data that is used by the algorithm by setting parameters as follows:</span></span>  
  
-   <span data-ttu-id="73f46-123">若要限制用作输入的值的数量，请降低 MAXIMUM_INPUT_ATTRIBUTES 的值。</span><span class="sxs-lookup"><span data-stu-id="73f46-123">To limit the values that are used as inputs, decrease the value of MAXIMUM_INPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="73f46-124">若要限制模型要分析的属性的数量，请降低 MAXIMUM_OUTPUT_ATTRIBUTES 的值。</span><span class="sxs-lookup"><span data-stu-id="73f46-124">To limit the number of attributes analyzed by the model, decrease the value of MAXIMUM_OUTPUT_ATTRIBUTES.</span></span>  
  
-   <span data-ttu-id="73f46-125">若要限制要为属性考虑的值的数量，请降低 MINIMUM_STATES 的值。</span><span class="sxs-lookup"><span data-stu-id="73f46-125">To limit the number of values that can be considered for any one attribute, decrease the value of MINIMUM_STATES.</span></span>  
  
## <a name="customizing-the-naive-bayes-algorithm"></a><span data-ttu-id="73f46-126">自定义 Naive Bayes 算法</span><span class="sxs-lookup"><span data-stu-id="73f46-126">Customizing the Naive Bayes Algorithm</span></span>  
 <span data-ttu-id="73f46-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法支持多个参数，这些参数可影响所生成的挖掘模型的行为、性能以及准确性。</span><span class="sxs-lookup"><span data-stu-id="73f46-127">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="73f46-128">您还可以对模型列设置建模标志来控制数据的处理方式，或者对挖掘结构设置标志来指定如何处理缺失值或 Null 值。</span><span class="sxs-lookup"><span data-stu-id="73f46-128">You can also set modeling flags on the model columns to control how data is processed, or set flags on the mining structure to specify how missing values or nulls should be handled.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="73f46-129">设置算法参数</span><span class="sxs-lookup"><span data-stu-id="73f46-129">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="73f46-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法支持多个参数，这些参数可影响所生成的挖掘模型的性能和准确性。</span><span class="sxs-lookup"><span data-stu-id="73f46-130">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports several parameters that affect the performance and accuracy of the resulting mining model.</span></span> <span data-ttu-id="73f46-131">下表对各参数进行了说明：</span><span class="sxs-lookup"><span data-stu-id="73f46-131">The following table describes each parameter.</span></span>  
  
 <span data-ttu-id="73f46-132">*MAXIMUM_INPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="73f46-132">*MAXIMUM_INPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="73f46-133">指定算法在调用功能选择之前可以处理的最大输入属性数。</span><span class="sxs-lookup"><span data-stu-id="73f46-133">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="73f46-134">如果将此值设置为 0，则为输入属性禁用功能选择。</span><span class="sxs-lookup"><span data-stu-id="73f46-134">Setting this value to 0 disables feature selection for input attributes.</span></span>  
  
 <span data-ttu-id="73f46-135">默认值为 255。</span><span class="sxs-lookup"><span data-stu-id="73f46-135">The default is 255.</span></span>  
  
 <span data-ttu-id="73f46-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span><span class="sxs-lookup"><span data-stu-id="73f46-136">*MAXIMUM_OUTPUT_ATTRIBUTES*</span></span>  
 <span data-ttu-id="73f46-137">指定算法在调用功能选择之前可以处理的最大输出属性数。</span><span class="sxs-lookup"><span data-stu-id="73f46-137">Specifies the maximum number of output attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="73f46-138">如果将此值设置为 0，则为输出属性禁用功能选择。</span><span class="sxs-lookup"><span data-stu-id="73f46-138">Setting this value to 0 disables feature selection for output attributes.</span></span>  
  
 <span data-ttu-id="73f46-139">默认值为 255。</span><span class="sxs-lookup"><span data-stu-id="73f46-139">The default is 255.</span></span>  
  
 <span data-ttu-id="73f46-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="73f46-140">*MINIMUM_DEPENDENCY_PROBABILITY*</span></span>  
 <span data-ttu-id="73f46-141">指定输入属性和输出属性之间的最小依赖关系概率。</span><span class="sxs-lookup"><span data-stu-id="73f46-141">Specifies the minimum dependency probability between input and output attributes.</span></span> <span data-ttu-id="73f46-142">该值用于限制算法生成的内容大小。</span><span class="sxs-lookup"><span data-stu-id="73f46-142">This value is used to limit the size of the content that is generated by the algorithm.</span></span> <span data-ttu-id="73f46-143">此属性可以设置为 0 到 1 之间的值。</span><span class="sxs-lookup"><span data-stu-id="73f46-143">This property can be set from 0 to 1.</span></span> <span data-ttu-id="73f46-144">较大的值减少模型内容中的特性数。</span><span class="sxs-lookup"><span data-stu-id="73f46-144">Larger values reduce the number of attributes in the content of the model.</span></span>  
  
 <span data-ttu-id="73f46-145">默认值为 0.5。</span><span class="sxs-lookup"><span data-stu-id="73f46-145">The default is 0.5.</span></span>  
  
 <span data-ttu-id="73f46-146">*MAXIMUM_STATES*</span><span class="sxs-lookup"><span data-stu-id="73f46-146">*MAXIMUM_STATES*</span></span>  
 <span data-ttu-id="73f46-147">指定算法支持的最大属性状态数。</span><span class="sxs-lookup"><span data-stu-id="73f46-147">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="73f46-148">如果属性的状态数大于最大状态数，则算法将使用属性的最常用状态，并将剩余状态视为缺失。</span><span class="sxs-lookup"><span data-stu-id="73f46-148">If the number of states that an attribute has is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as missing.</span></span>  
  
 <span data-ttu-id="73f46-149">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="73f46-149">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="73f46-150">建模标志</span><span class="sxs-lookup"><span data-stu-id="73f46-150">Modeling Flags</span></span>  
 <span data-ttu-id="73f46-151">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法支持下列建模标志。</span><span class="sxs-lookup"><span data-stu-id="73f46-151">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the following modeling flags.</span></span> <span data-ttu-id="73f46-152">创建挖掘结构或挖掘模型时，定义建模标志以指定分析期间如何处理每列中的值。</span><span class="sxs-lookup"><span data-stu-id="73f46-152">When you create the mining structure or mining model, you define modeling flags to specify how values in each column are handled during analysis.</span></span> <span data-ttu-id="73f46-153">有关详细信息，请参阅[建模标志（数据挖掘）](modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="73f46-153">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
|<span data-ttu-id="73f46-154">建模标志</span><span class="sxs-lookup"><span data-stu-id="73f46-154">Modeling Flag</span></span>|<span data-ttu-id="73f46-155">说明</span><span class="sxs-lookup"><span data-stu-id="73f46-155">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="73f46-156">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="73f46-156">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="73f46-157">表示该列将被视为具有两个可能状态：Missing 和 Existing。</span><span class="sxs-lookup"><span data-stu-id="73f46-157">Means that the column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="73f46-158">Null 表示缺失值。</span><span class="sxs-lookup"><span data-stu-id="73f46-158">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="73f46-159">适用于挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="73f46-159">Applies to mining model column.</span></span>|  
|<span data-ttu-id="73f46-160">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="73f46-160">NOT NULL</span></span>|<span data-ttu-id="73f46-161">指示该列不能包含 Null。</span><span class="sxs-lookup"><span data-stu-id="73f46-161">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="73f46-162">如果 Analysis Services 在模型定型过程中遇到 Null 值，将会导致错误。</span><span class="sxs-lookup"><span data-stu-id="73f46-162">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="73f46-163">适用于挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="73f46-163">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73f46-164">要求</span><span class="sxs-lookup"><span data-stu-id="73f46-164">Requirements</span></span>  
 <span data-ttu-id="73f46-165">一个 Naive Bayes 树模型必须包含一个键列、至少一个可预测列和至少一个输入列。</span><span class="sxs-lookup"><span data-stu-id="73f46-165">A Naive Bayes tree model must contain a key column, at least one predictable attribute, and at least one input attribute.</span></span> <span data-ttu-id="73f46-166">所有属性均不能为连续属性；如果数据包含连续数值数据，则将会被忽略或离散化。</span><span class="sxs-lookup"><span data-stu-id="73f46-166">No attribute can be continuous; if your data contains continuous numeric data, it will be ignored or discretized.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="73f46-167">输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="73f46-167">Input and Predictable Columns</span></span>  
 <span data-ttu-id="73f46-168">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法支持下表中列出的特定输入列和可预测列。</span><span class="sxs-lookup"><span data-stu-id="73f46-168">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="73f46-169">有关内容类型在用于挖掘模型中时的含义的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="73f46-169">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="73f46-170">列</span><span class="sxs-lookup"><span data-stu-id="73f46-170">Column</span></span>|<span data-ttu-id="73f46-171">内容类型</span><span class="sxs-lookup"><span data-stu-id="73f46-171">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="73f46-172">输入属性</span><span class="sxs-lookup"><span data-stu-id="73f46-172">Input attribute</span></span>|<span data-ttu-id="73f46-173">Cyclical、Discrete、Discretized、Key、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="73f46-173">Cyclical, Discrete, Discretized, Key, Table, and Ordered</span></span>|  
|<span data-ttu-id="73f46-174">可预测属性</span><span class="sxs-lookup"><span data-stu-id="73f46-174">Predictable attribute</span></span>|<span data-ttu-id="73f46-175">Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="73f46-175">Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="73f46-176">支持 Cyclical 和 Ordered 内容类型，但算法会将它们视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="73f46-176">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f46-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73f46-177">See Also</span></span>  
 <span data-ttu-id="73f46-178">[Microsoft Naive Bayes 算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="73f46-178">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 <span data-ttu-id="73f46-179">[Naive Bayes 模型查询示例](naive-bayes-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="73f46-179">[Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) </span></span>  
 [<span data-ttu-id="73f46-180">Naive Bayes 模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="73f46-180">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
