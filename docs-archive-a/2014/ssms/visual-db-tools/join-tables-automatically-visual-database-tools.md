---
title: 自动联接表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: d05100f801d972759c1b5c105814f5cdbdccf84f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682590"
---
# <a name="join-tables-automatically-visual-database-tools"></a><span data-ttu-id="c2935-102">自动联接表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c2935-102">Join Tables Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="c2935-103">将两个或多个表添加到查询中时， [查询和视图设计器](visual-database-tools.md) 会尝试确定它们是否相关。</span><span class="sxs-lookup"><span data-stu-id="c2935-103">When you add two or more tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to determine if they are related.</span></span> <span data-ttu-id="c2935-104">如果相关，查询和视图设计器将自动在表示表或表结构对象的矩形之间添加联接线。</span><span class="sxs-lookup"><span data-stu-id="c2935-104">If they are, the Query and View Designer automatically puts join lines between the rectangles representing the tables or table-structured objects.</span></span>  
  
 <span data-ttu-id="c2935-105">如果满足以下条件，查询和视图设计器就会将表识别为联接的表：</span><span class="sxs-lookup"><span data-stu-id="c2935-105">The Query and View Designer will recognize tables as joined if:</span></span>  
  
-   <span data-ttu-id="c2935-106">数据库包含指定这些表相关的信息。</span><span class="sxs-lookup"><span data-stu-id="c2935-106">The database contains information that specifies that the tables are related.</span></span>  
  
-   <span data-ttu-id="c2935-107">如果两个表各有一列具有相同的名称和数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2935-107">If two columns, one in each table, have the same name and data type.</span></span> <span data-ttu-id="c2935-108">该列必须至少在一个表中是主键。</span><span class="sxs-lookup"><span data-stu-id="c2935-108">The column must be a primary key in at least one of the tables.</span></span> <span data-ttu-id="c2935-109">例如，假设添加 `employee` 和 `jobs` 表，如果 `job_id` 列是 `jobs` 表的主键，并且两个表中都有一个名为 `job_id` 的列，且具有相同的数据类型，那么查询和视图设计器将自动联接这两个表。</span><span class="sxs-lookup"><span data-stu-id="c2935-109">For example, if you add `employee` and `jobs` tables, if the `job_id` column is the primary key in the `jobs` table, and if each table has a column called `job_id` with the same data type, the Query and View Designer will automatically join the tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c2935-110">查询和视图设计器根据具有相同名称和数据类型的列只能创建一个联接。</span><span class="sxs-lookup"><span data-stu-id="c2935-110">The Query and View Designer will create only one join based on columns with the same name and data type.</span></span> <span data-ttu-id="c2935-111">如果有多种联接可能，查询和视图设计器在根据所找到的第一组匹配列创建一个联接后即会停止。</span><span class="sxs-lookup"><span data-stu-id="c2935-111">If more than one join is possible, the Query and View Designer stops after creating a join based on the first set of matching columns that it finds.</span></span>  
  
-   <span data-ttu-id="c2935-112">查询和视图设计器可以检测到搜索条件（WHERE 子句）实际上是否为联接条件。</span><span class="sxs-lookup"><span data-stu-id="c2935-112">The Query and View Designer detects that a search condition (a WHERE clause) is actually a join condition.</span></span> <span data-ttu-id="c2935-113">例如，假设您添加表 `employee` 和 `jobs`，再创建一个搜索条件，搜索这两个表的 `job_id` 列中的相同值。</span><span class="sxs-lookup"><span data-stu-id="c2935-113">For example, you might add the tables `employee` and `jobs`, then create a search condition that searches for the same value in the `job_id` column of both tables.</span></span> <span data-ttu-id="c2935-114">当执行搜索时，查询和视图设计器可检测到该搜索条件会导致联接，就会根据该搜索条件创建联接条件。</span><span class="sxs-lookup"><span data-stu-id="c2935-114">When you do, the Query and View Designer detects that the search condition results in a join, and then creates a join condition based on the search condition.</span></span>  
  
 <span data-ttu-id="c2935-115">如果查询和视图设计器创建了一个不适合于您的查询的联接，您可以修改或移除该联接。</span><span class="sxs-lookup"><span data-stu-id="c2935-115">If the Query and View Designer has created a join that is not suitable to your query, you can modify the join or remove it.</span></span> <span data-ttu-id="c2935-116">有关详细信息，请参阅[修改联接运算符 (Visual Database Tools)](modify-join-operators-visual-database-tools.md) 和[删除联接 (Visual Database Tools)](remove-joins-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c2935-116">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) and [Remove Joins &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="c2935-117">如果查询和视图设计器在查询中没有自动联接表，您可以自己创建联接。</span><span class="sxs-lookup"><span data-stu-id="c2935-117">If the Query and View Designer does not automatically join the tables in your query, you can create a join yourself.</span></span> <span data-ttu-id="c2935-118">有关详细信息，请参阅[手动联接表 (Visual Database Tools)](join-tables-manually-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c2935-118">For details, see [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2935-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2935-119">See Also</span></span>  
 <span data-ttu-id="c2935-120">[查询和视图设计器如何表示 &#40;Visual Database Tools 的联接&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c2935-120">[How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="c2935-121">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c2935-121">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c2935-122">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c2935-122">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
