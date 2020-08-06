---
title: 数据挖掘算法 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589978"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a><span data-ttu-id="1c7ae-102">数据挖掘算法（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="1c7ae-102">Data Mining Algorithms (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="1c7ae-103">Office 数据挖掘外接程序支持使用以下数据挖掘算法创建分析模型。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-103">The Data Mining Add-ins for Office supports creation of analytical models using the following data mining algorithms.</span></span> <span data-ttu-id="1c7ae-104">所有算法基于已知的计算机学习方法，并已由 Microsoft 研究院实现。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-104">All algorithms are based on well-known machine learning methods and have been implemented by Microsoft Research.</span></span>  
  
## <a name="algorithms"></a><span data-ttu-id="1c7ae-105">算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-105">Algorithms</span></span>  
  
|<span data-ttu-id="1c7ae-106">计算机学习方法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-106">Machine learning method</span></span>|<span data-ttu-id="1c7ae-107">工作原理</span><span class="sxs-lookup"><span data-stu-id="1c7ae-107">How it works</span></span>|  
|-----------------------------|------------------|  
|<span data-ttu-id="1c7ae-108">Microsoft 关联规则算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-108">Microsoft Association Rules  algorithm</span></span>|<span data-ttu-id="1c7ae-109">了解哪些产品一起被购买或哪些事件一起发生，并使用该模型生成一些建议。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-109">Discover which products are purchased together or which events occur together, and use the model to create recommendations.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|<span data-ttu-id="1c7ae-110">Microsoft 聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-110">Microsoft Clustering algorithm</span></span>|<span data-ttu-id="1c7ae-111">定义市场细分，自动将相关客户归入一组，或在数据中查找关系以供进一步挖掘时使用。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-111">Define market segments, automatically group related customers together, or find relationships in data to use in further mining.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|<span data-ttu-id="1c7ae-112">Microsoft 决策树算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-112">Microsoft Decision Trees algorithm</span></span>|<span data-ttu-id="1c7ae-113">识别数据的各个元素之间的以前未知的关系，以更好地进行决策或查找导致特定结果的因素。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-113">Identify previously unknown relationships between various elements of your data to better inform your decisions, or find the factors that lead to specific outcomes.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|<span data-ttu-id="1c7ae-114">Microsoft 线性回归算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-114">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="1c7ae-115">查找描述导致数值结果的因素的数学表达式。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-115">Find a mathematical formula that describes factors that contribute to a numeric outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|<span data-ttu-id="1c7ae-116">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-116">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="1c7ae-117">识别导致二进制结果的因素，并了解如何使用它们来影响结果。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-117">Identify the factors that contribute to binary outcomes, and learn how to use those to affect results.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|<span data-ttu-id="1c7ae-118">Microsoft Naïve Bayes 算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-118">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="1c7ae-119">发现数据中的关系并查找那些与结果最有关的关系。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-119">Explore relationships in your data and find those mostly closely correlated with an outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|<span data-ttu-id="1c7ae-120">Microsoft 神经网络算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-120">Microsoft Neural Networks algorithm</span></span>|<span data-ttu-id="1c7ae-121">查找多个输入以及甚至多个输出之间隐藏的关系。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-121">Find hidden relationships among multiple inputs and even multiple outputs.</span></span> <span data-ttu-id="1c7ae-122">用于探索或预测。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-122">Use for exploration or for prediction.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|<span data-ttu-id="1c7ae-123">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="1c7ae-123">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="1c7ae-124">使用历史数据来预测将来的值。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-124">Use historical data to forecast future values.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a><span data-ttu-id="1c7ae-125">高级选项</span><span class="sxs-lookup"><span data-stu-id="1c7ae-125">Advanced Options</span></span>  
 <span data-ttu-id="1c7ae-126">使用 Excel 数据挖掘客户端时，您可以选择创建自己的数据挖掘结构和模型，或优化算法的参数。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-126">When you use the Data Mining Client for Excel, you have the option to create your own data mining structures and models, or to fine-tune the parameters of the algorithms.</span></span>  
  
 [<span data-ttu-id="1c7ae-127">SQL Server 数据挖掘外接程序的算法参数 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7ae-127">Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;</span></span>](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 <span data-ttu-id="1c7ae-128">使用这些高级选项可以两种方式来自定义您的模型：</span><span class="sxs-lookup"><span data-stu-id="1c7ae-128">There are two ways to customize your models using these advanced options:</span></span>  
  
-   <span data-ttu-id="1c7ae-129">使用 **“数据挖掘查询”** 向导创建您的模型。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-129">Use the **Data Mining Query** wizard to create your model.</span></span>  
  
-   <span data-ttu-id="1c7ae-130">在 **“数据挖掘客户端”** 中，在启动向导后，单击 **“参数”**。</span><span class="sxs-lookup"><span data-stu-id="1c7ae-130">In the **Data Mining Client**, after you start the wizard, click **Parameters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7ae-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c7ae-131">See Also</span></span>  
 <span data-ttu-id="1c7ae-132">[查询 &#40;SQL Server 数据挖掘外接程序&#41;](query-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="1c7ae-132">[Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="1c7ae-133">&#40;Excel 数据挖掘外接程序的高级建模&#41;</span><span class="sxs-lookup"><span data-stu-id="1c7ae-133">Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;</span></span>](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
