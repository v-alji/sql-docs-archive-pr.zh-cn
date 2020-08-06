---
title: 备份设备（“常规”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578266"
---
# <a name="backup-device-general-page"></a><span data-ttu-id="abad4-102">备份设备（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="abad4-102">Backup Device (General Page)</span></span>
  <span data-ttu-id="abad4-103">使用 **“常规”** 页可指定或查看逻辑备份设备的常规属性。</span><span class="sxs-lookup"><span data-stu-id="abad4-103">Use the **General** page to specify or view the general properties of a logical backup device.</span></span>  
  
 <span data-ttu-id="abad4-104">**使用 SQL Server Management Studio 查看备份设备的内容**</span><span class="sxs-lookup"><span data-stu-id="abad4-104">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="abad4-105">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-105">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="abad4-106">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-106">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="abad4-107">选项</span><span class="sxs-lookup"><span data-stu-id="abad4-107">Options</span></span>  
 <span data-ttu-id="abad4-108">**设备名称**</span><span class="sxs-lookup"><span data-stu-id="abad4-108">**Device name**</span></span>  
 <span data-ttu-id="abad4-109">查看现有逻辑备份设备的名称，或指定新逻辑备份设备的名称。</span><span class="sxs-lookup"><span data-stu-id="abad4-109">View the name of an existing logical backup device or specify the name of a new logical backup device.</span></span>  
  
 <span data-ttu-id="abad4-110">**磁带**</span><span class="sxs-lookup"><span data-stu-id="abad4-110">**Tape**</span></span>  
 <span data-ttu-id="abad4-111">在“磁带”  列表中查看或选择目标磁带设备。</span><span class="sxs-lookup"><span data-stu-id="abad4-111">View or select the destination tape device in the **Tape** list.</span></span> <span data-ttu-id="abad4-112">仅在运行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例的计算机附连有磁带机时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="abad4-112">This option is available only if a tape drive is attached to the computer that is running the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abad4-113">远程计算机中的磁带备份设备不是有效的备份目标。</span><span class="sxs-lookup"><span data-stu-id="abad4-113">Tape backup devices on remote computers are not valid backup destinations.</span></span>  
  
 <span data-ttu-id="abad4-114">**File**</span><span class="sxs-lookup"><span data-stu-id="abad4-114">**File**</span></span>  
 <span data-ttu-id="abad4-115">查看现有逻辑备份设备的目标文件，或指定新逻辑备份设备的目标文件。</span><span class="sxs-lookup"><span data-stu-id="abad4-115">View the destination file of an existing logical backup device, or specify a destination file for a new logical backup device.</span></span>  
  
-   <span data-ttu-id="abad4-116">对于现有的逻辑备份设备，将显示备份文件的路径。</span><span class="sxs-lookup"><span data-stu-id="abad4-116">For an existing logical backup device, the path of the backup file is displayed.</span></span> <span data-ttu-id="abad4-117">**“文件”** 字段不可编辑，“浏览”按钮也不可用。</span><span class="sxs-lookup"><span data-stu-id="abad4-117">The **File** field is not editable, and the Browse button is unavailable.</span></span>  
  
-   <span data-ttu-id="abad4-118">对于新的逻辑备份设备，您必须提供为其定义逻辑备份设备的备份文件的路径。</span><span class="sxs-lookup"><span data-stu-id="abad4-118">For a new logical backup device, you must supply the path of the backup file for which you are defining the logical backup device.</span></span> <span data-ttu-id="abad4-119">此文件并不一定已经存在。</span><span class="sxs-lookup"><span data-stu-id="abad4-119">This file does not have to exist yet.</span></span>  
  
     <span data-ttu-id="abad4-120">若要指定本地备份文件，可以单击 **“文件”** 文本框右侧的“浏览”按钮。</span><span class="sxs-lookup"><span data-stu-id="abad4-120">To specify a local backup file, you can click the Browse button to the right of the **File** text box.</span></span> <span data-ttu-id="abad4-121">然后，在 **“定位数据库文件”** 对话框中，您可以导航到运行服务器实例的计算机中任意固定驱动器上的任意位置。</span><span class="sxs-lookup"><span data-stu-id="abad4-121">Then, in the **Locate Database Files** dialog box, you can navigate to any location on any of the fixed drives on the computer running the server instance.</span></span> <span data-ttu-id="abad4-122">如果备份文件尚不存在，则必须在该对话框的 **“文件名”** 字段中输入要使用的文件名。</span><span class="sxs-lookup"><span data-stu-id="abad4-122">If the backup file does not exist yet, you must enter the filename you want to use in the **File name** field of that dialog box.</span></span>  
  
     <span data-ttu-id="abad4-123">或者，也可以手动编辑 **“文件”** 字段，以覆盖默认路径、文件名和扩展名。</span><span class="sxs-lookup"><span data-stu-id="abad4-123">Alternatively, you can edit the **File** field manually to override the default path, file name, and extension.</span></span> <span data-ttu-id="abad4-124">若要将远程文件指定为备份目标，请输入其完全限定的通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="abad4-124">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="abad4-125">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="abad4-125">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="abad4-126">通过网络备份数据时可能会出现网络错误；因此，建议您在完成备份后验证备份操作。</span><span class="sxs-lookup"><span data-stu-id="abad4-126">Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="abad4-127">有关详细信息，请参阅 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="abad4-127">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abad4-128">备注</span><span class="sxs-lookup"><span data-stu-id="abad4-128">Remarks</span></span>  
 <span data-ttu-id="abad4-129">包含一个或多个备份设备的集合的备份构成一个介质集。</span><span class="sxs-lookup"><span data-stu-id="abad4-129">The backups on a set of one or more backup devices compose a single media set.</span></span> <span data-ttu-id="abad4-130">“介质集”  是“备份介质”（磁带或磁盘文件）的有序集合，使用固定类型和数量的备份设备向其写入一个或多个备份操作。</span><span class="sxs-lookup"><span data-stu-id="abad4-130">A *media set* is an ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="abad4-131">有关媒体集的信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)实例的计算机附连有磁带机时，此选项才可用。</span><span class="sxs-lookup"><span data-stu-id="abad4-131">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="abad4-132">将介质集中的第一个备份写入逻辑备份设备时，将对与逻辑备份设备对应的物理备份设备进行初始化。</span><span class="sxs-lookup"><span data-stu-id="abad4-132">The physical backup device corresponding to a logical backup device is initialized when the first backup in the media set is written to the logical backup device.</span></span> <span data-ttu-id="abad4-133">如果物理备份设备是尚不存在的文件，则此时将创建该文件。</span><span class="sxs-lookup"><span data-stu-id="abad4-133">If the physical backup device is a file that does not exist yet, it is created at that time.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="abad4-134">相关任务</span><span class="sxs-lookup"><span data-stu-id="abad4-134">Related Tasks</span></span>  
  
-   [<span data-ttu-id="abad4-135">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-135">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="abad4-136">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-136">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="abad4-137">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-137">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="abad4-138">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-138">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="abad4-139">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-139">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="abad4-140">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-140">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="abad4-141">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-141">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="abad4-142">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-142">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="abad4-143">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-143">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="abad4-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abad4-144">See Also</span></span>  
 <span data-ttu-id="abad4-145">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="abad4-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="abad4-146">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="abad4-146">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
