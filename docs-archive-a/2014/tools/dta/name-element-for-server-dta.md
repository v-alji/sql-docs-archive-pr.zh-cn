---
title: 服务器 (DTA) 的名称元素 |Microsoft Docs
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
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 202258c3c87f8a35d1ee30b19880f5e9423fa394
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588800"
---
# <a name="name-element-for-server-dta"></a><span data-ttu-id="ee76d-102">服务器的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ee76d-102">Name Element for Server (DTA)</span></span>
  <span data-ttu-id="ee76d-103">包含要优化的数据库所在服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="ee76d-103">Contains the name of the server where the databases you want to tune reside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee76d-104">语法</span><span class="sxs-lookup"><span data-stu-id="ee76d-104">Syntax</span></span>  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="ee76d-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="ee76d-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="ee76d-106">特征</span><span class="sxs-lookup"><span data-stu-id="ee76d-106">Characteristic</span></span>|<span data-ttu-id="ee76d-107">说明</span><span class="sxs-lookup"><span data-stu-id="ee76d-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ee76d-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="ee76d-108">**Data type and length**</span></span>|<span data-ttu-id="ee76d-109">`string`，介于 1 到 255 个字符之间。</span><span class="sxs-lookup"><span data-stu-id="ee76d-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="ee76d-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="ee76d-110">**Default value**</span></span>|<span data-ttu-id="ee76d-111">无。</span><span class="sxs-lookup"><span data-stu-id="ee76d-111">None.</span></span>|  
|<span data-ttu-id="ee76d-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="ee76d-112">**Occurrence**</span></span>|<span data-ttu-id="ee76d-113">每个 **服务器** 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="ee76d-113">Required once per **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ee76d-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="ee76d-114">Element Relationships</span></span>  
  
|<span data-ttu-id="ee76d-115">关系</span><span class="sxs-lookup"><span data-stu-id="ee76d-115">Relationship</span></span>|<span data-ttu-id="ee76d-116">元素</span><span class="sxs-lookup"><span data-stu-id="ee76d-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ee76d-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="ee76d-117">**Parent element**</span></span>|[<span data-ttu-id="ee76d-118">服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ee76d-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="ee76d-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="ee76d-119">**Child elements**</span></span>|<span data-ttu-id="ee76d-120">无。</span><span class="sxs-lookup"><span data-stu-id="ee76d-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee76d-121">示例</span><span class="sxs-lookup"><span data-stu-id="ee76d-121">Example</span></span>  
 <span data-ttu-id="ee76d-122">有关如何使用该 **Name** 元素的示例，请参阅 [服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="ee76d-122">For an example of how this **Name** element is used, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee76d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee76d-123">See Also</span></span>  
 [<span data-ttu-id="ee76d-124">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="ee76d-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
