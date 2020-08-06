---
title: Integration Services (SSIS) 变量 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 956211ec971d69dc2fdb430dcada82a097280808
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586853"
---
# <a name="integration-services-ssis-variables"></a><span data-ttu-id="6a42c-102">Integration Services (SSIS) 变量</span><span class="sxs-lookup"><span data-stu-id="6a42c-102">Integration Services (SSIS) Variables</span></span>
  <span data-ttu-id="6a42c-103">变量存储 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包及其容器、任务和事件处理程序在运行时可以使用的值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-103">Variables store values that a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its containers, tasks, and event handlers can use at run time.</span></span> <span data-ttu-id="6a42c-104">脚本任务和脚本组件中的脚本也可以使用变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-104">The scripts in the Script task and the Script component can also use variables.</span></span> <span data-ttu-id="6a42c-105">将任务和容器按顺序组织为工作流的优先约束在其约束定义包含表达式时可以使用变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-105">The precedence constraints that sequence tasks and containers into a workflow can use variables when their constraint definitions include expressions.</span></span>  
  
 <span data-ttu-id="6a42c-106">可以将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包中的变量用于下列目的：</span><span class="sxs-lookup"><span data-stu-id="6a42c-106">You can use variables in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="6a42c-107">在运行时更新包元素的属性。</span><span class="sxs-lookup"><span data-stu-id="6a42c-107">Updating properties of package elements at run time.</span></span> <span data-ttu-id="6a42c-108">例如，可以动态设置 Foreach 循环容器所允许的并发可执行文件数。</span><span class="sxs-lookup"><span data-stu-id="6a42c-108">For example, you can dynamically set the number of concurrent executables that a Foreach Loop container allows.</span></span>  
  
-   <span data-ttu-id="6a42c-109">包含内存中的查找表。</span><span class="sxs-lookup"><span data-stu-id="6a42c-109">Including an in-memory lookup table.</span></span> <span data-ttu-id="6a42c-110">例如，包可以运行加载带数据值的变量的执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="6a42c-110">For example, a package can run an Execute SQL task that loads a variable with data values.</span></span>  
  
-   <span data-ttu-id="6a42c-111">加载带数据值的变量，然后使用这些变量指定 WHERE 子句中的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="6a42c-111">Loading variables with data values and then using them to specify a search condition in a WHERE clause.</span></span> <span data-ttu-id="6a42c-112">例如，脚本任务中的脚本可以更新执行 SQL 任务中的 Transact-SQL 语句所使用的变量的值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-112">For example, the script in a Script task can update the value of a variable that is used by a Transact-SQL statement in an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="6a42c-113">加载带整数的变量，然后使用该值控制包控制流中的循环。</span><span class="sxs-lookup"><span data-stu-id="6a42c-113">Loading a variable with an integer and then using the value to control looping within a package control flow.</span></span> <span data-ttu-id="6a42c-114">例如，可以在 For 循环容器的计算表达式中使用变量来控制迭代。</span><span class="sxs-lookup"><span data-stu-id="6a42c-114">For example, you can use a variable in the evaluation expression of a For Loop container to control iteration.</span></span>  
  
-   <span data-ttu-id="6a42c-115">在运行时填充 Transact-SQL 语句的参数值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-115">Populating parameter values for Transact-SQL statements at run time.</span></span> <span data-ttu-id="6a42c-116">例如，包可以运行执行 SQL 任务，然后使用变量动态设置 Transact-SQL 语句中的参数。</span><span class="sxs-lookup"><span data-stu-id="6a42c-116">For example, a package can run an Execute SQL task and then use variables to dynamically set the parameters in a Transact-SQL statement.</span></span>  
  
-   <span data-ttu-id="6a42c-117">生成包含变量值的表达式。</span><span class="sxs-lookup"><span data-stu-id="6a42c-117">Building expressions that include variable values.</span></span> <span data-ttu-id="6a42c-118">例如，派生列转换可以用变量值乘以列值所得结果来填充列。</span><span class="sxs-lookup"><span data-stu-id="6a42c-118">For example, the Derived Column transformation can populate a column with the result obtained by multiplying a variable value by a column value.</span></span>  
  
