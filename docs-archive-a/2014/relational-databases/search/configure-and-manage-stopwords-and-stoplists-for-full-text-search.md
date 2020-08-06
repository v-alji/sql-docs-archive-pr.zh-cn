---
title: 为全文搜索配置和管理非索引字和非索引字表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 103b5024368c5ca239856580e9b45473aabf6a92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693712"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a><span data-ttu-id="d94df-102">为全文搜索配置和管理非索引字和非索引字表</span><span class="sxs-lookup"><span data-stu-id="d94df-102">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>
  <span data-ttu-id="d94df-103">为了精简全文检索， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了一种机制，用于去掉那些经常出现但对搜索无益的字符串。</span><span class="sxs-lookup"><span data-stu-id="d94df-103">To prevent a full-text index from becoming bloated, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a mechanism that discards commonly occurring strings that do not help the search.</span></span> <span data-ttu-id="d94df-104">这些去掉的字符串称为“非索引字”  。</span><span class="sxs-lookup"><span data-stu-id="d94df-104">These discarded strings are called *stopwords*.</span></span> <span data-ttu-id="d94df-105">在索引创建期间，全文引擎将忽略全文检索中的非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-105">During index creation, the Full-Text Engine omits stopwords from the full-text index.</span></span> <span data-ttu-id="d94df-106">也就是说全文查询将不搜索非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-106">This means that full-text queries will not search on stopwords.</span></span>  
  
##  <a name="understanding-stopwords-and-stoplists"></a><a name="understand"></a><span data-ttu-id="d94df-107">了解非索引字和非索引字</span><span class="sxs-lookup"><span data-stu-id="d94df-107">Understanding Stopwords and Stoplists</span></span>  
 <span data-ttu-id="d94df-108">非索引字可以是在特定语言中具有含义的词，也可以是不具有语言含义的“标记” \*\* 。</span><span class="sxs-lookup"><span data-stu-id="d94df-108">A stopword can be a word with meaning in a specific language, or it can be a *token* that does not have linguistic meaning.</span></span> <span data-ttu-id="d94df-109">例如，在英语中，诸如“a”、“and”、“is”和“the”之类的词将被排除在全文检索之外，这是因为已经知道它们对搜索没有用处。</span><span class="sxs-lookup"><span data-stu-id="d94df-109">For example, in the English language, words such as "a," "and," "is," and "the" are left out of the full-text index since they are known to be useless to a search.</span></span>  
  
 <span data-ttu-id="d94df-110">尽管全文检索会忽略所包含的非索引字，但它确实会考虑非索引字的位置。</span><span class="sxs-lookup"><span data-stu-id="d94df-110">Although it ignores the inclusion of stopwords, the full-text index does take into account their position.</span></span> <span data-ttu-id="d94df-111">例如，请看下面这个短语：“Instructions are applicable to these Adventure Works Cycles models”。</span><span class="sxs-lookup"><span data-stu-id="d94df-111">For example, consider the phrase, "Instructions are applicable to these Adventure Works Cycles models".</span></span> <span data-ttu-id="d94df-112">下表显示了短语中各个词的位置：</span><span class="sxs-lookup"><span data-stu-id="d94df-112">The following table depicts the position of the words in the phrase:</span></span>  
  
