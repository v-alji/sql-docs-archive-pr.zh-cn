---
title: 为可用性组设置 SQL Server 托管备份到 Azure |Microsoft Docs
description: 本教程演示如何为参与 Always On 可用性组的数据库配置 SQL Server 托管 Microsoft Azure 备份。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 0c4553cd-d8e4-4691-963a-4e414cc0f1ba
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebae9f75ac25698582b7f3e4c78c2fb773bd803e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576960"
---
# <a name="setting-up-sql-server-managed-backup-to-azure-for-availability-groups"></a><span data-ttu-id="3e9da-103">为可用性组设置针对 Azure 的 SQL Server 托管备份</span><span class="sxs-lookup"><span data-stu-id="3e9da-103">Setting up SQL Server Managed Backup to Azure for Availability Groups</span></span>
  <span data-ttu-id="3e9da-104">本主题是有关为参与 AlwaysOn 可用性组的数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的教程。</span><span class="sxs-lookup"><span data-stu-id="3e9da-104">This topic is a tutorial on configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases participating in AlwaysOn Availability Groups.</span></span>  
  
## <a name="availability-group-configurations"></a><span data-ttu-id="3e9da-105">可用性组配置</span><span class="sxs-lookup"><span data-stu-id="3e9da-105">Availability Group Configurations</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="3e9da-106">对于可用性组数据库，无论副本是在本地配置还是完全在 Azure 上配置，还是在本地与一个或多个 Azure 虚拟机之间进行混合实现，都支持。</span><span class="sxs-lookup"><span data-stu-id="3e9da-106">is supported for Availability Group databases, whether the replicas are all configured on-premises, or entirely on Azure, or a Hybrid implementation between on-premises and on one or more Azure virtual machines.</span></span> <span data-ttu-id="3e9da-107">不过，对于一个或多个实现，可能需要考虑以下方面：</span><span class="sxs-lookup"><span data-stu-id="3e9da-107">However you might need to consider the following for one or more implementations:</span></span>  
  
-   <span data-ttu-id="3e9da-108">日志备份频率：日志备份频率是时间和日志增长。</span><span class="sxs-lookup"><span data-stu-id="3e9da-108">Log Backup Frequency: The frequency of log backup is both time and log growth.</span></span> <span data-ttu-id="3e9da-109">例如，日志每两小时备份一次，除非两小时内使用的日志空间为 5 MB 或更多。</span><span class="sxs-lookup"><span data-stu-id="3e9da-109">For example, the log backup is taken once every 2 hours unless the log space used within the two hour period is 5 MB or more.</span></span> <span data-ttu-id="3e9da-110">这适用于所有实现，包括本地、云或混合实现。</span><span class="sxs-lookup"><span data-stu-id="3e9da-110">This applies to all implementations, on-premises, cloud, or a Hybrid.</span></span>  
  
-   <span data-ttu-id="3e9da-111">网络带宽：这适用于副本位于不同物理位置的实现，例如在混合云中，或在仅限云的配置中跨不同的 Azure 区域。</span><span class="sxs-lookup"><span data-stu-id="3e9da-111">Network Bandwidth: This applies to implementations where the replicas are located in different physical locations, like in a hybrid cloud, or across different Azure regions in a cloud only configuration.</span></span> <span data-ttu-id="3e9da-112">如果副本设置为同步复制，网络带宽会影响副本的滞后时间，这又可能导致主副本的日志增长。</span><span class="sxs-lookup"><span data-stu-id="3e9da-112">The network bandwidth can affect the latency of the secondaries and if the secondaries are set to synchronous replication, then this can cause log growth on the primary.</span></span> <span data-ttu-id="3e9da-113">如果副本设置为同步复制，由于网络滞后时间，副本可能无法保持同步，这在故障转移到辅助副本时可能导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="3e9da-113">If the secondaries are set to synchronous replication, the secondaries may not be able to keep up due to network latency, which can result in data loss in the event of a failover to the secondary replica.</span></span>  
  
### <a name="configuring-ss_smartbackup-for-availability-databases"></a><span data-ttu-id="3e9da-114">为可用性数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e9da-114">Configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Availability Databases.</span></span>  
 <span data-ttu-id="3e9da-115">**权限：**</span><span class="sxs-lookup"><span data-stu-id="3e9da-115">**Permissions:**</span></span>  
  
