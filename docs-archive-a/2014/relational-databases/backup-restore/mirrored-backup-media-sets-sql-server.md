---
title: 镜像备份媒体集 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server], mirrored backups
- mirrored media sets [SQL Server]
- backup mirrors [SQL Server]
- duplicate backup copies
- interchangeable backup copies [SQL Server]
- media sets [SQL Server], mirrored backup media sets
- backup media [SQL Server], mirrored media
ms.assetid: 05a0b8d1-3585-4f77-972f-69d1c0d4aa9b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce3513c67a0087dd00021de75f360b19819b46db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590869"
---
# <a name="mirrored-backup-media-sets-sql-server"></a><span data-ttu-id="63097-102">镜像备份介质集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63097-102">Mirrored Backup Media Sets (SQL Server)</span></span>
    
> [!NOTE]  
>  <span data-ttu-id="63097-103">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Enterprise Edition 支持镜像备份介质集。</span><span class="sxs-lookup"><span data-stu-id="63097-103">Mirrored backup media sets are supported only in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="63097-104">镜像介质集通过降低备份设备故障的影响来提高备份的可靠性。</span><span class="sxs-lookup"><span data-stu-id="63097-104">Mirroring a media set increases backup reliability by reducing the impact of backup-device malfunctions.</span></span> <span data-ttu-id="63097-105">由于备份是防止数据丢失的最后“防线”，因此备份设备出现故障的后果是非常严重的。</span><span class="sxs-lookup"><span data-stu-id="63097-105">These malfunctions are very serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="63097-106">随着数据库大小的增加，备份设备或介质发生故障致使备份不可还原的可能性也相应增加。</span><span class="sxs-lookup"><span data-stu-id="63097-106">As databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="63097-107">镜像备份介质通过提供冗余来提高备份的可靠性。</span><span class="sxs-lookup"><span data-stu-id="63097-107">Mirroring backup media increases the reliability of backups by providing redundancy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="63097-108">有关媒体集的常规信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)Enterprise Edition 支持镜像备份介质集。</span><span class="sxs-lookup"><span data-stu-id="63097-108">For information about media sets in general, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="63097-109">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="63097-109">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="63097-110">镜像介质集概述</span><span class="sxs-lookup"><span data-stu-id="63097-110">Overview of Mirrored Media Sets</span></span>](#OverviewofMirroredMediaSets)  
  
-   [<span data-ttu-id="63097-111">备份镜像的硬件要求</span><span class="sxs-lookup"><span data-stu-id="63097-111">Hardware Requirements for Backup Mirrors</span></span>](#HardwareReqs)  
  
-   [<span data-ttu-id="63097-112">相关任务</span><span class="sxs-lookup"><span data-stu-id="63097-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="overview-of-mirrored-media-sets"></a><a name="OverviewofMirroredMediaSets"></a> <span data-ttu-id="63097-113">镜像介质集概述</span><span class="sxs-lookup"><span data-stu-id="63097-113">Overview of Mirrored Media Sets</span></span>  
 <span data-ttu-id="63097-114">介质镜像是介质集的一个属性。</span><span class="sxs-lookup"><span data-stu-id="63097-114">Media mirroring is a property of the media set.</span></span> <span data-ttu-id="63097-115">*镜像媒体集* 是由媒体集的多个副本（*镜像*）组成的。</span><span class="sxs-lookup"><span data-stu-id="63097-115">A *mirrored media set* consists of multiple copies (*mirrors*) of the media set.</span></span> <span data-ttu-id="63097-116">介质集包含一个或多个介质簇，其中每个介质簇对应一个备份设备。</span><span class="sxs-lookup"><span data-stu-id="63097-116">A media set contains one or more media families, each of which corresponds to a backup device.</span></span> <span data-ttu-id="63097-117">例如，如果 BACKUP DATABASE 语句的 TO 子句列出三个设备，则 BACKUP 将数据分布在三个介质簇中，每个设备一个介质簇。</span><span class="sxs-lookup"><span data-stu-id="63097-117">For example, if the TO clause of a BACKUP DATABASE statement lists three devices, BACKUP spreads the data among three media families, one per device.</span></span> <span data-ttu-id="63097-118">介质簇和镜像的数量在创建介质集时进行定义（使用指定了 WITH FORMAT 的 BACKUP DATABASE 语句）。</span><span class="sxs-lookup"><span data-stu-id="63097-118">The number of media families and mirrors is defined when the media set is created (by a BACKUP DATABASE statement that specifies WITH FORMAT).</span></span>  
  
 <span data-ttu-id="63097-119">一个镜像介质集包含两个到四个镜像。</span><span class="sxs-lookup"><span data-stu-id="63097-119">A mirrored media set possesses from two to four mirrors.</span></span> <span data-ttu-id="63097-120">每个镜像包含介质集中的所有介质簇。</span><span class="sxs-lookup"><span data-stu-id="63097-120">Each mirror contains all the media families in the media set.</span></span> <span data-ttu-id="63097-121">镜像必须有相同的设备数，每个介质簇一个设备。</span><span class="sxs-lookup"><span data-stu-id="63097-121">The mirrors require the same number of devices, one per media family.</span></span> <span data-ttu-id="63097-122">每个镜像要求每个介质簇都有一个单独的备份设备。</span><span class="sxs-lookup"><span data-stu-id="63097-122">Each mirror requires a separate backup device for each media family.</span></span> <span data-ttu-id="63097-123">例如，包含四个介质簇、三个镜像的镜像介质集需要十二个备份设备。</span><span class="sxs-lookup"><span data-stu-id="63097-123">For example, a mirrored media set that consists of four media families with three mirrors requires twelve backup devices.</span></span> <span data-ttu-id="63097-124">所有这些设备必须是相同的。</span><span class="sxs-lookup"><span data-stu-id="63097-124">All of these devices must be equivalent.</span></span> <span data-ttu-id="63097-125">例如，使用同一制造商提供的同一型号的磁带机。</span><span class="sxs-lookup"><span data-stu-id="63097-125">For example, tape drives that have the same model number from the same manufacturer.</span></span>  
  
 <span data-ttu-id="63097-126">下图显示了包含两个介质簇、两个镜像的镜像介质集示例。</span><span class="sxs-lookup"><span data-stu-id="63097-126">The following illustration shows an example of a mirrored media set that consists of two media families with two mirrors.</span></span> <span data-ttu-id="63097-127">每个介质簇都包含三个介质卷，这些介质卷在每个镜像中都备份一次。</span><span class="sxs-lookup"><span data-stu-id="63097-127">Each media family contains three media volumes, which are backed up one time per mirror.</span></span>  
  
 <span data-ttu-id="63097-128">![镜像介质集：具有两个镜像的两个介质簇](../../database-engine/media/bnr-backup-media-mirror.gif "镜像介质集：具有两个镜像的两个介质簇")</span><span class="sxs-lookup"><span data-stu-id="63097-128">![Mirrored media set: two families with two mirrors](../../database-engine/media/bnr-backup-media-mirror.gif "Mirrored media set: two families with two mirrors")</span></span>  
  
 <span data-ttu-id="63097-129">镜像中的对应卷都具有相同的内容。</span><span class="sxs-lookup"><span data-stu-id="63097-129">Corresponding volumes on the mirrors have identical contents.</span></span> <span data-ttu-id="63097-130">这样，还原时它们可以互换。</span><span class="sxs-lookup"><span data-stu-id="63097-130">This makes them interchangeable at restore time.</span></span> <span data-ttu-id="63097-131">例如，在上图中，tape2 的第三卷可以与 tape0 的第三卷互换。</span><span class="sxs-lookup"><span data-stu-id="63097-131">For example, in the previous illustration, the third volume of tape2 is interchangeable with the third volume of tape0.</span></span>  
  
 <span data-ttu-id="63097-132">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 通过将数据同步写入设备来保证镜像介质具有相同的内容。</span><span class="sxs-lookup"><span data-stu-id="63097-132">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] guarantees that the mirrored media have identical contents by synchronizing writes to the devices.</span></span> <span data-ttu-id="63097-133">填充任一镜像时，同时也会填充所有镜像。</span><span class="sxs-lookup"><span data-stu-id="63097-133">When any one of the mirrors fills, all the mirrors are spanned at one time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63097-134">不能通过删除某个镜像来隐性分割（拆分）镜像介质集。</span><span class="sxs-lookup"><span data-stu-id="63097-134">A mirrored media set cannot be implicitly broken (split) by removing a mirror.</span></span> <span data-ttu-id="63097-135">如果某个镜像中磁带或磁盘已损坏或已经过重新格式化，则该镜像不能再用于其他备份。</span><span class="sxs-lookup"><span data-stu-id="63097-135">If any tape or disk in a mirror is damaged or reformatted, the mirror is no longer usable for additional backups.</span></span> <span data-ttu-id="63097-136">至少有一个完整镜像保持完好无损时，才可以读取介质集。</span><span class="sxs-lookup"><span data-stu-id="63097-136">If at least one full mirror remains intact, the media set can be read.</span></span> <span data-ttu-id="63097-137">如果每个镜像都丢失了指定的介质簇，则介质集将不再可用。</span><span class="sxs-lookup"><span data-stu-id="63097-137">If every mirror loses a given media family, the media set is useless.</span></span>  
  
 <span data-ttu-id="63097-138">备份和还原操作对是否必须存在所有镜像有不同的要求。</span><span class="sxs-lookup"><span data-stu-id="63097-138">Backup and restore operations impose different requirements on whether all the mirrors must be present.</span></span> <span data-ttu-id="63097-139">对写入（即创建或扩展）镜像介质集的备份操作，必须存在所有镜像。</span><span class="sxs-lookup"><span data-stu-id="63097-139">For a backup operation to write (that is, to create or extend) a mirrored media set, all the mirrors must be present.</span></span> <span data-ttu-id="63097-140">相反，从镜像介质集中还原备份时，对于每个介质簇，只能指定一个镜像。</span><span class="sxs-lookup"><span data-stu-id="63097-140">In contrast, when you are restoring a backup from a mirrored media set, you can specify only a single mirror for each media family.</span></span> <span data-ttu-id="63097-141">从其进行还原的设备可以少于介质簇，但每个介质簇只能处理一次。</span><span class="sxs-lookup"><span data-stu-id="63097-141">You can restore from fewer devices than families, but each media family is processed only one time.</span></span> <span data-ttu-id="63097-142">不过，在出现错误的情况下，如果具有其他镜像则可快速解决某些还原问题。</span><span class="sxs-lookup"><span data-stu-id="63097-142">In the presence of errors, however, having the other mirrors enables some restore problems to be resolved quickly.</span></span> <span data-ttu-id="63097-143">您可以使用其他镜像服务器中的相应卷替换损坏的介质卷。</span><span class="sxs-lookup"><span data-stu-id="63097-143">You can substitute a damaged media volume with the corresponding volume from another mirror.</span></span> <span data-ttu-id="63097-144">这是因为 RESTORE 和 RESTORE VERIFYONLY 支持使用其他镜像中的相应备份介质卷替换损坏的介质。</span><span class="sxs-lookup"><span data-stu-id="63097-144">This is because RESTORE and RESTORE VERIFYONLY support substitution of damaged media with the corresponding backup-media volume from another mirror.</span></span>  
  
##  <a name="hardware-requirements-for-backup-mirrors"></a><a name="HardwareReqs"></a> <span data-ttu-id="63097-145">备份镜像的硬件要求</span><span class="sxs-lookup"><span data-stu-id="63097-145">Hardware Requirements for Backup Mirrors</span></span>  
 <span data-ttu-id="63097-146">磁盘和磁带可作为备份镜像的设备（磁盘不支持延续磁带）。</span><span class="sxs-lookup"><span data-stu-id="63097-146">Mirroring applies both to disk and tape (disks do not support continuation tapes).</span></span> <span data-ttu-id="63097-147">用于单个备份或还原操作的所有备份设备的类型必须相同（磁盘或磁带）。</span><span class="sxs-lookup"><span data-stu-id="63097-147">All backup devices for a single backup or restore operation must be of the same type, disk or tape.</span></span>  
  
 <span data-ttu-id="63097-148">在这些广泛的设备类别中，必须使用具有相同属性的相似设备。</span><span class="sxs-lookup"><span data-stu-id="63097-148">Within these broader classes, you must use similar devices that have the same properties.</span></span> <span data-ttu-id="63097-149">设备不够相似会生成错误消息 (3212)。</span><span class="sxs-lookup"><span data-stu-id="63097-149">Insufficiently similar devices generate an error message (3212).</span></span> <span data-ttu-id="63097-150">为了避免出现设备不匹配的情况，请使用相同的设备，例如，只使用同一制造商提供的同一型号的设备。</span><span class="sxs-lookup"><span data-stu-id="63097-150">To avoid the risk of a device mismatch, use devices that are equivalent, such as, only drives with the same model number from the same manufacturer.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="63097-151">相关任务</span><span class="sxs-lookup"><span data-stu-id="63097-151">Related Tasks</span></span>  
 <span data-ttu-id="63097-152">**备份至镜像备份设备**</span><span class="sxs-lookup"><span data-stu-id="63097-152">**To back up to mirrored backup devices**</span></span>  
  
-   [<span data-ttu-id="63097-153">备份至镜像媒体集 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="63097-153">Back Up to a Mirrored Media Set &#40;Transact-SQL&#41;</span></span>](back-up-to-a-mirrored-media-set-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="63097-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63097-154">See Also</span></span>  
 <span data-ttu-id="63097-155">[备份和还原期间可能出现的媒体错误 (SQL Server)](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63097-155">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 <span data-ttu-id="63097-156">[RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="63097-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="63097-157">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="63097-157">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="63097-158">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="63097-158">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
