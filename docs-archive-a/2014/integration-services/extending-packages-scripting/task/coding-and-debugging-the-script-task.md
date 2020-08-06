---
title: 脚本任务的编码和调试 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f4383469368ac1fe3c70ff82f8c8bb2cf755838
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682957"
---
# <a name="coding-and-debugging-the-script-task"></a><span data-ttu-id="1b3fb-102">脚本任务的编码和调试</span><span class="sxs-lookup"><span data-stu-id="1b3fb-102">Coding and Debugging the Script Task</span></span>
  <span data-ttu-id="1b3fb-103">在“脚本任务编辑器”  中配置完脚本任务后，即可在脚本任务开发环境中编写自己的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-103">After configuring the Script task in the **Script Task Editor**, you write your custom code in the Script task development environment.</span></span>

## <a name="script-task-development-environment"></a><span data-ttu-id="1b3fb-104">脚本任务开发环境</span><span class="sxs-lookup"><span data-stu-id="1b3fb-104">Script Task Development Environment</span></span>
 <span data-ttu-id="1b3fb-105">脚本任务将 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 用作脚本自身的开发环境。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-105">The Script task uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the development environment for the script itself.</span></span>

 <span data-ttu-id="1b3fb-106">脚本代码以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 编写。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-106">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="1b3fb-107">在“脚本任务编辑器”中设置 **ScriptLanguage** 属性可指定脚本语言。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-107">You specify the script language by setting the **ScriptLanguage** property in the **Script Task Editor**.</span></span> <span data-ttu-id="1b3fb-108">如果您倾向于使用其他编程语言，您可以用您选择的语言开发自定义程序集，然后通过脚本任务中的代码调用其功能。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-108">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script task.</span></span>

 <span data-ttu-id="1b3fb-109">您在脚本任务中创建的脚本存储在包定义中。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-109">The script that you create in the Script task is stored in the package definition.</span></span> <span data-ttu-id="1b3fb-110">由于没有单独的脚本文件，</span><span class="sxs-lookup"><span data-stu-id="1b3fb-110">There is no separate script file.</span></span> <span data-ttu-id="1b3fb-111">因此，使用脚本任务不会影响包部署。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-111">Therefore, the use of the Script task does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="1b3fb-112">在设计包和调试脚本时，脚本代码将临时写入项目文件。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-112">When you design the package and debug the script, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="1b3fb-113">在文件中存储敏感信息会埋下安全隐患，因此建议您不要在脚本代码中包含敏感信息，如密码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-113">Because storing sensitive information in a file is a potential security risk, we recommend that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="1b3fb-114">默认情况下，`Option Strict` 在 IDE 中处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-114">By default, `Option Strict` is disabled in the IDE.</span></span>

## <a name="script-task-project-structure"></a><span data-ttu-id="1b3fb-115">脚本任务项目结构</span><span class="sxs-lookup"><span data-stu-id="1b3fb-115">Script Task Project Structure</span></span>
 <span data-ttu-id="1b3fb-116">创建或修改包含在脚本任务中的脚本时，VSTA 会打开一个空的新项目或重新打开现有项目。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-116">When you create or modify the script that is contained in a Script task, VSTA opens an empty new project or reopens the existing project.</span></span> <span data-ttu-id="1b3fb-117">创建此 VSTA 项目不会影响包的部署，因为项目保存在包文件内；脚本任务不会创建其他文件。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-117">The creation of this VSTA project does not affect the deployment of the package, because the project is saved inside the package file; the Script task does not create additional files.</span></span>

### <a name="project-items-and-classes-in-the-script-task-project"></a><span data-ttu-id="1b3fb-118">脚本任务项目中的项目项和类</span><span class="sxs-lookup"><span data-stu-id="1b3fb-118">Project Items and Classes in the Script Task Project</span></span>
 <span data-ttu-id="1b3fb-119">默认情况下，显示在 VSTA 项目资源管理器窗口中的脚本任务项目包含单个项：`ScriptMain`。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-119">By default, the Script task project displayed in the VSTA Project Explorer window contains a single item, `ScriptMain`.</span></span> <span data-ttu-id="1b3fb-120">`ScriptMain` 项又包含单个类，名称也为 `ScriptMain`。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-120">The `ScriptMain` item, in turn, contains a single class, also named `ScriptMain`.</span></span> <span data-ttu-id="1b3fb-121">该类中的代码元素根据您选择的脚本任务编程语言而有所不同：</span><span class="sxs-lookup"><span data-stu-id="1b3fb-121">The code elements in the class vary depending on the programming language that you selected for the Script task:</span></span>

