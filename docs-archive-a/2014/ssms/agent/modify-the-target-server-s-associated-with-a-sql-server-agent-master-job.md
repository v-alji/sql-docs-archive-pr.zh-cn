---
title: 修改与 SQL Server 代理主作业关联的目标服务器 () |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 176e73b6-08aa-48ec-b349-e84b431e65cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b7b5ab114366cdafe40b7a70f523fef43eb11d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591068"
---
# <a name="modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="120a6-102">修改与 SQL Server 代理主作业关联的目标服务器</span><span class="sxs-lookup"><span data-stu-id="120a6-102">Modify the Target Server(s) Associated with a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="120a6-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改与 SQL Server 代理主作业关联的目标服务器。</span><span class="sxs-lookup"><span data-stu-id="120a6-103">This topic describes how to modify the target server(s) associated with a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="120a6-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="120a6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="120a6-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="120a6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="120a6-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="120a6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="120a6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="120a6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="120a6-108">**若要修改与 SQL Server 代理主作业关联的目标服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="120a6-108">**To modify the target server(s) associated with a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="120a6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="120a6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="120a6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="120a6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="120a6-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="120a6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="120a6-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="120a6-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="120a6-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="120a6-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="120a6-114">Security</span><span class="sxs-lookup"><span data-stu-id="120a6-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="120a6-115">权限</span><span class="sxs-lookup"><span data-stu-id="120a6-115">Permissions</span></span>  
 <span data-ttu-id="120a6-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="120a6-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="120a6-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="120a6-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="120a6-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="120a6-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-target-servers-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="120a6-119">修改与 SQL Server 代理主作业关联的目标服务器</span><span class="sxs-lookup"><span data-stu-id="120a6-119">To modify the target server(s) associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="120a6-120">在 **“对象资源管理器”** 中，单击加号以展开要修改目标服务器的作业所在的服务器。</span><span class="sxs-lookup"><span data-stu-id="120a6-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify the target server.</span></span>  
  
2.  <span data-ttu-id="120a6-121">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="120a6-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="120a6-122">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="120a6-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="120a6-123">右键单击要修改目标服务器的作业，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="120a6-123">Right-click the job where you want to modify the target server and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="120a6-124">在 "**作业属性-**_job_name_ " 对话框中的 "**选择页**" 下，选择 "**目标**"。</span><span class="sxs-lookup"><span data-stu-id="120a6-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Targets**.</span></span> <span data-ttu-id="120a6-125">有关此页上可用选项的详细信息，请参阅[作业属性：新建作业 &#40;目标&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="120a6-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
6.  <span data-ttu-id="120a6-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="120a6-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="120a6-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="120a6-127">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-target-server-currently-associated-with-a-sql-server-agent-master-job"></a><span data-ttu-id="120a6-128">删除当前与 SQL Server 代理主作业关联的目标服务器</span><span class="sxs-lookup"><span data-stu-id="120a6-128">To delete a target server currently associated with a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="120a6-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="120a6-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="120a6-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="120a6-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="120a6-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。</span><span class="sxs-lookup"><span data-stu-id="120a6-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes the server SEATTLE2 from processing the Weekly Sales Backupsjob   
    -- assumes that the Weekly Sales Backups job exists  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="120a6-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_jobserver ](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="120a6-132">For more information, see [sp_delete_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql).</span></span>  
  
#### <a name="to-associate-a-target-server-with-the-current-sql-server-agent-master-job"></a><span data-ttu-id="120a6-133">将目标服务器关联到当前的 SQL Server 代理主作业</span><span class="sxs-lookup"><span data-stu-id="120a6-133">To associate a target server with the current SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="120a6-134">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="120a6-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="120a6-135">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="120a6-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="120a6-136">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="120a6-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2   
    -- assumes that the Weekly Sales Backups job already exists and that   
    -- SEATTLE2 is registered as a target server for the current instance  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="120a6-137">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobserver ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="120a6-137">For more information, see [sp_add_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql).</span></span>  
  
  
