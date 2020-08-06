---
title: 使用 RANK 限制搜索结果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- row ranking [full-text search]
- relevance ranking values [full-text search]
- full-text search [SQL Server], rankings
- index rankings [full-text search]
- ranked results [full-text search]
- rankings [full-text search]
- per-row rank values [full-text search]
ms.assetid: 06a776e6-296c-4ec7-9fa5-0794709ccb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1b930b3238cb541965e1984d1561f1a1c22d87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690462"
---
# <a name="limit-search-results-with-rank"></a><span data-ttu-id="fd23d-102">使用 RANK 限制搜索结果</span><span class="sxs-lookup"><span data-stu-id="fd23d-102">Limit Search Results with RANK</span></span>
  <span data-ttu-id="fd23d-103">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 和 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 函数返回名为 RANK 的列，该列包含从 0 到 1000 的序数值（排名值）。</span><span class="sxs-lookup"><span data-stu-id="fd23d-103">The [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) functions return a column named RANK that contains ordinal values from 0 through 1000 (rank values).</span></span> <span data-ttu-id="fd23d-104">这些值用来根据返回的行与选择条件的匹配程度对这些行进行排名。</span><span class="sxs-lookup"><span data-stu-id="fd23d-104">These values are used to rank the rows returned according to how well they match the selection criteria.</span></span> <span data-ttu-id="fd23d-105">排名值仅表示结果集中各行相关性的相对顺序，值越小，表示相关性越低。</span><span class="sxs-lookup"><span data-stu-id="fd23d-105">The rank values indicate only a relative order of relevance of the rows in the result set, with a lower value indicating lower relevance.</span></span> <span data-ttu-id="fd23d-106">实际的值并不重要，并且每次运行查询时实际值通常都不同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-106">The actual values are unimportant and typically differ each time the query is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd23d-107">CONTAINS 和 FREETEXT 谓词不会返回任何排名值。</span><span class="sxs-lookup"><span data-stu-id="fd23d-107">The CONTAINS and FREETEXT predicates do not return any rank values.</span></span>  
  
 <span data-ttu-id="fd23d-108">符合搜索条件的项通常有很多。</span><span class="sxs-lookup"><span data-stu-id="fd23d-108">The number of items matching a search condition is often very large.</span></span> <span data-ttu-id="fd23d-109">为防止 CONTAINSTABLE 或 FREETEXTTABLE 查询返回太多匹配项，请使用可选的 *top_n_by_rank* 参数，此参数仅返回行的子集。</span><span class="sxs-lookup"><span data-stu-id="fd23d-109">To prevent CONTAINSTABLE or FREETEXTTABLE queries from returning too many matches, use the optional *top_n_by_rank* parameter, which returns only a subset of rows.</span></span> <span data-ttu-id="fd23d-110">*top_n_by_rank* 是一个整数值 *n*，它指定仅返回 *n* 个排名值最高的匹配项，并按降序排列。</span><span class="sxs-lookup"><span data-stu-id="fd23d-110">*top_n_by_rank* is an integer value, *n*, that specifies that only the *n* highest ranked matches are to be returned, in descending order.</span></span> <span data-ttu-id="fd23d-111">如果 *top_n_by_rank* 与其他参数组合使用，则查询返回的行数可能会少于实际与所有谓词都匹配的行数。</span><span class="sxs-lookup"><span data-stu-id="fd23d-111">If *top_n_by_rank* is combined with other parameters, the query could return fewer rows than the number of rows that actually match all the predicates.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="fd23d-112">按排名对匹配项进行排序，并且最多只返回指定数目的行。</span><span class="sxs-lookup"><span data-stu-id="fd23d-112">orders the matches by rank and returns only up to the specified number of rows.</span></span> <span data-ttu-id="fd23d-113">这样可以大幅度提高性能。</span><span class="sxs-lookup"><span data-stu-id="fd23d-113">This choice can result in a dramatic increase in performance.</span></span> <span data-ttu-id="fd23d-114">例如，对于正常情况下会从一个包含一百万行的表中返回 100,000 行的查询，如果只要求返回前 100 行，此查询的处理速度会更快。</span><span class="sxs-lookup"><span data-stu-id="fd23d-114">For example, a query that would normally return 100,000 rows from a table of one million rows are processed more quickly if only the top 100 rows are requested.</span></span>  
  
