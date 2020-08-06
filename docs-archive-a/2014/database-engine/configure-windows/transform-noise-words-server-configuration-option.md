---
title: transform noise words 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 49de4a381de3e998073a73c284e3e3e5960f4921
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692510"
---
# <a name="transform-noise-words-server-configuration-option"></a><span data-ttu-id="b543b-102">transform noise words 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="b543b-102">transform noise words Server Configuration Option</span></span>
  <span data-ttu-id="b543b-103">使用 `transform noise words` 服务器配置选项来取消干扰词（即[非索引字](../../relational-databases/search/full-text-search.md)）导致全文查询的布尔操作返回零行时出现的错误消息。</span><span class="sxs-lookup"><span data-stu-id="b543b-103">Use the `transform noise words` server configuration option to suppress an error message if noise words, that is [stopwords](../../relational-databases/search/full-text-search.md), cause a Boolean operation on a full-text query to return zero rows.</span></span> <span data-ttu-id="b543b-104">此选项对于使用其布尔操作或 NEAR 操作包括干扰词的 CONTAINS 谓词的全文查询非常有用。</span><span class="sxs-lookup"><span data-stu-id="b543b-104">This option is useful for full-text queries that use the CONTAINS predicate in which Boolean operations or NEAR operations include noise words.</span></span> <span data-ttu-id="b543b-105">下表中列出了该选项的可能值。</span><span class="sxs-lookup"><span data-stu-id="b543b-105">The possible values are described in the following table.</span></span>  
  
