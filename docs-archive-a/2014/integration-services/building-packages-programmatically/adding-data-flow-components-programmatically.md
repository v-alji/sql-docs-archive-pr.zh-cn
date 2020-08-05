---
title: 以编程方式添加数据流组件 | Microsoft Docs
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: c06065cf-43e5-4b6b-9824-7309d7f5e35e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 807e758e42b738c4b0bf64b1d6f48bc29649ae6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580845"
---
# <a name="adding-data-flow-components-programmatically"></a><span data-ttu-id="f225a-102">以编程方式添加数据流组件</span><span class="sxs-lookup"><span data-stu-id="f225a-102">Adding Data Flow Components Programmatically</span></span>
  <span data-ttu-id="f225a-103">若要生成数据流，则可以先添加组件。</span><span class="sxs-lookup"><span data-stu-id="f225a-103">When you build a data flow, you start by adding components.</span></span> <span data-ttu-id="f225a-104">然后配置这些组件并将它们连接在一起，以便在运行时建立数据流。</span><span class="sxs-lookup"><span data-stu-id="f225a-104">Then you configure those components and connect them together to establish the flow of data at run time.</span></span> <span data-ttu-id="f225a-105">本节将介绍如何向数据流任务添加组件、如何创建组件的设计时实例以及配置该组件。</span><span class="sxs-lookup"><span data-stu-id="f225a-105">This section describes adding a component to the data flow task, creating the design-time instance of the component, and then configuring the component.</span></span> <span data-ttu-id="f225a-106">有关如何连接组件的详细信息，请参阅[以编程方式连接数据流组件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="f225a-106">For information about how to connect components, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-component"></a><span data-ttu-id="f225a-107">添加组件</span><span class="sxs-lookup"><span data-stu-id="f225a-107">Adding a Component</span></span>  
 <span data-ttu-id="f225a-108">对 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> 集合调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> 方法可创建新组件并将其添加到数据流任务。</span><span class="sxs-lookup"><span data-stu-id="f225a-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> collection to create a new component and add it to the data flow task.</span></span> <span data-ttu-id="f225a-109">此方法将返回组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口。</span><span class="sxs-lookup"><span data-stu-id="f225a-109">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component.</span></span> <span data-ttu-id="f225a-110">但是，此时 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 不包含特定于任一组件的信息。</span><span class="sxs-lookup"><span data-stu-id="f225a-110">However, at this point, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> does not contain information specific to any one component.</span></span> <span data-ttu-id="f225a-111">设置 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 属性可标识组件的类型。</span><span class="sxs-lookup"><span data-stu-id="f225a-111">Set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property to identify the type of component.</span></span> <span data-ttu-id="f225a-112">数据流任务将使用此属性的值在运行时创建组件的实例。</span><span class="sxs-lookup"><span data-stu-id="f225a-112">The data flow task uses the value of this property to create an instance of the component at run time.</span></span>  
  
 <span data-ttu-id="f225a-113">在 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 属性中指定的值可为 CLSID、PROGID 或组件的 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f225a-113">The value specified in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property can be the CLSID, PROGID, or <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property of the component.</span></span> <span data-ttu-id="f225a-114">CLSID 通常作为组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 属性值显示在“属性”窗口中。</span><span class="sxs-lookup"><span data-stu-id="f225a-114">The CLSID is normally displayed in the Properties window as the value of the component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="f225a-115">有关获取可用组件的此属性和其他属性的信息，请参阅[以编程方式查找数据流组件](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="f225a-115">For information about obtaining this property and other properties of available components, see [Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-managed-component"></a><span data-ttu-id="f225a-116">添加托管组件</span><span class="sxs-lookup"><span data-stu-id="f225a-116">Adding a Managed Component</span></span>  
 <span data-ttu-id="f225a-117">您不能使用 CLSID 或 PROGID 向数据流添加一个托管数据流组件，因为这些值指向包装而不是组件本身。</span><span class="sxs-lookup"><span data-stu-id="f225a-117">You cannot use the CLSID or PROGID to add one the managed data flow components to the data flow, because these values point to a wrapper and not to the component itself.</span></span> <span data-ttu-id="f225a-118">您可以改用 `CreationName` 属性或 `AssemblyQualifiedName` 属性，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f225a-118">Instead you can use the `CreationName` property or the `AssemblyQualifiedName` property as shown in the following sample.</span></span>  
  
 <span data-ttu-id="f225a-119">若要使用 `AssemblyQualifiedName` 属性，则必须在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 项目中添加对包含托管组件的程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="f225a-119">If you intend to use the `AssemblyQualifiedName` property, then you must add a reference in your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] project to the assembly that contains the managed component.</span></span> <span data-ttu-id="f225a-120">这些程序集没有在“添加引用”  对话框的 .NET 选项卡上列出。</span><span class="sxs-lookup"><span data-stu-id="f225a-120">These assemblies are not listed on the .NET tab of the **Add Reference** dialog box.</span></span> <span data-ttu-id="f225a-121">通常需要浏览至 C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents  文件夹查找程序集。</span><span class="sxs-lookup"><span data-stu-id="f225a-121">Normally you must browse to locate the assembly in the **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** folder.</span></span>  
  
 <span data-ttu-id="f225a-122">内置托管数据流组件包括：</span><span class="sxs-lookup"><span data-stu-id="f225a-122">The built-in managed data flow components include:</span></span>  
  
