---
title: " (AlwaysOn 可用性组向导) 选择 \"初始数据同步\" 页 |Microsoft Docs"
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693101"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a><span data-ttu-id="f4288-102">“选择初始数据同步”页（AlwaysOn 可用性组向导）</span><span class="sxs-lookup"><span data-stu-id="f4288-102">Select Initial Data Synchronization Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="f4288-103">使用 AlwaysOn **“选择初始数据同步”** 页可为新的辅助数据库的初始数据同步指示您的首选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-103">Use the AlwaysOn **Select Initial Data Synchronization** page to indicate your preference for initial data synchronization of new secondary databases.</span></span> <span data-ttu-id="f4288-104">此页为三个向导所共有：[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]、[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 和 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4288-104">This page is shared by three wizards-the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and the [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].</span></span>  
  
 <span data-ttu-id="f4288-105">可能的选项包括 **“完全”**、 **“仅加入”** 或 **“跳过初始数据同步”**。</span><span class="sxs-lookup"><span data-stu-id="f4288-105">The possible choices include **Full**, **Join only**, or **Skip initial data synchronization**.</span></span> <span data-ttu-id="f4288-106">选择 **“完全”** 或 **“仅加入”** 之前，确保您的环境符合先决条件。</span><span class="sxs-lookup"><span data-stu-id="f4288-106">Before you select **Full** or **Join only** ensure that your environment meets the prerequisites.</span></span>  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f4288-107">建议</span><span class="sxs-lookup"><span data-stu-id="f4288-107">Recommendations</span></span>  
  
-   <span data-ttu-id="f4288-108">在初始数据同步过程中挂起主数据库的日志备份任务。</span><span class="sxs-lookup"><span data-stu-id="f4288-108">Suspend log backup tasks for the primary databases during initial data synchronization.</span></span>  
  
-   <span data-ttu-id="f4288-109">对于大型数据库，完整备份和还原操作可能占用大量的时间和资源。</span><span class="sxs-lookup"><span data-stu-id="f4288-109">For large database, full backup and restore operations can take extensive time and resources.</span></span> <span data-ttu-id="f4288-110">在这种情况下，我们建议您自行准备辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-110">In such cases, we recommend that you prepare secondary databases yourself.</span></span> <span data-ttu-id="f4288-111">有关详细信息，请参阅本主题后面的 [手动准备辅助数据库](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="f4288-111">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="f4288-112">完全初始数据同步要求您指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="f4288-112">Full initial data synchronization requires you to specify a network share.</span></span> <span data-ttu-id="f4288-113">在使用向导执行完整初始数据同步之前，建议您对网络共享文件夹的访问权限实施安全计划。</span><span class="sxs-lookup"><span data-stu-id="f4288-113">Before you use a wizard to perform full initial data synchronization, we recommend that you implement a security plan for the access permissions on the network share folder.</span></span> <span data-ttu-id="f4288-114">此预防措施很重要，因为备份文件中潜在敏感的数据可由对该文件夹具有“读”权限的任何人访问。</span><span class="sxs-lookup"><span data-stu-id="f4288-114">This precaution is important because potentially sensitive data in the backup file can be accessed by anyone who has a READ permission on the folder.</span></span> <span data-ttu-id="f4288-115">此外，若要保护备份操作和还原操作，建议您对每个承载可用性副本的服务器实例和网络共享文件夹之间的网络通道提供适当的保护。</span><span class="sxs-lookup"><span data-stu-id="f4288-115">Also, to protect your backup and restore operations, we recommend that you secure the network channels between every server instance that hosts an availability replica and the network share folder.</span></span>  
  
     <span data-ttu-id="f4288-116">如果必须高度保护您的备份操作和还原操作，建议您选择 **“仅加入”** 或 **“跳过初始数据同步”** 选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-116">If your backup and restore operations must be highly secured, we recommend that you select either the **Join only** or **Skip initial data synchronization** option.</span></span>  
  
##  <a name="full"></a><a name="Full"></a><span data-ttu-id="f4288-117">达到</span><span class="sxs-lookup"><span data-stu-id="f4288-117">Full</span></span>  
 <span data-ttu-id="f4288-118">对于每个主数据库， **“完全”** 选项将在一个工作流中执行以下若干操作：创建主数据库的完整备份和日志备份、通过在承载辅助副本的每个服务器实例上还原这些备份来创建对应的辅助数据库，以及将每个辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="f4288-118">For each primary database, the **Full** option performs several operations in one workflow:  create a full and log backup of the primary database, create the corresponding secondary databases by restoring these backups on every server instance that is hosting a secondary replica, and join each secondary database to availability group.</span></span>  
  
 <span data-ttu-id="f4288-119">仅当您的环境符合使用完全初始数据同步的以下先决条件且您希望该向导自动启动数据同步时，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-119">Select this option only if your environment meets the following prerequisites for using full initial data synchronization, and you want the wizard to automatically start data synchronization.</span></span>  
  
 <span data-ttu-id="f4288-120">**使用完全初始数据同步的先决条件**</span><span class="sxs-lookup"><span data-stu-id="f4288-120">**Prerequisites for using full initial data synchronization**</span></span>  
  
-   <span data-ttu-id="f4288-121">在承载可用性组的副本的每个服务器实例上，所有数据库文件路径都必须完全相同。</span><span class="sxs-lookup"><span data-stu-id="f4288-121">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4288-122">如果您运行该向导的服务器实例和要承载辅助副本的任何服务器实例之间的备份和还原文件路径不同，</span><span class="sxs-lookup"><span data-stu-id="f4288-122">If the backup and restore file paths differ between the server instance where you run the wizard and any server instance that is to host a secondary replica.</span></span> <span data-ttu-id="f4288-123">必须使用 WITH MOVE 选项手动执行备份和还原操作。</span><span class="sxs-lookup"><span data-stu-id="f4288-123">The backup and restore operations must be performed manually using the WITH MOVE option.</span></span> <span data-ttu-id="f4288-124">有关详细信息，请参阅本主题后面的 [手动准备辅助数据库](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="f4288-124">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="f4288-125">没有任何主数据库名称可存在于承载辅助副本的任何服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="f4288-125">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="f4288-126">这意味着尚没有任何新的辅助数据库可以存在。</span><span class="sxs-lookup"><span data-stu-id="f4288-126">This means that none of the new secondary databases can exist yet.</span></span>  
  
-   <span data-ttu-id="f4288-127">为了使该向导创建并访问备份，需要指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="f4288-127">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="f4288-128">对于主副本，用于启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="f4288-128">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="f4288-129">对于辅助副本，该帐户必须具有对网络共享区的读权限。</span><span class="sxs-lookup"><span data-stu-id="f4288-129">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f4288-130">日志备份将是您的日志备份链的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4288-130">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="f4288-131">适当地存储日志备份文件。</span><span class="sxs-lookup"><span data-stu-id="f4288-131">Store the log backup files appropriately.</span></span>  
  
 <span data-ttu-id="f4288-132">**如果未满足先决条件**</span><span class="sxs-lookup"><span data-stu-id="f4288-132">**If prerequisites are not met**</span></span>  
  
 <span data-ttu-id="f4288-133">向导不能为此可用性组创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-133">The wizard cannot create the secondary databases for this availability group.</span></span> <span data-ttu-id="f4288-134">有关如何准备辅助数据库的详细信息，请参阅本主题后面的 [手动准备辅助数据库](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="f4288-134">For information on how to prepare them, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
 <span data-ttu-id="f4288-135">**如果满足先决条件**</span><span class="sxs-lookup"><span data-stu-id="f4288-135">**If prerequisites are met**</span></span>  
  
 <span data-ttu-id="f4288-136">如果完全满足这些先决条件并且您想要向导执行完全初始数据同步，请选择 **“完全”** 选项并指定网络共享。</span><span class="sxs-lookup"><span data-stu-id="f4288-136">If these prerequisites are all met and you want the wizard to perform full initial data synchronization, select the **Full** option and specify a network share.</span></span> <span data-ttu-id="f4288-137">这将导致向导创建每个所选数据库的完整的数据库和日志备份，并将这些备份放置于您指定的网络共享上。</span><span class="sxs-lookup"><span data-stu-id="f4288-137">This will cause  the wizard to create full database and log backups of every selected database and to place these backups on the network share that you specify.</span></span> <span data-ttu-id="f4288-138">然后，在承载新的辅助副本之一的每个服务器实例上，该向导将通过使用 RESTORE WITH NORECOVERY 还原备份以创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-138">Then, on every server instance that hosts one of the new secondary replicas, the wizard will create the secondary databases by restoring backups using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="f4288-139">创建每个辅助数据库之后，该向导将新的辅助数据库加入可用性组中。</span><span class="sxs-lookup"><span data-stu-id="f4288-139">After creating each of the secondary databases, the wizard will join the new secondary database to the availability group.</span></span> <span data-ttu-id="f4288-140">加入辅助数据库后，将在该数据库上启动数据同步。</span><span class="sxs-lookup"><span data-stu-id="f4288-140">As soon as a secondary database is joined, data synchronizations starts on that database.</span></span>  
  
 <span data-ttu-id="f4288-141">**指定所有副本可访问的共享网络位置**</span><span class="sxs-lookup"><span data-stu-id="f4288-141">**Specify a shared network location accessible by all replicas**</span></span>  
 <span data-ttu-id="f4288-142">若要创建和还原备份，该向导要求您指定一个网络共享。</span><span class="sxs-lookup"><span data-stu-id="f4288-142">To create and restore backups, the wizard requires that you specify a network share.</span></span> <span data-ttu-id="f4288-143">用于在承载可用性副本的每个服务器实例上启动 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帐户必须对网络共享具有读写文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="f4288-143">The account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] on each server instance that will host an availability replica must have read and write file-system permissions on the network share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f4288-144">日志备份将是您的日志备份链的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4288-144">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="f4288-145">适当地存储其备份文件。</span><span class="sxs-lookup"><span data-stu-id="f4288-145">Store their backup files appropriately.</span></span>  
  
