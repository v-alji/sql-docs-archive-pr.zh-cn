---
title: 复制发布模型概述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a6b6bd555cf87a8dcb334db2c44e17ed99aa845d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587352"
---
# <a name="replication-publishing-model-overview"></a><span data-ttu-id="14c2f-102">复制发布模型概述</span><span class="sxs-lookup"><span data-stu-id="14c2f-102">Replication Publishing Model Overview</span></span>
  <span data-ttu-id="14c2f-103">复制使用出版业术语表示复制拓扑中的组件，其中包括发布服务器、分发服务器、订阅服务器、发布、项目和订阅。</span><span class="sxs-lookup"><span data-stu-id="14c2f-103">Replication uses a publishing industry metaphor to represent the components in a replication topology, which include Publisher, Distributor, Subscribers, publications, articles, and subscriptions.</span></span> <span data-ttu-id="14c2f-104">可借助杂志的概念来帮助理解 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制：</span><span class="sxs-lookup"><span data-stu-id="14c2f-104">It is helpful to think of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication in terms of a magazine:</span></span>

-   <span data-ttu-id="14c2f-105">杂志出版商（发布服务器）生产一种或多种刊物（发布）</span><span class="sxs-lookup"><span data-stu-id="14c2f-105">A magazine publisher produces one or more publications</span></span>

-   <span data-ttu-id="14c2f-106">刊物（发布）包含文章（项目）</span><span class="sxs-lookup"><span data-stu-id="14c2f-106">A publication contains articles</span></span>

-   <span data-ttu-id="14c2f-107">出版商（发布服务器）可以直接发行（分发）杂志，也可以使用发行商（分发服务器）</span><span class="sxs-lookup"><span data-stu-id="14c2f-107">The publisher either distributes the magazine directly or uses a distributor</span></span>

-   <span data-ttu-id="14c2f-108">订阅者（订阅服务器）接收订阅的刊物（发布）</span><span class="sxs-lookup"><span data-stu-id="14c2f-108">Subscribers receive publications to which they have subscribed</span></span>

 <span data-ttu-id="14c2f-109">虽然杂志术语有助于理解复制，但重要的是要注意到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 复制包含有这套术语未予以表述的功能，尤其是订阅服务器进行更新的功能以及发布服务器将增量更改发送到发布中的项目的功能。</span><span class="sxs-lookup"><span data-stu-id="14c2f-109">Although the magazine metaphor is useful for understanding replication, it is important to note that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication includes functionality that is not represented in this metaphor, particularly the ability for a Subscriber to make updates and for a Publisher to send out incremental changes to the articles in a publication.</span></span>

 <span data-ttu-id="14c2f-110">“复制拓扑”  定义了服务器和数据副本间的关系，并阐明了决定数据如何在服务器之间流动的逻辑。</span><span class="sxs-lookup"><span data-stu-id="14c2f-110">A *replication topology* defines the relationship between servers and copies of data and clarifies the logic that determines how data flows between servers.</span></span> <span data-ttu-id="14c2f-111">有若干复制进程（称为“代理” ）负责在发布服务器和订阅服务器之间复制和移动数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-111">There are several replication processes (referred to as *agents*) that are responsible for copying and moving data between the Publisher and Subscribers.</span></span> <span data-ttu-id="14c2f-112">下图为复制中所涉及的组件和进程的概述。</span><span class="sxs-lookup"><span data-stu-id="14c2f-112">The following illustration is an overview of the components and processes involved in replication.</span></span>

 <span data-ttu-id="14c2f-113">![复制组件和数据流](../media/replintro1.gif "复制组件和数据流")</span><span class="sxs-lookup"><span data-stu-id="14c2f-113">![Replication components and data flow](../media/replintro1.gif "Replication components and data flow")</span></span>

## <a name="publisher"></a><span data-ttu-id="14c2f-114">发布者</span><span class="sxs-lookup"><span data-stu-id="14c2f-114">Publisher</span></span>
 <span data-ttu-id="14c2f-115">发布服务器是一种数据库实例，它通过复制向其他位置提供数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-115">The Publisher is a database instance that makes data available to other locations through replication.</span></span> <span data-ttu-id="14c2f-116">发布服务器可以有一个或多个发布，每个发布定义一组要复制的具有逻辑关系的对象和数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-116">The Publisher can have one or more publications, each defining a logically related set of objects and data to replicate.</span></span>

