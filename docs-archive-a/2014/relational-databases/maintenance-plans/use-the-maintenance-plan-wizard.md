---
title: 使用维护计划向导 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.ag.maintwiz.planprop.f1
- sql12.ag.maintwiz.task.f1
- sql12.ag.maintwiz.maintcleanup.f1
- sql12.ag.maintwiz.indexdefrag.f1
- sql12.ag.maintwiz.order.f1
- sql12.ag.maintwiz.histcleanup.f1
- sql12.ag.maintwiz.backuplog.f1
- sql12.ag.maintwiz.progress.f1
- sql12.ag.maintwiz.execagentjob.f1
- sql12.ag.maintwiz.integrity.f1
- sql12.ag.maintwiz.welcome.f1
- sql12.ag.maintwiz.backupdiff.f1
- sql12.ag.maintwiz.server.f1
- sql12.ag.maintwiz.summary.f1
- sql12.ag.maintwiz.backupfull.f1
- sql12.ag.maintwiz.report.f1
- sql12.ag.maintwiz.shrinkdb.f1
- sql12.ag.maintwiz.reindex.f1
- sql12.ag.maintwiz.updatestats.f1
helpviewer_keywords:
- Maintenance Plan Wizard
- Database Maintenance Plan Wizard
- Database Maintenance Plan Wizard, starting
ms.assetid: db65c726-9892-480c-873b-3af29afcee44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac134bbd4c65da4700990b69b09134230e98903f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578891"
---
# <a name="use-the-maintenance-plan-wizard"></a><span data-ttu-id="c46fc-102">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="c46fc-102">Use the Maintenance Plan Wizard</span></span>
  <span data-ttu-id="c46fc-103">本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中使用维护计划向导创建单个服务器或多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Wizard in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c46fc-104">维护计划向导可创建 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理可定期运行的维护计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-104">The Maintenance Plan Wizard creates a maintenance plan that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can run on a regular basis.</span></span> <span data-ttu-id="c46fc-105">它使您可以执行各种数据库管理任务，包括备份、数据库完整性检查或以指定的间隔更新数据库统计信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-105">This allows you to perform various database administration tasks, including backups, database integrity checks, or database statistics updates, at specified intervals.</span></span>  
  
 <span data-ttu-id="c46fc-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c46fc-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c46fc-107">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c46fc-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c46fc-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c46fc-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c46fc-109">安全性</span><span class="sxs-lookup"><span data-stu-id="c46fc-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="c46fc-110">在 SQL Server Management Studio 中使用维护计划向导创建维护计划</span><span class="sxs-lookup"><span data-stu-id="c46fc-110">Creating a maintenance plan using the Maintenance Plan Wizard in SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c46fc-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="c46fc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c46fc-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="c46fc-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c46fc-113">若要创建多服务器维护计划，必须配置包含一个主服务器和一个（或多个）目标服务器的多服务器环境。</span><span class="sxs-lookup"><span data-stu-id="c46fc-113">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="c46fc-114">必须在主服务器上创建和维护多服务器维护计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-114">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="c46fc-115">在目标服务器上可以查看这些计划，但不能进行维护。</span><span class="sxs-lookup"><span data-stu-id="c46fc-115">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="c46fc-116">**db_ssisadmin** 和 **dc_admin** 角色的成员可以将其特权提升为 **sysadmin**。</span><span class="sxs-lookup"><span data-stu-id="c46fc-116">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="c46fc-117">因为这些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 **代理的** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全上下文可以执行这些包，所以可以实现特权提升。</span><span class="sxs-lookup"><span data-stu-id="c46fc-117">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="c46fc-118">若要防止在运行维护计划、数据收集组和其它 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时提升特权，请将运行包的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业配置为具有有限特权的代理帐户，或仅将 **sysadmin** 成员添加到 **db_ssisadmin** 和 **dc_admin** 角色。</span><span class="sxs-lookup"><span data-stu-id="c46fc-118">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c46fc-119">Security</span><span class="sxs-lookup"><span data-stu-id="c46fc-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c46fc-120">权限</span><span class="sxs-lookup"><span data-stu-id="c46fc-120">Permissions</span></span>  
 <span data-ttu-id="c46fc-121">若要创建或管理维护计划，您必须是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="c46fc-121">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="c46fc-122">对象资源管理器只为属于 **sysadmin** 固定服务器角色成员的用户显示 **“维护计划”** 节点。</span><span class="sxs-lookup"><span data-stu-id="c46fc-122">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-wizard"></a><a name="SSMSProcedure"></a><span data-ttu-id="c46fc-123">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="c46fc-123">Using Maintenance Plan Wizard</span></span>  
  
#### <a name="to-start-the-maintenance-plan-wizard"></a><span data-ttu-id="c46fc-124">启动维护计划向导</span><span class="sxs-lookup"><span data-stu-id="c46fc-124">To start the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="c46fc-125">展开要创建您的管理计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="c46fc-125">Expand the server where you want to create your management plan.</span></span>  
  
