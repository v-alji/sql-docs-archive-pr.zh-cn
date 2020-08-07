---
title: 删除作业步骤日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
ms.openlocfilehash: de7c64c4d7cf461eef563ae6989e043d125c6f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587695"
---
# <a name="delete-a-job-step-log"></a><span data-ttu-id="1da97-102">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="1da97-102">Delete a Job Step Log</span></span>
  <span data-ttu-id="1da97-103">本主题介绍如何删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤日志。</span><span class="sxs-lookup"><span data-stu-id="1da97-103">This topic describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>  
  
-   <span data-ttu-id="1da97-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="1da97-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1da97-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1da97-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1da97-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1da97-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1da97-107">**若要删除 SQL Server 代理作业步骤日志，可使用：**</span><span class="sxs-lookup"><span data-stu-id="1da97-107">**To delete a SQL Server Agent job step log, using:**</span></span>  
  
     [<span data-ttu-id="1da97-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1da97-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="1da97-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1da97-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="1da97-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="1da97-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1da97-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="1da97-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1da97-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="1da97-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1da97-113">删除作业步骤时，将自动删除其输出日志。</span><span class="sxs-lookup"><span data-stu-id="1da97-113">When job steps are deleted their output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1da97-114">Security</span><span class="sxs-lookup"><span data-stu-id="1da97-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1da97-115">权限</span><span class="sxs-lookup"><span data-stu-id="1da97-115">Permissions</span></span>  
 <span data-ttu-id="1da97-116">除非您是 **sysadmin** 固定服务器角色的成员，否则您只能修改自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="1da97-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="1da97-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1da97-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="1da97-118">删除 SQL Server 代理作业步骤日志</span><span class="sxs-lookup"><span data-stu-id="1da97-118">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="1da97-119">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="1da97-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="1da97-120">展开“SQL Server 代理”\*\*\*\*，再展开“作业”\*\*\*\*，然后右键单击要修改的作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1da97-120">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1da97-121">在 **“作业属性”** 对话框中，删除所选作业步骤。</span><span class="sxs-lookup"><span data-stu-id="1da97-121">In the **Job Properties** dialog box, delete the selected job step.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="1da97-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1da97-122">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a><span data-ttu-id="1da97-123">删除 SQL Server 代理作业步骤日志</span><span class="sxs-lookup"><span data-stu-id="1da97-123">To delete a SQL Server Agent job step log</span></span>  
  
1.  <span data-ttu-id="1da97-124">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="1da97-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1da97-125">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="1da97-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1da97-126">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="1da97-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 <span data-ttu-id="1da97-127">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_jobsteplog ](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1da97-127">For more information, see [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="1da97-128">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="1da97-128">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="1da97-129">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `DeleteJobStepLogs` 类的 `Job` 方法。</span><span class="sxs-lookup"><span data-stu-id="1da97-129">Use the `DeleteJobStepLogs` methods of the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="1da97-130">有关详细信息，请参阅[SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1da97-130">For more information, see[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
  
```powershell
# Delete all job step log files that have ID values larger than 5.  
$srv = New-Object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```
