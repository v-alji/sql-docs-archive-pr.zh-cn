---
title: 数据库 (DTA) 的架构元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7653177878f3a832abd2d1ca266bc5feb17b9a29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578606"
---
# <a name="schema-element-for-database-dta"></a><span data-ttu-id="6ab6f-102">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="6ab6f-102">Schema Element for Database (DTA)</span></span>
  <span data-ttu-id="6ab6f-103">指定要优化的数据库的架构。</span><span class="sxs-lookup"><span data-stu-id="6ab6f-103">Specifies the schema of the database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab6f-104">语法</span><span class="sxs-lookup"><span data-stu-id="6ab6f-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="6ab6f-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="6ab6f-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="6ab6f-106">特征</span><span class="sxs-lookup"><span data-stu-id="6ab6f-106">Characteristic</span></span>|<span data-ttu-id="6ab6f-107">说明</span><span class="sxs-lookup"><span data-stu-id="6ab6f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6ab6f-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="6ab6f-108">**Data type and length**</span></span>|<span data-ttu-id="6ab6f-109">无。</span><span class="sxs-lookup"><span data-stu-id="6ab6f-109">None.</span></span>|  
|<span data-ttu-id="6ab6f-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="6ab6f-110">**Default value**</span></span>|<span data-ttu-id="6ab6f-111">无。</span><span class="sxs-lookup"><span data-stu-id="6ab6f-111">None.</span></span>|  
|<span data-ttu-id="6ab6f-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="6ab6f-112">**Occurrence**</span></span>|<span data-ttu-id="6ab6f-113">对于在 **Server** 元素下指定的 **Database** 元素，需要使用一次。</span><span class="sxs-lookup"><span data-stu-id="6ab6f-113">Required once for the **Database** element that is specified under the **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="6ab6f-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="6ab6f-114">Element Relationships</span></span>  
  
|<span data-ttu-id="6ab6f-115">关系</span><span class="sxs-lookup"><span data-stu-id="6ab6f-115">Relationship</span></span>|<span data-ttu-id="6ab6f-116">元素</span><span class="sxs-lookup"><span data-stu-id="6ab6f-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="6ab6f-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="6ab6f-117">**Parent element**</span></span>|[<span data-ttu-id="6ab6f-118">服务器的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="6ab6f-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="6ab6f-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="6ab6f-119">**Child elements**</span></span>|[<span data-ttu-id="6ab6f-120">架构的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="6ab6f-120">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)<br /><br /> [<span data-ttu-id="6ab6f-121">架构的表元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="6ab6f-121">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="6ab6f-122">示例</span><span class="sxs-lookup"><span data-stu-id="6ab6f-122">Example</span></span>  
 <span data-ttu-id="6ab6f-123">有关此元素的使用示例，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab6f-123">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab6f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ab6f-124">See Also</span></span>  
 [<span data-ttu-id="6ab6f-125">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="6ab6f-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
