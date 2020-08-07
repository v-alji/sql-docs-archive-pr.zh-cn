---
title: 使用脚本组件创建目标 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1245dde111b24d1c37e2c5550d236c97126ee725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588657"
---
# <a name="creating-a-destination-with-the-script-component"></a><span data-ttu-id="ddb7b-102">使用脚本组件创建目标</span><span class="sxs-lookup"><span data-stu-id="ddb7b-102">Creating a Destination with the Script Component</span></span>
  <span data-ttu-id="ddb7b-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的数据流中的目标组件用于将从上游源和转换接收的数据保存到数据源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-103">You use a destination component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to save data received from upstream sources and transformations to a data source.</span></span> <span data-ttu-id="ddb7b-104">目标组件通常通过现有连接管理器连接数据源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-104">Ordinarily the destination component connects to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="ddb7b-105">有关脚本组件的概述，请参阅 [使用脚本组件扩展数据流] (。/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="ddb7b-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="ddb7b-106">脚本组件及其生成的基础结构代码可以大大简化自定义数据流组件的开发过程。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="ddb7b-107">但是，若要了解脚本组件的工作方式，通读[开发自定义数据流组件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)部分，特别是[开发自定义目标组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)部分中的自定义数据流组件开发步骤很有帮助。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-107">However, to understand how the Script component works, you may find it useful to read through the steps for developing a custom data flow components in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).</span></span>

## <a name="getting-started-with-a-destination-component"></a><span data-ttu-id="ddb7b-108">开始一个目标组件</span><span class="sxs-lookup"><span data-stu-id="ddb7b-108">Getting Started with a Destination Component</span></span>
 <span data-ttu-id="ddb7b-109">向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器的“数据流”选项卡添加脚本组件时，“选择脚本组件类型”  对话框将打开并提示用户选择“源”  、“目标”  或“转换”  脚本。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-109">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a **Source**, **Destination**, or **Transformation** script.</span></span> <span data-ttu-id="ddb7b-110">在此对话框中选择“目标”  。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-110">In this dialog box, select **Destination**.</span></span>

 <span data-ttu-id="ddb7b-111">然后，将转换的输出连接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中的目标组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-111">Next, connect the output of a transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ddb7b-112">出于测试目的，可以将源直接连接到目标，而不经任何转换。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-112">For testing, you can connect a source directly to a destination without any transformations.</span></span>

