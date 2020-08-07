---
title: 选择备份目标 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ffd1d2529dd13e42689bcf168c972d757fb5499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589149"
---
# <a name="select-backup-destination"></a><span data-ttu-id="e3c0d-102">选择备份目标</span><span class="sxs-lookup"><span data-stu-id="e3c0d-102">Select Backup Destination</span></span>
  <span data-ttu-id="e3c0d-103">使用 **“选择备份目标”** 对话框可以选择一个设备作为备份目标。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-103">Use the **Select Backup Destination** dialog box to select a device as your backup destination.</span></span> <span data-ttu-id="e3c0d-104">备份目标可以是磁盘，也可以是逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-104">A backup destination can be either a disk or a logical backup device.</span></span>  
  
 <span data-ttu-id="e3c0d-105">**使用 SQL Server Management Studio 备份数据库**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-105">**To use SQL Server Management Studio to back up a database**</span></span>  
  
-   [<span data-ttu-id="e3c0d-106">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e3c0d-106">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="e3c0d-107">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e3c0d-107">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="e3c0d-108">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e3c0d-108">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="e3c0d-109">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e3c0d-109">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="e3c0d-110">选项</span><span class="sxs-lookup"><span data-stu-id="e3c0d-110">Options</span></span>  
 <span data-ttu-id="e3c0d-111">此对话框中的选项取决于所选目标是位于磁盘上还是位于磁带上。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-111">The options of this dialog box depend on whether you are selecting a destination on disk or on tape.</span></span>  
  
 <span data-ttu-id="e3c0d-112">**磁盘上的目标**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-112">**Destination on disk**</span></span>  
 <span data-ttu-id="e3c0d-113">若要指定备份目标，请选择下列选项之一。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-113">To specify a backup destination, choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3c0d-114">**文件名**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-114">**File name**</span></span>|<span data-ttu-id="e3c0d-115">选择此选项，以在文本框中输入作为备份目标的本地文件或远程文件。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-115">Choose this option to enter a local or remote file as the backup destination in the text box.</span></span><br /><br /> <span data-ttu-id="e3c0d-116">若要指定本地文件，请单击文本框右侧的 "浏览" 按钮并导航到运行服务器的计算机上固定驱动器上的文件，或者直接输入完整路径和文件名。例如， `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak` 。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-116">To specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.</span></span><br /><br /> <span data-ttu-id="e3c0d-117">若要将远程文件指定为备份目标，请输入其完全限定的通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-117">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="e3c0d-118">有关详细信息，请参阅 [备份设备 (SQL Server)](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-118">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span><br /><br /> <span data-ttu-id="e3c0d-119">**\*\* 重要说明 \*\*** 通过网络备份数据时可能会出现网络错误；因此，建议你在完成备份后验证备份操作。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-119">**\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="e3c0d-120">有关详细信息，请参阅 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-120">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>|  
|<span data-ttu-id="e3c0d-121">**备份设备**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-121">**Backup device**</span></span>|<span data-ttu-id="e3c0d-122">选择此选项以选择逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-122">Choose this option to select a logical backup device.</span></span><br /><br /> <span data-ttu-id="e3c0d-123">注意：有关如何创建磁盘备份设备的详细信息，请参阅[为磁盘文件定义逻辑备份设备 (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-123">Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).</span></span>|  
  
 <span data-ttu-id="e3c0d-124">**磁带上的目标**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-124">**Destination on tape**</span></span>  
 <span data-ttu-id="e3c0d-125">在与运行服务器（即 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例）的计算机建立了物理连接的磁带机上指定备份目标。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-125">Specify a backup destination on a tape drive physically connected to the computer running the server (that is, the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]).</span></span> <span data-ttu-id="e3c0d-126">选择以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e3c0d-126">Choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3c0d-127">**磁带机**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-127">**Tape drive**</span></span>|<span data-ttu-id="e3c0d-128">选择此选项，以从与运行服务器实例的计算机建立了物理连接的磁带机列表中选择磁带机作为备份目标。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-128">Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="e3c0d-129">注意：远程计算机中的磁带备份设备不是有效的备份目标。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-129">Note: Tape backup devices on remote computers are not valid backup destinations.</span></span>|  
|<span data-ttu-id="e3c0d-130">**备份设备**</span><span class="sxs-lookup"><span data-stu-id="e3c0d-130">**Backup device**</span></span>|<span data-ttu-id="e3c0d-131">选择此选项以选择现有的逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-131">Choose this option to select an existing logical backup device.</span></span> <span data-ttu-id="e3c0d-132">这些逻辑备份设备对应于与运行服务器实例的计算机建立了物理连接的磁带机。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-132">These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="e3c0d-133">注意：有关如何创建磁带备份设备的详细信息，请参阅[为磁带驱动器定义逻辑备份设备 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c0d-133">Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3c0d-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3c0d-134">See Also</span></span>  
 <span data-ttu-id="e3c0d-135">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3c0d-135">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="e3c0d-136">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e3c0d-136">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
