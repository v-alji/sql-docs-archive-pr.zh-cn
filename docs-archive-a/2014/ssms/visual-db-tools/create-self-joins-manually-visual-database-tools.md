---
title: 手动创建自联接 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- self-joins
- manual joins [SQL Server]
- joins [SQL Server], self
ms.assetid: 910ed516-cb84-481b-95d0-cba3e89afdba
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31e125fdfe0f7f285ea679cfe85356d1aa10353a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587693"
---
# <a name="create-self-joins-manually-visual-database-tools"></a><span data-ttu-id="778de-102">手动创建自联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="778de-102">Create Self-Joins Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="778de-103">即使表在数据库中没有自反关系，您也可将它与自身联接。</span><span class="sxs-lookup"><span data-stu-id="778de-103">You can join a table to itself even if the table does not have a reflexive relationship in the database.</span></span> <span data-ttu-id="778de-104">例如，可使用自联接查找生活在同一市县的作者对。</span><span class="sxs-lookup"><span data-stu-id="778de-104">For example, you can use a self-join to find pairs of authors living in the same city.</span></span>  
  
 <span data-ttu-id="778de-105">与任何联接一样，自联接至少需要两个表。</span><span class="sxs-lookup"><span data-stu-id="778de-105">As with any join, a self-join requires at least two tables.</span></span> <span data-ttu-id="778de-106">不同之处在于，您不是向查询中添加第二个表，而是添加同一个表的第二个实例。</span><span class="sxs-lookup"><span data-stu-id="778de-106">The difference is that, instead of adding a second table to the query, you add a second instance of the same table.</span></span> <span data-ttu-id="778de-107">这样，可将表的第一个实例中的列与第二个实例中的同一列相比较，以便对列中的值相互进行比较。</span><span class="sxs-lookup"><span data-stu-id="778de-107">That way, you can compare a column in the first instance of the table to the same column in the second instance, which allows you to compare the values in a column to each other.</span></span> <span data-ttu-id="778de-108">[查询和视图设计器](visual-database-tools.md) 为表的第二个实例分配一个别名。</span><span class="sxs-lookup"><span data-stu-id="778de-108">The [Query and View Designer](visual-database-tools.md) assigns an alias to the second instance of the table.</span></span>  
  
 <span data-ttu-id="778de-109">例如，若要创建自联接来查找居住在 Berkeley 的所有作者对，则可将表的第一个实例中的 `city` 列与第二个实例中的 `city` 列相比较。</span><span class="sxs-lookup"><span data-stu-id="778de-109">For example, if you are creating a self-join to find all pairs of authors within Berkeley, you compare the `city` column in the first instance of the table against the `city` column in the second instance.</span></span> <span data-ttu-id="778de-110">生成的查询结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="778de-110">The resulting query might look like the following:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="778de-111">创建自联接通常需要多个联接条件。</span><span class="sxs-lookup"><span data-stu-id="778de-111">Creating a self-join often requires multiple join conditions.</span></span> <span data-ttu-id="778de-112">若要了解其中的原因，请考虑上述查询的结果：</span><span class="sxs-lookup"><span data-stu-id="778de-112">To understand why, consider the result of the preceding query:</span></span>  
  
```  
Cheryl Carson       Cheryl Carson  
Abraham Bennet      Abraham Bennet  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="778de-113">第一行没有用，它只是指示 Cheryl Carson 和 Cheryl Carson 生活在同一市县。</span><span class="sxs-lookup"><span data-stu-id="778de-113">The first row is useless; it indicates that Cheryl Carson lives in the same city as Cheryl Carson.</span></span> <span data-ttu-id="778de-114">第二行也没有用。</span><span class="sxs-lookup"><span data-stu-id="778de-114">The second row is equally useless.</span></span> <span data-ttu-id="778de-115">若要消除这些无用数据，可添加另一个条件，仅保留其中的两个作者姓名是指不同作者的结果行。</span><span class="sxs-lookup"><span data-stu-id="778de-115">To eliminate this useless data, you add another condition retaining only those result rows in which the two author names describe different authors.</span></span> <span data-ttu-id="778de-116">生成的查询结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="778de-116">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             <> authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="778de-117">结果集就精简为：</span><span class="sxs-lookup"><span data-stu-id="778de-117">The result set is improved:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="778de-118">但是这两个结果行是冗余的。</span><span class="sxs-lookup"><span data-stu-id="778de-118">But the two result rows are redundant.</span></span> <span data-ttu-id="778de-119">第一行说 Carson 与 Bennet 生活在同一市县，第二行说 Bennet 与 Carson 生活在同一市县。</span><span class="sxs-lookup"><span data-stu-id="778de-119">The first says Carson lives in the same city as Bennet, and the second says the Bennet lives in the same city as Carson.</span></span> <span data-ttu-id="778de-120">若要消除这一冗余，可将第二个联接条件从“不等于”更改为“小于”。</span><span class="sxs-lookup"><span data-stu-id="778de-120">To eliminate this redundancy, you can alter the second join condition from "not equals" to "less than."</span></span> <span data-ttu-id="778de-121">生成的查询结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="778de-121">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             < authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="778de-122">结果集类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="778de-122">And the result set looks like this:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
```  
  
