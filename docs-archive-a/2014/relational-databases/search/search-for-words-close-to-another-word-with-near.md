---
title: 使用 NEAR 搜索与另一个词邻近的词 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- word searches [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- proximity searches [full-text search]
- full-text search [SQL Server], proximity searches
- full-text queries [SQL Server], proximity
- queries [full-text search], proximity
ms.assetid: 87520646-4865-49ae-8790-f766b80a41f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c2d187ea3ed951ac6f17eb4babc5f4f77451d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691168"
---
# <a name="search-for-words-close-to-another-word-with-near"></a><span data-ttu-id="159bf-102">使用 NEAR 搜索与另一个词邻近的词</span><span class="sxs-lookup"><span data-stu-id="159bf-102">Search for Words Close to Another Word with NEAR</span></span>
  <span data-ttu-id="159bf-103">可以在 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 谓词或 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 函数中使用邻近词 (NEAR) 来搜索相互邻近的字词或短语。</span><span class="sxs-lookup"><span data-stu-id="159bf-103">You can use a proximity term (NEAR) in a [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) function to search for words or phrases near one another.</span></span> <span data-ttu-id="159bf-104">还可以指定在第一个搜索词与最后一个搜索之间最多可以有几个非搜索词。</span><span class="sxs-lookup"><span data-stu-id="159bf-104">You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="159bf-105">此外，可以按任意顺序或您指定的顺序搜索词或短语。</span><span class="sxs-lookup"><span data-stu-id="159bf-105">In addition, you can search for words or phrases in any order, or you can search for words and phrases in the order in which you specify them.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="159bf-106">同时支持以前的[通用邻近词](#Generic_NEAR)（现已不推荐使用）和[自定义邻近词](#Custom_NEAR)，这是中的新术语 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="159bf-106">supports both the earlier [generic proximity term](#Generic_NEAR), which is now deprecated, and the [custom proximity term](#Custom_NEAR), which is new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
##  <a name="the-custom-proximity-term"></a><a name="Custom_NEAR"></a><span data-ttu-id="159bf-107">自定义邻近词</span><span class="sxs-lookup"><span data-stu-id="159bf-107">The Custom Proximity Term</span></span>  
 <span data-ttu-id="159bf-108">自定义邻近词引入了下列新功能：</span><span class="sxs-lookup"><span data-stu-id="159bf-108">The custom proximity term introduces the following new capabilities:</span></span>  
  
-   <span data-ttu-id="159bf-109">可以指定第一个搜索词与最后一个搜索词之间存在的非搜索词的最大数目或最大距离\*\*，以作为构成匹配项的条件。</span><span class="sxs-lookup"><span data-stu-id="159bf-109">You can specify the maximum number of non-search terms, or *maximum distance*, that separates the first and last search terms in order to constitute a match.</span></span>  
  
-   <span data-ttu-id="159bf-110">如果指定词的最大数目，还可以指定搜索词必须以指定顺序出现在匹配项中。</span><span class="sxs-lookup"><span data-stu-id="159bf-110">If you specify the maximum number of terms, you can also specify that matches must contain the search terms in the specified order.</span></span>  
  
 <span data-ttu-id="159bf-111">若要成为一个符合条件的匹配项，文本字符串必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="159bf-111">To qualify as a match, a string of text must:</span></span>  
  
-   <span data-ttu-id="159bf-112">以其中一个指定搜索词开头，以其中另一个指定搜索词结尾。</span><span class="sxs-lookup"><span data-stu-id="159bf-112">Start with one of the specified search terms and end with the one of the other specified search terms.</span></span>  
  
-   <span data-ttu-id="159bf-113">包含所有指定的搜索词。</span><span class="sxs-lookup"><span data-stu-id="159bf-113">Contain all of the specified search terms.</span></span>  
  
-   <span data-ttu-id="159bf-114">如果指定了最大距离，在第一个搜索词和最后一个搜索词之间出现的非搜索词（包括非索引字）的数目必须少于或等于最大距离。</span><span class="sxs-lookup"><span data-stu-id="159bf-114">The number of non-search terms, including stopwords, that occur between the first and last search terms must be less than or equal to the maximum distance, if specified.</span></span>  
  
 <span data-ttu-id="159bf-115">基本语法为：</span><span class="sxs-lookup"><span data-stu-id="159bf-115">The basic syntax is:</span></span>  
  
 <span data-ttu-id="159bf-116">NEAR (</span><span class="sxs-lookup"><span data-stu-id="159bf-116">NEAR (</span></span>  
  
 <span data-ttu-id="159bf-117">{</span><span class="sxs-lookup"><span data-stu-id="159bf-117">{</span></span>  
  
 <span data-ttu-id="159bf-118">*search_term* [,.。。*n* ]</span><span class="sxs-lookup"><span data-stu-id="159bf-118">*search_term* [ ,...*n* ]</span></span>  
  
 |  
  
 <span data-ttu-id="159bf-119"> (*search_term* [,.。。*n* ] ) [，<maximum_distance> [，<match_order>]]</span><span class="sxs-lookup"><span data-stu-id="159bf-119">(*search_term* [ ,...*n* ] ) [, <maximum_distance> [, <match_order> ] ]</span></span>  
  
 <span data-ttu-id="159bf-120">}</span><span class="sxs-lookup"><span data-stu-id="159bf-120">}</span></span>  
  
 <span data-ttu-id="159bf-121">)</span><span class="sxs-lookup"><span data-stu-id="159bf-121">)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="159bf-122">有关 <custom_proximity_term> 语法的详细信息，请参阅 [CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="159bf-122">For more information about the <custom_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="159bf-123">例如，可以搜索距离“Smith”两个词以内的“John”，如下所示：</span><span class="sxs-lookup"><span data-stu-id="159bf-123">For example, you could search for 'John' within two terms of 'Smith', as follows:</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((John, Smith), 2)')  
```  
  
 <span data-ttu-id="159bf-124">匹配的字符串的一些示例包括“`John Jacob Smith`”和“`Smith, John`”。</span><span class="sxs-lookup"><span data-stu-id="159bf-124">Some examples of strings that match are "`John Jacob Smith`" and "`Smith, John`".</span></span> <span data-ttu-id="159bf-125">字符串“`John Jones knows Fred Smith`”中间隔有三个非搜索词，因此它不是一个匹配项。</span><span class="sxs-lookup"><span data-stu-id="159bf-125">The string "`John Jones knows Fred Smith`" contains three intervening non-search terms, so it is not a match.</span></span>  
  
 <span data-ttu-id="159bf-126">若要求查找指定顺序的词，可以将上面的邻近词示例更改为 `NEAR((John, Smith),2, TRUE).` 。这样将搜索距离“`John`”两个词以内的“`Smith`”并且“`John`”必须在“`Smith`”之前。</span><span class="sxs-lookup"><span data-stu-id="159bf-126">To require that the terms be found in the specified order, you would change the example proximity term to `NEAR((John, Smith),2, TRUE).` This searches for "`John`" within two terms of "`Smith`" but only when "`John`" precedes "`Smith`".</span></span> <span data-ttu-id="159bf-127">在从左向右阅读的语言（如英语）中，匹配的字符串的示例有“`John Jacob Smith`”。</span><span class="sxs-lookup"><span data-stu-id="159bf-127">In a language that reads from left to right, such as English, an example of a string that matches is "`John Jacob Smith`".</span></span>  
  
 <span data-ttu-id="159bf-128">请注意，对于从右向左阅读的语言（例如阿拉伯语或希伯来语），全文引擎会以相反的顺序应用指定词。</span><span class="sxs-lookup"><span data-stu-id="159bf-128">Note that for a language that reads from right to left, such as Arabic or Hebrew, the Full-Text Engine applies the specified terms in reverse order.</span></span> <span data-ttu-id="159bf-129">此外， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的对象资源管理器会自动颠倒从右到左语言中指定的文字显示顺序。</span><span class="sxs-lookup"><span data-stu-id="159bf-129">Also, Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] automatically reverses the display order of words specified in right-to-left languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="159bf-130"> 有关详细信息，请参阅本主题后面的“[有关邻近搜索的更多考虑因素](#Additional_Considerations)”。</span><span class="sxs-lookup"><span data-stu-id="159bf-130">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="how-maximum-distance-is-measured"></a><span data-ttu-id="159bf-131">最大距离的测量方式</span><span class="sxs-lookup"><span data-stu-id="159bf-131">How Maximum Distance Is Measured</span></span>  
 <span data-ttu-id="159bf-132">特定的最大距离（例如 10 或 25）决定在给定字符串的第一个搜索词与最后一个搜索词之间可以出现多少个非搜索词（包括非索引字）。</span><span class="sxs-lookup"><span data-stu-id="159bf-132">A specific maximum distance, such as 10 or 25, determines how many non-search terms, including stopwords, can occur between the first and last search terms in a given string.</span></span> <span data-ttu-id="159bf-133">例如， `NEAR((dogs, cats, "hunting mice"), 3)` 将返回以下行，其中非搜索词的总数为 3（“`enjoy`”、“`but`”和“`avoid`”)：</span><span class="sxs-lookup"><span data-stu-id="159bf-133">For example, `NEAR((dogs, cats, "hunting mice"), 3)` would return the following row, in which the total number of non-search terms is three ("`enjoy`", "`but`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="159bf-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="159bf-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span></span>  
  
 <span data-ttu-id="159bf-135">相同的邻近词将不返回以下行，因为最大距离超过了四个非搜索词（“`enjoy`”、“`but`”、“`usually`”和“`avoid`”）：</span><span class="sxs-lookup"><span data-stu-id="159bf-135">The same proximity term would not return the following row, because the maximum distance is exceeded by the four non-search terms ("`enjoy`", "`but`", "`usually`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="159bf-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="159bf-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span></span>  
  
### <a name="combining-a-custom-proximity-term-with-other-terms"></a><span data-ttu-id="159bf-137">将自定义邻近词与其他词组合使用</span><span class="sxs-lookup"><span data-stu-id="159bf-137">Combining a Custom Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="159bf-138">可以将自定义邻近词与一些其他词组合使用。</span><span class="sxs-lookup"><span data-stu-id="159bf-138">You can combine a custom proximity term with some other terms.</span></span> <span data-ttu-id="159bf-139">可以使用 AND (&), OR (|) 或 AND NOT (&!) 将一个自定义邻近词与另一个自定义邻近词、简单词或前缀词组合使用。</span><span class="sxs-lookup"><span data-stu-id="159bf-139">You can use AND (&), OR (|), or AND NOT (&!) to combine a custom proximity term with another custom proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="159bf-140">例如：</span><span class="sxs-lookup"><span data-stu-id="159bf-140">For example:</span></span>  
  
-   <span data-ttu-id="159bf-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span><span class="sxs-lookup"><span data-stu-id="159bf-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span></span>  
  
-   <span data-ttu-id="159bf-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span><span class="sxs-lookup"><span data-stu-id="159bf-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span></span>  
  
-   <span data-ttu-id="159bf-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span><span class="sxs-lookup"><span data-stu-id="159bf-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span></span>  
  
-   <span data-ttu-id="159bf-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span><span class="sxs-lookup"><span data-stu-id="159bf-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span></span>  
  
-   <span data-ttu-id="159bf-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span><span class="sxs-lookup"><span data-stu-id="159bf-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span></span>  
  
 <span data-ttu-id="159bf-146">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="159bf-146">For example,</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((term1, term2), 5, TRUE) AND term3')  
```  
  
 <span data-ttu-id="159bf-147">不能将自定义邻近词与通用邻近词 (*term1* NEAR *term2*) 、生成词 (ISABOUT ... ) 或加权术语 () 。</span><span class="sxs-lookup"><span data-stu-id="159bf-147">You cannot combine a custom proximity term with a generic proximity term (*term1* NEAR *term2*), a generation term (ISABOUT ...), or a weighted term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-custom-proximity-term"></a><span data-ttu-id="159bf-148">示例：使用自定义邻近词</span><span class="sxs-lookup"><span data-stu-id="159bf-148">Example: Using the Custom Proximity Term</span></span>  
 <span data-ttu-id="159bf-149">以下示例在 `Production.Document` 示例数据库的 `AdventureWorks2012` 表中搜索包含与字词“bracket”在同一文档中的字词“reflector”的所有文档摘要。</span><span class="sxs-lookup"><span data-stu-id="159bf-149">The following example searches the `Production.Document` table of the `AdventureWorks2012` sample database for all document summaries that contain the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  

  
##  <a name="additional-considerations-for-proximity-searches"></a><a name="Additional_Considerations"></a><span data-ttu-id="159bf-150">邻近搜索的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="159bf-150">Additional Considerations for Proximity Searches</span></span>  
 <span data-ttu-id="159bf-151">本节讨论了对通用邻近搜索和自定义邻近搜索都有影响的考虑因素：</span><span class="sxs-lookup"><span data-stu-id="159bf-151">This section discusses consideration that affect both generic and custom proximity searches:</span></span>  
  
-   <span data-ttu-id="159bf-152">搜索词的重叠匹配项</span><span class="sxs-lookup"><span data-stu-id="159bf-152">Overlapping occurrences of search terms</span></span>  
  
     <span data-ttu-id="159bf-153">所有邻近搜索始终都仅查找非重叠匹配项。</span><span class="sxs-lookup"><span data-stu-id="159bf-153">All proximity searches always look for only non-overlapping occurrences.</span></span> <span data-ttu-id="159bf-154">搜索词的重叠匹配项永远不会符合匹配项的条件。</span><span class="sxs-lookup"><span data-stu-id="159bf-154">Overlapping occurrences of search terms never qualify as matches.</span></span> <span data-ttu-id="159bf-155">例如，请考虑以下邻近词，它按照此顺序搜索“`A`”和“`AA`”，并且最大距离为两个词：</span><span class="sxs-lookup"><span data-stu-id="159bf-155">For example, consider the following proximity term, which searches "`A`" and "`AA`" in this order with a maximum distance of two terms:</span></span>  
  
    ```  
    CONTAINS(column_name, 'NEAR((A,AA),2, TRUE')  
    ```  
  
     <span data-ttu-id="159bf-156">可能的匹配项是“`AAA`”、“`A.AA`”和“`A..AA`”。</span><span class="sxs-lookup"><span data-stu-id="159bf-156">The possible matches are as "`AAA`", "`A.AA`", and "`A..AA`".</span></span> <span data-ttu-id="159bf-157">仅包含“`AA`”的行将不匹配。</span><span class="sxs-lookup"><span data-stu-id="159bf-157">Rows containing just "`AA`" would not match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="159bf-158">可以指定重叠的词，例如 `NEAR("mountain bike", "bike trails")` 或 `(NEAR(comfort*, comfortable), 5)`。</span><span class="sxs-lookup"><span data-stu-id="159bf-158">You can specify terms that overlap, for example, `NEAR("mountain bike", "bike trails")` or `(NEAR(comfort*, comfortable), 5)`.</span></span> <span data-ttu-id="159bf-159">指定重叠词会增加查询的复杂性，这是因为增加了可能的匹配项排列。</span><span class="sxs-lookup"><span data-stu-id="159bf-159">Specifying a overlapping terms increases the complexity of the query by increasing the possible match permutations.</span></span> <span data-ttu-id="159bf-160">如果指定了大量这样的重叠词，查询可能会耗尽资源并失败。</span><span class="sxs-lookup"><span data-stu-id="159bf-160">If you specify a large number of such overlapping terms, the query can run out of resources and fail.</span></span> <span data-ttu-id="159bf-161">如果发生这种情况，请简化查询，然后重试。</span><span class="sxs-lookup"><span data-stu-id="159bf-161">If this occurs, simplify the query and try again.</span></span>  
  
-   <span data-ttu-id="159bf-162">通用 NEAR 和自定义 NEAR（无论是否指定最大距离）都指示词之间的逻辑距离，而不是词之间的绝对距离间。</span><span class="sxs-lookup"><span data-stu-id="159bf-162">Both generic NEAR and custom NEAR (regardless of whether a maximum distance is specified) indicate the logical distance between terms, rather than the absolute distance between them.</span></span> <span data-ttu-id="159bf-163">例如，某一段落内其他短语或句子中的字词被视为距离远于同一短语或句子中的字词，而与其实际临近情况无关，因为假定它们是不相关的。</span><span class="sxs-lookup"><span data-stu-id="159bf-163">For example, terms within different phrases or sentences within a paragraph are treated as farther apart than terms in the same phrase or sentence, regardless of their actual proximity, on the assumption that they are less related.</span></span> <span data-ttu-id="159bf-164">同样，不同段落中的字词被视为距离更远。</span><span class="sxs-lookup"><span data-stu-id="159bf-164">Likewise, terms in different paragraphs are treated as being even farther apart.</span></span> <span data-ttu-id="159bf-165">如果一个匹配项包含一个句子、一个段落或一个章节，用于文档排名的差距将分别提高 8、128 或 1024。</span><span class="sxs-lookup"><span data-stu-id="159bf-165">If a match spans the end of a sentence, paragraph, or chapter, the gap used for ranking a document is increased by 8, 128, or 1024, respectively.</span></span>  
  
-   <span data-ttu-id="159bf-166">邻近词通过 CONTAINSTABLE 函数对排名的影响</span><span class="sxs-lookup"><span data-stu-id="159bf-166">Impact of proximity terms on ranking by the CONTAINSTABLE function</span></span>  
  
     <span data-ttu-id="159bf-167">当 NEAR 在 CONTAINSTABLE 函数中使用时，文档中相对于文档长度的匹配项数以及每个匹配项中第一个与最后一个搜索词之间的距离会影响每个文档的排名。</span><span class="sxs-lookup"><span data-stu-id="159bf-167">When NEAR is used in the CONTAINSTABLE function, the number of hits in a document relative to its length as well as the distance between the first and last search terms in each of the hits affects the ranking of each document.</span></span> <span data-ttu-id="159bf-168">对于通用邻近词，如果匹配的搜索词之间相隔的距离 > 50 个逻辑词，则对文档返回的排名为 0。</span><span class="sxs-lookup"><span data-stu-id="159bf-168">For a generic proximity term, if the matched search terms are >50 logical terms apart, the rank returned on a document is 0.</span></span> <span data-ttu-id="159bf-169">对于没有指定一个整数作为最大距离的自定义邻近词，只有其包含的匹配项的相隔距离 > 100 个逻辑词时，文档才会得到 0 排名。</span><span class="sxs-lookup"><span data-stu-id="159bf-169">For a custom proximity term that does not specify an integer as the maximum distance, a document that contains only hits whose gap is >100 logical terms will receive a ranking of 0.</span></span> <span data-ttu-id="159bf-170">有关自定义邻近搜索排名的详细信息，请参阅 [Limit Search Results with RANK](limit-search-results-with-rank.md)。</span><span class="sxs-lookup"><span data-stu-id="159bf-170">For more information about ranking of custom proximity searches, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
-   <span data-ttu-id="159bf-171">**transform noise words** 服务器选项</span><span class="sxs-lookup"><span data-stu-id="159bf-171">The **transform noise words** server option</span></span>  
  
     <span data-ttu-id="159bf-172">如果在邻近搜索中指定了非索引字，则 **transform noise words** 的值会影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处理非索引字的方式。</span><span class="sxs-lookup"><span data-stu-id="159bf-172">The value of **transform noise words** impacts how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] treats stopwords if they are specified in proximity searches.</span></span> <span data-ttu-id="159bf-173">有关详细信息，请参阅 [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="159bf-173">For more information, see [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).</span></span>  
  

  
##  <a name="the-deprecated-generic-proximity-term"></a><a name="Generic_NEAR"></a><span data-ttu-id="159bf-174">不推荐使用的通用邻近词</span><span class="sxs-lookup"><span data-stu-id="159bf-174">The Deprecated Generic Proximity Term</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="159bf-175">我们建议您使用 [自定义邻近词](#Custom_NEAR)。</span><span class="sxs-lookup"><span data-stu-id="159bf-175">We recommend that you use the [custom proximity term](#Custom_NEAR).</span></span>  
  
 <span data-ttu-id="159bf-176">通用邻近词表明指定的搜索词必须全部出现在一个文档中匹配项才能返回，而与搜索词之间非搜索词的数目（距离\*\*）无关。</span><span class="sxs-lookup"><span data-stu-id="159bf-176">A generic proximity term indicates that the specified search terms must all occur in a document for a match to be returned, regardless of the number of non-search terms (the *distance*) between the search terms.</span></span> <span data-ttu-id="159bf-177">基本语法为：</span><span class="sxs-lookup"><span data-stu-id="159bf-177">The basic syntax is:</span></span>  
  
 <span data-ttu-id="159bf-178">{ *search_term* {NEAR | ~} *search_term* }[ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="159bf-178">{ *search_term* { NEAR | ~ } *search_term* } [ ,...*n* ]</span></span>  
  
 <span data-ttu-id="159bf-179">例如，在下面的示例中，单词“fox”和“chicken”必须都出现才能产生一个匹配项，不管它们的出现顺序如何：</span><span class="sxs-lookup"><span data-stu-id="159bf-179">For example, in the following examples, the words 'fox' and 'chicken' must both appear, in either order, to produce a match:</span></span>  
  
-   `CONTAINS(column_name, 'fox NEAR chicken')`  
  
-   `CONTAINSTABLE(table_name, column_name, 'fox ~ chicken')`  
  
> [!NOTE]  
>  <span data-ttu-id="159bf-180">有关 <generic_proximity_term> 语法的信息，请参阅 [CONTAINS (Transact-SQL)](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="159bf-180">For information about the <generic_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="159bf-181"> 有关详细信息，请参阅本主题后面的“[有关邻近搜索的更多考虑因素](#Additional_Considerations)”。</span><span class="sxs-lookup"><span data-stu-id="159bf-181">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="combining-a-generic-proximity-term-with-other-terms"></a><span data-ttu-id="159bf-182">将通用邻近词与其他词组合使用</span><span class="sxs-lookup"><span data-stu-id="159bf-182">Combining a Generic Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="159bf-183">可以使用 AND (&), OR (|) 或 AND NOT (&!) 将一个通用邻近词与另一个通用邻近词、简单词或前缀词组合使用。</span><span class="sxs-lookup"><span data-stu-id="159bf-183">You can use AND (&), OR (|), or AND NOT (&!) to combine a generic proximity term with another generic proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="159bf-184">例如：</span><span class="sxs-lookup"><span data-stu-id="159bf-184">For example:</span></span>  
  
```  
CONTAINSTABLE (Production.ProductDescription,  
   Description,   
   '(light NEAR aluminum) OR  
   (lightweight NEAR aluminum)'  
)  
```  
  
 <span data-ttu-id="159bf-185">不能将通用邻近词与自定义邻近词（例如 `NEAR((term1,term2),5)` ，加权字词 (ISABOUT ) ）或 (FORMSOF ... ) 中的代等项组合在一起。</span><span class="sxs-lookup"><span data-stu-id="159bf-185">You cannot combine a generic proximity term with a custom proximity term, such as `NEAR((term1,term2),5)`, a weighted term (ISABOUT ...), or a generational term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-generic-proximity-term"></a><span data-ttu-id="159bf-186">示例： 使用通用邻近词</span><span class="sxs-lookup"><span data-stu-id="159bf-186">Example: Using the Generic Proximity Term</span></span>  
 <span data-ttu-id="159bf-187">下面的示例使用通用邻近词在一个有字词“bracket”的文档中搜索字词“reflector”。</span><span class="sxs-lookup"><span data-stu-id="159bf-187">The following example uses the generic proximity term to search for the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable INNER JOIN  
  CONTAINSTABLE(Production.Document, Document,  
  '(reflector NEAR bracket)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
 <span data-ttu-id="159bf-188">注意，也可以在 CONTAINSTABLE 中反转词条，所得到的结果相同：</span><span class="sxs-lookup"><span data-stu-id="159bf-188">Notice that you can also reverse the terms in CONTAINSTABLE to get the same result:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(bracket NEAR reflector)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="159bf-189">可以用字符 ~ 来代替前面查询中的 NEAR 关键字，其结果是一样的：</span><span class="sxs-lookup"><span data-stu-id="159bf-189">You can use the tilde character (~) in place of the NEAR keyword in the earlier query, and get the same results:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="159bf-190">可以在搜索条件中指定两个以上的词或短语。</span><span class="sxs-lookup"><span data-stu-id="159bf-190">More than two words or phrases can be specified in the search conditions.</span></span> <span data-ttu-id="159bf-191">例如，可以编写：</span><span class="sxs-lookup"><span data-stu-id="159bf-191">For example, it is possible to write:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket ~ installation)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="159bf-192">这意味着“reflector”必须与“bracket”在同一文档中，“bracket”必须与“installation”在同一文档中。</span><span class="sxs-lookup"><span data-stu-id="159bf-192">This means that "reflector" must be in the same document as "bracket", and "bracket" must be in the same document as "installation".</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="159bf-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="159bf-193">See Also</span></span>  
 <span data-ttu-id="159bf-194">[CONTAINSTABLE (Transact-SQL)](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="159bf-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="159bf-195">[使用全文搜索查询](query-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="159bf-195">[Query with Full-Text Search](query-with-full-text-search.md) </span></span>  
 [<span data-ttu-id="159bf-196">CONTAINS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="159bf-196">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
