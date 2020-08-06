---
title: 查看和修改项目属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8194b5cc2d4c4a2f1f116ca5a99ea16e18156f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691173"
---
# <a name="view-and-modify-article-properties"></a><span data-ttu-id="00276-102">查看和修改项目属性</span><span class="sxs-lookup"><span data-stu-id="00276-102">View and Modify Article Properties</span></span>
  <span data-ttu-id="00276-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中查看和修改项目属性。</span><span class="sxs-lookup"><span data-stu-id="00276-103">This topic describes how to view and modify article properties in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="00276-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="00276-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="00276-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="00276-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="00276-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="00276-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="00276-107">建议</span><span class="sxs-lookup"><span data-stu-id="00276-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="00276-108">**查看和修改项目属性，使用：**</span><span class="sxs-lookup"><span data-stu-id="00276-108">**To view and modify article properties, using:**</span></span>  
  
     [<span data-ttu-id="00276-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="00276-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="00276-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00276-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="00276-111">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="00276-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="00276-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="00276-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="00276-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="00276-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="00276-114">创建复制后，有些属性便不可以再进行修改，如果该发布存在订阅，则其他属性也无法再进行修改。</span><span class="sxs-lookup"><span data-stu-id="00276-114">Some properties cannot be modified after a publication has been created, and others cannot be modified if there are subscriptions to the publication.</span></span> <span data-ttu-id="00276-115">不能进行修改的属性将显示为只读。</span><span class="sxs-lookup"><span data-stu-id="00276-115">Properties that cannot be modified are displayed as read-only.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="00276-116">建议</span><span class="sxs-lookup"><span data-stu-id="00276-116">Recommendations</span></span>  
  
-   <span data-ttu-id="00276-117">创建发布之后，某些属性更改要求新的快照。</span><span class="sxs-lookup"><span data-stu-id="00276-117">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="00276-118">如果发布具有多个订阅，某些更改还会要求重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="00276-118">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="00276-119">有关详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)和[向现有发布添加项目和从中删除项目](add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="00276-119">For more information, see [Change Publication and Article Properties](change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="00276-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="00276-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="00276-121">可在“发布属性 - \<Publication>”对话框（在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 和复制监视器中可用）中查看和修改项目属性。</span><span class="sxs-lookup"><span data-stu-id="00276-121">View and modify article properties in the **Publication Properties - \<Publication>** dialog box, which is available in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and Replication Monitor.</span></span> <span data-ttu-id="00276-122">有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="00276-122">For information about starting Replication Monitor, see [Start the Replication Monitor](../monitor/start-the-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="00276-123">**“常规”** 页，包含发布名称和说明、数据库名称、发布类型以及订阅过期设置。</span><span class="sxs-lookup"><span data-stu-id="00276-123">The **General** page includes the publication name and description, the database name, the type of publication, and the subscription expiration settings.</span></span>  
  
-   <span data-ttu-id="00276-124">**“项目”** 页，对应于新建发布向导中的 **“项目”** 页。</span><span class="sxs-lookup"><span data-stu-id="00276-124">The **Articles** page corresponds to the **Articles** page in the New Publication Wizard.</span></span> <span data-ttu-id="00276-125">使用此页可添加和删除项目，以及更改项目的属性和列筛选。</span><span class="sxs-lookup"><span data-stu-id="00276-125">Use this page to add and delete articles, and to change properties and column filtering for articles.</span></span>  
  
-   <span data-ttu-id="00276-126">**“筛选行”** 页，对应于新建发布向导中的 **“筛选表行”** 页。</span><span class="sxs-lookup"><span data-stu-id="00276-126">The **Filter Rows** page corresponds to the **Filter Table Rows** page in the New Publication Wizard.</span></span> <span data-ttu-id="00276-127">使用此页可添加、编辑和删除所有发布类型的静态行筛选器，以及添加、编辑和删除合并发布的参数化行筛选器和联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="00276-127">Use this page to add, edit, and delete static row filters for all types of publications, and to add, edit, and delete parameterized row filters and join filters for merge publications.</span></span>  
  
-   <span data-ttu-id="00276-128">**“快照”** 页，使您可以指定快照的格式和位置、快照是否压缩，以及应用快照前后要运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="00276-128">The **Snapshot** page allows you to specify the format and location of the snapshot, whether the snapshot should be compressed, and scripts to run before and after the snapshot is applied.</span></span>  
  
-   <span data-ttu-id="00276-129">**“FTP 快照”** 页（适用于快照和事务发布，以及运行 SQL Server 2005 之前版本的发布服务器的合并发布），使您可以指定订阅服务器是否可以通过文件传输协议 (FTP) 下载快照文件。</span><span class="sxs-lookup"><span data-stu-id="00276-129">The **FTP Snapshot** page (for snapshot and transactional publications, and merge publications for Publishers running versions prior to SQL Server 2005) allows you to specify whether Subscribers can download snapshot files through File Transfer Protocol (FTP).</span></span>  
  
-   <span data-ttu-id="00276-130">**“FTP 快照和 Internet”** 页（适用于运行 SQL Server 2005 或更高版本的发布服务器的合并发布），使您可以指定订阅服务器是否可以通过 FTP 下载快照文件，以及订阅服务器是否可以通过 HTTPS 对订阅进行同步。</span><span class="sxs-lookup"><span data-stu-id="00276-130">The **FTP Snapshot and Internet** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers can download snapshot files through FTP, and whether Subscribers can synchronize subscriptions through HTTPS.</span></span>  
  
-   <span data-ttu-id="00276-131">**“订阅选项”** 页，使您可以设置多个应用于所有订阅的选项。</span><span class="sxs-lookup"><span data-stu-id="00276-131">The **Subscription Options** page allows you to set a number of options that apply to all subscriptions.</span></span> <span data-ttu-id="00276-132">这些选项会随着发布类型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="00276-132">The options differ depending on the type of publication.</span></span>  
  
-   <span data-ttu-id="00276-133">**“发布访问列表”** 页，使您可以指定可以访问发布的登录名和组。</span><span class="sxs-lookup"><span data-stu-id="00276-133">The **Publication Access List** page allows you to specify which logins and groups can access a publication.</span></span>  
  
-   <span data-ttu-id="00276-134">**“代理安全性”** 页，使您可以访问用于运行下列代理并连接复制拓扑中计算机的帐户设置：所有发布的快照代理、所有事务发布的日志读取器代理以及允许排队更新订阅的事务发布的队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="00276-134">The **Agent Security** page allows you to access settings for the accounts under which the following agents run and make connections to the computers in a replication topology: the Snapshot Agent for all publications; the Log Reader Agent for all transactional publications; and the Queue Reader Agent for transactional publications that allow queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="00276-135">**“数据分区”** 页（适用于来自运行 SQL Server 2005 或更高版本的发布服务器的合并发布），使您可以指定在快照不可用时使用参数化筛选器的发布的订阅服务器是否可以请求快照。</span><span class="sxs-lookup"><span data-stu-id="00276-135">The **Data Partitions** page (for merge publications from Publishers running SQL Server 2005 or later) allows you to specify whether Subscribers to publications with parameterized filters can request a snapshot if one is not available.</span></span> <span data-ttu-id="00276-136">它还允许一次性或按循环计划生成一个或多个分区的快照。</span><span class="sxs-lookup"><span data-stu-id="00276-136">It also allows you to generate snapshots for one or more partitions, either once or on a recurring schedule.</span></span>  
  
#### <a name="to-view-and-modify-article-properties"></a><span data-ttu-id="00276-137">查看和修改项目属性</span><span class="sxs-lookup"><span data-stu-id="00276-137">To view and modify article properties</span></span>  
  
1.  <span data-ttu-id="00276-138">在“发布属性 - \<Publication>”对话框的“项目”页面上，选择一个项目，然后单击“项目属性”  。</span><span class="sxs-lookup"><span data-stu-id="00276-138">On the **Articles** Page of the **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="00276-139">选择要将更改应用于哪些项目属性：</span><span class="sxs-lookup"><span data-stu-id="00276-139">Select which articles property changes should apply to:</span></span>  
  
    -   <span data-ttu-id="00276-140">单击“设置突出显示的 \<ObjectType> 项目的属性”以启动“项目属性 - \<ObjectName>”对话框；在此对话框中进行的属性更改仅应用于在“项目”页上的对象窗格中突出显示的对象。  </span><span class="sxs-lookup"><span data-stu-id="00276-140">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="00276-141">单击“设置所有 \<ObjectType> 项目的属性”以启动“所有 \<ObjectType> 项目的属性”对话框；在此对话框中进行的属性更改应用于“项目”页上的对象窗格中该类型的所有对象，包括尚未选择进行发布的对象。  </span><span class="sxs-lookup"><span data-stu-id="00276-141">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="00276-142">在“所有 \<ObjectType> 项目的属性”对话框中进行的属性更改会替代之前在“项目属性 - \<ObjectName>”对话框中进行的任何更改。 </span><span class="sxs-lookup"><span data-stu-id="00276-142">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="00276-143">例如，若要为某对象类型的所有项目设置一些默认值，但还希望为单个对象设置一些属性，请首先设置所有项目的默认值。</span><span class="sxs-lookup"><span data-stu-id="00276-143">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="00276-144">然后再设置单个对象的属性。</span><span class="sxs-lookup"><span data-stu-id="00276-144">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="00276-145">根据需要修改属性，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="00276-145">Modify any properties if necessary, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="00276-146">在“发布属性 - \<Publication>”对话框中单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="00276-146">Click **OK** on the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="00276-147">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="00276-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="00276-148">可以使用复制存储过程以编程方式修改项目以及返回其属性。</span><span class="sxs-lookup"><span data-stu-id="00276-148">Articles can be modified and their properties returned programmatically using replication stored procedures.</span></span> <span data-ttu-id="00276-149">使用的存储过程取决于项目所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="00276-149">The stored procedures that you use depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="00276-150">查看属于快照发布或事务发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-150">To view the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="00276-151">执行[sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)，为\*\* \@ 发布**参数指定发布的名称，为** \@ 项目\*\*参数指定项目的名称。</span><span class="sxs-lookup"><span data-stu-id="00276-151">Execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="00276-152">如果不指定\*\* \@ 项目\*\*，则会为发布中的所有项目返回信息。</span><span class="sxs-lookup"><span data-stu-id="00276-152">If you do not specify **\@article**, information will be returned for all articles in the publication.</span></span>  
  
2.  <span data-ttu-id="00276-153">为表项目执行 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) 可列出基表中可用的所有列。</span><span class="sxs-lookup"><span data-stu-id="00276-153">Execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="00276-154">修改属于快照发布或事务发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-154">To modify the properties of an article belonging to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="00276-155">执行[sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)，并在\*\* \@ 属性**参数中指定要更改的项目属性，并在** \@ value\*\*参数中指定此属性的新值。</span><span class="sxs-lookup"><span data-stu-id="00276-155">Execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00276-156">如果更改需要生成新快照，则还必须将\*\* \@ force_invalidate_snapshot**的值指定为**1\*\* ，并且如果更改需要重新初始化订阅服务器，则还必须将\*\* \@ force_reinit_subscription**的值指定为**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="00276-156">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="00276-157">有关更改时需要新快照或重新初始化的属性的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="00276-157">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="00276-158">查看属于合并发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-158">To view the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="00276-159">执行[sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)，为\*\* \@ 发布**参数指定发布的名称，为** \@ 项目\*\*参数指定项目的名称。</span><span class="sxs-lookup"><span data-stu-id="00276-159">Execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql), specifying the name of the publication for the **\@publication** parameter and the name of the article for the **\@article** parameter.</span></span> <span data-ttu-id="00276-160">如果未指定这些参数，将返回为发布或发布服务器中所有项目的信息。</span><span class="sxs-lookup"><span data-stu-id="00276-160">If you do not specify these parameters, information will be returned for all articles in a publication or at the publisher.</span></span>  
  
2.  <span data-ttu-id="00276-161">为表项目执行 [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) 可列出基表中可用的所有列。</span><span class="sxs-lookup"><span data-stu-id="00276-161">Execute [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) for table articles to list all columns available in the base table.</span></span>  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a><span data-ttu-id="00276-162">修改属于合并发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-162">To modify the properties of an article belonging to a merge publication</span></span>  
  
1.  <span data-ttu-id="00276-163">执行[sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)，并在\*\* \@ 属性**参数中指定要更改的项目属性，并在** \@ value\*\*参数中指定此属性的新值。</span><span class="sxs-lookup"><span data-stu-id="00276-163">Execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), specifying the article property being changed in the **\@property** parameter and the new value of this property in the **\@value** parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00276-164">如果更改需要生成新快照，则还必须将\*\* \@ force_invalidate_snapshot**的值指定为**1\*\* ，并且如果更改需要重新初始化订阅服务器，则还必须将\*\* \@ force_reinit_subscription**的值指定为**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="00276-164">If the change requires the generation of a new snapshot, you must also specify a value of **1** for **\@force_invalidate_snapshot**, and if the change requires that Subscribers be reinitialized, you must also specify a value of **1** for **\@force_reinit_subscription**.</span></span> <span data-ttu-id="00276-165">有关更改时需要新快照或重新初始化的属性的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="00276-165">For more information on the properties that, when changed, require a new snapshot or reinitialization, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="00276-166">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="00276-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="00276-167">此事务复制示例返回了已发布项目的属性。</span><span class="sxs-lookup"><span data-stu-id="00276-167">This transactional replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_helptranarticle)]  
  
 <span data-ttu-id="00276-168">此事务复制示例更改了已发布项目的架构选项。</span><span class="sxs-lookup"><span data-stu-id="00276-168">This transactional replication example changes the schema options for the published article.</span></span>  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_changetranarticle)]  
  
 <span data-ttu-id="00276-169">此合并复制示例返回了已发布项目的属性。</span><span class="sxs-lookup"><span data-stu-id="00276-169">This merge replication example returns the properties of the published article.</span></span>  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_helpmergearticle)]  
  
 <span data-ttu-id="00276-170">此合并复制示例更改了发布项目的冲突检测设置。</span><span class="sxs-lookup"><span data-stu-id="00276-170">This merge replication example changes the conflict detection settings for a published article.</span></span>  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_changemergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="00276-171">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="00276-171">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="00276-172">可以使用复制管理对象 (RMO) 以编程方式修改项目以及访问其属性。</span><span class="sxs-lookup"><span data-stu-id="00276-172">You can modify articles and access their properties programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="00276-173">用于查看或修改项目属性的 RMO 类取决于项目所属的发布的类型。</span><span class="sxs-lookup"><span data-stu-id="00276-173">The RMO classes you use to view or modify article properties depend on the type of publication to which the article belongs.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="00276-174">查看或修改属于快照发布或事务发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-174">To view or modify properties of an article that belongs to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="00276-175">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="00276-175">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="00276-176">创建的 <xref:Microsoft.SqlServer.Replication.TransArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="00276-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransArticle> class.</span></span>  
  
