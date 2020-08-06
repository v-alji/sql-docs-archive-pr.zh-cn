---
title: 通过参数化筛选器为合并发布管理分区 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- partitions [SQL Server replication]
- merge replication partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], partition management
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 983b02865c0564919259f896bf09d8bdb0cd969f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577528"
---
# <a name="manage-partitions-for-a-merge-publication-with-parameterized-filters"></a><span data-ttu-id="f8230-102">通过参数化筛选器为合并发布管理分区</span><span class="sxs-lookup"><span data-stu-id="f8230-102">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>
  <span data-ttu-id="f8230-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中通过参数化筛选器为合并发布管理分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-103">This topic describes how to manage partitions for a merge publication with parameterized filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="f8230-104">参数化行筛选器可用于生成不重叠的分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-104">Parameterized row filters can be used to generate nonoverlapping partitions.</span></span> <span data-ttu-id="f8230-105">可以限制这些分区，以便只有一个订阅接收到给定分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-105">These partitions can be restricted so that only one subscription receives a given partition.</span></span> <span data-ttu-id="f8230-106">在这类情况下，大量订阅服务器将导致大量的分区，从而需要同等数量的分区快照。</span><span class="sxs-lookup"><span data-stu-id="f8230-106">In these cases, a large number of subscribers will result in a large number of partitions, which in turn requires an equal number of partitioned snapshots.</span></span> <span data-ttu-id="f8230-107">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="f8230-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="f8230-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f8230-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="f8230-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f8230-110">建议</span><span class="sxs-lookup"><span data-stu-id="f8230-110">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="f8230-111">**通过参数化筛选器为合并发布管理分区，使用：**</span><span class="sxs-lookup"><span data-stu-id="f8230-111">**To manage partitions for a merge publication with parameterized filters, using:**</span></span>  
  
     [<span data-ttu-id="f8230-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f8230-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f8230-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8230-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="f8230-114">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="f8230-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f8230-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="f8230-115">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f8230-116">建议</span><span class="sxs-lookup"><span data-stu-id="f8230-116">Recommendations</span></span>  
  
-   <span data-ttu-id="f8230-117">如果对复制拓扑编写脚本（建议这样做），则发布脚本包含用于创建数据分区的存储过程调用。</span><span class="sxs-lookup"><span data-stu-id="f8230-117">If you script a replication topology, which is recommended, publication scripts contain the stored procedure calls to create data partitions.</span></span> <span data-ttu-id="f8230-118">该脚本提供了对所创建的分区的引用和一种在必要时重建分区的途径。</span><span class="sxs-lookup"><span data-stu-id="f8230-118">The script provides a reference for the partitions created and a way in which to re-create one or more partitions if necessary.</span></span> <span data-ttu-id="f8230-119">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-119">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="f8230-120">如果发布具有的参数化筛选器可生成带有非重叠分区的订阅，并且如果特定订阅丢失并需要重新创建，则您必须执行以下操作：删除曾订阅的分区，重新创建订阅，然后重新创建该分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-120">When a publication has parameterized filters that yield subscriptions with nonoverlapping partitions, and if a particular subscription is lost and needs to be re-created, you must do the following: remove the partition that was subscribed to, re-create the subscription, and then re-create the partition.</span></span> <span data-ttu-id="f8230-121">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-121">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span> <span data-ttu-id="f8230-122">生成发布创建脚本时，复制会为现有订阅服务器分区生成创建脚本。</span><span class="sxs-lookup"><span data-stu-id="f8230-122">Replication generates creation scripts for existing Subscriber partitions when a publication creation script is generated.</span></span> <span data-ttu-id="f8230-123">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-123">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f8230-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f8230-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f8230-125">可在“发布属性 - \<Publication>”对话框的“数据分区”页面上管理分区 。</span><span class="sxs-lookup"><span data-stu-id="f8230-125">Manage partitions on the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="f8230-126">有关访问此对话框的详细信息，请参阅 [View and Modify Publication Properties](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-126">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="f8230-127">在此页上，可以执行下列操作：创建和删除分区、允许订阅服务器启动快照的生成和传递、生成一个或多个分区的快照和清除快照。</span><span class="sxs-lookup"><span data-stu-id="f8230-127">On this page you can: create and delete partitions; allow Subscribers to initiate snapshot generation and delivery; generate snapshots for one or more partitions; and clean up snapshots.</span></span>  
  
#### <a name="to-create-a-partition"></a><span data-ttu-id="f8230-128">创建分区</span><span class="sxs-lookup"><span data-stu-id="f8230-128">To create a partition</span></span>  
  
1.  <span data-ttu-id="f8230-129">在“发布属性 - \<Publication>”对话框的“数据分区”页面上，单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="f8230-129">On the **Data Partitions** page of the **Publication Properties - \<Publication>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="f8230-130">在 **“添加数据分区”** 对话框中，输入与要创建的分区相关联的 **HOST_NAME()** 和/或 **SUSER_SNAME()** 的值。</span><span class="sxs-lookup"><span data-stu-id="f8230-130">In the **Add Data Partition** dialog box, enter a value for the **HOST_NAME()** and/or **SUSER_SNAME()** value associated with the partition you want to create.</span></span>  
  
3.  <span data-ttu-id="f8230-131">还可以指定快照刷新计划：</span><span class="sxs-lookup"><span data-stu-id="f8230-131">Optionally specify a schedule for refreshing snapshots:</span></span>  
  
    1.  <span data-ttu-id="f8230-132">选择 **“安排此分区的快照代理在以下时间运行”**</span><span class="sxs-lookup"><span data-stu-id="f8230-132">Select **Schedule the Snapshot Agent for this partition to run at the following time(s)**</span></span>  
  
    2.  <span data-ttu-id="f8230-133">接受默认的快照刷新计划，或者单击 **“更改”** 以指定其他计划。</span><span class="sxs-lookup"><span data-stu-id="f8230-133">Accept the default schedule for refreshing snapshots, or click **Change** to specify a different schedule.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="f8230-134">删除分区</span><span class="sxs-lookup"><span data-stu-id="f8230-134">To delete a partition</span></span>  
  
1.  <span data-ttu-id="f8230-135">在 **“数据分区”** 页上，在网格中选择分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-135">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="f8230-136">单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="f8230-136">Click **Delete**.</span></span>  
  
#### <a name="to-allow-subscribers-to-initiate-snapshot-generation-and-delivery"></a><span data-ttu-id="f8230-137">允许订阅服务器启动快照的生成和传递</span><span class="sxs-lookup"><span data-stu-id="f8230-137">To allow Subscribers to initiate snapshot generation and delivery</span></span>  
  
1.  <span data-ttu-id="f8230-138">在 **“数据分区”** 页上，选择 **“在新订阅服务器尝试同步时，根据需要自动定义分区并生成快照”** 。</span><span class="sxs-lookup"><span data-stu-id="f8230-138">On the **Data Partitions** page, select **Automatically define a partition and generate a snapshot if needed when a new Subscriber tries to synchronize**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-generate-a-snapshot-for-a-partition"></a><span data-ttu-id="f8230-139">生成分区快照</span><span class="sxs-lookup"><span data-stu-id="f8230-139">To generate a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="f8230-140">在 **“数据分区”** 页上，在网格中选择分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-140">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="f8230-141">单击 **“立即生成所选快照”**</span><span class="sxs-lookup"><span data-stu-id="f8230-141">Click **Generate the selected snapshots now**.</span></span>  
  
#### <a name="to-clean-up-a-snapshot-for-a-partition"></a><span data-ttu-id="f8230-142">清除分区快照</span><span class="sxs-lookup"><span data-stu-id="f8230-142">To clean up a snapshot for a partition</span></span>  
  
1.  <span data-ttu-id="f8230-143">在 **“数据分区”** 页上，在网格中选择分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-143">On the **Data Partitions** page, select a partition in the grid.</span></span>  
  
2.  <span data-ttu-id="f8230-144">单击 **“清除现有快照”** 。</span><span class="sxs-lookup"><span data-stu-id="f8230-144">Click **Clean up the existing snapshots**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f8230-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f8230-145">Using Transact-SQL</span></span>  
 <span data-ttu-id="f8230-146">为了更好地管理带有参数化筛选器的发布，可使用复制存储过程以编程方式枚举现有的分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-146">To better manage a publication with parameterized filters, you can programmatically enumerate the existing partitions using replication stored procedures.</span></span> <span data-ttu-id="f8230-147">还可以创建和删除现有的分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-147">You can also create and delete existing partitions.</span></span> <span data-ttu-id="f8230-148">可以获取以下有关现有分区的信息：</span><span class="sxs-lookup"><span data-stu-id="f8230-148">The following information on existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="f8230-149">如何筛选分区（使用 [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) 或 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)）。</span><span class="sxs-lookup"><span data-stu-id="f8230-149">How a partition is filtered (using [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) or [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)).</span></span>  
  
