---
title: 备份设备（“介质内容”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.contents.f1
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07204b5e05ce9fc17e6ea23450066f9f58b7cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587433"
---
# <a name="backup-device-media-contents-page"></a><span data-ttu-id="5143b-102">备份设备（“介质内容”页）</span><span class="sxs-lookup"><span data-stu-id="5143b-102">Backup Device (Media Contents Page)</span></span>
  <span data-ttu-id="5143b-103">使用 **“备份设备”** 对话框可以查看备份信息。</span><span class="sxs-lookup"><span data-stu-id="5143b-103">Use the **Backup Device** dialog box to view the backup information.</span></span> <span data-ttu-id="5143b-104">此信息描述设备、介质、介质集以及备份集。</span><span class="sxs-lookup"><span data-stu-id="5143b-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="5143b-105">**使用 SQL Server Management Studio 查看备份设备的内容**</span><span class="sxs-lookup"><span data-stu-id="5143b-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="5143b-106">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="5143b-107">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="5143b-108">选项</span><span class="sxs-lookup"><span data-stu-id="5143b-108">Options</span></span>  
 <span data-ttu-id="5143b-109">查看有关各个介质、介质集和备份集的信息。</span><span class="sxs-lookup"><span data-stu-id="5143b-109">View information about the individual media, media set, and backup sets.</span></span>  
  
 <span data-ttu-id="5143b-110">**介质**</span><span class="sxs-lookup"><span data-stu-id="5143b-110">**Media**</span></span>  
 <span data-ttu-id="5143b-111">存储备份信息的磁盘或磁带集。</span><span class="sxs-lookup"><span data-stu-id="5143b-111">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="5143b-112">**介质顺序**</span><span class="sxs-lookup"><span data-stu-id="5143b-112">**Media sequence**</span></span>  
 <span data-ttu-id="5143b-113">列出介质序列号、簇序列号以及镜像标识符（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="5143b-113">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="5143b-114">每个物理备份介质都标记有介质序列号，表示介质的使用顺序。</span><span class="sxs-lookup"><span data-stu-id="5143b-114">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="5143b-115">第一个备份介质的标记为 1，第二个介质（第一个延续磁带）的标记为 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="5143b-115">The initial backup media is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="5143b-116">在还原备份集时，还原备份的操作员根据介质序列号可以确保按正确的顺序装入介质。</span><span class="sxs-lookup"><span data-stu-id="5143b-116">When the backup set is restored, the media sequence numbers ensure that the operator restoring the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="5143b-117">**创建时间**</span><span class="sxs-lookup"><span data-stu-id="5143b-117">**Created on**</span></span>  
 <span data-ttu-id="5143b-118">显示介质集的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="5143b-118">Displays the creation date and time of the media set.</span></span>  
  
 <span data-ttu-id="5143b-119">**介质集**</span><span class="sxs-lookup"><span data-stu-id="5143b-119">**Media Set**</span></span>  
 <span data-ttu-id="5143b-120">介质集是通过使用一定数量的备份设备写入一个或多个备份操作的备份介质的有序集合。</span><span class="sxs-lookup"><span data-stu-id="5143b-120">A media set is an ordered collection of backup media to which one or more backup operations have written by using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="5143b-121">**名称**</span><span class="sxs-lookup"><span data-stu-id="5143b-121">**Name**</span></span>  
 <span data-ttu-id="5143b-122">显示介质集的名称（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="5143b-122">Displays the name of the media set, if any.</span></span>  
  
 <span data-ttu-id="5143b-123">**说明**</span><span class="sxs-lookup"><span data-stu-id="5143b-123">**Description**</span></span>  
 <span data-ttu-id="5143b-124">显示介质集的说明（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="5143b-124">Displays the description of the media set, if any.</span></span>  
  
 <span data-ttu-id="5143b-125">**介质簇计数**</span><span class="sxs-lookup"><span data-stu-id="5143b-125">**Media family count**</span></span>  
 <span data-ttu-id="5143b-126">显示介质集中的簇数。</span><span class="sxs-lookup"><span data-stu-id="5143b-126">Displays the number of families in the media set.</span></span> <span data-ttu-id="5143b-127">每个介质集都是一个或多个介质簇的集合。</span><span class="sxs-lookup"><span data-stu-id="5143b-127">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="5143b-128">对给定单个备份设备（或镜像备份设备组）的所有输出形成单个介质簇。</span><span class="sxs-lookup"><span data-stu-id="5143b-128">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="5143b-129">每个介质集对于一个单独设备（或镜像设备组）包含一个介质簇；例如，如果介质集使用两个非镜像备份设备，则介质集包含两个介质簇。</span><span class="sxs-lookup"><span data-stu-id="5143b-129">Each media set contains one media family per separate device (or group of mirrored devices); for instance, if a media set uses two non-mirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="5143b-130">**备份集**</span><span class="sxs-lookup"><span data-stu-id="5143b-130">**Backup sets**</span></span>  
 <span data-ttu-id="5143b-131">显示介质上包含的备份集的有关信息。</span><span class="sxs-lookup"><span data-stu-id="5143b-131">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="5143b-132">备份集是成功备份操作的结果，其内容分布于相应的一组备份设备上的介质中。</span><span class="sxs-lookup"><span data-stu-id="5143b-132">A backup set is the result of a successful backup operation, whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="5143b-133">标头</span><span class="sxs-lookup"><span data-stu-id="5143b-133">Header</span></span>|<span data-ttu-id="5143b-134">值</span><span class="sxs-lookup"><span data-stu-id="5143b-134">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="5143b-135">**名称**</span><span class="sxs-lookup"><span data-stu-id="5143b-135">**Name**</span></span>|<span data-ttu-id="5143b-136">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="5143b-136">The name of the backup set.</span></span>|  