|<span data-ttu-id="b543b-106">值</span><span class="sxs-lookup"><span data-stu-id="b543b-106">Value</span></span>|<span data-ttu-id="b543b-107">说明</span><span class="sxs-lookup"><span data-stu-id="b543b-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b543b-108">0</span><span class="sxs-lookup"><span data-stu-id="b543b-108">0</span></span>|<span data-ttu-id="b543b-109">不转换干扰词（或非索引字）。</span><span class="sxs-lookup"><span data-stu-id="b543b-109">Noise words (or stopwords) are not transformed.</span></span> <span data-ttu-id="b543b-110">在某个全文查询包含干扰词时，该查询将返回零行，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将引发警告。</span><span class="sxs-lookup"><span data-stu-id="b543b-110">When a full-text query contains noise words, the query returns zero rows, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] raises a warning.</span></span> <span data-ttu-id="b543b-111">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="b543b-111">This is the default behavior.</span></span><br /><br /> <span data-ttu-id="b543b-112">请注意，此警告是运行时警告。</span><span class="sxs-lookup"><span data-stu-id="b543b-112">Note that the warning is a run-time warning.</span></span> <span data-ttu-id="b543b-113">因此，如果未执行全文查询子句，则不会引发警告。</span><span class="sxs-lookup"><span data-stu-id="b543b-113">Therefore, if the full-text clause in the query is not executed, the warning is not raised.</span></span> <span data-ttu-id="b543b-114">对于本地查询，只引发一个警告，即使存在多个全文查询子句时也是如此。</span><span class="sxs-lookup"><span data-stu-id="b543b-114">For a local query, only one warning is raised, even when there are multiple full-text query clauses.</span></span> <span data-ttu-id="b543b-115">对于远程查询，链接服务器可能无法中继错误；因此，可能无法引发警告。</span><span class="sxs-lookup"><span data-stu-id="b543b-115">For a remote query, the linked server might not relay the error; therefore, the warning might not be raised.</span></span>|  
|<span data-ttu-id="b543b-116">1</span><span class="sxs-lookup"><span data-stu-id="b543b-116">1</span></span>|<span data-ttu-id="b543b-117">转换干扰词（或非索引字）。</span><span class="sxs-lookup"><span data-stu-id="b543b-117">Noise words (or stopwords) are transformed.</span></span> <span data-ttu-id="b543b-118">它们将被忽略，并且将对其余查询进行计算。</span><span class="sxs-lookup"><span data-stu-id="b543b-118">They are ignored, and the rest of the query is evaluated.</span></span><br /><br /> <span data-ttu-id="b543b-119">如果用邻近词指定了干扰词，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将删除它们。</span><span class="sxs-lookup"><span data-stu-id="b543b-119">If noise words are specified in a proximity term, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] removes them.</span></span> <span data-ttu-id="b543b-120">例如，干扰词 `is` 将从 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`删除，并且将搜索查询转换为 `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`。</span><span class="sxs-lookup"><span data-stu-id="b543b-120">For example, the noise word `is` is removed from `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`, transforming the search query into `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`.</span></span> <span data-ttu-id="b543b-121">请注意， `CONTAINS(<column_name>, 'NEAR(hello,is)')` 将转换为简单 `CONTAINS(<column_name>, hello)` ，因为仅存在一个有效搜索词。</span><span class="sxs-lookup"><span data-stu-id="b543b-121">Notice that `CONTAINS(<column_name>, 'NEAR(hello,is)')` would be transformed into simply `CONTAINS(<column_name>, hello)` because there is only one valid search term.</span></span>|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a><span data-ttu-id="b543b-122">转换干扰词设置的影响</span><span class="sxs-lookup"><span data-stu-id="b543b-122">Effects of the transform noise words Setting</span></span>  
 <span data-ttu-id="b543b-123">本节将基于 `transform noise words` 的替代设置，说明包含干扰词“`the`”的查询的行为。</span><span class="sxs-lookup"><span data-stu-id="b543b-123">This section illustrates the behavior of queries containing a noise word, "`the`", under the alternate settings of `transform noise words`.</span></span>  <span data-ttu-id="b543b-124">假定示例全文查询字符串将对包含以下数据的表行运行： `[1, "The black cat"]`。</span><span class="sxs-lookup"><span data-stu-id="b543b-124">The sample full-text query strings are assumed to be run against a table row containing the following data: `[1, "The black cat"]`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b543b-125">所有此类应用场景都可以生成干扰词警告。</span><span class="sxs-lookup"><span data-stu-id="b543b-125">All such scenarios can generate a noise word warning.</span></span>  
  
-   <span data-ttu-id="b543b-126">转换干扰词设置为 0：</span><span class="sxs-lookup"><span data-stu-id="b543b-126">With transform noise words set to 0:</span></span>  
  
    |<span data-ttu-id="b543b-127">查询字符串</span><span class="sxs-lookup"><span data-stu-id="b543b-127">Query string</span></span>|<span data-ttu-id="b543b-128">结果</span><span class="sxs-lookup"><span data-stu-id="b543b-128">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="b543b-129">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-129">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="b543b-130">无结果（此行为对于 "`the`" AND "`cat`" 是相同的。）</span><span class="sxs-lookup"><span data-stu-id="b543b-130">No results (The behavior is the same for "`the`" AND "`cat`".)</span></span>|  
    |<span data-ttu-id="b543b-131">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-131">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="b543b-132">无结果（此行为对于 "`the`" NEAR "`cat`" 是相同的。）</span><span class="sxs-lookup"><span data-stu-id="b543b-132">No results (The behavior is the same for "`the`" NEAR "`cat`".)</span></span>|  
    |<span data-ttu-id="b543b-133">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="b543b-133">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="b543b-134">无结果</span><span class="sxs-lookup"><span data-stu-id="b543b-134">No results</span></span>|  
    |<span data-ttu-id="b543b-135">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-135">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="b543b-136">无结果</span><span class="sxs-lookup"><span data-stu-id="b543b-136">No results</span></span>|  
  
-   <span data-ttu-id="b543b-137">转换干扰词设置为 1：</span><span class="sxs-lookup"><span data-stu-id="b543b-137">With transform noise words set to 1:</span></span>  
  
    |<span data-ttu-id="b543b-138">查询字符串</span><span class="sxs-lookup"><span data-stu-id="b543b-138">Query string</span></span>|<span data-ttu-id="b543b-139">结果</span><span class="sxs-lookup"><span data-stu-id="b543b-139">Result</span></span>|  
    |------------------|------------|  
    |<span data-ttu-id="b543b-140">"`cat`" AND "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-140">"`cat`" AND "`the`"</span></span>|<span data-ttu-id="b543b-141">命中 ID 为 1 的行</span><span class="sxs-lookup"><span data-stu-id="b543b-141">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="b543b-142">"`cat`" NEAR "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-142">"`cat`" NEAR "`the`"</span></span>|<span data-ttu-id="b543b-143">命中 ID 为 1 的行</span><span class="sxs-lookup"><span data-stu-id="b543b-143">Hit for row with ID 1</span></span>|  
    |<span data-ttu-id="b543b-144">"`the`" AND NOT "`black`"</span><span class="sxs-lookup"><span data-stu-id="b543b-144">"`the`" AND NOT "`black`"</span></span>|<span data-ttu-id="b543b-145">无结果</span><span class="sxs-lookup"><span data-stu-id="b543b-145">No results</span></span>|  
    |<span data-ttu-id="b543b-146">"`black`" AND NOT "`the`"</span><span class="sxs-lookup"><span data-stu-id="b543b-146">"`black`" AND NOT "`the`"</span></span>|<span data-ttu-id="b543b-147">命中 ID 为 1 的行</span><span class="sxs-lookup"><span data-stu-id="b543b-147">Hit for row with ID 1</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b543b-148">示例</span><span class="sxs-lookup"><span data-stu-id="b543b-148">Example</span></span>  
 <span data-ttu-id="b543b-149">以下示例将 `transform noise words` 设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="b543b-149">The following example sets `transform noise words` to `1`.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b543b-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b543b-150">See Also</span></span>  
 <span data-ttu-id="b543b-151">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b543b-151">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="b543b-152">CONTAINS (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b543b-152">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
