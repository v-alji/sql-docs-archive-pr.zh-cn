---
title: Integration Services (SSIS) 表达式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff0bd46034108537ebede7567b042997c94871ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689990"
---
# <a name="integration-services-ssis-expressions"></a><span data-ttu-id="2ad09-102">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="2ad09-102">Integration Services (SSIS) Expressions</span></span>
  <span data-ttu-id="2ad09-103">表达式是生成单个数据值的符号（标识符、文字、函数和运算符）的组合。</span><span class="sxs-lookup"><span data-stu-id="2ad09-103">An expression is a combination of symbols-identifiers, literals, functions, and operators-that yields a single data value.</span></span> <span data-ttu-id="2ad09-104">简单的表达式可以是单个常量、变量或函数。</span><span class="sxs-lookup"><span data-stu-id="2ad09-104">Simple expressions can be a single constant, variable, or function.</span></span> <span data-ttu-id="2ad09-105">更多情况下，表达式较为复杂，会使用多个运算符和函数，并且引用多个列和变量。</span><span class="sxs-lookup"><span data-stu-id="2ad09-105">More frequently, expressions are complex, using multiple operators and functions and referencing multiple columns and variables.</span></span> <span data-ttu-id="2ad09-106">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，表达式可以用于定义 CASE 语句的条件，创建和更新数据列中的值，为变量赋值，在运行时更新或填充属性，定义优先约束中的约束，以及提供 For 循环容器所使用的表达式。</span><span class="sxs-lookup"><span data-stu-id="2ad09-106">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expressions can be used to define conditions for CASE statements, create and update values in data columns, assign values to variables, update or populate properties at run time, define constraints in precedence constraints, and provide the expressions used by the For Loop container.</span></span>  
  
 <span data-ttu-id="2ad09-107">表达式基于表达式语言和表达式计算器。</span><span class="sxs-lookup"><span data-stu-id="2ad09-107">Expressions are based on an expression language, and the expression evaluator.</span></span> <span data-ttu-id="2ad09-108">表达式计算器分析表达式，并确定表达式是否按照表达式语言的规则执行。</span><span class="sxs-lookup"><span data-stu-id="2ad09-108">The expression evaluator parses the expression and determines whether the expression follows the rules of the expression language.</span></span> <span data-ttu-id="2ad09-109">有关表达式语法和支持的文本和标识符的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="2ad09-109">For more information about the expression syntax and supported literals and identifiers, see the following topics.</span></span>  
  
