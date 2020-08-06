---
title: 开发具有异步输出的自定义转换组件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], transformation components
- asynchronous outputs [Integration Services]
- ProcessInput method
- cache [Integration Services]
- buffer allocations [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], transformation components
ms.assetid: 1c3e92c7-a4fa-4fdd-b9ca-ac3069536274
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41e2ecdf9f90765e75ff2b8c9c0681a25366e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691816"
---
# <a name="developing-a-custom-transformation-component-with-asynchronous-outputs"></a><span data-ttu-id="1ee17-102">开发具有异步输出的自定义转换组件</span><span class="sxs-lookup"><span data-stu-id="1ee17-102">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>
  <span data-ttu-id="1ee17-103">如果某个转换直到组件收到其所有输入行后才输出行，或者该转换不是为收到的每个输入行生成一个输出行，则可以使用具有异步输出的组件。</span><span class="sxs-lookup"><span data-stu-id="1ee17-103">You use a component with asynchronous outputs when a transform cannot output rows until the component has received all its input rows, or when the transformation does not produce exactly one output row for each row received as input.</span></span> <span data-ttu-id="1ee17-104">例如，聚合转换只有在它读取所有行之后才能计算各行的总和。</span><span class="sxs-lookup"><span data-stu-id="1ee17-104">The Aggregate transformation, for example, cannot calculate a sum across rows until it has read all the rows.</span></span> <span data-ttu-id="1ee17-105">与之相反，如果可以在每个数据行传递给组件时就修改该行，则可以使用具有同步输出的组件。</span><span class="sxs-lookup"><span data-stu-id="1ee17-105">In contrast, you can use a component with synchronous outputs any time when you modify each row of data as it passes through.</span></span> <span data-ttu-id="1ee17-106">您可以就地修改每行的数据，或者创建一个或多个新列，其中每一列的值与每个输入行对应。</span><span class="sxs-lookup"><span data-stu-id="1ee17-106">You can modify the data for each row in place, or you can create one or more new columns, each of which has a value for every one of the input rows.</span></span> <span data-ttu-id="1ee17-107">有关同步组件和异步组件之间的差异的详细信息，请参阅[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee17-107">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="1ee17-108">具有异步输出的转换组件非常独特，因为它们既充当目标组件又充当源组件。</span><span class="sxs-lookup"><span data-stu-id="1ee17-108">Transformation components with asynchronous outputs are unique because they act as both destination and source components.</span></span> <span data-ttu-id="1ee17-109">此类组件从上游组件接收行，然后添加下游组件所使用的行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-109">This kind of component receives rows from upstream components, and adds rows that are consumed by downstream components.</span></span> <span data-ttu-id="1ee17-110">其他任何数据流组件都不同时执行这两个操作。</span><span class="sxs-lookup"><span data-stu-id="1ee17-110">No other data flow component performs both of these operations.</span></span>

 <span data-ttu-id="1ee17-111">对于具有同步输出的组件，如果来自其上游组件的列可用于该组件，则对于该组件下游的组件，这些列是自动可用的。</span><span class="sxs-lookup"><span data-stu-id="1ee17-111">The columns from upstream components that are available to a component with synchronous outputs are automatically available to components downstream from the component.</span></span> <span data-ttu-id="1ee17-112">因此，具有同步输出的组件不一定要定义输出列，以便为下一组件提供列和行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-112">Therefore, a component with synchronous outputs does not have to define any output columns to provide columns and rows to the next component.</span></span> <span data-ttu-id="1ee17-113">而具有异步输出的组件则必须定义输出列并向下游组件提供行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-113">Components with asynchronous outputs, on the other hand, must define output columns and provide rows to downstream components.</span></span> <span data-ttu-id="1ee17-114">因此，具有异步输出的组件在设计时和执行时要执行更多的任务，而组件开发人员要实现更多的代码。</span><span class="sxs-lookup"><span data-stu-id="1ee17-114">Therefore a component with asynchronous outputs has more tasks to perform during both design and execution time, and the component developer has more code to implement.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1ee17-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含多个具有异步输出的转换。</span><span class="sxs-lookup"><span data-stu-id="1ee17-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains several transformations with asynchronous outputs.</span></span> <span data-ttu-id="1ee17-116">例如，排序转换需要收到所有行才能对这些行进行排序，这是通过异步输出完成的。</span><span class="sxs-lookup"><span data-stu-id="1ee17-116">For example, the Sort transformation requires all its rows before it can sort them, and achieves this by using asynchronous outputs.</span></span> <span data-ttu-id="1ee17-117">该转换收到所有行之后，对这些行进行排序，然后将这些行添加到其输出。</span><span class="sxs-lookup"><span data-stu-id="1ee17-117">After it has received all its rows, it sorts them and adds them to its output.</span></span>

 <span data-ttu-id="1ee17-118">本节详细说明如何开发具有异步输出的转换。</span><span class="sxs-lookup"><span data-stu-id="1ee17-118">This section explains in detail how to develop transformations with asynchronous outputs.</span></span> <span data-ttu-id="1ee17-119">有关源组件开发的详细信息，请参阅[开发自定义源组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee17-119">For more information about source component development, see [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="1ee17-120">设计时</span><span class="sxs-lookup"><span data-stu-id="1ee17-120">Design Time</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="1ee17-121">创建组件</span><span class="sxs-lookup"><span data-stu-id="1ee17-121">Creating the Component</span></span>
 <span data-ttu-id="1ee17-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 对象的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 属性标识输出是同步的还是异步的。</span><span class="sxs-lookup"><span data-stu-id="1ee17-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property on the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object identifies whether an output is synchronous or asynchronous.</span></span> <span data-ttu-id="1ee17-123">若要创建异步输出，请将该输出添加到组件，然后将 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 设置为零。</span><span class="sxs-lookup"><span data-stu-id="1ee17-123">To create an asynchronous output, add the output to the component and set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> to zero.</span></span> <span data-ttu-id="1ee17-124">设置此属性还可以确定数据流任务是为组件的输入和输出都分配 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象，还是只分配一个缓冲区由两个对象共享。</span><span class="sxs-lookup"><span data-stu-id="1ee17-124">Setting this property also determines whether the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects for both the input and output of the component, or whether a single buffer is allocated and shared between the two objects.</span></span>

 <span data-ttu-id="1ee17-125">下面的示例代码演示在其 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 实现中创建异步输出的组件。</span><span class="sxs-lookup"><span data-stu-id="1ee17-125">The following sample code shows a component that creates an asynchronous output in its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> implementation.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "AsyncComponent",ComponentType = ComponentType.Transform)]
    public class AsyncComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Call the base class, which adds a synchronous input
            // and output.
            base.ProvideComponentProperties();

            // Make the output asynchronous.
            IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
            output.SynchronousInputID = 0;
        }
    }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

