---
title: 备份数据库（“备份选项”页）| Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ffd527ba4334244c7fd4c5d4a73099093cb8520b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591432"
---
# <a name="back-up-database-backup-options-page"></a><span data-ttu-id="df476-102">备份数据库（“备份选项”页）</span><span class="sxs-lookup"><span data-stu-id="df476-102">Back Up Database (Backup Options Page)</span></span>
  <span data-ttu-id="df476-103">使用  **“备份数据库”** 对话框的 **“备份选项”** 页可以查看或修改数据库备份选项。</span><span class="sxs-lookup"><span data-stu-id="df476-103">Use the  **Backup Options** page of the **Back Up Database** dialog box to view or modify database backup options.</span></span>  
  
 <span data-ttu-id="df476-104">**使用 SQL Server Management Studio 创建备份**</span><span class="sxs-lookup"><span data-stu-id="df476-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="df476-105">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df476-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="df476-106">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df476-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="df476-107">可以定义用于创建数据库备份的数据库维护计划。</span><span class="sxs-lookup"><span data-stu-id="df476-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="df476-108">有关详细信息，请参阅[维护计划](../maintenance-plans/maintenance-plans.md)和[使用维护计划向导](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="df476-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df476-109">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定备份任务时，可以通过单击“脚本”  按钮，再为脚本选择一个目标，生成对应的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 脚本。</span><span class="sxs-lookup"><span data-stu-id="df476-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df476-110">选项</span><span class="sxs-lookup"><span data-stu-id="df476-110">Options</span></span>  
  
### <a name="backup-set"></a><span data-ttu-id="df476-111">备份集</span><span class="sxs-lookup"><span data-stu-id="df476-111">Backup set</span></span>  
 <span data-ttu-id="df476-112">**“备份集”** 面板中的选项允许您指定有关备份操作所创建的备份集的可选信息。</span><span class="sxs-lookup"><span data-stu-id="df476-112">The options of the **Backup set** panel allow for you to specify optional information about the backup set created by the back up operation.</span></span>  
  
 <span data-ttu-id="df476-113">**名称**</span><span class="sxs-lookup"><span data-stu-id="df476-113">**Name**</span></span>  
 <span data-ttu-id="df476-114">指定备份集名称。</span><span class="sxs-lookup"><span data-stu-id="df476-114">Specify the backup set name.</span></span> <span data-ttu-id="df476-115">系统将根据数据库名称和备份类型自动建议一个默认名称。</span><span class="sxs-lookup"><span data-stu-id="df476-115">The system automatically suggests a default name based on the database name and the backup type.</span></span>  
  
 <span data-ttu-id="df476-116">有关备份集的信息，请参阅[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df476-116">For information about backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="df476-117">**说明**</span><span class="sxs-lookup"><span data-stu-id="df476-117">**Description**</span></span>  
 <span data-ttu-id="df476-118">输入备份集的说明。</span><span class="sxs-lookup"><span data-stu-id="df476-118">Enter a description of the backup set.</span></span>  
  
 <span data-ttu-id="df476-119">**备份集过期时间**</span><span class="sxs-lookup"><span data-stu-id="df476-119">**Backup set will expire**</span></span>  
 <span data-ttu-id="df476-120">选择以下过期选项之一：</span><span class="sxs-lookup"><span data-stu-id="df476-120">Choose one of the following expiration options.</span></span> <span data-ttu-id="df476-121">如果选择 **“URL”** 作为备份目标，则禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="df476-121">This option is disabled if **URL** is chosen as the backup destination.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="df476-122">**之后**</span><span class="sxs-lookup"><span data-stu-id="df476-122">**After**</span></span>|<span data-ttu-id="df476-123">指定在多少天后此备份集才会过期，从而可被覆盖。</span><span class="sxs-lookup"><span data-stu-id="df476-123">Specify the number of days that must elapse before this backup set expires and can be overwritten.</span></span> <span data-ttu-id="df476-124">此值范围为 0 到 99999 天；0 天表示备份集将永不过期。</span><span class="sxs-lookup"><span data-stu-id="df476-124">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span><br /><br /> <span data-ttu-id="df476-125">备份过期时间的默认值是在“默认备份介质保持期(天)”  选项中设置的值。</span><span class="sxs-lookup"><span data-stu-id="df476-125">The default value for backup expiration is the value set in the **Default backup media retention (in days)** option.</span></span> <span data-ttu-id="df476-126">若要访问此选项，请在对象资源管理器中右键单击服务器名称，再选择  “属性”；然后，单击  “服务器属性”对话框的  “数据库设置”页。</span><span class="sxs-lookup"><span data-stu-id="df476-126">To access this, right-click the server name in Object Explorer and select **Properties**; then click the **Database Settings** page of the **Server Properties** dialog box.</span></span>|  
|<span data-ttu-id="df476-127">**On**</span><span class="sxs-lookup"><span data-stu-id="df476-127">**On**</span></span>|<span data-ttu-id="df476-128">指定备份集过期从而可被覆盖的具体日期。</span><span class="sxs-lookup"><span data-stu-id="df476-128">Specify a specific date when the backup set expires and can be overwritten.</span></span>|  
  
### <a name="compression"></a><span data-ttu-id="df476-129">压缩</span><span class="sxs-lookup"><span data-stu-id="df476-129">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="df476-130">（或更高版本）支持 [备份压缩](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="df476-130">(or a later version) supports [backup compression](backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="df476-131">**设置备份压缩**</span><span class="sxs-lookup"><span data-stu-id="df476-131">**Set backup compression**</span></span>  
 <span data-ttu-id="df476-132">在 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] （或更高版本）中，选择以下备份压缩值之一：</span><span class="sxs-lookup"><span data-stu-id="df476-132">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (or a later version), select one of the following backup compression values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="df476-133">**使用默认服务器设置**</span><span class="sxs-lookup"><span data-stu-id="df476-133">**Use the default server setting**</span></span>|<span data-ttu-id="df476-134">单击此选项可使用服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="df476-134">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="df476-135">此默认值可通过 **backup compression default** 服务器配置选项进行设置。</span><span class="sxs-lookup"><span data-stu-id="df476-135">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="df476-136">有关如何查看此选项当前设置的信息，请参阅 [查看或配置 backup compression default 服务器配置选项](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="df476-136">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="df476-137">**压缩备份**</span><span class="sxs-lookup"><span data-stu-id="df476-137">**Compress backup**</span></span>|<span data-ttu-id="df476-138">单击此选项可压缩备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="df476-138">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="df476-139">**\*\* 重要提示 \*\*** 默认情况下，压缩会大大提高 CPU 使用率，但压缩进程占用的额外 CPU 可能会对并发操作造成不利影响。</span><span class="sxs-lookup"><span data-stu-id="df476-139">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="df476-140">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受 [资源调控器](../resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="df476-140">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="df476-141">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="df476-141">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="df476-142">**不压缩备份**</span><span class="sxs-lookup"><span data-stu-id="df476-142">**Do not compress backup**</span></span>|<span data-ttu-id="df476-143">单击此选项可创建未压缩的备份，而不考虑服务器级别默认值。</span><span class="sxs-lookup"><span data-stu-id="df476-143">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
### <a name="encryption"></a><span data-ttu-id="df476-144">加密</span><span class="sxs-lookup"><span data-stu-id="df476-144">Encryption</span></span>  
 <span data-ttu-id="df476-145">若要创建加密的备份，请选中 **“加密备份”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="df476-145">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="df476-146">选择要用于加密步骤的加密算法，然后从现有证书或非对称密钥的列表中提供一个证书或非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="df476-146">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="df476-147">可用于加密的算法是：</span><span class="sxs-lookup"><span data-stu-id="df476-147">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="df476-148">AES 128</span><span class="sxs-lookup"><span data-stu-id="df476-148">AES 128</span></span>  
  
-   <span data-ttu-id="df476-149">AES 192</span><span class="sxs-lookup"><span data-stu-id="df476-149">AES 192</span></span>  
  
-   <span data-ttu-id="df476-150">AES 256</span><span class="sxs-lookup"><span data-stu-id="df476-150">AES 256</span></span>  
  
-   <span data-ttu-id="df476-151">三重 DES</span><span class="sxs-lookup"><span data-stu-id="df476-151">Triple DES</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="df476-152">如果您选择了追加到现有备份集，则禁用加密选项。</span><span class="sxs-lookup"><span data-stu-id="df476-152">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
>   
>  <span data-ttu-id="df476-153">建议做法是备份证书或密钥，而存储它们的位置要与所加密的备份不同。</span><span class="sxs-lookup"><span data-stu-id="df476-153">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
>   
>  <span data-ttu-id="df476-154">仅支持位于可扩展密钥管理 (EKM) 中的密钥。</span><span class="sxs-lookup"><span data-stu-id="df476-154">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df476-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="df476-155">See Also</span></span>  
 <span data-ttu-id="df476-156">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="df476-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="df476-157">[备份事务日志 (SQL Server)](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df476-157">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="df476-158">[备份文件和文件组 (SQL Server)](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df476-158">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="df476-159">在数据库损坏时备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df476-159">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
