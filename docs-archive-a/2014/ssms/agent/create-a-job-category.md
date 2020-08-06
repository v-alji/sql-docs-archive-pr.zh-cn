---
title: 创建作业类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f6daeeca6253861e8a9dcbb72faa2bd55eb2761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691496"
---
# <a name="create-a-job-category"></a><span data-ttu-id="cf261-102">创建作业类别</span><span class="sxs-lookup"><span data-stu-id="cf261-102">Create a Job Category</span></span>
  <span data-ttu-id="cf261-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 管理对象在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建作业类别。</span><span class="sxs-lookup"><span data-stu-id="cf261-103">This topic describes how to create a job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf261-104">代理提供了内置作业类别，可以向这些类别分配作业，也可以创建作业类别并对其分配作业。</span><span class="sxs-lookup"><span data-stu-id="cf261-104">Agent provides built-in job categories that you can assign jobs to, or you can create a job category and assign jobs to it.</span></span> <span data-ttu-id="cf261-105">作业类别有助于您组织作业，从而更容易筛选和分组。</span><span class="sxs-lookup"><span data-stu-id="cf261-105">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="cf261-106">例如，可以将所有数据库备份作业组织到“数据库维护”类别中。</span><span class="sxs-lookup"><span data-stu-id="cf261-106">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="cf261-107">此外，还可以创建自己的作业类别。</span><span class="sxs-lookup"><span data-stu-id="cf261-107">You can also create your own job categories.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf261-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="cf261-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cf261-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cf261-109">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cf261-110">多服务器类别仅存在于主服务器上。</span><span class="sxs-lookup"><span data-stu-id="cf261-110">Multiserver categories exist only on a master server.</span></span> <span data-ttu-id="cf261-111">主服务器上仅提供了一个默认作业类别：“[未分类(多服务器)]”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf261-111">There is only one default job category available on a master server: [**Uncategorized (Multi-Server)**].</span></span> <span data-ttu-id="cf261-112">下载多服务器作业后，其类别将在目标服务器上更改为“来自 MSX 的作业” \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="cf261-112">When a multiserver job is downloaded, its category is changed to **Jobs From MSX** at the target server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf261-113">Security</span><span class="sxs-lookup"><span data-stu-id="cf261-113">Security</span></span>  
 <span data-ttu-id="cf261-114">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="cf261-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="cf261-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf261-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="cf261-116">创建作业类别</span><span class="sxs-lookup"><span data-stu-id="cf261-116">To create a job category</span></span>  
  
1.  <span data-ttu-id="cf261-117">在 **“对象资源管理器”** 中，单击加号以展开您想要在其中创建作业类别的服务器。</span><span class="sxs-lookup"><span data-stu-id="cf261-117">In **Object Explorer**, click the plus sign to expand the server where you want to create a job category.</span></span>  
  
2.  <span data-ttu-id="cf261-118">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="cf261-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="cf261-119">右键单击 **“作业”** 文件夹，然后选择 **“管理作业类别”**。</span><span class="sxs-lookup"><span data-stu-id="cf261-119">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="cf261-120">在“管理作业类别” \*\*\*\*_server_name_ 对话框中，单击“添加” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf261-120">In the **Manage Job Categories**_server_name_ dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="cf261-121">在新对话框的 **“名称”** 框中，输入新作业类别的名称。</span><span class="sxs-lookup"><span data-stu-id="cf261-121">In the new dialog box, in the **Name** box, enter a name for the new job category.</span></span>  
  
6.  <span data-ttu-id="cf261-122">选中 **“显示所有作业”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="cf261-122">Select the **Show all jobs** check box.</span></span> <span data-ttu-id="cf261-123">通过选中作业对应的框来为新类别选择一个或多个作业。</span><span class="sxs-lookup"><span data-stu-id="cf261-123">Select one or more jobs for the new category by checking the boxes corresponding to the jobs.</span></span>  
  
7.  <span data-ttu-id="cf261-124">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="cf261-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="cf261-125">在“管理作业类别” \*\*\*\*_server_name_ 对话框中，单击“刷新” \*\*\*\* 以确保新的作业类别处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="cf261-125">In the **Manage Job Categories**_server_name_ dialog box, click **Refresh** to ensure that the new job category is active.</span></span> <span data-ttu-id="cf261-126">如果一切都与预期情况相同，则关闭此对话框。</span><span class="sxs-lookup"><span data-stu-id="cf261-126">If everything looks as expected, close this dialog box.</span></span>  
  
 <span data-ttu-id="cf261-127">有关这些对话框的详细信息，请参阅[作业类别：管理作业类别](job-categories-manage-job-categories.md)和[作业类别属性和新作业类别](job-categories-properties-new-job-category.md)。</span><span class="sxs-lookup"><span data-stu-id="cf261-127">For more information on these dialog boxes, see [Job Categories: Manage Job Categories](job-categories-manage-job-categories.md) and [Job Categories Properties and New Job Category](job-categories-properties-new-job-category.md).</span></span>  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="cf261-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf261-128">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="cf261-129">创建作业类别</span><span class="sxs-lookup"><span data-stu-id="cf261-129">To create a job category</span></span>  
  
1.  <span data-ttu-id="cf261-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cf261-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf261-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="cf261-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf261-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="cf261-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="cf261-133">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_category ](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cf261-133">For more information, see [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="cf261-134">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="cf261-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="cf261-135">**创建作业类别**</span><span class="sxs-lookup"><span data-stu-id="cf261-135">**To create a job category**</span></span>  
  
 <span data-ttu-id="cf261-136">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `JobCategory` 类。</span><span class="sxs-lookup"><span data-stu-id="cf261-136">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="cf261-137">有关示例代码，请参阅 [在 SQL Server 代理中计划自动管理任务](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="cf261-137">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
