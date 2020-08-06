---
title: 收缩数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246036bfea6dc8431f878165330f7f0571949897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682875"
---
# <a name="shrink-a-database"></a><span data-ttu-id="dd95e-102">收缩数据库</span><span class="sxs-lookup"><span data-stu-id="dd95e-102">Shrink a Database</span></span>
  <span data-ttu-id="dd95e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中使用对象收缩数据库。</span><span class="sxs-lookup"><span data-stu-id="dd95e-103">This topic describes how to shrink a database by using Object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dd95e-104">收缩数据文件通过将数据页从文件末尾移动到更靠近文件开头的未占用的空间来恢复空间。</span><span class="sxs-lookup"><span data-stu-id="dd95e-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="dd95e-105">在文件末尾创建足够的可用空间后，可以取消对文件末尾的数据页的分配并将它们返回给文件系统。</span><span class="sxs-lookup"><span data-stu-id="dd95e-105">When enough free space is created at the end of the file, data pages at end of the file can be deallocated and returned to the file system.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dd95e-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="dd95e-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dd95e-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="dd95e-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="dd95e-108">收缩后的数据库不能小于数据库的最小大小。</span><span class="sxs-lookup"><span data-stu-id="dd95e-108">The database cannot be made smaller than the minimum size of the database.</span></span> <span data-ttu-id="dd95e-109">最小大小是在数据库最初创建时指定的大小，或是上一次使用文件大小更改操作（如 DBCC SHRINKFILE）设置的显式大小。</span><span class="sxs-lookup"><span data-stu-id="dd95e-109">The minimum size is the size specified when the database was originally created, or the last explicit size set by using a file-size-changing operation, such as DBCC SHRINKFILE.</span></span> <span data-ttu-id="dd95e-110">例如，如果数据库最初创建时的大小为 10 MB，后来增长到 100 MB，则该数据库最小只能收缩到 10 MB，即使已经删除数据库的所有数据也是如此。</span><span class="sxs-lookup"><span data-stu-id="dd95e-110">For example, if a database was originally created with a size of 10 MB and grew to 100 MB, the smallest size the database could be reduced to is 10 MB, even if all the data in the database has been deleted.</span></span>  
  
-   <span data-ttu-id="dd95e-111">不能在备份数据库时收缩数据库。</span><span class="sxs-lookup"><span data-stu-id="dd95e-111">You cannot shrink a database while the database is being backed up.</span></span> <span data-ttu-id="dd95e-112">反之，也不能在数据库执行收缩操作时备份数据库。</span><span class="sxs-lookup"><span data-stu-id="dd95e-112">Conversely, you cannot backup a database while a shrink operation on the database is in process.</span></span>  
  
-   <span data-ttu-id="dd95e-113">遇到 xVelocity 内存优化的列存储索引时，DBCC SHRINKDATABASE 将会失败。</span><span class="sxs-lookup"><span data-stu-id="dd95e-113">DBCC SHRINKDATABASE will fail when it encounters an xVelocity memory optimized columnstore index.</span></span> <span data-ttu-id="dd95e-114">遇到 columnstore 索引之前完成的工作将会成功，因此数据库可能会较小。</span><span class="sxs-lookup"><span data-stu-id="dd95e-114">Work completed before encountering the columnstore index will succeed so the database might be smaller.</span></span> <span data-ttu-id="dd95e-115">若要完成 DBCC SHRINKDATABASE，请在执行 DBCC SHRINKDATABASE 前禁用所有列存储索引，然后重新生成列存储索引。</span><span class="sxs-lookup"><span data-stu-id="dd95e-115">To complete DBCC SHRINKDATABASE, disable all columnstore indexes before executing DBCC SHRINKDATABASE, and then rebuild the columnstore indexes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="dd95e-116">建议</span><span class="sxs-lookup"><span data-stu-id="dd95e-116">Recommendations</span></span>  
  
-   <span data-ttu-id="dd95e-117">若要查看数据库中当前的可用（未分配）空间量。</span><span class="sxs-lookup"><span data-stu-id="dd95e-117">To view the current amount of free (unallocated) space in the database.</span></span> <span data-ttu-id="dd95e-118">有关详细信息，请参阅 [显示数据库的数据和日志空间信息](display-data-and-log-space-information-for-a-database.md)</span><span class="sxs-lookup"><span data-stu-id="dd95e-118">For more information, see [Display Data and Log Space Information for a Database](display-data-and-log-space-information-for-a-database.md)</span></span>  
  
