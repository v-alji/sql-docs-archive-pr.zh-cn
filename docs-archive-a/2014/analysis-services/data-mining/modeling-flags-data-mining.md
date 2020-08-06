---
title: 数据挖掘)  (建模标志 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- data types [data mining]
- REGRESSOR flag
- MODEL_EXISTENCE_ONLY flag
- REGRESSOR column
- columns [data mining], modeling flags
- NOT NULL modeling flag
- modeling flags [data mining]
- null values [Analysis Services]
- MODEL_EXISTENCE_ONLY column
- coding [Data Mining]
ms.assetid: 8826d5ce-9ba8-4490-981b-39690ace40a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f1c802f6503b84ff4f6879c18d3bffebb46d7ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687371"
---
# <a name="modeling-flags-data-mining"></a><span data-ttu-id="1eb93-102">建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1eb93-102">Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="1eb93-103">您可以使用中的建模标志 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 为数据挖掘算法提供有关事例表中定义的数据的其他信息。</span><span class="sxs-lookup"><span data-stu-id="1eb93-103">You can use modeling flags in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide additional information to a data mining algorithm about the data that is defined in a case table.</span></span> <span data-ttu-id="1eb93-104">该算法可以使用该附加信息生成更精确的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1eb93-104">The algorithm can use this information to build a more accurate data mining model.</span></span>  
  
 <span data-ttu-id="1eb93-105">某些建模标志是在挖掘结构级别定义的，而其他标志则是在挖掘模型列级别定义的。</span><span class="sxs-lookup"><span data-stu-id="1eb93-105">Some modeling flags are defined at the level of the mining structure, whereas others are defined at the level of the mining model column.</span></span> <span data-ttu-id="1eb93-106">例如，可以将 `NOT NULL` 建模标志与挖掘结构列一起使用。</span><span class="sxs-lookup"><span data-stu-id="1eb93-106">For example, the `NOT NULL` modeling flag is used with mining structure columns.</span></span> <span data-ttu-id="1eb93-107">您可以根据用于创建模型的算法，在挖掘模型列上定义其他建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-107">You can define additional modeling flags on the mining model columns, depending on the algorithm you use to create the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1eb93-108">除了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]预定义的这些标志以外，第三方插件还可能具有其他建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-108">Third-party plug-ins might have other modeling flags, in addition to those pre-defined by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="list-of-modeling-flags"></a><span data-ttu-id="1eb93-109">建模标志列表</span><span class="sxs-lookup"><span data-stu-id="1eb93-109">List of Modeling Flags</span></span>  
 <span data-ttu-id="1eb93-110">下面的列表介绍了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中支持的建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-110">The following list describes the modeling flags that are supported in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1eb93-111">有关特定算法支持的建模标志的信息，请参阅用于创建模型的算法的技术参考主题。</span><span class="sxs-lookup"><span data-stu-id="1eb93-111">For information about modeling flags that are supported by specific algorithms, see the technical reference topic for the algorithm that was used to create the model.</span></span>  
  
 `NOT NULL`  
 <span data-ttu-id="1eb93-112">指示属性列的值不应包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="1eb93-112">Indicates that the values for the attribute column should never contain a null value.</span></span> <span data-ttu-id="1eb93-113">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在模型定型过程中发现该属性列的值为 Null 值，则将出现错误。</span><span class="sxs-lookup"><span data-stu-id="1eb93-113">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null value for this attribute column during the model training process.</span></span>  
  
 <span data-ttu-id="1eb93-114">**MODEL_EXISTENCE_ONLY**</span><span class="sxs-lookup"><span data-stu-id="1eb93-114">**MODEL_EXISTENCE_ONLY**</span></span>  
 <span data-ttu-id="1eb93-115">指示该列将被视为具有两种状态：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="1eb93-115">Indicates that the column will be treated as having two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="1eb93-116">如果该值为 `NULL`，将被视为 Missing。</span><span class="sxs-lookup"><span data-stu-id="1eb93-116">If the value is `NULL`, it is treated as Missing.</span></span> <span data-ttu-id="1eb93-117">MODEL_EXISTENCE_ONLY 标志将应用于可预测属性，并且大多数算法都支持该标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-117">The MODEL_EXISTENCE_ONLY flag is applied to the predictable attribute and is supported by most algorithms.</span></span>  
  
 <span data-ttu-id="1eb93-118">实际上，将 MODEL_EXISTENCE_ONLY 标志设置为 `True` 会更改值的表示形式，以使得仅存在两种状态：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="1eb93-118">In effect, setting the MODEL_EXISTENCE_ONLY flag to `True` changes the representation of the values such that there are only two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="1eb93-119">将所有非 Missing 状态合并为一个 `Existing` 值。</span><span class="sxs-lookup"><span data-stu-id="1eb93-119">All the non-missing states are combined into a single `Existing` value.</span></span>  
  
 <span data-ttu-id="1eb93-120">此建模标志的典型用法是指示以下情况中的属性：`NULL` 状态具有隐含意义；`NOT NULL` 状态的显式值可能不与列中有任意值时一样重要。</span><span class="sxs-lookup"><span data-stu-id="1eb93-120">A typical use for this modeling flag would be in attributes for which the `NULL` state has an implicit meaning, and the explicit value of the `NOT NULL` state might not be as important as the fact that the column has any value.</span></span> <span data-ttu-id="1eb93-121">例如，如果某个合同永远不会签署，则 [DateContractSigned] 列可能为 `NULL`，但如果该合同已签署，则 [DateContractSigned] 列为 `NOT NULL`。</span><span class="sxs-lookup"><span data-stu-id="1eb93-121">For example, a [DateContractSigned] column might be `NULL` if a contract was never signed and `NOT NULL` if the contract was signed.</span></span> <span data-ttu-id="1eb93-122">因此，如果模型的目的是用于预测合同是否会签署，则可以使用 MODEL_EXISTENCE_ONLY 标志忽略 `NOT NULL` 事例中的准确日期值，而只区分联系人为 `Missing` 或 `Existing` 的事例。</span><span class="sxs-lookup"><span data-stu-id="1eb93-122">Therefore, if the purpose of the model is to predict whether a contract will be signed, you can use the MODEL_EXISTENCE_ONLY flag to ignore the exact date value in the `NOT NULL` cases and distinguish only between cases where a contract is `Missing` or `Existing`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1eb93-123">Missing 是算法所使用的一种特殊状态，不同于列中文本值 “Missing”。</span><span class="sxs-lookup"><span data-stu-id="1eb93-123">Missing is a special state used by the algorithm, and differs from the text value "Missing" in a column.</span></span> <span data-ttu-id="1eb93-124">有关详细信息，请参阅 [缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)预定义的这些标志以外，第三方插件还可能具有其他建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-124">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="1eb93-125">指示该列在处理期间适合用作回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-125">Indicates that the column is a candidate for used as a regressor during processing.</span></span> <span data-ttu-id="1eb93-126">该标志是在挖掘模型列中定义的，只能将其应用于具有连续数值数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="1eb93-126">This flag is defined on a mining model column, and can only be applied to columns that have a continuous numeric data type.</span></span> <span data-ttu-id="1eb93-127">有关使用此标志的详细信息，请参阅本主题中的[回归量建模标志的使用](#bkmk_UseRegressors)部分。</span><span class="sxs-lookup"><span data-stu-id="1eb93-127">For more information about the use of this flag, see the section in this topic, [Uses of the REGRESSOR Modeling Flag](#bkmk_UseRegressors).</span></span>  
  
