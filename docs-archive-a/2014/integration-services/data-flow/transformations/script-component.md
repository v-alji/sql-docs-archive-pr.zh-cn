---
title: 脚本组件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af8e500e399b0f69a7e34c9e2e01c74d83256107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694545"
---
# <a name="script-component"></a><span data-ttu-id="864e5-102">脚本组件</span><span class="sxs-lookup"><span data-stu-id="864e5-102">Script Component</span></span>
  <span data-ttu-id="864e5-103">脚本组件承载脚本，并使包能够包含和运行自定义的脚本代码。</span><span class="sxs-lookup"><span data-stu-id="864e5-103">The Script component hosts script and enables a package to include and run custom script code.</span></span> <span data-ttu-id="864e5-104">可以将包中的脚本组件用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="864e5-104">You can use the Script component in packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="864e5-105">将多个转换应用于数据，而不是在数据流中使用多个转换。</span><span class="sxs-lookup"><span data-stu-id="864e5-105">Apply multiple transformations to data instead of using multiple transformations in the data flow.</span></span> <span data-ttu-id="864e5-106">例如，脚本可以将两列中的值相加，然后计算和的平均值。</span><span class="sxs-lookup"><span data-stu-id="864e5-106">For example, a script can add the values in two columns and then calculate the average of the sum.</span></span>  
  
-   <span data-ttu-id="864e5-107">访问现有 .NET 程序集中的业务规则。</span><span class="sxs-lookup"><span data-stu-id="864e5-107">Access business rules in an existing .NET assembly.</span></span> <span data-ttu-id="864e5-108">例如，脚本可以应用指定 `Income` 列中有效值范围的业务规则。</span><span class="sxs-lookup"><span data-stu-id="864e5-108">For example, a script can apply a business rule that specifies the range of values that are valid in an `Income` column.</span></span>  
  
-   <span data-ttu-id="864e5-109">除 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 表达式语法提供的函数和运算符之外，还可使用自定义公式和函数。</span><span class="sxs-lookup"><span data-stu-id="864e5-109">Use custom formulas and functions in addition to the functions and operators that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expression grammar provides.</span></span> <span data-ttu-id="864e5-110">例如，使用 LUHN 公式验证信用卡号。</span><span class="sxs-lookup"><span data-stu-id="864e5-110">For example, validate credit card numbers that use the LUHN formula.</span></span>  
  
