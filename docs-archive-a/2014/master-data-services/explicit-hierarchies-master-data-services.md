---
title: 显式层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, about explicit hierarchies
- hierarchies [Master Data Services], explicit hierarchies
- explicit hierarchies
ms.assetid: e6f44e37-e1f0-4c38-a816-1935a856d5a4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f37f341dc2c003683e696f2767a6b644047d5a0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689491"
---
# <a name="explicit-hierarchies-master-data-services"></a><span data-ttu-id="1097b-102">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-102">Explicit Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="1097b-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，显式层次结构以您指定的任意方式组织一个实体中的成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], an explicit hierarchy organizes members from a single entity in any way you specify.</span></span> <span data-ttu-id="1097b-104">显式层次结构可以是不规则的，并且与派生层次结构不同，该结构不依据基于域的属性关系。</span><span class="sxs-lookup"><span data-stu-id="1097b-104">The structure can be ragged and unlike derived hierarchies, explicit hierarchies are not based on domain-based attribute relationships.</span></span>

## <a name="consolidated-members-group-other-members"></a><span data-ttu-id="1097b-105">合并成员将其他成员分组</span><span class="sxs-lookup"><span data-stu-id="1097b-105">Consolidated Members Group Other Members</span></span>
 <span data-ttu-id="1097b-106">显式层次结构使用您为将其他成员分组而创建的合并成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-106">An explicit hierarchy uses consolidated members that you create for the purpose of grouping other members.</span></span> <span data-ttu-id="1097b-107">这些合并成员一次只能属于一个显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="1097b-107">These consolidated members can belong to only one explicit hierarchy at a time.</span></span> <span data-ttu-id="1097b-108">显式层次结构还包括关联的实体中的所有叶成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-108">An explicit hierarchy also includes all of the leaf members from the associated entity.</span></span>

 <span data-ttu-id="1097b-109">显式层次结构可以是不规则的，这意味着层次结构可以同时在不同级别结束。</span><span class="sxs-lookup"><span data-stu-id="1097b-109">An explicit hierarchy can be ragged, which means that the hierarchy can end at different levels simultaneously.</span></span> <span data-ttu-id="1097b-110">每个合并成员下面可以有不限数目的合并成员和叶成员，也可以没有任何成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-110">Each consolidated member can have an unlimited number of consolidated and leaf members underneath, or can have none.</span></span> <span data-ttu-id="1097b-111">叶成员可以在单个合并成员下，也可以在多个级别的合并成员下。</span><span class="sxs-lookup"><span data-stu-id="1097b-111">The leaf members can be under a single consolidated member or under multiple levels of consolidated members.</span></span>

