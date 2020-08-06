---
title: 创建数据库快照 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
ms.openlocfilehash: bae68c2d507e1dd3809e76a9d842b765d72234e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693950"
---
# <a name="create-a-database-snapshot-transact-sql"></a><span data-ttu-id="3345d-102">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3345d-102">Create a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="3345d-103">创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库快照的唯一方式是使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3345d-103">The only way to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot is to use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="3345d-104">不支持创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-104">does not support the creation of database snapshots.</span></span>  
  
-   <span data-ttu-id="3345d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="3345d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3345d-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="3345d-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="3345d-107">安全性</span><span class="sxs-lookup"><span data-stu-id="3345d-107">Security</span></span>](#Security)  
  
     [<span data-ttu-id="3345d-108">最佳做法：命名数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-108">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   <span data-ttu-id="3345d-109">**若要创建数据库快照，请使用：**  [transact-sql](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="3345d-109">**To create a database snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3345d-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="3345d-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="3345d-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="3345d-111">Prerequisites</span></span>  
 <span data-ttu-id="3345d-112">可以使用任何恢复模式的源数据库必须满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="3345d-112">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="3345d-113">服务器实例必须运行支持数据库快照的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="3345d-113">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database snapshot.</span></span> <span data-ttu-id="3345d-114">有关中的数据库快照支持的信息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，请参阅[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="3345d-114">For information about support for database snapshots in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="3345d-115">源数据库必须处于联机状态，除非该数据库是数据库镜像会话中的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="3345d-115">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="3345d-116">若要在镜像数据库中创建数据库快照，数据库必须处于同步[镜像状态](../../database-engine/database-mirroring/mirroring-states-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3345d-116">To create a database snapshot on a mirror database, the database must be in the synchronized[mirroring state](../../database-engine/database-mirroring/mirroring-states-sql-server.md).</span></span>  
  
-   <span data-ttu-id="3345d-117">不能将源数据库配置为可缩放共享数据库。</span><span class="sxs-lookup"><span data-stu-id="3345d-117">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3345d-118">有关其他重要事项的信息，请参阅 [数据库快照 (SQL Server)](database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3345d-118">For information about other significant considerations, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3345d-119">建议</span><span class="sxs-lookup"><span data-stu-id="3345d-119">Recommendations</span></span>  
 <span data-ttu-id="3345d-120">本节讨论以下最佳做法：</span><span class="sxs-lookup"><span data-stu-id="3345d-120">This section discusses the following best practices:</span></span>  
  
-   [<span data-ttu-id="3345d-121">最佳做法：命名数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-121">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   [<span data-ttu-id="3345d-122">最佳做法：限制数据库快照的数量</span><span class="sxs-lookup"><span data-stu-id="3345d-122">Best Practice: Limiting the Number of Database Snapshots</span></span>](#Limiting_Number)  
  
-   [<span data-ttu-id="3345d-123">最佳做法：将客户端连接到数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-123">Best Practice: Client Connections to a Database Snapshot</span></span>](#Client_Connections)  
  
####  <a name="best-practice-naming-database-snapshots"></a><a name="Naming"></a> <span data-ttu-id="3345d-124">最佳做法：命名数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-124">Best Practice: Naming Database Snapshots</span></span>  
 <span data-ttu-id="3345d-125">创建数据库快照之前，考虑如何命名它们是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="3345d-125">Before creating snapshots, it is important to consider how to name them.</span></span> <span data-ttu-id="3345d-126">每个数据库快照都需要一个唯一的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="3345d-126">Each database snapshot requires a unique database name.</span></span> <span data-ttu-id="3345d-127">为了便于管理，数据库快照的名称可以包含标识数据库的信息，例如：</span><span class="sxs-lookup"><span data-stu-id="3345d-127">For administrative ease, the name of a snapshot can incorporate information that identifies the database, such as:</span></span>  
  
-   <span data-ttu-id="3345d-128">源数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3345d-128">The name of the source database.</span></span>  
  
-   <span data-ttu-id="3345d-129">表明新名称用于快照的指示信息。</span><span class="sxs-lookup"><span data-stu-id="3345d-129">An indication that the new name is for a snapshot.</span></span>  
  
-   <span data-ttu-id="3345d-130">快照的创建日期和时间、序列号或一些其他的信息（例如一天中的某个时间）以区分给定的数据库上的连续快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-130">The creation date and time of the snapshot, a sequence number, or some other information, such as time of day, to distinguish sequential snapshots on a given database.</span></span>  
  
 <span data-ttu-id="3345d-131">例如，假设有一系列的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-131">For example, consider a series of snapshots for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="3345d-132">在上午 6 时和下午 6 时（基于 24 小时制）之间，</span><span class="sxs-lookup"><span data-stu-id="3345d-132">Three daily snapshots are created at 6-hour intervals between 6 A.M.</span></span> <span data-ttu-id="3345d-133">以 6 个小时为间隔创建三个每日快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-133">and 6 P.M., based on a 24-hour clock.</span></span> <span data-ttu-id="3345d-134">每个每日快照保持 24 小时才被删除并被同一名称的新快照替换。</span><span class="sxs-lookup"><span data-stu-id="3345d-134">Each daily snapshot is kept for 24 hours before being dropped and replaced by a new snapshot of the same name.</span></span> <span data-ttu-id="3345d-135">请注意，每个快照名称指明了小时，而非天：</span><span class="sxs-lookup"><span data-stu-id="3345d-135">Note that each snapshot name indicates the hour, but not the day:</span></span>  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 <span data-ttu-id="3345d-136">另外，如果这些每日快照创建的时间每天都变化，则推荐使用不太精确的命名约定，例如：</span><span class="sxs-lookup"><span data-stu-id="3345d-136">Alternatively, if the creation time of these daily snapshots varies from day to day, a less precise naming convention might be preferable, for example:</span></span>  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
####  <a name="best-practice-limiting-the-number-of-database-snapshots"></a><a name="Limiting_Number"></a> <span data-ttu-id="3345d-137">最佳做法：限制数据库快照的数量</span><span class="sxs-lookup"><span data-stu-id="3345d-137">Best Practice: Limiting the Number of Database Snapshots</span></span>  
 <span data-ttu-id="3345d-138">随着时间的变化创建一系列快照可捕获源数据库的连续快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-138">Creating a series of snapshots over time captures sequential snapshots of the source database.</span></span> <span data-ttu-id="3345d-139">每个数据库快照会一直保存在系统中，直到被显式删除。</span><span class="sxs-lookup"><span data-stu-id="3345d-139">Each snapshot persists until it is explicitly dropped.</span></span> <span data-ttu-id="3345d-140">因为每个快照会随着原始页的更新而不断增长，所以您可能想在创建新快照后通过删除旧的快照来节省空间。</span><span class="sxs-lookup"><span data-stu-id="3345d-140">Because each snapshot will continue to grow as original pages are updated, you may want to conserve disk space by deleting an older snapshot after creating a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3345d-141">如果想要还原到某个数据库快照，则需要从该数据库中删除所有其他快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-141">If you want to revert to a database snapshot, you need to delete any other snapshots from that database.</span></span>  
  
####  <a name="best-practice-client-connections-to-a-database-snapshot"></a><a name="Client_Connections"></a> <span data-ttu-id="3345d-142">最佳做法：将客户端连接到数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-142">Best Practice: Client Connections to a Database Snapshot</span></span>  
 <span data-ttu-id="3345d-143">若要使用数据库快照，客户端需要知道它的位置。</span><span class="sxs-lookup"><span data-stu-id="3345d-143">To use a database snapshot, clients need to know where to find it.</span></span> <span data-ttu-id="3345d-144">正在创建或删除另一个数据库快照时，用户可以从一个数据库快照读取。</span><span class="sxs-lookup"><span data-stu-id="3345d-144">Users can read from one database snapshot while another is being created or deleted.</span></span> <span data-ttu-id="3345d-145">但是，如果用新快照替代现有快照，您需要将客户端重新定向到新快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-145">However, when you substitute a new snapshot for an existing one, you need to redirect clients to the new snapshot.</span></span> <span data-ttu-id="3345d-146">用户可以通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]手动连接到数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-146">Users can manually connect to a database snapshot by means of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3345d-147">但是，若要支持生产环境，您应该创建一个编程解决方案，该方案透明地将报表编写客户端定向到数据库的最新数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-147">However, to support a production environment, you should create a programmatic solution that transparently directs report-writing clients to the latest database snapshot of the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3345d-148">Security</span><span class="sxs-lookup"><span data-stu-id="3345d-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3345d-149">权限</span><span class="sxs-lookup"><span data-stu-id="3345d-149">Permissions</span></span>  
 <span data-ttu-id="3345d-150">可创建数据库的任何用户都可以创建数据库快照；但是，若要创建镜像数据库的快照，你必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="3345d-150">Any user who can create a database can create a database snapshot; however, to create a snapshot of a mirror database, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3345d-151">如何创建数据库快照（使用 Transact-SQL）</span><span class="sxs-lookup"><span data-stu-id="3345d-151">How to Create a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="3345d-152">**创建数据库快照**</span><span class="sxs-lookup"><span data-stu-id="3345d-152">**To create a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3345d-153">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="3345d-153">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="3345d-154">根据源数据库的当前大小，确保有足够的磁盘空间存放数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-154">Based on the current size of the source database, ensure that you have sufficient disk space to hold the database snapshot.</span></span> <span data-ttu-id="3345d-155">数据库快照的最大大小为创建快照时源数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="3345d-155">The maximum size of a database snapshot is the size of the source database at snapshot creation.</span></span> <span data-ttu-id="3345d-156">有关详细信息，请参阅[查看数据库快照的稀疏文件大小 (Transact-SQL)](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="3345d-156">For more information, see [View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="3345d-157">使用 AS SNAPSHOT OF 子句对文件执行 CREATE DATABASE 语句。</span><span class="sxs-lookup"><span data-stu-id="3345d-157">Issue a CREATE DATABASE statement on the files using the AS SNAPSHOT OF clause.</span></span> <span data-ttu-id="3345d-158">创建快照需要指定源数据库的每个数据库文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="3345d-158">Creating a snapshot requires specifying the logical name of every database file of the source database.</span></span> <span data-ttu-id="3345d-159">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="3345d-159">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="3345d-160">CREATE DATABASE *database_snapshot_name*</span><span class="sxs-lookup"><span data-stu-id="3345d-160">CREATE DATABASE *database_snapshot_name*</span></span>  
  
     <span data-ttu-id="3345d-161">ON</span><span class="sxs-lookup"><span data-stu-id="3345d-161">ON</span></span>  
  
     <span data-ttu-id="3345d-162">(</span><span class="sxs-lookup"><span data-stu-id="3345d-162">(</span></span>  
  
     <span data-ttu-id="3345d-163">NAME =*logical_file_name*,</span><span class="sxs-lookup"><span data-stu-id="3345d-163">NAME =*logical_file_name*,</span></span>  
  
     <span data-ttu-id="3345d-164">FILENAME ='*os_file_name*'</span><span class="sxs-lookup"><span data-stu-id="3345d-164">FILENAME ='*os_file_name*'</span></span>  
  
     <span data-ttu-id="3345d-165">) [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="3345d-165">) [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="3345d-166">AS SNAPSHOT OF *source_database_name*</span><span class="sxs-lookup"><span data-stu-id="3345d-166">AS SNAPSHOT OF *source_database_name*</span></span>  
  
     <span data-ttu-id="3345d-167">[;]</span><span class="sxs-lookup"><span data-stu-id="3345d-167">[;]</span></span>  
  
     <span data-ttu-id="3345d-168">其中，source_database_name 是源数据库，logical_file_name 是引用该文件时在 SQL Server 中使用的逻辑名称，os_file_name 是创建该文件时操作系统使用的路径和文件名，database_snapshot_name 是将数据库恢复到的快照的名称。</span><span class="sxs-lookup"><span data-stu-id="3345d-168">Where *source_\*\*database_name* is the source database, *logical_file_name i*s the logical name used in SQL Server when referencing the file, *os_file_name* is the path and file name used by the operating system when you create the file, and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="3345d-169">有关该语法的完整描述，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3345d-169">For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3345d-170">创建数据库快照时，CREATE DATABASE 语句中不允许有日志文件、脱机文件、还原文件和不起作用的文件。</span><span class="sxs-lookup"><span data-stu-id="3345d-170">When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3345d-171">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3345d-171">Examples (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3345d-172">示例中使用的扩展名 `.ss` 是随意选择的。</span><span class="sxs-lookup"><span data-stu-id="3345d-172">The `.ss` extension used in the examples is arbitrary.</span></span>  
  
 <span data-ttu-id="3345d-173">本部分包含以下示例：</span><span class="sxs-lookup"><span data-stu-id="3345d-173">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="3345d-174">A.</span><span class="sxs-lookup"><span data-stu-id="3345d-174">A.</span></span> [<span data-ttu-id="3345d-175">对 AdventureWorks 数据库创建快照</span><span class="sxs-lookup"><span data-stu-id="3345d-175">Creating a snapshot on the AdventureWorks database</span></span>](#Creating_on_AW)  
  
-   <span data-ttu-id="3345d-176">B.</span><span class="sxs-lookup"><span data-stu-id="3345d-176">B.</span></span> [<span data-ttu-id="3345d-177">对 Sales 数据库创建快照</span><span class="sxs-lookup"><span data-stu-id="3345d-177">Creating a snapshot on the Sales database</span></span>](#Creating_on_Sales)  
  
####  <a name="a-creating-a-snapshot-on-the-adventureworks-database"></a><a name="Creating_on_AW"></a> <span data-ttu-id="3345d-178">A.</span><span class="sxs-lookup"><span data-stu-id="3345d-178">A.</span></span> <span data-ttu-id="3345d-179">对 AdventureWorks 数据库创建快照</span><span class="sxs-lookup"><span data-stu-id="3345d-179">Creating a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="3345d-180">此示例对 `AdventureWorks` 数据库创建数据库快照。</span><span class="sxs-lookup"><span data-stu-id="3345d-180">This example creates a database snapshot on the `AdventureWorks` database.</span></span> <span data-ttu-id="3345d-181">快照名称 `AdventureWorks_dbss_1800`及其稀疏文件的名称 `AdventureWorks_data_1800.ss`指明了创建时间 6 P.M.（1800 小时）。</span><span class="sxs-lookup"><span data-stu-id="3345d-181">The snapshot name, `AdventureWorks_dbss_1800`, and the file name of its sparse file, `AdventureWorks_data_1800.ss`, indicate the creation time, 6 P.M (1800 hours).</span></span>  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="b-creating-a-snapshot-on-the-sales-database"></a><a name="Creating_on_Sales"></a> <span data-ttu-id="3345d-182">B.</span><span class="sxs-lookup"><span data-stu-id="3345d-182">B.</span></span> <span data-ttu-id="3345d-183">对 Sales 数据库创建快照</span><span class="sxs-lookup"><span data-stu-id="3345d-183">Creating a snapshot on the Sales database</span></span>  
 <span data-ttu-id="3345d-184">此示例对 `sales_snapshot1200`数据库创建数据库快照 `Sales` 。</span><span class="sxs-lookup"><span data-stu-id="3345d-184">This example creates a database snapshot, `sales_snapshot1200`, on the `Sales` database.</span></span> <span data-ttu-id="3345d-185">此数据库是在[创建数据库 &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)中的 "创建具有文件组的数据库" 示例中创建的。</span><span class="sxs-lookup"><span data-stu-id="3345d-185">This database was created in the example, "Creating a database that has filegroups," in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3345d-186">相关任务</span><span class="sxs-lookup"><span data-stu-id="3345d-186">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3345d-187">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3345d-187">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="3345d-188">将数据库恢复到数据库快照</span><span class="sxs-lookup"><span data-stu-id="3345d-188">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="3345d-189">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3345d-189">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="3345d-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3345d-190">See Also</span></span>  
 <span data-ttu-id="3345d-191">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3345d-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="3345d-192">数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3345d-192">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
