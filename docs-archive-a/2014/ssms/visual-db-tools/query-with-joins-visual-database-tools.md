---
title: 使用联接进行查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- View Designer, joins
- table joins [SQL Server]
- multiple table joins
- Visual Database Tools [SQL Server], queries
- Query Designer [SQL Server], joins
- joins [SQL Server], queries
ms.assetid: 8f068207-d777-4e64-8c4c-d821f0ddb450
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9d0053e6786d96508be8a87347cdc0b19975a3fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688395"
---
# <a name="query-with-joins-visual-database-tools"></a><span data-ttu-id="75970-102">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-102">Query with Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="75970-103">查询结果可包含来自多个表或表值对象的数据。</span><span class="sxs-lookup"><span data-stu-id="75970-103">A query result can include data from multiple tables or table-valued objects.</span></span> <span data-ttu-id="75970-104">若要组合来自多个表值对象的数据，可使用 SQL 的 JOIN 操作。</span><span class="sxs-lookup"><span data-stu-id="75970-104">To combine data from multiple table-valued objects, you use the JOIN operation from SQL.</span></span>  
  
 <span data-ttu-id="75970-105">有关使用多个表创建查询的信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="75970-105">For information about creating queries using multiple tables, see the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75970-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="75970-106">In This Section</span></span>  
 [<span data-ttu-id="75970-107">修改联接运算符 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-107">Modify Join Operators &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="75970-108">指定应使用等号 (=) 之外的其他运算符联接表。</span><span class="sxs-lookup"><span data-stu-id="75970-108">Specify that tables should be joined using an operator other than equal (=).</span></span>  
  
 [<span data-ttu-id="75970-109">查询和视图设计器如何表示联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-109">How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;</span></span>](how-the-query-and-view-designer-represents-joins-visual-database-tools.md)  
 <span data-ttu-id="75970-110">解释联接在“关系图”窗格中的图形表示形式。</span><span class="sxs-lookup"><span data-stu-id="75970-110">Explains the graphic representation of the join as you see it in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="75970-111">自动联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-111">Join Tables Automatically &#40;Visual Database Tools&#41;</span></span>](join-tables-automatically-visual-database-tools.md)  
 <span data-ttu-id="75970-112">介绍设置由查询和视图设计器决定是否应联接表的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-112">Steps for allowing the Query and View Designer determine if tables should be joined.</span></span>  
  
 [<span data-ttu-id="75970-113">手动联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-113">Join Tables Manually &#40;Visual Database Tools&#41;</span></span>](join-tables-manually-visual-database-tools.md)  
 <span data-ttu-id="75970-114">介绍在“关系图”窗格中手动创建联接的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-114">Steps for creating a join manually in the Diagram pane.</span></span>  
  
 [<span data-ttu-id="75970-115">在多个列上联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-115">Join Tables on Multiple Columns &#40;Visual Database Tools&#41;</span></span>](join-tables-on-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="75970-116">介绍按多个条件联接多个表的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-116">Steps for joining tables with multiple criteria for each table.</span></span>  
  
 [<span data-ttu-id="75970-117">创建外部联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-117">Create Outer Joins &#40;Visual Database Tools&#41;</span></span>](create-outer-joins-visual-database-tools.md)  
 <span data-ttu-id="75970-118">指定即使某些行与相应表中的行不匹配，联接表也应包含这些行。</span><span class="sxs-lookup"><span data-stu-id="75970-118">Specify that joined tables should include rows even when they do not match rows in the corresponding table.</span></span>  
  
 [<span data-ttu-id="75970-119">删除联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-119">Remove Joins &#40;Visual Database Tools&#41;</span></span>](remove-joins-visual-database-tools.md)  
 <span data-ttu-id="75970-120">介绍移除表之间的联接的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-120">Steps for removing a join between tables.</span></span>  
  
 [<span data-ttu-id="75970-121">自动创建自联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-121">Create Self-Joins Automatically &#40;Visual Database Tools&#41;</span></span>](create-self-joins-automatically-visual-database-tools.md)  
 <span data-ttu-id="75970-122">介绍设置由查询和视图设计器创建自联接的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-122">Steps for allowing the Query and View Designer to create a self-join.</span></span>  
  
 [<span data-ttu-id="75970-123">手动创建自联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-123">Create Self-Joins Manually &#40;Visual Database Tools&#41;</span></span>](create-self-joins-manually-visual-database-tools.md)  
 <span data-ttu-id="75970-124">介绍使用联接在单个表中查找数据子集的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-124">Steps for using a join to find subsets of data within a single table.</span></span>  
  
 [<span data-ttu-id="75970-125">查看联接属性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-125">View Join Properties &#40;Visual Database Tools&#41;</span></span>](view-join-properties-visual-database-tools.md)  
 <span data-ttu-id="75970-126">介绍查看联接的属性的步骤。</span><span class="sxs-lookup"><span data-stu-id="75970-126">Steps for viewing the properties of a join.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75970-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="75970-127">Related Sections</span></span>  
 [<span data-ttu-id="75970-128">查询类型 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-128">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="75970-129">提供指向介绍所支持查询类型的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="75970-129">Provides links to topics describing the supported query types.</span></span>  
  
 [<span data-ttu-id="75970-130">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="75970-131">提供指向介绍最常见查询任务的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="75970-131">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="75970-132">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="75970-132">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
 <span data-ttu-id="75970-133">提供指向介绍各种搜索条件以及如何使用这些搜索条件的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="75970-133">Provides links to topics covering the various kinds of search criteria and how to use them.</span></span>  
  
  
