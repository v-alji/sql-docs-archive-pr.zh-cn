---
title: 订阅，未分发的命令 (事务订阅，SQL Server 2005 及更高版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bbd82b4f4855c99076404d8b621edca11a7e1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689326"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a><span data-ttu-id="5cab2-102">订阅，未分发的命令（事务订阅，SQL Server 2005 和更高版本）</span><span class="sxs-lookup"><span data-stu-id="5cab2-102">Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="5cab2-103">**“未分发的命令”** 选项卡显示分发数据库中尚未传递到所选订阅服务器的命令数的相关信息，以及传递这些命令的估计时间。</span><span class="sxs-lookup"><span data-stu-id="5cab2-103">The **Undistributed Commands** tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="5cab2-104">有关查看分发数据库中的命令的信息，请参阅 [sp_replshowcmds (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5cab2-104">For information about viewing the commands in the distribution database, see [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5cab2-105">选项</span><span class="sxs-lookup"><span data-stu-id="5cab2-105">Options</span></span>  
 <span data-ttu-id="5cab2-106">**分发数据库中等待应用于此订阅服务器的命令数**</span><span class="sxs-lookup"><span data-stu-id="5cab2-106">**Number of commands in the distribution database waiting to be applied to this Subscriber**</span></span>  
 <span data-ttu-id="5cab2-107">在分发数据库中尚未传递到所选订阅服务器的命令数。</span><span class="sxs-lookup"><span data-stu-id="5cab2-107">The number of commands in the distribution database that have not been delivered to the selected Subscriber.</span></span> <span data-ttu-id="5cab2-108">一个命令由一个 Transact-SQL 数据操作语言 (DML) 语句或一个数据定义语言 (DDL) 语句组成。</span><span class="sxs-lookup"><span data-stu-id="5cab2-108">A command consists of one Transact-SQL data manipulation language (DML) statement or one data definition language (DDL) statement.</span></span>  
  
 <span data-ttu-id="5cab2-109">**根据过去的性能估计应用这些命令所需的时间为**</span><span class="sxs-lookup"><span data-stu-id="5cab2-109">**Estimated time to apply these commands, based on past performance**</span></span>  
 <span data-ttu-id="5cab2-110">将命令传递到订阅服务器所需的估计时间。</span><span class="sxs-lookup"><span data-stu-id="5cab2-110">The estimated amount of time to deliver commands to the Subscriber.</span></span> <span data-ttu-id="5cab2-111">如果此值大于生成快照并将其应用于订阅服务器所需的时间，请考虑重新初始化订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="5cab2-111">If this value is greater than the amount of time required to generate and apply a snapshot to the Subscriber, consider reinitializing the Subscriber.</span></span> <span data-ttu-id="5cab2-112">有关详细信息，请参阅 [重新初始化订阅](reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="5cab2-112">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cab2-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5cab2-113">See Also</span></span>  
 <span data-ttu-id="5cab2-114">[启动复制监视器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5cab2-114">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="5cab2-115">[用复制监视器监视性能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="5cab2-115">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 [<span data-ttu-id="5cab2-116">监视复制</span><span class="sxs-lookup"><span data-stu-id="5cab2-116">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
