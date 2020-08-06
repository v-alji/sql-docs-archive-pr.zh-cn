---
title: 使用全文搜索查询 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d78707925303d5e19d93b170f257d76fb7d1747d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689835"
---
# <a name="query-with-full-text-search"></a><span data-ttu-id="67f1e-102">使用全文搜索查询</span><span class="sxs-lookup"><span data-stu-id="67f1e-102">Query with Full-Text Search</span></span>
  <span data-ttu-id="67f1e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文查询使用全文谓词（CONTAINS 和 FREETEXT）以及全文函数（CONTAINSTABLE 和 FREETEXTTABLE）来定义全文搜索。</span><span class="sxs-lookup"><span data-stu-id="67f1e-103">To define full-text searches, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text queries use the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE.</span></span> <span data-ttu-id="67f1e-104">它们支持复杂的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语法，这种语法支持各种形式的查询词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-104">These support rich [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that supports a variety of forms of query terms.</span></span> <span data-ttu-id="67f1e-105">若要编写全文查询，必须了解何时以及如何使用这些谓词和函数。</span><span class="sxs-lookup"><span data-stu-id="67f1e-105">To write full-text queries, you must learn when and how to use these predicates and functions.</span></span>  
  
##  <a name="overview-of-the-full-text-predicates-contains-and-freetext"></a><a name="OV_ft_predicates"></a> <span data-ttu-id="67f1e-106">(CONTAINS 和 FREETEXT 的全文谓词概述) </span><span class="sxs-lookup"><span data-stu-id="67f1e-106">Overview of the Full-Text Predicates (CONTAINS and FREETEXT)</span></span>  
 <span data-ttu-id="67f1e-107">CONTAINS 和 FREETEXT 谓词返回 TRUE 或 FALSE 值。</span><span class="sxs-lookup"><span data-stu-id="67f1e-107">The CONTAINS and FREETEXT predicates return a TRUE or FALSE value.</span></span> <span data-ttu-id="67f1e-108">它们只能用于指定选择条件，以确定给定的行是否与全文查询相匹配。</span><span class="sxs-lookup"><span data-stu-id="67f1e-108">They can be used only to specify selection criteria for determining whether a given row matches the full-text query.</span></span> <span data-ttu-id="67f1e-109">匹配的行在结果集中返回。</span><span class="sxs-lookup"><span data-stu-id="67f1e-109">Matching rows are returned in the result set.</span></span> <span data-ttu-id="67f1e-110">CONTAINS 和 FREETEXT 在 SELECT 语句的 WHERE 或 HAVING 子句中指定。</span><span class="sxs-lookup"><span data-stu-id="67f1e-110">CONTAINS and FREETEXT are specified in the WHERE or HAVING clause of a SELECT statement.</span></span> <span data-ttu-id="67f1e-111">它们可以与任何其他 [!INCLUDE[tsql](../../includes/tsql-md.md)] 谓词（例如 LIKE 和 BETWEEN）结合使用。</span><span class="sxs-lookup"><span data-stu-id="67f1e-111">They can be combined with any of the other [!INCLUDE[tsql](../../includes/tsql-md.md)] predicates, such as LIKE and BETWEEN.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-112">有关这些谓词的语法和参数的信息，请参阅[CONTAINS &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql)和[FREETEXT &#40;transact-sql&#41;](/sql/t-sql/queries/freetext-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-112">For information about the syntax and arguments of these predicates, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) and [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).</span></span>  
  
 <span data-ttu-id="67f1e-113">当使用 CONTAINS 或 FREETEXT 时，可以指定搜索表中的单个列、一组列或所有列。</span><span class="sxs-lookup"><span data-stu-id="67f1e-113">When using CONTAINS or FREETEXT, you can specify either a single column, a list of columns, or all columns in the table to be searched.</span></span> <span data-ttu-id="67f1e-114">此外，还可以指定语言，以便给定的全文查询使用此语言的资源进行断字和词干分析、同义词库查找以及干扰词删除。</span><span class="sxs-lookup"><span data-stu-id="67f1e-114">Optionally, you can specify the language whose resources will be used by given full-text query for word breaking and stemming, thesaurus lookups, and noise-word removal.</span></span>  
  
 <span data-ttu-id="67f1e-115">CONTAINS 和 FREETEXT 可用于搜索不同种类的匹配项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f1e-115">CONTAINS and FREETEXT are useful for different kind of matches, as follows:</span></span>  
  
