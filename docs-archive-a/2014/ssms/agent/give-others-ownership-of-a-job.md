---
title: 将作业所有权授予其他人 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2cf03fdc9031ce9761125d95619438837f2959bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577202"
---
# <a name="give-others-ownership-of-a-job"></a><span data-ttu-id="f070e-102">Give Others Ownership of a Job</span><span class="sxs-lookup"><span data-stu-id="f070e-102">Give Others Ownership of a Job</span></span>
  <span data-ttu-id="f070e-103">本主题介绍如何将代理作业的所有权重新分配 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 给另一个用户。</span><span class="sxs-lookup"><span data-stu-id="f070e-103">This topic describes how to reassign ownership of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>  
  
-   <span data-ttu-id="f070e-104">**开始之前：** [限制和局限](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="f070e-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="f070e-105">**若要将作业所有权授予其他人，请使用：**</span><span class="sxs-lookup"><span data-stu-id="f070e-105">**To give others ownership of a job, using:**</span></span>  
  
     [<span data-ttu-id="f070e-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f070e-106">SQL Server Management Studio</span></span>](#SSMSProc2)  
  
     [<span data-ttu-id="f070e-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f070e-107">Transact-SQL</span></span>](#TsqlProc2)  
  
     [<span data-ttu-id="f070e-108">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="f070e-108">SQL Server Management Objects</span></span>](#SMOProc2)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f070e-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="f070e-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f070e-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="f070e-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f070e-111">若要创建作业，用户必须是某个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色或 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="f070e-111">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="f070e-112">作业只能由其所有者或 **sysadmin** 角色的成员进行编辑。</span><span class="sxs-lookup"><span data-stu-id="f070e-112">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="f070e-113">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的固定数据库角色的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="f070e-113">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="f070e-114">您必须是系统管理员才可以更改作业的所有者。</span><span class="sxs-lookup"><span data-stu-id="f070e-114">You must be a system administrator to change the owner of a job.</span></span>  
  
 <span data-ttu-id="f070e-115">将作业指派给另一个登录名并不保证新所有者有足够的权限来成功运行该作业。</span><span class="sxs-lookup"><span data-stu-id="f070e-115">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f070e-116">Security</span><span class="sxs-lookup"><span data-stu-id="f070e-116">Security</span></span>  
 <span data-ttu-id="f070e-117">为了安全起见，仅作业所有者或 **sysadmin** 角色的成员可以更改作业的定义。</span><span class="sxs-lookup"><span data-stu-id="f070e-117">For security reasons, only the job owner or a member of the **sysadmin** role can change the definition of the job.</span></span> <span data-ttu-id="f070e-118">只有 **sysadmin** 固定服务器角色的成员才可以将作业所有权分配给其他用户，并且他们可以运行任何作业，而不管作业所有者是谁。</span><span class="sxs-lookup"><span data-stu-id="f070e-118">Only members of the **sysadmin** fixed server role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f070e-119">如果将作业所有权重新指派到的用户不是 **sysadmin** 固定服务器角色的成员，而执行作业的步骤需要代理帐户（例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包执行），则请确保该用户可以访问该代理帐户，否则作业将失败。</span><span class="sxs-lookup"><span data-stu-id="f070e-119">If you change job ownership to a user who is not a member of the **sysadmin** fixed server role, and the job is executing job steps that require proxy accounts (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution), make sure that the user has access to that proxy account or else the job will fail.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f070e-120">权限</span><span class="sxs-lookup"><span data-stu-id="f070e-120">Permissions</span></span>  
 <span data-ttu-id="f070e-121">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f070e-121">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProc2"></a> <span data-ttu-id="f070e-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f070e-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f070e-123">**将作业所有权授予其他人**</span><span class="sxs-lookup"><span data-stu-id="f070e-123">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="f070e-124">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="f070e-124">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f070e-125">展开“SQL Server 代理”\*\*\*\*，再展开“作业”\*\*\*\*，右键单击相应作业，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f070e-125">Expand **SQL Server Agent**, expand **Jobs**, right-click the job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f070e-126">在 **“所有者”** 列表中，选择一个登录名。</span><span class="sxs-lookup"><span data-stu-id="f070e-126">In the **Owner** list, select a login.</span></span> <span data-ttu-id="f070e-127">您必须是系统管理员才可以更改作业的所有者。</span><span class="sxs-lookup"><span data-stu-id="f070e-127">You must be a system administrator to change the owner of a job.</span></span>  
  
     <span data-ttu-id="f070e-128">将作业指派给另一个登录名并不保证新所有者有足够的权限来成功运行该作业。</span><span class="sxs-lookup"><span data-stu-id="f070e-128">Assigning a job to another login does not guarantee that the new owner has sufficient permission to run the job successfully.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProc2"></a> <span data-ttu-id="f070e-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f070e-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="f070e-130">**将作业所有权授予其他人**</span><span class="sxs-lookup"><span data-stu-id="f070e-130">**To give others ownership of a job**</span></span>  
  
1.  <span data-ttu-id="f070e-131">在对象资源管理器中，连接到数据库引擎实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="f070e-131">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f070e-132">在工具栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="f070e-132">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f070e-133">在查询窗口中，输入以下语句，这些语句使用[sp_manage_jobs_by_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql)系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="f070e-133">In the query window, enter the following statements that use the [sp_manage_jobs_by_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql) system stored procedure.</span></span> <span data-ttu-id="f070e-134">以下示例将所有作业从 `danw` 重新分配给 `fran??oisa`。</span><span class="sxs-lookup"><span data-stu-id="f070e-134">The following example reassigns all jobs from `danw` to `fran??oisa`.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'fran??oisa' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMOProc2"></a><span data-ttu-id="f070e-135">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="f070e-135">Using SQL Server Management Objects</span></span>  

### <a name="to-give-others-ownership-of-a-job"></a><span data-ttu-id="f070e-136">将作业所有权授予其他人</span><span class="sxs-lookup"><span data-stu-id="f070e-136">To give others ownership of a job</span></span>
  
1.  <span data-ttu-id="f070e-137">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `Job` 类。</span><span class="sxs-lookup"><span data-stu-id="f070e-137">Call the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="f070e-138">有关示例代码，请参阅 [在 SQL Server 代理中计划自动管理任务](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="f070e-138">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f070e-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f070e-139">See Also</span></span>  
 <span data-ttu-id="f070e-140">[执行作业](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="f070e-140">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="f070e-141">创建作业</span><span class="sxs-lookup"><span data-stu-id="f070e-141">Create Jobs</span></span>](create-jobs.md)  
