---
title: 对表和列启用语义搜索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], enabling
ms.assetid: 895d220c-6749-4954-9dd3-2ea4c6a321ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f11ba654f7cc34f521990e8c420d41885d3c55b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690480"
---
# <a name="enable-semantic-search-on-tables-and-columns"></a><span data-ttu-id="6ba84-102">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="6ba84-102">Enable Semantic Search on Tables and Columns</span></span>
  <span data-ttu-id="6ba84-103">介绍如何启用或禁用包含文档或文本的选定列上的统计语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-103">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 <span data-ttu-id="6ba84-104">统计语义搜索使用全文搜索创建的索引并创建其他索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-104">Statistical Semantic Search uses the indexes that are created by Full-Text Search, and creates additional indexes.</span></span> <span data-ttu-id="6ba84-105">作为全文搜索上的此依赖关系的结果，您可在定义新的全文索引或更改现有全文索引时创建一个新的语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-105">As a result of this dependency on full-text search, you create a new semantic index when you define a new full-text index, or when you alter an existing full-text index.</span></span> <span data-ttu-id="6ba84-106">可以按本主题中所述使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的全文索引向导和其他对话框创建新的语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-106">You can create a new semantic index by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, or by using the Full-Text Indexing Wizard and other dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as described in this topic.</span></span>  
  
##  <a name="creating-a-semantic-index"></a><a name="BasicEnabling"></a><span data-ttu-id="6ba84-107">创建语义索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-107">Creating a Semantic Index</span></span>  
  
###  <a name="requirements-and-restrictions-for-creating-a-semantic-index"></a><a name="reqenable"></a><span data-ttu-id="6ba84-108">创建语义索引的要求和限制</span><span class="sxs-lookup"><span data-stu-id="6ba84-108">Requirements and Restrictions for Creating a Semantic Index</span></span>  
  
-   <span data-ttu-id="6ba84-109">可以对任何支持全文索引的数据库对象创建索引，包括表和索引视图。</span><span class="sxs-lookup"><span data-stu-id="6ba84-109">You can create an index on any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="6ba84-110">在您可以启用特定列的语义索引之前，必须满足下列先决条件：</span><span class="sxs-lookup"><span data-stu-id="6ba84-110">Before you can enable semantic indexing for specific columns, the following prerequisites must exist:</span></span>  
  
    -   <span data-ttu-id="6ba84-111">数据库必须具有全文目录。</span><span class="sxs-lookup"><span data-stu-id="6ba84-111">A full-text catalog must exist for the database.</span></span>  
  
    -   <span data-ttu-id="6ba84-112">表必须具有全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-112">The table must have a full-text index.</span></span>  
  
    -   <span data-ttu-id="6ba84-113">选定列必须参与全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-113">The selected columns must participate in the full-text index.</span></span>  
  
     <span data-ttu-id="6ba84-114">您可以同时创建并启用所有这些要求。</span><span class="sxs-lookup"><span data-stu-id="6ba84-114">You can create and enable all these requirements at the same time.</span></span>  
  
