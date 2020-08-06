---
title: 配置度量值组属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03dad3d8ee33ea8a78b08f9a354d0db3d177198c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691983"
---
# <a name="configure-measure-group-properties"></a><span data-ttu-id="3d315-102">配置度量值组属性</span><span class="sxs-lookup"><span data-stu-id="3d315-102">Configure Measure Group Properties</span></span>
  <span data-ttu-id="3d315-103">通过使用度量值组属性，您可以定义度量值组的工作方式。</span><span class="sxs-lookup"><span data-stu-id="3d315-103">Measures groups have properties that enable you to define how measure groups function.</span></span>  
  
## <a name="measure-group-properties"></a><span data-ttu-id="3d315-104">度量值组属性</span><span class="sxs-lookup"><span data-stu-id="3d315-104">Measure Group Properties</span></span>  
 <span data-ttu-id="3d315-105">度量值组属性确定整个度量值组的行为，并设置度量值组内度量值的某些属性的默认行为。</span><span class="sxs-lookup"><span data-stu-id="3d315-105">Measure group properties determine behaviors for the entire measure group and set the default behaviors for certain properties of measures within a measure group.</span></span>  
  
|<span data-ttu-id="3d315-106">属性</span><span class="sxs-lookup"><span data-stu-id="3d315-106">Property</span></span>|<span data-ttu-id="3d315-107">定义</span><span class="sxs-lookup"><span data-stu-id="3d315-107">Definition</span></span>|  
|--------------|----------------|  
|`AggregationPrefix`|<span data-ttu-id="3d315-108">适用于 ROLAP 存储。</span><span class="sxs-lookup"><span data-stu-id="3d315-108">Applies to ROLAP storage.</span></span> <span data-ttu-id="3d315-109">将公共前缀分配给 SQL Server 中的索引视图，用于为与此度量值组关联的分区存储聚合。</span><span class="sxs-lookup"><span data-stu-id="3d315-109">Assigns a common prefix to the indexed views in SQL Server, used to store aggregations for the partitions associated with this measure group.</span></span>|  
|`DataAggregation`|<span data-ttu-id="3d315-110">此属性是保留供将来使用，当前不起任何作用。</span><span class="sxs-lookup"><span data-stu-id="3d315-110">This property is reserved for future use and currently has no effect.</span></span> <span data-ttu-id="3d315-111">因此，建议你不要修改此设置。</span><span class="sxs-lookup"><span data-stu-id="3d315-111">Therefore, it is recommended that you do not modify this setting.</span></span>|  
|`Description`|<span data-ttu-id="3d315-112">你可以使用此属性来记录度量值组。</span><span class="sxs-lookup"><span data-stu-id="3d315-112">You can use this property to document the measure group.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="3d315-113">可配置的错误处理设置，用于处理重复键、未知键、空键、错误限制、检测到错误时的操作以及错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="3d315-113">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span> <span data-ttu-id="3d315-114">请参阅[多维数据集、分区和维度处理的错误配置（SSAS - 多维）](error-configuration-for-cube-partition-and-dimension-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="3d315-114">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
|`EstimatedRows`|<span data-ttu-id="3d315-115">指定事实数据表中的估计行数。</span><span class="sxs-lookup"><span data-stu-id="3d315-115">Specifies the estimated number of rows in the fact table.</span></span>|  
|`EstimatedSize`|<span data-ttu-id="3d315-116">指定度量值组的估计大小(字节)。</span><span class="sxs-lookup"><span data-stu-id="3d315-116">Specifies the estimated size (in bytes) of the measure group.</span></span>|  
|`ID`|<span data-ttu-id="3d315-117">指定对象的标识符。</span><span class="sxs-lookup"><span data-stu-id="3d315-117">Specifies the identifier of the object.</span></span>|  
|`IgnoreUnrelatedDimensions`|<span data-ttu-id="3d315-118">确定当查询中包括与度量值组无关的维度的成员时，是否将无关维度强制为顶级。</span><span class="sxs-lookup"><span data-stu-id="3d315-118">Determines whether unrelated dimensions are forced to their top level when members of dimensions that are unrelated to the measure group are included in a query.</span></span> <span data-ttu-id="3d315-119">默认设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="3d315-119">Default setting is `True`.</span></span>|  
|`Name`|<span data-ttu-id="3d315-120">度量值的名称。</span><span class="sxs-lookup"><span data-stu-id="3d315-120">Name of the measure.</span></span> <span data-ttu-id="3d315-121">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="3d315-121">This property is read-only.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="3d315-122">可配置的错误处理设置，用于处理重复键、未知键、空键、错误限制、检测到错误时的操作以及错误日志文件。</span><span class="sxs-lookup"><span data-stu-id="3d315-122">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="3d315-123">指示在处理期间或之后是否进行索引和聚合。</span><span class="sxs-lookup"><span data-stu-id="3d315-123">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="3d315-124">选项是 Regular 和 LazyAggregations。</span><span class="sxs-lookup"><span data-stu-id="3d315-124">Options are Regular and LazyAggregations.</span></span> <span data-ttu-id="3d315-125">LazyAggregations 可作为后台任务运行聚合。</span><span class="sxs-lookup"><span data-stu-id="3d315-125">LazyAggregations can be used to run aggregation as a background task.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="3d315-126">确定在后台操作（例如，惰性聚合和索引）期间多维数据集的处理优先级。</span><span class="sxs-lookup"><span data-stu-id="3d315-126">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="3d315-127">默认值为**0**。</span><span class="sxs-lookup"><span data-stu-id="3d315-127">The default value is **0**.</span></span>|  
|`StorageLocation`|<span data-ttu-id="3d315-128">度量值组的文件系统存储位置。</span><span class="sxs-lookup"><span data-stu-id="3d315-128">The file system storage location for the measure group.</span></span> <span data-ttu-id="3d315-129">如果未指定，则从包含度量值组的多维数据集中继承该位置。</span><span class="sxs-lookup"><span data-stu-id="3d315-129">If none is specified, the location is inherited from the cube that contains the measure group.</span></span>|  
|`StorageMode`|<span data-ttu-id="3d315-130">度量值组的存储模式。</span><span class="sxs-lookup"><span data-stu-id="3d315-130">The storage mode for the measure group.</span></span> <span data-ttu-id="3d315-131">可用值是 MOLAP、ROLAP 或 HOLAP。</span><span class="sxs-lookup"><span data-stu-id="3d315-131">Available values are MOLAP, ROLAP, or HOLAP.</span></span>|  
|`Type`|<span data-ttu-id="3d315-132">指定度量值组的类型。</span><span class="sxs-lookup"><span data-stu-id="3d315-132">Specifies the type of the measure group.</span></span>|  
  
  
