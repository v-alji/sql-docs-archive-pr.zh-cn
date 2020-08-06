---
title: 传输作业任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.f1
helpviewer_keywords:
- Transfer Jobs task [Integration Services]
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d692934d5f7c8c1449b123ee8b9caf1d8bb34744
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576912"
---
# <a name="transfer-jobs-task"></a><span data-ttu-id="6b251-102">传输作业任务</span><span class="sxs-lookup"><span data-stu-id="6b251-102">Transfer Jobs Task</span></span>
  <span data-ttu-id="6b251-103">传输作业任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例之间传输一个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理作业。</span><span class="sxs-lookup"><span data-stu-id="6b251-103">The Transfer Jobs task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6b251-104">传输作业任务可以配置为传输所有作业，或者只传输指定的作业。</span><span class="sxs-lookup"><span data-stu-id="6b251-104">The Transfer Jobs task can be configured to transfer all jobs, or only specified jobs.</span></span> <span data-ttu-id="6b251-105">您还可以指示是否在目标服务器上启用传输的作业。</span><span class="sxs-lookup"><span data-stu-id="6b251-105">You can also indicate whether the transferred jobs are enabled at the destination.</span></span>  
  
 <span data-ttu-id="6b251-106">要传输的作业可能已经存在于目标服务器上。</span><span class="sxs-lookup"><span data-stu-id="6b251-106">The jobs to be transferred may already exist on the destination.</span></span> <span data-ttu-id="6b251-107">传输作业任务可以配置为以下列方式处理现有作业：</span><span class="sxs-lookup"><span data-stu-id="6b251-107">The Transfer Jobs task can be configured to handle existing jobs in the following ways:</span></span>  
  
-   <span data-ttu-id="6b251-108">覆盖现有作业。</span><span class="sxs-lookup"><span data-stu-id="6b251-108">Overwrite existing jobs.</span></span>  
  
-   <span data-ttu-id="6b251-109">如果存在重复作业，则该任务失败。</span><span class="sxs-lookup"><span data-stu-id="6b251-109">Fail the task when duplicate jobs exist.</span></span>  
  
-   <span data-ttu-id="6b251-110">跳过重复作业。</span><span class="sxs-lookup"><span data-stu-id="6b251-110">Skip duplicate jobs.</span></span>  
  
 <span data-ttu-id="6b251-111">在运行时，传输作业任务使用一个或两个 SMO 连接管理器连接到源服务器和目标服务器。</span><span class="sxs-lookup"><span data-stu-id="6b251-111">At run time, the Transfer Jobs task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="6b251-112">SMO 连接管理器与传输作业任务分开进行配置，然后在传输作业任务中引用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="6b251-112">The SMO connection manager is configured separately from the Transfer Jobs task, and then is referenced in the Transfer Jobs task.</span></span> <span data-ttu-id="6b251-113">SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="6b251-113">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="6b251-114">有关详细信息，请参阅 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="6b251-114">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
