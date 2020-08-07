---
title: 使用脚本组件创建异步转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 465c4a597b4a18d7bd956116cd5d7640a5393958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587472"
---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a><span data-ttu-id="ed082-102">使用脚本组件创建异步转换</span><span class="sxs-lookup"><span data-stu-id="ed082-102">Creating an Asynchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="ed082-103">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中使用转换组件可以在数据从源传递到目标时修改和分析该数据。</span><span class="sxs-lookup"><span data-stu-id="ed082-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="ed082-104">具有同步输出的转换在每个输入行传递给该组件时对该行进行处理。</span><span class="sxs-lookup"><span data-stu-id="ed082-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="ed082-105">具有异步输出的转换可能要等收到所有输入行之后才完成其处理，也可能在收到所有输入行之前输出某些行。</span><span class="sxs-lookup"><span data-stu-id="ed082-105">A transformation with asynchronous outputs may wait to complete its processing until the transformation has received all input rows, or the transformation may output certain rows before it has received all input rows.</span></span> <span data-ttu-id="ed082-106">本主题讨论异步转换。</span><span class="sxs-lookup"><span data-stu-id="ed082-106">This topic discusses an asynchronous transformation.</span></span> <span data-ttu-id="ed082-107">如果你的处理需要同步转换，请参阅[使用脚本组件创建同步转换](../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-107">If your processing requires a synchronous transformation, see [Creating a Synchronous Transformation with the Script Component](../data-flow/transformations/script-component.md).</span></span> <span data-ttu-id="ed082-108">有关同步组件和异步组件之间的差异的详细信息，请参阅[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-108">For more information about the differences between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="ed082-109">有关脚本组件的概述，请参阅[使用脚本组件扩展数据流](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="ed082-110">脚本组件及其生成的基础结构代码可以简化自定义数据流组件的开发过程。</span><span class="sxs-lookup"><span data-stu-id="ed082-110">The Script component and the infrastructure code that it generates for you simplify the process of developing a custom data flow component.</span></span> <span data-ttu-id="ed082-111">但是，若要了解脚本组件的工作方式，通读以下步骤很有帮助，这些步骤是在[开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)部分，特别是在[开发具有同步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)部分开发自定义数据流组件必须遵循的。</span><span class="sxs-lookup"><span data-stu-id="ed082-111">However, to understand how the Script component works, you may find it useful to read through the steps that you must follow in developing a custom data flow component in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-an-asynchronous-transformation-component"></a><span data-ttu-id="ed082-112">开始一个异步转换组件</span><span class="sxs-lookup"><span data-stu-id="ed082-112">Getting Started with an Asynchronous Transformation Component</span></span>
 <span data-ttu-id="ed082-113">向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“数据流”选项卡添加脚本组件时，“选择脚本组件类型”  对话框会出现，提示用户将组件预配置为源、转换或目标。</span><span class="sxs-lookup"><span data-stu-id="ed082-113">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box appears, prompting you to preconfigure the component as a source, transformation, or destination.</span></span> <span data-ttu-id="ed082-114">在此对话框中，选择“转换”  。</span><span class="sxs-lookup"><span data-stu-id="ed082-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="ed082-115">在元数据设计模式下配置异步转换组件</span><span class="sxs-lookup"><span data-stu-id="ed082-115">Configuring an Asynchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="ed082-116">选择创建转换组件的选项后，可使用“脚本转换编辑器”  配置该组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="ed082-117">有关详细信息，请参阅[在脚本组件编辑器中配置脚本组件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="ed082-118">若要选择脚本组件使用的脚本语言，请在“脚本转换编辑器”对话框的“脚本”页设置 **ScriptLanguage** 属性。</span><span class="sxs-lookup"><span data-stu-id="ed082-118">To select the script language that the Script component will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="ed082-119">若要设置脚本组件的默认脚本语言，请使用“选项”对话框的“常规”页上的“脚本语言”选项。</span><span class="sxs-lookup"><span data-stu-id="ed082-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="ed082-120">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="ed082-121">数据流转换组件有一个输入并支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-121">A data flow transformation component has one input and supports one or more outputs.</span></span> <span data-ttu-id="ed082-122">在编写自定义脚本之前，必须在元数据设计模式下完成的一个步骤是使用“脚本转换编辑器”  配置组件的输入和输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-122">Configuring the input and outputs of your component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="ed082-123">配置输入列</span><span class="sxs-lookup"><span data-stu-id="ed082-123">Configuring Input Columns</span></span>
 <span data-ttu-id="ed082-124">使用脚本组件创建的转换组件只有一个输入。</span><span class="sxs-lookup"><span data-stu-id="ed082-124">A transformation component created by using the Script component has a single input.</span></span>

 <span data-ttu-id="ed082-125">在“脚本转换编辑器”的“输入列”页上，列列表显示数据流上游组件输出中的可用列。</span><span class="sxs-lookup"><span data-stu-id="ed082-125">On the **Input Columns** page of the **Script Transformation Editor**, the columns list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="ed082-126">选择要转换或传递的列。</span><span class="sxs-lookup"><span data-stu-id="ed082-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="ed082-127">将要就地转换的所有列标记为读/写。</span><span class="sxs-lookup"><span data-stu-id="ed082-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="ed082-128">有关“脚本转换编辑器”的“输入列”页的详细信息，请参阅[脚本转换编辑器（“输入列”页）](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="ed082-129">配置输入、输出和输出列</span><span class="sxs-lookup"><span data-stu-id="ed082-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="ed082-130">转换组件支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="ed082-131">通常，具有异步输出的转换有两个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-131">Frequently a transformation with asynchronous outputs has two outputs.</span></span> <span data-ttu-id="ed082-132">例如，在您对位于特定城市中的地址进行计数时，可以将地址数据传递给一个输出，同时将聚合结果发送给另一个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-132">For example, when you count the number of addresses located in a specific city, you may want to pass the address data through to one output, while sending the result of the aggregation to another output.</span></span> <span data-ttu-id="ed082-133">聚合输出还需要一个新的输出列。</span><span class="sxs-lookup"><span data-stu-id="ed082-133">The aggregation output also requires a new output column.</span></span>

 <span data-ttu-id="ed082-134">在“脚本转换编辑器”的“输入和输出”页中，可以看到已经默认创建了一个输出，但是还没有创建任何输出列。</span><span class="sxs-lookup"><span data-stu-id="ed082-134">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you see that a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="ed082-135">可以在编辑器的这一页配置下列各项：</span><span class="sxs-lookup"><span data-stu-id="ed082-135">On this page of the editor, you can configure the following items:</span></span>

-   <span data-ttu-id="ed082-136">您可能希望创建一个或多个附加输出，如聚合结果的输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-136">You may want to create one or more additional outputs, such as an output for the result of an aggregation.</span></span> <span data-ttu-id="ed082-137">使用“添加输出”  和“删除输出”  按钮管理异步转换组件的输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-137">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your asynchronous transformation component.</span></span> <span data-ttu-id="ed082-138">将每个输出的 `SynchronousInputID` 属性设置为零可以指示该输出不只是传递来自上游组件的数据或在现有行和列中就地对该数据进行转换。</span><span class="sxs-lookup"><span data-stu-id="ed082-138">Set the `SynchronousInputID` property of each output to zero to indicate that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns.</span></span> <span data-ttu-id="ed082-139">此设置使输出和输入异步。</span><span class="sxs-lookup"><span data-stu-id="ed082-139">It is this setting that makes the outputs asynchronous to the input.</span></span>

-   <span data-ttu-id="ed082-140">您可以为输入和输出指定一个友好名称。</span><span class="sxs-lookup"><span data-stu-id="ed082-140">You may want to assign a friendly name to the input and outputs.</span></span> <span data-ttu-id="ed082-141">脚本组件可以使用这些名称来生成类型化取值函数属性，这些属性用于在脚本中引用输入和输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="ed082-142">通常，异步转换会向数据流添加列。</span><span class="sxs-lookup"><span data-stu-id="ed082-142">Frequently an asynchronous transformation adds columns to the data flow.</span></span> <span data-ttu-id="ed082-143">当输出的 `SynchronousInputID` 属性为零，表示该输出不只是传递来自上游组件的数据或在现有行和列中就地对该数据进行转换时，您必须对该输出显式添加和配置输出列。</span><span class="sxs-lookup"><span data-stu-id="ed082-143">When the `SynchronousInputID` property of an output is zero, indicating that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns, you must add and configure output columns explicitly on the output.</span></span> <span data-ttu-id="ed082-144">输出列不必与其所映射到的输入列同名。</span><span class="sxs-lookup"><span data-stu-id="ed082-144">Output columns do not have to have the same names as the input columns to which they are mapped.</span></span>

-   <span data-ttu-id="ed082-145">您可以添加更多列来包含其他信息。</span><span class="sxs-lookup"><span data-stu-id="ed082-145">You may want to add more columns to contain additional information.</span></span> <span data-ttu-id="ed082-146">您必须编写自己的代码来向这些附加列填充数据。</span><span class="sxs-lookup"><span data-stu-id="ed082-146">You must write your own code to fill the additional columns with data.</span></span> <span data-ttu-id="ed082-147">有关重现标准错误输出行为的信息，请参阅[模拟脚本组件的错误输出](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-147">For information about reproducing the behavior of a standard error output, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="ed082-148">有关“脚本转换编辑器”的“输入和输出”页上的详细信息，请参阅[脚本转换编辑器（“输入和输出”页）](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-148">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="ed082-149">添加变量</span><span class="sxs-lookup"><span data-stu-id="ed082-149">Adding Variables</span></span>
 <span data-ttu-id="ed082-150">如果要在脚本中使用任何现有变量的值，可以在“脚本转换编辑器”的“脚本”页上的 ReadOnlyVariables 和 ReadWriteVariables 属性字段中添加这些变量。</span><span class="sxs-lookup"><span data-stu-id="ed082-150">If there are any existing variables whose values you want to use in your script, you can add them in the ReadOnlyVariables and ReadWriteVariables property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="ed082-151">在属性字段中添加多个变量时，请用逗号将变量名隔开。</span><span class="sxs-lookup"><span data-stu-id="ed082-151">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="ed082-152">还可以选择多个变量，方法是单击和属性字段旁的省略号 (**...**) `ReadOnlyVariables` 按钮 `ReadWriteVariables` ，然后在 "**选择变量**" 对话框中选择变量。</span><span class="sxs-lookup"><span data-stu-id="ed082-152">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="ed082-153">有关如何在脚本组件中使用变量的常规信息，请参阅[在脚本组件中使用变量](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-153">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="ed082-154">有关“脚本转换编辑器”的“脚本”页的详细信息，请参阅[脚本转换编辑器（“脚本”页）](../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-154">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="ed082-155">在代码设计模式下编写异步转换组件脚本</span><span class="sxs-lookup"><span data-stu-id="ed082-155">Scripting an Asynchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="ed082-156">为组件配置完所有元数据后，可以编写自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="ed082-156">After you have configured all the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="ed082-157">在“脚本转换编辑器”的“脚本”页面中，单击“编辑脚本”打开 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE，可在其中添加自定义脚本    。</span><span class="sxs-lookup"><span data-stu-id="ed082-157">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="ed082-158">编写脚本所使用的语言取决于为“脚本”页上的 **ScriptLanguage** 属性选择 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 还是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作为脚本语言。</span><span class="sxs-lookup"><span data-stu-id="ed082-158">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="ed082-159">有关适用于使用脚本组件创建的所有组件类型的重要信息，请参阅[脚本组件的编码和调试](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ed082-159">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="ed082-160">了解自动生成的代码</span><span class="sxs-lookup"><span data-stu-id="ed082-160">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="ed082-161">创建并配置转换组件后打开 VSTA IDE 时，可编辑的 `ScriptMain` 类将显示在代码编辑器中，其中包含 ProcessInputRow 和 CreateNewOutputRows 方法的存根。</span><span class="sxs-lookup"><span data-stu-id="ed082-161">When you open the VSTA IDE after creating and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with stubs for the ProcessInputRow and the CreateNewOutputRows methods.</span></span> <span data-ttu-id="ed082-162">在 ScriptMain 类中可编写自定义代码，ProcessInputRow 是转换组件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="ed082-162">The ScriptMain class is where you will write your custom code, and ProcessInputRow is the most important method in a transformation component.</span></span> <span data-ttu-id="ed082-163"> 方法通常在源组件中使用，该组件与异步转换相似，因为这两个组件都必须创建自己的输出行。</span><span class="sxs-lookup"><span data-stu-id="ed082-163">The `CreateNewOutputRows` method is more typically used in a source component, which is like an asynchronous transformation in that both components must create their own output rows.</span></span>

 <span data-ttu-id="ed082-164">如果打开 VSTA 的 "**项目资源管理器**" 窗口，可以看到脚本组件还生成了只读 `BufferWrapper` 和 `ComponentWrapper` 项目项。</span><span class="sxs-lookup"><span data-stu-id="ed082-164">If you open the VSTA **Project Explorer** window, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="ed082-165">ScriptMain 类从项目项中的 UserComponent 类继承 `ComponentWrapper` 。</span><span class="sxs-lookup"><span data-stu-id="ed082-165">The ScriptMain class inherits from the UserComponent class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="ed082-166">在运行时，数据流引擎调用类中的 PrimeOutput 方法 `UserComponent` ，该方法重写父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> 方法 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 。</span><span class="sxs-lookup"><span data-stu-id="ed082-166">At run time, the data flow engine calls the PrimeOutput method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="ed082-167">PrimeOutput 方法又调用 CreateNewOutputRows 方法。</span><span class="sxs-lookup"><span data-stu-id="ed082-167">The PrimeOutput method in turn calls the CreateNewOutputRows method.</span></span>

 <span data-ttu-id="ed082-168">随后，数据流引擎调用 UserComponent 类中的 ProcessInput 方法，该方法替代 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ed082-168">Next, the data flow engine invokes the ProcessInput method in the UserComponent class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="ed082-169">而 ProcessInput 方法遍历输入缓冲区中的所有行并为每一行调用一次 ProcessInputRow 方法。</span><span class="sxs-lookup"><span data-stu-id="ed082-169">The ProcessInput method in turn loops through the rows in the input buffer and calls the ProcessInputRow method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="ed082-170">编写自定义代码</span><span class="sxs-lookup"><span data-stu-id="ed082-170">Writing Your Custom Code</span></span>
 <span data-ttu-id="ed082-171">若要完成自定义异步转换组件的创建，必须使用已重写的 ProcessInputRow 方法来处理输入缓冲区每一行中的数据。</span><span class="sxs-lookup"><span data-stu-id="ed082-171">To finish creating a custom asynchronous transformation component, you must use the overridden ProcessInputRow method to process the data in each row of the input buffer.</span></span> <span data-ttu-id="ed082-172">由于输出与输入不同步，因此您必须向输出显式写入数据行。</span><span class="sxs-lookup"><span data-stu-id="ed082-172">Because the outputs are not synchronous to the input, you must explicitly write rows of data to the outputs.</span></span>

 <span data-ttu-id="ed082-173">在异步转换中，可以根据需要在 ProcessInputRow 或 ProcessInput 方法中使用 AddRow 方法向输出添加行。</span><span class="sxs-lookup"><span data-stu-id="ed082-173">In an asynchronous transformation, you can use the AddRow method to add rows to the output as appropriate from within the ProcessInputRow or ProcessInput methods.</span></span> <span data-ttu-id="ed082-174">不一定要使用 CreateNewOutputRows 方法。</span><span class="sxs-lookup"><span data-stu-id="ed082-174">You do not have to use the CreateNewOutputRows method.</span></span> <span data-ttu-id="ed082-175">如果要将单行结果（如聚合结果）写入特定输出，可以使用 CreateNewOutputRows 方法预先创建该输出行，然后在处理完所有输入行之后填充其值。</span><span class="sxs-lookup"><span data-stu-id="ed082-175">If you are writing a single row of results, such as aggregation results, to a particular output, you can create the output row beforehand by using the CreateNewOutputRows method, and fill in its values later after processing all input rows.</span></span> <span data-ttu-id="ed082-176">但是，在 CreateNewOutputRows 方法中创建多个行是没有任何用处的，因为脚本组件只允许使用输入或输出中的当前行。</span><span class="sxs-lookup"><span data-stu-id="ed082-176">However it is not useful to create multiple rows in the CreateNewOutputRows method, because the Script component only lets you use the current row in an input or output.</span></span> <span data-ttu-id="ed082-177">CreateNewOutputRows 方法在源组件中更重要，源组件没有任何输入行要处理。</span><span class="sxs-lookup"><span data-stu-id="ed082-177">The CreateNewOutputRows method is more important in a source component where there are no input rows to process.</span></span>

 <span data-ttu-id="ed082-178">可能还需要重写 ProcessInput 方法本身，以便在遍历输入缓冲区并为每行调用 ProcessInputRow 之前或之后执行附加的预处理或最终处理。</span><span class="sxs-lookup"><span data-stu-id="ed082-178">You may also want to override the ProcessInput method itself, so that you can do additional preliminary or final processing before or after you loop through the input buffer and call ProcessInputRow for each row.</span></span> <span data-ttu-id="ed082-179">例如，本主题中的其中一个代码示例重写 ProcessInput，以将特定城市中的地址数计算为 ProcessInputRow 循环通过行 `.` ，示例在处理完所有行后，将汇总值写入到第二个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-179">For example, one of the code examples in this topic overrides ProcessInput to count the number of addresses in a specific city as ProcessInputRow loops through rows`.` The example writes the summary value to the second output after all rows have been processed.</span></span> <span data-ttu-id="ed082-180">该示例在 ProcessInput 中完成输出，原因是调用 PostExecute 时，输出缓冲区不再可用。</span><span class="sxs-lookup"><span data-stu-id="ed082-180">The example completes the output in ProcessInput because the output buffers are no longer available when PostExecute is called.</span></span>

 <span data-ttu-id="ed082-181">根据用户的要求，可能还需要在 ScriptMain 类中可用的 PreExecute 和 PostExecute 方法中编写脚本来执行任何预处理或最终处理。</span><span class="sxs-lookup"><span data-stu-id="ed082-181">Depending on your requirements, you may also want to write script in the PreExecute and PostExecute methods available in the ScriptMain class to perform any preliminary or final processing.</span></span>

> [!NOTE]
>  <span data-ttu-id="ed082-182">如果是从头开始开发自定义数据流组件的，有一点很重要，即，重写 PrimeOutput 方法来缓存对输出缓冲区的引用，以便稍后能向这些缓冲区添加数据行。</span><span class="sxs-lookup"><span data-stu-id="ed082-182">If you were developing a custom data flow component from scratch, it would be important to override the PrimeOutput method to cache references to the output buffers so that you could add rows of data to the buffers later.</span></span> <span data-ttu-id="ed082-183">在脚本组件中这不是必需的，因为 `BufferWrapper` 项目项中有自动生成的表示每个输出缓冲区的类。</span><span class="sxs-lookup"><span data-stu-id="ed082-183">In the Script component, this is not necessary because you have an automatically generated class representing each output buffer in the `BufferWrapper` project item.</span></span>

## <a name="example"></a><span data-ttu-id="ed082-184">示例</span><span class="sxs-lookup"><span data-stu-id="ed082-184">Example</span></span>
 <span data-ttu-id="ed082-185">此示例演示在 ScriptMain 类中创建异步转换组件所需的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="ed082-185">This example demonstrates the custom code that is required in the ScriptMain class to create an asynchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="ed082-186">这些示例使用 AdventureWorks 示例数据库中的 Person.Address 表并在数据流中传递它的第一列和第四列，即 intAddressID 和 nvarchar(30)City 列     。</span><span class="sxs-lookup"><span data-stu-id="ed082-186">These examples use the **Person.Address** table in the **AdventureWorks** sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="ed082-187">在本节中，在源、转换和目标示例中使用相同的数据。</span><span class="sxs-lookup"><span data-stu-id="ed082-187">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="ed082-188">每个示例的其他前提条件和假设都记录在文档中。</span><span class="sxs-lookup"><span data-stu-id="ed082-188">Additional prerequisites and assumptions are documented for each example.</span></span>

 <span data-ttu-id="ed082-189">此示例演示具有两个输出的异步转换组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-189">This example demonstrates an asynchronous transformation component with two outputs.</span></span> <span data-ttu-id="ed082-190">此转换将 **AddressID** 和 **City** 列传递给一个输出，同时它对位于特定城市 (Redmond, Washington, U.S.A.) 中的地址进行计数，然后将结果值输出到另一个输出。</span><span class="sxs-lookup"><span data-stu-id="ed082-190">This transformation passes through the **AddressID** and **City** columns to one output, while it counts the number of addresses located in a specific city (Redmond, Washington, U.S.A.), and then outputs the resulting value to a second output.</span></span>

 <span data-ttu-id="ed082-191">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="ed082-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="ed082-192">向数据流设计器图面添加新的脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="ed082-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="ed082-193">在设计器中将源或另一转换的输出连接到新转换组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-193">Connect the output of a source or of another transformation to the new transformation component in the designer.</span></span> <span data-ttu-id="ed082-194">此输出应提供 AdventureWorks 示例数据库的 Person.Address 表中的数据，其中至少包含 AddressID 和 City 列。</span><span class="sxs-lookup"><span data-stu-id="ed082-194">This output should provide data from the **Person.Address** table of the **AdventureWorks** sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="ed082-195">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="ed082-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="ed082-196">在“输入列”  页中，选择 AddressID  和 City  列。</span><span class="sxs-lookup"><span data-stu-id="ed082-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="ed082-197">在“输入和输出”\*\*\*\* 页中，向第一个输出添加 **AddressID** 和 **City** 输出列并进行配置。</span><span class="sxs-lookup"><span data-stu-id="ed082-197">On the **Inputs and Outputs** page, add and configure the **AddressID** and **City** output columns on the first output.</span></span> <span data-ttu-id="ed082-198">添加另一个输出，然后向第二个输出添加汇总值的输出列。</span><span class="sxs-lookup"><span data-stu-id="ed082-198">Add a second output, and add an output column for the summary value on the second output.</span></span> <span data-ttu-id="ed082-199">将第一个输出的 SynchronousInputID 属性设置为 0，因为此示例显式将每个输入行复制到第一个输出中。</span><span class="sxs-lookup"><span data-stu-id="ed082-199">Set the SynchronousInputID property of the first output to 0, because this example copies each input row explicitly to the first output.</span></span> <span data-ttu-id="ed082-200">新创建的输出的 SynchronousInputID 属性已经设置为 0。</span><span class="sxs-lookup"><span data-stu-id="ed082-200">The SynchronousInputID property of the newly-created output is already set to 0.</span></span>

5.  <span data-ttu-id="ed082-201">重命名输入、输出和新输出列，使其名称更具说明性。</span><span class="sxs-lookup"><span data-stu-id="ed082-201">Rename the input, the outputs, and the new output column to give them more descriptive names.</span></span> <span data-ttu-id="ed082-202">该示例使用 **MyAddressInput** 作为输入的名称，**MyAddressOutput** 和 **MySummaryOutput** 作为输出的名称，**MyRedmondCount** 作为第二个输出中的输出列的名称。</span><span class="sxs-lookup"><span data-stu-id="ed082-202">The example uses **MyAddressInput** as the name of the input, **MyAddressOutput** and **MySummaryOutput** for the outputs, and **MyRedmondCount** for the output column on the second output.</span></span>

6.  <span data-ttu-id="ed082-203">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="ed082-203">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="ed082-204">然后关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="ed082-204">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="ed082-205">为需要 **AddressID** 和 **City** 列的第一个输出创建和配置一个目标组件，例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标或[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中演示的示例目标组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-205">Create and configure a destination component for the first output that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), .</span></span> <span data-ttu-id="ed082-206">然后将该转换的第一个输出，即 **MyAddressOutput**，连接到目标组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-206">Then connect the first output of the transformation, **MyAddressOutput**, to the destination component.</span></span> <span data-ttu-id="ed082-207">在 AdventureWorks 数据库中运行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令，以创建目标表：</span><span class="sxs-lookup"><span data-stu-id="ed082-207">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the **AdventureWorks** database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="ed082-208">为第二个输出创建和配置另一个目标组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-208">Create and configure another destination component for the second output.</span></span> <span data-ttu-id="ed082-209">然后将该转换的第二个输出，即 **MySummaryOutput**，连接到该目标组件。</span><span class="sxs-lookup"><span data-stu-id="ed082-209">Then connect the second output of the transformation, **MySummaryOutput**, to the destination component.</span></span> <span data-ttu-id="ed082-210">由于第二个输出写入只带有一个值的一行，因此可以轻松对目标配置一个连接到只含一列的新文件的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ed082-210">Because the second output writes a single row with a single value, you can easily configure a destination with a Flat File connection manager that connects to a new file that has a single column.</span></span> <span data-ttu-id="ed082-211">在该示例中，此目标列名为 **MyRedmondCount**。</span><span class="sxs-lookup"><span data-stu-id="ed082-211">In the example, this destination column is named **MyRedmondCount**.</span></span>

9. <span data-ttu-id="ed082-212">运行该示例。</span><span class="sxs-lookup"><span data-stu-id="ed082-212">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Private myRedmondAddressCount As Integer

    Public Overrides Sub CreateNewOutputRows()

        MySummaryOutputBuffer.AddRow()

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)

        While Buffer.NextRow()
            MyAddressInput_ProcessInputRow(Buffer)
        End While

        If Buffer.EndOfRowset Then
            MyAddressOutputBuffer.SetEndOfRowset()
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount
            MySummaryOutputBuffer.SetEndOfRowset()
        End If

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With MyAddressOutputBuffer
            .AddRow()
            .AddressID = Row.AddressID
            .City = Row.City
        End With

        If Row.City.ToUpper = "REDMOND" Then
            myRedmondAddressCount += 1
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    private int myRedmondAddressCount;

    public override void CreateNewOutputRows()
    {

        MySummaryOutputBuffer.AddRow();

    }

    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)
    {

        while (Buffer.NextRow())
        {
            MyAddressInput_ProcessInputRow(Buffer);
        }

        if (Buffer.EndOfRowset())
        {
            MyAddressOutputBuffer.SetEndOfRowset();
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;
            MySummaryOutputBuffer.SetEndOfRowset();
        }

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            MyAddressOutputBuffer.AddRow();
            MyAddressOutputBuffer.AddressID = Row.AddressID;
            MyAddressOutputBuffer.City = Row.City;
        }

        if (Row.City.ToUpper() == "REDMOND")
        {
            myRedmondAddressCount += 1;
        }

    }

}

```

<span data-ttu-id="ed082-213">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ed082-213">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ed082-214">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="ed082-214">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ed082-215">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="ed082-215">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ed082-216">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="ed082-216">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed082-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed082-217">See Also</span></span>
 <span data-ttu-id="ed082-218">[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)[使用脚本组件创建同步转换](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)[开发具有异步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="ed082-218">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span></span>


