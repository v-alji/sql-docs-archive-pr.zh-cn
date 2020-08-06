---
title: 媒体集、媒体簇和备份集 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media sets [SQL Server], about media sets
- backup media [SQL Server], about backup media
- backups [SQL Server], media sets
- media sets [SQL Server]
- media headers [SQL Server]
- backup sets [SQL Server], about backup sets
- backup media [SQL Server], media sets
- backups [SQL Server], media families
- backup media [SQL Server], media families
- media families [SQL Server]
- backups [SQL Server], backup sets
- backup sets [SQL Server]
ms.assetid: 2b8f19a2-ee9d-4120-b194-fbcd2076a489
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 853451ea5a7c43cd073fdf75703b3c4651b442d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589183"
---
# <a name="media-sets-media-families-and-backup-sets-sql-server"></a><span data-ttu-id="9e5ae-102">介质集、介质簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-102">Media Sets, Media Families, and Backup Sets (SQL Server)</span></span>
  <span data-ttu-id="9e5ae-103">本主题介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原的基本备份介质术语，适用于对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-103">This topic introduces the basic backup-media terminology of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore and is intended for readers who are new to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e5ae-104">本主题介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用于备份介质的格式、备份介质和备份设备之间的对应关系、备份介质上备份的组织结构，以及介质集和介质簇的若干注意事项。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-104">This topic describes the format that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for backup media, the correspondence between backup media and backup devices, the organization of backups on backup media, and several considerations for media sets and media families.</span></span> <span data-ttu-id="9e5ae-105">本主题还介绍在第一次使用备份介质或在使用新介质集替代旧介质集之前对备份介质进行初始化和格式化的步骤，如何覆盖介质集中的旧备份集，以及如何将新备份集追加到介质集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-105">The topic also describes the steps initializing or formatting backup media before you use it for the first time or replace an old media set with a new media set, how to overwrite old backup sets in a media set, and how to append new backup sets to a media set.</span></span>

