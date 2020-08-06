---
title: 数据库 (DTA) 的名称元素 |Microsoft Docs
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
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: c692e31b9175bf05dcfb0504ea79e98cbb82f36b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682519"
---
# <a name="name-element-for-database-dta"></a><span data-ttu-id="508d0-102">数据库的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="508d0-102">Name Element for Database (DTA)</span></span>
  <span data-ttu-id="508d0-103">指定要优化的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="508d0-103">Specifies the name of a database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508d0-104">语法</span><span class="sxs-lookup"><span data-stu-id="508d0-104">Syntax</span></span>  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="508d0-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="508d0-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="508d0-106">特征</span><span class="sxs-lookup"><span data-stu-id="508d0-106">Characteristic</span></span>|<span data-ttu-id="508d0-107">说明</span><span class="sxs-lookup"><span data-stu-id="508d0-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="508d0-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="508d0-108">**Data type and length**</span></span>|<span data-ttu-id="508d0-109">`string`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="508d0-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="508d0-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="508d0-110">**Default value**</span></span>|<span data-ttu-id="508d0-111">无。</span><span class="sxs-lookup"><span data-stu-id="508d0-111">None.</span></span>|  
|<span data-ttu-id="508d0-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="508d0-112">**Occurrence**</span></span>|<span data-ttu-id="508d0-113">每个 `Database` 元素必须出现一次。</span><span class="sxs-lookup"><span data-stu-id="508d0-113">Required once per `Database` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="508d0-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="508d0-114">Element Relationships</span></span>  
  
|<span data-ttu-id="508d0-115">关系</span><span class="sxs-lookup"><span data-stu-id="508d0-115">Relationship</span></span>|<span data-ttu-id="508d0-116">元素</span><span class="sxs-lookup"><span data-stu-id="508d0-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="508d0-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="508d0-117">**Parent element**</span></span>|[<span data-ttu-id="508d0-118">服务器的数据库元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="508d0-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="508d0-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="508d0-119">**Child elements**</span></span>|<span data-ttu-id="508d0-120">无。</span><span class="sxs-lookup"><span data-stu-id="508d0-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="508d0-121">示例</span><span class="sxs-lookup"><span data-stu-id="508d0-121">Example</span></span>  
 <span data-ttu-id="508d0-122">有关此元素的使用示例，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="508d0-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508d0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="508d0-123">See Also</span></span>  
 [<span data-ttu-id="508d0-124">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="508d0-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