-   <span data-ttu-id="1b3fb-122">如果脚本任务配置为 [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] 编程语言，则 `ScriptMain` 类有一个公共子例程 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-122">When the Script task is configured for the [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] programming language, the `ScriptMain` class has a public subroutine, `Main`.</span></span> <span data-ttu-id="1b3fb-123">`ScriptMain.Main` 子例程是运行脚本任务时运行库所调用的方法。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-123">The `ScriptMain.Main` subroutine is the method that the runtime calls when you run your Script task.</span></span>

     <span data-ttu-id="1b3fb-124">默认情况下，新脚本的 `Main` 子例程中只有一行代码：`Dts.TaskResult = ScriptResults.Success`。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-124">By default, the only code in the `Main` subroutine of a new script is the line `Dts.TaskResult = ScriptResults.Success`.</span></span> <span data-ttu-id="1b3fb-125">此代码行通知运行库任务运行成功。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-125">This line informs the runtime that the task was successful in its operation.</span></span> <span data-ttu-id="1b3fb-126">`Dts.TaskResult`[从脚本任务返回结果](../../extending-packages-scripting/task/returning-results-from-the-script-task.md)中对属性进行了讨论。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-126">The `Dts.TaskResult` property is discussed in [Returning Results from the Script Task](../../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>

-   <span data-ttu-id="1b3fb-127">如果脚本任务配置为 Visual C# 编程语言，则 `ScriptMain` 类有一个公共方法：`Main`。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-127">When the Script task is configured for the Visual C# programming language, the `ScriptMain` class has a public method, `Main`.</span></span> <span data-ttu-id="1b3fb-128">此方法在脚本任务运行时调用。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-128">The method is called when the Script task runs.</span></span>

     <span data-ttu-id="1b3fb-129">默认情况下，`Main` 方法包含一行代码：`Dts.TaskResult = (int)ScriptResults.Success`。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-129">By default, the `Main` method includes the line `Dts.TaskResult = (int)ScriptResults.Success`.</span></span> <span data-ttu-id="1b3fb-130">此代码行通知运行库任务运行成功。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-130">This line informs the runtime that the task was successful in its operation.</span></span>

 <span data-ttu-id="1b3fb-131">`ScriptMain` 项可包含 `ScriptMain` 类之外的类。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-131">The `ScriptMain` item can contain classes other than the `ScriptMain` class.</span></span> <span data-ttu-id="1b3fb-132">这些类仅在它们所在的脚本任务中可用。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-132">Classes are available only to the Script task in which they reside.</span></span>

 <span data-ttu-id="1b3fb-133">默认情况下，`ScriptMain` 项目项包含以下自动生成的代码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-133">By default, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="1b3fb-134">该代码模板还提供脚本任务的概览以及有关如何检索和操作 SSIS 对象（如变量、事件和连接）的其他信息。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-134">The code template also provides an overview of the Script task, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Task
' Write scripts using Microsoft Visual Basic 2008.
' The ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy

<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _
Partial Class ScriptMain

Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup

End Sub

Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown
Try
' Unlock variables from the read-only and read-write variable collection properties
If (Dts.Variables.Count <> 0) Then
Dts.Variables.Unlock()
End If
Catch ex As Exception
        End Try
End Sub

Enum ScriptResults
Success = DTSExecResult.Success
Failure = DTSExecResult.Failure
End Enum

' The execution engine calls this method when the task executes.
' To access the object model, use the Dts property. Connections, variables, events,
' and logging features are available as members of the Dts property as shown in the following examples.
'
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)
'
' To use the connections collection use something like the following:
' ConnectionManager cm = Dts.Connections.Add("OLEDB")
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"
'
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.
' 
' To open Help, press F1.

Public Sub Main()
'
' Add your code here
'
Dts.TaskResult = ScriptResults.Success
End Sub

End Class
```

```csharp
/*
   Microsoft SQL Server Integration Services Script Task
   Write scripts using Microsoft Visual C# 2008.
   The ScriptMain is the entry point class of the script.
*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;
using System.Windows.Forms;

namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj
{
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]
    public partial class ScriptMain
    {
        private void ScriptMain_Startup(object sender, EventArgs e)
        {

        }

        private void ScriptMain_Shutdown(object sender, EventArgs e)
        {
            try
            {
                // Unlock variables from the read-only and read-write variable collection properties
                if (Dts.Variables.Count != 0)
                {
                    Dts.Variables.Unlock();
                }
            }
            catch
            {
            }
        }

        #region VSTA generated code
        private void InternalStartup()
        {
            this.Startup += new System.EventHandler(ScriptMain_Startup);
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);
        }
        enum ScriptResults
        {
            Success = DTSExecResult.Success,
            Failure = DTSExecResult.Failure
        };

        #endregion

        /*
The execution engine calls this method when the task executes.
To access the object model, use the Dts property. Connections, variables, events,
and logging features are available as members of the Dts property as shown in the following examples.

To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;
To post a log entry, call Dts.Log("This is my log text", 999, null);
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);

To use the connections collection use something like the following:
ConnectionManager cm = Dts.Connections.Add("OLEDB");
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";

Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.

To open Help, press F1.
*/

        public void Main()
        {
            // TODO: Add your code here
            Dts.TaskResult = (int)ScriptResults.Success;
        }
    }
