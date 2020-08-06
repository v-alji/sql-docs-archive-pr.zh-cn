---
title: 创建插入结果查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- result sets [SQL Server], queries
- results [SQL Server], query
- Insert Results query
- queries [SQL Server], results
ms.assetid: 8770d630-09cc-47ec-a0e9-e9de2d7bbc89
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02643c2cf3295debe740a696941f8730d4417254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689217"
---
# <a name="create-insert-results-queries-visual-database-tools"></a><span data-ttu-id="c2f93-102">创建插入结果查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c2f93-102">Create Insert Results Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="c2f93-103">您可以使用“插入结果”查询将行从一个表复制到另一个表或在同一个表内复制行。</span><span class="sxs-lookup"><span data-stu-id="c2f93-103">You can copy rows from one table to another or within a table using an Insert Results query.</span></span> <span data-ttu-id="c2f93-104">例如，在 `titles` 表中，您可使用“插入结果”查询将某个出版商的所有书名信息复制到另一个可用于该出版商的表中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-104">For example, in a `titles` table, you can use an Insert Results query to copy information about all the titles for one publisher to a second table that you can make available to that publisher.</span></span> <span data-ttu-id="c2f93-105">“插入结果”查询与“生成表”查询类似，但前者是将行复制到现有表中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-105">An Insert Results query is similar to Make Table Queries, but copies rows into an existing table.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="c2f93-106">您也可以使用剪切和粘贴功能将行从一个表复制到另一个表中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-106">You can also copy rows from one table to another using cut and paste.</span></span> <span data-ttu-id="c2f93-107">还可以为每个表创建一个查询，然后运行这些查询。</span><span class="sxs-lookup"><span data-stu-id="c2f93-107">Create a query for each table and run the queries.</span></span> <span data-ttu-id="c2f93-108">将所需的行从一个结果网格复制到另一个结果网格中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-108">Copy the rows you want from one results grid to the other.</span></span>  
  
 <span data-ttu-id="c2f93-109">当创建“插入结果”查询时，需要指定：</span><span class="sxs-lookup"><span data-stu-id="c2f93-109">When you create an Insert Results query, you specify:</span></span>  
  
-   <span data-ttu-id="c2f93-110">要将行复制到其中的数据库表（目标表）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-110">The database table to copy rows to (the destination table).</span></span>  
  
-   <span data-ttu-id="c2f93-111">从中复制行的一个或多个表（源表）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-111">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="c2f93-112">指定的源表将成为子查询的一部分。</span><span class="sxs-lookup"><span data-stu-id="c2f93-112">The source table or tables become part of a subquery.</span></span> <span data-ttu-id="c2f93-113">如果在同一个表内复制，则源表就是目标表。</span><span class="sxs-lookup"><span data-stu-id="c2f93-113">If you are copying within a table, the source table is the same as the destination table.</span></span>  
  
-   <span data-ttu-id="c2f93-114">源表中要复制其内容的列。</span><span class="sxs-lookup"><span data-stu-id="c2f93-114">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="c2f93-115">目标表中要向其中复制数据的目标列。</span><span class="sxs-lookup"><span data-stu-id="c2f93-115">The target columns in the destination table to copy the data to.</span></span>  
  
-   <span data-ttu-id="c2f93-116">定义要复制的行的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="c2f93-116">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="c2f93-117">排序顺序（如果您希望按特定顺序复制行）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-117">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="c2f93-118">“分组依据”选项（如果您希望仅复制摘要信息）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-118">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="c2f93-119">例如，下面的查询将书名信息从 `titles` 表复制到名为 `archivetitles`的存档表。</span><span class="sxs-lookup"><span data-stu-id="c2f93-119">For example, the following query copies title information from the `titles` table to an archive table called `archivetitles`.</span></span> <span data-ttu-id="c2f93-120">该查询将复制属于特定出版商的所有书名的四列内容：</span><span class="sxs-lookup"><span data-stu-id="c2f93-120">The query copies the contents of four columns for all titles belonging to a particular publisher:</span></span>  
  