> [!NOTE]
>  <span data-ttu-id="9e5ae-106">有关 SQL Server 备份到 Azure Blob 存储服务的详细信息，请参阅[SQL Server 备份和还原与 Azure Blob 存储服务进行备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-106">For more information on SQL Server backup to the Azure Blob storage service,, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>


##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="9e5ae-107">术语和定义</span><span class="sxs-lookup"><span data-stu-id="9e5ae-107">Terms and Definitions</span></span>
 <span data-ttu-id="9e5ae-108">介质集 (介质集 (media set)) 备份介质（磁带或磁盘文件）的有序集合，使用固定类型和数量的备份设备向其写入了一个或多个备份操作。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-108">media set An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>

 <span data-ttu-id="9e5ae-109">介质簇 (介质簇 (media family)) 在介质集中的单个非镜像设备或一组镜像设备上创建的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-109">media family Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>

 <span data-ttu-id="9e5ae-110">备份集 (备份集 (backup set)) 通过成功的备份操作添加到介质组的备份内容。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-110">backup set The backup content that is added to a media set by a successful backup operation.</span></span>


##  <a name="overview-of-media-sets-media-families-and-backup-sets"></a><a name="OvMediaSetsFamiliesBackupSets"></a><span data-ttu-id="9e5ae-111">介质集、介质簇和备份集概述</span><span class="sxs-lookup"><span data-stu-id="9e5ae-111">Overview of Media Sets, Media Families, and Backup Sets</span></span>
 <span data-ttu-id="9e5ae-112">包含一个或多个备份介质的集合的备份构成一个介质集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-112">The backups on a set of one or more backup media compose a single media set.</span></span> <span data-ttu-id="9e5ae-113">*媒体集* 是 *备份媒体*（磁带或磁盘文件，或者是 Azure Blob）的有序集合，一个或多个备份操作使用固定类型和数量的备份设备向其写入。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-113">A *media set* is an ordered collection of *backup media*, tapes or disk files, or Azure Blobs, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="9e5ae-114">给定媒体集使用磁带驱动器，或者使用磁盘驱动器或 Azure Blob，但不能结合使用两者或以上。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-114">A given media set uses tape drives, or disk drives or Azure blobs, but not a combination of two or more.</span></span> <span data-ttu-id="9e5ae-115">例如，与介质集关联的备份设备可能是三个名为 `\\.\TAPE0`、 `\\.\TAPE1`和 `\\.\TAPE2`的磁带机。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-115">For example, the backup devices associated with a media set might be three tape drives named `\\.\TAPE0`, `\\.\TAPE1`, and `\\.\TAPE2`.</span></span> <span data-ttu-id="9e5ae-116">该介质集仅包含磁带，最少需要三个磁带（每个磁带机一个磁带）。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-116">That media set contains only tapes, starting with a minimum of three tapes (one per drive).</span></span> <span data-ttu-id="9e5ae-117">备份设备的类型和数量是在创建介质集时建立的，不能更改。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-117">The type and number of backup devices are established when a media set is created, and they cannot be changed.</span></span> <span data-ttu-id="9e5ae-118">但是，如有必要，可以在备份和还原操作之间将给定设备替换为同一类型的设备。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-118">However, if necessary, between backup and restore operations a given device can be replaced with a device of the same type.</span></span>

 <span data-ttu-id="9e5ae-119">介质集是在备份操作过程中通过格式化备份介质从而在备份介质上创建的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-119">A media set is created on the backup media during a backup operation by formatting the backup media.</span></span> <span data-ttu-id="9e5ae-120">有关详细信息，请参阅本主题后面的 [创建新介质集](#CreatingMediaSet)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-120">For more information, see [Creating a New Media Set](#CreatingMediaSet), later in this topic.</span></span> <span data-ttu-id="9e5ae-121">设置格式后，每个文件或磁带都包含介质集的介质标头，可以开始接收备份内容。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-121">After formatting, each file or tape contains a media header for the media set and is ready to receive backup content.</span></span> <span data-ttu-id="9e5ae-122">有了标头后，备份操作会将指定数据备份到为该操作指定的所有备份设备中的备份介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-122">With the header in place, the backup operation proceeds to back up the specified data to the backup media on all of the backup devices specified for the operation.</span></span>

> [!NOTE]
>  <span data-ttu-id="9e5ae-123">可以镜像介质集，以防介质卷（磁带或磁盘文件）被破坏。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-123">Media sets can be mirrored to protect against a damaged media volume (a tape or disk file).</span></span> <span data-ttu-id="9e5ae-124">有关详细信息，请参阅本主题后面的 [镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md)不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-124">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="9e5ae-125">或更高版本可以读取压缩的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-125">or later can read compressed backups.</span></span> <span data-ttu-id="9e5ae-126">有关详细信息，请参阅[备份压缩 (SQL Server)](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-126">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


### <a name="media-families"></a><span data-ttu-id="9e5ae-127">介质簇</span><span class="sxs-lookup"><span data-stu-id="9e5ae-127">Media Families</span></span>
 <span data-ttu-id="9e5ae-128">“介质簇”  由在介质集中的单个非镜像设备或一组镜像设备上创建的备份构成。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-128">Backups created on a single nonmirrored device or a set of mirrored devices in a media set constitute a *media family*.</span></span> <span data-ttu-id="9e5ae-129">介质集所使用的备份设备的数量决定了介质集中的介质簇的数量。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-129">The number of backup devices used for the media set determines the number of media families in a media set.</span></span> <span data-ttu-id="9e5ae-130">例如，如果介质集使用两个非镜像备份设备，则该介质集包含两个介质簇。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-130">For example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>

> [!NOTE]
>  <span data-ttu-id="9e5ae-131">在镜像介质集中，所有介质簇也是镜像的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-131">In a mirrored media set, each media family is mirrored.</span></span> <span data-ttu-id="9e5ae-132">例如，如果使用六个备份设备来设置介质集的格式，其中使用了两个镜像，则有三个介质簇，每个介质簇包含两个相同的备份数据副本。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-132">For example, if six backup devices are used to format a media set, where two mirrors are used, there are three media families, each containing two equivalent copies of backup data.</span></span> <span data-ttu-id="9e5ae-133">有关镜像媒体集的详细信息，请参阅[镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-133">For more information about mirrored media sets, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 <span data-ttu-id="9e5ae-134">介质簇中的每个磁带或磁盘都分配了“介质序列号”  。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-134">Each tape or disk in a media family is assigned a *media sequence number*.</span></span> <span data-ttu-id="9e5ae-135">磁盘的介质序列号通常为 1。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-135">The media sequence number of a disk is always 1.</span></span> <span data-ttu-id="9e5ae-136">在磁带介质簇中，起始磁带的序列号为 1，第二盘磁带的序列号为 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-136">In a tape media family, the sequence number of the initial tape is 1, the sequence number of the second tape is 2, and so forth.</span></span> <span data-ttu-id="9e5ae-137">有关详细信息，请参阅 [使用介质集和介质簇](#ConsiderationsForMediaSetFamilies)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-137">For more information, see [Using Media Sets and Families](#ConsiderationsForMediaSetFamilies).</span></span>

#### <a name="the-media-header"></a><span data-ttu-id="9e5ae-138">介质标头</span><span class="sxs-lookup"><span data-stu-id="9e5ae-138">The Media Header</span></span>
 <span data-ttu-id="9e5ae-139">备份介质（磁盘文件或磁带）的每个卷都包含介质标头，介质标头是在第一次使用磁带（或磁盘）执行备份操作时创建的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-139">Every volume of backup media (disk file or tape) contains a media header that is created when by the first backup operation that uses the tape (or disk).</span></span> <span data-ttu-id="9e5ae-140">标头在重新设置介质格式之前保持不变。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-140">That header remains intact until the media is reformatted.</span></span>

 <span data-ttu-id="9e5ae-141">介质标头包含标识介质（磁盘文件或磁带）及其在所属介质簇中的位置所需的所有信息。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-141">The media header contains all of the information required to identify the media (disk file or tape) and its place within the media family to which it belongs.</span></span> <span data-ttu-id="9e5ae-142">此信息包括：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-142">This information includes:</span></span>

-   <span data-ttu-id="9e5ae-143">介质的名称。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-143">The name of the media.</span></span>

     <span data-ttu-id="9e5ae-144">介质名称是可选的，但建议始终使用能够明确标识介质的名称。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-144">The media name is optionally, but we recommend consistently using media names that clearly identify your media.</span></span> <span data-ttu-id="9e5ae-145">介质名称由设置介质格式的用户指定。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-145">A media name is assigned by whoever formats the media.</span></span>

-   <span data-ttu-id="9e5ae-146">介质集的唯一标识号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-146">The unique identification number of the media set.</span></span>

-   <span data-ttu-id="9e5ae-147">介质集中的介质簇数。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-147">The number of media families in the media set.</span></span>

-   <span data-ttu-id="9e5ae-148">包含此介质的介质簇的序列号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-148">The sequence number of the media family containing this media.</span></span>

-   <span data-ttu-id="9e5ae-149">介质簇的唯一标识号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-149">The unique identification number for the media family.</span></span>

-   <span data-ttu-id="9e5ae-150">介质簇中此介质的序列号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-150">The sequence number of this media in the media family.</span></span> <span data-ttu-id="9e5ae-151">对于磁盘文件，此值始终为 1。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-151">For a disk file, this value is always 1.</span></span>

-   <span data-ttu-id="9e5ae-152">介质说明中是包含 MTF 介质标签还是包含介质说明。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-152">Whether the media description contains an MTF media label or a media description.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9e5ae-153">用于备份或还原操作的所有介质都使用一种标准备份格式，该格式 [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] 保留由其他应用程序写入的任何 mtf 介质标签，但不会写入 mtf 介质标签。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-153">All media that is used for a backup or restore operation use a standard backup format called [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] preserves any MTF media label written by another application but does not write MTF media labels.</span></span>

-   <span data-ttu-id="9e5ae-154">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 磁带格式介质标签或介质说明（自由格式文本）。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-154">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format media label or the media description (in free-form text).</span></span>

-   <span data-ttu-id="9e5ae-155">用于创建标签的备份软件的名称。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-155">The name of the backup software that wrote the label.</span></span>

-   <span data-ttu-id="9e5ae-156">格式化介质的软件供应商的唯一供应商标识号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-156">The unique vendor identification number of the software vendor that formatted the media.</span></span>

-   <span data-ttu-id="9e5ae-157">创建标签的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-157">The date and time the label was written.</span></span>

-   <span data-ttu-id="9e5ae-158">介质集中的镜像数 (1-4)，1 表示设备未镜像。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-158">The number of mirrors in the set (1-4); 1 indicates an unmirrored device.</span></span>

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="9e5ae-159">可以处理使用早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]设置格式的介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-159">can process media formatted by earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

### <a name="backup-sets"></a><span data-ttu-id="9e5ae-160">备份集</span><span class="sxs-lookup"><span data-stu-id="9e5ae-160">Backup Sets</span></span>
 <span data-ttu-id="9e5ae-161">成功的备份操作将向介质集中添加一个“备份集”  。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-161">A successful backup operation adds a single *backup set* to the media set.</span></span> <span data-ttu-id="9e5ae-162">从备份所属的介质集方面对备份集进行说明。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-162">The backup set is described in terms of the media set to which the backup belongs.</span></span> <span data-ttu-id="9e5ae-163">如果备份介质只包含一个介质簇，则该簇包含整个备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-163">If the backup media consists of only one media family, that family contains the entire backup set.</span></span> <span data-ttu-id="9e5ae-164">如果备份介质包含多个介质簇，则备份集分布在各个介质簇之间。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-164">If the backup media consists of multiple media families, the backup set is distributed among them.</span></span> <span data-ttu-id="9e5ae-165">在每个介质上，备份集都包含说明备份集的标头。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-165">On each medium, the backup set contains a header that describes the backup set.</span></span>

 <span data-ttu-id="9e5ae-166">下例显示一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，该语句使用三个磁带机作为备份设备，为 `MyAdvWorks_MediaSet_1` 数据库创建一个名为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 的介质集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-166">The following example shows a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates a media set called `MyAdvWorks_MediaSet_1` for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database using three tape drives as backup devices:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   FORMAT,
   MEDIANAME = 'MyAdvWorks_MediaSet_1'
```

 <span data-ttu-id="9e5ae-167">如果成功，此备份操作将生成一个新的介质集，该介质集包含一个新介质标头和一个分布在三个磁带上的备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-167">If successful, this backup operation results in a new media set containing a new media header and one backup set spread across three tapes.</span></span> <span data-ttu-id="9e5ae-168">下图说明了这些结果：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-168">The following figure illustrates these results:</span></span>

 <span data-ttu-id="9e5ae-169">![3 个磁带上的媒体标头和第一个备份集](../../database-engine/media/bnr-mediaset-new.gif "3 个磁带上的媒体标头和第一个备份集")</span><span class="sxs-lookup"><span data-stu-id="9e5ae-169">![Media header and first backup set on 3 tapes](../../database-engine/media/bnr-mediaset-new.gif "Media header and first backup set on 3 tapes")</span></span>

 <span data-ttu-id="9e5ae-170">通常，创建介质集后，后续备份操作将依次向介质集追加其备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-170">Typically, after a media set is created, subsequent backup operations, one after another, append their backup sets to the media set.</span></span> <span data-ttu-id="9e5ae-171">备份集使用的所有介质构成了介质集，而与所涉及到的介质或备份设备的数量无关。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-171">All of the media used by a backup set make up the media set, regardless of the number of media or backup devices involved.</span></span> <span data-ttu-id="9e5ae-172">备份集按照其在介质集中的位置依次编号，从而使您能够指定还原哪个备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-172">Backup sets are sequentially numbered by their position in the media set, allowing you to specify which backup set to restore.</span></span>

 <span data-ttu-id="9e5ae-173">介质集的每个备份操作都必须写入相同数量和类型的备份设备。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-173">Every backup operation to a media set must write to the same number and type of backup devices.</span></span> <span data-ttu-id="9e5ae-174">如果使用多个设备，则与第一个备份集相同，每个后续备份集的内容都分布在所有设备的备份介质中。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-174">With multiple devices, as with the first backup set, the content of every subsequent backup set is distributed among the backup media on all of the devices.</span></span> <span data-ttu-id="9e5ae-175">为了继续上面的示例，第二个备份操作（差异备份）将向同一介质集追加信息：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-175">To continue the above example, a second backup operation (a differential backup) appends information to the same media set:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   NOINIT,
   MEDIANAME = 'AdventureWorksMediaSet1',
   DIFFERENTIAL
```

> [!NOTE]
>  <span data-ttu-id="9e5ae-176">NOINIT 选项是默认选项，但为清楚起见，要包括此选项。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-176">The NOINIT option is the default, but is included for clarity.</span></span>

 <span data-ttu-id="9e5ae-177">如果第二个备份操作成功，将向介质集写入第二个备份集，并按以下方式分布备份内容：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-177">If the second backup operation succeeds, it writes a second backup set to the media set, with the following distribution of backup content:</span></span>

 <span data-ttu-id="9e5ae-178">![第二个备份集分散在 3 个媒体集磁带上](../../database-engine/media/bnr-mediaset-appendedto.gif "第二个备份集分散在 3 个媒体集磁带上")</span><span class="sxs-lookup"><span data-stu-id="9e5ae-178">![Second backup set spread across 3 media-set tapes](../../database-engine/media/bnr-mediaset-appendedto.gif "Second backup set spread across 3 media-set tapes")</span></span>

 <span data-ttu-id="9e5ae-179">在还原备份时，您可以使用 FILE 选项来指定想要使用的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-179">When you are restoring backups, you can use you the FILE option to specify which backups you want to use.</span></span> <span data-ttu-id="9e5ae-180">下面的示例展示了 FILE **=** _backup_set_file_number_ 子句的使用方法，在还原 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的完整数据库备份并随后还原位于相同媒体集上的数据库差异备份时使用该子句。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-180">The following example shows the use of FILE **=**_backup_set_file_number_ clauses when restoring a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database followed by a differential database backup on the same media set.</span></span> <span data-ttu-id="9e5ae-181">介质集使用了三个备份磁带，它们位于磁带机 `\\.\tape0`、 `tape1`和 `tape2`上。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-181">The media set uses three backup tapes, which are on tape drives `\\.\tape0`, `tape1`, and `tape2`.</span></span>

```
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=1, 
   NORECOVERY;
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2' 
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=2, 
   RECOVERY;
GO
```

 <span data-ttu-id="9e5ae-182">历史记录表存储了媒体集及其媒体簇和备份集的相关信息，有关历史记录表的信息，请参阅 [备份历史记录和标头信息 (SQL Server)](backup-history-and-header-information-sql-server.md)不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-182">For information about the history tables that store information about media sets and their media families and backup sets, see [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md).</span></span>

 <span data-ttu-id="9e5ae-183">介质集中备份介质的数量取决于下列几个因素：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-183">The number of backup media in a media set depends on several factors:</span></span>

-   <span data-ttu-id="9e5ae-184">备份设备的数量</span><span class="sxs-lookup"><span data-stu-id="9e5ae-184">Number of backup devices</span></span>

-   <span data-ttu-id="9e5ae-185">备份设备的类型</span><span class="sxs-lookup"><span data-stu-id="9e5ae-185">Type of backup devices</span></span>

-   <span data-ttu-id="9e5ae-186">备份集的数量</span><span class="sxs-lookup"><span data-stu-id="9e5ae-186">Number of backup sets</span></span>

##  <a name="using-media-sets-and-families"></a><a name="ConsiderationsForMediaSetFamilies"></a><span data-ttu-id="9e5ae-187">使用介质集和系列</span><span class="sxs-lookup"><span data-stu-id="9e5ae-187">Using Media Sets and Families</span></span>
 <span data-ttu-id="9e5ae-188">本节讨论使用介质集和介质簇的若干注意事项。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-188">This section discusses several considerations for using media sets and media families.</span></span>



###  <a name="creating-a-new-media-set"></a><a name="CreatingMediaSet"></a><span data-ttu-id="9e5ae-189">创建新介质集</span><span class="sxs-lookup"><span data-stu-id="9e5ae-189">Creating a New Media Set</span></span>
 <span data-ttu-id="9e5ae-190">若要创建新介质集，必须格式化备份介质（一个或多个磁带或磁盘文件）。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-190">To create a new media set, you must format the backup media (one or more tapes or disk files).</span></span> <span data-ttu-id="9e5ae-191">格式化进程会对备份介质进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-191">The formatting process changes the backup media as follows:</span></span>

1.  <span data-ttu-id="9e5ae-192">删除旧标头（如果存在），从而有效地删除备份介质中以前的内容。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-192">Deletes the old header (if any), effectively deleting the previous contents of the backup media.</span></span>

     <span data-ttu-id="9e5ae-193">格式化磁带设备会删除当前装入的磁带中以前所有内容。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-193">Formatting a tape device deletes all previous contents of the currently mounted tape.</span></span> <span data-ttu-id="9e5ae-194">格式化磁盘只影响您为备份操作指定的文件。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-194">Formatting a disk affects only the file that you specify for the backup operation</span></span>

2.  <span data-ttu-id="9e5ae-195">向每个备份设备中的备份介质（磁带或磁盘文件）写入新的介质标头。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-195">Writes a new media header on the backup media (tape or disk file) on each of the backup devices.</span></span>


###  <a name="backing-up-to-an-existing-media-set"></a><a name="UseExistingMediaSet"></a><span data-ttu-id="9e5ae-196">备份到现有介质集</span><span class="sxs-lookup"><span data-stu-id="9e5ae-196">Backing Up to an Existing Media Set</span></span>
 <span data-ttu-id="9e5ae-197">当备份到某个现有介质集时，您可以使用以下两个选项：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-197">When you are backing up to an existing media set, you have the following two options:</span></span>

-   <span data-ttu-id="9e5ae-198">追加到现有备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-198">Append to the existing backup set.</span></span>

     <span data-ttu-id="9e5ae-199">为了尽可能利用可用空间，通常将新的备份集追加到现有介质集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-199">To make the best possible use of the available space, new backup sets typically are appended to existing media set.</span></span> <span data-ttu-id="9e5ae-200">追加到备份时会保留所有以前的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-200">Appending to the backup preserves any prior backups.</span></span> <span data-ttu-id="9e5ae-201">有关详细信息，请参阅本节后面的 [追加到现有备份集](#Appending)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-201">For more information, see [Appending to Existing Backup Sets](#Appending), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9e5ae-202">追加是 BACKUP 的默认行为，可以通过使用 NOINIT 选项显式指定追加。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-202">Appending, which is the default behavior of the BACKUP, can be explicitly specified by using the NOINIT option.</span></span>

-   <span data-ttu-id="9e5ae-203">使用当前备份覆盖所有现有备份集，保持当前介质标头位置不变。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-203">Overwrite all existing backup sets with the current backup, leaving the current media header in place.</span></span>

     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9e5ae-204">备份提供防止意外覆盖介质的安全措施。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-204">backup has safeguards to prevent you from accidentally overwriting media.</span></span> <span data-ttu-id="9e5ae-205">但是，备份集到达预定义的到期日期时，备份会自动覆盖备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-205">However, backup can automatically overwrite backup sets that have reached a predefined expiration date.</span></span>

     <span data-ttu-id="9e5ae-206">对于磁带标头，适当地保留标头还是很有帮助的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-206">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="9e5ae-207">有关详细信息，请参阅本节后面的 [覆盖备份集](#Overwriting)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-207">For more information, see [Overwriting Backup Sets](#Overwriting), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9e5ae-208">使用 BACKUP 语句中的 INIT 选项可指定覆盖现有备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-208">Overwriting existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span>

####  <a name="appending-to-existing-backup-sets"></a><a name="Appending"></a><span data-ttu-id="9e5ae-209">追加到现有备份集</span><span class="sxs-lookup"><span data-stu-id="9e5ae-209">Appending to Existing Backup Sets</span></span>
 <span data-ttu-id="9e5ae-210">可以将来自相同或不同数据库的、在不同时间执行的备份存储在同一个介质上。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-210">Backups performed at different times from the same or different databases can be stored on the same media.</span></span> <span data-ttu-id="9e5ae-211">通过将其他备份集追加到现有介质上，介质上以前的内容保持不变，新的备份在介质上最后一个备份的结尾处写入。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-211">By appending another backup set to existing media, the previous contents of the media remain intact, and the new backup is written after the end of the last backup on the media.</span></span>

 <span data-ttu-id="9e5ae-212">默认情况下, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 始终在介质上追加新的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-212">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always appends new backups to media.</span></span> <span data-ttu-id="9e5ae-213">只能在介质的结尾处追加备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-213">Appending can occur only at the end of the media.</span></span> <span data-ttu-id="9e5ae-214">例如，如果介质卷包含五个备份集，则不能跳过前三个备份集而用新的备份集覆盖第四个备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-214">For example, if a media volume contains five backup sets, it is not possible to skip the first three backup sets to overwrite the fourth backup set with a new backup set.</span></span>

 <span data-ttu-id="9e5ae-215">如果将 BACKUP WITH NOREWIND 用于磁带备份，则磁带在操作结束时将保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-215">If you use BACKUP WITH NOREWIND for a tape backup, the tape will be left open at the end of the operation.</span></span> <span data-ttu-id="9e5ae-216">这使您得以在磁带中追加其他备份，而不用倒带然后再次往前扫描以查找最后一个备份集。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-216">This allows you to append further backups to the tape without rewinding the tape and then scanning forward again to find the last backup set.</span></span> <span data-ttu-id="9e5ae-217">你可以在 **sys.dm_io_backup_tapes** 动态管理视图中找到打开的磁带驱动器的列表；有关详细信息，请参阅 [sys.dm_io_backup_tapes (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-217">You can find the list of open tape drives in the **sys.dm_io_backup_tapes** dynamic management view; for more information, see [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql).</span></span>

 <span data-ttu-id="9e5ae-218">Microsoft Windows 备份和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份可以共享同一介质，但它们之间不能相互操作。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-218">Microsoft Windows backups and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups can share the same media, but they are not interoperable.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9e5ae-219">备份不能备份 Windows 数据。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-219">backup cannot back up Windows data.</span></span>

> [!IMPORTANT]
>  [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="9e5ae-220">或更高版本可以读取压缩的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-220">or later versions can read compressed backups.</span></span> <span data-ttu-id="9e5ae-221">有关详细信息，请参阅[备份压缩 (SQL Server)](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-221">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


####  <a name="overwriting-backup-sets"></a><a name="Overwriting"></a><span data-ttu-id="9e5ae-222">覆盖备份集</span><span class="sxs-lookup"><span data-stu-id="9e5ae-222">Overwriting Backup Sets</span></span>
 <span data-ttu-id="9e5ae-223">覆盖现有备份集是使用 BACKUP 语句的 INIT 选项指定的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-223">Overwriting of existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span> <span data-ttu-id="9e5ae-224">此选项将覆盖介质上的所有备份集并保留介质标头（如果有）。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-224">This option overwrites all the backup sets on the media and preserve the media header, if any.</span></span> <span data-ttu-id="9e5ae-225">如果没有介质标头，则创建一个标头。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-225">If no media header exists, one is created.</span></span>

 <span data-ttu-id="9e5ae-226">对于磁带标头，适当地保留标头还是很有帮助的。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-226">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="9e5ae-227">对于磁盘备份介质，只覆盖备份操作中指定的备份设备所使用的文件；磁盘上的其他文件不受影响。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-227">For disk backup media, only the files used by the backup devices specified in the backup operation are overwritten; other files on the disk are unaffected.</span></span> <span data-ttu-id="9e5ae-228">覆盖备份时，保留现有的所有介质标头，同时将新的备份创建为备份设备中的第一个备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-228">When overwriting backups, any existing media header is preserved, and the new backup is created as the first backup on the backup device.</span></span> <span data-ttu-id="9e5ae-229">如果没有现有的介质标头，将自动编写一个带相关介质名称和介质描述的有效介质标头。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-229">If there is no existing media header, a valid media header with an associated media name and media description is written automatically.</span></span> <span data-ttu-id="9e5ae-230">如果现有的介质标头无效，备份操作将终止。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-230">If the existing media header is invalid, the backup operation terminates.</span></span> <span data-ttu-id="9e5ae-231">如果介质为空，则使用给定的 MEDIANAME、MEDIAPASSWORD 和 MEDIADESCRIPTION（如果存在）生成新的介质标头。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-231">If the media is empty, the new media header is generated with the given MEDIANAME, MEDIAPASSWORD, and MEDIADESCRIPTION, if any.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9e5ae-232">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]开始，MEDIAPASSWORD 选项不再可用于创建备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-232">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the MEDIAPASSWORD option is discontinued for creating backups.</span></span> <span data-ttu-id="9e5ae-233">但仍可以还原使用密码创建的备份。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-233">However, you can still restore backups created with passwords.</span></span>

 <span data-ttu-id="9e5ae-234">存在下列任一条件时不覆盖备份介质：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-234">Backup media is not overwritten if either of the following conditions exists:</span></span>

-   <span data-ttu-id="9e5ae-235">介质上的现有备份尚未过期。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-235">The existing backups on the media have not expired.</span></span> <span data-ttu-id="9e5ae-236">（如果指定 SKIP，则不检查过期。）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-236">(If SKIP is specified, expiration is not checked.)</span></span>

     <span data-ttu-id="9e5ae-237">过期日期将指定备份过期的日期，并可以由另一个备份覆盖。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-237">The expiration date specifies the date that the backup expires and can be overwritten by another backup.</span></span> <span data-ttu-id="9e5ae-238">创建备份时可以指定过期日期。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-238">You can specify the expiration date when a backup is created.</span></span> <span data-ttu-id="9e5ae-239">默认情况下，过期日期由 **sp_configure** 设置的 **media retention**选项确定。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-239">By default, the expiration date is determined by the **media retention** option set with **sp_configure**.</span></span> <span data-ttu-id="9e5ae-240">有关详细信息，请参阅本主题后面的 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-240">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>

-   <span data-ttu-id="9e5ae-241">介质名称（如果有）与备份介质上的名称不匹配。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-241">The media name, if provided, does not match the name on the backup media.</span></span>

     <span data-ttu-id="9e5ae-242">介质名称是一个描述性名称，用于方便地识别介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-242">The media name is a descriptive name used for easy identification of the media.</span></span>

 <span data-ttu-id="9e5ae-243">如果确实想要覆盖现有介质（例如知道不再需要磁带上的备份），则可以显式跳过这些检查。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-243">If you are sure you want to overwrite the existing media (for example, if you know that the backups on the tape are no longer needed), you can explicitly skip these checks.</span></span>

 <span data-ttu-id="9e5ae-244">如果备份介质受 Microsoft Windows 密码保护，则 Microsoft SQL Server 不会写入介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-244">If the backup media is password protected by Microsoft Windows, Microsoft SQL Server does not write to the media.</span></span> <span data-ttu-id="9e5ae-245">若要覆盖有密码保护的介质，必须重新初始化该介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-245">To overwrite media that is password protected, you must reinitialize the media.</span></span>


###  <a name="sequence-numbers"></a><a name="SequenceNumbers"></a><span data-ttu-id="9e5ae-246">序列号</span><span class="sxs-lookup"><span data-stu-id="9e5ae-246">Sequence Numbers</span></span>
 <span data-ttu-id="9e5ae-247">对于介质集中的多个介质簇或介质簇中的多个备份介质，正确的顺序很重要。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-247">The correct order is important for multiple media families within a media set or multiple backup media within a media family.</span></span> <span data-ttu-id="9e5ae-248">因此，备份按以下方式分配序列号：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-248">Therefore, backup assigns sequence numbers in the following ways:</span></span>

-   <span data-ttu-id="9e5ae-249">介质集中的有序介质簇</span><span class="sxs-lookup"><span data-stu-id="9e5ae-249">Sequential media families within a media set</span></span>

     <span data-ttu-id="9e5ae-250">在介质集中，根据介质簇在介质集中的位置，按顺序给介质簇进行编号。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-250">Within a media set, the media families are numbered sequentially according to their position in the media set.</span></span> <span data-ttu-id="9e5ae-251">媒体簇号记录在 **backupmediafamily** 表的 **family_sequence_number** 列中。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-251">The media-family number is recorded in the **family_sequence_number** column of the **backupmediafamily** table.</span></span>

-   <span data-ttu-id="9e5ae-252">介质簇中的物理介质</span><span class="sxs-lookup"><span data-stu-id="9e5ae-252">Physical media within a media family</span></span>

     <span data-ttu-id="9e5ae-253">介质序列号指示介质簇中的物理介质的顺序。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-253">A media sequence number indicates the order of the physical media within a media family.</span></span> <span data-ttu-id="9e5ae-254">对于第一个备份介质，序列号是 1。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-254">The sequence number is 1 for the initial backup media.</span></span> <span data-ttu-id="9e5ae-255">第一个备份介质的标记为 1，第二个介质（第一个延续磁带）的标记为 2，依此类推。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-255">This is tagged with 1; the second (the first continuation tape) is tagged with 2; and so on.</span></span> <span data-ttu-id="9e5ae-256">在还原备份集时，介质序列号可以确保负责还原备份的操作员按正确的顺序装入介质。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-256">When the backup set is restored, the media sequence numbers make sure that the operator restoring the backup mounts the correct media in the correct order.</span></span>

###  <a name="multiple-devices"></a><a name="MultipleDevices"></a> <span data-ttu-id="9e5ae-257">多个设备</span><span class="sxs-lookup"><span data-stu-id="9e5ae-257">Multiple Devices</span></span>
 <span data-ttu-id="9e5ae-258">当您使用多个磁带机或磁盘文件时，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-258">When you use multiple tape drives or disk files, the following considerations apply:</span></span>

-   <span data-ttu-id="9e5ae-259">备份时的注意事项：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-259">For backup:</span></span>

     <span data-ttu-id="9e5ae-260">由备份操作创建的整个介质集必须用于所有后续备份操作。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-260">The complete media set that is created by a backup operation must be used by all subsequent backup operations.</span></span> <span data-ttu-id="9e5ae-261">例如，如果介质集是使用两台磁带备份设备创建的，则涉及相同介质集的所有后续备份操作都必须使用两台备份设备。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-261">For example, if a media set was created by using two tape backup devices, all subsequent backup operations that involve the same media set must use two backup devices.</span></span>

-   <span data-ttu-id="9e5ae-262">还原时的注意事项：</span><span class="sxs-lookup"><span data-stu-id="9e5ae-262">For restore:</span></span>

     <span data-ttu-id="9e5ae-263">对于任何从磁盘备份进行的还原以及任何联机还原，必须同时装入全部介质簇。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-263">For any restore from disk backups and for any online restore, all the all media families must be concurrently mounted.</span></span> <span data-ttu-id="9e5ae-264">对于从磁带备份进行的脱机还原，可以在数量少于介质簇的备份设备中处理介质簇。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-264">For an offline restore from tape backups, you can process the media families from fewer backup devices.</span></span> <span data-ttu-id="9e5ae-265">必须在每一介质簇已完全处理之后才能开始处理另一个介质簇。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-265">Each media family must be processed completely before starting to process another media family.</span></span> <span data-ttu-id="9e5ae-266">介质簇总是并行处理的，除非使用单个设备还原介质簇。</span><span class="sxs-lookup"><span data-stu-id="9e5ae-266">Media families are always processed in parallel, unless they are being restored with a single device.</span></span>

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9e5ae-267">相关任务</span><span class="sxs-lookup"><span data-stu-id="9e5ae-267">Related Tasks</span></span>
 <span data-ttu-id="9e5ae-268">**创建新介质集**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-268">**To create a new media set**</span></span>

-   <span data-ttu-id="9e5ae-269">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)（“备份到新媒体集并清除所有现有备份集”  选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-269">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Back up to a new media set, and erase all existing backup sets** option)</span></span>

-   <span data-ttu-id="9e5ae-270">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) （FORMAT 选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT option)</span></span>

-   <xref:Microsoft.SqlServer.Management.Smo.Backup.FormatMedia%2A>

 <span data-ttu-id="9e5ae-271">**在现有介质上追加新的备份**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-271">**To append a new backup to existing media**</span></span>

-   <span data-ttu-id="9e5ae-272">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)（“追加到现有备份集”  选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-272">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Append to the existing backup set** option)</span></span>

-   <span data-ttu-id="9e5ae-273">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) （NOINIT 选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT option)</span></span>

 <span data-ttu-id="9e5ae-274">**覆盖所有现有备份集**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-274">**To overwrite existing backup sets**</span></span>

-   <span data-ttu-id="9e5ae-275">[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)（“覆盖所有现有备份集”  选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-275">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Overwrite all existing backup sets** option)</span></span>

-   <span data-ttu-id="9e5ae-276">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) （INIT 选项）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT option)</span></span>

 <span data-ttu-id="9e5ae-277">**设置过期日期**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-277">**To set the expiration date**</span></span>

