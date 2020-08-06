---
title: 开发具有多个输入的数据流组件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb56878c1b1b68dfdc4de19cb2b811de494c761b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691814"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a><span data-ttu-id="9c2b0-102">开发具有多个输入的数据流组件</span><span class="sxs-lookup"><span data-stu-id="9c2b0-102">Developing Data Flow Components with Multiple Inputs</span></span>
  <span data-ttu-id="9c2b0-103">如果其多个输入以不相等速率生成数据，则具有多个输入的数据流组件可能会占用过多的内存。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-103">A data flow component with multiple inputs may consume excessive memory if its multiple inputs produce data at uneven rates.</span></span> <span data-ttu-id="9c2b0-104">开发支持两个或多个输入的自定义数据流组件时，可以通过使用 Microsoft.SqlServer.Dts.Pipeline 命名空间中的下列成员来管理此内存压力：</span><span class="sxs-lookup"><span data-stu-id="9c2b0-104">When you develop a custom data flow component that supports two or more inputs, you can manage this memory pressure by using the following members in the Microsoft.SqlServer.Dts.Pipeline namespace:</span></span>  
  
-   <span data-ttu-id="9c2b0-105"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 属性。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-105">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class.</span></span> <span data-ttu-id="9c2b0-106">如果您想要实现使您的自定义数据流组件可管理以不相等速率流动的数据所需的代码，则将此属性的值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-106">Set the value of this property to `true` if you want to implement the code that is necessary for your custom data flow component to manage data flowing at uneven rates.</span></span>  
  
-   <span data-ttu-id="9c2b0-107"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-107">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="9c2b0-108">如果您将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 属性设置为 `true`，则必须提供此方法的实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-108">You must provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true`.</span></span> <span data-ttu-id="9c2b0-109">如果未提供某一实现方式，则数据流引擎将在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-109">If you do not provide an implementation, the data flow engine raises an exception at run time.</span></span>  
  
-   <span data-ttu-id="9c2b0-110"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="9c2b0-111">如果您将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 属性设置为 `true`，并且您的自定义组件支持多个输入，则必须也提供此方法的实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-111">You must also provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` and your custom component supports more than two inputs.</span></span> <span data-ttu-id="9c2b0-112">如果未提供某一实现方式，且用户附加多个输入，则数据流引擎将在运行时将引发异常。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-112">If you do not provide an implementation, the data flow engine raises an exception at run time if the user attaches more than two inputs.</span></span>  
  
 <span data-ttu-id="9c2b0-113">这些成员一起使您能够开发一个解决方案来解决内存压力，该解决方案类似于 Microsoft 为合并转换和合并联接转换开发的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-113">Together, these members enable you to develop a solution for memory pressure that is similar to the solution that Microsoft developed for the Merge and Merge Join transformations.</span></span>  
  
