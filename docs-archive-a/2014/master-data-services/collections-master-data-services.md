---
title: 集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services]
- collections [Master Data Services], about collections
ms.assetid: 5aa1d1e0-b4e5-4897-8e74-01dcf418df73
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce49c57aad5da52dabba32a0f3fb9b6f4f45b209
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689510"
---
# <a name="collections-master-data-services"></a><span data-ttu-id="cf48f-102">集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cf48f-102">Collections (Master Data Services)</span></span>
  <span data-ttu-id="cf48f-103">集合是一组来自单个实体的叶成员和合并成员。</span><span class="sxs-lookup"><span data-stu-id="cf48f-103">A collection is a group of leaf and consolidated members from a single entity.</span></span> <span data-ttu-id="cf48f-104">不需要完整层次结构并且想要查看不同的成员分组以便进行报告或分析时，或者需要创建分类时，使用集合。</span><span class="sxs-lookup"><span data-stu-id="cf48f-104">Use collections when you do not need a complete hierarchy and you want to view different groupings of members for reporting or analysis, or when you need to create a taxonomy.</span></span>  
  
## <a name="what-collections-contain"></a><span data-ttu-id="cf48f-105">集合包含的内容</span><span class="sxs-lookup"><span data-stu-id="cf48f-105">What Collections Contain</span></span>  
 <span data-ttu-id="cf48f-106">集合不限制可以包含的成员数或成员类型，只要这些成员在同一个实体中即可。</span><span class="sxs-lookup"><span data-stu-id="cf48f-106">Collections do not limit the number or type of members you can include, as long as the members are within the same entity.</span></span> <span data-ttu-id="cf48f-107">集合可以包含来自多个强制性显式层次结构和非强制性显式层次结构的叶成员和合并成员。</span><span class="sxs-lookup"><span data-stu-id="cf48f-107">A collection can contain leaf and consolidated members from multiple mandatory and non-mandatory explicit hierarchies.</span></span>  
  
 <span data-ttu-id="cf48f-108">创建集合时，创建的不是分层结构，而是成员的平面列表。</span><span class="sxs-lookup"><span data-stu-id="cf48f-108">When you create a collection, you are not creating a hierarchical structure; you are creating a flat list of members.</span></span> <span data-ttu-id="cf48f-109">从层次结构中选择某个节点并将其添加到集合时，您所选的合并成员是唯一添加到集合的成员。</span><span class="sxs-lookup"><span data-stu-id="cf48f-109">When you select a node from a hierarchy and add it to the collection, the consolidated member you selected is the only member added to the collection.</span></span>  
  
 <span data-ttu-id="cf48f-110">集合还可以包含其他集合。</span><span class="sxs-lookup"><span data-stu-id="cf48f-110">A collection can also contain other collections.</span></span> <span data-ttu-id="cf48f-111">可以使用集合的集合来创建分类。</span><span class="sxs-lookup"><span data-stu-id="cf48f-111">You can use collections of collections to create taxonomies.</span></span>  
  
 <span data-ttu-id="cf48f-112">创建集合时，您将自动作为所有者列出。</span><span class="sxs-lookup"><span data-stu-id="cf48f-112">When you create a collection you are automatically listed as the owner.</span></span> <span data-ttu-id="cf48f-113">如果您是管理员，则可以根据需要为您的集合创建其他属性。</span><span class="sxs-lookup"><span data-stu-id="cf48f-113">If you are an administrator, you can create other attributes for your collection as needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf48f-114">在创建集合前，必须为显式层次结构启用了实体。</span><span class="sxs-lookup"><span data-stu-id="cf48f-114">Before you can create a collection, the entity must be enabled for explicit hierarchies.</span></span> <span data-ttu-id="cf48f-115">有关详细信息，请参阅为[显式层次结构和集合启用实体 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cf48f-115">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
## <a name="subscription-views-for-collections"></a><span data-ttu-id="cf48f-116">集合的订阅视图</span><span class="sxs-lookup"><span data-stu-id="cf48f-116">Subscription Views for Collections</span></span>  
 <span data-ttu-id="cf48f-117">显示集合的订阅视图有两种。</span><span class="sxs-lookup"><span data-stu-id="cf48f-117">There are two types of subscription views that show collections.</span></span> <span data-ttu-id="cf48f-118">**集合属性** 格式显示集合列表以及与集合相关的任何属性（如说明或所有者）。</span><span class="sxs-lookup"><span data-stu-id="cf48f-118">The **Collection attributes** format shows a list of collections and any attributes related to the collections (like description or owner).</span></span> <span data-ttu-id="cf48f-119">**“集合”** 格式显示所有集合中的所有成员以及每个成员权重和排序顺序。</span><span class="sxs-lookup"><span data-stu-id="cf48f-119">The **Collections** format shows all members in all collections, as well as each members weight and sort order.</span></span> <span data-ttu-id="cf48f-120">有关详细信息，请参阅将[数据导出 &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cf48f-120">For more information, see [Exporting Data &#40;Master Data Services&#41;](overview-exporting-data-master-data-services.md).</span></span>  
  
 <span data-ttu-id="cf48f-121">如果为集合中的特定成员设置了权重值，则这些值在相关订阅视图中可用。</span><span class="sxs-lookup"><span data-stu-id="cf48f-121">If you set weight values for specific members in a collection, these values are available in related subscription views.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cf48f-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="cf48f-122">Related Tasks</span></span>  
  
|<span data-ttu-id="cf48f-123">任务说明</span><span class="sxs-lookup"><span data-stu-id="cf48f-123">Task Description</span></span>|<span data-ttu-id="cf48f-124">主题</span><span class="sxs-lookup"><span data-stu-id="cf48f-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="cf48f-125">为显式层次结构和集合启用实体。</span><span class="sxs-lookup"><span data-stu-id="cf48f-125">Enable an entity for explicit hierarchies and collections.</span></span>|[<span data-ttu-id="cf48f-126">为显式层次结构和集合启用实体 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cf48f-126">Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;</span></span>](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)|  
|<span data-ttu-id="cf48f-127">创建新集合。</span><span class="sxs-lookup"><span data-stu-id="cf48f-127">Create a new collection.</span></span>|[<span data-ttu-id="cf48f-128">创建集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cf48f-128">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)|  
|<span data-ttu-id="cf48f-129">向现有集合添加成员。</span><span class="sxs-lookup"><span data-stu-id="cf48f-129">Add members to an existing collection.</span></span>|[<span data-ttu-id="cf48f-130">将成员添加到集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cf48f-130">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="cf48f-131">相关内容</span><span class="sxs-lookup"><span data-stu-id="cf48f-131">Related Content</span></span>  
  
-   [<span data-ttu-id="cf48f-132">显式层次结构 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cf48f-132">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [<span data-ttu-id="cf48f-133">将数据导出 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cf48f-133">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
