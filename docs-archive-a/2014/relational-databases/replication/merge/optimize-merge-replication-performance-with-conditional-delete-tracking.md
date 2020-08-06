---
title: 使用条件性删除跟踪优化合并复制性能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46fc189d2a2e0ebf5ea44775585a69d52783a7e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576680"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a><span data-ttu-id="74522-102">用条件性删除跟踪优化合并复制的性能</span><span class="sxs-lookup"><span data-stu-id="74522-102">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="74522-103">通过使用合并复制，可以指定复制触发器和系统表跟踪不应删除一个或多个项目的操作。</span><span class="sxs-lookup"><span data-stu-id="74522-103">With merge replication you can specify that deletes for one or more articles should not be tracked by replication triggers and system tables.</span></span> <span data-ttu-id="74522-104">如果为某项目指定了此选项，删除就不会从发布服务器或任何订阅服务器进行跟踪或复制。</span><span class="sxs-lookup"><span data-stu-id="74522-104">If you specify this option for an article, deletes are not tracked or replicated from the Publisher or any Subscribers.</span></span> <span data-ttu-id="74522-105">此选项可用于支持许多应用程序方案，并为不需要或不希望复制删除的情况提供性能优化。</span><span class="sxs-lookup"><span data-stu-id="74522-105">This option is available to support a number of application scenarios and to provide a performance optimization for cases in which the replication of deletes is not necessary or desirable.</span></span> <span data-ttu-id="74522-106">性能可以通过三种方式增强：不存储将删除的元数据、同步期间不枚举删除和不在订阅服务器上复制和应用删除。</span><span class="sxs-lookup"><span data-stu-id="74522-106">Performance is enhanced in three ways: metadata for deletes is not stored; deletes are not enumerated during synchronization; deletes are not replicated to and applied at the Subscriber.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="74522-107">若要使用仅下载项目，发布的兼容级别必须至少为 90RTM。</span><span class="sxs-lookup"><span data-stu-id="74522-107">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
 <span data-ttu-id="74522-108">此选项可以在创建发布时指定，也可以在应用程序要求复制某些删除而不复制另一些删除（如批删除）时打开和关闭此选项。</span><span class="sxs-lookup"><span data-stu-id="74522-108">The option can be specified when a publication is created or it can be toggled on and off if an application requires that some deletes be replicated and that others not be replicated, such as batch deletes.</span></span> <span data-ttu-id="74522-109">下列示例说明了在应用程序中可能使用此选项的几种情况：</span><span class="sxs-lookup"><span data-stu-id="74522-109">The following examples illustrate ways in which this option might be used in an application:</span></span>  
  
-   <span data-ttu-id="74522-110">移动销售组的应用程序通常都有一些表，如 **SalesOrderHeader**、 **SalesOrderDetail** 和 **Product**。</span><span class="sxs-lookup"><span data-stu-id="74522-110">An application for a mobile sales force typically has tables such as **SalesOrderHeader**, **SalesOrderDetail** and **Product**.</span></span> <span data-ttu-id="74522-111">订单在订阅服务器上输入，然后复制到发布服务器上，发布服务器通常向订单履行系统提供数据。</span><span class="sxs-lookup"><span data-stu-id="74522-111">Orders are entered at the Subscriber and then replicated to the Publisher, which often supplies data to an order fulfillment system.</span></span> <span data-ttu-id="74522-112">许多移动员工用的手持设备存储量通常都很有限：因此发布服务器接收到订单后就可以在订阅服务器上将其删除。</span><span class="sxs-lookup"><span data-stu-id="74522-112">Many mobile workers use handheld devices which have limited storage: after the order is received at the Publisher, it can be deleted at the Subscriber.</span></span> <span data-ttu-id="74522-113">删除不会传播到发布服务器，因为订单在系统中仍是活动的。</span><span class="sxs-lookup"><span data-stu-id="74522-113">The delete is not propagated to the Publisher, because the order is still active in the system.</span></span>  
  
     <span data-ttu-id="74522-114">这种情况下，不会对 **SalesOrderHeader** 和 **SalesOrderDetail** 表中的删除进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="74522-114">In this scenario, deletes would not be tracked for the **SalesOrderHeader** and **SalesOrderDetail** tables.</span></span> <span data-ttu-id="74522-115">但会对 **Product** 表中的删除进行跟踪，因为如果某产品在发布服务器上删除，则删除应发送到订阅服务器以保持产品列表最新。</span><span class="sxs-lookup"><span data-stu-id="74522-115">Deletes would be tracked for the **Product** table, because if a product is deleted at the Publisher, the delete should be sent to the Subscriber to keep the product list up to date.</span></span>  
  
-   <span data-ttu-id="74522-116">应用程序可以在表中存储历史数据，比如 **TransactionHistory**表，该表会定期清除超过一年的历史记录。</span><span class="sxs-lookup"><span data-stu-id="74522-116">An application could store historical data in a table such as **TransactionHistory**, which is periodically purged of records older than a year.</span></span> <span data-ttu-id="74522-117">对表可以进行筛选，以使订阅服务器只接收当月的事务数据。</span><span class="sxs-lookup"><span data-stu-id="74522-117">The table could be filtered such that Subscribers only receive data on transactions within the current month.</span></span> <span data-ttu-id="74522-118">在清除旧数据的发布服务器上的月度批量删除与订阅服务器无关，但默认情况下还会对这些删除进行跟踪和枚举。</span><span class="sxs-lookup"><span data-stu-id="74522-118">Monthly batch deletes at the Publisher that purge older data are not relevant to Subscribers, but they would still be tracked and enumerated by default.</span></span>  
  
     <span data-ttu-id="74522-119">在这种情况下，执行批处理前，可以停止系统中的活动，而应用程序也可以禁用对删除的跟踪。</span><span class="sxs-lookup"><span data-stu-id="74522-119">In this scenario, before the batch processing occurred, activity could be stopped on the system, and the application could disable the tracking of deletes.</span></span> <span data-ttu-id="74522-120">处理完成后，跟踪可以重新启用。</span><span class="sxs-lookup"><span data-stu-id="74522-120">After the processing has finished, tracking could again be enabled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74522-121">如果其他活动在发布服务器上继续运行，则必须确保在禁用对删除的跟踪时不发生任何将传播到订阅服务器的删除。</span><span class="sxs-lookup"><span data-stu-id="74522-121">If other activity continues at the Publisher, you must ensure that deletes that should be propagated to Subscribers do not occur while delete tracking is disabled.</span></span>  
  
 <span data-ttu-id="74522-122">**指定不应跟踪删除**</span><span class="sxs-lookup"><span data-stu-id="74522-122">**To specify that deletes should not be tracked**</span></span>  
  
-   <span data-ttu-id="74522-123">复制 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 编程：[为合并项目指定不应跟踪删除（复制 Transact-SQL 编程）](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span><span class="sxs-lookup"><span data-stu-id="74522-123">Replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming: [Specify That Deletes Should Not Be Tracked For Merge Articles &#40;Replication Transact-SQL Programming&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74522-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74522-124">See Also</span></span>  
 <span data-ttu-id="74522-125">[用于合并复制的项目选项](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="74522-125">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="74522-126">使用仅下载项目优化合并复制性能</span><span class="sxs-lookup"><span data-stu-id="74522-126">Optimize Merge Replication Performance with Download-Only Articles</span></span>](optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
