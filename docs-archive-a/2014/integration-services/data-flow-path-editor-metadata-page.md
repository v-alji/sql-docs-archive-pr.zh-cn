---
title: 数据流路径编辑器 (元数据页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.metadata.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: b30bb9d7-ebc0-4b1a-8d0f-ee006b32e841
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c2c314707d8baa2fb0f853438f6486acf2a10a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688104"
---
# <a name="data-flow-path-editor-metadata-page"></a><span data-ttu-id="146c7-102">数据流路径编辑器（“元数据”页）</span><span class="sxs-lookup"><span data-stu-id="146c7-102">Data Flow Path Editor (Metadata Page)</span></span>
  <span data-ttu-id="146c7-103">可以使用 **“数据流路径编辑器”** 对话框的 **“元数据”** 页查看路径列的元数据。</span><span class="sxs-lookup"><span data-stu-id="146c7-103">Use the **Metadata** page of the **Data Flow Path Editor** dialog box to view the metadata of the path columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="146c7-104">选项</span><span class="sxs-lookup"><span data-stu-id="146c7-104">Options</span></span>  
 <span data-ttu-id="146c7-105">**路径元数据**</span><span class="sxs-lookup"><span data-stu-id="146c7-105">**Path metadata**</span></span>  
 <span data-ttu-id="146c7-106">列出列元数据。</span><span class="sxs-lookup"><span data-stu-id="146c7-106">Lists column metadata.</span></span> <span data-ttu-id="146c7-107">单击列标题可以对列数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="146c7-107">Click the column headings to sort column data.</span></span>  
  
 <span data-ttu-id="146c7-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="146c7-108">**Name**</span></span>  
 <span data-ttu-id="146c7-109">列出列的名称。</span><span class="sxs-lookup"><span data-stu-id="146c7-109">Lists the column name.</span></span>  
  
 <span data-ttu-id="146c7-110">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="146c7-110">**Data Type**</span></span>  
 <span data-ttu-id="146c7-111">列出列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="146c7-111">Lists the data type of the column.</span></span>  
  
 <span data-ttu-id="146c7-112">**精度**</span><span class="sxs-lookup"><span data-stu-id="146c7-112">**Precision**</span></span>  
 <span data-ttu-id="146c7-113">列出数值的位数。</span><span class="sxs-lookup"><span data-stu-id="146c7-113">Lists the number of digits in a numeric value.</span></span>  
  
 <span data-ttu-id="146c7-114">**缩放**</span><span class="sxs-lookup"><span data-stu-id="146c7-114">**Scale**</span></span>  
 <span data-ttu-id="146c7-115">列出数值的小数点后的位数。</span><span class="sxs-lookup"><span data-stu-id="146c7-115">List the number of digits to the right of the decimal point in a numeric value.</span></span>  
  
 <span data-ttu-id="146c7-116">**长度**</span><span class="sxs-lookup"><span data-stu-id="146c7-116">**Length**</span></span>  
 <span data-ttu-id="146c7-117">列出列的当前长度。</span><span class="sxs-lookup"><span data-stu-id="146c7-117">Lists the current length of the column.</span></span>  
  
 <span data-ttu-id="146c7-118">**代码页**</span><span class="sxs-lookup"><span data-stu-id="146c7-118">**Code Page**</span></span>  
 <span data-ttu-id="146c7-119">列出列的代码页。</span><span class="sxs-lookup"><span data-stu-id="146c7-119">Lists the code page of the column.</span></span> <span data-ttu-id="146c7-120">如果值为 **0** ，则表示该列不使用代码页。</span><span class="sxs-lookup"><span data-stu-id="146c7-120">The value **0** indicates that the column does not use a code page.</span></span> <span data-ttu-id="146c7-121">当数据为 Unicode 字符，或者数据为数值、日期或时间数据类型时，则会发生上述情况。</span><span class="sxs-lookup"><span data-stu-id="146c7-121">This occurs when data is in Unicode, or has a numeric, date, or time data type.</span></span>  
  
 <span data-ttu-id="146c7-122">**排序键位置**</span><span class="sxs-lookup"><span data-stu-id="146c7-122">**Sort Key Position**</span></span>  
 <span data-ttu-id="146c7-123">列出列的排序键位置。</span><span class="sxs-lookup"><span data-stu-id="146c7-123">Lists the sort key position of the column.</span></span> <span data-ttu-id="146c7-124">如何值为 **0** ，则表示未对该列进行排序。</span><span class="sxs-lookup"><span data-stu-id="146c7-124">The value **0** indicates the column is not sorted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="146c7-125">减号 (-) 前缀表示该列按降序排序。</span><span class="sxs-lookup"><span data-stu-id="146c7-125">A minus (-) prefix indicates the column is sorted in descending order.</span></span>  
  
 <span data-ttu-id="146c7-126">**比较标志**</span><span class="sxs-lookup"><span data-stu-id="146c7-126">**Comparison Flags**</span></span>  
 <span data-ttu-id="146c7-127">列出应用于该列的比较标志。</span><span class="sxs-lookup"><span data-stu-id="146c7-127">Lists the comparison flags that apply to the column.</span></span>  
  
 <span data-ttu-id="146c7-128">**源组件**</span><span class="sxs-lookup"><span data-stu-id="146c7-128">**Source Component**</span></span>  
 <span data-ttu-id="146c7-129">列出作为列的源的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="146c7-129">Lists the data flow component that is the source of the column.</span></span>  
  
 <span data-ttu-id="146c7-130">**复制到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="146c7-130">**Copy to Clipboard**</span></span>  
 <span data-ttu-id="146c7-131">将列的元数据复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="146c7-131">Copy the column metadata to the clipboard.</span></span> <span data-ttu-id="146c7-132">默认情况下，按当前显示的顺序复制所有元数据行。</span><span class="sxs-lookup"><span data-stu-id="146c7-132">By default, all metadata rows are copied as sorted in the order currently displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="146c7-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="146c7-133">See Also</span></span>  
 <span data-ttu-id="146c7-134">[数据流路径编辑器 &#40;常规 "页面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="146c7-134">[Data Flow Path Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="146c7-135">[数据流路径编辑器 &#40;数据查看器页&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="146c7-135">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="146c7-136">[数据流](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="146c7-136">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="146c7-137">在包中使用批注</span><span class="sxs-lookup"><span data-stu-id="146c7-137">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