|<span data-ttu-id="5143b-137">类型</span><span class="sxs-lookup"><span data-stu-id="5143b-137">**Type**</span></span>|<span data-ttu-id="5143b-138">备份对象：数据库、文件或 \<blank>（对于事务日志）。</span><span class="sxs-lookup"><span data-stu-id="5143b-138">The backed-up object: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="5143b-139">组件</span><span class="sxs-lookup"><span data-stu-id="5143b-139">**Component**</span></span>|<span data-ttu-id="5143b-140">执行的备份类型：“完整”、“差异”或“事务日志”。</span><span class="sxs-lookup"><span data-stu-id="5143b-140">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="5143b-141">**Server**</span><span class="sxs-lookup"><span data-stu-id="5143b-141">**Server**</span></span>|<span data-ttu-id="5143b-142">执行备份操作的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例名。</span><span class="sxs-lookup"><span data-stu-id="5143b-142">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="5143b-143">**Database**</span><span class="sxs-lookup"><span data-stu-id="5143b-143">**Database**</span></span>|<span data-ttu-id="5143b-144">已备份数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="5143b-144">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="5143b-145">**位置**</span><span class="sxs-lookup"><span data-stu-id="5143b-145">**Position**</span></span>|<span data-ttu-id="5143b-146">备份集在卷中的位置。</span><span class="sxs-lookup"><span data-stu-id="5143b-146">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="5143b-147">**Date**</span><span class="sxs-lookup"><span data-stu-id="5143b-147">**Date**</span></span>|<span data-ttu-id="5143b-148">备份操作完成的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="5143b-148">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="5143b-149">**大小**</span><span class="sxs-lookup"><span data-stu-id="5143b-149">**Size**</span></span>|<span data-ttu-id="5143b-150">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="5143b-150">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="5143b-151">**用户名**</span><span class="sxs-lookup"><span data-stu-id="5143b-151">**User Name**</span></span>|<span data-ttu-id="5143b-152">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="5143b-152">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="5143b-153">**过期日期**</span><span class="sxs-lookup"><span data-stu-id="5143b-153">**Expiration**</span></span>|<span data-ttu-id="5143b-154">备份集的过期日期和时间。</span><span class="sxs-lookup"><span data-stu-id="5143b-154">The date and time the backup set expires.</span></span>|  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5143b-155">相关任务</span><span class="sxs-lookup"><span data-stu-id="5143b-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="5143b-156">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-156">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="5143b-157">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-157">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="5143b-158">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-158">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="5143b-159">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-159">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="5143b-160">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-160">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="5143b-161">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-161">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="5143b-162">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-162">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="5143b-163">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-163">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="5143b-164">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-164">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="5143b-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5143b-165">See Also</span></span>  
 <span data-ttu-id="5143b-166">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5143b-166">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="5143b-167">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5143b-167">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