##  <a name="examples-of-using-rank-to-limit-search-results"></a><a name="examples"></a> <span data-ttu-id="fd23d-115">使用 RANK 限制搜索结果的示例</span><span class="sxs-lookup"><span data-stu-id="fd23d-115">Examples of Using RANK to Limit Search Results</span></span>  
  
### <a name="example-a-searching-for-only-the-top-three-matches"></a><span data-ttu-id="fd23d-116">示例 A：仅搜索前三个匹配项</span><span class="sxs-lookup"><span data-stu-id="fd23d-116">Example A: Searching for only the top three matches</span></span>  
 <span data-ttu-id="fd23d-117">下面的示例使用 CONTAINSTABLE 仅返回前三个匹配项。</span><span class="sxs-lookup"><span data-stu-id="fd23d-117">The following example uses CONTAINSTABLE to return only the top three matches.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT K.RANK, AddressLine1, City  
FROM Person.Address AS A  
  INNER JOIN  
  CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("des*",  
    Rue WEIGHT(0.5),  
    Bouchers WEIGHT(0.9))',  
    3) AS K  
  ON A.AddressID = K.[KEY]  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
RANK        Address                          City  
----------- -------------------------------- ------------------------------  
172         9005, rue des Bouchers           Paris  
172         5, rue des Bouchers              Orleans  
172         5, rue des Bouchers              Metz  
  
(3 row(s) affected)  
```  
  
  
### <a name="example-b-searching-for-the-top-ten-matches"></a><span data-ttu-id="fd23d-118">示例 B：搜索前十个匹配项</span><span class="sxs-lookup"><span data-stu-id="fd23d-118">Example B: Searching for the top ten matches</span></span>  
 <span data-ttu-id="fd23d-119">下面的示例使用 CONTAINSTABLE 返回前 5 个产品的说明，其中 `Description` 列在单词“light”或“lightweight”附近包含字词“aluminum”。</span><span class="sxs-lookup"><span data-stu-id="fd23d-119">The following example uses CONTAINSTABLE to return the description of the top 5 products where the `Description` column contains the word "aluminum" near either the word "light" or the word "lightweight".</span></span>  
  
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
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
GO  
```  
  
  
##  <a name="how-search-query-results-are-ranked"></a><a name="how"></a> <span data-ttu-id="fd23d-120">搜索查询结果如何进行排名</span><span class="sxs-lookup"><span data-stu-id="fd23d-120">How Search Query Results Are Ranked</span></span>  
 <span data-ttu-id="fd23d-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的全文搜索可以生成可选分数（或排名值），该分数（或排名值）指示全文查询返回的数据的相关性。</span><span class="sxs-lookup"><span data-stu-id="fd23d-121">Full-text search in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can generate an optional score (or rank value) that indicates the relevance of the data returned by a full-text query.</span></span> <span data-ttu-id="fd23d-122">对于每一行计算此排名值，并且可将此排名值用作排序条件按相关性对给定查询的结果集排序。</span><span class="sxs-lookup"><span data-stu-id="fd23d-122">This rank value is calculated on every row and can be used as an ordering criteria to sort the result set of a given query by relevance.</span></span> <span data-ttu-id="fd23d-123">此排名值仅指示结果集中各行相关性的相对顺序。</span><span class="sxs-lookup"><span data-stu-id="fd23d-123">The rank values indicate only a relative order of relevance of the rows in the result set.</span></span> <span data-ttu-id="fd23d-124">实际的值并不重要，并且每次运行查询时实际值通常都不同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-124">The actual values are unimportant and typically differ each time the query is run.</span></span> <span data-ttu-id="fd23d-125">此排名值在不同的查询之间没有任何意义。</span><span class="sxs-lookup"><span data-stu-id="fd23d-125">The rank value does not hold any significance across queries.</span></span>  
  
