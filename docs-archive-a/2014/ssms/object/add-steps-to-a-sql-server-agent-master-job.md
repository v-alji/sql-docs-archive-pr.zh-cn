---
title: 向 SQL Server 代理主作业添加步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9cc1e8ab-7ddc-427b-859e-203aa7e24642
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccff8d6f4faa7bef549b5a179a957ce798250dbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576517"
---
# <a name="add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="fadab-102">Add Steps to a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="fadab-102">Add Steps to a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="fadab-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中向 SQL Server 代理主作业添加步骤。</span><span class="sxs-lookup"><span data-stu-id="fadab-103">This topic describes how to add steps to a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fadab-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="fadab-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fadab-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="fadab-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fadab-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fadab-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fadab-107">安全性</span><span class="sxs-lookup"><span data-stu-id="fadab-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fadab-108">**若要向 SQL Server 代理主作业添加步骤，请使用：**</span><span class="sxs-lookup"><span data-stu-id="fadab-108">**To add steps to a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="fadab-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fadab-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fadab-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fadab-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fadab-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="fadab-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fadab-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="fadab-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="fadab-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="fadab-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fadab-114">Security</span><span class="sxs-lookup"><span data-stu-id="fadab-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fadab-115">权限</span><span class="sxs-lookup"><span data-stu-id="fadab-115">Permissions</span></span>  
 <span data-ttu-id="fadab-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="fadab-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="fadab-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](../agent/implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="fadab-117">For detailed information, see [Implement SQL Server Agent Security](../agent/implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fadab-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fadab-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="fadab-119">向 SQL Server 代理主作业添加步骤</span><span class="sxs-lookup"><span data-stu-id="fadab-119">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="fadab-120">在 **“对象资源管理器”** 中，单击加号以展开包含要添加步骤的作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="fadab-120">In **Object Explorer,** click the plus sign to expand the server that contains the job to which you want to add steps.</span></span>  
  
2.  <span data-ttu-id="fadab-121">单击加号以展开 **“SQL Server 代理”** 。</span><span class="sxs-lookup"><span data-stu-id="fadab-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="fadab-122">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="fadab-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="fadab-123">右键单击要向其添加步骤的作业，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="fadab-123">Right-click the job to which you want to add steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="fadab-124">在“作业属性 - job_name”对话框中的“选择页”下，选择“步骤”  。</span><span class="sxs-lookup"><span data-stu-id="fadab-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span> <span data-ttu-id="fadab-125">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;步骤页&#41;](../agent/job-properties-new-job-steps-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fadab-125">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](../agent/job-properties-new-job-steps-page.md).</span></span>  

6.  <span data-ttu-id="fadab-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="fadab-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fadab-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fadab-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-steps-to-a-sql-server-agent-master-job"></a><span data-ttu-id="fadab-128">向 SQL Server 代理主作业添加步骤</span><span class="sxs-lookup"><span data-stu-id="fadab-128">To add steps to a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="fadab-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="fadab-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fadab-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="fadab-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fadab-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="fadab-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates a job step that changes database access to read-only for the Sales database.   
    -- specifies 5 retry attempts, with each retry to occur after a 5 minute wait.   
    -- assumes that the Weekly Sales Data Backup job already exists  
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
  
 <span data-ttu-id="fadab-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fadab-132">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
  
