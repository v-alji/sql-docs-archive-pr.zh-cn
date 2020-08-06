---
title: 备份和还原全文目录和索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c0df49c03325da375427c6566799f374fcc9dd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590144"
---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a><span data-ttu-id="ed8be-102">备份和还原全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="ed8be-102">Back Up and Restore Full-Text Catalogs and Indexes</span></span>
  <span data-ttu-id="ed8be-103">本主题说明如何备份和还原在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中创建的全文索引。</span><span class="sxs-lookup"><span data-stu-id="ed8be-103">This topic explains how to back up and restore full-text indexes created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ed8be-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，全文目录是一个逻辑概念，并不驻留在文件组中。</span><span class="sxs-lookup"><span data-stu-id="ed8be-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the full-text catalog is a logical concept and does not reside in a filegroup.</span></span> <span data-ttu-id="ed8be-105">因此，若要备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的全文目录，必须识别包含属于该目录的全文索引的每个文件组。</span><span class="sxs-lookup"><span data-stu-id="ed8be-105">Therefore, to back up a full-text catalog in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must identify every filegroup that contains a full-text index that belongs to the catalog.</span></span> <span data-ttu-id="ed8be-106">然后您必须逐个备份这些文件组。</span><span class="sxs-lookup"><span data-stu-id="ed8be-106">Then you must back up those filegroups, one by one.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ed8be-107">可以在升级 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 数据库时导入全文目录。</span><span class="sxs-lookup"><span data-stu-id="ed8be-107">It is possible to import full-text catalogs when upgrading a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database.</span></span> <span data-ttu-id="ed8be-108">每个导入的全文目录在其自身的文件组中都是一个数据库文件。</span><span class="sxs-lookup"><span data-stu-id="ed8be-108">Each imported full-text catalog is a database file in its own filegroup.</span></span> <span data-ttu-id="ed8be-109">若要备份导入的目录，只需备份其文件组即可。</span><span class="sxs-lookup"><span data-stu-id="ed8be-109">To back up an imported catalog, simply back up its filegroup.</span></span> <span data-ttu-id="ed8be-110">有关详细信息，请参阅 [联机丛书中的](https://go.microsoft.com/fwlink/?LinkID=121052)备份和还原全文目录 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed8be-110">For more information, see [Backing Up and Restoring Full-Text Catalogs](https://go.microsoft.com/fwlink/?LinkID=121052), in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Books Online.</span></span>  
  
##  <a name="backing-up-the-full-text-indexes-of-a-full-text-catalog"></a><a name="backingup"></a> <span data-ttu-id="ed8be-111">备份全文目录的全文索引</span><span class="sxs-lookup"><span data-stu-id="ed8be-111">Backing Up the Full-Text Indexes of a Full-Text Catalog</span></span>  
  
###  <a name="finding-the-full-text-indexes-of-a-full-text-catalog"></a><a name="Find_FTIs_of_a_Catalog"></a> <span data-ttu-id="ed8be-112">查找全文目录的全文索引</span><span class="sxs-lookup"><span data-stu-id="ed8be-112">Finding the Full-Text Indexes of a Full-Text Catalog</span></span>  
 <span data-ttu-id="ed8be-113">你可以通过使用以下 [SELECT](/sql/t-sql/queries/select-transact-sql) 语句检索全文索引的属性，此语句将从 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) 和 [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) 目录视图选择一些列。</span><span class="sxs-lookup"><span data-stu-id="ed8be-113">You can retrieve the properties of the full-text indexes by using the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement, which selects columns from the [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) and [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) catalog views.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  

  
###  <a name="finding-the-filegroup-or-file-that-contains-a-full-text-index"></a><a name="Find_FG_of_FTI"></a> <span data-ttu-id="ed8be-114">查找包含全文索引的文件组或文件</span><span class="sxs-lookup"><span data-stu-id="ed8be-114">Finding the Filegroup or File That Contains a Full-Text Index</span></span>  
 <span data-ttu-id="ed8be-115">创建全文索引时，该全文索引将放在以下某个位置：</span><span class="sxs-lookup"><span data-stu-id="ed8be-115">When a full-text index is created, it is placed in one of the following locations:</span></span>  
  
-   <span data-ttu-id="ed8be-116">用户指定的文件组。</span><span class="sxs-lookup"><span data-stu-id="ed8be-116">A user-specified filegroup.</span></span>  
  
-   <span data-ttu-id="ed8be-117">与基表或视图相同的文件组（对于未分区表而言）。</span><span class="sxs-lookup"><span data-stu-id="ed8be-117">The same filegroup as base table or view, for a nonpartitioned table.</span></span>  
  
