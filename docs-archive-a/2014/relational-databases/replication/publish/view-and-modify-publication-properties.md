---
title: 查看和修改发布属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 89b969bc3e285bbdc633a2b39d237968b216069a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577527"
---
# <a name="view-and-modify-publication-properties"></a><span data-ttu-id="2ee7f-102">查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-102">View and Modify Publication Properties</span></span>
  <span data-ttu-id="2ee7f-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中查看和修改发布属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-103">This topic describes how to view and modify publication properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="2ee7f-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2ee7f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2ee7f-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2ee7f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2ee7f-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2ee7f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2ee7f-107">建议</span><span class="sxs-lookup"><span data-stu-id="2ee7f-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2ee7f-108">**查看和修改发布属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="2ee7f-108">**To view and modify publication properties, using:**</span></span>  
  
     [<span data-ttu-id="2ee7f-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ee7f-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2ee7f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ee7f-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="2ee7f-111">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2ee7f-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ee7f-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="2ee7f-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2ee7f-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2ee7f-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2ee7f-114">创建复制后，有些属性便不可以再进行修改，如果该发布存在订阅，则其他属性也无法再进行修改。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="2ee7f-115">不能进行修改的属性将显示为只读。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2ee7f-116">建议</span><span class="sxs-lookup"><span data-stu-id="2ee7f-116">Recommendations</span></span>  
  
-   <span data-ttu-id="2ee7f-117">创建发布之后，某些属性更改要求新的快照。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="2ee7f-118">如果发布具有多个订阅，某些更改还会要求重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="2ee7f-119">有关详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)和[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ee7f-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ee7f-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2ee7f-121">可在“发布属性 - \<Publication>”对话框（在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 和复制监视器中可用）中查看和修改发布属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-121">View and modify publication properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="2ee7f-122">有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="2ee7f-123">“发布属性 - \<Publication>”对话框中包括以下页面：</span><span class="sxs-lookup"><span data-stu-id="2ee7f-123">The **Publication Properties - \<Publication>** dialog box includes the following pages:</span></span>  
  
-   <span data-ttu-id="2ee7f-124">**“常规”** 页，包含发布名称和说明、数据库名称、发布类型以及订阅过期设置。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-124">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="2ee7f-125">**“项目”** 页，对应于新建发布向导中的 **“项目”** 页。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-125">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="2ee7f-126">使用此页可添加和删除项目，以及更改项目的属性和列筛选。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-126">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="2ee7f-127">**“筛选行”** 页，对应于新建发布向导中的 **“筛选表行”** 页。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-127">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="2ee7f-128">使用此页可添加、编辑和删除所有发布类型的静态行筛选器，以及添加、编辑和删除合并发布的参数化行筛选器和联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-128">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="2ee7f-129">**“快照”** 页，使您可以指定快照的格式和位置、快照是否压缩，以及应用快照前后要运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-129">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="2ee7f-130">**“FTP 快照”** 页（适用于快照和事务发布，以及运行 SQL Server 2005 之前版本的发布服务器的合并发布），使您可以指定订阅服务器是否可以通过文件传输协议 (FTP) 下载快照文件。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-130">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="2ee7f-131">**“FTP 快照和 Internet”** 页（适用于运行 SQL Server 2005 或更高版本的发布服务器的合并发布），使您可以指定订阅服务器是否可以通过 FTP 下载快照文件，以及订阅服务器是否可以通过 HTTPS 对订阅进行同步。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-131">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="2ee7f-132">**“订阅选项”** 页，使您可以设置多个应用于所有订阅的选项。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-132">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="2ee7f-133">这些选项会随着发布类型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-133">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="2ee7f-134">**“发布访问列表”** 页，使您可以指定可以访问发布的登录名和组。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-134">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="2ee7f-135">**“代理安全性”** 页，使您可以访问用于运行下列代理并连接复制拓扑中计算机的帐户设置：所有发布的快照代理、所有事务发布的日志读取器代理以及允许排队更新订阅的事务发布的队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-135">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="2ee7f-136">**“数据分区”** 页（适用于来自运行 SQL Server 2005 或更高版本的发布服务器的合并发布），使您可以指定在快照不可用时使用参数化筛选器的发布的订阅服务器是否可以请求快照。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-136">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="2ee7f-137">它还允许一次性或按循环计划生成一个或多个分区的快照。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-137">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a><span data-ttu-id="2ee7f-138">在 Management Studio 中查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-138">To view and modify publication properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="2ee7f-139">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到发布服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-139">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="2ee7f-140">展开 **“复制”** 文件夹，再展开 **“本地发布”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-140">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="2ee7f-141">右键单击发布，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-141">Right-click a publication, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="2ee7f-142">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-142">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a><span data-ttu-id="2ee7f-143">在复制监视器中查看和修改发布属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-143">To view and modify publication properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="2ee7f-144">在复制监视器的左侧窗格中展开发布服务器组，然后展开一个发布服务器。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-144">Expand a Publisher group in the left pane of Replication Monitor, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="2ee7f-145">右键单击发布，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-145">Right-click a publication, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="2ee7f-146">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-146">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2ee7f-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ee7f-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="2ee7f-148">可以使用复制存储过程以编程方式修改发布以及返回其属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-148">Publications can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="2ee7f-149">您使用的存储过程取决于发布的类型。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-149">The stored procedures that you use will depend on the type of publication.</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2ee7f-150">查看快照发布或事务发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-150">To view the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-151">执行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)，为 \@publication 参数指定该发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-151">Execute [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="2ee7f-152">如果未指定此参数，则会返回发布服务器上所有发布的相关信息。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-152">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2ee7f-153">更改快照发布或事务发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-153">To change the properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-154">执行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，在 \@property 参数中指定要更改的发布属性，并在 \@value 参数中指定此属性的新值 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-154">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying the publication property to change in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ee7f-155">如果该更改将要求生成新快照，则还必须将 \@force_invalidate_snapshot 的值指定为 1，而如果该更改将要求重新初始化订阅服务器，则必须将 \@force_reinit_subscription 的值指定为 1   。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-155">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="2ee7f-156">有关更改时需要新快照或重新初始化的属性的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-156">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a><span data-ttu-id="2ee7f-157">查看合并发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-157">To view the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-158">执行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，为 \@publication 参数指定该发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-158">Execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span> <span data-ttu-id="2ee7f-159">如果未指定此参数，则会返回发布服务器上所有发布的相关信息。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-159">If you do not specify this parameter, information on all publications at the Publisher is returned.</span></span>  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a><span data-ttu-id="2ee7f-160">更改合并发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-160">To change the properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-161">执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，在 \@property 参数中指定要更改的发布属性，并在 \@value 参数中指定此属性的新值 。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-161">Execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying the publication property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ee7f-162">如果该更改将要求生成新快照，则还必须将 \@force_invalidate_snapshot 的值指定为 1，而如果该更改将要求重新初始化订阅服务器，则必须将 \@force_reinit_subscription 的值指定为 1。有关那些在更改后要求生成新快照或重新初始化的属性的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)   。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-162">If the change will require the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change will require that Subscribers be reinitialized, you must specify a value of **1** for **\@force_reinit_subscription** For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a><span data-ttu-id="2ee7f-163">查看快照的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-163">To view the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="2ee7f-164">执行 [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql)，为 \@publication 参数指定该发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-164">Execute [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql), specifying the name of the publication for the **\@publication** parameter.</span></span>  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a><span data-ttu-id="2ee7f-165">更改快照的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-165">To change the properties of a snapshot</span></span>  
  
