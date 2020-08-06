---
title: 第4课：浏览目标邮件模型 (基本的数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8659350b126164e06550acdbecec04bb07499c55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691385"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a><span data-ttu-id="b85f3-102">第 4 课：浏览 Targeted Mailing 模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b85f3-102">Lesson 4: Exploring the Targeted Mailing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b85f3-103">在处理项目中的模型后，可以浏览它们以查找所关注的趋势。</span><span class="sxs-lookup"><span data-stu-id="b85f3-103">After the models in your project have been processed, you can explore them to look for interesting trends.</span></span> <span data-ttu-id="b85f3-104">因为仅仅查看数字难以发现复杂的模式，SQL Server 数据挖掘提供一些可视工具，可帮助您调查数据和理解算法在数据内发现的规则和关系。</span><span class="sxs-lookup"><span data-stu-id="b85f3-104">Because patterns can be complex and difficult simply by looking at numbers, SQL Server Data Mining provides some visual tools that help you investigate the data and understand the rules and relationships that the algorithms have discovered within the data.</span></span> <span data-ttu-id="b85f3-105">您还可以使用各种准确性测试来在部署之前验证您的数据集或发现哪个模型的性能最佳。</span><span class="sxs-lookup"><span data-stu-id="b85f3-105">You can also use a variety of accuracy tests to validate your dataset or discover which model performs best before you deploy it.</span></span>  
  
 <span data-ttu-id="b85f3-106">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 浏览模型时，所创建的每个模型都将列在数据挖掘设计器的 "**挖掘模型查看器**" 选项卡中。</span><span class="sxs-lookup"><span data-stu-id="b85f3-106">When you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to explore your models, each model you created is listed in the **Mining Model Viewer** tab in Data Mining Designer.</span></span> <span data-ttu-id="b85f3-107">您可以使用查看器来浏览模型。</span><span class="sxs-lookup"><span data-stu-id="b85f3-107">You can use the viewers to explore the models.</span></span> <span data-ttu-id="b85f3-108">这些查看器也在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中提供。</span><span class="sxs-lookup"><span data-stu-id="b85f3-108">These viewers are also available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b85f3-109">用于在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中生成模型的每种算法将返回不同类型的结果。</span><span class="sxs-lookup"><span data-stu-id="b85f3-109">Each algorithm that you used to build a model in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] returns a different type of result.</span></span> <span data-ttu-id="b85f3-110">因此，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 为每种计算机学习模型提供自定义查看器。</span><span class="sxs-lookup"><span data-stu-id="b85f3-110">Therefore, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides custom viewers for each type of machine learning model.</span></span>  
  
 <span data-ttu-id="b85f3-111">如果要了解详细信息， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 还提供了一个名为 "**一般内容树查看器**" 的 HTML 查看器，该查看器以半表格格式显示有关模型数据的详细信息以及找到的任何模式。</span><span class="sxs-lookup"><span data-stu-id="b85f3-111">If you want to get into details, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] also provides an HTML viewer, called the **Generic Content Tree Viewer**, that displays detailed information about the model data and any patterns that were found, in a semi-tabular format.</span></span> <span data-ttu-id="b85f3-112">有关详细信息，请参阅 [使用 Microsoft 一般内容树查看器浏览模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="b85f3-112">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="b85f3-113">在本课中，您将查看三个模型的结果。</span><span class="sxs-lookup"><span data-stu-id="b85f3-113">In this lesson you will look at the results from your three models.</span></span> <span data-ttu-id="b85f3-114">每个模型类型基于不同的算法，为观察数据提供了不同角度。</span><span class="sxs-lookup"><span data-stu-id="b85f3-114">Each model type is based on a different algorithm and provides different insights into the data.</span></span>  
  
-   <span data-ttu-id="b85f3-115">决策树模型告诉您影响自行车购买的各因素。</span><span class="sxs-lookup"><span data-stu-id="b85f3-115">The Decision Tree model tells you about factors that influence bike buying.</span></span>  
  
-   <span data-ttu-id="b85f3-116">聚类分析模型按照包括客户的自行车购买行为的属性和其他所选属性来对客户进行分组。</span><span class="sxs-lookup"><span data-stu-id="b85f3-116">The Clustering model groups your customers by attributes that include their bike buying behavior and other selected attributes.</span></span>  
  
-   <span data-ttu-id="b85f3-117">Naive Bayes 模型使您可以浏览不同属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="b85f3-117">The Naive Bayes model enables you to explore the relationship between different attributes.</span></span>  
  
 <span data-ttu-id="b85f3-118">请参阅以下主题以了解有关每个挖掘模型查看器的更多信息。</span><span class="sxs-lookup"><span data-stu-id="b85f3-118">See the following topics to learn more about each of the mining model viewers.</span></span>  
  
-   [<span data-ttu-id="b85f3-119">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b85f3-119">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="b85f3-120">浏览聚类分析模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b85f3-120">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="b85f3-121">浏览 Naive Bayes 模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b85f3-121">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="b85f3-122">所有这三种模型都可以使用**一般内容树查看器**进行查看，以提取公式、数据值等。</span><span class="sxs-lookup"><span data-stu-id="b85f3-122">All three models can be viewed using the **Generic Content Tree Viewer**, to extract formulas, data values, and so forth.</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="b85f3-123">课程中的第一个任务</span><span class="sxs-lookup"><span data-stu-id="b85f3-123">First Task in Lesson</span></span>  
 [<span data-ttu-id="b85f3-124">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b85f3-124">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="b85f3-125">前一课</span><span class="sxs-lookup"><span data-stu-id="b85f3-125">Previous Lesson</span></span>  
 [<span data-ttu-id="b85f3-126">第 3 课：添加和处理模型</span><span class="sxs-lookup"><span data-stu-id="b85f3-126">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="b85f3-127">下一课</span><span class="sxs-lookup"><span data-stu-id="b85f3-127">Next Lesson</span></span>  
 [<span data-ttu-id="b85f3-128">第5课：测试模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b85f3-128">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b85f3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b85f3-129">See Also</span></span>  
 <span data-ttu-id="b85f3-130">[挖掘模型查看器任务和操作指南](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b85f3-130">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="b85f3-131">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="b85f3-131">Data Mining Model Viewers</span></span>](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
