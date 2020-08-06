---
title: 成员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services]
- consolidated members [Master Data Services]
- consolidated members [Master Data Services], about consolidated members
- members [Master Data Services], about members
- leaf members [Master Data Services], about leaf members
- members [Master Data Services]
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 89d2edb21b58575dffc21d9a6470171251889cc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688982"
---
# <a name="members-master-data-services"></a><span data-ttu-id="ce002-102">成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-102">Members (Master Data Services)</span></span>
  <span data-ttu-id="ce002-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，成员是物理主数据。</span><span class="sxs-lookup"><span data-stu-id="ce002-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], members are the physical master data.</span></span> <span data-ttu-id="ce002-104">例如，成员可以是 Product 实体中的 Road-150 自行车或 Customer 实体中的特定客户。</span><span class="sxs-lookup"><span data-stu-id="ce002-104">For example, a member can be a Road-150 bike in a Product entity or a specific customer in a Customer entity.</span></span>

## <a name="how-members-relate-to-other-model-objects"></a><span data-ttu-id="ce002-105">成员如何与其他模型对象关联</span><span class="sxs-lookup"><span data-stu-id="ce002-105">How Members Relate to Other Model Objects</span></span>
 <span data-ttu-id="ce002-106">可以将成员看作一个表中的行。</span><span class="sxs-lookup"><span data-stu-id="ce002-106">You can think of members as rows in a table.</span></span> <span data-ttu-id="ce002-107">相关成员包含在一个实体中，每个成员由属性值进行定义。</span><span class="sxs-lookup"><span data-stu-id="ce002-107">Related members are contained in an entity, and each member is defined by attribute values.</span></span>

 <span data-ttu-id="ce002-108">在此示例中，该表表示实体，表中的行表示成员，表中的列表示属性。</span><span class="sxs-lookup"><span data-stu-id="ce002-108">In this example, the table represents an entity, the rows in the table represent members, and the columns in the table represent attributes.</span></span> <span data-ttu-id="ce002-109">每个单元表示特定成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="ce002-109">Each cell represents an attribute value for a specific member.</span></span>

 <span data-ttu-id="ce002-110">![表示为表的 Master Data Services 实体](../../2014/master-data-services/media/mds-conc-entity-table.gif "表示为表的 Master Data Services 实体")</span><span class="sxs-lookup"><span data-stu-id="ce002-110">![Master Data Services Entity Represented as Table](../../2014/master-data-services/media/mds-conc-entity-table.gif "Master Data Services Entity Represented as Table")</span></span>

## <a name="member-types"></a><span data-ttu-id="ce002-111">成员类型</span><span class="sxs-lookup"><span data-stu-id="ce002-111">Member Types</span></span>
 <span data-ttu-id="ce002-112">存在三种类型的成员：叶成员、合并成员和集合成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-112">There are three types of members: leaf members, consolidated members, and collection members.</span></span>

 <span data-ttu-id="ce002-113">叶成员是实体中的默认成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-113">Leaf members are the default members in an entity.</span></span>

-   <span data-ttu-id="ce002-114">在派生层次结构中，叶成员是唯一的成员类型。</span><span class="sxs-lookup"><span data-stu-id="ce002-114">In derived hierarchies, leaf members are the only type of member.</span></span> <span data-ttu-id="ce002-115">来自一个实体的叶成员用作来自其他实体的叶成员的父级。</span><span class="sxs-lookup"><span data-stu-id="ce002-115">Leaf members from one entity are used as parents of leaf members from another entity.</span></span>

-   <span data-ttu-id="ce002-116">在显式层次结构中，叶成员位于最低级别并且不能具有子级。</span><span class="sxs-lookup"><span data-stu-id="ce002-116">In explicit hierarchies, leaf members are the lowest level and cannot have children.</span></span>

 <span data-ttu-id="ce002-117">只有为实体启用显式层次结构和集合时，合并成员才存在。</span><span class="sxs-lookup"><span data-stu-id="ce002-117">Consolidated members exist only when explicit hierarchies and collections are enabled for the entity.</span></span>

-   <span data-ttu-id="ce002-118">派生层次结构不包含合并成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-118">Derived hierarchies do not contain consolidated members.</span></span>

-   <span data-ttu-id="ce002-119">在显式层次结构中，合并成员可以是层次结构中其他成员的父级，也可以是子级。</span><span class="sxs-lookup"><span data-stu-id="ce002-119">In explicit hierarchies, consolidated members can be parents of other members within the hierarchy, or they can be children.</span></span>

