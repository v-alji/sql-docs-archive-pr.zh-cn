---
title: 中级数据挖掘教程 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 090bcd8cc987da57a5c4bdf27e6782ae07b85719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578599"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a><span data-ttu-id="1e82b-102">数据挖掘中级教程（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="1e82b-102">Intermediate Data Mining Tutorial (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="1e82b-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供用于创建和使用数据挖掘模型的集成环境。</span><span class="sxs-lookup"><span data-stu-id="1e82b-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides an integrated environment for creating and working with data mining models.</span></span> <span data-ttu-id="1e82b-104">您可以方便地绑定到数据源、针对同一个数据创建和测试多个模型并部署要用于进行预测分析的模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-104">You can easily bind to data sources, create and test multiple models on the same data, and deploy models for use in predictive analysis.</span></span>  
  
 <span data-ttu-id="1e82b-105">在数据挖掘基础教程中，您学习了如何使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 创建数据挖掘解决方案，而且生成了三个支持目标邮递活动的模型，这些模型可用来分析客户购买行为并确定潜在的购买目标。</span><span class="sxs-lookup"><span data-stu-id="1e82b-105">In the Basic Data Mining Tutorial, you learned how to use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a data mining solution, and you built three models to support a targeted mailing campaign for analyzing customer purchasing behavior and for targeting potential buyers.</span></span>  
  
 <span data-ttu-id="1e82b-106">本中级教程基于这些经验而构建，其中介绍了几个新方案（包括预测和市场篮分析等常见业务要求）。</span><span class="sxs-lookup"><span data-stu-id="1e82b-106">This intermediate tutorial builds on that experience and introduces several new scenarios, including common business requirements such as forecasting and market basket analysis.</span></span> <span data-ttu-id="1e82b-107">您将学习如何创建时序模型、关联模型以及顺序分析和聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-107">You will learn how to create a time series model, an association model, and a sequence clustering model.</span></span> <span data-ttu-id="1e82b-108">最后，您将学习如何使用神经网络了解数据相关性，以及使用逻辑回归进行预测。</span><span class="sxs-lookup"><span data-stu-id="1e82b-108">Finally, you will learn how to use neural network to explore correlations in data and to use logistic regression for predictions.</span></span>  
  
 <span data-ttu-id="1e82b-109">这些课程是相互独立的，可以单独完成。</span><span class="sxs-lookup"><span data-stu-id="1e82b-109">The lessons are independent and can be completed separately.</span></span>  
  
 <span data-ttu-id="1e82b-110">若要完成以下教程，您应该熟悉数据挖掘工具，以及在数据挖掘基础教程中引入的挖掘模型查看器。</span><span class="sxs-lookup"><span data-stu-id="1e82b-110">To complete the following tutorials, you should to be familiar with the data mining tools and with the mining model viewers that were introduced in the Basic Data Mining Tutorial.</span></span>  
  
 <span data-ttu-id="1e82b-111">所有的方案都使用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据源，但是您将为不同的方案创建不同的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="1e82b-111">All scenarios use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source, but you will create different data source views for different scenarios.</span></span> <span data-ttu-id="1e82b-112">只要您是首先创建数据源，就可以按任何顺序做练习。</span><span class="sxs-lookup"><span data-stu-id="1e82b-112">You can do the lessons in any order as long as you create the data source first.</span></span>  
  
## <a name="lesson-scenarios"></a><span data-ttu-id="1e82b-113">课程方案</span><span class="sxs-lookup"><span data-stu-id="1e82b-113">Lesson Scenarios</span></span>  
 <span data-ttu-id="1e82b-114">在成功完成目标邮寄活动之后，系统已经要求您利用自己的数据挖掘知识来开发几个要用于进行业务规划的新模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-114">After your success with the targeted mailing campaign, you have been asked to apply your knowledge of data mining to develop several new models for use in business planning.</span></span> <span data-ttu-id="1e82b-115">其中包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="1e82b-115">These include the following tasks:</span></span>  
  
-   <span data-ttu-id="1e82b-116">**预测：** 您将创建*时序*模型，以预测世界各地不同地区的产品销售额。</span><span class="sxs-lookup"><span data-stu-id="1e82b-116">**Forecasting:** You will create a *time series* model, to forecast the sales of products in different regions around the world.</span></span> <span data-ttu-id="1e82b-117">您将为每个区域开发单独的模型，并学习如何使用*交叉预测*。</span><span class="sxs-lookup"><span data-stu-id="1e82b-117">You will develop individual models for each region and learn how to use *cross-prediction*.</span></span>  
  
-   <span data-ttu-id="1e82b-118">**市场篮分析：** 您将创建一个*关联模型*，用于分析在访问电子商务网站时所购买产品的分组 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e82b-118">**Market basket analysis:** You will create an *association model*, to analyze groupings of products that are purchased during visits to the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] e-commerce site.</span></span> <span data-ttu-id="1e82b-119">根据此市场篮模型，你可以向客户推荐产品。</span><span class="sxs-lookup"><span data-stu-id="1e82b-119">Based on this market basket model, you can recommend products to customers.</span></span>  
  
-   <span data-ttu-id="1e82b-120">**序列分析：** 你构建了*顺序分析和聚类分析模型*，用于分析客户购买产品的顺序。</span><span class="sxs-lookup"><span data-stu-id="1e82b-120">**Sequence analysis:** You build a *sequence clustering model*, to analyze the order in which customers buy products.</span></span> <span data-ttu-id="1e82b-121">您可以基于这个模型规划对网站设计或新产品套餐进行的更改。</span><span class="sxs-lookup"><span data-stu-id="1e82b-121">Based on this model, you can plan changes in Web site design or new product offerings.</span></span>  
  
