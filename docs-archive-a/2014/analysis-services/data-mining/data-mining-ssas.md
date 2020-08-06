---
title: 数据挖掘 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7044ee397d457f7924d0db99dbec6659f969f104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589373"
---
# <a name="data-mining-ssas"></a><span data-ttu-id="ee4ec-102">数据挖掘 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="ee4ec-102">Data Mining (SSAS)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ee4ec-103">为合并数据挖掘的解决方案提供一个集成的平台。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-103">provides an integrated platform for solutions that incorporate data mining.</span></span> <span data-ttu-id="ee4ec-104">您可以使用关系数据或多维数据集数据创建具有预测分析功能的商业智能解决方案。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-104">You can use either relational or cube data to create business intelligence solutions with predictive analytics.</span></span>  
  
## <a name="benefits-of-data-mining"></a><span data-ttu-id="ee4ec-105">数据挖掘的优点</span><span class="sxs-lookup"><span data-stu-id="ee4ec-105">Benefits of Data Mining</span></span>  
 <span data-ttu-id="ee4ec-106">数据挖掘使用精心研究的统计原则来发现您的数据中的模式，帮助您针对复杂问题作出明智的决策。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-106">Data mining uses well-researched statistical principles to discover patterns in your data, helping you make intelligent decisions about complex problems.</span></span> <span data-ttu-id="ee4ec-107">通过将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的数据挖掘算法应用于您的数据，您可以预测趋势、标识模式、创建规则和建议、分析复杂数据集中的事件顺序以及洞察新情况。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-107">By applying the data mining algorithms in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to your data, you can forecast trends, identify patterns, create rules and recommendations, analyze the sequence of events in complex data sets, and gain new insights.</span></span>  
  
 <span data-ttu-id="ee4ec-108">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的数据挖掘不仅功能强大和易于访问，并且与许多人在进行分析和报告工作时喜欢使用的工具集成在一起。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-108">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], data mining is powerful, accessible, and integrated with the tools that many people prefer to use for analysis and reporting.</span></span> <span data-ttu-id="ee4ec-109">通过查看本节中提供的链接，您可以获取在开始学习数据挖掘时需要掌握的丰富背景信息。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-109">See the links in this section to get the broad background about data mining that you need to get started.</span></span>  
  
## <a name="key-data-mining-features"></a><span data-ttu-id="ee4ec-110">关键数据挖掘功能</span><span class="sxs-lookup"><span data-stu-id="ee4ec-110">Key Data Mining Features</span></span>  
 <span data-ttu-id="ee4ec-111">SQL Server 提供了以下功能来支持集成的数据挖掘解决方案：</span><span class="sxs-lookup"><span data-stu-id="ee4ec-111">SQL Server provides the following features in support of integrated data mining solutions:</span></span>  
  
-   <span data-ttu-id="ee4ec-112">多个数据源：您无需创建数据仓库或 OLAP 多维数据集就可以执行数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-112">Multiple data sources: You do not have to create a data warehouse or an OLAP cube to do data mining.</span></span> <span data-ttu-id="ee4ec-113">你可以使用来自外部提供程序、电子表格甚至文本文件的表格格式数据。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-113">You can use tabular data from external providers, spreadsheets, and even text files.</span></span> <span data-ttu-id="ee4ec-114">此外，您还可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中轻松地挖掘创建的 OLAP 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-114">You can also easily mine OLAP cubes created in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ee4ec-115">但是，不能使用内存中数据库的数据。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-115">However, you cannot use data from an in-memory database.</span></span>  
  
-   <span data-ttu-id="ee4ec-116">集成的数据清理、数据管理和 ETL：Data Quality Services 提供了用于探查和清理数据的高级工具。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-116">Integrated data cleansing, data management, and ETL: Data Quality Services provides advanced tools for profiling and cleansing data.</span></span> <span data-ttu-id="ee4ec-117">Integration Services 可用于生成 ETL 进程以用于清理数据，并且还用于生成、处理、定型和更新模型。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-117">Integration Services can be used to build ETL processes for cleaning data, and also for building, processing, training, and updating models.</span></span>  
  
