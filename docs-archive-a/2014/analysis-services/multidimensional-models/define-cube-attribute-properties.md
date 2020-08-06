---
title: 定义多维数据集特性属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
author: minewiskan
ms.author: owend
ms.openlocfilehash: c02d57e8d24e625dc0613f25d97765c9ae018803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577889"
---
# <a name="define-cube-attribute-properties"></a><span data-ttu-id="a655b-102">定义多维数据集特性属性</span><span class="sxs-lookup"><span data-stu-id="a655b-102">Define Cube Attribute Properties</span></span>
  <span data-ttu-id="a655b-103">通过使用多维数据集特性属性，您可以为基于同一数据库维度的多维数据集维度中的维度特性指定唯一的设置。</span><span class="sxs-lookup"><span data-stu-id="a655b-103">Cube attribute properties enable you to specify unique settings for dimension attributes in cube dimensions based on the same database dimension.</span></span> <span data-ttu-id="a655b-104">下表介绍了多维数据集特性的属性。</span><span class="sxs-lookup"><span data-stu-id="a655b-104">The following table describes the properties of a cube attribute.</span></span>  
  
|<span data-ttu-id="a655b-105">属性</span><span class="sxs-lookup"><span data-stu-id="a655b-105">Property</span></span>|<span data-ttu-id="a655b-106">说明</span><span class="sxs-lookup"><span data-stu-id="a655b-106">Description</span></span>|  
|--------------|-----------------|  
|`AggregationUsage`|<span data-ttu-id="a655b-107">指定聚合设计向导将如何设计此属性的聚合。</span><span class="sxs-lookup"><span data-stu-id="a655b-107">Specifies how the Aggregation Design Wizard will design aggregations for the attribute.</span></span> <span data-ttu-id="a655b-108">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="a655b-108">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="a655b-109">`Default`：默认值。</span><span class="sxs-lookup"><span data-stu-id="a655b-109">`Default`: Default.</span></span> <span data-ttu-id="a655b-110">聚合设计向导根据属性类型应用默认规则（对于键为 Full，对于其他为 Unrestricted）。</span><span class="sxs-lookup"><span data-stu-id="a655b-110">The Aggregation Design Wizard applies a default rule based on the type of attribute (Full for keys, Unrestricted for others).</span></span><br /><br /> <span data-ttu-id="a655b-111">`None`：多维数据集的所有聚合都不应包括此属性。</span><span class="sxs-lookup"><span data-stu-id="a655b-111">`None`: No aggregation for the cube should include this attribute.</span></span><br /><br /> <span data-ttu-id="a655b-112">`Unrestricted`：聚合设计向导上没有任何限制。</span><span class="sxs-lookup"><span data-stu-id="a655b-112">`Unrestricted`: No restrictions are placed on the Aggregation Design Wizard.</span></span><br /><br /> <span data-ttu-id="a655b-113">`Full`：多维数据集的每个聚合都必须包含此属性。</span><span class="sxs-lookup"><span data-stu-id="a655b-113">`Full`: Every aggregation for the cube must include this attribute.</span></span>|  
|`AttributeHierarchyEnabled`|<span data-ttu-id="a655b-114">标识是否对此多维数据集维度启用属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a655b-114">Identifies whether the attribute hierarchy is enables on this cube dimension.</span></span> <span data-ttu-id="a655b-115">这可以对特定多维数据集或维度角色禁用属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a655b-115">This allows attribute hierarchies to be disabled on specific cubes or dimension roles.</span></span> <span data-ttu-id="a655b-116">如果禁用了基础属性层次结构，则此设置不起作用。</span><span class="sxs-lookup"><span data-stu-id="a655b-116">This setting has no effect if the underlying attribute hierarchy is disabled.</span></span> <span data-ttu-id="a655b-117">默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="a655b-117">Default value is `True`.</span></span>|  
|`OptimizedState`|<span data-ttu-id="a655b-118">指示是否对此多维数据集维度优化属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a655b-118">Indicates whether the attribute hierarchy is optimized on this cube dimension.</span></span> <span data-ttu-id="a655b-119">这可以对特定多维数据集或维度角色优化属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="a655b-119">This allows attribute hierarchies to be optimized on specific cubes or dimension roles.</span></span> <span data-ttu-id="a655b-120">如果未优化基础属性层次结构，则此设置不起作用。</span><span class="sxs-lookup"><span data-stu-id="a655b-120">This setting has no effect if the underlying attribute hierarchy is not optimized.</span></span> <span data-ttu-id="a655b-121">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="a655b-121">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="a655b-122">`FullyOptimized`：默认值。</span><span class="sxs-lookup"><span data-stu-id="a655b-122">`FullyOptimized`: Default.</span></span> <span data-ttu-id="a655b-123">实例为层次结构生成索引以提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a655b-123">The instance builds indexes for the hierarchy to improve query performance.</span></span> <span data-ttu-id="a655b-124">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="a655b-124">This is the default value.</span></span><br /><br /> <span data-ttu-id="a655b-125">`NotOptimized`：实例不生成其他索引。</span><span class="sxs-lookup"><span data-stu-id="a655b-125">`NotOptimized`: The instance does not build additional indexes.</span></span>|  
|`AttributeHierarchyVisible`|<span data-ttu-id="a655b-126">指示属性层次结构在此多维数据集维度上是否可见。</span><span class="sxs-lookup"><span data-stu-id="a655b-126">Indicates whether the attribute hierarchy is visible on this cube dimension.</span></span> <span data-ttu-id="a655b-127">这可以使属性层次结构在特定多维数据集或维度角色上可见。</span><span class="sxs-lookup"><span data-stu-id="a655b-127">This allows attribute hierarchies to be visible on specific cubes or dimension roles.</span></span> <span data-ttu-id="a655b-128">如果基础属性层次结构不可见，则此设置不起作用。</span><span class="sxs-lookup"><span data-stu-id="a655b-128">This setting has no effect if the underlying attribute hierarchy is not visible.</span></span> <span data-ttu-id="a655b-129">默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="a655b-129">The default value is `True`.</span></span>|  
|`AttributeID`|<span data-ttu-id="a655b-130">包含属性的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="a655b-130">Contains the unique identifier (ID) of the attribute.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a655b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a655b-131">See Also</span></span>  
 <span data-ttu-id="a655b-132">[定义多维数据集维度属性](define-cube-dimension-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a655b-132">[Define Cube Dimension Properties](define-cube-dimension-properties.md) </span></span>  
 [<span data-ttu-id="a655b-133">定义多维数据集层次结构属性</span><span class="sxs-lookup"><span data-stu-id="a655b-133">Define Cube Hierarchy Properties</span></span>](define-cube-hierarchy-properties.md)  
  
  
