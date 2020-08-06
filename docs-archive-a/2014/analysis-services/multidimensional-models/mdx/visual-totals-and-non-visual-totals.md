---
title: 直观合计和非直观合计 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ddff047be6a819d05276848cbeb430fb8e4c9c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691940"
---
# <a name="visual-totals-and-non-visual-totals"></a><span data-ttu-id="39b26-102">直观合计和非直观合计</span><span class="sxs-lookup"><span data-stu-id="39b26-102">Visual Totals and Non Visual Totals</span></span>
  <span data-ttu-id="39b26-103">直观合计是位于列尾或行尾的合计，它将列或行中可见的所有项相加。</span><span class="sxs-lookup"><span data-stu-id="39b26-103">Visual Totals are totals at the end of a column or row that add up all of the items visible in the column or row.</span></span> <span data-ttu-id="39b26-104">这是大多数表在显示时的默认行为。</span><span class="sxs-lookup"><span data-stu-id="39b26-104">This is the default behavior for most tables when displayed.</span></span> <span data-ttu-id="39b26-105">但有一些情况，用户想要只显示表中的某些列，但保留针对整个行的合计，包括那些未显示的行。</span><span class="sxs-lookup"><span data-stu-id="39b26-105">However, there are times when the user wants to display only certain columns in a table but keep the totals for the entire row, including those that are not displayed.</span></span> <span data-ttu-id="39b26-106">这称作 `Non Visual Totals`，因为合计来自可见值以及非可见值。</span><span class="sxs-lookup"><span data-stu-id="39b26-106">These are called `Non Visual Totals`, because the total comes from both the visible and non-visible values.</span></span>  
  
 <span data-ttu-id="39b26-107">下面的应用场景对非直观合计的行为进行了演示。</span><span class="sxs-lookup"><span data-stu-id="39b26-107">The following scenario demonstrates the behavior of Non Visual totals.</span></span> <span data-ttu-id="39b26-108">第一步显示直观合计的默认行为。</span><span class="sxs-lookup"><span data-stu-id="39b26-108">The first step shows the default behavior of Visual Totals.</span></span>  
  
 <span data-ttu-id="39b26-109">下面的示例用于查询 [Adventure Works]，以获取表中的 [Reseller Sales Amount] 数字，在该表中产品类别为列，分销商业务类型为行。</span><span class="sxs-lookup"><span data-stu-id="39b26-109">The following example is a query of [Adventure Works] to obtain [Reseller Sales Amount] figures in a table where the product categories are the columns and the reseller business types are the rows.</span></span> <span data-ttu-id="39b26-110">请注意，合计是在发出以下 SELECT 语句时为产品和分销商给出的：</span><span class="sxs-lookup"><span data-stu-id="39b26-110">Note that totals are given for both products and resellers when the following SELECT statement is issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="39b26-111">产生以下结果：</span><span class="sxs-lookup"><span data-stu-id="39b26-111">Produces the following results:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="39b26-112">**所有产品**</span><span class="sxs-lookup"><span data-stu-id="39b26-112">**All Products**</span></span>|<span data-ttu-id="39b26-113">**配件**</span><span class="sxs-lookup"><span data-stu-id="39b26-113">**Accessories**</span></span>|<span data-ttu-id="39b26-114">**自行车**</span><span class="sxs-lookup"><span data-stu-id="39b26-114">**Bikes**</span></span>|<span data-ttu-id="39b26-115">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="39b26-115">**Clothing**</span></span>|<span data-ttu-id="39b26-116">**组件**</span><span class="sxs-lookup"><span data-stu-id="39b26-116">**Components**</span></span>|  
