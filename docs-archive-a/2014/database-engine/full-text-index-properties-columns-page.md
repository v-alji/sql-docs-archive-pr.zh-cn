---
title: 全文本索引属性 (列页面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: rothja
ms.author: jroth
ms.openlocfilehash: f947af04463948ef551c6df866d5a306c248c6b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591542"
---
# <a name="full-text-index-properties-columns-page"></a><span data-ttu-id="b2d4e-102">全文索引属性（“列”页）</span><span class="sxs-lookup"><span data-stu-id="b2d4e-102">Full-Text Index Properties (Columns Page)</span></span>
  <span data-ttu-id="b2d4e-103">**查看或更改全文索引的属性**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-103">**To view or change the properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="b2d4e-104">管理全文索引</span><span class="sxs-lookup"><span data-stu-id="b2d4e-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="b2d4e-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="b2d4e-105">UI element list</span></span>  
 <span data-ttu-id="b2d4e-106">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-106">**Unique index**</span></span>  
 <span data-ttu-id="b2d4e-107">从下拉列表中选择索引。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-107">Select an index from the drop down list.</span></span> <span data-ttu-id="b2d4e-108">索引必须是唯一且不为 Null 的单键列索引。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-108">The index must be a single-key-column, unique, non-nullable index.</span></span>  
  
 <span data-ttu-id="b2d4e-109">**选择将进行全文索引的合格列**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-109">**Select the eligible columns that will be full-text indexed**</span></span>  
 <span data-ttu-id="b2d4e-110">此网格显示可用于此全文索引的表列。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-110">The grid displays the table columns that are available for this full-text index.</span></span> <span data-ttu-id="b2d4e-111">已选中当前是全文索引的列。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-111">Columns that are currently full-text indexed are checked.</span></span> <span data-ttu-id="b2d4e-112">或者，可以选中要成为全文索引的其他列。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-112">Optionally, you can check additional columns that you want to be full-text indexed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b2d4e-113">在单击“确定”之前，请确保至少选中一列。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-113">Ensure that at least one column is checked before you click OK.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2d4e-114">**可用列**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-114">**Available Columns**</span></span>|<span data-ttu-id="b2d4e-115">列名称。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-115">The column name.</span></span>|  
|<span data-ttu-id="b2d4e-116">**断字符语言**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-116">**Language for Word Breaker**</span></span>|<span data-ttu-id="b2d4e-117">其断字符和词干分析器对所有全文索引数据执行语言分析的语言。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-117">The language whose word breakers and stemmers perform linguistic analysis on all full-text indexed data.</span></span><br /><br /> <span data-ttu-id="b2d4e-118">有关详细信息，请参阅为[搜索配置和管理断字符和词干分析器](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)和在[创建全文索引时选择语言](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-118">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) and [Choose a Language When Creating a Full-Text Index](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).</span></span>|  
|<span data-ttu-id="b2d4e-119">**Type**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-119">**Type**</span></span>|<span data-ttu-id="b2d4e-120">保留所选列的文档类型的表列的名称。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-120">The name of the table column that holds the document type of the selected column.</span></span> <span data-ttu-id="b2d4e-121">这是只读属性。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-121">This is a read-only property.</span></span>|  
|<span data-ttu-id="b2d4e-122">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="b2d4e-122">**Statistical Semantics**</span></span>|<span data-ttu-id="b2d4e-123">选择是否为所选列启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-123">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="b2d4e-124">有关详细信息，请参阅[语义搜索 (SQL Server)](../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-124">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="b2d4e-125">如果您在选择 **“统计语义”** 前选择某一 **“语言”**，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将被禁用。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-125">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="b2d4e-126">如果你在选择\*\*\*\*“语言”前选择\*\*\*\*“统计语义”，则下拉组合框中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="b2d4e-126">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2d4e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2d4e-127">See Also</span></span>  
 [<span data-ttu-id="b2d4e-128">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="b2d4e-128">Populate Full-Text Indexes</span></span>](../relational-databases/search/populate-full-text-indexes.md)  
  
  
