---
title: XML 源自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e152b23b4f59ca46cb8272ca677dc1161b3efec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589770"
---
# <a name="xml-source-custom-properties"></a><span data-ttu-id="971f8-102">XML 源自定义属性</span><span class="sxs-lookup"><span data-stu-id="971f8-102">XML Source Custom Properties</span></span>
  <span data-ttu-id="971f8-103">XML 源具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="971f8-103">The XML source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="971f8-104">下表介绍 XML 源的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="971f8-104">The following table describes the custom properties of the XML source.</span></span> <span data-ttu-id="971f8-105">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="971f8-105">All properties are read/write.</span></span>  
  
|<span data-ttu-id="971f8-106">属性名称</span><span class="sxs-lookup"><span data-stu-id="971f8-106">Property name</span></span>|<span data-ttu-id="971f8-107">数据类型</span><span class="sxs-lookup"><span data-stu-id="971f8-107">Data Type</span></span>|<span data-ttu-id="971f8-108">说明</span><span class="sxs-lookup"><span data-stu-id="971f8-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="971f8-109">AccessMode</span><span class="sxs-lookup"><span data-stu-id="971f8-109">AccessMode</span></span>|<span data-ttu-id="971f8-110">Integer</span><span class="sxs-lookup"><span data-stu-id="971f8-110">Integer</span></span>|<span data-ttu-id="971f8-111">用来访问 XML 数据的模式。</span><span class="sxs-lookup"><span data-stu-id="971f8-111">The mode used to access the XML data.</span></span>|  
|<span data-ttu-id="971f8-112">UseInlineSchema</span><span class="sxs-lookup"><span data-stu-id="971f8-112">UseInlineSchema</span></span>|<span data-ttu-id="971f8-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="971f8-113">Boolean</span></span>|<span data-ttu-id="971f8-114">该值指示是否要在 XML 源中使用内联架构定义。</span><span class="sxs-lookup"><span data-stu-id="971f8-114">A value that indicates whether to use an inline schema definition within the XML source.</span></span> <span data-ttu-id="971f8-115">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="971f8-115">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="971f8-116">XMLData</span><span class="sxs-lookup"><span data-stu-id="971f8-116">XMLData</span></span>|<span data-ttu-id="971f8-117">String</span><span class="sxs-lookup"><span data-stu-id="971f8-117">String</span></span>|<span data-ttu-id="971f8-118">要从中检索 XML 数据的文件或变量。</span><span class="sxs-lookup"><span data-stu-id="971f8-118">The file or variables from which to retrieve the XML data.</span></span><br /><br /> <span data-ttu-id="971f8-119">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="971f8-119">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="971f8-120">XMLSchemaDefinition</span><span class="sxs-lookup"><span data-stu-id="971f8-120">XMLSchemaDefinition</span></span>|<span data-ttu-id="971f8-121">String</span><span class="sxs-lookup"><span data-stu-id="971f8-121">String</span></span>|<span data-ttu-id="971f8-122">架构定义文件 (.xsd) 的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="971f8-122">The path and file name of the schema definition file (.xsd).</span></span><br /><br /> <span data-ttu-id="971f8-123">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="971f8-123">The value of this property can be specified by using a property expression.</span></span>|  
  
 <span data-ttu-id="971f8-124">下表描述了 XML 源的输出的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="971f8-124">The following table describes the custom properties of the output of the XML source.</span></span> <span data-ttu-id="971f8-125">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="971f8-125">All properties are read/write.</span></span>  
  
|<span data-ttu-id="971f8-126">属性名称</span><span class="sxs-lookup"><span data-stu-id="971f8-126">Property name</span></span>|<span data-ttu-id="971f8-127">数据类型</span><span class="sxs-lookup"><span data-stu-id="971f8-127">Data Type</span></span>|<span data-ttu-id="971f8-128">说明</span><span class="sxs-lookup"><span data-stu-id="971f8-128">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="971f8-129">RowsetID</span><span class="sxs-lookup"><span data-stu-id="971f8-129">RowsetID</span></span>|<span data-ttu-id="971f8-130">String</span><span class="sxs-lookup"><span data-stu-id="971f8-130">String</span></span>|<span data-ttu-id="971f8-131">标识与输出关联的行集的值。</span><span class="sxs-lookup"><span data-stu-id="971f8-131">A value that identifies the rowset associated with the output.</span></span>|  
  
 <span data-ttu-id="971f8-132">XML 源的输出列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="971f8-132">The output columns of the XML source have no custom properties.</span></span>  
  
 <span data-ttu-id="971f8-133">有关详细信息，请参阅 [XML Source](xml-source.md)。</span><span class="sxs-lookup"><span data-stu-id="971f8-133">For more information, see [XML Source](xml-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971f8-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="971f8-134">See Also</span></span>  
 [<span data-ttu-id="971f8-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="971f8-135">Common Properties</span></span>](../common-properties.md)  
  
  
