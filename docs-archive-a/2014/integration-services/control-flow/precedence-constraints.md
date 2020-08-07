---
title: 优先约束 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a08fd1d66e43ede4c54284518bab191be8997a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587959"
---
# <a name="precedence-constraints"></a><span data-ttu-id="64d44-102">优先约束</span><span class="sxs-lookup"><span data-stu-id="64d44-102">Precedence Constraints</span></span>
  <span data-ttu-id="64d44-103">优先约束在控制流中链接包中的可执行文件、容器和任务，并指定决定可执行文件是否运行的条件。</span><span class="sxs-lookup"><span data-stu-id="64d44-103">Precedence constraints link executables, containers, and tasks in packages in a control flow, and specify conditions that determine whether executables run.</span></span> <span data-ttu-id="64d44-104">可执行文件可以是 For 循环容器、Foreach 循环容器、序列容器、任务或事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="64d44-104">An executable can be a For Loop, Foreach Loop, or Sequence container; a task; or an event handler.</span></span> <span data-ttu-id="64d44-105">事件处理程序也使用优先约束将其可执行文件链接为控制流。</span><span class="sxs-lookup"><span data-stu-id="64d44-105">Event handlers also use precedence constraints to link their executables into a control flow.</span></span>

 <span data-ttu-id="64d44-106">优先约束链接两个可执行文件：优先可执行文件和受约束的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="64d44-106">A precedence constraint links two executables: the precedence executable and the constrained executable.</span></span> <span data-ttu-id="64d44-107">优先可执行文件先于受约束的可执行文件运行，而优先可执行文件的执行结果可能决定受约束的可执行文件是否运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-107">The precedence executable runs before the constrained executable, and the execution result of the precedence executable may determine whether the constrained executable runs.</span></span> <span data-ttu-id="64d44-108">下列关系图显示由优先约束链接的两个可执行文件。</span><span class="sxs-lookup"><span data-stu-id="64d44-108">The following diagram shows two executables linked by a precedence constraint.</span></span>

 <span data-ttu-id="64d44-109">![由优先约束连接的可执行文件](../media/ssis-pcsimple.gif "由优先约束连接的可执行文件")</span><span class="sxs-lookup"><span data-stu-id="64d44-109">![Executables connected by a precedence constraint](../media/ssis-pcsimple.gif "Executables connected by a precedence constraint")</span></span>

 <span data-ttu-id="64d44-110">在线性控制流（即不分支的控制流）中，优先约束独自控制任务运行的顺序。</span><span class="sxs-lookup"><span data-stu-id="64d44-110">In a linear control flow, that is, one without branching, precedence constraints alone govern the sequence in which tasks run.</span></span> <span data-ttu-id="64d44-111">如果控制流有分支，则由 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行时引擎决定紧随分支之后的任务和容器的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="64d44-111">If a control flow branches, the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine determines the execution order among the tasks and containers that immediately follow the branching.</span></span> <span data-ttu-id="64d44-112">运行时引擎还决定着控制流中未连接的工作流的执行顺序。</span><span class="sxs-lookup"><span data-stu-id="64d44-112">The run-time engine also determines execution order among unconnected workflows in a control flow.</span></span>

 <span data-ttu-id="64d44-113">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的嵌套容器体系结构使得所有容器（除仅封装单个任务的任务宿主容器之外）均可包含其他容器，且每个容器都有自己的控制流。</span><span class="sxs-lookup"><span data-stu-id="64d44-113">The nested-container architecture of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enables all containers, except for the task host container that encapsulates only a single task, to include other containers, each with its own control flow.</span></span> <span data-ttu-id="64d44-114">For 循环容器、Foreach 循环容器和序列容器可以包含多个任务和其他容器，而这些任务和容器又可以包含多个任务和容器，如此逐层嵌套。</span><span class="sxs-lookup"><span data-stu-id="64d44-114">The For Loop, Foreach Loop, and Sequence containers can include multiple tasks and other containers, which in turn can include multiple tasks and containers.</span></span> <span data-ttu-id="64d44-115">例如，带有脚本任务和序列容器的包具有链接该脚本任务和序列容器的优先约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-115">For example, a package with a Script task and a Sequence container has a precedence constraint that links the Script task and the Sequence container.</span></span> <span data-ttu-id="64d44-116">序列容器包含三个脚本任务，且容器的优先约束将此三个脚本任务链接为控制流。</span><span class="sxs-lookup"><span data-stu-id="64d44-116">The Sequence container includes three Script tasks, and its precedence constraints link the three Script tasks into a control flow.</span></span> <span data-ttu-id="64d44-117">下列关系图显示包中带有两级嵌套的优先约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-117">The following diagram shows the precedence constraints in a package with two levels of nesting.</span></span>

 <span data-ttu-id="64d44-118">![包中的优先约束](../media/mw-dts-12.gif "包中的优先约束")</span><span class="sxs-lookup"><span data-stu-id="64d44-118">![Precedence contraints in a package](../media/mw-dts-12.gif "Precedence contraints in a package")</span></span>

 <span data-ttu-id="64d44-119">由于包位于 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 容器层次结构的顶部，因此优先约束不能链接多个包；但是可以向包添加执行包任务并间接地将其他包链接到控制流中。</span><span class="sxs-lookup"><span data-stu-id="64d44-119">Because the package is at the top of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] container hierarchy, multiple packages cannot be linked by precedence constraints; however, you can add an Execute Package task to a package and indirectly link another package into the control flow.</span></span>

 <span data-ttu-id="64d44-120">可以使用下列方式配置优先约束：</span><span class="sxs-lookup"><span data-stu-id="64d44-120">You can configure precedence constraints in the following ways:</span></span>

