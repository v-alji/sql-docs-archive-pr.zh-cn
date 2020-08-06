---
title: 可用性副本之间的会话期间的可能故障 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server, HADR]
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], troubleshooting
ms.assetid: cd613898-82d9-482f-a255-0230a6c7d6fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4cfacb7f7c75875d4f5d0b0b435d282b3f537cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690805"
---
# <a name="possible-failures-during-sessions-between-availability-replicas-sql-server"></a><span data-ttu-id="deb47-102">可用性副本之间的会话期间的可能故障 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="deb47-102">Possible Failures During Sessions Between Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="deb47-103">物理故障、操作系统故障或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障都可能导致两个可用性副本之间的会话失败。</span><span class="sxs-lookup"><span data-stu-id="deb47-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] problems can cause a failure in a session between two availability replicas.</span></span> <span data-ttu-id="deb47-104">可用性副本不会定期检查 Sqlservr.exe 所依赖的组件来验证这些组件是在正常运行还是已出现故障。</span><span class="sxs-lookup"><span data-stu-id="deb47-104">An availability replica does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="deb47-105">但对于某些类型的故障，受影响的组件将向 Sqlservr.exe 报告错误。</span><span class="sxs-lookup"><span data-stu-id="deb47-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="deb47-106">由另一个组件报告的错误称为“硬错误 ”。</span><span class="sxs-lookup"><span data-stu-id="deb47-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="deb47-107">为了检测可能忽略的其他故障，[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]实施了自己的会话超时机制。</span><span class="sxs-lookup"><span data-stu-id="deb47-107">To detect other failures that would otherwise go unnoticed, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements its own session-timeout mechanism.</span></span> <span data-ttu-id="deb47-108">以秒为单位指定会话超时期限。</span><span class="sxs-lookup"><span data-stu-id="deb47-108">Specifies the session-timeout period in seconds.</span></span> <span data-ttu-id="deb47-109">此超时期限是一个服务器实例在考虑断开另一实例的连接之前，等待接收来自该实例的 PING 消息的最长时间。</span><span class="sxs-lookup"><span data-stu-id="deb47-109">This time-out period is the maximum time that a server instance waits to receive a PING message from another instance before considering that other instance to be disconnected.</span></span> <span data-ttu-id="deb47-110">两个可用性副本之间发生会话超时时，可用性副本将假定已发生故障并声明一个“软错误 \*\*”。</span><span class="sxs-lookup"><span data-stu-id="deb47-110">When a session timeout occurs between two availability replicas, the availability replicas assume that a failure has occurred and declares a *soft error*.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="deb47-111">无法检测到主数据库之外的数据库中的故障。</span><span class="sxs-lookup"><span data-stu-id="deb47-111">Failures in databases other than the primary database are not detectable.</span></span> <span data-ttu-id="deb47-112">此外，也不太可能检测到数据磁盘故障，除非数据库因为数据磁盘故障而重新启动。</span><span class="sxs-lookup"><span data-stu-id="deb47-112">Moreover, a data disk failure is unlikely to be detected unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="deb47-113">错误检测的速度以及由此决定的对故障的反应时间取决于是硬错误还是软错误。</span><span class="sxs-lookup"><span data-stu-id="deb47-113">The speed of error detection and, therefore, the reaction time to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="deb47-114">系统可以立即报告某些硬错误，例如网络故障。</span><span class="sxs-lookup"><span data-stu-id="deb47-114">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="deb47-115">但在某些情况下，特定于组件的超时期限可能会延迟报告某些硬错误。</span><span class="sxs-lookup"><span data-stu-id="deb47-115">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="deb47-116">对于软错误，会话超时期限的长度决定了错误检测的速度。</span><span class="sxs-lookup"><span data-stu-id="deb47-116">For soft errors, the length of the session-timeout period determines the speed of error detection.</span></span> <span data-ttu-id="deb47-117">默认情况下，此期限为 10 秒钟。</span><span class="sxs-lookup"><span data-stu-id="deb47-117">By default, this period is 10 seconds.</span></span> <span data-ttu-id="deb47-118">这是建议的最小值。</span><span class="sxs-lookup"><span data-stu-id="deb47-118">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="deb47-119">硬错误导致的故障</span><span class="sxs-lookup"><span data-stu-id="deb47-119">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="deb47-120">可能的硬错误原因包括（但不限于）下列几种情况：</span><span class="sxs-lookup"><span data-stu-id="deb47-120">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="deb47-121">连接或网线断开</span><span class="sxs-lookup"><span data-stu-id="deb47-121">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="deb47-122">网卡出现故障</span><span class="sxs-lookup"><span data-stu-id="deb47-122">A bad network card</span></span>  
  
-   <span data-ttu-id="deb47-123">路由器更改</span><span class="sxs-lookup"><span data-stu-id="deb47-123">A router change</span></span>  
  
