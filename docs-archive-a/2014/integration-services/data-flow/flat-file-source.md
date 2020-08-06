---
title: 平面文件源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b1ca0f38c457256b3f2ed2ddb81bfbd0dc06b6c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694046"
---
# <a name="flat-file-source"></a><span data-ttu-id="5e6bf-102">平面文件源</span><span class="sxs-lookup"><span data-stu-id="5e6bf-102">Flat File Source</span></span>
  <span data-ttu-id="5e6bf-103">平面文件源从文本文件中读取数据。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-103">The Flat File source reads data from a text file.</span></span> <span data-ttu-id="5e6bf-104">文本文件可以为带分隔符格式、固定宽度格式或混合格式。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-104">The text file can be in delimited, fixed width, or mixed format.</span></span>  
  
-   <span data-ttu-id="5e6bf-105">带分隔符格式使用列和行分隔符定义列和行。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-105">Delimited format uses column and row delimiters to define columns and rows.</span></span>  
  
-   <span data-ttu-id="5e6bf-106">固定宽度格式使用宽度定义列和行。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-106">Fixed width format uses width to define columns and rows.</span></span> <span data-ttu-id="5e6bf-107">此格式还包含一个用于将字段填充到其最大宽度的字符。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-107">This format also includes a character for padding fields to their maximum width.</span></span>  
  
-   <span data-ttu-id="5e6bf-108">右边未对齐格式使用宽度定义除最后一列的所有列，最后一列由行分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-108">Ragged right format uses width to define all columns, except for the last column, which is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="5e6bf-109">可以按照下列方式配置平面文件源：</span><span class="sxs-lookup"><span data-stu-id="5e6bf-109">You can configure the Flat File source in the following ways:</span></span>  
  
-   <span data-ttu-id="5e6bf-110">将一个列添加到转换输出（此转换输出包含平面文件源从中提取数据的文本文件的名称）中。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-110">Add a column to the transformation output that contains the name of the text file from which the Flat File source extracts data.</span></span>  
  