|<span data-ttu-id="39b26-117">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="39b26-117">**All Resellers**</span></span>|<span data-ttu-id="39b26-118">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="39b26-118">**$80,450,596.98**</span></span>|<span data-ttu-id="39b26-119">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="39b26-119">**$571,297.93**</span></span>|<span data-ttu-id="39b26-120">**$66,302,381.56**</span><span class="sxs-lookup"><span data-stu-id="39b26-120">**$66,302,381.56**</span></span>|<span data-ttu-id="39b26-121">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="39b26-121">**$1,777,840.84**</span></span>|<span data-ttu-id="39b26-122">**$11,799,076.66**</span><span class="sxs-lookup"><span data-stu-id="39b26-122">**$11,799,076.66**</span></span>|  
|<span data-ttu-id="39b26-123">**Specialty Bike Shop**</span><span class="sxs-lookup"><span data-stu-id="39b26-123">**Specialty Bike Shop**</span></span>|<span data-ttu-id="39b26-124">**$6,756,166.18**</span><span class="sxs-lookup"><span data-stu-id="39b26-124">**$6,756,166.18**</span></span>|<span data-ttu-id="39b26-125">**$65,125.48**</span><span class="sxs-lookup"><span data-stu-id="39b26-125">**$65,125.48**</span></span>|<span data-ttu-id="39b26-126">**$6,080,117.73**</span><span class="sxs-lookup"><span data-stu-id="39b26-126">**$6,080,117.73**</span></span>|<span data-ttu-id="39b26-127">**$252,933.91**</span><span class="sxs-lookup"><span data-stu-id="39b26-127">**$252,933.91**</span></span>|<span data-ttu-id="39b26-128">**$357,989.07**</span><span class="sxs-lookup"><span data-stu-id="39b26-128">**$357,989.07**</span></span>|  
|<span data-ttu-id="39b26-129">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="39b26-129">**Value Added Reseller**</span></span>|<span data-ttu-id="39b26-130">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="39b26-130">**$34,967,517.33**</span></span>|<span data-ttu-id="39b26-131">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="39b26-131">**$175,002.81**</span></span>|<span data-ttu-id="39b26-132">**$30,892,354.33**</span><span class="sxs-lookup"><span data-stu-id="39b26-132">**$30,892,354.33**</span></span>|<span data-ttu-id="39b26-133">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="39b26-133">**$592,385.71**</span></span>|<span data-ttu-id="39b26-134">**$3,307,774.48**</span><span class="sxs-lookup"><span data-stu-id="39b26-134">**$3,307,774.48**</span></span>|  
|<span data-ttu-id="39b26-135">**仓库**</span><span class="sxs-lookup"><span data-stu-id="39b26-135">**Warehouse**</span></span>|<span data-ttu-id="39b26-136">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="39b26-136">**$38,726,913.48**</span></span>|<span data-ttu-id="39b26-137">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="39b26-137">**$331,169.64**</span></span>|<span data-ttu-id="39b26-138">**$29,329,909.50**</span><span class="sxs-lookup"><span data-stu-id="39b26-138">**$29,329,909.50**</span></span>|<span data-ttu-id="39b26-139">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="39b26-139">**$932,521.23**</span></span>|<span data-ttu-id="39b26-140">**$8,133,313.11**</span><span class="sxs-lookup"><span data-stu-id="39b26-140">**$8,133,313.11**</span></span>|  
  
## <a name="non-visual-on-rows-and-columns"></a><span data-ttu-id="39b26-141">针对行和列的非直观合计</span><span class="sxs-lookup"><span data-stu-id="39b26-141">Non-Visual on rows and columns</span></span>  
 <span data-ttu-id="39b26-142">要生成一个仅具有“附件”和“服装”产品、“增值分销商”和“仓库分销商”数据的表，但仍保留总合计，则使用 NON VISUAL 编写如下语句：</span><span class="sxs-lookup"><span data-stu-id="39b26-142">To produce a table with data only for the Accessories and Clothing products, the Value Added Reseller and Warehouse resellers, yet keeping the overall totals could be written as follows using NON VISUAL:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="39b26-143">产生以下结果：</span><span class="sxs-lookup"><span data-stu-id="39b26-143">Produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="39b26-144">**所有产品**</span><span class="sxs-lookup"><span data-stu-id="39b26-144">**All Products**</span></span>|<span data-ttu-id="39b26-145">**配件**</span><span class="sxs-lookup"><span data-stu-id="39b26-145">**Accessories**</span></span>|<span data-ttu-id="39b26-146">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="39b26-146">**Clothing**</span></span>|  
|<span data-ttu-id="39b26-147">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="39b26-147">**All Resellers**</span></span>|<span data-ttu-id="39b26-148">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="39b26-148">**$80,450,596.98**</span></span>|<span data-ttu-id="39b26-149">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="39b26-149">**$571,297.93**</span></span>|<span data-ttu-id="39b26-150">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="39b26-150">**$1,777,840.84**</span></span>|  
|<span data-ttu-id="39b26-151">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="39b26-151">**Value Added Reseller**</span></span>|<span data-ttu-id="39b26-152">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="39b26-152">**$34,967,517.33**</span></span>|<span data-ttu-id="39b26-153">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="39b26-153">**$175,002.81**</span></span>|<span data-ttu-id="39b26-154">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="39b26-154">**$592,385.71**</span></span>|  
|<span data-ttu-id="39b26-155">**仓库**</span><span class="sxs-lookup"><span data-stu-id="39b26-155">**Warehouse**</span></span>|<span data-ttu-id="39b26-156">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="39b26-156">**$38,726,913.48**</span></span>|<span data-ttu-id="39b26-157">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="39b26-157">**$331,169.64**</span></span>|<span data-ttu-id="39b26-158">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="39b26-158">**$932,521.23**</span></span>|  
  