## <a name="configuring-a-destination-component-in-metadata-design-mode"></a><span data-ttu-id="ddb7b-113">在元数据设计模式下配置目标组件</span><span class="sxs-lookup"><span data-stu-id="ddb7b-113">Configuring a Destination Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="ddb7b-114">选择创建目标组件的选项后，可使用“脚本转换编辑器”  配置该组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-114">After you select the option to create a destination component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="ddb7b-115">有关详细信息，请参阅[在脚本组件编辑器中配置脚本组件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-115">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="ddb7b-116">若要选择脚本目标使用的脚本语言，请在“脚本转换编辑器”  对话框的“脚本”  页上设置 **ScriptLanguage** 属性。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-116">To select the script language that the Script destination will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="ddb7b-117">若要设置脚本组件的默认脚本语言，请使用“选项”  对话框的“常规”  页上的“脚本语言”  选项。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-117">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="ddb7b-118">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-118">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="ddb7b-119">数据流目标组件有一个输入，没有输出。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-119">A data flow destination component has one input and no outputs.</span></span> <span data-ttu-id="ddb7b-120">在编写自定义脚本之前，必须在元数据设计模式下完成的一个步骤是使用“脚本转换编辑器”  配置组件的输入。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-120">Configuring the input for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="ddb7b-121">添加连接管理器</span><span class="sxs-lookup"><span data-stu-id="ddb7b-121">Adding Connection Managers</span></span>
 <span data-ttu-id="ddb7b-122">目标组件通常使用现有连接管理器连接将数据流中的数据保存到的数据源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-122">Ordinarily a destination component uses an existing connection manager to connect to the data source to which it saves data from the data flow.</span></span> <span data-ttu-id="ddb7b-123">在“脚本转换编辑器”  的“连接管理器”  页中，单击“添加”  以添加适当的连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-123">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="ddb7b-124">但是，连接管理器只是一个封装和存储连接特定类型数据源所需信息的便利单元。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-124">However, a connection manager is just a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="ddb7b-125">您必须编写自己的自定义代码才能加载或保存数据，并且才有可能打开和关闭与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-125">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span>

 <span data-ttu-id="ddb7b-126">有关如何在脚本组件中使用连接管理器的常规信息，请参阅[在脚本组件中连接数据源](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-126">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="ddb7b-127">有关“脚本转换编辑器”  的“连接管理器”  页的详细信息，请参阅[脚本转换编辑器（“连接管理器”页）](../script-transformation-editor-connection-managers-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-127">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-inputs-and-input-columns"></a><span data-ttu-id="ddb7b-128">配置输入和输入列</span><span class="sxs-lookup"><span data-stu-id="ddb7b-128">Configuring Inputs and Input Columns</span></span>
 <span data-ttu-id="ddb7b-129">目标组件有一个输入，没有输出。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-129">A destination component has one input and no outputs.</span></span>

 <span data-ttu-id="ddb7b-130">在“脚本转换编辑器”  的“输入列”  页中，列列表显示数据流上游组件的输出中可用的列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-130">On the **Input Columns** page of the **Script Transformation Editor**, the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="ddb7b-131">选择要保存的列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-131">Select the columns that you want to save.</span></span>

 <span data-ttu-id="ddb7b-132">有关“脚本转换编辑器”  的“输入列”  页的详细信息，请参阅[脚本转换编辑器（“输入列”页）](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-132">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

 <span data-ttu-id="ddb7b-133">“脚本转换编辑器”  的“输入和输出”  页显示单一输入，可以将其重命名。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-133">The **Inputs and Outputs** page of the **Script Transformation Editor** shows a single input, which you can rename.</span></span> <span data-ttu-id="ddb7b-134">通过使用在自动生成的代码中创建的取值函数属性，在脚本中将通过输入的名称来引用输入。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-134">You will refer to the input by its name in your script by using the accessor property created in the auto-generated code.</span></span>

 <span data-ttu-id="ddb7b-135">有关“脚本转换编辑器”  的“输入和输出”  页上的详细信息，请参阅[脚本转换编辑器（“输入和输出”页）](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-135">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="ddb7b-136">添加变量</span><span class="sxs-lookup"><span data-stu-id="ddb7b-136">Adding Variables</span></span>
 <span data-ttu-id="ddb7b-137">如果要在脚本中使用现有变量，可以在 " `ReadOnlyVariables` `ReadWriteVariables` **脚本转换编辑器**" 的 "**脚本**" 页上的和属性字段中添加这些变量。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-137">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="ddb7b-138">在属性字段中添加多个变量时，请用逗号将变量名隔开。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-138">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="ddb7b-139">还可以选择多个变量，方法是单击和属性字段旁的省略号 (**...**) `ReadOnlyVariables` 按钮 `ReadWriteVariables` ，然后在 "**选择变量**" 对话框中选择变量。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-139">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="ddb7b-140">有关如何在脚本组件中使用变量的常规信息，请参阅[在脚本组件中使用变量](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-140">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="ddb7b-141">有关“脚本转换编辑器”的“脚本”页的详细信息，请参阅[脚本转换编辑器（“脚本”页）](../script-transformation-editor-script-page.md)   。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-141">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-destination-component-in-code-design-mode"></a><span data-ttu-id="ddb7b-142">在代码设计模式下编写目标组件脚本</span><span class="sxs-lookup"><span data-stu-id="ddb7b-142">Scripting a Destination Component in Code-Design Mode</span></span>
 <span data-ttu-id="ddb7b-143">为组件配置完元数据后，可以编写自定义脚本。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-143">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="ddb7b-144">在“脚本转换编辑器”的“脚本”页面中，单击“编辑脚本”打开 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE，可在其中添加自定义脚本    。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-144">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="ddb7b-145">编写脚本所使用的语言取决于为“脚本”  页上的 **ScriptLanguage** 属性选择 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 还是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作为脚本语言。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-145">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="ddb7b-146">有关适用于使用脚本组件创建的所有组件类型的重要信息，请参阅[脚本组件的编码和调试](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-146">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="ddb7b-147">了解自动生成的代码</span><span class="sxs-lookup"><span data-stu-id="ddb7b-147">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="ddb7b-148">创建并配置目标组件后打开 VSTA IDE 时，可编辑的 `ScriptMain` 类将显示在代码编辑器中，其中有 `ProcessInputRow` 方法的存根。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-148">When you open the VSTA IDE after you create and configuring a destination component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="ddb7b-149">在 `ScriptMain` 类中可编写自定义代码，`ProcessInputRow` 是目标组件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-149">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a destination component.</span></span>

 <span data-ttu-id="ddb7b-150">如果在 VSTA 中打开 "**项目资源管理器**" 窗口，可以看到脚本组件还生成了只读的 `BufferWrapper` 和 `ComponentWrapper` 项目项。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-150">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="ddb7b-151">`ScriptMain` 类从 `UserComponent` 项目项中的 `ComponentWrapper` 类继承。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-151">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="ddb7b-152">在运行时，数据流引擎调用 `ProcessInput` 类中的 `UserComponent` 方法，该方法重写 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 父类的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-152">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="ddb7b-153">而 `ProcessInput` 方法遍历输入缓冲区中的所有行并为每一行调用一次 `ProcessInputRow` 方法。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-153">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="ddb7b-154">编写自定义代码</span><span class="sxs-lookup"><span data-stu-id="ddb7b-154">Writing Your Custom Code</span></span>
 <span data-ttu-id="ddb7b-155">为了完成创建自定义目标组件，您可以在 `ScriptMain` 类的以下方法中编写脚本。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-155">To finish creating a custom destination component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="ddb7b-156">重写 `AcquireConnections` 方法以连接外部数据源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-156">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="ddb7b-157">从连接管理器中提取连接对象或者需要的连接信息。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-157">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="ddb7b-158">重写 `PreExecute` 方法以准备保存数据。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-158">Override the `PreExecute` method to prepare to save the data.</span></span> <span data-ttu-id="ddb7b-159">例如，您可以在此方法中创建和配置 `SqlCommand` 及其参数。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-159">For example, you may want to create and configure a `SqlCommand` and its parameters in this method.</span></span>

3.  <span data-ttu-id="ddb7b-160">使用重写的 `ProcessInputRow` 方法将每个输入行复制到外部数据源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-160">Use the overridden `ProcessInputRow` method to copy each input row to the external data source.</span></span> <span data-ttu-id="ddb7b-161">例如，对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标，可以将列值复制到 `SqlCommand` 的参数中，并为每一行执行一次该命令。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-161">For example, for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, you can copy the column values into the parameters of a `SqlCommand` and execute the command one time for each row.</span></span> <span data-ttu-id="ddb7b-162">对于平面文件目标，可以将每列的值写入 `StreamWriter`，用列分隔符将这些值隔开。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-162">For a flat file destination, you can write the values for each column to a `StreamWriter`, separating the values by the column delimiter.</span></span>

4.  <span data-ttu-id="ddb7b-163">如果需要，重写 `PostExecute` 方法以断开与外部数据源的连接，并执行任何其他必需的清除操作。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-163">Override the `PostExecute` method to disconnect from the external data source, if required, and to perform any other required cleanup.</span></span>

## <a name="examples"></a><span data-ttu-id="ddb7b-164">示例</span><span class="sxs-lookup"><span data-stu-id="ddb7b-164">Examples</span></span>
 <span data-ttu-id="ddb7b-165">下面的示例演示在 `ScriptMain` 类中创建目标组件所需的代码。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-165">The examples that follow demonstrate code that is required in the `ScriptMain` class to create a destination component.</span></span>

> [!NOTE]
>  <span data-ttu-id="ddb7b-166">这些示例使用示例数据库中的**Person**表， `AdventureWorks` 并通过数据流传递其第一列和第四列， **int \* AddressID**\* 和**nvarchar (30) City**列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-166">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="ddb7b-167">在本节中，在源、转换和目标示例中使用相同的数据。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-167">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="ddb7b-168">每个示例的其他前提条件和假设都记录在文档中。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-168">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-destination-example"></a><span data-ttu-id="ddb7b-169">ADO.NET 目标示例</span><span class="sxs-lookup"><span data-stu-id="ddb7b-169">ADO.NET Destination Example</span></span>
 <span data-ttu-id="ddb7b-170">本示例演示了使用现有 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器将数据流中的数据保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表中的目标组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-170">This example demonstrates a destination component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to save data from the data flow into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="ddb7b-171">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="ddb7b-171">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="ddb7b-172">创建使用 `SqlClient` 访问接口连接 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 数据库的 `AdventureWorks` 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-172">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="ddb7b-173">在 `AdventureWorks` 数据库中运行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令，创建一个目标表：</span><span class="sxs-lookup"><span data-stu-id="ddb7b-173">Create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

3.  <span data-ttu-id="ddb7b-174">向数据流设计器图面添加新的脚本组件并将其配置为目标。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-174">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

4.  <span data-ttu-id="ddb7b-175">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中将上游源或转换的输出连接到目标组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-175">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ddb7b-176"> (可以将源直接连接到目标，而无需进行任何转换。 ) 此输出应提供示例数据库的 AddressID**表中的数据**， `AdventureWorks` 其中至少包含了**AddressID**和**City**列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-176">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="ddb7b-177">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-177">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="ddb7b-178">在“输入列”  页中，选择 **AddressID** 和 **City** 输入列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-178">On the **Input Columns** page, select the **AddressID** and **City** input columns.</span></span>

6.  <span data-ttu-id="ddb7b-179">在“输入和输出”  页中，用更具说明性的名称（如 **MyAddressInput**）重命名输入。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-179">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>

7.  <span data-ttu-id="ddb7b-180">在“连接管理器”  页中，添加或创建 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 连接管理器，并以诸如 **MyADONETConnectionManager** 之类的名称命名。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-180">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager with a name such as **MyADONETConnectionManager**.</span></span>

8.  <span data-ttu-id="ddb7b-181">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-181">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="ddb7b-182">然后关闭脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-182">Then close the script development environment.</span></span>

9. <span data-ttu-id="ddb7b-183">关闭“脚本转换编辑器”  并运行该示例。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-183">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.Data.SqlClient
...
Public Class ScriptMain
    Inherits UserComponent

    Dim connMgr As IDTSConnectionManager100
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        connMgr = Me.Connections.MyADONETConnectionManager
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

    End Sub

    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)
        With sqlCmd
            .Parameters("@addressid").Value = Row.AddressID
            .Parameters("@city").Value = Row.City
            .ExecuteNonQuery()
        End With
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
    SqlCommand sqlCmd;
    SqlParameter sqlParam;

    public override void AcquireConnections(object Transaction)
    {

        connMgr = this.Connections.MyADONETConnectionManager;
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +
            "VALUES(@addressid, @city)", sqlConn);
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);
        sqlCmd.Parameters.Add(sqlParam);
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);
        sqlCmd.Parameters.Add(sqlParam);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {
        {
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;
            sqlCmd.Parameters["@city"].Value = Row.City;
            sqlCmd.ExecuteNonQuery();
        }
    }

    public override void ReleaseConnections()
    {

        connMgr.ReleaseConnection(sqlConn);

    }

}
```

### <a name="flat-file-destination-example"></a><span data-ttu-id="ddb7b-184">平面文件目标示例</span><span class="sxs-lookup"><span data-stu-id="ddb7b-184">Flat File Destination Example</span></span>
 <span data-ttu-id="ddb7b-185">本示例演示了使用现有平面文件连接管理器将数据流中的数据保存到平面文件中的目标组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-185">This example demonstrates a destination component that uses an existing Flat File connection manager to save data from the data flow to a flat file.</span></span>

 <span data-ttu-id="ddb7b-186">如果要运行此示例代码，必须按照如下方式配置包和组件：</span><span class="sxs-lookup"><span data-stu-id="ddb7b-186">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="ddb7b-187">创建连接目标文件的平面文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-187">Create a Flat File connection manager that connects to a destination file.</span></span> <span data-ttu-id="ddb7b-188">该文件不必一定存在，目标组件会创建它。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-188">The file does not have to exist; the destination component will create it.</span></span> <span data-ttu-id="ddb7b-189">将目标文件配置为包含 **AddressID** 和 **City** 列的逗号分隔文件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-189">Configure the destination file as a comma-delimited file that contains the **AddressID** and **City** columns.</span></span>

2.  <span data-ttu-id="ddb7b-190">向数据流设计器图面添加新的脚本组件并将其配置为目标。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-190">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

3.  <span data-ttu-id="ddb7b-191">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中将上游源或转换的输出连接到目标组件。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-191">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="ddb7b-192"> (可以将源直接连接到目标，而无需进行任何转换。 ) 此输出应提供示例数据库**的 AddressID 表中**的数据 `AdventureWorks` ，并且至少应包含**AddressID**和**City**列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-192">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database, and should contain at least the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="ddb7b-193">打开“脚本转换编辑器”  。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-193">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="ddb7b-194">在“输入列”  页中，选择 AddressID  和 City  列。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-194">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="ddb7b-195">在“输入和输出”  页中，用更具说明性的名称（如 **MyAddressInput**）重命名输入。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-195">On the **Inputs and Outputs** page, rename the input with a more descriptive name, such as **MyAddressInput**.</span></span>

6.  <span data-ttu-id="ddb7b-196">在“连接管理器”  页中，添加或创建平面文件连接管理器，并以说明性的名称命名，如 **MyFlatFileDestConnectionManager**。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-196">On the **Connection Managers** page, add or create the Flat File connection manager with a descriptive name such as **MyFlatFileDestConnectionManager**.</span></span>

7.  <span data-ttu-id="ddb7b-197">在“脚本”页中，单击“编辑脚本”并输入下面的脚本   。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-197">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="ddb7b-198">然后关闭脚本开发环境。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-198">Then close the script development environment.</span></span>

8.  <span data-ttu-id="ddb7b-199">关闭“脚本转换编辑器”  并运行该示例。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-199">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.IO
...
Public Class ScriptMain
    Inherits UserComponent

    Dim copiedAddressFile As String
    Private textWriter As StreamWriter
    Private columnDelimiter As String = ","

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        Dim connMgr As IDTSConnectionManager100 = _
            Me.Connections.MyFlatFileDestConnectionManager
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)

    End Sub

    Public Overrides Sub PreExecute()

        textWriter = New StreamWriter(copiedAddressFile, False)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With textWriter
            If Not Row.AddressID_IsNull Then
                .Write(Row.AddressID)
            End If
            .Write(columnDelimiter)
            If Not Row.City_IsNull Then
                .Write(Row.City)
            End If
            .WriteLine()
        End With

    End Sub

    Public Overrides Sub PostExecute()

        textWriter.Close()

    End Sub

End Class
```

```csharp
using System.IO;
public class ScriptMain:
    UserComponent

{
    string copiedAddressFile;
    private StreamWriter textWriter;
    private string columnDelimiter = ",";

    public override void AcquireConnections(object Transaction)
    {

        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;
        copiedAddressFile = (string) connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        textWriter = new StreamWriter(copiedAddressFile, false);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            if (!Row.AddressID_IsNull)
            {
                textWriter.Write(Row.AddressID);
            }
            textWriter.Write(columnDelimiter);
            if (!Row.City_IsNull)
            {
                textWriter.Write(Row.City);
            }
            textWriter.WriteLine();
        }

    }

    public override void PostExecute()
    {

        textWriter.Close();

    }

}
```

<span data-ttu-id="ddb7b-200">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="ddb7b-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ddb7b-201">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="ddb7b-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ddb7b-202">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="ddb7b-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ddb7b-203">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="ddb7b-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddb7b-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddb7b-204">See Also</span></span>
 <span data-ttu-id="ddb7b-205">[使用脚本组件创建源](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)[开发自定义目标组件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span><span class="sxs-lookup"><span data-stu-id="ddb7b-205">[Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span></span>