-   [<span data-ttu-id="9e5ae-278">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-278">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)

 <span data-ttu-id="9e5ae-279">**查看介质序列号和簇序列号**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-279">**To view the media sequence and family sequence numbers**</span></span>

-   [<span data-ttu-id="9e5ae-280">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-280">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   <span data-ttu-id="9e5ae-281">[backupmediafamily (Transact-SQL)](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)（**family_sequence_number** 列）</span><span class="sxs-lookup"><span data-stu-id="9e5ae-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** column)</span></span>

 <span data-ttu-id="9e5ae-282">**查看特定备份设备中的备份集**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-282">**To view the backup sets on a particular backup device**</span></span>

-   [<span data-ttu-id="9e5ae-283">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-283">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)

-   [<span data-ttu-id="9e5ae-284">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-284">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   [<span data-ttu-id="9e5ae-285">RESTORE HEADERONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)

 <span data-ttu-id="9e5ae-286">**读取备份设备中的介质的介质标头**</span><span class="sxs-lookup"><span data-stu-id="9e5ae-286">**To read the media header of the media on a backup device**</span></span>

-   [<span data-ttu-id="9e5ae-287">RESTORE LABELONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)


## <a name="see-also"></a><span data-ttu-id="9e5ae-288">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e5ae-288">See Also</span></span>
 <span data-ttu-id="9e5ae-289">备份和还原[SQL Server 数据库](back-up-and-restore-of-sql-server-databases.md)[在备份和还原期间可能的媒体错误 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [备份历史记录和标头信息](backup-history-and-header-information-sql-server.md)&#40;SQL Server&#41;[镜像备份媒体集 &#40;](mirrored-backup-media-sets-sql-server.md) SQL Server&#41;&#40;&#41;[transact-sql &#40;](/sql/t-sql/statements/backup-transact-sql) [Restore&#41;transact-sql](/sql/t-sql/statements/restore-statements-transact-sql) &#40;[restore REWINDONLY&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) transact-sql sp_configure &#40;[&#41;transact-sql](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="9e5ae-289">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span></span>


