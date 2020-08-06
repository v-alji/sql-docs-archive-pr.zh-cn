---
title: blocked process threshold 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9d5b61aaf23a8e74cb11afbf4e8bdb958fde6abe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691873"
---
# <a name="blocked-process-threshold-server-configuration-option"></a><span data-ttu-id="4c88a-102">blocked process threshold 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="4c88a-102">blocked process threshold Server Configuration Option</span></span>
  <span data-ttu-id="4c88a-103">**blocked process threshold** 选项用于指定阈值（以秒为单位），超过该阈值将生成阻塞的进程报告。</span><span class="sxs-lookup"><span data-stu-id="4c88a-103">Use the **blocked process threshold** option to specify the threshold, in seconds, at which blocked process reports are generated.</span></span> <span data-ttu-id="4c88a-104">该阈值可介于 0 到 86,400 之间。</span><span class="sxs-lookup"><span data-stu-id="4c88a-104">The threshold can be set from 0 to 86,400.</span></span> <span data-ttu-id="4c88a-105">默认情况下，不生成阻塞的进程报告。</span><span class="sxs-lookup"><span data-stu-id="4c88a-105">By default, no blocked process reports are produced.</span></span> <span data-ttu-id="4c88a-106">对于系统任务或正在等待未生成可检测死锁的资源的任务，不生成该事件。</span><span class="sxs-lookup"><span data-stu-id="4c88a-106">This event is not generated for system tasks or for tasks that are waiting on resources that do not generate detectable deadlocks.</span></span>  
  
 <span data-ttu-id="4c88a-107">可以定义一个生成该事件时执行的 [警报](../../ssms/agent/alerts.md) 。</span><span class="sxs-lookup"><span data-stu-id="4c88a-107">You can define an [alert](../../ssms/agent/alerts.md) to be executed when this event is generated.</span></span> <span data-ttu-id="4c88a-108">例如，可以选择通知管理员采取相应的操作来处理阻塞情况。</span><span class="sxs-lookup"><span data-stu-id="4c88a-108">So for example, you can choose to page the administrator to take appropriate action to handle the blocking situation.</span></span>  
  
 <span data-ttu-id="4c88a-109">阻塞的进程阈值使用死锁监视器后台线程监视等待时间大于（或数倍于）配置的阈值的任务列表。</span><span class="sxs-lookup"><span data-stu-id="4c88a-109">Blocked process threshold uses the deadlock monitor background thread to walk through the list of tasks waiting for a time greater than or multiples of the configured threshold.</span></span> <span data-ttu-id="4c88a-110">每个报告间隔中，为每个阻塞的任务生成一次事件。</span><span class="sxs-lookup"><span data-stu-id="4c88a-110">The event is generated once per reporting interval for each of the blocked tasks.</span></span>  
  
 <span data-ttu-id="4c88a-111">已通过最大努力完成了阻塞的进程报告。</span><span class="sxs-lookup"><span data-stu-id="4c88a-111">The blocked process report is done on a best effort basis.</span></span> <span data-ttu-id="4c88a-112">不保证报表的数据始终为实时数据，也不保证报表数据接近实时。</span><span class="sxs-lookup"><span data-stu-id="4c88a-112">There is no guarantee of any real-time or even close to real-time reporting.</span></span>  
  
 <span data-ttu-id="4c88a-113">该设置立即生效，无需停止并重新启动服务器。</span><span class="sxs-lookup"><span data-stu-id="4c88a-113">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4c88a-114">示例</span><span class="sxs-lookup"><span data-stu-id="4c88a-114">Examples</span></span>  
 <span data-ttu-id="4c88a-115">下面的示例将 `blocked process threshold` 设置为 `20` 秒，超过该阈值将为阻塞的每个任务生成阻塞的进程报告。</span><span class="sxs-lookup"><span data-stu-id="4c88a-115">The following example sets the `blocked process threshold` to `20` seconds, generating a blocked process report for each task that is blocked.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c88a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c88a-116">See Also</span></span>  
 <span data-ttu-id="4c88a-117">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4c88a-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="4c88a-118">Blocked Process Report 事件类</span><span class="sxs-lookup"><span data-stu-id="4c88a-118">Blocked Process Report Event Class</span></span>](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
