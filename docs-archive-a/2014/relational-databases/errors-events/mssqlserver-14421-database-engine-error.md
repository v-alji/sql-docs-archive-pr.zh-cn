---
title: MSSQLSERVER_14421 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14421 (Database Engine error)
ms.assetid: 03e76d4a-d463-4673-8843-08e4ecaefe27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d6bc793911797c334d87238ec46531f7afbf63ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589654"
---
# <a name="mssqlserver_14421"></a><span data-ttu-id="02d12-102">MSSQLSERVER_14421</span><span class="sxs-lookup"><span data-stu-id="02d12-102">MSSQLSERVER_14421</span></span>
    
## <a name="details"></a><span data-ttu-id="02d12-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="02d12-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02d12-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="02d12-104">Product Name</span></span>|<span data-ttu-id="02d12-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="02d12-105">SQL Server</span></span>|  
|<span data-ttu-id="02d12-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="02d12-106">Event ID</span></span>|<span data-ttu-id="02d12-107">14421</span><span class="sxs-lookup"><span data-stu-id="02d12-107">14421</span></span>|  
|<span data-ttu-id="02d12-108">事件源</span><span class="sxs-lookup"><span data-stu-id="02d12-108">Event Source</span></span>|<span data-ttu-id="02d12-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="02d12-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="02d12-110">组件</span><span class="sxs-lookup"><span data-stu-id="02d12-110">Component</span></span>|<span data-ttu-id="02d12-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="02d12-111">SQLEngine</span></span>|  
|<span data-ttu-id="02d12-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="02d12-112">Symbolic Name</span></span>|<span data-ttu-id="02d12-113">SQLErrorNum14421</span><span class="sxs-lookup"><span data-stu-id="02d12-113">SQLErrorNum14421</span></span>|  
|<span data-ttu-id="02d12-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="02d12-114">Message Text</span></span>|<span data-ttu-id="02d12-115">日志传送辅助数据库 %s.%s 的还原阈值为 %d 分钟，并且现在不同步。在过去的 %d 分钟之内未执行任何还原操作。</span><span class="sxs-lookup"><span data-stu-id="02d12-115">The log shipping secondary database %s.%s has restore threshold of %d minutes and is out of sync. No restore was performed for %d minutes.</span></span> <span data-ttu-id="02d12-116">还原操作滞后了 %d 分钟。</span><span class="sxs-lookup"><span data-stu-id="02d12-116">Restored latency is %d minutes.</span></span> <span data-ttu-id="02d12-117">请查看代理日志和日志传送监视器信息。</span><span class="sxs-lookup"><span data-stu-id="02d12-117">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02d12-118">说明</span><span class="sxs-lookup"><span data-stu-id="02d12-118">Explanation</span></span>  
 <span data-ttu-id="02d12-119">此消息指出日志传送在超出还原阈值的情况下不同步。</span><span class="sxs-lookup"><span data-stu-id="02d12-119">This message indicates that log shipping is out of synchronization beyond the restore threshold.</span></span> <span data-ttu-id="02d12-120">还原阈值是生成消息之前在还原操作之间允许等待的分钟数。</span><span class="sxs-lookup"><span data-stu-id="02d12-120">The restore threshold is the number of minutes that can elapse between restore operations before a message is generated.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="02d12-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="02d12-121">Possible Causes</span></span>  
 <span data-ttu-id="02d12-122">此消息并不一定表示日志传送存在问题。</span><span class="sxs-lookup"><span data-stu-id="02d12-122">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="02d12-123">相反，此消息可能表示存在以下问题之一：</span><span class="sxs-lookup"><span data-stu-id="02d12-123">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="02d12-124">还原作业未运行。</span><span class="sxs-lookup"><span data-stu-id="02d12-124">The restore job is not running.</span></span>  
  
     <span data-ttu-id="02d12-125">导致作业未运行的可能原因包括：辅助服务器实例上的 SQL Server 代理服务未运行、作业被禁用或作业计划已更改。</span><span class="sxs-lookup"><span data-stu-id="02d12-125">Possible causes of the job not running include the following: the SQL Server Agent service on the secondary server instance is not running, the job is disabled, or the schedule of the job has been changed.</span></span>  
  
