---
title: MSSQLSERVER_14420 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a17ab1e2281530b06c9ad27ac2a31672de0681e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580290"
---
# <a name="mssqlserver_14420"></a><span data-ttu-id="87683-102">MSSQLSERVER_14420</span><span class="sxs-lookup"><span data-stu-id="87683-102">MSSQLSERVER_14420</span></span>
    
## <a name="details"></a><span data-ttu-id="87683-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="87683-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87683-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="87683-104">Product Name</span></span>|<span data-ttu-id="87683-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="87683-105">SQL Server</span></span>|  
|<span data-ttu-id="87683-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="87683-106">Event ID</span></span>|<span data-ttu-id="87683-107">14420</span><span class="sxs-lookup"><span data-stu-id="87683-107">14420</span></span>|  
|<span data-ttu-id="87683-108">事件源</span><span class="sxs-lookup"><span data-stu-id="87683-108">Event Source</span></span>|<span data-ttu-id="87683-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="87683-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="87683-110">组件</span><span class="sxs-lookup"><span data-stu-id="87683-110">Component</span></span>|<span data-ttu-id="87683-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="87683-111">SQLEngine</span></span>|  
|<span data-ttu-id="87683-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="87683-112">Symbolic Name</span></span>|<span data-ttu-id="87683-113">SQLErrorNum14420</span><span class="sxs-lookup"><span data-stu-id="87683-113">SQLErrorNum14420</span></span>|  
|<span data-ttu-id="87683-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="87683-114">Message Text</span></span>|<span data-ttu-id="87683-115">日志传送主数据库 %s.%s 的备份阈值为 %d 分钟，在过去的 %d 分钟之内未执行备份日志操作。</span><span class="sxs-lookup"><span data-stu-id="87683-115">The log shipping primary database %s.%s has backup threshold of %d minutes and has not performed a backup log operation for %d minutes.</span></span> <span data-ttu-id="87683-116">请查看代理日志和日志传送监视器信息。</span><span class="sxs-lookup"><span data-stu-id="87683-116">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="87683-117">说明</span><span class="sxs-lookup"><span data-stu-id="87683-117">Explanation</span></span>  
 <span data-ttu-id="87683-118">日志传送在超出备份阈值的情况下不同步。</span><span class="sxs-lookup"><span data-stu-id="87683-118">Log shipping is out of synchronization beyond the backup threshold.</span></span> <span data-ttu-id="87683-119">备份阈值是生成警报之前在日志传送备份作业之间允许等待的分钟数。</span><span class="sxs-lookup"><span data-stu-id="87683-119">The backup threshold is the number of minutes that are allowed to elapse between log-shipping backup jobs before an alert is generated.</span></span> <span data-ttu-id="87683-120">此消息并不一定表示日志传送存在问题。</span><span class="sxs-lookup"><span data-stu-id="87683-120">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="87683-121">相反，此消息可能表示存在以下问题之一：</span><span class="sxs-lookup"><span data-stu-id="87683-121">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="87683-122">备份作业未运行。</span><span class="sxs-lookup"><span data-stu-id="87683-122">The backup job is not running.</span></span> <span data-ttu-id="87683-123">导致此问题的可能原因包括：主服务器实例上的 SQL Server 代理服务未运行、作业被禁用或作业的计划已更改。</span><span class="sxs-lookup"><span data-stu-id="87683-123">Possible causes for this include the following: the SQL Server Agent service on the primary server instance is not running, the job is disabled, or the job's schedule has been changed.</span></span>  
  
