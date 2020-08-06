---
title: 仲裁：见证服务器如何影响数据库可用性（数据库镜像） | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- quorum [SQL Server], database mirroring
- running exposed in database mirroring [SQL Server]
- witness-to-partner quorum [SQL Server]
- partners [SQL Server], partner-to-partner quorum
- witness [SQL Server], quorum
- have quorum [SQL Server]
- quorum [SQL Server]
- mirror database [SQL Server]
- full quorum [SQL Server]
- high-availability mode [SQL Server]
ms.assetid: a62d9dd7-3667-4751-a294-a61fc9caae7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ada152f280a4ac75543f09e5f5afa7c72c0cbef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690118"
---
# <a name="quorum-how-a-witness-affects-database-availability-database-mirroring"></a><span data-ttu-id="334b3-102">仲裁：见证服务器如何影响数据库可用性（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="334b3-102">Quorum: How a Witness Affects Database Availability (Database Mirroring)</span></span>
  <span data-ttu-id="334b3-103">每当为数据库镜像会话设置见证服务器时，都需要“仲裁  ”。</span><span class="sxs-lookup"><span data-stu-id="334b3-103">Whenever a witness is set for a database mirroring session, *quorum* is required.</span></span> <span data-ttu-id="334b3-104">仲裁是数据库镜像会话中两个或多个服务器实例彼此连接时存在的一种关系。</span><span class="sxs-lookup"><span data-stu-id="334b3-104">Quorum is a relationship that exists when two or more server instances in a database mirroring session are connected to each other.</span></span> <span data-ttu-id="334b3-105">仲裁通常包括三个互连的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="334b3-105">Typically, quorum involves three interconnected server instances.</span></span> <span data-ttu-id="334b3-106">设置见证服务器时，必须具有仲裁才能使用数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-106">When a witness is set, quorum is required to make the database available.</span></span> <span data-ttu-id="334b3-107">仲裁旨在用于具有自动故障转移功能的高安全性模式，可确保一个数据库一次只属于一个伙伴。</span><span class="sxs-lookup"><span data-stu-id="334b3-107">Designed for high-safety mode with automatic failover, quorum makes sure that a database is owned by only one partner at a time.</span></span>  
  
 <span data-ttu-id="334b3-108">如果特定的服务器实例与镜像会话断开连接，则该实例将失去仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-108">If a particular server instance becomes disconnected from a mirroring session, that instance loses quorum.</span></span> <span data-ttu-id="334b3-109">如果没有连接任何服务器实例，则会话将失去仲裁，并无法使用数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-109">If no server instances are connected, the session loses quorum and the database becomes unavailable.</span></span> <span data-ttu-id="334b3-110">可以进行的仲裁有三种：</span><span class="sxs-lookup"><span data-stu-id="334b3-110">Three types of quorum are possible:</span></span>  
  
-   <span data-ttu-id="334b3-111">“完全仲裁  ”包含伙伴双方以及见证服务器。</span><span class="sxs-lookup"><span data-stu-id="334b3-111">A *full quorum* includes both partners and the witness.</span></span>  
  
-   <span data-ttu-id="334b3-112">见证服务器-伙伴仲裁包含见证服务器和一个伙伴。</span><span class="sxs-lookup"><span data-stu-id="334b3-112">A *witness-to-partner quorum* consists of the witness and either partner.</span></span>  
  
