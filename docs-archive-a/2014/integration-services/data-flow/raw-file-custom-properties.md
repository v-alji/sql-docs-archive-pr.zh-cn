---
title: 原始文件自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7614c03fbf44f37597e586549e306d01c28b523d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579662"
---
# <a name="raw-file-custom-properties"></a><span data-ttu-id="5f44e-102">原始文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="5f44e-102">Raw File Custom Properties</span></span>
  <span data-ttu-id="5f44e-103">**源自定义属性**</span><span class="sxs-lookup"><span data-stu-id="5f44e-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="5f44e-104">原始文件源具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-104">The Raw File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="5f44e-105">下表介绍原始文件源的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-105">The following table describes the custom properties of the Raw File source.</span></span> <span data-ttu-id="5f44e-106">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="5f44e-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="5f44e-107">属性名称</span><span class="sxs-lookup"><span data-stu-id="5f44e-107">Property name</span></span>|<span data-ttu-id="5f44e-108">数据类型</span><span class="sxs-lookup"><span data-stu-id="5f44e-108">Data Type</span></span>|<span data-ttu-id="5f44e-109">说明</span><span class="sxs-lookup"><span data-stu-id="5f44e-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="5f44e-110">AccessMode</span><span class="sxs-lookup"><span data-stu-id="5f44e-110">AccessMode</span></span>|<span data-ttu-id="5f44e-111">Integer（枚举）</span><span class="sxs-lookup"><span data-stu-id="5f44e-111">Integer (enumeration)</span></span>|<span data-ttu-id="5f44e-112">用来访问原始数据的模式。</span><span class="sxs-lookup"><span data-stu-id="5f44e-112">The mode used to access the raw data.</span></span> <span data-ttu-id="5f44e-113">可能的值为 `File name` (0) 和 `File name from variable` (1)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-113">The possible values are `File name` (0) and `File name from variable` (1).</span></span> <span data-ttu-id="5f44e-114">默认值为 `File name` (0)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-114">The default value is `File name` (0).</span></span>|  
|<span data-ttu-id="5f44e-115">FileName</span><span class="sxs-lookup"><span data-stu-id="5f44e-115">FileName</span></span>|<span data-ttu-id="5f44e-116">String</span><span class="sxs-lookup"><span data-stu-id="5f44e-116">String</span></span>|<span data-ttu-id="5f44e-117">源文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="5f44e-117">The path and file name of the source file.</span></span>|  
  
 <span data-ttu-id="5f44e-118">原始文件源的输出和输出列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-118">The output and the output columns of the Raw File source have no custom properties.</span></span>  
  
 <span data-ttu-id="5f44e-119">有关详细信息，请参阅 [Raw File Source](raw-file-source.md)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-119">For more information, see [Raw File Source](raw-file-source.md).</span></span>  
  
 <span data-ttu-id="5f44e-120">**目标自定义属性**</span><span class="sxs-lookup"><span data-stu-id="5f44e-120">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="5f44e-121">原始文件目标具有自定义属性和所有数据流组件通用的属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-121">The Raw File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="5f44e-122">下表介绍了原始文件目标的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-122">The following table describes the custom properties of the Raw File destination.</span></span> <span data-ttu-id="5f44e-123">所有属性均可读/写。</span><span class="sxs-lookup"><span data-stu-id="5f44e-123">All properties are read/write.</span></span>  
  
|<span data-ttu-id="5f44e-124">属性名称</span><span class="sxs-lookup"><span data-stu-id="5f44e-124">Property name</span></span>|<span data-ttu-id="5f44e-125">数据类型</span><span class="sxs-lookup"><span data-stu-id="5f44e-125">Data Type</span></span>|<span data-ttu-id="5f44e-126">说明</span><span class="sxs-lookup"><span data-stu-id="5f44e-126">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="5f44e-127">AccessMode</span><span class="sxs-lookup"><span data-stu-id="5f44e-127">AccessMode</span></span>|<span data-ttu-id="5f44e-128">Integer（枚举）</span><span class="sxs-lookup"><span data-stu-id="5f44e-128">Integer (enumeration)</span></span>|<span data-ttu-id="5f44e-129">一个值，指定 FileName 属性是包含文件名还是包含变量（包含文件名）名。</span><span class="sxs-lookup"><span data-stu-id="5f44e-129">A value that specifies whether the FileName property contains a file name, or the name of a variable that contains a file name.</span></span> <span data-ttu-id="5f44e-130">选项为 `File name` (0) 和 `File name from variable` (1)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-130">The options are `File name` (0) and `File name from variable` (1).</span></span>|  
|<span data-ttu-id="5f44e-131">FileName</span><span class="sxs-lookup"><span data-stu-id="5f44e-131">FileName</span></span>|<span data-ttu-id="5f44e-132">String</span><span class="sxs-lookup"><span data-stu-id="5f44e-132">String</span></span>|<span data-ttu-id="5f44e-133">原始文件目标要写入的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5f44e-133">The name of the file to which the Raw File destination writes.</span></span>|  
|<span data-ttu-id="5f44e-134">WriteOption</span><span class="sxs-lookup"><span data-stu-id="5f44e-134">WriteOption</span></span>|<span data-ttu-id="5f44e-135">Integer（枚举）</span><span class="sxs-lookup"><span data-stu-id="5f44e-135">Integer (enumeration)</span></span>|<span data-ttu-id="5f44e-136">一个指定原始文件目标是否删除具有相同名称的现有文件的值。</span><span class="sxs-lookup"><span data-stu-id="5f44e-136">A value that specifies whether the Raw File destination deletes an existing file that has the same name.</span></span> <span data-ttu-id="5f44e-137">选项为 `Create Always` (0)、`Create Once` (1)、`Truncate and Append` (3) 和 `Append` (2)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-137">The options are `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), and `Append` (2).</span></span> <span data-ttu-id="5f44e-138">此属性的默认值为 `Create Always` (0)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-138">The default value of this property is `Create Always` (0).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5f44e-139">追加操作要求追加数据的元数据与文件中已有数据的元数据匹配。</span><span class="sxs-lookup"><span data-stu-id="5f44e-139">An append operation requires the metadata of the appended data to match the metadata of the data already present in the file.</span></span>  
  
 <span data-ttu-id="5f44e-140">原始文件目标的输入和输入列没有自定义属性。</span><span class="sxs-lookup"><span data-stu-id="5f44e-140">The input and the input columns of the Raw File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="5f44e-141">有关详细信息，请参阅 [Raw File Destination](raw-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="5f44e-141">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f44e-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f44e-142">See Also</span></span>  
 [<span data-ttu-id="5f44e-143">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5f44e-143">Common Properties</span></span>](../common-properties.md)  
  
  
