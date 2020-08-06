---
title: 数据流组件的运行时方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df0afe4c29044541c5a57aa3a466283ab4fe4fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690759"
---
# <a name="run-time-methods-of-a-data-flow-component"></a><span data-ttu-id="0df27-102">数据流组件的运行时方法</span><span class="sxs-lookup"><span data-stu-id="0df27-102">Run-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="0df27-103">在运行时，数据流任务将检查一系列组件、准备执行计划以及管理执行工作计划的工作线程池。</span><span class="sxs-lookup"><span data-stu-id="0df27-103">At run time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="0df27-104">任务先从源加载数据行，再通过转换处理这些行，然后将它们保存到目标。</span><span class="sxs-lookup"><span data-stu-id="0df27-104">The task loads rows of data from sources, processes them through transformations, then saves them to destinations.</span></span>  
  
## <a name="sequence-of-method-execution"></a><span data-ttu-id="0df27-105">方法执行顺序</span><span class="sxs-lookup"><span data-stu-id="0df27-105">Sequence of Method Execution</span></span>  
 <span data-ttu-id="0df27-106">在数据流组件的执行期间，将调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基类中的方法的子集。</span><span class="sxs-lookup"><span data-stu-id="0df27-106">During the execution of a data flow component, a subset of the methods in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is called.</span></span> <span data-ttu-id="0df27-107">除 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法外，所调用的方法及其调用顺序始终相同。</span><span class="sxs-lookup"><span data-stu-id="0df27-107">The methods, and the sequence in which they are called, are always the same, with the exception of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="0df27-108">这两个方法是基于组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 对象的存在性及其配置调用的。</span><span class="sxs-lookup"><span data-stu-id="0df27-108">These two methods are called based on the existence and configuration of a component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects.</span></span>  
  
 <span data-ttu-id="0df27-109">下面的列表以这些方法在组件执行期间的调用顺序来显示它们。</span><span class="sxs-lookup"><span data-stu-id="0df27-109">The following list shows the methods in the order in which they are called during component execution.</span></span> <span data-ttu-id="0df27-110">请注意，如果调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>，则始终在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 之前调用。</span><span class="sxs-lookup"><span data-stu-id="0df27-110">Note that <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, when called, is always called before <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a><span data-ttu-id="0df27-111">PrimeOutput 方法</span><span class="sxs-lookup"><span data-stu-id="0df27-111">PrimeOutput Method</span></span>  
 <span data-ttu-id="0df27-112">当组件具有至少一个通过 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> 对象附加到下游组件的输出，且该输出的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 属性为零时，即调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-112">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called when a component has at least one output, attached to a downstream component through an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, and the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property of the output is zero.</span></span> <span data-ttu-id="0df27-113">针对源组件和具有异步输出的转换调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-113">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called for source components and for transformations with asynchronous outputs.</span></span> <span data-ttu-id="0df27-114">与下面介绍的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法不同，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法仅针对每个需要它的组件调用一次。</span><span class="sxs-lookup"><span data-stu-id="0df27-114">Unlike the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method described below, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is only called once for each component that requires it.</span></span>  
  
### <a name="processinput-method"></a><span data-ttu-id="0df27-115">ProcessInput 方法</span><span class="sxs-lookup"><span data-stu-id="0df27-115">ProcessInput Method</span></span>  
 <span data-ttu-id="0df27-116">针对至少具有一个由 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 对象附加到上游组件的输入的组件调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for components that have at least one input attached to an upstream component by an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object.</span></span> <span data-ttu-id="0df27-117">针对目标组件和具有同步输出的转换调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-117">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for destination components and for transformations with synchronous outputs.</span></span> <span data-ttu-id="0df27-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 可重复调用，直到没有要处理的来自上游组件的行为止。</span><span class="sxs-lookup"><span data-stu-id="0df27-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> is called repeatedly until there are no more rows to process from upstream components.</span></span>  
  
## <a name="working-with-inputs-and-outputs"></a><span data-ttu-id="0df27-119">使用输入和输出</span><span class="sxs-lookup"><span data-stu-id="0df27-119">Working with Inputs and Outputs</span></span>  
 <span data-ttu-id="0df27-120">在运行时，数据流组件执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="0df27-120">At run time, data flow components perform the following tasks:</span></span>  
  
-   <span data-ttu-id="0df27-121">源组件添加行。</span><span class="sxs-lookup"><span data-stu-id="0df27-121">Source components add rows.</span></span>  
  
