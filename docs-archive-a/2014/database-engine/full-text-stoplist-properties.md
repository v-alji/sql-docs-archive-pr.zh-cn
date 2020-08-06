---
title: 全文非索引字表属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff27a1258d5164e3e93d34b6ff757993d6f6363
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591531"
---
# <a name="full-text-stoplist-properties"></a><span data-ttu-id="3f06e-102">全文非索引字表属性</span><span class="sxs-lookup"><span data-stu-id="3f06e-102">Full-Text Stoplist Properties</span></span>
  <span data-ttu-id="3f06e-103">使用该对话框可以添加或删除单个非索引字、删除特定语言的所有非索引字或者清除当前的非索引字表。</span><span class="sxs-lookup"><span data-stu-id="3f06e-103">Use this dialog box to add or delete individual stopwords, delete all stopwords for a specific language, or clear the current stoplist.</span></span> <span data-ttu-id="3f06e-104">非索引字是指包括在非索引字表中的常用字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-104">A stopword is a commonly used word that is included in a stoplist.</span></span> <span data-ttu-id="3f06e-105">非索引字表中的非索引字将从使用非索引字表的表的全文索引中省略。</span><span class="sxs-lookup"><span data-stu-id="3f06e-105">The stopwords in a stoplist are omitted from full-text indexing for tables that use the stoplist.</span></span> <span data-ttu-id="3f06e-106">有关详细信息，请参阅 [为全文搜索配置和管理非索引字和非索引字表](../relational-databases/search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="3f06e-106">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="3f06e-107">**使用 SQL Server Management Studio 更改非索引字表属性**</span><span class="sxs-lookup"><span data-stu-id="3f06e-107">**To use SQL Server Management Studio to change stoplist properties**</span></span>  
  
-   [<span data-ttu-id="3f06e-108">为全文搜索配置和管理非索引字和非索引字表</span><span class="sxs-lookup"><span data-stu-id="3f06e-108">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a><span data-ttu-id="3f06e-109">选项</span><span class="sxs-lookup"><span data-stu-id="3f06e-109">Options</span></span>  
 <span data-ttu-id="3f06e-110">**Action**</span><span class="sxs-lookup"><span data-stu-id="3f06e-110">**Action**</span></span>  
 <span data-ttu-id="3f06e-111">指定要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3f06e-111">Specifies the action that you want to perform.</span></span>  
  
 <span data-ttu-id="3f06e-112">**添加非索引字**</span><span class="sxs-lookup"><span data-stu-id="3f06e-112">**Add stopword**</span></span>  
 <span data-ttu-id="3f06e-113">向非索引字表中添加常用字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-113">Add a commonly used word to the stoplist.</span></span>  
  
 <span data-ttu-id="3f06e-114">**删除非索引字**</span><span class="sxs-lookup"><span data-stu-id="3f06e-114">**Delete stopword**</span></span>  
 <span data-ttu-id="3f06e-115">从非索引字表中删除非索引字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-115">Delete a stopword from the stoplist.</span></span>  
  
 <span data-ttu-id="3f06e-116">**删除所有非索引字**</span><span class="sxs-lookup"><span data-stu-id="3f06e-116">**Delete all stopwords**</span></span>  
 <span data-ttu-id="3f06e-117">删除特定语言的所有非索引字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-117">Delete all the stopwords for a specific language.</span></span>  
  
 <span data-ttu-id="3f06e-118">**清除非索引字表**</span><span class="sxs-lookup"><span data-stu-id="3f06e-118">**Clear stoplist**</span></span>  
 <span data-ttu-id="3f06e-119">通过删除所有语言的全部非索引字来清除非索引字表。</span><span class="sxs-lookup"><span data-stu-id="3f06e-119">Clear the stoplist by deleting all the stopwords for all languages.</span></span>  
  
 <span data-ttu-id="3f06e-120">**非索引字**</span><span class="sxs-lookup"><span data-stu-id="3f06e-120">**Stopword**</span></span>  
 <span data-ttu-id="3f06e-121">如果您选择的是 **“添加非索引字”** 或 **“删除非索引字”**，请在 **“非索引字”** 字段中输入所需的非索引字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-121">If you selected **Add stopword** or **Delete stopword**, enter the stopword in the **Stopword** field.</span></span> <span data-ttu-id="3f06e-122">新的非索引字必须是唯一的，也就是说，在针对所选语言的此非索引字表中还不存在该非索引字。</span><span class="sxs-lookup"><span data-stu-id="3f06e-122">A new stopword must be unique; that is, not yet in this stoplist for the language that you select.</span></span>  
  
 <span data-ttu-id="3f06e-123">**全文语言**</span><span class="sxs-lookup"><span data-stu-id="3f06e-123">**Full-text language**</span></span>  
 <span data-ttu-id="3f06e-124">如果您选择的是 **“添加非索引字”**、 **“删除非索引字”** 或 **“删除所有非索引字”**，请从列表框中选择非索引字的语言。</span><span class="sxs-lookup"><span data-stu-id="3f06e-124">If you selected **Add stopword**, **Delete stopword**, or **Delete all stopwords**, select the language of the stopword or stopwords from the list box.</span></span> <span data-ttu-id="3f06e-125">这将列出该服务器实例支持的所有全文语言。</span><span class="sxs-lookup"><span data-stu-id="3f06e-125">This lists all the full-text languages that are supported by the server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f06e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f06e-126">See Also</span></span>  
 <span data-ttu-id="3f06e-127">[sys. fulltext_stopwords &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f06e-127">[sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql) </span></span>  
 <span data-ttu-id="3f06e-128">[sys. fulltext_stoplists &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f06e-128">[sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql) </span></span>  
 <span data-ttu-id="3f06e-129">[为全文搜索配置和管理非索引字和非索引字](../relational-databases/search/full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="3f06e-129">[Configure and Manage Stopwords and Stoplists for Full-Text Search](../relational-databases/search/full-text-search.md) </span></span>  
 <span data-ttu-id="3f06e-130">[更改全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f06e-130">[ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql) </span></span>  
 <span data-ttu-id="3f06e-131">[创建全文非索引字表 &#40;Transact-sql&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f06e-131">[CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql) </span></span>  
 [<span data-ttu-id="3f06e-132">DROP FULLTEXT STOPLIST (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3f06e-132">DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
