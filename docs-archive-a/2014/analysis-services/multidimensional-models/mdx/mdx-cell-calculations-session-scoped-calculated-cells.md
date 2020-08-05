---
title: 创建会话作用域的计算单元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 199de07778a153cd1bc40b5033d364e5e0055bd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580933"
---
# <a name="creating-session-scoped-calculated-cells"></a><span data-ttu-id="da096-102">创建会话作用域的计算单元</span><span class="sxs-lookup"><span data-stu-id="da096-102">Creating Session-Scoped Calculated Cells</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="da096-103">已不推荐使用此语法。</span><span class="sxs-lookup"><span data-stu-id="da096-103">This syntax has been deprecated.</span></span> <span data-ttu-id="da096-104">应当改用 MDX 赋值。</span><span class="sxs-lookup"><span data-stu-id="da096-104">You should use MDX assignments should instead.</span></span> <span data-ttu-id="da096-105">有关分配的详细信息，请参阅[基本 MDX 脚本 (MDX)](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="da096-105">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="da096-106">若要创建适用于同一会话中的所有查询的计算单元，请使用 [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) 语句或 [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) 语句。</span><span class="sxs-lookup"><span data-stu-id="da096-106">To create calculated cells that are available to all queries in the same session, you can use either the [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) statement or the [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) statement.</span></span> <span data-ttu-id="da096-107">这两个语句的结果相同。</span><span class="sxs-lookup"><span data-stu-id="da096-107">Both statements have the same result.</span></span>  
  
## <a name="create-cell-calculation-syntax"></a><span data-ttu-id="da096-108">CREATE CELL CALCULATION 语法</span><span class="sxs-lookup"><span data-stu-id="da096-108">CREATE CELL CALCULATION Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="da096-109">已不推荐使用此语法。</span><span class="sxs-lookup"><span data-stu-id="da096-109">This syntax has been deprecated.</span></span> <span data-ttu-id="da096-110">应当改用 MDX 赋值。</span><span class="sxs-lookup"><span data-stu-id="da096-110">You should use MDX assignments should instead.</span></span> <span data-ttu-id="da096-111">有关分配的详细信息，请参阅[基本 MDX 脚本 (MDX)](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="da096-111">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="da096-112">按照以下语法使用 CREATE CELL CALCULATION 语句定义会话作用域的计算单元：</span><span class="sxs-lookup"><span data-stu-id="da096-112">Use the following syntax to use the CREATE CELL CALCULATION statement to define a session-scoped calculated cell:</span></span>  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a><span data-ttu-id="da096-113">ALTER CUBE 语法</span><span class="sxs-lookup"><span data-stu-id="da096-113">ALTER CUBE Syntax</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="da096-114">已不推荐使用此语法。</span><span class="sxs-lookup"><span data-stu-id="da096-114">This syntax has been deprecated.</span></span> <span data-ttu-id="da096-115">应当改用 MDX 赋值。</span><span class="sxs-lookup"><span data-stu-id="da096-115">You should use MDX assignments should instead.</span></span> <span data-ttu-id="da096-116">有关分配的详细信息，请参阅[基本 MDX 脚本 (MDX)](the-basic-mdx-script-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="da096-116">For more information on assignments, see [The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md).</span></span>  
  
 <span data-ttu-id="da096-117">按照以下语法使用 ALTER CUBE 语句定义会话作用域的计算单元：</span><span class="sxs-lookup"><span data-stu-id="da096-117">Use the following syntax to use the ALTER CUBE statement to define a session-scoped calculated cell:</span></span>  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 <span data-ttu-id="da096-118">`String_Expression` 值包含一个正交、单维度 MDX 集表达式列表，每个表达式都必须解析为下表列出的集类别之一。</span><span class="sxs-lookup"><span data-stu-id="da096-118">The `String_Expression` value contains a list of orthogonal, single-dimensional MDX set expressions, each of which must resolve to one of the categories of sets that are listed in the following table.</span></span>  
  
|<span data-ttu-id="da096-119">类别</span><span class="sxs-lookup"><span data-stu-id="da096-119">Category</span></span>|<span data-ttu-id="da096-120">说明</span><span class="sxs-lookup"><span data-stu-id="da096-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="da096-121">空集</span><span class="sxs-lookup"><span data-stu-id="da096-121">Empty set</span></span>|<span data-ttu-id="da096-122">解析为空集的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="da096-122">An MDX set expression that resolves into an empty set.</span></span> <span data-ttu-id="da096-123">在这种情况下，计算单元的作用域是整个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="da096-123">In this case, the scope of the calculated cell is the whole cube.</span></span>|  
|<span data-ttu-id="da096-124">单个成员集</span><span class="sxs-lookup"><span data-stu-id="da096-124">Single member set</span></span>|<span data-ttu-id="da096-125">解析为单个成员的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="da096-125">An MDX set expression that resolves into a single member.</span></span>|  
|<span data-ttu-id="da096-126">级别成员集</span><span class="sxs-lookup"><span data-stu-id="da096-126">Set of level members</span></span>|<span data-ttu-id="da096-127">解析为单个级别的成员的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="da096-127">An MDX set expression that resolves into the members of a single level.</span></span> <span data-ttu-id="da096-128">*Level_Expression*就是其中的一个示例。`Members`</span><span class="sxs-lookup"><span data-stu-id="da096-128">An example of this is the *Level_Expression*.`Members`</span></span> <span data-ttu-id="da096-129">MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="da096-129">MDX function.</span></span> <span data-ttu-id="da096-130">若要包括计算成员，请使用*Level_Expression*。`AllMembers`</span><span class="sxs-lookup"><span data-stu-id="da096-130">To include calculated members, use the *Level_Expression*.`AllMembers`</span></span> <span data-ttu-id="da096-131">MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="da096-131">MDX function.</span></span><br /><br /> <span data-ttu-id="da096-132">有关详细信息，请参阅 [AllMembers (MDX)](/sql/mdx/allmembers-mdx)。</span><span class="sxs-lookup"><span data-stu-id="da096-132">For more information, see [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).</span></span>|  
|<span data-ttu-id="da096-133">后代集</span><span class="sxs-lookup"><span data-stu-id="da096-133">Set of descendants</span></span>|<span data-ttu-id="da096-134">解析为指定成员的后代的 MDX 集表达式。</span><span class="sxs-lookup"><span data-stu-id="da096-134">An MDX set expression that resolves into the descendants of a specified member.</span></span> <span data-ttu-id="da096-135">例如， `Descendants` (*Member_Expression*， *Level_Expression* *Desc_Flag*) MDX 函数。</span><span class="sxs-lookup"><span data-stu-id="da096-135">An example of this is the `Descendants`(*Member_Expression*, *Level_Expression*, *Desc_Flag*) MDX function.</span></span><br /><br /> <span data-ttu-id="da096-136">有关详细信息，请参阅 [Descendants (MDX)](/sql/mdx/descendants-mdx)。</span><span class="sxs-lookup"><span data-stu-id="da096-136">For more information, see [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da096-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da096-137">See Also</span></span>  
 [<span data-ttu-id="da096-138">在 MDX 中生成单元格计算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="da096-138">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
