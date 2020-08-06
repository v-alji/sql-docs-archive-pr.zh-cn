---
title: 指定搜索条件 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa5dab8326de079c385a3a508bc1b01b1ee1247d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586050"
---
# <a name="specify-search-conditions-visual-database-tools"></a><span data-ttu-id="d39cf-102">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d39cf-102">Specify Search Conditions (Visual Database Tools)</span></span>
  <span data-ttu-id="d39cf-103">通过指定搜索条件可以指定在查询中出现的数据行。</span><span class="sxs-lookup"><span data-stu-id="d39cf-103">You can specify the data rows that appear in your query by specifying search conditions.</span></span> <span data-ttu-id="d39cf-104">例如，若要查询 `employee` 表，则可以指定仅查找在特定区域工作的雇员。</span><span class="sxs-lookup"><span data-stu-id="d39cf-104">For example, if you are querying an `employee` table, you can specify that you want to find only the employees who work in a particular region.</span></span>  
  
 <span data-ttu-id="d39cf-105">搜索添加是使用表达式来指定的。</span><span class="sxs-lookup"><span data-stu-id="d39cf-105">You specify search conditions using an expression.</span></span> <span data-ttu-id="d39cf-106">表达式通常由运算符和搜索值组成。</span><span class="sxs-lookup"><span data-stu-id="d39cf-106">Most commonly the expression consists of an operator and a search value.</span></span> <span data-ttu-id="d39cf-107">例如，若要查找特定销售区域的雇员，可以为 `region` 列指定以下搜索条件：</span><span class="sxs-lookup"><span data-stu-id="d39cf-107">For example, to find employees in a particular sales region, you might specify the following search criterion for the `region` column:</span></span>  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d39cf-108">如果处理多个表，则查询和视图设计器将检查每个搜索条件以确定正在进行的比较是否将导致联接。</span><span class="sxs-lookup"><span data-stu-id="d39cf-108">If you are working with multiple tables, the Query and View Designer examines each search condition to determine whether the comparison you are making results in a join.</span></span> <span data-ttu-id="d39cf-109">如果将导致联接，则查询和视图设计器会自动将搜索条件转换为联接。</span><span class="sxs-lookup"><span data-stu-id="d39cf-109">If so, the Query and View Designer automatically converts the search condition into a join.</span></span> <span data-ttu-id="d39cf-110">有关详细信息，请参阅[自动联接表 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="d39cf-110">For more information, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-specify-search-conditions"></a><span data-ttu-id="d39cf-111">指定搜索条件</span><span class="sxs-lookup"><span data-stu-id="d39cf-111">To specify search conditions</span></span>  
  
1.  <span data-ttu-id="d39cf-112">如果尚未指定搜索条件，请将要在搜索条件内使用的列或表达式添加到“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="d39cf-112">If you have not done so already, add the columns or expressions that you want to use within your search condition to the Criteria pane.</span></span>  
  
     <span data-ttu-id="d39cf-113">如果创建选择查询，并且不希望在查询输出中显示搜索列或表达式，请清除每个搜索列或表达式的“输出”  列，以将其从输出列中删除。</span><span class="sxs-lookup"><span data-stu-id="d39cf-113">If you are creating a Select query and do not want the search columns or expressions to appear in the query output, clear the **Output** column for each search column or expression to remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="d39cf-114">找到包含要搜索的数据列或表达式的行，然后在“筛选器”  列中输入搜索条件。</span><span class="sxs-lookup"><span data-stu-id="d39cf-114">Locate the row containing the data column or expression to search, and then in the **Filter** column, enter a search condition.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d39cf-115">如果不输入运算符，则查询和视图设计器将自动插入相等运算符“=”。</span><span class="sxs-lookup"><span data-stu-id="d39cf-115">If you do not enter an operator, the Query and View Designer automatically inserts the equality operator "=".</span></span>  
  
 <span data-ttu-id="d39cf-116">查询和视图设计器通过添加或修改 WHERE 子句来更新 [SQL 窗格](sql-pane-visual-database-tools.md) 中的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="d39cf-116">The Query and View Designer updates the SQL statement in the [SQL Pane](sql-pane-visual-database-tools.md) by adding or modifying the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39cf-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d39cf-117">See Also</span></span>  
 <span data-ttu-id="d39cf-118">[&#40;Visual Database Tools&#41;中输入搜索值的规则](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d39cf-118">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d39cf-119">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d39cf-119">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
