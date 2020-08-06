---
title: 添加或更改属性表达式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], creating
- expressions [Integration Services], property expressions
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d6d12fbe46930818af2b47b59620963d39616e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588676"
---
# <a name="add-or-change-a-property-expression"></a><span data-ttu-id="4d98a-102">添加或更改属性表达式</span><span class="sxs-lookup"><span data-stu-id="4d98a-102">Add or Change a Property Expression</span></span>
  <span data-ttu-id="4d98a-103">可以为包、任务、Foreach 循环容器、For 循环容器、序列容器、事件处理程序、包和项目级别连接管理器以及日志提供程序创建属性表达式。</span><span class="sxs-lookup"><span data-stu-id="4d98a-103">You can create property expressions for packages, tasks, Foreach Loop containers, For Loop containers, Sequence containers, event handlers, package and project level connection managers, and log providers.</span></span>  
  
 <span data-ttu-id="4d98a-104">若要创建或更改属性表达式，您可以使用 **“属性表达式编辑器”** 或 **“表达式生成器”** 。</span><span class="sxs-lookup"><span data-stu-id="4d98a-104">To create or change property expressions, you can use either the **Property Expressions Editor** or **Expression Builder**.</span></span> <span data-ttu-id="4d98a-105">可以从任务和容器使用的自定义编辑器中访问 **“属性表达式编辑器”** ，也可以从 **“属性”** 窗口中进行访问。</span><span class="sxs-lookup"><span data-stu-id="4d98a-105">The **Property Expressions Editor** can be accessed from either the custom editors that are available for tasks and containers, or from the **Properties** window.</span></span> <span data-ttu-id="4d98a-106">可以从 **“属性表达式编辑器”** 内部访问 **“表达式生成器”** 。</span><span class="sxs-lookup"><span data-stu-id="4d98a-106">**Expression Builder** can be accessed from inside the **Property Expressions Editor**.</span></span> <span data-ttu-id="4d98a-107">在 **“属性表达式编辑器”** 或 **“表达式生成器”** 中编写表达式时， **“表达式生成器”** 提供一组图形工具，可以非常容易地生成复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="4d98a-107">While you can write expressions in either the **Property Expressions Editor** or **Expression Builder**, **Expression Builder** provides a graphical set of tools that makes it simple to build complex expressions.</span></span>  
  
 <span data-ttu-id="4d98a-108">若要了解 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的语法、运算符和函数的详细信息，请参阅[运算符（SSIS 表达式）](operators-ssis-expression.md)和[函数（SSIS 表达式）](functions-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="4d98a-108">To learn more about the syntax, operators, and functions that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, see [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) and [Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md).</span></span> <span data-ttu-id="4d98a-109">每个运算符或函数的主题都包括在表达式中使用该运算符或函数的示例。</span><span class="sxs-lookup"><span data-stu-id="4d98a-109">The topic for each operator or function includes examples of using that operator or function in an expression.</span></span> <span data-ttu-id="4d98a-110">有关更复杂的表达式示例，请参阅 [在包中使用属性表达式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="4d98a-110">For examples of more complex expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
### <a name="to-create-or-change-a-property-expression"></a><span data-ttu-id="4d98a-111">创建或更改属性表达式</span><span class="sxs-lookup"><span data-stu-id="4d98a-111">To create or change a property expression</span></span>  
  
1.  <span data-ttu-id="4d98a-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开包含所需 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的项目。</span><span class="sxs-lookup"><span data-stu-id="4d98a-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="4d98a-113">在解决方案资源管理器中，双击该包将其打开，再执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="4d98a-113">In Solution Explorer, double-click the package to open it, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="4d98a-114">如果该项是一个任务或一个容器，请双击该项，再单击编辑器中的“表达式”  。</span><span class="sxs-lookup"><span data-stu-id="4d98a-114">If the item is a task or a container, double-click the item, and then click **Expressions** in the editor.</span></span>  
  
    -   <span data-ttu-id="4d98a-115">右键单击项，再单击  “属性”。</span><span class="sxs-lookup"><span data-stu-id="4d98a-115">Right-click the item and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4d98a-116">单击“表达式”框，再单击省略号 (…)  。</span><span class="sxs-lookup"><span data-stu-id="4d98a-116">Click in the **Expressions** box and then click the ellipsis (...).</span></span>  
  
4.  <span data-ttu-id="4d98a-117">在 **“属性表达式编辑器”** 中的 **“属性”** 列表中选择某个属性，然后执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="4d98a-117">In the **Property Expressions Editor**, select a property in the **Property** list, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="4d98a-118">在 **“表达式”** 列中直接键入或更改属性表达式，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4d98a-118">Type or change the property expression directly in the **Expression** column, and then click **OK**.</span></span>  
  
         <span data-ttu-id="4d98a-119">-或-</span><span class="sxs-lookup"><span data-stu-id="4d98a-119">-or-</span></span>  
  
    -   <span data-ttu-id="4d98a-120">单击属性的表达式行中的省略号 (...) 以打开“表达式生成器”  。</span><span class="sxs-lookup"><span data-stu-id="4d98a-120">Click the ellipsis (...) in the expression row of the property to open the **Expression Builder**.</span></span>  
  
5.  <span data-ttu-id="4d98a-121">（可选）在“表达式生成器”  中，执行下列任一任务：</span><span class="sxs-lookup"><span data-stu-id="4d98a-121">(Optional) In the **Expression Builder**, do any of the following tasks:</span></span>  
  
    -   <span data-ttu-id="4d98a-122">若要访问系统和用户定义的变量，请展开  “变量”。</span><span class="sxs-lookup"><span data-stu-id="4d98a-122">To access system and user-defined variables, expand **Variables**.</span></span>  
  
    -   <span data-ttu-id="4d98a-123">若要访问 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 表达式语言提供的函数、转换和运算符，请展开“数学函数”、“字符串函数”、“日期/时间函数”、“NULL 函数”、“类型转换”和“运算符”       。</span><span class="sxs-lookup"><span data-stu-id="4d98a-123">To access the functions, the casts, and the operators that the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression language provides, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators**.</span></span>  
  
    -   <span data-ttu-id="4d98a-124">若要在 **“表达式生成器”** 中生成或更改表达式，请将变量、列、函数、运算符和转换拖到 **“表达式”** 框中，也可以在该框中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="4d98a-124">To build or change an expression in the **Expression Builder**, drag variables, columns, functions, operators, and casts to the **Expression** box, or type the expression in the box.</span></span>  
  
    -   <span data-ttu-id="4d98a-125">若要查看表达式的计算结果，请在 **“表达式生成器”** 中单击 **“计算表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="4d98a-125">To view the evaluation result of the expression, click **Evaluate Expression** in the **Expression Builder**.</span></span>  
  
         <span data-ttu-id="4d98a-126">如果表达式无效，则将出现描述表达式语法错误的警报。</span><span class="sxs-lookup"><span data-stu-id="4d98a-126">If the expression is not valid, an alert appears that describes the syntax errors in the expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4d98a-127">计算表达式时不会将计算结果分配给属性。</span><span class="sxs-lookup"><span data-stu-id="4d98a-127">Evaluating an expression does not assign the evaluation result to the property.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d98a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d98a-128">See Also</span></span>  
 <span data-ttu-id="4d98a-129">[Integration Services (SSIS) 表达式](integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-129">[Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="4d98a-130">[在包中使用属性表达式](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-130">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="4d98a-131">[Integration Services (SSIS) 包](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-131">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="4d98a-132">[Integration Services 容器](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-132">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="4d98a-133">[Integration Services 任务](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-133">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="4d98a-134">[Integration Services (SSIS) 事件处理程序](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="4d98a-135">[Integration Services (SSIS) 连接](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="4d98a-135">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="4d98a-136">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="4d98a-136">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)  
  
  
