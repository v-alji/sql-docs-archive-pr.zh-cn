---
title: 为合并复制筛选已发布数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ad9ad45a64f57a6bef8255373180ea943af9893f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576694"
---
# <a name="filter-published-data-for-merge-replication"></a><span data-ttu-id="84e79-102">为合并复制筛选已发布数据</span><span class="sxs-lookup"><span data-stu-id="84e79-102">Filter Published Data for Merge Replication</span></span>
  <span data-ttu-id="84e79-103">除了可使用其他类型的复制定义的静态行筛选器和列筛选器之外，合并复制还提供参数化行筛选器和联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="84e79-103">In addition to the static row filters and column filters you can define with other types of replication, merge replication offers parameterized row filters and join filters.</span></span> <span data-ttu-id="84e79-104">有关静态行筛选器和列筛选器的详细信息，请参阅[筛选已发布数据](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="84e79-104">For more information about static row filters and column filters, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
 <span data-ttu-id="84e79-105">合并复制用于多种支持移动用户的应用程序；这些应用程序通常有大量订阅，每个订阅接收唯一的数据集。</span><span class="sxs-lookup"><span data-stu-id="84e79-105">Merge replication is used in many applications that support mobile users; these applications usually have a large number of subscriptions with each subscription receiving a unique data set.</span></span> <span data-ttu-id="84e79-106">与联接筛选器结合的参数化筛选器允许管理员设置一个发布（或最多少量几个发布），并为用户提供不同的数据集，这就降低了因创建多个发布而造成的管理开销。</span><span class="sxs-lookup"><span data-stu-id="84e79-106">Parameterized filters combined with join filters allow an administrator to set up one publication (or at most a small number of publications) and yet provide different data sets to users, reducing the management overhead introduced by creating multiple publications.</span></span>  
  
-   <span data-ttu-id="84e79-107">通过参数化筛选器，可以将数据的不同分区发送给不同的订阅服务器，而不需要创建多个发布。</span><span class="sxs-lookup"><span data-stu-id="84e79-107">Parameterized filters allow different partitions of data to be sent to different Subscribers without requiring multiple publications to be created.</span></span> <span data-ttu-id="84e79-108">例如，可以对表进行筛选，以便仅将给定销售代表的数据复制给此销售代表。</span><span class="sxs-lookup"><span data-stu-id="84e79-108">For example, a table can be filtered so that data for a given sales representative is replicated only to that representative.</span></span> <span data-ttu-id="84e79-109">参数化筛选器具有多种选项，允许定制筛选以优化性能并最大限度符合数据和应用程序的要求。</span><span class="sxs-lookup"><span data-stu-id="84e79-109">Parameterized filters have a variety of options that allow you to tailor filtering to optimize performance and best match your data and application requirements.</span></span> <span data-ttu-id="84e79-110">有关详细信息，请参阅 [参数化行筛选器](parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="84e79-110">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="84e79-111">联接筛选器通常与参数化筛选器一起使用，以扩展对相关表的筛选（还可与静态筛选器一起使用）。</span><span class="sxs-lookup"><span data-stu-id="84e79-111">Join filters are typically used in conjunction with parameterized filters to extend filtering to related tables (they can also be used in conjunction with static filters).</span></span> <span data-ttu-id="84e79-112">例如，销售代表通常在其他表（如 customer 和 order 表）中也有数据。</span><span class="sxs-lookup"><span data-stu-id="84e79-112">For example, the sales representative typically has data in other tables such as customer and order tables.</span></span> <span data-ttu-id="84e79-113">可以对这些数据进行筛选，从而使销售代表只收到其客户和客户订单的相关数据。</span><span class="sxs-lookup"><span data-stu-id="84e79-113">This data can be filtered so the sales representative receives only the data on her customers and her customers' orders.</span></span> <span data-ttu-id="84e79-114">有关详细信息，请参阅 [Join Filters](join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="84e79-114">For more information, see [Join Filters](join-filters.md).</span></span>  
  
 <span data-ttu-id="84e79-115">筛选器不能包含复制所用的 `rowguidcol` 来标识行。</span><span class="sxs-lookup"><span data-stu-id="84e79-115">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="84e79-116">默认情况下，这是您设置合并复制时添加的列，命名为 **rowguid**。</span><span class="sxs-lookup"><span data-stu-id="84e79-116">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e79-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84e79-117">See Also</span></span>  
 [<span data-ttu-id="84e79-118">发布数据和数据库对象</span><span class="sxs-lookup"><span data-stu-id="84e79-118">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
