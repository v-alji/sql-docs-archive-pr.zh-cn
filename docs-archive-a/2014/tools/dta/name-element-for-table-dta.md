---
title: ) DTA 的表 (名称元素 |Microsoft Docs
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
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fa8481cf8990fb63995abcb6300cd9a352c859a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588797"
---
# <a name="name-element-for-table-dta"></a><span data-ttu-id="ec7f3-102">表的名称元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ec7f3-102">Name Element for Table (DTA)</span></span>
  <span data-ttu-id="ec7f3-103">指定表名以进行优化。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-103">Specifies a table name for tuning.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec7f3-104">语法</span><span class="sxs-lookup"><span data-stu-id="ec7f3-104">Syntax</span></span>  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="ec7f3-105">元素特征</span><span class="sxs-lookup"><span data-stu-id="ec7f3-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="ec7f3-106">特征</span><span class="sxs-lookup"><span data-stu-id="ec7f3-106">Characteristic</span></span>|<span data-ttu-id="ec7f3-107">说明</span><span class="sxs-lookup"><span data-stu-id="ec7f3-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ec7f3-108">**数据类型和长度**</span><span class="sxs-lookup"><span data-stu-id="ec7f3-108">**Data type and length**</span></span>|<span data-ttu-id="ec7f3-109">`string`，介于 1 到 255 个字符之间。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="ec7f3-110">**默认值**</span><span class="sxs-lookup"><span data-stu-id="ec7f3-110">**Default value**</span></span>|<span data-ttu-id="ec7f3-111">无。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-111">None.</span></span>|  
|<span data-ttu-id="ec7f3-112">**出现次数**</span><span class="sxs-lookup"><span data-stu-id="ec7f3-112">**Occurrence**</span></span>|<span data-ttu-id="ec7f3-113">必需。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-113">Required.</span></span> <span data-ttu-id="ec7f3-114">每个 `Table` 元素一次。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-114">Once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ec7f3-115">元素关系</span><span class="sxs-lookup"><span data-stu-id="ec7f3-115">Element Relationships</span></span>  
  
|<span data-ttu-id="ec7f3-116">关系</span><span class="sxs-lookup"><span data-stu-id="ec7f3-116">Relationship</span></span>|<span data-ttu-id="ec7f3-117">元素</span><span class="sxs-lookup"><span data-stu-id="ec7f3-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ec7f3-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="ec7f3-118">**Parent element**</span></span>|[<span data-ttu-id="ec7f3-119">架构的表元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="ec7f3-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="ec7f3-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="ec7f3-120">**Child elements**</span></span>|<span data-ttu-id="ec7f3-121">无。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-121">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ec7f3-122">示例</span><span class="sxs-lookup"><span data-stu-id="ec7f3-122">Example</span></span>  
 <span data-ttu-id="ec7f3-123">有关使用示例，请参阅[服务器元素 (DTA)](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="ec7f3-123">For a usage example, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7f3-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec7f3-124">See Also</span></span>  
 [<span data-ttu-id="ec7f3-125">XML 输入文件引用（数据库引擎优化顾问）</span><span class="sxs-lookup"><span data-stu-id="ec7f3-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
