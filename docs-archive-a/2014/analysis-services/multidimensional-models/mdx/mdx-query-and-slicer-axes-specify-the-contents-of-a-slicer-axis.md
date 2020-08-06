---
title: " (MDX) 指定切片器轴的内容 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- filtering data [MDX]
ms.assetid: c56b0a70-cdec-427f-990e-425290344e7d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8620c54970ea14a2ac01c85262a372d2b3db0d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687280"
---
# <a name="specifying-the-contents-of-a-slicer-axis-mdx"></a><span data-ttu-id="56d64-102">指定切片器轴的内容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="56d64-102">Specifying the Contents of a Slicer Axis (MDX)</span></span>
  <span data-ttu-id="56d64-103">切片器轴将对多维表达式 (MDX) SELECT 语句返回的数据进行筛选，限定返回的数据，从而只返回与指定成员相关的数据。</span><span class="sxs-lookup"><span data-stu-id="56d64-103">The slicer axis filters the data returned by the Multidimensional Expressions (MDX) SELECT statement, restricting the returned data so that only data intersecting with the specified members will be returned.</span></span> <span data-ttu-id="56d64-104">可以将其看成是在查询中不可见的多余的轴。</span><span class="sxs-lookup"><span data-stu-id="56d64-104">It can be thought of as an invisible extra axis in a query.</span></span> <span data-ttu-id="56d64-105">切片器轴是在 MDX 中 SELECT 语句的 WHERE 子句中定义的。</span><span class="sxs-lookup"><span data-stu-id="56d64-105">The slicer axis is defined in the WHERE clause of the SELECT statement in MDX.</span></span>  
  
## <a name="slicer-axis-syntax"></a><span data-ttu-id="56d64-106">切片器轴的语法</span><span class="sxs-lookup"><span data-stu-id="56d64-106">Slicer Axis Syntax</span></span>  
 <span data-ttu-id="56d64-107">若要显式指定切片器轴，请使用 MDX 中的 `<SELECT slicer axis clause>` ，如以下语法所述。</span><span class="sxs-lookup"><span data-stu-id="56d64-107">To explicitly specify a slicer axis, you  using the `<SELECT slicer axis clause>` in MDX, as described in the following syntax:</span></span>  
  
```  
<SELECT slicer axis clause> ::=  WHERE Set_Expression  
```  
  
 <span data-ttu-id="56d64-108">在所示的切片器轴语法中，可以向 `Set_Expression` 传递元组表达式（被视为集以便对子句求值）或集表达式。</span><span class="sxs-lookup"><span data-stu-id="56d64-108">In the slicer axis syntax shown, `Set_Expression` can take either a tuple expression, which is treated as a set for the purposes of evaluating the clause, or a set expression.</span></span> <span data-ttu-id="56d64-109">如果指定了集表达式，则 MDX 通过将结果单元聚合到集的每个元组中，尝试对该集求值。</span><span class="sxs-lookup"><span data-stu-id="56d64-109">If a set expression is specified, MDX will try to evaluate the set, aggregating the result cells in every tuple along the set.</span></span> <span data-ttu-id="56d64-110">也就是说，MDX 将尝试对集使用 [Aggregate](/sql/mdx/aggregate-mdx) 函数，用与其相关的聚合函数来聚合每个度量值。</span><span class="sxs-lookup"><span data-stu-id="56d64-110">In other words, MDX will try to use the [Aggregate](/sql/mdx/aggregate-mdx) function on the set, aggregating each measure by its associated aggregation function.</span></span> <span data-ttu-id="56d64-111">另外，如果集表达式无法表示为属性层次结构成员的叉积，则 MDX 在求值时将切片器集表达式以外的单元视为空。</span><span class="sxs-lookup"><span data-stu-id="56d64-111">Also, if the set expression cannot be expressed as a crossjoin of attribute hierarchy members, MDX treats cells that fall outside of the set expression for the slicer as null for evaluation purposes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="56d64-112">与 SQL 中的 WHERE 子句不同，MDX SELECT 语句的 WHERE 子句不从直接筛选针对查询行轴返回的内容。</span><span class="sxs-lookup"><span data-stu-id="56d64-112">Unlike the WHERE clause in SQL, the WHERE clause of an MDX SELECT statement never directly filters what is returned on the Rows axis of a query.</span></span> <span data-ttu-id="56d64-113">若要筛选查询行或列轴上显示的内容，请使用多种 MDX 函数，例如 FILTER、NONEMPTY 和 TOPCOUNT。</span><span class="sxs-lookup"><span data-stu-id="56d64-113">To filter what appears on the Rows or Columns axis of a query, you can use a variety of MDX functions, for example FILTER, NONEMPTY and TOPCOUNT.</span></span>  
  
