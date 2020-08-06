---
title: 调试数据流 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- data viewers [Integration Services]
- data flow [Integration Services], debugging
- debugging [Integration Services], data flow
- counting rows
ms.assetid: 1c574f1b-54f7-4c05-8e42-8620e2c1df0f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed1d1b7ebb119d452ca3de92fdad47552d1cc36c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690709"
---
# <a name="debugging-data-flow"></a><span data-ttu-id="3ea9c-102">调试数据流</span><span class="sxs-lookup"><span data-stu-id="3ea9c-102">Debugging Data Flow</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3ea9c-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器包含可用于解决 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包中数据流问题的功能和工具。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] and the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer include features and tools that you can use to troubleshoot the data flows in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="3ea9c-104">设计器提供数据查看器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-104">Designer provides data viewers.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="3ea9c-105">设计器和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 转换提供行计数。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-105">Designer and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations provide row counts.</span></span>  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="3ea9c-106">设计器在运行时提供进度报告。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-106">Designer provides progress reporting at run time.</span></span>  
  
## <a name="data-viewers"></a><span data-ttu-id="3ea9c-107">数据查看器</span><span class="sxs-lookup"><span data-stu-id="3ea9c-107">Data Viewers</span></span>  
 <span data-ttu-id="3ea9c-108">数据查看器显示数据流中两个组件间的数据。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-108">Data viewers display data between two components in a data flow.</span></span> <span data-ttu-id="3ea9c-109">当数据从数据源提取出来并首次进入数据流时、转换对数据进行更新前后以及数据加载到其目标之前，数据查看器均可显示数据。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-109">Data viewers can display data when the data is extracted from a data source and first enters a data flow, before and after a transformation updates the data, and before the data is loaded into its destination.</span></span>  
  
 <span data-ttu-id="3ea9c-110">若要查看数据，请将数据查看器附加到连接两个数据流组件的路径。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-110">To view the data, you attach data viewers to the path that connects two data flow components.</span></span> <span data-ttu-id="3ea9c-111">在数据流组件间查看数据的能力，使得确定异常数据值、查看转换更改列值的方式以及发现转换失败的原因变得更加简单。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-111">The ability to view data between data flow components makes it easier to identify unexpected data values, view the way a transformation changes column values, and discover the reason that a transformation fails.</span></span> <span data-ttu-id="3ea9c-112">例如，您可能发现引用表中的查找失败，而为更正此问题，可以添加一个为空列提供默认数据的转换。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-112">For example, you may find that a lookup in a reference table fails, and to correct this you may want to add a transformation that provides default data for blank columns.</span></span>  
  
 <span data-ttu-id="3ea9c-113">数据查看器可以在网格中显示数据。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-113">A data viewer can display data in a grid.</span></span> <span data-ttu-id="3ea9c-114">若使用网格方式，则选择要显示的列。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-114">Using a grid, you select the columns to display.</span></span> <span data-ttu-id="3ea9c-115">选定列的值以表格的格式显示。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-115">The values for the selected columns display in a tabular format.</span></span>  
  
 <span data-ttu-id="3ea9c-116">您还可以在一个路径上包含多个数据查看器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-116">You can also include multiple data viewers on a path.</span></span> <span data-ttu-id="3ea9c-117">可以用不同的格式显示相同的数据（例如，为数据创建一个图表视图和一个网格视图），也可以为不同的数据列创建不同的数据查看器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-117">You can display the same data in different formats-for example, create a chart view and a grid view of the data-or create different data viewers for different columns of data.</span></span>  
  
 <span data-ttu-id="3ea9c-118">在将数据查看器添加到路径时， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器会将数据查看器图标添加到 **“数据流”** 选项卡的设计图面中，紧临该路径。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-118">When you add a data viewer to a path, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer adds a data viewer icon to the design surface of the **Data Flow** tab, next to the path.</span></span> <span data-ttu-id="3ea9c-119">可具有多个输出的转换（如有条件拆分转换）可以在每个路径上包含一个数据查看器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-119">Transformations that can have multiple outputs, such as the Conditional Split transformation, can include a data viewer on each path.</span></span>  
  
 <span data-ttu-id="3ea9c-120">在运行时， **“数据查看器”** 窗口会打开，并显示由数据查看器格式所指定的信息。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-120">At run time, a **Data Viewer** window opens and displays the information specified by the data viewer format.</span></span> <span data-ttu-id="3ea9c-121">例如，使用网格格式的数据查看器会显示选定列的数据、传递到数据流组件的输出行的行数以及所显示的行数。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-121">For example, a data viewer that uses the grid format shows data for the selected columns, the number of output rows passed to the data flow component, and the number of rows displayed.</span></span> <span data-ttu-id="3ea9c-122">信息按缓冲显示，根据数据流中的行的宽度，缓冲可以包含较多或较少的行。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-122">The information displays buffer by buffer and, depending on the width of the rows in the data flow, a buffer may contain more or fewer rows.</span></span>  
  
 <span data-ttu-id="3ea9c-123">在 **“数据查看器”** 对话框中，可以将数据复制到剪贴板、从表中清除所有数据、重新配置数据查看器、恢复数据流，以及分离或附加数据查看器。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-123">In the **Data Viewer** dialog box, you can copy the data to the Clipboard, clear all data from the table, reconfigure the data viewer, resume the flow of data, and detach or attach the data viewer.</span></span>  
  
