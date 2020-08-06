---
title: 派生层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies
- hierarchies [Master Data Services], derived hierarchies
- derived hierarchies, about derived hierarchies
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92867f225a8f14e59cb9a519f174902d0739773a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591929"
---
# <a name="derived-hierarchies-master-data-services"></a><span data-ttu-id="0c26a-102">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-102">Derived Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="0c26a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 派生层次结构从在模型的实体之间已存在的基于域的属性关系中派生。</span><span class="sxs-lookup"><span data-stu-id="0c26a-103">A [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] derived hierarchy is derived from the domain-based attribute relationships that already exist between entities in a model.</span></span>

 <span data-ttu-id="0c26a-104">您可以创建一个派生层次结构，以便突出显示模型中任何现有的基于域的属性关系。</span><span class="sxs-lookup"><span data-stu-id="0c26a-104">You can create a derived hierarchy to highlight any of the existing domain-based attribute relationships in the model.</span></span>

## <a name="leaf-members-group-other-leaf-members"></a><span data-ttu-id="0c26a-105">叶成员将其他叶成员分组</span><span class="sxs-lookup"><span data-stu-id="0c26a-105">Leaf Members Group Other Leaf Members</span></span>
 <span data-ttu-id="0c26a-106">在派生层次结构中，一个实体的叶成员用于对其他实体的叶成员进行分组。</span><span class="sxs-lookup"><span data-stu-id="0c26a-106">In a derived hierarchy, the leaf members from one entity are used to group the leaf members of another entity.</span></span> <span data-ttu-id="0c26a-107">派生层次结构基于这些实体之间的关系。</span><span class="sxs-lookup"><span data-stu-id="0c26a-107">A derived hierarchy is based on the relationship between these entities.</span></span> <span data-ttu-id="0c26a-108">显式层次结构正相反，它仅基于来自一个实体的成员，并且以您指定的任何方式结构化。</span><span class="sxs-lookup"><span data-stu-id="0c26a-108">An explicit hierarchy, in contrast, is based on members from a single entity only and is structured in any way you specify.</span></span>

 <span data-ttu-id="0c26a-109">可以更改派生层次结构的结构而不会影响基础数据。</span><span class="sxs-lookup"><span data-stu-id="0c26a-109">You can change the structure of a derived hierarchy without affecting the underlying data.</span></span> <span data-ttu-id="0c26a-110">只要关系仍存在于模型中，删除派生层次结构就不会影响您的主数据。</span><span class="sxs-lookup"><span data-stu-id="0c26a-110">As long as the relationships still exist in the model, deleting a derived hierarchy has no effect on your master data.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="0c26a-111">显式层次结构与派生层次结构</span><span class="sxs-lookup"><span data-stu-id="0c26a-111">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="0c26a-112">下表显示显式层次结构与派生层次结构之间的一些区别。</span><span class="sxs-lookup"><span data-stu-id="0c26a-112">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="0c26a-113">显式层次结构</span><span class="sxs-lookup"><span data-stu-id="0c26a-113">Explicit Hierarchies</span></span>|<span data-ttu-id="0c26a-114">派生层次结构</span><span class="sxs-lookup"><span data-stu-id="0c26a-114">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="0c26a-115">结构是由用户定义的</span><span class="sxs-lookup"><span data-stu-id="0c26a-115">Structure is defined by the user</span></span>|<span data-ttu-id="0c26a-116">结构是从基于域的属性间的关系派生的</span><span class="sxs-lookup"><span data-stu-id="0c26a-116">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="0c26a-117">包含单个实体的成员</span><span class="sxs-lookup"><span data-stu-id="0c26a-117">Contains members from a single entity</span></span>|<span data-ttu-id="0c26a-118">包含多个实体的成员</span><span class="sxs-lookup"><span data-stu-id="0c26a-118">Contains members from multiple entities</span></span>|
|<span data-ttu-id="0c26a-119">使用合并成员对其他成员进行分组</span><span class="sxs-lookup"><span data-stu-id="0c26a-119">Uses consolidated members to group other members</span></span>|<span data-ttu-id="0c26a-120">使用来自一个实体的叶成员对其他实体的叶成员进行分组</span><span class="sxs-lookup"><span data-stu-id="0c26a-120">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="0c26a-121">可以是不规则的</span><span class="sxs-lookup"><span data-stu-id="0c26a-121">Can be ragged</span></span>|<span data-ttu-id="0c26a-122">始终包含一致的级别数</span><span class="sxs-lookup"><span data-stu-id="0c26a-122">Always contains a consistent number of levels</span></span>|