3.  <span data-ttu-id="00276-177">设置 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="00276-177">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="00276-178">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="00276-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="00276-179">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="00276-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="00276-180">如果此方法返回 `false`，则说明步骤 3 中的项目属性定义不正确或此项目不存在。</span><span class="sxs-lookup"><span data-stu-id="00276-180">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="00276-181">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.TransArticle> 属性中的一个设置新值。</span><span class="sxs-lookup"><span data-stu-id="00276-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="00276-182">（可选）如果已将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法以在服务器上提交更改。</span><span class="sxs-lookup"><span data-stu-id="00276-182">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="00276-183">如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `false`（默认值），则会将更改立即发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="00276-183">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a><span data-ttu-id="00276-184">查看或修改属于合并发布的项目的属性</span><span class="sxs-lookup"><span data-stu-id="00276-184">To view or modify properties of an article that belongs to a merge publication</span></span>  
  
1.  <span data-ttu-id="00276-185">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="00276-185">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="00276-186">创建的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="00276-186">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class.</span></span>  
  
3.  <span data-ttu-id="00276-187">设置 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>和 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="00276-187">Set the <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, and <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="00276-188">为 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置步骤 1 中的连接。</span><span class="sxs-lookup"><span data-stu-id="00276-188">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="00276-189">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="00276-189">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="00276-190">如果此方法返回 `false`，则说明步骤 3 中的项目属性定义不正确或此项目不存在。</span><span class="sxs-lookup"><span data-stu-id="00276-190">If this method returns `false`, either the article properties in step 3 were defined incorrectly or the article does not exist.</span></span>  
  
