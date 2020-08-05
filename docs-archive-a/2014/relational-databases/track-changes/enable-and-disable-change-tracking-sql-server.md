---
title: 启用和禁用更改跟踪 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], disabling
- data changes [SQL Server]
- change tracking [SQL Server], enabling
- tracking data changes [SQL Server]
- change tracking [SQL Server], configuring
- data [SQL Server], changing
ms.assetid: 1c92ec7e-ae53-4498-8bfd-c66a42a24d54
author: rothja
ms.author: jroth
ms.openlocfilehash: 402c63ae03df14e3a725fbc440575f5233d502f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581147"
---
# <a name="enable-and-disable-change-tracking-sql-server"></a><span data-ttu-id="6470e-102">启用和禁用更改跟踪 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6470e-102">Enable and Disable Change Tracking (SQL Server)</span></span>
  <span data-ttu-id="6470e-103">本主题说明如何对数据库和表启用和禁用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-103">This topic describes how to enable and disable change tracking for a database and a table.</span></span>  
  
## <a name="enable-change-tracking-for-a-database"></a><span data-ttu-id="6470e-104">对数据库启用更改跟踪</span><span class="sxs-lookup"><span data-stu-id="6470e-104">Enable Change Tracking for a Database</span></span>  
 <span data-ttu-id="6470e-105">您必须先在数据库级别启用更改跟踪，然后才能使用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-105">Before you can use change tracking, you must enable change tracking at the database level.</span></span> <span data-ttu-id="6470e-106">下面的示例显示了如何使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)来启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-106">The following example shows how to enable change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(CHANGE_RETENTION = 2 DAYS, AUTO_CLEANUP = ON)  
