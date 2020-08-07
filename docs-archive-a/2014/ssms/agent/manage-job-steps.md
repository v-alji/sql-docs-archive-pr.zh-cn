---
title: 管理作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server replication]
- job steps [SQL Server Agent]
- jobs [SQL Server Agent], Integration Services package step
- executable programs as job steps
- operating systems [SQL Server], job steps
- Transact-SQL job step
- job steps [Transact-SQL]
- Integration Services packages, job steps
- replication job steps [SQL Server]
- logs [SQL Server], jobs
- SQL Server Agent jobs, job steps
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: 51352afc-a0a4-428b-8985-f9e58bb57c31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7362df13956e44b73d6984691e882bec2f39a1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588237"
---
# <a name="manage-job-steps"></a><span data-ttu-id="54665-102">管理作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-102">Manage Job Steps</span></span>
  <span data-ttu-id="54665-103">作业步骤是作业对数据库或服务器执行的操作。</span><span class="sxs-lookup"><span data-stu-id="54665-103">A job step is an action that the job takes on a database or a server.</span></span> <span data-ttu-id="54665-104">每个作业必须至少有一个作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-104">Every job must have at least one job step.</span></span> <span data-ttu-id="54665-105">作业步骤可以为：</span><span class="sxs-lookup"><span data-stu-id="54665-105">Job steps can be:</span></span>  
  
-   <span data-ttu-id="54665-106">可执行程序和操作系统命令。</span><span class="sxs-lookup"><span data-stu-id="54665-106">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="54665-107">语句，包括存储过程和扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="54665-107">statements, including stored procedures and extended stored procedures.</span></span>  
  
-   <span data-ttu-id="54665-108">PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="54665-108">PowerShell scripts.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="54665-109">ActiveX 脚本。</span><span class="sxs-lookup"><span data-stu-id="54665-109">ActiveX scripts.</span></span>  
  
