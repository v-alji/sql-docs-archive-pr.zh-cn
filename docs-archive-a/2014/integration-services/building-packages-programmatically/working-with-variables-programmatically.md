---
title: 以编程方式使用变量 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System namespace
- scope [Integration Services]
- variables [Integration Services], programmatically
- configuration files [Integration Services]
- Variables collection
- User namespace
- custom variables [Integration Services]
- variables [Integration Services], customizing
ms.assetid: c4b76a3d-94ca-4a8e-bb45-cb8bd0ea3ec1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c903ee6adb8989eaeb93efbe943eca93c73eae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692506"
---
# <a name="working-with-variables-programmatically"></a><span data-ttu-id="a1c73-102">以编程方式使用变量</span><span class="sxs-lookup"><span data-stu-id="a1c73-102">Working with Variables Programmatically</span></span>
  <span data-ttu-id="a1c73-103">变量提供一种在包、容器、任务和事件处理程序中动态设置值和控制进程的方式。</span><span class="sxs-lookup"><span data-stu-id="a1c73-103">Variables are a way to dynamically set values and control processes in packages, containers, tasks, and event handlers.</span></span> <span data-ttu-id="a1c73-104">优先约束还可使用变量来控制数据流流向不同任务的方向。</span><span class="sxs-lookup"><span data-stu-id="a1c73-104">Variables can also be used by precedence constraints to control the direction of the flow of data to different tasks.</span></span> <span data-ttu-id="a1c73-105">变量具有多种用途：</span><span class="sxs-lookup"><span data-stu-id="a1c73-105">Variables have a variety of uses:</span></span>

-   <span data-ttu-id="a1c73-106">在运行时更新包的属性。</span><span class="sxs-lookup"><span data-stu-id="a1c73-106">Update properties of a package at run time.</span></span>

-   <span data-ttu-id="a1c73-107">在运行时填充 Transact-SQL 语句的参数值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-107">Populate parameter values for Transact-SQL statements at run time.</span></span>

