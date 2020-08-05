---
title: 在 SQL Server 代理中运行 Windows PowerShell 步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8c100e2eaf1f9b706087bd991fbc268540c29a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581338"
---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a><span data-ttu-id="10442-102">在 SQL Server 代理中运行 Windows PowerShell 步骤</span><span class="sxs-lookup"><span data-stu-id="10442-102">Run Windows PowerShell Steps in SQL Server Agent</span></span>
  <span data-ttu-id="10442-103">使用 SQL Server 代理可以在计划时间运行 SQL Server PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="10442-103">Use SQL Server Agent to run SQL Server PowerShell scripts at schedule times.</span></span>  
  
1.  <span data-ttu-id="10442-104">**开始之前：**  [限制和局限](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="10442-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="10442-105">**若要从 SQL Server 代理运行 PowerShell，请使用：** [PowerShell 作业步骤](#PShellJob)、[命令提示符作业步骤](#CmdExecJob)</span><span class="sxs-lookup"><span data-stu-id="10442-105">**To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="10442-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="10442-106">Before You Begin</span></span>  
 <span data-ttu-id="10442-107">共有多种类型的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业步骤。</span><span class="sxs-lookup"><span data-stu-id="10442-107">There are several types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="10442-108">每种类型都与用来实现特定环境（如复制代理或命令提示环境）的子系统关联。</span><span class="sxs-lookup"><span data-stu-id="10442-108">Each type is associated with a subsystem that implements a specific environment, such as a replication agent or command prompt environment.</span></span> <span data-ttu-id="10442-109">您可以对 Windows PowerShell 脚本进行编码，然后使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理将这些脚本包括在按计划时间运行或者为了响应 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事件而运行的作业中。</span><span class="sxs-lookup"><span data-stu-id="10442-109">You can code Windows PowerShell scripts, and then use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to include the scripts in jobs that run at scheduled times or in response to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="10442-110">可以使用命令提示作业步骤或 PowerShell 作业步骤运行 Windows PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="10442-110">Windows PowerShell scripts can be run using either a command prompt job step or a PowerShell job step.</span></span>  
  
1.  <span data-ttu-id="10442-111">使用 PowerShell 作业步骤以便让 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理子系统运行 `sqlps` 实用工具，该实用工具将启动 PowerShell 2.0 并导入 `sqlps` 模块。</span><span class="sxs-lookup"><span data-stu-id="10442-111">Use a PowerShell job step to have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent subsystem run the `sqlps` utility, which launches PowerShell 2.0 and imports the `sqlps` module.</span></span>  
  
2.  <span data-ttu-id="10442-112">使用命令提示作业步骤以便运行 PowerShell.exe，并且指定导入 `sqlps` 模块的脚本。</span><span class="sxs-lookup"><span data-stu-id="10442-112">Use a command prompt job step to run PowerShell.exe, and specify a script that imports the `sqlps` module.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="10442-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="10442-113">Limitations and Restrictions</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="10442-114">运行 PowerShell 并且导入 `sqlps` 模块的每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业步骤都将启动一个进程，该进程将占用大约 20 MB 的内存。</span><span class="sxs-lookup"><span data-stu-id="10442-114">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job step that runs PowerShell with the `sqlps` module launches a process which consumes approximately 20 MB of memory.</span></span> <span data-ttu-id="10442-115">同时运行大量的 Windows PowerShell 作业步骤会对性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="10442-115">Running large numbers of concurrent Windows PowerShell job steps can adversely impact performance.</span></span>  
  
##  <a name="create-a-powershell-job-step"></a><a name="PShellJob"></a><span data-ttu-id="10442-116">创建 PowerShell 作业步骤</span><span class="sxs-lookup"><span data-stu-id="10442-116">Create a PowerShell Job Step</span></span>  
 <span data-ttu-id="10442-117">**创建 PowerShell 作业步骤**</span><span class="sxs-lookup"><span data-stu-id="10442-117">**To create a PowerShell job step**</span></span>  
  
1.  <span data-ttu-id="10442-118">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10442-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="10442-119">有关创建作业的详细信息，请参阅 [创建作业](../ssms/agent/create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="10442-119">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="10442-120">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="10442-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="10442-121">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="10442-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="10442-122">在 **“类型”** 列表中单击 **PowerShell**。</span><span class="sxs-lookup"><span data-stu-id="10442-122">In the **Type** list, click **PowerShell**.</span></span>  
  
5.  <span data-ttu-id="10442-123">在 **“运行身份”** 列表中，选择该作业将要使用的代理帐户和凭据。</span><span class="sxs-lookup"><span data-stu-id="10442-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
6.  <span data-ttu-id="10442-124">在 **“命令”** 框中，输入将为该作业步骤执行的 PowerShell 脚本语法。</span><span class="sxs-lookup"><span data-stu-id="10442-124">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="10442-125">或者，单击 **“打开”** ，选择包含脚本语法的文件。</span><span class="sxs-lookup"><span data-stu-id="10442-125">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
7.  <span data-ttu-id="10442-126">单击 **“高级”** 页设置以下作业步骤选项：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数以及重试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="10442-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="create-a-command-prompt-job-step"></a><a name="CmdExecJob"></a><span data-ttu-id="10442-127">创建命令提示作业步骤</span><span class="sxs-lookup"><span data-stu-id="10442-127">Create a Command Prompt Job Step</span></span>  
 <span data-ttu-id="10442-128">**创建 CmdExec 作业步骤**</span><span class="sxs-lookup"><span data-stu-id="10442-128">**To create a CmdExec job step**</span></span>  
  
1.  <span data-ttu-id="10442-129">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10442-129">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="10442-130">有关创建作业的详细信息，请参阅 [创建作业](../ssms/agent/create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="10442-130">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="10442-131">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="10442-131">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="10442-132">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="10442-132">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="10442-133">在 **“类型”** 列表中，选择 **“操作系统(CmdExec)”**。</span><span class="sxs-lookup"><span data-stu-id="10442-133">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
5.  <span data-ttu-id="10442-134">在 **“运行身份”** 列表中，选择具有作业将使用的凭据的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="10442-134">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="10442-135">默认情况下，CmdExec 作业步骤在 SQL Server 代理服务帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="10442-135">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
6.  <span data-ttu-id="10442-136">在 **“成功命令的进程退出代码”** 框中，输入一个介于 0 到 999999 之间的值。</span><span class="sxs-lookup"><span data-stu-id="10442-136">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
7.  <span data-ttu-id="10442-137">在 **“命令”** 框中，输入 powershell.exe 以及指定要运行的 PowerShell 脚本的参数。</span><span class="sxs-lookup"><span data-stu-id="10442-137">In the **Command** box, enter powershell.exe with parameters specifying the PowerShell script to be run.</span></span>  
  
8.  <span data-ttu-id="10442-138">单击 **“高级”** 页设置以下作业步骤选项，例如：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数，以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理将作业步骤输出写入哪个文件。</span><span class="sxs-lookup"><span data-stu-id="10442-138">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="10442-139">只有 **sysadmin** 固定服务器角色的成员才可以将作业步骤输出写入到操作系统文件中。</span><span class="sxs-lookup"><span data-stu-id="10442-139">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10442-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10442-140">See Also</span></span>  
 [<span data-ttu-id="10442-141">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="10442-141">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