-   <span data-ttu-id="ee4ec-118">多个可自定义的算法：除了提供聚类分析、神经网络和决策树之类的算法之外，该平台还支持开发您自己的自定义插件算法。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-118">Multiple customizable algorithms: In addition to providing algorithms such as clustering, neural networks, and decisions trees, the platform supports development of your own custom plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="ee4ec-119">模型测试基础结构：使用重要的统计工具（例如交叉验证、分类矩阵、提升图和散点图）测试您的模型和数据集。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-119">Model testing infrastructure: Test your models and data sets using important statistical tools as cross-validation, classification matrices, lift charts, and scatter plots.</span></span> <span data-ttu-id="ee4ec-120">轻松创建和管理测试和定型集。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-120">Easily create and manage testing and training sets.</span></span>  
  
-   <span data-ttu-id="ee4ec-121">查询和钻取：创建预测查询、检索模型模式和统计信息以及钻取到事例数据。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-121">Querying and drillthrough: Create prediction queries, retrieve model patterns and statistics, and drill through to case data.</span></span>  
  
-   <span data-ttu-id="ee4ec-122">客户端工具：除了 SQL Server 提供的开发和设计工具之外，您还可以使用 Excel 数据挖掘外接程序来创建、查询和浏览模型。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-122">Client tools: In addition to the development and design studios provided by SQL Server, you can use the Data Mining Add-ins for Excel to create, query, and browse models.</span></span> <span data-ttu-id="ee4ec-123">或者，创建自定义的客户端，包括 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-123">Or, create custom clients, including Web services.</span></span>  
  
-   <span data-ttu-id="ee4ec-124">脚本语言支持和托管 API：所有数据挖掘对象都是完全可编程的。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-124">Scripting language support and managed API: All data mining objects are fully programmable.</span></span> <span data-ttu-id="ee4ec-125">可通过用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的 MDX、XMLA 或 PowerShell 扩展插件来撰写脚本。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-125">Scripting is possible through MDX, XMLA, or the PowerShell extensions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ee4ec-126">使用数据挖掘扩展插件 (DMX) 语言来进行快速查询和脚本撰写。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-126">Use the Data Mining Extensions (DMX) language for fast querying and scripting.</span></span>  
  
-   <span data-ttu-id="ee4ec-127">安全性和部署：通过 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供基于角色的安全性，包括用于钻取到模型和结构数据的单独权限。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-127">Security and deployment: Provides role-based security through [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], including separate permissions for drillthrough to model and structure data.</span></span> <span data-ttu-id="ee4ec-128">轻松地将模型部署到其他服务器，以便用户可以访问模式或执行预测。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-128">Easy deployment of models to other servers, so that users can access the patterns or perform predictions</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee4ec-129">本节内容</span><span class="sxs-lookup"><span data-stu-id="ee4ec-129">In This Section</span></span>  
 <span data-ttu-id="ee4ec-130">本节中的主题介绍 SQL Server 数据挖掘的主要功能和相关任务。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-130">The topics in this section introduce the principal features of SQL Server Data Mining and related tasks.</span></span>  
  
-   [<span data-ttu-id="ee4ec-131">数据挖掘概念</span><span class="sxs-lookup"><span data-stu-id="ee4ec-131">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
-   [<span data-ttu-id="ee4ec-132">数据挖掘算法（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="ee4ec-132">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ee4ec-133">挖掘结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="ee4ec-133">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ee4ec-134">挖掘模型（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="ee4ec-134">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ee4ec-135">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="ee4ec-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
-   [<span data-ttu-id="ee4ec-136">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="ee4ec-136">Data Mining Queries</span></span>](data-mining-queries.md)  
  
-   [<span data-ttu-id="ee4ec-137">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="ee4ec-137">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
-   [<span data-ttu-id="ee4ec-138">数据挖掘工具</span><span class="sxs-lookup"><span data-stu-id="ee4ec-138">Data Mining Tools</span></span>](data-mining-tools.md)  
  
-   [<span data-ttu-id="ee4ec-139">数据挖掘体系结构</span><span class="sxs-lookup"><span data-stu-id="ee4ec-139">Data Mining Architecture</span></span>](data-mining-architecture.md)  
  
-   [<span data-ttu-id="ee4ec-140">安全性概述（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="ee4ec-140">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
  