## <a name="setting-the-supportsbackpressure-property"></a><span data-ttu-id="9c2b0-114">设置 SupportsBackPressure 属性</span><span class="sxs-lookup"><span data-stu-id="9c2b0-114">Setting the SupportsBackPressure Property</span></span>  
 <span data-ttu-id="9c2b0-115">为支持多个输入的自定义数据流组件实现更好的内存管理的第一步是将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 属性的值设置为 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 中的 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-115">The first step in implementing better memory management for a custom data flow component that supports multiple inputs is to set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="9c2b0-116">在 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 的值为 `true` 时，数据流引擎将调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法；并且在有多个输入时，还在运行时调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-116">When the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> is `true`, the data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method and, when there are more than two inputs, also calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method at run time.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9c2b0-117">示例</span><span class="sxs-lookup"><span data-stu-id="9c2b0-117">Example</span></span>  
 <span data-ttu-id="9c2b0-118">在下面的示例中，<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 的实现方式将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 的值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-118">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> sets the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> to `true`.</span></span>  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a><span data-ttu-id="9c2b0-119">实现 IsInputReady 方法</span><span class="sxs-lookup"><span data-stu-id="9c2b0-119">Implementing the IsInputReady Method</span></span>  
 <span data-ttu-id="9c2b0-120">在您在 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 对象中将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 属性的值设置为 `true` 时，还必须提供 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法的实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-120">When you set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> object, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c2b0-121">您的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法的实现方式不应在基类中调用这些实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-121">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="9c2b0-122">基类中此方法的默认实现方式只是引发 `NotImplementedException`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-122">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="9c2b0-123">实现此方法时，为该组件的每个输入都在布尔 canProcess  数组中设置元素的状态。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-123">When you implement this method, you set the status of an element in the Boolean *canProcess* array for each of the component's inputs.</span></span> <span data-ttu-id="9c2b0-124"> (在*inputIDs*数组中由其 ID 值标识输入。 ) 将*canProcess*数组中元素的值设置为 `true` 用于输入时，数据流引擎将调用该组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法，并为指定的输入提供更多数据。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-124">(The inputs are identified by their ID values in the *inputIDs* array.) When you set the value of an element in the *canProcess* array to `true` for an input, the data flow engine calls the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method and provides more data for the specified input.</span></span>  
  
 <span data-ttu-id="9c2b0-125">当更多的上游数据可用时，至少一个输入的*canProcess*数组元素的值必须始终为 `true` ，否则处理将停止。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-125">While more upstream data is available, the value of the *canProcess* array element for at least one input must always be `true`, or processing stops.</span></span>  
  
 <span data-ttu-id="9c2b0-126">数据流引擎将在发送每个数据缓冲区前调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法，以便确定哪些输入正在等待接收更多数据。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-126">The data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method before sending each buffer of data to determine which inputs are waiting to receive more data.</span></span> <span data-ttu-id="9c2b0-127">在返回值指示某个输入被阻塞时，数据流引擎暂时为该输入缓存附加的数据缓冲区，而不是将它们发送到该组件。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-127">When the return value indicates that an input is blocked, the data flow engine temporarily caches additional buffers of data for that input instead of sending them to the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c2b0-128">您不必在自己的代码中调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-128">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="9c2b0-129">数据流引擎调用这些方法以及您覆盖的 `PipelineComponent` 类的其他方法（在数据流引擎运行您的组件时）。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-129">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9c2b0-130">示例</span><span class="sxs-lookup"><span data-stu-id="9c2b0-130">Example</span></span>  
 <span data-ttu-id="9c2b0-131">在下面的示例中，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法的实现方式指示在以下条件成立时某个输入正在等待接收更多数据：</span><span class="sxs-lookup"><span data-stu-id="9c2b0-131">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that an input is waiting to receive more data when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="9c2b0-132">更多的上游数据可用于该输入 (`!inputEOR`)。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-132">More upstream data is available for the input (`!inputEOR`).</span></span>  
  
-   <span data-ttu-id="9c2b0-133">在已接收该组件的缓冲区中，对于该输入该组件当前不具有可供处理的数据 (`inputBuffers[inputIndex].CurrentRow() == null`)。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-133">The component does not currently have data available to process for the input in the buffers that the component has already received (`inputBuffers[inputIndex].CurrentRow() == null`).</span></span>  
  
 <span data-ttu-id="9c2b0-134">如果某个输入正在等待接收更多数据，则数据流组件通过将设置为 `true` 与该输入相对应的*canProcess*数组中的元素的值来指示这一点。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-134">If an input is waiting to receive more data, the data flow component indicates this by setting to `true` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
 <span data-ttu-id="9c2b0-135">相反，在该组件对于该输入仍具有可供处理的数据时，该示例将挂起对该输入的处理。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-135">Conversely, when the component still has data available to process for the input, the example suspends the processing of the input.</span></span> <span data-ttu-id="9c2b0-136">该示例通过将设置为 `false` 与该输入相对应的*canProcess*数组中的元素的值来实现此目标。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-136">The example does this by setting to `false` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 <span data-ttu-id="9c2b0-137">前面的示例使用布尔型 `inputEOR` 数组指示是否有更多的上游数据可用于每个输入。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-137">The preceding example uses the Boolean `inputEOR` array to indicate whether more upstream data is available for each input.</span></span> <span data-ttu-id="9c2b0-138">该数组名称中的 `EOR` 表示“行集结束”，并且引用数据流缓冲区的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-138">`EOR` in the name of the array represents "end of rowset" and refers to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property of data flow buffers.</span></span> <span data-ttu-id="9c2b0-139">在此处未包括的示例部分中，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法为它接收的每个数据缓冲区检查 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-139">In a portion of the example that is not included here, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method checks the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property for each buffer of data that it receives.</span></span> <span data-ttu-id="9c2b0-140">在 `true` 的值指示没有更多的上游数据可用于某个输入时，该示例将针对该输入将 `inputEOR` 数组元素的值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-140">When a value of `true` indicates that there is no more upstream data available for an input, the example sets the value of the `inputEOR` array element for that input to `true`.</span></span> <span data-ttu-id="9c2b0-141"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> *canProcess* `false` 当 `inputEOR` 数组元素的值指示没有更多的上游数据可用于输入时，此方法的示例会将 canProcess 数组中相应元素的值设置为。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-141">This example of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method sets the value of the corresponding element in the *canProcess* array to `false` for an input when the value of the `inputEOR` array element indicates that there is no more upstream data available for the input.</span></span>  
  
