---
title: 为数据流组件开发用户界面 | Microsoft Docs
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
- data flow components [Integration Services], custom editors
- user interfaces [Integration Services]
- custom data flow components [Integration Services], custom editors
- custom component editors [Integration Services]
- IDtsComponentUI interface
- UITypeName property
- custom user interface [Integration Services], custom data flow component
- editors [Integration Services]
ms.assetid: 10b829a1-609b-42e3-9070-cfe5a2bb698c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f97f21ad14a5fa67fb49192931a0cb46d0cb41da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688067"
---
# <a name="developing-a-user-interface-for-a-data-flow-component"></a><span data-ttu-id="d9ecd-102">为数据流组件开发用户界面</span><span class="sxs-lookup"><span data-stu-id="d9ecd-102">Developing a User Interface for a Data Flow Component</span></span>
  <span data-ttu-id="d9ecd-103">组件开发人员可以为组件提供自定义用户界面，编辑该组件时，此界面会显示在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-103">Component developers can provide a custom user interface for a component, which is displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] when the component is edited.</span></span> <span data-ttu-id="d9ecd-104">通过实现自定义用户界面，您可以在组件添加到数据流任务中或从数据流任务中删除以及请求该组件的帮助时获得通知。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-104">Implementing a custom user interface provides you with notification when the component is added to or deleted from a data flow task, and when help is requested for the component.</span></span>

 <span data-ttu-id="d9ecd-105">如果没有为您的组件提供自定义用户界面，用户仍然可以配置该组件及其自定义属性，方法是使用“高级编辑器”。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-105">If you do not provide a custom user interface for your component, users can still configure the component and its custom properties by using the Advanced Editor.</span></span> <span data-ttu-id="d9ecd-106">您可以根据需要使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 属性确保高级编辑器允许用户适当地编辑自定义属性值。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-106">You can ensure that the Advanced Editor allows users to edit custom property values appropriately by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> properties of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> when appropriate.</span></span> <span data-ttu-id="d9ecd-107">有关详细信息，请参阅[数据流组件的设计时方法](design-time-methods-of-a-data-flow-component.md)中的“创建自定义属性”。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-107">For more information, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>

## <a name="setting-the-uitypename-property"></a><span data-ttu-id="d9ecd-108">设置 UITypeName 属性</span><span class="sxs-lookup"><span data-stu-id="d9ecd-108">Setting the UITypeName Property</span></span>
 <span data-ttu-id="d9ecd-109">若要提供自定义用户界面，开发人员必须将 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 属性设置为实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 接口的类的名称。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-109">To provide a custom user interface, the developer must set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> to the name of a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="d9ecd-110">组件设置此属性时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 会在该组件在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中编辑时加载并调用自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-110">When this property is set by the component, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] loads and calls the custom user interface when the component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="d9ecd-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 属性是以逗号分隔的用于标识类型的完全限定名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property is a comma-delimited string that identifies the fully qualified name of the type.</span></span> <span data-ttu-id="d9ecd-112">下面的列表按顺序显示标识类型的元素：</span><span class="sxs-lookup"><span data-stu-id="d9ecd-112">The following list shows, in order, the elements that identify the type:</span></span>

-   <span data-ttu-id="d9ecd-113">类型名称</span><span class="sxs-lookup"><span data-stu-id="d9ecd-113">Type name</span></span>

-   <span data-ttu-id="d9ecd-114">程序集名称</span><span class="sxs-lookup"><span data-stu-id="d9ecd-114">Assembly name</span></span>

-   <span data-ttu-id="d9ecd-115">文件版本</span><span class="sxs-lookup"><span data-stu-id="d9ecd-115">File version</span></span>

-   <span data-ttu-id="d9ecd-116">环境</span><span class="sxs-lookup"><span data-stu-id="d9ecd-116">Culture</span></span>

-   <span data-ttu-id="d9ecd-117">公钥标记</span><span class="sxs-lookup"><span data-stu-id="d9ecd-117">Public key token</span></span>

 <span data-ttu-id="d9ecd-118">下面的代码示例演示从 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基类派生的类，并指定 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-118">The following code example shows a class that derives from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class and specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property.</span></span>

