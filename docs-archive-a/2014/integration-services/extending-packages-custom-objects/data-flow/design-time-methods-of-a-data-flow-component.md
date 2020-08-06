---
title: 数据流组件的设计时方法 | Microsoft Docs
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
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e33fc4eb5805318dac217d2c5cbaedfd4bca70fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588661"
---
# <a name="design-time-methods-of-a-data-flow-component"></a><span data-ttu-id="f7d8a-102">数据流组件的设计时方法</span><span class="sxs-lookup"><span data-stu-id="f7d8a-102">Design-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="f7d8a-103">在执行前，称数据流任务处于设计时状态，因为它将接受增量更改。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-103">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="f7d8a-104">这些更改可以包括添加或删除组件、添加或删除连接组件的路径对象以及更改组件的元数据。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-104">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="f7d8a-105">出现元数据更改时，组件可监视这些更改并对这些更改作出响应。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-105">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="f7d8a-106">例如，组件可以禁止某些更改或为响应某一更改而进行其他更改。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-106">For example, a component can disallow certain changes or make additional changes in response to a change.</span></span> <span data-ttu-id="f7d8a-107">在设计时，设计器通过设计时 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 接口与组件进行交互。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-107">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>

## <a name="design-time-implementation"></a><span data-ttu-id="f7d8a-108">设计时实现</span><span class="sxs-lookup"><span data-stu-id="f7d8a-108">Design-Time Implementation</span></span>
 <span data-ttu-id="f7d8a-109">组件的设计时接口通过 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 接口描述。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-109">The design-time interface of a component is described by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span> <span data-ttu-id="f7d8a-110">虽然您不显式实现此接口，但熟悉此接口中定义的方法将有助于您了解 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基类的哪些方法与组件的设计时实例相对应。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-110">Although you do not explicitly implement this interface, a familiarity with the methods defined in this interface will help you understand which methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class correspond to the design-time instance of a component.</span></span>

 <span data-ttu-id="f7d8a-111">组件加载到 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 后，组件的设计时实例将会被实例化，并会在编辑组件时调用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 接口的方法。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-111">When a component is loaded in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], the design-time instance of the component is instantiated and the methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface are called as the component is edited.</span></span> <span data-ttu-id="f7d8a-112">基类的实现使您可以只重写您组件需要的方法。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-112">The implementation of the base class lets you override only those methods that your component requires.</span></span> <span data-ttu-id="f7d8a-113">在很多情况下，您可以重写这些方法，以阻止不当的组件编辑。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-113">In many cases, you may override these methods to prevent inappropriate edits to a component.</span></span> <span data-ttu-id="f7d8a-114">例如，若要阻止用户向组件中添加输出，可重写 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-114">For example, to prevent users from adding an output to a component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> method.</span></span> <span data-ttu-id="f7d8a-115">否则，当基类调用此方法的实现时，它会向组件中添加一个输出。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-115">Otherwise, when the implementation of this method by the base class is called, it adds an output to the component.</span></span>

 <span data-ttu-id="f7d8a-116">无论组件的用途或功能是什么，您都应重写 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-116">Regardless of the purpose or functionality of your component, you should override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> methods.</span></span> <span data-ttu-id="f7d8a-117">有关 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 的详细信息，请参阅[验证数据流组件](validating-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-117">For more information about <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, see [Validating a Data Flow Component](validating-a-data-flow-component.md).</span></span>

## <a name="providecomponentproperties-method"></a><span data-ttu-id="f7d8a-118">ProvideComponentProperties 方法</span><span class="sxs-lookup"><span data-stu-id="f7d8a-118">ProvideComponentProperties Method</span></span>
 <span data-ttu-id="f7d8a-119">组件的初始化在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法中进行。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-119">The initialization of a component occurs in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="f7d8a-120">此方法在组件添加到数据流任务时由 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器调用，它类似于一个类构造函数。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-120">This method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer when a component is added to the data flow task, and is similar to a class constructor.</span></span> <span data-ttu-id="f7d8a-121">组件开发人员应该在此方法调用期间创建并初始化该方法的输入、输出和自定义属性。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-121">Component developers should create and initialize their inputs, outputs, and custom properties during this method call.</span></span> <span data-ttu-id="f7d8a-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法不同于构造函数，因为并不是每次实例化组件的设计时实例或运行时实例时都会调用此方法。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method differs from a constructor because it is not called every time that the design-time instance or run-time instance of the component is instantiated.</span></span>

 <span data-ttu-id="f7d8a-123">方法的基类实现向组件中添加输入和输出，并向 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 属性分配输入的 ID。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-123">The base class implementation of the method adds an input and an output to the component and assigns the ID of the input to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property.</span></span> <span data-ttu-id="f7d8a-124">但是，在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，未命名基类添加的输入和输出对象。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-124">However, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the input and output objects added by the base class are not named.</span></span> <span data-ttu-id="f7d8a-125">如果包中的某个组件具有未设置 Name 属性的输入或输出对象，则无法成功加载包。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-125">Packages that contain a component with input or output objects whose Name property is not set will not successfully load.</span></span> <span data-ttu-id="f7d8a-126">因此，在使用基实现时，必须对默认输入和输出的 Name 属性显式赋值。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-126">Therefore, when you use the base implementation, you must assign values explicitly to the Name property of the default input and output.</span></span>

