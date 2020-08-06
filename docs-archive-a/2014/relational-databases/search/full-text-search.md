---
title: 全文搜索 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server]
ms.assetid: a0ce315d-f96d-4e5d-b4eb-ff76811cab75
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16303c34d44a056f1f505a2d1876b2ee23df994c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578774"
---
# <a name="full-text-search"></a><span data-ttu-id="32b0d-102">全文搜索</span><span class="sxs-lookup"><span data-stu-id="32b0d-102">Full-Text Search</span></span>
  <span data-ttu-id="32b0d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 中的全文搜索为用户和应用程序提供了对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中基于字符的数据运行全文查询的功能。</span><span class="sxs-lookup"><span data-stu-id="32b0d-103">Full-Text Search in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] lets users and applications run full-text queries against character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="32b0d-104">在可以对某一表运行全文查询之前，数据库管理员必须对该表创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="32b0d-104">Before you can run full-text queries on a table, the database administrator must create a full-text index on the table.</span></span> <span data-ttu-id="32b0d-105">全文索引包括表中一个或多个基于字符的列。</span><span class="sxs-lookup"><span data-stu-id="32b0d-105">The full-text index includes one or more character-based columns in the table.</span></span> <span data-ttu-id="32b0d-106">这些列可以具有下列任何一种数据类型：`char`、`varchar`、`nchar`、`nvarchar`、`text`、`ntext`、`image`、`xml` 或 `varbinary(max)` 和 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="32b0d-106">These columns can have any of the following data types: `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, or `varbinary(max)` and FILESTREAM.</span></span> <span data-ttu-id="32b0d-107">每个全文索引都对表中的一个或多个列创建索引，并且每个列都可以使用特定语言。</span><span class="sxs-lookup"><span data-stu-id="32b0d-107">Each full-text index indexes one or more columns from the table, and each column can use a specific language.</span></span>

 <span data-ttu-id="32b0d-108">全文查询根据特定语言（例如，英语或日语）的规则对词和短语进行操作，从而对全文索引中的文本数据执行语言搜索。</span><span class="sxs-lookup"><span data-stu-id="32b0d-108">Full-text queries perform linguistic searches against text data in full-text indexes by operating on words and phrases based on rules of a particular language such as English or Japanese.</span></span> <span data-ttu-id="32b0d-109">全文查询可以包括简单的词和短语，或者词或短语的多种形式。</span><span class="sxs-lookup"><span data-stu-id="32b0d-109">Full-text queries can include simple words and phrases or multiple forms of a word or phrase.</span></span> <span data-ttu-id="32b0d-110">全文查询返回包含至少一个匹配项（也称为“命中”）的所有文档。</span><span class="sxs-lookup"><span data-stu-id="32b0d-110">A full-text query returns any documents that contain at least one match (also known as a *hit*).</span></span> <span data-ttu-id="32b0d-111">当目标文档包含在全文查询中指定的所有字词，并符合任何其他搜索条件（如匹配的字词之间的距离）时，即发生匹配。</span><span class="sxs-lookup"><span data-stu-id="32b0d-111">A match occurs when a target document contains all the terms specified in the full-text query, and meets any other search conditions, such as the distance between the matching terms.</span></span>

