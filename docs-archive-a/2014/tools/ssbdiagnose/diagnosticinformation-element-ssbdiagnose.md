---
title: DiagnosticInformation 元素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92d76a065c24ddc1fc8d85989ed3202308571951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579447"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a><span data-ttu-id="eebed-102">DiagnosticInformation 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="eebed-102">DiagnosticInformation Element (ssbdiagnose)</span></span>
  <span data-ttu-id="eebed-103">**DiagnosticInformation** 元素包含报告实用工具发现的诊断信息的所有元素。</span><span class="sxs-lookup"><span data-stu-id="eebed-103">The **DiagnosticInformation** element contains all elements that report the diagnostic information found by the utility.</span></span> <span data-ttu-id="eebed-104">**DiagnosticInformation** 是 **ssbdiagnostic** XML 输出文件的根元素。</span><span class="sxs-lookup"><span data-stu-id="eebed-104">**DiagnosticInformation** is the root element of a **ssbdiagnostic** XML output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eebed-105">语法</span><span class="sxs-lookup"><span data-stu-id="eebed-105">Syntax</span></span>  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="eebed-106">元素属性</span><span class="sxs-lookup"><span data-stu-id="eebed-106">Element Attributes</span></span>  
  
|<span data-ttu-id="eebed-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="eebed-107">Attribute</span></span>|<span data-ttu-id="eebed-108">说明</span><span class="sxs-lookup"><span data-stu-id="eebed-108">Description</span></span>|  
|---------------|-----------------|  
|`None`|<span data-ttu-id="eebed-109">空值</span><span class="sxs-lookup"><span data-stu-id="eebed-109">N/A</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="eebed-110">元素特征</span><span class="sxs-lookup"><span data-stu-id="eebed-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="eebed-111">特征</span><span class="sxs-lookup"><span data-stu-id="eebed-111">Characteristic</span></span>|<span data-ttu-id="eebed-112">说明</span><span class="sxs-lookup"><span data-stu-id="eebed-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="eebed-113">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="eebed-113">**Data type and length**</span></span>|<span data-ttu-id="eebed-114">无。</span><span class="sxs-lookup"><span data-stu-id="eebed-114">None.</span></span>|  
|<span data-ttu-id="eebed-115">**默认值**</span><span class="sxs-lookup"><span data-stu-id="eebed-115">**Default value**</span></span>|<span data-ttu-id="eebed-116">无。</span><span class="sxs-lookup"><span data-stu-id="eebed-116">None.</span></span>|  
|<span data-ttu-id="eebed-117">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="eebed-117">**Occurrence**</span></span>|<span data-ttu-id="eebed-118">每个 **ssbdiagnose** XML 输出文件一次。</span><span class="sxs-lookup"><span data-stu-id="eebed-118">Once per **ssbdiagnose** XML output file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="eebed-119">元素关系</span><span class="sxs-lookup"><span data-stu-id="eebed-119">Element Relationships</span></span>  
  
|<span data-ttu-id="eebed-120">关系</span><span class="sxs-lookup"><span data-stu-id="eebed-120">Relationship</span></span>|<span data-ttu-id="eebed-121">元素</span><span class="sxs-lookup"><span data-stu-id="eebed-121">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="eebed-122">**父元素**</span><span class="sxs-lookup"><span data-stu-id="eebed-122">**Parent element**</span></span>|<span data-ttu-id="eebed-123">无。</span><span class="sxs-lookup"><span data-stu-id="eebed-123">None.</span></span>|  
|<span data-ttu-id="eebed-124">**子元素**</span><span class="sxs-lookup"><span data-stu-id="eebed-124">**Child elements**</span></span>|[<span data-ttu-id="eebed-125">Banner 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="eebed-125">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)<br /><br /> [<span data-ttu-id="eebed-126">Issue 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="eebed-126">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a><span data-ttu-id="eebed-127">备注</span><span class="sxs-lookup"><span data-stu-id="eebed-127">Remarks</span></span>  
 <span data-ttu-id="eebed-128">有关 XML namespaces 的详细信息，请参阅 [MSDN Library 中的](https://go.microsoft.com/fwlink/?LinkId=7341) Namespaces in an XML Document [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eebed-128">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebed-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eebed-129">See Also</span></span>  
 [<span data-ttu-id="eebed-130">ssbdiagnose 实用工具 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="eebed-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
