---
title: 用于更新结果的规则 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- updating query results
- Query Designer [SQL Server], Results pane
- Results pane
ms.assetid: de131ef0-ccbd-446f-9400-b93c7b8fa537
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc6befc6571f29be95b176f8de6d7dcfaed9108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691008"
---
# <a name="rules-for-updating-results-visual-database-tools"></a><span data-ttu-id="00097-102">更新结果的规则 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="00097-102">Rules for Updating Results (Visual Database Tools)</span></span>
  <span data-ttu-id="00097-103">在许多情况下，都可以更新显示在 [“结果”窗格](visual-database-tools.md)中的结果集。</span><span class="sxs-lookup"><span data-stu-id="00097-103">In many cases, you can update the result set displayed in the [Results Pane](visual-database-tools.md).</span></span> <span data-ttu-id="00097-104">不过，在某些情况下却不能这样做。</span><span class="sxs-lookup"><span data-stu-id="00097-104">However, in some cases you cannot.</span></span>  
  
 <span data-ttu-id="00097-105">一般而言，若要更新结果， [查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md) 必须具备足够的信息来唯一标识表中的行。</span><span class="sxs-lookup"><span data-stu-id="00097-105">In general, in order to update results, the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) must have sufficient information to uniquely identify the row in the table.</span></span> <span data-ttu-id="00097-106">例如，查询在输出列表中包括主键。</span><span class="sxs-lookup"><span data-stu-id="00097-106">An example is if the query includes a primary key in the output list.</span></span> <span data-ttu-id="00097-107">此外，您还必须有足够的权限才能更新数据库。</span><span class="sxs-lookup"><span data-stu-id="00097-107">In addition, you must have sufficient permission to update the database.</span></span>  
  
 <span data-ttu-id="00097-108">如果查询是基于视图的，您也许可以对视图进行更新。</span><span class="sxs-lookup"><span data-stu-id="00097-108">If your query is based on a view, you might be able to update it.</span></span> <span data-ttu-id="00097-109">同样的原则不仅仅适用于视图本身，除非这些原则适用于视图中的基础表。</span><span class="sxs-lookup"><span data-stu-id="00097-109">The same guidelines apply, except that they apply to the underlying tables in the view, not just to the view itself.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00097-110">查询和视图设计器无法事先确定您是否可更新基于某一视图的结果集。</span><span class="sxs-lookup"><span data-stu-id="00097-110">The Query and View Designer cannot determine in advance whether you can update a result set based on a view.</span></span> <span data-ttu-id="00097-111">因此，尽管您可能无法更新所有的视图，但查询设计器仍会把它们全部显示出来。</span><span class="sxs-lookup"><span data-stu-id="00097-111">Therefore, it displays all views, even though you might not be able to update them.</span></span>  
  
 <span data-ttu-id="00097-112">下表汇总了一些特定实例，在这些例子中您也许可以更新“结果”窗格中的查询结果，也许不能。</span><span class="sxs-lookup"><span data-stu-id="00097-112">The following table summarizes specific instances in which you might and might not be able to update query results in the Results pane.</span></span> <span data-ttu-id="00097-113">在许多情况下，所使用的数据库决定了您是否可以更新查询结果。</span><span class="sxs-lookup"><span data-stu-id="00097-113">In many cases, the database you are using dictates whether you can update query results.</span></span>  
  
