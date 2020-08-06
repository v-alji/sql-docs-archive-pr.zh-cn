---
title: 管理和监视服务器实例的全文搜索 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], about
- full-text search [SQL Server], server management
ms.assetid: 2733ed78-6d33-4bf9-94da-60c3141b87c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1ba4b2f081047f25fa775e0c8754caa4ce643e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690459"
---
# <a name="manage-and-monitor-full-text-search-for-a-server-instance"></a><span data-ttu-id="e7932-102">管理和监视服务器实例的全文搜索</span><span class="sxs-lookup"><span data-stu-id="e7932-102">Manage and Monitor Full-Text Search for a Server Instance</span></span>
  <span data-ttu-id="e7932-103">针对服务器实例的全文管理包括：</span><span class="sxs-lookup"><span data-stu-id="e7932-103">Full-text administration for a server instance includes:</span></span>  
  
-   <span data-ttu-id="e7932-104">诸如管理 FDHOST Launcher 服务 (MSSQLFDLauncher)、重新启动筛选器后台程序宿主进程（如果您更改服务帐户凭据）、配置服务器范围内的全文属性以及备份全文目录之类的系统管理任务。</span><span class="sxs-lookup"><span data-stu-id="e7932-104">System management tasks such as managing the FDHOST Launcher service (MSSQLFDLauncher), restarting filter daemon host process if you change the service account credentials, configuring server-wide full-text properties, and backing up full-text catalogs.</span></span> <span data-ttu-id="e7932-105">例如，在服务器级，您可以指定在整体上与服务器实例的默认语言不同的默认全文语言。</span><span class="sxs-lookup"><span data-stu-id="e7932-105">At the server level, for example, you can specify a default full-text language that differs from the default language of the server instance as a whole.</span></span>  
  
-   <span data-ttu-id="e7932-106">配置全文语言组件（断字符和词干分析器、同义词库文件、非索引字和非索引字表）。</span><span class="sxs-lookup"><span data-stu-id="e7932-106">Configuring full-text linguistic components (word breakers and stemmers, thesaurus file, and stopwords and stoplists).</span></span>  
  
-   <span data-ttu-id="e7932-107">配置用户数据库以进行全文搜索。</span><span class="sxs-lookup"><span data-stu-id="e7932-107">Configuring a user database for full-text search.</span></span> <span data-ttu-id="e7932-108">这涉及为数据库创建一个或多个全文目录并对每个要对其执行全文查询的表或索引视图定义一个全文索引。</span><span class="sxs-lookup"><span data-stu-id="e7932-108">This involves creating one or more full-text catalogs for the database and defining a full-text index on each table or indexed view on which you want to execute full-text queries.</span></span>  
  
##  <a name="viewing-or-changing-server-properties-for-full-text-search"></a><a name="props"></a> <span data-ttu-id="e7932-109">查看和更改全文搜索的服务器属性</span><span class="sxs-lookup"><span data-stu-id="e7932-109">Viewing or Changing Server Properties for Full-Text Search</span></span>  
 <span data-ttu-id="e7932-110">可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]实例的全文属性。</span><span class="sxs-lookup"><span data-stu-id="e7932-110">You can view the full-text properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-view-and-change-server-properties-for-full-text-search"></a><span data-ttu-id="e7932-111">查看和更改全文搜索的服务器属性</span><span class="sxs-lookup"><span data-stu-id="e7932-111">To view and change server properties for full-text search</span></span>  
  
