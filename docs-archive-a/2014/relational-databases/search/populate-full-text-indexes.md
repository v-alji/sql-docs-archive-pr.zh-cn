---
title: 填充全文索引 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- index populations [full-text search]
- incremental populations [full-text search]
- populations [full-text search]
- full-text search [SQL Server], populations
- crawls [full-text search]
- automatic full-text index updates
- change tracking-based populations [full-text search]
- manual updates [full-text search]
- manual populations [full-text search]
- auto populations [full-text search]
- full-text indexes [SQL Server], key column
- full populations [full-text search]
- full-text indexes [SQL Server], populations
ms.assetid: 76767b20-ef55-49ce-8dc4-e77cb8ff618a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9ab93a3514fa260c8c3836da85c767da3c3051a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589486"
---
# <a name="populate-full-text-indexes"></a><span data-ttu-id="35688-102">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="35688-102">Populate Full-Text Indexes</span></span>
  <span data-ttu-id="35688-103">创建和维护全文索引涉及使用称为“填充”（也称为“爬网”）的过程填充索引。</span><span class="sxs-lookup"><span data-stu-id="35688-103">Creating and maintaining a full-text index involves populating the index by using a process called a *population* (also known as a *crawl*).</span></span>  
  
##  <a name="types-of-population"></a><a name="types"></a><span data-ttu-id="35688-104">填充类型</span><span class="sxs-lookup"><span data-stu-id="35688-104">Types of Population</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="35688-105">支持以下填充类型：完全填充、基于更改跟踪的自动或手动填充和基于时间戳的增量填充。</span><span class="sxs-lookup"><span data-stu-id="35688-105">supports the following types of population: full population, change tracking-based automatic or manual population, and incremental timestamp-based population.</span></span>  
  
### <a name="full-population"></a><span data-ttu-id="35688-106">完全填充</span><span class="sxs-lookup"><span data-stu-id="35688-106">Full Population</span></span>  
 <span data-ttu-id="35688-107">在完全填充期间，为表或索引视图的所有行生成索引条目。</span><span class="sxs-lookup"><span data-stu-id="35688-107">During a full population, index entries are built for all the rows of a table or indexed view.</span></span> <span data-ttu-id="35688-108">全文索引的完全填充为基表或索引视图的所有行生成索引条目。</span><span class="sxs-lookup"><span data-stu-id="35688-108">A full population of a full-text index, builds index entries for all the rows of the base table or indexed view.</span></span>  
  
 <span data-ttu-id="35688-109">默认情况下，一旦创建新的全文索引， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 便会对其进行完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] populates a new full-text index fully as soon as it is created.</span></span> <span data-ttu-id="35688-110">但是，完全填充会占用相当多的资源。</span><span class="sxs-lookup"><span data-stu-id="35688-110">However, a full population can consume a significant amount of resources.</span></span> <span data-ttu-id="35688-111">因此，当在高峰期创建全文索引时，最佳做法通常是将完全填充推迟到非高峰时段，当全文索引的基表非常大时更应如此。</span><span class="sxs-lookup"><span data-stu-id="35688-111">Therefore, when creating a full-text index during peak periods, it is often a best practice to delay the full population until an off-peak time, particularly if the base table of an full-text index is large.</span></span> <span data-ttu-id="35688-112">不过，索引所属的全文目录在填充其所有全文索引之后才可使用。</span><span class="sxs-lookup"><span data-stu-id="35688-112">However, the full-text catalog to which the index belongs is not usable until all of its full-text indexes are populated.</span></span> <span data-ttu-id="35688-113">若要创建全文索引而不立即填充它，请在 CREATE FULLTEXT INDEX 语句中指定 CHANGE_TRACKING OFF, NO POPULATION 子句。</span><span class="sxs-lookup"><span data-stu-id="35688-113">To create a full-text index without populating it immediately, specify the CHANGE_TRACKING OFF, NO POPULATION clause in the CREATE FULLTEXT INDEX statement.</span></span> <span data-ttu-id="35688-114">如果您指定 CHANGE_TRACKING MANUAL，全文引擎将使用语句。</span><span class="sxs-lookup"><span data-stu-id="35688-114">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses statement.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="35688-115">将不填充新的全文索引，直到您使用 START 完全填充或开始增量填充子句来执行 ALTER 全文索引语句为止。</span><span class="sxs-lookup"><span data-stu-id="35688-115">will not populate the new full-text index until you execute an ALTER FULLTEXT INDEX statement using the START FULL POPULATION or START INCREMENTAL POPULATION clause.</span></span> <span data-ttu-id="35688-116">有关详细信息，请参阅本主题后面的示例“A.</span><span class="sxs-lookup"><span data-stu-id="35688-116">For more information, see examples "A.</span></span> <span data-ttu-id="35688-117">创建全文索引而不运行完全填充”和“B.</span><span class="sxs-lookup"><span data-stu-id="35688-117">Creating a full-text index without running a full population" and "B.</span></span> <span data-ttu-id="35688-118">对表运行完全填充”。</span><span class="sxs-lookup"><span data-stu-id="35688-118">Running a full population on table," later in this topic.</span></span>  
  

  