-   <span data-ttu-id="ed8be-118">主文件组（对于分区表而言）。</span><span class="sxs-lookup"><span data-stu-id="ed8be-118">The primary filegroup, for a partitioned table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed8be-119">有关创建全文索引的详细信息，请参阅[创建和管理全文索引](create-and-manage-full-text-indexes.md)和 [CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ed8be-119">For information about creating a full-text index, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) and [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="ed8be-120">若要查找表或视图的全文索引所属的文件组，请使用以下查询，其中 *object_name* 为表或视图的名称：</span><span class="sxs-lookup"><span data-stu-id="ed8be-120">To find the filegroup of full-text index on a table or view, use the following query, where *object_name* is the name of the table or view:</span></span>  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  

  
###  <a name="backing-up-the-filegroups-that-contain-full-text-indexes"></a><a name="Back_up_FTIs_of_FTC"></a> <span data-ttu-id="ed8be-121">备份包含全文索引的文件组</span><span class="sxs-lookup"><span data-stu-id="ed8be-121">Backing Up the Filegroups That Contain Full-Text Indexes</span></span>  
 <span data-ttu-id="ed8be-122">在找到包含全文目录索引的文件组后，您需要备份找到的每个文件组。</span><span class="sxs-lookup"><span data-stu-id="ed8be-122">After you find the filegroups that contain the indexes of a full-text catalog, you need back up each of the filegroups.</span></span> <span data-ttu-id="ed8be-123">在备份过程中，不会删除或添加全文目录。</span><span class="sxs-lookup"><span data-stu-id="ed8be-123">During the backup process, full-text catalogs may not be dropped or added.</span></span>  
  
 <span data-ttu-id="ed8be-124">文件组的首次备份必须是完整文件备份。</span><span class="sxs-lookup"><span data-stu-id="ed8be-124">The first backup of a filegroup must be a full file backup.</span></span> <span data-ttu-id="ed8be-125">在创建文件组的完整文件备份之后，您可以仅备份文件组中的更改，方法是：创建一系列基于完整文件备份的一个或多个差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="ed8be-125">After you have created a full file backup for a filegroup, you could back up only the changes in a filegroup by creating a series of one or more differential file backups that are based on the full file backup.</span></span>  
  
 <span data-ttu-id="ed8be-126">**备份文件和文件组**</span><span class="sxs-lookup"><span data-stu-id="ed8be-126">**To back up files and filegroups**</span></span>  
  
-   [<span data-ttu-id="ed8be-127">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed8be-127">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="ed8be-128">BACKUP (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed8be-128">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  

  
##  <a name="restoring-a-full-text-index"></a><a name="Restore_FTI"></a> <span data-ttu-id="ed8be-129">还原全文索引</span><span class="sxs-lookup"><span data-stu-id="ed8be-129">Restoring a Full-Text Index</span></span>  
 <span data-ttu-id="ed8be-130">还原备份的文件组将还原全文索引文件，以及此文件组中的其他文件。</span><span class="sxs-lookup"><span data-stu-id="ed8be-130">Restoring a backed-up filegroup restores the full-text index files, as well as the other files in the filegroup.</span></span> <span data-ttu-id="ed8be-131">默认情况下，文件组将还原至该文件组在备份时所在的磁盘位置。</span><span class="sxs-lookup"><span data-stu-id="ed8be-131">By default, the filegroup is restored to the disk location on which the filegroup was backed up.</span></span>  
  
 <span data-ttu-id="ed8be-132">如果在创建备份时全文索引表处于联机状态并且正在运行填充，则在还原之后将继续填充。</span><span class="sxs-lookup"><span data-stu-id="ed8be-132">If a full-text indexed table was online and a population was running when the backup was created, the population is resumed after the restore.</span></span>  
  
 <span data-ttu-id="ed8be-133">**还原文件组**</span><span class="sxs-lookup"><span data-stu-id="ed8be-133">**To restore a filegroup**</span></span>  
  
-   [<span data-ttu-id="ed8be-134">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed8be-134">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="ed8be-135">在现有文件上还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed8be-135">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="ed8be-136">将文件还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed8be-136">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="ed8be-137">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ed8be-137">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  

  
## <a name="see-also"></a><span data-ttu-id="ed8be-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed8be-138">See Also</span></span>  
 <span data-ttu-id="ed8be-139">[管理和监视服务器实例的全文搜索](manage-and-monitor-full-text-search-for-a-server-instance.md) </span><span class="sxs-lookup"><span data-stu-id="ed8be-139">[Manage and Monitor Full-Text Search for a Server Instance](manage-and-monitor-full-text-search-for-a-server-instance.md) </span></span>  
 [<span data-ttu-id="ed8be-140">升级全文搜索</span><span class="sxs-lookup"><span data-stu-id="ed8be-140">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)  
  
  
