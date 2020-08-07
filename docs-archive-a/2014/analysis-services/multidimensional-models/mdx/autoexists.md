---
title: Autoexists |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd35958a364456c12d58392afe3754f6adcf97b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588118"
---
# <a name="autoexists"></a><span data-ttu-id="69cd5-102">Autoexists</span><span class="sxs-lookup"><span data-stu-id="69cd5-102">Autoexists</span></span>
  <span data-ttu-id="69cd5-103">“autoexists” \*\* 的概念将多维数据集空间限制为在多维数据集中实际存在的那些单元，而不是可能由于从同一层次结构创建属性层次结构成员的所有可能组合而存在的那些单元。</span><span class="sxs-lookup"><span data-stu-id="69cd5-103">The concept of *autoexists* limits the cube space to those cells that actually exist in the cube in contraposition to those that might exist as a result of creating all possible combinations of attribute hierarchy members from the same hierarchy.</span></span> <span data-ttu-id="69cd5-104">其原因在于，一个属性层次结构的成员不能与同一维度中其他属性层次结构的成员共存。</span><span class="sxs-lookup"><span data-stu-id="69cd5-104">This is because members of one attribute hierarchy cannot exist with members of another attribute hierarchy in the same dimension.</span></span> <span data-ttu-id="69cd5-105">在 SELECT 语句中使用同一维度的两个或更多属性层次结构时，Analysis Services 会计算这些属性的表达式，以确保这些属性的成员得到适当限制，使它们满足所有其他属性的条件。</span><span class="sxs-lookup"><span data-stu-id="69cd5-105">When two or more attribute hierarchies of the same dimension are used in a SELECT statement, Analysis Services evaluates the attributes' expressions to make sure that the members of those attributes are properly confined to meet the criteria of all other attributes.</span></span>  
  
 <span data-ttu-id="69cd5-106">例如，假定您在处理来自 Geography 维度的属性。</span><span class="sxs-lookup"><span data-stu-id="69cd5-106">For example, suppose you are working with attributes from the Geography dimension.</span></span> <span data-ttu-id="69cd5-107">如果您有一个表达式返回 City 属性中的所有成员，另一个表达式将 Country 属性中的成员限定为欧洲的所有国家/地区，这样将使 City 成员限制为仅属于欧洲国家的城市。</span><span class="sxs-lookup"><span data-stu-id="69cd5-107">If you have one expression that returns all members from the City attribute and another expression that confines members from the Country attribute to all countries in Europe, then this will result in the City members being confined to only those cities that belong to countries in Europe.</span></span> <span data-ttu-id="69cd5-108">其原因就在于 Analysis Services 的 autoexists 特性。</span><span class="sxs-lookup"><span data-stu-id="69cd5-108">This is because of the autoexists characteristic of Analysis Services.</span></span> <span data-ttu-id="69cd5-109">Autoexists 仅适用于同一维度中的属性，因为它试图阻止在一个属性表达式中排除的维度记录被包括在其他属性表达式中。</span><span class="sxs-lookup"><span data-stu-id="69cd5-109">Autoexists only applies to attributes from the same dimension because it tries to prevent the dimension records excluded in one attribute expression from being included by the other attribute expressions.</span></span> <span data-ttu-id="69cd5-110">也可以将 Autoexists 理解为不同的属性表达式产生的维度行的交集。</span><span class="sxs-lookup"><span data-stu-id="69cd5-110">Autoexists can also be understood as the resulting intersection of the different attributes expressions over the dimension rows.</span></span>  
  
## <a name="cell-existence"></a><span data-ttu-id="69cd5-111">单元存在性</span><span class="sxs-lookup"><span data-stu-id="69cd5-111">Cell Existence</span></span>  
 <span data-ttu-id="69cd5-112">以下单元始终存在：</span><span class="sxs-lookup"><span data-stu-id="69cd5-112">The following cells always exist:</span></span>  
  
-   <span data-ttu-id="69cd5-113">在与同一维度中其他层次结构的成员相交时，每个层次结构的“（全部）”成员。</span><span class="sxs-lookup"><span data-stu-id="69cd5-113">The (All) member, of every hierarchy, when crossed with members of other hierarchies in the same dimension.</span></span>  
  
