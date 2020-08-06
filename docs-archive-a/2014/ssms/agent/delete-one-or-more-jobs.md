---
title: 删除一个或多个作业 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 436625f9ad629a6b0e574aa046059f4e7e9c2bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578006"
---
# <a name="delete-one-or-more-jobs"></a><span data-ttu-id="63032-102">删除一个或多个作业</span><span class="sxs-lookup"><span data-stu-id="63032-102">Delete One or More Jobs</span></span>
  <span data-ttu-id="63032-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理对象在中删除代理作业 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63032-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="63032-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="63032-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="63032-105">Security</span><span class="sxs-lookup"><span data-stu-id="63032-105">Security</span></span>  
 <span data-ttu-id="63032-106">除非你是 **sysadmin** 固定服务器角色的成员，否则只能删除自己拥有的作业。</span><span class="sxs-lookup"><span data-stu-id="63032-106">Unless you are a member of the **sysadmin** fixed server role, you can only delete jobs that you own.</span></span>  
  
 
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="63032-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63032-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="63032-108">删除作业</span><span class="sxs-lookup"><span data-stu-id="63032-108">To delete a job</span></span>  
  
1.  <span data-ttu-id="63032-109">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="63032-109">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="63032-110">依次展开“SQL Server 代理”\*\*\*\* 和“作业”\*\*\*\*，右键单击要删除的作业，再单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63032-110">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="63032-111">在“删除对象”\*\*\*\* 对话框中，确认选择了要删除的作业。</span><span class="sxs-lookup"><span data-stu-id="63032-111">In the **Delete Object** dialog box, confirm that the job you intend to delete is selected.</span></span>  
  
4.  <span data-ttu-id="63032-112">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="63032-112">Click **OK**.</span></span>  
  
#### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="63032-113">删除多个作业</span><span class="sxs-lookup"><span data-stu-id="63032-113">To delete multiple jobs</span></span>  
  
1.  <span data-ttu-id="63032-114">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="63032-114">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="63032-115">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="63032-115">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="63032-116">右键单击“作业活动监视器”\*\*\*\*，然后单击“查看作业活动”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63032-116">Right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="63032-117">在作业活动监视器中，选择要删除的作业，右键单击选择的作业，然后选择“删除作业”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63032-117">In the Job Activity Monitor, select the jobs you want to delete, right-click your selection, and choose **Delete jobs**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="63032-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="63032-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="63032-119">删除作业</span><span class="sxs-lookup"><span data-stu-id="63032-119">To delete a job</span></span>  
  
1.  <span data-ttu-id="63032-120">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="63032-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="63032-121">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="63032-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="63032-122">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="63032-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="63032-123">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_job ](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="63032-123">For more information, see [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="63032-124">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="63032-124">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="63032-125">删除多个作业</span><span class="sxs-lookup"><span data-stu-id="63032-125">To delete multiple jobs</span></span>
  
 <span data-ttu-id="63032-126">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobCollection` 类。</span><span class="sxs-lookup"><span data-stu-id="63032-126">Use the `JobCollection` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="63032-127">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="63032-127">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
