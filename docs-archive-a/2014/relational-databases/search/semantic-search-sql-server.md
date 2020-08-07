---
title: 语义搜索 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91062864b77ba3c62a87d66b8ff93068f9c10c8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691164"
---
# <a name="semantic-search-sql-server"></a><span data-ttu-id="f4e85-102">语义搜索 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4e85-102">Semantic Search (SQL Server)</span></span>
  <span data-ttu-id="f4e85-103">统计语义搜索通过提取统计上相关的“关键短语” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]*并对其进行索引，提供对*中存储的非结构化文档的更深层次剖析。</span><span class="sxs-lookup"><span data-stu-id="f4e85-103">Statistical Semantic Search provides deep insight into unstructured documents stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases by extracting and indexing statistically relevant *key phrases*.</span></span> <span data-ttu-id="f4e85-104">然后，它还使用这些关键短语标识“相似或相关文档” \*\* 并对其进行索引。</span><span class="sxs-lookup"><span data-stu-id="f4e85-104">Then it also uses these key phrases to identify and index *documents that are similar or related*.</span></span>  
  
 <span data-ttu-id="f4e85-105">您通过使用三个 Transact-SQL 行集函数将结果作为结构化数据检索，查询这些语义索引。</span><span class="sxs-lookup"><span data-stu-id="f4e85-105">You query these semantic indexes by using three Transact-SQL rowset functions to retrieve the results as structured data.</span></span>  
  
##  <a name="what-can-i-do-with-semantic-search"></a><a name="whatcanido"></a><span data-ttu-id="f4e85-106">语义搜索有哪些用途？</span><span class="sxs-lookup"><span data-stu-id="f4e85-106">What Can I Do with Semantic Search?</span></span>  
 <span data-ttu-id="f4e85-107">语义搜索以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中现有的全文搜索功能为基础，但允许超出关键字搜索范畴的新方案。</span><span class="sxs-lookup"><span data-stu-id="f4e85-107">Semantic search builds upon the existing full-text search feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but enables new scenarios that extend beyond keyword searches.</span></span> <span data-ttu-id="f4e85-108">全文搜索允许你查询文档中的“词”**，语义搜索则允许你查询文档的“含义”**。</span><span class="sxs-lookup"><span data-stu-id="f4e85-108">While full-text search lets you query the *words* in a document, semantic search lets you query the *meaning* of the document.</span></span> <span data-ttu-id="f4e85-109">现有的可能解决方案包括自动标记提取、相关内容发现以及相似内容中层次结构导航。</span><span class="sxs-lookup"><span data-stu-id="f4e85-109">Solutions that are now possible include automatic tag extraction, related content discovery, and hierarchical navigation across similar content.</span></span> <span data-ttu-id="f4e85-110">例如，您可以查询关键短语的索引来建立一个组织或文档集的分类索引。</span><span class="sxs-lookup"><span data-stu-id="f4e85-110">For example, you can query the index of key phrases to build the taxonomy for an organization, or for a corpus of documents.</span></span> <span data-ttu-id="f4e85-111">或者，您可以查询文档相似性索引来标识匹配某一工作描述的简历。</span><span class="sxs-lookup"><span data-stu-id="f4e85-111">Or, you can query the document similarity index to identify resumes that match a job description.</span></span>  
  
 <span data-ttu-id="f4e85-112">下面的示例演示了语义搜索的功能。</span><span class="sxs-lookup"><span data-stu-id="f4e85-112">The following examples demonstrate the capabilities of Semantic Search.</span></span>  
  
