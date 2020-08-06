---
title: 配置快照属性（复制 Transact-SQL 编程）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691660"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a><span data-ttu-id="10256-102">配置快照属性（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="10256-102">Configure Snapshot Properties (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="10256-103">可以使用复制存储过程以编程方式定义和修改快照属性，使用的存储过程取决于发布的类型。</span><span class="sxs-lookup"><span data-stu-id="10256-103">Snapshot properties can be defined and modified programmatically using replication stored procedures, where the stored procedures used depend on the type of publication.</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a><span data-ttu-id="10256-104">在创建快照发布或事务发布时配置快照属性</span><span class="sxs-lookup"><span data-stu-id="10256-104">To configure snapshot properties when creating a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="10256-105">在发布服务器上，执行 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="10256-105">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="10256-106">为指定发布名称，为指定一个 **@publication** 值， **snapshot**并为**指定** **@repl_freq** 以下一个或多个快照相关参数：</span><span class="sxs-lookup"><span data-stu-id="10256-106">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="10256-107">**@alt_snapshot_folder**-如果此发布的快照可从该位置访问，而不是在快照默认文件夹中访问，请指定路径。</span><span class="sxs-lookup"><span data-stu-id="10256-107">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="10256-108">**@compress_snapshot**-如果备用快照文件夹中的快照文件是 CAB 文件格式的压缩文件，则将值指定**为 true** [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="10256-108">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB file format.</span></span>  
  
    -   <span data-ttu-id="10256-109">**@pre_snapshot_script**-指定在初始快照应用之前的初始化过程中将在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-109">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-110">**@post_snapshot_script**-指定在初始快照应用之后的初始化过程中将在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-110">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-111">**@snapshot_in_defaultfolder**-如果快照仅在非默认位置可用，则将值指定为**false** 。</span><span class="sxs-lookup"><span data-stu-id="10256-111">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
     <span data-ttu-id="10256-112">有关创建发布的详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="10256-112">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a><span data-ttu-id="10256-113">创建合并发布时配置快照属性</span><span class="sxs-lookup"><span data-stu-id="10256-113">To configure snapshot properties when creating a merge publication</span></span>  
  
1.  <span data-ttu-id="10256-114">在发布服务器上，执行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="10256-114">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="10256-115">为指定发布名称，为指定一个 **@publication** 值， **snapshot**并为**指定** **@repl_freq** 以下一个或多个快照相关参数：</span><span class="sxs-lookup"><span data-stu-id="10256-115">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="10256-116">**@alt_snapshot_folder**-如果此发布的快照可从该位置访问，而不是在快照默认文件夹中访问，请指定路径。</span><span class="sxs-lookup"><span data-stu-id="10256-116">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="10256-117">**@compress_snapshot**-如果备用快照文件夹中的快照文件是 CAB 文件格式的压缩文件，则将值指定**为 true** 。</span><span class="sxs-lookup"><span data-stu-id="10256-117">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="10256-118">**@pre_snapshot_script**-指定在初始快照应用之前的初始化过程中将在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-118">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-119">**@post_snapshot_script**-指定在初始快照应用之后的初始化过程中将在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-119">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-120">**@snapshot_in_defaultfolder**-如果快照仅在非默认位置可用，则将值指定为**false** 。</span><span class="sxs-lookup"><span data-stu-id="10256-120">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="10256-121">有关创建发布的详细信息，请参阅 [Create a Publication](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="10256-121">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a><span data-ttu-id="10256-122">修改现有快照发布或事务发布的快照属性</span><span class="sxs-lookup"><span data-stu-id="10256-122">To modify snapshot properties of an existing snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="10256-123">在发布服务器上，对发布数据库执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="10256-123">At the Publisher on the publication database, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="10256-124">将的值指定**1**为 1 **@force_invalidate_snapshot** ，并为指定以下值之一 **@property** ：</span><span class="sxs-lookup"><span data-stu-id="10256-124">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="10256-125">**alt_snapshot_folder** -还为的备用快照文件夹指定新路径 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="10256-125">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="10256-126">**compress_snapshot** -还将值指定为**true**或**false** ， **@value** 以指示备用快照文件夹中的快照文件是否为 CAB 文件格式的压缩文件。</span><span class="sxs-lookup"><span data-stu-id="10256-126">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="10256-127">**pre_snapshot_script** -还 **@value** 可指定在初始化过程中，在应用初始快照之前，在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-127">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-128">**post_snapshot_script** -还可 **@value** 指定在初始化初始快照后，在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-128">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-129">**snapshot_in_defaultfolder** - 也将值指定为 **true** 或 **false** ，以指示快照是否仅在非默认位置可用。</span><span class="sxs-lookup"><span data-stu-id="10256-129">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="10256-130">（可选）在发布服务器上，对发布数据库执行 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="10256-130">(Optional) At the Publisher on the publication database, execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql).</span></span> <span data-ttu-id="10256-131">指定 **@publication** 和要更改的一个或多个计划或安全凭据参数。</span><span class="sxs-lookup"><span data-stu-id="10256-131">Specify **@publication** and one or more of the scheduling or security credential parameters being changed.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="10256-132">如果可能，请在运行时提示用户输入安全凭据。</span><span class="sxs-lookup"><span data-stu-id="10256-132">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="10256-133">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="10256-133">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
3.  <span data-ttu-id="10256-134">在命令提示符处运行 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 或启动快照代理作业以生成新的快照。</span><span class="sxs-lookup"><span data-stu-id="10256-134">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="10256-135">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="10256-135">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a><span data-ttu-id="10256-136">修改现有合并发布的快照属性</span><span class="sxs-lookup"><span data-stu-id="10256-136">To modify snapshot properties of an existing merge publication</span></span>  
  