### <a name="statistics-for-ranking"></a><span data-ttu-id="fd23d-126">排名统计信息</span><span class="sxs-lookup"><span data-stu-id="fd23d-126">Statistics for Ranking</span></span>  
 <span data-ttu-id="fd23d-127">生成索引后，将收集统计信息以用于排名。</span><span class="sxs-lookup"><span data-stu-id="fd23d-127">When an index is built, statistics are collected for use in ranking.</span></span> <span data-ttu-id="fd23d-128">生成全文目录的过程不会直接得出一个索引结构。</span><span class="sxs-lookup"><span data-stu-id="fd23d-128">The process of building a full-text catalog does not directly result in a single index structure.</span></span> <span data-ttu-id="fd23d-129">而是在对数据创建索引时，由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的全文引擎创建多个中间索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-129">Instead, the Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] creates intermediate indexes as data is indexed.</span></span> <span data-ttu-id="fd23d-130">全文引擎随后会将这些索引根据需要合并为一个较大的索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-130">The Full-Text Engine then merges these indexes into a larger index as needed.</span></span> <span data-ttu-id="fd23d-131">此过程可以多次重复。</span><span class="sxs-lookup"><span data-stu-id="fd23d-131">This process can be repeated many times.</span></span> <span data-ttu-id="fd23d-132">最后，全文引擎将进行“主合并”，将所有中间索引合并为一个较大的主索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-132">The Full-Text Engine then conducts a "master merge" that combines all of the intermediate indexes into one large master index.</span></span>  
  
 <span data-ttu-id="fd23d-133">在每个中间索引级别都会收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="fd23d-133">Statistics are collected at each intermediate index level.</span></span> <span data-ttu-id="fd23d-134">合并索引时，统计信息也将被合并。</span><span class="sxs-lookup"><span data-stu-id="fd23d-134">The statistics are merged when the indexes are merged.</span></span> <span data-ttu-id="fd23d-135">某些统计值只有在主合并过程中才能生成。</span><span class="sxs-lookup"><span data-stu-id="fd23d-135">Some statistical values can only be generated during the master merging process.</span></span>  
  
 <span data-ttu-id="fd23d-136">对查询结果集排名时， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将使用最大中间索引的统计信息。</span><span class="sxs-lookup"><span data-stu-id="fd23d-136">While ranking a query result set, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses statistics from the largest intermediate index.</span></span> <span data-ttu-id="fd23d-137">这取决于是否合并了中间索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-137">This depends on whether intermediate indexes have been merged or not.</span></span> <span data-ttu-id="fd23d-138">因此，如果未合并中间索引，则排名统计信息在准确性上会有变化。</span><span class="sxs-lookup"><span data-stu-id="fd23d-138">As a result, ranking statistics can vary in accuracy if the intermediate indexes have not been merged.</span></span> <span data-ttu-id="fd23d-139">这解释了为什么随着全文索引数据的添加、修改和删除，以及较小索引的合并，同样的查询会返回不同的排名结果。</span><span class="sxs-lookup"><span data-stu-id="fd23d-139">This explains why the same query can return different rank results over time as full-text indexed data is added, modified, and deleted, and as the smaller indexes are merged.</span></span>  
  
 <span data-ttu-id="fd23d-140">为了尽量减小索引大小以及尽量降低计算的复杂程度，经常会对统计信息进行舍入。</span><span class="sxs-lookup"><span data-stu-id="fd23d-140">To minimize the size of the index and computational complexity, statistics are often rounded.</span></span>  
  
 <span data-ttu-id="fd23d-141">下表包含了对计算排名非常重要的一些常用术语和统计值。</span><span class="sxs-lookup"><span data-stu-id="fd23d-141">The list below includes some commonly used terms and statistical values that are important in calculating rank.</span></span>  
  
 <span data-ttu-id="fd23d-142">properties</span><span class="sxs-lookup"><span data-stu-id="fd23d-142">Property</span></span>  
 <span data-ttu-id="fd23d-143">行的全文索引列。</span><span class="sxs-lookup"><span data-stu-id="fd23d-143">A full-text indexed column of the row.</span></span>  
  
 <span data-ttu-id="fd23d-144">Document</span><span class="sxs-lookup"><span data-stu-id="fd23d-144">Document</span></span>  
 <span data-ttu-id="fd23d-145">在查询中返回的实体。</span><span class="sxs-lookup"><span data-stu-id="fd23d-145">The entity that is returned in queries.</span></span> <span data-ttu-id="fd23d-146">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，此实体对应于一行。</span><span class="sxs-lookup"><span data-stu-id="fd23d-146">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] this corresponds to a row.</span></span> <span data-ttu-id="fd23d-147">正如一行可以具有多个全文索引列一样，一个文档也可以具有多个属性。</span><span class="sxs-lookup"><span data-stu-id="fd23d-147">A document can have multiple properties, just as a row can have multiple full-text indexed columns.</span></span>  
  
 <span data-ttu-id="fd23d-148">索引</span><span class="sxs-lookup"><span data-stu-id="fd23d-148">Index</span></span>  
 <span data-ttu-id="fd23d-149">一个或多个文档的单个倒排索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-149">A single inverted index of one or more documents.</span></span> <span data-ttu-id="fd23d-150">此索引可以整个位于内存中或整个位于磁盘上。</span><span class="sxs-lookup"><span data-stu-id="fd23d-150">This may be entirely in memory or on disk.</span></span> <span data-ttu-id="fd23d-151">许多查询统计信息都与匹配的那个索引相关。</span><span class="sxs-lookup"><span data-stu-id="fd23d-151">Many query statistics are relative to the individual index where the match occurred.</span></span>  
  
 <span data-ttu-id="fd23d-152">全文目录</span><span class="sxs-lookup"><span data-stu-id="fd23d-152">Full-Text Catalog</span></span>  
 <span data-ttu-id="fd23d-153">当作一个查询实体来处理的中间索引的集合。</span><span class="sxs-lookup"><span data-stu-id="fd23d-153">A collection of intermediate indexes treated as one entity for queries.</span></span> <span data-ttu-id="fd23d-154">目录是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理员可以看到的组织结构单位。</span><span class="sxs-lookup"><span data-stu-id="fd23d-154">Catalogs are the unit of organization visible to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="fd23d-155">词、标记或项</span><span class="sxs-lookup"><span data-stu-id="fd23d-155">Word, token or item</span></span>  
 <span data-ttu-id="fd23d-156">全文引擎中的匹配单位。</span><span class="sxs-lookup"><span data-stu-id="fd23d-156">The unit of matching in the full-text engine.</span></span> <span data-ttu-id="fd23d-157">文档中的文本流将由特定语言的断字符词汇切分为词或标记。</span><span class="sxs-lookup"><span data-stu-id="fd23d-157">Streams of text from documents are tokenized into words, or tokens by language-specific word breakers.</span></span>  
  
 <span data-ttu-id="fd23d-158">出现次数</span><span class="sxs-lookup"><span data-stu-id="fd23d-158">Occurrence</span></span>  
 <span data-ttu-id="fd23d-159">文档属性中的词偏移量取决于断字符。</span><span class="sxs-lookup"><span data-stu-id="fd23d-159">The word offset in a document property as determined by the word breaker.</span></span> <span data-ttu-id="fd23d-160">第一个词出现在位置 1，下一个词出现在位置 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="fd23d-160">The first word is at occurrence 1, the next at 2, and so on.</span></span> <span data-ttu-id="fd23d-161">为避免在短语和邻近查询中出现假正数，句子结尾和段落结尾引入了较大的位置间隔。</span><span class="sxs-lookup"><span data-stu-id="fd23d-161">In order to avoid false positives in phrase and proximity queries, end-of-sentence and end-of-paragraph introduce larger occurrence gaps.</span></span>  
  
 <span data-ttu-id="fd23d-162">TermFrequency</span><span class="sxs-lookup"><span data-stu-id="fd23d-162">TermFrequency</span></span>  
 <span data-ttu-id="fd23d-163">此数值记录了键值在某一行中出现的次数。</span><span class="sxs-lookup"><span data-stu-id="fd23d-163">The number times the key value occurs in a row.</span></span>  
  
 <span data-ttu-id="fd23d-164">IndexedRowCount</span><span class="sxs-lookup"><span data-stu-id="fd23d-164">IndexedRowCount</span></span>  
 <span data-ttu-id="fd23d-165">索引行总数。</span><span class="sxs-lookup"><span data-stu-id="fd23d-165">Total number of rows indexed.</span></span> <span data-ttu-id="fd23d-166">此数值基于中间索引中维护的计数来计算。</span><span class="sxs-lookup"><span data-stu-id="fd23d-166">This is computed, based on counts maintained in the intermediate indexes.</span></span> <span data-ttu-id="fd23d-167">此数值在准确性上会有变化。</span><span class="sxs-lookup"><span data-stu-id="fd23d-167">This number can vary in accuracy.</span></span>  
  
 <span data-ttu-id="fd23d-168">KeyRowCount</span><span class="sxs-lookup"><span data-stu-id="fd23d-168">KeyRowCount</span></span>  
 <span data-ttu-id="fd23d-169">全文目录中包含给定键的总行数。</span><span class="sxs-lookup"><span data-stu-id="fd23d-169">Total number of rows in the full-text catalog that contain a given key.</span></span>  
  
 <span data-ttu-id="fd23d-170">MaxOccurrence</span><span class="sxs-lookup"><span data-stu-id="fd23d-170">MaxOccurrence</span></span>  
 <span data-ttu-id="fd23d-171">某一行中的给定属性在全文目录中偏移量最大的位置。</span><span class="sxs-lookup"><span data-stu-id="fd23d-171">The largest occurrence stored in a full-text catalog for a given property in a row.</span></span>  
  
 <span data-ttu-id="fd23d-172">MaxQueryRank</span><span class="sxs-lookup"><span data-stu-id="fd23d-172">MaxQueryRank</span></span>  
 <span data-ttu-id="fd23d-173">由全文引擎返回的最大排名 1000。</span><span class="sxs-lookup"><span data-stu-id="fd23d-173">The maximum rank, 1000, returned by the Full-Text Engine.</span></span>  
  
  