```  
  
 <span data-ttu-id="6470e-107">你还可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 数据库属性（“ChangeTracking”页） [数据库属性（“ChangeTracking”页）](../databases/database-properties-changetracking-page.md) 中启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-107">You can also enable change tracking in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="6470e-108">可以在启用更改跟踪时指定 CHANGE_RETENTION 和 AUTO_CLEANUP 选项，并且可以在启用更改跟踪后随时更改这些值。</span><span class="sxs-lookup"><span data-stu-id="6470e-108">You can specify the CHANGE_RETENTION and AUTO_CLEANUP options when you enable change tracking, and you can change the values at any time after change tracking is enabled.</span></span>  
  
 <span data-ttu-id="6470e-109">更改保持期值指定了更改跟踪信息的保留时间。</span><span class="sxs-lookup"><span data-stu-id="6470e-109">The change retention value specifies the time period for which change tracking information is kept.</span></span> <span data-ttu-id="6470e-110">早于此时间的更改跟踪信息将被定期删除。</span><span class="sxs-lookup"><span data-stu-id="6470e-110">Change tracking information that is older than this time period is removed periodically.</span></span> <span data-ttu-id="6470e-111">设置该值时，应考虑应用程序与数据库中的表进行同步的频率。</span><span class="sxs-lookup"><span data-stu-id="6470e-111">When you are setting this value, you should consider how often applications will synchronize with the tables in the database.</span></span> <span data-ttu-id="6470e-112">指定的保持期必须至少等于最大同步时间间隔。</span><span class="sxs-lookup"><span data-stu-id="6470e-112">The specified retention period must be at least as long as the maximum time period between synchronizations.</span></span> <span data-ttu-id="6470e-113">如果应用程序获取更改的时间间隔过长，则返回的结果可能不正确，因为某些更改信息可能已被删除。</span><span class="sxs-lookup"><span data-stu-id="6470e-113">If an application obtains changes at longer intervals, the results that are returned might be incorrect because some of the change information has probably been removed.</span></span> <span data-ttu-id="6470e-114">若要避免获取错误的结果，应用程序可以使用 CHANGE_TRACKING_MIN_VALID_VERSION 系统函数来确定同步之间的时间间隔是否已太长。</span><span class="sxs-lookup"><span data-stu-id="6470e-114">To avoid obtaining incorrect results, an application can use the CHANGE_TRACKING_MIN_VALID_VERSION system function to determine whether the interval between synchronizations has been too long.</span></span>  
  
 <span data-ttu-id="6470e-115">可使用 AUTO_CLEANUP 选项来启用或禁用删除陈旧的更改跟踪信息的清除任务。</span><span class="sxs-lookup"><span data-stu-id="6470e-115">You can use the AUTO_CLEANUP option to enable or disable the cleanup task that removes old change tracking information.</span></span> <span data-ttu-id="6470e-116">如果出现临时性问题使得应用程序无法同步，并且在问题解决之前必须暂停用于删除早于保持期的更改跟踪信息的进程，则该设置会很有用。</span><span class="sxs-lookup"><span data-stu-id="6470e-116">This can be useful when there is a temporary problem that prevents applications from synchronizing and the process for removing change tracking information older than the retention period must be paused until the problem is resolved.</span></span>  
  
 <span data-ttu-id="6470e-117">对于使用更改跟踪的任何数据库，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="6470e-117">For any database that uses change tracking, be aware of the following:</span></span>  
  
-   <span data-ttu-id="6470e-118">若要使用更改跟踪，必须将数据库兼容级别设为 90 或更高。</span><span class="sxs-lookup"><span data-stu-id="6470e-118">To use change tracking, the database compatibility level must be set to 90 or greater.</span></span> <span data-ttu-id="6470e-119">如果数据库的兼容级别低于 90，则可以配置更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-119">If a database has a compatibility level of less than 90, you can configure change tracking.</span></span> <span data-ttu-id="6470e-120">但是，用于获取更改跟踪信息的 CHANGETABLE 函数将返回错误。</span><span class="sxs-lookup"><span data-stu-id="6470e-120">However, the CHANGETABLE function, which is used to obtain change tracking information, will return an error.</span></span>  
  
-   <span data-ttu-id="6470e-121">使用快照隔离是帮助确保所有更改跟踪信息保持一致的最简单方式。</span><span class="sxs-lookup"><span data-stu-id="6470e-121">Using snapshot isolation is the easiest way for you to help ensure that all change tracking information is consistent.</span></span> <span data-ttu-id="6470e-122">因此，我们强烈建议将数据库的快照隔离设为 ON。</span><span class="sxs-lookup"><span data-stu-id="6470e-122">For this reason, we strongly recommend that snapshot isolation be set to ON for the database.</span></span> <span data-ttu-id="6470e-123">有关详细信息，请参阅[处理更改跟踪 (SQL Server)](work-with-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6470e-123">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
## <a name="enable-change-tracking-for-a-table"></a><span data-ttu-id="6470e-124">对表启用更改跟踪</span><span class="sxs-lookup"><span data-stu-id="6470e-124">Enable Change Tracking for a Table</span></span>  
 <span data-ttu-id="6470e-125">对于要跟踪的每个表都必须启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-125">Change tracking must be enabled for each table that you want tracked.</span></span> <span data-ttu-id="6470e-126">启用更改跟踪后，将会为表中受 DML 操作影响的所有行保留更改跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="6470e-126">When change tracking is enabled, change tracking information is maintained for all rows in the table that are affected by a DML operation.</span></span>  
  
 <span data-ttu-id="6470e-127">下面的示例显示了如何使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)来对表启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-127">The following example shows how to enable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
 <span data-ttu-id="6470e-128">你还可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 数据库属性（“ChangeTracking”页） [数据库属性（“ChangeTracking”页）](../databases/database-properties-changetracking-page.md) 中启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-128">You can also enable change tracking for a table in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="6470e-129">当 TRACK_COLUMNS_UPDATED 选项设为 ON 时， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 会将有关哪些列已更新的额外信息存储到内部更改跟踪表中。</span><span class="sxs-lookup"><span data-stu-id="6470e-129">When the TRACK_COLUMNS_UPDATED option is set to ON, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] stores extra information about which columns were updated to the internal change tracking table.</span></span> <span data-ttu-id="6470e-130">列跟踪使应用程序可以只同步那些已更新的列。</span><span class="sxs-lookup"><span data-stu-id="6470e-130">Column tracking can enable an application to synchronize only those columns that were updated.</span></span> <span data-ttu-id="6470e-131">这可以提高效率和性能。</span><span class="sxs-lookup"><span data-stu-id="6470e-131">This can improve efficiency and performance.</span></span> <span data-ttu-id="6470e-132">但是，由于保留列跟踪信息增加了一些额外的存储开销，因而默认情况下此选项设为 OFF。</span><span class="sxs-lookup"><span data-stu-id="6470e-132">However, because maintaining column tracking information adds some extra storage overhead, this option is set to OFF by default.</span></span>  
  
## <a name="disable-change-tracking-for-a-database-or-table"></a><span data-ttu-id="6470e-133">为数据库或表禁用更改跟踪</span><span class="sxs-lookup"><span data-stu-id="6470e-133">Disable Change Tracking for a Database or Table</span></span>  
 <span data-ttu-id="6470e-134">必须首先为所有启用了更改跟踪的表禁用更改跟踪，然后才能将数据库的更改跟踪设为 OFF。</span><span class="sxs-lookup"><span data-stu-id="6470e-134">Change tracking must first be disabled for all change-tracked tables before change tracking can be set to OFF for the database.</span></span> <span data-ttu-id="6470e-135">若要确定数据库中哪些表启用了更改跟踪，请使用 [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="6470e-135">To determine the tables that have change tracking enabled for a database, use the [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) catalog view.</span></span>  
  
 <span data-ttu-id="6470e-136">当数据库中没有用于跟踪更改的表时，便可以禁用数据库的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-136">When no tables in a database track changes, you can disable change tracking for the database.</span></span> <span data-ttu-id="6470e-137">下面的示例显示如何使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)对数据库禁用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-137">The following example shows how to disable change tracking for a database by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF  
```  
  
 <span data-ttu-id="6470e-138">下面的示例显示了如何使用 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)对表禁用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6470e-138">The following example shows how to disable change tracking for a table by using [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
