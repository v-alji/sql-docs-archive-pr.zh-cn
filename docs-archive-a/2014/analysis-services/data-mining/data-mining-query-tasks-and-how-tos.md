---
title: 数据挖掘查询任务和操作指南 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], how-to topics
ms.assetid: 1bc2a775-6e62-4c66-a53c-201f2ea66295
author: minewiskan
ms.author: owend
ms.openlocfilehash: 454a3af33d0c18232bb36771235b328a17da6b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591010"
---
# <a name="data-mining-query-tasks-and-how-tos"></a><span data-ttu-id="dee1f-102">数据挖掘查询任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="dee1f-102">Data Mining Query Tasks and How-tos</span></span>
  <span data-ttu-id="dee1f-103">创建查询的功能对于使用您的数据挖掘模型十分重要。</span><span class="sxs-lookup"><span data-stu-id="dee1f-103">The ability to create queries is critical if you are to make use of your data mining models.</span></span> <span data-ttu-id="dee1f-104">本节提供一些示例链接，这些示例演示如何通过使用在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中提供的工具创建针对数据挖掘模型的查询。</span><span class="sxs-lookup"><span data-stu-id="dee1f-104">This section provides links to examples of how to create queries against a data mining model by using the tools provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="dee1f-105">有关数据挖掘查询的涵义或可创建的不同类型查询的详细信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="dee1f-105">If you need more information about what a data mining query is, or the different types of queries you can create, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="creating-queries-with-prediction-query-builder"></a><span data-ttu-id="dee1f-106">使用预测查询生成器创建查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-106">Creating Queries with Prediction Query Builder</span></span>  
 <span data-ttu-id="dee1f-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中均提供预测查询生成器，作为以图形形式对数据挖掘模型生成查询的一种方法。</span><span class="sxs-lookup"><span data-stu-id="dee1f-107">The Prediction Query Builder is provided in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a way of graphically building queries against data mining models.</span></span> <span data-ttu-id="dee1f-108">下面的主题说明如何选择模型、指定数据源、自定义预测和保存输出。</span><span class="sxs-lookup"><span data-stu-id="dee1f-108">The following topics explain how you can select a model, specify a data source, customize the predictions, and save output.</span></span>  
  
-   [<span data-ttu-id="dee1f-109">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-109">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="dee1f-110">在数据挖掘设计器中创建单独查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-110">Create a Singleton Query in the Data Mining Designer</span></span>](create-a-singleton-query-in-the-data-mining-designer.md)  
  
-   [<span data-ttu-id="dee1f-111">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-111">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)  
  
-   [<span data-ttu-id="dee1f-112">查看和保存预测查询的结果</span><span class="sxs-lookup"><span data-stu-id="dee1f-112">View and Save the Results of a Prediction Query</span></span>](view-and-save-the-results-of-a-prediction-query.md)  
  
-   [<span data-ttu-id="dee1f-113">手动编辑预测查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-113">Manually Edit a Prediction Query</span></span>](manually-edit-a-prediction-query.md)  
  
-   [<span data-ttu-id="dee1f-114">将预测函数应用于模型</span><span class="sxs-lookup"><span data-stu-id="dee1f-114">Apply Prediction Functions to a Model</span></span>](apply-prediction-functions-to-a-model.md)  
  
-   [<span data-ttu-id="dee1f-115">为预测查询选择和映射输入数据</span><span class="sxs-lookup"><span data-stu-id="dee1f-115">Choose and Map Input Data for a Prediction Query</span></span>](choose-and-map-input-data-for-a-prediction-query.md)  
  
## <a name="using-other-data-mining-query-tools"></a><span data-ttu-id="dee1f-116">使用其他数据挖掘查询工具</span><span class="sxs-lookup"><span data-stu-id="dee1f-116">Using Other Data Mining Query Tools</span></span>  
 <span data-ttu-id="dee1f-117">除了使用预测查询生成器之外，还可以使用 DMX 或 XMLA 将查询直接键入 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="dee1f-117">In addition to using the Prediction Query Builder, you can type a query directly into [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using DMX or by using XMLA.</span></span> <span data-ttu-id="dee1f-118">您还可以通过编程方式生成预测查询并且将这些查询发送到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="dee1f-118">You can also build prediction queries programmatically and send them to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="dee1f-119">下面的主题提供有关如何在预测查询生成器之外创建和使用预测查询的详细信息。</span><span class="sxs-lookup"><span data-stu-id="dee1f-119">The following topics provide more information about how to create and work with prediction queries outside of the Prediction Query Builder.</span></span>  
  
 [<span data-ttu-id="dee1f-120">通过模板创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-120">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="dee1f-121">介绍如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的工具来生成并运行预测查询。</span><span class="sxs-lookup"><span data-stu-id="dee1f-121">Describes how to use the tools in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to build and run a prediction query.</span></span>  
  
 [<span data-ttu-id="dee1f-122">通过模板创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-122">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
 <span data-ttu-id="dee1f-123">介绍如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中提供的模板来向预测查询添加参数。</span><span class="sxs-lookup"><span data-stu-id="dee1f-123">Describes how to use the templates that are provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add parameters to a prediction query.</span></span>  
  
 [<span data-ttu-id="dee1f-124">更改数据挖掘查询的超时值</span><span class="sxs-lookup"><span data-stu-id="dee1f-124">Change the Time-out Value for Data Mining Queries</span></span>](change-the-time-out-value-for-data-mining-queries.md)  
 <span data-ttu-id="dee1f-125">介绍如何在服务器上设置可控制数据挖掘查询的相关行为的属性。</span><span class="sxs-lookup"><span data-stu-id="dee1f-125">Describes how to set properties on the server that control behavior related to data mining queries.</span></span>  
  
 [<span data-ttu-id="dee1f-126">针对挖掘模型创建内容查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-126">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
 <span data-ttu-id="dee1f-127">介绍如何通过使用数据挖掘架构行集来创建返回挖掘模型中存储的详细信息的查询。</span><span class="sxs-lookup"><span data-stu-id="dee1f-127">Describes how to create queries that return detailed information that is stored in the mining model by using the data mining schema rowsets.</span></span>  
  
 [<span data-ttu-id="dee1f-128">使用 XMLA 创建数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="dee1f-128">Create a Data Mining Query by Using XMLA</span></span>](create-a-data-mining-query-by-using-xmla.md)  
 <span data-ttu-id="dee1f-129">介绍如何通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 XMLA 模板，创建针对挖掘模型内容的查询。</span><span class="sxs-lookup"><span data-stu-id="dee1f-129">Describes how to create a query against mining model content by using the XMLA templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee1f-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dee1f-130">See Also</span></span>  
 <span data-ttu-id="dee1f-131">[查询和表达式语言参考 &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span><span class="sxs-lookup"><span data-stu-id="dee1f-131">[Query and Expression Language Reference &#40;Analysis Services&#41;](https://msdn.microsoft.com/library/gg492188(SQL.130).aspx) </span></span>  
 [<span data-ttu-id="dee1f-132">数据挖掘存储过程（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="dee1f-132">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
