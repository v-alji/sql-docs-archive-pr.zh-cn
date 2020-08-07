---
title: " (MDX) 指定查询轴的内容 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cellsets [MDX]
- query axis [MDX]
ms.assetid: c745ade0-738e-4a98-a3f0-3eabfd3eeba2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 28fd867b8f8caaf74e4dd704753c354368da2e89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690819"
---
# <a name="specifying-the-contents-of-a-query-axis-mdx"></a><span data-ttu-id="8214b-102">指定查询轴的内容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8214b-102">Specifying the Contents of a Query Axis (MDX)</span></span>
  <span data-ttu-id="8214b-103">查询轴用于指定多维表达式 (MDX) SELECT 语句返回的单元集的范围。</span><span class="sxs-lookup"><span data-stu-id="8214b-103">Query axes specify the edges of a cellset returned by a Multidimensional Expressions (MDX) SELECT statement.</span></span> <span data-ttu-id="8214b-104">通过指定单元集的范围可以限定客户端可以看到的返回数据。</span><span class="sxs-lookup"><span data-stu-id="8214b-104">Specifying the edges of a cellset lets you restrict the returned data that is visible to the client.</span></span>  
  
 <span data-ttu-id="8214b-105">若要指定查询轴，请使用 `<SELECT query axis clause>` 将某个集分配给特定的查询轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-105">To specify query axes, you use the `<SELECT query axis clause>` to assign a set to a particular query axis.</span></span> <span data-ttu-id="8214b-106">每个 `<SELECT query axis clause>` 值均定义一个查询轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-106">Each `<SELECT query axis clause>` value defines one query axis.</span></span> <span data-ttu-id="8214b-107">数据集中的轴数等于 SELECT 语句中 `<SELECT query axis clause>` 值的数目。</span><span class="sxs-lookup"><span data-stu-id="8214b-107">The number of axes in the dataset is equal to the number of `<SELECT query axis clause>` values in the SELECT statement.</span></span>  
  
