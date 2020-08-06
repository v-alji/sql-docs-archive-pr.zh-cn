---
title: 在 SQL Server 代理中计划自动管理任务Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a7620935a257a4200999cce27ba901588839b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590139"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a><span data-ttu-id="c6957-102">在 SQL Server 代理中计划自动管理任务</span><span class="sxs-lookup"><span data-stu-id="c6957-102">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>
  <span data-ttu-id="c6957-103">在 SMO 中，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理由下列对象表示：</span><span class="sxs-lookup"><span data-stu-id="c6957-103">In SMO, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is represented by the following objects:</span></span>  
  
-   <span data-ttu-id="c6957-104"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> 对象具有作业、警报和操作员三个集合。</span><span class="sxs-lookup"><span data-stu-id="c6957-104">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> object has three collections of jobs, alerts and operators.</span></span>  
  
-   <span data-ttu-id="c6957-105"><xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> 对象表示可由 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理自动向其发送事件通知的寻呼程序、电子邮件地址和 net send 操作员列表。</span><span class="sxs-lookup"><span data-stu-id="c6957-105">The <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> object represents a list of pager, e-mail addresses and net send operators that can be notified of events automatically by the Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="c6957-106"><xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> 对象表示由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 监视的系统事件或性能条件等情况的列表。</span><span class="sxs-lookup"><span data-stu-id="c6957-106">The <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> object represents a list of circumstances such as system events or performance conditions that are monitored by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c6957-107"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> 对象稍微复杂一些。</span><span class="sxs-lookup"><span data-stu-id="c6957-107">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> object is slightly more complex.</span></span> <span data-ttu-id="c6957-108">它表示按指定计划运行的多步骤任务列表。</span><span class="sxs-lookup"><span data-stu-id="c6957-108">It represents a list of multi-step tasks that run at specified schedules.</span></span> <span data-ttu-id="c6957-109">步骤和计划信息存储在 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> 和 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> 对象中。</span><span class="sxs-lookup"><span data-stu-id="c6957-109">The steps and schedule information are stored in the <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> and <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> objects.</span></span>  
  
 <span data-ttu-id="c6957-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理对象位于 <xref:Microsoft.SqlServer.Management.Smo.Agent> 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="c6957-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent objects are in the <xref:Microsoft.SqlServer.Management.Smo.Agent> namespace.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c6957-111">示例</span><span class="sxs-lookup"><span data-stu-id="c6957-111">Examples</span></span>  
 <span data-ttu-id="c6957-112">若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。</span><span class="sxs-lookup"><span data-stu-id="c6957-112">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="c6957-113">有关详细信息，请参阅[在 Visual studio .net 中创建 VISUAL BASIC SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 visual Studio .Net 中创建 VISUAL C&#35; smo 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="c6957-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
1.  <span data-ttu-id="c6957-114">对于使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理的程序，必须包括 `Imports` 语句以限定该代理的命名空间。</span><span class="sxs-lookup"><span data-stu-id="c6957-114">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, you must include the `Imports` statement to qualify the Agent namespace.</span></span> <span data-ttu-id="c6957-115">请在应用程序的其他 `Imports` 语句之后、任何声明之前插入该语句，例如：</span><span class="sxs-lookup"><span data-stu-id="c6957-115">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a><span data-ttu-id="c6957-116">在 Visual Basic 中创建包含步骤和计划的作业</span><span class="sxs-lookup"><span data-stu-id="c6957-116">Creating a Job with Steps and a Schedule in Visual Basic</span></span>  
 <span data-ttu-id="c6957-117">此代码示例将创建包含步骤和计划的作业，然后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="c6957-117">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a><span data-ttu-id="c6957-118">在 Visual C# 中创建包含步骤和计划的作业</span><span class="sxs-lookup"><span data-stu-id="c6957-118">Creating a Job with Steps and a Schedule in Visual C#</span></span>  
 <span data-ttu-id="c6957-119">此代码示例将创建包含步骤和计划的作业，然后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="c6957-119">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a><span data-ttu-id="c6957-120">在 PowerShell 中创建包含步骤和计划的作业</span><span class="sxs-lookup"><span data-stu-id="c6957-120">Creating a Job with Steps and a Schedule in PowerShell</span></span>  
 <span data-ttu-id="c6957-121">此代码示例将创建包含步骤和计划的作业，然后通知操作员。</span><span class="sxs-lookup"><span data-stu-id="c6957-121">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a><span data-ttu-id="c6957-122">在 Visual Basic 中创建警报</span><span class="sxs-lookup"><span data-stu-id="c6957-122">Creating an Alert in Visual Basic</span></span>  
 <span data-ttu-id="c6957-123">此代码示例将创建由性能条件触发的警报。</span><span class="sxs-lookup"><span data-stu-id="c6957-123">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="c6957-124">该条件必须以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="c6957-124">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="c6957-125">**ObjectName |CounterName |实例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="c6957-125">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="c6957-126">对于警报通知，操作员是必需的。</span><span class="sxs-lookup"><span data-stu-id="c6957-126">An operator is required for the alert notification.</span></span> <span data-ttu-id="c6957-127"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 类型需要方括号，因为 `operator` 是一个 Visual Basic 关键字。</span><span class="sxs-lookup"><span data-stu-id="c6957-127">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a Visual Basic keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a><span data-ttu-id="c6957-128">在 Visual C# 中创建警报</span><span class="sxs-lookup"><span data-stu-id="c6957-128">Creating an Alert in Visual C#</span></span>  
 <span data-ttu-id="c6957-129">此代码示例将创建由性能条件触发的警报。</span><span class="sxs-lookup"><span data-stu-id="c6957-129">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="c6957-130">该条件必须以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="c6957-130">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="c6957-131">**ObjectName |CounterName |实例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="c6957-131">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="c6957-132">对于警报通知，操作员是必需的。</span><span class="sxs-lookup"><span data-stu-id="c6957-132">An operator is required for the alert notification.</span></span> <span data-ttu-id="c6957-133"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 类型需要方括号，因为 `operator` 是一个 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 关键字。</span><span class="sxs-lookup"><span data-stu-id="c6957-133">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```csharp
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a><span data-ttu-id="c6957-134">在 PowerShell 中创建警报</span><span class="sxs-lookup"><span data-stu-id="c6957-134">Creating an Alert in PowerShell</span></span>  
 <span data-ttu-id="c6957-135">此代码示例将创建由性能条件触发的警报。</span><span class="sxs-lookup"><span data-stu-id="c6957-135">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="c6957-136">该条件必须以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="c6957-136">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="c6957-137">**ObjectName |CounterName |实例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="c6957-137">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="c6957-138">对于警报通知，操作员是必需的。</span><span class="sxs-lookup"><span data-stu-id="c6957-138">An operator is required for the alert notification.</span></span> <span data-ttu-id="c6957-139"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 类型需要方括号，因为 `operator` 是一个 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 关键字。</span><span class="sxs-lookup"><span data-stu-id="c6957-139">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a><span data-ttu-id="c6957-140">在 Visual Basic 中使用代理帐户允许用户访问子系统</span><span class="sxs-lookup"><span data-stu-id="c6957-140">Allowing User Access to Subsystem by Using a Proxy Account in Visual Basic</span></span>  
 <span data-ttu-id="c6957-141">此代码示例演示如何使用 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 方法来允许用户访问指定的子系统。</span><span class="sxs-lookup"><span data-stu-id="c6957-141">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a><span data-ttu-id="c6957-142">在 Visual C# 中使用代理帐户允许用户访问子系统</span><span class="sxs-lookup"><span data-stu-id="c6957-142">Allowing User Access to Subsystem by Using a Proxy Account in Visual C#</span></span>  
 <span data-ttu-id="c6957-143">此代码示例演示如何使用 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 方法来允许用户访问指定的子系统。</span><span class="sxs-lookup"><span data-stu-id="c6957-143">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a><span data-ttu-id="c6957-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6957-144">See Also</span></span>  
 <span data-ttu-id="c6957-145">[SQL Server 代理](../../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="c6957-145">[SQL Server Agent](../../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="c6957-146">执行作业</span><span class="sxs-lookup"><span data-stu-id="c6957-146">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
