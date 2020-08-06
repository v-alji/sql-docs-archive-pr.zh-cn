---
title: DTA) 的列 (名称元素 |Microsoft Docs
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
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
author: stevestein
ms.author: sstein
ms.openlocfilehash: fad3d9a86a7c5db6b6a7503dc90b5a1540e3618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682525"
---
# <a name="name-element-for-column-dta"></a><span data-ttu-id="dee07-102">列的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="dee07-102">Name Element for Column (DTA)</span></span>
  <span data-ttu-id="dee07-103">在用户指定的配置中指定索引列的名称。</span><span class="sxs-lookup"><span data-stu-id="dee07-103">Specifies the name for an index column in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee07-104">语法</span><span class="sxs-lookup"><span data-stu-id="dee07-104">Syntax</span></span>  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="dee07-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="dee07-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="dee07-106">特征</span><span class="sxs-lookup"><span data-stu-id="dee07-106">Characteristic</span></span>|<span data-ttu-id="dee07-107">说明</span><span class="sxs-lookup"><span data-stu-id="dee07-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="dee07-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="dee07-108">**Data type and length**</span></span>|<span data-ttu-id="dee07-109">`string`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="dee07-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="dee07-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="dee07-110">**Default value**</span></span>|<span data-ttu-id="dee07-111">无。</span><span class="sxs-lookup"><span data-stu-id="dee07-111">None.</span></span>|  
|<span data-ttu-id="dee07-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="dee07-112">**Occurrence**</span></span>|<span data-ttu-id="dee07-113">对于每个 `Column` 元素必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="dee07-113">Required once for each `Column` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="dee07-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="dee07-114">Element Relationships</span></span>  
  
|<span data-ttu-id="dee07-115">关系</span><span class="sxs-lookup"><span data-stu-id="dee07-115">Relationship</span></span>|<span data-ttu-id="dee07-116">元素</span><span class="sxs-lookup"><span data-stu-id="dee07-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="dee07-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="dee07-117">**Parent element**</span></span>|[<span data-ttu-id="dee07-118">索引的列元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="dee07-118">Column Element for Index &#40;DTA&#41;</span></span>](column-element-for-index-dta.md)|  
|<span data-ttu-id="dee07-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="dee07-119">**Child elements**</span></span>|<span data-ttu-id="dee07-120">无。</span><span class="sxs-lookup"><span data-stu-id="dee07-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dee07-121">示例</span><span class="sxs-lookup"><span data-stu-id="dee07-121">Example</span></span>  
 <span data-ttu-id="dee07-122">有关此元素的用法示例，请参阅[使用用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="dee07-122">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee07-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dee07-123">See Also</span></span>  
 [<span data-ttu-id="dee07-124">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="dee07-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  