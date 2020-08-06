---
title: 表属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.tableproperties.storage.f1
- sql12.SWB.SELECTCOLUMNS.F1
- sql12.swb.tableproperties.filetable.f1
- sql12.swb.tableproperties.general.f1
- sql12.swb.tableproperties.changetracking.f1
ms.assetid: ad8a2fd4-f092-4c0f-be85-54ce8b9d725a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 037e56649d3473e3fe09b9533bcc96b4729870d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587266"
---
# <a name="table-properties"></a><span data-ttu-id="dab03-102">表属性</span><span class="sxs-lookup"><span data-stu-id="dab03-102">Table Properties</span></span>
  <span data-ttu-id="dab03-103">本主题介绍在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“表属性”对话框中显示的表属性。</span><span class="sxs-lookup"><span data-stu-id="dab03-103">This topic describes the table properties that are displayed in the Table Properties dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="dab03-104">有关如何显示这些属性的详细信息，请参阅 [查看表定义](view-the-table-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="dab03-104">For more information about how to display these properties, see [View the Table Definition](view-the-table-definition.md).</span></span>  
  
 <span data-ttu-id="dab03-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="dab03-105">**In This Topic**</span></span>  
  
1.  [<span data-ttu-id="dab03-106">“常规”页</span><span class="sxs-lookup"><span data-stu-id="dab03-106">General Page</span></span>](#GeneralPage)  
  
2.  [<span data-ttu-id="dab03-107">“更改跟踪”页</span><span class="sxs-lookup"><span data-stu-id="dab03-107">Change Tracking Page</span></span>](#ChangeTracking)  
  
3.  [<span data-ttu-id="dab03-108">“文件表”页</span><span class="sxs-lookup"><span data-stu-id="dab03-108">File Table Page</span></span>](#FileTable)  
  
4.  [<span data-ttu-id="dab03-109">“存储”页</span><span class="sxs-lookup"><span data-stu-id="dab03-109">Storage Page</span></span>](#Storage)  
  
##  <a name="general-page"></a><a name="GeneralPage"></a> <span data-ttu-id="dab03-110">“常规”页</span><span class="sxs-lookup"><span data-stu-id="dab03-110">General Page</span></span>  
 <span data-ttu-id="dab03-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="dab03-111">**Database**</span></span>  
 <span data-ttu-id="dab03-112">包含此表的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-112">The name of the database containing this table.</span></span>  
  
 <span data-ttu-id="dab03-113">**Server**</span><span class="sxs-lookup"><span data-stu-id="dab03-113">**Server**</span></span>  
 <span data-ttu-id="dab03-114">当前服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-114">The name of the current server instance.</span></span>  
  
 <span data-ttu-id="dab03-115">**用户**</span><span class="sxs-lookup"><span data-stu-id="dab03-115">**User**</span></span>  
 <span data-ttu-id="dab03-116">此连接的用户名。</span><span class="sxs-lookup"><span data-stu-id="dab03-116">The name of the user of this connection.</span></span>  
  
 <span data-ttu-id="dab03-117">**创建日期**</span><span class="sxs-lookup"><span data-stu-id="dab03-117">**Created Date**</span></span>  
 <span data-ttu-id="dab03-118">该表的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="dab03-118">The date and time that the table was created.</span></span>  
  
 <span data-ttu-id="dab03-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="dab03-119">**Name**</span></span>  
 <span data-ttu-id="dab03-120">表的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-120">The name of the table.</span></span>  
  
 <span data-ttu-id="dab03-121">**架构**</span><span class="sxs-lookup"><span data-stu-id="dab03-121">**Schema**</span></span>  
 <span data-ttu-id="dab03-122">该表所属的架构。</span><span class="sxs-lookup"><span data-stu-id="dab03-122">The schema that owns the table.</span></span>  
  
 <span data-ttu-id="dab03-123">**系统对象**</span><span class="sxs-lookup"><span data-stu-id="dab03-123">**System object**</span></span>  
 <span data-ttu-id="dab03-124">指示此表为系统表， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用此表来保存内部信息。</span><span class="sxs-lookup"><span data-stu-id="dab03-124">Indicates this table is a system table, used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to contain internal information.</span></span> <span data-ttu-id="dab03-125">用户不要直接更改或引用系统表。</span><span class="sxs-lookup"><span data-stu-id="dab03-125">Users should not directly change or reference system tables.</span></span>  
  
 <span data-ttu-id="dab03-126">**ANSI NULLs**</span><span class="sxs-lookup"><span data-stu-id="dab03-126">**ANSI NULLs**</span></span>  
 <span data-ttu-id="dab03-127">指示在创建对象时 ANSI NULL 选项是否设为 ON。</span><span class="sxs-lookup"><span data-stu-id="dab03-127">Indicates if the object was created with the ANSI NULLs option set to ON.</span></span> <span data-ttu-id="dab03-128">有关详细信息，请参阅 [SET ANSI_NULLS (Transact SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="dab03-128">For more information, see [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)</span></span>  
  
 <span data-ttu-id="dab03-129">**带引号的标识符**</span><span class="sxs-lookup"><span data-stu-id="dab03-129">**Quoted identifier**</span></span>  
 <span data-ttu-id="dab03-130">指示在创建对象时带引号的标识符选项是否设为 ON。</span><span class="sxs-lookup"><span data-stu-id="dab03-130">Indicates if the object was created with the quoted identifier option set to ON.</span></span> <span data-ttu-id="dab03-131">有关详细信息，请参阅 [SET QUOTED_IDENTIFIER (Transact SQL)](/sql/t-sql/statements/set-quoted-identifier-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="dab03-131">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)</span></span>  
  
 <span data-ttu-id="dab03-132">**锁升级**</span><span class="sxs-lookup"><span data-stu-id="dab03-132">**Lock Escalation**</span></span>  
 <span data-ttu-id="dab03-133">指示表的锁升级粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-133">Indicates the lock escalation granularity of the table.</span></span> <span data-ttu-id="dab03-134">有关数据库引擎中的锁定的详细信息，请参阅 [SQL Server 事务锁定和行版本控制指南](https://msdn.microsoft.com/library/jj856598.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dab03-134">For more information about locking in the Database Engine, see [SQL Server Transaction Locking and Row Versioning Guide](https://msdn.microsoft.com/library/jj856598.aspx).</span></span> <span data-ttu-id="dab03-135">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="dab03-135">Possible values are:</span></span>  
  
 <span data-ttu-id="dab03-136">AUTO</span><span class="sxs-lookup"><span data-stu-id="dab03-136">AUTO</span></span>  
 <span data-ttu-id="dab03-137">此选项可让 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 选择适合于表架构的锁升级粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-137">This option allows the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to select the lock escalation granularity that is appropriate for the table schema.</span></span>  
  
-   <span data-ttu-id="dab03-138">如果该表已分区，则允许锁升级到堆或 B 树 (HoBT) 粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-138">If the table is partitioned, lock escalation will be allowed to the heap or B-tree (HoBT) granularity.</span></span> <span data-ttu-id="dab03-139">锁升级到 HoBT 级别之后，该锁以后将不会升级到 TABLE 粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-139">After the lock is escalated to the HoBT level, the lock will not be escalated later to TABLE granularity.</span></span>  
  
-   <span data-ttu-id="dab03-140">如果该表未分区，则会将锁升级到 TABLE 粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-140">If the table is not partitioned, the lock escalation will be done to the TABLE granularity.</span></span>  
  
 <span data-ttu-id="dab03-141">TABLE</span><span class="sxs-lookup"><span data-stu-id="dab03-141">TABLE</span></span>  
 <span data-ttu-id="dab03-142">无论表是否已分区，都会将锁升级到表级粒度。</span><span class="sxs-lookup"><span data-stu-id="dab03-142">Lock escalation will be done at table-level granularity regardless of whether the table is partitioned or not partitioned.</span></span> <span data-ttu-id="dab03-143">默认值为 TABLE。</span><span class="sxs-lookup"><span data-stu-id="dab03-143">TABLE is the default value.</span></span>  
  
 <span data-ttu-id="dab03-144">DISABLE</span><span class="sxs-lookup"><span data-stu-id="dab03-144">DISABLE</span></span>  
 <span data-ttu-id="dab03-145">在大多数情况下禁止锁升级。</span><span class="sxs-lookup"><span data-stu-id="dab03-145">Prevents lock escalation in most cases.</span></span> <span data-ttu-id="dab03-146">表级别的锁未完全禁止。</span><span class="sxs-lookup"><span data-stu-id="dab03-146">Table-level locks are not completely disallowed.</span></span> <span data-ttu-id="dab03-147">例如，当扫描在可序列化隔离级别下没有聚集索引的表时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 必须使用表锁来保证数据的完整性。</span><span class="sxs-lookup"><span data-stu-id="dab03-147">For example, when you are scanning a table that has no clustered index under the serializable isolation level, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must take a table lock to protect data integrity.</span></span>  
  
 <span data-ttu-id="dab03-148">**对表进行复制**</span><span class="sxs-lookup"><span data-stu-id="dab03-148">**Table is replicated**</span></span>  
 <span data-ttu-id="dab03-149">指示是否使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制将表复制到其他数据库。</span><span class="sxs-lookup"><span data-stu-id="dab03-149">Indicates when the table is replicated to another database using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="dab03-150">可能的值为 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="dab03-150">Possible values are `True` or `False`.</span></span>  
  
##  <a name="change-tracking-page"></a><a name="ChangeTracking"></a><span data-ttu-id="dab03-151">更改跟踪页面</span><span class="sxs-lookup"><span data-stu-id="dab03-151">Change Tracking Page</span></span>  
 <span data-ttu-id="dab03-152">**更改跟踪**</span><span class="sxs-lookup"><span data-stu-id="dab03-152">**Change Tracking**</span></span>  
 <span data-ttu-id="dab03-153">指示是否对相应的表启用了更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="dab03-153">Indicates whether change tracking is enabled for the table.</span></span> <span data-ttu-id="dab03-154">默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="dab03-154">The default value is `False`.</span></span>  
  
 <span data-ttu-id="dab03-155">只有对数据库启用了更改跟踪，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="dab03-155">This option is available only when change tracking is enabled for the database.</span></span>  
  
 <span data-ttu-id="dab03-156">若要启用更改跟踪，相应的表必须具有一个主键，且您必须拥有修改该表的权限。</span><span class="sxs-lookup"><span data-stu-id="dab03-156">To enable change tracking, the table must have a primary key, and you must have permission to modify the table.</span></span> <span data-ttu-id="dab03-157">您可以使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)来配置更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="dab03-157">You can configure change tracking by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="dab03-158">**跟踪已更新的列**</span><span class="sxs-lookup"><span data-stu-id="dab03-158">**Track Columns Updated**</span></span>  
 <span data-ttu-id="dab03-159">指示 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 是否跟踪哪些列已更新。</span><span class="sxs-lookup"><span data-stu-id="dab03-159">Indicates whether the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tracks which columns were updated.</span></span>  
  
 <span data-ttu-id="dab03-160">有关更改跟踪的详细信息，请参阅[关于更改跟踪 (SQL Server)](../track-changes/about-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dab03-160">For more information about Change Tracking, see [About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).</span></span>  
  
##  <a name="filetable-page"></a><a name="FileTable"></a><span data-ttu-id="dab03-161">FileTable 页</span><span class="sxs-lookup"><span data-stu-id="dab03-161">FileTable Page</span></span>  
 <span data-ttu-id="dab03-162">显示与 FileTable 相关的表的属性。</span><span class="sxs-lookup"><span data-stu-id="dab03-162">Displays properties of the table related to FileTables.</span></span> <span data-ttu-id="dab03-163">有关详细信息，请参阅 [FileTables (SQL Server)](../blob/filetables-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dab03-163">For more information, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span>  
  
 <span data-ttu-id="dab03-164">**FileTable 名称列排序规则**</span><span class="sxs-lookup"><span data-stu-id="dab03-164">**FileTable name column collation**</span></span>  
 <span data-ttu-id="dab03-165">应用于 FileTable 的 **Name** 列的排序规则。</span><span class="sxs-lookup"><span data-stu-id="dab03-165">The collation that is applied to the **Name** column in a FileTable.</span></span> <span data-ttu-id="dab03-166">该 **Name** 列包含文件和目录名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-166">The **Name** column contains file and directory names.</span></span>  
  
 <span data-ttu-id="dab03-167">**FileTable 目录名称**</span><span class="sxs-lookup"><span data-stu-id="dab03-167">**FileTable directory name**</span></span>  
 <span data-ttu-id="dab03-168">FileTable 的根文件夹。</span><span class="sxs-lookup"><span data-stu-id="dab03-168">The root folder for the FileTable.</span></span>  
  
 <span data-ttu-id="dab03-169">**启用 FileTable 命名空间**</span><span class="sxs-lookup"><span data-stu-id="dab03-169">**FileTable namespace enabled**</span></span>  
 <span data-ttu-id="dab03-170">在为 `True` 时，该值指示该表为 FileTable。</span><span class="sxs-lookup"><span data-stu-id="dab03-170">When `True`, this value indicates that the table is a FileTable.</span></span> <span data-ttu-id="dab03-171">如果您将该值更改为 `False`，则是在将 FileTable 更改为普通用户表。</span><span class="sxs-lookup"><span data-stu-id="dab03-171">If you change this value to `False`, you are changing the FileTable to an ordinary user table.</span></span> <span data-ttu-id="dab03-172">如果您以后想要将该表更改回 FileTable，则该表将必须首先通过 FileTable 一致性检查，之后转换才会成功。</span><span class="sxs-lookup"><span data-stu-id="dab03-172">If you later want to change the table back to a FileTable, the table will have to pass a FileTable consistency check before the conversion succeeds.</span></span>  
  
##  <a name="storage-page"></a><a name="Storage"></a><span data-ttu-id="dab03-173">存储页</span><span class="sxs-lookup"><span data-stu-id="dab03-173">Storage Page</span></span>  
 <span data-ttu-id="dab03-174">显示所选表中与存储相关的属性。</span><span class="sxs-lookup"><span data-stu-id="dab03-174">Displays the storage related properties of the selected table.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="dab03-175">压缩</span><span class="sxs-lookup"><span data-stu-id="dab03-175">Compression</span></span>  
 <span data-ttu-id="dab03-176">**压缩类型**</span><span class="sxs-lookup"><span data-stu-id="dab03-176">**Compression type**</span></span>  
 <span data-ttu-id="dab03-177">表的压缩类型。</span><span class="sxs-lookup"><span data-stu-id="dab03-177">The compression type of the table.</span></span> <span data-ttu-id="dab03-178">此属性仅可用于未分区的表。</span><span class="sxs-lookup"><span data-stu-id="dab03-178">This property is only available for tables that are not partitioned.</span></span> <span data-ttu-id="dab03-179">有关详细信息，请参阅 [Data Compression](../data-compression/data-compression.md)。</span><span class="sxs-lookup"><span data-stu-id="dab03-179">For more information, see [Data Compression](../data-compression/data-compression.md).</span></span>  
  
 <span data-ttu-id="dab03-180">**使用页压缩的分区**</span><span class="sxs-lookup"><span data-stu-id="dab03-180">**Partitions using page compression**</span></span>  
 <span data-ttu-id="dab03-181">使用页压缩的分区号。</span><span class="sxs-lookup"><span data-stu-id="dab03-181">The partition numbers that are using page compression.</span></span> <span data-ttu-id="dab03-182">此属性仅可用于已分区表。</span><span class="sxs-lookup"><span data-stu-id="dab03-182">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="dab03-183">**未压缩的分区**</span><span class="sxs-lookup"><span data-stu-id="dab03-183">**Partitions not compressed**</span></span>  
 <span data-ttu-id="dab03-184">未压缩的分区号。</span><span class="sxs-lookup"><span data-stu-id="dab03-184">The partition numbers that are not compressed.</span></span> <span data-ttu-id="dab03-185">此属性仅可用于已分区表。</span><span class="sxs-lookup"><span data-stu-id="dab03-185">This property is only available for partitioned tables.</span></span>  
  
 <span data-ttu-id="dab03-186">**使用行压缩的分区**</span><span class="sxs-lookup"><span data-stu-id="dab03-186">**Partitions using row compression**</span></span>  
 <span data-ttu-id="dab03-187">使用行压缩的分区号。</span><span class="sxs-lookup"><span data-stu-id="dab03-187">The partition numbers that are using row compression.</span></span> <span data-ttu-id="dab03-188">此属性仅可用于已分区表。</span><span class="sxs-lookup"><span data-stu-id="dab03-188">This property is only available for partitioned tables.</span></span>  
  
### <a name="filegroup"></a><span data-ttu-id="dab03-189">文件组</span><span class="sxs-lookup"><span data-stu-id="dab03-189">Filegroup</span></span>  
 <span data-ttu-id="dab03-190">**文本文件组**</span><span class="sxs-lookup"><span data-stu-id="dab03-190">**Text filegroup**</span></span>  
 <span data-ttu-id="dab03-191">包含该表文本数据的文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-191">The name of the filegroup that contains the text data for the table.</span></span>  
  
 <span data-ttu-id="dab03-192">**文件组**</span><span class="sxs-lookup"><span data-stu-id="dab03-192">**Filegroup**</span></span>  
 <span data-ttu-id="dab03-193">包含该表的文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-193">The name of the filegroup that contains the table.</span></span>  
  
 <span data-ttu-id="dab03-194">**已对表进行分区**</span><span class="sxs-lookup"><span data-stu-id="dab03-194">**Table is partitioned**</span></span>  
 <span data-ttu-id="dab03-195">可能的值为 `True` 和 `False`。</span><span class="sxs-lookup"><span data-stu-id="dab03-195">Possible values are `True` and `False`.</span></span>  
  
 <span data-ttu-id="dab03-196">**Filestream 文件组**</span><span class="sxs-lookup"><span data-stu-id="dab03-196">**Filestream filegroup**</span></span>  
 <span data-ttu-id="dab03-197">如果该表包含具有 FILESTREAM 属性的 `varbinary(max)` 列，则指定 FILESTREAM 数据文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-197">Specify the name of the FILESTREAM data filegroup if the table has a `varbinary(max)` column that has the FILESTREAM attribute.</span></span> <span data-ttu-id="dab03-198">默认值为默认的 FILESTREAM 数据文件组。</span><span class="sxs-lookup"><span data-stu-id="dab03-198">The default value is the default FILESTREAM data filegroup.</span></span>  
  
 <span data-ttu-id="dab03-199">如果该表不包含 FILESTREAM 数据，则该字段为空白。</span><span class="sxs-lookup"><span data-stu-id="dab03-199">If the table does not contain FILESTREAM data, the field is blank.</span></span>  
  
### <a name="general"></a><span data-ttu-id="dab03-200">常规</span><span class="sxs-lookup"><span data-stu-id="dab03-200">General</span></span>  
 <span data-ttu-id="dab03-201">**Vardecimal 存储格式已启用**</span><span class="sxs-lookup"><span data-stu-id="dab03-201">**Vardecimal storage format is enabled**</span></span>  
 <span data-ttu-id="dab03-202">如果 `True` 为，则此只读值表示 `decimal` `numeric` 使用 vardecimal 存储格式存储和数据类型。</span><span class="sxs-lookup"><span data-stu-id="dab03-202">When `True`, this read-only value indicates that `decimal` and `numeric` data types are stored by using the vardecimal storage format.</span></span> <span data-ttu-id="dab03-203">若要更改此选项，请使用 `vardecimal storage format` [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)的选项。</span><span class="sxs-lookup"><span data-stu-id="dab03-203">To change this option, use the `vardecimal storage format` option of [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="dab03-204">不推荐使用 Vardecimal 存储格式。</span><span class="sxs-lookup"><span data-stu-id="dab03-204">Vardecimal storage format is deprecated.</span></span> <span data-ttu-id="dab03-205">请改用 ROW 压缩。</span><span class="sxs-lookup"><span data-stu-id="dab03-205">Use ROW compression instead.</span></span>  
  
 <span data-ttu-id="dab03-206">**索引空间**</span><span class="sxs-lookup"><span data-stu-id="dab03-206">**Index space**</span></span>  
 <span data-ttu-id="dab03-207">索引在表中所占的空间大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="dab03-207">The amount of space in megabytes that the indexes occupy in the table.</span></span> <span data-ttu-id="dab03-208">此值不包括表的 XML 索引空间使用量。</span><span class="sxs-lookup"><span data-stu-id="dab03-208">This value does not include XML index space usage for the table.</span></span> <span data-ttu-id="dab03-209">如果 XML 索引属于表，则使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="dab03-209">If XML indexes belong to the table, use [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) instead.</span></span>  
  
 <span data-ttu-id="dab03-210">**行计数**</span><span class="sxs-lookup"><span data-stu-id="dab03-210">**Row count**</span></span>  
 <span data-ttu-id="dab03-211">表中的行数。</span><span class="sxs-lookup"><span data-stu-id="dab03-211">The number of rows in the table.</span></span>  
  
 <span data-ttu-id="dab03-212">**数据空间**</span><span class="sxs-lookup"><span data-stu-id="dab03-212">**Data space**</span></span>  
 <span data-ttu-id="dab03-213">数据在表中所占的空间大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="dab03-213">The amount of space in megabytes that the data occupies in the table.</span></span>  
  
### <a name="partitioning"></a><span data-ttu-id="dab03-214">分区</span><span class="sxs-lookup"><span data-stu-id="dab03-214">Partitioning</span></span>  
 <span data-ttu-id="dab03-215">此部分仅适用于已进行分区的表。</span><span class="sxs-lookup"><span data-stu-id="dab03-215">This section is only available if the table is partitioned.</span></span> <span data-ttu-id="dab03-216">有关详细信息，请参阅 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="dab03-216">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="dab03-217">**分区列**</span><span class="sxs-lookup"><span data-stu-id="dab03-217">**Partition column**</span></span>  
 <span data-ttu-id="dab03-218">对表进行分区时所依据的列的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-218">The name of the column on which the table is partitioned.</span></span>  
  
 <span data-ttu-id="dab03-219">**分区方案**</span><span class="sxs-lookup"><span data-stu-id="dab03-219">**Partition scheme**</span></span>  
 <span data-ttu-id="dab03-220">如果表已分区，则为分区方案的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-220">Name of the partition scheme if the table is partitioned.</span></span> <span data-ttu-id="dab03-221">如果表未分区，则该字段为空白。</span><span class="sxs-lookup"><span data-stu-id="dab03-221">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="dab03-222">**分区数**</span><span class="sxs-lookup"><span data-stu-id="dab03-222">**Number of partitions**</span></span>  
 <span data-ttu-id="dab03-223">表中的分区数。</span><span class="sxs-lookup"><span data-stu-id="dab03-223">The number of partitions in the table.</span></span>  
  
 <span data-ttu-id="dab03-224">**FILESTREAM 分区方案**</span><span class="sxs-lookup"><span data-stu-id="dab03-224">**FILESTREAM partition scheme**</span></span>  
 <span data-ttu-id="dab03-225">如果表已分区，则为 FILESTREAM 分区方案的名称。</span><span class="sxs-lookup"><span data-stu-id="dab03-225">The name of the FILESTREAM partition scheme if the table is partitioned.</span></span> <span data-ttu-id="dab03-226">如果表未分区，则该字段为空白。</span><span class="sxs-lookup"><span data-stu-id="dab03-226">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="dab03-227">FILESTREAM 分区方案必须与 **“分区方案”** 选项中指定的方案对称。</span><span class="sxs-lookup"><span data-stu-id="dab03-227">The FILESTREAM partition scheme must be symmetric to the scheme that is specified in the **Partition scheme** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab03-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dab03-228">See Also</span></span>  
 <span data-ttu-id="dab03-229">[查看表定义](view-the-table-definition.md) </span><span class="sxs-lookup"><span data-stu-id="dab03-229">[View the Table Definition](view-the-table-definition.md) </span></span>  
 [<span data-ttu-id="dab03-230">修改列（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="dab03-230">Modify Columns &#40;Database Engine&#41;</span></span>](../tables/modify-columns-database-engine.md)  
  
  
