---
title: 导出列转换编辑器 (列 "页) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580315"
---
# <a name="export-column-transformation-editor-columns-page"></a><span data-ttu-id="1874d-102">导出列转换编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="1874d-102">Export Column Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="1874d-103">可以使用 **“导出列转换编辑器”** 对话框的 **“列”** 页，指定数据流中要提取到文件的列。</span><span class="sxs-lookup"><span data-stu-id="1874d-103">Use the **Columns** page of the **Export Column Transformation Editor** dialog box to specify columns in the data flow to extract to files.</span></span> <span data-ttu-id="1874d-104">可以指定导出列转换是将数据追加到文件还是覆盖现有文件。</span><span class="sxs-lookup"><span data-stu-id="1874d-104">You can specify whether the Export Column transformation appends data to a file or overwrites an existing file.</span></span>  
  
 <span data-ttu-id="1874d-105">若要了解有关导出列转换的详细信息，请参阅 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="1874d-105">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1874d-106">选项</span><span class="sxs-lookup"><span data-stu-id="1874d-106">Options</span></span>  
 <span data-ttu-id="1874d-107">**提取列**</span><span class="sxs-lookup"><span data-stu-id="1874d-107">**Extract Column**</span></span>  
 <span data-ttu-id="1874d-108">从包含文本数据或图像数据的输入列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="1874d-108">Select from the list of input columns that contain text or image data.</span></span> <span data-ttu-id="1874d-109">所有行都应包含 **“提取列”** 和 **“文件路径列”** 的定义。</span><span class="sxs-lookup"><span data-stu-id="1874d-109">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="1874d-110">**“文件路径列”**</span><span class="sxs-lookup"><span data-stu-id="1874d-110">**File Path Column**</span></span>  
 <span data-ttu-id="1874d-111">从包含文件路径和文件名的输入列的列表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="1874d-111">Select from the list of input columns that contain file paths and file names.</span></span> <span data-ttu-id="1874d-112">所有行都应包含 **“提取列”** 和 **“文件路径列”** 的定义。</span><span class="sxs-lookup"><span data-stu-id="1874d-112">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="1874d-113">**允许追加**</span><span class="sxs-lookup"><span data-stu-id="1874d-113">**Allow Append**</span></span>  
 <span data-ttu-id="1874d-114">指定转换是否将数据追加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="1874d-114">Specify whether the transformation appends data to existing files.</span></span> <span data-ttu-id="1874d-115">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1874d-115">The default is `false`.</span></span>  
  
 <span data-ttu-id="1874d-116">**强制截断**</span><span class="sxs-lookup"><span data-stu-id="1874d-116">**Force Truncate**</span></span>  
 <span data-ttu-id="1874d-117">指定转换在写入数据之前是否删除现有文件的内容。</span><span class="sxs-lookup"><span data-stu-id="1874d-117">Specify whether the transformation deletes the contents of existing files before writing data.</span></span> <span data-ttu-id="1874d-118">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1874d-118">The default is `false`.</span></span>  
  
 <span data-ttu-id="1874d-119">**写入 BOM**</span><span class="sxs-lookup"><span data-stu-id="1874d-119">**Write BOM**</span></span>  
 <span data-ttu-id="1874d-120">指定是否将字节顺序标记 (BOM) 写入文件。</span><span class="sxs-lookup"><span data-stu-id="1874d-120">Specify whether to write a byte-order mark (BOM) to the file.</span></span> <span data-ttu-id="1874d-121">只有在数据具有 `DT_NTEXT` 或 DT_WSTR 数据类型，并且未将数据追加到现有数据文件时，才会写入 BOM。</span><span class="sxs-lookup"><span data-stu-id="1874d-121">A BOM is only written if the data has the `DT_NTEXT` or DT_WSTR data type and is not appended to an existing data file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1874d-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1874d-122">See Also</span></span>  
 <span data-ttu-id="1874d-123">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1874d-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="1874d-124">导出列转换编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="1874d-124">Export Column Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
