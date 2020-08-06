---
title: 聚合转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9e69d741ddd2bd14a31d7aa79a8c825641713523
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682974"
---
# <a name="aggregate-transformation"></a><span data-ttu-id="5a061-102">聚合转换</span><span class="sxs-lookup"><span data-stu-id="5a061-102">Aggregate Transformation</span></span>
  <span data-ttu-id="5a061-103">聚合转换将聚合函数（如 Average）应用于列值，并将结果复制到转换输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-103">The Aggregate transformation applies aggregate functions, such as Average, to column values and copies the results to the transformation output.</span></span> <span data-ttu-id="5a061-104">除聚合函数以外，转换还提供 GROUP BY 子句，用于指定所要聚合的组。</span><span class="sxs-lookup"><span data-stu-id="5a061-104">Besides aggregate functions, the transformation provides the GROUP BY clause, which you can use to specify groups to aggregate across.</span></span>  
  
## <a name="operations"></a><span data-ttu-id="5a061-105">操作</span><span class="sxs-lookup"><span data-stu-id="5a061-105">Operations</span></span>  
 <span data-ttu-id="5a061-106">聚合转换支持下列运算。</span><span class="sxs-lookup"><span data-stu-id="5a061-106">The Aggregate transformation supports the following operations.</span></span>  
  