|<span data-ttu-id="d94df-113">Word</span><span class="sxs-lookup"><span data-stu-id="d94df-113">Word</span></span>|<span data-ttu-id="d94df-114">位置</span><span class="sxs-lookup"><span data-stu-id="d94df-114">Position</span></span>|  
|----------|--------------|  
|<span data-ttu-id="d94df-115">Instructions</span><span class="sxs-lookup"><span data-stu-id="d94df-115">Instructions</span></span>|<span data-ttu-id="d94df-116">1</span><span class="sxs-lookup"><span data-stu-id="d94df-116">1</span></span>|  
|<span data-ttu-id="d94df-117">are</span><span class="sxs-lookup"><span data-stu-id="d94df-117">are</span></span>|<span data-ttu-id="d94df-118">2</span><span class="sxs-lookup"><span data-stu-id="d94df-118">2</span></span>|  
|<span data-ttu-id="d94df-119">applicable</span><span class="sxs-lookup"><span data-stu-id="d94df-119">applicable</span></span>|<span data-ttu-id="d94df-120">3</span><span class="sxs-lookup"><span data-stu-id="d94df-120">3</span></span>|  
|<span data-ttu-id="d94df-121">to</span><span class="sxs-lookup"><span data-stu-id="d94df-121">to</span></span>|<span data-ttu-id="d94df-122">4</span><span class="sxs-lookup"><span data-stu-id="d94df-122">4</span></span>|  
|<span data-ttu-id="d94df-123">these</span><span class="sxs-lookup"><span data-stu-id="d94df-123">these</span></span>|<span data-ttu-id="d94df-124">5</span><span class="sxs-lookup"><span data-stu-id="d94df-124">5</span></span>|  
|<span data-ttu-id="d94df-125">Adventure</span><span class="sxs-lookup"><span data-stu-id="d94df-125">Adventure</span></span>|<span data-ttu-id="d94df-126">6</span><span class="sxs-lookup"><span data-stu-id="d94df-126">6</span></span>|  
|<span data-ttu-id="d94df-127">Works</span><span class="sxs-lookup"><span data-stu-id="d94df-127">Works</span></span>|<span data-ttu-id="d94df-128">7</span><span class="sxs-lookup"><span data-stu-id="d94df-128">7</span></span>|  
|<span data-ttu-id="d94df-129">周期</span><span class="sxs-lookup"><span data-stu-id="d94df-129">Cycles</span></span>|<span data-ttu-id="d94df-130">8</span><span class="sxs-lookup"><span data-stu-id="d94df-130">8</span></span>|  
|<span data-ttu-id="d94df-131">模型</span><span class="sxs-lookup"><span data-stu-id="d94df-131">models</span></span>|<span data-ttu-id="d94df-132">9</span><span class="sxs-lookup"><span data-stu-id="d94df-132">9</span></span>|  
  
 <span data-ttu-id="d94df-133">分别在第 2、第 4 和第 5 个位置的非索引字“are”、“to”和“these”将被排除在全文检索之外。</span><span class="sxs-lookup"><span data-stu-id="d94df-133">The stopwords "are", "to", and "these" that are in positions 2, 4, and 5 are left out of the full-text index.</span></span> <span data-ttu-id="d94df-134">但是会保留它们的位置信息，从而使短语中其他词的位置不受影响。</span><span class="sxs-lookup"><span data-stu-id="d94df-134">However, their positional information is maintained, thereby leaving the position of the other words in the phrase unaffected.</span></span>  
  
 <span data-ttu-id="d94df-135">使用称为“非索引字表”的对象在数据库中管理非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-135">Stopwords are managed in databases using objects called stoplists.</span></span> <span data-ttu-id="d94df-136">“非索引字表”\*\* 是一个由非索引字组成的列表，这些非索引字在与全文检索关联时会应用于该索引的全文查询。</span><span class="sxs-lookup"><span data-stu-id="d94df-136">A *stoplist* is a list of stopwords that, when associated with a full-text index, is applied to full-text queries on that index.</span></span>  
  
  
##  <a name="creating-a-stoplist"></a><a name="creating"></a><span data-ttu-id="d94df-137">创建非索引字表</span><span class="sxs-lookup"><span data-stu-id="d94df-137">Creating a Stoplist</span></span>  
 <span data-ttu-id="d94df-138">可使用下列任一方法创建非索引字表：</span><span class="sxs-lookup"><span data-stu-id="d94df-138">You can create a stoplist in any of the following ways:</span></span>  
  
