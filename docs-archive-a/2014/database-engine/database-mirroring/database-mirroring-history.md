---
title: 数据库镜像历史记录 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.databasemirroringhistory.f1
ms.assetid: 1d6e4b10-4a23-47d7-9918-c417992f09d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e32ad9bfdce15413d89fbd5ba3d79a5ef14f7a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589209"
---
# <a name="database-mirroring-history"></a><span data-ttu-id="5fb0e-102">数据库镜像历史记录</span><span class="sxs-lookup"><span data-stu-id="5fb0e-102">Database Mirroring History</span></span>
  <span data-ttu-id="5fb0e-103">使用该对话框可以查看位于指定服务器实例中的镜像数据库的镜像状态历史记录。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-103">Use this dialog box to view the history of mirroring status for a mirrored database on a specified server instance.</span></span>  
  
 <span data-ttu-id="5fb0e-104">**使用 SQL Server Management Studio 监视数据库镜像**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-104">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="5fb0e-105">启动数据库镜像监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5fb0e-105">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="5fb0e-106">选项</span><span class="sxs-lookup"><span data-stu-id="5fb0e-106">Options</span></span>  
 <span data-ttu-id="5fb0e-107">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-107">**Server instance**</span></span>  
 <span data-ttu-id="5fb0e-108">从中报告历史记录的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-108">Name of the server instance from which the history is being reported.</span></span>  
  
 <span data-ttu-id="5fb0e-109">**Database**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-109">**Database**</span></span>  
 <span data-ttu-id="5fb0e-110">正报告其历史记录的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-110">Name of the database whose history is being reported.</span></span>  
  
 <span data-ttu-id="5fb0e-111">**筛选列表依据**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-111">**Filter list by**</span></span>  
 <span data-ttu-id="5fb0e-112">列出筛选器值。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-112">Lists filter values.</span></span> <span data-ttu-id="5fb0e-113">选择新值时将自动刷新网格。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-113">Choosing a new value refreshes the grid automatically.</span></span>  
  
 <span data-ttu-id="5fb0e-114">可能的筛选器值有：</span><span class="sxs-lookup"><span data-stu-id="5fb0e-114">The possible filter values are:</span></span>  
  
-   <span data-ttu-id="5fb0e-115">前两个小时</span><span class="sxs-lookup"><span data-stu-id="5fb0e-115">Last two hours</span></span>  
  
-   <span data-ttu-id="5fb0e-116">前四个小时</span><span class="sxs-lookup"><span data-stu-id="5fb0e-116">Last four hours</span></span>  
  
-   <span data-ttu-id="5fb0e-117">前八个小时</span><span class="sxs-lookup"><span data-stu-id="5fb0e-117">Last eight hours</span></span>  
  
-   <span data-ttu-id="5fb0e-118">前一天</span><span class="sxs-lookup"><span data-stu-id="5fb0e-118">Last day</span></span>  
  
-   <span data-ttu-id="5fb0e-119">前两天</span><span class="sxs-lookup"><span data-stu-id="5fb0e-119">Last two days</span></span>  
  
-   <span data-ttu-id="5fb0e-120">前 100 条记录</span><span class="sxs-lookup"><span data-stu-id="5fb0e-120">Last 100 records</span></span>  
  
-   <span data-ttu-id="5fb0e-121">前 500 条记录</span><span class="sxs-lookup"><span data-stu-id="5fb0e-121">Last 500 records</span></span>  
  
-   <span data-ttu-id="5fb0e-122">前 1000 条记录</span><span class="sxs-lookup"><span data-stu-id="5fb0e-122">Last 1000 records</span></span>  
  
