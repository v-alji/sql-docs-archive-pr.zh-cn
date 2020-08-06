---
title: 使用快照初始化订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b776e71e9d1197bc174169aee8ccf692884308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578076"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a><span data-ttu-id="d9e0a-102">使用快照初始化订阅</span><span class="sxs-lookup"><span data-stu-id="d9e0a-102">Initialize a Subscription with a Snapshot</span></span>
  <span data-ttu-id="d9e0a-103">在创建发布后，通常会创建一个初始快照，并将其复制到快照文件夹中（默认情况下，使用新建发布向导创建的合并发布将会执行此操作）。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-103">After a publication has been created, an initial snapshot is typically created and copied to the snapshot folder (this occurs by default for merge publications created with the New Publication Wizard).</span></span> <span data-ttu-id="d9e0a-104">此快照然后将在订阅的初始同步期间由分发代理（对于事务发布和快照发布）或合并代理（对于合并发布）应用于订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-104">It is then applied to the Subscriber by the Distribution Agent (for transactional and snapshot publications) or the Merge Agent (for merge publications) during the initial synchronization of the subscription.</span></span> <span data-ttu-id="d9e0a-105">快照过程取决于发布的类型：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-105">The snapshot process depends on the type of publication:</span></span>  
  
-   <span data-ttu-id="d9e0a-106">如果快照用于快照发布、事务发布或不使用参数化筛选器的合并发布，那么快照将包含大容量复制程序 (bcp) 文件中的架构和数据，还包含进行复制所必需的约束、扩展属性、索引、触发器和系统表。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-106">If the snapshot is for a snapshot publication, a transactional publication, or a merge publication that doesn't use parameterized filters, the snapshot contains the schema and data in bulk copy program (bcp) files, as well as constraints, extended properties, indexes, triggers, and the system tables necessary for replication.</span></span> <span data-ttu-id="d9e0a-107">有关创建和应用快照的详细信息，请参阅[创建并应用快照](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-107">For more information about creating and applying the snapshot, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
-   <span data-ttu-id="d9e0a-108">如果快照用于使用参数化筛选器的合并发布，则创建快照的过程包括两部分。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-108">If the snapshot is for a merge publication that uses parameterized filters, the snapshot is created using a two-part process.</span></span> <span data-ttu-id="d9e0a-109">首先创建包含复制脚本和已发布对象的架构（但不包含数据）的架构快照。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-109">First a schema snapshot is created that contains the replication scripts and the schema of the published objects, but not the data.</span></span> <span data-ttu-id="d9e0a-110">然后，使用包括脚本、从架构快照复制的架构以及属于订阅分区的数据的快照初始化每个订阅。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-110">Each subscription is then initialized with a snapshot that includes the scripts and schema copied from the schema snapshot and the data that belongs to the subscription's partition.</span></span> <span data-ttu-id="d9e0a-111">有关详细信息，请参阅 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-111">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="d9e0a-112">根据复制的类型以及发布中包含的项目，快照可由不同的文件组成。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-112">The snapshot consists of different files depending on the type of replication and the articles in your publication.</span></span> <span data-ttu-id="d9e0a-113">这些文件复制到配置分发服务器时指定的默认快照文件夹中，或创建发布时指定的备用快照文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-113">These files are copied to the default snapshot folder specified when the Distributor was configured or the alternate snapshot folder specified when the publication was created.</span></span>  
  
