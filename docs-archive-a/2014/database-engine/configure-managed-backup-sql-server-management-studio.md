---
title: 配置托管备份 (SQL Server Management Studio) |Microsoft Docs
description: 使用 "托管备份" 对话框可以配置 SQL Server 托管备份到 Azure 的默认设置。 了解需要考虑的选项。
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e952ef1102ac67bd0ed9f72d0c201d54b320b5ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576984"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a><span data-ttu-id="79d52-104">配置托管备份 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="79d52-104">Configure Managed Backup (SQL Server Management Studio)</span></span>
  <span data-ttu-id="79d52-105">"**托管备份**" 对话框允许您为 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 实例配置默认值。</span><span class="sxs-lookup"><span data-stu-id="79d52-105">The **Managed Backup** dialog allows you to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] defaults for the instance.</span></span> <span data-ttu-id="79d52-106">本主题介绍如何使用此对话框来配置实例的 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 默认设置以及执行此操作时必须考虑的选项。</span><span class="sxs-lookup"><span data-stu-id="79d52-106">This topic describes how to use this dialog to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default settings for the instance and options you must consider when doing so.</span></span> <span data-ttu-id="79d52-107">为实例配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 时，该设置将应用于任何此后创建的新数据库。</span><span class="sxs-lookup"><span data-stu-id="79d52-107">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for the instance, the settings are applied to any new database created thereafter.</span></span>  
  
 <span data-ttu-id="79d52-108">如果要 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 为特定数据库配置，请参阅为[数据库启用和配置 SQL Server 托管备份到 Azure](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)。</span><span class="sxs-lookup"><span data-stu-id="79d52-108">If you want to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="79d52-109">代理服务器不支持 SQL Server 托管备份。</span><span class="sxs-lookup"><span data-stu-id="79d52-109">SQL Server Managed Backup is not supported with proxy servers.</span></span> 
  
## <a name="task-list"></a><span data-ttu-id="79d52-110">任务列表</span><span class="sxs-lookup"><span data-stu-id="79d52-110">Task List</span></span>  
  