```csharp
public override void ProvideComponentProperties()
{
    /// TODO: Reset the component.
    /// TODO: Add custom properties.
    /// TODO: Add input objects.
    /// TODO: Add output objects.
}
```

```vb
Public Overrides Sub ProvideComponentProperties()
    ' TODO: Reset the component.
    ' TODO: Add custom properties.
    ' TODO: Add input objects.
    ' TODO: Add output objects.
End Sub
```

### <a name="creating-custom-properties"></a><span data-ttu-id="f7d8a-127">创建自定义属性</span><span class="sxs-lookup"><span data-stu-id="f7d8a-127">Creating Custom Properties</span></span>
 <span data-ttu-id="f7d8a-128">在对 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法的调用中，组件开发人员应该向组件添加自定义属性 (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>)。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-128">The call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method is where component developers should add custom properties (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) to the component.</span></span> <span data-ttu-id="f7d8a-129">自定义属性没有数据类型属性。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-129">Custom properties do not have a data type property.</span></span> <span data-ttu-id="f7d8a-130">自定义属性的数据类型由值的数据类型设置，您已将该数据类型分配给其 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-130">The data type of a custom property is set by the data type of the value that you assign to its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> property.</span></span> <span data-ttu-id="f7d8a-131">但是，在向自定义属性分配初始值后，不能分配具有其他数据类型的值。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-131">However, after you have assigned an initial value to the custom property, you cannot assign a value with a different data type.</span></span>

> [!NOTE]
>  <span data-ttu-id="f7d8a-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 接口提供对 `Object` 类型的属性值的有限支持。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-132">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> interface has limited support for property values of type `Object`.</span></span> <span data-ttu-id="f7d8a-133">能够作为自定义属性值存储的唯一对象是简单类型数组，如字符串或整数。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-133">The only object that you can store as the value of a custom property is an array of simple types such as strings or integers.</span></span>

 <span data-ttu-id="f7d8a-134">可指示自定义属性支持属性表达式，方法是从 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> 枚举将其 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> 属性的值设置为 `CPET_NOTIFY`，如下列示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-134">You can indicate that your custom property supports property expressions by setting the value of its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> property to `CPET_NOTIFY` from the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> enumeration, as shown in the following example.</span></span> <span data-ttu-id="f7d8a-135">不必添加用于处理或验证用户输入的属性表达式的任何代码。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-135">You do not have to add any code to handle or to validate the property expression entered by the user.</span></span> <span data-ttu-id="f7d8a-136">可以设置属性的默认值、验证该值并正常读取和使用该值。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-136">You can set a default value for the property, validate its value, and read and use its value normally.</span></span>

```csharp
IDTSCustomProperty100 myCustomProperty;
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;
```

```vb
Dim myCustomProperty As IDTSCustomProperty100
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY
```

 <span data-ttu-id="f7d8a-137">您可以通过使用属性来限制用户从枚举中选择自定义属性值 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> ，如下面的示例所示，该示例假设您已经定义了一个名为的公共枚举 `MyValidValues` 。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-137">You can limit users to selecting a custom property value from an enumeration by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> property, as shown in the following example, which assumes that you have defined a public enumeration named `MyValidValues`.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the type with the custom property.
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;
// Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne;  
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the type with the custom property.
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName 
' Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne
```

 <span data-ttu-id="f7d8a-138">有关详细信息，请参阅 [MSDN 库](https://go.microsoft.com/fwlink/?LinkId=7022)中的“通用类型转换”和“实现类型转换器”。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-138">For more information, see "Generalized Type Conversion" and "Implementing a Type Converter" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

 <span data-ttu-id="f7d8a-139">可使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 属性指定自定义属性的值的自定义编辑器对话框，如下列示例中所示。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-139">You can specify a custom editor dialog box for the value of your custom property by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property, as shown in the following example.</span></span> <span data-ttu-id="f7d8a-140">首先，如果无法找到能够满足您需要的现有 UI 类型编辑器，则必须创建从 `System.Drawing.Design.UITypeEditor` 继承的自定义属性编辑器。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-140">First, you must create a custom type editor that inherits from `System.Drawing.Design.UITypeEditor`, if you cannot locate an existing UI type editor class that fits your needs.</span></span>

```csharp
public class MyCustomTypeEditor : UITypeEditor
{
...
}
```

```vb
Public Class MyCustomTypeEditor
  Inherits UITypeEditor 
  ...
End Class
```

 <span data-ttu-id="f7d8a-141">然后，指定此类作为自定义属性的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-141">Next, specify this class as the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property of your custom property.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the editor with the custom property.
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the editor with the custom property.
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName
```

 <span data-ttu-id="f7d8a-142">有关详细信息，请参阅 [MSDN 库](https://go.microsoft.com/fwlink/?LinkId=7022)中的“实现 UI 类型编辑器”。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-142">For more information, see "Implementing a UI Type Editor" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

<span data-ttu-id="f7d8a-143">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f7d8a-143">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f7d8a-144">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="f7d8a-144">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f7d8a-145">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="f7d8a-145">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f7d8a-146">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="f7d8a-146">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7d8a-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7d8a-147">See Also</span></span>
 [<span data-ttu-id="f7d8a-148">数据流组件的运行时方法</span><span class="sxs-lookup"><span data-stu-id="f7d8a-148">Run-time Methods of a Data Flow Component</span></span>](run-time-methods-of-a-data-flow-component.md)


