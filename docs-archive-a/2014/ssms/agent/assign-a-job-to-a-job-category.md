---
title: 将作业分配到作业类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 208ff6722a9c18fd4dd0d061575f0d496af27810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591086"
---
# <a name="assign-a-job-to-a-job-category"></a><span data-ttu-id="ed307-102">将作业分配到作业类别</span><span class="sxs-lookup"><span data-stu-id="ed307-102">Assign a Job to a Job Category</span></span>
  <span data-ttu-id="ed307-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理对象将代理作业分配到中的作业类别 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ed307-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to job categories in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="ed307-104">作业类别有助于您组织作业，从而更容易筛选和分组。</span><span class="sxs-lookup"><span data-stu-id="ed307-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="ed307-105">例如，可以将所有数据库备份作业组织到“数据库维护”类别中。</span><span class="sxs-lookup"><span data-stu-id="ed307-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="ed307-106">可以将作业分配到内置作业类别，也可以创建用户定义的作业类别，然后将作业分配至其中。</span><span class="sxs-lookup"><span data-stu-id="ed307-106">You can assign jobs to built-in job categories, or you can create a user-defined job category and then assign jobs to that.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed307-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="ed307-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed307-108">Security</span><span class="sxs-lookup"><span data-stu-id="ed307-108">Security</span></span>  
 <span data-ttu-id="ed307-109">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ed307-109">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="ed307-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ed307-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="ed307-111">将作业分配到作业类别</span><span class="sxs-lookup"><span data-stu-id="ed307-111">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="ed307-112">在 **“对象资源管理器”** 中，单击加号以展开要将作业分配到作业类别的服务器。</span><span class="sxs-lookup"><span data-stu-id="ed307-112">In **Object Explorer**, click the plus sign to expand the server where you want to assign a job to a job category.</span></span>  
  
2.  <span data-ttu-id="ed307-113">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="ed307-113">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="ed307-114">单击加号以便展开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ed307-114">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="ed307-115">右键单击要编辑的作业，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed307-115">Right-click the job you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="ed307-116">在“作业属性 - job_name”\*\*\*\*__ 对话框的“类别”\*\*\*\* 列表中，选择要分配给作业的作业类别。</span><span class="sxs-lookup"><span data-stu-id="ed307-116">In the **Job Properties -**_job_name_ dialog box, in the **Category** list, select the job category you want to assign to the job.</span></span>  
  
6.  <span data-ttu-id="ed307-117">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ed307-117">Click **OK**.</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="ed307-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ed307-118">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="ed307-119">将作业分配到作业类别</span><span class="sxs-lookup"><span data-stu-id="ed307-119">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="ed307-120">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="ed307-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ed307-121">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="ed307-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ed307-122">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="ed307-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="ed307-123">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_job ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ed307-123">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="ed307-124">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="ed307-124">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="ed307-125">**将作业分配到作业类别**</span><span class="sxs-lookup"><span data-stu-id="ed307-125">**To assign a job to a job category**</span></span>  
  
 <span data-ttu-id="ed307-126">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobCategory` 类。</span><span class="sxs-lookup"><span data-stu-id="ed307-126">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
  
  
