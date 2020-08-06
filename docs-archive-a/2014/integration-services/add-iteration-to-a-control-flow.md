---
title: 向控制流添加迭代 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- repeating workflows
- adding iterations
- control flow [Integration Services], iterations
- expressions [Integration Services], control flow
- iterations [Integration Services]
- For Loop containers
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b576ab080c541ef96987d3375215185f5cadb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585940"
---
# <a name="add-iteration-to-a-control-flow"></a><span data-ttu-id="ebee8-102">将迭代添加到控制流</span><span class="sxs-lookup"><span data-stu-id="ebee8-102">Add Iteration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="ebee8-103">包含 For 循环容器，此控制流元素使得可以更简便地包含按条件重复包中控制流的循环。</span><span class="sxs-lookup"><span data-stu-id="ebee8-103">includes the For Loop container, a control flow element that makes it simple to include looping that conditionally repeats a control flow in a package.</span></span> <span data-ttu-id="ebee8-104">有关详细信息，请参阅 [For 循环容器](control-flow/for-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-104">For more information, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
 <span data-ttu-id="ebee8-105">For 循环容器计算每次循环迭代的条件，并在该条件的计算结果为 false 时停止。</span><span class="sxs-lookup"><span data-stu-id="ebee8-105">The For Loop container evaluates a condition on each iteration of the loop, and stops when the condition evaluates to false.</span></span> <span data-ttu-id="ebee8-106">For 循环容器含有用于对循环进行初始化的表达式，并指定停止执行重复控制流的求值条件，以及为表达式（其更新与求值条件进行比较的值）赋值。</span><span class="sxs-lookup"><span data-stu-id="ebee8-106">The For Loop container includes expressions for initializing the loop, specifying the evaluation condition that stops execution of the repeating control flow, and assigning a value to an expression that updates the value against which the evaluation condition is compared.</span></span> <span data-ttu-id="ebee8-107">必须提供求值条件，但初始化表达式和赋值表达式为可选。</span><span class="sxs-lookup"><span data-stu-id="ebee8-107">You must provide an evaluation condition, but initialization and assignment expressions are optional.</span></span>  
  
 <span data-ttu-id="ebee8-108">For 循环容器不提供功能，只提供用来生成可重复的控制流的结构。</span><span class="sxs-lookup"><span data-stu-id="ebee8-108">The For Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow.</span></span> <span data-ttu-id="ebee8-109">若要提供容器功能，则 For 循环容器中必须至少包含一个任务。</span><span class="sxs-lookup"><span data-stu-id="ebee8-109">To provide container functionality, you must include at least one task in the For Loop container.</span></span> <span data-ttu-id="ebee8-110">有关详细信息，请参阅 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-110">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="ebee8-111">For 循环容器可包含具有多个任务的控制流，还可包含其他容器。</span><span class="sxs-lookup"><span data-stu-id="ebee8-111">The For Loop container can include a control flow with multiple tasks, and can include other containers.</span></span> <span data-ttu-id="ebee8-112">将任务和容器添加到 For 循环容器的过程与将它们添加到包的过程相似，不同的是将任务和容器拖动到 For 循环容器而不是拖动到包。</span><span class="sxs-lookup"><span data-stu-id="ebee8-112">Adding tasks and containers to a For Loop container is similar to adding them to a package, except you drag the tasks and containers to the For Loop container instead of to the package.</span></span> <span data-ttu-id="ebee8-113">如果 For 循环容器包含多个任务或容器，可以使用优先约束连接它们，就像在包中操作一样。</span><span class="sxs-lookup"><span data-stu-id="ebee8-113">If the For Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="ebee8-114">有关详细信息，请参阅 [优先约束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-114">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