-   <span data-ttu-id="d94df-139">在数据库中使用系统提供的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="d94df-139">Using the system-supplied stoplist in the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d94df-140">为每种支持的语言（即默认情况下与给定断字符关联的每种语言）都附带了一个包含最常用非索引字的系统非索引字表。</span><span class="sxs-lookup"><span data-stu-id="d94df-140">ships with a system stoplist that contains the most commonly used stopwords for each supported language, that is for every language that is associated with given word breakers by default.</span></span> <span data-ttu-id="d94df-141">系统非索引字表包含所有支持语言的常用非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-141">The system stoplist contains common stopwords for all supported languages.</span></span>  <span data-ttu-id="d94df-142">可以复制系统非索引字表并通过添加和删除非索引字来自定义自己的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="d94df-142">You can copy the system stoplist, and customize your copy by adding and removing stopwords.</span></span>  
  
     <span data-ttu-id="d94df-143">系统非索引字表安装在 [Resource](../databases/resource-database.md) 数据库中。</span><span class="sxs-lookup"><span data-stu-id="d94df-143">The system stoplist is installed in the [Resource](../databases/resource-database.md) database.</span></span>  
  
-   <span data-ttu-id="d94df-144">创建自己的非索引字表，然后针对您所指定的任何语言将非索引字添加到非索引字表中。</span><span class="sxs-lookup"><span data-stu-id="d94df-144">Creating your own stoplist, and then adding stopwords to it for any language that you specify.</span></span> <span data-ttu-id="d94df-145">必要时，您还可以从您的非索引字表中删除非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-145">You can also drop stopwords from your stoplist when necessary.</span></span>  
  
-   <span data-ttu-id="d94df-146">在当前服务器实例中使用任何其他数据库中的现有自定义非索引字表，然后根据需要添加和删除非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-146">Using an existing custom stoplist from any other database in the current server instance and then adding and dropping stopwords as necessary.</span></span>  
  
 <span data-ttu-id="d94df-147">**创建非索引字表**</span><span class="sxs-lookup"><span data-stu-id="d94df-147">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="d94df-148">CREATE FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-148">CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a><span data-ttu-id="d94df-149">在 Management Studio 中创建全文非索引字表</span><span class="sxs-lookup"><span data-stu-id="d94df-149">To create a full-text stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="d94df-150">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="d94df-150">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="d94df-151">展开“数据库”\*\*\*\*，然后展开要在其中创建全文非索引字表的数据库。</span><span class="sxs-lookup"><span data-stu-id="d94df-151">Expand **Databases**, and then expand the database in which you want to create the full-text stoplist.</span></span>  
  
3.  <span data-ttu-id="d94df-152">展开“存储”\*\*\*\*，然后右键单击“全文非索引字表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d94df-152">Expand **Storage**, and then right-click **Full-Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="d94df-153">选择“新建全文非索引字表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d94df-153">Select **New Full-Text Stoplist**.</span></span>  
  
5.  <span data-ttu-id="d94df-154">指定非索引字表名称。</span><span class="sxs-lookup"><span data-stu-id="d94df-154">Specify the stoplist name.</span></span>  
  
6.  <span data-ttu-id="d94df-155">（可选）将另外某人指定为非索引字表所有者。</span><span class="sxs-lookup"><span data-stu-id="d94df-155">Optionally, specify someone else as the stoplist owner.</span></span>  
  
