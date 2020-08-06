---
title: 管理和监视语义搜索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690455"
---
# <a name="manage-and-monitor-semantic-search"></a><span data-ttu-id="9dd41-102">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="9dd41-102">Manage and Monitor Semantic Search</span></span>
  <span data-ttu-id="9dd41-103">说明语义索引编制过程以及与管理和监视索引相关的任务。</span><span class="sxs-lookup"><span data-stu-id="9dd41-103">Describes the process of semantic indexing and the tasks related to managing and monitoring the indexes.</span></span>  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a><span data-ttu-id="9dd41-104">如何：检查语义索引编制的状态</span><span class="sxs-lookup"><span data-stu-id="9dd41-104">How To: Check the Status of Semantic Indexing</span></span>  
 <span data-ttu-id="9dd41-105">**语义索引编制的第一阶段是否已完成？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-105">**Is the first phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="9dd41-106">查询动态管理视图 [sys.dm_fts_index_population (Transact SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)，并检查 **status** 和 **status_description** 列。</span><span class="sxs-lookup"><span data-stu-id="9dd41-106">Query the dynamic management view, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), and check the **status** and **status_description** columns.</span></span>  
  
 <span data-ttu-id="9dd41-107">索引编制的第一阶段包括填充全文关键字索引和语义关键短语索引，以及提取文档相似性数据。</span><span class="sxs-lookup"><span data-stu-id="9dd41-107">The first phase of indexing includes the population of the full-text keyword index and the semantic key phrase index, as well as the extraction of document similarity data.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="9dd41-108">**语义索引编制的第二阶段是否已完成？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-108">**Is the second phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="9dd41-109">查询动态管理视图 [sys.dm_fts_semantic_similarity_population (Transact SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)，并检查 **status** 和 **status_description** 列。</span><span class="sxs-lookup"><span data-stu-id="9dd41-109">Query the dynamic management view, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), and check the **status** and **status_description** columns..</span></span>  
  
 <span data-ttu-id="9dd41-110">索引编制的第二阶段包括填充语义文档相似性索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-110">The second phase of indexing includes the population of the semantic document similarity index.</span></span>  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a><span data-ttu-id="9dd41-111">如何：检查语义索引的大小</span><span class="sxs-lookup"><span data-stu-id="9dd41-111">How To: Check the Size of the Semantic Indexes</span></span>  
 <span data-ttu-id="9dd41-112">**语义关键短语索引或语义文档相似性索引的逻辑大小是多少？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-112">**What is the logical size of a semantic key phrase index or a semantic document similarity index?**</span></span>  
 <span data-ttu-id="9dd41-113">查询动态管理视图 [sys.dm_db_fts_index_physical_stats (Transact SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9dd41-113">Query the dynamic management view, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="9dd41-114">以索引页数显示该逻辑大小。</span><span class="sxs-lookup"><span data-stu-id="9dd41-114">The logical size is displayed in number of index pages.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="9dd41-115">**全文目录的全文索引和语义索引的总大小是多少？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-115">**What is the total size of the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="9dd41-116">查询 [FULLTEXTCATALOGPROPERTY (Transact SQL)](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 元数据函数的 **IndexSize** 属性 。</span><span class="sxs-lookup"><span data-stu-id="9dd41-116">Query the **IndexSize** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 <span data-ttu-id="9dd41-117">**有多少项编入全文目录的全文索引和语义索引？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-117">**How many items are indexed in the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="9dd41-118">查询 [FULLTEXTCATALOGPROPERTY (Transact SQL)](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 元数据函数的 **ItemCount** 属性 。</span><span class="sxs-lookup"><span data-stu-id="9dd41-118">Query the **ItemCount** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a><span data-ttu-id="9dd41-119">如何：强制填充语义索引</span><span class="sxs-lookup"><span data-stu-id="9dd41-119">How To: Force the Population of the Semantic Indexes</span></span>  
 <span data-ttu-id="9dd41-120">可以使用 START/STOP/PAUSE 或 RESUME POPULATION 子句以及针对全文索引而描述的相同语法和行为，强制填充全文索引和语义索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-120">You can force the population of full-text and semantic indexes by using the START/STOP/PAUSE or RESUME POPULATION clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="9dd41-121">更多详细信息，请参阅 [ALTER FULLTEXT INDEX (Transact-SQL )](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 和[填充全文索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="9dd41-121">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) and [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="9dd41-122">由于语义索引编制依赖于全文索引编制，因此仅在填充关联的全文索引后填充语义索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-122">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="9dd41-123">**示例：启动全文索引和语义索引的完全填充**</span><span class="sxs-lookup"><span data-stu-id="9dd41-123">**Example: Start a full population of full-text and semantic indexes**</span></span>  
  
 <span data-ttu-id="9dd41-124">以下示例通过更改 AdventureWorks2012 示例数据库的 **Production.Document** 表的现有全文索引，启动全文索引和语义索引的完全填充。</span><span class="sxs-lookup"><span data-stu-id="9dd41-124">The following example starts full population of both full-text and semantic indexes by altering an existing full-text index on the **Production.Document** table in the AdventureWorks2012 sample database.</span></span>  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a><span data-ttu-id="9dd41-125">如何禁用或重新启用语义索引编制</span><span class="sxs-lookup"><span data-stu-id="9dd41-125">How To: Disable or Re-enable Semantic Indexing</span></span>  
 <span data-ttu-id="9dd41-126">可以使用 ENABLE/DISABLE 子句以及针对全文索引而描述的相同语法和行为，启用或禁用全文索引编制或语义索引编制。</span><span class="sxs-lookup"><span data-stu-id="9dd41-126">You can enable or disable full-text or semantic indexing by using the ENABLE/DISABLE clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="9dd41-127">有关详细信息，请参阅 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9dd41-127">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="9dd41-128">禁用和挂起语义索引编制时，可以继续成功进行针对语义数据的查询并返回以前的索引数据。</span><span class="sxs-lookup"><span data-stu-id="9dd41-128">When semantic indexing is disabled and suspended, queries over semantic data continue to work successfully and to return previously indexed data.</span></span> <span data-ttu-id="9dd41-129">此行为与全文搜索的行为不一致。</span><span class="sxs-lookup"><span data-stu-id="9dd41-129">This behavior is not consistent with the behavior of Full-Text Search.</span></span>  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a><span data-ttu-id="9dd41-130">语义索引的阶段</span><span class="sxs-lookup"><span data-stu-id="9dd41-130">Phases of Semantic Indexing</span></span>  
 <span data-ttu-id="9dd41-131">语义搜索对于启用它的每个列将两种类型的数据编入索引：</span><span class="sxs-lookup"><span data-stu-id="9dd41-131">Semantic Search indexes two kinds of data for each column on which it is enabled:</span></span>  
  
1.  <span data-ttu-id="9dd41-132">**关键短语**</span><span class="sxs-lookup"><span data-stu-id="9dd41-132">**Key phrases**</span></span>  
  
2.  <span data-ttu-id="9dd41-133">**文档相似性**</span><span class="sxs-lookup"><span data-stu-id="9dd41-133">**Document similarity**</span></span>  
  
 <span data-ttu-id="9dd41-134">语义索引编制在两个阶段中发生，与全文索引编制一起进行：</span><span class="sxs-lookup"><span data-stu-id="9dd41-134">Semantic indexing occurs in two phases, in conjunction with full-text indexing:</span></span>  
  
1.  <span data-ttu-id="9dd41-135">**阶段 1**。</span><span class="sxs-lookup"><span data-stu-id="9dd41-135">**Phase 1**.</span></span> <span data-ttu-id="9dd41-136">同时并行填充全文关键字索引和语义关键短语索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-136">The full-text keyword index and the semantic key phrase index are populated in parallel at the same time.</span></span> <span data-ttu-id="9dd41-137">还在此时提取编制文档相似性索引所需的数据。</span><span class="sxs-lookup"><span data-stu-id="9dd41-137">The data required to index document similarity is also extracted at this time.</span></span>  
  
2.  <span data-ttu-id="9dd41-138">**阶段 2**：</span><span class="sxs-lookup"><span data-stu-id="9dd41-138">**Phase 2**.</span></span> <span data-ttu-id="9dd41-139">然后填充语义文档相似性索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-139">The semantic document similarity index is then populated.</span></span> <span data-ttu-id="9dd41-140">此索引依赖于在前一阶段填充的两个索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-140">This index depends on both indexes that were populated in the preceding phase.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a><span data-ttu-id="9dd41-141">问题：未填充语义索引</span><span class="sxs-lookup"><span data-stu-id="9dd41-141">Problem: Semantic Indexes Are Not Populated</span></span>  
 <span data-ttu-id="9dd41-142">**是否已填充关联的全文索引？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-142">**Are the associated full-text indexes populated?**</span></span>  
 <span data-ttu-id="9dd41-143">由于语义索引编制依赖于全文索引编制，因此仅在填充关联的全文索引后填充语义索引。</span><span class="sxs-lookup"><span data-stu-id="9dd41-143">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="9dd41-144">**是否正确安装和配置了全文搜索和语义搜索？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-144">**Are full-text search and semantic search properly installed and configured?**</span></span>  
 <span data-ttu-id="9dd41-145">有关详细信息，请参阅 [安装和配置语义搜索](install-and-configure-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="9dd41-145">For more information, see [Install and Configure Semantic Search](install-and-configure-semantic-search.md).</span></span>  
  
 <span data-ttu-id="9dd41-146">**FDHOST 服务是否不可用或存在导致全文索引编制失败的其他情况？**</span><span class="sxs-lookup"><span data-stu-id="9dd41-146">**Is the FDHOST service not available, or is there another condition that would cause full-text indexing to fail?**</span></span>  
 <span data-ttu-id="9dd41-147">有关详细信息，请参阅 [全文索引疑难解答](troubleshoot-full-text-indexing.md)。</span><span class="sxs-lookup"><span data-stu-id="9dd41-147">For more information, see [Troubleshoot Full-Text Indexing](troubleshoot-full-text-indexing.md).</span></span>  
  
  