<DtsPipelineComponent(DisplayName:="AsyncComponent", ComponentType:=ComponentType.Transform)> _
Public Class AsyncComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Call the base class, which adds a synchronous input
        ' and output.
        Me.ProvideComponentProperties()

        ' Make the output asynchronous.
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
        output.SynchronousInputID = 0

    End Sub

End Class
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="1ee17-126">创建和配置输出列</span><span class="sxs-lookup"><span data-stu-id="1ee17-126">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="1ee17-127">如上所述，异步组件向其输出列集合添加列来为下游组件提供列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-127">As mentioned earlier, an asynchronous component adds columns to its output column collection to provide columns to downstream components.</span></span> <span data-ttu-id="1ee17-128">有几种设计时方法可供选择，具体方法取决于组件的需求。</span><span class="sxs-lookup"><span data-stu-id="1ee17-128">There are several design-time methods to choose from, depending on the needs of the component.</span></span> <span data-ttu-id="1ee17-129">例如，如果要将来自上游组件的所有列都传递给下游组件，则需要重写 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> 方法来添加列，因为这是第一个使输入列可用于组件的方法。</span><span class="sxs-lookup"><span data-stu-id="1ee17-129">For example, if you want to pass all the columns from the upstream components to the downstream components, you would override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> method to add the columns, because this is the first method in which the input columns are available to the component.</span></span>

 <span data-ttu-id="1ee17-130">如果组件基于为其输入选择的列来创建输出列，请重写 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> 方法来选择输出列并指示如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="1ee17-130">If the component creates output columns based on the columns selected for its input, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> method to select the output columns and to indicate how they will be used.</span></span>

 <span data-ttu-id="1ee17-131">如果具有异步输出的组件基于来自上游组件的列创建输出列，并且可用的上游列发生变化，则该组件应更新其输出列集合。</span><span class="sxs-lookup"><span data-stu-id="1ee17-131">If a component with asynchronous outputs creates output columns based on the columns from upstream components, and the available upstream columns change, the component should update its output column collection.</span></span> <span data-ttu-id="1ee17-132">这些更改应该由组件在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 中检测，并在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 中修复。</span><span class="sxs-lookup"><span data-stu-id="1ee17-132">These changes should be detected by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and fixed during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.</span></span>

