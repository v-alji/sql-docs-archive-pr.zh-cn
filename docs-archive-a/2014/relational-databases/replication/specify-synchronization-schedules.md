---
title: 指定同步计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], synchronizing
- scheduling synchronization [SQL Server replication]
- synchronization [SQL Server replication], schedules
- replication [SQL Server], synchronization
ms.assetid: 97f2535b-ec19-4973-823d-bcf3d5aa0216
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d752817f7d620b2c6e5fdc5eeb2178c50c42040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692343"
---
# <a name="specify-synchronization-schedules"></a><span data-ttu-id="86717-102">指定同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-102">Specify Synchronization Schedules</span></span>
  <span data-ttu-id="86717-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定同步计划。</span><span class="sxs-lookup"><span data-stu-id="86717-103">This topic describes how to specify synchronization schedules in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="86717-104">在创建订阅时，可以定义同步计划以控制何时运行订阅的复制代理。</span><span class="sxs-lookup"><span data-stu-id="86717-104">When you create a subscription, you can define a synchronization schedule that controls when the replication agent for the subscription will run.</span></span> <span data-ttu-id="86717-105">如果没有指定计划参数，则订阅将使用默认计划。</span><span class="sxs-lookup"><span data-stu-id="86717-105">If you do not specify scheduling parameters, the subscription will use the default schedule.</span></span>  
  
 <span data-ttu-id="86717-106">订阅由分发代理（对于快照复制和事务复制）或合并代理（对于合并复制）进行同步。</span><span class="sxs-lookup"><span data-stu-id="86717-106">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="86717-107">代理可以连续运行、按需运行或按计划运行。</span><span class="sxs-lookup"><span data-stu-id="86717-107">Agents can run continuously, run on demand, or run on a schedule.</span></span>  
  
 <span data-ttu-id="86717-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="86717-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="86717-109">**指定同步计划，使用：**</span><span class="sxs-lookup"><span data-stu-id="86717-109">**To specify synchronization schedules, using:**</span></span>  
  
     [<span data-ttu-id="86717-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86717-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="86717-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86717-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="86717-112">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="86717-112">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="86717-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86717-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="86717-114">可在新建订阅向导的 **“同步计划”** 页上指定同步计划。</span><span class="sxs-lookup"><span data-stu-id="86717-114">Specify synchronization schedules on the **Synchronization Schedule** page of the New Subscription Wizard.</span></span> <span data-ttu-id="86717-115">有关访问此向导的详细信息，请参阅 [Create a Push Subscription](create-a-push-subscription.md) 和 [Create a Pull Subscription](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-115">For more information about accessing this wizard, see [Create a Push Subscription](create-a-push-subscription.md) and [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="86717-116">在 **“作业计划属性”** 对话框中修改同步计划，该对话框位于 **的** “作业” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 文件夹和复制监视器的代理详细信息窗口中。</span><span class="sxs-lookup"><span data-stu-id="86717-116">Modify synchronization schedules in the **Job Schedule Properties** dialog box, which is available from the **Jobs** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and from the agent details windows in Replication Monitor.</span></span> <span data-ttu-id="86717-117">有关启动复制监视器的信息，请参阅[启动复制监视器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-117">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="86717-118">如果从 **“作业”** 文件夹指定计划，请使用下表确定代理作业的名称。</span><span class="sxs-lookup"><span data-stu-id="86717-118">If you specify schedules from the **Jobs** folder, use the following table to determine the agent job name.</span></span>  
  
|<span data-ttu-id="86717-119">代理</span><span class="sxs-lookup"><span data-stu-id="86717-119">Agent</span></span>|<span data-ttu-id="86717-120">作业名称</span><span class="sxs-lookup"><span data-stu-id="86717-120">Job name</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="86717-121">请求订阅的合并代理</span><span class="sxs-lookup"><span data-stu-id="86717-121">Merge Agent for pull subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<integer>**|  
|<span data-ttu-id="86717-122">推送订阅的合并代理</span><span class="sxs-lookup"><span data-stu-id="86717-122">Merge Agent for push subscriptions</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
|<span data-ttu-id="86717-123">推送订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="86717-123">Distribution Agent for push subscriptions</span></span>|<span data-ttu-id="86717-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86717-124">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>** <sup>1</sup></span></span>|  
|<span data-ttu-id="86717-125">请求订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="86717-125">Distribution Agent for pull subscriptions</span></span>|<span data-ttu-id="86717-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="86717-126">**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<SubscriptionDatabase>-\<GUID>** <sup>2</sup></span></span>|  
|<span data-ttu-id="86717-127">非 SQL Server 订阅服务器的推送订阅的分发代理</span><span class="sxs-lookup"><span data-stu-id="86717-127">Distribution Agent for push subscriptions to non-SQL Server Subscribers</span></span>|**\<Publisher>-\<PublicationDatabase>-\<Publication>-\<Subscriber>-\<integer>**|  
  
 <span data-ttu-id="86717-128"><sup>1</sup> 对于 Oracle 发布的推送订阅，它是 \*\*\<Publisher>-\<Publisher**>，而不是 \<Publisher>-\<PublicationDatabase></span><span class="sxs-lookup"><span data-stu-id="86717-128"><sup>1</sup> For push subscriptions to Oracle publications, it is \*\*\<Publisher>-\<Publisher**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
 <span data-ttu-id="86717-129"><sup>2</sup> 对于 Oracle 发布的请求订阅，它是 \*\*\<Publisher>-\<DistributionDatabase**>，而不是 \<Publisher>-\<PublicationDatabase></span><span class="sxs-lookup"><span data-stu-id="86717-129"><sup>2</sup> For pull subscriptions to Oracle publications, it is \*\*\<Publisher>-\<DistributionDatabase**> rather than **\<Publisher>-\<PublicationDatabase>**</span></span>  
  
#### <a name="to-specify-synchronization-schedules"></a><span data-ttu-id="86717-130">指定同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-130">To specify synchronization schedules</span></span>  
  
1.  <span data-ttu-id="86717-131">在新建订阅向导的“同步计划”页上，从“代理计划”下拉列表中为要创建的每个订阅选择以下值之一： </span><span class="sxs-lookup"><span data-stu-id="86717-131">On the **SynchronizationSchedule** page of the New Subscription Wizard, select one of the following values from the **Agent Schedule** drop-down list for each subscription you are creating:</span></span>  
  
    -   <span data-ttu-id="86717-132">**连续运行**</span><span class="sxs-lookup"><span data-stu-id="86717-132">**Run continuously**</span></span>  
  
    -   <span data-ttu-id="86717-133">**仅按需运行**</span><span class="sxs-lookup"><span data-stu-id="86717-133">**Run on demand only**</span></span>  
  
    -   **\<Define Schedule...>**  
  
2.  <span data-ttu-id="86717-134">如果选择“\<Define Schedule...>”，请在“作业计划属性”对话框中指定一个计划，然后单击“确定”。  </span><span class="sxs-lookup"><span data-stu-id="86717-134">If you select **\<Define Schedule...>**, specify a schedule in the **Job Schedule Properties** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="86717-135">完成向导。</span><span class="sxs-lookup"><span data-stu-id="86717-135">Complete the wizard.</span></span>  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-replication-monitor"></a><span data-ttu-id="86717-136">在复制监视器中修改推送订阅的同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-136">To modify a synchronization schedule for a push subscription in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="86717-137">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，然后单击某个发布。</span><span class="sxs-lookup"><span data-stu-id="86717-137">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="86717-138">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="86717-138">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="86717-139">右键单击订阅，然后单击 **“查看详细信息”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-139">Right-click a subscription, and then click **View Details**.</span></span>  
  
4.  <span data-ttu-id="86717-140">在 "**订阅 \< SubscriptionName> \*\* " 窗口中，单击 "**操作**"，然后单击 " \*\* \<AgentName> 作业属性**"。</span><span class="sxs-lookup"><span data-stu-id="86717-140">In the **Subscription \< SubscriptionName>** window, click **Action**, and then click **\<AgentName> Job Properties**.</span></span>  
  
5.  <span data-ttu-id="86717-141">在“作业属性 - \<JobName>”对话框的“计划”页上，单击“编辑”。  </span><span class="sxs-lookup"><span data-stu-id="86717-141">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
6.  <span data-ttu-id="86717-142">在 **“作业计划属性”** 对话框中，从 **“计划类型”** 下拉列表中选择一个值：</span><span class="sxs-lookup"><span data-stu-id="86717-142">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="86717-143">若要指定代理应连续运行，请选择 **“SQL Server 代理启动时自动启动”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-143">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="86717-144">若要指定代理应按计划运行，请选择 **“重复执行”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-144">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="86717-145">若要指定代理应按需运行，请选择 **“执行一次”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-145">To specify that the agent should run on demand, select **One time**.</span></span>  
  
7.  <span data-ttu-id="86717-146">如果选择 **“重复执行”** ，请为代理指定计划。</span><span class="sxs-lookup"><span data-stu-id="86717-146">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-push-subscription-in-management-studio"></a><span data-ttu-id="86717-147">在 Management Studio 中修改推送订阅的同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-147">To modify a synchronization schedule for a push subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="86717-148">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="86717-148">Connect to the Distributor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="86717-149">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="86717-149">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="86717-150">右键单击与订阅相关联的分发代理或合并代理的作业，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-150">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="86717-151">在“作业属性 - \<JobName>”对话框的“计划”页上，单击“编辑”。  </span><span class="sxs-lookup"><span data-stu-id="86717-151">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="86717-152">在 **“作业计划属性”** 对话框中，从 **“计划类型”** 下拉列表中选择一个值：</span><span class="sxs-lookup"><span data-stu-id="86717-152">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="86717-153">若要指定代理应连续运行，请选择 **“SQL Server 代理启动时自动启动”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-153">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="86717-154">若要指定代理应按计划运行，请选择 **“重复执行”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-154">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="86717-155">若要指定代理应按需运行，请选择 **“执行一次”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-155">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="86717-156">如果选择 **“重复执行”** ，请为代理指定计划。</span><span class="sxs-lookup"><span data-stu-id="86717-156">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### <a name="to-modify-a-synchronization-schedule-for-a-pull-subscription-in-management-studio"></a><span data-ttu-id="86717-157">在 Management Studio 中修改请求订阅的同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-157">To modify a synchronization schedule for a pull subscription in Management Studio</span></span>  
  
1.  <span data-ttu-id="86717-158">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="86717-158">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="86717-159">展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="86717-159">Expand the **SQL Server Agent** folder, and then expand the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="86717-160">右键单击与订阅相关联的分发代理或合并代理的作业，再单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-160">Right-click the job for the Distribution Agent or Merge Agent associated with the subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="86717-161">在“作业属性 - \<JobName>”对话框的“计划”页上，单击“编辑”。  </span><span class="sxs-lookup"><span data-stu-id="86717-161">On the **Schedules** page of the **Job Properties - \<JobName>** dialog box, click **Edit.**</span></span>  
  
5.  <span data-ttu-id="86717-162">在 **“作业计划属性”** 对话框中，从 **“计划类型”** 下拉列表中选择一个值：</span><span class="sxs-lookup"><span data-stu-id="86717-162">In the **Job Schedule Properties** dialog box, select a value from the **Schedule Type** drop-down list:</span></span>  
  
    -   <span data-ttu-id="86717-163">若要指定代理应连续运行，请选择 **“SQL Server 代理启动时自动启动”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-163">To specify that the agent should run continuously, select **Start automatically when SQL Server Agent starts**.</span></span>  
  
    -   <span data-ttu-id="86717-164">若要指定代理应按计划运行，请选择 **“重复执行”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-164">To specify that the agent should run on a schedule, select **Recurring**.</span></span>  
  
    -   <span data-ttu-id="86717-165">若要指定代理应按需运行，请选择 **“执行一次”** 。</span><span class="sxs-lookup"><span data-stu-id="86717-165">To specify that the agent should run on demand, select **One time**.</span></span>  
  
6.  <span data-ttu-id="86717-166">如果选择 **“重复执行”** ，请为代理指定计划。</span><span class="sxs-lookup"><span data-stu-id="86717-166">If you select **Recurring**, specify a schedule for the agent.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="86717-167">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86717-167">Using Transact-SQL</span></span>  
 <span data-ttu-id="86717-168">您可以使用复制存储过程以编程的方式定义同步计划。</span><span class="sxs-lookup"><span data-stu-id="86717-168">You can define synchronization schedules programmatically using replication stored procedures.</span></span> <span data-ttu-id="86717-169">所使用的存储过程取决于复制类型和订阅类型（请求或推送）。</span><span class="sxs-lookup"><span data-stu-id="86717-169">The stored procedures that you use depend on the type of replication and the type of subscription (pull or push).</span></span>  
  
 <span data-ttu-id="86717-170">计划由以下计划参数定义，而计划的行为从 [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql) 继承：</span><span class="sxs-lookup"><span data-stu-id="86717-170">A schedule is defined by the following scheduling parameters, the behaviors of which are inherited from [sp_add_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql):</span></span>  
  
-   <span data-ttu-id="86717-171">**@frequency_type**-计划代理时所使用的频率类型。</span><span class="sxs-lookup"><span data-stu-id="86717-171">**@frequency_type** - the type of frequency used when scheduling the agent.</span></span>  
  
-   <span data-ttu-id="86717-172">**@frequency_interval**-运行代理的一周中的某一天。</span><span class="sxs-lookup"><span data-stu-id="86717-172">**@frequency_interval** - the day of the week when an agent runs.</span></span>  
  
-   <span data-ttu-id="86717-173">**@frequency_relative_interval**-计划每月运行代理的给定月份的星期。</span><span class="sxs-lookup"><span data-stu-id="86717-173">**@frequency_relative_interval** - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
-   <span data-ttu-id="86717-174">**@frequency_recurrence_factor**-同步之间发生的频率类型单位数。</span><span class="sxs-lookup"><span data-stu-id="86717-174">**@frequency_recurrence_factor** - the number of frequency-type units that occur between synchronizations.</span></span>  
  
-   <span data-ttu-id="86717-175">**@frequency_subday**-一天内多次运行代理时的频率单位。</span><span class="sxs-lookup"><span data-stu-id="86717-175">**@frequency_subday** - the frequency unit when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="86717-176">**@frequency_subday_interval**-一天内多次运行代理时运行之间的频率单位数。</span><span class="sxs-lookup"><span data-stu-id="86717-176">**@frequency_subday_interval** - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
-   <span data-ttu-id="86717-177">**@active_start_time_of_day**-在给定日期内代理运行开始的最早时间。</span><span class="sxs-lookup"><span data-stu-id="86717-177">**@active_start_time_of_day** - the earliest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="86717-178">**@active_end_time_of_day**-在给定日期内代理运行开始的最晚时间。</span><span class="sxs-lookup"><span data-stu-id="86717-178">**@active_end_time_of_day** - the latest time in a given day when an agent run will start.</span></span>  
  
-   <span data-ttu-id="86717-179">**@active_start_date**-代理计划生效的第一天。</span><span class="sxs-lookup"><span data-stu-id="86717-179">**@active_start_date** - the first day that the agent schedule will be in effect.</span></span>  
  
-   <span data-ttu-id="86717-180">**@active_end_date**-代理计划生效的最后一天。</span><span class="sxs-lookup"><span data-stu-id="86717-180">**@active_end_date** - the last day that the agent schedule will be in effect.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="86717-181">为事务发布的请求订阅定义同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-181">To define the synchronization schedule for a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="86717-182">对事务发布创建一个新的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-182">Create a new pull subscription to a transactional publication.</span></span> <span data-ttu-id="86717-183">有关详细信息，请参阅 [创建请求订阅](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-183">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-184">在订阅服务器上，执行 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86717-184">At the Subscriber, execute [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="86717-185">指定 **@publisher** 、 **@publisher_db** 、 **@publication** 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 运行订阅服务器上分发代理的 Windows 凭据 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="86717-185">Specify **@publisher**, **@publisher_db**, **@publication**, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="86717-186">指定上面详细说明的同步参数，为同步订阅的分发代理作业定义计划。</span><span class="sxs-lookup"><span data-stu-id="86717-186">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="86717-187">为事务发布的推送订阅定义同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-187">To define the synchronization schedule for a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="86717-188">对事务发布创建一个新的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-188">Create a new push subscription to a transactional publication.</span></span> <span data-ttu-id="86717-189">有关详细信息，请参阅 [创建推送订阅](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-189">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-190">在订阅服务器上，执行 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86717-190">At the Subscriber, execute [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="86717-191">指定 **@subscriber** 、 **@subscriber_db** 、 **@publication** 和运行订阅服务器上分发代理的 Windows 凭据 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="86717-191">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Distribution Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="86717-192">指定上面详细说明的同步参数，为同步订阅的分发代理作业定义计划。</span><span class="sxs-lookup"><span data-stu-id="86717-192">Specify the synchronization parameters, detailed above, that define the schedule for the Distribution Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="86717-193">为合并发布的请求订阅定义同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-193">To define the synchronization schedule for a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="86717-194">对合并发布创建一个新的请求订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-194">Create a new pull subscription to a merge publication.</span></span> <span data-ttu-id="86717-195">有关详细信息，请参阅 [创建请求订阅](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-195">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-196">在订阅服务器上，执行 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86717-196">At the Subscriber, execute [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="86717-197">指定 **@publisher** 、 **@publisher_db** 、 **@publication** 和运行订阅服务器上合并代理的 Windows 凭据 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="86717-197">Specify **@publisher**, **@publisher_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="86717-198">指定上面详细说明的同步参数，为同步订阅的合并代理作业定义计划。</span><span class="sxs-lookup"><span data-stu-id="86717-198">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
#### <a name="to-define-the-synchronization-schedule-for-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="86717-199">为合并发布的推送订阅定义同步计划</span><span class="sxs-lookup"><span data-stu-id="86717-199">To define the synchronization schedule for a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="86717-200">对合并发布创建一个新的推送订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-200">Create a new push subscription to a merge publication.</span></span> <span data-ttu-id="86717-201">有关详细信息，请参阅 [创建推送订阅](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-201">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-202">在订阅服务器上，执行 [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86717-202">At the Subscriber, execute [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="86717-203">指定 **@subscriber** 、 **@subscriber_db** 、 **@publication** 和运行订阅服务器上合并代理的 Windows 凭据 **@job_name** **@password** 。</span><span class="sxs-lookup"><span data-stu-id="86717-203">Specify **@subscriber**, **@subscriber_db**, **@publication**, and the Windows credentials under which the Merge Agent at the Subscriber runs for **@job_name** and **@password**.</span></span> <span data-ttu-id="86717-204">指定上面详细说明的同步参数，为同步订阅的合并代理作业定义计划。</span><span class="sxs-lookup"><span data-stu-id="86717-204">Specify the synchronization parameters, detailed above, that define the schedule for the Merge Agent job that synchronizes the subscription.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="86717-205">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="86717-205">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="86717-206">复制使用 SQL Server 代理为定期发生的活动计划作业（如快照生成和订阅同步）。</span><span class="sxs-lookup"><span data-stu-id="86717-206">Replication uses the SQL Server Agent to schedule jobs for activities that occur periodically, such as snapshot generation and subscription synchronization.</span></span> <span data-ttu-id="86717-207">可以编程的方式使用复制管理对象 (RMO) 为复制代理作业指定计划。</span><span class="sxs-lookup"><span data-stu-id="86717-207">You can use Replication Management Objects (RMO) programmatically to specify schedules for replication agent jobs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86717-208">创建一个订阅并将 `false`（请求订阅的默认行为）的值指定为 `CreateSyncAgentByDefault` 时，不会创建代理作业，并忽略计划属性。</span><span class="sxs-lookup"><span data-stu-id="86717-208">When you create a subscription and specify a value `false` for `CreateSyncAgentByDefault` (the default behavior for pull subscriptions) the agent job is not created and scheduling properties are ignored.</span></span> <span data-ttu-id="86717-209">在这种情况下，必须由应用程序确定同步计划。</span><span class="sxs-lookup"><span data-stu-id="86717-209">In this case, the synchronization schedule must be determined by the application.</span></span> <span data-ttu-id="86717-210">有关详细信息，请参阅 [Create a Pull Subscription](create-a-pull-subscription.md) 和 [Create a Push Subscription](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-210">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md) and [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="86717-211">在创建事务发布的推送订阅时定义一个复制代理计划</span><span class="sxs-lookup"><span data-stu-id="86717-211">To define a replication agent schedule when you create a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="86717-212">为要创建的订阅创建一个 <xref:Microsoft.SqlServer.Replication.TransSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="86717-212">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="86717-213">有关详细信息，请参阅 [创建推送订阅](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-213">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-214">在调用 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>之前，设置 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 属性的下列一个或多个字段：</span><span class="sxs-lookup"><span data-stu-id="86717-214">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="86717-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 计划代理时所使用的频率类型（如每天或每周）。</span><span class="sxs-lookup"><span data-stu-id="86717-215"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="86717-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 星期几运行代理。</span><span class="sxs-lookup"><span data-stu-id="86717-216"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="86717-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 计划每月运行代理的给定月份的星期。</span><span class="sxs-lookup"><span data-stu-id="86717-217"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month when the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="86717-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同步之间发生的频率类型单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-218"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="86717-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 一天内多次运行代理时的频率单位。</span><span class="sxs-lookup"><span data-stu-id="86717-219"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 一天内多次运行代理时运行之间的频率单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-220"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 在给定日期内代理运行开始的最早时间。</span><span class="sxs-lookup"><span data-stu-id="86717-221"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 在给定日期内代理运行开始的最晚时间。</span><span class="sxs-lookup"><span data-stu-id="86717-222"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理计划有效的起始日期。</span><span class="sxs-lookup"><span data-stu-id="86717-223"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="86717-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理计划有效的结束日期。</span><span class="sxs-lookup"><span data-stu-id="86717-224"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86717-225">如果未指定上述某个属性，将设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="86717-225">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="86717-226">调用 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 方法创建订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-226">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="86717-227">在创建事务发布的请求订阅时定义一个复制代理计划</span><span class="sxs-lookup"><span data-stu-id="86717-227">To define a replication agent schedule when you create a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="86717-228">为要创建的订阅创建一个 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="86717-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="86717-229">有关详细信息，请参阅 [创建请求订阅](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-229">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-230">在调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>之前，设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 属性的下列一个或多个字段：</span><span class="sxs-lookup"><span data-stu-id="86717-230">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="86717-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 计划代理时所使用的频率类型（如每天或每周）。</span><span class="sxs-lookup"><span data-stu-id="86717-231"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="86717-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 星期几运行代理。</span><span class="sxs-lookup"><span data-stu-id="86717-232"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="86717-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 计划每月运行代理的给定月份的星期。</span><span class="sxs-lookup"><span data-stu-id="86717-233"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="86717-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同步之间发生的频率类型单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-234"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="86717-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 一天内多次运行代理时的频率单位。</span><span class="sxs-lookup"><span data-stu-id="86717-235"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 一天内多次运行代理时运行之间的频率单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-236"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 在给定日期内代理运行开始的最早时间。</span><span class="sxs-lookup"><span data-stu-id="86717-237"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 在给定日期内代理运行开始的最晚时间。</span><span class="sxs-lookup"><span data-stu-id="86717-238"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理计划有效的起始日期。</span><span class="sxs-lookup"><span data-stu-id="86717-239"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="86717-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理计划有效的结束日期。</span><span class="sxs-lookup"><span data-stu-id="86717-240"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86717-241">如果未指定上述某个属性，将设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="86717-241">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="86717-242">调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 方法创建订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-242">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="86717-243">在创建合并发布的请求订阅时定义一个复制代理计划</span><span class="sxs-lookup"><span data-stu-id="86717-243">To define a replication agent schedule when you create a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="86717-244">为要创建的订阅创建一个 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="86717-244">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="86717-245">有关详细信息，请参阅 [创建请求订阅](create-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-245">For more information, see [Create a Pull Subscription](create-a-pull-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-246">在调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>之前，设置 <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> 属性的下列一个或多个字段：</span><span class="sxs-lookup"><span data-stu-id="86717-246">Before you call <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.PullSubscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="86717-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 计划代理时所使用的频率类型（如每天或每周）。</span><span class="sxs-lookup"><span data-stu-id="86717-247"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="86717-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 星期几运行代理。</span><span class="sxs-lookup"><span data-stu-id="86717-248"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="86717-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 计划每月运行代理的给定月份的星期。</span><span class="sxs-lookup"><span data-stu-id="86717-249"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="86717-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同步之间发生的频率类型单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-250"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="86717-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 一天内多次运行代理时的频率单位。</span><span class="sxs-lookup"><span data-stu-id="86717-251"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 一天内多次运行代理时运行之间的频率单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-252"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 在给定日期内代理运行开始的最早时间。</span><span class="sxs-lookup"><span data-stu-id="86717-253"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 在给定日期内代理运行开始的最晚时间。</span><span class="sxs-lookup"><span data-stu-id="86717-254"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理计划有效的起始日期。</span><span class="sxs-lookup"><span data-stu-id="86717-255"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="86717-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理计划有效的结束日期。</span><span class="sxs-lookup"><span data-stu-id="86717-256"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86717-257">如果未指定上述某个属性，将设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="86717-257">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="86717-258">调用 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> 方法创建订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-258">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> method to create the subscription.</span></span>  
  
#### <a name="to-define-a-replication-agent-schedule-when-you-create-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="86717-259">在创建合并发布的推送订阅时定义一个复制代理计划</span><span class="sxs-lookup"><span data-stu-id="86717-259">To define a replication agent schedule when you create a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="86717-260">为要创建的订阅创建一个 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="86717-260">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class for the subscription you are creating.</span></span> <span data-ttu-id="86717-261">有关详细信息，请参阅 [创建推送订阅](create-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="86717-261">For more information, see [Create a Push Subscription](create-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="86717-262">在调用 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>之前，设置 <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> 属性的下列一个或多个字段：</span><span class="sxs-lookup"><span data-stu-id="86717-262">Before you call <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A>, set one or more of the following fields of the <xref:Microsoft.SqlServer.Replication.Subscription.AgentSchedule%2A> property:</span></span>  
  
    -   <span data-ttu-id="86717-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - 计划代理时所使用的频率类型（如每天或每周）。</span><span class="sxs-lookup"><span data-stu-id="86717-263"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyType%2A> - the type of frequency (such as daily or weekly) that you use when you schedule the agent.</span></span>  
  
    -   <span data-ttu-id="86717-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - 星期几运行代理。</span><span class="sxs-lookup"><span data-stu-id="86717-264"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyInterval%2A> - the day of the week that an agent runs.</span></span>  
  
    -   <span data-ttu-id="86717-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - 计划每月运行代理的给定月份的星期。</span><span class="sxs-lookup"><span data-stu-id="86717-265"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRelativeInterval%2A> - the week of a given month that the agent is scheduled to run monthly.</span></span>  
  
    -   <span data-ttu-id="86717-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - 同步之间发生的频率类型单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-266"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencyRecurrenceFactor%2A> - the number of frequency-type units that occur between synchronizations.</span></span>  
  
    -   <span data-ttu-id="86717-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - 一天内多次运行代理时的频率单位。</span><span class="sxs-lookup"><span data-stu-id="86717-267"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDay%2A> - the frequency unit when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - 一天内多次运行代理时运行之间的频率单位数值。</span><span class="sxs-lookup"><span data-stu-id="86717-268"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.FrequencySubDayInterval%2A> - the number of frequency units between runs when the agent runs more often than once a day.</span></span>  
  
    -   <span data-ttu-id="86717-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - 在给定日期内代理运行开始的最早时间。</span><span class="sxs-lookup"><span data-stu-id="86717-269"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartTime%2A> - earliest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - 在给定日期内代理运行开始的最晚时间。</span><span class="sxs-lookup"><span data-stu-id="86717-270"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndTime%2A> - latest time on a given day that an agent run starts.</span></span>  
  
    -   <span data-ttu-id="86717-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - 代理计划有效的起始日期。</span><span class="sxs-lookup"><span data-stu-id="86717-271"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveStartDate%2A> - first day that the agent schedule is in effect.</span></span>  
  
    -   <span data-ttu-id="86717-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - 代理计划有效的结束日期。</span><span class="sxs-lookup"><span data-stu-id="86717-272"><xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule.ActiveEndDate%2A> - last day that the agent schedule is in effect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="86717-273">如果未指定上述某个属性，将设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="86717-273">If you do not specify one of these properties, a default value is set.</span></span>  
  
3.  <span data-ttu-id="86717-274">调用 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> 方法创建订阅。</span><span class="sxs-lookup"><span data-stu-id="86717-274">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> method to create the subscription.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="86717-275">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="86717-275">Example (RMO)</span></span>  
 <span data-ttu-id="86717-276">此示例创建一个合并发布的推送订阅并指定同步订阅计划。</span><span class="sxs-lookup"><span data-stu-id="86717-276">This example creates a push subscription to a merge publication and specifies the schedule on which the subscription is synchronized.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="86717-277">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86717-277">See Also</span></span>  
 <span data-ttu-id="86717-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="86717-278">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 <span data-ttu-id="86717-279">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="86717-279">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="86717-280">[同步推送订阅](synchronize-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="86717-280">[Synchronize a Push Subscription](synchronize-a-push-subscription.md) </span></span>  
 <span data-ttu-id="86717-281">[同步请求订阅](synchronize-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="86717-281">[Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="86717-282">同步数据</span><span class="sxs-lookup"><span data-stu-id="86717-282">Synchronize Data</span></span>](synchronize-data.md)  
  
  