## <a name="creating-a-variable-depth-hierarchy"></a><span data-ttu-id="0c26a-123">创建可变深度层次结构</span><span class="sxs-lookup"><span data-stu-id="0c26a-123">Creating a Variable-Depth Hierarchy</span></span>
 <span data-ttu-id="0c26a-124">有两种建议的方法可创建可变深度层次结构：</span><span class="sxs-lookup"><span data-stu-id="0c26a-124">There are two recommended ways to create a variable-depth hierarchy:</span></span>

-   <span data-ttu-id="0c26a-125">如果需要所有级别具有相同的属性，请创建一个实体，然后使用基于该实体的基于域的属性创建此实体的递归层次结构。</span><span class="sxs-lookup"><span data-stu-id="0c26a-125">If you need all levels to have the same attributes, create a single entity, and then create a recursive hierarchy on this entity, using a domain-based attribute that is based on the entity.</span></span>

-   <span data-ttu-id="0c26a-126">如果需要叶成员一组属性，上级另一组属性，请创建两个实体来生成一个派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="0c26a-126">If you need one set of attributes for the leaf members and another set of attributes in the upper levels, create two entities for a derived hierarchy.</span></span> <span data-ttu-id="0c26a-127">对于叶实体，请使用基于父实体的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="0c26a-127">For the leaf entity, use a domain-based attribute that is based upon the parent entity.</span></span> <span data-ttu-id="0c26a-128">对于父实体，请使用基于其自身的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="0c26a-128">For the parent entity, use a domain-based attribute that is based upon itself.</span></span>

## <a name="derived-hierarchy-example"></a><span data-ttu-id="0c26a-129">派生层次结构示例</span><span class="sxs-lookup"><span data-stu-id="0c26a-129">Derived Hierarchy Example</span></span>
 <span data-ttu-id="0c26a-130">在下面的示例中，Product 实体的叶成员按 Subcategory 实体的叶成员进行分组，后者又按 Category 实体的叶成员进行分组。</span><span class="sxs-lookup"><span data-stu-id="0c26a-130">In the following example, leaf members of the Product entity are grouped by leaf members of the Subcategory entity, which are then grouped by leaf members of the Category entity.</span></span> <span data-ttu-id="0c26a-131">此层次结构是可能的，因为 Product 实体具有名为 Subcategory 的基于域的属性，并且 Subcategory 实体具有名为 Category 的基于域的属性。</span><span class="sxs-lookup"><span data-stu-id="0c26a-131">This hierarchy is possible because the Product entity has a domain-based attribute named Subcategory, and the Subcategory entity has a domain-based attribute named Category.</span></span>

 <span data-ttu-id="0c26a-132">该层次结构显示如何对成员进行分组。</span><span class="sxs-lookup"><span data-stu-id="0c26a-132">The hierarchy structure shows how the members are grouped.</span></span> <span data-ttu-id="0c26a-133">具有最多成员的实体位于底部。</span><span class="sxs-lookup"><span data-stu-id="0c26a-133">The entity with the most members is at the bottom.</span></span>

 <span data-ttu-id="0c26a-134">![从模型结构派生的层次结构](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "从模型结构派生的层次结构")</span><span class="sxs-lookup"><span data-stu-id="0c26a-134">![Hierarchy Derived from Model Structure](../../2014/master-data-services/media/mds-conc-derived-hierarchy-structure.gif "Hierarchy Derived from Model Structure")</span></span>

 <span data-ttu-id="0c26a-135">在派生层次结构中，可以突出显示 Product 和 Subcategory 之间的关系，然后突出显示 Subcategory 和 Category 之间的关系。</span><span class="sxs-lookup"><span data-stu-id="0c26a-135">In a derived hierarchy, you can highlight the relationship between Product and Subcategory, and then between Subcategory and Category.</span></span> <span data-ttu-id="0c26a-136">当您查看此层次结构中的成员时，在树的每个级别中包含同一实体中的成员。</span><span class="sxs-lookup"><span data-stu-id="0c26a-136">When you view the members in this hierarchy, each level in the tree contains members from the same entity.</span></span>

 <span data-ttu-id="0c26a-137">![山地车派生层次结构示例](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "山地车派生层次结构示例")</span><span class="sxs-lookup"><span data-stu-id="0c26a-137">![Mountain Bike Derived Hierarchy Example](../../2014/master-data-services/media/mds-conc-derived-hierarchy-example.gif "Mountain Bike Derived Hierarchy Example")</span></span>

 <span data-ttu-id="0c26a-138">这种类型的层次结构防止将成员移到无效的级别。</span><span class="sxs-lookup"><span data-stu-id="0c26a-138">This type of hierarchy prevents you from moving a member to a level that is not valid.</span></span> <span data-ttu-id="0c26a-139">例如，可以将 Road-650 自行车从子类别“公路自行车”移到另一个子类别“山地车”。</span><span class="sxs-lookup"><span data-stu-id="0c26a-139">For example, you can move the Road-650 bike from one subcategory, Road Bikes, to another, Mountain Bikes.</span></span> <span data-ttu-id="0c26a-140">不能直接将 Road-650 移到某个类别下，如 1 {自行车}。</span><span class="sxs-lookup"><span data-stu-id="0c26a-140">You cannot move Road-650 directly under a category, like 1 {Bikes}.</span></span> <span data-ttu-id="0c26a-141">每次在层次结构树中移动成员时，将更改该成员基于域的属性值以反映移动。</span><span class="sxs-lookup"><span data-stu-id="0c26a-141">Each time you move a member in the hierarchy tree, the member's domain-based attribute value changes to reflect the move.</span></span>

