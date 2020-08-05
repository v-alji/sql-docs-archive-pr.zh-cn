---
title: 了解传递顺序和求解次序 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- evaluation order [MDX]
- calculation order [MDX]
- SOLVE_ORDER property
- queries [MDX], solve orders
- solve orders [MDX]
- pass orders [MDX]
- expressions [MDX], solve orders
ms.assetid: 7ed7d4ee-4644-4c5d-99a4-c4b429d0203c
author: minewiskan
ms.author: owend
ms.openlocfilehash: d92ccd9d1eeb05272a95c6f429f8c756bcb0022e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580931"
---
# <a name="understanding-pass-order-and-solve-order-mdx"></a><span data-ttu-id="dffc9-102">理解传递次序和求解次序 (MDX)</span><span class="sxs-lookup"><span data-stu-id="dffc9-102">Understanding Pass Order and Solve Order (MDX)</span></span>
  <span data-ttu-id="dffc9-103">当某个多维数据集是 MDX 脚本的计算结果时，该多维数据集可能会经历许多计算阶段，具体取决于与计算有关的各种功能的使用情况。</span><span class="sxs-lookup"><span data-stu-id="dffc9-103">When a cube is calculated as the result of an MDX script, it can go through many stages of computation depending on the use of various calculation-related features.</span></span> <span data-ttu-id="dffc9-104">每个阶段称为一个计算传递。</span><span class="sxs-lookup"><span data-stu-id="dffc9-104">Each of these stages is referred to as a calculation pass.</span></span>  
  
 <span data-ttu-id="dffc9-105">计算传递可以按序号位置（称为“计算传递号”）进行引用。</span><span class="sxs-lookup"><span data-stu-id="dffc9-105">A calculation pass can be referred to by an ordinal position, called the calculation pass number.</span></span> <span data-ttu-id="dffc9-106">完全计算一个多维数据集中的所有单元所需的计算传递数称为多维数据集的计算传递深度。</span><span class="sxs-lookup"><span data-stu-id="dffc9-106">The count of calculation passes that are required to fully compute all the cells of a cube is referred to as the calculation pass depth of the cube.</span></span>  
  
 <span data-ttu-id="dffc9-107">事实数据表和写回数据仅影响传递 0。</span><span class="sxs-lookup"><span data-stu-id="dffc9-107">Fact table and writeback data only impact pass 0.</span></span> <span data-ttu-id="dffc9-108">脚本将在传递 0 后填充数据，脚本中的每一个赋值和计算语句都将创建一个新的传递。</span><span class="sxs-lookup"><span data-stu-id="dffc9-108">Scripts populate data after pass 0; each assignment and calculate statement in a script creates a new pass.</span></span> <span data-ttu-id="dffc9-109">在 MDX 脚本外，对绝对传递 0 的引用将引用脚本为多维数据集创建的最后一个传递。</span><span class="sxs-lookup"><span data-stu-id="dffc9-109">Outside the MDX script, references to absolute pass 0 refer to the last pass created by the script for the cube.</span></span>  
  
 <span data-ttu-id="dffc9-110">在所有传递中都会创建计算成员，但表达式只应用于当前传递。</span><span class="sxs-lookup"><span data-stu-id="dffc9-110">Calculated members are created at all passes, but the expression is applied at the current pass.</span></span> <span data-ttu-id="dffc9-111">之前的传递包含计算度量值，但是值为空。</span><span class="sxs-lookup"><span data-stu-id="dffc9-111">Prior passes contain the calculated measure, but with a null value.</span></span>  
  
## <a name="solve-order"></a><span data-ttu-id="dffc9-112">求解次序</span><span class="sxs-lookup"><span data-stu-id="dffc9-112">Solve Order</span></span>  
 <span data-ttu-id="dffc9-113">求解次序决定了出现相互竞争的表达式时的计算优先级。</span><span class="sxs-lookup"><span data-stu-id="dffc9-113">Solve order determines the priority of calculation in the event of competing expressions.</span></span> <span data-ttu-id="dffc9-114">在一个传递中，求解次序决定了两点：</span><span class="sxs-lookup"><span data-stu-id="dffc9-114">Within a single pass, solve order determines two things:</span></span>  
  