### <a name="rank-computation-issues"></a><span data-ttu-id="fd23d-174">排名计算问题</span><span class="sxs-lookup"><span data-stu-id="fd23d-174">Rank Computation Issues</span></span>  
 <span data-ttu-id="fd23d-175">计算排名的过程，取决于一系列因素。</span><span class="sxs-lookup"><span data-stu-id="fd23d-175">The process of computing rank, depends on a number of factors.</span></span>  <span data-ttu-id="fd23d-176">不同语言的断字符对文本进行的词汇切分也不同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-176">Different language word breakers tokenize text differently.</span></span> <span data-ttu-id="fd23d-177">例如，字符串“dog-house”可以被一种断字符断为“dog”和“house”而被另一种断字符断为“dog-house”。</span><span class="sxs-lookup"><span data-stu-id="fd23d-177">For example, the string "dog-house" could be broken into "dog" "house" by one word breaker and into "dog-house" by another.</span></span> <span data-ttu-id="fd23d-178">这意味着匹配和排名将根据所指定语言而有所不同，因为不仅词不同，而且文档长度也不同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-178">This means that matching and ranking will vary based on the language specified, because not only are the words different, but so is the document length.</span></span> <span data-ttu-id="fd23d-179">文档长度的差异可能会影响所有查询的排名。</span><span class="sxs-lookup"><span data-stu-id="fd23d-179">The document length difference can affect ranking for all queries.</span></span>  
  
 <span data-ttu-id="fd23d-180">诸如 `IndexRowCount` 之类的统计信息可能会大不相同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-180">Statistics such as `IndexRowCount` can vary widely.</span></span> <span data-ttu-id="fd23d-181">例如，如果一个目录的主索引有二十亿行，那么对一个新文档的索引将被编制为内存中的中间索引，而基于该内存中索引内的文档数对该文档的排名可能与主索引中的文档排名不同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-181">For example, if a catalog has 2 billion rows in the master index, then one new document is indexed into an in-memory intermediate index, and ranks for that document based on the number of documents in the in-memory index could be skewed compared with ranks for documents from the master index.</span></span> <span data-ttu-id="fd23d-182">因此，建议在完成产生大量要创建索引或重新创建索引的行的任意填充后，使用 ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将这些索引合并为一个主索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-182">For this reason, it is recommended that after any population that results in large number of rows being indexed or re-indexed the indexes be merged into a master index using the ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="fd23d-183">全文引擎也会根据参数（例如中间索引的数目和大小）自动合并索引。</span><span class="sxs-lookup"><span data-stu-id="fd23d-183">The Full-Text Engine will also automatically merge the indexes based on parameters such as the number and size of intermediate indexes.</span></span>  
  
 <span data-ttu-id="fd23d-184">`MaxOccurrence` 值被规范化到 32 个范围的其中一个内。</span><span class="sxs-lookup"><span data-stu-id="fd23d-184">`MaxOccurrence` values are normalized into 1 of 32 ranges.</span></span> <span data-ttu-id="fd23d-185">举例来说，这意味着 50 个字长的文档与 100 个字长的文档的处理方式相同。</span><span class="sxs-lookup"><span data-stu-id="fd23d-185">This means, for example, that a document 50 words long is treated the same as a document 100 words long.</span></span> <span data-ttu-id="fd23d-186">下面是用于规范化的表。</span><span class="sxs-lookup"><span data-stu-id="fd23d-186">Below is the table used for normalization.</span></span> <span data-ttu-id="fd23d-187">由于文档长度位于相邻表值32和128之间的范围内，因此它们被有效地视为具有相同的长度，128 (32 < `docLength` <= 128) 。</span><span class="sxs-lookup"><span data-stu-id="fd23d-187">Because the document lengths are in the range between adjacent table values 32 and 128, they are effectively treated as having the same length, 128 (32 < `docLength` <= 128).</span></span>  
  