```sql  
ALTER TABLE Person.Contact  
DISABLE CHANGE_TRACKING;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6470e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6470e-139">See Also</span></span>  
 <span data-ttu-id="6470e-140">[数据库属性（“ChangeTracking”页）](../databases/database-properties-changetracking-page.md) </span><span class="sxs-lookup"><span data-stu-id="6470e-140">[Database Properties &#40;ChangeTracking Page&#41;](../databases/database-properties-changetracking-page.md) </span></span>  
 <span data-ttu-id="6470e-141">[ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span><span class="sxs-lookup"><span data-stu-id="6470e-141">[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options) </span></span>  
 <span data-ttu-id="6470e-142">[sys.change_tracking_databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span><span class="sxs-lookup"><span data-stu-id="6470e-142">[sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases) </span></span>  
 <span data-ttu-id="6470e-143">[sys.change_tracking_tables (Transact-SQL)](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span><span class="sxs-lookup"><span data-stu-id="6470e-143">[sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) </span></span>  
 <span data-ttu-id="6470e-144">[跟踪数据更改 (SQL Server)](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6470e-144">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="6470e-145">[关于更改跟踪 (SQL Server)](../track-changes/about-change-tracking-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6470e-145">[About Change Tracking &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md) </span></span>  
 <span data-ttu-id="6470e-146">[处理变更数据 (SQL Server)](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6470e-146">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="6470e-147">管理更改跟踪 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6470e-147">Manage Change Tracking &#40;SQL Server&#41;</span></span>](manage-change-tracking-sql-server.md)  
  
  