-   <span data-ttu-id="deb47-124">防火墙更改</span><span class="sxs-lookup"><span data-stu-id="deb47-124">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="deb47-125">端点重新配置</span><span class="sxs-lookup"><span data-stu-id="deb47-125">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="deb47-126">事务日志驻留的驱动器丢失</span><span class="sxs-lookup"><span data-stu-id="deb47-126">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="deb47-127">操作系统或进程故障</span><span class="sxs-lookup"><span data-stu-id="deb47-127">Operating system or process failure</span></span>  
  
 <span data-ttu-id="deb47-128">例如，如果主数据库中的日志驱动器停止响应或失败，操作系统会通知 Sqlservr.exe 出现严重错误。</span><span class="sxs-lookup"><span data-stu-id="deb47-128">For example, when the log drive on the primary database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="deb47-129">某些组件（如网络组件和某些 IO 子系统）使用它们自己的超时设置来确定故障。</span><span class="sxs-lookup"><span data-stu-id="deb47-129">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="deb47-130">这些超时设置独立于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，后者不了解它们，并且完全不能识别其行为。</span><span class="sxs-lookup"><span data-stu-id="deb47-130">Such time-outs are independent of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="deb47-131">在这些情况下，超时延迟会延长发生故障与可用性副本收到所引发硬错误之间的时间。</span><span class="sxs-lookup"><span data-stu-id="deb47-131">In these cases, the time-out delay increases the time between a failure and when the availability replica receives the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="deb47-132">仅在出现软错误时，才对可用性副本执行有效的错误检查。</span><span class="sxs-lookup"><span data-stu-id="deb47-132">The only active error checking performed for availability replicas occurs for soft error cases.</span></span> <span data-ttu-id="deb47-133">有关详细信息，请参阅本主题后面的“软错误导致的故障”。</span><span class="sxs-lookup"><span data-stu-id="deb47-133">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="deb47-134">若要了解网络出现的错误情况，请咨询网络工程师，询问当 TCP 连接发生下列事件时，哪些错误消息会发送到端口：</span><span class="sxs-lookup"><span data-stu-id="deb47-134">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="deb47-135">DNS 未运行。</span><span class="sxs-lookup"><span data-stu-id="deb47-135">DNS is not working.</span></span>  
  
