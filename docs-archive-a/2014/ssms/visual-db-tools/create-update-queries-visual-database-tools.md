---
title: 创建更新查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bbea575d544875dba73de923474cc11bbcb46a9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587688"
---
# <a name="create-update-queries-visual-database-tools"></a><span data-ttu-id="65fc5-102">创建更新查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="65fc5-102">Create Update Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="65fc5-103">可以使用“更新”查询在一次操作中更改多个行中的内容。</span><span class="sxs-lookup"><span data-stu-id="65fc5-103">You can change the contents of multiple rows in one operation by using an Update query.</span></span> <span data-ttu-id="65fc5-104">例如，在 `titles` 表中，可以使用“更新”查询将特定出版商出版的所有书籍都加价 10%。</span><span class="sxs-lookup"><span data-stu-id="65fc5-104">For example, in a `titles` table you can use an Update query to add 10% to the price of all books for a particular publisher.</span></span>  
  
 <span data-ttu-id="65fc5-105">在创建“更新”查询时，需要指定：</span><span class="sxs-lookup"><span data-stu-id="65fc5-105">When you create an Update query, you specify:</span></span>  
  
-   <span data-ttu-id="65fc5-106">要更新的表。</span><span class="sxs-lookup"><span data-stu-id="65fc5-106">The table to update.</span></span>  
  
-   <span data-ttu-id="65fc5-107">要更新其内容的列。</span><span class="sxs-lookup"><span data-stu-id="65fc5-107">The columns whose contents you want to update.</span></span>  
  
-   <span data-ttu-id="65fc5-108">用来更新单个列的值或表达式。</span><span class="sxs-lookup"><span data-stu-id="65fc5-108">The value or expression to use to update the individual columns.</span></span>  
  
-   <span data-ttu-id="65fc5-109">定义要更新的行的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="65fc5-109">Search conditions to define the rows you want to update.</span></span>  
  
 <span data-ttu-id="65fc5-110">例如，以下查询通过将一个出版商出版的所有书籍都加价 10% 来更新 `titles` 表：</span><span class="sxs-lookup"><span data-stu-id="65fc5-110">For example, the following query updates the `titles` table by adding 10% to the price of all titles for one publisher:</span></span>  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="65fc5-111">无法撤消执行“更新”查询的操作。</span><span class="sxs-lookup"><span data-stu-id="65fc5-111">You cannot undo the action of executing an Update query.</span></span> <span data-ttu-id="65fc5-112">作为预防措施，可在执行该查询前备份数据。</span><span class="sxs-lookup"><span data-stu-id="65fc5-112">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-update-query"></a><span data-ttu-id="65fc5-113">创建“更新”查询</span><span class="sxs-lookup"><span data-stu-id="65fc5-113">To create an Update query</span></span>  
  
1.  <span data-ttu-id="65fc5-114">将要更新的表添加到“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="65fc5-114">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="65fc5-115">在“查询设计器”  菜单中，指向“更改类型”  ，再单击“更新”  。</span><span class="sxs-lookup"><span data-stu-id="65fc5-115">From the **Query Designer** menu point to **Change Type**, and then click **Update**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65fc5-116">如果启动“更新”查询时“关系图”窗格中显示有多个表，则查询和视图设计器将显示“[选择插入值的目标表](visual-database-tools.md)”对话框，以提示你输入要更新的表名。</span><span class="sxs-lookup"><span data-stu-id="65fc5-116">If more than one table is displayed in the Diagram pane when you start the Update query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="65fc5-117">在“关系图”窗格中，单击要为其提供新值的每个列的复选框。</span><span class="sxs-lookup"><span data-stu-id="65fc5-117">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="65fc5-118">这些列将显示在“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="65fc5-118">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="65fc5-119">列只有在添加到查询后才能更新。</span><span class="sxs-lookup"><span data-stu-id="65fc5-119">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="65fc5-120">在“条件”窗格的“新建值”  列中，输入列的更新值。</span><span class="sxs-lookup"><span data-stu-id="65fc5-120">In the **New Value** column of the Criteria pane, enter the update value for the column.</span></span> <span data-ttu-id="65fc5-121">可以输入文字值、列名或表达式。</span><span class="sxs-lookup"><span data-stu-id="65fc5-121">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="65fc5-122">该值必须与要更新的列的数据类型相匹配（或兼容）。</span><span class="sxs-lookup"><span data-stu-id="65fc5-122">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="65fc5-123">查询和视图设计器无法检查值是否适合要更新的列的长度。</span><span class="sxs-lookup"><span data-stu-id="65fc5-123">The Query and View Designer cannot check that a value fits within the length of the column you are updating.</span></span> <span data-ttu-id="65fc5-124">如果所提供的值太长，那么可能会在不提出警告的情况下截断该值。</span><span class="sxs-lookup"><span data-stu-id="65fc5-124">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="65fc5-125">例如，如果 `name` 列的长度为 20 个字符，但您指定的更新值为 25 个字符，那么可能会截断后 5 个字符。</span><span class="sxs-lookup"><span data-stu-id="65fc5-125">For example, if a `name` column is 20 characters long but you specify an update value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
5.  <span data-ttu-id="65fc5-126">在“筛选器”  列中输入搜索条件，定义要更新的行。</span><span class="sxs-lookup"><span data-stu-id="65fc5-126">Define the rows to update by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="65fc5-127">有关详细信息，请参阅[指定搜索条件 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="65fc5-127">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="65fc5-128">如果未指定搜索条件，将更新指定表中的所有行。</span><span class="sxs-lookup"><span data-stu-id="65fc5-128">If you do not specify a search condition, all rows in the specified table will be updated.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="65fc5-129">当向“条件”窗格中添加要在搜索条件中使用的列时，查询和视图设计器也会将其添加到要更新的列的列表中。</span><span class="sxs-lookup"><span data-stu-id="65fc5-129">When you add a column to the Criteria pane for use in a search condition, the Query and View Designer also adds it to the list of columns to be updated.</span></span> <span data-ttu-id="65fc5-130">若要在搜索条件中使用某列但不更新该列，请在表示表或表值对象的矩形中，清除该列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="65fc5-130">If you want to use a column for a search condition but not update it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
 <span data-ttu-id="65fc5-131">在执行“更新”查询时，不会在 [“结果”窗格](results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="65fc5-131">When you execute an Update query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="65fc5-132">但是，会显示一条消息，指示已更改的行数。</span><span class="sxs-lookup"><span data-stu-id="65fc5-132">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fc5-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65fc5-133">See Also</span></span>  
 <span data-ttu-id="65fc5-134">[Visual Database Tools &#40;支持的查询类型&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="65fc5-134">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="65fc5-135">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="65fc5-135">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="65fc5-136">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="65fc5-136">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
