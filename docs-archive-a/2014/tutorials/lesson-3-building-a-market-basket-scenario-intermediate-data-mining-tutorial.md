---
title: 第3课：生成市场篮方案 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a281aa62fbf08393c95f12ded9886ac212b3165f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691389"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="a9ec5-102">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="a9ec5-102">Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="a9ec5-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场部希望改进公司的网站以促进跨区销售。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to improve the company Web site to promote cross-selling.</span></span> <span data-ttu-id="a9ec5-104">作为网站更新的一部分，他们希望能够根据客户的在线购物篮中已有的其他产品来预测客户可能要购买的产品。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-104">As part of the site update, they would like the ability to predict products that a customer might want to purchase, based on the other products that are already in the customer's online shopping basket.</span></span> <span data-ttu-id="a9ec5-105">市场部还希望更好的了解客户购买行为，以便他们能够将网站设计为将可能被集中购买的项统一放置在一个位置上。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-105">The marketing department also wants to understand customer purchasing behavior better, so that they can design the Web site so that the items that tend to be purchased together appear together.</span></span> <span data-ttu-id="a9ec5-106">他们已经了解数据挖掘对于此类“ \*\* 市场蓝分析”尤其有用，并已经请您来开发一个数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-106">They have learned that data mining is especially useful for this kind of *market basket analysis* and have asked you to develop a data mining model.</span></span>  
  
 <span data-ttu-id="a9ec5-107">在完成本课中的任务之后，您还会获得一个可显示客户历史交易中的商品分组的完整挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-107">After you complete the tasks in this lesson, you will have a mining model that shows groups of items from historical customer transactions.</span></span> <span data-ttu-id="a9ec5-108">另外，您可以使用挖掘模型来预测客户可能希望购买的其他产品。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-108">Additionally, you can use the mining model to predict additional items that a customer may want to purchase.</span></span>  
  
 <span data-ttu-id="a9ec5-109">若要完成本课程中的任务，您将使用您在数据挖掘中级教程第一课中创建的解决方案和数据源[&#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-109">To complete the tasks in this lesson, you will use the solution and data source that you created in the first lesson of the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="a9ec5-110">您将通过添加一个数据源视图并在该视图中包含多个有关客户的表（包括客户购买情况的嵌套表）来修改此解决方案。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-110">You will modify this solution by adding a data source view that contains tables about the customer, including a nested table of customer purchases.</span></span>  <span data-ttu-id="a9ec5-111">随后，您将生成一个使用 Microsoft 关联规则算法的挖掘模型，该模型适于市场篮方案。</span><span class="sxs-lookup"><span data-stu-id="a9ec5-111">You will then build a mining model that uses the Microsoft Association Rules algorithm, which is suited to market basket scenarios.</span></span>  
  
 <span data-ttu-id="a9ec5-112">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="a9ec5-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="a9ec5-113">添加具有嵌套表的数据源视图 &#40;中间数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-113">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a9ec5-114">创建市场篮结构和模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-114">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a9ec5-115">&#40;中级数据挖掘教程来修改和处理市场篮模型&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-115">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a9ec5-116">&#40;中级数据挖掘教程了解市场篮模型&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-116">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a9ec5-117">在挖掘模型中筛选嵌套表 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-117">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a9ec5-118">预测 &#40;中级数据挖掘教程的关联&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-118">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a9ec5-119">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="a9ec5-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a9ec5-120">添加具有嵌套表的数据源视图 &#40;中间数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-120">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="a9ec5-121">所有课程</span><span class="sxs-lookup"><span data-stu-id="a9ec5-121">All Lessons</span></span>  
 [<span data-ttu-id="a9ec5-122">第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-122">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="a9ec5-123">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-123">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="a9ec5-124">第 3 课：市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="a9ec5-124">Lesson 3: Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="a9ec5-125">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-125">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="a9ec5-126">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="a9ec5-126">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a9ec5-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9ec5-127">See Also</span></span>  
 <span data-ttu-id="a9ec5-128">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="a9ec5-128">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="a9ec5-129">[第2课： &#40;中级数据挖掘教程构建预测方案&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="a9ec5-129">[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="a9ec5-130">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a9ec5-130">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