2.  <span data-ttu-id="c46fc-126">展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c46fc-126">Expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="c46fc-127">右键单击“维护计划”文件夹，然后选择“维护计划向导”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-127">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="c46fc-128">在 **“SQL Server 维护计划向导”** 页上，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-128">On the **SQL Server Maintenance Plan Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="c46fc-129">关于 **“选择计划属性”** 页：</span><span class="sxs-lookup"><span data-stu-id="c46fc-129">On the **Select Plan Properties** page:</span></span>  
  
    1.  <span data-ttu-id="c46fc-130">在 **“名称”** 框中，输入您创建的维护计划的名称。</span><span class="sxs-lookup"><span data-stu-id="c46fc-130">In the **Name** box, enter the name of the maintenance plan you are creating.</span></span>  
  
    2.  <span data-ttu-id="c46fc-131">在 **“说明”** 框中，简要介绍您的维护计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-131">In the **Description** box, briefly describe your maintenance plan.</span></span>  
  
    3.  <span data-ttu-id="c46fc-132">在 **“运行身份”** 列表中，指定执行维护计划时 Microsoft SQL Server 代理使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="c46fc-132">In the **Run as** list, specify the credential that Microsoft SQL Server Agent uses when executing the maintenance plan.</span></span>  
  
    4.  <span data-ttu-id="c46fc-133">选择 **“每项任务单独计划”** 或 **“整个计划统筹安排或无计划”** 指定维护计划的重复执行计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-133">Select either **Separate schedules for each task** or **Single schedule for the entire plan or no schedule** to specify the recurring schedule of the maintenance plan.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c46fc-134">如果您选中 **“每项任务单独计划”**，则需要为您维护计划中的每个任务按照 **e.**</span><span class="sxs-lookup"><span data-stu-id="c46fc-134">If you select **Separate schedules for each task**, you will need to follow the steps in **e.**</span></span> <span data-ttu-id="c46fc-135">下面的步骤执行操作。</span><span class="sxs-lookup"><span data-stu-id="c46fc-135">below for each task in your maintenance plan.</span></span>  
  
    5.  <span data-ttu-id="c46fc-136">如果您选择了 **“整个计划统筹安排或无计划”** ，则在 **“计划”** 下面单击 **“更改”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-136">If you selected **Single schedule for the entire plan or no schedule**, under **Schedule**, click **Change**.</span></span>  
  
        1.  <span data-ttu-id="c46fc-137">在“新建作业计划”对话框的“名称”框中，输入作业计划的名称 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-137">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
        2.  <span data-ttu-id="c46fc-138">在 **“计划类型”** 列表中选择计划类型：</span><span class="sxs-lookup"><span data-stu-id="c46fc-138">On the **Schedule type** list, select the type of schedule:</span></span>  
  
            -   <span data-ttu-id="c46fc-139">**SQL Server 代理启动时自动启动**</span><span class="sxs-lookup"><span data-stu-id="c46fc-139">**Start automatically when SQL Server Agent starts**</span></span>  
  
            -   <span data-ttu-id="c46fc-140">**CPU 空闲时启动**</span><span class="sxs-lookup"><span data-stu-id="c46fc-140">**Start whenever the CPUs become idle**</span></span>  
  
            -   <span data-ttu-id="c46fc-141">**重复执行**。</span><span class="sxs-lookup"><span data-stu-id="c46fc-141">**Recurring**.</span></span> <span data-ttu-id="c46fc-142">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-142">This is the default selection.</span></span>  
  
            -   <span data-ttu-id="c46fc-143">**一次**</span><span class="sxs-lookup"><span data-stu-id="c46fc-143">**One time**</span></span>  
  
        3.  <span data-ttu-id="c46fc-144">选择或清除 **“已启用”** 复选框以启用或禁用计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-144">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
        4.  <span data-ttu-id="c46fc-145">如果选择 **“重复执行”** ：</span><span class="sxs-lookup"><span data-stu-id="c46fc-145">If you select **Recurring**:</span></span>  
  
            1.  <span data-ttu-id="c46fc-146">在 **“频率”** 下的 **“执行”** 列表中，指定执行的频率：</span><span class="sxs-lookup"><span data-stu-id="c46fc-146">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
                -   <span data-ttu-id="c46fc-147">如果选择 **“每天”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（天）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-147">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
                -   <span data-ttu-id="c46fc-148">如果选择 **“每周”** ，请在 **“执行间隔”** 框中输入重复作业计划的频率（周）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-148">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="c46fc-149">选择运行作业计划的一周中的某天或某些天。</span><span class="sxs-lookup"><span data-stu-id="c46fc-149">Select the day or days of the week on which the job schedule is run.</span></span>  
  
                -   <span data-ttu-id="c46fc-150">如果选择 **“每月”** ，可以选择 **“天”** 或 **“特定日期”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-150">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                    -   <span data-ttu-id="c46fc-151">如果选择 **“天”** ，请输入要运行作业计划的当月日期和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-151">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="c46fc-152">例如，如果要每隔一个月在当月的 15 日运行计划作业，请选择“天”，在第一个框中输入“15”，在第二个框中输入“2”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-152">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="c46fc-153">请注意，第二个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-153">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                    -   <span data-ttu-id="c46fc-154">如果选择 **“特定日期”** ，请选择要运行作业计划的当月内一周的特定一天和作业计划的重复频率（月）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-154">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="c46fc-155">例如，如果要每隔一个月在当月的最后一个工作日运行作业计划，请选择“天”，从第一个列表中选择“最后一周”，从第二个列表中选择“工作日”，然后在最后一个框中输入“2”  。</span><span class="sxs-lookup"><span data-stu-id="c46fc-155">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="c46fc-156">还可以从前两个列表中选择“第一周”、“第二周”、“第三周”或“第四周”以及特定工作日（例如：星期日或星期三）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-156">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="c46fc-157">请注意，最后一个框中允许的最大数是“99”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-157">Please note that the largest number allowed in the last box is "99".</span></span>  
  
            2.  <span data-ttu-id="c46fc-158">在 **“每天频率”** 下，指定作业计划运行的当天作业计划的重复频率。</span><span class="sxs-lookup"><span data-stu-id="c46fc-158">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
                -   <span data-ttu-id="c46fc-159">如果选择 **“执行一次，时间为:”** ，请在 **“执行一次，时间为:”** 框中输入运行作业计划的当天的特定时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-159">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="c46fc-160">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="c46fc-160">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
                -   <span data-ttu-id="c46fc-161">如果选择 **“执行间隔”** ，请在 **“频率”** 下指定所选日运行作业计划的频率。</span><span class="sxs-lookup"><span data-stu-id="c46fc-161">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="c46fc-162">例如，如果要在运行作业计划的当天每隔 2 小时重复一次，请选择“执行间隔”，在第一个框中输入“2”，然后从列表中选择“小时” 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-162">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="c46fc-163">从此列表中还可以选择“分钟”和“秒”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-163">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="c46fc-164">请注意，第一个框中允许的最大数是“100”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-164">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                     <span data-ttu-id="c46fc-165">在 **“开始时间”** 框中，输入开始运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-165">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="c46fc-166">在 **“结束时间”** 框中，输入停止重复作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-166">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="c46fc-167">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="c46fc-167">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            3.  <span data-ttu-id="c46fc-168">在 **“持续时间”** 下的 **“开始日期”** 中，输入希望作业计划开始运行的日期。</span><span class="sxs-lookup"><span data-stu-id="c46fc-168">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="c46fc-169">选择 **“结束日期”** 或 **“无结束日期”** 以指示作业计划应在何时停止运行。</span><span class="sxs-lookup"><span data-stu-id="c46fc-169">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="c46fc-170">如果选择 **“结束日期”** ，输入希望作业计划停止运行的日期。</span><span class="sxs-lookup"><span data-stu-id="c46fc-170">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
        5.  <span data-ttu-id="c46fc-171">如果选择“执行一次”，请在“执行一次”下的“日期”框中输入将运行作业计划的日期。</span><span class="sxs-lookup"><span data-stu-id="c46fc-171">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="c46fc-172">在 **“时间”** 框中，输入将运行作业计划的时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-172">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="c46fc-173">输入当天的小时、分钟和秒以及 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="c46fc-173">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        6.  <span data-ttu-id="c46fc-174">在 **“摘要”** 下的 **“说明”** 中，验证所有作业计划设置均正确。</span><span class="sxs-lookup"><span data-stu-id="c46fc-174">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
        7.  <span data-ttu-id="c46fc-175">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-175">Click **OK**.</span></span>  
  
    6.  <span data-ttu-id="c46fc-176">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-176">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="c46fc-177">在 **“选择目标服务器”** 页上，选择要运行维护计划的服务器。</span><span class="sxs-lookup"><span data-stu-id="c46fc-177">On the **Select Target Servers** page, select the servers where you want to run the maintenance plan.</span></span> <span data-ttu-id="c46fc-178">此页仅在配置为主服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上可见。</span><span class="sxs-lookup"><span data-stu-id="c46fc-178">This page is only visible on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances that are configured as master servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c46fc-179">若要创建多服务器维护计划，必须配置包含一台主服务器和一台或多台目标服务器的多服务器环境，并且应将本地服务器配置为主服务器。</span><span class="sxs-lookup"><span data-stu-id="c46fc-179">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured, and the local server should be configured as a master server.</span></span> <span data-ttu-id="c46fc-180">在多服务器环境中，此页显示“(本地)”主服务器和所有相应的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="c46fc-180">In multiserver environments, this page displays the **(local)** master server and all corresponding target servers.</span></span>  
  
7.  <span data-ttu-id="c46fc-181">在 **“选择维护任务”** 页上，选择一个或多个要添加到该计划中的维护任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-181">On the **Select Maintenance Tasks** page, select one or more maintenance tasks to add to the plan.</span></span> <span data-ttu-id="c46fc-182">当您已选择所有必要的任务时，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-182">When you have selected all of the necessary tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c46fc-183">你在此处选择的任务将确定在“选择维护任务顺序”\*\*\*\* 页之后将需要完成的页。</span><span class="sxs-lookup"><span data-stu-id="c46fc-183">The tasks you select here will determine which pages you will need to complete after the **Select Maintenance Task Order** page below.</span></span>  
  
8.  <span data-ttu-id="c46fc-184">在“选择维护任务顺序”页上，选择一个任务，然后单击“上移…”或“下移…”以更改其执行顺序  。</span><span class="sxs-lookup"><span data-stu-id="c46fc-184">On the **Select Maintenance Task Order** page, select a task and click either **Move Up...** or **Move Down...** to change its order of execution.</span></span> <span data-ttu-id="c46fc-185">完成操作后，或如果您对当前任务的顺序感到满意时，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-185">When finished, or if you are satisfied with the current order of tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c46fc-186">如果你在上面的“选择计划属性”\*\*\*\* 页中选择了“每项任务单独计划”\*\*\*\*，则无法在此页上更改维护任务的顺序。</span><span class="sxs-lookup"><span data-stu-id="c46fc-186">If you selected **Separate schedules for each task** on the **Select Plan Properties** page above, you will not be able to change the order of the maintenance tasks on this page.</span></span>  
  
#### <a name="define-database-check-integrity-checkdb-tasks"></a><span data-ttu-id="c46fc-187">定义数据库检查完整性 (CHECKDB) 任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-187">Define Database Check Integrity (CHECKDB) Tasks</span></span>  
  