### <a name="change-tracking-based-population"></a><span data-ttu-id="35688-119">基于更改跟踪的填充</span><span class="sxs-lookup"><span data-stu-id="35688-119">Change Tracking-Based Population</span></span>  
 <span data-ttu-id="35688-120">或者，您可以在对全文索引进行初始完全填充之后使用更改跟踪对其进行维护。</span><span class="sxs-lookup"><span data-stu-id="35688-120">Optionally, you can use change tracking to maintain a full-text index after its initial full population.</span></span> <span data-ttu-id="35688-121">将出现与更改跟踪关联的较小开销，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 维护它用来跟踪自上次填充后对基表所做更改的表。</span><span class="sxs-lookup"><span data-stu-id="35688-121">There is a small overhead associated with change tracking because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a table in which it tracks changes to the base table since the last population.</span></span> <span data-ttu-id="35688-122">当使用更改跟踪时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 维护基表或索引视图中已通过更新、删除或插入进行过修改的行的记录。</span><span class="sxs-lookup"><span data-stu-id="35688-122">When change tracking is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a record of the rows in the base table or indexed view that have been modified by updates, deletes, or inserts.</span></span> <span data-ttu-id="35688-123">通过 WRITETEXT 和 UPDATETEXT 所做的数据更改不会反映到全文索引中，也不能使用更改跟踪方法拾取。</span><span class="sxs-lookup"><span data-stu-id="35688-123">Data changes through WRITETEXT and UPDATETEXT are not reflected in the full-text index, and are not picked up with change tracking.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35688-124">对于包含 `timestamp` 列的表，可以使用增量填充。</span><span class="sxs-lookup"><span data-stu-id="35688-124">For tables containing a `timestamp` column, you can use incremental populations.</span></span>  
  
 <span data-ttu-id="35688-125">如果在创建索引期间启用更改跟踪，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在新全文索引创建之后立即对其进行完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-125">When change tracking is enabled during index creation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fully populates the new full-text index immediately after it is created.</span></span> <span data-ttu-id="35688-126">其后，将跟踪更改并将更改传播到全文索引。</span><span class="sxs-lookup"><span data-stu-id="35688-126">Thereafter, changes are tracked and propagated to the full-text index.</span></span> <span data-ttu-id="35688-127">有两类更改跟踪：自动（CHANGE_TRACKING AUTO 选项）和手动（CHANGE_TRACKING MANUAL 选项）。</span><span class="sxs-lookup"><span data-stu-id="35688-127">There are two types of change tracking, automatic (CHANGE_TRACKING AUTO option) and manual (CHANGE_TRACKING MANUAL option).</span></span> <span data-ttu-id="35688-128">自动更改跟踪为默认行为。</span><span class="sxs-lookup"><span data-stu-id="35688-128">Automatic change tracking is the default behavior.</span></span>  
  
 <span data-ttu-id="35688-129">更改跟踪的类型确定全文索引的填充方式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="35688-129">The type of change tracking determines how the full-text index is populated, as follows:</span></span>  
  
