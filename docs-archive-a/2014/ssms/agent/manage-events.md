---
title: 管理事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ca6d56440b06d285cbb90f8d92325d59a452c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682659"
---
# <a name="manage-events"></a><span data-ttu-id="e6e61-102">管理事件</span><span class="sxs-lookup"><span data-stu-id="e6e61-102">Manage Events</span></span>
  <span data-ttu-id="e6e61-103">可以将达到或超过特定错误严重级别的所有事件消息转发到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e6e61-103">You can forward to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all event messages that meet or exceed a specific error severity level.</span></span> <span data-ttu-id="e6e61-104">这称为“事件转发”\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6e61-104">This is called *event forwarding*.</span></span> <span data-ttu-id="e6e61-105">转发服务器是一台专用服务器，同时也可以是一台主服务器。</span><span class="sxs-lookup"><span data-stu-id="e6e61-105">The forwarding server is a dedicated server that can also be a master server.</span></span> <span data-ttu-id="e6e61-106">可以利用事件转发对一组服务器进行集中警报管理，从而减少负荷较重的服务器的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e6e61-106">You can use event forwarding to centralize alert management for a group of servers, thereby reducing the workload on heavily used servers.</span></span>  
  
 <span data-ttu-id="e6e61-107">如果一台服务器收到另外一组服务器的事件，则接收事件的服务器称为“警报管理服务器”\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6e61-107">When one server receives events for a group of other servers, the server that receives events is called an *alerts management server*.</span></span> <span data-ttu-id="e6e61-108">在多服务器环境下，可以将主服务器指定为警报管理服务器。</span><span class="sxs-lookup"><span data-stu-id="e6e61-108">In a multiserver environment, you designate the master server as the alerts management server.</span></span>  
  
## <a name="advantages-of-using-an-alerts-management-server"></a><span data-ttu-id="e6e61-109">使用警报管理服务器的优点</span><span class="sxs-lookup"><span data-stu-id="e6e61-109">Advantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="e6e61-110">设置警报管理服务器的优势包括：</span><span class="sxs-lookup"><span data-stu-id="e6e61-110">The advantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="e6e61-111">**集中性**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-111">**Centralization**.</span></span> <span data-ttu-id="e6e61-112">可以从单台服务器对多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的事件进行集中控制，并获得这些事件的合并视图。</span><span class="sxs-lookup"><span data-stu-id="e6e61-112">Centralized control and a consolidated view of the events of several instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are possible from a single server.</span></span>  
  
-   <span data-ttu-id="e6e61-113">**可伸缩性**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-113">**Scalability**.</span></span> <span data-ttu-id="e6e61-114">许多物理服务器可以作为一台逻辑服务器来管理。</span><span class="sxs-lookup"><span data-stu-id="e6e61-114">Many physical servers can be administered as one logical server.</span></span> <span data-ttu-id="e6e61-115">可以根据需要在这个物理服务器组中添加或删除服务器。</span><span class="sxs-lookup"><span data-stu-id="e6e61-115">You can add or remove servers to this physical server group as needed.</span></span>  
  
-   <span data-ttu-id="e6e61-116">**效率**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-116">**Efficiency**.</span></span> <span data-ttu-id="e6e61-117">由于只需要定义一次警报和操作员，因此减少了配置时间。</span><span class="sxs-lookup"><span data-stu-id="e6e61-117">Configuration time is reduced, because you need to define alerts and operators only once.</span></span>  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a><span data-ttu-id="e6e61-118">使用警报管理服务器的缺点</span><span class="sxs-lookup"><span data-stu-id="e6e61-118">Disadvantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="e6e61-119">设置警报管理服务器的缺点包括：</span><span class="sxs-lookup"><span data-stu-id="e6e61-119">The disadvantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="e6e61-120">**通信流量增加**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-120">**Increased traffic**.</span></span> <span data-ttu-id="e6e61-121">向警报管理服务器转发事件会增加网络通信流量。</span><span class="sxs-lookup"><span data-stu-id="e6e61-121">Forwarding events to an alerts management server can increase network traffic.</span></span> <span data-ttu-id="e6e61-122">可以通过将事件转发限于超过指定严重级别的事件来缓解这种通信流量增加。</span><span class="sxs-lookup"><span data-stu-id="e6e61-122">This increase can be moderated by restricting event forwarding to events that are above a designated severity level.</span></span>  
  