> [!NOTE]
>  <span data-ttu-id="1ee17-133">从输出列集合中删除一个输出列时，数据流中引用该列的下游组件会受到不利影响。</span><span class="sxs-lookup"><span data-stu-id="1ee17-133">When an output column is removed from the output column collection, downstream components in the data flow that reference the column are adversely affected.</span></span> <span data-ttu-id="1ee17-134">必须修复而不是先删除再重新创建该输出列，以防止下游组件断开。</span><span class="sxs-lookup"><span data-stu-id="1ee17-134">The output column must be repaired without removing and recreating the column to prevent breaking the downstream components.</span></span> <span data-ttu-id="1ee17-135">例如，如果该列的数据类型发生变化，必须更新数据类型。</span><span class="sxs-lookup"><span data-stu-id="1ee17-135">For example, if the data type of the column has changed, you must update the data type.</span></span>

 <span data-ttu-id="1ee17-136">下面的代码示例演示了一个组件，它对来自上游组件的每个可用列都向其输出列集合添加一个输出列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-136">The following code example shows a component that adds an output column to its output column collection for each column available from the upstream component.</span></span>

```csharp
public override void OnInputPathAttached(int inputID)
{
   IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);
   IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
   IDTSVirtualInput100 vInput = input.GetVirtualInput();

   foreach (IDTSVirtualInputColumn100 vCol in vInput.VirtualInputColumnCollection)
   {
      IDTSOutputColumn100 outCol = output.OutputColumnCollection.New();
      outCol.Name = vCol.Name;
      outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage);
   }
}
```

```vb
Public Overrides Sub OnInputPathAttached(ByVal inputID As Integer)

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput()

    For Each vCol As IDTSVirtualInputColumn100 In vInput.VirtualInputColumnCollection

        Dim outCol As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        outCol.Name = vCol.Name
        outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage)

    Next
End Sub
```

## <a name="run-time"></a><span data-ttu-id="1ee17-137">运行时</span><span class="sxs-lookup"><span data-stu-id="1ee17-137">Run Time</span></span>
 <span data-ttu-id="1ee17-138">具有异步输出的组件在运行时执行的一系列方法也与其他类型的组件不同。</span><span class="sxs-lookup"><span data-stu-id="1ee17-138">Components with asynchronous outputs also execute a different sequence of methods at run time than other types of components.</span></span> <span data-ttu-id="1ee17-139">首先，只有这种组件既接受对 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法的调用又接受对 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="1ee17-139">First, they are the only components that receive a call to both the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="1ee17-140">其次，具有异步输出的组件还需要在开始处理前访问所有传入行；因此，这些组件必须在内部缓存输入行直到读取所有行为止。</span><span class="sxs-lookup"><span data-stu-id="1ee17-140">Components with asynchronous outputs also require access to all the incoming rows before they can start processing; therefore, they must cache the input rows internally until all rows have been read.</span></span> <span data-ttu-id="1ee17-141">最后，与其他组件不同，具有异步输出的组件既接收输入缓冲区又接收输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1ee17-141">Finally, unlike other components, components with asynchronous outputs receive both an input buffer and an output buffer.</span></span>

