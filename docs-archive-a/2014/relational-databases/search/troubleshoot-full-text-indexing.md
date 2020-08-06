---
title: 排除全文索引故障 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eaca5fcf2dfbac57fc6d3ba6178251927d15aba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591213"
---
# <a name="troubleshoot-full-text-indexing"></a><span data-ttu-id="d829d-102">排除全文索引故障</span><span class="sxs-lookup"><span data-stu-id="d829d-102">Troubleshoot Full-Text Indexing</span></span>
     
##  <a name="troubleshoot-full-text-indexing-failures"></a><a name="failure"></a> <span data-ttu-id="d829d-103">排除全文索引故障</span><span class="sxs-lookup"><span data-stu-id="d829d-103">Troubleshoot Full-Text Indexing Failures</span></span>  
 <span data-ttu-id="d829d-104">填充或维护全文索引时，由于下面描述的原因，全文索引器可能无法对一个或多个行编制索引。</span><span class="sxs-lookup"><span data-stu-id="d829d-104">While populating or maintaining a full-text index, the full-text indexer, for reasons described below, might fail to index one or more rows.</span></span> <span data-ttu-id="d829d-105">这些行级别的错误不会干扰填充的进行。</span><span class="sxs-lookup"><span data-stu-id="d829d-105">These row-level errors do not prevent the population from completing.</span></span> <span data-ttu-id="d829d-106">索引器会跳过这些行，这意味着您无法查询这些行中包含的内容。</span><span class="sxs-lookup"><span data-stu-id="d829d-106">The indexer skips these rows, which means that you are not able to query for content contained in these rows.</span></span>  
  
 <span data-ttu-id="d829d-107">在以下情况下，可能会发生索引失败：</span><span class="sxs-lookup"><span data-stu-id="d829d-107">Indexing failures can occur when:</span></span>  
  
-   <span data-ttu-id="d829d-108">索引器找不到或无法加载筛选器或断字符组件。</span><span class="sxs-lookup"><span data-stu-id="d829d-108">The indexer cannot find or load a filter or word breaker component.</span></span> <span data-ttu-id="d829d-109">如果表中的行所包含的文档格式或内容使用了尚未注册到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的语言，则这样的索引失败可能会发生。</span><span class="sxs-lookup"><span data-stu-id="d829d-109">This failure can occur if the table row contains a document format or content in a language that has not been registered with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d829d-110">如果在加载时已注册的断字符或筛选器组件未经过签名或签名验证失败，则这样的索引失败也可能会发生。</span><span class="sxs-lookup"><span data-stu-id="d829d-110">This failure can also happen if the registered word breaker or filter component was not signed or failed signature verification when it was being loaded.</span></span>  
  
-   <span data-ttu-id="d829d-111">诸如断字符或筛选器这样的组件失败，并向索引器返回错误。</span><span class="sxs-lookup"><span data-stu-id="d829d-111">A component, such as a word breaker or filter, fails and returns an error to the indexer.</span></span> <span data-ttu-id="d829d-112">如果所索引的文档已损坏，并且筛选器无法从该文档提取文本，则这样的索引失败可能会发生。</span><span class="sxs-lookup"><span data-stu-id="d829d-112">This can happen if the document being indexed is corrupt and the filter is unable to extract text from the document.</span></span> <span data-ttu-id="d829d-113">由于全文筛选器后台程序宿主 (fdhost.exe) 受到的内存限制，当组件无法处理超过某个大小的单行中的内容时，这样的索引失败也可能会发生。</span><span class="sxs-lookup"><span data-stu-id="d829d-113">This can also occur when a component is unable to handle the content of a single row above a certain size, due to memory limits on the full-text filter daemon host (fdhost.exe).</span></span>  
  
 <span data-ttu-id="d829d-114">对于每个行级别的失败，爬网日志将包含有关失败原因的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d829d-114">For each row-level failure, the crawl log contains details on the reason for the failure.</span></span> <span data-ttu-id="d829d-115">将在完整或增量填充的末尾总计错误计数。</span><span class="sxs-lookup"><span data-stu-id="d829d-115">The error counts are summarized at the end of a full or incremental population.</span></span>  
  
 <span data-ttu-id="d829d-116">还有其他失败会影响索引进程本身，使填充无法完成：</span><span class="sxs-lookup"><span data-stu-id="d829d-116">There are other failures that can impact the indexing process itself and prevent the population from completing:</span></span>  
  
