---
title: 同步请求订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- pull subscriptions [SQL Server replication], synchronizing
- synchronization [SQL Server replication], pull subscriptions
- subscriptions [SQL Server replication], pull
ms.assetid: 3ca24b23-fdc3-408e-8208-a2ace48fc8e3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 826622cd17862c0535e60c01baab756af2b2996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587345"
---
# <a name="synchronize-a-pull-subscription"></a><span data-ttu-id="63d8f-102">同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="63d8f-102">Synchronize a Pull Subscription</span></span>
  <span data-ttu-id="63d8f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]复制代理 [或复制管理对象 (RMO) 在](agents/replication-agents-overview.md)中同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-103">This topic describes how to synchronize a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="63d8f-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63d8f-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="63d8f-105">订阅由分发代理（对于快照复制和事务复制）或合并代理（对于合并复制）进行同步。</span><span class="sxs-lookup"><span data-stu-id="63d8f-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="63d8f-106">代理可以连续运行、按需运行或按计划运行。</span><span class="sxs-lookup"><span data-stu-id="63d8f-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="63d8f-107">有关如何指定同步计划的详细信息，请参阅[指定同步计划](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="63d8f-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="63d8f-108">在 **中的** “本地订阅” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]文件夹中，按需同步订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-108">Synchronize a subscription on demand from the **Local Subscriptions** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-on-demand-in-management-studio"></a><span data-ttu-id="63d8f-109">在 Management Studio 中按需同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="63d8f-109">To synchronize a pull subscription on demand in Management Studio</span></span>  
  
1.  <span data-ttu-id="63d8f-110">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="63d8f-110">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="63d8f-111">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="63d8f-111">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="63d8f-112">右键单击要同步的订阅，然后单击 **“查看同步状态”** 。</span><span class="sxs-lookup"><span data-stu-id="63d8f-112">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="63d8f-113">在“查看同步状态 - \<Subscriber>:\<SubscriptionDatabase>”对话框中，单击“启动” 。</span><span class="sxs-lookup"><span data-stu-id="63d8f-113">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="63d8f-114">完成同步后，将显示消息 **“同步完成”** 。</span><span class="sxs-lookup"><span data-stu-id="63d8f-114">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
5.  <span data-ttu-id="63d8f-115">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="63d8f-115">Click **Close**.</span></span>  
  
##  <a name="replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="63d8f-116">Replication Agents</span><span class="sxs-lookup"><span data-stu-id="63d8f-116">Replication Agents</span></span>  
 <span data-ttu-id="63d8f-117">可通过在命令提示符下调用相应的复制代理可执行文件，以编程方式按需同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-117">Pull subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="63d8f-118">被调用的复制代理可执行文件将取决于请求订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="63d8f-118">The replication agent executable file that is invoked will depend on the type of publication to which the pull subscription belongs.</span></span> <span data-ttu-id="63d8f-119">有关详细信息，请参阅 [Replication Agents](agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="63d8f-119">For more information, see [Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63d8f-120">复制代理使用通过命令提示符启动该代理的用户的 Windows 身份验证凭据连接到本地服务器。</span><span class="sxs-lookup"><span data-stu-id="63d8f-120">Replication agents connect to the local server using the Windows Authentication credentials of the user who started the agent from the command prompt.</span></span> <span data-ttu-id="63d8f-121">这些 Windows 凭据还在使用 Windows 集成身份验证连接到远程服务器时使用。</span><span class="sxs-lookup"><span data-stu-id="63d8f-121">These Windows credentials are also used when connecting to remote servers using Windows Integrated Authentication.</span></span>  
  