-   <span data-ttu-id="64d44-121">指定求值运算。</span><span class="sxs-lookup"><span data-stu-id="64d44-121">Specify an evaluation operation.</span></span> <span data-ttu-id="64d44-122">优先约束同时使用约束值和表达式，或者使用其中任一个来决定受约束的可执行文件是否运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-122">The precedence constraint uses a constraint value, an expression, both, or either to determine whether the constrained executable runs.</span></span>

-   <span data-ttu-id="64d44-123">如果优先约束使用执行结果，则您可以指定执行结果成功、失败或完成。</span><span class="sxs-lookup"><span data-stu-id="64d44-123">If the precedence constraint uses an execution result, you can specify the execution result to be success, failure, or completion.</span></span>

-   <span data-ttu-id="64d44-124">如果优先约束使用计算结果，则您可以提供计算结果为布尔值的表达式。</span><span class="sxs-lookup"><span data-stu-id="64d44-124">If the precedence constraint uses an evaluation result, you can provide an expression that evaluates to a Boolean.</span></span>

-   <span data-ttu-id="64d44-125">指定优先约束是单独计算还是与应用于受约束可执行文件的其他约束一起计算。</span><span class="sxs-lookup"><span data-stu-id="64d44-125">Specify whether the precedence constraint is evaluated singly or together with other constraints that apply to the constrained executable.</span></span>

## <a name="evaluation-operations"></a><span data-ttu-id="64d44-126">求值运算</span><span class="sxs-lookup"><span data-stu-id="64d44-126">Evaluation Operations</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="64d44-127">提供下列求值运算：</span><span class="sxs-lookup"><span data-stu-id="64d44-127">provides the following evaluation operations:</span></span>

-   <span data-ttu-id="64d44-128">仅使用优先可执行文件的执行结果来决定受约束的可执行文件是否运行的约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-128">A constraint that uses only the execution result of the precedence executable to determine whether the constrained executable runs.</span></span> <span data-ttu-id="64d44-129">优先可执行文件的执行结果可以为完成、成功或失败。</span><span class="sxs-lookup"><span data-stu-id="64d44-129">The execution result of the precedence executable can be completion, success, or failure.</span></span> <span data-ttu-id="64d44-130">这是默认操作。</span><span class="sxs-lookup"><span data-stu-id="64d44-130">This is the default operation.</span></span>

-   <span data-ttu-id="64d44-131">求值以决定受约束的可执行文件是否运行的表达式。</span><span class="sxs-lookup"><span data-stu-id="64d44-131">An expression that is evaluated to determine whether the constrained executable runs.</span></span> <span data-ttu-id="64d44-132">如果表达式计算结果为 true，则受约束的可执行文件运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-132">If the expression evaluates to true, the constrained executable runs.</span></span>

-   <span data-ttu-id="64d44-133">组合了对优先可执行文件执行结果以及对计算表达式返回结果的要求的表达式和约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-133">An expression and a constraint that combines the requirements of execution results of the precedence executable and the return results of evaluating the expression.</span></span>

-   <span data-ttu-id="64d44-134">使用优先可执行文件执行结果或使用计算表达式返回结果的表达式或约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-134">An expression or a constraint that uses either the execution results of the precedence executable or the return results of evaluating the expression.</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="64d44-135">设计器用颜色标识优先约束的类型。</span><span class="sxs-lookup"><span data-stu-id="64d44-135">Designer uses color to identify the type of precedence constraint.</span></span> <span data-ttu-id="64d44-136">“成功”约束为绿色，“失败”约束为红色，而“完成”约束为蓝色。</span><span class="sxs-lookup"><span data-stu-id="64d44-136">The Success constraint is green, the Failure constraint is red, and the Completion constraint is blue.</span></span> <span data-ttu-id="64d44-137">若要在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中显示表明约束类型的文本标签，则必须配置 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器的可访问性功能。</span><span class="sxs-lookup"><span data-stu-id="64d44-137">To display text labels in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer that show the type of the constraint, you must configure the accessibility features of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="64d44-138">表达式必须是有效的 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 表达式，且可以包含函数、运算符以及系统和自定义变量。</span><span class="sxs-lookup"><span data-stu-id="64d44-138">The expression must be a valid [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression, and it can include functions, operators, and system and custom variables.</span></span> <span data-ttu-id="64d44-139">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)和 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="64d44-139">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>

