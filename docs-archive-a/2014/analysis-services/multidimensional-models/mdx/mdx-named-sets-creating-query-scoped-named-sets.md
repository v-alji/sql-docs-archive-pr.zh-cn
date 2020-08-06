---
title: " (MDX) 创建查询作用域的命名集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- query-scoped named sets [MDX]
- WITH keyword
ms.assetid: 78bc1e9a-1bc4-4a5a-ab0b-cf430c8fbfe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6eccb4e20fca03079a04a0219b07f6411b80a433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689053"
---
# <a name="creating-query-scoped-named-sets-mdx"></a><span data-ttu-id="d4bd2-102">创建查询作用域的命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d4bd2-102">Creating Query-Scoped Named Sets (MDX)</span></span>
  <span data-ttu-id="d4bd2-103">如果某个命名集仅用于单个多维表达式 (MDX) 查询，则可以使用 WITH 关键字来定义该命名集。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-103">If a named set is only required for a single Multidimensional Expressions (MDX) query, you can define that named set by using the WITH keyword.</span></span> <span data-ttu-id="d4bd2-104">使用 WITH 关键字创建的命名集在执行完查询之后就不再存在。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-104">A named set that is created by using the WITH keyword no longer exists after the query has finished running.</span></span>  
  
 <span data-ttu-id="d4bd2-105">如本主题中所述，WITH 关键字的语法非常灵活，甚至允许使用函数来定义命名集。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-105">As discussed in this topic, the syntax of the WITH keyword is quite flexible, even accommodating the use of functions to define the named set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4bd2-106">有关命名集的详细信息，请参阅[在 MDX 中生成命名集 (MDX)](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-106">For more information about named sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
## <a name="with-keyword-syntax"></a><span data-ttu-id="d4bd2-107">WITH 关键字语法</span><span class="sxs-lookup"><span data-stu-id="d4bd2-107">WITH Keyword Syntax</span></span>  
 <span data-ttu-id="d4bd2-108">可以使用以下语法将 WITH 关键字添加到 MDX SELECT 语句：</span><span class="sxs-lookup"><span data-stu-id="d4bd2-108">Use the following syntax to add the WITH keyword to a MDX SELECT statement:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
  
<SELECT WITH clause> ::=  
   ( SET Set_Identifier AS 'Set_Expression')  
  
```  
  
 <span data-ttu-id="d4bd2-109">在 WITH 关键字的语法中， `Set_Identifier` 参数包含命名集的别名。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-109">In the syntax for the WITH keyword, the `Set_Identifier` parameter contains the alias for the named set.</span></span> <span data-ttu-id="d4bd2-110">`Set_Expression` 参数包含命名集别名所指代的集表达式。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-110">The `Set_Expression` parameter contains the set expression to which the named set alias refers.</span></span>  
  
## <a name="with-keyword-example"></a><span data-ttu-id="d4bd2-111">WITH 关键字示例</span><span class="sxs-lookup"><span data-stu-id="d4bd2-111">WITH Keyword Example</span></span>  
 <span data-ttu-id="d4bd2-112">下列 MDX 查询将检查 `FoodMart 2000`（Microsoft SQL Server 2000 Analysis Services 示例数据库）中各种 Chardonnay 酒和 Chablis 酒的单位销售额。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-112">The following MDX query examines the unit sales of the various Chardonnay and Chablis wines in `FoodMart 2000`, the sample database for Microsoft SQL Server 2000 Analysis Services.</span></span> <span data-ttu-id="d4bd2-113">尽管就结果集而言此查询相当简单，但是在必须维护这种查询的情况下，它就显得冗长且难处理。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-113">This query, although fairly simple in terms of the result set, is lengthy and unwieldy when you have to maintenance such a query.</span></span>  
  
```  
SELECT  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]} ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
 <span data-ttu-id="d4bd2-114">若要使上述 MDX 更易于维护，可以使用 WITH 关键字为此查询创建一个命名集。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-114">To make the previous MDX query easier to maintain, you can create a named set for the query by using the WITH keyword.</span></span> <span data-ttu-id="d4bd2-115">以下代码显示了如何使用 WITH 关键字来创建命名集 `[ChardonnayChablis]`，以及该命名集如何使得 SELECT 语句更简洁、更易于维护。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-115">The following code shows how to use the WITH keyword to create a named set, `[ChardonnayChablis]`, and how the named set makes the SELECT statement shorter and easier to maintain.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   {[Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chardonnay],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Good].[Good Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Pearl].[Pearl Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Portsmouth].[Portsmouth Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Top Measure].[Top Measure Chablis Wine],  
   [Product].[All Products].[Drink].[Alcoholic Beverages].[Beer and Wine].[Wine].[Walrus].[Walrus Chablis Wine]}  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
```  
  
### <a name="using-functions-together-with-the-with-keyword"></a><span data-ttu-id="d4bd2-116">将函数与 WITH 关键字一起使用</span><span class="sxs-lookup"><span data-stu-id="d4bd2-116">Using Functions Together with the WITH Keyword</span></span>  
 <span data-ttu-id="d4bd2-117">尽管可以显式定义命名集的每个成员，但是这种方法可能会产生过长的语句。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-117">Although you can explicitly define each member of a named set, this approach can produce a lengthy statement.</span></span> <span data-ttu-id="d4bd2-118">若要使命名集的创建和维护更简单，可以使用 MDX 函数来定义成员。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-118">To make the creation and maintenance of a named set easier, you can use MDX functions to define the members.</span></span>  
  
 <span data-ttu-id="d4bd2-119">例如，下面的 MDX 查询示例使用 [Filter](/sql/mdx/filter-mdx)、 [CurrentMember](/sql/mdx/current-mdx)和 [Name](/sql/mdx/members-string-mdx) MDX 函数以及 InStr VBA 函数创建 `[ChardonnayChablis]` 命名集。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-119">For example, the following MDX query example uses the [Filter](/sql/mdx/filter-mdx), [CurrentMember](/sql/mdx/current-mdx), and [Name](/sql/mdx/members-string-mdx) MDX functions and the InStr VBA function to create the `[ChardonnayChablis]` named set.</span></span> <span data-ttu-id="d4bd2-120">这种版本的 `[ChardonnayChablis]` 命名集与本主题前面所演示的显式定义的命名集相同。</span><span class="sxs-lookup"><span data-stu-id="d4bd2-120">This version of the `[ChardonnayChablis]` named set is the same as the explicitly defined version shown previously in this topic.</span></span>  
  
```  
WITH SET [ChardonnayChablis] AS  
   'Filter([Product].Members, (InStr(1, [Product].CurrentMember.Name, "chardonnay") <> 0) OR (InStr(1, [Product].CurrentMember.Name, "chablis") <> 0))'  
  
SELECT  
   [ChardonnayChablis] ON COLUMNS,  
   {Measures.[Unit Sales]} ON ROWS  
FROM Sales  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4bd2-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4bd2-121">See Also</span></span>  
 <span data-ttu-id="d4bd2-122">[SELECT 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span><span class="sxs-lookup"><span data-stu-id="d4bd2-122">[SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select) </span></span>  
 [<span data-ttu-id="d4bd2-123">创建会话作用域的命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="d4bd2-123">Creating Session-Scoped Named Sets &#40;MDX&#41;</span></span>](mdx-named-sets-creating-session-scoped-named-sets.md)  
  
  
