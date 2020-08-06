---
title: 更改 SQL Server 代理主作业计划的详细信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85546bc93e6626bfcc85a28f06a4c2fe24fe9fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591082"
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a><span data-ttu-id="79ec2-102">Change the Scheduling Details for a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="79ec2-102">Change the Scheduling Details for a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="79ec2-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中更改作业定义计划的详细信息。</span><span class="sxs-lookup"><span data-stu-id="79ec2-103">This topic describes how to change the scheduling details for a job definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="79ec2-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="79ec2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="79ec2-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="79ec2-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="79ec2-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="79ec2-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="79ec2-107">安全性</span><span class="sxs-lookup"><span data-stu-id="79ec2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="79ec2-108">**若要更改作业定义计划的详细信息，请使用：**</span><span class="sxs-lookup"><span data-stu-id="79ec2-108">**To change the scheduling details for a job definition, using:**</span></span>  
  
     [<span data-ttu-id="79ec2-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="79ec2-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="79ec2-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79ec2-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="79ec2-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="79ec2-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="79ec2-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="79ec2-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="79ec2-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="79ec2-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="79ec2-114">Security</span><span class="sxs-lookup"><span data-stu-id="79ec2-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="79ec2-115">权限</span><span class="sxs-lookup"><span data-stu-id="79ec2-115">Permissions</span></span>  
 <span data-ttu-id="79ec2-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="79ec2-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="79ec2-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="79ec2-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="79ec2-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="79ec2-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="79ec2-119">更改作业定义计划的详细信息</span><span class="sxs-lookup"><span data-stu-id="79ec2-119">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="79ec2-120">在 **“对象资源管理器”** 中，单击加号以展开包含要编辑其计划的作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="79ec2-120">In **Object Explorer,** click the plus sign to expand the server that contains the job whose schedule you want to edit.</span></span>  
  
2.  <span data-ttu-id="79ec2-121">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="79ec2-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="79ec2-122">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="79ec2-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="79ec2-123">右键单击要编辑其计划的作业，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79ec2-123">Right-click the job whose schedule you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="79ec2-124">在 "**作业属性-**_job_name_ " 对话框中的 "**选择页**" 下，选择 "**计划**"。</span><span class="sxs-lookup"><span data-stu-id="79ec2-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Schedules**.</span></span> <span data-ttu-id="79ec2-125">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;计划页&#41;](job-properties-new-job-schedules-page.md)。</span><span class="sxs-lookup"><span data-stu-id="79ec2-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md).</span></span>  
  
6.  <span data-ttu-id="79ec2-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="79ec2-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="79ec2-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79ec2-127">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="79ec2-128">更改作业定义计划的详细信息</span><span class="sxs-lookup"><span data-stu-id="79ec2-128">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="79ec2-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="79ec2-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="79ec2-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="79ec2-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="79ec2-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="79ec2-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
 <span data-ttu-id="79ec2-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_schedule ](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79ec2-132">For more information, see [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql).</span></span>  
  
  
