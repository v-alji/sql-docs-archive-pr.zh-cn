---
title: 更改 SQL Server 代理主作业的步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a9defc17b5b39ab8a322b6da29960eb9968c2e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591084"
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="676a0-102">Change Steps of a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="676a0-102">Change Steps of a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="676a0-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中更改 SQL Server 代理主作业的步骤。</span><span class="sxs-lookup"><span data-stu-id="676a0-103">This topic describes how to make changes to the steps of a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="676a0-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="676a0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="676a0-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="676a0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="676a0-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="676a0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="676a0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="676a0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="676a0-108">**若要更改 SQL Server 代理主作业的步骤，请使用：**</span><span class="sxs-lookup"><span data-stu-id="676a0-108">**To make changes to the steps of a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="676a0-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="676a0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="676a0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="676a0-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="676a0-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="676a0-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="676a0-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="676a0-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="676a0-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="676a0-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="676a0-114">Security</span><span class="sxs-lookup"><span data-stu-id="676a0-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="676a0-115">权限</span><span class="sxs-lookup"><span data-stu-id="676a0-115">Permissions</span></span>  
 <span data-ttu-id="676a0-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="676a0-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="676a0-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="676a0-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="676a0-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="676a0-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="676a0-119">更改 SQL Server 代理主作业的步骤</span><span class="sxs-lookup"><span data-stu-id="676a0-119">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="676a0-120">在 **“对象资源管理器”** 中，单击加号以展开包含要修改步骤的作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="676a0-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify steps.</span></span>  
  
2.  <span data-ttu-id="676a0-121">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="676a0-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="676a0-122">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="676a0-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="676a0-123">右键单击要修改步骤的作业，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="676a0-123">Right-click the job where you want to modify steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="676a0-124">在 "**作业属性-**_job_name_ " 对话框中的 "**选择页**" 下，选择 "**步骤**"。</span><span class="sxs-lookup"><span data-stu-id="676a0-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="676a0-125">单击 "**编辑**" 以打开 "**作业步骤属性-**_job_step_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="676a0-125">Click **Edit** to open the **Job Step Properties -**_job_step_name_ dialog box.</span></span> <span data-ttu-id="676a0-126">有关此对话框中可用选项的详细信息，请参阅[作业步骤属性： "新建作业步骤" &#40;"常规" 页&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)和[作业步骤属性：新建作业步骤 &#40;"高级" 页&#41;](job-step-properties-new-job-step-advanced-page.md)。</span><span class="sxs-lookup"><span data-stu-id="676a0-126">For more information on the available options in this dialog box, see [Job Step Properties: New Job Step &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) and [Job Step Properties: New Job Step &#40;Advanced Page&#41;](job-step-properties-new-job-step-advanced-page.md).</span></span>  
  
7.  <span data-ttu-id="676a0-127">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="676a0-127">When finished, click **OK**.</span></span>  
  
8.  <span data-ttu-id="676a0-128">在 "**作业属性-**_job_name_ " 对话框中，单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="676a0-128">In the **Job Properties -**_job_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="676a0-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="676a0-129">Using Transact-SQL</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="676a0-130">更改 SQL Server 代理主作业的步骤</span><span class="sxs-lookup"><span data-stu-id="676a0-130">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="676a0-131">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="676a0-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="676a0-132">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="676a0-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="676a0-133">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="676a0-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the number of retry attempts for the first step of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
 <span data-ttu-id="676a0-134">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_jobstep ](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="676a0-134">For more information, see [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql).</span></span>  
  
  
