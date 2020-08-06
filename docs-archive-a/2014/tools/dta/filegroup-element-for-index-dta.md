---
title: 用于索引 (DTA) 的文件组元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ed8ea723d6c0798b93e16411ee47d6e956c6c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691448"
---
# <a name="filegroup-element-for-index-dta"></a><span data-ttu-id="a72c3-102">索引的文件组元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a72c3-102">Filegroup Element for Index (DTA)</span></span>
  <span data-ttu-id="a72c3-103">指定要针对用户指定的配置，对其创建索引的文件组。</span><span class="sxs-lookup"><span data-stu-id="a72c3-103">Specifies the filegroup on which the index is to be created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a72c3-104">语法</span><span class="sxs-lookup"><span data-stu-id="a72c3-104">Syntax</span></span>  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="a72c3-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="a72c3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="a72c3-106">特征</span><span class="sxs-lookup"><span data-stu-id="a72c3-106">Characteristic</span></span>|<span data-ttu-id="a72c3-107">说明</span><span class="sxs-lookup"><span data-stu-id="a72c3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a72c3-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="a72c3-108">**Data type and length**</span></span>|<span data-ttu-id="a72c3-109">`string`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="a72c3-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="a72c3-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="a72c3-110">**Default value**</span></span>|<span data-ttu-id="a72c3-111">无。</span><span class="sxs-lookup"><span data-stu-id="a72c3-111">None.</span></span>|  
|<span data-ttu-id="a72c3-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="a72c3-112">**Occurrence**</span></span>|<span data-ttu-id="a72c3-113">可选。</span><span class="sxs-lookup"><span data-stu-id="a72c3-113">Optional.</span></span> <span data-ttu-id="a72c3-114">对于每个 `Index` 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="a72c3-114">Can use once for each `Index` element.</span></span> <span data-ttu-id="a72c3-115">如果为 `PartitionScheme` 元素指定了 `PartitionColumn` 和 `Index` 元素，则不能使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a72c3-115">This element cannot be used if the `PartitionScheme` and `PartitionColumn` elements are specified for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a72c3-116">元素关系</span><span class="sxs-lookup"><span data-stu-id="a72c3-116">Element Relationships</span></span>  
  
|<span data-ttu-id="a72c3-117">关系</span><span class="sxs-lookup"><span data-stu-id="a72c3-117">Relationship</span></span>|<span data-ttu-id="a72c3-118">元素</span><span class="sxs-lookup"><span data-stu-id="a72c3-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a72c3-119">**父元素**</span><span class="sxs-lookup"><span data-stu-id="a72c3-119">**Parent element**</span></span>|[<span data-ttu-id="a72c3-120">索引元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a72c3-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="a72c3-121">**子元素**</span><span class="sxs-lookup"><span data-stu-id="a72c3-121">**Child elements**</span></span>|<span data-ttu-id="a72c3-122">无。</span><span class="sxs-lookup"><span data-stu-id="a72c3-122">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a72c3-123">示例</span><span class="sxs-lookup"><span data-stu-id="a72c3-123">Example</span></span>  
 <span data-ttu-id="a72c3-124">有关此元素的用法示例，请参阅[使用用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="a72c3-124">For a usage example of this element, see [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a72c3-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a72c3-125">See Also</span></span>  
 [<span data-ttu-id="a72c3-126">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="a72c3-126">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
