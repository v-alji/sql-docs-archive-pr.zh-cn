---
title: 管理整个企业内的作业 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 385435302b2e987c86afb17eaebf90e91bc93e56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580543"
---
# <a name="manage-jobs-across-an-enterprise"></a><span data-ttu-id="13126-102">管理整个企业内的作业</span><span class="sxs-lookup"><span data-stu-id="13126-102">Manage Jobs Across an Enterprise</span></span>
  <span data-ttu-id="13126-103">如果在外部对多服务器作业定义进行更改 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，则必须将更改发布到下载列表，以便目标服务器可以再次下载更新后的作业。</span><span class="sxs-lookup"><span data-stu-id="13126-103">If you make changes to multiserver job definitions outside [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must post the changes to the download list so that target servers can download the updated job again.</span></span> <span data-ttu-id="13126-104">为了确保目标服务器具有当前的作业定义，在更新多服务器作业后，请发布一条 INSERT 指令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13126-104">To ensure that target servers have current job definitions, post an INSERT instruction after you update the multiserver job, as follows:</span></span>  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 <span data-ttu-id="13126-105">若要通知目标服务器多服务器作业已被修改，必须在使用以下任一过程之后调用前一个命令：</span><span class="sxs-lookup"><span data-stu-id="13126-105">To notify target servers that a multiserver job has been modified, you must invoke the preceding command after using any of the following procedures:</span></span>  
  
-   [<span data-ttu-id="13126-106">sp_add_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="13126-106">sp_add_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="13126-107">sp_update_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="13126-107">sp_update_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [<span data-ttu-id="13126-108">sp_delete_jobstep (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="13126-108">sp_delete_jobstep (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [<span data-ttu-id="13126-109">sp_attach_schedule (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="13126-109">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="13126-110">sp_detach_schedule &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="13126-110">sp_detach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  <span data-ttu-id="13126-111">调用 **sp_update_job** 或 **sp_delete_job** 后不需要调用 **sp_post_msx_operation**，因为这些存储过程会自动向下载列表发布所需的更改。</span><span class="sxs-lookup"><span data-stu-id="13126-111">It is not necessary to call **sp_post_msx_operation** after you call **sp_update_job** or **sp_delete_job**, because these stored procedures post the required changes to the download list automatically.</span></span>  
  
 <span data-ttu-id="13126-112">以下是管理整个企业内的作业要执行的常规任务：</span><span class="sxs-lookup"><span data-stu-id="13126-112">The following are common tasks for managing jobs across an enterprise:</span></span>  
  
 <span data-ttu-id="13126-113">**检查目标服务器的状态**</span><span class="sxs-lookup"><span data-stu-id="13126-113">**To check the status of a target server**</span></span>  
  
-   [<span data-ttu-id="13126-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13126-114">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [<span data-ttu-id="13126-115">SQL Server 管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="13126-115">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="13126-116">**更改作业的目标服务器**</span><span class="sxs-lookup"><span data-stu-id="13126-116">**To change the target servers for a job**</span></span>  
  
-   [<span data-ttu-id="13126-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13126-117">SQL Server Management Studio</span></span>](modify-the-target-servers-for-a-job.md)  
  
-   [<span data-ttu-id="13126-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13126-118">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [<span data-ttu-id="13126-119">SQL Server 管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="13126-119">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="13126-120">**更改目标服务器的位置**</span><span class="sxs-lookup"><span data-stu-id="13126-120">**To change the location of a target server**</span></span>  
  
-   [<span data-ttu-id="13126-121">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13126-121">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="13126-122">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13126-122">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [<span data-ttu-id="13126-123">SQL Server 管理对象 (SMO)</span><span class="sxs-lookup"><span data-stu-id="13126-123">SQL Server Management Objects (SMO)</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 <span data-ttu-id="13126-124">**同步目标服务器的时钟**</span><span class="sxs-lookup"><span data-stu-id="13126-124">**To synchronize target server clocks**</span></span>  
  
-   [<span data-ttu-id="13126-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13126-125">SQL Server Management Studio</span></span>](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="13126-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13126-126">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 <span data-ttu-id="13126-127">**强制目标服务器轮询主服务器**</span><span class="sxs-lookup"><span data-stu-id="13126-127">**To force a target server to poll the master server**</span></span>  
  
-   [<span data-ttu-id="13126-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="13126-128">SQL Server Management Studio</span></span>](force-a-target-server-to-poll-the-master-server.md)  
  
-   [<span data-ttu-id="13126-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="13126-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="13126-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13126-130">See Also</span></span>  
 [<span data-ttu-id="13126-131">管理事件</span><span class="sxs-lookup"><span data-stu-id="13126-131">Manage Events</span></span>](manage-events.md)  
  
  
