---
title: 从 SQL Server 代理主作业中删除步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 871e6162-1221-464d-8f7f-7e454dcd9edb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5996971225ee0b300b307c5af24dec464dbfd43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591052"
---
# <a name="remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="8b43f-102">Remove Steps from a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="8b43f-102">Remove Steps from a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="8b43f-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除 SQL Server 代理主作业中的步骤。</span><span class="sxs-lookup"><span data-stu-id="8b43f-103">This topic describes how to remove steps from a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8b43f-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="8b43f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8b43f-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="8b43f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8b43f-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="8b43f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8b43f-107">安全性</span><span class="sxs-lookup"><span data-stu-id="8b43f-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8b43f-108">**若要从 SQL Server 代理主作业中删除步骤，请使用：**</span><span class="sxs-lookup"><span data-stu-id="8b43f-108">**To remove steps from a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="8b43f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8b43f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8b43f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8b43f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8b43f-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="8b43f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8b43f-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="8b43f-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8b43f-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主作业不能同时把本地服务器和远程服务器作为目标。</span><span class="sxs-lookup"><span data-stu-id="8b43f-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8b43f-114">Security</span><span class="sxs-lookup"><span data-stu-id="8b43f-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8b43f-115">权限</span><span class="sxs-lookup"><span data-stu-id="8b43f-115">Permissions</span></span>  
 <span data-ttu-id="8b43f-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="8b43f-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="8b43f-117">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="8b43f-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8b43f-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8b43f-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="8b43f-119">从 SQL Server 代理主作业中删除步骤</span><span class="sxs-lookup"><span data-stu-id="8b43f-119">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="8b43f-120">在 **“对象资源管理器”** 中，单击加号以展开包含要从中删除步骤的作业的服务器。</span><span class="sxs-lookup"><span data-stu-id="8b43f-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to delete steps.</span></span>  
  
2.  <span data-ttu-id="8b43f-121">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="8b43f-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="8b43f-122">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8b43f-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="8b43f-123">右键单击要从中删除步骤的作业，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8b43f-123">Right-click the job where you want to delete steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="8b43f-124">在 "**作业属性-**_job_name_ " 对话框中的 "**选择页**" 下，选择 "**步骤**"。</span><span class="sxs-lookup"><span data-stu-id="8b43f-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="8b43f-125">在 **“作业步骤列表”** 下，选择要删除的作业步骤，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="8b43f-125">Under **Job step list**, select the job step you want to delete and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="8b43f-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8b43f-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8b43f-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8b43f-127">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="8b43f-128">从 SQL Server 代理主作业中删除步骤</span><span class="sxs-lookup"><span data-stu-id="8b43f-128">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="8b43f-129">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="8b43f-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8b43f-130">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="8b43f-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8b43f-131">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="8b43f-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes job step 1 from the job Weekly Sales Data Backup   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="8b43f-132">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_jobstep ](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8b43f-132">For more information, see [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql).</span></span>  
  
  
