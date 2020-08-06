---
title: 利用 DMX 创建和查询数据挖掘模型：教程 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 145b81a7-c0c3-4ca3-bb32-0b482423b9a0
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 22ed01105a32f460bcbeb2c067299fdf62af2eed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576455"
---
# <a name="creating-and-querying-data-mining-models-with-dmx-tutorials-analysis-services---data-mining"></a><span data-ttu-id="52811-102">使用 DMX 创建和查询数据挖掘模型：教程（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="52811-102">Creating and Querying Data Mining Models with DMX: Tutorials (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="52811-103">使用创建数据挖掘解决方案后 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，您可以针对数据挖掘模型创建查询以预测趋势、检索数据中的模式并度量挖掘模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="52811-103">After you have created a data mining solution by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can create queries against the data mining models to predict trends, retrieve patterns in the data, and measure the accuracy of the mining models.</span></span>  
  
 <span data-ttu-id="52811-104">以下列表中的分步教程将帮助你了解如何使用生成和运行数据挖掘查询， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 以便能够充分利用数据。</span><span class="sxs-lookup"><span data-stu-id="52811-104">The step-by-step tutorials in the following list will help you learn how to build and run data mining queries by using [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so that you can get the most from your data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52811-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="52811-105">In This Section</span></span>  
  
-   [<span data-ttu-id="52811-106">自行车购买者 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="52811-106">Bike Buyer DMX Tutorial</span></span>](../../2014/tutorials/bike-buyer-dmx-tutorial.md)  
  
     <span data-ttu-id="52811-107">本教程不但可引导您完成使用数据挖掘扩展插件 (DMX) 语言创建新挖掘结构和挖掘模型的过程，还会介绍如何创建 DMX 预测查询。</span><span class="sxs-lookup"><span data-stu-id="52811-107">This tutorial walks you through the creation of a new mining structure and mining models by using the Data Mining Extensions (DMX) language, and explains how to create DMX prediction queries.</span></span>  
  
-   [<span data-ttu-id="52811-108">市场篮 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="52811-108">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
     <span data-ttu-id="52811-109">本教程使用一个典型的市场篮方案，您可从中发现客户同时购买的产品之间的关联性。</span><span class="sxs-lookup"><span data-stu-id="52811-109">This tutorial uses a typical market basket scenario, where you find associations between the products that customers purchase together.</span></span> <span data-ttu-id="52811-110">本教程还演示了如何在创建挖掘结构时使用嵌套表。</span><span class="sxs-lookup"><span data-stu-id="52811-110">This tutorial also demonstrates how to use nested tables when you create a mining structure.</span></span> <span data-ttu-id="52811-111">您将基于此结构生成并定型模型，然后使用 DMX 创建预测。</span><span class="sxs-lookup"><span data-stu-id="52811-111">You build and train a model based on this structure, and then create predictions using DMX.</span></span>  
  
-   [<span data-ttu-id="52811-112">时序预测 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="52811-112">Time Series Prediction DMX Tutorial</span></span>](../../2014/tutorials/time-series-prediction-dmx-tutorial.md)  
  
     <span data-ttu-id="52811-113">本教程创建一个预测模型以演示 CREATE MODEL (DMX) 语句的用法。</span><span class="sxs-lookup"><span data-stu-id="52811-113">This tutorial creates a forecasting model to illustrate the use of the CREATE MODEL (DMX) statement.</span></span> <span data-ttu-id="52811-114">然后，添加相关的模型，并通过更改 Microsoft 时序算法的参数来自定义每个模型的行为。</span><span class="sxs-lookup"><span data-stu-id="52811-114">You then add related models and customize the behavior of each by changing the parameters of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="52811-115">最后，创建预测并使用新数据更新预测。</span><span class="sxs-lookup"><span data-stu-id="52811-115">Finally you create predictions and update the predictions with new data.</span></span> <span data-ttu-id="52811-116">在创建预测时更新时序是在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 中增加的功能。</span><span class="sxs-lookup"><span data-stu-id="52811-116">The ability to update a time series while making predictions was added in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52811-117">参考</span><span class="sxs-lookup"><span data-stu-id="52811-117">Reference</span></span>  
 [<span data-ttu-id="52811-118">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="52811-118">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="52811-119">数据挖掘扩展插件 (DMX) 参考</span><span class="sxs-lookup"><span data-stu-id="52811-119">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
## <a name="related-sections"></a><span data-ttu-id="52811-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="52811-120">Related Sections</span></span>  
  
-   [<span data-ttu-id="52811-121">数据挖掘基础教程</span><span class="sxs-lookup"><span data-stu-id="52811-121">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
     <span data-ttu-id="52811-122">本教程介绍了基本概念，例如如何创建项目以及如何生成挖掘结构和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="52811-122">This tutorial introduces basic concepts, such as how to create a project and how to build mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="52811-123">中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="52811-123">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
     <span data-ttu-id="52811-124">本教程包含一系列独立课程，每个课程向您介绍不同的模型类型。</span><span class="sxs-lookup"><span data-stu-id="52811-124">This tutorial contains a number of independent lessons, each introducing you to a different model type.</span></span> <span data-ttu-id="52811-125">每个课程向您演示创建模型、浏览模型、自定义模型以及创建预测查询的过程。</span><span class="sxs-lookup"><span data-stu-id="52811-125">Each lesson walks you through the process of creating a model, exploring the model, and then customizing the model and creating prediction queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52811-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52811-126">See Also</span></span>  
 <span data-ttu-id="52811-127">[数据挖掘解决方案](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="52811-127">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="52811-128">[数据挖掘工具](../../2014/analysis-services/data-mining/data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="52811-128">[Data Mining Tools](../../2014/analysis-services/data-mining/data-mining-tools.md) </span></span>  
 [<span data-ttu-id="52811-129">数据挖掘项目</span><span class="sxs-lookup"><span data-stu-id="52811-129">Data Mining Projects</span></span>](../../2014/analysis-services/data-mining/data-mining-projects.md)  
  
  
