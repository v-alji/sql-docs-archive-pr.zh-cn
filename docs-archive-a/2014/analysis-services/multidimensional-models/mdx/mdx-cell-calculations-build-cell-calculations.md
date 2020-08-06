---
title: 在 MDX 中生成单元计算 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ab3219850c49c2ec16a12aab3ba7db67e9a8721
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690823"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a><span data-ttu-id="b0ffe-102">在 MDX 中生成单元计算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b0ffe-102">Building Cell Calculations in MDX (MDX)</span></span>
  <span data-ttu-id="b0ffe-103">多维表达式 (MDX) 提供许多用于生成计算值（如计算成员、自定义汇总以及自定义成员）的工具。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-103">Multidimensional Expressions (MDX) provides you with a number of tools for generating calculated values, such as calculated members, custom rollups, and custom members.</span></span> <span data-ttu-id="b0ffe-104">然而，使用这些功能很难影响一组特定的单元或单个单元。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-104">However, using these features to affect a specific set of cells, or a single cell for that matter, would be difficult.</span></span>  
  
 <span data-ttu-id="b0ffe-105">若要生成专门用于单元的计算值，需要使用 MDX 中的计算单元功能。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-105">To generated calculated values for specifically for cells, you need to use the calculated cells feature in MDX.</span></span> <span data-ttu-id="b0ffe-106">计算单元允许您定义单元的特定部分（称为“计算子多维数据集” \*\*），并根据可应用于每个单元的可选条件将某个公式应用于该计算子多维数据集内的各个单元。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-106">Calculated cells let you define a specific slice of cells, called a *calculation subcube*, and apply a formula to each and every cell within the calculation subcube, subject to an optional condition that can be applied to each cell.</span></span>  
  
 <span data-ttu-id="b0ffe-107">计算单元还提供了复杂的功能，如目标查找公式（如 KPI 中所使用的）或推测分析公式。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-107">Calculated cells also offer complex functionality, such as goal-seeking formulas, as used in KPIs, or speculative analysis formulas.</span></span> <span data-ttu-id="b0ffe-108">此级别的功能来自中的 "传递顺序" 功能，通过该功能，可以通过 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 计算单元进行递归传递，并按传递顺序将计算公式应用于特定阶段。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-108">This level of functionality comes from the pass order feature in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that allows recursive passes to be made with calculated cells, with calculation formulas applied at specific passes in the pass order.</span></span> <span data-ttu-id="b0ffe-109">有关传递次序的详细信息，请参阅[理解传递次序和求解次序 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-109">For more information on pass order, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="b0ffe-110">就创建作用域而言，计算单元类似于命名集和计算成员，因为可以为会话或单个查询的生存期临时创建计算单元，或将计算单元作为多维数据集的一部分在全局作用域内使用：</span><span class="sxs-lookup"><span data-stu-id="b0ffe-110">In terms of creation scope, calculated cells are similar to both named sets and calculated members in that calculated cells can be temporarily created for the lifetime of either a session or a single query, or made globally available as part of a cube:</span></span>  
  
-   <span data-ttu-id="b0ffe-111">**查询作用域：** 若要创建定义为 MDX 查询的一部分的计算单元（计算单元的作用域因此局限于该查询），请使用 WITH 关键字。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-111">**Query-scoped** To create a calculated cell that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="b0ffe-112">然后可以在 MDX SELECT 语句中使用该计算单元。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-112">You can then use the calculated cell within an MDX SELECT statement.</span></span> <span data-ttu-id="b0ffe-113">使用这种方法，可以更改使用 `WITH` 关键字创建的计算单元，而不会打乱 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-113">Using this approach, the calculated cell created by using the `WITH` keyword can be changed without disturbing the SELECT statement.</span></span>  
  
     <span data-ttu-id="b0ffe-114">有关如何使用 WITH 关键字创建计算成员的详细信息，请参阅 [创建查询作用域的单元计算 (MDX)](../../multidimensional-models-olap-logical-cube-objects/calculations.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-114">For more information about how to use the WITH keyword to create calculated members, see [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
-   <span data-ttu-id="b0ffe-115">**会话作用域：** 若要创建作用域比查询的上下文更广（也就是说，其作用域是 MDX 会话的生存期）的计算成员，请使用 CREATE CELL CALCULATION 或 ALTER CUBE 语句。</span><span class="sxs-lookup"><span data-stu-id="b0ffe-115">**Session-scoped** To create a calculated member whose scope is wider than the context of the query, that is, whose scope is the lifetime of the MDX session, you use either the CREATE CELL CALCULATION or ALTER CUBE statement.</span></span>  
  
     <span data-ttu-id="b0ffe-116">有关如何使用 CREATE CELL CALCULATION 或 ALTER CUBE 语句在会话中创建计算单元的详细信息，请参阅 [创建会话作用域的计算单元](mdx-cell-calculations-session-scoped-calculated-cells.md)</span><span class="sxs-lookup"><span data-stu-id="b0ffe-116">For more information about how to use either the CREATE CELL CALCULATION or ALTER CUBE statement to create calculated cells in a session, see [Creating Session-Scoped Calculated Cells](mdx-cell-calculations-session-scoped-calculated-cells.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ffe-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0ffe-117">See Also</span></span>  
 <span data-ttu-id="b0ffe-118">[ALTER CUBE 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span><span class="sxs-lookup"><span data-stu-id="b0ffe-118">[ALTER CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube) </span></span>  
 <span data-ttu-id="b0ffe-119">[&#40;MDX 创建单元计算语句&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span><span class="sxs-lookup"><span data-stu-id="b0ffe-119">[CREATE CELL CALCULATION Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation) </span></span>  
 <span data-ttu-id="b0ffe-120">[&#40;MDX&#41;创建查询作用域的单元计算](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span><span class="sxs-lookup"><span data-stu-id="b0ffe-120">[Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md) </span></span>  
 [<span data-ttu-id="b0ffe-121">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b0ffe-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
