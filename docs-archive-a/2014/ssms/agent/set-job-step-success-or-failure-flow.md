---
title: 设置作业步骤的成功流或失败流 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: fddc5820676cb231b6f0cd5f7151e24d8eceaefa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694205"
---
# <a name="set-job-step-success-or-failure-flow"></a><span data-ttu-id="a63c8-102">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="a63c8-102">Set Job Step Success or Failure Flow</span></span>
  <span data-ttu-id="a63c8-103">创建 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业时，可以指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作业执行期间发生故障时应采取的操作。</span><span class="sxs-lookup"><span data-stu-id="a63c8-103">When creating [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you can specify what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span> <span data-ttu-id="a63c8-104">根据每个作业步骤的成功或失败确定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a63c8-104">Determine the action that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take upon the success or failure of each job step.</span></span> <span data-ttu-id="a63c8-105">然后通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理使用以下过程配置作业步骤的操作流逻辑。</span><span class="sxs-lookup"><span data-stu-id="a63c8-105">Then use the following procedure to configure the job step action flow logic by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="a63c8-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a63c8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a63c8-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a63c8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a63c8-108">**若要设置作业步骤的成功流或失败流，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a63c8-108">**To set job step success or failure flow, using:**</span></span>  
  
     [<span data-ttu-id="a63c8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a63c8-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="a63c8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a63c8-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="a63c8-111">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="a63c8-111">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="a63c8-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="a63c8-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a63c8-113">Security</span><span class="sxs-lookup"><span data-stu-id="a63c8-113">Security</span></span>  
 <span data-ttu-id="a63c8-114">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a63c8-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="a63c8-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a63c8-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="a63c8-116">设置作业步骤的成功流或失败流</span><span class="sxs-lookup"><span data-stu-id="a63c8-116">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="a63c8-117">在 **对象资源管理器**中，展开 **“SQL Server 代理”**，然后展开 **“作业”**。</span><span class="sxs-lookup"><span data-stu-id="a63c8-117">In **Object Explorer**, expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
2.  <span data-ttu-id="a63c8-118">右键单击要编辑的作业，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a63c8-118">Right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a63c8-119">选择 **“步骤”** 页，单击一个步骤，再单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="a63c8-119">Select the **Steps** page, click a step, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="a63c8-120">在 **“作业步骤属性”** 对话框中，选择 **“高级”** 页。</span><span class="sxs-lookup"><span data-stu-id="a63c8-120">In the **Job Step Properties** dialog box, select the **Advanced** page.</span></span>  
  
5.  <span data-ttu-id="a63c8-121">在“成功时要执行的操作”\*\*\*\* 列表中，单击作业步骤成功完成时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a63c8-121">In the **On success action**list, click the action to perform if the job step completes successfully.</span></span>  
  
6.  <span data-ttu-id="a63c8-122">在 **“重试次数”** 框中输入介于 0 到 9999 之间的次数，应将作业步骤重复该次数，然后才能认为其失败。</span><span class="sxs-lookup"><span data-stu-id="a63c8-122">In the **Retry attempts** box, enter the number of times from 0 through 9999 that the job step should be repeated before it is considered to have failed.</span></span> <span data-ttu-id="a63c8-123">如果在“重试次数”\*\*\*\* 框中输入的值大于 0，则应在“重试间隔（分钟）”\*\*\*\* 框中输入介于 1 到 9999 之间的分钟数，必须经过该间隔后才能重试作业步骤。</span><span class="sxs-lookup"><span data-stu-id="a63c8-123">If you entered a value greater than 0 in the **Retry attempts** box, enter in the **Retry interval (minutes)** box the number of minutes from 1 through 9999 that must pass before the job step is retried.</span></span>  
  
7.  <span data-ttu-id="a63c8-124">在 **“失败时要执行的操作”** 列表中，单击作业步骤失败时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a63c8-124">In the **On failure action** list, click the action to perform if the job step fails.</span></span>  
  
8.  <span data-ttu-id="a63c8-125">如果作业是一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本，则可以从下列选项中进行选择：</span><span class="sxs-lookup"><span data-stu-id="a63c8-125">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="a63c8-126">在 **“输出文件”** 框中，输入要将脚本输出写入的输出文件名。</span><span class="sxs-lookup"><span data-stu-id="a63c8-126">In the **Output file** box, enter the name of an output file to which the script output will be written.</span></span> <span data-ttu-id="a63c8-127">默认情况下，每次执行作业步骤时都覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="a63c8-127">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="a63c8-128">如果不希望覆盖输出文件，请选中 **“将输出追加到现有文件”**。</span><span class="sxs-lookup"><span data-stu-id="a63c8-128">If you do not want the output file overwritten, check **Append output to existing file**.</span></span>  
  
    -   <span data-ttu-id="a63c8-129">如果希望将作业步骤记录到一个数据库表中，请选中 **“记录到表”** 。</span><span class="sxs-lookup"><span data-stu-id="a63c8-129">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="a63c8-130">默认情况下，每次执行作业步骤时都覆盖该表的内容。</span><span class="sxs-lookup"><span data-stu-id="a63c8-130">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="a63c8-131">如果不希望覆盖表内容，则请选中 **“将输出追加到表中的现有条目”**。</span><span class="sxs-lookup"><span data-stu-id="a63c8-131">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="a63c8-132">在执行作业步骤后，您可以通过单击 **“查看”** 来查看此表的内容。</span><span class="sxs-lookup"><span data-stu-id="a63c8-132">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="a63c8-133">如果希望将输出包括在步骤的历史记录中，请选中 **“在历史记录中包含步骤输出”** 。</span><span class="sxs-lookup"><span data-stu-id="a63c8-133">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="a63c8-134">仅当没有错误时，才会显示输出结果。</span><span class="sxs-lookup"><span data-stu-id="a63c8-134">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="a63c8-135">此外，输出可能会被截断。</span><span class="sxs-lookup"><span data-stu-id="a63c8-135">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="a63c8-136">如果 **“作为以下用户运行”** 列表可用，则选择具有作业要使用的凭据的代理帐户。</span><span class="sxs-lookup"><span data-stu-id="a63c8-136">If the **Run as user** list is available, select the proxy account with the credentials that the job will use.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="a63c8-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a63c8-137">Using Transact-SQL</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="a63c8-138">设置作业步骤的成功流或失败流</span><span class="sxs-lookup"><span data-stu-id="a63c8-138">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="a63c8-139">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a63c8-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a63c8-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a63c8-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a63c8-141">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a63c8-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
 <span data-ttu-id="a63c8-142">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a63c8-142">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="a63c8-143">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="a63c8-143">Using SQL Server Management Objects</span></span>  

### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="a63c8-144">设置作业步骤的成功流或失败流</span><span class="sxs-lookup"><span data-stu-id="a63c8-144">To set job step success or failure flow</span></span>
  
 <span data-ttu-id="a63c8-145">通过使用所选的编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="a63c8-145">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="a63c8-146">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a63c8-146">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
