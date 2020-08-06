---
title: 编写自定义任务代码 | Microsoft Docs
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
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c369f4a7e8352be7ddde9e2e3938b47b0bcc1349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587923"
---
# <a name="coding-a-custom-task"></a><span data-ttu-id="3023d-102">编写自定义任务代码</span><span class="sxs-lookup"><span data-stu-id="3023d-102">Coding a Custom Task</span></span>
  <span data-ttu-id="3023d-103">创建继承自 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基类的类并将 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性应用于该类后，必须重写基类的属性和方法的实现才能提供自定义功能。</span><span class="sxs-lookup"><span data-stu-id="3023d-103">After you have created a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>

## <a name="configuring-the-task"></a><span data-ttu-id="3023d-104">配置任务</span><span class="sxs-lookup"><span data-stu-id="3023d-104">Configuring the Task</span></span>

### <a name="validating-the-task"></a><span data-ttu-id="3023d-105">验证任务</span><span class="sxs-lookup"><span data-stu-id="3023d-105">Validating the Task</span></span>
 <span data-ttu-id="3023d-106">设计 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包时，可以使用验证来检查每个任务的设置，以便及时发现不正确或不恰当的设置，而不是只在运行时才发现所有错误。</span><span class="sxs-lookup"><span data-stu-id="3023d-106">When you are designing an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package, you can use validation to verify settings on each task, so that you can catch incorrect or inappropriate settings as soon as they are set, instead of finding all errors at run-time only.</span></span> <span data-ttu-id="3023d-107">验证的目的是确定任务是否包含将阻止任务成功运行的无效设置或连接。</span><span class="sxs-lookup"><span data-stu-id="3023d-107">The purpose of validation is to determine whether the task contains invalid settings or connections that will prevent it from running successfully.</span></span> <span data-ttu-id="3023d-108">这可确保包所包含的任务首次运行能够更为顺利。</span><span class="sxs-lookup"><span data-stu-id="3023d-108">This makes sure that the package contains tasks that have a good chance of running on their first run.</span></span>

 <span data-ttu-id="3023d-109">在自定义代码中使用 `Validate` 方法可实现验证。</span><span class="sxs-lookup"><span data-stu-id="3023d-109">You can implement validation by using the `Validate` method in custom code.</span></span> <span data-ttu-id="3023d-110">运行时引擎通过对任务调用 `Validate` 方法来验证任务。</span><span class="sxs-lookup"><span data-stu-id="3023d-110">The run-time engine validates a task by calling the `Validate` method on the task.</span></span> <span data-ttu-id="3023d-111">任务开发人员应负责定义任务验证成功或失败的标准并通知运行时引擎此评估的结果。</span><span class="sxs-lookup"><span data-stu-id="3023d-111">It is the responsibility of the task developer to define the criteria that give you a successful or failed task validation, and to notify the run-time engine of the result of this evaluation.</span></span>

#### <a name="task-abstract-base-class"></a><span data-ttu-id="3023d-112">任务抽象基类</span><span class="sxs-lookup"><span data-stu-id="3023d-112">Task Abstract Base Class</span></span>
 <span data-ttu-id="3023d-113">[Microsoft SqlServer](/dotnet/api/microsoft.sqlserver.dts.runtime.task) abstract 基类提供了 `Validate` 每个任务重写以定义其验证条件的方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-113">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) abstract base class provides the `Validate` method that each task overrides to define its validation criteria.</span></span> <span data-ttu-id="3023d-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器将在包设计过程中多次自动调用 `Validate` 方法，并在警告或错误发生时向用户提供可视化提示，以帮助识别任务的配置问题。</span><span class="sxs-lookup"><span data-stu-id="3023d-114">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically calls the `Validate` method multiple times during package design, and provides visual cues to the user when warnings or errors occur to help identify problems with the configuration of the task.</span></span> <span data-ttu-id="3023d-115">任务返回 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 枚举的值并引发警告和错误事件，从而提供验证结果。</span><span class="sxs-lookup"><span data-stu-id="3023d-115">Tasks provide validation results by returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and by raising warning and error events.</span></span> <span data-ttu-id="3023d-116">这些事件包含将在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中向用户显示的信息。</span><span class="sxs-lookup"><span data-stu-id="3023d-116">These events contain information that is displayed to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="3023d-117">下面是一些验证示例：</span><span class="sxs-lookup"><span data-stu-id="3023d-117">Some examples for validation follow:</span></span>

