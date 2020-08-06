---
title: 脚本组件的编码和调试 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9363ad447ca3d0031289eafb1d8f616320fca5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587917"
---
# <a name="coding-and-debugging-the-script-component"></a><span data-ttu-id="ba815-102">脚本组件的编码和调试</span><span class="sxs-lookup"><span data-stu-id="ba815-102">Coding and Debugging the Script Component</span></span>
  <span data-ttu-id="ba815-103">在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中，脚本组件具有两种模式：元数据设计模式和代码设计模式。</span><span class="sxs-lookup"><span data-stu-id="ba815-103">In [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata design mode and code design mode.</span></span> <span data-ttu-id="ba815-104">打开“脚本转换编辑器”后，组件将进入元数据设计模式，你可以在该模式下配置元数据并设置组件属性  。</span><span class="sxs-lookup"><span data-stu-id="ba815-104">When you open the **Script Transformation Editor**, the component enters metadata design mode, in which you configure metadata and set component properties.</span></span> <span data-ttu-id="ba815-105">在元数据设计模式下，设置脚本组件的属性并配置输入和输出后，可以切换到代码设计模式，以编写自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="ba815-105">After you have set the properties of the Script component and configured the input and outputs in metadata design mode, you can switch to code design mode to write your custom script.</span></span> <span data-ttu-id="ba815-106">有关元数据设计模式和代码设计模式的详细信息，请参阅[在脚本组件编辑器中配置脚本组件](configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-106">For more information about metadata design mode and code design mode, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md).</span></span>

## <a name="writing-the-script-in-code-design-mode"></a><span data-ttu-id="ba815-107">在代码设计模式下编写脚本</span><span class="sxs-lookup"><span data-stu-id="ba815-107">Writing the Script in Code Design Mode</span></span>

### <a name="script-component-development-environment"></a><span data-ttu-id="ba815-108">脚本组件开发环境</span><span class="sxs-lookup"><span data-stu-id="ba815-108">Script Component Development Environment</span></span>
 <span data-ttu-id="ba815-109">要编写脚本，请在“脚本转换编辑器”的“脚本”页面中，单击“编辑脚本”打开  Tools for Applications (VSTA) IDE   [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ba815-109">To write your script, click **Edit Script** on the **Script** page of the **Script Transformation Editor** to open the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE.</span></span> <span data-ttu-id="ba815-110">VSTA IDE 包含 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET 环境的所有标准功能，如具有颜色编码的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 编辑器、IntelliSense 和对象浏览器。</span><span class="sxs-lookup"><span data-stu-id="ba815-110">The VSTA IDE includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span>

 <span data-ttu-id="ba815-111">脚本代码以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 编写。</span><span class="sxs-lookup"><span data-stu-id="ba815-111">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="ba815-112">在“脚本转换编辑器”中设置 ScriptLanguage 属性可指定脚本语言   。</span><span class="sxs-lookup"><span data-stu-id="ba815-112">You specify the script language by setting the **ScriptLanguage** property in the **Script Transformation Editor**.</span></span> <span data-ttu-id="ba815-113">如果您倾向于使用其他编程语言，则可以用您选择的语言开发自定义程序集，然后通过脚本组件中的代码调用其功能。</span><span class="sxs-lookup"><span data-stu-id="ba815-113">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script component.</span></span>

 <span data-ttu-id="ba815-114">您在脚本组件中创建的脚本存储在包定义中。</span><span class="sxs-lookup"><span data-stu-id="ba815-114">The script that you create in the Script component is stored in the package definition.</span></span> <span data-ttu-id="ba815-115">由于没有单独的脚本文件，</span><span class="sxs-lookup"><span data-stu-id="ba815-115">There is no separate script file.</span></span> <span data-ttu-id="ba815-116">因此，使用脚本组件不会影响包部署。</span><span class="sxs-lookup"><span data-stu-id="ba815-116">Therefore, the use of the Script component does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="ba815-117">设计包时，脚本代码将临时写入项目文件。</span><span class="sxs-lookup"><span data-stu-id="ba815-117">While you design the package, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="ba815-118">由于在文件中存储敏感信息存在潜在的安全风险，因此建议您不要在脚本代码中包含敏感信息，如密码。</span><span class="sxs-lookup"><span data-stu-id="ba815-118">Because storing sensitive information in a file is a potential security risk, we recommended that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="ba815-119">默认情况下，`Option Strict` 在 IDE 中处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="ba815-119">By default, `Option Strict` is disabled in the IDE.</span></span>

### <a name="script-component-project-structure"></a><span data-ttu-id="ba815-120">脚本组件项目结构</span><span class="sxs-lookup"><span data-stu-id="ba815-120">Script Component Project Structure</span></span>
 <span data-ttu-id="ba815-121">脚本组件的功能在于它可生成基础结构代码，从而减少您必须编写的代码的数量。</span><span class="sxs-lookup"><span data-stu-id="ba815-121">The power of the Script component is that it can generate infrastructure code that reduces the amount of code that you must write.</span></span> <span data-ttu-id="ba815-122">此功能依赖于这样一个事实：输入和输出及其列和属性都是事先固定且已知的。</span><span class="sxs-lookup"><span data-stu-id="ba815-122">This feature relies on the fact that inputs and outputs and their columns and properties are fixed and known in advance.</span></span> <span data-ttu-id="ba815-123">因此，您对组件的元数据所做的任何后续更改都可能会使已编写的代码无效。</span><span class="sxs-lookup"><span data-stu-id="ba815-123">Therefore, any subsequent changes that you make to the component's metadata may invalidate the code that you have written.</span></span> <span data-ttu-id="ba815-124">这将在包的执行过程中导致编译错误。</span><span class="sxs-lookup"><span data-stu-id="ba815-124">This causes compilation errors during execution of the package.</span></span>

#### <a name="project-items-and-classes-in-the-script-component-project"></a><span data-ttu-id="ba815-125">脚本组件项目中的项目项和类</span><span class="sxs-lookup"><span data-stu-id="ba815-125">Project Items and Classes in the Script Component Project</span></span>
 <span data-ttu-id="ba815-126">切换到代码设计模式后，VSTA IDE 将打开并显示 `ScriptMain` 项目项。</span><span class="sxs-lookup"><span data-stu-id="ba815-126">When you switch to code design mode, the VSTA IDE opens and displays the `ScriptMain` project item.</span></span> <span data-ttu-id="ba815-127">`ScriptMain` 项目项包含可编辑的 `ScriptMain` 类，该类用作脚本的入口点，您可在其中编写代码。</span><span class="sxs-lookup"><span data-stu-id="ba815-127">The `ScriptMain` project item contains the editable `ScriptMain` class, which serves as the entry point for the script and which is where you write your code.</span></span> <span data-ttu-id="ba815-128">该类中的代码元素根据您选择的脚本任务编程语言而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ba815-128">The code elements in the class vary depending on the programming language that you selected for the Script task.</span></span>

 <span data-ttu-id="ba815-129">脚本项目包含两个自动生成的附加只读项目项：</span><span class="sxs-lookup"><span data-stu-id="ba815-129">The script project contains two additional auto-generated read-only project items:</span></span>

-   <span data-ttu-id="ba815-130">`ComponentWrapper` 项目项包含三个类：</span><span class="sxs-lookup"><span data-stu-id="ba815-130">The `ComponentWrapper` project item contains three classes:</span></span>

    -   <span data-ttu-id="ba815-131">`UserComponent` 类，继承自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>，包含您将用于处理数据和与包进行交互的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="ba815-131">The `UserComponent` class, which inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> and contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="ba815-132">`ScriptMain` 类从 `UserComponent` 类继承。</span><span class="sxs-lookup"><span data-stu-id="ba815-132">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

    -   <span data-ttu-id="ba815-133">`Connections` 集合类，包含对在“脚本转换编辑器”的“连接管理器”页上选择的连接的引用。</span><span class="sxs-lookup"><span data-stu-id="ba815-133">A `Connections` collection class that contains references to the connections selected on the Connection Manager page of the Script Transformation Editor.</span></span>

    -   <span data-ttu-id="ba815-134">一个 `Variables` 集合类，包含对在 " `ReadOnlyVariable` `ReadWriteVariables` **脚本转换编辑器**" 的 "**脚本**" 页上的和属性中输入的变量的引用。</span><span class="sxs-lookup"><span data-stu-id="ba815-134">A `Variables` collection class that contains references to the variables entered in the `ReadOnlyVariable` and `ReadWriteVariables` properties on the **Script** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="ba815-135">`BufferWrapper` <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 对于在 "**脚本转换编辑器**" 的 "**输入和输出**" 页上配置的每个输入和输出，项目项都包含从继承的类。</span><span class="sxs-lookup"><span data-stu-id="ba815-135">The `BufferWrapper` project item contains a class that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output configured on the **Inputs and Outputs** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="ba815-136">其中每个类都包含与已配置的输入和输出列对应的类型化取值函数属性以及包含这些列的数据流缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ba815-136">Each of these classes contains typed accessor properties that correspond to the configured input and output columns, and the data flow buffers that contain the columns.</span></span>

 <span data-ttu-id="ba815-137">有关如何使用这些对象、方法和属性的信息，请参阅[了解脚本组件对象模型](understanding-the-script-component-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-137">For information about how to use these objects, methods, and properties, see [Understanding the Script Component Object Model](understanding-the-script-component-object-model.md).</span></span> <span data-ttu-id="ba815-138">有关如何在特定类型的脚本组件中使用这些类的方法和属性的信息，请参阅[其他脚本组件示例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)一节。</span><span class="sxs-lookup"><span data-stu-id="ba815-138">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="ba815-139">该示例主题还包含完整的代码示例。</span><span class="sxs-lookup"><span data-stu-id="ba815-139">The example topics also contain complete code samples.</span></span>

 <span data-ttu-id="ba815-140">将脚本组件配置为转换时，`ScriptMain` 项目项将包含下列自动生成的代码。</span><span class="sxs-lookup"><span data-stu-id="ba815-140">When you configure the Script component as a transformation, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="ba815-141">该代码模板还提供脚本组件的概览以及有关如何检索和操作 SSIS 对象（如变量、事件和连接）的其他信息。</span><span class="sxs-lookup"><span data-stu-id="ba815-141">The code template also provides an overview of the Script component, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Component
' Write scripts using Microsoft Visual Basic 2008.
' ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _
<CLSCompliant(False)> _
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub PreExecute()
        MyBase.PreExecute()
        '
        ' Add your code here for preprocessing or remove if not needed
        '
    End Sub

    Public Overrides Sub PostExecute()
        MyBase.PostExecute()
        '
        ' Add your code here for postprocessing or remove if not needed
        ' You can set read/write variables here, for example:
        ' Me.Variables.MyIntVar = 100
        '
    End Sub

    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)
        '
        ' Add your code here
        '
    End Sub

End Class
```

```csharp
/* Microsoft SQL Server Integration Services user script component
*  Write scripts using Microsoft Visual C# 2008.
*  ScriptMain is the entry point class of the script.*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]
public class ScriptMain : UserComponent
{

    public override void PreExecute()
    {
        base.PreExecute();
        /*
          Add your code here for preprocessing or remove if not needed
        */
    }

    public override void PostExecute()
    {
        base.PostExecute();
        /*
          Add your code here for postprocessing or remove if not needed
          You can set read/write variables here, for example:
          Variables.MyIntVar = 100
        */
    }

    public override void Input0_ProcessInputRow(Input0Buffer Row)
    {
        /*
          Add your code here
        */
    }

}
```

#### <a name="additional-project-items-in-the-script-component-project"></a><span data-ttu-id="ba815-142">脚本组件项目中的其他项目项</span><span class="sxs-lookup"><span data-stu-id="ba815-142">Additional Project Items in the Script Component Project</span></span>
 <span data-ttu-id="ba815-143">脚本组件项目可包含默认的 `ScriptMain` 项以外的其他项。</span><span class="sxs-lookup"><span data-stu-id="ba815-143">The Script component project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="ba815-144">您可以向项目中添加类、模块、代码文件和文件夹，并使用文件夹来组织项组。</span><span class="sxs-lookup"><span data-stu-id="ba815-144">You can add classes, modules, code files, and folders to the project, and you can use folders to organize groups of items.</span></span>

 <span data-ttu-id="ba815-145">您添加的所有项在包中都将持久化。</span><span class="sxs-lookup"><span data-stu-id="ba815-145">All the items that you add are persisted inside the package.</span></span>

#### <a name="references-in-the-script-component-project"></a><span data-ttu-id="ba815-146">脚本组件项目中的引用</span><span class="sxs-lookup"><span data-stu-id="ba815-146">References in the Script Component Project</span></span>
 <span data-ttu-id="ba815-147">在“项目资源管理器”中右键单击脚本任务项目，然后单击“添加引用”，可以添加对托管程序集的引用   。</span><span class="sxs-lookup"><span data-stu-id="ba815-147">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="ba815-148">有关详细信息，请参阅[引用脚本解决方案中的其他程序集](../referencing-other-assemblies-in-scripting-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-148">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="ba815-149">可以在“类视图”或“项目资源管理器”中查看 VSTA IDE 中的项目引用   。</span><span class="sxs-lookup"><span data-stu-id="ba815-149">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="ba815-150">这些窗口都可以从“视图”菜单中打开  。</span><span class="sxs-lookup"><span data-stu-id="ba815-150">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="ba815-151">可以从“项目”菜单、“项目资源管理器”或“类视图”添加新引用    。</span><span class="sxs-lookup"><span data-stu-id="ba815-151">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-component"></a><span data-ttu-id="ba815-152">与脚本组件中的包进行交互</span><span class="sxs-lookup"><span data-stu-id="ba815-152">Interacting with the Package in the Script Component</span></span>
 <span data-ttu-id="ba815-153">您在脚本组件中编写的自定义脚本可通过自动生成的基类中的强类型取值函数来访问和使用包含包中的变量和连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ba815-153">The custom script that you write in the Script component can access and use variables and connection managers from the containing package through strongly-typed accessors in the auto-generated base classes.</span></span> <span data-ttu-id="ba815-154">但是，若要使这些变量和连接管理器可用于您的脚本，您必须先对它们进行配置，然后才可进入代码设计模式。</span><span class="sxs-lookup"><span data-stu-id="ba815-154">However, you must configure both variables and connection managers before entering code-design mode if you want to make them available to your script.</span></span> <span data-ttu-id="ba815-155">还可以从脚本组件代码引发事件并执行日志记录。</span><span class="sxs-lookup"><span data-stu-id="ba815-155">You can also raise events and perform logging from your Script component code.</span></span>

 <span data-ttu-id="ba815-156">脚本组件项目中自动生成的项目项可提供以下用于与包进行交互的对象、方法和属性。</span><span class="sxs-lookup"><span data-stu-id="ba815-156">The autogenerated project items in the Script component project provide the following objects, methods, and properties for interacting with the package.</span></span>

|<span data-ttu-id="ba815-157">包的功能</span><span class="sxs-lookup"><span data-stu-id="ba815-157">Package Feature</span></span>|<span data-ttu-id="ba815-158">访问方法</span><span class="sxs-lookup"><span data-stu-id="ba815-158">Access Method</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="ba815-159">变量</span><span class="sxs-lookup"><span data-stu-id="ba815-159">Variables</span></span>|<span data-ttu-id="ba815-160">使用 `Variables` 项目项的 `ComponentWrapper` 集合类中的命名取值函数属性和类型化取值函数属性，这些属性通过 `Variables` 类的 `ScriptMain` 属性公开。</span><span class="sxs-lookup"><span data-stu-id="ba815-160">Use the named and typed accessor properties in the `Variables` collection class in the `ComponentWrapper` project item, exposed through the `Variables` property of the `ScriptMain` class.</span></span><br /><br /> <span data-ttu-id="ba815-161">`PreExecute` 方法仅可访问只读变量。</span><span class="sxs-lookup"><span data-stu-id="ba815-161">The `PreExecute` method can access only read-only variables.</span></span> <span data-ttu-id="ba815-162">`PostExecute` 方法既可以访问只读变量，又可以访问读/写变量。</span><span class="sxs-lookup"><span data-stu-id="ba815-162">The `PostExecute` method can access both read-only and read/write variables.</span></span>|
|<span data-ttu-id="ba815-163">连接</span><span class="sxs-lookup"><span data-stu-id="ba815-163">Connections</span></span>|<span data-ttu-id="ba815-164">使用 `Connections` 项目项的 `ComponentWrapper` 集合类中的命名取值函数属性和类型化取值函数属性，这些属性通过 `Connections` 类的 `ScriptMain` 属性公开。</span><span class="sxs-lookup"><span data-stu-id="ba815-164">Use the named and typed accessor properties in the `Connections` collection class in the `ComponentWrapper` project item, exposed through the `Connections` property of the `ScriptMain` class.</span></span>|
|<span data-ttu-id="ba815-165">事件</span><span class="sxs-lookup"><span data-stu-id="ba815-165">Events</span></span>|<span data-ttu-id="ba815-166">使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 类的属性 `ScriptMain` 和接口的\*\*灭火器 \<X> \*\*方法引发事件 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 。</span><span class="sxs-lookup"><span data-stu-id="ba815-166">Raise events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class and the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>|
|<span data-ttu-id="ba815-167">日志记录</span><span class="sxs-lookup"><span data-stu-id="ba815-167">Logging</span></span>|<span data-ttu-id="ba815-168">使用 `ScriptMain` 类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法执行日志记录。</span><span class="sxs-lookup"><span data-stu-id="ba815-168">Perform logging by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class.</span></span>|

## <a name="debugging-the-script-component"></a><span data-ttu-id="ba815-169">调试脚本组件</span><span class="sxs-lookup"><span data-stu-id="ba815-169">Debugging the Script Component</span></span>
 <span data-ttu-id="ba815-170">若要调试脚本组件中的代码，请在代码中设置至少一个断点，然后关闭 VSTA IDE 以在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中运行包。</span><span class="sxs-lookup"><span data-stu-id="ba815-170">To debug the code in your Script component, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ba815-171">当包执行进入脚本组件时，VSTA IDE 会在只读模式下重新打开并显示您的代码。</span><span class="sxs-lookup"><span data-stu-id="ba815-171">When package execution enters the Script component, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="ba815-172">包执行到达您的断点后，您可以检查变量值，并单步执行剩余代码。</span><span class="sxs-lookup"><span data-stu-id="ba815-172">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!NOTE]
>  <span data-ttu-id="ba815-173">如果将脚本组件作为从执行包任务运行的子包的一部分来执行，则不能调试该脚本组件。</span><span class="sxs-lookup"><span data-stu-id="ba815-173">You cannot debug a Script component when you run the Script component as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="ba815-174">在这些情况下，您在子包的脚本组件中设置的断点将被忽略。</span><span class="sxs-lookup"><span data-stu-id="ba815-174">Breakpoints that you set in the Script component in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="ba815-175">您可以通过单独运行子包来正常调试子包。</span><span class="sxs-lookup"><span data-stu-id="ba815-175">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="ba815-176">当调试包含多个脚本组件的包时，调试器将调试一个脚本组件。</span><span class="sxs-lookup"><span data-stu-id="ba815-176">When you debug a package that contains multiple Script components, the debugger debugs one Script component.</span></span> <span data-ttu-id="ba815-177">系统可以在调试器完成调试后调试另一个脚本组件，就像在 Foreach 循环容器或 For 循环容器中那样。</span><span class="sxs-lookup"><span data-stu-id="ba815-177">The system can debug another Script component if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

 <span data-ttu-id="ba815-178">还可以使用以下方法监视脚本组件的执行：</span><span class="sxs-lookup"><span data-stu-id="ba815-178">You can also monitor the execution of the Script component by using the following methods:</span></span>

-   <span data-ttu-id="ba815-179">中断执行，并使用 `MessageBox.Show` **system.web**命名空间中的方法显示模式消息。</span><span class="sxs-lookup"><span data-stu-id="ba815-179">Interrupt execution and display a modal message by using the `MessageBox.Show` method in the **System.Windows.Forms** namespace.</span></span> <span data-ttu-id="ba815-180">（调试过程结束后，请删除此代码。）</span><span class="sxs-lookup"><span data-stu-id="ba815-180">(Remove this code after you complete the debugging process.)</span></span>

-   <span data-ttu-id="ba815-181">引发信息性消息、警告和错误的事件。</span><span class="sxs-lookup"><span data-stu-id="ba815-181">Raise events for informational messages, warnings, and errors.</span></span> <span data-ttu-id="ba815-182">FireInformation、FireWarning 和 FireError 方法可在 Visual Studio“输出”窗口中显示事件说明  。</span><span class="sxs-lookup"><span data-stu-id="ba815-182">The FireInformation, FireWarning, and FireError methods display the event description in the Visual Studio **Output** window.</span></span> <span data-ttu-id="ba815-183">但是，FireProgress、Console.Write 和 Console.WriteLine 方法在“输出”窗口中不显示任何信息  。</span><span class="sxs-lookup"><span data-stu-id="ba815-183">However, the FireProgress method, the Console.Write method, and Console.WriteLine method do not display any information in the **Output** window.</span></span> <span data-ttu-id="ba815-184">FireProgress 事件的消息显示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器的“进度”选项卡中。</span><span class="sxs-lookup"><span data-stu-id="ba815-184">Messages from the FireProgress event appear on the **Progress** tab of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ba815-185">有关详细信息，请参阅[在脚本组件中引发事件](../../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-185">For more information, see [Raising Events in the Script Component](../../data-flow/transformations/script-component.md).</span></span>

-   <span data-ttu-id="ba815-186">将事件或用户定义的消息记录到已启用的日志记录提供程序中。</span><span class="sxs-lookup"><span data-stu-id="ba815-186">Log events or user-defined messages to enabled logging providers.</span></span> <span data-ttu-id="ba815-187">有关详细信息，请参阅[脚本组件中的日志记录](logging-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-187">For more information, see [Logging in the Script Component](logging-in-the-script-component.md).</span></span>

 <span data-ttu-id="ba815-188">如果你只想检查配置为源或转换的脚本组件的输出，而不将数据保存到目标，则可以使用[行计数转换](../../data-flow/transformations/row-count-transformation.md)停止数据流，并向脚本组件的输出附加一个数据查看器。</span><span class="sxs-lookup"><span data-stu-id="ba815-188">If you just want to examine the output of a Script component configured as a source or as a transformation, without saving the data to a destination, you can stop the data flow with a [Row Count Transformation](../../data-flow/transformations/row-count-transformation.md) and attach a data viewer to the output of the Script component.</span></span> <span data-ttu-id="ba815-189">有关数据查看器的信息，请参阅[调试数据流](../../troubleshooting/debugging-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="ba815-189">For information about data viewers, see [Debugging Data Flow](../../troubleshooting/debugging-data-flow.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ba815-190">本节内容</span><span class="sxs-lookup"><span data-stu-id="ba815-190">In This Section</span></span>
 <span data-ttu-id="ba815-191">有关编写脚本组件代码的详细信息，请参阅本节中的下列主题。</span><span class="sxs-lookup"><span data-stu-id="ba815-191">For more information about coding the Script component, see the following topics in this section.</span></span>

 <span data-ttu-id="ba815-192">[了解脚本组件对象模型](understanding-the-script-component-object-model.md)介绍如何使用脚本组件中提供的对象、方法和属性。</span><span class="sxs-lookup"><span data-stu-id="ba815-192">[Understanding the Script Component Object Model](understanding-the-script-component-object-model.md) Explains how to use the objects, methods, and properties available in the Script component.</span></span>

 <span data-ttu-id="ba815-193">[引用脚本解决方案中的其他程序集](../referencing-other-assemblies-in-scripting-solutions.md)说明如何 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 在脚本组件中从类库引用对象。</span><span class="sxs-lookup"><span data-stu-id="ba815-193">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) Explains how to reference objects from the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library in the Script component.</span></span>

 <span data-ttu-id="ba815-194">[模拟脚本组件的错误输出](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)说明如何模拟脚本组件在处理过程中引发错误的行的错误输出。</span><span class="sxs-lookup"><span data-stu-id="ba815-194">[Simulating an Error Output for the Script Component](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md) Explains how to simulate an error output for rows that raise errors during processing by the Script component.</span></span>

## <a name="external-resources"></a><span data-ttu-id="ba815-195">外部资源</span><span class="sxs-lookup"><span data-stu-id="ba815-195">External Resources</span></span>

-   <span data-ttu-id="ba815-196">blogs.msdn.com 上的博客文章：[VSTA setup and configuration troubles for SSIS 2008 and R2 installations（针对 SSIS 2008 和 R2 安装的 VSTA 安装和配置难题）](https://go.microsoft.com/fwlink/?LinkId=215661)。</span><span class="sxs-lookup"><span data-stu-id="ba815-196">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="ba815-197">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ba815-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ba815-198">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="ba815-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ba815-199">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="ba815-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ba815-200">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="ba815-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba815-201">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba815-201">See Also</span></span>
 [<span data-ttu-id="ba815-202">在脚本组件编辑器中配置脚本组件</span><span class="sxs-lookup"><span data-stu-id="ba815-202">Configuring the Script Component in the Script Component Editor</span></span>](configuring-the-script-component-in-the-script-component-editor.md)