-   <span data-ttu-id="35688-130">自动填充</span><span class="sxs-lookup"><span data-stu-id="35688-130">Automatic population</span></span>  
  
     <span data-ttu-id="35688-131">默认情况下，或者如果您指定 CHANGE_TRACKING AUTO，全文引擎将对全文索引使用自动填充。</span><span class="sxs-lookup"><span data-stu-id="35688-131">By default, or if you specify CHANGE_TRACKING AUTO, the Full-Text Engine uses automatic population on the full-text index.</span></span> <span data-ttu-id="35688-132">完成首次完全填充之后，当修改基表中的数据时将跟踪更改并自动传播跟踪的更改。</span><span class="sxs-lookup"><span data-stu-id="35688-132">After the initial full population completes, changes are tracked as data is modified in the base table, and the tracked changes are propagated automatically.</span></span> <span data-ttu-id="35688-133">不过，由于全文索引是在后台更新的，因此传播的更改可能不会立即反映到索引中。</span><span class="sxs-lookup"><span data-stu-id="35688-133">The full-text index is updated in the background, however, so propagated changes might not be reflected immediately in the index.</span></span>  
  
     <span data-ttu-id="35688-134">**设置使用自动填充的跟踪更改**</span><span class="sxs-lookup"><span data-stu-id="35688-134">**To set up tracking changes with automatic population**</span></span>  
  
    -   <span data-ttu-id="35688-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="35688-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING AUTO</span></span>  
  
    -   <span data-ttu-id="35688-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="35688-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING AUTO</span></span>  
  
     <span data-ttu-id="35688-137">有关详细信息，请参阅本主题后面的示例“E.</span><span class="sxs-lookup"><span data-stu-id="35688-137">For more information, see example "E.</span></span> <span data-ttu-id="35688-138">更改全文索引以使用自动更改跟踪”。</span><span class="sxs-lookup"><span data-stu-id="35688-138">Altering a full-text index to use automatic change tracking," later in this topic.</span></span>  
  
-   <span data-ttu-id="35688-139">手动填充</span><span class="sxs-lookup"><span data-stu-id="35688-139">Manual population</span></span>  
  
     <span data-ttu-id="35688-140">如果您指定 CHANGE_TRACKING MANUAL，全文引擎将对全文索引使用手动填充。</span><span class="sxs-lookup"><span data-stu-id="35688-140">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses manual population on the full-text index.</span></span> <span data-ttu-id="35688-141">完成首次完全填充之后，当修改基表中的数据时将跟踪更改。</span><span class="sxs-lookup"><span data-stu-id="35688-141">After the initial full population completes, changes are tracked as data is modified in the base table.</span></span> <span data-ttu-id="35688-142">但是，这些更改不会传播到全文索引，直至你执行 ALTER FULLTEXT INDEX …START UPDATE POPULATION 语句手动应用更改。</span><span class="sxs-lookup"><span data-stu-id="35688-142">However, they are not propagated to the full-text index until you execute an ALTER FULLTEXT INDEX ... START UPDATE POPULATION statement.</span></span> <span data-ttu-id="35688-143">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来定期调用此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="35688-143">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to call this [!INCLUDE[tsql](../../includes/tsql-md.md)] statement periodically.</span></span>  
  
     <span data-ttu-id="35688-144">**启动使用手动填充的跟踪更改**</span><span class="sxs-lookup"><span data-stu-id="35688-144">**To start tracking changes with manual population**</span></span>  
  
    -   <span data-ttu-id="35688-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="35688-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING MANUAL</span></span>  
  
    -   <span data-ttu-id="35688-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="35688-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING MANUAL</span></span>  
  
     <span data-ttu-id="35688-147">有关详细信息，请参阅本主题后面的示例“C.</span><span class="sxs-lookup"><span data-stu-id="35688-147">For more information, see examples "C.</span></span> <span data-ttu-id="35688-148">使用手动更改跟踪创建全文索引”和“D.</span><span class="sxs-lookup"><span data-stu-id="35688-148">Creating a full-text index with manual change tracking" and "D.</span></span> <span data-ttu-id="35688-149">运行手动填充”。</span><span class="sxs-lookup"><span data-stu-id="35688-149">Running a manual population," later in this topic.</span></span>  
  
 <span data-ttu-id="35688-150">**关闭更改跟踪**</span><span class="sxs-lookup"><span data-stu-id="35688-150">**To turn off change tracking**</span></span>  
  
-   <span data-ttu-id="35688-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="35688-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING OFF</span></span>  
  