|<span data-ttu-id="d9e0a-114">复制类型</span><span class="sxs-lookup"><span data-stu-id="d9e0a-114">Type of Replication</span></span>|<span data-ttu-id="d9e0a-115">常用快照文件</span><span class="sxs-lookup"><span data-stu-id="d9e0a-115">Common Snapshot Files</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="d9e0a-116">快照复制或事务复制</span><span class="sxs-lookup"><span data-stu-id="d9e0a-116">Snapshot Replication or Transactional Replication</span></span>|<span data-ttu-id="d9e0a-117">架构 (.sch)、数据 (.bcp)、约束和索引 (.dri)、约束 (.idx)、触发器 (.trg)（只用于更新订阅服务器）、压缩的快照文件 (.cab)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-117">schema (.sch); data (.bcp); constraints and indexes (.dri); constraints (.idx); triggers (.trg):for updating Subscribers only; compressed snapshot files (.cab).</span></span>|  
|<span data-ttu-id="d9e0a-118">合并复制</span><span class="sxs-lookup"><span data-stu-id="d9e0a-118">Merge Replication</span></span>|<span data-ttu-id="d9e0a-119">架构 (.sch)、数据 (.bcp)、约束和索引 (.dri)、触发器 (.trg)、系统表数据 (.sys)、冲突表 (.cft)、压缩的快照文件 (.cab)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-119">schema (.sch); data (.bcp); constraints and indexes (.dri); triggers (.trg); system table data (.sys); conflict tables (.cft); compressed snapshot files (.cab).</span></span>|  
  
 <span data-ttu-id="d9e0a-120">如果快照传输在任一点中断，它将自动恢复并且不再重新发送已经全部传输的任何文件。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-120">If the snapshot transfer is interrupted at any point, it will automatically resume and will not resend any files that have already been completely transferred.</span></span> <span data-ttu-id="d9e0a-121">对于每个发布项目，快照代理的传递单位是 bcp 文件，因此已部分传递的文件必须全部重新传递。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-121">The unit of delivery for the Snapshot Agent is the bcp file for each publication article, so files that are partially delivered must be completely redelivered.</span></span> <span data-ttu-id="d9e0a-122">不过，恢复快照可以大幅度减少传输的数据量，即便在连接不可靠的情况下也可以确保及时进行快照传递。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-122">However, resuming the snapshot can significantly reduce the amount of data transmitted and ensure timely snapshot delivery even if the connection is unreliable.</span></span>  
  
## <a name="snapshot-options"></a><span data-ttu-id="d9e0a-123">快照选项</span><span class="sxs-lookup"><span data-stu-id="d9e0a-123">Snapshot Options</span></span>  
 <span data-ttu-id="d9e0a-124">使用快照初始化订阅时有许多可用选项。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-124">There are a number of options available when initializing a subscription with a snapshot.</span></span> <span data-ttu-id="d9e0a-125">可以：</span><span class="sxs-lookup"><span data-stu-id="d9e0a-125">You can:</span></span>  
  
-   <span data-ttu-id="d9e0a-126">指定一个备用快照文件夹位置，以替代默认的快照文件夹位置或者与之并存。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-126">Specify an alternate snapshot folder location instead of, or in addition, to the default snapshot folder location.</span></span> <span data-ttu-id="d9e0a-127">有关详细信息，请参阅 [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-127">For more information, see [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).</span></span>  
  
-   <span data-ttu-id="d9e0a-128">压缩快照，以便在可移动介质上进行存储或者通过速度较低的网络进行传输。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-128">Compress snapshots for storage on removable media or for transfer over a slow network.</span></span> <span data-ttu-id="d9e0a-129">有关详细信息，请参阅 [Compressed Snapshots](compressed-snapshots.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-129">For more information, see [Compressed Snapshots](compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="d9e0a-130">在应用快照之前或之后执行 Transact-SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-130">Execute Transact-SQL scripts before or after the snapshot is applied.</span></span> <span data-ttu-id="d9e0a-131">有关详细信息，请参阅[在应用快照之前和之后执行脚本](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-131">For more information, see [Execute Scripts Before and After the Snapshot Is Applied](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).</span></span>  
  
-   <span data-ttu-id="d9e0a-132">使用文件传输协议 (FTP) 传输快照文件。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-132">Transfer snapshot files using File Transfer Protocol (FTP).</span></span> <span data-ttu-id="d9e0a-133">有关详细信息，请参阅[通过 FTP 传输快照](transfer-snapshots-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e0a-133">For more information, see [Transfer Snapshots Through FTP](transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e0a-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9e0a-134">See Also</span></span>  
 <span data-ttu-id="d9e0a-135">[初始化订阅](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="d9e0a-135">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="d9e0a-136">保护快照文件夹</span><span class="sxs-lookup"><span data-stu-id="d9e0a-136">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