> [!NOTE]
>  <span data-ttu-id="1097b-112">在创建显式层次结构前，必须为显式层次结构启用了实体。</span><span class="sxs-lookup"><span data-stu-id="1097b-112">Before you can create an explicit hierarchy, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="1097b-113">有关详细信息，请参阅为[显式层次结构和集合启用实体 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1097b-113">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>

## <a name="types-of-explicit-hierarchies"></a><span data-ttu-id="1097b-114">显式层次结构的类型</span><span class="sxs-lookup"><span data-stu-id="1097b-114">Types of Explicit Hierarchies</span></span>
 <span data-ttu-id="1097b-115">显式层次结构有两种类型：强制和非强制。</span><span class="sxs-lookup"><span data-stu-id="1097b-115">There are two types of explicit hierarchies: mandatory and non-mandatory.</span></span>

### <a name="mandatory-explicit-hierarchy"></a><span data-ttu-id="1097b-116">强制显式层次结构</span><span class="sxs-lookup"><span data-stu-id="1097b-116">Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="1097b-117">强制显式层次结构要求所有叶成员必须包含在层次结构树中。</span><span class="sxs-lookup"><span data-stu-id="1097b-117">A mandatory explicit hierarchy is a hierarchy in which all leaf members must be included in the hierarchy tree.</span></span> <span data-ttu-id="1097b-118">默认情况下，所有成员都包含在该树的根上。</span><span class="sxs-lookup"><span data-stu-id="1097b-118">By default, all members are included at the root of the tree.</span></span> <span data-ttu-id="1097b-119">您可以根据需要重新排列成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-119">You can rearrange the members as needed.</span></span>

### <a name="non-mandatory-explicit-hierarchy"></a><span data-ttu-id="1097b-120">非强制显式层次结构</span><span class="sxs-lookup"><span data-stu-id="1097b-120">Non-Mandatory Explicit Hierarchy</span></span>
 <span data-ttu-id="1097b-121">非强制显式层次结构是所有叶成员都处于系统创建的“未使用”\*\*\*\* 节点中的层次结构。</span><span class="sxs-lookup"><span data-stu-id="1097b-121">A non-mandatory explicit hierarchy is a hierarchy in which all leaf members are in a system-created **Unused** node.</span></span> <span data-ttu-id="1097b-122">可以根据需要将成员移出此节点。</span><span class="sxs-lookup"><span data-stu-id="1097b-122">You can move members out of this node as you need them.</span></span> <span data-ttu-id="1097b-123">其余成员可以保留在 **“未使用”** 节点中。</span><span class="sxs-lookup"><span data-stu-id="1097b-123">The rest of the members can remain in the **Unused** node.</span></span>

 <span data-ttu-id="1097b-124">使用非强制显式层次结构时，对层次结构所做的任何报告或分析可能与对强制层次结构所做的报告或分析不一致。</span><span class="sxs-lookup"><span data-stu-id="1097b-124">When you use non-mandatory explicit hierarchies, any reporting or analysis done on the hierarchy may not match reporting or analysis done on mandatory hierarchies.</span></span>

## <a name="rules"></a><span data-ttu-id="1097b-125">规则</span><span class="sxs-lookup"><span data-stu-id="1097b-125">Rules</span></span>
 <span data-ttu-id="1097b-126">下列规则适用于（强制和非强制）的显式层次结构：</span><span class="sxs-lookup"><span data-stu-id="1097b-126">The following rules apply to explicit hierarchies (both mandatory and non-mandatory).</span></span>

-   <span data-ttu-id="1097b-127">每个叶成员只能在层次结构中包含一次。</span><span class="sxs-lookup"><span data-stu-id="1097b-127">Each leaf member can be included in the hierarchy only once.</span></span>

-   <span data-ttu-id="1097b-128">必须在层次结构中包含所有合并成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-128">All consolidated members must be included in a hierarchy.</span></span>

-   <span data-ttu-id="1097b-129">合并成员不能在多个显式层次结构中。</span><span class="sxs-lookup"><span data-stu-id="1097b-129">Consolidated members cannot be in more than one explicit hierarchy.</span></span>

-   <span data-ttu-id="1097b-130">层次结构树中的合并成员不要求其下面还包含叶成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-130">Consolidated members in the hierarchy tree do not have to contain leaf members underneath them.</span></span>

-   <span data-ttu-id="1097b-131">如果删除显式层次结构，将删除该层次结构中使用的所有合并成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-131">If you delete an explicit hierarchy, all consolidated members that were used in the hierarchy are deleted.</span></span>

-   <span data-ttu-id="1097b-132">如果删除显式层次结构中的合并成员，则将按该合并成员分组的所有叶成员移到根部。</span><span class="sxs-lookup"><span data-stu-id="1097b-132">If you delete a consolidated member that was in an explicit hierarchy, all leaf members that were grouped by that consolidated member are moved to the root.</span></span>

## <a name="explicit-hierarchies-versus-derived-hierarchies"></a><span data-ttu-id="1097b-133">显式层次结构与派生层次结构</span><span class="sxs-lookup"><span data-stu-id="1097b-133">Explicit Hierarchies versus Derived Hierarchies</span></span>
 <span data-ttu-id="1097b-134">下表显示显式层次结构与派生层次结构之间的一些区别。</span><span class="sxs-lookup"><span data-stu-id="1097b-134">The following table shows some of the differences between explicit and derived hierarchies.</span></span>

|<span data-ttu-id="1097b-135">显式层次结构</span><span class="sxs-lookup"><span data-stu-id="1097b-135">Explicit Hierarchies</span></span>|<span data-ttu-id="1097b-136">派生层次结构</span><span class="sxs-lookup"><span data-stu-id="1097b-136">Derived Hierarchies</span></span>|
|--------------------------|-------------------------|
|<span data-ttu-id="1097b-137">结构是由用户定义的</span><span class="sxs-lookup"><span data-stu-id="1097b-137">Structure is defined by the user</span></span>|<span data-ttu-id="1097b-138">结构是从基于域的属性间的关系派生的</span><span class="sxs-lookup"><span data-stu-id="1097b-138">Structure is derived from the relationships between domain-based attributes</span></span>|
|<span data-ttu-id="1097b-139">包含单个实体的成员</span><span class="sxs-lookup"><span data-stu-id="1097b-139">Contains members from a single entity</span></span>|<span data-ttu-id="1097b-140">包含多个实体的成员</span><span class="sxs-lookup"><span data-stu-id="1097b-140">Contains members from multiple entities</span></span>|
|<span data-ttu-id="1097b-141">使用合并成员对其他成员进行分组</span><span class="sxs-lookup"><span data-stu-id="1097b-141">Uses consolidated members to group other members</span></span>|<span data-ttu-id="1097b-142">使用来自一个实体的叶成员对其他实体的叶成员进行分组</span><span class="sxs-lookup"><span data-stu-id="1097b-142">Uses leaf members from one entity to group leaf members from another entity</span></span>|
|<span data-ttu-id="1097b-143">可以是不规则的</span><span class="sxs-lookup"><span data-stu-id="1097b-143">Can be ragged</span></span>|<span data-ttu-id="1097b-144">始终包含一致的级别数</span><span class="sxs-lookup"><span data-stu-id="1097b-144">Always contains a consistent number of levels</span></span>|

## <a name="explicit-hierarchy-example"></a><span data-ttu-id="1097b-145">显式层次结构示例</span><span class="sxs-lookup"><span data-stu-id="1097b-145">Explicit Hierarchy Example</span></span>
 <span data-ttu-id="1097b-146">在下面的示例中，Product 实体包含以下叶成员：BK-M101 {Mountain-100}、BK-M201 {Mountain-200}、BK-M301 {Mountain-300}、BK-R150 {Road-150}、BK-R450 {Road-450} 和 BK-R650 {Road-650}。</span><span class="sxs-lookup"><span data-stu-id="1097b-146">In the following example, the Product entity contains these leaf members: BK-M101 {Mountain-100}, BK-M201 {Mountain-200}, BK-M301 {Mountain-300}, BK-R150 {Road-150}, BK-R450 {Road-450}, and BK-R650 {Road-650}.</span></span>

 <span data-ttu-id="1097b-147">若要在特定的合并点汇总这些叶成员，您可以在 Product 实体中创建合并成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-147">To summarize these leaf members at specific consolidation points, you can create consolidated members in the Product entity.</span></span> <span data-ttu-id="1097b-148">在要汇总叶成员的层次结构树的级别中插入合并成员。</span><span class="sxs-lookup"><span data-stu-id="1097b-148">Insert the consolidated members at levels in the hierarchy tree where you want to summarize the leaf members.</span></span> <span data-ttu-id="1097b-149">对插入合并成员的位置没有限制，但是每个成员（叶成员或合并成员）只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="1097b-149">There is no limitation on where you insert your consolidated members; however, each member (leaf or consolidated) can be used only once.</span></span>

 <span data-ttu-id="1097b-150">![山地车显式层次结构示例](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "山地车显式层次结构示例")</span><span class="sxs-lookup"><span data-stu-id="1097b-150">![Mountain Bike Explicit Hierarchy Example](../../2014/master-data-services/media/mds-conc-explicit-hierarchy.gif "Mountain Bike Explicit Hierarchy Example")</span></span>

 <span data-ttu-id="1097b-151">合并成员可用于将任何级别的成员分组，叶成员和合并成员按您确定的顺序排序。</span><span class="sxs-lookup"><span data-stu-id="1097b-151">Consolidated members can be used to group members at any level, and leaf and consolidated members are sorted in the order you determine.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="1097b-152">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="1097b-152">Related Tasks</span></span>

|<span data-ttu-id="1097b-153">任务说明</span><span class="sxs-lookup"><span data-stu-id="1097b-153">Task Description</span></span>|<span data-ttu-id="1097b-154">主题</span><span class="sxs-lookup"><span data-stu-id="1097b-154">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="1097b-155">为显式层次结构和集合启用实体。</span><span class="sxs-lookup"><span data-stu-id="1097b-155">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="1097b-156">为显式层次结构和集合启用实体 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1097b-156">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="1097b-157">创建新的显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="1097b-157">Create a new explicit hierarchy.</span></span>|[<span data-ttu-id="1097b-158">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-158">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="1097b-159">更改现有显式层次结构的名称。</span><span class="sxs-lookup"><span data-stu-id="1097b-159">Change the name of an existing explicity hierarchy.</span></span>|[<span data-ttu-id="1097b-160">更改显式层次结构名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-160">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="1097b-161">删除现有显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="1097b-161">Delete an existing explicit hierarchy.</span></span>|[<span data-ttu-id="1097b-162">删除显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-162">Delete an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-explicit-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a><span data-ttu-id="1097b-163">相关内容</span><span class="sxs-lookup"><span data-stu-id="1097b-163">Related Content</span></span>

-   [<span data-ttu-id="1097b-164">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-164">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="1097b-165">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1097b-165">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)


