---
title: 执行计划和缓冲区分配 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], buffer allocations
- custom data flow components [Integration Services], execution plans
- buffer allocations [Integration Services]
- data flow components [Integration Services], buffer allocations
- data flow components [Integration Services], execution plans
- execution plans [Integration Services]
ms.assetid: 679d9ff0-641e-47c3-abb8-d1a7dcb279dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03b8bb22988ccf77f8920252ac2d600478c92f3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688068"
---
# <a name="execution-plan-and-buffer-allocation"></a><span data-ttu-id="62a5b-102">执行计划和缓冲区分配</span><span class="sxs-lookup"><span data-stu-id="62a5b-102">Execution Plan and Buffer Allocation</span></span>
  <span data-ttu-id="62a5b-103">在执行之前，数据流任务会先检查其组件，并为每一个组件序列生成一个执行计划。</span><span class="sxs-lookup"><span data-stu-id="62a5b-103">Before execution, the data flow task examines its components and generates an execution plan for each sequence of components.</span></span> <span data-ttu-id="62a5b-104">本节提供有关执行计划、如何查看执行计划以及如何基于执行计划分配输入和输出缓冲区的详细信息。</span><span class="sxs-lookup"><span data-stu-id="62a5b-104">This section provides details about the execution plan, how to view the plan, and how input and output buffers are allocated based on the execution plan.</span></span>  
  
## <a name="understanding-the-execution-plan"></a><span data-ttu-id="62a5b-105">了解执行计划</span><span class="sxs-lookup"><span data-stu-id="62a5b-105">Understanding the Execution Plan</span></span>  
 <span data-ttu-id="62a5b-106">执行计划包含源线程和工作线程，每个线程均包含指定源线程的输出工作列表或指定工作线程的输入和输出工作列表的工作列表。</span><span class="sxs-lookup"><span data-stu-id="62a5b-106">An execution plan contains source threads and work threads, and each thread contains work lists that specify output work lists for source threads or input and output work lists for work threads.</span></span> <span data-ttu-id="62a5b-107">执行计划中的源线程表示数据流中的源组件，并在执行计划中由 SourceThread\*\*n 标识，其中 n 为从零开始的源线程编号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62a5b-107">The source threads in an execution plan represent the source components in the data flow and are identified in the execution plan by *SourceThread\*\*n*, where *n* is the zero-based number of the source thread.</span></span>  
  
 <span data-ttu-id="62a5b-108">每个源线程都会创建一个缓冲区，设置一个侦听器，并对源组件调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="62a5b-108">Each source thread creates a buffer, sets a listener, and calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method on the source component.</span></span> <span data-ttu-id="62a5b-109">执行从源线程开始，数据也从这里开始出现，因为源组件开始向数据流任务为其提供的输出缓冲区中添加行。</span><span class="sxs-lookup"><span data-stu-id="62a5b-109">This is where execution starts and data originates, as the source component starts adding rows to the output buffers that are provided to it by the data flow task.</span></span> <span data-ttu-id="62a5b-110">源线程开始运行之后，会在工作线程之间平衡分配工作量。</span><span class="sxs-lookup"><span data-stu-id="62a5b-110">After the source threads are running, the balance of work is distributed among work threads.</span></span>  
  
 <span data-ttu-id="62a5b-111">工作线程可能同时包含输入工作列表和输出工作列表，并在执行计划中被标识为 WorkThread\*\*n，其中 n 为从零开始的工作线程编号\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="62a5b-111">A work thread may contain both input and output work lists and is identified in the execution plan as *WorkThread\*\*n*, where *n* is the zero-based number of the work thread.</span></span> <span data-ttu-id="62a5b-112">当图形中包含具有异步输出的组件时，这些线程将包含输出工作列表。</span><span class="sxs-lookup"><span data-stu-id="62a5b-112">These threads contain output work lists when the graph contains a component with asynchronous outputs.</span></span>  
  
 <span data-ttu-id="62a5b-113">下面的示例执行计划表示了一个数据流，该数据流包含一个源组件、一个具有异步输出的转换和一个目标组件，它们依次连接。</span><span class="sxs-lookup"><span data-stu-id="62a5b-113">The following sample execution plan represents a data flow that contains a source component connected to a transformation with an asynchronous output connected to a destination component.</span></span> <span data-ttu-id="62a5b-114">在此示例中，WorkThread0 包含一个输出工作列表，因为转换组件有一个异步输出。</span><span class="sxs-lookup"><span data-stu-id="62a5b-114">In this example, WorkThread0 contains an output work list because the transformation component has an asynchronous output.</span></span>  
  
