---
title: For 循环容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6c864779237fdbf4dd249f87b7c06655293c047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576939"
---
# <a name="for-loop-container"></a><span data-ttu-id="3223a-102">For 循环容器</span><span class="sxs-lookup"><span data-stu-id="3223a-102">For Loop Container</span></span>
  <span data-ttu-id="3223a-103">For 循环容器定义包中的重复控制流。</span><span class="sxs-lookup"><span data-stu-id="3223a-103">The For Loop container defines a repeating control flow in a package.</span></span> <span data-ttu-id="3223a-104">此循环实现类似于编程语言中的 **For** 循环结构。</span><span class="sxs-lookup"><span data-stu-id="3223a-104">The loop implementation is similar to the **For** looping structure in programming languages.</span></span> <span data-ttu-id="3223a-105">循环每次重复时，For 循环容器都计算一个表达式并重复运行其工作流，直到表达式计算结果为 `False`。</span><span class="sxs-lookup"><span data-stu-id="3223a-105">In each repeat of the loop, the For Loop container evaluates an expression and repeats its workflow until the expression evaluates to `False`.</span></span>  
  
 <span data-ttu-id="3223a-106">For 循环容器使用下列元素定义循环：</span><span class="sxs-lookup"><span data-stu-id="3223a-106">The For Loop container usesthe following elements to define the loop:</span></span>  
  
-   <span data-ttu-id="3223a-107">为循环计数器赋值的可选初始化表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-107">An optional initialization expression that assigns values to the loop counters.</span></span>  
  
-   <span data-ttu-id="3223a-108">包含用于测试循环应停止还是继续的表达式的求值表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-108">An evaluation expression that contains the expression used to test whether the loop should stop or continue.</span></span>  
  
