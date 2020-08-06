---
title: 数据库镜像期间可能出现的故障 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- time-out period [SQL Server database mirroring]
- soft errors [SQL Server]
- database mirroring [SQL Server], troubleshooting
- timeout errors [SQL Server]
- troubleshooting [SQL Server], database mirroring
- hard errors
- failed database mirroring sessions [SQL Server]
ms.assetid: d7031f58-5f49-4e6d-9a62-9b420f2bb17e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 25ba1ccc87c024fa3da370f2ff19251a1bee9f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690127"
---
# <a name="possible-failures-during-database-mirroring"></a><span data-ttu-id="509c3-102">Possible Failures During Database Mirroring</span><span class="sxs-lookup"><span data-stu-id="509c3-102">Possible Failures During Database Mirroring</span></span>
  <span data-ttu-id="509c3-103">物理故障、操作系统故障或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障都可能导致数据库镜像会话失败。</span><span class="sxs-lookup"><span data-stu-id="509c3-103">Physical, operating system, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problems can cause a failure in a database mirroring session.</span></span> <span data-ttu-id="509c3-104">数据库镜像不会定期检查 Sqlservr.exe 所依赖的组件来验证组件是在正常运行还是已出现故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-104">Database mirroring does not regularly check the components on which Sqlservr.exe relies to verify whether they are functioning correctly or have failed.</span></span> <span data-ttu-id="509c3-105">但对于某些类型的故障，受影响的组件将向 Sqlservr.exe 报告错误。</span><span class="sxs-lookup"><span data-stu-id="509c3-105">However, for some types of failures, the affected component reports an error to Sqlservr.exe.</span></span> <span data-ttu-id="509c3-106">由另一个组件报告的错误称为“硬错误 ”。</span><span class="sxs-lookup"><span data-stu-id="509c3-106">An error reported by another component is called a *hard error*.</span></span> <span data-ttu-id="509c3-107">为了检测可能未被注意的其他故障，数据库镜像采用了自己的超时机制。</span><span class="sxs-lookup"><span data-stu-id="509c3-107">To detect other failures that would otherwise go unnoticed, database mirroring implements its own time-out mechanism.</span></span> <span data-ttu-id="509c3-108">发生镜像超时时，数据库镜像假定已发生故障并声明一个“软错误”。</span><span class="sxs-lookup"><span data-stu-id="509c3-108">When a mirroring time-out occurs, database mirroring assumes that a failure has occurred and declares a *soft error*.</span></span> <span data-ttu-id="509c3-109">然而，某些在 SQL Server 实例级别发生的故障不会导致镜像超时，并且检测不到。</span><span class="sxs-lookup"><span data-stu-id="509c3-109">However, some failures that happen at the SQL Server instance level do not cause mirroring to time-out and can go undetected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="509c3-110">在数据库镜像会话中无法检测到数据库（除镜像数据库之外）故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-110">Failures in databases other than the mirrored database are not detectable in a database mirroring session.</span></span> <span data-ttu-id="509c3-111">此外，也无法检测到数据磁盘故障，除非数据库因为数据磁盘故障而重新启动。</span><span class="sxs-lookup"><span data-stu-id="509c3-111">Moreover, a data disk failure is unlikely to be detected, unless the database is restarted because of a data disk failure.</span></span>  
  
 <span data-ttu-id="509c3-112">因此，错误检测的速度以及镜像会话对故障的反应时间取决于是硬错误还是软错误。</span><span class="sxs-lookup"><span data-stu-id="509c3-112">The speed of error detection and, therefore, the reaction time of the mirroring session to a failure, depends on whether the error is hard or soft.</span></span> <span data-ttu-id="509c3-113">系统可以立即报告某些硬错误，例如网络故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-113">Some hard errors, such as network failures are reported immediately.</span></span> <span data-ttu-id="509c3-114">但在某些情况下，特定于组件的超时期限可能会延迟报告某些硬错误。</span><span class="sxs-lookup"><span data-stu-id="509c3-114">However, in some cases, component-specific time-out periods can delay the reporting of some hard errors.</span></span> <span data-ttu-id="509c3-115">对于软错误，镜像超时期限的长度决定了错误检测的速度。</span><span class="sxs-lookup"><span data-stu-id="509c3-115">For soft errors, the length of the mirroring time-out period determines the speed of error detection.</span></span> <span data-ttu-id="509c3-116">默认情况下，此期限为 10 秒钟。</span><span class="sxs-lookup"><span data-stu-id="509c3-116">By default, this period is 10 seconds.</span></span> <span data-ttu-id="509c3-117">这是建议的最小值。</span><span class="sxs-lookup"><span data-stu-id="509c3-117">This is the minimum recommended value.</span></span>  
  
