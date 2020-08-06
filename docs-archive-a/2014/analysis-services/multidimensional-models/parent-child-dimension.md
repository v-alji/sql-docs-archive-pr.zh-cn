---
title: 父子层次结构 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], parent-child
- dimensions [Analysis Services], parent-child
- parent attributes [Analysis Services]
- data members [Analysis Services]
- hierarchies [Analysis Services], multilevel
- self-joins
- self-referencing relationships
- members [Analysis Services], data
- parent-child dimensions [Analysis Services]
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
author: minewiskan
ms.author: owend
ms.openlocfilehash: b08641e9ba17e6ad2e2f4112e01073d448aa8564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694147"
---
# <a name="parent-child-hierarchy"></a><span data-ttu-id="c9d7b-102">父子层次结构</span><span class="sxs-lookup"><span data-stu-id="c9d7b-102">Parent-Child Hierarchy</span></span>
  <span data-ttu-id="c9d7b-103">父子层次结构是标准维度中包含父属性的层次结构。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-103">A parent-child hierarchy is a hierarchy in a standard dimension that contains a parent attribute.</span></span> <span data-ttu-id="c9d7b-104">父属性用于说明维度主表内部的自引用关系或自联接\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-104">A parent attribute describes a *self-referencing relationship*, or *self-join*, within a dimension main table.</span></span> <span data-ttu-id="c9d7b-105">父子层次结构是根据单个父属性构造的。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-105">Parent-child hierarchies are constructed from a single parent attribute.</span></span> <span data-ttu-id="c9d7b-106">层次结构中出现的级别是通过与父属性关联的成员之间的父子关系形成的，因此只为一个父子层次结构分配一个级别。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-106">Only one level is assigned to a parent-child hierarchy, because the levels present in the hierarchy are drawn from the parent-child relationships between members associated with the parent attribute.</span></span> <span data-ttu-id="c9d7b-107">父子层次结构内成员的位置由父特性的 `KeyColumns` 和 `RootMemberIf` 属性确定，而级别内成员的位置则由父特性的 `OrderBy` 属性确定。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-107">The position of a member in a parent-child hierarchy is determined by the `KeyColumns` and `RootMemberIf` properties of the parent attribute, whereas the position of a member in a level is determined by the `OrderBy` property of the parent attribute.</span></span> <span data-ttu-id="c9d7b-108">有关特性属性的详细信息，请参阅 [属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-108">For more information about attribute properties, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
 <span data-ttu-id="c9d7b-109">由于父子层次结构中各级别之间均存在父子关系，因此一些非叶成员除了包含从子成员聚合的数据外，还可以包含派生自基础数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-109">Because of parent-child relationships between levels in a parent-child hierarchy, some nonleaf members can also have data derived from underlying data sources, in addition to data aggregated from child members.</span></span>  
  
## <a name="dimension-schema"></a><span data-ttu-id="c9d7b-110">维度架构</span><span class="sxs-lookup"><span data-stu-id="c9d7b-110">Dimension Schema</span></span>  
 <span data-ttu-id="c9d7b-111">父子层次结构的维度架构依赖于维度主表中提供的自引用关系。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-111">The dimension schema of a parent-child hierarchy depends on a self-referencing relationship present on the dimension main table.</span></span> <span data-ttu-id="c9d7b-112">例如，以下关系图说明了 **示例数据库中的** DimOrganization [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] 维度主表。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-112">For example, the following diagram illustrates the **DimOrganization** dimension main table in the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] sample database.</span></span>  
  
 <span data-ttu-id="c9d7b-113">![DimOrganization 表中的自引用联接](../dev-guide/media/dimorganization.gif "DimOrganization 表中的自引用联接")</span><span class="sxs-lookup"><span data-stu-id="c9d7b-113">![Self-referencing join in DimOrganization table](../dev-guide/media/dimorganization.gif "Self-referencing join in DimOrganization table")</span></span>  
  
 <span data-ttu-id="c9d7b-114">在该维度表中， **ParentOrganizationKey** 列与 **OrganizationKey** 主键列具有外键关系。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-114">In this dimension table, the **ParentOrganizationKey** column has a foreign key relationship with the **OrganizationKey** primary key column.</span></span> <span data-ttu-id="c9d7b-115">换言之，该表中的每个记录都可以通过父子关系与该表中的其他记录相关联。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-115">In other words, each record in this table can be related through a parent-child relationship with another record in the table.</span></span> <span data-ttu-id="c9d7b-116">这种自联接通常用于表示单位的实体数据，例如某个部门内部的雇员管理结构。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-116">This kind of self-join is generally used to represent organization entity data, such as the management structure of employees in a department.</span></span>  
  
