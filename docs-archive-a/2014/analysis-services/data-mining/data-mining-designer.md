---
title: 数据挖掘设计器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820cde158dfabff525081060369daace0e83c8dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577922"
---
# <a name="data-mining-designer"></a><span data-ttu-id="96888-102">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="96888-102">Data Mining Designer</span></span>
  <span data-ttu-id="96888-103">数据挖掘设计器是在中使用挖掘模型的主要环境 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="96888-103">Data Mining Designer is the primary environment in which you work with mining models in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="96888-104">您可以通过选择一个现有挖掘结构或使用数据挖掘向导创建一个新的挖掘结构和挖掘模型来访问该设计器。</span><span class="sxs-lookup"><span data-stu-id="96888-104">You can access the designer either by selecting an existing mining structure, or by using the Data Mining Wizard to create a new mining structure and mining model.</span></span> <span data-ttu-id="96888-105">可以使用数据挖掘设计器执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="96888-105">You can use Data Mining Designer to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="96888-106">修改最初由数据挖掘向导创建的挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="96888-106">Modify the mining structure and the mining model that were initially created by the Data Mining Wizard.</span></span>  
  
-   <span data-ttu-id="96888-107">根据现有的挖掘结构创建新模型。</span><span class="sxs-lookup"><span data-stu-id="96888-107">Create new models based on an existing mining structure.</span></span>  
  
-   <span data-ttu-id="96888-108">定型和浏览挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="96888-108">Train and browse mining models.</span></span>  
  
-   <span data-ttu-id="96888-109">通过使用准确性图表比较模型。</span><span class="sxs-lookup"><span data-stu-id="96888-109">Compare models by using accuracy charts.</span></span>  
  
-   <span data-ttu-id="96888-110">根据挖掘模型创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="96888-110">Create prediction queries based on mining models.</span></span>  
  
