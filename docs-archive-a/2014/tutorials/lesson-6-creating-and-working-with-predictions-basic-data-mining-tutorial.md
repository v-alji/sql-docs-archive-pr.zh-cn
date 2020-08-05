---
title: 第6课：创建和使用预测 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b213cb58-2c40-4c89-b08b-d3c36a4afad3
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d0a8bfdf83e96622a19ac72490e8602d12afc9df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579905"
---
# <a name="lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="c631f-102">第 6 课：创建和使用预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c631f-102">Lesson 6: Creating and Working with Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c631f-103">您已经定型、测试并浏览了创建的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="c631f-103">You have trained, tested, and explored the data mining models you created.</span></span> <span data-ttu-id="c631f-104">现在已准备好使用模型来标识最可能响应新目标邮递活动的人。</span><span class="sxs-lookup"><span data-stu-id="c631f-104">Now you are ready to use the models to identify the people most likely to respond to the new targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="c631f-105">在本课中，您将创建查询来预测哪些客户最有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="c631f-105">In this lesson you will create a query to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="c631f-106">您还将检索预测正确的*概率*，以便市场营销部门可以决定是否要使用该预测。</span><span class="sxs-lookup"><span data-stu-id="c631f-106">You will also retrieve the *probability* that the prediction is correct, so the marketing department can decide whether to you can decide whether to use the prediction or not.</span></span>  
  
 <span data-ttu-id="c631f-107">在对很有可能购买自行车的客户进行标识后，您将钻取挖掘模型中事例的详细信息，以检索这些客户的姓名和联系信息。</span><span class="sxs-lookup"><span data-stu-id="c631f-107">Once you have identified customers with a high probability of purchasing a bike, you will drill through to the details of the cases in the mining model to retrieve names and contact information for these customers.</span></span>  
  
 <span data-ttu-id="c631f-108">本课程包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="c631f-108">This lesson contains the following topics:</span></span>  
  
 [<span data-ttu-id="c631f-109">创建预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c631f-109">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="c631f-110">对结构数据使用钻取 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="c631f-110">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="c631f-111">下一课</span><span class="sxs-lookup"><span data-stu-id="c631f-111">Next Lesson</span></span>  
 [<span data-ttu-id="c631f-112">中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;</span><span class="sxs-lookup"><span data-stu-id="c631f-112">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="c631f-113">前一课</span><span class="sxs-lookup"><span data-stu-id="c631f-113">Previous Lesson</span></span>  
 [<span data-ttu-id="c631f-114">第5课：测试模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="c631f-114">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c631f-115">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c631f-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c631f-116">创建预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="c631f-116">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c631f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c631f-117">See Also</span></span>  
 <span data-ttu-id="c631f-118">[&#40;Analysis Services 数据挖掘的决策树模型的挖掘模型内容&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c631f-118">[Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="c631f-119">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="c631f-119">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