##  <a name="join-only"></a><a name="Joinonly"></a><span data-ttu-id="f4288-146">仅联接</span><span class="sxs-lookup"><span data-stu-id="f4288-146">Join only</span></span>  
 <span data-ttu-id="f4288-147">仅当每个承载可用性组的辅助副本的服务器实例上已存在新的辅助数据库时，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-147">Select this option only if the new secondary databases already exist on each server instance that hosts a secondary replica for the availability group.</span></span> <span data-ttu-id="f4288-148">有关准备辅助数据库的信息，请参阅本主题后面的 [手动准备辅助数据库](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="f4288-148">For information about preparing secondary databases, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this section.</span></span>  
  
 <span data-ttu-id="f4288-149">如果您选择 **“仅加入”**，则该向导将尝试将每个现有辅助数据库加入可用性组中。</span><span class="sxs-lookup"><span data-stu-id="f4288-149">If you select **Join only**, the wizard will attempt to join each existing secondary database to the availability group.</span></span>  
  
## <a name="skip-initial-data-synchronization"></a><span data-ttu-id="f4288-150">跳过初始数据同步</span><span class="sxs-lookup"><span data-stu-id="f4288-150">Skip initial data synchronization</span></span>  
 <span data-ttu-id="f4288-151">如果您希望自行执行每个主数据库的数据库备份和日志备份，并将它们还原到每个承载辅助副本的服务器实例，则选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-151">Select this option if you want to perform your own database and log backups of every primary database, restore them to every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="f4288-152">退出向导后，您需要加入每个辅助副本上的每个辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-152">After you exit the wizard, you will then need to join every secondary database on every secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4288-153">有关详细信息，请参阅[启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f4288-153">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a><span data-ttu-id="f4288-154">手动准备辅助数据库</span><span class="sxs-lookup"><span data-stu-id="f4288-154">To Prepare Secondary Databases Manually</span></span>  
 <span data-ttu-id="f4288-155">若要独立于任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 向导准备辅助数据库，可以使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="f4288-155">To prepare secondary databases independently of any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard, you can use either of the following approaches:</span></span>  
  