-   <span data-ttu-id="3023d-118">连接管理器验证特定文件名。</span><span class="sxs-lookup"><span data-stu-id="3023d-118">A connection manager validates the specific file name.</span></span>

-   <span data-ttu-id="3023d-119">连接管理器验证输入类型是否为预期类型，如 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3023d-119">A connection manager validates that the type of input is the expected type, such as an XML file.</span></span>

-   <span data-ttu-id="3023d-120">要求数据库输入的任务确定自己收不到来自非数据库连接的数据。</span><span class="sxs-lookup"><span data-stu-id="3023d-120">A task that expects database input verifies that it cannot receive data from a non-database connection.</span></span>

-   <span data-ttu-id="3023d-121">任务确保自己的所有属性都不会相互冲突。</span><span class="sxs-lookup"><span data-stu-id="3023d-121">A task guarantees that none of its properties contradicts other properties set on the same task.</span></span>

-   <span data-ttu-id="3023d-122">任务确保在执行时使用的所有必需资源都可用。</span><span class="sxs-lookup"><span data-stu-id="3023d-122">A task guarantees that all required resources used by the task at execution time are available.</span></span>

 <span data-ttu-id="3023d-123">在确定验证对象时，有时需要考虑性能因素。</span><span class="sxs-lookup"><span data-stu-id="3023d-123">Performance is something to consider in determining what is validated and what is not.</span></span> <span data-ttu-id="3023d-124">例如，任务的输入可能是一个低带宽或通信量过大的网络连接。</span><span class="sxs-lookup"><span data-stu-id="3023d-124">For example, the input to a task might be a connection over a network that has low bandwidth or heavy traffic.</span></span> <span data-ttu-id="3023d-125">若要验证该资源是否可用，可能需要几秒钟的处理时间。</span><span class="sxs-lookup"><span data-stu-id="3023d-125">The validation may take several seconds to process if you decide to validate that the resource is available.</span></span> <span data-ttu-id="3023d-126">别的验证可能需要往返于需要量很大的服务器，低验证例程的速度可能就会降低。</span><span class="sxs-lookup"><span data-stu-id="3023d-126">Another validation may cause a round-trip to a server that is in high demand, and the validation routine might be slow.</span></span> <span data-ttu-id="3023d-127">虽然许多属性和设置都可以进行验证，但并不是所有属性和设置都应该进行验证。</span><span class="sxs-lookup"><span data-stu-id="3023d-127">Although there are many properties and settings that can be validated, not everything should be validated.</span></span>

-   <span data-ttu-id="3023d-128">在任务运行前，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 还会调用 `Validate` 方法中的代码；如果验证失败，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 将取消执行。</span><span class="sxs-lookup"><span data-stu-id="3023d-128">The code in the `Validate` method is also called by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> before the task is run, and the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> cancels execution if validation fails.</span></span>

