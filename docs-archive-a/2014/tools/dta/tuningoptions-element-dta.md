---
title: " (DTA) 的 TuningOptions 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fab1c55c9d036424142b2692e8335ea65c22340
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691436"
---
# <a name="tuningoptions-element-dta"></a><span data-ttu-id="f227b-102">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-102">TuningOptions Element (DTA)</span></span>
  <span data-ttu-id="f227b-103">包含用于特定优化会话的优化选项。</span><span class="sxs-lookup"><span data-stu-id="f227b-103">Contains the tuning options for a specific tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f227b-104">语法</span><span class="sxs-lookup"><span data-stu-id="f227b-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="f227b-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="f227b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="f227b-106">特征</span><span class="sxs-lookup"><span data-stu-id="f227b-106">Characteristic</span></span>|<span data-ttu-id="f227b-107">说明</span><span class="sxs-lookup"><span data-stu-id="f227b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f227b-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="f227b-108">**Data type and length**</span></span>|<span data-ttu-id="f227b-109">无。</span><span class="sxs-lookup"><span data-stu-id="f227b-109">None.</span></span>|  
|<span data-ttu-id="f227b-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="f227b-110">**Default value**</span></span>|<span data-ttu-id="f227b-111">无。</span><span class="sxs-lookup"><span data-stu-id="f227b-111">None.</span></span>|  
|<span data-ttu-id="f227b-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="f227b-112">**Occurrence**</span></span>|<span data-ttu-id="f227b-113">可选。</span><span class="sxs-lookup"><span data-stu-id="f227b-113">Optional.</span></span> <span data-ttu-id="f227b-114">如果已使用，则每个 `DTAInput` 元素只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="f227b-114">If used, can only be used once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="f227b-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="f227b-115">Element Relationships</span></span>  
  
|<span data-ttu-id="f227b-116">关系</span><span class="sxs-lookup"><span data-stu-id="f227b-116">Relationship</span></span>|<span data-ttu-id="f227b-117">元素</span><span class="sxs-lookup"><span data-stu-id="f227b-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="f227b-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="f227b-118">**Parent element**</span></span>|[<span data-ttu-id="f227b-119">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-119">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="f227b-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="f227b-120">**Child elements**</span></span>|<span data-ttu-id="f227b-121">`ReportSet` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-121">`ReportSet` element.</span></span> <span data-ttu-id="f227b-122">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-122">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="f227b-123">`TuningLogTable` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-123">`TuningLogTable` element.</span></span> <span data-ttu-id="f227b-124">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-124">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="f227b-125">`NumberOfEvents` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-125">`NumberOfEvents` element.</span></span> <span data-ttu-id="f227b-126">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-126">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> [<span data-ttu-id="f227b-127">TuningTimeInMin 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-127">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-128">StorageBoundInMB 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-128">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)<br /><br /> <span data-ttu-id="f227b-129">`MaxKeyColumnsInIndex` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-129">`MaxKeyColumnsInIndex` element.</span></span> <span data-ttu-id="f227b-130">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-130">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="f227b-131">`MaxColumnsInIndex` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-131">`MaxColumnsInIndex` element.</span></span> <span data-ttu-id="f227b-132">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-132">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="f227b-133">`MinPercentageImprovement` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-133">`MinPercentageImprovement` element.</span></span> <span data-ttu-id="f227b-134">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)</span><span class="sxs-lookup"><span data-stu-id="f227b-134">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100)</span></span><br /><br /> [<span data-ttu-id="f227b-135">TestServer 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-135">TestServer Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-136">FeatureSet 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-136">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-137">分区元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-137">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-138">DropOnlyMode 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-138">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-139">KeepExisting 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-139">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-140">OnlineIndexOperation 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-140">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)<br /><br /> [<span data-ttu-id="f227b-141">DatabaseToConnect 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="f227b-141">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)<br /><br /> <span data-ttu-id="f227b-142">`IgnoreConstantsInWorkload` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-142">`IgnoreConstantsInWorkload` element.</span></span> <span data-ttu-id="f227b-143">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-143">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="f227b-144">`RetainShellDB` 元素。</span><span class="sxs-lookup"><span data-stu-id="f227b-144">`RetainShellDB` element.</span></span> <span data-ttu-id="f227b-145">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="f227b-145">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f227b-146">示例</span><span class="sxs-lookup"><span data-stu-id="f227b-146">Example</span></span>  
 <span data-ttu-id="f227b-147">有关元素的示例 `TuningOptions` ，请参阅[&#40;DTA&#41;的 XML 输入文件示例](xml-input-file-samples-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="f227b-147">For examples of the `TuningOptions` element, see the [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f227b-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f227b-148">See Also</span></span>  
 [<span data-ttu-id="f227b-149">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="f227b-149">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