-   [<span data-ttu-id="2ad09-110">语法 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="2ad09-110">Syntax &#40;SSIS&#41;</span></span>](syntax-ssis.md)  
  
-   [<span data-ttu-id="2ad09-111">文字 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="2ad09-111">Literals &#40;SSIS&#41;</span></span>](numeric-string-and-boolean-literals.md)  
  
-   [<span data-ttu-id="2ad09-112">标识符 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="2ad09-112">Identifiers &#40;SSIS&#41;</span></span>](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a><span data-ttu-id="2ad09-113">使用表达式的组件</span><span class="sxs-lookup"><span data-stu-id="2ad09-113">Components that Use Expressions</span></span>  
 <span data-ttu-id="2ad09-114">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的下列元素可以使用表达式：</span><span class="sxs-lookup"><span data-stu-id="2ad09-114">The following elements in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can use expressions:</span></span>  
  
-   <span data-ttu-id="2ad09-115">有条件拆分转换可以根据表达式实现决策结构，将数据行定向到不同目标。</span><span class="sxs-lookup"><span data-stu-id="2ad09-115">The Conditional Split transformation implements a decision structure based on expressions to direct data rows to different destinations.</span></span> <span data-ttu-id="2ad09-116">有条件拆分转换中所使用的表达式的计算结果必须为 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="2ad09-116">Expressions used in a Conditional Split transformation must evaluate to `true` or `false`.</span></span> <span data-ttu-id="2ad09-117">例如，如果行满足表达式“Column1 > Column2”中的条件，则可以路由到单独的输出。</span><span class="sxs-lookup"><span data-stu-id="2ad09-117">For example, rows that meet the condition in the expression "Column1 > Column2" can be routed to a separate output.</span></span>  
  
-   <span data-ttu-id="2ad09-118">派生列转换使用通过表达式所创建的值来填充数据流中的新列或更新现有列。</span><span class="sxs-lookup"><span data-stu-id="2ad09-118">The Derived Column transformation uses values created by using expressions either to populate new columns in a data flow, or to update existing columns.</span></span> <span data-ttu-id="2ad09-119">例如，表达式 Column1 + " ABC" 可以用于更新值，或创建具有串联字符串的新值。</span><span class="sxs-lookup"><span data-stu-id="2ad09-119">For example, the expression Column1 + " ABC" can be used to update a value or to create a new value with the concatenated string.</span></span>  
  
-   <span data-ttu-id="2ad09-120">变量可以使用表达式来设置其值。</span><span class="sxs-lookup"><span data-stu-id="2ad09-120">Variables use an expression to set their value.</span></span> <span data-ttu-id="2ad09-121">例如，GETDATE() 可以将变量的值设置为当前日期。</span><span class="sxs-lookup"><span data-stu-id="2ad09-121">For example, GETDATE() sets the value of the variable to the current date.</span></span>  
  
-   <span data-ttu-id="2ad09-122">优先约束可以使用表达式指定确定在包中运行约束任务还是容器的条件。</span><span class="sxs-lookup"><span data-stu-id="2ad09-122">Precedence constraints can use expressions to specify the conditions that determine whether the constrained task or container in a package runs.</span></span> <span data-ttu-id="2ad09-123">优先约束中使用的表达式的计算结果必须为 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="2ad09-123">Expressions used in a precedence constraint must evaluate to `true` or `false`.</span></span> <span data-ttu-id="2ad09-124">例如，表达式“\@A > \@B”比较两个用户定义的变量，以确定是否运行受约束任务。</span><span class="sxs-lookup"><span data-stu-id="2ad09-124">For example, the expression \@A > \@B compares two user-defined variables to determine whether the constrained task runs.</span></span>  
  
-   <span data-ttu-id="2ad09-125">For 循环容器可以使用表达式来生成循环结构使用的初始化语句、计算语句、增量语句。</span><span class="sxs-lookup"><span data-stu-id="2ad09-125">The For Loop container can use expressions to build the initialization, evaluation, and the incrementing statements that the looping structure uses.</span></span> <span data-ttu-id="2ad09-126">例如，表达式 \@Counter = 1 初始化循环计数器。</span><span class="sxs-lookup"><span data-stu-id="2ad09-126">For example, the expression \@Counter = 1 initializes the loop counter.</span></span>  
  
 <span data-ttu-id="2ad09-127">表达式还可以用于更新包、容器（如 For 循环和 Foreach 循环）、任务、包和项目级连接管理器、日志提供程序以及 Foreach 枚举器的属性值。</span><span class="sxs-lookup"><span data-stu-id="2ad09-127">Expressions can also be used to update the values of properties of packages, containers such as the For Loop and Foreach Loop, tasks, package and project level connection managers, log providers, and Foreach enumerators.</span></span> <span data-ttu-id="2ad09-128">例如，使用属性表达式，可以将字符串“Localhost.AdventureWorks”分配给执行 SQL 任务的 ConnectionName 属性。</span><span class="sxs-lookup"><span data-stu-id="2ad09-128">For example, using a property expression, the string "Localhost.AdventureWorks" can be assigned to the ConnectionName property of the Execute SQL task.</span></span> <span data-ttu-id="2ad09-129">有关详细信息，请参阅 [在包中使用属性表达式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad09-129">For more information, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="icon-markers-for-expressions"></a><span data-ttu-id="2ad09-130">表达式的图标标记</span><span class="sxs-lookup"><span data-stu-id="2ad09-130">Icon Markers for Expressions</span></span>  
 <span data-ttu-id="2ad09-131">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，设置有表达式的连接管理器、变量和任务旁边会显示特殊的图标标记。</span><span class="sxs-lookup"><span data-stu-id="2ad09-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a special icon marker displays next to connection managers, variables, and tasks that have expressions set on them.</span></span> <span data-ttu-id="2ad09-132">**HasExpressions** 属性在支持表达式（变量除外）的所有 SSIS 对象上均可用。</span><span class="sxs-lookup"><span data-stu-id="2ad09-132">The **HasExpressions** property is available on all SSIS objects that support expresions, with the exception of variables.</span></span> <span data-ttu-id="2ad09-133">通过该属性，您可以轻松识别出哪些对象具有表达式。</span><span class="sxs-lookup"><span data-stu-id="2ad09-133">The property enables you to easily identy which objects have expressions.</span></span>  
  
## <a name="expression-builder"></a><span data-ttu-id="2ad09-134">表达式生成器</span><span class="sxs-lookup"><span data-stu-id="2ad09-134">Expression Builder</span></span>  
 <span data-ttu-id="2ad09-135">表达式生成器是一种用于生成表达式的图形工具。</span><span class="sxs-lookup"><span data-stu-id="2ad09-135">The expression builder is a graphical tool for building expressions.</span></span> <span data-ttu-id="2ad09-136">**“有条件拆分转换编辑器”** 对话框、 **“派生列转换编辑器”** 对话框和 **“表达式生成器”** 对话框中提供的表达式生成器是用于生成表达式的图形工具。</span><span class="sxs-lookup"><span data-stu-id="2ad09-136">It is available in the **Conditional Split Transformation Editor**, **Derived Column Transformation Editor** dialog boxes, and in the **Expression Builder** dialog box, is a graphical tool for building expressions.</span></span>  
  
 <span data-ttu-id="2ad09-137">表达式生成器提供包含包特定元素的文件夹，还提供包含表达式语言所提供的函数、类型转换和运算符的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2ad09-137">The expression builder provides folders that contain package-specific elements, and folders that contain the functions, type casts, and operators that the expression language provides.</span></span> <span data-ttu-id="2ad09-138">包特定元素包括系统变量和用户定义的变量。</span><span class="sxs-lookup"><span data-stu-id="2ad09-138">The package-specific elements include system variables and user-defined variables.</span></span> <span data-ttu-id="2ad09-139">在 **“有条件拆分转换编辑器”** 对话框和 **“派生列转换编辑器”** 对话框中，您还可以查看数据列。</span><span class="sxs-lookup"><span data-stu-id="2ad09-139">In the **Conditional Split Transformation Editor** and **Derived Column Transformation Editor** dialog boxes, you can also view data columns.</span></span> <span data-ttu-id="2ad09-140">若要为转换生成表达式，可以将项从文件夹中拖到 **“条件”** 或 **“表达式”** 列中，也可以直接在列中键入表达式。</span><span class="sxs-lookup"><span data-stu-id="2ad09-140">To build expressions for the transformations, you can drag items from the folders to the **Condition** or **Expression** column or you can type the expression directly in the column.</span></span> <span data-ttu-id="2ad09-141">表达式生成器会自动添加所需的语法元素，如变量名的 \@ 前缀。</span><span class="sxs-lookup"><span data-stu-id="2ad09-141">The expression builder automatically adds needed syntax elements such as the \@ prefix on variable names.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ad09-142">用户定义的变量名和系统变量名区分大小写。</span><span class="sxs-lookup"><span data-stu-id="2ad09-142">The names of user-defined and system variables are case-sensitive.</span></span>  
  
 <span data-ttu-id="2ad09-143">变量具有作用域，因此表达式生成器中的 **“变量”** 文件夹只列出处于作用域中并且可以使用的变量。</span><span class="sxs-lookup"><span data-stu-id="2ad09-143">Variables have scope, and the **Variables** folder in the expression builder lists only variables that are in scope and available to use.</span></span> <span data-ttu-id="2ad09-144">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="2ad09-144">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2ad09-145">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2ad09-145">Related Tasks</span></span>  
 [<span data-ttu-id="2ad09-146">在数据流组件中使用表达式</span><span class="sxs-lookup"><span data-stu-id="2ad09-146">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="2ad09-147">相关内容</span><span class="sxs-lookup"><span data-stu-id="2ad09-147">Related Content</span></span>  
 <span data-ttu-id="2ad09-148">social.technet.microsoft.com 上的技术文章 [SSIS 表达式示例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="2ad09-148">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad09-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ad09-149">See Also</span></span>  
 [<span data-ttu-id="2ad09-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="2ad09-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