7.  <span data-ttu-id="d94df-156">从下列创建非索引字表的选项中选择一个：</span><span class="sxs-lookup"><span data-stu-id="d94df-156">Select one of the following create stoplist options:</span></span>  
  
    -   <span data-ttu-id="d94df-157">**创建空非索引字表**</span><span class="sxs-lookup"><span data-stu-id="d94df-157">**Create an empty stoplist**</span></span>  
  
    -   <span data-ttu-id="d94df-158">**从系统非索引字表创建**</span><span class="sxs-lookup"><span data-stu-id="d94df-158">**Create from the system stoplist**</span></span>  
  
    -   <span data-ttu-id="d94df-159">**从现有全文非索引字表创建**</span><span class="sxs-lookup"><span data-stu-id="d94df-159">**Create from an existing full-text stoplist**</span></span>  
  
     <span data-ttu-id="d94df-160">有关详细信息，请参阅[新建全文非索引字表（常规页）](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="d94df-160">For more information, see [New Full-Text Stoplist &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d94df-161">**删除非索引字表**</span><span class="sxs-lookup"><span data-stu-id="d94df-161">**To drop a stoplist**</span></span>  
  
-   [<span data-ttu-id="d94df-162">DROP FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-162">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="using-a-stoplist-in-full-text-queries"></a><a name="queries"></a><span data-ttu-id="d94df-163">在全文查询中使用非索引字表</span><span class="sxs-lookup"><span data-stu-id="d94df-163">Using a Stoplist in Full-Text Queries</span></span>  
 <span data-ttu-id="d94df-164">若要在查询中使用非索引字表，必须将该非索引字表与全文检索关联。</span><span class="sxs-lookup"><span data-stu-id="d94df-164">To make use of a stoplist in queries, you must associate it with a full-text index.</span></span> <span data-ttu-id="d94df-165">可以在创建全文检索时将非索引字表附加到全文检索中，也可以在以后更改索引来添加非索引字表。</span><span class="sxs-lookup"><span data-stu-id="d94df-165">You can attach a stoplist to a full-text index when you create the index, or you can alter the index later to add a stoplist.</span></span>  
  
 <span data-ttu-id="d94df-166">**创建全文检索并将非索引字表与其关联起来**</span><span class="sxs-lookup"><span data-stu-id="d94df-166">**To create a full-text index and associate a stoplist with it**</span></span>  
  
-   [<span data-ttu-id="d94df-167">CREATE FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-167">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 <span data-ttu-id="d94df-168">**将非索引字表与现有的全文检索关联起来或取消它们之间的关联**</span><span class="sxs-lookup"><span data-stu-id="d94df-168">**To associate or disassociate a stoplist with an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="d94df-169">ALTER FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-169">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 <span data-ttu-id="d94df-170">**取消非索引字导致全文查询的布尔操作失败时产生的错误消息。**</span><span class="sxs-lookup"><span data-stu-id="d94df-170">**To suppress an error message if stopwords cause a Boolean operation on a full-text query to fail**</span></span>  
  
-   [<span data-ttu-id="d94df-171">transform noise words 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="d94df-171">transform noise words Server Configuration Option</span></span>](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing-stoplists-and-stoplist-metadata"></a><a name="viewing"></a><span data-ttu-id="d94df-172">查看非索引字和非索引字表元数据</span><span class="sxs-lookup"><span data-stu-id="d94df-172">Viewing Stoplists and Stoplist Metadata</span></span>  
 <span data-ttu-id="d94df-173">**查看非索引字表的所有非索引字**</span><span class="sxs-lookup"><span data-stu-id="d94df-173">**To view all the stopwords of a stoplist**</span></span>  
  
-   [<span data-ttu-id="d94df-174">sys.fulltext_stopwords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-174">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="d94df-175">**获取有关当前数据库中所有非索引字表的信息**</span><span class="sxs-lookup"><span data-stu-id="d94df-175">**To get information about all the stoplists in the current database**</span></span>  
  
-   [<span data-ttu-id="d94df-176">sys.fulltext_stoplists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-176">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [<span data-ttu-id="d94df-177">sys.fulltext_stopwords (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-177">sys.fulltext_stopwords &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 <span data-ttu-id="d94df-178">**查看断字符的词汇切分结果、同义词库和非索引字表组合**</span><span class="sxs-lookup"><span data-stu-id="d94df-178">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="d94df-179">sys. dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="d94df-179">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="changing-the-stopwords-in-a-stoplist"></a><a name="change"></a><span data-ttu-id="d94df-180">更改非索引字表中的非索引字</span><span class="sxs-lookup"><span data-stu-id="d94df-180">Changing the Stopwords in a Stoplist</span></span>  
 <span data-ttu-id="d94df-181">**向非索引字表中添加非索引字或从中删除非索引字**</span><span class="sxs-lookup"><span data-stu-id="d94df-181">**To add or drop stopwords from a stoplist**</span></span>  
  
-   [<span data-ttu-id="d94df-182">ALTER FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d94df-182">ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a><span data-ttu-id="d94df-183">使用 Management Studio 更改非索引字表中的非索引字</span><span class="sxs-lookup"><span data-stu-id="d94df-183">To change the stopwords in a stoplist in Management Studio</span></span>  
  
1.  <span data-ttu-id="d94df-184">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="d94df-184">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="d94df-185">展开 **“数据库”**，然后展开数据库。</span><span class="sxs-lookup"><span data-stu-id="d94df-185">Expand **Databases**, and then expand the database.</span></span>  
  
3.  <span data-ttu-id="d94df-186">展开 **“存储”**，然后选择 **“全文非索引字表”**。</span><span class="sxs-lookup"><span data-stu-id="d94df-186">Expand **Storage**, and then select **Full Text Stoplists**.</span></span>  
  
4.  <span data-ttu-id="d94df-187">右键单击要更改其属性的非索引字表，然后选择“属性”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d94df-187">Right-click the stoplist whose properties you want to change, and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="d94df-188">在“ [全文非索引字表属性](../../database-engine/full-text-stoplist-properties.md) ”对话框中：</span><span class="sxs-lookup"><span data-stu-id="d94df-188">In the [Full-Text Stoplist Properties](../../database-engine/full-text-stoplist-properties.md) dialog box:</span></span>  
  
    1.  <span data-ttu-id="d94df-189">在 **“操作”** 列表框中，选择下列操作之一： **“添加非索引字”**、 **“删除非索引字”**、 **“删除所有非索引字”** 或 **“清除非索引字表”**。</span><span class="sxs-lookup"><span data-stu-id="d94df-189">In the **Action** list box, select one of the following actions: **Add stopword**, **Delete stopword**, **Delete all stopwords**, or **Clear stoplist**.</span></span>  
  
    2.  <span data-ttu-id="d94df-190">如果对选定的操作启用了 **“非索引字”** 文本框，请输入一个非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-190">If the **Stopword** text box is enabled for the selected action, enter a single stopword.</span></span> <span data-ttu-id="d94df-191">该非索引字必须是唯一的，也就是说，在针对所选语言的此非索引字表中还不存在该非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-191">This stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
    3.  <span data-ttu-id="d94df-192">如果对选定的操作启用了“全文语言”\*\*\*\* 列表框，请选择一种语言。</span><span class="sxs-lookup"><span data-stu-id="d94df-192">If the **Full-text language** list box is enabled for the selected action, select a language.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrading-noise-words-from-sql-server-2005"></a><a name="upgrade"></a><span data-ttu-id="d94df-193">从 SQL Server 2005 升级干扰词</span><span class="sxs-lookup"><span data-stu-id="d94df-193">Upgrading Noise Words from SQL Server 2005</span></span>  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="d94df-194">干扰词已替换为非索引字。</span><span class="sxs-lookup"><span data-stu-id="d94df-194">noise words have been replaced by stopwords.</span></span> <span data-ttu-id="d94df-195">从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]升级数据库后，将不再使用干扰词文件。</span><span class="sxs-lookup"><span data-stu-id="d94df-195">When a database is upgraded from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the noise-word files are no longer used.</span></span> <span data-ttu-id="d94df-196">然而，干扰词文件存储在 FTDATA\FTNoiseThesaurusBak 文件夹中，您可以在以后更新或生成对应的非索引字表时使用它们。</span><span class="sxs-lookup"><span data-stu-id="d94df-196">However, the noise-word files are stored in the FTDATA\ FTNoiseThesaurusBak folder, and you can use them later when updating or building the corresponding stoplists.</span></span> <span data-ttu-id="d94df-197">有关将干扰词文件升级到非索引字表的信息，请参阅 [升级全文搜索](upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="d94df-197">For information about upgrading noise-word files to stoplists, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
  
  