-   <span data-ttu-id="5e6bf-111">指定平面文件源是否将列中长度为零的字符串解释为空值。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-111">Specify whether the Flat File source interprets zero-length strings in columns as null values.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e6bf-112">若要将长度为零的字符串解释为空值，平面文件源使用的平面文件连接管理器必须配置为使用带分隔符格式。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-112">The Flat File connection manager that the Flat File source uses must be configured to use a delimited format to interpret zero-length strings as nulls.</span></span> <span data-ttu-id="5e6bf-113">如果连接管理器使用固定宽度或右边未对齐格式，那么由空格组成的数据便无法解释为空值。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-113">If the connection manager uses the fixed width or ragged right formats, data that consists of spaces cannot be interpreted as null values.</span></span>  
  
 <span data-ttu-id="5e6bf-114">平面文件源输出中的输出列包含 FastParse 属性。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-114">The output columns in the output of the Flat File source include the FastParse property.</span></span> <span data-ttu-id="5e6bf-115">FastParse 指示该列是使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的速度较快但不区分区域设置的较快分析例程，还是使用区分区域设置的标准分析例程。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-115">FastParse indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="5e6bf-116">有关详细信息，请参阅 [Fast Parse](../fast-parse.md) 和 [Standard Parse](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-116">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span>  
  
 <span data-ttu-id="5e6bf-117">输出列还包含 UseBinaryFormat 属性。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-117">Output columns also include the UseBinaryFormat property.</span></span> <span data-ttu-id="5e6bf-118">使用该属性可在文件中实现对二进制数据（如带有组合型十进制格式的数据）的支持。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-118">You use this property to implement support for binary data, such as data with the packed decimal format, in files.</span></span> <span data-ttu-id="5e6bf-119">默认情况下，UseBinaryFormat 设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-119">By default UseBinaryFormat is set to `false`.</span></span> <span data-ttu-id="5e6bf-120">如果要使用二进制格式，请将 UseBinaryFormat 设置为， `true` 并将输出列上的数据类型设置为 `DT_BYTES` 。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-120">If you want to use a binary format, set UseBinaryFormat to `true` and the data type on the output column to `DT_BYTES`.</span></span> <span data-ttu-id="5e6bf-121">执行上述操作时，平面文件源将跳过数据转换并将数据原样传递到输出列。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-121">When you do this, the Flat File source skips the data conversion and passes the data to the output column as is.</span></span> <span data-ttu-id="5e6bf-122">然后，可以使用“派生列”或“数据转换”等转换将 `DT_BYTES` 数据转换为不同的数据类型，或者在脚本转换中编写自定义脚本来解释数据。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-122">You can then use a transformation such as the Derived Column or Data Conversion to cast the `DT_BYTES` data to a different data type, or you can write custom script in a Script transformation to interpret the data.</span></span> <span data-ttu-id="5e6bf-123">也可以编写自定义数据流组件来解释数据。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-123">You can also write a custom data flow component to interpret the data.</span></span> <span data-ttu-id="5e6bf-124">有关可强制转换为的数据类型的详细信息 `DT_BYTES` ，请参阅[CAST &#40;SSIS 表达式&#41;](../expressions/cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-124">For more information about which data types you can cast `DT_BYTES` to, see [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="5e6bf-125">此源使用平面文件连接管理器访问文本文件。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-125">This source uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="5e6bf-126">通过设置平面文件连接管理器的属性，可以提供关于文件和文件中每列的信息，并可以指定平面文件源应如何处理文本文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-126">By setting properties on the Flat File connection manager, you can provide information about the file and each column in it, and specify how the Flat File source should handle the data in the text file.</span></span> <span data-ttu-id="5e6bf-127">例如，可以指定文件中分隔列和行的字符，以及每列的数据类型和长度。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-127">For example, you can specify the characters that delimit columns and rows in the file, and the data type and the length of each column.</span></span> <span data-ttu-id="5e6bf-128">有关详细信息，请参阅 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-128">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="5e6bf-129">此源具有一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-129">This source has one output and one error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-source"></a><span data-ttu-id="5e6bf-130">平面文件源的配置</span><span class="sxs-lookup"><span data-stu-id="5e6bf-130">Configuration of the Flat File Source</span></span>  
 <span data-ttu-id="5e6bf-131">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5e6bf-132">有关可在 **“平面文件源编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="5e6bf-132">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5e6bf-133">平面文件源编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="5e6bf-133">Flat File Source Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="5e6bf-134">平面文件源编辑器（“列”页）</span><span class="sxs-lookup"><span data-stu-id="5e6bf-134">Flat File Source Editor &#40;Columns Page&#41;</span></span>](../flat-file-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="5e6bf-135">平面文件源编辑器（“错误输出”页）</span><span class="sxs-lookup"><span data-stu-id="5e6bf-135">Flat File Source Editor &#40;Error Output Page&#41;</span></span>](../flat-file-source-editor-error-output-page.md)  
  
 <span data-ttu-id="5e6bf-136">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-136">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="5e6bf-137">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="5e6bf-137">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5e6bf-138">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5e6bf-138">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="5e6bf-139">平面文件自定义属性</span><span class="sxs-lookup"><span data-stu-id="5e6bf-139">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="5e6bf-140">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="5e6bf-140">Related Tasks</span></span>  
 <span data-ttu-id="5e6bf-141">有关如何设置数据流组件属性的详细信息，请参阅 [设置数据流组件属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="5e6bf-141">For details about how to set properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6bf-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e6bf-142">See Also</span></span>  
 <span data-ttu-id="5e6bf-143">[平面文件目标](flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="5e6bf-143">[Flat File Destination](flat-file-destination.md) </span></span>  
 [<span data-ttu-id="5e6bf-144">数据流</span><span class="sxs-lookup"><span data-stu-id="5e6bf-144">Data Flow</span></span>](data-flow.md)  
  
  
