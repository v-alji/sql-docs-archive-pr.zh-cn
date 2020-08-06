---
title: 用于配置 (DTA) 的服务器元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88182cdad2e7313f0910a106ee37d727d840bfed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588789"
---
# <a name="server-element-for-configuration-dta"></a><span data-ttu-id="4a7b7-102">配置的服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4a7b7-102">Server Element for Configuration (DTA)</span></span>
  <span data-ttu-id="4a7b7-103">包含需要数据库引擎优化顾问评估其假设配置（由 `Configuration` 元素指定）的服务器的标识信息。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-103">Contains the identifying information for the server where you want Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7b7-104">语法</span><span class="sxs-lookup"><span data-stu-id="4a7b7-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="4a7b7-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="4a7b7-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="4a7b7-106">特征</span><span class="sxs-lookup"><span data-stu-id="4a7b7-106">Characteristic</span></span>|<span data-ttu-id="4a7b7-107">说明</span><span class="sxs-lookup"><span data-stu-id="4a7b7-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4a7b7-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="4a7b7-108">**Data type and length**</span></span>|<span data-ttu-id="4a7b7-109">无。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-109">None.</span></span>|  
|<span data-ttu-id="4a7b7-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="4a7b7-110">**Default value**</span></span>|<span data-ttu-id="4a7b7-111">无。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-111">None.</span></span>|  
|<span data-ttu-id="4a7b7-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="4a7b7-112">**Occurrence**</span></span>|<span data-ttu-id="4a7b7-113">每个 `Configuration` 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-113">Required once per `Configuration` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="4a7b7-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="4a7b7-114">Element Relationships</span></span>  
  
|<span data-ttu-id="4a7b7-115">关系</span><span class="sxs-lookup"><span data-stu-id="4a7b7-115">Relationship</span></span>|<span data-ttu-id="4a7b7-116">元素</span><span class="sxs-lookup"><span data-stu-id="4a7b7-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="4a7b7-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="4a7b7-117">**Parent element**</span></span>|[<span data-ttu-id="4a7b7-118">配置元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4a7b7-118">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
|<span data-ttu-id="4a7b7-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="4a7b7-119">**Child elements**</span></span>|[<span data-ttu-id="4a7b7-120">服务器的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4a7b7-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="4a7b7-121">配置的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4a7b7-121">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="4a7b7-122">备注</span><span class="sxs-lookup"><span data-stu-id="4a7b7-122">Remarks</span></span>  
 <span data-ttu-id="4a7b7-123">只能为元素指定一个 `Server` 元素 `Configuration` 。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-123">You can specify only one `Server` element for the `Configuration` element.</span></span> <span data-ttu-id="4a7b7-124">在 **数据库引擎优化顾问 XML 架构** 中，此元素的名称为 [ServerTypecomplexType](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-124">This element is of the **ServerTypecomplexType** name in the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span> <span data-ttu-id="4a7b7-125">请不要将此 `Server` 元素与 `DTAInput` 元素的子元素混淆。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-125">Do not confuse this `Server` element with the one that is the child of the `DTAInput` element.</span></span> <span data-ttu-id="4a7b7-126">有关详细信息，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-126">For more information, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a7b7-127">示例</span><span class="sxs-lookup"><span data-stu-id="4a7b7-127">Example</span></span>  
 <span data-ttu-id="4a7b7-128">有关用法示例，请参阅[具有用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="4a7b7-128">For a usage example, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7b7-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a7b7-129">See Also</span></span>  
 [<span data-ttu-id="4a7b7-130">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="4a7b7-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