## <a name="hierarchies-and-levels"></a><span data-ttu-id="c9d7b-117">层次结构和级别</span><span class="sxs-lookup"><span data-stu-id="c9d7b-117">Hierarchies and Levels</span></span>  
 <span data-ttu-id="c9d7b-118">不具有父子关系的维度通过分组依据属性和排序依据属性来构造层次结构。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-118">Dimensions that do not have a parent-child relationship construct hierarchies by grouping and ordering attributes.</span></span> <span data-ttu-id="c9d7b-119">这些维度从属性名称中派生出其层次结构的级别名称。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-119">These dimensions derive the level names for their hierarchies from the attribute names.</span></span>  
  
 <span data-ttu-id="c9d7b-120">但是，父子维度通过检查维度主表中包含的数据，然后评估该表中记录之间的父子关系来构造父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-120">However, parent-child dimensions construct parent-child hierarchies by examining the data that the dimension main table contains, and then evaluating the parent-child relationships between the records in the table.</span></span> <span data-ttu-id="c9d7b-121">有关父子层次结构的详细信息，请参阅 [用户层次结构](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-121">For more information about parent-child hierarchies, see [User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).</span></span>  
  
 <span data-ttu-id="c9d7b-122">父子层次结构不会从用于创建层次结构的属性中派生父子层次结构中级别的名称。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-122">Parent-child hierarchies do not derive the names for the levels in a parent-child hierarchy from the attributes that are used to create the hierarchy.</span></span> <span data-ttu-id="c9d7b-123">相反，这些维度通过使用命名模板自动创建级别名称-一个字符串表达式，可以在控制属性如何生成属性层次结构的父属性级别指定。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-123">Instead, these dimensions create level names automatically by using a naming template-a string expression you can specify at the level of the parent attribute that controls how the attribute generates the attribute hierarchy.</span></span> <span data-ttu-id="c9d7b-124">有关如何设置父属性的命名模板的详细信息，请参阅 [属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-124">For more information about how to set the naming template for a parent attribute, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="data-members"></a><span data-ttu-id="c9d7b-125">数据成员</span><span class="sxs-lookup"><span data-stu-id="c9d7b-125">Data Members</span></span>  
 <span data-ttu-id="c9d7b-126">通常，维度中的叶成员包含直接派生自基础数据源的数据，而非叶成员包含派生自对子成员所执行的聚合的数据。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-126">Typically, leaf members in a dimension contain data derived directly from underlying data sources, whereas nonleaf members contain data derived from aggregations performed on child members.</span></span>  
  
 <span data-ttu-id="c9d7b-127">但是在父子层次结构中，一些非叶成员除了包含基于子成员聚合的数据外，还可能包含派生自基础数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-127">However, parent-child hierarchies might have some nonleaf members whose data is derived from underlying data sources, in addition to data aggregated from child members.</span></span> <span data-ttu-id="c9d7b-128">对于父子层次结构中的这些非叶成员，可为其创建包含基础事实数据表数据的特殊的系统生成子成员。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-128">For these nonleaf members in a parent-child hierarchy, special system-generated child members can be created that contain the underlying fact table data.</span></span> <span data-ttu-id="c9d7b-129">这些特殊子成员称为“数据成员 \*\*”，它们包含一个与非叶成员直接相关、且与通过该非叶成员后代计算出来的汇总值无关的值。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-129">Referred to as *data members*, these special child members contain a value that is directly associated with a nonleaf member and is independent of the summary value calculated from the descendants of the nonleaf member.</span></span> <span data-ttu-id="c9d7b-130">有关数据成员的详细信息，请参阅 [父子层次结构中的属性](parent-child-dimension-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d7b-130">For more information about data members, see [Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d7b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9d7b-131">See Also</span></span>  
 <span data-ttu-id="c9d7b-132">[父子层次结构中的属性](parent-child-dimension-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="c9d7b-132">[Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md) </span></span>  
 [<span data-ttu-id="c9d7b-133">数据库维度属性</span><span class="sxs-lookup"><span data-stu-id="c9d7b-133">Database Dimension Properties</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
