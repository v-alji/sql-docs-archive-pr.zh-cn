---
title: 创建删除查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: stevestein
ms.author: sstein
ms.openlocfilehash: a76c3aaef623365e419f40f3058308f6217d75d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591026"
---
# <a name="create-delete-queries-visual-database-tools"></a><span data-ttu-id="2f2ca-102">创建删除查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2f2ca-102">Create Delete Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="2f2ca-103">您可以通过使用“删除”查询来删除表中的所有行。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-103">You can delete all rows in a table by using a Delete query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f2ca-104">删除表中的所有行会清除表中的数据，但不会删除表本身。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-104">Deleting all rows from a table clears the data in the table but does not delete the table itself.</span></span> <span data-ttu-id="2f2ca-105">若要从数据库中删除表，请在对象资源管理器中右键单击该表，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-105">To delete a table from a database, right-click the table in Object Explorer and click **Delete**.</span></span>  
  
 <span data-ttu-id="2f2ca-106">在创建“删除”查询时，“条件”窗格将发生相应变化以反映可用于删除行的选项。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-106">When you create a Delete query, the Criteria pane changes to reflect the options available for deleting rows.</span></span> <span data-ttu-id="2f2ca-107">因为不在“删除”查询中显示数据，所以将移除“输出”、“排序方式”和“排序顺序”列。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-107">Because you do not display data in a Delete query, the Output, Sort By, and Sort Order columns are removed.</span></span> <span data-ttu-id="2f2ca-108">此外，因为无法指定要删除的单个列，所以在代表表或表值对象的矩形中，将移除列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-108">In addition, the check boxes next to the column names in the rectangle representing the table or table-valued object are removed because you cannot specify individual columns to delete.</span></span>  
  
 <span data-ttu-id="2f2ca-109">如果查询和视图设计器不能删除一个或多个行，则将不会删除任何一个行，并且您将收到一条消息，指出哪个（些）行包含不能从数据库中删除的信息。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-109">If the Query and View Designer can't delete one or more of the rows none of them will be deleted and you will receive a message telling you which row(s) contain information that can't be deleted from the database.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2f2ca-110">无法撤消执行“删除”查询的操作。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-110">You cannot undo the action of executing a Delete query.</span></span> <span data-ttu-id="2f2ca-111">作为预防措施，请在执行“删除”查询之前备份数据。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-111">As a precaution, back up your data before executing a Delete query.</span></span>  
  
### <a name="to-create-a-delete-query"></a><span data-ttu-id="2f2ca-112">创建“删除”查询</span><span class="sxs-lookup"><span data-stu-id="2f2ca-112">To create a Delete query</span></span>  
  
1.  <span data-ttu-id="2f2ca-113">将要从中删除行的表添加到“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-113">Add the table to delete rows from to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="2f2ca-114">在“查询设计器”  菜单中，指向“更改类型”  ，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-114">From the **Query Designer** menu, point to **Change Type**, and then click **Delete**.</span></span> <span data-ttu-id="2f2ca-115">**注意** 如果启动“删除”查询时，在“关系图”窗格中显示有多个表，则查询和视图设计器将显示[“删除表”对话框](visual-database-tools.md)，以提示你选择要从中删除行的表名。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-115">**Note** If more than one table is displayed in the Diagram pane when you start the Delete query, the Query and View Designer displays the [Delete Table Dialog Box](visual-database-tools.md) to prompt you for the name of the table to delete rows from.</span></span>  
  
 <span data-ttu-id="2f2ca-116">在执行“删除”查询时，不会在 [“结果”窗格](results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-116">When you execute the Delete query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="2f2ca-117">但是，会显示一条消息，指示已删除的行数。</span><span class="sxs-lookup"><span data-stu-id="2f2ca-117">Instead, a message appears indicating how many rows were deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2ca-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f2ca-118">See Also</span></span>  
 <span data-ttu-id="2f2ca-119">[Visual Database Tools &#40;支持的查询类型&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2f2ca-119">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2f2ca-120">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2f2ca-120">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
