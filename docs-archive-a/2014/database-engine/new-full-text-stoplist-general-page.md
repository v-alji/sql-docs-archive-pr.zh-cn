---
title: 新建全文非索引字表 (常规页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: rothja
ms.author: jroth
ms.openlocfilehash: a6272fb570b85989f38c8187e29712966862710d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590366"
---
# <a name="new-full-text-stoplist-general-page"></a><span data-ttu-id="516e9-102">新建全文非索引字表（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="516e9-102">New Full-Text Stoplist (General Page)</span></span>
  <span data-ttu-id="516e9-103">使用此对话框可以创建全文非索引字表。</span><span class="sxs-lookup"><span data-stu-id="516e9-103">Use this dialog box to create a full-text stoplist.</span></span> <span data-ttu-id="516e9-104">“非索引字表” \*\* 是一组称为“非索引字” \*\* 的常用字，在使用非索引字表的表的全文索引中会省略这些非索引字。</span><span class="sxs-lookup"><span data-stu-id="516e9-104">A *stoplist* is a set of commonly used words, called *stopwords*, that are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="516e9-105">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="516e9-105">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="516e9-106">**使用 SQL Server Management Studio 创建非索引字表**</span><span class="sxs-lookup"><span data-stu-id="516e9-106">**To use SQL Server Management Studio to create a stoplist**</span></span>  
  
-   [<span data-ttu-id="516e9-107">为全文搜索配置和管理非索引字和非索引字表</span><span class="sxs-lookup"><span data-stu-id="516e9-107">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="516e9-108">选项</span><span class="sxs-lookup"><span data-stu-id="516e9-108">Options</span></span>  
 <span data-ttu-id="516e9-109">**全文非索引字表名称**</span><span class="sxs-lookup"><span data-stu-id="516e9-109">**Full-text stoplist name**</span></span>  
 <span data-ttu-id="516e9-110">输入全文非索引字表的名称。</span><span class="sxs-lookup"><span data-stu-id="516e9-110">Enter the name of the full-text stoplist.</span></span>  
  
 <span data-ttu-id="516e9-111">**所有者**</span><span class="sxs-lookup"><span data-stu-id="516e9-111">**Owner**</span></span>  
 <span data-ttu-id="516e9-112">指定全文非索引字表的所有者。</span><span class="sxs-lookup"><span data-stu-id="516e9-112">Specify the owner of the full-text stoplist.</span></span> <span data-ttu-id="516e9-113">如果希望将所有权分配给您自己（即分配给当前用户），请将此字段留空。</span><span class="sxs-lookup"><span data-stu-id="516e9-113">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span>  
  
 <span data-ttu-id="516e9-114">若要指定另一个用户，请单击浏览按钮。</span><span class="sxs-lookup"><span data-stu-id="516e9-114">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-stoplist-options"></a><span data-ttu-id="516e9-115">创建非索引字表选项</span><span class="sxs-lookup"><span data-stu-id="516e9-115">Create stoplist options</span></span>  
 <span data-ttu-id="516e9-116">单击下列创建选项之一：</span><span class="sxs-lookup"><span data-stu-id="516e9-116">Click one of the following create options:</span></span>  
  
 <span data-ttu-id="516e9-117">**创建空非索引字表**</span><span class="sxs-lookup"><span data-stu-id="516e9-117">**Create an empty stoplist**</span></span>  
 <span data-ttu-id="516e9-118">新非索引字表将不包含任何非索引字。</span><span class="sxs-lookup"><span data-stu-id="516e9-118">The new stoplist will not contain any stopwords.</span></span>  
  
 <span data-ttu-id="516e9-119">**从系统非索引字表创建**</span><span class="sxs-lookup"><span data-stu-id="516e9-119">**Create from the system stoplist**</span></span>  
 <span data-ttu-id="516e9-120">用默认存在于 [资源数据库](../relational-databases/databases/resource-database.md)中的非索引字表创建新的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="516e9-120">The new stoplist is created from the stoplist that exists by default in the [Resource database](../relational-databases/databases/resource-database.md).</span></span>  
  
 <span data-ttu-id="516e9-121">**从现有全文非索引字表创建**</span><span class="sxs-lookup"><span data-stu-id="516e9-121">**Create from an existing full-text stoplist**</span></span>  
 <span data-ttu-id="516e9-122">通过复制现有的非索引字表来创建新的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="516e9-122">The new stoplist is created by copying an existing stoplist.</span></span>  
  
 <span data-ttu-id="516e9-123">**源数据库**</span><span class="sxs-lookup"><span data-stu-id="516e9-123">**Source database**</span></span>  
 <span data-ttu-id="516e9-124">指定现有非索引字表所属的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="516e9-124">Specifies the name of the database to which the existing stoplist belongs.</span></span> <span data-ttu-id="516e9-125">默认情况下选择当前数据库。</span><span class="sxs-lookup"><span data-stu-id="516e9-125">The current database is selected by default.</span></span> <span data-ttu-id="516e9-126">也可以从列表框中选择其他数据库。</span><span class="sxs-lookup"><span data-stu-id="516e9-126">Optionally, select a different database from the list box.</span></span>  
  
 <span data-ttu-id="516e9-127">**源非索引字表**</span><span class="sxs-lookup"><span data-stu-id="516e9-127">**Source stoplist**</span></span>  
 <span data-ttu-id="516e9-128">指定现有非索引字表的名称。</span><span class="sxs-lookup"><span data-stu-id="516e9-128">Specifies the name of an existing stoplist.</span></span> <span data-ttu-id="516e9-129">从可用非索引字表的列表中，选择一个要用作源的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="516e9-129">From the list of available stoplists, select the one to use as the source.</span></span> <span data-ttu-id="516e9-130">可用非索引字表按照它们在对象资源管理器中显示的顺序列出。</span><span class="sxs-lookup"><span data-stu-id="516e9-130">The available stoplists are listed in the order in which they appear in Object Explorer.</span></span>  
  
 <span data-ttu-id="516e9-131">如果源非索引字表的停止词中指定的任何语言未在当前数据库中注册，CREATE FULLTEXT STOPLIST 将成功，但会返回警告且不会添加相应的停止词。</span><span class="sxs-lookup"><span data-stu-id="516e9-131">If any languages specified in the stop words of the source stoplist are not registered in the current database, CREATE FULLTEXT STOPLIST succeeds, but warning(s) are returned and the corresponding stop words are not added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516e9-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="516e9-132">See Also</span></span>  
 <span data-ttu-id="516e9-133">[更改全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="516e9-133">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="516e9-134">[创建全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="516e9-134">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="516e9-135">[删除全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="516e9-135">[DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="516e9-136">[为全文搜索配置和管理非索引字和非索引字](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="516e9-136">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 [<span data-ttu-id="516e9-137">sys.fulltext_stoplists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="516e9-137">sys.fulltext_stoplists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