> [!NOTE]
>  <span data-ttu-id="32b0d-112">全文搜索是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库引擎的一个可选组件。</span><span class="sxs-lookup"><span data-stu-id="32b0d-112">Full-text search is an optional component of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine.</span></span> <span data-ttu-id="32b0d-113">有关详细信息，请参阅[Install SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-113">For more information, see [Install SQL Server 2014](../../database-engine/install-windows/install-sql-server.md).</span></span>

##  <a name="what-can-i-do-with-full-text-search"></a><a name="benefits"></a><span data-ttu-id="32b0d-114">对于全文搜索，我该怎么办？</span><span class="sxs-lookup"><span data-stu-id="32b0d-114">What Can I Do with Full-Text Search?</span></span>
 <span data-ttu-id="32b0d-115">全文搜索适用于各种业务方案，如电子商务-在网站上搜索项目;法律公司-在法律数据存储库中搜索案例历史记录;或人力资源部门-将作业说明与存储的简历匹配。</span><span class="sxs-lookup"><span data-stu-id="32b0d-115">Full-text search is applicable to a wide range of business scenarios such as e-businesses-searching for items on a web site; law firms-searching for case histories in a legal-data repository; or human resources departments-matching job descriptions with stored resumes.</span></span> <span data-ttu-id="32b0d-116">不管是什么样的商业应用场景，全文搜索的基本管理任务和开发任务是相同的。</span><span class="sxs-lookup"><span data-stu-id="32b0d-116">The basic administrative and development tasks of full-text search are equivalent regardless of business scenarios.</span></span> <span data-ttu-id="32b0d-117">然而，在给定的商业应用场景中，可以对全文索引和查询进行优化以使其满足业务目标。</span><span class="sxs-lookup"><span data-stu-id="32b0d-117">However, in a given business scenario, full-text index and queries can be honed to meet business goals.</span></span> <span data-ttu-id="32b0d-118">例如，对于电子商务来说，最大限度地提高性能可能比对结果进行排序、检索的准确性（实际上有多少个现有匹配项是由全文查询返回的）或支持多种语言更重要。</span><span class="sxs-lookup"><span data-stu-id="32b0d-118">For example, for an e-business maximizing performance might be more important than ranking of results, recall accuracy (how many of the existing matches are actually returned by a full-text query), or supporting multiple languages.</span></span> <span data-ttu-id="32b0d-119">对于律师事务所来说，首先需要考虑的可能是返回所有可能存在的匹配项（“返回全部”\*\* 信息）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-119">For a law firm, returning every possible hit (*total recall* of information) might be the most important consideration.</span></span>

 [<span data-ttu-id="32b0d-120">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-120">In This Topic</span></span>](#top)

###  <a name="full-text-search-queries"></a><a name="queries"></a><span data-ttu-id="32b0d-121">全文搜索查询</span><span class="sxs-lookup"><span data-stu-id="32b0d-121">Full-Text Search Queries</span></span>
 <span data-ttu-id="32b0d-122">在将列添加到全文索引之后，用户和应用程序即可对列中的文本运行全文查询。</span><span class="sxs-lookup"><span data-stu-id="32b0d-122">After columns have been added to a full-text index, users and applications can run full-text queries on the text in the columns.</span></span> <span data-ttu-id="32b0d-123">这些查询可以搜索以下项中的任一项：</span><span class="sxs-lookup"><span data-stu-id="32b0d-123">These queries can search for any of the following:</span></span>

-   <span data-ttu-id="32b0d-124">一个或多个特定的词或短语（“简单词”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-124">One or more specific words or phrases (*simple term*)</span></span>

-   <span data-ttu-id="32b0d-125">以指定文本开头的词或短语（“前缀词”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-125">A word or a phrase where the words begin with specified text (*prefix term*)</span></span>

-   <span data-ttu-id="32b0d-126">特定词的变形（“派生词”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-126">Inflectional forms of a specific word (*generation term*)</span></span>

-   <span data-ttu-id="32b0d-127">与另一个词或短语邻近的词或短语（“邻近词”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-127">A word or phrase close to another word or phrase (*proximity term*)</span></span>

-   <span data-ttu-id="32b0d-128">特定词的同义词形式（“同义词库”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-128">Synonymous forms of a specific word (*thesaurus*)</span></span>

-   <span data-ttu-id="32b0d-129">使用加权值的词或短语（“加权词”）</span><span class="sxs-lookup"><span data-stu-id="32b0d-129">Words or phrases using weighted values (*weighted term*)</span></span>

 <span data-ttu-id="32b0d-130">全文查询不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="32b0d-130">Full-text queries are not case-sensitive.</span></span> <span data-ttu-id="32b0d-131">例如对于 "Aluminum" 或 "aluminum"，搜索将返回相同的结果。</span><span class="sxs-lookup"><span data-stu-id="32b0d-131">For example, searching for "Aluminum" or "aluminum" returns the same results.</span></span>

 <span data-ttu-id="32b0d-132">全文查询使用一小组 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 谓词（CONTAINS 和 FREETEXT）和函数（CONTAINSTABLE 和 FREETEXTTABLE）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-132">Full-text queries use a small set of [!INCLUDE[tsql](../../../includes/tsql-md.md)] predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE).</span></span> <span data-ttu-id="32b0d-133">然而，给定商业应用场景的搜索目标会对全文查询的结构产生影响。</span><span class="sxs-lookup"><span data-stu-id="32b0d-133">However, the search goals of a given business scenario influence the structure of the full-text queries.</span></span> <span data-ttu-id="32b0d-134">例如：</span><span class="sxs-lookup"><span data-stu-id="32b0d-134">For example:</span></span>

-   <span data-ttu-id="32b0d-135">电子商务（在网站上搜索产品）：</span><span class="sxs-lookup"><span data-stu-id="32b0d-135">e-business-searching for a product on a website:</span></span>

    ```
    SELECT product_id 
    FROM products 
    WHERE CONTAINS(product_description, "Snap Happy 100EZ"
        OR FORMSOF(THESAURUS,'Snap Happy')
        OR '100EZ') 
    AND product_cost < 200 ;
    ```

-   <span data-ttu-id="32b0d-136">招聘员工（搜索具有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用经验的职位候选人）：</span><span class="sxs-lookup"><span data-stu-id="32b0d-136">Recruitment scenario-searching for job candidates that have experience working with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

    ```
    SELECT candidate_name,SSN 
    FROM candidates 
    WHERE CONTAINS(candidate_resume,"SQL Server") AND candidate_division = 'DBA';
    ```

 <span data-ttu-id="32b0d-137">有关详细信息，请参阅 [使用全文搜索查询](query-with-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-137">For more information, see [Query with Full-Text Search](query-with-full-text-search.md).</span></span>

 [<span data-ttu-id="32b0d-138">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-138">In This Topic</span></span>](#top)

###  <a name="comparing-like-to-full-text-search"></a><a name="like"></a><span data-ttu-id="32b0d-139">与全文搜索的比较</span><span class="sxs-lookup"><span data-stu-id="32b0d-139">Comparing LIKE to Full-Text Search</span></span>
 <span data-ttu-id="32b0d-140">与全文搜索不同， [LIKE](/sql/t-sql/language-elements/like-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 谓词仅对字符模式有效。</span><span class="sxs-lookup"><span data-stu-id="32b0d-140">In contrast to full-text search, the [LIKE](/sql/t-sql/language-elements/like-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] predicate works on character patterns only.</span></span> <span data-ttu-id="32b0d-141">另外，不能使用 LIKE 谓词来查询格式化的二进制数据。</span><span class="sxs-lookup"><span data-stu-id="32b0d-141">Also, you cannot use the LIKE predicate to query formatted binary data.</span></span> <span data-ttu-id="32b0d-142">此外，对大量非结构化的文本数据执行 LIKE 查询要比对相同数据执行同样的全文查询慢得多。</span><span class="sxs-lookup"><span data-stu-id="32b0d-142">Furthermore, a LIKE query against a large amount of unstructured text data is much slower than an equivalent full-text query against the same data.</span></span> <span data-ttu-id="32b0d-143">对数百万行文本数据进行的 LIKE 查询可能需要几分钟的时间才能返回结果；而对于同样的数据，全文查询只需要几秒甚至更少的时间，具体取决于返回的行数。</span><span class="sxs-lookup"><span data-stu-id="32b0d-143">A LIKE query against millions of rows of text data can take minutes to return; whereas a full-text query can take only seconds or less against the same data, depending on the number of rows that are returned.</span></span>

 [<span data-ttu-id="32b0d-144">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-144">In This Topic</span></span>](#top)

##  <a name="components-and-architecture-of-full-text-search"></a><a name="architecture"></a><span data-ttu-id="32b0d-145">全文搜索的组件和体系结构</span><span class="sxs-lookup"><span data-stu-id="32b0d-145">Components and Architecture of Full-Text Search</span></span>
 <span data-ttu-id="32b0d-146">全文搜索体系结构包括以下进程：</span><span class="sxs-lookup"><span data-stu-id="32b0d-146">Full-text search architecture consists of the following processes:</span></span>

-   <span data-ttu-id="32b0d-147">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程 (sqlservr.exe)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-147">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process (sqlservr.exe).</span></span>

-   <span data-ttu-id="32b0d-148">筛选器后台程序宿主进程 (fdhost.exe)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-148">The filter daemon host process (fdhost.exe).</span></span>

     <span data-ttu-id="32b0d-149">为了安全起见，筛选器由称为筛选器后台程序宿主的单独进程加载。</span><span class="sxs-lookup"><span data-stu-id="32b0d-149">For security reasons, filters are loaded by separate processes called the filter daemon hosts.</span></span> <span data-ttu-id="32b0d-150">fdhost.exe 进程是由 FDHOST 启动器服务 (MSSQLFDLauncher) 创建的，这些进程使用 FDHOST 启动器服务帐户的安全凭据运行。</span><span class="sxs-lookup"><span data-stu-id="32b0d-150">The fdhost.exe processes are created by an FDHOST launcher service (MSSQLFDLauncher), and they run under the security credentials of the FDHOST launcher service account.</span></span> <span data-ttu-id="32b0d-151">因此，必须运行 FDHOST 启动器服务才能正常进行全文索引和全文查询。</span><span class="sxs-lookup"><span data-stu-id="32b0d-151">Therefore, the FDHOST launcher service must be running for full-text indexing and full-text querying to work.</span></span> <span data-ttu-id="32b0d-152">有关设置此服务的服务帐户的信息，请参阅 [设置用于全文筛选器后台程序启动器的服务帐户](set-the-service-account-for-the-full-text-filter-daemon-launcher.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-152">For information about setting the service account for this service, see [Set the Service Account for the Full-text Filter Daemon Launcher](set-the-service-account-for-the-full-text-filter-daemon-launcher.md).</span></span>

 <span data-ttu-id="32b0d-153">这两个进程包含全文搜索体系结构的各组件。</span><span class="sxs-lookup"><span data-stu-id="32b0d-153">These two processes contain the components of the full-text search architecture.</span></span> <span data-ttu-id="32b0d-154">下图概括了这些组件及其关系。</span><span class="sxs-lookup"><span data-stu-id="32b0d-154">These components and their relationships are summarized in the following illustration.</span></span> <span data-ttu-id="32b0d-155">该图后面的内容介绍了这些组件。</span><span class="sxs-lookup"><span data-stu-id="32b0d-155">The components are described after the illustration.</span></span>

 <span data-ttu-id="32b0d-156">![全文搜索体系结构](../../database-engine/media/ifts-arch.gif "全文搜索体系结构")</span><span class="sxs-lookup"><span data-stu-id="32b0d-156">![full-text search architecture](../../database-engine/media/ifts-arch.gif "full-text search architecture")</span></span>

 [<span data-ttu-id="32b0d-157">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-157">In This Topic</span></span>](#top)

###  <a name="sql-server-process"></a><a name="sqlprocess"></a><span data-ttu-id="32b0d-158">SQL Server 进程</span><span class="sxs-lookup"><span data-stu-id="32b0d-158">SQL Server Process</span></span>
 <span data-ttu-id="32b0d-159">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 进程使用全文搜索的以下组件：</span><span class="sxs-lookup"><span data-stu-id="32b0d-159">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process uses the following components for full-text search:</span></span>

-   <span data-ttu-id="32b0d-160">**用户表。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-160">**User tables.**</span></span> <span data-ttu-id="32b0d-161">这些表包含要进行全文索引的数据。</span><span class="sxs-lookup"><span data-stu-id="32b0d-161">These tables contain the data to be full-text indexed.</span></span>

-   <span data-ttu-id="32b0d-162">**全文收集器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-162">**Full-text gatherer.**</span></span> <span data-ttu-id="32b0d-163">全文收集器使用全文爬网线程。</span><span class="sxs-lookup"><span data-stu-id="32b0d-163">The full-text gatherer works with the full-text crawl threads.</span></span> <span data-ttu-id="32b0d-164">它负责计划和驱动对全文索引的填充，并负责监视全文目录。</span><span class="sxs-lookup"><span data-stu-id="32b0d-164">It is responsible for scheduling and driving the population of full-text indexes, and also for monitoring full-text catalogs.</span></span>

-   <span data-ttu-id="32b0d-165">**同义词库文件。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-165">**Thesaurus files.**</span></span> <span data-ttu-id="32b0d-166">这些文件包含搜索项的同义词。</span><span class="sxs-lookup"><span data-stu-id="32b0d-166">These files contain synonyms of search terms.</span></span> <span data-ttu-id="32b0d-167">有关详细信息，请参阅 [为全文搜索配置和管理同义词库文件](configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-167">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>

-   <span data-ttu-id="32b0d-168">**非索引字表对象。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-168">**Stoplist objects.**</span></span> <span data-ttu-id="32b0d-169">非索引字表对象包含对搜索无用的常见词列表。</span><span class="sxs-lookup"><span data-stu-id="32b0d-169">Stoplist objects contain a list of common words that are not useful for the search.</span></span> <span data-ttu-id="32b0d-170">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-170">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>

-   <span data-ttu-id="32b0d-171">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 查询处理器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-171">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query processor.**</span></span> <span data-ttu-id="32b0d-172">查询处理器编译并执行 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="32b0d-172">The query processor compiles and executes SQL queries.</span></span> <span data-ttu-id="32b0d-173">如果 SQL 查询包含全文搜索查询，则在编译和执行期间该查询都会发送到全文引擎。</span><span class="sxs-lookup"><span data-stu-id="32b0d-173">If a SQL query includes a full-text search query, the query is sent to the Full-Text Engine, both during compilation and during execution.</span></span> <span data-ttu-id="32b0d-174">查询结果将与全文索引相匹配。</span><span class="sxs-lookup"><span data-stu-id="32b0d-174">The query result is matched against the full-text index.</span></span>

-   <span data-ttu-id="32b0d-175">**全文引擎。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-175">**Full-Text Engine.**</span></span> <span data-ttu-id="32b0d-176">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的全文引擎现已与查询处理器完全集成。</span><span class="sxs-lookup"><span data-stu-id="32b0d-176">The Full-Text Engine in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is fully integrated with the query processor.</span></span> <span data-ttu-id="32b0d-177">全文引擎编译和执行全文查询。</span><span class="sxs-lookup"><span data-stu-id="32b0d-177">The Full-Text Engine compiles and executes full-text queries.</span></span> <span data-ttu-id="32b0d-178">作为查询执行的一部分，全文引擎可能会接收来自同义词库和非索引字表的输入。</span><span class="sxs-lookup"><span data-stu-id="32b0d-178">As part of query execution, the Full-Text Engine might receive input from the thesaurus and stoplist.</span></span>

-   <span data-ttu-id="32b0d-179">**索引编写器（索引器）。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-179">**Index writer (indexer).**</span></span> <span data-ttu-id="32b0d-180">索引编写器生成用于存储索引标记的结构。</span><span class="sxs-lookup"><span data-stu-id="32b0d-180">The index writer builds the structure that is used to store the indexed tokens.</span></span>

-   <span data-ttu-id="32b0d-181">**筛选器后台程序管理器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-181">**Filter daemon manager.**</span></span> <span data-ttu-id="32b0d-182">筛选器后台程序管理器负责监视全文引擎筛选器后台程序宿主的状态。</span><span class="sxs-lookup"><span data-stu-id="32b0d-182">The filter daemon manager is responsible for monitoring the status of the Full-Text Engine filter daemon host.</span></span>

 [<span data-ttu-id="32b0d-183">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-183">In This Topic</span></span>](#top)

###  <a name="filter-daemon-host-process"></a><a name="fdhostprocess"></a><span data-ttu-id="32b0d-184">筛选器后台程序宿主进程</span><span class="sxs-lookup"><span data-stu-id="32b0d-184">Filter Daemon Host Process</span></span>
 <span data-ttu-id="32b0d-185">筛选器后台程序宿主是一个由全文引擎启动的进程。</span><span class="sxs-lookup"><span data-stu-id="32b0d-185">The filter daemon host is a process that is started by the Full-Text Engine.</span></span> <span data-ttu-id="32b0d-186">它运行下列全文搜索组件，这些组件负责对表中的数据进行访问、筛选和断字，同时还负责对查询输入进行断字和提取词干。</span><span class="sxs-lookup"><span data-stu-id="32b0d-186">It runs the following full-text search components, which are responsible for accessing, filtering, and word breaking data from tables, as well as for word breaking and stemming the query input.</span></span>

 <span data-ttu-id="32b0d-187">筛选器后台程序宿主的组件如下：</span><span class="sxs-lookup"><span data-stu-id="32b0d-187">The components of the filter daemon host are as follows:</span></span>

-   <span data-ttu-id="32b0d-188">**协议处理程序。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-188">**Protocol handler.**</span></span> <span data-ttu-id="32b0d-189">此组件从内存中取出数据，以进行进一步的处理，并访问指定数据库的用户表中的数据。</span><span class="sxs-lookup"><span data-stu-id="32b0d-189">This component pulls the data from memory for further processing and accesses data from a user table in a specified database.</span></span> <span data-ttu-id="32b0d-190">其职责之一是从全文索引列中收集数据，并将所收集的数据传递给筛选器后台程序宿主，从而由该宿主根据需要应用筛选和断字符。</span><span class="sxs-lookup"><span data-stu-id="32b0d-190">One of its responsibilities is to gather data from the columns being full-text indexed and pass it to the filter daemon host, which will apply filtering and word breaker as required.</span></span>

-   <span data-ttu-id="32b0d-191">**筛选器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-191">**Filters.**</span></span> <span data-ttu-id="32b0d-192">某些数据类型需要筛选，然后才能为文档中的数据（包括 、、 或  列中的数据）创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="32b0d-192">Some data types require filtering before the data in a document can be full-text indexed, including data in `varbinary`, `varbinary(max)`, `image`, or `xml` columns.</span></span> <span data-ttu-id="32b0d-193">给定文档采用何种筛选器取决于文档类型。</span><span class="sxs-lookup"><span data-stu-id="32b0d-193">The filter used for a given document depends on its document type.</span></span> <span data-ttu-id="32b0d-194">例如，Microsoft Word (.doc) 文档、Microsoft Excel (.xls) 文档和 XML (.xml) 文档分别使用不同的筛选器。</span><span class="sxs-lookup"><span data-stu-id="32b0d-194">For example, different filters are used for Microsoft Word (.doc) documents, Microsoft Excel (.xls) documents, and XML (.xml) documents.</span></span> <span data-ttu-id="32b0d-195">然后，筛选器从文档中提取文本块区，删除嵌入的格式并保留文本，如有可能的话也会保留有关文本位置的信息。</span><span class="sxs-lookup"><span data-stu-id="32b0d-195">Then the filter extracts chunks of text from the document, removing embedded formatting and retaining the text and, potentially, information about the position of the text.</span></span> <span data-ttu-id="32b0d-196">结果将以文本化信息流的形式出现。</span><span class="sxs-lookup"><span data-stu-id="32b0d-196">The result is a stream of textual information.</span></span> <span data-ttu-id="32b0d-197">有关详细信息，请参阅 [配置和管理搜索筛选器](configure-and-manage-filters-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-197">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>

-   <span data-ttu-id="32b0d-198">**断字符和词干分析器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-198">**Word breakers and stemmers.**</span></span> <span data-ttu-id="32b0d-199">断字符是特定于语言的组件，它根据给定语言的词汇规则查找词边界（“断字”）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-199">A word breaker is a language-specific component that finds word boundaries based on the lexical rules of a given language (*word breaking*).</span></span> <span data-ttu-id="32b0d-200">每个断字符都与用于组合动词及执行变形扩展的特定于语言的词干分析器组件相关联。</span><span class="sxs-lookup"><span data-stu-id="32b0d-200">Each word breaker is associated with a language-specific stemmer component that conjugates verbs and performs inflectional expansions.</span></span> <span data-ttu-id="32b0d-201">在创建索引时，筛选器后台程序宿主使用断字符和词干分析器来对给定表列中的文本数据执行语言分析。</span><span class="sxs-lookup"><span data-stu-id="32b0d-201">At indexing time, the filter daemon host uses a word breaker and stemmer to perform linguistic analysis on the textual data from a given table column.</span></span> <span data-ttu-id="32b0d-202">与全文索引中的表列相关的语言将决定为列创建索引时要使用的断字符和词干分析器。</span><span class="sxs-lookup"><span data-stu-id="32b0d-202">The language that is associated with a table column in the full-text index determines which word breaker and stemmer are used for indexing the column.</span></span> <span data-ttu-id="32b0d-203">有关详细信息，请参阅 [配置和管理断字符和词干分析器以便搜索](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-203">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>

 [<span data-ttu-id="32b0d-204">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-204">In This Topic</span></span>](#top)

##  <a name="full-text-search-processing"></a><a name="processing"></a><span data-ttu-id="32b0d-205">全文搜索处理</span><span class="sxs-lookup"><span data-stu-id="32b0d-205">Full-Text Search Processing</span></span>
 <span data-ttu-id="32b0d-206">全文搜索由全文引擎提供支持。</span><span class="sxs-lookup"><span data-stu-id="32b0d-206">Full-text search is powered by the Full-Text Engine.</span></span> <span data-ttu-id="32b0d-207">全文引擎有两个角色：索引支持和查询支持。</span><span class="sxs-lookup"><span data-stu-id="32b0d-207">The Full-Text Engine has two roles: indexing support and querying support.</span></span>

###  <a name="full-text-indexing-process"></a><a name="indexing"></a><span data-ttu-id="32b0d-208">全文索引过程</span><span class="sxs-lookup"><span data-stu-id="32b0d-208">Full-Text Indexing Process</span></span>
 <span data-ttu-id="32b0d-209">全文填充（也称为爬网）开始后，全文引擎会将大批数据存入内存并通知筛选器后台程序宿主。</span><span class="sxs-lookup"><span data-stu-id="32b0d-209">When a full-text population (also known as a crawl) is initiated, the Full-Text Engine pushes large batches of data into memory and notifies the filter daemon host.</span></span> <span data-ttu-id="32b0d-210">宿主对数据进行筛选和断字，并将转换的数据转换为倒排词列表。</span><span class="sxs-lookup"><span data-stu-id="32b0d-210">The host filters and word breaks the data and converts the converted data into inverted word lists.</span></span> <span data-ttu-id="32b0d-211">然后，全文搜索从词列表中提取转换的数据，对其进行处理以删除非索引字，然后将某一批次的词列表永久保存到一个或多个倒排索引中。</span><span class="sxs-lookup"><span data-stu-id="32b0d-211">The full-text search then pulls the converted data from the word lists, processes the data to remove stopwords, and persists the word lists for a batch into one or more inverted indexes.</span></span>

 <span data-ttu-id="32b0d-212">对存储在或列中的数据编制索引时 `varbinary(max)` `image` ，筛选器（实现**IFilter**接口）将基于该 (数据的指定文件格式（例如，Word) ）来提取文本 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="32b0d-212">When indexing data stored in a `varbinary(max)` or `image` column, the filter, which implements the **IFilter** interface, extracts text based on the specified file format for that data (for example, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word).</span></span> <span data-ttu-id="32b0d-213">在某些情况下，筛选器组件要求将 `varbinary(max)` 或 `image` 数据写出到 filterdata 文件夹，而不是推送到内存。</span><span class="sxs-lookup"><span data-stu-id="32b0d-213">In some cases, the filter components require the `varbinary(max)`, or `image` data to be written out to the filterdata folder, instead of being pushed into memory.</span></span>

 <span data-ttu-id="32b0d-214">在处理过程中，通过断字符将收集到的文本数据分隔成各个单独的标记或关键字。</span><span class="sxs-lookup"><span data-stu-id="32b0d-214">As part of processing, the gathered text data is passed through a word breaker to separate the text into individual tokens, or keywords.</span></span> <span data-ttu-id="32b0d-215">用于词汇切分的语言将在列级指定，或者也可以通过筛选器组件在 `varbinary(max)`、`image` 或 `xml` 数据内标识。</span><span class="sxs-lookup"><span data-stu-id="32b0d-215">The language used for tokenization is specified at the column level, or can be identified within `varbinary(max)`, `image`, or `xml` data by the filter component.</span></span>

 <span data-ttu-id="32b0d-216">还可能会进行其他处理以删除非索引字，并在将标记存储到全文索引或索引片断之前对其进行规范化。</span><span class="sxs-lookup"><span data-stu-id="32b0d-216">Additional processing may be performed to remove stopwords, and to normalize tokens before they are stored in the full-text index or an index fragment.</span></span>

 <span data-ttu-id="32b0d-217">填充完成后，将触发最终的合并过程，以便将索引碎片合并为一个主全文索引。</span><span class="sxs-lookup"><span data-stu-id="32b0d-217">When a population has completed, a final merge process is triggered that merges the index fragments together into one master full-text index.</span></span> <span data-ttu-id="32b0d-218">由于只需要查询主索引而不需要查询大量索引碎片，因此这将提高查询性能，并且可以使用更好的计分统计信息来得出相关性排名。</span><span class="sxs-lookup"><span data-stu-id="32b0d-218">This results in improved query performance since only the master index needs to be queried rather than a number of index fragments, and better scoring statistics may be used for relevance ranking.</span></span>

 [<span data-ttu-id="32b0d-219">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-219">In This Topic</span></span>](#top)

###  <a name="full-text-querying-process"></a><a name="querying"></a><span data-ttu-id="32b0d-220">全文查询过程</span><span class="sxs-lookup"><span data-stu-id="32b0d-220">Full-Text Querying Process</span></span>
 <span data-ttu-id="32b0d-221">查询处理器将查询的全文部分传递到全文引擎以进行处理。</span><span class="sxs-lookup"><span data-stu-id="32b0d-221">The query processor passes the full-text portions of a query to the Full-Text Engine for processing.</span></span> <span data-ttu-id="32b0d-222">全文引擎执行断字，此外，它还可以执行同义词库扩展、词干分析以及非索引字（干扰词）处理。</span><span class="sxs-lookup"><span data-stu-id="32b0d-222">The Full-Text Engine performs word breaking and, optionally, thesaurus expansions, stemming, and stopword (noise-word) processing.</span></span> <span data-ttu-id="32b0d-223">然后，查询的全文部分以 SQL 运算符的形式表示，主要作为流式表值函数 (STVF)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-223">Then the full-text portions of the query are represented in the form of SQL operators, primarily as streaming table-valued functions (STVFs).</span></span> <span data-ttu-id="32b0d-224">在查询执行过程中，这些 STVF 访问倒排索引以检索正确结果。</span><span class="sxs-lookup"><span data-stu-id="32b0d-224">During query execution, these STVFs access the inverted index to retrieve the correct results.</span></span> <span data-ttu-id="32b0d-225">此时会将结果返回给客户端，或者先将它们进一步处理，再将它们返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="32b0d-225">The results are either returned to the client at this point, or they are further processed before being returned to the client.</span></span>

 [<span data-ttu-id="32b0d-226">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-226">In This Topic</span></span>](#top)

##  <a name="linguistic-components-and-language-support-in-full-text-search"></a><a name="components"></a><span data-ttu-id="32b0d-227">全文搜索中的语言组件和语言支持</span><span class="sxs-lookup"><span data-stu-id="32b0d-227">Linguistic Components and Language Support in Full-Text Search</span></span>
 <span data-ttu-id="32b0d-228">全文搜索支持大约 50 种不同语言，例如英语、西班牙语、中文、日语、阿拉伯语、孟加拉语和印地语。</span><span class="sxs-lookup"><span data-stu-id="32b0d-228">Full-text search supports almost 50 diverse languages, such as English, Spanish, Chinese, Japanese, Arabic, Bangla, and Hindi.</span></span> <span data-ttu-id="32b0d-229">有关支持的全文语言的完整列表，请参阅 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-229">For a complete list of the supported full-text languages, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span> <span data-ttu-id="32b0d-230">全文索引中包含的每一列与一个 Microsoft Windows 区域设置标识符 (LCID) 相关联，每个区域设置标识符等同于全文搜索支持的一种语言。</span><span class="sxs-lookup"><span data-stu-id="32b0d-230">Each of the columns contained in the full-text index is associated with a Microsoft Windows locale identifier (LCID) that equates to a language that is supported by full-text search.</span></span> <span data-ttu-id="32b0d-231">例如，LCID 1033 等于美国英语，LCID 2057 等于英国英语。</span><span class="sxs-lookup"><span data-stu-id="32b0d-231">For example, LCID 1033 equates to U.S English, and LCID 2057 equates to British English.</span></span> <span data-ttu-id="32b0d-232">对于每种支持的全文语言， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 提供语言组件以支持对以该语言存储的全文数据进行索引和查询。</span><span class="sxs-lookup"><span data-stu-id="32b0d-232">For each supported full-text language, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides linguistic components that support indexing and querying full-text data that is stored in that language.</span></span>

 <span data-ttu-id="32b0d-233">语言特有组件包括：</span><span class="sxs-lookup"><span data-stu-id="32b0d-233">Language-specific components include the following:</span></span>

-   <span data-ttu-id="32b0d-234">**断字符和词干分析器。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-234">**Word breakers and stemmers.**</span></span> <span data-ttu-id="32b0d-235">断字符根据给定语言的词汇规则查找词边界（“断字”）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-235">A word breaker finds word boundaries based on the lexical rules of a given language (*word breaking*).</span></span> <span data-ttu-id="32b0d-236">每个断字符与一个词干分析器相关联，该词干分析器组合了同一种语言的动词。</span><span class="sxs-lookup"><span data-stu-id="32b0d-236">Each word breaker is associated with a stemmer that conjugates verbs for the same language.</span></span> <span data-ttu-id="32b0d-237">有关详细信息，请参阅 [配置和管理断字符和词干分析器以便搜索](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-237">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>

-   <span data-ttu-id="32b0d-238">**非索引字表。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-238">**Stoplists.**</span></span> <span data-ttu-id="32b0d-239">提供系统非索引字表，其中包含一组基本非索引字（也称为干扰词）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-239">A system stoplist is provided that contains a basic set stopwords (also known as noise words).</span></span> <span data-ttu-id="32b0d-240">“非索引字”是对搜索没有任何帮助并且被全文查询忽略的词。</span><span class="sxs-lookup"><span data-stu-id="32b0d-240">A *stopword* is a word that does not help the search and is ignored by full-text queries.</span></span> <span data-ttu-id="32b0d-241">例如，在英语区域设置中，诸如“a”、“and”、“is”和“the”之类的词都被视为非索引字。</span><span class="sxs-lookup"><span data-stu-id="32b0d-241">For example, for the English locale words such as "a", "and", "is", and "the" are considered stopwords.</span></span> <span data-ttu-id="32b0d-242">通常情况下，需要配置一个或多个同义词库文件和非索引字表。</span><span class="sxs-lookup"><span data-stu-id="32b0d-242">Typically, you will need to configure one or more thesaurus files and stoplists.</span></span> <span data-ttu-id="32b0d-243">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-243">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>

-   <span data-ttu-id="32b0d-244">**同义词库文件。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-244">**Thesaurus files.**</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="32b0d-245">还会安装一个全局同义词库文件，并且还为每种全文语言安装一个同义词库文件。</span><span class="sxs-lookup"><span data-stu-id="32b0d-245">also installs a thesaurus file for each full-text language, as well as a global thesaurus file.</span></span> <span data-ttu-id="32b0d-246">安装的同义词库文件实际上是空的，不过可以编辑它们以便为特定语言或商业应用场景定义同义词。</span><span class="sxs-lookup"><span data-stu-id="32b0d-246">The installed thesaurus files are essentially empty, but you can edit them to define synonyms for a specific language or business scenario.</span></span> <span data-ttu-id="32b0d-247">通过开发针对全文数据定制的同义词库，您可以有效地扩大对这些数据的全文查询的范围。</span><span class="sxs-lookup"><span data-stu-id="32b0d-247">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="32b0d-248">有关详细信息，请参阅 [为全文搜索配置和管理同义词库文件](configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-248">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>

-   <span data-ttu-id="32b0d-249">**筛选器 (iFilter)。**</span><span class="sxs-lookup"><span data-stu-id="32b0d-249">**Filters (iFilters).**</span></span>  <span data-ttu-id="32b0d-250">对 `varbinary(max)`、`image` 或 `xml` 数据类型列中的文档进行索引时，需要使用筛选器来执行额外的处理工作。</span><span class="sxs-lookup"><span data-stu-id="32b0d-250">Indexing a document in a `varbinary(max)`, `image`, or `xml` data type column requires a filter to perform extra processing.</span></span> <span data-ttu-id="32b0d-251">此筛选器必须特定于文档类型（.doc、.pdf、.xls、.xml 等）。</span><span class="sxs-lookup"><span data-stu-id="32b0d-251">The filter must be specific to the document type (.doc, .pdf, .xls, .xml, and so forth).</span></span> <span data-ttu-id="32b0d-252">有关详细信息，请参阅 [配置和管理搜索筛选器](configure-and-manage-filters-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="32b0d-252">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>

 <span data-ttu-id="32b0d-253">断字符（和词干分析器）以及筛选器在筛选器后台程序宿主进程 (fdhost.exe) 中运行。</span><span class="sxs-lookup"><span data-stu-id="32b0d-253">Word breakers (and stemmers) and filters run in the filter daemon host process (fdhost.exe).</span></span>

 [<span data-ttu-id="32b0d-254">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-254">In This Topic</span></span>](#top)

##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="32b0d-255">相关任务</span><span class="sxs-lookup"><span data-stu-id="32b0d-255">Related Tasks</span></span>

-   [<span data-ttu-id="32b0d-256">全文搜索入门</span><span class="sxs-lookup"><span data-stu-id="32b0d-256">Get Started with Full-Text Search</span></span>](get-started-with-full-text-search.md)

-   <span data-ttu-id="32b0d-257">撰写全文查询</span><span class="sxs-lookup"><span data-stu-id="32b0d-257">Writing Full-Text Queries</span></span>

    -   [<span data-ttu-id="32b0d-258">使用全文搜索查询</span><span class="sxs-lookup"><span data-stu-id="32b0d-258">Query with Full-Text Search</span></span>](query-with-full-text-search.md)

    -   [<span data-ttu-id="32b0d-259">使用 NEAR 搜索与另一个词邻近的词</span><span class="sxs-lookup"><span data-stu-id="32b0d-259">Search for Words Close to Another Word with NEAR</span></span>](search-for-words-close-to-another-word-with-near.md)

    -   [<span data-ttu-id="32b0d-260">使用 RANK 限制搜索结果</span><span class="sxs-lookup"><span data-stu-id="32b0d-260">Limit Search Results with RANK</span></span>](limit-search-results-with-rank.md)

    -   [<span data-ttu-id="32b0d-261">改进全文查询的性能</span><span class="sxs-lookup"><span data-stu-id="32b0d-261">Improve the Performance of Full-Text Queries</span></span>](improve-the-performance-of-full-text-queries.md)

    -   [<span data-ttu-id="32b0d-262">使用搜索属性列表搜索文档属性</span><span class="sxs-lookup"><span data-stu-id="32b0d-262">Search Document Properties with Search Property Lists</span></span>](search-document-properties-with-search-property-lists.md)

    -   [<span data-ttu-id="32b0d-263">查找搜索属性的属性集 GUID 和属性整数 ID</span><span class="sxs-lookup"><span data-stu-id="32b0d-263">Find Property Set GUIDs and Property Integer IDs for Search Properties</span></span>](find-property-set-guids-and-property-integer-ids-for-search-properties.md)

-   <span data-ttu-id="32b0d-264">管理目录和索引</span><span class="sxs-lookup"><span data-stu-id="32b0d-264">Managing Catalogs and Indexes</span></span>

    -   [<span data-ttu-id="32b0d-265">创建和管理全文索引目录</span><span class="sxs-lookup"><span data-stu-id="32b0d-265">Create and Manage Full-Text Catalogs</span></span>](create-and-manage-full-text-catalogs.md)

    -   [<span data-ttu-id="32b0d-266">创建和管理全文索引</span><span class="sxs-lookup"><span data-stu-id="32b0d-266">Create and Manage Full-Text Indexes</span></span>](create-and-manage-full-text-indexes.md)

    -   [<span data-ttu-id="32b0d-267">创建全文索引时选择语言</span><span class="sxs-lookup"><span data-stu-id="32b0d-267">Choose a Language When Creating a Full-Text Index</span></span>](choose-a-language-when-creating-a-full-text-index.md)

    -   [<span data-ttu-id="32b0d-268">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="32b0d-268">Populate Full-Text Indexes</span></span>](populate-full-text-indexes.md)

    -   [<span data-ttu-id="32b0d-269">管理全文索引</span><span class="sxs-lookup"><span data-stu-id="32b0d-269">Manage Full-Text Indexes</span></span>](../../database-engine/manage-full-text-indexes.md)

    -   [<span data-ttu-id="32b0d-270">改进全文索引的性能</span><span class="sxs-lookup"><span data-stu-id="32b0d-270">Improve the Performance of Full-Text Indexes</span></span>](improve-the-performance-of-full-text-indexes.md)

    -   [<span data-ttu-id="32b0d-271">排除全文索引故障</span><span class="sxs-lookup"><span data-stu-id="32b0d-271">Troubleshoot Full-Text Indexing</span></span>](troubleshoot-full-text-indexing.md)

    -   [<span data-ttu-id="32b0d-272">备份和还原全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="32b0d-272">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](back-up-and-restore-full-text-catalogs-and-indexes.md)

-   <span data-ttu-id="32b0d-273">管理语言组件</span><span class="sxs-lookup"><span data-stu-id="32b0d-273">Managing the Linguistic Components</span></span>

    -   [<span data-ttu-id="32b0d-274">配置和管理搜索筛选器</span><span class="sxs-lookup"><span data-stu-id="32b0d-274">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)

    -   [<span data-ttu-id="32b0d-275">配置和管理断字符和词干分析器以便搜索</span><span class="sxs-lookup"><span data-stu-id="32b0d-275">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)

    -   [<span data-ttu-id="32b0d-276">查看或更改注册的筛选器和断字符</span><span class="sxs-lookup"><span data-stu-id="32b0d-276">View or Change Registered Filters and Word Breakers</span></span>](view-or-change-registered-filters-and-word-breakers.md)

    -   [<span data-ttu-id="32b0d-277">将搜索功能所使用的断字符还原到以前的版本</span><span class="sxs-lookup"><span data-stu-id="32b0d-277">Revert the Word Breakers Used by Search to the Previous Version</span></span>](revert-the-word-breakers-used-by-search-to-the-previous-version.md)

    -   [<span data-ttu-id="32b0d-278">更改用于美国英语和英国英语的断字符</span><span class="sxs-lookup"><span data-stu-id="32b0d-278">Change the Word Breaker Used for US English and UK English</span></span>](change-the-word-breaker-used-for-us-english-and-uk-english.md)

    -   [<span data-ttu-id="32b0d-279">使用自定义词典自定义断字符的行为</span><span class="sxs-lookup"><span data-stu-id="32b0d-279">Customize the Behavior of Word Breakers with a Custom Dictionary</span></span>](customize-the-behavior-of-word-breakers-with-a-custom-dictionary.md)

    -   [<span data-ttu-id="32b0d-280">为全文搜索配置和管理非索引字和非索引字表</span><span class="sxs-lookup"><span data-stu-id="32b0d-280">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)

    -   [<span data-ttu-id="32b0d-281">为全文搜索配置和管理同义词库文件</span><span class="sxs-lookup"><span data-stu-id="32b0d-281">Configure and Manage Thesaurus Files for Full-Text Search</span></span>](configure-and-manage-thesaurus-files-for-full-text-search.md)

-   <span data-ttu-id="32b0d-282">管理全文搜索</span><span class="sxs-lookup"><span data-stu-id="32b0d-282">Managing Full-Text Search</span></span>

    -   [<span data-ttu-id="32b0d-283">管理和监视服务器实例的全文搜索</span><span class="sxs-lookup"><span data-stu-id="32b0d-283">Manage and Monitor Full-Text Search for a Server Instance</span></span>](manage-and-monitor-full-text-search-for-a-server-instance.md)

    -   [<span data-ttu-id="32b0d-284">设置用于全文筛选器后台程序启动器的服务帐户</span><span class="sxs-lookup"><span data-stu-id="32b0d-284">Set the Service Account for the Full-text Filter Daemon Launcher</span></span>](set-the-service-account-for-the-full-text-filter-daemon-launcher.md)

-   [<span data-ttu-id="32b0d-285">升级全文搜索</span><span class="sxs-lookup"><span data-stu-id="32b0d-285">Upgrade Full-Text Search</span></span>](upgrade-full-text-search.md)

 [<span data-ttu-id="32b0d-286">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-286">In This Topic</span></span>](#top)

##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="32b0d-287">相关内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-287">Related Content</span></span>

-   [<span data-ttu-id="32b0d-288">全文搜索 DDL、函数、存储过程和视图</span><span class="sxs-lookup"><span data-stu-id="32b0d-288">Full-Text Search DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)

 [<span data-ttu-id="32b0d-289">本主题内容</span><span class="sxs-lookup"><span data-stu-id="32b0d-289">In This Topic</span></span>](#top)