## <a name="implementing-the-getdependentinputs-method"></a><span data-ttu-id="9c2b0-142">实现 GetDependentInputs 方法</span><span class="sxs-lookup"><span data-stu-id="9c2b0-142">Implementing the GetDependentInputs Method</span></span>  
 <span data-ttu-id="9c2b0-143">在您的自定义数据流组件支持多个输入时，您还必须为 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法提供实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-143">When your custom data flow component supports more than two inputs, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c2b0-144">您的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法的实现方式不应在基类中调用这些实现方式。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-144">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="9c2b0-145">基类中此方法的默认实现方式只是引发 `NotImplementedException`。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-145">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="9c2b0-146">在用户将多个输入附加到组件时，数据流引擎仅调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-146">The data flow engine only calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method when the user attaches more than two inputs to the component.</span></span> <span data-ttu-id="9c2b0-147">如果组件仅具有两个输入，并且 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法指示一个输入被阻塞 (*canProcess*  =  `false`) ，则数据流引擎将知道另一个输入正在等待接收更多数据。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-147">When a component has only two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked (*canProcess* = `false`), the data flow engine knows that the other input is waiting to receive more data.</span></span> <span data-ttu-id="9c2b0-148">但是，在存在多个输入，并且 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 方法指示一个输入被阻塞时，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 中的附加代码标识哪些输入正在等待接收更多数据。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-148">However, when there are more than two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked, the additional code in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> identifies which inputs are waiting to receive more data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c2b0-149">您不必在自己的代码中调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-149">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="9c2b0-150">数据流引擎调用这些方法以及您覆盖的 `PipelineComponent` 类的其他方法（在数据流引擎运行您的组件时）。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-150">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9c2b0-151">示例</span><span class="sxs-lookup"><span data-stu-id="9c2b0-151">Example</span></span>  
 <span data-ttu-id="9c2b0-152">对于被阻塞的特定输入，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法的以下实现方式返回正在等待接收更多数据、并因此阻塞指定输入的输入集合。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-152">For a specific input that is blocked, the following implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method returns a collection of the inputs that are waiting to receive more data, and are therefore blocking the specified input.</span></span> <span data-ttu-id="9c2b0-153">该组件通过检查在已接收组件的缓冲区中是否存在当前没有可供处理的数据的输入（但并非已阻塞的输入）(`inputBuffers[i].CurrentRow() == null`)，标识正在阻塞的输入 。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-153">The component identifies the blocking inputs by checking for inputs other than the blocked input that do not currently have data available to process in the buffers that the component has already received (`inputBuffers[i].CurrentRow() == null`).</span></span> <span data-ttu-id="9c2b0-154">然后，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 方法将正在阻塞的输入的集合以输入 ID 的集合的形式返回。</span><span class="sxs-lookup"><span data-stu-id="9c2b0-154">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method then returns the collection of blocking inputs as a collection of input IDs.</span></span>  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  
