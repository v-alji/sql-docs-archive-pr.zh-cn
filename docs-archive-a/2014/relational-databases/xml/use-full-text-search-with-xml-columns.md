---
title: 对 XML 列使用全文搜索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml columns [full-text search]
- indexes [full-text search]
ms.assetid: 8096cfc6-1836-4ed5-a769-a5d63b137171
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b6b23933fde6a09d043c7055b0daa7c07035cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688628"
---
# <a name="use-full-text-search-with-xml-columns"></a><span data-ttu-id="bb196-102">对 XML 列使用全文搜索</span><span class="sxs-lookup"><span data-stu-id="bb196-102">Use Full-Text Search with XML Columns</span></span>
  <span data-ttu-id="bb196-103">您可以对 XML 列创建全文索引，这种索引对 XML 值的内容进行索引，但忽略 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="bb196-103">You can create a full-text index on XML columns that indexes the content of the XML values, but ignores the XML markup.</span></span> <span data-ttu-id="bb196-104">元素标记用作标记边界。</span><span class="sxs-lookup"><span data-stu-id="bb196-104">Element tags are used as token boundaries.</span></span> <span data-ttu-id="bb196-105">将对以下项进行索引：</span><span class="sxs-lookup"><span data-stu-id="bb196-105">The following items are indexed:</span></span>  
  
-   <span data-ttu-id="bb196-106">XML 元素的内容。</span><span class="sxs-lookup"><span data-stu-id="bb196-106">The content of XML elements.</span></span>  
  
-   <span data-ttu-id="bb196-107">仅限顶级元素的 XML 属性的内容，除非这些值是数值。</span><span class="sxs-lookup"><span data-stu-id="bb196-107">The content of XML attributes of the top-level element only, unless those values are numeric values.</span></span>  
  
 <span data-ttu-id="bb196-108">如有可能，可以按如下方式将全文搜索与 XML 索引结合起来：</span><span class="sxs-lookup"><span data-stu-id="bb196-108">When possible, you can combine full-text search with XML index in the following way:</span></span>  
  
1.  <span data-ttu-id="bb196-109">首先，使用 SQL 全文搜索筛选感兴趣的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="bb196-109">First, filter the XML values of interest by using SQL full-text search.</span></span>  
  
2.  <span data-ttu-id="bb196-110">然后，查询那些使用 XML 列的 XML 索引的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="bb196-110">Next, query those XML values that use XML index on the XML column.</span></span>  
  
## <a name="example-combining-full-text-search-with-xml-querying"></a><span data-ttu-id="bb196-111">示例：将全文搜索和 XML 查询结合起来</span><span class="sxs-lookup"><span data-stu-id="bb196-111">Example: Combining Full-text Search with XML Querying</span></span>  
 <span data-ttu-id="bb196-112">对 XML 列创建了全文索引后，下面的查询将检查 XML 值是否在书的标题中包含“custom”一词：</span><span class="sxs-lookup"><span data-stu-id="bb196-112">After the full-text index has been created on the XML column, the following query checks that an XML value contains the word "custom" in the title of a book:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'custom')   
AND    xCol.exist('/book/title/text()[contains(.,"custom")]') =1  
```  
  
 <span data-ttu-id="bb196-113">**contains()** 方法使用全文索引来将文档中任何位置包含“custom”一词的 XML 值组合为一个子集。</span><span class="sxs-lookup"><span data-stu-id="bb196-113">The **contains()** method uses the full-text index to subset the XML values that contain the word "custom" anywhere in the document.</span></span> <span data-ttu-id="bb196-114">**exist()** 子句确保“custom”一词出现在书的标题中。</span><span class="sxs-lookup"><span data-stu-id="bb196-114">The **exist()** clause ensures that the word "custom" occurs in the title of a book.</span></span>  
  
 <span data-ttu-id="bb196-115">使用 **contains()** 的全文搜索与 XQuery **contains()** 具有不同语义。</span><span class="sxs-lookup"><span data-stu-id="bb196-115">A full-text search that uses **contains()** and XQuery **contains()** has different semantics.</span></span> <span data-ttu-id="bb196-116">后者是子字符串匹配，前者是使用词干匹配的标记匹配。</span><span class="sxs-lookup"><span data-stu-id="bb196-116">The latter is a substring match and the former is a token match that uses stemming.</span></span> <span data-ttu-id="bb196-117">因此，如果搜索标题中包含“run”的字符串，则匹配结果将包括“run”、“runs”和“running”，因为同时满足全文 **contains()** 和 Xquery **contains()** 。</span><span class="sxs-lookup"><span data-stu-id="bb196-117">Therefore, if the search is for the string that has "run" in the title, the matches will include "run", "runs", and "running", because both the full-text **contains()** and the Xquery **contains()** are satisfied.</span></span> <span data-ttu-id="bb196-118">但是，查询不匹配标题中的“customizable”一词，因为全文 **contains()** 失败，但满足 Xquery **contains()** 。</span><span class="sxs-lookup"><span data-stu-id="bb196-118">However, the query does not match the word "customizable" in the title in that the full-text **contains()** fails, but the Xquery **contains()** is satisfied.</span></span> <span data-ttu-id="bb196-119">通常，对于纯子字符串匹配，应删除全文 **contains()** 子句。</span><span class="sxs-lookup"><span data-stu-id="bb196-119">Generally, for pure substring match, the full-text **contains()** clause should be removed.</span></span>  
  
 <span data-ttu-id="bb196-120">此外，全文搜索使用词干匹配，而 XQuery **contains()** 是文字匹配。</span><span class="sxs-lookup"><span data-stu-id="bb196-120">Additionally, full-text search uses word stemming, but XQuery **contains()** is a literal match.</span></span> <span data-ttu-id="bb196-121">这一区别在下一个示例中进行说明。</span><span class="sxs-lookup"><span data-stu-id="bb196-121">This difference is illustrated in the next example.</span></span>  
  
## <a name="example-full-text-search-on-xml-values-using-stemming"></a><span data-ttu-id="bb196-122">示例：使用词干分解对 XML 值进行全文搜索</span><span class="sxs-lookup"><span data-stu-id="bb196-122">Example: Full-text Search on XML Values Using Stemming</span></span>  
 <span data-ttu-id="bb196-123">通常不能消除上一个示例中执行的 XQuery **contains()** 检查。</span><span class="sxs-lookup"><span data-stu-id="bb196-123">The XQuery **contains()** check that was performed in the previous example generally cannot be eliminated.</span></span> <span data-ttu-id="bb196-124">请看下面的查询：</span><span class="sxs-lookup"><span data-stu-id="bb196-124">Consider this query:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'run')   
```  
  
 <span data-ttu-id="bb196-125">因为使用了词干匹配，所以文档中的“ran”一词匹配搜索条件。</span><span class="sxs-lookup"><span data-stu-id="bb196-125">The word "ran" in the document matches the search condition because of stemming.</span></span> <span data-ttu-id="bb196-126">此外，不通过使用 XQuery 来检查搜索上下文。</span><span class="sxs-lookup"><span data-stu-id="bb196-126">Additionally, the search context is not checked by using XQuery.</span></span>  
  
 <span data-ttu-id="bb196-127">当通过使用全文索引的 AXSD 将 XML 分解为关系列时，对 XML 视图执行的 XPath 查询不对基础表执行全文搜索。</span><span class="sxs-lookup"><span data-stu-id="bb196-127">When XML is decomposed into relational columns by using AXSD that are full-text indexed, XPath queries that occur over the XML view do not perform full-text search on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb196-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb196-128">See Also</span></span>  
 [<span data-ttu-id="bb196-129">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bb196-129">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
