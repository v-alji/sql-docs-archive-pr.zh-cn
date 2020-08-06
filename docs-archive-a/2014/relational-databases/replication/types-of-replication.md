---
title: 复制类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5576331004eca44bc32dbde8f430284f75e6eb70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690496"
---
# <a name="types-of-replication"></a><span data-ttu-id="e6250-102">复制类型</span><span class="sxs-lookup"><span data-stu-id="e6250-102">Types of Replication</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="e6250-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供以下类型的复制以用于分布式应用程序：</span><span class="sxs-lookup"><span data-stu-id="e6250-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following types of replication for use in distributed applications:</span></span>  
  
-   <span data-ttu-id="e6250-104">事务复制。</span><span class="sxs-lookup"><span data-stu-id="e6250-104">Transactional replication.</span></span> <span data-ttu-id="e6250-105">有关详细信息，请参阅 [事务复制](transactional/transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="e6250-105">For more information, see [Transactional Replication](transactional/transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="e6250-106">合并复制。</span><span class="sxs-lookup"><span data-stu-id="e6250-106">Merge replication.</span></span> <span data-ttu-id="e6250-107">有关详细信息，请参阅[合并复制](merge/merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="e6250-107">For more information, see [Merge Replication](merge/merge-replication.md).</span></span>  
  
-   <span data-ttu-id="e6250-108">快照复制。</span><span class="sxs-lookup"><span data-stu-id="e6250-108">Snapshot replication.</span></span> <span data-ttu-id="e6250-109">有关详细信息，请参阅[快照复制](snapshot-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="e6250-109">For more information, see [Snapshot Replication](snapshot-replication.md).</span></span>  
  
 <span data-ttu-id="e6250-110">为应用程序选择的复制类型取决于多种因素，其中包括实际复制环境、要复制的数据类型和数量，以及是否在订阅服务器上更新数据等等。</span><span class="sxs-lookup"><span data-stu-id="e6250-110">The type of replication you choose for an application depends on many factors, including the physical replication environment, the type and quantity of data to be replicated, and whether the data is updated at the Subscriber.</span></span> <span data-ttu-id="e6250-111">实际环境包括复制中所涉及的计算机数量和位置，以及这些计算机是客户端（工作站、便携式电脑或手持设备）还是服务器。</span><span class="sxs-lookup"><span data-stu-id="e6250-111">The physical environment includes the number and location of computers involved in replication and whether these computers are clients (workstations, laptops, or handheld devices) or servers.</span></span>  
  
 <span data-ttu-id="e6250-112">每种复制类型通常都开始于发布服务器和订阅服务器之间的已发布对象的初始同步。</span><span class="sxs-lookup"><span data-stu-id="e6250-112">Each type of replication typically begins with an initial synchronization of the published objects between the Publisher and Subscribers.</span></span> <span data-ttu-id="e6250-113">此初始同步可以由带有“快照” 的复制执行，该快照为发布所指定的所有对象和数据的副本。</span><span class="sxs-lookup"><span data-stu-id="e6250-113">This initial synchronization can be performed by replication with a *snapshot*, which is a copy of all of the objects and data specified by a publication.</span></span> <span data-ttu-id="e6250-114">快照在创建之后，便被传递到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="e6250-114">After the snapshot is created, it is delivered to the Subscribers.</span></span> <span data-ttu-id="e6250-115">对于某些应用程序而言，只需快照复制即可。</span><span class="sxs-lookup"><span data-stu-id="e6250-115">For some applications, snapshot replication is all that is required.</span></span> <span data-ttu-id="e6250-116">对于另一些类型的应用程序而言，后续数据更改应随着时间而增量式地传递到订阅服务器，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="e6250-116">For other types of applications, it is important that subsequent data changes flow to the Subscriber incrementally over time.</span></span> <span data-ttu-id="e6250-117">某些应用程序也需要更改从订阅服务器传递回发布服务器。</span><span class="sxs-lookup"><span data-stu-id="e6250-117">Some applications also require that changes flow from the Subscriber back to the Publisher.</span></span> <span data-ttu-id="e6250-118">事务复制和合并复制为这些类型的应用程序提供了若干选项。</span><span class="sxs-lookup"><span data-stu-id="e6250-118">Transactional replication and merge replication provide options for these types of applications.</span></span>  
  
 <span data-ttu-id="e6250-119">不会跟踪快照复制的数据更改；每次应用快照时，都将完全覆盖现有数据。</span><span class="sxs-lookup"><span data-stu-id="e6250-119">Data changes are not tracked for snapshot replication; each time a snapshot is applied, it completely overwrites the existing data.</span></span> <span data-ttu-id="e6250-120">事务复制通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事务日志跟踪更改，而合并复制则通过触发器和元数据表跟踪更改。</span><span class="sxs-lookup"><span data-stu-id="e6250-120">Transactional replication tracks changes through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, and merge replication tracks changes through triggers and metadata tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6250-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6250-121">See Also</span></span>  
 [<span data-ttu-id="e6250-122">复制代理概述</span><span class="sxs-lookup"><span data-stu-id="e6250-122">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
