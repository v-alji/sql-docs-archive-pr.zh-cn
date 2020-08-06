---
title: 第5课：测试模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fcfd9a9e90d9c6800af4dfd1599bbdd62d9520ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690917"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a><span data-ttu-id="b6b56-102">第 5 课：测试模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b6b56-102">Lesson 5: Testing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b6b56-103">现在，已使用目标邮递方案定型集处理了模型，将针对测试集来测试模型。</span><span class="sxs-lookup"><span data-stu-id="b6b56-103">Now that you have processed the model by using the targeted mailing scenario training set, you will test your models against the testing set.</span></span> <span data-ttu-id="b6b56-104">验证是数据挖掘过程中的重要步骤。</span><span class="sxs-lookup"><span data-stu-id="b6b56-104">Validation is an important step in the data mining process.</span></span> <span data-ttu-id="b6b56-105">在将挖掘模型部署到生产环境之前，了解目标邮递挖掘模型针对实际数据的性能很重要。</span><span class="sxs-lookup"><span data-stu-id="b6b56-105">Knowing how well your targeted mailing mining models perform against real data is important before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="b6b56-106">由于测试集内的数据已经包含了自行车购买的已知值，因此可以方便地确定模型的预测是否准确。</span><span class="sxs-lookup"><span data-stu-id="b6b56-106">Because the data in the testing set already contains known values for bike buying, it is easy to determine whether the model's predictions are correct.</span></span> <span data-ttu-id="b6b56-107">市场部将使用最佳模型 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 来识别其目标邮递活动的客户。</span><span class="sxs-lookup"><span data-stu-id="b6b56-107">The model that performs the best will be used by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department to identify the customers for their targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="b6b56-108">在本课中，您将使用多种方法验证模型：</span><span class="sxs-lookup"><span data-stu-id="b6b56-108">In this lesson you will validate your models using multiple methods:</span></span>  
  
1.  <span data-ttu-id="b6b56-109">您将针对测试集进行预测，以查看模型对已知结果的准确程度。</span><span class="sxs-lookup"><span data-stu-id="b6b56-109">You'll make predictions against the testing set to see how accurate the model is on known results.</span></span> <span data-ttu-id="b6b56-110">你将使用*提升图*来度量其有效性。</span><span class="sxs-lookup"><span data-stu-id="b6b56-110">You'll use a *lift chart* to measure its effectiveness.</span></span>  
  
     [<span data-ttu-id="b6b56-111">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b6b56-111">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  <span data-ttu-id="b6b56-112">您将针对筛选的数据子集来测试模型。</span><span class="sxs-lookup"><span data-stu-id="b6b56-112">You will test your models on a filtered subset of the data.</span></span> <span data-ttu-id="b6b56-113">您可以在同一提升图中比较多个模型。</span><span class="sxs-lookup"><span data-stu-id="b6b56-113">You can compare multiple models in the same lift chart.</span></span>  
  
     [<span data-ttu-id="b6b56-114">&#40;数据挖掘基础教程中测试筛选的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b56-114">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="b6b56-115">有关模型验证一般情况的详细信息，请参阅[数据挖掘概念](../../2014/analysis-services/data-mining/data-mining-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b56-115">For more information about how model validation in general, see [Data Mining Concepts](../../2014/analysis-services/data-mining/data-mining-concepts.md).</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="b6b56-116">课程中的第一个任务</span><span class="sxs-lookup"><span data-stu-id="b6b56-116">First Task in Lesson</span></span>  
 [<span data-ttu-id="b6b56-117">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b6b56-117">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="b6b56-118">前一课</span><span class="sxs-lookup"><span data-stu-id="b6b56-118">Previous Lesson</span></span>  
 [<span data-ttu-id="b6b56-119">第4课：浏览目标邮件模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b6b56-119">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="b6b56-120">下一课</span><span class="sxs-lookup"><span data-stu-id="b6b56-120">Next Lesson</span></span>  
 [<span data-ttu-id="b6b56-121">第 6 课：创建和使用预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b6b56-121">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b6b56-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6b56-122">See Also</span></span>  
 <span data-ttu-id="b6b56-123">["提升图" 选项卡 &#40;挖掘准确性图表视图&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="b6b56-123">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span></span>  
 <span data-ttu-id="b6b56-124">[Analysis Services &#40;提升图表&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b6b56-124">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b6b56-125">[测试和验证 &#40;数据挖掘&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b6b56-125">[Testing and Validation &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="b6b56-126">["分类矩阵" 选项卡 &#40;挖掘准确性图表视图&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="b6b56-126">[Classification Matrix Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span></span>  
 [<span data-ttu-id="b6b56-127">分类矩阵（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="b6b56-127">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
