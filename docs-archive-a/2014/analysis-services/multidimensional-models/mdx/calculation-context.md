---
title: 计算上下文 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aec8aa98-b77d-4f8f-9684-2618b1d8e970
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6d14df51c6ec37fb96520af7acf207227ae4ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690180"
---
# <a name="calculation-context"></a><span data-ttu-id="202c6-102">计算上下文</span><span class="sxs-lookup"><span data-stu-id="202c6-102">Calculation Context</span></span>
  <span data-ttu-id="202c6-103">计算上下文是多维数据集的已知子空间，在其中，将对表达式进行计算，并且所有坐标或者是显式已知的，或者可以从表达式派生。</span><span class="sxs-lookup"><span data-stu-id="202c6-103">The calculation context is the known subspace of the cube where an expression is evaluated and all coordinates are either explicitly known or can be derived from the expression.</span></span>  
  
## <a name="determining-the-calculation-context"></a><span data-ttu-id="202c6-104">确定计算上下文</span><span class="sxs-lookup"><span data-stu-id="202c6-104">Determining the calculation context</span></span>  
 <span data-ttu-id="202c6-105">每个集、成员、元组或数值函数均在整个 MDX 表达式或语句的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="202c6-105">Every set, member, tuple, or numeric function executes in the context of the entire MDX expression or statement.</span></span> <span data-ttu-id="202c6-106">当参数（例如元组）传递到函数时，仅显式提供多维数据集空间中的若干个坐标。</span><span class="sxs-lookup"><span data-stu-id="202c6-106">When an argument, such as a tuple, is passed to a function, only some of the coordinates in the cube space are explicitly provided.</span></span> <span data-ttu-id="202c6-107">其他坐标根据当前计算上下文来获取。</span><span class="sxs-lookup"><span data-stu-id="202c6-107">The other coordinates are obtained based on the current calculation context.</span></span>  
  
 <span data-ttu-id="202c6-108">按照以下顺序确定未指定的单元坐标和属性成员的计算上下文：</span><span class="sxs-lookup"><span data-stu-id="202c6-108">The calculation context for unspecified cell coordinates and attribute members is determined in the following order:</span></span>  
  
1.  <span data-ttu-id="202c6-109">FROM 子句（如果适用）- 此子句可指定整个多维数据集，或以 SELECT 语句的形式指定子多维数据集。</span><span class="sxs-lookup"><span data-stu-id="202c6-109">The FROM clause (if applicable) - this clause can either specify an entire cube or can specify a subcube in the form of a SELECT statement.</span></span>  
  
2.  <span data-ttu-id="202c6-110">WHERE 子句（如果适用）- 此子句也称为“切片器轴”\*\*，可在其上指定集、元组或成员以限制查询在列轴或行轴上返回成员。</span><span class="sxs-lookup"><span data-stu-id="202c6-110">The WHERE clause (if applicable) - this clause, which is also known as the *slicer axis*, on which you specify a set, tuple, or member that restricts the members returned on the column and row axis by a query.</span></span> <span data-ttu-id="202c6-111">从概念上来说，未在列轴或行轴上显式指定的每个属性层次结构的默认成员均是切片器轴的一部分。</span><span class="sxs-lookup"><span data-stu-id="202c6-111">Conceptually, the default member of every attribute hierarchy that is not explicitly specified on column or row axis is part of the slicer axis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="202c6-112">在切片器轴和其他轴上指定特定属性的单元坐标时，函数中指定的坐标可能优先确定轴上的集的成员。</span><span class="sxs-lookup"><span data-stu-id="202c6-112">When cell coordinates for a particular attribute are specified on both the slicer axis and on another axis, the coordinates specified in the function may take precedence in determining the members of the set on the axis.</span></span> <span data-ttu-id="202c6-113">[Filter (MDX)](/sql/mdx/filter-mdx) 和 [Order (MDX)](/sql/mdx/order-mdx) 函数是这类函数的示例 - 你可以按属性成员（通过 WHERE 子句或 FROM 子句中的 SELECT 语句排除在计算上下文之外）对结果进行筛选或排序。</span><span class="sxs-lookup"><span data-stu-id="202c6-113">The [Filter (MDX)](/sql/mdx/filter-mdx) and [Order (MDX)](/sql/mdx/order-mdx) functions are examples of such functions - you can filter or order a result by attribute members that are excluded from the calculation context by the WHERE clause, or by a SELECT statement in the FROM clause.</span></span>  
  
3.  <span data-ttu-id="202c6-114">在查询或表达式中定义的命名集和计算成员。</span><span class="sxs-lookup"><span data-stu-id="202c6-114">The named sets and calculated members defined in the query or expression.</span></span>  
  
