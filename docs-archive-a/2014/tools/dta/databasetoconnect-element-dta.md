---
title: " (DTA) 的 DatabaseToConnect 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c21b36319e4007264677d499b84964c7cb5ea7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682534"
---
# <a name="databasetoconnect-element-dta"></a><span data-ttu-id="4868b-102">DatabaseToConnect 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4868b-102">DatabaseToConnect Element (DTA)</span></span>
  <span data-ttu-id="4868b-103">指定数据库引擎优化顾问在优化工作负荷时连接到的第一个数据库。</span><span class="sxs-lookup"><span data-stu-id="4868b-103">Specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4868b-104">语法</span><span class="sxs-lookup"><span data-stu-id="4868b-104">Syntax</span></span>  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="4868b-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="4868b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="4868b-106">特征</span><span class="sxs-lookup"><span data-stu-id="4868b-106">Characteristic</span></span>|<span data-ttu-id="4868b-107">说明</span><span class="sxs-lookup"><span data-stu-id="4868b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4868b-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="4868b-108">**Data type and length**</span></span>|<span data-ttu-id="4868b-109">`string`，长度没有限制。</span><span class="sxs-lookup"><span data-stu-id="4868b-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="4868b-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="4868b-110">**Default value**</span></span>|<span data-ttu-id="4868b-111">无。</span><span class="sxs-lookup"><span data-stu-id="4868b-111">None.</span></span>|  
|<span data-ttu-id="4868b-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="4868b-112">**Occurrence**</span></span>|<span data-ttu-id="4868b-113">可选。</span><span class="sxs-lookup"><span data-stu-id="4868b-113">Optional.</span></span> <span data-ttu-id="4868b-114">对于每个 `TuningOptions` 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="4868b-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="4868b-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="4868b-115">Element Relationships</span></span>  
  
|<span data-ttu-id="4868b-116">关系</span><span class="sxs-lookup"><span data-stu-id="4868b-116">Relationship</span></span>|<span data-ttu-id="4868b-117">元素</span><span class="sxs-lookup"><span data-stu-id="4868b-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="4868b-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="4868b-118">**Parent element**</span></span>|[<span data-ttu-id="4868b-119">TuningOptions 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4868b-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="4868b-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="4868b-120">**Child elements**</span></span>|<span data-ttu-id="4868b-121">无</span><span class="sxs-lookup"><span data-stu-id="4868b-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4868b-122">备注</span><span class="sxs-lookup"><span data-stu-id="4868b-122">Remarks</span></span>  
 <span data-ttu-id="4868b-123">使用 `DatabaseToConnect`，可以指定希望数据库引擎优化顾问在启动优化会话时连接到的第一个数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="4868b-123">Use `DatabaseToConnect` to specify the name of the first database to which you want Database Engine Tuning Advisor to connect when it starts the tuning session.</span></span> <span data-ttu-id="4868b-124">此元素只能指定一个数据库。</span><span class="sxs-lookup"><span data-stu-id="4868b-124">You can specify only one database with this element.</span></span> <span data-ttu-id="4868b-125">如果指定了多个数据库名称，数据库引擎优化顾问将返回错误。</span><span class="sxs-lookup"><span data-stu-id="4868b-125">If multiple database names are specified, Database Engine Tuning Advisor returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4868b-126">示例</span><span class="sxs-lookup"><span data-stu-id="4868b-126">Example</span></span>  
 <span data-ttu-id="4868b-127">有关使用示例，请参阅[使用内联工作负荷的 XML 输入文件示例 (DTA)](xml-input-file-sample-with-inline-workload-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="4868b-127">For a usage example, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4868b-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4868b-128">See Also</span></span>  
 [<span data-ttu-id="4868b-129">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="4868b-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
