---
title: 为组指定条件 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
ms.openlocfilehash: da9bc1b70fbfae8bf2a68a3a3ba332020020f310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576468"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a><span data-ttu-id="0071f-102">为组指定条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0071f-102">Specify Conditions for Groups (Visual Database Tools)</span></span>
  <span data-ttu-id="0071f-103">可以通过指定应用于整个组的条件（HAVING 子句）来限制查询中出现的组。</span><span class="sxs-lookup"><span data-stu-id="0071f-103">You can limit the groups that appear in a query by specifying a condition that applies to groups as a whole - a HAVING clause.</span></span> <span data-ttu-id="0071f-104">对数据进行分组和聚合后，将应用 HAVING 子句中的条件。</span><span class="sxs-lookup"><span data-stu-id="0071f-104">After the data has been grouped and aggregated, the conditions in the HAVING clause are applied.</span></span> <span data-ttu-id="0071f-105">只有满足条件的组才会出现在查询中。</span><span class="sxs-lookup"><span data-stu-id="0071f-105">Only the groups that meet the conditions appear in the query.</span></span>  
  
 <span data-ttu-id="0071f-106">例如，您可能希望看到 `titles` 表中每个出版商出版的所有书籍的平均价格，但只显示平均价格超过 10.00 美元的部分。</span><span class="sxs-lookup"><span data-stu-id="0071f-106">For example, you might want to see the average price of all books for each publisher in a `titles` table, but only if the average price exceeds $10.00.</span></span> <span data-ttu-id="0071f-107">在这种情况下，您可以为 HAVING 子句指定如下条件： `AVG(price) > 10`。</span><span class="sxs-lookup"><span data-stu-id="0071f-107">In that case, you could specify a HAVING clause with a condition such as `AVG(price) > 10`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0071f-108">在某些情况下，在对整个组应用条件之前，可能希望排除组中的单个行。</span><span class="sxs-lookup"><span data-stu-id="0071f-108">In some instances, you might want to exclude individual rows from groups before applying a condition to groups as a whole.</span></span> <span data-ttu-id="0071f-109">有关详细信息，请参阅[在同一查询中使用 HAVING 和 WHERE 子句 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0071f-109">For details, see [Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="0071f-110">通过使用 AND 和 OR 链接条件，可以为 HAVING 子句创建复杂的条件。</span><span class="sxs-lookup"><span data-stu-id="0071f-110">You can create complex conditions for a HAVING clause by using AND and OR to link conditions.</span></span> <span data-ttu-id="0071f-111">有关在搜索条件中使用 AND 和 OR 的详细信息，请参阅[为一列指定多个搜索条件 (Visual Database Tools)](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0071f-111">For details about using AND and OR in search conditions, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).</span></span>  
  
### <a name="to-specify-a-condition-for-a-group"></a><span data-ttu-id="0071f-112">为组指定条件</span><span class="sxs-lookup"><span data-stu-id="0071f-112">To specify a condition for a group</span></span>  
  
1.  <span data-ttu-id="0071f-113">为查询指定组。</span><span class="sxs-lookup"><span data-stu-id="0071f-113">Specify the groups for your query.</span></span> <span data-ttu-id="0071f-114">有关详细信息，请参阅[对查询结果中的行进行分组 (Visual Database Tools)](group-rows-in-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0071f-114">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="0071f-115">如果条件要基于的列不在“[条件](criteria-pane-visual-database-tools.md)”窗格中，请添加该列。</span><span class="sxs-lookup"><span data-stu-id="0071f-115">If it is not already in the [Criteria pane](criteria-pane-visual-database-tools.md), add the column on which you want to base the condition.</span></span> <span data-ttu-id="0071f-116">（大多数情况下，该条件所涉及的列已经是组或汇总列。）不能使用未包含在聚合函数或 GROUP BY 子句中的列。</span><span class="sxs-lookup"><span data-stu-id="0071f-116">(Most often the condition involves a column that is already a group or summary column.) You cannot use a column that is not part of an aggregate function or of the GROUP BY clause.</span></span>  
  
3.  <span data-ttu-id="0071f-117">在“筛选器”  列中，指定要对组应用的条件。</span><span class="sxs-lookup"><span data-stu-id="0071f-117">In the **Filter** column, specify the condition to apply to the group.</span></span>  
  
     <span data-ttu-id="0071f-118">[查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md)将自动在“[SQL 窗格](sql-pane-visual-database-tools.md)”的语句中创建 HAVING 子句，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="0071f-118">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically creates a HAVING clause in the statement in the [SQL pane](sql-pane-visual-database-tools.md), such as in the following example:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  <span data-ttu-id="0071f-119">对于要指定的每个其他条件重复第 2 和第 3 步。</span><span class="sxs-lookup"><span data-stu-id="0071f-119">Repeat steps 2 and 3 for each additional condition you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0071f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0071f-120">See Also</span></span>  
 [<span data-ttu-id="0071f-121">对查询结果进行排序和分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0071f-121">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
