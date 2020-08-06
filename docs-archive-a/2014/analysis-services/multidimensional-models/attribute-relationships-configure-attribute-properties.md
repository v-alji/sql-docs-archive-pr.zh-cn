---
title: 配置属性关系属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577906"
---
# <a name="configure-attribute-relationship-properties"></a><span data-ttu-id="4a537-102">配置特性关系属性</span><span class="sxs-lookup"><span data-stu-id="4a537-102">Configure Attribute Relationship Properties</span></span>
  <span data-ttu-id="4a537-103">下表列出了特性关系的属性并对这些属性进行了说明。</span><span class="sxs-lookup"><span data-stu-id="4a537-103">The following table lists and describes the properties of an attribute relationship.</span></span>  
  
|<span data-ttu-id="4a537-104">属性</span><span class="sxs-lookup"><span data-stu-id="4a537-104">Property</span></span>|<span data-ttu-id="4a537-105">说明</span><span class="sxs-lookup"><span data-stu-id="4a537-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4a537-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="4a537-106">Attribute</span></span>|<span data-ttu-id="4a537-107">包含特性的名称。</span><span class="sxs-lookup"><span data-stu-id="4a537-107">Contains the name of the attribute.</span></span>|  
|<span data-ttu-id="4a537-108">基数</span><span class="sxs-lookup"><span data-stu-id="4a537-108">Cardinality</span></span>|<span data-ttu-id="4a537-109">指示关系的基数。</span><span class="sxs-lookup"><span data-stu-id="4a537-109">Indicates the cardinality of the relationship.</span></span> <span data-ttu-id="4a537-110">对于多对一关系，值为 Many，对于一对一关系，值为 One。</span><span class="sxs-lookup"><span data-stu-id="4a537-110">Values are Many, for a many to one relationship, or One, for a one to one relationship.</span></span> <span data-ttu-id="4a537-111">默认值为 Many。</span><span class="sxs-lookup"><span data-stu-id="4a537-111">Default value is Many.</span></span> <span data-ttu-id="4a537-112">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，基数属性不起作用-保留以供将来实现使用。</span><span class="sxs-lookup"><span data-stu-id="4a537-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cardinality property has no effect - its use is reserved for a future implementation.</span></span>|  
|<span data-ttu-id="4a537-113">名称</span><span class="sxs-lookup"><span data-stu-id="4a537-113">Name</span></span>|<span data-ttu-id="4a537-114">包含属性的友好名称。</span><span class="sxs-lookup"><span data-stu-id="4a537-114">Contains the friendly name of the attribute.</span></span>|  
|<span data-ttu-id="4a537-115">RelationshipType</span><span class="sxs-lookup"><span data-stu-id="4a537-115">RelationshipType</span></span>|<span data-ttu-id="4a537-116">指示成员关系是否随时间而更改。</span><span class="sxs-lookup"><span data-stu-id="4a537-116">Indicates whether member relationships change over time.</span></span> <span data-ttu-id="4a537-117">值为 Rigid 和 Flexible，前者表示成员之间的关系不随时间而更改，后者表示成员之间的关系随时间而更改。</span><span class="sxs-lookup"><span data-stu-id="4a537-117">Values are Rigid, which means that relationships between members do not change over time, or Flexible, which means that relationships between members change over time.</span></span> <span data-ttu-id="4a537-118">默认值为 Flexible。</span><span class="sxs-lookup"><span data-stu-id="4a537-118">Default is Flexible.</span></span> <span data-ttu-id="4a537-119">如果您将关系定义为 Flexible（柔性），则将删除聚合并作为增量更新的一部分重新计算（如果只添加了新成员，则将不删除聚合）。</span><span class="sxs-lookup"><span data-stu-id="4a537-119">If you define a relationship as flexible, aggregations are dropped and recomputed as part of an incremental update (they will not be dropped if only new members are added).</span></span> <span data-ttu-id="4a537-120">如果您将关系定义为 Rigid（刚性），则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会在增量更新维度时保留聚合。</span><span class="sxs-lookup"><span data-stu-id="4a537-120">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains aggregations when the dimension is incrementally updated.</span></span> <span data-ttu-id="4a537-121">如果定义为刚性的关系发生了实际更改， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会在增量处理过程中生成错误。</span><span class="sxs-lookup"><span data-stu-id="4a537-121">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates an error during incremental processing.</span></span> <span data-ttu-id="4a537-122">指定适当的关系和关系属性，可提高查询和处理性能。</span><span class="sxs-lookup"><span data-stu-id="4a537-122">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span>|  
|<span data-ttu-id="4a537-123">可见</span><span class="sxs-lookup"><span data-stu-id="4a537-123">Visible</span></span>|<span data-ttu-id="4a537-124">确定属性关系的可见性。</span><span class="sxs-lookup"><span data-stu-id="4a537-124">Determines the visibility of the attribute relationship.</span></span> <span data-ttu-id="4a537-125">值为 True 或 False。</span><span class="sxs-lookup"><span data-stu-id="4a537-125">Values are True or False.</span></span> <span data-ttu-id="4a537-126">默认值为 True。</span><span class="sxs-lookup"><span data-stu-id="4a537-126">Default is True.</span></span>|  
  
  