### <a name="understanding-the-buffers"></a><span data-ttu-id="1ee17-142">了解缓冲区</span><span class="sxs-lookup"><span data-stu-id="1ee17-142">Understanding the Buffers</span></span>
 <span data-ttu-id="1ee17-143">组件在调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 期间接收输入缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1ee17-143">The input buffer is received by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="1ee17-144">此缓冲区包含由上游组件添加到该缓冲区中的行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-144">This buffer contains the rows added to the buffer by upstream components.</span></span> <span data-ttu-id="1ee17-145">该缓冲区还包含组件的输入列以及上游组件输出中提供的但是没有添加到异步组件输入集合中的列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-145">The buffer also contains the columns of the component's input, in addition to the columns that were provided in the output of an upstream component but were not added to the asynchronous component's input collection.</span></span>

 <span data-ttu-id="1ee17-146">输出缓冲区在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 中提供给组件，该缓冲区最初不包含行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-146">The output buffer, which is provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, does not initially contain rows.</span></span> <span data-ttu-id="1ee17-147">组件会向此缓冲区添加行，并在其写满时将其提供给下游组件。</span><span class="sxs-lookup"><span data-stu-id="1ee17-147">The component adds rows to this buffer and provides the buffer to downstream components when it is full.</span></span> <span data-ttu-id="1ee17-148">输出缓冲区包含在组件输出列集合中定义的列，还包含其他下游组件添加到其输出中的所有列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-148">The output buffer contains the columns defined in the component's output column collection, in addition to any columns that other downstream components have added to their outputs.</span></span>

 <span data-ttu-id="1ee17-149">此行为与具有同步输出的组件不同，后者只接收一个共享缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1ee17-149">This is different behavior from that of components with synchronous outputs, which receive a single shared buffer.</span></span> <span data-ttu-id="1ee17-150">具有同步输出的组件的共享缓冲区包含该组件的输入列和输出列，还包含添加到上游和下游组件输出中的列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-150">The shared buffer of a component with synchronous outputs contains both the input and output columns of the component, in addition to columns added to the outputs of upstream and downstream components.</span></span>

### <a name="processing-rows"></a><span data-ttu-id="1ee17-151">处理行</span><span class="sxs-lookup"><span data-stu-id="1ee17-151">Processing Rows</span></span>

#### <a name="caching-input-rows"></a><span data-ttu-id="1ee17-152">缓存输入行</span><span class="sxs-lookup"><span data-stu-id="1ee17-152">Caching Input Rows</span></span>
 <span data-ttu-id="1ee17-153">编写具有异步输出的组件时，有三种方法可向输出缓冲区添加行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-153">When you write a component with asynchronous outputs, you have three options for adding rows to the output buffer.</span></span> <span data-ttu-id="1ee17-154">您可以在接收输入行时添加它们，可以在接收到来自上游组件的所有行之后缓存它们，也可以在适合组件之时添加它们。</span><span class="sxs-lookup"><span data-stu-id="1ee17-154">You can add them as input rows are received, you can cache them until the component has received all the rows from the upstream component, or you can add them when it is appropriate to do so for the component.</span></span> <span data-ttu-id="1ee17-155">所选择的方法取决于组件的需要。</span><span class="sxs-lookup"><span data-stu-id="1ee17-155">The method that you choose depends on the requirements of the component.</span></span> <span data-ttu-id="1ee17-156">例如，排序组件需要在接收到所有上游行之后才能对其进行排序。</span><span class="sxs-lookup"><span data-stu-id="1ee17-156">For example, the Sort component requires that all the upstream rows be received before they can be sorted.</span></span> <span data-ttu-id="1ee17-157">因此，它会等到读取所有行之后再向输出缓冲区添加行。</span><span class="sxs-lookup"><span data-stu-id="1ee17-157">Therefore, it waits until all rows have been read before adding rows to the output buffer.</span></span>

 <span data-ttu-id="1ee17-158">在输入缓冲区中接收到的行必须由组件在内部缓存，直到它可以处理这些行为止。</span><span class="sxs-lookup"><span data-stu-id="1ee17-158">The rows that are received in the input buffer must be cached internally by the component until it is ready to process them.</span></span> <span data-ttu-id="1ee17-159">传入缓冲区行可缓存在数据表、多维数组或任何其他内部结构中。</span><span class="sxs-lookup"><span data-stu-id="1ee17-159">The incoming buffer rows can be cached in a data table, a multidimensional array, or any other internal structure.</span></span>

