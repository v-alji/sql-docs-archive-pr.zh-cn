---
title: 全文搜索入门 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text indexes [SQL Server], creating
- full-text search [SQL Server], about
- full-text search [SQL Server], setting up
ms.assetid: 1fa628ba-0ee4-4d8f-b086-c4e52962ca4a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: eec806bffba330ac3ab995c1b3bfd3504589ecfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688785"
---
# <a name="get-started-with-full-text-search"></a><span data-ttu-id="7e5a2-102">全文搜索入门</span><span class="sxs-lookup"><span data-stu-id="7e5a2-102">Get Started with Full-Text Search</span></span>
  <span data-ttu-id="7e5a2-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的数据库在默认情况下支持全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-103">Databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are full-text enabled by default.</span></span> <span data-ttu-id="7e5a2-104">不过，若要对表使用全文索引，必须对要使用全文引擎访问的表列设置全文索引功能。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-104">However, to use a full-text index on a table, you must set up full-text indexing capability on the columns of the tables that you want to access using the Full-Text Engine.</span></span>  
  
##  <a name="configuring-a-database-for-full-text-search"></a><a name="configure"></a><span data-ttu-id="7e5a2-105">配置数据库以进行全文搜索</span><span class="sxs-lookup"><span data-stu-id="7e5a2-105">Configuring a Database for Full-Text Search</span></span>  
 <span data-ttu-id="7e5a2-106">对于任何应用场景，数据库管理员都要执行以下基本步骤来将数据库中的表列配置为可以进行全文搜索：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-106">For any scenario, a database administrator performs the following basic steps to configure table columns in a database for full-text search:</span></span>  
  
1.  <span data-ttu-id="7e5a2-107">创建全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-107">Create a full-text catalog.</span></span>  
  
2.  <span data-ttu-id="7e5a2-108">在要搜索的每个表中，按以下方法创建全文索引：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-108">On each table that you want to search, create a full-text index by:</span></span>  
  
    1.  <span data-ttu-id="7e5a2-109">标识要包含在全文索引中的各个文本列。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-109">Identify each text columns that you want to include in the full-text index.</span></span>  
  
    2.  <span data-ttu-id="7e5a2-110">如果给定列包含存储为二进制数据 (`varbinary(max)` 或 `image` 数据) 的文档，则必须 (*类型列*) 指定一个表列，该列标识要编制索引的列中的每个文档的类型。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-110">If a given column contains documents stored as binary data (`varbinary(max)`, or `image` data), you must specify a table column (the *type column*) that identifies the type of each document in the column being indexed.</span></span>  
  
    3.  <span data-ttu-id="7e5a2-111">指定对列中文档进行全文搜索时所使用的语言。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-111">Specify the language that you want full-text search to use on the documents in the column.</span></span>  
  
    4.  <span data-ttu-id="7e5a2-112">选择全文索引中要使用的更改跟踪机制，以跟踪基表及其列中的更改。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-112">Choose the change-tracking mechanism that you want to use on the full-text index to track changes in the base table and its columns.</span></span>  
  
 <span data-ttu-id="7e5a2-113">全文搜索通过使用以下“语言组件”\*\* 支持多种语言：断字符和词干分析器、包含非索引字（也称为“干扰词”）的非索引字表及同义词库文件。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-113">Full-text search supports multiple languages through the use of the following *linguistic components*: word breakers and stemmers, stoplists that contain stopwords (also known as noise words), and thesaurus files.</span></span> <span data-ttu-id="7e5a2-114">在某些情况下，同义词库文件和非索引字表需要由数据库管理员配置。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-114">Thesaurus files and, in some cases, stoplists require configuration by a database administrator.</span></span> <span data-ttu-id="7e5a2-115">给定同义词库文件支持使用相应语言的所有全文索引，给定非索引字表可以根据您的需要与尽可能多的全文索引相关联。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-115">A given thesaurus file supports all full-text indexes that use the corresponding language, and a given stoplist can be associated with as many full-text indexes as you want.</span></span>  
  