1.  <span data-ttu-id="e7932-112">在“对象资源管理器”中，右键单击服务器，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="e7932-112">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e7932-113">在“服务器属性”  对话框中，单击“高级”  页以查看有关全文搜索的服务器信息。</span><span class="sxs-lookup"><span data-stu-id="e7932-113">In the **Server Properties** dialog box, click the **Advanced** page to view server information about full-text search.</span></span> <span data-ttu-id="e7932-114">全文属性如下所示：</span><span class="sxs-lookup"><span data-stu-id="e7932-114">The full-text properties are as follows:</span></span>  
  
    -   <span data-ttu-id="e7932-115">**默认全文语言**</span><span class="sxs-lookup"><span data-stu-id="e7932-115">**Default Full-Text Language**</span></span>  
  
         <span data-ttu-id="e7932-116">指定全文检索列的默认语言。</span><span class="sxs-lookup"><span data-stu-id="e7932-116">Specifies a default language for full-text indexed columns.</span></span> <span data-ttu-id="e7932-117">全文检索数据的语言分析取决于数据的语言。</span><span class="sxs-lookup"><span data-stu-id="e7932-117">Linguistic analysis of full-text indexed data is dependent on the language of the data.</span></span> <span data-ttu-id="e7932-118">该选项的默认值为服务器的语言。</span><span class="sxs-lookup"><span data-stu-id="e7932-118">The default value of this option is the language of the server.</span></span> <span data-ttu-id="e7932-119">有关与所显示设置相对应的语言，请参阅 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e7932-119">For the language that corresponds to the displayed setting, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span>  
  
    -   <span data-ttu-id="e7932-120">**全文升级选项**</span><span class="sxs-lookup"><span data-stu-id="e7932-120">**Full-Text Upgrade Option**</span></span>  
  
         <span data-ttu-id="e7932-121">此服务器属性控制将数据库从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 升级到更高版本时迁移全文索引的方式。</span><span class="sxs-lookup"><span data-stu-id="e7932-121">This server property controls how full-text indexes are migrated when upgrading a database from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] to a later version.</span></span> <span data-ttu-id="e7932-122">此属性适用于以下升级方式：附加数据库、还原数据库备份、还原文件备份或使用复制数据库向导复制数据库。</span><span class="sxs-lookup"><span data-stu-id="e7932-122">This property applies to upgrading by attaching a database, restoring a database backup, restoring a file backup, or copying the database by using the Copy Database Wizard.</span></span>  
  
         <span data-ttu-id="e7932-123">可以选择的选项如下：</span><span class="sxs-lookup"><span data-stu-id="e7932-123">The alternatives are as follows:</span></span>  
  
         <span data-ttu-id="e7932-124">**导入**</span><span class="sxs-lookup"><span data-stu-id="e7932-124">**Import**</span></span>  
         <span data-ttu-id="e7932-125">导入全文目录。</span><span class="sxs-lookup"><span data-stu-id="e7932-125">Full-text catalogs are imported.</span></span> <span data-ttu-id="e7932-126">一般情况下，导入速度比重新生成速度要快很多。</span><span class="sxs-lookup"><span data-stu-id="e7932-126">Typically, import is significantly faster than rebuild.</span></span> <span data-ttu-id="e7932-127">例如，当仅使用一个 CPU 时，导入的运行速度比重新生成要快 10 倍左右。</span><span class="sxs-lookup"><span data-stu-id="e7932-127">For example, when using only one CPU, import runs about 10 times faster than rebuild.</span></span> <span data-ttu-id="e7932-128">不过，导入的全文目录不能使用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]中引入的新的和增强的断字符，因此最终可能还是要重新生成全文目录。</span><span class="sxs-lookup"><span data-stu-id="e7932-128">However, an imported full-text catalog does not use the new and enhanced word breakers introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], so you might want to rebuild your full-text catalogs eventually.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e7932-129">重新生成可以以多线程模式运行，如果可用的 CPU 在 10 个以上，且您允许重新生成操作使用所有这些 CPU，则重新生成操作的运行速度可能比导入更快。</span><span class="sxs-lookup"><span data-stu-id="e7932-129">Rebuild can run in multi-threaded mode, and if more than 10 CPUs are available, rebuild might run faster than import if you allow rebuild to use all of the CPUs.</span></span>  
  
         <span data-ttu-id="e7932-130">如果全文目录不可用，则会重新生成关联的全文检索。</span><span class="sxs-lookup"><span data-stu-id="e7932-130">If a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="e7932-131">此选项仅对 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 数据库可用。</span><span class="sxs-lookup"><span data-stu-id="e7932-131">This option is available for only [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] databases.</span></span>  
  
         <span data-ttu-id="e7932-132">**重新生成**</span><span class="sxs-lookup"><span data-stu-id="e7932-132">**Rebuild**</span></span>  
         <span data-ttu-id="e7932-133">使用新的和增强的断字符重新生成全文目录。</span><span class="sxs-lookup"><span data-stu-id="e7932-133">Full-text catalogs are rebuilt using the new and enhanced word breakers.</span></span> <span data-ttu-id="e7932-134">重新生成索引可能需要一些时间，且升级后可能需要占用大量的 CPU 和内存。</span><span class="sxs-lookup"><span data-stu-id="e7932-134">Rebuilding indexes can take awhile, and a significant amount of CPU and memory might be required after the upgrade.</span></span>  
  
         <span data-ttu-id="e7932-135">**重置**</span><span class="sxs-lookup"><span data-stu-id="e7932-135">**Reset**</span></span>  
         <span data-ttu-id="e7932-136">重置全文目录。</span><span class="sxs-lookup"><span data-stu-id="e7932-136">Full-text catalogs are reset.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="e7932-137">将删除全文目录文件，但会保留全文目录和全文索引的元数据。</span><span class="sxs-lookup"><span data-stu-id="e7932-137">full-text catalog files are removed, but the metadata for full-text catalogs and full-text indexes is retained.</span></span> <span data-ttu-id="e7932-138">在进行升级后，所有全文检索将禁用更改跟踪，并且不会自动启动爬网。</span><span class="sxs-lookup"><span data-stu-id="e7932-138">After being upgraded, all full-text indexes are disabled for change tracking and crawls are not started automatically.</span></span> <span data-ttu-id="e7932-139">在升级完成后，目录将保留为空，直至手动执行完全填充。</span><span class="sxs-lookup"><span data-stu-id="e7932-139">The catalog will remain empty until you manually issue a full population, after the upgrade completes.</span></span>  
  
         <span data-ttu-id="e7932-140">有关选择全文升级选项的信息，请参阅[升级全文搜索](upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="e7932-140">For information about choosing a full-text upgrade option, see [Upgrade Full-Text Search](upgrade-full-text-search.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e7932-141">也可以使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** 操作来设置全文升级选项。</span><span class="sxs-lookup"><span data-stu-id="e7932-141">The full-text upgrade option can also be set by using the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)**upgrade_option** action.</span></span>  
  
##  <a name="viewing-additional-full-text-server-properties"></a><a name="metadata"></a> <span data-ttu-id="e7932-142">查看其他全文服务器属性</span><span class="sxs-lookup"><span data-stu-id="e7932-142">Viewing Additional Full-Text Server Properties</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="e7932-143">函数可用来获取全文搜索的各种服务器级属性的值。</span><span class="sxs-lookup"><span data-stu-id="e7932-143">functions can be used to obtain the value of various server-level properties of full-text search.</span></span> <span data-ttu-id="e7932-144">此信息可用于全文搜索的管理和故障排除。</span><span class="sxs-lookup"><span data-stu-id="e7932-144">This information is useful for administrating and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="e7932-145">下表列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务器实例全文属性及其相关的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 函数。</span><span class="sxs-lookup"><span data-stu-id="e7932-145">The following table lists full-text properties of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server instance and their related [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="e7932-146">properties</span><span class="sxs-lookup"><span data-stu-id="e7932-146">Property</span></span>|<span data-ttu-id="e7932-147">说明</span><span class="sxs-lookup"><span data-stu-id="e7932-147">Description</span></span>|<span data-ttu-id="e7932-148">函数</span><span class="sxs-lookup"><span data-stu-id="e7932-148">Function</span></span>|  
|--------------|-----------------|--------------|  
|`IsFullTextInstalled`|<span data-ttu-id="e7932-149">全文组件是否安装在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的当前实例中。</span><span class="sxs-lookup"><span data-stu-id="e7932-149">Whether the full-text component is installed with the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="e7932-150">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e7932-150">FULLTEXTSERVICEPROPERTY</span></span>](/sql/t-sql/functions/fulltextserviceproperty-transact-sql)<br /><br /> [<span data-ttu-id="e7932-151">SERVERPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e7932-151">SERVERPROPERTY</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|  
|`LoadOSResources`|<span data-ttu-id="e7932-152">此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例中是否注册并使用了操作系统断字符和筛选器。</span><span class="sxs-lookup"><span data-stu-id="e7932-152">Whether operating system word breakers and filters are registered and used with this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="e7932-153">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e7932-153">FULLTEXTSERVICEPROPERTY</span></span>|  
|`VerifySignature`|<span data-ttu-id="e7932-154">指定全文引擎是否只加载已签名的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="e7932-154">Specifies whether only signed binaries are loaded by the Full-Text Engine.</span></span>|<span data-ttu-id="e7932-155">FULLTEXTSERVICEPROPERTY</span><span class="sxs-lookup"><span data-stu-id="e7932-155">FULLTEXTSERVICEPROPERTY</span></span>|  
  
##  <a name="monitoring-full-text-search-activity"></a><a name="monitor"></a> <span data-ttu-id="e7932-156">监视全文搜索活动</span><span class="sxs-lookup"><span data-stu-id="e7932-156">Monitoring Full-Text Search Activity</span></span>  
 <span data-ttu-id="e7932-157">有几个动态管理视图和函数可用来监视服务器实例上的全文搜索活动。</span><span class="sxs-lookup"><span data-stu-id="e7932-157">Several dynamic management views and functions are useful monitoring full-text search activity on a server instance.</span></span>  
  
 <span data-ttu-id="e7932-158">**查看与正在进行填充活动的全文目录有关的信息**</span><span class="sxs-lookup"><span data-stu-id="e7932-158">**To view information about the full-text catalogs with in-progress population activity**</span></span>  
  
-   [<span data-ttu-id="e7932-159">sys.dm_fts_active_catalogs (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-159">sys.dm_fts_active_catalogs &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-active-catalogs-transact-sql)  
  
 <span data-ttu-id="e7932-160">**查看筛选器后台程序宿主进程的当前活动**</span><span class="sxs-lookup"><span data-stu-id="e7932-160">**To view current activity of a filter daemon host process**</span></span>  
  
-   [<span data-ttu-id="e7932-161">sys.dm_fts_fdhosts (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-161">sys.dm_fts_fdhosts &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-fdhosts-transact-sql)  
  
 <span data-ttu-id="e7932-162">**查看与正在进行的索引填充有关的信息**</span><span class="sxs-lookup"><span data-stu-id="e7932-162">**To view information about in-progress index populations**</span></span>  
  
-   [<span data-ttu-id="e7932-163">sys.dm_fts_index_population (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-163">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)  
  
 <span data-ttu-id="e7932-164">**查看作为爬网或爬网范围的一部分使用的内存池中的内存缓冲区。**</span><span class="sxs-lookup"><span data-stu-id="e7932-164">**To view memory buffers in a memory pool that are used as part of a crawl or crawl range.**</span></span>  
  
-   [<span data-ttu-id="e7932-165">sys.dm_fts_memory_buffers (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-165">sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)  
  
 <span data-ttu-id="e7932-166">**查看可供全文爬网或全文爬网范围的全文收集器组件使用的共享内存池**</span><span class="sxs-lookup"><span data-stu-id="e7932-166">**To view the shared memory pools available to the full-text gatherer component for a full-text crawl or a full-text crawl range**</span></span>  
  
-   [<span data-ttu-id="e7932-167">sys.dm_fts_memory_pools (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-167">sys.dm_fts_memory_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)  
  
 <span data-ttu-id="e7932-168">**查看每个全文索引批次的相关信息**</span><span class="sxs-lookup"><span data-stu-id="e7932-168">**To view information about each full-text indexing batch**</span></span>  
  
-   [<span data-ttu-id="e7932-169">sys.dm_fts_outstanding_batches (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-169">sys.dm_fts_outstanding_batches &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-outstanding-batches-transact-sql)  
  
 <span data-ttu-id="e7932-170">**查看与正在进行的填充操作有关的特定范围的相关信息**</span><span class="sxs-lookup"><span data-stu-id="e7932-170">**To view information about the specific ranges related to an in-progress population**</span></span>  
  
-   [<span data-ttu-id="e7932-171">sys.dm_fts_population_ranges (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e7932-171">sys.dm_fts_population_ranges &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-population-ranges-transact-sql)  
  
  
