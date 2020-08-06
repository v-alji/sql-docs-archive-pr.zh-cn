---
title: 使用仅下载项目优化合并复制性能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 8851faa6-e6df-4ea5-a6ea-2a3471680fa3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8414174971792f8a2c256cd564dd1ea224527463
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576677"
---
# <a name="optimize-merge-replication-performance-with-download-only-articles"></a><span data-ttu-id="574bf-102">使用仅下载项目优化合并复制的性能</span><span class="sxs-lookup"><span data-stu-id="574bf-102">Optimize Merge Replication Performance with Download-Only Articles</span></span>
  <span data-ttu-id="574bf-103">合并复制提供了两种不同的项目类型以满足不同的应用程序需要。</span><span class="sxs-lookup"><span data-stu-id="574bf-103">Merge replication offers two different article types to address different application needs.</span></span> <span data-ttu-id="574bf-104">根据应用程序的需要，发布可以包含下列项目类型中的一个或多个：</span><span class="sxs-lookup"><span data-stu-id="574bf-104">Publications can contain one or more of each of these article types as appropriate for the application:</span></span>  
  
-   <span data-ttu-id="574bf-105">标准项目</span><span class="sxs-lookup"><span data-stu-id="574bf-105">Standard articles</span></span>  
  
-   <span data-ttu-id="574bf-106">仅下载项目</span><span class="sxs-lookup"><span data-stu-id="574bf-106">Download-only articles</span></span>  
  
 <span data-ttu-id="574bf-107">仅下载项目比标准项目具有性能优势，应尽可能使用这种项目。</span><span class="sxs-lookup"><span data-stu-id="574bf-107">Download-only articles provide performance advantages over standard articles and should be used where appropriate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="574bf-108">若要使用仅下载项目，发布的兼容级别必须至少为 90RTM。</span><span class="sxs-lookup"><span data-stu-id="574bf-108">To use download-only articles, the compatibility level of the publication must be at least 90RTM.</span></span>  
  
## <a name="standard-articles"></a><span data-ttu-id="574bf-109">标准项目</span><span class="sxs-lookup"><span data-stu-id="574bf-109">Standard Articles</span></span>  
 <span data-ttu-id="574bf-110">标准项目是默认项目，可以提供所有合并复制功能，包括丰富的冲突检测和解决。</span><span class="sxs-lookup"><span data-stu-id="574bf-110">Standard articles are the default, offering the full range of merge replication features, including rich conflict detection and resolution.</span></span> <span data-ttu-id="574bf-111">标准项目适用于由多个订阅服务器更新的表，表以外的对象（如存储过程和视图）始终按标准项目发布。</span><span class="sxs-lookup"><span data-stu-id="574bf-111">Standard articles are appropriate for tables that are updated by multiple Subscribers; objects other than tables, such as stored procedures and views, are always published as standard articles.</span></span>  
  
