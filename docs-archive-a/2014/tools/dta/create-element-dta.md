---
title: " (DTA) 创建元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 407f16c3898e56cd393e36c39ed799b83e0092ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682539"
---
# <a name="create-element-dta"></a><span data-ttu-id="de65f-102">创建元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="de65f-102">Create Element (DTA)</span></span>
  <span data-ttu-id="de65f-103">包含有关用户指定配置中的索引、统计信息或堆结构的信息。</span><span class="sxs-lookup"><span data-stu-id="de65f-103">Contains information about the indexes, statistics, or heap structures in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de65f-104">语法</span><span class="sxs-lookup"><span data-stu-id="de65f-104">Syntax</span></span>  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="de65f-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="de65f-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="de65f-106">特征</span><span class="sxs-lookup"><span data-stu-id="de65f-106">Characteristic</span></span>|<span data-ttu-id="de65f-107">说明</span><span class="sxs-lookup"><span data-stu-id="de65f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="de65f-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="de65f-108">**Data type and length**</span></span>|<span data-ttu-id="de65f-109">无。</span><span class="sxs-lookup"><span data-stu-id="de65f-109">None.</span></span>|  
|<span data-ttu-id="de65f-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="de65f-110">**Default value**</span></span>|<span data-ttu-id="de65f-111">无。</span><span class="sxs-lookup"><span data-stu-id="de65f-111">None.</span></span>|  
|<span data-ttu-id="de65f-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="de65f-112">**Occurrence**</span></span>|<span data-ttu-id="de65f-113">对每个物理设计结构类型（索引、统计或堆结构）只需使用一次。</span><span class="sxs-lookup"><span data-stu-id="de65f-113">Required once for each physical design structure type (indexes, statistics, or heap structures).</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="de65f-114">元素关系</span><span class="sxs-lookup"><span data-stu-id="de65f-114">Element Relationships</span></span>  
  
|<span data-ttu-id="de65f-115">关系</span><span class="sxs-lookup"><span data-stu-id="de65f-115">Relationship</span></span>|<span data-ttu-id="de65f-116">元素</span><span class="sxs-lookup"><span data-stu-id="de65f-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="de65f-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="de65f-117">**Parent element**</span></span>|[<span data-ttu-id="de65f-118">建议元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="de65f-118">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
|<span data-ttu-id="de65f-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="de65f-119">**Child elements**</span></span>|[<span data-ttu-id="de65f-120">索引元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="de65f-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)<br /><br /> <span data-ttu-id="de65f-121">`Statistics`元素 (参阅[数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="de65f-121">`Statistics` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span><br /><br /> <span data-ttu-id="de65f-122">`Heap`元素 (参阅[数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="de65f-122">`Heap` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de65f-123">备注</span><span class="sxs-lookup"><span data-stu-id="de65f-123">Remarks</span></span>  
 <span data-ttu-id="de65f-124">在数据库引擎优化顾问 XML 架构中，此元素的名称为 **CreateTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="de65f-124">This element is of the **CreateTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="de65f-125">此元素用于为用户指定的配置创建索引、统计信息和堆结构。</span><span class="sxs-lookup"><span data-stu-id="de65f-125">It is used to create indexes, statistics, and heap structures for a user-specified configuration.</span></span> <span data-ttu-id="de65f-126">请勿将此 `Create` 元素和其他可用于创建视图 (`CreateViewType`) 或分区 (`CreatePType`) 的其他类型混淆。</span><span class="sxs-lookup"><span data-stu-id="de65f-126">Do not confuse this `Create` element with the other types that can be used to create views (`CreateViewType`) or partitioning (`CreatePType`).</span></span> <span data-ttu-id="de65f-127">有关这些其他元素类型的信息，请参阅[数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/) `Create` 。</span><span class="sxs-lookup"><span data-stu-id="de65f-127">Refer to the [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information about these other `Create` element types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de65f-128">示例</span><span class="sxs-lookup"><span data-stu-id="de65f-128">Example</span></span>  
 <span data-ttu-id="de65f-129">有关此元素的用法示例，请参阅[用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="de65f-129">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de65f-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de65f-130">See Also</span></span>  
 [<span data-ttu-id="de65f-131">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="de65f-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