## <a name="viewing-and-changing-modeling-flags"></a><span data-ttu-id="1eb93-128">查看和更改建模标志</span><span class="sxs-lookup"><span data-stu-id="1eb93-128">Viewing and Changing Modeling Flags</span></span>  
 <span data-ttu-id="1eb93-129">通过查看结构或模型的属性，可以在数据挖掘设计器中查看与挖掘结构列或模型列关联的建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-129">You can view the modeling flags associated with a mining structure column or model column in Data Mining Designer by viewing the properties of the structure or model.</span></span>  
  
 <span data-ttu-id="1eb93-130">若要确定已应用于当前挖掘结构的建模标志，可使用与如下查询创建一个针对数据挖掘架构行集的查询，用于仅返回结构列的建模标志：</span><span class="sxs-lookup"><span data-stu-id="1eb93-130">To determine which modeling flags have been applied to the current mining structure, you can create a query against the data mining schema rowset that returns the modeling flags for just the structure columns, by using a query like the following:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_STRUCTURE_COLUMNS  
WHERE STRUCTURE_NAME = '<structure name>'  
```  
  
 <span data-ttu-id="1eb93-131">可通过使用数据挖掘设计器并编辑关联列的属性，来添加或更改模型中使用的建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-131">You can add or change the modeling flags used in a model by using the Data Mining Designer and editing the properties of the associated columns.</span></span> <span data-ttu-id="1eb93-132">此类更改需要重新处理结构或模型。</span><span class="sxs-lookup"><span data-stu-id="1eb93-132">Such changes require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="1eb93-133">可使用 DMX 或使用 AMO 或 XMLA 脚本来指定新挖掘结构或挖掘模型中的建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-133">You can specify modeling flags in a new mining structure or mining model by using DMX, or by using AMO or XMLA scripts.</span></span> <span data-ttu-id="1eb93-134">但是，不能使用 DMX 更改现有挖掘模型和结构中使用的建模标志。</span><span class="sxs-lookup"><span data-stu-id="1eb93-134">However, you cannot change the modeling flags used in an existing mining model and structure by using DMX.</span></span> <span data-ttu-id="1eb93-135">您必须使用语法 `ALTER MINING STRUCTURE....ADD MINING MODEL`创建新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1eb93-135">You must create a new mining model by using the syntax, `ALTER MINING STRUCTURE....ADD MINING MODEL`.</span></span>  
  
##  <a name="uses-of-the-regressor-modeling-flag"></a><a name="bkmk_UseRegressors"></a> <span data-ttu-id="1eb93-136">使用 REGRESSOR 建模标志</span><span class="sxs-lookup"><span data-stu-id="1eb93-136">Uses of the REGRESSOR Modeling Flag</span></span>  
 <span data-ttu-id="1eb93-137">当对某个列设置 REGRESSOR 建模标志时，指示的是列包含潜在回归量的算法。</span><span class="sxs-lookup"><span data-stu-id="1eb93-137">When you set the REGRESSOR modeling flag on a column, you are indicating to the algorithm that the column contains potential regressors.</span></span> <span data-ttu-id="1eb93-138">模型中使用的实际回归量是由算法确定的。</span><span class="sxs-lookup"><span data-stu-id="1eb93-138">The actual regressors that are used in the model are determined by the algorithm.</span></span> <span data-ttu-id="1eb93-139">如果潜在回归量不对可预测属性建模，则可以忽略该潜在回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-139">A potential regressor can be discarded if it does not model the predictable attribute.</span></span>  
  
 <span data-ttu-id="1eb93-140">使用数据挖掘向导构建模型时，会将所有的连续输入列都标记为潜在回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-140">When you build a model by using the Data Mining wizard, all continuous input columns are flagged as possible regressors.</span></span> <span data-ttu-id="1eb93-141">因此，即使没有为某个列显式设置 REGRESSOR 标记，该列也可能会在模型中用作回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-141">Therefore, even if you do not explicitly set the REGRESSOR flag on a column, the column might be used as a regressor in the model.</span></span>  
  
 <span data-ttu-id="1eb93-142">您可以通过对挖掘模型的架构行集执行查询来确定处理的模型中实际使用的回归量，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="1eb93-142">You can determine the regressors that were actually used in the processed model by performing a query against the schema rowset for the mining model, as shown in the following example:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_COLUMNS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="1eb93-143">**注意** 如果修改某个挖掘模型并将某列的内容类型从连续更改为离散，则必须手动更改该挖掘列上的标志，然后重新处理该模型。</span><span class="sxs-lookup"><span data-stu-id="1eb93-143">**Note** If you modify a mining model and change the content type of a column from continuous to discrete, you must manually change the flag on the mining column and then reprocess the model.</span></span>  
  
### <a name="regressors-in-linear-regression-models"></a><span data-ttu-id="1eb93-144">线性回归模型中的回归量</span><span class="sxs-lookup"><span data-stu-id="1eb93-144">Regressors in Linear Regression Models</span></span>  
 <span data-ttu-id="1eb93-145">线性回归模型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法。</span><span class="sxs-lookup"><span data-stu-id="1eb93-145">Linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="1eb93-146">即使不使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法，任何决策树模型也都可以包含表示连续属性的回归的树或节点。</span><span class="sxs-lookup"><span data-stu-id="1eb93-146">Even if you do not use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, any decision tree model can contain a tree or nodes that represents a regression on a continuous attribute.</span></span>  
  
 <span data-ttu-id="1eb93-147">因此，在这些模型中，您无需指定连续列表示回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-147">Therefore, in these models you do not need to specify that a continuous column represents a regressor.</span></span> <span data-ttu-id="1eb93-148">即使不对列设置 REGRESSOR 标志， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法也会将数据集分区成具有有意义模式的区域。</span><span class="sxs-lookup"><span data-stu-id="1eb93-148">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm will partition the dataset into regions with meaningful patterns even if you do not set the REGRESSOR flag on the column.</span></span> <span data-ttu-id="1eb93-149">其差异是：如果设置建模标志，此算法将尝试查找以下形式的回归等式，以适合树中节点的模式。</span><span class="sxs-lookup"><span data-stu-id="1eb93-149">The difference is that when you set the modeling flag, the algorithm will try to find regression equations of the following form to fit the patterns in the nodes of  the tree.</span></span>  
  
 <span data-ttu-id="1eb93-150">a\*C1 + b\*C2 + ...</span><span class="sxs-lookup"><span data-stu-id="1eb93-150">a\*C1 + b\*C2 + ...</span></span>  
  
 <span data-ttu-id="1eb93-151">然后，将对剩余的总和进行计算，如果偏差过大，则在树中执行强制拆分。</span><span class="sxs-lookup"><span data-stu-id="1eb93-151">Then, the sum of the residuals is calculated, and if the deviation is too great, a split is forced in the tree.</span></span>  
  
 <span data-ttu-id="1eb93-152">例如，如果是将 **Income** 用作属性来预测客户购买行为，并对该列设置了 REGRESSOR 建模标志，则该算法将使用标准回归公式先尝试适合 **Income** 值。</span><span class="sxs-lookup"><span data-stu-id="1eb93-152">For example, if you are predicting customer purchasing behavior using **Income** as an attribute, and set the REGRESSOR modeling flag on the column, the algorithm would first try to fit the **Income** values by using a standard regression formula.</span></span> <span data-ttu-id="1eb93-153">如果偏差过大，则放弃使用回归公式，并根据其他一些属性对树进行拆分。</span><span class="sxs-lookup"><span data-stu-id="1eb93-153">If the deviation is too great, the regression formula is abandoned and the tree would be split on some other attribute.</span></span> <span data-ttu-id="1eb93-154">拆分后，该决策树算法随后尝试适合每个分支中收入的回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-154">The decision tree algorithm would then try fit a regressor for income in each of the branches after the split.</span></span>  
  
 <span data-ttu-id="1eb93-155">可以使用 FORCE_REGRESSOR 参数来保证该算法使用特定的回归量。</span><span class="sxs-lookup"><span data-stu-id="1eb93-155">You can use the FORCE_REGRESSOR parameter to guarantee that the algorithm will use a particular regressor.</span></span> <span data-ttu-id="1eb93-156">此参数可以与决策树算法和线性回归算法一起使用。</span><span class="sxs-lookup"><span data-stu-id="1eb93-156">This parameter can be used with the Decision Trees algorithm and Linear Regression algorithm.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1eb93-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1eb93-157">Related Tasks</span></span>  
 <span data-ttu-id="1eb93-158">使用以下链接了解有关使用建模标志的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1eb93-158">Use the following links to learn more about using modeling flags.</span></span>  
  
|<span data-ttu-id="1eb93-159">任务</span><span class="sxs-lookup"><span data-stu-id="1eb93-159">Task</span></span>|<span data-ttu-id="1eb93-160">主题</span><span class="sxs-lookup"><span data-stu-id="1eb93-160">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1eb93-161">使用数据挖掘设计器编辑建模标志</span><span class="sxs-lookup"><span data-stu-id="1eb93-161">Edit modeling flags by using the Data Mining Designer</span></span>|[<span data-ttu-id="1eb93-162">查看或更改建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1eb93-162">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="1eb93-163">指定算法的提示以建议可能的回归量</span><span class="sxs-lookup"><span data-stu-id="1eb93-163">Specify a hint to the algorithm to recommend likely regressors</span></span>|[<span data-ttu-id="1eb93-164">在模型中指定用作回归量的列</span><span class="sxs-lookup"><span data-stu-id="1eb93-164">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)|  
|<span data-ttu-id="1eb93-165">请参阅特定算法支持的建模标志（在每个算法参考主题的“建模标志”部分中）</span><span class="sxs-lookup"><span data-stu-id="1eb93-165">See the modeling flags supported by specific algorithms (in the Modeling Flags section for each algorithm reference topic)</span></span>|[<span data-ttu-id="1eb93-166">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1eb93-166">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)|  
|<span data-ttu-id="1eb93-167">了解有关挖掘结构列以及可对其设置的属性的更多信息</span><span class="sxs-lookup"><span data-stu-id="1eb93-167">Learn more about mining structure columns and the properties that you can set on them</span></span>|[<span data-ttu-id="1eb93-168">挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="1eb93-168">Mining Structure Columns</span></span>](mining-structure-columns.md)|  
|<span data-ttu-id="1eb93-169">了解可在模型级别应用的挖掘模型列和建模标志</span><span class="sxs-lookup"><span data-stu-id="1eb93-169">Learn about mining model columns and modeling flags that can be applied at the model level</span></span>|[<span data-ttu-id="1eb93-170">挖掘模型列</span><span class="sxs-lookup"><span data-stu-id="1eb93-170">Mining Model Columns</span></span>](mining-model-columns.md)|  
|<span data-ttu-id="1eb93-171">请参阅用于在 DMX 语句中使用建模标志的语法</span><span class="sxs-lookup"><span data-stu-id="1eb93-171">See syntax for  working with modeling  flags in DMX statements</span></span>|[<span data-ttu-id="1eb93-172">建模标志 (DMX)</span><span class="sxs-lookup"><span data-stu-id="1eb93-172">Modeling Flags &#40;DMX&#41;</span></span>](/sql/dmx/modeling-flags-dmx)|  
|<span data-ttu-id="1eb93-173">了解缺失值以及如何处理它们</span><span class="sxs-lookup"><span data-stu-id="1eb93-173">Understand missing values and how to work with  them</span></span>|[<span data-ttu-id="1eb93-174">缺失值（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1eb93-174">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)|  
|<span data-ttu-id="1eb93-175">了解如何管理模型和结构以及设置用法属性</span><span class="sxs-lookup"><span data-stu-id="1eb93-175">Learn about managing models and structures and setting usage properties</span></span>|[<span data-ttu-id="1eb93-176">移动数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="1eb93-176">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)|  
  
  
