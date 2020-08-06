---
title: 管理全文索引 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 92eb3669930407b359b8eeed4d3df2e802bdacdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591517"
---
# <a name="manage-full-text-indexes"></a><span data-ttu-id="13fe8-102">管理全文索引</span><span class="sxs-lookup"><span data-stu-id="13fe8-102">Manage Full-Text Indexes</span></span>
     
##  <a name="viewing-and-changing-the-properties-of-a-full-text-index"></a><a name="view"></a><span data-ttu-id="13fe8-103">查看和更改全文索引的属性</span><span class="sxs-lookup"><span data-stu-id="13fe8-103">Viewing and Changing the Properties of a Full-Text Index</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a><span data-ttu-id="13fe8-104">在 Management Studio 中查看或更改全文索引的属性</span><span class="sxs-lookup"><span data-stu-id="13fe8-104">To view or change the properties of a full-text index in Management Studio</span></span>  
  
1.  <span data-ttu-id="13fe8-105">在对象资源管理器中，展开服务器。</span><span class="sxs-lookup"><span data-stu-id="13fe8-105">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="13fe8-106">展开“数据库”，然后展开包含全文索引的数据库。</span><span class="sxs-lookup"><span data-stu-id="13fe8-106">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="13fe8-107">展开 **“表”** 。</span><span class="sxs-lookup"><span data-stu-id="13fe8-107">Expand **Tables**.</span></span>  
  
4.  <span data-ttu-id="13fe8-108">右键单击对其定义了全文索引的表，选择“全文索引”，然后在“全文索引”上下文菜单中单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="13fe8-108">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="13fe8-109">此时将打开“全文索引属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="13fe8-109">This opens the **Full-text index Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="13fe8-110">在 **“选择页”** 窗格中，您可以选择下列页中的任一页：</span><span class="sxs-lookup"><span data-stu-id="13fe8-110">In the **Select a page** pane, you can select any of the following pages:</span></span>  
  
    |<span data-ttu-id="13fe8-111">页</span><span class="sxs-lookup"><span data-stu-id="13fe8-111">Page</span></span>|<span data-ttu-id="13fe8-112">说明</span><span class="sxs-lookup"><span data-stu-id="13fe8-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="13fe8-113">**常规**</span><span class="sxs-lookup"><span data-stu-id="13fe8-113">**General**</span></span>|<span data-ttu-id="13fe8-114">显示全文索引的基本属性。</span><span class="sxs-lookup"><span data-stu-id="13fe8-114">Displays basic properties of the full-text index.</span></span> <span data-ttu-id="13fe8-115">这些基本属性包括若干个可修改属性和多个不可更改属性，后者如数据库名称、表名和全文键列的名称。</span><span class="sxs-lookup"><span data-stu-id="13fe8-115">These include several modifiable properties and a number of unchangeable properties such as database name, table name, and the name of full-text key column.</span></span> <span data-ttu-id="13fe8-116">可修改属性包括：</span><span class="sxs-lookup"><span data-stu-id="13fe8-116">The modifiable properties are:</span></span><br /><br /> <span data-ttu-id="13fe8-117">**全文索引非索引字表**</span><span class="sxs-lookup"><span data-stu-id="13fe8-117">**Full-Text Index Stoplist**</span></span><br /><br /> <span data-ttu-id="13fe8-118">**全文索引已启用**</span><span class="sxs-lookup"><span data-stu-id="13fe8-118">**Full-Text Indexing Enabled**</span></span><br /><br /> <span data-ttu-id="13fe8-119">**更改跟踪**</span><span class="sxs-lookup"><span data-stu-id="13fe8-119">**Change Tracking**</span></span><br /><br /> <span data-ttu-id="13fe8-120">**搜索属性列表**</span><span class="sxs-lookup"><span data-stu-id="13fe8-120">**Search Property List**</span></span><br /><br /> <br /><br /> <span data-ttu-id="13fe8-121">有关详细信息，请参阅[全文本索引属性（常规页）](full-text-index-properties-general-page.md)。</span><span class="sxs-lookup"><span data-stu-id="13fe8-121">For more information, see [Full-Text Index Properties &#40;General Page&#41;](full-text-index-properties-general-page.md).</span></span>|  
    |<span data-ttu-id="13fe8-122">**“列”**</span><span class="sxs-lookup"><span data-stu-id="13fe8-122">**Columns**</span></span>|<span data-ttu-id="13fe8-123">显示可用于全文索引的表列。</span><span class="sxs-lookup"><span data-stu-id="13fe8-123">Displays the table columns that are available for full-text indexing.</span></span> <span data-ttu-id="13fe8-124">对于选中的列，均会创建全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-124">The selected column or columns are full-text indexed.</span></span> <span data-ttu-id="13fe8-125">您可以根据需要选择将任意数目的可用列包括在全文索引中。</span><span class="sxs-lookup"><span data-stu-id="13fe8-125">You can select as many of the available columns as you want to include in the full-text index.</span></span> <span data-ttu-id="13fe8-126">有关详细信息，请参阅[全文本索引属性（列页）](../../2014/database-engine/full-text-index-properties-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="13fe8-126">For more information, see [Full-Text Index Properties &#40;Columns Page&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).</span></span>|  
    |<span data-ttu-id="13fe8-127">**计划**</span><span class="sxs-lookup"><span data-stu-id="13fe8-127">**Schedules**</span></span>|<span data-ttu-id="13fe8-128">使用此页可以创建或管理 SQL Server 代理作业的计划，该作业用于启动全文索引填充的表增量填充。</span><span class="sxs-lookup"><span data-stu-id="13fe8-128">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population for the full-text index populations.</span></span> <span data-ttu-id="13fe8-129">有关详细信息，请参阅 [填充全文索引](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="13fe8-129">For more information, see [Populate Full-Text Indexes](../relational-databases/indexes/indexes.md).</span></span><br /><br /> <span data-ttu-id="13fe8-130"><strong> \* \* 重要 \* 说明 \* </strong>在您退出 "**全文索引属性**" 对话框后，任何新创建的计划都将与 SQL Server 代理作业关联 (*database_name*上启动增量表填充。*table_name*) 。</span><span class="sxs-lookup"><span data-stu-id="13fe8-130"><strong>\*\* Important \*\*</strong> After you exit the **Full-Text Index Properties** dialog box, any newly created schedule is associated with a SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*).</span></span>|  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] <span data-ttu-id="13fe8-131">以保存任何更改并退出“全文索引属性”对话框。 </span><span class="sxs-lookup"><span data-stu-id="13fe8-131">to save any changes and exit the **Full-text index Properties** dialog box.</span></span>  
  
