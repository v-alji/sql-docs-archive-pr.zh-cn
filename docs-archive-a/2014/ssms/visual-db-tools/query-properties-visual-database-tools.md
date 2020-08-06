---
title: 查询属性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69636
- vdt.ppg.querydesigner.query
ms.assetid: 07495669-6ed5-4004-904e-aae1230be5e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e3c8adfb50e15113228afe8b48218f341f19084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688403"
---
# <a name="query-properties-visual-database-tools"></a><span data-ttu-id="d58f6-102">查询属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d58f6-102">Query Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="d58f6-103">当您在查询和视图设计器中打开查询时，将在“属性”窗口中显示以下属性。</span><span class="sxs-lookup"><span data-stu-id="d58f6-103">These properties appear in the Properties window when you have a query open in Query and View Designer.</span></span> <span data-ttu-id="d58f6-104">除非另行说明，否则这些属性都可以在“属性”窗口中编辑。</span><span class="sxs-lookup"><span data-stu-id="d58f6-104">Unless otherwise noted, you can edit these properties in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d58f6-105">本主题中的属性按类别排序，而不是按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="d58f6-105">The properties in this topic are ordered by category, rather than alphabetically.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d58f6-106">选项</span><span class="sxs-lookup"><span data-stu-id="d58f6-106">Options</span></span>  
 <span data-ttu-id="d58f6-107">**标识类别**</span><span class="sxs-lookup"><span data-stu-id="d58f6-107">**Identity Category**</span></span>  
 <span data-ttu-id="d58f6-108">展开此项可显示“名称”  属性。</span><span class="sxs-lookup"><span data-stu-id="d58f6-108">Expand to show the **Name** property.</span></span>  
  
 <span data-ttu-id="d58f6-109">**名称**</span><span class="sxs-lookup"><span data-stu-id="d58f6-109">**Name**</span></span>  
 <span data-ttu-id="d58f6-110">显示当前查询的名称。</span><span class="sxs-lookup"><span data-stu-id="d58f6-110">Shows the name of the current query.</span></span> <span data-ttu-id="d58f6-111">无法在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中更改。</span><span class="sxs-lookup"><span data-stu-id="d58f6-111">Cannot be changed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="d58f6-112">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="d58f6-112">**Database Name**</span></span>  
 <span data-ttu-id="d58f6-113">显示所选表的数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="d58f6-113">Shows the name of the data source for the selected table.</span></span>  
  
 <span data-ttu-id="d58f6-114">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="d58f6-114">**Server Name**</span></span>  
 <span data-ttu-id="d58f6-115">显示用于数据源的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="d58f6-115">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="d58f6-116">**查询设计器类别**</span><span class="sxs-lookup"><span data-stu-id="d58f6-116">**Query Designer Category**</span></span>  
 <span data-ttu-id="d58f6-117">展开此项可显示剩余的属性。</span><span class="sxs-lookup"><span data-stu-id="d58f6-117">Expands to show the remaining properties.</span></span>  
  
 <span data-ttu-id="d58f6-118">**目标表**</span><span class="sxs-lookup"><span data-stu-id="d58f6-118">**Destination table**</span></span>  
 <span data-ttu-id="d58f6-119">指定要向其中插入数据的表的名称。</span><span class="sxs-lookup"><span data-stu-id="d58f6-119">Specify the name of the table into which you are inserting data.</span></span> <span data-ttu-id="d58f6-120">如果正在创建“插入”查询或“生成表”查询，则会显示此列表。</span><span class="sxs-lookup"><span data-stu-id="d58f6-120">This list appears if you are creating an INSERT query or MAKE TABLE query.</span></span> <span data-ttu-id="d58f6-121">对于“插入”查询，请从列表中选择表名。</span><span class="sxs-lookup"><span data-stu-id="d58f6-121">For an INSERT query, select a table name from the list.</span></span>  
  
 <span data-ttu-id="d58f6-122">对于“生成表”查询，请键入新表的名称。</span><span class="sxs-lookup"><span data-stu-id="d58f6-122">For a MAKE TABLE query, type the name of the new table.</span></span> <span data-ttu-id="d58f6-123">若要在另一个数据源中创建目的表，请指定完全限定的表名，包括目标数据源名称、所有者（如有需要）以及表名。</span><span class="sxs-lookup"><span data-stu-id="d58f6-123">To create a destination table in another data source, specify a fully qualified table name, including the name of the target data source, the owner (if required), and the name of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d58f6-124">查询设计器不检查该名称是否已在使用中，也不检查您是否具有创建表的权限。</span><span class="sxs-lookup"><span data-stu-id="d58f6-124">Query Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
 <span data-ttu-id="d58f6-125">**DISTINCT 值**</span><span class="sxs-lookup"><span data-stu-id="d58f6-125">**Distinct values**</span></span>  
 <span data-ttu-id="d58f6-126">指定查询将在结果集中筛选出重复值。</span><span class="sxs-lookup"><span data-stu-id="d58f6-126">Specify that the query will filter out duplicates in the result set.</span></span> <span data-ttu-id="d58f6-127">当只使用表中的部分列并且这些列可能包含重复值时，或者当联接两个或更多表的过程会在结果集中产生重复行时，此选项非常有用。</span><span class="sxs-lookup"><span data-stu-id="d58f6-127">This option is useful when you are using only some of the columns from the table or tables and those columns might contain duplicate values, or when the process of joining two or more tables produces duplicate rows in the result set.</span></span> <span data-ttu-id="d58f6-128">选择该选项等效于向 SQL 窗格内的语句中插入 DISTINCT 一词。</span><span class="sxs-lookup"><span data-stu-id="d58f6-128">Choosing this option is equivalent to inserting the word DISTINCT into the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="d58f6-129">**GROUP BY 扩展**</span><span class="sxs-lookup"><span data-stu-id="d58f6-129">**GROUP BY Extension**</span></span>  
 <span data-ttu-id="d58f6-130">指定对于基于聚合查询的查询，附加选项可用。</span><span class="sxs-lookup"><span data-stu-id="d58f6-130">Specify that additional options for queries based on aggregate queries are available.</span></span> <span data-ttu-id="d58f6-131">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-131">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="d58f6-132">**输出所有列**</span><span class="sxs-lookup"><span data-stu-id="d58f6-132">**Output All Columns**</span></span>  
 <span data-ttu-id="d58f6-133">指定当前查询中所有表的全部列都将包含在结果集中。</span><span class="sxs-lookup"><span data-stu-id="d58f6-133">Specify that all columns from all tables in the current query will be in the result set.</span></span> <span data-ttu-id="d58f6-134">选择此选项等效于在 SQL 语句的 SELECT 关键字后指定星号 (\*) 代替单个列名。</span><span class="sxs-lookup"><span data-stu-id="d58f6-134">Choosing this option is equivalent to specifying an asterisk (\*) in place of individual column names after the SELECT keyword in the SQL statement.</span></span>  
  
 <span data-ttu-id="d58f6-135">**查询参数列表**</span><span class="sxs-lookup"><span data-stu-id="d58f6-135">**Query Parameter List**</span></span>  
 <span data-ttu-id="d58f6-136">显示查询参数。</span><span class="sxs-lookup"><span data-stu-id="d58f6-136">Shows query parameters.</span></span> <span data-ttu-id="d58f6-137">若要编辑这些参数，请单击相应属性，再单击该属性右侧的省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="d58f6-137">To edit the parameters click the property and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="d58f6-138">（仅适用于一般性的 OLE DB。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-138">(Applies only to generic OLE DB.)</span></span>  
  
 <span data-ttu-id="d58f6-139">**SQL 注释**</span><span class="sxs-lookup"><span data-stu-id="d58f6-139">**SQL Comment**</span></span>  
 <span data-ttu-id="d58f6-140">显示 SQL 语句的说明。</span><span class="sxs-lookup"><span data-stu-id="d58f6-140">Shows a description of the SQL statements.</span></span> <span data-ttu-id="d58f6-141">若要查看或编辑完整的说明，请单击相应的说明，再单击属性右侧的省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="d58f6-141">To see the entire description or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="d58f6-142">您的注释可以包含查询使用者和使用时间等信息。</span><span class="sxs-lookup"><span data-stu-id="d58f6-142">Your comments can include information such as who uses the query and when they use it.</span></span> <span data-ttu-id="d58f6-143">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更高版本的数据库。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-143">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 databases or later.)</span></span>  
  
 <span data-ttu-id="d58f6-144">**Top 规范类别**</span><span class="sxs-lookup"><span data-stu-id="d58f6-144">**Top Specification Category**</span></span>  
 <span data-ttu-id="d58f6-145">展开此项可显示“Top”  、“百分比”  、“表达式”  和“With Ties”  属性的属性。</span><span class="sxs-lookup"><span data-stu-id="d58f6-145">Expand to show properties for the **Top**, **Percent**, **Expression**, and **With Ties** properties.</span></span>  
  
 <span data-ttu-id="d58f6-146">**(最前面)**</span><span class="sxs-lookup"><span data-stu-id="d58f6-146">**(Top)**</span></span>  
 <span data-ttu-id="d58f6-147">指定查询将包括 TOP 子句，该子句只返回结果集中的前 n  行或前百分之 n  行。</span><span class="sxs-lookup"><span data-stu-id="d58f6-147">Specify hat the query will include a TOP clause, which returns only the first *n* rows or first *n* percentage of rows in the result set.</span></span> <span data-ttu-id="d58f6-148">默认情况下，查询将在结果集中返回前 10 行。</span><span class="sxs-lookup"><span data-stu-id="d58f6-148">The default is that the query returns the first 10 rows in the result set.</span></span>  
  
 <span data-ttu-id="d58f6-149">使用此框可更改返回的行数或指定不同的百分比值。</span><span class="sxs-lookup"><span data-stu-id="d58f6-149">Use this box to change the number of rows to return or to specify a different percentage.</span></span> <span data-ttu-id="d58f6-150">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-150">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later.)</span></span>  
  
 <span data-ttu-id="d58f6-151">**表达式**</span><span class="sxs-lookup"><span data-stu-id="d58f6-151">**Expression**</span></span>  
 <span data-ttu-id="d58f6-152">指定查询将返回的行数或行数百分比。</span><span class="sxs-lookup"><span data-stu-id="d58f6-152">Specify the number or percentage of rows that the query will return.</span></span> <span data-ttu-id="d58f6-153">如果将“百分比”  设置为“是”，此数字表示查询将返回的行数百分比；如果将“百分比”  设置为“否”，则此数字表示要返回的行数。</span><span class="sxs-lookup"><span data-stu-id="d58f6-153">If you set **Percent** to Yes, this number is the percentage of rows the query will return; if you set **Percent** to No, it represents the number of rows to return.</span></span> <span data-ttu-id="d58f6-154">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-154">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="d58f6-155">**百分比**</span><span class="sxs-lookup"><span data-stu-id="d58f6-155">**Percent**</span></span>  
 <span data-ttu-id="d58f6-156">指定查询将只返回结果集中的前百分之 n  的行。</span><span class="sxs-lookup"><span data-stu-id="d58f6-156">Specify that the query will return only the first *n* percent of rows in the result set.</span></span> <span data-ttu-id="d58f6-157">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-157">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
 <span data-ttu-id="d58f6-158">**With Ties**</span><span class="sxs-lookup"><span data-stu-id="d58f6-158">**With Ties**</span></span>  
 <span data-ttu-id="d58f6-159">指定视图将包括 WITH TIES 子句。</span><span class="sxs-lookup"><span data-stu-id="d58f6-159">Specify that the view will include a WITH TIES clause.</span></span> <span data-ttu-id="d58f6-160">如果视图包含 ORDER BY 子句和基于百分比的 TOP 子句，WITH TIES 将非常有用。</span><span class="sxs-lookup"><span data-stu-id="d58f6-160">WITH TIES is useful if a view includes an ORDER BY clause and a TOP clause based on percentage.</span></span> <span data-ttu-id="d58f6-161">如果设置了该选项，并且百分比截止位置在一组行的中间，且这些行在 ORDER BY 子句中具有相同的值，则视图将会扩展，以包含所有这样的行。</span><span class="sxs-lookup"><span data-stu-id="d58f6-161">If this option is set, and if the percentage cutoff falls in the middle of a set of rows with identical values in the ORDER BY clause, the view is extended to include all such rows.</span></span> <span data-ttu-id="d58f6-162">（仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 或更高版本。）</span><span class="sxs-lookup"><span data-stu-id="d58f6-162">(Applies only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58f6-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d58f6-163">See Also</span></span>  
 <span data-ttu-id="d58f6-164">[用参数查询 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d58f6-164">[Query with Parameters &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d58f6-165">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d58f6-165">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