-   <span data-ttu-id="e6e61-123">**单个故障点**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-123">**Single point of failure**.</span></span> <span data-ttu-id="e6e61-124">如果警报管理服务器离线，则不会为管理的一组服务器中的任何事件发出警报。</span><span class="sxs-lookup"><span data-stu-id="e6e61-124">If the alerts management server goes offline, no alerts are issued for any event on the managed group of servers.</span></span>  
  
-   <span data-ttu-id="e6e61-125">**服务器负载**。</span><span class="sxs-lookup"><span data-stu-id="e6e61-125">**Server load**.</span></span> <span data-ttu-id="e6e61-126">处理转发事件的警报会导致警报管理服务器上的处理负荷增加。</span><span class="sxs-lookup"><span data-stu-id="e6e61-126">Handling alerts for the forwarded events causes an increased processing load on the alerts management server.</span></span>  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a><span data-ttu-id="e6e61-127">警报管理服务器使用准则</span><span class="sxs-lookup"><span data-stu-id="e6e61-127">Guidelines for Using an Alerts Management Server</span></span>  
 <span data-ttu-id="e6e61-128">配置警报管理服务器时，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="e6e61-128">When configuring an alerts management server, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="e6e61-129">为了接收转发的事件，警报管理服务器必须是 SQL Server 的默认实例。</span><span class="sxs-lookup"><span data-stu-id="e6e61-129">In order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="e6e61-130">避免在警报管理服务器上运行非常重要或负荷较重的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e6e61-130">Avoid running critical or heavily used applications on the alerts management server.</span></span>  
  
-   <span data-ttu-id="e6e61-131">针对配置多台服务器共享同一台警报管理服务器时涉及的网络通信流量进行仔细计划。</span><span class="sxs-lookup"><span data-stu-id="e6e61-131">Carefully plan for the network traffic involved in configuring many servers to share the same alerts management server.</span></span> <span data-ttu-id="e6e61-132">如果发生阻塞，应减少特定警报管理服务器管理的服务器的数目。</span><span class="sxs-lookup"><span data-stu-id="e6e61-132">If congestion results, reduce the number of servers that use a particular alerts management server.</span></span>  
  
     <span data-ttu-id="e6e61-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中注册的服务器组成一个列表，作为候选的警报转发服务器。</span><span class="sxs-lookup"><span data-stu-id="e6e61-133">The servers that are registered within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] constitute the list of servers available to be chosen by that server as the alerts-forwarding server.</span></span>  
  
-   <span data-ttu-id="e6e61-134">对于要求有服务器特定的响应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本地实例，定义相应警报，而不是将警报转发给警报管理服务器。</span><span class="sxs-lookup"><span data-stu-id="e6e61-134">Define alerts on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that require a server-specific response, instead of forwarding the alerts to the alerts management server.</span></span>  
  
     <span data-ttu-id="e6e61-135">警报管理服务器将所有向其转发事件消息的服务器当作一个逻辑整体看待。</span><span class="sxs-lookup"><span data-stu-id="e6e61-135">The alerts management server views all the servers forwarding to it as a logical whole.</span></span> <span data-ttu-id="e6e61-136">例如，警报管理服务器响应发自服务器 A 的 605 事件的方式和发自服务器 B 的 605 事件相同。</span><span class="sxs-lookup"><span data-stu-id="e6e61-136">For example, an alerts management server responds in the same way to a 605 event from server A and a 605 event from server B.</span></span>  
  
