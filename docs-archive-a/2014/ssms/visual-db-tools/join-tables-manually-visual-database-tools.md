---
title: 手动联接表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- manual joins [SQL Server]
- joins [SQL Server], manual
- joins [SQL Server], creating
ms.assetid: 9c785356-646b-4c87-82d4-25efd6051d9d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83f7615be3f5f18164dd3ca0f62ef6cbd9167be3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682591"
---
# <a name="join-tables-manually-visual-database-tools"></a><span data-ttu-id="ed7b2-102">手动联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ed7b2-102">Join Tables Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="ed7b2-103">向查询中添加两个或多个表时， [查询和视图设计器](visual-database-tools.md) 将尝试根据公共数据或数据库中存储的关于这些表如何相关的信息来联接这些表。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-103">When you add two (or more) tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to join them based on common data or on information stored in the database about how tables are related.</span></span> <span data-ttu-id="ed7b2-104">有关详细信息，请参阅[自动联接表 (Visual Database Tools)](join-tables-automatically-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-104">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md).</span></span> <span data-ttu-id="ed7b2-105">但是，如果查询和视图设计器未自动联接这些表，或者您希望在这些表之间创建其他联接条件，则可手动联接这些表。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-105">However, if the Query and View Designer has not joined the tables automatically, or if you want to create additional join conditions between tables, you can join tables manually.</span></span>  
  
 <span data-ttu-id="ed7b2-106">除基于包含相同信息的列之外，还可以基于任意两列之间的比较创建联接。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-106">You can create joins based on comparisons between any two columns, not just columns that contain the same information.</span></span> <span data-ttu-id="ed7b2-107">例如，如果数据库包含 `titles` 和 `roysched`两个表，则可将 `ytd_sales` 表的 `titles` 列中的值与 `lorange` 表的 `hirange` 和 `roysched` 列中的值相比较。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-107">For example, if your database contains two tables, `titles` and `roysched`, you can compare values in the `ytd_sales` column of the `titles` table against the `lorange` and `hirange` columns in the `roysched` table.</span></span> <span data-ttu-id="ed7b2-108">创建此联接将允许您查找特定的书名，这些书籍截止到目前为止的年销售额介于版税的最高和最低范围之内。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-108">Creating this join would allow you to find titles for which the year-to-date sales falls between the low and high ranges for the royalty payments.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ed7b2-109">如果联接条件中的列已建立索引，则联接的速度最快。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-109">Joins work fastest if the columns in the join condition have been indexed.</span></span> <span data-ttu-id="ed7b2-110">在某些情况下，对没有建立索引的列进行联接会导致查询速度缓慢。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-110">In some cases, joining on unindexed columns can result in a slow query.</span></span>  
  
### <a name="to-manually-join-tables-or-table-structured-objects"></a><span data-ttu-id="ed7b2-111">手动联接表或表结构对象</span><span class="sxs-lookup"><span data-stu-id="ed7b2-111">To manually join tables or table-structured objects</span></span>  
  
1.  <span data-ttu-id="ed7b2-112">将要联接的对象添加到 [“关系图”窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-112">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the objects you want to join.</span></span>  
  
2.  <span data-ttu-id="ed7b2-113">拖动第一个表或表结构对象中的联接列的名称，并将其拖放到第二个表或表结构对象中的相关列上。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-113">Drag the name of the join column in the first table or table-structured object and drop it onto the related column in the second table or table-structured object.</span></span> <span data-ttu-id="ed7b2-114">联接不能基于 `text`、`ntext` 或 i`mage` 列。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-114">You cannot base a join on `text`, `ntext`, or i`mage` columns.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ed7b2-115">联接列必须具有相同（或兼容）的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-115">The join columns must be of the same (or compatible) data types.</span></span> <span data-ttu-id="ed7b2-116">例如，如果第一个表中的联接列是日期，则必须将其与第二个表中的日期列相关。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-116">For example, if the join column in the first table is a date, you must relate it to a date column in the second table.</span></span> <span data-ttu-id="ed7b2-117">另一方面，如果第一个联接列是整数，则相关联接列也必须是整数数据类型，但它的大小可以不同。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-117">On the other hand, if the first join column is an integer, the related join column must also be of an integer data type, but it can be a different size.</span></span> <span data-ttu-id="ed7b2-118">查询和视图设计器不检查要用来创建联接的列的数据类型，但当您执行查询时，如果数据类型不兼容，数据库将显示错误。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-118">The Query and View Designer will not check the data types of the columns you use to create a join, but when you execute the query, the database will display an error if the data types are not compatible.</span></span>  
  
3.  <span data-ttu-id="ed7b2-119">如果需要，请更改联接运算符；默认情况下，该运算符是等号 (=)。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-119">If necessary, change the join operator; by default, the operator is an equal sign (=).</span></span> <span data-ttu-id="ed7b2-120">有关详细信息，请参阅[修改联接运算符 (Visual Database Tools)](modify-join-operators-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-120">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="ed7b2-121">查询和视图设计器将在 [SQL 窗格](sql-pane-visual-database-tools.md)内的 SQL 语句中添加 INNER JOIN 子句。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-121">The Query and View Designer adds an INNER JOIN clause to the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="ed7b2-122">您可以将其类型更改为外部联接。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-122">You can change the type to an outer join.</span></span> <span data-ttu-id="ed7b2-123">有关详细信息，请参阅[创建外部联接 (Visual Database Tools)](create-outer-joins-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7b2-123">For details see [Create Outer Joins &#40;Visual Database Tools&#41;](create-outer-joins-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed7b2-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed7b2-124">See Also</span></span>  
 [<span data-ttu-id="ed7b2-125">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ed7b2-125">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
