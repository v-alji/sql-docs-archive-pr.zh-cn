---
title: 第4课：生成顺序分析和聚类分析方案 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0f417c685d8af898de7c66ffe82045fa76b582e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682459"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="2d87a-102">第 4 课：生成顺序分析和聚类分析方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2d87a-102">Lesson 4: Building a Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2d87a-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场部需要了解客户浏览 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 网站的方式。</span><span class="sxs-lookup"><span data-stu-id="2d87a-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to understand how customers move through the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] Web site.</span></span> <span data-ttu-id="2d87a-104">公司认为存在一个顺序模式，客户以这种模式将产品放入其购物篮中。</span><span class="sxs-lookup"><span data-stu-id="2d87a-104">The company suspects that there is a pattern to the order in which customers put products into their shopping baskets.</span></span> <span data-ttu-id="2d87a-105">它们希望分析购买序列的顺序，以了解客户如何向其购物篮中添加相关产品。</span><span class="sxs-lookup"><span data-stu-id="2d87a-105">They want to analyze the order of purchase sequences to learn how customers add related items to their baskets.</span></span> <span data-ttu-id="2d87a-106">然后可使用上述信息简化网站的流程，这样便可引导客户购买更多的产品。</span><span class="sxs-lookup"><span data-stu-id="2d87a-106">They can then use this information to streamline the flow of the Web site so that it leads customers to purchase additional products.</span></span>  
  
 <span data-ttu-id="2d87a-107">完成本课程中的任务时，您已经创建了一个挖掘模型，该模型使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 顺序分析和聚类分析算法预测客户将放入购物篮中的下一个产品。</span><span class="sxs-lookup"><span data-stu-id="2d87a-107">After you complete the tasks in this lesson, you will have created a mining model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm to predict the next item that customers will put into their shopping baskets.</span></span> <span data-ttu-id="2d87a-108">您将试用两个版本的模型：一个模型仅分析购物篮中产品的顺序，另一个模型中包含一些其他可用来进行聚类分析的客户统计信息。</span><span class="sxs-lookup"><span data-stu-id="2d87a-108">You will experiment with two versions of the model: one that analyzes only the order of products in the basket, and one that contains some additional customer demographics for clustering.</span></span> <span data-ttu-id="2d87a-109">最后，您将使用这些模型创建预测，以向客户推荐产品。</span><span class="sxs-lookup"><span data-stu-id="2d87a-109">Finally, you will use the models to create predictions that you can use to recommend products to customers.</span></span>  
  
 <span data-ttu-id="2d87a-110">若要完成本课中的任务，您将使用您在第3课中创建的市场篮挖掘结构[&#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2d87a-110">To complete the tasks in the lesson, you will use the market basket mining structure that you created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="2d87a-111">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="2d87a-111">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="2d87a-112">创建顺序分析和聚类分析挖掘模型结构 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-112">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="2d87a-113">处理顺序分析和聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="2d87a-113">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [<span data-ttu-id="2d87a-114">浏览顺序分析和聚类分析模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-114">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2d87a-115">&#40;中级数据挖掘教程创建相关的顺序分析和聚类分析模型&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-115">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2d87a-116">对顺序分析和聚类分析模型创建预测 &#40;中间数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-116">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2d87a-117">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2d87a-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2d87a-118">创建顺序分析和聚类分析挖掘模型结构 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-118">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="2d87a-119">所有课程</span><span class="sxs-lookup"><span data-stu-id="2d87a-119">All Lessons</span></span>  
 [<span data-ttu-id="2d87a-120">第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-120">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2d87a-121">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-121">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2d87a-122">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2d87a-122">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="2d87a-123">第 4 课：顺序分析和聚类分析方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2d87a-123">Lesson 4: Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="2d87a-124">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2d87a-124">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d87a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d87a-125">See Also</span></span>  
 <span data-ttu-id="2d87a-126">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2d87a-126">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="2d87a-127">中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="2d87a-127">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