|<span data-ttu-id="00097-114">查询</span><span class="sxs-lookup"><span data-stu-id="00097-114">Query</span></span>|<span data-ttu-id="00097-115">结果是否可更新</span><span class="sxs-lookup"><span data-stu-id="00097-115">Can results be updated?</span></span>|  
|-----------|-----------------------------|  
|<span data-ttu-id="00097-116">基于表并且输出列表中包含主键的查询</span><span class="sxs-lookup"><span data-stu-id="00097-116">Query based on one table with primary key in the output list</span></span>|<span data-ttu-id="00097-117">是（但下面列出的除外）。</span><span class="sxs-lookup"><span data-stu-id="00097-117">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="00097-118">基于无唯一索引和主键的表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-118">Query based on a table with no unique index and without a primary key</span></span>|<span data-ttu-id="00097-119">取决于查询和数据库。</span><span class="sxs-lookup"><span data-stu-id="00097-119">Depends on query and database.</span></span> <span data-ttu-id="00097-120">有些数据库在有足够的信息用于唯一地标识记录时才允许进行更新。</span><span class="sxs-lookup"><span data-stu-id="00097-120">Some databases allow updates if sufficient information is available to uniquely identify records.</span></span>|  
|<span data-ttu-id="00097-121">基于未联接在一起的多个表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-121">Query based on multiple tables which are not joined</span></span>|<span data-ttu-id="00097-122">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-122">No.</span></span>|  
|<span data-ttu-id="00097-123">基于数据库中标记为只读数据的查询</span><span class="sxs-lookup"><span data-stu-id="00097-123">Query based on data marked as read-only in the database</span></span>|<span data-ttu-id="00097-124">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-124">No.</span></span>|  
|<span data-ttu-id="00097-125">基于包含一个无约束表的视图的查询</span><span class="sxs-lookup"><span data-stu-id="00097-125">Query based on a view that involves one table with no constraints</span></span>|<span data-ttu-id="00097-126">是（但下面列出的除外）。</span><span class="sxs-lookup"><span data-stu-id="00097-126">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="00097-127">基于用一对一关系联接的表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-127">Query based on tables joined with a one-to-one relationship</span></span>|<span data-ttu-id="00097-128">是（但下面列出的除外）。</span><span class="sxs-lookup"><span data-stu-id="00097-128">Yes (except as listed below).</span></span>|  
|<span data-ttu-id="00097-129">基于用一对多关系联接的表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-129">Query based on tables joined with a one-to-many relationship</span></span>|<span data-ttu-id="00097-130">通常是。</span><span class="sxs-lookup"><span data-stu-id="00097-130">Usually.</span></span>|  
|<span data-ttu-id="00097-131">基于有多对多关系的表（不少于三个）的查询</span><span class="sxs-lookup"><span data-stu-id="00097-131">Query based on three or more tables in which there is a many-to-many relationship</span></span>|<span data-ttu-id="00097-132">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-132">No.</span></span>|  
|<span data-ttu-id="00097-133">基于未授予其更新权限的表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-133">Query based on a table for which update permission is not granted</span></span>|<span data-ttu-id="00097-134">可删除但不可更新。</span><span class="sxs-lookup"><span data-stu-id="00097-134">Can delete but not update.</span></span>|  
|<span data-ttu-id="00097-135">基于未授予其删除权限的表的查询</span><span class="sxs-lookup"><span data-stu-id="00097-135">Query based on a table for which delete permission is not granted</span></span>|<span data-ttu-id="00097-136">可更新但不可删除。</span><span class="sxs-lookup"><span data-stu-id="00097-136">Can update but not delete.</span></span>|  
|<span data-ttu-id="00097-137">聚合查询</span><span class="sxs-lookup"><span data-stu-id="00097-137">Aggregate query</span></span>|<span data-ttu-id="00097-138">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-138">No.</span></span>|  
|<span data-ttu-id="00097-139">基于包含总计或聚合函数的子查询的查询</span><span class="sxs-lookup"><span data-stu-id="00097-139">Query based on a subquery that contains totals or aggregate functions</span></span>|<span data-ttu-id="00097-140">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-140">No.</span></span>|  
|<span data-ttu-id="00097-141">包括 DISTINCT 关键字（用于排除重复的行）的查询</span><span class="sxs-lookup"><span data-stu-id="00097-141">Query that includes the DISTINCT keyword to exclude duplicate rows</span></span>|<span data-ttu-id="00097-142">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-142">No.</span></span>|  
|<span data-ttu-id="00097-143">FROM 子句包括用户定义函数的查询（查询返回一个表且用户定义函数包含多个 Select 语句）</span><span class="sxs-lookup"><span data-stu-id="00097-143">Query whose FROM clause includes a user-defined function that returns a table and the user-defined function contains multiple select statements</span></span>|<span data-ttu-id="00097-144">不是。</span><span class="sxs-lookup"><span data-stu-id="00097-144">No.</span></span>|  
|<span data-ttu-id="00097-145">FROM 子句中包括内联用户定义函数的查询</span><span class="sxs-lookup"><span data-stu-id="00097-145">Query whose FROM clause includes an inline user-defined function</span></span>|<span data-ttu-id="00097-146">是的。</span><span class="sxs-lookup"><span data-stu-id="00097-146">Yes.</span></span>|  
  
 <span data-ttu-id="00097-147">此外，您也许不能在查询结果中更新特定的列。</span><span class="sxs-lookup"><span data-stu-id="00097-147">In addition, you might not be able to update specific columns in the query results.</span></span> <span data-ttu-id="00097-148">下面的列表汇总了不能在“结果”窗格中更新的特定类型的列。</span><span class="sxs-lookup"><span data-stu-id="00097-148">The following list summarizes specific types of columns that you cannot update in the Results pane.</span></span>  
  
-   <span data-ttu-id="00097-149">基于表达式的列</span><span class="sxs-lookup"><span data-stu-id="00097-149">Columns based on expressions</span></span>  
  
-   <span data-ttu-id="00097-150">基于用户定义的标量函数的列</span><span class="sxs-lookup"><span data-stu-id="00097-150">Columns based on scalar user-defined functions</span></span>  
  
-   <span data-ttu-id="00097-151">已由其他用户删除的行或列</span><span class="sxs-lookup"><span data-stu-id="00097-151">Rows or columns deleted by another user</span></span>  
  
-   <span data-ttu-id="00097-152">其他用户锁定的行或列（通常，锁定的行在解锁后就可更新）</span><span class="sxs-lookup"><span data-stu-id="00097-152">Rows or columns locked by another user (locked rows can usually be updated as soon as they are unlocked)</span></span>  
  
-   <span data-ttu-id="00097-153">时间戳列或 BLOB 列</span><span class="sxs-lookup"><span data-stu-id="00097-153">Timestamp or BLOB columns</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00097-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00097-154">See Also</span></span>  
 [<span data-ttu-id="00097-155">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="00097-155">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