1.  <span data-ttu-id="10256-137">在发布服务器上，对发布数据库执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="10256-137">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="10256-138">将的值指定**1**为 1 **@force_invalidate_snapshot** ，并为指定以下值之一 **@property** ：</span><span class="sxs-lookup"><span data-stu-id="10256-138">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="10256-139">**alt_snapshot_folder** -还为的备用快照文件夹指定新路径 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="10256-139">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="10256-140">**compress_snapshot** -还将值指定为**true**或**false** ， **@value** 以指示备用快照文件夹中的快照文件是否为 CAB 文件格式的压缩文件。</span><span class="sxs-lookup"><span data-stu-id="10256-140">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="10256-141">**pre_snapshot_script** -还 **@value** 可指定在初始化过程中，在应用初始快照之前，在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-141">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-142">**post_snapshot_script** -还可 **@value** 指定在初始化初始快照后，在订阅服务器上执行的 **.sql**文件的文件名和完整路径。</span><span class="sxs-lookup"><span data-stu-id="10256-142">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="10256-143">**snapshot_in_defaultfolder** - 也将值指定为 **true** 或 **false** ，以指示快照是否仅在非默认位置可用。</span><span class="sxs-lookup"><span data-stu-id="10256-143">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="10256-144">在命令提示符处运行 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 或启动快照代理作业以生成新的快照。</span><span class="sxs-lookup"><span data-stu-id="10256-144">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="10256-145">有关详细信息，请参阅 [创建并应用初始快照](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="10256-145">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10256-146">示例</span><span class="sxs-lookup"><span data-stu-id="10256-146">Example</span></span>  
 <span data-ttu-id="10256-147">此示例创建一个使用备用快照文件夹和压缩快照的发布。</span><span class="sxs-lookup"><span data-stu-id="10256-147">This example creates a publication that uses an alternate snapshot folder and a compressed snapshot.</span></span>  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a><span data-ttu-id="10256-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10256-148">See Also</span></span>  
 <span data-ttu-id="10256-149">[备用快照文件夹位置](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="10256-149">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="10256-150">[压缩的快照](../compressed-snapshots.md) </span><span class="sxs-lookup"><span data-stu-id="10256-150">[Compressed Snapshots](../compressed-snapshots.md) </span></span>  
 <span data-ttu-id="10256-151">[在应用快照之前和之后执行脚本](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span><span class="sxs-lookup"><span data-stu-id="10256-151">[Execute Scripts Before and After the Snapshot Is Applied](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span></span>  
 <span data-ttu-id="10256-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="10256-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="10256-153">[通过 FTP 传输快照](../transfer-snapshots-through-ftp.md) </span><span class="sxs-lookup"><span data-stu-id="10256-153">[Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md) </span></span>  
 [<span data-ttu-id="10256-154">更改发布和项目属性</span><span class="sxs-lookup"><span data-stu-id="10256-154">Change Publication and Article Properties</span></span>](change-publication-and-article-properties.md)  
  
  
