---
title: 创建 SQL Server 代理作业以存档数据库邮件和事件日志 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- archiving mail messages and attachments [SQL Server]
- removing mail messages and attachements
- Database Mail [SQL Server], archiving
- saving mail messages and attachments
ms.assetid: 8f8f0fba-f750-4533-9b76-a9cdbcdc3b14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b958b280c358a8aeb752600dee1c2aee31d14db1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580293"
---
# <a name="create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs"></a><span data-ttu-id="7872d-102">创建 SQL Server 代理作业以存档数据库邮件和事件日志</span><span class="sxs-lookup"><span data-stu-id="7872d-102">Create a SQL Server Agent Job to Archive Database Mail Messages and Event Logs</span></span>
  <span data-ttu-id="7872d-103">数据库邮件及其附件的副本与数据库邮件事件日志一起保存在 **msdb** 表中。</span><span class="sxs-lookup"><span data-stu-id="7872d-103">Copies of Database Mail messages and their attachments are retained in **msdb** tables along with the Database Mail event log.</span></span> <span data-ttu-id="7872d-104">您可能希望定期减小这些表的大小并对不再需要的邮件和事件进行存档。</span><span class="sxs-lookup"><span data-stu-id="7872d-104">Periodically you might want to reduce the size of the tables and archive messages and events that are no longer needed.</span></span> <span data-ttu-id="7872d-105">下列过程将创建一个 SQL Server 代理作业，以自动完成上述过程。</span><span class="sxs-lookup"><span data-stu-id="7872d-105">The following procedures create a SQL Server Agent job to automate the process.</span></span>  
  
