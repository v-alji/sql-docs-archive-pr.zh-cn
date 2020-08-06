---
title: 时序预测 DMX 教程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fbc9a0640767b3fbae04cebb9a047c2ec2b669b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578564"
---
# <a name="time-series-prediction-dmx-tutorial"></a><span data-ttu-id="f4c90-102">时序预测 DMX 教程</span><span class="sxs-lookup"><span data-stu-id="f4c90-102">Time Series Prediction DMX Tutorial</span></span>
  <span data-ttu-id="f4c90-103">在本教程中，将学习如何创建时序挖掘结构，创建三个自定义时序挖掘模型，然后使用这些模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="f4c90-103">In this tutorial, you will learn how to create a time series mining structure, create three custom time series mining models, and then make predictions by using those models.</span></span>  
  
 <span data-ttu-id="f4c90-104">挖掘模型基于 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 示例数据库（存储虚构公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的数据）中所包含的数据。</span><span class="sxs-lookup"><span data-stu-id="f4c90-104">The mining models are based on the data contained in the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f4c90-105">是一家大型跨国制造公司。</span><span class="sxs-lookup"><span data-stu-id="f4c90-105">is a large, multinational manufacturing company.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="f4c90-106">教程方案</span><span class="sxs-lookup"><span data-stu-id="f4c90-106">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f4c90-107">已经决定使用数据挖掘功能来生成销售预测。</span><span class="sxs-lookup"><span data-stu-id="f4c90-107">has decided to use data mining to generate sales projections.</span></span> <span data-ttu-id="f4c90-108">它们已经生成了一些区域预测模型;有关详细信息，请参阅[第2课：生成预测方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c90-108">They have already built some regional forecasting models; for more information, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="f4c90-109">但是，销售部门需要能够定期用新的销售数据更新数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-109">However, the Sales Department needs to be able to periodically update the data mining model with new sales data.</span></span> <span data-ttu-id="f4c90-110">它们还希望自定义模型来提供不同的预测。</span><span class="sxs-lookup"><span data-stu-id="f4c90-110">They also want to customize the models to provide different projections.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="f4c90-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供了多个可用于完成此任务的工具：</span><span class="sxs-lookup"><span data-stu-id="f4c90-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="f4c90-112">数据挖掘扩展插件 (DMX) 查询语言</span><span class="sxs-lookup"><span data-stu-id="f4c90-112">The Data Mining Extensions (DMX) query language</span></span>  
  
-   <span data-ttu-id="f4c90-113">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="f4c90-113">The Microsoft Time Series Algorithm</span></span>  
  
-   <span data-ttu-id="f4c90-114"> 中的查询编辑器</span><span class="sxs-lookup"><span data-stu-id="f4c90-114">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="f4c90-115"> 时序算法创建可用于预测时间相关数据的模型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-115">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates models that can be used for prediction of time-related data.</span></span> <span data-ttu-id="f4c90-116">数据挖掘扩展插件 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一种查询语言，可用来创建挖掘模型和预测查询。</span><span class="sxs-lookup"><span data-stu-id="f4c90-116">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create mining models and prediction queries.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="f4c90-117">学习内容</span><span class="sxs-lookup"><span data-stu-id="f4c90-117">What You Will Learn</span></span>  
 <span data-ttu-id="f4c90-118">本教程假定您已经熟悉 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用来创建挖掘模型的对象。</span><span class="sxs-lookup"><span data-stu-id="f4c90-118">This tutorial assumes that you are already familiar with the objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="f4c90-119">如果以前未使用 DMX 创建挖掘结构或挖掘模型，请参阅[自行车购买者 DMX 教程](../../2014/tutorials/bike-buyer-dmx-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="f4c90-119">If you have not previously created a mining structure or mining model by using DMX, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
 <span data-ttu-id="f4c90-120">本教程分为以下几课：</span><span class="sxs-lookup"><span data-stu-id="f4c90-120">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="f4c90-121">第 1 课：创建时序挖掘模型和挖掘结构</span><span class="sxs-lookup"><span data-stu-id="f4c90-121">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 <span data-ttu-id="f4c90-122">在本课中，您将学习如何使用 `CREATE MINING MODEL` 语句添加新的预测模型及其相关的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-122">In this lesson, you will learn how to use the `CREATE MINING MODEL` statement to add a new forecasting model and a related mining model.</span></span>  
  
 [<span data-ttu-id="f4c90-123">第 2 课：向时序挖掘结构添加挖掘模型</span><span class="sxs-lookup"><span data-stu-id="f4c90-123">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 <span data-ttu-id="f4c90-124">在本课中，您将学习如何使用 ALTER MINING STRUCTURE 语句向时序结构中添加新的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-124">In this lesson, you will learn how to use the ALTER MINING STRUCTURE statement to add new mining models to the time series structure.</span></span> <span data-ttu-id="f4c90-125">您还将学习如何自定义用来分析时序的算法。</span><span class="sxs-lookup"><span data-stu-id="f4c90-125">You will also learn how to customize the algorithm used for analyzing a time series.</span></span>  
  
 [<span data-ttu-id="f4c90-126">第 3 课：准备时序结构和模型</span><span class="sxs-lookup"><span data-stu-id="f4c90-126">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 <span data-ttu-id="f4c90-127">在本课中，您将学习如何使用 `INSERT INTO` 语句并用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 数据库中的数据填充结构来为模型定型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-127">In this lesson, you will learn how to train the models by using the `INSERT INTO` statement and populating the structure with data from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 [<span data-ttu-id="f4c90-128">第 4 课：使用 DMX 创建时序预测</span><span class="sxs-lookup"><span data-stu-id="f4c90-128">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 <span data-ttu-id="f4c90-129">在本课中，您将学习如何创建时序预测。</span><span class="sxs-lookup"><span data-stu-id="f4c90-129">In this lesson, you will learn how to create time series predictions.</span></span>  
  
 [<span data-ttu-id="f4c90-130">第 5 课：扩展时序模型</span><span class="sxs-lookup"><span data-stu-id="f4c90-130">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 <span data-ttu-id="f4c90-131">在本课中，您将学习在进行预测时，如何使用 `EXTEND_MODEL_CASES` 参数用新数据更新模型。</span><span class="sxs-lookup"><span data-stu-id="f4c90-131">In this lesson, you will learn how to use the `EXTEND_MODEL_CASES` parameter to update the model with new data when you make predictions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c90-132">要求</span><span class="sxs-lookup"><span data-stu-id="f4c90-132">Requirements</span></span>  
 <span data-ttu-id="f4c90-133">执行本教程前，请确保安装了下列各项：</span><span class="sxs-lookup"><span data-stu-id="f4c90-133">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f4c90-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c90-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f4c90-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c90-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="f4c90-136"> 数据库</span><span class="sxs-lookup"><span data-stu-id="f4c90-136">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="f4c90-137">为了增强安全性，默认情况下将不安装该示例数据库。</span><span class="sxs-lookup"><span data-stu-id="f4c90-137">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="f4c90-138">若要安装的正式示例数据库 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) Microsoft SQL Server 产品示例 "部分中的" Microsoft SQL Server 示例和社区项目 "主页。</span><span class="sxs-lookup"><span data-stu-id="f4c90-138">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="f4c90-139">单击 "**数据库**"，再单击 "**发布**" 选项卡，然后选择所需的数据库。</span><span class="sxs-lookup"><span data-stu-id="f4c90-139">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4c90-140">查看教程时，建议您将 "**下一个主题**" 和 "**上一个主题**" 按钮添加到文档查看器工具栏。</span><span class="sxs-lookup"><span data-stu-id="f4c90-140">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c90-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4c90-141">See Also</span></span>  
 <span data-ttu-id="f4c90-142">[数据挖掘基础教程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f4c90-142">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="f4c90-143">中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="f4c90-143">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
