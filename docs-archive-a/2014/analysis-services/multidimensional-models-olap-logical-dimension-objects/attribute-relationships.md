---
title: 属性关系 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- member properties [Analysis Services], attribute relationships
- security [Analysis Services], properties
- PROPERTIES keyword
- storage [Analysis Services], attribute relationships
- natural hierarchies [Analysis Services]
- dimensions [Analysis Services], member properties
- queries [MDX], attribute relationships
- user-defined hierarchies [Analysis Services]
- attributes [Analysis Services], relationships
- member properties [Analysis Services]
- members [Analysis Services], attribute relationships
- storing data [Analysis Services], attribute relationships
- relationships [Analysis Services], attributes
ms.assetid: 2491422a-4cf5-4b23-b6ab-289222b22ce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 122638a2728a8a85ee58661196797383da20eef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690187"
---
# <a name="attribute-relationships"></a><span data-ttu-id="bc7d4-102">的维度设计器中，可以在“维度结构”视图的</span><span class="sxs-lookup"><span data-stu-id="bc7d4-102">Attribute Relationships</span></span>
  <span data-ttu-id="bc7d4-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度中的属性始终直接或间接与键属性相关。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="bc7d4-104">当您基于星型架构（在该架构中，所有维度属性都派生自同一关系表）定义维度时，维度的键属性和每个非键属性之间会自动定义属性关系。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-104">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="bc7d4-105">当您基于雪花架构（在该架构中，维度属性派生自多个相关的表）定义维度时，会自动按如下方式定义属性关系：</span><span class="sxs-lookup"><span data-stu-id="bc7d4-105">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span>  
  
-   <span data-ttu-id="bc7d4-106">在键属性与绑定到主维度表中各列的每个非键属性之间定义。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-106">Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span>  
  
-   <span data-ttu-id="bc7d4-107">在键属性与绑定到辅助表中链接基础维度表的外键的属性之间定义。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-107">Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span>  
  
