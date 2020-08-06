---
title: 数据库快照 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- static database views
- snapshots [SQL Server database snapshots]
- source databases [SQL Server]
- snapshots [SQL Server database snapshots], about database snapshots
- database snapshots [SQL Server]
- read-only database views
- database snapshots [SQL Server], about database snapshots
ms.assetid: 00179314-f23e-47cb-a35c-da6f180f86d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a0fa9b6cee2287d4e6060d4cb39f34d909e7db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693945"
---
# <a name="database-snapshots-sql-server"></a><span data-ttu-id="70f1c-102">数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70f1c-102">Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="70f1c-103">数据库快照是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库（源数据库）的只读静态视图。</span><span class="sxs-lookup"><span data-stu-id="70f1c-103">A database snapshot is a read-only, static view of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database (the *source database*).</span></span> <span data-ttu-id="70f1c-104">自创建快照那刻起，数据库快照在事务上与源数据库一致。</span><span class="sxs-lookup"><span data-stu-id="70f1c-104">The database snapshot is transactionally consistent with the source database as of the moment of the snapshot's creation.</span></span> <span data-ttu-id="70f1c-105">数据库快照始终与其源数据库位于同一服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="70f1c-105">A database snapshot always resides on the same server instance as its source database.</span></span> <span data-ttu-id="70f1c-106">当源数据库更新时，数据库快照也将更新。</span><span class="sxs-lookup"><span data-stu-id="70f1c-106">As the source database is updated, the database snapshot is updated.</span></span> <span data-ttu-id="70f1c-107">因此，数据库快照存在的时间越长，就越有可能用完其可用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="70f1c-107">Therefore, the longer a database snapshot exists, the more likely it is to use up its available disk space.</span></span>  
  
 <span data-ttu-id="70f1c-108">给定源数据库中可以存在多个快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-108">Multiple snapshots can exist on a given source database.</span></span> <span data-ttu-id="70f1c-109">在数据库所有者显式删除每个数据库快照之前，该快照将一直保留。</span><span class="sxs-lookup"><span data-stu-id="70f1c-109">Each database snapshot persists until it is explicitly dropped by the database owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f1c-110">数据库快照与快照备份、事务的快照隔离或快照复制无关。</span><span class="sxs-lookup"><span data-stu-id="70f1c-110">Database snapshots are unrelated to snapshot backups, snapshot isolation of transactions, or snapshot replication.</span></span>  
  
 <span data-ttu-id="70f1c-111">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="70f1c-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="70f1c-112">功能概述</span><span class="sxs-lookup"><span data-stu-id="70f1c-112">Feature Overview</span></span>](#FeatureOverview)  
  
