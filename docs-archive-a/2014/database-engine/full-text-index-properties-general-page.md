---
title: 全文本索引属性 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
ms.openlocfilehash: 61b9f2948df138c39230cf6f5787c395a364c695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591539"
---
# <a name="full-text-index-properties-general-page"></a><span data-ttu-id="1a9e9-102">全文索引属性（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="1a9e9-102">Full-Text Index Properties (General Page)</span></span>
  <span data-ttu-id="1a9e9-103">**查看或更改全文索引的可修改属性**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-103">**To view or change the modifiable properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="1a9e9-104">管理全文索引</span><span class="sxs-lookup"><span data-stu-id="1a9e9-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="1a9e9-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="1a9e9-105">UI element list</span></span>  
 <span data-ttu-id="1a9e9-106">**全文目录**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-106">**Full-Text Catalog**</span></span>  
 <span data-ttu-id="1a9e9-107">显示全文索引所关联的全文目录的名称。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-107">Displays the name of the full-text catalog with which the full-text index is associated.</span></span>  
  
 <span data-ttu-id="1a9e9-108">**Database**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-108">**Database**</span></span>  
 <span data-ttu-id="1a9e9-109">显示驻留全文索引的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-109">Displays the name of the database in which the full-text index resides.</span></span>  
  
 <span data-ttu-id="1a9e9-110">**表**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-110">**Table**</span></span>  
 <span data-ttu-id="1a9e9-111">显示定义全文索引的表的名称。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-111">Displays the name of the table on which the full-text index is defined.</span></span>  
  
 <span data-ttu-id="1a9e9-112">**全文索引键**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-112">**Full-Text Index Key**</span></span>  
 <span data-ttu-id="1a9e9-113">显示全文索引关键的名称，此键是表的单个列上的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-113">Displays the name of the full-text index key, which is a unique index on a single column of the table.</span></span>  
  
 <span data-ttu-id="1a9e9-114">**表全文填充状态**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-114">**Table Full-Text Populate Status**</span></span>  
 <span data-ttu-id="1a9e9-115">显示全文索引表的填充状态。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-115">Displays the population status of the full-text indexed table.</span></span>  
  
 <span data-ttu-id="1a9e9-116">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="1a9e9-116">The possible values are as follows:</span></span>  
  
 <span data-ttu-id="1a9e9-117">0 = 空闲。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-117">0 = Idle.</span></span>  
  
 <span data-ttu-id="1a9e9-118">1 = 完整填充正在进行中。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-118">1 = Full population is in progress.</span></span>  
  
 <span data-ttu-id="1a9e9-119">2 = 增量填充正在进行中。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-119">2 = Incremental population is in progress.</span></span>  
  
 <span data-ttu-id="1a9e9-120">3 = 跟踪更改的传播正在进行中。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-120">3 = Propagation of tracked changes is in progress.</span></span>  
  
 <span data-ttu-id="1a9e9-121">4 = 后台更新索引正在进行中，比如自动更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-121">4 = Background update index is in progress, such as automatic change tracking.</span></span>  
  
 <span data-ttu-id="1a9e9-122">5 = 全文索引已中止或暂停。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-122">5 = Full-text indexing is throttled or paused.</span></span>  
  
 <span data-ttu-id="1a9e9-123">**活动全文索引**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-123">**Active Full-Text Index**</span></span>  
 <span data-ttu-id="1a9e9-124">指示表是否有活动的全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-124">Indicates whether the table has an active full-text index.</span></span>  
  
 <span data-ttu-id="1a9e9-125">1 = True</span><span class="sxs-lookup"><span data-stu-id="1a9e9-125">1 = True</span></span>  
  
 <span data-ttu-id="1a9e9-126">0 = False</span><span class="sxs-lookup"><span data-stu-id="1a9e9-126">0 = False</span></span>  
  
 <span data-ttu-id="1a9e9-127">**全文索引文件组**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-127">**Full-Text Index Filegroup**</span></span>  
 <span data-ttu-id="1a9e9-128">全文索引所属的文件组。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-128">The filegroup to which the full-text index belongs.</span></span>  
  
 <span data-ttu-id="1a9e9-129">**全文索引非索引字表**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-129">**Full-Text Index Stoplist**</span></span>  
 <span data-ttu-id="1a9e9-130">当前与全文索引关联的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-130">The stoplist that is currently associated with the full-text index.</span></span> <span data-ttu-id="1a9e9-131">非索引字表是 [非索引字](../relational-databases/search/full-text-search.md)的列表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-131">A stoplist is a list of [stopwords](../relational-databases/search/full-text-search.md).</span></span> <span data-ttu-id="1a9e9-132">与全文索引关联的非索引字表（如果有）适用于该索引的全文查询。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-132">The stoplist associated with a full-text index, if any, is applied to full-text queries on that index.</span></span> <span data-ttu-id="1a9e9-133">您可以通过从列表中选择，从索引中删除非索引字表 **\<OFF>** ，也可以选择其他非索引字表; **\<SYSTEM>** 表示系统非索引字表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-133">You can remove the stoplist from the index by selecting **\<OFF>** from the list, or you can select a different stoplist; **\<SYSTEM>** indicates the system stoplist.</span></span>  
  
 <span data-ttu-id="1a9e9-134">**创建非索引字表**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-134">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="1a9e9-135">为全文搜索配置和管理非索引字和非索引字表</span><span class="sxs-lookup"><span data-stu-id="1a9e9-135">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
 <span data-ttu-id="1a9e9-136">**搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-136">**Search Property List**</span></span>  
 <span data-ttu-id="1a9e9-137">当前与全文索引关联的搜索属性列表（如果有）。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-137">The search property list that is currently associated with the full-text index, if any.</span></span> <span data-ttu-id="1a9e9-138">搜索属性列表指定一组文档属性，在填充关联的全文索引时这些文档属性包括在其中。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-138">A search property list specifies a set of document properties that are included in the associated full-text index when it is populated.</span></span> <span data-ttu-id="1a9e9-139">有关详细信息，请参阅 [使用搜索属性列表搜索文档属性](../relational-databases/search/search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-139">For more information, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="1a9e9-140">**\<Off>** 指示当前没有与索引关联的搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-140">**\<Off>** indicates that there is currently no search property list associated with the index.</span></span> <span data-ttu-id="1a9e9-141">您可以通过从列表中选择，从索引中删除当前搜索属性列表 **\<Off>** ，也可以从列表中选择不同的搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-141">You can remove the current search property list from the index by selecting **\<Off>** from the list, or you can select a different search property list from the list.</span></span> <span data-ttu-id="1a9e9-142">在此处只列出当前数据库中的搜索属性列表。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-142">Only search property lists in the current database are listed here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a9e9-143">您可以将给定的搜索属性列表与同一数据库中的多个全文索引相关联。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-143">You can associate a given search property list with more than one full-text index in the same database.</span></span>  
  
 <span data-ttu-id="1a9e9-144">**创建搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-144">**To create a search property list**</span></span>  
  
-   [<span data-ttu-id="1a9e9-145">使用搜索属性列表搜索文档属性</span><span class="sxs-lookup"><span data-stu-id="1a9e9-145">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 <span data-ttu-id="1a9e9-146">**表全文项计数**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-146">**Table Full-Text Item Count**</span></span>  
 <span data-ttu-id="1a9e9-147">指示成功执行了全文索引的行数。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-147">Indicates the number of rows that were full-text indexed successfully.</span></span>  
  
 <span data-ttu-id="1a9e9-148">此属性对应于由 OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] 函数返回的 `TableFulltextItemCount` 属性。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-148">This property corresponds to the `TableFulltextItemCount` property returned by the OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="1a9e9-149">**已处理的表全文文档数**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-149">**Table Full-Text Docs Processed**</span></span>  
 <span data-ttu-id="1a9e9-150">显示自从全文索引开始以来已处理的行数。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-150">Displays the number of rows that have been processed since the start of full-text indexing.</span></span> <span data-ttu-id="1a9e9-151">在为进行全文搜索而正在编制索引的表中，将一个行的所有列视为要编制索引的文档的一部分。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-151">In a table that is being indexed for full-text search, all the columns of one row are considered as part of one document to be indexed.</span></span> <span data-ttu-id="1a9e9-152">已删除的行不被计数。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-152">Deleted rows are not counted.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a9e9-153">0</span><span class="sxs-lookup"><span data-stu-id="1a9e9-153">0</span></span>|<span data-ttu-id="1a9e9-154">指示全文索引已完成，并且没有活动填充。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-154">Indicates that full-text indexing is completed and there is no active population.</span></span>|  
|<span data-ttu-id="1a9e9-155">> 0</span><span class="sxs-lookup"><span data-stu-id="1a9e9-155">> 0</span></span>|<span data-ttu-id="1a9e9-156">对于活动填充，指示自从执行任何以下操作以来由插入或更新操作所处理的文档数：填充、启用具有后台更新索引填充功能的更改跟踪（比如自动更改跟踪）、更改全文索引架构、重建全文目录、重新启动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的实例等等。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-156">For an active population, indicates the number of documents processed by insert or update operations since any of the following: a population, enabling of change tracking with background update index population (such as auto change tracking), changing the full-text index schema, rebuilding the full-text catalog, restarting the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and so forth.</span></span>|  
  
 <span data-ttu-id="1a9e9-157">**表全文挂起更改**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-157">**Table Full-Text Pending Changes**</span></span>  
 <span data-ttu-id="1a9e9-158">要处理的挂起更改跟踪项的数目。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-158">Number of pending change tracking entries to process.</span></span>  
  
 <span data-ttu-id="1a9e9-159">0 = 不启用更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-159">0 = change tracking is not enabled.</span></span>  
  
 <span data-ttu-id="1a9e9-160">NULL = 表没有全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-160">NULL = Table does not have a full-text index.</span></span>  
  
 <span data-ttu-id="1a9e9-161">**表全文失败计数**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-161">**Table Full-Text Fail Count**</span></span>  
 <span data-ttu-id="1a9e9-162">全文搜索未索引的行数。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-162">The number of rows that full-text search did not index.</span></span>  
  
 <span data-ttu-id="1a9e9-163">0 = 填充已完成。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-163">0 = The population has completed.</span></span>  
  
 <span data-ttu-id="1a9e9-164">\>0 = 以下项之一：</span><span class="sxs-lookup"><span data-stu-id="1a9e9-164">\>0 = One of the following:</span></span>  
  
-   <span data-ttu-id="1a9e9-165">自从完整、增量或手动的更改跟踪填充开始以来未索引的文档数。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-165">The number of documents that were not indexed since the start of full, incremental, or manual change tracking population.</span></span>  
  
-   <span data-ttu-id="1a9e9-166">对于有后台更新索引的更改跟踪，则是自从填充开始以来未索引的行数，或重新启动填充。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-166">For change tracking with background update index, the number of rows that were not indexed since the start of the population, or the restart of the population.</span></span> <span data-ttu-id="1a9e9-167">这可以由架构更改、目录重建、服务器重新启动等等导致。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-167">This could be caused by a schema change, rebuild of the catalog, server restart, and so on</span></span>  
  
 <span data-ttu-id="1a9e9-168">**全文索引已启用**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-168">**Full-Text Indexing Enabled**</span></span>  
 <span data-ttu-id="1a9e9-169">指定是否已启用全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-169">Specifies whether full-text indexing is enabled.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a9e9-170">**True**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-170">**True**</span></span>|<span data-ttu-id="1a9e9-171">已启用</span><span class="sxs-lookup"><span data-stu-id="1a9e9-171">Enabled</span></span>|  
|<span data-ttu-id="1a9e9-172">**False**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-172">**False**</span></span>|<span data-ttu-id="1a9e9-173">已禁用</span><span class="sxs-lookup"><span data-stu-id="1a9e9-173">Disabled</span></span>|  
  
 <span data-ttu-id="1a9e9-174">**更改跟踪**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-174">**Change Tracking**</span></span>  
 <span data-ttu-id="1a9e9-175">指定表是否启用了全文更改跟踪，如果启用，则是什么种类。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-175">Specifies whether the table has full-text change-tracking enabled, and if so, what kind.</span></span> <span data-ttu-id="1a9e9-176">全文更改跟踪用于记录已设置全文索引的表或索引视图中已修改的行。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-176">Full-text change tracking maintains a record of the rows that have been modified in a table or indexed view that has been set up for full-text indexing.</span></span> <span data-ttu-id="1a9e9-177">这些更改可以传播到全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-177">These changes can be propagated to the full-text index.</span></span>  
  
 <span data-ttu-id="1a9e9-178">**“更改跟踪”** 值如下：</span><span class="sxs-lookup"><span data-stu-id="1a9e9-178">The **Change Tracking** values are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a9e9-179">关闭</span><span class="sxs-lookup"><span data-stu-id="1a9e9-179">**Off**</span></span>|<span data-ttu-id="1a9e9-180">不以基础数据的更改来更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-180">The full-text index is not updated with changes to the underlying data.</span></span>|  
|<span data-ttu-id="1a9e9-181">手动</span><span class="sxs-lookup"><span data-stu-id="1a9e9-181">**Manual**</span></span>|<span data-ttu-id="1a9e9-182">基础数据发生更改时，不自动更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-182">The full-text index is not updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="1a9e9-183">但是，会维护基础数据的更改，并且可以使用 SQL Server 代理定期或手动将它们传播到</span><span class="sxs-lookup"><span data-stu-id="1a9e9-183">However, changes to the underlying data are maintained, and you can propagate them to the .</span></span> <span data-ttu-id="1a9e9-184">全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-184">full-text index either on a schedule using SQL Server Agent or manually.</span></span>|  
|<span data-ttu-id="1a9e9-185">**自动**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-185">**Automatic**</span></span>|<span data-ttu-id="1a9e9-186">当基表中的基础数据发生更改时，则自动更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-186">The full-text index is updated automatically as changes occur to the underlying data in the base table.</span></span>|  
  
 <span data-ttu-id="1a9e9-187">**重新填充索引**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-187">**Repopulate index**</span></span>  
 <span data-ttu-id="1a9e9-188">单击它可以在退出对话框后启动对全文索引的填充。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-188">Click to start a population on the full-text index on exiting the dialog box.</span></span> <span data-ttu-id="1a9e9-189">请选择以下填充类型之一：</span><span class="sxs-lookup"><span data-stu-id="1a9e9-189">Select one of the following types of population:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a9e9-190">**完整**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-190">**Full**</span></span>|<span data-ttu-id="1a9e9-191">在表的完整填充期间，为所有行生成索引条目。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-191">During a full population of a table, index entries are built for all the rows.</span></span>|  
|<span data-ttu-id="1a9e9-192">**式**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-192">**Incremental**</span></span>|<span data-ttu-id="1a9e9-193">增量填充在全文索引中更新上次填充的当时或之后添加、删除或修改的行。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-193">Incremental population updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="1a9e9-194">执行增量填充需要基表包含一个 `timestamp` 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-194">Performing an incremental population requires that the base table contain a column of the `timestamp` data type.</span></span>|  
|<span data-ttu-id="1a9e9-195">**更新**</span><span class="sxs-lookup"><span data-stu-id="1a9e9-195">**Update**</span></span>|<span data-ttu-id="1a9e9-196">一旦修改基表中的数据，将更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="1a9e9-196">The full-text index is updated whenever the data in the base table is modified.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a9e9-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1a9e9-197">See Also</span></span>  
 [<span data-ttu-id="1a9e9-198">全文搜索入门</span><span class="sxs-lookup"><span data-stu-id="1a9e9-198">Get Started with Full-Text Search</span></span>](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
