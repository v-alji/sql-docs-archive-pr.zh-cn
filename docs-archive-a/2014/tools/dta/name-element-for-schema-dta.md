---
title: 架构 (DTA) 的名称元素 |Microsoft Docs
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
ms.assetid: 014e4854-fed2-454b-8557-5f7c5bb6b17a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 678a6d58b35b25be2aed6d91fcae7ceb2640bdcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690957"
---
# <a name="name-element-for-schema-dta"></a><span data-ttu-id="c7ad6-102">架构的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c7ad6-102">Name Element for Schema (DTA)</span></span>
  <span data-ttu-id="c7ad6-103">包含架构的名称。</span><span class="sxs-lookup"><span data-stu-id="c7ad6-103">Contains name of the schema.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ad6-104">语法</span><span class="sxs-lookup"><span data-stu-id="c7ad6-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here  
    <Schema>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c7ad6-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="c7ad6-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="c7ad6-106">特征</span><span class="sxs-lookup"><span data-stu-id="c7ad6-106">Characteristic</span></span>|<span data-ttu-id="c7ad6-107">说明</span><span class="sxs-lookup"><span data-stu-id="c7ad6-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c7ad6-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="c7ad6-108">**Data type and length**</span></span>|<span data-ttu-id="c7ad6-109">`string`，介于 1 到 255 个字符之间</span><span class="sxs-lookup"><span data-stu-id="c7ad6-109">`string`, between 1 and 255 characters</span></span>|  
|<span data-ttu-id="c7ad6-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="c7ad6-110">**Default value**</span></span>|<span data-ttu-id="c7ad6-111">无。</span><span class="sxs-lookup"><span data-stu-id="c7ad6-111">None.</span></span>|  
|<span data-ttu-id="c7ad6-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="c7ad6-112">**Occurrence**</span></span>|<span data-ttu-id="c7ad6-113">要求每个 **架构** 元素出现一次。</span><span class="sxs-lookup"><span data-stu-id="c7ad6-113">Required once per **Schema** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c7ad6-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="c7ad6-114">Element Relationships</span></span>  
  
|<span data-ttu-id="c7ad6-115">关系</span><span class="sxs-lookup"><span data-stu-id="c7ad6-115">Relationship</span></span>|<span data-ttu-id="c7ad6-116">元素</span><span class="sxs-lookup"><span data-stu-id="c7ad6-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c7ad6-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="c7ad6-117">**Parent element**</span></span>|[<span data-ttu-id="c7ad6-118">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c7ad6-118">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="c7ad6-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="c7ad6-119">**Child elements**</span></span>|<span data-ttu-id="c7ad6-120">无。</span><span class="sxs-lookup"><span data-stu-id="c7ad6-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7ad6-121">示例</span><span class="sxs-lookup"><span data-stu-id="c7ad6-121">Example</span></span>  
 <span data-ttu-id="c7ad6-122">有关此元素的使用示例，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="c7ad6-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ad6-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7ad6-123">See Also</span></span>  
 [<span data-ttu-id="c7ad6-124">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="c7ad6-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
