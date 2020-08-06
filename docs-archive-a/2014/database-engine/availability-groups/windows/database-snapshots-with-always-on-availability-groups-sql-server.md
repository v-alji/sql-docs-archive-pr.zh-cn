---
title: SQL Server) 的 AlwaysOn 可用性组 (数据库快照 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 7432da1c-ce2f-4cd9-af41-54c97744166b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1e4307653b5b8150d71019a373ee073d15123f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691877"
---
# <a name="database-snapshots-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="a5f66-102">含有 AlwaysOn 可用性组的数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a5f66-102">Database Snapshots with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="a5f66-103">您可在可用性组中的主数据库或辅助数据库上创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="a5f66-103">You can create a database snapshot on an primary or secondary database in an availability group.</span></span> <span data-ttu-id="a5f66-104">副本角色必须是 PRIMARY 或 SECONDARY，且不处于 RESOLVING 状态。</span><span class="sxs-lookup"><span data-stu-id="a5f66-104">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
 <span data-ttu-id="a5f66-105">当您创建一个数据库快照时，我们建议数据库同步状态是 SYNCHRONIZING 或 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="a5f66-105">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="a5f66-106">但是，当数据库同步状态为 NOT SYNCHRONIZING 时，可以创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="a5f66-106">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
 <span data-ttu-id="a5f66-107">如果辅助副本断开与主副本的连接，则该辅助副本上的数据库快照应该继续工作。</span><span class="sxs-lookup"><span data-stu-id="a5f66-107">A database snapshot on a secondary replica should continue to work if the replica is DISCONNECTED from the primary replica.</span></span>  
  
 <span data-ttu-id="a5f66-108">某些 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 情况会导致源数据库及其数据库快照重新启动，暂时断开用户连接。</span><span class="sxs-lookup"><span data-stu-id="a5f66-108">Some [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] conditions cause both the source database and its database snapshots to be restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="a5f66-109">这些情况如下所示：</span><span class="sxs-lookup"><span data-stu-id="a5f66-109">These conditions are as follows:</span></span>  
  
-   <span data-ttu-id="a5f66-110">主副本更改角色，无论是因为当前主副本脱机并且在同一服务器实例上恢复联机状态，还是因为可用性组故障转移。</span><span class="sxs-lookup"><span data-stu-id="a5f66-110">The primary replica changes roles, whether because the current primary replica goes off line and comes back online on the same server instance or because the availability group fails over.</span></span>  
  
-   <span data-ttu-id="a5f66-111">数据库进入辅助角色。</span><span class="sxs-lookup"><span data-stu-id="a5f66-111">The database enters the secondary role.</span></span>  
  
 <span data-ttu-id="a5f66-112">如果承载数据库快照的可用性副本故障转移，则该数据库快照将保留在创建了这些快照的服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="a5f66-112">If the availability replica that hosts database snapshots is failed over, the database snapshots remain on the server instance where they were created.</span></span> <span data-ttu-id="a5f66-113">用户可以在故障转移后继续使用快照。如果性能是您的环境中的关注点，我们建议您仅在配置为手动故障转移模式的辅助副本承载的辅助数据库上创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="a5f66-113">Users can continue to use the snapshots after the failover.If performance is a concern in your environment, we recommend that you create database snapshots only on secondary databases that are hosted by a secondary replica that is configured for manual failover mode.</span></span>  <span data-ttu-id="a5f66-114">如果您曾经将可用性组手动故障转移到此辅助副本，则可以在其他辅助副本上创建一组新的数据库快照，将客户端重定向到这些新的数据库快照，并且从新的主数据库上删除所有数据库快照。</span><span class="sxs-lookup"><span data-stu-id="a5f66-114">If you ever manually fail over the availability group to this secondary replica, you can create a new set of database snapshots on another secondary replica, redirect clients to the new database snapshots, and drop all of the database snapshots from the now primary databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f66-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5f66-115">See Also</span></span>  
 <span data-ttu-id="a5f66-116">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a5f66-116">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a5f66-117">数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a5f66-117">Database Snapshots &#40;SQL Server&#41;</span></span>](../../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