-   <span data-ttu-id="e6e61-137">配置了警报系统后，定期检查 Microsoft Windows 应用程序日志中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件。</span><span class="sxs-lookup"><span data-stu-id="e6e61-137">After configuring your alert system, periodically check the Microsoft Windows application log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events.</span></span>  
  
     <span data-ttu-id="e6e61-138">警报引擎遇到的失败情况都使用源名称“SQL Server 代理”写入本地 Windows 应用程序日志中。</span><span class="sxs-lookup"><span data-stu-id="e6e61-138">Failure conditions encountered by the alerts engine are written to the local Windows application log with a source name of "SQL Server Agent."</span></span> <span data-ttu-id="e6e61-139">例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理无法按照定义发出电子邮件通知，则应用程序日志会记录一个事件。</span><span class="sxs-lookup"><span data-stu-id="e6e61-139">For example, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent cannot send an e-mail notification as it has been defined, an event is logged in the application log.</span></span>  
  
 <span data-ttu-id="e6e61-140">如果一个本地定义的警报处于禁用状态时，发生了本来会触发该警报的事件，则该事件被转发给警报管理服务器（如果它满足警报转发条件）。</span><span class="sxs-lookup"><span data-stu-id="e6e61-140">If a locally defined alert is inactivated, and an event occurs that would have caused the alert to fire, the event is forwarded to the alerts management server (if it satisfies the alert-forwarding condition).</span></span> <span data-ttu-id="e6e61-141">这种转发允许本地站点的用户按照需要禁用和启用本地替代警报（即同时也在警报管理服务器上定义的本地定义的警报）。</span><span class="sxs-lookup"><span data-stu-id="e6e61-141">This forwarding allows local overrides (alerts defined locally that are also defined on the alerts management server) to be turned off and on as needed by the user at the local site.</span></span> <span data-ttu-id="e6e61-142">您也可以要求总是转发事件，即使它们也是由本地警报处理。</span><span class="sxs-lookup"><span data-stu-id="e6e61-142">You can also request that events always be forwarded, even if they are also handled by local alerts.</span></span>  
  
 <span data-ttu-id="e6e61-143">以下是在多服务器环境中管理事件的常规任务：</span><span class="sxs-lookup"><span data-stu-id="e6e61-143">The following are common tasks for managing events in a multiserver environment:</span></span>  
  
 <span data-ttu-id="e6e61-144">**指定警报管理服务器**</span><span class="sxs-lookup"><span data-stu-id="e6e61-144">**To designate an alerts management server**</span></span>  
  
-   [<span data-ttu-id="e6e61-145">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6e61-145">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="e6e61-146">**定义对警报的响应**</span><span class="sxs-lookup"><span data-stu-id="e6e61-146">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="e6e61-147">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e6e61-147">SQL Server Management Studio</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="e6e61-148">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e6e61-148">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a><span data-ttu-id="e6e61-149">运行事件触发的作业</span><span class="sxs-lookup"><span data-stu-id="e6e61-149">Running Event-Triggered Jobs</span></span>  
 <span data-ttu-id="e6e61-150">可以定义一个响应警报时执行的作业。</span><span class="sxs-lookup"><span data-stu-id="e6e61-150">You can define a job to be executed in response to an alert.</span></span> <span data-ttu-id="e6e61-151">例如，可以执行一个作业，对警报检测出的问题进行更正或做进一步的诊断。</span><span class="sxs-lookup"><span data-stu-id="e6e61-151">For example, you can execute a job that corrects or further diagnoses a problem detected by the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6e61-152">由于作业会导致发生事件，应注意不要创建递归的警报作业循环。</span><span class="sxs-lookup"><span data-stu-id="e6e61-152">Because a job can raise an event, be careful not to create a recursive alert-job loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e61-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6e61-153">See Also</span></span>  
 [<span data-ttu-id="e6e61-154">sys.sys消息 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="e6e61-154">sys.sysmessages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  
