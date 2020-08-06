---
title: Integration Services 路径 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c52bbd06974311a7fc94b3058309399d70df0034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689551"
---
# <a name="integration-services-paths"></a><span data-ttu-id="563ea-102">Integration Services 路径</span><span class="sxs-lookup"><span data-stu-id="563ea-102">Integration Services Paths</span></span>
  <span data-ttu-id="563ea-103">路径将一个数据流组件的输出连接到另一个组件的输入，以此连接数据流中的两个组件。</span><span class="sxs-lookup"><span data-stu-id="563ea-103">A path connects two components in a data flow by connecting the output of one data flow component to the input of another component.</span></span> <span data-ttu-id="563ea-104">路径具有源和目标。</span><span class="sxs-lookup"><span data-stu-id="563ea-104">A path has a source and a destination.</span></span> <span data-ttu-id="563ea-105">例如，如果路径连接一个 OLE DB 源和一个排序转换，那么 OLE DB 源就是路径的源，而排序转换就是路径的目标。</span><span class="sxs-lookup"><span data-stu-id="563ea-105">For example, if a path connects an OLE DB source and a Sort transformation, the OLE DB source is the source of the path, and the Sort transformation is the destination of the path.</span></span> <span data-ttu-id="563ea-106">源是路径开始处的组件，而目标是路径结束处的组件。</span><span class="sxs-lookup"><span data-stu-id="563ea-106">The source is the component where the path starts, and the destination is the component where the path ends.</span></span>  
  
 <span data-ttu-id="563ea-107">如果在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中运行包，您可以将数据查看器附加到一个路径，以此来查看数据流中的数据。</span><span class="sxs-lookup"><span data-stu-id="563ea-107">If you run a package in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can view the data in a data flow by attaching data viewers to a path.</span></span> <span data-ttu-id="563ea-108">数据查看器可配置为在网格中显示数据。</span><span class="sxs-lookup"><span data-stu-id="563ea-108">A data viewer can be configured to display data in a grid.</span></span> <span data-ttu-id="563ea-109">数据查看器是个很有用的调试工具。</span><span class="sxs-lookup"><span data-stu-id="563ea-109">A data viewer is a useful debugging tool.</span></span> <span data-ttu-id="563ea-110">有关详细信息，请参阅 [Debugging Data Flow](../troubleshooting/debugging-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="563ea-110">For more information, see [Debugging Data Flow](../troubleshooting/debugging-data-flow.md).</span></span>  
  
## <a name="configuration-of-the-path"></a><span data-ttu-id="563ea-111">路径的配置</span><span class="sxs-lookup"><span data-stu-id="563ea-111">Configuration of the Path</span></span>  
 <span data-ttu-id="563ea-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器提供 **“数据流路径编辑器”** 对话框，用于设置路径属性、查看通过该路径的数据列的元数据以及配置数据查看器。</span><span class="sxs-lookup"><span data-stu-id="563ea-112">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides the **Data Flow Path Editor** dialog box for setting path properties, viewing the metadata of the data columns that pass through the path, and configuring data viewers.</span></span>  
  
 <span data-ttu-id="563ea-113">可配置的路径属性有路径的名称、说明和批注。</span><span class="sxs-lookup"><span data-stu-id="563ea-113">The configurable path properties include the name, description, and annotation of the path.</span></span> <span data-ttu-id="563ea-114">还可以用编程的方式配置路径。</span><span class="sxs-lookup"><span data-stu-id="563ea-114">You can also configure paths programmatically.</span></span> <span data-ttu-id="563ea-115">有关详细信息，请参阅 [以编程方式连接数据流组件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="563ea-115">For more information, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
 <span data-ttu-id="563ea-116">路径批注显示路径源的名称或 **设计器中** “数据流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡的设计图面上的路径名称。</span><span class="sxs-lookup"><span data-stu-id="563ea-116">A path annotation displays the name of the path source or the path name on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="563ea-117">路径批注与可以添加到数据流、控制流和事件处理程序的批注类似，</span><span class="sxs-lookup"><span data-stu-id="563ea-117">Path annotations are similar to the annotations you can add to data flows, control flows, and event handlers.</span></span> <span data-ttu-id="563ea-118">唯一区别是路径批注附加到路径，而其他批注则显示在 **设计器的**“数据流” **、** “控制流” **和**“事件处理程序” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="563ea-118">The only difference is that a path annotation is attached to a path, whereas other annotations appear on the **Data Flow**, **Control Flow**, and **Event Handle**r tabs of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="563ea-119">元数据显示前一组件的输出中每一列的名称、数据类型、精度、小数位数、长度、代码页和源组件。</span><span class="sxs-lookup"><span data-stu-id="563ea-119">The metadata shows the name, data type, precision, scale, length, code page, and source component of each column in the output of the previous component.</span></span> <span data-ttu-id="563ea-120">源组件是创建此列的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="563ea-120">The source component is the data flow component that created the column.</span></span> <span data-ttu-id="563ea-121">这可能是数据流中的第一个组件，也可能不是。</span><span class="sxs-lookup"><span data-stu-id="563ea-121">This may or may not be the first component in the data flow.</span></span> <span data-ttu-id="563ea-122">例如，Union All 和排序转换创建自己的列，并且是其输出列的源。</span><span class="sxs-lookup"><span data-stu-id="563ea-122">For example, the Union All and Sort transformations create their own columns, and they are the sources of their output columns.</span></span> <span data-ttu-id="563ea-123">反之，复制列转换则可以不加更改地传递列，或者通过复制输入列来创建新列。</span><span class="sxs-lookup"><span data-stu-id="563ea-123">In contrast, a Copy Column transformation can pass through columns without changing them or can create new columns by copying input columns.</span></span> <span data-ttu-id="563ea-124">复制列转换仅是新列的源组件。</span><span class="sxs-lookup"><span data-stu-id="563ea-124">The Copy Column transformation is the source component only of the new columns.</span></span>  
  
 <span data-ttu-id="563ea-125">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="563ea-125">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="563ea-126">有关可在 **“数据流路径编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="563ea-126">For more information about the properties that you can set in the **Data Flow Path Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="563ea-127">数据流路径编辑器 &#40;常规 "页面&#41;</span><span class="sxs-lookup"><span data-stu-id="563ea-127">Data Flow Path Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="563ea-128">数据流路径编辑器 &#40;元数据页&#41;</span><span class="sxs-lookup"><span data-stu-id="563ea-128">Data Flow Path Editor &#40;Metadata Page&#41;</span></span>](../data-flow-path-editor-metadata-page.md)  
  
-   [<span data-ttu-id="563ea-129">数据流路径编辑器 &#40;数据查看器页&#41;</span><span class="sxs-lookup"><span data-stu-id="563ea-129">Data Flow Path Editor &#40;Data Viewers Page&#41;</span></span>](../data-flow-path-editor-data-viewers-page.md)  
  
 <span data-ttu-id="563ea-130">有关可以编程方式设置的属性的详细信息，请参阅 [Path Properties](../path-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="563ea-130">For more information about the properties that you can set programmatically, see [Path Properties](../path-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="563ea-131">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="563ea-131">Related Tasks</span></span>  
  
-   [<span data-ttu-id="563ea-132">在数据流路径编辑器中查看路径元数据</span><span class="sxs-lookup"><span data-stu-id="563ea-132">View Path Metadata in the Data Flow Path Editor</span></span>](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [<span data-ttu-id="563ea-133">连接数据流中的组件</span><span class="sxs-lookup"><span data-stu-id="563ea-133">Connect Components in a Data Flow</span></span>](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a><span data-ttu-id="563ea-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="563ea-134">See Also</span></span>  
 [<span data-ttu-id="563ea-135">数据流</span><span class="sxs-lookup"><span data-stu-id="563ea-135">Data Flow</span></span>](data-flow.md)  
  
  
