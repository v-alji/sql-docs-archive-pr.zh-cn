---
title: " (DTA) 的 StorageBoundInMB 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea49b0af981b8f8d96efb087033d8f1466364c76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691450"
---
# <a name="storageboundinmb-element-dta"></a><span data-ttu-id="3f6e3-102">StorageBoundInMB 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="3f6e3-102">StorageBoundInMB Element (DTA)</span></span>
  <span data-ttu-id="3f6e3-103">指定数据库引擎优化顾问优化建议（索引和分区集）可用的最大空间 (MB)。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-103">Specifies the maximum space in megabytes that can be consumed by the Database Engine Tuning Advisor tuning recommendation (index and partitioning set).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6e3-104">语法</span><span class="sxs-lookup"><span data-stu-id="3f6e3-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="3f6e3-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="3f6e3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="3f6e3-106">特征</span><span class="sxs-lookup"><span data-stu-id="3f6e3-106">Characteristic</span></span>|<span data-ttu-id="3f6e3-107">说明</span><span class="sxs-lookup"><span data-stu-id="3f6e3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3f6e3-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="3f6e3-108">**Data type and length**</span></span>|<span data-ttu-id="3f6e3-109">`unsignedInt`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="3f6e3-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="3f6e3-110">**Default value**</span></span>|<span data-ttu-id="3f6e3-111">无。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-111">None.</span></span>|  
|<span data-ttu-id="3f6e3-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="3f6e3-112">**Occurrence**</span></span>|<span data-ttu-id="3f6e3-113">可选。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-113">Optional.</span></span> <span data-ttu-id="3f6e3-114">仅能对 `TuningOptions` 元素使用一次。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-114">Can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="3f6e3-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="3f6e3-115">Element Relationships</span></span>  
  
|<span data-ttu-id="3f6e3-116">关系</span><span class="sxs-lookup"><span data-stu-id="3f6e3-116">Relationship</span></span>|<span data-ttu-id="3f6e3-117">元素</span><span class="sxs-lookup"><span data-stu-id="3f6e3-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="3f6e3-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="3f6e3-118">**Parent element**</span></span>|[<span data-ttu-id="3f6e3-119">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="3f6e3-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="3f6e3-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="3f6e3-120">**Child elements**</span></span>|<span data-ttu-id="3f6e3-121">无</span><span class="sxs-lookup"><span data-stu-id="3f6e3-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f6e3-122">备注</span><span class="sxs-lookup"><span data-stu-id="3f6e3-122">Remarks</span></span>  
 <span data-ttu-id="3f6e3-123">优化多个数据库时，建议对所有数据库都进行空间计算。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-123">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="3f6e3-124">默认情况下，数据库引擎优化顾问会使用以下存储空间中较小的一个：</span><span class="sxs-lookup"><span data-stu-id="3f6e3-124">By default, Database Engine Tuning Advisor assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="3f6e3-125">当前原始数据大小的三倍，原始数据包含堆大小和表的聚集索引大小的总和。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-125">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables.</span></span>  
  
-   <span data-ttu-id="3f6e3-126">所有已附连磁盘驱动器的可用空间加上原始数据的大小。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-126">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="3f6e3-127">默认存储大小不包括非聚集索引和索引视图。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-127">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="3f6e3-128">如果为 `StorageBoundInMB` 元素指定的值超出了磁盘空间的实际大小，则数据库引擎优化顾问会返回一个错误消息，但继续进行优化。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-128">If the value specified for the `StorageBoundInMB` element exceeds the actual disk space, Database Engine Tuning Advisor returns an error, but continues tuning.</span></span> <span data-ttu-id="3f6e3-129">优化完成之后，如果决定实现建议，则可增加磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="3f6e3-129">After tuning is complete, you can add disk space if you decide to implement the recommendation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6e3-130">示例</span><span class="sxs-lookup"><span data-stu-id="3f6e3-130">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="3f6e3-131">说明</span><span class="sxs-lookup"><span data-stu-id="3f6e3-131">Description</span></span>  
 <span data-ttu-id="3f6e3-132">以下代码示例说明如何将优化建议可以消耗的最大磁盘空间设置为 1500 MB：</span><span class="sxs-lookup"><span data-stu-id="3f6e3-132">The following code example shows how to set a limit of 1500 megabytes as the maximum disk space that a tuning recommendation can consume:</span></span>  
  
## <a name="code"></a><span data-ttu-id="3f6e3-133">代码</span><span class="sxs-lookup"><span data-stu-id="3f6e3-133">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f6e3-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f6e3-134">See Also</span></span>  
 [<span data-ttu-id="3f6e3-135">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="3f6e3-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