-   <span data-ttu-id="02d12-126">还原作业失败。</span><span class="sxs-lookup"><span data-stu-id="02d12-126">The restore job is failing.</span></span>  
  
     <span data-ttu-id="02d12-127">导致作业失败的可能原因包括：还原文件夹路径无效、磁盘已满或可能导致 RESTORE 语句失败的其他任何原因。</span><span class="sxs-lookup"><span data-stu-id="02d12-127">Possible causes of the job failing include the following: the restore folder path is not valid, the disk is full, or any other reason that the RESTORE statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02d12-128">用户操作</span><span class="sxs-lookup"><span data-stu-id="02d12-128">User Action</span></span>  
 <span data-ttu-id="02d12-129">排除错误消息</span><span class="sxs-lookup"><span data-stu-id="02d12-129">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="02d12-130">确保辅助服务器实例的 SQL Server 代理服务处于运行状态，同时启用了该辅助数据库的还原作业并安排它以适当的频率运行。</span><span class="sxs-lookup"><span data-stu-id="02d12-130">Make sure that the SQL Server Agent service is running for the secondary server instance and that the restore job for this secondary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="02d12-131">辅助服务器上的还原作业可能失败。</span><span class="sxs-lookup"><span data-stu-id="02d12-131">The restore job on the secondary server might be failing.</span></span> <span data-ttu-id="02d12-132">在这种情况下，请查看还原作业的作业历史记录以寻找原因。</span><span class="sxs-lookup"><span data-stu-id="02d12-132">In this case, check the job history for the restore job to look for the cause.</span></span>  
  
-   <span data-ttu-id="02d12-133">在辅助服务器实例上运行的日志传送还原作业可能无法连接到监视服务器实例以更新 **log_shipping_monitor_secondary** 表。</span><span class="sxs-lookup"><span data-stu-id="02d12-133">The log shipping restore job, which runs on the secondary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_secondary** table.</span></span> <span data-ttu-id="02d12-134">这可能是由于监视服务器实例和辅助服务器实例之间的身份验证问题引起的。</span><span class="sxs-lookup"><span data-stu-id="02d12-134">This might be caused by an authentication problem between the monitor server instance and the secondary server instance.</span></span>  
  
-   <span data-ttu-id="02d12-135">备份警报阈值可能包含错误的值。</span><span class="sxs-lookup"><span data-stu-id="02d12-135">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="02d12-136">理想情况下，至少将该值设置为还原作业频率的三倍。</span><span class="sxs-lookup"><span data-stu-id="02d12-136">Ideally, this value is set to at least three times the frequency of the restore job.</span></span> <span data-ttu-id="02d12-137">如果在配置了日志传送并使之起作用之后更改了还原作业的频率，则必须相应地更新备份警报阈值的值。</span><span class="sxs-lookup"><span data-stu-id="02d12-137">If you change the frequency of the restore job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="02d12-138">当监视服务器实例离线并重新在线时，在警报消息作业运行之前不会使用当前值更新 **log_shipping_monitor_secondary** 表。</span><span class="sxs-lookup"><span data-stu-id="02d12-138">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_secondary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="02d12-139">还原作业虽然成功但显示消息“找不到可以应用到辅助数据库的日志备份文件”时，可能引发错误 14421。</span><span class="sxs-lookup"><span data-stu-id="02d12-139">Error 14421 can be raised when a restore job succeeds with, "Could not find a log backup file that could be applied to secondary database."</span></span> <span data-ttu-id="02d12-140">出现这种情况时，将不更新还原时间。</span><span class="sxs-lookup"><span data-stu-id="02d12-140">When this occurs, the restore time is not updated.</span></span> <span data-ttu-id="02d12-141">在这种情况下，错误原因可能是复制作业存在问题。</span><span class="sxs-lookup"><span data-stu-id="02d12-141">The cause of the error in this case might be an issue with the copy job.</span></span>  
  
     <span data-ttu-id="02d12-142">若要使用辅助数据库的最新数据更新监视表，请在辅助服务器实例上运行 **sp_refresh_log_shipping_monitor**。</span><span class="sxs-lookup"><span data-stu-id="02d12-142">To update the monitor tables with the latest data for the secondary database, run **sp_refresh_log_shipping_monitor** on the secondary server instance.</span></span>  
  
-   <span data-ttu-id="02d12-143">在辅助服务器实例或监视服务器实例上，日期或时间不正确。</span><span class="sxs-lookup"><span data-stu-id="02d12-143">On the secondary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="02d12-144">这也可能生成警报消息。</span><span class="sxs-lookup"><span data-stu-id="02d12-144">This may also generate alert messages.</span></span> <span data-ttu-id="02d12-145">可能在其中一个服务器实例上修改了系统日期或时间。</span><span class="sxs-lookup"><span data-stu-id="02d12-145">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="02d12-146">两个服务器实例的时区不同不会引发问题。</span><span class="sxs-lookup"><span data-stu-id="02d12-146">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d12-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02d12-147">See Also</span></span>  
 <span data-ttu-id="02d12-148">[log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="02d12-148">[log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="02d12-149">[关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02d12-149">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="02d12-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="02d12-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="02d12-151">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="02d12-151">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="02d12-152">关于日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="02d12-152">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
