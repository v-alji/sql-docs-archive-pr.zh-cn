---
title: 从查询中删除表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: stevestein
ms.author: sstein
ms.openlocfilehash: fab5380e13742f3cd289ce17f26ad2e5fb9089ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586054"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a><span data-ttu-id="6fd06-102">从查询中删除表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6fd06-102">Remove Tables from Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="6fd06-103">可从查询中移除表或任何表值对象。</span><span class="sxs-lookup"><span data-stu-id="6fd06-103">You can remove a table - or any table-valued object - from the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6fd06-104">移除表或表值对象不会从数据库中删除任何内容，该操作只会将表或表值对象从当前查询中移除。</span><span class="sxs-lookup"><span data-stu-id="6fd06-104">Removing a table or table-valued object does not delete anything from the database; it only removes it from the current query.</span></span> <span data-ttu-id="6fd06-105">有关从数据库中删除表的详细信息，请参阅[Delete Tables &#40;数据库引擎&#41;](../../relational-databases/tables/delete-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd06-105">For details about removing a table from a database, see [Delete Tables &#40;Database Engine&#41;](../../relational-databases/tables/delete-tables-database-engine.md).</span></span>  
  
### <a name="to-remove-a-table-or-table-structured-object"></a><span data-ttu-id="6fd06-106">移除表或表结构对象</span><span class="sxs-lookup"><span data-stu-id="6fd06-106">To remove a table or table-structured object</span></span>  
  
-   <span data-ttu-id="6fd06-107">在“关系图”  窗格中，选择表、视图、用户定义函数、同义词或查询，再按 Delete；或者右键单击该对象，然后在显示的对话框中选择“删除”  。</span><span class="sxs-lookup"><span data-stu-id="6fd06-107">In the **Diagram Pane**, select the table, view, user-defined function, synonym, or query, and then press DELETE, or right-click the object and then choose **Remove** in the resulting dialog box.</span></span> <span data-ttu-id="6fd06-108">您可一次选择和移除多个对象。</span><span class="sxs-lookup"><span data-stu-id="6fd06-108">You can select and remove multiple objects at one time.</span></span>  
  
     <span data-ttu-id="6fd06-109">-或-</span><span class="sxs-lookup"><span data-stu-id="6fd06-109">-or-</span></span>  
  
-   <span data-ttu-id="6fd06-110">在 **SQL 窗格**中删除对该对象的所有引用。</span><span class="sxs-lookup"><span data-stu-id="6fd06-110">Remove all references to the object in the **SQL Pane.**</span></span>  
  
 <span data-ttu-id="6fd06-111">当移除表或表值对象时，查询和视图设计器将自动删除涉及该表或表值对象的联接，并在“SQL 窗格”  和“条件窗格”  中删除对该对象的列的引用。</span><span class="sxs-lookup"><span data-stu-id="6fd06-111">When you remove a table or table-valued object, the Query and View Designer automatically removes joins that involve that table or table-valued object and removes references to the object's columns in the **SQL Pane** and **Criteria Pane**.</span></span> <span data-ttu-id="6fd06-112">但是，如果查询包含涉及该对象的复杂表达式，则只有在移除对该对象的所有引用后才会自动移除该对象。</span><span class="sxs-lookup"><span data-stu-id="6fd06-112">However, if the query contains complex expressions involving the object, the object is not automatically removed until all references to it are removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd06-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fd06-113">See Also</span></span>  
 <span data-ttu-id="6fd06-114">[在 Visual Database Tools &#40;向查询中添加表&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fd06-114">[Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fd06-115">[&#40;Visual Database Tools 创建表别名&#41;](create-table-aliases-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fd06-115">[Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fd06-116">[指定 Visual Database Tools &#40;搜索条件&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fd06-116">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6fd06-117">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6fd06-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6fd06-118">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6fd06-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
