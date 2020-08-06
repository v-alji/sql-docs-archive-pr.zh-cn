---
title: 查看作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 26406aaf2ba0ac4809eb7ac2c84799469d0468d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591718"
---
# <a name="view-a-job"></a><span data-ttu-id="eb785-102">View a Job</span><span class="sxs-lookup"><span data-stu-id="eb785-102">View a Job</span></span>
  <span data-ttu-id="eb785-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或在中查看代理作业 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eb785-103">This topic describes how to view [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb785-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="eb785-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb785-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="eb785-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb785-106">安全性</span><span class="sxs-lookup"><span data-stu-id="eb785-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eb785-107">**若要查看作业，可使用：**</span><span class="sxs-lookup"><span data-stu-id="eb785-107">**To view a job, using:**</span></span>  
  
     [<span data-ttu-id="eb785-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb785-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="eb785-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb785-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="eb785-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="eb785-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb785-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="eb785-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb785-112">Security</span><span class="sxs-lookup"><span data-stu-id="eb785-112">Security</span></span>  
 <span data-ttu-id="eb785-113">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能查看自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="eb785-113">You can only view jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="eb785-114">此角色的成员可以查看所有作业。</span><span class="sxs-lookup"><span data-stu-id="eb785-114">Members of this role can view all jobs.</span></span> <span data-ttu-id="eb785-115">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="eb785-115">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="eb785-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb785-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="eb785-117">查看作业</span><span class="sxs-lookup"><span data-stu-id="eb785-117">To view a job</span></span>  
  
1.  <span data-ttu-id="eb785-118">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="eb785-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="eb785-119">展开 **“SQL Server 代理”**，再展开 **“作业”**。</span><span class="sxs-lookup"><span data-stu-id="eb785-119">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="eb785-120">右键单击一个作业，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="eb785-120">Right-click a job, and then click **Properties**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="eb785-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb785-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="eb785-122">查看作业</span><span class="sxs-lookup"><span data-stu-id="eb785-122">To view a job</span></span>  
  
1.  <span data-ttu-id="eb785-123">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="eb785-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb785-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="eb785-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb785-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="eb785-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="eb785-126">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="eb785-126">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="eb785-127">**查看作业**</span><span class="sxs-lookup"><span data-stu-id="eb785-127">**To view a job**</span></span>  
  
 <span data-ttu-id="eb785-128">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `Job` 类。</span><span class="sxs-lookup"><span data-stu-id="eb785-128">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="eb785-129">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="eb785-129">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
