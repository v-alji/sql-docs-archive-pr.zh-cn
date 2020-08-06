---
title: OnlineIndexOperation 元素 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48943c1b31d7a0a24ae939050d44494476e50034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588796"
---
# <a name="onlineindexoperation-element-dta"></a><span data-ttu-id="2ab1d-102">OnlineIndexOperation 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2ab1d-102">OnlineIndexOperation Element (DTA)</span></span>
  <span data-ttu-id="2ab1d-103">指定是否可联机创建数据库引擎优化顾问建议的索引、索引视图或分区。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-103">Specifies whether the indexes, indexed views, or partitions that Database Engine Tuning Advisor recommends can be created online.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ab1d-104">语法</span><span class="sxs-lookup"><span data-stu-id="2ab1d-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="2ab1d-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="2ab1d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="2ab1d-106">特征</span><span class="sxs-lookup"><span data-stu-id="2ab1d-106">Characteristic</span></span>|<span data-ttu-id="2ab1d-107">说明</span><span class="sxs-lookup"><span data-stu-id="2ab1d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2ab1d-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-108">**Data type and length**</span></span>|<span data-ttu-id="2ab1d-109">`string`，无最大长度。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="2ab1d-110">**允许的值**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-110">**Allowed values**</span></span>|<span data-ttu-id="2ab1d-111">**OFF**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-111">**OFF**</span></span><br /> <span data-ttu-id="2ab1d-112">建议的物理设计结构都无法联机创建。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-112">No recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="2ab1d-113">**ON**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-113">**ON**</span></span><br /> <span data-ttu-id="2ab1d-114">所有建议的物理设计结构都可以联机创建。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-114">All recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="2ab1d-115">**MIXED**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-115">**MIXED**</span></span><br /> <span data-ttu-id="2ab1d-116">数据库引擎优化顾问会尝试建议可以联机创建的物理设计结构。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-116">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span><br /><br /> <span data-ttu-id="2ab1d-117">将这些值中的一个值用于此元素。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-117">Use one of these values with this element.</span></span> <span data-ttu-id="2ab1d-118">如果联机创建索引，则将向其对象定义中追加 **ONLINE = ON** 关键字。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-118">If indexes are created online, the keyword **ONLINE = ON** is appended to its object definition.</span></span>|  
|<span data-ttu-id="2ab1d-119">**默认值**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-119">**Default value**</span></span>|<span data-ttu-id="2ab1d-120">无。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-120">None.</span></span>|  
|<span data-ttu-id="2ab1d-121">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-121">**Occurrence**</span></span>|<span data-ttu-id="2ab1d-122">可选。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-122">Optional.</span></span> <span data-ttu-id="2ab1d-123">如果使用 `TuningOptions` 元素，则只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-123">If used, can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2ab1d-124">元素关系</span><span class="sxs-lookup"><span data-stu-id="2ab1d-124">Element Relationships</span></span>  
  
|<span data-ttu-id="2ab1d-125">关系</span><span class="sxs-lookup"><span data-stu-id="2ab1d-125">Relationship</span></span>|<span data-ttu-id="2ab1d-126">元素</span><span class="sxs-lookup"><span data-stu-id="2ab1d-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2ab1d-127">**父元素**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-127">**Parent element**</span></span>|[<span data-ttu-id="2ab1d-128">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2ab1d-128">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="2ab1d-129">**子元素**</span><span class="sxs-lookup"><span data-stu-id="2ab1d-129">**Child elements**</span></span>|<span data-ttu-id="2ab1d-130">无。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ab1d-131">示例</span><span class="sxs-lookup"><span data-stu-id="2ab1d-131">Example</span></span>  
 <span data-ttu-id="2ab1d-132">有关此元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab1d-132">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab1d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ab1d-133">See Also</span></span>  
 [<span data-ttu-id="2ab1d-134">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="2ab1d-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
