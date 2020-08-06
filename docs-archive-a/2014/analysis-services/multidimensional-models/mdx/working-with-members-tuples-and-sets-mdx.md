---
title: " (MDX) 使用成员、元组和集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], tuples
- member keys [MDX]
- MDX [Analysis Services], sets
- calculated members [MDX]
- members [MDX]
- Multidimensional Expressions [Analysis Services], members
- named sets [MDX]
- Multidimensional Expressions [Analysis Services], tuples
- member functions [MDX]
- sets [MDX]
- MDX [Analysis Services], members
- member names [MDX]
- Multidimensional Expressions [Analysis Services], sets
- tuple functions
- tuples
- set functions [MDX]
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ce3bf2d5ad7df2b1cd74897b3b49c7cef97e8ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577876"
---
# <a name="working-with-members-tuples-and-sets-mdx"></a><span data-ttu-id="92b5c-102">使用成员、元组和集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="92b5c-102">Working with Members, Tuples, and Sets (MDX)</span></span>
  <span data-ttu-id="92b5c-103">MDX 提供多个可返回一个或多个成员、元组或集的函数，或对成员、元组或集进行操作的函数。</span><span class="sxs-lookup"><span data-stu-id="92b5c-103">MDX provides numerous functions that return one or more members, tuples, or sets; or that act upon a member, tuple, or set.</span></span>  
  
