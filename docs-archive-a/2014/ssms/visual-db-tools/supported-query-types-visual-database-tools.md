---
title: 支持的查询类型 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Delete query
- queries [SQL Server], types
- Update query
- Query Designer [SQL Server], query types
- Criteria pane
- Insert Values query
- Select query
- Make Table query
- Insert Results query
- Diagram pane [Visual Database Tools]
- View Designer, query types
ms.assetid: 72b9116c-c128-4078-a78d-257a2955a3f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: b00b7018fc6d0b631696811bd1870e09842b4162
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691465"
---
# <a name="supported-query-types-visual-database-tools"></a><span data-ttu-id="40ae9-102">支持的查询类型 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="40ae9-102">Supported Query Types (Visual Database Tools)</span></span>
  <span data-ttu-id="40ae9-103">可以在 [查询和视图设计器](visual-database-tools.md)的“关系图”窗格和“条件”窗格（图形化窗格）中创建以下类型的查询：</span><span class="sxs-lookup"><span data-stu-id="40ae9-103">You can create the following types of queries in the Diagram and Criteria panes (the graphical panes) of the [Query and View Designer](visual-database-tools.md):</span></span>  
  
-   <span data-ttu-id="40ae9-104">**“选择”查询** 从一个或多个表或视图中检索数据。</span><span class="sxs-lookup"><span data-stu-id="40ae9-104">**Select query** Retrieves data from one or more tables or views.</span></span> <span data-ttu-id="40ae9-105">此类型的查询将创建一个 SQL SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-105">This type of query creates an SQL SELECT statement.</span></span>  
  
-   <span data-ttu-id="40ae9-106">**插入结果** 通过将现有行作为新行从一个表复制到另一个表或同一个表中，从而创建新行。</span><span class="sxs-lookup"><span data-stu-id="40ae9-106">**Insert Results** Creates new rows by copying existing rows from one table into another, or into the same table as new rows.</span></span> <span data-ttu-id="40ae9-107">此类型的查询将创建一个 SQL INSERT INTO...SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-107">This type of query creates an SQL INSERT INTO...SELECT statement.</span></span>  
  
-   <span data-ttu-id="40ae9-108">**插入值** 创建新行并将值插入指定列。</span><span class="sxs-lookup"><span data-stu-id="40ae9-108">**Insert Values** Creates a new row and inserts values into specified columns.</span></span> <span data-ttu-id="40ae9-109">此类型的查询将创建一个 SQL INSERT INTO...VALUES 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-109">This type of query creates an SQL INSERT INTO...VALUES statement.</span></span>  
  
-   <span data-ttu-id="40ae9-110">**“更新”查询** 更改表中一个或多个现有行中单个列的值。</span><span class="sxs-lookup"><span data-stu-id="40ae9-110">**Update query** Changes the values of individual columns in one or more existing rows in a table.</span></span> <span data-ttu-id="40ae9-111">此类型的查询将创建一个 SQL UPDATE...SET 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-111">This type of query creates an SQL UPDATE...SET statement.</span></span>  
  
-   <span data-ttu-id="40ae9-112">**“删除”查询** 从表中移除一行或多行。</span><span class="sxs-lookup"><span data-stu-id="40ae9-112">**Delete query** Removes one or more rows from a table.</span></span> <span data-ttu-id="40ae9-113">此类型的查询将创建一个 SQL DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-113">This type of query creates an SQL DELETE statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="40ae9-114">“删除”查询会从表中移除整行。</span><span class="sxs-lookup"><span data-stu-id="40ae9-114">A Delete query removes entire rows from the table.</span></span> <span data-ttu-id="40ae9-115">如果想删除单个数据列中的值，请使用“更新”查询。</span><span class="sxs-lookup"><span data-stu-id="40ae9-115">If you want to delete values from individual data columns, use an Update query.</span></span>  
  
-   <span data-ttu-id="40ae9-116">**“生成表”查询** 创建新表，并通过将查询结果复制到该表在表中创建行。</span><span class="sxs-lookup"><span data-stu-id="40ae9-116">**Make Table query** Creates a new table and creates rows in it by copying the results of a query into it.</span></span> <span data-ttu-id="40ae9-117">此类型的查询将创建一个 SQL SELECT...INTO 语句。</span><span class="sxs-lookup"><span data-stu-id="40ae9-117">This type of query creates an SQL SELECT...INTO statement.</span></span>  
  
 <span data-ttu-id="40ae9-118">除了可以使用图形化窗格创建的查询之外，还可以向 SQL 窗格中输入任何 SQL 语句，例如“联合”查询。</span><span class="sxs-lookup"><span data-stu-id="40ae9-118">In addition to the queries you can create using the graphical panes, you can enter any SQL statement into the SQL pane, such as Union queries.</span></span>  
  
 <span data-ttu-id="40ae9-119">在使用 SQL 语句创建无法在图形化窗格中显示的查询时，查询和视图设计器会将这些图形化窗格显示为灰色，以表示它们不再反映正在创建的查询。</span><span class="sxs-lookup"><span data-stu-id="40ae9-119">When you create queries using SQL statements that cannot be represented in the graphical panes, the Query and View Designer dims those panes to indicate that they do not reflect the query you are creating.</span></span> <span data-ttu-id="40ae9-120">不过，变成灰色的窗格仍然是活动的，而且在许多情况下，仍可以在这些窗格中对查询进行修改。</span><span class="sxs-lookup"><span data-stu-id="40ae9-120">However, the dimmed panes are still active and, in many cases, you can make changes to the query in those panes.</span></span> <span data-ttu-id="40ae9-121">如果所做的更改产生的查询可以在图形化窗格中显示，则这些窗格将不再显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="40ae9-121">If the changes you make result in a query that can be represented in the graphical panes, those panes are no longer dimmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ae9-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40ae9-122">See Also</span></span>  
 <span data-ttu-id="40ae9-123">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="40ae9-123">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="40ae9-124">查询类型 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="40ae9-124">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
