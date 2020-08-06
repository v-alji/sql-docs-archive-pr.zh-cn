---
title: 数据挖掘基础教程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ed557ffb5b8592be4d4375aca40e461d699d6ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691405"
---
# <a name="basic-data-mining-tutorial"></a><span data-ttu-id="4632d-102">数据挖掘基础教程</span><span class="sxs-lookup"><span data-stu-id="4632d-102">Basic Data Mining Tutorial</span></span>
  <span data-ttu-id="4632d-103">欢迎使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据挖掘基础教程。</span><span class="sxs-lookup"><span data-stu-id="4632d-103">Welcome to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Basic Data Mining Tutorial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="4632d-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]提供用于创建数据挖掘模型和进行预测的集成环境。</span><span class="sxs-lookup"><span data-stu-id="4632d-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides an integrated environment for creating data mining models and making predictions.</span></span> <span data-ttu-id="4632d-105">在本教程中，您将完成一个用于目标邮递活动的方案，在此方案中您使用计算机学习来分析和预测客户购买行为。</span><span class="sxs-lookup"><span data-stu-id="4632d-105">In this tutorial, you will complete a scenario for a targeted mailing campaign in which you use machine learning to analyze and predict customer purchasing behavior.</span></span> <span data-ttu-id="4632d-106">本教程说明了如何使用三种最重要的数据挖掘算法：聚类、决策树和 Naive Bayes。</span><span class="sxs-lookup"><span data-stu-id="4632d-106">The tutorial demonstrates how to use three of the most important data mining algorithms: clustering, decision trees, and Naive Bayes.</span></span> <span data-ttu-id="4632d-107">您还将学习如何使用挖掘模型查看器分析您的发现，以及如何使用中包含的数据挖掘工具创建预测和准确性图表 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4632d-107">You will also learn how to analyze your findings using the mining model viewers, and to create predictions and accuracy charts using the data mining tools that are included in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4632d-108">虚构公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 用于所有的示例。</span><span class="sxs-lookup"><span data-stu-id="4632d-108">The fictitious company, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], is used for all examples.</span></span>  
  
 <span data-ttu-id="4632d-109">当您使用数据挖掘工具时，我们建议您同时完成数据[挖掘的中间教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4632d-109">When you are comfortable using the data mining tools, we recommend that you also complete the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="4632d-110">这些课演示如何使用预测、市场篮分析、时序、关联模型、嵌套表、顺序分析和聚类分析。</span><span class="sxs-lookup"><span data-stu-id="4632d-110">The lessons demonstrate how to use forecasting, market basket analysis, time series, association models, nested tables, and sequence clustering.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="4632d-111">教程方案</span><span class="sxs-lookup"><span data-stu-id="4632d-111">Tutorial Scenario</span></span>  
 <span data-ttu-id="4632d-112">在本教程中，您是谁已经 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 过了了解有关公司客户的详细信息的员工，这些人员基于历史购买情况，然后使用该历史数据进行营销。</span><span class="sxs-lookup"><span data-stu-id="4632d-112">In this tutorial, you are an employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with learning more about the company's customers based on historical purchases, and then using that historical data to make predictions that can be used in marketing.</span></span> <span data-ttu-id="4632d-113">公司以前从未进行过数据挖掘，因此您必须创建一个专门用于数据挖掘的新数据库并建立几个数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="4632d-113">The company has never done data mining before, so you must create a new database specifically for data mining and set up several data mining models.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="4632d-114">学习内容</span><span class="sxs-lookup"><span data-stu-id="4632d-114">What You Will Learn</span></span>  
 <span data-ttu-id="4632d-115">本教程将讲述如何创建和使用数种不同类型的计算机学习方法。</span><span class="sxs-lookup"><span data-stu-id="4632d-115">This tutorial teaches you how to create and work with several different types of machine learning methods.</span></span> <span data-ttu-id="4632d-116">您还将学习如何创建挖掘模型的副本以及如何将筛选器应用到输入数据以获得不同结果。</span><span class="sxs-lookup"><span data-stu-id="4632d-116">You will also learn how to create a copy of a mining model, and apply a filter to the input data to get different results.</span></span> <span data-ttu-id="4632d-117">之后，您可以使用提升图比较两个模型的结果。</span><span class="sxs-lookup"><span data-stu-id="4632d-117">Afterwards you can compare the results of both models using a lift chart.</span></span> <span data-ttu-id="4632d-118">最后，您将使用钻取功能从基础挖掘结构检索其他数据。</span><span class="sxs-lookup"><span data-stu-id="4632d-118">Finally, you will use drillthrough to retrieve additional data from the underlying mining structure.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="4632d-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]数据挖掘包括以下功能，可帮助您轻松地开发和比较多个预测模型，然后对结果采取操作：</span><span class="sxs-lookup"><span data-stu-id="4632d-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Data Mining includes the following features that help you easily develop and compare multiple predictive models and then take actions on the results :</span></span>  
  
-   <span data-ttu-id="4632d-120">*维持测试集-* 在创建挖掘结构时，您现在可以将挖掘结构中的数据划分为定型集和测试集。</span><span class="sxs-lookup"><span data-stu-id="4632d-120">*Holdout Test Sets -* When you create a mining structure, you can now divide the data in the mining structure into training and testing sets.</span></span> <span data-ttu-id="4632d-121">这让您能够在类似的数据集上测试模型，以及比较相关模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="4632d-121">This lets you test models on similar data sets, and compare the accuracy of related models.</span></span>  
  
-   <span data-ttu-id="4632d-122">*挖掘模型筛选器-* 你现在可以将筛选器附加到挖掘模型，并在定型和测试期间应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="4632d-122">*Mining model filters -* You can now attach filters to a mining model, and apply the filter during both training and testing.</span></span> <span data-ttu-id="4632d-123">这让您能够轻松地在不同的数据子集上生成相关模型。</span><span class="sxs-lookup"><span data-stu-id="4632d-123">This lets you easily build related models on different subsets of the data.</span></span>  
  
-   <span data-ttu-id="4632d-124">*钻取到结构事例和结构列-* 你现在可以从挖掘模型中的常规模式轻松移到数据源中可操作的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4632d-124">*Drillthrough to Structure Cases and Structure Columns -* You can now easily move from the general patterns in the mining model to actionable detail in the data source.</span></span>  
  
 <span data-ttu-id="4632d-125">本教程分为以下几课：</span><span class="sxs-lookup"><span data-stu-id="4632d-125">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="4632d-126">第1课：准备 Analysis Services 数据库 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="4632d-126">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 <span data-ttu-id="4632d-127">在本课程中，您将学习如何创建新的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，添加数据源和数据源视图，以及准备将用于数据挖掘的新数据库。</span><span class="sxs-lookup"><span data-stu-id="4632d-127">In this lesson, you will learn how to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, add a data source and data source view, and prepare the new database to be used with data mining.</span></span>  
  
 [<span data-ttu-id="4632d-128">第2课： &#40;基本数据挖掘教程生成目标邮件结构&#41;</span><span class="sxs-lookup"><span data-stu-id="4632d-128">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 <span data-ttu-id="4632d-129">在本课中，您将学习如何创建可用作目标邮寄方案一部分的挖掘模型结构。</span><span class="sxs-lookup"><span data-stu-id="4632d-129">In this lesson, you will learn how to create a mining model structure that can be used as part of a targeted mailing scenario.</span></span>  
  
 [<span data-ttu-id="4632d-130">第 3 课：添加和处理模型</span><span class="sxs-lookup"><span data-stu-id="4632d-130">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 <span data-ttu-id="4632d-131">在本课中，您将学习如何向结构中添加模型。</span><span class="sxs-lookup"><span data-stu-id="4632d-131">In this lesson you will learn how to add models to a structure.</span></span> <span data-ttu-id="4632d-132">您创建的模型是用如下算法生成的：</span><span class="sxs-lookup"><span data-stu-id="4632d-132">The models you create are built with the following algorithms:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4632d-133">决策树</span><span class="sxs-lookup"><span data-stu-id="4632d-133">Decision Trees</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4632d-134">聚类分析</span><span class="sxs-lookup"><span data-stu-id="4632d-134">Clustering</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4632d-135">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="4632d-135">Naive Bayes</span></span>  
  
 [<span data-ttu-id="4632d-136">第4课：浏览目标邮件模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="4632d-136">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="4632d-137">在本课中，您将学习如何使用查看器浏览和解释在每个模型中发现的内容。</span><span class="sxs-lookup"><span data-stu-id="4632d-137">In this lesson you will learn how to explore and interpret the findings of each model using the Viewers.</span></span>  
  
 [<span data-ttu-id="4632d-138">第5课：测试模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="4632d-138">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="4632d-139">在本课中，您将创建某个 Targeted Mailing 模型的副本，添加一个挖掘模型筛选器以将定型数据限制在特定客户集，然后评估该模型的可行性。</span><span class="sxs-lookup"><span data-stu-id="4632d-139">In this lesson, you make a copy of one of the targeted mailing models, add a mining model filter to restrict the training data to a particular set of customers, and then assess the viability of the model.</span></span>  
  
 [<span data-ttu-id="4632d-140">第 6 课：创建和使用预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="4632d-140">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 <span data-ttu-id="4632d-141">在本数据挖掘基础教程的最后一课中，您将使用该模型预测哪些客户最有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="4632d-141">In this final lesson of the Basic Data Mining Tutorial, you use the model to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="4632d-142">随后，您将钻取到基础事例以获取联系信息。</span><span class="sxs-lookup"><span data-stu-id="4632d-142">You then drill through to the underlying cases to obtain contact information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4632d-143">要求</span><span class="sxs-lookup"><span data-stu-id="4632d-143">Requirements</span></span>  
 <span data-ttu-id="4632d-144">请确保已安装下列软件：</span><span class="sxs-lookup"><span data-stu-id="4632d-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="4632d-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4632d-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="4632d-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在多维模式下</span><span class="sxs-lookup"><span data-stu-id="4632d-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in multidimensional mode</span></span>  
  
-   <span data-ttu-id="4632d-147">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="4632d-147">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="4632d-148">为了增强安全性，示例数据库不随 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 一起安装。</span><span class="sxs-lookup"><span data-stu-id="4632d-148">To enhance security, the sample databases are not installed with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4632d-149">若要安装的正式数据库 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请访问[Microsoft SQL 示例数据库](https://go.microsoft.com/fwlink/?LinkId=88417)页，并选择 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4632d-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4632d-150">当您完成教程时，您可能会发现，如果您向文档查看器工具栏添加了 "**下一主题**" 和 "**上一个主题**" 按钮，在各个步骤间来回移动会更容易。</span><span class="sxs-lookup"><span data-stu-id="4632d-150">When you are working through a tutorial, you might find it easier to move back and forth between the steps if you add the **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4632d-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4632d-151">See Also</span></span>  
 <span data-ttu-id="4632d-152">[数据挖掘解决方案](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="4632d-152">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="4632d-153">[挖掘模型任务和操作指南](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="4632d-153">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="4632d-154">使用 DMX 创建和查询数据挖掘模型：教程（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="4632d-154">Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
