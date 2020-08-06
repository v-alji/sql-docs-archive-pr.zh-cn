---
title: 创建表别名 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f9e6269fe6e24e8d98922094e799fbf4b5af584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587690"
---
# <a name="create-table-aliases-visual-database-tools"></a><span data-ttu-id="85bb1-102">创建表别名 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="85bb1-102">Create Table Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="85bb1-103">别名可使表名的使用更为方便。</span><span class="sxs-lookup"><span data-stu-id="85bb1-103">Aliases can make it easier to work with table names.</span></span> <span data-ttu-id="85bb1-104">在以下情况下，使用别名很有帮助：</span><span class="sxs-lookup"><span data-stu-id="85bb1-104">Using aliases is helpful when:</span></span>  
  
-   <span data-ttu-id="85bb1-105">希望使 [SQL](visual-database-tools.md) 窗格中的语句更简短、更容易阅读。</span><span class="sxs-lookup"><span data-stu-id="85bb1-105">You want to make the statement in the [SQL Pane](visual-database-tools.md) shorter and easier to read.</span></span>  
  
-   <span data-ttu-id="85bb1-106">经常在查询中引用表名（如在限定列名时），并希望确保查询不超过特定的字符长度限制。</span><span class="sxs-lookup"><span data-stu-id="85bb1-106">You refer to the table name often in your query - such as in qualifying column names - and want to be sure you stay within a specific character-length limit for your query.</span></span> <span data-ttu-id="85bb1-107">（一些数据库对查询进行了最大长度限制。）</span><span class="sxs-lookup"><span data-stu-id="85bb1-107">(Some databases impose a maximum length for queries.)</span></span>  
  
-   <span data-ttu-id="85bb1-108">使用同一个表的多个实例（如在自联接中），并需要一种引用其中的一个实例或其他实例的方法。</span><span class="sxs-lookup"><span data-stu-id="85bb1-108">You are working with multiple instances of the same table (such as in a self-join) and need a way to refer to one instance or the other.</span></span>  
  
 <span data-ttu-id="85bb1-109">例如，可以为表名 `"e"` _ `employee`创建别名`information`，然后在查询的其余部分使用 `"e"` 引用该表。</span><span class="sxs-lookup"><span data-stu-id="85bb1-109">For example, you can create an alias `"e"` for a table name `employee`_`information`, and then refer to the table as `"e"` throughout the rest of the query.</span></span>  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a><span data-ttu-id="85bb1-110">为表或表值对象创建别名</span><span class="sxs-lookup"><span data-stu-id="85bb1-110">To create an alias for a table or table-valued object</span></span>  
  
1.  <span data-ttu-id="85bb1-111">将表或表值对象添加到查询中。</span><span class="sxs-lookup"><span data-stu-id="85bb1-111">Add the table or table-valued object to your query.</span></span>  
  
2.  <span data-ttu-id="85bb1-112">在“关系图”  窗格中，右键单击要为其创建别名的对象，然后从快捷菜单中选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="85bb1-112">In the **Diagram Pane**, right-click the object for which you want to create an alias, then select **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="85bb1-113">在“属性”  窗口的“别名”  字段中输入别名。</span><span class="sxs-lookup"><span data-stu-id="85bb1-113">In the **Properties** window, enter the alias in the **Alias** field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85bb1-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85bb1-114">See Also</span></span>  
 <span data-ttu-id="85bb1-115">[在 Visual Database Tools &#40;向查询中添加表&#41;](add-tables-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="85bb1-115">[Add Tables to Queries &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="85bb1-116">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="85bb1-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="85bb1-117">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="85bb1-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="85bb1-118">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="85bb1-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
