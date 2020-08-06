---
title: 其他复制升级问题 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e8ce3f35ead9d3322c636462f682ef391703cfe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590021"
---
# <a name="other-replication-upgrade-issues"></a><span data-ttu-id="ad7fe-102">其他复制升级问题</span><span class="sxs-lookup"><span data-stu-id="ad7fe-102">Other Replication Upgrade Issues</span></span>
  <span data-ttu-id="ad7fe-103">本主题涵盖了许多未由升级顾问报告的升级问题。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-103">This topic covers a number of upgrade issues that are not reported by Upgrade Advisor.</span></span>  
  
## <a name="versions-supported"></a><span data-ttu-id="ad7fe-104">支持的版本</span><span class="sxs-lookup"><span data-stu-id="ad7fe-104">Versions Supported</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ad7fe-105">支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本升级复制的数据库。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-105">supports upgrading replicated databases from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad7fe-106">在升级某个节点时，不必停止其他节点的活动。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-106">You do not have to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="ad7fe-107">请务必遵守有关拓扑中支持哪些版本的规则。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-107">Ensure that you adhere to the rules regarding which versions are supported in a topology.</span></span>  
  
 <span data-ttu-id="ad7fe-108">当在不同版本的之间进行复制时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，通常仅限于所使用的最早版本的功能。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-108">When you replicate between or among different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you are usually limited to the functionality of the earliest version that is being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad7fe-109">由于 64 位和 32 位环境中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘存储格式相同，因此复制拓扑可以将运行于 32 位环境中的服务器实例与运行于 64 位环境中的服务器实例结合起来。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-109">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments, a replication topology can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  
 <span data-ttu-id="ad7fe-110">对于所有类型的复制，分发服务器版本不得低于发布服务器版本。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-110">For all types of replication, the Distributor version must be no earlier than the Publisher version.</span></span> <span data-ttu-id="ad7fe-111">（分发服务器通常与发布服务器是同一个实例。）</span><span class="sxs-lookup"><span data-stu-id="ad7fe-111">(Frequently, the Distributor is the same instance as the Publisher.)</span></span>  
  
 <span data-ttu-id="ad7fe-112">对于事务复制，用于事务发布的订阅服务器版本可以是两个发布服务器版本中的任何一个版本。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-112">For transactional replication, a Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span>  
  
 <span data-ttu-id="ad7fe-113">对于合并复制，用于合并发布的订阅服务器的版本不能比发布服务器版本高。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-113">For merge replication, a Subscriber to a merge publication can be any version no later than the Publisher version.</span></span>  
  
## <a name="merge-replication-batches-changes"></a><span data-ttu-id="ad7fe-114">对合并复制批次进行的更改</span><span class="sxs-lookup"><span data-stu-id="ad7fe-114">Merge Replication Batches Changes</span></span>  
 <span data-ttu-id="ad7fe-115">为提高性能，合并代理执行的更改是成批执行的；因此，可以在一个语句内插入、更新或删除多行。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-115">Changes that are made by the Merge Agent are batched to improve performance; therefore, more than one row can be inserted, updated, or deleted within a single statement.</span></span> <span data-ttu-id="ad7fe-116">如果发布数据库或订阅数据库中任何已发布的表都有触发器，请确保这些触发器可以处理插入、更新和删除多行的操作。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-116">If any published tables in the publication or subscription databases have triggers, ensure that the triggers can handle multirow inserts, updates, and deletes.</span></span> <span data-ttu-id="ad7fe-117">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“DML 触发器的多行注意事项”。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-117">For more information, see "Multirow Considerations for DML Triggers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="activex-control-changes"></a><span data-ttu-id="ad7fe-118">对 ActiveX 控件进行的更改</span><span class="sxs-lookup"><span data-stu-id="ad7fe-118">ActiveX Control Changes</span></span>  
 <span data-ttu-id="ad7fe-119">已经针对复制 ActiveX 控件进行了如下更改：</span><span class="sxs-lookup"><span data-stu-id="ad7fe-119">The following changes have been made for replication ActiveX controls:</span></span>  
  
-   <span data-ttu-id="ad7fe-120">所有 ActiveX 控件都标记为对脚本编写和初始化不安全。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-120">All ActiveX controls are marked as unsafe for scripting and initialization.</span></span>  
  
-   <span data-ttu-id="ad7fe-121">已经删除了快照 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-121">The Snapshot ActiveX control has been dropped.</span></span> <span data-ttu-id="ad7fe-122">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或者使用复制存储过程以编程方式创建和管理快照。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-122">You can create and manage snapshots by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or programmatically by using replication stored procedures.</span></span> <span data-ttu-id="ad7fe-123">有关详细信息，请参阅 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 联机丛书中的“如何创建和应用初始快照 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])”和“如何创建初始快照（复制 Transact-SQL 编程）”主题。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-123">For more information, see the topics "How to: Create and Apply the Initial Snapshot ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)])" and "How to: Create the Initial Snapshot (Replication Transact-SQL Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="ad7fe-124">分发 ActiveX 控件和合并 ActiveX 控件已废止。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-124">The Distribution ActiveX control and Merge ActiveX control have been deprecated.</span></span> <span data-ttu-id="ad7fe-125">对于使用复制管理对象 (RMO) 的托管代码应用程序提供了类似功能。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-125">Similar functionality is provided for managed code applications using Replication Management Objects (RMO).</span></span> <span data-ttu-id="ad7fe-126">有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“同步订阅（RMO 编程）”。</span><span class="sxs-lookup"><span data-stu-id="ad7fe-126">For more information, see "Synchronizing Subscriptions (RMO Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7fe-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad7fe-127">See Also</span></span>  
 [<span data-ttu-id="ad7fe-128">复制升级问题</span><span class="sxs-lookup"><span data-stu-id="ad7fe-128">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
