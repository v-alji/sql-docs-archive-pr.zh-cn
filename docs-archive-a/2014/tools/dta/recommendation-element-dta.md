---
title: DTA)  (建议元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4eb54a106d67f0217a2604b2d08754d0d2c0765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578607"
---
# <a name="recommendation-element-dta"></a><span data-ttu-id="e09f3-102">建议元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e09f3-102">Recommendation Element (DTA)</span></span>
  <span data-ttu-id="e09f3-103">包含有关属于用户指定配置的假设索引的信息。</span><span class="sxs-lookup"><span data-stu-id="e09f3-103">Contains information about the hypothetical indexes that are part of a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09f3-104">语法</span><span class="sxs-lookup"><span data-stu-id="e09f3-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="e09f3-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="e09f3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="e09f3-106">特征</span><span class="sxs-lookup"><span data-stu-id="e09f3-106">Characteristic</span></span>|<span data-ttu-id="e09f3-107">说明</span><span class="sxs-lookup"><span data-stu-id="e09f3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e09f3-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="e09f3-108">**Data type and length**</span></span>|<span data-ttu-id="e09f3-109">无。</span><span class="sxs-lookup"><span data-stu-id="e09f3-109">None.</span></span>|  
|<span data-ttu-id="e09f3-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="e09f3-110">**Default value**</span></span>|<span data-ttu-id="e09f3-111">无。</span><span class="sxs-lookup"><span data-stu-id="e09f3-111">None.</span></span>|  
|<span data-ttu-id="e09f3-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="e09f3-112">**Occurrence**</span></span>|<span data-ttu-id="e09f3-113">可选。</span><span class="sxs-lookup"><span data-stu-id="e09f3-113">Optional.</span></span> <span data-ttu-id="e09f3-114">对于每个 `Table` 元素可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="e09f3-114">Can use once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="e09f3-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="e09f3-115">Element Relationships</span></span>  
  
|<span data-ttu-id="e09f3-116">关系</span><span class="sxs-lookup"><span data-stu-id="e09f3-116">Relationship</span></span>|<span data-ttu-id="e09f3-117">元素</span><span class="sxs-lookup"><span data-stu-id="e09f3-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="e09f3-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="e09f3-118">**Parent element**</span></span>|[<span data-ttu-id="e09f3-119">架构的表元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e09f3-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="e09f3-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="e09f3-120">**Child elements**</span></span>|[<span data-ttu-id="e09f3-121">创建元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="e09f3-121">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)<br /><br /> <span data-ttu-id="e09f3-122">`Drop` 元素。</span><span class="sxs-lookup"><span data-stu-id="e09f3-122">`Drop` element.</span></span> <span data-ttu-id="e09f3-123">有关详细信息，请参阅 [数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="e09f3-123">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e09f3-124">备注</span><span class="sxs-lookup"><span data-stu-id="e09f3-124">Remarks</span></span>  
 <span data-ttu-id="e09f3-125">在数据库引擎优化顾问 XML 架构中，此元素的名称为 **RecommendationTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="e09f3-125">This element is of the **RecommendationTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="e09f3-126">该元素用于指定假设配置的索引。</span><span class="sxs-lookup"><span data-stu-id="e09f3-126">It is used to specify indexes for a hypothetical configuration.</span></span> <span data-ttu-id="e09f3-127">请不要将此 `Recommendation` 元素与可用于指定分区 (`RecommendationPType`) 或视图 (`RecommendationViewType`) 的其他类型混淆。</span><span class="sxs-lookup"><span data-stu-id="e09f3-127">Do not confuse this `Recommendation` element with the other types that can be used to specify partitioning (`RecommendationPType`) or views (`RecommendationViewType`).</span></span> <span data-ttu-id="e09f3-128">有关这些其他 `Recommendation` 元素类型的信息，请参阅[数据库引擎优化顾问 XML 架构](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="e09f3-128">For information about these other `Recommendation` element types, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09f3-129">示例</span><span class="sxs-lookup"><span data-stu-id="e09f3-129">Example</span></span>  
 <span data-ttu-id="e09f3-130">有关此元素的用法示例，请参阅[用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="e09f3-130">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09f3-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e09f3-131">See Also</span></span>  
 [<span data-ttu-id="e09f3-132">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="e09f3-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