-   <span data-ttu-id="deb47-136">网线被拔掉。</span><span class="sxs-lookup"><span data-stu-id="deb47-136">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="deb47-137">Windows 防火墙阻止了特定端口。</span><span class="sxs-lookup"><span data-stu-id="deb47-137">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="deb47-138">监视端口的应用程序出现故障。</span><span class="sxs-lookup"><span data-stu-id="deb47-138">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="deb47-139">重命名基于 Windows 的服务器。</span><span class="sxs-lookup"><span data-stu-id="deb47-139">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="deb47-140">重新启动基于 Windows 的服务器。</span><span class="sxs-lookup"><span data-stu-id="deb47-140">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssHADRc](../../../includes/sshadrc-md.md)]<span data-ttu-id="deb47-141">无法避免与客户端访问服务器相关的问题。</span><span class="sxs-lookup"><span data-stu-id="deb47-141">does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="deb47-142">例如，假设由公用网络适配器处理与主副本的客户端连接，而由专用网络接口卡处理承载可用性组的副本的服务器实例之间的所有通信流量。</span><span class="sxs-lookup"><span data-stu-id="deb47-142">For example, consider a case in which a public network adapter handles client connections to the primary replica, while a private network interface card handles traffic among the server instances that are hosting the replicas of an availability group.</span></span> <span data-ttu-id="deb47-143">此时，公用网络适配器的故障将阻止客户端访问数据库。</span><span class="sxs-lookup"><span data-stu-id="deb47-143">In this case, failure of the public network adapter would prevent clients from accessing the databases.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="deb47-144">软错误导致的故障</span><span class="sxs-lookup"><span data-stu-id="deb47-144">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="deb47-145">可能导致会话超时的情况包括（但不限于）下列各项：</span><span class="sxs-lookup"><span data-stu-id="deb47-145">Conditions that might cause session timeouts include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="deb47-146">诸如 TCP 链接超时、数据包被删除或损坏或数据包顺序错误等网络错误。</span><span class="sxs-lookup"><span data-stu-id="deb47-146">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="deb47-147">不响应的操作系统、服务器或数据库。</span><span class="sxs-lookup"><span data-stu-id="deb47-147">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="deb47-148">Windows 服务器超时。</span><span class="sxs-lookup"><span data-stu-id="deb47-148">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="deb47-149">计算资源不足，例如 CPU 或磁盘超负荷运转，事务日志填满，或系统用完内存或线程。</span><span class="sxs-lookup"><span data-stu-id="deb47-149">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="deb47-150">在这些情况下，需要增加超时期限、降低工作负荷或更换硬件以处理相应的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="deb47-150">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-session-timeout-mechanism"></a><span data-ttu-id="deb47-151">会话超时机制</span><span class="sxs-lookup"><span data-stu-id="deb47-151">The Session-Timeout Mechanism</span></span>  
 <span data-ttu-id="deb47-152">由于软错误不能由服务器实例直接检测到，因此，软错误可能导致一个可用性副本无限期等待会话中另一个可用性副本的响应。</span><span class="sxs-lookup"><span data-stu-id="deb47-152">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause an availability replica to wait indefinitely for a response from the other availability replica in a session.</span></span> <span data-ttu-id="deb47-153">为了防止发生这种情况， [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实施了会话超时机制，此机制基于以下条件：所连接的可用性副本会在每个打开的连接上按固定间隔发送 ping。</span><span class="sxs-lookup"><span data-stu-id="deb47-153">To prevent this, [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implements a session time-out mechanism, based on the connected availability replicas sending out a ping on each open connection at a fixed interval.</span></span> <span data-ttu-id="deb47-154">在超时期限内收到 ping 指示连接仍是开放的，且服务器实例正在通过此连接进行通信。</span><span class="sxs-lookup"><span data-stu-id="deb47-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="deb47-155">收到 ping 后，副本将重置此连接上的超时计数器。</span><span class="sxs-lookup"><span data-stu-id="deb47-155">On receiving a ping, a replica resets its time-out counter on that connection.</span></span> <span data-ttu-id="deb47-156">有关可用性模式和会话超时的关系的信息，请参阅[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="deb47-156">For information about the relationship of availability mode and session timeouts, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="deb47-157">主副本和辅助副本相互 ping 以指示它们仍处于活动状态，会话超时限制防止一个副本无限期等待接收另一个副本的 ping。</span><span class="sxs-lookup"><span data-stu-id="deb47-157">The primary and secondary replicas ping each other to signal that they are still active, and a session-timeout limit prevents either replica from waiting indefinitely to receive a ping from the other replica.</span></span> <span data-ttu-id="deb47-158">会话超时限制是用户可配置的副本属性，默认值为 10 秒。</span><span class="sxs-lookup"><span data-stu-id="deb47-158">The session-timeout limit is a user-configurable replica property with a default value of 10 seconds.</span></span> <span data-ttu-id="deb47-159">在超时期限内收到 ping 指示连接仍是开放的，且服务器实例正在通过此连接进行通信。</span><span class="sxs-lookup"><span data-stu-id="deb47-159">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="deb47-160">收到 ping 后，可用性副本将重置此连接的超时计数器。</span><span class="sxs-lookup"><span data-stu-id="deb47-160">On receiving a ping, an availability replica resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="deb47-161">如果在会话超时期限内没有收到来自另一个副本的 ping，则连接将超时。连接已关闭，超时的副本进入断开连接状态。</span><span class="sxs-lookup"><span data-stu-id="deb47-161">If no ping is received from the other replica within the session-timeout period, the connection times out. The connection is closed, and the timed-out replica enters the DISCONNECTED state.</span></span> <span data-ttu-id="deb47-162">即使为同步提交模式配置了断开连接的副本，事务也将不等待该副本重新连接和重新同步。</span><span class="sxs-lookup"><span data-stu-id="deb47-162">Even if a disconnected replica is configured for synchronous-commit mode, transactions will not wait for that replica to reconnect and resynchronize.</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="deb47-163">响应错误</span><span class="sxs-lookup"><span data-stu-id="deb47-163">Responding to an Error</span></span>  
 <span data-ttu-id="deb47-164">无论出现何种错误类型，检测到错误的服务器都会根据实例的角色、会话可用性模式以及会话中任何其他连接的状态做出相应的响应。</span><span class="sxs-lookup"><span data-stu-id="deb47-164">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the availability mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="deb47-165">有关丢失伙伴后会发生的情况的信息，请参阅[可用性模式 (AlwaysOn 可用性组) ](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="deb47-165">For information about what occurs on the loss of a partner, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="deb47-166">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="deb47-166">Related Tasks</span></span>  
 <span data-ttu-id="deb47-167">**更改超时值（仅限同步提交可用性模式）**</span><span class="sxs-lookup"><span data-stu-id="deb47-167">**To change the time-out value (synchronous-commit availability mode only)**</span></span>  
  
-   [<span data-ttu-id="deb47-168">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="deb47-168">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="deb47-169">**查看当前超时值**</span><span class="sxs-lookup"><span data-stu-id="deb47-169">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="deb47-170">查询 [sys.availability_replicas（Transact-SQL）](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)中的 **session_timeout**。</span><span class="sxs-lookup"><span data-stu-id="deb47-170">Query **session_timeout** in [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb47-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="deb47-171">See Also</span></span>  
 [<span data-ttu-id="deb47-172">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="deb47-172">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
