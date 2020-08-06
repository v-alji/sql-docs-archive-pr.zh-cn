---
title: 多维数据集属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27d4202774107795eaddf76c27e21010d534d977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578504"
---
# <a name="cube-properties"></a><span data-ttu-id="b94c0-102">多维数据集属性</span><span class="sxs-lookup"><span data-stu-id="b94c0-102">Cube Properties</span></span>
  <span data-ttu-id="b94c0-103">可以在多维数据集中设置很多属性以影响整个多维数据集的行为。</span><span class="sxs-lookup"><span data-stu-id="b94c0-103">Cubes have a number of properties that you can set to affect cube-wide behavior.</span></span> <span data-ttu-id="b94c0-104">下表总结了这些属性。</span><span class="sxs-lookup"><span data-stu-id="b94c0-104">These properties are summarized in the following table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b94c0-105">某些属性是在创建多维数据集时自动设置的，不能更改。</span><span class="sxs-lookup"><span data-stu-id="b94c0-105">Some properties are set automatically when the cube is created and cannot be changed.</span></span>  
  
 <span data-ttu-id="b94c0-106">有关如何设置多维数据集属性的详细信息，请参阅[多维数据集设计器 &#40;Analysis Services 多维数据&#41;](../cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b94c0-106">For more information about how to set cube properties, see [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
|<span data-ttu-id="b94c0-107">属性</span><span class="sxs-lookup"><span data-stu-id="b94c0-107">Property</span></span>|<span data-ttu-id="b94c0-108">说明</span><span class="sxs-lookup"><span data-stu-id="b94c0-108">Description</span></span>|  
|--------------|-----------------|  
|`AggregationPrefix`|<span data-ttu-id="b94c0-109">指定用于聚合名称的通用前缀。</span><span class="sxs-lookup"><span data-stu-id="b94c0-109">Specifies the common prefix that is used for aggregation names.</span></span>|  
|`Collation`|<span data-ttu-id="b94c0-110">指定以下划线分隔的区域设置标识符 (LCID) 和比较标志，例如 Latin1_General_C1_AS。</span><span class="sxs-lookup"><span data-stu-id="b94c0-110">Specifies the locale identifier (LCID) and the comparison flag, separated by an underscore: for example, Latin1_General_C1_AS.</span></span>|  
|`DefaultMeasure`|<span data-ttu-id="b94c0-111">包含定义多维数据集的默认度量值的多维表达式 (MDX)。</span><span class="sxs-lookup"><span data-stu-id="b94c0-111">Contains a Multidimensional Expressions (MDX) expression that defines the default measure for the cube.</span></span>|  
|`Description`|<span data-ttu-id="b94c0-112">提供多维数据集的说明，可以在客户端应用程序中显示。</span><span class="sxs-lookup"><span data-stu-id="b94c0-112">Provides a description of the cube, which may be exposed in client applications.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="b94c0-113">包含可配置的错误处理设置，用于处理重复键、未知键、错误限制以及检测到错误时执行的操作、错误日志文件和空键处理。</span><span class="sxs-lookup"><span data-stu-id="b94c0-113">Contains configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`EstimatedRows`|<span data-ttu-id="b94c0-114">指定多维数据集中的估计行数。</span><span class="sxs-lookup"><span data-stu-id="b94c0-114">Specifies the number of estimated rows in the cube.</span></span>|  
|`ID`|<span data-ttu-id="b94c0-115">包含多维数据集的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="b94c0-115">Contains the unique identifier (ID) of the cube.</span></span>|  
|`Language`|<span data-ttu-id="b94c0-116">指定多维数据集的默认语言标识符。</span><span class="sxs-lookup"><span data-stu-id="b94c0-116">Specifies the default language identifier of the cube.</span></span>|  
|`Name`|<span data-ttu-id="b94c0-117">指定多维数据集的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="b94c0-117">Specifies the user-friendly name of the cube.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="b94c0-118">定义多维数据集的主动缓存设置。</span><span class="sxs-lookup"><span data-stu-id="b94c0-118">Defines proactive cache settings for the cube.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="b94c0-119">指示在处理期间或之后是否进行索引和聚合。</span><span class="sxs-lookup"><span data-stu-id="b94c0-119">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="b94c0-120">选项为**常规**或 `lazy` 。</span><span class="sxs-lookup"><span data-stu-id="b94c0-120">Options are **regular** or `lazy`.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="b94c0-121">确定在后台操作（例如，惰性聚合和索引）期间多维数据集的处理优先级。</span><span class="sxs-lookup"><span data-stu-id="b94c0-121">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="b94c0-122">默认值为**0**。</span><span class="sxs-lookup"><span data-stu-id="b94c0-122">The default value is **0**.</span></span>|  
|`ScriptCacheProcessingMode`|<span data-ttu-id="b94c0-123">指示在处理期间或之后是否生成脚本缓存。</span><span class="sxs-lookup"><span data-stu-id="b94c0-123">Indicates whether the script cache should be built during or after processing.</span></span> <span data-ttu-id="b94c0-124">选项为 "**常规**" 和 `lazy` 。</span><span class="sxs-lookup"><span data-stu-id="b94c0-124">Options are **regular** and `lazy`.</span></span>|  
|`ScriptErrorHandlingMode`|<span data-ttu-id="b94c0-125">确定错误处理。</span><span class="sxs-lookup"><span data-stu-id="b94c0-125">Determines error handling.</span></span> <span data-ttu-id="b94c0-126">选项是 `IgnoreNone` 或 `IgnoreAll`</span><span class="sxs-lookup"><span data-stu-id="b94c0-126">Options are `IgnoreNone` or `IgnoreAll`</span></span>|  
|`Source`|<span data-ttu-id="b94c0-127">显示用于多维数据集的数据源视图</span><span class="sxs-lookup"><span data-stu-id="b94c0-127">Displays the data source view used for the cube.</span></span>|  
|`StorageLocation`|<span data-ttu-id="b94c0-128">指定多维数据集的文件系统存储位置。</span><span class="sxs-lookup"><span data-stu-id="b94c0-128">Specifies the file system storage location for the cube.</span></span> <span data-ttu-id="b94c0-129">如果未指定任何位置，则从包含多维数据集对象的数据库中继承位置。</span><span class="sxs-lookup"><span data-stu-id="b94c0-129">If none is specified, the location is inherited from the database that contains the cube object.</span></span>|  
|`StorageMode`|<span data-ttu-id="b94c0-130">指定多维数据集的存储模式。</span><span class="sxs-lookup"><span data-stu-id="b94c0-130">Specifies the storage mode for the cube.</span></span> <span data-ttu-id="b94c0-131">值为 `MOLAP` 、 `ROLAP` 或`HOLAP``.`</span><span class="sxs-lookup"><span data-stu-id="b94c0-131">Values are `MOLAP`, `ROLAP`, or `HOLAP``.`</span></span>|  
|`Visible`|<span data-ttu-id="b94c0-132">确定多维数据集的可见性。</span><span class="sxs-lookup"><span data-stu-id="b94c0-132">Determines the visibility of the cube.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b94c0-133">有关在处理 null 值和其他数据完整性问题时设置 ErrorConfiguration 属性的值的详细信息，请参阅[处理 Analysis Services 2005 中的数据完整性问题](https://go.microsoft.com/fwlink/?LinkId=81891)。</span><span class="sxs-lookup"><span data-stu-id="b94c0-133">For more information about setting values for the ErrorConfiguration property when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94c0-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b94c0-134">See Also</span></span>  
 [<span data-ttu-id="b94c0-135">主动缓存 &#40;分区&#41;</span><span class="sxs-lookup"><span data-stu-id="b94c0-135">Proactive Caching &#40;Partitions&#41;</span></span>](partitions-proactive-caching.md)  
  
  