-   <span data-ttu-id="bc7d4-108">在绑定到辅助表中外键的属性与绑定到辅助表中各列的每个非键属性之间定义。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-108">Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>  
  
 <span data-ttu-id="bc7d4-109">但是，由于多种原因您可能需要更改这些默认的属性关系。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-109">However, there are a number of reasons why you might want to change these default attribute relationships.</span></span> <span data-ttu-id="bc7d4-110">例如，您可能需要定义自然层次结构、自定义排序顺序或基于非键属性的维度粒度。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-110">For example, you might want to define a natural hierarchy, a custom sort order, or dimension granularity based on a non-key attribute.</span></span> <span data-ttu-id="bc7d4-111">有关详细信息，请参阅[维度特性属性参考](../multidimensional-models/dimension-attribute-properties-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-111">For more information, see [Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc7d4-112">特性关系在多维表达式 (MDX) 中称作成员属性。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-112">Attribute relationships are known in Multidimensional Expressions (MDX) as member properties.</span></span>  
  
## <a name="natural-hierarchy-relationships"></a><span data-ttu-id="bc7d4-113">自然层次结构关系</span><span class="sxs-lookup"><span data-stu-id="bc7d4-113">Natural Hierarchy Relationships</span></span>  
 <span data-ttu-id="bc7d4-114">当用户定义层次结构中包含的每个属性都与其下直接属性具有一对多关系时，层次结构就是自然层次结构。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-114">A hierarchy is a natural hierarchy when each attribute included in the user-defined hierarchy has a one to many relationship with the attribute immediately below it.</span></span> <span data-ttu-id="bc7d4-115">例如，请参考基于具有八列的关系源表的“客户”维度：</span><span class="sxs-lookup"><span data-stu-id="bc7d4-115">For example, consider a Customer dimension based on a relational source table with eight columns:</span></span>  
  
-   <span data-ttu-id="bc7d4-116">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="bc7d4-116">CustomerKey</span></span>  
  
-   <span data-ttu-id="bc7d4-117">CustomerName</span><span class="sxs-lookup"><span data-stu-id="bc7d4-117">CustomerName</span></span>  
  
-   <span data-ttu-id="bc7d4-118">年龄</span><span class="sxs-lookup"><span data-stu-id="bc7d4-118">Age</span></span>  
  
-   <span data-ttu-id="bc7d4-119">性别</span><span class="sxs-lookup"><span data-stu-id="bc7d4-119">Gender</span></span>  
  
-   <span data-ttu-id="bc7d4-120">电子邮件</span><span class="sxs-lookup"><span data-stu-id="bc7d4-120">Email</span></span>  
  
-   <span data-ttu-id="bc7d4-121">城市</span><span class="sxs-lookup"><span data-stu-id="bc7d4-121">City</span></span>  
  
-   <span data-ttu-id="bc7d4-122">国家/地区</span><span class="sxs-lookup"><span data-stu-id="bc7d4-122">Country</span></span>  
  
-   <span data-ttu-id="bc7d4-123">区域</span><span class="sxs-lookup"><span data-stu-id="bc7d4-123">Region</span></span>  
  
 <span data-ttu-id="bc7d4-124">相应的 Analysis Services 维度具有七个属性：</span><span class="sxs-lookup"><span data-stu-id="bc7d4-124">The corresponding Analysis Services dimension has seven attributes:</span></span>  
  
-   <span data-ttu-id="bc7d4-125">客户（基于 CustomerKey，其中 CustomerName 提供成员名称）</span><span class="sxs-lookup"><span data-stu-id="bc7d4-125">Customer (based on CustomerKey, with CustomerName supplying member names)</span></span>  
  
-   <span data-ttu-id="bc7d4-126">年龄、性别、电子邮件、市县、地区、国家(地区)</span><span class="sxs-lookup"><span data-stu-id="bc7d4-126">Age, Gender, Email, City, Region, Country</span></span>  
  
 <span data-ttu-id="bc7d4-127">通过在某级别的属性和此级别下面的级别的属性之间创建属性关系，强制执行表示自然层次结构的关系。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-127">Relationships representing natural hierarchies are enforced by creating an attribute relationship between the attribute for a level and the attribute for the level below it.</span></span> <span data-ttu-id="bc7d4-128">对于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，这可指定自然关系和潜在聚合。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-128">For [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], this specifies a natural relationship and potential aggregation.</span></span> <span data-ttu-id="bc7d4-129">在“客户”维度中，“国家(地区)”、“区域”、“市县”和“客户”属性具有自然层次结构。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-129">In the Customer dimension, a natural hierarchy exists for the Country, Region, City, and Customer attributes.</span></span> <span data-ttu-id="bc7d4-130">通过添加下列属性关系来说明 `{Country, Region, City, Customer}` 的自然层次结构：</span><span class="sxs-lookup"><span data-stu-id="bc7d4-130">The natural hierarchy for `{Country, Region, City, Customer}` is described by adding the following attribute relationships:</span></span>  
  
-   <span data-ttu-id="bc7d4-131">与“区域”属性具有属性关系的“国家(地区)”属性。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-131">The Country attribute as an attribute relationship to the Region attribute.</span></span>  
  
-   <span data-ttu-id="bc7d4-132">与“市县”属性具有属性关系的“区域”属性。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-132">The Region attribute as an attribute relationship to the City attribute.</span></span>  
  
-   <span data-ttu-id="bc7d4-133">与“客户”属性具有属性关系的“市县”属性。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-133">The City attribute as an attribute relationship to the Customer attribute.</span></span>  
  
 <span data-ttu-id="bc7d4-134">若要在多维数据集中导航数据，您还可以创建一个用户定义的层次结构，该层次结构不表示数据 (（称为*即席*层次结构或*报表*层次结构) ）中的自然层次结构。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-134">For navigating data in the cube, you can also create a user-defined hierarchy that does not represent a natural hierarchy in the data (which is called an *ad hoc* or *reporting* hierarchy).</span></span> <span data-ttu-id="bc7d4-135">例如，您可以基于 `{Age, Gender}` 创建用户定义层次结构。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-135">For example, you could create a user-defined hierarchy based on `{Age, Gender}`.</span></span> <span data-ttu-id="bc7d4-136">用户不会看到这两个层次结构的行为方式有任何差别，但自然层次结构从用户隐藏了聚合和索引结构，后者用于源数据中的自然关系。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-136">Users do not see any difference in how the two hierarchies behave, although the natural hierarchy benefits from aggregating and indexing structures - hidden from the user - that account for the natural relationships in the source data.</span></span>  
  
 <span data-ttu-id="bc7d4-137">级别的 `SourceAttribute` 属性确定用于说明该级别的特性。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-137">The `SourceAttribute` property of a level determines which attribute is used to describe the level.</span></span> <span data-ttu-id="bc7d4-138">特性的 `KeyColumns` 属性指定数据源视图中提供成员的列。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-138">The `KeyColumns` property on the attribute specifies the column in the data source view that supplies the members.</span></span> <span data-ttu-id="bc7d4-139">特性的 `NameColumn` 属性可以指定成员的其他名称列。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-139">The `NameColumn` property on the attribute can specify a different name column for the members.</span></span>  
  
 <span data-ttu-id="bc7d4-140">若要使用定义用户定义层次结构中的级别 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，可以使用**维度设计器**来选择维度属性、维度表中的列或多维数据集的数据源视图中包含的相关表中的列。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-140">To define a level in a user-defined hierarchy using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the **Dimension Designer** allows you to select a dimension attribute, a column in a dimension table, or a column from a related table included in the data source view for the cube.</span></span> <span data-ttu-id="bc7d4-141">有关创建用户定义的层次结构的详细信息，请参阅[创建用户定义的层次结构](../multidimensional-models/user-defined-hierarchies-create.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-141">For more information about creating user-defined hierarchies, see [Create User-Defined Hierarchies](../multidimensional-models/user-defined-hierarchies-create.md).</span></span>  
  
 <span data-ttu-id="bc7d4-142">在 Analysis Services 中，通常对成员的内容进行假定。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-142">In Analysis Services, an assumption is usually made about the content of members.</span></span> <span data-ttu-id="bc7d4-143">叶成员没有后代，并且包含派生自基础数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-143">Leaf members have no descendents and contain data derived from underlying data sources.</span></span> <span data-ttu-id="bc7d4-144">非叶成员则具有后代，并且包含派生自对子成员执行的聚合的数据。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-144">Nonleaf members have descendents and contain data derived from aggregations performed on child members.</span></span> <span data-ttu-id="bc7d4-145">在聚合级别中，各成员基于其从属级别的聚合。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-145">In aggregated levels, members are based on aggregations of subordinate levels.</span></span> <span data-ttu-id="bc7d4-146">因此，当级别源特性的 `IsAggregatable` 属性设置为 `False` 时，不应添加可聚合的特性作为该级别上面的级别。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-146">Therefore, when the `IsAggregatable` property is set to `False` on a source attribute for a level, no aggregatable attributes should be added as levels above it.</span></span>  
  
## <a name="defining-an-attribute-relationship"></a><span data-ttu-id="bc7d4-147">定义属性关系</span><span class="sxs-lookup"><span data-stu-id="bc7d4-147">Defining an Attribute Relationship</span></span>  
 <span data-ttu-id="bc7d4-148">创建属性关系时的主要约束是确保，对于属性关系引用的属性，属性关系所属的属性中的任何成员的值不超过一个。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-148">The main constraint when you create an attribute relationship is to make sure that the attribute referred to by the attribute relationship has no more than one value for any member in the attribute to which the attribute relationship belongs.</span></span> <span data-ttu-id="bc7d4-149">例如，如果您在“市县”属性与“省市自治区”属性之间定义了关系，则每个市县只能与单个省市自治区相关。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-149">For example, if you define a relationship between a City attribute and a State attribute, each city can only relate to a single state.</span></span>  
  
## <a name="attribute-relationship-queries"></a><span data-ttu-id="bc7d4-150">属性关系查询</span><span class="sxs-lookup"><span data-stu-id="bc7d4-150">Attribute Relationship Queries</span></span>  
 <span data-ttu-id="bc7d4-151">可以通过 MDX `PROPERTIES` 语句的 `SELECT` 关键字以成员属性的形式使用 MDX 查询从特性关系检索数据。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-151">You can use MDX queries to retrieve data from attribute relationships, in the form of member properties, with the `PROPERTIES` keyword of the MDX `SELECT` statement.</span></span> <span data-ttu-id="bc7d4-152">有关如何使用 MDX 检索成员属性的详细信息，请参阅[&#40;MDX&#41;使用成员属性](../multidimensional-models/mdx/mdx-member-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7d4-152">For more information about how to use MDX to retrieve member properties, see [Using Member Properties &#40;MDX&#41;](../multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7d4-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc7d4-153">See Also</span></span>  
 <span data-ttu-id="bc7d4-154">[属性和属性层次结构](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="bc7d4-154">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="bc7d4-155">[维度特性属性参考](../multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bc7d4-155">[Dimension Attribute Properties Reference](../multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="bc7d4-156">[用户层次结构](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="bc7d4-156">[User Hierarchies](user-hierarchies.md) </span></span>  
 [<span data-ttu-id="bc7d4-157">用户层次结构属性</span><span class="sxs-lookup"><span data-stu-id="bc7d4-157">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