#### <a name="user-interface-considerations-during-validation"></a><span data-ttu-id="3023d-129">验证过程中用户界面的注意事项</span><span class="sxs-lookup"><span data-stu-id="3023d-129">User Interface Considerations during Validation</span></span>
 <span data-ttu-id="3023d-130">[Microsoft SqlServer. Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task)包含一个 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 作为方法参数的接口 `Validate` 。</span><span class="sxs-lookup"><span data-stu-id="3023d-130">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) includes an <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface as a parameter to the `Validate` method.</span></span> <span data-ttu-id="3023d-131"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 接口包含一些方法，任务可调用这些方法以向运行时引擎引发事件。</span><span class="sxs-lookup"><span data-stu-id="3023d-131">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the methods that are called by the task in order to raise events to the run-time engine.</span></span> <span data-ttu-id="3023d-132">在验证期间出现警告或错误情况时会调用 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-132">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods are called when a warning or error condition occurs during validation.</span></span> <span data-ttu-id="3023d-133">这两个警告方法需要相同的参数，包括错误代码、源组件、说明、帮助文件以及帮助上下文信息。</span><span class="sxs-lookup"><span data-stu-id="3023d-133">Both warning methods require the same parameters, which include an error code, source component, description, Help file, and Help context information.</span></span> <span data-ttu-id="3023d-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器使用这些信息在设计图面上显示可视化提示。</span><span class="sxs-lookup"><span data-stu-id="3023d-134">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses this information to display visual cues on the design surface.</span></span> <span data-ttu-id="3023d-135">设计器提供的可视化提示包含感叹号图标，该图标显示在设计图面上的任务旁。</span><span class="sxs-lookup"><span data-stu-id="3023d-135">The visual cues that are provided by the designer include an exclamation icon that appears next to the task on the designer surface.</span></span> <span data-ttu-id="3023d-136">此可视化提示通知用户：任务需要其他配置才能继续执行。</span><span class="sxs-lookup"><span data-stu-id="3023d-136">This visual cue signals to the user that the task requires additional configuration before execution can continue.</span></span>

 <span data-ttu-id="3023d-137">感叹号图标还显示一个包含错误消息的工具提示。</span><span class="sxs-lookup"><span data-stu-id="3023d-137">The exclamation icon also displays a ToolTip that contains an error message.</span></span> <span data-ttu-id="3023d-138">错误消息由任务在事件的说明参数中提供。</span><span class="sxs-lookup"><span data-stu-id="3023d-138">The error message is provided by the task in the description parameter of the event.</span></span> <span data-ttu-id="3023d-139">错误消息还显示在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的“任务列表”窗格中，该窗格可供用户集中查看所有验证错误。</span><span class="sxs-lookup"><span data-stu-id="3023d-139">Error messages are also displayed in the **Task List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], providing the user with a central location for viewing all validation errors.</span></span>

