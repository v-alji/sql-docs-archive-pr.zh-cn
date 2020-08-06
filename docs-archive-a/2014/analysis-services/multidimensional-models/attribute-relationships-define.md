---
title: 定义属性关系 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: a694c68a55de2533c4ce7791d3be865008b6321f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577898"
---
# <a name="define-attribute-relationships"></a><span data-ttu-id="9c78d-102">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="9c78d-102">Define Attribute Relationships</span></span>
  <span data-ttu-id="9c78d-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，属性是维度的基本构造块。</span><span class="sxs-lookup"><span data-stu-id="9c78d-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes are the fundamental building block of a dimension.</span></span> <span data-ttu-id="9c78d-104">维度包含一组在属性关系基础上组织而成的属性。</span><span class="sxs-lookup"><span data-stu-id="9c78d-104">A dimension contains a set of attributes that are organized based on attribute relationships.</span></span>  
  
 <span data-ttu-id="9c78d-105">对于维度中包含的每个表，都存在将表的键属性与该表的其他属性相关联的属性关系。</span><span class="sxs-lookup"><span data-stu-id="9c78d-105">For each table included in a dimension, there is an attribute relationship that relates the table's key attribute to other attributes from that table.</span></span> <span data-ttu-id="9c78d-106">创建维度时可创建此关系。</span><span class="sxs-lookup"><span data-stu-id="9c78d-106">You create this relationship when you create the dimension.</span></span>  
  
 <span data-ttu-id="9c78d-107">属性关系具备以下优点：</span><span class="sxs-lookup"><span data-stu-id="9c78d-107">An attribute relationship provides the following advantages:</span></span>  
  
-   <span data-ttu-id="9c78d-108">减少维度处理所需的内存量。</span><span class="sxs-lookup"><span data-stu-id="9c78d-108">Reduces the amount of memory needed for dimension processing.</span></span> <span data-ttu-id="9c78d-109">加快维度、分区和查询的处理速度。</span><span class="sxs-lookup"><span data-stu-id="9c78d-109">This speeds up dimension, partition, and query processing.</span></span>  
  
-   <span data-ttu-id="9c78d-110">提高查询性能，因为存储访问速度更快而且执行计划更优化。</span><span class="sxs-lookup"><span data-stu-id="9c78d-110">Increases query performance because storage access is faster and execution plans are better optimized.</span></span>  
  
-   <span data-ttu-id="9c78d-111">如果用户定义的层次结构是沿关系路径定义的，则聚合设计算法会选择更有效的聚合。</span><span class="sxs-lookup"><span data-stu-id="9c78d-111">Results in the selection of more effective aggregates by the aggregation design algorithms, provided that user-defined hierarchies have been defined along the relationship paths.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c78d-112">有关定义和配置属性关系的重要性和意义的详细信息，请参阅[SQL Server 2005 Analysis Services 性能指南](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的 "提高查询性能" 一节。</span><span class="sxs-lookup"><span data-stu-id="9c78d-112">For more information about the importance and implications of defining and configuring attribute relationships, see the section, "Enhancing query performance," in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="attribute-relationship-considerations"></a><span data-ttu-id="9c78d-113">属性关系注意事项</span><span class="sxs-lookup"><span data-stu-id="9c78d-113">Attribute Relationship Considerations</span></span>  
 <span data-ttu-id="9c78d-114">当基础数据支持时，还应定义属性间唯一的属性关系。</span><span class="sxs-lookup"><span data-stu-id="9c78d-114">When the underlying data supports it, you should also define unique attribute relationships between attributes.</span></span> <span data-ttu-id="9c78d-115">若要定义唯一属性关系，请使用维度设计器的 **“属性关系”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9c78d-115">To define unique attribute relationships, use the **Attribute Relationships** tab of Dimension Designer.</span></span>  
  
 <span data-ttu-id="9c78d-116">具有对外关系的任何属性必须具有与其相关属性关联的唯一键。</span><span class="sxs-lookup"><span data-stu-id="9c78d-116">Any attribute that has an outgoing relationship must have a unique key relative to its related attribute.</span></span> <span data-ttu-id="9c78d-117">换言之，源属性中的一个成员必须并且只能标识相关属性中的一个成员。</span><span class="sxs-lookup"><span data-stu-id="9c78d-117">In other words, a member in a source attribute must identify one and only one member in a related attribute.</span></span> <span data-ttu-id="9c78d-118">例如，关系“City -> State”。</span><span class="sxs-lookup"><span data-stu-id="9c78d-118">For example, consider the relationship, City -> State.</span></span> <span data-ttu-id="9c78d-119">在此关系中，源属性为 City，相关属性为 State。</span><span class="sxs-lookup"><span data-stu-id="9c78d-119">In this relationship, the source attribute is City and the related attribute is State.</span></span> <span data-ttu-id="9c78d-120">源属性为 "多" 方，相关端为多对一关系的 "一" 方。</span><span class="sxs-lookup"><span data-stu-id="9c78d-120">The source attribute is the "many" side and the related side is the "one" side of the many-to-one relationship.</span></span> <span data-ttu-id="9c78d-121">源属性的键为 City + State。</span><span class="sxs-lookup"><span data-stu-id="9c78d-121">The key for the source attribute would be City + State.</span></span> <span data-ttu-id="9c78d-122">有关详细信息，请参阅 [创建、修改或删除属性关系](attribute-relationships-create-modify-or-delete-relationship.md)</span><span class="sxs-lookup"><span data-stu-id="9c78d-122">For more information, see [Create, Modify, or Delete an Attribute Relationship](attribute-relationships-create-modify-or-delete-relationship.md).</span></span>  
  
 <span data-ttu-id="9c78d-123">有关特性关系的属性详细信息，请参阅 [配置特性关系属性](attribute-relationships-configure-attribute-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9c78d-123">For more information about properties of an attribute relationship, see [Configure Attribute Relationship Properties](attribute-relationships-configure-attribute-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c78d-124">属性关系定义不正确会导致查询结果无效。</span><span class="sxs-lookup"><span data-stu-id="9c78d-124">Defining attribute relationships incorrectly can cause invalid query results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c78d-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c78d-125">See Also</span></span>  
 [<span data-ttu-id="9c78d-126">的维度设计器中，可以在“维度结构”视图的</span><span class="sxs-lookup"><span data-stu-id="9c78d-126">Attribute Relationships</span></span>](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
