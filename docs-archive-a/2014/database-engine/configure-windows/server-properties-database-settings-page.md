---
title: 服务器属性（“数据库设置”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3beb2b6aa9a34982cccdfb252941c1c779a16121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692513"
---
# <a name="server-properties-database-settings-page"></a><span data-ttu-id="8ef3b-102">服务器属性（“数据库设置”页）</span><span class="sxs-lookup"><span data-stu-id="8ef3b-102">Server Properties (Database Settings Page)</span></span>
  <span data-ttu-id="8ef3b-103">使用此页可以查看或修改数据库设置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-103">Use this page to view or modify your database settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8ef3b-104">选项</span><span class="sxs-lookup"><span data-stu-id="8ef3b-104">Options</span></span>  
 <span data-ttu-id="8ef3b-105">**默认索引填充因子**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-105">**Default index fill factor**</span></span>  
 <span data-ttu-id="8ef3b-106">指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用现有数据创建新索引时对每一页的填充程度。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-106">Specifies how full [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should make each page when it creates a new index using existing data.</span></span> <span data-ttu-id="8ef3b-107">由于在页填充时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须花时间来拆分页，因此填充因子会影响性能。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-107">The fill factor affects performance because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must take time to split pages when they fill up.</span></span>  
  
 <span data-ttu-id="8ef3b-108">默认值为 100。有效值介于 0 和 100 之间。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-108">The default value is 0; valid values range from 0 through 100.</span></span> <span data-ttu-id="8ef3b-109">填充因子值为 0 或 100 时，表示基于完全数据页创建聚集索引，并基于完全叶子页创建非聚集索引，但在索引树的较高级别中预留空间。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-109">A fill factor of 0 or 100 creates clustered indexes with full data pages and nonclustered indexes with full leaf pages, but it leaves some space within the upper level of the index tree.</span></span> <span data-ttu-id="8ef3b-110">填充因子值 0 和 100 在所有方面都是相同的。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-110">Fill factor values 0 and 100 are identical in all respects.</span></span>  
  
 <span data-ttu-id="8ef3b-111">较小的填充因子值将导致 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基于不饱满的页创建索引。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-111">Small fill factor values cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create indexes with pages that are not full.</span></span> <span data-ttu-id="8ef3b-112">每一个索引占用更多的存储空间，但同时也允许以后无需拆分页面即可插入索引。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-112">Each index takes more storage space, but there is more room for subsequent insertions without requiring page splits.</span></span>  
  
 <span data-ttu-id="8ef3b-113">**无限期等待**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-113">**Wait indefinitely**</span></span>  
 <span data-ttu-id="8ef3b-114">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在等待新备份磁带时永不超时。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will never time out while waiting for a new backup tape.</span></span>  
  
 <span data-ttu-id="8ef3b-115">**尝试一次**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-115">**Try once**</span></span>  
 <span data-ttu-id="8ef3b-116">指定如果需要备份磁带但它却不可用，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将超时。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-116">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available when needed.</span></span>  
  
 <span data-ttu-id="8ef3b-117">**尝试的分钟数**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-117">**Try for minute(s)**</span></span>  
 <span data-ttu-id="8ef3b-118">指定如果备份磁带在指定的时间内不可用， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将超时。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-118">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available within the period specified.</span></span>  
  
 <span data-ttu-id="8ef3b-119">**默认备份介质保持期(天)**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-119">**Default backup media retention (in days)**</span></span>  
 <span data-ttu-id="8ef3b-120">提供一个系统范围默认值，指示在用于数据库备份或事务日志备份后每一个备份介质的保留时间。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-120">Provides a system-wide default for the length of time to retain each backup medium after it has been used for a database or transaction log backup.</span></span> <span data-ttu-id="8ef3b-121">此选项可以防止在指定的日期前覆盖备份。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-121">This option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span>  
  
 <span data-ttu-id="8ef3b-122">**压缩备份**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-122">**Compress backup**</span></span>  
 <span data-ttu-id="8ef3b-123">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]（或更高版本）中，指示“backup compression default”选项的当前设置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-123">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), indicates the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="8ef3b-124">此选项决定了用于压缩备份的服务器级默认设置，具体如下：</span><span class="sxs-lookup"><span data-stu-id="8ef3b-124">This option determines the server-level default for compressing backups, as follows:</span></span>  
  