-   <span data-ttu-id="dffc9-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 计算维度、成员、计算成员、自定义汇总和计算单元的顺序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-115">The order in which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates dimensions, members, calculated members, custom rollups, and calculated cells.</span></span>  
  
-   <span data-ttu-id="dffc9-116">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 计算自定义成员、计算成员、自定义汇总和计算单元的次序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-116">The order in which [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates custom members, calculated members, custom rollup, and calculated cells.</span></span>  
  
 <span data-ttu-id="dffc9-117">具有最高求解次序的成员优先。</span><span class="sxs-lookup"><span data-stu-id="dffc9-117">The member with the highest solve order takes precedence.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dffc9-118">此优先级的例外情况是聚合函数。</span><span class="sxs-lookup"><span data-stu-id="dffc9-118">The exception to this precedence is the Aggregate function.</span></span> <span data-ttu-id="dffc9-119">与聚合函数一起使用的计算成员的求解次序比任何相交的计算度量值都低。</span><span class="sxs-lookup"><span data-stu-id="dffc9-119">Calculated members with the Aggregate function have a lower solve order than any intersecting calculated measure.</span></span>  
  
## <a name="solve-order-values-and-precedence"></a><span data-ttu-id="dffc9-120">求解次序值和优先级</span><span class="sxs-lookup"><span data-stu-id="dffc9-120">Solve Order Values and Precedence</span></span>  
 <span data-ttu-id="dffc9-121">求解次序值的范围为 -8181 到 65535。</span><span class="sxs-lookup"><span data-stu-id="dffc9-121">Solve order values can range from -8181 to 65535.</span></span> <span data-ttu-id="dffc9-122">在此范围内，有些求解次序值对应于特定类型的计算，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="dffc9-122">In this range, some solve order values correspond to specific kinds of calculations, as shown in the following table.</span></span>  
  
|<span data-ttu-id="dffc9-123">计算</span><span class="sxs-lookup"><span data-stu-id="dffc9-123">Calculation</span></span>|<span data-ttu-id="dffc9-124">求解次序</span><span class="sxs-lookup"><span data-stu-id="dffc9-124">Solve Order</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="dffc9-125">自定义成员公式</span><span class="sxs-lookup"><span data-stu-id="dffc9-125">Custom member formulas</span></span>|<span data-ttu-id="dffc9-126">-5119</span><span class="sxs-lookup"><span data-stu-id="dffc9-126">-5119</span></span>|  
|<span data-ttu-id="dffc9-127">一元运算符</span><span class="sxs-lookup"><span data-stu-id="dffc9-127">Unary operators</span></span>|<span data-ttu-id="dffc9-128">-5119</span><span class="sxs-lookup"><span data-stu-id="dffc9-128">-5119</span></span>|  
|<span data-ttu-id="dffc9-129">直观合计计算</span><span class="sxs-lookup"><span data-stu-id="dffc9-129">Visual totals calculation</span></span>|<span data-ttu-id="dffc9-130">-4096</span><span class="sxs-lookup"><span data-stu-id="dffc9-130">-4096</span></span>|  
|<span data-ttu-id="dffc9-131">所有其他计算（如果没有另行指定）</span><span class="sxs-lookup"><span data-stu-id="dffc9-131">All other calculations (if not otherwise specified)</span></span>|<span data-ttu-id="dffc9-132">0</span><span class="sxs-lookup"><span data-stu-id="dffc9-132">0</span></span>|  
  
 <span data-ttu-id="dffc9-133">强烈建议设置求解次序值时仅使用正整数。</span><span class="sxs-lookup"><span data-stu-id="dffc9-133">It is highly recommended that you use only positive integers when setting solve order values.</span></span> <span data-ttu-id="dffc9-134">如果赋值小于上表中所示的求解次序值，计算传递可能会变得不可预知。</span><span class="sxs-lookup"><span data-stu-id="dffc9-134">If you assign values that are lower than the solve order values shown in the previous table, the calculation pass can become unpredictable.</span></span> <span data-ttu-id="dffc9-135">例如，计算成员的计算接收的求解次序值小于默认自定义汇总公式值 -5119。</span><span class="sxs-lookup"><span data-stu-id="dffc9-135">For example, the calculation for a calculated member receives a solve order value that is lower than the default custom rollup formula value of -5119.</span></span> <span data-ttu-id="dffc9-136">这样一个低的求解次序值会导致计算成员在自定义汇总公式之前计算，并产生错误的结果。</span><span class="sxs-lookup"><span data-stu-id="dffc9-136">Such a low solve order value causes the calculated members to be calculated before the custom rollup formulas, and can produce incorrect results.</span></span>  
  
