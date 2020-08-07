---
title: 基本 MDX 查询 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], SELECT statement
- queries [MDX], about queries
- cellsets [MDX]
- SELECT statement [MDX]
- cubes [Analysis Services], SELECT statement
ms.assetid: 4fa5a95a-fec9-4584-875c-dbf030c53e82
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6b1a70753abe8e477bd1e522a37f4513cc12a52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589312"
---
# <a name="the-basic-mdx-query-mdx"></a><span data-ttu-id="b4d65-102">基本 MDX 查询 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b4d65-102">The Basic MDX Query (MDX)</span></span>
  <span data-ttu-id="b4d65-103">MDX) 查询 (基本多维表达式是 SELECT 语句-MDX 中最常用的查询。</span><span class="sxs-lookup"><span data-stu-id="b4d65-103">The basic Multidimensional Expressions (MDX) query is the SELECT statement-the most frequently used query in MDX.</span></span> <span data-ttu-id="b4d65-104">通过了解 MDX SELECT 语句如何指定结果集、SELECT 语句的语法是怎样的以及如何使用 SELECT 语句创建简单查询，您将切实理解如何使用 MDX 来查询多维数据。</span><span class="sxs-lookup"><span data-stu-id="b4d65-104">By understanding how an MDX SELECT statement must specify a result set, what the syntax of the SELECT statement is, and how to create a simple query using the SELECT statement, you will have a solid understanding of how to use MDX to query multidimensional data.</span></span>  
  
## <a name="specifying-a-result-set"></a><span data-ttu-id="b4d65-105">指定结果集</span><span class="sxs-lookup"><span data-stu-id="b4d65-105">Specifying a Result Set</span></span>  
 <span data-ttu-id="b4d65-106">在 MDX 中，SELECT 语句可指定一个结果集，其中包含从多维数据集中返回的多维数据子集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-106">In MDX, the SELECT statement specifies a result set that contains a subset of multidimensional data that has been returned from a cube.</span></span> <span data-ttu-id="b4d65-107">若要指定结果集，MDX 查询必须包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="b4d65-107">To specify a result set, an MDX query must contain the following information:</span></span>  
  
-   <span data-ttu-id="b4d65-108">希望结果集要包含的轴数。</span><span class="sxs-lookup"><span data-stu-id="b4d65-108">The number of axes that you want the result set to contain.</span></span> <span data-ttu-id="b4d65-109">最多可在 MDX 查询中指定 128 个轴。</span><span class="sxs-lookup"><span data-stu-id="b4d65-109">You can specify up to 128 axes in an MDX query.</span></span>  
  
-   <span data-ttu-id="b4d65-110">要包括在 MDX 查询的各个轴上的的成员或元组集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-110">The set of members or tuples to include on each axis of the MDX query.</span></span>  
  
-   <span data-ttu-id="b4d65-111">用于设置 MDX 查询上下文的多维数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="b4d65-111">The name of the cube that sets the context of the MDX query.</span></span>  
  
-   <span data-ttu-id="b4d65-112">要包括在切片器轴上的成员或元组集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-112">The set of members or tuples to include on the slicer axis.</span></span> <span data-ttu-id="b4d65-113">有关切片器和查询轴的详细信息，请参阅[使用查询轴和切片器轴限定查询 (MDX)](mdx-query-and-slicer-axes-restricting-the-query.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-113">For more information about slicer and query axes, see[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md).</span></span>  
  
 <span data-ttu-id="b4d65-114">为了标识查询轴、要查询的多维数据集以及切片器轴，MDX SELECT 语句使用下列子句：</span><span class="sxs-lookup"><span data-stu-id="b4d65-114">To identify the query axes, the cube that will be queried, and the slicer axis, the MDX SELECT statement uses the following clauses:</span></span>  
  
-   <span data-ttu-id="b4d65-115">SELECT 子句，用于确定 MDX SELECT 语句的查询轴。</span><span class="sxs-lookup"><span data-stu-id="b4d65-115">A SELECT clause that determines the query axes of an MDX SELECT statement.</span></span> <span data-ttu-id="b4d65-116">有关在 SELECT 子句中构造查询轴的详细信息，请参阅[指定查询轴的内容 (MDX) ](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-116">For more information about the construction of query axes in a SELECT clause, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="b4d65-117">用于确定将要查询的多维数据集的 FROM 子句。</span><span class="sxs-lookup"><span data-stu-id="b4d65-117">A FROM clause that determines which cube will be queried.</span></span> <span data-ttu-id="b4d65-118">有关 FROM 子句的详细信息，请参阅 [SELECT 语句 (MDX)](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-118">For more information about the FROM clause, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
-   <span data-ttu-id="b4d65-119">可选的 WHERE 子句，用于确定在切片器轴上使用哪些成员或元组来限制返回的数据。</span><span class="sxs-lookup"><span data-stu-id="b4d65-119">An optional WHERE clause that determines which members or tuples to use on the slicer axis to restrict the data returned.</span></span> <span data-ttu-id="b4d65-120">有关在 WHERE 子句中构造切片器轴的详细信息，请参阅[指定切片器轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-120">For more information about the construction of a slicer axis in a WHERE clause, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4d65-121">有关 SELECT 语句的各种子句的详细信息，请参阅 [SELECT 语句 (MDX)](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-121">For more detailed information about the various clauses of the SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="select-statement-syntax"></a><span data-ttu-id="b4d65-122">SELECT 语句的语法</span><span class="sxs-lookup"><span data-stu-id="b4d65-122">SELECT Statement Syntax</span></span>  
 <span data-ttu-id="b4d65-123">以下语法显示了一个包括 SELECT、FROM 和 WHERE 子句的基本 SELECT 语句用法：</span><span class="sxs-lookup"><span data-stu-id="b4d65-123">The following syntax shows a basic SELECT statement that includes the use of the SELECT, FROM, and WHERE clauses:</span></span>  
  
```  
[ WITH <SELECT WITH clause> [ , <SELECT WITH clause> ... ] ]   
SELECT [ * | ( <SELECT query axis clause>   
    [ , <SELECT query axis clause> ... ] ) ]  
FROM <SELECT subcube clause>   
[ <SELECT slicer axis clause> ]  
[ <SELECT cell property list clause> ]  
```  
  
 <span data-ttu-id="b4d65-124">MDX SELECT 语句支持可选的语法（如 WITH 关键字），支持使用 MDX 函数来创建计算成员以便确定是否包含在轴或切片器轴中，并支持在查询中返回特定单元属性的值。</span><span class="sxs-lookup"><span data-stu-id="b4d65-124">The MDX SELECT statement supports optional syntax, such as the WITH keyword, the use of MDX functions to create calculated members for inclusion in an axis or slicer axis, and the ability to return the values of specific cell properties as part of the query.</span></span> <span data-ttu-id="b4d65-125">有关 MDX SELECT 语句的详细信息，请参阅 [SELECT 语句 (MDX)](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-125">For more information about the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
### <a name="comparing-the-syntax-of-the-mdx-select-statement-to-sql"></a><span data-ttu-id="b4d65-126">比较 MDX SELECT 语句的语法与 SQL 语法</span><span class="sxs-lookup"><span data-stu-id="b4d65-126">Comparing the Syntax of the MDX SELECT Statement to SQL</span></span>  
 <span data-ttu-id="b4d65-127">MDX SELECT 语句所用的语法格式与 SQL 语法相似。</span><span class="sxs-lookup"><span data-stu-id="b4d65-127">The syntax format for the MDX SELECT statement is similar to that of SQL syntax.</span></span> <span data-ttu-id="b4d65-128">但也有几个基本差异：</span><span class="sxs-lookup"><span data-stu-id="b4d65-128">However, there are several fundamental differences:</span></span>  
  
-   <span data-ttu-id="b4d65-129">MDX 语法通过用大括号括住元组或成员来区分集， ({和} 个字符。 ) 有关成员、元组和集语法的详细信息，请参阅使用[成员、元组和集 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-129">MDX syntax distinguishes sets by surrounding tuples or members with braces (the { and } characters.) For more information about member, tuple, and set syntax, see [Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md).</span></span>  
  
-   <span data-ttu-id="b4d65-130">MDX 查询在 SELECT 语句中可有 0、1、2 或最多 128 个查询轴。</span><span class="sxs-lookup"><span data-stu-id="b4d65-130">MDX queries can have 0, 1, 2 or up to 128 query axes in the SELECT statement.</span></span> <span data-ttu-id="b4d65-131">每个轴具有完全相同的行为方式，这一点与 SQL 不同，后者的查询行为中，行和列之间存在显着的差异。</span><span class="sxs-lookup"><span data-stu-id="b4d65-131">Each axis behaves in exactly the same way, unlike SQL where there are significant differences between how the rows and the columns of a query behave.</span></span>  
  
-   <span data-ttu-id="b4d65-132">像 SQL 查询一样，FROM 子句可为 MDX 查询指定数据源。</span><span class="sxs-lookup"><span data-stu-id="b4d65-132">As with an SQL query, the FROM clause names the source of the data for the MDX query.</span></span> <span data-ttu-id="b4d65-133">但是，MDX FROM 子句被限定为单个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-133">However, the MDX FROM clause is restricted to a single cube.</span></span> <span data-ttu-id="b4d65-134">若要检索来自其他多维数据集的信息，需要使用 LookupCube 函数逐个值地进行检索。</span><span class="sxs-lookup"><span data-stu-id="b4d65-134">Information from other cubes can be retrieved on a value-by-value basis by using the LookupCube function.</span></span>  
  
-   <span data-ttu-id="b4d65-135">WHERE 子句描述了 MDX 查询中的切片器轴。</span><span class="sxs-lookup"><span data-stu-id="b4d65-135">The WHERE clause describes the slicer axis in an MDX query.</span></span> <span data-ttu-id="b4d65-136">它的作用就像一个无形的东西（查询中的额外轴），会对结果集的单元中显示的值进行切片；而 SQL WHERE 子句则不同，它不会直接影响查询的行轴上显示的内容。</span><span class="sxs-lookup"><span data-stu-id="b4d65-136">It acts as something like an invisible, extra axis in the query, slicing the values that appear in the cells in the result set; unlike the SQL WHERE clause it does not directly affect what appears on the rows axis of the query.</span></span> <span data-ttu-id="b4d65-137">可通过其他 MDX 功能（如 FILTER 函数）来获得 SQL WHERE 子句的功能。</span><span class="sxs-lookup"><span data-stu-id="b4d65-137">The functionality of the SQL WHERE clause is available through other MDX functions such as the FILTER function.</span></span>  
  
## <a name="select-statement-example"></a><span data-ttu-id="b4d65-138">SELECT 语句示例</span><span class="sxs-lookup"><span data-stu-id="b4d65-138">SELECT Statement Example</span></span>  
 <span data-ttu-id="b4d65-139">以下示例显示了使用 SELECT 语句的基本 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="b4d65-139">The following example shows a basic MDX query that uses the SELECT statement.</span></span> <span data-ttu-id="b4d65-140">此查询返回包含 Southwest 销售区域 2002 和 2003 年度销售额和税额的结果集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-140">This query returns a result set that contains the 2002 and 2003 sales and tax amounts for the Southwest sales territories.</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON COLUMNS,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON ROWS  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="b4d65-141">在此示例中，此查询定义了以下结果集信息：</span><span class="sxs-lookup"><span data-stu-id="b4d65-141">In this example, the query defines the following result set information:</span></span>  
  
-   <span data-ttu-id="b4d65-142">SELECT 子句将查询轴设置为 Measures 维度的 Sales Amount 和 Tax Amount 成员，以及 Date 维度的 2002 和 2003 成员。</span><span class="sxs-lookup"><span data-stu-id="b4d65-142">The SELECT clause sets the query axes as the Sales Amount and Tax Amount members of the Measures dimension, and the 2002 and 2003 members of the Date dimension.</span></span>  
  
-   <span data-ttu-id="b4d65-143">FROM 子句指明数据源为 Adventure Works 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="b4d65-143">The FROM clause indicates that the data source is the Adventure Works cube.</span></span>  
  
-   <span data-ttu-id="b4d65-144">WHERE 子句将切片器轴定义为 Sales Territory 维度的 Southwest 成员。</span><span class="sxs-lookup"><span data-stu-id="b4d65-144">The WHERE clause defines the slicer axis as the Southwest member of the Sales Territory dimension.</span></span>  
  
 <span data-ttu-id="b4d65-145">请注意，此查询示例还使用了 COLUMNS 和 ROWS 轴别名。</span><span class="sxs-lookup"><span data-stu-id="b4d65-145">Notice that the query example also uses the COLUMNS and ROWS axis aliases.</span></span> <span data-ttu-id="b4d65-146">也可以使用这些轴的序号位置。</span><span class="sxs-lookup"><span data-stu-id="b4d65-146">The ordinal positions for these axes could also have been used.</span></span> <span data-ttu-id="b4d65-147">以下示例显示了如何编写 MDX 查询以使用每个轴的序号位置：</span><span class="sxs-lookup"><span data-stu-id="b4d65-147">The following example shows how the MDX query could have been written to use the ordinal position of each axis:</span></span>  
  
```  
SELECT  
    { [Measures].[Sales Amount],   
        [Measures].[Tax Amount] } ON 0,  
    { [Date].[Fiscal].[Fiscal Year].&[2002],   
        [Date].[Fiscal].[Fiscal Year].&[2003] } ON 1  
FROM [Adventure Works]  
WHERE ( [Sales Territory].[Southwest] )  
```  
  
 <span data-ttu-id="b4d65-148">有关更多详细示例，请参阅[指定查询轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) 和[指定切片器轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="b4d65-148">For more detailed examples, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)and [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d65-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4d65-149">See Also</span></span>  
 <span data-ttu-id="b4d65-150">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="b4d65-150">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 [<span data-ttu-id="b4d65-151">SELECT 语句 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b4d65-151">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
