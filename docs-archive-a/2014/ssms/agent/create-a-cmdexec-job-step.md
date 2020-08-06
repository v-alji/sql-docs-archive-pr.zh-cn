---
title: 创建 CmdExec 作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c557b8ea4228d27b73d361c50aac62232d1e00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586056"
---
# <a name="create-a-cmdexec-job-step"></a><span data-ttu-id="2bcd5-102">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="2bcd5-102">Create a CmdExec Job Step</span></span>
  <span data-ttu-id="2bcd5-103">本主题介绍如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过使用或 SQL Server 管理对象，在中创建和定义 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用可执行程序或操作系统命令的代理作业 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 步骤 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that uses an executable program or operating system command by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="2bcd5-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2bcd5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2bcd5-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2bcd5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2bcd5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2bcd5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2bcd5-107">**若要创建 CmdExec 作业步骤，可使用：**</span><span class="sxs-lookup"><span data-stu-id="2bcd5-107">**To create a CmdExec job step, using:**</span></span>  
  
     [<span data-ttu-id="2bcd5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2bcd5-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="2bcd5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2bcd5-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="2bcd5-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="2bcd5-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2bcd5-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="2bcd5-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2bcd5-112">Security</span><span class="sxs-lookup"><span data-stu-id="2bcd5-112">Security</span></span>  
 <span data-ttu-id="2bcd5-113">默认情况下，只有 **sysadmin** 固定服务器角色的成员可以创建 CmdExec 作业步骤。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-113">By default, only members of the **sysadmin** fixed server role can create CmdExec job steps.</span></span> <span data-ttu-id="2bcd5-114">除非 **sysadmin** 用户创建一个代理帐户，否则这些作业步骤将在 SQL Server 代理服务帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-114">These job steps run under the context of the SQL Server Agent service account unless the **sysadmin** user creates a proxy account.</span></span> <span data-ttu-id="2bcd5-115">如果不属于 **sysadmin** 角色成员的用户具有访问 CmdExec 代理帐户的权限，则也可以创建 CmdExec 作业步骤。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-115">Users who are not members of the **sysadmin** role can create CmdExec job steps if they have access to a CmdExec proxy account.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2bcd5-116">权限</span><span class="sxs-lookup"><span data-stu-id="2bcd5-116">Permissions</span></span>  
 <span data-ttu-id="2bcd5-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="2bcd5-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2bcd5-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="2bcd5-119">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="2bcd5-119">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="2bcd5-120">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2bcd5-121">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-121">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2bcd5-122">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-122">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2bcd5-123">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-123">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="2bcd5-124">在 **“类型”** 列表中，选择 **“操作系统(CmdExec)”**。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-124">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
6.  <span data-ttu-id="2bcd5-125">在 **“运行身份”** 列表中，选择具有作业将使用的凭据的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-125">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="2bcd5-126">默认情况下，CmdExec 作业步骤在 SQL Server 代理服务帐户的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-126">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
7.  <span data-ttu-id="2bcd5-127">在 **“成功命令的进程退出代码”** 框中，输入一个介于 0 到 999999 之间的值。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-127">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
8.  <span data-ttu-id="2bcd5-128">在 **“命令”** 框中，输入操作系统命令或可执行程序。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-128">In the **Command** box, enter the operating system command or executable program.</span></span> <span data-ttu-id="2bcd5-129">请参阅“使用 Transact T-SQL”中的示例。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-129">See "Using Transact T-SQL for an example.</span></span>  
  
9. <span data-ttu-id="2bcd5-130">单击 **“高级”** 页设置以下作业步骤选项，例如：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将作业步骤输出写入哪个文件。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-130">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="2bcd5-131">只有 **sysadmin** 固定服务器角色的成员才可以将作业步骤输出写入到操作系统文件中。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-131">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="2bcd5-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2bcd5-132">Using Transact-SQL</span></span>  
  
### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="2bcd5-133">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="2bcd5-133">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="2bcd5-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2bcd5-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2bcd5-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="2bcd5-137">有关详细信息，请参阅[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="2bcd5-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="2bcd5-138">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="2bcd5-138">Using SQL Server Management Objects</span></span>  

### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="2bcd5-139">创建 CmdExec 作业步骤</span><span class="sxs-lookup"><span data-stu-id="2bcd5-139">To create a CmdExec job step</span></span>
  
 <span data-ttu-id="2bcd5-140">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