## <a name="member-functions"></a><span data-ttu-id="92b5c-104">成员函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-104">Member Functions</span></span>  
 <span data-ttu-id="92b5c-105">MDX 提供多个用于从其他 MDX 实体（如从维度、级别、集或元组）检索成员的函数。</span><span class="sxs-lookup"><span data-stu-id="92b5c-105">MDX provides several functions for retrieving members from other MDX entities, such as from dimensions, levels, sets, or tuples.</span></span> <span data-ttu-id="92b5c-106">例如， [FirstChild](/sql/mdx/firstchild-mdx) 函数是一个对成员进行操作的函数，该函数返回一个成员。</span><span class="sxs-lookup"><span data-stu-id="92b5c-106">For example, the [FirstChild](/sql/mdx/firstchild-mdx) function is a function that acts upon a member and returns a member.</span></span>  
  
 <span data-ttu-id="92b5c-107">若要获得时间维度的第一个子成员，可以显式标示该成员，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="92b5c-107">To obtain the first child member of the Time dimension, you can explicitly state the member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="92b5c-108">还可以使用 `FirstChild` 函数返回此成员，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="92b5c-108">You can also use the `FirstChild` function to return the same member, as in the following example.</span></span>  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="92b5c-109">有关 MDX 成员函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-109">For more information about MDX member functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="tuple-functions"></a><span data-ttu-id="92b5c-110">元组函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-110">Tuple Functions</span></span>  
 <span data-ttu-id="92b5c-111">MDX 提供多个返回元组的函数，它们可在任何接受元组的地方使用。</span><span class="sxs-lookup"><span data-stu-id="92b5c-111">MDX provides several functions that return tuples, and they can be used anywhere that a tuple is accepted.</span></span> <span data-ttu-id="92b5c-112">例如，[Item (Tuple) (MDX)](/sql/mdx/item-tuple-mdx) 函数可用于从集中提取第一个元组，当你知道某个集是由单个元组组成，并且要向需要元组的函数提供该元组时，此函数非常有用。</span><span class="sxs-lookup"><span data-stu-id="92b5c-112">For example, the [Item &#40;Tuple&#41; &#40;MDX&#41;](/sql/mdx/item-tuple-mdx) function can be used to extract the first tuple from set, which is very useful when you know that a set is composed of a single tuple and you want to supply that tuple to a function that requires a tuple.</span></span>  
  
 <span data-ttu-id="92b5c-113">下面的示例返回列轴上元组集中的第一个元组。</span><span class="sxs-lookup"><span data-stu-id="92b5c-113">The following example returns the first tuple from within the set of tuples on the column axis.</span></span>  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="92b5c-114">有关元组函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-114">For more information about tuple functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="set-functions"></a><span data-ttu-id="92b5c-115">集函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-115">Set Functions</span></span>  
 <span data-ttu-id="92b5c-116">MDX 提供多个返回集的函数。</span><span class="sxs-lookup"><span data-stu-id="92b5c-116">MDX provides several functions that return sets.</span></span> <span data-ttu-id="92b5c-117">显式键入元组并将它们括在大括号内并不是检索集的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="92b5c-117">Explicitly typing tuples and enclosing them in braces is not the only way to retrieve a set.</span></span> <span data-ttu-id="92b5c-118">有关返回集的成员函数的详细信息，请参阅 [MDX 中的重要概念 (Analysis Services)](../key-concepts-in-mdx-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-118">For more information about the members function to return a set, see [Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md).</span></span> <span data-ttu-id="92b5c-119">还有很多其他集函数。</span><span class="sxs-lookup"><span data-stu-id="92b5c-119">There are many additional set functions.</span></span>  
  
 <span data-ttu-id="92b5c-120">冒号运算符允许您使用成员的自然顺序创建集。</span><span class="sxs-lookup"><span data-stu-id="92b5c-120">The colon operator lets you use the natural order of members to create a set.</span></span> <span data-ttu-id="92b5c-121">例如，下面的示例中显示的集包含 2002 日历年第一季度到第四季度的元组。</span><span class="sxs-lookup"><span data-stu-id="92b5c-121">For example, the set shown in the following example contains tuples for the 1st through the 4th quarter of calendar year 2002.</span></span>  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="92b5c-122">如果不使用冒号运算符创建集，则可以通过指定下面示例中的元组来创建相同的成员集。</span><span class="sxs-lookup"><span data-stu-id="92b5c-122">If you do not use the colon operator to create the set, you can create the same set of members by specifying the tuples in the following example.</span></span>  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="92b5c-123">冒号运算符起到包含作用。</span><span class="sxs-lookup"><span data-stu-id="92b5c-123">The colon operator is an inclusive function.</span></span> <span data-ttu-id="92b5c-124">生成的集中包含冒号运算符两侧的成员。</span><span class="sxs-lookup"><span data-stu-id="92b5c-124">The members on both sides of the colon operator are included in the resulting set.</span></span>  
  
 <span data-ttu-id="92b5c-125">有关集函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-125">For more information about set functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="array-functions"></a><span data-ttu-id="92b5c-126">数组函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-126">Array Functions</span></span>  
 <span data-ttu-id="92b5c-127">数组函数对集进行操作并返回一个数组。</span><span class="sxs-lookup"><span data-stu-id="92b5c-127">An array function acts upon a set and returns an array.</span></span> <span data-ttu-id="92b5c-128">有关数组函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-128">For more information about array functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="hierarchy-functions"></a><span data-ttu-id="92b5c-129">层次结构函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-129">Hierarchy Functions</span></span>  
 <span data-ttu-id="92b5c-130">通过对成员、级别、层次结构或字符串进行操作，层次结构函数返回一个层次结构。</span><span class="sxs-lookup"><span data-stu-id="92b5c-130">A hierarchy function returns a hierarchy by acting upon a member, level, hierarchy, or string.</span></span> <span data-ttu-id="92b5c-131">有关层次结构函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-131">For more information about hierarchy functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="level-functions"></a><span data-ttu-id="92b5c-132">级别函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-132">Level Functions</span></span>  
 <span data-ttu-id="92b5c-133">通过对成员、级别或字符串进行操作，级别函数返回一个级别。</span><span class="sxs-lookup"><span data-stu-id="92b5c-133">A level function returns a level by acting upon a member, level, or string.</span></span> <span data-ttu-id="92b5c-134">有关级别函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-134">For more information about level functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="logical-functions"></a><span data-ttu-id="92b5c-135">逻辑函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-135">Logical Functions</span></span>  
 <span data-ttu-id="92b5c-136">逻辑函数对 MDX 表达式进行操作，返回表达式中有关元组、成员或集的信息。</span><span class="sxs-lookup"><span data-stu-id="92b5c-136">A logical function acts upon a MDX expression to return information about the tuples, members, or sets in the expression.</span></span> <span data-ttu-id="92b5c-137">例如，[IsEmpty (MDX)](/sql/mdx/isempty-mdx) 函数评估表达式是否返回了空单元值。</span><span class="sxs-lookup"><span data-stu-id="92b5c-137">For example, the [IsEmpty &#40;MDX&#41;](/sql/mdx/isempty-mdx) function evaluates whether an expression has returned an empty cell value.</span></span> <span data-ttu-id="92b5c-138">有关逻辑函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-138">For more information about logical functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="numeric-functions"></a><span data-ttu-id="92b5c-139">数值函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-139">Numeric Functions</span></span>  
 <span data-ttu-id="92b5c-140">数值函数对 MDX 表达式进行操作，返回一个标量值。</span><span class="sxs-lookup"><span data-stu-id="92b5c-140">A numeric function acts upon a MDX expression to return a scalar value.</span></span> <span data-ttu-id="92b5c-141">例如，[Aggregate (MDX)](/sql/mdx/aggregate-mdx) 函数返回一个标量值，该值由对指定集中元组的度量值聚合而得。</span><span class="sxs-lookup"><span data-stu-id="92b5c-141">For example, the [Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) function returns a scalar value calculated by aggregating measures over the tuples in a specified set.</span></span> <span data-ttu-id="92b5c-142">有关数值函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-142">For more information about numeric functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="string-functions"></a><span data-ttu-id="92b5c-143">字符串函数</span><span class="sxs-lookup"><span data-stu-id="92b5c-143">String Functions</span></span>  
 <span data-ttu-id="92b5c-144">字符串函数对 MDX 表达式进行操作，返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="92b5c-144">A string function acts upon a MDX expression to return a string.</span></span> <span data-ttu-id="92b5c-145">例如，[UniqueName (MDX)](/sql/mdx/uniquename-mdx) 函数返回一个字符串值，该字符串包含维度、层次结构、级别或成员的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="92b5c-145">For example, the [UniqueName &#40;MDX&#41;](/sql/mdx/uniquename-mdx) function returns a string value containing the unique name of a dimension, hierarchy, level, or member.</span></span> <span data-ttu-id="92b5c-146">有关字符串函数的详细信息，请参阅 [MDX 函数引用 (MDX)](/sql/mdx/mdx-function-reference-mdx)。</span><span class="sxs-lookup"><span data-stu-id="92b5c-146">For more information about string functions, see [MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b5c-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92b5c-147">See Also</span></span>  
 <span data-ttu-id="92b5c-148">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="92b5c-148">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="92b5c-149">[MDX 查询基础知识 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="92b5c-149">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="92b5c-150">MDX 函数引用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="92b5c-150">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
