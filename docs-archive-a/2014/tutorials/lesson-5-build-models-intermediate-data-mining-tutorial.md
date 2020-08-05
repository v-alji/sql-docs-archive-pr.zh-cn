---
title: 第5课：生成神经网络和逻辑回归模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a8c9fcf0380582f15fa2bf30d6fdeb97bb2ab1fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581059"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="47671-102">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="47671-102">Lesson 5: Building Neural Network and Logistic Regression Models (Intermediate Data Mining Tutorial)</span></span>
  
  
 <span data-ttu-id="47671-103">[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 业务部门正在开展旨在提高客户对呼叫中心满意度的计划。</span><span class="sxs-lookup"><span data-stu-id="47671-103">The Operations department of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] is engaged in a project to improve customer satisfaction with their call center.</span></span> <span data-ttu-id="47671-104">他们雇用了一位供应商来管理呼叫中心并报告有关呼叫中心工作效率的指标，同时请您分析该供应商提供的一些初步数据。</span><span class="sxs-lookup"><span data-stu-id="47671-104">They hired a vendor to manage the call center and to report metrics on call center effectiveness, and have asked you to analyze some preliminary data provided by the vendor.</span></span> <span data-ttu-id="47671-105">他们想知道是否会有任何值得关注的发现。</span><span class="sxs-lookup"><span data-stu-id="47671-105">They want to know if there are any interesting findings.</span></span> <span data-ttu-id="47671-106">特别是，他们想知道这些数据是否间接显示了人员配备的任何问题或改进客户满意度的方式。</span><span class="sxs-lookup"><span data-stu-id="47671-106">In particular, they would like to know if the data suggests any staffing problems with staffing or ways to improve customer satisfaction.</span></span>  
  
 <span data-ttu-id="47671-107">该数据集很小，只包括 30 天内呼叫中心的运转情况。</span><span class="sxs-lookup"><span data-stu-id="47671-107">The data set is small and covers only a 30-day period in the operation of the call center.</span></span> <span data-ttu-id="47671-108">数据跟踪每个班次的操作员新手和有经验操作员的人数、来电数、订单数以及必须解决的问题数、客户等待某人回电话的平均时间。</span><span class="sxs-lookup"><span data-stu-id="47671-108">The data tracks the number of new and experienced operators in each shift, the number of incoming calls, the number of orders as well as issues that must be resolved, and the average time a customer waits for someone to respond to a call.</span></span> <span data-ttu-id="47671-109">数据还包含基于“挂断率” \*\* 的服务质量指标，它反映客户不满意的程度。</span><span class="sxs-lookup"><span data-stu-id="47671-109">The data also includes a service quality metric based on *abandon rate*, which is an indicator of customer frustration.</span></span>  
  
 <span data-ttu-id="47671-110">因为您事先对将显示的数据没有任何期望，您决定使用神经网络模型来探查可能的相关性。</span><span class="sxs-lookup"><span data-stu-id="47671-110">Because you do not have any prior expectations about what the data will show, you decide to use a neural network model to explore possible correlations.</span></span> <span data-ttu-id="47671-111">神经网络模型通常用于探查，因为该模型能够分析多个输入和输出之间的复杂关系。</span><span class="sxs-lookup"><span data-stu-id="47671-111">Neural network models are often used for exploration because they can analyze complex relationships between many inputs and outputs.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="47671-112">学习内容</span><span class="sxs-lookup"><span data-stu-id="47671-112">What You Will Learn</span></span>  
 <span data-ttu-id="47671-113">在本课中，您将使用神经网络算法生成一个模型，使您和业务团队可以用来理解数据中的趋势。</span><span class="sxs-lookup"><span data-stu-id="47671-113">In this lesson, you will use the neural network algorithm to build a model that you and the Operations team can use to understand the trends in the data.</span></span> <span data-ttu-id="47671-114">作为本课的一部分，您将尝试回答下列问题：</span><span class="sxs-lookup"><span data-stu-id="47671-114">As part of this lesson, you will try to answer the following questions:</span></span>  
  
-   <span data-ttu-id="47671-115">哪些因素会影响客户满意度？</span><span class="sxs-lookup"><span data-stu-id="47671-115">What factors affect customer satisfaction?</span></span>  
  
-   <span data-ttu-id="47671-116">呼叫中心如何能够改进服务质量？</span><span class="sxs-lookup"><span data-stu-id="47671-116">What can the call center do to improve service quality?</span></span>  
  
 <span data-ttu-id="47671-117">根据结果，您将生成可用于预测的逻辑回归模型。</span><span class="sxs-lookup"><span data-stu-id="47671-117">Based on the results, you will then build a logistic regression model that you can use for predictions.</span></span> <span data-ttu-id="47671-118">业务团队将使用该预测来帮助规划呼叫中心的运营。</span><span class="sxs-lookup"><span data-stu-id="47671-118">The predictions will be used by the Operations team as an aid in planning call center operation.</span></span>  
  
 <span data-ttu-id="47671-119">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="47671-119">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="47671-120">为呼叫中心数据添加数据源视图 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-120">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="47671-121">创建神经网络结构和模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-121">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="47671-122">探索呼叫中心模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-122">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="47671-123">向呼叫中心结构中添加逻辑回归模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-123">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="47671-124">&#40;中级数据挖掘教程为呼叫中心模型创建预测&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-124">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="47671-125">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="47671-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="47671-126">为呼叫中心数据添加数据源视图 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-126">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="47671-127">所有课程</span><span class="sxs-lookup"><span data-stu-id="47671-127">All Lessons</span></span>  
 [<span data-ttu-id="47671-128">第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-128">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="47671-129">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="47671-130">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="47671-130">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="47671-131">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-131">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 <span data-ttu-id="47671-132">第 5 课：神经网络和逻辑回归方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="47671-132">Lesson 5: Neural Network and Logistic Regression Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47671-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47671-133">See Also</span></span>  
 <span data-ttu-id="47671-134">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="47671-134">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="47671-135">中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="47671-135">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