## <a name="use-hierarchies-and-collections-to-organize-members"></a><span data-ttu-id="ce002-120">使用层次结构和集合组织成员</span><span class="sxs-lookup"><span data-stu-id="ce002-120">Use Hierarchies and Collections to Organize Members</span></span>
 <span data-ttu-id="ce002-121">层次结构和集合可用于分组成员便于报告或分析。</span><span class="sxs-lookup"><span data-stu-id="ce002-121">Hierarchies and collections can be used to group members for reporting or analysis.</span></span> <span data-ttu-id="ce002-122">有关详细信息，请参阅 [层次结构 (Master Data Services)](hierarchies-master-data-services.md) 和 [集合 (Master Data Services)](../../2014/master-data-services/collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ce002-122">For more information, see [Hierarchies &#40;Master Data Services&#41;](hierarchies-master-data-services.md) and [Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md).</span></span>

## <a name="member-example"></a><span data-ttu-id="ce002-123">成员示例</span><span class="sxs-lookup"><span data-stu-id="ce002-123">Member Example</span></span>
 <span data-ttu-id="ce002-124">在下面的示例中，每个成员均包含 Name、Code、Subcategory、StandardCost、ListPrice 和 FilePhoto 属性值。</span><span class="sxs-lookup"><span data-stu-id="ce002-124">In the following example, each member is made up of a Name, Code, Subcategory, StandardCost, ListPrice, and FilePhoto attribute value.</span></span>

 <span data-ttu-id="ce002-125">![自行车产品实体表](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "自行车产品实体表")</span><span class="sxs-lookup"><span data-stu-id="ce002-125">![Bike Product Entity Table](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Bike Product Entity Table")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="ce002-126">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ce002-126">Related Tasks</span></span>

|<span data-ttu-id="ce002-127">任务说明</span><span class="sxs-lookup"><span data-stu-id="ce002-127">Task Description</span></span>|<span data-ttu-id="ce002-128">主题</span><span class="sxs-lookup"><span data-stu-id="ce002-128">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="ce002-129">创建新的叶成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-129">Create a new leaf member.</span></span>|[<span data-ttu-id="ce002-130">创建叶成员 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ce002-130">Create a Leaf Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)|
|<span data-ttu-id="ce002-131">创建新的合并成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-131">Create a new consolidated member.</span></span>|[<span data-ttu-id="ce002-132">创建合并成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-132">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)|
|<span data-ttu-id="ce002-133">删除现有成员或集合。</span><span class="sxs-lookup"><span data-stu-id="ce002-133">Delete an existing member or collection.</span></span>|[<span data-ttu-id="ce002-134">删除成员或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-134">Delete a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="ce002-135">重新激活已删除的成员或集合。</span><span class="sxs-lookup"><span data-stu-id="ce002-135">Reactivate a deleted member or collection.</span></span>|[<span data-ttu-id="ce002-136">重新激活成员或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-136">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)|
|<span data-ttu-id="ce002-137">更新成员的属性值。</span><span class="sxs-lookup"><span data-stu-id="ce002-137">Update the attribute values of a member.</span></span>|[<span data-ttu-id="ce002-138">更改属性类型（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="ce002-138">Change the Attribute Type &#40;MDS Add-in for Excel&#41;</span></span>](microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|
|<span data-ttu-id="ce002-139">在层次结构中移动成员。</span><span class="sxs-lookup"><span data-stu-id="ce002-139">Move members within a hierarchy.</span></span>|[<span data-ttu-id="ce002-140">在层次结构中移动 &#40;Master Data Services 的成员&#41;</span><span class="sxs-lookup"><span data-stu-id="ce002-140">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="ce002-141">相关内容</span><span class="sxs-lookup"><span data-stu-id="ce002-141">Related Content</span></span>

-   [<span data-ttu-id="ce002-142">Master Data Services 概述</span><span class="sxs-lookup"><span data-stu-id="ce002-142">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)

-   [<span data-ttu-id="ce002-143">实体 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-143">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)

-   [<span data-ttu-id="ce002-144">属性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-144">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)

-   [<span data-ttu-id="ce002-145">层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-145">Hierarchies &#40;Master Data Services&#41;</span></span>](hierarchies-master-data-services.md)

-   [<span data-ttu-id="ce002-146">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-146">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)

-   [<span data-ttu-id="ce002-147">叶权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-147">Leaf Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/leaf-permissions-master-data-services.md)

-   [<span data-ttu-id="ce002-148">&#40;Master Data Services 的合并权限&#41;</span><span class="sxs-lookup"><span data-stu-id="ce002-148">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)

-   [<span data-ttu-id="ce002-149">Filter 运算符 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ce002-149">Filter Operators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/filter-operators-master-data-services.md)


