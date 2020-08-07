---
title: SQL Server 备份到 URL 最佳做法和故障排除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06127b5e4b422750554c30fae23b6190107cb643
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587871"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a><span data-ttu-id="3b611-102">SQL Server 备份到 URL 最佳实践和故障排除</span><span class="sxs-lookup"><span data-stu-id="3b611-102">SQL Server Backup to URL Best Practices and Troubleshooting</span></span>
  <span data-ttu-id="3b611-103">本主题介绍 SQL Server 备份和还原到 Azure Blob 服务的最佳做法和故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="3b611-103">This topic includes best practices and troubleshooting tips for SQL Server backup and restores to the Azure Blob service.</span></span>  
  
 <span data-ttu-id="3b611-104">有关将 Azure Blob 存储服务用于 SQL Server 备份或还原操作的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="3b611-104">For more information about using Azure Blob storage service for SQL Server backup or restore operations, see:</span></span>  
  
-   [<span data-ttu-id="3b611-105">使用 Azure Blob 存储服务执行 SQL Server 备份和还原</span><span class="sxs-lookup"><span data-stu-id="3b611-105">SQL Server Backup and Restore with Azure Blob Storage Service</span></span>](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [<span data-ttu-id="3b611-106">教程：将 SQL Server 备份和还原到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="3b611-106">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a><span data-ttu-id="3b611-107">管理备份</span><span class="sxs-lookup"><span data-stu-id="3b611-107">Managing Backups</span></span>  
 <span data-ttu-id="3b611-108">下表列出了管理备份的一般建议：</span><span class="sxs-lookup"><span data-stu-id="3b611-108">The following list includes general recommendations to manage backups:</span></span>  
  
-   <span data-ttu-id="3b611-109">建议为每个备份使用唯一文件名以防止意外覆盖 blob。</span><span class="sxs-lookup"><span data-stu-id="3b611-109">Unique file name for every backup is recommended to prevent accidentally overwriting the blobs.</span></span>  
  
-   <span data-ttu-id="3b611-110">创建容器时，建议将访问级别设置为 **“私有”** ，这样只有可以提供所需的身份验证信息的用户或帐户可以在容器中读取或写入 blob。</span><span class="sxs-lookup"><span data-stu-id="3b611-110">When creating a container, it is recommended that you set the access level to **private**, so only users or accounts that can provide the required authentication information can read or write the blobs in the container.</span></span>  
  
-   <span data-ttu-id="3b611-111">对于在 Azure 虚拟机中运行 SQL Server 实例上的 SQL Server 数据库，请使用虚拟机所在区域中的存储帐户，以避免区域之间的数据传输成本。</span><span class="sxs-lookup"><span data-stu-id="3b611-111">For SQL Server databases on an instance of SQL Server running in an Azure Virtual Machine, use a storage account in the same region as the virtual machine to avoid data transfer costs between regions.</span></span> <span data-ttu-id="3b611-112">使用同一区域还可以确保备份和还原操作具有最佳性能。</span><span class="sxs-lookup"><span data-stu-id="3b611-112">Using the same region also ensures optimal performance for backup and restore operations.</span></span>  
  
-   <span data-ttu-id="3b611-113">失败的备份活动可能导致无效的备份文件。</span><span class="sxs-lookup"><span data-stu-id="3b611-113">Failed backup activity can result in an invalid backup file.</span></span> <span data-ttu-id="3b611-114">我们建议定期标识失败的备份和删除 blob 文件。</span><span class="sxs-lookup"><span data-stu-id="3b611-114">We recommend periodic identification of failed backups and deleting the blob files.</span></span> <span data-ttu-id="3b611-115">有关详细信息，请参阅 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span><span class="sxs-lookup"><span data-stu-id="3b611-115">For more information, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
-   <span data-ttu-id="3b611-116">在备份期间使用 `WITH COMPRESSION` 选项可以最大程度降低存储成本和存储事务成本。</span><span class="sxs-lookup"><span data-stu-id="3b611-116">Using the `WITH COMPRESSION` option during backup can minimize your storage costs and storage transaction costs.</span></span> <span data-ttu-id="3b611-117">它也会减少完成备份过程所需的时间。</span><span class="sxs-lookup"><span data-stu-id="3b611-117">It can also decrease the time taken to complete the backup process.</span></span>  
  
## <a name="handling-large-files"></a><span data-ttu-id="3b611-118">处理大型文件</span><span class="sxs-lookup"><span data-stu-id="3b611-118">Handling Large Files</span></span>  
  
-   <span data-ttu-id="3b611-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份操作使用多个线程来优化与 Azure Blob 存储服务的数据传输。</span><span class="sxs-lookup"><span data-stu-id="3b611-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup operation uses multiple threads to optimize data transfer to Azure Blob storage services.</span></span>  <span data-ttu-id="3b611-120">但是性能取决于各种因素，如 ISV 带宽和数据库的大小。</span><span class="sxs-lookup"><span data-stu-id="3b611-120">However the performance depends on various factors, such as ISV bandwidth and size of the database.</span></span> <span data-ttu-id="3b611-121">如果您计划从内部 SQL Server 数据库备份大型数据库或文件组，建议您首先执行某些吞吐量测试。</span><span class="sxs-lookup"><span data-stu-id="3b611-121">If you plan to back up large databases or filegroups from an on-premise SQL Server database, it is recommended that you do some throughput testing first.</span></span> <span data-ttu-id="3b611-122">[Azure 存储 SLA](https://go.microsoft.com/fwlink/?LinkId=271619)具有可考虑的 blob 的最大处理时间。</span><span class="sxs-lookup"><span data-stu-id="3b611-122">[Azure storage SLA's](https://go.microsoft.com/fwlink/?LinkId=271619) have maximum processing times for blobs that you can take into consideration.</span></span>  
  
-   <span data-ttu-id="3b611-123">使用在**管理备份**部分中建议的 `WITH COMPRESSION` 选项，在备份大型文件时这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="3b611-123">Using the `WITH COMPRESSION` option as recommended in the **Managing Backup** section, it is very important when backing up large files.</span></span>  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a><span data-ttu-id="3b611-124">备份到 URL 或从 URL 还原故障排除</span><span class="sxs-lookup"><span data-stu-id="3b611-124">Troubleshooting Backup To or Restore from URL</span></span>  
 <span data-ttu-id="3b611-125">以下内容提供了在备份到 Azure Blob 存储服务或从中还原时出现问题的一些快速解决方法。</span><span class="sxs-lookup"><span data-stu-id="3b611-125">Following are some quick ways to troubleshoot errors when backing up to or restoring from the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="3b611-126">若要避免由于不支持的选项或限制导致的错误，请查看[SQL Server 备份和还原 Azure Blob 存储服务](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)一文中的限制列表，并提供对备份和还原命令的支持。</span><span class="sxs-lookup"><span data-stu-id="3b611-126">To avoid errors due to unsupported options or limitations, review the list of limitations, and support for BACKUP and RESTORE commands information in the [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) article.</span></span>  
  
 <span data-ttu-id="3b611-127">**身份验证错误：**</span><span class="sxs-lookup"><span data-stu-id="3b611-127">**Authentication Errors:**</span></span>  
  
-   <span data-ttu-id="3b611-128">WITH CREDENTIAL 是一个新选项，需要备份到 Azure Blob 存储服务或从中进行还原。</span><span class="sxs-lookup"><span data-stu-id="3b611-128">WITH CREDENTIAL is a new option and required to back up to or restore from the Azure Blob storage service.</span></span> <span data-ttu-id="3b611-129">与凭据有关的失败可能包括：</span><span class="sxs-lookup"><span data-stu-id="3b611-129">Failures related to credential could be the following:</span></span>  
  
     <span data-ttu-id="3b611-130">`BACKUP` 或 `RESTORE` 命令中指定的凭据不存在。</span><span class="sxs-lookup"><span data-stu-id="3b611-130">The credential specified in the `BACKUP` or `RESTORE` command does not exist.</span></span> <span data-ttu-id="3b611-131">要避免此问题，如果备份语句中没有指定凭据，可以使用 T-SQL 语句来创建凭据。</span><span class="sxs-lookup"><span data-stu-id="3b611-131">To avoid this issue, you can include T-SQL statements to create the credential if one does not exist in the backup statement.</span></span> <span data-ttu-id="3b611-132">以下是您可以使用的一个示例：</span><span class="sxs-lookup"><span data-stu-id="3b611-132">The following is an example you can use:</span></span>  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   <span data-ttu-id="3b611-133">凭据存在但是用于运行备份命令的登录帐户没有访问凭据的权限。</span><span class="sxs-lookup"><span data-stu-id="3b611-133">The credential exists but the login account that is used to run the backup command does not have permissions to access the credentials.</span></span> <span data-ttu-id="3b611-134">使用角色为 **db_backupoperator** 且拥有 **更改任意凭据** 权限的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="3b611-134">Use a login account in the **db_backupoperator** role with **Alter any credential** permissions.</span></span>  
  
-   <span data-ttu-id="3b611-135">验证存储帐户名称和密钥值。</span><span class="sxs-lookup"><span data-stu-id="3b611-135">Verify the storage account name and key values.</span></span> <span data-ttu-id="3b611-136">在凭据中存储的信息必须与你在备份和还原操作中使用的 Azure 存储帐户的属性值匹配。</span><span class="sxs-lookup"><span data-stu-id="3b611-136">The information stored in the credential must match the property values of the Azure storage account you are using in the backup and restore operations.</span></span>  
  
 <span data-ttu-id="3b611-137">**备份错误/失败：**</span><span class="sxs-lookup"><span data-stu-id="3b611-137">**Backup Errors/Failures:**</span></span>  
  
-   <span data-ttu-id="3b611-138">并行备份到同一 blob 导致一个备份失败，发生 **“初始化失败”** 错误。</span><span class="sxs-lookup"><span data-stu-id="3b611-138">Parallel backups to the same blob cause one of the backups to fail with an **Initialization failed** error.</span></span>  
  
-   <span data-ttu-id="3b611-139">使用以下错误日志帮助解决备份错误：</span><span class="sxs-lookup"><span data-stu-id="3b611-139">Use the following error logs to help with troubleshooting backup errors:</span></span>  
  
    -   <span data-ttu-id="3b611-140">设置跟踪标志 3051 以启用记录到具有以下格式的特定错误日志：</span><span class="sxs-lookup"><span data-stu-id="3b611-140">Set trace flag 3051 to turn on logging to a specific error log with the following format in:</span></span>  
  
         <span data-ttu-id="3b611-141">BackupToUrl- \<instname> - \<dbname> -action- \<PID> .log 其中 \<action> 是以下其中之一：</span><span class="sxs-lookup"><span data-stu-id="3b611-141">BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log Where \<action> is one of:</span></span>  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   <span data-ttu-id="3b611-142">你还可以通过查看 Windows 事件日志（名称为 "SQLBackupToUrl" 的应用程序日志下）来查找信息。</span><span class="sxs-lookup"><span data-stu-id="3b611-142">You can also find information by reviewing the Windows Event Log - Under Application logs with the name 'SQLBackupToUrl'.</span></span>  
  
-   <span data-ttu-id="3b611-143">从压缩备份中还原时，您可能看到以下错误：</span><span class="sxs-lookup"><span data-stu-id="3b611-143">When restoring from a compressed backup, you might see the following error:</span></span>  
  
    -   <span data-ttu-id="3b611-144">**出现 SqlException 3284。严重性：16状态：5**</span><span class="sxs-lookup"><span data-stu-id="3b611-144">**SqlException 3284 occurred. Severity: 16 State: 5**</span></span>  
        <span data-ttu-id="3b611-145">**设备 "" 上的消息标记 https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak 未对齐。使用用于创建 backupset 的相同块大小重新发出 Restore 语句： ' 65536 ' 看起来像一个可能值。**</span><span class="sxs-lookup"><span data-stu-id="3b611-145">**Message Filemark on device 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' is not aligned. Reissue the Restore statement with the same block size used to create the backupset: '65536' looks like a possible value.**</span></span>  
  
         <span data-ttu-id="3b611-146">要修复此错误，请重新发布指定了 `BACKUP` 的 `BLOCKSIZE = 65536` 语句。</span><span class="sxs-lookup"><span data-stu-id="3b611-146">To solve this error, reissue the `BACKUP` statement with `BLOCKSIZE = 65536` specified.</span></span>  
  
-   <span data-ttu-id="3b611-147">由于 blob 具有活动租约，备份期间出错：失败的备份活动可能导致 blob 产生活动租约。</span><span class="sxs-lookup"><span data-stu-id="3b611-147">Error during backup due to blobs that have active lease on them: Failed backup activity can result in blobs with active leases.</span></span>  
  
     <span data-ttu-id="3b611-148">如果重新尝试执行备份语句，备份操作可能失败，出现类似于以下的错误：</span><span class="sxs-lookup"><span data-stu-id="3b611-148">If a backup statement is reattempted, backup operation might fail with an error similar to the following:</span></span>  
  
     <span data-ttu-id="3b611-149">**“备份到 URL”收到来自远程端点的异常。异常消息：远程服务器返回错误：(412) 当前 blob 上有租约，但请求中没有指定租约 ID**。</span><span class="sxs-lookup"><span data-stu-id="3b611-149">**Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (412) There is currently a lease on the blob and no lease ID was specified in the request**.</span></span>  
  
     <span data-ttu-id="3b611-150">如果尝试对具有活动租约的备份 blob 文件执行还原语句，则还原操作失败，出现类似于以下的错误：</span><span class="sxs-lookup"><span data-stu-id="3b611-150">If a restore statement is attempted on a backup blob file that has an active lease, the restore operation fails with an error similar to the following:</span></span>  
  
     <span data-ttu-id="3b611-151">**异常消息：远程服务器返回了错误：(409)。有冲突。**</span><span class="sxs-lookup"><span data-stu-id="3b611-151">**Exception Message: The remote server returned an error: (409) Conflict..**</span></span>  
  
     <span data-ttu-id="3b611-152">发生这种错误时，需要删除 blob 文件。</span><span class="sxs-lookup"><span data-stu-id="3b611-152">When such error occurs, the blob files need to be deleted.</span></span> <span data-ttu-id="3b611-153">有关此情形和如何解决此问题的详细信息，请参阅 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span><span class="sxs-lookup"><span data-stu-id="3b611-153">For more information on this scenario and how to correct this problem, see [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)</span></span>  
  
## <a name="proxy-errors"></a><span data-ttu-id="3b611-154">代理错误</span><span class="sxs-lookup"><span data-stu-id="3b611-154">Proxy Errors</span></span>  
 <span data-ttu-id="3b611-155">如果您使用代理服务器访问 Internet，可能会发现以下问题：</span><span class="sxs-lookup"><span data-stu-id="3b611-155">If you are using Proxy Servers to access the internet, you may see the following issues:</span></span>  
  
 <span data-ttu-id="3b611-156">**代理服务器限制连接：**</span><span class="sxs-lookup"><span data-stu-id="3b611-156">**Connection throttling by Proxy Servers:**</span></span>  
  
 <span data-ttu-id="3b611-157">代理服务器可能具有限制每分钟连接次数的设置。</span><span class="sxs-lookup"><span data-stu-id="3b611-157">Proxy Servers can have settings that limit the number of connections per minute.</span></span> <span data-ttu-id="3b611-158">“备份到 URL”进程是一个多线程进程，因此可能超过此限制。</span><span class="sxs-lookup"><span data-stu-id="3b611-158">The Backup to URL process is a multi-threaded process and hence can go over this limit.</span></span> <span data-ttu-id="3b611-159">如果出现此情况，代理服务器将终止连接。</span><span class="sxs-lookup"><span data-stu-id="3b611-159">If this happens, the proxy server kills the connection.</span></span> <span data-ttu-id="3b611-160">若要解决此问题，请更改代理设置，使 SQL Server 不使用该代理。</span><span class="sxs-lookup"><span data-stu-id="3b611-160">To resolve this issue, change the proxy settings so SQL Server is not using the proxy.</span></span>   <span data-ttu-id="3b611-161">下面是一些您可能在错误日志中看到的类型或错误消息的示例：</span><span class="sxs-lookup"><span data-stu-id="3b611-161">Following are some examples of the types or error messages you may see in the error log:</span></span>  
  
-   <span data-ttu-id="3b611-162">在 "" 上写入 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak 失败： "备份到 URL" 收到来自远程终结点的异常。</span><span class="sxs-lookup"><span data-stu-id="3b611-162">Write on "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" failed: Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="3b611-163">异常消息: 无法从传输连接中读取数据: 连接已关闭。</span><span class="sxs-lookup"><span data-stu-id="3b611-163">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
-   <span data-ttu-id="3b611-164">文件“http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:”上发生不可恢复的 I/O 错误。无法从远程终结点收集错误。</span><span class="sxs-lookup"><span data-stu-id="3b611-164">A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Error could not be gathered from Remote Endpoint.</span></span>  
  
     <span data-ttu-id="3b611-165">消息 3013，级别 16，状态 1，第 2 行</span><span class="sxs-lookup"><span data-stu-id="3b611-165">Msg 3013, Level 16, State 1, Line 2</span></span>  
  
     <span data-ttu-id="3b611-166">备份数据库异常终止。</span><span class="sxs-lookup"><span data-stu-id="3b611-166">BACKUP DATABASE is terminating abnormally.</span></span>  
  
-   <span data-ttu-id="3b611-167">BackupIoRequest：： ReportIoError：备份设备 "" 上的写入失败 http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak 。</span><span class="sxs-lookup"><span data-stu-id="3b611-167">BackupIoRequest::ReportIoError: write failure on backup device 'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak'.</span></span> <span data-ttu-id="3b611-168">操作系统错误，“备份到 URL”收到来自远程端点的异常。</span><span class="sxs-lookup"><span data-stu-id="3b611-168">Operating system error Backup to URL received an exception from the remote endpoint.</span></span> <span data-ttu-id="3b611-169">异常消息: 无法从传输连接中读取数据: 连接已关闭。</span><span class="sxs-lookup"><span data-stu-id="3b611-169">Exception Message: Unable to read data from the transport connection: The connection was closed.</span></span>  
  
 <span data-ttu-id="3b611-170">如果使用跟踪标志 3051 打开详细日志记录，您还可能在日志中看到以下消息：</span><span class="sxs-lookup"><span data-stu-id="3b611-170">If you turn on the verbose logging using the trace flag 3051 you may also see the following message in the logs:</span></span>  
  
 <span data-ttu-id="3b611-171">HTTP 状态代码 502，HTTP 状态消息代理错误 (每分钟的 HTTP 请求数超出配置限制。</span><span class="sxs-lookup"><span data-stu-id="3b611-171">HTTP status code 502, HTTP Status Message Proxy Error ( The number of HTTP requests per minute exceeded the configured limit.</span></span> <span data-ttu-id="3b611-172">请与 ISA Server 管理员联系。</span><span class="sxs-lookup"><span data-stu-id="3b611-172">Contact your ISA Server administrator.</span></span>  <span data-ttu-id="3b611-173">)</span><span class="sxs-lookup"><span data-stu-id="3b611-173">)</span></span>  
  
 <span data-ttu-id="3b611-174">**未选择默认代理设置：**</span><span class="sxs-lookup"><span data-stu-id="3b611-174">**Default Proxy Settings not picked up:**</span></span>  
  
 <span data-ttu-id="3b611-175">有时不会选取默认设置，导致出现如下代理身份验证错误：在\*文件 "" 上发生不可恢复的 i/o 错误： " http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak: 备份到 URL" 收到来自远程终结点的异常。异常消息：远程服务器返回错误： (407) \* **需要代理身份验证**。</span><span class="sxs-lookup"><span data-stu-id="3b611-175">Sometimes the default settings are not picked up causing proxy authentication errors such as the one shown below:*A nonrecoverable I/O error occurred on file "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (407)* **Proxy Authentication Required**.</span></span>  
  
 <span data-ttu-id="3b611-176">若要解决此问题，请使用以下步骤创建一个配置文件，以允许“备份到 URL”进程使用默认代理设置：</span><span class="sxs-lookup"><span data-stu-id="3b611-176">To resolve this issue, create a configuration file that allows the Backup to URL process to use the default proxy settings using the following steps:</span></span>  
  
1.  <span data-ttu-id="3b611-177">使用以下 xml 创建一个名为 BackuptoURL.exe.config 的配置文件：</span><span class="sxs-lookup"><span data-stu-id="3b611-177">Create a configuration file named BackuptoURL.exe.config  with the following xml:</span></span>  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  <span data-ttu-id="3b611-178">将该配置文件置于 SQL Server 实例的 Binn 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3b611-178">Place the configuration file in the Binn folder of the SQL Server Instance.</span></span> <span data-ttu-id="3b611-179">例如，如果我的 SQL Server 安装在计算机的 C 驱动器上，请将配置文件放在此处： *C:\Program FILES\MICROSOFT SQL Server\MSSQL12. \<InstanceName>\MSSQL\Binn*。</span><span class="sxs-lookup"><span data-stu-id="3b611-179">For example, if my SQL Server is installed on the C drive of the machine, place the configuration file here: *C:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Binn*.</span></span>  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a><span data-ttu-id="3b611-180">排除针对 Azure 的 SQL Server 托管备份的故障</span><span class="sxs-lookup"><span data-stu-id="3b611-180">Troubleshooting SQL Server Managed Backup to Azure</span></span>  
 <span data-ttu-id="3b611-181">由于 SQL Server 托管备份构建在“备份到 URL”上，因此上面各节中介绍的故障排除提示适用于使用 SQL Server 托管备份的数据库或实例。</span><span class="sxs-lookup"><span data-stu-id="3b611-181">Since SQL Server Managed Backup is built on top of Backup to URL, the troubleshooting tips described in the earlier sections apply to databases or instances using SQL Server Managed Backup.</span></span>  <span data-ttu-id="3b611-182">有关解决 SQL Server 将托管备份到 Azure 的问题的详细信息，请参阅[SQL Server 托管备份到 azure 的故障排除](sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="3b611-182">Information about troubleshooting SQL Server Managed Backup to Azure is described in detail in [Troubleshooting SQL Server Managed  Backup to Azure](sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b611-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b611-183">See Also</span></span>  
 [<span data-ttu-id="3b611-184">从 Azure 中存储的备份还原</span><span class="sxs-lookup"><span data-stu-id="3b611-184">Restoring From Backups Stored in Azure</span></span>](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
