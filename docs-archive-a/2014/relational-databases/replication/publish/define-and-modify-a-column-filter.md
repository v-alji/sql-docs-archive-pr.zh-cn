---
title: 定义和修改列筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a655976f925f83d8c9446cab99016f32ab14887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591254"
---
# <a name="define-and-modify-a-column-filter"></a><span data-ttu-id="2da7d-102">定义和修改列筛选器</span><span class="sxs-lookup"><span data-stu-id="2da7d-102">Define and Modify a Column Filter</span></span>
  <span data-ttu-id="2da7d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义和修改列筛选器。</span><span class="sxs-lookup"><span data-stu-id="2da7d-103">This topic describes how to define and modify a column filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2da7d-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2da7d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2da7d-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2da7d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2da7d-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2da7d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="2da7d-107">**定义和修改列筛选器，使用：**</span><span class="sxs-lookup"><span data-stu-id="2da7d-107">**To define and modify a column filter, using:**</span></span>  
  
     [<span data-ttu-id="2da7d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2da7d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2da7d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2da7d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2da7d-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="2da7d-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2da7d-111">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2da7d-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2da7d-112">某些列无法筛选；有关详细信息，请参阅[筛选已发布数据](filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-112">Some columns cannot be filtered; for more information, see [Filter Published Data](filter-published-data.md).</span></span> <span data-ttu-id="2da7d-113">如果在初始化订阅之后修改了列筛选器，则必须在更改后生成新的快照并重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="2da7d-113">If you modify a column filter after subscriptions have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="2da7d-114">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2da7d-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2da7d-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2da7d-116">可以在新建发布向导的 **“项目”** 页上定义列筛选器。</span><span class="sxs-lookup"><span data-stu-id="2da7d-116">Define column filters on the **Articles** page of the New Publication Wizard.</span></span> <span data-ttu-id="2da7d-117">有关使用新建发布向导的详细信息，请参阅[创建发布](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-117">For more information about using the New Publication Wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="2da7d-118">在“发布属性 - \<Publication>”对话框的“项目”页面上定义和修改列筛选器 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-118">Define and modify column filters on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2da7d-119">有关发布和项目属性的详细信息，请参阅[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-119">For more information about publication and article properties, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-column-filter"></a><span data-ttu-id="2da7d-120">定义列筛选器</span><span class="sxs-lookup"><span data-stu-id="2da7d-120">To define a column filter</span></span>  
  
1.  <span data-ttu-id="2da7d-121">在新建发布向导的 **“项目”** 页上，在 **“要发布的对象”** 窗格中展开要筛选的表。</span><span class="sxs-lookup"><span data-stu-id="2da7d-121">On the **Articles** page of the New Publication Wizard, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="2da7d-122">清除要筛选的每个列旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="2da7d-122">Clear the check box next to each column you want to filter.</span></span>  
  
#### <a name="to-modify-column-filtering"></a><span data-ttu-id="2da7d-123">修改列筛选</span><span class="sxs-lookup"><span data-stu-id="2da7d-123">To modify column filtering</span></span>  
  
1.  <span data-ttu-id="2da7d-124">在“发布属性 - \<Publication>”对话框的“项目”页面上，在“要发布的对象”窗格中展开要筛选的表  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-124">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, expand the table to be filtered in the **Objects to publish** pane.</span></span>  
  
2.  <span data-ttu-id="2da7d-125">清除要筛选的每个列旁边的复选框，并确保选中每个应包含在项目中的列的复选框。</span><span class="sxs-lookup"><span data-stu-id="2da7d-125">Clear the check box next to each column you want to filter, and ensure that the check box is selected for each column that should be included in the article.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2da7d-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2da7d-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="2da7d-127">在创建表项目时，您可以定义要在项目中包含的列以及在定义项目后更改列。</span><span class="sxs-lookup"><span data-stu-id="2da7d-127">When creating table articles, you can define which columns to include in the article and change the columns after the article has been defined.</span></span> <span data-ttu-id="2da7d-128">您可以使用复制存储过程以编程的方式创建和修改已筛选的列。</span><span class="sxs-lookup"><span data-stu-id="2da7d-128">You can create and modify filtered columns programmatically using replication stored procedures.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2da7d-129">下列过程假定基础表未发生更改。</span><span class="sxs-lookup"><span data-stu-id="2da7d-129">The following procedures assume that the underlying table has not changed.</span></span> <span data-ttu-id="2da7d-130">有关将数据定义语言 (DDL) 更改复制到已发布表的信息，请参阅[对发布数据库进行架构更改](make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-130">For information on replicating data definition language (DDL) changes to published tables, see [Make Schema Changes on Publication Databases](make-schema-changes-on-publication-databases.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2da7d-131">为快照发布或事务发布中发布的项目定义列筛选器</span><span class="sxs-lookup"><span data-stu-id="2da7d-131">To define a column filter for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2da7d-132">定义要筛选的项目。</span><span class="sxs-lookup"><span data-stu-id="2da7d-132">Define the article to filter.</span></span> <span data-ttu-id="2da7d-133">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-133">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="2da7d-134">在发布服务器的发布数据库中，执行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-134">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql).</span></span> <span data-ttu-id="2da7d-135">这将定义要包括在项目中或要从项目中删除的列。</span><span class="sxs-lookup"><span data-stu-id="2da7d-135">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="2da7d-136">如果仅发布拥有许多列的表中的几个列，请对要添加的每个列执行一次 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-136">If publishing only a few columns from a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="2da7d-137">为 \@column 指定列名称并将 \@operation 的值指定为 add  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-137">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="2da7d-138">如果发布拥有许多列的表中的大部分列，请执行 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)，同时将 \@column 的值指定为 null 并将 \@operation 的值指定为 add，以添加所有列   。</span><span class="sxs-lookup"><span data-stu-id="2da7d-138">If publishing most of the columns in a table with many columns, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="2da7d-139">然后，对每个要排除的列执行一次 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql)，同时将 \@operation 的值指定为 drop，并为 \@column 指定排除的列名称  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-139">Then execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
3.  <span data-ttu-id="2da7d-140">在发布服务器的发布数据库中，执行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-140">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="2da7d-141">为 \@publication 指定发布名称并为 \@article 指定已筛选项目的名称  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-141">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="2da7d-142">这将为筛选的项目创建同步对象。</span><span class="sxs-lookup"><span data-stu-id="2da7d-142">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2da7d-143">为快照发布或事务发布中发布的项目更改列筛选器以包括其他列</span><span class="sxs-lookup"><span data-stu-id="2da7d-143">To change a column filter to include additional columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2da7d-144">在发布服务器的发布数据库中，对要添加的每个列执行一次 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-144">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="2da7d-145">为 \@column 指定列名称并将 \@operation 的值指定为 add  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-145">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="2da7d-146">在发布服务器的发布数据库中，执行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-146">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="2da7d-147">为 \@publication 指定发布名称并为 \@article 指定已筛选项目的名称  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-147">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="2da7d-148">如果发布拥有现有订阅，请将 \@change_active 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-148">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="2da7d-149">这将为已筛选的项目重新创建同步对象。</span><span class="sxs-lookup"><span data-stu-id="2da7d-149">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="2da7d-150">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="2da7d-150">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="2da7d-151">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="2da7d-151">Reinitialize subscriptions.</span></span> <span data-ttu-id="2da7d-152">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-152">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2da7d-153">为快照发布或事务发布中发布的项目更改列筛选器以删除列</span><span class="sxs-lookup"><span data-stu-id="2da7d-153">To change a column filter to remove columns for an article published in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2da7d-154">在发布服务器的发布数据库中，对要删除的每个列执行一次 [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-154">At the Publisher on the publication database, execute [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="2da7d-155">为 \@column 指定列名称并将 \@operation 的值指定为 drop  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-155">Specify the column name for **\@column** and a value of **drop** for **\@operation**.</span></span>  
  
2.  <span data-ttu-id="2da7d-156">在发布服务器的发布数据库中，执行 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-156">At the Publisher on the publication database, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="2da7d-157">为 \@publication 指定发布名称并为 \@article 指定已筛选项目的名称  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-157">Specify the publication name for **\@publication** and the name of the filtered article for **\@article**.</span></span> <span data-ttu-id="2da7d-158">如果发布拥有现有订阅，请将 \@change_active 的值指定为 1 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-158">If the publication has existing subscriptions, specify a value of **1** for **\@change_active**.</span></span> <span data-ttu-id="2da7d-159">这将为已筛选的项目重新创建同步对象。</span><span class="sxs-lookup"><span data-stu-id="2da7d-159">This re-creates the synchronization objects for the filtered article.</span></span>  
  
3.  <span data-ttu-id="2da7d-160">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="2da7d-160">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
4.  <span data-ttu-id="2da7d-161">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="2da7d-161">Reinitialize subscriptions.</span></span> <span data-ttu-id="2da7d-162">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-162">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="2da7d-163">为合并复制中发布的项目定义列筛选器</span><span class="sxs-lookup"><span data-stu-id="2da7d-163">To define a column filter for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="2da7d-164">定义要筛选的项目。</span><span class="sxs-lookup"><span data-stu-id="2da7d-164">Define the article to filter.</span></span> <span data-ttu-id="2da7d-165">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-165">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="2da7d-166">在发布服务器的发布数据库中，执行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-166">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql).</span></span> <span data-ttu-id="2da7d-167">这将定义要包括在项目中或要从项目中删除的列。</span><span class="sxs-lookup"><span data-stu-id="2da7d-167">This defines the columns to include or remove from the article.</span></span>  
  
    -   <span data-ttu-id="2da7d-168">如果仅发布拥有许多列的表中的几个列，请对要添加的每个列执行一次 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-168">If publishing only a few columns from a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="2da7d-169">为 \@column 指定列名称并将 \@operation 的值指定为 add  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-169">Specify the column name for **\@column** and a value of **add** for **\@operation**.</span></span>  
  
    -   <span data-ttu-id="2da7d-170">如果发布拥有许多列的表中的大部分列，请执行 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)，同时将 \@column 的值指定为 null 并将 \@operation 的值指定为 add，以添加所有列   。</span><span class="sxs-lookup"><span data-stu-id="2da7d-170">If publishing most of the columns in a table with many columns, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), specifying a value of **null** for **\@column** and a value of **add** for **\@operation** to add all columns.</span></span> <span data-ttu-id="2da7d-171">然后，对每个要排除的列执行一次 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql)，同时将 \@operation 的值指定为 drop 并为 \@column 指定已排除的列名称  。</span><span class="sxs-lookup"><span data-stu-id="2da7d-171">Then execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql), once for each column being excluded, specifying a value of **drop** for **\@operation** and the excluded column name for **\@column**.</span></span>  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="2da7d-172">为合并发布中发布的项目更改列筛选器以包括其他列</span><span class="sxs-lookup"><span data-stu-id="2da7d-172">To change a column filter to include additional columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="2da7d-173">在发布服务器的发布数据库中，对要添加的每个列执行一次 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-173">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being added.</span></span> <span data-ttu-id="2da7d-174">为 \@column 指定列名称，将 \@operation 的值指定为 add，并将 \@force_invalidate_snapshot 和 \@force_reinit_subscription 的值都指定为 1     。</span><span class="sxs-lookup"><span data-stu-id="2da7d-174">Specify the column name for **\@column**, a value of **add** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="2da7d-175">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="2da7d-175">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="2da7d-176">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="2da7d-176">Reinitialize subscriptions.</span></span> <span data-ttu-id="2da7d-177">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-177">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a><span data-ttu-id="2da7d-178">为合并发布中发布的项目更改列筛选器以删除列</span><span class="sxs-lookup"><span data-stu-id="2da7d-178">To change a column filter to remove columns for an article published in a merge publication</span></span>  
  