1.  <span data-ttu-id="c46fc-188">在 **“定义数据库检查完整性任务”** 页中，选择将检查用户和系统表以及索引的分配和结构完整性的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-188">On the **Define Database Check Integrity Task** page, choose the database or databases where the allocation and structural integrity of user and system tables and indexes will be checked.</span></span> <span data-ttu-id="c46fc-189">通过运行 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，该任务可确保报告数据库中存在的所有完整性问题，以便系统管理员或数据库所有者能够在以后加以解决。</span><span class="sxs-lookup"><span data-stu-id="c46fc-189">By running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement, this task ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span> <span data-ttu-id="c46fc-190">有关详细信息，请参阅[DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)。完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-190">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-191">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-191">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-192">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-192">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-193">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-193">Specify the databases affected by this task.</span></span>  
  
    -   <span data-ttu-id="c46fc-194">**“所有数据库”**</span><span class="sxs-lookup"><span data-stu-id="c46fc-194">**All databases**</span></span>  
  
         <span data-ttu-id="c46fc-195">生成对所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库（“tempdb”除外）运行此任务的维护计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-195">Generate a maintenance plan that runs this task against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
    -   <span data-ttu-id="c46fc-196">**系统数据库**</span><span class="sxs-lookup"><span data-stu-id="c46fc-196">**System databases**</span></span>  
  
         <span data-ttu-id="c46fc-197">生成的维护计划将对除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tempdb **和用户创建的数据库之外的** 系统数据库运行此任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-197">Generate a maintenance plan that runs this task against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb** and user-created databases.</span></span>  
  
    -   <span data-ttu-id="c46fc-198">**所有用户数据库(master、model、msdb、tempdb 除外)**</span><span class="sxs-lookup"><span data-stu-id="c46fc-198">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
  
         <span data-ttu-id="c46fc-199">生成的维护计划将对用户创建的所有数据库运行此任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-199">Generate a maintenance plan that runs this task against all user-created databases.</span></span> <span data-ttu-id="c46fc-200">但不会对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统数据库运行任何维护任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-200">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
    -   <span data-ttu-id="c46fc-201">**以下数据库**</span><span class="sxs-lookup"><span data-stu-id="c46fc-201">**These databases**</span></span>  
  
         <span data-ttu-id="c46fc-202">生成的维护计划只对所选数据库运行此任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-202">Generate a maintenance plan that runs this task against only those databases that are selected.</span></span> <span data-ttu-id="c46fc-203">如果选择此选项，则必须至少在列表中选择一个数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-203">At least one database in the list must be selected if this option is chosen.</span></span>  
  
     <span data-ttu-id="c46fc-204">“包含索引”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-204">**Include indexes** check box</span></span>  
     <span data-ttu-id="c46fc-205">检查所有索引页以及表数据页的完整性。</span><span class="sxs-lookup"><span data-stu-id="c46fc-205">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
#### <a name="define-database-shrink-tasks"></a><span data-ttu-id="c46fc-206">定义数据库收缩任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-206">Define Database Shrink Tasks</span></span>  
  
