---
title: 向查询中添加表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 572002bc913cc9916a75ce2b16c12064452d250f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587132"
---
# <a name="add-tables-to-queries-visual-database-tools"></a><span data-ttu-id="f0098-102">向查询中添加表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0098-102">Add Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="f0098-103">创建查询时，实际是在从表或其他表结构对象（视图和某些用户定义的函数）中检索数据。</span><span class="sxs-lookup"><span data-stu-id="f0098-103">When you create a query, you are retrieving data from a table or other objects structured like tables - views and certain user-defined functions.</span></span> <span data-ttu-id="f0098-104">若要在查询中使用这些对象中的任何对象，可将其添加到“关系图”  窗格中。</span><span class="sxs-lookup"><span data-stu-id="f0098-104">To work with any of these objects in your query, you add them to the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a><span data-ttu-id="f0098-105">向查询中添加表或表值对象</span><span class="sxs-lookup"><span data-stu-id="f0098-105">To add a table or table-valued object to a query</span></span>  
  
1.  <span data-ttu-id="f0098-106">在查询和视图设计器的“关系图”  窗格中，右键单击背景，然后从快捷菜单中选择“添加表”  。</span><span class="sxs-lookup"><span data-stu-id="f0098-106">In the **Diagram pane** of the Query and View Designer, right-click the background and choose **Add Table** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f0098-107">在“添加表”  对话框中，选择与要添加到查询中的对象类型相应的选项卡。</span><span class="sxs-lookup"><span data-stu-id="f0098-107">In the **Add Table** dialog box, select the tab for the type of object you want to add to the query.</span></span>  
  
3.  <span data-ttu-id="f0098-108">在项的列表中，双击要添加的每一项。</span><span class="sxs-lookup"><span data-stu-id="f0098-108">In the list of items, double-click each item you want to add.</span></span>  
  
4.  <span data-ttu-id="f0098-109">完成添加项后，单击“关闭”  。</span><span class="sxs-lookup"><span data-stu-id="f0098-109">When you finish adding items, click **Close**.</span></span>  
  
     <span data-ttu-id="f0098-110">查询和视图设计器会相应地更新“关系图窗格”  、“条件窗格”  和“SQL 窗格”  。</span><span class="sxs-lookup"><span data-stu-id="f0098-110">The Query and View Designer updates the **Diagram Pane**, **Criteria Pane**, and **SQL Pane** accordingly.</span></span>  
  
 <span data-ttu-id="f0098-111">在 SQL 窗格内的语句中引用表和视图时，所引用的表和视图将自动添加到查询中。</span><span class="sxs-lookup"><span data-stu-id="f0098-111">Tables and views are automatically added to the query when you reference them in the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="f0098-112">如果您对表或表结构对象没有足够的访问权限，或者提供程序无法返回其相关信息，则查询和视图设计器将不显示该表或表结构对象的数据列。</span><span class="sxs-lookup"><span data-stu-id="f0098-112">The Query and View Designer will not display data columns for a table or table-structured object if you do not have sufficient access rights to it or if the provider cannot return information about it.</span></span> <span data-ttu-id="f0098-113">在这种情况下，仅显示该表或表值对象的标题栏和“\*(所有列)”复选框。</span><span class="sxs-lookup"><span data-stu-id="f0098-113">In such cases, only a title bar and the \* (All Columns) check box are displayed for the table or table-valued object.</span></span>  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a><span data-ttu-id="f0098-114">将现有查询添加到新查询中</span><span class="sxs-lookup"><span data-stu-id="f0098-114">To add an existing query to a new query</span></span>  
  
1.  <span data-ttu-id="f0098-115">确保在创建的新查询中显示“SQL 窗格”  。</span><span class="sxs-lookup"><span data-stu-id="f0098-115">Make sure the **SQL Pane** is displayed in the new query you are creating.</span></span>  
  
2.  <span data-ttu-id="f0098-116">在“SQL 窗格”  中，在单词 FROM 后键入左括号和右括号 ()。</span><span class="sxs-lookup"><span data-stu-id="f0098-116">In the **SQL Pane**, type a right and left parentheses () after the word FROM.</span></span>  
  
3.  <span data-ttu-id="f0098-117">为现有的查询打开查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f0098-117">Open the Query Designer for the existing query.</span></span> <span data-ttu-id="f0098-118">（现在当您打开了两个查询设计器。）</span><span class="sxs-lookup"><span data-stu-id="f0098-118">(You now have two Query Designers open.)</span></span>  
  
4.  <span data-ttu-id="f0098-119">显示内部查询的“SQL 窗格”，内部查询是指要包括在新的外部查询中的现有查询  。</span><span class="sxs-lookup"><span data-stu-id="f0098-119">Display the **SQL Pane** for the inner query - the existing query you are including in the new, outer query.</span></span>  
  
5.  <span data-ttu-id="f0098-120">选中“SQL 窗格”  中的所有文本，然后将其复制到剪贴板中。</span><span class="sxs-lookup"><span data-stu-id="f0098-120">Select all the text in the **SQL Pane**, and copy it to the Clipboard.</span></span>  
  
6.  <span data-ttu-id="f0098-121">单击新查询的“SQL 窗格”  ，将光标置于添加的括号之间，然后粘贴剪贴板中的内容。</span><span class="sxs-lookup"><span data-stu-id="f0098-121">Click in the **SQL Pane** of the new query, situate the cursor between the parentheses you added, and paste the contents of the Clipboard.</span></span>  
  
7.  <span data-ttu-id="f0098-122">仍然是在“SQL 窗格”  中，在右括号的后面添加别名。</span><span class="sxs-lookup"><span data-stu-id="f0098-122">Still in the **SQL Pane**, add an alias after the right parenthesis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0098-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0098-123">See Also</span></span>  
 <span data-ttu-id="f0098-124">[&#40;Visual Database Tools 创建表别名&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0098-124">[Create Table Aliases &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="f0098-125">[从查询中删除表 &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0098-125">[Remove Tables from Queries &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="f0098-126">[指定 Visual Database Tools &#40;搜索条件&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0098-126">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="f0098-127">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0098-127">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f0098-128">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0098-128">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