```  
SourceThread0   
    Influences: 72 158   
    Output Work List   
        CreatePrimeBuffer of type 1 for output id 10   
        SetBufferListener: "WorkThread0" for input ID 73   
        CallPrimeOutput on component "OLE DB Source" (1)   
    End Output Work List   
    This thread drives 0 distributors   
End SourceThread0   
WorkThread0   
    Influences: 72 158   
    Input Work list, input ID 73   
        CallProcessInput on input ID 73 on component "Sort" (72) for view type 2   
    End Input Work list for input 73   
    Output Work List   
        CreatePrimeBuffer of type 3 for output id 74   
        SetBufferListener: "WorkThread1" for input ID 171with internal handoff   
        CallPrimeOutput on component "Sort" (72)   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread0   
WorkThread1   
    Influences: 158   
    Input Work list, input ID 171  
        CallProcessInput on input ID 171 on component "OLE DB Destination" (158) for view type 4  
    End Input Work list for input 171   
    Output Work List   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="62a5b-115">每次执行包时，都会生成一个执行计划，可通过向包中添加日志提供程序、启用日志记录并选择 PipelineExecutionPlan 事件来捕获该执行计划  。</span><span class="sxs-lookup"><span data-stu-id="62a5b-115">The execution plan is generated every time a package is executed, and can be captured by adding a log provider to the package, enabling logging, and selecting the **PipelineExecutionPlan** event.</span></span>  
  
## <a name="understanding-buffer-allocation"></a><span data-ttu-id="62a5b-116">了解缓冲区分配</span><span class="sxs-lookup"><span data-stu-id="62a5b-116">Understanding Buffer Allocation</span></span>  
 <span data-ttu-id="62a5b-117">工作流任务会基于执行计划创建缓冲区，这些缓冲区包含在数据流组件的输出中定义的列。</span><span class="sxs-lookup"><span data-stu-id="62a5b-117">Based on the execution plan, the data flow task creates buffers that contain the columns defined in the outputs of the data flow components.</span></span> <span data-ttu-id="62a5b-118">在数据流通过这一系列组件的过程中，会重用缓冲区，直至遇到具有异步输出的组件为止。</span><span class="sxs-lookup"><span data-stu-id="62a5b-118">The buffer is reused as the data flows through the sequence of components, until a component with asynchronous outputs is encountered.</span></span> <span data-ttu-id="62a5b-119">此时将创建新的缓冲区，其中包含异步输出的输出列和下游组件的输出列。</span><span class="sxs-lookup"><span data-stu-id="62a5b-119">Then, a new buffer is created, which contains the output columns of the asynchronous output and the output columns of downstream components.</span></span>  
  
 <span data-ttu-id="62a5b-120">在执行期间，组件可以访问当前源线程或工作线程中的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="62a5b-120">During execution, components have access to the buffer in the current source or work thread.</span></span> <span data-ttu-id="62a5b-121">缓冲区可以是 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法提供的输入缓冲区，也可以是 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法提供的输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="62a5b-121">The buffer is either an input buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, or an output buffer, provided by the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="62a5b-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 属性还将每个缓冲区标识为输入缓冲区或输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="62a5b-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> also identifies each buffer as an input or output buffer.</span></span>  
  
 <span data-ttu-id="62a5b-123">具有异步输出的转换组件从 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法接收现有输入缓冲区，并从 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法接收新的输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="62a5b-123">Transformation components with asynchronous outputs receive the existing input buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, and receive the new output buffer from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="62a5b-124">具有异步输出的转换组件是唯一一种可同时接收输入缓冲区和输出缓冲区的数据流组件。</span><span class="sxs-lookup"><span data-stu-id="62a5b-124">A transformation component with asynchronous outputs is the only type of data flow component that receives both an input and an output buffer.</span></span>  
  
 <span data-ttu-id="62a5b-125">由于提供给组件的缓冲区所包含的列数可能大于组件的输入或输出列集合中的列数，因此，组件开发人员可通过调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 方法并指定列的 `LineageID`，在缓冲区中查找列。</span><span class="sxs-lookup"><span data-stu-id="62a5b-125">Because the buffer provided to a component is likely to contain more columns than the component has in its input or output column collections, component developers can call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method to locate a column in the buffer by specifying its `LineageID`.</span></span>  
  
<span data-ttu-id="62a5b-126">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="62a5b-126">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="62a5b-127">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="62a5b-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="62a5b-128">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="62a5b-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="62a5b-129">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="62a5b-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