-   <span data-ttu-id="69cd5-114">在与其非计算同级相交或者与其非计算同级的父级或子级相交时的计算成员。</span><span class="sxs-lookup"><span data-stu-id="69cd5-114">Calculated members when crossed with their non-calculated siblings, or with the parents or descendants of their non-calculated siblings.</span></span>  
  
## <a name="providing-non-existing-cells"></a><span data-ttu-id="69cd5-115">提供不存在的单元</span><span class="sxs-lookup"><span data-stu-id="69cd5-115">Providing Non-existing cells</span></span>  
 <span data-ttu-id="69cd5-116">不存在的单元是系统为响应请求在多维数据集中不存在的单元的查询或计算而提供的单元。</span><span class="sxs-lookup"><span data-stu-id="69cd5-116">A non-existing cell is a cell provided by the system as a response to a query or calculation that requests a cell that does not exist in the cube.</span></span> <span data-ttu-id="69cd5-117">例如，如果某多维数据集具有 City 属性层次结构、属于 Geography 维度的 Country 属性层次结构和 Internet Sales Amount 度量值，则此多维数据集的空间仅包含那些共存的成员。</span><span class="sxs-lookup"><span data-stu-id="69cd5-117">For example, if you have a cube that has a City attribute hierarchy and a Country attribute hierarchy that belong to the Geography dimension, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="69cd5-118">例如，如果 City 属性层次结构包含城市 New York、London、Paris、Tokyo 和 Melbourne，而 Country 属性层次结构包含国家（地区）United States、United Kingdom、France、Japan 和 Australia，则该多维数据集的空间不包含 Paris 和 United States 相交处的空间（单元）。</span><span class="sxs-lookup"><span data-stu-id="69cd5-118">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="69cd5-119">当查询单元不存在时，不存在的单元返回空，即它们无法包含计算结果，并且您不能定义写入此空间的计算。</span><span class="sxs-lookup"><span data-stu-id="69cd5-119">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="69cd5-120">例如，下面的语句包含不存在的单元。</span><span class="sxs-lookup"><span data-stu-id="69cd5-120">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="69cd5-121">此查询使用 [Members (Set) (MDX)](/sql/mdx/members-set-mdx) 函数返回列轴上 Gender 属性层次结构的成员集，并将此集与行轴上 Customer 属性层次结构的指定成员集相交。</span><span class="sxs-lookup"><span data-stu-id="69cd5-121">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="69cd5-122">执行前面的查询时，Aaron A. Allen 与 Female 相交处的单元将显示空。</span><span class="sxs-lookup"><span data-stu-id="69cd5-122">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="69cd5-123">同样，Abigail Clark 与 Male 相交处的单元也将显示空。</span><span class="sxs-lookup"><span data-stu-id="69cd5-123">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="69cd5-124">这些单元不存在并且不能包含值，但不存在的单元可出现在查询返回的结果中。</span><span class="sxs-lookup"><span data-stu-id="69cd5-124">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="69cd5-125">如果使用 [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 函数返回同一维度中属性层次结构中的属性层次结构成员的叉积，自动共存将限制只返回那些实际存在的元组集，而不是返回整个笛卡尔乘积的元组。</span><span class="sxs-lookup"><span data-stu-id="69cd5-125">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="69cd5-126">例如，运行以下查询并检查其结果。</span><span class="sxs-lookup"><span data-stu-id="69cd5-126">For example, run and then examine the results from the execution of the following query.</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="69cd5-127">请注意 0 用于表示列轴的名称，它是列轴“axis(0)”的简称。</span><span class="sxs-lookup"><span data-stu-id="69cd5-127">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="69cd5-128">前面的查询仅为查询中每个属性层次结构的共存成员返回单元。</span><span class="sxs-lookup"><span data-stu-id="69cd5-128">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="69cd5-129">之前的查询还可以使用[交叉结合 (MDX) ](/sql/mdx/crossjoin-mdx)函数的新 \* 变体来编写。</span><span class="sxs-lookup"><span data-stu-id="69cd5-129">The previous query can also be written using the new \* variant of the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="69cd5-130">前面的查询还可以通过以下方式来编写：</span><span class="sxs-lookup"><span data-stu-id="69cd5-130">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="69cd5-131">虽然结果集中的元数据将不同，但返回的单元值将是相同的。</span><span class="sxs-lookup"><span data-stu-id="69cd5-131">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="69cd5-132">例如，在前面的查询中，Country 层次结构已移到切片器轴（在 WHERE 子句中），因此没有显式显示在结果集中。</span><span class="sxs-lookup"><span data-stu-id="69cd5-132">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="69cd5-133">这三个前面的查询都说明了中的自动共存行为的影响 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="69cd5-133">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="deep-and-shallow-autoexists"></a><span data-ttu-id="69cd5-134">深度和浅表 Autoexists</span><span class="sxs-lookup"><span data-stu-id="69cd5-134">Deep and Shallow Autoexists</span></span>  
 <span data-ttu-id="69cd5-135">Autoexists 可以深度或浅表的形式应用于表达式。</span><span class="sxs-lookup"><span data-stu-id="69cd5-135">Autoexists can be applied to the expressions as Deep or Shallow.</span></span> <span data-ttu-id="69cd5-136">`Deep Autoexists` 意味着将对所有表达式进行计算，以便在应用了切片器表达式、轴中的嵌套 select 表达式等后到达可能的最深空间。</span><span class="sxs-lookup"><span data-stu-id="69cd5-136">`Deep Autoexists` means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span> <span data-ttu-id="69cd5-137">`Shallow Autoexists` 意味着在将当前表达式和这些结果传递到当前表达式之前对外部表达式进行计算。</span><span class="sxs-lookup"><span data-stu-id="69cd5-137">`Shallow Autoexists` means that external expressions are evaluated before the current expression and those results are passed to the current expression.</span></span> <span data-ttu-id="69cd5-138">默认设置为深度 autoexists。</span><span class="sxs-lookup"><span data-stu-id="69cd5-138">The default setting is deep autoexists.</span></span>  
  
 <span data-ttu-id="69cd5-139">下面的应用场景和示例将帮助阐明不同类型的 Autoexists。</span><span class="sxs-lookup"><span data-stu-id="69cd5-139">The following scenario and samples will help to illustrate the different types of Autoexistss.</span></span> <span data-ttu-id="69cd5-140">在下面的示例中，将创建两个集：一个作为计算表达式，另一个作为常量表达式。</span><span class="sxs-lookup"><span data-stu-id="69cd5-140">In the following examples two sets will be created: one as a calculated expression and the other as a constant expression.</span></span>  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="69cd5-141">获得的结果集如下：</span><span class="sxs-lookup"><span data-stu-id="69cd5-141">The obtained result set is:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="69cd5-142">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-142">**Reseller Sales Amount**</span></span>|<span data-ttu-id="69cd5-143">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-143">**Discount Amount**</span></span>|<span data-ttu-id="69cd5-144">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-144">**PCT Discount**</span></span>|  
|<span data-ttu-id="69cd5-145">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="69cd5-145">**Mountain-200**</span></span>|<span data-ttu-id="69cd5-146">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="69cd5-146">**$14,356,699.36**</span></span>|<span data-ttu-id="69cd5-147">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="69cd5-147">**$19,012.71**</span></span>|<span data-ttu-id="69cd5-148">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-148">**0.13%**</span></span>|  
|<span data-ttu-id="69cd5-149">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="69cd5-149">**Road-250**</span></span>|<span data-ttu-id="69cd5-150">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="69cd5-150">**$9,377,457.68**</span></span>|<span data-ttu-id="69cd5-151">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="69cd5-151">**$4,032.47**</span></span>|<span data-ttu-id="69cd5-152">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-152">**0.04%**</span></span>|  
|<span data-ttu-id="69cd5-153">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="69cd5-153">**Mountain-100**</span></span>|<span data-ttu-id="69cd5-154">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-154">**$8,568,958.27**</span></span>|<span data-ttu-id="69cd5-155">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-155">**$139,393.27**</span></span>|<span data-ttu-id="69cd5-156">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-156">**1.63%**</span></span>|  
|<span data-ttu-id="69cd5-157">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="69cd5-157">**Road-650**</span></span>|<span data-ttu-id="69cd5-158">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="69cd5-158">**$7,442,141.81**</span></span>|<span data-ttu-id="69cd5-159">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="69cd5-159">**$39,698.30**</span></span>|<span data-ttu-id="69cd5-160">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-160">**0.53%**</span></span>|  
|<span data-ttu-id="69cd5-161">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="69cd5-161">**Touring-1000**</span></span>|<span data-ttu-id="69cd5-162">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="69cd5-162">**$6,723,794.29**</span></span>|<span data-ttu-id="69cd5-163">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="69cd5-163">**$166,144.17**</span></span>|<span data-ttu-id="69cd5-164">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-164">**2.47%**</span></span>|  
|<span data-ttu-id="69cd5-165">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-165">**Road-550-W**</span></span>|<span data-ttu-id="69cd5-166">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="69cd5-166">**$3,668,383.88**</span></span>|<span data-ttu-id="69cd5-167">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="69cd5-167">**$1,901.97**</span></span>|<span data-ttu-id="69cd5-168">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-168">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-169">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-169">**Road-350-W**</span></span>|<span data-ttu-id="69cd5-170">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="69cd5-170">**$3,665,932.31**</span></span>|<span data-ttu-id="69cd5-171">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="69cd5-171">**$20,946.50**</span></span>|<span data-ttu-id="69cd5-172">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-172">**0.57%**</span></span>|  
|<span data-ttu-id="69cd5-173">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-173">**HL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-174">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-174">**$3,365,069.27**</span></span>|<span data-ttu-id="69cd5-175">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="69cd5-175">**$174.11**</span></span>|<span data-ttu-id="69cd5-176">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-176">**0.01%**</span></span>|  
|<span data-ttu-id="69cd5-177">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="69cd5-177">**Road-150**</span></span>|<span data-ttu-id="69cd5-178">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="69cd5-178">**$2,363,805.16**</span></span>|<span data-ttu-id="69cd5-179">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="69cd5-179">**$0.00**</span></span>|<span data-ttu-id="69cd5-180">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-180">**0.00%**</span></span>|  
|<span data-ttu-id="69cd5-181">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="69cd5-181">**Touring-3000**</span></span>|<span data-ttu-id="69cd5-182">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="69cd5-182">**$2,046,508.26**</span></span>|<span data-ttu-id="69cd5-183">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="69cd5-183">**$79,582.15**</span></span>|<span data-ttu-id="69cd5-184">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-184">**3.89%**</span></span>|  
  
 <span data-ttu-id="69cd5-185">获得的产品集似乎与 Preferred10Products 相同；因此，请验证 Preferred10Products 集：</span><span class="sxs-lookup"><span data-stu-id="69cd5-185">The obtained set of products seems to be the same as Preferred10Products; so, verifying the Preferred10Products set:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="69cd5-186">根据以下结果，两个产品集（Top10SellingProducts 和 Preferred10Products）是相同的</span><span class="sxs-lookup"><span data-stu-id="69cd5-186">As per the following results, both sets (Top10SellingProducts, Preferred10Products) are the same</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="69cd5-187">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-187">**Reseller Sales Amount**</span></span>|<span data-ttu-id="69cd5-188">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-188">**Discount Amount**</span></span>|<span data-ttu-id="69cd5-189">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-189">**PCT Discount**</span></span>|  
|<span data-ttu-id="69cd5-190">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="69cd5-190">**Mountain-200**</span></span>|<span data-ttu-id="69cd5-191">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="69cd5-191">**$14,356,699.36**</span></span>|<span data-ttu-id="69cd5-192">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="69cd5-192">**$19,012.71**</span></span>|<span data-ttu-id="69cd5-193">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-193">**0.13%**</span></span>|  
|<span data-ttu-id="69cd5-194">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="69cd5-194">**Road-250**</span></span>|<span data-ttu-id="69cd5-195">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="69cd5-195">**$9,377,457.68**</span></span>|<span data-ttu-id="69cd5-196">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="69cd5-196">**$4,032.47**</span></span>|<span data-ttu-id="69cd5-197">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-197">**0.04%**</span></span>|  
|<span data-ttu-id="69cd5-198">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="69cd5-198">**Mountain-100**</span></span>|<span data-ttu-id="69cd5-199">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-199">**$8,568,958.27**</span></span>|<span data-ttu-id="69cd5-200">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-200">**$139,393.27**</span></span>|<span data-ttu-id="69cd5-201">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-201">**1.63%**</span></span>|  
|<span data-ttu-id="69cd5-202">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="69cd5-202">**Road-650**</span></span>|<span data-ttu-id="69cd5-203">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="69cd5-203">**$7,442,141.81**</span></span>|<span data-ttu-id="69cd5-204">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="69cd5-204">**$39,698.30**</span></span>|<span data-ttu-id="69cd5-205">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-205">**0.53%**</span></span>|  
|<span data-ttu-id="69cd5-206">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="69cd5-206">**Touring-1000**</span></span>|<span data-ttu-id="69cd5-207">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="69cd5-207">**$6,723,794.29**</span></span>|<span data-ttu-id="69cd5-208">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="69cd5-208">**$166,144.17**</span></span>|<span data-ttu-id="69cd5-209">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-209">**2.47%**</span></span>|  
|<span data-ttu-id="69cd5-210">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-210">**Road-550-W**</span></span>|<span data-ttu-id="69cd5-211">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="69cd5-211">**$3,668,383.88**</span></span>|<span data-ttu-id="69cd5-212">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="69cd5-212">**$1,901.97**</span></span>|<span data-ttu-id="69cd5-213">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-213">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-214">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-214">**Road-350-W**</span></span>|<span data-ttu-id="69cd5-215">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="69cd5-215">**$3,665,932.31**</span></span>|<span data-ttu-id="69cd5-216">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="69cd5-216">**$20,946.50**</span></span>|<span data-ttu-id="69cd5-217">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-217">**0.57%**</span></span>|  
|<span data-ttu-id="69cd5-218">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-218">**HL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-219">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-219">**$3,365,069.27**</span></span>|<span data-ttu-id="69cd5-220">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="69cd5-220">**$174.11**</span></span>|<span data-ttu-id="69cd5-221">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-221">**0.01%**</span></span>|  
|<span data-ttu-id="69cd5-222">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="69cd5-222">**Road-150**</span></span>|<span data-ttu-id="69cd5-223">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="69cd5-223">**$2,363,805.16**</span></span>|<span data-ttu-id="69cd5-224">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="69cd5-224">**$0.00**</span></span>|<span data-ttu-id="69cd5-225">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-225">**0.00%**</span></span>|  
|<span data-ttu-id="69cd5-226">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="69cd5-226">**Touring-3000**</span></span>|<span data-ttu-id="69cd5-227">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="69cd5-227">**$2,046,508.26**</span></span>|<span data-ttu-id="69cd5-228">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="69cd5-228">**$79,582.15**</span></span>|<span data-ttu-id="69cd5-229">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-229">**3.89%**</span></span>|  
  
 <span data-ttu-id="69cd5-230">下面的示例将阐释深度 Autoexists 的概念。</span><span class="sxs-lookup"><span data-stu-id="69cd5-230">The following example will illustrate the concept of deep Autoexists.</span></span> <span data-ttu-id="69cd5-231">在该示例中，我们将依据 [Product].[Product Line] 属性对 [Mountain] 组中的产品筛选 Top10SellingProducts。</span><span class="sxs-lookup"><span data-stu-id="69cd5-231">In the example we are filtering Top10SellingProducts by [Product].[Product Line] attribute for those in [Mountain] group.</span></span> <span data-ttu-id="69cd5-232">请注意两个属性（slicer 和 axis）均属于同一维度 [Product]。</span><span class="sxs-lookup"><span data-stu-id="69cd5-232">Note that both attributes (slicer and axis) belong to the same dimension, [Product].</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="69cd5-233">产生以下结果集：</span><span class="sxs-lookup"><span data-stu-id="69cd5-233">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="69cd5-234">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-234">**Reseller Sales Amount**</span></span>|<span data-ttu-id="69cd5-235">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-235">**Discount Amount**</span></span>|<span data-ttu-id="69cd5-236">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-236">**PCT Discount**</span></span>|  
|<span data-ttu-id="69cd5-237">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="69cd5-237">**Mountain-200**</span></span>|<span data-ttu-id="69cd5-238">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="69cd5-238">**$14,356,699.36**</span></span>|<span data-ttu-id="69cd5-239">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="69cd5-239">**$19,012.71**</span></span>|<span data-ttu-id="69cd5-240">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-240">**0.13%**</span></span>|  
|<span data-ttu-id="69cd5-241">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="69cd5-241">**Mountain-100**</span></span>|<span data-ttu-id="69cd5-242">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-242">**$8,568,958.27**</span></span>|<span data-ttu-id="69cd5-243">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-243">**$139,393.27**</span></span>|<span data-ttu-id="69cd5-244">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-244">**1.63%**</span></span>|  
|<span data-ttu-id="69cd5-245">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-245">**HL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-246">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-246">**$3,365,069.27**</span></span>|<span data-ttu-id="69cd5-247">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="69cd5-247">**$174.11**</span></span>|<span data-ttu-id="69cd5-248">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-248">**0.01%**</span></span>|  
|<span data-ttu-id="69cd5-249">**Mountain-300**</span><span class="sxs-lookup"><span data-stu-id="69cd5-249">**Mountain-300**</span></span>|<span data-ttu-id="69cd5-250">**$1,907,249.38**</span><span class="sxs-lookup"><span data-stu-id="69cd5-250">**$1,907,249.38**</span></span>|<span data-ttu-id="69cd5-251">**$876.95**</span><span class="sxs-lookup"><span data-stu-id="69cd5-251">**$876.95**</span></span>|<span data-ttu-id="69cd5-252">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-252">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-253">**Mountain-500**</span><span class="sxs-lookup"><span data-stu-id="69cd5-253">**Mountain-500**</span></span>|<span data-ttu-id="69cd5-254">**$1,067,327.31**</span><span class="sxs-lookup"><span data-stu-id="69cd5-254">**$1,067,327.31**</span></span>|<span data-ttu-id="69cd5-255">**$17,266.09**</span><span class="sxs-lookup"><span data-stu-id="69cd5-255">**$17,266.09**</span></span>|<span data-ttu-id="69cd5-256">**1.62%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-256">**1.62%**</span></span>|  
|<span data-ttu-id="69cd5-257">**Mountain-400-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-257">**Mountain-400-W**</span></span>|<span data-ttu-id="69cd5-258">**$592,450.05**</span><span class="sxs-lookup"><span data-stu-id="69cd5-258">**$592,450.05**</span></span>|<span data-ttu-id="69cd5-259">**$303.49**</span><span class="sxs-lookup"><span data-stu-id="69cd5-259">**$303.49**</span></span>|<span data-ttu-id="69cd5-260">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-260">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-261">**LL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-261">**LL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-262">**$521,864.42**</span><span class="sxs-lookup"><span data-stu-id="69cd5-262">**$521,864.42**</span></span>|<span data-ttu-id="69cd5-263">**$252.41**</span><span class="sxs-lookup"><span data-stu-id="69cd5-263">**$252.41**</span></span>|<span data-ttu-id="69cd5-264">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-264">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-265">**ML Mountain Frame-W**</span><span class="sxs-lookup"><span data-stu-id="69cd5-265">**ML Mountain Frame-W**</span></span>|<span data-ttu-id="69cd5-266">**$482,953.16**</span><span class="sxs-lookup"><span data-stu-id="69cd5-266">**$482,953.16**</span></span>|<span data-ttu-id="69cd5-267">**$206.95**</span><span class="sxs-lookup"><span data-stu-id="69cd5-267">**$206.95**</span></span>|<span data-ttu-id="69cd5-268">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-268">**0.04%**</span></span>|  
|<span data-ttu-id="69cd5-269">**ML Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-269">**ML Mountain Frame**</span></span>|<span data-ttu-id="69cd5-270">**$343,785.29**</span><span class="sxs-lookup"><span data-stu-id="69cd5-270">**$343,785.29**</span></span>|<span data-ttu-id="69cd5-271">**$161.82**</span><span class="sxs-lookup"><span data-stu-id="69cd5-271">**$161.82**</span></span>|<span data-ttu-id="69cd5-272">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-272">**0.05%**</span></span>|  
|<span data-ttu-id="69cd5-273">**Women's Mountain Shorts**</span><span class="sxs-lookup"><span data-stu-id="69cd5-273">**Women's Mountain Shorts**</span></span>|<span data-ttu-id="69cd5-274">**$260,304.09**</span><span class="sxs-lookup"><span data-stu-id="69cd5-274">**$260,304.09**</span></span>|<span data-ttu-id="69cd5-275">**$6,675.56**</span><span class="sxs-lookup"><span data-stu-id="69cd5-275">**$6,675.56**</span></span>|<span data-ttu-id="69cd5-276">**2.56%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-276">**2.56%**</span></span>|  
  
 <span data-ttu-id="69cd5-277">在上面的结果集中，我们看到 Top10SellingProducts 列表中有七种新产品，并且 Mountain-200、Mountain-100 和 HL Mountain Frame 移到了列表顶部。</span><span class="sxs-lookup"><span data-stu-id="69cd5-277">In the above result set we have seven newcomers to the list of Top10SellingProducts and Mountain-200, Mountain-100, and HL Mountain Frame have moved to the top of the list.</span></span> <span data-ttu-id="69cd5-278">在前面的结果集中，这三个值是混杂的。</span><span class="sxs-lookup"><span data-stu-id="69cd5-278">In the previous result set those three values were interspersed.</span></span>  
  
 <span data-ttu-id="69cd5-279">这称为深度 Autoexists，因为对 Top10SellingProducts 集进行计算以符合查询的切片条件。</span><span class="sxs-lookup"><span data-stu-id="69cd5-279">This is called Deep Autoexists, because the Top10SellingProducts set is evaluated to meet the slicing conditions of the query.</span></span> <span data-ttu-id="69cd5-280">深度 Autoexists 意味着将对所有表达式进行计算，以便在应用了切片器表达式、轴中的嵌套 select 表达式等后到达可能的最深空间。</span><span class="sxs-lookup"><span data-stu-id="69cd5-280">Deep Autoexists means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span>  
  
 <span data-ttu-id="69cd5-281">不过，有人可能希望能够对与 Preferred10Products 等效的 Top10SellingProducts 进行分析，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="69cd5-281">However, one might want to be able to do the analysis over the Top10SellingProducts as equivalent to Preferred10Products, as in the following example:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="69cd5-282">产生以下结果集：</span><span class="sxs-lookup"><span data-stu-id="69cd5-282">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="69cd5-283">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-283">**Reseller Sales Amount**</span></span>|<span data-ttu-id="69cd5-284">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-284">**Discount Amount**</span></span>|<span data-ttu-id="69cd5-285">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-285">**PCT Discount**</span></span>|  
|<span data-ttu-id="69cd5-286">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="69cd5-286">**Mountain-200**</span></span>|<span data-ttu-id="69cd5-287">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="69cd5-287">**$14,356,699.36**</span></span>|<span data-ttu-id="69cd5-288">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="69cd5-288">**$19,012.71**</span></span>|<span data-ttu-id="69cd5-289">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-289">**0.13%**</span></span>|  
|<span data-ttu-id="69cd5-290">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="69cd5-290">**Mountain-100**</span></span>|<span data-ttu-id="69cd5-291">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-291">**$8,568,958.27**</span></span>|<span data-ttu-id="69cd5-292">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-292">**$139,393.27**</span></span>|<span data-ttu-id="69cd5-293">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-293">**1.63%**</span></span>|  
|<span data-ttu-id="69cd5-294">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-294">**HL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-295">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-295">**$3,365,069.27**</span></span>|<span data-ttu-id="69cd5-296">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="69cd5-296">**$174.11**</span></span>|<span data-ttu-id="69cd5-297">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-297">**0.01%**</span></span>|  
  
 <span data-ttu-id="69cd5-298">在上面的示例中，与预期的一样，切片生成的结果仅包含 Preferred10Products 中属于 [Product].[Product Line] 中的 [Mountain] 组的那些产品，因为 Preferred10Products 是一个常量表达式。</span><span class="sxs-lookup"><span data-stu-id="69cd5-298">In the above results, the slicing gives a result that contains only those products from Preferred10Products that are part of the [Mountain] group in [Product].[Product Line]; as expected, because Preferred10Products is a constant expression.</span></span>  
  
 <span data-ttu-id="69cd5-299">此结果集还可以理解为浅表 Autoexists。</span><span class="sxs-lookup"><span data-stu-id="69cd5-299">This result set is also understood as Shallow Autoexists.</span></span> <span data-ttu-id="69cd5-300">这是因为该表达式是在切片子句之前计算的。</span><span class="sxs-lookup"><span data-stu-id="69cd5-300">This is because the expression is evaluated before the slicing clause.</span></span> <span data-ttu-id="69cd5-301">在上面的示例中，出于演示目的以介绍这一概念，该表达式是一个常量表达式。</span><span class="sxs-lookup"><span data-stu-id="69cd5-301">In the previous example, the expression was a constant expression for illustration purposes in order to introduce the concept.</span></span>  
  
 <span data-ttu-id="69cd5-302">可以使用 `Autoexists` 连接字符串属性在会话级修改 Autoexists 的行为。</span><span class="sxs-lookup"><span data-stu-id="69cd5-302">Autoexists behavior can be modified at the session level using the `Autoexists` connection string property.</span></span> <span data-ttu-id="69cd5-303">下面的示例先打开一个新会话，然后将 *Autoexists=3* 属性添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="69cd5-303">The following example begins by opening a new session and adding the *Autoexists=3* property to the connection string.</span></span> <span data-ttu-id="69cd5-304">必须打开新连接才能执行该示例。</span><span class="sxs-lookup"><span data-stu-id="69cd5-304">You must open a new connection in order to do the example.</span></span> <span data-ttu-id="69cd5-305">在与 Autoexist 设置建立连接后，设置将一直有效，直到该连接结束。</span><span class="sxs-lookup"><span data-stu-id="69cd5-305">Once the connection is established with the Autoexist setting it will remain in effect until that connection is finished.</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="69cd5-306">下面的结果集现在显示 Autoexists 的浅表行为。</span><span class="sxs-lookup"><span data-stu-id="69cd5-306">The following result set now shows the shallow behavior of Autoexists.</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="69cd5-307">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-307">**Reseller Sales Amount**</span></span>|<span data-ttu-id="69cd5-308">**Discount Amount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-308">**Discount Amount**</span></span>|<span data-ttu-id="69cd5-309">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="69cd5-309">**PCT Discount**</span></span>|  
|<span data-ttu-id="69cd5-310">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="69cd5-310">**Mountain-200**</span></span>|<span data-ttu-id="69cd5-311">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="69cd5-311">**$14,356,699.36**</span></span>|<span data-ttu-id="69cd5-312">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="69cd5-312">**$19,012.71**</span></span>|<span data-ttu-id="69cd5-313">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-313">**0.13%**</span></span>|  
|<span data-ttu-id="69cd5-314">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="69cd5-314">**Mountain-100**</span></span>|<span data-ttu-id="69cd5-315">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-315">**$8,568,958.27**</span></span>|<span data-ttu-id="69cd5-316">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-316">**$139,393.27**</span></span>|<span data-ttu-id="69cd5-317">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-317">**1.63%**</span></span>|  
|<span data-ttu-id="69cd5-318">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="69cd5-318">**HL Mountain Frame**</span></span>|<span data-ttu-id="69cd5-319">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="69cd5-319">**$3,365,069.27**</span></span>|<span data-ttu-id="69cd5-320">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="69cd5-320">**$174.11**</span></span>|<span data-ttu-id="69cd5-321">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="69cd5-321">**0.01%**</span></span>|  
  
 <span data-ttu-id="69cd5-322">使用连接字符串中的 AUTOEXISTS = [1 | 2 | 3] 参数可以修改 Autoexists 行为;[&#40;xmla&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)和参数用法，请参阅支持的 xmla 属性 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="69cd5-322">Autoexists behavior can be modified by using the AUTOEXISTS=[1|2|3] parameter in the connection string; see [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) and <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> for parameter usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69cd5-323">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69cd5-323">See Also</span></span>  
 <span data-ttu-id="69cd5-324">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="69cd5-324">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="69cd5-325">[多维数据集空间](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="69cd5-325">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="69cd5-326">[元](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="69cd5-326">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="69cd5-327">[使用成员、元组和集 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="69cd5-327">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="69cd5-328">[直观合计和非直观合计](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="69cd5-328">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="69cd5-329">[Mdx 语言参考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="69cd5-329">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="69cd5-330">多维表达式 (MDX) 参考</span><span class="sxs-lookup"><span data-stu-id="69cd5-330">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