-   <span data-ttu-id="f8230-150">用于生成分区快照的作业的名称。</span><span class="sxs-lookup"><span data-stu-id="f8230-150">The name of the job that generates a partitioned snapshot.</span></span>  
  
-   <span data-ttu-id="f8230-151">分区快照作业上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="f8230-151">The last time that a partitioned snapshot job ran.</span></span>  
  
 <span data-ttu-id="f8230-152">尽管在初始化新订阅时可以按需生成由两部分构成的快照的第二部分，但通过下面的过程可以控制此快照的生成方式，并在最方便的时候预生成该快照。</span><span class="sxs-lookup"><span data-stu-id="f8230-152">While the second part of the two-part snapshot can be generated on-demand when a new subscription is initialized, the procedures below enable you to control how this snapshot is generated and to pre-generate this snapshot when it is most convenient.</span></span> <span data-ttu-id="f8230-153">有关详细信息，请参阅 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-153">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="f8230-154">查看有关现有分区的信息</span><span class="sxs-lookup"><span data-stu-id="f8230-154">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="f8230-155">在发布服务器上，对发布数据库执行 [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f8230-155">At the Publisher on the publication database, execute [sp_helpmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql).</span></span> <span data-ttu-id="f8230-156">指定\*\* \@ 发布的名称。\*\*</span><span class="sxs-lookup"><span data-stu-id="f8230-156">Specify the name of the publication for **\@publication**.</span></span> <span data-ttu-id="f8230-157"> (可选) 指\定\** \@ suser_sname**或** \@ host_nam\e\**以仅基于单个筛选条件返回信息。</span><span class="sxs-lookup"><span data-stu-id="f8230-157">(Optional) Specify **\@suser_sname** or **\@host_name** to return only information based on a single filtering criterion.</span></span>  
  