## <a name="distributor"></a><span data-ttu-id="14c2f-117">分发服务器</span><span class="sxs-lookup"><span data-stu-id="14c2f-117">Distributor</span></span>
 <span data-ttu-id="14c2f-118">分发服务器也是一种数据库实例，它起着存储区的作用，用于复制与一个或多个发布服务器相关联的特定数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-118">The Distributor is a database instance that acts as a store for replication specific data associated with one or more Publishers.</span></span> <span data-ttu-id="14c2f-119">每个发布服务器都与分发服务器中的单个数据库（称作分发数据库）相关联。</span><span class="sxs-lookup"><span data-stu-id="14c2f-119">Each Publisher is associated with a single database (known as a distribution database) at the Distributor.</span></span> <span data-ttu-id="14c2f-120">分发数据库存储复制状态数据和有关发布的元数据，并且在某些情况下为从发布服务器向订阅服务器移动的数据起着排队的作用。</span><span class="sxs-lookup"><span data-stu-id="14c2f-120">The distribution database stores replication status data, metadata about the publication, and, in some cases, acts as a queue for data moving from the Publisher to the Subscribers.</span></span> <span data-ttu-id="14c2f-121">在很多情况下，一个数据库服务器实例充当发布服务器和分发服务器两个角色。</span><span class="sxs-lookup"><span data-stu-id="14c2f-121">In many cases, a single database server instance acts as both the Publisher and the Distributor.</span></span> <span data-ttu-id="14c2f-122">这称为“本地分发服务器” 。</span><span class="sxs-lookup"><span data-stu-id="14c2f-122">This is known as a *local Distributor*.</span></span> <span data-ttu-id="14c2f-123">当发布服务器和分发服务器按各自的数据库服务器实例配置时，把分发服务器称为“远程分发服务器” 。</span><span class="sxs-lookup"><span data-stu-id="14c2f-123">When the Publisher and the Distributor are configured on separate database server instances, the Distributor is known as a *remote Distributor*.</span></span>

## <a name="subscribers"></a><span data-ttu-id="14c2f-124">订阅服务器</span><span class="sxs-lookup"><span data-stu-id="14c2f-124">Subscribers</span></span>
 <span data-ttu-id="14c2f-125">订阅服务器是接收复制数据的数据库实例。</span><span class="sxs-lookup"><span data-stu-id="14c2f-125">A Subscriber is a database instance that receives replicated data.</span></span> <span data-ttu-id="14c2f-126">订阅服务器可以接收来自多个发布服务器和发布的数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-126">A Subscriber can receive data from multiple Publishers and publications.</span></span> <span data-ttu-id="14c2f-127">根据所选的复制类型，订阅服务器还可以将数据更改传递回发布服务器或者将数据重新发布到其他订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="14c2f-127">Depending on the type of replication chosen, the Subscriber can also pass data changes back to the Publisher or republish the data to other Subscribers.</span></span>

## <a name="article"></a><span data-ttu-id="14c2f-128">项目</span><span class="sxs-lookup"><span data-stu-id="14c2f-128">Article</span></span>
 <span data-ttu-id="14c2f-129">项目用于标识发布中包含的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="14c2f-129">An article identifies a database object that is included in a publication.</span></span> <span data-ttu-id="14c2f-130">一次发布可以包含不同类型的项目，包括表、视图、存储过程和其他对象。</span><span class="sxs-lookup"><span data-stu-id="14c2f-130">A publication can contain different types of articles, including tables, views, stored procedures, and other objects.</span></span> <span data-ttu-id="14c2f-131">当把表作为项目发布时，可以用筛选器限制发送到订阅服务器的数据的列和行。</span><span class="sxs-lookup"><span data-stu-id="14c2f-131">When tables are published as articles, filters can be used to restrict the columns and rows of the data sent to Subscribers.</span></span>

## <a name="publication"></a><span data-ttu-id="14c2f-132">发布</span><span class="sxs-lookup"><span data-stu-id="14c2f-132">Publication</span></span>
 <span data-ttu-id="14c2f-133">发布是一个数据库中的一个或多个项目的集合。</span><span class="sxs-lookup"><span data-stu-id="14c2f-133">A publication is a collection of one or more articles from one database.</span></span> <span data-ttu-id="14c2f-134">将多个项目分组成一个发布，使得更便于指定一组作为一个单元复制的、具有逻辑关系的数据库对象和数据。</span><span class="sxs-lookup"><span data-stu-id="14c2f-134">The grouping of multiple articles into a publication makes it easier to specify a logically related set of database objects and data that are replicated as a unit.</span></span>

## <a name="subscription"></a><span data-ttu-id="14c2f-135">订阅</span><span class="sxs-lookup"><span data-stu-id="14c2f-135">Subscription</span></span>
 <span data-ttu-id="14c2f-136">订阅是把发布副本传递到订阅服务器的请求。</span><span class="sxs-lookup"><span data-stu-id="14c2f-136">A subscription is a request for a copy of a publication to be delivered to a Subscriber.</span></span> <span data-ttu-id="14c2f-137">订阅定义将接收的发布和接收的时间、地点。</span><span class="sxs-lookup"><span data-stu-id="14c2f-137">The subscription defines what publication will be received, where, and when.</span></span> <span data-ttu-id="14c2f-138">有两种类型的订阅：推送订阅和请求订阅。</span><span class="sxs-lookup"><span data-stu-id="14c2f-138">There are two types of subscriptions: push and pull.</span></span> <span data-ttu-id="14c2f-139">有关推送订阅和请求订阅的详细信息，请参阅[订阅发布](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="14c2f-139">For more information about push and pull subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14c2f-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14c2f-140">See Also</span></span>
 <span data-ttu-id="14c2f-141">[复制代理概述](../agents/replication-agents-overview.md)[复制类型](../types-of-replication.md)[为 AlwaysOn 可用性组 (SQL Server) ](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [维护 AlwaysOn 发布数据库](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14c2f-141">[Replication Agents Overview](../agents/replication-agents-overview.md) [Types of Replication](../types-of-replication.md) [Configure Replication for AlwaysOn Availability Groups (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)</span></span>


