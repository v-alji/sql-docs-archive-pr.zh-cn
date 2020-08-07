---
title: 如何确定权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ea3306b772224bc8602659c7e17e8dc1634f0d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587877"
---
# <a name="how-permissions-are-determined-master-data-services"></a><span data-ttu-id="89515-102">如何确定权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="89515-102">How Permissions Are Determined (Master Data Services)</span></span>
  <span data-ttu-id="89515-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，配置安全性的最简单方式是向用户所属的组分配模型对象权限。</span><span class="sxs-lookup"><span data-stu-id="89515-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], the simplest way to configure security is to assign model object permissions to a group that the user is a member of.</span></span>

 <span data-ttu-id="89515-104">在以下情况下安全设置变得较为复杂：</span><span class="sxs-lookup"><span data-stu-id="89515-104">Security becomes more complex when:</span></span>

-   <span data-ttu-id="89515-105">同时分配了模型对象权限和层次结构成员权限。</span><span class="sxs-lookup"><span data-stu-id="89515-105">Both model object and hierarchy member permissions are assigned.</span></span>

-   <span data-ttu-id="89515-106">用户属于多个组，且同时向该用户和多个组分配了权限。</span><span class="sxs-lookup"><span data-stu-id="89515-106">The user belongs to groups and permission is assigned to both the user and groups.</span></span>

-   <span data-ttu-id="89515-107">用户属于多个组，而且向多个组分配了权限。</span><span class="sxs-lookup"><span data-stu-id="89515-107">The user belongs to groups and permission is assigned to multiple groups.</span></span>

## <a name="permissions-assigned-to-a-single-group-or-user"></a><span data-ttu-id="89515-108">向单个组或用户分配了权限</span><span class="sxs-lookup"><span data-stu-id="89515-108">Permissions assigned to a single group or user</span></span>
 <span data-ttu-id="89515-109">如果向单个组或用户分配了权限，将基于以下工作流确定权限。</span><span class="sxs-lookup"><span data-stu-id="89515-109">If you assign permissions to a single group or user, permissions are determined based on the following workflow.</span></span>

 <span data-ttu-id="89515-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span><span class="sxs-lookup"><span data-stu-id="89515-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span></span>

### <a name="step-1-effective-attribute-permissions-are-determined"></a><span data-ttu-id="89515-111">步骤 1：确定有效属性权限。</span><span class="sxs-lookup"><span data-stu-id="89515-111">Step 1: Effective attribute permissions are determined.</span></span>
 <span data-ttu-id="89515-112">下面的列表说明如何确定有效属性权限：</span><span class="sxs-lookup"><span data-stu-id="89515-112">The following list describes how effective attribute permissions are determined:</span></span>

-   <span data-ttu-id="89515-113">分配给模型对象的权限确定用户可以访问哪些属性。</span><span class="sxs-lookup"><span data-stu-id="89515-113">Permissions assigned to model objects determine which attributes a user can access.</span></span>

-   <span data-ttu-id="89515-114">所有模型对象都自动继承模型结构中较高级别上最近对象的权限。</span><span class="sxs-lookup"><span data-stu-id="89515-114">All model objects automatically inherit permission from the closest object at a higher level in the model structure.</span></span>

-   <span data-ttu-id="89515-115">与该实体同级的所有对象都被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-115">Any objects at the same level as the entity are implicitly denied.</span></span>