#### <a name="to-add-a-data-viewer"></a><span data-ttu-id="3ea9c-124">添加数据查看器</span><span class="sxs-lookup"><span data-stu-id="3ea9c-124">To add a data viewer</span></span>  
  
-   [<span data-ttu-id="3ea9c-125">将数据查看器添加到数据流</span><span class="sxs-lookup"><span data-stu-id="3ea9c-125">Add a Data Viewer to a Data Flow</span></span>](../add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="row-counts"></a><span data-ttu-id="3ea9c-126">行计数</span><span class="sxs-lookup"><span data-stu-id="3ea9c-126">Row Counts</span></span>  
 <span data-ttu-id="3ea9c-127">通过路径已传递的行的数量在 **设计器中的** “数据流” [!INCLUDE[ssIS](../../includes/ssis-md.md)] 选项卡的设计图面上紧临该路径显示。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-127">The number of rows that have passed through a path is displayed on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer next to the path.</span></span> <span data-ttu-id="3ea9c-128">随着数据在路径中的移动，该数量会定期更新。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-128">The number is updated periodically while the data moves through the path.</span></span>  
  
 <span data-ttu-id="3ea9c-129">您还可以将行计数转换添加到数据流中，以捕获变量中的最终行计数。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-129">You can also add a Row Count transformation to the data flow to capture the final row count in a variable.</span></span> <span data-ttu-id="3ea9c-130">有关详细信息，请参阅 [Row Count Transformation](../data-flow/transformations/row-count-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-130">For more information, see [Row Count Transformation](../data-flow/transformations/row-count-transformation.md).</span></span>  
  
## <a name="progress-reporting"></a><span data-ttu-id="3ea9c-131">进度报告</span><span class="sxs-lookup"><span data-stu-id="3ea9c-131">Progress Reporting</span></span>  
 <span data-ttu-id="3ea9c-132">在运行包时， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器用指示状态的颜色显示每个数据流组件，以此在 **“数据流”** 选项卡设计图面上描绘进度。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-132">When you run a package, [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer depicts progress on the design surface of the **Data Flow** tab by displaying each data flow component in a color that indicates status.</span></span> <span data-ttu-id="3ea9c-133">当每个组件开始执行其工作时，颜色由无色变为黄色，而在成功完成后，则变为绿色。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-133">When each component starts to perform its work, it changes from no color to yellow, and when it finishes successfully, it changes to green.</span></span> <span data-ttu-id="3ea9c-134">红色指示组件失败。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-134">A red color indicates that the component failed.</span></span>  
  
 <span data-ttu-id="3ea9c-135">下表介绍颜色编码。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-135">The following table describes the color-coding.</span></span>  
  
|<span data-ttu-id="3ea9c-136">Color</span><span class="sxs-lookup"><span data-stu-id="3ea9c-136">Color</span></span>|<span data-ttu-id="3ea9c-137">说明</span><span class="sxs-lookup"><span data-stu-id="3ea9c-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ea9c-138">无色</span><span class="sxs-lookup"><span data-stu-id="3ea9c-138">No color</span></span>|<span data-ttu-id="3ea9c-139">等待被数据流引擎调用。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-139">Waiting to be called by the data flow engine.</span></span>|  
|<span data-ttu-id="3ea9c-140">Yellow</span><span class="sxs-lookup"><span data-stu-id="3ea9c-140">Yellow</span></span>|<span data-ttu-id="3ea9c-141">正在执行转换、提取数据或加载数据。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-141">Performing a transformation, extracting data, or loading data.</span></span>|  
|<span data-ttu-id="3ea9c-142">绿色</span><span class="sxs-lookup"><span data-stu-id="3ea9c-142">Green</span></span>|<span data-ttu-id="3ea9c-143">成功运行。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-143">Ran successfully.</span></span>|  
|<span data-ttu-id="3ea9c-144">红色</span><span class="sxs-lookup"><span data-stu-id="3ea9c-144">red</span></span>|<span data-ttu-id="3ea9c-145">运行中出现错误。</span><span class="sxs-lookup"><span data-stu-id="3ea9c-145">Ran with errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea9c-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea9c-146">See Also</span></span>  
 [<span data-ttu-id="3ea9c-147">包开发的疑难解答工具</span><span class="sxs-lookup"><span data-stu-id="3ea9c-147">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)  
  
  