##  <a name="setting-up-a-full-text-catalog-and-index"></a><a name="setup"></a><span data-ttu-id="7e5a2-116">设置全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-116">Setting Up a Full-Text Catalog and Index</span></span>  
 <span data-ttu-id="7e5a2-117">这涉及以下基本步骤：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-117">This involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="7e5a2-118">创建全文目录来存储全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-118">Create a full-text catalog to store full-text indexes.</span></span>  
  
     <span data-ttu-id="7e5a2-119">每个全文索引必须属于一个全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-119">Each full-text index must belong to a full-text catalog.</span></span> <span data-ttu-id="7e5a2-120">您可以为每个全文索引创建一个单独的文本目录，也可以将多个全文索引与给定目录关联起来。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-120">You can create a separate text catalog for each full-text index, or you can associate multiple full-text indexes with a given catalog.</span></span> <span data-ttu-id="7e5a2-121">全文目录是虚拟对象，不属于任何文件组。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-121">A full-text catalog is a virtual object and does not belong to any filegroup.</span></span> <span data-ttu-id="7e5a2-122">该目录是表示一组全文索引的逻辑概念。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-122">The catalog is a logical concept that refers to a group of full-text indexes.</span></span>  
  
2.  <span data-ttu-id="7e5a2-123">对表或索引视图创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-123">Create a full-text index on the table or indexed view.</span></span>  
  
     <span data-ttu-id="7e5a2-124">全文索引是一种特殊类型的基于标记的功能性索引，由全文引擎生成和维护。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-124">A full-text index is a special type of token-based functional index that is built and maintained by the Full-Text Engine.</span></span> <span data-ttu-id="7e5a2-125">若要对表或视图创建全文搜索，则该表或视图必须具有唯一的、不可为 Null 的单列索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-125">To create full-text search on a table or view, it must have a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="7e5a2-126">全文引擎需要使用此唯一索引将表中的每一行映射到一个唯一的可压缩键。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-126">The Full-Text Engine requires this unique index to map each row in the table to a unique, compressible key.</span></span> <span data-ttu-id="7e5a2-127">全文索引可以包括 `char`、`varchar`、`nchar`、`nvarchar`、`text`、`ntext`、`image`、`xml`、`varbinary` 和 `varbinary(max)` 列。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-127">A full-text index can include `char`, `varchar`, `nchar`, `nvarchar`, `text`, `ntext`, `image`, `xml`, `varbinary`, and `varbinary(max)` columns.</span></span> <span data-ttu-id="7e5a2-128">有关详细信息，请参阅 [创建和管理全文索引](create-and-manage-full-text-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-128">For more information, see [Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md).</span></span>  
  
 <span data-ttu-id="7e5a2-129">在了解如何创建全文索引之前，请务必考虑它们与普通 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 索引的不同之处。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-129">Before learning about creating full-text indexes, it is important to consider how they differ from regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes.</span></span> <span data-ttu-id="7e5a2-130">下表列出差异。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-130">The following table lists the differences.</span></span>  
  
|<span data-ttu-id="7e5a2-131">全文索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-131">Full-text indexes</span></span>|<span data-ttu-id="7e5a2-132">普通 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-132">Regular SQL Server indexes</span></span>|  
|------------------------|--------------------------------|  
|<span data-ttu-id="7e5a2-133">每个表只允许有一个全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-133">Only one full-text index allowed per table.</span></span>|<span data-ttu-id="7e5a2-134">每个表允许有多个普通索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-134">Several regular indexes allowed per table.</span></span>|  
|<span data-ttu-id="7e5a2-135">将数据添加到全文索引的操作称为“填充”，可以通过计划或特定请求来请求填充，也可以在添加新数据时自动填充。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-135">The addition of data to full-text indexes, called a *population*, can be requested through either a schedule or a specific request, or can occur automatically with the addition of new data.</span></span>|<span data-ttu-id="7e5a2-136">当插入、更新或删除作为其基础的数据时自动更新。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-136">Updated automatically when the data upon which they are based is inserted, updated, or deleted.</span></span>|  
|<span data-ttu-id="7e5a2-137">在同一个数据库内分组为一个或多个全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-137">Grouped within the same database into one or more full-text catalogs.</span></span>|<span data-ttu-id="7e5a2-138">不分组。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-138">Not grouped.</span></span>|  
  
  
##  <a name="choosing-options-for-a-full-text-index"></a><a name="options"></a><span data-ttu-id="7e5a2-139">选择全文索引的选项</span><span class="sxs-lookup"><span data-stu-id="7e5a2-139">Choosing Options for a Full-Text Index</span></span>  
 <span data-ttu-id="7e5a2-140">本节涵盖以下内容：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-140">This section covers the following:</span></span>  
  
-   <span data-ttu-id="7e5a2-141">选择列语言</span><span class="sxs-lookup"><span data-stu-id="7e5a2-141">Choosing the column language</span></span>  
  
-   <span data-ttu-id="7e5a2-142">选择全文索引的文件组</span><span class="sxs-lookup"><span data-stu-id="7e5a2-142">Choosing a filegroup for a full-text index</span></span>  
  
-   <span data-ttu-id="7e5a2-143">将全文索引分配到全文目录</span><span class="sxs-lookup"><span data-stu-id="7e5a2-143">Assigning the full-text index to a full-text catalog</span></span>  
  
-   <span data-ttu-id="7e5a2-144">将非索引字表与全文索引关联</span><span class="sxs-lookup"><span data-stu-id="7e5a2-144">Associating a stoplist with the full-text index</span></span>  
  
-   <span data-ttu-id="7e5a2-145">更新全文索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-145">Updating a full-text index</span></span>  
  
### <a name="choosing-the-column-language"></a><span data-ttu-id="7e5a2-146">选择列语言</span><span class="sxs-lookup"><span data-stu-id="7e5a2-146">Choosing the Column Language</span></span>  
 <span data-ttu-id="7e5a2-147">有关在选择列语言时要注意的事项的信息，请参阅[创建全文索引时选择语言](choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-147">For information about things to consider when you are choosing the column language, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
### <a name="choosing-a-filegroup-for-a-full-text-index"></a><span data-ttu-id="7e5a2-148">选择全文索引的文件组</span><span class="sxs-lookup"><span data-stu-id="7e5a2-148">Choosing a Filegroup for a Full-Text Index</span></span>  
 <span data-ttu-id="7e5a2-149">生成全文索引是一个需要大量占用 I/O 的过程（它需要频繁地从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 读取数据，然后将筛选后的数据传播到全文索引）。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-149">The process of building a full-text index is fairly I/O intensive (on a high level, it consists of reading data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then propagating the filtered data to the full-text index).</span></span> <span data-ttu-id="7e5a2-150">最佳做法是将全文索引置于最适于最大程度地提高 I/O 性能的数据库文件组中，或者将全文索引置于另一个卷的其他文件组中。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-150">As a best practice, locate a full-text index in the database filegroup that is best for maximizing I/O performance or locate the full-text indexes in a different filegroup on another volume.</span></span>  
  
 <span data-ttu-id="7e5a2-151">如果您非常注重管理的方便性，建议您将表数据和所有关联的全文目录存储在同一文件组中。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-151">When ease of management is important to you, we recommend that you store table data and any affiliated full-text catalogs in the same filegroup.</span></span> <span data-ttu-id="7e5a2-152">出于性能的考虑，有时您可能需要将表数据和全文索引置于存储在不同卷上的不同文件组中，以便最大化 I/O 并行度。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-152">Sometimes, for performance reasons, you might want to have the table data and the full-text index in different filegroups that are stored on different volumes to maximize I/O parallelism.</span></span>  
  
  
### <a name="assigning-the-full-text-index-to-a-full-text-catalog"></a><span data-ttu-id="7e5a2-153">将全文索引分配到全文目录</span><span class="sxs-lookup"><span data-stu-id="7e5a2-153">Assigning the Full-Text Index to a Full-Text Catalog</span></span>  
 <span data-ttu-id="7e5a2-154">计划表的全文索引在全文目录中的位置非常重要。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-154">It is important to plan the placement of full-text indexes for tables in full-text catalogs.</span></span>  
  
 <span data-ttu-id="7e5a2-155">建议将具有相同更新特征的表（如更改次数少的与更改次数多的，或者在一天中某个特定时段内频繁更改的表）关联在一起，并置于同一全文目录下。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-155">We recommend associating tables with the same update characteristics (such as small number of changes versus large number of changes, or tables that change frequently during a particular time of day) together under the same full-text catalog.</span></span> <span data-ttu-id="7e5a2-156">通过设置全文目录填充计划，会使全文索引与表保持同步，且在数据库活动较多时不会对数据库服务器的资源使用产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-156">By setting up full-text catalog population schedules, full-text indexes stay synchronous with the tables without adversely affecting the resource usage of the database server during periods of high database activity.</span></span>  
  
 <span data-ttu-id="7e5a2-157">将表分配到全文目录时，应考虑下列准则：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-157">When you assign a table to a full-text catalog, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="7e5a2-158">始终选择可用于全文唯一键的最小唯一索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-158">Always select the smallest unique index available for your full-text unique key.</span></span> <span data-ttu-id="7e5a2-159"> (4 字节的、基于整数的索引是最佳的。 ) 这样可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 显著减少文件系统中 Search 服务所需的资源。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-159">(A 4-byte, integer-based index is optimal.) This reduces the resources required by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search service in the file system significantly.</span></span> <span data-ttu-id="7e5a2-160">如果主键较大（超过 100 个字节），可以考虑选择表中的另一个唯一索引（或创建另一个唯一索引）来作为全文唯一键。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-160">If the primary key is large (over 100 bytes), consider choosing another unique index in the table (or creating another unique index) as the full-text unique key.</span></span> <span data-ttu-id="7e5a2-161">否则，如果全文唯一键的大小超过所允许的最大值（900 个字节），全文填充将无法继续进行。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-161">Otherwise, if the full-text unique key size exceeds the maximum size allowed (900 bytes), full-text population will not be able to proceed.</span></span>  
  
-   <span data-ttu-id="7e5a2-162">如果创建索引的表有数百万行，请将该表分配到其自身的全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-162">If you are indexing a table that has millions of rows, assign the table to its own full-text catalog.</span></span>  
  
-   <span data-ttu-id="7e5a2-163">考虑要进行全文索引的表中发生的更改量以及总行数。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-163">Consider the amount of changes occurring in the tables being full-text indexed, as well as the total number of rows.</span></span> <span data-ttu-id="7e5a2-164">如果要更改的总行数与上次全文填充期间表中出现的行数合起来达到了数百万行，请将该表分配到其自身的全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-164">If the total number of rows being changed, together with the numbers of rows in the table present during the last full-text population, represents millions of rows, assign the table to its own full-text catalog.</span></span>  
  
  
### <a name="associating-a-stoplist-with-the-full-text-index"></a><span data-ttu-id="7e5a2-165">将非索引字表与全文索引关联</span><span class="sxs-lookup"><span data-stu-id="7e5a2-165">Associating a Stoplist with the Full-Text Index</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="7e5a2-166">引入了非索引字表。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-166">introduces stoplists.</span></span> <span data-ttu-id="7e5a2-167">“非索引字表”  是非索引字（也称为“干扰词”）的列表。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-167">A *stoplist* is a list of stopwords, also known as noise words.</span></span> <span data-ttu-id="7e5a2-168">非索引字表与每个全文索引相关联，因而该非索引字表中的词会应用于对该索引的全文查询。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-168">A stoplist is associated with each full-text index, and the words in that stoplist are applied to full-text queries on that index.</span></span> <span data-ttu-id="7e5a2-169">默认情况下，系统非索引字表与新的全文索引相关联。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-169">By default, the system stoplist is associated with a new full-text index.</span></span> <span data-ttu-id="7e5a2-170">不过，您也可以创建和使用您自己的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-170">However, you can create and use your own stoplist instead.</span></span> <span data-ttu-id="7e5a2-171">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-171">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="7e5a2-172">例如，以下[CREATE 全文非索引字表](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句通过从系统非索引字表进行复制来创建一个名为 myStoplist3 的新的全文非索引字表：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-172">For example, the following [CREATE FULLTEXT STOPLIST](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new full-text stoplist named myStoplist3 by copying from the system stoplist:</span></span>  
  
```  
CREATE FULLTEXT STOPLIST myStoplist FROM SYSTEM STOPLIST;  
GO  
```  
  
 <span data-ttu-id="7e5a2-173">下面的[ALTER 全文非索引字表](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将更改名为 myStoplist 的非索引字表，并为西班牙语添加单词 "en"，然后为法语添加单词 "en"：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-173">The following [ALTER FULLTEXT STOPLIST](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement alters a stoplist named myStoplist, adding the word 'en', first for Spanish and then for French:</span></span>  
  
```  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST MyStoplist ADD 'en' LANGUAGE 'French';  
GO  
```  
  
  
### <a name="updating-a-full-text-index"></a><span data-ttu-id="7e5a2-174">更新全文索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-174">Updating a Full-Text Index</span></span>  
 <span data-ttu-id="7e5a2-175">与普通 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 索引一样，全文索引可以在相关表中的数据修改时自动更新。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-175">Like regular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indexes, full-text indexes can be automatically updated as data is modified in the associated tables.</span></span> <span data-ttu-id="7e5a2-176">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-176">This is the default behavior.</span></span> <span data-ttu-id="7e5a2-177">另外，还可以手动或在预定的间隔更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-177">Alternatively, you can keep your full-text indexes up-to-date manually or at specified scheduled intervals.</span></span> <span data-ttu-id="7e5a2-178">由于填充全文索引可能极为耗费时间和资源，因此索引更新通常作为异步进程执行，该进程在后台运行，在基表中进行修改后使全文索引保持最新。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-178">Populating a full-text index can be time-consuming and resource-intensive, therefore, index updating is usually performed as an asynchronous process that runs in the background and keeps the full-text index up to date after modifications in the base table.</span></span> <span data-ttu-id="7e5a2-179">在基表中进行每次更改后立即更新全文索引可能会占用大量的资源。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-179">Updating a full-text index immediately after each change in the base table can be resource-intensive.</span></span> <span data-ttu-id="7e5a2-180">因此，如果更新/插入/删除操作非常频繁，您可能会发现查询性能有所降低。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-180">Therefore, if you have a very high update/insert/delete rate, you might experience some degradation in query performance.</span></span> <span data-ttu-id="7e5a2-181">如果出现这种情况，可以考虑制定一个手动的更改跟踪更新计划，以便按一定的间隔更新大量的更改，从而避免与查询争用资源。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-181">If this occurs, consider scheduling manual change tracking updates to keep up with the numerous changes from time to time, rather than competing with queries for resources.</span></span>  
  
 <span data-ttu-id="7e5a2-182">若要监视填充状态，请使用 FULLTEXTCATALOGPROPERTY 或 OBJECTPROPERTYEX 函数。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-182">To monitor the population status, use either the FULLTEXTCATALOGPROPERTY or OBJECTPROPERTYEX functions.</span></span> <span data-ttu-id="7e5a2-183">若要获得目录填充状态，请运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-183">To get the catalog population status, run the following statement:</span></span>  
  
```  
SELECT FULLTEXTCATALOGPROPERTY('AdvWksDocFTCat', 'Populatestatus');  
```  
  
 <span data-ttu-id="7e5a2-184">通常，如果正在进行完全填充，则返回的结果为 1。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-184">Typically, if a full population is in progress, the result returned is 1.</span></span>  
  
  
##  <a name="example-setting-up-full-text-search"></a><a name="example"></a><span data-ttu-id="7e5a2-185">示例：设置全文搜索</span><span class="sxs-lookup"><span data-stu-id="7e5a2-185">Example: Setting Up Full-Text Search</span></span>  
 <span data-ttu-id="7e5a2-186">下面的示例由两部分组成，首先对 AdventureWorks 数据库创建名为 `AdvWksDocFTCat` 的全文目录，然后对 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中的 `Document` 表创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-186">The following two-part example creates a full-text catalog named `AdvWksDocFTCat` on the AdventureWorks database and then creates a full-text index on the `Document` table in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="7e5a2-187">此语句将在安装过程中指定的默认位置创建全文目录。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-187">This statement creates the full-text catalog in the default directory specified during setup.</span></span> <span data-ttu-id="7e5a2-188">将在默认目录下创建名为 `AdvWksDocFTCat` 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-188">The folder named `AdvWksDocFTCat` is in the default directory.</span></span>  
  
1.  <span data-ttu-id="7e5a2-189">为了创建名为 `AdvWksDocFTCat`的全文目录，此示例使用了 [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-189">To create a full-text catalog named `AdvWksDocFTCat`, the example uses a [CREATE FULLTEXT CATALOG](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) statement:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    CREATE FULLTEXT CATALOG AdvWksDocFTCat;  
    ```  
  
2.  <span data-ttu-id="7e5a2-190">在对 Document 表创建全文索引之前，请确保该表具有唯一的、不可为 Null 的单列索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-190">Before you can create a full-text index on the Document table, ensure that the table has a unique, single-column, non-nullable index.</span></span> <span data-ttu-id="7e5a2-191">下面的 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) 语句可对 Document 表的 DocumentID 列创建唯一索引 `ui_ukDoc`：</span><span class="sxs-lookup"><span data-stu-id="7e5a2-191">The following [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement creates a unique index, `ui_ukDoc`, on the DocumentID column of the Document table:</span></span>  
  
    ```  
    CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
    ```  
  
3.  <span data-ttu-id="7e5a2-192">具有唯一键后，即可使用下面的 `Document` CREATE FULLTEXT INDEX [语句对](/sql/t-sql/statements/create-fulltext-index-transact-sql) 表创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-192">After you have a unique key, you can create a full-text index on the `Document` table by using the following [CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) statement.</span></span>  
  
    ```  
    CREATE FULLTEXT INDEX ON Production.Document  
    (  
        Document                         --Full-text index column name   
            TYPE COLUMN FileExtension    --Name of column that contains file type information  
            Language 2057                 --2057 is the LCID for British English  
    )  
    KEY INDEX ui_ukDoc ON AdvWksDocFTCat --Unique index  
    WITH CHANGE_TRACKING AUTO            --Population type;  
    GO  
  
    ```  
  
     <span data-ttu-id="7e5a2-193">此示例中定义的 TYPE COLUMN 指定表中的类型列，该列包含“Document”列（为二进制类型）的每一行中文档的类型。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-193">The TYPE COLUMN defined in this example specifies the type column in the table that contains the type of the document in each row of the column 'Document' (which is of binary type).</span></span> <span data-ttu-id="7e5a2-194">"类型" 列将用户提供的文件扩展名（".doc"、".xls" 等）存储在给定行中的文档中。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-194">The type column stores the user-supplied file extension-".doc", ".xls", and so on-of the document in a given row.</span></span> <span data-ttu-id="7e5a2-195">全文引擎使用给定行中的文件扩展名调用正确的筛选器，以用于分析该行中的数据。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-195">The Full-Text Engine uses the file extension in a given row to invoke the correct filter to use for parsing the data in that row.</span></span> <span data-ttu-id="7e5a2-196">在该筛选器对该行的二进制数据进行分析后，指定的断字符将分析其内容（在此示例中，使用的是英国英语的断字符）。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-196">After the filter has parsed the binary data of the row, the specified word breaker will parse the content (in this example, the word breaker for British English is used).</span></span> <span data-ttu-id="7e5a2-197">请注意，仅在进行索引时，或者在对全文索引启用了自动更改跟踪的情况下用户在基表中插入或更新列时，才会执行筛选过程。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-197">Note that the filtering process happens only at indexing time or if a user inserts or updates a column in the base table while automatic change tracking is enabled for the full-text index.</span></span> <span data-ttu-id="7e5a2-198">有关详细信息，请参阅 [配置和管理搜索筛选器](configure-and-manage-filters-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-198">For more information, see [Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md).</span></span>  
  
  
##  <a name="common-tasks"></a><a name="tasks"></a><span data-ttu-id="7e5a2-199">常见任务</span><span class="sxs-lookup"><span data-stu-id="7e5a2-199">Common Tasks</span></span>  
  
### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="7e5a2-200">创建全文目录</span><span class="sxs-lookup"><span data-stu-id="7e5a2-200">To Create a Full-Text Catalog</span></span>  
  
-   [<span data-ttu-id="7e5a2-201">CREATE FULLTEXT CATALOG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-201">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
-   [<span data-ttu-id="7e5a2-202">创建和管理全文索引目录</span><span class="sxs-lookup"><span data-stu-id="7e5a2-202">Create and Manage Full-Text Catalogs</span></span>](create-and-manage-full-text-catalogs.md)  
  
### <a name="to-view-the-indexes-of-a-table-or-view"></a><span data-ttu-id="7e5a2-203">查看表（或视图）的索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-203">To View the Indexes of a Table (or View)</span></span>  
  
-   [<span data-ttu-id="7e5a2-204">sys.indexes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-204">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
### <a name="to-create-a-unique-index"></a><span data-ttu-id="7e5a2-205">创建唯一索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-205">To Create a Unique Index</span></span>  
  
-   [<span data-ttu-id="7e5a2-206">CREATE INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-206">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="7e5a2-207">打开表设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-207">Open Table Designer &#40;Visual Database Tools&#41;</span></span>](../../ssms/visual-db-tools/visual-database-tools.md)  
  
### <a name="to-create-a-full-text-index"></a><span data-ttu-id="7e5a2-208">创建全文索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-208">To Create a Full-Text Index</span></span>  
  
-   [<span data-ttu-id="7e5a2-209">CREATE FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-209">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
-   [<span data-ttu-id="7e5a2-210">创建和管理全文索引</span><span class="sxs-lookup"><span data-stu-id="7e5a2-210">Create and Manage Full-Text Indexes</span></span>](create-and-manage-full-text-indexes.md)  
  
### <a name="to-view-information-about-a-full-text-index"></a><span data-ttu-id="7e5a2-211">查看有关全文索引的信息</span><span class="sxs-lookup"><span data-stu-id="7e5a2-211">To View Information about a Full-Text Index</span></span>  
  
|<span data-ttu-id="7e5a2-212">目录视图或动态管理视图</span><span class="sxs-lookup"><span data-stu-id="7e5a2-212">Catalog or Dynamic Management View</span></span>|<span data-ttu-id="7e5a2-213">说明</span><span class="sxs-lookup"><span data-stu-id="7e5a2-213">Description</span></span>|  
|----------------------------------------|-----------------|  
|[<span data-ttu-id="7e5a2-214">sys.fulltext_index_catalog_usages (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-214">sys.fulltext_index_catalog_usages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql)|<span data-ttu-id="7e5a2-215">对于全文索引引用的每个全文目录，返回与其对应的一行。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-215">Returns a row for each full-text catalog to full-text index reference.</span></span>|  
|[<span data-ttu-id="7e5a2-216">sys.fulltext_index_columns (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-216">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|<span data-ttu-id="7e5a2-217">对构成全文索引的每列都包含一行。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-217">Contains a row for each column that is part of a full-text index.</span></span>|  
|[<span data-ttu-id="7e5a2-218">sys.fulltext_index_fragments (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-218">sys.fulltext_index_fragments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql)|<span data-ttu-id="7e5a2-219">全文索引使用内部表（称为“全文索引片断”）来存储倒排索引数据。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-219">A fulltext index uses internal tables called full-text index fragments to store the inverted index data.</span></span> <span data-ttu-id="7e5a2-220">可以使用此视图来查询有关这些片断的元数据。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-220">This view can be used to query the metadata about these fragments.</span></span> <span data-ttu-id="7e5a2-221">在此视图中，每个全文索引片断在每个包含全文索引的表中各占一行。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-221">This view contains a row for each full-text index fragment in every table that contains a full-text index.</span></span>|  
|[<span data-ttu-id="7e5a2-222">sys.fulltext_indexes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-222">sys.fulltext_indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)|<span data-ttu-id="7e5a2-223">表对象的每个全文索引各占一行。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-223">Contains a row per full-text index of a tabular object.</span></span>|  
|[<span data-ttu-id="7e5a2-224">sys.dm_fts_index_keywords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-224">sys.dm_fts_index_keywords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql)|<span data-ttu-id="7e5a2-225">返回有关指定表的全文索引内容的信息。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-225">Returns information about the content of a full-text index for the specified table.</span></span>|  
|[<span data-ttu-id="7e5a2-226">sys.dm_fts_index_keywords_by_document (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-226">sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql)|<span data-ttu-id="7e5a2-227">返回有关指定表的文档级全文索引内容的信息。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-227">Returns information about the document-level content of a full-text index for the specified table.</span></span> <span data-ttu-id="7e5a2-228">给定关键字可以出现在几个文档中。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-228">A given keyword can appear in several documents.</span></span>|  
|[<span data-ttu-id="7e5a2-229">sys.dm_fts_index_population (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-229">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|<span data-ttu-id="7e5a2-230">返回有关当前正在进行的全文索引填充的信息。</span><span class="sxs-lookup"><span data-stu-id="7e5a2-230">Returns information about the full-text index populations currently in progress.</span></span>|  
  
  
## <a name="see-also"></a><span data-ttu-id="7e5a2-231">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e5a2-231">See Also</span></span>  
 <span data-ttu-id="7e5a2-232">[CREATE FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-232">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="7e5a2-233">[CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-233">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 <span data-ttu-id="7e5a2-234">[创建全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-234">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="7e5a2-235">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-235">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="7e5a2-236">[填充全文索引](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-236">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="7e5a2-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-sql&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7e5a2-237">[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) </span></span>  
 [<span data-ttu-id="7e5a2-238">OBJECTPROPERTYEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7e5a2-238">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)  
  
  
