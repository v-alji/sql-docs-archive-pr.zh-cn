---
title: "\"数据流路径编辑器\" (\"常规\" 页) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.general.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71eca61b1454e2e8cb811bbe450f584191ae77b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688108"
---
# <a name="data-flow-path-editor-general-page"></a><span data-ttu-id="a540d-102">数据流路径编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="a540d-102">Data Flow Path Editor (General Page)</span></span>
  <span data-ttu-id="a540d-103">可以使用 **“数据流路径编辑器”** 对话框设置路径属性，查看列元数据以及管理附加到路径的数据查看器。</span><span class="sxs-lookup"><span data-stu-id="a540d-103">Use the **Data Flow Path Editor** dialog box to set path properties, view column metadata, and manage the data viewers attached to the path.</span></span>  
  
 <span data-ttu-id="a540d-104">使用 **“数据流路径编辑器”** 对话框的 **“常规”** 节点可以对路径进行命名和说明以及指定路径批注选项。</span><span class="sxs-lookup"><span data-stu-id="a540d-104">Use the **General** node of the **Data Flow Path Editor** dialog box to name and describe the path, and to specify the options for path annotation.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a540d-105">选项</span><span class="sxs-lookup"><span data-stu-id="a540d-105">Options</span></span>  
 <span data-ttu-id="a540d-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="a540d-106">**Name**</span></span>  
 <span data-ttu-id="a540d-107">为路径提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="a540d-107">Provide a unique name for the path.</span></span>  
  
 <span data-ttu-id="a540d-108">**ID**</span><span class="sxs-lookup"><span data-stu-id="a540d-108">**ID**</span></span>  
 <span data-ttu-id="a540d-109">路径的沿袭标识符。</span><span class="sxs-lookup"><span data-stu-id="a540d-109">The lineage identifier of the path.</span></span> <span data-ttu-id="a540d-110">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="a540d-110">This property is read-only.</span></span>  
  
 <span data-ttu-id="a540d-111">**IdentificationString**</span><span class="sxs-lookup"><span data-stu-id="a540d-111">**IdentificationString**</span></span>  
 <span data-ttu-id="a540d-112">用于标识路径的字符串。</span><span class="sxs-lookup"><span data-stu-id="a540d-112">The string that identifies the path.</span></span> <span data-ttu-id="a540d-113">从上面输入的名称自动生成。</span><span class="sxs-lookup"><span data-stu-id="a540d-113">Automatically generated from the name entered above.</span></span>  
  
 <span data-ttu-id="a540d-114">**说明**</span><span class="sxs-lookup"><span data-stu-id="a540d-114">**Description**</span></span>  
 <span data-ttu-id="a540d-115">描述该路径。</span><span class="sxs-lookup"><span data-stu-id="a540d-115">Describe the path.</span></span>  
  
 <span data-ttu-id="a540d-116">**PathAnnotation**</span><span class="sxs-lookup"><span data-stu-id="a540d-116">**PathAnnotation**</span></span>  
 <span data-ttu-id="a540d-117">指定要使用的批注类型。</span><span class="sxs-lookup"><span data-stu-id="a540d-117">Specify the type of annotation to use.</span></span> <span data-ttu-id="a540d-118">选择 **Never** 可以禁用批注；选择 **AsNeeded** 可以启用按需批注；选择 **SourceName** 可以使用 **SourceName** 选项的值自动进行批注；选择 **PathName** 可以使用 **Name** 属性的值自动进行批注。</span><span class="sxs-lookup"><span data-stu-id="a540d-118">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **SourceName** to automatically annotate using the value of the **SourceName** option, and **PathName** to automatically annotate using the value of the **Name** property.</span></span>  
  
 <span data-ttu-id="a540d-119">**DestinationName**</span><span class="sxs-lookup"><span data-stu-id="a540d-119">**DestinationName**</span></span>  
 <span data-ttu-id="a540d-120">显示作为路径结尾的输入。</span><span class="sxs-lookup"><span data-stu-id="a540d-120">Displays the input that is the end of the path.</span></span>  
  
 <span data-ttu-id="a540d-121">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="a540d-121">**SourceName**</span></span>  
 <span data-ttu-id="a540d-122">显示作为路径开头的输出。</span><span class="sxs-lookup"><span data-stu-id="a540d-122">Displays the output that is the start of the path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a540d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a540d-123">See Also</span></span>  
 <span data-ttu-id="a540d-124">[数据流路径编辑器 &#40;元数据页&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span><span class="sxs-lookup"><span data-stu-id="a540d-124">[Data Flow Path Editor &#40;Metadata Page&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span></span>  
 <span data-ttu-id="a540d-125">[数据流路径编辑器 &#40;数据查看器页&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="a540d-125">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="a540d-126">[数据流](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="a540d-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="a540d-127">在包中使用批注</span><span class="sxs-lookup"><span data-stu-id="a540d-127">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