-   <span data-ttu-id="dd95e-119">当您计划收缩数据库时，请考虑以下信息：</span><span class="sxs-lookup"><span data-stu-id="dd95e-119">Consider the following information when you plan to shrink a database:</span></span>  
  
    -   <span data-ttu-id="dd95e-120">在执行会产生许多未使用空间的操作（如截断表或删除表操作）后，执行收缩操作最有效。</span><span class="sxs-lookup"><span data-stu-id="dd95e-120">A shrink operation is most effective after an operation that creates lots of unused space, such as a truncate table or a drop table operation.</span></span>  
  
    -   <span data-ttu-id="dd95e-121">大多数数据库都需要一些可用空间，以供常规日常操作使用。</span><span class="sxs-lookup"><span data-stu-id="dd95e-121">Most databases require some free space to be available for regular day-to-day operations.</span></span> <span data-ttu-id="dd95e-122">如果反复收缩数据库并注意到数据库大小变大，则表明收缩的空间是常规操作所必需的。</span><span class="sxs-lookup"><span data-stu-id="dd95e-122">If you shrink a database repeatedly and notice that the database size grows again, this indicates that the space that was shrunk is required for regular operations.</span></span> <span data-ttu-id="dd95e-123">在这种情况下，反复收缩数据库是一种无谓的操作。</span><span class="sxs-lookup"><span data-stu-id="dd95e-123">In these cases, repeatedly shrinking the database is a wasted operation.</span></span>  
  
    -   <span data-ttu-id="dd95e-124">收缩操作不会保留数据库中索引的碎片状态，通常还会在一定程度上增加碎片。</span><span class="sxs-lookup"><span data-stu-id="dd95e-124">A shrink operation does not preserve the fragmentation state of indexes in the database, and generally increases fragmentation to a degree.</span></span> <span data-ttu-id="dd95e-125">这是不要反复收缩数据库的另一个原因。</span><span class="sxs-lookup"><span data-stu-id="dd95e-125">This is another reason not to repeatedly shrink the database.</span></span>  
  
    -   <span data-ttu-id="dd95e-126">除非有特定要求，否则不要将 AUTO_SHRINK 数据库选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="dd95e-126">Unless you have a specific requirement, do not set the AUTO_SHRINK database option to ON.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dd95e-127">Security</span><span class="sxs-lookup"><span data-stu-id="dd95e-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dd95e-128">权限</span><span class="sxs-lookup"><span data-stu-id="dd95e-128">Permissions</span></span>  
 <span data-ttu-id="dd95e-129">要求具有 **sysadmin** 固定服务器角色或 **db_owner** 固定数据库角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="dd95e-129">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dd95e-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dd95e-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="dd95e-131">收缩数据库</span><span class="sxs-lookup"><span data-stu-id="dd95e-131">To shrink a database</span></span>  
  
