---
title: " (DTA) 的 FeatureSet 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d36c28b24a56ef2dcdf69578fb7e8c196306a416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692041"
---
# <a name="featureset-element-dta"></a><span data-ttu-id="c77f6-102">FeatureSet 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c77f6-102">FeatureSet Element (DTA)</span></span>
  <span data-ttu-id="c77f6-103">包含数据库引擎优化顾问在分析中使用的物理设计结构（索引或索引视图）。</span><span class="sxs-lookup"><span data-stu-id="c77f6-103">Contains the physical design structures (indexes or indexed views) that you would like Database Engine Tuning Advisor to use during analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c77f6-104">语法</span><span class="sxs-lookup"><span data-stu-id="c77f6-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c77f6-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="c77f6-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="c77f6-106">特征</span><span class="sxs-lookup"><span data-stu-id="c77f6-106">Characteristic</span></span>|<span data-ttu-id="c77f6-107">说明</span><span class="sxs-lookup"><span data-stu-id="c77f6-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c77f6-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="c77f6-108">**Data type and length**</span></span>|<span data-ttu-id="c77f6-109">`string`，无最大长度。</span><span class="sxs-lookup"><span data-stu-id="c77f6-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="c77f6-110">**允许的值**</span><span class="sxs-lookup"><span data-stu-id="c77f6-110">**Allowed values**</span></span>|<span data-ttu-id="c77f6-111">**IDX_IV**</span><span class="sxs-lookup"><span data-stu-id="c77f6-111">**IDX_IV**</span></span><br /> <span data-ttu-id="c77f6-112">索引和索引视图。</span><span class="sxs-lookup"><span data-stu-id="c77f6-112">Indexes and indexed views.</span></span><br /><br /> <span data-ttu-id="c77f6-113">**IDX**</span><span class="sxs-lookup"><span data-stu-id="c77f6-113">**IDX**</span></span><br /> <span data-ttu-id="c77f6-114">仅限索引。</span><span class="sxs-lookup"><span data-stu-id="c77f6-114">Indexes only.</span></span><br /><br /> <span data-ttu-id="c77f6-115">**IV**</span><span class="sxs-lookup"><span data-stu-id="c77f6-115">**IV**</span></span><br /> <span data-ttu-id="c77f6-116">仅限索引视图。</span><span class="sxs-lookup"><span data-stu-id="c77f6-116">Indexed views only.</span></span><br /><br /> <span data-ttu-id="c77f6-117">**NCL_IDX**</span><span class="sxs-lookup"><span data-stu-id="c77f6-117">**NCL_IDX**</span></span><br /> <span data-ttu-id="c77f6-118">仅限非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="c77f6-118">Nonclustered indexes only.</span></span><br /><br /> <span data-ttu-id="c77f6-119">将这些值中的一个值用于此元素。</span><span class="sxs-lookup"><span data-stu-id="c77f6-119">Use one of these values with this element.</span></span>|  
|<span data-ttu-id="c77f6-120">**默认值**</span><span class="sxs-lookup"><span data-stu-id="c77f6-120">**Default value**</span></span>|<span data-ttu-id="c77f6-121">**IDX**</span><span class="sxs-lookup"><span data-stu-id="c77f6-121">**IDX**</span></span>|  
|<span data-ttu-id="c77f6-122">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="c77f6-122">**Occurrence**</span></span>|<span data-ttu-id="c77f6-123">除非使用了 `TuningOptions` 元素，否则对每个 `DropOnlyMode` 元素仅需要一次。</span><span class="sxs-lookup"><span data-stu-id="c77f6-123">Required once for each `TuningOptions` element, unless the `DropOnlyMode` element is used.</span></span> <span data-ttu-id="c77f6-124">如果使用 `DropOnlyMode`，则无法使用 `FeatureSet`。</span><span class="sxs-lookup"><span data-stu-id="c77f6-124">If `DropOnlyMode` is used, you cannot use `FeatureSet`.</span></span> <span data-ttu-id="c77f6-125">这两种元素是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="c77f6-125">These elements are mutually exclusive.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c77f6-126">元素关系</span><span class="sxs-lookup"><span data-stu-id="c77f6-126">Element Relationships</span></span>  
  
|<span data-ttu-id="c77f6-127">关系</span><span class="sxs-lookup"><span data-stu-id="c77f6-127">Relationship</span></span>|<span data-ttu-id="c77f6-128">元素</span><span class="sxs-lookup"><span data-stu-id="c77f6-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c77f6-129">**父元素**</span><span class="sxs-lookup"><span data-stu-id="c77f6-129">**Parent element**</span></span>|[<span data-ttu-id="c77f6-130">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c77f6-130">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="c77f6-131">**子元素**</span><span class="sxs-lookup"><span data-stu-id="c77f6-131">**Child elements**</span></span>|<span data-ttu-id="c77f6-132">无。</span><span class="sxs-lookup"><span data-stu-id="c77f6-132">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c77f6-133">示例</span><span class="sxs-lookup"><span data-stu-id="c77f6-133">Example</span></span>  
 <span data-ttu-id="c77f6-134">有关此元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="c77f6-134">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77f6-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c77f6-135">See Also</span></span>  
 [<span data-ttu-id="c77f6-136">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="c77f6-136">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