-   <span data-ttu-id="67f1e-116">使用 CONTAINS（或 CONTAINSTABLE）可搜索单个词和短语的精确或模糊（不太精确的）匹配项、在一定差别范围内的相近词或加权匹配项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-116">Use CONTAINS (or CONTAINSTABLE) for precise or fuzzy (less precise) matches to single words and phrases, the proximity of words within a certain distance of one another, or weighted matches.</span></span> <span data-ttu-id="67f1e-117">当使用 CONTAINS 时，必须指定至少一个搜索条件，该搜索条件须指定要搜索的文本以及确定匹配项的条件。</span><span class="sxs-lookup"><span data-stu-id="67f1e-117">When using CONTAINS, you must specify at least one search condition that specifies the text that you are searching for and the conditions that determine matches.</span></span>  
  
     <span data-ttu-id="67f1e-118">可以在搜索条件之间使用逻辑运算。</span><span class="sxs-lookup"><span data-stu-id="67f1e-118">You can use logical operation between search conditions.</span></span> <span data-ttu-id="67f1e-119">有关详细信息，请参阅本主题后面的[使用布尔运算符（AND、OR 和 NOT (IN CONTAINS AND CONTAINSTABLE) ](#Using_Boolean_Operators)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-119">For more information, see [Using Boolean operators-AND, OR, AND NOT (in CONTAINS and CONTAINSTABLE)](#Using_Boolean_Operators), later in this topic.</span></span>  
  
-   <span data-ttu-id="67f1e-120">使用 FREETEXT（或 FREETEXTTABLE）可搜索与指定词、短语或句子（Freetext 字符串\*\*）的含义相符但措辞不完全相同的匹配项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-120">Use FREETEXT (or FREETEXTTABLE) for matching the meaning, but not the exact wording, of specified words, phrases or sentences (the *freetext string*).</span></span> <span data-ttu-id="67f1e-121">只要在指定列的全文索引中找到任何搜索词或任何搜索词的任何形式，就会生成匹配项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-121">Matches are generated if any term or form of any term is found in the full-text index of a specified column.</span></span>  
  
 <span data-ttu-id="67f1e-122">可以在 CONTAINS 或 FREETEXT 谓词中使用由四部分组成的名称对链接服务器上的目标表的全文索引列进行查询。</span><span class="sxs-lookup"><span data-stu-id="67f1e-122">You can use a four-part name in the CONTAINS or FREETEXT predicate to query full-text indexed columns of the target tables on a linked server.</span></span> <span data-ttu-id="67f1e-123">若要准备远程服务器以接收全文查询，请在远程服务器上的目标表和列上创建全文索引，然后将该远程服务器添加为链接服务器。</span><span class="sxs-lookup"><span data-stu-id="67f1e-123">To prepare a remote server to receive full-text queries, create a full-text index on the target tables and columns on the remote server and then add the remote server as a linked server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-124">当数据库兼容级别设置为100时， [OUTPUT 子句](/sql/t-sql/queries/output-clause-transact-sql)中不允许使用全文谓词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-124">Full-text predicates are not allowed in the [OUTPUT Clause](/sql/t-sql/queries/output-clause-transact-sql) when the database compatibility level is set to 100.</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="67f1e-125">示例</span><span class="sxs-lookup"><span data-stu-id="67f1e-125">Examples</span></span>  
  
#### <a name="a-using-contains-with-simple_term"></a><span data-ttu-id="67f1e-126">A.</span><span class="sxs-lookup"><span data-stu-id="67f1e-126">A.</span></span> <span data-ttu-id="67f1e-127">将 CONTAINS 与 <简单词> 一起使用</span><span class="sxs-lookup"><span data-stu-id="67f1e-127">Using CONTAINS with <simple_term></span></span>  
 <span data-ttu-id="67f1e-128">下面的示例查找包含 `$80.99` 一词且价格为 `"Mountain"`的所有产品。</span><span class="sxs-lookup"><span data-stu-id="67f1e-128">The following example finds all products with a price of `$80.99` that contain the word `"Mountain"`.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a><span data-ttu-id="67f1e-129">B.</span><span class="sxs-lookup"><span data-stu-id="67f1e-129">B.</span></span> <span data-ttu-id="67f1e-130">使用 FREETEXT 搜索包含指定字符值的单词</span><span class="sxs-lookup"><span data-stu-id="67f1e-130">Using FREETEXT to search for words containing specified character values</span></span>  
 <span data-ttu-id="67f1e-131">以下示例搜索包含与 vital、safety、components 相关的单词的所有文档。</span><span class="sxs-lookup"><span data-stu-id="67f1e-131">The following example searches for all documents containing the words related to vital, safety, components.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="overview-of-the-full-text-functions-containstable-and-freetexttable"></a><a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a><span data-ttu-id="67f1e-132">全文函数概述 (CONTAINSTABLE 和 FREETEXTTABLE) </span><span class="sxs-lookup"><span data-stu-id="67f1e-132">Overview of the Full-Text Functions (CONTAINSTABLE and FREETEXTTABLE)</span></span>  
 <span data-ttu-id="67f1e-133">像一般的表名一样，CONTAINSTABLE 和 FREETEXTTABLE 函数也可以在 SELECT 语句的 FROM 子句中进行引用。</span><span class="sxs-lookup"><span data-stu-id="67f1e-133">The CONTAINSTABLE and FREETEXTTABLE functions are referenced like a regular table name in the FROM clause of a SELECT statement.</span></span> <span data-ttu-id="67f1e-134">它们返回与全文查询匹配的、包含零行、一行或多行的表。</span><span class="sxs-lookup"><span data-stu-id="67f1e-134">They return a table of zero, one, or more rows that match the full-text query.</span></span> <span data-ttu-id="67f1e-135">返回的表只包含与该函数的全文搜索条件中指定的选择条件相匹配的基表的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-135">The returned table contains only rows of the base table that match the selection criteria specified in the full-text search condition of the function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-136">有关这些函数的语法和参数的信息，请参阅[CONTAINSTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)和[FREETEXTTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-136">For information about the syntax and arguments of these functions, see [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).</span></span>  
  
 <span data-ttu-id="67f1e-137">使用这些函数之一的查询返回每一行的相关性排名值 (RANK) 和全文键 (KEY)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f1e-137">Queries using one of these functions return a relevance ranking value (RANK) and full-text key (KEY) for each row, as follows:</span></span>  
  
-   <span data-ttu-id="67f1e-138">KEY 列</span><span class="sxs-lookup"><span data-stu-id="67f1e-138">KEY column</span></span>  
  
     <span data-ttu-id="67f1e-139">KEY 列返回所返回行的唯一值。</span><span class="sxs-lookup"><span data-stu-id="67f1e-139">The KEY column returns unique values of the returned rows.</span></span> <span data-ttu-id="67f1e-140">可使用 KEY 列指定选择条件。</span><span class="sxs-lookup"><span data-stu-id="67f1e-140">The KEY column can be used to specify selection criteria.</span></span>  
  
-   <span data-ttu-id="67f1e-141">RANK 列</span><span class="sxs-lookup"><span data-stu-id="67f1e-141">RANK column</span></span>  
  
     <span data-ttu-id="67f1e-142">RANK 列返回每一行的排名值 \*\* ，此值指示该行与选择条件相匹配的程度。</span><span class="sxs-lookup"><span data-stu-id="67f1e-142">The RANK column returns a *rank value* for each row that indicates how well the row matched the selection criteria.</span></span> <span data-ttu-id="67f1e-143">行中文本或文档的排名值越高，该行与给定的全文查询的相关性就越高。</span><span class="sxs-lookup"><span data-stu-id="67f1e-143">The higher the rank value of the text or document in a row, the more relevant the row is for the given full-text query.</span></span> <span data-ttu-id="67f1e-144">请注意，不同行的排名可以相同。</span><span class="sxs-lookup"><span data-stu-id="67f1e-144">Note that different rows can be ranked identically.</span></span> <span data-ttu-id="67f1e-145">可以通过指定可选的 top_n_by_rank\*\* 参数限制返回的匹配项的数目。</span><span class="sxs-lookup"><span data-stu-id="67f1e-145">You can limit the number of matches to be returned by specifying the optional *top_n_by_rank* parameter.</span></span> <span data-ttu-id="67f1e-146">有关详细信息，请参阅 [使用 RANK 限制搜索结果](limit-search-results-with-rank.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-146">For more information, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
 <span data-ttu-id="67f1e-147">当使用这些函数之一时，必须指定要进行全文搜索的基表。</span><span class="sxs-lookup"><span data-stu-id="67f1e-147">When using either of these functions, you must specify the base table that is to be full-text searched.</span></span> <span data-ttu-id="67f1e-148">与谓词一样，可以指定搜索表中的单个列、一组列或所有列；此外，还可以指定给定的全文查询将使用的资源的语言。</span><span class="sxs-lookup"><span data-stu-id="67f1e-148">As with the predicates, you can specify a single column, a list of columns, or all columns in the table to be searched, and optionally, the language whose resources will be used by given full-text query.</span></span>  
  
 <span data-ttu-id="67f1e-149">CONTAINSTABLE 用来搜索的匹配项的种类与 CONTAINS 相同，FREETEXTTABLE 用来搜索的匹配项的种类与 FREETEXT 相同。</span><span class="sxs-lookup"><span data-stu-id="67f1e-149">CONTAINSTABLE is useful for the same kinds of matches as CONTAINS, and FREETEXTTABLE is useful for the same kinds of matches as FREETEXT.</span></span> <span data-ttu-id="67f1e-150">有关详细信息，请参阅本主题前面的 [全文谓词（CONTAINS 和 FREETEXT）概述](#OV_ft_predicates)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-150">For more information, see [Overview of the Full-Text Predicates (CONTAINS and FREETEXT)](#OV_ft_predicates), earlier in this topic.</span></span> <span data-ttu-id="67f1e-151">在运行使用 CONTAINSTABLE 和 FREETEXTTABLE 函数的查询时，必须显式联接与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基表中的行一起返回的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-151">When running queries that use the CONTAINSTABLE and FREETEXTTABLE functions you must explicitly join rows that are returned with the rows in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base table.</span></span>  
  
 <span data-ttu-id="67f1e-152">通常，需要将 CONTAINSTABLE 或 FREETEXTTABLE 的结果与基表联接。</span><span class="sxs-lookup"><span data-stu-id="67f1e-152">Typically, the result of CONTAINSTABLE or FREETEXTTABLE needs to be joined with the base table.</span></span> <span data-ttu-id="67f1e-153">在这样的情况下，需要知道唯一键列名称。</span><span class="sxs-lookup"><span data-stu-id="67f1e-153">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="67f1e-154">该列出现在每个启用全文的表中，用于强制表的唯一行（“唯一键列”\*\*）。</span><span class="sxs-lookup"><span data-stu-id="67f1e-154">This column, which occurs in every full-text enabled table, is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="67f1e-155">有关详细信息，请参阅 [管理全文索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-155">For more information, see [Manage Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="67f1e-156">示例</span><span class="sxs-lookup"><span data-stu-id="67f1e-156">Examples</span></span>  
  
#### <a name="a-using-containstable"></a><span data-ttu-id="67f1e-157">A.</span><span class="sxs-lookup"><span data-stu-id="67f1e-157">A.</span></span> <span data-ttu-id="67f1e-158">使用 CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="67f1e-158">Using CONTAINSTABLE</span></span>  
 <span data-ttu-id="67f1e-159">对于在词“light”或“lightweight”附近包含词“aluminum”的 **Description** 列，以下示例返回其所有产品的说明 ID 和说明。</span><span class="sxs-lookup"><span data-stu-id="67f1e-159">The following example returns the description ID and description of all products for which the **Description** column contain the word "aluminum" near either the word "light" or the word "lightweight."</span></span> <span data-ttu-id="67f1e-160">仅返回排名值为 2 或更高的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-160">Only rows with a rank value of 2 or higher are returned.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a><span data-ttu-id="67f1e-161">B.</span><span class="sxs-lookup"><span data-stu-id="67f1e-161">B.</span></span> <span data-ttu-id="67f1e-162">使用 FREETEXTTABLE</span><span class="sxs-lookup"><span data-stu-id="67f1e-162">Using FREETEXTTABLE</span></span>  
 <span data-ttu-id="67f1e-163">以下示例扩展了 FREETEXTTABLE 查询，以便首先返回排名最高的行，然后将每一行的排名添加到选择列表中。</span><span class="sxs-lookup"><span data-stu-id="67f1e-163">The following example extends a FREETEXTTABLE query to return the highest ranked rows first and to add the ranking of each row to the select list.</span></span> <span data-ttu-id="67f1e-164">若要指定查询，必须知道**ProductDescriptionID**是表的唯一键列 `ProductDescription` 。</span><span class="sxs-lookup"><span data-stu-id="67f1e-164">To specify the query, you must know that **ProductDescriptionID** is the unique key column for the `ProductDescription` table.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="67f1e-165">下面是同一查询的扩展查询，此查询只返回排名值为 10 或更高的行：</span><span class="sxs-lookup"><span data-stu-id="67f1e-165">Here is an extension of the same query that only returns rows with a rank value of 10 or greater:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="using-boolean-operators---and-or-and-not---in-contains-and-containstable"></a><a name="Using_Boolean_Operators"></a><span data-ttu-id="67f1e-166">使用布尔运算符（AND、OR 和 NOT in CONTAINS 和 CONTAINSTABLE）</span><span class="sxs-lookup"><span data-stu-id="67f1e-166">Using Boolean operators - AND, OR, and NOT - in CONTAINS and CONTAINSTABLE</span></span>  
 <span data-ttu-id="67f1e-167">CONTAINS 谓词和 CONTAINSTABLE 函数使用相同的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="67f1e-167">The CONTAINS predicate and CONTAINSTABLE function use the same search conditions.</span></span> <span data-ttu-id="67f1e-168">两者都支持使用布尔运算符（AND、OR 和 NOT）来合并多个搜索词，以执行逻辑运算。</span><span class="sxs-lookup"><span data-stu-id="67f1e-168">Both support combining several search terms by using Boolean operators-AND, OR, AND NOT-to perform logical operations.</span></span> <span data-ttu-id="67f1e-169">例如，可以使用 AND 查找既包含“latte”又包含“New York-style bagel”的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-169">You could use AND, for example, to find rows that contain both "latte" and "New York-style bagel".</span></span> <span data-ttu-id="67f1e-170">例如，可以使用 AND NOT 查找包含“bagel”但不包含“cream cheese”的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-170">You can use AND NOT, for example, to find the rows that contain "bagel" but do not contain "cream cheese".</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-171">相反，FREETEXT 和 FREETEXTTABLE 将布尔值项视为词来搜索。</span><span class="sxs-lookup"><span data-stu-id="67f1e-171">In contrast, FREETEXT and FREETEXTTABLE treat the Boolean terms as words to be searched.</span></span>  
  
 <span data-ttu-id="67f1e-172">有关将 CONTAINS 与其他使用逻辑运算符 AND、OR 和 NOT 的谓词结合使用的信息，请参阅 [搜索条件 (Transact-SQL)](/sql/t-sql/queries/search-condition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-172">For information about combining CONTAINS with other predicates that use the logical operators AND, OR, and NOT, see [Search Condition &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).</span></span>  
  
### <a name="example"></a><span data-ttu-id="67f1e-173">示例</span><span class="sxs-lookup"><span data-stu-id="67f1e-173">Example</span></span>  
 <span data-ttu-id="67f1e-174">下面的示例使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库的 ProductDescription 表。</span><span class="sxs-lookup"><span data-stu-id="67f1e-174">The following example uses the ProductDescription table of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="67f1e-175">该查询使用 CONTAINS 谓词搜索说明 ID 不等于 5 并且既包含词“Aluminum”又包含词“spindle”的说明。</span><span class="sxs-lookup"><span data-stu-id="67f1e-175">The query uses the CONTAINS predicate to search for descriptions in which the description ID is not equal to 5 and the description contains both the word "Aluminum" and the word "spindle."</span></span> <span data-ttu-id="67f1e-176">该搜索条件使用 AND 布尔运算符。</span><span class="sxs-lookup"><span data-stu-id="67f1e-176">The search condition uses the AND Boolean operator.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="additional-considerations-for-full-text-queries"></a><a name="Additional_Considerations"></a><span data-ttu-id="67f1e-177">全文查询的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="67f1e-177">Additional Considerations for Full-Text Queries</span></span>  
 <span data-ttu-id="67f1e-178">编写全文查询时还应考虑下列事项:</span><span class="sxs-lookup"><span data-stu-id="67f1e-178">When writing full-text queries also consider the following:</span></span>  
  
-   <span data-ttu-id="67f1e-179">LANGUAGE 选项</span><span class="sxs-lookup"><span data-stu-id="67f1e-179">The LANGUAGE option</span></span>  
  
     <span data-ttu-id="67f1e-180">许多查询词在很大程度上依赖于断字符行为。</span><span class="sxs-lookup"><span data-stu-id="67f1e-180">Many query terms depend heavily on word-breaker behavior.</span></span> <span data-ttu-id="67f1e-181">为了确保您使用的是正确的断字符（和词干分析器）以及同义词库文件，我们建议您指定 LANGUAGE 选项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-181">To ensure that you are using the correct word breaker (and stemmer) and thesaurus file, we recommend that you specify the LANGUAGE option.</span></span> <span data-ttu-id="67f1e-182">有关详细信息，请参阅 [创建全文索引时选择语言](choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-182">For more information, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
-   <span data-ttu-id="67f1e-183">非索引字</span><span class="sxs-lookup"><span data-stu-id="67f1e-183">Stopwords</span></span>  
  
     <span data-ttu-id="67f1e-184">当定义全文查询时，全文引擎会去除搜索条件中的非索引字（也称为干扰词）。</span><span class="sxs-lookup"><span data-stu-id="67f1e-184">When defining a full-text query, the Full-Text Engine discards stopwords (also called noise words) from the search criteria.</span></span> <span data-ttu-id="67f1e-185">非索引字是可能经常出现但通常对搜索特定文本没有帮助的词，如“a”、“and”、“is”或“the”。</span><span class="sxs-lookup"><span data-stu-id="67f1e-185">Stopwords are words such as "a," "and," "is," or "the," that can occur frequently but that typically do not help when searching for particular text.</span></span> <span data-ttu-id="67f1e-186">非索引字在非索引字表中列出。</span><span class="sxs-lookup"><span data-stu-id="67f1e-186">Stopwords are listed in a stoplist.</span></span> <span data-ttu-id="67f1e-187">每个全文索引都与一个特定的非索引字表相关联，该非索引字表决定在进行索引时省略查询或索引中的哪些非索引字。</span><span class="sxs-lookup"><span data-stu-id="67f1e-187">Each full-text index is associated with a specific stoplist, which determines what stopwords are omitted from the query or the index at indexing time.</span></span> <span data-ttu-id="67f1e-188">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-188">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](full-text-search.md).</span></span>  
  
-   <span data-ttu-id="67f1e-189">同义词库</span><span class="sxs-lookup"><span data-stu-id="67f1e-189">The thesaurus</span></span>  
  
     <span data-ttu-id="67f1e-190">FREETEXT 和 FREETEXTTABLE 查询默认情况下使用同义词库。</span><span class="sxs-lookup"><span data-stu-id="67f1e-190">FREETEXT and FREETEXTTABLE queries use the thesaurus by default.</span></span> <span data-ttu-id="67f1e-191">CONTAINS 和 CONTAINSTABLE 支持可选的 THESAURUS 参数。</span><span class="sxs-lookup"><span data-stu-id="67f1e-191">CONTAINS and CONTAINSTABLE support an optional THESAURUS argument.</span></span>  
  
-   <span data-ttu-id="67f1e-192">事例敏感性</span><span class="sxs-lookup"><span data-stu-id="67f1e-192">Case sensitivity</span></span>  
  
     <span data-ttu-id="67f1e-193">全文搜索查询不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="67f1e-193">Full-text search queries are case-insensitive.</span></span> <span data-ttu-id="67f1e-194">但是，在日语中，有许多表示语音的拼字法，其中拼字规范化这一概念与不区分大小写类似，如 kana = 不区分。</span><span class="sxs-lookup"><span data-stu-id="67f1e-194">However, in Japanese, there are multiple phonetic orthographies in which the concept of orthographic normalization is akin to case insensitivity (for example, kana = insensitivity).</span></span> <span data-ttu-id="67f1e-195">这种拼字规范化不受支持。</span><span class="sxs-lookup"><span data-stu-id="67f1e-195">This type of orthographic normalization is not supported.</span></span>  
  

  
##  <a name="querying-varbinarymax-and-xml-columns"></a><a name="varbinary"></a><span data-ttu-id="67f1e-196">查询 varbinary (max) 和 xml 列</span><span class="sxs-lookup"><span data-stu-id="67f1e-196">Querying varbinary(max) and xml Columns</span></span>  
 <span data-ttu-id="67f1e-197">如果 `varbinary(max)`、`varbinary` 或 `xml` 列是全文索引列，则与任何其他全文索引列一样，可以使用全文谓词（CONTAINS 和 FREETEXT）以及函数（CONTAINSTABLE 和 FREETEXTTABLE）来查询该列。</span><span class="sxs-lookup"><span data-stu-id="67f1e-197">If a `varbinary(max)`, `varbinary`, or `xml` column is full-text indexed, it can be queried using the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE), like any other full-text indexed column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="67f1e-198">全文搜索还可以用于图像列。</span><span class="sxs-lookup"><span data-stu-id="67f1e-198">Full-text search also works with image columns.</span></span> <span data-ttu-id="67f1e-199">然而，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将来的版本中将删除 `image` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="67f1e-199">However, the `image` data type will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67f1e-200">请避免在新的开发工作中使用此数据类型，并计划修改当前使用此数据类型的应用程序。</span><span class="sxs-lookup"><span data-stu-id="67f1e-200">Avoid using this data type in new development work, and plan to modify applications that currently use it.</span></span> <span data-ttu-id="67f1e-201">请改用 `varbinary(max)` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="67f1e-201">Use the `varbinary(max)` data type instead.</span></span>  
  
### <a name="varbinarymax-or-varbinary-data"></a><span data-ttu-id="67f1e-202">varbinary(max) 或 varbinary 数据</span><span class="sxs-lookup"><span data-stu-id="67f1e-202">varbinary(max) or varbinary data</span></span>  
 <span data-ttu-id="67f1e-203">单个 `varbinary(max)` 或 `varbinary` 列可以存储多种类型的文档。</span><span class="sxs-lookup"><span data-stu-id="67f1e-203">A single `varbinary(max)` or `varbinary` column can store many types of documents.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="67f1e-204">支持安装了相应筛选器并且在操作系统中可用的任何文档类型。</span><span class="sxs-lookup"><span data-stu-id="67f1e-204">supports any document type for which a filter is installed and available in the operative system.</span></span> <span data-ttu-id="67f1e-205">每个文档的文档类型由该文档的文件扩展名标识。</span><span class="sxs-lookup"><span data-stu-id="67f1e-205">The document type of each document is identified by the file extension of the document.</span></span> <span data-ttu-id="67f1e-206">例如，对于 .doc 文件扩展名，全文搜索将使用支持 Microsoft Word 文档的筛选器。</span><span class="sxs-lookup"><span data-stu-id="67f1e-206">For example, for a .doc file extension, full-text search uses the filter that supports Microsoft Word documents.</span></span> <span data-ttu-id="67f1e-207">有关可用文档类型的列表，请查询 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="67f1e-207">For a list of available document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="67f1e-208">请注意，全文引擎可以利用操作系统中安装的现有筛选器。</span><span class="sxs-lookup"><span data-stu-id="67f1e-208">Note that the Full-Text Engine can leverage existing filters that are installed in the operating system.</span></span> <span data-ttu-id="67f1e-209">在您可以使用操作系统筛选器、断字符和词干分析器之前，您必须将它们加载到服务器实例中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f1e-209">Before you can use operating-system filters, word breakers, and stemmers, you must load them in the server instance, as follows:</span></span>  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 <span data-ttu-id="67f1e-210">若要对 `varbinary(max)` 列创建全文索引，全文引擎需要访问 `varbinary(max)` 列中文档的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="67f1e-210">To create a full-text index on a `varbinary(max)` column, the Full-Text Engine needs access to the file extensions of the documents in the `varbinary(max)` column.</span></span> <span data-ttu-id="67f1e-211">此信息必须存储在一个称为“类型列”的表列中，该列必须与全文索引中的 `varbinary(max)` 列相关联。</span><span class="sxs-lookup"><span data-stu-id="67f1e-211">This information must be stored in a table column, called a type column, that must be associated with the `varbinary(max)` column in the full-text index.</span></span> <span data-ttu-id="67f1e-212">在为文档创建索引时，全文引擎将使用类型列中的文件扩展名来标识要使用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="67f1e-212">When indexing a document, the Full-Text Engine uses the file extension in the type column to identify which filter to use.</span></span>  
  
 
  
### <a name="xml-data"></a><span data-ttu-id="67f1e-213">xml 数据</span><span class="sxs-lookup"><span data-stu-id="67f1e-213">xml data</span></span>  
 <span data-ttu-id="67f1e-214">`xml` 数据类型列仅存储 XML 文档和片段，并且只有 XML 筛选器用于此类文档。</span><span class="sxs-lookup"><span data-stu-id="67f1e-214">An `xml` data type column stores only XML documents and fragments, and only the XML filter is used for the documents.</span></span> <span data-ttu-id="67f1e-215">因此，无需类型列。</span><span class="sxs-lookup"><span data-stu-id="67f1e-215">Therefore, a type column is unnecessary.</span></span> <span data-ttu-id="67f1e-216">在 `xml` 列上，全文索引会为 XML 元素的内容创建索引，但会忽略 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="67f1e-216">On `xml` columns, the full-text index indexes the content of the XML elements, but ignores the XML markup.</span></span> <span data-ttu-id="67f1e-217">不为数值的属性值都会进行全文索引。</span><span class="sxs-lookup"><span data-stu-id="67f1e-217">Attribute values are full-text indexed unless they are numeric values.</span></span> <span data-ttu-id="67f1e-218">元素标记用作标记边界。</span><span class="sxs-lookup"><span data-stu-id="67f1e-218">Element tags are used as token boundaries.</span></span> <span data-ttu-id="67f1e-219">支持包含多种语言的格式正确的 XML 或 HTML 文档和片段。</span><span class="sxs-lookup"><span data-stu-id="67f1e-219">Well-formed XML or HTML documents and fragments containing multiple languages are supported.</span></span>  
  
 <span data-ttu-id="67f1e-220">有关对列进行查询的详细信息 `xml` ，请参阅对[XML 列使用全文搜索](../xml/use-full-text-search-with-xml-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-220">For more information about querying on an `xml` column, see [Use Full-Text Search with XML Columns](../xml/use-full-text-search-with-xml-columns.md).</span></span>  
  
 
  
##  <a name="supported-forms-of-query-terms"></a><a name="supported"></a><span data-ttu-id="67f1e-221">支持的查询词形式</span><span class="sxs-lookup"><span data-stu-id="67f1e-221">Supported Forms of Query Terms</span></span>  
 <span data-ttu-id="67f1e-222">此部分总结了为全文谓词和行集值函数为每种查询提供的支持。</span><span class="sxs-lookup"><span data-stu-id="67f1e-222">This section summarizes the support provided for each form of query by the full-text predicates and rowset-valued functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-223">有关给定查询词的语法，请单击下表“支持”\*\*\*\* 列中的相应链接。</span><span class="sxs-lookup"><span data-stu-id="67f1e-223">For the syntax a given query term, click the corresponding links in **Supported by** column of the following table.</span></span>  
  
|<span data-ttu-id="67f1e-224">查询词形式</span><span class="sxs-lookup"><span data-stu-id="67f1e-224">Query-term form</span></span>|<span data-ttu-id="67f1e-225">说明</span><span class="sxs-lookup"><span data-stu-id="67f1e-225">Description</span></span>|<span data-ttu-id="67f1e-226">支持的服务</span><span class="sxs-lookup"><span data-stu-id="67f1e-226">Supported by</span></span>|  
|----------------------|-----------------|------------------|  
|<span data-ttu-id="67f1e-227">一个或多个特定的词或短语（“简单词”）</span><span class="sxs-lookup"><span data-stu-id="67f1e-227">One or more specific words or phrases (*simple term*)</span></span>|<span data-ttu-id="67f1e-228">在全文搜索中，词（或“标记”\*\*）是其边界由相应的断字符标识、遵循指定语言的语言规则的字符串。</span><span class="sxs-lookup"><span data-stu-id="67f1e-228">In full-text search, a word (or *token*) is a string whose boundaries are identified by appropriate word breakers, following the linguistic rules of the specified language.</span></span> <span data-ttu-id="67f1e-229">有效的短语由多个词组成，词之间可以有标点符号也可以没有标点符号。</span><span class="sxs-lookup"><span data-stu-id="67f1e-229">A valid phrase consists of multiple words, with or without any punctuation marks between them.</span></span><br /><br /> <span data-ttu-id="67f1e-230">例如，"新月形面包" 是一个词，"caf？"</span><span class="sxs-lookup"><span data-stu-id="67f1e-230">For example, "croissant" is a word, and "caf??</span></span> <span data-ttu-id="67f1e-231">au lait "是一个短语。</span><span class="sxs-lookup"><span data-stu-id="67f1e-231">au lait" is a phrase.</span></span> <span data-ttu-id="67f1e-232">这样的词和短语称为“简单词”。</span><span class="sxs-lookup"><span data-stu-id="67f1e-232">Words and phrases such as these are called simple terms.</span></span><br /><br /> <span data-ttu-id="67f1e-233">有关详细信息，请参阅本主题后面的 [搜索特定的词或短语（简单词）](#Simple_Term)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-233">For more information, see [Searching for Specific word or Phrase (Simple Term)](#Simple_Term), later in this topic.</span></span>|<span data-ttu-id="67f1e-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 查找短语的完全匹配项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) look for an exact match for the phrase.</span></span><br /><br /> <span data-ttu-id="67f1e-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 和 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 将短语拆分为几个词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) break up the phrase into separate words.</span></span>|  
|<span data-ttu-id="67f1e-236">以指定文本开头的词或短语（“前缀词”）</span><span class="sxs-lookup"><span data-stu-id="67f1e-236">A word or a phrase where the words begin with specified text (*prefix term*)</span></span>|<span data-ttu-id="67f1e-237">前缀词指附加到一个词的前面以生成一个派生词或变形的字符串。</span><span class="sxs-lookup"><span data-stu-id="67f1e-237">A prefix term refers to a string that is affixed to the front of a word to produce a derivative word or an inflected form.</span></span><br /><br /> <span data-ttu-id="67f1e-238">对于单个前缀词，以指定词开头的任何词将是结果集的一部分。</span><span class="sxs-lookup"><span data-stu-id="67f1e-238">For a single prefix term, any word starting with the specified term will be part of the result set.</span></span> <span data-ttu-id="67f1e-239">例如，词“auto\*”与“automatic”、“automobile”等匹配。</span><span class="sxs-lookup"><span data-stu-id="67f1e-239">For example, the term "auto\*" matches "automatic", "automobile", and so forth.</span></span><br /><br /> <span data-ttu-id="67f1e-240">如果是短语，则该短语内的每个词都被看作是一个前缀。</span><span class="sxs-lookup"><span data-stu-id="67f1e-240">For a phrase, each word within the phrase is considered to be a prefix term.</span></span> <span data-ttu-id="67f1e-241">例如，词“auto tran\*”与“automatic transmission”和“automobile transducer”匹配，但与“automatic motor transmission”不匹配。</span><span class="sxs-lookup"><span data-stu-id="67f1e-241">For example, the term "auto tran\*" matches "automatic transmission" and "automobile transducer", but it does not match "automatic motor transmission".</span></span><br /><br /> <span data-ttu-id="67f1e-242">有关详细信息，请参阅本主题后面的 [执行前缀搜索（前缀词）](#Prefix_Term)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-242">For more information, see [Performing Prefix Searches (Prefix Term)](#Prefix_Term), later in this topic.</span></span>|<span data-ttu-id="67f1e-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="67f1e-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="67f1e-244"> (生成术语的特定单词的变形形式 *-变形*) </span><span class="sxs-lookup"><span data-stu-id="67f1e-244">Inflectional forms of a specific word (*generation term-inflectional*)</span></span>|<span data-ttu-id="67f1e-245">变形是动词的不同时态和语态形式，或是名词的单数和复数形式。</span><span class="sxs-lookup"><span data-stu-id="67f1e-245">The inflectional forms are the different tenses and conjugations of a verb or the singular and plural forms of a noun.</span></span> <span data-ttu-id="67f1e-246">例如，搜索词“drive”的变形。</span><span class="sxs-lookup"><span data-stu-id="67f1e-246">For example, search for the inflectional form of the word "drive".</span></span> <span data-ttu-id="67f1e-247">如果表中不同的行包含词“drive”、“drives”、“drove”、“driving”和“driven”，则这些词都会出现在结果集中，原因是它们每一个都可以从词 drive 变形而来。</span><span class="sxs-lookup"><span data-stu-id="67f1e-247">If various rows in the table include the words "drive", "drives", "drove", "driving", and "driven", all would be in the result set because each of these can be inflectionally generated from the word drive.</span></span><br /><br /> <span data-ttu-id="67f1e-248">有关详细信息，请参阅本主题后面的 [搜索特定词的变形（派生词）](#Inflectional_Generation_Term)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-248">For more information, see [Searching for the Inflectional Form of a Specific Word (Generation Term)](#Inflectional_Generation_Term), later in this topic.</span></span>|<span data-ttu-id="67f1e-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql)和[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)在默认情况下查找所有指定词的变形术语。</span><span class="sxs-lookup"><span data-stu-id="67f1e-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) look for inflectional terms of all specified words by default.</span></span><br /><br /> <span data-ttu-id="67f1e-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 支持可选的 INFLECTIONAL 参数。</span><span class="sxs-lookup"><span data-stu-id="67f1e-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional INFLECTIONAL argument.</span></span>|  
|<span data-ttu-id="67f1e-251"> (*生成词同义词库*的特定单词的同义词窗体) </span><span class="sxs-lookup"><span data-stu-id="67f1e-251">Synonymous forms of a specific word (*generation term-thesaurus*)</span></span>|<span data-ttu-id="67f1e-252">同义词库为词定义用户指定的同义词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-252">A thesaurus defines user-specified synonyms for terms.</span></span> <span data-ttu-id="67f1e-253">例如，如果将项“{car, automobile, truck, van}”添加到同义词库，则可以搜索单词“car”的同义词库形式。</span><span class="sxs-lookup"><span data-stu-id="67f1e-253">For example, if an entry, "{car, automobile, truck, van}", is added to a thesaurus, you can search for the thesaurus form of the word "car".</span></span> <span data-ttu-id="67f1e-254">由于这些单词中的每一个都属于包含单词“car”的同义词扩展集，因此在所查询的表中所有包括单词“automobile”、“truck”、“van”或“car”的行都会出现在结果集中。</span><span class="sxs-lookup"><span data-stu-id="67f1e-254">All rows in the table queried that include the words "automobile", "truck", "van", or "car", appear in the result set because each of these words belong to the synonym expansion set containing the word "car".</span></span><br /><br /> <span data-ttu-id="67f1e-255">有关同义词库文件的结构的信息，请参阅 [配置和管理全文搜索同义词库文件](configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-255">For information about the structure of thesaurus files, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>|<span data-ttu-id="67f1e-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql)和[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)在默认情况下使用同义词库。</span><span class="sxs-lookup"><span data-stu-id="67f1e-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) use the thesaurus by default.</span></span><br /><br /> <span data-ttu-id="67f1e-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql)和[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)支持可选的同义词库参数。</span><span class="sxs-lookup"><span data-stu-id="67f1e-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional THESAURUS argument.</span></span>|  
|<span data-ttu-id="67f1e-258">与另一个词或短语邻近的词或短语（“邻近词”）</span><span class="sxs-lookup"><span data-stu-id="67f1e-258">A word or phrase close to another word or phrase (*proximity term*)</span></span>|<span data-ttu-id="67f1e-259">邻近词表示相邻的词或短语。还可以指定在第一个搜索词与最后一个搜索之间最多可以有几个非搜索词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-259">A proximity term indicates words or phrases that are near to each other., You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="67f1e-260">此外，可以以任意顺序或您指定的顺序搜索词或短语。</span><span class="sxs-lookup"><span data-stu-id="67f1e-260">In addition, you can search for words or phrases in any order, or in the order in which you specify them.</span></span><br /><br /> <span data-ttu-id="67f1e-261">例如，查找词“ice”与“hockey”邻近或短语“ice skating”与“ice hockey”邻近的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-261">For example, you want to find the rows in which the word "ice" is near the word "hockey" or in which the phrase "ice skating" is near the phrase "ice hockey".</span></span><br /><br /> <span data-ttu-id="67f1e-262">有关详细信息，请参阅 [使用 NEAR 搜索与另一个词邻近的词](search-for-words-close-to-another-word-with-near.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-262">For more information, see [Search for Words Close to Another Word with NEAR](search-for-words-close-to-another-word-with-near.md).</span></span>|<span data-ttu-id="67f1e-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="67f1e-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="67f1e-264">使用加权值的词或短语（“加权词”）</span><span class="sxs-lookup"><span data-stu-id="67f1e-264">Words or phrases using weighted values (*weighted term*)</span></span>|<span data-ttu-id="67f1e-265">加权值指示一组词和短语中的每个词和短语的重要程度。</span><span class="sxs-lookup"><span data-stu-id="67f1e-265">A weighting value that indicates the degree of importance for each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="67f1e-266">加权值的最低值是 0.0，最高值是 1.0。</span><span class="sxs-lookup"><span data-stu-id="67f1e-266">A weight value of 0.0 is the lowest, and a weight value of 1.0 is the highest.</span></span><br /><br /> <span data-ttu-id="67f1e-267">例如，在某个搜索多个词条的查询中，可以为每个搜索单词指定一个加权值，用于指示它相对于搜索条件中其他单词的重要性。</span><span class="sxs-lookup"><span data-stu-id="67f1e-267">For example, in a query searching for multiple terms, you can assign each search word a weight value indicating its importance relative to the other words in the search condition.</span></span> <span data-ttu-id="67f1e-268">此查询类型的结果将按指定给搜索单词的相对权重首先返回最相关的行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-268">The results for this type of query return the most relevant rows first, according to the relative weight you have assigned to search words.</span></span> <span data-ttu-id="67f1e-269">结果集由包含任何指定词（或它们之间的内容）的文档或行组成；但是，由于与不同搜索词关联的加权值的不同，某些结果将被视为比其他结果更相关。</span><span class="sxs-lookup"><span data-stu-id="67f1e-269">The result sets contain documents or rows containing any of the specified terms (or content between them); however, some results will be considered more relevant than others because of the variation in the weighted values associated with different searched terms.</span></span><br /><br /> <span data-ttu-id="67f1e-270">有关详细信息，请参阅本主题后面的 [使用加权值搜索词或短语（加权词）](#Weighted_Term)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-270">For more information, see [Searching for Words or Phrases Using Weighted Values (Weighted Term)](#Weighted_Term), later in this topic.</span></span>|[<span data-ttu-id="67f1e-271">CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="67f1e-271">CONTAINSTABLE</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="searching-for-specific-word-or-phrase-simple-term"></a><a name="Simple_Term"></a><span data-ttu-id="67f1e-272">搜索特定的词或短语 (简单术语) </span><span class="sxs-lookup"><span data-stu-id="67f1e-272">Searching for Specific Word or Phrase (Simple Term)</span></span>  
 <span data-ttu-id="67f1e-273">可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)或 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 在表中搜索特定短语。</span><span class="sxs-lookup"><span data-stu-id="67f1e-273">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search a table for a specific phrase.</span></span> <span data-ttu-id="67f1e-274">例如，如果要在 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库的 `ProductReview` 表中进行搜索，以查找关于某种产品的包含“learning curve”短语的所有注释，可以使用 CONTAINS 谓词，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f1e-274">For example, if you want to search the `ProductReview` table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to find all comments about a product with the phrase "learning curve", you could use the CONTAINS predicate as follows:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 <span data-ttu-id="67f1e-275">搜索条件（在本例中是“learning curve”）可以很复杂，可由一项或多项组成。</span><span class="sxs-lookup"><span data-stu-id="67f1e-275">The search condition, in this case "learning curve", can be quite complex and can be composed of one or more terms</span></span>  
  
 
  
###  <a name="performing-prefix-searches-prefix-term"></a><a name="Prefix_Term"></a> <span data-ttu-id="67f1e-276">(前缀术语) 执行前缀搜索</span><span class="sxs-lookup"><span data-stu-id="67f1e-276">Performing Prefix Searches (Prefix Term)</span></span>  
 <span data-ttu-id="67f1e-277">可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 或 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 来搜索具有指定前缀的词或短语。</span><span class="sxs-lookup"><span data-stu-id="67f1e-277">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql) or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases with a specified prefix.</span></span> <span data-ttu-id="67f1e-278">将返回列中所有包含以指定前缀开头的文本的项。</span><span class="sxs-lookup"><span data-stu-id="67f1e-278">All entries in the column that contain text beginning with the specified prefix are returned.</span></span> <span data-ttu-id="67f1e-279">例如，要搜索包含前缀 `top`- 的所有行，如 `top``ple`、 `top``ping`和 `top`。</span><span class="sxs-lookup"><span data-stu-id="67f1e-279">For example, to search for all rows that contain the prefix `top`-, as in `top``ple`, `top``ping`, and `top`.</span></span> <span data-ttu-id="67f1e-280">该查询如下所示：</span><span class="sxs-lookup"><span data-stu-id="67f1e-280">The query looks like this:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 <span data-ttu-id="67f1e-281">将会返回所有与星号 (\*) 之前指定的文本相匹配的文本。</span><span class="sxs-lookup"><span data-stu-id="67f1e-281">All text that matches the text specified before the asterisk (\*) is returned.</span></span> <span data-ttu-id="67f1e-282">如果未在文本和星号前后加上双引号标记（如 `CONTAINS (DESCRIPTION, 'top*')`），则全文搜索将不把星号当作通配符。</span><span class="sxs-lookup"><span data-stu-id="67f1e-282">If the text and asterisk are not delimited by double quotation marks, as in `CONTAINS (DESCRIPTION, 'top*')`, full-text search does not consider the asterisk to be a wildcard..</span></span>  
  
 <span data-ttu-id="67f1e-283">当前缀词是短语时，组成该短语的每个标记均被看作是单独的前缀词。</span><span class="sxs-lookup"><span data-stu-id="67f1e-283">When the prefix term is a phrase, each token making up the phrase is considered a separate prefix term.</span></span> <span data-ttu-id="67f1e-284">将返回包含以这些前缀词开头的词的所有行。</span><span class="sxs-lookup"><span data-stu-id="67f1e-284">All rows that have words beginning with the prefix terms will be returned.</span></span> <span data-ttu-id="67f1e-285">例如，前缀词“light bread\*”将查找带有“light breaded”、“lightly breaded”或“light bread”文本的行，但不会返回“lightly toasted bread”。</span><span class="sxs-lookup"><span data-stu-id="67f1e-285">For example, the prefix term "light bread\*" will find rows with text of "light breaded," "lightly breaded," or "light bread," but it will not return "lightly toasted bread".</span></span>  
  
 
  
###  <a name="searching-for-inflectional-forms-of-a-specific-word-generation-term"></a><a name="Inflectional_Generation_Term"></a><span data-ttu-id="67f1e-286">搜索特定词 (生成词) 的变形形式</span><span class="sxs-lookup"><span data-stu-id="67f1e-286">Searching for Inflectional Forms of a Specific Word (Generation Term)</span></span>  
 <span data-ttu-id="67f1e-287">可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)或 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 搜索动词的所有不同时态和语态形式或搜索名词的单数和复数形式（变形搜索）或者搜索特定词的同义词形式（同义词库搜索）。</span><span class="sxs-lookup"><span data-stu-id="67f1e-287">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search for all the different tenses and conjugations of a verb or both the singular and plural forms of a noun (an inflectional search) or for synonymous forms of a specific word (a thesaurus search).</span></span>  
  
 <span data-ttu-id="67f1e-288">以下示例在 `Comments` 数据库的 `ProductReview` 表的 `AdventureWorks` 列搜索“foot”的任意变形（“foot”、“feet”等）：</span><span class="sxs-lookup"><span data-stu-id="67f1e-288">The following example searches for any form of "foot" ("foot", "feet", and so on) in the `Comments` column of the `ProductReview` table in the `AdventureWorks` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="67f1e-289">全文搜索使用词干分析器，它允许您搜索某个动词的不同时态和语态形式，或搜索某个名词的单数和复数形式。</span><span class="sxs-lookup"><span data-stu-id="67f1e-289">Full-text search uses stemmers, which allow you to search for the different tenses and conjugations of a verb, or both the singular and plural forms of a noun.</span></span> <span data-ttu-id="67f1e-290">有关词干分析器的详细信息，请参阅 [配置和管理断字符和词干分析器以便搜索](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-290">For more information about stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  

  
###  <a name="searching-for-words-or-phrases-using-weighted-values-weighted-term"></a><a name="Weighted_Term"></a><span data-ttu-id="67f1e-291">使用加权值搜索词或短语 (加权术语) </span><span class="sxs-lookup"><span data-stu-id="67f1e-291">Searching for Words or Phrases Using Weighted Values (Weighted Term)</span></span>  
 <span data-ttu-id="67f1e-292">您可以使用 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 来搜索词或短语并指定加权值。</span><span class="sxs-lookup"><span data-stu-id="67f1e-292">You can use [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases and specify a weighting value.</span></span> <span data-ttu-id="67f1e-293">加权值用介于 0.0 到 1.0 之间的一个数字来表示，用于指示一组词和短语中的每个词和短语的重要程度。</span><span class="sxs-lookup"><span data-stu-id="67f1e-293">Weight, measured as a number from 0.0 through 1.0, indicates the importance of each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="67f1e-294">加权值的最低值是 0.0，最高值是 1.0。</span><span class="sxs-lookup"><span data-stu-id="67f1e-294">A weight of 0.0 is the lowest, and a weight of 1.0 is the highest.</span></span>  
  
 <span data-ttu-id="67f1e-295">下例所示的查询使用加权值搜索所有符合以下条件的客户地址：地址中任何以字符串“Bay”开头的文本包含“Street”或“View”。</span><span class="sxs-lookup"><span data-stu-id="67f1e-295">The following example shows a query that searches for all customer addresses, using weights, in which any text beginning with the string "Bay" has either "Street" or "View".</span></span> <span data-ttu-id="67f1e-296">在结果中，对那些包含较多指定词的行赋予较高的排名。</span><span class="sxs-lookup"><span data-stu-id="67f1e-296">The results give a higher rank to those rows that contain more of the words specified.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="67f1e-297">加权词可以与任意简单词、前缀词、派生词或邻近词一起使用。</span><span class="sxs-lookup"><span data-stu-id="67f1e-297">A weighted term can be used in conjunction with any simple term, prefix term, generation term, or proximity term.</span></span>  
  

  
##  <a name="viewing-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a><a name="tokens"></a><span data-ttu-id="67f1e-298">查看断字符、同义词库和非索引字表组合的词汇切分结果</span><span class="sxs-lookup"><span data-stu-id="67f1e-298">Viewing the Tokenization Result of a Word Breaker, Thesaurus, and Stoplist Combination</span></span>  
 <span data-ttu-id="67f1e-299">对查询字符串输入应用给定的断字符、同义词库和非索引字表组合后，可以使用 **sys.dm_fts_parser** 动态管理视图查看词汇切分结果。</span><span class="sxs-lookup"><span data-stu-id="67f1e-299">After applying a given word breaker, thesaurus, and stoplist combination to a query string input, you can view the tokenization result by using the **sys.dm_fts_parser** dynamic management view.</span></span> <span data-ttu-id="67f1e-300">有关详细信息，请参阅[sys.dm_fts_parser (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="67f1e-300">For more information, see [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="67f1e-301">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67f1e-301">See Also</span></span>  
 <span data-ttu-id="67f1e-302">[CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f1e-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="67f1e-303">[CONTAINSTABLE (Transact-SQL)](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f1e-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="67f1e-304">[FREETEXT (Transact-SQL)](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f1e-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="67f1e-305">[FREETEXTTABLE (Transact-SQL)](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="67f1e-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 <span data-ttu-id="67f1e-306">[创建全文搜索查询 (Visual Database Tools)](../../ssms/visual-db-tools/visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="67f1e-306">[Create Full-Text Search Queries &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span></span>  
 [<span data-ttu-id="67f1e-307">改进全文查询的性能</span><span class="sxs-lookup"><span data-stu-id="67f1e-307">Improve the Performance of Full-Text Queries</span></span>](improve-the-performance-of-full-text-queries.md)  
  
  
