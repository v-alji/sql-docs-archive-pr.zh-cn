---
title: 收缩文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkfile.f1
helpviewer_keywords:
- shrinking files
- decreasing file size
- databases [SQL Server], shrinking
- reducing file size
- size [SQL Server], files
- file size [SQL Server]
ms.assetid: ce5c8798-c039-4ab2-81e7-90a8d688b893
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac69e4bd2db3ef7fe0815d235dd1de7d3396b302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682874"
---
# <a name="shrink-a-file"></a><span data-ttu-id="de89d-102">收缩文件</span><span class="sxs-lookup"><span data-stu-id="de89d-102">Shrink a File</span></span>
  <span data-ttu-id="de89d-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中收缩数据或日志文件。</span><span class="sxs-lookup"><span data-stu-id="de89d-103">This topic describes how to shrink a data or log file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="de89d-104">收缩数据文件通过将数据页从文件末尾移动到更靠近文件开头的未占用的空间来恢复空间。</span><span class="sxs-lookup"><span data-stu-id="de89d-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="de89d-105">在文件末尾创建足够的可用空间后，可以取消对文件末尾的数据页的分配并将它们返回给文件系统。</span><span class="sxs-lookup"><span data-stu-id="de89d-105">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
 <span data-ttu-id="de89d-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="de89d-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="de89d-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="de89d-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="de89d-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="de89d-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="de89d-109">建议</span><span class="sxs-lookup"><span data-stu-id="de89d-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="de89d-110">安全性</span><span class="sxs-lookup"><span data-stu-id="de89d-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="de89d-111">**若要收缩数据或日志文件，请使用：**</span><span class="sxs-lookup"><span data-stu-id="de89d-111">**To shrink a data or log file, using:**</span></span>  
  
     [<span data-ttu-id="de89d-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="de89d-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="de89d-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="de89d-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="de89d-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="de89d-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="de89d-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="de89d-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="de89d-116">主数据文件不能收缩到小于 model 数据库中的主文件的大小。</span><span class="sxs-lookup"><span data-stu-id="de89d-116">The primary data file cannot be made smaller than the size of the primary file in the model database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="de89d-117">建议</span><span class="sxs-lookup"><span data-stu-id="de89d-117">Recommendations</span></span>  
  
-   <span data-ttu-id="de89d-118">被移动用来收缩文件的数据可以分布到文件的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="de89d-118">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="de89d-119">这将导致索引碎片并使搜索索引范围的查询变慢。</span><span class="sxs-lookup"><span data-stu-id="de89d-119">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="de89d-120">若要消除碎片，请考虑在收缩后重新生成文件的索引。</span><span class="sxs-lookup"><span data-stu-id="de89d-120">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="de89d-121">Security</span><span class="sxs-lookup"><span data-stu-id="de89d-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="de89d-122">权限</span><span class="sxs-lookup"><span data-stu-id="de89d-122">Permissions</span></span>  
 <span data-ttu-id="de89d-123">要求具有 **sysadmin** 固定服务器角色或 **db_owner** 固定数据库角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="de89d-123">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="de89d-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="de89d-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="de89d-125">收缩数据或日志文件</span><span class="sxs-lookup"><span data-stu-id="de89d-125">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="de89d-126">在对象资源管理器中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="de89d-126">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="de89d-127">展开 **“数据库”** ，再右键单击要收缩的数据库。</span><span class="sxs-lookup"><span data-stu-id="de89d-127">Expand **Databases** and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="de89d-128">依次指向 **“任务”** 和 **“收缩”** ，再单击 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="de89d-128">Point to **Tasks**, point to **Shrink**, and then click **Files**.</span></span>  
  
     <span data-ttu-id="de89d-129">**Database**</span><span class="sxs-lookup"><span data-stu-id="de89d-129">**Database**</span></span>  
     <span data-ttu-id="de89d-130">显示所选数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="de89d-130">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="de89d-131">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="de89d-131">**File type**</span></span>  
     <span data-ttu-id="de89d-132">选择文件的文件类型。</span><span class="sxs-lookup"><span data-stu-id="de89d-132">Select the file type for the file.</span></span> <span data-ttu-id="de89d-133">可用的选项包括 **“数据”** 和 **“日志”** 文件。</span><span class="sxs-lookup"><span data-stu-id="de89d-133">The available choices are **Data** and **Log** files.</span></span> <span data-ttu-id="de89d-134">默认选项为 **“数据”** 。</span><span class="sxs-lookup"><span data-stu-id="de89d-134">The default selection is **Data**.</span></span> <span data-ttu-id="de89d-135">选择不同的文件组类型，其他字段中的选项会相应地发生更改。</span><span class="sxs-lookup"><span data-stu-id="de89d-135">Selecting a different filegroup type changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="de89d-136">**文件组**</span><span class="sxs-lookup"><span data-stu-id="de89d-136">**Filegroup**</span></span>  
     <span data-ttu-id="de89d-137">在与以上所选的 **“文件类型”** 相关联的文件组列表中选择文件组。</span><span class="sxs-lookup"><span data-stu-id="de89d-137">Select a filegroup from the list of Filegroups associated with the selected **File type** above.</span></span> <span data-ttu-id="de89d-138">选择不同的文件组，其他字段中的选项会相应地发生更改。</span><span class="sxs-lookup"><span data-stu-id="de89d-138">Selecting a different filegroup changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="de89d-139">**文件名**</span><span class="sxs-lookup"><span data-stu-id="de89d-139">**File name**</span></span>  
     <span data-ttu-id="de89d-140">从所选文件组和文件类型的可用文件列表中选择文件。</span><span class="sxs-lookup"><span data-stu-id="de89d-140">Select a file from the list of available files of the selected filegroup and file type.</span></span>  
  
     <span data-ttu-id="de89d-141">**位置**</span><span class="sxs-lookup"><span data-stu-id="de89d-141">**Location**</span></span>  
     <span data-ttu-id="de89d-142">显示当前所选文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="de89d-142">Displays the full path to the currently selected file.</span></span> <span data-ttu-id="de89d-143">此路径无法编辑，但是可以复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="de89d-143">The path is not editable, but it can be copied to the clipboard.</span></span>  
  
     <span data-ttu-id="de89d-144">**当前分配的空间**</span><span class="sxs-lookup"><span data-stu-id="de89d-144">**Currently allocated space**</span></span>  
     <span data-ttu-id="de89d-145">对于数据文件，会显示当前分配的空间。</span><span class="sxs-lookup"><span data-stu-id="de89d-145">For data files, displays the current allocated space.</span></span> <span data-ttu-id="de89d-146">对于日志文件，会显示根据 DBCC SQLPERF (LOGSPACE) 的输出计算出的当前分配的空间。</span><span class="sxs-lookup"><span data-stu-id="de89d-146">For log files, displays the current allocated space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="de89d-147">**可用空间**</span><span class="sxs-lookup"><span data-stu-id="de89d-147">**Available free space**</span></span>  
     <span data-ttu-id="de89d-148">对于数据文件，会显示根据 SHOWFILESTATS (fileid) 的输出计算出的当前可用空间。</span><span class="sxs-lookup"><span data-stu-id="de89d-148">For data files, displays the current available free space computed from the output of DBCC SHOWFILESTATS(fileid).</span></span> <span data-ttu-id="de89d-149">对于日志文件，会显示根据 DBCC SQLPERF (LOGSPACE) 的输出计算出的当前可用空间。</span><span class="sxs-lookup"><span data-stu-id="de89d-149">For log files, displays the current available free space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="de89d-150">**释放未使用的空间**</span><span class="sxs-lookup"><span data-stu-id="de89d-150">**Release unused space**</span></span>  
     <span data-ttu-id="de89d-151">将任何文件中未使用的空间释放给操作系统，并将文件收缩到最后分配的区，因此无需移动任何数据即可减小文件尺寸。</span><span class="sxs-lookup"><span data-stu-id="de89d-151">Cause any unused space in the files to be released to the operating system and shrink the file to the last allocated extent, reducing the file size without moving any data.</span></span> <span data-ttu-id="de89d-152">不会将行重新定位到未分配的页。</span><span class="sxs-lookup"><span data-stu-id="de89d-152">No attempt is made to relocate rows to unallocated pages.</span></span>  
  
     <span data-ttu-id="de89d-153">**在释放未使用的空间前重新组织页**</span><span class="sxs-lookup"><span data-stu-id="de89d-153">**Reorganize pages before releasing unused space**</span></span>  
     <span data-ttu-id="de89d-154">等效于执行用于指定目标文件大小的 DBCC SHRINKFILE。</span><span class="sxs-lookup"><span data-stu-id="de89d-154">Equivalent to executing DBCC SHRINKFILE specifying the target file size.</span></span> <span data-ttu-id="de89d-155">选中此选项时，用户必须在 **“将文件收缩到”** 框中指定目标文件的大小。</span><span class="sxs-lookup"><span data-stu-id="de89d-155">When this option is selected, the user must specify a target file size in the **Shrink file to** box.</span></span>  
  
     <span data-ttu-id="de89d-156">**“将文件收缩到”**</span><span class="sxs-lookup"><span data-stu-id="de89d-156">**Shrink file to**</span></span>  
     <span data-ttu-id="de89d-157">为收缩操作指定目标文件的大小。</span><span class="sxs-lookup"><span data-stu-id="de89d-157">Specifies the target file size for the shrink operation.</span></span> <span data-ttu-id="de89d-158">此大小值不得小于当前分配的空间或大于为文件分配的全部区的大小。</span><span class="sxs-lookup"><span data-stu-id="de89d-158">The size cannot be less than the current allocated space or more than the total extents allocated to the file.</span></span> <span data-ttu-id="de89d-159">如果输入的值超出最小值或最大值，那么一旦焦点改变或单击工具栏上的按钮时，数值将恢复到最小值或最大值。</span><span class="sxs-lookup"><span data-stu-id="de89d-159">Entering a value beyond the minimum or the maximum will revert to the min or the max once the focus is changed or when any of the buttons on the toolbar are clicked.</span></span>  
  
     <span data-ttu-id="de89d-160">**通过将数据迁移到同一文件组中的其他文件来清空文件**</span><span class="sxs-lookup"><span data-stu-id="de89d-160">**Empty file by migrating the data to other files in the same filegroup**</span></span>  
     <span data-ttu-id="de89d-161">从指定文件迁移所有数据。</span><span class="sxs-lookup"><span data-stu-id="de89d-161">Migrate all data from the specified file.</span></span> <span data-ttu-id="de89d-162">此选项允许使用 ALTER DATABASE 语句删除文件。</span><span class="sxs-lookup"><span data-stu-id="de89d-162">This option allows the file to be dropped using the ALTER DATABASE statement.</span></span> <span data-ttu-id="de89d-163">此选项等效于执行带有 EMPTYFILE 选项的 DBCC SHRINKFILE。</span><span class="sxs-lookup"><span data-stu-id="de89d-163">This option is equivalent to executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
4.  <span data-ttu-id="de89d-164">选择文件类型和文件名。</span><span class="sxs-lookup"><span data-stu-id="de89d-164">Select the file type and file name.</span></span>  
  
5.  <span data-ttu-id="de89d-165">根据需要，选中 **“释放未使用的空间”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="de89d-165">Optionally, select the **Release unused space** check box.</span></span>  
  
     <span data-ttu-id="de89d-166">选中此选项后，将为操作系统释放文件中所有未使用的空间，并将文件收缩到上次分配的区。</span><span class="sxs-lookup"><span data-stu-id="de89d-166">Selecting this option causes any unused space in the file to be released to the operating system and shrinks the file to the last allocated extent.</span></span> <span data-ttu-id="de89d-167">这将减小文件的大小，但不移动任何数据。</span><span class="sxs-lookup"><span data-stu-id="de89d-167">This reduces the file size without moving any data.</span></span>  
  
6.  <span data-ttu-id="de89d-168">根据需要，可以选中 **“在释放未使用的空间前重新组织文件”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="de89d-168">Optionally, select the **Reorganize files before releasing unused space** check box.</span></span> <span data-ttu-id="de89d-169">如果选中此选项，则必须指定 **“将文件收缩到”** 值。</span><span class="sxs-lookup"><span data-stu-id="de89d-169">If this is selected, the **Shrink file to** value must be specified.</span></span> <span data-ttu-id="de89d-170">默认情况下，该选项为清除状态。</span><span class="sxs-lookup"><span data-stu-id="de89d-170">By default, the option is cleared.</span></span>  
  
     <span data-ttu-id="de89d-171">选中此选项后，将为操作系统释放文件中所有未使用的空间，并尝试将行重新定位到未分配页。</span><span class="sxs-lookup"><span data-stu-id="de89d-171">Selecting this option causes any unused space in the file to be released to the operating system and tries to relocate rows to unallocated pages.</span></span>  
  
7.  <span data-ttu-id="de89d-172">根据需要，输入在收缩数据库后数据库文件中要保留的最大可用空间百分比。</span><span class="sxs-lookup"><span data-stu-id="de89d-172">Optionally, enter the maximum percentage of free space to be left in the database file after the database has been shrunk.</span></span> <span data-ttu-id="de89d-173">值可以介于 0 和 99 之间。</span><span class="sxs-lookup"><span data-stu-id="de89d-173">Permissible values are between 0 and 99.</span></span> <span data-ttu-id="de89d-174">只有启用 **“在释放未使用的空间前重新组织文件”** 以后，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="de89d-174">This option is only available when **Reorganize files before releasing unused space** is enabled.</span></span>  
  
8.  <span data-ttu-id="de89d-175">根据需要，选中 **“通过将数据迁移到同一文件组中的其他文件来清空文件”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="de89d-175">Optionally, select the **Empty file by migrating the data to other files in the same filegroup** check box.</span></span>  
  
     <span data-ttu-id="de89d-176">选中此选项后，将指定文件中的所有数据移至同一文件组中的其他文件中。</span><span class="sxs-lookup"><span data-stu-id="de89d-176">Selecting this option moves all data from the specified file to other files in the filegroup.</span></span> <span data-ttu-id="de89d-177">然后就可以删除空文件。</span><span class="sxs-lookup"><span data-stu-id="de89d-177">The empty file can then be deleted.</span></span> <span data-ttu-id="de89d-178">此选项与执行包含 EMPTYFILE 选项 DBCC SHRINKFILE 相同。</span><span class="sxs-lookup"><span data-stu-id="de89d-178">This option is the same as executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
9. <span data-ttu-id="de89d-179">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="de89d-179">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="de89d-180">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="de89d-180">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="de89d-181">收缩数据或日志文件</span><span class="sxs-lookup"><span data-stu-id="de89d-181">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="de89d-182">连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="de89d-182">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="de89d-183">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="de89d-183">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="de89d-184">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="de89d-184">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="de89d-185">此示例使用 [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) 将 `UserDB` 数据库中名为 `DataFile1` 的数据文件的大小收缩到 7 MB。</span><span class="sxs-lookup"><span data-stu-id="de89d-185">This example uses [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) to shrink the size of a data file named `DataFile1` in the `UserDB` database to 7 MB.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKFILE1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkfile1)]  
  
## <a name="see-also"></a><span data-ttu-id="de89d-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de89d-186">See Also</span></span>  
 <span data-ttu-id="de89d-187">[DBCC SHRINKDATABASE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de89d-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span></span>  
 <span data-ttu-id="de89d-188">[收缩数据库](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="de89d-188">[Shrink a Database](shrink-a-database.md) </span></span>  
 <span data-ttu-id="de89d-189">[删除数据库中的数据文件或日志文件](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="de89d-189">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 <span data-ttu-id="de89d-190">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de89d-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="de89d-191">sys.database_files (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="de89d-191">sys.database_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)  
  
  
