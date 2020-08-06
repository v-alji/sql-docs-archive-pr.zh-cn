---
title: TuningTimeInMin 元素 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dae3fe4e9ac3126f43ec017c34d2bc548fda6d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691435"
---
# <a name="tuningtimeinmin-element-dta"></a><span data-ttu-id="92fd2-102">TuningTimeInMin 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="92fd2-102">TuningTimeInMin Element (DTA)</span></span>
  <span data-ttu-id="92fd2-103">指定优化会话的最大时间长度（分钟）。</span><span class="sxs-lookup"><span data-stu-id="92fd2-103">Specifies the maximum length of a tuning session in minutes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fd2-104">语法</span><span class="sxs-lookup"><span data-stu-id="92fd2-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="92fd2-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="92fd2-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="92fd2-106">特征</span><span class="sxs-lookup"><span data-stu-id="92fd2-106">Characteristic</span></span>|<span data-ttu-id="92fd2-107">说明</span><span class="sxs-lookup"><span data-stu-id="92fd2-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="92fd2-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="92fd2-108">**Data type and length**</span></span>|<span data-ttu-id="92fd2-109">`unsignedInt`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="92fd2-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="92fd2-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="92fd2-110">**Default value**</span></span>|<span data-ttu-id="92fd2-111">480 分钟（8 小时）。</span><span class="sxs-lookup"><span data-stu-id="92fd2-111">480 minutes (8 hours).</span></span>|  
|<span data-ttu-id="92fd2-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="92fd2-112">**Occurrence**</span></span>|<span data-ttu-id="92fd2-113">除非已为 `NumberOfEvents` 元素指定了一个值，否则为必需项。</span><span class="sxs-lookup"><span data-stu-id="92fd2-113">Required unless a value has been specified for the `NumberOfEvents` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="92fd2-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="92fd2-114">Element Relationships</span></span>  
  
|<span data-ttu-id="92fd2-115">关系</span><span class="sxs-lookup"><span data-stu-id="92fd2-115">Relationship</span></span>|<span data-ttu-id="92fd2-116">元素</span><span class="sxs-lookup"><span data-stu-id="92fd2-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="92fd2-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="92fd2-117">**Parent element**</span></span>|[<span data-ttu-id="92fd2-118">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="92fd2-118">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="92fd2-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="92fd2-119">**Child elements**</span></span>|<span data-ttu-id="92fd2-120">无</span><span class="sxs-lookup"><span data-stu-id="92fd2-120">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="92fd2-121">示例</span><span class="sxs-lookup"><span data-stu-id="92fd2-121">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="92fd2-122">说明</span><span class="sxs-lookup"><span data-stu-id="92fd2-122">Description</span></span>  
 <span data-ttu-id="92fd2-123">以下代码示例显示如何将 12 个小时设置为最长优化时间：</span><span class="sxs-lookup"><span data-stu-id="92fd2-123">The following code example shows how to set 12 hours as the maximum tuning time:</span></span>  
  
## <a name="code"></a><span data-ttu-id="92fd2-124">代码</span><span class="sxs-lookup"><span data-stu-id="92fd2-124">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92fd2-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92fd2-125">See Also</span></span>  
 [<span data-ttu-id="92fd2-126">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="92fd2-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