## <a name="transferring-jobs-between-instances-of-sql-server"></a><span data-ttu-id="6b251-115">在 SQL Server 实例之间传输作业</span><span class="sxs-lookup"><span data-stu-id="6b251-115">Transferring Jobs Between Instances of SQL Server</span></span>  
 <span data-ttu-id="6b251-116">传输作业任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。</span><span class="sxs-lookup"><span data-stu-id="6b251-116">The Transfer Jobs task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="6b251-117">对于使用哪个版本作为源或目标，没有限制。</span><span class="sxs-lookup"><span data-stu-id="6b251-117">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="6b251-118">事件</span><span class="sxs-lookup"><span data-stu-id="6b251-118">Events</span></span>  
 <span data-ttu-id="6b251-119">传输作业任务将引发报告已传输的作业数的信息事件，而且在覆盖作业时还会引发警告事件。</span><span class="sxs-lookup"><span data-stu-id="6b251-119">The Transfer Jobs task raises an information event that reports the number of jobs transferred and a warning event when a job is overwritten.</span></span> <span data-ttu-id="6b251-120">该任务并不报告作业传输的进度，它仅报告 0% 和 100% 完成。</span><span class="sxs-lookup"><span data-stu-id="6b251-120">The task does not report incremental progress of the job transfer; it reports only 0% and 100% completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="6b251-121">执行值</span><span class="sxs-lookup"><span data-stu-id="6b251-121">Execution Value</span></span>  
 <span data-ttu-id="6b251-122">在该任务的 `ExecutionValue` 属性中定义的执行值返回已传输的作业数。</span><span class="sxs-lookup"><span data-stu-id="6b251-122">The execution value, defined in the `ExecutionValue` property of the task, returns the number of jobs that are transferred.</span></span> <span data-ttu-id="6b251-123">通过将用户定义的变量分配给传输作业任务的 `ExecValueVariable` 属性，包中的其他对象就可以访问有关作业传输的信息。</span><span class="sxs-lookup"><span data-stu-id="6b251-123">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Jobs task, information about the job transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="6b251-124">有关详细信息，请参阅 [Integration Services (SSIS) 变量](../integration-services-ssis-variables.md)和[在包中使用变量](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="6b251-124">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="6b251-125">日志项</span><span class="sxs-lookup"><span data-stu-id="6b251-125">Log Entries</span></span>  
 <span data-ttu-id="6b251-126">传输作业任务包括下列自定义日志项：</span><span class="sxs-lookup"><span data-stu-id="6b251-126">The Transfer Jobs task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="6b251-127">TransferJobsTaskStarTransferringObjects   此日志项报告传输已经开始。</span><span class="sxs-lookup"><span data-stu-id="6b251-127">TransferJobsTaskStarTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="6b251-128">日志项包括开始时间。</span><span class="sxs-lookup"><span data-stu-id="6b251-128">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="6b251-129">TransferJobsTaskFinishedTransferringObjects    此日志项报告传输已经完成。</span><span class="sxs-lookup"><span data-stu-id="6b251-129">TransferJobsTaskFinishedTransferringObjects    This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="6b251-130">日志项包括结束时间。</span><span class="sxs-lookup"><span data-stu-id="6b251-130">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="6b251-131">此外，还有 `OnInformation` 事件的日志项（报告已传输的作业数），以及 `OnWarning` 事件的日志项（是为目标服务器上每个被覆盖的作业写入的）。</span><span class="sxs-lookup"><span data-stu-id="6b251-131">In addition, a log entry for the `OnInformation` event reports the number of jobs that were transferred and a log entry for the `OnWarning` event is written for each job on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="6b251-132">安全和权限</span><span class="sxs-lookup"><span data-stu-id="6b251-132">Security and Permissions</span></span>  
 <span data-ttu-id="6b251-133">若要传输作业，用户必须是 sysadmin 固定服务器角色的成员，或者是同时位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的源实例和目标实例上的 msdb 数据库的固定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="6b251-133">To transfer jobs, the user must be a member of the sysadmin fixed server role or one of the fixed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles on the msdb database on the both the source and destination instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="configuration-of-the-transfer-jobs-task"></a><span data-ttu-id="6b251-134">传输作业任务的配置</span><span class="sxs-lookup"><span data-stu-id="6b251-134">Configuration of the Transfer Jobs Task</span></span>  
 <span data-ttu-id="6b251-135">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="6b251-135">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6b251-136">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="6b251-136">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="6b251-137">传输作业任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="6b251-137">Transfer Jobs Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="6b251-138">传输作业任务编辑器（“作业”页）</span><span class="sxs-lookup"><span data-stu-id="6b251-138">Transfer Jobs Task Editor &#40;Jobs Page&#41;</span></span>](../transfer-jobs-task-editor-jobs-page.md)  
  
-   [<span data-ttu-id="6b251-139">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="6b251-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="6b251-140">有关以编程方式设置这些属性的信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="6b251-140">For information about programmatically setting these properties, click the of the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="6b251-141">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6b251-141">Related Tasks</span></span>  
 <span data-ttu-id="6b251-142">有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：</span><span class="sxs-lookup"><span data-stu-id="6b251-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="6b251-143">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="6b251-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b251-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b251-144">See Also</span></span>  
 <span data-ttu-id="6b251-145">[Integration Services 任务](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="6b251-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="6b251-146">控制流</span><span class="sxs-lookup"><span data-stu-id="6b251-146">Control Flow</span></span>](control-flow.md)  
  
  
