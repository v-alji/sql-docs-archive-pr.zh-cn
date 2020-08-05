---
title: 设备内容 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c904718eca671b1965a95d0d400f3f6fa075b500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581328"
---
# <a name="device-contents-sql-server"></a><span data-ttu-id="40fed-102">设备内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40fed-102">Device Contents (SQL Server)</span></span>
  <span data-ttu-id="40fed-103">使用此对话框可以查看备份信息。</span><span class="sxs-lookup"><span data-stu-id="40fed-103">Use this dialog box to view the backup information.</span></span> <span data-ttu-id="40fed-104">此信息描述设备、介质、介质集以及备份集。</span><span class="sxs-lookup"><span data-stu-id="40fed-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="40fed-105">**使用 SQL Server Management Studio 查看备份设备的内容**</span><span class="sxs-lookup"><span data-stu-id="40fed-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="40fed-106">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40fed-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="40fed-107">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40fed-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="40fed-108">选项</span><span class="sxs-lookup"><span data-stu-id="40fed-108">Options</span></span>  
 <span data-ttu-id="40fed-109">**介质**</span><span class="sxs-lookup"><span data-stu-id="40fed-109">**Media**</span></span>  
 <span data-ttu-id="40fed-110">存储备份信息的磁盘或磁带集。</span><span class="sxs-lookup"><span data-stu-id="40fed-110">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="40fed-111">**介质顺序**</span><span class="sxs-lookup"><span data-stu-id="40fed-111">**Media sequence**</span></span>  
 <span data-ttu-id="40fed-112">列出介质序列号、簇序列号以及镜像标识符（如果有的话）。</span><span class="sxs-lookup"><span data-stu-id="40fed-112">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="40fed-113">每个物理备份介质都标记有介质序列号，表示介质的使用顺序。</span><span class="sxs-lookup"><span data-stu-id="40fed-113">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="40fed-114">第一个备份介质的标记为 1，第二个介质（第一个延续磁带）的标记为 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="40fed-114">The initial backup medium is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="40fed-115">在还原备份集时，还原备份的操作员根据介质序列号可以确保按正确的顺序装入介质。</span><span class="sxs-lookup"><span data-stu-id="40fed-115">When the backup set is restored, the media sequence numbers ensure that the operator that restores the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="40fed-116">**创建时间**</span><span class="sxs-lookup"><span data-stu-id="40fed-116">**Created on**</span></span>  
 <span data-ttu-id="40fed-117">显示介质日期。</span><span class="sxs-lookup"><span data-stu-id="40fed-117">Displays the media date.</span></span>  
  
 <span data-ttu-id="40fed-118">**介质集**</span><span class="sxs-lookup"><span data-stu-id="40fed-118">**Media Set**</span></span>  
 <span data-ttu-id="40fed-119">介质集是通过使用一定数量的备份设备写入一个或多个备份操作的备份介质的有序集合。</span><span class="sxs-lookup"><span data-stu-id="40fed-119">A media set is an ordered collection of backup media to which one or more backup operations have written using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="40fed-120">**名称**</span><span class="sxs-lookup"><span data-stu-id="40fed-120">**Name**</span></span>  
 <span data-ttu-id="40fed-121">显示介质集的名称。</span><span class="sxs-lookup"><span data-stu-id="40fed-121">Displays the name of the media set.</span></span>  
  
 <span data-ttu-id="40fed-122">**说明**</span><span class="sxs-lookup"><span data-stu-id="40fed-122">**Description**</span></span>  
 <span data-ttu-id="40fed-123">显示介质集的说明。</span><span class="sxs-lookup"><span data-stu-id="40fed-123">Displays the description media set.</span></span>  
  
 <span data-ttu-id="40fed-124">**介质簇计数**</span><span class="sxs-lookup"><span data-stu-id="40fed-124">**Media family count**</span></span>  
 <span data-ttu-id="40fed-125">显示介质簇计数。</span><span class="sxs-lookup"><span data-stu-id="40fed-125">Displays the media family count.</span></span> <span data-ttu-id="40fed-126">每个介质集都是一个或多个介质簇的集合。</span><span class="sxs-lookup"><span data-stu-id="40fed-126">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="40fed-127">对给定单个备份设备（或镜像备份设备组）的所有输出形成单个介质簇。</span><span class="sxs-lookup"><span data-stu-id="40fed-127">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="40fed-128">每个介质集对于一个单独设备（或镜像设备组）包含一个介质簇；例如，如果介质集使用两个非镜像备份设备，则介质集包含两个介质簇。</span><span class="sxs-lookup"><span data-stu-id="40fed-128">Each media set contains one media family per separate device (or group of mirrored devices); for example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="40fed-129">**备份集**</span><span class="sxs-lookup"><span data-stu-id="40fed-129">**Backup sets**</span></span>  
 <span data-ttu-id="40fed-130">显示介质上包含的备份集的有关信息。</span><span class="sxs-lookup"><span data-stu-id="40fed-130">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="40fed-131">备份集是成功备份操作的结果，其内容分布于相应的一组备份设备上的介质中。</span><span class="sxs-lookup"><span data-stu-id="40fed-131">A backup set is the result of a successful backup operation whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="40fed-132">标头</span><span class="sxs-lookup"><span data-stu-id="40fed-132">Header</span></span>|<span data-ttu-id="40fed-133">值</span><span class="sxs-lookup"><span data-stu-id="40fed-133">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="40fed-134">**名称**</span><span class="sxs-lookup"><span data-stu-id="40fed-134">**Name**</span></span>|<span data-ttu-id="40fed-135">备份集的名称。</span><span class="sxs-lookup"><span data-stu-id="40fed-135">The name of the backup set.</span></span>|  