1.  <span data-ttu-id="c46fc-207">在 **“定义收缩数据库任务”** 页上，使用 `DBCC SHRINKDATABASE` 语句以及 `NOTRUNCATE` 或 `TRUNCATEONLY` 选项，可以创建一个任务，以尝试减小所选数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="c46fc-207">On the **Define Shrink Database Task** page, create a task that attempts to reduce the size of the selected databases by using the `DBCC SHRINKDATABASE` statement, with either the `NOTRUNCATE` or `TRUNCATEONLY` option.</span></span> <span data-ttu-id="c46fc-208">有关详细信息，请参阅 [DBCC SHRINKDATABASE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-208">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span> <span data-ttu-id="c46fc-209">完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-209">When complete, click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c46fc-210">被移动用来收缩文件的数据可以分布到文件的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="c46fc-210">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="c46fc-211">这将导致索引碎片并使搜索索引范围的查询变慢。</span><span class="sxs-lookup"><span data-stu-id="c46fc-211">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="c46fc-212">若要消除碎片，请考虑在收缩后重新生成文件的索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-212">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
     <span data-ttu-id="c46fc-213">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-213">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-214">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-214">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-215">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-215">Specify the databases affected by this task.</span></span> <span data-ttu-id="c46fc-216">有关此列表上可用选项的详细信息，请参阅上述步骤 9。</span><span class="sxs-lookup"><span data-stu-id="c46fc-216">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="c46fc-217">“当数据库大小超过指定值时收缩数据库”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-217">**Shrink database when it grows beyond** box</span></span>  
     <span data-ttu-id="c46fc-218">指定引发此任务的数据库大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-218">Specify the size in megabytes that causes the task to execute.</span></span>  
  
     <span data-ttu-id="c46fc-219">“收缩后保留的可用空间”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-219">**Amount of free space to remain after shrink** box</span></span>  
     <span data-ttu-id="c46fc-220">当数据库文件中的可用空间达到此值时停止收缩（以百分比表示）。</span><span class="sxs-lookup"><span data-stu-id="c46fc-220">Stop shrinking when free space in database files reaches this size (as a percentage).</span></span>  
  
     <span data-ttu-id="c46fc-221">**将释放的空间保留在数据库文件中**</span><span class="sxs-lookup"><span data-stu-id="c46fc-221">**Retain freed space in database files**</span></span>  
     <span data-ttu-id="c46fc-222">将数据库精简为连续页，但不释放这些页，因此数据库文件不会收缩。</span><span class="sxs-lookup"><span data-stu-id="c46fc-222">The database is condensed to contiguous pages but the pages are not deallocated, and the database files do not shrink.</span></span> <span data-ttu-id="c46fc-223">如果希望数据库再次扩大，但不希望重新分配空间，则使用此选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-223">Use this option if you expect the database to expand again, and you do not want to reallocate space.</span></span> <span data-ttu-id="c46fc-224">使用此选项时，数据库文件不会尽可能地收缩。</span><span class="sxs-lookup"><span data-stu-id="c46fc-224">With this option, the database files do not shrink as much as possible.</span></span> <span data-ttu-id="c46fc-225">这将使用 NOTRUNCATE 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-225">This uses the NOTRUNCATE option.</span></span>  
  
     <span data-ttu-id="c46fc-226">**将释放的空间归还给操作系统**</span><span class="sxs-lookup"><span data-stu-id="c46fc-226">**Return freed space to operating system**</span></span>  
     <span data-ttu-id="c46fc-227">将数据库精简为连续页，并将这些页释放回操作系统，以供其他程序使用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-227">The database is condensed to contiguous pages and the pages are released back to the operating system for use by other programs.</span></span> <span data-ttu-id="c46fc-228">此数据库文件将尽可能地收缩。</span><span class="sxs-lookup"><span data-stu-id="c46fc-228">This database files shrink as much as possible.</span></span> <span data-ttu-id="c46fc-229">这将使用 TRUNCATEONLY 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-229">This uses the TRUNCATEONLY option.</span></span> <span data-ttu-id="c46fc-230">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-230">This is the default option.</span></span>  
  
#### <a name="define-the-index-tasks"></a><span data-ttu-id="c46fc-231">定义索引任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-231">Define the Index Tasks</span></span>  
  
1.  <span data-ttu-id="c46fc-232">在 **“定义重新组织索引任务”** 页上，选择用来移动索引页以提高搜索顺序效率的服务器。</span><span class="sxs-lookup"><span data-stu-id="c46fc-232">On the **Define Reorganize Index Task** page, select the server or servers where you'll be moving index pages into a more efficient search order.</span></span> <span data-ttu-id="c46fc-233">此任务使用 `ALTER INDEX ... REORGANIZE` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-233">This task uses the `ALTER INDEX ... REORGANIZE` statement.</span></span> <span data-ttu-id="c46fc-234">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-234">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span> <span data-ttu-id="c46fc-235">完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-235">When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-236">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-236">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-237">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-237">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-238">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-238">Specify the databases affected by this task.</span></span> <span data-ttu-id="c46fc-239">有关此列表上可用选项的详细信息，请参阅上述步骤 9。</span><span class="sxs-lookup"><span data-stu-id="c46fc-239">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="c46fc-240">“对象”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-240">**Object** list</span></span>  
     <span data-ttu-id="c46fc-241">将“选择”列表限制为显示表、视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="c46fc-241">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="c46fc-242">仅当从上面的 **“数据库”** 列表中选中单个数据库时，该列表才可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-242">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="c46fc-243">“选择”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-243">**Selection** list</span></span>  
     <span data-ttu-id="c46fc-244">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-244">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="c46fc-245">在“对象”框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-245">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="c46fc-246">“压缩大型对象”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-246">**Compact large objects** check box</span></span>  
     <span data-ttu-id="c46fc-247">在可能的情况下，释放表和视图的空间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-247">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="c46fc-248">此选项使用 `ALTER INDEX ... LOB_COMPACTION = ON`。</span><span class="sxs-lookup"><span data-stu-id="c46fc-248">This option uses `ALTER INDEX ... LOB_COMPACTION = ON`.</span></span>  
  
2.  <span data-ttu-id="c46fc-249">在“定义重新生成索引任务”页上，选择你将重新创建多个索引的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-249">On the **Define Rebuild Index Task** page, select the database or databases where you'll be re-creating multiple indexes.</span></span> <span data-ttu-id="c46fc-250">此任务使用 `ALTER INDEX ... REBUILD PARTITION` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-250">This task uses the `ALTER INDEX ... REBUILD PARTITION` statement.</span></span> <span data-ttu-id="c46fc-251">有关详细信息，请参阅 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。）完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-251">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).) When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-252">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-252">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-253">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-253">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-254">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-254">Specify the databases affected by this task.</span></span> <span data-ttu-id="c46fc-255">有关此列表上可用选项的详细信息，请参阅上述步骤 9。</span><span class="sxs-lookup"><span data-stu-id="c46fc-255">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="c46fc-256">“对象”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-256">**Object** list</span></span>  
     <span data-ttu-id="c46fc-257">将“选择”列表限制为显示表、视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="c46fc-257">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="c46fc-258">仅当从上面的 **“数据库”** 列表中选中单个数据库时，该列表才可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-258">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="c46fc-259">“选择”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-259">**Selection** list</span></span>  
     <span data-ttu-id="c46fc-260">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-260">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="c46fc-261">在“对象”框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-261">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="c46fc-262">“可用空间选项”区域</span><span class="sxs-lookup"><span data-stu-id="c46fc-262">**Free space options** area</span></span>  
     <span data-ttu-id="c46fc-263">提供了用于将填充因子应用到索引和表的选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-263">Presents options for applying fill factor to indexes and tables.</span></span>  
  
     <span data-ttu-id="c46fc-264">**每页的默认可用空间**</span><span class="sxs-lookup"><span data-stu-id="c46fc-264">**Default free space per page**</span></span>  
     <span data-ttu-id="c46fc-265">使用默认可用空间重新组织页。</span><span class="sxs-lookup"><span data-stu-id="c46fc-265">Reorganizes the pages with the default amount of free space.</span></span> <span data-ttu-id="c46fc-266">这将删除数据库中表上的索引，并使用在创建索引时指定的填充因子重新创建索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-266">This will drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span> <span data-ttu-id="c46fc-267">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-267">This is the default option.</span></span>  
  
     <span data-ttu-id="c46fc-268">“将每页可用空间更改为”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-268">**Change free space per page to** box</span></span>  
     <span data-ttu-id="c46fc-269">删除数据库中表上的索引，并使用新的、自动计算的填充因子重新创建索引，从而在索引页上保留指定的可用空间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-269">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="c46fc-270">百分比越高，索引页上保留的可用空间就越多，并且索引增长也就越大。</span><span class="sxs-lookup"><span data-stu-id="c46fc-270">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="c46fc-271">有效值为 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="c46fc-271">Valid values are from 0 through 100.</span></span> <span data-ttu-id="c46fc-272">使用 `FILLFACTOR` 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-272">Uses the `FILLFACTOR` option.</span></span>  
  
     <span data-ttu-id="c46fc-273">“高级选项”区域</span><span class="sxs-lookup"><span data-stu-id="c46fc-273">**Advanced options** area</span></span>  
     <span data-ttu-id="c46fc-274">提供用于排序索引和重建索引的其他选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-274">Presents additional options for sorting indexes and reindexing.</span></span>  
  
     <span data-ttu-id="c46fc-275">“对 tempdb 中的结果进行排序”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-275">**Sort results in tempdb** check box</span></span>  
     <span data-ttu-id="c46fc-276">使用 `SORT_IN_TEMPDB` 选项，该选项确定在索引创建过程中生成的中间排序结果的临时存储位置。</span><span class="sxs-lookup"><span data-stu-id="c46fc-276">Uses the `SORT_IN_TEMPDB` option which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="c46fc-277">如果不需要执行排序操作，或者可以在内存中执行排序，则忽略 `SORT_IN_TEMPDB` 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-277">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB` option is ignored.</span></span>  
  
     <span data-ttu-id="c46fc-278">“重建索引时保持索引联机”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-278">**Keep index online while reindexing** check box</span></span>  
     <span data-ttu-id="c46fc-279">使用 `ONLINE` 选项，用户可以在索引操作期间访问基础表或聚集索引数据以及任何关联的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-279">Uses the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span> <span data-ttu-id="c46fc-280">选择此选项将激活用于重新生成不允许联机重新生成的索引的其他选项：“不重新生成索引”和“脱机重新生成索引” 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-280">Selecting this option activates additional options for rebuilding indexes that do not allow for online rebuilds: **Do not rebuild indexes** and **Rebuild indexes offline**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c46fc-281">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的各版本中均不提供联机索引操作。</span><span class="sxs-lookup"><span data-stu-id="c46fc-281">Online index operations are not available in every edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c46fc-282">有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-282">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
#### <a name="define-the-update-statistics-task"></a><span data-ttu-id="c46fc-283">定义更新统计信息任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-283">Define the Update Statistics Task</span></span>  
  
1.  <span data-ttu-id="c46fc-284">在 **“定义更新统计信息任务”** 页上，定义将对其进行更新表和索引统计信息的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-284">On the **Define Update Statistics Task** page, define the database or databases on which table and index statistics will be updated.</span></span> <span data-ttu-id="c46fc-285">此任务使用 `UPDATE STATISTICS` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-285">This task uses the `UPDATE STATISTICS` statement.</span></span> <span data-ttu-id="c46fc-286">有关详细信息，请参阅 [更新统计信息 (Transact-SQL)](/sql/t-sql/statements/update-statistics-transact-sql)。完成后，单击“下一步”</span><span class="sxs-lookup"><span data-stu-id="c46fc-286">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) When finished, click **Next**</span></span>  
  
     <span data-ttu-id="c46fc-287">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-287">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-288">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-288">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-289">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-289">Specify the databases affected by this task.</span></span> <span data-ttu-id="c46fc-290">有关此列表上可用选项的详细信息，请参阅上述步骤 9。</span><span class="sxs-lookup"><span data-stu-id="c46fc-290">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="c46fc-291">“对象”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-291">**Object** list</span></span>  
     <span data-ttu-id="c46fc-292">将“选择”列表限制为显示表、视图或同时显示两者。</span><span class="sxs-lookup"><span data-stu-id="c46fc-292">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="c46fc-293">仅当从上面的 **“数据库”** 列表中选中单个数据库时，该列表才可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-293">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="c46fc-294">“选择”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-294">**Selection** list</span></span>  
     <span data-ttu-id="c46fc-295">指定受此任务影响的表或索引。</span><span class="sxs-lookup"><span data-stu-id="c46fc-295">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="c46fc-296">在“对象”框中选择 **“表和视图”** 时不可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-296">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="c46fc-297">**所有现有统计信息**</span><span class="sxs-lookup"><span data-stu-id="c46fc-297">**All existing statistics**</span></span>  
     <span data-ttu-id="c46fc-298">同时更新列和索引的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-298">Update statistics for both columns and indexes.</span></span>  
  
     <span data-ttu-id="c46fc-299">**仅限列统计信息**</span><span class="sxs-lookup"><span data-stu-id="c46fc-299">**Column statistics only**</span></span>  
     <span data-ttu-id="c46fc-300">仅更新列统计信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-300">Only update column statistics.</span></span> <span data-ttu-id="c46fc-301">使用 `WITH COLUMNS` 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-301">Uses the `WITH COLUMNS` option.</span></span>  
  
     <span data-ttu-id="c46fc-302">**仅限索引统计信息**</span><span class="sxs-lookup"><span data-stu-id="c46fc-302">**Index statistics only**</span></span>  
     <span data-ttu-id="c46fc-303">仅更新索引统计信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-303">Only update index statistics.</span></span> <span data-ttu-id="c46fc-304">使用 `WITH INDEX` 选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-304">Uses the `WITH INDEX` option.</span></span>  
  
     <span data-ttu-id="c46fc-305">**扫描类型**</span><span class="sxs-lookup"><span data-stu-id="c46fc-305">**Scan type**</span></span>  
     <span data-ttu-id="c46fc-306">用于收集已更新统计信息的扫描的类型。</span><span class="sxs-lookup"><span data-stu-id="c46fc-306">Type of scan used to gather updated statistics.</span></span>  
  
     <span data-ttu-id="c46fc-307">**完全扫描**</span><span class="sxs-lookup"><span data-stu-id="c46fc-307">**Full scan**</span></span>  
     <span data-ttu-id="c46fc-308">读取表或视图中的所有行来收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-308">Read all rows in the table or view to gather the statistics.</span></span>  
  
     <span data-ttu-id="c46fc-309">**抽样依据**</span><span class="sxs-lookup"><span data-stu-id="c46fc-309">**Sample by**</span></span>  
     <span data-ttu-id="c46fc-310">指定在收集较大型的表或视图的统计信息时要抽样的表或索引视图的百分比或者行数。</span><span class="sxs-lookup"><span data-stu-id="c46fc-310">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
