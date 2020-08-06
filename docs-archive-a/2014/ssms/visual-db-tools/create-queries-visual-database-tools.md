---
title: 创建查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52392adff03b27e1c4c19f354bc62c350cccf17a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577193"
---
# <a name="create-queries-visual-database-tools"></a><span data-ttu-id="ad51a-102">创建查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ad51a-102">Create Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="ad51a-103">使用查询，您可以从数据库的表和视图中检索数据。</span><span class="sxs-lookup"><span data-stu-id="ad51a-103">Queries allow you to retrieve data from the tables and views in your database.</span></span> <span data-ttu-id="ad51a-104">在“查询和视图设计器”  中创建和使用查询，该窗口由四个窗格组成：[“关系图”窗格](visual-database-tools.md)、[“SQL”窗格](sql-pane-visual-database-tools.md)、[“条件”窗格](criteria-pane-visual-database-tools.md)和[“结果”窗格](results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ad51a-104">You create and work with queries in **Query and View Designer**, which is composed of four panes: the [Diagram Pane](visual-database-tools.md), the [SQL Pane](sql-pane-visual-database-tools.md), the [Criteria Pane](criteria-pane-visual-database-tools.md), and the [Results Pane](results-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-a-new-query"></a><span data-ttu-id="ad51a-105">创建新查询</span><span class="sxs-lookup"><span data-stu-id="ad51a-105">To create a new query</span></span>  
  
1.  <span data-ttu-id="ad51a-106">在“对象资源管理器”  中，展开要查询的数据库的“表”  节点。</span><span class="sxs-lookup"><span data-stu-id="ad51a-106">In **Object Explorer**, expand the **Tables** node for the database you want to query.</span></span> <span data-ttu-id="ad51a-107">右键单击要查询的表，再单击“打开表”  。</span><span class="sxs-lookup"><span data-stu-id="ad51a-107">Right-click the table you want to query and click **Open Table**.</span></span>  
  
2.  <span data-ttu-id="ad51a-108">若要向查询添加更多表，请在“查询设计器”菜单中，选择“添加表”  。</span><span class="sxs-lookup"><span data-stu-id="ad51a-108">To add more tables to the query, on the Query Designer menu, select **Add Table**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad51a-109">如果没有看到“关系图”  、“SQL”  、“条件”  或“结果”  窗格，请在“查询设计器”菜单中指向“窗格”  ，再单击要打开的窗格。</span><span class="sxs-lookup"><span data-stu-id="ad51a-109">If you do not see the **Diagram**, **SQL**, **Criteria**, or **Results** panes, from the Query Designer menu, point to **Pane** and click the pane you want to open.</span></span>  
  
3.  <span data-ttu-id="ad51a-110">在“添加表”  对话框中，选择要查询的表，再对每个表单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="ad51a-110">In the **Add Table** dialog box, select the tables you want to query and click **Add** for each one.</span></span>  
  
4.  <span data-ttu-id="ad51a-111">添加完要查询的所有表之后，单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="ad51a-111">Once you have added all the tables you want to query, click **Close**.</span></span>  
  
     <span data-ttu-id="ad51a-112">若要在以后添加更多表，请右键单击“关系图”  窗格中的空白位置，然后在快捷菜单中单击“添加表”  。</span><span class="sxs-lookup"><span data-stu-id="ad51a-112">To add more tables later, right-click the open space in the **Diagram** pane and from the shortcut menu click **Add Table**.</span></span>  
  
5.  <span data-ttu-id="ad51a-113">在“关系图”  窗格中，对于要查询的每个列，选中其表值对象中的复选框。</span><span class="sxs-lookup"><span data-stu-id="ad51a-113">In the **Diagram Pane**, check the boxes in the table-valued objects for each column you want to query.</span></span>  
  
6.  <span data-ttu-id="ad51a-114">在“查询设计器”菜单中，选择“执行 SQL”  以运行查询。</span><span class="sxs-lookup"><span data-stu-id="ad51a-114">From the Query Designer menu, choose **Execute SQL** to run your query.</span></span>  
  
 <span data-ttu-id="ad51a-115">若要进一步改进查询，可以在“SQL”  窗格中更改 SQL 代码，或者在“条件”  窗格中选择排序顺序和列别名等选项。</span><span class="sxs-lookup"><span data-stu-id="ad51a-115">To further refine your query, you can change the SQL code in the **SQL Pane** or choose options such as sort order and column aliases in the **Criteria Pane.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad51a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad51a-116">See Also</span></span>  
 <span data-ttu-id="ad51a-117">[&#40;Visual Database Tools 保存查询&#41;](save-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ad51a-117">[Save Queries &#40;Visual Database Tools&#41;](save-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ad51a-118">[Visual Database Tools &#40;查询类型&#41;](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ad51a-118">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ad51a-119">[指定 Visual Database Tools &#40;搜索条件&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ad51a-119">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ad51a-120">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ad51a-120">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ad51a-121">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ad51a-121">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
