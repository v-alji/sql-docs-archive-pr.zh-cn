---
title: 数据库维度属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588729"
---
# <a name="database-dimension-properties"></a><span data-ttu-id="3b6da-102">数据库维度属性</span><span class="sxs-lookup"><span data-stu-id="3b6da-102">Database Dimension Properties</span></span>
  <span data-ttu-id="3b6da-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度的特征是由维度的元数据根据各种维度属性的设置以及维度所包含的属性或层次结构来定义的。</span><span class="sxs-lookup"><span data-stu-id="3b6da-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the characteristics of a dimension are defined by the metadata for the dimension, based on the settings of various dimension properties, and on the attributes or hierarchies that are contained by the dimension.</span></span> <span data-ttu-id="3b6da-104">下表说明了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的维度属性。</span><span class="sxs-lookup"><span data-stu-id="3b6da-104">The following table describes the dimension properties in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="3b6da-105">属性</span><span class="sxs-lookup"><span data-stu-id="3b6da-105">Property</span></span>|<span data-ttu-id="3b6da-106">说明</span><span class="sxs-lookup"><span data-stu-id="3b6da-106">Description</span></span>|  
|--------------|-----------------|  
|`AttributeAllMemberName`|<span data-ttu-id="3b6da-107">指定维度中属性的“全部”成员的名称。</span><span class="sxs-lookup"><span data-stu-id="3b6da-107">Specifies the name of the All member for attributes in a dimension.</span></span>|  
|`Collation`|<span data-ttu-id="3b6da-108">确定维度使用的排序规则。</span><span class="sxs-lookup"><span data-stu-id="3b6da-108">Determines the collation used by the dimension.</span></span>|  
|`CurrentStorageMode`|<span data-ttu-id="3b6da-109">包含维度的当前存储模式。</span><span class="sxs-lookup"><span data-stu-id="3b6da-109">Contains the current storage mode for the dimension.</span></span>|  
|`DependsOnDimension`|<span data-ttu-id="3b6da-110">包含维度所依赖的其他维度的 ID（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="3b6da-110">Contains the ID of another dimension on which the dimension depends, if any.</span></span>|  
|`Description`|<span data-ttu-id="3b6da-111">包含维度的说明。</span><span class="sxs-lookup"><span data-stu-id="3b6da-111">Contains the description of the dimension.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="3b6da-112">可配置的错误处理设置，用于处理重复键、未知键、错误限制以及检测到错误执行的操作、错误日志文件和空键处理。</span><span class="sxs-lookup"><span data-stu-id="3b6da-112">Configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`ID`|<span data-ttu-id="3b6da-113">包含维度的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="3b6da-113">Contains the unique identifier (ID) of the dimension.</span></span>|  
|`Language`|<span data-ttu-id="3b6da-114">指定维度的默认语言。</span><span class="sxs-lookup"><span data-stu-id="3b6da-114">Specifies the default language for the dimension.</span></span>|  
|`MdxMissingMemberMode`|<span data-ttu-id="3b6da-115">确定如何处理多维表达式 (MDX) 语句中缺少的成员。</span><span class="sxs-lookup"><span data-stu-id="3b6da-115">Determines how missing members are handled for Multidimensional Expressions (MDX) statements.</span></span>|  
|`MiningModelID`|<span data-ttu-id="3b6da-116">包含数据挖掘维度所关联的挖掘模型的 ID。</span><span class="sxs-lookup"><span data-stu-id="3b6da-116">Contains the ID of the mining model with which the data mining dimension is associated.</span></span> <span data-ttu-id="3b6da-117">此属性仅适用于挖掘模型维度。</span><span class="sxs-lookup"><span data-stu-id="3b6da-117">This property is applicable only if the dimension is a mining model dimension.</span></span>|  
|`Name`|<span data-ttu-id="3b6da-118">指定维度的名称。</span><span class="sxs-lookup"><span data-stu-id="3b6da-118">Specifies the name of the dimension.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="3b6da-119">定义维度的主动缓存设置。</span><span class="sxs-lookup"><span data-stu-id="3b6da-119">Defines the proactive cache settings for the dimension.</span></span>|  
|`ProcessingGroup`|<span data-ttu-id="3b6da-120">指定处理组。</span><span class="sxs-lookup"><span data-stu-id="3b6da-120">Specifies the processing group.</span></span> <span data-ttu-id="3b6da-121">值为 ByAttribute 或 ByTable。</span><span class="sxs-lookup"><span data-stu-id="3b6da-121">Values are ByAttribute or ByTable.</span></span> <span data-ttu-id="3b6da-122">默认值为 `ByAttribute`。</span><span class="sxs-lookup"><span data-stu-id="3b6da-122">Default is `ByAttribute`.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="3b6da-123">指示是否应该在处理期间或处理之后对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 进行聚合以及为其建立索引。</span><span class="sxs-lookup"><span data-stu-id="3b6da-123">Indicates whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should index and aggregate during or after processing.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="3b6da-124">确定在后台操作期间（例如惰性聚合、索引或群集）维度的处理优先级。</span><span class="sxs-lookup"><span data-stu-id="3b6da-124">Determines the processing priority of the dimension during background operations such as lazy aggregation, indexing, or clustering.</span></span>|  
|`Source`|<span data-ttu-id="3b6da-125">标识维度绑定到的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="3b6da-125">Identifies the data source view to which the dimension is bound.</span></span>|  
|`StorageMode`|<span data-ttu-id="3b6da-126">确定维度的存储模式。</span><span class="sxs-lookup"><span data-stu-id="3b6da-126">Determines the storage mode for the dimension.</span></span>|  
|`Type`|<span data-ttu-id="3b6da-127">指定维度的类型。</span><span class="sxs-lookup"><span data-stu-id="3b6da-127">Specifies the type of the dimension.</span></span>|  
|`UnknownMember`|<span data-ttu-id="3b6da-128">指示未知成员是否可见。</span><span class="sxs-lookup"><span data-stu-id="3b6da-128">Indicates whether the unknown member is visible.</span></span>|  
|`UnknownMemberName`|<span data-ttu-id="3b6da-129">指定维度未知成员的标题，以维度的默认语言显示。</span><span class="sxs-lookup"><span data-stu-id="3b6da-129">Specifies the caption, in the default language of the dimension, for the unknown member of the dimension.</span></span>|  
|`WriteEnabled`|<span data-ttu-id="3b6da-130">指示维度写回是否可用（视安全权限而定）。</span><span class="sxs-lookup"><span data-stu-id="3b6da-130">Indicates whether dimension writebacks are available (subject to security permissions).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3b6da-131">有关在处理 null 值和其他数据完整性问题时设置 ErrorConfiguration 和 UnknownMember 属性的值的详细信息，请参阅[处理 Analysis Services 2005 中的数据完整性问题](https://go.microsoft.com/fwlink/?LinkId=81891)。</span><span class="sxs-lookup"><span data-stu-id="3b6da-131">For more information about setting values for the ErrorConfiguration and UnknownMember properties when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6da-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b6da-132">See Also</span></span>  
 <span data-ttu-id="3b6da-133">[属性和属性层次结构](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="3b6da-133">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="3b6da-134">[用户层次结构](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="3b6da-134">[User Hierarchies](user-hierarchies.md) </span></span>  
 <span data-ttu-id="3b6da-135">[维度关系](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="3b6da-135">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 [<span data-ttu-id="3b6da-136">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="3b6da-136">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