-   <span data-ttu-id="5fb0e-123">所有记录</span><span class="sxs-lookup"><span data-stu-id="5fb0e-123">All records</span></span>  
  
 <span data-ttu-id="5fb0e-124">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-124">**Refresh**</span></span>  
 <span data-ttu-id="5fb0e-125">单击它可刷新历史记录列表。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-125">Click to refresh the history list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fb0e-126">该对话框不自动刷新历史记录列表。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-126">This dialog box does not automatically refresh the history list.</span></span> <span data-ttu-id="5fb0e-127">若要刷新该列表，可单击 **“刷新”** 或选择另一个筛选选项。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-127">To refresh the list, either click **Refresh** or choose another filter option.</span></span> <span data-ttu-id="5fb0e-128">只有 **sysadmin** 固定服务器角色的成员才能更新镜像历史记录。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-128">Only members of the **sysadmin** fixed server role can update the mirroring history.</span></span>  
  
 <span data-ttu-id="5fb0e-129">**History**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-129">**History**</span></span>  
 <span data-ttu-id="5fb0e-130">显示历史记录列表。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-130">Displays the history list.</span></span> <span data-ttu-id="5fb0e-131">单击列标题，可以按该列对网格进行排序。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-131">Clicking on a column header sorts the grid by that column.</span></span> <span data-ttu-id="5fb0e-132">该列表包含以下列：</span><span class="sxs-lookup"><span data-stu-id="5fb0e-132">The list contains the following columns:</span></span>  
  