```

### <a name="additional-project-items-in-the-script-task-project"></a><span data-ttu-id="1b3fb-135">脚本任务项目中的其他项目项</span><span class="sxs-lookup"><span data-stu-id="1b3fb-135">Additional Project Items in the Script Task Project</span></span>
 <span data-ttu-id="1b3fb-136">脚本任务项目可包含默认的 `ScriptMain` 项以外的项。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-136">The Script task project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="1b3fb-137">您可以向项目添加类、模块和代码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-137">You can add classes, modules, and code files to the project.</span></span> <span data-ttu-id="1b3fb-138">您还可以使用文件夹来组织项组。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-138">You can also use folders to organize groups of items.</span></span> <span data-ttu-id="1b3fb-139">您添加的所有项在包中都将持久化。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-139">All the items that you add are persisted inside the package.</span></span>

### <a name="references-in-the-script-task-project"></a><span data-ttu-id="1b3fb-140">脚本任务项目中的引用</span><span class="sxs-lookup"><span data-stu-id="1b3fb-140">References in the Script Task Project</span></span>
 <span data-ttu-id="1b3fb-141">在“项目资源管理器”中右键单击脚本任务项目，然后单击“添加引用”，可以添加对托管程序集的引用   。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-141">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="1b3fb-142">有关详细信息，请参阅[引用脚本解决方案中的其他程序集](../referencing-other-assemblies-in-scripting-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-142">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="1b3fb-143">可以在“类视图”或“项目资源管理器”中查看 VSTA IDE 中的项目引用   。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-143">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="1b3fb-144">这些窗口都可以从“视图”菜单中打开  。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-144">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="1b3fb-145">可以从“项目”菜单、“项目资源管理器”或“类视图”添加新引用    。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-145">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-task"></a><span data-ttu-id="1b3fb-146">在脚本任务中与包进行交互</span><span class="sxs-lookup"><span data-stu-id="1b3fb-146">Interacting with the Package in the Script Task</span></span>
 <span data-ttu-id="1b3fb-147">脚本任务使用全局 `Dts` 对象（<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 类的一个实例）及其成员与包含包和 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 运行库进行交互。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-147">The Script task uses the global `Dts` object, which is an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, and its members to interact with the containing package and with the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

 <span data-ttu-id="1b3fb-148">下表列出了 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 类的主要公共成员，该类通过全局 `Dts` 对象向脚本任务代码公开。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-148">The following table lists the principal public members of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, which is exposed to Script task code through the global `Dts` object.</span></span> <span data-ttu-id="1b3fb-149">本节中的主题详细讨论这些成员的使用。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-149">The topics in this section discuss the use of these members in more detail.</span></span>

|<span data-ttu-id="1b3fb-150">成员</span><span class="sxs-lookup"><span data-stu-id="1b3fb-150">Member</span></span>|<span data-ttu-id="1b3fb-151">目的</span><span class="sxs-lookup"><span data-stu-id="1b3fb-151">Purpose</span></span>|
|------------|-------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|<span data-ttu-id="1b3fb-152">提供对包中定义的连接管理器的访问。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-152">Provides access to connection managers defined in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|<span data-ttu-id="1b3fb-153">提供事件接口，使脚本任务能够引发错误、警告和信息性消息。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-153">Provides an events interface to let the Script task raise errors, warnings, and informational messages.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|<span data-ttu-id="1b3fb-154">提供一种向运行库返回单个对象（除 `TaskResult` 之外）的简单方法，该对象还可用于工作流分支跳转。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-154">Provides a simple way to return a single object to the runtime (in addition to the `TaskResult`) that can also be used for workflow branching.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|<span data-ttu-id="1b3fb-155">向已启用的日志提供程序记录信息，如任务进度和结果。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-155">Logs information such as task progress and results to enabled log providers.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|<span data-ttu-id="1b3fb-156">报告任务成功或失败。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-156">Reports the success or failure of the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|<span data-ttu-id="1b3fb-157">提供任务的容器运行于的事务（如果有）。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-157">Provides the transaction, if any, within which the task's container is running.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|<span data-ttu-id="1b3fb-158">提供对 `ReadOnlyVariables` 和 `ReadWriteVariables` 任务属性中列出的、在脚本中使用的变量的访问。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-158">Provides access to the variables listed in the `ReadOnlyVariables` and `ReadWriteVariables` task properties for use within the script.</span></span>|

 <span data-ttu-id="1b3fb-159"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 类还包含一些您可能不会使用的公共成员。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-159">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class also contains some public members that you will probably not use.</span></span>

|<span data-ttu-id="1b3fb-160">成员</span><span class="sxs-lookup"><span data-stu-id="1b3fb-160">Member</span></span>|<span data-ttu-id="1b3fb-161">说明</span><span class="sxs-lookup"><span data-stu-id="1b3fb-161">Description</span></span>|
|------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|<span data-ttu-id="1b3fb-162">使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性可更加方便地访问变量。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-162">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property provides more convenient access to variables.</span></span> <span data-ttu-id="1b3fb-163">虽然您可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>，但您必须为读和写显式调用锁定和解锁变量的方法。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-163">Although you can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must explicitly call methods to lock and unlock variables for reading and writing.</span></span> <span data-ttu-id="1b3fb-164">使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 属性时，脚本任务会为您处理锁定语义。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-164">The Script task handles locking semantics for you when you use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>|

## <a name="debugging-the-script-task"></a><span data-ttu-id="1b3fb-165">调试脚本任务</span><span class="sxs-lookup"><span data-stu-id="1b3fb-165">Debugging the Script Task</span></span>
 <span data-ttu-id="1b3fb-166">若要调试脚本任务中的代码，请在代码中设置至少一个断点，然后关闭 VSTA IDE 以在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中运行包。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-166">To debug the code in your Script task, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="1b3fb-167">当包执行进入脚本任务时，VSTA IDE 会在只读模式下重新打开并显示您的代码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-167">When package execution enters the Script task, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="1b3fb-168">包执行到达您的断点后，您可以检查变量值，并单步执行剩余代码。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-168">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!WARNING]
>  <span data-ttu-id="1b3fb-169">可以在 64 位模式下运行包时调试脚本任务。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-169">You can debug the Script task when you run the package in 64-bit mode.</span></span>

> [!NOTE]
>  <span data-ttu-id="1b3fb-170">您必须执行包，以调试您的脚本任务。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-170">You must execute the package to debug into your Script task.</span></span> <span data-ttu-id="1b3fb-171">如果您只执行单个任务，则脚本任务代码中的断点将被忽略。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-171">If you execute only the individual task, breakpoints in the Script task code are ignored.</span></span>

> [!NOTE]
>  <span data-ttu-id="1b3fb-172">如果将脚本任务作为从执行包任务运行的子包的一部分来执行，则不能调试该脚本任务。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-172">You cannot debug a Script task when you run the Script task as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="1b3fb-173">在这些情况下，您在子包中的脚本任务中设置的断点将被忽略。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-173">Breakpoints that you set in the Script task in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="1b3fb-174">您可以通过单独运行子包来正常调试子包。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-174">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="1b3fb-175">当调试包含多个脚本任务的包时，调试器将调试一个脚本任务。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-175">When you debug a package that contains multiple Script tasks, the debugger debugs one Script task.</span></span> <span data-ttu-id="1b3fb-176">系统可以在调试器完成调试后调试另一个脚本任务，就像在 Foreach 循环容器或 For 循环容器中那样。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-176">The system can debug another Script task if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

## <a name="external-resources"></a><span data-ttu-id="1b3fb-177">外部资源</span><span class="sxs-lookup"><span data-stu-id="1b3fb-177">External Resources</span></span>

-   <span data-ttu-id="1b3fb-178">blogs.msdn.com 上的博客文章：[VSTA setup and configuration troubles for SSIS 2008 and R2 installations（针对 SSIS 2008 和 R2 安装的 VSTA 安装和配置难题）](https://go.microsoft.com/fwlink/?LinkId=215661)。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-178">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="1b3fb-179">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1b3fb-179">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1b3fb-180">若要从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1b3fb-180">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1b3fb-181">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1b3fb-181">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1b3fb-182">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1b3fb-182">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b3fb-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b3fb-183">See Also</span></span>
 <span data-ttu-id="1b3fb-184">[引用脚本解决方案中的其他程序集](../referencing-other-assemblies-in-scripting-solutions.md)在["脚本任务编辑器" 中配置脚本任务](configuring-the-script-task-in-the-script-task-editor.md)</span><span class="sxs-lookup"><span data-stu-id="1b3fb-184">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) [Configuring the Script Task in the Script Task Editor](configuring-the-script-task-in-the-script-task-editor.md)</span></span>


