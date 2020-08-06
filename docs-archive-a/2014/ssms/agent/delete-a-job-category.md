---
title: 删除作业类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e96dd0461f3dace138b7822cdbaaa2fa242e2cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687411"
---
# <a name="delete-a-job-category"></a><span data-ttu-id="02fa2-102">删除作业类别</span><span class="sxs-lookup"><span data-stu-id="02fa2-102">Delete a Job Category</span></span>
  <span data-ttu-id="02fa2-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理对象在中删除代理作业类别 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02fa2-103">This topic describes how to delete a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="02fa2-104">作业类别有助于您组织作业，从而更容易筛选和分组。</span><span class="sxs-lookup"><span data-stu-id="02fa2-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="02fa2-105">例如，可以将所有数据库备份作业组织到“数据库维护”类别中。</span><span class="sxs-lookup"><span data-stu-id="02fa2-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span>  

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="02fa2-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="02fa2-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="02fa2-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="02fa2-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="02fa2-108">在删除用户定义的作业类别时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将提示您，将分配给它的作业重新分配给其他作业类别。</span><span class="sxs-lookup"><span data-stu-id="02fa2-108">When you delete a user-defined job category, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prompts you to reassign the jobs that are assigned to it to another job category.</span></span> <span data-ttu-id="02fa2-109">仅可以删除用户定义的作业类别。</span><span class="sxs-lookup"><span data-stu-id="02fa2-109">You can only delete user-defined job categories.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="02fa2-110">Security</span><span class="sxs-lookup"><span data-stu-id="02fa2-110">Security</span></span>  
 <span data-ttu-id="02fa2-111">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="02fa2-111">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="02fa2-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="02fa2-112">Using SQL Server Management Studio</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="02fa2-113">删除作业类别</span><span class="sxs-lookup"><span data-stu-id="02fa2-113">To delete a job category</span></span>  
  
1.  <span data-ttu-id="02fa2-114">在 **“对象资源管理器”** 中，单击加号以展开您想要在其中删除作业类别的服务器。</span><span class="sxs-lookup"><span data-stu-id="02fa2-114">In **Object Explorer**, click the plus sign to expand the server where you want to delete a job category.</span></span>  
  
2.  <span data-ttu-id="02fa2-115">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="02fa2-115">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="02fa2-116">右键单击 **“作业”** 文件夹，然后选择 **“管理作业类别”**。</span><span class="sxs-lookup"><span data-stu-id="02fa2-116">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="02fa2-117">在“管理作业类别” \*\*\*\*_server_name_ 对话框中，选择要删除的作业类别。</span><span class="sxs-lookup"><span data-stu-id="02fa2-117">In the **Manage Job Categories**_server_name_ dialog box, select the job category to delete.</span></span>  
  
5.  <span data-ttu-id="02fa2-118">单击“删除” 。</span><span class="sxs-lookup"><span data-stu-id="02fa2-118">Click **Delete**.</span></span>  
  
6.  <span data-ttu-id="02fa2-119">在 **“作业类别”** 对话框中，单击 **“是”**。</span><span class="sxs-lookup"><span data-stu-id="02fa2-119">In the **Job Categories** dialog box, click **Yes**.</span></span>  
  
7.  <span data-ttu-id="02fa2-120">关闭 "**管理作业类别**_server_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="02fa2-120">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="02fa2-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="02fa2-121">Using Transact-SQL</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="02fa2-122">删除作业类别</span><span class="sxs-lookup"><span data-stu-id="02fa2-122">To delete a job category</span></span>  
  
1.  <span data-ttu-id="02fa2-123">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="02fa2-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="02fa2-124">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="02fa2-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="02fa2-125">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="02fa2-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 <span data-ttu-id="02fa2-126">有关详细信息，请参阅[&#40;transact-sql&#41;sp_delete_category ](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="02fa2-126">For more information, see [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).</span></span>  

  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="02fa2-127">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="02fa2-127">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-a-job-category"></a><span data-ttu-id="02fa2-128">删除作业类别</span><span class="sxs-lookup"><span data-stu-id="02fa2-128">To delete a job category</span></span>
  
 <span data-ttu-id="02fa2-129">通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 `JobCategory` 类。</span><span class="sxs-lookup"><span data-stu-id="02fa2-129">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