```  
{ 16, 32, 128, 256, 512, 725, 1024, 1450, 2048, 2896, 4096, 5792, 8192, 11585,   
16384, 23170, 28000, 32768, 39554, 46340, 55938, 65536, 92681, 131072, 185363,   
262144, 370727, 524288, 741455, 1048576, 2097152, 4194304 };  
  
```  
  
  
### <a name="ranking-of-containstable"></a><span data-ttu-id="fd23d-188">CONTAINSTABLE 排名</span><span class="sxs-lookup"><span data-stu-id="fd23d-188">Ranking of CONTAINSTABLE</span></span>  
 <span data-ttu-id="fd23d-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 排名使用以下算法：</span><span class="sxs-lookup"><span data-stu-id="fd23d-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) ranking uses the following algorithm:</span></span>  
  
```  
StatisticalWeight = Log2( ( 2 + IndexedRowCount ) / KeyRowCount )  
Rank = min( MaxQueryRank, HitCount * 16 * StatisticalWeight / MaxOccurrence )  
```  
  
 <span data-ttu-id="fd23d-190">短语匹配项的排名方式与各个键类似，只不过要估计 `KeyRowCount`（包含该短语的行数），并且此值可能会比实际值大。</span><span class="sxs-lookup"><span data-stu-id="fd23d-190">Phrase matches are ranked just like individual keys except that `KeyRowCount` (the number of rows containing the phrase) is estimated and can be inaccurate and higher than the actual number.</span></span>  
  
 <span data-ttu-id="fd23d-191">**NEAR 的排名**</span><span class="sxs-lookup"><span data-stu-id="fd23d-191">**Ranking of NEAR**</span></span>  
  
 <span data-ttu-id="fd23d-192">通过使用 NEAR 选项，CONTAINSTABLE 支持查询彼此接近的两个或更多个搜索词。</span><span class="sxs-lookup"><span data-stu-id="fd23d-192">CONTAINSTABLE supports querying for two or more search terms in proximity to each other by using the NEAR option.</span></span> <span data-ttu-id="fd23d-193">每个返回行的排名值基于以下几个参数。</span><span class="sxs-lookup"><span data-stu-id="fd23d-193">The rank value of each returned row is based on several parameters.</span></span> <span data-ttu-id="fd23d-194">一个主要排名因素是相对于文档长度的匹配项总数（或“命中数”  ）。</span><span class="sxs-lookup"><span data-stu-id="fd23d-194">One major ranking factor is the total number of matches (or *hits*) relative to the length of the document.</span></span> <span data-ttu-id="fd23d-195">因此举例来说，如果一个 100 个字长的文档和一个 900 个字长的文档中包含相同的匹配项，那么 100 个字长的文档的排名更靠前。</span><span class="sxs-lookup"><span data-stu-id="fd23d-195">Thus, for example, if a 100-word document and a 900-word document contain identical matches, the 100-word document is ranked higher.</span></span>  
  
 <span data-ttu-id="fd23d-196">根据匹配项中第一个与最后一个搜索词之间的距离，一行中每个匹配项的总长度也会提高该行的排名。</span><span class="sxs-lookup"><span data-stu-id="fd23d-196">The total length of each hit in a row will also contribute to the ranking of that row based on the distance between the first and last search terms of that hit.</span></span> <span data-ttu-id="fd23d-197">距离越小，该匹配项对该行排名值的贡献就越大。</span><span class="sxs-lookup"><span data-stu-id="fd23d-197">The smaller the distance, the more the hit contributes to the rank value of the row.</span></span> <span data-ttu-id="fd23d-198">如果全文查询没有指定一个整数作为最大距离，只有包含的匹配项的相隔距离大于 100 个逻辑词时，文档才会得到 0 排名。</span><span class="sxs-lookup"><span data-stu-id="fd23d-198">If a full-text query does not specify an integer as the maximum distance, a document that contains only hits whose distances are greater than 100 logical terms apart, will have a ranking of 0.</span></span>  
  
 <span data-ttu-id="fd23d-199">**ISABOUT 排名**</span><span class="sxs-lookup"><span data-stu-id="fd23d-199">**Ranking of ISABOUT**</span></span>  
  
 <span data-ttu-id="fd23d-200">CONTAINSTABLE 使用 ISABOUT 选项支持查询加权词。</span><span class="sxs-lookup"><span data-stu-id="fd23d-200">CONTAINSTABLE supports querying for weighted terms by using the ISABOUT option.</span></span> <span data-ttu-id="fd23d-201">按照传统信息检索系统的说法，ISABOUT 表示向量空间查询。</span><span class="sxs-lookup"><span data-stu-id="fd23d-201">ISABOUT is a vector-space query in traditional information retrieval terminology.</span></span> <span data-ttu-id="fd23d-202">所使用的默认排名算法为广为人知的公式 Jaccard。</span><span class="sxs-lookup"><span data-stu-id="fd23d-202">The default ranking algorithm used is Jaccard, a widely known formula.</span></span> <span data-ttu-id="fd23d-203">将根据查询中的每个词计算排名，然后按如下描述将这些排名相结合。</span><span class="sxs-lookup"><span data-stu-id="fd23d-203">The ranking is computed for each term in the query and then combined as described below.</span></span>  
  
