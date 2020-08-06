---
title: " (ssbdiagnose) 的横幅元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694200"
---
# <a name="banner-element-ssbdiagnose"></a><span data-ttu-id="0fae5-102">Banner 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="0fae5-102">Banner Element (ssbdiagnose)</span></span>
  <span data-ttu-id="0fae5-103">标识生成 **ssbdiagnose** 输出 XML 文件的实用工具。</span><span class="sxs-lookup"><span data-stu-id="0fae5-103">Identifies which utility generated the **ssbdiagnose** output XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fae5-104">语法</span><span class="sxs-lookup"><span data-stu-id="0fae5-104">Syntax</span></span>  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="0fae5-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="0fae5-105">Element Attributes</span></span>  
  
|<span data-ttu-id="0fae5-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="0fae5-106">Attribute</span></span>|<span data-ttu-id="0fae5-107">说明</span><span class="sxs-lookup"><span data-stu-id="0fae5-107">Description</span></span>|  
|---------------|-----------------|  
|`title`|<span data-ttu-id="0fae5-108">标识生成 **ssbdiagnose** XML 输出文件的实用工具。</span><span class="sxs-lookup"><span data-stu-id="0fae5-108">Identifies the utility that generated the **ssbdiagnose** XML output file.</span></span>|  
|`product`|<span data-ttu-id="0fae5-109">标识生成 **ssbdiagnose** XML 输出文件的产品。</span><span class="sxs-lookup"><span data-stu-id="0fae5-109">Identifies the product that generated the **ssbdiagnose** XML output file.</span></span>|  
|`version`|<span data-ttu-id="0fae5-110">标识生成 XML 输出文件的实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="0fae5-110">Identifies which version of the utility generated the XML output file.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="0fae5-111">元素特征</span><span class="sxs-lookup"><span data-stu-id="0fae5-111">Element Characteristics</span></span>  
  
|<span data-ttu-id="0fae5-112">特征</span><span class="sxs-lookup"><span data-stu-id="0fae5-112">Characteristic</span></span>|<span data-ttu-id="0fae5-113">说明</span><span class="sxs-lookup"><span data-stu-id="0fae5-113">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="0fae5-114">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="0fae5-114">**Data type and length**</span></span>|<span data-ttu-id="0fae5-115">无。</span><span class="sxs-lookup"><span data-stu-id="0fae5-115">None.</span></span>|  
|<span data-ttu-id="0fae5-116">**默认值**</span><span class="sxs-lookup"><span data-stu-id="0fae5-116">**Default value**</span></span>|<span data-ttu-id="0fae5-117">无。</span><span class="sxs-lookup"><span data-stu-id="0fae5-117">None.</span></span>|  
|<span data-ttu-id="0fae5-118">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="0fae5-118">**Occurrence**</span></span>|<span data-ttu-id="0fae5-119">每个 **ssbdiagnose** 输出 XML 文件出现一次。</span><span class="sxs-lookup"><span data-stu-id="0fae5-119">Occurs once per **ssbdiagnose** output XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="0fae5-120">元素关系</span><span class="sxs-lookup"><span data-stu-id="0fae5-120">Element Relationships</span></span>  
  
|<span data-ttu-id="0fae5-121">关系</span><span class="sxs-lookup"><span data-stu-id="0fae5-121">Relationship</span></span>|<span data-ttu-id="0fae5-122">元素</span><span class="sxs-lookup"><span data-stu-id="0fae5-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="0fae5-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="0fae5-123">**Parent element**</span></span>|[<span data-ttu-id="0fae5-124">DiagnosticInformation 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="0fae5-124">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="0fae5-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="0fae5-125">**Child elements**</span></span>|<span data-ttu-id="0fae5-126">无。</span><span class="sxs-lookup"><span data-stu-id="0fae5-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fae5-127">示例</span><span class="sxs-lookup"><span data-stu-id="0fae5-127">Example</span></span>  
 <span data-ttu-id="0fae5-128">这是一个 Banner 元素的示例。</span><span class="sxs-lookup"><span data-stu-id="0fae5-128">This is an example of a banner element.</span></span>  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fae5-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fae5-129">See Also</span></span>  
 [<span data-ttu-id="0fae5-130">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="0fae5-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
