---
title: 在数据流组件中引发和定义事件 | Microsoft Docs
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
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688044"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a><span data-ttu-id="b9e6d-102">在数据流组件中引发和定义事件</span><span class="sxs-lookup"><span data-stu-id="b9e6d-102">Raising and Defining Events in a Data Flow Component</span></span>
  <span data-ttu-id="b9e6d-103">组件开发人员可通过调用对 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 属性公开的方法，引发在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 接口中定义的一部分事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-103">Component developers can raise a subset of the events defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface by calling the methods exposed on the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="b9e6d-104">还可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 集合定义自定义事件，并使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法在执行过程中引发这些事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-104">You can also define custom events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection, and raise them during execution by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="b9e6d-105">本节介绍如何创建和引发事件，并提供在设计时应于何时引发事件的指南。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-105">This section describes how to create and raise an event, and provides guidelines on when you should raise events at design time.</span></span>

## <a name="raising-events"></a><span data-ttu-id="b9e6d-106">引发事件</span><span class="sxs-lookup"><span data-stu-id="b9e6d-106">Raising Events</span></span>
 <span data-ttu-id="b9e6d-107">组件使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口的 Fire\<X> 方法引发事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-107">Components raise events by using the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="b9e6d-108">您可以在组件设计和执行的过程中引发事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-108">You can raise events during component design and execution.</span></span> <span data-ttu-id="b9e6d-109">通常，在组件设计过程中，验证期间会调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-109">Typically, during component design, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> methods are called during validation.</span></span> <span data-ttu-id="b9e6d-110">这些事件在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的“错误列表”窗格中显示消息，并在某个组件配置不正确时，向该组件的用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-110">These events display messages in the **Error List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and provide feedback to users of the component when a component is incorrectly configured.</span></span>

 <span data-ttu-id="b9e6d-111">组件也可以在执行过程中的任一点引发事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-111">Components can also raise events at any point during execution.</span></span> <span data-ttu-id="b9e6d-112">组件开发人员可通过事件在组件执行时向该组件的用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-112">Events allow component developers to provide feedback to users of the component as it executes.</span></span> <span data-ttu-id="b9e6d-113">在执行过程中调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 方法可能导致包失败。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-113">Calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> method during execution is likely to fail the package.</span></span>

## <a name="defining-and-raising-custom-events"></a><span data-ttu-id="b9e6d-114">定义和引发自定义事件</span><span class="sxs-lookup"><span data-stu-id="b9e6d-114">Defining and Raising Custom Events</span></span>

### <a name="defining-a-custom-event"></a><span data-ttu-id="b9e6d-115">定义自定义事件</span><span class="sxs-lookup"><span data-stu-id="b9e6d-115">Defining a Custom Event</span></span>
 <span data-ttu-id="b9e6d-116">调用 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 方法可创建自定义事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-116">Custom events are created by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection.</span></span> <span data-ttu-id="b9e6d-117">此集合由数据流任务设置，并作为属性通过 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基类提供给组件开发人员。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-117">This collection is set by the data flow task and provided as a property to the component developer through the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="b9e6d-118">此类包含调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法的过程中由数据流任务定义的自定义事件和组件定义的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-118">This class contains custom events defined by the data flow task and custom events defined by the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method.</span></span>

 <span data-ttu-id="b9e6d-119">组件的自定义事件不会持久保留在包 XML 中。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-119">The custom events of a component are not persisted in the package XML.</span></span> <span data-ttu-id="b9e6d-120">因此，在设计和执行过程中都调用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法，以允许组件定义所引发的事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-120">Therefore, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method is called during both design and execution to allow the component to define the events it raises.</span></span>

 <span data-ttu-id="b9e6d-121"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 方法的 allowEventHandlers 参数指定组件是否允许为事件创建 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 对象。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-121">The *allowEventHandlers* parameter of the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method specifies whether the component allows <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects to be created for the event.</span></span> <span data-ttu-id="b9e6d-122">请注意，<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> 是同步的。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-122">Note that <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> are synchronous.</span></span> <span data-ttu-id="b9e6d-123">因此，直到附加到自定义事件的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 执行完毕后，组件才会继续执行。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-123">Therefore the component does not resume execution until an <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> attached to the custom event has finished executing.</span></span> <span data-ttu-id="b9e6d-124">如果*allowEventHandlers*参数为 `true` ，则通过由 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行时自动创建和填充的变量，事件的每个参数都将自动提供给任何对象使用。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-124">If the *allowEventHandlers* parameter is `true`, each parameter of the event is automatically made available to any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects through variables that are created and populated automatically by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

### <a name="raising-a-custom-event"></a><span data-ttu-id="b9e6d-125">引发自定义事件</span><span class="sxs-lookup"><span data-stu-id="b9e6d-125">Raising a Custom Event</span></span>
 <span data-ttu-id="b9e6d-126">通过调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法并提供事件的名称、文本和参数，组件可引发自定义事件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-126">Components raise custom events by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method, and providing the name, text, and parameters of the event.</span></span> <span data-ttu-id="b9e6d-127">如果*allowEventHandlers*参数为 `true` ，则 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 运行时引擎将执行为自定义事件创建的任何。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-127">If the *allowEventHandlers* parameter is `true`, any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> that are created for the custom event are executed by the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] run-time engine.</span></span>

### <a name="custom-event-sample"></a><span data-ttu-id="b9e6d-128">自定义事件示例</span><span class="sxs-lookup"><span data-stu-id="b9e6d-128">Custom Event Sample</span></span>
 <span data-ttu-id="b9e6d-129">下面的代码示例演示了在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法中定义自定义事件，然后通过调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法在运行时引发该事件的组件。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-129">The following code example shows a component that defines a custom event during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method, and then raises the event at run time by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span>

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

<span data-ttu-id="b9e6d-130">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b9e6d-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b9e6d-131">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="b9e6d-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b9e6d-132">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="b9e6d-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b9e6d-133">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="b9e6d-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e6d-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9e6d-134">See Also</span></span>
 <span data-ttu-id="b9e6d-135">[Integration Services &#40;SSIS&#41; 事件处理程序](../../integration-services-ssis-event-handlers.md)[将事件处理程序添加到包](../../add-an-event-handler-to-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="b9e6d-135">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) [Add an Event Handler to a Package](../../add-an-event-handler-to-a-package.md)</span></span>