1.  <span data-ttu-id="2ee7f-166">执行 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)，为相应的快照参数指定一个或多个新的快照属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-166">Execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql), specifying one or more of the new snapshot properties for the appropriate snapshot parameters.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2ee7f-167">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2ee7f-167">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="2ee7f-168">此事务复制示例将返回该发布的属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-168">This transactional replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 <span data-ttu-id="2ee7f-169">此事务复制示例将为发布禁用架构复制。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-169">This transactional replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 <span data-ttu-id="2ee7f-170">此合并复制示例将返回该发布的属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-170">This merge replication example returns the properties of the publication.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 <span data-ttu-id="2ee7f-171">此合并复制示例将为发布禁用架构复制。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-171">This merge replication example disables schema replication for the publication.</span></span>  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="2ee7f-172">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2ee7f-172">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="2ee7f-173">可以使用复制管理对象 (RMO) 以编程方式修改发布以及访问其属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-173">You can modify publications and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="2ee7f-174">查看或修改发布属性所使用的 RMO 类取决于发布的类型。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-174">The RMO classes that you use to view or modify publication properties depend on the type of publication.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2ee7f-175">查看或修改快照发布或事务发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-175">To view or modify properties of a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2ee7f-177">创建 <xref:Microsoft.SqlServer.Replication.TransPublication> 类的实例，为发布设置 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为在步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="2ee7f-178">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="2ee7f-179">如果此方法返回 `false`，则说明步骤 2 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-179">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="2ee7f-180">（可选）若要更改属性，为一个或多个可设置的属性设置新值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-180">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="2ee7f-181">使用逻辑 AND 运算符（在 Microsoft Visual C# 中为 `&`，在 Microsoft Visual Basic 中为 `And`）可确定是否为 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 属性设置了给定的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-181">Use the logical AND operator (`&` in Microsoft Visual C# and `And` in Microsoft Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="2ee7f-182">使用逻辑 OR 运算符（在 Visual C# 中为 `|`，在 Visual Basic 中为 `Or`）和逻辑异或运算符（在 Visual C# 中为 `^`，在 Visual Basic 中为 `Xor`）可更改 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 属性的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-182">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="2ee7f-183">（可选）如果已将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法以在服务器上提交更改。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-183">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="2ee7f-184">如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `false`（默认值），则会将更改立即发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-184">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a><span data-ttu-id="2ee7f-185">查看或修改合并发布的属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-185">To view or modify properties of a merge publication</span></span>  
  
1.  <span data-ttu-id="2ee7f-186">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-186">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2ee7f-187">创建 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例，为发布设置 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为在步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-187">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="2ee7f-188">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-188">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="2ee7f-189">如果此方法返回 `false`，则说明步骤 2 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-189">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="2ee7f-190">（可选）若要更改属性，为一个或多个可设置的属性设置新值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-190">(Optional) To change properties, set a new value for one or more of the settable properties.</span></span> <span data-ttu-id="2ee7f-191">使用逻辑 AND 运算符（在 Visual C# 中为 `&`，在 Visual Basic 中为 `And`）可确定是否为 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 属性设置了给定的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-191">Use the logical AND operator (`&` in Visual C# and `And` in Visual Basic) to determine if a given <xref:Microsoft.SqlServer.Replication.PublicationAttributes> value is set for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span> <span data-ttu-id="2ee7f-192">使用逻辑 OR 运算符（在 Visual C# 中为 `|`，在 Visual Basic 中为 `Or`）和逻辑异或运算符（在 Visual C# 中为 `^`，在 Visual Basic 中为 `Xor`）可更改 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> 属性的 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-192">Use the inclusive logical OR operator (`|` in Visual C# and `Or` in Visual Basic) and the exclusive logical OR operator (`^` in Visual C# and `Xor` in Visual Basic) to change the <xref:Microsoft.SqlServer.Replication.PublicationAttributes> values for the <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> property.</span></span>  
  
5.  <span data-ttu-id="2ee7f-193">（可选）如果已将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法以在服务器上提交更改。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-193">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="2ee7f-194">如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `false`（默认值），则会将更改立即发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-194">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="2ee7f-195">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2ee7f-195">Examples (RMO)</span></span>  
 <span data-ttu-id="2ee7f-196">该示例设置事务发布的发布属性。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-196">This example sets publication attributes for a transactional publication.</span></span> <span data-ttu-id="2ee7f-197">这些更改将被缓存，直至将其显式发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-197">The changes are cached until explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 <span data-ttu-id="2ee7f-198">该示例禁用合并发布的 DDL 复制。</span><span class="sxs-lookup"><span data-stu-id="2ee7f-198">This example disables DDL replication for a merge publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a><span data-ttu-id="2ee7f-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ee7f-199">See Also</span></span>  
 <span data-ttu-id="2ee7f-200">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-200">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="2ee7f-201">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-201">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="2ee7f-202">[对发布数据库进行架构更改](make-schema-changes-on-publication-databases.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-202">[Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md) </span></span>  
 <span data-ttu-id="2ee7f-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-203">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="2ee7f-204">[向发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-204">[Add Articles to and Drop Articles from a Publication](add-articles-to-and-drop-articles-from-a-publication.md) </span></span>  
 <span data-ttu-id="2ee7f-205">[使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2ee7f-205">[View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="2ee7f-206">查看和修改项目属性</span><span class="sxs-lookup"><span data-stu-id="2ee7f-206">View and Modify Article Properties</span></span>](view-and-modify-article-properties.md)  
  
  
