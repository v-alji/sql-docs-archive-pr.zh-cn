---
title: 多维模型中的数据源视图 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services]
- data source views [Analysis Services], about data source views
- SQL Server Analysis Services, data source views
- data source views [Analysis Services], multiple
- Analysis Services, data source views
- multiple data source views
- SSAS, data source views
ms.assetid: 4c12376f-4fc2-492b-9a00-93eec34571ed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1aef6b6d716ec71ac082ca8b7c042492c1712b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693543"
---
# <a name="data-source-views-in-multidimensional-models"></a><span data-ttu-id="50b51-102">多维模型中的数据源视图</span><span class="sxs-lookup"><span data-stu-id="50b51-102">Data Source Views in Multidimensional Models</span></span>
  <span data-ttu-id="50b51-103">数据源视图 (DSV) 是关系数据源的抽象，它成为在多维项目中创建的多维数据集和维度的基础。</span><span class="sxs-lookup"><span data-stu-id="50b51-103">A data source view (DSV) is an abstraction of a relational data source that becomes the basis of the cubes and dimensions you create in a multidimensional project.</span></span> <span data-ttu-id="50b51-104">DSV 旨在让您控制项目中使用的数据结构，并且独立于基础数据源工作（例如，重命名或连接列，而不必直接修改原始数据源）。</span><span class="sxs-lookup"><span data-stu-id="50b51-104">The purpose of a DSV is to give you control over the data structures used in your project, and to work independently of the underlying data sources (for example, the ability to rename or concatenate columns without directly modifying the original data source).</span></span>  
  
 <span data-ttu-id="50b51-105">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中，可以根据一个或多个数据源生成多个数据源视图，并构造每一个数据源视图以满足不同解决方案的要求。</span><span class="sxs-lookup"><span data-stu-id="50b51-105">You can build multiple data source views in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database on one or more data sources, and construct each one to satisfy the requirements for a different solution.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="50b51-106">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="50b51-106">Related Tasks</span></span>  
 [<span data-ttu-id="50b51-107">定义数据源视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-107">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](defining-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-108">在数据源视图中添加或删除表或视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-108">Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;</span></span>](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-109">在数据源视图中更改属性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-109">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-110">在数据源视图中定义逻辑关系 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-110">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-relationships-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-111">在数据源视图中定义逻辑主键 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-111">Define Logical Primary Keys in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-primary-keys-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-112">在数据源视图中定义命名计算 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-112">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-113">在数据源视图中定义命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-113">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-114">在数据源视图中替换表或命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-114">Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;</span></span>](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-115">使用数据源视图设计器中的关系图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-115">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
 [<span data-ttu-id="50b51-116">在数据源视图中浏览数据 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-116">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](explore-data-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-117">删除数据源视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-117">Delete a Data Source View &#40;Analysis Services&#41;</span></span>](delete-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="50b51-118">刷新数据源视图中的架构 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="50b51-118">Refresh the Schema in a Data Source View &#40;Analysis Services&#41;</span></span>](refresh-the-schema-in-a-data-source-view-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="50b51-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50b51-119">See Also</span></span>  
 <span data-ttu-id="50b51-120">[架构生成向导 &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="50b51-120">[Schema Generation Wizard &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span></span>  
 [<span data-ttu-id="50b51-121">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="50b51-121">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