-   <span data-ttu-id="334b3-113">伙伴-伙伴仲裁包含伙伴双方。</span><span class="sxs-lookup"><span data-stu-id="334b3-113">A *partner-to-partner quorum* consists of the two partners.</span></span>  
  
 <span data-ttu-id="334b3-114">下图显示了这三种类型的仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-114">The following figure shows these types of quorum.</span></span>  
  
 <span data-ttu-id="334b3-115">![仲裁：完全；见证服务器和伙伴；伙伴双方](../media/dbm-failovautoquorum.gif "仲裁：完全；见证服务器和伙伴；伙伴双方")</span><span class="sxs-lookup"><span data-stu-id="334b3-115">![Quorums: full; witness and partner; both partners](../media/dbm-failovautoquorum.gif "Quorums: full; witness and partner; both partners")</span></span>  
  
 <span data-ttu-id="334b3-116">只要当前的主体服务器具有仲裁，它就拥有主体服务器的角色并可继续操作数据库，除非数据库所有者执行手动故障转移。</span><span class="sxs-lookup"><span data-stu-id="334b3-116">As long as the current principal server has quorum, this server owns the role of principal and continues to serve the database, unless the database owner performs a manual failover.</span></span> <span data-ttu-id="334b3-117">如果主体服务器失去仲裁，它将停止操作数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-117">If the principal server loses quorum, it stops serving the database.</span></span> <span data-ttu-id="334b3-118">仅当主体服务器失去仲裁时，才会发生自动故障转移，这确保它不再操作数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-118">Automatic failover can occur only if the principal database has lost quorum, which guarantees that it is no longer serving the database.</span></span>  
  
 <span data-ttu-id="334b3-119">断开连接的服务器实例将保存其在会话中的最新角色。</span><span class="sxs-lookup"><span data-stu-id="334b3-119">A disconnected server instance saves its most recent role in the session.</span></span> <span data-ttu-id="334b3-120">通常，断开连接的服务器实例将在重新启动并重新获得仲裁时重新连接到会话。</span><span class="sxs-lookup"><span data-stu-id="334b3-120">Typically, a disconnected server instance reconnects to the session when it restarts and regains quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="334b3-121">只有在需要使用具有自动故障转移功能的高安全性模式时，才应设置见证服务器。</span><span class="sxs-lookup"><span data-stu-id="334b3-121">The witness should be set only when you intend to use high-safety mode with automatic failover.</span></span> <span data-ttu-id="334b3-122">在高性能模式下，由于从不需要见证服务器，因此极力建议将 WITNESS 属性设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="334b3-122">In high-performance mode, for which a witness is never required, we strongly recommend setting the WITNESS property to OFF.</span></span> <span data-ttu-id="334b3-123">有关见证服务器对高性能模式影响的信息，请参阅 [数据库镜像运行模式](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="334b3-123">For information about the impact of a witness on high-performance mode, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="quorum-in-high-safety-mode-sessions"></a><span data-ttu-id="334b3-124">高安全性模式会话中的仲裁</span><span class="sxs-lookup"><span data-stu-id="334b3-124">Quorum in High-Safety Mode Sessions</span></span>  
 <span data-ttu-id="334b3-125">在高安全性模式下，仲裁通过提供上下文来允许自动故障转移，在这个上下文中，具有仲裁的服务器实例可以判定哪个伙伴拥有主体服务器角色。</span><span class="sxs-lookup"><span data-stu-id="334b3-125">In high-safety mode, quorum allows automatic failover by providing a context in which the server instances with quorum arbitrate which partner owns the role of principal.</span></span> <span data-ttu-id="334b3-126">主体服务器如果具有仲裁就可以操作数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-126">The principal server serves the database if it has quorum.</span></span> <span data-ttu-id="334b3-127">如果在同步的镜像服务器和见证服务器仍具有仲裁的时候主体服务器丢失仲裁，则会发生自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="334b3-127">If the principal server loses quorum when the synchronized mirror server and witness retain quorum, automatic failover occurs.</span></span>  
  
 <span data-ttu-id="334b3-128">高安全性模式的仲裁方案包括：</span><span class="sxs-lookup"><span data-stu-id="334b3-128">The quorum scenarios for high-safety mode are as follows:</span></span>  
  
-   <span data-ttu-id="334b3-129">包含伙伴双方和见证服务器的“完全仲裁  ”。</span><span class="sxs-lookup"><span data-stu-id="334b3-129">A *full quorum* that consists of both partners and the witness.</span></span>  
  
     <span data-ttu-id="334b3-130">所有三个服务器实例通常都参与三方仲裁，这称为完全仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-130">Ordinarily, all three server instances participate in a three-way quorum, called a *full quorum*.</span></span> <span data-ttu-id="334b3-131">使用完全仲裁，主体服务器和镜像服务器一直执行其各自的角色（除非发生手动故障转移）。</span><span class="sxs-lookup"><span data-stu-id="334b3-131">With a full quorum, the principal and mirror servers continue to perform their respective roles (unless manual failover occurs).</span></span>  
  
-   <span data-ttu-id="334b3-132">包含见证服务器和一个伙伴的见证服务器-伙伴仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-132">A *witness-to-partner quorum* that consists of the witness and either partner.</span></span>  
  
     <span data-ttu-id="334b3-133">如果因为其中一个伙伴丢失而中断伙伴之间的网络连接，则可能发生下列情况：</span><span class="sxs-lookup"><span data-stu-id="334b3-133">If the network connection between the partners is lost because one of the partners has been lost, the following cases are possible:</span></span>  
  
    -   <span data-ttu-id="334b3-134">镜像服务器丢失，主体服务器和见证服务器仍具有仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-134">The mirror server is lost, and the principal server and witness retain quorum.</span></span>  
  
         <span data-ttu-id="334b3-135">在这种情况下，主体服务器将数据库设置为 DISCONNECTED，并在镜像处于 SUSPENDED 状态的情况下运行。</span><span class="sxs-lookup"><span data-stu-id="334b3-135">In this case, the principal sets its database to DISCONNECTED and runs with mirroring in a SUSPENDED state.</span></span> <span data-ttu-id="334b3-136">（因为数据库当前尚未镜像，所以这称为公开运行。）镜像服务器重新联接会话时，它将作为镜像服务器重新获得仲裁，并开始与其数据库副本重新同步。</span><span class="sxs-lookup"><span data-stu-id="334b3-136">(This is referred to as *running exposed*, because the database is currently not being mirrored.) When the mirror server rejoins the session, the server regains quorum as mirror and starts resynchronizing its copy of the database.</span></span>  
  
    -   <span data-ttu-id="334b3-137">主体服务器丢失，见证服务器和镜像服务器仍具有仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-137">The principal server is lost, and the witness and the mirror server retain quorum.</span></span>  
  
         <span data-ttu-id="334b3-138">在这种情况下，发生自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="334b3-138">In this case, automatic failover occurs.</span></span> <span data-ttu-id="334b3-139">有关详细信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="334b3-139">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
    -   <span data-ttu-id="334b3-140">所有服务器实例都将失去仲裁，但随后镜像和见证服务器将重新连接。</span><span class="sxs-lookup"><span data-stu-id="334b3-140">All the server instances lose quorum, but subsequently the mirror and witness reconnect.</span></span> <span data-ttu-id="334b3-141">在此情况下将不提供数据库服务。</span><span class="sxs-lookup"><span data-stu-id="334b3-141">The database will not be served in this case.</span></span>  
  
     <span data-ttu-id="334b3-142">两个伙伴与见证服务器之间保持连接时，故障转移伙伴之间的网络连接很少会断开。</span><span class="sxs-lookup"><span data-stu-id="334b3-142">Rarely, the network connection between failover partners is lost while both partners remain connected to the witness.</span></span> <span data-ttu-id="334b3-143">在这种情况下，存在两个分开的见证服务器-伙伴仲裁，见证服务器作为连接。</span><span class="sxs-lookup"><span data-stu-id="334b3-143">In this event, two, separate witness-to-partner quorums exist, with the witness as a liaison.</span></span> <span data-ttu-id="334b3-144">见证服务器将通知镜像服务器：主体服务器仍在连接状态。</span><span class="sxs-lookup"><span data-stu-id="334b3-144">The witness informs the mirror server that the principal server is still connected.</span></span> <span data-ttu-id="334b3-145">因此，不会出现自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="334b3-145">Therefore, automatic failover does not occur.</span></span> <span data-ttu-id="334b3-146">而镜像服务器将保留镜像角色并等待重新连接到主体服务器。</span><span class="sxs-lookup"><span data-stu-id="334b3-146">Instead, the mirror server retains the mirror role and waits to reconnect to the principal.</span></span> <span data-ttu-id="334b3-147">如果此时重做队列包含日志记录，镜像服务器将继续前滚镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-147">If the redo queue contains log records at this point, the mirror server continues to roll forward the mirror database.</span></span> <span data-ttu-id="334b3-148">重新连接后，镜像服务器将与镜像数据库重新同步。</span><span class="sxs-lookup"><span data-stu-id="334b3-148">On reconnecting, the mirror server will resynchronize the mirror database.</span></span>  
  
-   <span data-ttu-id="334b3-149">包含伙伴双方的伙伴-伙伴仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-149">A *partner-to-partner quorum* that consists of the two partners.</span></span>  
  
     <span data-ttu-id="334b3-150">只要伙伴仍具有仲裁，数据库就会继续处于 SYNCHRONIZED 状态，手动故障转移就可以进行。</span><span class="sxs-lookup"><span data-stu-id="334b3-150">As long as the partners retain quorum, the database continues in a SYNCHRONIZED state, and manual failover remains possible.</span></span> <span data-ttu-id="334b3-151">如果没有见证服务器，则无法使用自动故障转移功能；但当见证服务器重新获得仲裁时，会话将恢复正常操作，并重新支持自动故障转移。</span><span class="sxs-lookup"><span data-stu-id="334b3-151">Without the witness, automatic failover is not possible; but when the witness regains quorum, the session resumes regular operation, and automatic failover is supported again.</span></span>  
  
-   <span data-ttu-id="334b3-152">会话丢失仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-152">The session loses quorum.</span></span>  
  
     <span data-ttu-id="334b3-153">如果所有服务器实例此间的连接断开，就称为会话“丢失仲裁 ”。</span><span class="sxs-lookup"><span data-stu-id="334b3-153">If all the server instances become disconnected from each other, the session is said to have *lost quorum*.</span></span> <span data-ttu-id="334b3-154">当服务器实例恢复彼此间的连接时，它们将重新获得相互仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-154">As server instances reconnect to each other, they regain quorum with each other.</span></span>  
  
    -   <span data-ttu-id="334b3-155">如果主体服务器与其他服务器实例中的任何一个重新连接，即可使用数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-155">If the principal server reconnects with either of the other server instances, the database becomes available.</span></span>  
  
    -   <span data-ttu-id="334b3-156">如果主体服务器依旧断开连接，但镜像服务器和见证服务器恢复了相互之间的连接，则不能进行自动故障转移，因为可能会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="334b3-156">If the principal server remains disconnected, but the mirror and witness reconnect to each other, automatic failover cannot occur because data loss might occur.</span></span> <span data-ttu-id="334b3-157">因此，在主体服务器重新加入会话之前，依旧不能使用数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-157">Therefore, the database remains unavailable, until the principal server rejoins the session.</span></span>  
  
    -   <span data-ttu-id="334b3-158">当三个服务器实例全部恢复连接时，将重新获得完全仲裁，会话将恢复其正常操作。</span><span class="sxs-lookup"><span data-stu-id="334b3-158">When all three server instances have reconnected, full quorum is regained, and the session resumes its regular operation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="334b3-159">当会话具有伙伴-伙伴仲裁时，如果任一伙伴失去仲裁，会话将失去仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-159">When a session has a partner-to-partner quorum, if either partner loses quorum, the session loses quorum.</span></span> <span data-ttu-id="334b3-160">因此，如果您希望见证服务器在很长一段时间内保持断开，我们建议您暂时将见证服务器从会话中删除。</span><span class="sxs-lookup"><span data-stu-id="334b3-160">Therefore, if you expect the witness to remain disconnected for lots of time, we recommend that you temporarily remove the witness from the session.</span></span> <span data-ttu-id="334b3-161">如果删除见证服务器，则不再需要仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-161">Removing the witness removes the requirement for quorum.</span></span> <span data-ttu-id="334b3-162">然后，如果镜像服务器断开连接，则主体服务器可以继续操作数据库。</span><span class="sxs-lookup"><span data-stu-id="334b3-162">Then, if the mirror server becomes disconnected, the principal server can continue to serve the database.</span></span> <span data-ttu-id="334b3-163">有关如何添加或删除见证服务器的信息，请参阅 [Database Mirroring Witness](database-mirroring-witness.md)。</span><span class="sxs-lookup"><span data-stu-id="334b3-163">For information about how to add or remove a witness, see [Database Mirroring Witness](database-mirroring-witness.md).</span></span>  
  
### <a name="how-quorum-affects-database-availability"></a><span data-ttu-id="334b3-164">仲裁如何影响数据库可用性</span><span class="sxs-lookup"><span data-stu-id="334b3-164">How Quorum Affects Database Availability</span></span>  
 <span data-ttu-id="334b3-165">下图显示的是见证服务器与伙伴如何相互作用，以确保在给定时间内，只有一个伙伴拥有主体服务器角色并且只有当前主体服务器才能使其数据库联机。</span><span class="sxs-lookup"><span data-stu-id="334b3-165">The following illustration shows how the witness and the partners cooperate to make sure that, at given time, only one partner owns the role of principal and only the current principal server can bring its database online.</span></span> <span data-ttu-id="334b3-166">两个方案都以完全仲裁（ **Partner_A** 具有主体角色， **Partner_B** 具有镜像角色）为起点。</span><span class="sxs-lookup"><span data-stu-id="334b3-166">Both scenarios start with full quorum, and **Partner_A** in the principal role and **Partner_B** in the mirror role.</span></span>  
  
 <span data-ttu-id="334b3-167">![见证服务器与伙伴的协作方式](../media/dbm-quorum-scenarios.gif "见证服务器与伙伴的协作方式")</span><span class="sxs-lookup"><span data-stu-id="334b3-167">![How the witness and partners cooperate](../media/dbm-quorum-scenarios.gif "How the witness and partners cooperate")</span></span>  
  
 <span data-ttu-id="334b3-168">方案 1 显示的是：在原始主体服务器 (**Partner_A**) 失败后，见证服务器和镜像服务器如何同时认定主体 **Partner_A**不再可用并构成仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-168">Scenario 1 shows how after the original principal server (**Partner_A**) fails, the witness and mirror agree that the principal, **Partner_A**, is not available any longer and form quorum.</span></span> <span data-ttu-id="334b3-169">然后，镜像服务器 **Partner_B** 承担主体角色。</span><span class="sxs-lookup"><span data-stu-id="334b3-169">The mirror, **Partner_B** then assumes the principal role.</span></span> <span data-ttu-id="334b3-170">出现自动故障转移时， **Partner_B**使其数据库副本联机。</span><span class="sxs-lookup"><span data-stu-id="334b3-170">Automatic failover occurs, and **Partner_B**, brings its copy of the database online.</span></span> <span data-ttu-id="334b3-171">然后 **Partner_B** 出现故障，数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="334b3-171">Then **Partner_B** goes down, and the database goes offline.</span></span> <span data-ttu-id="334b3-172">随后，先前的主体服务器 **Partner_A**重新连接到见证服务器重新获取仲裁，但是通过与见证服务器通信， **Partner_A** 获知不能使其数据库副本联机，因为 **Partner_B** 现在拥有主体角色。</span><span class="sxs-lookup"><span data-stu-id="334b3-172">Later, the former principal server, **Partner_A**, reconnects to the witness regaining quorum, but on communicating with the witness, **Partner_A** learns that it cannot bring its copy of the database online, because **Partner_B** now owns the principal role.</span></span> <span data-ttu-id="334b3-173">当 **Partner_B** 重新加入会话时，将使数据库恢复联机。</span><span class="sxs-lookup"><span data-stu-id="334b3-173">When **Partner_B** rejoins the session, it brings the database back online.</span></span>  
  
 <span data-ttu-id="334b3-174">在方案 2 中，见证服务器丢失仲裁，而伙伴 **Partner_A** 和 **Partner_B**彼此保留仲裁，数据库保持联机。</span><span class="sxs-lookup"><span data-stu-id="334b3-174">In Scenario 2, the witness loses quorum, while the partners, **Partner_A** and **Partner_B**, retain quorum with each other, and the database remains online.</span></span> <span data-ttu-id="334b3-175">然后，伙伴们也失去其仲裁，数据库处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="334b3-175">Then the partners lose their quorum, too, and the database goes offline.</span></span> <span data-ttu-id="334b3-176">随后，主体服务器 **Partner_A**重新连接到见证服务器以重新获取仲裁。</span><span class="sxs-lookup"><span data-stu-id="334b3-176">Later, the principal server, **Partner_A**, reconnects to the witness regaining quorum.</span></span> <span data-ttu-id="334b3-177">见证服务器确认 **Partner_A** 仍拥有主体角色，并且 **Partner_A** 使数据库恢复联机。</span><span class="sxs-lookup"><span data-stu-id="334b3-177">The witness confirms that **Partner_A** still owns the principal role, and **Partner_A** brings the database back online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334b3-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="334b3-178">See Also</span></span>  
 <span data-ttu-id="334b3-179">[数据库镜像运行模式](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="334b3-179">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="334b3-180">[数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="334b3-180">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="334b3-181">[数据库镜像见证服务器](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="334b3-181">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="334b3-182">[数据库镜像期间可能出现的故障](possible-failures-during-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="334b3-182">[Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md) </span></span>  
 [<span data-ttu-id="334b3-183">镜像状态 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="334b3-183">Mirroring States &#40;SQL Server&#41;</span></span>](mirroring-states-sql-server.md)  
  
  