### <a name="creating-and-changing-solve-order"></a><span data-ttu-id="dffc9-137">创建和更改求解次序</span><span class="sxs-lookup"><span data-stu-id="dffc9-137">Creating and Changing Solve Order</span></span>  
 <span data-ttu-id="dffc9-138">在多维数据集设计器的 **“计算”** 窗格上，可以通过更改计算顺序来更改计算成员和计算单元的求解次序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-138">In Cube Designer, on the **Calculations Pane**, you can change the solve order for calculated members and calculated cells by changing the order of the calculations.</span></span>  
  
 <span data-ttu-id="dffc9-139">在 MDX 中，可以使用 `SOLVE_ORDER` 关键字来创建或更改计算成员和计算单元。</span><span class="sxs-lookup"><span data-stu-id="dffc9-139">In MDX, you can use the `SOLVE_ORDER` keyword to create or change calculated members and calculated cells.</span></span>  
  
## <a name="solve-order-examples"></a><span data-ttu-id="dffc9-140">求解次序示例</span><span class="sxs-lookup"><span data-stu-id="dffc9-140">Solve Order Examples</span></span>  
 <span data-ttu-id="dffc9-141">为了说明求解次序可能具有的复杂性，下面的系列 MDX 查询将以两个本身没有求解次序问题的查询开始，</span><span class="sxs-lookup"><span data-stu-id="dffc9-141">To illustrate the potential complexities of solve order, the following series of MDX queries starts with two queries that each individually have no solve order issues.</span></span> <span data-ttu-id="dffc9-142">然后将这两个查询合并成一个需要求解次序的查询。</span><span class="sxs-lookup"><span data-stu-id="dffc9-142">These two queries are then combined into a query that requires solve order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dffc9-143">您可以针对 Adventure Works 示例多维数据库运行这些 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="dffc9-143">You can run these MDX queries against the Adventure Works sample multidimensional database.</span></span> <span data-ttu-id="dffc9-144">可以从 codeplex 站点下载 [AdventureWorks 多维模型 SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) 示例。</span><span class="sxs-lookup"><span data-stu-id="dffc9-144">You can download the [AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) sample from the codeplex site.</span></span>  
  
### <a name="query-1-differences-in-income-and-expenses"></a><span data-ttu-id="dffc9-145">查询 1-收入与支出之间的差异</span><span class="sxs-lookup"><span data-stu-id="dffc9-145">Query 1-Differences in Income and Expenses</span></span>  
 <span data-ttu-id="dffc9-146">对于第一个 MDX 查询，通过构造一个与以下示例类似的简单 MDX 查询，计算每年的销售与成本之间的差额：</span><span class="sxs-lookup"><span data-stu-id="dffc9-146">For the first MDX query, calculate the difference in sales and costs for each year by constructing a simple MDX query similar to the following example:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] )  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="dffc9-147">在此查询中，只有一个计算成员 `Year Difference`。</span><span class="sxs-lookup"><span data-stu-id="dffc9-147">In this query, there is only one calculated member, `Year Difference`.</span></span> <span data-ttu-id="dffc9-148">因为只有一个计算成员，所以只要多维数据集不使用任何计算成员，求解次序就不是问题。</span><span class="sxs-lookup"><span data-stu-id="dffc9-148">Because there is only one calculated member, solve order is not an issue, as long as the cube does not use any calculated members.</span></span>  
  
 <span data-ttu-id="dffc9-149">此 MDX 查询将生成一个类似于下表的结果集。</span><span class="sxs-lookup"><span data-stu-id="dffc9-149">This MDX query produces a result set similar to the following table.</span></span>  
  