|<span data-ttu-id="5fb0e-133">列名称</span><span class="sxs-lookup"><span data-stu-id="5fb0e-133">Column name</span></span>|<span data-ttu-id="5fb0e-134">说明</span><span class="sxs-lookup"><span data-stu-id="5fb0e-134">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5fb0e-135">**记录时间**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-135">**Time Recorded**</span></span>|<span data-ttu-id="5fb0e-136">历史记录行的时间戳。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-136">Timestamp of the history row.</span></span>|  
|<span data-ttu-id="5fb0e-137">**角色**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-137">**Role**</span></span>|<span data-ttu-id="5fb0e-138">数据库的服务器实例的当前镜像角色，即主体或镜像。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-138">Current mirroring role of the server instance for this database, either Principal or Mirror.</span></span>|  
|<span data-ttu-id="5fb0e-139">**镜像状态**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-139">**Mirroring State**</span></span>|<span data-ttu-id="5fb0e-140">数据库的状态：</span><span class="sxs-lookup"><span data-stu-id="5fb0e-140">State of the database:</span></span><br /><br /> <span data-ttu-id="5fb0e-141">已断开连接</span><span class="sxs-lookup"><span data-stu-id="5fb0e-141">Disconnected</span></span><br /><br /> <span data-ttu-id="5fb0e-142">正在挂起故障转移</span><span class="sxs-lookup"><span data-stu-id="5fb0e-142">Pending Failover</span></span><br /><br /> <span data-ttu-id="5fb0e-143">Suspended</span><span class="sxs-lookup"><span data-stu-id="5fb0e-143">Suspended</span></span><br /><br /> <span data-ttu-id="5fb0e-144">已同步</span><span class="sxs-lookup"><span data-stu-id="5fb0e-144">Synchronized</span></span><br /><br /> <span data-ttu-id="5fb0e-145">正在同步</span><span class="sxs-lookup"><span data-stu-id="5fb0e-145">Synchronizing</span></span><br /><br /> <span data-ttu-id="5fb0e-146">未知</span><span class="sxs-lookup"><span data-stu-id="5fb0e-146">Unknown</span></span>|  
|<span data-ttu-id="5fb0e-147">**见证服务器连接**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-147">**Witness Connection**</span></span>|<span data-ttu-id="5fb0e-148">见证服务器连接在数据库镜像会话中的状态，即连接或已断开连接。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-148">State of the witness connection in the mirroring session of the database, either Connected or Disconnected.</span></span> <span data-ttu-id="5fb0e-149">如果没有见证服务器，则该值为 NULL。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-149">If there is no witness, the value is NULL.</span></span>|  
|<span data-ttu-id="5fb0e-150">**未发送日志**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-150">**Unsent Log**</span></span>|<span data-ttu-id="5fb0e-151">主体服务器实例上的发送队列中的未发送日志的大小（以 KB 计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-151">Size, in kilobytes (KB), of the unsent log in the send queue on the principal server instance.</span></span>|  
|<span data-ttu-id="5fb0e-152">**发送时间**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-152">**Time to Send**</span></span>|<span data-ttu-id="5fb0e-153">主体服务器实例将当前位于发送队列中的日志发送到镜像服务器实例所需的近似时间量（发送速率）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-153">Approximate amount of time the principal server instance will require to send the log that is currently in the send queue to the mirror server instance (the *send rate*).</span></span> <span data-ttu-id="5fb0e-154">由于传入事务的速率变化很大，因此发送日志的时间只是一个估计值。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-154">Because the rate of incoming transactions can vary significantly, the time to send log is an estimate.</span></span> <span data-ttu-id="5fb0e-155">但是，发送速率对于粗略估计手动故障转移所需的时间非常有用。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-155">However, the send rate can be useful for roughly estimating the time required for a manual failover.</span></span>|  
|<span data-ttu-id="5fb0e-156">**发送速率**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-156">**Send Rate**</span></span>|<span data-ttu-id="5fb0e-157">将事务发送到镜像服务器实例的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-157">Rate at which transactions are being sent to the mirror server instance, in KB per second.</span></span>|  
|<span data-ttu-id="5fb0e-158">**新事务速率**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-158">**New Transaction Rate**</span></span>|<span data-ttu-id="5fb0e-159">将传入事务输入到主体服务器日志的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-159">Rate at which incoming transactions are being entered into the principal's log, in KB per second.</span></span> <span data-ttu-id="5fb0e-160">若要判断镜像是否落后、停滞或赶上，可将值与 **“发送时间”** 值进行比较。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-160">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Time to Send** value.</span></span>|  
|<span data-ttu-id="5fb0e-161">**最早的未发送事务**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-161">**Oldest Unsent Transaction**</span></span>|<span data-ttu-id="5fb0e-162">发送队列中最早的未发送事务的保留时间。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-162">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="5fb0e-163">事务保留时间指示在将事务发送到镜像服务器实例之前将其保留的分钟数。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-163">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="5fb0e-164">该值有助于测量数据丢失的可能性（以时间计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-164">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="5fb0e-165">**未还原日志**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-165">**Unrestored Log**</span></span>|<span data-ttu-id="5fb0e-166">在重做队列中等待的日志量（以 KB 计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-166">The amount of log waiting in the redo queue, in KB.</span></span>|  
|<span data-ttu-id="5fb0e-167">**还原时间**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-167">**Time to Restore**</span></span>|<span data-ttu-id="5fb0e-168">将当前在重做队列中的日志应用于镜像数据库所需的近似分钟数。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-168">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>|  
|<span data-ttu-id="5fb0e-169">**还原速率**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-169">**Restore Rate**</span></span>|<span data-ttu-id="5fb0e-170">将事务还原到镜像数据库的速率（以 KB/秒计）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-170">Rate at which transactions are being restored into the mirror database, in KB per second.</span></span>|  
|<span data-ttu-id="5fb0e-171">**镜像提交开销**</span><span class="sxs-lookup"><span data-stu-id="5fb0e-171">**Mirror Commit Overhead**</span></span>|<span data-ttu-id="5fb0e-172">每个事务平均延迟的毫秒数（仅在同步模式下）。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-172">Average delay per transaction in milliseconds (only in synchronous modes).</span></span> <span data-ttu-id="5fb0e-173">此延迟是主体服务器实例等待镜像服务器实例将事务日志记录写入重做队列时，所发生的开销量。</span><span class="sxs-lookup"><span data-stu-id="5fb0e-173">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fb0e-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fb0e-174">See Also</span></span>  
 <span data-ttu-id="5fb0e-175">[启动数据库镜像监视器 (SQL Server Management Studio)](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5fb0e-175">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="5fb0e-176">[监视数据库镜像 (SQL Server)](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5fb0e-176">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="5fb0e-177">启动配置数据库镜像安全向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5fb0e-177">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