## <a name="execution-results"></a><span data-ttu-id="64d44-140">执行结果</span><span class="sxs-lookup"><span data-stu-id="64d44-140">Execution Results</span></span>
 <span data-ttu-id="64d44-141">优先约束可以单独使用下列执行结果或将这些结果与表达式结合使用。</span><span class="sxs-lookup"><span data-stu-id="64d44-141">The precedence constraint can use the following execution results alone or in combination with an expression.</span></span>

-   <span data-ttu-id="64d44-142">完成仅要求优先可执行文件完成而不考虑结果，受约束的执行文件便可运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-142">Completion requires only that the precedence executable has completed, without regard to outcome, in order for the constrained executable to run.</span></span>

-   <span data-ttu-id="64d44-143">成功要求优先可执行文件必须成功完成，受约束的可执行文件才能运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-143">Success requires that the precedence executable must complete successfully for the constrained executable to run.</span></span>

-   <span data-ttu-id="64d44-144">失败要求优先可执行文件失败，受约束的可执行文件便可运行。</span><span class="sxs-lookup"><span data-stu-id="64d44-144">Failure requires that the precedence executable fail for the constrained executable to run.</span></span>

> [!NOTE]
>  <span data-ttu-id="64d44-145">优先约束必须为相同 `Precedence Constraint` 集合的成员，才能组成逻辑与条件。</span><span class="sxs-lookup"><span data-stu-id="64d44-145">Only precedence constraints that are members of the same `Precedence Constraint` collection can be grouped in a logical AND condition.</span></span> <span data-ttu-id="64d44-146">例如，不能组合来自两个 Foreach 循环容器的优先约束。</span><span class="sxs-lookup"><span data-stu-id="64d44-146">For example, you cannot combine precedence constraints from two Foreach Loop containers.</span></span>

## <a name="configuration-of-the-precedence-constraint"></a><span data-ttu-id="64d44-147">优先约束的配置</span><span class="sxs-lookup"><span data-stu-id="64d44-147">Configuration of the Precedence Constraint</span></span>
 <span data-ttu-id="64d44-148">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="64d44-148">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>

 <span data-ttu-id="64d44-149">有关可以在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的信息，请参阅 [优先约束编辑器](../precedence-constraint-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="64d44-149">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Precedence Constraint Editor](../precedence-constraint-editor.md).</span></span>

 <span data-ttu-id="64d44-150">有关如何以编程方式设置这些属性的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>。</span><span class="sxs-lookup"><span data-stu-id="64d44-150">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="64d44-151">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="64d44-151">Related Tasks</span></span>
 <span data-ttu-id="64d44-152">有关如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="64d44-152">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>

-   [<span data-ttu-id="64d44-153">设置优先约束的属性</span><span class="sxs-lookup"><span data-stu-id="64d44-153">Set the Properties of a Precedence Constraint</span></span>](../set-the-properties-of-a-precedence-constraint.md)

-   [<span data-ttu-id="64d44-154">使用快捷菜单设置优先约束的值</span><span class="sxs-lookup"><span data-stu-id="64d44-154">Set the Value of a Precedence Constraint by Using the Shortcut Menu</span></span>](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)

-   [<span data-ttu-id="64d44-155">使用默认优先约束来连接任务和容器</span><span class="sxs-lookup"><span data-stu-id="64d44-155">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)

     <span data-ttu-id="64d44-156">本主题提供有关如何设置优先约束的默认行为以及如何用默认优先约束来连接可执行文件的信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="64d44-156">This topic provides information on how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints, see.</span></span>

## <a name="related-content"></a><span data-ttu-id="64d44-157">相关内容</span><span class="sxs-lookup"><span data-stu-id="64d44-157">Related Content</span></span>
 <span data-ttu-id="64d44-158">social.technet.microsoft.com 上的技术文章 [SSIS 表达式示例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="64d44-158">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>

## <a name="see-also"></a><span data-ttu-id="64d44-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64d44-159">See Also</span></span>
 <span data-ttu-id="64d44-160">[将表达式添加到优先约束](../add-expressions-to-precedence-constraints.md)[多个优先约束](../multiple-precedence-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="64d44-160">[Add Expressions to Precedence Constraints](../add-expressions-to-precedence-constraints.md) [Multiple Precedence Constraints](../multiple-precedence-constraints.md)</span></span>


