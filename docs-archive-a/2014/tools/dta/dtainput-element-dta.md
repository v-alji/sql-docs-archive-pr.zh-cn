---
title: " (DTA) 的 DTAInput 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7d2ff380a4ae1595e50aae472efc5fb4ac72efe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687399"
---
# <a name="dtainput-element-dta"></a><span data-ttu-id="e5646-102">DTAInput 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-102">DTAInput Element (DTA)</span></span>
  <span data-ttu-id="e5646-103">包含用于数据库引擎优化顾问的 XML 输入的定义。</span><span class="sxs-lookup"><span data-stu-id="e5646-103">Contains the definition of XML input for Database Engine Tuning Advisor.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5646-104">语法</span><span class="sxs-lookup"><span data-stu-id="e5646-104">Syntax</span></span>  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e5646-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="e5646-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e5646-106">特征</span><span class="sxs-lookup"><span data-stu-id="e5646-106">Characteristics</span></span>|<span data-ttu-id="e5646-107">说明</span><span class="sxs-lookup"><span data-stu-id="e5646-107">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="e5646-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="e5646-108">**Data type and length**</span></span>|<span data-ttu-id="e5646-109">无。</span><span class="sxs-lookup"><span data-stu-id="e5646-109">None.</span></span>|  
|<span data-ttu-id="e5646-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="e5646-110">**Default value**</span></span>|<span data-ttu-id="e5646-111">无。</span><span class="sxs-lookup"><span data-stu-id="e5646-111">None.</span></span>|  
|<span data-ttu-id="e5646-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="e5646-112">**Occurrence**</span></span>|<span data-ttu-id="e5646-113">可选。对于每个 **DTAXML** 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="e5646-113">Optional once per **DTAXML** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e5646-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="e5646-114">Element Relationships</span></span>  
  
|<span data-ttu-id="e5646-115">关系</span><span class="sxs-lookup"><span data-stu-id="e5646-115">Relationship</span></span>|<span data-ttu-id="e5646-116">元素</span><span class="sxs-lookup"><span data-stu-id="e5646-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e5646-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="e5646-117">**Parent element**</span></span>|[<span data-ttu-id="e5646-118">DTAXML 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-118">DTAXML Element &#40;DTA&#41;</span></span>](dtaxml-element-dta.md)|  
|<span data-ttu-id="e5646-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="e5646-119">**Child elements**</span></span>|[<span data-ttu-id="e5646-120">服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-120">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="e5646-121">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-121">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)<br /><br /> [<span data-ttu-id="e5646-122">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-122">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)<br /><br /> [<span data-ttu-id="e5646-123">配置元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e5646-123">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="e5646-124">备注</span><span class="sxs-lookup"><span data-stu-id="e5646-124">Remarks</span></span>  
 <span data-ttu-id="e5646-125">此元素是数据库引擎优化顾问输入架构层次结构的根元素。</span><span class="sxs-lookup"><span data-stu-id="e5646-125">This element is the root of the Database Engine Tuning Advisor input schema hierarchy.</span></span> <span data-ttu-id="e5646-126">数据库引擎优化顾问的输入可以是各种参数，这些参数指定了要优化其数据库的服务器、工作负荷、优化选项或用户指定配置。</span><span class="sxs-lookup"><span data-stu-id="e5646-126">Input to Database Engine Tuning Advisor can be arguments that specify the servers whose databases you want to tune, workloads, tuning options, or a user-specified configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5646-127">示例</span><span class="sxs-lookup"><span data-stu-id="e5646-127">Example</span></span>  
 <span data-ttu-id="e5646-128">有关 **DTAInput** 元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e5646-128">For a usage example of the **DTAInput** element, see [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5646-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5646-129">See Also</span></span>  
 [<span data-ttu-id="e5646-130">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="e5646-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
