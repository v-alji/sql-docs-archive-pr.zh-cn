---
title: 在查询中指定 TOP 子句 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8228779703b1bbe3753f1e2728e83b4b5c3a3d17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693162"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a><span data-ttu-id="75667-102">在查询中指定 TOP 子句 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75667-102">Specify the TOP Clause in Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="75667-103">TOP 子句仅返回查询的前 *n* 行或 *n percent* 的行。</span><span class="sxs-lookup"><span data-stu-id="75667-103">The TOP clause returns only the first *n* or *n percent* rows from a query.</span></span> <span data-ttu-id="75667-104">在需要检查部分结果以核实查询是否按预期执行时，TOP 子句十分有用，这样就不会占用返回所有查询结果所需的资源。</span><span class="sxs-lookup"><span data-stu-id="75667-104">The TOP clause is useful when you want to inspect a portion of your results to find out if your query does what you expect it to do, without taking the resources necessary to return all of the query results.</span></span>  
  
### <a name="to-specify-the-top-clause-in-queries"></a><span data-ttu-id="75667-105">在查询中指定 TOP 子句</span><span class="sxs-lookup"><span data-stu-id="75667-105">To specify the TOP clause in queries</span></span>  
  
1.  <span data-ttu-id="75667-106">在解决方案资源管理器中打开一个查询或创建新的查询。</span><span class="sxs-lookup"><span data-stu-id="75667-106">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="75667-107">在“视图”  菜单中，单击“属性窗口”  。</span><span class="sxs-lookup"><span data-stu-id="75667-107">From the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="75667-108">在“属性”  窗口中，找到并展开“Top 规范”  属性。</span><span class="sxs-lookup"><span data-stu-id="75667-108">In the **Properties Window**, locate and expand the **Top Specification** property.</span></span>  
  
4.  <span data-ttu-id="75667-109">单击“(最前面)”  子属性并将其设置为“是”  。</span><span class="sxs-lookup"><span data-stu-id="75667-109">Click the **(Top)** child property and set it to **Yes**.</span></span>  
  
5.  <span data-ttu-id="75667-110">在“表达式”  子属性中，键入结果为数值的表达式（例如，“10”或“2\*5”）。</span><span class="sxs-lookup"><span data-stu-id="75667-110">In the **Expression** child property, type an expression that has a numeric result (for example, "10" or "2\*5").</span></span>  
  
6.  <span data-ttu-id="75667-111">单击“百分比”  子属性，并指示将“表达式”  属性视为所有返回行的百分比（是）还是返回行的绝对数值（否）。</span><span class="sxs-lookup"><span data-stu-id="75667-111">Click the **Percent** child property and indicate whether or not to treat the **Expression** property as a percentage of all rows returned (Yes) or as the absolute number of rows returned (No).</span></span>  
  
7.  <span data-ttu-id="75667-112">如果查询使用 ORDER BY 子句，请单击“With Ties”  子属性，然后选择“是”  在只包含组中部分行时显示该组中的所有行，或选择“否”  截断这些行。</span><span class="sxs-lookup"><span data-stu-id="75667-112">If your query uses the ORDER BY clause, click the **With Ties** child property and choose **Yes** to display all rows in a group if only part of the group is included or **No** to truncate them.</span></span>  
  
 <span data-ttu-id="75667-113">执行以上过程时，请注意 SQL 窗格中显示的 TOP 子句会随之更改，以反映属性的最新设置。</span><span class="sxs-lookup"><span data-stu-id="75667-113">As you work through the preceding procedure, notice that the TOP clause, displayed in the SQL pane, changes to reflect the current settings of the properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75667-114">还可以通过在 SQL 窗格中编辑 TOP 子句来更改“Top 规范”  的子属性的值。</span><span class="sxs-lookup"><span data-stu-id="75667-114">You can also change the values of the child properties of the **Top Specification** by editing the TOP clause in the SQL pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75667-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75667-115">See Also</span></span>  
 <span data-ttu-id="75667-116">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="75667-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="75667-117">查询属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75667-117">Query Properties &#40;Visual Database Tools&#41;</span></span>](query-properties-visual-database-tools.md)  
  
  
