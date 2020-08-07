---
title: 轮询服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6370e53083d2cf818e8c8b09752d49e092755a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588235"
---
# <a name="poll-servers"></a><span data-ttu-id="2d498-102">轮询服务器</span><span class="sxs-lookup"><span data-stu-id="2d498-102">Poll Servers</span></span>
  <span data-ttu-id="2d498-103">实现多服务器管理后，目标服务器将定期联系主服务器以上载有关已执行的作业的信息，并下载新的作业。</span><span class="sxs-lookup"><span data-stu-id="2d498-103">When multiserver administration is implemented, target servers periodically contact the master server to upload information on jobs that have been executed, and download new jobs.</span></span> <span data-ttu-id="2d498-104">联系主服务器的过程称为服务器轮询**，该过程按定期的轮询间隔** 发生。</span><span class="sxs-lookup"><span data-stu-id="2d498-104">The process of contacting the master server is called *server polling,* which takes place at regular *polling intervals.*</span></span>  
  
## <a name="polling-intervals"></a><span data-ttu-id="2d498-105">轮询间隔</span><span class="sxs-lookup"><span data-stu-id="2d498-105">Polling Intervals</span></span>  
 <span data-ttu-id="2d498-106">轮询间隔（默认情况下为一分钟）控制目标服务器连接到主服务器以下载指令并上载作业执行结果的频率。</span><span class="sxs-lookup"><span data-stu-id="2d498-106">The polling interval (one minute by default) controls how frequently the target server connects to the master server to download instructions and upload the results of job execution.</span></span>  
  
 <span data-ttu-id="2d498-107">当目标服务器轮询主服务器时，它从 **msdb** 数据库的 **sysdownloadlist** 表中读取分配给目标服务器的操作。</span><span class="sxs-lookup"><span data-stu-id="2d498-107">When a target server polls the master server, it reads the operations assigned to the target server from the **sysdownloadlist** table in the **msdb** database.</span></span> <span data-ttu-id="2d498-108">这些操作控制多服务器作业和目标服务器行为的不同方面。</span><span class="sxs-lookup"><span data-stu-id="2d498-108">These operations control multiserver jobs and various aspects of the behavior of a target server.</span></span> <span data-ttu-id="2d498-109">操作的示例包括删除作业、插入作业、启动作业和更新目标服务器的轮询间隔。</span><span class="sxs-lookup"><span data-stu-id="2d498-109">Examples of operations include deleting a job, inserting a job, starting a job, and updating the polling interval of a target server.</span></span>  
  
 <span data-ttu-id="2d498-110">将操作发布到 **sysdownloadlist** 表中有下面两种方式：</span><span class="sxs-lookup"><span data-stu-id="2d498-110">Operations are posted to the **sysdownloadlist** table in either of the following ways:</span></span>  
  
-   <span data-ttu-id="2d498-111">使用 **sp_post_msx_operation** 存储过程显式发布。</span><span class="sxs-lookup"><span data-stu-id="2d498-111">Explicitly by using the **sp_post_msx_operation** stored procedure.</span></span>  
  
-   <span data-ttu-id="2d498-112">使用其他作业存储过程隐式发布。</span><span class="sxs-lookup"><span data-stu-id="2d498-112">Implicitly by using other job stored procedures.</span></span>  
  
 <span data-ttu-id="2d498-113">如果使用作业存储过程修改多服务器作业计划或作业步骤，或者使用 SQL 分布式管理对象 (SQL-DMO) 控制多服务器作业，请在修改多服务器作业步骤或计划后发出下列命令：</span><span class="sxs-lookup"><span data-stu-id="2d498-113">If you use job stored procedures to modify multiserver job schedules or job steps, or SQL Distributed Management Objects (SQL-DMO) to control multiserver jobs, issue the following command after modifying a multiserver job's steps or schedules:</span></span>  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="2d498-114">发出此命令将保持目标服务器与当前作业定义同步。</span><span class="sxs-lookup"><span data-stu-id="2d498-114">Issue this command keeps the target servers synchronized with the current job definition.</span></span>  
  
 <span data-ttu-id="2d498-115">您不必显式发布操作，如果您使用：</span><span class="sxs-lookup"><span data-stu-id="2d498-115">You do not have to post operations explicitly if you use the following:</span></span>  
  
-   <span data-ttu-id="2d498-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 控制多服务器作业。</span><span class="sxs-lookup"><span data-stu-id="2d498-116">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to control multiserver jobs.</span></span>  
  
-   <span data-ttu-id="2d498-117">不修改作业计划或作业步骤的作业存储过程。</span><span class="sxs-lookup"><span data-stu-id="2d498-117">Job stored procedures that do not modify job schedules or job steps.</span></span>  
  
 <span data-ttu-id="2d498-118">**强制目标服务器轮询主服务器**</span><span class="sxs-lookup"><span data-stu-id="2d498-118">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="2d498-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2d498-119">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="2d498-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2d498-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="2d498-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d498-121">See Also</span></span>  
 [<span data-ttu-id="2d498-122">管理事件</span><span class="sxs-lookup"><span data-stu-id="2d498-122">Manage Events</span></span>](manage-events.md)  
  
  
