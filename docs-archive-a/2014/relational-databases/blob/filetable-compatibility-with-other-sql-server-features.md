---
title: FileTable 与其他 SQL Server 功能的兼容性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], using with other features
ms.assetid: f12a17e4-bd3d-42b0-b253-efc36876db37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a6ac6668ff362a986646c4e01b1f0e5e722611c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692972"
---
# <a name="filetable-compatibility-with-other-sql-server-features"></a><span data-ttu-id="ac511-102">FileTable 与其他 SQL Server 功能的兼容性</span><span class="sxs-lookup"><span data-stu-id="ac511-102">FileTable Compatibility with Other SQL Server Features</span></span>
  <span data-ttu-id="ac511-103">说明 FileTable 如何与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的其他功能配合使用。</span><span class="sxs-lookup"><span data-stu-id="ac511-103">Describes how FileTables work with other features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="alwayson-availability-groups-and-filetables"></a><a name="alwayson"></a> <span data-ttu-id="ac511-104">AlwaysOn 可用性组和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-104">AlwaysOn Availability Groups and FileTables</span></span>  
 <span data-ttu-id="ac511-105">在包含 FILESTREAM 或 FileTable 数据的数据库属于某一 AlwaysOn 可用性组时：</span><span class="sxs-lookup"><span data-stu-id="ac511-105">When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:</span></span>  
  