||<span data-ttu-id="dffc9-150">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="dffc9-150">Internet Sales Amount</span></span>|<span data-ttu-id="dffc9-151">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="dffc9-151">Internet Total Product Cost</span></span>|  
|-|---------------------------|---------------------------------|  
|<span data-ttu-id="dffc9-152">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="dffc9-152">**CY 2007**</span></span>|<span data-ttu-id="dffc9-153">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="dffc9-153">$9,791,060.30</span></span>|<span data-ttu-id="dffc9-154">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="dffc9-154">$5,718,327.17</span></span>|  
|<span data-ttu-id="dffc9-155">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="dffc9-155">**CY 2008**</span></span>|<span data-ttu-id="dffc9-156">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="dffc9-156">$9,770,899.74</span></span>|<span data-ttu-id="dffc9-157">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="dffc9-157">$5,721,205.24</span></span>|  
|<span data-ttu-id="dffc9-158">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="dffc9-158">**Year Difference**</span></span>|<span data-ttu-id="dffc9-159">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="dffc9-159">($20,160.56)</span></span>|<span data-ttu-id="dffc9-160">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="dffc9-160">$2,878.06</span></span>|  
  
### <a name="query-2-percentage-of-income-after-expenses"></a><span data-ttu-id="dffc9-161">查询 2-支出后的收益百分比</span><span class="sxs-lookup"><span data-stu-id="dffc9-161">Query 2-Percentage of Income after Expenses</span></span>  
 <span data-ttu-id="dffc9-162">对于第二个查询，通过使用下面的 MDX 查询，计算每年扣除支出后的收益百分比：</span><span class="sxs-lookup"><span data-stu-id="dffc9-162">For the second query, calculate the percentage of income after expenses for each year using the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Measures].[Profit Margin] AS   
([Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent"  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="dffc9-163">与上一个查询类似，此 MDX 查询只有一个计算成员 `Profit Margin`，因此也不会有任何求解次序问题。</span><span class="sxs-lookup"><span data-stu-id="dffc9-163">This MDX query, like the previous one, has only a single calculated member, `Profit Margin`, and therefore does not have any solve order complications.</span></span>  
  
 <span data-ttu-id="dffc9-164">此 MDX 查询将生成一个类似于下表的略有不同的结果集。</span><span class="sxs-lookup"><span data-stu-id="dffc9-164">This MDX query produces a slightly different result set, similar to the following table.</span></span>  
  
||<span data-ttu-id="dffc9-165">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="dffc9-165">Internet Sales Amount</span></span>|<span data-ttu-id="dffc9-166">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="dffc9-166">Internet Total Product Cost</span></span>|<span data-ttu-id="dffc9-167">Profit Margin</span><span class="sxs-lookup"><span data-stu-id="dffc9-167">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="dffc9-168">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="dffc9-168">**CY 2007**</span></span>|<span data-ttu-id="dffc9-169">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="dffc9-169">$9,791,060.30</span></span>|<span data-ttu-id="dffc9-170">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="dffc9-170">$5,718,327.17</span></span>|<span data-ttu-id="dffc9-171">41.60%</span><span class="sxs-lookup"><span data-stu-id="dffc9-171">41.60%</span></span>|  
|<span data-ttu-id="dffc9-172">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="dffc9-172">**CY 2008**</span></span>|<span data-ttu-id="dffc9-173">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="dffc9-173">$9,770,899.74</span></span>|<span data-ttu-id="dffc9-174">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="dffc9-174">$5,721,205.24</span></span>|<span data-ttu-id="dffc9-175">41.45%</span><span class="sxs-lookup"><span data-stu-id="dffc9-175">41.45%</span></span>|  
  
 <span data-ttu-id="dffc9-176">第一个查询与第二个查询在结果集方面的差异来自计算成员位置的不同。</span><span class="sxs-lookup"><span data-stu-id="dffc9-176">The difference in result sets between the first query and the second query comes from the difference in placement of the calculated member.</span></span> <span data-ttu-id="dffc9-177">在第一个查询中，计算成员是 ROWS 轴的一部分，而在第二个查询中，计算成员是 COLUMNS 轴的一部分。</span><span class="sxs-lookup"><span data-stu-id="dffc9-177">In the first query, the calculated member is part of the ROWS axis, not the COLUMNS axis shown in the second query.</span></span> <span data-ttu-id="dffc9-178">下一个查询将两个计算成员合并到一个 MDX 查询中，这种位置上的不同在这个查询中就会变得非常重要。</span><span class="sxs-lookup"><span data-stu-id="dffc9-178">This difference in placement becomes important in the next query, which combines the two calculated members in a single MDX query.</span></span>  
  
### <a name="query-3-combined-year-difference-and-net-income-calculations"></a><span data-ttu-id="dffc9-179">查询 3-组合年份差额和净收益计算</span><span class="sxs-lookup"><span data-stu-id="dffc9-179">Query 3-Combined Year Difference and Net Income Calculations</span></span>  
 <span data-ttu-id="dffc9-180">在最后这个查询中，将上面两个示例合并成一个 MDX 查询，此时由于要同时对列和行进行计算，因此求解次序变得重要起来。</span><span class="sxs-lookup"><span data-stu-id="dffc9-180">In this final query combining both of the previous examples into a single MDX query, solve order becomes important because of the calculations on both columns and rows.</span></span> <span data-ttu-id="dffc9-181">为了确保按正确的顺序进行计算，请使用 `SOLVE_ORDER` 关键字定义进行计算的顺序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-181">To make sure that the calculations occur in the correct sequence, define the sequence in which the calculations occur by using the `SOLVE_ORDER` keyword.</span></span>  
  
 <span data-ttu-id="dffc9-182">`SOLVE_ORDER` 关键字指定 MDX 查询或 `CREATE MEMBER` 命令中计算成员的求解次序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-182">The `SOLVE_ORDER` keyword specifies the solve order of calculated members in an MDX query or a `CREATE MEMBER` command.</span></span> <span data-ttu-id="dffc9-183">`SOLVE_ORDER` 关键字使用的整数值是相对的，不要求从零开始，也不要求是连续的。</span><span class="sxs-lookup"><span data-stu-id="dffc9-183">The integer values used with the `SOLVE_ORDER` keyword are relative, do not need to start at zero, and do not need to be consecutive.</span></span> <span data-ttu-id="dffc9-184">该值只是告诉 MDX 基于通过计算具有较大求解次序值的成员得出的值来计算成员。</span><span class="sxs-lookup"><span data-stu-id="dffc9-184">The value simply tells MDX to calculate a member based on values derived from calculating members with a higher value.</span></span> <span data-ttu-id="dffc9-185">如果不使用 `SOLVE_ORDER` 关键字定义计算成员，计算成员的默认值将为零。</span><span class="sxs-lookup"><span data-stu-id="dffc9-185">If a calculated member is defined without the `SOLVE_ORDER` keyword, the default value of that calculated member is zero.</span></span>  
  
 <span data-ttu-id="dffc9-186">例如，如果合并前面两个查询示例中使用的计算，则两个计算成员 `Year Difference` 和 `Profit Margin`将相交于 MDX 查询示例的结果数据集中的一个单元中。</span><span class="sxs-lookup"><span data-stu-id="dffc9-186">For example, if you combine the calculations used in the first two example queries, the two calculated members, `Year Difference` and `Profit Margin`, intersect at a single cell in the result dataset of the MDX query example.</span></span> <span data-ttu-id="dffc9-187">确定 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 如何计算此单元的唯一方式是通过求解次序。</span><span class="sxs-lookup"><span data-stu-id="dffc9-187">The only way to determine how [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] will evaluate this cell is by the solve order.</span></span> <span data-ttu-id="dffc9-188">根据两个计算成员的求解次序，用于构造此单元的公式将生成不同的结果。</span><span class="sxs-lookup"><span data-stu-id="dffc9-188">The formulas that are used to construct this cell will produce different results depending upon the solve order of the two calculated members.</span></span>  
  
 <span data-ttu-id="dffc9-189">首先，尝试将前面两个查询中使用的计算合并到下面的 MDX 查询中：</span><span class="sxs-lookup"><span data-stu-id="dffc9-189">First, try combining the calculations used in the first two queries in the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 1  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 2  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="dffc9-190">在这个合并的 MDX 查询示例中， `Profit Margin` 具有最高的求解次序，因此当两个表达式会相互影响时，它具有优先权。</span><span class="sxs-lookup"><span data-stu-id="dffc9-190">In this combined MDX query example, `Profit Margin` has the highest solve order, so it takes precedence when the two expressions interact.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="dffc9-191">使用 `Profit Margin` 公式计算相关的单元。</span><span class="sxs-lookup"><span data-stu-id="dffc9-191">evaluates the cell in question by using the `Profit Margin` formula.</span></span> <span data-ttu-id="dffc9-192">此嵌套计算的结果如下表所示。</span><span class="sxs-lookup"><span data-stu-id="dffc9-192">The results of this nested calculation, as shown in the following table.</span></span>  
  
||<span data-ttu-id="dffc9-193">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="dffc9-193">Internet Sales Amount</span></span>|<span data-ttu-id="dffc9-194">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="dffc9-194">Internet Total Product Cost</span></span>|<span data-ttu-id="dffc9-195">Profit Margin</span><span class="sxs-lookup"><span data-stu-id="dffc9-195">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="dffc9-196">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="dffc9-196">**CY 2007**</span></span>|<span data-ttu-id="dffc9-197">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="dffc9-197">$9,791,060.30</span></span>|<span data-ttu-id="dffc9-198">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="dffc9-198">$5,718,327.17</span></span>|<span data-ttu-id="dffc9-199">41.60%</span><span class="sxs-lookup"><span data-stu-id="dffc9-199">41.60%</span></span>|  
|<span data-ttu-id="dffc9-200">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="dffc9-200">**CY 2008**</span></span>|<span data-ttu-id="dffc9-201">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="dffc9-201">$9,770,899.74</span></span>|<span data-ttu-id="dffc9-202">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="dffc9-202">$5,721,205.24</span></span>|<span data-ttu-id="dffc9-203">41.45%</span><span class="sxs-lookup"><span data-stu-id="dffc9-203">41.45%</span></span>|  
|<span data-ttu-id="dffc9-204">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="dffc9-204">**Year Difference**</span></span>|<span data-ttu-id="dffc9-205">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="dffc9-205">($20,160.56)</span></span>|<span data-ttu-id="dffc9-206">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="dffc9-206">$2,878.06</span></span>|<span data-ttu-id="dffc9-207">114.28%</span><span class="sxs-lookup"><span data-stu-id="dffc9-207">114.28%</span></span>|  
  
 <span data-ttu-id="dffc9-208">共享单元中的结果基于 `Profit Margin`所用的公式。</span><span class="sxs-lookup"><span data-stu-id="dffc9-208">The result in the shared cell is based on the formula for `Profit Margin`.</span></span> <span data-ttu-id="dffc9-209">也就是说， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 使用 `Year Difference` 数据计算共享单元中的结果，这样就会得到以下公式（为清楚起见，对结果进行了舍入）：</span><span class="sxs-lookup"><span data-stu-id="dffc9-209">That is, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell with the `Year Difference` data, producing the following formula (the result is rounded for clarity):</span></span>  
  
```  
((9,770,899.74 - 9,791,060.30) - (5,721,205.24 - 5,718,327.17)) / (9,770,899.74 - 9,791,060.30) = 1.14275744   
```  
  
 <span data-ttu-id="dffc9-210">或</span><span class="sxs-lookup"><span data-stu-id="dffc9-210">or</span></span>  
  
```  
(23,038.63) / (20,160.56) = 114.28%  
```  
  
 <span data-ttu-id="dffc9-211">这明显是错误的。</span><span class="sxs-lookup"><span data-stu-id="dffc9-211">This is clearly incorrect.</span></span> <span data-ttu-id="dffc9-212">但是，如果您切换了 MDX 查询中计算成员的求解次序， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将以不同的方式计算共享单元中的结果。</span><span class="sxs-lookup"><span data-stu-id="dffc9-212">However, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell differently if you switch the solve orders for the calculated members in the MDX query.</span></span> <span data-ttu-id="dffc9-213">下面合并的 MDX 查询反转了计算成员的求解次序：</span><span class="sxs-lookup"><span data-stu-id="dffc9-213">The following combined MDX query reverses the solve order for the calculated members:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 2  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 1  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="dffc9-214">由于已经切换了计算成员的求解次序，因此 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将使用 `Year Difference` 公式来计算此单元，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="dffc9-214">As the order of the calculated members has been switched, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the `Year Difference` formula to evaluate the cell, as shown in the following table.</span></span>  
  
||<span data-ttu-id="dffc9-215">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="dffc9-215">Internet Sales Amount</span></span>|<span data-ttu-id="dffc9-216">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="dffc9-216">Internet Total Product Cost</span></span>|<span data-ttu-id="dffc9-217">Profit Margin</span><span class="sxs-lookup"><span data-stu-id="dffc9-217">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="dffc9-218">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="dffc9-218">**CY 2007**</span></span>|<span data-ttu-id="dffc9-219">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="dffc9-219">$9,791,060.30</span></span>|<span data-ttu-id="dffc9-220">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="dffc9-220">$5,718,327.17</span></span>|<span data-ttu-id="dffc9-221">41.60%</span><span class="sxs-lookup"><span data-stu-id="dffc9-221">41.60%</span></span>|  
|<span data-ttu-id="dffc9-222">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="dffc9-222">**CY 2008**</span></span>|<span data-ttu-id="dffc9-223">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="dffc9-223">$9,770,899.74</span></span>|<span data-ttu-id="dffc9-224">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="dffc9-224">$5,721,205.24</span></span>|<span data-ttu-id="dffc9-225">41.45%</span><span class="sxs-lookup"><span data-stu-id="dffc9-225">41.45%</span></span>|  
|<span data-ttu-id="dffc9-226">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="dffc9-226">**Year Difference**</span></span>|<span data-ttu-id="dffc9-227">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="dffc9-227">($20,160.56)</span></span>|<span data-ttu-id="dffc9-228">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="dffc9-228">$2,878.06</span></span>|<span data-ttu-id="dffc9-229">(0.15%)</span><span class="sxs-lookup"><span data-stu-id="dffc9-229">(0.15%)</span></span>|  
  
 <span data-ttu-id="dffc9-230">因为此查询对 `Year Difference` 数据使用 `Profit Margin` 公式，所以共享单元的公式与以下计算类似：</span><span class="sxs-lookup"><span data-stu-id="dffc9-230">Because this query uses the `Year Difference` formula with the `Profit Margin` data, the formula for the shared cell resembles the following calculation:</span></span>  
  
```  
(($9,770,899.74 - 5,721,205.24) / $9,770,899.74) - ((9,791,060.30 - 5,718,327.17) / 9,791,060.30) = -0.15   
```  
  
 <span data-ttu-id="dffc9-231">或</span><span class="sxs-lookup"><span data-stu-id="dffc9-231">Or</span></span>  
  
```  
0.4145 - 0.4160= -0.15  
```  
  
## <a name="additional-considerations"></a><span data-ttu-id="dffc9-232">其他注意事项</span><span class="sxs-lookup"><span data-stu-id="dffc9-232">Additional Considerations</span></span>  
 <span data-ttu-id="dffc9-233">求解次序可能会成为需要处理的非常复杂的问题，尤其是在具有很多维度而维度涉及计算成员、自定义汇总公式或计算单元的多维数据集中，更是如此。</span><span class="sxs-lookup"><span data-stu-id="dffc9-233">Solve order can be a very complex issue to deal with, especially in cubes with a high number of dimensions involving calculated member, custom rollup formulas, or calculated cells.</span></span> <span data-ttu-id="dffc9-234">当 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 计算 MDX 查询时， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 将考虑给定传递中涉及的所有内容的求解次序值，包括 MDX 查询中指定的多维数据集的维度。</span><span class="sxs-lookup"><span data-stu-id="dffc9-234">When [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates an MDX query, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] takes into account the solve order values for everything involved within a given pass, including the dimensions of the cube specified in the MDX query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffc9-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dffc9-235">See Also</span></span>  
 <span data-ttu-id="dffc9-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span><span class="sxs-lookup"><span data-stu-id="dffc9-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span></span>  
 <span data-ttu-id="dffc9-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span><span class="sxs-lookup"><span data-stu-id="dffc9-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span></span>  
 <span data-ttu-id="dffc9-238">[CREATE MEMBER 语句 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="dffc9-238">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 [<span data-ttu-id="dffc9-239">操作数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="dffc9-239">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
