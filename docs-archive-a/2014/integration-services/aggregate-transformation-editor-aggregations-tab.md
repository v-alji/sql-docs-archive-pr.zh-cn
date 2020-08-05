---
title: 聚合转换编辑器 (聚合 "选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30cafb68a69a061fe4b79e832f356b82926c9761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579721"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a><span data-ttu-id="755e7-102">聚合转换编辑器（“聚合”选项卡）</span><span class="sxs-lookup"><span data-stu-id="755e7-102">Aggregate Transformation Editor (Aggregations Tab)</span></span>
  <span data-ttu-id="755e7-103">可以使用 **“聚合转换编辑器”** 对话框的 **“聚合”** 选项卡指定聚合的列以及聚合属性。</span><span class="sxs-lookup"><span data-stu-id="755e7-103">Use the **Aggregations** tab of the **Aggregate Transformation Editor** dialog box to specify columns for aggregation and aggregation properties.</span></span> <span data-ttu-id="755e7-104">可以应用多个聚合。</span><span class="sxs-lookup"><span data-stu-id="755e7-104">You can apply multiple aggregations.</span></span> <span data-ttu-id="755e7-105">此转换不生成错误输出。</span><span class="sxs-lookup"><span data-stu-id="755e7-105">This transformation does not generate an error output.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="755e7-106">对于键计数、键范围、非重复键计数和非重复键范围的选项来说，如果是在“高级”\*\*\*\* 选项卡中指定的，则会应用于组件级；如果是在“聚合”\*\*\*\* 选项卡的高级显示部分中指定的，则会应用于输出级；而如果是在“聚合”\*\*\*\* 选项卡底部的列列表中指定的，则会应用于列级。</span><span class="sxs-lookup"><span data-stu-id="755e7-106">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="755e7-107">在聚合转换中， **“键”** 和 **“键范围”** 是指期望 **“分组依据”** 操作产生的组数。</span><span class="sxs-lookup"><span data-stu-id="755e7-107">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="755e7-108">**“非重复键计数”** 和 **“非重复键数范围”** 是指期望 **“非重复计数”** 操作产生的非重复值的数量。</span><span class="sxs-lookup"><span data-stu-id="755e7-108">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="755e7-109">若要了解有关聚合转换的详细信息，请参阅 [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="755e7-109">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="755e7-110">选项</span><span class="sxs-lookup"><span data-stu-id="755e7-110">Options</span></span>  
 <span data-ttu-id="755e7-111">**高级/基本**</span><span class="sxs-lookup"><span data-stu-id="755e7-111">**Advanced / Basic**</span></span>  
 <span data-ttu-id="755e7-112">显示或隐藏为多个输出配置多个聚合的选项。</span><span class="sxs-lookup"><span data-stu-id="755e7-112">Display or hide options to configure multiple aggregations for multiple outputs.</span></span> <span data-ttu-id="755e7-113">默认情况下，隐藏“高级”选项。</span><span class="sxs-lookup"><span data-stu-id="755e7-113">By default, the Advanced options are hidden.</span></span>  
  
 <span data-ttu-id="755e7-114">**聚合名**</span><span class="sxs-lookup"><span data-stu-id="755e7-114">**Aggregation Name**</span></span>  
 <span data-ttu-id="755e7-115">在“高级”显示中，键入聚合的友好名称。</span><span class="sxs-lookup"><span data-stu-id="755e7-115">In the Advanced display, type a friendly name for the aggregation.</span></span>  
  
 <span data-ttu-id="755e7-116">**按列分组**</span><span class="sxs-lookup"><span data-stu-id="755e7-116">**Group By Columns**</span></span>  
 <span data-ttu-id="755e7-117">在“高级”显示中，通过使用下面描述的“可用输入列”\*\*\*\* 列表，选择用于分组的列。</span><span class="sxs-lookup"><span data-stu-id="755e7-117">In the Advanced display, select columns for grouping by using the **Available Input Columns** list as described below.</span></span>  
  
 <span data-ttu-id="755e7-118">**键范围**</span><span class="sxs-lookup"><span data-stu-id="755e7-118">**Key Scale**</span></span>  
 <span data-ttu-id="755e7-119">在“高级”显示中，根据需要指定聚合可写入的键的大致数目。</span><span class="sxs-lookup"><span data-stu-id="755e7-119">In the Advanced display, optionally specify the approximate number of keys that the aggregation can write.</span></span> <span data-ttu-id="755e7-120">默认情况下，此选项的值为 **“未指定”**。</span><span class="sxs-lookup"><span data-stu-id="755e7-120">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="755e7-121">如果同时设置了 **“键范围”** 和 **“键”** 属性，则 **“键”** 的值优先。</span><span class="sxs-lookup"><span data-stu-id="755e7-121">If both the **Key Scale** and **Keys** properties are set, the value of **Keys** takes precedence.</span></span>  
  
|<span data-ttu-id="755e7-122">值</span><span class="sxs-lookup"><span data-stu-id="755e7-122">Value</span></span>|<span data-ttu-id="755e7-123">说明</span><span class="sxs-lookup"><span data-stu-id="755e7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="755e7-124">未指定</span><span class="sxs-lookup"><span data-stu-id="755e7-124">Unspecified</span></span>|<span data-ttu-id="755e7-125">不使用“键范围”属性。</span><span class="sxs-lookup"><span data-stu-id="755e7-125">The Key Scale property is not used.</span></span>|  
|<span data-ttu-id="755e7-126">低</span><span class="sxs-lookup"><span data-stu-id="755e7-126">Low</span></span>|<span data-ttu-id="755e7-127">聚合可以写入大约 500,000 个键。</span><span class="sxs-lookup"><span data-stu-id="755e7-127">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="755e7-128">中型</span><span class="sxs-lookup"><span data-stu-id="755e7-128">Medium</span></span>|<span data-ttu-id="755e7-129">聚合可以写入大约 5,000,000 个键。</span><span class="sxs-lookup"><span data-stu-id="755e7-129">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="755e7-130">高</span><span class="sxs-lookup"><span data-stu-id="755e7-130">High</span></span>|<span data-ttu-id="755e7-131">聚合可以写入 25,000,000 个以上的键。</span><span class="sxs-lookup"><span data-stu-id="755e7-131">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="755e7-132">**“键”**</span><span class="sxs-lookup"><span data-stu-id="755e7-132">**Keys**</span></span>  
 <span data-ttu-id="755e7-133">在“高级”显示中，根据需要指定聚合可写入的键的精确数目。</span><span class="sxs-lookup"><span data-stu-id="755e7-133">In the Advanced display, optionally specify the exact number of keys that the aggregation can write.</span></span> <span data-ttu-id="755e7-134">如果同时指定了 **“键范围”** 和 **“键”** ，则 **“键”** 优先。</span><span class="sxs-lookup"><span data-stu-id="755e7-134">If both **Key Scale** and **Keys** are specified, **Keys** takes precedence.</span></span>  
  
 <span data-ttu-id="755e7-135">**可用输入列**</span><span class="sxs-lookup"><span data-stu-id="755e7-135">**Available Input Columns**</span></span>  
 <span data-ttu-id="755e7-136">通过使用此表中的复选框，从可用输入列列表中选择。</span><span class="sxs-lookup"><span data-stu-id="755e7-136">Select from the list of available input columns by using the check boxes in this table.</span></span>  
  
 <span data-ttu-id="755e7-137">**输入列**</span><span class="sxs-lookup"><span data-stu-id="755e7-137">**Input Column**</span></span>  
 <span data-ttu-id="755e7-138">从可用输入列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="755e7-138">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="755e7-139">**输出别名**</span><span class="sxs-lookup"><span data-stu-id="755e7-139">**Output Alias**</span></span>  
 <span data-ttu-id="755e7-140">为每一列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="755e7-140">Type an alias for each column.</span></span> <span data-ttu-id="755e7-141">默认值为输入列的名称；不过，您也可以任选一个唯一的描述性名称。</span><span class="sxs-lookup"><span data-stu-id="755e7-141">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="755e7-142">**操作**</span><span class="sxs-lookup"><span data-stu-id="755e7-142">**Operation**</span></span>  
 <span data-ttu-id="755e7-143">参照下表，从可用操作列表中选择。</span><span class="sxs-lookup"><span data-stu-id="755e7-143">Choose from the list of available operations, using the following table as a guide.</span></span>  
  
|<span data-ttu-id="755e7-144">Operation</span><span class="sxs-lookup"><span data-stu-id="755e7-144">Operation</span></span>|<span data-ttu-id="755e7-145">说明</span><span class="sxs-lookup"><span data-stu-id="755e7-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="755e7-146">**GroupBy**</span><span class="sxs-lookup"><span data-stu-id="755e7-146">**GroupBy**</span></span>|<span data-ttu-id="755e7-147">将数据集划分为组。</span><span class="sxs-lookup"><span data-stu-id="755e7-147">Divides datasets into groups.</span></span> <span data-ttu-id="755e7-148">可以将任何数据类型的列用于分组。</span><span class="sxs-lookup"><span data-stu-id="755e7-148">Columns with any data type can be used for grouping.</span></span> <span data-ttu-id="755e7-149">有关详细信息，请参阅 GROUP BY。</span><span class="sxs-lookup"><span data-stu-id="755e7-149">For more information, see GROUP BY.</span></span>|  
|<span data-ttu-id="755e7-150">**长度**</span><span class="sxs-lookup"><span data-stu-id="755e7-150">**Sum**</span></span>|<span data-ttu-id="755e7-151">对列中的值求和。</span><span class="sxs-lookup"><span data-stu-id="755e7-151">Sums the values in a column.</span></span> <span data-ttu-id="755e7-152">只能对数值数据类型的列求和。</span><span class="sxs-lookup"><span data-stu-id="755e7-152">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="755e7-153">有关详细信息，请参阅 SUM。</span><span class="sxs-lookup"><span data-stu-id="755e7-153">For more information, see SUM.</span></span>|  
|<span data-ttu-id="755e7-154">**平均值**</span><span class="sxs-lookup"><span data-stu-id="755e7-154">**Average**</span></span>|<span data-ttu-id="755e7-155">返回列中值的平均值。</span><span class="sxs-lookup"><span data-stu-id="755e7-155">Returns the average of the column values in a column.</span></span> <span data-ttu-id="755e7-156">只能对数值数据类型的列求平均值。</span><span class="sxs-lookup"><span data-stu-id="755e7-156">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="755e7-157">有关详细信息，请参阅 AVG。</span><span class="sxs-lookup"><span data-stu-id="755e7-157">For more information, see AVG.</span></span>|  
|<span data-ttu-id="755e7-158">**Count**</span><span class="sxs-lookup"><span data-stu-id="755e7-158">**Count**</span></span>|<span data-ttu-id="755e7-159">返回组中的项数。</span><span class="sxs-lookup"><span data-stu-id="755e7-159">Returns the number of items in a group.</span></span> <span data-ttu-id="755e7-160">有关详细信息，请参阅 COUNT。</span><span class="sxs-lookup"><span data-stu-id="755e7-160">For more information, see COUNT.</span></span>|  
|<span data-ttu-id="755e7-161">**CountDistinct**</span><span class="sxs-lookup"><span data-stu-id="755e7-161">**CountDistinct**</span></span>|<span data-ttu-id="755e7-162">返回组中的唯一非空值的数量。</span><span class="sxs-lookup"><span data-stu-id="755e7-162">Returns the number of unique nonnull values in a group.</span></span> <span data-ttu-id="755e7-163">有关详细信息，请参阅 COUNT 和 DISTINCT。</span><span class="sxs-lookup"><span data-stu-id="755e7-163">For more information, see COUNT and Distinct.</span></span>|  
|<span data-ttu-id="755e7-164">**最低**</span><span class="sxs-lookup"><span data-stu-id="755e7-164">**Minimum**</span></span>|<span data-ttu-id="755e7-165">返回组中的最小值。</span><span class="sxs-lookup"><span data-stu-id="755e7-165">Returns the minimum value in a group.</span></span> <span data-ttu-id="755e7-166">只限于数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="755e7-166">Restricted to numeric data types.</span></span>|  
|<span data-ttu-id="755e7-167">最大值</span><span class="sxs-lookup"><span data-stu-id="755e7-167">**Maximum**</span></span>|<span data-ttu-id="755e7-168">返回组中的最大值。</span><span class="sxs-lookup"><span data-stu-id="755e7-168">Returns the maximum value in a group.</span></span> <span data-ttu-id="755e7-169">只限于数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="755e7-169">Restricted to numeric data types.</span></span>|  
  
 <span data-ttu-id="755e7-170">**比较标志**</span><span class="sxs-lookup"><span data-stu-id="755e7-170">**Comparison Flags**</span></span>  
 <span data-ttu-id="755e7-171">如果选择“分组依据”\*\*\*\*，请使用复选框来控制转换如何执行比较。</span><span class="sxs-lookup"><span data-stu-id="755e7-171">If you choose **Group By**, use the check boxes to control how the transformation performs the comparison.</span></span> <span data-ttu-id="755e7-172">有关字符串比较选项的信息，请参阅 [Comparing String Data](data-flow/comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="755e7-172">For information on the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="755e7-173">**Count Distinct Scale**</span><span class="sxs-lookup"><span data-stu-id="755e7-173">**Count Distinct Scale**</span></span>  
 <span data-ttu-id="755e7-174">根据需要，可以指定聚合能够写入的非重复值的大致数目。</span><span class="sxs-lookup"><span data-stu-id="755e7-174">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="755e7-175">默认情况下，此选项的值为 **“未指定”**。</span><span class="sxs-lookup"><span data-stu-id="755e7-175">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="755e7-176">如果同时 `CountDistinctScale` 指定了和**CountDistinctKeys** ，则**CountDistinctKeys**优先。</span><span class="sxs-lookup"><span data-stu-id="755e7-176">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
|<span data-ttu-id="755e7-177">值</span><span class="sxs-lookup"><span data-stu-id="755e7-177">Value</span></span>|<span data-ttu-id="755e7-178">说明</span><span class="sxs-lookup"><span data-stu-id="755e7-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="755e7-179">未指定</span><span class="sxs-lookup"><span data-stu-id="755e7-179">Unspecified</span></span>|<span data-ttu-id="755e7-180">不使用 `CountDistinctScale` 属性。</span><span class="sxs-lookup"><span data-stu-id="755e7-180">The `CountDistinctScale` property is not used.</span></span>|  
|<span data-ttu-id="755e7-181">低</span><span class="sxs-lookup"><span data-stu-id="755e7-181">Low</span></span>|<span data-ttu-id="755e7-182">聚合可以写入大约 500,000 个非重复值。</span><span class="sxs-lookup"><span data-stu-id="755e7-182">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="755e7-183">中型</span><span class="sxs-lookup"><span data-stu-id="755e7-183">Medium</span></span>|<span data-ttu-id="755e7-184">聚合可以写入大约 5,000,000 个非重复值。</span><span class="sxs-lookup"><span data-stu-id="755e7-184">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="755e7-185">高</span><span class="sxs-lookup"><span data-stu-id="755e7-185">High</span></span>|<span data-ttu-id="755e7-186">聚合可以写入 25,000,000 个以上的非重复值。</span><span class="sxs-lookup"><span data-stu-id="755e7-186">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="755e7-187">**Count Distinct Keys**</span><span class="sxs-lookup"><span data-stu-id="755e7-187">**Count Distinct Keys**</span></span>  
 <span data-ttu-id="755e7-188">根据需要，可以指定聚合能够写入的非重复值的精确数目。</span><span class="sxs-lookup"><span data-stu-id="755e7-188">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="755e7-189">如果同时 `CountDistinctScale` 指定了和**CountDistinctKeys** ，则**CountDistinctKeys**优先。</span><span class="sxs-lookup"><span data-stu-id="755e7-189">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755e7-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="755e7-190">See Also</span></span>  
 <span data-ttu-id="755e7-191">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="755e7-191">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="755e7-192">[聚合转换编辑器 &#40;高级 "选项卡&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="755e7-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="755e7-193">使用聚合转换来聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="755e7-193">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