4.  <span data-ttu-id="202c6-115">在行轴和列轴上指定的元组和集，对没有显示在行轴、列轴或切片器轴上的属性使用默认成员。</span><span class="sxs-lookup"><span data-stu-id="202c6-115">The tuples and sets specified on the row and column axes, utilizing the default member for attributes that do not appear on the row, column, or slicer axis.</span></span>  
  
5.  <span data-ttu-id="202c6-116">每个轴上的多维数据集或子多维数据集，消除了轴上的空元组并应用 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="202c6-116">The cube or subcube cells on each axis, eliminating empty tuples on the axis and applying the HAVING clause.</span></span>  
  
6.  <span data-ttu-id="202c6-117">有关详细信息，请参阅 [在查询中建立多维数据集上下文 (MDX)](establishing-cube-context-in-a-query-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="202c6-117">For more information, see [Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md).</span></span>  
  
 <span data-ttu-id="202c6-118">在以下查询中，由 WHERE 子句中指定的 Country 属性成员和 Calendar Year 属性成员限制行轴的计算上下文。</span><span class="sxs-lookup"><span data-stu-id="202c6-118">In the following query, the calculation context for the row axis is restricted by the Country attribute member and the Calendar Year attribute member that are specified in the WHERE clause.</span></span>  
  
```  
SELECT Customer.City.City.Members ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France, [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="202c6-119">如果通过在行轴上指定 `FILTER` 函数修改此查询，并在 `FILTER` 函数中使用 Calendar Year 属性层次结构成员，则可以修改 Calendar Year 属性层次结构中的属性成员（用于为列轴上的集的成员提供计算上下文）。</span><span class="sxs-lookup"><span data-stu-id="202c6-119">However, if you modify this query by specifying the `FILTER` function on the row axis, and utilize a Calendar Year attribute hierarchy member in the `FILTER` function, then the attribute member from the Calendar Year attribute hierarchy that is used to provide the calculation context for the members of the set on the column axis can be modified.</span></span>  
  
```  
SELECT FILTER  
   (  
      Customer.City.City.Members,   
         ([Date].[Calendar].[Calendar Year].[CY 2003],  
            Measures.[Internet Order Quantity]) > 75   
   ) ON 0  
FROM [Adventure Works]  
WHERE (Customer.Country.France,  
   [Date].[Calendar].[Calendar Year].[CY 2004],  
   Measures.[Internet Sales Amount])  
```  
  
 <span data-ttu-id="202c6-120">在前面的查询中，由 Calendar Year 属性层次结构的 CY 2003 成员筛选列轴上所显示元组的单元的计算上下文，即便 Calendar Year 属性层次结构名义上的计算上下文为 CY 2004 也是如此。</span><span class="sxs-lookup"><span data-stu-id="202c6-120">In the previous query, the calculation context for the cells in the tuples that appear on the column axis is filtered by the CY 2003 member of the Calendar Year attribute hierarchy, even though the nominal calculation context for the Calendar Year attribute hierarchy is CY 2004.</span></span> <span data-ttu-id="202c6-121">另外，它由 Internet Order Quantity 度量值筛选。</span><span class="sxs-lookup"><span data-stu-id="202c6-121">Furthermore, it is filtered by the Internet Order Quantity measure.</span></span> <span data-ttu-id="202c6-122">不过，只要设置了列轴上的集成员，就将再次由 WHERE 子句确定显示在该轴上的成员值的计算上下文。</span><span class="sxs-lookup"><span data-stu-id="202c6-122">However, once the members of the set on the column axis is set, the calculation context for the values for the members that appear on the axis is again determined by the WHERE clause.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="202c6-123">若要提高查询性能，应在解析过程中尽早地消除成员和元组。</span><span class="sxs-lookup"><span data-stu-id="202c6-123">To increase query performance, you should eliminate members and tuples as early in the resolution process as possible.</span></span> <span data-ttu-id="202c6-124">通过这种方式，针对最终成员集的复杂查询时间计算涉及的单元最少。</span><span class="sxs-lookup"><span data-stu-id="202c6-124">In this manner, complex query time calculations on the final set of members operate on the fewest cells possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202c6-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="202c6-125">See Also</span></span>  
 <span data-ttu-id="202c6-126">[在查询 &#40;MDX&#41;中建立多维数据集上下文](establishing-cube-context-in-a-query-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="202c6-126">[Establishing Cube Context in a Query &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md) </span></span>  
 <span data-ttu-id="202c6-127">[MDX 查询基础知识 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="202c6-127">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="202c6-128">MDX 中的重要概念 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="202c6-128">Key Concepts in MDX &#40;Analysis Services&#41;</span></span>](../key-concepts-in-mdx-analysis-services.md)  
  
  
