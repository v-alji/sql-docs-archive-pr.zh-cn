---
title: " (DTA) 的 KeepExisting 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: cde9b3091b75f55e4b9c79137853fbd7d4e0daf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690972"
---
# <a name="keepexisting-element-dta"></a><span data-ttu-id="a63f8-102">KeepExisting 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a63f8-102">KeepExisting Element (DTA)</span></span>
  <span data-ttu-id="a63f8-103">指定数据库引擎优化顾问在生成建议时必须保留的物理设计结构（索引、索引视图或分区）。</span><span class="sxs-lookup"><span data-stu-id="a63f8-103">Specifies the physical design structures (indexes, indexed views, or partitioning) that Database Engine Tuning Advisor must retain when generating its recommendation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63f8-104">语法</span><span class="sxs-lookup"><span data-stu-id="a63f8-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="a63f8-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="a63f8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="a63f8-106">特征</span><span class="sxs-lookup"><span data-stu-id="a63f8-106">Characteristic</span></span>|<span data-ttu-id="a63f8-107">说明</span><span class="sxs-lookup"><span data-stu-id="a63f8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a63f8-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="a63f8-108">**Data type and length**</span></span>|<span data-ttu-id="a63f8-109">`string`，服务器强制执行的长度限制。</span><span class="sxs-lookup"><span data-stu-id="a63f8-109">`string`, length limit enforced by the server.</span></span>|  
|<span data-ttu-id="a63f8-110">**允许的值**</span><span class="sxs-lookup"><span data-stu-id="a63f8-110">**Allowed values**</span></span>|<span data-ttu-id="a63f8-111">**NONE**</span><span class="sxs-lookup"><span data-stu-id="a63f8-111">**NONE**</span></span><br /> <span data-ttu-id="a63f8-112">无现有结构。</span><span class="sxs-lookup"><span data-stu-id="a63f8-112">No existing structures.</span></span><br /><br /> <span data-ttu-id="a63f8-113">**ALL**</span><span class="sxs-lookup"><span data-stu-id="a63f8-113">**ALL**</span></span><br /> <span data-ttu-id="a63f8-114">所有现有结构。</span><span class="sxs-lookup"><span data-stu-id="a63f8-114">All existing structures.</span></span><br /><br /> <span data-ttu-id="a63f8-115">**ALIGNED**</span><span class="sxs-lookup"><span data-stu-id="a63f8-115">**ALIGNED**</span></span><br /> <span data-ttu-id="a63f8-116">所有分区对齐结构。</span><span class="sxs-lookup"><span data-stu-id="a63f8-116">All partition-aligned structures.</span></span><br /><br /> <span data-ttu-id="a63f8-117">**CL_IDX**</span><span class="sxs-lookup"><span data-stu-id="a63f8-117">**CL_IDX**</span></span><br /> <span data-ttu-id="a63f8-118">表中的所有聚集索引。</span><span class="sxs-lookup"><span data-stu-id="a63f8-118">All clustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="a63f8-119">**IDX**</span><span class="sxs-lookup"><span data-stu-id="a63f8-119">**IDX**</span></span><br /> <span data-ttu-id="a63f8-120">表中的所有聚集索引和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="a63f8-120">All clustered and nonclustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="a63f8-121">只能将这些值中的一个用于此元素。</span><span class="sxs-lookup"><span data-stu-id="a63f8-121">Use only one of these values with this element.</span></span>|  
|<span data-ttu-id="a63f8-122">**默认值**</span><span class="sxs-lookup"><span data-stu-id="a63f8-122">**Default value**</span></span>|<span data-ttu-id="a63f8-123">无。</span><span class="sxs-lookup"><span data-stu-id="a63f8-123">None.</span></span>|  
|<span data-ttu-id="a63f8-124">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="a63f8-124">**Occurrence**</span></span>|<span data-ttu-id="a63f8-125">可选。</span><span class="sxs-lookup"><span data-stu-id="a63f8-125">Optional.</span></span> <span data-ttu-id="a63f8-126">对于每个 `TuningOptions` 元素只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="a63f8-126">Can use only once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a63f8-127">元素关系</span><span class="sxs-lookup"><span data-stu-id="a63f8-127">Element Relationships</span></span>  
  
|<span data-ttu-id="a63f8-128">关系</span><span class="sxs-lookup"><span data-stu-id="a63f8-128">Relationship</span></span>|<span data-ttu-id="a63f8-129">元素</span><span class="sxs-lookup"><span data-stu-id="a63f8-129">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a63f8-130">**父元素**</span><span class="sxs-lookup"><span data-stu-id="a63f8-130">**Parent element**</span></span>|[<span data-ttu-id="a63f8-131">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a63f8-131">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="a63f8-132">**子元素**</span><span class="sxs-lookup"><span data-stu-id="a63f8-132">**Child elements**</span></span>|<span data-ttu-id="a63f8-133">无。</span><span class="sxs-lookup"><span data-stu-id="a63f8-133">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a63f8-134">示例</span><span class="sxs-lookup"><span data-stu-id="a63f8-134">Example</span></span>  
 <span data-ttu-id="a63f8-135">有关此元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="a63f8-135">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63f8-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a63f8-136">See Also</span></span>  
 [<span data-ttu-id="a63f8-137">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="a63f8-137">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
