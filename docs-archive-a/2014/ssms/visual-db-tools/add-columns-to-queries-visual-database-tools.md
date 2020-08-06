---
title: 向查询中添加列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 49c6e575eea2d4437be1f16b400ca22120471fcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579960"
---
# <a name="add-columns-to-queries-visual-database-tools"></a><span data-ttu-id="d3ef4-102">向查询中添加列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d3ef4-102">Add Columns to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="d3ef4-103">若要在查询中使用列，必须将其添加到查询中。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-103">To use a column in a query, you must add it to the query.</span></span> <span data-ttu-id="d3ef4-104">您可以添加某个列，以在查询输出中显示该列，使用该列进行排序，搜索该列的内容或对其内容进行汇总。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-104">You might add a column to display it in query output, to use it for sorting, to search the contents of the column, or to summarize its contents.</span></span> <span data-ttu-id="d3ef4-105">您可以决定在运行查询时，“结果”窗格中将包括查询中使用的哪些列。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-105">You can decide which of the columns you use in the query are included in the results pane when the query is run.</span></span> <span data-ttu-id="d3ef4-106">有关详细信息，请参阅[从查询结果中删除列 (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="d3ef4-106">For more information see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3ef4-107">若要在查询和视图设计器中查看列的数据类型，请在“关系图”  窗格中选择表或表值对象，然后在“属性”窗口中单击“列列表”。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-107">To view the data type of a column in Query and View Designer; select the table or table-valued object in the **Diagram Pane** and in the properties window click Column List.</span></span> <span data-ttu-id="d3ef4-108">再单击省略号“(…)”以打开“列列表”对话框   。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-108">Then click the **ellipses (...)** to open the **Column List** dialog box.</span></span>  
  
 <span data-ttu-id="d3ef4-109">无论在查询中的任何位置使用列，都还可使用由列、文本、运算符和函数的任意组合组成的表达式。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-109">Wherever you use a column in a query, you can also use an expression that can consist of any combination of columns, literals, operators, and functions.</span></span>  
  
### <a name="to-add-an-individual-column"></a><span data-ttu-id="d3ef4-110">添加单个列</span><span class="sxs-lookup"><span data-stu-id="d3ef4-110">To add an individual column</span></span>  
  
-   <span data-ttu-id="d3ef4-111">在“关系图”  窗格中，选中要包括的列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-111">In the **Diagram Pane**, select the check box next to the column that you want to include.</span></span>  
  
     <span data-ttu-id="d3ef4-112">-或-</span><span class="sxs-lookup"><span data-stu-id="d3ef4-112">-or-</span></span>  
  
-   <span data-ttu-id="d3ef4-113">在“条件”  窗格中移动到第一个空白网格行，单击“列”  列中的字段，然后从下拉列表中选择一个列名。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-113">In the **Criteria Pane**, move to the first blank grid row, click the field in the **Column** column, and select a column name from the drop-down list.</span></span>  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a><span data-ttu-id="d3ef4-114">添加一个表或表值对象的所有列</span><span class="sxs-lookup"><span data-stu-id="d3ef4-114">To add all columns for one table or table-valued object</span></span>  
  
-   <span data-ttu-id="d3ef4-115">在 "**关系图" 窗格**中，选中 " \*\* \* (所有列) \*\*旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-115">In the **Diagram Pane**, select the check box next to **\*(All Columns)**.</span></span>  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a><span data-ttu-id="d3ef4-116">添加所有表和表结构对象的所有列</span><span class="sxs-lookup"><span data-stu-id="d3ef4-116">To add all columns for all tables and table-structured objects</span></span>  
  
1.  <span data-ttu-id="d3ef4-117">确保没有选定“表操作”  窗格中的任何联接线。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-117">Make sure no join lines in the **Table Operations Pane** are selected.</span></span>  
  
2.  <span data-ttu-id="d3ef4-118">右键单击“设计”窗口的空白位置，然后从快捷菜单中选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-118">Right-click in the empty space of the Design window and choose **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="d3ef4-119">在“属性”窗口中，单击“输出所有列”  ，然后从下拉列表中选择“是”  或“否”  。</span><span class="sxs-lookup"><span data-stu-id="d3ef4-119">In the Properties window click **Output all columns** and choose **Yes** or **No** from the dropdown list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ef4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3ef4-120">See Also</span></span>  
 <span data-ttu-id="d3ef4-121">[从查询结果中删除列 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3ef4-121">[Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="d3ef4-122">[&#40;Visual Database Tools&#41;从查询中删除列](remove-columns-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3ef4-122">[Remove Columns from Queries &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="d3ef4-123">[指定 Visual Database Tools &#40;搜索条件&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3ef4-123">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="d3ef4-124">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3ef4-124">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d3ef4-125">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d3ef4-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