-   <span data-ttu-id="6ba84-115">可以对具有任何支持全文索引的数据类型的列创建语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-115">You can create a semantic index on columns that have any of the data types that are supported for full-text indexing.</span></span> <span data-ttu-id="6ba84-116">有关详细信息，请参阅 [创建和管理全文索引](create-and-manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-116">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
-   <span data-ttu-id="6ba84-117">您可为 `varbinary(max)` 列指定支持全文索引的任何文档类型。</span><span class="sxs-lookup"><span data-stu-id="6ba84-117">You can specify any document type that is supported for full-text indexing for `varbinary(max)` columns.</span></span> <span data-ttu-id="6ba84-118">有关详细信息，请参阅本主题中的 [如何确定可对哪些文档类型编制索引](#doctypes) 。</span><span class="sxs-lookup"><span data-stu-id="6ba84-118">For more information, see [How To: Determine Which Document Types Can Be Indexed](#doctypes) in this topic.</span></span>  
  
-   <span data-ttu-id="6ba84-119">语义索引为你选择的列创建两种类型的索引：关键短语索引和文档相似性索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-119">Semantic indexing creates two types of indexes for the columns that you select - an index of key phrases, and an index of document similarity.</span></span> <span data-ttu-id="6ba84-120">启用语义索引时，您无法只选择其中一种索引类型。</span><span class="sxs-lookup"><span data-stu-id="6ba84-120">You cannot select only one type of index or the other when you enable semantic indexing.</span></span> <span data-ttu-id="6ba84-121">但是，您可以单独查询这两种索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-121">However you can query these two indexes independently.</span></span> <span data-ttu-id="6ba84-122">有关详细信息，请参阅 [使用语义搜索在文档中查找关键短语](find-key-phrases-in-documents-with-semantic-search.md) 和 [使用语义搜索查找相似和相关文档](find-similar-and-related-documents-with-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-122">For more information, see [Find Key Phrases in Documents with Semantic Search](find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="6ba84-123">如果未显式指定语义索引的 LCID，则仅将主要语言及其关联的语言统计信息用于语义索引编制。</span><span class="sxs-lookup"><span data-stu-id="6ba84-123">If you do not explicitly specify an LCID for a semantic index, then only the primary language and its associated language statistics are used for semantic indexing.</span></span>  
  
-   <span data-ttu-id="6ba84-124">如果为缺少语言模型的列指定语言，创建索引将失败并返回错误消息。</span><span class="sxs-lookup"><span data-stu-id="6ba84-124">If you specify a language for a column for which the language model is not available, the creation of the index fails and returns an error message.</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-no-full-text-index"></a><a name="HowToEnableCreate"></a><span data-ttu-id="6ba84-125">如何：在没有全文索引时创建语义索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-125">How To: Create a Semantic Index When There Is No Full-Text Index</span></span>  
 <span data-ttu-id="6ba84-126">使用 **CREATE FULLTEXT INDEX** 语句创建新的全文索引时，可以通过指定关键字 **STATISTICAL_SEMANTICS** 作为列定义的一部分在列级别启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-126">When you create a new full-text index with the **CREATE FULLTEXT INDEX** statement, you can enable semantic indexing at the column level by specifying the keyword **STATISTICAL_SEMANTICS** as part of the column definition.</span></span> <span data-ttu-id="6ba84-127">还可以在使用全文索引向导创建新的全文索引时启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-127">You can also enable semantic indexing when you use the Full-Text Indexing Wizard to create a new full-text index.</span></span>  
  
 <span data-ttu-id="6ba84-128">**使用 Transact-SQL 创建新的语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-128">**Create a new semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="6ba84-129">为要创建语义索引的每个列调用 **CREATE FULLTEXT INDEX** 语句并指定 **STATISTICAL_SEMANTICS**。</span><span class="sxs-lookup"><span data-stu-id="6ba84-129">Call the **CREATE FULLTEXT INDEX** statement and specify **STATISTICAL_SEMANTICS** for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="6ba84-130">有关此语句的所有选项的详细信息，请参阅 [CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-130">For more information about all the options for this statement, see [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="6ba84-131">**示例 1：创建一个唯一索引、全文索引和语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-131">**Example 1: Create a unique index, full-text index, and semantic index**</span></span>  
  
 <span data-ttu-id="6ba84-132">以下示例创建一个默认全文目录 **ft**.。然后，该示例对 AdventureWorks2012 示例数据库的 **HumanResources.JobCandidate** 表的 **JobCandidateID** 列创建一个唯一索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-132">The following example creates a default full-text catalog, **ft**. The example then creates a unique index on the **JobCandidateID** column of the **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="6ba84-133">需要将此唯一索引用作全文索引的键列。</span><span class="sxs-lookup"><span data-stu-id="6ba84-133">This unique index is required as the key column for a full-text index.</span></span> <span data-ttu-id="6ba84-134">然后，该示例在 **Resume** 列上创建一个全文索引和语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-134">The example then creates a full-text index and a semantic index on the **Resume** column.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG ft AS DEFAULT  
GO  
  
CREATE UNIQUE INDEX ui_ukJobCand  
    ON HumanResources.JobCandidate(JobCandidateID)  
GO  
  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate  
    (Resume  
        Language 1033  
        Statistical_Semantics  
    )   
    KEY INDEX JobCandidateID   
    WITH STOPLIST = SYSTEM  
GO  
```  
  
 <span data-ttu-id="6ba84-135">**示例 2：对具有延迟索引填充的几个列创建一个全文索引和语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-135">**Example 2: Create a full-text and semantic index on several columns with delayed index population**</span></span>  
  
 <span data-ttu-id="6ba84-136">以下示例在 AdventureWorks2012 示例数据库中创建一个全文目录 **documents_catalog**。</span><span class="sxs-lookup"><span data-stu-id="6ba84-136">The following example creates a full-text catalog, **documents_catalog**, in the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="6ba84-137">然后，该示例创建一个使用该新目录的全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-137">The example then creates a full-text index that uses this new catalog.</span></span> <span data-ttu-id="6ba84-138">全文索引针对 **Production.Document**表的 **Title**、 **DocumentSummary** 和 **Document** 列创建，而语义索引仅针对 **Document** 列创建。</span><span class="sxs-lookup"><span data-stu-id="6ba84-138">The full-text index is created on the **Title**, **DocumentSummary**, and **Document** columns of the **Production.Document** table, while the semantic index is only created on the **Document** column.</span></span> <span data-ttu-id="6ba84-139">此全文索引使用新创建的全文目录和现有的唯一键索引 **PK_Document_DocumentID**。</span><span class="sxs-lookup"><span data-stu-id="6ba84-139">This full-text index uses the newly-created full-text catalog and an existing unique key index, **PK_Document_DocumentID**.</span></span> <span data-ttu-id="6ba84-140">根据建议，此索引键在整数列 **DocumentID**上创建。</span><span class="sxs-lookup"><span data-stu-id="6ba84-140">As recommended, this index key is created on an integer column, **DocumentID**.</span></span> <span data-ttu-id="6ba84-141">该示例指定英语的 LCID 1033，这是列中数据的语言。</span><span class="sxs-lookup"><span data-stu-id="6ba84-141">The example specifies the LCID for English, 1033, which is the language of the data in the columns.</span></span>  
  
 <span data-ttu-id="6ba84-142">该示例还指定关闭更改跟踪并且不进行填充。</span><span class="sxs-lookup"><span data-stu-id="6ba84-142">This example also specifies that change tracking is off with no population.</span></span> <span data-ttu-id="6ba84-143">随后，在非峰值时间，该示例使用 **ALTER FULLTEXT INDEX** 语句对新索引开始进行完全填充，并启用自动更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="6ba84-143">Later, during off-peak hours, the example uses an **ALTER FULLTEXT INDEX** statement to start a full population on the new index and enable automatic change tracking.</span></span>  
  
```sql  
CREATE FULLTEXT CATALOG documents_catalog  
GO  
  
CREATE FULLTEXT INDEX ON Production.Document  
    (   
    Title  
        Language 1033,   
    DocumentSummary  
        Language 1033,   
    Document   
        TYPE COLUMN FileExtension  
        Language 1033  
        Statistical_Semantics  
    )  
    KEY INDEX PK_Document_DocumentID  
        ON documents_catalog  
        WITH CHANGE_TRACKING OFF, NO POPULATION  
GO  
```  
  
 <span data-ttu-id="6ba84-144">随后，在非峰值时间，填充索引：</span><span class="sxs-lookup"><span data-stu-id="6ba84-144">Later, at an off-peak time, the index is populated:</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO  
GO  
```  
  
 <span data-ttu-id="6ba84-145">**使用 SQL Server Management Studio 创建新的语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-145">**Create a new semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="6ba84-146">运行全文索引向导并在“选择表列” 页为每个要创建语义索引的列启用“统计语义” 。</span><span class="sxs-lookup"><span data-stu-id="6ba84-146">Run the Full-Text Indexing Wizard and enable **Statistical Semantics** on the **Select Table Columns** page for each column on which you want to create a semantic index.</span></span> <span data-ttu-id="6ba84-147">有关详细信息，包括有关如何启动全文索引向导的信息，请参阅 [使用全文索引向导](use-the-full-text-indexing-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-147">For more information, including information about how to start the Full-Text Indexing Wizard, see [Use the Full-Text Indexing Wizard](use-the-full-text-indexing-wizard.md).</span></span>  
  
###  <a name="how-to-create-a-semantic-index-when-there-is-an-existing-full-text-index"></a><a name="HowToEnableAlter"></a><span data-ttu-id="6ba84-148">如何：在存在现有全文索引时创建语义索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-148">How To: Create a Semantic Index When There Is an Existing Full-Text Index</span></span>  
 <span data-ttu-id="6ba84-149">在使用 **ALTER FULLTEXT INDEX** 语句更改现有全文索引时，可以添加语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-149">You can add semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="6ba84-150">您还可在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用各种对话框添加语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-150">You can also add semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6ba84-151">**使用 Transact-SQL 添加语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-151">**Add a semantic index by using Transact-SQL**</span></span>  
 <span data-ttu-id="6ba84-152">为每个要添加语义索引的列使用以下所述的选项调用 **ALTER FULLTEXT INDEX** 语句。</span><span class="sxs-lookup"><span data-stu-id="6ba84-152">Call the **ALTER FULLTEXT INDEX** statement with the options described below for each column on which you want to add a semantic index.</span></span> <span data-ttu-id="6ba84-153">有关此语句的所有选项的详细信息，请参阅 [ ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-153">For more information about all the options for this statement, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="6ba84-154">除非你特别指定，否则在调用 **ALTER** 后，将重新填充全文索引和语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-154">Both full-text and semantic indexes are repopulated after a call to **ALTER**, unless you specify otherwise.</span></span>  
  
-   <span data-ttu-id="6ba84-155">若要仅将全文索引添加到列，请使用 **ADD** 语法。</span><span class="sxs-lookup"><span data-stu-id="6ba84-155">To add full-text indexing only to a column, use the **ADD** syntax.</span></span>  
  
-   <span data-ttu-id="6ba84-156">若要同时将全文索引和语义索引添加到列，请使用带 **STATISTICAL_SEMANTICS** 选项的 **ADD** 语法。</span><span class="sxs-lookup"><span data-stu-id="6ba84-156">To add both full-text and semantic indexing to a column, use the **ADD** syntax with the **STATISTICAL_SEMANTICS** option.</span></span>  
  
-   <span data-ttu-id="6ba84-157">若要将语义索引添加到已启用全文索引的列，请使用 **ADD STATISTICAL_SEMANTICS** 选项。</span><span class="sxs-lookup"><span data-stu-id="6ba84-157">To add semantic indexing to a column that is already enabled for full-text indexing, use the **ADD STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="6ba84-158">在单个 **ALTER** 语句中只能将语义索引添加到一个列。</span><span class="sxs-lookup"><span data-stu-id="6ba84-158">You can only add semantic indexing to one column in a single **ALTER** statement.</span></span>  
  
 <span data-ttu-id="6ba84-159">**示例：将语义索引添加到已有全文索引的列**</span><span class="sxs-lookup"><span data-stu-id="6ba84-159">**Example: Add semantic indexing to a column that already has full-text indexing**</span></span>  
  
 <span data-ttu-id="6ba84-160">以下示例更改 AdventureWorks2012 示例数据库的 **Production.Document** 表的现有全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-160">The following example alters an existing full-text index on **Production.Document** table in AdventureWorks2012 sample database.</span></span> <span data-ttu-id="6ba84-161">该示例对 **Production.Document** 表的 **Document** 列添加语义索引，该列已有全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-161">The example adds a semantic index on the **Document** column of the **Production.Document** table, which already has a full-text index.</span></span> <span data-ttu-id="6ba84-162">该示例指定将不自动重新填充索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-162">The example specifies that the index will not be repopulated automatically.</span></span>  
  
```sql  
ALTER FULLTEXT INDEX ON Production.Document  
    ALTER COLUMN Document  
        ADD Statistical_Semantics  
    WITH NO POPULATION  
GO  
```  
  
 <span data-ttu-id="6ba84-163">**使用 SQL Server Management Studio 添加语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-163">**Add a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="6ba84-164">可以在“全文索引属性”对话框的“全文索引列”页上更改启用语义索引和全文索引的列。</span><span class="sxs-lookup"><span data-stu-id="6ba84-164">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="6ba84-165">有关详细信息，请参阅 [管理全文索引](../../database-engine/manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-165">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-altering-an-existing-index"></a><a name="addreq"></a><span data-ttu-id="6ba84-166">更改现有索引的要求和限制</span><span class="sxs-lookup"><span data-stu-id="6ba84-166">Requirements and Restrictions for Altering an Existing Index</span></span>  
  
-   <span data-ttu-id="6ba84-167">正在填充索引时，不能更改现有索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-167">You cannot alter an existing index while population of the index is in progress.</span></span> <span data-ttu-id="6ba84-168">有关监视索引填充进度的详细信息，请参阅 [管理和监视语义搜索](manage-and-monitor-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-168">For more information on monitoring the progress of index population, see [Manage and Monitor Semantic Search](manage-and-monitor-semantic-search.md).</span></span>  
  
-   <span data-ttu-id="6ba84-169">在 **ALTER FULLTEXT INDEX** 语句的单次调用中，不能将索引添加到列以及更改或删除同一列的索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-169">You cannot add indexing to a column, and alter or drop indexing for the same column, in a single call to the **ALTER FULLTEXT INDEX** statement.</span></span>  
  
##  <a name="dropping-a-semantic-index"></a><a name="dropping"></a><span data-ttu-id="6ba84-170">删除语义索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-170">Dropping a Semantic Index</span></span>  
  
###  <a name="how-to-drop-a-semantic-index"></a><a name="drophow"></a><span data-ttu-id="6ba84-171">如何：删除语义索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-171">How to: Drop a Semantic Index</span></span>  
 <span data-ttu-id="6ba84-172">在使用 **ALTER FULLTEXT INDEX** 语句更改现有全文索引时，可以删除语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-172">You can drop semantic indexing when you alter an existing full-text index with the **ALTER FULLTEXT INDEX** statement.</span></span> <span data-ttu-id="6ba84-173">您还可在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用各种对话框删除语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-173">You can also drop semantic indexing by using various dialog boxes in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6ba84-174">**使用 Transact-SQL 删除语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-174">**Drop a semantic index by using Transact-SQL**</span></span>  
 -   <span data-ttu-id="6ba84-175">若要仅从一个或多个列删除语义索引，请使用**ALTER column***column_name***drop STATISTICAL_SEMANTICS**选项来调用**alter 全文 INDEX**语句。</span><span class="sxs-lookup"><span data-stu-id="6ba84-175">To drop semantic indexing only from a column or columns, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP STATISTICAL_SEMANTICS** option.</span></span> <span data-ttu-id="6ba84-176">可以在单个 **ALTER** 语句中从多个列删除索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-176">You can drop the indexing from multiple columns in a single **ALTER** statement.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP STATISTICAL_SEMANTICS  
    GO  
    ```  
  
-   <span data-ttu-id="6ba84-177">若要从一列中删除全文索引和语义索引，请使用**ALTER column***column_name***Drop**选项调用**alter full INDEX**语句。</span><span class="sxs-lookup"><span data-stu-id="6ba84-177">To drop both full-text and semantic indexing from a column, call the **ALTER FULLTEXT INDEX** statement with the **ALTER COLUMN***column_name***DROP** option.</span></span>  
  
    ```sql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP  
    GO  
    ```  
  
 <span data-ttu-id="6ba84-178">**使用 SQL Server Management Studio 删除语义索引**</span><span class="sxs-lookup"><span data-stu-id="6ba84-178">**Drop a semantic index by using SQL Server Management Studio**</span></span>  
 <span data-ttu-id="6ba84-179">可以在“全文索引属性”对话框的“全文索引列”页上更改启用语义索引和全文索引的列。</span><span class="sxs-lookup"><span data-stu-id="6ba84-179">You can change the columns that are enabled for semantic and full-text indexing on the **Full-Text Index Columns** page of the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="6ba84-180">有关详细信息，请参阅 [管理全文索引](../../database-engine/manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-180">For more information, see [Manage Full-Text Indexes](../../database-engine/manage-full-text-indexes.md).</span></span>  
  
###  <a name="requirements-and-restrictions-for-dropping-a-semantic-index"></a><a name="dropreq"></a><span data-ttu-id="6ba84-181">删除语义索引的要求和限制</span><span class="sxs-lookup"><span data-stu-id="6ba84-181">Requirements and Restrictions for Dropping a Semantic Index</span></span>  
  
-   <span data-ttu-id="6ba84-182">保留语义索引时不能从列删除全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-182">You cannot drop full-text indexing from a column while retaining semantic indexing.</span></span> <span data-ttu-id="6ba84-183">对于文档相似性结果，语义索引依赖于全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-183">Semantic indexing depends on full-text indexing for document similarity results.</span></span>  
  
-   <span data-ttu-id="6ba84-184">在从表中启用语义索引的最后一个列中删除语义索引时，不能指定 **NO POPULATION** 选项。</span><span class="sxs-lookup"><span data-stu-id="6ba84-184">You cannot specify the **NO POPULATION** option when you drop semantic indexing from the last column in a table for which semantic indexing was enabled.</span></span> <span data-ttu-id="6ba84-185">需要一个填充周期来删除以前编制索引的结果。</span><span class="sxs-lookup"><span data-stu-id="6ba84-185">A population cycle is required to remove the results that were indexed previously.</span></span>  
  
## <a name="checking-whether-semantic-search-is-enabled-on-database-objects"></a><span data-ttu-id="6ba84-186">检查是否在数据库对象上启用了语义搜索</span><span class="sxs-lookup"><span data-stu-id="6ba84-186">Checking Whether Semantic Search Is Enabled on Database Objects</span></span>  
  
###  <a name="how-to-check-whether-semantic-search-is-enabled-on-database-objects"></a><a name="HowToCheckEnabled"></a><span data-ttu-id="6ba84-187">如何：检查是否在数据库对象上启用了语义搜索</span><span class="sxs-lookup"><span data-stu-id="6ba84-187">How To: Check Whether Semantic Search Is Enabled on Database Objects</span></span>  
 <span data-ttu-id="6ba84-188">**是否为数据库启用了语义搜索？**</span><span class="sxs-lookup"><span data-stu-id="6ba84-188">**Is semantic search enabled for a database?**</span></span>  
 <span data-ttu-id="6ba84-189">查询 [DATABASEPROPERTYEX (Transact-SQL)](/sql/t-sql/functions/databasepropertyex-transact-sql) 元数据函数的 **IsFullTextEnabled** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ba84-189">Query the **IsFullTextEnabled** property of the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="6ba84-190">返回值 1 表示为数据库启用了全文搜索和语义搜索；返回值 0 表示未启用它们。</span><span class="sxs-lookup"><span data-stu-id="6ba84-190">A return value of 1 indicates that full-text search and semantic search are enabled for the database; a return value of 0 indicates that they are not enabled.</span></span>  
  
```sql  
SELECT DATABASEPROPERTYEX('database_name', 'IsFullTextEnabled')  
GO  
```  
  
 <span data-ttu-id="6ba84-191">**是否为表启用了语义搜索？**</span><span class="sxs-lookup"><span data-stu-id="6ba84-191">**Is semantic search enabled for a table?**</span></span>  
 <span data-ttu-id="6ba84-192">查询 [OBJECTPROPERTYEX (Transact-SQL)](/sql/t-sql/functions/objectproperty-transact-sql) 元数据函数的 **TableFullTextSemanticExtraction** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ba84-192">Query the **TableFullTextSemanticExtraction** property of the [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) metadata function.</span></span>  
  
 <span data-ttu-id="6ba84-193">返回值 1 表示为表启用了语义搜索；返回值 0 表示未启用它。</span><span class="sxs-lookup"><span data-stu-id="6ba84-193">A return value of 1 indicates that semantic search is enabled for the table; a return value of 0 indicates that it is not enabled.</span></span>  
  
```scr  
SELECT OBJECTPROPERTYEX(OBJECT_ID('table_name'), 'TableFullTextSemanticExtraction')  
GO  
```  
  
 <span data-ttu-id="6ba84-194">**是否为列启用了语义搜索？**</span><span class="sxs-lookup"><span data-stu-id="6ba84-194">**Is semantic search enabled for a column?**</span></span>  
 <span data-ttu-id="6ba84-195">若要确定是否为特定列启用了语义搜索：</span><span class="sxs-lookup"><span data-stu-id="6ba84-195">To determine whether semantic search is enabled for a specific column:</span></span>  
  
-   <span data-ttu-id="6ba84-196">查询 [COLUMNPROPERTY (Transact-SQL)](/sql/t-sql/functions/columnproperty-transact-sql) 元数据函数的 **StatisticalSemantics** 属性。</span><span class="sxs-lookup"><span data-stu-id="6ba84-196">Query the **StatisticalSemantics** property of the [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) metadata function.</span></span>  
  
     <span data-ttu-id="6ba84-197">返回值 1 表示为列启用了语义搜索；返回值 0 表示未启用它。</span><span class="sxs-lookup"><span data-stu-id="6ba84-197">A return value of 1 indicates that semantic search is enabled for the column; a return value of 0 indicates that it is not enabled.</span></span>  
  
    ```sql  
    SELECT COLUMNPROPERTY(OBJECT_ID('table_name'), 'column_name', 'StatisticalSemantics')  
    GO  
    ```  
  
-   <span data-ttu-id="6ba84-198">查询目录视图 [sys.fulltext_index_columns (Transact SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) 以获取全文索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-198">Query the catalog view [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) for the full-text index.</span></span>  
  
     <span data-ttu-id="6ba84-199">**statistical_semantics** 列中的值 1 表示除了启用全文索引编制外，还为指定的列启用了语义索引编制。</span><span class="sxs-lookup"><span data-stu-id="6ba84-199">A value of 1 in the **statistical_semantics** column indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
    ```sql  
    SELECT * FROM sys.fulltext_index_columns WHERE object_id = OBJECT_ID('table_name')  
    GO  
    ```  
  
-   <span data-ttu-id="6ba84-200">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的对象资源管理器中，右键单击一个列，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6ba84-200">In Object Explorer in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click on a column and select **Properties**.</span></span> <span data-ttu-id="6ba84-201">在 **“列属性”** 对话框的 **“常规”** 页上，查看 **“统计语义”** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="6ba84-201">On the **General** page of the **Column Properties** dialog box, check the value of the **Statistical Semantics** property.</span></span>  
  
     <span data-ttu-id="6ba84-202">值 True 表示除了启用全文索引外，还为指定的列启用了语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-202">A value of True indicates that the specified column is enabled for semantic indexing in addition to full-text indexing.</span></span>  
  
## <a name="determining-what-can-be-indexed-for-semantic-search"></a><span data-ttu-id="6ba84-203">确定可对哪些内容编制索引以进行语义搜索</span><span class="sxs-lookup"><span data-stu-id="6ba84-203">Determining What Can Be Indexed for Semantic Search</span></span>  
  
###  <a name="how-to-check-which-languages-are-supported-for-semantic-search"></a><a name="HowToCheckLanguages"></a><span data-ttu-id="6ba84-204">如何：检查语义搜索支持的语言</span><span class="sxs-lookup"><span data-stu-id="6ba84-204">How To: Check Which Languages Are Supported for Semantic Search</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6ba84-205">语义索引比全文索引支持的语言少。</span><span class="sxs-lookup"><span data-stu-id="6ba84-205">Fewer languages are supported for semantic indexing than for full-text indexing.</span></span> <span data-ttu-id="6ba84-206">因此，您可以对某些列编制索引以进行全文搜索，但不能进行语义搜索。</span><span class="sxs-lookup"><span data-stu-id="6ba84-206">As a result, there may be columns that you can index for full-text search, but not for semantic search.</span></span>  
  
 <span data-ttu-id="6ba84-207">查询目录视图 [sys.fulltext_semantic_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-207">Query the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
```sql  
SELECT * FROM sys.fulltext_semantic_languages  
GO  
```  
  
 <span data-ttu-id="6ba84-208">语义索引支持以下语言。</span><span class="sxs-lookup"><span data-stu-id="6ba84-208">The following languages are supported for semantic indexing.</span></span> <span data-ttu-id="6ba84-209">此列表按 LCID 列出了目录视图 [sys.fulltext_semantic_languages (Transact SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) 的输出。</span><span class="sxs-lookup"><span data-stu-id="6ba84-209">This list represents the output of the catalog view [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql), ordered by LCID.</span></span>  
  
|<span data-ttu-id="6ba84-210">语言</span><span class="sxs-lookup"><span data-stu-id="6ba84-210">Language</span></span>|<span data-ttu-id="6ba84-211">LCID</span><span class="sxs-lookup"><span data-stu-id="6ba84-211">LCID</span></span>|  
|--------------|----------|  
|<span data-ttu-id="6ba84-212">德语</span><span class="sxs-lookup"><span data-stu-id="6ba84-212">German</span></span>|<span data-ttu-id="6ba84-213">1031</span><span class="sxs-lookup"><span data-stu-id="6ba84-213">1031</span></span>|  
|<span data-ttu-id="6ba84-214">英语(美国)</span><span class="sxs-lookup"><span data-stu-id="6ba84-214">English (US)</span></span>|<span data-ttu-id="6ba84-215">2052</span><span class="sxs-lookup"><span data-stu-id="6ba84-215">1033</span></span>|  
|<span data-ttu-id="6ba84-216">法语</span><span class="sxs-lookup"><span data-stu-id="6ba84-216">French</span></span>|<span data-ttu-id="6ba84-217">1036</span><span class="sxs-lookup"><span data-stu-id="6ba84-217">1036</span></span>|  
|<span data-ttu-id="6ba84-218">意大利语</span><span class="sxs-lookup"><span data-stu-id="6ba84-218">Italian</span></span>|<span data-ttu-id="6ba84-219">1040</span><span class="sxs-lookup"><span data-stu-id="6ba84-219">1040</span></span>|  
|<span data-ttu-id="6ba84-220">葡萄牙语(巴西)</span><span class="sxs-lookup"><span data-stu-id="6ba84-220">Portuguese (Brazil)</span></span>|<span data-ttu-id="6ba84-221">1046</span><span class="sxs-lookup"><span data-stu-id="6ba84-221">1046</span></span>|  
|<span data-ttu-id="6ba84-222">俄语</span><span class="sxs-lookup"><span data-stu-id="6ba84-222">Russian</span></span>|<span data-ttu-id="6ba84-223">1049</span><span class="sxs-lookup"><span data-stu-id="6ba84-223">1049</span></span>|  
|<span data-ttu-id="6ba84-224">瑞典语</span><span class="sxs-lookup"><span data-stu-id="6ba84-224">Swedish</span></span>|<span data-ttu-id="6ba84-225">1053</span><span class="sxs-lookup"><span data-stu-id="6ba84-225">1053</span></span>|  
|<span data-ttu-id="6ba84-226">英语(英国)</span><span class="sxs-lookup"><span data-stu-id="6ba84-226">English (UK)</span></span>|<span data-ttu-id="6ba84-227">2057</span><span class="sxs-lookup"><span data-stu-id="6ba84-227">2057</span></span>|  
|<span data-ttu-id="6ba84-228">葡萄牙语(葡萄牙)</span><span class="sxs-lookup"><span data-stu-id="6ba84-228">Portuguese (Portugal)</span></span>|<span data-ttu-id="6ba84-229">2070</span><span class="sxs-lookup"><span data-stu-id="6ba84-229">2070</span></span>|  
|<span data-ttu-id="6ba84-230">西班牙语</span><span class="sxs-lookup"><span data-stu-id="6ba84-230">Spanish</span></span>|<span data-ttu-id="6ba84-231">3082</span><span class="sxs-lookup"><span data-stu-id="6ba84-231">3082</span></span>|  
  
###  <a name="how-to-determine-which-document-types-can-be-indexed"></a><a name="doctypes"></a><span data-ttu-id="6ba84-232">如何：确定可以为哪些文档类型编制索引</span><span class="sxs-lookup"><span data-stu-id="6ba84-232">How To: Determine Which Document Types Can Be Indexed</span></span>  
 <span data-ttu-id="6ba84-233">查询目录视图 [sys.fulltext_document_types (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-233">Query the catalog view [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).</span></span>  
  
 <span data-ttu-id="6ba84-234">如果您要为其编制索引的文档类型不在所支持类型的列表中，则可能必须查找、下载和安装其他筛选器。</span><span class="sxs-lookup"><span data-stu-id="6ba84-234">If the document type that you want to index is not in the list of supported types, then you may have to locate, download, and install additional filters.</span></span> <span data-ttu-id="6ba84-235">有关详细信息，请参阅 [查看或更改注册的筛选器和断字符](view-or-change-registered-filters-and-word-breakers.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba84-235">For more information, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
##  <a name="best-practice-consider-creating-a-separate-filegroup-for-the-full-text-and-semantic-indexes"></a><a name="BestPracticeFilegroup"></a><span data-ttu-id="6ba84-236">最佳做法：考虑为全文索引和语义索引创建单独的文件组</span><span class="sxs-lookup"><span data-stu-id="6ba84-236">Best Practice: Consider Creating a Separate Filegroup for the Full-Text and Semantic Indexes</span></span>  
 <span data-ttu-id="6ba84-237">如果磁盘空间分配成问题，请考虑为全文索引和语义索引创建单独的文件组。</span><span class="sxs-lookup"><span data-stu-id="6ba84-237">Consider creating a separate filegroup for the full-text and semantic indexes if disk space allocation is a concern.</span></span> <span data-ttu-id="6ba84-238">在全文索引所在的文件组中创建语义索引。</span><span class="sxs-lookup"><span data-stu-id="6ba84-238">The semantic indexes are created in the same filegroup as the full-text index.</span></span> <span data-ttu-id="6ba84-239">完全填充的语义索引可能包含大量数据。</span><span class="sxs-lookup"><span data-stu-id="6ba84-239">A fully populated semantic index may contain large amount of data.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-searching-on-specific-column-returns-no-results"></a><a name="IssueNoResults"></a><span data-ttu-id="6ba84-240">问题：搜索特定列时未返回结果</span><span class="sxs-lookup"><span data-stu-id="6ba84-240">Problem: Searching on Specific Column Returns No Results</span></span>  
 <span data-ttu-id="6ba84-241">**是否为 Unicode 语言指定了非 Unicode LCID？**</span><span class="sxs-lookup"><span data-stu-id="6ba84-241">**Was a non-Unicode LCID specified for a Unicode language?**</span></span>  
 <span data-ttu-id="6ba84-242">可能对非 Unicode 列类型启用了语义索引，而该列的 LCID 用于只有 Unicode 词的语言，如用于俄语的 LCID 1049。</span><span class="sxs-lookup"><span data-stu-id="6ba84-242">It is possible to enable semantic indexing on a non-Unicode column type with an LCID for a language that only has Unicode words, such as LCID 1049 for Russian.</span></span> <span data-ttu-id="6ba84-243">在这种情况下，将不从此列的语义索引返回结果。</span><span class="sxs-lookup"><span data-stu-id="6ba84-243">In this case, no results will ever be returned from the semantic indexes on this column.</span></span>  
  
  
