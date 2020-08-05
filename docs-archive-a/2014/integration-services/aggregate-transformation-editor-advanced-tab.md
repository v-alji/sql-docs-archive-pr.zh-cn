---
title: 聚合转换编辑器 (高级选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb3742a83f363f74004a5aac0eefc589ee2a5be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579724"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a><span data-ttu-id="13e95-102">聚合转换编辑器（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="13e95-102">Aggregate Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="13e95-103">可以使用 **“聚合转换编辑器”** 对话框的 **“高级”** 选项卡设置组件属性，指定聚合以及设置输入和输出列的属性。</span><span class="sxs-lookup"><span data-stu-id="13e95-103">Use the **Advanced** tab of the **Aggregate Transformation Editor** dialog box to set component properties, specify aggregations, and set properties of input and output columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13e95-104">对于键计数、键范围、非重复键计数和非重复键范围的选项来说，如果是在“高级”\*\*\*\* 选项卡中指定的，则会应用于组件级；如果是在“聚合”\*\*\*\* 选项卡的高级显示部分中指定的，则会应用于输出级；而如果是在“聚合”\*\*\*\* 选项卡底部的列列表中指定的，则会应用于列级。</span><span class="sxs-lookup"><span data-stu-id="13e95-104">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="13e95-105">在聚合转换中， **“键”** 和 **“键范围”** 是指期望 **“分组依据”** 操作产生的组数。</span><span class="sxs-lookup"><span data-stu-id="13e95-105">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="13e95-106">**“非重复键计数”** 和 **“非重复键数范围”** 是指期望 **“非重复计数”** 操作产生的非重复值的数量。</span><span class="sxs-lookup"><span data-stu-id="13e95-106">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="13e95-107">若要了解有关聚合转换的详细信息，请参阅 [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="13e95-107">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="13e95-108">选项</span><span class="sxs-lookup"><span data-stu-id="13e95-108">Options</span></span>  
 <span data-ttu-id="13e95-109">**“键范围”**</span><span class="sxs-lookup"><span data-stu-id="13e95-109">**Keys scale**</span></span>  
 <span data-ttu-id="13e95-110">根据需要，可以指定聚合所需的键的大致数目。</span><span class="sxs-lookup"><span data-stu-id="13e95-110">Optionally specify the approximate number of keys that the aggregation expects.</span></span> <span data-ttu-id="13e95-111">转换将使用此信息优化其初始缓存大小。</span><span class="sxs-lookup"><span data-stu-id="13e95-111">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="13e95-112">默认情况下，此选项的值为 **“未指定”**。</span><span class="sxs-lookup"><span data-stu-id="13e95-112">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="13e95-113">如果同时指定了 **“键范围”** 和 **“键数”** ，则 **“键数”** 优先。</span><span class="sxs-lookup"><span data-stu-id="13e95-113">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
|<span data-ttu-id="13e95-114">值</span><span class="sxs-lookup"><span data-stu-id="13e95-114">Value</span></span>|<span data-ttu-id="13e95-115">说明</span><span class="sxs-lookup"><span data-stu-id="13e95-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13e95-116">未指定</span><span class="sxs-lookup"><span data-stu-id="13e95-116">Unspecified</span></span>|<span data-ttu-id="13e95-117">不使用 **“键范围”** 属性。</span><span class="sxs-lookup"><span data-stu-id="13e95-117">The **Keys scale** property is not used.</span></span>|  
|<span data-ttu-id="13e95-118">低</span><span class="sxs-lookup"><span data-stu-id="13e95-118">Low</span></span>|<span data-ttu-id="13e95-119">聚合可以写入大约 500,000 个键。</span><span class="sxs-lookup"><span data-stu-id="13e95-119">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="13e95-120">中型</span><span class="sxs-lookup"><span data-stu-id="13e95-120">Medium</span></span>|<span data-ttu-id="13e95-121">聚合可以写入大约 5,000,000 个键。</span><span class="sxs-lookup"><span data-stu-id="13e95-121">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="13e95-122">高</span><span class="sxs-lookup"><span data-stu-id="13e95-122">High</span></span>|<span data-ttu-id="13e95-123">聚合可以写入 25,000,000 个以上的键。</span><span class="sxs-lookup"><span data-stu-id="13e95-123">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="13e95-124">**键数**</span><span class="sxs-lookup"><span data-stu-id="13e95-124">**Number of keys**</span></span>  
 <span data-ttu-id="13e95-125">根据需要，可以指定聚合所需的键的精确数目。</span><span class="sxs-lookup"><span data-stu-id="13e95-125">Optionally specify the exact number of keys that the aggregation expects.</span></span> <span data-ttu-id="13e95-126">转换将使用此信息优化其初始缓存大小。</span><span class="sxs-lookup"><span data-stu-id="13e95-126">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="13e95-127">如果同时指定了 **“键范围”** 和 **“键数”** ，则 **“键数”** 优先。</span><span class="sxs-lookup"><span data-stu-id="13e95-127">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
 <span data-ttu-id="13e95-128">**非重复计数**</span><span class="sxs-lookup"><span data-stu-id="13e95-128">**Count distinct scale**</span></span>  
 <span data-ttu-id="13e95-129">根据需要，可以指定聚合能够写入的非重复值的大致数目。</span><span class="sxs-lookup"><span data-stu-id="13e95-129">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="13e95-130">默认情况下，此选项的值为 **“未指定”**。</span><span class="sxs-lookup"><span data-stu-id="13e95-130">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="13e95-131">如果同时指定了 **“非重复键数范围”** 和 **“非重复键计数”** ，则 **“非重复键计数”** 优先。</span><span class="sxs-lookup"><span data-stu-id="13e95-131">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
|<span data-ttu-id="13e95-132">值</span><span class="sxs-lookup"><span data-stu-id="13e95-132">Value</span></span>|<span data-ttu-id="13e95-133">说明</span><span class="sxs-lookup"><span data-stu-id="13e95-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13e95-134">未指定</span><span class="sxs-lookup"><span data-stu-id="13e95-134">Unspecified</span></span>|<span data-ttu-id="13e95-135">不使用 CountDistinctScale 属性。</span><span class="sxs-lookup"><span data-stu-id="13e95-135">The CountDistinctScale property is not used.</span></span>|  
|<span data-ttu-id="13e95-136">低</span><span class="sxs-lookup"><span data-stu-id="13e95-136">Low</span></span>|<span data-ttu-id="13e95-137">聚合可以写入大约 500,000 个非重复值。</span><span class="sxs-lookup"><span data-stu-id="13e95-137">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="13e95-138">中型</span><span class="sxs-lookup"><span data-stu-id="13e95-138">Medium</span></span>|<span data-ttu-id="13e95-139">聚合可以写入大约 5,000,000 个非重复值。</span><span class="sxs-lookup"><span data-stu-id="13e95-139">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="13e95-140">高</span><span class="sxs-lookup"><span data-stu-id="13e95-140">High</span></span>|<span data-ttu-id="13e95-141">聚合可以写入 25,000,000 个以上的非重复值。</span><span class="sxs-lookup"><span data-stu-id="13e95-141">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="13e95-142">**非重复键计数**</span><span class="sxs-lookup"><span data-stu-id="13e95-142">**Count distinct keys**</span></span>  
 <span data-ttu-id="13e95-143">根据需要，可以指定聚合能够写入的非重复值的精确数目。</span><span class="sxs-lookup"><span data-stu-id="13e95-143">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="13e95-144">如果同时指定了 **“非重复键数范围”** 和 **“非重复键计数”** ，则 **“非重复键计数”** 优先。</span><span class="sxs-lookup"><span data-stu-id="13e95-144">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
 <span data-ttu-id="13e95-145">**自动扩展系数**</span><span class="sxs-lookup"><span data-stu-id="13e95-145">**Auto extend factor**</span></span>  
 <span data-ttu-id="13e95-146">使用一个 1 到 100 之间的值指定在聚合过程中内存可扩展的百分比。</span><span class="sxs-lookup"><span data-stu-id="13e95-146">Use a value between 1 and 100 to specify the percentage by which memory can be extended during the aggregation.</span></span> <span data-ttu-id="13e95-147">默认情况下，此选项的值为 **25%**。</span><span class="sxs-lookup"><span data-stu-id="13e95-147">By default, the value of this option is **25%**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e95-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13e95-148">See Also</span></span>  
 <span data-ttu-id="13e95-149">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="13e95-149">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="13e95-150">[聚合转换编辑器 &#40;聚合 "选项卡&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span><span class="sxs-lookup"><span data-stu-id="13e95-150">[Aggregate Transformation Editor &#40;Aggregations Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span></span>  
 [<span data-ttu-id="13e95-151">使用聚合转换来聚合数据集中的值</span><span class="sxs-lookup"><span data-stu-id="13e95-151">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
