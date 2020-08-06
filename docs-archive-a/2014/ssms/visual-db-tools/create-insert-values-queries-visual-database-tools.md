---
title: 创建“插入值”查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fc71b0148ee8a7e92c517fe75b56c329b3c88f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689215"
---
# <a name="create-insert-values-queries-visual-database-tools"></a><span data-ttu-id="638fe-102">创建“插入值”查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="638fe-102">Create Insert Values Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="638fe-103">可以使用“插入值”查询在当前表中创建新行。</span><span class="sxs-lookup"><span data-stu-id="638fe-103">You can create a new row in the current table using an Insert Values query.</span></span> <span data-ttu-id="638fe-104">在创建“插入值”查询时，需要指定：</span><span class="sxs-lookup"><span data-stu-id="638fe-104">When you create an Insert Values query, you specify:</span></span>  
  
-   <span data-ttu-id="638fe-105">要向其中添加行的数据库表。</span><span class="sxs-lookup"><span data-stu-id="638fe-105">The database table to add the row to.</span></span>  
  
-   <span data-ttu-id="638fe-106">要添加其内容的列。</span><span class="sxs-lookup"><span data-stu-id="638fe-106">The columns whose contents you want to add.</span></span>  
  
-   <span data-ttu-id="638fe-107">要插入到各个列中的值或表达式。</span><span class="sxs-lookup"><span data-stu-id="638fe-107">The value or expression to insert into the individual columns.</span></span>  
  
 <span data-ttu-id="638fe-108">例如，下面的查询将向 `titles` 表中添加一行，指定书名、类型、出版商和价格的值：</span><span class="sxs-lookup"><span data-stu-id="638fe-108">For example, the following query adds a row to the `titles` table, specifying values for the title, type, publisher, and price:</span></span>  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 <span data-ttu-id="638fe-109">在创建“插入值”查询时，“条件”窗格将发生相应变化以仅反映可用于插入新行的选项：要插入的列名和值。</span><span class="sxs-lookup"><span data-stu-id="638fe-109">When you create an Insert Values query, the Criteria pane changes to reflect the only options available for inserting a new row: the column name and the value to insert.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="638fe-110">无法撤消执行“插入值”查询的操作。</span><span class="sxs-lookup"><span data-stu-id="638fe-110">You cannot undo the action of executing an Insert Values query.</span></span> <span data-ttu-id="638fe-111">作为预防措施，可在执行该查询前备份数据。</span><span class="sxs-lookup"><span data-stu-id="638fe-111">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-values-query"></a><span data-ttu-id="638fe-112">创建“插入值”查询</span><span class="sxs-lookup"><span data-stu-id="638fe-112">To create an Insert Values query</span></span>  
  
1.  <span data-ttu-id="638fe-113">将要更新的表添加到“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="638fe-113">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="638fe-114">在“查询设计器”  菜单中，指向“更改类型”  ，再单击“插入值”  。</span><span class="sxs-lookup"><span data-stu-id="638fe-114">From the **Query Designer** menu point to **Change Type**, and then click **Insert Values**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="638fe-115">如果启动“插入值”查询时“关系图”窗格中显示有多个表，则查询和视图设计器将显示[“选择插入值的目标表”对话框](visual-database-tools.md)，以提示你输入要更新的表名。</span><span class="sxs-lookup"><span data-stu-id="638fe-115">If more than one table is displayed in the Diagram pane when you start the Insert Values query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="638fe-116">在“关系图”窗格中，单击要为其提供新值的每个列的复选框。</span><span class="sxs-lookup"><span data-stu-id="638fe-116">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="638fe-117">这些列将显示在“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="638fe-117">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="638fe-118">列只有在添加到查询后才能更新。</span><span class="sxs-lookup"><span data-stu-id="638fe-118">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="638fe-119">在“条件”窗格的“新建值”  列中，为列输入新值。</span><span class="sxs-lookup"><span data-stu-id="638fe-119">In the **New Value** column of the Criteria pane, enter the new value for the column.</span></span> <span data-ttu-id="638fe-120">可以输入文字值、列名或表达式。</span><span class="sxs-lookup"><span data-stu-id="638fe-120">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="638fe-121">该值必须与要更新的列的数据类型相匹配（或兼容）。</span><span class="sxs-lookup"><span data-stu-id="638fe-121">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="638fe-122">查询和视图设计器无法检查值是否适合要插入的列的长度。</span><span class="sxs-lookup"><span data-stu-id="638fe-122">The Query and View Designer cannot check that a value fits within the length of the column you are inserting.</span></span> <span data-ttu-id="638fe-123">如果所提供的值太长，那么可能会在不提出警告的情况下截断该值。</span><span class="sxs-lookup"><span data-stu-id="638fe-123">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="638fe-124">例如，如果 `name` 列的长度为 20 个字符，但您指定的插入值为 25 个字符，那么可能会截断后 5 个字符。</span><span class="sxs-lookup"><span data-stu-id="638fe-124">For example, if a `name` column is 20 characters long but you specify an insert value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
 <span data-ttu-id="638fe-125">在执行“插入值”查询时，不会在 [“结果”窗格](results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="638fe-125">When you execute an Insert Values query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="638fe-126">但是，会显示一条消息，指示已更改的行数。</span><span class="sxs-lookup"><span data-stu-id="638fe-126">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638fe-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="638fe-127">See Also</span></span>  
 <span data-ttu-id="638fe-128">[Visual Database Tools &#40;支持的查询类型&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="638fe-128">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="638fe-129">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="638fe-129">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="638fe-130">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="638fe-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