6.  <span data-ttu-id="00276-191">（可选）若要更改属性，请为可以设置的 <xref:Microsoft.SqlServer.Replication.MergeArticle> 属性中的一个设置新值。</span><span class="sxs-lookup"><span data-stu-id="00276-191">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeArticle> properties that can be set.</span></span>  
  
7.  <span data-ttu-id="00276-192">（可选）如果已将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `true`，则调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法以在服务器上提交更改。</span><span class="sxs-lookup"><span data-stu-id="00276-192">(Optional) If you specified a value of `true` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit changes on the server.</span></span> <span data-ttu-id="00276-193">如果将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 的值指定为 `false`（默认值），则会将更改立即发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="00276-193">If you specified a value of `false` for <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (the default), changes are sent to the server immediately.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="00276-194">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="00276-194">Example (RMO)</span></span>  
 <span data-ttu-id="00276-195">此示例更改一个合并项目来指定该项目所使用的业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="00276-195">This example changes a merge article to specify the business logic handler used by the article.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a><span data-ttu-id="00276-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00276-196">See Also</span></span>  
 <span data-ttu-id="00276-197">[为合并项目实现业务逻辑处理程序](../implement-a-business-logic-handler-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="00276-197">[Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="00276-198">[发布数据和数据库对象](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="00276-198">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="00276-199">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="00276-199">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="00276-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="00276-200">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="00276-201">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="00276-201">Advanced Merge Replication Conflict Detection and Resolution</span></span>](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
