---
title: 架构 (DTA) 的 Table 元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd444b1da99b22e0259dc1f50818c1763b7052ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691446"
---
# <a name="table-element-for-schema-dta"></a><span data-ttu-id="09cad-102">架构的表元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="09cad-102">Table Element for Schema (DTA)</span></span>
  <span data-ttu-id="09cad-103">指定用于优化的表。</span><span class="sxs-lookup"><span data-stu-id="09cad-103">Specifies the table for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cad-104">语法</span><span class="sxs-lookup"><span data-stu-id="09cad-104">Syntax</span></span>  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="09cad-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="09cad-105">Element Attributes</span></span>  
  
|<span data-ttu-id="09cad-106">Attribute</span><span class="sxs-lookup"><span data-stu-id="09cad-106">Attribute</span></span>|<span data-ttu-id="09cad-107">说明</span><span class="sxs-lookup"><span data-stu-id="09cad-107">Description</span></span>|  
|---------------|-----------------|  
|`NumberOfRows`|<span data-ttu-id="09cad-108">可选。</span><span class="sxs-lookup"><span data-stu-id="09cad-108">Optional.</span></span> <span data-ttu-id="09cad-109">允许您模拟不同大小的表的整数。</span><span class="sxs-lookup"><span data-stu-id="09cad-109">Integer that allows you to simulate tables of different sizes.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="09cad-110">元素特征</span><span class="sxs-lookup"><span data-stu-id="09cad-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="09cad-111">特征</span><span class="sxs-lookup"><span data-stu-id="09cad-111">Characteristic</span></span>|<span data-ttu-id="09cad-112">说明</span><span class="sxs-lookup"><span data-stu-id="09cad-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="09cad-113">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="09cad-113">**Data type and length**</span></span>|<span data-ttu-id="09cad-114">**字符串**，长度为 1 到 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="09cad-114">**string**, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="09cad-115">**默认值**</span><span class="sxs-lookup"><span data-stu-id="09cad-115">**Default value**</span></span>|<span data-ttu-id="09cad-116">无。</span><span class="sxs-lookup"><span data-stu-id="09cad-116">None.</span></span>|  
|<span data-ttu-id="09cad-117">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="09cad-117">**Occurrence**</span></span>|<span data-ttu-id="09cad-118">可选。</span><span class="sxs-lookup"><span data-stu-id="09cad-118">Optional.</span></span> <span data-ttu-id="09cad-119">列出数量与工作负荷相当的表。</span><span class="sxs-lookup"><span data-stu-id="09cad-119">List as many tables as appropriate for your workload.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="09cad-120">元素关系</span><span class="sxs-lookup"><span data-stu-id="09cad-120">Element Relationships</span></span>  
  
|<span data-ttu-id="09cad-121">关系</span><span class="sxs-lookup"><span data-stu-id="09cad-121">Relationship</span></span>|<span data-ttu-id="09cad-122">元素</span><span class="sxs-lookup"><span data-stu-id="09cad-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="09cad-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="09cad-123">**Parent element**</span></span>|[<span data-ttu-id="09cad-124">数据库的架构元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="09cad-124">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
|<span data-ttu-id="09cad-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="09cad-125">**Child elements**</span></span>|[<span data-ttu-id="09cad-126">表的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="09cad-126">Name Element for Table &#40;DTA&#41;</span></span>](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="09cad-127">备注</span><span class="sxs-lookup"><span data-stu-id="09cad-127">Remarks</span></span>  
 <span data-ttu-id="09cad-128">如果不指定 `Table` 元素，则数据库引擎优化顾问将假定指定数据库中的所有表都可优化。</span><span class="sxs-lookup"><span data-stu-id="09cad-128">If you do not specify a `Table` element, Database Engine Tuning Advisor will assume all tables on the specified database can be tuned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09cad-129">示例</span><span class="sxs-lookup"><span data-stu-id="09cad-129">Example</span></span>  
 <span data-ttu-id="09cad-130">有关使用示例，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="09cad-130">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09cad-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09cad-131">See Also</span></span>  
 [<span data-ttu-id="09cad-132">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="09cad-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