#### <a name="adding-output-rows"></a><span data-ttu-id="1ee17-160">添加输出行</span><span class="sxs-lookup"><span data-stu-id="1ee17-160">Adding Output Rows</span></span>
 <span data-ttu-id="1ee17-161">无论是在接收行的同时将行添加到输出缓冲区中还是在接收所有行之后再将其添加到输出缓冲区中，您都可以通过对输出缓冲区调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> 方法来实现。</span><span class="sxs-lookup"><span data-stu-id="1ee17-161">Whether you add rows to the output buffer as they are received or after receiving all of the rows, you do so by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method on the output buffer.</span></span> <span data-ttu-id="1ee17-162">添加行之后，您可以在新行中设置每列的值。</span><span class="sxs-lookup"><span data-stu-id="1ee17-162">After you have added the row, you set the values of each column in the new row.</span></span>

 <span data-ttu-id="1ee17-163">由于有时输出缓冲区中的列多于组件输出列集合中的列，因此您必须先找到相应列在缓冲区中的索引，然后才能设置其值。</span><span class="sxs-lookup"><span data-stu-id="1ee17-163">Because there are sometimes more columns in the output buffer than in the output column collection of the component, you must locate the index of the appropriate column in the buffer before you can set its value.</span></span> <span data-ttu-id="1ee17-164"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 属性的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法返回缓冲区行中具有指定沿袭 ID 的列的索引，该索引随后用于给该缓冲区列赋值。</span><span class="sxs-lookup"><span data-stu-id="1ee17-164">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property returns the index of the column in the buffer row with the specified lineage ID, which is then used to assign the value to the buffer column.</span></span>

 <span data-ttu-id="1ee17-165">在调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 方法或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法之前调用的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法是可使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 属性的第一个方法，并且是可以在输入和输出缓冲区中查找列索引的第一个机会。</span><span class="sxs-lookup"><span data-stu-id="1ee17-165">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, which is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method or the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, is the first method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property is available, and the first opportunity to locate the indexes of the columns in the input and output buffers.</span></span>

