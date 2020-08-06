---
title: " (DTA) 的 TestServer 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TestServer element
ms.assetid: caa3547a-2cd5-47ad-ace2-a36752835cfe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d1f1fadf76a43caca262652254e8a778602183c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691447"
---
# <a name="testserver-element-dta"></a><span data-ttu-id="5b0fe-102">TestServer 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="5b0fe-102">TestServer Element (DTA)</span></span>
  <span data-ttu-id="5b0fe-103">指定在优化生产服务器时要使用的测试服务器。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-103">Specifies the test server to use when tuning a production server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0fe-104">语法</span><span class="sxs-lookup"><span data-stu-id="5b0fe-104">Syntax</span></span>  
  
```  
  
<TuningOptions>  
  <TestServer>...</TestServer>  
   ...code removed here...  
</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="5b0fe-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="5b0fe-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="5b0fe-106">特征</span><span class="sxs-lookup"><span data-stu-id="5b0fe-106">Characteristic</span></span>|<span data-ttu-id="5b0fe-107">说明</span><span class="sxs-lookup"><span data-stu-id="5b0fe-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5b0fe-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="5b0fe-108">**Data type and length**</span></span>|<span data-ttu-id="5b0fe-109">**string**，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-109">**string**, unlimited length.</span></span>|  
|<span data-ttu-id="5b0fe-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="5b0fe-110">**Default value**</span></span>|<span data-ttu-id="5b0fe-111">无。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-111">None.</span></span>|  
|<span data-ttu-id="5b0fe-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="5b0fe-112">**Occurrence**</span></span>|<span data-ttu-id="5b0fe-113">可选。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-113">Optional.</span></span> <span data-ttu-id="5b0fe-114">对于每个 `TuningOptions` 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="5b0fe-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="5b0fe-115">Element Relationships</span></span>  
  
|<span data-ttu-id="5b0fe-116">关系</span><span class="sxs-lookup"><span data-stu-id="5b0fe-116">Relationship</span></span>|<span data-ttu-id="5b0fe-117">元素</span><span class="sxs-lookup"><span data-stu-id="5b0fe-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="5b0fe-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="5b0fe-118">**Parent element**</span></span>|[<span data-ttu-id="5b0fe-119">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="5b0fe-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="5b0fe-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="5b0fe-120">**Child elements**</span></span>|<span data-ttu-id="5b0fe-121">无。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b0fe-122">示例</span><span class="sxs-lookup"><span data-stu-id="5b0fe-122">Example</span></span>  
 <span data-ttu-id="5b0fe-123">有关此元素的用法示例，请参阅 [减轻生产服务器优化负荷](../../relational-databases/performance/reduce-the-production-server-tuning-load.md)。</span><span class="sxs-lookup"><span data-stu-id="5b0fe-123">For a usage example of this element, see [Reduce the Production Server Tuning Load](../../relational-databases/performance/reduce-the-production-server-tuning-load.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0fe-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b0fe-124">See Also</span></span>  
 [<span data-ttu-id="5b0fe-125">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="5b0fe-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
