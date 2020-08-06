---
title: 导入列转换 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4330438614cce7892e74dc9a1dcbb6680b72972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589799"
---
# <a name="import-column-transformation"></a><span data-ttu-id="0b8a1-102">导入列转换</span><span class="sxs-lookup"><span data-stu-id="0b8a1-102">Import Column Transformation</span></span>
  <span data-ttu-id="0b8a1-103">导入列转换从文件中读取数据并将数据添加到数据流中的列中。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-103">The Import Column transformation reads data from files and adds the data to columns in a data flow.</span></span> <span data-ttu-id="0b8a1-104">通过此转换，包可将存储于各个单独文件中的文本和图像添加到数据流中。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-104">Using this transformation, a package can add text and images stored in separate files to a data flow.</span></span> <span data-ttu-id="0b8a1-105">例如，如果某个数据流将数据加载到存储产品信息的表中，则它可包含导入列转换以便从文件中导入每个产品的客户评论并将评论添加到数据流中。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-105">For example, a data flow that loads data into a table that stores product information can include the Import Column transformation to import customer reviews of each product from files and add the reviews to the data flow.</span></span>  
  
 <span data-ttu-id="0b8a1-106">可以按照下列方式配置导入列转换：</span><span class="sxs-lookup"><span data-stu-id="0b8a1-106">You can configure the Import Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="0b8a1-107">指定转换要向其添加数据的列。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-107">Specify the columns to which the transformation adds data.</span></span>  
  
-   <span data-ttu-id="0b8a1-108">指定转换是否需要字节顺序标记 (BOM)。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-108">Specify whether the transformation expects a byte-order mark (BOM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0b8a1-109">仅当数据为 DT_NTEXT 数据类型时才需要 BOM。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-109">A BOM is only expected if the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="0b8a1-110">转换输入中的列包含存储数据的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-110">A column in the transformation input contains the names of files that hold the data.</span></span> <span data-ttu-id="0b8a1-111">数据集中的每一行均可指定一个不同的文件。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-111">Each row in the dataset can specify a different file.</span></span> <span data-ttu-id="0b8a1-112">导入列转换处理行时，将读取文件名，打开文件系统中的相应文件，并将文件内容加载到输出列中。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-112">When the Import Column transformation processes a row, it reads the file name, opens the corresponding file in the file system, and loads the file content into an output column.</span></span> <span data-ttu-id="0b8a1-113">输出列的数据类型必须是 DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-113">The data type of the output column must be DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="0b8a1-114">有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-114">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="0b8a1-115">此转换有一个输入、一个输出和一个错误输出。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-115">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="configuration-of-the-import-column-transformation"></a><span data-ttu-id="0b8a1-116">导入列转换的配置</span><span class="sxs-lookup"><span data-stu-id="0b8a1-116">Configuration of the Import Column Transformation</span></span>  
 <span data-ttu-id="0b8a1-117">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-117">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0b8a1-118">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="0b8a1-119">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="0b8a1-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0b8a1-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="0b8a1-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="0b8a1-121">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="0b8a1-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="0b8a1-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="0b8a1-122">Related Tasks</span></span>  
 <span data-ttu-id="0b8a1-123">有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0b8a1-123">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8a1-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b8a1-124">See Also</span></span>  
 <span data-ttu-id="0b8a1-125">[导出列转换](export-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="0b8a1-125">[Export Column Transformation](export-column-transformation.md) </span></span>  
 <span data-ttu-id="0b8a1-126">[数据流](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="0b8a1-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="0b8a1-127">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="0b8a1-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
