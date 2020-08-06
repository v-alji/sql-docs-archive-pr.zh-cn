---
title: 镜像状态 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d458939ba233bdfe7a99edd38afc74b5433ae061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578389"
---
# <a name="mirroring-states-sql-server"></a><span data-ttu-id="8f978-102">镜像状态 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f978-102">Mirroring States (SQL Server)</span></span>
  <span data-ttu-id="8f978-103">数据库镜像会话期间，镜像数据库一直处于一种特定状态（镜像状态）。</span><span class="sxs-lookup"><span data-stu-id="8f978-103">During a database mirroring session, the mirrored database is always in a specific state (the *mirroring state*).</span></span> <span data-ttu-id="8f978-104">数据库的状态反映了通信状态、数据流和伙伴之间数据的差异。</span><span class="sxs-lookup"><span data-stu-id="8f978-104">The state of the database reflects the communication status, data flow, and the difference in data between the partners.</span></span> <span data-ttu-id="8f978-105">数据库镜像会话采用的状态与主体数据库相同。</span><span class="sxs-lookup"><span data-stu-id="8f978-105">The database mirroring session adopts the same state as the principal database.</span></span>  
  
 <span data-ttu-id="8f978-106">在整个数据库镜像会话期间，服务器实例相互监视。</span><span class="sxs-lookup"><span data-stu-id="8f978-106">Throughout a database mirroring session, the server instances monitor each other.</span></span> <span data-ttu-id="8f978-107">伙伴使用镜像状态监视数据库。</span><span class="sxs-lookup"><span data-stu-id="8f978-107">The partners use the mirroring state to monitor the database.</span></span> <span data-ttu-id="8f978-108">除 PENDING_FAILOVER 状态外，主体数据库和镜像数据库始终处于同一状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-108">With the exception of the PENDING_FAILOVER state, the principal and mirror database are always in the same state.</span></span> <span data-ttu-id="8f978-109">如果为会话设置一个见证服务器，则每个伙伴都将使用其连接状态（CONNECTED 或 DISCONNECTED）监视该见证服务器。</span><span class="sxs-lookup"><span data-stu-id="8f978-109">If a witness is set for the session, each of the partners monitors the witness using its connection state (CONNECTED or DISCONNECTED).</span></span>  
  
 <span data-ttu-id="8f978-110">可能的数据库镜像状态如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f978-110">The possible mirroring states of the database are as follows:</span></span>  
  