-   <span data-ttu-id="87683-124">备份作业失败。</span><span class="sxs-lookup"><span data-stu-id="87683-124">The backup job is failing.</span></span> <span data-ttu-id="87683-125">导致此问题的可能原因包括：备份文件夹路径无效、磁盘已满或可能导致 BACKUP 语句失败的其他任何原因。</span><span class="sxs-lookup"><span data-stu-id="87683-125">Possible causes for this include the following: the backup folder path is not valid, the disk is full, or any other reason that the BACKUP statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="87683-126">用户操作</span><span class="sxs-lookup"><span data-stu-id="87683-126">User Action</span></span>  
 <span data-ttu-id="87683-127">排除错误消息</span><span class="sxs-lookup"><span data-stu-id="87683-127">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="87683-128">确保主服务器实例的 SQL Server 代理服务处于运行状态，同时启用了该主数据库的备份作业并安排它以适当的频率运行。</span><span class="sxs-lookup"><span data-stu-id="87683-128">Make sure that the SQL Server Agent service is running for the primary server instance and that the backup job for this primary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="87683-129">主服务器上的备份作业可能失败。</span><span class="sxs-lookup"><span data-stu-id="87683-129">The backup job on the primary server might be failing.</span></span> <span data-ttu-id="87683-130">在这种情况下，请查看备份作业的作业历史记录以寻找原因。</span><span class="sxs-lookup"><span data-stu-id="87683-130">In this case, examine the job history for the backup job to look for the cause.</span></span>  
  
-   <span data-ttu-id="87683-131">在主服务器实例上运行的日志传送备份作业可能无法连接到监视服务器实例以更新 **log_shipping_monitor_primary** 表。</span><span class="sxs-lookup"><span data-stu-id="87683-131">The log shipping backup job, which runs on the primary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_primary** table.</span></span> <span data-ttu-id="87683-132">这可能是由于监视服务器实例和主服务器实例之间的身份验证问题引起的。</span><span class="sxs-lookup"><span data-stu-id="87683-132">This could be caused by an authentication problem between the monitor server instance and the primary server instance.</span></span>  
  
-   <span data-ttu-id="87683-133">备份警报阈值可能包含错误的值。</span><span class="sxs-lookup"><span data-stu-id="87683-133">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="87683-134">理想情况下，至少将该值设置为备份作业频率的三倍。</span><span class="sxs-lookup"><span data-stu-id="87683-134">Ideally, this value is set to at least three times the frequency of the backup job.</span></span> <span data-ttu-id="87683-135">如果在配置了日志传送并使之起作用之后更改了备份作业的频率，则必须相应地更新备份警报阈值的值。</span><span class="sxs-lookup"><span data-stu-id="87683-135">If you change the frequency of the backup job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="87683-136">当监视服务器实例离线并重新在线时，在警报消息作业运行之前不会使用当前值更新 **log_shipping_monitor_primary** 表。</span><span class="sxs-lookup"><span data-stu-id="87683-136">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_primary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="87683-137">若要使用主数据库的最新数据更新监视表，请在主服务器实例上运行 **sp_refresh_log_shipping_monitor**。</span><span class="sxs-lookup"><span data-stu-id="87683-137">To update the monitor tables with the latest data for the primary database, run **sp_refresh_log_shipping_monitor** on the primary server instance.</span></span>  
  
-   <span data-ttu-id="87683-138">在主服务器实例或监视服务器实例上，日期或时间不正确。</span><span class="sxs-lookup"><span data-stu-id="87683-138">On the primary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="87683-139">这也可能生成警报消息。</span><span class="sxs-lookup"><span data-stu-id="87683-139">This may also generate alert messages.</span></span> <span data-ttu-id="87683-140">可能在其中一个服务器实例上修改了系统日期或时间。</span><span class="sxs-lookup"><span data-stu-id="87683-140">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87683-141">两个服务器实例的时区不同不会引发问题。</span><span class="sxs-lookup"><span data-stu-id="87683-141">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87683-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87683-142">See Also</span></span>  
 <span data-ttu-id="87683-143">[log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87683-143">[log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="87683-144">[关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="87683-144">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="87683-145">[sp_help_log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87683-145">[sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="87683-146">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87683-146">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="87683-147">关于日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="87683-147">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
