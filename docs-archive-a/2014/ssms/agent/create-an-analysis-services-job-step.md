---
title: 创建 Analysis Services 作业步骤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0e63c22d4cad270bcb544b03decba269e4f43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689265"
---
# <a name="create-an-analysis-services-job-step"></a><span data-ttu-id="2065f-102">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="2065f-102">Create an Analysis Services Job Step</span></span>
  <span data-ttu-id="2065f-103">本主题说明如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中创建和定义通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 SQL Server 管理对象执行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Analysis Services 命令和查询的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代理作业步骤。</span><span class="sxs-lookup"><span data-stu-id="2065f-103">This topic describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="2065f-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2065f-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2065f-105">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2065f-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2065f-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2065f-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2065f-107">**若要使用 Analysis Services 命令和/或查询创建 SQL Server 作业步骤，请使用：**</span><span class="sxs-lookup"><span data-stu-id="2065f-107">**To create a SQL Server job steps using Analysis Services commands and/or queries, with:**</span></span>  
  
     [<span data-ttu-id="2065f-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2065f-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="2065f-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2065f-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="2065f-110">SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="2065f-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2065f-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="2065f-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2065f-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2065f-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2065f-113">如果作业步骤使用 Analysis Services 命令，则命令语句必须是 XML for Analysis Services **Execute** 方法。</span><span class="sxs-lookup"><span data-stu-id="2065f-113">If the job step uses an Analysis Services command, the command statement must be an XML for Analysis Services **Execute** method.</span></span> <span data-ttu-id="2065f-114">该语句可以不包含完整的简单对象访问协议 (SOAP) 信封和 XML for Analysis **Discover** 方法。</span><span class="sxs-lookup"><span data-stu-id="2065f-114">The statement may not contain a complete Simple Object Access Protocol (SOAP) envelope or an XML for Analysis **Discover** method.</span></span> <span data-ttu-id="2065f-115">虽然 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 支持完整的 SOAP 信封和 **Discover** 方法，但是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤却不支持。</span><span class="sxs-lookup"><span data-stu-id="2065f-115">While [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span> <span data-ttu-id="2065f-116">有关 XML for Analysis Services 的详细信息，请参阅 [XML for Analysis 概述 (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2065f-116">For more information about XML for Analysis Services, see [XML for Analysis Overview (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx).</span></span>  
  
-   <span data-ttu-id="2065f-117">如果作业步骤使用 Analysis Services 查询，则查询语句必须是多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="2065f-117">If the job step uses an Analysis Services query, the query statement must be a multidimensional expressions (MDX) query.</span></span> <span data-ttu-id="2065f-118">有关 MDX 的详细信息，请参阅[Mdx Query 基础 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="2065f-118">For more information about MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2065f-119">Security</span><span class="sxs-lookup"><span data-stu-id="2065f-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2065f-120">权限</span><span class="sxs-lookup"><span data-stu-id="2065f-120">Permissions</span></span>  
  
-   <span data-ttu-id="2065f-121">若要运行使用 Analysis Services 子系统的作业步骤，用户必须是 **sysadmin** 固定服务器角色的成员或有权访问为使用该子系统而定义的有效代理帐户。</span><span class="sxs-lookup"><span data-stu-id="2065f-121">To run a job step that uses the Analysis Services subsystem, a user must be a member of the **sysadmin** fixed server role or have access to a valid proxy account defined to use this subsystem.</span></span> <span data-ttu-id="2065f-122">此外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户或代理必须是 Analysis Services 管理员或有效的 Windows 域帐户。</span><span class="sxs-lookup"><span data-stu-id="2065f-122">In addition, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account or the proxy must be an Analysis Services administrator and a valid Windows domain account.</span></span>  
  
-   <span data-ttu-id="2065f-123">只有 **sysadmin** 固定服务器角色的成员才可以将作业步骤输出写入到文件中。</span><span class="sxs-lookup"><span data-stu-id="2065f-123">Only members of the **sysadmin** fixed server role can write job step output to a file.</span></span> <span data-ttu-id="2065f-124">如果运行作业步骤的用户是 **msdb** 数据库中 **SQLAgentUserRole** 数据库角色的成员，则输出只能写入表中。</span><span class="sxs-lookup"><span data-stu-id="2065f-124">If the job step is run by users who are members of the **SQLAgentUserRole** database role in the **msdb** database, then the output can be written only to a table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2065f-125">代理会将作业步骤输出写入 **msdb** 数据库中的 **sysjobstepslog** 表。</span><span class="sxs-lookup"><span data-stu-id="2065f-125">Agent writes job step output to the **sysjobstepslog** table in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="2065f-126">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2065f-126">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="2065f-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2065f-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="2065f-128">创建 Analysis Services 命令作业步骤</span><span class="sxs-lookup"><span data-stu-id="2065f-128">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="2065f-129">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="2065f-129">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2065f-130">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2065f-130">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="2065f-131">有关创建作业的详细信息，请参阅 [创建作业](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="2065f-131">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="2065f-132">在 **“作业属性”** 对话框中，单击 **“步骤”** 页面，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-132">In the **Job Properties** dialog box, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2065f-133">在 **“新建作业步骤”** 对话框中，键入作业 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-133">In the **New Job Step** dialog box, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="2065f-134">在 **“类型”** 列表中，单击 **“SQL Server Analysis Services 命令”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-134">In the **Type** list, click **SQL Server Analysis Services Command**.</span></span>  
  
6.  <span data-ttu-id="2065f-135">在 **“运行身份”** 列表中，选择为使用 Analysis Services 命令子系统而定义的代理。</span><span class="sxs-lookup"><span data-stu-id="2065f-135">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Command subsystem.</span></span> <span data-ttu-id="2065f-136">如果用户是 **sysadmin** 固定服务器角色的成员，还可以选择 **“SQL Agent 服务帐户”** 运行此作业步骤。</span><span class="sxs-lookup"><span data-stu-id="2065f-136">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="2065f-137">选择用于运行作业步骤的 **“服务器”** 或键入服务器名称。</span><span class="sxs-lookup"><span data-stu-id="2065f-137">Select the **Server** where the job step will run, or type the server name.</span></span>  
  
8.  <span data-ttu-id="2065f-138">在 **“命令”** 框中，键入要执行的语句，或者单击 **“打开”** 选择一个语句。</span><span class="sxs-lookup"><span data-stu-id="2065f-138">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="2065f-139">单击 **“高级”** 页可定义此作业步骤的选项，例如在作业步骤成功或失败时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理所应执行的操作、作业步骤的尝试次数以及用于写入作业步骤输出的位置。</span><span class="sxs-lookup"><span data-stu-id="2065f-139">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="2065f-140">创建 Analysis Services 查询作业步骤</span><span class="sxs-lookup"><span data-stu-id="2065f-140">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="2065f-141">在**对象资源管理器中，** 连接到的实例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然后展开该实例。</span><span class="sxs-lookup"><span data-stu-id="2065f-141">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="2065f-142">展开“SQL Server 代理”\*\*\*\*，创建一个新作业或右键单击一个现有作业，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2065f-142">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="2065f-143">有关创建作业的详细信息，请参阅 [创建作业](create-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="2065f-143">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="2065f-144">在 **“作业属性”** 对话框中，单击 **“步骤”** 页，再单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-144">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2065f-145">在 **“新建作业步骤”** 对话框中，键入作业的 **“步骤名称”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-145">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="2065f-146">在 **“类型”** 列表中，单击 **“SQL Server Analysis Services 查询”**。</span><span class="sxs-lookup"><span data-stu-id="2065f-146">In the **Type** list, click **SQL Server Analysis Services Query**.</span></span>  
  
6.  <span data-ttu-id="2065f-147">在 **“运行身份”** 列表中，选择为使用 Analysis Services 查询子系统而定义的代理。</span><span class="sxs-lookup"><span data-stu-id="2065f-147">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Query subsystem.</span></span> <span data-ttu-id="2065f-148">如果用户是 **sysadmin** 固定服务器角色的成员，还可以选择 **“SQL Agent 服务帐户”** 运行此作业步骤。</span><span class="sxs-lookup"><span data-stu-id="2065f-148">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="2065f-149">选择用于运行作业步骤的 **“服务器”** 和 **“数据库”** ，或者键入服务器或数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="2065f-149">Select the **Server** and the **Database** where the job step will run, or type the server or database name.</span></span>  
  
8.  <span data-ttu-id="2065f-150">在 **“命令”** 框中，键入要执行的语句，或者单击 **“打开”** 选择一个语句。</span><span class="sxs-lookup"><span data-stu-id="2065f-150">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="2065f-151">单击 **“高级”** 页可定义此作业步骤的选项，例如在作业步骤成功或失败时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理所应执行的操作、作业步骤的尝试次数以及用于写入作业步骤输出的位置。</span><span class="sxs-lookup"><span data-stu-id="2065f-151">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="2065f-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2065f-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="2065f-153">创建 Analysis Services 命令作业步骤</span><span class="sxs-lookup"><span data-stu-id="2065f-153">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="2065f-154">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="2065f-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2065f-155">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2065f-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2065f-156">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2065f-156">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
        <ParentObject>  
            <DatabaseID>AdventureWorks2012</DatabaseID>  
        </ParentObject>  
        <ObjectDefinition>  
            <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
                <ID>AdventureWorks2012</ID>  
                <Name>Adventure Works 2012</Name>  
                <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorks2012;Integrated Security=True</ConnectionString>  
                <ImpersonationInfo>  
                    <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
                </ImpersonationInfo>  
                <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
                <Timeout>PT0S</Timeout>  
            </DataSource>  
        </ObjectDefinition>  
    </Create>', ;  
    GO  
    ```  
  
 <span data-ttu-id="2065f-157">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2065f-157">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="2065f-158">创建 Analysis Services 查询作业步骤</span><span class="sxs-lookup"><span data-stu-id="2065f-158">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="2065f-159">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="2065f-159">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2065f-160">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2065f-160">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2065f-161">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2065f-161">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses MDX to return data  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Returns the Internet sales amount by state',  
        @subsystem = N'ANALYSISQUERY',  
        @command = N' SELECT  
       [Measures].[Internet Sales Amount] ON COLUMNS,  
       [Customer].[State-Province].Members ON ROWS  
    FROM [AdventureWorks2012]',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="2065f-162">有关详细信息，请参阅[&#40;transact-sql&#41;sp_add_jobstep ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2065f-162">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="2065f-163">使用 SQL Server 管理对象</span><span class="sxs-lookup"><span data-stu-id="2065f-163">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="2065f-164">**创建 PowerShell 脚本作业步骤**</span><span class="sxs-lookup"><span data-stu-id="2065f-164">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="2065f-165">通过使用所选的编程语言（如 XMLA 或 MDX）来使用 `JobStep` 类。</span><span class="sxs-lookup"><span data-stu-id="2065f-165">Use the `JobStep` class by using a programming language that you choose, such as XMLA or MDX.</span></span> <span data-ttu-id="2065f-166">有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2065f-166">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
