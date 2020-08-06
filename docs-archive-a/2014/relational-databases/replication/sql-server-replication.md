---
title: SQL Server 复制 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e51f45e06939971ada6166fb977c787ad0354926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577505"
---
# <a name="sql-server-replication"></a><span data-ttu-id="de362-102">SQL Server 复制</span><span class="sxs-lookup"><span data-stu-id="de362-102">SQL Server Replication</span></span>
  <span data-ttu-id="de362-103">复制是一组技术，它将数据和数据库对象从一个数据库复制和分发到另一个数据库，然后在数据库之间进行同步以保持一致性。</span><span class="sxs-lookup"><span data-stu-id="de362-103">Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span> <span data-ttu-id="de362-104">使用复制，可以在局域网和广域网、拨号连接、无线连接和 Internet 上将数据分发到不同位置以及分发给远程或移动用户。</span><span class="sxs-lookup"><span data-stu-id="de362-104">Using replication, you can distribute data to different locations and to remote or mobile users over local and wide area networks, dial-up connections, wireless connections, and the Internet.</span></span>  
  
 <span data-ttu-id="de362-105">事务复制通常用于需要高吞吐量的服务器到服务器方案（包括：提高可伸缩性和可用性、数据仓库和报告、集成多个站点的数据、集成异类数据以及减轻批处理的负荷）。</span><span class="sxs-lookup"><span data-stu-id="de362-105">Transactional replication is typically used in server-to-server scenarios that require high throughput, including: improving scalability and availability; data warehousing and reporting; integrating data from multiple sites; integrating heterogeneous data; and offloading batch processing.</span></span> <span data-ttu-id="de362-106">合并复制主要是为可能存在数据冲突的移动应用程序或分步式服务器应用程序设计的。</span><span class="sxs-lookup"><span data-stu-id="de362-106">Merge replication is primarily designed for mobile applications or distributed server applications that have possible data conflicts.</span></span> <span data-ttu-id="de362-107">常见应用场景包括：与移动用户交换数据、POS（消费者销售点）应用程序以及集成来自多个站点的数据。</span><span class="sxs-lookup"><span data-stu-id="de362-107">Common scenarios include: exchanging data with mobile users; consumer point of sale (POS) applications; and integration of data from multiple sites.</span></span> <span data-ttu-id="de362-108">快照复制用于为事务复制和合并复制提供初始数据集；在适合数据完全刷新时也可以使用快照复制。</span><span class="sxs-lookup"><span data-stu-id="de362-108">Snapshot replication is used to provide the initial data set for transactional and merge replication; it can also be used when complete refreshes of data are appropriate.</span></span> <span data-ttu-id="de362-109">利用这三种复制， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供功能强大且灵活的系统，以便使企业范围的数据同步。</span><span class="sxs-lookup"><span data-stu-id="de362-109">With these three types of replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a powerful and flexible system for synchronizing data across your enterprise.</span></span> <span data-ttu-id="de362-110">[!INCLUDE[win8srv](../../includes/win8srv-md.md)] 和 [!INCLUDE[win8](../../includes/win8-md.md)]都支持复制到 SQLCE 3.5 和 SQLCE 4.0。</span><span class="sxs-lookup"><span data-stu-id="de362-110">Replication to SQLCE 3.5 and SQLCE 4.0 is supported on both [!INCLUDE[win8srv](../../includes/win8srv-md.md)] and [!INCLUDE[win8](../../includes/win8-md.md)].</span></span>  
  
 <span data-ttu-id="de362-111">除了复制以外，还可以使用 Microsoft Sync Framework 来同步数据库。</span><span class="sxs-lookup"><span data-stu-id="de362-111">As an alternative to replication, you can synchronize databases by using Microsoft Sync Framework.</span></span> <span data-ttu-id="de362-112">Sync Framework 提供了相关的组件和一个直观且灵活的 API，使得在 SQL Server、SQL Server Express、SQL Server Compact 和 SQL Azure 数据库之间进行同步变得非常轻松。</span><span class="sxs-lookup"><span data-stu-id="de362-112">Sync Framework includes components and an intuitive and flexible API that make it easy to synchronize among SQL Server, SQL Server Express, SQL Server Compact, and SQL Azure databases.</span></span> <span data-ttu-id="de362-113">Sync Framework 还包括一些类，它们可改写为在 SQL Server 数据库和任何其他与 ADO.NET 兼容的数据库之间进行同步。</span><span class="sxs-lookup"><span data-stu-id="de362-113">Sync Framework also includes classes that can be adapted to synchronize between a SQL Server database and any other database that is compatible with ADO.NET.</span></span> <span data-ttu-id="de362-114">有关 Sync Framework 数据库同步组件的详细文档，请参阅 [同步数据库](https://go.microsoft.com/fwlink/?LinkId=209079)。</span><span class="sxs-lookup"><span data-stu-id="de362-114">For detailed documentation of the Sync Framework database synchronization components, see [Synchronizing Databases](https://go.microsoft.com/fwlink/?LinkId=209079).</span></span> <span data-ttu-id="de362-115">有关 Sync Framework 的概述，请参阅 [Microsoft Sync Framework 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=209078)。</span><span class="sxs-lookup"><span data-stu-id="de362-115">For an overview of Sync Framework, see [Microsoft Sync Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=209078).</span></span> <span data-ttu-id="de362-116">有关 Sync Framework 与合并复制的比较，请参阅 [同步数据库概述](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="de362-116">For a comparison between Sync Framework and Merge Replication, see [Synchronizing Databases Overview](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)</span></span>  
  

## <a name="whats-new"></a><span data-ttu-id="de362-117">新增功能</span><span class="sxs-lookup"><span data-stu-id="de362-117">What's new</span></span> 
- <span data-ttu-id="de362-118">SQL Server 2017 未向 SQL Server 复制引入重要的新功能。</span><span class="sxs-lookup"><span data-stu-id="de362-118">SQL Server 2017 has not introduced significant new features to SQL Server replication.</span></span> 
- <span data-ttu-id="de362-119">SQL Server 2016 未向 SQL Server 复制引入重要的新功能。</span><span class="sxs-lookup"><span data-stu-id="de362-119">SQL Server 2016 has not introduced significant new features to SQL Server replication.</span></span> 

<span data-ttu-id="de362-120">有关后向兼容性详细信息，请参阅[复制后向兼容性](replication-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="de362-120">For backward compatibility information see, [Replication Backward Compatibility](replication-backward-compatibility.md)</span></span> 


 ## <a name="replication-security"></a><span data-ttu-id="de362-121">复制安全性</span><span class="sxs-lookup"><span data-stu-id="de362-121">Replication security</span></span>
  
-   [<span data-ttu-id="de362-122">查看和修改复制安全设置</span><span class="sxs-lookup"><span data-stu-id="de362-122">View and Modify Replication Security Settings</span></span>](security/view-and-modify-replication-security-settings.md)  
-   [<span data-ttu-id="de362-123">管理发布访问列表中的登录名</span><span class="sxs-lookup"><span data-stu-id="de362-123">Manage Logins in the Publication Access List</span></span>](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a><span data-ttu-id="de362-124">发布和分发</span><span class="sxs-lookup"><span data-stu-id="de362-124">Publishing and Distribution</span></span>  
  
-   [<span data-ttu-id="de362-125">配置发布和分发</span><span class="sxs-lookup"><span data-stu-id="de362-125">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)   
-   [<span data-ttu-id="de362-126">查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="de362-126">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="de362-127">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="de362-127">Disable Publishing and Distribution</span></span>](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a><span data-ttu-id="de362-128">发布和项目</span><span class="sxs-lookup"><span data-stu-id="de362-128">Publications and Articles</span></span> 
  
-   [<span data-ttu-id="de362-129">创建发布</span><span class="sxs-lookup"><span data-stu-id="de362-129">Create a Publication</span></span>](publish/create-a-publication.md)    
-   [<span data-ttu-id="de362-130">定义项目</span><span class="sxs-lookup"><span data-stu-id="de362-130">Define an Article</span></span>](publish/define-an-article.md)   
-   [<span data-ttu-id="de362-131">查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="de362-131">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="de362-132">查看和修改项目属性</span><span class="sxs-lookup"><span data-stu-id="de362-132">View and Modify Article Properties</span></span>](publish/view-and-modify-article-properties.md)    
-   [<span data-ttu-id="de362-133">删除发布</span><span class="sxs-lookup"><span data-stu-id="de362-133">Delete a Publication</span></span>](publish/delete-a-publication.md)   
-   [<span data-ttu-id="de362-134">删除项目</span><span class="sxs-lookup"><span data-stu-id="de362-134">Delete an Article</span></span>](publish/delete-an-article.md)    
-   [<span data-ttu-id="de362-135">从 Oracle 数据库创建发布</span><span class="sxs-lookup"><span data-stu-id="de362-135">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   
-   [<span data-ttu-id="de362-136">设置订阅的过期期限</span><span class="sxs-lookup"><span data-stu-id="de362-136">Set the Expiration Period for Subscriptions</span></span>](publish/set-the-expiration-period-for-subscriptions.md)  
-   [<span data-ttu-id="de362-137">指定架构选项</span><span class="sxs-lookup"><span data-stu-id="de362-137">Specify Schema Options</span></span>](publish/specify-schema-options.md)  
-   [<span data-ttu-id="de362-138">复制架构更改</span><span class="sxs-lookup"><span data-stu-id="de362-138">Replicate Schema Changes</span></span>](publish/replicate-schema-changes.md)    
-   [<span data-ttu-id="de362-139">管理标识列</span><span class="sxs-lookup"><span data-stu-id="de362-139">Manage Identity Columns</span></span>](publish/manage-identity-columns.md)   
-   [<span data-ttu-id="de362-140">设置合并发布的兼容级别</span><span class="sxs-lookup"><span data-stu-id="de362-140">Set the Compatibility Level for Merge Publications</span></span>](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a><span data-ttu-id="de362-141">快照选项</span><span class="sxs-lookup"><span data-stu-id="de362-141">Snapshot Options</span></span>  
  
-   [<span data-ttu-id="de362-142">配置快照属性</span><span class="sxs-lookup"><span data-stu-id="de362-142">Configure Snapshot Properties</span></span>](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-143">通过 FTP 传递快照</span><span class="sxs-lookup"><span data-stu-id="de362-143">Deliver a Snapshot Through FTP</span></span>](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a><span data-ttu-id="de362-144">筛选数据</span><span class="sxs-lookup"><span data-stu-id="de362-144">Filter Data</span></span>  
  
-   [<span data-ttu-id="de362-145">定义和修改列筛选器</span><span class="sxs-lookup"><span data-stu-id="de362-145">Define and Modify a Column Filter</span></span>](publish/define-and-modify-a-column-filter.md)    
-   [<span data-ttu-id="de362-146">定义和修改静态行筛选器</span><span class="sxs-lookup"><span data-stu-id="de362-146">Define and Modify a Static Row Filter</span></span>](publish/define-and-modify-a-static-row-filter.md)    
-   [<span data-ttu-id="de362-147">定义和修改合并项目的参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="de362-147">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [<span data-ttu-id="de362-148">优化参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="de362-148">Optimize Parameterized Row Filters</span></span>](publish/optimize-parameterized-row-filters.md)    
-   [<span data-ttu-id="de362-149">定义和修改合并项目间的联接筛选器</span><span class="sxs-lookup"><span data-stu-id="de362-149">Define and Modify a Join Filter Between Merge Articles</span></span>](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a><span data-ttu-id="de362-150">事务复制选项</span><span class="sxs-lookup"><span data-stu-id="de362-150">Transactional Replication Options</span></span>  
  
-   [<span data-ttu-id="de362-151">为事务项目的数据更改设置传播方法</span><span class="sxs-lookup"><span data-stu-id="de362-151">Set the Propagation Method for Data Changes to Transactional Articles</span></span>](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [<span data-ttu-id="de362-152">允许更新事务发布的订阅</span><span class="sxs-lookup"><span data-stu-id="de362-152">Enable Updating Subscriptions for Transactional Publications</span></span>](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a><span data-ttu-id="de362-153">合并复制选项</span><span class="sxs-lookup"><span data-stu-id="de362-153">Merge Replication Options</span></span>  
  
-   [<span data-ttu-id="de362-154">定义合并表项目间的逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="de362-154">Define a Logical Record Relationship Between Merge Table Articles</span></span>](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [<span data-ttu-id="de362-155">指定合并复制属性</span><span class="sxs-lookup"><span data-stu-id="de362-155">Specify Merge replication properties</span></span>](publish/specify-merge-replication-properties.md)    
-   [<span data-ttu-id="de362-156">指定合并项目冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="de362-156">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a><span data-ttu-id="de362-157">管理订阅</span><span class="sxs-lookup"><span data-stu-id="de362-157">Manage Subscriptions</span></span>  
  
-   [<span data-ttu-id="de362-158">创建请求订阅</span><span class="sxs-lookup"><span data-stu-id="de362-158">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)    
-   [<span data-ttu-id="de362-159">查看和修改请求订阅属性</span><span class="sxs-lookup"><span data-stu-id="de362-159">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)    
-   [<span data-ttu-id="de362-160">删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="de362-160">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)    
-   [<span data-ttu-id="de362-161">创建推送订阅</span><span class="sxs-lookup"><span data-stu-id="de362-161">Create a Push Subscription</span></span>](create-a-push-subscription.md)   
-   [<span data-ttu-id="de362-162">查看和修改推送订阅属性</span><span class="sxs-lookup"><span data-stu-id="de362-162">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)   
-   [<span data-ttu-id="de362-163">删除推送订阅</span><span class="sxs-lookup"><span data-stu-id="de362-163">Delete a Push Subscription</span></span>](delete-a-push-subscription.md)   
-   [<span data-ttu-id="de362-164">指定同步计划</span><span class="sxs-lookup"><span data-stu-id="de362-164">Specify Synchronization Schedules</span></span>](specify-synchronization-schedules.md)    
-   [<span data-ttu-id="de362-165">创建事务发布的可更新订阅</span><span class="sxs-lookup"><span data-stu-id="de362-165">Create an Updatable Subscription to a Transactional Publication</span></span>](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [<span data-ttu-id="de362-166">为非 SQL Server 订阅服务器创建订阅</span><span class="sxs-lookup"><span data-stu-id="de362-166">Create a Subscription for a Non-SQL Server Subscriber</span></span>](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a><span data-ttu-id="de362-167">同步订阅</span><span class="sxs-lookup"><span data-stu-id="de362-167">Synchronize Subscriptions</span></span>  
  
-   [<span data-ttu-id="de362-168">创建并应用初始快照</span><span class="sxs-lookup"><span data-stu-id="de362-168">Create and Apply the Initial Snapshot</span></span>](create-and-apply-the-initial-snapshot.md)   
-   [<span data-ttu-id="de362-169">为包含参数化筛选器的合并发布创建快照</span><span class="sxs-lookup"><span data-stu-id="de362-169">Create a Snapshot for a Merge Publication with Parameterized Filters</span></span>](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="de362-170">从备份初始化事务订阅</span><span class="sxs-lookup"><span data-stu-id="de362-170">Initialize a Transactional Subscription from a Backup</span></span>](initialize-a-transactional-subscription-from-a-backup.md)    
-   [<span data-ttu-id="de362-171">手动初始化订阅</span><span class="sxs-lookup"><span data-stu-id="de362-171">Initialize a Subscription Manually</span></span>](initialize-a-subscription-manually.md)    
-   [<span data-ttu-id="de362-172">同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="de362-172">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)    
-   [<span data-ttu-id="de362-173">同步推送订阅</span><span class="sxs-lookup"><span data-stu-id="de362-173">Synchronize a Push Subscription</span></span>](synchronize-a-push-subscription.md)   
-   [<span data-ttu-id="de362-174">重新初始化订阅</span><span class="sxs-lookup"><span data-stu-id="de362-174">Reinitialize a Subscription</span></span>](reinitialize-a-subscription.md)    
-   [<span data-ttu-id="de362-175">在同步期间执行脚本</span><span class="sxs-lookup"><span data-stu-id="de362-175">Execute Scripts During Synchronization</span></span>](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-176">为合并项目实现业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="de362-176">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [<span data-ttu-id="de362-177">调试业务逻辑处理程序（复制编程）</span><span class="sxs-lookup"><span data-stu-id="de362-177">Debug a Business Logic Handler &#40;Replication Programming&#41;</span></span>](debug-a-business-logic-handler-replication-programming.md)    
-   [<span data-ttu-id="de362-178">控制同步期间触发器和约束的行为</span><span class="sxs-lookup"><span data-stu-id="de362-178">Control the Behavior of Triggers and Constraints During Synchronization</span></span>](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [<span data-ttu-id="de362-179">为合并项目实现自定义冲突解决程序</span><span class="sxs-lookup"><span data-stu-id="de362-179">Implement a Custom Conflict Resolver for a Merge Article</span></span>](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a><span data-ttu-id="de362-180">Administeration</span><span class="sxs-lookup"><span data-stu-id="de362-180">Administeration</span></span> 
  
-   [<span data-ttu-id="de362-181">处理复制代理配置文件</span><span class="sxs-lookup"><span data-stu-id="de362-181">Work with Replication Agent Profiles</span></span>](agents/work-with-replication-agent-profiles.md)   
-   [<span data-ttu-id="de362-182">在订阅服务器上验证数据</span><span class="sxs-lookup"><span data-stu-id="de362-182">Validate Data at the Subscriber</span></span>](validate-data-at-the-subscriber.md)    
-   [<span data-ttu-id="de362-183">通过参数化筛选器为合并发布管理分区</span><span class="sxs-lookup"><span data-stu-id="de362-183">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="de362-184">将数据批量加载到合并发布的表中</span><span class="sxs-lookup"><span data-stu-id="de362-184">Bulk-Load Data into Tables in a Merge Publication</span></span>](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [<span data-ttu-id="de362-185">清除合并元数据</span><span class="sxs-lookup"><span data-stu-id="de362-185">Clean Up Merge Metadata</span></span>](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-186">执行合并项目的虚更新</span><span class="sxs-lookup"><span data-stu-id="de362-186">Perform a Dummy Update for a Merge Article</span></span>](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-187">查看分发数据库中的复制命令和其他信息</span><span class="sxs-lookup"><span data-stu-id="de362-187">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="de362-188">为事务复制启用协调备份</span><span class="sxs-lookup"><span data-stu-id="de362-188">Enable Coordinated Backups for Transactional Replication</span></span>](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [<span data-ttu-id="de362-189">管理对等拓扑</span><span class="sxs-lookup"><span data-stu-id="de362-189">Administer a Peer-to-Peer Topology</span></span>](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-190">静止复制拓扑</span><span class="sxs-lookup"><span data-stu-id="de362-190">Quiesce a Replication Topology</span></span>](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="de362-191">为 Oracle 发布服务器配置事务集作业</span><span class="sxs-lookup"><span data-stu-id="de362-191">Configure the Transaction Set Job for an Oracle Publisher</span></span>](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [<span data-ttu-id="de362-192">升级复制脚本</span><span class="sxs-lookup"><span data-stu-id="de362-192">Upgrade Replication Scripts</span></span>](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a><span data-ttu-id="de362-193">监视</span><span class="sxs-lookup"><span data-stu-id="de362-193">Monitor</span></span>
  
-   [<span data-ttu-id="de362-194">允许非管理员使用复制监视器</span><span class="sxs-lookup"><span data-stu-id="de362-194">Allow Non-Administrators to Use Replication Monitor</span></span>](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [<span data-ttu-id="de362-195">以编程方式监视复制</span><span class="sxs-lookup"><span data-stu-id="de362-195">Programmatically Monitor Replication</span></span>](monitor/programmatically-monitor-replication.md)    
-   [<span data-ttu-id="de362-196">查看分发数据库中的复制命令和其他信息</span><span class="sxs-lookup"><span data-stu-id="de362-196">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="de362-197">查看合并发布的冲突信息</span><span class="sxs-lookup"><span data-stu-id="de362-197">View Conflict Information for Merge Publications</span></span>](view-conflict-information-for-merge-publications.md) 
-   [<span data-ttu-id="de362-198">为事务复制测量滞后时间和验证连接</span><span class="sxs-lookup"><span data-stu-id="de362-198">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  