## <a name="sample"></a><span data-ttu-id="1ee17-166">示例</span><span class="sxs-lookup"><span data-stu-id="1ee17-166">Sample</span></span>
 <span data-ttu-id="1ee17-167">下面的示例演示一个具有异步输出的简单转换组件，该组件在接收到行时将其添加到输出缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="1ee17-167">The following sample shows a simple transformation component with asynchronous outputs that adds rows to the output buffer as they are received.</span></span> <span data-ttu-id="1ee17-168">此示例未演示本主题中讨论的全部方法和功能。</span><span class="sxs-lookup"><span data-stu-id="1ee17-168">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="1ee17-169">它演示了每个具有异步输出的自定义转换组件都必须重写的重要方法，但不包含用于设计时验证的代码。</span><span class="sxs-lookup"><span data-stu-id="1ee17-169">It demonstrates the important methods that every custom transformation component with asynchronous outputs must override, but does not contain code for design-time validation.</span></span> <span data-ttu-id="1ee17-170">此外，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 中的代码假定对于输入列集合中的每一列，输出列集合中都有相应的一列。</span><span class="sxs-lookup"><span data-stu-id="1ee17-170">Also, the code in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> assumes that the output column collection has one column for each column in the input column collection.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
   [DtsPipelineComponent(DisplayName = "AsynchronousOutput")]
   public class AsynchronousOutput : PipelineComponent
   {
      PipelineBuffer outputBuffer;
      int[] inputColumnBufferIndexes;
      int[] outputColumnBufferIndexes;

      public override void ProvideComponentProperties()
      {
         // Let the base class add the input and output objects.
         base.ProvideComponentProperties();

         // Name the input and output, and make the
         // output asynchronous.
         ComponentMetaData.InputCollection[0].Name = "Input";
         ComponentMetaData.OutputCollection[0].Name = "AsyncOutput";
         ComponentMetaData.OutputCollection[0].SynchronousInputID = 0;
      }
      public override void PreExecute()
      {
         IDTSInput100 input = ComponentMetaData.InputCollection[0];
         IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

         inputColumnBufferIndexes = new int[input.InputColumnCollection.Count];
         outputColumnBufferIndexes = new int[output.OutputColumnCollection.Count];

         for (int col = 0; col < input.InputColumnCollection.Count; col++)
            inputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[col].LineageID);

         for (int col = 0; col < output.OutputColumnCollection.Count; col++)
            outputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[col].LineageID);

      }

      public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
      {
         if (buffers.Length != 0)
            outputBuffer = buffers[0];
      }
      public override void ProcessInput(int inputID, PipelineBuffer buffer)
      {
            // Advance the buffer to the next row.
            while (buffer.NextRow())
            {
               // Add a row to the output buffer.
               outputBuffer.AddRow();
               for (int x = 0; x < inputColumnBufferIndexes.Length; x++)
               {
                  // Copy the data from the input buffer column to the output buffer column.
                  outputBuffer[outputColumnBufferIndexes[x]] = buffer[inputColumnBufferIndexes[x]];
               }
            }
         if (buffer.EndOfRowset)
         {
            // EndOfRowset on the input buffer is true.
            // Set EndOfRowset on the output buffer.
            outputBuffer.SetEndOfRowset();
         }
      }
   }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="AsynchronousOutput")> _
    Public Class AsynchronousOutput

        Inherits PipelineComponent

        Private outputBuffer As PipelineBuffer
        Private inputColumnBufferIndexes As Integer()
        Private outputColumnBufferIndexes As Integer()

        Public Overrides Sub ProvideComponentProperties()

            ' Let the base class add the input and output objects.
            Me.ProvideComponentProperties()

            ' Name the input and output, and make the
            ' output asynchronous.
            ComponentMetaData.InputCollection(0).Name = "Input"
            ComponentMetaData.OutputCollection(0).Name = "AsyncOutput"
            ComponentMetaData.OutputCollection(0).SynchronousInputID = 0
        End Sub

        Public Overrides Sub PreExecute()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)
            Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

            ReDim inputColumnBufferIndexes(input.InputColumnCollection.Count)
            ReDim outputColumnBufferIndexes(output.OutputColumnCollection.Count)

            For col As Integer = 0 To input.InputColumnCollection.Count
                inputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(col).LineageID)
            Next

            For col As Integer = 0 To output.OutputColumnCollection.Count
                outputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(col).LineageID)
            Next

        End Sub
        Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

            If buffers.Length <> 0 Then
                outputBuffer = buffers(0)
            End If

        End Sub

        Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

                ' Advance the buffer to the next row.
                While (buffer.NextRow())

                    ' Add a row to the output buffer.
                    outputBuffer.AddRow()
                    For x As Integer = 0 To inputColumnBufferIndexes.Length

                        ' Copy the data from the input buffer column to the output buffer column.
                        outputBuffer(outputColumnBufferIndexes(x)) = buffer(inputColumnBufferIndexes(x))

                    Next
                End While

            If buffer.EndOfRowset = True Then
                ' EndOfRowset on the input buffer is true.
                ' Set the end of row set on the output buffer.
                outputBuffer.SetEndOfRowset()
            End If
        End Sub
    End Class
End Namespace
```

<span data-ttu-id="1ee17-171">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1ee17-171">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1ee17-172">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1ee17-172">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1ee17-173">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1ee17-173">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1ee17-174">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1ee17-174">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ee17-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ee17-175">See Also</span></span>
 <span data-ttu-id="1ee17-176">[开发具有同步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="1ee17-176">[Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span></span>