## <a name="ss_smartbackup-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] <span data-ttu-id="79d52-111">函数使用 SQL Server Management Studio 中的托管备份接口</span><span class="sxs-lookup"><span data-stu-id="79d52-111">Functions Using Managed Backup Interface in SQL Server Management Studio</span></span>  
 <span data-ttu-id="79d52-112">在此版本中，你只能使用**管理备份**接口配置实例级别的默认设置。</span><span class="sxs-lookup"><span data-stu-id="79d52-112">In this release, you can only configure instance level default settings using the **Management Backup** interface.</span></span> <span data-ttu-id="79d52-113">你不能为数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]、暂停或继续 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 操作，或设置电子邮件通知。</span><span class="sxs-lookup"><span data-stu-id="79d52-113">You cannot configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database, pause or resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations, or setup email notifications.</span></span> <span data-ttu-id="79d52-114">有关如何执行当前不受**托管备份**接口支持的操作的信息，请参阅[SQL Server 托管备份到 Azure-保持和存储设置](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="79d52-114">For information on how to perform operations not currently supported through the **Managed Backup** interface, see [SQL Server Managed Backup to Azure - Retention and Storage Settings](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="79d52-115">权限</span><span class="sxs-lookup"><span data-stu-id="79d52-115">Permissions</span></span>  
 <span data-ttu-id="79d52-116">**SQL Server Management Studio 查看托管备份节点：** 若要查看**对象资源管理器**中的**托管备份**节点，你必须是系统管理员或具有专门授予你的用户帐户的下列权限：</span><span class="sxs-lookup"><span data-stu-id="79d52-116">**View Managed Backup Node is SQL Server Management Studio:** To view  **Managed Backup** node in **Object Explorer**, you must either be a System Admin or have the following permissions specifically granted to your user account:</span></span>  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   <span data-ttu-id="79d52-117">`EXECUTE` 上的 `smart_admin.fn_is_master_switch_on`</span><span class="sxs-lookup"><span data-stu-id="79d52-117">`EXECUTE` on `smart_admin.fn_is_master_switch_on`.</span></span>  
  
-   <span data-ttu-id="79d52-118">`SELECT` 上的 `smart_admin.fn_backup_instance_config`</span><span class="sxs-lookup"><span data-stu-id="79d52-118">`SELECT` on `smart_admin.fn_backup_instance_config`.</span></span>  
  
 <span data-ttu-id="79d52-119">**若要配置托管备份：** 若要 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 在 SQL Server Management Studio 中配置，您必须是系统管理员或具有以下权限：</span><span class="sxs-lookup"><span data-stu-id="79d52-119">**To Configure Managed Backup:** to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] in SQL Server Management Studio, you must be a System Administrator or have the following permissions:</span></span>  
  
 <span data-ttu-id="79d52-120">`db_backupoperator` 数据库角色中的成员、具有 `ALTER ANY CREDENTIAL` 权限，以及对 `sp_delete_backuphistory` 存储过程具有 `EXECUTE` 权限。</span><span class="sxs-lookup"><span data-stu-id="79d52-120">Membership in `db_backupoperator` database role, with `ALTER ANY CREDENTIAL` permissions, and `EXECUTE` permissions on `sp_delete_backuphistory` stored procedure.</span></span>  
  
 <span data-ttu-id="79d52-121">对 `smart_admin.fn_get_current_xevent_settings` 函数的 `SELECT` 权限。</span><span class="sxs-lookup"><span data-stu-id="79d52-121">`SELECT` permissions on the `smart_admin.fn_get_current_xevent_settings` function.</span></span>  
  
 <span data-ttu-id="79d52-122">`EXECUTE`对 `smart_admin.sp_get_backup_diagnostics` 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="79d52-122">`EXECUTE` permissions on the `smart_admin.sp_get_backup_diagnostics` stored procedure.</span></span> <span data-ttu-id="79d52-123">此外，它还需要 `VIEW SERVER STATE` 权限，因为它在内部调用其他需要此权限的系统对象。</span><span class="sxs-lookup"><span data-stu-id="79d52-123">In addition, it requires `VIEW SERVER STATE` permissions as it internally calls other system objects that require this permission.</span></span>  
  
 <span data-ttu-id="79d52-124">对 `smart_admin.sp_set_instance_backup` 和 `smart_admin.sp_backup_master_switch` 的`EXECUTE` 权限。</span><span class="sxs-lookup"><span data-stu-id="79d52-124">`EXECUTE` permissions on `smart_admin.sp_set_instance_backup`, and `smart_admin.sp_backup_master_switch`.</span></span>  
  
## <a name="configure-ss_smartbackup-using-sql-server-management-studio"></a><span data-ttu-id="79d52-125">使用 SQL Server Management Studio 配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d52-125">Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] using SQL Server Management Studio</span></span>  
 <span data-ttu-id="79d52-126">从 "**对象资源管理器**" 中，展开 "**管理**" 节点，然后右键单击 "**托管备份**"。</span><span class="sxs-lookup"><span data-stu-id="79d52-126">From the **object explorer**, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="79d52-127">选择“配置” 。</span><span class="sxs-lookup"><span data-stu-id="79d52-127">Select **Configure**.</span></span> <span data-ttu-id="79d52-128">这将打开 **“托管备份”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="79d52-128">This opens the **Managed Backup** dialog.</span></span>  
  
 <span data-ttu-id="79d52-129">选中 "**启用托管备份**" 选项并指定配置值：</span><span class="sxs-lookup"><span data-stu-id="79d52-129">Check **Enable Managed Backup** option and specify the configuration values:</span></span>  
  
 <span data-ttu-id="79d52-130">**文件保留**期按天指定，并且应介于1和30之间。</span><span class="sxs-lookup"><span data-stu-id="79d52-130">The **File retention** period is specified in days and should be between 1 and 30.</span></span>  
  
 <span data-ttu-id="79d52-131">选择的**SQL 凭据**应与存储帐户匹配。</span><span class="sxs-lookup"><span data-stu-id="79d52-131">The **SQL Credential** you select should match the storage account.</span></span> <span data-ttu-id="79d52-132">如果当前没有用于存储身份验证信息的 SQL 凭据，则可以通过单击 "**创建**" 来创建一个。</span><span class="sxs-lookup"><span data-stu-id="79d52-132">If you currently do not have a SQL Credential that stores the authentication information, you can create one by clicking **Create**.</span></span> <span data-ttu-id="79d52-133">你还可以通过使用 CREATE CREDENTIAL Transact-SQL 语句创建凭据，并提供用于身份识别的存储帐户名和用于 SECRET 参数的访问密钥。</span><span class="sxs-lookup"><span data-stu-id="79d52-133">You can also create credential by using the CREATE CREDENTIAL Transact-SQL statement, and provide the storage account name for Identity and the access key for the SECRET parameters.</span></span> <span data-ttu-id="79d52-134">有关详细信息，请参阅[创建凭据](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential)。</span><span class="sxs-lookup"><span data-stu-id="79d52-134">For more information, see [Create a Credential](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).</span></span>  
  
 <span data-ttu-id="79d52-135">指定 Azure 存储帐户的**存储 URL** 、存储存储帐户的身份验证信息的 SQL 凭据以及备份文件的保留期。</span><span class="sxs-lookup"><span data-stu-id="79d52-135">Specify the **Storage URL** for the Azure storage account, the SQL Credential that stores the authentication information for the storage account, and the retention period for the backup files.</span></span>  
  
 <span data-ttu-id="79d52-136">存储 URL 格式为： https:// \<StorageAccount> 。 blob.core.windows.net/</span><span class="sxs-lookup"><span data-stu-id="79d52-136">The storage URL format is: https://\<StorageAccount>.blob.core.windows.net/</span></span>  
  
 <span data-ttu-id="79d52-137">若要在实例级别设置加密设置，请选中 "**加密备份**" 选项，并指定要用于加密的算法和证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="79d52-137">To set the encryption settings at the instance level, check **Encrypt Backup** option, and specify the algorithm and a Certificate or Asymmetric Key to use for the encryption.</span></span>  <span data-ttu-id="79d52-138">以实例级别设置的此值将用于应用此配置后创建的所有新数据库。</span><span class="sxs-lookup"><span data-stu-id="79d52-138">This is set at the instance level is used for all the new databases created once this configuration has been applied.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="79d52-139">如果未配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，则此对话框不能用于指定加密选项。</span><span class="sxs-lookup"><span data-stu-id="79d52-139">This dialog cannot be used to specify the encryption options without configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="79d52-140">这些加密选项仅适用于 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 操作。</span><span class="sxs-lookup"><span data-stu-id="79d52-140">These encryption options only apply to [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] operations.</span></span> <span data-ttu-id="79d52-141">若要对其他备份过程使用加密，请参阅[备份加密](../relational-databases/backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="79d52-141">To use encryption for other backup procedures, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
### <a name="considerations"></a><span data-ttu-id="79d52-142">注意事项</span><span class="sxs-lookup"><span data-stu-id="79d52-142">Considerations</span></span>  
 <span data-ttu-id="79d52-143">如果你以实例级别配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，此设置将应用于任何此后创建的新数据库。</span><span class="sxs-lookup"><span data-stu-id="79d52-143">If you configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level, the settings are applied to any new database created thereafter.</span></span>  <span data-ttu-id="79d52-144">然而，现有数据库将不会自动继承这些设置。</span><span class="sxs-lookup"><span data-stu-id="79d52-144">However, existing database will not automatically inherit these settings.</span></span> <span data-ttu-id="79d52-145">若要为以前存在的数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，你必须专门配置每个数据库。</span><span class="sxs-lookup"><span data-stu-id="79d52-145">To configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on previously existing databases, you must configure each database specifically.</span></span> <span data-ttu-id="79d52-146">有关详细信息，请参阅为[数据库启用和配置 SQL Server 托管备份到 Azure](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure)。</span><span class="sxs-lookup"><span data-stu-id="79d52-146">For more information, see [Enable and Configure SQL Server Managed Backup to Azure for a Database](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).</span></span>  
  
 <span data-ttu-id="79d52-147">如果 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 使用暂停 `smart_admin.sp_backup_master_switch` ，你将看到一条警告消息 "已禁用托管备份，当前配置将无法生效 ..."尝试完成配置时。</span><span class="sxs-lookup"><span data-stu-id="79d52-147">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has been paused using the `smart_admin.sp_backup_master_switch`, you will see a warning message " Managed Backup is disabled and the current configurations will not take effect..." when you try to complete the configuration.</span></span> <span data-ttu-id="79d52-148">使用 `smart_admin.sp_backup_master_switch` 存储的并设置 @new_state = 1。</span><span class="sxs-lookup"><span data-stu-id="79d52-148">Use the `smart_admin.sp_backup_master_switch` stored and set the @new_state=1.</span></span> <span data-ttu-id="79d52-149">这将恢复 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服务且该配置设置将生效。</span><span class="sxs-lookup"><span data-stu-id="79d52-149">This will resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services and the configuration settings will take into effect.</span></span> <span data-ttu-id="79d52-150">有关存储过程的详细信息，请参阅[smart_admin backup_master_switch &#40;transact-sql&#41;sp_ ](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="79d52-150">For more information on the stored procedure, see [smart_admin.sp_ backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d52-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="79d52-151">See Also</span></span>  
 [<span data-ttu-id="79d52-152">SQL Server 托管备份到 Azure：互操作性和共存</span><span class="sxs-lookup"><span data-stu-id="79d52-152">SQL Server Managed Backup to Azure: Interoperability and Coexistence</span></span>](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
