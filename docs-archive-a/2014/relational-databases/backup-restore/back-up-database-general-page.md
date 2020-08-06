---
title: 备份数据库（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c315c827e1c8b206b2098009510bf6468bd7d74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591428"
---
# <a name="back-up-database-general-page"></a><span data-ttu-id="97808-102">备份数据库（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="97808-102">Back Up Database (General Page)</span></span>
  <span data-ttu-id="97808-103">使用 **“备份数据库”** 对话框中的 **“常规”** 页可以查看或修改数据库备份操作的设置。</span><span class="sxs-lookup"><span data-stu-id="97808-103">Use the **General** page of the **Back Up Database** dialog box to view or modify settings for a database back up operation.</span></span>  
  
 <span data-ttu-id="97808-104">有关基本备份概念的详细信息，请参阅 [备份概述 (SQL Server)](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97808-104">For more information about basic backup concepts, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97808-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定备份任务时，可以通过单击“脚本”  按钮，再为脚本选择一个目标，生成对应的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 脚本。</span><span class="sxs-lookup"><span data-stu-id="97808-105">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
 <span data-ttu-id="97808-106">**使用 SQL Server Management Studio 创建备份**</span><span class="sxs-lookup"><span data-stu-id="97808-106">**To use SQL Server Management Studio to create a backup**</span></span>  
  
-   [<span data-ttu-id="97808-107">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97808-107">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="97808-108">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97808-108">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="97808-109">可以定义用于创建数据库备份的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="97808-109">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="97808-110">有关详细信息，请参阅 [联机丛书中的](../maintenance-plans/maintenance-plans.md) 数据库维护计划 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="97808-110">For more information, see [Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="97808-111">**创建部分备份**</span><span class="sxs-lookup"><span data-stu-id="97808-111">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="97808-112">对于部分备份，必须使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句和 PARTIAL 选项。</span><span class="sxs-lookup"><span data-stu-id="97808-112">For a partial backup, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97808-113">选项</span><span class="sxs-lookup"><span data-stu-id="97808-113">Options</span></span>  
  
### <a name="source"></a><span data-ttu-id="97808-114">源</span><span class="sxs-lookup"><span data-stu-id="97808-114">Source</span></span>  
 <span data-ttu-id="97808-115">可通过 **“源”** 面板中的选项标识数据库并指定备份操作的备份类型和组件。</span><span class="sxs-lookup"><span data-stu-id="97808-115">The options of the **Source** panel identify the database and specify the backup type and component for the back up operation.</span></span>  
  
 <span data-ttu-id="97808-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="97808-116">**Database**</span></span>  
 <span data-ttu-id="97808-117">选择要备份的数据库。</span><span class="sxs-lookup"><span data-stu-id="97808-117">Select the database to back up.</span></span>  
  
 <span data-ttu-id="97808-118">**恢复模式**</span><span class="sxs-lookup"><span data-stu-id="97808-118">**Recovery model**</span></span>  
 <span data-ttu-id="97808-119">查看为所选数据库显示的恢复模式（SIMPLE、FULL 或 BULK_LOGGED）。</span><span class="sxs-lookup"><span data-stu-id="97808-119">View the recovery model (SIMPLE, FULL, or BULK_LOGGED) displayed for the selected database.</span></span>  
  
 <span data-ttu-id="97808-120">**备份类型**</span><span class="sxs-lookup"><span data-stu-id="97808-120">**Backup type**</span></span>  
 <span data-ttu-id="97808-121">选择要对指定数据库执行的备份的类型。</span><span class="sxs-lookup"><span data-stu-id="97808-121">Select the type of backup you want to perform on the specified database.</span></span>  
  
|<span data-ttu-id="97808-122">备份类型</span><span class="sxs-lookup"><span data-stu-id="97808-122">Backup type</span></span>|<span data-ttu-id="97808-123">适用于</span><span class="sxs-lookup"><span data-stu-id="97808-123">Available for</span></span>|<span data-ttu-id="97808-124">限制</span><span class="sxs-lookup"><span data-stu-id="97808-124">Restrictions</span></span>|  
|-----------------|-------------------|------------------|  
|<span data-ttu-id="97808-125">完全</span><span class="sxs-lookup"><span data-stu-id="97808-125">Full</span></span>|<span data-ttu-id="97808-126">数据库、文件和文件组</span><span class="sxs-lookup"><span data-stu-id="97808-126">Databases, files, and filegroups</span></span>|<span data-ttu-id="97808-127">对于 **master** 数据库，只能执行完整备份。</span><span class="sxs-lookup"><span data-stu-id="97808-127">On the **master** database, only full backups are possible.</span></span><br /><br /> <span data-ttu-id="97808-128">在简单恢复模式下，文件和文件组备份只适用于只读文件组。</span><span class="sxs-lookup"><span data-stu-id="97808-128">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="97808-129">差异</span><span class="sxs-lookup"><span data-stu-id="97808-129">Differential</span></span>|<span data-ttu-id="97808-130">数据库、文件和文件组</span><span class="sxs-lookup"><span data-stu-id="97808-130">Databases, files, and filegroups</span></span>|<span data-ttu-id="97808-131">在简单恢复模式下，文件和文件组备份只适用于只读文件组。</span><span class="sxs-lookup"><span data-stu-id="97808-131">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="97808-132">事务日志</span><span class="sxs-lookup"><span data-stu-id="97808-132">Transaction Log</span></span>|<span data-ttu-id="97808-133">事务日志</span><span class="sxs-lookup"><span data-stu-id="97808-133">Transaction logs</span></span>|<span data-ttu-id="97808-134">事务日志备份不适用于简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="97808-134">Transaction log backups are not available for the Simple Recovery Model.</span></span>|  
  
 <span data-ttu-id="97808-135">**仅复制备份**</span><span class="sxs-lookup"><span data-stu-id="97808-135">**Copy Only Backup**</span></span>  
 <span data-ttu-id="97808-136">选择创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="97808-136">Select to create a copy-only backup.</span></span> <span data-ttu-id="97808-137">*仅复制备份*是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独立于常规备份序列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的备份。</span><span class="sxs-lookup"><span data-stu-id="97808-137">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="97808-138">有关详细信息，请参阅[仅复制备份 (SQL Server)](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97808-138">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97808-139">选择“差异”  选项时，无法创建仅复制备份。</span><span class="sxs-lookup"><span data-stu-id="97808-139">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
 <span data-ttu-id="97808-140">**备份组件**</span><span class="sxs-lookup"><span data-stu-id="97808-140">**Backup component**</span></span>  
 <span data-ttu-id="97808-141">选择要备份的数据库组件。</span><span class="sxs-lookup"><span data-stu-id="97808-141">Select the database component to be backed up.</span></span> <span data-ttu-id="97808-142">如果在 **“备份类型”** 列表中选择了 **“事务日志”** ，则不会激活此选项。</span><span class="sxs-lookup"><span data-stu-id="97808-142">If **Transaction Log** is selected in the **Backup type** list, this option is not activated.</span></span>  
  
 <span data-ttu-id="97808-143">选择以下选项按钮之一：</span><span class="sxs-lookup"><span data-stu-id="97808-143">Select one of the following option buttons:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97808-144">**Database**</span><span class="sxs-lookup"><span data-stu-id="97808-144">**Database**</span></span>|<span data-ttu-id="97808-145">指定备份整个数据库。</span><span class="sxs-lookup"><span data-stu-id="97808-145">Specifies that the entire database be backed up.</span></span>|  
|<span data-ttu-id="97808-146">**文件和文件组**</span><span class="sxs-lookup"><span data-stu-id="97808-146">**Files and filegroups**</span></span>|<span data-ttu-id="97808-147">指定要备份的文件和/或文件组。</span><span class="sxs-lookup"><span data-stu-id="97808-147">Specifies that the specified files and/or filegroups be backed up.</span></span><br /><br /> <span data-ttu-id="97808-148">选择此选项，打开 **“选择文件和文件组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="97808-148">Selecting this option, opens the **Select Files and Filegroups** dialog box.</span></span> <span data-ttu-id="97808-149">在选择要备份的文件组或文件并单击“确定”  后，所选内容将显示在“文件组和文件”  框中。</span><span class="sxs-lookup"><span data-stu-id="97808-149">After you select the filegroups or files you want to back up and click **Ok**, your selections appear in the **Filegroups and files** box.</span></span>|  
  
### <a name="destination"></a><span data-ttu-id="97808-150">目标</span><span class="sxs-lookup"><span data-stu-id="97808-150">Destination</span></span>  
 <span data-ttu-id="97808-151">“目标”  面板中的选项允许您为备份操作指定备份设备的类型，并查找现有的逻辑或物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="97808-151">The options of the **Destination** panel allow for you to specify the type of backup device for the back up operation and find an existing logical or physical backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97808-152">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备的信息，请参阅[备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97808-152">For information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="97808-153">**备份到**</span><span class="sxs-lookup"><span data-stu-id="97808-153">**Back up to**</span></span>  
 <span data-ttu-id="97808-154">选择以下类型介质之一，作为要备份到的目标。</span><span class="sxs-lookup"><span data-stu-id="97808-154">Select one of the following types of media to which to back up.</span></span> <span data-ttu-id="97808-155">选择的目标将显示在 **“备份到”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="97808-155">The destinations you select appear in the **Back up to** list.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97808-156">**磁盘**</span><span class="sxs-lookup"><span data-stu-id="97808-156">**Disk**</span></span>|<span data-ttu-id="97808-157">备份到磁盘。</span><span class="sxs-lookup"><span data-stu-id="97808-157">Backs up to disk.</span></span> <span data-ttu-id="97808-158">这可能是一个为该数据库创建的系统文件或基于磁盘的逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="97808-158">This may be a system file or a disk-based logical backup device created for the database.</span></span> <span data-ttu-id="97808-159">当前所选的磁盘将显示在 **“备份到”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="97808-159">The currently selected disks appear in the **Back up to** list.</span></span> <span data-ttu-id="97808-160">您最多可以为备份操作选择 64 个磁盘设备。</span><span class="sxs-lookup"><span data-stu-id="97808-160">You can select up to 64 disk devices for your backup operation.</span></span>|  
|<span data-ttu-id="97808-161">**磁带**</span><span class="sxs-lookup"><span data-stu-id="97808-161">**Tape**</span></span>|<span data-ttu-id="97808-162">备份到磁带。</span><span class="sxs-lookup"><span data-stu-id="97808-162">Backs up to tape.</span></span> <span data-ttu-id="97808-163">这可能是一个为该数据库创建的本地磁带机或基于磁带的逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="97808-163">This may be a local tape drive or a tape-based logical backup device created for the database.</span></span> <span data-ttu-id="97808-164">当前所选的磁带将显示在 **“备份到”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="97808-164">The currently selected tapes appear in the **Back up to** list.</span></span> <span data-ttu-id="97808-165">最大数目为 64。</span><span class="sxs-lookup"><span data-stu-id="97808-165">The maximum number is 64.</span></span> <span data-ttu-id="97808-166">如果服务器没有相连的磁带设备，此选项将停用。</span><span class="sxs-lookup"><span data-stu-id="97808-166">If there are no tape devices attached to the server, this option is deactivated.</span></span> <span data-ttu-id="97808-167">您选择的磁带将列在 **“备份到”** 列表中。</span><span class="sxs-lookup"><span data-stu-id="97808-167">The tapes you select are listed in the **Back up to** list.</span></span><br /><br /> <span data-ttu-id="97808-168">注意：在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未来版本中将不再支持磁带备份设备。</span><span class="sxs-lookup"><span data-stu-id="97808-168">Note: Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97808-169">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="97808-169">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>|  
|<span data-ttu-id="97808-170">**URL**</span><span class="sxs-lookup"><span data-stu-id="97808-170">**URL**</span></span>|<span data-ttu-id="97808-171">备份到 Azure Blob 存储。</span><span class="sxs-lookup"><span data-stu-id="97808-171">Backs up to Azure Blob storage.</span></span>|  
  
 <span data-ttu-id="97808-172">显示的下一组选项会取决于所选目标的类型。</span><span class="sxs-lookup"><span data-stu-id="97808-172">The next set of options displayed depends on the type of destination selected.</span></span> <span data-ttu-id="97808-173">如果您选择“磁盘”或“磁带”，则会显示以下选项。</span><span class="sxs-lookup"><span data-stu-id="97808-173">If you select Disk or Tape, the following options are displayed.</span></span>  
  
 <span data-ttu-id="97808-174">**添加**</span><span class="sxs-lookup"><span data-stu-id="97808-174">**Add**</span></span>  
 <span data-ttu-id="97808-175">将文件或设备添加到“备份到”  列表中。</span><span class="sxs-lookup"><span data-stu-id="97808-175">Adds a file or device to the **Back up to** list.</span></span> <span data-ttu-id="97808-176">最多可以同时向本地磁盘或远程磁盘上的 64 个设备进行备份。</span><span class="sxs-lookup"><span data-stu-id="97808-176">You can back up to 64 devices simultaneously on a local disk or remote disk.</span></span> <span data-ttu-id="97808-177">若要指定远程磁盘上的文件，请使用完全限定的通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="97808-177">To specify a file on a remote disk, use the fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="97808-178">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97808-178">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="97808-179">**删除**</span><span class="sxs-lookup"><span data-stu-id="97808-179">**Remove**</span></span>  
 <span data-ttu-id="97808-180">从“备份到”  列表中删除一个或多个当前所选的设备。</span><span class="sxs-lookup"><span data-stu-id="97808-180">Removes one or more currently selected devices from the **Back up to** list.</span></span>  
  
 <span data-ttu-id="97808-181">**Contents**</span><span class="sxs-lookup"><span data-stu-id="97808-181">**Contents**</span></span>  
 <span data-ttu-id="97808-182">显示所选设备的介质内容。</span><span class="sxs-lookup"><span data-stu-id="97808-182">Displays the media contents for the selected device.</span></span>  
  
 <span data-ttu-id="97808-183">如果您选择“URL”作为备份目标，则会显示以下选项：</span><span class="sxs-lookup"><span data-stu-id="97808-183">If you select URL as the backup destination, the following options are displayed:</span></span>  
  
 <span data-ttu-id="97808-184">**文件名**</span><span class="sxs-lookup"><span data-stu-id="97808-184">**File Name**</span></span>  
 <span data-ttu-id="97808-185">指定备份文件的名称。</span><span class="sxs-lookup"><span data-stu-id="97808-185">Specify the name of the backup file.</span></span>  
  
 <span data-ttu-id="97808-186">**SQL 凭据**</span><span class="sxs-lookup"><span data-stu-id="97808-186">**SQL credential**</span></span>  
 <span data-ttu-id="97808-187">选择用于向 Azure 存储进行身份验证的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="97808-187">Select a SQL Credential used to authenticate to  Azure Storage.</span></span> <span data-ttu-id="97808-188">如果没有可使用的现有 SQL 凭据，则单击 **“创建”** 按钮可创建新的 SQL 凭据。</span><span class="sxs-lookup"><span data-stu-id="97808-188">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97808-189">单击 **“创建”** 打开的对话框需要管理证书或订阅的发布配置文件。</span><span class="sxs-lookup"><span data-stu-id="97808-189">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="97808-190">如果您无权访问管理证书或发布配置文件，可以创建一个 SQL 凭据，方法是使用 Transact-SQL 或 SQL Server Management Studio 指定存储帐户名称和访问密钥信息。</span><span class="sxs-lookup"><span data-stu-id="97808-190">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="97808-191">请参阅[创建凭据](../security/authentication-access/create-a-credential.md#Credential)主题中中的示例代码，使用 transact-sql 创建凭据。</span><span class="sxs-lookup"><span data-stu-id="97808-191">See the sample code in the in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="97808-192">或者，使用 SQL Server Management Studio，从数据库引擎实例中右键单击 **“安全性”**，依次选择 **“新建”** 和 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="97808-192">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="97808-193">在 **“标识”** 字段中指定存储帐户名称，在 **“密码”** 字段中指定访问密钥。</span><span class="sxs-lookup"><span data-stu-id="97808-193">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
 <span data-ttu-id="97808-194">**Azure 存储容器**</span><span class="sxs-lookup"><span data-stu-id="97808-194">**Azure storage container**</span></span>  
 <span data-ttu-id="97808-195">指定 Azure 存储容器的名称</span><span class="sxs-lookup"><span data-stu-id="97808-195">Specify the name of the Azure storage container</span></span>  
  
 <span data-ttu-id="97808-196">**URL 前缀：**</span><span class="sxs-lookup"><span data-stu-id="97808-196">**URL prefix:**</span></span>  
 <span data-ttu-id="97808-197">这是基于在 SQL 凭据中存储的存储帐户信息以及您指定的 Azure 存储容器名称自动生成的。</span><span class="sxs-lookup"><span data-stu-id="97808-197">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="97808-198">建议不要编辑此字段中的信息，除非使用的域采用 **\<storage account>.blob.core.windows.net** 以外的格式。</span><span class="sxs-lookup"><span data-stu-id="97808-198">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97808-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97808-199">See Also</span></span>  
 <span data-ttu-id="97808-200">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97808-200">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="97808-201">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97808-201">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="97808-202">[为磁盘文件定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97808-202">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="97808-203">[为磁带驱动器定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97808-203">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="97808-204">恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97808-204">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
