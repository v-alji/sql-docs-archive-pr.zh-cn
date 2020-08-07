---
title: 层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services]
- hierarchies [Master Data Services], about hierarchies
ms.assetid: 70dbb1fc-ead7-45be-9552-a45e3ccd8d21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 126a01c03134c6859426c09fda398408694795f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587881"
---
# <a name="hierarchies-master-data-services"></a><span data-ttu-id="d761c-102">层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-102">Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="d761c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，层次结构是一种树结构，您可以使用它：</span><span class="sxs-lookup"><span data-stu-id="d761c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a hierarchy is a tree structure that you can use to:</span></span>

-   <span data-ttu-id="d761c-104">将类似成员分组以便使结构组织得更好。</span><span class="sxs-lookup"><span data-stu-id="d761c-104">Group similar members for organizational purposes.</span></span>

-   <span data-ttu-id="d761c-105">合并和汇总成员以便进行报告和分析。</span><span class="sxs-lookup"><span data-stu-id="d761c-105">Consolidate and summarize members for reporting and analysis.</span></span>

## <a name="what-hierarchies-contain"></a><span data-ttu-id="d761c-106">层次结构包含的内容</span><span class="sxs-lookup"><span data-stu-id="d761c-106">What Hierarchies Contain</span></span>
 <span data-ttu-id="d761c-107">每个层次结构包含一个或多个实体的成员。</span><span class="sxs-lookup"><span data-stu-id="d761c-107">Each hierarchy contains members from one or more entities.</span></span> <span data-ttu-id="d761c-108">添加、更改或删除成员时，将更新所有层次结构。</span><span class="sxs-lookup"><span data-stu-id="d761c-108">When a member is added, changed, or deleted, all hierarchies are updated.</span></span> <span data-ttu-id="d761c-109">这可确保数据在所有层次结构中是准确的。</span><span class="sxs-lookup"><span data-stu-id="d761c-109">This ensures that the data is accurate in all hierarchies.</span></span> <span data-ttu-id="d761c-110">层次结构还有助于确保每个成员计入一次且只计入一次。</span><span class="sxs-lookup"><span data-stu-id="d761c-110">Hierarchies also help ensure that each member is counted once and only once.</span></span>

 <span data-ttu-id="d761c-111">若要创建成员子集的分组，请考虑使用集合。</span><span class="sxs-lookup"><span data-stu-id="d761c-111">If you want to create a grouping of a subset of members, consider using a collection.</span></span> <span data-ttu-id="d761c-112">有关详细信息，请参阅 [集合 (Master Data Services)](collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d761c-112">For more information, see [Collections &#40;Master Data Services&#41;](collections-master-data-services.md).</span></span>

## <a name="kinds-of-hierarchies"></a><span data-ttu-id="d761c-113">层次结构类型</span><span class="sxs-lookup"><span data-stu-id="d761c-113">Kinds of Hierarchies</span></span>
 <span data-ttu-id="d761c-114">可以创建多个层次结构，以不同的方式查看和组织您的成员。</span><span class="sxs-lookup"><span data-stu-id="d761c-114">You can create multiple hierarchies to view and organize your members in different ways.</span></span> <span data-ttu-id="d761c-115">您可以：</span><span class="sxs-lookup"><span data-stu-id="d761c-115">You can create:</span></span>

-   <span data-ttu-id="d761c-116">从单个实体创建不规则层次结构（称为显式层次结构）。</span><span class="sxs-lookup"><span data-stu-id="d761c-116">Ragged hierarchies from a single entity, which are called explicit hierarchies.</span></span> <span data-ttu-id="d761c-117">有关详细信息，请参阅 [显式层次结构 (Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d761c-117">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>

-   <span data-ttu-id="d761c-118">从多个实体创建基于级别的层次结构，该层次结构基于实体和其属性之间的现有关系（称为派生层次结构）。</span><span class="sxs-lookup"><span data-stu-id="d761c-118">Level-based hierarchies from multiple entities, based on the existing relationships between entities and their attributes, which are called derived hierarchies.</span></span> <span data-ttu-id="d761c-119">有关详细信息，请参阅 [派生层次结构 (Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d761c-119">For more information, see [Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="d761c-120">层次结构中的所有成员都必须在同一模型中。</span><span class="sxs-lookup"><span data-stu-id="d761c-120">All members in a hierarchy must be within the same model.</span></span>

## <a name="hierarchies-are-not-taxonomies"></a><span data-ttu-id="d761c-121">层次结构不是分类</span><span class="sxs-lookup"><span data-stu-id="d761c-121">Hierarchies Are Not Taxonomies</span></span>
 <span data-ttu-id="d761c-122">层次结构与分类不同。</span><span class="sxs-lookup"><span data-stu-id="d761c-122">A hierarchy is different from a taxonomy.</span></span> <span data-ttu-id="d761c-123">分类组织成员时一次处理多个属性，而层次结构组织成员时一次处理一个属性。</span><span class="sxs-lookup"><span data-stu-id="d761c-123">A taxonomy organizes members by multiple attributes at the same time, while a hierarchy organizes members by one attribute at a time.</span></span> <span data-ttu-id="d761c-124">分类可以多次包含同一成员，而层次结构只能包含成员一次。</span><span class="sxs-lookup"><span data-stu-id="d761c-124">A taxonomy can include the same member multiple times, while a hierarchy includes a member only once.</span></span>

 <span data-ttu-id="d761c-125">例如，同一自行车可以包含在一个分类中两次：一次由于它是红色的，一次由于它的规格为 38。</span><span class="sxs-lookup"><span data-stu-id="d761c-125">For example, the same bike can be included in a taxonomy twice: once because it's red, and once because it's a size 38.</span></span> <span data-ttu-id="d761c-126">在层次结构中，该自行车只能包含一次，因此您必须决定是依据颜色还是规格来显示它。</span><span class="sxs-lookup"><span data-stu-id="d761c-126">In a hierarchy, the bike is included only once, so you must decide whether to show it in relation to its color or its size.</span></span>

## <a name="hierarchy-example"></a><span data-ttu-id="d761c-127">层次结构示例</span><span class="sxs-lookup"><span data-stu-id="d761c-127">Hierarchy Example</span></span>
 <span data-ttu-id="d761c-128">在下面的示例中，product 成员按 subcategory 成员进行分组。</span><span class="sxs-lookup"><span data-stu-id="d761c-128">In the following example, product members are grouped by subcategory members.</span></span>

 <span data-ttu-id="d761c-129">![按子类别分组的层次结构示例](../../2014/master-data-services/media/mds-conc-hierarchy.gif "按子类别分组的层次结构示例")</span><span class="sxs-lookup"><span data-stu-id="d761c-129">![Hierarchy Grouped by Subcategory Example](../../2014/master-data-services/media/mds-conc-hierarchy.gif "Hierarchy Grouped by Subcategory Example")</span></span>

## <a name="related-tasks"></a><span data-ttu-id="d761c-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d761c-130">Related Tasks</span></span>

|<span data-ttu-id="d761c-131">任务说明</span><span class="sxs-lookup"><span data-stu-id="d761c-131">Task Description</span></span>|<span data-ttu-id="d761c-132">主题</span><span class="sxs-lookup"><span data-stu-id="d761c-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="d761c-133">为显式层次结构和集合启用实体。</span><span class="sxs-lookup"><span data-stu-id="d761c-133">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="d761c-134">为显式层次结构和集合启用实体 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d761c-134">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|
|<span data-ttu-id="d761c-135">创建显式层次结构。</span><span class="sxs-lookup"><span data-stu-id="d761c-135">Create a explicit hierarchy.</span></span>|[<span data-ttu-id="d761c-136">创建显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-136">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|<span data-ttu-id="d761c-137">创建派生层次结构。</span><span class="sxs-lookup"><span data-stu-id="d761c-137">Create a derived hierarchy.</span></span>|[<span data-ttu-id="d761c-138">创建派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-138">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="d761c-139">隐藏或删除现有派生层次结构中的级别。</span><span class="sxs-lookup"><span data-stu-id="d761c-139">Hide or delete levels in an existing derived hierarchy.</span></span>|[<span data-ttu-id="d761c-140">隐藏或删除派生层次结构中的级别 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-140">Hide or Delete Levels in a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="d761c-141">相关内容</span><span class="sxs-lookup"><span data-stu-id="d761c-141">Related Content</span></span>

-   [<span data-ttu-id="d761c-142">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-142">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)

-   [<span data-ttu-id="d761c-143">派生层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-143">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [<span data-ttu-id="d761c-144">递归层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-144">Recursive Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/recursive-hierarchies-master-data-services.md)

-   [<span data-ttu-id="d761c-145">具有显式顶端的派生层次结构 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d761c-145">Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)

-   [<span data-ttu-id="d761c-146">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d761c-146">Collections &#40;Master Data Services&#41;</span></span>](collections-master-data-services.md)