-   <span data-ttu-id="0df27-122">具有同步输出的转换组件接收源组件提供的行。</span><span class="sxs-lookup"><span data-stu-id="0df27-122">Transformation components with synchronous outputs receive rows provided by source components.</span></span>  
  
-   <span data-ttu-id="0df27-123">具有异步输出的转换组件接收行和添加行。</span><span class="sxs-lookup"><span data-stu-id="0df27-123">Transformation components with asynchronous outputs receive rows and add rows.</span></span>  
  
-   <span data-ttu-id="0df27-124">目标组件接收行，然后将接收到的行加载到目标。</span><span class="sxs-lookup"><span data-stu-id="0df27-124">Destination components receive rows and then load them into a destination.</span></span>  
  
 <span data-ttu-id="0df27-125">在执行期间，数据流任务将分配 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象，这些对象包含在一系列组件的输出列集合中定义的所有列。</span><span class="sxs-lookup"><span data-stu-id="0df27-125">During execution, the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain all the columns defined in the output column collections of a sequence of components.</span></span> <span data-ttu-id="0df27-126">例如，如果数据流序列中的四个组件都向其输出列集合中添加一个输出列，则提供给每个组件的缓冲区中将包含四个列，分别对应每个组件的输出列。</span><span class="sxs-lookup"><span data-stu-id="0df27-126">For example, if each of four components in a data flow sequence adds one output column to its output column collection,the buffer that is provided to each component contains four columns, one for each output column per component.</span></span> <span data-ttu-id="0df27-127">受此行为影响，组件有时将接收包含不使用的列的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="0df27-127">Because of this behavior, a component sometimes receives buffers that contain columns it does not use.</span></span>  
  
 <span data-ttu-id="0df27-128">由于组件接收的缓冲区可能包含该组件不使用的列，因此必须在数据流提供给组件的缓冲区中查找将在组件的输入和输出列集合中使用的列。</span><span class="sxs-lookup"><span data-stu-id="0df27-128">Since the buffers received by your component may contain columns that the component will not use, you must locate the columns that you want to use in your component's input and output column collections in the buffer provided to the component by the data flow task.</span></span> <span data-ttu-id="0df27-129">可使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 属性的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法实现此目的。</span><span class="sxs-lookup"><span data-stu-id="0df27-129">You do this by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property.</span></span> <span data-ttu-id="0df27-130">出于性能方面的考虑，此任务通常在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 方法期间执行，而不在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 中执行。</span><span class="sxs-lookup"><span data-stu-id="0df27-130">For performance reasons, this task is ordinarily performed during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, rather than in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
 <span data-ttu-id="0df27-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法之前调用，这是在组件可使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 之后第一个组件可执行列查找任务的机会。</span><span class="sxs-lookup"><span data-stu-id="0df27-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods, and is the first opportunity for a component to perform this work after the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> becomes available to the component.</span></span> <span data-ttu-id="0df27-132">在此方法期间，组件应在缓冲区查找列，并内部存储此信息，以便在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法中使用这些列。</span><span class="sxs-lookup"><span data-stu-id="0df27-132">During this method, the component should locate its columns in the buffers and store this information internally so the columns can be used in either the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span>  
  
 <span data-ttu-id="0df27-133">下面的代码示例演示具有同步输出的转换组件如何在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期间在缓冲区查找其输出列。</span><span class="sxs-lookup"><span data-stu-id="0df27-133">The following code example demonstrates how a transformation component with a synchronous output locates its input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span>  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a><span data-ttu-id="0df27-134">添加行</span><span class="sxs-lookup"><span data-stu-id="0df27-134">Adding Rows</span></span>  
 <span data-ttu-id="0df27-135">组件通过向 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象添加行来向下游组件提供行。</span><span class="sxs-lookup"><span data-stu-id="0df27-135">Components supply rows to downstream components by adding rows to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="0df27-136">数据流任务将一组输出缓冲区作为参数提供给 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 方法，其中一个缓冲区对应一个连接到下游组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 对象。</span><span class="sxs-lookup"><span data-stu-id="0df27-136">The data flow task provides an array of output buffers - one for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that is connected to a downstream component - as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="0df27-137">源组件和具有异步输出的转换组件向缓冲区中添加行，并在完成行添加后调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-137">Source components and transformation components with asynchronous outputs add rows to the buffers and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method when they are finished adding rows.</span></span> <span data-ttu-id="0df27-138">数据流任务将管理其提供给组件的输出缓冲区，并在缓冲区写满之后自动将缓冲区中的行移动至下一个组件。</span><span class="sxs-lookup"><span data-stu-id="0df27-138">The data flow task manages the output buffers that it supplies to components and, as a buffer becomes full, automatically moves the rows in the buffer to the next component.</span></span> <span data-ttu-id="0df27-139">与可重复调用的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法不同，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法仅为每个组件调用一次。</span><span class="sxs-lookup"><span data-stu-id="0df27-139">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is called one time per component, unlike  the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, which is called repeatedly.</span></span>  
  
 <span data-ttu-id="0df27-140">下面的代码示例演示组件如何在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法期间向其输出缓冲区添加行，然后调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0df27-140">The following code example demonstrates how a component adds rows to its output buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method, then calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method.</span></span>  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 <span data-ttu-id="0df27-141">有关开发用于向输出缓冲区添加行的组件的详细信息，请参阅[开发自定义源组件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)和[开发具有异步输出的自定义转换组件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)。</span><span class="sxs-lookup"><span data-stu-id="0df27-141">For more information about developing components that add rows to output buffers, see [Developing a Custom Source Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) and [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span>  
  
