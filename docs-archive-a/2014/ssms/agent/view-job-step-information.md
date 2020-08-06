---
title: 查看作业步骤信息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d9fc6a006884bc564b5db2bfa8b168c8ae59149
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576527"
---
# <a name="view-job-step-information"></a><span data-ttu-id="aa27c-102">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="aa27c-102">View Job Step Information</span></span>
  <span data-ttu-id="aa27c-103">本主题说明如何在“作业步骤属性”对话框中查看作业步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="aa27c-103">This topic describes how to view job step details in the Job Step Properties dialog.</span></span> <span data-ttu-id="aa27c-104">它还包括有关查看作业步骤输出的信息。</span><span class="sxs-lookup"><span data-stu-id="aa27c-104">It also includes information about viewing job step output.</span></span>  
  
-   <span data-ttu-id="aa27c-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="aa27c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="aa27c-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa27c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="aa27c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="aa27c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="aa27c-108">**若要查看作业步骤信息，可使用：**</span><span class="sxs-lookup"><span data-stu-id="aa27c-108">**To view job step information, using:**</span></span>  
  
     [<span data-ttu-id="aa27c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa27c-109">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aa27c-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="aa27c-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="aa27c-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="aa27c-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="aa27c-112">如果已将作业步骤配置为将其输出写入到表或文件，并且作业已经至少运行过一次，则可以在 **“作业步骤属性”** 对话框的 **“高级”** 页上查看其输出。</span><span class="sxs-lookup"><span data-stu-id="aa27c-112">If the job step has been configured to write its output to a table or file and the job has run at least once, you can view its output on the **Advanced** page of the **Job Step Properties** dialog.</span></span> <span data-ttu-id="aa27c-113">作业或作业步骤删除时，输出日志也将自动删除。</span><span class="sxs-lookup"><span data-stu-id="aa27c-113">When a job or job step is deleted, the output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aa27c-114">Security</span><span class="sxs-lookup"><span data-stu-id="aa27c-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="aa27c-115">权限</span><span class="sxs-lookup"><span data-stu-id="aa27c-115">Permissions</span></span>  
 <span data-ttu-id="aa27c-116">您只能查看自己拥有的那些作业，除非您是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="aa27c-116">You can view only those jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="aa27c-117">此角色的成员可以查看所有作业和作业步骤的详细信息。</span><span class="sxs-lookup"><span data-stu-id="aa27c-117">Members of this role can view all jobs and job step details.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="aa27c-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="aa27c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-step-information"></a><span data-ttu-id="aa27c-119">查看作业步骤信息</span><span class="sxs-lookup"><span data-stu-id="aa27c-119">To view job step information</span></span>  
  
1.  <span data-ttu-id="aa27c-120">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="aa27c-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="aa27c-121">依次展开“SQL Server 代理”\*\*\*\* 和“作业”\*\*\*\*，右键单击包含要查看的作业步骤的作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa27c-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that contains the job step to be viewed, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="aa27c-122">在 **“作业属性”** 对话框中，单击 **“步骤”** 页。</span><span class="sxs-lookup"><span data-stu-id="aa27c-122">In the **Job Properties** dialog, click the **Steps** page.</span></span>  
  
4.  <span data-ttu-id="aa27c-123">单击要查看的作业步骤，再单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="aa27c-123">Click the job step to be viewed, and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="aa27c-124">在 **“作业步骤属性”** 对话框的 **“常规”** 页上，可以查看作业步骤的类型和用途。</span><span class="sxs-lookup"><span data-stu-id="aa27c-124">On the **General** page of the **Job Step Properties** dialog, you can view the type of job step and what it does.</span></span>  
  
6.  <span data-ttu-id="aa27c-125">单击 **“高级”** 页以查看作业步骤成功或失败时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理所执行的操作、该作业步骤应尝试的次数、该作业步骤输出的位置以及运行该作业步骤的用户。</span><span class="sxs-lookup"><span data-stu-id="aa27c-125">Click the **Advanced** page to view the actions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes if the job step succeeds or fails, how many times the job step should be attempted, where the job step output is written, and the user the job step runs as.</span></span>  
  
#### <a name="to-view-job-step-output"></a><span data-ttu-id="aa27c-126">查看作业步骤输出</span><span class="sxs-lookup"><span data-stu-id="aa27c-126">To view job step output</span></span>  
  
1.  <span data-ttu-id="aa27c-127">在 **“作业步骤属性”** 对话框中，单击 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="aa27c-127">In the **Job Step Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="aa27c-128">根据所连接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本，可以查看作业步骤输出文件或表，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aa27c-128">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connected to, you can view either the job step output file or table as follows:</span></span>  
  
    -   <span data-ttu-id="aa27c-129">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或更高版本时，只有选中 **“记录到表”** ，才能单击 **“查看”** 。</span><span class="sxs-lookup"><span data-stu-id="aa27c-129">When you are connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later, you can click **View** only when **Log to table** is checked.</span></span> <span data-ttu-id="aa27c-130">在这种情况下，作业步骤输出将写入 **msdb** 数据库的 **sysjobstepslogs** 表中。</span><span class="sxs-lookup"><span data-stu-id="aa27c-130">In this case, the job step output is written to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
    -   <span data-ttu-id="aa27c-131">在作业步骤输出写入到文件时，禁用 **“查看”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="aa27c-131">The **View** button is disabled when job step output is written to a file.</span></span> <span data-ttu-id="aa27c-132">若要查看作业步骤输出文件，请使用记事本。</span><span class="sxs-lookup"><span data-stu-id="aa27c-132">To view a job step output file, use Notepad.</span></span>  
  
  