#### <a name="to-start-the-distribution-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="63d8f-122">通过命令提示符或批处理文件启动分发代理</span><span class="sxs-lookup"><span data-stu-id="63d8f-122">To start the distribution agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="63d8f-123">在命令提示符下或批处理文件中，通过运行 [distrib.exe](agents/replication-distribution-agent.md) 并指定下列命令行参数来启动 **复制分发代理**：</span><span class="sxs-lookup"><span data-stu-id="63d8f-123">From the command prompt or in a batch file, start the [Replication Distribution Agent](agents/replication-distribution-agent.md) by running **distrib.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="63d8f-124">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="63d8f-124">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="63d8f-125">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="63d8f-125">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="63d8f-126">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="63d8f-126">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="63d8f-127">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-127">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="63d8f-128">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="63d8f-128">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="63d8f-129">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="63d8f-129">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="63d8f-130">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-130">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="63d8f-131">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-131">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="63d8f-132">如果您使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则还必须指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="63d8f-132">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="63d8f-133">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-133">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-134">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-134">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-135">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="63d8f-135">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="63d8f-136">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-136">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-137">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-137">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-138">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="63d8f-138">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="63d8f-139">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-139">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-140">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-140">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-141">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="63d8f-141">**-SubscriberSecurityMode** = **0**</span></span>  
  
#### <a name="to-start-the-merge-agent-from-the-command-prompt-or-from-a-batch-file"></a><span data-ttu-id="63d8f-142">在命令提示符下或批处理文件中启动合并代理</span><span class="sxs-lookup"><span data-stu-id="63d8f-142">To start the merge agent from the command prompt or from a batch file</span></span>  
  