```  
INSERT INTO archivetitles   
   (title_id, title, type, pub_id)  
SELECT title_id, title, type, pub_id  
FROM titles  
WHERE (pub_id = '0766')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c2f93-121">若要在新行中插入值，请使用“插入值”查询。</span><span class="sxs-lookup"><span data-stu-id="c2f93-121">To insert values into a new row, use an Insert Values query.</span></span>  
  
 <span data-ttu-id="c2f93-122">您可复制某行中所选列或全部列的内容。</span><span class="sxs-lookup"><span data-stu-id="c2f93-122">You can copy the contents of selected columns or of all columns in a row.</span></span> <span data-ttu-id="c2f93-123">不论是哪种情况，您要复制的数据都必须与要复制到其中的行内的列兼容。</span><span class="sxs-lookup"><span data-stu-id="c2f93-123">In either case, the data you are copying must be compatible with the columns in the rows you are copying to.</span></span> <span data-ttu-id="c2f93-124">例如，如果复制某列（如 `price`）中的内容，则要复制到其中的行内的列必须能够接受带小数点的数字数据。</span><span class="sxs-lookup"><span data-stu-id="c2f93-124">For example, if you copy the contents of a column such as `price`, the column in the row you are copying to must accept numeric data with decimal places.</span></span> <span data-ttu-id="c2f93-125">若要复制整个行，目标表与源表的相同物理位置的列必须要相互兼容。</span><span class="sxs-lookup"><span data-stu-id="c2f93-125">If you are copying an entire row, the destination table must have compatible columns in the same physical position as the source table.</span></span>  
  
 <span data-ttu-id="c2f93-126">当您创建“插入结果”查询时，“条件”窗格将相应变化以反映可用于复制数据的选项。</span><span class="sxs-lookup"><span data-stu-id="c2f93-126">When you create an Insert Results query, the Criteria pane changes to reflect options available for copying data.</span></span> <span data-ttu-id="c2f93-127">使用增加的“追加”列，您可以指定应将数据复制到其中的列。</span><span class="sxs-lookup"><span data-stu-id="c2f93-127">An Append column is added to allow you to specify the columns into which data should be copied.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c2f93-128">无法撤消执行“插入结果”查询的操作。</span><span class="sxs-lookup"><span data-stu-id="c2f93-128">You cannot undo the action of executing an Insert Results query.</span></span> <span data-ttu-id="c2f93-129">作为预防措施，可在执行该查询前备份数据。</span><span class="sxs-lookup"><span data-stu-id="c2f93-129">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-results-query"></a><span data-ttu-id="c2f93-130">创建“插入结果”查询</span><span class="sxs-lookup"><span data-stu-id="c2f93-130">To create an Insert Results query</span></span>  
  
1.  <span data-ttu-id="c2f93-131">创建一个新查询并添加要从其中复制行的表（源表）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-131">Create a new query and add the table from which you want to copy rows (the source table).</span></span> <span data-ttu-id="c2f93-132">若要在同一个表内复制行，则可将源表作为目标表添加。</span><span class="sxs-lookup"><span data-stu-id="c2f93-132">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
2.  <span data-ttu-id="c2f93-133">在 **“查询设计器”** 菜单中，指向 **“更改类型”** ，再单击 **“插入结果”** 。</span><span class="sxs-lookup"><span data-stu-id="c2f93-133">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
3.  <span data-ttu-id="c2f93-134">在“ [选择插入结果的目标表](visual-database-tools.md)”对话框中，选择要将行复制到其中的表（目标表）。</span><span class="sxs-lookup"><span data-stu-id="c2f93-134">In the [Choose Target Table for Insert Results Dialog Box](visual-database-tools.md), select the table to copy rows to (the destination table).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2f93-135">查询和视图设计器无法预先确定您可更新哪些表和视图。</span><span class="sxs-lookup"><span data-stu-id="c2f93-135">The Query and View Designer cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="c2f93-136">因此，“从查询选择插入的表”对话框中的“表名称”列表将显示所查询的数据连接中的所有可用表和视图，甚至包括不能将行复制到其中的表和视图。</span><span class="sxs-lookup"><span data-stu-id="c2f93-136">Therefore, the **Table Name** list in the **Choose Table for Insert From Query** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
4.  <span data-ttu-id="c2f93-137">在表示表或表值对象的矩形中，选择要复制其内容的列的名称。</span><span class="sxs-lookup"><span data-stu-id="c2f93-137">In the rectangle representing the table or table-valued object, choose the names of the columns whose contents you want to copy.</span></span> <span data-ttu-id="c2f93-138">若要复制整行，请选择 " \*\* \*)  (所有列\*\*"。</span><span class="sxs-lookup"><span data-stu-id="c2f93-138">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="c2f93-139">查询和视图设计器会将选择的列添加到“条件”窗格的“列”  列中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-139">The Query and View Designer adds the columns you choose to the **Column** column of the Criteriapane.</span></span>  
  
5.  <span data-ttu-id="c2f93-140">在“条件”窗格的“追加”  列中，为要复制的每个列选择目标表中的相应目标列。</span><span class="sxs-lookup"><span data-stu-id="c2f93-140">In the **Append** column of the Criteria pane, select a target column in the destination table for each column you are copying.</span></span> <span data-ttu-id="c2f93-141">如果要复制整行，请选择\*tablename。 \* \*</span><span class="sxs-lookup"><span data-stu-id="c2f93-141">Choose *tablename.\** if you are copying entire rows.</span></span> <span data-ttu-id="c2f93-142">目标表中的列必须与源表中的列具有相同（或兼容）的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2f93-142">The columns in the destination table must have the same (or compatible) data types as the columns in the source table.</span></span>  
  
6.  <span data-ttu-id="c2f93-143">如果希望按特定顺序复制行，请指定排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c2f93-143">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="c2f93-144">有关详细信息，请参阅[对查询结果进行排序和分组 (Visual Database Tools)](sort-and-group-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f93-144">For details, see [Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).</span></span>  
  
7.  <span data-ttu-id="c2f93-145">通过在“筛选器”  列中输入搜索条件来指定要复制的行。</span><span class="sxs-lookup"><span data-stu-id="c2f93-145">Specify the rows to copy by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="c2f93-146">有关详细信息，请参阅[指定搜索条件 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f93-146">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="c2f93-147">如果未指定搜索条件，则源表中的所有行都会复制到目标表中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-147">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2f93-148">当向“条件”窗格添加要搜索的列时，查询和视图设计器也会将该列添加到要复制的列的列表中。</span><span class="sxs-lookup"><span data-stu-id="c2f93-148">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="c2f93-149">如果希望在搜索中使用某列但不复制该列，请在表示表或表值对象的矩形中，清除该列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="c2f93-149">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
8.  <span data-ttu-id="c2f93-150">如果希望复制摘要信息，请指定“分组依据”选项。</span><span class="sxs-lookup"><span data-stu-id="c2f93-150">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="c2f93-151">有关详细信息，请参阅[汇总查询结果 (Visual Database Tools)](summarize-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f93-151">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="c2f93-152">在执行“插入结果”查询时，不会在 [“结果”窗格](results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="c2f93-152">When you execute an Insert Results query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="c2f93-153">但是，会显示一条消息，指出已复制的行数。</span><span class="sxs-lookup"><span data-stu-id="c2f93-153">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f93-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2f93-154">See Also</span></span>  
 <span data-ttu-id="c2f93-155">[Visual Database Tools &#40;查询类型&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c2f93-155">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c2f93-156">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c2f93-156">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
