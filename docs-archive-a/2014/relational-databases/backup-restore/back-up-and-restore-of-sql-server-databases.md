---
title: SQL Server 数据库的备份和还原 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], see restoring [SQL Server]
- backups [SQL Server]
- restoring databases [SQL Server]
- backup [SQL Server], see backing up [SQL Server]
- databases [SQL Server], restoring
- backing up databases [SQL Server]
- restore [SQL Server], see restoring [SQL Server]
- disaster recovery [SQL Server], see backing up [SQL Server]
- backing up [SQL Server]
- Database Engine [SQL Server], backups
- databases [SQL Server], backups
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec2104219d98ed3cb97bfbb8993a3c28d45841c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591435"
---
# <a name="back-up-and-restore-of-sql-server-databases"></a><span data-ttu-id="0fa94-102">SQL Server 数据库的备份和还原</span><span class="sxs-lookup"><span data-stu-id="0fa94-102">Back Up and Restore of SQL Server Databases</span></span>
  <span data-ttu-id="0fa94-103">本主题介绍备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的优点、基本的备份和还原术语，还介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的备份和还原策略以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="0fa94-103">This topic describes the benefits of backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, basic backup and restore terms, and introduces backup and restore strategies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and security considerations for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore.</span></span>  
  
 <span data-ttu-id="0fa94-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原组件为保护存储在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中的关键数据提供了基本安全保障。</span><span class="sxs-lookup"><span data-stu-id="0fa94-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore component provides an essential safeguard for protecting critical data stored in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="0fa94-105">为了尽量降低灾难性数据丢失的风险，需备份数据库，以便定期保存对数据的修改。</span><span class="sxs-lookup"><span data-stu-id="0fa94-105">To minimize the risk of catastrophic data loss, you need to back up your databases to preserve modifications to your data on a regular basis.</span></span> <span data-ttu-id="0fa94-106">计划良好的备份和还原策略有助于保护数据库，使之免受各种故障导致的数据丢失的威胁。</span><span class="sxs-lookup"><span data-stu-id="0fa94-106">A well-planned backup and restore strategy helps protect databases against data loss caused by a variety of failures.</span></span> <span data-ttu-id="0fa94-107">测试策略，方法是先还原一组备份，然后恢复数据库，以便准备好对灾难进行有效的响应。</span><span class="sxs-lookup"><span data-stu-id="0fa94-107">Test your strategy by restoring a set of backups and then recovering your database to prepare you to respond effectively to a disaster.</span></span>  
  
 <span data-ttu-id="0fa94-108">除了在本地存储中存储备份外，SQL Server 还支持备份到 Azure Blob 存储服务和从其还原。</span><span class="sxs-lookup"><span data-stu-id="0fa94-108">In addition to local storage for storing the backups, SQL Server also supports backup to and restore from the Azure Blob Storage Service.</span></span> <span data-ttu-id="0fa94-109">有关详细信息，请参阅[使用 Azure Blob 存储服务执行 SQL Server 备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-109">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  

  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="0fa94-110">优势</span><span class="sxs-lookup"><span data-stu-id="0fa94-110">Benefits</span></span>  
  
-   <span data-ttu-id="0fa94-111">备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库、在备份上运行测试还原过程以及在另一个安全位置存储备份副本可防止可能的灾难性数据丢失。</span><span class="sxs-lookup"><span data-stu-id="0fa94-111">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, running test restores procedures on your backups, and storing copies of backups in a safe, off-site location protects you from potentially catastrophic data loss.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0fa94-112">这是可靠地保护您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="0fa94-112">This is the only way to reliably protect your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data.</span></span>  
  
     <span data-ttu-id="0fa94-113">使用有效的数据库备份，可从多种故障中恢复数据，例如：</span><span class="sxs-lookup"><span data-stu-id="0fa94-113">With valid backups of a database, you can recover your data from many failures, such as:</span></span>  
  
    -   <span data-ttu-id="0fa94-114">介质故障。</span><span class="sxs-lookup"><span data-stu-id="0fa94-114">Media failure.</span></span>  
  
    -   <span data-ttu-id="0fa94-115">用户错误（例如，误删除了某个表）。</span><span class="sxs-lookup"><span data-stu-id="0fa94-115">User errors, for example, dropping a table by mistake.</span></span>  
  
    -   <span data-ttu-id="0fa94-116">硬件故障（例如，磁盘驱动器损坏或服务器报废）。</span><span class="sxs-lookup"><span data-stu-id="0fa94-116">Hardware failures, for example, a damaged disk drive or permanent loss of a server.</span></span>  
  
    -   <span data-ttu-id="0fa94-117">自然灾难。</span><span class="sxs-lookup"><span data-stu-id="0fa94-117">Natural disasters.</span></span> <span data-ttu-id="0fa94-118">通过使用 SQL Server 备份到 Azure Blob 存储服务，可以在本地位置之外的其他区域创建一个站外备份，这样在发生影响本地位置的自然灾难时仍可以使用数据库。</span><span class="sxs-lookup"><span data-stu-id="0fa94-118">By using SQL Server Backup to Azure Blob storage service, you can create an off-site backup in a different region than your on-premises location, to use in the event of a natural disaster affecting your on-premises location.</span></span>  
  
-   <span data-ttu-id="0fa94-119">此外，数据库备份对于进行日常管理（如将数据库从一台服务器复制到另一台服务器、设置 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或数据库镜像以及进行存档）非常有用。</span><span class="sxs-lookup"><span data-stu-id="0fa94-119">Additionally, backups of a database are useful for routine administrative purposes, such as copying a database from one server to another, setting up [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring, and archiving.</span></span>  
  

  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="0fa94-120">组件和概念</span><span class="sxs-lookup"><span data-stu-id="0fa94-120">Components and Concepts</span></span>  
 <span data-ttu-id="0fa94-121">备份 [动词] (back up)</span><span class="sxs-lookup"><span data-stu-id="0fa94-121">back up [verb]</span></span>  
 <span data-ttu-id="0fa94-122">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库或其事务日志中将数据或日志记录复制到备份设备（如磁盘），以创建数据备份或日志备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-122">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="0fa94-123">备份 [名词] (backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-123">backup [noun]</span></span>  
 <span data-ttu-id="0fa94-124">可用于在出现故障后还原或恢复数据的数据副本。</span><span class="sxs-lookup"><span data-stu-id="0fa94-124">A copy of data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="0fa94-125">数据库备份还可用于将数据库副本还原到新位置。</span><span class="sxs-lookup"><span data-stu-id="0fa94-125">Backups of a database can also be used to restore a copy the database to a new location.</span></span>  
  
 <span data-ttu-id="0fa94-126">备份设备 (backup device)</span><span class="sxs-lookup"><span data-stu-id="0fa94-126">backup device</span></span>  
 <span data-ttu-id="0fa94-127">要写入 SQL Server 备份及能从中还原这些备份的磁盘或磁带设备。</span><span class="sxs-lookup"><span data-stu-id="0fa94-127">A disk or tape device to which SQL Server backups are written and from which they can be restored.</span></span> <span data-ttu-id="0fa94-128">SQL Server 备份也可以写入 Azure Blob 存储服务，并且使用 URL  格式来指定备份文件的目标和名称。</span><span class="sxs-lookup"><span data-stu-id="0fa94-128">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="0fa94-129">有关详细信息，请参阅[使用 Azure Blob 存储服务执行 SQL Server 备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-129">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="0fa94-130">备份介质</span><span class="sxs-lookup"><span data-stu-id="0fa94-130">backup media</span></span>  
 <span data-ttu-id="0fa94-131">已写入一个或多个备份的一个或多个磁带或磁盘文件。</span><span class="sxs-lookup"><span data-stu-id="0fa94-131">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 <span data-ttu-id="0fa94-132">数据备份 (data backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-132">data backup</span></span>  
 <span data-ttu-id="0fa94-133">完整数据库的数据备份（数据库备份）、部分数据库的数据备份（部分备份）或一组数据文件或文件组（文件备份）。</span><span class="sxs-lookup"><span data-stu-id="0fa94-133">A backup of data in a complete database (a database backup), a partial database ( a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 <span data-ttu-id="0fa94-134">数据库备份 (database backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-134">database backup</span></span>  
 <span data-ttu-id="0fa94-135">数据库的备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-135">A backup of a database.</span></span> <span data-ttu-id="0fa94-136">完整数据库备份表示备份完成时的整个数据库。</span><span class="sxs-lookup"><span data-stu-id="0fa94-136">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="0fa94-137">差异数据库备份只包含自最近完整备份以来对数据库所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0fa94-137">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 <span data-ttu-id="0fa94-138">差异备份 (differential backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-138">differential backup</span></span>  
 <span data-ttu-id="0fa94-139">一种数据备份，基于完整数据库或部分数据库或一组数据文件或文件组（差异基准）的最新完整备份，并且仅包含自确定差异基准以来发生更改的数据。</span><span class="sxs-lookup"><span data-stu-id="0fa94-139">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the differential base) and that contains only the data that has changed since that base.</span></span>  
  
 <span data-ttu-id="0fa94-140">完整备份 (full backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-140">full backup</span></span>  
 <span data-ttu-id="0fa94-141">一种数据备份，包含特定数据库或者一组特定的文件组或文件中的所有数据，以及可以恢复这些数据的足够的日志。</span><span class="sxs-lookup"><span data-stu-id="0fa94-141">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 <span data-ttu-id="0fa94-142">日志备份 (log backup)</span><span class="sxs-lookup"><span data-stu-id="0fa94-142">log backup</span></span>  
 <span data-ttu-id="0fa94-143">包括以前日志备份中未备份的所有日志记录的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-143">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="0fa94-144">（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="0fa94-144">(full recovery model)</span></span>  
  
 <span data-ttu-id="0fa94-145">recover</span><span class="sxs-lookup"><span data-stu-id="0fa94-145">recover</span></span>  
 <span data-ttu-id="0fa94-146">将数据库恢复到稳定且一致的状态。</span><span class="sxs-lookup"><span data-stu-id="0fa94-146">To return a database to a stable and consistent state.</span></span>  
  
 <span data-ttu-id="0fa94-147">recovery</span><span class="sxs-lookup"><span data-stu-id="0fa94-147">recovery</span></span>  
 <span data-ttu-id="0fa94-148">将数据库恢复到事务一致状态的数据库启动阶段或 Restore With Recovery 阶段。</span><span class="sxs-lookup"><span data-stu-id="0fa94-148">A phase of database startup or of a restore with recovery that brings the database into a transaction-consistent state.</span></span>  
  
 <span data-ttu-id="0fa94-149">恢复模式</span><span class="sxs-lookup"><span data-stu-id="0fa94-149">recovery model</span></span>  
 <span data-ttu-id="0fa94-150">用于控制数据库上的事务日志维护的数据库属性。</span><span class="sxs-lookup"><span data-stu-id="0fa94-150">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="0fa94-151">有三种恢复模式：简单恢复模式、完整恢复模式和大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-151">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="0fa94-152">数据库的恢复模式确定其备份和还原要求。</span><span class="sxs-lookup"><span data-stu-id="0fa94-152">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 <span data-ttu-id="0fa94-153">还原</span><span class="sxs-lookup"><span data-stu-id="0fa94-153">restore</span></span>  
 <span data-ttu-id="0fa94-154">一种包括多个阶段的过程，用于将指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份中的所有数据和日志页复制到指定数据库，然后通过应用记录的更改使该数据在时间上向前移动，以前滚备份中记录的所有事务。</span><span class="sxs-lookup"><span data-stu-id="0fa94-154">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  

  
##  <a name="introduction-to-backup-and-restore-strategies"></a><a name="BnrStrategies"></a><span data-ttu-id="0fa94-155">备份和还原策略简介</span><span class="sxs-lookup"><span data-stu-id="0fa94-155">Introduction to Backup and Restore Strategies</span></span>  
 <span data-ttu-id="0fa94-156">备份和还原数据必须根据特定环境进行自定义，并且必须使用可用资源。</span><span class="sxs-lookup"><span data-stu-id="0fa94-156">Backing up and restoring data must be customized to a particular environment and must work with the available resources.</span></span> <span data-ttu-id="0fa94-157">因此，可靠使用备份和还原以实现恢复需要有一个备份和还原策略。</span><span class="sxs-lookup"><span data-stu-id="0fa94-157">Therefore, a reliable use of backup and restore for recovery requires a backup and restore strategy.</span></span> <span data-ttu-id="0fa94-158">设计良好的备份和还原策略在考虑到特定业务要求的同时，可以尽量提高数据的可用性并尽量减少数据的丢失。</span><span class="sxs-lookup"><span data-stu-id="0fa94-158">A well-designed backup and restore strategy maximizes data availability and minimizes data loss, while considering your particular business requirements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0fa94-159">请将数据库和备份放置在不同的设备上。</span><span class="sxs-lookup"><span data-stu-id="0fa94-159">Place the database and backups on separate devices.</span></span> <span data-ttu-id="0fa94-160">否则，如果包含数据库的设备失败，备份也将不可用。</span><span class="sxs-lookup"><span data-stu-id="0fa94-160">Otherwise, if the device containing the database fails, your backups will be unavailable.</span></span> <span data-ttu-id="0fa94-161">此外，将数据和备份放置在不同的设备上还可以提高写入备份和使用数据库时的 I/O 性能。</span><span class="sxs-lookup"><span data-stu-id="0fa94-161">Placing the data and backups on separate devices also enhances the I/O performance for both writing backups and the production use of the database.</span></span>  
  
 <span data-ttu-id="0fa94-162">备份和还原策略包含备份部分和还原部分。</span><span class="sxs-lookup"><span data-stu-id="0fa94-162">A backup and restore strategy contains a backup portion and a restore portion.</span></span> <span data-ttu-id="0fa94-163">策略的备份部分定义备份的类型和频率、备份所需硬件的特性和速度、备份的测试方法以及备份介质的存储位置和方法（包括安全注意事项）。</span><span class="sxs-lookup"><span data-stu-id="0fa94-163">The backup part of the strategy defines the type and frequency of backups, the nature and speed of the hardware that is required for them, how backups are to be tested, and where and how backup media is to be stored (including security considerations).</span></span> <span data-ttu-id="0fa94-164">策略的还原部分定义负责执行还原的人员以及如何执行还原以满足数据库可用性和尽量减少数据丢失的目标。</span><span class="sxs-lookup"><span data-stu-id="0fa94-164">The restore part of the strategy defines who is responsible for performing restores and how restores should be performed to meet your goals for availability of the database and for minimizing data loss.</span></span> <span data-ttu-id="0fa94-165">建议您将备份和还原过程记录下来并在运行手册中保留记录文档的副本。</span><span class="sxs-lookup"><span data-stu-id="0fa94-165">We recommend that you document your backup and restore procedures and keep a copy of the documentation in your run book.</span></span>  
  
 <span data-ttu-id="0fa94-166">设计有效的备份和还原策略需要仔细计划、实现和测试。</span><span class="sxs-lookup"><span data-stu-id="0fa94-166">Designing an effective backup and restore strategy requires careful planning, implementation, and testing.</span></span> <span data-ttu-id="0fa94-167">测试是必需环节。</span><span class="sxs-lookup"><span data-stu-id="0fa94-167">Testing is required.</span></span> <span data-ttu-id="0fa94-168">直到成功还原了还原策略中所有组合内的备份后，才会生成备份策略。</span><span class="sxs-lookup"><span data-stu-id="0fa94-168">You do not have a backup strategy until you have successfully restored backups in all the combinations that are included in your restore strategy.</span></span> <span data-ttu-id="0fa94-169">必须考虑各种因素。</span><span class="sxs-lookup"><span data-stu-id="0fa94-169">You must consider a variety of factors.</span></span> <span data-ttu-id="0fa94-170">其中包括：</span><span class="sxs-lookup"><span data-stu-id="0fa94-170">These include the following:</span></span>  
  
-   <span data-ttu-id="0fa94-171">您的组织对数据库的生产目标，尤其是对可用性和防止数据丢失的要求。</span><span class="sxs-lookup"><span data-stu-id="0fa94-171">The production goals of your organization for the databases, especially the requirements for availability and protection of data from loss.</span></span>  
  
-   <span data-ttu-id="0fa94-172">每个数据库的特性，包括：大小、使用模式、内容特性以及数据要求等。</span><span class="sxs-lookup"><span data-stu-id="0fa94-172">The nature of each of your databases: its size, its usage patterns, the nature of its content, the requirements for its data, and so on.</span></span>  
  
-   <span data-ttu-id="0fa94-173">对资源的约束，例如：硬件、人员、备份介质的存储空间以及所存储介质的物理安全性等。</span><span class="sxs-lookup"><span data-stu-id="0fa94-173">Constraints on resources, such as: hardware, personnel, space for storing backup media, the physical security of the stored media, and so on.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0fa94-174">在 64 位和 32 位环境中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘存储格式均相同。</span><span class="sxs-lookup"><span data-stu-id="0fa94-174">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="0fa94-175">因此，可以将 32 位环境中的备份还原到 64 位环境中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0fa94-175">Therefore, backup and restore work across 32-bit and 64-bit environments.</span></span> <span data-ttu-id="0fa94-176">在运行在某个环境中的服务器实例上，可以还原在运行在另一个环境中的服务器实例上创建的备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-176">A backup created on a server instance running in one environment can be restored on a server instance that runs in the other environment.</span></span>  
  

  
### <a name="impact-of-the-recovery-model-on-backup-and-restore"></a><span data-ttu-id="0fa94-177">恢复模式对备份和还原的影响</span><span class="sxs-lookup"><span data-stu-id="0fa94-177">Impact of the Recovery Model on Backup and Restore</span></span>  
 <span data-ttu-id="0fa94-178">备份和还原操作发生在恢复模式的上下文中。</span><span class="sxs-lookup"><span data-stu-id="0fa94-178">Backup and restore operations occur within the context of a recovery model.</span></span> <span data-ttu-id="0fa94-179">恢复模式是一种数据库属性，用于控制事务日志的管理方式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-179">A recovery model is a database property that controls how the transaction log is managed.</span></span> <span data-ttu-id="0fa94-180">此外，数据库的恢复模式还决定数据库支持的备份类型和还原方案。</span><span class="sxs-lookup"><span data-stu-id="0fa94-180">Also, the recovery model of a database determines what types of backups and what restore scenarios are supported for the database.</span></span> <span data-ttu-id="0fa94-181">通常，数据库使用简单恢复模式或完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-181">Typically a database uses either the simple recovery model or the full recovery model.</span></span> <span data-ttu-id="0fa94-182">可以在执行大容量操作之前切换到大容量日志恢复模式，以补充完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-182">The full recovery model can be supplemented by switching to the bulk-logged recovery model before bulk operations.</span></span> <span data-ttu-id="0fa94-183">有关这些恢复模式以及它们是如何影响事务日志管理方式的说明，请参阅[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-183">For an introduction to these recovery models and how they affect transaction log management, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="0fa94-184">数据库的最佳恢复模式取决于您的业务要求。</span><span class="sxs-lookup"><span data-stu-id="0fa94-184">The best choice of recovery model for the database depends on your business requirements.</span></span> <span data-ttu-id="0fa94-185">若要免去事务日志管理工作并简化备份和还原，请使用简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-185">To avoid transaction log management and simplify backup and restore, use the simple recovery model.</span></span> <span data-ttu-id="0fa94-186">若要在管理开销一定的情况下使工作丢失的可能性降到最低，请使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="0fa94-186">To minimize work-loss exposure, at the cost of administrative overhead, use the full recovery model.</span></span> <span data-ttu-id="0fa94-187">有关恢复模式对备份和还原存在哪些影响的信息，请参阅 [备份概述 (SQL Server)](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-187">For information about the effect of recovery models on backup and restore, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
### <a name="design-the-backup-strategy"></a><span data-ttu-id="0fa94-188">设计备份策略</span><span class="sxs-lookup"><span data-stu-id="0fa94-188">Design the Backup Strategy</span></span>  
 <span data-ttu-id="0fa94-189">当为特定数据库选择了满足业务要求的恢复模式后，需要计划并实现相应的备份策略。</span><span class="sxs-lookup"><span data-stu-id="0fa94-189">After you have selected a recovery model that meets your business requirements for a specific database, you have to plan and implement a corresponding backup strategy.</span></span> <span data-ttu-id="0fa94-190">最佳备份策略取决于各种因素，以下因素尤其重要：</span><span class="sxs-lookup"><span data-stu-id="0fa94-190">The optimal backup strategy depends on a variety of factors, of which the following are especially significant:</span></span>  
  
-   <span data-ttu-id="0fa94-191">一天中应用程序访问数据库的时间有多长？</span><span class="sxs-lookup"><span data-stu-id="0fa94-191">How many hours a day do applications have to access the database?</span></span>  
  
     <span data-ttu-id="0fa94-192">如果存在一个可预测的非高峰时段，则建议您将完整数据库备份安排在此时段。</span><span class="sxs-lookup"><span data-stu-id="0fa94-192">If there is a predictable off-peak period, we recommend that you schedule full database backups for that period.</span></span>  
  
-   <span data-ttu-id="0fa94-193">更改和更新可能发生的频率如何？</span><span class="sxs-lookup"><span data-stu-id="0fa94-193">How frequently are changes and updates likely to occur?</span></span>  
  
     <span data-ttu-id="0fa94-194">如果更改经常发生，请考虑下列事项：</span><span class="sxs-lookup"><span data-stu-id="0fa94-194">If changes are frequent, consider the following:</span></span>  
  
    -   <span data-ttu-id="0fa94-195">在简单恢复模式下，请考虑将差异备份安排在完整数据库备份之间。</span><span class="sxs-lookup"><span data-stu-id="0fa94-195">Under the simple recovery model, consider scheduling differential backups between full database backups.</span></span> <span data-ttu-id="0fa94-196">差异备份只能捕获自上次完整数据库备份之后的更改。</span><span class="sxs-lookup"><span data-stu-id="0fa94-196">A differential backup captures only the changes since the last full database backup.</span></span>  
  
    -   <span data-ttu-id="0fa94-197">在完整恢复模式下，应安排经常的日志备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-197">Under the full recovery model, you should schedule frequent log backups.</span></span> <span data-ttu-id="0fa94-198">在完整备份之间安排差异备份可减少数据还原后需要还原的日志备份数，从而缩短还原时间。</span><span class="sxs-lookup"><span data-stu-id="0fa94-198">Scheduling differential backups between full backups can reduce restore time by reducing the number of log backups you have to restore after restoring the data.</span></span>  
  
-   <span data-ttu-id="0fa94-199">可能只是更改数据库的小部分内容，还是需要更改数据库的大部分内容？</span><span class="sxs-lookup"><span data-stu-id="0fa94-199">Are changes likely to occur in only a small part of the database or in a large part of the database?</span></span>  
  
     <span data-ttu-id="0fa94-200">对于更改集中于部分文件或文件组的大型数据库，部分备份和/或文件备份非常有用。</span><span class="sxs-lookup"><span data-stu-id="0fa94-200">For a large database in which changes are concentrated in a part of the files or filegroups, partial backups and or file backups can be useful.</span></span> <span data-ttu-id="0fa94-201">有关详细信息，请参阅[部分备份 (SQL Server)](partial-backups-sql-server.md) 和[完整文件备份 (SQL Server)](full-file-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-201">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md) and [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0fa94-202">完整数据库备份需要多少磁盘空间？</span><span class="sxs-lookup"><span data-stu-id="0fa94-202">How much disk space will a full database backup require?</span></span>  
  
     <span data-ttu-id="0fa94-203">有关详细信息，请参阅本部分后面的 [估计完整数据库备份的大小](#EstimateDbBuSize)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-203">For more information, see [Estimating the Size of a Full Database Backup](#EstimateDbBuSize), later in this section.</span></span>  
  
####  <a name="estimate-the-size-of-a-full-database-backup"></a><a name="EstimateDbBuSize"></a><span data-ttu-id="0fa94-204">估计完整数据库备份的大小</span><span class="sxs-lookup"><span data-stu-id="0fa94-204">Estimate the Size of a Full Database Backup</span></span>  
 <span data-ttu-id="0fa94-205">在实现备份与还原策略之前，应当估计完整数据库备份将使用的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="0fa94-205">Before you implement a backup and restore strategy, you should estimate how much disk space a full database backup will use.</span></span> <span data-ttu-id="0fa94-206">备份操作会将数据库中的数据复制到备份文件。</span><span class="sxs-lookup"><span data-stu-id="0fa94-206">The backup operation copies the data in the database to the backup file.</span></span> <span data-ttu-id="0fa94-207">备份仅包含数据库中的实际数据，而不包含任何未使用的空间。</span><span class="sxs-lookup"><span data-stu-id="0fa94-207">The backup contains only the actual data in the database and not any unused space.</span></span> <span data-ttu-id="0fa94-208">因此，备份通常小于数据库本身。</span><span class="sxs-lookup"><span data-stu-id="0fa94-208">Therefore, the backup is usually smaller than the database itself.</span></span> <span data-ttu-id="0fa94-209">你可以使用 **sp_spaceused** 系统存储过程估计完整数据库备份的大小。</span><span class="sxs-lookup"><span data-stu-id="0fa94-209">You can estimate the size of a full database backup by using the **sp_spaceused** system stored procedure.</span></span> <span data-ttu-id="0fa94-210">有关详细信息，请参阅 [sp_spaceused (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-210">For more information, see [sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql).</span></span>  
  
### <a name="schedule-backups"></a><span data-ttu-id="0fa94-211">计划备份</span><span class="sxs-lookup"><span data-stu-id="0fa94-211">Schedule Backups</span></span>  
 <span data-ttu-id="0fa94-212">执行备份操作对运行中的事务影响很小，因此可以在正常操作过程中执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="0fa94-212">Performing a backup operation has minimal effect on transactions that are running; therefore, backup operations can be run during regular operations.</span></span> <span data-ttu-id="0fa94-213">您可以在对生产工作负荷的影响很小的情况下执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份。</span><span class="sxs-lookup"><span data-stu-id="0fa94-213">You can perform a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup with minimal effect on production workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fa94-214">有关备份过程中的并发限制的信息，请参阅 [备份概述 (SQL Server)](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-214">For information about concurrency restrictions during backup, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="0fa94-215">确定所需的备份类型和必须执行每种备份类型的频率后，建议您将定期备份计划为数据库维护计划的一部分。</span><span class="sxs-lookup"><span data-stu-id="0fa94-215">After you decide what types of backups you require and how frequently you have to perform each type, we recommend that you schedule regular backups as part of a database maintenance plan for the database.</span></span> <span data-ttu-id="0fa94-216">有关维护计划以及如何为数据库备份和日志备份创建维护计划的信息，请参阅 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="0fa94-216">For information about maintenance plans and how to create them for database backups and log backups, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
### <a name="test-your-backups"></a><span data-ttu-id="0fa94-217">测试备份</span><span class="sxs-lookup"><span data-stu-id="0fa94-217">Test Your Backups</span></span>  
 <span data-ttu-id="0fa94-218">直到完成备份测试后，才会生成还原策略。</span><span class="sxs-lookup"><span data-stu-id="0fa94-218">You do not have a restore strategy until you have tested your backups.</span></span> <span data-ttu-id="0fa94-219">必须通过将数据库副本还原到测试系统，针对每个数据库的备份策略进行全面测试。</span><span class="sxs-lookup"><span data-stu-id="0fa94-219">It is very important to thoroughly test your backup strategy for each of your databases by restoring a copy of the database onto a test system.</span></span> <span data-ttu-id="0fa94-220">您必须对每种要使用的备份类型进行还原测试。</span><span class="sxs-lookup"><span data-stu-id="0fa94-220">You must test restoring every type of backup that you intend to use.</span></span>  
  
 <span data-ttu-id="0fa94-221">建议您为每个数据库维护一个操作手册。</span><span class="sxs-lookup"><span data-stu-id="0fa94-221">We recommend that you maintain an operations manual for each database.</span></span> <span data-ttu-id="0fa94-222">此操作手册应记录备份的位置、备份设备名称（如果有），以及还原测试备份所需的时间。</span><span class="sxs-lookup"><span data-stu-id="0fa94-222">This operations manual should document the location of the backups, backup device names (if any), and the amount of time that is required to restore the test backups.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0fa94-223">相关任务</span><span class="sxs-lookup"><span data-stu-id="0fa94-223">Related Tasks</span></span>  
  
### <a name="scheduling-backup-jobs"></a><span data-ttu-id="0fa94-224">计划备份作业</span><span class="sxs-lookup"><span data-stu-id="0fa94-224">Scheduling Backup Jobs</span></span>  
  
-   [<span data-ttu-id="0fa94-225">创建维护计划</span><span class="sxs-lookup"><span data-stu-id="0fa94-225">Create a Maintenance Plan</span></span>](../maintenance-plans/create-a-maintenance-plan.md)  
  
-   [<span data-ttu-id="0fa94-226">创建作业</span><span class="sxs-lookup"><span data-stu-id="0fa94-226">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="0fa94-227">安排作业计划</span><span class="sxs-lookup"><span data-stu-id="0fa94-227">Schedule a Job</span></span>](../../ssms/agent/schedule-a-job.md)  
  
### <a name="working-with-backup-devices-and-backup-media"></a><span data-ttu-id="0fa94-228">使用备份设备和备份介质</span><span class="sxs-lookup"><span data-stu-id="0fa94-228">Working with Backup Devices and Backup Media</span></span>  
  
-   [<span data-ttu-id="0fa94-229">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-229">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-230">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-230">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-231">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-231">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-232">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-232">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-233">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-233">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-234">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-234">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-235">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-236">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-236">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-237">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-237">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
### <a name="creating-backups"></a><span data-ttu-id="0fa94-238">创建备份</span><span class="sxs-lookup"><span data-stu-id="0fa94-238">Creating Backups</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fa94-239">对于部分备份或仅复制备份，必须分别使用带 PARTIAL 或 COPY_ONLY 选项的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="0fa94-239">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
 <span data-ttu-id="0fa94-240">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0fa94-240">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0fa94-241">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-241">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-242">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-242">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-243">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-243">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-244">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-244">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="0fa94-245">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0fa94-245">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0fa94-246">使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-246">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="0fa94-247">在数据库损坏时备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-247">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-248">在备份或还原期间启用或禁用备份校验和 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-248">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-249">指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-249">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  

  
### <a name="restoring-data-backups"></a><span data-ttu-id="0fa94-250">还原数据备份</span><span class="sxs-lookup"><span data-stu-id="0fa94-250">Restoring Data Backups</span></span>  
 <span data-ttu-id="0fa94-251">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0fa94-251">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0fa94-252">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa94-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="0fa94-253">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-253">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-254">还原差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-254">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-255">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-255">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
 <span data-ttu-id="0fa94-256">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0fa94-256">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0fa94-257">在简单恢复模式下还原数据库备份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-257">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="0fa94-258">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-258">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="0fa94-259">在现有文件上还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-259">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-260">将文件还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-260">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-261">还原 master 数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-261">Restore the master Database &#40;Transact-SQL&#41;</span></span>](restore-the-master-database-transact-sql.md)  
  

  
### <a name="restoring-transaction-logs-full-recovery-model"></a><span data-ttu-id="0fa94-262">还原事务日志（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="0fa94-262">Restoring Transaction Logs (Full Recovery Model)</span></span>  
 <span data-ttu-id="0fa94-263">**使用 SQL Server Management Studio**</span><span class="sxs-lookup"><span data-stu-id="0fa94-263">**Using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="0fa94-264">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0fa94-264">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0fa94-265">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-265">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="0fa94-266">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="0fa94-266">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
 <span data-ttu-id="0fa94-267">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0fa94-267">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0fa94-268">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="0fa94-268">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  

  
### <a name="additional-restore-tasks"></a><span data-ttu-id="0fa94-269">其他还原任务</span><span class="sxs-lookup"><span data-stu-id="0fa94-269">Additional Restore Tasks</span></span>  
 <span data-ttu-id="0fa94-270">**使用 Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="0fa94-270">**Using Transact-SQL**</span></span>  
  
-   [<span data-ttu-id="0fa94-271">重新启动中断的还原操作 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-271">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](restart-an-interrupted-restore-operation-transact-sql.md)  
  
-   [<span data-ttu-id="0fa94-272">恢复数据库但不还原数据 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0fa94-272">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="0fa94-273">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fa94-273">See Also</span></span>  
 <span data-ttu-id="0fa94-274">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-274">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="0fa94-275">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-275">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="0fa94-276">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0fa94-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0fa94-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0fa94-277">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="0fa94-278">[备份和还原 Analysis Services 数据库](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span><span class="sxs-lookup"><span data-stu-id="0fa94-278">[Backup and Restore of Analysis Services Databases](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases) </span></span>  
 <span data-ttu-id="0fa94-279">[备份和还原全文目录和索引](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-279">[Back Up and Restore Full-Text Catalogs and Indexes](../search/back-up-and-restore-full-text-catalogs-and-indexes.md) </span></span>  
 <span data-ttu-id="0fa94-280">[备份和还原复制的数据库](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-280">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 <span data-ttu-id="0fa94-281">[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-281">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="0fa94-282">[恢复模式 (SQL Server)](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fa94-282">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 [<span data-ttu-id="0fa94-283">媒体集、媒体簇和备份集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fa94-283">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
