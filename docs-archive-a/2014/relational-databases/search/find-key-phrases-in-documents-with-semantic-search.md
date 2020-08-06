---
title: 使用语义搜索在文档中查找关键短语 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8388fb704bf13f44d025e6e32a1450d537f61832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688799"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a><span data-ttu-id="caadb-102">使用语义搜索查找文档中的关键短语</span><span class="sxs-lookup"><span data-stu-id="caadb-102">Find Key Phrases in Documents with Semantic Search</span></span>
  <span data-ttu-id="caadb-103">介绍如何在为统计语义索引配置的文档或文本列中查找关键短语。</span><span class="sxs-lookup"><span data-stu-id="caadb-103">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-key-phrases-in-documents"></a><a name="BasicsQueryKey"></a><span data-ttu-id="caadb-104">在文档中查找关键短语</span><span class="sxs-lookup"><span data-stu-id="caadb-104">Finding Key Phrases in Documents</span></span>  
  
###  <a name="how-to-find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a><span data-ttu-id="caadb-105">如何：通过 SEMANTICKEYPHRASETABLE 在文档中查找关键短语</span><span class="sxs-lookup"><span data-stu-id="caadb-105">How to: Find the Key Phrases in Documents with SEMANTICKEYPHRASETABLE</span></span>  
 <span data-ttu-id="caadb-106">若要确定特定文档中的关键短语或确定包含特定关键短语的文档，可以查询函数 [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="caadb-106">To identify the key phrases in specific documents, or to identify documents that contain specific key phrases, query the function [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
 <span data-ttu-id="caadb-107">SEMANTICKEYPHRASETABLE 为与指定表中的列关联的那些关键短语返回包含零行、一行或多行的表。</span><span class="sxs-lookup"><span data-stu-id="caadb-107">SEMANTICKEYPHRASETABLE returns a table with zero, one, or more rows for those key phrases associated with columns in the specified table.</span></span> <span data-ttu-id="caadb-108">可以在 SELECT 语句的 FROM 子句中像引用常规表名那样引用此行集函数。</span><span class="sxs-lookup"><span data-stu-id="caadb-108">This rowset function can be referenced in the FROM clause of a SELECT statement as if it were a regular table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caadb-109">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，对于语义搜索只将单个单词编入索引，多词短语 (ngrams) 未编入索引。</span><span class="sxs-lookup"><span data-stu-id="caadb-109">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], only single words are indexed for semantic search; multi-word phrases (ngrams) are not indexed.</span></span> <span data-ttu-id="caadb-110">此外，相同单词的各种形式单独编入索引，例如，“computer”和“computers”单独编入索引。</span><span class="sxs-lookup"><span data-stu-id="caadb-110">Also, various forms of the same word are indexed separately; for example, "computer" and "computers" are indexed separately.</span></span>  
  
 <span data-ttu-id="caadb-111">有关 SEMANTICKEYPHRASETABLE 函数所需的参数和它返回的结果表的详细信息，请参阅 [semantickeyphrasetable (Transact-SQL)](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="caadb-111">For detailed information about the parameters required by the SEMANTICKEYPHRASETABLE function, and about the table of results that it returns, see [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="caadb-112">针对的列必须启用了全文索引和语义索引。</span><span class="sxs-lookup"><span data-stu-id="caadb-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a><span data-ttu-id="caadb-113">示例1：查找特定文档中的前几个关键短语</span><span class="sxs-lookup"><span data-stu-id="caadb-113">Example 1: Find the Top Key Phrases in a Specific Document</span></span>  
 <span data-ttu-id="caadb-114">以下示例从通过 @DocumentId 变量指定的文档中检索前 10 个关键短语，该变量位于 AdventureWorks 示例数据库的 Production.Document 表的 Document 列中。</span><span class="sxs-lookup"><span data-stu-id="caadb-114">The following example retrieves the top 10 key phrases from the document specified by the @DocumentId variable in the Document column of the Production.Document table of the AdventureWorks sample database.</span></span> <span data-ttu-id="caadb-115">@DocumentId 变量表示全文检索的键列的一个值。</span><span class="sxs-lookup"><span data-stu-id="caadb-115">The @DocumentId variable represents a value from the key column of the full-text index.</span></span>  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 <span data-ttu-id="caadb-116">**SEMANTICKEYPHRASETABLE** 函数使用索引查找替代表扫描高效检索这些结果。</span><span class="sxs-lookup"><span data-stu-id="caadb-116">The **SEMANTICKEYPHRASETABLE** function retrieves these results efficiently by using an index seek instead of a table scan.</span></span>  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a><span data-ttu-id="caadb-117">示例2：查找包含特定关键短语的顶级文档</span><span class="sxs-lookup"><span data-stu-id="caadb-117">Example 2: Find the Top Documents that Contain a Specific Key Phrase</span></span>  
 <span data-ttu-id="caadb-118">以下示例从 AdventureWorks 示例数据库的 Production.Document 表的 Document 列中检索包含关键短语“Bracket”的前 25 个文档。</span><span class="sxs-lookup"><span data-stu-id="caadb-118">The following example retrieves the top 25 documents that contain the key phrase "Bracket" from the Document column of the Production.Document table of the AdventureWorks sample database.</span></span>  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