|<span data-ttu-id="5a061-107">Operation</span><span class="sxs-lookup"><span data-stu-id="5a061-107">Operation</span></span>|<span data-ttu-id="5a061-108">说明</span><span class="sxs-lookup"><span data-stu-id="5a061-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a061-109">Group by</span><span class="sxs-lookup"><span data-stu-id="5a061-109">Group by</span></span>|<span data-ttu-id="5a061-110">将数据集划分为组。</span><span class="sxs-lookup"><span data-stu-id="5a061-110">Divides datasets into groups.</span></span> <span data-ttu-id="5a061-111">任何数据类型的列都可用于分组。</span><span class="sxs-lookup"><span data-stu-id="5a061-111">Columns of any data type can be used for grouping.</span></span> <span data-ttu-id="5a061-112">有关详细信息，请参阅 [GROUP BY (Transact-SQL)](/sql/t-sql/queries/select-group-by-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-112">For more information, see [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).</span></span>|  
|<span data-ttu-id="5a061-113">SUM</span><span class="sxs-lookup"><span data-stu-id="5a061-113">Sum</span></span>|<span data-ttu-id="5a061-114">对列中的值求和。</span><span class="sxs-lookup"><span data-stu-id="5a061-114">Sums the values in a column.</span></span> <span data-ttu-id="5a061-115">只能对数值数据类型的列求和。</span><span class="sxs-lookup"><span data-stu-id="5a061-115">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="5a061-116">有关详细信息，请参阅 [SUM (Transact-SQL)](/sql/t-sql/functions/sum-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-116">For more information, see [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).</span></span>|  
|<span data-ttu-id="5a061-117">平均值</span><span class="sxs-lookup"><span data-stu-id="5a061-117">Average</span></span>|<span data-ttu-id="5a061-118">返回列中值的平均值。</span><span class="sxs-lookup"><span data-stu-id="5a061-118">Returns the average of the column values in a column.</span></span> <span data-ttu-id="5a061-119">只能对数值数据类型的列求平均值。</span><span class="sxs-lookup"><span data-stu-id="5a061-119">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="5a061-120">有关详细信息，请参阅 [AVG (Transact-SQL)](/sql/t-sql/functions/avg-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-120">For more information, see [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).</span></span>|  
|<span data-ttu-id="5a061-121">Count</span><span class="sxs-lookup"><span data-stu-id="5a061-121">Count</span></span>|<span data-ttu-id="5a061-122">返回组中的项数。</span><span class="sxs-lookup"><span data-stu-id="5a061-122">Returns the number of items in a group.</span></span> <span data-ttu-id="5a061-123">有关详细信息，请参阅 [COUNT (Transact-SQL)](/sql/t-sql/functions/count-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-123">For more information, see [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).</span></span>|  
|<span data-ttu-id="5a061-124">Count distinct</span><span class="sxs-lookup"><span data-stu-id="5a061-124">Count distinct</span></span>|<span data-ttu-id="5a061-125">返回组中的唯一非空值的数量。</span><span class="sxs-lookup"><span data-stu-id="5a061-125">Returns the number of unique nonnull values in a group.</span></span>|  
|<span data-ttu-id="5a061-126">最小值</span><span class="sxs-lookup"><span data-stu-id="5a061-126">Minimum</span></span>|<span data-ttu-id="5a061-127">返回组中的最小值。</span><span class="sxs-lookup"><span data-stu-id="5a061-127">Returns the minimum value in a group.</span></span> <span data-ttu-id="5a061-128">有关详细信息，请参阅 [MIN (Transact-SQL)](/sql/t-sql/functions/min-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-128">For more information, see [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql).</span></span> <span data-ttu-id="5a061-129">与 Transact-SQL MIN 函数不同，此运算只能用于数值、日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="5a061-129">In contrast to the Transact-SQL MIN function, this operation can be used only with numeric, date, and time data types.</span></span>|  
|<span data-ttu-id="5a061-130">最大值</span><span class="sxs-lookup"><span data-stu-id="5a061-130">Maximum</span></span>|<span data-ttu-id="5a061-131">返回组中的最大值。</span><span class="sxs-lookup"><span data-stu-id="5a061-131">Returns the maximum value in a group.</span></span> <span data-ttu-id="5a061-132">有关详细信息，请参阅 [MAX (Transact-SQL)](/sql/t-sql/functions/max-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5a061-132">For more information, see [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql).</span></span> <span data-ttu-id="5a061-133">与 Transact-SQL MAX 函数不同，此运算只能用于数值、日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="5a061-133">In contrast to the Transact-SQL MAX function, this operation can be used only with numeric, date, and time data types.</span></span>|  
  
 <span data-ttu-id="5a061-134">聚合转换处理空值的方式和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 关系数据库引擎相同。</span><span class="sxs-lookup"><span data-stu-id="5a061-134">The Aggregate transformation handles null values in the same way as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] relational database engine.</span></span> <span data-ttu-id="5a061-135">此行为在 SQL-92 标准中定义。</span><span class="sxs-lookup"><span data-stu-id="5a061-135">The behavior is defined in the SQL-92 standard.</span></span> <span data-ttu-id="5a061-136">下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="5a061-136">The following rules apply:</span></span>  
  
-   <span data-ttu-id="5a061-137">在 GROUP BY 子句中，空值和其他列值处理方式类似。</span><span class="sxs-lookup"><span data-stu-id="5a061-137">In a GROUP BY clause, nulls are treated like other column values.</span></span> <span data-ttu-id="5a061-138">如果分组列包含多个空值，那么这些空值将放入单独的一组中。</span><span class="sxs-lookup"><span data-stu-id="5a061-138">If the grouping column contains more than one null value, the null values are put into a single group.</span></span>  
  
-   <span data-ttu-id="5a061-139">在 COUNT（列名称）和 COUNT（DISTINCT 列名称）函数中，空值将被忽略，并且结果将排除包含指定列中的空值的行。</span><span class="sxs-lookup"><span data-stu-id="5a061-139">In the COUNT (column name) and COUNT (DISTINCT column name) functions, nulls are ignored and the result excludes rows that contain null values in the named column.</span></span>  
  
-   <span data-ttu-id="5a061-140">在 COUNT (\*) 函数中，对所有行计数，包括含空值的行。</span><span class="sxs-lookup"><span data-stu-id="5a061-140">In the COUNT (\*) function, all rows are counted, including rows with null values.</span></span>  
  
## <a name="big-numbers-in-aggregates"></a><span data-ttu-id="5a061-141">聚合中的大数</span><span class="sxs-lookup"><span data-stu-id="5a061-141">Big Numbers in Aggregates</span></span>  
 <span data-ttu-id="5a061-142">列可能包含因数值庞大或精度要求高而需要特别考虑的数值。</span><span class="sxs-lookup"><span data-stu-id="5a061-142">A column may contain numeric values that require special consideration because of their large value or precision requirements.</span></span> <span data-ttu-id="5a061-143">聚合转换包含 IsBig 属性，你可以针对输出列设置它，以便调用对大数或高精度数字的特别处理。</span><span class="sxs-lookup"><span data-stu-id="5a061-143">The Aggregation transformation includes the IsBig property, which you can set on output columns to invoke special handling of big or high-precision numbers.</span></span> <span data-ttu-id="5a061-144">如果列值可能超过 40 亿，或者需要超过 float 数据类型的精度，则应将 IsBig 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="5a061-144">If a column value may exceed 4 billion or a precision beyond a float data type is required, IsBig should be set to 1.</span></span>  
  
 <span data-ttu-id="5a061-145">将 IsBig 属性设置为 1 将以下列方式影响聚合转换的输出：</span><span class="sxs-lookup"><span data-stu-id="5a061-145">Setting the IsBig property to 1 affects the output of the aggregation transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="5a061-146">使用 DT_R8 数据类型，而不用 DT_R4 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5a061-146">The DT_R8 data type is used instead of the DT_R4 data type.</span></span>  
  
-   <span data-ttu-id="5a061-147">计数结果以 DT_UI8 数据类型存储。</span><span class="sxs-lookup"><span data-stu-id="5a061-147">Count results are stored as the DT_UI8 data type.</span></span>  
  
-   <span data-ttu-id="5a061-148">非重复计数结果以 DT_UI4 数据类型存储。</span><span class="sxs-lookup"><span data-stu-id="5a061-148">Distinct count results are stored as the DT_UI4 data type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a061-149">在用于 GROUP BY、Maximum 或 Minimum 运算的列中，不能将 IsBig 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="5a061-149">You cannot set IsBig to 1 on columns that are used in the GROUP BY, Maximum, or Minimum operations.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="5a061-150">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="5a061-150">Performance Considerations</span></span>  
 <span data-ttu-id="5a061-151">聚合转换包含一组属性，对其进行设置可增强转换的性能。</span><span class="sxs-lookup"><span data-stu-id="5a061-151">The Aggregate transformation includes a set of properties that you can set to enhance the performance of the transformation.</span></span>  
  
-   <span data-ttu-id="5a061-152">执行 **Group by** 运算时，请设置组件的 Keys 或 KeysScale 属性和组件输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-152">When performing a **Group by** operation, set the Keys or KeysScale properties of the component and the component outputs.</span></span> <span data-ttu-id="5a061-153">通过使用 Keys，可指定要求转换处理的精确键数。</span><span class="sxs-lookup"><span data-stu-id="5a061-153">Using Keys, you can specify the exact number of keys the transformation is expected to handle.</span></span> <span data-ttu-id="5a061-154">（在此上下文中，Keys 指的是要求 **Group by** 运算产生的组数。）使用 KeysScale，可以指定大致的键数。</span><span class="sxs-lookup"><span data-stu-id="5a061-154">(In this context, Keys refers to the number of groups that are expected to result from a **Group by** operation.) Using KeysScale, you can specify an approximate number of keys.</span></span> <span data-ttu-id="5a061-155">为 Keys 或 KeyScale 指定适当的值将会提高性能，原因是转换能够为转换缓存的数据分配足量的内存。</span><span class="sxs-lookup"><span data-stu-id="5a061-155">When you specify an appropriate value for Keys or KeyScale, you improve performance because the tranformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
-   <span data-ttu-id="5a061-156">执行 **Distinct count** 运算时，请设置组件的 CountDistinctKeys 或 CountDistinctScale 属性。</span><span class="sxs-lookup"><span data-stu-id="5a061-156">When performing a **Distinct count** operation, set the CountDistinctKeys or CountDistinctScale properties of the component.</span></span> <span data-ttu-id="5a061-157">使用 CountDistinctKeys 可指定要求转换处理的非重复计数运算的精确键数。</span><span class="sxs-lookup"><span data-stu-id="5a061-157">Using CountDistinctKeys, you can specify the exact number of keys the transformation is expected to handle for a count distinct operation.</span></span> <span data-ttu-id="5a061-158">（在此上下文中，CountDistinctKeys 指的是要求 **Distinct count** 运算产生的非重复值数。）使用 CountDistinctScale，可指定非重复计数运算的大致键数。</span><span class="sxs-lookup"><span data-stu-id="5a061-158">(In this context, CountDistinctKeys refers to the number of distinct values that are expected to result from a **Distinct count** operation.) Using CountDistinctScale, you can specify an approximate number of keys for a count distinct operation.</span></span> <span data-ttu-id="5a061-159">为 CountDistinctKeys 或 CountDistinctScale 指定适当的值将会提高性能，原因是转换能够为转换缓存的数据分配足量的内存。</span><span class="sxs-lookup"><span data-stu-id="5a061-159">When you specify an appropriate value for CountDistinctKeys or CountDistinctScale, you improve performance because the transformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
## <a name="aggregate-transformation-configuration"></a><span data-ttu-id="5a061-160">聚合转换配置</span><span class="sxs-lookup"><span data-stu-id="5a061-160">Aggregate Transformation Configuration</span></span>  
 <span data-ttu-id="5a061-161">在转换级、输出级和列级配置聚合转换。</span><span class="sxs-lookup"><span data-stu-id="5a061-161">You configure the Aggregate transformation at the transformation, output, and column levels.</span></span>  
  
-   <span data-ttu-id="5a061-162">在转换级，可以通过指定以下值配置聚合转换，以便提高性能：</span><span class="sxs-lookup"><span data-stu-id="5a061-162">At the transformation level, you configure the Aggregate transformation for performance by specifying the following values:</span></span>  
  
    -   <span data-ttu-id="5a061-163">要求 **Group by** 运算产生的组数。</span><span class="sxs-lookup"><span data-stu-id="5a061-163">The number of groups that are expected to result from a **Group by** operation.</span></span>  
  
    -   <span data-ttu-id="5a061-164">要求 **Count distinct** 运算产生的非重复值数。</span><span class="sxs-lookup"><span data-stu-id="5a061-164">The number of distinct values that are expected to result from a **Count distinct** operation.</span></span>  
  
    -   <span data-ttu-id="5a061-165">聚合过程中内存可扩展的百分比。</span><span class="sxs-lookup"><span data-stu-id="5a061-165">The percentage by which memory can be extended during the aggregation.</span></span>  
  
     <span data-ttu-id="5a061-166">还可以将聚合转换配置为在除数为零时生成警告而不是失败。</span><span class="sxs-lookup"><span data-stu-id="5a061-166">The Aggregate transformation can also be configured to generate a warning instead of failing when the value of a divisor is zero.</span></span>  
  
-   <span data-ttu-id="5a061-167">在输出级，可以通过指定要求 **Group by** 运算产生的组数配置聚合转换，以提高性能。</span><span class="sxs-lookup"><span data-stu-id="5a061-167">At the output level, you configure the Aggregate transformation for performance by specifying the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="5a061-168">聚合转换支持多个输出，每个输出可采用不同配置。</span><span class="sxs-lookup"><span data-stu-id="5a061-168">The Aggregate transformation supports multiple outputs, and each can be configured differently.</span></span>  
  
-   <span data-ttu-id="5a061-169">在列级，可以指定以下值：</span><span class="sxs-lookup"><span data-stu-id="5a061-169">At the column level, you specify the following values:</span></span>  
  
    -   <span data-ttu-id="5a061-170">列执行的聚合。</span><span class="sxs-lookup"><span data-stu-id="5a061-170">The aggregation that the column performs.</span></span>  
  
    -   <span data-ttu-id="5a061-171">聚合的比较选项。</span><span class="sxs-lookup"><span data-stu-id="5a061-171">The comparison options of the aggregation.</span></span>  
  
 <span data-ttu-id="5a061-172">还可以通过指定以下值配置聚合转换，以便提高性能：</span><span class="sxs-lookup"><span data-stu-id="5a061-172">You can also configure the Aggregate transformation for performance by specifying these values:</span></span>  
  
-   <span data-ttu-id="5a061-173">要求对列执行的 **Group by** 运算产生的组数。</span><span class="sxs-lookup"><span data-stu-id="5a061-173">The number of groups that are expected to result from a **Group by** operation on the column.</span></span>  
  
-   <span data-ttu-id="5a061-174">要求对列执行的 **Count distinct** 运算产生的非重复值数。</span><span class="sxs-lookup"><span data-stu-id="5a061-174">The number of distinct values that are expected to result from a **Count distinct** operation on the column.</span></span>  
  
 <span data-ttu-id="5a061-175">如果列包含很大的数值或精度很高的数值，还可以将这样的列标识为 IsBig。</span><span class="sxs-lookup"><span data-stu-id="5a061-175">You can also identify columns as IsBig if a column contains large numeric values or numeric values with high precision.</span></span>  
  
 <span data-ttu-id="5a061-176">聚合转换是异步过程，也就是说它并非逐行地占用和发布数据，</span><span class="sxs-lookup"><span data-stu-id="5a061-176">The Aggregate transformation is asynchronous, which means that it does not consume and publish data row by row.</span></span> <span data-ttu-id="5a061-177">而是占用整个行集，执行其分组和聚合操作，然后发布结果。</span><span class="sxs-lookup"><span data-stu-id="5a061-177">Instead it consumes the whole rowset, performs its groupings and aggregations, and then publishes the results.</span></span>  
  
 <span data-ttu-id="5a061-178">此转换不传递任何列，而是在数据流中为发布的数据创建新列。</span><span class="sxs-lookup"><span data-stu-id="5a061-178">This transformation does not pass through any columns, but creates new columns in the data flow for the data it publishes.</span></span> <span data-ttu-id="5a061-179">只有应用聚合函数的输入列或转换用于分组的输入列才复制到转换输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-179">Only the input columns to which aggregate functions apply or the input columns the transformation uses for grouping are copied to the transformation output.</span></span> <span data-ttu-id="5a061-180">例如，聚合转换输入可能有三列： **CountryRegion**、 **City**和 **Population**。</span><span class="sxs-lookup"><span data-stu-id="5a061-180">For example, an Aggregate transformation input might have three columns: **CountryRegion**, **City**, and **Population**.</span></span> <span data-ttu-id="5a061-181">转换按 **CountryRegion** 列分组，并对 **Population** 列应用 Sum 函数。</span><span class="sxs-lookup"><span data-stu-id="5a061-181">The transformation groups by the **CountryRegion** column and applies the Sum function to the **Population** column.</span></span> <span data-ttu-id="5a061-182">因此，输出不包含 **City** 列。</span><span class="sxs-lookup"><span data-stu-id="5a061-182">Therefore the output does not include the **City** column.</span></span>  
  
 <span data-ttu-id="5a061-183">也可将多个输出添加到聚合转换，并将每个聚合定向到不同输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-183">You can also add multiple outputs to the Aggregate transformation and direct each aggregation to a different output.</span></span> <span data-ttu-id="5a061-184">例如，如果聚合转换应用 Sum 和 Average 函数，则可以将每个聚合定向到不同输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-184">For example, if the Aggregate transformation applies the Sum and the Average functions, each aggregation can be directed to a different output.</span></span>  
  
 <span data-ttu-id="5a061-185">可以对单个输入列应用多个聚合。</span><span class="sxs-lookup"><span data-stu-id="5a061-185">You can apply multiple aggregations to a single input column.</span></span> <span data-ttu-id="5a061-186">例如，如果需要名为 **Sales**的输入列的和值与平均值，则可以配置转换，使其将 Sum 和 Average 函数都应用于 **Sales** 列。</span><span class="sxs-lookup"><span data-stu-id="5a061-186">For example, if you want the sum and average values for an input column named **Sales**, you can configure the transformation to apply both the Sum and Average functions to the **Sales** column.</span></span>  
  
 <span data-ttu-id="5a061-187">聚合转换具有一个输入和一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-187">The Aggregate transformation has one input and one or more outputs.</span></span> <span data-ttu-id="5a061-188">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="5a061-188">It does not support an error output.</span></span>  
  
 <span data-ttu-id="5a061-189">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="5a061-189">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5a061-190">有关可在 **“聚合转换编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="5a061-190">For more information about the properties that you can set in the **Aggregate Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a061-191">聚合转换编辑器（“聚合”选项卡）</span><span class="sxs-lookup"><span data-stu-id="5a061-191">Aggregate Transformation Editor &#40;Aggregations Tab&#41;</span></span>](../../aggregate-transformation-editor-aggregations-tab.md)  
  
-   [<span data-ttu-id="5a061-192">聚合转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="5a061-192">Aggregate Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../aggregate-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="5a061-193">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="5a061-193">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="5a061-194">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="5a061-194">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a061-195">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5a061-195">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="5a061-196">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="5a061-196">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="5a061-197">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="5a061-197">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a061-198">使用聚合转换来聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="5a061-198">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [<span data-ttu-id="5a061-199">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="5a061-199">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="5a061-200">为合并转换和合并联接转换排序数据</span><span class="sxs-lookup"><span data-stu-id="5a061-200">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="5a061-201">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5a061-201">Related Tasks</span></span>  
 [<span data-ttu-id="5a061-202">使用聚合转换来聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="5a061-202">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a061-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a061-203">See Also</span></span>  
 <span data-ttu-id="5a061-204">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5a061-204">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="5a061-205">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="5a061-205">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