#### <a name="validation-example"></a><span data-ttu-id="3023d-140">验证示例</span><span class="sxs-lookup"><span data-stu-id="3023d-140">Validation Example</span></span>
 <span data-ttu-id="3023d-141">下面的代码示例演示一个具有 `UserName` 属性的任务。</span><span class="sxs-lookup"><span data-stu-id="3023d-141">The following code example shows a task with a `UserName` property.</span></span> <span data-ttu-id="3023d-142">此属性已被指定为验证成功所必需的。</span><span class="sxs-lookup"><span data-stu-id="3023d-142">This property has been specified as required for validation to succeed.</span></span> <span data-ttu-id="3023d-143">如果未设置此属性，任务将会发布错误，并从 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> 枚举返回 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>。</span><span class="sxs-lookup"><span data-stu-id="3023d-143">If the property is not set, the task posts an error, and returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span> <span data-ttu-id="3023d-144">`Validate` 方法包装在 try/catch 块中，如果出现异常，验证将失败。</span><span class="sxs-lookup"><span data-stu-id="3023d-144">The `Validate` method is wrapped in a try/catch block, and fails validation if an exception occurs.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string userName = "";

  public override DTSExecResult Validate(Connections connections,
     VariableDispenser variableDispenser, IDTSComponentEvents events,
     IDTSLogging log)
  {
    try
    {
      if (this.userName == "")
      {
        //   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);
        //   Fail validation.
        return DTSExecResult.Failure;
      }
      //   Return success.
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string UserName
  {
    get
    {
      return this.userName;
    }
    set
    {
      this.userName = value;
    }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _userName As String = ""

  Public Overrides Function Validate(ByVal connections As Connections, _
     ByVal variableDispenser As VariableDispenser, _
     ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging) As DTSExecResult

    Try
      If Me._userName = "" Then
        '   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)
        '   Fail validation.
        Return DTSExecResult.Failure
      End If
      '   Return success.
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property UserName() As String
    Get
      Return Me._userName
    End Get
    Set(ByVal Value As String)
      Me._userName = Value
    End Set
  End Property

End Class
```

### <a name="persisting-the-task"></a><span data-ttu-id="3023d-145">使任务持久化</span><span class="sxs-lookup"><span data-stu-id="3023d-145">Persisting the Task</span></span>
 <span data-ttu-id="3023d-146">通常不需要对任务实现自定义持久性。</span><span class="sxs-lookup"><span data-stu-id="3023d-146">Ordinarily you do not have to implement custom persistence for a task.</span></span> <span data-ttu-id="3023d-147">自定义持久性仅在对象的属性使用复杂数据类型时才需要。</span><span class="sxs-lookup"><span data-stu-id="3023d-147">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="3023d-148">有关详细信息，请参阅[开发用于 Integration Services 的自定义对象](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3023d-148">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>

## <a name="executing-the-task"></a><span data-ttu-id="3023d-149">执行任务</span><span class="sxs-lookup"><span data-stu-id="3023d-149">Executing the Task</span></span>
 <span data-ttu-id="3023d-150">本节介绍如何使用任务继承和重写的 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-150">This section describes how to use the `Execute` method that is inherited and overridden by tasks.</span></span> <span data-ttu-id="3023d-151">本节还介绍用于提供任务执行结果信息的各种方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-151">This section also explains various ways of providing information about the results of task execution.</span></span>

### <a name="execute-method"></a><span data-ttu-id="3023d-152">Execute 方法</span><span class="sxs-lookup"><span data-stu-id="3023d-152">Execute Method</span></span>
 <span data-ttu-id="3023d-153">当 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行库调用包中包含的任务的 `Execute` 方法时，该任务将会运行。</span><span class="sxs-lookup"><span data-stu-id="3023d-153">Tasks that are contained in a package run when the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls their `Execute` method.</span></span> <span data-ttu-id="3023d-154">任务在此方法中实现其核心业务逻辑和功能，并通过发布消息、从枚举返回值 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 和重写属性的属性来提供执行结果 `get` `ExecutionValue` 。</span><span class="sxs-lookup"><span data-stu-id="3023d-154">Tasks implement their core business logic and functionality in this method, and provide the results of execution by posting messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and overriding the property `get` of the `ExecutionValue` property.</span></span>

 <span data-ttu-id="3023d-155">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基类提供了 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法的默认实现。</span><span class="sxs-lookup"><span data-stu-id="3023d-155">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class provides a default implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="3023d-156">自定义任务重写此方法以定义其运行时功能。</span><span class="sxs-lookup"><span data-stu-id="3023d-156">The custom tasks override this method to define their run-time functionality.</span></span> <span data-ttu-id="3023d-157"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 对象包装任务，从而将该任务与运行时引擎和包中的其他对象隔离。</span><span class="sxs-lookup"><span data-stu-id="3023d-157">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object wraps the task, isolating it from the run-time engine and the other objects in the package.</span></span> <span data-ttu-id="3023d-158">由于这种隔离，任务不知道它在包中所处的执行顺序位置，所以仅在由运行库调用时才运行。</span><span class="sxs-lookup"><span data-stu-id="3023d-158">Because of this isolation, the task is unaware of its location in the package with regard to its execution order, and runs only when it is called by the runtime.</span></span> <span data-ttu-id="3023d-159">这种体系结构可防止任务在执行期间修改包时可能发生的问题。</span><span class="sxs-lookup"><span data-stu-id="3023d-159">This architecture prevents problems that can occur when tasks modify the package during execution.</span></span> <span data-ttu-id="3023d-160">只有通过向任务提供作为 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法参数的对象，该任务才能访问包中的其他对象。</span><span class="sxs-lookup"><span data-stu-id="3023d-160">The task is provided access to the other objects in the package only through the objects supplied to it as parameters in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="3023d-161">这些参数允许任务引发事件、向事件日志写入条目、访问变量集合以及在事务中登记与数据源的连接，同时还保持确保包的稳定性和可靠性所需的隔离。</span><span class="sxs-lookup"><span data-stu-id="3023d-161">These parameters let tasks raise events, write entries to the event log, access the variables collection, and enlist connections to data sources in transactions, while still maintaining the isolation that is necessary to guarantee the stability and reliability of the package.</span></span>

 <span data-ttu-id="3023d-162">下表列出了提供给任务的 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法的参数。</span><span class="sxs-lookup"><span data-stu-id="3023d-162">The following table lists the parameters provided to the task in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>

|<span data-ttu-id="3023d-163">参数</span><span class="sxs-lookup"><span data-stu-id="3023d-163">Parameter</span></span>|<span data-ttu-id="3023d-164">说明</span><span class="sxs-lookup"><span data-stu-id="3023d-164">Description</span></span>|
|---------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|<span data-ttu-id="3023d-165">包含任务可用的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="3023d-165">Contains a collection of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects available to the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|<span data-ttu-id="3023d-166">包含任务可用的变量。</span><span class="sxs-lookup"><span data-stu-id="3023d-166">Contains the variables available to the task.</span></span> <span data-ttu-id="3023d-167">任务通过 VariableDispenser 使用变量，而不直接使用变量。</span><span class="sxs-lookup"><span data-stu-id="3023d-167">The tasks use variables through the VariableDispenser; the tasks do not use variables directly.</span></span> <span data-ttu-id="3023d-168">变量分配器可锁定变量和解除变量锁定，并防止死锁或覆盖。</span><span class="sxs-lookup"><span data-stu-id="3023d-168">The variable dispenser locks and unlocks variables, and prevents deadlocks or overwrites.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|<span data-ttu-id="3023d-169">包含任务向运行时引擎引发事件而调用的方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-169">Contains the methods called by the task to raise events to the run-time engine.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|<span data-ttu-id="3023d-170">包含任务向事件日志写入条目所使用的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="3023d-170">Contains methods and properties used by the task to write entries to the event log.</span></span>|
|<span data-ttu-id="3023d-171">对象</span><span class="sxs-lookup"><span data-stu-id="3023d-171">Object</span></span>|<span data-ttu-id="3023d-172">包含容器（如果有）所属的事务对象。</span><span class="sxs-lookup"><span data-stu-id="3023d-172">Contains the transaction object that the container is a part of, if any.</span></span> <span data-ttu-id="3023d-173">此值作为参数传递给 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 对象的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 方法。</span><span class="sxs-lookup"><span data-stu-id="3023d-173">This value is passed as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object.</span></span>|

### <a name="providing-execution-feedback"></a><span data-ttu-id="3023d-174">提供执行反馈</span><span class="sxs-lookup"><span data-stu-id="3023d-174">Providing Execution Feedback</span></span>
 <span data-ttu-id="3023d-175">任务将其代码包装到 `try/catch` 块中，以防止向运行时引擎引发异常。</span><span class="sxs-lookup"><span data-stu-id="3023d-175">Tasks wrap their code in `try/catch` blocks to prevent exceptions from being raised to the run-time engine.</span></span> <span data-ttu-id="3023d-176">这样可确保包会完成执行，不会意外停止。</span><span class="sxs-lookup"><span data-stu-id="3023d-176">This ensures that the package finishes execution and does not stop unexpectedly.</span></span> <span data-ttu-id="3023d-177">但是，运行时引擎提供了其他机制，可处理任务执行期间可能会出现的错误情况。</span><span class="sxs-lookup"><span data-stu-id="3023d-177">However, the run-time engine provides other mechanisms for handling error conditions that can occur during the execution of a task.</span></span> <span data-ttu-id="3023d-178">这些机制包括发布错误和警告信息、从 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 结构返回值、发布消息、返回 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值以及通过 <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> 属性提供任务执行结果的信息。</span><span class="sxs-lookup"><span data-stu-id="3023d-178">These include posting error and warning messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> structure, posting messages, returning the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value, and disclosing information about the results of task execution through the <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> property.</span></span>

 <span data-ttu-id="3023d-179"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 接口包含 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 方法，任务可调用这些方法向运行时引擎发布错误和警告消息。</span><span class="sxs-lookup"><span data-stu-id="3023d-179">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods, which can be called by the task to post error and warning messages to the run-time engine.</span></span> <span data-ttu-id="3023d-180">这两个方法需要一些参数，如错误代码、源组件、说明、帮助文件以及帮助上下文信息。</span><span class="sxs-lookup"><span data-stu-id="3023d-180">Both methods require parameters such as the error code, source component, description, Help file, and help context information.</span></span> <span data-ttu-id="3023d-181">根据任务的配置，运行库会通过引发事件和断点或向事件日志写入信息来响应这些消息。</span><span class="sxs-lookup"><span data-stu-id="3023d-181">Depending on the configuration of the task, the runtime responds to these messages by raising events and breakpoints, or by writing information to the event log.</span></span>

 <span data-ttu-id="3023d-182"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 还提供 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 属性，该属性可用于提供有关执行结果的其他信息。</span><span class="sxs-lookup"><span data-stu-id="3023d-182">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> also provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property that can be used to provide additional information about the results of execution.</span></span> <span data-ttu-id="3023d-183">例如，如果任务要在其 `Execute` 方法中删除表中的行，则该任务可能会将所删除的行数作为 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 属性的值返回。</span><span class="sxs-lookup"><span data-stu-id="3023d-183">For example, if a task deletes rows from a table as part of its `Execute` method, it might return the number of rows deleted as the value of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property.</span></span> <span data-ttu-id="3023d-184">此外，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 还提供 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="3023d-184">In addition, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> property.</span></span> <span data-ttu-id="3023d-185">此属性允许用户将从任务返回的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 映射到任何任务可见的变量。</span><span class="sxs-lookup"><span data-stu-id="3023d-185">This property lets the user map the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> returned from the task to any variable visible to the task.</span></span> <span data-ttu-id="3023d-186">随后，指定的变量即可用于建立任务之间的优先约束。</span><span class="sxs-lookup"><span data-stu-id="3023d-186">The specified variable can then be used to establish precedence constraints between tasks.</span></span>

### <a name="execution-example"></a><span data-ttu-id="3023d-187">执行示例</span><span class="sxs-lookup"><span data-stu-id="3023d-187">Execution Example</span></span>
 <span data-ttu-id="3023d-188">下面的代码示例演示 `Execute` 方法的实现，并演示了一个重写的 `ExecutionValue` 属性。</span><span class="sxs-lookup"><span data-stu-id="3023d-188">The following code example demonstrates an implementation of the `Execute` method, and shows an overridden `ExecutionValue` property.</span></span> <span data-ttu-id="3023d-189">该任务删除其 `fileName` 属性指定的文件。</span><span class="sxs-lookup"><span data-stu-id="3023d-189">The task deletes the file that is specified by the `fileName` property of the task.</span></span> <span data-ttu-id="3023d-190">如果该文件不存在或 `fileName` 属性为空字符串，任务将发布一条警告。</span><span class="sxs-lookup"><span data-stu-id="3023d-190">The task posts a warning if the file does not exist, or if the `fileName` property is an empty string.</span></span> <span data-ttu-id="3023d-191">该任务在 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 属性中返回一个 `Boolean` 值，以指示该文件是否已删除。</span><span class="sxs-lookup"><span data-stu-id="3023d-191">The task returns a `Boolean` value in the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property to indicate whether the file was deleted.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string fileName = "";
  private bool fileDeleted = false;

  public override DTSExecResult Execute(Connections cons,
     VariableDispenser vars, IDTSComponentEvents events,
     IDTSLogging log, Object txn)
  {
    try
    {
      if (this.fileName == "")
      {
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);
        this.fileDeleted = false;
      }
      else
      {
        if (System.IO.File.Exists(this.fileName))
        {
          System.IO.File.Delete(this.fileName);
          this.fileDeleted = true;
        }
        else
          this.fileDeleted = false;
      }
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string FileName
  {
    get { return this.fileName; }
    set { this.fileName = value; }
  }
  public override object ExecutionValue
  {
    get { return this.fileDeleted; }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _fileName As String = ""
  Private _fileDeleted As Boolean = False

  Public Overrides Function Execute(ByVal cons As Connections, _
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult

    Try
      If Me._fileName = "" Then
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)
        Me._fileDeleted = False
      Else
        If System.IO.File.Exists(Me._fileName) Then
          System.IO.File.Delete(Me._fileName)
          Me._fileDeleted = True
        Else
          Me._fileDeleted = False
        End If
      End If
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property FileName() As String
    Get
      Return Me._fileName
    End Get
    Set(ByVal Value As String)
      Me._fileName = Value
    End Set
  End Property

  Public Overrides ReadOnly Property ExecutionValue() As Object
    Get
      Return Me._fileDeleted
    End Get
  End Property

End Class
```

<span data-ttu-id="3023d-192">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="3023d-192">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3023d-193">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="3023d-193">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3023d-194">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="3023d-194">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3023d-195">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="3023d-195">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="3023d-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3023d-196">See Also</span></span>
 <span data-ttu-id="3023d-197">[创建自定义任务](creating-a-custom-task.md)[编码自](coding-a-custom-task.md)定义任务[为开发自定义任务开发用户界面](developing-a-user-interface-for-a-custom-task.md)</span><span class="sxs-lookup"><span data-stu-id="3023d-197">[Creating a Custom Task](creating-a-custom-task.md) [Coding a Custom Task](coding-a-custom-task.md) [Developing a User Interface for a Custom Task](developing-a-user-interface-for-a-custom-task.md)</span></span>