-   <span data-ttu-id="3e9da-116">要求具有**db_backupoperator**数据库角色的成员身份、具有**ALTER ANY CREDENTIAL**权限以及 `EXECUTE` 对**sp_delete_backuphistory**存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="3e9da-116">Requires membership in **db_backupoperator** database role, with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on **sp_delete_backuphistory**stored procedure.</span></span>  
  
-   <span data-ttu-id="3e9da-117">需要对**smart_admin fn_get_current_xevent_settings**函数的**SELECT**权限。</span><span class="sxs-lookup"><span data-stu-id="3e9da-117">Requires **SELECT** permissions on the **smart_admin.fn_get_current_xevent_settings**function.</span></span>  
  
-   <span data-ttu-id="3e9da-118">需要 `EXECUTE` 对 smart_admin 的权限**sp_get_backup_diagnostics**存储过程。</span><span class="sxs-lookup"><span data-stu-id="3e9da-118">Requires `EXECUTE` permissions on the **smart_admin.sp_get_backup_diagnostics** stored procedure.</span></span> <span data-ttu-id="3e9da-119">此外，它还需要 `VIEW SERVER STATE` 权限，因为它在内部调用其他需要此权限的系统对象。</span><span class="sxs-lookup"><span data-stu-id="3e9da-119">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
-   <span data-ttu-id="3e9da-120">需要 `EXECUTE` 对 `smart_admin.sp_set_instance_backup` 和 `smart_admin.sp_backup_master_switch` 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="3e9da-120">Requires `EXECUTE` permissions on the `smart_admin.sp_set_instance_backup` and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  
  
 <span data-ttu-id="3e9da-121">下面是为 AlwaysOn 可用性组设置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="3e9da-121">The following are the basic steps to setting up an AlwaysOn Availability Group with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="3e9da-122">本主题后面将介绍详细的分步教程。</span><span class="sxs-lookup"><span data-stu-id="3e9da-122">A detailed step-by step tutorial is described later in this topic.</span></span>  
  
