---
title: 配置元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d11938d9a9a694f994a3ea977022a393cbae23d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682549"
---
# <a name="configuration-element-dta"></a><span data-ttu-id="098e0-102">配置元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="098e0-102">Configuration Element (DTA)</span></span>
  <span data-ttu-id="098e0-103">指定一个用户指定的配置（由现有和假想的物理设计结构组成），以便数据库引擎优化顾问在优化工作负荷时进行分析。</span><span class="sxs-lookup"><span data-stu-id="098e0-103">Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098e0-104">语法</span><span class="sxs-lookup"><span data-stu-id="098e0-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="098e0-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="098e0-105">Element Attributes</span></span>  
  
|<span data-ttu-id="098e0-106">配置属性</span><span class="sxs-lookup"><span data-stu-id="098e0-106">Configuration Attribute</span></span>|<span data-ttu-id="098e0-107">说明</span><span class="sxs-lookup"><span data-stu-id="098e0-107">Description</span></span>|  
|-----------------------------|-----------------|  
|`SpecificationMode`|<span data-ttu-id="098e0-108">可选。</span><span class="sxs-lookup"><span data-stu-id="098e0-108">Optional.</span></span> <span data-ttu-id="098e0-109">指定数据库引擎优化顾问是依据当前的现有配置分析指定的配置，还是将指定的配置作为一个全新的独立配置进行分析。</span><span class="sxs-lookup"><span data-stu-id="098e0-109">Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one.</span></span> <span data-ttu-id="098e0-110">使用 string 数据类型将此属性指定为以下允许  值之一：</span><span class="sxs-lookup"><span data-stu-id="098e0-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="098e0-111">`Relative`:</span><span class="sxs-lookup"><span data-stu-id="098e0-111">`Relative`:</span></span> <br />                  <span data-ttu-id="098e0-112">依据被优化的数据库中的物理设计结构（索引、索引视图和分区）的当前现有配置来评估指定的配置。</span><span class="sxs-lookup"><span data-stu-id="098e0-112">Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned.</span></span> <span data-ttu-id="098e0-113">例如：</span><span class="sxs-lookup"><span data-stu-id="098e0-113">For example:</span></span> <br />`<Configuration SpecificationMode="Relative">`<br /><br /> <span data-ttu-id="098e0-114">`Absolute`:</span><span class="sxs-lookup"><span data-stu-id="098e0-114">`Absolute`:</span></span> <br />                  <span data-ttu-id="098e0-115">将指定配置作为独立配置进行评估。</span><span class="sxs-lookup"><span data-stu-id="098e0-115">Evaluates the specified configuration as a standalone configuration.</span></span> <span data-ttu-id="098e0-116">如果指定 Absolute，则数据库引擎优化顾问将不考虑现有配置。</span><span class="sxs-lookup"><span data-stu-id="098e0-116">When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration.</span></span> <span data-ttu-id="098e0-117">例如：</span><span class="sxs-lookup"><span data-stu-id="098e0-117">For example:</span></span><br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="098e0-118">元素特征</span><span class="sxs-lookup"><span data-stu-id="098e0-118">Element Characteristics</span></span>  
  
|<span data-ttu-id="098e0-119">特征</span><span class="sxs-lookup"><span data-stu-id="098e0-119">Characteristic</span></span>|<span data-ttu-id="098e0-120">说明</span><span class="sxs-lookup"><span data-stu-id="098e0-120">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="098e0-121">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="098e0-121">**Data type and length**</span></span>|<span data-ttu-id="098e0-122">无。</span><span class="sxs-lookup"><span data-stu-id="098e0-122">None.</span></span>|  
|<span data-ttu-id="098e0-123">**默认值**</span><span class="sxs-lookup"><span data-stu-id="098e0-123">**Default value**</span></span>|<span data-ttu-id="098e0-124">无。</span><span class="sxs-lookup"><span data-stu-id="098e0-124">None.</span></span>|  
|<span data-ttu-id="098e0-125">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="098e0-125">**Occurrence**</span></span>|<span data-ttu-id="098e0-126">可选。</span><span class="sxs-lookup"><span data-stu-id="098e0-126">Optional.</span></span> <span data-ttu-id="098e0-127">对于每个 `DTAInput` 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="098e0-127">Can use once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="098e0-128">元素关系</span><span class="sxs-lookup"><span data-stu-id="098e0-128">Element Relationships</span></span>  
  
|<span data-ttu-id="098e0-129">关系</span><span class="sxs-lookup"><span data-stu-id="098e0-129">Relationship</span></span>|<span data-ttu-id="098e0-130">元素</span><span class="sxs-lookup"><span data-stu-id="098e0-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="098e0-131">**父元素**</span><span class="sxs-lookup"><span data-stu-id="098e0-131">**Parent element**</span></span>|[<span data-ttu-id="098e0-132">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="098e0-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="098e0-133">**子元素**</span><span class="sxs-lookup"><span data-stu-id="098e0-133">**Child elements**</span></span>|[<span data-ttu-id="098e0-134">用于配置的服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="098e0-134">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="098e0-135">示例</span><span class="sxs-lookup"><span data-stu-id="098e0-135">Example</span></span>  
 <span data-ttu-id="098e0-136">有关此元素的用法示例，请参阅[用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="098e0-136">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098e0-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="098e0-137">See Also</span></span>  
 [<span data-ttu-id="098e0-138">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="098e0-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