-   [<span data-ttu-id="70f1c-113">数据库快照的优点</span><span class="sxs-lookup"><span data-stu-id="70f1c-113">Benefits of Database Snapshots</span></span>](#Benefits)  
  
-   [<span data-ttu-id="70f1c-114">术语和定义</span><span class="sxs-lookup"><span data-stu-id="70f1c-114">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="70f1c-115">数据库快照的先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-115">Prerequisites for and Limitations on Database Snapshots</span></span>](#LimitationsRequirements)  
  
-   [<span data-ttu-id="70f1c-116">相关任务</span><span class="sxs-lookup"><span data-stu-id="70f1c-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="feature-overview"></a><a name="FeatureOverview"></a> <span data-ttu-id="70f1c-117">功能概述</span><span class="sxs-lookup"><span data-stu-id="70f1c-117">Feature Overview</span></span>  
 <span data-ttu-id="70f1c-118">数据库快照在数据页级运行。</span><span class="sxs-lookup"><span data-stu-id="70f1c-118">Database snapshots operate at the data-page level.</span></span> <span data-ttu-id="70f1c-119">在第一次修改源数据库页之前，先将原始页从源数据库复制到快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-119">Before a page of the source database is modified for the first time, the original page is copied from the source database to the snapshot.</span></span> <span data-ttu-id="70f1c-120">快照将存储原始页，保留它们在创建快照时的数据记录。</span><span class="sxs-lookup"><span data-stu-id="70f1c-120">The snapshot stores the original page, preserving the data records as they existed when the snapshot was created.</span></span> <span data-ttu-id="70f1c-121">对要进行第一次修改的每一页重复此过程。</span><span class="sxs-lookup"><span data-stu-id="70f1c-121">The same process is repeated for every page that is being modified for the first time.</span></span> <span data-ttu-id="70f1c-122">对于用户而言，数据库快照似乎始终保持不变，因为对数据库快照的读操作始终访问原始数据页，而与页驻留的位置无关。</span><span class="sxs-lookup"><span data-stu-id="70f1c-122">To the user, a database snapshot appears never to change, because read operations on a database snapshot always access the original data pages, regardless of where they reside.</span></span>  
  
 <span data-ttu-id="70f1c-123">为了存储复制的原始页，快照使用一个或多个“稀疏文件” 。</span><span class="sxs-lookup"><span data-stu-id="70f1c-123">To store the copied original pages, the snapshot uses one or more *sparse files*.</span></span> <span data-ttu-id="70f1c-124">最初，稀疏文件实质上是空文件，不包含用户数据并且未被分配存储用户数据的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="70f1c-124">Initially, a sparse file is an essentially empty file that contains no user data and has not yet been allocated disk space for user data.</span></span> <span data-ttu-id="70f1c-125">随着源数据库中更新的页越来越多，文件的大小也不断增长。</span><span class="sxs-lookup"><span data-stu-id="70f1c-125">As more and more pages are updated in the source database, the size of the file grows.</span></span> <span data-ttu-id="70f1c-126">下图说明了两种相对的更新模式对快照大小的影响。</span><span class="sxs-lookup"><span data-stu-id="70f1c-126">The following figure illustrates the effects of two contrasting update patterns on the size of a snapshot.</span></span> <span data-ttu-id="70f1c-127">更新模式 A 反映的是在快照使用期限内仅有 30% 的原始页更新的环境。</span><span class="sxs-lookup"><span data-stu-id="70f1c-127">Update pattern A reflects an environment in which only 30 percent of the original pages are updated during the life of the snapshot.</span></span> <span data-ttu-id="70f1c-128">更新模式 B 反映的是在快照使用期限内有 80% 的原始页更新的环境。</span><span class="sxs-lookup"><span data-stu-id="70f1c-128">Update pattern B reflects an environment in which 80 percent of the original pages are updated during the life of the snapshot.</span></span>  
  
 <span data-ttu-id="70f1c-129">![备用更新模式和快照大小](../../database-engine/media/dbview-04.gif "备用更新模式和快照大小")</span><span class="sxs-lookup"><span data-stu-id="70f1c-129">![Alternative update patterns and snapshot size](../../database-engine/media/dbview-04.gif "Alternative update patterns and snapshot size")</span></span>  
  
##  <a name="benefits-of-database-snapshots"></a><a name="Benefits"></a> <span data-ttu-id="70f1c-130">数据库快照的优点</span><span class="sxs-lookup"><span data-stu-id="70f1c-130">Benefits of Database Snapshots</span></span>  
  
-   <span data-ttu-id="70f1c-131">快照可用于报告目的。</span><span class="sxs-lookup"><span data-stu-id="70f1c-131">Snapshots can be used for reporting purposes.</span></span>  
  
     <span data-ttu-id="70f1c-132">客户端可以查询数据库快照，这对于基于创建快照时的数据编写报表是很有用的。</span><span class="sxs-lookup"><span data-stu-id="70f1c-132">Clients can query a database snapshot, which makes it useful for writing reports based on the data at the time of snapshot creation.</span></span>  
  
-   <span data-ttu-id="70f1c-133">维护历史数据以生成报表。</span><span class="sxs-lookup"><span data-stu-id="70f1c-133">Maintaining historical data for report generation.</span></span>  
  
     <span data-ttu-id="70f1c-134">快照可以从特定时点扩展用户对数据的访问权限。</span><span class="sxs-lookup"><span data-stu-id="70f1c-134">A snapshot can extend user access to data from a particular point in time.</span></span> <span data-ttu-id="70f1c-135">例如，您可以在给定时间段（例如，财务季度）要结束的时候创建数据库快照以便日后制作报表。</span><span class="sxs-lookup"><span data-stu-id="70f1c-135">For example, you can create a database snapshot at the end of a given time period (such as a financial quarter) for later reporting.</span></span> <span data-ttu-id="70f1c-136">然后便可以在快照上运行期间要结束时创建的报表。</span><span class="sxs-lookup"><span data-stu-id="70f1c-136">You can then run end-of-period reports on the snapshot.</span></span> <span data-ttu-id="70f1c-137">如果磁盘空间允许，还可以维护任意多个不同期间要结束时的快照，以便能够对这些时间段的结果进行查询。例如，调查单位性能。</span><span class="sxs-lookup"><span data-stu-id="70f1c-137">If disk space permits, you can also maintain end-of-period snapshots indefinitely, allowing queries against the results from these periods; for example, to investigate organizational performance.</span></span>  
  
-   <span data-ttu-id="70f1c-138">使用为了实现可用性目标而维护的镜像数据库来减轻报表负载。</span><span class="sxs-lookup"><span data-stu-id="70f1c-138">Using a mirror database that you are maintaining for availability purposes to offload reporting.</span></span>  
  
     <span data-ttu-id="70f1c-139">使用带有数据库镜像的数据库快照，使您能够访问镜像服务器上的数据以生成报表。</span><span class="sxs-lookup"><span data-stu-id="70f1c-139">Using database snapshots with database mirroring permits you to make the data on the mirror server accessible for reporting.</span></span> <span data-ttu-id="70f1c-140">而且，在镜像数据库上运行查询可以释放主体数据库上的资源。</span><span class="sxs-lookup"><span data-stu-id="70f1c-140">Additionally, running queries on the mirror database can free up resources on the principal.</span></span> <span data-ttu-id="70f1c-141">有关详细信息，请参阅 [数据库镜像和数据库快照 (SQL Server)](database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70f1c-141">For more information, see [Database Mirroring and Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
-   <span data-ttu-id="70f1c-142">使数据免受管理失误所带来的影响。</span><span class="sxs-lookup"><span data-stu-id="70f1c-142">Safeguarding data against administrative error.</span></span>  
  
-   <span data-ttu-id="70f1c-143">如果源数据库上出现用户错误，您可将源数据库恢复到创建给定数据库快照时的状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-143">In the event of a user error on a source database, you can revert the source database to the state it was in when a given database snapshot was created.</span></span> <span data-ttu-id="70f1c-144">丢失的数据仅限于创建快照后数据库更新的数据。</span><span class="sxs-lookup"><span data-stu-id="70f1c-144">Data loss is confined to updates to the database since the snapshot's creation.</span></span>  
  
     <span data-ttu-id="70f1c-145">例如，在进行重大更新（比如大容量更新或架构更改）前，对数据库创建数据库快照以保护数据。</span><span class="sxs-lookup"><span data-stu-id="70f1c-145">For example, before doing major updates, such as a bulk update or a schema change, create a database snapshot on the database protects data.</span></span> <span data-ttu-id="70f1c-146">一旦进行了错误操作，可以使用快照将数据库恢复到生成快照时的状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-146">If you make a mistake, you can use the snapshot to recover by reverting the database to the snapshot.</span></span> <span data-ttu-id="70f1c-147">为此目的进行的恢复很可能比从备份还原快得多；但是，此后您无法对数据进行前滚操作。</span><span class="sxs-lookup"><span data-stu-id="70f1c-147">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="70f1c-148">无法对脱机或损坏的数据库进行恢复。</span><span class="sxs-lookup"><span data-stu-id="70f1c-148">Reverting does not work in an offline or corrupted database.</span></span> <span data-ttu-id="70f1c-149">因此，为了保护数据库，非常有必要定期执行备份并测试还原计划。</span><span class="sxs-lookup"><span data-stu-id="70f1c-149">Therefore, taking regular backups and testing your restore plan are necessary to protect a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70f1c-150">数据库快照与源数据库相关。</span><span class="sxs-lookup"><span data-stu-id="70f1c-150">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="70f1c-151">因此，使用数据库快照恢复数据库不能代替备份和还原策略。</span><span class="sxs-lookup"><span data-stu-id="70f1c-151">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="70f1c-152">严格按计划执行备份仍然至关重要。</span><span class="sxs-lookup"><span data-stu-id="70f1c-152">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="70f1c-153">如果必须将源数据库还原到创建数据库快照的时间点，请实施允许您执行该操作的备份策略。</span><span class="sxs-lookup"><span data-stu-id="70f1c-153">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="70f1c-154">使数据免受用户失误所带来的影响。</span><span class="sxs-lookup"><span data-stu-id="70f1c-154">Safeguarding data against user error.</span></span>  
  
     <span data-ttu-id="70f1c-155">定期创建数据库快照，可以减轻重大用户错误（例如，删除的表）的影响。</span><span class="sxs-lookup"><span data-stu-id="70f1c-155">By creating database snapshots on a regular basis, you can mitigate the impact of a major user error, such as a dropped table.</span></span> <span data-ttu-id="70f1c-156">为了很好地保护数据，可以创建时间跨度足以识别和处理大多数用户错误的一系列数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-156">For a high level of protection, you can create a series of database snapshots spanning enough time to recognize and respond to most user errors.</span></span> <span data-ttu-id="70f1c-157">例如，根据磁盘资源，可以每 24 小时创建 6 到 12 个滚动快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-157">For instance, you might maintain 6 to 12 rolling snapshots spanning a 24-hour interval, depending on your disk resources.</span></span> <span data-ttu-id="70f1c-158">每创建一个新的快照，就删除最早的快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-158">Then, each time a new snapshot is created, the earliest snapshot can be deleted.</span></span>  
  
    -   <span data-ttu-id="70f1c-159">若要从用户错误中恢复，可以将数据库恢复到在错误发生的前一时刻的快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-159">To recover from a user error, you can revert the database to the snapshot immediately before the error.</span></span> <span data-ttu-id="70f1c-160">为此目的进行的恢复很可能比从备份还原快得多；但是，此后您无法对数据进行前滚操作。</span><span class="sxs-lookup"><span data-stu-id="70f1c-160">Reverting is potentially much faster for this purpose than restoring from a backup; however, you cannot roll forward afterward.</span></span>  
  
    -   <span data-ttu-id="70f1c-161">或者，也可以利用快照中的信息，手动重新创建删除的表或其他丢失的数据。</span><span class="sxs-lookup"><span data-stu-id="70f1c-161">Alternatively, you may be able to manually reconstruct a dropped table or other lost data from the information in a snapshot.</span></span> <span data-ttu-id="70f1c-162">例如，可以将快照中的数据大容量复制到数据库中，然后手动将数据合并回数据库中。</span><span class="sxs-lookup"><span data-stu-id="70f1c-162">For instance, you could bulk copy the data out of the snapshot into the database and manually merge the data back into the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70f1c-163">使用数据库快照的原因，决定了数据库需要多少个并发快照、多久创建一次新快照以及将其保留多久。</span><span class="sxs-lookup"><span data-stu-id="70f1c-163">Your reasons for using database snapshots determine how many concurrent snapshots you need on a database, how frequently to create a new snapshot, and how long to keep it.</span></span>  
  
-   <span data-ttu-id="70f1c-164">管理测试数据库</span><span class="sxs-lookup"><span data-stu-id="70f1c-164">Managing a test database</span></span>  
  
     <span data-ttu-id="70f1c-165">在测试环境中，当每一轮测试开始时针对要包含相同数据的数据库重复运行测试协议将十分有用。</span><span class="sxs-lookup"><span data-stu-id="70f1c-165">In a testing environment, it can be useful when repeatedly running a test protocol for the database to contain identical data at the start of each round of testing.</span></span> <span data-ttu-id="70f1c-166">在运行第一轮测试前，应用程序开发人员或测试人员可以在测试数据库中创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-166">Before running the first round, an application developer or tester can create a database snapshot on the test database.</span></span> <span data-ttu-id="70f1c-167">每次运行测试之后，数据库都可以通过恢复数据库快照快速返回到它以前的状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-167">After each test run, the database can be quickly returned to its prior state by reverting the database snapshot.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="70f1c-168">术语和定义</span><span class="sxs-lookup"><span data-stu-id="70f1c-168">Terms and Definitions</span></span>  
 <span data-ttu-id="70f1c-169">database snapshot</span><span class="sxs-lookup"><span data-stu-id="70f1c-169">database snapshot</span></span>  
 <span data-ttu-id="70f1c-170">一个数据库（源数据库）的事务一致的只读静态视图。</span><span class="sxs-lookup"><span data-stu-id="70f1c-170">A transactionally consistent, read-only, static view of a database (the source database).</span></span>  
  
 <span data-ttu-id="70f1c-171">源数据库 (source database)</span><span class="sxs-lookup"><span data-stu-id="70f1c-171">source database</span></span>  
 <span data-ttu-id="70f1c-172">对于数据库快照，指的是在其上创建快照的数据库。</span><span class="sxs-lookup"><span data-stu-id="70f1c-172">For a database snapshot, the database on which the snapshot was created.</span></span> <span data-ttu-id="70f1c-173">数据库快照与源数据库相关。</span><span class="sxs-lookup"><span data-stu-id="70f1c-173">Database snapshots are dependent on the source database.</span></span> <span data-ttu-id="70f1c-174">数据库快照必须与数据库在同一服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="70f1c-174">The snapshots of a database must be on the same server instance as the database.</span></span> <span data-ttu-id="70f1c-175">此外，如果数据库因某种原因而不可用，则它的所有数据库快照也将不可用。</span><span class="sxs-lookup"><span data-stu-id="70f1c-175">Furthermore, if that database becomes unavailable for any reason, all of its database snapshots also become unavailable.</span></span>  
  
 <span data-ttu-id="70f1c-176">稀疏文件 (sparse file)</span><span class="sxs-lookup"><span data-stu-id="70f1c-176">sparse file</span></span>  
 <span data-ttu-id="70f1c-177">NTFS 文件系统提供的文件，需要的磁盘空间要比其他文件格式少很多。</span><span class="sxs-lookup"><span data-stu-id="70f1c-177">A file provided by the NTFS file system that requires much less disk space than would otherwise be needed.</span></span> <span data-ttu-id="70f1c-178">稀疏文件用于存储复制到数据库快照的页面。</span><span class="sxs-lookup"><span data-stu-id="70f1c-178">A sparse file is used to store pages copied to a database snapshot.</span></span> <span data-ttu-id="70f1c-179">首次创建稀疏文件时，稀疏文件占用的磁盘空间非常少。</span><span class="sxs-lookup"><span data-stu-id="70f1c-179">When first created, a sparse file takes up little disk space.</span></span> <span data-ttu-id="70f1c-180">随着数据写入数据库快照，NTFS 会将磁盘空间逐渐分配给相应的稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="70f1c-180">As data is written to a database snapshot, NTFS allocates disk space gradually to the corresponding sparse file.</span></span>  
  
##  <a name="prerequisites-for-and-limitations-on-database-snapshots"></a><a name="LimitationsRequirements"></a> <span data-ttu-id="70f1c-181">数据库快照的先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-181">Prerequisites for and Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="70f1c-182">**本节内容：**</span><span class="sxs-lookup"><span data-stu-id="70f1c-182">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="70f1c-183">先决条件</span><span class="sxs-lookup"><span data-stu-id="70f1c-183">Prerequisites</span></span>](#Prerequisites)  
  
-   [<span data-ttu-id="70f1c-184">源数据库的限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-184">Limitations on the Source Database</span></span>](#LimitsOnSourceDb)  
  
-   [<span data-ttu-id="70f1c-185">数据库快照的限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-185">Limitations on Database Snapshots</span></span>](#LimitsOnDbSS)  
  
-   [<span data-ttu-id="70f1c-186">磁盘空间要求</span><span class="sxs-lookup"><span data-stu-id="70f1c-186">Disk Space Requirements</span></span>](#DiskSpace)  
  
-   [<span data-ttu-id="70f1c-187">含有脱机文件组的数据库快照</span><span class="sxs-lookup"><span data-stu-id="70f1c-187">Database Snapshots with Offline Filegroups</span></span>](#OfflineFGs)  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="70f1c-188">先决条件</span><span class="sxs-lookup"><span data-stu-id="70f1c-188">Prerequisites</span></span>  
 <span data-ttu-id="70f1c-189">可以使用任何恢复模式的源数据库必须满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="70f1c-189">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="70f1c-190">服务器实例必须在支持数据库快照的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本上运行。</span><span class="sxs-lookup"><span data-stu-id="70f1c-190">The server instance must be running on an edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that supports database snapshots.</span></span> <span data-ttu-id="70f1c-191">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="70f1c-191">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="70f1c-192">源数据库必须处于联机状态，除非该数据库是数据库镜像会话中的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="70f1c-192">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="70f1c-193">您可在可用性组中的任何主数据库或辅助数据库上创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-193">You can create a database snapshot on any primary or secondary database in an availability group.</span></span> <span data-ttu-id="70f1c-194">副本角色必须是 PRIMARY 或 SECONDARY，且不处于 RESOLVING 状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-194">The replica role must be either PRIMARY or SECONDARY, not in the RESOLVING state.</span></span>  
  
     <span data-ttu-id="70f1c-195">当您创建一个数据库快照时，我们建议数据库同步状态是 SYNCHRONIZING 或 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="70f1c-195">We recommend that the database synchronization state be SYNCHRONIZING or SYNCHRONIZED when you create a database snapshot.</span></span> <span data-ttu-id="70f1c-196">但是，当数据库同步状态为 NOT SYNCHRONIZING 时，可以创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-196">However, database snapshots can be created when the database synchronization state is NOT SYNCHRONIZING.</span></span>  
  
     <span data-ttu-id="70f1c-197">有关详细信息，请参阅[含有 AlwaysOn 可用性组的数据库快照 (SQL Server)](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70f1c-197">For more information, see [Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/database-snapshots-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="70f1c-198">若要在镜像数据库中创建数据库快照，数据库必须处于 SYNCHRONIZED 镜像状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-198">To create a database snapshot on a mirror database, the database must be in the SYNCHRONIZED mirroring state.</span></span>  
  
-   <span data-ttu-id="70f1c-199">不能将源数据库配置为可缩放共享数据库。</span><span class="sxs-lookup"><span data-stu-id="70f1c-199">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f1c-200">所有恢复模式都支持数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-200">All recovery models support database snapshots.</span></span>  
  
###  <a name="limitations-on-the-source-database"></a><a name="LimitsOnSourceDb"></a> <span data-ttu-id="70f1c-201">源数据库的限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-201">Limitations on the Source Database</span></span>  
 <span data-ttu-id="70f1c-202">只要存在数据库快照，快照的源数据库就存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="70f1c-202">As long as a database snapshot exists, the following limitations exist on the snapshot's source database:</span></span>  
  
-   <span data-ttu-id="70f1c-203">不能对数据库进行删除、分离或还原。</span><span class="sxs-lookup"><span data-stu-id="70f1c-203">The database cannot be dropped, detached, or restored.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70f1c-204">可以备份源数据库，这方面将不受数据库快照的影响。</span><span class="sxs-lookup"><span data-stu-id="70f1c-204">Backing up the source database works normally; it is unaffected by database snapshots.</span></span>  
  
-   <span data-ttu-id="70f1c-205">源数据库的性能受到影响。由于每次更新页时都会对快照执行“写入时复制”操作，导致源数据库上的 I/O 增加。</span><span class="sxs-lookup"><span data-stu-id="70f1c-205">Performance is reduced, due to increased I/O on the source database resulting from a copy-on-write operation to the snapshot every time a page is updated.</span></span>  
  
-   <span data-ttu-id="70f1c-206">不能从源数据库或任何快照中删除文件。</span><span class="sxs-lookup"><span data-stu-id="70f1c-206">Files cannot be dropped from the source database or from any snapshots.</span></span>  
  
###  <a name="limitations-on-database-snapshots"></a><a name="LimitsOnDbSS"></a> <span data-ttu-id="70f1c-207">数据库快照的限制</span><span class="sxs-lookup"><span data-stu-id="70f1c-207">Limitations on Database Snapshots</span></span>  
 <span data-ttu-id="70f1c-208">数据库快照存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="70f1c-208">The following limitations apply to database snapshots:</span></span>  
  
-   <span data-ttu-id="70f1c-209">数据库快照必须与源数据库在相同的服务器实例上创建和保留。</span><span class="sxs-lookup"><span data-stu-id="70f1c-209">A database snapshot must be created and remain on the same server instance as the source database.</span></span>  
  
-   <span data-ttu-id="70f1c-210">始终对整个数据库制作数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-210">Database snapshots always work on an entire database.</span></span>  
  
-   <span data-ttu-id="70f1c-211">数据库快照依赖于源数据库，但不是冗余存储。</span><span class="sxs-lookup"><span data-stu-id="70f1c-211">Database snapshots are dependent on the source database and are not redundant storage.</span></span> <span data-ttu-id="70f1c-212">它们无法防止磁盘错误或其他类型的损坏。</span><span class="sxs-lookup"><span data-stu-id="70f1c-212">They do not protect against disk errors or other types of corruption.</span></span> <span data-ttu-id="70f1c-213">因此，使用数据库快照恢复数据库不能代替备份和还原策略。</span><span class="sxs-lookup"><span data-stu-id="70f1c-213">Therefore, using database snapshots for reverting a database is not a substitute for your backup and restore strategy.</span></span> <span data-ttu-id="70f1c-214">严格按计划执行备份仍然至关重要。</span><span class="sxs-lookup"><span data-stu-id="70f1c-214">Performing all your scheduled backups remains essential.</span></span> <span data-ttu-id="70f1c-215">如果必须将源数据库还原到创建数据库快照的时间点，请实施允许您执行该操作的备份策略。</span><span class="sxs-lookup"><span data-stu-id="70f1c-215">If you must restore the source database to the point in time at which you created a database snapshot, implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="70f1c-216">当将源数据库中更新的页强制压入快照时，如果快照用尽磁盘空间或者遇到其他错误，则该快照将成为可疑快照并且必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="70f1c-216">When a page getting updated on the source database is pushed to a snapshot, if the snapshot runs out of disk space or encounters some other error, the snapshot becomes suspect and must be deleted.</span></span>  
  
-   <span data-ttu-id="70f1c-217">快照为只读。</span><span class="sxs-lookup"><span data-stu-id="70f1c-217">Snapshots are read-only.</span></span> <span data-ttu-id="70f1c-218">由于它们为只读，所以无法升级。</span><span class="sxs-lookup"><span data-stu-id="70f1c-218">Since they are read only, they cannot be upgraded.</span></span> <span data-ttu-id="70f1c-219">因此，可以知道数据库快照在升级后会不可用。</span><span class="sxs-lookup"><span data-stu-id="70f1c-219">Therefore, database snapshots are not expected to be viable after an upgrade.</span></span>  
  
-   <span data-ttu-id="70f1c-220">禁止对 **model**数据库、 **master**数据库和 **tempdb** 数据库创建快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-220">Snapshots of the **model**, **master**, and **tempdb** databases are prohibited.</span></span>  
  
-   <span data-ttu-id="70f1c-221">不能更改数据库快照文件的任何规范。</span><span class="sxs-lookup"><span data-stu-id="70f1c-221">You cannot change any of the specifications of the database snapshot files.</span></span>  
  
-   <span data-ttu-id="70f1c-222">不能从数据库快照中删除文件。</span><span class="sxs-lookup"><span data-stu-id="70f1c-222">You cannot drop files from a database snapshot.</span></span>  
  
-   <span data-ttu-id="70f1c-223">不能备份或还原数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-223">You cannot back up or restore database snapshots.</span></span>  
  
-   <span data-ttu-id="70f1c-224">不能附加或分离数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-224">You cannot attach or detach database snapshots.</span></span>  
  
-   <span data-ttu-id="70f1c-225">不能在 FAT32 文件系统或 RAW 分区上创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-225">You cannot create database snapshots on FAT32 file system or RAW partitions.</span></span> <span data-ttu-id="70f1c-226">数据库快照所用的稀疏文件由 NTFS 文件系统提供。</span><span class="sxs-lookup"><span data-stu-id="70f1c-226">The sparse files used by database snapshots are provided by the NTFS file system.</span></span>  
  
-   <span data-ttu-id="70f1c-227">数据库快照不支持全文索引。</span><span class="sxs-lookup"><span data-stu-id="70f1c-227">Full-text indexing is not supported on database snapshots.</span></span> <span data-ttu-id="70f1c-228">不从源数据库传播全文目录。</span><span class="sxs-lookup"><span data-stu-id="70f1c-228">Full-text catalogs are not propagated from the source database.</span></span>  
  
-   <span data-ttu-id="70f1c-229">数据库快照将继承快照创建时其源数据库的安全约束。</span><span class="sxs-lookup"><span data-stu-id="70f1c-229">A database snapshot inherits the security constraints of its source database at the time of snapshot creation.</span></span> <span data-ttu-id="70f1c-230">由于快照是只读的，因此无法更改继承的权限，对源数据库的更改权限将不反映在现有快照中。</span><span class="sxs-lookup"><span data-stu-id="70f1c-230">Because snapshots are read-only, inherited permissions cannot be changed and permission changes made to the source will not be reflected in existing snapshots.</span></span>  
  
-   <span data-ttu-id="70f1c-231">快照始终反映创建该快照时的文件组状态：联机文件组将保持联机状态，脱机文件组将保持脱机状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-231">A snapshot always reflects the state of filegroups at the time of snapshot creation: online filegroups remain online, and offline filegroups remain offline.</span></span> <span data-ttu-id="70f1c-232">有关详细信息，请参阅本主题后面的“含有脱机文件组的数据库快照”。</span><span class="sxs-lookup"><span data-stu-id="70f1c-232">For more information, see "Database Snapshots with Offline Filegroups" later in this topic.</span></span>  
  
-   <span data-ttu-id="70f1c-233">如果源数据库的状态为 RECOVERY_PENDING，可能无法访问其数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-233">If a source database becomes RECOVERY_PENDING, its database snapshots may become inaccessible.</span></span> <span data-ttu-id="70f1c-234">但是，当解决了源数据库的问题之后，快照将再次变成可用快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-234">After the issue on the source database is resolved, however, its snapshots should become available again.</span></span>  
  
-   <span data-ttu-id="70f1c-235">只读文件组和压缩文件组不支持恢复操作。</span><span class="sxs-lookup"><span data-stu-id="70f1c-235">Reverting is unsupported for read-only filegroups and for compressed filegroups.</span></span> <span data-ttu-id="70f1c-236">尝试恢复包含下列任意一种文件组的数据库将失败。</span><span class="sxs-lookup"><span data-stu-id="70f1c-236">Attempts to revert a database containing either of these types of filegroups fail.</span></span>  
  
-   <span data-ttu-id="70f1c-237">在日志传送配置中，只能针对主数据库，而不能针对辅助数据库创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-237">In a log shipping configuration, database snapshots can be created only on the primary database, not on a secondary database.</span></span> <span data-ttu-id="70f1c-238">如果您在主服务器实例和辅助服务器实例之间切换角色，则在将主数据库设置为辅助数据库之前，必须先删除所有数据库快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-238">If you switch roles between the primary server instance and a secondary server instance, you must drop all the database snapshots before you can set the primary database up as a secondary database.</span></span>  
  
-   <span data-ttu-id="70f1c-239">不能将数据库快照配置为可缩放共享数据库。</span><span class="sxs-lookup"><span data-stu-id="70f1c-239">A database snapshot cannot be configured as a scalable shared database.</span></span>  
  
-   <span data-ttu-id="70f1c-240">数据库快照不支持 FILESTREAM 文件组。</span><span class="sxs-lookup"><span data-stu-id="70f1c-240">FILESTREAM filegroups are not supported by database snapshots.</span></span> <span data-ttu-id="70f1c-241">如果源数据库中存在 FILESTREAM 文件组，则它们在数据库快照中被标识为脱机状态，且其数据库快照不能用于恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="70f1c-241">If FILESTREAM filegroups exist in a source database, they are marked as offline in its database snapshots, and the database snapshots cannot be used for reverting the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70f1c-242">对数据库快照执行的 SELECT 语句不能指定 FILESTREAM 列；否则，将返回如下错误消息： `Could not continue scan with NOLOCK due to data movement.`</span><span class="sxs-lookup"><span data-stu-id="70f1c-242">A SELECT statement that is executed on a database snapshot must not specify a FILESTREAM column; otherwise, the following error message will be returned: `Could not continue scan with NOLOCK due to data movement.`</span></span>  
  
-   <span data-ttu-id="70f1c-243">当有关只读快照的统计信息丢失或变得陈旧时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将创建临时统计信息并在 tempdb 中进行维护。</span><span class="sxs-lookup"><span data-stu-id="70f1c-243">When statistics on a read-only snapshot are missing or stale, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] creates and maintains temporary statistics in tempdb.</span></span> <span data-ttu-id="70f1c-244">有关详细信息，请参阅[统计信息](../statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="70f1c-244">For more information, see [Statistics](../statistics/statistics.md).</span></span>  
  
###  <a name="disk-space-requirements"></a><a name="DiskSpace"></a> <span data-ttu-id="70f1c-245">磁盘空间要求</span><span class="sxs-lookup"><span data-stu-id="70f1c-245">Disk Space Requirements</span></span>  
 <span data-ttu-id="70f1c-246">数据库快照占用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="70f1c-246">Database snapshots consume disk space.</span></span> <span data-ttu-id="70f1c-247">如果数据库快照用尽了磁盘空间，将被标记为可疑，必须将其删除。</span><span class="sxs-lookup"><span data-stu-id="70f1c-247">If a database snapshot runs out of disk space, it is marked as suspect and must be dropped.</span></span> <span data-ttu-id="70f1c-248">（但是，源数据库不会受到影响，对其执行的操作仍能继续正常进行。）然而，与一份完整的数据库相比，快照具有高度空间有效性。</span><span class="sxs-lookup"><span data-stu-id="70f1c-248">(The source database, however, is not affected; actions on it continue normally.) Compared to a full copy of a database, however, snapshots are highly space efficient.</span></span> <span data-ttu-id="70f1c-249">快照仅需足够存储空间来存储在其生存期中更改的页。</span><span class="sxs-lookup"><span data-stu-id="70f1c-249">A snapshot requires only enough storage for the pages that change during its lifetime.</span></span> <span data-ttu-id="70f1c-250">通常情况下，快照只会保留一段有限的时间，因此其大小不是主要问题。</span><span class="sxs-lookup"><span data-stu-id="70f1c-250">Generally, snapshots are kept for a limited time, so their size is not a major concern.</span></span>  
  
 <span data-ttu-id="70f1c-251">但是，保留快照的时间越长，越有可能将可用空间用完。</span><span class="sxs-lookup"><span data-stu-id="70f1c-251">The longer you keep a snapshot, however, the more likely it is to use up available space.</span></span> <span data-ttu-id="70f1c-252">稀疏文件最大只能增长到创建快照时相应的源数据库文件的大小。</span><span class="sxs-lookup"><span data-stu-id="70f1c-252">The maximum size to which a sparse file can grow is the size of the corresponding source database file at the time of the snapshot creation.</span></span>  
  
 <span data-ttu-id="70f1c-253">如果数据库快照用完了磁盘空间，则必须删除该快照。</span><span class="sxs-lookup"><span data-stu-id="70f1c-253">If a database snapshot runs out of disk space, it must be deleted (dropped).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f1c-254">除文件空间外，数据库快照与数据库占用的资源量大致相同。</span><span class="sxs-lookup"><span data-stu-id="70f1c-254">Except for file space, a database snapshot consumes roughly as many resources as a database.</span></span>  
  
###  <a name="database-snapshots-with-offline-filegroups"></a><a name="OfflineFGs"></a> <span data-ttu-id="70f1c-255">含有脱机文件组的数据库快照</span><span class="sxs-lookup"><span data-stu-id="70f1c-255">Database Snapshots with Offline Filegroups</span></span>  
 <span data-ttu-id="70f1c-256">当您尝试执行下列任何操作时，源数据库中的脱机文件组都将影响数据库快照：</span><span class="sxs-lookup"><span data-stu-id="70f1c-256">Offline filegroups in the source database affect database snapshots when you try to do any of the following:</span></span>  
  
-   <span data-ttu-id="70f1c-257">创建快照</span><span class="sxs-lookup"><span data-stu-id="70f1c-257">Create a snapshot</span></span>  
  
     <span data-ttu-id="70f1c-258">当源数据库具有一个或多个脱机文件组时，快照创建只有在文件组处于脱机状态时才能成功。</span><span class="sxs-lookup"><span data-stu-id="70f1c-258">When a source database has one or more offline filegroups, snapshot creation succeeds with the filegroups offline.</span></span> <span data-ttu-id="70f1c-259">不能为脱机文件组创建稀疏文件。</span><span class="sxs-lookup"><span data-stu-id="70f1c-259">Sparse files are not created for the offline filegroups.</span></span>  
  
-   <span data-ttu-id="70f1c-260">使文件组脱机</span><span class="sxs-lookup"><span data-stu-id="70f1c-260">Take a filegroup offline</span></span>  
  
     <span data-ttu-id="70f1c-261">可以在源数据库中使文件脱机。</span><span class="sxs-lookup"><span data-stu-id="70f1c-261">You can take a file offline in the source database.</span></span> <span data-ttu-id="70f1c-262">但是，如果创建快照时文件组处于联机状态，则该文件组在数据库快照中仍将保持联机状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-262">However, the filegroup remains online in database snapshots if it was online when the snapshot was created.</span></span> <span data-ttu-id="70f1c-263">如果查询的数据在快照创建后已更改，则在快照中可以访问原始数据页。</span><span class="sxs-lookup"><span data-stu-id="70f1c-263">If the queried data has changed since snapshot creation, the original data page will be accessible in the snapshot.</span></span> <span data-ttu-id="70f1c-264">但是，使用快照访问文件组中未修改数据的查询可能会由于出现输入/输出 (I/O) 错误而失败。</span><span class="sxs-lookup"><span data-stu-id="70f1c-264">However, queries that use the snapshot to access unmodified data in the filegroup are likely to fail with input/output (I/O) errors.</span></span>  
  
-   <span data-ttu-id="70f1c-265">使文件组联机</span><span class="sxs-lookup"><span data-stu-id="70f1c-265">Bring a filegroup online</span></span>  
  
     <span data-ttu-id="70f1c-266">只要数据库具有任何快照，就不能使其中的文件组联机。</span><span class="sxs-lookup"><span data-stu-id="70f1c-266">You cannot bring a filegroup online in a database that has any database snapshots.</span></span> <span data-ttu-id="70f1c-267">如果在创建快照时文件组处于脱机状态，或当数据库快照存在时使文件组脱机，则文件组将保持脱机状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-267">If a filegroup is offline at the time of snapshot creation or is taken offline while a database snapshot exists, the filegroup remains offline.</span></span> <span data-ttu-id="70f1c-268">这是因为使文件重新联机需要还原该文件，而如果数据库已具有快照，则无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="70f1c-268">This is because bringing a file back online involves restoring it, which is not possible if a database snapshot exists on the database.</span></span>  
  
-   <span data-ttu-id="70f1c-269">将源数据库恢复到快照</span><span class="sxs-lookup"><span data-stu-id="70f1c-269">Revert the source database to the snapshot</span></span>  
  
     <span data-ttu-id="70f1c-270">将源数据库恢复到数据库快照要求除创建快照时处于脱机状态的文件组外，所有文件组都要处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="70f1c-270">Reverting a source database to a database snapshot requires that all of the filegroups are online except for filegroups that were offline when the snapshot was created.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="70f1c-271">相关任务</span><span class="sxs-lookup"><span data-stu-id="70f1c-271">Related Tasks</span></span>  
  
-   [<span data-ttu-id="70f1c-272">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70f1c-272">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="70f1c-273">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70f1c-273">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="70f1c-274">查看数据库快照的稀疏文件大小 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70f1c-274">View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;</span></span>](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="70f1c-275">将数据库恢复到数据库快照</span><span class="sxs-lookup"><span data-stu-id="70f1c-275">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="70f1c-276">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="70f1c-276">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="70f1c-277">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70f1c-277">See Also</span></span>  
 [<span data-ttu-id="70f1c-278">数据库镜像和数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="70f1c-278">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