### <a name="to-create-a-self-join-manually"></a><span data-ttu-id="778de-123">手动创建自联接</span><span class="sxs-lookup"><span data-stu-id="778de-123">To create a self-join manually</span></span>  
  
1.  <span data-ttu-id="778de-124">将要使用的表或表值对象添加到 [“关系图”窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="778de-124">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the table or table-valued object you want to work with.</span></span>  
  
2.  <span data-ttu-id="778de-125">再次添加同一个表，以便“关系图”窗格中显示同一个表或表值对象两次。</span><span class="sxs-lookup"><span data-stu-id="778de-125">Add the same table again, so that the Diagram pane shows the same table or table-valued object twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="778de-126">查询和视图设计器将通过为表名添加一个顺序号来为第二个实例分配别名。</span><span class="sxs-lookup"><span data-stu-id="778de-126">The Query and View Designer assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="778de-127">此外，查询和视图设计器会在“关系图”窗格内表或表值对象的两个实例之间创建一条联接线。</span><span class="sxs-lookup"><span data-stu-id="778de-127">In addition, the Query and View Designer creates a join line between the two occurrences of the table or table-valued object within the Diagram pane.</span></span>  
  
3.  <span data-ttu-id="778de-128">右键单击联接线，再从快捷菜单中选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="778de-128">Right-click the join line and choose **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="778de-129">在“属性”窗口中，单击“联接条件和类型”，再单击该属性右侧的省略号 (…)   。</span><span class="sxs-lookup"><span data-stu-id="778de-129">In the Properties window click **Join Condition and Type** and click the **ellipses (...)** to the right of the property.</span></span>  
  
5.  <span data-ttu-id="778de-130">在[“联接”对话框](join-dialog-box-visual-database-tools.md)中，根据需要更改两个主键间的比较运算符。</span><span class="sxs-lookup"><span data-stu-id="778de-130">In the [Join Dialog Box](join-dialog-box-visual-database-tools.md) change the comparison operator between the primary keys as required.</span></span> <span data-ttu-id="778de-131">例如，可将运算符更改为小于 (<)。</span><span class="sxs-lookup"><span data-stu-id="778de-131">For example, you might change the operator to less than (<).</span></span>  
  
6.  <span data-ttu-id="778de-132">通过拖动表或表值对象的第一个实例中的主联接列的名称，并将其放置到第二个实例的相应列上，即可创建附加联接条件（例如，authors.zip = authors1.zip）。</span><span class="sxs-lookup"><span data-stu-id="778de-132">Create the additional join condition (for example, authors.zip = authors1.zip) by dragging the name of the primary join column in the first occurrence of the table or table-valued object and dropping it on the corresponding column in the second occurrence.</span></span>  
  
7.  <span data-ttu-id="778de-133">为查询指定其他选项，如输出列、搜索条件和排序顺序等。</span><span class="sxs-lookup"><span data-stu-id="778de-133">Specify other options for the query such as output columns, search conditions, and sort order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="778de-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="778de-134">See Also</span></span>  
 <span data-ttu-id="778de-135">[自动创建自联接 &#40;Visual Database Tools&#41;](create-self-joins-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="778de-135">[Create Self-Joins Automatically &#40;Visual Database Tools&#41;](create-self-joins-automatically-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="778de-136">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="778de-136">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
