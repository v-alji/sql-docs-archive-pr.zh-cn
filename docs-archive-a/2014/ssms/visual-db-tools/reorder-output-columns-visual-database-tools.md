---
title: 重新排列输出列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97fa3f768b03f24b8c8d154624a2d7a91aba45f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587118"
---
# <a name="reorder-output-columns-visual-database-tools"></a><span data-ttu-id="3f66b-102">重新排列输出列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3f66b-102">Reorder Output Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="3f66b-103">向“选择”查询中添加数据列的顺序决定了这些列在结果中显示的顺序。</span><span class="sxs-lookup"><span data-stu-id="3f66b-103">The order in which you add data columns to a Select query determines the order in which they appear in the results.</span></span> <span data-ttu-id="3f66b-104">向查询中添加的第一列显示在结果的最左边，接下来是第二列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="3f66b-104">The first column you add to the query appears leftmost in the results, the second column next, and so on.</span></span>  
  
 <span data-ttu-id="3f66b-105">如果创建的是“更新”或“插入”查询，则添加列的顺序将影响数据的处理顺序。</span><span class="sxs-lookup"><span data-stu-id="3f66b-105">If you are creating Update or Insert queries, the order in which you add columns affects the order in which data is processed.</span></span>  
  
 <span data-ttu-id="3f66b-106">若要控制数据列在结果集中显示的位置或控制数据列的使用顺序，可以对列重新排序。</span><span class="sxs-lookup"><span data-stu-id="3f66b-106">To control where a data column appears in the result set, or in what order it is used, you can reorder the columns.</span></span>  
  
### <a name="to-reorder-columns-for-output"></a><span data-ttu-id="3f66b-107">对输出列重新排序</span><span class="sxs-lookup"><span data-stu-id="3f66b-107">To reorder columns for output</span></span>  
  
1.  <span data-ttu-id="3f66b-108">在“ [条件](visual-database-tools.md)”窗格中，通过单击行左侧的行选择器按钮来选择包含该列的行。</span><span class="sxs-lookup"><span data-stu-id="3f66b-108">In the [Criteria pane](visual-database-tools.md), select the row containing the column by clicking the row selector button to the left of the row.</span></span>  
  
2.  <span data-ttu-id="3f66b-109">指向行选择器按钮，然后将该行拖动到新位置。</span><span class="sxs-lookup"><span data-stu-id="3f66b-109">Point to the row selector button and drag the row to a new location.</span></span>  
  
     <span data-ttu-id="3f66b-110">-或-</span><span class="sxs-lookup"><span data-stu-id="3f66b-110">-or-</span></span>  
  
     <span data-ttu-id="3f66b-111">在 [“SQL”窗格](sql-pane-visual-database-tools.md)中编辑列名的顺序。</span><span class="sxs-lookup"><span data-stu-id="3f66b-111">Edit the order of the column names in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="3f66b-112">您可以在“条件”窗格中的特定位置添加数据行，方法是：通过向“条件”窗格中插入空白行，再指定要插入的数据列。</span><span class="sxs-lookup"><span data-stu-id="3f66b-112">You can add a data row at a specific location in the Criteria pane by inserting a blank row into the Criteria pane, and then specifying the data column to insert.</span></span> <span data-ttu-id="3f66b-113">有关详细信息，请参阅[向查询中添加列 (Visual Database Tools)](add-columns-to-queries-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3f66b-113">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f66b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f66b-114">See Also</span></span>  
 <span data-ttu-id="3f66b-115">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3f66b-115">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="3f66b-116">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3f66b-116">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3f66b-117">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3f66b-117">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