1.  <span data-ttu-id="dd95e-132">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="dd95e-132">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="dd95e-133">展开“数据库”，再右键单击要收缩的数据库。</span><span class="sxs-lookup"><span data-stu-id="dd95e-133">Expand **Databases**, and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="dd95e-134">指向 **“任务”** ，指向 **“收缩”** ，然后单击 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="dd95e-134">Point to **Tasks**, point to **Shrink**, and then click **Database**.</span></span>  
  
     <span data-ttu-id="dd95e-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="dd95e-135">**Database**</span></span>  
     <span data-ttu-id="dd95e-136">显示所选数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="dd95e-136">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="dd95e-137">**当前分配的空间**</span><span class="sxs-lookup"><span data-stu-id="dd95e-137">**Current allocated space**</span></span>  
     <span data-ttu-id="dd95e-138">显示所选数据库的总已用空间和未使用空间。</span><span class="sxs-lookup"><span data-stu-id="dd95e-138">Displays the total used and unused space for the selected database.</span></span>  
  
     <span data-ttu-id="dd95e-139">**可用空间**</span><span class="sxs-lookup"><span data-stu-id="dd95e-139">**Available free space**</span></span>  
     <span data-ttu-id="dd95e-140">显示所选数据库的日志和数据文件中可用空间的总和。</span><span class="sxs-lookup"><span data-stu-id="dd95e-140">Displays the sum of free space in the log and data files of the selected database.</span></span>  
  
     <span data-ttu-id="dd95e-141">**在释放未使用的空间前重新组织文件**</span><span class="sxs-lookup"><span data-stu-id="dd95e-141">**Reorganize files before releasing unused space**</span></span>  
     <span data-ttu-id="dd95e-142">选择此选项等效于执行指定了目标百分比选项的 DBCC SHRINKDATABASE。</span><span class="sxs-lookup"><span data-stu-id="dd95e-142">Selecting this option is equivalent to executing DBCC SHRINKDATABASE specifying a target percent option.</span></span> <span data-ttu-id="dd95e-143">清除此选项等效于执行带 TRUNCATEONLY 选项的 DBCC SHRINKDATABASE。</span><span class="sxs-lookup"><span data-stu-id="dd95e-143">Clearing this option is equivalent to executing DBCC SHRINKDATABASE with TRUNCATEONLY option.</span></span> <span data-ttu-id="dd95e-144">在打开对话框时，默认情况下不选择此选项。</span><span class="sxs-lookup"><span data-stu-id="dd95e-144">By default, this option is not selected when the dialog is opened.</span></span> <span data-ttu-id="dd95e-145">如果选择此选项，用户必须指定目标百分比选项。</span><span class="sxs-lookup"><span data-stu-id="dd95e-145">If this option is selected, the user must specify a target percent option.</span></span>  
  
     <span data-ttu-id="dd95e-146">**收缩后文件中的最大可用空间**</span><span class="sxs-lookup"><span data-stu-id="dd95e-146">**Maximum free space in files after shrinking**</span></span>  
     <span data-ttu-id="dd95e-147">输入在数据库收缩后数据库文件中剩余可用空间的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="dd95e-147">Enter the maximum percentage of free space to be left in the database files after the database has been shrunk.</span></span> <span data-ttu-id="dd95e-148">值可以介于 0 和 99 之间。</span><span class="sxs-lookup"><span data-stu-id="dd95e-148">Permissible values are between 0 and 99.</span></span>  
  
4.  <span data-ttu-id="dd95e-149">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="dd95e-149">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dd95e-150">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dd95e-150">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="dd95e-151">收缩数据库</span><span class="sxs-lookup"><span data-stu-id="dd95e-151">To shrink a database</span></span>  
  
1.  <span data-ttu-id="dd95e-152">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd95e-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dd95e-153">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="dd95e-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dd95e-154">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="dd95e-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="dd95e-155">此实例使用 [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) 减少 `UserDB` 数据库中数据文件和日志文件的大小并允许数据库中有 `10` ％ 的可用空间。</span><span class="sxs-lookup"><span data-stu-id="dd95e-155">This example uses [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) to decreases the size of the data and log files in the `UserDB` database and to allow for `10` percent free space in the database.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="follow-up-after-you-shrink-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="dd95e-156">跟进：在收缩数据库之后</span><span class="sxs-lookup"><span data-stu-id="dd95e-156">Follow Up: After you shrink a database</span></span>  
 <span data-ttu-id="dd95e-157">被移动用来收缩文件的数据可以分布到文件的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="dd95e-157">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="dd95e-158">这将导致索引碎片并使搜索索引范围的查询变慢。</span><span class="sxs-lookup"><span data-stu-id="dd95e-158">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="dd95e-159">若要消除碎片，请考虑在收缩后重新生成文件的索引。</span><span class="sxs-lookup"><span data-stu-id="dd95e-159">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd95e-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd95e-160">See Also</span></span>  
 <span data-ttu-id="dd95e-161">[收缩文件](shrink-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="dd95e-161">[Shrink a File](shrink-a-file.md) </span></span>  
 <span data-ttu-id="dd95e-162">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd95e-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="dd95e-163">[sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd95e-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="dd95e-164">[DBCC (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd95e-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="dd95e-165">[DBCC SHRINKFILE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dd95e-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span></span>  
 [<span data-ttu-id="dd95e-166">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="dd95e-166">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
