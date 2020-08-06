---
title: 同步推送订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], push subscriptions
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], synchronizing
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5fb2f7bd961748272d6cd67e3412b09d9370a6f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689853"
---
# <a name="synchronize-a-push-subscription"></a><span data-ttu-id="3c41d-102">同步推送订阅</span><span class="sxs-lookup"><span data-stu-id="3c41d-102">Synchronize a Push Subscription</span></span>
  <span data-ttu-id="3c41d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]复制代理 [或复制管理对象 (RMO) 在](agents/replication-agents-overview.md)中同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-103">This topic describes how to synchronize a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [replication agents](agents/replication-agents-overview.md), or Replication Management Objects (RMO).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3c41d-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3c41d-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3c41d-105">订阅由分发代理（对于快照复制和事务复制）或合并代理（对于合并复制）进行同步。</span><span class="sxs-lookup"><span data-stu-id="3c41d-105">Subscriptions are synchronized by the Distribution Agent (for snapshot and transactional replication) or the Merge Agent (for merge replication).</span></span> <span data-ttu-id="3c41d-106">代理可以连续运行、按需运行或按计划运行。</span><span class="sxs-lookup"><span data-stu-id="3c41d-106">Agents can run continuously, run on demand, or run on a schedule.</span></span> <span data-ttu-id="3c41d-107">有关如何指定同步计划的详细信息，请参阅[指定同步计划](specify-synchronization-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="3c41d-107">For more information about specifying synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="3c41d-108">从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的“本地发布”和“本地订阅”文件夹及复制监视器的“所有订阅”选项卡中，按需同步订阅  。</span><span class="sxs-lookup"><span data-stu-id="3c41d-108">Synchronize a subscription on demand from the **Local Publications** and **Local Subscriptions** folders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and the **All Subscriptions** tab in Replication Monitor.</span></span> <span data-ttu-id="3c41d-109">不能从订阅服务器按需同步对 Oracle 发布的订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-109">Subscriptions to Oracle publications cannot be synchronized on demand from the Subscriber.</span></span> <span data-ttu-id="3c41d-110">有关启动复制监视器的信息，请参阅[启动复制监视器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3c41d-110">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-publisher"></a><span data-ttu-id="3c41d-111">在 Management Studio 中按需同步推送订阅（在发布服务器中）</span><span class="sxs-lookup"><span data-stu-id="3c41d-111">To synchronize a push subscription on demand in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="3c41d-112">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="3c41d-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="3c41d-113">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3c41d-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="3c41d-114">展开要同步其订阅的发布。</span><span class="sxs-lookup"><span data-stu-id="3c41d-114">Expand the publication for which you want to synchronize subscriptions.</span></span>  
  
4.  <span data-ttu-id="3c41d-115">右键单击要同步的订阅，然后单击 **“查看同步状态”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-115">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
5.  <span data-ttu-id="3c41d-116">在“查看同步状态 - \<Subscriber>:\<SubscriptionDatabase>”对话框中，单击“启动” 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-116">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="3c41d-117">完成同步后，将显示消息 **“同步完成”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-117">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="3c41d-118">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3c41d-118">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-management-studio-at-the-subscriber"></a><span data-ttu-id="3c41d-119">在 Management Studio 中按需同步推送订阅（在订阅服务器中）</span><span class="sxs-lookup"><span data-stu-id="3c41d-119">To synchronize a push subscription on demand in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="3c41d-120">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中连接到订阅服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="3c41d-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="3c41d-121">展开 **“复制”** 文件夹，再展开 **“本地订阅”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3c41d-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="3c41d-122">右键单击要同步的订阅，然后单击 **“查看同步状态”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-122">Right-click the subscription you want to synchronize, and then click **View Synchronization Status**.</span></span>  
  
4.  <span data-ttu-id="3c41d-123">将显示一条消息，指示建立与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="3c41d-123">A message is displayed about establishing a connection to the Distributor.</span></span> <span data-ttu-id="3c41d-124">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="3c41d-124">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="3c41d-125">在“查看同步状态 - \<Subscriber>:\<SubscriptionDatabase>”对话框中，单击“启动” 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-125">In the **View Synchronization Status - \<Subscriber>:\<SubscriptionDatabase>** dialog box, click **Start**.</span></span> <span data-ttu-id="3c41d-126">完成同步后，将显示消息 **“同步完成”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-126">When synchronization is complete, the message **Synchronization completed** is displayed.</span></span>  
  
6.  <span data-ttu-id="3c41d-127">单击“关闭”。</span><span class="sxs-lookup"><span data-stu-id="3c41d-127">Click **Close**.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-on-demand-in-replication-monitor"></a><span data-ttu-id="3c41d-128">在复制监视器中按需同步推送订阅</span><span class="sxs-lookup"><span data-stu-id="3c41d-128">To synchronize a push subscription on demand in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="3c41d-129">在复制监视器的左窗格中依次展开发布服务器组、发布服务器，再单击一个发布。</span><span class="sxs-lookup"><span data-stu-id="3c41d-129">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="3c41d-130">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3c41d-130">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="3c41d-131">右键单击要同步的订阅，然后单击 **“开始同步”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-131">Right-click the subscription you want to synchronize, and then click **Start Synchronizing**.</span></span>  
  
4.  <span data-ttu-id="3c41d-132">若要查看同步进度，请右键单击该订阅，然后单击 **“查看详细信息”** 。</span><span class="sxs-lookup"><span data-stu-id="3c41d-132">To view synchronization progress, right-click the subscription, and then click **View Details**.</span></span>  
  
##  <a name="using-replication-agents"></a><a name="ReplProg"></a> <span data-ttu-id="3c41d-133">使用复制代理</span><span class="sxs-lookup"><span data-stu-id="3c41d-133">Using Replication Agents</span></span>  
 <span data-ttu-id="3c41d-134">可通过在命令提示符下调用相应的复制代理可执行文件，以编程方式按需同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-134">Push subscriptions can be synchronized programmatically and on-demand by invoking the appropriate replication agent executable file from the command prompt.</span></span> <span data-ttu-id="3c41d-135">被调用的复制代理可执行文件将取决于推送订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="3c41d-135">The replication agent executable file that is invoked will depend on the type of publication to which the push subscription belongs.</span></span>  
  
#### <a name="to-start-the-distribution-agent-to-synchronize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="3c41d-136">启动分发代理以将推送订阅与事务发布进行同步</span><span class="sxs-lookup"><span data-stu-id="3c41d-136">To start the Distribution Agent to synchronize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="3c41d-137">通过命令提示符或分发服务器中的批处理文件，执行 **distrib.exe**。</span><span class="sxs-lookup"><span data-stu-id="3c41d-137">From the command prompt or in a batch file at the Distributor, execute **distrib.exe**.</span></span> <span data-ttu-id="3c41d-138">指定下列命令行参数：</span><span class="sxs-lookup"><span data-stu-id="3c41d-138">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="3c41d-139">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="3c41d-139">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="3c41d-140">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="3c41d-140">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="3c41d-141">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="3c41d-141">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="3c41d-142">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="3c41d-142">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="3c41d-143">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="3c41d-143">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="3c41d-144">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-144">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="3c41d-145">如果您使用的是 SQL Server 身份验证，则还必须指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="3c41d-145">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="3c41d-146">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-146">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-147">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-147">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-148">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-148">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="3c41d-149">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-149">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-150">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-150">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-151">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-151">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="3c41d-152">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-152">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-153">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-153">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-154">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-154">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### <a name="to-start-the-merge-agent-to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="3c41d-155">启动合并代理以将推送订阅与合并发布进行同步</span><span class="sxs-lookup"><span data-stu-id="3c41d-155">To start the Merge Agent to synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="3c41d-156">通过命令提示符或分发服务器中的批处理文件，执行 **replmerg.exe**。</span><span class="sxs-lookup"><span data-stu-id="3c41d-156">From the command prompt or in a batch file at the Distributor, execute **replmerg.exe**.</span></span> <span data-ttu-id="3c41d-157">指定下列命令行参数：</span><span class="sxs-lookup"><span data-stu-id="3c41d-157">Specify the following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="3c41d-158">**-Publisher**</span><span class="sxs-lookup"><span data-stu-id="3c41d-158">**-Publisher**</span></span>  
  
    -   <span data-ttu-id="3c41d-159">**-PublisherDB**</span><span class="sxs-lookup"><span data-stu-id="3c41d-159">**-PublisherDB**</span></span>  
  
    -   <span data-ttu-id="3c41d-160">**-Publication**</span><span class="sxs-lookup"><span data-stu-id="3c41d-160">**-Publication**</span></span>  
  
    -   <span data-ttu-id="3c41d-161">**-Distributor**</span><span class="sxs-lookup"><span data-stu-id="3c41d-161">**-Distributor**</span></span>  
  
    -   <span data-ttu-id="3c41d-162">**-Subscriber**</span><span class="sxs-lookup"><span data-stu-id="3c41d-162">**-Subscriber**</span></span>  
  
    -   <span data-ttu-id="3c41d-163">**-SubscriberDB**</span><span class="sxs-lookup"><span data-stu-id="3c41d-163">**-SubscriberDB**</span></span>  
  
    -   <span data-ttu-id="3c41d-164">**-SubscriptionType = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-164">**-SubscriptionType = 0**</span></span>  
  
     <span data-ttu-id="3c41d-165">如果您使用的是 SQL Server 身份验证，则还必须指定下列参数：</span><span class="sxs-lookup"><span data-stu-id="3c41d-165">If you are using SQL Server Authentication, you must also specify the following arguments:</span></span>  
  
    -   <span data-ttu-id="3c41d-166">**-DistributorLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-166">**-DistributorLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-167">**-DistributorPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-167">**-DistributorPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-168">**-DistributorSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-168">**-DistributorSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="3c41d-169">**-PublisherLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-169">**-PublisherLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-170">**-PublisherPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-170">**-PublisherPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-171">**-PublisherSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-171">**-PublisherSecurityMode = 0**</span></span>  
  
    -   <span data-ttu-id="3c41d-172">**-SubscriberLogin**</span><span class="sxs-lookup"><span data-stu-id="3c41d-172">**-SubscriberLogin**</span></span>  
  
    -   <span data-ttu-id="3c41d-173">**-SubscriberPassword**</span><span class="sxs-lookup"><span data-stu-id="3c41d-173">**-SubscriberPassword**</span></span>  
  
    -   <span data-ttu-id="3c41d-174">**-SubscriberSecurityMode = 0**</span><span class="sxs-lookup"><span data-stu-id="3c41d-174">**-SubscriberSecurityMode = 0**</span></span>  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="examples-replication-agents"></a><a name="TsqlExample"></a> <span data-ttu-id="3c41d-175">示例（复制代理）</span><span class="sxs-lookup"><span data-stu-id="3c41d-175">Examples (Replication Agents)</span></span>  
 <span data-ttu-id="3c41d-176">以下示例启动分发代理以同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-176">The following example starts the Distribution Agent to synchronize a push subscription.</span></span>  
  
 
```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4
```
  
 <span data-ttu-id="3c41d-177">以下示例启动合并代理以同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-177">The following example starts the Merge Agent to synchronize a push subscription.</span></span>  

```
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1
```
  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="3c41d-178">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="3c41d-178">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="3c41d-179">可以使用复制管理对象 (RMO) 和托管代码的复制代理功能访问权限以编程方式同步推送订阅。</span><span class="sxs-lookup"><span data-stu-id="3c41d-179">You can synchronize push subscriptions programmatically by using Replication Management Objects (RMO) and managed code access to replication agent functionalities.</span></span> <span data-ttu-id="3c41d-180">用于同步推送订阅的类取决于订阅所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="3c41d-180">The classes that you use to synchronize a push subscription depend on the type of publication to which the subscription belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c41d-181">如果您要启动一个自主运行而不影响应用程序的订阅，请异步启动代理。</span><span class="sxs-lookup"><span data-stu-id="3c41d-181">If you want to start a synchronization that runs autonomously without affecting your application, start the agent asynchronously.</span></span> <span data-ttu-id="3c41d-182">但是，如果您要监视同步的结果并在同步进程期间从代理处接收回调（例如，您要显示进度栏），则应当同步启动代理。</span><span class="sxs-lookup"><span data-stu-id="3c41d-182">However, if you want to monitor the outcome of the synchronization and receive callbacks from the agent during the synchronization process (for example, if you want to display a progress bar), you should start the agent synchronously.</span></span> <span data-ttu-id="3c41d-183">对于 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] 订阅服务器，必须同步启动代理。</span><span class="sxs-lookup"><span data-stu-id="3c41d-183">For [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] Subscribers, you must start the agent synchronously.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="3c41d-184">将推送订阅与快照发布或事务发布进行同步</span><span class="sxs-lookup"><span data-stu-id="3c41d-184">To synchronize a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="3c41d-185">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="3c41d-185">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="3c41d-186">创建 <xref:Microsoft.SqlServer.Replication.TransSubscription> 类的实例并设置下列属性：</span><span class="sxs-lookup"><span data-stu-id="3c41d-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class and set the following properties:</span></span>  
  
    -   <span data-ttu-id="3c41d-187">用于 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>的发布数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-187">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-188">用于 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>的订阅所属的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-188">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-189">用于 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>的订阅数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-189">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-190">用于 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>的订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-190">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-191">在步骤 1 中为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>创建的连接。</span><span class="sxs-lookup"><span data-stu-id="3c41d-191">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="3c41d-192">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以获取其他订阅属性。</span><span class="sxs-lookup"><span data-stu-id="3c41d-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="3c41d-193">如果该方法返回 `false`，则确保订阅存在。</span><span class="sxs-lookup"><span data-stu-id="3c41d-193">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="3c41d-194">使用下列方法之一在分发服务器中启动分发代理：</span><span class="sxs-lookup"><span data-stu-id="3c41d-194">Start the Distribution Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="3c41d-195">在步骤 2 中的 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> 实例上调用 <xref:Microsoft.SqlServer.Replication.TransSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-195">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.TransSubscription> from step 2.</span></span> <span data-ttu-id="3c41d-196">该方法异步启动分发代理，并在代理作业运行时立即将控制权返回给您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3c41d-196">This method starts the Distribution Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="3c41d-197">如果创建的订阅的 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 的值为 `false`，则不能调用该方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-197">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-198">获取 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> 属性中 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> 类的实例，然后调用 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-198">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="3c41d-199">该方法可以同步启动代理，并且控制权仍属于运行代理作业。</span><span class="sxs-lookup"><span data-stu-id="3c41d-199">This method starts the agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="3c41d-200">在执行同步期间，您可以在代理仍旧运行的情况下处理 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="3c41d-200">During synchronous execution you can handle the <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
#### <a name="to-synchronize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="3c41d-201">将推送订阅与合并发布进行同步</span><span class="sxs-lookup"><span data-stu-id="3c41d-201">To synchronize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="3c41d-202">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与分发服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="3c41d-202">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="3c41d-203">创建 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 类的实例并设置下列属性：</span><span class="sxs-lookup"><span data-stu-id="3c41d-203">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="3c41d-204">用于 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>的发布数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-204">The publication database name for <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-205">用于 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>的订阅所属的发布的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-205">The name of the publication to which the subscription belongs for <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-206">用于 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>的订阅数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-206">The name of the subscription database for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-207">用于 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>的订阅服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="3c41d-207">The name of the Subscriber for <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-208">在步骤 1 中为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>创建的连接。</span><span class="sxs-lookup"><span data-stu-id="3c41d-208">The connection created in step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="3c41d-209">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以获取其他订阅属性。</span><span class="sxs-lookup"><span data-stu-id="3c41d-209">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the remaining subscription properties.</span></span> <span data-ttu-id="3c41d-210">如果该方法返回 `false`，则确保订阅存在。</span><span class="sxs-lookup"><span data-stu-id="3c41d-210">If this method returns `false`, verify that the subscription exists.</span></span>  
  
4.  <span data-ttu-id="3c41d-211">使用下列方法之一在分发服务器中启动合并代理：</span><span class="sxs-lookup"><span data-stu-id="3c41d-211">Start the Merge Agent at the Distributor in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="3c41d-212">在步骤 2 中的 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> 实例上调用 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-212">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> method on the instance of <xref:Microsoft.SqlServer.Replication.MergeSubscription> from step 2.</span></span> <span data-ttu-id="3c41d-213">该方法异步启动合并代理，并在代理作业运行时立即将控制权返回给您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3c41d-213">This method starts the Merge Agent asynchronously, and control immediately returns to your application while the agent job is running.</span></span> <span data-ttu-id="3c41d-214">如果创建的订阅的 <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> 的值为 `false`，则不能调用该方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-214">You cannot call this method if the subscription was created with a value of `false` for <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.</span></span>  
  
    -   <span data-ttu-id="3c41d-215">获取 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> 属性中 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> 类的实例，然后调用 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3c41d-215">Obtain an instance of the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> class from the <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> property, and call the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> method.</span></span> <span data-ttu-id="3c41d-216">该方法可以同步启动合并代理，并且控件仍属于运行代理作业。</span><span class="sxs-lookup"><span data-stu-id="3c41d-216">This method starts the Merge Agent synchronously, and control remains with the running agent job.</span></span> <span data-ttu-id="3c41d-217">在执行同步期间，您可以在代理仍旧运行的情况下处理 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> 事件。</span><span class="sxs-lookup"><span data-stu-id="3c41d-217">During synchronous execution, you can handle the <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> event while the agent is running.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="3c41d-218">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="3c41d-218">Examples (RMO)</span></span>  
 <span data-ttu-id="3c41d-219">该示例将推送订阅与事务发布进行同步，其中，代理使用代理作业进行异步启动。</span><span class="sxs-lookup"><span data-stu-id="3c41d-219">This example synchronizes a push subscription to a transactional publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 <span data-ttu-id="3c41d-220">该示例将推送订阅与事务发布进行同步，其中，代理进行同步启动。</span><span class="sxs-lookup"><span data-stu-id="3c41d-220">This example synchronizes a push subscription to a transactional publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 <span data-ttu-id="3c41d-221">该示例将推送订阅与合并发布进行同步，其中，代理使用代理作业进行异步启动。</span><span class="sxs-lookup"><span data-stu-id="3c41d-221">This example synchronizes a push subscription to a merge publication, where the agent is started asynchronously using the agent job.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 <span data-ttu-id="3c41d-222">该示例将推送订阅与合并发布进行同步，其中，代理进行同步启动。</span><span class="sxs-lookup"><span data-stu-id="3c41d-222">This example synchronizes a push subscription to a merge publication, where the agent is started synchronously.</span></span>  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="3c41d-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c41d-223">See Also</span></span>  
 <span data-ttu-id="3c41d-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="3c41d-224">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="3c41d-225">[同步数据](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="3c41d-225">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="3c41d-226">复制安全最佳做法</span><span class="sxs-lookup"><span data-stu-id="3c41d-226">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
