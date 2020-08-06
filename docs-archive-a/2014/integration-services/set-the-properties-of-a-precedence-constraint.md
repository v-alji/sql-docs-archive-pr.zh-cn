---
title: 设置优先约束的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55b95bdb79d801156bef6198bc0f57accb5d9517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590271"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a><span data-ttu-id="a3b15-102">设置优先约束的属性</span><span class="sxs-lookup"><span data-stu-id="a3b15-102">Set the Properties of a Precedence Constraint</span></span>
  <span data-ttu-id="a3b15-103">若要设置优先约束属性，您可以使用下列工具之一：</span><span class="sxs-lookup"><span data-stu-id="a3b15-103">To set properties on precedence constraints, you can use one of these tools:</span></span>  
  
-   <span data-ttu-id="a3b15-104">可以使用 **“优先约束编辑器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="a3b15-104">You can use the **Precedence Constraint Editor** dialog box.</span></span>  
  
-   <span data-ttu-id="a3b15-105">可以使用“属性”窗口。</span><span class="sxs-lookup"><span data-stu-id="a3b15-105">You can use the Properties window.</span></span> <span data-ttu-id="a3b15-106">“属性”窗口列出了用于对 **“优先约束编辑器”** 对话框中未提供的优先约束进行配置的属性。</span><span class="sxs-lookup"><span data-stu-id="a3b15-106">The Properties window lists properties for configuring precedence constraints that are not available in the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="a3b15-107">在“属性”窗口中，您可以提供优先约束的说明和名称，也可以配置要在设计图面上为优先约束显示的批注。</span><span class="sxs-lookup"><span data-stu-id="a3b15-107">In the Properties window, you can provide a description and name of the precedence constraint, and configure the annotation to display for the precedence constraint on the design surface.</span></span>  
  
 <span data-ttu-id="a3b15-108">下面的过程介绍如何使用下列每种工具设置优先约束的属性。</span><span class="sxs-lookup"><span data-stu-id="a3b15-108">The following procedures describe how to set properties on precedence constraints by using each of these tools.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a><span data-ttu-id="a3b15-109">使用优先约束编辑器设置优先约束属性</span><span class="sxs-lookup"><span data-stu-id="a3b15-109">To set the properties of a precedence constraint by using the Precedence Constraint Editor</span></span>  
  
1.  <span data-ttu-id="a3b15-110">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="a3b15-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a3b15-111">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="a3b15-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a3b15-112">单击 **“控制流”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a3b15-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a3b15-113">双击优先约束。</span><span class="sxs-lookup"><span data-stu-id="a3b15-113">Double-click the precedence constraint.</span></span>  
  
     <span data-ttu-id="a3b15-114">**“优先约束编辑器”** 将打开。</span><span class="sxs-lookup"><span data-stu-id="a3b15-114">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="a3b15-115">在“求值运算”下拉列表中，选择求值运算。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a3b15-115">In the **Evaluation operation** drop-down list, select an evaluation operation.</span></span>  
  
6.  <span data-ttu-id="a3b15-116">在 `Value` 下拉列表中，选择优先可执行文件的执行结果。</span><span class="sxs-lookup"><span data-stu-id="a3b15-116">In the `Value` drop-down list, select the execution result of the precedence executable.</span></span>  
  
7.  <span data-ttu-id="a3b15-117">如果求值运算使用表达式，请在 `Expression` 框中键入表达式，然后单击 "**测试**" 以计算表达式。</span><span class="sxs-lookup"><span data-stu-id="a3b15-117">If the evaluation operation uses an expression, in the `Expression` box, type an expression, and click **Test** to evaluate the expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3b15-118">变量名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="a3b15-118">Variable names are case-sensitive.</span></span>  
  
8.  <span data-ttu-id="a3b15-119">如果多个任务或容器连接到受约束的可执行文件，请选择 "**逻辑与**" 以指定所有前面的可执行文件的执行结果必须计算为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a3b15-119">If multiple tasks or containers are connected to the constrained executable, select **Logical AND** to specify that the execution results of all preceding executables must evaluate to `true`.</span></span> <span data-ttu-id="a3b15-120">选择 "**逻辑或**" 以指定只有一个执行结果的计算结果为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a3b15-120">Select **Logical OR** to specify that only one execution result must evaluate to `true`.</span></span>  
  
9. <span data-ttu-id="a3b15-121">单击 **“确定”** ，关闭 **“优先约束编辑器”**。</span><span class="sxs-lookup"><span data-stu-id="a3b15-121">Click **OK** to close the **Precedence Constraint Editor**.</span></span>  
  
10. <span data-ttu-id="a3b15-122">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="a3b15-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a><span data-ttu-id="a3b15-123">使用“属性”窗口设置优先约束属性</span><span class="sxs-lookup"><span data-stu-id="a3b15-123">To set the properties of a precedence constraint by using the Properties window</span></span>  
  
1.  <span data-ttu-id="a3b15-124">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含要修改的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="a3b15-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to modify.</span></span>  
  
2.  <span data-ttu-id="a3b15-125">在解决方案资源管理器中，双击该包将其打开。</span><span class="sxs-lookup"><span data-stu-id="a3b15-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a3b15-126">单击 "**控制流**" 选项卡。在 "**控制流**" 选项卡的设计图面上，右键单击优先约束，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="a3b15-126">Click the **Control Flow** tab. On the design surface of the **Control Flow** tab, right-click the precedence constraint, and then click **Properties**.</span></span> <span data-ttu-id="a3b15-127">在“属性”窗口中修改属性值。</span><span class="sxs-lookup"><span data-stu-id="a3b15-127">In the Properties window, modify the property values.</span></span>  
  
