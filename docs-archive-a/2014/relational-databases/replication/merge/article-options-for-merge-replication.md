---
title: 合并复制的项目选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], article options
- articles [SQL Server replication], merge replication options
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d4f9e6391962d5755983322073f738ba84f02633
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576704"
---
# <a name="article-options-for-merge-replication"></a><span data-ttu-id="a17cf-102">合并复制的项目选项</span><span class="sxs-lookup"><span data-stu-id="a17cf-102">Article Options for Merge Replication</span></span>
  <span data-ttu-id="a17cf-103">有许多用于合并表项目的选项，可以使用这些选项自定义复制行为以满足应用程序的需要。</span><span class="sxs-lookup"><span data-stu-id="a17cf-103">There are many options for merge table articles that enable you to customize replication behavior to the needs of your applications.</span></span> <span data-ttu-id="a17cf-104">使用合并复制可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a17cf-104">By using merge replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="a17cf-105">使用行筛选器、联接筛选器和列筛选器。</span><span class="sxs-lookup"><span data-stu-id="a17cf-105">Use row filters, join filters, and column filters.</span></span> <span data-ttu-id="a17cf-106">通过筛选表项目，可以为要发布的数据创建分区。</span><span class="sxs-lookup"><span data-stu-id="a17cf-106">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="a17cf-107">有关详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-107">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="a17cf-108">指定是否将订阅服务器上的更改上载到发布服务器。</span><span class="sxs-lookup"><span data-stu-id="a17cf-108">Specify whether changes at the Subscriber are uploaded to the Publisher.</span></span> <span data-ttu-id="a17cf-109">对于其中部分或全部数据在订阅服务器上应为只读的应用程序，仅用于下载的项目提供性能收益。</span><span class="sxs-lookup"><span data-stu-id="a17cf-109">For applications in which some or all data should be read-only at the Subscriber, download-only articles provide a performance benefit.</span></span> <span data-ttu-id="a17cf-110">有关详细信息，请参阅[使用仅下载项目优化合并复制性能](optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-110">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
-   <span data-ttu-id="a17cf-111">指定复制触发器和系统表不能跟踪一个或多个项目的删除操作。</span><span class="sxs-lookup"><span data-stu-id="a17cf-111">Specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="a17cf-112">此选项在许多应用方案中都非常有用。</span><span class="sxs-lookup"><span data-stu-id="a17cf-112">This option can be useful in many application scenarios.</span></span> <span data-ttu-id="a17cf-113">其中包括那些使用不需要复制的批处理删除操作的应用方案。</span><span class="sxs-lookup"><span data-stu-id="a17cf-113">These include scenarios that use batch deletes that do not need to be replicated.</span></span> <span data-ttu-id="a17cf-114">有关详细信息，请参阅[使用条件性删除跟踪优化合并复制性能](optimize-merge-replication-performance-with-conditional-delete-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-114">For more information, see [Optimize Merge Replication Performance with Conditional Delete Tracking](optimize-merge-replication-performance-with-conditional-delete-tracking.md).</span></span>  
  
-   <span data-ttu-id="a17cf-115">指定项目的处理顺序以确保项目按照应用程序要求的顺序处理。</span><span class="sxs-lookup"><span data-stu-id="a17cf-115">Specify the processing order of articles to make sure that articles are processed in the order required by your application.</span></span> <span data-ttu-id="a17cf-116">有关详细信息，请参阅[指定合并复制属性](../publish/specify-merge-replication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-116">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="a17cf-117">指定应将一组相关记录作为一个单元进行处理（默认情况下，合并复制逐行处理对表的更改）。</span><span class="sxs-lookup"><span data-stu-id="a17cf-117">Specify that a set of related records should be processed as a unit (by default, merge replication processes changes to tables on a row-by-row basis).</span></span> <span data-ttu-id="a17cf-118">有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-118">For more information, see [Group Changes to Related Rows with Logical Records](group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
-   <span data-ttu-id="a17cf-119">在一个拓扑中的多个节点上更改相同数据的情况下使用冲突检测和解决方法。</span><span class="sxs-lookup"><span data-stu-id="a17cf-119">Use conflict detection and resolution for cases in which the same data could be changed at more than one node in a topology.</span></span> <span data-ttu-id="a17cf-120">有关详细信息，请参阅 [检测并解决合并复制冲突](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-120">For more information, see [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
-   <span data-ttu-id="a17cf-121">指定架构选项（例如，是否将约束和触发器复制到订阅服务器）。</span><span class="sxs-lookup"><span data-stu-id="a17cf-121">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="a17cf-122">有关详细信息，请参阅 [指定架构选项](../publish/specify-schema-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-122">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="a17cf-123">使用业务逻辑处理程序来对同步期间出现的许多情况进行响应。</span><span class="sxs-lookup"><span data-stu-id="a17cf-123">Use a business logic handler to respond to many conditions during synchronization.</span></span> <span data-ttu-id="a17cf-124">这些情况包括发生数据更改、冲突和错误。</span><span class="sxs-lookup"><span data-stu-id="a17cf-124">These include data changes, conflicts, and errors.</span></span> <span data-ttu-id="a17cf-125">有关详细信息，请参阅[合并同步期间执行业务逻辑](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="a17cf-125">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17cf-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a17cf-126">See Also</span></span>  
 [<span data-ttu-id="a17cf-127">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="a17cf-127">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
