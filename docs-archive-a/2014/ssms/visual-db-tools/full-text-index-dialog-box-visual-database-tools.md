---
title: “全文索引”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextindex
ms.assetid: ef45b585-2567-4abe-b421-9fd0994e0146
author: stevestein
ms.author: sstein
ms.openlocfilehash: f98d3bf43707caedd8c9d0a01349f36d5a5bfbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693590"
---
# <a name="full-text-index-dialog-box-visual-database-tools"></a><span data-ttu-id="c1790-102">“全文索引”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c1790-102">Full-Text Index Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="c1790-103">使用此对话框可以创建全文索引，用于对数据库表中基于文本的列进行全文搜索。</span><span class="sxs-lookup"><span data-stu-id="c1790-103">This dialog box allows you to create a full-text index, for full-text searches on text-based columns in your database tables.</span></span> <span data-ttu-id="c1790-104">全文索引依赖于常规索引，因此必须先创建常规索引。</span><span class="sxs-lookup"><span data-stu-id="c1790-104">A full-text index relies on a regular index, so you must create that first.</span></span> <span data-ttu-id="c1790-105">常规索引只能对单个非空的列创建，而且最好选择值较小的列而不是选择值较大的列。</span><span class="sxs-lookup"><span data-stu-id="c1790-105">The regular index must be created on a single, non-null column; it is best to choose a column with small values rather than a column with large ones.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1790-106">若要创建全文索引，必须先使用外部工具（如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或企业管理器）为数据库创建一个全文本目录。</span><span class="sxs-lookup"><span data-stu-id="c1790-106">To create a full-text index, you must first create a full-text catalog for the database using an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1790-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本中都不提供全文检索功能。</span><span class="sxs-lookup"><span data-stu-id="c1790-107">Full-text index functionality is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c1790-108">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="c1790-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c1790-109">选项</span><span class="sxs-lookup"><span data-stu-id="c1790-109">Options</span></span>  
 <span data-ttu-id="c1790-110">**选定的全文索引**</span><span class="sxs-lookup"><span data-stu-id="c1790-110">**Selected Full-Text Index**</span></span>  
 <span data-ttu-id="c1790-111">列出现有的全文索引。</span><span class="sxs-lookup"><span data-stu-id="c1790-111">Lists existing full-text indexes.</span></span> <span data-ttu-id="c1790-112">选择一个索引即可在右侧的网格中显示其属性。</span><span class="sxs-lookup"><span data-stu-id="c1790-112">Select an index to show its properties in the grid to the right.</span></span> <span data-ttu-id="c1790-113">如果该列表为空，则表示尚未为该表定义任何全文本关系。</span><span class="sxs-lookup"><span data-stu-id="c1790-113">If the list is empty, no full-text relationships have been defined for the table.</span></span>  
  
 <span data-ttu-id="c1790-114">**添加**</span><span class="sxs-lookup"><span data-stu-id="c1790-114">**Add**</span></span>  
 <span data-ttu-id="c1790-115">创建新的全文索引。</span><span class="sxs-lookup"><span data-stu-id="c1790-115">Create a new full-text index.</span></span>  
  
 <span data-ttu-id="c1790-116">**删除**</span><span class="sxs-lookup"><span data-stu-id="c1790-116">**Delete**</span></span>  
 <span data-ttu-id="c1790-117">删除在“选定的全文检索”  列表中所选的全文检索。</span><span class="sxs-lookup"><span data-stu-id="c1790-117">Delete the full-text index selected in the **Selected Full-Text Index** list.</span></span>  
  
 <span data-ttu-id="c1790-118">**常规类别**</span><span class="sxs-lookup"><span data-stu-id="c1790-118">**General Category**</span></span>  
 <span data-ttu-id="c1790-119">展开此项可显示“列”  和“全文本目录名称”  。</span><span class="sxs-lookup"><span data-stu-id="c1790-119">When expanded, shows **Columns** and **Full-text Catalog Name**.</span></span>  
  
 <span data-ttu-id="c1790-120">**“列”**</span><span class="sxs-lookup"><span data-stu-id="c1790-120">**Columns**</span></span>  
 <span data-ttu-id="c1790-121">显示一个逗号分隔列表，其中列出了可进行全文搜索的列的名称。</span><span class="sxs-lookup"><span data-stu-id="c1790-121">Displays a comma-separated list of the names of full-text-searchable columns.</span></span> <span data-ttu-id="c1790-122">若要查看完整列表，请单击该属性字段左侧的省略号按钮“(…)”  。</span><span class="sxs-lookup"><span data-stu-id="c1790-122">To see the complete list, click the ellipsis button (**...**) to the left of the property field.</span></span>  
  
 <span data-ttu-id="c1790-123">**全文本目录名称**</span><span class="sxs-lookup"><span data-stu-id="c1790-123">**Full-Text Catalog Name**</span></span>  
 <span data-ttu-id="c1790-124">显示用于存储此全文索引的全文本目录的名称。</span><span class="sxs-lookup"><span data-stu-id="c1790-124">Displays the name of the full-text catalog on which this full-text index is stored.</span></span> <span data-ttu-id="c1790-125">若要将索引存储在其他目录中，请单击当前目录名称，再从下拉列表中选择其他目录。</span><span class="sxs-lookup"><span data-stu-id="c1790-125">To store the index on a different catalog, click the catalog name and choose another from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1790-126">必须先在外部工具（例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或企业管理器）中创建目录。</span><span class="sxs-lookup"><span data-stu-id="c1790-126">The catalog must be created first in an outside tool, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Enterprise Manager.</span></span>  
  
 <span data-ttu-id="c1790-127">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="c1790-127">**Identity Category**</span></span>  
 <span data-ttu-id="c1790-128">展开此项可显示此索引的名称字段。</span><span class="sxs-lookup"><span data-stu-id="c1790-128">When expanded, shows the name field for this index.</span></span>  
  
 <span data-ttu-id="c1790-129">**名称**</span><span class="sxs-lookup"><span data-stu-id="c1790-129">**Name**</span></span>  
 <span data-ttu-id="c1790-130">显示此全文索引的系统指定名称。</span><span class="sxs-lookup"><span data-stu-id="c1790-130">Displays the system-specified name for this full-text index.</span></span>  
  
 <span data-ttu-id="c1790-131">**表设计器类别**</span><span class="sxs-lookup"><span data-stu-id="c1790-131">**Table Designer Category**</span></span>  
 <span data-ttu-id="c1790-132">展开此项可显示指示索引执行方式的属性。</span><span class="sxs-lookup"><span data-stu-id="c1790-132">When expanded, shows properties that dictate how the index performs.</span></span>  
  
 <span data-ttu-id="c1790-133">**活动**</span><span class="sxs-lookup"><span data-stu-id="c1790-133">**Active**</span></span>  
 <span data-ttu-id="c1790-134">显示当前是否可以使用此全文索引执行全文搜索。</span><span class="sxs-lookup"><span data-stu-id="c1790-134">Indicates whether you can currently perform a full-text search using this full-text index.</span></span>  
  
 <span data-ttu-id="c1790-135">**更改跟踪设置**</span><span class="sxs-lookup"><span data-stu-id="c1790-135">**Change Tracking Setting**</span></span>  
 <span data-ttu-id="c1790-136">描述此索引的更改跟踪状态：“手动”、“自动”或“关闭”。</span><span class="sxs-lookup"><span data-stu-id="c1790-136">Describes the status of change tracking for this index: Manual, Auto, or Off.</span></span>  
  
 <span data-ttu-id="c1790-137">**爬网已完成**</span><span class="sxs-lookup"><span data-stu-id="c1790-137">**Crawl Completed**</span></span>  
 <span data-ttu-id="c1790-138">显示最近一次爬网是否已完成。</span><span class="sxs-lookup"><span data-stu-id="c1790-138">Shows whether the most recent crawl has been completed.</span></span> <span data-ttu-id="c1790-139">如果此属性值为“否”，则表示爬网当前正在进行。</span><span class="sxs-lookup"><span data-stu-id="c1790-139">If this property value is No, a crawl is currently in progress.</span></span>  
  
 <span data-ttu-id="c1790-140">**当前或上一次爬网的结束日期和时间**</span><span class="sxs-lookup"><span data-stu-id="c1790-140">**End Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="c1790-141">显示最近一次爬网的结束日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c1790-141">Displays the date and time that the most recent crawl ended.</span></span>  
  
 <span data-ttu-id="c1790-142">**当前或上一次爬网中的错误数**</span><span class="sxs-lookup"><span data-stu-id="c1790-142">**Errors In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="c1790-143">显示当前或最近一次爬网中的错误数。</span><span class="sxs-lookup"><span data-stu-id="c1790-143">Displays the number of errors in current or most recent crawl.</span></span>  
  
 <span data-ttu-id="c1790-144">**索引版本**</span><span class="sxs-lookup"><span data-stu-id="c1790-144">**Index Version**</span></span>  
 <span data-ttu-id="c1790-145">显示爬网开始时表的架构版本。</span><span class="sxs-lookup"><span data-stu-id="c1790-145">Displays the schema version of table at time the crawl started.</span></span>  
  
 <span data-ttu-id="c1790-146">**当前或上一次爬网中的行数**</span><span class="sxs-lookup"><span data-stu-id="c1790-146">**Rows In Current Or Last Crawl**</span></span>  
 <span data-ttu-id="c1790-147">显示在当前或最近一次爬网中更新的行数。</span><span class="sxs-lookup"><span data-stu-id="c1790-147">Displays the number of rows updated in the current or most recent crawl.</span></span>  
  
 <span data-ttu-id="c1790-148">**当前或上一次爬网的开始日期和时间**</span><span class="sxs-lookup"><span data-stu-id="c1790-148">**Start Date And Time Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="c1790-149">显示当前或最近一次爬网的开始日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c1790-149">Displays the date and time that the current or most recent crawl started.</span></span>  
  
 <span data-ttu-id="c1790-150">**下一次爬网的时间戳**</span><span class="sxs-lookup"><span data-stu-id="c1790-150">**Time Stamp For Next Crawl**</span></span>  
 <span data-ttu-id="c1790-151">显示下一次爬网的开始日期和时间。</span><span class="sxs-lookup"><span data-stu-id="c1790-151">Displays the date and time that the next crawl will start.</span></span>  
  
 <span data-ttu-id="c1790-152">**当前或上一次爬网的类型**</span><span class="sxs-lookup"><span data-stu-id="c1790-152">**Type Of Current Or Last Crawl**</span></span>  
 <span data-ttu-id="c1790-153">显示当前或最近一次爬网的类型：“完全”、“增量”、“更新”或“自动传播”。</span><span class="sxs-lookup"><span data-stu-id="c1790-153">Displays the type of the current or most recent crawl: Full, Incremental, Update, or Auto Propagation.</span></span>  
  
 <span data-ttu-id="c1790-154">**唯一索引名称**</span><span class="sxs-lookup"><span data-stu-id="c1790-154">**Unique Index Name**</span></span>  
 <span data-ttu-id="c1790-155">显示此数据库中具有唯一单列索引的所有列的名称列表。</span><span class="sxs-lookup"><span data-stu-id="c1790-155">Displays a list of all of the names of columns in this database that have unique single-column indexes.</span></span> <span data-ttu-id="c1790-156">这些列可用于创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="c1790-156">These columns can be used to create a full-text index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1790-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1790-157">See Also</span></span>  
 <span data-ttu-id="c1790-158">[使用全文索引向导](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="c1790-158">[Use the Full-Text Indexing Wizard](../../relational-databases/search/use-the-full-text-indexing-wizard.md) </span></span>  
 [<span data-ttu-id="c1790-159">CREATE FULLTEXT INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c1790-159">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
  