## <a name="system-and-user-defined-variables"></a><span data-ttu-id="6a42c-119">系统变量和用户定义变量</span><span class="sxs-lookup"><span data-stu-id="6a42c-119">System and User-Defined Variables</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6a42c-120">支持两种类型的变量：用户定义变量和系统变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-120">supports two types of variables: user-defined variables and system variables.</span></span> <span data-ttu-id="6a42c-121">用户定义变量由包开发人员定义，系统变量由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]定义。</span><span class="sxs-lookup"><span data-stu-id="6a42c-121">User-defined variables are defined by package developers, and system variables are defined by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="6a42c-122">可以创建包所需数量的用户定义变量，但不能另外创建系统变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-122">You can create as many user-defined variables as a package requires, but you cannot create additional system variables.</span></span>  
  
 <span data-ttu-id="6a42c-123">在执行 SQL 任务用来在 SQL 语句中将变量映射到参数的参数绑定中，可以使用所有变量（系统和用户定义）。</span><span class="sxs-lookup"><span data-stu-id="6a42c-123">All variables-system and user-defined-can be used in the parameter bindings that the Execute SQL task uses to map variables to parameters in SQL statements.</span></span> <span data-ttu-id="6a42c-124">有关详细信息，请参阅 [执行 SQL 任务](control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的参数和返回代码](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-124">For more information, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a42c-125">用户定义变量和系统变量的名称是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="6a42c-125">The names of user-defined and system variables are case sensitive.</span></span>  
  
 <span data-ttu-id="6a42c-126">可以为所有 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 容器类型创建用户定义变量，这些容器类型包括包、Foreach 循环容器、For 循环容器、序列容器、任务以及事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6a42c-126">You can create user-defined variables for all [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types: packages, Foreach Loop containers, For Loop containers, Sequence containers, tasks, and event handlers.</span></span> <span data-ttu-id="6a42c-127">用户定义变量是容器中 Variables 集合的成员。</span><span class="sxs-lookup"><span data-stu-id="6a42c-127">User-defined variables are members of the Variables collection of the container.</span></span>  
  
 <span data-ttu-id="6a42c-128">使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器创建包时， **设计器** “包资源管理器” **选项卡上的** “变量” [!INCLUDE[ssIS](../includes/ssis-md.md)] 文件夹中可以看到 Variables 集合的成员。</span><span class="sxs-lookup"><span data-stu-id="6a42c-128">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the Variables collections in the **Variables** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="6a42c-129">这些文件夹列出了用户定义变量和系统变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-129">The folders list user-defined variables and system variables.</span></span>  
  
 <span data-ttu-id="6a42c-130">可以使用下列方式配置用户定义变量：</span><span class="sxs-lookup"><span data-stu-id="6a42c-130">You can configure user-defined variables in the following ways:</span></span>  
  
-   <span data-ttu-id="6a42c-131">提供变量的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="6a42c-131">Provide a name and description for the variable.</span></span>  
  
-   <span data-ttu-id="6a42c-132">指定变量的命名空间。</span><span class="sxs-lookup"><span data-stu-id="6a42c-132">Specify a namespace for the variable.</span></span>  
  
-   <span data-ttu-id="6a42c-133">指示变量是否在其值更改时引发事件。</span><span class="sxs-lookup"><span data-stu-id="6a42c-133">Indicate whether the variable raises an event when its value changes.</span></span>  
  
-   <span data-ttu-id="6a42c-134">指示变量是只读还是读/写。</span><span class="sxs-lookup"><span data-stu-id="6a42c-134">Indicate whether the variable is read-only or read/write.</span></span>  
  
-   <span data-ttu-id="6a42c-135">使用表达式的计算结果设置变量值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-135">Use the evaluation result of an expression to set the variable value.</span></span>  
  
-   <span data-ttu-id="6a42c-136">在包或包对象（如任务）的范围内创建变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-136">Create the variable in the scope of the package or a package object such as a task.</span></span>  
  
-   <span data-ttu-id="6a42c-137">指定变量的值和数据类型。</span><span class="sxs-lookup"><span data-stu-id="6a42c-137">Specify the value and data type of the variable.</span></span>  
  
 <span data-ttu-id="6a42c-138">对系统变量唯一可配置的选项是指定变量在更改值时是否引发事件。</span><span class="sxs-lookup"><span data-stu-id="6a42c-138">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="6a42c-139">不同的容器类型有一组不同的系统变量可用。</span><span class="sxs-lookup"><span data-stu-id="6a42c-139">A different set of system variables is available for different container types.</span></span> <span data-ttu-id="6a42c-140">有关包及其元素所使用的系统变量的详细信息，请参阅 [System Variables](system-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-140">For more information about the system variables used by packages and their elements, see [System Variables](system-variables.md).</span></span>  
  
 <span data-ttu-id="6a42c-141">有关变量的实际使用情况的详细信息，请参阅 [在包中使用变量](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-141">For more information about real-life use scenarios for variables, see [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
## <a name="variable-properties"></a><span data-ttu-id="6a42c-142">变量属性</span><span class="sxs-lookup"><span data-stu-id="6a42c-142">Variable Properties</span></span>  
 <span data-ttu-id="6a42c-143">你可通过在“变量”窗口或“属性”窗口中设置以下属性来配置用户定义变量   。</span><span class="sxs-lookup"><span data-stu-id="6a42c-143">You can configure user-defined variables by setting the following properties in either the **Variables** window or the **Properties** window.</span></span> <span data-ttu-id="6a42c-144">某些属性仅在“属性”窗口中提供。</span><span class="sxs-lookup"><span data-stu-id="6a42c-144">Certain properties are available only in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a42c-145">对系统变量唯一可配置的选项是指定变量在更改值时是否引发事件。</span><span class="sxs-lookup"><span data-stu-id="6a42c-145">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="6a42c-146">说明</span><span class="sxs-lookup"><span data-stu-id="6a42c-146">Description</span></span>  
 <span data-ttu-id="6a42c-147">指定对变量的描述。</span><span class="sxs-lookup"><span data-stu-id="6a42c-147">Specifies the description of the variable.</span></span>  
  
 <span data-ttu-id="6a42c-148">EvaluateAsExpression</span><span class="sxs-lookup"><span data-stu-id="6a42c-148">EvaluateAsExpression</span></span>  
 <span data-ttu-id="6a42c-149">当属性设置为时 `True` ，提供的表达式用于设置变量值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-149">When the property is set to `True`, the expression provided is used to set the variable value.</span></span>  
  
 <span data-ttu-id="6a42c-150">Expression</span><span class="sxs-lookup"><span data-stu-id="6a42c-150">Expression</span></span>  
 <span data-ttu-id="6a42c-151">指定分配给该变量的表达式。</span><span class="sxs-lookup"><span data-stu-id="6a42c-151">Specifies the expression that is assigned to the variable.</span></span>  
  
 <span data-ttu-id="6a42c-152">名称</span><span class="sxs-lookup"><span data-stu-id="6a42c-152">Name</span></span>  
 <span data-ttu-id="6a42c-153">指定变量名称。</span><span class="sxs-lookup"><span data-stu-id="6a42c-153">Specifies the variable name.</span></span>  
  
 <span data-ttu-id="6a42c-154">命名空间</span><span class="sxs-lookup"><span data-stu-id="6a42c-154">Namespace</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="6a42c-155">提供了两个命名空间：User 和 System   。</span><span class="sxs-lookup"><span data-stu-id="6a42c-155">provides two namespaces, **User** and **System**.</span></span> <span data-ttu-id="6a42c-156">默认情况下，自定义变量位于 **User** 命名空间中，系统变量位于 **System** 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="6a42c-156">By default, custom variables are in the **User** namespace, and system variables are in the **System** namespace.</span></span> <span data-ttu-id="6a42c-157">你可以为用户定义变量创建其他命名空间，并可以更改 **User** 命名空间的名称，但不能更改 **System** 命名空间的名称，也不能向 **System** 命名空间添加变量或将系统变量分配给其他命名空间。</span><span class="sxs-lookup"><span data-stu-id="6a42c-157">You can create additional namespaces for user-defined variables and change the name of the **User** namespace, but you cannot change the name of the **System** namespace, add variables to the **System** namespace, or assign system variables to a different namespace.</span></span>  
  
 <span data-ttu-id="6a42c-158">RaiseChangedEvent</span><span class="sxs-lookup"><span data-stu-id="6a42c-158">RaiseChangedEvent</span></span>  
 <span data-ttu-id="6a42c-159">将此属性设置为 `True` 时，变量值的改变将会引发 `OnVariableValueChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="6a42c-159">When the property is set to `True`, the `OnVariableValueChanged` event is raised when the variable changes value.</span></span>  
  
 <span data-ttu-id="6a42c-160">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6a42c-160">ReadOnly</span></span>  
 <span data-ttu-id="6a42c-161">将此属性设置为 `False` 时，该变量为读\写变量。</span><span class="sxs-lookup"><span data-stu-id="6a42c-161">When the property is set to `False`, the variable is read\write.</span></span>  
  
 <span data-ttu-id="6a42c-162">范围</span><span class="sxs-lookup"><span data-stu-id="6a42c-162">Scope</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="6a42c-163">可通过单击“变量”窗口中的“移动变量”来更改此属性设置   。</span><span class="sxs-lookup"><span data-stu-id="6a42c-163">You can change this property setting only by clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="6a42c-164">变量在包的作用域内或者包中的容器、任务或事件处理程序的作用域内创建。</span><span class="sxs-lookup"><span data-stu-id="6a42c-164">A variable is created within the scope of a package or within the scope of a container, task, or event handler in the package.</span></span> <span data-ttu-id="6a42c-165">因为包容器位于容器层次结构的顶部，所以包作用域内的变量所起作用类似于全局变量，而且这些变量可由包中所有容器使用。</span><span class="sxs-lookup"><span data-stu-id="6a42c-165">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables and can be used by all containers in the package.</span></span> <span data-ttu-id="6a42c-166">同样，在 For 循环容器等容器的范围内定义的变量可由 For 循环容器中所有任务或容器使用。</span><span class="sxs-lookup"><span data-stu-id="6a42c-166">Similarly, variables defined within the scope of a container such as a For Loop container can be used by all tasks or containers within the For Loop container.</span></span>  
  
 <span data-ttu-id="6a42c-167">如果包使用执行包任务运行其他包，则可以使用父包变量配置类型，使在调用的包或执行包任务范围内定义的变量可供被调用的包使用。</span><span class="sxs-lookup"><span data-stu-id="6a42c-167">If a package runs other packages by using the Execute Package task, the variables defined in the scope of the calling package or the Execute Package task can be made available to the called package by using the Parent Package Variable configuration type.</span></span> <span data-ttu-id="6a42c-168">有关详细信息，请参阅 [Package Configurations](../../2014/integration-services/package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-168">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
 <span data-ttu-id="6a42c-169">IncludeInDebugDump</span><span class="sxs-lookup"><span data-stu-id="6a42c-169">IncludeInDebugDump</span></span>  
 <span data-ttu-id="6a42c-170">指示调试转储文件中是否包括变量值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-170">Indicate whether the variable value is included in the debug dump files.</span></span>  
  
 <span data-ttu-id="6a42c-171">对于用户定义的变量和系统变量， **InclueInDebugDump**选项的默认值为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="6a42c-171">For user-defined variables and system variables, the default value for the **InclueInDebugDump** option is `true`.</span></span>  
  
 <span data-ttu-id="6a42c-172">但是，对于用户定义的变量， **IncludeInDebugDump** `false` 当满足以下条件时，系统会将 IncludeInDebugDump 选项重置为：</span><span class="sxs-lookup"><span data-stu-id="6a42c-172">However, for user-defined variables, the system resets the **IncludeInDebugDump** option to `false` when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="6a42c-173">如果**EvaluateAsExpression**变量属性设置为 `true` ，则系统会将**IncludeInDebugDump**选项重置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6a42c-173">If the **EvaluateAsExpression** variable property is set to `true`, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
     <span data-ttu-id="6a42c-174">若要在调试转储文件中包括表达式文本作为变量值，请将**IncludeInDebugDump**选项设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="6a42c-174">To include the text of the expression as the variable value in the debug dump files, set the **IncludeInDebugDump** option to `true`.</span></span>  
  
-   <span data-ttu-id="6a42c-175">如果将变量数据类型更改为字符串，系统会将**IncludeInDebugDump**选项重置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6a42c-175">If the variable data type is changed to a string, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
 <span data-ttu-id="6a42c-176">当系统将**IncludeInDebugDump**选项重置为时 `false` ，这可能会覆盖用户选择的值。</span><span class="sxs-lookup"><span data-stu-id="6a42c-176">When the system resets the **IncludeInDebugDump** option to `false`, this might override the value selected by the user.</span></span>  
  
 <span data-ttu-id="6a42c-177">值</span><span class="sxs-lookup"><span data-stu-id="6a42c-177">Value</span></span>  
 <span data-ttu-id="6a42c-178">用户定义变量的值可以是文字或表达式。</span><span class="sxs-lookup"><span data-stu-id="6a42c-178">The value of a user-defined variable can be a literal or an expression.</span></span> <span data-ttu-id="6a42c-179">变量包含设置变量值和值的数据类型的选项。</span><span class="sxs-lookup"><span data-stu-id="6a42c-179">A variable includes options for setting the variable value and the data type of the value.</span></span> <span data-ttu-id="6a42c-180">这两种属性必须兼容：例如，字符串值不能与整数数据类型一起使用。</span><span class="sxs-lookup"><span data-stu-id="6a42c-180">The two properties must be compatible: for example, the use of a string value together with an integer data type is not valid.</span></span>  
  
 <span data-ttu-id="6a42c-181">如果将变量配置为作为表达式进行计算，则必须提供表达式。</span><span class="sxs-lookup"><span data-stu-id="6a42c-181">If the variable is configured to evaluate as an expression, you must provide an expression.</span></span> <span data-ttu-id="6a42c-182">在运行时计算表达式，而该变量将设置为计算结果。</span><span class="sxs-lookup"><span data-stu-id="6a42c-182">At run time, the expression is evaluated, and the variable is set to the evaluation result.</span></span> <span data-ttu-id="6a42c-183">例如，如果变量使用表达式 `DATEPART("month", GETDATE())` ，则变量的值与当前日期月份部分的数字相同。</span><span class="sxs-lookup"><span data-stu-id="6a42c-183">For example, if a variable uses the expression `DATEPART("month", GETDATE())` the value of the variable is the number equivalent of the month for the current date.</span></span> <span data-ttu-id="6a42c-184">表达式必须是使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 表达式语法的有效表达式。</span><span class="sxs-lookup"><span data-stu-id="6a42c-184">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar syntax.</span></span> <span data-ttu-id="6a42c-185">表达式和变量一起使用时，表达式可以使用文字以及表达式语法所提供的运算符和函数，但表达式不能引用包中数据流的列。</span><span class="sxs-lookup"><span data-stu-id="6a42c-185">When an expression is used with variables, the expression can use literals and the operators and functions that the expression grammar provides, but the expression cannot reference the columns from a data flow in the package.</span></span> <span data-ttu-id="6a42c-186">表达式的最大长度为 4000 个字符。</span><span class="sxs-lookup"><span data-stu-id="6a42c-186">The maximum length of an expression is 4000 characters.</span></span> <span data-ttu-id="6a42c-187">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-187">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="6a42c-188">ValueType</span><span class="sxs-lookup"><span data-stu-id="6a42c-188">ValueType</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="6a42c-189"> 此属性值出现在 **“变量”** 窗口中的 **“数据类型”** 列中。</span><span class="sxs-lookup"><span data-stu-id="6a42c-189">The property value appears in the **Data type** column in the **Variables** window.</span></span>  
  
 <span data-ttu-id="6a42c-190">指定变量值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6a42c-190">Specifies the data type of the variable value.</span></span>  
  
## <a name="configuring-variables"></a><span data-ttu-id="6a42c-191">配置变量</span><span class="sxs-lookup"><span data-stu-id="6a42c-191">Configuring Variables</span></span>  
 <span data-ttu-id="6a42c-192">可以通过 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="6a42c-192">You can set properties through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6a42c-193">有关可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [“变量”窗口](../../2014/integration-services/variables-window.md)。</span><span class="sxs-lookup"><span data-stu-id="6a42c-193">For more information about the properties that you can set in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, see [Variables Window](../../2014/integration-services/variables-window.md).</span></span>  
  
 <span data-ttu-id="6a42c-194">若要了解变量属性的详细信息，以及关于以编程方式设置这些属性的详细信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.Variable>。</span><span class="sxs-lookup"><span data-stu-id="6a42c-194">To learn more about variable properties, and for more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6a42c-195">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6a42c-195">Related Tasks</span></span>  
 [<span data-ttu-id="6a42c-196">添加、删除、更改包中用户定义变量的作用域</span><span class="sxs-lookup"><span data-stu-id="6a42c-196">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [<span data-ttu-id="6a42c-197">设置用户定义变量的属性</span><span class="sxs-lookup"><span data-stu-id="6a42c-197">Set the Properties of a User-Defined Variable</span></span>](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [<span data-ttu-id="6a42c-198">在子包中使用变量和参数的值</span><span class="sxs-lookup"><span data-stu-id="6a42c-198">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [<span data-ttu-id="6a42c-199">将查询参数映射到数据流组件中的变量</span><span class="sxs-lookup"><span data-stu-id="6a42c-199">Map Query Parameters to Variables in a Data Flow Component</span></span>](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