## <a name="failures-due-to-hard-errors"></a><span data-ttu-id="509c3-118">硬错误导致的故障</span><span class="sxs-lookup"><span data-stu-id="509c3-118">Failures Due to Hard Errors</span></span>  
 <span data-ttu-id="509c3-119">可能的硬错误原因包括（但不限于）下列几种情况：</span><span class="sxs-lookup"><span data-stu-id="509c3-119">Possible causes of hard errors include (but are not limited to) the following conditions:</span></span>  
  
-   <span data-ttu-id="509c3-120">连接或网线断开</span><span class="sxs-lookup"><span data-stu-id="509c3-120">A broken connection or wire</span></span>  
  
-   <span data-ttu-id="509c3-121">网卡出现故障</span><span class="sxs-lookup"><span data-stu-id="509c3-121">A bad network card</span></span>  
  
-   <span data-ttu-id="509c3-122">路由器更改</span><span class="sxs-lookup"><span data-stu-id="509c3-122">A router change</span></span>  
  
-   <span data-ttu-id="509c3-123">防火墙更改</span><span class="sxs-lookup"><span data-stu-id="509c3-123">Changes in the firewall</span></span>  
  
-   <span data-ttu-id="509c3-124">端点重新配置</span><span class="sxs-lookup"><span data-stu-id="509c3-124">Endpoint reconfiguration</span></span>  
  
-   <span data-ttu-id="509c3-125">事务日志驻留的驱动器丢失</span><span class="sxs-lookup"><span data-stu-id="509c3-125">Loss of the drive where the transaction log resides</span></span>  
  
-   <span data-ttu-id="509c3-126">操作系统或进程故障</span><span class="sxs-lookup"><span data-stu-id="509c3-126">Operating system or process failure</span></span>  
  
 <span data-ttu-id="509c3-127">例如，如果主体数据库中的日志驱动器停止响应或失败，操作系统会通知 Sqlservr.exe 出现严重错误。</span><span class="sxs-lookup"><span data-stu-id="509c3-127">For example, when the log drive on the principal database becomes unresponsive and fails, the operating system informs Sqlservr.exe that a serious error has occurred.</span></span>  
  
 <span data-ttu-id="509c3-128">某些组件（如网络组件和某些 IO 子系统）使用它们自己的超时设置来确定故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-128">Some components, such as network components and some IO subsystems, have their own time-outs to determine failures.</span></span> <span data-ttu-id="509c3-129">这些超时设置独立于数据库镜像，数据库镜像不了解它们，并且完全不能识别其行为。</span><span class="sxs-lookup"><span data-stu-id="509c3-129">Such time-outs are independent of database mirroring, which has no knowledge of them and is completely unaware of their behavior.</span></span> <span data-ttu-id="509c3-130">在这些情况下，超时延迟会延长发生故障与数据库镜像收到所引发硬错误之间的时间。</span><span class="sxs-lookup"><span data-stu-id="509c3-130">In these cases, the time-out delay increases the time between a failure and when database mirroring receive the resulting hard error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="509c3-131">出现软错误时，仅对数据库镜像执行活动的错误检查。</span><span class="sxs-lookup"><span data-stu-id="509c3-131">The only active error checking performed for database mirroring occurs for soft error cases.</span></span> <span data-ttu-id="509c3-132">有关详细信息，请参阅本主题后面的“软错误导致的故障”。</span><span class="sxs-lookup"><span data-stu-id="509c3-132">For more information, see "Failures Due to Soft Errors," later in this topic.</span></span>  
  
 <span data-ttu-id="509c3-133">若要了解网络出现的错误情况，请咨询网络工程师，询问当 TCP 连接发生下列事件时，哪些错误消息会发送到端口：</span><span class="sxs-lookup"><span data-stu-id="509c3-133">To help you interpret the error conditions that occur on the network, ask a network engineer what error messages are sent to a port when the following events occur on a TCP connection:</span></span>  
  
-   <span data-ttu-id="509c3-134">DNS 未运行。</span><span class="sxs-lookup"><span data-stu-id="509c3-134">DNS is not working.</span></span>  
  
-   <span data-ttu-id="509c3-135">网线被拔掉。</span><span class="sxs-lookup"><span data-stu-id="509c3-135">Cables are unplugged.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="509c3-136">Windows 防火墙阻止了特定端口。</span><span class="sxs-lookup"><span data-stu-id="509c3-136">Windows has a firewall that blocks a specific port.</span></span>  
  
-   <span data-ttu-id="509c3-137">监视端口的应用程序出现故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-137">The application that is monitoring a port fails.</span></span>  
  
-   <span data-ttu-id="509c3-138">重命名基于 Windows 的服务器。</span><span class="sxs-lookup"><span data-stu-id="509c3-138">A Windows-based server is renamed.</span></span>  
  