## <a name="non-visual-on-rows"></a><span data-ttu-id="39b26-159">针对行的非直观合计</span><span class="sxs-lookup"><span data-stu-id="39b26-159">Non-Visual on rows</span></span>  
 <span data-ttu-id="39b26-160">要生成一个表，其中列是进行直观加和，对于行总数则是所有 [类别] 的实际总和，应发出以下查询：</span><span class="sxs-lookup"><span data-stu-id="39b26-160">To produce a table that visually totals the columns but for row totals brings the true total of all [Category], the following query should be issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="39b26-161">请注意，NON VISUAL 仅应用到 [Category]。</span><span class="sxs-lookup"><span data-stu-id="39b26-161">Note how NON VISUAL is only applied to [Category].</span></span>  
  
 <span data-ttu-id="39b26-162">上述查询产生以下结果：</span><span class="sxs-lookup"><span data-stu-id="39b26-162">The above query produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="39b26-163">All Products</span><span class="sxs-lookup"><span data-stu-id="39b26-163">All Products</span></span>|<span data-ttu-id="39b26-164">配件</span><span class="sxs-lookup"><span data-stu-id="39b26-164">Accessories</span></span>|<span data-ttu-id="39b26-165">Clothing</span><span class="sxs-lookup"><span data-stu-id="39b26-165">Clothing</span></span>|  
|<span data-ttu-id="39b26-166">All Resellers</span><span class="sxs-lookup"><span data-stu-id="39b26-166">All Resellers</span></span>|<span data-ttu-id="39b26-167">$73,694,430.80</span><span class="sxs-lookup"><span data-stu-id="39b26-167">$73,694,430.80</span></span>|<span data-ttu-id="39b26-168">$506,172.45</span><span class="sxs-lookup"><span data-stu-id="39b26-168">$506,172.45</span></span>|<span data-ttu-id="39b26-169">$1,524,906.93</span><span class="sxs-lookup"><span data-stu-id="39b26-169">$1,524,906.93</span></span>|  
|<span data-ttu-id="39b26-170">Value Added Reseller</span><span class="sxs-lookup"><span data-stu-id="39b26-170">Value Added Reseller</span></span>|<span data-ttu-id="39b26-171">$34,967,517.33</span><span class="sxs-lookup"><span data-stu-id="39b26-171">$34,967,517.33</span></span>|<span data-ttu-id="39b26-172">$175,002.81</span><span class="sxs-lookup"><span data-stu-id="39b26-172">$175,002.81</span></span>|<span data-ttu-id="39b26-173">$592,385.71</span><span class="sxs-lookup"><span data-stu-id="39b26-173">$592,385.71</span></span>|  
|<span data-ttu-id="39b26-174">Warehouse</span><span class="sxs-lookup"><span data-stu-id="39b26-174">Warehouse</span></span>|<span data-ttu-id="39b26-175">$38,726,913.48</span><span class="sxs-lookup"><span data-stu-id="39b26-175">$38,726,913.48</span></span>|<span data-ttu-id="39b26-176">$331,169.64</span><span class="sxs-lookup"><span data-stu-id="39b26-176">$331,169.64</span></span>|<span data-ttu-id="39b26-177">$932,521.23</span><span class="sxs-lookup"><span data-stu-id="39b26-177">$932,521.23</span></span>|  
  
 <span data-ttu-id="39b26-178">与上述结果比较时，您可以观察到 [All Resellers] 行现在是将 [Value Added Reseller] 和 [Warehouse] 仓库的显示值相加，但 [All Products] 列会显示所有产品的总值，包括那些未显示的值。</span><span class="sxs-lookup"><span data-stu-id="39b26-178">When compared with the previous results, you can observe that the [All Resellers] row now adds up to the displayed values for [Value Added Reseller] and [Warehouse] but that the [All Products] column shows the total value for all products, including those not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b26-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39b26-179">See Also</span></span>  
 <span data-ttu-id="39b26-180">[MDX &#40;Analysis Services 中的关键概念&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-180">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="39b26-181">[Autoexists](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-181">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="39b26-182">[使用成员、元组和集 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-182">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="39b26-183">[MDX 查询基础知识 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-183">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="39b26-184">[基本 MDX 查询 &#40;MDX&#41;](mdx-query-the-basic-query.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-184">[The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md) </span></span>  
 <span data-ttu-id="39b26-185">[用查询轴和切片器轴限定查询 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span><span class="sxs-lookup"><span data-stu-id="39b26-185">[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span></span>  
 [<span data-ttu-id="39b26-186">在查询中建立多维数据集上下文 (MDX)</span><span class="sxs-lookup"><span data-stu-id="39b26-186">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)  
  
  
