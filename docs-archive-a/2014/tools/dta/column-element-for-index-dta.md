---
title: DTA) 的索引 (列元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67853dc7d1193d3a0f80e56023846bc55a20bdaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682551"
---
# <a name="column-element-for-index-dta"></a><span data-ttu-id="a8d4e-102">索引的列元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a8d4e-102">Column Element for Index (DTA)</span></span>
  <span data-ttu-id="a8d4e-103">指定在其上为用户指定的配置创建索引的列。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-103">Specifies the columns on which the index is created for a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d4e-104">语法</span><span class="sxs-lookup"><span data-stu-id="a8d4e-104">Syntax</span></span>  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="a8d4e-105">元素属性</span><span class="sxs-lookup"><span data-stu-id="a8d4e-105">Element Attributes</span></span>  
  
|<span data-ttu-id="a8d4e-106">列属性</span><span class="sxs-lookup"><span data-stu-id="a8d4e-106">Column Attribute</span></span>|<span data-ttu-id="a8d4e-107">说明</span><span class="sxs-lookup"><span data-stu-id="a8d4e-107">Description</span></span>|  
|----------------------|-----------------|  
|`Type`|<span data-ttu-id="a8d4e-108">可选。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-108">Optional.</span></span> <span data-ttu-id="a8d4e-109">指定索引列类型。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-109">Specifies the index column type.</span></span> <span data-ttu-id="a8d4e-110">使用 string 数据类型将此属性指定为以下允许  值之一：</span><span class="sxs-lookup"><span data-stu-id="a8d4e-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="a8d4e-111">`KeyColumn`:</span><span class="sxs-lookup"><span data-stu-id="a8d4e-111">`KeyColumn`:</span></span><br />                  <span data-ttu-id="a8d4e-112">指定按索引键进行引用的列。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-112">Specifies that the column is referenced by an index key.</span></span> <span data-ttu-id="a8d4e-113">使用下面的语法设置此属性：</span><span class="sxs-lookup"><span data-stu-id="a8d4e-113">Use the following syntax to set this attribute:</span></span><br />`<Column Type="KeyColumn">`<br /><span data-ttu-id="a8d4e-114">有关键列的详细信息，请参阅 [群集索引和非群集索引介绍](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-114">For more information about key columns, see [Clustered and Nonclustered Indexes Described](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).</span></span><br /><br /> <span data-ttu-id="a8d4e-115">`IncludedColumn`：指定列是 (而不是键列) 的包含列。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-115">`IncludedColumn`: Specifies that the column is an included column (instead of a key column).</span></span> <span data-ttu-id="a8d4e-116">使用下面的语法设置此属性：</span><span class="sxs-lookup"><span data-stu-id="a8d4e-116">Use the following syntax to set this attribute:</span></span><br />`<Column Type="IncludedColumn">`<br /><span data-ttu-id="a8d4e-117">有关包含列的详细信息，请参阅 [创建带有包含列的索引](../../relational-databases/indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-117">For more information about included columns, see [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).</span></span>|  
|`SortOrder`|<span data-ttu-id="a8d4e-118">可选。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-118">Optional.</span></span> <span data-ttu-id="a8d4e-119">指定列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-119">Specifies the sorting order of the column.</span></span> <span data-ttu-id="a8d4e-120">请使用 **string** 数据类型按如下格式指定 **Ascending** 或 **Descending** 排序顺序：</span><span class="sxs-lookup"><span data-stu-id="a8d4e-120">Use a **string** data type to specify either an **"Ascending"** or **"Descending"** sorting order as follows:</span></span><br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="a8d4e-121">元素特征</span><span class="sxs-lookup"><span data-stu-id="a8d4e-121">Element Characteristics</span></span>  
  
|<span data-ttu-id="a8d4e-122">特征</span><span class="sxs-lookup"><span data-stu-id="a8d4e-122">Characteristic</span></span>|<span data-ttu-id="a8d4e-123">说明</span><span class="sxs-lookup"><span data-stu-id="a8d4e-123">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a8d4e-124">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="a8d4e-124">**Data type and length**</span></span>|<span data-ttu-id="a8d4e-125">无。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-125">None.</span></span>|  
|<span data-ttu-id="a8d4e-126">**默认值**</span><span class="sxs-lookup"><span data-stu-id="a8d4e-126">**Default value**</span></span>|<span data-ttu-id="a8d4e-127">无。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-127">None.</span></span>|  
|<span data-ttu-id="a8d4e-128">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="a8d4e-128">**Occurrence**</span></span>|<span data-ttu-id="a8d4e-129">最多可以为 `Index` 元素指定 1024 列。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-129">Can specify up to 1024 columns for the `Index` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a8d4e-130">元素关系</span><span class="sxs-lookup"><span data-stu-id="a8d4e-130">Element Relationships</span></span>  
  
|<span data-ttu-id="a8d4e-131">关系</span><span class="sxs-lookup"><span data-stu-id="a8d4e-131">Relationship</span></span>|<span data-ttu-id="a8d4e-132">元素</span><span class="sxs-lookup"><span data-stu-id="a8d4e-132">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a8d4e-133">**父元素**</span><span class="sxs-lookup"><span data-stu-id="a8d4e-133">**Parent element**</span></span>|[<span data-ttu-id="a8d4e-134">索引元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a8d4e-134">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)|  
|<span data-ttu-id="a8d4e-135">**子元素**</span><span class="sxs-lookup"><span data-stu-id="a8d4e-135">**Child elements**</span></span>|[<span data-ttu-id="a8d4e-136">列的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="a8d4e-136">Name Element for Column &#40;DTA&#41;</span></span>](name-element-for-column-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="a8d4e-137">示例</span><span class="sxs-lookup"><span data-stu-id="a8d4e-137">Example</span></span>  
 <span data-ttu-id="a8d4e-138">有关此元素的用法示例，请参阅[用户指定配置 (DTA) 的 XML 输入文件示例](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d4e-138">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d4e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8d4e-139">See Also</span></span>  
 [<span data-ttu-id="a8d4e-140">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="a8d4e-140">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