```  
ContainsRank = same formula used for CONTAINSTABLE ranking of a single term (above).  
Weight = the weight specified in the query for each term. Default weight is 1.  
WeightedSum = ??[key=1 to n] ContainsRankKey * WeightKey  
Rank =  ( MaxQueryRank * WeightedSum ) / ( ( ??[key=1 to n] ContainsRankKey^2 )   
      + ( ??[key=1 to n] WeightKey^2 ) - ( WeightedSum ) )  
  
```  
  
  
### <a name="ranking-of-freetexttable"></a><span data-ttu-id="fd23d-204">FREETEXTTABLE 排名</span><span class="sxs-lookup"><span data-stu-id="fd23d-204">Ranking of FREETEXTTABLE</span></span>  
 <span data-ttu-id="fd23d-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 排名基于 OKAPI BM25 排名公式计算。</span><span class="sxs-lookup"><span data-stu-id="fd23d-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) ranking is based on the OKAPI BM25 ranking formula.</span></span> <span data-ttu-id="fd23d-206">FREETEXTTABLE 查询将通过派生词（原始查询词的变形）向查询中添加词，这些词将被作为单独的、与派生出它们的词没有特殊联系的词来处理。</span><span class="sxs-lookup"><span data-stu-id="fd23d-206">FREETEXTTABLE queries will add words to the query via inflectional generation (inflected forms of the original query words); these words are treated as separate words with no special relationship to the words from which they were generated.</span></span> <span data-ttu-id="fd23d-207">同义词库功能派生出的同义词将被当作单独的、具有同等加权值的词来处理。</span><span class="sxs-lookup"><span data-stu-id="fd23d-207">Synonyms generated from the Thesaurus feature are treated as separate, equally weighted terms.</span></span> <span data-ttu-id="fd23d-208">查询中的每个词都会对排名产生影响。</span><span class="sxs-lookup"><span data-stu-id="fd23d-208">Each word in the query contributes to the rank.</span></span>  
  