#### <a name="to-define-a-new-partition-and-generate-a-new-partitioned-snapshot"></a><span data-ttu-id="f8230-158">定义新分区并生成新分区快照</span><span class="sxs-lookup"><span data-stu-id="f8230-158">To define a new partition and generate a new partitioned snapshot</span></span>  
  
1.  <span data-ttu-id="f8230-159">在发布服务器上，对发布数据库执行 [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f8230-159">At the Publisher on the publication database, execute [sp_addmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql).</span></span> <span data-ttu-id="f8230-160">指定发布的发布名称，并为以下各项之一\*\* \@ 指定用于定义\*\*分区的参数化值：</span><span class="sxs-lookup"><span data-stu-id="f8230-160">Specify the name of the publication for **\@publication**, and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="f8230-161">\*\* \@ suser_sname\*\* -参数化筛选器由[SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)返回的值定义时。</span><span class="sxs-lookup"><span data-stu-id="f8230-161">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="f8230-162">\*\* \@ host_name\*\* -参数化筛选器由[HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)返回的值定义时。</span><span class="sxs-lookup"><span data-stu-id="f8230-162">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
2.  <span data-ttu-id="f8230-163">创建并初始化此新分区的参数化快照。</span><span class="sxs-lookup"><span data-stu-id="f8230-163">Create and initialize the parameterized snapshot for this new partition.</span></span> <span data-ttu-id="f8230-164">有关详细信息，请参阅 [为包含参数化筛选器的合并发布创建快照](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-164">For more information, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
#### <a name="to-delete-a-partition"></a><span data-ttu-id="f8230-165">删除分区</span><span class="sxs-lookup"><span data-stu-id="f8230-165">To delete a partition</span></span>  
  
1.  <span data-ttu-id="f8230-166">在发布服务器上，对发布数据库执行 [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f8230-166">At the Publisher on the publication database, execute [sp_dropmergepartition &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql).</span></span> <span data-ttu-id="f8230-167">指定发布\*\* \@ 的发布名称，并为\*\*以下各项之一指定用于定义分区的参数化值：</span><span class="sxs-lookup"><span data-stu-id="f8230-167">Specify the name of the publication for **\@publication** and the parameterized value that defines the partition for one of the following:</span></span>  
  
    -   <span data-ttu-id="f8230-168">\*\* \@ suser_sname\*\* -参数化筛选器由[SUSER_SNAME &#40;transact-sql&#41;](/sql/t-sql/functions/suser-sname-transact-sql)返回的值定义时。</span><span class="sxs-lookup"><span data-stu-id="f8230-168">**\@suser_sname** - when the parameterized filter is defined by the value returned by [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql).</span></span>  
  
    -   <span data-ttu-id="f8230-169">\*\* \@ host_name\*\* -参数化筛选器由[HOST_NAME &#40;transact-sql&#41;](/sql/t-sql/functions/host-name-transact-sql)返回的值定义时。</span><span class="sxs-lookup"><span data-stu-id="f8230-169">**\@host_name** - when the parameterized filter is defined by the value returned by [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql).</span></span>  
  
     <span data-ttu-id="f8230-170">此操作还将删除快照作业以及该分区的任何快照文件。</span><span class="sxs-lookup"><span data-stu-id="f8230-170">This also removes the snapshot job and any snapshot files for the partition.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="f8230-171">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="f8230-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="f8230-172">若要更好地管理具有参数化筛选器的发布，可以通过使用复制管理对象 (RMO) 以编程方式创建新的订阅服务器分区，枚举现有的订阅服务器分区以及删除订阅服务器分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-172">To better manage a publication with parameterized filters, you can programmatically create new Subscriber partitions, enumerate the existing Subscriber partitions, and delete Subscriber partitions by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="f8230-173">有关如何创建订阅服务器分区的信息，请参阅 [为包含参数化筛选器的合并发布创建快照](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="f8230-173">For information about how to create Subscriber partitions, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span> <span data-ttu-id="f8230-174">可以获得有关现有分区的以下信息：</span><span class="sxs-lookup"><span data-stu-id="f8230-174">The following information about existing partitions can be obtained:</span></span>  
  
-   <span data-ttu-id="f8230-175">分区所基于的值和筛选函数。</span><span class="sxs-lookup"><span data-stu-id="f8230-175">The value and filtering function upon which the partition is based.</span></span>  
  
-   <span data-ttu-id="f8230-176">为订阅服务器生成参数化快照的作业的名称。</span><span class="sxs-lookup"><span data-stu-id="f8230-176">The name of the job that generates a parameterized snapshot for the Subscriber.</span></span>  
  
-   <span data-ttu-id="f8230-177">参数化快照作业上次运行的时间。</span><span class="sxs-lookup"><span data-stu-id="f8230-177">The last time that a parameterized snapshot job ran.</span></span>  
  
#### <a name="to-view-information-on-existing-partitions"></a><span data-ttu-id="f8230-178">查看有关现有分区的信息</span><span class="sxs-lookup"><span data-stu-id="f8230-178">To view information on existing partitions</span></span>  
  
1.  <span data-ttu-id="f8230-179">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f8230-179">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f8230-180">创建的 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f8230-180">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="f8230-181">设置发布的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="f8230-181">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="f8230-182">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="f8230-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="f8230-183">如果此方法返回 `false`，则说明步骤 2 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="f8230-183">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="f8230-184">调用 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，然后将结果传递至 <xref:Microsoft.SqlServer.Replication.MergePartition> 对象数组。</span><span class="sxs-lookup"><span data-stu-id="f8230-184">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="f8230-185">对数组中的每个 <xref:Microsoft.SqlServer.Replication.MergePartition> 对象，获取感兴趣的任何属性。</span><span class="sxs-lookup"><span data-stu-id="f8230-185">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, get any properties of interest.</span></span>  
  
#### <a name="to-delete-existing-partitions"></a><span data-ttu-id="f8230-186">删除现有分区</span><span class="sxs-lookup"><span data-stu-id="f8230-186">To delete existing partitions</span></span>  
  
1.  <span data-ttu-id="f8230-187">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="f8230-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="f8230-188">创建的 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="f8230-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span> <span data-ttu-id="f8230-189">设置发布的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性，并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为步骤 1 中创建的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 。</span><span class="sxs-lookup"><span data-stu-id="f8230-189">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> created in step 1.</span></span>  
  
3.  <span data-ttu-id="f8230-190">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="f8230-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="f8230-191">如果此方法返回 `false`，则说明步骤 2 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="f8230-191">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="f8230-192">调用 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> 方法，然后将结果传递至 <xref:Microsoft.SqlServer.Replication.MergePartition> 对象数组。</span><span class="sxs-lookup"><span data-stu-id="f8230-192">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> method, and pass the result to an array of <xref:Microsoft.SqlServer.Replication.MergePartition> objects.</span></span>  
  
5.  <span data-ttu-id="f8230-193">对数组中的每个 <xref:Microsoft.SqlServer.Replication.MergePartition> 对象，确定是否应删除分区。</span><span class="sxs-lookup"><span data-stu-id="f8230-193">For each <xref:Microsoft.SqlServer.Replication.MergePartition> object in the array, determine whether the partition should be deleted.</span></span> <span data-ttu-id="f8230-194">此决定通常基于 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> 属性的值或 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="f8230-194">This decision is usually based on the value of the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> property or the <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> property.</span></span>  
  
6.  <span data-ttu-id="f8230-195">在步骤 2 中的 <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> 对象上调用 <xref:Microsoft.SqlServer.Replication.MergePublication> 方法。</span><span class="sxs-lookup"><span data-stu-id="f8230-195">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> method on the <xref:Microsoft.SqlServer.Replication.MergePublication> object from step 2.</span></span> <span data-ttu-id="f8230-196">传递步骤 5 中的 <xref:Microsoft.SqlServer.Replication.MergePartition> 对象。</span><span class="sxs-lookup"><span data-stu-id="f8230-196">Pass the <xref:Microsoft.SqlServer.Replication.MergePartition> object from step 5.</span></span>  
  
7.  <span data-ttu-id="f8230-197">对已删除的每个分区重复步骤 6。</span><span class="sxs-lookup"><span data-stu-id="f8230-197">Repeat step 6 for each partition that is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8230-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8230-198">See Also</span></span>  
 <span data-ttu-id="f8230-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="f8230-199">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="f8230-200">Snapshots for Merge Publications with Parameterized Filters</span><span class="sxs-lookup"><span data-stu-id="f8230-200">Snapshots for Merge Publications with Parameterized Filters</span></span>](../snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
