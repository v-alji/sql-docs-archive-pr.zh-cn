---
title: " (DTA) 的索引的名称元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 2300e9cf-f0a8-49e6-b1f5-45ffe03ccb5f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a878923a3d483fae5ad6b55421a2b286f15ceb29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693149"
---
# <a name="name-element-for-index-dta"></a><span data-ttu-id="ca69a-102">索引的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ca69a-102">Name Element for Index (DTA)</span></span>
  <span data-ttu-id="ca69a-103">在用户指定的配置中为索引指定一个名称。</span><span class="sxs-lookup"><span data-stu-id="ca69a-103">Specifies a name for an index in the user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca69a-104">语法</span><span class="sxs-lookup"><span data-stu-id="ca69a-104">Syntax</span></span>  
  
```  
  
<Create>  
    <Index>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="ca69a-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="ca69a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="ca69a-106">特征</span><span class="sxs-lookup"><span data-stu-id="ca69a-106">Characteristic</span></span>|<span data-ttu-id="ca69a-107">说明</span><span class="sxs-lookup"><span data-stu-id="ca69a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ca69a-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="ca69a-108">**Data type and length**</span></span>|<span data-ttu-id="ca69a-109">`string`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="ca69a-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="ca69a-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="ca69a-110">**Default value**</span></span>|<span data-ttu-id="ca69a-111">无。</span><span class="sxs-lookup"><span data-stu-id="ca69a-111">None.</span></span>|  
|<span data-ttu-id="ca69a-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="ca69a-112">**Occurrence**</span></span>|<span data-ttu-id="ca69a-113">对于每个 `Index` 元素必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="ca69a-113">Required once for each `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ca69a-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="ca69a-114">Element Relationships</span></span>  
  
|<span data-ttu-id="ca69a-115">关系</span><span class="sxs-lookup"><span data-stu-id="ca69a-115">Relationship</span></span>|<span data-ttu-id="ca69a-116">元素</span><span class="sxs-lookup"><span data-stu-id="ca69a-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ca69a-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="ca69a-117">**Parent element**</span></span>|[<span data-ttu-id="ca69a-118">索引元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ca69a-118">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="ca69a-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="ca69a-119">**Child elements**</span></span>|<span data-ttu-id="ca69a-120">无。</span><span class="sxs-lookup"><span data-stu-id="ca69a-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca69a-121">示例</span><span class="sxs-lookup"><span data-stu-id="ca69a-121">Example</span></span>  
 <span data-ttu-id="ca69a-122">有关此元素的用法示例，请参阅[使用用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="ca69a-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca69a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca69a-123">See Also</span></span>  
 [<span data-ttu-id="ca69a-124">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="ca69a-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
