---
title: 第2课：生成预测方案 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c81d5846df0a37c2b4182cb92fea86ce6f3417a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577167"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="2addd-102">第 2 课：生成预测方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2addd-102">Lesson 2: Building a Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2addd-103">作为 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]的销售分析人员，您需要对下一年产品的销售量做出预测。</span><span class="sxs-lookup"><span data-stu-id="2addd-103">As the sales analyst for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you have been asked to forecast the sales of products for the next year.</span></span> <span data-ttu-id="2addd-104">特别是已要求您比较不同区域和产品线的预测值。</span><span class="sxs-lookup"><span data-stu-id="2addd-104">In particular, you have been asked to compare forecasts for the different regions and product lines.</span></span> <span data-ttu-id="2addd-105">此外，您还需要确定不同产品的销售量在一年中的不同时间是否有变化。</span><span class="sxs-lookup"><span data-stu-id="2addd-105">Additionally, you have been asked to determine whether sales of different products vary depending on the time of the year.</span></span>  
  
 <span data-ttu-id="2addd-106">为了找到所需的信息，在本课程中您将按三个区域汇总公司每月的销售数据：欧洲、北美洲和太平洋地区。</span><span class="sxs-lookup"><span data-stu-id="2addd-106">To find the requested information, in this lesson you will summarize the company's sales data at the monthly level, and you will also summarize sales figures by three regions: Europe, North America, and the Pacific.</span></span>  
  
 <span data-ttu-id="2addd-107">完成本课程中的任务之后，您便能回答下列问题：</span><span class="sxs-lookup"><span data-stu-id="2addd-107">After you complete the tasks in this lesson, you will be able to answer the following questions:</span></span>  
  
-   <span data-ttu-id="2addd-108">不同型号自行车的销售量如何随时间变化？</span><span class="sxs-lookup"><span data-stu-id="2addd-108">How do the sales of different bike models change over time?</span></span>  
  
-   <span data-ttu-id="2addd-109">这三个区域的销售模式之间是否存在差异？</span><span class="sxs-lookup"><span data-stu-id="2addd-109">Are there differences between the patterns for sales in the three regions?</span></span>  
  
-   <span data-ttu-id="2addd-110">我们能预测销售旺季吗？</span><span class="sxs-lookup"><span data-stu-id="2addd-110">Can we forecast sales peaks?</span></span>  
  
 <span data-ttu-id="2addd-111">本课程可以分两部分完成：</span><span class="sxs-lookup"><span data-stu-id="2addd-111">The lesson can be completed in two parts:</span></span>  
  
-   <span data-ttu-id="2addd-112">第一部分引入如何创建和使用时序模型的基本知识。</span><span class="sxs-lookup"><span data-stu-id="2addd-112">Part One introduces the basics of how to create and use a time series model.</span></span>  
  
-   <span data-ttu-id="2addd-113">第二部分将指导您基于所有区域创建常规时序模型。</span><span class="sxs-lookup"><span data-stu-id="2addd-113">Part Two walks you through creation of a general time series model, based on all regions.</span></span> <span data-ttu-id="2addd-114">您可以将此常规模型用于*交叉预测*。</span><span class="sxs-lookup"><span data-stu-id="2addd-114">You can use this general model for *cross-prediction*.</span></span>  
  
 <span data-ttu-id="2addd-115">若要完成本课中的任务（如下所列），您将使用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 您在[第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)中创建的数据源。</span><span class="sxs-lookup"><span data-stu-id="2addd-115">To complete the tasks in this lesson, which are listed below, you will use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source that you created in [Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2addd-116">对于此版本， [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 示例数据库中的日期已更新。</span><span class="sxs-lookup"><span data-stu-id="2addd-116">The dates in the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sample database have been updated for this release.</span></span> <span data-ttu-id="2addd-117">如果您使用 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]的早期版本，则可以在执行这些步骤后生成模型，但可能会看到不同的结果。</span><span class="sxs-lookup"><span data-stu-id="2addd-117">If you use an earlier version of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you can build the model following these steps, but you might see different results.</span></span>  
  
 <span data-ttu-id="2addd-118">**创建简单预测模型**</span><span class="sxs-lookup"><span data-stu-id="2addd-118">**Creating a Simple Forecasting Model**</span></span>  
  
-   [<span data-ttu-id="2addd-119">添加数据源视图以便预测 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-119">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-120">创建预测结构和模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-120">Creating a Forecasting Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-121">&#40;中级数据挖掘教程修改预测结构&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-121">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-122">自定义和处理预测模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-122">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-123">了解 &#40;中级数据挖掘教程的预测模型&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-123">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-124">&#40;中级数据挖掘教程创建时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-124">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="2addd-125">**创建用于交叉预测的常规预测模型**</span><span class="sxs-lookup"><span data-stu-id="2addd-125">**Creating a General Forecasting Model for Cross-Prediction**</span></span>  
  
-   [<span data-ttu-id="2addd-126">&#40;中级数据挖掘教程的高级时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-126">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-127">使用更新的数据 &#40;中级数据挖掘教程的时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-127">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2addd-128">使用替换数据 &#40;中级数据挖掘教程的时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-128">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="2addd-129">&#40;中级数据挖掘教程比较预测模型的预测&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-129">Comparing Predictions for Forecasting Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2addd-130">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="2addd-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2addd-131">添加数据源视图以便预测 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-131">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2addd-132">了解 &#40;中级数据挖掘教程的时序模型的要求&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-132">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="2addd-133">所有课程</span><span class="sxs-lookup"><span data-stu-id="2addd-133">All Lessons</span></span>  
 [<span data-ttu-id="2addd-134">第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-134">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="2addd-135">第 2 课：预测方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2addd-135">Lesson 2: Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="2addd-136">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2addd-136">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2addd-137">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="2addd-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="2addd-138">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="2addd-138">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2addd-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2addd-139">See Also</span></span>  
 <span data-ttu-id="2addd-140">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2addd-140">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="2addd-141">[中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2addd-141">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="2addd-142">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="2addd-142">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