-   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="f225a-123">源</span><span class="sxs-lookup"><span data-stu-id="f225a-123">Source</span></span>  
  
-   <span data-ttu-id="f225a-124">XML 源</span><span class="sxs-lookup"><span data-stu-id="f225a-124">XML Source</span></span>  
  
-   <span data-ttu-id="f225a-125">DataReader 目标</span><span class="sxs-lookup"><span data-stu-id="f225a-125">DataReader Destination</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="f225a-126">Compact 目标</span><span class="sxs-lookup"><span data-stu-id="f225a-126">Compact Destination</span></span>  
  
-   <span data-ttu-id="f225a-127">脚本组件</span><span class="sxs-lookup"><span data-stu-id="f225a-127">Script Component</span></span>  
  
 <span data-ttu-id="f225a-128">下面的代码示例演示将托管组件添加到数据流的两种方法：</span><span class="sxs-lookup"><span data-stu-id="f225a-128">The following code sample shows both ways of adding a managed component to the data flow:</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Microsoft.SqlServer.Dts.Runtime.Package package = new Microsoft.SqlServer.Dts.Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Microsoft.SqlServer.Dts.Runtime.TaskHost thMainPipe = (Microsoft.SqlServer.Dts.Runtime.TaskHost)e;  
      MainPipe dataFlowTask = (MainPipe)thMainPipe.InnerObject;  
  
      // The Application object will be used to obtain the CreationName  
      //  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
      Application app = new Application();  
  
      // Add a first ADO NET source to the data flow.  
      //  The CreationName property requires an Application instance.  
      IDTSComponentMetaData100 component1 = dataFlowTask.ComponentMetaDataCollection.New();  
      component1.Name = "DataReader Source";  
      component1.ComponentClassID = app.PipelineComponentInfos["DataReader Source"].CreationName;  
  
      // Add a second ADO NET source to the data flow.  
      //  The AssemblyQualifiedName property requires a reference to the assembly.  
      IDTSComponentMetaData100 component2 = dataFlowTask.ComponentMetaDataCollection.New();  
      component2.Name = "DataReader Source";  
      component2.ComponentClassID = typeof(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName;  
    }  
  }  
}  
  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' The Application object will be used to obtain the CreationName  
    '  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
    Dim app As New Application()  
  
    ' Add a first ADO NET source to the data flow.  
    '  The CreationName property requires an Application instance.  
    Dim component1 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component1.Name = "DataReader Source"  
    component1.ComponentClassID = app.PipelineComponentInfos("DataReader Source").CreationName  
  
    ' Add a second ADO NET source to the data flow.  
    '  The AssemblyQualifiedName property requires a reference to the assembly.  
    Dim component2 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component2.Name = "DataReader Source"  
    component2.ComponentClassID = _  
      GetType(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName  
  
  End Sub  
  
End Module  
```  
  
## <a name="creating-the-design-time-instance-of-the-component"></a><span data-ttu-id="f225a-129">创建组件的设计时实例</span><span class="sxs-lookup"><span data-stu-id="f225a-129">Creating the Design-time Instance of the Component</span></span>  
 <span data-ttu-id="f225a-130">调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> 方法可以创建由 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 属性标识的组件的设计时实例。</span><span class="sxs-lookup"><span data-stu-id="f225a-130">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method to create the design time instance of the component identified by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="f225a-131">此方法将返回 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 对象，它是 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 接口的托管包装。</span><span class="sxs-lookup"><span data-stu-id="f225a-131">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> object, which is the managed wrapper for the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="f225a-132">应尽可能使用设计时实例的方法而不是通过直接修改组件元数据来修改组件。</span><span class="sxs-lookup"><span data-stu-id="f225a-132">Whenever possible, you should modify a component by using the methods of the design-time instance instead of by modifying the component metadata directly.</span></span> <span data-ttu-id="f225a-133">尽管元数据中存在必须直接设置的项（如连接），但是通常不建议直接修改元数据，因为这样将跳过组件监视和验证更改的功能。</span><span class="sxs-lookup"><span data-stu-id="f225a-133">Although there are items in the metadata that you must set directly, such as connections, generally it is inadvisable to modify the metadata directly because you bypass the ability of the component to monitor and validate changes.</span></span>  
  
## <a name="assigning-connections"></a><span data-ttu-id="f225a-134">分配连接</span><span class="sxs-lookup"><span data-stu-id="f225a-134">Assigning Connections</span></span>  
 <span data-ttu-id="f225a-135">某些组件（如 OLE DB 源组件）需要连接到外部数据并使用包中的现有 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象来实现此分配目的。</span><span class="sxs-lookup"><span data-stu-id="f225a-135">Some components, such as the OLE DB Source component, require a connection to external data and use an existing <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object in the package for this purpose.</span></span> <span data-ttu-id="f225a-136"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 属性指示组件所需的运行时 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象的数量。</span><span class="sxs-lookup"><span data-stu-id="f225a-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection indicates the number of run-time <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects required by the component.</span></span> <span data-ttu-id="f225a-137">如果该计数大于零，则组件需要连接。</span><span class="sxs-lookup"><span data-stu-id="f225a-137">If the count is greater than zero, the component requires a connection.</span></span> <span data-ttu-id="f225a-138">可通过指定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> 中的第一个连接的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 属性，将包中的连接管理器分配给组件。</span><span class="sxs-lookup"><span data-stu-id="f225a-138">Assign a connection manager from the package to the component by specifying the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> properties of the first connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span> <span data-ttu-id="f225a-139">请注意，运行时连接集合中的连接管理器的名称必须与从包中引用的连接管理器的名称匹配。</span><span class="sxs-lookup"><span data-stu-id="f225a-139">Note that the name of the connection manager in the run-time connection collection must match the name of the connection managerreferenced from the package.</span></span>  
  
## <a name="setting-the-values-of-custom-properties"></a><span data-ttu-id="f225a-140">设置自定义属性的值</span><span class="sxs-lookup"><span data-stu-id="f225a-140">Setting the Values of Custom Properties</span></span>  
 <span data-ttu-id="f225a-141">创建组件的设计时实例后，可调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f225a-141">After creating the design-time instance of the component, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="f225a-142">此方法类似于构造函数，因为该方法通过创建其自定义属性及其输入和输出对象来初始化新创建的组件。</span><span class="sxs-lookup"><span data-stu-id="f225a-142">This method is similar to a constructor because it initializes a newly created component by creating its custom properties and its input and output objects.</span></span> <span data-ttu-id="f225a-143">请不要对组件多次调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A>，因为该组件可能会对自己进行重置，从而丢失之前对其元数据所做的所有修改。</span><span class="sxs-lookup"><span data-stu-id="f225a-143">Do not call <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> more than one time on a component, because the component may reset itself and lose any modifications previously made to its metadata.</span></span>  
  
 <span data-ttu-id="f225a-144">组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> 包含特定于该组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="f225a-144">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> of the component contains a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> objects specific to the component.</span></span> <span data-ttu-id="f225a-145">与对象属性在对象中始终可见的其他编程模型不同，组件在您调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 方法时只填充其自定义属性集合。</span><span class="sxs-lookup"><span data-stu-id="f225a-145">Unlike other programming models, where the properties of an object are always visible on the object, components only populate their custom property collections when you call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="f225a-146">调用该方法后，使用组件的设计时实例的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> 方法可将值分配给组件的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="f225a-146">After you call method, use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> method of the design-time instance of the component to assign values to its custom properties.</span></span> <span data-ttu-id="f225a-147">此方法接受用于标识自定义属性并提供其新值的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="f225a-147">This method accepts a name/value pair that identifies the custom property and provides its new value.</span></span>  
  
## <a name="initializing-output-columns"></a><span data-ttu-id="f225a-148">初始化输出列</span><span class="sxs-lookup"><span data-stu-id="f225a-148">Initializing Output Columns</span></span>  
 <span data-ttu-id="f225a-149">向任务添加组件并对该组件进行配置后，将初始化对象的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 中的列的集合。</span><span class="sxs-lookup"><span data-stu-id="f225a-149">After you add a component to the task and configure it, initialize the collection of columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the object.</span></span> <span data-ttu-id="f225a-150">此步骤特别适用于源组件，但是可能不会初始化转换和目标组件的列，因为它们通常依赖于从上游组件接收到的列。</span><span class="sxs-lookup"><span data-stu-id="f225a-150">This step is especially relevant for source components, but may not initialize the columns for transformation and destination components because they generally depend on the columns that they receive from upstream components.</span></span>  
  
 <span data-ttu-id="f225a-151">调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> 方法可初始化源组件的输出中的列。</span><span class="sxs-lookup"><span data-stu-id="f225a-151">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> method to initialize the columns in the outputs of a source component.</span></span> <span data-ttu-id="f225a-152">由于组件不会自动连接到外部数据源，所以应先调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> 方法，然后再调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A>，以提供对其外部数据源的组件访问以及填充组件列元数据的功能。</span><span class="sxs-lookup"><span data-stu-id="f225a-152">Because components do not automatically connect to external data sources, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> method before calling <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> to provide the component access to its external data source and the ability to populate its column metadata.</span></span> <span data-ttu-id="f225a-153">最后，调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> 方法以释放连接。</span><span class="sxs-lookup"><span data-stu-id="f225a-153">Finally, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> method to release the connection.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f225a-154">下一步</span><span class="sxs-lookup"><span data-stu-id="f225a-154">Next Step</span></span>  
 <span data-ttu-id="f225a-155">添加并配置组件之后，下一步是创建组件之间的路径，这将在[在两个组件之间创建路径](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)主题中讨论。</span><span class="sxs-lookup"><span data-stu-id="f225a-155">After adding and configuring the component, the next step is to create paths between components, which is discussed in the topic, [Creating a Path Between Two Components](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="f225a-156">示例</span><span class="sxs-lookup"><span data-stu-id="f225a-156">Sample</span></span>  
 <span data-ttu-id="f225a-157">下面的代码示例向数据流任务添加 OLE DB 源组件、创建组件的设计时实例并配置组件的属性。</span><span class="sxs-lookup"><span data-stu-id="f225a-157">The following code sample adds the OLE DB Source component to a data flow task, creates a design-time instance of the component, and configures the component's properties.</span></span> <span data-ttu-id="f225a-158">此示例需要对 Microsoft.SqlServer.DTSRuntimeWrap 程序集的附加引用。</span><span class="sxs-lookup"><span data-stu-id="f225a-158">This example requires an additional reference to the assembly Microsoft.SqlServer.DTSRuntimeWrap.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Runtime.Package package = new Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Runtime.TaskHost thMainPipe = e as Runtime.TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Add an OLEDB connection manager to the package.  
      ConnectionManager cm = package.Connections.Add("OLEDB");  
      cm.Name = "OLEDB ConnectionManager";  
      cm.ConnectionString = "Data Source=(local);" +   
        "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" +   
        "Integrated Security=SSPI;"  
  
      // Add an OLE DB source to the data flow.  
      IDTSComponentMetaData100 component =   
        dataFlowTask.ComponentMetaDataCollection.New();  
      component.Name = "OLEDBSource";  
      component.ComponentClassID = "DTSAdapter.OleDbSource.1";  
      // You can also use the CLSID of the component instead of the PROGID.  
      //component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
      // Get the design time instance of the component.  
      CManagedComponentWrapper instance = component.Instantiate();  
  
      // Initialize the component  
      instance.ProvideComponentProperties();  
  
      // Specify the connection manager.  
      if (component.RuntimeConnectionCollection.Count > 0)  
      {  
        component.RuntimeConnectionCollection[0].ConnectionManager =   
          DtsConvert.GetExtendedInterface(package.Connections[0]);  
        component.RuntimeConnectionCollection[0].ConnectionManagerID =   
          package.Connections[0].ID;      }  
  
      // Set the custom properties.  
      instance.SetComponentProperty("AccessMode", 2);  
      instance.SetComponentProperty("SqlCommand",   
        "Select * from Production.Product");  
  
      // Reinitialize the metadata.  
      instance.AcquireConnections(null);  
      instance.ReinitializeMetaData();  
      instance.ReleaseConnections();  
  
      // Add other components to the data flow and connect them.  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Add an OLEDB connection manager to the package.  
    Dim cm As ConnectionManager = package.Connections.Add("OLEDB")  
    cm.Name = "OLEDB ConnectionManager"  
    cm.ConnectionString = "Data Source=(local);" & _  
      "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;"  
  
    ' Add an OLE DB source to the data flow.  
    Dim component As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component.Name = "OLEDBSource"  
    component.ComponentClassID = "DTSAdapter.OleDbSource.1"  
    ' You can also use the CLSID of the component instead of the PROGID.  
    'component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
    ' Get the design time instance of the component.  
    Dim instance As CManagedComponentWrapper = component.Instantiate()  
  
    ' Initialize the component.  
    instance.ProvideComponentProperties()  
  
    ' Specify the connection manager.  
    If component.RuntimeConnectionCollection.Count > 0 Then  
      component.RuntimeConnectionCollection(0).ConnectionManager = _  
        DtsConvert.GetExtendedInterface(package.Connections(0))  
      component.RuntimeConnectionCollection(0).ConnectionManagerID = _  
        package.Connections(0).ID  
    End If  
  
    ' Set the custom properties.  
    instance.SetComponentProperty("AccessMode", 2)  
    instance.SetComponentProperty("SqlCommand", _  
      "Select * from Production.Product")  
  
    ' Reinitialize the metadata.  
    instance.AcquireConnections(vbNull)  
    instance.ReinitializeMetaData()  
    instance.ReleaseConnections()  
  
    ' Add other components to the data flow and connect them.  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="f225a-159">外部资源</span><span class="sxs-lookup"><span data-stu-id="f225a-159">External Resources</span></span>  
 <span data-ttu-id="f225a-160">blogs.msdn.com 上的博客文章 [EzAPI - 为 SQL Server 2012 更新](https://go.microsoft.com/fwlink/?LinkId=243223)。</span><span class="sxs-lookup"><span data-stu-id="f225a-160">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="f225a-161">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f225a-161">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f225a-162">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="f225a-162">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f225a-163">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="f225a-163">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f225a-164">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="f225a-164">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f225a-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f225a-165">See Also</span></span>  
 [<span data-ttu-id="f225a-166">以编程方式连接数据流组件</span><span class="sxs-lookup"><span data-stu-id="f225a-166">Connecting Data Flow Components Programmatically</span></span>](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
  
  
