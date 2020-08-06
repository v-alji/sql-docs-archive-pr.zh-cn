---
title: " (DTA) 的 DropOnlyMode 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b274dc394a933308cf2161cc271d09b8391900c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682532"
---
# <a name="droponlymode-element-dta"></a><span data-ttu-id="c3371-102">DropOnlyMode 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c3371-102">DropOnlyMode Element (DTA)</span></span>
  <span data-ttu-id="c3371-103">指定数据库引擎优化顾问在优化会话过程中只应考虑删除现有的索引、索引视图或分区。</span><span class="sxs-lookup"><span data-stu-id="c3371-103">Specifies that Database Engine Tuning Advisor should only consider dropping existing indexes, indexed views, or partitions during the tuning session.</span></span> <span data-ttu-id="c3371-104">如果指定了此优化选项，则不考虑任何新物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="c3371-104">No new physical design structures are considered when this tuning option is specified.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3371-105">语法</span><span class="sxs-lookup"><span data-stu-id="c3371-105">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c3371-106">元素特征</span><span class="sxs-lookup"><span data-stu-id="c3371-106">Element Characteristics</span></span>  
  
|<span data-ttu-id="c3371-107">特征</span><span class="sxs-lookup"><span data-stu-id="c3371-107">Characteristic</span></span>|<span data-ttu-id="c3371-108">说明</span><span class="sxs-lookup"><span data-stu-id="c3371-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c3371-109">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="c3371-109">**Data type and length**</span></span>|<span data-ttu-id="c3371-110">无。</span><span class="sxs-lookup"><span data-stu-id="c3371-110">None.</span></span>|  
|<span data-ttu-id="c3371-111">**默认值**</span><span class="sxs-lookup"><span data-stu-id="c3371-111">**Default value**</span></span>|<span data-ttu-id="c3371-112">无。</span><span class="sxs-lookup"><span data-stu-id="c3371-112">None.</span></span>|  
|<span data-ttu-id="c3371-113">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="c3371-113">**Occurrence**</span></span>|<span data-ttu-id="c3371-114">可选。</span><span class="sxs-lookup"><span data-stu-id="c3371-114">Optional.</span></span> <span data-ttu-id="c3371-115">对于每个 `TuningOptions` 元素只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="c3371-115">Can use only once for each `TuningOptions` element.</span></span> <span data-ttu-id="c3371-116">如果在 `TuningOptions` 元素中指定了下列元素，则不能使用此元素：</span><span class="sxs-lookup"><span data-stu-id="c3371-116">Cannot be used if the following elements are specified in the `TuningOptions` element:</span></span><br /><br /> [<span data-ttu-id="c3371-117">FeatureSet 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c3371-117">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="c3371-118">分区元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c3371-118">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> <span data-ttu-id="c3371-119">将 [KeepExisting 元素 (DTA)](keepexisting-element-dta.md) 设置为 **ALL**</span><span class="sxs-lookup"><span data-stu-id="c3371-119">[KeepExisting Element &#40;DTA&#41;](keepexisting-element-dta.md) is set to **ALL**</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c3371-120">元素关系</span><span class="sxs-lookup"><span data-stu-id="c3371-120">Element Relationships</span></span>  
  
|<span data-ttu-id="c3371-121">关系</span><span class="sxs-lookup"><span data-stu-id="c3371-121">Relationship</span></span>|<span data-ttu-id="c3371-122">元素</span><span class="sxs-lookup"><span data-stu-id="c3371-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c3371-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="c3371-123">**Parent element**</span></span>|[<span data-ttu-id="c3371-124">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c3371-124">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="c3371-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="c3371-125">**Child elements**</span></span>|<span data-ttu-id="c3371-126">无。</span><span class="sxs-lookup"><span data-stu-id="c3371-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3371-127">示例</span><span class="sxs-lookup"><span data-stu-id="c3371-127">Example</span></span>  
 <span data-ttu-id="c3371-128">以下示例说明数据库引擎优化顾问 XML 输入文件的 `TuningOptions` 部分，其中指定了 `DropOnlyMode`。</span><span class="sxs-lookup"><span data-stu-id="c3371-128">The following example shows the `TuningOptions` section of a Database Engine Tuning Advisor XML input file where the `DropOnlyMode` is specified.</span></span> <span data-ttu-id="c3371-129">本例中，优化时间限定为 24 小时（1440 分钟），并且所有现有的聚集索引和非聚集索引将被删除：</span><span class="sxs-lookup"><span data-stu-id="c3371-129">In this example the tuning time is limited to 24 hours (1440 minutes) and all existing clustered and nonclustered indexes will be considered for dropping:</span></span>  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3371-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3371-130">See Also</span></span>  
 [<span data-ttu-id="c3371-131">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="c3371-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
