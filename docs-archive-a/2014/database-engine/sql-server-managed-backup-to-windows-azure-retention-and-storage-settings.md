---
title: SQL Server 托管备份到 Azure-保持和存储设置 |Microsoft Docs
description: 本主题介绍如何为数据库配置 SQL Server 托管备份以 Microsoft Azure，以及如何配置实例的默认设置。
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: c4aa26ea-5465-40cc-8b83-f50603cb9db1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ebdb81f8aa9edb9cd9326bcb1d286d5d3fe632c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691860"
---
# <a name="sql-server-managed-backup-to-azure---retention-and-storage-settings"></a><span data-ttu-id="bbdb2-103">针对 Azure 的 SQL Server 托管备份 - 保留和存储设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-103">SQL Server Managed Backup to Azure - Retention and Storage Settings</span></span>
  <span data-ttu-id="bbdb2-104">本主题介绍为数据库配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 以及为实例配置默认设置的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-104">This topic describes the basic steps to configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database and to configure default settings for the instance.</span></span> <span data-ttu-id="bbdb2-105">本主题还介绍为实例暂停和恢复 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服务所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-105">The topic also describes the steps necessary to pause and resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for the instance.</span></span>  
  
 <span data-ttu-id="bbdb2-106">有关设置的完整演练 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，请参阅[设置 SQL Server 托管备份到 azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) ，并[将 SQL Server 托管备份设置为可用性组的 azure](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-106">For a complete walkthrough of setting up [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] see [Setting up SQL Server Managed Backup to Azure](../relational-databases/backup-restore/enable-sql-server-managed-backup-to-microsoft-azure.md) and [Setting up SQL Server Managed Backup to Azure for Availability Groups](../../2014/database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bbdb2-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="bbdb2-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bbdb2-108">限制和局限</span><span class="sxs-lookup"><span data-stu-id="bbdb2-108">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bbdb2-109">不要对当前正使用维护计划或日志传送的数据库启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-109">Do not enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on databases that are currently using maintenance plans or log shipping.</span></span> <span data-ttu-id="bbdb2-110">有关互操作性和与其他 SQL Server 功能共存的详细信息，请参阅[SQL Server 托管备份到 Azure：互操作性和共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span><span class="sxs-lookup"><span data-stu-id="bbdb2-110">For more information on interoperability and coexistence with other SQL Server features, see [SQL Server Managed Backup to Azure: Interoperability and Coexistence](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="bbdb2-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="bbdb2-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="bbdb2-112">SQL Server 代理应运行。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-112">SQL Server Agent should be running.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="bbdb2-113">如果 SQL Server 代理停止了一段时间然后重新启动，则取决于 SQL 代理停止和启动之间的时间长度，可能会看到备份活动增多，并且可能有日志备份的积压工作等待运行。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-113">If SQL Server Agent is stopped for a period of time and then restarted, you may see an increased backup activity depending on the length of time elapsed between the stop and start of SQL Agent, and there might be a backlog of log backups waiting to run.</span></span> <span data-ttu-id="bbdb2-114">应考虑将 SQL Server 代理配置为在启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-114">Consider configuring SQL Server Agent to start automatically on start up.</span></span>  
  
-   <span data-ttu-id="bbdb2-115">将身份验证信息存储到存储帐户的 Azure 存储帐户和 SQL 凭据应该在配置之前创建 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-115">A Azure storage account and a SQL Credential that stores the authentication information to the storage account should both be created before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="bbdb2-116">有关详细信息，请参阅 [SQL Server 备份到 URL](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) 主题的 **Introduction to Key Components and Concepts** 部分以及 [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-116">For more information see [Introduction to Key Components and Concepts](../relational-databases/backup-restore/sql-server-backup-to-url.md#intorkeyconcepts) section of the **SQL Server Backup to URL** topic, and [Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="bbdb2-117">创建存储备份所需的容器。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-117">creates the necessary containers to store the backups.</span></span> <span data-ttu-id="bbdb2-118">使用 "计算机名称-实例名称" 格式创建容器名称。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-118">The container name is created using 'machine name-instance name' format.</span></span> <span data-ttu-id="bbdb2-119">对于 AlwaysOn 可用性组，使用可用性组的 GUID 为容器命名。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-119">For AlwaysOn Availability Groups the container is named using the GUID of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bbdb2-120">Security</span><span class="sxs-lookup"><span data-stu-id="bbdb2-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bbdb2-121">权限</span><span class="sxs-lookup"><span data-stu-id="bbdb2-121">Permissions</span></span>  
 <span data-ttu-id="bbdb2-122">若要运行启用的存储过程 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，您必须是 `System Administrator` 具有**ALTER ANY CREDENTIAL**权限的**db_backupoperator**数据库角色中的或成员，以及 `EXECUTE` 对**sp_delete_backuphistory**和 `smart_admin.sp_backup_master_switch` 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-122">To run the stored procedures that enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], you must be a  either a `System Administrator` or  member  in the **db_backupoperator** database role with **ALTER ANY CREDENTIAL** permissions, and `EXECUTE` permissions on the **sp_delete_backuphistory**, and `smart_admin.sp_backup_master_switch` stored procedures.</span></span>  <span data-ttu-id="bbdb2-123">用于查看现有设置的存储过程和函数通常分别需要针对存储过程的 `Execute` 权限以及针对函数的 `Select` 权限。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-123">Stored procedures and functions used to review the existing settings typically require `Execute` permissions on the stored procedure and `Select` on the function respectively.</span></span>  
  

  
###  <a name="considerations-for-enabling-ss_smartbackup-for-databases-and-instances"></a><a name="Considerations"></a><span data-ttu-id="bbdb2-124">为 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 数据库和实例启用的注意事项</span><span class="sxs-lookup"><span data-stu-id="bbdb2-124">Considerations for enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for Databases and Instances</span></span>  
 <span data-ttu-id="bbdb2-125">可单独为各个数据库或为整个实例启用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-125">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] can be enabled for individual databases separately or for the entire instance.</span></span> <span data-ttu-id="bbdb2-126">具体选项取决于针对实例上数据库的可恢复性要求，管理多个数据库和实例的要求，以及在战略上使用 Azure 存储。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-126">The choices depend on the recoverability requirements for the databases on the instance, requirements for managing multiple databases and instances, and using Azure storage strategically.</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-database-level"></a><span data-ttu-id="bbdb2-127">在数据库级别启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-127">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Database Level</span></span>  
 <span data-ttu-id="bbdb2-128">如果数据库对于备份和保持期（可恢复性 SLA）的具体要求与实例上其他的数据库不同，则为该数据库在数据库级别配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-128">If a database has specific requirements for backup and retention period (recoverability SLA) that is different from other databases on the instance, configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level for this database.</span></span> <span data-ttu-id="bbdb2-129">数据库级别设置将取代实例级别配置设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-129">Database level settings override instance level configuration settings.</span></span> <span data-ttu-id="bbdb2-130">但是，可对同一实例一起使用这两个选项。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-130">However both these options can be used together on the same instance.</span></span> <span data-ttu-id="bbdb2-131">下面列出了在数据库级别启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的优点和注意事项。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-131">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the database level.</span></span>  
  
-   <span data-ttu-id="bbdb2-132">更精细：每个数据库有单独的配置设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-132">More granular: Separate configuration settings for each database.</span></span> <span data-ttu-id="bbdb2-133">个别数据库可支持不同的保持期。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-133">Can support different retention periods for individual databases.</span></span>  
  
-   <span data-ttu-id="bbdb2-134">取代数据库的实例级别设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-134">Overrides instance level settings for the database.</span></span>  
  
-   <span data-ttu-id="bbdb2-135">可用于通过选择要备份的单独数据库，降低存储成本。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-135">Can be used to reduce storage costs by selecting individual databases to be backed up.</span></span>  
  
-   <span data-ttu-id="bbdb2-136">需要管理每个数据库</span><span class="sxs-lookup"><span data-stu-id="bbdb2-136">Requires managing each database</span></span>  
  
#### <a name="enabling-ss_smartbackup-at-the-instance-level-with-default-settings"></a><span data-ttu-id="bbdb2-137">使用默认设置在实例级别启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-137">Enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level with Default Settings</span></span>  
 <span data-ttu-id="bbdb2-138">如果实例中的大多数数据库对备份和保持策略具有相同的要求，或者如果您希望在创建时自动备份新数据库实例，则使用此设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-138">Use this setting if most of the databases in the instance have the same requirements for backup and retention policies, or if you want new database instances to automatically be backed up on creation.</span></span> <span data-ttu-id="bbdb2-139">仍可单独配置对于策略是例外的几个数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-139">A few databases that are exception to the policy can still be configured individually.</span></span> <span data-ttu-id="bbdb2-140">下面是在实例级别启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的好处和注意事项的列表。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-140">Following is a list of advantages and considerations when enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the instance level.</span></span>  
  
-   <span data-ttu-id="bbdb2-141">实例级别的自动化：常用设置自动应用于之后新添加的数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-141">Automation at the instance level: Common settings applied to automatically for new databases added thereafter.</span></span>  
  
-   <span data-ttu-id="bbdb2-142">在实例上创建新数据库后很快就自动备份这些数据库</span><span class="sxs-lookup"><span data-stu-id="bbdb2-142">New databases will be automatically backed up soon after they are created on the instances</span></span>  
  
-   <span data-ttu-id="bbdb2-143">可应用于保持期要求相同的数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-143">Can be applied to databases that have the same retention period requirements.</span></span>  
  
-   <span data-ttu-id="bbdb2-144">即使在实例级别启用了 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 备份并配置了默认设置，也仍可配置需要不同保持期的个别数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-144">You can still configure individual databases that require a different retention period even with [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] backup enabled at in instance level with default settings.</span></span> <span data-ttu-id="bbdb2-145">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]如果不打算使用 Azure 存储进行备份，也可以对数据库禁用。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-145">You can also disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for databases if you do not intend to use Azure storage for the backups.</span></span>  
  
##  <a name="enable-and-configure-ss_smartbackup-for-a-database"></a><a name="DatabaseConfigure"></a><span data-ttu-id="bbdb2-146">为数据库启用和配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-146">Enable and Configure [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a Database</span></span>  
 <span data-ttu-id="bbdb2-147">系统存储过程 `smart_admin.sp_set_db_backup` 用于为特定数据库启用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-147">The system stored procedure `smart_admin.sp_set_db_backup` is used to enable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database.</span></span> <span data-ttu-id="bbdb2-148">首次对数据库启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 时，除了启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]之外，还必须指定以下信息：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-148">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time on the database, the following information must be specified in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:</span></span>  
  
-   <span data-ttu-id="bbdb2-149">数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-149">The name of the database.</span></span>  
  
-   <span data-ttu-id="bbdb2-150">保持期。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-150">The retention period.</span></span>  
  
-   <span data-ttu-id="bbdb2-151">用于对 Azure 存储帐户进行身份验证的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-151">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="bbdb2-152">指定不使用\* \@ encryption_algorithm\*NO_ENCRYPTION 进行加密，  =  **NO_ENCRYPTION**或指定支持的加密算法。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-152">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="bbdb2-153">有关加密的详细信息，请参阅 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-153">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="bbdb2-154">仅通过 Transact-SQL 支持针对数据库级别配置的[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-154">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for database level configuration is only supported through Transact-SQL.</span></span>  
  
 <span data-ttu-id="bbdb2-155">为数据库启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 后，将保持此信息。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-155">Once [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for a database this information is persisted.</span></span> <span data-ttu-id="bbdb2-156">如果要更改配置，则只需要数据库名称和要更改的设置，未指定其他参数的现有值时， [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 保留这些值。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-156">If you are changing the configuration, only the database name and the setting you want to change is required, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values for other parameters when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bbdb2-157">在某一数据库上配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 前，它对于现有配置（如果有）可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-157">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on a database it might be useful to existing configuration if any.</span></span> <span data-ttu-id="bbdb2-158">在本节的后面将介绍查看数据库的配置设置的步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-158">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
-   <span data-ttu-id="bbdb2-159">**使用 Transact-sql：**</span><span class="sxs-lookup"><span data-stu-id="bbdb2-159">**Using Transact-SQL:**</span></span>  
  
     <span data-ttu-id="bbdb2-160">如果是 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 首次启用，则所需的参数为： \* \@ database_name*、 \* \@ credential_name* \* \@ encryption_algorithm*， \* \@ enable_backup* \* \@ storage_url\*参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-160">If you are enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the first time, the required parameters are: *\@database_name*, *\@credential_name*, *\@encryption_algorithm*,  *\@enable_backup* The *\@storage_url* parameter is optional.</span></span> <span data-ttu-id="bbdb2-161">如果未提供参数的值 @storage_url ，则使用 SQL 凭据中的存储帐户信息来派生该值。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-161">If you do not provide a value for  the @storage_url parameter, the value is derived using the storage account information from the SQL Credential.</span></span> <span data-ttu-id="bbdb2-162">如果提供存储 URL，则只应为存储帐户的根提供该 URL，并且该 URL 必须与您指定的 SQL 凭据中的信息相符。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-162">If you provide the storage URL you should only provide the URL for the root of the storage account, and must match the information in the SQL Credential you specified.</span></span>  
  
    1.  <span data-ttu-id="bbdb2-163">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-163">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
    2.  <span data-ttu-id="bbdb2-164">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-164">From the Standard bar, click **New Query**.</span></span>  
  
    3.  <span data-ttu-id="bbdb2-165">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-165">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="bbdb2-166">此示例 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 为数据库 "TestDB" 启用。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-166">This example enables [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for the database 'TestDB'.</span></span> <span data-ttu-id="bbdb2-167">保持期设置为 30 天。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-167">The retention period is set to 30 days.</span></span> <span data-ttu-id="bbdb2-168">本例通过指定加密算法和加密程序信息，使用加密选项。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-168">This sample uses the encryption option by specifying the encryption algorithm and the encryptor information.</span></span>  
  
    ```sql
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@enable_backup=1  
                    ,@retention_days =30   
                    ,@credential_name ='MyCredential'  
                    ,@encryption_algorithm ='AES_256'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
    GO
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bbdb2-169">保持期可设置为从 1 到 30 天之间的任何值。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-169">The retention period can be set to any value from 1 to 30 days.</span></span>  
    >   
    >  <span data-ttu-id="bbdb2-170">有关如何创建加密证书的详细信息，请参阅 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)中的“创建备份证书”步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-170">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
     <span data-ttu-id="bbdb2-171">有关此存储过程的详细信息，请参阅[smart_admin set_db_backup &#40;transact-sql&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="bbdb2-171">For more information on this stored procedure, see [smart_admin.set_db_backup &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/dn451013(v=sql.120).aspx)</span></span>  
  
     <span data-ttu-id="bbdb2-172">若要查看数据库的配置设置，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-172">To review the configuration settings for a database use the following query:</span></span>  
  
    ```sql
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('TestDB')  
    ```  
  
##  <a name="enable-and-configure-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceConfigure"></a><span data-ttu-id="bbdb2-173">为实例启用和配置默认 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-173">Enable and Configure Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="bbdb2-174">可以 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 通过两种方式在实例级别启用和配置默认设置：使用系统存储过程 `smart_admin.set_instance_backup` 或**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-174">You can enable and configure default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings at the instance level in two ways:  By using the system stored procedure `smart_admin.set_instance_backup` or **SQL Server Management Studio**.</span></span> <span data-ttu-id="bbdb2-175">下面说明了这两种方法：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-175">The two methods are explained below:</span></span>  
  
 <span data-ttu-id="bbdb2-176">**smart_admin. set_instance_backup：**。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-176">**smart_admin.set_instance_backup:**.</span></span> <span data-ttu-id="bbdb2-177">通过为\* \@ enable_backup*参数指定值\*\*1*\* ，可以启用备份并设置默认配置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-177">By specifying the value **1** for *\@enable_backup* parameter, you can enable backup and set the default configurations.</span></span> <span data-ttu-id="bbdb2-178">在实例级别应用后，将这些默认设置应用于添加到此实例的任何新数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-178">Once applied at the instance level, these default settings are applied to any new database that is added to this instance.</span></span>  <span data-ttu-id="bbdb2-179">首次启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 时，除了对实例启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 之外，还必须提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-179">When [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the first time, the following information must be provided in addition to enabling [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on the instance:</span></span>  
  
-   <span data-ttu-id="bbdb2-180">保持期。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-180">The retention period.</span></span>  
  
-   <span data-ttu-id="bbdb2-181">用于对 Azure 存储帐户进行身份验证的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-181">SQL Credential used to authenticate to the Azure storage account.</span></span>  
  
-   <span data-ttu-id="bbdb2-182">加密选项。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-182">The encryption option.</span></span> <span data-ttu-id="bbdb2-183">指定不使用\* \@ encryption_algorithm\*NO_ENCRYPTION 进行加密，  =  **NO_ENCRYPTION**或指定支持的加密算法。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-183">Either specify not to encrypt using *\@encryption_algorithm* = **NO_ENCRYPTION** or specify a supported encryption algorithm.</span></span> <span data-ttu-id="bbdb2-184">有关加密的详细信息，请参阅 [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-184">For more information on encryption, see [Backup Encryption](../relational-databases/backup-restore/backup-encryption.md).</span></span>  
  
 <span data-ttu-id="bbdb2-185">启用后，这些设置将被保留。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-185">Once enabled these settings are persisted.</span></span> <span data-ttu-id="bbdb2-186">如果要更改配置，则只需要数据库名称和要更改的设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-186">If you are changing the configuration, only the database name and the setting you want to change is required.</span></span> <span data-ttu-id="bbdb2-187">未指定现有的值时，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]保留这些值。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-187">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] retains the existing values when not specified.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bbdb2-188">在某一实例上配置 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 前，它对于检查现有配置（如果有）可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-188">Before configuring [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] on an instance, it might be useful to check for existing configuration, if any.</span></span> <span data-ttu-id="bbdb2-189">在本节的后面将介绍查看数据库的配置设置的步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-189">The step to reviewing configuration settings for a database is explained later in this section.</span></span>  
  
 <span data-ttu-id="bbdb2-190">**SQL Server Management Studio：** 若要在 SQL Server Management Studio 中执行此任务，请转到对象资源管理器，展开 **“管理”** 节点，然后右键单击 **“托管备份”**。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-190">**SQL Server Management Studio:** To do this task in SQL Server Management Studio, go the object explorer, expand the **Management** node, and right click on **Managed Backup**.</span></span> <span data-ttu-id="bbdb2-191">选择“配置” 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-191">Select **Configure**.</span></span> <span data-ttu-id="bbdb2-192">这将打开 **“托管备份”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-192">This opens the **Managed Backup** dialog.</span></span> <span data-ttu-id="bbdb2-193">使用此对话框可指定保持期、SQL 凭据、存储 URL 和加密设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-193">Use this dialog to specify the retention period, SQL Credential, Storage URL, and the encryption settings.</span></span> <span data-ttu-id="bbdb2-194">有关此对话框的特定帮助，请参阅[配置托管备份 &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-194">For specific help with this dialog, see [Configure Managed Backup &#40;SQL Server Management Studio&#41;](configure-managed-backup-sql-server-management-studio.md).</span></span>  
  
#### <a name="using-transact-sql"></a><span data-ttu-id="bbdb2-195">“使用 Transact-SQL”</span><span class="sxs-lookup"><span data-stu-id="bbdb2-195">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="bbdb2-196">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-196">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-197">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-197">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-198">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-198">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
   EXEC smart_admin.sp_set_instance_backup  
                @retention_days=30   
                ,@credential_name='sqlbackuptoURL'  
                ,@encryption_algorithm ='AES_128'  
                ,@encryptor_type= 'Certificate'  
                ,@encryptor_name='MyBackupCert'  
                ,@enable_backup=1;  
GO  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bbdb2-199">保持期可设置为从 1 到 30 天之间的任何值。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-199">The retention period can be set to any value from 1 to 30 days.</span></span>  
>   
>  <span data-ttu-id="bbdb2-200">有关如何创建加密证书的详细信息，请参阅 [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md)中的“创建备份证书”步骤。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-200">For more information on creating a certificate for encryption, see the Create a Backup Certificate step in [Create an Encrypted Backup](../relational-databases/backup-restore/create-an-encrypted-backup.md).</span></span>  
  
 <span data-ttu-id="bbdb2-201">若要查看实例的默认配置设置，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-201">To view the default configuration settings for the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_instance_config ();
```  
  
#### <a name="using-powershell"></a><span data-ttu-id="bbdb2-202">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbdb2-202">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="bbdb2-203">启动 PowerShell 实例</span><span class="sxs-lookup"><span data-stu-id="bbdb2-203">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="bbdb2-204">在修改后运行以下脚本以便适合您的设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-204">Run the following script after modifying it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    $encryptionOption = New-SqlBackupEncryptionOption -EncryptionAlgorithm Aes128 -EncryptorType ServerCertificate -EncryptorName "MyBackupCert"  
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -BackupEnabled $True -BackupRetentionPeriodInDays 10 -EncryptionOption $encryptionOption  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bbdb2-205">在您在配置默认设置后创建新的数据库时，最多需要用 15 分钟以便使用默认设置配置该数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-205">When you create a new database after configuring the default settings, it may take up to 15 minutes for the database to be configured with the default settings.</span></span> <span data-ttu-id="bbdb2-206">这也将应用于从 **Simple** 更改为 **Full** 或 **Bulk-Logged** 恢复模型的数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-206">This also applies to databases that are changed from **Simple** to **Full** or **Bulk-Logged** recovery model.</span></span>  
  
##  <a name="disable-ss_smartbackup-for-a-database"></a><a name="DatabaseDisable"></a> <span data-ttu-id="bbdb2-207">为数据库禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-207">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a database</span></span>  
 <span data-ttu-id="bbdb2-208">可通过使用 `sp_set_db_backup` 系统存储过程，禁用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-208">You can disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings by using the `sp_set_db_backup` system stored procedure.</span></span> <span data-ttu-id="bbdb2-209">\* \@ Enableparameter\*用于启用和禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 特定数据库的配置; 其中，1启用，0禁用配置设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-209">The *\@enableparameter* is used to enable and disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configurations for a specific database, where 1 enables and 0 disables the configuration settings.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-for-a-specific-database"></a><span data-ttu-id="bbdb2-210">为特定数据库禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-210">To Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for a specific database:</span></span>  
  
1.  <span data-ttu-id="bbdb2-211">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-211">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-212">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-212">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-213">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-213">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin.sp_set_db_backup   
                @database_name='TestDB'   
                ,@enable_backup=0;  
GO
```  
  
##  <a name="disable-ss_smartbackup-for-all-the-databases-on-the-instance"></a><a name="DatabaseAllDisable"></a> <span data-ttu-id="bbdb2-214">为实例上的所有数据库禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-214">Disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] for all the databases on the Instance</span></span>  
 <span data-ttu-id="bbdb2-215">下面的过程适用于要从实例上当前启用了 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 的所有数据库禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 配置设置的情形。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-215">The following procedure is for when you want to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] configuration settings from all the databases that currently have [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled on the instance.</span></span>  <span data-ttu-id="bbdb2-216">存储 URL、保持和 SQL 凭据之类的配置设置将在元数据中保留；并且如果以后为数据库启用了 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，则可以使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-216">The configuration settings like the storage URL, retention, and the SQL Credential will remain in the metadata and can be used  if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the database at a later time.</span></span> <span data-ttu-id="bbdb2-217">如果您要暂停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服务，则可以使用在本主题后面的以下部分中说明的主开关。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-217">If you want to just pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services temporarily, you can use the master switch explained in the following sections later in this topic.</span></span>  
  
#### <a name="to-disable-ss_smartbackupfor-all-the-databases"></a><span data-ttu-id="bbdb2-218">为所有数据库禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-218">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]for all the databases:</span></span>  
  
1.  <span data-ttu-id="bbdb2-219">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-219">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-220">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-220">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-221">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-221">Copy and paste the following example into the query window and click `Execute`.</span></span> <span data-ttu-id="bbdb2-222">下例确定是否在实例级别配置了[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]以及是否所有启用了[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]的数据库都在实例上，并且执行系统存储过程 `sp_set_db_backup` 以禁用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-222">The following example identifies if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured at the instance level and all the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled databases on the instance, and executes the system stored procedure `sp_set_db_backup` to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span>  
  
```sql
-- Create a working table to store the database names  
Declare @DBNames TABLE  
  
       (  
             RowID int IDENTITY PRIMARY KEY  
             ,DBName varchar(500)  
  
       )  
-- Define the variables  
DECLARE @rowid int  
DECLARE @dbname varchar(500)  
DECLARE @SQL varchar(2000)  
-- Get the database names from the system function  
  
INSERT INTO @DBNames (DBName)  
  
SELECT db_name  
       FROM
  
       smart_admin.fn_backup_db_config (NULL)  
       WHERE is_smart_backup_enabled = 1  
  
       --Select DBName from @DBNames 
       select @rowid = min(RowID) FROM @DBNames  
  
       WHILE @rowID IS NOT NULL  
       Begin
             Set @dbname = (Select DBName From @DBNames Where RowID = @rowid)  
             Begin  
             Set @SQL = 'EXEC smart_admin.sp_set_db_backup    
                @database_name= '''+'' + @dbname+ ''+''',   
                @enable_backup=0'  
  
            EXECUTE (@SQL)  
  
             END  
             Select @rowid = min(RowID)  
             From @DBNames Where RowID > @rowid  
  
       END
```  
  
 <span data-ttu-id="bbdb2-223">若要查看实例上所有数据库的配置设置，请使用以下查询：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-223">To review the configuration settings for all the databases on the instance, use the following query:</span></span>  
  
```sql
Use msdb;  
GO  
SELECT * FROM smart_admin.fn_backup_db_config (NULL);  
GO
```  
  
##  <a name="disable-default-ss_smartbackup-settings-for-the-instance"></a><a name="InstanceDisable"></a> <span data-ttu-id="bbdb2-224">禁用实例的默认 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-224">Disable Default [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] settings for the Instance</span></span>  
 <span data-ttu-id="bbdb2-225">实例级别的默认设置适用于在该实例上创建的所有新数据库。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-225">Default settings at the instance level apply to all new databases created on that instance.</span></span>  <span data-ttu-id="bbdb2-226">如果不再需要默认设置，则可以通过使用 **smart_admin.sp_set_instance_backup** 系统存储过程，禁用此配置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-226">If you no longer need or require default settings, you can disable this configuration by using the **smart_admin.sp_set_instance_backup** System stored procedure.</span></span> <span data-ttu-id="bbdb2-227">禁用并不会删除存储 URL、保持设置或 SQL 凭据名称之类的其他配置设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-227">Disabling does not remove the other configuration settings like the storage URL, retention setting, or the SQL Credential name.</span></span> <span data-ttu-id="bbdb2-228">如果以后为该实例启用了 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ，将使用这些设置。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-228">These settings will be used if [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is enabled for the instance at a later time.</span></span>  
  
#### <a name="to-disable-ss_smartbackup-default-configuration-settings"></a><span data-ttu-id="bbdb2-229">禁用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 默认配置设置：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-229">To disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] default configuration settings:</span></span>  
  
1.  <span data-ttu-id="bbdb2-230">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-230">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-231">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-231">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-232">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-232">Copy and paste the following example into the query window and click `Execute`.</span></span>  
  
    ```sql
    Use msdb;  
    Go  
    EXEC smart_admin.sp_set_instance_backup  
                    @enable_backup=0;  
    GO
    ```  
  
#### <a name="using-powershell"></a><span data-ttu-id="bbdb2-233">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbdb2-233">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="bbdb2-234">启动 PowerShell 实例</span><span class="sxs-lookup"><span data-stu-id="bbdb2-234">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="bbdb2-235">运行以下脚本：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-235">Run the following script:</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Set-SqlSmartAdmin -BackupEnabled $False  
    ```  
  
##  <a name="pause-ss_smartbackup-at-the-instance-level"></a><a name="InstancePause"></a> <span data-ttu-id="bbdb2-236">在实例级别暂停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-236">Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] at the Instance Level</span></span>  
 <span data-ttu-id="bbdb2-237">有时可能需要在短期内临时暂停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-237">There might be times when you need to temporarily pause the [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] services for a short period time.</span></span>  <span data-ttu-id="bbdb2-238">通过 `smart_admin.sp_backup_master_switch` 系统存储过程，可在实例级别禁用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]服务。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-238">The `smart_admin.sp_backup_master_switch` system stored procedure allows you to disable [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] service at the instance level.</span></span>  <span data-ttu-id="bbdb2-239">使用相同的存储过程恢复 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-239">The same stored procedure is used to resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="bbdb2-240">@state 参数用于定义是应禁用还是启用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-240">The @state parameter is used to define whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] should be turned off or on.</span></span>  
  
#### <a name="to-pause-ss_smartbackup-services-using-transact-sql"></a><span data-ttu-id="bbdb2-241">使用 Transact-SQL 暂停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 服务：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-241">To Pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Services Using Transact-SQL:</span></span>  
  
1.  <span data-ttu-id="bbdb2-242">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-242">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-243">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-243">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-244">将以下示例复制并粘贴到查询窗口中，然后单击`Execute`</span><span class="sxs-lookup"><span data-stu-id="bbdb2-244">Copy and paste the following example into the query window and then click `Execute`</span></span>  
  
```sql
Use msdb;  
GO  
EXEC smart_admin.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
#### <a name="to-pause-ss_smartbackup-using-powershell"></a><span data-ttu-id="bbdb2-245">使用 PowerShell 暂停 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-245">To pause [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="bbdb2-246">启动 PowerShell 实例</span><span class="sxs-lookup"><span data-stu-id="bbdb2-246">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="bbdb2-247">在修改后运行以下脚本以便适合您的设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-247">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $False  
    ```  
  
#### <a name="to-resume-ss_smartbackup-using-transact-sql"></a><span data-ttu-id="bbdb2-248">使用 Transact-SQL 恢复 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="bbdb2-248">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="bbdb2-249">连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-249">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbdb2-250">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-250">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bbdb2-251">将以下示例复制并粘贴到查询窗口中，然后单击 `Execute` 。</span><span class="sxs-lookup"><span data-stu-id="bbdb2-251">Copy and paste the following example into the query window and then click `Execute`.</span></span>  
  
```sql
Use msdb;  
Go  
EXEC smart_admin. sp_backup_master_switch @new_state=1;  
GO
```  
  
#### <a name="to-resume-ss_smartbackup-using-powershell"></a><span data-ttu-id="bbdb2-252">使用 PowerShell 恢复 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdb2-252">To resume [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Using PowerShell</span></span>  
  
1.  <span data-ttu-id="bbdb2-253">启动 PowerShell 实例</span><span class="sxs-lookup"><span data-stu-id="bbdb2-253">Start a PowerShell Instance</span></span>  
  
2.  <span data-ttu-id="bbdb2-254">在修改后运行以下脚本以便适合您的设置</span><span class="sxs-lookup"><span data-stu-id="bbdb2-254">Run the following script after you modify it to suit your settings</span></span>  
  
    ```powershell
    cd SQLSERVER:\SQL\Computer\MyInstance
    Get-SqlSmartAdmin | Set-SqlSmartAdmin -MasterSwitch $True  
    ```  