-   <span data-ttu-id="509c3-139">重新启动基于 Windows 的服务器。</span><span class="sxs-lookup"><span data-stu-id="509c3-139">A Windows-based server is rebooted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="509c3-140">镜像无法避免与客户端访问服务器相关的问题。</span><span class="sxs-lookup"><span data-stu-id="509c3-140">Mirroring does not protect against problems specific to client accessing the servers.</span></span> <span data-ttu-id="509c3-141">例如，假设由公用网络适配器处理与主体服务器实例的客户端连接，而由专用网络接口卡处理服务器实例之间的所有镜像通信流量。</span><span class="sxs-lookup"><span data-stu-id="509c3-141">For example, consider a case in which a public network adapter handles client connections to the principal server instance, while a private network interface card handles all mirroring traffic among server instances.</span></span> <span data-ttu-id="509c3-142">此时，尽管数据库可以继续进行镜像，但公用网络适配器的故障将防止客户端访问数据库。</span><span class="sxs-lookup"><span data-stu-id="509c3-142">In this case, failure of the public network adapter would prevent clients from accessing the database, though the database would continue to be mirrored.</span></span>  
  
## <a name="failures-due-to-soft-errors"></a><span data-ttu-id="509c3-143">软错误导致的故障</span><span class="sxs-lookup"><span data-stu-id="509c3-143">Failures Due to Soft Errors</span></span>  
 <span data-ttu-id="509c3-144">导致镜像超时的情况包括（但不限于）下列各项：</span><span class="sxs-lookup"><span data-stu-id="509c3-144">Conditions that might cause mirroring time-outs include (but are not limited to) the following:</span></span>  
  
-   <span data-ttu-id="509c3-145">诸如 TCP 链接超时、数据包被删除或损坏或数据包顺序错误等网络错误。</span><span class="sxs-lookup"><span data-stu-id="509c3-145">Network errors such as TCP link time-outs, dropped or corrupted packets, or packets that are in an incorrect order.</span></span>  
  
-   <span data-ttu-id="509c3-146">不响应的操作系统、服务器或数据库。</span><span class="sxs-lookup"><span data-stu-id="509c3-146">An operating system, server, or database that is not responding.</span></span>  
  
-   <span data-ttu-id="509c3-147">Windows 服务器超时。</span><span class="sxs-lookup"><span data-stu-id="509c3-147">A Windows server timing out.</span></span>  
  
-   <span data-ttu-id="509c3-148">计算资源不足，例如 CPU 或磁盘超负荷运转，事务日志填满，或系统用完内存或线程。</span><span class="sxs-lookup"><span data-stu-id="509c3-148">Insufficient computing resources, such as a CPU or disk overload, the transaction log filling up, or the system is running out of memory or threads.</span></span> <span data-ttu-id="509c3-149">在这些情况下，需要增加超时期限、降低工作负荷或更换硬件以处理相应的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="509c3-149">In these cases, you must increase the time-out period, reduce the workload, or change the hardware to handle the workload.</span></span>  
  
