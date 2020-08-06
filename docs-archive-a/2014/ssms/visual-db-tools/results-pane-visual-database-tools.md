---
title: “结果”窗格 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- synchronization [SQL Server], query results with definition
- displaying query results in grid
- grid showing query results [SQL Server]
- showing query results in grid
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- viewing query results
- queries [SQL Server], results
- Results pane
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: f0db32336931f74777be56befcde9501dc484b69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577186"
---
# <a name="results-pane-visual-database-tools"></a><span data-ttu-id="3b9a6-102">“结果”窗格 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b9a6-102">Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="3b9a6-103">“结果”窗格显示最近执行的 SELECT 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-103">The Results pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="3b9a6-104">（其他类型查询的结果会在消息框中显示。）若要打开“结果”窗格，请打开或创建一个查询或视图，或者返回某个表的数据。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-104">(The results of other query types are displayed in message boxes.) To open the results pane, open or create a query or view or return a table's data.</span></span> <span data-ttu-id="3b9a6-105">如果默认情况下不显示“结果”窗格，请在 **“查询设计器”** 菜单中，指向 **“窗格”** ，再单击 **“结果”** 。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-105">If the results pane doesn't show by default, from the **Query Designer** menu, point to **Pane**, and then click **Results**.</span></span>  
  
## <a name="what-you-can-do-in-the-results-pane"></a><span data-ttu-id="3b9a6-106">可以在“结果”窗格中执行的操作</span><span class="sxs-lookup"><span data-stu-id="3b9a6-106">What You Can Do in the Results Pane</span></span>  
  
-   <span data-ttu-id="3b9a6-107">在类似于电子表格的网格中查看最近执行的 SELECT 查询的结果集。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-107">View the result set for the most recently executed SELECT query in a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="3b9a6-108">对于显示单个表或视图中的数据的查询或视图，您可以编辑结果集中各个列的值、添加新行以及删除现有的行。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-108">For queries or views that show data from a single table or view, you can edit the values in individual columns in the result set, add new rows, and delete existing rows.</span></span>  
  
## <a name="limitations-in-the-results-pane"></a><span data-ttu-id="3b9a6-109">“结果”窗格中的限制</span><span class="sxs-lookup"><span data-stu-id="3b9a6-109">Limitations in the Results Pane</span></span>  
  
-   <span data-ttu-id="3b9a6-110">表值函数返回的结果只有在某些情况下才能更新。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-110">Results returned by table-valued functions can only be updated in some cases.</span></span>  
  
-   <span data-ttu-id="3b9a6-111">如果查询或视图所包括的列来自多个表或视图，则不能更新这些查询或视图。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-111">Queries or views that include columns from more than one table or view cannot be updated.</span></span>  
  
-   <span data-ttu-id="3b9a6-112">不能更新存储过程返回的结果。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-112">Results returned by a stored procedure cannot be updated.</span></span>  
  
-   <span data-ttu-id="3b9a6-113">不能更新使用 GROUP BY 或 DISTINCT 子句的查询或视图。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-113">Queries or views using the GROUP BY or DISTINCT clauses are not updatable.</span></span>  
  
## <a name="navigating-in-the-results-pane"></a><span data-ttu-id="3b9a6-114">在“结果”窗格中导航</span><span class="sxs-lookup"><span data-stu-id="3b9a6-114">Navigating in the Results Pane</span></span>  
 <span data-ttu-id="3b9a6-115">您可以使用“结果”窗格底部的导航栏在记录之间快速导航。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-115">You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.</span></span>  
  
 <span data-ttu-id="3b9a6-116">导航栏中提供了多个按钮，可分别用于跳转到第一个记录、最后一个记录、下一个记录、上一个记录以及某个特定记录。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-116">There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.</span></span>  
  
 <span data-ttu-id="3b9a6-117">若要转到特定的记录，请在导航栏的文本框中键入行号，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-117">To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.</span></span>  
  
 <span data-ttu-id="3b9a6-118">有关在查询和视图设计器中使用键盘快捷方式的信息，请参阅[在查询和视图设计器中导航 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-118">For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="keeping-the-results-set-synchronized-with-the-query-definition"></a><span data-ttu-id="3b9a6-119">使结果集与查询定义保持同步</span><span class="sxs-lookup"><span data-stu-id="3b9a6-119">Keeping the Results Set Synchronized with the Query Definition</span></span>  
 <span data-ttu-id="3b9a6-120">当您处理查询或视图的结果时，可能会出现“结果”窗格中的记录与查询定义不同步的情况。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-120">While you are working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the query's definition.</span></span> <span data-ttu-id="3b9a6-121">例如，如果您用查询搜索出表的五列中的四列，然后使用“关系图”窗格将第五列添加到查询的定义中，则第五列的数据不会自动添加到“结果”窗格中。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-121">For example, if you run a query for four out of five columns in a table, and then use the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the Results pane.</span></span> <span data-ttu-id="3b9a6-122">若要使“结果”窗格反映新的查询定义，请再次运行该查询。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-122">To make the results pane reflect the new query definition, run the query again.</span></span>  
  
 <span data-ttu-id="3b9a6-123">如果某个查询发生更改，则在“结果”窗格的右下角会出现一个警报图标和文本“查询已更改”。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-123">If a query changes, an alert icon and the text "Query Changed" appears in the lower-right corner of the results pane.</span></span> <span data-ttu-id="3b9a6-124">该图标在窗格的左上角反复出现。</span><span class="sxs-lookup"><span data-stu-id="3b9a6-124">The icon is repeated in the upper-left corner of the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9a6-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b9a6-125">See Also</span></span>  
 <span data-ttu-id="3b9a6-126">[&#40;Visual Database Tools 创建查询&#41;](create-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b9a6-126">[Create Queries &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3b9a6-127">[&#40;Visual Database Tools 运行查询&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b9a6-127">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3b9a6-128">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b9a6-128">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3b9a6-129">[Visual Database Tools &#40;的 "关系图" 窗格&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b9a6-129">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3b9a6-130">[Visual Database Tools &#40;的 "条件" 窗格&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3b9a6-130">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3b9a6-131">使用“结果”窗格中的数据 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b9a6-131">Work with Data in the Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
