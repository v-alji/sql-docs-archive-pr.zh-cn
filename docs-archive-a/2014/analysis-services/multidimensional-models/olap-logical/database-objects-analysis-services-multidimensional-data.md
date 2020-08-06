---
title: Analysis Services 多维数据)  (数据库对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694621"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="391fa-102">数据库对象（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="391fa-102">Database Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="391fa-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例包含用于联机分析处理 (OLAP) 和数据挖掘的数据库对象和程序集。</span><span class="sxs-lookup"><span data-stu-id="391fa-103">A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance contains database objects and assemblies for use with online analytical processing (OLAP) and data mining.</span></span>  
  
-   <span data-ttu-id="391fa-104">数据库包含 OLAP 和数据挖掘对象，例如数据源、数据源视图、多维数据集、度量值、度量值组、维度、属性、层次结构、挖掘结构、挖掘模型和角色。</span><span class="sxs-lookup"><span data-stu-id="391fa-104">Databases contain OLAP and data mining objects, such as data sources, data source views, cubes, measures, measure groups, dimensions, attributes, hierarchies, mining structures, mining models and roles.</span></span>  
  
-   <span data-ttu-id="391fa-105">程序集中包含用户定义的函数，这些函数对多维表达式 (MDX) 和数据挖掘扩展插件 (DMX) 语言所提供的内部函数的功能进行了扩展。</span><span class="sxs-lookup"><span data-stu-id="391fa-105">Assemblies contain user-defined functions that extend the functionality of the intrinsic functions provided with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span>  
  
 <span data-ttu-id="391fa-106"><xref:Microsoft.AnalysisServices.Database> 对象是商业智能项目（如 OLAP 多维数据集、维度和数据挖掘结构）需要的所有数据对象及其支持对象（如 <xref:Microsoft.AnalysisServices.DataSource>、<xref:Microsoft.AnalysisServices.Account> 和 <xref:Microsoft.AnalysisServices.Role>）的容器。</span><span class="sxs-lookup"><span data-stu-id="391fa-106">The <xref:Microsoft.AnalysisServices.Database> object is the container for all data objects that are needed for a business intelligence project (such as OLAP cubes, dimensions, and data mining structures), and their supporting objects (such as <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account>, and <xref:Microsoft.AnalysisServices.Role>).</span></span>  
  
 <span data-ttu-id="391fa-107"><xref:Microsoft.AnalysisServices.Database> 对象可提供对包含以下项的对象和属性的访问：</span><span class="sxs-lookup"><span data-stu-id="391fa-107">A <xref:Microsoft.AnalysisServices.Database> object provides access to objects and attributes that include the following:</span></span>  
  
-   <span data-ttu-id="391fa-108">可访问的所有多维数据集，以一个集合表示。</span><span class="sxs-lookup"><span data-stu-id="391fa-108">All cubes that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="391fa-109">可访问的所有维度，以一个集合表示。</span><span class="sxs-lookup"><span data-stu-id="391fa-109">All dimensions that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="391fa-110">可访问的所有挖掘结构，以一个集合表示。</span><span class="sxs-lookup"><span data-stu-id="391fa-110">All mining structures that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="391fa-111">所有数据源和数据源视图，以两个集合表示。</span><span class="sxs-lookup"><span data-stu-id="391fa-111">All data sources and data source views, as two collections.</span></span>  
  
-   <span data-ttu-id="391fa-112">所有角色和数据库权限，以两个集合表示。</span><span class="sxs-lookup"><span data-stu-id="391fa-112">All roles and database permissions, as two collections.</span></span>  
  
-   <span data-ttu-id="391fa-113">数据库的排序规则值。</span><span class="sxs-lookup"><span data-stu-id="391fa-113">The collation value for the database.</span></span>  
  
-   <span data-ttu-id="391fa-114">数据库的估计大小。</span><span class="sxs-lookup"><span data-stu-id="391fa-114">The estimated size of the database.</span></span>  
  
-   <span data-ttu-id="391fa-115">数据库的语言值。</span><span class="sxs-lookup"><span data-stu-id="391fa-115">The language value of the database.</span></span>  
  
-   <span data-ttu-id="391fa-116">数据库的可见设置。</span><span class="sxs-lookup"><span data-stu-id="391fa-116">The visible setting for the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="391fa-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="391fa-117">In This Section</span></span>  
 <span data-ttu-id="391fa-118">以下主题介绍 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中 OLAP 和数据挖掘功能共享的对象。</span><span class="sxs-lookup"><span data-stu-id="391fa-118">The following topics describe objects shared by both OLAP and data mining features in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="391fa-119">主题</span><span class="sxs-lookup"><span data-stu-id="391fa-119">Topic</span></span>|<span data-ttu-id="391fa-120">说明</span><span class="sxs-lookup"><span data-stu-id="391fa-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="391fa-121">多维模型中的数据源</span><span class="sxs-lookup"><span data-stu-id="391fa-121">Data Sources in Multidimensional Models</span></span>](../data-sources-in-multidimensional-models.md)|<span data-ttu-id="391fa-122">介绍 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的数据源。</span><span class="sxs-lookup"><span data-stu-id="391fa-122">Describes a data source in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="391fa-123">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="391fa-123">Data Source Views in Multidimensional Models</span></span>](../data-source-views-in-multidimensional-models.md)|<span data-ttu-id="391fa-124">介绍 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中基于一个或多个数据源的逻辑数据模型。</span><span class="sxs-lookup"><span data-stu-id="391fa-124">Describes a logical data model based on one or more data sources, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="391fa-125">多维模型中的多维数据集</span><span class="sxs-lookup"><span data-stu-id="391fa-125">Cubes in Multidimensional Models</span></span>](../cubes-in-multidimensional-models.md)|<span data-ttu-id="391fa-126">介绍多维数据集和多维数据集对象，包括度量值、度量值组、维度用法关系、计算、关键绩效指标 (KPI)、操作、翻译、分区和透视。</span><span class="sxs-lookup"><span data-stu-id="391fa-126">Describes cubes and cube objects, including measures, measure groups, dimension usage relationships, calculations, key performance indicators, actions, translations, partitions, and perspectives.</span></span>|  
|[<span data-ttu-id="391fa-127">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="391fa-127">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="391fa-128">介绍维度和维度对象，包括属性、属性关系、层次结构、级别和成员。</span><span class="sxs-lookup"><span data-stu-id="391fa-128">Describes dimensions and dimension objects, including attributes, attribute relationships, hierarchies, levels, and members.</span></span>|  
|[<span data-ttu-id="391fa-129">挖掘结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="391fa-129">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../data-mining/mining-structures-analysis-services-data-mining.md)|<span data-ttu-id="391fa-130">介绍挖掘结构和挖掘对象，包括挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="391fa-130">Describes mining structures and mining objects, including mining models.</span></span>|  
|[<span data-ttu-id="391fa-131">安全角色（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="391fa-131">Security Roles  &#40;Analysis Services - Multidimensional Data&#41;</span></span>](security-roles-analysis-services-multidimensional-data.md)|<span data-ttu-id="391fa-132">介绍一个角色，它是在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中用于对对象的访问进行控制的安全机制。</span><span class="sxs-lookup"><span data-stu-id="391fa-132">Describes a role, the security mechanism used to control access to objects in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="391fa-133">多维模型程序集管理</span><span class="sxs-lookup"><span data-stu-id="391fa-133">Multidimensional Model Assemblies Management</span></span>](../multidimensional-model-assemblies-management.md)|<span data-ttu-id="391fa-134">介绍一个程序集，它是在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中用于扩展 MDX 和 DMX 语言的用户定义函数的集合。</span><span class="sxs-lookup"><span data-stu-id="391fa-134">Describes an assembly, a collection of user-defined functions used to extend the MDX and DMX languages, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="391fa-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="391fa-135">See Also</span></span>  
 <span data-ttu-id="391fa-136">[支持 &#40;SSAS 多维&#41;的数据源](../supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="391fa-136">[Data Sources Supported &#40;SSAS Multidimensional&#41;](../supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="391fa-137">[&#40;SSAS&#41;的多维模型解决方案](../multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="391fa-137">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="391fa-138">数据挖掘解决方案</span><span class="sxs-lookup"><span data-stu-id="391fa-138">Data Mining Solutions</span></span>](../../data-mining/data-mining-solutions.md)  
  
  
