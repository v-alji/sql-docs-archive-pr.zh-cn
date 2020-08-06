---
title: 设置 SQL Server 托管备份到 Azure |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b9e3b86fde91028106263310aad8a1952fc041a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590221"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a><span data-ttu-id="f85e6-102">设置针对 Azure 的 SQL Server 托管备份</span><span class="sxs-lookup"><span data-stu-id="f85e6-102">Setting up SQL Server Managed Backup to Azure</span></span>
  <span data-ttu-id="f85e6-103">本主题包括两个教程：</span><span class="sxs-lookup"><span data-stu-id="f85e6-103">This topic includes two tutorials:</span></span>  
  
 <span data-ttu-id="f85e6-104">在数据库级别设置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]、启用电子邮件通知和监视备份活动。</span><span class="sxs-lookup"><span data-stu-id="f85e6-104">Set up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="f85e6-105">在实例级别设置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]、启用电子邮件通知和监视备份活动。</span><span class="sxs-lookup"><span data-stu-id="f85e6-105">Setting up  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the instance level, enable email notification, and monitor backup activity.</span></span>  
  
 <span data-ttu-id="f85e6-106">有关为可用性组设置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的教程，请参阅为[可用性组 Microsoft Azure 设置 SQL Server 托管备份](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-106">For a tutorial on setting up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for Availability Groups, see [Setting up SQL Server Managed Backup to Microsoft Azure for Availability Groups](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
## <a name="setting-up-ss_smartbackup"></a><span data-ttu-id="f85e6-107">设置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85e6-107">Setting Up [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span></span>  
  
### <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><span data-ttu-id="f85e6-108">为数据库启用和配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85e6-108">Enable and Configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="f85e6-109">本教程首先介绍为数据库 (TestDB) 启用和配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]所需的步骤，然后介绍允许监视 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]运行状况的步骤。</span><span class="sxs-lookup"><span data-stu-id="f85e6-109">This tutorial describes the steps necessary to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a database (TestDB), followed by steps to enable monitoring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="f85e6-110">**权限：**</span><span class="sxs-lookup"><span data-stu-id="f85e6-110">**Permissions:**</span></span>  
  
-   <span data-ttu-id="f85e6-111">要求具有**db_backupoperator**数据库角色的成员身份、具有**ALTER ANY CREDENTIAL**权限以及 `EXECUTE` 对**sp_delete_backuphistory**存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="f85e6-111">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="f85e6-112">需要对**smart_admin fn_get_current_xevent_settings**函数的**SELECT**权限。</span><span class="sxs-lookup"><span data-stu-id="f85e6-112">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="f85e6-113">需要 `EXECUTE` 对 smart_admin 的权限**sp_get_backup_diagnostics**存储过程。</span><span class="sxs-lookup"><span data-stu-id="f85e6-113">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="f85e6-114">此外，它还需要 `VIEW SERVER STATE` 权限，因为它在内部调用其他需要此权限的系统对象。</span><span class="sxs-lookup"><span data-stu-id="f85e6-114">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="f85e6-115">需要 `EXECUTE` 对 `smart_admin.sp_set_instance_backup` 和 `smart_admin.sp_backup_master_switch` 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="f85e6-115">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  


1.  <span data-ttu-id="f85e6-116">**创建 Microsoft Azure 的存储帐户：** 备份存储在 Microsoft Azure 存储服务中。</span><span class="sxs-lookup"><span data-stu-id="f85e6-116">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="f85e6-117">如果还没有帐户，则必须先创建一个 Microsoft Azure 的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-117">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="f85e6-118">SQL Server 2014 使用不同于块 blob 和追加 blob 的页 blob。</span><span class="sxs-lookup"><span data-stu-id="f85e6-118">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="f85e6-119">因此，您必须创建一个常规用途帐户，而不是一个 blob 帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-119">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="f85e6-120">有关详细信息，请参阅[有关 Azure 存储帐户](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-120">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="f85e6-121">请记录存储帐户名称和访问密钥。</span><span class="sxs-lookup"><span data-stu-id="f85e6-121">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="f85e6-122">存储帐户名称和访问密钥用于创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="f85e6-122">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="f85e6-123">使用 SQL 凭据对存储帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f85e6-123">The SQL Credential is used to authenticate to the storage account.</span></span>  
 
2.  <span data-ttu-id="f85e6-124">**创建 SQL 凭据：** 使用存储帐户的名称作为标识，并使用存储访问密钥作为密码创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="f85e6-124">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="f85e6-125">**确保已启动并正在运行 SQL Server 代理服务：** 如果当前未运行，则启动 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="f85e6-125">**Ensure SQL Server Agent service is Started and Running:**  Start SQL Server Agent if it is not currently running.</span></span>  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="f85e6-126">需要实例上运行有 SQL Server 代理才能执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="f85e6-126">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="f85e6-127">可能要将 SQL Server 代理设置为自动运行，以确保可定期进行备份操作。</span><span class="sxs-lookup"><span data-stu-id="f85e6-127">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="f85e6-128">**确定保持期：** 确定备份文件的保持期。</span><span class="sxs-lookup"><span data-stu-id="f85e6-128">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="f85e6-129">以天为单位指定保持期，范围可为 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="f85e6-129">The retention period is specified in days and can range from 1 to 30.</span></span>  
  
5.  <span data-ttu-id="f85e6-130">**启用和配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ：** 启动 SQL Server Management Studio 并连接到安装了数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="f85e6-130">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance where the database is installed.</span></span> <span data-ttu-id="f85e6-131">在根据要求修改数据库名称、SQL 凭据、保持期和加密选项的值后，从查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-131">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="f85e6-132">有关创建用于加密的证书的详细信息，请参阅[创建加密的备份](create-an-encrypted-backup.md)中的**创建备份证书**步骤。</span><span class="sxs-lookup"><span data-stu-id="f85e6-132">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="f85e6-133">。</span><span class="sxs-lookup"><span data-stu-id="f85e6-133">is now enabled on the database you specified.</span></span> <span data-ttu-id="f85e6-134">数据库上的备份操作最多可能需要 15 分钟才能运行。</span><span class="sxs-lookup"><span data-stu-id="f85e6-134">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span>  
  
6.  <span data-ttu-id="f85e6-135">**查看扩展事件默认配置：** 通过运行以下 transact-SQL 语句，检查扩展事件设置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-135">**Review Extended Event Default Configuration:** Review the Extended Event settings by running the following transact-SQL statement.</span></span>  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="f85e6-136">应看到默认情况下启用管理、操作和分析通道事件，且无法禁用这些事件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-136">You should see that Admin, Operational, and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="f85e6-137">这对于需要手动干预的事件来说应当已经足够。</span><span class="sxs-lookup"><span data-stu-id="f85e6-137">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="f85e6-138">您可以启用调试事件，但是调试通道包含 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 用来检测问题和解决问题的信息性事件和调试事件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-138">You can enable debug events, but the debug channels include informational and debug events that [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="f85e6-139">有关详细信息，请参阅[监视 SQL Server 托管备份到 Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-139">For more information, see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
7.  <span data-ttu-id="f85e6-140">**启用和配置运行状况通知：** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 有一个存储过程，它创建代理作业以发出可能需要注意的错误或警告的电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="f85e6-140">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span> <span data-ttu-id="f85e6-141">以下步骤说明了启用和配置电子邮件通知的过程：</span><span class="sxs-lookup"><span data-stu-id="f85e6-141">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="f85e6-142">如果尚未在此实例上启用数据库邮件，请进行设置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-142">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="f85e6-143">有关详细信息，请参阅 [Configure Database Mail](../database-mail/configure-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-143">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="f85e6-144">将 SQL Server 代理通知配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-144">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="f85e6-145">有关详细信息，请参阅 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-145">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="f85e6-146">**启用电子邮件通知以接收备份错误和警告：** 在查询窗口中，运行以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-146">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         <span data-ttu-id="f85e6-147">有关详细信息和完整的示例脚本，请参阅[监视 SQL Server 托管备份到 Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-147">For more information, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
8.  <span data-ttu-id="f85e6-148">**在 Microsoft Azure 存储帐户中查看备份文件：** 从 SQL Server Management Studio 或 Azure 管理门户中连接到存储帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-148">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="f85e6-149">您将看到一个 SQL Server 实例的容器，其中承载您配置为使用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的数据库。</span><span class="sxs-lookup"><span data-stu-id="f85e6-149">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="f85e6-150">您也会在为数据库启用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的 15 分钟内，看到数据库和日志备份。</span><span class="sxs-lookup"><span data-stu-id="f85e6-150">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
9. <span data-ttu-id="f85e6-151">**监视运行状态：** 可以通过以前配置的电子邮件通知进行监视，也可以主动监控记录的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-151">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="f85e6-152">以下是一些用于查看事件的示例 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-152">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="f85e6-153">本节中描述的步骤是专门用于在数据库上首次配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f85e6-153">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="f85e6-154">您可以使用相同的系统存储过程**smart_admin sp_set_db_backup**来修改现有配置，并提供新值。</span><span class="sxs-lookup"><span data-stu-id="f85e6-154">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="f85e6-155">有关详细信息，请参阅[SQL Server 托管备份到 Microsoft Azure 保留和存储设置](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-155">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="enable-ss_smartbackup-for-the-instance-with-default-settings"></a><span data-ttu-id="f85e6-156">使用默认设置为实例启用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85e6-156">Enable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the Instance with Default Settings</span></span>  
 <span data-ttu-id="f85e6-157">本教程介绍为 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 实例 "MyInstance" 启用和配置的步骤 \\ 。</span><span class="sxs-lookup"><span data-stu-id="f85e6-157">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for the instance, 'MyInstance',\\.</span></span> <span data-ttu-id="f85e6-158">其中包括允许监视 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 运行状况的步骤。</span><span class="sxs-lookup"><span data-stu-id="f85e6-158">It includes steps to enable monitoring the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
 <span data-ttu-id="f85e6-159">**权限：**</span><span class="sxs-lookup"><span data-stu-id="f85e6-159">**Permissions:**</span></span>  
  
-   <span data-ttu-id="f85e6-160">要求具有**db_backupoperator**数据库角色的成员身份、具有**ALTER ANY CREDENTIAL**权限以及 `EXECUTE` 对**sp_delete_backuphistory**存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="f85e6-160">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="f85e6-161">需要对**smart_admin fn_get_current_xevent_settings**函数的**SELECT**权限。</span><span class="sxs-lookup"><span data-stu-id="f85e6-161">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="f85e6-162">需要 `EXECUTE` 对 smart_admin 的权限**sp_get_backup_diagnostics**存储过程。</span><span class="sxs-lookup"><span data-stu-id="f85e6-162">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="f85e6-163">此外，它还需要 `VIEW SERVER STATE` 权限，因为它在内部调用其他需要此权限的系统对象。</span><span class="sxs-lookup"><span data-stu-id="f85e6-163">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  


1.  <span data-ttu-id="f85e6-164">**创建 Microsoft Azure 的存储帐户：** 备份存储在 Microsoft Azure 存储服务中。</span><span class="sxs-lookup"><span data-stu-id="f85e6-164">**Create a Microsoft Azure storage account:** The backups are stored in the Microsoft Azure storage service.</span></span> <span data-ttu-id="f85e6-165">如果还没有帐户，则必须先创建一个 Microsoft Azure 的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-165">You must first create a Microsoft Azure storage account, if you do not already have an account.</span></span>
    - <span data-ttu-id="f85e6-166">SQL Server 2014 使用不同于块 blob 和追加 blob 的页 blob。</span><span class="sxs-lookup"><span data-stu-id="f85e6-166">SQL Server 2014 uses page blobs, which are different than block and append blobs.</span></span> <span data-ttu-id="f85e6-167">因此，您必须创建一个常规用途帐户，而不是一个 blob 帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-167">Therefore you must create a general purpose account, and not a blob account.</span></span> <span data-ttu-id="f85e6-168">有关详细信息，请参阅[有关 Azure 存储帐户](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-168">For more information, see [About Azure storage accounts](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span>
    - <span data-ttu-id="f85e6-169">请记录存储帐户名称和访问密钥。</span><span class="sxs-lookup"><span data-stu-id="f85e6-169">Make a note of the storage account name, and the access keys.</span></span> <span data-ttu-id="f85e6-170">存储帐户名称和访问密钥用于创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="f85e6-170">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="f85e6-171">使用 SQL 凭据对存储帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f85e6-171">The SQL Credential is used to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="f85e6-172">**创建 SQL 凭据：** 使用存储帐户的名称作为标识，并使用存储访问密钥作为密码创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="f85e6-172">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="f85e6-173">**确保 SQL Server 代理服务已启动且正在运行：** 如果 SQL Server 代理当前未运行，请启动它。</span><span class="sxs-lookup"><span data-stu-id="f85e6-173">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] <span data-ttu-id="f85e6-174">需要实例上运行有 SQL Server 代理才能执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="f85e6-174">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="f85e6-175">可能要将 SQL Server 代理设置为自动运行，以确保可定期进行备份操作。</span><span class="sxs-lookup"><span data-stu-id="f85e6-175">You may want to set SQL Server Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="f85e6-176">**确定保持期：** 确定备份文件的保持期。</span><span class="sxs-lookup"><span data-stu-id="f85e6-176">**Determine the retention period:** Determine the retention period for the backup files.</span></span> <span data-ttu-id="f85e6-177">以天为单位指定保持期，范围可为 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="f85e6-177">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="f85e6-178">在实例级别使用默认值启用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 后，此后创建的所有新数据库将继承这些设置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-178">Once [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is enabled at the instance level with the defaults all new databases created thereafter will inherit the settings.</span></span> <span data-ttu-id="f85e6-179">只会支持和自动配置设置为完整或大容量日志恢复模式的数据库。</span><span class="sxs-lookup"><span data-stu-id="f85e6-179">Only databases that are set to full or bulk-logged recovery models are supported and will be configured automatically.</span></span> <span data-ttu-id="f85e6-180">如果您不想配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]，您可以随时为特定数据库禁用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f85e6-180">You may disable [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] for a specific database at any time if you  do not want [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configured.</span></span> <span data-ttu-id="f85e6-181">还可通过在数据库级别配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]，更改特定数据库的配置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-181">You can also change the configuration for a specific database by configuring [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
5.  <span data-ttu-id="f85e6-182">**启用和配置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ：** 启动 SQL Server Management Studio 并连接到 SQL Server 的实例。</span><span class="sxs-lookup"><span data-stu-id="f85e6-182">**Enable and configure [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** Start SQL Server Management Studio and connect to the instance of SQL Server.</span></span> <span data-ttu-id="f85e6-183">在根据要求修改数据库名称、SQL 凭据、保持期和加密选项的值之后，在查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-183">From the query window run the following statement after you modify the values for the database name, SQL Credential, retention period, and the encryption options per your requirements:</span></span>  
  
     <span data-ttu-id="f85e6-184">有关创建用于加密的证书的详细信息，请参阅[创建加密的备份](create-an-encrypted-backup.md)中的**创建备份证书**步骤。</span><span class="sxs-lookup"><span data-stu-id="f85e6-184">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](create-an-encrypted-backup.md).</span></span>  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     <span data-ttu-id="f85e6-185">现在，已对实例启用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f85e6-185">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] is now enabled on the instance.</span></span>  
  
6.  <span data-ttu-id="f85e6-186">通过运行以下 Transact-SQL 语句验证配置设置：</span><span class="sxs-lookup"><span data-stu-id="f85e6-186">Verify the configuration settings by running the following Transact-SQL statement:</span></span>  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  <span data-ttu-id="f85e6-187">在实例上创建新数据库。</span><span class="sxs-lookup"><span data-stu-id="f85e6-187">Create a new database on the instance.</span></span> <span data-ttu-id="f85e6-188">运行以下 Transact-SQL 语句，查看数据库的 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 配置设置：</span><span class="sxs-lookup"><span data-stu-id="f85e6-188">Run the following Transact-SQL statement to view the [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] configuration settings for the database:</span></span>  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     <span data-ttu-id="f85e6-189">最多可能需要 15 分钟才能显示设置，并开始运行数据库的备份操作。</span><span class="sxs-lookup"><span data-stu-id="f85e6-189">It may take up to 15 minutes for the settings to show and backup operations on the database to start to run.</span></span>  
  
8.  <span data-ttu-id="f85e6-190">**启用和配置运行状况通知：** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 有一个存储过程，它创建代理作业以发出可能需要注意的错误或警告的电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="f85e6-190">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="f85e6-191">若要接收此类通知，必须允许运行这个创建 SQL Server 代理作业的存储过程。</span><span class="sxs-lookup"><span data-stu-id="f85e6-191">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="f85e6-192">以下步骤说明了启用和配置电子邮件通知的过程：</span><span class="sxs-lookup"><span data-stu-id="f85e6-192">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="f85e6-193">如果尚未在此实例上启用数据库邮件，请进行设置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-193">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="f85e6-194">有关详细信息，请参阅 [Configure Database Mail](../database-mail/configure-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-194">For more information, see [Configure Database Mail](../database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="f85e6-195">将 SQL Server 代理通知配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-195">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="f85e6-196">有关详细信息，请参阅 [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-196">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="f85e6-197">**启用电子邮件通知以接收备份错误和警告：** 在查询窗口中，运行以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-197">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         <span data-ttu-id="f85e6-198">有关如何监视的详细信息和完整的示例脚本，请参阅[监视 SQL Server 托管备份到 Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="f85e6-198">For more information about how to monitor, and a full sample script see [Monitor SQL Server Managed Backup to Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="f85e6-199">**在 Microsoft Azure 存储帐户中查看备份文件：** 从 SQL Server Management Studio 或 Azure 管理门户中连接到存储帐户。</span><span class="sxs-lookup"><span data-stu-id="f85e6-199">**View backup files in the Microsoft Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="f85e6-200">您将看到一个 SQL Server 实例的容器，其中承载您配置为使用 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的数据库。</span><span class="sxs-lookup"><span data-stu-id="f85e6-200">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="f85e6-201">您也会在创建新数据库 15 分钟内，看到数据库和日志备份。</span><span class="sxs-lookup"><span data-stu-id="f85e6-201">You may also see a database and a log backup within 15 minutes of creating a new database.</span></span>  
  
10. <span data-ttu-id="f85e6-202">**监视运行状态：** 可以通过以前配置的电子邮件通知进行监视，也可以主动监控记录的事件。</span><span class="sxs-lookup"><span data-stu-id="f85e6-202">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="f85e6-203">以下是一些用于查看事件的示例 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="f85e6-203">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 <span data-ttu-id="f85e6-204">可通过专门在数据库级别配置设置，在特定数据库中取代 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 默认设置。</span><span class="sxs-lookup"><span data-stu-id="f85e6-204">[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] default settings can be overridden for a specific database by configuring the settings specifically at the database level.</span></span> <span data-ttu-id="f85e6-205">您还可以临时暂停和继续运行 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f85e6-205">You can also pause and resume [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] service temporarily.</span></span> <span data-ttu-id="f85e6-206">有关详细信息，请参阅[SQL Server 托管备份到 Microsoft Azure 保留和存储设置](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f85e6-206">For more information, see [SQL Server Managed Backup to Microsoft Azure - Retention and Storage Settings](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)</span></span>  
  
  
