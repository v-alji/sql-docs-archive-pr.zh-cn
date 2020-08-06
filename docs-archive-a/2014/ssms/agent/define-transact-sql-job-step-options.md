---
title: 定义 Transact-SQL 作业步骤选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc1d6412e52e74ce0c6d987d6189c0c72ffd7df7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687412"
---
# <a name="define-transact-sql-job-step-options"></a><span data-ttu-id="0ba35-102">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="0ba35-102">Define Transact-SQL Job Step Options</span></span>
  <span data-ttu-id="0ba35-103">本主题说明如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用或 SQL Server 管理对象在中定义代理作业步骤的选项 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0ba35-103">This topic describes how to define options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="0ba35-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0ba35-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0ba35-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0ba35-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0ba35-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0ba35-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0ba35-107">**若要定义 Transact-SQL 作业步骤选项，请使用：** ，</span><span class="sxs-lookup"><span data-stu-id="0ba35-107">**To define Transact-SQL job step options, using:** ,</span></span>  
  
     [<span data-ttu-id="0ba35-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ba35-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0ba35-109">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0ba35-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0ba35-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="0ba35-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0ba35-111">Security</span><span class="sxs-lookup"><span data-stu-id="0ba35-111">Security</span></span>  
 <span data-ttu-id="0ba35-112">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba35-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0ba35-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0ba35-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-transact-sql-job-step-options"></a><span data-ttu-id="0ba35-114">定义 Transact-SQL 作业步骤选项</span><span class="sxs-lookup"><span data-stu-id="0ba35-114">To define Transact-SQL job step options</span></span>  
  
1.  <span data-ttu-id="0ba35-115">在 **对象资源管理器**中，展开 **“SQL Server 代理”**，展开 **“作业”**，右键单击要编辑的作业，然后单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="0ba35-115">In **Object Explorer**, expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0ba35-116">单击 **“步骤”** 页，单击一个作业步骤，再单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="0ba35-116">Click the **Steps** page, click a job step, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="0ba35-117">在 **“作业步骤属性”** 对话框上，确认作业类型为 **“Transact-SQL 脚本(TSQL)”**，然后选择 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="0ba35-117">On the **Job Step Properties** dialog, confirm that the job type is **Transact-SQL script (TSQL)**, and then select the **Advanced** page.</span></span>  
  
4.  <span data-ttu-id="0ba35-118">如果作业成功，请从 **“成功时要执行的操作”** 列表中进行选择，指定要采取的操作。</span><span class="sxs-lookup"><span data-stu-id="0ba35-118">Specify an action to take if the job is successful by selecting from the **On success action** list.</span></span>  
  
5.  <span data-ttu-id="0ba35-119">在 **“重试次数”** 框中输入 0 到 9999 之间的一个数字，指定重试的次数。</span><span class="sxs-lookup"><span data-stu-id="0ba35-119">Specify a number of retry attempts by entering a number from 0 to 9999 into the **Retry attempts** box.</span></span>  
  
6.  <span data-ttu-id="0ba35-120">在 **“重试间隔”** 框中输入 0 到 9999 的数字，指定重试的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0ba35-120">Specify a retry interval by entering a number of minutes from 0 to 9999 into the **Retry interval** box.</span></span>  
  
7.  <span data-ttu-id="0ba35-121">如果作业失败，请从 **“失败时要执行的操作”** 列表中进行选择，指定要采取的操作。</span><span class="sxs-lookup"><span data-stu-id="0ba35-121">Specify an action to take if the job fails by choosing from the **On failure action** list.</span></span>  
  
8.  <span data-ttu-id="0ba35-122">如果作业是一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，则可以从下列选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="0ba35-122">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="0ba35-123">输入 **输出文件**的名称。</span><span class="sxs-lookup"><span data-stu-id="0ba35-123">Enter the name of an **Output file**.</span></span> <span data-ttu-id="0ba35-124">默认情况下，每次执行作业步骤时都覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="0ba35-124">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="0ba35-125">如果不希望覆盖输出文件，请选中 **“将输出追加到现有文件”**。</span><span class="sxs-lookup"><span data-stu-id="0ba35-125">If you do not want the output file overwritten, check **Append output to existing file**.</span></span> <span data-ttu-id="0ba35-126">只有 **sysadmin** 固定服务器角色的成员才能设置此选项。</span><span class="sxs-lookup"><span data-stu-id="0ba35-126">This option is only available to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="0ba35-127">请注意， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 不允许用户查看文件系统中的任意文件。因此您不能使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 查看写入文件系统的作业步骤日志。</span><span class="sxs-lookup"><span data-stu-id="0ba35-127">Note that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not allow users to view arbitrary files on the file system, so you cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view job step logs that are written to the file system.</span></span>  
  
    -   <span data-ttu-id="0ba35-128">如果希望将作业步骤记录到一个数据库表中，请选中 **“记录到表”** 。</span><span class="sxs-lookup"><span data-stu-id="0ba35-128">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="0ba35-129">默认情况下，每次执行作业步骤时都覆盖该表的内容。</span><span class="sxs-lookup"><span data-stu-id="0ba35-129">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="0ba35-130">如果不希望覆盖表内容，则请选中 **“将输出追加到表中的现有条目”**。</span><span class="sxs-lookup"><span data-stu-id="0ba35-130">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="0ba35-131">在执行作业步骤后，您可以通过单击 **“查看”** 来查看此表的内容。</span><span class="sxs-lookup"><span data-stu-id="0ba35-131">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="0ba35-132">如果希望将输出包括在步骤的历史记录中，请选中 **“在历史记录中包含步骤输出”** 。</span><span class="sxs-lookup"><span data-stu-id="0ba35-132">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="0ba35-133">仅当没有错误时，才会显示输出结果。</span><span class="sxs-lookup"><span data-stu-id="0ba35-133">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="0ba35-134">此外，输出可能会被截断。</span><span class="sxs-lookup"><span data-stu-id="0ba35-134">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="0ba35-135">如果您是 **sysadmin** 固定服务器角色的成员，并且希望以其他 SQL 登录身份运行此作业步骤，请从 **“作为以下用户运行”** 列表中选择 SQL 登录名。</span><span class="sxs-lookup"><span data-stu-id="0ba35-135">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0ba35-136">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="0ba35-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0ba35-137">**定义 Transact-SQL 作业步骤选项**</span><span class="sxs-lookup"><span data-stu-id="0ba35-137">**To define Transact-SQL job step options**</span></span>  
  
 <span data-ttu-id="0ba35-138">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="0ba35-138">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