1.  <span data-ttu-id="3e9da-123">创建可用性组后，配置首选备份副本。</span><span class="sxs-lookup"><span data-stu-id="3e9da-123">Once you have created Availability Group, configure the preferred backup replica.</span></span> <span data-ttu-id="3e9da-124"> 也会使用可用性组的这个设置来确定将哪个副本用于备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-124">This setting for the Availability Group is also used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine which replica to use for backup.</span></span> <span data-ttu-id="3e9da-125">有关如何设置备份首选项的分步说明，请参阅[在可用性副本上配置备份 &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-125">For step by step instructions about how to set up the backup preference, see [Configure Backup on Availability Replicas &#40;SQL Server&#41;](availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).</span></span>  <span data-ttu-id="3e9da-126">如果要创建新的 AlwaysOn 可用性组，请参阅[使用 AlwaysOn 可用性组的入门 &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-126">If you are creating a new AlwaysOn Availability Group, see [Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/getting-started-with-always-on-availability-groups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="3e9da-127">配置对辅助副本的只读连接访问。</span><span class="sxs-lookup"><span data-stu-id="3e9da-127">Configure read only connection access to the secondary replicas.</span></span> <span data-ttu-id="3e9da-128">有关如何配置只读访问的分步说明，请参阅[在可用性副本上配置只读访问 &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="3e9da-128">For step by step instructions about how to configure read only access, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)</span></span>  
  
3.  <span data-ttu-id="3e9da-129">指定备份副本。</span><span class="sxs-lookup"><span data-stu-id="3e9da-129">Specify Backup replica.</span></span> <span data-ttu-id="3e9da-130">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 使用首选备份副本设置决定使用哪个数据库安排从它进行备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-130">The preferred backup replica setting is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine which database to use for scheduling backups from..</span></span>  <span data-ttu-id="3e9da-131">若要确定当前副本是否为首选备份副本，请使用[sys. fn_hadr_backup_is_preferred_replica &#40;transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)函数。</span><span class="sxs-lookup"><span data-stu-id="3e9da-131">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function.</span></span>  
  
4.  <span data-ttu-id="3e9da-132">在每个副本上， [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 使用**智能 sp_set_db_backup**存储过程的数据库的运行配置。</span><span class="sxs-lookup"><span data-stu-id="3e9da-132">On each replica run [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration for the database using the **smart-admin.sp_set_db_backup** stored procedure.</span></span>  
  
     <span data-ttu-id="3e9da-133">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 故障转移后的行为：\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 将继续工作，并在发生故障转移事件后维护备份副本和可恢复性。</span><span class="sxs-lookup"><span data-stu-id="3e9da-133">**[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] behavior after a failover:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will continue to work and maintain backup copies and recoverability after a failover event.</span></span> <span data-ttu-id="3e9da-134">故障转移后不需要执行任何特定操作。</span><span class="sxs-lookup"><span data-stu-id="3e9da-134">No specific action is required after a failover.</span></span>  
  
#### <a name="considerations-and-requirements"></a><span data-ttu-id="3e9da-135">注意事项和要求：</span><span class="sxs-lookup"><span data-stu-id="3e9da-135">Considerations and Requirements:</span></span>  
 <span data-ttu-id="3e9da-136">为参与 AlwaysOn 可用性组的数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 需要考虑特定的事项并且有特定的要求。</span><span class="sxs-lookup"><span data-stu-id="3e9da-136">Configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases participating in AlwaysOn Availability Group requires specific considerations and requirements.</span></span> <span data-ttu-id="3e9da-137">下面列出了注意事项和要求：</span><span class="sxs-lookup"><span data-stu-id="3e9da-137">Following is a list of considerations and requirements:</span></span>  
  
-   <span data-ttu-id="3e9da-138">对于参与同一可用性组的所有 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 节点上的所有数据库，各项 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置设置都应该相同。</span><span class="sxs-lookup"><span data-stu-id="3e9da-138">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings should be the same for all the databases on all the nodes of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] participating in the same Availability Group.</span></span> <span data-ttu-id="3e9da-139">要想实现此目标，您可以在数据库级别为主要副本和所有其他副本设置相同的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 配置，也可以在参与可用性组的所有节点上设置相同的默认 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 设置。</span><span class="sxs-lookup"><span data-stu-id="3e9da-139">You can achieve this either by setting  the same [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for the primary and all the replicas at the database level, or by setting the same default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings on all the nodes participating in the Availability Groups.</span></span> <span data-ttu-id="3e9da-140">我们建议在数据库级别设置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，因为在数据库级别配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 可将设置与数据库隔离，因此更改默认设置只会影响实例上的所有其他数据库。</span><span class="sxs-lookup"><span data-stu-id="3e9da-140">We recommend setting [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database because configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level lets you isolate the settings to the databases and changes to default settings affect all other databases on the instance.</span></span>  
  
-   <span data-ttu-id="3e9da-141">指定备份副本。</span><span class="sxs-lookup"><span data-stu-id="3e9da-141">Specify Backup replica.</span></span> <span data-ttu-id="3e9da-142"> 使用首选备份副本设置安排备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-142">The preferred backup replica setting is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to schedule the backups.</span></span> <span data-ttu-id="3e9da-143">若要确定当前副本是否为首选备份副本，请使用[sys. fn_hadr_backup_is_preferred_replica &#40;transact-sql&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)函数。</span><span class="sxs-lookup"><span data-stu-id="3e9da-143">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function.</span></span>  
  
-   <span data-ttu-id="3e9da-144">如果将辅助副本配置为首选副本，则至少应为它配置只读连接访问权限。</span><span class="sxs-lookup"><span data-stu-id="3e9da-144">If the secondary replica is configured as the preferred replica, it should be configured to have at least read only connection access.</span></span> <span data-ttu-id="3e9da-145">不支持对辅助数据库没有连接访问权限的可用性组。</span><span class="sxs-lookup"><span data-stu-id="3e9da-145">Availability groups that have no connection access to secondary databases are not supported.</span></span>  <span data-ttu-id="3e9da-146">有关详细信息，请参阅 [配置对可用性副本的只读访问 (SQL Server)](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-146">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="3e9da-147">如果您在配置完可用性组后配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 会尝试复制任何现有备份，并将它们复制到存储容器中。</span><span class="sxs-lookup"><span data-stu-id="3e9da-147">If you are configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] after you configure the Availability Group, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will attempt to copy any existing backups based and copy them over to the storage container.</span></span>  <span data-ttu-id="3e9da-148">如果 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 找不到或不能访问现有备份，它将安排一次完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-148">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to find or access existing backups, it will schedule a full database backup.</span></span> <span data-ttu-id="3e9da-149">这是为了优化可用性组数据库的备份操作而专门进行的。</span><span class="sxs-lookup"><span data-stu-id="3e9da-149">This is done specifically to optimize the backup operations for Availability Group databases.</span></span>  
  
-   <span data-ttu-id="3e9da-150">如果正在创建新的可用性数据库，并且不打算将实例级别设置应用于数据库，则可能需要考虑禁用实例级别设置。</span><span class="sxs-lookup"><span data-stu-id="3e9da-150">You may want to consider disabling the instance level settings if you are creating a new availability database, and you don't intend to apply the instance level settings to the database</span></span>  
  
-   <span data-ttu-id="3e9da-151">当使用加密时，对所有副本使用相同的证书。</span><span class="sxs-lookup"><span data-stu-id="3e9da-151">When using encryption, use the same certificate on all the replicas.</span></span> <span data-ttu-id="3e9da-152">这有助于在故障转移或还原到不同副本时保持连续不间断的备份操作。</span><span class="sxs-lookup"><span data-stu-id="3e9da-152">This facilitates continued and uninterrupted backup operations in the event of a failover or restores to a different replica.</span></span>  
  
#### <a name="enable-and-configure-ss_smartbackup-for-an-availability-database"></a><span data-ttu-id="3e9da-153">为可用性数据库启用和配置 </span><span class="sxs-lookup"><span data-stu-id="3e9da-153">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for an Availability Database</span></span>  
 <span data-ttu-id="3e9da-154">本教程首先介绍为计算机 Node1 和 Node2 上的数据库 (AGTestDB) 启用和配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的步骤，然后介绍允许监视 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 运行状况的步骤。</span><span class="sxs-lookup"><span data-stu-id="3e9da-154">This tutorial describes the steps to enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database (AGTestDB) on computers Node1 and Node2, followed by steps to enable monitoring the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] health status.</span></span>  
  
1.  <span data-ttu-id="3e9da-155">**创建 Azure 存储帐户：** 备份存储在 Azure Blob 存储服务中。</span><span class="sxs-lookup"><span data-stu-id="3e9da-155">**Create an Azure storage account:** The backups are stored in the Azure Blob storage service.</span></span> <span data-ttu-id="3e9da-156">如果还没有 Azure 存储帐户，则必须先创建一个。</span><span class="sxs-lookup"><span data-stu-id="3e9da-156">You must first create an Azure storage account, if you do not already have one.</span></span> <span data-ttu-id="3e9da-157">有关详细信息，请参阅[创建 Azure 存储帐户](https://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-157">For more information, see [Creating an Azure Storage Account](https://www.windowsazure.com/manage/services/storage/how-to-create-a-storage-account/).</span></span> <span data-ttu-id="3e9da-158">记录下存储帐户的名称、访问密钥和存储帐户的 URL。</span><span class="sxs-lookup"><span data-stu-id="3e9da-158">Make a note of the storage account name, access keys, and URL of the storage account.</span></span> <span data-ttu-id="3e9da-159">存储帐户名称和访问密钥用于创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="3e9da-159">The storage account name and access key information is used to create a SQL Credential.</span></span> <span data-ttu-id="3e9da-160"> 在备份操作期间使用 SQL 凭据对存储帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="3e9da-160">The SQL Credential is used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] during backup operations to authenticate to the storage account.</span></span>  
  
2.  <span data-ttu-id="3e9da-161">**创建 SQL 凭据：** 使用存储帐户的名称作为标识，并使用存储访问密钥作为密码创建 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="3e9da-161">**Create a SQL Credential:** Create a SQL Credential using the name of the storage account as the Identity and the storage access key as the password.</span></span>  
  
3.  <span data-ttu-id="3e9da-162">**确保 SQL Server 代理服务已启动且正在运行：** 如果 SQL Server 代理当前未运行，请启动它。</span><span class="sxs-lookup"><span data-stu-id="3e9da-162">**Ensure SQL Server Agent service is Started and Running:** Start SQL Server Agent if it is not currently running.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="3e9da-163">需要实例上运行有 SQL Server 代理才能执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="3e9da-163">requires SQL Server Agent to be running on the instance to perform backup operations.</span></span>  <span data-ttu-id="3e9da-164">可能要将 SQL 代理设置为自动运行以确保可正常进行备份操作。</span><span class="sxs-lookup"><span data-stu-id="3e9da-164">You may want to set SQL Agent to run automatically to make sure that backup operations can occur regularly.</span></span>  
  
4.  <span data-ttu-id="3e9da-165">**确定保持期：** 确定备份文件的保持期。</span><span class="sxs-lookup"><span data-stu-id="3e9da-165">**Determine the retention period:** Determine the retention period that you want for the backup files.</span></span> <span data-ttu-id="3e9da-166">以天为单位指定保持期，范围可为 1 到 30。</span><span class="sxs-lookup"><span data-stu-id="3e9da-166">The retention period is specified in days and can range from 1 to 30.</span></span> <span data-ttu-id="3e9da-167">保持期决定了可恢复数据库的时段。</span><span class="sxs-lookup"><span data-stu-id="3e9da-167">The retention period determines the recoverability time frame for the database.</span></span>  
  
5.  <span data-ttu-id="3e9da-168">**创建在备份期间用于加密的证书或非对称密钥：** 在第一个节点节点1上创建证书，然后使用备份证书将其导出到文件[&#40;transact-sql&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-168">**Create a Certificate or Asymmetric key to use for encryption during back up:** Create the certificate on the first node Node1, and then export it to a file using [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)..</span></span> <span data-ttu-id="3e9da-169">在 Node 2 上，使用从 Node 1 导出的文件创建证书。</span><span class="sxs-lookup"><span data-stu-id="3e9da-169">On Node 2, create a certificate using the file exported from Node 1 .</span></span> <span data-ttu-id="3e9da-170">有关从文件创建证书的详细信息，请参阅[CREATE certificate &#40;transact-sql&#41;](/sql/t-sql/statements/create-certificate-transact-sql)中的示例。</span><span class="sxs-lookup"><span data-stu-id="3e9da-170">For more information on creating a certificate from a file, see the example in [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
6.  <span data-ttu-id="3e9da-171">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 在节点1上启用和配置 AGTestDB：\*\* Start SQL Server Management Studio，并连接到在其中安装了可用性数据库的节点1上的实例。</span><span class="sxs-lookup"><span data-stu-id="3e9da-171">**Enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for AGTestDB on Node1:** Start SQL Server Management Studio  and connect to the instance on Node1 where the availability database  is installed.</span></span> <span data-ttu-id="3e9da-172">在根据要求修改数据库名称、存储 URL、SQL 凭据和保持期的值后，从查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="3e9da-172">From the query window run the following statement after you modify the values for the database name, storage URL, SQL Credential and retention period per your requirements:</span></span>  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     <span data-ttu-id="3e9da-173">有关创建用于加密的证书的详细信息，请参阅[创建加密的备份](../relational-databases/backup-restore/create-an-encrypted-backup.md)中的**创建备份证书**步骤。</span><span class="sxs-lookup"><span data-stu-id="3e9da-173">For more information on creating a certificate for encryption, see the **Create a Backup Certificate** step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
7.  <span data-ttu-id="3e9da-174">\*\* [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 为节点2上的 AGTestDB 启用和配置：\*\* Start SQL Server Management Studio 并连接到安装了可用性数据库的节点2上的实例。</span><span class="sxs-lookup"><span data-stu-id="3e9da-174">**Enable and configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for AGTestDB on Node2:** Start SQL Server Management Studio and connect to the instance on Node2 where the availability database  is installed.</span></span> <span data-ttu-id="3e9da-175">在根据要求修改数据库名称、存储 URL、SQL 凭据和保持期的值后，从查询窗口中运行以下语句：</span><span class="sxs-lookup"><span data-stu-id="3e9da-175">From the query window run the following statement after you modify the values for the database name, storage URL, SQL Credential and retention period per your requirements:</span></span>  
  
    ```sql  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='AGTestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
    ```  
  
     [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="3e9da-176">。</span><span class="sxs-lookup"><span data-stu-id="3e9da-176">is now enabled on the database you specified.</span></span> <span data-ttu-id="3e9da-177">数据库上的备份操作最多可能需要 15 分钟才能运行。</span><span class="sxs-lookup"><span data-stu-id="3e9da-177">It may take up to 15 minutes for the backup operations on the database to start to run.</span></span> <span data-ttu-id="3e9da-178">备份将在首选备份副本上进行。</span><span class="sxs-lookup"><span data-stu-id="3e9da-178">The backup will occur on the preferred backup replica.</span></span>  
  
8.  <span data-ttu-id="3e9da-179">**查看扩展事件默认配置：** 通过在用于安排从其进行备份的副本上运行以下 transact-sql 语句，检查扩展事件配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3e9da-179">**Review Extended Event Default Configuration:**  Review the Extended Event configuration by running the following transact-SQL statement on the replica that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is using to schedule the backups from.</span></span> <span data-ttu-id="3e9da-180">这通常是数据库所属可用性组的首选备份副本设置。</span><span class="sxs-lookup"><span data-stu-id="3e9da-180">This is usually the preferred backup replica setting for the Availability Group that the database belongs to.</span></span>  
  
    ```sql  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings(); 
    ```  
  
     <span data-ttu-id="3e9da-181">应看到默认情况下启用管理、操作和分析通道事件，且无法禁用这些事件。</span><span class="sxs-lookup"><span data-stu-id="3e9da-181">You should see that Admin, Operational  and Analytical channel events are enabled by default and cannot be disabled.</span></span> <span data-ttu-id="3e9da-182">这对于需要手动干预的事件来说应当已经足够。</span><span class="sxs-lookup"><span data-stu-id="3e9da-182">This should be sufficient to monitor the events that require manual intervention.</span></span>  <span data-ttu-id="3e9da-183">您可以启用调试事件，但是这些通道包含 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 用来检测问题和解决问题的信息性事件和调试事件。</span><span class="sxs-lookup"><span data-stu-id="3e9da-183">You can enable the debug events, but these channels include informational and debug events that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] uses to detect issues and solve them.</span></span> <span data-ttu-id="3e9da-184">有关详细信息，请参阅[监视 SQL Server 托管备份到 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-184">For more information, see [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
9. <span data-ttu-id="3e9da-185">**启用和配置运行状况通知：** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 有一个存储过程，它创建代理作业以发出可能需要注意的错误或警告的电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="3e9da-185">**Enable and Configure Notification for Health Status:** [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has a stored procedure that creates an agent job to send out e-mail notifications of errors or warnings that may require attention.</span></span>  <span data-ttu-id="3e9da-186">若要接收此类通知，必须允许运行这个创建 SQL Server 代理作业的存储过程。</span><span class="sxs-lookup"><span data-stu-id="3e9da-186">To receive such notifications, you must enable run the stored procedure which creates a SQL Server Agent Job.</span></span> <span data-ttu-id="3e9da-187">以下步骤说明了启用和配置电子邮件通知的过程：</span><span class="sxs-lookup"><span data-stu-id="3e9da-187">The following steps describe the process to enable and configure e-mail notifications:</span></span>  
  
    1.  <span data-ttu-id="3e9da-188">如果尚未在此实例上启用数据库邮件，请进行设置。</span><span class="sxs-lookup"><span data-stu-id="3e9da-188">Setup Database Mail if it is not already enabled on the instance.</span></span> <span data-ttu-id="3e9da-189">有关详细信息，请参阅 [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-189">For more information, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
    2.  <span data-ttu-id="3e9da-190">将 SQL Server 代理通知配置为使用数据库邮件。</span><span class="sxs-lookup"><span data-stu-id="3e9da-190">Configure SQL Server Agent Notification to use Database Mail.</span></span> <span data-ttu-id="3e9da-191">有关详细信息，请参阅 [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-191">For more information, see [Configure SQL Server Agent Mail to Use Database Mail](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).</span></span>  
  
    3.  <span data-ttu-id="3e9da-192">**启用电子邮件通知以接收备份错误和警告：** 在查询窗口中，运行以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="3e9da-192">**Enable e-mail notifications to receive backup errors and warnings:** From the query window, run the following Transact-SQL statements:</span></span>  
  
        ```sql  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email>'  
        ```  
  
         <span data-ttu-id="3e9da-193">有关详细信息和完整的示例脚本，请参阅[监视 SQL Server 托管备份到 Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-193">For more information and a full sample script see [Monitor SQL Server Managed Backup to Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md).</span></span>  
  
10. <span data-ttu-id="3e9da-194">**在 Azure 存储帐户中查看备份文件：** 从 SQL Server Management Studio 或 Azure 管理门户连接到存储帐户。</span><span class="sxs-lookup"><span data-stu-id="3e9da-194">**View backup files in the Azure Storage Account:** Connect to the storage account from SQL Server Management Studio or the Azure Management Portal.</span></span> <span data-ttu-id="3e9da-195">您将看到一个 SQL Server 实例的容器，其中承载您配置为使用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的数据库。</span><span class="sxs-lookup"><span data-stu-id="3e9da-195">You will see a container for the instance of SQL Server that hosts the database you configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="3e9da-196">您也会在为数据库启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的 15 分钟内，看到数据库和日志备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-196">You may also see a database and a log backup within 15 minutes of enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database.</span></span>  
  
11. <span data-ttu-id="3e9da-197">**监视运行状态：** 可以通过以前配置的电子邮件通知进行监视，也可以主动监控记录的事件。</span><span class="sxs-lookup"><span data-stu-id="3e9da-197">**Monitor the Health Status:**  You can monitor through e-mail notifications you configured previously, or actively monitor the events logged.</span></span> <span data-ttu-id="3e9da-198">以下是一些用于查看事件的示例 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="3e9da-198">The following are some example Transact-SQL Statements used to view the events:</span></span>  
  
    ```sql  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event varchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
    ```  
  
    ```sql  
    -- to enable debug events  
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
    ```sql  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
    ```  
  
 <span data-ttu-id="3e9da-199">本节中描述的步骤是专门用于在数据库上首次配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3e9da-199">The steps described in this section are specifically for configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time on the database.</span></span> <span data-ttu-id="3e9da-200">您可以使用相同的系统存储过程**smart_admin sp_set_db_backup**来修改现有配置，并提供新值。</span><span class="sxs-lookup"><span data-stu-id="3e9da-200">You can modify the existing configurations using the same system stored procedure **smart_admin.sp_set_db_backup** and provide the new values.</span></span> <span data-ttu-id="3e9da-201">有关详细信息，请参阅[SQL Server 托管备份到 Azure-保持和存储设置](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="3e9da-201">For more information, see [SQL Server Managed Backup to Azure - Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
### <a name="considerations-when-removing-a-database-from-alwayson-availability-group-configuration"></a><span data-ttu-id="3e9da-202">从 AlwaysOn 可用性组删除数据库时的注意事项</span><span class="sxs-lookup"><span data-stu-id="3e9da-202">Considerations when Removing a Database from AlwaysOn Availability Group Configuration</span></span>  
 <span data-ttu-id="3e9da-203">如果从 AlwaysOn 可用性组配置中删除了一个数据库，并且该数据库现在是独立数据库，我们建议使用[smart_admin sp_backup_on_demand &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql)来执行备份。</span><span class="sxs-lookup"><span data-stu-id="3e9da-203">If a database is removed from the AlwaysOn Availability Group configuration and is now a stand-alone database, we recommend doing backup using [smart_admin.sp_backup_on_demand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-on-demand-transact-sql).</span></span> <span data-ttu-id="3e9da-204">采用这种方式创建数据库备份时，将建立一个新的备份链，而文件将被放入实例特定的容器而非可用性容器中，当数据库是可用性组的一部分时，数据库存储在可用性容器中。</span><span class="sxs-lookup"><span data-stu-id="3e9da-204">When you create a database backup  this way, it establishes  a new backup chain and the file will be placed in the instance specific container as opposed to Availability container where the backups were stored when the database was part of Availability Group.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3e9da-205">无法保证在可用性组状态更改之前可在此场景下从备份恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="3e9da-205">The recoverability of the database in this scenario from backups previous to the change in the Availability Group status is not guaranteed.</span></span>  
  