##  <a name="viewing-the-properties-of-indexed-tables-and-columns"></a><a name="props"></a><span data-ttu-id="13fe8-132">查看索引表和列的属性</span><span class="sxs-lookup"><span data-stu-id="13fe8-132">Viewing the Properties of Indexed Tables and Columns</span></span>  
 <span data-ttu-id="13fe8-133">一些 [!INCLUDE[tsql](../includes/tsql-md.md)] 函数（例如 OBJECTPROPERTYEX）可用来获取各种全文索引属性的值。</span><span class="sxs-lookup"><span data-stu-id="13fe8-133">Several [!INCLUDE[tsql](../includes/tsql-md.md)] functions such as OBJECTPROPERTYEX can be used to obtain the value of various full-text indexing properties.</span></span> <span data-ttu-id="13fe8-134">此信息可用于全文搜索的管理和故障排除。</span><span class="sxs-lookup"><span data-stu-id="13fe8-134">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="13fe8-135">下表列出了与索引表和列相关的全文属性及其相关 [!INCLUDE[tsql](../includes/tsql-md.md)] 函数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-135">The following table lists the full-text properties related to indexed tables and columns and their related [!INCLUDE[tsql](../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="13fe8-136">properties</span><span class="sxs-lookup"><span data-stu-id="13fe8-136">Property</span></span>|<span data-ttu-id="13fe8-137">说明</span><span class="sxs-lookup"><span data-stu-id="13fe8-137">Description</span></span>|<span data-ttu-id="13fe8-138">函数</span><span class="sxs-lookup"><span data-stu-id="13fe8-138">Function</span></span>|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|<span data-ttu-id="13fe8-139">表中的 TYPE COLUMN，其中包含列的文档类型信息。</span><span class="sxs-lookup"><span data-stu-id="13fe8-139">TYPE COLUMN in the table that holds the document type information of the column.</span></span>|[<span data-ttu-id="13fe8-140">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="13fe8-140">COLUMNPROPERTY</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|<span data-ttu-id="13fe8-141">列是否启用了全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-141">Whether a column has been enabled for full-text indexing.</span></span>|<span data-ttu-id="13fe8-142">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="13fe8-142">COLUMNPROPERTY</span></span>|  
