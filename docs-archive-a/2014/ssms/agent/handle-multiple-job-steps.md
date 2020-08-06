---
title: 处理多个作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef0fb69b5bfd028977276d8efabc333a21e0feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577197"
---
# <a name="handle-multiple-job-steps"></a><span data-ttu-id="0c3a4-102">处理多个作业步骤</span><span class="sxs-lookup"><span data-stu-id="0c3a4-102">Handle Multiple Job Steps</span></span>
  <span data-ttu-id="0c3a4-103">如果作业有多个作业步骤，必须指定这些作业步骤的运行顺序。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-103">If your job has more than one job step, you must specify the order in which the job steps run.</span></span> <span data-ttu-id="0c3a4-104">这称为\*流控制 \* *。*</span><span class="sxs-lookup"><span data-stu-id="0c3a4-104">This is called *control of flow\*\*.*</span></span> <span data-ttu-id="0c3a4-105">您可以随时添加新的作业步骤并重排作业步骤流，更改在下次运行作业时生效。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-105">You can add new job steps and rearrange the flow of job steps at any time; the changes take effect the next time the job is run.</span></span> <span data-ttu-id="0c3a4-106">下图说明了一个数据库备份作业的流控制。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-106">This illustration shows the control of flow for a database backup job.</span></span>  
  
 <span data-ttu-id="0c3a4-107">![SQL Server 代理作业步骤的流控制](../../database-engine/media/dbflow01.gif "SQL Server 代理作业步骤的流控制")</span><span class="sxs-lookup"><span data-stu-id="0c3a4-107">![SQL Server Agent job steps control of flow](../../database-engine/media/dbflow01.gif "SQL Server Agent job steps control of flow")</span></span>  
  
 <span data-ttu-id="0c3a4-108">第一步是备份数据库。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-108">The first step is Backup Database.</span></span> <span data-ttu-id="0c3a4-109">如果这一步失败， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将把失败报告给定义为接收通知的操作员。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-109">If this step fails, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent reports failure to the operator who is defined to receive notification.</span></span> <span data-ttu-id="0c3a4-110">如果备份数据库步骤成功，则作业将继续进行下一步，即“清理”客户端数据。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-110">If the Backup Database step succeeds, the job proceeds to the next step, "Scrub" Customer Data.</span></span> <span data-ttu-id="0c3a4-111">如果这一步失败， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理将向前跳至还原数据库。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-111">If this step fails, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent skips forward to Restore Database.</span></span> <span data-ttu-id="0c3a4-112">如果“清理”客户端数据成功，则作业将继续进行下一步，即更新统计信息，如此继续，直至最后报告成功或报告失败。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-112">If "Scrub" Customer Data succeeds, the job proceeds to the next step, Update Statistics, and so on, until the final step either results in Report Success or Report Failure.</span></span>  
  
 <span data-ttu-id="0c3a4-113">为每个作业步骤的成功和失败都定义一个流控制操作。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-113">You define a control-of-flow action for the success and failure of each job step.</span></span> <span data-ttu-id="0c3a4-114">必须指定作业步骤成功执行的操作和作业步骤失败时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-114">You must specify an action to be taken when a job step succeeds and an action to be taken when a job step fails.</span></span> <span data-ttu-id="0c3a4-115">还可以定义对失败的作业步骤进行重试的次数以及重试时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-115">You can also define the number of retry attempts for failed job steps and the interval between the retry attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c3a4-116">当使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理图形用户界面 (GUI) 并从多步骤作业中删除一个或多个步骤时，GUI 将删除所有作业步骤，然后使用正确的成功时或失败时引用重新添加剩余的步骤。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-116">When you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent graphical user interface (GUI) and delete one or more steps from a multistep job, the GUI removes all job steps and then adds the remaining steps back with the correct on-success or on-failure references.</span></span> <span data-ttu-id="0c3a4-117">例如，假设您有一个包含五个步骤的作业，第一步配置为在顺利完成时即跳到第 4 步。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-117">For example, suppose you have a job with five steps, and the first step is configured to jump to step 4 if it completes successfully.</span></span> <span data-ttu-id="0c3a4-118">如果删除第 3 步，则 GUI 将删除此作业的所有步骤，然后使用正确的引用添加剩余的四个步骤（1、2、4 和 5）。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-118">If you delete step 3, the GUI removes all steps for this job and adds the remaining four steps (1, 2, 4, and 5) with corrected references.</span></span> <span data-ttu-id="0c3a4-119">在此示例中，第 1 步中的引用将重新配置为在第 1 步顺利完成时即跳到第 3 步。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-119">In this case, the reference in step 1 would be reconfigured to jump to step 3 if step 1 completes successfully.</span></span>  
  
 <span data-ttu-id="0c3a4-120">作业步骤必须自包含。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-120">Job steps must be self-contained.</span></span> <span data-ttu-id="0c3a4-121">也就是说，作业不能在作业步骤之间传递布尔值、数据或数值。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-121">That is, a job cannot pass Boolean values, data, or numeric values between job steps.</span></span> <span data-ttu-id="0c3a4-122">但可以使用永久表或全局临时表在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤之间传递值。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-122">You can, however, pass values from one [!INCLUDE[tsql](../../includes/tsql-md.md)] job step to another by using permanent tables or global temporary tables.</span></span> <span data-ttu-id="0c3a4-123">可以使用文件在运行可执行程序的作业步骤之间传递值。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-123">You can pass values from job steps that run executable programs from one job step to another job step by using files.</span></span> <span data-ttu-id="0c3a4-124">例如，一个作业步骤运行的可执行程序向一个文件写入数据，后续作业步骤运行的可执行程序读取该文件。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-124">For example, the executable run by one job step writes a file, and the executable run by a subsequent job step reads the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c3a4-125">如果创建循环作业步骤（作业步骤 1 后面跟着作业步骤 2，然后作业步骤 2 又返回到作业步骤 1），则在使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]创建作业时会出现警告消息。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-125">If you create looping job steps (job step 1 is followed by job step 2, then job step 2 returns to job step 1), a warning message appears when the job is created using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0c3a4-126">代理在作业历史记录中记录作业和作业步骤信息。</span><span class="sxs-lookup"><span data-stu-id="0c3a4-126">Agent records job and job step information in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3a4-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c3a4-127">See Also</span></span>  
 <span data-ttu-id="0c3a4-128">[sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c3a4-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="0c3a4-129">[dbo.sysjobhistory &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c3a4-129">[dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span></span>  
 <span data-ttu-id="0c3a4-130">[dbo.sys作业 &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c3a4-130">[dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span></span>  
 <span data-ttu-id="0c3a4-131">[dbo.sysjobsteps &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c3a4-131">[dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span></span>  
 <span data-ttu-id="0c3a4-132">[执行作业](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="0c3a4-132">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="0c3a4-133">管理作业步骤</span><span class="sxs-lookup"><span data-stu-id="0c3a4-133">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