-   <span data-ttu-id="d829d-117">全文索引超过了全文目录中可以包含的行数限制。</span><span class="sxs-lookup"><span data-stu-id="d829d-117">The full-text index exceeds the limit for the number of rows that can be contained in a full-text catalog.</span></span>  
  
-   <span data-ttu-id="d829d-118">索引的表的聚集索引或全文键索引已更改、删除或重新生成。</span><span class="sxs-lookup"><span data-stu-id="d829d-118">A clustered index or full-text key index on the table being indexed gets altered, dropped, or rebuilt.</span></span>  
  
-   <span data-ttu-id="d829d-119">硬件故障或磁盘损坏导致全文目录遭到破坏。</span><span class="sxs-lookup"><span data-stu-id="d829d-119">A hardware failure or disk corruption results in the corruption of the full-text catalog.</span></span>  
  
-   <span data-ttu-id="d829d-120">全文索引的表所在的文件组转到脱机状态，或已设为只读。</span><span class="sxs-lookup"><span data-stu-id="d829d-120">A file group that contains the table being full-text indexed goes offline, or is made read-only.</span></span>  
  
 <span data-ttu-id="d829d-121">在任何重要的全文索引填充操作结束时，或在发现填充未完成时，应当查看爬网日志。</span><span class="sxs-lookup"><span data-stu-id="d829d-121">You should view the crawl log at the end of any significant full-text index population operation, or when you find that a population did not complete.</span></span>  
  
### <a name="unsigned-components"></a><span data-ttu-id="d829d-122">未签名的组件</span><span class="sxs-lookup"><span data-stu-id="d829d-122">Unsigned Components</span></span>  
 <span data-ttu-id="d829d-123">默认情况下，全文索引器要求它所加载的筛选器和断字符经过签名。</span><span class="sxs-lookup"><span data-stu-id="d829d-123">By default, the full-text indexer requires the filters and word breakers that it loads to be signed.</span></span> <span data-ttu-id="d829d-124">如果它们未经过签名（这种情况有时是在安装自定义组件时造成的），则必须将全文索引器配置为忽略签名验证。</span><span class="sxs-lookup"><span data-stu-id="d829d-124">If they are not signed, which is the case sometimes when custom components are installed, you must configure the full-text indexer to ignore signature verification.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d829d-125">忽略签名验证将降低 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的安全性。</span><span class="sxs-lookup"><span data-stu-id="d829d-125">Ignoring signature verification makes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] less secure.</span></span> <span data-ttu-id="d829d-126">我们建议您对所实现的所有组件进行签名，或确保您获得的所有组件都经过签名。</span><span class="sxs-lookup"><span data-stu-id="d829d-126">We recommend that you sign any components that you implement or ensure that any components that you acquire are signed.</span></span> <span data-ttu-id="d829d-127">有关对组件进行签名的信息，请参阅 [sp_fulltext_service (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d829d-127">For information about signing components, see [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  

  
##  <a name="full-text-index-in-inconsistent-state-after-transaction-log-restored"></a><a name="state"></a> <span data-ttu-id="d829d-128">对事务日志进行还原后全文索引处于不一致状态</span><span class="sxs-lookup"><span data-stu-id="d829d-128">Full-Text Index in Inconsistent State after Transaction Log Restored</span></span>  
 <span data-ttu-id="d829d-129">还原数据库的事务日志时可能会看到一条警告，指示全文索引处于不一致状态。</span><span class="sxs-lookup"><span data-stu-id="d829d-129">When restoring the transaction log of a database, you might see a warning indicating that the full-text index is not in a consistent state.</span></span> <span data-ttu-id="d829d-130">导致不一致的原因是在备份数据库之后，针对表的全文索引被修改了。</span><span class="sxs-lookup"><span data-stu-id="d829d-130">The reason for this is that the full-text index on a table was modified after the database was backed up.</span></span> <span data-ttu-id="d829d-131">若要使全文索引处于一致状态，必须对表执行完全填充（爬网）。</span><span class="sxs-lookup"><span data-stu-id="d829d-131">To bring the full-text index to a consistent state, you must run a full population (crawl) on the table.</span></span> <span data-ttu-id="d829d-132">有关详细信息，请参阅 [填充全文索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="d829d-132">For more information, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="d829d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d829d-133">See Also</span></span>  
 <span data-ttu-id="d829d-134">[ALTER FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d829d-134">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="d829d-135">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="d829d-135">Populate Full-Text Indexes</span></span>](../indexes/indexes.md)  
  
  