-   <span data-ttu-id="8ef3b-125">如果未选中 **“压缩备份”** 框，在默认情况下将不压缩新备份。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-125">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
-   <span data-ttu-id="8ef3b-126">如果 **“压缩备份”** 框已选中，则默认情况下将压缩新备份。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-126">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8ef3b-127">默认情况下，压缩显著增加 CPU 使用率，并且压缩进程占用的额外 CPU 可能会对并发操作造成不利影响。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-127">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="8ef3b-128">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受 [资源调控器](../../relational-databases/resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-128">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="8ef3b-129">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-129">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="8ef3b-130">如果你是 **sysadmin** 或 **serveradmin** 固定服务器角色的成员，则可以通过单击“压缩备份”  框来更改设置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-130">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can change the setting by clicking the **Compress backup** box.</span></span>  
  
 <span data-ttu-id="8ef3b-131">有关详细信息，请参阅[查看或配置“backup compression default”服务器配置选项](view-or-configure-the-backup-compression-default-server-configuration-option.md)和[备份压缩 (SQL Server)](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-131">For more information, see [View or Configure the backup compression default Server Configuration Option](view-or-configure-the-backup-compression-default-server-configuration-option.md) and [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="8ef3b-132">**恢复间隔(分钟)**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-132">**Recovery interval (minutes)**</span></span>  
 <span data-ttu-id="8ef3b-133">设置每个数据库恢复时所需的最大分钟数。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-133">Sets the maximum number of minutes per database to recover databases.</span></span> <span data-ttu-id="8ef3b-134">默认值为 0，指示由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自动配置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-134">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8ef3b-135">实际上，这表示每个数据库的恢复时间不超过 1 分钟，对于活动的数据库大约每 1 分钟有一个检查点。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-135">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span> <span data-ttu-id="8ef3b-136">有关详细信息，请参阅 [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-136">For more information, see [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="8ef3b-137">**Data**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-137">**Data**</span></span>  
 <span data-ttu-id="8ef3b-138">指定数据文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-138">Specifies the default location for data files.</span></span> <span data-ttu-id="8ef3b-139">单击“浏览”按钮导航到新的默认位置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-139">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="8ef3b-140">直到重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-140">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="8ef3b-141">**日志**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-141">**Log**</span></span>  
 <span data-ttu-id="8ef3b-142">指定日志文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-142">Specifies the default location for log files.</span></span> <span data-ttu-id="8ef3b-143">单击“浏览”按钮导航到新的默认位置。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-143">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="8ef3b-144">直到重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-144">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="8ef3b-145">**配置值**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-145">**Configured Values**</span></span>  
 <span data-ttu-id="8ef3b-146">显示此窗格上选项的配置值。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-146">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="8ef3b-147">如果更改了这些值，请单击 **“运行值”** 以查看更改是否已生效。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-147">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="8ef3b-148">如果尚未生效，则必须首先重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-148">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="8ef3b-149">**“运行值”**</span><span class="sxs-lookup"><span data-stu-id="8ef3b-149">**Running Values**</span></span>  
 <span data-ttu-id="8ef3b-150">查看此窗格上选项的当前运行值。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-150">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="8ef3b-151">这些值是只读的。</span><span class="sxs-lookup"><span data-stu-id="8ef3b-151">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef3b-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ef3b-152">See Also</span></span>  
 <span data-ttu-id="8ef3b-153">[服务器配置选项 (SQL Server)](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ef3b-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="8ef3b-154">为索引指定填充因子</span><span class="sxs-lookup"><span data-stu-id="8ef3b-154">Specify Fill Factor for an Index</span></span>](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
  