|<span data-ttu-id="40fed-136">类型</span><span class="sxs-lookup"><span data-stu-id="40fed-136">**Type**</span></span>|<span data-ttu-id="40fed-137">执行的备份类型：“完整”、“差异”或“事务日志”。</span><span class="sxs-lookup"><span data-stu-id="40fed-137">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="40fed-138">组件</span><span class="sxs-lookup"><span data-stu-id="40fed-138">**Component**</span></span>|<span data-ttu-id="40fed-139">备份组件：数据库、文件或 \<blank>（对于事务日志）。</span><span class="sxs-lookup"><span data-stu-id="40fed-139">The backed-up component: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="40fed-140">**Server**</span><span class="sxs-lookup"><span data-stu-id="40fed-140">**Server**</span></span>|<span data-ttu-id="40fed-141">执行备份操作的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例名。</span><span class="sxs-lookup"><span data-stu-id="40fed-141">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="40fed-142">**Database**</span><span class="sxs-lookup"><span data-stu-id="40fed-142">**Database**</span></span>|<span data-ttu-id="40fed-143">已备份数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="40fed-143">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="40fed-144">**位置**</span><span class="sxs-lookup"><span data-stu-id="40fed-144">**Position**</span></span>|<span data-ttu-id="40fed-145">备份集在卷中的位置。</span><span class="sxs-lookup"><span data-stu-id="40fed-145">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="40fed-146">**Date**</span><span class="sxs-lookup"><span data-stu-id="40fed-146">**Date**</span></span>|<span data-ttu-id="40fed-147">备份操作完成的日期和时间，按客户端的区域设置显示。</span><span class="sxs-lookup"><span data-stu-id="40fed-147">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="40fed-148">**大小**</span><span class="sxs-lookup"><span data-stu-id="40fed-148">**Size**</span></span>|<span data-ttu-id="40fed-149">备份集的大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="40fed-149">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="40fed-150">**用户名**</span><span class="sxs-lookup"><span data-stu-id="40fed-150">**User Name**</span></span>|<span data-ttu-id="40fed-151">执行备份操作的用户的名称。</span><span class="sxs-lookup"><span data-stu-id="40fed-151">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="40fed-152">**过期日期**</span><span class="sxs-lookup"><span data-stu-id="40fed-152">**Expiration**</span></span>|<span data-ttu-id="40fed-153">备份集的过期日期和时间。</span><span class="sxs-lookup"><span data-stu-id="40fed-153">The date and time the backup set expires.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40fed-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40fed-154">See Also</span></span>  
 [<span data-ttu-id="40fed-155">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="40fed-155">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