-   <span data-ttu-id="35688-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="35688-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING OFF</span></span>  
  

  
### <a name="incremental-timestamp-based-population"></a><span data-ttu-id="35688-153">基于时间戳的增量填充</span><span class="sxs-lookup"><span data-stu-id="35688-153">Incremental Timestamp-Based Population</span></span>  
 <span data-ttu-id="35688-154">增量填充是手动填充全文索引的一种替代机制。</span><span class="sxs-lookup"><span data-stu-id="35688-154">An incremental population is an alternative mechanism for manually populating a full-text index.</span></span> <span data-ttu-id="35688-155">您可以对 CHANGE_TRACKING 设置为 MANUAL 或 OFF 的全文索引运行增量填充。</span><span class="sxs-lookup"><span data-stu-id="35688-155">You can run an incremental population for a full-text index that has CHANGE_TRACKING set to MANUAL or OFF.</span></span> <span data-ttu-id="35688-156">如果全文索引的第一个填充是增量填充，它将对所有行编制索引并使其等效于完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-156">If the first population on a full-text index is an incremental population, it indexes all rows, making it equivalent to a full population.</span></span>  
  
 <span data-ttu-id="35688-157">增量填充要求索引表必须具有 `timestamp` 数据类型的列。</span><span class="sxs-lookup"><span data-stu-id="35688-157">The requirement for incremental population is that the indexed table must have a column of the `timestamp` data type.</span></span> <span data-ttu-id="35688-158">如果 `timestamp` 列不存在，则无法执行增量填充。</span><span class="sxs-lookup"><span data-stu-id="35688-158">If a `timestamp` column does not exist, incremental population cannot be performed.</span></span> <span data-ttu-id="35688-159">对不含 `timestamp` 列的表请求增量填充会导致完全填充操作。</span><span class="sxs-lookup"><span data-stu-id="35688-159">A request for incremental population on a table without a `timestamp` column results in a full population operation.</span></span> <span data-ttu-id="35688-160">另外，如果影响表全文索引的任意元数据自上次填充以来发生了变化，则增量填充请求将作为完全填充来执行。</span><span class="sxs-lookup"><span data-stu-id="35688-160">Also, if any metadata that affects the full-text index for the table has changed since the last population, incremental population requests are implemented as full populations.</span></span> <span data-ttu-id="35688-161">这包括更改任何列、索引或全文索引定义所引起的元数据更改。</span><span class="sxs-lookup"><span data-stu-id="35688-161">This includes metadata changes caused by altering any column, index, or full-text index definitions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="35688-162">使用 `timestamp` 列标识自上次填充后发生更改的行。</span><span class="sxs-lookup"><span data-stu-id="35688-162">uses the `timestamp` column to identify rows that have changed since the last population.</span></span> <span data-ttu-id="35688-163">然后，增量填充在全文索引中更新上次填充的当时或之后添加、删除或修改的行。</span><span class="sxs-lookup"><span data-stu-id="35688-163">The incremental population then updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="35688-164">如果对表进行大量插入操作，则使用增量填充会较使用手动填充有效。</span><span class="sxs-lookup"><span data-stu-id="35688-164">If a table experiences a high volume of inserts, using incremental population can be more efficient that using manual population.</span></span>  
  
 <span data-ttu-id="35688-165">在填充结束时，全文引擎将记录新的 `timestamp` 值。</span><span class="sxs-lookup"><span data-stu-id="35688-165">At the end of a population, the Full-Text Engine records a new `timestamp` value.</span></span> <span data-ttu-id="35688-166">该值是 SQL 收集器遇到的最大 `timestamp` 值。</span><span class="sxs-lookup"><span data-stu-id="35688-166">This value is the largest `timestamp` value that SQL Gatherer has encountered.</span></span> <span data-ttu-id="35688-167">以后再启动增量填充时，将会使用此值。</span><span class="sxs-lookup"><span data-stu-id="35688-167">This value will be used when a subsequent incremental population starts.</span></span>  
  
 <span data-ttu-id="35688-168">若要运行增量填充，请执行使用 START INCREMENTAL POPULATION 子句的 ALTER FULLTEXT INDEX 语句。</span><span class="sxs-lookup"><span data-stu-id="35688-168">To run an incremental population, execute an ALTER FULLTEXT INDEX statement using the START INCREMENTAL POPULATION clause.</span></span>  
  

  