1.  <span data-ttu-id="63d8f-143">在命令提示符下或批处理文件中，通过运行 [replmerg.exe](agents/replication-merge-agent.md) 并指定下列命令行参数来启动 **复制合并代理**：</span><span class="sxs-lookup"><span data-stu-id="63d8f-143">From the command prompt or in a batch file, start the [Replication Merge Agent](agents/replication-merge-agent.md) by running **replmerg.exe**, specifying the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="63d8f-144">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="63d8f-144">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="63d8f-145">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="63d8f-145">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="63d8f-146">**-PublisherSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-146">**-PublisherSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="63d8f-147">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="63d8f-147">**-Publication**</span></span>  
  
    -   <span data-ttu-id="63d8f-148">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="63d8f-148">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="63d8f-149">**-DistributorSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-149">**-DistributorSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="63d8f-150">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="63d8f-150">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="63d8f-151">**-SubscriberSecurityMode** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-151">**-SubscriberSecurityMode** = **1**</span></span>  
  
    -   <span data-ttu-id="63d8f-152">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="63d8f-152">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="63d8f-153">**-SubscriptionType** = **1**</span><span class="sxs-lookup"><span data-stu-id="63d8f-153">**-SubscriptionType** = **1**</span></span>  
  
     <span data-ttu-id="63d8f-154">如果您使用的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证，则还必须指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="63d8f-154">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="63d8f-155">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-155">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-156">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-156">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-157">**-DistributorSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="63d8f-157">**-DistributorSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="63d8f-158">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-158">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-159">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-159">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-160">**-PublisherSecurityMode** =  **\@publisher_security_mode**</span><span class="sxs-lookup"><span data-stu-id="63d8f-160">**-PublisherSecurityMode** = **0**</span></span>  
  
    -   <span data-ttu-id="63d8f-161">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="63d8f-161">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="63d8f-162">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="63d8f-162">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="63d8f-163">**-SubscriberSecurityMode** = **0**</span><span class="sxs-lookup"><span data-stu-id="63d8f-163">**-SubscriberSecurityMode** = **0**</span></span>  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="63d8f-164">示例（复制代理）</span><span class="sxs-lookup"><span data-stu-id="63d8f-164">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="63d8f-165">以下示例启动分发代理以同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-165">The following example starts the Distribution Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="63d8f-166">所有连接均使用 Windows 身份验证实现。</span><span class="sxs-lookup"><span data-stu-id="63d8f-166">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_synctranpullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/synctranpullsub_10.bat)]  
  
 <span data-ttu-id="63d8f-167">以下示例启动合并代理以同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-167">The following example starts the Merge Agent to synchronize a pull subscription.</span></span> <span data-ttu-id="63d8f-168">所有连接均使用 Windows 身份验证实现。</span><span class="sxs-lookup"><span data-stu-id="63d8f-168">All connections are made using Windows Authentication.</span></span>  
  
 [!code-sql[HowTo#bat_syncmergepullsub_10](../../snippets/tsql/SQL15/replication/howto/tsql/syncmergepullsub_10.bat)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="63d8f-169">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="63d8f-169">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="63d8f-170">可以使用复制管理对象 (RMO) 和托管代码对复制代理功能的访问权限，以编程方式同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="63d8f-170">You can synchronize pull subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="63d8f-171">用于同步请求订阅的类取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="63d8f-171">The classes you use to synchronize a pull subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63d8f-172">如果您要启动一个自主运行而不影响应用程序的订阅，请异步启动代理。</span><span class="sxs-lookup"><span data-stu-id="63d8f-172">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="63d8f-173">但是，如果您要监视同步的结果并在同步进程期间从代理处接收回调（例如，要显示进度栏），则应当同步启动代理。</span><span class="sxs-lookup"><span data-stu-id="63d8f-173">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="63d8f-174">对于 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 订阅服务器，必须同步启动代理。</span><span class="sxs-lookup"><span data-stu-id="63d8f-174">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="63d8f-175">将请求订阅与快照或事务发布进行同步</span><span class="sxs-lookup"><span data-stu-id="63d8f-175">To synchronize a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="63d8f-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="63d8f-176">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="63d8f-177">创建 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 类的实例并设置下列属性：</span><span class="sxs-lookup"><span data-stu-id="63d8f-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="63d8f-178">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>的订阅数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-178">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-179">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>的订阅所属的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-179">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-180">为 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>设置发布数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-180">The name of the publication database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-181">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>的发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-181">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-182">在步骤 1 中为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>创建的连接。</span><span class="sxs-lookup"><span data-stu-id="63d8f-182">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="63d8f-183">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以获取其他订阅属性。</span><span class="sxs-lookup"><span data-stu-id="63d8f-183">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="63d8f-184">如果该方法返回 `false`，则确保订阅存在。</span><span class="sxs-lookup"><span data-stu-id="63d8f-184">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="63d8f-185">使用下列方法之一在订阅服务器中启动分发代理：</span><span class="sxs-lookup"><span data-stu-id="63d8f-185">Start the Distribution Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="63d8f-186">在步骤 2 中的 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> 实例上调用 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-186">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransPullSubscription> from step 2.</span></span> <span data-ttu-id="63d8f-187">该方法异步启动分发代理，并在代理作业运行时立即将控制权返回给您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="63d8f-187">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="63d8f-188">您不能为 [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 订阅服务器调用该方法，如果创建的订阅的 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 的值为 `false`（默认值），则也不能调用该方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-188">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="63d8f-189">获取 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 属性中 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> 类的实例，然后调用 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-189">Get an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="63d8f-190">该方法可以同步启动代理，并且控制权仍属于运行代理作业。</span><span class="sxs-lookup"><span data-stu-id="63d8f-190">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="63d8f-191">在执行同步期间，您可以在代理仍旧运行的情况下处理 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="63d8f-191">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="63d8f-192">如果你在 `false` 创建请求订阅时将的值指定为 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (默认) ，则还需要指定 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A> 、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A> 和（可选）， <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> 因为订阅的与代理作业相关的元数据在[MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)中不可用。</span><span class="sxs-lookup"><span data-stu-id="63d8f-192">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorSecurityMode%2A>, and optionally <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorLogin%2A> and <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.DistributorPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
#### <a name="to-synchronize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="63d8f-193">将请求订阅与合并发布进行同步</span><span class="sxs-lookup"><span data-stu-id="63d8f-193">To synchronize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="63d8f-194">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与订阅服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="63d8f-194">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="63d8f-195">创建 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 类的实例并设置下列属性：</span><span class="sxs-lookup"><span data-stu-id="63d8f-195">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="63d8f-196">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>的订阅数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-196">The subscription database name for <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-197">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>的订阅所属的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-197">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-198">将 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>设置为已发布的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-198">The name of the published database for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-199">用于 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>的发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="63d8f-199">The name of the Publisher for <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>.</span></span>  
  
    -   <span data-ttu-id="63d8f-200">在步骤 1 中为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>创建的连接。</span><span class="sxs-lookup"><span data-stu-id="63d8f-200">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="63d8f-201">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以获取其他订阅属性。</span><span class="sxs-lookup"><span data-stu-id="63d8f-201">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="63d8f-202">如果该方法返回 `false`，则确保订阅存在。</span><span class="sxs-lookup"><span data-stu-id="63d8f-202">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="63d8f-203">使用下列方法之一在订阅服务器中启动合并代理：</span><span class="sxs-lookup"><span data-stu-id="63d8f-203">Start the Merge Agent at the Subscriber in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="63d8f-204">在步骤 2 中的 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> 实例上调用 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-204">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergePullSubscription> from step 2.</span></span> <span data-ttu-id="63d8f-205">该方法异步启动合并代理，并在代理作业运行时立即将控制权返回给您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="63d8f-205">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="63d8f-206">您不能为 [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 订阅服务器调用该方法，如果创建的订阅的 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> 的值为 `false`（默认值），则也不能调用该方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-206">You cannot call this method for [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers or if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default).</span></span>  
  
    -   <span data-ttu-id="63d8f-207">获取 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 属性中 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> 类的实例，然后调用 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="63d8f-207">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="63d8f-208">该方法可以同步启动合并代理，并且控件仍属于运行代理作业。</span><span class="sxs-lookup"><span data-stu-id="63d8f-208">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="63d8f-209">在执行同步期间，您可以在代理仍旧运行的情况下处理 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="63d8f-209">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="63d8f-210">如果你在 `false` 创建请求订阅时将的值指定为 <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (默认) ，则还需要指定、、、、、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A> 和（ <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A> 可选）， <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A> <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> 因为订阅的与代理作业相关的元数据在[MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql)中不可用。</span><span class="sxs-lookup"><span data-stu-id="63d8f-210">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> (the default) when you created the pull subscription, you also need to specify <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Distributor%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherSecurityMode%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.HostName%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.SubscriptionType%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.ExchangeType%2A>, and optionally <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorLogin%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.DistributorPassword%2A>, <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherLogin%2A>, and <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.PublisherPassword%2A> because the agent job related metadata for the subscription is not available in [MSsubscription_properties](/sql/relational-databases/system-tables/mssubscription-properties-transact-sql).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="63d8f-211">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="63d8f-211">Examples (RMO)</span></span>  
 <span data-ttu-id="63d8f-212">该示例将请求订阅与事务发布进行同步，其中，代理使用代理作业进行异步启动。</span><span class="sxs-lookup"><span data-stu-id="63d8f-212">This example synchronizes a pull subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub_withjob)]  
  
 <span data-ttu-id="63d8f-213">该示例将请求订阅与事务发布进行同步，其中，代理进行同步启动。</span><span class="sxs-lookup"><span data-stu-id="63d8f-213">This example synchronizes a pull subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpullsub)]  
  
 <span data-ttu-id="63d8f-214">该示例将请求订阅与合并发布进行同步，其中，代理使用代理作业进行异步启动。</span><span class="sxs-lookup"><span data-stu-id="63d8f-214">This example synchronizes a pull subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_withjob)]  
  
 <span data-ttu-id="63d8f-215">该示例将请求订阅与合并发布进行同步，其中，代理进行同步启动。</span><span class="sxs-lookup"><span data-stu-id="63d8f-215">This example synchronizes a pull subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub)]  
  
 <span data-ttu-id="63d8f-216">该示例使用 Web 同步将请求订阅与合并发布进行同步。</span><span class="sxs-lookup"><span data-stu-id="63d8f-216">This example synchronizes a pull subscription to a merge publication using Web synchronization.</span></span> <span data-ttu-id="63d8f-217">该订阅是在没有代理作业和相关订阅元数据的情况下创建的，因此，必须同步启动代理，并提供更多的订阅信息。</span><span class="sxs-lookup"><span data-stu-id="63d8f-217">The subscription was created without the agent job and related subscription metadata, so the agent must be started synchronously and additional subscription information is supplied.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePullSub_NoJobWebSync](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepullsub_nojobwebsync)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePullSub_NoJobWebSync](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepullsub_nojobwebsync)]  
  
## <a name="see-also"></a><span data-ttu-id="63d8f-218">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63d8f-218">See Also</span></span>  
 <span data-ttu-id="63d8f-219">[同步数据](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="63d8f-219">[Synchronize Data](synchronize-data.md) </span></span>  
 <span data-ttu-id="63d8f-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="63d8f-220">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 [<span data-ttu-id="63d8f-221">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="63d8f-221">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
