---
title: 数据库镜像和数据库快照 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- snapshots [SQL Server database snapshots], database mirroring
- database snapshots [SQL Server], database mirroring
ms.assetid: 0bf1be90-7ce4-484c-aaa7-f8a782f57c5f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9df0b74270280bf2315c6a35a80d4b009b75a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579767"
---
# <a name="database-mirroring-and-database-snapshots-sql-server"></a><span data-ttu-id="db26d-102">数据库镜像和数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db26d-102">Database Mirroring and Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="db26d-103">可以利用为了实现可用性目标而维护的镜像数据库来减轻报表的负载。</span><span class="sxs-lookup"><span data-stu-id="db26d-103">You can take advantage of a mirror database that you are maintaining for availability purposes to offload reporting.</span></span> <span data-ttu-id="db26d-104">若要将镜像数据库用于报表，可以在镜像数据库中创建数据库快照，并将客户端连接请求定向到最新的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-104">To use a mirror database for reporting, you can create a database snapshot on the mirror database and direct client connection requests to the most recent snapshot.</span></span> <span data-ttu-id="db26d-105">由于数据库快照只在创建快照时存在，因此，它是一个静态的、只读的并与其源数据库保持事务一致的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-105">A database snapshot is a static, read-only, transaction-consistent snapshot of its source database as it existed at the moment of the snapshot's creation.</span></span> <span data-ttu-id="db26d-106">若要在镜像数据库中创建数据库快照，数据库必须处于同步镜像状态。</span><span class="sxs-lookup"><span data-stu-id="db26d-106">To create a database snapshot on a mirror database, the database must be in the synchronized mirroring state.</span></span>  
  
 <span data-ttu-id="db26d-107">与镜像数据库本身不同，客户端可以访问数据库快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-107">Unlike the mirror database itself, a database snapshot is accessible to clients.</span></span> <span data-ttu-id="db26d-108">只要镜像服务器与主体服务器进行通信，就可以将报表客户端连接定向到快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-108">As long as the mirror server is communicating with the principal server, you can direct reporting clients to connect to a snapshot.</span></span> <span data-ttu-id="db26d-109">注意，由于数据库快照是静态的，因此没有新数据可用。</span><span class="sxs-lookup"><span data-stu-id="db26d-109">Note that because a database snapshot is static, new data is not available.</span></span> <span data-ttu-id="db26d-110">为了让用户能够使用相对较新的数据，必须定期创建新的数据库快照，并通过应用程序将传入客户端连接定向到最新的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-110">To make relatively recent data available to your users, you must create a new database snapshot periodically and have applications direct incoming client connections to the newest snapshot.</span></span>  
  
 <span data-ttu-id="db26d-111">新的数据库快照几乎是空的，但是它会随着越来越多的数据页的首次更新而增长。</span><span class="sxs-lookup"><span data-stu-id="db26d-111">A new database snapshot is almost empty, but it grows over time as more and more database pages are updated for the first time.</span></span> <span data-ttu-id="db26d-112">由于数据库中的每个快照都以这种方式增长，因此，每个数据库快照与常规数据库使用同样多的资源。</span><span class="sxs-lookup"><span data-stu-id="db26d-112">Because every snapshot on a database grows incrementally in this way, each database snapshot consumes as much resources as a normal database.</span></span> <span data-ttu-id="db26d-113">根据镜像服务器和主体服务器的配置，在镜像数据库中保留过多的数据库快照可能会降低主体数据库的性能。</span><span class="sxs-lookup"><span data-stu-id="db26d-113">Depending on the configurations of the mirror server and principal server, having an excessive number of database snapshots on a mirror database might decrease performance on the principal database.</span></span> <span data-ttu-id="db26d-114">因此，我们建议在镜像数据库中仅保留少量相对较新的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-114">Therefore, we recommend that you keep only a few relatively recent snapshots on your mirror databases.</span></span> <span data-ttu-id="db26d-115">一般情况下，在创建替换快照之后，应重新将传入查询定向到新的快照，并在完成所有当前的查询之后删除较早的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-115">Typically, after you create a replacement snapshot, you should redirect incoming queries to the new snapshot and drop the earlier snapshot after any current queries complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db26d-116">有关数据库快照的详细信息，请参阅 [数据库快照 (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db26d-116">For more information about database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).</span></span>  
  
 <span data-ttu-id="db26d-117">如果出现角色切换，则数据库及其快照将重新启动并暂时断开与用户的连接。</span><span class="sxs-lookup"><span data-stu-id="db26d-117">If role switching occurs, the database and its snapshots are restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="db26d-118">然后，数据库快照保留在创建时所在的服务器实例中，并成为新的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="db26d-118">Afterwards, the database snapshots remain on the server instance where they were created, which has become the new principal database.</span></span> <span data-ttu-id="db26d-119">用户可以在故障转移后继续使用快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-119">Users can continue to use the snapshots after the failover.</span></span> <span data-ttu-id="db26d-120">但是，这样会给新的主体服务器带来额外的负荷。</span><span class="sxs-lookup"><span data-stu-id="db26d-120">However, this places an additional load on the new principal server.</span></span> <span data-ttu-id="db26d-121">如果在您的环境中性能是一个关注点，则我们建议您应在新镜像数据库成为可用后，在其中创建快照，并将客户端重新定向到新快照，同时从以前的镜像数据库中删除所有数据库快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-121">If performance is a concern in your environment, we recommend that you create a snapshot on the new mirror database when it becomes available, redirect clients to the new snapshot, and drop all of the database snapshots from the former mirror database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db26d-122">对于能很好地向外扩展的专用报告解决方案，可以考虑复制。</span><span class="sxs-lookup"><span data-stu-id="db26d-122">For a dedicated reporting solution that scales out well, consider replication.</span></span> <span data-ttu-id="db26d-123">有关详细信息，请参阅 [SQL Server Replication](../install-windows/install-sql-server-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="db26d-123">For more information, see [SQL Server Replication](../install-windows/install-sql-server-replication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db26d-124">示例</span><span class="sxs-lookup"><span data-stu-id="db26d-124">Example</span></span>  
 <span data-ttu-id="db26d-125">下面的示例将对镜像数据库创建快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-125">This example creates snapshots on a mirrored database.</span></span>  
  
 <span data-ttu-id="db26d-126">假定数据库镜像会话的数据库为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="db26d-126">Assume that the database of a database mirroring session is [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="db26d-127">此示例在 `AdventureWorks` 数据库（位于驱动器 `F` 中）的镜像副本中创建了三个数据库快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-127">This example creates three database snapshots on the mirror copy of the `AdventureWorks` database, which resides on the `F` drive.</span></span> <span data-ttu-id="db26d-128">分别将这些快照命名为 `AdventureWorks_0600`、 `AdventureWorks_1200`和 `AdventureWorks_1800` ，以标识它们的近似创建次数。</span><span class="sxs-lookup"><span data-stu-id="db26d-128">The snapshots are named `AdventureWorks_0600`, `AdventureWorks_1200`, and `AdventureWorks_1800` to identify their approximate creation times.</span></span>  
  
1.  <span data-ttu-id="db26d-129">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的镜像中创建第一个数据库快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-129">Create the first database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_0600  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_0600.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
2.  <span data-ttu-id="db26d-130">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的镜像中创建第二个数据库快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-130">Create the second database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="db26d-131">仍在使用 `AdventureWorks_0600` 的用户可以继续使用它。</span><span class="sxs-lookup"><span data-stu-id="db26d-131">Users who are still using `AdventureWorks_0600` can continue to use it.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1200  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1200.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="db26d-132">此时，可以用编程的方式将新客户端连接定向至最新的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-132">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
3.  <span data-ttu-id="db26d-133">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的镜像中创建第三个快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-133">Create the third snapshot on the mirror [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="db26d-134">仍在使用 `AdventureWorks_0600` 或 `AdventureWorks_1200` 的用户可以继续使用它们。</span><span class="sxs-lookup"><span data-stu-id="db26d-134">Users who are still using `AdventureWorks_0600` or `AdventureWorks_1200` can continue to use them.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1800  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1800.SNP')  
        AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="db26d-135">此时，可以用编程的方式将新客户端连接定向至最新的快照。</span><span class="sxs-lookup"><span data-stu-id="db26d-135">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="db26d-136">相关任务</span><span class="sxs-lookup"><span data-stu-id="db26d-136">Related Tasks</span></span>  
  
-   [<span data-ttu-id="db26d-137">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db26d-137">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="db26d-138">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db26d-138">View a Database Snapshot &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="db26d-139">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db26d-139">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  

  
## <a name="see-also"></a><span data-ttu-id="db26d-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db26d-140">See Also</span></span>  
 <span data-ttu-id="db26d-141">[数据库快照 (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db26d-141">[Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span></span>  
 [<span data-ttu-id="db26d-142">将客户端连接到数据库镜像会话 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db26d-142">Connect Clients to a Database Mirroring Session &#40;SQL Server&#41;</span></span>](connect-clients-to-a-database-mirroring-session-sql-server.md)  
  
  