-   <span data-ttu-id="864e5-111">验证列数据，并跳过包含无效数据的记录。</span><span class="sxs-lookup"><span data-stu-id="864e5-111">Validate column data and skip records that contain invalid data.</span></span> <span data-ttu-id="864e5-112">例如，脚本可以评估邮资额的合理性，并跳过金额过高或过低的记录。</span><span class="sxs-lookup"><span data-stu-id="864e5-112">For example, a script can assess the reasonableness of a postage amount and skip records with extremely high or low amounts.</span></span>  
  
 <span data-ttu-id="864e5-113">脚本组件为将自定义函数纳入数据流提供了简便快捷的方法。</span><span class="sxs-lookup"><span data-stu-id="864e5-113">The Script component provides an easy and quick way to include custom functions in a data flow.</span></span> <span data-ttu-id="864e5-114">但是，如果您计划在多个包中重新使用脚本代码，则应考虑编写自定义组件，而不使用脚本组件。</span><span class="sxs-lookup"><span data-stu-id="864e5-114">However, if you plan to reuse the script code in multiple packages, you should consider programming a custom component instead of using the Script component.</span></span> <span data-ttu-id="864e5-115">有关详细信息，请参阅 [开发自定义数据流组件](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="864e5-115">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="864e5-116">如果脚本组件包含尝试读取 NULL 列值的脚本，则在您运行包时此脚本组件将失败。</span><span class="sxs-lookup"><span data-stu-id="864e5-116">If the Script component contains a script that tries to read the value of a column that is NULL, the Script component fails when you run the package.</span></span> <span data-ttu-id="864e5-117">建议你的脚本先使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> 方法确定相应列是否为 NULL，再尝试读取该列的值。</span><span class="sxs-lookup"><span data-stu-id="864e5-117">We recommend that your script use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> method to determine whether the column is NULL before trying to read the column value.</span></span>  
  
 <span data-ttu-id="864e5-118">脚本组件可用作源、转换或目标。</span><span class="sxs-lookup"><span data-stu-id="864e5-118">The Script component can be used as a source, a transformation, or a destination.</span></span> <span data-ttu-id="864e5-119">该组件支持一个输入和多个输出。</span><span class="sxs-lookup"><span data-stu-id="864e5-119">This component supports one input and multiple outputs.</span></span> <span data-ttu-id="864e5-120">根据其使用方式，该组件可以支持一个输入或多个输出，也可二者都支持。</span><span class="sxs-lookup"><span data-stu-id="864e5-120">Depending on how the component is used, it supports either an input or outputs or both.</span></span> <span data-ttu-id="864e5-121">脚本由输入或输出中的每一行调用。</span><span class="sxs-lookup"><span data-stu-id="864e5-121">The script is invoked by every row in the input or output.</span></span>  
  
-   <span data-ttu-id="864e5-122">如果用作源，则脚本组件支持多个输出。</span><span class="sxs-lookup"><span data-stu-id="864e5-122">If used as a source, the Script component supports multiple outputs.</span></span>  
  
-   <span data-ttu-id="864e5-123">如果用作转换，则脚本组件支持一个输入和多个输出。</span><span class="sxs-lookup"><span data-stu-id="864e5-123">If used as a transformation, the Script component supports one input and multiple outputs.</span></span>  
  
-   <span data-ttu-id="864e5-124">如果用作目标，则脚本组件支持一个输入。</span><span class="sxs-lookup"><span data-stu-id="864e5-124">If used as a destination, the Script component supports one input.</span></span>  
  
 <span data-ttu-id="864e5-125">脚本组件不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="864e5-125">The Script component does not support error outputs.</span></span>  
  
 <span data-ttu-id="864e5-126">确定将此脚本组件作为包的正确选择之后，必须配置输入和输出、开发该组件使用的脚本并配置组件本身。</span><span class="sxs-lookup"><span data-stu-id="864e5-126">After you decide that the Script component is the appropriate choice for your package, you have to configure the inputs and outputs, develop the script that the component uses, and configure the component itself.</span></span>  
  
## <a name="understanding-the-script-component-modes"></a><span data-ttu-id="864e5-127">了解脚本组件模式</span><span class="sxs-lookup"><span data-stu-id="864e5-127">Understanding the Script Component Modes</span></span>  
 <span data-ttu-id="864e5-128">在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中，脚本组件具有两种模式：元数据设计模式和代码设计模式。</span><span class="sxs-lookup"><span data-stu-id="864e5-128">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata-design mode and code-design mode.</span></span> <span data-ttu-id="864e5-129">在元数据设计模式中，可以添加和修改脚本组件的输入和输出，但不能编写代码。</span><span class="sxs-lookup"><span data-stu-id="864e5-129">In metadata-design mode, you can add and modify the Script component inputs and outputs, but you cannot write code.</span></span> <span data-ttu-id="864e5-130">配置完所有的输入和输出后，即可切换至代码设计模式编写脚本。</span><span class="sxs-lookup"><span data-stu-id="864e5-130">After all the inputs and outputs are configured, you switch to code-design mode to write the script.</span></span> <span data-ttu-id="864e5-131">脚本组件从输入和输出的元数据自动生成基代码。</span><span class="sxs-lookup"><span data-stu-id="864e5-131">The Script component automatically generates base code from the metadata of the inputs and outputs.</span></span> <span data-ttu-id="864e5-132">如果在脚本组件生成基代码后更改元数据，则您的代码可能无法再编译，因为更新的基代码可能与您的代码不兼容。</span><span class="sxs-lookup"><span data-stu-id="864e5-132">If you change the metadata after the Script component generates the base code, your code may no longer compile because the updated base code may be incompatible with your code.</span></span>  
  
## <a name="writing-the-script-that-the-component-uses"></a><span data-ttu-id="864e5-133">编写组件使用的脚本</span><span class="sxs-lookup"><span data-stu-id="864e5-133">Writing the Script that the Component Uses</span></span>  
 <span data-ttu-id="864e5-134">脚本组件将 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 用作编写脚本的环境。</span><span class="sxs-lookup"><span data-stu-id="864e5-134">The Script component uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts.</span></span> <span data-ttu-id="864e5-135">您可以从 **“脚本转换编辑器”** 访问 VSTA。</span><span class="sxs-lookup"><span data-stu-id="864e5-135">You access VSTA from the **Script Transformation Editor**.</span></span> <span data-ttu-id="864e5-136">有关详细信息，请参阅 [脚本转换编辑器（“脚本”页）](../../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="864e5-136">For more information, see [Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).</span></span>  
  
 <span data-ttu-id="864e5-137">脚本组件提供一个 VSTA 项目，其中包含一个名为 ScriptMain 的自动生成的类，表示组件元数据。</span><span class="sxs-lookup"><span data-stu-id="864e5-137">The Script component provides a VSTA project that includes an auto-generated class, named ScriptMain, that represents the component metadata.</span></span> <span data-ttu-id="864e5-138">例如，如果将脚本组件用作具有三个输出的转换，则 ScriptMain 为每个输出都包含一种方法。</span><span class="sxs-lookup"><span data-stu-id="864e5-138">For example, if the Script component is used as a transformation that has three outputs, ScriptMain includes a method for each output.</span></span> <span data-ttu-id="864e5-139">ScriptMain 是脚本的入口点。</span><span class="sxs-lookup"><span data-stu-id="864e5-139">ScriptMain is the entry point to the script.</span></span>  
  
 <span data-ttu-id="864e5-140">VSTA 包含 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 环境的所有标准功能，如具有颜色编码的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 编辑器、IntelliSense 和对象浏览器。</span><span class="sxs-lookup"><span data-stu-id="864e5-140">VSTA includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span> <span data-ttu-id="864e5-141">脚本组件使用的脚本存储在包定义中，</span><span class="sxs-lookup"><span data-stu-id="864e5-141">The script that the Script component uses is stored in the package definition.</span></span> <span data-ttu-id="864e5-142">设计包时，脚本代码将临时写入项目文件。</span><span class="sxs-lookup"><span data-stu-id="864e5-142">When you are designing the package, the script code is temporarily written to a project file.</span></span>  
  
 <span data-ttu-id="864e5-143">VSTA 支持 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 编程语言。</span><span class="sxs-lookup"><span data-stu-id="864e5-143">VSTA supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic programming languages.</span></span>  
  
 <span data-ttu-id="864e5-144">有关如何对脚本组件进行编程的信息，请参阅 [使用脚本组件扩展数据流](script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="864e5-144">For information about how to program the Script component, see [Extending the Data Flow with the Script Component](script-component.md).</span></span> <span data-ttu-id="864e5-145">有关如何将脚本组件配置为源、转换或目标的更多特定信息，请参阅 [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)。</span><span class="sxs-lookup"><span data-stu-id="864e5-145">For more specific information about how to configure the Script component as a source, transformation, or destination, see [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span> <span data-ttu-id="864e5-146">有关说明脚本组件使用的其他示例（如 ODBC 目标），请参阅 [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="864e5-146">For additional examples such as an ODBC destination that demonstrate the use of the Script component, see [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="864e5-147">在早期版本中您可以指示是否对脚本进行预编译，而在 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 和更高版本中，不同的是，所有脚本都要预编译。</span><span class="sxs-lookup"><span data-stu-id="864e5-147">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="864e5-148">脚本进行预编译后，运行时将不加载语言引擎，因此包运行得更快。</span><span class="sxs-lookup"><span data-stu-id="864e5-148">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="864e5-149">但是，预编译二进制文件占用了大量的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="864e5-149">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-component"></a><span data-ttu-id="864e5-150">配置脚本组件</span><span class="sxs-lookup"><span data-stu-id="864e5-150">Configuring the Script Component</span></span>  
 <span data-ttu-id="864e5-151">可以采用下列方法来配置脚本组件：</span><span class="sxs-lookup"><span data-stu-id="864e5-151">You can configure the Script component in the following ways:</span></span>  
  
-   <span data-ttu-id="864e5-152">选择要引用的输入列。</span><span class="sxs-lookup"><span data-stu-id="864e5-152">Select the input columns to reference.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="864e5-153">使用 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器时，可以仅配置一个输入。</span><span class="sxs-lookup"><span data-stu-id="864e5-153">You can configure only one input when you use the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
-   <span data-ttu-id="864e5-154">提供组件运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="864e5-154">Provide the script that the component runs.</span></span>  
  
-   <span data-ttu-id="864e5-155">指定脚本语言。</span><span class="sxs-lookup"><span data-stu-id="864e5-155">Specify the script language.</span></span>  
  
-   <span data-ttu-id="864e5-156">提供逗号分隔的只读和读/写变量列表。</span><span class="sxs-lookup"><span data-stu-id="864e5-156">Provide comma-separated lists of read-only and read/write variables.</span></span>  
  
-   <span data-ttu-id="864e5-157">添加更多输出，并且添加脚本要向其赋值的输出列。</span><span class="sxs-lookup"><span data-stu-id="864e5-157">Add more outputs, and add output columns to which the script assigns.</span></span>  
  
 <span data-ttu-id="864e5-158">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="864e5-158">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-component-in-the-designer"></a><span data-ttu-id="864e5-159">配置设计器中的脚本组件</span><span class="sxs-lookup"><span data-stu-id="864e5-159">Configuring the Script Component in the Designer</span></span>  
 <span data-ttu-id="864e5-160">有关可在 **“脚本转换编辑器”** 对话框中设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="864e5-160">For more information about the properties that you can set in the **Script Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="864e5-161">脚本转换编辑器（“输入列”页）</span><span class="sxs-lookup"><span data-stu-id="864e5-161">Script Transformation Editor &#40;Input Columns Page&#41;</span></span>](../../script-transformation-editor-input-columns-page.md)  
  
-   [<span data-ttu-id="864e5-162">脚本转换编辑器（“输入和输出”页）</span><span class="sxs-lookup"><span data-stu-id="864e5-162">Script Transformation Editor &#40;Inputs and Outputs Page&#41;</span></span>](../../script-transformation-editor-inputs-and-outputs-page.md)  
  
-   [<span data-ttu-id="864e5-163">脚本转换编辑器（“脚本”页）</span><span class="sxs-lookup"><span data-stu-id="864e5-163">Script Transformation Editor &#40;Script Page&#41;</span></span>](../../script-transformation-editor-script-page.md)  
  
-   [<span data-ttu-id="864e5-164">脚本转换编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="864e5-164">Script Transformation Editor &#40;Connection Managers Page&#41;</span></span>](../../script-transformation-editor-connection-managers-page.md)  
  
 <span data-ttu-id="864e5-165">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="864e5-165">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="864e5-166">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="864e5-166">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a><span data-ttu-id="864e5-167">以编程方式配置脚本组件</span><span class="sxs-lookup"><span data-stu-id="864e5-167">Configuring the Script Component Programmatically</span></span>  
 <span data-ttu-id="864e5-168">有关可在 **“属性”** 窗口中或以编程形式设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="864e5-168">For more information about the properties that you can set in the **Properties** window or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="864e5-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="864e5-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="864e5-170">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="864e5-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="864e5-171">有关如何设置属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="864e5-171">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="864e5-172">设置数据流组件的属性</span><span class="sxs-lookup"><span data-stu-id="864e5-172">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="864e5-173">相关内容</span><span class="sxs-lookup"><span data-stu-id="864e5-173">Related Content</span></span>  
 [<span data-ttu-id="864e5-174">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="864e5-174">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
 [<span data-ttu-id="864e5-175">使用脚本组件扩展数据流</span><span class="sxs-lookup"><span data-stu-id="864e5-175">Extending the Data Flow with the Script Component</span></span>](script-component.md)  
  
  
