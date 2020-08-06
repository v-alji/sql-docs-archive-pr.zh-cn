---
title: " (DTA) 的 EventString 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 981cd0be06fd0972426fcb2fa67b0c4143cf9178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692051"
---
# <a name="eventstring-element-dta"></a><span data-ttu-id="af63a-102">EventString 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="af63a-102">EventString Element (DTA)</span></span>
  <span data-ttu-id="af63a-103">直接在 XML 输入文件中指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本工作负荷。</span><span class="sxs-lookup"><span data-stu-id="af63a-103">Specifies a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload directly in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af63a-104">语法</span><span class="sxs-lookup"><span data-stu-id="af63a-104">Syntax</span></span>  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="af63a-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="af63a-105">Element Attributes</span></span>  
  
|<span data-ttu-id="af63a-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="af63a-106">Attribute</span></span>|<span data-ttu-id="af63a-107">说明</span><span class="sxs-lookup"><span data-stu-id="af63a-107">Description</span></span>|  
|---------------|-----------------|  
|`Weight`|<span data-ttu-id="af63a-108">可选。</span><span class="sxs-lookup"><span data-stu-id="af63a-108">Optional.</span></span> <span data-ttu-id="af63a-109">为指定的事件指定查询加权系数（重要性系数）。</span><span class="sxs-lookup"><span data-stu-id="af63a-109">Specifies the query weight factor (a factor of importance) for the specified event.</span></span> <span data-ttu-id="af63a-110">使用 `float` 数据类型指定加权。</span><span class="sxs-lookup"><span data-stu-id="af63a-110">Use a `float` data type to specify the weight.</span></span> <span data-ttu-id="af63a-111">例如，`Weight`="100.01"。</span><span class="sxs-lookup"><span data-stu-id="af63a-111">For example, `Weight`="100.01".</span></span> <span data-ttu-id="af63a-112">可为 `Weight` 指定的最小值为“0”。</span><span class="sxs-lookup"><span data-stu-id="af63a-112">The minimum value you can specify for `Weight` is "0".</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="af63a-113">元素特征</span><span class="sxs-lookup"><span data-stu-id="af63a-113">Element Characteristics</span></span>  
  
|<span data-ttu-id="af63a-114">特征</span><span class="sxs-lookup"><span data-stu-id="af63a-114">Characteristic</span></span>|<span data-ttu-id="af63a-115">说明</span><span class="sxs-lookup"><span data-stu-id="af63a-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="af63a-116">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="af63a-116">**Data type and length**</span></span>|<span data-ttu-id="af63a-117">，无限长。</span><span class="sxs-lookup"><span data-stu-id="af63a-117">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="af63a-118">**默认值**</span><span class="sxs-lookup"><span data-stu-id="af63a-118">**Default value**</span></span>|<span data-ttu-id="af63a-119">无。</span><span class="sxs-lookup"><span data-stu-id="af63a-119">None.</span></span>|  
|<span data-ttu-id="af63a-120">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="af63a-120">**Occurrence**</span></span>|<span data-ttu-id="af63a-121">如果未指定其他类型的工作负荷，则必须使用一次。</span><span class="sxs-lookup"><span data-stu-id="af63a-121">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="af63a-122">必须为父元素 `EventString` 指定子元素 `File`、`Database` 或 `Workload`，但只能使用一种类型。</span><span class="sxs-lookup"><span data-stu-id="af63a-122">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="af63a-123">例如，如果指定了具有 `EventString` 元素的工作负荷，则不能在相同的 XML 输入文件中指定具有 `File` 元素的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="af63a-123">For example, if you specify a workload with the `EventString` element, then you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="af63a-124">元素关系</span><span class="sxs-lookup"><span data-stu-id="af63a-124">Element Relationships</span></span>  
  
|<span data-ttu-id="af63a-125">关系</span><span class="sxs-lookup"><span data-stu-id="af63a-125">Relationship</span></span>|<span data-ttu-id="af63a-126">元素</span><span class="sxs-lookup"><span data-stu-id="af63a-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="af63a-127">**父元素**</span><span class="sxs-lookup"><span data-stu-id="af63a-127">**Parent element**</span></span>|[<span data-ttu-id="af63a-128">工作负荷元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="af63a-128">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="af63a-129">**子元素**</span><span class="sxs-lookup"><span data-stu-id="af63a-129">**Child elements**</span></span>|<span data-ttu-id="af63a-130">无。</span><span class="sxs-lookup"><span data-stu-id="af63a-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af63a-131">示例</span><span class="sxs-lookup"><span data-stu-id="af63a-131">Example</span></span>  
 <span data-ttu-id="af63a-132">有关该元素的使用示例，请参阅[使用内联工作负荷的 XML 输入文件示例 (DTA)](xml-input-file-sample-with-inline-workload-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="af63a-132">For a usage example of this element, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af63a-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af63a-133">See Also</span></span>  
 [<span data-ttu-id="af63a-134">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="af63a-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
