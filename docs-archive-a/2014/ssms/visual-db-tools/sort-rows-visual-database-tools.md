---
title: 对行进行排序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4939c08a4be8c6a7aa3a52d55928abe077f25d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692068"
---
# <a name="sort-rows-visual-database-tools"></a><span data-ttu-id="24134-102">对行进行排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="24134-102">Sort Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="24134-103">您可以对查询结果中的行进行排序。</span><span class="sxs-lookup"><span data-stu-id="24134-103">You can order the rows in a query result.</span></span> <span data-ttu-id="24134-104">也就是说，可以对特定的列或一组列进行命名，该列或这些列的值决定结果集中行的顺序。</span><span class="sxs-lookup"><span data-stu-id="24134-104">That is, you can name a particular column or set of columns whose values determine the order of rows in the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24134-105">排序顺序在一定程度上由列的排序规则顺序来决定。</span><span class="sxs-lookup"><span data-stu-id="24134-105">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="24134-106">可以在 [“排序规则”对话框](visual-database-tools.md)中更改排序规则顺序。</span><span class="sxs-lookup"><span data-stu-id="24134-106">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="24134-107">下面是几种可以用来对查询结果进行排序的方法：</span><span class="sxs-lookup"><span data-stu-id="24134-107">There are several ways in which you can sort query results:</span></span>  
  
-   <span data-ttu-id="24134-108">**可按升序或降序来排列行** 默认情况下，SQL 使用排序依据列按升序排列行。</span><span class="sxs-lookup"><span data-stu-id="24134-108">**You can arrange rows in ascending or descending order** By default, SQL uses order-by columns to arrange rows in ascending order.</span></span> <span data-ttu-id="24134-109">例如，若要依据价格按升序来排列书籍名称，只需按 price 列对行进行排序即可。</span><span class="sxs-lookup"><span data-stu-id="24134-109">For example, to arrange the book titles by ascending price, simply sort the rows by the price column.</span></span> <span data-ttu-id="24134-110">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-110">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     <span data-ttu-id="24134-111">另一方面，若要排列书籍名称，使较贵的书排在前面，可以显式指定最贵的排在第一位的顺序。</span><span class="sxs-lookup"><span data-stu-id="24134-111">On the other hand, if you want to arrange the titles with the more expensive books first, you can explicitly specify a highest-first ordering.</span></span> <span data-ttu-id="24134-112">也就是说，指定应按 price 列的降序值来排列结果行。</span><span class="sxs-lookup"><span data-stu-id="24134-112">That is, you indicate that the result rows should be arranged by descending values of the price column.</span></span> <span data-ttu-id="24134-113">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-113">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="24134-114">**可按多个列进行排序** 例如，可以创建每个作者占一行、先按省市自治区再按市县排序的结果集。</span><span class="sxs-lookup"><span data-stu-id="24134-114">**You can sort by multiple columns** For example, you can create a result set with one row for each author, ordering first by state and then by city.</span></span> <span data-ttu-id="24134-115">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-115">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   <span data-ttu-id="24134-116">**可按未显示在结果集中的列进行排序** 例如，可以创建这样的结果集：最贵的书排在第一位，尽管该书的价格没有显示在结果集中。</span><span class="sxs-lookup"><span data-stu-id="24134-116">**You can sort by columns not appearing in the result set** For example, you can create a result set with the most expensive titles first, even though the prices do not appear.</span></span> <span data-ttu-id="24134-117">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-117">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="24134-118">**可按派生列进行排序** 例如，可以创建每个书籍名称占一行的结果集，并将单本版税最高的书排在第一位。</span><span class="sxs-lookup"><span data-stu-id="24134-118">**You can sort by derived columns** For example, you can create a result set in which each row contains a book title - with the books that pay the highest royalty per copy appearing first.</span></span> <span data-ttu-id="24134-119">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-119">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     <span data-ttu-id="24134-120">（用于计算每本书单本所赚版税的公式突出显示。）</span><span class="sxs-lookup"><span data-stu-id="24134-120">(The formula for calculating the royalty that each book earns per copy is emphasized.)</span></span>  
  
     <span data-ttu-id="24134-121">若要计算派生列，可以使用 SQL 语法（如上例所示），或者使用返回标量值的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="24134-121">To calculate a derived column, you can use SQL syntax, as in the preceding example, or you can use a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="24134-122">有关用户定义函数的详细信息，请参阅 SQL Server 文档。</span><span class="sxs-lookup"><span data-stu-id="24134-122">For more information about user-defined functions, see the SQL Server documentation.</span></span>  
  
-   <span data-ttu-id="24134-123">**可对分组的行进行排序** 例如，可以创建这样的结果集：每行描述一个市县以及该市县中的作者数，并使包含作者多的市县排在前面。</span><span class="sxs-lookup"><span data-stu-id="24134-123">**You can sort grouped rows** For example; you can create a result set in which each row describes a city, plus the number of authors in that city - with the cities containing many authors appearing first.</span></span> <span data-ttu-id="24134-124">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-124">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     <span data-ttu-id="24134-125">请注意，该查询将 `state` 用作次要排序列。</span><span class="sxs-lookup"><span data-stu-id="24134-125">Notice that the query uses `state` as a secondary sort column.</span></span> <span data-ttu-id="24134-126">因此，如果两个州的作者数相同，则这两个州将按字母顺序显示。</span><span class="sxs-lookup"><span data-stu-id="24134-126">Thus, if two states have the same number of authors, those states will appear in alphabetical order.</span></span>  
  
-   <span data-ttu-id="24134-127">**可使用国际数据进行排序** 也就是说，可以使用与该列的默认约定不同的排序约定对列进行排序。</span><span class="sxs-lookup"><span data-stu-id="24134-127">**You can sort using international data** That is; you can sort a column using collating conventions that differ from the default conventions for that column.</span></span> <span data-ttu-id="24134-128">例如，可以编写一个查询，用于通过 Jaime Pati？？检索所有书名。i/o.</span><span class="sxs-lookup"><span data-stu-id="24134-128">For example, you can write a query that retrieves all the book titles by Jaime Pati??o.</span></span> <span data-ttu-id="24134-129">若要按字母顺序显示书籍名称，请对 title 列使用 Spanish 排序顺序。</span><span class="sxs-lookup"><span data-stu-id="24134-129">To display the titles in alphabetical order, you use a Spanish collating sequence for the title column.</span></span> <span data-ttu-id="24134-130">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="24134-130">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Pati??o'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="24134-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24134-131">See Also</span></span>  
 <span data-ttu-id="24134-132">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="24134-132">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="24134-133">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="24134-133">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