```csharp
[DtsPipelineComponent(
DisplayName="SampleComponent",
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...",
ComponentType = ComponentType.Transform)]
public class SampleComponent : PipelineComponent
{
//TODO: Implement the component here.
}
```

```vb
<DtsPipelineComponent(DisplayName="SampleComponent", _
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...", ComponentType=ComponentType.Transform)> _ 
Public Class SampleComponent 
 Inherits PipelineComponent 
End Class
```

## <a name="implementing-the-idtscomponentui-interface"></a><span data-ttu-id="d9ecd-119">实现 IDtsComponentUI 接口</span><span class="sxs-lookup"><span data-stu-id="d9ecd-119">Implementing the IDtsComponentUI Interface</span></span>
 <span data-ttu-id="d9ecd-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 接口包含在添加、删除和编辑组件时 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器调用的方法。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-120">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface contains methods that [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls when a component is added, deleted, and edited.</span></span> <span data-ttu-id="d9ecd-121">组件开发人员可以在其对这些方法的实现中提供代码来与组件的用户进行交互。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-121">Component developers can provide code in their implementation of these methods to interact with users of the component.</span></span>

 <span data-ttu-id="d9ecd-122">此类通常在独立于组件自身的程序集中实现。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-122">This class is typically implemented in an assembly separate from the component itself.</span></span> <span data-ttu-id="d9ecd-123">虽然不是必须使用单独的程序集，但是这样做可以使开发人员单独生成和部署组件及用户界面，并保持组件的二进制程序文件较小。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-123">Although use of a separate assembly is not required, this lets the developer build and deploy the component and the user interface independently of each other, and keeps the binary footprint of the component small.</span></span>

 <span data-ttu-id="d9ecd-124">通过实现自定义用户界面，当组件在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中被编辑时，组件开发人员可以对组件实施更多控制。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-124">Implementing a custom user interface gives the component developer more control over the component as it is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="d9ecd-125">例如，组件可以将代码添加到在一个组件最初添加到数据流任务时调用的 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 方法中，并显示一个用于指导用户完成组件初始配置的向导。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-125">For example, a component can add code to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> method, which is called when a component is initially added to a data flow task, and display a wizard that guides the user through the initial configuration of the component.</span></span>

 <span data-ttu-id="d9ecd-126">创建实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 接口的类后，必须添加代码以响应用户与组件的交互。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-126">After you have created a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, you must add code to respond to user interaction with the component.</span></span> <span data-ttu-id="d9ecd-127"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法提供组件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口，并在调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法之前调用。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-127">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component, and is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> methods.</span></span> <span data-ttu-id="d9ecd-128">此引用应存储在私有成员变量中，然后用于修改组件的元数据。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-128">This reference should be stored in a private member variable and used to modify the component's metadata thereafter.</span></span>

## <a name="modifying-a-component-and-persisting-changes"></a><span data-ttu-id="d9ecd-129">修改组件并使更改持久化</span><span class="sxs-lookup"><span data-stu-id="d9ecd-129">Modifying a Component and Persisting Changes</span></span>
 <span data-ttu-id="d9ecd-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口作为一个参数提供给 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-130">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface is provided as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method.</span></span> <span data-ttu-id="d9ecd-131">此引用应由用户界面代码缓存在成员变量中，然后用于修改组件以响应用户与用户界面的交互。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-131">This reference should be cached in a member variable by the user interface code, and then used to modify the component in response to user interaction with the user interface.</span></span>

 <span data-ttu-id="d9ecd-132">虽然可以通过 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 接口直接修改组件，但是最好使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 方法创建一个 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> 实例。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-132">Although you can modify the component directly through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, it is better to create an instance of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method.</span></span> <span data-ttu-id="d9ecd-133">使用该接口直接编辑组件时，将绕过组件的验证保护。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-133">When you edit the component directly by using the interface, you bypass the component's validation safeguards.</span></span> <span data-ttu-id="d9ecd-134">通过 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 使用组件的设计时实例的优点是可以确保组件可以控制对它的更改。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-134">The advantage of using the design-time instance of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> is that you ensure that the component has control over the changes made to it.</span></span>

 <span data-ttu-id="d9ecd-135"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法的返回值确定对组件的更改是持久的还是被放弃。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-135">The return value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method determines whether changes made to a component are persisted or discarded.</span></span> <span data-ttu-id="d9ecd-136">此方法返回 `false` 时，所有更改都被放弃；返回 `true` 时，将持久化对组件的更改并将包标记为需要保存。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-136">When this method returns `false`, all changes are discarded; `true` persists the changes to the component and marks the package as needing to be saved.</span></span>

### <a name="using-the-services-of-the-ssis-designer"></a><span data-ttu-id="d9ecd-137">使用 SSIS 设计器的服务</span><span class="sxs-lookup"><span data-stu-id="d9ecd-137">Using the Services of the SSIS Designer</span></span>
 <span data-ttu-id="d9ecd-138">使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法的 `IServiceProvider` 参数可以访问 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器的以下服务：</span><span class="sxs-lookup"><span data-stu-id="d9ecd-138">The `IServiceProvider` parameter of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides access to the following services of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer:</span></span>

|<span data-ttu-id="d9ecd-139">服务</span><span class="sxs-lookup"><span data-stu-id="d9ecd-139">Service</span></span>|<span data-ttu-id="d9ecd-140">说明</span><span class="sxs-lookup"><span data-stu-id="d9ecd-140">Description</span></span>|
|-------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsClipboardService>|<span data-ttu-id="d9ecd-141">用于确定组件是否是通过复制/粘贴或剪切/粘贴操作生成的。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-141">Used to determine whether the component was generated as part of a copy/paste or cut/paste operation.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionService>|<span data-ttu-id="d9ecd-142">用于访问包中的现有连接或在包中创建新连接。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-142">Used to access existing connections or to create new connections in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IErrorCollectionService>|<span data-ttu-id="d9ecd-143">用于在您需要捕获组件引发的所有错误和警告而不是只接收最后一个错误或警告时，从数据流组件中捕获事件。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-143">Used to capture events from data flow components when you need to capture all the errors and warnings raised by the component instead of receiving only the last error or warning.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsVariableService>|<span data-ttu-id="d9ecd-144">用于访问包中的现有变量或在包中创建新变量。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-144">Used to access existing variables or to create new variables in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsPipelineEnvironmentService>|<span data-ttu-id="d9ecd-145">数据流组件使用它来访问父数据流任务以及数据流中的其他组件。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-145">Used by data flow components to access the parent Data Flow task and other components in the data flow.</span></span> <span data-ttu-id="d9ecd-146">此功能可用于开发像渐变维度向导一样根据需要创建和连接其他数据流组件的组件。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-146">This feature could be used to develop a component like the Slowly Changing Dimension Wizard that creates and connects additional data flow components as needed.</span></span>|

 <span data-ttu-id="d9ecd-147">使用这些服务，组件开发人员可以访问组件所加载到的包中的对象以及在该包中创建对象。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-147">These services provide component developers the ability to access and create objects in the package in which the component is loaded.</span></span>

## <a name="sample"></a><span data-ttu-id="d9ecd-148">示例</span><span class="sxs-lookup"><span data-stu-id="d9ecd-148">Sample</span></span>
 <span data-ttu-id="d9ecd-149">下面的代码示例演示如何将实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 接口的自定义用户界面类与用作组件编辑器的 Windows 窗体相集成。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-149">The following code example shows the integration of a custom user interface class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, and a Windows form that serves as the editor for a component.</span></span>

### <a name="custom-user-interface-class"></a><span data-ttu-id="d9ecd-150">自定义用户界面类</span><span class="sxs-lookup"><span data-stu-id="d9ecd-150">Custom User Interface Class</span></span>
 <span data-ttu-id="d9ecd-151">下面的代码演示实现 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 接口的类。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-151">The following code shows the class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="d9ecd-152"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法创建组件编辑器，然后显示该窗体。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-152">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method creates the component editor and then displays the form.</span></span> <span data-ttu-id="d9ecd-153">窗体的返回值确定对组件的更改是否是持久的。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-153">The return value of the form determines whether changes to the component are persisted.</span></span>

```csharp
using System;
using System.Windows.Forms;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Pipeline.Design;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    public class SampleComponentUI : IDtsComponentUI
    {
        IDTSComponentMetaData100 md;
        IServiceProvider sp;

        public void Help(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void New(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void Delete(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Variables vars, Connections cons)
        {
            // Create and display the form for the user interface.
            SampleComponentUIForm componentEditor = new SampleComponentUIForm(cons, vars, md);

            DialogResult result  = componentEditor.ShowDialog(parentWindow);

            if (result == DialogResult.OK)
                return true;

            return false;
        }
        public void Initialize(IDTSComponentMetaData100 dtsComponentMetadata, IServiceProvider serviceProvider)
        {
            // Store the component metadata.
            this.md = dtsComponentMetadata;
        }
    }
}
```

```vb
Imports System 
Imports System.Windows.Forms 
Imports Microsoft.SqlServer.Dts.Runtime 
Imports Microsoft.SqlServer.Dts.Pipeline.Design 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Class SampleComponentUI 
 Implements IDtsComponentUI 
   Private md As IDTSComponentMetaData100 
   Private sp As IServiceProvider 

   Public Sub Help(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub New(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub Delete(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal vars As Variables, ByVal cons As Connections) As Boolean 
     ' Create and display the form for the user interface.
     Dim componentEditor As SampleComponentUIForm = New SampleComponentUIForm(cons, vars, md) 
     Dim result As DialogResult = componentEditor.ShowDialog(parentWindow) 
     If result = DialogResult.OK Then 
       Return True 
     End If 
     Return False 
   End Function 

   Public Sub Initialize(ByVal dtsComponentMetadata As IDTSComponentMetaData100, ByVal serviceProvider As IServiceProvider) 
     Me.md = dtsComponentMetadata 
   End Sub 
 End Class 

End Namespace
```

### <a name="custom-editor"></a><span data-ttu-id="d9ecd-154">自定义编辑器</span><span class="sxs-lookup"><span data-stu-id="d9ecd-154">Custom Editor</span></span>
 <span data-ttu-id="d9ecd-155">下面的代码演示在调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法的过程中显示的 Windows 窗体的实现。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-155">The following code shows the implementation of the Windows form that is shown during the call to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method.</span></span>

```csharp
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    public partial class SampleComponentUIForm : System.Windows.Forms.Form
    {
        private Connections connections;
        private Variables variables;
        private IDTSComponentMetaData100 metaData;
        private CManagedComponentWrapper designTimeInstance;
        private System.ComponentModel.IContainer components = null;

        public SampleComponentUIForm( Connections cons, Variables vars, IDTSComponentMetaData100 md)
        {
            variables = vars;
            connections = cons;
            metaData = md;
        }

        private void btnOk_Click(object sender, System.EventArgs e)
        {
            if (designTimeInstance == null)
                designTimeInstance = metaData.Instantiate();

            designTimeInstance.SetComponentProperty( "CustomProperty", txtCustomPropertyValue.Text);

            this.Close();
        }

        private void btnCancel_Click(object sender, System.EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System 
Imports System.Drawing 
Imports System.Collections 
Imports System.ComponentModel 
Imports System.Windows.Forms 
Imports System.Data 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Partial Class SampleComponentUIForm 
  Inherits System.Windows.Forms.Form 
   Private connections As Connections 
   Private variables As Variables 
   Private metaData As IDTSComponentMetaData100 
   Private designTimeInstance As CManagedComponentWrapper 
   Private components As System.ComponentModel.IContainer = Nothing 

   Public Sub New(ByVal cons As Connections, ByVal vars As Variables, ByVal md As IDTSComponentMetaData100) 
     variables = vars 
     connections = cons 
     metaData = md 
   End Sub 

   Private Sub btnOk_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     If designTimeInstance Is Nothing Then 
       designTimeInstance = metaData.Instantiate 
     End If 
     designTimeInstance.SetComponentProperty("CustomProperty", txtCustomPropertyValue.Text) 
     Me.Close 
   End Sub 

   Private Sub btnCancel_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     Me.Close 
   End Sub 
 End Class 

End Namespace
```

<span data-ttu-id="d9ecd-156">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d9ecd-156">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d9ecd-157">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="d9ecd-157">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d9ecd-158">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="d9ecd-158">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d9ecd-159">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="d9ecd-159">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ecd-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9ecd-160">See Also</span></span>
 [<span data-ttu-id="d9ecd-161">创建自定义数据流组件</span><span class="sxs-lookup"><span data-stu-id="d9ecd-161">Creating a Custom Data Flow Component</span></span>](creating-a-custom-data-flow-component.md)