### <a name="receiving-rows"></a><span data-ttu-id="0df27-142">接收行</span><span class="sxs-lookup"><span data-stu-id="0df27-142">Receiving Rows</span></span>  
 <span data-ttu-id="0df27-143">组件在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象中接收来自上游组件的行。</span><span class="sxs-lookup"><span data-stu-id="0df27-143">Components receive rows from upstream components in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="0df27-144">数据流任务将 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象作为参数提供给 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法，该对象包含上游组件添加到数据流的行。</span><span class="sxs-lookup"><span data-stu-id="0df27-144">The data flow task provides a <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> object that contains the rows added to the data flow by upstream components as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="0df27-145">此输出缓冲区可用于检查和修改缓冲区中的行和列，但不能用于添加或删除行。</span><span class="sxs-lookup"><span data-stu-id="0df27-145">This input buffer can be used to examine and modify the rows and columns in the buffer, but cannot be used to add or remove rows.</span></span> <span data-ttu-id="0df27-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法可重复调用，直到没有可用的缓冲区为止。</span><span class="sxs-lookup"><span data-stu-id="0df27-146">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method is called repeatedly until there are no more available buffers.</span></span> <span data-ttu-id="0df27-147">最后一次调用时，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 属性为 `true`。</span><span class="sxs-lookup"><span data-stu-id="0df27-147">The last time it is called, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="0df27-148">可使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 方法（可将缓冲区移至下一行）循环访问缓冲区中的行集合。</span><span class="sxs-lookup"><span data-stu-id="0df27-148">You can iterate over the collection of rows in the buffer by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method, which advances the buffer to the next row.</span></span> <span data-ttu-id="0df27-149">当缓冲区位于集合中的最后一行时，此方法将返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="0df27-149">This method returns `false` when the buffer is on the last row in the collection.</span></span> <span data-ttu-id="0df27-150">您不必检查 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 属性，除非在处理最后一行数据后需要执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="0df27-150">You do not have to check the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property unless you have to perform an additional action after the last rows of data have been processed.</span></span>  
  
 <span data-ttu-id="0df27-151">下面的文本显示了 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 方法和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 属性的正确用法：</span><span class="sxs-lookup"><span data-stu-id="0df27-151">The following text shows the correct pattern for using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property:</span></span>  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 <span data-ttu-id="0df27-152">下面的代码示例演示组件如何在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法期间处理输入缓冲区中的行。</span><span class="sxs-lookup"><span data-stu-id="0df27-152">The following code example demonstrates how a component processes the rows in input buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 <span data-ttu-id="0df27-153">有关开发用于接收输入缓冲区中的行的组件的详细信息，请参阅[开发自定义目标组件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)和[开发具有同步输出的自定义转换组件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)。</span><span class="sxs-lookup"><span data-stu-id="0df27-153">For more information about developing components that receive rows in input buffers, see [Developing a Custom Destination Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) and [Developing a Custom Transformation Component with Synchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>  
  
<span data-ttu-id="0df27-154">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="0df27-154">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0df27-155">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="0df27-155">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0df27-156">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="0df27-156">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0df27-157">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="0df27-157">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df27-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0df27-158">See Also</span></span>  
 [<span data-ttu-id="0df27-159">数据流组件的设计时方法</span><span class="sxs-lookup"><span data-stu-id="0df27-159">Design-time Methods of a Data Flow Component</span></span>](design-time-methods-of-a-data-flow-component.md)  
  
  
