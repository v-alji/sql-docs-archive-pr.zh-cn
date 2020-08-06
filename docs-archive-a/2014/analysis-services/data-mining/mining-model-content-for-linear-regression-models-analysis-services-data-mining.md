---
title: 线性回归模型的挖掘模型内容 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- mining model content, linear regression models
- regression algorithms [Analysis Services]
ms.assetid: a6abcb75-524e-4e0a-a375-c10475ac0a9d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cb41cf0053f236b4bda8d4520030603a391d1c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690241"
---
# <a name="mining-model-content-for-linear-regression-models-analysis-services---data-mining"></a><span data-ttu-id="fbef5-102">线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="fbef5-102">Mining Model Content for Linear Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="fbef5-103">本主题介绍使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="fbef5-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="fbef5-104">有关所有模型类型的挖掘模型内容的常规说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fbef5-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-linear-regression-model"></a><span data-ttu-id="fbef5-105">了解线性回归模型的结构</span><span class="sxs-lookup"><span data-stu-id="fbef5-105">Understanding the Structure of a Linear Regression Model</span></span>  
 <span data-ttu-id="fbef5-106">线性回归模型的结构非常简单。</span><span class="sxs-lookup"><span data-stu-id="fbef5-106">A linear regression model has an extremely simple structure.</span></span> <span data-ttu-id="fbef5-107">每个模型都具有一个表示该模型及其元数据的单一父节点，以及一个回归树节点 (NODE_TYPE = 25) ，其中包含每个可预测属性的回归公式。</span><span class="sxs-lookup"><span data-stu-id="fbef5-107">Each model has a single parent node that represents the model and its metadata, and a regression tree node (NODE_TYPE = 25) that contains the regression formula for each predictable attribute.</span></span>  
  
 <span data-ttu-id="fbef5-108">![线性回归的模型内容结构](../media/modelcontentstructure-linreg.gif "线性回归的模型内容结构")</span><span class="sxs-lookup"><span data-stu-id="fbef5-108">![Structure of model for linear regression](../media/modelcontentstructure-linreg.gif "Structure of model for linear regression")</span></span>  
  
 <span data-ttu-id="fbef5-109">线性回归模型与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树使用相同的算法，但线性回归模型使用不同的参数来约束树，并且仅接受连续属性作为输入。</span><span class="sxs-lookup"><span data-stu-id="fbef5-109">Linear regression models use the same algorithm as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees, but different parameters are used to constrain the tree, and only continuous attributes are accepted as inputs.</span></span> <span data-ttu-id="fbef5-110">但是，由于线性回归模型基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法，线性回归模型使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树查看器来显示。</span><span class="sxs-lookup"><span data-stu-id="fbef5-110">However, because linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, linear regression models are displayed by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Tree Viewer.</span></span> <span data-ttu-id="fbef5-111">有关详细信息，请参阅 [使用 Microsoft 树查看器浏览模型](browse-a-model-using-the-microsoft-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="fbef5-111">For information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="fbef5-112">以下部分将说明如何解释回归公式节点中的信息。</span><span class="sxs-lookup"><span data-stu-id="fbef5-112">The next section explains how to interpret information in the regression formula node.</span></span> <span data-ttu-id="fbef5-113">该信息不仅适用于线性回归模型，还适用于将回归作为树的一部分包括在其中的决策树模型。</span><span class="sxs-lookup"><span data-stu-id="fbef5-113">This information applies not only to linear regression models, but also to decision trees models that contain regressions in a portion of the tree.</span></span>  
  
## <a name="model-content-for-a-linear-regression-model"></a><span data-ttu-id="fbef5-114">线性回归模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="fbef5-114">Model Content for a Linear Regression Model</span></span>  
 <span data-ttu-id="fbef5-115">本部分提供的详细信息和示例仅针对挖掘模型内容中与线性回归有特殊关系的列。</span><span class="sxs-lookup"><span data-stu-id="fbef5-115">This section provides detail and examples only for those columns in the mining model content that have particular relevance for linear regression.</span></span>  
  
 <span data-ttu-id="fbef5-116">有关架构行集中的通用列的信息，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fbef5-116">For information about general-purpose columns in the schema rowset, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="fbef5-117">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="fbef5-117">MODEL_CATALOG</span></span>  
 <span data-ttu-id="fbef5-118">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="fbef5-118">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="fbef5-119">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-119">MODEL_NAME</span></span>  
 <span data-ttu-id="fbef5-120">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="fbef5-120">Name of the model.</span></span>  
  
 <span data-ttu-id="fbef5-121">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-121">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="fbef5-122">**根节点：** 空白</span><span class="sxs-lookup"><span data-stu-id="fbef5-122">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="fbef5-123">**回归节点：** 可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="fbef5-123">**Regression node:** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="fbef5-124">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-124">NODE_NAME</span></span>  
 <span data-ttu-id="fbef5-125">始终与 NODE_UNIQUE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="fbef5-125">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="fbef5-126">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-126">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="fbef5-127">此模型中节点的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="fbef5-127">A unique identifier for the node within the model.</span></span> <span data-ttu-id="fbef5-128">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="fbef5-128">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="fbef5-129">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fbef5-129">NODE_TYPE</span></span>  
 <span data-ttu-id="fbef5-130">线性回归模型输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="fbef5-130">A linear regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="fbef5-131">节点类型 ID</span><span class="sxs-lookup"><span data-stu-id="fbef5-131">Node Type ID</span></span>|<span data-ttu-id="fbef5-132">类型</span><span class="sxs-lookup"><span data-stu-id="fbef5-132">Type</span></span>|<span data-ttu-id="fbef5-133">说明</span><span class="sxs-lookup"><span data-stu-id="fbef5-133">Description</span></span>|  
|------------------|----------|-----------------|  
|<span data-ttu-id="fbef5-134">25</span><span class="sxs-lookup"><span data-stu-id="fbef5-134">25</span></span>|<span data-ttu-id="fbef5-135">回归树根节点</span><span class="sxs-lookup"><span data-stu-id="fbef5-135">Regression tree root</span></span>|<span data-ttu-id="fbef5-136">包含描述输入和输出变量之间的关系的公式。</span><span class="sxs-lookup"><span data-stu-id="fbef5-136">Contains the formula that describes the relationship between the input and output variable.</span></span>|  
  
 <span data-ttu-id="fbef5-137">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fbef5-137">NODE_CAPTION</span></span>  
 <span data-ttu-id="fbef5-138">与节点关联的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="fbef5-138">A label or a caption associated with the node.</span></span> <span data-ttu-id="fbef5-139">此属性主要用于显示目的。</span><span class="sxs-lookup"><span data-stu-id="fbef5-139">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="fbef5-140">**根节点：** 空白</span><span class="sxs-lookup"><span data-stu-id="fbef5-140">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="fbef5-141">**回归节点：** 全部。</span><span class="sxs-lookup"><span data-stu-id="fbef5-141">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="fbef5-142">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="fbef5-142">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="fbef5-143">对节点所具有的子节点数的估计。</span><span class="sxs-lookup"><span data-stu-id="fbef5-143">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="fbef5-144">**根节点：** 指示回归节点的数目。</span><span class="sxs-lookup"><span data-stu-id="fbef5-144">**Root node:** Indicates the number of regression nodes.</span></span> <span data-ttu-id="fbef5-145">为模型中的每个可预测属性创建一个回归节点。</span><span class="sxs-lookup"><span data-stu-id="fbef5-145">One regression node is created for each predictable attribute in the model.</span></span>  
  
 <span data-ttu-id="fbef5-146">**回归节点：** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="fbef5-146">**Regression node:** Always 0.</span></span>  
  
 <span data-ttu-id="fbef5-147">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-147">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="fbef5-148">节点的父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="fbef5-148">The unique name of the node's parent.</span></span> <span data-ttu-id="fbef5-149">根级别上的任何节点均返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="fbef5-149">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="fbef5-150">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fbef5-150">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="fbef5-151">节点的说明。</span><span class="sxs-lookup"><span data-stu-id="fbef5-151">A description of the node.</span></span>  
  
 <span data-ttu-id="fbef5-152">**根节点：** 空白</span><span class="sxs-lookup"><span data-stu-id="fbef5-152">**Root node:** Blank</span></span>  
  
 <span data-ttu-id="fbef5-153">**回归节点：** 全部。</span><span class="sxs-lookup"><span data-stu-id="fbef5-153">**Regression node:** All.</span></span>  
  
 <span data-ttu-id="fbef5-154">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="fbef5-154">NODE_RULE</span></span>  
 <span data-ttu-id="fbef5-155">不用于线性回归模型。</span><span class="sxs-lookup"><span data-stu-id="fbef5-155">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="fbef5-156">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="fbef5-156">MARGINAL_RULE</span></span>  
 <span data-ttu-id="fbef5-157">不用于线性回归模型。</span><span class="sxs-lookup"><span data-stu-id="fbef5-157">Not used for linear regression models.</span></span>  
  
 <span data-ttu-id="fbef5-158">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fbef5-158">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="fbef5-159">与此节点相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="fbef5-159">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="fbef5-160">**根节点：** 0</span><span class="sxs-lookup"><span data-stu-id="fbef5-160">**Root node:** 0</span></span>  
  
 <span data-ttu-id="fbef5-161">**回归节点：** 1</span><span class="sxs-lookup"><span data-stu-id="fbef5-161">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="fbef5-162">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fbef5-162">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="fbef5-163">从父节点到达该节点的概率。</span><span class="sxs-lookup"><span data-stu-id="fbef5-163">The probability of reaching the node from the parent node.</span></span>  
  
 <span data-ttu-id="fbef5-164">**根节点：** 0</span><span class="sxs-lookup"><span data-stu-id="fbef5-164">**Root node:** 0</span></span>  
  
 <span data-ttu-id="fbef5-165">**回归节点：** 1</span><span class="sxs-lookup"><span data-stu-id="fbef5-165">**Regression node:** 1</span></span>  
  
 <span data-ttu-id="fbef5-166">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="fbef5-166">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="fbef5-167">提供有关节点中的值的统计信息的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="fbef5-167">A nested table that provides statistics about the values in the node.</span></span>  
  
 <span data-ttu-id="fbef5-168">**根节点：** 0</span><span class="sxs-lookup"><span data-stu-id="fbef5-168">**Root node:** 0</span></span>  
  
 <span data-ttu-id="fbef5-169">**回归节点：** 包含用于生成回归公式的元素的表。</span><span class="sxs-lookup"><span data-stu-id="fbef5-169">**Regression node:** A table that contains the elements used to build the regression formula.</span></span> <span data-ttu-id="fbef5-170">回归节点包含下列值类型：</span><span class="sxs-lookup"><span data-stu-id="fbef5-170">A regression node contains the following value types:</span></span>  
  
|<span data-ttu-id="fbef5-171">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="fbef5-171">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="fbef5-172">1（缺失）</span><span class="sxs-lookup"><span data-stu-id="fbef5-172">1 (Missing)</span></span>|  
|<span data-ttu-id="fbef5-173">3（连续）</span><span class="sxs-lookup"><span data-stu-id="fbef5-173">3 (Continuous)</span></span>|  
|<span data-ttu-id="fbef5-174">7（系数）</span><span class="sxs-lookup"><span data-stu-id="fbef5-174">7 (Coefficient)</span></span>|  
|<span data-ttu-id="fbef5-175">8（得分）</span><span class="sxs-lookup"><span data-stu-id="fbef5-175">8 (Score Gain)</span></span>|  
|<span data-ttu-id="fbef5-176">9（统计信息）</span><span class="sxs-lookup"><span data-stu-id="fbef5-176">9 (Statistics)</span></span>|  
|<span data-ttu-id="fbef5-177">11（截距）</span><span class="sxs-lookup"><span data-stu-id="fbef5-177">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="fbef5-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fbef5-178">NODE_SUPPORT</span></span>  
 <span data-ttu-id="fbef5-179">支持此节点的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="fbef5-179">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="fbef5-180">**根节点：** 0</span><span class="sxs-lookup"><span data-stu-id="fbef5-180">**Root node:** 0</span></span>  
  
 <span data-ttu-id="fbef5-181">**回归节点：** 定型事例的计数。</span><span class="sxs-lookup"><span data-stu-id="fbef5-181">**Regression node:** Count of training cases.</span></span>  
  
 <span data-ttu-id="fbef5-182">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="fbef5-182">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="fbef5-183">可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="fbef5-183">Name of predictable attribute.</span></span>  
  
 <span data-ttu-id="fbef5-184">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="fbef5-184">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="fbef5-185">与 NODE_PROBABILITY 相同</span><span class="sxs-lookup"><span data-stu-id="fbef5-185">Same as NODE_PROBABILITY</span></span>  
  
 <span data-ttu-id="fbef5-186">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fbef5-186">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="fbef5-187">用于显示的标签。</span><span class="sxs-lookup"><span data-stu-id="fbef5-187">Label used for display purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbef5-188">备注</span><span class="sxs-lookup"><span data-stu-id="fbef5-188">Remarks</span></span>  
 <span data-ttu-id="fbef5-189">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法创建模型时，数据挖掘引擎创建决策树模型的特殊实例，并提供约束树的参数，将树约束为在单个节点中包含所有定型数据。</span><span class="sxs-lookup"><span data-stu-id="fbef5-189">When you create a model by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, the data mining engine creates a special instance of a decision trees model and supplies parameters that constrain the tree to contain all the training data in a single node.</span></span> <span data-ttu-id="fbef5-190">将标记所有连续输入并将其视为潜在回归量，但仅将适合数据的回归量作为回归量保留在最终模型中。</span><span class="sxs-lookup"><span data-stu-id="fbef5-190">All continuous inputs are flagged and evaluated as potential regressors, but only those regressors that fit the data are retained as regressors in the final model.</span></span> <span data-ttu-id="fbef5-191">分析过程要么为每个回归量各生成一个回归公式，要么根本不生成任何回归公式。</span><span class="sxs-lookup"><span data-stu-id="fbef5-191">The analysis produces either a single regression formula for each regressor or no regression formula at all.</span></span>  
  
 <span data-ttu-id="fbef5-192">你可以在“挖掘图例”中查看完整的回归公式，方法是在 [Microsoft 树查看器](browse-a-model-using-the-microsoft-tree-viewer.md)中单击“(全部)”节点。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fbef5-192">You can view the complete regression formula in the **Mining Legend**, by clicking the **(All)** node in the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="fbef5-193">此外，在创建包括连续可预测属性的决策树模型时，有时树具有的回归节点会共享回归树节点的属性。</span><span class="sxs-lookup"><span data-stu-id="fbef5-193">Also, when you create a decision trees model that includes a continuous predictable attribute, sometimes the tree has regression nodes that share the properties of regression tree nodes.</span></span>  
  
##  <a name="node-distribution-for-continuous-attributes"></a><a name="NodeDist_Regression"></a><span data-ttu-id="fbef5-194">连续属性的节点分布</span><span class="sxs-lookup"><span data-stu-id="fbef5-194">Node Distribution for Continuous Attributes</span></span>  
 <span data-ttu-id="fbef5-195">回归节点中大多数重要信息都包含在 NODE_DISTRIBUTION 表中。</span><span class="sxs-lookup"><span data-stu-id="fbef5-195">Most of the important information in a regression node is contained in the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="fbef5-196">下面的示例演示 NODE_DISTRIBUTION 表的布局。</span><span class="sxs-lookup"><span data-stu-id="fbef5-196">The following example illustrates the layout of the NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="fbef5-197">在此示例中，使用目标邮件挖掘结构创建的线性回归模型基于客户的年龄预测其收入。</span><span class="sxs-lookup"><span data-stu-id="fbef5-197">In this example, the Targeted Mailing mining structure has been used to create a linear regression model that predicts customer income based on age.</span></span> <span data-ttu-id="fbef5-198">该模型仅用于演示目的，因为使用现有 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 示例数据和挖掘结构可以方便地生成该模型。</span><span class="sxs-lookup"><span data-stu-id="fbef5-198">The model is for the purpose of illustration only, because it can be built easily using the existing [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample data and mining structure.</span></span>  
  
|<span data-ttu-id="fbef5-199">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fbef5-199">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="fbef5-200">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="fbef5-200">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="fbef5-201">Support</span><span class="sxs-lookup"><span data-stu-id="fbef5-201">SUPPORT</span></span>|<span data-ttu-id="fbef5-202">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fbef5-202">PROBABILITY</span></span>|<span data-ttu-id="fbef5-203">方差</span><span class="sxs-lookup"><span data-stu-id="fbef5-203">VARIANCE</span></span>|<span data-ttu-id="fbef5-204">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="fbef5-204">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="fbef5-205">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="fbef5-205">Yearly Income</span></span>|<span data-ttu-id="fbef5-206">Missing</span><span class="sxs-lookup"><span data-stu-id="fbef5-206">Missing</span></span>|<span data-ttu-id="fbef5-207">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-207">0</span></span>|<span data-ttu-id="fbef5-208">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="fbef5-208">0.000457142857142857</span></span>|<span data-ttu-id="fbef5-209">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-209">0</span></span>|<span data-ttu-id="fbef5-210">1</span><span class="sxs-lookup"><span data-stu-id="fbef5-210">1</span></span>|  
|<span data-ttu-id="fbef5-211">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="fbef5-211">Yearly Income</span></span>|<span data-ttu-id="fbef5-212">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="fbef5-212">57220.8876687257</span></span>|<span data-ttu-id="fbef5-213">17484</span><span class="sxs-lookup"><span data-stu-id="fbef5-213">17484</span></span>|<span data-ttu-id="fbef5-214">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="fbef5-214">0.999542857142857</span></span>|<span data-ttu-id="fbef5-215">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="fbef5-215">1041275619.52776</span></span>|<span data-ttu-id="fbef5-216">3</span><span class="sxs-lookup"><span data-stu-id="fbef5-216">3</span></span>|  
|<span data-ttu-id="fbef5-217">年限</span><span class="sxs-lookup"><span data-stu-id="fbef5-217">Age</span></span>|<span data-ttu-id="fbef5-218">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="fbef5-218">471.687717702463</span></span>|<span data-ttu-id="fbef5-219">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-219">0</span></span>|<span data-ttu-id="fbef5-220">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-220">0</span></span>|<span data-ttu-id="fbef5-221">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="fbef5-221">126.969442359327</span></span>|<span data-ttu-id="fbef5-222">7</span><span class="sxs-lookup"><span data-stu-id="fbef5-222">7</span></span>|  
|<span data-ttu-id="fbef5-223">年限</span><span class="sxs-lookup"><span data-stu-id="fbef5-223">Age</span></span>|<span data-ttu-id="fbef5-224">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="fbef5-224">234.680904692439</span></span>|<span data-ttu-id="fbef5-225">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-225">0</span></span>|<span data-ttu-id="fbef5-226">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-226">0</span></span>|<span data-ttu-id="fbef5-227">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-227">0</span></span>|<span data-ttu-id="fbef5-228">8</span><span class="sxs-lookup"><span data-stu-id="fbef5-228">8</span></span>|  
|<span data-ttu-id="fbef5-229">年限</span><span class="sxs-lookup"><span data-stu-id="fbef5-229">Age</span></span>|<span data-ttu-id="fbef5-230">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="fbef5-230">45.4269617936399</span></span>|<span data-ttu-id="fbef5-231">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-231">0</span></span>|<span data-ttu-id="fbef5-232">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-232">0</span></span>|<span data-ttu-id="fbef5-233">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="fbef5-233">126.969442359327</span></span>|<span data-ttu-id="fbef5-234">9</span><span class="sxs-lookup"><span data-stu-id="fbef5-234">9</span></span>|  
||<span data-ttu-id="fbef5-235">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="fbef5-235">35793.5477381267</span></span>|<span data-ttu-id="fbef5-236">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-236">0</span></span>|<span data-ttu-id="fbef5-237">0</span><span class="sxs-lookup"><span data-stu-id="fbef5-237">0</span></span>|<span data-ttu-id="fbef5-238">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="fbef5-238">1012968919.28372</span></span>|<span data-ttu-id="fbef5-239">11</span><span class="sxs-lookup"><span data-stu-id="fbef5-239">11</span></span>|  
  
 <span data-ttu-id="fbef5-240">NODE_DISTRIBUTION 表包含多个行，每个行按变量进行分组。</span><span class="sxs-lookup"><span data-stu-id="fbef5-240">The NODE_DISTRIBUTION table contains multiple rows, each grouped by a variable.</span></span> <span data-ttu-id="fbef5-241">前两个行的值类型始终为 1 和 3，用于描述目标属性。</span><span class="sxs-lookup"><span data-stu-id="fbef5-241">The first two rows are always value types 1 and 3, and describe the target attribute.</span></span> <span data-ttu-id="fbef5-242">\*\* 后续行提供有关特定“回归量”的公式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fbef5-242">The succeeding rows provide details about the formula for a particular *regressor*.</span></span> <span data-ttu-id="fbef5-243">回归量是与输出变量具有线性关系的输入变量。</span><span class="sxs-lookup"><span data-stu-id="fbef5-243">A regressor is an input variable that has a linear relationship with the output variable.</span></span> <span data-ttu-id="fbef5-244">您可以拥有多个回归量，并且每个回归量将针对系数 (VALUETYPE = 7)、得分 (VALUETYPE = 8) 和统计信息 (VALUETYPE = 9) 包含单独的行。</span><span class="sxs-lookup"><span data-stu-id="fbef5-244">You can have multiple regressors, and each regressor will have a separate row for the coefficient (VALUETYPE = 7), score gain (VALUETYPE = 8), and statistics (VALUETYPE = 9).</span></span> <span data-ttu-id="fbef5-245">最后，表还具有一个包含公式的截距 (VALUETYPE = 11) 的行。</span><span class="sxs-lookup"><span data-stu-id="fbef5-245">Finally, the table has a row that contains the intercept of the equation (VALUETYPE = 11).</span></span>  
  
### <a name="elements-of-the-regression-formula"></a><span data-ttu-id="fbef5-246">回归公式的元素</span><span class="sxs-lookup"><span data-stu-id="fbef5-246">Elements of the Regression Formula</span></span>  
 <span data-ttu-id="fbef5-247">NODE_DISTRIBUTION 嵌套表将回归公式的每个元素包含在一个单独的行中。</span><span class="sxs-lookup"><span data-stu-id="fbef5-247">The nested NODE_DISTRIBUTION table contains each element of the regression formula in a separate row.</span></span> <span data-ttu-id="fbef5-248">示例结果的前两行数据包含有关可预测属性 **Yearly Income**的信息，该属性建立了依赖变量的模型。</span><span class="sxs-lookup"><span data-stu-id="fbef5-248">The first two rows of data in the example results contain information about the predictable attribute, **Yearly Income**, which models the dependent variable.</span></span> <span data-ttu-id="fbef5-249">SUPPORT 列显示支持该属性的以下两种状态的事例计数： **Yearly Income** 值可用或缺少 **Yearly Income** 值。</span><span class="sxs-lookup"><span data-stu-id="fbef5-249">The SUPPORT column shows the count of cases in support of the two states of this attribute: either a **Yearly Income** value was available, or the **Yearly Income** value was missing.</span></span>  
  
 <span data-ttu-id="fbef5-250">VARIANCE 列提供可预测属性的计算出的方差。</span><span class="sxs-lookup"><span data-stu-id="fbef5-250">The VARIANCE column tells you the computed variance of the predictable attribute.</span></span> <span data-ttu-id="fbef5-251">\*\* “方差”可度量示例中的值在给定预期分布情况下的离散程度。</span><span class="sxs-lookup"><span data-stu-id="fbef5-251">*Variance* is a measure of how scattered the values are in a sample, given an expected distribution.</span></span> <span data-ttu-id="fbef5-252">此处的方差通过取平均值偏差的平方的平均值计算而来。</span><span class="sxs-lookup"><span data-stu-id="fbef5-252">Variance here is calculated by taking the average of the squared deviation from the mean.</span></span> <span data-ttu-id="fbef5-253">方差的平方根也称为标准偏差。</span><span class="sxs-lookup"><span data-stu-id="fbef5-253">The square root of the variance is also known as standard deviation.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="fbef5-254">未提供标准偏差，但是可通过计算轻松得出其值。</span><span class="sxs-lookup"><span data-stu-id="fbef5-254">does not provide the standard deviation but you can easily calculate it.</span></span>  
  
 <span data-ttu-id="fbef5-255">对于每个回归量，输出包括三行。</span><span class="sxs-lookup"><span data-stu-id="fbef5-255">For each regressor, three rows are output.</span></span> <span data-ttu-id="fbef5-256">它们包括系数、得分和回归量统计信息。</span><span class="sxs-lookup"><span data-stu-id="fbef5-256">They contain the coefficient, score gain, and regressor statistics.</span></span>  
  
 <span data-ttu-id="fbef5-257">最后，表还包含一个提供公式的截距的行。</span><span class="sxs-lookup"><span data-stu-id="fbef5-257">Finally, the table contains a row that provides the intercept for the equation.</span></span>  
  
#### <a name="coefficient"></a><span data-ttu-id="fbef5-258">系数</span><span class="sxs-lookup"><span data-stu-id="fbef5-258">Coefficient</span></span>  
 <span data-ttu-id="fbef5-259">对于每个回归量，会计算出一个系数 (VALUETYPE = 7)。</span><span class="sxs-lookup"><span data-stu-id="fbef5-259">For each regressor, a coefficient (VALUETYPE = 7) is calculated.</span></span> <span data-ttu-id="fbef5-260">系数自身显示在 ATTRIBUTE_VALUE 列中，而 VARIANCE 列显示系数的方差。</span><span class="sxs-lookup"><span data-stu-id="fbef5-260">The coefficient itself appears in the ATTRIBUTE_VALUE column, whereas the VARIANCE column tells you the variance for the coefficient.</span></span> <span data-ttu-id="fbef5-261">计算系数的目的在于实现最大程度的线性。</span><span class="sxs-lookup"><span data-stu-id="fbef5-261">The coefficients are calculated so as to maximize linearity.</span></span>  
  
#### <a name="score-gain"></a><span data-ttu-id="fbef5-262">得分</span><span class="sxs-lookup"><span data-stu-id="fbef5-262">Score Gain</span></span>  
 <span data-ttu-id="fbef5-263">每个回归量的得分 (VALUETYPE = 8) 表示属性的兴趣性分数。</span><span class="sxs-lookup"><span data-stu-id="fbef5-263">The score gain (VALUETYPE = 8) for each regressor represents the interestingness score of the attribute.</span></span> <span data-ttu-id="fbef5-264">您可以使用此值来估计多个回归量的有用性。</span><span class="sxs-lookup"><span data-stu-id="fbef5-264">You can use this value to estimate the usefulness of multiple regressors.</span></span>  
  
#### <a name="statistics"></a><span data-ttu-id="fbef5-265">统计信息</span><span class="sxs-lookup"><span data-stu-id="fbef5-265">Statistics</span></span>  
 <span data-ttu-id="fbef5-266">回归量统计信息 (VALUETYPE = 9) 是其事例具有相应值的属性的平均值。</span><span class="sxs-lookup"><span data-stu-id="fbef5-266">The regressor statistic (VALUETYPE = 9) is the mean for the attribute for cases that have a value.</span></span> <span data-ttu-id="fbef5-267">ATTRIBUTE_VALUE 列包含平均值自身，而 VARIANCE 列包含平均值偏差的总和。</span><span class="sxs-lookup"><span data-stu-id="fbef5-267">The ATTRIBUTE_VALUE column contains the mean itself, whereas the VARIANCE column contains the sum of deviations from the mean.</span></span>  
  
#### <a name="intercept"></a><span data-ttu-id="fbef5-268">截距</span><span class="sxs-lookup"><span data-stu-id="fbef5-268">Intercept</span></span>  
 <span data-ttu-id="fbef5-269">通常，回归公式中的“截距”(VALUETYPE = 11) 或“残差”指示当输入属性为 0 时可预测属性的值。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="fbef5-269">Normally, the *intercept* (VALUETYPE = 11) or *residual* in a regression equation tells you the value of the predictable attribute, at the point where the input attribute, is 0.</span></span> <span data-ttu-id="fbef5-270">在大多数情况下都不可能发生这种情况，该情况可能产生不够直观的结果。</span><span class="sxs-lookup"><span data-stu-id="fbef5-270">In many cases, this might not happen, and could lead to counterintuitive results.</span></span>  
  
 <span data-ttu-id="fbef5-271">例如，在根据年龄预测收入的模型中，了解 0 岁时的收入毫无用处。</span><span class="sxs-lookup"><span data-stu-id="fbef5-271">For example, in a model that predicts income based on age, it is useless to learn the income at age 0.</span></span> <span data-ttu-id="fbef5-272">在现实生活中，了解与平均值有关的人类行为通常更有用。</span><span class="sxs-lookup"><span data-stu-id="fbef5-272">In real-life, it is typically more useful to know about the behavior of the line with respect to average values.</span></span> <span data-ttu-id="fbef5-273">因此，会 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 修改截距，以表示与平均值的关系中的每个回归量。</span><span class="sxs-lookup"><span data-stu-id="fbef5-273">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifies the intercept to express each regressor in a relationship with the mean.</span></span>  
  
 <span data-ttu-id="fbef5-274">在挖掘模型内容中很难显示此调整，但是如果在 **Microsoft 树查看器** 的 **“挖掘图例”** 中查看完成后的公式，则可以很清楚地显示这一调整。</span><span class="sxs-lookup"><span data-stu-id="fbef5-274">This adjustment is difficult to see in the mining model content, but is apparent if you view the completed equation in the **Mining Legend** of the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="fbef5-275">回归公式从点 0 移向表示平均值的点。</span><span class="sxs-lookup"><span data-stu-id="fbef5-275">The regression formula is shifted away from the 0 point to the point that represents the mean.</span></span> <span data-ttu-id="fbef5-276">这样，可以根据当前数据呈现一个更直观的视图。</span><span class="sxs-lookup"><span data-stu-id="fbef5-276">This presents a view that is more intuitive given the current data.</span></span>  
  
 <span data-ttu-id="fbef5-277">因此，假定平均年龄约为 45，回归公式的截距 (VALUETYPE = 11) 则指示平均收入。</span><span class="sxs-lookup"><span data-stu-id="fbef5-277">Therefore, assuming that the mean age is around 45, the intercept (VALUETYPE = 11) for the regression formula tells you the mean income.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbef5-278">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbef5-278">See Also</span></span>  
 <span data-ttu-id="fbef5-279">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fbef5-279">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="fbef5-280">[Microsoft 线性回归算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="fbef5-280">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="fbef5-281">[Microsoft 线性回归算法技术参考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fbef5-281">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="fbef5-282">线性回归模型查询示例</span><span class="sxs-lookup"><span data-stu-id="fbef5-282">Linear Regression Model Query Examples</span></span>](linear-regression-model-query-examples.md)  
  
  
