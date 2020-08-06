---
title: Server (DTA) 的数据库元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a48d255898eff6bd780f8edf2c8d2da7229b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682536"
---
# <a name="database-element-for-server-dta"></a><span data-ttu-id="e0f6b-102">服务器的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e0f6b-102">Database Element for Server (DTA)</span></span>
  <span data-ttu-id="e0f6b-103">指定特定服务器上要优化的数据库。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-103">Specifies the database you want to tune on a specific server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f6b-104">语法</span><span class="sxs-lookup"><span data-stu-id="e0f6b-104">Syntax</span></span>  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e0f6b-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="e0f6b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e0f6b-106">特征</span><span class="sxs-lookup"><span data-stu-id="e0f6b-106">Characteristic</span></span>|<span data-ttu-id="e0f6b-107">说明</span><span class="sxs-lookup"><span data-stu-id="e0f6b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e0f6b-108">数据类型和长度</span><span class="sxs-lookup"><span data-stu-id="e0f6b-108">Data type and length</span></span>|<span data-ttu-id="e0f6b-109">无。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-109">None.</span></span>|  
|<span data-ttu-id="e0f6b-110">默认值</span><span class="sxs-lookup"><span data-stu-id="e0f6b-110">Default value</span></span>|<span data-ttu-id="e0f6b-111">无。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-111">None.</span></span>|  
|<span data-ttu-id="e0f6b-112">出现次数</span><span class="sxs-lookup"><span data-stu-id="e0f6b-112">Occurrence</span></span>|<span data-ttu-id="e0f6b-113">对于每个 `Server` 元素需要使用一次或多次。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-113">Required one or more times per `Server` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e0f6b-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="e0f6b-114">Element Relationships</span></span>  
  
|<span data-ttu-id="e0f6b-115">关系</span><span class="sxs-lookup"><span data-stu-id="e0f6b-115">Relationship</span></span>|<span data-ttu-id="e0f6b-116">元素</span><span class="sxs-lookup"><span data-stu-id="e0f6b-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e0f6b-117">父元素</span><span class="sxs-lookup"><span data-stu-id="e0f6b-117">Parent element</span></span>|[<span data-ttu-id="e0f6b-118">服务器元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e0f6b-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="e0f6b-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e0f6b-119">Child elements</span></span>|[<span data-ttu-id="e0f6b-120">数据库的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e0f6b-120">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="e0f6b-121">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e0f6b-121">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="e0f6b-122">备注</span><span class="sxs-lookup"><span data-stu-id="e0f6b-122">Remarks</span></span>  
 <span data-ttu-id="e0f6b-123">在数据库引擎优化顾问 XML 架构中，此元素的名称为 **DatabaseDetailsTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-123">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="e0f6b-124">请不要将此 `Database` 元素与根级父元素为 `Configuration` 元素的元素相混淆。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-124">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="e0f6b-125">有关详细信息，请参阅[用于配置的数据库元素 (DTA)](database-element-for-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-125">For more information, see [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f6b-126">示例</span><span class="sxs-lookup"><span data-stu-id="e0f6b-126">Example</span></span>  
 <span data-ttu-id="e0f6b-127">有关元素的用法示例 `Database` ，请参阅[Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f6b-127">For a usage example of the `Database` element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f6b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0f6b-128">See Also</span></span>  
 [<span data-ttu-id="e0f6b-129">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="e0f6b-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