1.  <span data-ttu-id="2da7d-179">在发布服务器的发布数据库中，对要删除的每个列执行一次 [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2da7d-179">At the Publisher on the publication database, execute [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) once for each column being removed.</span></span> <span data-ttu-id="2da7d-180">为 \@column 指定列名称，将 \@operation 的值指定为 drop，并将 \@force_invalidate_snapshot 和 \@force_reinit_subscription 的值指定为 1     。</span><span class="sxs-lookup"><span data-stu-id="2da7d-180">Specify the column name for **\@column**, a value of **drop** for **\@operation** and a value of **1** for both **\@force_invalidate_snapshot** and **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="2da7d-181">对发布重新运行快照代理作业以生成更新的快照。</span><span class="sxs-lookup"><span data-stu-id="2da7d-181">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span>  
  
3.  <span data-ttu-id="2da7d-182">重新初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="2da7d-182">Reinitialize subscriptions.</span></span> <span data-ttu-id="2da7d-183">有关详细信息，请参阅 [重新初始化订阅](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="2da7d-183">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2da7d-184">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2da7d-184">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="2da7d-185">在此事务复制示例中， `DaysToManufacture` 列将从基于 `Product` 表的项目中删除。</span><span class="sxs-lookup"><span data-stu-id="2da7d-185">In this transactional replication example, the `DaysToManufacture` column is removed from an article based on the `Product` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="2da7d-186">在此合并复制示例中， `CreditCardApprovalCode` 列将从基于 `SalesOrderHeader` 表的项目中删除。</span><span class="sxs-lookup"><span data-stu-id="2da7d-186">In this merge replication example, the `CreditCardApprovalCode` column is removed from an article based on the `SalesOrderHeader` table.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="2da7d-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2da7d-187">See Also</span></span>  
 <span data-ttu-id="2da7d-188">[更改发布和项目属性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2da7d-188">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="2da7d-189">[筛选已发布数据](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="2da7d-189">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="2da7d-190">为合并复制筛选已发布数据</span><span class="sxs-lookup"><span data-stu-id="2da7d-190">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