## <a name="notes"></a><span data-ttu-id="0c26a-142">注释</span><span class="sxs-lookup"><span data-stu-id="0c26a-142">Notes</span></span>
 <span data-ttu-id="0c26a-143">派生层次结构树中的所有成员都按代码排序。</span><span class="sxs-lookup"><span data-stu-id="0c26a-143">All members in a derived hierarchy tree are sorted by code.</span></span> <span data-ttu-id="0c26a-144">不能更改排序顺序。</span><span class="sxs-lookup"><span data-stu-id="0c26a-144">You cannot change the sort order.</span></span>

 <span data-ttu-id="0c26a-145">如果成员基于域的属性为空且该属性用于派生层次结构，则该成员不会显示在层次结构中。</span><span class="sxs-lookup"><span data-stu-id="0c26a-145">If a member's domain-based attribute is blank and the attribute is used for a derived hierarchy, the member is not displayed in the hierarchy.</span></span> <span data-ttu-id="0c26a-146">创建业务规则来要求填充属性。</span><span class="sxs-lookup"><span data-stu-id="0c26a-146">Create business rules to require attributes to be populated.</span></span> <span data-ttu-id="0c26a-147">有关详细信息，请参阅[要求属性值 &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0c26a-147">For more information, see [Require Attribute Values &#40;Master Data Services&#41;](require-attribute-values-master-data-services.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="0c26a-148">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0c26a-148">Related Tasks</span></span>

|<span data-ttu-id="0c26a-149">任务说明</span><span class="sxs-lookup"><span data-stu-id="0c26a-149">Task Description</span></span>|<span data-ttu-id="0c26a-150">主题</span><span class="sxs-lookup"><span data-stu-id="0c26a-150">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="0c26a-151">创建新的派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="0c26a-151">Create a new derived hierarchy.</span></span>|[<span data-ttu-id="0c26a-152">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-152">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="0c26a-153">隐藏或删除现有派生层次结构中的级别。</span><span class="sxs-lookup"><span data-stu-id="0c26a-153">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="0c26a-154">隐藏或删除派生层次结构中的级别 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-154">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="0c26a-155">更改现有派生层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="0c26a-155">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="0c26a-156">更改派生层次结构名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-156">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="0c26a-157">删除现有派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="0c26a-157">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="0c26a-158">删除派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-158">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="0c26a-159">相关内容</span><span class="sxs-lookup"><span data-stu-id="0c26a-159">Related Content</span></span>

-   [<span data-ttu-id="0c26a-160">基于域的属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-160">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="0c26a-161">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-161">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="0c26a-162">递归层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-162">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="0c26a-163">具有显式顶端的派生层次结构 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0c26a-163">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="0c26a-164">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0c26a-164">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