#### <a name="define-the-history-cleanup-task"></a><span data-ttu-id="c46fc-311">定义清除历史记录任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-311">Define the History Cleanup Task</span></span>  
  
1.  <span data-ttu-id="c46fc-312">在 **“定义清除历史记录任务”** 页上，选择您要删除旧的任务历史记录的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-312">On the **Define History Cleanup Task** page, define the database or databases where you want to discard old task history.</span></span> <span data-ttu-id="c46fc-313">该任务使用 `EXEC sp_purge_jobhistory`、 `EXEC sp_maintplan_delete_log`和 `EXEC sp_delete_backuphistory` 语句从 **msdb** 表中删除历史记录信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-313">This task uses the `EXEC sp_purge_jobhistory`, `EXEC sp_maintplan_delete_log`, and `EXEC sp_delete_backuphistory` statements to remove history information from the **msdb** tables.</span></span> <span data-ttu-id="c46fc-314">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-314">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-315">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-315">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-316">**选择要删除的历史数据**</span><span class="sxs-lookup"><span data-stu-id="c46fc-316">**Select the historical data to delete**</span></span>  
     <span data-ttu-id="c46fc-317">选中要删除的任务数据的类型</span><span class="sxs-lookup"><span data-stu-id="c46fc-317">Chose the type of task data to delete/</span></span>  
  
     <span data-ttu-id="c46fc-318">**备份和还原历史记录**</span><span class="sxs-lookup"><span data-stu-id="c46fc-318">**Backup and restore history**</span></span>  
     <span data-ttu-id="c46fc-319">当您希望还原数据库时，保留有关最近备份创建时间的记录可帮助 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建恢复计划。</span><span class="sxs-lookup"><span data-stu-id="c46fc-319">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="c46fc-320">保留期应当至少为完整数据库备份的频率。</span><span class="sxs-lookup"><span data-stu-id="c46fc-320">The retention period should be at least the frequency of full database backups.</span></span>  
  
     <span data-ttu-id="c46fc-321">**SQL Server 代理作业历史记录**</span><span class="sxs-lookup"><span data-stu-id="c46fc-321">**SQL Server Agent Job history**</span></span>  
     <span data-ttu-id="c46fc-322">使用此历史记录有助于排除失败作业的故障，或者确定数据库操作发生的原因。</span><span class="sxs-lookup"><span data-stu-id="c46fc-322">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="c46fc-323">**维护计划历史记录**</span><span class="sxs-lookup"><span data-stu-id="c46fc-323">**Maintenance Plan history**</span></span>  
     <span data-ttu-id="c46fc-324">使用此历史记录有助于排除失败的维护计划作业的故障，或者确定数据库操作发生的原因。</span><span class="sxs-lookup"><span data-stu-id="c46fc-324">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="c46fc-325">**删除历史数据，如果其保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="c46fc-325">**Remove historical data older than**</span></span>  
     <span data-ttu-id="c46fc-326">指定要删除项的保留时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-326">Specify age of items that you want to delete.</span></span> <span data-ttu-id="c46fc-327">你可以指定“小时”、“天”、“周”（默认值）、“月”或“年”</span><span class="sxs-lookup"><span data-stu-id="c46fc-327">You can specify **Hour(s)**, **Day(s)**, **Week(s)** (the default), **Month(s)**, or **Year(s)**</span></span>  
  
#### <a name="define-the-execute-agent-job-task"></a><span data-ttu-id="c46fc-328">定义执行代理作业任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-328">Define the Execute Agent Job Task</span></span>  
  