## <a name="query-axis-syntax"></a><span data-ttu-id="8214b-108">查询轴的语法</span><span class="sxs-lookup"><span data-stu-id="8214b-108">Query Axis Syntax</span></span>  
 <span data-ttu-id="8214b-109">以下语法显示了 `<SELECT query axis clause>`的语法：</span><span class="sxs-lookup"><span data-stu-id="8214b-109">The following syntax shows the syntax for the `<SELECT query axis clause>`:</span></span>  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 <span data-ttu-id="8214b-110">每个查询轴具有一个编号：零 (0) 表示 x 轴，1 表示 y 轴，2 表示 z 轴，依此类推。</span><span class="sxs-lookup"><span data-stu-id="8214b-110">Each query axis has a number: zero (0) for the x-axis, 1 for the y-axis, 2 for the z-axis, and so on.</span></span> <span data-ttu-id="8214b-111">在 `<SELECT query axis clause>`的语法中， `Integer_Expression` 值指定了轴编号。</span><span class="sxs-lookup"><span data-stu-id="8214b-111">In the syntax for the `<SELECT query axis clause>`, the `Integer_Expression` value specifies the axis number.</span></span> <span data-ttu-id="8214b-112">MDX 查询最多可以指定 128 个轴，但几乎没有 MDX 查询会用到 5 个以上的轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-112">An MDX query can support up to 128 specified axes, but very few MDX queries will use more than 5 axes.</span></span> <span data-ttu-id="8214b-113">对于前 5 个轴，也可以改为使用 COLUMNS、ROWS、PAGES、SECTIONS 和 CHAPTERS 别名。</span><span class="sxs-lookup"><span data-stu-id="8214b-113">For the first 5 axes, the aliases COLUMNS, ROWS, PAGES, SECTIONS, and CHAPTERS can instead be used.</span></span>  
  
 <span data-ttu-id="8214b-114">MDX 查询无法跳过查询轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-114">An MDX query cannot skip query axes.</span></span> <span data-ttu-id="8214b-115">也就是说，包括一个或多个查询轴的查询不能排除编号较低的轴或中间轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-115">That is, a query that includes one or more query axes must not exclude lower-numbered or intermediate axes.</span></span> <span data-ttu-id="8214b-116">例如，查询不能有 ROWS 轴而无 COLUMNS 轴，或有 COLUMNS 和 PAGES 轴而无 ROWS 轴。</span><span class="sxs-lookup"><span data-stu-id="8214b-116">For example, a query cannot have a ROWS axis without a COLUMNS axis, or have COLUMNS and PAGES axes without a ROWS axis.</span></span>  
  
 <span data-ttu-id="8214b-117">但是，可以指定不带任何轴的 SELECT 子句，即，空的 SELECT 子句。</span><span class="sxs-lookup"><span data-stu-id="8214b-117">However, you can specify a SELECT clause without any axes (that is, an empty SELECT clause).</span></span> <span data-ttu-id="8214b-118">在这种情况下，所有维度均为切片器维度，并且 MDX 查询选择一个单元。</span><span class="sxs-lookup"><span data-stu-id="8214b-118">In this case, all dimensions are slicer dimensions, and the MDX query selects one cell.</span></span>  
  
 <span data-ttu-id="8214b-119">在前面所示的查询轴语法中，每个 `Set_Expression` 值均指定用于定义查询轴内容的集。</span><span class="sxs-lookup"><span data-stu-id="8214b-119">In the query axis syntax previously shown, each `Set_Expression` value specifies the set that defines the contents of the query axis.</span></span> <span data-ttu-id="8214b-120">有关集的详细信息，请参阅[使用成员、元组和集 (MDX)](working-with-members-tuples-and-sets-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="8214b-120">For more information about sets, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8214b-121">示例</span><span class="sxs-lookup"><span data-stu-id="8214b-121">Examples</span></span>  
 <span data-ttu-id="8214b-122">下面的简单 SELECT 语句针对 Columns 轴返回度量值 Internet Sales Amount，并使用 MDX MEMBERS 函数返回 Rows 轴的 Date 维度上的 Calendar 层次结构中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="8214b-122">The following simple SELECT statement returns the measure Internet Sales Amount on the Columns axis, and uses the MDX MEMBERS function to return all the members from the Calendar hierarchy on the Date dimension on the Rows axis:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="8214b-123">下面的两个查询返回完全相同的结果，但说明的是使用轴编号而不是别名：</span><span class="sxs-lookup"><span data-stu-id="8214b-123">The two following queries return exactly the same results but demonstrate the use of axis numbers rather than aliases:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="8214b-124">在集定义前面使用的 NON EMPTY 关键字提供了一种简便方法，从轴中删除所有空元组。</span><span class="sxs-lookup"><span data-stu-id="8214b-124">The NON EMPTY keyword, used before the set definition, is an easy way to remove all empty tuples from an axis.</span></span> <span data-ttu-id="8214b-125">例如，在我们已看到的示例中，到目前为止，多维数据集中没有从8月2004开始的数据。</span><span class="sxs-lookup"><span data-stu-id="8214b-125">For example, in the examples we've seen so far there is no data in the cube from August 2004 onwards.</span></span> <span data-ttu-id="8214b-126">要从单元集中删除列中没有数据的所有行，只需在 Rows 轴定义中的集前面添加 NON EMPTY 即可，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8214b-126">To remove all rows from the cellset that have no data in any column, simply add NON EMPTY before the set on the Rows axis definition as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 <span data-ttu-id="8214b-127">可以在查询中的所有轴上使用 NON EMPTY。</span><span class="sxs-lookup"><span data-stu-id="8214b-127">NON EMPTY can be used on all axes in a query.</span></span> <span data-ttu-id="8214b-128">将以下两个查询的结果进行比较，第一个结果不使用 NON EMPTY，第二个结果在两个轴上都使用 NON EMPTY：</span><span class="sxs-lookup"><span data-stu-id="8214b-128">Compare the results of the following two queries, the first of which does not use NON EMPTY and the second of which does on both axes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 <span data-ttu-id="8214b-129">可以使用 HAVING 子句基于特定条件筛选某个轴的内容；它没有可获得相同结果的其他方法（如 FILTER 函数）灵活，但使用起来更简单一些。</span><span class="sxs-lookup"><span data-stu-id="8214b-129">The HAVING clause can be used to filter the contents of an axis based on a specific criteria; it is less flexible than other methods that can achieve the same results, such as the FILTER function, but it is simpler to use.</span></span> <span data-ttu-id="8214b-130">下面的示例仅返回 Internet Sales Amount 大于 $15,000 的日期：</span><span class="sxs-lookup"><span data-stu-id="8214b-130">Here is an example that returns only those dates where Internet Sales Amount is greater than $15,000:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="8214b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8214b-131">See Also</span></span>  
 [<span data-ttu-id="8214b-132">指定切片器轴的内容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8214b-132">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
