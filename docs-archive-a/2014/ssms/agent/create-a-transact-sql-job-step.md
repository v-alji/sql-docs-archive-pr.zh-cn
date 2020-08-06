---
title: 创建 Transact-SQL 作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b83ee944d2ca5c10ff1b77f3e6e6da6054b5c99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692103"
---
# <a name="create-a-transact-sql-job-step"></a><span data-ttu-id="77366-102">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="77366-102">Create a Transact-SQL Job Step</span></span>
  <span data-ttu-id="77366-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象创建在中执行脚本的代理作业步骤 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="77366-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="77366-104">这些作业步骤脚本可以调用存储过程和扩展存储过程。</span><span class="sxs-lookup"><span data-stu-id="77366-104">These job step scripts may call stored procedures and extended stored procedures.</span></span> <span data-ttu-id="77366-105">一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作业步骤可以包含多个批处理和嵌入的 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="77366-105">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches and embedded GO commands.</span></span> <span data-ttu-id="77366-106">有关创建作业的详细信息，请参阅 [创建作业](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="77366-106">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
 <span data-ttu-id="77366-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="77366-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="77366-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="77366-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="77366-109">安全性</span><span class="sxs-lookup"><span data-stu-id="77366-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="77366-110">**若要创建 Transact-SQL 作业步骤，可使用：**</span><span class="sxs-lookup"><span data-stu-id="77366-110">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="77366-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="77366-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="77366-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="77366-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="77366-113">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="77366-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="77366-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="77366-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="77366-115">Security</span><span class="sxs-lookup"><span data-stu-id="77366-115">Security</span></span>  
 <span data-ttu-id="77366-116">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="77366-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="77366-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="77366-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="77366-118">创建 Transact-SQL 作业步骤</span><span class="sxs-lookup"><span data-stu-id="77366-118">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="77366-119">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="77366-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="77366-120">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77366-120">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="77366-121">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="77366-121">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="77366-122">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="77366-122">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="77366-123">在“类型”\*\*\*\* 列表中，单击“Transact-SQL 脚本 (TSQL)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77366-123">In the **Type** list, click **Transact-SQL Script (TSQL)**.</span></span>  
  
6.  <span data-ttu-id="77366-124">在 **“命令”** 框中，键入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批命令，或者单击 **“打开”** ，选择一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文件用作命令。</span><span class="sxs-lookup"><span data-stu-id="77366-124">In the **Command** box, type the [!INCLUDE[tsql](../../includes/tsql-md.md)] command batches, or click **Open** to select a [!INCLUDE[tsql](../../includes/tsql-md.md)] file to use as the command.</span></span>  
  
7.  <span data-ttu-id="77366-125">单击 **“分析”** 检查语法。</span><span class="sxs-lookup"><span data-stu-id="77366-125">Click **Parse** to check your syntax.</span></span>  
  
8.  <span data-ttu-id="77366-126">如果语法正确，将显示“分析成功”消息。</span><span class="sxs-lookup"><span data-stu-id="77366-126">The message "Parse succeeded" is displayed when your syntax is correct.</span></span> <span data-ttu-id="77366-127">如果发现错误，更正语法后再继续。</span><span class="sxs-lookup"><span data-stu-id="77366-127">If an error is found, correct the syntax before continuing.</span></span>  
  
9. <span data-ttu-id="77366-128">单击 **“高级”** 页设置以下作业步骤选项，例如：当该作业步骤成功或失败时将执行的操作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理应该尝试执行该作业步骤的次数，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将作业步骤输出写入哪个文件或表。</span><span class="sxs-lookup"><span data-stu-id="77366-128">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file or table where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="77366-129">只有 **sysadmin** 固定服务器角色的成员才可以将作业步骤输出写入到操作系统文件中。</span><span class="sxs-lookup"><span data-stu-id="77366-129">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span> <span data-ttu-id="77366-130">所有 SQL Server 代理用户都可以将输出写入表中。</span><span class="sxs-lookup"><span data-stu-id="77366-130">All SQL Server Agent users can log output to a table.</span></span>  
  
10. <span data-ttu-id="77366-131">如果您是 **sysadmin** 固定服务器角色的成员，并且希望以其他 SQL 登录身份运行此作业步骤，请从 **“作为以下用户运行”** 列表中选择 SQL 登录名。</span><span class="sxs-lookup"><span data-stu-id="77366-131">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="77366-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="77366-132">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="77366-133">创建 Transact-SQL 作业步骤</span><span class="sxs-lookup"><span data-stu-id="77366-133">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="77366-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="77366-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="77366-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="77366-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="77366-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="77366-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="77366-137">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="77366-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="77366-138">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="77366-138">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="77366-139">**创建 Transact-SQL 作业步骤**</span><span class="sxs-lookup"><span data-stu-id="77366-139">**To create a Transact-SQL job step**</span></span>  
  
 <span data-ttu-id="77366-140">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="77366-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
