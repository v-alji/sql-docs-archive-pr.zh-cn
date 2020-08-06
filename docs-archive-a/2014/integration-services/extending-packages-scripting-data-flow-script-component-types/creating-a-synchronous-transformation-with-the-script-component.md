---
title: 使用脚本组件创建同步转换 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34252f1caba4e2c1b3b99788d32527a33793b6ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587473"
---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a><span data-ttu-id="8f3ec-102">使用脚本组件创建同步转换</span><span class="sxs-lookup"><span data-stu-id="8f3ec-102">Creating a Synchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="8f3ec-103">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中使用转换组件可以在数据从源传递到目标时修改和分析该数据。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="8f3ec-104">具有同步输出的转换在每个输入行传递给该组件时对该行进行处理。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="8f3ec-105">具有异步输出的转换在等到接收所有输入行之后才能完成处理。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-105">A transformation with asynchronous outputs waits until it has received all input rows to complete its processing.</span></span> <span data-ttu-id="8f3ec-106">本主题讨论同步转换。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-106">This topic discusses a synchronous transformation.</span></span> <span data-ttu-id="8f3ec-107">有关异步转换的信息，请参阅[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-107">For information about asynchronous transformations, see [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span> <span data-ttu-id="8f3ec-108">有关同步组件和异步组件之间的差异的详细信息，请参阅[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-108">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="8f3ec-109">有关脚本组件的概述，请参阅[使用脚本组件扩展数据流](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="8f3ec-110">脚本组件及其生成的基础结构代码可以大大简化自定义数据流组件的开发过程。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-110">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="8f3ec-111">但是，若要了解脚本组件的工作方式，读取以下步骤很有帮助，这些步骤是在[开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)部分，特别是在[开发具有同步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)部分开发自定义数据流组件必须遵循的。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-111">However, to understand how the Script component works, you may find it useful to read the steps that you must follow in developing a custom data flow component in the section on [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-a-synchronous-transformation-component"></a><span data-ttu-id="8f3ec-112">开始一个同步转换组件</span><span class="sxs-lookup"><span data-stu-id="8f3ec-112">Getting Started with a Synchronous Transformation Component</span></span>
 <span data-ttu-id="8f3ec-113">向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“数据流”窗格添加脚本组件时，“选择脚本组件类型”  对话框将打开，并提示选择源、目标或转换组件类型。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-113">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation component type.</span></span> <span data-ttu-id="8f3ec-114">在此对话框中，选择“转换”  。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="8f3ec-115">在元数据设计模式下配置同步转换组件</span><span class="sxs-lookup"><span data-stu-id="8f3ec-115">Configuring a Synchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="8f3ec-116">选择创建转换组件的选项后，可使用“脚本转换编辑器”  配置该组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="8f3ec-117">有关详细信息，请参阅[在脚本组件编辑器中配置脚本组件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="8f3ec-118">若要设置脚本组件的脚本语言，请在“脚本转换编辑器”的“脚本”页上设置“ScriptLanguage”属性。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-118">To set the script language for the Script component, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="8f3ec-119">若要设置脚本组件的默认脚本语言，请使用“选项”对话框的“常规”页上的“脚本语言”选项。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="8f3ec-120">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="8f3ec-121">数据流转换组件有一个输入并支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-121">A data flow transformation component has one input, and supports one or more outputs.</span></span> <span data-ttu-id="8f3ec-122">在写入自定义脚本之前，必须在元数据设计模式下完成的一个步骤是使用“脚本转换编辑器”  配置组件的输入和输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-122">Configuring the input and outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="8f3ec-123">配置输入列</span><span class="sxs-lookup"><span data-stu-id="8f3ec-123">Configuring Input Columns</span></span>
 <span data-ttu-id="8f3ec-124">转换组件具有一个输入。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-124">A transformation component has one input.</span></span>

 <span data-ttu-id="8f3ec-125">在“脚本转换编辑器”的“输入列”页中，列列表显示数据流上游组件的输出中可用的列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-125">On the **Input Columns** page of the **Script Transformation Editor,** the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="8f3ec-126">选择要转换或传递的列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="8f3ec-127">将要就地转换的所有列标记为读/写。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="8f3ec-128">有关“脚本转换编辑器”的“输入列”页的详细信息，请参阅[脚本转换编辑器（“输入列”页）](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="8f3ec-129">配置输入、输出和输出列</span><span class="sxs-lookup"><span data-stu-id="8f3ec-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="8f3ec-130">转换组件支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="8f3ec-131">在“脚本转换编辑器”的“输入和输出”页中，可以看到已创建一个输出，但是还没有创建任何输出列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-131">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you can see that a single output has been created, but the output has no columns.</span></span> <span data-ttu-id="8f3ec-132">在编辑器的这一页，可能需要或希望配置以下各项。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-132">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="8f3ec-133">创建一个或多个附加输出，如包含意外值的行的模拟错误输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-133">Create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="8f3ec-134">使用“添加输出”  和“删除输出”  按钮以管理同步转换组件的输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-134">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your synchronous transformation component.</span></span> <span data-ttu-id="8f3ec-135">所有输入行都定向到所有可用输出，除非您表示希望将每一行重定向到一个输出或其他输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-135">All input rows are directed to all available outputs unless you indicate that you intend to redirect each row to one output or the other.</span></span> <span data-ttu-id="8f3ec-136">您可通过为输出的 `ExclusionGroup` 属性指定一个非零的整数值来表示希望重定向行。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-136">You indicate that you intend to redirect rows by specifying a non-zero integer value for the `ExclusionGroup` property on the outputs.</span></span> <span data-ttu-id="8f3ec-137">在 `ExclusionGroup` 中输入的用于标识输出的特定整数值并不重要，但是您必须对指定的输出组使用同一个整数。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-137">The specific integer value entered in `ExclusionGroup` to identify the outputs is not significant, but you must use the same integer consistently for the specified group of outputs.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="8f3ec-138">当您不希望输出所有行时，还可以对单个输出使用非零 `ExclusionGroup` 属性值。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="8f3ec-139">但是，在这种情况下，你必须为想要发送给输出的每一行显式调用 DirectRowTo\<outputbuffer> 方法。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-139">However, in this case,  you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="8f3ec-140">为输入和输出指定一个更具说明性的名称。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-140">Assign a more descriptive name to the input and outputs.</span></span> <span data-ttu-id="8f3ec-141">脚本组件可以使用这些名称来生成类型化取值函数属性，这些属性用于在脚本中引用输入和输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="8f3ec-142">对于同步转换，将列保持原样。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-142">Leave columns as is for synchronous transformations.</span></span> <span data-ttu-id="8f3ec-143">通常，同步转换不会向数据流添加列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-143">Typically a synchronous transformation does not add columns to the data flow.</span></span> <span data-ttu-id="8f3ec-144">会在缓冲区中就地修改数据，然后将缓冲区传递到数据流的下一个组件中。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-144">Data is modified in place in the buffer, and the buffer is passed on to the next component in the data flow.</span></span> <span data-ttu-id="8f3ec-145">如果是这种情况，您不需要对转换的输出显式添加和配置输出列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-145">If this is the case, you do not have to add and configure output columns explicitly on the transformation's outputs.</span></span> <span data-ttu-id="8f3ec-146">输出显示在编辑器中，并且不包含任何显式定义的列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-146">The outputs appear in the editor without any explicitly defined columns.</span></span>

-   <span data-ttu-id="8f3ec-147">向行级错误的模拟错误输出添加新列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-147">Add new columns to simulated error outputs for row-level errors.</span></span> <span data-ttu-id="8f3ec-148">通常，同一 `ExclusionGroup` 中的多个输出具有一组相同的输出列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-148">Ordinarily multiple outputs in the same `ExclusionGroup` have the same set of output columns.</span></span> <span data-ttu-id="8f3ec-149">但是，如果要创建模拟的错误输出，则可能要添加多个列来包含错误信息。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-149">However, if you are creating a simulated error output, you may want to add more columns to contain error information.</span></span> <span data-ttu-id="8f3ec-150">有关数据流引擎如何处理错误行的信息，请参阅[在数据流组件中使用错误输出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-150">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="8f3ec-151">请注意，在脚本组件中，必须编写您自己的代码以便使用适当的错误信息填充这些附加列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-151">Note that in the Script component you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="8f3ec-152">有关详细信息，请参阅[模拟脚本组件的错误输出](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-152">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="8f3ec-153">有关“脚本转换编辑器”的“输入和输出”页上的详细信息，请参阅[脚本转换编辑器（“输入和输出”页）](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-153">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="8f3ec-154">添加变量</span><span class="sxs-lookup"><span data-stu-id="8f3ec-154">Adding Variables</span></span>
 <span data-ttu-id="8f3ec-155">如果要在脚本中使用现有变量，可以在 " `ReadOnlyVariables` `ReadWriteVariables` **脚本转换编辑器**" 的 "**脚本**" 页上的和属性字段中添加这些变量。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-155">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="8f3ec-156">在属性字段中添加多个变量时，请用逗号将变量名隔开。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-156">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="8f3ec-157">还可以选择多个变量，方法是单击和属性字段旁的省略号 (**...**) `ReadOnlyVariables` 按钮 `ReadWriteVariables` ，然后在 "**选择变量**" 对话框中选择变量。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-157">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="8f3ec-158">有关如何在脚本组件中使用变量的常规信息，请参阅[在脚本组件中使用变量](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-158">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="8f3ec-159">有关“脚本转换编辑器”的“脚本”页的详细信息，请参阅[脚本转换编辑器（“脚本”页）](../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-159">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="8f3ec-160">在代码设计模式下编写同步转换组件脚本</span><span class="sxs-lookup"><span data-stu-id="8f3ec-160">Scripting a Synchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="8f3ec-161">为组件配置完元数据后，可以编写自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-161">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="8f3ec-162">在“脚本转换编辑器”的“脚本”页面中，单击“编辑脚本”打开 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE，可在其中添加自定义脚本    。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-162">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="8f3ec-163">编写脚本所使用的语言取决于为“脚本”页上的 **ScriptLanguage** 属性选择 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 还是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作为脚本语言。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-163">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="8f3ec-164">有关适用于使用脚本组件创建的所有组件类型的重要信息，请参阅[脚本组件的编码和调试](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-164">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="8f3ec-165">了解自动生成的代码</span><span class="sxs-lookup"><span data-stu-id="8f3ec-165">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="8f3ec-166">创建并配置转换组件后打开 VSTA IDE 时，可编辑的 `ScriptMain` 类将显示在代码编辑器中，其中有 `ProcessInputRow` 方法的存根。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-166">When you open the VSTA IDE after you create and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="8f3ec-167">在 `ScriptMain` 类中可编写自定义代码，`ProcessInputRow` 是转换组件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-167">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a transformation component.</span></span>

 <span data-ttu-id="8f3ec-168">如果在 VSTA 中打开 "**项目资源管理器**" 窗口，可以看到脚本组件还生成了只读的 `BufferWrapper` 和 `ComponentWrapper` 项目项。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-168">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="8f3ec-169"> 类从  项目项中的  类继承。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-169">The `ScriptMain` class inherits from the `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="8f3ec-170">在运行时，数据流引擎调用 `ProcessInput` 类中的 `UserComponent` 方法，该方法重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-170">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="8f3ec-171">而 `ProcessInput` 方法遍历输入缓冲区中的所有行并为每一行调用一次 `ProcessInputRow` 方法。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-171">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="8f3ec-172">编写自定义代码</span><span class="sxs-lookup"><span data-stu-id="8f3ec-172">Writing Your Custom Code</span></span>
 <span data-ttu-id="8f3ec-173">具有同步传输的转换组件是要编写的所有数据流组件中最简单的部分。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-173">A transformation component with synchronous outputs is the simplest of all data flow components to write.</span></span> <span data-ttu-id="8f3ec-174">例如，本主题中稍后演示的单个输出示例包含以下自定义代码：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-174">For example, the single-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
```

```csharp
Row.City = (Row.City).ToUpper();

```

 <span data-ttu-id="8f3ec-175">若要完成创建自定义同步转换组件，必须使用已重写的 `ProcessInputRow` 方法来转换输入缓冲区的每行中的数据。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-175">To finish creating a custom synchronous transformation component, you use the overridden `ProcessInputRow` method to transform the data in each row of the input buffer.</span></span> <span data-ttu-id="8f3ec-176">缓冲区写满后，数据流引擎会将此缓冲区传递给数据流中的下一个组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-176">The data flow engine passes this buffer, when full, to the next component in the data flow.</span></span>

 <span data-ttu-id="8f3ec-177">根据需要，您还可以在 `PreExecute` 类中可用的 `PostExecute` 和 `ScriptMain` 方法中编写脚本来执行预处理或最终处理。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-177">Depending on your requirements, you may also want to write script in the `PreExecute` and `PostExecute` methods, available in the `ScriptMain` class, to perform preliminary or final processing.</span></span>

### <a name="working-with-multiple-outputs"></a><span data-ttu-id="8f3ec-178">使用多个输出</span><span class="sxs-lookup"><span data-stu-id="8f3ec-178">Working with Multiple Outputs</span></span>
 <span data-ttu-id="8f3ec-179">将输入行定向到两个或多个可能的输出中的一个输出时所需的自定义代码比之前讨论的单个输出方案所需的代码要少得多。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-179">Directing input rows to one of two or more possible outputs does not require much more custom code than the single-output scenario discussed earlier.</span></span> <span data-ttu-id="8f3ec-180">例如，本主题中稍后演示的两个输出示例包含以下自定义代码：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-180">For example, the two-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
If Row.City = "REDMOND" Then
    Row.DirectRowToMyRedmondAddresses()
Else
    Row.DirectRowToMyOtherAddresses()
End If
```

```csharp
Row.City = (Row.City).ToUpper();

if (Row.City=="REDMOND")
{
    Row.DirectRowToMyRedmondAddresses();
}
else
{
    Row.DirectRowToMyOtherAddresses();
}
```

 <span data-ttu-id="8f3ec-181">在此示例中，脚本组件将基于已配置的输出名称生成 DirectRowTo\<OutputBufferX> 方法。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-181">In this example, the Script component generates the **DirectRowTo\<OutputBufferX>** methods for you, based on the names of the outputs that you configured.</span></span> <span data-ttu-id="8f3ec-182">您可以使用类似的代码将错误行定向到模拟的错误输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-182">You can use similar code to direct error rows to a simulated error output.</span></span>

## <a name="examples"></a><span data-ttu-id="8f3ec-183">示例</span><span class="sxs-lookup"><span data-stu-id="8f3ec-183">Examples</span></span>
 <span data-ttu-id="8f3ec-184">此示例演示在 `ScriptMain` 类中创建同步转换组件所需的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-184">The examples here demonstrate the custom code that is required in the `ScriptMain` class to create a synchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="8f3ec-185">这些示例使用示例数据库中的**Person**表， `AdventureWorks` 并通过数据流传递其第一列和第四列，即**即 intaddressid**和**nvarchar (30) City**列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-185">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="8f3ec-186">在本节中，在源、转换和目标示例中使用相同的数据。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-186">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="8f3ec-187">每个示例的其他前提条件和假设都记录在文档中。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-187">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="single-output-synchronous-transformation-example"></a><span data-ttu-id="8f3ec-188">单个输出同步转换示例</span><span class="sxs-lookup"><span data-stu-id="8f3ec-188">Single Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="8f3ec-189">此示例演示具有单个输出的同步转换组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-189">This example demonstrates a synchronous transformation component with a single output.</span></span> <span data-ttu-id="8f3ec-190">此转换将传递 AddressID  列，并将 City  列转换为大写。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-190">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span>

 <span data-ttu-id="8f3ec-191">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="8f3ec-192">向数据流设计器图面添加新的脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="8f3ec-193">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中将源或另一转换的输出连接到新转换组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-193">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="8f3ec-194">此输出应提供示例数据库的**Person**表中 `AdventureWorks` 包含**AddressID**和**City**列的数据。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-194">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="8f3ec-195">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="8f3ec-196">在“输入列”  页中，选择 AddressID  和 City  列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="8f3ec-197">将 City  列标记为读取/写入。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-197">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="8f3ec-198">在“输入和输出”  页上，使用更具说明性的名称（如 MyAddressInput  和 MyAddressOutput  重命名输入和输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-198">On the **Inputs and Outputs** page, rename the input and output with more descriptive names, such as **MyAddressInput** and **MyAddressOutput**.</span></span> <span data-ttu-id="8f3ec-199">请注意，输出的 `SynchronousInputID` 与输入的 `ID` 相对应。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-199">Notice that the `SynchronousInputID` of the output corresponds to the `ID` of the input.</span></span> <span data-ttu-id="8f3ec-200">因此，您不需要添加和配置输出列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-200">Therefore you do not have to add and configure output columns.</span></span>

5.  <span data-ttu-id="8f3ec-201">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-201">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="8f3ec-202">然后关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-202">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="8f3ec-203">创建并配置目标组件，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标或 [使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md) 中演示的示例目标组件，该目标组件需要 AddressID 和 City 列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-203">Create and configure a destination component that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="8f3ec-204">然后，将转换的输出连接到目标组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-204">Then connect the output of the transformation to the destination component.</span></span> <span data-ttu-id="8f3ec-205">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 数据库中运行以下 `AdventureWorks` 命令，以创建目标表：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-205">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="8f3ec-206">运行该示例。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-206">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

    }

}
```

### <a name="two-output-synchronous-transformation-example"></a><span data-ttu-id="8f3ec-207">两个输出同步转换示例</span><span class="sxs-lookup"><span data-stu-id="8f3ec-207">Two-Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="8f3ec-208">此示例演示具有两个输出的同步转换组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-208">This example demonstrates a synchronous transformation component with two outputs.</span></span> <span data-ttu-id="8f3ec-209">此转换将传递 AddressID  列，并将 City  列转换为大写。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-209">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span> <span data-ttu-id="8f3ec-210">如果城市名为 Redmond，则将行定向到一个输出；将所有其他行定向到另一个输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-210">If the city name is Redmond, it directs the row to one output; it directs all other rows to another output.</span></span>

 <span data-ttu-id="8f3ec-211">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-211">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="8f3ec-212">向数据流设计器图面添加新的脚本组件并将其配置为转换。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-212">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="8f3ec-213">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中将源或另一转换的输出连接到新转换组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-213">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="8f3ec-214">此输出应提供示例数据库的**Person**表中的数据， `AdventureWorks` 其中至少包含**AddressID**和**City**列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-214">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="8f3ec-215">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-215">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="8f3ec-216">在“输入列”  页中，选择 AddressID  和 City  列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-216">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="8f3ec-217">将 City  列标记为读取/写入。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-217">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="8f3ec-218">在“输入和输出”  页中，创建第二个输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-218">On the **Inputs and Outputs** page, create a second output.</span></span> <span data-ttu-id="8f3ec-219">添加新的输出后，请确保将该输出的 `SynchronousInputID` 设置为输入的 `ID`。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-219">After you add the new output, make sure that you set its `SynchronousInputID` to the `ID` of the input.</span></span> <span data-ttu-id="8f3ec-220">已对第一个输出设置此属性，该输出是默认创建的。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-220">This property is already set on the first output, which is created by default.</span></span> <span data-ttu-id="8f3ec-221">对于每个输出，将 `ExclusionGroup` 属性设置为同一非零值，以指示您将在两个互相排斥的输出间拆分输入行。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-221">For each output, set the `ExclusionGroup` property to the same non-zero value to indicate that you will split the input rows between two mutually exclusive outputs.</span></span> <span data-ttu-id="8f3ec-222">无需向输出添加任何输出列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-222">You do not have to add any output columns to the outputs.</span></span>

5.  <span data-ttu-id="8f3ec-223">使用更具说明性的名称（如 MyAddressInput  、MyRedmondAddresses  和 MyOtherAddresses  ）重命名输入和输出。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-223">Rename the input and outputs with more descriptive names, such as **MyAddressInput**, **MyRedmondAddresses**, and **MyOtherAddresses**.</span></span>

6.  <span data-ttu-id="8f3ec-224">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-224">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="8f3ec-225">然后关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-225">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="8f3ec-226">创建并配置两个目标组件，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标、平面文件目标或在[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中演示的示例目标组件，这两个目标组件需要 AddressID 和 City 列。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-226">Create and configure two destination components that expect the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, a Flat File destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="8f3ec-227">然后，将转换的每个输出连接到任一目标组件。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-227">Then connect each of the outputs of the transformation to one of the destination components.</span></span> <span data-ttu-id="8f3ec-228">可通过在 `AdventureWorks` 数据库中运行与下列命令（具有唯一表名）类似的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令来创建目标表：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-228">You can create destination tables by running a [!INCLUDE[tsql](../../includes/tsql-md.md)] command similar to the following (with unique table names) in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2](
        [AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL
    ```

8.  <span data-ttu-id="8f3ec-229">运行该示例。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-229">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

        If Row.City = "REDMOND" Then
            Row.DirectRowToMyRedmondAddresses()
        Else
            Row.DirectRowToMyOtherAddresses()
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

        if (Row.City == "REDMOND")
        {
            Row.DirectRowToMyRedmondAddresses();
        }
        else
        {
            Row.DirectRowToMyOtherAddresses();
        }

    }
}
```

<span data-ttu-id="8f3ec-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **随时了解 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="8f3ec-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8f3ec-231">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="8f3ec-231">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8f3ec-232">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="8f3ec-232">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8f3ec-233">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="8f3ec-233">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f3ec-234">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f3ec-234">See Also</span></span>
 <span data-ttu-id="8f3ec-235">[了解同步和异步转换](../understanding-synchronous-and-asynchronous-transformations.md)[使用脚本组件创建异步转换](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)[开发具有同步输出的自定义转换组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="8f3ec-235">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span></span>


