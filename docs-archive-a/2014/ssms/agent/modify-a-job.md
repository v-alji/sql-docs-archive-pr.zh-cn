---
title: 修改作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d25830ad119a1f5f344a4dcf318c35bee5f86ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580540"
---
# <a name="modify-a-job"></a><span data-ttu-id="0c388-102">Modify a Job</span><span class="sxs-lookup"><span data-stu-id="0c388-102">Modify a Job</span></span>
  <span data-ttu-id="0c388-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象在中更改代理作业的属性 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0c388-103">This topic describes how to change the properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="0c388-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0c388-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0c388-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0c388-105">**Before you begin:** ,</span></span>  
  
     [<span data-ttu-id="0c388-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0c388-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0c388-107">安全性</span><span class="sxs-lookup"><span data-stu-id="0c388-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0c388-108">**若要修改作业，可使用：**</span><span class="sxs-lookup"><span data-stu-id="0c388-108">**To modify a job, using:**</span></span>  
  
     [<span data-ttu-id="0c388-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0c388-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0c388-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0c388-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="0c388-111">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0c388-111">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0c388-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="0c388-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0c388-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="0c388-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0c388-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="0c388-114">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0c388-115">Security</span><span class="sxs-lookup"><span data-stu-id="0c388-115">Security</span></span>  
 <span data-ttu-id="0c388-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="0c388-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="0c388-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0c388-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0c388-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0c388-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="0c388-119">修改作业</span><span class="sxs-lookup"><span data-stu-id="0c388-119">To modify a job</span></span>  
  
1.  <span data-ttu-id="0c388-120">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0c388-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0c388-121">展开“SQL Server 代理”\*\*\*\*，再展开“作业”\*\*\*\*，然后右键单击要修改的作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c388-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0c388-122">在 **“作业属性”** 对话框中，使用相应的页来更新作业的属性、步骤、计划、警报和通知。</span><span class="sxs-lookup"><span data-stu-id="0c388-122">In the **Job Properties** dialog box, update the job's properties, steps, schedule, alerts, and notifications using the corresponding pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="0c388-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0c388-123">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-job"></a><span data-ttu-id="0c388-124">修改作业</span><span class="sxs-lookup"><span data-stu-id="0c388-124">To modify a job</span></span>  
  
1.  <span data-ttu-id="0c388-125">在对象资源管理器中，连接到数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="0c388-125">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0c388-126">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="0c388-126">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0c388-127">在查询窗口中，使用以下系统存储过程修改作业。</span><span class="sxs-lookup"><span data-stu-id="0c388-127">In the query window, use the following system stored procedures to modify a job.</span></span>  
  
    -   <span data-ttu-id="0c388-128">执行[sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) ，以更改作业的属性。</span><span class="sxs-lookup"><span data-stu-id="0c388-128">Execute [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql) to change the attributes of a job.</span></span>  
  
    -   <span data-ttu-id="0c388-129">执行[sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) ，以更改作业定义的计划详细信息。</span><span class="sxs-lookup"><span data-stu-id="0c388-129">Execute [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql) to change the scheduling details for a job definition.</span></span>  
  
    -   <span data-ttu-id="0c388-130">执行[&#40;transact-sql&#41;sp_add_jobstep](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) ，以添加新的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="0c388-130">Execute [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql) to add new job steps.</span></span>  
  
    -   <span data-ttu-id="0c388-131">执行[sp_update_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) ，以更改预先存在的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="0c388-131">Execute [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) to change pre-existing job steps.</span></span>  
  
    -   <span data-ttu-id="0c388-132">执行[sp_delete_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) ，以便从作业中删除作业步骤。</span><span class="sxs-lookup"><span data-stu-id="0c388-132">Execute [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql) to remove a job step from a job.</span></span>  
  
    -   <span data-ttu-id="0c388-133">修改任何 SQLServer 代理主作业的其他存储过程：</span><span class="sxs-lookup"><span data-stu-id="0c388-133">Additional stored procedures to modify any SQL Server Agent master job:</span></span>  
  
        -   <span data-ttu-id="0c388-134">执行[sp_delete_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)删除当前与作业相关联的服务器。</span><span class="sxs-lookup"><span data-stu-id="0c388-134">Execute [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql) to delete a server currently associated with a job.</span></span>  
  
        -   <span data-ttu-id="0c388-135">执行[sp_add_jobserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) ，将服务器与当前作业相关联。</span><span class="sxs-lookup"><span data-stu-id="0c388-135">Execute [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql) to associate a server with the current job.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0c388-136">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0c388-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0c388-137">**修改作业**</span><span class="sxs-lookup"><span data-stu-id="0c388-137">**To modify a job**</span></span>  
  
 <span data-ttu-id="0c388-138">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `Job` 类。</span><span class="sxs-lookup"><span data-stu-id="0c388-138">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="0c388-139">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0c388-139">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
  