1.  <span data-ttu-id="c46fc-329">在 **“定义执行代理作业任务”** 页的 **“可用的 SQL Server 代理作业”** 下面，选中要运行的作业。</span><span class="sxs-lookup"><span data-stu-id="c46fc-329">On the **Define Execute Agent Job Task** page, under **Available SQL Server Agent jobs**, choose the job or jobs to run.</span></span> <span data-ttu-id="c46fc-330">如果没有 SQL 代理作业，此选项将不可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-330">This option will not be available if you have no SQL Agent jobs.</span></span> <span data-ttu-id="c46fc-331">此任务使用 `EXEC sp_start_job` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-331">This task uses the `EXEC sp_start_job` statement.</span></span> <span data-ttu-id="c46fc-332">有关详细信息，请参阅 [sp_start_job (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-332">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)When finished, click **Next**.</span></span>  
  
#### <a name="define-backup-tasks"></a><span data-ttu-id="c46fc-333">定义备份任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-333">Define Backup Tasks</span></span>  
  
1.  <span data-ttu-id="c46fc-334">在“定义备份数据库（完整）任务”页上，选择要对其运行完整备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-334">On the **Define Backup Database (Full) Task** page, select the database or databases on which to run a full backup.</span></span> <span data-ttu-id="c46fc-335">此任务使用 `BACKUP DATABASE` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-335">This task uses the `BACKUP DATABASE` statement.</span></span> <span data-ttu-id="c46fc-336">有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-336">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="c46fc-337">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-337">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-338">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-338">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-339">“备份类型”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-339">**Backup type** list</span></span>  
     <span data-ttu-id="c46fc-340">显示要执行的备份类型。</span><span class="sxs-lookup"><span data-stu-id="c46fc-340">Displays the type of backup to be performed.</span></span> <span data-ttu-id="c46fc-341">这是只读的。</span><span class="sxs-lookup"><span data-stu-id="c46fc-341">This is read-only.</span></span>  
  
     <span data-ttu-id="c46fc-342">“数据库”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-342">**Databases** list</span></span>  
     <span data-ttu-id="c46fc-343">指定受此任务影响的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-343">Specify the databases affected by this task.</span></span> <span data-ttu-id="c46fc-344">有关此列表上可用选项的详细信息，请参阅上述步骤 9。</span><span class="sxs-lookup"><span data-stu-id="c46fc-344">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="c46fc-345">**备份组件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-345">**Backup component**</span></span>  
     <span data-ttu-id="c46fc-346">选择“数据库”将备份整个数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-346">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="c46fc-347">选择 **“文件和文件组”** 将只备份部分数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-347">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="c46fc-348">如果选择此选项，请提供文件或文件组名称。</span><span class="sxs-lookup"><span data-stu-id="c46fc-348">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="c46fc-349">如果在 **“数据库”** 框中选择了多个数据库，只能对 **“备份组件”** 指定 **“数据库”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-349">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="c46fc-350">若要执行文件或文件组备份，请为每个数据库创建一个任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-350">To perform file or filegroup backups, create a task for each database.</span></span> <span data-ttu-id="c46fc-351">仅当选中上述 **“数据库”** 列表中的单个数据库时，这些选项才可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-351">These options are only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="c46fc-352">“备份集过期时间”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-352">**Backup set will expire** check box</span></span>  
     <span data-ttu-id="c46fc-353">指定允许覆盖该备份的备份集的日期。</span><span class="sxs-lookup"><span data-stu-id="c46fc-353">Specifies when the backup set for this backup can be overwritten.</span></span> <span data-ttu-id="c46fc-354">选择 **“晚于”** ，然后输入过期前的天数，或选择 **“在”** ，然后输入过期日期。</span><span class="sxs-lookup"><span data-stu-id="c46fc-354">Select **After** and enter a number of days to expiration, or select **On** and enter a date of expiration.</span></span> <span data-ttu-id="c46fc-355">如果选择 **URL** 作为备份目标，则禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-355">This option is disabled if **URL** is selected as the backup destination.</span></span>  
  
     <span data-ttu-id="c46fc-356">**备份到**</span><span class="sxs-lookup"><span data-stu-id="c46fc-356">**Back up to**</span></span>  
     <span data-ttu-id="c46fc-357">指定要将数据库备份到的介质。</span><span class="sxs-lookup"><span data-stu-id="c46fc-357">Specifies the medium on which to back up the database.</span></span> <span data-ttu-id="c46fc-358">选择 **“磁盘”** 、 **“磁带”** 或 **URL**。</span><span class="sxs-lookup"><span data-stu-id="c46fc-358">Select **Disk**, **Tape**, or **URL**.</span></span> <span data-ttu-id="c46fc-359">只有连接到该数据库所在计算机的磁带设备才可用。</span><span class="sxs-lookup"><span data-stu-id="c46fc-359">Only tape devices attached to the computer containing the database are available.</span></span>  
  
     <span data-ttu-id="c46fc-360">**跨一个或多个文件备份数据库**</span><span class="sxs-lookup"><span data-stu-id="c46fc-360">**Back up database(s) across one or more files**</span></span>  
     <span data-ttu-id="c46fc-361">单击“添加”可以打开“选择备份目标”对话框。</span><span class="sxs-lookup"><span data-stu-id="c46fc-361">Click **Add** to open the **Select Backup Destination** dialog box.</span></span> <span data-ttu-id="c46fc-362">如果选择 URL 作为备份目标，则禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-362">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="c46fc-363">单击 **“删除”** 将文件从该框中删除。</span><span class="sxs-lookup"><span data-stu-id="c46fc-363">Click **Remove** to remove a file from the box.</span></span>  
  
     <span data-ttu-id="c46fc-364">单击 **“内容”** 将读取文件头，并显示此文件的当前备份内容。</span><span class="sxs-lookup"><span data-stu-id="c46fc-364">Click **Contents** to read the file header and display the current backup contents of the file.</span></span>  
  
     <span data-ttu-id="c46fc-365">“选择备份目标”对话框</span><span class="sxs-lookup"><span data-stu-id="c46fc-365">**Select Backup Destination** dialog box</span></span>  
     <span data-ttu-id="c46fc-366">选择拥有备份目标的文件、磁带机或备份设备。</span><span class="sxs-lookup"><span data-stu-id="c46fc-366">Select the file, tape drive, or backup device for the backup destination.</span></span> <span data-ttu-id="c46fc-367">如果选择 URL 作为备份目标，则禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-367">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="c46fc-368">“如果备份文件存在”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-368">**If backup files exist** list</span></span>  
     <span data-ttu-id="c46fc-369">指定如何处理现有备份。</span><span class="sxs-lookup"><span data-stu-id="c46fc-369">Specify how to handle existing backups.</span></span> <span data-ttu-id="c46fc-370">选择 **“追加”** 将新备份添加到文件或磁带中的所有现有备份之后。</span><span class="sxs-lookup"><span data-stu-id="c46fc-370">Select **Append** to add the new backups after any existing backups in the file or on the tape.</span></span> <span data-ttu-id="c46fc-371">选择 **“覆盖”** 将删除文件或磁带中的旧内容，并将其替换为新备份。</span><span class="sxs-lookup"><span data-stu-id="c46fc-371">Select **Overwrite** to remove the old content of a file or tape, and replace it with this new backup.</span></span>  
  
     <span data-ttu-id="c46fc-372">**为每个数据库创建备份文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-372">**Create a backup file for every database**</span></span>  
     <span data-ttu-id="c46fc-373">在文件夹框中指定的位置创建一个备份文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-373">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="c46fc-374">为选定的每个数据库创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-374">One file is created for each database selected.</span></span> <span data-ttu-id="c46fc-375">如果选择 URL 作为备份目标，则禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-375">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="c46fc-376">“为每个数据库创建子目录”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-376">**Create a sub-directory for each database** check box</span></span>  
     <span data-ttu-id="c46fc-377">在指定磁盘目录下创建一个子目录，指定的磁盘目录包含维护计划中要备份的每一个数据库的数据库备份。</span><span class="sxs-lookup"><span data-stu-id="c46fc-377">Create a sub-directory under the specified disk directory that contains the database backup for each database being backed up as part of the maintenance plan.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c46fc-378">子目录将从父目录继承权限。</span><span class="sxs-lookup"><span data-stu-id="c46fc-378">The sub-directory will inherit permissions from the parent directory.</span></span> <span data-ttu-id="c46fc-379">请限制相关权限，以避免未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="c46fc-379">Restrict permissions to avoid unauthorized access.</span></span>  
  
     <span data-ttu-id="c46fc-380">“文件夹”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-380">**Folder** box</span></span>  
     <span data-ttu-id="c46fc-381">指定用来放置自动创建的数据库文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c46fc-381">Specify the folder to contain the automatically created database files.</span></span> <span data-ttu-id="c46fc-382">如果选择 URL 作为备份目标，则禁用该选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-382">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="c46fc-383">**SQL 凭据**</span><span class="sxs-lookup"><span data-stu-id="c46fc-383">**SQL Credential**</span></span>  
     <span data-ttu-id="c46fc-384">选择可用于对 Azure 存储进行身份验证的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="c46fc-384">Select a SQL Credential used to authenticate to Azure Storage.</span></span> <span data-ttu-id="c46fc-385">如果没有可使用的现有 SQL 凭据，则单击 **“创建”** 按钮可创建新的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="c46fc-385">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c46fc-386">单击 **“创建”** 打开的对话框需要管理证书或订阅的发布配置文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-386">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="c46fc-387">如果您无权访问管理证书或发布配置文件，可以创建一个 SQL 凭据，方法是使用 Transact-SQL 或 SQL Server Management Studio 指定存储帐户名称和访问密钥信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-387">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="c46fc-388">请参阅中的示例代码，以[创建凭据](../security/authentication-access/create-a-credential.md#Credential)主题，以便使用 transact-sql 创建凭据。</span><span class="sxs-lookup"><span data-stu-id="c46fc-388">See the sample code in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="c46fc-389">或者，使用 SQL Server Management Studio，从数据库引擎实例中右键单击 **“安全性”**，依次选择 **“新建”** 和 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="c46fc-389">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="c46fc-390">在 **“标识”** 字段中指定存储帐户名称，在 **“密码”** 字段中指定访问密钥。</span><span class="sxs-lookup"><span data-stu-id="c46fc-390">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
     <span data-ttu-id="c46fc-391">**Azure 存储容器**</span><span class="sxs-lookup"><span data-stu-id="c46fc-391">**Azure storage container**</span></span>  
     <span data-ttu-id="c46fc-392">指定 Azure 存储容器的名称</span><span class="sxs-lookup"><span data-stu-id="c46fc-392">Specify the name of the Azure storage container</span></span>  
  
     <span data-ttu-id="c46fc-393">**URL 前缀：**</span><span class="sxs-lookup"><span data-stu-id="c46fc-393">**URL prefix:**</span></span>  
     <span data-ttu-id="c46fc-394">这是基于在 SQL 凭据中存储的存储帐户信息以及您指定的 Azure 存储容器名称自动生成的。</span><span class="sxs-lookup"><span data-stu-id="c46fc-394">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="c46fc-395">建议不要编辑此字段中的信息，除非使用的域采用 **\<storage account>.blob.core.windows.net** 以外的格式。</span><span class="sxs-lookup"><span data-stu-id="c46fc-395">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
     <span data-ttu-id="c46fc-396">“备份文件扩展名”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-396">**Backup file extension** box</span></span>  
     <span data-ttu-id="c46fc-397">指定备份文件要使用的扩展名。</span><span class="sxs-lookup"><span data-stu-id="c46fc-397">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="c46fc-398">默认为 .bak。</span><span class="sxs-lookup"><span data-stu-id="c46fc-398">The default is .bak.</span></span>  
  
     <span data-ttu-id="c46fc-399">“验证备份完整性”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-399">**Verify backup integrity** check box</span></span>  
     <span data-ttu-id="c46fc-400">验证备份集是否完整以及所有卷是否都可读。</span><span class="sxs-lookup"><span data-stu-id="c46fc-400">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
     <span data-ttu-id="c46fc-401">**备份加密**</span><span class="sxs-lookup"><span data-stu-id="c46fc-401">**Backup Encryption**</span></span>  
     <span data-ttu-id="c46fc-402">若要创建加密的备份，请选中 **“加密备份”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="c46fc-402">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="c46fc-403">选择要用于加密步骤的加密算法，然后从现有证书或非对称密钥的列表中提供一个证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="c46fc-403">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="c46fc-404">可用于加密的算法是：</span><span class="sxs-lookup"><span data-stu-id="c46fc-404">The available algorithms for encryption are:</span></span>  
  
    -   <span data-ttu-id="c46fc-405">AES 128</span><span class="sxs-lookup"><span data-stu-id="c46fc-405">AES 128</span></span>  
  
    -   <span data-ttu-id="c46fc-406">AES 192</span><span class="sxs-lookup"><span data-stu-id="c46fc-406">AES 192</span></span>  
  
    -   <span data-ttu-id="c46fc-407">AES 256</span><span class="sxs-lookup"><span data-stu-id="c46fc-407">AES 256</span></span>  
  
    -   <span data-ttu-id="c46fc-408">三重 DES</span><span class="sxs-lookup"><span data-stu-id="c46fc-408">Triple DES</span></span>  
  
     <span data-ttu-id="c46fc-409">如果您选择了追加到现有备份集，则禁用加密选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-409">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
  
     <span data-ttu-id="c46fc-410">建议做法是备份证书或密钥，而存储它们的位置要与所加密的备份不同。</span><span class="sxs-lookup"><span data-stu-id="c46fc-410">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
  
     <span data-ttu-id="c46fc-411">仅支持位于可扩展密钥管理 (EKM) 中的密钥。</span><span class="sxs-lookup"><span data-stu-id="c46fc-411">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
     <span data-ttu-id="c46fc-412">“设置备份压缩”列表</span><span class="sxs-lookup"><span data-stu-id="c46fc-412">**Set backup compression**  list</span></span>  
     <span data-ttu-id="c46fc-413">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] （或更高版本）中，选择以下 [备份压缩](../backup-restore/backup-compression-sql-server.md) 值之一：</span><span class="sxs-lookup"><span data-stu-id="c46fc-413">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="c46fc-414">**使用默认服务器设置**</span><span class="sxs-lookup"><span data-stu-id="c46fc-414">**Use the default server setting**</span></span>|<span data-ttu-id="c46fc-415">单击此选项可使用服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c46fc-415">Click to use the server-level default.</span></span> <span data-ttu-id="c46fc-416">此默认值可通过 **backup compression default** 服务器配置选项进行设置。</span><span class="sxs-lookup"><span data-stu-id="c46fc-416">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="c46fc-417">有关如何查看此选项当前设置的信息，请参阅 [查看或配置 backup compression default 服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-417">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
    |<span data-ttu-id="c46fc-418">**压缩备份**</span><span class="sxs-lookup"><span data-stu-id="c46fc-418">**Compress backup**</span></span>|<span data-ttu-id="c46fc-419">单击此选项可压缩备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c46fc-419">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="c46fc-420">**\*\* 重要说明 \*\*** 默认情况下，压缩会大大提高 CPU 使用率，并且压缩进程占用的额外 CPU 可能会对并发操作造成不利影响。</span><span class="sxs-lookup"><span data-stu-id="c46fc-420">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="c46fc-421">因此，您可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受资源调控器限制。</span><span class="sxs-lookup"><span data-stu-id="c46fc-421">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the Resource Governor.</span></span> <span data-ttu-id="c46fc-422">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="c46fc-422">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
    |<span data-ttu-id="c46fc-423">**不压缩备份**</span><span class="sxs-lookup"><span data-stu-id="c46fc-423">**Do not compress backup**</span></span>|<span data-ttu-id="c46fc-424">单击此选项可创建未压缩的备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="c46fc-424">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
2.  <span data-ttu-id="c46fc-425">在“定义备份数据库（差异）任务”页上，选择要对其运行部分备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-425">On the **Define Backup Database (Differential) Task** page, select the database or databases on which to run a partial backup.</span></span> <span data-ttu-id="c46fc-426">有关此页上可用选项的详细信息，请参阅上述步骤 16 中列出的定义。</span><span class="sxs-lookup"><span data-stu-id="c46fc-426">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="c46fc-427">此任务使用 `BACKUP DATABASE ... WITH DIFFERENTIAL` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-427">This task uses the `BACKUP DATABASE ... WITH DIFFERENTIAL` statement.</span></span> <span data-ttu-id="c46fc-428">有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-428">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  <span data-ttu-id="c46fc-429">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-429">When finished, click **Next**.</span></span>  
  
3.  <span data-ttu-id="c46fc-430">在“定义备份数据库（事务日志）任务”页上，选择要对事务日志运行备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="c46fc-430">On the **Define Backup Database (Transaction Log) Task** page, select the database or databases on which to run a backup for a transaction log.</span></span> <span data-ttu-id="c46fc-431">有关此页上可用选项的详细信息，请参阅上述步骤 16 中列出的定义。</span><span class="sxs-lookup"><span data-stu-id="c46fc-431">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="c46fc-432">此任务使用 `BACKUP LOG` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-432">This task uses the `BACKUP LOG` statement.</span></span> <span data-ttu-id="c46fc-433">有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c46fc-433">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="c46fc-434">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-434">When finished, click **Next**.</span></span>  
  
#### <a name="define-maintenance-cleanup-tasks"></a><span data-ttu-id="c46fc-435">定义清除维护任务</span><span class="sxs-lookup"><span data-stu-id="c46fc-435">Define Maintenance Cleanup Tasks</span></span>  
  
1.  <span data-ttu-id="c46fc-436">在 **“定义清除维护任务”** 页上，指定要作为维护计划的一部分删除的文件类型，包括由维护计划文件和数据库备份文件创建的文本报告。</span><span class="sxs-lookup"><span data-stu-id="c46fc-436">On the **Define Maintenance Cleanup Task** page, specify the types of files to delete as part of the maintenance plan, including text reports created by maintenance plans and database backup files.</span></span> <span data-ttu-id="c46fc-437">此任务使用 `EXEC xp_delete_file` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-437">This task uses the `EXEC xp_delete_file` statement.</span></span> <span data-ttu-id="c46fc-438">完成后，单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-438">When finished, click **Next**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c46fc-439">此任务不会自动删除指定目录的子文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-439">This task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="c46fc-440">此预防措施减少了使用清除维护任务删除文件的恶意攻击的可能性。</span><span class="sxs-lookup"><span data-stu-id="c46fc-440">This precaution reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="c46fc-441">如果要删除一级子文件夹中的文件，必须选择“包括一级子文件夹”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-441">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
     <span data-ttu-id="c46fc-442">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-442">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-443">**删除以下类型的文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-443">**Delete files of the following type**</span></span>  
     <span data-ttu-id="c46fc-444">指定要删除的文件类型。</span><span class="sxs-lookup"><span data-stu-id="c46fc-444">Specify the type of files to be deleted.</span></span>  
  
     <span data-ttu-id="c46fc-445">**备份文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-445">**Backup files**</span></span>  
     <span data-ttu-id="c46fc-446">删除数据库备份文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-446">Delete database backup files.</span></span>  
  
     <span data-ttu-id="c46fc-447">**维护计划文本报告**</span><span class="sxs-lookup"><span data-stu-id="c46fc-447">**Maintenance Plan text reports**</span></span>  
     <span data-ttu-id="c46fc-448">删除以前运行的维护计划的文本报告。</span><span class="sxs-lookup"><span data-stu-id="c46fc-448">Delete text reports of previously run maintenance plans.</span></span>  
  
     <span data-ttu-id="c46fc-449">**文件位置**</span><span class="sxs-lookup"><span data-stu-id="c46fc-449">**File location**</span></span>  
     <span data-ttu-id="c46fc-450">指定要删除的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="c46fc-450">Specify path to files to be deleted.</span></span>  
  
     <span data-ttu-id="c46fc-451">**删除特定文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-451">**Delete specific file**</span></span>  
     <span data-ttu-id="c46fc-452">删除在“文件名”文本框中提供的特定文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-452">Delete the specific file provided in the **File name** text box.</span></span>  
  
     <span data-ttu-id="c46fc-453">**搜索文件夹并根据扩展名删除文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-453">**Search folder and delete files based on an extension**</span></span>  
     <span data-ttu-id="c46fc-454">删除指定文件夹中带有指定扩展名的所有文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-454">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="c46fc-455">使用此选项可一次删除多个文件，例如 Tuesday 文件夹中带有 .bak 扩展名的所有备份文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-455">Use this to delete multiple files at once, such as all backup files in the Tuesday folder with the .bak extension.</span></span>  
  
     <span data-ttu-id="c46fc-456">“文件夹”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-456">**Folder** box</span></span>  
     <span data-ttu-id="c46fc-457">要删除的文件所在的文件夹的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="c46fc-457">Path and name of the folder containing the files to be deleted.</span></span>  
  
     <span data-ttu-id="c46fc-458">“文件扩展名”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-458">**File extension** box</span></span>  
     <span data-ttu-id="c46fc-459">提供要删除的文件的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="c46fc-459">Provide the file extension of the files to be deleted.</span></span> <span data-ttu-id="c46fc-460">若要一次删除多个文件（例如 Tuesday 文件夹中带有 .bak 扩展名的所有备份文件），请指定 .bak。</span><span class="sxs-lookup"><span data-stu-id="c46fc-460">To delete multiple files at one time, like all backup files with the .bak extension in the Tuesday folder, specify .bak.</span></span>  
  
     <span data-ttu-id="c46fc-461">“包含一级子文件夹”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-461">**Include first-level subfolders** check box</span></span>  
     <span data-ttu-id="c46fc-462">从“文件夹”中指定的文件夹下的一级子文件夹中删除具有为“文件扩展名”指定的扩展名的文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-462">Delete files with the extension specified for **File extension** from first-level subfolders under the folder specified in **Folder**.</span></span>  
  
     <span data-ttu-id="c46fc-463">“在任务运行时根据文件保留时间删除文件”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-463">**Delete files based on the age of the file at task run time** check box</span></span>  
     <span data-ttu-id="c46fc-464">通过在“删除文件，如果其保留时间超过”框中提供数字和时间单位，指定将要删除的文件所要保留的最短时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-464">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
     <span data-ttu-id="c46fc-465">**删除文件，如果其保留时间超过**</span><span class="sxs-lookup"><span data-stu-id="c46fc-465">**Delete files older than the following**</span></span>  
     <span data-ttu-id="c46fc-466">通过提供数字和时间单位（“小时”、“天”、“周”、“月”或“年”），指定要删除的文件所保留的最短时间。</span><span class="sxs-lookup"><span data-stu-id="c46fc-466">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (**Hour**, **Day**, **Week**, **Month**, or **Year**).</span></span> <span data-ttu-id="c46fc-467">保留时间长于指定时间长度的文件将被删除。</span><span class="sxs-lookup"><span data-stu-id="c46fc-467">Files older than the time frame specified will be deleted.</span></span>  
  
#### <a name="select-report-options"></a><span data-ttu-id="c46fc-468">选择报告选项</span><span class="sxs-lookup"><span data-stu-id="c46fc-468">Select Report Options</span></span>  
  
1.  <span data-ttu-id="c46fc-469">在 **“选择报告选项”** 页中，选择对维护计划操作报表进行保存或分发的选项。</span><span class="sxs-lookup"><span data-stu-id="c46fc-469">On the **Select Report Options** page, select options for saving or distributing a report of the maintenance plan actions.</span></span> <span data-ttu-id="c46fc-470">此任务使用 `EXEC sp_notify_operator` 语句。</span><span class="sxs-lookup"><span data-stu-id="c46fc-470">This task uses the `EXEC sp_notify_operator` statement.</span></span> <span data-ttu-id="c46fc-471">有关详细信息，请参阅 [sp_notify_operator (Transact SQL)](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)。完成后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-471">For more information, see [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql).When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="c46fc-472">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-472">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c46fc-473">“将报告写入文本文件”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-473">**Write a report to a text file** check box</span></span>  
     <span data-ttu-id="c46fc-474">将报告保存到一个文件中。</span><span class="sxs-lookup"><span data-stu-id="c46fc-474">Save the report in a file.</span></span>  
  
     <span data-ttu-id="c46fc-475">“文件夹位置”框</span><span class="sxs-lookup"><span data-stu-id="c46fc-475">**Folder location** box</span></span>  
     <span data-ttu-id="c46fc-476">指定将要包含报告的文件的位置。</span><span class="sxs-lookup"><span data-stu-id="c46fc-476">Specify the location of the file that will contain the report.</span></span>  
  
     <span data-ttu-id="c46fc-477">“以电子邮件形式发送报告”复选框</span><span class="sxs-lookup"><span data-stu-id="c46fc-477">**E-mail report** check box</span></span>  
     <span data-ttu-id="c46fc-478">任务失败时发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-478">Send an e-mail when a task fails.</span></span> <span data-ttu-id="c46fc-479">你必须在 MSDB 为邮件主机数据库的情况下启用和正确配置数据库邮件，并拥有有效电子邮件地址的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作员，才能使用此任务。</span><span class="sxs-lookup"><span data-stu-id="c46fc-479">To use this task you must have Database Mail enabled and correctly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
     <span data-ttu-id="c46fc-480">**代理操作员**</span><span class="sxs-lookup"><span data-stu-id="c46fc-480">**Agent operator**</span></span>  
     <span data-ttu-id="c46fc-481">指定电子邮件的收件人。</span><span class="sxs-lookup"><span data-stu-id="c46fc-481">Specify the recipient of the e-mail.</span></span>  
  
     <span data-ttu-id="c46fc-482">**邮件配置文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-482">**Mail profile**</span></span>  
     <span data-ttu-id="c46fc-483">指定定义电子邮件发件人的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-483">Specify the profile that defines the sender of the e-mail.</span></span>  
  
#### <a name="complete-the-wizard"></a><span data-ttu-id="c46fc-484">完成该向导</span><span class="sxs-lookup"><span data-stu-id="c46fc-484">Complete the Wizard</span></span>  
  
1.  <span data-ttu-id="c46fc-485">在 **“完成该向导”** 页上，验证在先前页上所做的选择，然后单击 **“完成”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-485">On the **Complete the Wizard** page, verify the choices made on the previous pages, and click **Finish**.</span></span>  
  
2.  <span data-ttu-id="c46fc-486">在 **“维护向导进度”** 页上，监视有关维护计划向导的状态信息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-486">On the **Maintenance Wizard Progress** page, monitor status information about the actions of the Maintenance Plan Wizard.</span></span> <span data-ttu-id="c46fc-487">根据在向导中选择的选项，“进度”页可能会包含一个操作或多个操作。</span><span class="sxs-lookup"><span data-stu-id="c46fc-487">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="c46fc-488">最上面的方框显示向导的总体状态和向导已接收到的状态、错误和警告消息数。</span><span class="sxs-lookup"><span data-stu-id="c46fc-488">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="c46fc-489">**“维护向导进度”** 页上提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="c46fc-489">The following options are available on the **Maintenance Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="c46fc-490">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="c46fc-490">**Details**</span></span>  
     <span data-ttu-id="c46fc-491">提供向导执行的操作所返回的操作、状态和所有消息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-491">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="c46fc-492">**Action**</span><span class="sxs-lookup"><span data-stu-id="c46fc-492">**Action**</span></span>  
     <span data-ttu-id="c46fc-493">指定每个操作的类型和名称。</span><span class="sxs-lookup"><span data-stu-id="c46fc-493">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="c46fc-494">**Status**</span><span class="sxs-lookup"><span data-stu-id="c46fc-494">**Status**</span></span>  
     <span data-ttu-id="c46fc-495">指示向导操作作为一个整体返回的值是“成功”还是“失败”。</span><span class="sxs-lookup"><span data-stu-id="c46fc-495">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="c46fc-496">**消息**</span><span class="sxs-lookup"><span data-stu-id="c46fc-496">**Message**</span></span>  
     <span data-ttu-id="c46fc-497">提供从该进程中返回的任何错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="c46fc-497">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="c46fc-498">**Report**</span><span class="sxs-lookup"><span data-stu-id="c46fc-498">**Report**</span></span>  
     <span data-ttu-id="c46fc-499">创建包含创建分区向导结果的报告。</span><span class="sxs-lookup"><span data-stu-id="c46fc-499">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="c46fc-500">这些选项是 **“查看报告”** 、 **“将报告保存到文件”** 、 **“将报告复制到剪贴板”** 和 **“将报告作为电子邮件发送”** 。</span><span class="sxs-lookup"><span data-stu-id="c46fc-500">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="c46fc-501">**查看报告**</span><span class="sxs-lookup"><span data-stu-id="c46fc-501">**View Report**</span></span>  
     <span data-ttu-id="c46fc-502">打开“查看报告”对话框，其中包含关于创建分区向导进度的文本报告。</span><span class="sxs-lookup"><span data-stu-id="c46fc-502">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="c46fc-503">**将报告保存到文件**</span><span class="sxs-lookup"><span data-stu-id="c46fc-503">**Save Report to File**</span></span>  
     <span data-ttu-id="c46fc-504">打开“将报告另存为”对话框。</span><span class="sxs-lookup"><span data-stu-id="c46fc-504">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="c46fc-505">**将报告复制到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="c46fc-505">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="c46fc-506">将向导的进度报告结果复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="c46fc-506">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="c46fc-507">**“将报告作为电子邮件发送”**</span><span class="sxs-lookup"><span data-stu-id="c46fc-507">**Send Report as Email**</span></span>  
     <span data-ttu-id="c46fc-508">将向导的进度报告结果复制到电子邮件。</span><span class="sxs-lookup"><span data-stu-id="c46fc-508">Copies the results of the wizard's progress report into an email message.</span></span>  
  
  