-   <span data-ttu-id="54665-110">复制任务。</span><span class="sxs-lookup"><span data-stu-id="54665-110">Replication tasks.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="54665-111">任务。</span><span class="sxs-lookup"><span data-stu-id="54665-111">tasks.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="54665-112">包。</span><span class="sxs-lookup"><span data-stu-id="54665-112">packages.</span></span>  
  
 <span data-ttu-id="54665-113">每个作业步骤都在特定的安全上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="54665-113">Every job step runs in a specific security context.</span></span> <span data-ttu-id="54665-114">如果作业步骤指定一个代理，该作业步骤将在该代理凭据的安全上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="54665-114">If the job step specifies a proxy, the job step runs in the security context of the credential for the proxy.</span></span> <span data-ttu-id="54665-115">如果作业步骤没有指定代理，该作业步骤将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="54665-115">If a job step does not specify a proxy, the job step runs in the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account.</span></span> <span data-ttu-id="54665-116">只有 sysadmin 固定服务器角色成员可以创建没有显式指定代理的作业。</span><span class="sxs-lookup"><span data-stu-id="54665-116">Only members of the sysadmin fixed server role can create jobs that do not explicitly specify a proxy.</span></span>  
  
 <span data-ttu-id="54665-117">由于作业步骤在特定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户的上下文中运行，所以该用户必须具有执行作业步骤所需的权限和配置。</span><span class="sxs-lookup"><span data-stu-id="54665-117">Because job steps run in the context of a specific [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user, that user must have the permissions and configuration necessary for the job step to execute.</span></span> <span data-ttu-id="54665-118">例如，如果您创建一个需要驱动器号或通用命名约定 (UNC) 路径的作业，则在测试任务时，可使用您的 Windows 用户帐户来运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-118">For example, if you create a job that requires a drive letter or a Universal Naming Convention (UNC) path, the job steps may run under your Windows user account while testing the tasks.</span></span> <span data-ttu-id="54665-119">但是，运行作业步骤的 Windows 用户还必须具有所需的权限、驱动器号配置权限或对所需驱动器的访问权限。</span><span class="sxs-lookup"><span data-stu-id="54665-119">However, the Windows user for the job step must also have the necessary permissions, drive letter configurations, or access to the required drive.</span></span> <span data-ttu-id="54665-120">否则，作业步骤会失败。</span><span class="sxs-lookup"><span data-stu-id="54665-120">Otherwise, the job step fails.</span></span> <span data-ttu-id="54665-121">为了防止出现这种问题，请确保每个作业步骤的代理都具有该作业步骤所执行任务的必要权限。</span><span class="sxs-lookup"><span data-stu-id="54665-121">To prevent this problem, ensure that the proxy for each job step has the necessary permissions for the task that the job step performs.</span></span> <span data-ttu-id="54665-122">有关详细信息，请参阅[SQL Server 数据库引擎和 AZURE SQL Database 的安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="54665-122">For more information, see [Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).</span></span>  
  
## <a name="job-step-logs"></a><span data-ttu-id="54665-123">作业步骤日志</span><span class="sxs-lookup"><span data-stu-id="54665-123">Job Step Logs</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="54665-124">代理可以将某些作业步骤的输出写入操作系统文件，也可以将其写入 msdb 数据库中的 sysjobstepslogs 表。</span><span class="sxs-lookup"><span data-stu-id="54665-124">Agent can write output from some job steps either to an operating system file or to the sysjobstepslogs table in the msdb database.</span></span> <span data-ttu-id="54665-125">下列类型的作业步骤的输出可以写入以上两个目标位置：</span><span class="sxs-lookup"><span data-stu-id="54665-125">The following job step types can write output to both destinations:</span></span>  
  
-   <span data-ttu-id="54665-126">可执行程序和操作系统命令。</span><span class="sxs-lookup"><span data-stu-id="54665-126">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="54665-127">语句。</span><span class="sxs-lookup"><span data-stu-id="54665-127">statements.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="54665-128">任务。</span><span class="sxs-lookup"><span data-stu-id="54665-128">tasks.</span></span>  
  
 <span data-ttu-id="54665-129">只有作为 sysadmin 固定服务器角色成员的用户执行的作业步骤的输出可以写入操作系统文件。</span><span class="sxs-lookup"><span data-stu-id="54665-129">Only job steps that are executed by users who are members of the sysadmin fixed server role can write job step output to operating system files.</span></span> <span data-ttu-id="54665-130">如果作业步骤由作为 msdb 数据库中 SQLAgentUserRole、SQLAgentReaderRole 或 SQLAgentOperatorRole 等固定数据库角色成员的用户执行，则只能将这些作业步骤的输出写入 sysjobstepslogs 表。</span><span class="sxs-lookup"><span data-stu-id="54665-130">If job steps are executed by users who are members of the SQLAgentUserRole, SQLAgentReaderRole, or the SQLAgentOperatorRole fixed database roles in the msdb database, then the output from these job steps can be written only to the sysjobstepslogs table.</span></span>  
  
 <span data-ttu-id="54665-131">删除作业或作业步骤时，会自动删除作业步骤日志。</span><span class="sxs-lookup"><span data-stu-id="54665-131">Job step logs are automatically deleted when jobs or job steps are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54665-132">复制任务和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包作业步骤日志记录由它们各自的子系统处理。</span><span class="sxs-lookup"><span data-stu-id="54665-132">Replication task and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step logging is handled by their respective subsystem.</span></span> <span data-ttu-id="54665-133">无法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来为这些类型的作业步骤配置作业步骤日志记录。</span><span class="sxs-lookup"><span data-stu-id="54665-133">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to configure jog step logging for these types of job steps.</span></span>  
  
## <a name="executable-programs-and-operating-system-commands-as-job-steps"></a><span data-ttu-id="54665-134">作为作业步骤的可执行程序和操作系统命令</span><span class="sxs-lookup"><span data-stu-id="54665-134">Executable Programs and Operating-System Commands As Job Steps</span></span>  
 <span data-ttu-id="54665-135">可以将可执行程序和操作系统命令作为作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-135">Executable programs and operating-system commands can be used as job steps.</span></span> <span data-ttu-id="54665-136">这些文件的扩展名可以是 .bat、.cmd、.com 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="54665-136">These files may have .bat, .cmd, .com, or .exe file extensions.</span></span>  
  
 <span data-ttu-id="54665-137">使用可执行程序或操作系统命令作为作业步骤时，必须指定以下内容：</span><span class="sxs-lookup"><span data-stu-id="54665-137">When you use an executable program or an operating-system command as a job step, you must specify:</span></span>  
  
-   <span data-ttu-id="54665-138">命令成功完成时返回的进程退出代码。</span><span class="sxs-lookup"><span data-stu-id="54665-138">The process exit code returned if the command was successful.</span></span>  
  
-   <span data-ttu-id="54665-139">要执行的命令。</span><span class="sxs-lookup"><span data-stu-id="54665-139">The command to execute.</span></span> <span data-ttu-id="54665-140">若要执行操作系统命令，只需指定该命令本身。</span><span class="sxs-lookup"><span data-stu-id="54665-140">To execute an operating system command, this is simply the command itself.</span></span> <span data-ttu-id="54665-141">对于外部程序，这就是该程序的名称和用于该程序的参数，例如： **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span><span class="sxs-lookup"><span data-stu-id="54665-141">For an external program, this is the name of the program and the arguments to the program, for example: **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54665-142">如果系统路径或执行作业步骤的用户的路径指定的目录中不包含此可执行程序，则必须提供可执行程序的完整路径。</span><span class="sxs-lookup"><span data-stu-id="54665-142">You must provide the full path to the executable if the executable is not located in a directory specified in the system path or the path for the user that the job step runs as.</span></span>  
  
## <a name="transact-sql-job-steps"></a><span data-ttu-id="54665-143">Transact-SQL 作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-143">Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="54665-144">创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤时，必须执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="54665-144">When you create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step, you must:</span></span>  
  
-   <span data-ttu-id="54665-145">确定要在其中运行作业的数据库。</span><span class="sxs-lookup"><span data-stu-id="54665-145">Identify the database in which to run the job.</span></span>  
  
-   <span data-ttu-id="54665-146">键入要执行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="54665-146">Type the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute.</span></span> <span data-ttu-id="54665-147">该语句可以调用存储过程，也可以调用扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="54665-147">The statement may call a stored procedure or an extended stored procedure.</span></span>  
  
 <span data-ttu-id="54665-148">还可以选择将现有的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文件作为作业步骤的命令打开。</span><span class="sxs-lookup"><span data-stu-id="54665-148">Optionally, you can open an existing [!INCLUDE[tsql](../../includes/tsql-md.md)] file as the command for the job step.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="54665-149">作业步骤不使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="54665-149">job steps do not use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span> <span data-ttu-id="54665-150">而是由作业步骤的所有者或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户（如果作业步骤的所有者是 sysadmin 固定服务器角色的成员）运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-150">Instead, the job step runs as the owner of the job step, or as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account if the owner of the job step is a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="54665-151">Sysadmin 固定服务器角色的成员还可以使用 sp_add_jobstep 存储过程的 [!INCLUDE[tsql](../../includes/tsql-md.md)] database_user_name *参数来指定* 作业步骤在其他用户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="54665-151">Members of the sysadmin fixed server role can also specify that [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps run under the context of another user by using the *database_user_name* parameter of the sp_add_jobstep stored procedure.</span></span> <span data-ttu-id="54665-152">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="54665-152">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54665-153">一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤可以包含多个批处理。</span><span class="sxs-lookup"><span data-stu-id="54665-153">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="54665-154">作业步骤可以包含嵌入的 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="54665-154">job steps can contain embedded GO commands.</span></span>  
  
## <a name="powershell-scripting-job-steps"></a><span data-ttu-id="54665-155">PowerShell 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-155">PowerShell Scripting Job Steps</span></span>  
 <span data-ttu-id="54665-156">当创建 PowerShell 脚本作业步骤时，必须指定以下两项之一作为步骤的命令：</span><span class="sxs-lookup"><span data-stu-id="54665-156">When you create a PowerShell script job step, you must specify one of two things as the command for the step:</span></span>  
  
-   <span data-ttu-id="54665-157">PowerShell 脚本的文本。</span><span class="sxs-lookup"><span data-stu-id="54665-157">The text of a PowerShell script.</span></span>  
  
-   <span data-ttu-id="54665-158">要打开的现有 PowerShell 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="54665-158">An existing PowerShell script file to be opened.</span></span>  
  
 <span data-ttu-id="54665-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理 powershell 子系统打开一个 powershell 会话，并加载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell 管理单元。用作作业步骤命令的 PowerShell 脚本可以引用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供程序和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="54665-159">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell subsystem opens a PowerShell session and loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins. The PowerShell script used as the job step command can reference the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span> <span data-ttu-id="54665-160">有关使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 管理单元编写 PowerShell 脚本的详细信息，请参阅 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="54665-160">For more information about writing PowerShell scripts using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins, see the [SQL Server PowerShell](../../powershell/sql-server-powershell.md).</span></span>  
  
## <a name="activex-scripting-job-steps"></a><span data-ttu-id="54665-161">ActiveX 脚本作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-161">ActiveX Scripting Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="54665-162">在未来版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，ActiveX 脚本作业步骤将从 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理中删除。</span><span class="sxs-lookup"><span data-stu-id="54665-162">The ActiveX scripting job step will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54665-163">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="54665-163">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="54665-164">创建 ActiveX 脚本作业步骤时，必须执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="54665-164">When you create an ActiveX scripting job step, you must:</span></span>  
  
-   <span data-ttu-id="54665-165">确定编写作业步骤所使用的脚本语言。</span><span class="sxs-lookup"><span data-stu-id="54665-165">Identify the scripting language in which the job step is written.</span></span>  
  
-   <span data-ttu-id="54665-166">编写 ActiveX 脚本。</span><span class="sxs-lookup"><span data-stu-id="54665-166">Write the ActiveX script.</span></span>  
  
 <span data-ttu-id="54665-167">还可以将现有的 ActiveX 脚本文件作为作业步骤的命令打开。</span><span class="sxs-lookup"><span data-stu-id="54665-167">You can also open an existing ActiveX script file as the command for the job step.</span></span> <span data-ttu-id="54665-168">另外，可以在外部编译 ActiveX 脚本命令（例如，使用 Microsoft Visual Basic），然后作为可执行程序运行。</span><span class="sxs-lookup"><span data-stu-id="54665-168">Alternatively, ActiveX script commands can be externally compiled (for example, using Microsoft Visual Basic) and then run as executable programs.</span></span>  
  
 <span data-ttu-id="54665-169">当作业步骤命令是 ActiveX 脚本时，可以使用 SQLActiveScriptHost 对象将结果输出到作业步骤历史记录日志或创建 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="54665-169">When a job step command is an ActiveX script, you can use the SQLActiveScriptHost object to print output to the job step history log or create COM objects.</span></span> <span data-ttu-id="54665-170">SQLActiveScriptHost 是一个全局对象，由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理宿主系统引入脚本命名空间。</span><span class="sxs-lookup"><span data-stu-id="54665-170">SQLActiveScriptHost is a global object that is introduced by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent hosting system into the script name space.</span></span> <span data-ttu-id="54665-171">该对象具有两种方法（Print 和 CreateObject）。</span><span class="sxs-lookup"><span data-stu-id="54665-171">The object has two methods (Print and CreateObject).</span></span> <span data-ttu-id="54665-172">下面的示例说明 ActiveX 脚本在 Visual Basic Scripting Edition (VBScript) 中是如何实现的。</span><span class="sxs-lookup"><span data-stu-id="54665-172">The following example shows how ActiveX scripting works in Visual Basic Scripting Edition (VBScript).</span></span>  
  
```  
' VBScript example for ActiveX Scripting job step  
' Create a Dmo.Server object. The object connects to the  
' server on which the script is running.  
  
Set oServer = CreateObject("SQLDmo.SqlServer")  
oServer.LoginSecure = True  
oServer.Connect "(local)"  
'Disconnect and destroy the server object  
oServer.DisConnect  
Set oServer = nothing
```  
  
## <a name="replication-job-steps"></a><span data-ttu-id="54665-173">复制作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-173">Replication Job Steps</span></span>  
 <span data-ttu-id="54665-174">使用复制创建发布和订阅时，默认情况下会创建复制作业。</span><span class="sxs-lookup"><span data-stu-id="54665-174">When you create publications and subscriptions using replication, replication jobs are created by default.</span></span> <span data-ttu-id="54665-175">创建的作业类型由复制的类型（快照、事务或合并）和所用选项确定。</span><span class="sxs-lookup"><span data-stu-id="54665-175">The type of job created is determined by the type of replication (snapshot, transactional, or merge) and the options used.</span></span>  
  
 <span data-ttu-id="54665-176">复制作业步骤将激活下列复制代理之一：</span><span class="sxs-lookup"><span data-stu-id="54665-176">Replication job steps activate one of these replication agents:</span></span>  
  
-   <span data-ttu-id="54665-177">快照代理（快照作业）</span><span class="sxs-lookup"><span data-stu-id="54665-177">Snapshot Agent (Snapshot job)</span></span>  
  
-   <span data-ttu-id="54665-178">日志读取器代理（LogReader 作业）</span><span class="sxs-lookup"><span data-stu-id="54665-178">Log Reader Agent (LogReader job)</span></span>  
  
-   <span data-ttu-id="54665-179">分发代理（分发作业）</span><span class="sxs-lookup"><span data-stu-id="54665-179">Distribution Agent (Distribution job)</span></span>  
  
-   <span data-ttu-id="54665-180">合并代理（合并作业）</span><span class="sxs-lookup"><span data-stu-id="54665-180">Merge Agent (Merge job)</span></span>  
  
-   <span data-ttu-id="54665-181">队列读取器代理（QueueReader 作业）</span><span class="sxs-lookup"><span data-stu-id="54665-181">Queue Reader Agent (QueueReader job)</span></span>  
  
 <span data-ttu-id="54665-182">设置复制后，您可以指定以下列三种方式之一运行复制代理：在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理启动后连续运行、按需运行或按计划运行。</span><span class="sxs-lookup"><span data-stu-id="54665-182">When replication is set up, you can specify to run the replication agents in one of three ways: continuously after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is started, on demand, or according to a schedule.</span></span> <span data-ttu-id="54665-183">有关复制代理的详细信息，请参阅 [复制代理概述](../../relational-databases/replication/agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="54665-183">For more information about replication agents, see [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md).</span></span>  
  
## <a name="analysis-services-job-steps"></a><span data-ttu-id="54665-184">Analysis Services 作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-184">Analysis Services Job Steps</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="54665-185">代理支持两种不同类型的 Analysis Services 作业步骤：命令作业步骤和查询作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-185">Agent supports two distinct types of Analysis Services job steps, command job steps, and query job steps.</span></span>  
  
### <a name="analysis-services-command-job-steps"></a><span data-ttu-id="54665-186">Analysis Services 命令作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-186">Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="54665-187">创建 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 命令作业步骤时，必须：</span><span class="sxs-lookup"><span data-stu-id="54665-187">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] command job step, you must:</span></span>  
  
-   <span data-ttu-id="54665-188">标识要运行作业步骤的数据库 OLAP 服务器。</span><span class="sxs-lookup"><span data-stu-id="54665-188">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="54665-189">键入要执行的语句。</span><span class="sxs-lookup"><span data-stu-id="54665-189">Type the statement to execute.</span></span> <span data-ttu-id="54665-190">对于  Execute[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] \*\*\*\* 方法，此语句必须为 XML。</span><span class="sxs-lookup"><span data-stu-id="54665-190">The statement must be an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** method.</span></span> <span data-ttu-id="54665-191">对于  Discover[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] \*\*\*\* 方法，此语句可能不包含完整的 SOAP 信封或 XML。</span><span class="sxs-lookup"><span data-stu-id="54665-191">The statement may not contain a complete SOAP envelope or an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** method.</span></span> <span data-ttu-id="54665-192">注意：虽然 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 支持完整的 SOAP 信封和 **Discover** 方法，但是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤却不支持。</span><span class="sxs-lookup"><span data-stu-id="54665-192">Notice that, while [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span>  
  
### <a name="analysis-services-query-job-steps"></a><span data-ttu-id="54665-193">Analysis Services 查询作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-193">Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="54665-194">创建 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 查询作业步骤时，必须：</span><span class="sxs-lookup"><span data-stu-id="54665-194">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] query job step, you must:</span></span>  
  
-   <span data-ttu-id="54665-195">标识要运行作业步骤的数据库 OLAP 服务器。</span><span class="sxs-lookup"><span data-stu-id="54665-195">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="54665-196">键入要执行的语句。</span><span class="sxs-lookup"><span data-stu-id="54665-196">Type the statement to execute.</span></span> <span data-ttu-id="54665-197">该语句必须是一个多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="54665-197">The statement must be a multidimensional expressions (MDX) query.</span></span>  
  
 <span data-ttu-id="54665-198">有关 MDX 的详细信息，请参阅[Mdx Query 基础 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="54665-198">For more information on MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
## <a name="integration-services-packages"></a><span data-ttu-id="54665-199">Integration Services 包</span><span class="sxs-lookup"><span data-stu-id="54665-199">Integration Services Packages</span></span>  
 <span data-ttu-id="54665-200">当创建 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包作业步骤时，必须执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="54665-200">When you create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step, you must do the following:</span></span>  
  
-   <span data-ttu-id="54665-201">确定包的源。</span><span class="sxs-lookup"><span data-stu-id="54665-201">Identify the source of the package.</span></span>  
  
-   <span data-ttu-id="54665-202">确定包的位置。</span><span class="sxs-lookup"><span data-stu-id="54665-202">Identify the location of the package.</span></span>  
  
-   <span data-ttu-id="54665-203">如果包需要配置文件，则确定配置文件。</span><span class="sxs-lookup"><span data-stu-id="54665-203">If configuration files are required for the package, identify the configuration files.</span></span>  
  
-   <span data-ttu-id="54665-204">如果包需要命令文件，则确定命令文件。</span><span class="sxs-lookup"><span data-stu-id="54665-204">If command files are required for the package, identify the command files.</span></span>  
  
-   <span data-ttu-id="54665-205">确定用于包的验证。</span><span class="sxs-lookup"><span data-stu-id="54665-205">Identify the verification to use for the package.</span></span> <span data-ttu-id="54665-206">例如，可以指定包必须签名，也可以指定包必须具有特定的包 ID。</span><span class="sxs-lookup"><span data-stu-id="54665-206">For example, you can specify that the package must be signed, or that the package must have a specific package ID.</span></span>  
  
-   <span data-ttu-id="54665-207">确定包的数据源。</span><span class="sxs-lookup"><span data-stu-id="54665-207">Identify the data sources for the package.</span></span>  
  
-   <span data-ttu-id="54665-208">确定包的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="54665-208">Identify the log providers for the package.</span></span>  
  
-   <span data-ttu-id="54665-209">指定运行包之前要设置的变量和值。</span><span class="sxs-lookup"><span data-stu-id="54665-209">Specify variables and values to set before running the package.</span></span>  
  
-   <span data-ttu-id="54665-210">确定执行选项。</span><span class="sxs-lookup"><span data-stu-id="54665-210">Identify execution options.</span></span>  
  
-   <span data-ttu-id="54665-211">添加或修改命令行选项。</span><span class="sxs-lookup"><span data-stu-id="54665-211">Add or modify command-line options.</span></span>  
  
 <span data-ttu-id="54665-212">请注意，如果将包部署到 SSIS 目录并且指定 **SSIS 目录** 作为包的来源，则会自动获取包中的大多数此类配置信息。</span><span class="sxs-lookup"><span data-stu-id="54665-212">Note that if you deployed the package to the SSIS Catalog and you specify **SSIS Catalog** as the package source, much of this configuration information is obtained automatically from the package.</span></span> <span data-ttu-id="54665-213">在“配置”\*\*\*\* 选项卡下，可以指定环境、参数值、连接管理器值、属性重写以及包是否在 32 位运行时环境下运行。</span><span class="sxs-lookup"><span data-stu-id="54665-213">Under the **Configuration** tab you can specify the environment, parameter values, connection manager values, property overrides, and whether the package runs in a 32-bit runtime environment.</span></span>  
  
 <span data-ttu-id="54665-214">有关创建运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的作业步骤的详细信息，请参阅 [包的 SQL Server 代理作业](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="54665-214">For more information about creating job steps that run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="54665-215">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="54665-215">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54665-216">**说明**</span><span class="sxs-lookup"><span data-stu-id="54665-216">**Description**</span></span>|<span data-ttu-id="54665-217">**主题**</span><span class="sxs-lookup"><span data-stu-id="54665-217">**Topic**</span></span>|  
|<span data-ttu-id="54665-218">描述如何创建带有可执行程序的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-218">Describes how to create a job step with an executable program.</span></span>|[<span data-ttu-id="54665-219">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="54665-219">Create a CmdExec Job Step</span></span>](create-a-cmdexec-job-step.md)|  
|<span data-ttu-id="54665-220">介绍如何重置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理权限。</span><span class="sxs-lookup"><span data-stu-id="54665-220">Describes how to reset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent permissions.</span></span>|[<span data-ttu-id="54665-221">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="54665-221">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>](configure-a-user-to-create-and-manage-sql-server-agent-jobs.md)|  
|<span data-ttu-id="54665-222">介绍如何创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-222">Describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step.</span></span>|[<span data-ttu-id="54665-223">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="54665-223">Create a Transact-SQL Job Step</span></span>](create-a-transact-sql-job-step.md)|  
|<span data-ttu-id="54665-224">说明如何定义 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理 Transact-SQL 作业步骤的选项。</span><span class="sxs-lookup"><span data-stu-id="54665-224">Describes how to define options for Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Transact-SQL job steps.</span></span>|[<span data-ttu-id="54665-225">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="54665-225">Define Transact-SQL Job Step Options</span></span>](define-transact-sql-job-step-options.md)|  
|<span data-ttu-id="54665-226">介绍如何创建 ActiveX 脚本作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-226">Describes how to create an ActiveX script job step.</span></span>|[<span data-ttu-id="54665-227">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="54665-227">Create an ActiveX Script Job Step</span></span>](create-an-activex-script-job-step.md)|  
|<span data-ttu-id="54665-228">介绍如何创建和定义用于执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services 命令和查询的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤。</span><span class="sxs-lookup"><span data-stu-id="54665-228">Describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries.</span></span>|[<span data-ttu-id="54665-229">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="54665-229">Create an Analysis Services Job Step</span></span>](create-an-analysis-services-job-step.md)|  
|<span data-ttu-id="54665-230">介绍在作业执行期间失败时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 应执行什么操作。</span><span class="sxs-lookup"><span data-stu-id="54665-230">Describes what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span>|[<span data-ttu-id="54665-231">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="54665-231">Set Job Step Success or Failure Flow</span></span>](set-job-step-success-or-failure-flow.md)|  
|<span data-ttu-id="54665-232">说明如何在“作业步骤属性”对话框中查看作业步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="54665-232">Describes how to view job step details in the Job Step Properties dialog.</span></span>|[<span data-ttu-id="54665-233">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="54665-233">View Job Step Information</span></span>](view-job-step-information.md)|  
|<span data-ttu-id="54665-234">说明如何删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤日志。</span><span class="sxs-lookup"><span data-stu-id="54665-234">Describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>|[<span data-ttu-id="54665-235">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="54665-235">Delete a Job Step Log</span></span>](delete-a-job-step-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="54665-236">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54665-236">See Also</span></span>  
 <span data-ttu-id="54665-237">[dbo.sysjobstepslogs &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54665-237">[dbo.sysjobstepslogs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span></span>  
 <span data-ttu-id="54665-238">[创建作业](create-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="54665-238">[Create Jobs](create-jobs.md) </span></span>  
 [<span data-ttu-id="54665-239">sp_add_job (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="54665-239">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
