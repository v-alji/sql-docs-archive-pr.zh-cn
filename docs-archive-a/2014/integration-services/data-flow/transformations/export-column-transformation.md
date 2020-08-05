---
title: 导出列转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7ed2bef02d75b72870514e2333d2fa58720fb60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578974"
---
# <a name="export-column-transformation"></a><span data-ttu-id="c9d90-102">导出列转换</span><span class="sxs-lookup"><span data-stu-id="c9d90-102">Export Column Transformation</span></span>
  <span data-ttu-id="c9d90-103">导出列转换读取数据流中的数据，并将数据插入到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-103">The Export Column transformation reads data in a data flow and inserts the data into a file.</span></span> <span data-ttu-id="c9d90-104">例如，如果数据流包含产品信息（如每件产品的图片），则可使用导出列转换将图像保存到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-104">For example, if the data flow contains product information, such as a picture of each product, you could use the Export Column transformation to save the images to files.</span></span>  
  
## <a name="append-and-truncate-options"></a><span data-ttu-id="c9d90-105">追加和截断选项</span><span class="sxs-lookup"><span data-stu-id="c9d90-105">Append and Truncate Options</span></span>  
 <span data-ttu-id="c9d90-106">下表说明了追加和截断选项的设置如何影响结果。</span><span class="sxs-lookup"><span data-stu-id="c9d90-106">The following table describes how the settings for the append and truncate options affect results.</span></span>  
  
|<span data-ttu-id="c9d90-107">附加</span><span class="sxs-lookup"><span data-stu-id="c9d90-107">Append</span></span>|<span data-ttu-id="c9d90-108">Truncate</span><span class="sxs-lookup"><span data-stu-id="c9d90-108">Truncate</span></span>|<span data-ttu-id="c9d90-109">文件存在</span><span class="sxs-lookup"><span data-stu-id="c9d90-109">File exists</span></span>|<span data-ttu-id="c9d90-110">结果</span><span class="sxs-lookup"><span data-stu-id="c9d90-110">Results</span></span>|  
|------------|--------------|-----------------|-------------|  
|<span data-ttu-id="c9d90-111">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-111">False</span></span>|<span data-ttu-id="c9d90-112">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-112">False</span></span>|<span data-ttu-id="c9d90-113">否</span><span class="sxs-lookup"><span data-stu-id="c9d90-113">No</span></span>|<span data-ttu-id="c9d90-114">该转换将创建一个新文件并将数据写入到该文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-114">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="c9d90-115">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-115">True</span></span>|<span data-ttu-id="c9d90-116">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-116">False</span></span>|<span data-ttu-id="c9d90-117">否</span><span class="sxs-lookup"><span data-stu-id="c9d90-117">No</span></span>|<span data-ttu-id="c9d90-118">该转换将创建一个新文件并将数据写入到该文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-118">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="c9d90-119">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-119">False</span></span>|<span data-ttu-id="c9d90-120">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-120">True</span></span>|<span data-ttu-id="c9d90-121">否</span><span class="sxs-lookup"><span data-stu-id="c9d90-121">No</span></span>|<span data-ttu-id="c9d90-122">该转换将创建一个新文件并将数据写入到该文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-122">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="c9d90-123">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-123">True</span></span>|<span data-ttu-id="c9d90-124">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-124">True</span></span>|<span data-ttu-id="c9d90-125">否</span><span class="sxs-lookup"><span data-stu-id="c9d90-125">No</span></span>|<span data-ttu-id="c9d90-126">该转换的设计时验证失败。</span><span class="sxs-lookup"><span data-stu-id="c9d90-126">The transformation fails design time validation.</span></span> <span data-ttu-id="c9d90-127">将两个属性都设置为 `true` 是无效的。</span><span class="sxs-lookup"><span data-stu-id="c9d90-127">It is not valid to set both properties to `true`.</span></span>|  
|<span data-ttu-id="c9d90-128">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-128">False</span></span>|<span data-ttu-id="c9d90-129">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-129">False</span></span>|<span data-ttu-id="c9d90-130">是</span><span class="sxs-lookup"><span data-stu-id="c9d90-130">Yes</span></span>|<span data-ttu-id="c9d90-131">发生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="c9d90-131">A run-time error occurs.</span></span> <span data-ttu-id="c9d90-132">文件存在，但转换无法写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-132">The file exists, but the transformation cannot write to it.</span></span>|  
|<span data-ttu-id="c9d90-133">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-133">False</span></span>|<span data-ttu-id="c9d90-134">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-134">True</span></span>|<span data-ttu-id="c9d90-135">是</span><span class="sxs-lookup"><span data-stu-id="c9d90-135">Yes</span></span>|<span data-ttu-id="c9d90-136">转换将删除文件，然后重新创建文件并将数据写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-136">The transformation deletes and re-creates the file and writes the data to the file.</span></span>|  
|<span data-ttu-id="c9d90-137">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-137">True</span></span>|<span data-ttu-id="c9d90-138">False</span><span class="sxs-lookup"><span data-stu-id="c9d90-138">False</span></span>|<span data-ttu-id="c9d90-139">是</span><span class="sxs-lookup"><span data-stu-id="c9d90-139">Yes</span></span>|<span data-ttu-id="c9d90-140">转换将打开文件并将数据写入到文件末尾。</span><span class="sxs-lookup"><span data-stu-id="c9d90-140">The transformation opens the file and writes the data at the end of the file.</span></span>|  
|<span data-ttu-id="c9d90-141">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-141">True</span></span>|<span data-ttu-id="c9d90-142">True</span><span class="sxs-lookup"><span data-stu-id="c9d90-142">True</span></span>|<span data-ttu-id="c9d90-143">是</span><span class="sxs-lookup"><span data-stu-id="c9d90-143">Yes</span></span>|<span data-ttu-id="c9d90-144">该转换的设计时验证失败。</span><span class="sxs-lookup"><span data-stu-id="c9d90-144">The transformation fails design time validation.</span></span> <span data-ttu-id="c9d90-145">将两个属性都设置为 `true` 是无效的。</span><span class="sxs-lookup"><span data-stu-id="c9d90-145">It is not valid to set both properties to `true`.</span></span>|  
  