### <a name="the-mirroring-time-out-mechanism"></a><span data-ttu-id="509c3-150">镜像超时机制</span><span class="sxs-lookup"><span data-stu-id="509c3-150">The Mirroring Time-Out Mechanism</span></span>  
 <span data-ttu-id="509c3-151">由于软错误不能由服务器实例直接检测到，因此，软错误可能导致服务器实例无限期等待。</span><span class="sxs-lookup"><span data-stu-id="509c3-151">Because soft errors are not detectable directly by a server instance, a soft error could potentially cause a server instance to wait indefinitely.</span></span> <span data-ttu-id="509c3-152">为了防止发生这种情况，数据库镜像采用了它自己的超时机制，此机制基于镜像会话中的每个服务器实例会在每个开放连接上按固定间隔发送 ping。</span><span class="sxs-lookup"><span data-stu-id="509c3-152">To prevent this, database mirroring implements its own time-out mechanism, based on each server instance in a mirroring session sending out a ping on each open connection at a fixed interval.</span></span>  
  
 <span data-ttu-id="509c3-153">为了使连接保持开放，服务器实例必须能够在超时期限内在该连接上接收到 ping，此期限为定义的镜像超时时间再加上再发送一个 ping 所需的时间。</span><span class="sxs-lookup"><span data-stu-id="509c3-153">To keep a connection open, a server instance must receive a ping on that connection in the time-out period defined, plus the time that is required to send one more ping.</span></span> <span data-ttu-id="509c3-154">在超时期限内收到 ping 指示连接仍是开放的，且服务器实例正在通过此连接进行通信。</span><span class="sxs-lookup"><span data-stu-id="509c3-154">Receiving a ping during the time-out period indicates that the connection is still open and that the server instances are communicating over it.</span></span> <span data-ttu-id="509c3-155">接收到 ping 后，服务器实例将重置此连接上的超时计数器。</span><span class="sxs-lookup"><span data-stu-id="509c3-155">On receiving a ping, a server instance resets its time-out counter on that connection.</span></span>  
  
 <span data-ttu-id="509c3-156">如果未在超时期限内从此连接上收到 ping，则服务器实例认为此连接已超时。服务器实例将关闭超时连接，然后根据会话的状态和运行模式处理超时事件。</span><span class="sxs-lookup"><span data-stu-id="509c3-156">If no ping is received on a connection during the time-out period, a server instance considers the connection to have timed out. The server instance closes the timed-out connection and handles the time-out event according to the state and operating mode of the session.</span></span>  
  
 <span data-ttu-id="509c3-157">即使其他服务器实际工作正常，超时也被认为是一个故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-157">Even if the other server is actually proceeding correctly, a time-out is considered a failure.</span></span> <span data-ttu-id="509c3-158">如果会话的超时值太短而不能使任一伙伴做出正常响应，则会产生虚假故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-158">If the time-out value for a session is too short for the regular responsiveness of either partner, false failures can occur.</span></span> <span data-ttu-id="509c3-159">如果一个服务器实例成功地与另一个服务器实例实现通信，但后者的响应时间太短，以致于无法在超时期限过期之前接收到 ping，则会产生错误故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-159">A false failure occurs when one server instance successfully contacts another whose response time is so slow that its pings are not received before the time-out period expires.</span></span>  
  
 <span data-ttu-id="509c3-160">在高性能模式会话中，超时期限始终为 10 秒钟。</span><span class="sxs-lookup"><span data-stu-id="509c3-160">In high-performance mode sessions, the time-out period is always 10 seconds.</span></span> <span data-ttu-id="509c3-161">通常，该期限足以避免虚假故障。</span><span class="sxs-lookup"><span data-stu-id="509c3-161">This is generally enough to avoid false failures.</span></span> <span data-ttu-id="509c3-162">在高安全性模式会话中，默认超时期限为 10 秒钟，但您可以更改该持续时间。</span><span class="sxs-lookup"><span data-stu-id="509c3-162">In high-safety mode sessions, the default time-out period is 10 seconds, but you can change the duration.</span></span> <span data-ttu-id="509c3-163">为了避免虚假故障，建议镜像超时期限始终为 10 秒钟或更长。</span><span class="sxs-lookup"><span data-stu-id="509c3-163">To avoid false failures, we recommend that the mirroring time-out period always be 10 seconds or more.</span></span>  
  
 <span data-ttu-id="509c3-164">**更改超时值（仅限于高安全性模式）**</span><span class="sxs-lookup"><span data-stu-id="509c3-164">**To change the time-out value (high-safety mode only)**</span></span>  
  
-   <span data-ttu-id="509c3-165">使用 [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="509c3-165">Use the [ALTER DATABASE \<database> SET PARTNER TIMEOUT \<integer>](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="509c3-166">**查看当前超时值**</span><span class="sxs-lookup"><span data-stu-id="509c3-166">**To view the current time-out value**</span></span>  
  
-   <span data-ttu-id="509c3-167">在 **sys.database_mirroring** 中查询 [mirroring_connection_timeout](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="509c3-167">Query **mirroring_connection_timeout** in [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
## <a name="responding-to-an-error"></a><span data-ttu-id="509c3-168">响应错误</span><span class="sxs-lookup"><span data-stu-id="509c3-168">Responding to an Error</span></span>  
 <span data-ttu-id="509c3-169">无论出现何种错误类型，检测到错误的服务器都会根据实例的角色、会话运行模式以及会话中任何其他连接的状态做出相应的响应。</span><span class="sxs-lookup"><span data-stu-id="509c3-169">Regardless of the type of error, a server instance that detects an error responds appropriately based on the role of the instance, the operating mode of the session, and the state of any other connection in the session.</span></span> <span data-ttu-id="509c3-170">有关丢失伙伴后会发生的情况的信息，请参阅 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="509c3-170">For information about what occurs on the loss of a partner, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509c3-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="509c3-171">See Also</span></span>  
 <span data-ttu-id="509c3-172">[估计在角色切换期间服务的中断（数据库镜像）](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="509c3-172">[Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md) </span></span>  
 <span data-ttu-id="509c3-173">[数据库镜像运行模式](database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="509c3-173">[Database Mirroring Operating Modes](database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="509c3-174">[数据库镜像会话期间的角色切换 (SQL Server)](role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="509c3-174">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="509c3-175">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="509c3-175">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
