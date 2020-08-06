---
title: 使用脚本组件创建源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], source components
- output columns [Integration Services]
- sources [Integration Services], components
ms.assetid: 547c4179-ea82-4265-8c6f-04a2aa77a3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a352348f7f47157c5f2ec6d3ff01cea47de0ffb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587475"
---
# <a name="creating-a-source-with-the-script-component"></a><span data-ttu-id="32644-102">使用脚本组件创建源</span><span class="sxs-lookup"><span data-stu-id="32644-102">Creating a Source with the Script Component</span></span>
  <span data-ttu-id="32644-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中的源组件用于从数据源加载数据以传递到下游转换和目标。</span><span class="sxs-lookup"><span data-stu-id="32644-103">You use a source component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to load data from a data source to pass on to downstream transformations and destinations.</span></span> <span data-ttu-id="32644-104">通常通过现有连接管理器连接数据源。</span><span class="sxs-lookup"><span data-stu-id="32644-104">Ordinarily you connect to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="32644-105">有关脚本组件的概述，请参阅 [使用脚本组件扩展数据流] (。/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="32644-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="32644-106">脚本组件及其生成的基础结构代码可以大大简化自定义数据流组件的开发过程。</span><span class="sxs-lookup"><span data-stu-id="32644-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="32644-107">但要了解脚本组件的工作原理，熟悉自定义数据流组件的开发步骤很有帮助。</span><span class="sxs-lookup"><span data-stu-id="32644-107">However, to understand how the Script component works, you may find it useful to read through the steps that are involved in developing a custom data flow component.</span></span> <span data-ttu-id="32644-108">请参阅[开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)部分，特别是主题[开发自定义源组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-108">See the section [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), especially the topic [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="getting-started-with-a-source-component"></a><span data-ttu-id="32644-109">开始一个源组件</span><span class="sxs-lookup"><span data-stu-id="32644-109">Getting Started with a Source Component</span></span>
 <span data-ttu-id="32644-110">向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“数据流”窗格添加脚本组件时，“选择脚本组件类型”对话框将打开并提示你选择“源”、“目标”或“转换”脚本  。</span><span class="sxs-lookup"><span data-stu-id="32644-110">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation script.</span></span> <span data-ttu-id="32644-111">在此对话框中选择“源”  。</span><span class="sxs-lookup"><span data-stu-id="32644-111">In this dialog box, select **Source**.</span></span>

## <a name="configuring-a-source-component-in-metadata-design-mode"></a><span data-ttu-id="32644-112">在元数据设计模式下配置源组件</span><span class="sxs-lookup"><span data-stu-id="32644-112">Configuring a Source Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="32644-113">选择创建源组件后，可使用“脚本转换编辑器”配置该组件  。</span><span class="sxs-lookup"><span data-stu-id="32644-113">After selecting to create a source component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="32644-114">有关详细信息，请参阅[在脚本组件编辑器中配置脚本组件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-114">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="32644-115">数据流源组件没有输入，支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="32644-115">A data flow source component has no inputs and supports one or more outputs.</span></span> <span data-ttu-id="32644-116">在编写自定义脚本之前，必须在元数据设计模式下完成的一个步骤是使用“脚本转换编辑器”配置组件的输出  。</span><span class="sxs-lookup"><span data-stu-id="32644-116">Configuring the outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

 <span data-ttu-id="32644-117">还可以在“脚本转换编辑器”的“脚本”页上设置 ScriptLanguage 属性来指定脚本语言    。</span><span class="sxs-lookup"><span data-stu-id="32644-117">You can also specify the script language by setting the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="32644-118">若要设置脚本组件和脚本任务的默认脚本语言，请使用“选项”对话框的“常规”页上的“脚本语言”选项    。</span><span class="sxs-lookup"><span data-stu-id="32644-118">To set the default script language for Script components and Script Tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="32644-119">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-119">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="32644-120">添加连接管理器</span><span class="sxs-lookup"><span data-stu-id="32644-120">Adding Connection Managers</span></span>
 <span data-ttu-id="32644-121">源组件通常使用现有连接管理器连接将其中的数据加载到数据流的数据源。</span><span class="sxs-lookup"><span data-stu-id="32644-121">Ordinarily a source component uses an existing connection manager to connect to the data source from which it loads data into the data flow.</span></span> <span data-ttu-id="32644-122">在“脚本转换编辑器”  的“连接管理器”  页中，单击“添加”  以添加适当的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="32644-122">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="32644-123">但是，连接管理器只是一个封装和存储连接特定类型数据源必需信息的便利单元。</span><span class="sxs-lookup"><span data-stu-id="32644-123">However, a connection manager is only a convenient unit that encapsulates and stores the information that it must have to connect to a data source of a particular type.</span></span> <span data-ttu-id="32644-124">您必须编写自己的自定义代码才能加载或保存数据，并且才有可能打开和关闭与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="32644-124">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source also.</span></span>

 <span data-ttu-id="32644-125">有关如何在脚本组件中使用连接管理器的常规信息，请参阅[在脚本组件中连接数据源](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-125">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="32644-126">有关“脚本转换编辑器”  的“连接管理器”  页的详细信息，请参阅[脚本转换编辑器（“连接管理器”页）](../script-transformation-editor-connection-managers-page.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-126">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-outputs-and-output-columns"></a><span data-ttu-id="32644-127">配置输出和输出列</span><span class="sxs-lookup"><span data-stu-id="32644-127">Configuring Outputs and Output Columns</span></span>
 <span data-ttu-id="32644-128">源组件没有输入，支持一个或多个输出。</span><span class="sxs-lookup"><span data-stu-id="32644-128">A source component has no inputs and supports one or more outputs.</span></span> <span data-ttu-id="32644-129">在“脚本转换编辑器”的“输入和输出”页中，已默认创建一个输出，但是还没有创建任何输出列   。</span><span class="sxs-lookup"><span data-stu-id="32644-129">On the **Inputs and Outputs** page of the **Script Transformation Editor**, a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="32644-130">在编辑器的这一页，可能需要或希望配置以下各项。</span><span class="sxs-lookup"><span data-stu-id="32644-130">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="32644-131">必须为每个输出手动添加和配置输出列。</span><span class="sxs-lookup"><span data-stu-id="32644-131">You must add and configure output columns manually for each output.</span></span> <span data-ttu-id="32644-132">为每个输出选择“输出列”文件夹，然后使用“添加列”和“删除列”按钮管理源组件的每个输出的输出列   。</span><span class="sxs-lookup"><span data-stu-id="32644-132">Select the Output Columns folder for each output, and then use the **Add Column** and **Remove Column** buttons to manage the output columns for each output of the source component.</span></span> <span data-ttu-id="32644-133">随后，将使用在自动生成的代码中创建的类型化取值函数属性，在脚本中通过您在此处指定的名称来引用输出列。</span><span class="sxs-lookup"><span data-stu-id="32644-133">Later, you will refer to the output columns in your script by the names that you assign here, by using the typed accessor properties created for you in the auto-generated code.</span></span>

-   <span data-ttu-id="32644-134">您可能希望创建一个或多个附加输出，如包含意外值的行的模拟错误输出。</span><span class="sxs-lookup"><span data-stu-id="32644-134">You may want to create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="32644-135">使用“添加输出”和“删除输出”按钮可以管理源组件的输出   。</span><span class="sxs-lookup"><span data-stu-id="32644-135">Use the **Add Output** and **Remove Output** buttons to manage the outputs of the source component.</span></span> <span data-ttu-id="32644-136">所有输入行都定向到所有可用输出，除非您还为以下一些输出的 `ExclusionGroup` 属性指定了相同的非零值，您要在这些输出中将每一行只定向到共享同一 `ExclusionGroup` 值的输出之一。</span><span class="sxs-lookup"><span data-stu-id="32644-136">All input rows are directed to all available outputs unless you also specify an identical non-zero value for the `ExclusionGroup` property of those outputs where you intend to direct each row to only one of the outputs that share the same `ExclusionGroup` value.</span></span> <span data-ttu-id="32644-137">用于标识 `ExclusionGroup` 的所选特定整数值没有特殊要求。</span><span class="sxs-lookup"><span data-stu-id="32644-137">The particular integer value selected to identify the `ExclusionGroup` is not significant.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="32644-138">当您不希望输出所有行时，还可以对单个输出使用非零 `ExclusionGroup` 属性值。</span><span class="sxs-lookup"><span data-stu-id="32644-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="32644-139">但是，在这种情况下，必须为希望发送给输出的每一行显式调用 DirectRowTo\<outputbuffer> 方法。</span><span class="sxs-lookup"><span data-stu-id="32644-139">In this case, however, you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="32644-140">您可以为输出指定一个友好名称。</span><span class="sxs-lookup"><span data-stu-id="32644-140">You may want to assign a friendly name to the outputs.</span></span> <span data-ttu-id="32644-141">随后，将使用在自动生成的代码中创建的类型化取值函数属性，在脚本中通过输出的名称来引用输出。</span><span class="sxs-lookup"><span data-stu-id="32644-141">Later, you will refer to the outputs by their names in your script, by using the typed accessor properties created for you in the auto-generated code.</span></span>

-   <span data-ttu-id="32644-142">通常，同一 `ExclusionGroup` 中的多个输出具有相同的输出列。</span><span class="sxs-lookup"><span data-stu-id="32644-142">Ordinarily multiple outputs in the same `ExclusionGroup` have the same output columns.</span></span> <span data-ttu-id="32644-143">但是，如果要创建模拟的错误输出，则可能要添加多个列来存储错误信息。</span><span class="sxs-lookup"><span data-stu-id="32644-143">However, if you are creating a simulated error output, you may want to add more columns to store error information.</span></span> <span data-ttu-id="32644-144">有关数据流引擎如何处理错误行的信息，请参阅[在数据流组件中使用错误输出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-144">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="32644-145">但是，在脚本组件中，必须编写您自己的代码以便使用适当的错误信息填充这些附加列。</span><span class="sxs-lookup"><span data-stu-id="32644-145">In the Script component, however, you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="32644-146">有关详细信息，请参阅[模拟脚本组件的错误输出](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-146">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="32644-147">有关“脚本转换编辑器”  的“输入和输出”  页上的详细信息，请参阅[脚本转换编辑器（“输入和输出”页）](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-147">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="32644-148">添加变量</span><span class="sxs-lookup"><span data-stu-id="32644-148">Adding Variables</span></span>
 <span data-ttu-id="32644-149">如果要在脚本中使用任何现有变量的值，可以在 " `ReadOnlyVariables` `ReadWriteVariables` **脚本转换编辑器**" 的 "**脚本**" 页上的和属性字段中添加这些变量。</span><span class="sxs-lookup"><span data-stu-id="32644-149">If there are any existing variables whose values you want to use in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="32644-150">在属性字段中输入多个变量时，请用逗号将变量名隔开。</span><span class="sxs-lookup"><span data-stu-id="32644-150">When you enter multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="32644-151">您还可以通过单击和属性字段旁的省略号 (**...**) 按钮输入多个变量， `ReadOnlyVariables` 然后在 `ReadWriteVariables` "**选择变量**" 对话框中选择变量。</span><span class="sxs-lookup"><span data-stu-id="32644-151">You can also enter multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields and selecting variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="32644-152">有关如何在脚本组件中使用变量的常规信息，请参阅[在脚本组件中使用变量](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-152">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="32644-153">有关“脚本转换编辑器”的“脚本”页的详细信息，请参阅[脚本转换编辑器（“脚本”页）](../script-transformation-editor-script-page.md)   。</span><span class="sxs-lookup"><span data-stu-id="32644-153">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-source-component-in-code-design-mode"></a><span data-ttu-id="32644-154">在代码设计模式下编写源组件脚本</span><span class="sxs-lookup"><span data-stu-id="32644-154">Scripting a Source Component in Code-Design Mode</span></span>
 <span data-ttu-id="32644-155">为组件配置完元数据后，可以打开 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE 编写自定义脚本的代码。</span><span class="sxs-lookup"><span data-stu-id="32644-155">After you have configured the metadata for your component, open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE to code your custom script.</span></span> <span data-ttu-id="32644-156">若要打开 VSTA，请在“脚本转换编辑器”的“脚本”页中，单击“编辑脚本”    。</span><span class="sxs-lookup"><span data-stu-id="32644-156">To open VSTA, click **Edit Script** on the **Script** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="32644-157">可使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 编写你的脚本，具体取决于为 ScriptLanguage 属性选择的脚本语言  。</span><span class="sxs-lookup"><span data-stu-id="32644-157">You can write your script by using either [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#, depending on the script language selected for the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="32644-158">有关适用于使用脚本组件创建的所有组件类型的重要信息，请参阅[脚本组件的编码和调试](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="32644-158">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="32644-159">了解自动生成的代码</span><span class="sxs-lookup"><span data-stu-id="32644-159">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="32644-160">创建并配置源组件后打开 VSTA IDE 时，可编辑的 `ScriptMain` 类将显示在代码编辑器中。</span><span class="sxs-lookup"><span data-stu-id="32644-160">When you open the VSTA IDE after creating and configuring a source component, the editable `ScriptMain` class appears in the code editor.</span></span> <span data-ttu-id="32644-161">您将在 `ScriptMain` 类中编写您的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="32644-161">You write your custom code in the `ScriptMain` class.</span></span>

 <span data-ttu-id="32644-162">`ScriptMain` 类包含 `CreateNewOutputRows` 方法的存根。</span><span class="sxs-lookup"><span data-stu-id="32644-162">The `ScriptMain` class includes a stub for the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="32644-163"> 是源组件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="32644-163">The `CreateNewOutputRows` is the most important method in a source component.</span></span>

 <span data-ttu-id="32644-164">如果在 VSTA 中打开 "**项目资源管理器**" 窗口，可以看到脚本组件还生成了只读的 `BufferWrapper` 和 `ComponentWrapper` 项目项。</span><span class="sxs-lookup"><span data-stu-id="32644-164">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="32644-165">`ScriptMain` 类从 `UserComponent` 项目项中的 `ComponentWrapper` 类继承。</span><span class="sxs-lookup"><span data-stu-id="32644-165">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="32644-166">在运行时，数据流引擎调用 `PrimeOutput` 类中的 `UserComponent` 方法，该方法重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> 父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="32644-166">At run time, the data flow engine invokes the `PrimeOutput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="32644-167">`PrimeOutput` 方法又调用下列方法：</span><span class="sxs-lookup"><span data-stu-id="32644-167">The `PrimeOutput` method in turn calls the following methods:</span></span>

1.  <span data-ttu-id="32644-168">`CreateNewOutputRows` 方法，在 `ScriptMain` 中要重写该方法，以将数据源中的行添加到最初为空的输出缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="32644-168">The `CreateNewOutputRows` method, which you override in `ScriptMain` to add rows from the data source to the output buffers, which are empty at first.</span></span>

2.  <span data-ttu-id="32644-169"> 方法，默认情况下，该方法为空。</span><span class="sxs-lookup"><span data-stu-id="32644-169">The `FinishOutputs` method, which is empty by default.</span></span> <span data-ttu-id="32644-170">在 `ScriptMain` 中要重写此方法，以执行完成输出所需的任何处理。</span><span class="sxs-lookup"><span data-stu-id="32644-170">Override this method in `ScriptMain` to perform any processing that is required to complete the output.</span></span>

3.  <span data-ttu-id="32644-171">私有的 `MarkOutputsAsFinished` 方法，该方法调用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> 父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 方法来向数据流引擎指示输出已完成。</span><span class="sxs-lookup"><span data-stu-id="32644-171">The private `MarkOutputsAsFinished` method, which calls the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.SetEndOfRowset%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> parent class to indicate to the data flow engine that the output is finished.</span></span> <span data-ttu-id="32644-172">您无需在自己的代码中显式调用 `SetEndOfRowset`。</span><span class="sxs-lookup"><span data-stu-id="32644-172">You do not have to call `SetEndOfRowset` explicitly in your own code.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="32644-173">编写自定义代码</span><span class="sxs-lookup"><span data-stu-id="32644-173">Writing Your Custom Code</span></span>
 <span data-ttu-id="32644-174">为了完成创建自定义源组件，您可以在 `ScriptMain` 类的以下方法中编写脚本。</span><span class="sxs-lookup"><span data-stu-id="32644-174">To finish creating a custom source component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="32644-175">重写 `AcquireConnections` 方法以连接外部数据源。</span><span class="sxs-lookup"><span data-stu-id="32644-175">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="32644-176">从连接管理器中提取连接对象或者需要的连接信息。</span><span class="sxs-lookup"><span data-stu-id="32644-176">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="32644-177">如果可同时加载所有源数据，请重写 `PreExecute` 方法以加载数据。</span><span class="sxs-lookup"><span data-stu-id="32644-177">Override the `PreExecute` method to load data, if you can load all the source data at the same time.</span></span> <span data-ttu-id="32644-178">例如，可以对连接到 `SqlCommand` 数据库的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，然后同时将所有源数据加载到 `SqlDataReader` 中。</span><span class="sxs-lookup"><span data-stu-id="32644-178">For example, you can execute a `SqlCommand` against an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and load all the source data at the same time into a `SqlDataReader`.</span></span> <span data-ttu-id="32644-179">如果必须每次加载一行源数据（例如，读取文本文件时），则可在 `CreateNewOutputRows` 中遍历行时加载数据。</span><span class="sxs-lookup"><span data-stu-id="32644-179">If you must load the source data one row at a time (for example, when reading a text file), you can load the data as you loop through rows in `CreateNewOutputRows`.</span></span>

3.  <span data-ttu-id="32644-180">使用重写的 `CreateNewOutputRows` 方法将新行添加到空的输出缓冲区中，然后在新输出行的每列中填充值。</span><span class="sxs-lookup"><span data-stu-id="32644-180">Use the overridden `CreateNewOutputRows` method to add new rows to the empty output buffers and to fill in the values of each column in the new output rows.</span></span> <span data-ttu-id="32644-181">使用每个输出缓冲区的 `AddRow` 方法来添加空的新行，然后设置每列的值。</span><span class="sxs-lookup"><span data-stu-id="32644-181">Use the `AddRow` method of each output buffer to add an empty new row, and then set the values of each column.</span></span> <span data-ttu-id="32644-182">通常，从外部源所加载的列复制值。</span><span class="sxs-lookup"><span data-stu-id="32644-182">Typically you copy values from the columns loaded from the external source.</span></span>

4.  <span data-ttu-id="32644-183">重写 `PostExecute` 方法以完成数据处理。</span><span class="sxs-lookup"><span data-stu-id="32644-183">Override the `PostExecute` method to finish processing the data.</span></span> <span data-ttu-id="32644-184">例如，可以关闭用于加载数据的 `SqlDataReader`。</span><span class="sxs-lookup"><span data-stu-id="32644-184">For example, you can close the `SqlDataReader` that you used to load data.</span></span>

5.  <span data-ttu-id="32644-185">如果需要，重写 `ReleaseConnections` 方法以断开与外部数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="32644-185">Override the `ReleaseConnections` method to disconnect from the external data source, if required.</span></span>

## <a name="examples"></a><span data-ttu-id="32644-186">示例</span><span class="sxs-lookup"><span data-stu-id="32644-186">Examples</span></span>
 <span data-ttu-id="32644-187">下面的示例演示在 `ScriptMain` 类中创建源组件所需的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="32644-187">The following examples demonstrate the custom code that is required in the `ScriptMain` class to create a source component.</span></span>

> [!NOTE]
>  <span data-ttu-id="32644-188">这些示例使用示例数据库中的**Person**表， `AdventureWorks` 并通过数据流传递其第一列和第四列，即**即 intaddressid**和**nvarchar (30) City**列。</span><span class="sxs-lookup"><span data-stu-id="32644-188">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="32644-189">在本节中，在源、转换和目标示例中使用相同的数据。</span><span class="sxs-lookup"><span data-stu-id="32644-189">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="32644-190">每个示例的其他前提条件和假设都记录在文档中。</span><span class="sxs-lookup"><span data-stu-id="32644-190">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-source-example"></a><span data-ttu-id="32644-191">ADO.NET 源示例</span><span class="sxs-lookup"><span data-stu-id="32644-191">ADO.NET Source Example</span></span>
 <span data-ttu-id="32644-192">本示例演示了使用现有 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的数据加载到数据流中的源组件。</span><span class="sxs-lookup"><span data-stu-id="32644-192">This example demonstrates a source component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to load data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table into the data flow.</span></span>

 <span data-ttu-id="32644-193">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="32644-193">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="32644-194">创建使用 `SqlClient` 访问接口连接 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 数据库的 `AdventureWorks` 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="32644-194">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="32644-195">向数据流设计器图面添加新的脚本组件并将其配置为源。</span><span class="sxs-lookup"><span data-stu-id="32644-195">Add a new Script component to the Data Flow designer surface and configure it as a source.</span></span>

3.  <span data-ttu-id="32644-196">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32644-196">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="32644-197">在“输入和输出”页中，用更具说明性的名称（如 MyAddressOutput）重命名默认输出，然后添加并配置两个输出列 AddressID 和 City     。</span><span class="sxs-lookup"><span data-stu-id="32644-197">On the **Inputs and Outputs** page, rename the default output with a more descriptive name such as **MyAddressOutput**, and add and configure the two output columns, **AddressID** and **City**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="32644-198">确保将 City 输出列的数据类型更改为 DT_WSTR  。</span><span class="sxs-lookup"><span data-stu-id="32644-198">Be sure to change the data type of the **City** output column to DT_WSTR.</span></span>

4.  <span data-ttu-id="32644-199">在“连接管理器”页中，添加或创建 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器，并以诸如 MyADONETConnection 的名称命名   。</span><span class="sxs-lookup"><span data-stu-id="32644-199">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager and give it a name such as **MyADONETConnection**.</span></span>

5.  <span data-ttu-id="32644-200">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="32644-200">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="32644-201">然后关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32644-201">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="32644-202">创建并配置目标组件，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，或者[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中演示的示例目标组件，该组件需要 AddressID 和 City 列   。</span><span class="sxs-lookup"><span data-stu-id="32644-202">Create and configure a destination component, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), that expects the **AddressID** and **City** columns.</span></span> <span data-ttu-id="32644-203">然后将源组件连接到目标。</span><span class="sxs-lookup"><span data-stu-id="32644-203">Then connect the source component to the destination.</span></span> <span data-ttu-id="32644-204"> (可以将源直接连接到目标，而无需进行任何转换。 ) 可以通过在数据库中运行以下命令来创建目标表 [!INCLUDE[tsql](../../includes/tsql-md.md)] `AdventureWorks` ：</span><span class="sxs-lookup"><span data-stu-id="32644-204">(You can connect a source directly to a destination without any transformations.) You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="32644-205">运行该示例。</span><span class="sxs-lookup"><span data-stu-id="32644-205">Run the sample.</span></span>

    ```vb
    Imports System.Data.SqlClient
    ...
    Public Class ScriptMain
        Inherits UserComponent

        Dim connMgr As IDTSConnectionManager100
        Dim sqlConn As SqlConnection
        Dim sqlReader As SqlDataReader

        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

            connMgr = Me.Connections.MyADONETConnection
            sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

        End Sub

        Public Overrides Sub PreExecute()

            Dim cmd As New SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn)
            sqlReader = cmd.ExecuteReader

        End Sub

        Public Overrides Sub CreateNewOutputRows()

            Do While sqlReader.Read
                With MyAddressOutputBuffer
                    .AddRow()
                    .AddressID = sqlReader.GetInt32(0)
                    .City = sqlReader.GetString(1)
                End With
            Loop

        End Sub

        Public Overrides Sub PostExecute()

            sqlReader.Close()

        End Sub

        Public Overrides Sub ReleaseConnections()

            connMgr.ReleaseConnection(sqlConn)

        End Sub

    End Class
    ```

    ```csharp
    using System.Data.SqlClient;
    public class ScriptMain:
        UserComponent

    {
        IDTSConnectionManager100 connMgr;
        SqlConnection sqlConn;
        SqlDataReader sqlReader;

        public override void AcquireConnections(object Transaction)
        {
            connMgr = this.Connections.MyADONETConnection;
            sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

        }

        public override void PreExecute()
        {

            SqlCommand cmd = new SqlCommand("SELECT AddressID, City, StateProvinceID FROM Person.Address", sqlConn);
            sqlReader = cmd.ExecuteReader();

        }

        public override void CreateNewOutputRows()
        {

            while (sqlReader.Read())
            {
                {
                    MyAddressOutputBuffer.AddRow();
                    MyAddressOutputBuffer.AddressID = sqlReader.GetInt32(0);
                    MyAddressOutputBuffer.City = sqlReader.GetString(1);
                }
            }

        }

        public override void PostExecute()
        {

            sqlReader.Close();

        }

        public override void ReleaseConnections()
        {

            connMgr.ReleaseConnection(sqlConn);

        }

    }
    ```

### <a name="flat-file-source-example"></a><span data-ttu-id="32644-206">平面文件源示例</span><span class="sxs-lookup"><span data-stu-id="32644-206">Flat File Source Example</span></span>
 <span data-ttu-id="32644-207">本示例演示了使用现有平面文件连接管理器将平面文件中的数据加载到数据流中的源组件。</span><span class="sxs-lookup"><span data-stu-id="32644-207">This example demonstrates a source component that uses an existing Flat File connection manager to load data from a flat file into the data flow.</span></span> <span data-ttu-id="32644-208">通过将平面文件源数据从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中导出来创建该数据。</span><span class="sxs-lookup"><span data-stu-id="32644-208">The flat file source data is created by exporting it from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="32644-209">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="32644-209">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="32644-210">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导入和导出向导将 " **Person** " 表从 `AdventureWorks` 示例数据库导出到以逗号分隔的平面文件。</span><span class="sxs-lookup"><span data-stu-id="32644-210">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard to export the **Person.Address** table from the `AdventureWorks` sample database to a comma-delimited flat file.</span></span> <span data-ttu-id="32644-211">此示例使用文件名 ExportedAddresses.txt。</span><span class="sxs-lookup"><span data-stu-id="32644-211">This sample uses the file name ExportedAddresses.txt.</span></span>

2.  <span data-ttu-id="32644-212">创建连接导出的数据文件的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="32644-212">Create a Flat File connection manager that connects to the exported data file.</span></span>

3.  <span data-ttu-id="32644-213">向数据流设计器图面添加新的脚本组件并将其配置为源。</span><span class="sxs-lookup"><span data-stu-id="32644-213">Add a new Script component to the Data Flow designer surface and configure it as a source.</span></span>

4.  <span data-ttu-id="32644-214">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32644-214">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="32644-215">在“输入和输出”页中，用更具说明性的名称（如 MyAddressOutput）重命名默认输出   。</span><span class="sxs-lookup"><span data-stu-id="32644-215">On the **Inputs and Outputs** page, rename the default output with a more descriptive name such as **MyAddressOutput**.</span></span> <span data-ttu-id="32644-216">添加并配置两个输出列 AddressID 和 City   。</span><span class="sxs-lookup"><span data-stu-id="32644-216">Add and configure the two output columns, **AddressID** and **City**.</span></span>

5.  <span data-ttu-id="32644-217">在“连接管理器”页中，添加或创建平面文件连接管理器，并以说明性的名称命名，如 MyFlatFileSrcConnectionManager   。</span><span class="sxs-lookup"><span data-stu-id="32644-217">On the **Connection Managers** page, add or create the Flat File connection manager, using a descriptive name such as **MyFlatFileSrcConnectionManager**.</span></span>

6.  <span data-ttu-id="32644-218">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="32644-218">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="32644-219">然后关闭脚本开发环境和“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="32644-219">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="32644-220">创建并配置目标组件，如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，或者[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中演示的示例目标组件。</span><span class="sxs-lookup"><span data-stu-id="32644-220">Create and configure a destination component, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="32644-221">然后将源组件连接到目标。</span><span class="sxs-lookup"><span data-stu-id="32644-221">Then connect the source component to the destination.</span></span> <span data-ttu-id="32644-222"> (可以将源直接连接到目标，而无需进行任何转换。 ) 可以通过在数据库中运行以下命令来创建目标表 [!INCLUDE[tsql](../../includes/tsql-md.md)] `AdventureWorks` ：</span><span class="sxs-lookup"><span data-stu-id="32644-222">(You can connect a source directly to a destination without any transformations.) You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="32644-223">运行该示例。</span><span class="sxs-lookup"><span data-stu-id="32644-223">Run the sample.</span></span>

    ```vb
    Imports System.IO
    ...
    Public Class ScriptMain
        Inherits UserComponent

        Private textReader As StreamReader
        Private exportedAddressFile As String

        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

            Dim connMgr As IDTSConnectionManager100 = _
                Me.Connections.MyFlatFileSrcConnectionManager
            exportedAddressFile = _
                CType(connMgr.AcquireConnection(Nothing), String)

        End Sub

        Public Overrides Sub PreExecute()
            MyBase.PreExecute()
            textReader = New StreamReader(exportedAddressFile)
        End Sub

        Public Overrides Sub CreateNewOutputRows()

            Dim nextLine As String
            Dim columns As String()

            Dim delimiters As Char()
            delimiters = ",".ToCharArray

            nextLine = textReader.ReadLine
            Do While nextLine IsNot Nothing
                columns = nextLine.Split(delimiters)
                With MyAddressOutputBuffer
                    .AddRow()
                    .AddressID = columns(0)
                    .City = columns(3)
                End With
                nextLine = textReader.ReadLine
            Loop

        End Sub

        Public Overrides Sub PostExecute()
            MyBase.PostExecute()
            textReader.Close()

        End Sub

    End Class
    ```

    ```csharp
    using System.IO;
    public class ScriptMain:
        UserComponent

    {
        private StreamReader textReader;
        private string exportedAddressFile;

        public override void AcquireConnections(object Transaction)
        {

            IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileSrcConnectionManager;
            exportedAddressFile = (string)connMgr.AcquireConnection(null);

        }

        public override void PreExecute()
        {
            base.PreExecute();
            textReader = new StreamReader(exportedAddressFile);
        }

        public override void CreateNewOutputRows()
        {

            string nextLine;
            string[] columns;

            char[] delimiters;
            delimiters = ",".ToCharArray();

            nextLine = textReader.ReadLine();
            while (nextLine != null)
            {
                columns = nextLine.Split(delimiters);
                {
                    MyAddressOutputBuffer.AddRow();
                    MyAddressOutputBuffer.AddressID = columns[0];
                    MyAddressOutputBuffer.City = columns[3];
                }
                nextLine = textReader.ReadLine();
            }

        }

        public override void PostExecute()
        {

            base.PostExecute();
            textReader.Close();

        }

    }
    ```

<span data-ttu-id="32644-224">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="32644-224">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="32644-225">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="32644-225">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="32644-226">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="32644-226">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="32644-227">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="32644-227">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="32644-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32644-228">See Also</span></span>
 <span data-ttu-id="32644-229">[使用脚本组件创建目标](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)[开发自定义源组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)</span><span class="sxs-lookup"><span data-stu-id="32644-229">[Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md) [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)</span></span>