## <a name="configuration-of-the-export-column-transformation"></a><span data-ttu-id="c9d90-146">导出列转换的配置</span><span class="sxs-lookup"><span data-stu-id="c9d90-146">Configuration of the Export Column Transformation</span></span>  
 <span data-ttu-id="c9d90-147">可以按照下列方式配置导出列转换：</span><span class="sxs-lookup"><span data-stu-id="c9d90-147">You can configure the Export Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="c9d90-148">指定数据列和包含要向其写入数据的文件的路径的列。</span><span class="sxs-lookup"><span data-stu-id="c9d90-148">Specify the data columns and the columns that contain the path of files to which to write the data.</span></span>  
  
-   <span data-ttu-id="c9d90-149">指定数据插入操作是追加还是截断现有文件。</span><span class="sxs-lookup"><span data-stu-id="c9d90-149">Specify whether the data-insertion operation appends or truncates existing files.</span></span>  
  
-   <span data-ttu-id="c9d90-150">指定是否将字节顺序标记 (BOM) 写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-150">Specify whether a byte-order mark (BOM) is written to the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9d90-151">仅在不将数据追加到现有文件且数据具有 DT_NTEXT 数据类型时写入 BOM。</span><span class="sxs-lookup"><span data-stu-id="c9d90-151">A BOM is written only when the data is not appended to an existing file and the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="c9d90-152">此转换使用成对的输入列：一列包含文件名，另一列包含数据。</span><span class="sxs-lookup"><span data-stu-id="c9d90-152">The transformation uses pairs of input columns: One column contains a file name, and the other column contains data.</span></span> <span data-ttu-id="c9d90-153">数据集中的每一行都可指定一个不同的文件。</span><span class="sxs-lookup"><span data-stu-id="c9d90-153">Each row in the data set can specify a different file.</span></span> <span data-ttu-id="c9d90-154">转换在处理行时，数据将插入到指定的文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-154">As the transformation processes a row, the data is inserted into the specified file.</span></span> <span data-ttu-id="c9d90-155">在运行时，如果这些文件不存在，转换将创建这些文件，然后将数据写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="c9d90-155">At run time, the transformation creates the files, if they do not already exist, and then the transformation writes the data to the files.</span></span> <span data-ttu-id="c9d90-156">要写入的数据必须具有 DT_TEXT、DT_NTEXT 或 DT_IMAGE 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c9d90-156">The data to be written must have a DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="c9d90-157">有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d90-157">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="c9d90-158">此转换有一个输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="c9d90-158">This transformation has one input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="c9d90-159">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="c9d90-159">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c9d90-160">有关可以在“导出列转换编辑器”\*\*\*\* 对话框中设置的属性的详细信息，请参阅[导出列转换编辑器（“列”页）](../../export-column-transformation-editor-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d90-160">For more information about the properties that you can set in the **Export Column Transformation Editor** dialog box, see [Export Column Transformation Editor &#40;Columns Page&#41;](../../export-column-transformation-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="c9d90-161">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="c9d90-161">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="c9d90-162">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="c9d90-162">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c9d90-163">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c9d90-163">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="c9d90-164">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="c9d90-164">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="c9d90-165">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c9d90-165">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
