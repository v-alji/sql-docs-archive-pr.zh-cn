---
title: 管理 FileTable | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], security
- FileTables [SQL Server], managing access
ms.assetid: 93af982c-b4fe-4be0-8268-11f86dae27e1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a15a914c243f1fafd3b913d98113e984bf533086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689437"
---
# <a name="manage-filetables"></a><span data-ttu-id="a4bc3-102">管理 FileTable</span><span class="sxs-lookup"><span data-stu-id="a4bc3-102">Manage FileTables</span></span>
  <span data-ttu-id="a4bc3-103">说明用于管理 FileTable 的常见管理任务。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-103">Describes common administrative tasks for managing FileTables.</span></span>  
  
##  <a name="how-to-get-a-list-of-filetables-and-related-objects"></a><a name="HowToEnumerate"></a> <span data-ttu-id="a4bc3-104">如何：获取 FileTable 和相关对象的列表</span><span class="sxs-lookup"><span data-stu-id="a4bc3-104">How To: Get a List of FileTables and Related Objects</span></span>  
 <span data-ttu-id="a4bc3-105">若要获取 FileTable 的列表，请查询下列目录视图之一：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-105">To get a list of FileTables, query one of the following catalog views:</span></span>  
  
-   [<span data-ttu-id="a4bc3-106">sys.filetables (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a4bc3-106">sys.filetables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-filetables-transact-sql)  
  
-   <span data-ttu-id="a4bc3-107">[sys.tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)（检查 **is_filetable** 列的值。）</span><span class="sxs-lookup"><span data-stu-id="a4bc3-107">[sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql) (Check the value of the **is_filetable** column.)</span></span>  
  
```sql  
SELECT * FROM sys.filetables;  
GO  
  
SELECT * FROM sys.tables WHERE is_filetable = 1;  
GO  
```  
  
 <span data-ttu-id="a4bc3-108">若要获取在创建关联的 FileTable 时创建的系统定义对象的列表，请查询目录视图 [sys.filetable_system_defined_objects (Transact-SQL) ](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-108">To get a list of the system-defined objects that were created when the associated FileTables were created, query the catalog view [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).</span></span>  
  
```sql  
SELECT object_id, OBJECT_NAME(object_id) AS 'Object Name'  
    FROM sys.filetable_system_defined_objects  
    WHERE object_id = filetable_object_id;  
GO  
```  
  
##  <a name="disabling-and-re-enabling-non-transactional-access-at-the-database-level"></a><a name="BasicsDisabling"></a> <span data-ttu-id="a4bc3-109">禁用和重新启用数据库级别的非事务性访问权限</span><span class="sxs-lookup"><span data-stu-id="a4bc3-109">Disabling and Re-enabling Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="a4bc3-110">若要获取执行某些管理任务所需的独占访问权限，可能必须暂时禁用非事务性访问权限。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-110">To acquire the exclusive access that is required for certain administrative tasks, you may have to disable non-transactional access temporarily.</span></span>  
  
 <span data-ttu-id="a4bc3-111">**更改非事务性访问级别时 ALTER DATABASE 语句的行为**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-111">**Behavior of the ALTER DATABASE statement when changing the level of non-transactional access**</span></span>  
  
-   <span data-ttu-id="a4bc3-112">只要存在与请求的操作冲突的打开的文件句柄，在将非事务性访问权限设置为 READ_ONLY 或 OFF 时，ALTER DATABASE 命令就不会向用户返回控制。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-112">When you set non-transactional access to READ_ONLY or OFF, the ALTER DATABASE command does not return control to the user as long as there are open file handles that conflict with the requested operation.</span></span> <span data-ttu-id="a4bc3-113">与此操作冲突的文件句柄包括下列内容：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-113">The file handles that conflict with this operation include the following:</span></span>  
  
    -   <span data-ttu-id="a4bc3-114">当您将访问权限设置为 **NONE**时，则包括所有打开的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-114">When you are setting access to **NONE**, all open file handles.</span></span>  
  
    -   <span data-ttu-id="a4bc3-115">当你将访问权限设置为 **READ_ONLY**时，则包括打开以供写入访问的所有文件句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-115">When you are setting access to **READ_ONLY**, all file handles opened for write access.</span></span>  
  
     <span data-ttu-id="a4bc3-116">有关终止打开的文件句柄的信息，请参阅本主题中的 [终止与 FileTable 关联的打开的文件句柄](#BasicsKilling) 。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-116">For information about killing open file handles, see [Killing Open File Handles Associated with a FileTable](#BasicsKilling) in this topic.</span></span>  
  
     <span data-ttu-id="a4bc3-117">如果 ALTER DATABASE 命令被取消或因超时而结束，则不更改事务性访问级别。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-117">If the ALTER DATABASE command is canceled or ends with a timeout, then the level of transactional access is not changed.</span></span>  
  
-   <span data-ttu-id="a4bc3-118">如果调用带 WITH \<termination> 子句 (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT) 的 ALTER DATABASE 语句，则将终止所有打开的非事务性文件句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-118">If you call the ALTER DATABASE statement with a WITH \<termination> clause (ROLLBACK AFTER integer [ SECONDS ] | ROLLBACK IMMEDIATE | NO_WAIT), then all open non-transactional file handles are killed.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a4bc3-119">终止打开的文件句柄可能会导致用户丢失未保存的数据。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-119">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="a4bc3-120">此行为与文件系统自身的行为一致。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-120">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
 <span data-ttu-id="a4bc3-121">**禁用非事务性访问的影响**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-121">**Effects of disabling non-transactional access**</span></span>  
  
 <span data-ttu-id="a4bc3-122">更改数据库级别的非事务性访问级别会对数据库级别目录下的 FileTable 目录产生下列影响：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-122">Changing the level of non-transactional access at the database level has the following effects on the FileTable directories under the database-level directory:</span></span>  
  
-   <span data-ttu-id="a4bc3-123">当您将访问权限设置为 **NONE**时，将不再能够访问或看到所有 FileTable 目录及其内容。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-123">When you set access to **NONE**, then all the FileTable directories and their contents are no longer accessible or visible.</span></span>  
  
-   <span data-ttu-id="a4bc3-124">将访问权限设置为 **READ_ONLY**时，所有 FileTable 目录及其内容还是只读的。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-124">When you set access to **READ_ONLY**, then all the FileTable directories and their contents are also read-only.</span></span>  
  
 <span data-ttu-id="a4bc3-125">在实例级别禁用 FILESTREAM 将会对该实例上的数据库级别目录及其下的 FileTable 目录产生下列影响：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-125">Disabling FILESTREAM at the instance level has the following effects on the database-level directories on that instance, and the FileTable directories under them:</span></span>  
  
-   <span data-ttu-id="a4bc3-126">如果在实例级别禁用 FILESTREAM，将看不到该实例上的任何数据库级别目录。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-126">None of the database-level directories on the instance are visible if FILESTREAM is disabled at the instance level.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-non-transactional-access-at-the-database-level"></a><a name="HowToDisable"></a> <span data-ttu-id="a4bc3-127">如何：禁用和重新启用数据库级别的非事务性访问权限</span><span class="sxs-lookup"><span data-stu-id="a4bc3-127">How To: Disable and Re-enable Non-Transactional Access at the Database Level</span></span>  
 <span data-ttu-id="a4bc3-128">有关详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-128">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="a4bc3-129">**禁用完全非事务性访问权限**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-129">**To disable full non-transactional access**</span></span>  
 <span data-ttu-id="a4bc3-130">调用 **ALTER DATABASE** 语句并将 **NON_TRANSACTED_ACCESS 的值设置** 为 **READ_ONLY** 或 **OFF**。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-130">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **READ_ONLY** or **OFF**.</span></span>  
  
```sql  
-- Disable write access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = READ_ONLY );  
GO  
  
-- Disable non-transactional access.  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = OFF );  
GO  
```  
  
 <span data-ttu-id="a4bc3-131">**重新启用完全非事务性访问权限**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-131">**To re-enable full non-transactional access**</span></span>  
 <span data-ttu-id="a4bc3-132">调用 **ALTER DATABASE** 语句并将 **NON_TRANSACTED_ACCESS** 的值设置为 **FULL**。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-132">Call the **ALTER DATABASE** statement and SET the value of **NON_TRANSACTED_ACCESS** to **FULL**.</span></span>  
  
```sql  
ALTER DATABASE database_name  
    SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL );  
GO  
```  
  
###  <a name="how-to-ensure-the-visibility-of-the-filetables-in-a-database"></a><a name="visible"></a> <span data-ttu-id="a4bc3-133">如何：确保数据库中的 FileTable 的可见性</span><span class="sxs-lookup"><span data-stu-id="a4bc3-133">How to: Ensure the Visibility of the FileTables in a Database</span></span>  
 <span data-ttu-id="a4bc3-134">当满足以下所有条件时，则可看到数据库级别目录及其下的 FileTable 目录：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-134">A database-level directory and the FileTable directories under it are visible when all of these conditions are true:</span></span>  
  
1.  <span data-ttu-id="a4bc3-135">在实例级别启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-135">FILESTREAM is enabled at the instance level.</span></span>  
  
2.  <span data-ttu-id="a4bc3-136">在数据库级别启用非事务性访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-136">Non-transactional access is enabled at the database level.</span></span>  
  
3.  <span data-ttu-id="a4bc3-137">在数据库级别指定了有效目录。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-137">A valid directory has been specified at the database level.</span></span>  
  
##  <a name="disabling-and-re-enabling-the-filetable-namespace-at-the-table-level"></a><a name="BasicsEnabling"></a> <span data-ttu-id="a4bc3-138">禁用和重新启用表级别 FileTable 命名空间</span><span class="sxs-lookup"><span data-stu-id="a4bc3-138">Disabling and Re-enabling the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="a4bc3-139">禁用 FileTable 命名空间将会禁用所有系统定义的约束并触发使用 FileTable 创建的约束。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-139">Disabling the FileTable namespace disables all the system-defined constraints and triggers that were created with the FileTable.</span></span> <span data-ttu-id="a4bc3-140">在必须通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 操作大规模重新组织 FileTable 而不产生强制 FileTable 语义的开销时，这一点很有用。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-140">This is useful in cases where a FileTable has to be reorganized on a large scale by using [!INCLUDE[tsql](../../includes/tsql-md.md)] operations without incurring the expense of enforcing FileTable semantics.</span></span> <span data-ttu-id="a4bc3-141">但是，这些操作会将 FileTable 置于不一致的状态，会阻止重新启用 FileTable 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-141">However these operations can leave the FileTable in an inconsistent state, and can prevent the re-enabling of the FileTable namespace.</span></span>  
  
 <span data-ttu-id="a4bc3-142">禁用 FileTable 命名空间具有下列结果：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-142">Disabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="a4bc3-143">FileTable 列和数据被从表中物理删除。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-143">FileTable columns and data are not physically dropped from the table.</span></span>  
  
-   <span data-ttu-id="a4bc3-144">FileTable 目录及其包含的文件和目录不再出现在文件系统中，且不可用于文件 I/O 访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-144">The FileTable directory and the files and directories that it contains disappear from the file system and are not available for file i/o access.</span></span>  
  
-   <span data-ttu-id="a4bc3-145">无法删除和重新创建系统定义的 FileTable 列；但是，对于 DML 操作，它们的行为与普通列无异。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-145">System-defined FileTable columns cannot be dropped and recreated; otherwise, however, they behave like ordinary columns for DML operations.</span></span>  
  
-   <span data-ttu-id="a4bc3-146">打开的文件句柄可防止 FileTable 约束被禁用，因为此操作需要使用表上的架构锁。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-146">Open file handles prevent the FileTable constraints from being disabled, since this operation requires a schema lock on the table.</span></span>  
  
-   <span data-ttu-id="a4bc3-147">强制所有 FileTable 语义的操作（包括系统定义的约束和触发器）在 FileTable 命名空间被禁用后停止。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-147">Enforcement of all the FileTable semantics, including system-defined constraints and triggers, stops after the FileTable namespace is disabled.</span></span>  
  
 <span data-ttu-id="a4bc3-148">重新启用 FileTable 命名空间会产生下列结果：</span><span class="sxs-lookup"><span data-stu-id="a4bc3-148">Re-enabling a FileTable namespace has the following results:</span></span>  
  
-   <span data-ttu-id="a4bc3-149">检查 FileTable 以了解一致性。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-149">The FileTable is checked for consistency.</span></span> <span data-ttu-id="a4bc3-150">如果找到不一致处，则引发错误且 FileTable 保持禁用状态；否则，将重新启用 FileTable。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-150">If inconsistencies are found, then an error is raised and the FileTable remains disabled; otherwise, the FileTable is re-enabled.</span></span>  
  
-   <span data-ttu-id="a4bc3-151">强制 FileTable 语义的操作（包括系统定义的约束和触发器）将恢复。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-151">The enforcement of FileTable semantics, including system-defined constraints and triggers, is restored.</span></span>  
  
-   <span data-ttu-id="a4bc3-152">FileTable 目录及其包含的文件和目录将在文件系统中再次可见，且可用于文件 I/O 访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-152">The FileTable directory and the files and directories that it contains become visible in the file system and become available for file i/o access.</span></span>  
  
###  <a name="how-to-disable-and-re-enable-the-filetable-namespace-at-the-table-level"></a><a name="HowToEnableNS"></a> <span data-ttu-id="a4bc3-153">如何：禁用和重新启用表级别的 FileTable 命名空间</span><span class="sxs-lookup"><span data-stu-id="a4bc3-153">How To: Disable and Re-enable the FileTable Namespace at the Table Level</span></span>  
 <span data-ttu-id="a4bc3-154">使用 **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** 选项调用 ALTER TABLE 语句。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-154">Call the ALTER TABLE statement with the **{ ENABLE | DISABLE } FILETABLE_NAMESPACE** option.</span></span>  
  
 <span data-ttu-id="a4bc3-155">**禁用 FileTable 命名空间**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-155">**To disable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    DISABLE FILETABLE_NAMESPACE;  
GO  
```  
  
 <span data-ttu-id="a4bc3-156">**重新启用 FileTable 命名空间**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-156">**To re-enable the FileTable namespace**</span></span>  
 ```sql  
ALTER TABLE filetable_name  
    ENABLE FILETABLE_NAMESPACE;  
GO  
```  
  
##  <a name="killing-open-file-handles-associated-with-a-filetable"></a><a name="BasicsKilling"></a> <span data-ttu-id="a4bc3-157">终止与 FileTable 关联的打开的文件句柄</span><span class="sxs-lookup"><span data-stu-id="a4bc3-157">Killing Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="a4bc3-158">FileTable 中存储的文件的打开句柄可以阻止某些管理任务所需的独占访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-158">Open handles to the files stored in a FileTable can prevent the exclusive access that is required for certain administrative tasks.</span></span> <span data-ttu-id="a4bc3-159">若要启用紧急任务，您可能要终止与一个或多个 FileTable 关联的打开的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-159">To enable urgent tasks, you may have to kill open file handles associated with one or more FileTables.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a4bc3-160">终止打开的文件句柄可能会导致用户丢失未保存的数据。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-160">Killing open file handles may cause users to lose unsaved data.</span></span> <span data-ttu-id="a4bc3-161">此行为与文件系统自身的行为一致。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-161">This behavior is consistent with the behavior of the file system itself.</span></span>  
  
###  <a name="how-to-get-a-list-of-open-file-handles-associated-with-a-filetable"></a><a name="HowToListOpen"></a> <span data-ttu-id="a4bc3-162">如何：获取与 FileTable 关联的打开的文件句柄的列表</span><span class="sxs-lookup"><span data-stu-id="a4bc3-162">How To: Get a List of Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="a4bc3-163">查询目录视图 [sys.dm_filestream_non_transacted_handles (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-163">Query the catalog view [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.dm_filestream_non_transacted_handles;  
GO  
```  
  
###  <a name="how-to-kill-open-file-handles-associated-with-a-filetable"></a><a name="HowToKill"></a> <span data-ttu-id="a4bc3-164">如何：终止与 FileTable 关联的打开的文件句柄</span><span class="sxs-lookup"><span data-stu-id="a4bc3-164">How To: Kill Open File Handles Associated with a FileTable</span></span>  
 <span data-ttu-id="a4bc3-165">使用相应参数调用存储过程 [sp_kill_filestream_non_transacted_handles (Transact-SQL)](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) 以终止数据库或 FileTable 中所有打开的文件句柄或终止特定句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-165">Call the stored procedure [sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-kill-filestream-non-transacted-handles) with the appropriate arguments to kill all open file handles in the database or in the FileTable, or to kill a specific handle.</span></span>  
  
```  
USE database_name;  
  
-- Kill all open handles in all the filetables in the database.  
EXEC sp_kill_filestream_non_transacted_handles;  
GO  
  
-- Kill all open handles in a single filetable.  
EXEC sp_kill_filestream_non_transacted_handles @table_name = 'filetable_name';  
GO  
  
-- Kill a single handle.  
EXEC sp_kill_filestream_non_transacted_handles @handle_id = integer_handle_id;  
GO  
```  
  
###  <a name="how-to-identify-the-locks-held-by-filetables"></a><a name="HowToIdentifyLocks"></a> <span data-ttu-id="a4bc3-166">如何：确定 FileTable 持有的锁</span><span class="sxs-lookup"><span data-stu-id="a4bc3-166">How to: Identify the Locks Held by FileTables</span></span>  
 <span data-ttu-id="a4bc3-167">FileTable 持有的大多数锁与应用程序打开的文件相对应。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-167">Most locks taken by FileTables correspond to files opened by applications.</span></span>  
  
 <span data-ttu-id="a4bc3-168">**确定打开的文件和关联锁**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-168">**To identify open files and the associated locks**</span></span>  
 <span data-ttu-id="a4bc3-169">将动态管理视图 [sys.dm_tran_locks (Transact SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) 中的 **request_owner_id** 字段与 [sys.dm_filestream_non_transacted_handles (Transact SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql)中的 **fcb_id** 字段进行联接。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-169">Join the **request_owner_id** field in the dynamic management view [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) with the **fcb_id** field in [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql).</span></span> <span data-ttu-id="a4bc3-170">在某些情况下，锁并不对应单个打开的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-170">In some cases, the lock does not correspond to a single open file handle.</span></span>  
  
```sql  
SELECT opened_file_name  
    FROM sys.dm_filestream_non_transacted_handles  
    WHERE fcb_id IN  
        ( SELECT request_owner_id FROM sys.dm_tran_locks );  
GO  
```  
  
##  <a name="filetable-security"></a><a name="BasicsSecurity"></a> <span data-ttu-id="a4bc3-171">FileTable 安全性</span><span class="sxs-lookup"><span data-stu-id="a4bc3-171">FileTable Security</span></span>  
 <span data-ttu-id="a4bc3-172">存储在 FileTable 中的文件和目录仅受 SQL Server 安全机制的保护。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-172">The files and directories stored in FileTables are secured by SQL Server security only.</span></span> <span data-ttu-id="a4bc3-173">将对文件系统访问和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 访问强制实施基于表和列的安全性。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-173">Table and column-based security is enforced for file system access as well as [!INCLUDE[tsql](../../includes/tsql-md.md)] access.</span></span> <span data-ttu-id="a4bc3-174">不支持 Windows 文件系统安全 API 和 ACL 设置。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-174">Windows file system security APIs and ACL settings are not supported.</span></span>  
  
 <span data-ttu-id="a4bc3-175">由于文件数据作为 FILESTREAM 列存储在 FileTable 中，因此还将对 FileTable 应用 FILESTREAM 文件组和容器所适用的安全性和访问权限。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-175">The security and access permissions that are applicable to FILESTREAM filegroups and containers also apply to FileTables, since the file data is stored as a FILESTREAM column in the FileTable.</span></span>  
  
 <span data-ttu-id="a4bc3-176">**FileTable 安全性和 Transact-SQL 访问**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-176">**FileTable Security and Transact-SQL Access**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="a4bc3-177">将像对任何其他表一样保护对 FileTable 中数据的访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-177">access to data in FileTables is secured in the same way as any other table.</span></span> <span data-ttu-id="a4bc3-178">对访问或更改数据的每个操作进行相应的表级别和列级别安全检查。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-178">Appropriate table and column-level security checks are done for every operation that accesses or changes the data.</span></span>  
  
 <span data-ttu-id="a4bc3-179">**FileTable 安全性和文件系统访问**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-179">**FileTable Security and File System Access**</span></span>  
 <span data-ttu-id="a4bc3-180">文件系统 API 需要对 FileTable 中整个行的相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 权限（表级别权限）来打开存储在 FileTable 中的文件或目录的句柄。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-180">File system APIs require appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions on the entire row in the FileTable (that is, table-level permission) to open a handle to a file or directory stored in the FileTable.</span></span> <span data-ttu-id="a4bc3-181">如果用户对 FileTable 中的任何列没有相应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 权限，则将拒绝文件系统访问。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-181">If the user does not have the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission on any column in the FileTable, then file system access is denied.</span></span>  
  
##  <a name="backup-and-filetables"></a><a name="OtherBackup"></a> <span data-ttu-id="a4bc3-182">备份和 FileTable</span><span class="sxs-lookup"><span data-stu-id="a4bc3-182">Backup and FileTables</span></span>  
 <span data-ttu-id="a4bc3-183">当您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份 FileTable 时，FILESTREAM 数据将与数据库中的结构化数据一起备份。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-183">When you use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to back up a FileTable, the FILESTREAM data is backed up with the structured data in the database.</span></span> <span data-ttu-id="a4bc3-184">如果您不想将 FILESTREAM 数据与关系数据一起备份，则可以使用部分备份将 FILESTREAM 文件组排除在外。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-184">If you do not want to back up FILESTREAM data with relational data, you can use a partial backup to exclude FILESTREAM filegroups.</span></span>  
  
 <span data-ttu-id="a4bc3-185">**FileTable 备份的事务一致性**</span><span class="sxs-lookup"><span data-stu-id="a4bc3-185">**Transactional Consistency of FileTable Backups**</span></span>  
  
 <span data-ttu-id="a4bc3-186">很多管理工具和操作（包括备份、日志备份和事务性复制）通过读取事务日志来读取事务上一致的数据。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-186">Many administrative tools and operations, (including backup, log backup, and transactional replication) read transactionally consistent data by reading the transaction logs.</span></span> <span data-ttu-id="a4bc3-187">此时，它们读取作为事务的一部分更新的任意 FILESTREAM 数据。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-187">At this time, they read any FILESTREAM data updated as part of a transaction.</span></span> <span data-ttu-id="a4bc3-188">未在数据库级别启用非事务性访问时，这些工具和操作在确保完全事务一致性下工作。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-188">When non-transactional access is not enabled at the database level, these tools and operations work with full transactional consistency.</span></span>  
  
 <span data-ttu-id="a4bc3-189">但是，启用完全非事务性访问时，FileTable 可以包含比工具或进程从事务日志读取的事务更新（通过非事务性更新）更晚的数据。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-189">However, when full non-transactional access is enabled, then a FileTable could contain data that was updated more recently (through a non-transactional update) than the transaction that the tool or process is reading from the transaction log.</span></span> <span data-ttu-id="a4bc3-190">这意味着对特定事务进行的“时间点”还原操作包含的 FILESTREAM 数据可能比该事务更新。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-190">This means that a "point in time" restore operation to a specific transaction may contain FILESTREAM data that is more recent than that transaction.</span></span> <span data-ttu-id="a4bc3-191">在 FileTable 上允许非事务性更新时，这是预期的行为。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-191">This is the expected behavior when non-transactional updates are allowed on FileTables.</span></span>  
  
##  <a name="sql-server-profiler-and-filetables"></a><a name="Monitor"></a> <span data-ttu-id="a4bc3-192">SQL Server Profiler 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="a4bc3-192">SQL Server Profiler and FileTables</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a4bc3-193">Profiler 可为存储在 FileTable 中的文件捕获跟踪输出中的 Windows 文件打开和文件关闭操作。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-193">Profiler can capture the Windows File Open and File Close operations in trace output for files that are stored in a FileTable.</span></span>  
  
##  <a name="auditing-and-filetables"></a><a name="OtherAuditing"></a> <span data-ttu-id="a4bc3-194">审核和 FileTable</span><span class="sxs-lookup"><span data-stu-id="a4bc3-194">Auditing and FileTables</span></span>  
 <span data-ttu-id="a4bc3-195">可以像对任何其他表一样对 FileTable 进行审核。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-195">FileTable can be audited just like any other table.</span></span> <span data-ttu-id="a4bc3-196">但是，Win32 访问模式不是基于集的操作。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-196">Howerver, Win32 access patterns are not set based operations.</span></span> <span data-ttu-id="a4bc3-197">将文件系统中的单个操作转换为多个 Transact-SQL DML 操作。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-197">A single action in the file system translates into multiple Transact-SQL DML operations.</span></span> <span data-ttu-id="a4bc3-198">例如，在 Microsoft Word 中打开文件将转换为多个打开/关闭/创建/重命名/删除操作和相应的 Transact-SQL DML 活动。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-198">For example, opening a file in Microsoft Word translates into multiple open/close/create/rename/delete operations and corresponding Transact-SQL DML activities.</span></span> <span data-ttu-id="a4bc3-199">这将导致冗长的审核记录，很难将文件系统操作和相应的 Transact-SQL DML 审核记录关联。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-199">This results in verbose audit records where it is hard to correlate records between file system actions and corresponding Transact-SQL DML audit records.</span></span>  
  
##  <a name="dbcc-and-filetables"></a><a name="OtherDBCC"></a> <span data-ttu-id="a4bc3-200">DBCC 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="a4bc3-200">DBCC and FileTables</span></span>  
 <span data-ttu-id="a4bc3-201">可以使用 DBCC CHECKCONSTRAINTS 验证 FileTable 上的约束，包括系统定义的约束。</span><span class="sxs-lookup"><span data-stu-id="a4bc3-201">You can use DBCC CHECKCONSTRAINTS to validate the constraints on a FileTable including system-defined constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4bc3-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4bc3-202">See Also</span></span>  
 <span data-ttu-id="a4bc3-203">[FileTable 与其他 SQL Server 功能的兼容性](filetable-compatibility-with-other-sql-server-features.md) </span><span class="sxs-lookup"><span data-stu-id="a4bc3-203">[FileTable Compatibility with Other SQL Server Features](filetable-compatibility-with-other-sql-server-features.md) </span></span>  
 [<span data-ttu-id="a4bc3-204">FileTable DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="a4bc3-204">FileTable DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
  
  