-   <span data-ttu-id="7872d-106">**开始之前：** [先决条件](#Prerequisites)、[建议](#Recommendations)、[权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="7872d-106">**Before you begin:**  , [Prerequisites](#Prerequisites), [Recommendations](#Recommendations), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="7872d-107">**使用以下方法存档数据库邮件和日志：** [SQL Server 代理](#Process_Overview)</span><span class="sxs-lookup"><span data-stu-id="7872d-107">**To Archive Database Mail messages and logs using :**  [SQL Server Agent](#Process_Overview)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7872d-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="7872d-108">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="7872d-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="7872d-109">Prerequisites</span></span>  
 <span data-ttu-id="7872d-110">用于存储存档数据的新表可以位于特殊的存档数据库中。</span><span class="sxs-lookup"><span data-stu-id="7872d-110">The new tables to store the archive data might be located in a special archive database.</span></span> <span data-ttu-id="7872d-111">另外，还可将行导出到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="7872d-111">Alternatively the rows could be exported to a text file.</span></span>  
 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="7872d-112">建议</span><span class="sxs-lookup"><span data-stu-id="7872d-112">Recommendations</span></span>  
 <span data-ttu-id="7872d-113">在生产环境中，可能需要进一步添加错误检查，并在作业失败的情况下向操作员发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="7872d-113">In your production environment, you might want to add additional error checking and send an e-mail message to operators if the job fails.</span></span>  
  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7872d-114">权限</span><span class="sxs-lookup"><span data-stu-id="7872d-114">Permissions</span></span>  
 <span data-ttu-id="7872d-115">只有 **sysadmin** 固定服务器角色的成员才能执行本主题中介绍的存储过程。</span><span class="sxs-lookup"><span data-stu-id="7872d-115">You must be a member of the **sysadmin** fixed server role to execute the stored procedures described in this topic.</span></span>  
  
  
###  <a name="overview-of-the-process"></a><a name="Process_Overview"></a> <span data-ttu-id="7872d-116">过程概述</span><span class="sxs-lookup"><span data-stu-id="7872d-116">Overview of the Process</span></span>  
  
-   <span data-ttu-id="7872d-117">第一个过程创建一个名为“存档数据库邮件”的作业，其中包含下列步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-117">The first procedure creates a job named Archive Database Mail with the following steps.</span></span>  
  
    1.  <span data-ttu-id="7872d-118">将所有邮件从数据库邮件表中复制到一个格式为 **DBMailArchive_** _<year_month>_ 且用上一个月份命名的新表中。</span><span class="sxs-lookup"><span data-stu-id="7872d-118">Copy all messages from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_**_<year_month>_.</span></span>  
  
    2.  <span data-ttu-id="7872d-119">将与第一个步骤中复制的邮件相关的附件从数据库邮件表中复制到格式为 **DBMailArchive_Attachments_** <year_month> 且用上一个月份命名的新表中。</span><span class="sxs-lookup"><span data-stu-id="7872d-119">Copy the attachments related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Attachments_**_<year_month>_.</span></span>  
  
    3.  <span data-ttu-id="7872d-120">将数据库邮件事件日志中与第一个步骤中复制的邮件相关的事件从数据库邮件表中复制到格式为 **DBMailArchive_Log_** <year_month> 且用上一个月份命名的新表中。</span><span class="sxs-lookup"><span data-stu-id="7872d-120">Copy the events from the Database Mail event log that are related to the messages copied in the first step, from the Database Mail tables to a new table named after the previous month in the format **DBMailArchive_Log_**_<year_month>_.</span></span>  
  
    4.  <span data-ttu-id="7872d-121">从数据库邮件表中删除已传输邮件项的记录。</span><span class="sxs-lookup"><span data-stu-id="7872d-121">Delete the records of the transferred mail items from the Database Mail tables.</span></span>  
  
    5.  <span data-ttu-id="7872d-122">从数据库邮件事件日志中删除与已传输邮件项相关的事件。</span><span class="sxs-lookup"><span data-stu-id="7872d-122">Delete the events related to the transferred mail items from the Database Mail event log.</span></span>  
  
-   <span data-ttu-id="7872d-123">安排定期运行作业。</span><span class="sxs-lookup"><span data-stu-id="7872d-123">Schedule the job to run periodically.</span></span>  
 
  
## <a name="to-create-a-sql-server-agent-job"></a><span data-ttu-id="7872d-124">创建 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="7872d-124">To create a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="7872d-125">在对象资源管理器中，展开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，右键单击“作业”，然后单击“新建作业”。</span><span class="sxs-lookup"><span data-stu-id="7872d-125">In Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, and then click **New Job**.</span></span>  
  
2.  <span data-ttu-id="7872d-126">在 **“新建作业”** 对话框的 **“名称”** 框中，键入 **“存档数据库邮件”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-126">In the **New Job** dialog box, in the **Name** box, type **Archive Database Mail**.</span></span>  
  
3.  <span data-ttu-id="7872d-127">在 **“所有者”** 框中，确定所有者是 **sysadmin** 固定服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="7872d-127">In the **Owner** box, confirm that the owner is a member of the **sysadmin** fixed server role.</span></span>  
  
4.  <span data-ttu-id="7872d-128">在 **“类别”** 框中，单击 **“数据库维护”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-128">In the **Category** box, click the **Database Maintenance**.</span></span>  
  
5.  <span data-ttu-id="7872d-129">在 **“说明”** 框中，键入 **“存档数据库邮件”** ，然后单击 **“步骤”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-129">In the **Description** box, type **Archive Database Mail messages**, and then click **Steps**.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-messages"></a><span data-ttu-id="7872d-130">创建步骤以存档数据库邮件</span><span class="sxs-lookup"><span data-stu-id="7872d-130">To create a step to archive the Database Mail messages</span></span>  
  
1.  <span data-ttu-id="7872d-131">在 **“步骤”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-131">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="7872d-132">在 **“步骤名称”** 框中，键入 **“复制数据库邮件项”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-132">In the **Step name** box, type **Copy Database Mail Items**.</span></span>  
  
3.  <span data-ttu-id="7872d-133">在“类型”框中，选择“Transact-SQL 脚本 (T-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="7872d-133">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="7872d-134">在 **“数据库”** 框中，选择 **msdb**。</span><span class="sxs-lookup"><span data-stu-id="7872d-134">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="7872d-135">在 **“命令”** 框中，键入以下语句以创建用上一个月份命名的表，在其中包含早于当前月份的开始日期的行：</span><span class="sxs-lookup"><span data-stu-id="7872d-135">In the **Command** box, type the following statement to create a table named after the previous month, containing rows older than the start of the current month:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_' + @LastMonth + '] FROM sysmail_allitems WHERE send_request_date < ''' + @CopyDate +'''';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="7872d-136">单击 **“确定”** 保存步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-136">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-attachments"></a><span data-ttu-id="7872d-137">创建步骤以存档数据库邮件附件</span><span class="sxs-lookup"><span data-stu-id="7872d-137">To create a step to archive the Database Mail attachments</span></span>  
  
1.  <span data-ttu-id="7872d-138">在 **“步骤”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-138">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="7872d-139">在 **“步骤名称”** 框中，键入 **“复制数据库邮件附件”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-139">In the **Step name** box, type **Copy Database Mail Attachments**.</span></span>  
  
3.  <span data-ttu-id="7872d-140">在“类型”框中，选择“Transact-SQL 脚本 (T-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="7872d-140">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="7872d-141">在 **“数据库”** 框中，选择 **msdb**。</span><span class="sxs-lookup"><span data-stu-id="7872d-141">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="7872d-142">在 **“命令”** 框中，键入以下语句以创建用上一个月份命名的附件表，在其中包含与上一步中转移的邮件相对应的附件：</span><span class="sxs-lookup"><span data-stu-id="7872d-142">In the **Command** box, type the following statement to create an attachments table named after the previous month, containing the attachments that correspond to the messages transferred in the previous step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Attachments_' + @LastMonth + '] FROM sysmail_attachments   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="7872d-143">单击 **“确定”** 保存步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-143">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-archive-the-database-mail-log"></a><span data-ttu-id="7872d-144">创建步骤以存档数据库邮件日志</span><span class="sxs-lookup"><span data-stu-id="7872d-144">To create a step to archive the Database Mail log</span></span>  
  
1.  <span data-ttu-id="7872d-145">在 **“步骤”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-145">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="7872d-146">在 **“步骤名称”** 框中，键入 **“复制数据库邮件日志”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-146">In the **Step name** box, type **Copy Database Mail Log**.</span></span>  
  
3.  <span data-ttu-id="7872d-147">在“类型”框中，选择“Transact-SQL 脚本 (T-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="7872d-147">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="7872d-148">在 **“数据库”** 框中，选择 **msdb**。</span><span class="sxs-lookup"><span data-stu-id="7872d-148">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="7872d-149">在 **“命令”** 框中，键入以下语句以创建用上一个月份命名的日志表，在其中包含与在前面的步骤中传输的邮件相对应的日志项：</span><span class="sxs-lookup"><span data-stu-id="7872d-149">In the **Command** box, type the following statement to create a log table named after the previous month, containing the log entries that correspond to the messages transferred in the earlier step:</span></span>  
  
    ```  
    DECLARE @LastMonth nvarchar(12);  
    DECLARE @CopyDate nvarchar(20) ;  
    DECLARE @CreateTable nvarchar(250) ;  
    SET @LastMonth = (SELECT CAST(DATEPART(yyyy,GETDATE()) AS CHAR(4)) + '_' + CAST(DATEPART(mm,GETDATE())-1 AS varchar(2))) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime))  
    SET @CreateTable = 'SELECT * INTO msdb.dbo.[DBMailArchive_Log_' + @LastMonth + '] FROM sysmail_Event_Log   
     WHERE mailitem_id in (SELECT DISTINCT mailitem_id FROM [DBMailArchive_' + @LastMonth + '] )';  
    EXEC sp_executesql @CreateTable ;  
    ```  
  
6.  <span data-ttu-id="7872d-150">单击 **“确定”** 保存步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-150">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-rows-from-database-mail"></a><span data-ttu-id="7872d-151">创建步骤以从数据库邮件中删除已存档的行</span><span class="sxs-lookup"><span data-stu-id="7872d-151">To create a step to remove the archived rows from Database Mail</span></span>  
  
1.  <span data-ttu-id="7872d-152">在 **“步骤”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-152">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="7872d-153">在 **“步骤名称”** 框中，键入 **“从数据库邮件中删除行”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-153">In the **Step name** box, type **Remove rows from Database Mail**.</span></span>  
  
3.  <span data-ttu-id="7872d-154">在“类型”框中，选择“Transact-SQL 脚本 (T-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="7872d-154">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="7872d-155">在 **“数据库”** 框中，选择 **msdb**。</span><span class="sxs-lookup"><span data-stu-id="7872d-155">In the **Database** box, select **msdb**.</span></span>  
  
5.  <span data-ttu-id="7872d-156">在 **“命令”** 框中，键入以下语句以从数据库邮件表中删除早于当前月份的行：</span><span class="sxs-lookup"><span data-stu-id="7872d-156">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail tables:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @CopyDate ;  
    ```  
  
6.  <span data-ttu-id="7872d-157">单击 **“确定”** 保存步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-157">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-create-a-step-to-remove-the-archived-items-from-database-mail-event-log"></a><span data-ttu-id="7872d-158">创建步骤以从数据库邮件事件日志中删除已存档的项</span><span class="sxs-lookup"><span data-stu-id="7872d-158">To create a step to remove the archived items from Database Mail event log</span></span>  
  
1.  <span data-ttu-id="7872d-159">在 **“步骤”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-159">On the **Steps** page, click **New**.</span></span>  
  
2.  <span data-ttu-id="7872d-160">在 **“步骤名称”** 框中，键入 **“从数据库邮件事件日志中删除行”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-160">In the **Step Name** box type **Remove rows from Database Mail event log**.</span></span>  
  
3.  <span data-ttu-id="7872d-161">在“类型”框中，选择“Transact-SQL 脚本 (T-SQL)”。</span><span class="sxs-lookup"><span data-stu-id="7872d-161">In the **Type** box, select **Transact-SQL script (T-SQL)**.</span></span>  
  
4.  <span data-ttu-id="7872d-162">在 **“命令”** 框中，键入以下语句以从数据库邮件事件日志中删除早于当前月份的行：</span><span class="sxs-lookup"><span data-stu-id="7872d-162">In the **Command** box, type the following statement to remove rows older than the current month from the Database Mail event log:</span></span>  
  
    ```  
    DECLARE @CopyDate nvarchar(20) ;  
    SET @CopyDate = (SELECT CAST(CONVERT(char(8), CURRENT_TIMESTAMP- DATEPART(dd,GETDATE()-1), 112) AS datetime)) ;  
    EXECUTE msdb.dbo.sysmail_delete_log_sp @logged_before = @CopyDate ;  
    ```  
  
5.  <span data-ttu-id="7872d-163">单击 **“确定”** 保存步骤。</span><span class="sxs-lookup"><span data-stu-id="7872d-163">Click **OK** to save the step.</span></span>  
  
  
  
## <a name="to-schedule-the-job-to-run-periodically"></a><span data-ttu-id="7872d-164">安排定期运行作业</span><span class="sxs-lookup"><span data-stu-id="7872d-164">To schedule the job to run periodically</span></span>  
  
1.  <span data-ttu-id="7872d-165">在 **“新建作业”** 对话框中，单击 **“计划”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-165">In the **New Job** dialog box, click **Schedules**.</span></span>  
  
2.  <span data-ttu-id="7872d-166">在 **“计划”** 页上，单击 **“新建”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-166">On the **Schedules** page, click **New**.</span></span>  
  
3.  <span data-ttu-id="7872d-167">在 **“名称”** 框中，键入 **“存档数据库邮件”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-167">In the **Name** box, type **Archive Database Mail**.</span></span>  
  
4.  <span data-ttu-id="7872d-168">在 **“计划类型”** 框中，选择 **“重复执行”** 。</span><span class="sxs-lookup"><span data-stu-id="7872d-168">In the **Schedule type** box, select **Recurring**.</span></span>  
  
5.  <span data-ttu-id="7872d-169">在 **“频率”** 区域中，选择相应的选项以便定期运行该作业，比如每月一次。</span><span class="sxs-lookup"><span data-stu-id="7872d-169">In the **Frequency** area, select the options to run the job periodically, for example once every month.</span></span>  
  
6.  <span data-ttu-id="7872d-170">在“每天频率”区域中，选择“在 \<time> 执行一次” 。</span><span class="sxs-lookup"><span data-stu-id="7872d-170">In the **Daily frequency** area, select **Occurs once at \<time>**.</span></span>  
  
7.  <span data-ttu-id="7872d-171">验证其他选项已按您希望的那样进行了配置，然后单击 **“确定”** 保存计划。</span><span class="sxs-lookup"><span data-stu-id="7872d-171">Verify that the other options are configured as you wish, and then click **OK** to save the schedule.</span></span>  
  
8.  <span data-ttu-id="7872d-172">单击 **“确定”** 保存作业。</span><span class="sxs-lookup"><span data-stu-id="7872d-172">Click **OK** to save the job.</span></span>  
  
  
  
  
