---
title: 全文目录属性 (表和视图 "页) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
author: rothja
ms.author: jroth
ms.openlocfilehash: eb4d968af6c550d19fbb8934b5d76a1bd63cb8da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693043"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a><span data-ttu-id="b6191-102">全文目录属性（“表和视图”页）</span><span class="sxs-lookup"><span data-stu-id="b6191-102">Full-Text Catalog Properties (Tables and Views Page)</span></span>
  <span data-ttu-id="b6191-103">使用此对话框可以查看或修改为全文目录分配的表和视图。</span><span class="sxs-lookup"><span data-stu-id="b6191-103">Use this dialog page to view or modify the tables and views that are assigned to the full-text catalog.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b6191-104">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="b6191-104">UI element list</span></span>  
 <span data-ttu-id="b6191-105">**此数据库中所有合格的表/视图对象**</span><span class="sxs-lookup"><span data-stu-id="b6191-105">**All eligible table/view objects in this database**</span></span>  
 <span data-ttu-id="b6191-106">列出对其定义了唯一索引、但并未包含在全文目录中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="b6191-106">Lists the tables and views that have a unique index defined on them, but are not already a part of the full-text catalog.</span></span> <span data-ttu-id="b6191-107">若要选择某个表或视图并将其分配给目录，请在列表框中选择相应的项，然后按 "->" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b6191-107">To select a table or view and assign it to the catalog, select the items in the list box and press the "->" button.</span></span>  
  
 <span data-ttu-id="b6191-108">**分配给该目录的表/视图对象**</span><span class="sxs-lookup"><span data-stu-id="b6191-108">**Table/view objects assigned to the catalog**</span></span>  
 <span data-ttu-id="b6191-109">列出当前分配给全文目录的表和视图。</span><span class="sxs-lookup"><span data-stu-id="b6191-109">Lists the tables and views that are currently assigned to the full-text catalog</span></span>  
  
## <a name="selected-object-properties"></a><span data-ttu-id="b6191-110">所选对象属性</span><span class="sxs-lookup"><span data-stu-id="b6191-110">Selected Object Properties</span></span>  
 <span data-ttu-id="b6191-111">**所选对象属性**</span><span class="sxs-lookup"><span data-stu-id="b6191-111">**Selected object properties**</span></span>  
 <span data-ttu-id="b6191-112">显示在分配给该目录的对象的列表框中所选对象的属性。</span><span class="sxs-lookup"><span data-stu-id="b6191-112">Displays the properties of the selected object in the list box of objects assigned to the catalog.</span></span>  
  
 <span data-ttu-id="b6191-113">**唯一索引**</span><span class="sxs-lookup"><span data-stu-id="b6191-113">**Unique Index**</span></span>  
 <span data-ttu-id="b6191-114">列出表或视图可用的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="b6191-114">Lists the available unique indexes of the table or view.</span></span>  
  
 <span data-ttu-id="b6191-115">**表支持全文索引**</span><span class="sxs-lookup"><span data-stu-id="b6191-115">**Table is full-text enabled**</span></span>  
 <span data-ttu-id="b6191-116">若要对该表启用全文索引，请选中此复选框。</span><span class="sxs-lookup"><span data-stu-id="b6191-116">Select this check box to enable the full-text index on the table.</span></span> <span data-ttu-id="b6191-117">若要禁用全文索引，请清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="b6191-117">Clear the check box to disable the full-text index.</span></span>  
  
## <a name="eligible-columns-grid"></a><span data-ttu-id="b6191-118">“合格列”网格</span><span class="sxs-lookup"><span data-stu-id="b6191-118">Eligible Columns Grid</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6191-119">**可用列**</span><span class="sxs-lookup"><span data-stu-id="b6191-119">**Available Columns**</span></span>|<span data-ttu-id="b6191-120">显示进行全文索引的所有列。</span><span class="sxs-lookup"><span data-stu-id="b6191-120">Displays all the columns that are full-text indexed.</span></span> <span data-ttu-id="b6191-121">若要向全文索引中添加列，请选中相应的复选框。</span><span class="sxs-lookup"><span data-stu-id="b6191-121">Select a check box to add a column to the full-text index.</span></span>|  
|<span data-ttu-id="b6191-122">**断字符语言**</span><span class="sxs-lookup"><span data-stu-id="b6191-122">**Language for Word Breaker**</span></span>|<span data-ttu-id="b6191-123">显示断字符的语言。</span><span class="sxs-lookup"><span data-stu-id="b6191-123">Displays the language of the word breaker.</span></span>|  
|<span data-ttu-id="b6191-124">**数据类型列**</span><span class="sxs-lookup"><span data-stu-id="b6191-124">**Data Type Column**</span></span>|<span data-ttu-id="b6191-125">列出表中列的名称，该列包含在 "**可用列**" 中列出的列的文档类型（如果该列是 `varbinary(max)` 或 `image` 列）。</span><span class="sxs-lookup"><span data-stu-id="b6191-125">Lists the name of the column in the table that holds the document type of the column listed in **Available Columns** if the column is a `varbinary(max)` or `image` column.</span></span>|  
|<span data-ttu-id="b6191-126">**统计语义**</span><span class="sxs-lookup"><span data-stu-id="b6191-126">**Statistical Semantics**</span></span>|<span data-ttu-id="b6191-127">选择是否为所选列启用语义索引。</span><span class="sxs-lookup"><span data-stu-id="b6191-127">Select whether to enable semantic indexing for the selected column.</span></span> <span data-ttu-id="b6191-128">有关详细信息，请参阅[语义搜索 (SQL Server)](../relational-databases/search/semantic-search-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b6191-128">For more information, see [Semantic Search &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).</span></span><br /><br /> <span data-ttu-id="b6191-129">如果您在选择 **“统计语义”** 前选择某一 **“语言”**，并且所选语言没有关联的语义语言模型，则 **“统计语义”** 复选框将被禁用。</span><span class="sxs-lookup"><span data-stu-id="b6191-129">If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled.</span></span> <span data-ttu-id="b6191-130">如果你在选择\*\*\*\*“语言”前选择\*\*\*\*“统计语义”，则下拉组合框中提供的语言将限制为存在语义语言模型支持的那些语言。</span><span class="sxs-lookup"><span data-stu-id="b6191-130">If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop-down combo box will be restricted to those for which there is Semantic Language Model support.</span></span>|  
  
## <a name="track-changes"></a><span data-ttu-id="b6191-131">跟踪更改</span><span class="sxs-lookup"><span data-stu-id="b6191-131">Track Changes</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6191-132">**自动**</span><span class="sxs-lookup"><span data-stu-id="b6191-132">**Automatic**</span></span>|<span data-ttu-id="b6191-133">在修改、添加或删除基础表中的数据时，将自动更新全文索引。</span><span class="sxs-lookup"><span data-stu-id="b6191-133">The full-text index is automatically updated when the data in the underlying table is modified, added, or deleted.</span></span>|  
|<span data-ttu-id="b6191-134">手动</span><span class="sxs-lookup"><span data-stu-id="b6191-134">**Manual**</span></span>|<span data-ttu-id="b6191-135">在修改、添加或删除索引数据中的数据时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将跟踪所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b6191-135">When data is modified, added, or deleted in the indexed data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tracks the changes.</span></span> <span data-ttu-id="b6191-136">当 **“手动”** 更改跟踪处于有效状态时，不会使用这些更改自动更新索引。</span><span class="sxs-lookup"><span data-stu-id="b6191-136">When **Manual** change tracking is in effect, the index is not automatically updated with these changes.</span></span> <span data-ttu-id="b6191-137">相反，管理员可以使用 [ALTER FULLTEXT INDEX ...START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 语句手动应用更改。</span><span class="sxs-lookup"><span data-stu-id="b6191-137">Instead, an administrator can apply the changes manually by using an [ALTER FULLTEXT INDEX ... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) statement.</span></span>|  
|<span data-ttu-id="b6191-138">**不跟踪更改**</span><span class="sxs-lookup"><span data-stu-id="b6191-138">**Do not track change**</span></span>|<span data-ttu-id="b6191-139">如果此选项处于有效状态，则不会记录对目录中索引数据所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b6191-139">With this option in effect, changes to the indexed data in the catalog are not recorded.</span></span> <span data-ttu-id="b6191-140">管理员必须将 ALTER FULLTEXT INDEX 与 FULL POPULATION 或 INCREMENTAL POPULATION 一起使用以生成索引。</span><span class="sxs-lookup"><span data-stu-id="b6191-140">An administrator must build the index by using ALTER FULLTEXT INDEX with either FULL POPULATION or INCREMENTAL POPULATION.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6191-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6191-141">See Also</span></span>  
 <span data-ttu-id="b6191-142">[CREATE FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6191-142">[CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql) </span></span>  
 <span data-ttu-id="b6191-143">[&#40;Transact-sql&#41;更改全文目录](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b6191-143">[ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql) </span></span>  
 [<span data-ttu-id="b6191-144">填充全文索引</span><span class="sxs-lookup"><span data-stu-id="b6191-144">Populate Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
  
