---
title: 更改作业类别的成员身份 | Microsoft Docs
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
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9ed0db394f63594937ad923734b07fed8050955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591083"
---
# <a name="change-the-membership-of-a-job-category"></a><span data-ttu-id="c3959-102">Change the Membership of a Job Category</span><span class="sxs-lookup"><span data-stu-id="c3959-102">Change the Membership of a Job Category</span></span>
  <span data-ttu-id="c3959-103">本主题介绍如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]或 SQL Server 管理对象更改作业类别的成员身份。</span><span class="sxs-lookup"><span data-stu-id="c3959-103">This topic describes how to change the membership of the job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="c3959-104">作业类别有助于您组织作业，从而更容易筛选和分组。</span><span class="sxs-lookup"><span data-stu-id="c3959-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="c3959-105">可以创建自己的作业类别。</span><span class="sxs-lookup"><span data-stu-id="c3959-105">You can create your own job categories.</span></span> <span data-ttu-id="c3959-106">还可以更改作业类别中的 Microsoft SQL Server 代理作业成员身份。</span><span class="sxs-lookup"><span data-stu-id="c3959-106">You can also change Microsoft SQL Server Agent jobs membership in job categories.</span></span>  
  
 <span data-ttu-id="c3959-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="c3959-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c3959-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="c3959-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c3959-109">安全性</span><span class="sxs-lookup"><span data-stu-id="c3959-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c3959-110">**若要更改作业类别的成员身份，请使用**</span><span class="sxs-lookup"><span data-stu-id="c3959-110">**To change the membership of a job category, using:**</span></span>  
  
     [<span data-ttu-id="c3959-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c3959-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="c3959-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c3959-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="c3959-113">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="c3959-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c3959-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="c3959-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c3959-115">Security</span><span class="sxs-lookup"><span data-stu-id="c3959-115">Security</span></span>  
 <span data-ttu-id="c3959-116">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="c3959-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="c3959-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c3959-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="c3959-118">更改作业类别的成员身份</span><span class="sxs-lookup"><span data-stu-id="c3959-118">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="c3959-119">在 **“对象资源管理器”** 中，单击加号以展开您想要在其中编辑作业类别的服务器。</span><span class="sxs-lookup"><span data-stu-id="c3959-119">In **Object Explorer**, click the plus sign to expand the server where you want to edit a job category.</span></span>  
  
2.  <span data-ttu-id="c3959-120">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="c3959-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="c3959-121">右键单击 **“作业”** 文件夹，然后选择 **“管理作业类别”**。</span><span class="sxs-lookup"><span data-stu-id="c3959-121">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="c3959-122">在“管理作业类别” \*\*\*\*_server_name_ 对话框中，选择要编辑的作业类别，然后单击“查看作业” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3959-122">In the **Manage Job Categories**_server_name_ dialog box, select the job category that you want to edit, and then click **View Jobs**.</span></span>  
  
5.  <span data-ttu-id="c3959-123">选中 **“显示所有作业”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="c3959-123">Select the **Show all jobs** check box.</span></span>  
  
6.  <span data-ttu-id="c3959-124">若要向类别中添加作业，请在主网格中选中与作业对应的 **“选择”** 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="c3959-124">To add a job to the category, in the main grid, select the check box in the **Select** column corresponding to the job.</span></span> <span data-ttu-id="c3959-125">若要从类别中删除作业，请清除该框。</span><span class="sxs-lookup"><span data-stu-id="c3959-125">To remove a job from the category, clear the box.</span></span> <span data-ttu-id="c3959-126">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="c3959-126">When finished, click **OK**.</span></span>  
  
7.  <span data-ttu-id="c3959-127">关闭 "**管理作业类别**_server_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="c3959-127">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="c3959-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c3959-128">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="c3959-129">更改作业类别的成员身份</span><span class="sxs-lookup"><span data-stu-id="c3959-129">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="c3959-130">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="c3959-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3959-131">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="c3959-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c3959-132">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="c3959-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="c3959-133">有关详细信息，请参阅[&#40;transact-sql&#41;sp_update_job ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c3959-133">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="c3959-134">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="c3959-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="c3959-135">**更改作业类别的成员身份**</span><span class="sxs-lookup"><span data-stu-id="c3959-135">**To change the membership of a job category**</span></span>  
  
 <span data-ttu-id="c3959-136">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobCategory` 类。</span><span class="sxs-lookup"><span data-stu-id="c3959-136">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
