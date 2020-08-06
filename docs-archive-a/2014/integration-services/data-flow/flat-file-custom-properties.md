---
title: 平面文件自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b906e9268bf3a74ffcf5661953397ad7a24b77a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694048"
---
# <a name="flat-file-custom-properties"></a><span data-ttu-id="bf0e3-102">平面文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="bf0e3-102">Flat File Custom Properties</span></span>
  <span data-ttu-id="bf0e3-103">**源自定义属性**</span><span class="sxs-lookup"><span data-stu-id="bf0e3-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="bf0e3-104">平面文件源具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-104">The Flat File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="bf0e3-105">下表介绍平面文件源的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-105">The following table describes the custom properties of the Flat File source.</span></span> <span data-ttu-id="bf0e3-106">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bf0e3-107">属性名称</span><span class="sxs-lookup"><span data-stu-id="bf0e3-107">Property name</span></span>|<span data-ttu-id="bf0e3-108">数据类型</span><span class="sxs-lookup"><span data-stu-id="bf0e3-108">Data Type</span></span>|<span data-ttu-id="bf0e3-109">说明</span><span class="sxs-lookup"><span data-stu-id="bf0e3-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bf0e3-110">FileNameColumnName</span><span class="sxs-lookup"><span data-stu-id="bf0e3-110">FileNameColumnName</span></span>|<span data-ttu-id="bf0e3-111">String</span><span class="sxs-lookup"><span data-stu-id="bf0e3-111">String</span></span>|<span data-ttu-id="bf0e3-112">包含文件名的输出列的名称。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-112">The name of an output column that contains the file name.</span></span> <span data-ttu-id="bf0e3-113">如果未指定名称，则不会生成包含文件名的输出列。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-113">If no name is specified, no output column containing the file name will be generated.</span></span><br /><br /> <span data-ttu-id="bf0e3-114">注意：此属性未在 **平面文件源编辑器**中提供，但可以使用 **高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-114">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="bf0e3-115">RetainNulls</span><span class="sxs-lookup"><span data-stu-id="bf0e3-115">RetainNulls</span></span>|<span data-ttu-id="bf0e3-116">Boolean</span><span class="sxs-lookup"><span data-stu-id="bf0e3-116">Boolean</span></span>|<span data-ttu-id="bf0e3-117">该值指定当数据转换管道引擎处理数据时是否将源文件中的 Null 值仍保留为 Null 值。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-117">A value that specifies whether to retain Null values from the source file as Null values when the data is processed by the Data Transformation Pipeline engine.</span></span> <span data-ttu-id="bf0e3-118">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-118">The default value of this property is `False`.</span></span>|  
  
 <span data-ttu-id="bf0e3-119">平面文件源的输出没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-119">The output of the Flat File source has no custom properties.</span></span>  
  
 <span data-ttu-id="bf0e3-120">下表描述了平面文件源的输出列的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-120">The following table describes the custom properties of the output columns of the Flat File source.</span></span> <span data-ttu-id="bf0e3-121">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-121">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bf0e3-122">属性名称</span><span class="sxs-lookup"><span data-stu-id="bf0e3-122">Property name</span></span>|<span data-ttu-id="bf0e3-123">数据类型</span><span class="sxs-lookup"><span data-stu-id="bf0e3-123">Data Type</span></span>|<span data-ttu-id="bf0e3-124">说明</span><span class="sxs-lookup"><span data-stu-id="bf0e3-124">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bf0e3-125">FastParse</span><span class="sxs-lookup"><span data-stu-id="bf0e3-125">FastParse</span></span>|<span data-ttu-id="bf0e3-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="bf0e3-126">Boolean</span></span>|<span data-ttu-id="bf0e3-127">一个值，该值指示列是使用 DTS 提供的不区分区域设置的较快分析例程，还是使用标准的区分区域设置的分析例程。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-127">A value that indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that DTS provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="bf0e3-128">有关详细信息，请参阅 [Fast Parse](../fast-parse.md) 和 [Standard Parse](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-128">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span> <span data-ttu-id="bf0e3-129">此属性的默认值为 `False`。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-129">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="bf0e3-130">注意：此属性未在 **平面文件源编辑器**中提供，但可以使用 **高级编辑器**进行设置。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-130">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
  
 <span data-ttu-id="bf0e3-131">有关详细信息，请参阅 [Flat File Source](flat-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-131">For more information, see [Flat File Source](flat-file-source.md).</span></span>  
  
 <span data-ttu-id="bf0e3-132">**目标自定义属性**</span><span class="sxs-lookup"><span data-stu-id="bf0e3-132">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="bf0e3-133">平面文件目标具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-133">The Flat File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="bf0e3-134">下表介绍平面文件目标的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-134">The following table describes the custom properties of the Flat File destination.</span></span> <span data-ttu-id="bf0e3-135">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-135">All properties are read/write.</span></span>  
  
|<span data-ttu-id="bf0e3-136">属性名称</span><span class="sxs-lookup"><span data-stu-id="bf0e3-136">Property name</span></span>|<span data-ttu-id="bf0e3-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="bf0e3-137">Data Type</span></span>|<span data-ttu-id="bf0e3-138">说明</span><span class="sxs-lookup"><span data-stu-id="bf0e3-138">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="bf0e3-139">标头</span><span class="sxs-lookup"><span data-stu-id="bf0e3-139">Header</span></span>|<span data-ttu-id="bf0e3-140">String</span><span class="sxs-lookup"><span data-stu-id="bf0e3-140">String</span></span>|<span data-ttu-id="bf0e3-141">写入任何数据之前插入到文件中的文本块。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-141">A block of text that is inserted in the file before any data is written.</span></span><br /><br /> <span data-ttu-id="bf0e3-142">此属性的值可以使用属性表达式来指定。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-142">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="bf0e3-143">Overwrite</span><span class="sxs-lookup"><span data-stu-id="bf0e3-143">Overwrite</span></span>|<span data-ttu-id="bf0e3-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="bf0e3-144">Boolean</span></span>|<span data-ttu-id="bf0e3-145">一个值，指定是覆盖还是追加到具有相同名称的现有目标文件。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-145">A value that specifies whether to overwrite or append to an existing destination file that has the same name.</span></span> <span data-ttu-id="bf0e3-146">此属性的默认值为 `True`。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-146">The default value of this property is `True`.</span></span>|  
  
 <span data-ttu-id="bf0e3-147">平面文件目标的输入和输入列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-147">The input and the input columns of the Flat File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="bf0e3-148">有关详细信息，请参阅 [Flat File Destination](flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="bf0e3-148">For more information, see [Flat File Destination](flat-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf0e3-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf0e3-149">See Also</span></span>  
 [<span data-ttu-id="bf0e3-150">Common Properties</span><span class="sxs-lookup"><span data-stu-id="bf0e3-150">Common Properties</span></span>](../common-properties.md)  
  
  
