---
title: 开发具有同步输出的自定义转换组件 | Microsoft Docs
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
- ProcessInput method
- buffer allocations [Integration Services]
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- data flow components [Integration Services], transformation components
ms.assetid: b694d21f-9919-402d-9192-666c6449b0b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 94d78872570103d3df7e1cb96aecb144fafe4257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691817"
---
# <a name="developing-a-custom-transformation-component-with-synchronous-outputs"></a><span data-ttu-id="10abb-102">开发具有同步输出的自定义转换组件</span><span class="sxs-lookup"><span data-stu-id="10abb-102">Developing a Custom Transformation Component with Synchronous Outputs</span></span>
  <span data-ttu-id="10abb-103">具有同步输出的转换组件接收来自上游组件的行，并在将行传递到下游组件时读取或修改这些行的列中的值。</span><span class="sxs-lookup"><span data-stu-id="10abb-103">Transformation components with synchronous outputs receive rows from upstream components, and read or modify the values in the columns of these rows as they pass the rows to downstream components.</span></span> <span data-ttu-id="10abb-104">这些转换组件还定义从上游组件提供的列派生的其他输出列，但是它们不会向数据流添加行。</span><span class="sxs-lookup"><span data-stu-id="10abb-104">They may also define additional output columns that are derived from the columns provided by upstream components, but they do not add rows to the data flow.</span></span> <span data-ttu-id="10abb-105">有关同步组件和异步组件之间的差异的详细信息，请参阅[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="10abb-105">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>  
  
 <span data-ttu-id="10abb-106">这类组件适用的任务如下：任务中的数据在提供给组件时被内联修改，并且组件在处理这些行之前不必看到所有行。</span><span class="sxs-lookup"><span data-stu-id="10abb-106">This kind of component is suited for tasks where the data is modified inline as it is provided to the component and where the component does not have to see all the rows before processing them.</span></span> <span data-ttu-id="10abb-107">这是用于开发的最简单组件，因为具有同步输出的转换通常不连接到外部数据源、管理外部元数据列或向输出缓冲区添加行。</span><span class="sxs-lookup"><span data-stu-id="10abb-107">It is the easiest component to develop because transformations with synchronous outputs typically do not connect to external data sources, manage external metadata columns, or add rows to output buffers.</span></span>  
  
 <span data-ttu-id="10abb-108">创建具有同步输出的转换组件涉及添加一个将包含为该组件选择的上游列的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>，和一个可能包含组件创建的派生列的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 对象。</span><span class="sxs-lookup"><span data-stu-id="10abb-108">Creating a transformation component with synchronous outputs involves adding an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> that will contain the upstream columns selected for the component, and a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that may contain derived columns created by the component.</span></span> <span data-ttu-id="10abb-109">还包括实现设计时方法以及提供在执行期间用于读取或修改传入缓冲区中的列的代码。</span><span class="sxs-lookup"><span data-stu-id="10abb-109">It also includes implementing the design-time methods, and providing code that reads or modifies the columns in the incoming buffer rows during execution.</span></span>  
  
 <span data-ttu-id="10abb-110">本节提供了实现自定义转换组件所需的信息，以及有助于您更好地了解这些概念的代码示例。</span><span class="sxs-lookup"><span data-stu-id="10abb-110">This section provides the information that is required to implement a custom transformation component, and provides code examples to help you better understand the concepts.</span></span>  
  
## <a name="design-time"></a><span data-ttu-id="10abb-111">设计时</span><span class="sxs-lookup"><span data-stu-id="10abb-111">Design Time</span></span>  
 <span data-ttu-id="10abb-112">此组件的设计时代码涉及创建输入和输出、添加组件生成的任何其他输出列以及验证组件的配置。</span><span class="sxs-lookup"><span data-stu-id="10abb-112">The design-time code for this component involves creating the inputs and outputs, adding any additional output columns that the component generates, and validating the configuration of the component.</span></span>  
  
### <a name="creating-the-component"></a><span data-ttu-id="10abb-113">创建组件</span><span class="sxs-lookup"><span data-stu-id="10abb-113">Creating the Component</span></span>  
 <span data-ttu-id="10abb-114">组件的输入、输出和自定义属性通常在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法期间创建。</span><span class="sxs-lookup"><span data-stu-id="10abb-114">The inputs, outputs, and custom properties of the component are typically created during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="10abb-115">您可以使用两种方式添加具有同步输出的转换组件的输入和输出。</span><span class="sxs-lookup"><span data-stu-id="10abb-115">There are two ways that you can add the input and the output of a transformation component with synchronous outputs.</span></span> <span data-ttu-id="10abb-116">可以使用方法的基类实现，然后修改该方法创建的默认输入和输出，也可以自己显式添加输入和输出。</span><span class="sxs-lookup"><span data-stu-id="10abb-116">You can use the base class implementation of the method and then modify the default input and output that it creates, or you can explicitly add the input and output yourself.</span></span>  
  
 <span data-ttu-id="10abb-117">下面的代码示例演示显式添加输入和输出对象的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 实现。</span><span class="sxs-lookup"><span data-stu-id="10abb-117">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that explicitly adds the input and output objects.</span></span> <span data-ttu-id="10abb-118">注释中包含对将要完成同样任务的基类的调用。</span><span class="sxs-lookup"><span data-stu-id="10abb-118">The call to the base class that would accomplish the same thing is included in a comment.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SynchronousComponent", ComponentType = ComponentType.Transform)]  
    public class SyncComponent : PipelineComponent  
    {  
  
        public override void ProvideComponentProperties()  
        {  
            // Add the input.  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            // Add the output.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
            output.SynchronousInputID = input.ID;  
  
            // Alternatively, you can let the base class add the input and output  
            // and set the SynchronousInputID of the output to the ID of the input.  
            // base.ProvideComponentProperties();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="SynchronousComponent", ComponentType:=ComponentType.Transform)> _  
Public Class SyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Add the input.  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
        input.Name = "Input"  
  
        ' Add the output.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
        output.SynchronousInputID = Input.ID  
  
        ' Alternatively, you can let the base class add the input and output  
        ' and set the SynchronousInputID of the output to the ID of the input.  
        ' base.ProvideComponentProperties();  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="10abb-119">创建和配置输出列</span><span class="sxs-lookup"><span data-stu-id="10abb-119">Creating and Configuring Output Columns</span></span>  
 <span data-ttu-id="10abb-120">尽管具有同步输出的转换组件不向缓冲区添加行，但是它们可能向自己的输出添加额外的输出列。</span><span class="sxs-lookup"><span data-stu-id="10abb-120">Although transformation components with synchronous outputs do not add rows to buffers, they may add extra output columns to their output.</span></span> <span data-ttu-id="10abb-121">通常，当组件添加输出列时，新输出列的值在运行时从一个或多个列中包含的数据派生而来，这些列由上游组件提供给该组件。</span><span class="sxs-lookup"><span data-stu-id="10abb-121">Typically, when a component adds an output column, the values for the new output column are derived at run time from the data that is contained in one or more of the columns provided to the component by an upstream component.</span></span>  
  
 <span data-ttu-id="10abb-122">创建输出列后，必须设置该列的数据类型属性。</span><span class="sxs-lookup"><span data-stu-id="10abb-122">After an output column has been created, its data type properties must be set.</span></span> <span data-ttu-id="10abb-123">输出列的数据类型属性的设置需要特殊处理，并通过调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> 方法来执行。</span><span class="sxs-lookup"><span data-stu-id="10abb-123">Setting the data type properties of an output column requires special handling and is performed by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="10abb-124">此方法是必需的，因为 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> 属性在单独情况下都是只读的，原因是每个属性均取决于另一个属性的设置。</span><span class="sxs-lookup"><span data-stu-id="10abb-124">This method is required because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are individually read-only, because each depends on the settings of the other.</span></span> <span data-ttu-id="10abb-125">此方法可保证属性值的设置保持一致，并且数据流任务会验证是否正确设置了这些值。</span><span class="sxs-lookup"><span data-stu-id="10abb-125">This method guarantees that the values of the properties are set consistently, and the data flow task validates that they are set correctly.</span></span>  
  
 <span data-ttu-id="10abb-126">列的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 决定了为其他属性设置的值。</span><span class="sxs-lookup"><span data-stu-id="10abb-126">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="10abb-127">下表说明了对每个 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 的依赖属性的要求。</span><span class="sxs-lookup"><span data-stu-id="10abb-127">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="10abb-128">未列出的数据类型的依赖属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="10abb-128">The data types not listed have their dependent properties set to zero.</span></span>  
  
|<span data-ttu-id="10abb-129">数据类型</span><span class="sxs-lookup"><span data-stu-id="10abb-129">DataType</span></span>|<span data-ttu-id="10abb-130">长度</span><span class="sxs-lookup"><span data-stu-id="10abb-130">Length</span></span>|<span data-ttu-id="10abb-131">缩放</span><span class="sxs-lookup"><span data-stu-id="10abb-131">Scale</span></span>|<span data-ttu-id="10abb-132">Precision</span><span class="sxs-lookup"><span data-stu-id="10abb-132">Precision</span></span>|<span data-ttu-id="10abb-133">CodePage</span><span class="sxs-lookup"><span data-stu-id="10abb-133">CodePage</span></span>|  
|--------------|------------|-----------|---------------|--------------|  
|<span data-ttu-id="10abb-134">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="10abb-134">DT_DECIMAL</span></span>|<span data-ttu-id="10abb-135">0</span><span class="sxs-lookup"><span data-stu-id="10abb-135">0</span></span>|<span data-ttu-id="10abb-136">大于 0 且小于或等于 28。</span><span class="sxs-lookup"><span data-stu-id="10abb-136">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="10abb-137">0</span><span class="sxs-lookup"><span data-stu-id="10abb-137">0</span></span>|<span data-ttu-id="10abb-138">0</span><span class="sxs-lookup"><span data-stu-id="10abb-138">0</span></span>|  
|<span data-ttu-id="10abb-139">DT_CY</span><span class="sxs-lookup"><span data-stu-id="10abb-139">DT_CY</span></span>|<span data-ttu-id="10abb-140">0</span><span class="sxs-lookup"><span data-stu-id="10abb-140">0</span></span>|<span data-ttu-id="10abb-141">0</span><span class="sxs-lookup"><span data-stu-id="10abb-141">0</span></span>|<span data-ttu-id="10abb-142">0</span><span class="sxs-lookup"><span data-stu-id="10abb-142">0</span></span>|<span data-ttu-id="10abb-143">0</span><span class="sxs-lookup"><span data-stu-id="10abb-143">0</span></span>|  
|<span data-ttu-id="10abb-144">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="10abb-144">DT_NUMERIC</span></span>|<span data-ttu-id="10abb-145">0</span><span class="sxs-lookup"><span data-stu-id="10abb-145">0</span></span>|<span data-ttu-id="10abb-146">大于 0 且小于或等于 28，并且小于 Precision。</span><span class="sxs-lookup"><span data-stu-id="10abb-146">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="10abb-147">大于或等于 1 且小于或等于 38。</span><span class="sxs-lookup"><span data-stu-id="10abb-147">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="10abb-148">0</span><span class="sxs-lookup"><span data-stu-id="10abb-148">0</span></span>|  
|<span data-ttu-id="10abb-149">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="10abb-149">DT_BYTES</span></span>|<span data-ttu-id="10abb-150">大于 0。</span><span class="sxs-lookup"><span data-stu-id="10abb-150">Greater than 0.</span></span>|<span data-ttu-id="10abb-151">0</span><span class="sxs-lookup"><span data-stu-id="10abb-151">0</span></span>|<span data-ttu-id="10abb-152">0</span><span class="sxs-lookup"><span data-stu-id="10abb-152">0</span></span>|<span data-ttu-id="10abb-153">0</span><span class="sxs-lookup"><span data-stu-id="10abb-153">0</span></span>|  
|<span data-ttu-id="10abb-154">DT_STR</span><span class="sxs-lookup"><span data-stu-id="10abb-154">DT_STR</span></span>|<span data-ttu-id="10abb-155">大于 0 且小于 8000。</span><span class="sxs-lookup"><span data-stu-id="10abb-155">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="10abb-156">0</span><span class="sxs-lookup"><span data-stu-id="10abb-156">0</span></span>|<span data-ttu-id="10abb-157">0</span><span class="sxs-lookup"><span data-stu-id="10abb-157">0</span></span>|<span data-ttu-id="10abb-158">不为 0，并且是一个有效的代码页。</span><span class="sxs-lookup"><span data-stu-id="10abb-158">Not 0, and a valid code page.</span></span>|  
|<span data-ttu-id="10abb-159">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="10abb-159">DT_WSTR</span></span>|<span data-ttu-id="10abb-160">大于 0 且小于 4000。</span><span class="sxs-lookup"><span data-stu-id="10abb-160">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="10abb-161">0</span><span class="sxs-lookup"><span data-stu-id="10abb-161">0</span></span>|<span data-ttu-id="10abb-162">0</span><span class="sxs-lookup"><span data-stu-id="10abb-162">0</span></span>|<span data-ttu-id="10abb-163">0</span><span class="sxs-lookup"><span data-stu-id="10abb-163">0</span></span>|  
  
 <span data-ttu-id="10abb-164">由于对数据类型属性的限制是基于输出列的数据类型的，因此使用托管类型时必须选择正确的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="10abb-164">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="10abb-165">基类提供了三个帮助器方法：<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>，它们可协助托管组件开发人员在给定托管类型的情况下选择 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="10abb-165">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> that assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="10abb-166">这些方法用于将托管数据类型转换为 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数据类型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="10abb-166">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="10abb-167">运行时</span><span class="sxs-lookup"><span data-stu-id="10abb-167">Run Time</span></span>  
 <span data-ttu-id="10abb-168">通常，组件的运行时部分的实现分为两个任务：在缓冲区中查找组件的输入和输出列，以及在传入缓冲区行中读取或写入这些列的值。</span><span class="sxs-lookup"><span data-stu-id="10abb-168">Generally, the implementation of the run-time part of the component is categorized into two tasks-locating the input and output columns of the component in the buffer, and reading or writing the values of these columns in the incoming buffer rows.</span></span>  
  
### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="10abb-169">在缓冲区中查找列</span><span class="sxs-lookup"><span data-stu-id="10abb-169">Locating Columns in the Buffer</span></span>  
 <span data-ttu-id="10abb-170">在执行期间提供给组件的缓冲区中的列数将很可能超过组件的输入或输出集合中的列数。</span><span class="sxs-lookup"><span data-stu-id="10abb-170">The number of columns in the buffers that are provided to a component during execution will likely exceed the number of columns in the input or output collections of the component.</span></span> <span data-ttu-id="10abb-171">这是因为每个缓冲区都包含在数据流的组件中定义的所有输出列。</span><span class="sxs-lookup"><span data-stu-id="10abb-171">This is because each buffer contains all the output columns defined in the components in a data flow.</span></span> <span data-ttu-id="10abb-172">为了确保缓冲区列与输出或输出的列正确匹配，组件开发人员必须使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="10abb-172">To ensure that the buffer columns are correctly matched to the columns of the input or output, component developers must use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="10abb-173">此方法会根据其沿袭 ID 在已定义的缓冲区中查找列。</span><span class="sxs-lookup"><span data-stu-id="10abb-173">This method locates a column in the specified buffer by its lineage ID.</span></span> <span data-ttu-id="10abb-174">这些列通常在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期间进行查找，因为这是第一个其 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 属性可用的运行时方法。</span><span class="sxs-lookup"><span data-stu-id="10abb-174">Typically columns are located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> because this is the first run-time method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property becomes available.</span></span>  
  
 <span data-ttu-id="10abb-175">下面的代码示例演示了一个组件，该组件在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期间查找其输入和输出列集合中的列的索引。</span><span class="sxs-lookup"><span data-stu-id="10abb-175">The following code example shows a component that locates indexes of the columns in its input and output column collection during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span> <span data-ttu-id="10abb-176">列的索引存储在整数数组中，可在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 期间由组件访问。</span><span class="sxs-lookup"><span data-stu-id="10abb-176">The column indexes are stored in an integer array, and can be accessed by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
```csharp  
int []inputColumns;  
int []outputColumns;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    inputColumns = new int[input.InputColumnCollection.Count];  
    outputColumns = new int[output.OutputColumnCollection.Count];  
  
    for(int col=0; col < input.InputColumnCollection.Count; col++)  
    {  
        IDTSInputColumn100 inputColumn = input.InputColumnCollection[col];  
        inputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID);  
    }  
  
    for(int col=0; col < output.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 outputColumn = output.OutputColumnCollection[col];  
        outputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID);  
    }  
  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ReDim inputColumns(input.InputColumnCollection.Count)  
    ReDim outputColumns(output.OutputColumnCollection.Count)  
  
    For col As Integer = 0 To input.InputColumnCollection.Count  
  
        Dim inputColumn As IDTSInputColumn100 = input.InputColumnCollection(col)  
        inputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID)  
    Next  
  
    For col As Integer = 0 To output.OutputColumnCollection.Count  
  
        Dim outputColumn As IDTSOutputColumn100 = output.OutputColumnCollection(col)  
        outputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID)  
    Next  
  
End Sub  
```  
  
### <a name="processing-rows"></a><span data-ttu-id="10abb-177">处理行</span><span class="sxs-lookup"><span data-stu-id="10abb-177">Processing Rows</span></span>  
 <span data-ttu-id="10abb-178">组件可接收 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 对象，这些对象包含 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法中的行和列。</span><span class="sxs-lookup"><span data-stu-id="10abb-178">Components receive <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain rows and columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="10abb-179">在此方法中，将循环访问缓冲区中的行，并读取和修改 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期间标识的列。</span><span class="sxs-lookup"><span data-stu-id="10abb-179">During this method the rows in the buffer are iterated, and the columns identified during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> are read and modified.</span></span> <span data-ttu-id="10abb-180">数据流任务将重复调用该方法，直到上游组件不再提供行。</span><span class="sxs-lookup"><span data-stu-id="10abb-180">The method is called repeatedly by the data flow task until no more rows are provided from the upstream component.</span></span>  
  
 <span data-ttu-id="10abb-181">可使用数组索引器访问方法或者使用 `Get` 或 `Set` 方法之一来读取或写入缓冲区中的单个列。</span><span class="sxs-lookup"><span data-stu-id="10abb-181">An individual column in the buffer is read or written by using the array indexer access method, or by using one of the `Get` or `Set` methods.</span></span> <span data-ttu-id="10abb-182">`Get` 和 `Set` 方法的效率更高，应在缓冲区中的列的数据类型已知时使用。</span><span class="sxs-lookup"><span data-stu-id="10abb-182">The `Get` and `Set` methods are more efficient and should be used when the data type of the column in the buffer is known.</span></span>  
  
 <span data-ttu-id="10abb-183">下面的代码示例演示 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法的实现，该方法用于处理传入的行。</span><span class="sxs-lookup"><span data-stu-id="10abb-183">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method that processes incoming rows.</span></span>  
  
```csharp  
public override void ProcessInput( int InputID, PipelineBuffer buffer)  
{  
       while( buffer.NextRow())  
       {  
            for(int x=0; x < inputColumns.Length;x++)  
            {  
                if(!buffer.IsNull(inputColumns[x]))  
                {  
                    object columnData = buffer[inputColumns[x]];  
                    // TODO: Modify the column data.  
                    buffer[inputColumns[x]] = columnData;  
                }  
            }  
  
      }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal InputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For x As Integer = 0 To inputColumns.Length  
  
                if buffer.IsNull(inputColumns(x)) = false then  
  
                    Dim columnData As Object = buffer(inputColumns(x))  
                    ' TODO: Modify the column data.  
                    buffer(inputColumns(x)) = columnData  
  
                End If  
            Next  
  
        End While  
End Sub  
```  
  
## <a name="sample"></a><span data-ttu-id="10abb-184">示例</span><span class="sxs-lookup"><span data-stu-id="10abb-184">Sample</span></span>  
 <span data-ttu-id="10abb-185">下面的示例演示一个具有同步输出的简单转换组件，该组件将所有字符串列的值转换为大写。</span><span class="sxs-lookup"><span data-stu-id="10abb-185">The following sample shows a simple transformation component with synchronous outputs that converts the values of all string columns to uppercase.</span></span> <span data-ttu-id="10abb-186">此示例未演示本主题中讨论的全部方法和功能。</span><span class="sxs-lookup"><span data-stu-id="10abb-186">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="10abb-187">它演示了每个具有同步输出的自定义转换组件都必须重写的重要方法，但不包含用于设计时验证的代码。</span><span class="sxs-lookup"><span data-stu-id="10abb-187">It demonstrates the important methods that every custom transformation component with synchronous outputs must override, but does not contain code for design-time validation.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Uppercase  
{  
  [DtsPipelineComponent(DisplayName = "Uppercase")]  
  public class Uppercase : PipelineComponent  
  {  
    ArrayList m_ColumnIndexList = new ArrayList();  
  
    public override void ProvideComponentProperties()  
    {  
      base.ProvideComponentProperties();  
      ComponentMetaData.InputCollection[0].Name = "Uppercase Input";  
      ComponentMetaData.OutputCollection[0].Name = "Uppercase Output";  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        if (column.DataType == DataType.DT_STR || column.DataType == DataType.DT_WSTR)  
        {  
          m_ColumnIndexList.Add((int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID));  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        foreach (int columnIndex in m_ColumnIndexList)  
        {  
          string str = buffer.GetString(columnIndex);  
          buffer.SetString(columnIndex, str.ToUpper());  
        }  
      }  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.Collections   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace Uppercase   
  
 <DtsPipelineComponent(DisplayName="Uppercase")> _   
 Public Class Uppercase   
 Inherits PipelineComponent   
   Private m_ColumnIndexList As ArrayList = New ArrayList   
  
   Public  Overrides Sub ProvideComponentProperties()   
     MyBase.ProvideComponentProperties   
     ComponentMetaData.InputCollection(0).Name = "Uppercase Input"   
     ComponentMetaData.OutputCollection(0).Name = "Uppercase Output"   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     For Each column As IDTSInputColumn100 In inputColumns   
       If column.DataType = DataType.DT_STR OrElse column.DataType = DataType.DT_WSTR Then   
         m_ColumnIndexList.Add(CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer))   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       For Each columnIndex As Integer In m_ColumnIndexList   
         Dim str As String = buffer.GetString(columnIndex)   
         buffer.SetString(columnIndex, str.ToUpper)   
       Next   
     End While   
   End Sub   
 End Class   
End Namespace  
```  
  
<span data-ttu-id="10abb-188">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="10abb-188">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="10abb-189">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="10abb-189">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="10abb-190">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="10abb-190">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="10abb-191">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="10abb-191">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10abb-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10abb-192">See Also</span></span>  
 <span data-ttu-id="10abb-193">[开发具有异步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span><span class="sxs-lookup"><span data-stu-id="10abb-193">[Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span></span>  
 <span data-ttu-id="10abb-194">[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="10abb-194">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) </span></span>  
 [<span data-ttu-id="10abb-195">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="10abb-195">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