|`IsFulltextKey`|<span data-ttu-id="13fe8-143">索引是否为表的全文键。</span><span class="sxs-lookup"><span data-stu-id="13fe8-143">Whether the index is the full-text key for a table.</span></span>|[<span data-ttu-id="13fe8-144">INDEXPROPERTY</span><span class="sxs-lookup"><span data-stu-id="13fe8-144">INDEXPROPERTY</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|  
|<span data-ttu-id="13fe8-145">**TableFulltextBackgroundUpdateIndexOn**</span><span class="sxs-lookup"><span data-stu-id="13fe8-145">**TableFulltextBackgroundUpdateIndexOn**</span></span>|<span data-ttu-id="13fe8-146">表是否具有全文后台更新索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-146">Whether a table has full-text background update indexing.</span></span>|[<span data-ttu-id="13fe8-147">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-147">OBJECTPROPERTYEX</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|<span data-ttu-id="13fe8-148">表的全文索引数据所在的全文目录 ID。</span><span class="sxs-lookup"><span data-stu-id="13fe8-148">Full-text catalog ID in which the full-text index data for the table resides.</span></span>|<span data-ttu-id="13fe8-149">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-149">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextChangeTrackingOn`|<span data-ttu-id="13fe8-150">表是否启用了全文更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="13fe8-150">Whether a table has full-text change-tracking enabled.</span></span>|<span data-ttu-id="13fe8-151">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-151">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextDocsProcessed`|<span data-ttu-id="13fe8-152">自开始全文检索以来所处理的行数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-152">Number of rows processed since the start of full-text indexing.</span></span>|<span data-ttu-id="13fe8-153">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-153">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="13fe8-154">**TableFulltextFailCount**</span><span class="sxs-lookup"><span data-stu-id="13fe8-154">**TableFulltextFailCount**</span></span>|<span data-ttu-id="13fe8-155">全文搜索未编制索引的行数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-155">Number of rows Full-Text Search did not index.</span></span>|<span data-ttu-id="13fe8-156">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-156">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="13fe8-157">**TableFulltextItemCount**</span><span class="sxs-lookup"><span data-stu-id="13fe8-157">**TableFulltextItemCount**</span></span>|<span data-ttu-id="13fe8-158">成功编制了全文索引的行数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-158">Number of rows that were successfully full-text indexed.</span></span>|<span data-ttu-id="13fe8-159">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-159">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextKeyColumn`|<span data-ttu-id="13fe8-160">全文唯一键列的列 ID。</span><span class="sxs-lookup"><span data-stu-id="13fe8-160">The column ID of the full-text unique key column.</span></span>|<span data-ttu-id="13fe8-161">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-161">OBJECTPROPERTYEX</span></span>|  
|`TableFullTextMergeStatus`|<span data-ttu-id="13fe8-162">具有全文索引的表当前是否正在合并。</span><span class="sxs-lookup"><span data-stu-id="13fe8-162">Whether a table that has a full-text index is currently in merging.</span></span>|<span data-ttu-id="13fe8-163">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-163">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="13fe8-164">**TableFulltextPendingChanges**</span><span class="sxs-lookup"><span data-stu-id="13fe8-164">**TableFulltextPendingChanges**</span></span>|<span data-ttu-id="13fe8-165">要处理的挂起更改跟踪项的数目。</span><span class="sxs-lookup"><span data-stu-id="13fe8-165">Number of pending change tracking entries to process.</span></span>|<span data-ttu-id="13fe8-166">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-166">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextPopulateStatus`|<span data-ttu-id="13fe8-167">全文表的填充状态。</span><span class="sxs-lookup"><span data-stu-id="13fe8-167">Population status of a full-text table.</span></span>|<span data-ttu-id="13fe8-168">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-168">OBJECTPROPERTYEX</span></span>|  
|`TableHasActiveFulltextIndex`|<span data-ttu-id="13fe8-169">表是否具有活动的全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-169">Whether a table has an active full-text index.</span></span>|<span data-ttu-id="13fe8-170">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="13fe8-170">OBJECTPROPERTYEX</span></span>|  
  
##  <a name="getting-information-about-the-full-text-key-column"></a><a name="key"></a><span data-ttu-id="13fe8-171">获取有关全文键列的信息</span><span class="sxs-lookup"><span data-stu-id="13fe8-171">Getting Information about the Full-Text Key Column</span></span>  
 <span data-ttu-id="13fe8-172">通常情况下，CONTAINSTABLE 或 FREETEXTTABLE 行集值函数的结果需要与基表相联接。</span><span class="sxs-lookup"><span data-stu-id="13fe8-172">Typically, the result of CONTAINSTABLE or FREETEXTTABLE rowset-valued functions need to be joined with the base table.</span></span> <span data-ttu-id="13fe8-173">在这样的情况下，需要知道唯一键列名称。</span><span class="sxs-lookup"><span data-stu-id="13fe8-173">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="13fe8-174">可以查询给定的唯一索引是否作为全文键使用，并且可以获取全文键列的标识符。</span><span class="sxs-lookup"><span data-stu-id="13fe8-174">You can inquire whether a given unique index is used as the full-text key, and you can obtain the identifier of the full-text key column.</span></span>  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a><span data-ttu-id="13fe8-175">查询给定的唯一索引是否作为全文键列使用</span><span class="sxs-lookup"><span data-stu-id="13fe8-175">To inquire whether a given unique index is used as the full-text key column</span></span>  
  
1.  <span data-ttu-id="13fe8-176">使用 [SELECT](/sql/t-sql/queries/select-transact-sql) 语句调用 [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-176">Use a [SELECT](/sql/t-sql/queries/select-transact-sql) statement to call the [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) function.</span></span> <span data-ttu-id="13fe8-177">在函数调用中，使用 OBJECT_ID 函数将表名 (*table_name*) 转换为表 ID，指定该表的唯一索引的名称，并指定 `IsFulltextKey` 索引属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13fe8-177">In the function call use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID, specify the name of a unique index for the table, and specify the `IsFulltextKey` index property, as follows:</span></span>  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     <span data-ttu-id="13fe8-178">如果使用此索引来强制实现全文键列的唯一性，此语句返回 1，否则返回 0。</span><span class="sxs-lookup"><span data-stu-id="13fe8-178">This statement returns 1 if the index is used to enforce uniqueness of the full-text key column and 0 if it is not.</span></span>  
  
 <span data-ttu-id="13fe8-179">**示例**</span><span class="sxs-lookup"><span data-stu-id="13fe8-179">**Example**</span></span>  
  
 <span data-ttu-id="13fe8-180">下例查询 `PK_Document_DocumentID` 索引是否用于强制实现全文键列的唯一性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13fe8-180">The following example inquires whether the `PK_Document_DocumentID` index is used to enforce the uniqueness of the full-text key column, as follows:</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 <span data-ttu-id="13fe8-181">如果使用 `PK_Document_DocumentID` 索引来强制实现全文键列的唯一性，则此示例返回 1。</span><span class="sxs-lookup"><span data-stu-id="13fe8-181">This example returns 1 if the `PK_Document_DocumentID` index is used to enforce uniqueness of the full-text key column.</span></span> <span data-ttu-id="13fe8-182">否则，它返回 0 或 NULL。</span><span class="sxs-lookup"><span data-stu-id="13fe8-182">Otherwise, it returns 0 or NULL.</span></span> <span data-ttu-id="13fe8-183">NULL 表示您使用的是无效索引名称，索引名称与表不对应，或表不存在，等等。</span><span class="sxs-lookup"><span data-stu-id="13fe8-183">NULL implies you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a><span data-ttu-id="13fe8-184">查找全文键列的标识符</span><span class="sxs-lookup"><span data-stu-id="13fe8-184">To find the identifier of the full-text key column</span></span>  
  
1.  <span data-ttu-id="13fe8-185">每个启用全文的表都有一个列，该列用于强制实现表中行的唯一性（“唯一键列”）  。</span><span class="sxs-lookup"><span data-stu-id="13fe8-185">Each full-text enabled table has a column that is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="13fe8-186">从 OBJECTPROPERTYEX 函数获取的 `TableFulltextKeyColumn` 属性包含唯一键列的列 ID。</span><span class="sxs-lookup"><span data-stu-id="13fe8-186">The `TableFulltextKeyColumn` property, obtained from the OBJECTPROPERTYEX function, contains the column ID of the unique key column.</span></span>  
  
     <span data-ttu-id="13fe8-187">若要获取此标识符，可以使用 SELECT 语句调用 OBJECTPROPERTYEX 函数。</span><span class="sxs-lookup"><span data-stu-id="13fe8-187">To obtain this identifier, you can use a SELECT statement to call the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="13fe8-188">使用 OBJECT_ID 函数将表名 (*table_name*) 转换为表 ID，并指定 `TableFulltextKeyColumn` 属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13fe8-188">Use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID and specify the `TableFulltextKeyColumn` property, as follows:</span></span>  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 <span data-ttu-id="13fe8-189">**示例**</span><span class="sxs-lookup"><span data-stu-id="13fe8-189">**Examples**</span></span>  
  
 <span data-ttu-id="13fe8-190">下例返回全文键列的标识符或 NULL。</span><span class="sxs-lookup"><span data-stu-id="13fe8-190">The following example returns the identifier of the full-text key column or NULL.</span></span> <span data-ttu-id="13fe8-191">NULL 表示您使用的是无效索引名称，索引名称与表不对应，或表不存在，等等。</span><span class="sxs-lookup"><span data-stu-id="13fe8-191">NULL implies that you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 <span data-ttu-id="13fe8-192">下例说明如何使用唯一键列的标识符获取列的名称。</span><span class="sxs-lookup"><span data-stu-id="13fe8-192">The following example shows how to use the identifier of the unique key column to obtain the name of the column.</span></span>  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 <span data-ttu-id="13fe8-193">此示例返回一个名为 `Unique Key Column`的结果集列，该结果集列显示单个行，该行包含 Document 表的唯一键列 DocumentID 的名称。</span><span class="sxs-lookup"><span data-stu-id="13fe8-193">This example returns a result set column named `Unique Key Column`, which displays a single row containing the name of the unique key column of the Document table, DocumentID.</span></span> <span data-ttu-id="13fe8-194">请注意，如果此查询包含无效的索引名称，索引名称与表不对应或表不存在等，它将返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="13fe8-194">Note that if this query contained an invalid index name, the index name did not correspond to the table, the table did not exist, and so forth, it would return NULL.</span></span>  
  
##  <a name="disabling-or-re-enabling-a-table-for-full-text-indexing"></a><a name="disable"></a><span data-ttu-id="13fe8-195">为表禁用或重新启用全文索引</span><span class="sxs-lookup"><span data-stu-id="13fe8-195">Disabling or Re-enabling a Table for Full-Text Indexing</span></span>  
 <span data-ttu-id="13fe8-196">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，默认情况下所有由用户创建的数据库都启用了全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-196">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all user-created databases are full-text enabled by default.</span></span> <span data-ttu-id="13fe8-197">另外，在为表创建全文索引并将列添加到索引之后，就会自动为单个表启用全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-197">Additionally, an individual table is automatically enabled for full-text indexing as soon as a full-text index is created on it and a column is added to the index.</span></span> <span data-ttu-id="13fe8-198">从表的全文索引中删除最后一列时，会自动为表禁用全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-198">A table is automatically disabled for full-text indexing when the last column is dropped from its full-text index.</span></span>  
  
 <span data-ttu-id="13fe8-199">对于具有全文索引的表，可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]手动为表禁用或重新启用全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-199">On a table that has a full-text index, you can manually disable or re-enable a table for full-text indexing using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a><span data-ttu-id="13fe8-200">为表启用全文索引</span><span class="sxs-lookup"><span data-stu-id="13fe8-200">To enable a table for full-text indexing</span></span>  
  
1.  <span data-ttu-id="13fe8-201">展开服务器组，展开  “数据库”，再展开包含要为其启用全文索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="13fe8-201">Expand the server group, expand **Databases**, and expand the database that contains the table you want to enable for full-text indexing.</span></span>  
  
2.  <span data-ttu-id="13fe8-202">展开“表”  ，然后右键单击要为其禁用或重新启用全文索引的表。</span><span class="sxs-lookup"><span data-stu-id="13fe8-202">Expand **Tables**, and right-click the table that you want to disable or re-enable for full-text indexing.</span></span>  
  
3.  <span data-ttu-id="13fe8-203">选择  “全文索引”，然后单击  “禁用全文索引”或  “启用全文索引”。</span><span class="sxs-lookup"><span data-stu-id="13fe8-203">Select **Full-Text index**, and then click **Disable Full-Text index** or **Enable Full-Text index**.</span></span>  
  
##  <a name="removing-a-full-text-index-from-a-table"></a><a name="remove"></a><span data-ttu-id="13fe8-204">从表中删除全文索引</span><span class="sxs-lookup"><span data-stu-id="13fe8-204">Removing a Full-Text Index from a Table</span></span>  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a><span data-ttu-id="13fe8-205">从表中删除全文索引</span><span class="sxs-lookup"><span data-stu-id="13fe8-205">To remove a full-text index from a table</span></span>  
  
1.  <span data-ttu-id="13fe8-206">在对象资源管理器中，右键单击要删除的全文索引所在的表。</span><span class="sxs-lookup"><span data-stu-id="13fe8-206">In Object Explorer, right-click the table that has the full-text index that you want to delete.</span></span>  
  
2.  <span data-ttu-id="13fe8-207">选择  “删除全文索引”。</span><span class="sxs-lookup"><span data-stu-id="13fe8-207">Select **Delete Full-Text index**.</span></span>  
  
3.  <span data-ttu-id="13fe8-208">在出现提示时，单击  “确定”，确认是否要删除该全文索引。</span><span class="sxs-lookup"><span data-stu-id="13fe8-208">When prompted, click **OK** to confirm that you want to delete the full-text index.</span></span>  
  
  