|<span data-ttu-id="8f978-111">镜像状态</span><span class="sxs-lookup"><span data-stu-id="8f978-111">Mirroring state</span></span>|<span data-ttu-id="8f978-112">说明</span><span class="sxs-lookup"><span data-stu-id="8f978-112">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="8f978-113">SYNCHRONIZING</span><span class="sxs-lookup"><span data-stu-id="8f978-113">SYNCHRONIZING</span></span>|<span data-ttu-id="8f978-114">镜像数据库的内容滞后于主体数据库的内容。</span><span class="sxs-lookup"><span data-stu-id="8f978-114">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="8f978-115">主体服务器正在将日志记录发送到镜像服务器（正在将更改应用于镜像数据库以使其前滚）。</span><span class="sxs-lookup"><span data-stu-id="8f978-115">The principal server is sending log records to the mirror server, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="8f978-116">在数据库镜像会话开始时，数据库处于 SYNCHRONIZING 状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-116">At the start of a database mirroring session, the database is in the SYNCHRONIZING state.</span></span> <span data-ttu-id="8f978-117">主体服务器为数据库提供服务，同时镜像服务器尽量与主体服务器保持同步。</span><span class="sxs-lookup"><span data-stu-id="8f978-117">The principal server is serving the database, and the mirror is trying to catch up.</span></span>|  
|<span data-ttu-id="8f978-118">SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="8f978-118">SYNCHRONIZED</span></span>|<span data-ttu-id="8f978-119">当镜像服务器与主体服务器几乎保持同步时，镜像状态将更改为 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="8f978-119">When the mirror server becomes sufficiently caught up to the principal server, the mirroring state changes to SYNCHRONIZED.</span></span> <span data-ttu-id="8f978-120">只要主体服务器继续向镜像服务器发送更改，并且镜像服务器继续将更改应用于镜像数据库，数据库就会保持此状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-120">The database remains in this state as long as the principal server continues to send changes to the mirror server and the mirror server continues to apply changes to the mirror database.</span></span><br /><br /> <span data-ttu-id="8f978-121">如果将事务安全性设置为 FULL，则 SYNCHRONIZED 状态同时支持自动故障转移和手动故障转移，并且在故障转移后不会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="8f978-121">If transaction safety is set to FULLautomatic failover and manual failover are both supported in the SYNCHRONIZED state, there is no data loss after a failover.</span></span><br /><br /> <span data-ttu-id="8f978-122">如果关闭事务安全性，则即使处于 SYNCHRONIZED 状态，也总可能丢失某些数据。</span><span class="sxs-lookup"><span data-stu-id="8f978-122">If transaction safety is off, some data loss is always possible, even in the SYNCHRONIZED state.</span></span>|  
|<span data-ttu-id="8f978-123">SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="8f978-123">SUSPENDED</span></span>|<span data-ttu-id="8f978-124">数据库的镜像副本不可用。</span><span class="sxs-lookup"><span data-stu-id="8f978-124">The mirror copy of the database is not available.</span></span> <span data-ttu-id="8f978-125">主体数据库运行时不向镜像服务器发送任何日志，这种情况称为“运行已公开” 。</span><span class="sxs-lookup"><span data-stu-id="8f978-125">The principal database is running without sending any logs to the mirror server, a condition known as *running exposed*.</span></span> <span data-ttu-id="8f978-126">这是故障转移后的状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-126">This is the state after a failover.</span></span><br /><br /> <span data-ttu-id="8f978-127">如果发生重做错误或管理员暂停会话，则会话也可能会变为 SUSPENDED 状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-127">A session can also become SUSPENDED as a result of redo errors or if the administrator pauses the session.</span></span><br /><br /> <span data-ttu-id="8f978-128">SUSPENDED 是在伙伴关闭和启动时都能存在的持久性状态。</span><span class="sxs-lookup"><span data-stu-id="8f978-128">SUSPENDED is a persistent state that survives partner shutdowns and startups.</span></span>|  
|<span data-ttu-id="8f978-129">PENDING_FAILOVER</span><span class="sxs-lookup"><span data-stu-id="8f978-129">PENDING_FAILOVER</span></span>|<span data-ttu-id="8f978-130">此状态只在故障转移开始之后的主体服务器中存在，但此时服务器尚未转换到镜像角色。</span><span class="sxs-lookup"><span data-stu-id="8f978-130">This state is found only on the principal server after a failover has begun, but the server has not transitioned into the mirror role.</span></span><br /><br /> <span data-ttu-id="8f978-131">当故障转移开始时，主体数据库将进入 PENDING_FAILOVER 状态，快速终止任何用户连接，并在此后不久便接管镜像角色。</span><span class="sxs-lookup"><span data-stu-id="8f978-131">When the failover is initiated, the principal database goes into the PENDING_FAILOVER state, quickly terminates any user connections, and takes over the mirror role soon thereafter.</span></span>|  
|<span data-ttu-id="8f978-132">DISCONNECTED</span><span class="sxs-lookup"><span data-stu-id="8f978-132">DISCONNECTED</span></span>|<span data-ttu-id="8f978-133">伙伴已失去与其他伙伴的通信。</span><span class="sxs-lookup"><span data-stu-id="8f978-133">The partner has lost communication with the other partner.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f978-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f978-134">See Also</span></span>  
 [<span data-ttu-id="8f978-135">监视数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f978-135">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
