---
title: 数据库功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 04518abb-8581-47c8-a601-ee9136c3c0eb
author: rothja
ms.author: jroth
ms.openlocfilehash: 56b9f9ba9cc6e11ea82b822ae10b31710c8617b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587860"
---
# <a name="database-features"></a><span data-ttu-id="dd838-102">数据库功能</span><span class="sxs-lookup"><span data-stu-id="dd838-102">Database Features</span></span>
  <span data-ttu-id="dd838-103">本节包含与数据库关联的功能和任务、数据库对象、数据类型和用于处理或管理数据的机制。</span><span class="sxs-lookup"><span data-stu-id="dd838-103">This section contains the features and tasks associated with databases, database objects, data types, and the mechanisms used to work with or manage data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd838-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="dd838-104">In This Section</span></span>  
  
|||
|--|--|
|[<span data-ttu-id="dd838-105">数据库</span><span class="sxs-lookup"><span data-stu-id="dd838-105">Databases</span></span>](databases/databases.md)|[<span data-ttu-id="dd838-106">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="dd838-106">Back Up and Restore of SQL Server Databases</span></span>](backup-restore/back-up-and-restore-of-sql-server-databases.md)|  
|[<span data-ttu-id="dd838-107">表</span><span class="sxs-lookup"><span data-stu-id="dd838-107">Tables</span></span>](tables/tables.md)|[<span data-ttu-id="dd838-108">序列号</span><span class="sxs-lookup"><span data-stu-id="dd838-108">Sequence Numbers</span></span>](sequence-numbers/sequence-numbers.md)|[<span data-ttu-id="dd838-109">批量导入和导出数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-109">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](import-export/bulk-import-and-export-of-data-sql-server.md)|  
|[<span data-ttu-id="dd838-110">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="dd838-110">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp/in-memory-oltp-in-memory-optimization.md)|[<span data-ttu-id="dd838-111">DDL 触发器</span><span class="sxs-lookup"><span data-stu-id="dd838-111">DDL Triggers</span></span>](triggers/ddl-triggers.md)|[<span data-ttu-id="dd838-112">数据压缩</span><span class="sxs-lookup"><span data-stu-id="dd838-112">Data Compression</span></span>](data-compression/data-compression.md)|  
|[<span data-ttu-id="dd838-113">索引</span><span class="sxs-lookup"><span data-stu-id="dd838-113">Indexes</span></span>](indexes/indexes.md)|[<span data-ttu-id="dd838-114">DML 触发器</span><span class="sxs-lookup"><span data-stu-id="dd838-114">DML Triggers</span></span>](triggers/dml-triggers.md)|[<span data-ttu-id="dd838-115">Transact-SQL 中的 OLE 自动化对象</span><span class="sxs-lookup"><span data-stu-id="dd838-115">OLE Automation Objects in Transact-SQL</span></span>](stored-procedures/ole-automation-objects-in-transact-sql.md)|  
|[<span data-ttu-id="dd838-116">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="dd838-116">Partitioned Tables and Indexes</span></span>](partitions/partitioned-tables-and-indexes.md)|[<span data-ttu-id="dd838-117">同义词（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="dd838-117">Synonyms &#40;Database Engine&#41;</span></span>](synonyms/synonyms-database-engine.md)|[<span data-ttu-id="dd838-118">事件通知</span><span class="sxs-lookup"><span data-stu-id="dd838-118">Event Notifications</span></span>](service-broker/event-notifications.md)|  
|[<span data-ttu-id="dd838-119">Views</span><span class="sxs-lookup"><span data-stu-id="dd838-119">Views</span></span>](views/views.md)|[<span data-ttu-id="dd838-120">XML 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-120">XML Data &#40;SQL Server&#41;</span></span>](xml/xml-data-sql-server.md)|[<span data-ttu-id="dd838-121">监视和优化性能</span><span class="sxs-lookup"><span data-stu-id="dd838-121">Monitor and Tune for Performance</span></span>](performance/monitor-and-tune-for-performance.md)|  
|[<span data-ttu-id="dd838-122">存储过程（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="dd838-122">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures/stored-procedures-database-engine.md)|[<span data-ttu-id="dd838-123">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial/spatial-data-sql-server.md)||  
|[<span data-ttu-id="dd838-124">搜索 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dd838-124">Search &#40;SQL Server&#41;</span></span>](../database-engine/search-sql-server.md)|[<span data-ttu-id="dd838-125">二进制大型对象 (Blob) 数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-125">Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;</span></span>](blob/binary-large-object-blob-data-sql-server.md)||  
|[<span data-ttu-id="dd838-126">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="dd838-126">User-Defined Functions</span></span>](user-defined-functions/user-defined-functions.md)|[<span data-ttu-id="dd838-127">数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="dd838-127">Data-tier Applications</span></span>](data-tier-applications/data-tier-applications.md)||  
|[<span data-ttu-id="dd838-128">统计信息</span><span class="sxs-lookup"><span data-stu-id="dd838-128">Statistics</span></span>](statistics/statistics.md)|[<span data-ttu-id="dd838-129">事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-129">The Transaction Log &#40;SQL Server&#41;</span></span>](logs/the-transaction-log-sql-server.md)||  
|[<span data-ttu-id="dd838-130">计划指南</span><span class="sxs-lookup"><span data-stu-id="dd838-130">Plan Guides</span></span>](performance/plan-guides.md)|[<span data-ttu-id="dd838-131">数据库检查点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dd838-131">Database Checkpoints &#40;SQL Server&#41;</span></span>](logs/database-checkpoints-sql-server.md)||  
  
  