-   <span data-ttu-id="a1c73-108">控制 Foreach 循环流。</span><span class="sxs-lookup"><span data-stu-id="a1c73-108">Control the flow of a Foreach loop.</span></span> <span data-ttu-id="a1c73-109">有关详细信息，请参阅[将枚举添加到控制流](../control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-109">For more information, see [Add Enumeration to a Control Flow](../control-flow/control-flow.md).</span></span>

-   <span data-ttu-id="a1c73-110">通过在表达式中使用优先约束对其进行控制。</span><span class="sxs-lookup"><span data-stu-id="a1c73-110">Control a precedence constraint by its use in an expression.</span></span> <span data-ttu-id="a1c73-111">优先约束可在约束定义中包含变量。</span><span class="sxs-lookup"><span data-stu-id="a1c73-111">A precedence constraint can include variables in the constraint definition.</span></span> <span data-ttu-id="a1c73-112">有关详细信息，请参阅 [将表达式添加到优先约束](../control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-112">For more information, see [Add Expressions to Precedence Constraints](../control-flow/precedence-constraints.md).</span></span>

-   <span data-ttu-id="a1c73-113">控制 For 循环容器的条件重复。</span><span class="sxs-lookup"><span data-stu-id="a1c73-113">Control the conditional repeat of a For Loop container.</span></span> <span data-ttu-id="a1c73-114">有关详细信息，请参阅[将迭代添加到控制流](../add-iteration-to-a-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-114">For more information, see [Add Iteration to a Control Flow](../add-iteration-to-a-control-flow.md).</span></span>

-   <span data-ttu-id="a1c73-115">生成包含变量值的表达式。</span><span class="sxs-lookup"><span data-stu-id="a1c73-115">Build expressions that include variable values.</span></span>

-   <span data-ttu-id="a1c73-116">可以为所有容器类型创建自定义变量，这些容器类型包括：包、Foreach 循环  容器、For 循环  容器、Sequence  容器、TaskHost 和事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="a1c73-116">You can create custom variables for all container types: packages, **Foreach Loop** containers, **For Loop** containers, **Sequence** containers, TaskHosts, and event handlers.</span></span> <span data-ttu-id="a1c73-117">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-117">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>

## <a name="scope"></a><span data-ttu-id="a1c73-118">范围</span><span class="sxs-lookup"><span data-stu-id="a1c73-118">Scope</span></span>
 <span data-ttu-id="a1c73-119">每个容器都有自己的 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 集合。</span><span class="sxs-lookup"><span data-stu-id="a1c73-119">Each container has its own <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection.</span></span> <span data-ttu-id="a1c73-120">创建新变量时，新变量的作用域在其父容器的作用域内。</span><span class="sxs-lookup"><span data-stu-id="a1c73-120">When a new variable is created, it is within the scope of its parent container.</span></span> <span data-ttu-id="a1c73-121">由于包容器位于容器层次结构的顶部，所以包作用域内的变量所起作用类似于全局变量，并且这些变量对包中的所有容器都可见。</span><span class="sxs-lookup"><span data-stu-id="a1c73-121">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables, and are visible to all containers within the package.</span></span> <span data-ttu-id="a1c73-122">容器的变量集合还可由容器的子容器通过 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 集合进行访问，方法是使用集合中的变量名称或变量的索引。</span><span class="sxs-lookup"><span data-stu-id="a1c73-122">The collection of variables for the container can also be accessed by the children of the container through the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection, by using either the variable name or the variable's index in the collection.</span></span>

 <span data-ttu-id="a1c73-123">由于变量可见性的作用域是自上而下，所以在包级别声明的变量对包中的所有容器都可见。</span><span class="sxs-lookup"><span data-stu-id="a1c73-123">Because the visibility of a variable is scoped from the top down, variables declared at the package level are visible to all the containers in the package.</span></span> <span data-ttu-id="a1c73-124">因此，容器的 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 集合除了包含自己的变量，还包含所有属于其父容器的变量。</span><span class="sxs-lookup"><span data-stu-id="a1c73-124">Therefore, the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection on a container includes all the variables that belong to its parent in addition to its own variables</span></span>

 <span data-ttu-id="a1c73-125">相反，包含在任务中的变量在作用域和可见性方面都会受到限制，并且仅对该任务可见。</span><span class="sxs-lookup"><span data-stu-id="a1c73-125">Conversely, the variables that are contained in a task are limited in scope and visibility, and are only visible to the task.</span></span>

 <span data-ttu-id="a1c73-126">如果包运行其他包，则在调用包作用域内定义的变量将对被调用的包可用。</span><span class="sxs-lookup"><span data-stu-id="a1c73-126">If a package runs other packages, the variables defined in the scope of the calling package are available to the called package.</span></span> <span data-ttu-id="a1c73-127">唯一的例外是被调用的包中存在同名变量的情况。</span><span class="sxs-lookup"><span data-stu-id="a1c73-127">The only exception occurs when a same-named variable exists in the called package.</span></span> <span data-ttu-id="a1c73-128">发生此类冲突时，被调用的包中的变量值将会重写调用包的值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-128">When this collision occurs, the variable value in the called package overrides the value from the calling package.</span></span> <span data-ttu-id="a1c73-129">在被调用的包的作用域中定义的变量永远不对调用包可用。</span><span class="sxs-lookup"><span data-stu-id="a1c73-129">Variables defined in the scope of the called package are never available back to the calling package.</span></span>

 <span data-ttu-id="a1c73-130">下面的代码示例以编程方式创建一个对包作用域的变量 `myCustomVar`，然后遍历所有对包可见的变量，并打印这些变量的名称、数据类型和值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-130">The following code example programmatically creates a variable, `myCustomVar`, at the package scope, and then iterates through all the variables visible to the package, printing their name, data type, and value.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Application app = new Application();
      // Load a sample package that contains a variable that sets the file name.
      Package pkg = app.LoadPackage(
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +
        @"\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx",
        null);
      Variables pkgVars = pkg.Variables;
      Variable myVar = pkg.Variables.Add("myCustomVar", false, "User", "3");
      foreach (Variable pkgVar in pkgVars)
      {
        Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name,
          pkgVar.DataType, pkgVar.Value.ToString());
      }
      Console.Read();
    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim app As Application = New Application()
    ' Load a sample package that contains a variable that sets the file name.
    Dim pkg As Package = app.LoadPackage( _
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _
      "\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx", _
      Nothing)
    Dim pkgVars As Variables = pkg.Variables
    Dim myVar As Variable = pkg.Variables.Add("myCustomVar", False, "User", "3")
    Dim pkgVar As Variable
    For Each pkgVar In pkgVars
      Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name, _
        pkgVar.DataType, pkgVar.Value.ToString())
    Next
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="a1c73-131">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="a1c73-131">**Sample Output:**</span></span>

 `Variable: CancelEvent, Int32, 0`

 `Variable: CreationDate, DateTime, 4/18/2003 11:57:00 AM`

 `Variable: CreatorComputerName, String,`

 `Variable: CreatorName, String,`

 `Variable: ExecutionInstanceGUID, String, {237AB5A4-7E59-4FC9-8D61-E8F20363DF25}`

 `Variable: FileName, String, Junk`

 `Variable: InteractiveMode, Boolean, False`

 `Variable: LocaleID, Int32, 1033`

 `Variable: MachineName, String, MYCOMPUTERNAME`

 `Variable: myCustomVar, String, 3`

 `Variable: OfflineMode, Boolean, False`

 `Variable: PackageID, String, {F0D2E396-A6A5-42AE-9467-04CE946A810C}`

 `Variable: PackageName, String, DTSPackage1`

 `Variable: StartTime, DateTime, 1/28/2005 7:55:39 AM`

 `Variable: UserName, String, <domain>\<userid>`

 `Variable: VersionBuild, Int32, 198`

 `Variable: VersionComments, String,`

 `Variable: VersionGUID, String, {90E105B4-B4AF-4263-9CBD-C2050C2D6148}`

 `Variable: VersionMajor, Int32, 1`

 `Variable: VersionMinor, Int32, 0`

 <span data-ttu-id="a1c73-132">请注意，所有作用域在系统  命名空间内的变量都可用于该包。</span><span class="sxs-lookup"><span data-stu-id="a1c73-132">Notice that all the variables scoped in the **System** namespace are available to the package.</span></span> <span data-ttu-id="a1c73-133">有关详细信息，请参阅 [System Variables](../system-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-133">For more information, see [System Variables](../system-variables.md).</span></span>

## <a name="namespaces"></a><span data-ttu-id="a1c73-134">命名空间</span><span class="sxs-lookup"><span data-stu-id="a1c73-134">Namespaces</span></span>
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a1c73-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]（[!INCLUDE[ssIS](../../includes/ssis-md.md)]）提供了两个供变量驻留的默认命名空间；用户\*\*\*\* 和系统\*\*\*\* 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a1c73-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) provides two default namespaces where variables reside; **User** and **System** namespaces.</span></span> <span data-ttu-id="a1c73-136">默认情况下，开发人员所创建的任何自定义变量都会添加到用户  命名空间中。</span><span class="sxs-lookup"><span data-stu-id="a1c73-136">By default, any custom variable created by the developer is added to the **User** namespace.</span></span> <span data-ttu-id="a1c73-137">系统变量驻留在系统  命名空间中。</span><span class="sxs-lookup"><span data-stu-id="a1c73-137">System variables reside in the **System** namespace.</span></span> <span data-ttu-id="a1c73-138">可以创建除用户  命名空间以外的其他命名空间以保存自定义变量，可以更改用户  命名空间的名称，但是不能在系统  命名空间中添加变量或修改其中的变量，也不能向不同的命名空间分配系统变量。</span><span class="sxs-lookup"><span data-stu-id="a1c73-138">You can create additional namespaces other than the **User** namespace to hold custom variables, and you can change the name of the **User** namespace, but you cannot add or modify variables in the **System** namespace, or assign system variables to a different namespace.</span></span>

 <span data-ttu-id="a1c73-139">可用的系统变量互有差异，具体取决于容器类型。</span><span class="sxs-lookup"><span data-stu-id="a1c73-139">The system variables that are available differ depending on the container type.</span></span> <span data-ttu-id="a1c73-140">有关包、容器、任务和事件处理器可用的系统变量的列表，请参阅[系统变量](../system-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-140">For a list of the system variables available to packages, containers, tasks, and event handlers, see [System Variables](../system-variables.md).</span></span>

## <a name="value"></a><span data-ttu-id="a1c73-141">值</span><span class="sxs-lookup"><span data-stu-id="a1c73-141">Value</span></span>
 <span data-ttu-id="a1c73-142">自定义变量的值可以是文字或表达式：</span><span class="sxs-lookup"><span data-stu-id="a1c73-142">The value of a custom variable can be a literal or an expression:</span></span>

-   <span data-ttu-id="a1c73-143">如果希望变量包含文字值，请设置其 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-143">If you want the variable to contain a literal value, set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property.</span></span>

-   <span data-ttu-id="a1c73-144">如果希望变量包含表达式，以便将表达式的结果用作变量的值，请将变量的 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> 属性设置为 `true`，并在 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> 属性中提供一个表达式。</span><span class="sxs-lookup"><span data-stu-id="a1c73-144">If you want the variable to contain an expression, so that you can use the results of the expression as its value, set the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> property of the variable to `true`, and provide an expression in the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> property.</span></span> <span data-ttu-id="a1c73-145">在运行时计算表达式，并将表达式的结果用作变量的值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-145">At run time, the expression is evaluated, and the result of the expression is used as the value of the variable.</span></span> <span data-ttu-id="a1c73-146">例如，如果变量的表达式属性为 `"100 * 2""100 * 2"`，则变量的计算结果将为 200。</span><span class="sxs-lookup"><span data-stu-id="a1c73-146">For example, if the expression property of a variable is `"100 * 2""100 * 2"`, the variable evaluates to a value of 200.</span></span>

 <span data-ttu-id="a1c73-147">对于变量，您不能显式设置其 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-147">For a variable, you cannot explicitly set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A>.</span></span> <span data-ttu-id="a1c73-148"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> 值是从分配给变量的初始值推断得出的，之后将不可更改。</span><span class="sxs-lookup"><span data-stu-id="a1c73-148">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> value is inferred from the initial value assigned to the variable, and cannot be changed afterward.</span></span> <span data-ttu-id="a1c73-149">有关变量数据类型的详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-149">For more information about variable data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="a1c73-150">下面的代码示例创建一个新变量，将 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> 设置为 `true`，并向该变量的表达式属性分配表达式 `"100 * 2"`，然后输出该变量的值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-150">The following code example creates a new variable, sets <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> to `true`, assigns the expression `"100 * 2"` to the expression property of the variable, and then outputs the value of the variable.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package pkg = new Package();
      Variable v100 = pkg.Variables.Add("myVar", false, "", 1);
      v100.EvaluateAsExpression = true;
      v100.Expression = "100 * 2";
      Console.WriteLine("Expression for myVar: {0}", 
        v100.Properties["Expression"].GetValue(v100));
      Console.WriteLine("Value of myVar: {0}", v100.Value.ToString());
      Console.Read();
    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim pkg As Package = New Package
    Dim v100 As Variable = pkg.Variables.Add("myVar", False, "", 1)
    v100.EvaluateAsExpression = True
    v100.Expression = "100 * 2"
    Console.WriteLine("Expression for myVar: {0}", _
      v100.Properties("Expression").GetValue(v100))
    Console.WriteLine("Value of myVar: {0}", v100.Value.ToString)
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="a1c73-151">**示例输出：**</span><span class="sxs-lookup"><span data-stu-id="a1c73-151">**Sample Output:**</span></span>

 `Expression for myVar: 100 * 2`

 `Value of myVar: 200`

 <span data-ttu-id="a1c73-152">表达式必须是使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 表达式语法的有效表达式。</span><span class="sxs-lookup"><span data-stu-id="a1c73-152">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="a1c73-153">除了表达式语法提供的运算符和函数，变量表达式中还可以使用文字，但表达式不能引用其他变量或列。</span><span class="sxs-lookup"><span data-stu-id="a1c73-153">Literals are permitted in variable expressions, in addition to the operators and functions that the expression syntax provides, but expressions cannot reference other variables or columns.</span></span> <span data-ttu-id="a1c73-154">有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-154">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="a1c73-155">配置文件</span><span class="sxs-lookup"><span data-stu-id="a1c73-155">Configuration Files</span></span>
 <span data-ttu-id="a1c73-156">如果配置文件中包含自定义变量，则该变量可在运行时更新。</span><span class="sxs-lookup"><span data-stu-id="a1c73-156">If a configuration file includes a custom variable, the variable can be updated at run time.</span></span> <span data-ttu-id="a1c73-157">这意味着，当包运行时，配置文件中的新值会替换包中的原始变量值。</span><span class="sxs-lookup"><span data-stu-id="a1c73-157">What this means is that when the package runs, the value of the variable originally in the package is replaced with a new value from the configuration file.</span></span> <span data-ttu-id="a1c73-158">将包部署到需要不同变量值的多个服务器时，此替换技术将会很有用。</span><span class="sxs-lookup"><span data-stu-id="a1c73-158">This replacement technique is useful when a package is deployed to multiple servers that require different variable values.</span></span> <span data-ttu-id="a1c73-159">例如，变量可指定 Foreach 循环  容器重复其工作流的次数、列出引发错误时接收事件处理程序发送的电子邮件的收件人、或者更改包失败前可能发生的错误的数量。</span><span class="sxs-lookup"><span data-stu-id="a1c73-159">For example, a variable can specify the number of times a **Foreach Loop** container repeats its workflow, or list the recipients that an event handler sends e-mail to when an error is raised, or change the number of errors that can occur before the package fails.</span></span> <span data-ttu-id="a1c73-160">对于每种环境，这些变量都以编程方式在配置文件中动态提供。</span><span class="sxs-lookup"><span data-stu-id="a1c73-160">These variables are dynamically provided in configuration files for each environment.</span></span> <span data-ttu-id="a1c73-161">因此，配置文件中只允许读/写变量。</span><span class="sxs-lookup"><span data-stu-id="a1c73-161">Therefore, only variables that are read/write are allowed in configuration files.</span></span> <span data-ttu-id="a1c73-162">有关详细信息，请参阅 [创建包配置](../create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c73-162">For more information, see [Create Package Configurations](../create-package-configurations.md).</span></span>

<span data-ttu-id="a1c73-163">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a1c73-163">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a1c73-164">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="a1c73-164">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a1c73-165">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="a1c73-165">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a1c73-166">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="a1c73-166">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c73-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1c73-167">See Also</span></span>
 <span data-ttu-id="a1c73-168">[Integration Services &#40;SSIS&#41; 变量](../integration-services-ssis-variables.md)[在包中使用变量](../use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="a1c73-168">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) [Use Variables in Packages](../use-variables-in-packages.md)</span></span>