-   <span data-ttu-id="3223a-109">递增或递减循环计数器的可选迭代表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-109">An optional iteration expression that increments or decrements the loop counter.</span></span>  
  
 <span data-ttu-id="3223a-110">下图显示了一个具有发送邮件任务的 For 循环容器。</span><span class="sxs-lookup"><span data-stu-id="3223a-110">The following diagram shows a For Loop container with a Send Mail task.</span></span> <span data-ttu-id="3223a-111">如果初始化表达式为 `@Counter = 0`，求值表达式为 `@Counter < 4`，迭代表达式为 `@Counter = @Counter + 1`，则该循环将重复运行四次并发送四封电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3223a-111">If the initialization expression is `@Counter = 0`, the evaluation expression is `@Counter < 4`, and the iteration expression is `@Counter = @Counter + 1`, the loop repeats four times and sends four e-mail messages.</span></span>  
  
 <span data-ttu-id="3223a-112">![For 循环容器重复执行任务四次](../media/ssis-forloop.gif "For 循环容器重复执行任务四次")</span><span class="sxs-lookup"><span data-stu-id="3223a-112">![A For Loop container repeats a task four times](../media/ssis-forloop.gif "A For Loop container repeats a task four times")</span></span>  
  
 <span data-ttu-id="3223a-113">表达式必须是有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-113">The expressions must be valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="3223a-114">若要创建初始化和赋值表达式，可以使用赋值运算符 (=)。</span><span class="sxs-lookup"><span data-stu-id="3223a-114">To create the initialization and assignment expressions, you can use the assignment operator (=).</span></span> <span data-ttu-id="3223a-115">此运算符在其他方面不为 Integration Services 表达式语法所支持，只能供 For 循环容器中的初始化和赋值表达式类型使用。</span><span class="sxs-lookup"><span data-stu-id="3223a-115">This operator is not otherwise supported by the Integration Services expression grammar and can only be used by the initialization and assignment expression types in the For Loop container.</span></span> <span data-ttu-id="3223a-116">使用赋值运算符的任何表达式都必须使用语法 `@Var = <expression>`，其中 Var 是运行时变量，\<expression> 是遵循 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 表达式语法规则的表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-116">Any expression that uses the assignment operator must have the syntax `@Var = <expression>`, where **Var** is a run-time variable and \<expression> is an expression that follows the rules of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="3223a-117">表达式可以包含 SSIS 表达式语法支持的变量、文字以及任何运算符和函数。</span><span class="sxs-lookup"><span data-stu-id="3223a-117">The expression can include the variables, literals, and any operators and functions that the SSIS expression grammar supports.</span></span> <span data-ttu-id="3223a-118">表达式的计算结果的数据类型必须能够转换为变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3223a-118">The expression must evaluate to a data type that can be cast to the data type of the variable.</span></span>  
  
 <span data-ttu-id="3223a-119">一个 For 循环容器只能有一个求值表达式。</span><span class="sxs-lookup"><span data-stu-id="3223a-119">A For Loop container can have only one evaluation expression.</span></span> <span data-ttu-id="3223a-120">这意味着 For 循环容器对所有其控制流元素运行相同次数。</span><span class="sxs-lookup"><span data-stu-id="3223a-120">This means that the For Loop container runs all its control flow elements the same number of times.</span></span> <span data-ttu-id="3223a-121">因为 For 循环容器可以包含其他 For 循环容器，所以可以在包中构建嵌套循环和实现复杂循环。</span><span class="sxs-lookup"><span data-stu-id="3223a-121">Because the For Loop container can include other For Loop containers, you can build nested loops and implement complex looping in packages.</span></span>  
  
 <span data-ttu-id="3223a-122">可以为 For 循环容器设置一个事务属性，为包控制流的子集定义一个事务。</span><span class="sxs-lookup"><span data-stu-id="3223a-122">You can set a transaction property on the For Loop container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="3223a-123">采用这种方法，可以更详细地管理事务。</span><span class="sxs-lookup"><span data-stu-id="3223a-123">In this way, you can manage transactions at a more granular level.</span></span> <span data-ttu-id="3223a-124">例如，如果 For 循环容器多次重复一个更新表中数据的控制流，则可以配置 For 循环及其控制流，让它们使用一个事务来确保数据只有在全部数据都成功更新后才更新。</span><span class="sxs-lookup"><span data-stu-id="3223a-124">For example, if a For Loop container repeats a control flow that updates data in a table multiple times, you can configure the For Loop and its control flow to use a transaction to ensure that if not all data is updated successfully, no data is updated.</span></span> <span data-ttu-id="3223a-125">有关详细信息，请参阅 [Integration Services 事务](../integration-services-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="3223a-125">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-for-loop-container"></a><span data-ttu-id="3223a-126">For 循环容器的配置</span><span class="sxs-lookup"><span data-stu-id="3223a-126">Configuration of the For Loop Container</span></span>  
 <span data-ttu-id="3223a-127">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="3223a-127">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3223a-128">有关可以在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="3223a-128">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3223a-129">For 循环编辑器</span><span class="sxs-lookup"><span data-stu-id="3223a-129">For Loop Editor</span></span>](../for-loop-editor.md)  
  
-   [<span data-ttu-id="3223a-130">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="3223a-130">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="3223a-131">有关以编程方式设置这些属性的详细信息，请参阅开发人员指南中针对 **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** 类的文档。</span><span class="sxs-lookup"><span data-stu-id="3223a-131">For more information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3223a-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3223a-132">Related Tasks</span></span>  
 <span data-ttu-id="3223a-133">有关如何配置 For 循环容器的信息，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="3223a-133">For information about how to configure a For Loop Container, see the following topics.</span></span>  
  
-   [<span data-ttu-id="3223a-134">配置 For 循环容器</span><span class="sxs-lookup"><span data-stu-id="3223a-134">Configure a For Loop Container</span></span>](for-loop-container.md)  
  
-   [<span data-ttu-id="3223a-135">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="3223a-135">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="3223a-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3223a-136">See Also</span></span>  
 <span data-ttu-id="3223a-137">[控制流](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3223a-137">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="3223a-138">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="3223a-138">Integration Services &#40;SSIS&#41; Expressions</span></span>](../expressions/integration-services-ssis-expressions.md)  
  
  
