---
title: 删除联接 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576469"
---
# <a name="remove-joins-visual-database-tools"></a><span data-ttu-id="381b0-102">删除联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="381b0-102">Remove Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="381b0-103">如果您不希望表通过内部联接或外部联接进行联接，则可移除它们之间的联接。</span><span class="sxs-lookup"><span data-stu-id="381b0-103">If you do not want tables to be joined via an inner join or an outer join, you can remove the join between them.</span></span> <span data-ttu-id="381b0-104">例如，希望删除 [查询和视图设计器](visual-database-tools.md) 在两个表之间自动创建的联接。</span><span class="sxs-lookup"><span data-stu-id="381b0-104">For example, you might remove a join that the [Query and View Designer](visual-database-tools.md) has been created automatically between two tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="381b0-105">从查询中移除联接不会更改数据库中的基础关系。</span><span class="sxs-lookup"><span data-stu-id="381b0-105">Removing a join from a query does not alter the underlying relationship in the database.</span></span>  
  
 <span data-ttu-id="381b0-106">如果两个联接表都是查询的一部分，而且移除了它们之间的所有联接条件，那么生成的查询结果将变为这两个表的积，即变为 CROSS JOIN。</span><span class="sxs-lookup"><span data-stu-id="381b0-106">If two joined tables are part of your query and you remove all join conditions between them, the resulting query becomes the product of both tables - that is, it becomes a CROSS JOIN.</span></span>  
  
### <a name="to-remove-a-join"></a><span data-ttu-id="381b0-107">移除联接</span><span class="sxs-lookup"><span data-stu-id="381b0-107">To remove a join</span></span>  
  
-   <span data-ttu-id="381b0-108">在“ [关系图](diagram-pane-visual-database-tools.md)”窗格中，选择要删除的联接的联接线，再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="381b0-108">In the [Diagram pane](diagram-pane-visual-database-tools.md), select the join line for the join to remove, and then press the DELETE key.</span></span> <span data-ttu-id="381b0-109">您可一次选择并删除多个联接线。</span><span class="sxs-lookup"><span data-stu-id="381b0-109">You can select and delete multiple join lines at one time.</span></span>  
  
 <span data-ttu-id="381b0-110">查询和视图设计器将删除联接线并相应地更改 [SQL 窗格](sql-pane-visual-database-tools.md)中的语句。</span><span class="sxs-lookup"><span data-stu-id="381b0-110">The Query and View Designer removes the join line and alters the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381b0-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="381b0-111">See Also</span></span>  
 <span data-ttu-id="381b0-112">[&#40;Visual Database Tools 自动联接表&#41;](join-tables-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="381b0-112">[Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) </span></span>  
 <span data-ttu-id="381b0-113">[&#40;Visual Database Tools&#41;中手动联接表](join-tables-manually-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="381b0-113">[Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="381b0-114">使用联接进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="381b0-114">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