## <a name="mining-structure-tab"></a><span data-ttu-id="96888-111">“挖掘结构”选项卡</span><span class="sxs-lookup"><span data-stu-id="96888-111">Mining Structure Tab</span></span>  
 <span data-ttu-id="96888-112">使用 **“挖掘结构”** 选项卡添加列和修改现有挖掘结构的属性。</span><span class="sxs-lookup"><span data-stu-id="96888-112">Use the **Mining Structure** tab to add columns and modify the properties of an existing mining structure.</span></span> <span data-ttu-id="96888-113">下列任务和主题提供有关使用挖掘结构的详细信息：</span><span class="sxs-lookup"><span data-stu-id="96888-113">The following tasks and topics provide more information about working with mining structures:</span></span>  
  
 [<span data-ttu-id="96888-114">挖掘结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="96888-114">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="96888-115">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="96888-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a><span data-ttu-id="96888-116">“挖掘模型”选项卡</span><span class="sxs-lookup"><span data-stu-id="96888-116">Mining Models Tab</span></span>  
 <span data-ttu-id="96888-117">使用 **“挖掘模型”** 选项卡可管理现有的挖掘模型以及创建新模型。</span><span class="sxs-lookup"><span data-stu-id="96888-117">Use the **Mining Models** tab to manage existing mining models and to create new models.</span></span> <span data-ttu-id="96888-118">挖掘模型始终基于现有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="96888-118">Mining models are always based on an existing mining structure .</span></span>  
  
 <span data-ttu-id="96888-119">在“挖掘模型”\*\*\*\* 选项卡中，可以更改算法类型、添加或删除与模型结构关联的列、调整算法特定的列属性、指定挖掘模型列用法以及调整与挖掘模型关联的算法参数。</span><span class="sxs-lookup"><span data-stu-id="96888-119">In the **Mining Models** tab, you can change the algorithm type, add or remove columns that are associated with the model structure, adjust algorithm-specific column properties, specify the mining model column usage, and adjust algorithm parameters that are associated with the mining model.</span></span> <span data-ttu-id="96888-120">还可以将挖掘结构与所选模型或所有关联模型一起处理。</span><span class="sxs-lookup"><span data-stu-id="96888-120">You can also process the mining structure together with selected models or with all the associated models.</span></span>  
  
 <span data-ttu-id="96888-121">有关使用挖掘模型的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="96888-121">See the following topics for more information about working with mining models:</span></span>  
  
 [<span data-ttu-id="96888-122">挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="96888-122">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="96888-123">挖掘模型任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="96888-123">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a><span data-ttu-id="96888-124">“挖掘模型查看器”选项卡</span><span class="sxs-lookup"><span data-stu-id="96888-124">Mining Model Viewer Tab</span></span>  
 <span data-ttu-id="96888-125">使用 **“挖掘模型查看器”** 选项卡以可视化方式浏览挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="96888-125">Use the **Mining Model Viewer** tab to visually explore your mining models.</span></span> <span data-ttu-id="96888-126">每个挖掘模型都与显示特定于该模型的内容的一个自定义查看器相关联。</span><span class="sxs-lookup"><span data-stu-id="96888-126">Each mining model is associated with a custom viewer that displays content that is specific to that model.</span></span> <span data-ttu-id="96888-127">还可以使用内容查看器查看挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="96888-127">You can also view mining model content by using the content viewer.</span></span>  
  
 <span data-ttu-id="96888-128">有关使用数据挖掘查看器浏览挖掘模型的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="96888-128">See the following topics for more information about exploring mining models with the data mining viewers:</span></span>  
  
 [<span data-ttu-id="96888-129">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="96888-129">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
 [<span data-ttu-id="96888-130">挖掘模型查看器任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="96888-130">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a><span data-ttu-id="96888-131">“挖掘准确性图表”选项卡</span><span class="sxs-lookup"><span data-stu-id="96888-131">Mining Accuracy Chart Tab</span></span>  
 <span data-ttu-id="96888-132">使用 **“挖掘准确性图表”** 选项卡测试单个挖掘模型的预测准确性，或比较挖掘结构中包含的多个挖掘模型的效率。</span><span class="sxs-lookup"><span data-stu-id="96888-132">Use the **Mining Accuracy Chart** tab to test the predictive accuracy of a single mining model, or to compare the effectiveness of multiple mining models contained within a mining structure.</span></span> <span data-ttu-id="96888-133">该选项卡包含用于筛选数据、选择挖掘模型以及在提升图、利润图或分类矩阵中显示结果的工具。</span><span class="sxs-lookup"><span data-stu-id="96888-133">The tab contains tools for filtering the data, selecting mining models, and displaying the results in a lift chart, profit chart, or classification matrix.</span></span>  
  
 <span data-ttu-id="96888-134">有关测试和验证挖掘模型的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="96888-134">See the following topics for more information about testing and validating mining models:</span></span>  
  
 [<span data-ttu-id="96888-135">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="96888-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
 [<span data-ttu-id="96888-136">测试和验证任务和操作指南（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="96888-136">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a><span data-ttu-id="96888-137">“挖掘模型预测”选项卡</span><span class="sxs-lookup"><span data-stu-id="96888-137">Mining Model Prediction Tab</span></span>  
 <span data-ttu-id="96888-138">“挖掘模型预测”\*\*\*\* 选项卡包含预测查询生成器，可以使用此生成器创建数据挖掘扩展插件 (DMX) 预测查询。</span><span class="sxs-lookup"><span data-stu-id="96888-138">The **Mining Model Prediction** tab includes Prediction Query Builder, which you can use to create a Data Mining Extensions (DMX) prediction query.</span></span> <span data-ttu-id="96888-139">该选项卡包含用于指定挖掘模型和输入表、将挖掘模型中的列映射到输入表中的列、向查询中添加函数以及为各个列指定条件的工具。</span><span class="sxs-lookup"><span data-stu-id="96888-139">The tab contains tools for specifying mining models and input tables, mapping the columns in the mining model to columns in the input table, adding functions to a query, and specifying criteria for each column.</span></span>  
  
 <span data-ttu-id="96888-140">设计查询后，可以使用该选项卡中的不同视图来显示查询结果并手动修改查询。</span><span class="sxs-lookup"><span data-stu-id="96888-140">After you design a query, you can use different views in the tab to display the results of the query and to modify the query manually.</span></span> <span data-ttu-id="96888-141">还可以将查询结果保存到数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="96888-141">You can also save the results of the query to a table in a database.</span></span>  
  
 <span data-ttu-id="96888-142">有关创建数据挖掘查询的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="96888-142">See the following topics for more information about creating data mining queries:</span></span>  
  
 [<span data-ttu-id="96888-143">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="96888-143">Data Mining Queries</span></span>](data-mining-queries.md)  
  
 [<span data-ttu-id="96888-144">数据挖掘查询任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="96888-144">Data Mining Query Tasks and How-tos</span></span>](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a><span data-ttu-id="96888-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96888-145">See Also</span></span>  
 [<span data-ttu-id="96888-146">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="96888-146">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
