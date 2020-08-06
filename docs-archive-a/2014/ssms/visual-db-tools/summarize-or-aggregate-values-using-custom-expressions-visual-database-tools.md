---
title: 使用自定义表达式汇总或聚合值 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9f03f82842178a68c8a3d04ebc1bd738c0ab0b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691469"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a><span data-ttu-id="4789b-102">使用自定义表达式汇总或聚合值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4789b-102">Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)</span></span>
  <span data-ttu-id="4789b-103">除了使用聚合函数来聚合数据之外，还可以创建自定义表达式来生成聚合值。</span><span class="sxs-lookup"><span data-stu-id="4789b-103">In addition to using aggregate functions to aggregate data, you can create custom expressions to produce aggregate values.</span></span> <span data-ttu-id="4789b-104">可在聚合查询中的任何位置使用自定义表达式来替代聚合函数。</span><span class="sxs-lookup"><span data-stu-id="4789b-104">You can use custom expressions in place of aggregate functions anywhere in an aggregate query.</span></span>  
  
 <span data-ttu-id="4789b-105">例如，在 `titles` 表中，您可能希望创建一个查询，不仅显示平均价格，而且还显示打折时的平均价格。</span><span class="sxs-lookup"><span data-stu-id="4789b-105">For example, in the `titles` table you might want to create a query that shows not just the average price, but what the average price would be if it were discounted.</span></span>  
  
 <span data-ttu-id="4789b-106">所包括的表达式不能基于只涉及表中单个行的计算，表达式必须基于聚合值，因为在计算表达式时只有聚合值是可用的。</span><span class="sxs-lookup"><span data-stu-id="4789b-106">You cannot include an expression that is based on calculations involving only individual rows in the table; the expression must be based on an aggregate value, because only the aggregate values are available at the time the expression is calculated.</span></span>  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a><span data-ttu-id="4789b-107">为汇总值指定自定义表达式</span><span class="sxs-lookup"><span data-stu-id="4789b-107">To specify a custom expression for a summary value</span></span>  
  
1.  <span data-ttu-id="4789b-108">为查询指定组。</span><span class="sxs-lookup"><span data-stu-id="4789b-108">Specify the groups for your query.</span></span> <span data-ttu-id="4789b-109">有关详细信息，请参阅[对查询结果中的行进行分组 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4789b-109">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="4789b-110">移动到“条件”窗格中的空白行，然后在“列”  列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="4789b-110">Move to a blank row of the Criteria pane, and then type the expression in the **Columns** column.</span></span>  
  
     <span data-ttu-id="4789b-111">[查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md)将自动为表达式分配列别名，以在查询输出中创建有用的列标题。</span><span class="sxs-lookup"><span data-stu-id="4789b-111">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically assigns a column alias to the expression to create a useful column heading in query output.</span></span> <span data-ttu-id="4789b-112">有关详细信息，请参阅[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4789b-112">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
3.  <span data-ttu-id="4789b-113">在表达式的“分组依据”  列中，选择“表达式”  。</span><span class="sxs-lookup"><span data-stu-id="4789b-113">In the **Group By** column for the expression, select **Expression**.</span></span>  
  
4.  <span data-ttu-id="4789b-114">运行查询。</span><span class="sxs-lookup"><span data-stu-id="4789b-114">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4789b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4789b-115">See Also</span></span>  
 <span data-ttu-id="4789b-116">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4789b-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4789b-117">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4789b-117">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
