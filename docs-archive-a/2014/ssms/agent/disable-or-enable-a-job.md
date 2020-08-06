---
title: 禁用或启用作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42fe7cbeed1e2ff3f93b1afef52b165a7d660ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577215"
---
# <a name="disable-or-enable-a-job"></a><span data-ttu-id="d41d5-102">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="d41d5-102">Disable or Enable a Job</span></span>
  <span data-ttu-id="d41d5-103">本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中禁用 [!INCLUDE[tsql](../../includes/tsql-md.md)]代理作业。</span><span class="sxs-lookup"><span data-stu-id="d41d5-103">This topic describes how to disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d41d5-104">禁用作业不会将其删除，必要时可以再次启用该作业。</span><span class="sxs-lookup"><span data-stu-id="d41d5-104">When you disable a job, it is not deleted and can be enabled again when necessary.</span></span>  
  
 <span data-ttu-id="d41d5-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d41d5-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d41d5-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d41d5-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d41d5-107">安全性</span><span class="sxs-lookup"><span data-stu-id="d41d5-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d41d5-108">**若要禁用或启用作业，请使用：**</span><span class="sxs-lookup"><span data-stu-id="d41d5-108">**To disable or enable a job, using:**</span></span>  
  
     [<span data-ttu-id="d41d5-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d41d5-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="d41d5-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d41d5-110">Transact-SQL</span></span>](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d41d5-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="d41d5-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d41d5-112">Security</span><span class="sxs-lookup"><span data-stu-id="d41d5-112">Security</span></span>  
 <span data-ttu-id="d41d5-113">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d41d5-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d41d5-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d41d5-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="d41d5-115">禁用或启用作业</span><span class="sxs-lookup"><span data-stu-id="d41d5-115">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="d41d5-116">在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="d41d5-116">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d41d5-117">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="d41d5-117">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="d41d5-118">展开“作业”\*\*\*\*，然后右键单击要禁用或启用的作业。</span><span class="sxs-lookup"><span data-stu-id="d41d5-118">Expand **Jobs**, and then right-click the job that you want to disable or enable.</span></span>  
  
4.  <span data-ttu-id="d41d5-119">若要禁用作业，请单击 **“禁用”**。</span><span class="sxs-lookup"><span data-stu-id="d41d5-119">To disable a job, click **Disable**.</span></span> <span data-ttu-id="d41d5-120">若要启用作业，请单击 **“启用”**。</span><span class="sxs-lookup"><span data-stu-id="d41d5-120">To enable a job, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="d41d5-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d41d5-121">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="d41d5-122">禁用或启用作业</span><span class="sxs-lookup"><span data-stu-id="d41d5-122">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="d41d5-123">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d41d5-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d41d5-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d41d5-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d41d5-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d41d5-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="d41d5-126">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_job ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d41d5-126">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