##  <a name="examples-of-populating-full-text-indexes"></a><a name="examples"></a><span data-ttu-id="35688-169">填充全文索引的示例</span><span class="sxs-lookup"><span data-stu-id="35688-169">Examples of Populating Full-Text Indexes</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35688-170">本节中的示例使用 `Production.Document` 示例数据库的 `HumanResources.JobCandidate` 或 `AdventureWorks` 表。</span><span class="sxs-lookup"><span data-stu-id="35688-170">The examples in this section use the `Production.Document` or `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
### <a name="a-creating-a-full-text-index-without-running-a-full-population"></a><span data-ttu-id="35688-171">A.</span><span class="sxs-lookup"><span data-stu-id="35688-171">A.</span></span> <span data-ttu-id="35688-172">创建全文索引而不运行完全填充</span><span class="sxs-lookup"><span data-stu-id="35688-172">Creating a full-text index without running a full population</span></span>  
 <span data-ttu-id="35688-173">以下示例对 `Production.Document` 示例数据库的 `AdventureWorks` 表创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="35688-173">The following example creates a full-text index on the `Production.Document` table of the `AdventureWorks` sample database.</span></span> <span data-ttu-id="35688-174">该示例使用 WITH CHANGE_TRACKING OFF, NO POPULATION 来延迟初次完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-174">This example uses WITH CHANGE_TRACKING OFF, NO POPULATION to delay the initial full population.</span></span>  
  
```  
CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
CREATE FULLTEXT CATALOG AW_Production_FTCat;  
CREATE FULLTEXT INDEX ON Production.Document  
(  
    Document                         --Full-text index column name   
        TYPE COLUMN FileExtension    --Name of column that contains file type information  
        Language 1033                 --1033 is LCID for the English language  
)  
    KEY INDEX ui_ukDoc  
    ON AW_Production_FTCat  
    WITH CHANGE_TRACKING OFF, NO POPULATION;  
GO  
  
```  
  
### <a name="b-running-a-full-population-on-table"></a><span data-ttu-id="35688-175">B.</span><span class="sxs-lookup"><span data-stu-id="35688-175">B.</span></span> <span data-ttu-id="35688-176">对表运行完全填充</span><span class="sxs-lookup"><span data-stu-id="35688-176">Running a full population on table</span></span>  
 <span data-ttu-id="35688-177">以下示例对 `Production.Document` 示例数据库的 `AdventureWorks` 表运行完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-177">The following example runs a full population on the `Production.Document` table of the `AdventureWorks` sample database.</span></span>  
  
```  
ALTER FULLTEXT INDEX ON Production.Document  
   START FULL POPULATION;  
```  
  
### <a name="c-creating-a-full-text-index-with-manual-change-tracking"></a><span data-ttu-id="35688-178">C.</span><span class="sxs-lookup"><span data-stu-id="35688-178">C.</span></span> <span data-ttu-id="35688-179">使用手动更改跟踪创建全文索引</span><span class="sxs-lookup"><span data-stu-id="35688-179">Creating a full-text index with manual change tracking</span></span>  
 <span data-ttu-id="35688-180">以下示例对 `HumanResources.JobCandidate` 示例数据库的 `AdventureWorks` 表创建全文索引，该全文索引将使用具有手动填充的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="35688-180">The following example creates a full-text index that will use change tracking with manual population on the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH CHANGE_TRACKING=MANUAL;  
GO  
```  
  
### <a name="d-running-a-manual-population"></a><span data-ttu-id="35688-181">D.</span><span class="sxs-lookup"><span data-stu-id="35688-181">D.</span></span> <span data-ttu-id="35688-182">运行手动填充</span><span class="sxs-lookup"><span data-stu-id="35688-182">Running a manual population</span></span>  
 <span data-ttu-id="35688-183">以下示例对 `HumanResources.JobCandidate` 示例数据库的 `AdventureWorks` 表的更改跟踪全文索引运行手动填充。</span><span class="sxs-lookup"><span data-stu-id="35688-183">The following example runs a manual population on the change-tracked full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate START UPDATE POPULATION;  
GO  
```  
  
