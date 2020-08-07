---
title: 多维数据集 (Analysis Services 多维数据) 的多维数据集对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], objects
ms.assetid: 5cee362e-3f95-4467-bc6c-29b1518ecbf3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0e6dfb75be696ab26893e668b99dc36c7340f86c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587640"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="f4fa7-102">多维数据集对象（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f4fa7-102">Cube Objects (Analysis Services - Multidimensional Data)</span></span>
    
## <a name="introducing-cube-objects"></a><span data-ttu-id="f4fa7-103">多维数据集对象介绍</span><span class="sxs-lookup"><span data-stu-id="f4fa7-103">Introducing Cube Objects</span></span>  
 <span data-ttu-id="f4fa7-104">简单 <xref:Microsoft.AnalysisServices.Cube> 对象由基本信息、维度和度量值组组成。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-104">A simple <xref:Microsoft.AnalysisServices.Cube> object is composed of: basic information, dimensions, and measure groups.</span></span> <span data-ttu-id="f4fa7-105">基本信息包括多维数据集的名称、多维数据集的默认度量值、数据源和存储模式等。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-105">Basic information includes the name of the cube, the default measure of the cube, the data source, the storage mode, and others.</span></span>  
  
 <span data-ttu-id="f4fa7-106">维度集合包含在数据库维度集合的多维数据集中使用的实际维度集。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-106">The Dimensions collection contains the actual set of dimensions used in the cube from the database dimensions colection.</span></span> <span data-ttu-id="f4fa7-107">所有维度都必须先在数据库的维度集合中定义，然后才能在多维数据集中引用。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-107">All dimensions have to be defined in the dimensions collection of the database before being referenced in the cube.</span></span> <span data-ttu-id="f4fa7-108">专用维度在中不可用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-108">Private dimensions are not available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f4fa7-109">度量值组是多维数据集中的度量值集。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-109">Measure groups are sets of measures in the cube.</span></span> <span data-ttu-id="f4fa7-110">度量值组是具有常见数据源视图和维度集的度量值的集合。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-110">A measure group is a collection of measures that have a common data source view and a common set of dimensions.</span></span> <span data-ttu-id="f4fa7-111">度量值组是度量值的处理单元；可先对度量值组进行单独处理，然后再浏览。</span><span class="sxs-lookup"><span data-stu-id="f4fa7-111">A measure group is the unit of process for measures; measure groups can be processed individually and then browsed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4fa7-112">在本节中</span><span class="sxs-lookup"><span data-stu-id="f4fa7-112">In this section</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4fa7-113">主题</span><span class="sxs-lookup"><span data-stu-id="f4fa7-113">Topic</span></span>||  
|[<span data-ttu-id="f4fa7-114">操作（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f4fa7-114">Actions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="f4fa7-115">聚合和聚合设计</span><span class="sxs-lookup"><span data-stu-id="f4fa7-115">Aggregations and Aggregation Designs</span></span>](aggregations-and-aggregation-designs.md)||  
|[<span data-ttu-id="f4fa7-116">计算</span><span class="sxs-lookup"><span data-stu-id="f4fa7-116">Calculations</span></span>](calculations.md)||  
|[<span data-ttu-id="f4fa7-117">多维数据集单元 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f4fa7-117">Cube Cells &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-cells-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="f4fa7-118">多维数据集属性</span><span class="sxs-lookup"><span data-stu-id="f4fa7-118">Cube Properties</span></span>](cube-properties-multidimensional-model-programming.md)||  
|[<span data-ttu-id="f4fa7-119">多维数据集存储 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f4fa7-119">Cube Storage &#40;Analysis Services - Multidimensional Data&#41;</span></span>](cube-storage-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="f4fa7-120">多维数据集翻译</span><span class="sxs-lookup"><span data-stu-id="f4fa7-120">Cube Translations</span></span>](cube-translations.md)||  
|[<span data-ttu-id="f4fa7-121">维度关系</span><span class="sxs-lookup"><span data-stu-id="f4fa7-121">Dimension Relationships</span></span>](dimension-relationships.md)||  
|[<span data-ttu-id="f4fa7-122">多维模型中的关键绩效指标 (KPI)</span><span class="sxs-lookup"><span data-stu-id="f4fa7-122">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](../multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[<span data-ttu-id="f4fa7-123">度量值和度量值组</span><span class="sxs-lookup"><span data-stu-id="f4fa7-123">Measures and Measure Groups</span></span>](../multidimensional-models/measures-and-measure-groups.md)||  
|[<span data-ttu-id="f4fa7-124">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f4fa7-124">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partitions-analysis-services-multidimensional-data.md)||  
|[<span data-ttu-id="f4fa7-125">透视</span><span class="sxs-lookup"><span data-stu-id="f4fa7-125">Perspectives</span></span>](perspectives.md)||  
  
  