###  <a name="find-the-key-phrases-in-a-document"></a><a name="find1"></a><span data-ttu-id="f4e85-113">查找文档中的关键短语</span><span class="sxs-lookup"><span data-stu-id="f4e85-113">Find the Key Phrases in a Document</span></span>  
 <span data-ttu-id="f4e85-114">下面的查询获取在示例文档中已标识的关键短语。</span><span class="sxs-lookup"><span data-stu-id="f4e85-114">The following query gets the key phrases that were identified in the sample document.</span></span> <span data-ttu-id="f4e85-115">该查询按照对每个关键短语的统计重要性进行排名的分数以降序方式展示结果。</span><span class="sxs-lookup"><span data-stu-id="f4e85-115">It presents the results in descending order by the score that ranks the statistical significance of each key phrase.</span></span> <span data-ttu-id="f4e85-116">此查询调用 [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="f4e85-116">This query calls the [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) function.</span></span>  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-similar-or-related-documents"></a><a name="find2"></a><span data-ttu-id="f4e85-117">查找相似或相关文档</span><span class="sxs-lookup"><span data-stu-id="f4e85-117">Find Similar or Related Documents</span></span>  
 <span data-ttu-id="f4e85-118">以下查询获取已标识为与示例文档相似或相关的文档。</span><span class="sxs-lookup"><span data-stu-id="f4e85-118">The following query gets the documents that were identified as similar or related to the sample document.</span></span> <span data-ttu-id="f4e85-119">该查询按照对这两个文档的相似性进行排名的分数以降序方式展示结果。</span><span class="sxs-lookup"><span data-stu-id="f4e85-119">It presents the results in descending order by the score that ranks the similarity of the 2 documents.</span></span> <span data-ttu-id="f4e85-120">此查询调用 [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="f4e85-120">This query calls the [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) function.</span></span>  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-the-key-phrases-that-make-documents-similar-or-related"></a><a name="find3"></a><span data-ttu-id="f4e85-121">查找使文档相似或相关的关键短语</span><span class="sxs-lookup"><span data-stu-id="f4e85-121">Find the Key Phrases That Make Documents Similar or Related</span></span>  
 <span data-ttu-id="f4e85-122">以下查询获取使两个示例文档彼此相似或相关的关键短语。</span><span class="sxs-lookup"><span data-stu-id="f4e85-122">The following query gets the key phrases that make the 2 sample documents similar or related to one another.</span></span> <span data-ttu-id="f4e85-123">该查询按照对每个关键短语的权重进行排名的分数以降序方式展示结果。</span><span class="sxs-lookup"><span data-stu-id="f4e85-123">It presents the results in descending order by the score that ranks the weight of each key phrase.</span></span> <span data-ttu-id="f4e85-124">此查询调用 [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="f4e85-124">This query calls the [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) function.</span></span>  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="storing-documents-in-sql-server"></a><a name="store"></a><span data-ttu-id="f4e85-125">将文档存储在 SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4e85-125">Storing Documents in SQL Server</span></span>  
 <span data-ttu-id="f4e85-126">在您可以使用语义搜索对文档建立索引之前，必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中存储文档。</span><span class="sxs-lookup"><span data-stu-id="f4e85-126">Before you can index documents with Semantic Search, you have to store the documents in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="f4e85-127">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 FileTable 功能使非结构化的文件和文档能够很好地通过关系数据库处理。</span><span class="sxs-lookup"><span data-stu-id="f4e85-127">The FileTable feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] makes unstructured files and documents first-class citizens of the relational database.</span></span> <span data-ttu-id="f4e85-128">这样，数据库开发人员在 Transact-SQL 基于集的操作中可以将文档与结构化数据一起处理。</span><span class="sxs-lookup"><span data-stu-id="f4e85-128">As a result, database developers can manipulate documents together with structured data in Transact-SQL set-based operations.</span></span>  
  
 <span data-ttu-id="f4e85-129">有关 FileTable 功能的详细信息，请参阅 [FileTable (SQL Server)](../blob/filetables-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e85-129">For more information about the FileTable feature, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span> <span data-ttu-id="f4e85-130">有关 FILESTREAM 功能（这是用于在数据库中存储文档的另一个选项）的信息，请参阅 [FILESTREAM (SQL Server)](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e85-130">For information about the FILESTREAM feature, which is another option for storing documents in the database, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="f4e85-131">相关任务</span><span class="sxs-lookup"><span data-stu-id="f4e85-131">Related Tasks</span></span>  
 [<span data-ttu-id="f4e85-132">安装和配置语义搜索</span><span class="sxs-lookup"><span data-stu-id="f4e85-132">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)  
 <span data-ttu-id="f4e85-133">说明统计语义搜索的必备组件以及如何安装或检查它们。</span><span class="sxs-lookup"><span data-stu-id="f4e85-133">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
 [<span data-ttu-id="f4e85-134">对表和列启用语义搜索</span><span class="sxs-lookup"><span data-stu-id="f4e85-134">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)  
 <span data-ttu-id="f4e85-135">介绍如何启用或禁用包含文档或文本的选定列上的统计语义索引。</span><span class="sxs-lookup"><span data-stu-id="f4e85-135">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 [<span data-ttu-id="f4e85-136">使用语义搜索查找文档中的关键短语</span><span class="sxs-lookup"><span data-stu-id="f4e85-136">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)  
 <span data-ttu-id="f4e85-137">介绍如何在为统计语义索引配置的文档或文本列中查找关键短语。</span><span class="sxs-lookup"><span data-stu-id="f4e85-137">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="f4e85-138">使用语义搜索来查找相似和相关文档</span><span class="sxs-lookup"><span data-stu-id="f4e85-138">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)  
 <span data-ttu-id="f4e85-139">说明在为统计语义索引配置的列上如何查找相似或相关的文档或文本值，以及如何查找其相似或相关程度的信息。</span><span class="sxs-lookup"><span data-stu-id="f4e85-139">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="f4e85-140">管理和监视语义搜索</span><span class="sxs-lookup"><span data-stu-id="f4e85-140">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
 <span data-ttu-id="f4e85-141">说明语义索引编制的进度以及与监视和管理索引有关的任务。</span><span class="sxs-lookup"><span data-stu-id="f4e85-141">Describes the process of semantic indexing and the tasks related to monitoring and managing the indexes.</span></span>  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="f4e85-142">相关内容</span><span class="sxs-lookup"><span data-stu-id="f4e85-142">Related Content</span></span>  
 [<span data-ttu-id="f4e85-143">语义搜索 DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="f4e85-143">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="f4e85-144">列出用于支持统计语义搜索的新增或更改的 Transact-SQL 语句和 SQL Server 数据库对象。</span><span class="sxs-lookup"><span data-stu-id="f4e85-144">Lists the Transact-SQL statements and the SQL Server database objects added or changed to support statistical semantic search.</span></span>  
  
  