-   <span data-ttu-id="ac511-106">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]支持部分 FileTable 功能。</span><span class="sxs-lookup"><span data-stu-id="ac511-106">FileTable functionality is partially supported by [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="ac511-107">故障转移后，FileTable 数据在主副本上是可访问的，但是在可读辅助副本上不可访问。</span><span class="sxs-lookup"><span data-stu-id="ac511-107">After a failover, FileTable data is accessible on the primary replica, but FileTable data is not accessible on readable secondary replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ac511-108">请注意故障转移后支持所有 FILESTREAM 功能。</span><span class="sxs-lookup"><span data-stu-id="ac511-108">Notice that after a failover all FILESTREAM functionality is supported.</span></span> <span data-ttu-id="ac511-109">FILESTREAM 数据在可读辅助副本和新的主副本上均可访问。</span><span class="sxs-lookup"><span data-stu-id="ac511-109">FILESTREAM data is accessible on both readable secondary replicas and on the new primary.</span></span>  
  
-   <span data-ttu-id="ac511-110">FILESTREAM 和 FileTable 函数接受或返回虚拟网络名称 (VNN)，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="ac511-110">The FILESTREAM and FileTable functions accept or return virtual network names (VNNs) instead of computer names.</span></span> <span data-ttu-id="ac511-111">有关这些函数的详细信息，请参阅 [Filestream 和 FileTable 函数 (Transact-SQL)](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ac511-111">For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql).</span></span>  
  
-   <span data-ttu-id="ac511-112">通过文件系统 API 对 FILESTREAM 或 FileTable 数据进行的所有访问都应该使用 VNN，而非计算机名称。</span><span class="sxs-lookup"><span data-stu-id="ac511-112">All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names.</span></span> <span data-ttu-id="ac511-113">有关详细信息，请参阅 [FILESTREAM 和 FileTable 与 AlwaysOn 可用性组 (SQL Server)](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ac511-113">For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="partitioning-and-filetables"></a><a name="OtherPartitioning"></a> <span data-ttu-id="ac511-114">分区和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-114">Partitioning and FileTables</span></span>  
 <span data-ttu-id="ac511-115">FileTable 不支持分区。</span><span class="sxs-lookup"><span data-stu-id="ac511-115">Partitioning is not supported on FileTables.</span></span> <span data-ttu-id="ac511-116">通过对多个 FILESTREAM 文件组的支持，在大多数方案中可以解决纯向上扩展问题，而不必使用分区（不像 SQL 2008 FILESTREAM）。</span><span class="sxs-lookup"><span data-stu-id="ac511-116">With the support for multiple FILESTREAM file groups, pure scale-up issues can be handled without having to resort to partitioning  in most scenarios (unlike SQL 2008 FILESTREAMs).</span></span>  
  
##  <a name="replication-and-filetables"></a><a name="OtherRepl"></a> <span data-ttu-id="ac511-117">复制和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-117">Replication and FileTables</span></span>  
 <span data-ttu-id="ac511-118">FileTable 不支持复制和相关功能（包括事务性复制、合并复制、更改数据捕获和更改跟踪）。</span><span class="sxs-lookup"><span data-stu-id="ac511-118">Replication and related features (including transactional replication, merge replication, change data capture, and change tracking) are not supported with FileTables.</span></span>  
  
##  <a name="transaction-semantics-and-filetables"></a><a name="OtherIsolation"></a> <span data-ttu-id="ac511-119">事务语义和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-119">Transaction Semantics and FileTables</span></span>  
 <span data-ttu-id="ac511-120">**Windows 应用程序**</span><span class="sxs-lookup"><span data-stu-id="ac511-120">**Windows applications**</span></span>  
 <span data-ttu-id="ac511-121">Windows 应用程序不理解数据库事务，因此 Windows 写操作不提供数据库事务的 ACID 属性。</span><span class="sxs-lookup"><span data-stu-id="ac511-121">Windows applications do not understand database transactions, so Windows write operations do not provide the ACID properties of a database transaction.</span></span> <span data-ttu-id="ac511-122">因此事务性回滚和恢复不适用于 Windows 更新操作。</span><span class="sxs-lookup"><span data-stu-id="ac511-122">Therefore transactional rollbacks and recovery are not possible with Windows update operations.</span></span>  
  
 <span data-ttu-id="ac511-123">**Transact-SQL 应用程序**</span><span class="sxs-lookup"><span data-stu-id="ac511-123">**Transact-SQL applications**</span></span>  
 <span data-ttu-id="ac511-124">对于应用于 FileTable 中的 FILESTREAM (file_stream) 列的 TSQL 应用程序，隔离语义与常规用户表中的 FILESTREAM 数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="ac511-124">For TSQL applications working on the FILESTREAM (file_stream) column in a FileTable, the isolation semantics are the same as with FILESTREAM datatype in a regular user table.</span></span>  
  
##  <a name="query-notifications-and-filetables"></a><a name="OtherQueryNot"></a> <span data-ttu-id="ac511-125">查询通知和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-125">Query Notifications and FileTables</span></span>  
 <span data-ttu-id="ac511-126">查询不能包含对 FileTable、WHERE 子句或查询的任何其他部分中的 FILESTREAM 列的引用。</span><span class="sxs-lookup"><span data-stu-id="ac511-126">The query cannot contain reference to the FILESTREAM column in the FileTable, in the WHERE clause or any other part of the query.</span></span>  
  
##  <a name="select-into-and-filetables"></a><a name="OtherSelectInto"></a> <span data-ttu-id="ac511-127">SELECT INTO 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-127">SELECT INTO and FileTables</span></span>  
 <span data-ttu-id="ac511-128">FileTable 中的 SELECT INTO 语句将不在创建的目标表上传播 FileTable 语义（就像常规表中的 FILESTREAM 列一样）。</span><span class="sxs-lookup"><span data-stu-id="ac511-128">SELECT INTO statements from a FileTable will not propagate the FileTable semantics on the created destination table (just like FILESTREAM columns in a regular table).</span></span> <span data-ttu-id="ac511-129">所有目标表列的行为就像常规列的行为一样。</span><span class="sxs-lookup"><span data-stu-id="ac511-129">All the destination table columns will behave just like normal columns.</span></span> <span data-ttu-id="ac511-130">没有任何 FileTable 语义与之关联。</span><span class="sxs-lookup"><span data-stu-id="ac511-130">They will not have any FileTable semantics associated with them.</span></span>  
  
##  <a name="triggers-and-filetables"></a><a name="OtherTriggers"></a> <span data-ttu-id="ac511-131">触发器和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-131">Triggers and FileTables</span></span>  
 <span data-ttu-id="ac511-132">**DDL（数据定义语言）触发器**</span><span class="sxs-lookup"><span data-stu-id="ac511-132">**DDL (Data Definition Language) Triggers**</span></span>  
 <span data-ttu-id="ac511-133">对于 DDL 触发器用于 FileTable 没有特别的注意事项。</span><span class="sxs-lookup"><span data-stu-id="ac511-133">There are no special considerations for DDL triggers with FileTables.</span></span> <span data-ttu-id="ac511-134">对于 Create/Alter 数据库操作以及针对 FileTable 的 CREATE/ALTER TABLE 操作，普通 DDL 触发器将被激发。</span><span class="sxs-lookup"><span data-stu-id="ac511-134">Normal DDL triggers will fire for Create/Alter database operations as well as CREATE/ALTER TABLE operations for FileTables.</span></span> <span data-ttu-id="ac511-135">触发器可以通过调用 EVENTDATA() 函数来检索包括 DDL 命令文本和其他信息的实际事件数据。</span><span class="sxs-lookup"><span data-stu-id="ac511-135">Triggers can retrieve the actual event data that includes the DDL command text and other information by calling the EVENTDATA() function.</span></span> <span data-ttu-id="ac511-136">不添加新事件，也不更改现有 Eventdata 架构。</span><span class="sxs-lookup"><span data-stu-id="ac511-136">There are no new events or changes to the existing Eventdata schema.</span></span>  
  
 <span data-ttu-id="ac511-137">**DML（数据操作语言）触发器**</span><span class="sxs-lookup"><span data-stu-id="ac511-137">**DML (Data Manipulation Language) Triggers**</span></span>  
 <span data-ttu-id="ac511-138">在 DDL 操作过程中，将应用这些限制来创建触发器。</span><span class="sxs-lookup"><span data-stu-id="ac511-138">These restrictions will be enforced during the DDL operation to create triggers.</span></span>  
  
-   <span data-ttu-id="ac511-139">FileTable 不支持用于 DML 操作的 INSTEAD OF 触发器。</span><span class="sxs-lookup"><span data-stu-id="ac511-139">FileTables will NOT support INSTEAD OF triggers for DML operations.</span></span> <span data-ttu-id="ac511-140">对包含 FILESTREAM 列的所有表已存在一个限制。</span><span class="sxs-lookup"><span data-stu-id="ac511-140">This is an existing restriction on all tables that contain FILESTREAM columns.</span></span>  
  
-   <span data-ttu-id="ac511-141">FileTable 支持用于 DML 操作的 AFTER 触发器。</span><span class="sxs-lookup"><span data-stu-id="ac511-141">FileTables will support AFTER triggers for DML operations.</span></span>  
  
-   <span data-ttu-id="ac511-142">在 FileTable 上定义的触发器不能更新任何 FileTable（包括父 FileTable）。</span><span class="sxs-lookup"><span data-stu-id="ac511-142">Triggers defined on a FileTable cannot update any FileTables (including the parent FileTable).</span></span> <span data-ttu-id="ac511-143">存在此限制主要是为了防止在同一事务中触发器与文件系统访问持有的锁发生锁定冲突。</span><span class="sxs-lookup"><span data-stu-id="ac511-143">This restriction exists mainly to prevent a trigger from getting into locking conflicts with the locks held by the file system access in the same transaction.</span></span>  
  
 <span data-ttu-id="ac511-144">**非事务性访问及其对触发器的影响**</span><span class="sxs-lookup"><span data-stu-id="ac511-144">**Non-transactional access and its effects on triggers**</span></span>  
 -   <span data-ttu-id="ac511-145">在数据库中允许非事务性更新访问时，可以在任何表中执行 FILESTREAM 数据的就地更新，包括该数据库中的 FileTable。</span><span class="sxs-lookup"><span data-stu-id="ac511-145">When non-transactional update access is allowed in a database, it is possible to do in-place update of the FILESTREAM data in any table, including FileTable in that database.</span></span> <span data-ttu-id="ac511-146">由于这种可能性，FILESTREAM 内容的前像可能不能由触发器使用。</span><span class="sxs-lookup"><span data-stu-id="ac511-146">Due to this possibility, the before image of the FILESTREAM contents may not be available for use by the trigger.</span></span>  
  
-   <span data-ttu-id="ac511-147">对于通过文件系统的非事务性更新操作，SQL Server 将创建一个内部事务来捕获 CloseHandle 操作，任何定义的 DML 触发器可能作为该事务的一部分激发。</span><span class="sxs-lookup"><span data-stu-id="ac511-147">For non-transactional update operations through File system, SQL Server will create an internal transaction to capture the CloseHandle operation and the any defined DML triggers may be fired as part of that transaction.</span></span> <span data-ttu-id="ac511-148">将不阻止在触发器主体内对此类事务进行的回滚，但不回滚对该 FILESTREAM 所做的更改。</span><span class="sxs-lookup"><span data-stu-id="ac511-148">A rollback such a transaction inside the trigger body, while not prevented, does not roll back the changes done to the FILESTREAM.</span></span>  <span data-ttu-id="ac511-149">即使 FILESTREAM 内容可能已经更改，这种回滚仍可能会阻止 Update 触发器激发。</span><span class="sxs-lookup"><span data-stu-id="ac511-149">Such a rollback may also prevent the Update triggers from being fired, even though the FILESTREAM contents may have been changed.</span></span>  
  
-   <span data-ttu-id="ac511-150">除了这些影响外，FileTable 的触发器还需要处理一些其他行为。</span><span class="sxs-lookup"><span data-stu-id="ac511-150">In addition to these impacts, triggers on FileTables need to deal with couple of additional behaviors</span></span>  
  
    -   <span data-ttu-id="ac511-151">通过文件系统对 FileTable 执行非事务性更新操作时，FILESTREAM 内容可能被其他 Win32 操作以独占方式锁定，从而不能通过触发器主体对其进行读/写访问。</span><span class="sxs-lookup"><span data-stu-id="ac511-151">In case of non-transactional update operations on FileTable through the File system, it is possible that the FILESTREAM contents may be exclusively locked by other Win32 operations and may not be accessible for read/write through the trigger body.</span></span> <span data-ttu-id="ac511-152">在这些情况下，任何在触发器主体中对 FILESTREAM 内容进行访问的尝试都可能导致“共享冲突”错误。</span><span class="sxs-lookup"><span data-stu-id="ac511-152">In such cases, any attempt to access the FILESTREAM contents within the trigger body may give a "Sharing Violation" error.</span></span> <span data-ttu-id="ac511-153">触发器应设计为可正确地处理这类错误。</span><span class="sxs-lookup"><span data-stu-id="ac511-153">Triggers should be designed to handle such errors appropriately.</span></span>  
  
    -   <span data-ttu-id="ac511-154">FILESTREAM 的后像可能不稳定，原因是由于在文件系统访问中允许共享模式，其他非事务性更新也会同时频繁地向 FILESTREAM 写入内容。</span><span class="sxs-lookup"><span data-stu-id="ac511-154">AFTER image of the FILESTREAM may not be stable since in some cases it may be actively being written by other non-transactional updates at the same time (due to the sharing modes permitted in the File system access).</span></span>  
  
-   <span data-ttu-id="ac511-155">在恢复操作期间，Win32 句柄的异常终止（如通过管理员或数据库崩溃显式终止 Win32 句柄）将不执行用户触发器，即使 FILESTREAM 内容可能已被异常终止的 Win32 应用程序更改。</span><span class="sxs-lookup"><span data-stu-id="ac511-155">Abnormal termination of Win32 handles, like explicit killing of Win32 handles by an admin OR a database crash, will not execute user triggers during the recovery operations, even though the FILESTREAM content may have been changed by the abnormally terminated Win32 application.</span></span>  
  
##  <a name="views-and-filetables"></a><a name="OtherViews"></a> <span data-ttu-id="ac511-156">视图和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-156">Views and FileTables</span></span>  
 <span data-ttu-id="ac511-157">**视图**</span><span class="sxs-lookup"><span data-stu-id="ac511-157">**Views**</span></span>  
 <span data-ttu-id="ac511-158">可以像为任何其他表一样为 FileTable 创建视图。</span><span class="sxs-lookup"><span data-stu-id="ac511-158">A view can be created on a FileTable as on any other table.</span></span> <span data-ttu-id="ac511-159">但是对于为 FileTable 创建的视图有以下注意事项：</span><span class="sxs-lookup"><span data-stu-id="ac511-159">However the following considerations apply to a view created on a FileTable:</span></span>  
  
-   <span data-ttu-id="ac511-160">视图将不具有任何 FileTable 语义，</span><span class="sxs-lookup"><span data-stu-id="ac511-160">View will not have any FileTable semantics.</span></span> <span data-ttu-id="ac511-161">即，视图中的列（包括“文件属性”列）的行为与常规视图列一样，不具有任何特殊语义，对于表示文件/目录的行也是如此。</span><span class="sxs-lookup"><span data-stu-id="ac511-161">i.e. the columns in the view (including File Attribute columns) behave just like normal view columns without any special semantics and same is true for rows representing Files/directories.</span></span>  
  
-   <span data-ttu-id="ac511-162">可以基于“可更新视图”语义更新视图，但是基础表约束可能拒绝更新，就像在表中一样。</span><span class="sxs-lookup"><span data-stu-id="ac511-162">View may be updateable based on the "updateable view" semantics, but the underlying table constraints can reject the updates just like in the table.</span></span>  
  
-   <span data-ttu-id="ac511-163">可以通过将文件的路径添加为视图中的显式列，在视图中显示该路径。</span><span class="sxs-lookup"><span data-stu-id="ac511-163">File path for a file can be visualized in the view by adding it as an explicit column in the view.</span></span> <span data-ttu-id="ac511-164">例如：</span><span class="sxs-lookup"><span data-stu-id="ac511-164">For example:</span></span>  
  
     `CREATE VIEW MP3FILES AS SELECT column1, column2, ..., GetFileNamespacePath() AS PATH, column3,...  FROM Documents`  
  
 <span data-ttu-id="ac511-165">**索引视图**</span><span class="sxs-lookup"><span data-stu-id="ac511-165">**Indexed Views**</span></span>  
 <span data-ttu-id="ac511-166">当前索引视图不能包括 FILESTREAM 列或依赖 FILESTREAM 列的计算/持久计算列。</span><span class="sxs-lookup"><span data-stu-id="ac511-166">Currently Indexed views cannot include FILESTREAM columns or computed/persisted computed columns that depend on the FILESTREAM columns.</span></span> <span data-ttu-id="ac511-167">对于在 FileTable 上定义的视图也同样如此。</span><span class="sxs-lookup"><span data-stu-id="ac511-167">This behavior remains unchanged with views defined on the FileTable also.</span></span>  
  
##  <a name="snapshot-isolation-and-filetables"></a><a name="OtherSnapshots"></a> <span data-ttu-id="ac511-168">快照隔离和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-168">Snapshot Isolation and FileTables</span></span>  
 <span data-ttu-id="ac511-169">已提交读快照隔离 (RCSI) 和快照隔离 (SI) 依赖是否具有可用于读取器的数据快照，甚至正在对数据进行更新时也是如此。</span><span class="sxs-lookup"><span data-stu-id="ac511-169">Read Committed Snapshot Isolation (RCSI) and Snapshot Isolation (SI) rely on the ability to have a snapshot of the data available for readers even when update operations are happening on the data.</span></span> <span data-ttu-id="ac511-170">但是，FileTable 允许对文件流数据进行非事务性写访问。</span><span class="sxs-lookup"><span data-stu-id="ac511-170">However FileTables allow non-transactional write access to Filestream data.</span></span> <span data-ttu-id="ac511-171">因此，在包含 FileTable 的数据库中使用这些功能存在以下限制：</span><span class="sxs-lookup"><span data-stu-id="ac511-171">As a result, the following restrictions apply to the use of these features in databases that contain FileTables:</span></span>  
  
-   <span data-ttu-id="ac511-172">可以更改包含 FileTable 的数据库以启用 RCSI/SI。</span><span class="sxs-lookup"><span data-stu-id="ac511-172">A database that contains FileTables can be altered to enable RCSI/SI.</span></span>  
  
-   <span data-ttu-id="ac511-173">将对数据库的非事务性访问设置为 FULL 时，在 RCSI 或 SI 下运行的事务将具有以下行为：</span><span class="sxs-lookup"><span data-stu-id="ac511-173">When non_transactional access is set to FULL for the database, then a transaction running under RCSI or SI has the following behavior:</span></span>  
  
    -   <span data-ttu-id="ac511-174">对 FileTable file_stream 列的任何 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 读取将失败。</span><span class="sxs-lookup"><span data-stu-id="ac511-174">Any [!INCLUDE[tsql](../../../includes/tsql-md.md)] reads of the FileTable file_stream column fail.</span></span> <span data-ttu-id="ac511-175">对该列的 INSERT 和 UPDATE 仍将成功，前提是这些操作不会从 file_stream 列中读取数据。</span><span class="sxs-lookup"><span data-stu-id="ac511-175">INSERT and UPDATE to the column still succeed, as long as they do not read from the file_stream column.</span></span>  
  
    -   <span data-ttu-id="ac511-176">如果 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句指定 READCOMMITTEDLOCK 表提示，则读取将成功，并获取对行的锁定而不是使用行版本控制。</span><span class="sxs-lookup"><span data-stu-id="ac511-176">If the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement specifies READCOMMITTEDLOCK table hints, the reads succeed, and take locks on the rows, rather than use row versioning.</span></span>  
  
    -   <span data-ttu-id="ac511-177">事务性的 Win32 FileStream 打开请求也将失败。</span><span class="sxs-lookup"><span data-stu-id="ac511-177">Transacted Win32 FileStream open requests also fail.</span></span>  
  
    -   <span data-ttu-id="ac511-178">非事务性的 FileTable Win32 访问将成功。</span><span class="sxs-lookup"><span data-stu-id="ac511-178">Non-transacted FileTable Win32 access succeeds.</span></span> <span data-ttu-id="ac511-179">将不影响 FileTable 执行的所有内部查询。</span><span class="sxs-lookup"><span data-stu-id="ac511-179">All internal queries done by FileTable are not affected.</span></span>  
  
    -   <span data-ttu-id="ac511-180">无论数据库选项如何（READ_COMMITTED_SNAPSHOT 或 ALLOW_SNAPSHOT_ISOLATION），全文索引编制始终会成功。</span><span class="sxs-lookup"><span data-stu-id="ac511-180">Fulltext indexing always succeeds, no matter what the database options are (READ_COMMITTED_SNAPSHOT or ALLOW_SNAPSHOT_ISOLATION).</span></span>  
  
##  <a name="readable-secondary-databases"></a><a name="readsec"></a> <span data-ttu-id="ac511-181">可读辅助数据库</span><span class="sxs-lookup"><span data-stu-id="ac511-181">Readable Secondary Databases</span></span>  
 <span data-ttu-id="ac511-182">有关快照的注意事项同样适用于可读辅助数据库，如上一节 [快照隔离和 FileTable](#OtherSnapshots)中所述。</span><span class="sxs-lookup"><span data-stu-id="ac511-182">The same considerations apply to readable secondary databases as to snapshots, as described in the preceding section, [Snapshot Isolation and FileTables](#OtherSnapshots).</span></span>  
  
##  <a name="contained-databases-and-filetables"></a><a name="CDB"></a> <span data-ttu-id="ac511-183">包含的数据库和 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-183">Contained Databases and FileTables</span></span>  
 <span data-ttu-id="ac511-184">FileTable 功能所依赖的 FILESTREAM 功能要求在数据库外部的一些配置。</span><span class="sxs-lookup"><span data-stu-id="ac511-184">The FILESTREAM feature on which the FileTable feature depends requires some configuration outside of the database.</span></span> <span data-ttu-id="ac511-185">因此，使用 FILESTREAM 或 FileTable 的数据库并未被完全包含。</span><span class="sxs-lookup"><span data-stu-id="ac511-185">Therefore a database that uses FILESTREAM or FileTable is not fully contained.</span></span>  
  
 <span data-ttu-id="ac511-186">如果您想要使用包含的数据库的某些功能（例如包含的用户），则可以将数据库包含设置为 PARTIAL。</span><span class="sxs-lookup"><span data-stu-id="ac511-186">You can set database containment to PARTIAL if you want to use certain features of contained databases, such as contained users.</span></span> <span data-ttu-id="ac511-187">但在此情况下，您必须知道某些数据库设置未包含在数据库中，并且在数据库移动时不自动移动。</span><span class="sxs-lookup"><span data-stu-id="ac511-187">In this case, however, you must be aware that some of the database settings are not contained in the database and are not automatically moved when the database moves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac511-188">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac511-188">See Also</span></span>  
 [<span data-ttu-id="ac511-189">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="ac511-189">Manage FileTables</span></span>](manage-filetables.md)  
  
  