### <a name="implicit-slicer-axis"></a><span data-ttu-id="56d64-114">隐式切片器轴</span><span class="sxs-lookup"><span data-stu-id="56d64-114">Implicit Slicer Axis</span></span>  
 <span data-ttu-id="56d64-115">如果多维数据集中某个层次结构的成员未显式包括在查询轴中，则该层次结构的默认成员隐式包括在切片器轴中。</span><span class="sxs-lookup"><span data-stu-id="56d64-115">If a member from a hierarchy within the cube is not explicitly included in a query axis, the default member from that hierarchy is implicitly included in the slicer axis.</span></span> <span data-ttu-id="56d64-116">有关默认成员的详细信息，请参阅 [定义默认成员](../attribute-properties-define-a-default-member.md)。</span><span class="sxs-lookup"><span data-stu-id="56d64-116">For more information about default members, see [Define a Default Member](../attribute-properties-define-a-default-member.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="56d64-117">示例</span><span class="sxs-lookup"><span data-stu-id="56d64-117">Examples</span></span>  
 <span data-ttu-id="56d64-118">下面的查询不包括 WHERE 子句，并返回所有日历年的 Internet Sales Amount 度量值。</span><span class="sxs-lookup"><span data-stu-id="56d64-118">The following query does not include a WHERE clause, and returns the value of the Internet Sales Amount measure for all Calendar Years:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="56d64-119">按如下方式添加 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="56d64-119">Adding a WHERE clause, as follows:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States])  
  
```  
  
 <span data-ttu-id="56d64-120">不会更改针对查询行或列返回的内容;它将更改针对每个单元返回的值。</span><span class="sxs-lookup"><span data-stu-id="56d64-120">does not change what is returned on Rows or Columns in the query; it changes the values returned for each cell.</span></span> <span data-ttu-id="56d64-121">在本示例中，将对查询进行切片，以使其针对所有日历年返回 Internet Sales Amount（但仅针对居住在美国的客户）。可以将来自不同层次结构的多个成员添加到 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="56d64-121">In this example, the query is sliced so that it returns the value of Internet Sales Amount for all Calendar Years but only for Customers who live in the United States.Multiple members from different hierarchies can be added to the WHERE clause.</span></span> <span data-ttu-id="56d64-122">以下查询说明了针对居住在美国并在 Category Bikes 中购买了产品的客户的所有日历年的 Internet Sales Amount 的值。</span><span class="sxs-lookup"><span data-stu-id="56d64-122">The following query shows the value of Internet Sales Amount for all Calendar Years for Customers who live in the United States and who bought Products in the Category Bikes:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Country].&[United States], [Product].[Category].&[1])  
```  
  
 <span data-ttu-id="56d64-123">如果您要使用来自同一层次结构的多个成员，您需要在 WHERE 子句中包括一个集。</span><span class="sxs-lookup"><span data-stu-id="56d64-123">If you want to use multiple members from the same hierarchy, you need to include a set in the WHERE clause.</span></span> <span data-ttu-id="56d64-124">例如，以下查询说明了针对在 Category Bikes 中购买了产品并居住在美国或英国的客户的所有日历年的 Internet Sales Amount 的值：</span><span class="sxs-lookup"><span data-stu-id="56d64-124">For example, the following query shows the value of Internet Sales Amount for all Calendar Years for Customers who bought Products in the Category Bikes and live in either the United States or the United Kingdom:</span></span>  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
[Date].[Calendar Year].MEMBERS ON ROWS  
FROM [Adventure Works]  
WHERE(  
{[Customer].[Customer Geography].[Country].&[United States]  
, [Customer].[Customer Geography].[Country].&[United Kingdom]}  
, [Product].[Category].&[1])  
  
```  
  
 <span data-ttu-id="56d64-125">如上所述，如果使用 WHERE 子句的集，则会 隐式聚合该集中的所有成员的值。</span><span class="sxs-lookup"><span data-stu-id="56d64-125">As mentioned above, using a set in the WHERE clause will implicitly aggregate values for all members in the set.</span></span> <span data-ttu-id="56d64-126">在这种情况下，该查询说明了在每个单元中的美国和英国的聚合的值。</span><span class="sxs-lookup"><span data-stu-id="56d64-126">In this case, the query shows aggregated values for the United States and the United Kingdom in each cell.</span></span>  
  
  