-   <span data-ttu-id="f4288-156">使用 RESTORE WITH NORECOVERY 手动还原主数据库的最新数据库备份，然后使用 RESTORE WITH NORECOVERY 还原各个后续日志备份。</span><span class="sxs-lookup"><span data-stu-id="f4288-156">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="f4288-157">如果主数据库和辅助数据库具有不同的文件路径，则必须使用 WITH MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-157">If the primary and secondary databases have different file paths, you must use the WITH MOVE option.</span></span> <span data-ttu-id="f4288-158">在每个承载可用性组的辅助副本的服务器实例上执行此还原序列。</span><span class="sxs-lookup"><span data-stu-id="f4288-158">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  <span data-ttu-id="f4288-159">您可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 执行这些备份和还原操作。</span><span class="sxs-lookup"><span data-stu-id="f4288-159">You can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to perform these backup and restore operations.</span></span>  
  
     <span data-ttu-id="f4288-160">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="f4288-160">**For more information:**</span></span>  
  
     [<span data-ttu-id="f4288-161">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4288-161">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   <span data-ttu-id="f4288-162">如果您在将一个或多个日志传送主数据库添加到可用性组，则可能能够将一个或多个相应的辅助数据库从日志传送迁移到 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f4288-162">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="f4288-163">有关详细信息，请参阅[从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="f4288-163">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4288-164">在您为可用性组创建了所有辅助数据库后，如果您想要在辅助副本上执行备份，将需要重新配置该可用性组的自动备份首选项。</span><span class="sxs-lookup"><span data-stu-id="f4288-164">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
     <span data-ttu-id="f4288-165">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="f4288-165">**For more information:**</span></span>  
  
     [<span data-ttu-id="f4288-166">从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server 的先决条件&#41;</span><span class="sxs-lookup"><span data-stu-id="f4288-166">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [<span data-ttu-id="f4288-167">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4288-167">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="f4288-168">创建辅助数据库后，将所有当前日志备份应用于新的辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-168">After creating a secondary database, apply all current log backups to the new secondary database.</span></span>  
  
 <span data-ttu-id="f4288-169">或者，您也可以在运行向导前准备所有辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="f4288-169">Optionally, you can prepare all the secondary databases before you run the wizard.</span></span> <span data-ttu-id="f4288-170">然后，在向导的 **“指定初始数据同步”** 页上，选择 **“仅加入”** 选项以便自动将新的辅助数据库加入该可用性组。</span><span class="sxs-lookup"><span data-stu-id="f4288-170">Then, on the wizard's **Specify Initial Data Synchronization** page, select **Join only** to automatically join your new secondary databases to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="f4288-171">相关任务</span><span class="sxs-lookup"><span data-stu-id="f4288-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f4288-172">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4288-172">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4288-173">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4288-173">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4288-174">使用“将数据库添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4288-174">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="f4288-175">使用故障转移可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4288-175">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4288-176">启动 AlwaysOn 辅助数据库的数据移动 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4288-176">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="f4288-177">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4288-177">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4288-178">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4288-178">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4288-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4288-179">See Also</span></span>  
 [<span data-ttu-id="f4288-180">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="f4288-180">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