```  
Rank = ??[Terms in Query] w ( ( ( k1 + 1 ) tf ) / ( K + tf ) ) * ( ( k3 + 1 ) qtf / ( k3 + qtf ) ) )  
Where:   
w is the Robertson-Sparck Jones weight.   
In simplified form, w is defined as:   
w = log10 ( ( ( r + 0.5 ) * ( N - R + r + 0.5 ) ) / ( ( R - r + 0.5 ) * ( n - r + 0.5 ) )  
N is the number of indexed rows for the property being queried.   
n is the number of rows containing the word.   
K is ( k1 * ( ( 1 - b ) + ( b * dl / avdl ) ) ).   
dl is the property length, in word occurrences.   
avdl is the average length of the property being queried, in word occurrences.   
k1, b, and k3 are the constants 1.2, 0.75, and 8.0, respectively.   
tf is the frequency of the word in the queried property in a specific row.   
qtf is the frequency of the term in the query.   
```  
  
  
## <a name="see-also"></a><span data-ttu-id="fd23d-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd23d-209">See Also</span></span>  
 [<span data-ttu-id="fd23d-210">使用全文搜索查询</span><span class="sxs-lookup"><span data-stu-id="fd23d-210">Query with Full-Text Search</span></span>](query-with-full-text-search.md)  
  
  