## <a name="using-expressions-in-for-loop-configuration"></a><span data-ttu-id="ebee8-115">在 For 循环配置中使用表达式</span><span class="sxs-lookup"><span data-stu-id="ebee8-115">Using Expressions in For Loop Configuration</span></span>  
 <span data-ttu-id="ebee8-116">用指定求值条件、初始化值或赋值值的方法配置 For 循环容器时，可以使用文字或表达式。</span><span class="sxs-lookup"><span data-stu-id="ebee8-116">When you configure the For Loop container by specifying an evaluation condition, initialization value, or assignment value, you can use either literals or expressions.</span></span>  
  
 <span data-ttu-id="ebee8-117">表达式中可以包含变量。</span><span class="sxs-lookup"><span data-stu-id="ebee8-117">The expressions can include variables.</span></span> <span data-ttu-id="ebee8-118">使用变量的优点是变量可在运行时更新，使得包管理起来更灵活、更容易。</span><span class="sxs-lookup"><span data-stu-id="ebee8-118">The advantage of using variables is that they can be updated at run time, making the packages more flexible and easier to manage.</span></span> <span data-ttu-id="ebee8-119">表达式的最大长度为 4000 个字符。</span><span class="sxs-lookup"><span data-stu-id="ebee8-119">The maximum length of an expression is 4000 characters.</span></span>  
  
 <span data-ttu-id="ebee8-120">在表达式中指定变量时，必须在其前面加符号 @。</span><span class="sxs-lookup"><span data-stu-id="ebee8-120">When you specify a variable in an expression, you must preface the variable name with the at sign (@).</span></span> <span data-ttu-id="ebee8-121">例如，对于名为的变量 `Counter` ，请 @Counter 在 for 循环容器使用的表达式中输入。</span><span class="sxs-lookup"><span data-stu-id="ebee8-121">For example, for a variable named `Counter`, enter @Counter in the expression that the For Loop container uses.</span></span> <span data-ttu-id="ebee8-122">如果变量上包含了命名空间属性，则您必须用方括号将变量和命名空间括起来。</span><span class="sxs-lookup"><span data-stu-id="ebee8-122">If you include the namespace property on the variable, you must enclose the variable and namespace in brackets.</span></span> <span data-ttu-id="ebee8-123">例如，对于 `Counter` 命名空间中的变量 `MyNamespace` ，请键入 [ @MyNamespace::Counter ]。</span><span class="sxs-lookup"><span data-stu-id="ebee8-123">For example, for a `Counter` variable in the `MyNamespace` namespace, type [@MyNamespace::Counter].</span></span>  
  
 <span data-ttu-id="ebee8-124">For 循环容器使用的变量必须在 For 循环容器的范围内定义，或者在包容器层次结构中较高层次容器的范围内定义。</span><span class="sxs-lookup"><span data-stu-id="ebee8-124">The variables that the For Loop container uses must be defined in the scope of the For Loop container or in the scope of any container that is higher in the package container hierarchy.</span></span> <span data-ttu-id="ebee8-125">例如，For 循环容器可使用在其范围内定义的变量，也可使用在包范围内定义的变量。</span><span class="sxs-lookup"><span data-stu-id="ebee8-125">For example, a For Loop container can use variables defined in its scope and also variables defined in package scope.</span></span> <span data-ttu-id="ebee8-126">有关详细信息，请参阅 [Integration Services (SSIS) 变量](integration-services-ssis-variables.md)和[在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="ebee8-127">[!INCLUDE[ssIS](../includes/ssis-md.md)] 表达式语法提供了一整套运算符和函数，可以用于实现计算、初始化或赋值所用的复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="ebee8-127">The [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar provides a complete set of operators and functions for implementing complex expressions used for evaluation, initialization, or assignment.</span></span> <span data-ttu-id="ebee8-128">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-128">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
### <a name="to-implement-a-for-loop-container-in-a-control-flow"></a><span data-ttu-id="ebee8-129">在控制流中实现 For 循环容器</span><span class="sxs-lookup"><span data-stu-id="ebee8-129">To implement a For Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="ebee8-130">将 For 循环容器添加到包。</span><span class="sxs-lookup"><span data-stu-id="ebee8-130">Add the For Loop container to the package.</span></span> <span data-ttu-id="ebee8-131">有关详细信息，请参阅[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="ebee8-131">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="ebee8-132">.</span><span class="sxs-lookup"><span data-stu-id="ebee8-132">.</span></span>  
  
2.  <span data-ttu-id="ebee8-133">将任务和容器添加到 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="ebee8-133">Add tasks and containers to the For Loop container.</span></span> <span data-ttu-id="ebee8-134">有关详细信息，请参阅[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="ebee8-134">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="ebee8-135">.</span><span class="sxs-lookup"><span data-stu-id="ebee8-135">.</span></span>  
  
3.  <span data-ttu-id="ebee8-136">使用优先约束连接 For 循环容器中的任务和容器。</span><span class="sxs-lookup"><span data-stu-id="ebee8-136">Connect tasks and containers in the For Loop container using precedence constraints.</span></span> <span data-ttu-id="ebee8-137">有关详细信息，请参阅 [使用默认优先约束来连接任务和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-137">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="ebee8-138">配置 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="ebee8-138">Configure the For Loop container.</span></span> <span data-ttu-id="ebee8-139">有关详细信息，请参阅 [配置 For 循环容器](../../2014/integration-services/configure-a-for-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="ebee8-139">For more information, see [Configure a For Loop Container](../../2014/integration-services/configure-a-for-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebee8-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebee8-140">See Also</span></span>  
 <span data-ttu-id="ebee8-141">[在控制流中添加或删除任务或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ebee8-141">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="ebee8-142">[对组件进行分组或取消分组](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="ebee8-142">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="ebee8-143">[使用默认优先约束来连接任务和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="ebee8-143">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="ebee8-144">[向控制流添加枚举](../../2014/integration-services/add-enumeration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ebee8-144">[Add Enumeration to a Control Flow](../../2014/integration-services/add-enumeration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="ebee8-145">控制流</span><span class="sxs-lookup"><span data-stu-id="ebee8-145">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