## <a name="download-only-articles"></a><span data-ttu-id="574bf-112">仅下载项目</span><span class="sxs-lookup"><span data-stu-id="574bf-112">Download-Only Articles</span></span>  
 <span data-ttu-id="574bf-113">仅下载项目是为数据不在订阅服务器上更新的应用程序设计的，如包含在产品目录中的一组项目。</span><span class="sxs-lookup"><span data-stu-id="574bf-113">Download-only articles are designed for applications with data that is not updated at Subscribers, such as a set of articles that are contained in a product catalog.</span></span> <span data-ttu-id="574bf-114">产品目录通常在发布服务器上更新，而不是在订阅服务器上更新。</span><span class="sxs-lookup"><span data-stu-id="574bf-114">A product catalog is typically updated at the Publisher, but not at the Subscribers.</span></span> <span data-ttu-id="574bf-115">因为仅供下载的项目不能在订阅服务器上更新，所以跟踪元数据不会发送到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="574bf-115">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="574bf-116">这可以减少订阅服务器上的存储量并提高性能，特别是当网络连接较慢时。</span><span class="sxs-lookup"><span data-stu-id="574bf-116">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span>  
  
 <span data-ttu-id="574bf-117">仅下载项目与客户端订阅一起使用：如果项目设计为仅下载项目，则不能在使用客户端订阅的订阅服务器上插入、更新或删除该项目的行。</span><span class="sxs-lookup"><span data-stu-id="574bf-117">Download-only articles work in conjunction with client subscriptions: if an article is designated as download-only, rows for that article cannot be inserted, updated, or deleted at Subscribers who use client subscriptions.</span></span> <span data-ttu-id="574bf-118">使用服务器订阅类型的发布服务器和订阅服务器（通常是指将数据重新发布到其他订阅服务器的订阅服务器）可以插入、更新和删除数据。</span><span class="sxs-lookup"><span data-stu-id="574bf-118">Publishers and Subscribers that use the server subscription type (typically Subscribers that republish data to other Subscribers) can insert, update, and delete data.</span></span> <span data-ttu-id="574bf-119">有关客户端订阅的详细信息，请参阅[订阅发布](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="574bf-119">For more information about client subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="574bf-120">若要将某个项目指定为仅下载项目，请参阅 [指定合并表项目仅用于下载](../publish/specify-merge-replication-properties.md#download-only)。</span><span class="sxs-lookup"><span data-stu-id="574bf-120">To specify that an article is download-only, see [Specify That a Merge Table Article is Download-Only](../publish/specify-merge-replication-properties.md#download-only).</span></span>  
  
## <a name="using-different-article-types-in-your-applications"></a><span data-ttu-id="574bf-121">在应用程序中使用不同的项目类型</span><span class="sxs-lookup"><span data-stu-id="574bf-121">Using Different Article Types in Your Applications</span></span>  
 <span data-ttu-id="574bf-122">通过了解应用程序的要求，可以在最大灵活性和最佳性能之间找到平衡点。</span><span class="sxs-lookup"><span data-stu-id="574bf-122">By understanding the requirements of your application, you can make tradeoffs between maximum flexibility and optimal performance.</span></span> <span data-ttu-id="574bf-123">例如，在发布服务器和订阅服务器上都存在大量冲突和更改的应用程序将使用由标准项目组成的发布。</span><span class="sxs-lookup"><span data-stu-id="574bf-123">For example, applications with numerous conflicts and changes at both the Publisher and Subscribers will use a publication made up of standard articles.</span></span> <span data-ttu-id="574bf-124">有些应用程序（如销售人员自动化应用程序）可能包含存在潜在冲突的项目以及作为查找表的其他项目，这些项目可以指定为仅下载项目。</span><span class="sxs-lookup"><span data-stu-id="574bf-124">Some applications, such as a sales force automation application, might have articles with a potential for conflicts, and other articles that function as lookup tables, which can be specified as download-only.</span></span> <span data-ttu-id="574bf-125">数据输入应用程序（如销售点系统和现场人员自动化应用程序）通常以消除冲突的方式对数据进行严格的分区，使一个订阅服务器上的数据永远不会到另一个订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="574bf-125">Data entry applications, such as point of sales systems and field force automation applications, often strictly partition data in a way that conflicts are eliminated, and data from one Subscriber never goes to another.</span></span> <span data-ttu-id="574bf-126">在这些情况下，不重叠的分区、仅下载项目和预计算分区的组合可以提供最好的性能和最大的伸缩性。</span><span class="sxs-lookup"><span data-stu-id="574bf-126">In these situations, a combination of nonoverlapping partitions, download-only articles and precomputed partitions provides maximum performance and scalability.</span></span> <span data-ttu-id="574bf-127">有关不重叠分区和预计算分区的详细信息，请参阅 [参数化行筛选器](parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="574bf-127">For more information about nonoverlapping partitions and precomputed partitions, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="574bf-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="574bf-128">See Also</span></span>  
 <span data-ttu-id="574bf-129">[用于合并复制的项目选项](article-options-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="574bf-129">[Article Options for Merge Replication](article-options-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="574bf-130">用条件性删除跟踪优化合并复制的性能</span><span class="sxs-lookup"><span data-stu-id="574bf-130">Optimize Merge Replication Performance with Conditional Delete Tracking</span></span>](optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