-   <span data-ttu-id="89515-116">较高级别上的所有对象被授予导航访问权限。</span><span class="sxs-lookup"><span data-stu-id="89515-116">Any objects at a higher level are given navigational access.</span></span> <span data-ttu-id="89515-117">有关导航访问的详细信息，请参阅[导航访问 &#40;Master Data Services&#41;](navigational-access-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="89515-117">For more information about navigational access, see [Navigational Access &#40;Master Data Services&#41;](navigational-access-master-data-services.md).</span></span>

 <span data-ttu-id="89515-118">在此示例中，为实体分配了**只读**权限，并且该权限由该实体的属性（位于模型结构中较低级别）继承。</span><span class="sxs-lookup"><span data-stu-id="89515-118">In this example, **Read-only** permission is assigned to an entity and that permission is inherited by its attribute, which is at a lower level in the model structure.</span></span> <span data-ttu-id="89515-119">模型提供对此实体及其属性的导航访问权限。</span><span class="sxs-lookup"><span data-stu-id="89515-119">The model provides navigational access to this entity and its attribute.</span></span> <span data-ttu-id="89515-120">模型中的另一实体未分配显式权限，并且未继承任何权限，所以被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-120">The other entity in the model has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="89515-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="89515-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>

### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a><span data-ttu-id="89515-122">步骤 2：如果分配了层次结构成员权限，则需要确定有效的成员权限。</span><span class="sxs-lookup"><span data-stu-id="89515-122">Step 2: If hierarchy member permissions are assigned, effective member permissions are determined.</span></span>
 <span data-ttu-id="89515-123">下面的列表说明如何确定有效的层次结构成员权限：</span><span class="sxs-lookup"><span data-stu-id="89515-123">The following list describes how effective hierarchy member permissions are determined:</span></span>

-   <span data-ttu-id="89515-124">分配给层次结构节点的权限确定用户可以访问哪些成员。</span><span class="sxs-lookup"><span data-stu-id="89515-124">Permissions assigned to hierarchy nodes determine which members a user can access.</span></span>

-   <span data-ttu-id="89515-125">层次结构中的所有节点都自动继承层次结构中较高级别上最近对象的权限。</span><span class="sxs-lookup"><span data-stu-id="89515-125">All nodes in a hierarchy automatically inherit permission from the closest object at a higher level in the hierarchy structure.</span></span>

-   <span data-ttu-id="89515-126">同级的所有节点都被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-126">Any nodes at the same level are implicitly denied.</span></span>

-   <span data-ttu-id="89515-127">较高级别上未分配权限的所有节点都被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-127">Any nodes at higher levels that do not have permissions assigned are implicitly denied.</span></span>

 <span data-ttu-id="89515-128">在此示例中，**只读**权限分配给层次结构的一个节点，并且该权限由层次结构中较低级别的节点继承。</span><span class="sxs-lookup"><span data-stu-id="89515-128">In this example, **Read-only** permission is assigned to one node of the hierarchy and that permission is inherited by a node at a lower level in the hierarchy structure.</span></span> <span data-ttu-id="89515-129">没有向根分配权限，所以根被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-129">The root has no permission assigned, so it is implicitly denied.</span></span> <span data-ttu-id="89515-130">层次结构中的另一节点未分配显式权限，并且未继承任何权限，所以被隐式拒绝。</span><span class="sxs-lookup"><span data-stu-id="89515-130">The other node in the hierarchy structure has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="89515-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="89515-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span></span>

### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a><span data-ttu-id="89515-132">步骤 3：确定属性权限与成员权限的交集。</span><span class="sxs-lookup"><span data-stu-id="89515-132">Step 3: The intersection of attribute and member permissions is determined.</span></span>
 <span data-ttu-id="89515-133">如果有效属性权限不同于有效成员权限，必须为每个单独的属性值确定权限。</span><span class="sxs-lookup"><span data-stu-id="89515-133">If the effective attribute permissions are different than the effective member permissions, permissions must be determined for each individual attribute value.</span></span> <span data-ttu-id="89515-134">有关详细信息，请参阅 [重叠的模型和成员权限 (Master Data Services)](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="89515-134">For more information, see [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).</span></span>

## <a name="permissions-assigned-to-multiple-groups"></a><span data-ttu-id="89515-135">向多个组分配了权限</span><span class="sxs-lookup"><span data-stu-id="89515-135">Permissions assigned to multiple groups</span></span>
 <span data-ttu-id="89515-136">如果用户属于一个或多个组并且同时向用户和组分配了权限，则工作流会变得更为复杂。</span><span class="sxs-lookup"><span data-stu-id="89515-136">If a user belongs to one or more groups and permissions are assigned to both the user and the groups, the workflow becomes more complex.</span></span>

 <span data-ttu-id="89515-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span><span class="sxs-lookup"><span data-stu-id="89515-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span></span>

 <span data-ttu-id="89515-138">在这种情况下，对模型对象权限和层次结构成员权限进行比较之前，必须先解决重叠的用户和组权限。</span><span class="sxs-lookup"><span data-stu-id="89515-138">In this case, overlapping user and group permissions must be resolved before model object and hierarchy member permissions can be compared.</span></span> <span data-ttu-id="89515-139">有关详细信息，请参阅 [重叠的用户和组权限 (Master Data Services)](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="89515-139">For more information, see [Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89515-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89515-140">See Also</span></span>
 <span data-ttu-id="89515-141">[重叠的用户和组权限 &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [重叠模型和成员权限 &#40;Master Data Services](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="89515-141">[Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span></span>


