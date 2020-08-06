---
title: 第3课：添加和处理模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cc29927a-c368-4b8a-bbd0-af89a9f54dc9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da034089d8bbe7f1a967258d195a56ddbf13c03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577941"
---
# <a name="lesson-3-adding-and-processing-models"></a><span data-ttu-id="d53cd-102">第 3 课：添加和处理模型</span><span class="sxs-lookup"><span data-stu-id="d53cd-102">Lesson 3: Adding and Processing Models</span></span>
  <span data-ttu-id="d53cd-103">您在上一课中创建的挖掘结构包含一个基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d53cd-103">The mining structure that you created in the previous lesson contains a single mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="d53cd-104">您可以使用此模型来标识目标邮递活动的客户。</span><span class="sxs-lookup"><span data-stu-id="d53cd-104">You can use this model to identify customers for the targeted mailing campaign.</span></span> <span data-ttu-id="d53cd-105">但是，为了确保您的分析是全面的，更常见的做法是使用不同算法创建相关模型并比较其结果。</span><span class="sxs-lookup"><span data-stu-id="d53cd-105">However, to ensure that your analysis is thorough, it is a common practice to create related models using different algorithms and compare their results.</span></span> <span data-ttu-id="d53cd-106">通过这种方式，您也可以获得不同的理解。</span><span class="sxs-lookup"><span data-stu-id="d53cd-106">That way you can get different insights as well.</span></span> <span data-ttu-id="d53cd-107">因此，您将创建两个其他模型，然后处理并部署这两个模型。</span><span class="sxs-lookup"><span data-stu-id="d53cd-107">Therefore, you will create two additional models, then process and deploy the models.</span></span>  
  
 <span data-ttu-id="d53cd-108">在本课中，您将创建一组挖掘模型，这些模型将提示潜在客户列表中最有可能购买产品的客户。</span><span class="sxs-lookup"><span data-stu-id="d53cd-108">In this lesson, you will create a set of mining models that will suggest the most likely customers from a list of potential customers.</span></span>  
  
 <span data-ttu-id="d53cd-109">若要完成本课中的任务，您将使用[Microsoft 聚类分析算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)和[Microsoft Naive Bayes 算法](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="d53cd-109">To complete the tasks in this lesson, you will use the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and the [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md).</span></span>  
  
 <span data-ttu-id="d53cd-110">本课程包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="d53cd-110">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="d53cd-111">将新模型添加到目标邮件结构 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="d53cd-111">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="d53cd-112">在目标邮件结构中处理模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="d53cd-112">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="d53cd-113">课程中的第一个任务</span><span class="sxs-lookup"><span data-stu-id="d53cd-113">First Task in Lesson</span></span>  
 [<span data-ttu-id="d53cd-114">将新模型添加到目标邮件结构 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="d53cd-114">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="d53cd-115">前一课</span><span class="sxs-lookup"><span data-stu-id="d53cd-115">Previous Lesson</span></span>  
 [<span data-ttu-id="d53cd-116">第2课： &#40;基本数据挖掘教程生成目标邮件结构&#41;</span><span class="sxs-lookup"><span data-stu-id="d53cd-116">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="d53cd-117">下一课</span><span class="sxs-lookup"><span data-stu-id="d53cd-117">Next Lesson</span></span>  
 [<span data-ttu-id="d53cd-118">第4课：浏览目标邮件模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="d53cd-118">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="d53cd-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d53cd-119">See Also</span></span>  
 [<span data-ttu-id="d53cd-120">向结构中添加挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="d53cd-120">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)  
  
  
