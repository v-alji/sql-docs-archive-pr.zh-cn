---
title: 作业步骤属性： "新建作业步骤" ("高级" 页) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692088"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a><span data-ttu-id="3c073-102">作业步骤属性：新建作业步骤（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="3c073-102">Job Step Properties: New Job Step (Advanced Page)</span></span>
  <span data-ttu-id="3c073-103">使用此页可以查看和更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤的属性。</span><span class="sxs-lookup"><span data-stu-id="3c073-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c073-104">选项</span><span class="sxs-lookup"><span data-stu-id="3c073-104">Options</span></span>  
 <span data-ttu-id="3c073-105">**成功时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="3c073-105">**On success action**</span></span>  
 <span data-ttu-id="3c073-106">设置作业步骤成功时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3c073-106">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step succeeds.</span></span>  
  
 <span data-ttu-id="3c073-107">**重试次数**</span><span class="sxs-lookup"><span data-stu-id="3c073-107">**Retry attempts**</span></span>  
 <span data-ttu-id="3c073-108">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理对失败的作业步骤的重试次数。</span><span class="sxs-lookup"><span data-stu-id="3c073-108">Sets the number of times that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attempts to retry a failed job step.</span></span>  
  
 <span data-ttu-id="3c073-109">**重试间隔（分钟）**</span><span class="sxs-lookup"><span data-stu-id="3c073-109">**Retry interval (minutes)**</span></span>  
 <span data-ttu-id="3c073-110">设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理在重试操作之间等待的时间。</span><span class="sxs-lookup"><span data-stu-id="3c073-110">Sets the amount of time for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to wait between retry attempts.</span></span>  
  
 <span data-ttu-id="3c073-111">**失败时要执行的操作**</span><span class="sxs-lookup"><span data-stu-id="3c073-111">**On failure action**</span></span>  
 <span data-ttu-id="3c073-112">设置作业步骤失败时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="3c073-112">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step fails.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="3c073-113">Transact-SQL 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="3c073-113">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="3c073-114">**输出文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-114">**Output file**</span></span>  
 <span data-ttu-id="3c073-115">设置用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-115">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="3c073-116">此选项仅对 **sysadmin** 固定服务器角色的成员可用。</span><span class="sxs-lookup"><span data-stu-id="3c073-116">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="3c073-117">**...**</span><span class="sxs-lookup"><span data-stu-id="3c073-117">**...**</span></span>  
 <span data-ttu-id="3c073-118">浏览至用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-118">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-119">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-119">**View**</span></span>  
 <span data-ttu-id="3c073-120">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，此按钮对于查看输出文件处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="3c073-120">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="3c073-121">相反，请使用记事本查看作业步骤输出文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-121">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="3c073-122">**将输出追加到现有文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-122">**Append output to existing file**</span></span>  
 <span data-ttu-id="3c073-123">将输出追加到文件的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-123">Append output to the existing contents of the file.</span></span> <span data-ttu-id="3c073-124">否则，每次作业步骤运行时都将覆盖以前的文件内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-124">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-125">**记录到表**</span><span class="sxs-lookup"><span data-stu-id="3c073-125">**Log to table**</span></span>  
 <span data-ttu-id="3c073-126">将作业步骤的输出记录到 **msdb** 数据库的 **sysjobstepslogs** 表中。</span><span class="sxs-lookup"><span data-stu-id="3c073-126">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="3c073-127">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-127">**View**</span></span>  
 <span data-ttu-id="3c073-128">在作业步骤至少运行一次后，单击“查看”\*\*\*\* 即可在该表中查看输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-128">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="3c073-129">**将输出追加到表中的现有条目**</span><span class="sxs-lookup"><span data-stu-id="3c073-129">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="3c073-130">将输出追加到表的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-130">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="3c073-131">否则，每次作业步骤运行时都将覆盖以前的表内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-131">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-132">**在历史记录中包含步骤输出**</span><span class="sxs-lookup"><span data-stu-id="3c073-132">**Include step output in history**</span></span>  
 <span data-ttu-id="3c073-133">选择此选项将在作业历史记录中包含作业步骤的输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-133">Select this option to include output from the job step in the job history.</span></span>  
  
 <span data-ttu-id="3c073-134">**作为以下用户运行**</span><span class="sxs-lookup"><span data-stu-id="3c073-134">**Run as user**</span></span>  
 <span data-ttu-id="3c073-135">如果你是 **sysadmin** 固定服务器角色的成员，则可选择另一个 SQL 登录名运行此作业步骤。</span><span class="sxs-lookup"><span data-stu-id="3c073-135">If you are a member of the **sysadmin** fixed server role, you can select another SQL login to run this job step.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="3c073-136">操作系统 (CmdExec) 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="3c073-136">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="3c073-137">**输出文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-137">**Output file**</span></span>  
 <span data-ttu-id="3c073-138">设置用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-138">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-139">**...**</span><span class="sxs-lookup"><span data-stu-id="3c073-139">**...**</span></span>  
 <span data-ttu-id="3c073-140">浏览至用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-140">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-141">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-141">**View**</span></span>  
 <span data-ttu-id="3c073-142">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，此按钮对于查看输出文件处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="3c073-142">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="3c073-143">相反，请使用记事本查看作业步骤输出文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-143">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="3c073-144">**将输出追加到现有文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-144">**Append output to existing file**</span></span>  
 <span data-ttu-id="3c073-145">每次运行时将作业步骤输出追加到之前的文件内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-145">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="3c073-146">**记录到表**</span><span class="sxs-lookup"><span data-stu-id="3c073-146">**Log to table**</span></span>  
 <span data-ttu-id="3c073-147">将作业步骤的输出记录到 **msdb** 数据库的 **sysjobstepslogs** 表中。</span><span class="sxs-lookup"><span data-stu-id="3c073-147">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="3c073-148">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-148">**View**</span></span>  
 <span data-ttu-id="3c073-149">在作业步骤至少运行一次后，单击“查看”\*\*\*\* 即可在该表中查看输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-149">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="3c073-150">**将输出追加到表中的现有条目**</span><span class="sxs-lookup"><span data-stu-id="3c073-150">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="3c073-151">将输出追加到表的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-151">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="3c073-152">否则，每次作业步骤运行时都将覆盖以前的表内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-152">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-153">**在历史记录中包含步骤输出**</span><span class="sxs-lookup"><span data-stu-id="3c073-153">**Include step output in history**</span></span>  
 <span data-ttu-id="3c073-154">选择此选项将在作业历史记录中包含作业步骤的输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-154">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="3c073-155">PowerShell 作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="3c073-155">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="3c073-156">**输出文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-156">**Output file**</span></span>  
 <span data-ttu-id="3c073-157">设置用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-157">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-158">**...**</span><span class="sxs-lookup"><span data-stu-id="3c073-158">**...**</span></span>  
 <span data-ttu-id="3c073-159">浏览至用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-159">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-160">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-160">**View**</span></span>  
 <span data-ttu-id="3c073-161">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，此按钮对于查看输出文件处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="3c073-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="3c073-162">相反，请使用记事本查看作业步骤输出文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-162">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="3c073-163">**将输出追加到现有文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-163">**Append output to existing file**</span></span>  
 <span data-ttu-id="3c073-164">每次运行时将作业步骤输出追加到之前的文件内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-164">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="3c073-165">**记录到表**</span><span class="sxs-lookup"><span data-stu-id="3c073-165">**Log to table**</span></span>  
 <span data-ttu-id="3c073-166">将作业步骤的输出记录到 **msdb** 数据库的 **sysjobstepslogs** 表中。</span><span class="sxs-lookup"><span data-stu-id="3c073-166">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="3c073-167">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-167">**View**</span></span>  
 <span data-ttu-id="3c073-168">在作业步骤至少运行一次后，单击“查看”\*\*\*\* 即可在该表中查看输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-168">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="3c073-169">**将输出追加到表中的现有条目**</span><span class="sxs-lookup"><span data-stu-id="3c073-169">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="3c073-170">将输出追加到表的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-170">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="3c073-171">否则，每次作业步骤运行时都将覆盖以前的表内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-171">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-172">**在历史记录中包含步骤输出**</span><span class="sxs-lookup"><span data-stu-id="3c073-172">**Include step output in history**</span></span>  
 <span data-ttu-id="3c073-173">选择此选项将在作业历史记录中包含作业步骤的输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-173">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="3c073-174">复制队列读取器作业步骤的选项</span><span class="sxs-lookup"><span data-stu-id="3c073-174">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="3c073-175">**Server**</span><span class="sxs-lookup"><span data-stu-id="3c073-175">**Server**</span></span>  
 <span data-ttu-id="3c073-176">设置服务器用于复制队列读取器作业步骤。</span><span class="sxs-lookup"><span data-stu-id="3c073-176">Sets the server to use for a replication queue reader job step.</span></span>  
  
 <span data-ttu-id="3c073-177">**Database**</span><span class="sxs-lookup"><span data-stu-id="3c073-177">**Database**</span></span>  
 <span data-ttu-id="3c073-178">设置数据库用于复制队列读取器作业步骤。</span><span class="sxs-lookup"><span data-stu-id="3c073-178">Sets the database to use for a replication queue reader job step.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a><span data-ttu-id="3c073-179">SQL Server Analysis Services 作业步骤的选项。</span><span class="sxs-lookup"><span data-stu-id="3c073-179">Options for SQL Server Analysis Services Job Steps</span></span>  
 <span data-ttu-id="3c073-180">**输出文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-180">**Output file**</span></span>  
 <span data-ttu-id="3c073-181">设置用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-181">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="3c073-182">此选项仅对 **sysadmin** 固定服务器角色的成员可用。</span><span class="sxs-lookup"><span data-stu-id="3c073-182">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="3c073-183">**...**</span><span class="sxs-lookup"><span data-stu-id="3c073-183">**...**</span></span>  
 <span data-ttu-id="3c073-184">浏览至用于作业步骤输出的文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-184">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="3c073-185">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-185">**View**</span></span>  
 <span data-ttu-id="3c073-186">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]禁止通过此按钮查看输出文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-186">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="3c073-187">相反，请使用记事本查看作业步骤输出文件。</span><span class="sxs-lookup"><span data-stu-id="3c073-187">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="3c073-188">**将输出追加到现有文件**</span><span class="sxs-lookup"><span data-stu-id="3c073-188">**Append output to existing file**</span></span>  
 <span data-ttu-id="3c073-189">将输出追加到文件的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-189">Append output to the existing contents of the file.</span></span> <span data-ttu-id="3c073-190">否则，每次作业步骤运行时都将覆盖以前的文件内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-190">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-191">**记录到表**</span><span class="sxs-lookup"><span data-stu-id="3c073-191">**Log to table**</span></span>  
 <span data-ttu-id="3c073-192">将作业步骤的输出记录到 **msdb** 数据库的 **sysjobstepslogs** 表中。</span><span class="sxs-lookup"><span data-stu-id="3c073-192">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="3c073-193">**视图**</span><span class="sxs-lookup"><span data-stu-id="3c073-193">**View**</span></span>  
 <span data-ttu-id="3c073-194">在作业步骤至少运行一次后，单击“查看”\*\*\*\* 即可在该表中查看输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-194">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="3c073-195">**将输出追加到表中的现有条目**</span><span class="sxs-lookup"><span data-stu-id="3c073-195">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="3c073-196">将输出追加到表的现有内容后面。</span><span class="sxs-lookup"><span data-stu-id="3c073-196">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="3c073-197">否则，每次作业步骤运行时都将覆盖以前的表内容。</span><span class="sxs-lookup"><span data-stu-id="3c073-197">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="3c073-198">**在历史记录中包含步骤输出**</span><span class="sxs-lookup"><span data-stu-id="3c073-198">**Include step output in history**</span></span>  
 <span data-ttu-id="3c073-199">选择此选项将在作业历史记录中包含作业步骤的输出。</span><span class="sxs-lookup"><span data-stu-id="3c073-199">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c073-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c073-200">See Also</span></span>  
 [<span data-ttu-id="3c073-201">管理作业步骤</span><span class="sxs-lookup"><span data-stu-id="3c073-201">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