### <a name="e-altering-a-full-text-index-to-use-automatic-change-tracking"></a><span data-ttu-id="35688-184">E.</span><span class="sxs-lookup"><span data-stu-id="35688-184">E.</span></span> <span data-ttu-id="35688-185">更改全文索引以使用自动更改跟踪</span><span class="sxs-lookup"><span data-stu-id="35688-185">Altering a full-text index to use automatic change tracking</span></span>  
 <span data-ttu-id="35688-186">以下示例更改 `HumanResources.JobCandidate` 示例数据库的 `AdventureWorks` 表的全文索引以使用自动填充的更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="35688-186">The following example changes the full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database to use change tracking with automatic population.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate SET CHANGE_TRACKING AUTO;  
GO   
```  
  

  
##  <a name="creating-or-changing-a-schedule-for-incremental-population"></a><a name="create"></a><span data-ttu-id="35688-187">创建或更改增量填充计划</span><span class="sxs-lookup"><span data-stu-id="35688-187">Creating or Changing a Schedule for Incremental Population</span></span>  
  
#### <a name="to-create-or-change-a-schedule-for-incremental-population-in-management-studio"></a><span data-ttu-id="35688-188">在 Management Studio 中创建或更改增量填充计划</span><span class="sxs-lookup"><span data-stu-id="35688-188">To create or change a schedule for incremental population in Management Studio</span></span>  
  
1.  <span data-ttu-id="35688-189">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="35688-189">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="35688-190">展开“数据库”，然后展开包含全文索引的数据库。</span><span class="sxs-lookup"><span data-stu-id="35688-190">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="35688-191">展开 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="35688-191">Expand **Tables**.</span></span>  
  
 <span data-ttu-id="35688-192">右键单击对其定义了全文索引的表，选择“全文索引”，然后在“全文索引”上下文菜单中单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="35688-192">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="35688-193">此时将打开“全文索引属性”对话框。</span><span class="sxs-lookup"><span data-stu-id="35688-193">This opens the **Full-text index Properties** dialog box.</span></span>  
  
1.  <span data-ttu-id="35688-194">在 "**选择页**" 窗格中，选择 "计划"。</span><span class="sxs-lookup"><span data-stu-id="35688-194">In the **Select a page** pane, select Schedules.</span></span>  
  
     <span data-ttu-id="35688-195">使用此页可以创建或管理 SQL Server 代理作业的计划，该作业用于启动对全文索引基表或索引视图的表增量填充。</span><span class="sxs-lookup"><span data-stu-id="35688-195">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population on the base table or indexed view of the full-text index.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="35688-196">如果基表或视图不包含 `timestamp` 数据类型的列，则执行完全填充。</span><span class="sxs-lookup"><span data-stu-id="35688-196">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
     <span data-ttu-id="35688-197">选项如下：</span><span class="sxs-lookup"><span data-stu-id="35688-197">The options are as follows:</span></span>  
  
    -   <span data-ttu-id="35688-198">若要**创建**新计划，请单击“新建”。</span><span class="sxs-lookup"><span data-stu-id="35688-198">To create a new schedule, click **New**.</span></span>  
  
         <span data-ttu-id="35688-199">此时将打开“新建全文索引表计划”对话框，你可以在此对话框中创建计划。</span><span class="sxs-lookup"><span data-stu-id="35688-199">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can create a schedule.</span></span> <span data-ttu-id="35688-200">若要保存计划，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="35688-200">To save the schedule, click **OK**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="35688-201">在退出“全文索引属性”对话框之后，SQL Server 代理作业（对 *database_name*.*table_name* 启动表增量填充）将与新计划相关联。</span><span class="sxs-lookup"><span data-stu-id="35688-201">A SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*) is associated with a new schedule after you exit the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="35688-202">如果您针对该全文索引创建多个计划，则这些计划都将使用同一作业。</span><span class="sxs-lookup"><span data-stu-id="35688-202">If you create multiple schedules for the full-text index, they all use the same job.</span></span>  
  
    -   <span data-ttu-id="35688-203">若要更改某个计划，请选择该计划并单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="35688-203">To change a schedule, select it and click **Edit**.</span></span>  
  
         <span data-ttu-id="35688-204">此时将打开“新建全文索引表计划” 对话框，你可以在此对话框中修改计划。</span><span class="sxs-lookup"><span data-stu-id="35688-204">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can modify the schedule.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="35688-205">有关修改作业的信息，请参阅 [修改作业](../../ssms/agent/modify-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="35688-205">For information about modifying a job, see [Modify a Job](../../ssms/agent/modify-a-job.md).</span></span>  
  
    -   <span data-ttu-id="35688-206">若要删除某个计划，请选择该计划并单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="35688-206">To remove a schedule, select it and click **Delete**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  

  
##  <a name="troubleshooting-errors-in-a-full-text-population-crawl"></a><a name="crawl"></a><span data-ttu-id="35688-207">排除全文填充 (爬网中的错误) </span><span class="sxs-lookup"><span data-stu-id="35688-207">Troubleshooting Errors in a Full-Text Population (Crawl)</span></span>  
 <span data-ttu-id="35688-208">如果在爬网期间发生了错误，全文搜索的爬网日志功能会创建并维护一个爬网日志，该日志是一个纯文本文件。</span><span class="sxs-lookup"><span data-stu-id="35688-208">When an error occurs during a crawl, the Full-Text Search crawl logging facility creates and maintains a crawl log, which is a plain text file.</span></span> <span data-ttu-id="35688-209">每个爬网日志都对应于某一个全文目录。</span><span class="sxs-lookup"><span data-stu-id="35688-209">Each crawl log corresponds to a particular full-text catalog.</span></span> <span data-ttu-id="35688-210">默认情况下，给定实例（此处为第一个实例）的爬网日志位于 %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="35688-210">By default crawl logs for a given instance, in this case, the first instance, are located in %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG folder.</span></span> <span data-ttu-id="35688-211">爬网日志文件遵循以下命名方案：</span><span class="sxs-lookup"><span data-stu-id="35688-211">The crawl log file follows the following naming scheme:</span></span>  
  
 <span data-ttu-id="35688-212">SQLFT0000500008.2 \<DatabaseID> \<FullTextCatalogID> 。日志 [ \<n> ]</span><span class="sxs-lookup"><span data-stu-id="35688-212">SQLFT\<DatabaseID>\<FullTextCatalogID>.LOG[\<n>]</span></span>  
  
 <`DatabaseID`>  
 <span data-ttu-id="35688-213">数据库的 ID。</span><span class="sxs-lookup"><span data-stu-id="35688-213">The ID of a database.</span></span><span data-ttu-id="35688-214"> <`dbid`> 是一个带有前导零的五位数字。</span><span class="sxs-lookup"><span data-stu-id="35688-214"> <`dbid`> is a five digit number with leading zeros.</span></span>  
  
 <`FullTextCatalogID`>  
 <span data-ttu-id="35688-215">全文目录 ID。</span><span class="sxs-lookup"><span data-stu-id="35688-215">Full-text catalog ID.</span></span><span data-ttu-id="35688-216"> <`catid`> 是一个带有前导零的五位数字。</span><span class="sxs-lookup"><span data-stu-id="35688-216"> <`catid`> is a five digit number with leading zeros.</span></span>  
  
 <`n`>  
 <span data-ttu-id="35688-217">是一个整数，指示同一全文目录现有的一个或多个爬网日志。</span><span class="sxs-lookup"><span data-stu-id="35688-217">Is an integer that indicates one or more crawl logs of the same full-text catalog exist.</span></span>  
  
 <span data-ttu-id="35688-218">例如，SQLFT0000500008.2 是一个数据库 ID 为 5、全文目录 ID 为 8 的数据库爬网日志文件。</span><span class="sxs-lookup"><span data-stu-id="35688-218">For example, SQLFT0000500008.2 is the crawl log file for a database with database ID = 5, and full-text catalog ID = 8.</span></span> <span data-ttu-id="35688-219">文件名结尾的 2 指示此数据库/目录对具有两个爬网日志文件。</span><span class="sxs-lookup"><span data-stu-id="35688-219">The 2 at the end of the file name indicates that there are two crawl log files for this database/catalog pair.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="35688-220">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35688-220">See Also</span></span>  
 <span data-ttu-id="35688-221">[sys.dm_fts_index_population (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="35688-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span></span>  
 <span data-ttu-id="35688-222">[全文搜索入门](get-started-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="35688-222">[Get Started with Full-Text Search](get-started-with-full-text-search.md) </span></span>  
 <span data-ttu-id="35688-223">[创建和管理全文索引](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="35688-223">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="35688-224">[CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="35688-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="35688-225">ALTER FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="35688-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
