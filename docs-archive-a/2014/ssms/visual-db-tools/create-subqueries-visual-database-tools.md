---
title: 创建子查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 540228839b9734992be008b5d4fb7d717176832e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587691"
---
# <a name="create-subqueries-visual-database-tools"></a><span data-ttu-id="e5701-102">创建子查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e5701-102">Create Subqueries (Visual Database Tools)</span></span>
  <span data-ttu-id="e5701-103">可以将一个查询的结果用作另一个查询的输入。</span><span class="sxs-lookup"><span data-stu-id="e5701-103">You can use the results of one query as the input for another.</span></span> <span data-ttu-id="e5701-104">可以将子查询的结果用作使用 IN(&#xA0;</ph>) 函数、EXISTS 运算符或 FROM 子句的语句。</span><span class="sxs-lookup"><span data-stu-id="e5701-104">You can use the results of a subquery as a statement that uses the IN( ) function, the EXISTS operator, or the FROM clause.</span></span>  
  
 <span data-ttu-id="e5701-105">若要创建子查询，可以在 SQL 窗格中将其直接输入，或者复制一个查询并将其粘贴到另一个查询中。</span><span class="sxs-lookup"><span data-stu-id="e5701-105">You can create a subquery by entering it directly into the SQL pane or by copying a query and pasting it into another.</span></span>  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a><span data-ttu-id="e5701-106">在 SQL 窗格中定义子查询</span><span class="sxs-lookup"><span data-stu-id="e5701-106">To define a subquery in the SQL pane</span></span>  
  
1.  <span data-ttu-id="e5701-107">创建主查询。</span><span class="sxs-lookup"><span data-stu-id="e5701-107">Create the primary query.</span></span>  
  
2.  <span data-ttu-id="e5701-108">在 SQL 窗格中选择 SQL 语句，然后使用“复制”  将该查询移动到剪贴板中。</span><span class="sxs-lookup"><span data-stu-id="e5701-108">In the SQL pane, select the SQL statement, and then use **Copy** to move the query to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="e5701-109">启动新查询，然后使用“粘贴”  将第一个查询移动到新查询的 WHERE 或 FROM 子句中。</span><span class="sxs-lookup"><span data-stu-id="e5701-109">Start the new query, and then use **Paste** to move the first query into the new query's WHERE or FROM clause.</span></span>  
  
     <span data-ttu-id="e5701-110">例如，假设有两个表（`products` 和 `suppliers`），您希望创建显示瑞典供应商的所有产品的查询。</span><span class="sxs-lookup"><span data-stu-id="e5701-110">For example, imagine you have two tables, `products` and `suppliers`, and you want to create a query showing all products for suppliers in Sweden.</span></span> <span data-ttu-id="e5701-111">在 `suppliers` 表中创建第一个查询以查找所有的瑞典供应商：</span><span class="sxs-lookup"><span data-stu-id="e5701-111">Create the first query on the `suppliers` table to find all Swedish suppliers:</span></span>  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
     <span data-ttu-id="e5701-112">使用“复制”命令将此查询移动到剪贴板中。</span><span class="sxs-lookup"><span data-stu-id="e5701-112">Use the Copy command to move this query to the Clipboard.</span></span> <span data-ttu-id="e5701-113">使用 `products` 表创建第二个查询，列出所需的产品信息：</span><span class="sxs-lookup"><span data-stu-id="e5701-113">Create the second query using the `products` table, listing the information you need about products:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
     <span data-ttu-id="e5701-114">在 SQL 窗格中，向第二个查询中添加 WHERE 子句，然后从剪贴板粘贴第一个查询。</span><span class="sxs-lookup"><span data-stu-id="e5701-114">In the SQL pane, add a WHERE clause to the second query, then paste the first query from the Clipboard.</span></span> <span data-ttu-id="e5701-115">用括号将第一个查询括起来，最终结果类似于以下形式：</span><span class="sxs-lookup"><span data-stu-id="e5701-115">Place parentheses around the first query, so that the end result looks like this:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e5701-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5701-116">See Also</span></span>  
 <span data-ttu-id="e5701-117">[Visual Database Tools &#40;支持的查询类型&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e5701-117">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e5701-118">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e5701-118">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
