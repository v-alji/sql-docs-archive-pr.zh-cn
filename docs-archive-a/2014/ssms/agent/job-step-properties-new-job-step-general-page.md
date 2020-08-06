---
title: 作业步骤属性： "新建作业步骤" ("常规" 页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: stevestein
ms.author: sstein
ms.openlocfilehash: c76e1ecb69a1475ec102f143a6a1ca34fbf91e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588808"
---
# <a name="job-step-properties-new-job-step-general-page"></a><span data-ttu-id="568ad-102">作业步骤属性：新建作业步骤（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="568ad-102">Job Step Properties: New Job Step (General Page)</span></span>
  <span data-ttu-id="568ad-103">使用此页可以查看和更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤的属性或定义新的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="568ad-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step, or to define a new job step.</span></span>  
  
 <span data-ttu-id="568ad-104">若要导航到此页，请在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器中展开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，右键单击“作业”\*\*\*\*，单击“新建作业”\*\*\*\*，选择“步骤”\*\*\*\* 页，再单击“新建”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="568ad-104">To navigate to this page, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, click **New Jobs**, select the **Steps** page, and click **New**.</span></span> <span data-ttu-id="568ad-105">也可以通过以下方法导航到此页：在对象资源管理器中右键单击某项作业，单击“属性”\*\*\*\*，选择“步骤”\*\*\*\* 页，再依次单击“新建”\*\*\*\*、“插入”\*\*\*\* 或“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="568ad-105">You can also navigate to this page by right-clicking a job in Object Explorer, clicking **Properties**, selecting the **Steps** page, and clicking **New**, **Insert**, or **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="568ad-106">选项</span><span class="sxs-lookup"><span data-stu-id="568ad-106">Options</span></span>  
 <span data-ttu-id="568ad-107">**步骤名称**</span><span class="sxs-lookup"><span data-stu-id="568ad-107">**Step name**</span></span>  
 <span data-ttu-id="568ad-108">设置作业步骤的名称。</span><span class="sxs-lookup"><span data-stu-id="568ad-108">Set the name of the job step.</span></span>  
  
 <span data-ttu-id="568ad-109">**Type**</span><span class="sxs-lookup"><span data-stu-id="568ad-109">**Type**</span></span>  
 <span data-ttu-id="568ad-110">设置作业步骤使用的子系统。</span><span class="sxs-lookup"><span data-stu-id="568ad-110">Set the subsystem that the job step uses.</span></span> <span data-ttu-id="568ad-111">显示的用于定义作业步骤的选项会根据所选子系统的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="568ad-111">Based on the subsystem you choose, the options displayed for defining the job step change.</span></span>  
  
 <span data-ttu-id="568ad-112">**运行身份**</span><span class="sxs-lookup"><span data-stu-id="568ad-112">**Run as**</span></span>  
 <span data-ttu-id="568ad-113">为作业步骤设置代理帐户。</span><span class="sxs-lookup"><span data-stu-id="568ad-113">Set the proxy account for the job step.</span></span> <span data-ttu-id="568ad-114">sysadmin 固定服务器角色的成员还可以指定“SQL 代理服务帐户”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="568ad-114">Members of the sysadmin fixed server role may also specify the **SQL Agent Service Account**.</span></span>  
  
 <span data-ttu-id="568ad-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="568ad-115">**Database**</span></span>  
 <span data-ttu-id="568ad-116">设置在其中运行作业步骤的数据库。</span><span class="sxs-lookup"><span data-stu-id="568ad-116">Set the database that the job step runs in.</span></span> <span data-ttu-id="568ad-117">此选项并不适用于所有作业步骤类型。</span><span class="sxs-lookup"><span data-stu-id="568ad-117">This option is not available for all job step types.</span></span>  
  
 <span data-ttu-id="568ad-118">**命令**</span><span class="sxs-lookup"><span data-stu-id="568ad-118">**Command**</span></span>  
 <span data-ttu-id="568ad-119">设置作业步骤运行的命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-119">Set the command that the job step runs.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="568ad-120">Transact-SQL 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-120">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="568ad-121">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-121">**Open**</span></span>  
 <span data-ttu-id="568ad-122">从文件加载命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-122">Load the command from a file.</span></span>  
  
 <span data-ttu-id="568ad-123">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-123">**Select All**</span></span>  
 <span data-ttu-id="568ad-124">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-124">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-125">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-125">**Copy**</span></span>  
 <span data-ttu-id="568ad-126">将所选文本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="568ad-126">Copy the selected text to the Clipboard.</span></span>  
  
 <span data-ttu-id="568ad-127">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-127">**Paste**</span></span>  
 <span data-ttu-id="568ad-128">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-128">Paste the contents of the Clipboard.</span></span>  
  
 <span data-ttu-id="568ad-129">Parse</span><span class="sxs-lookup"><span data-stu-id="568ad-129">**Parse**</span></span>  
 <span data-ttu-id="568ad-130">检查命令的语法。</span><span class="sxs-lookup"><span data-stu-id="568ad-130">Check the syntax of the command.</span></span>  
  
## <a name="options-for-activex-script-job-steps"></a><span data-ttu-id="568ad-131">ActiveX 脚本作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-131">Options for ActiveX Script Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="568ad-132">在未来版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，将从 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理中删除 ActiveX 脚本编写子系统。</span><span class="sxs-lookup"><span data-stu-id="568ad-132">The ActiveX Scripting subsystem will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="568ad-133">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="568ad-133">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="568ad-134">**VBScript**</span><span class="sxs-lookup"><span data-stu-id="568ad-134">**VBScript**</span></span>  
 <span data-ttu-id="568ad-135">将 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 脚本版本指定为作业步骤的语言。</span><span class="sxs-lookup"><span data-stu-id="568ad-135">Specify [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition as the language for the job steps.</span></span>  
  
 <span data-ttu-id="568ad-136">**JScript**</span><span class="sxs-lookup"><span data-stu-id="568ad-136">**JScript**</span></span>  
 <span data-ttu-id="568ad-137">将 JScript 指定为作业步骤的语言。</span><span class="sxs-lookup"><span data-stu-id="568ad-137">Specify JScript as the language for the job steps.</span></span>  
  
 <span data-ttu-id="568ad-138">**其他**</span><span class="sxs-lookup"><span data-stu-id="568ad-138">**Other**</span></span>  
 <span data-ttu-id="568ad-139">键入用其他脚本语言编写的作业步骤的语言名称。</span><span class="sxs-lookup"><span data-stu-id="568ad-139">Type the name of the language for job steps written in another scripting language.</span></span>  
  
 <span data-ttu-id="568ad-140">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-140">**Open**</span></span>  
 <span data-ttu-id="568ad-141">从文件加载命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-141">Load the command from a file.</span></span>  
  
 <span data-ttu-id="568ad-142">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-142">**Select All**</span></span>  
 <span data-ttu-id="568ad-143">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-143">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-144">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-144">**Copy**</span></span>  
 <span data-ttu-id="568ad-145">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-145">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-146">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-146">**Paste**</span></span>  
 <span data-ttu-id="568ad-147">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-147">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="568ad-148">操作系统 (CmdExec) 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-148">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="568ad-149">**成功命令的进程退出代码**</span><span class="sxs-lookup"><span data-stu-id="568ad-149">**Process exit code of a successful command**</span></span>  
 <span data-ttu-id="568ad-150">键入命令返回的用来指示进程成功的退出代码。</span><span class="sxs-lookup"><span data-stu-id="568ad-150">Type the exit code that the command returns to indicate success.</span></span>  
  
 <span data-ttu-id="568ad-151">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-151">**Open**</span></span>  
 <span data-ttu-id="568ad-152">从文件加载命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-152">Load the command from a file.</span></span>  
  
 <span data-ttu-id="568ad-153">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-153">**Select All**</span></span>  
 <span data-ttu-id="568ad-154">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-154">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-155">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-155">**Copy**</span></span>  
 <span data-ttu-id="568ad-156">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-156">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-157">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-157">**Paste**</span></span>  
 <span data-ttu-id="568ad-158">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-158">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="568ad-159">PowerShell 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-159">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="568ad-160">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-160">**Open**</span></span>  
 <span data-ttu-id="568ad-161">从文件加载脚本。</span><span class="sxs-lookup"><span data-stu-id="568ad-161">Load the script from a file.</span></span>  
  
 <span data-ttu-id="568ad-162">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-162">**Select All**</span></span>  
 <span data-ttu-id="568ad-163">选择脚本文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-163">Select the text of the script.</span></span>  
  
 <span data-ttu-id="568ad-164">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-164">**Copy**</span></span>  
 <span data-ttu-id="568ad-165">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-165">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-166">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-166">**Paste**</span></span>  
 <span data-ttu-id="568ad-167">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-167">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-distributor-job-steps"></a><span data-ttu-id="568ad-168">复制分发服务器作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-168">Options for Replication Distributor Job Steps</span></span>  
 <span data-ttu-id="568ad-169">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-169">**Select All**</span></span>  
 <span data-ttu-id="568ad-170">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-170">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-171">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-171">**Copy**</span></span>  
 <span data-ttu-id="568ad-172">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-172">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-173">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-173">**Paste**</span></span>  
 <span data-ttu-id="568ad-174">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-174">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-merge-job-steps"></a><span data-ttu-id="568ad-175">复制合并作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-175">Options for Replication Merge Job Steps</span></span>  
 <span data-ttu-id="568ad-176">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-176">**Select All**</span></span>  
 <span data-ttu-id="568ad-177">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-177">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-178">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-178">**Copy**</span></span>  
 <span data-ttu-id="568ad-179">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-179">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-180">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-180">**Paste**</span></span>  
 <span data-ttu-id="568ad-181">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-181">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="568ad-182">复制队列读取器作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-182">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="568ad-183">**Database**</span><span class="sxs-lookup"><span data-stu-id="568ad-183">**Database**</span></span>  
 <span data-ttu-id="568ad-184">用于作业步骤的数据库。</span><span class="sxs-lookup"><span data-stu-id="568ad-184">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="568ad-185">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-185">**Select All**</span></span>  
 <span data-ttu-id="568ad-186">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-186">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-187">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-187">**Copy**</span></span>  
 <span data-ttu-id="568ad-188">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-188">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-189">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-189">**Paste**</span></span>  
 <span data-ttu-id="568ad-190">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-190">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-snapshot-job-steps"></a><span data-ttu-id="568ad-191">复制快照作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-191">Options for Replication Snapshot Job Steps</span></span>  
 <span data-ttu-id="568ad-192">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-192">**Select All**</span></span>  
 <span data-ttu-id="568ad-193">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-193">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-194">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-194">**Copy**</span></span>  
 <span data-ttu-id="568ad-195">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-195">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-196">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-196">**Paste**</span></span>  
 <span data-ttu-id="568ad-197">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-197">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a><span data-ttu-id="568ad-198">复制事务-日志读取器作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-198">Options for Replication Transaction-Log Reader Job Steps</span></span>  
 <span data-ttu-id="568ad-199">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-199">**Select All**</span></span>  
 <span data-ttu-id="568ad-200">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-200">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-201">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-201">**Copy**</span></span>  
 <span data-ttu-id="568ad-202">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-202">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-203">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-203">**Paste**</span></span>  
 <span data-ttu-id="568ad-204">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-204">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a><span data-ttu-id="568ad-205">SQL Server Analysis Services 命令作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-205">Options for SQL Server Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="568ad-206">**Server**</span><span class="sxs-lookup"><span data-stu-id="568ad-206">**Server**</span></span>  
 <span data-ttu-id="568ad-207">选择运行作业步骤的服务器。</span><span class="sxs-lookup"><span data-stu-id="568ad-207">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="568ad-208">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-208">**Open**</span></span>  
 <span data-ttu-id="568ad-209">从文件加载命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-209">Load the command from a file.</span></span>  
  
 <span data-ttu-id="568ad-210">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-210">**Select All**</span></span>  
 <span data-ttu-id="568ad-211">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-211">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-212">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-212">**Copy**</span></span>  
 <span data-ttu-id="568ad-213">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-213">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-214">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-214">**Paste**</span></span>  
 <span data-ttu-id="568ad-215">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-215">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a><span data-ttu-id="568ad-216">SQL Server Analysis Services 查询作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-216">Options for SQL Server Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="568ad-217">**Server**</span><span class="sxs-lookup"><span data-stu-id="568ad-217">**Server**</span></span>  
 <span data-ttu-id="568ad-218">选择运行作业步骤的服务器。</span><span class="sxs-lookup"><span data-stu-id="568ad-218">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="568ad-219">**Database**</span><span class="sxs-lookup"><span data-stu-id="568ad-219">**Database**</span></span>  
 <span data-ttu-id="568ad-220">用于作业步骤的数据库。</span><span class="sxs-lookup"><span data-stu-id="568ad-220">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="568ad-221">**打开**</span><span class="sxs-lookup"><span data-stu-id="568ad-221">**Open**</span></span>  
 <span data-ttu-id="568ad-222">从文件加载命令。</span><span class="sxs-lookup"><span data-stu-id="568ad-222">Load the command from a file.</span></span>  
  
 <span data-ttu-id="568ad-223">**全选**</span><span class="sxs-lookup"><span data-stu-id="568ad-223">**Select All**</span></span>  
 <span data-ttu-id="568ad-224">选择命令文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-224">Select the text of the command.</span></span>  
  
 <span data-ttu-id="568ad-225">**复制**</span><span class="sxs-lookup"><span data-stu-id="568ad-225">**Copy**</span></span>  
 <span data-ttu-id="568ad-226">复制选定的文本。</span><span class="sxs-lookup"><span data-stu-id="568ad-226">Copy the selected text.</span></span>  
  
 <span data-ttu-id="568ad-227">**粘贴**</span><span class="sxs-lookup"><span data-stu-id="568ad-227">**Paste**</span></span>  
 <span data-ttu-id="568ad-228">粘贴剪贴板的内容。</span><span class="sxs-lookup"><span data-stu-id="568ad-228">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a><span data-ttu-id="568ad-229">Integration Services 包执行作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="568ad-229">Options for Integration Services Package Execution Job Steps</span></span>  
  
### <a name="general-tab"></a><span data-ttu-id="568ad-230">“常规”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-230">General Tab</span></span>  
 <span data-ttu-id="568ad-231">指定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 包的位置以及使用的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="568ad-231">Specify where the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package is located and what authentication method to use.</span></span> <span data-ttu-id="568ad-232">选择此选项卡后，可以使用以下选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-232">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="568ad-233">**包源**</span><span class="sxs-lookup"><span data-stu-id="568ad-233">**Package source**</span></span>  
 <span data-ttu-id="568ad-234">指定 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的存储位置。</span><span class="sxs-lookup"><span data-stu-id="568ad-234">Specify where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="568ad-235">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="568ad-235">Choose one of the following:</span></span>  
  
-   <span data-ttu-id="568ad-236">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="568ad-236">**SQL Server**</span></span>  
  
-   <span data-ttu-id="568ad-237">**文件系统**</span><span class="sxs-lookup"><span data-stu-id="568ad-237">**File system**</span></span>  
  
-   <span data-ttu-id="568ad-238">**SSIS 包存储区**</span><span class="sxs-lookup"><span data-stu-id="568ad-238">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="568ad-239">**Server**</span><span class="sxs-lookup"><span data-stu-id="568ad-239">**Server**</span></span>  
 <span data-ttu-id="568ad-240">键入存储 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包的服务器名。</span><span class="sxs-lookup"><span data-stu-id="568ad-240">Type the server name where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="568ad-241">仅当为“包源”\*\*\*\* 指定了 **SQL Server** 或“SSIS 包存储区”\*\*\*\* 时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="568ad-241">This option is only available when **SQL Server** or **SSIS Package Store** is specified for **Package Source**.</span></span>  
  
 <span data-ttu-id="568ad-242">**Use Windows Authentication**</span><span class="sxs-lookup"><span data-stu-id="568ad-242">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="568ad-243">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 身份验证登录到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="568ad-243">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="568ad-244">**Use SQL Server Authentication**</span><span class="sxs-lookup"><span data-stu-id="568ad-244">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="568ad-245">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证登录 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="568ad-245">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="568ad-246">如果选择了此身份验证方法，请输入相应的“用户名”\*\*\*\* 和“密码”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="568ad-246">If this method of authentication is selected, enter the appropriate **User name** and **Password**.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="568ad-247">提供身份验证是为了向后兼容。</span><span class="sxs-lookup"><span data-stu-id="568ad-247">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="568ad-248">为了增强安全性，请使用 Windows 身份验证（如果可能的话）。</span><span class="sxs-lookup"><span data-stu-id="568ad-248">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="568ad-249">**包**</span><span class="sxs-lookup"><span data-stu-id="568ad-249">**Package**</span></span>  
 <span data-ttu-id="568ad-250">键入包的位置。</span><span class="sxs-lookup"><span data-stu-id="568ad-250">Type the location of the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="568ad-251">对于受密码保护的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包，请单击“配置”\*\*\*\* 选项卡，在“包密码”\*\*\*\* 对话框中输入密码。</span><span class="sxs-lookup"><span data-stu-id="568ad-251">For password-protected [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages, click the **Configurations** tab to enter the password in the **Package Password** dialog box.</span></span> <span data-ttu-id="568ad-252">否则，执行受密码保护包的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业将失败。</span><span class="sxs-lookup"><span data-stu-id="568ad-252">Otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that executes the password-protected package will fail.</span></span>  
  
### <a name="configurations-tab"></a><span data-ttu-id="568ad-253">“配置”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-253">Configurations Tab</span></span>  
 <span data-ttu-id="568ad-254">为 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包指定配置选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-254">Specify configuration options for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="568ad-255">选择此选项卡后，以下选项可用：</span><span class="sxs-lookup"><span data-stu-id="568ad-255">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="568ad-256">**配置文件**</span><span class="sxs-lookup"><span data-stu-id="568ad-256">**Configuration files**</span></span>  
 <span data-ttu-id="568ad-257">列出包的配置文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-257">Lists the configuration files for the package.</span></span>  
  
 <span data-ttu-id="568ad-258">**添加**</span><span class="sxs-lookup"><span data-stu-id="568ad-258">**Add**</span></span>  
 <span data-ttu-id="568ad-259">添加包的配置文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-259">Add a configuration file for the package.</span></span>  
  
 <span data-ttu-id="568ad-260">**移除**</span><span class="sxs-lookup"><span data-stu-id="568ad-260">**Remove**</span></span>  
 <span data-ttu-id="568ad-261">删除包的配置文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-261">Remove a configuration file for the package.</span></span>  
  
 <span data-ttu-id="568ad-262">**上移**</span><span class="sxs-lookup"><span data-stu-id="568ad-262">**Move Up**</span></span>  
 <span data-ttu-id="568ad-263">将所选的配置文件上移。</span><span class="sxs-lookup"><span data-stu-id="568ad-263">Move the selected configuration file up.</span></span>  
  
 <span data-ttu-id="568ad-264">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="568ad-264">**Move Down**</span></span>  
 <span data-ttu-id="568ad-265">将所选的配置文件下移。</span><span class="sxs-lookup"><span data-stu-id="568ad-265">Move the selected configuration file down.</span></span>  
  
### <a name="command-files-tab"></a><span data-ttu-id="568ad-266">“命令文件”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-266">Command Files Tab</span></span>  
 <span data-ttu-id="568ad-267">选择包的命令文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-267">Select command files for the package.</span></span> <span data-ttu-id="568ad-268">将按照命令文件在列表中的显示顺序对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="568ad-268">Command files are processed in the order in which they appear in the list.</span></span> <span data-ttu-id="568ad-269">选择此选项卡后，可以使用以下选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-269">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="568ad-270">**命令文件**</span><span class="sxs-lookup"><span data-stu-id="568ad-270">**Command files**</span></span>  
 <span data-ttu-id="568ad-271">列出包的命令文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-271">Lists the command files for the package.</span></span>  
  
 <span data-ttu-id="568ad-272">**添加**</span><span class="sxs-lookup"><span data-stu-id="568ad-272">**Add**</span></span>  
 <span data-ttu-id="568ad-273">添加命令文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-273">Add a command file.</span></span>  
  
 <span data-ttu-id="568ad-274">**移除**</span><span class="sxs-lookup"><span data-stu-id="568ad-274">**Remove**</span></span>  
 <span data-ttu-id="568ad-275">删除所选的命令文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-275">Remove the selected command file.</span></span>  
  
 <span data-ttu-id="568ad-276">**上移**</span><span class="sxs-lookup"><span data-stu-id="568ad-276">**Move Up**</span></span>  
 <span data-ttu-id="568ad-277">将所选的命令文件上移。</span><span class="sxs-lookup"><span data-stu-id="568ad-277">Move the selected command file up.</span></span>  
  
 <span data-ttu-id="568ad-278">**“下移”**</span><span class="sxs-lookup"><span data-stu-id="568ad-278">**Move Down**</span></span>  
 <span data-ttu-id="568ad-279">将所选的命令文件下移。</span><span class="sxs-lookup"><span data-stu-id="568ad-279">Move the selected command file down.</span></span>  
  
### <a name="data-sources-tab"></a><span data-ttu-id="568ad-280">“数据源”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-280">Data Sources Tab</span></span>  
 <span data-ttu-id="568ad-281">在此选项卡上查看包中指定的数据源。</span><span class="sxs-lookup"><span data-stu-id="568ad-281">View the data sources specified in the package on this tab.</span></span>  
  
 <span data-ttu-id="568ad-282">**连接管理器**</span><span class="sxs-lookup"><span data-stu-id="568ad-282">**Connection Manager**</span></span>  
 <span data-ttu-id="568ad-283">查看数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="568ad-283">View the name of the data source.</span></span>  
  
 <span data-ttu-id="568ad-284">**说明**</span><span class="sxs-lookup"><span data-stu-id="568ad-284">**Description**</span></span>  
 <span data-ttu-id="568ad-285">查看数据源的说明。</span><span class="sxs-lookup"><span data-stu-id="568ad-285">View the description of the data source.</span></span>  
  
 <span data-ttu-id="568ad-286">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="568ad-286">**Connection String**</span></span>  
 <span data-ttu-id="568ad-287">查看数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="568ad-287">View the connection string for the data source.</span></span>  
  
### <a name="execution-options-tab"></a><span data-ttu-id="568ad-288">“执行选项”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-288">Execution Options Tab</span></span>  
 <span data-ttu-id="568ad-289">在此选项卡上查看或更改包的执行选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-289">View or change the execution options for the package on this tab.</span></span>  
  
 <span data-ttu-id="568ad-290">**发生验证警告时包失败**</span><span class="sxs-lookup"><span data-stu-id="568ad-290">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="568ad-291">如果希望在出现验证警告时包执行失败，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-291">Select this option for package execution to fail if validation warnings occur.</span></span>  
  
 <span data-ttu-id="568ad-292">**验证但不执行包**</span><span class="sxs-lookup"><span data-stu-id="568ad-292">**Validate package without executing**</span></span>  
 <span data-ttu-id="568ad-293">如果希望作业步骤验证但不执行包，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-293">Select this option for the job step to validate, but not execute, the package.</span></span>  
  
 <span data-ttu-id="568ad-294">**最大并发可执行文件数**</span><span class="sxs-lookup"><span data-stu-id="568ad-294">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="568ad-295">可以同时运行的可执行文件的最大数量。</span><span class="sxs-lookup"><span data-stu-id="568ad-295">Maximum number of executable files that can run at one time.</span></span>  
  
 <span data-ttu-id="568ad-296">**启用包检查点**</span><span class="sxs-lookup"><span data-stu-id="568ad-296">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="568ad-297">如果希望作业步骤使用包检查点，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-297">Select this option for the job step to use package checkpoints.</span></span>  
  
 <span data-ttu-id="568ad-298">**检查点文件**</span><span class="sxs-lookup"><span data-stu-id="568ad-298">**Checkpoint file**</span></span>  
 <span data-ttu-id="568ad-299">键入包检查点文件的名称。</span><span class="sxs-lookup"><span data-stu-id="568ad-299">Type the name of the package checkpoint file.</span></span>  
  
 <span data-ttu-id="568ad-300">**...**</span><span class="sxs-lookup"><span data-stu-id="568ad-300">**...**</span></span>  
 <span data-ttu-id="568ad-301">浏览以找到包检查点文件。</span><span class="sxs-lookup"><span data-stu-id="568ad-301">Browse to find the package checkpoint file.</span></span>  
  
 <span data-ttu-id="568ad-302">**覆盖重新启动选项**</span><span class="sxs-lookup"><span data-stu-id="568ad-302">**Override restart options**</span></span>  
 <span data-ttu-id="568ad-303">如果希望为此作业步骤指定的重新启动选项与包中指定的重新启动选项不同，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-303">Select this option to specify restart options for this job step that are different from the restart options specified in the package.</span></span>  
  
 <span data-ttu-id="568ad-304">**重新启动选项**</span><span class="sxs-lookup"><span data-stu-id="568ad-304">**Restart option**</span></span>  
 <span data-ttu-id="568ad-305">选择包重新启动时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="568ad-305">Select the action to take when the package restarts.</span></span>  
  
### <a name="logging-tab"></a><span data-ttu-id="568ad-306">“日志记录”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-306">Logging Tab</span></span>  
 <span data-ttu-id="568ad-307">在此选项卡上查看或更改包的日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="568ad-307">View or change the log providers for the package on this tab.</span></span>  
  
 <span data-ttu-id="568ad-308">**日志提供程序**</span><span class="sxs-lookup"><span data-stu-id="568ad-308">**Log Provider**</span></span>  
 <span data-ttu-id="568ad-309">选择日志提供程序的 ClassID。</span><span class="sxs-lookup"><span data-stu-id="568ad-309">Select the ClassID for the log provider.</span></span>  
  
 <span data-ttu-id="568ad-310">**配置字符串**</span><span class="sxs-lookup"><span data-stu-id="568ad-310">**Configuration String**</span></span>  
 <span data-ttu-id="568ad-311">键入日志提供程序的配置字符串。</span><span class="sxs-lookup"><span data-stu-id="568ad-311">Type the configuration string for the log provider.</span></span>  
  
 <span data-ttu-id="568ad-312">**移除**</span><span class="sxs-lookup"><span data-stu-id="568ad-312">**Remove**</span></span>  
 <span data-ttu-id="568ad-313">删除日志提供程序。</span><span class="sxs-lookup"><span data-stu-id="568ad-313">Removes the log provider.</span></span>  
  
### <a name="set-values-tab"></a><span data-ttu-id="568ad-314">“设置值”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-314">Set Values Tab</span></span>  
 <span data-ttu-id="568ad-315">在此选项卡上查看或更改包的属性值。</span><span class="sxs-lookup"><span data-stu-id="568ad-315">View or change property values for the package on this tab.</span></span>  
  
 <span data-ttu-id="568ad-316">**属性路径**</span><span class="sxs-lookup"><span data-stu-id="568ad-316">**Property path**</span></span>  
 <span data-ttu-id="568ad-317">查看或更改属性的路径。</span><span class="sxs-lookup"><span data-stu-id="568ad-317">View or change the path for the property.</span></span>  
  
 <span data-ttu-id="568ad-318">**值**</span><span class="sxs-lookup"><span data-stu-id="568ad-318">**Value**</span></span>  
 <span data-ttu-id="568ad-319">查看或更改属性的值。</span><span class="sxs-lookup"><span data-stu-id="568ad-319">View or change the value for the property.</span></span>  
  
 <span data-ttu-id="568ad-320">**移除**</span><span class="sxs-lookup"><span data-stu-id="568ad-320">**Remove**</span></span>  
 <span data-ttu-id="568ad-321">删除属性。</span><span class="sxs-lookup"><span data-stu-id="568ad-321">Removes the property.</span></span>  
  
### <a name="verification-tab"></a><span data-ttu-id="568ad-322">“验证”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-322">Verification Tab</span></span>  
 <span data-ttu-id="568ad-323">在此选项卡上为作业步骤选择验证选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-323">Select the verification options for the job step on this tab.</span></span>  
  
 <span data-ttu-id="568ad-324">**仅执行已签名的包**</span><span class="sxs-lookup"><span data-stu-id="568ad-324">**Execute only signed packages**</span></span>  
 <span data-ttu-id="568ad-325">仅运行已经签名的包。</span><span class="sxs-lookup"><span data-stu-id="568ad-325">Run only packages that have been signed.</span></span> <span data-ttu-id="568ad-326">选择此选项后，如果包没有签名，则作业步骤失败。</span><span class="sxs-lookup"><span data-stu-id="568ad-326">When this option is selected, the job step fails if the package is unsigned.</span></span>  
  
 <span data-ttu-id="568ad-327">**验证包生成**</span><span class="sxs-lookup"><span data-stu-id="568ad-327">**Verify package build**</span></span>  
 <span data-ttu-id="568ad-328">仅运行有特定内部版本号的包。</span><span class="sxs-lookup"><span data-stu-id="568ad-328">Run only packages with a specific build number.</span></span> <span data-ttu-id="568ad-329">选择此选项后，如果包没有特定内部版本号，则作业步骤失败。</span><span class="sxs-lookup"><span data-stu-id="568ad-329">When this option is selected, the job step fails if the package does not have the specified build number.</span></span>  
  
 <span data-ttu-id="568ad-330">**生成**</span><span class="sxs-lookup"><span data-stu-id="568ad-330">**Build**</span></span>  
 <span data-ttu-id="568ad-331">键入包的内部版本号。</span><span class="sxs-lookup"><span data-stu-id="568ad-331">Type the build number of the package.</span></span>  
  
 <span data-ttu-id="568ad-332">**验证包 ID**</span><span class="sxs-lookup"><span data-stu-id="568ad-332">**Verify package ID**</span></span>  
 <span data-ttu-id="568ad-333">仅运行有特定 ID 的包。</span><span class="sxs-lookup"><span data-stu-id="568ad-333">Run only packages with a specific ID.</span></span> <span data-ttu-id="568ad-334">选择此选项后，如果包没有指定的 ID，则作业步骤将失败。</span><span class="sxs-lookup"><span data-stu-id="568ad-334">When this option is selected, the job step fails if the package does not have the specified ID.</span></span>  
  
 <span data-ttu-id="568ad-335">**包 ID**</span><span class="sxs-lookup"><span data-stu-id="568ad-335">**Package ID**</span></span>  
 <span data-ttu-id="568ad-336">键入包 ID。</span><span class="sxs-lookup"><span data-stu-id="568ad-336">Type the package ID.</span></span>  
  
 <span data-ttu-id="568ad-337">**验证版本 ID**</span><span class="sxs-lookup"><span data-stu-id="568ad-337">**Verify version ID**</span></span>  
 <span data-ttu-id="568ad-338">仅运行有特定版本 ID 的包。</span><span class="sxs-lookup"><span data-stu-id="568ad-338">Run only packages with a specific version ID.</span></span> <span data-ttu-id="568ad-339">选择此选项后，如果包没有指定的版本 ID，则作业步骤将失败。</span><span class="sxs-lookup"><span data-stu-id="568ad-339">When this option is selected, the job step fails if the package does not have the specified version ID.</span></span>  
  
 <span data-ttu-id="568ad-340">**版本 ID**</span><span class="sxs-lookup"><span data-stu-id="568ad-340">**Version ID**</span></span>  
 <span data-ttu-id="568ad-341">键入版本 ID。</span><span class="sxs-lookup"><span data-stu-id="568ad-341">Type the version ID.</span></span>  
  
### <a name="command-line-tab"></a><span data-ttu-id="568ad-342">“命令行”选项卡</span><span class="sxs-lookup"><span data-stu-id="568ad-342">Command Line Tab</span></span>  
 <span data-ttu-id="568ad-343">为包指定命令行选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-343">Specify command-line options for the package.</span></span> <span data-ttu-id="568ad-344">选择此选项卡后，以下选项可用：</span><span class="sxs-lookup"><span data-stu-id="568ad-344">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="568ad-345">**还原原始选项**</span><span class="sxs-lookup"><span data-stu-id="568ad-345">**Restore the original options**</span></span>  
 <span data-ttu-id="568ad-346">使用在此对话框中设置的命令行选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-346">Use the command-line options set in this dialog.</span></span>  
  
 <span data-ttu-id="568ad-347">**手动编辑命令行**</span><span class="sxs-lookup"><span data-stu-id="568ad-347">**Edit the command line manually**</span></span>  
 <span data-ttu-id="568ad-348">在命令行窗口中指定选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-348">Specify options in the command-line window.</span></span>  
  
 <span data-ttu-id="568ad-349">**命令行**</span><span class="sxs-lookup"><span data-stu-id="568ad-349">**Command line**</span></span>  
 <span data-ttu-id="568ad-350">键入用于此包的命令行选项。</span><span class="sxs-lookup"><span data-stu-id="568ad-350">Type the command line options to use for this package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568ad-351">另请参阅</span><span class="sxs-lookup"><span data-stu-id="568ad-351">See Also</span></span>  
 <span data-ttu-id="568ad-352">[管理作业步骤](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="568ad-352">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="568ad-353">[包的 SQL Server 代理作业](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span><span class="sxs-lookup"><span data-stu-id="568ad-353">[SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span></span>  
 [<span data-ttu-id="568ad-354">复制代理管理</span><span class="sxs-lookup"><span data-stu-id="568ad-354">Replication Agent Administration</span></span>](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