4.  <span data-ttu-id="a3b15-128">在“属性”窗口中，设置优先约束的下列读/写属性：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a3b15-128">In the **Properties** window, set the following read/write properties of precedence constraints:</span></span>  
  
    |<span data-ttu-id="a3b15-129">读/写属性</span><span class="sxs-lookup"><span data-stu-id="a3b15-129">Read/write property</span></span>|<span data-ttu-id="a3b15-130">配置操作</span><span class="sxs-lookup"><span data-stu-id="a3b15-130">Configuration action</span></span>|  
    |--------------------------|--------------------------|  
    |<span data-ttu-id="a3b15-131">说明</span><span class="sxs-lookup"><span data-stu-id="a3b15-131">Description</span></span>|<span data-ttu-id="a3b15-132">提供说明。</span><span class="sxs-lookup"><span data-stu-id="a3b15-132">Provide a description.</span></span>|  
    |<span data-ttu-id="a3b15-133">EvalOp</span><span class="sxs-lookup"><span data-stu-id="a3b15-133">EvalOp</span></span>|<span data-ttu-id="a3b15-134">选择一个求值运算。</span><span class="sxs-lookup"><span data-stu-id="a3b15-134">Select an evaluation operation.</span></span> <span data-ttu-id="a3b15-135">如果 `Expression` 选择了、 **ExpressionAndConstant**或**expressionorconstant 运算**操作，则可以指定一个表达式。</span><span class="sxs-lookup"><span data-stu-id="a3b15-135">If the `Expression`, **ExpressionAndConstant**, or **ExpressionOrConstant** operation is selected, you can specify an expression.</span></span>|  
    |<span data-ttu-id="a3b15-136">Expression</span><span class="sxs-lookup"><span data-stu-id="a3b15-136">Expression</span></span>|<span data-ttu-id="a3b15-137">如果求值运算包含 and 表达式，则请提供一个表达式。</span><span class="sxs-lookup"><span data-stu-id="a3b15-137">If the evaluation operation includes and expression, provide an expression.</span></span> <span data-ttu-id="a3b15-138">表达式的计算结果必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="a3b15-138">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="a3b15-139">有关表达式语言的详细信息，请参阅 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a3b15-139">For more information about the expression language, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>|  
    |<span data-ttu-id="a3b15-140">LogicalAnd</span><span class="sxs-lookup"><span data-stu-id="a3b15-140">LogicalAnd</span></span>|<span data-ttu-id="a3b15-141">设置 `LogicalAnd` 此项可指定在多个可执行文件位于或链接到受约束的可执行文件时，优先约束与其他优先约束一起计算</span><span class="sxs-lookup"><span data-stu-id="a3b15-141">Set `LogicalAnd` to specify whether the precedence constraint is evaluated in concert with other precedence constraints, when multiple executables precede and are linked to the constrained executable</span></span>|  
    |<span data-ttu-id="a3b15-142">名称</span><span class="sxs-lookup"><span data-stu-id="a3b15-142">Name</span></span>|<span data-ttu-id="a3b15-143">更新优先约束的名称。</span><span class="sxs-lookup"><span data-stu-id="a3b15-143">Update the name of the precedence constraint.</span></span>|  
    |<span data-ttu-id="a3b15-144">ShowAnnotation</span><span class="sxs-lookup"><span data-stu-id="a3b15-144">ShowAnnotation</span></span>|<span data-ttu-id="a3b15-145">指定要使用的批注类型。</span><span class="sxs-lookup"><span data-stu-id="a3b15-145">Specify the type of annotation to use.</span></span> <span data-ttu-id="a3b15-146">选择 **Never** 可以禁用批注；选择 **AsNeeded** 可以启用按需批注；选择 **ConstraintName** 可以使用 Name 属性的值自动进行批注；选择 **ConstraintDescription** 可以使用 Description 属性的值自动进行批注；选择 **ConstraintOptions** 可以使用 Value 和 Expression 属性的值自动进行批注。</span><span class="sxs-lookup"><span data-stu-id="a3b15-146">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **ConstraintName** to automatically annotate using the value of the Name property, **ConstraintDescription** to automatically annotate using the value of the Description property, and **ConstraintOptions** to automatically annotate using the values of the Value and Expression properties.</span></span>|  
    |<span data-ttu-id="a3b15-147">值</span><span class="sxs-lookup"><span data-stu-id="a3b15-147">Value</span></span>|<span data-ttu-id="a3b15-148">如果在 EvalOP 属性中指定的求值运算包含约束，请选择受约束的可执行文件的执行结果。</span><span class="sxs-lookup"><span data-stu-id="a3b15-148">If the evaluation operation specified in the EvalOP property includes a constraint, select the execution result of the constraining executable.</span></span>|  
  
5.  <span data-ttu-id="a3b15-149">关闭“属性”窗口。</span><span class="sxs-lookup"><span data-stu-id="a3b15-149">Close the Properties window.</span></span>  
  
6.  <span data-ttu-id="a3b15-150">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="a3b15-150">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b15-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a3b15-151">See Also</span></span>  
 <span data-ttu-id="a3b15-152">[优先约束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="a3b15-152">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="a3b15-153">[使用默认优先约束来连接任务和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="a3b15-153">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="a3b15-154">[使用快捷菜单设置优先约束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="a3b15-154">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 [<span data-ttu-id="a3b15-155">在优先约束中使用表达式</span><span class="sxs-lookup"><span data-stu-id="a3b15-155">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