-   <span data-ttu-id="1e82b-122">**因素分析：** 您可以使用*神经网络*模型来浏览呼叫中心数据中服务质量差的可能原因。</span><span class="sxs-lookup"><span data-stu-id="1e82b-122">**Factor analysis:** You use a *neural network* model to explore the possible causes of poor service quality in call center data.</span></span> <span data-ttu-id="1e82b-123">基于初步模式的见解，你将创建*逻辑回归模型*来预测改善客户体验的策略。</span><span class="sxs-lookup"><span data-stu-id="1e82b-123">Based on the insights from the preliminary model, you will create a *logistic regression model* to predict strategies for improving customer experience.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="1e82b-124">学习内容</span><span class="sxs-lookup"><span data-stu-id="1e82b-124">What You Will Learn</span></span>  
 <span data-ttu-id="1e82b-125">本教程将讲述如何创建和使用多种类型的数据挖掘算法。</span><span class="sxs-lookup"><span data-stu-id="1e82b-125">This tutorial teaches you how to create and work with several types of data mining algorithms.</span></span> <span data-ttu-id="1e82b-126">本教程分为以下几课：</span><span class="sxs-lookup"><span data-stu-id="1e82b-126">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="1e82b-127">第1课：创建中级数据挖掘解决方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="1e82b-127">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="1e82b-128">在本课中，您将基于 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库创建一个新的项目，以便支持多个新数据源视图和更多的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-128">In this lesson, you will create a new project based on the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database, to support several new data sources views and many more mining models.</span></span>  
  
 [<span data-ttu-id="1e82b-129">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="1e82b-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="1e82b-130">在本课中，您将创建一个可用作预测方案一部分的挖掘模型，</span><span class="sxs-lookup"><span data-stu-id="1e82b-130">In this lesson, you will create a mining model that can be used as part of a forecasting scenario.</span></span> <span data-ttu-id="1e82b-131">还将浏览用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-131">You will also explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
 <span data-ttu-id="1e82b-132">您将为每个地区生成单独的模型，而且还生成一个可用于进行交叉预测的通用模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-132">You will build models for individual regions, and then build a general model that can be used for cross-prediction.</span></span>  
  
 [<span data-ttu-id="1e82b-133">第 3 课：生成市场篮方案（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="1e82b-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="1e82b-134">在本课中，您将添加一个新的数据源视图，并学习如何处理嵌套表及其键。</span><span class="sxs-lookup"><span data-stu-id="1e82b-134">In this lesson, you will add a new data source view and learn how to work with nested tables and keys.</span></span> <span data-ttu-id="1e82b-135">您将基于此数据创建一个可用作市场篮方案一部分的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-135">Based on this data, you will create a mining model that can be used as part of a market basket scenario.</span></span> <span data-ttu-id="1e82b-136">您还将浏览用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-136">You will also explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
 [<span data-ttu-id="1e82b-137">第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="1e82b-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 <span data-ttu-id="1e82b-138">在本课中，您将创建一个可用作顺序分析和聚类分析方案一部分的挖掘模型，</span><span class="sxs-lookup"><span data-stu-id="1e82b-138">In this lesson, you will create a mining model that can be used as part of a sequence clustering scenario.</span></span> <span data-ttu-id="1e82b-139">还将学习如何利用通过 [!INCLUDE[msCoName](../includes/msconame-md.md)] 顺序分析和聚类分析算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-139">You will also learn how to explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="1e82b-140">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="1e82b-140">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="1e82b-141">在本课中，您将使用 Microsoft 神经网络和 Microsoft 逻辑回归算法创建若干相关的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="1e82b-141">In this lesson, you will create several related mining models, using the Microsoft Neural Network and Microsoft Logistic Regression algorithms.</span></span> <span data-ttu-id="1e82b-142">您还将学习如何使用数据源视图来基于模型浏览数据。</span><span class="sxs-lookup"><span data-stu-id="1e82b-142">You will also learn to work with data source views to explore data underlying the models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e82b-143">要求</span><span class="sxs-lookup"><span data-stu-id="1e82b-143">Requirements</span></span>  
 <span data-ttu-id="1e82b-144">请确保已安装下列软件：</span><span class="sxs-lookup"><span data-stu-id="1e82b-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="1e82b-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e82b-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="1e82b-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e82b-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1e82b-147">数据库的 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e82b-147">with the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="1e82b-148">为了增强安全性，默认情况下将不安装该示例数据库。</span><span class="sxs-lookup"><span data-stu-id="1e82b-148">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="1e82b-149">若要安装的正式数据库 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请访问[Microsoft SQL 示例数据库](https://go.microsoft.com/fwlink/?LinkId=88417)页，并选择相应的示例数据库版本。</span><span class="sxs-lookup"><span data-stu-id="1e82b-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select the appropriate version of the sample database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e82b-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e82b-150">See Also</span></span>  
 <span data-ttu-id="1e82b-151">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1e82b-151">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="1e82b-152">[自行车购买者 DMX 教程](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1e82b-152">[Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span></span>  
 [<span data-ttu-id="1e82b-153">市场篮 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="1e82b-153">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
