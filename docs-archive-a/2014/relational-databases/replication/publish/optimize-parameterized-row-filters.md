---
title: 优化参数化行筛选器 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1c6448d8e2dba7a68fab441d4d08fd4a4a1db4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693247"
---
# <a name="optimize-parameterized-row-filters"></a><span data-ttu-id="2177e-102">优化参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="2177e-102">Optimize Parameterized Row Filters</span></span>
  <span data-ttu-id="2177e-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中优化参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="2177e-103">This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2177e-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2177e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2177e-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2177e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2177e-106">建议</span><span class="sxs-lookup"><span data-stu-id="2177e-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2177e-107">**优化参数化行筛选器，使用：**</span><span class="sxs-lookup"><span data-stu-id="2177e-107">**To optimize parameterized row filters, using:**</span></span>  
  
     [<span data-ttu-id="2177e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2177e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2177e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2177e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2177e-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="2177e-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2177e-111">建议</span><span class="sxs-lookup"><span data-stu-id="2177e-111">Recommendations</span></span>  
  
-   <span data-ttu-id="2177e-112">当使用参数化筛选器时，可通过在创建发布时指定 **use partition groups** 或 **keep partition changes** 选项来控制合并复制处理筛选器的方式。</span><span class="sxs-lookup"><span data-stu-id="2177e-112">When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication.</span></span> <span data-ttu-id="2177e-113">通过将其他元数据存储在发布数据库中，上述选项可提高具有已筛选项目的发布的同步性能。</span><span class="sxs-lookup"><span data-stu-id="2177e-113">These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database.</span></span> <span data-ttu-id="2177e-114">通过在创建项目时设置 **partition options** ，您可以控制在订阅服务器之间共享数据的方式。</span><span class="sxs-lookup"><span data-stu-id="2177e-114">You can control how the data is shared among Subscribers by setting **partition options** when you create an article.</span></span> <span data-ttu-id="2177e-115">有关这些要求的详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-115">For more information about these requirements, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="2177e-116">使用 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact 订阅服务器时，keep_partition_changes 必须设置为 true 以确保正确传播删除操作。</span><span class="sxs-lookup"><span data-stu-id="2177e-116">With [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated.</span></span> <span data-ttu-id="2177e-117">设置为 false 时，订阅服务器可能有比预期更多的行。</span><span class="sxs-lookup"><span data-stu-id="2177e-117">When set to false, the subscriber might have more rows than expected.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2177e-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2177e-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2177e-119">以下设置可用于优化参数化行筛选器：</span><span class="sxs-lookup"><span data-stu-id="2177e-119">The following settings can be used to optimize parameterized row filters:</span></span>  
  
 <span data-ttu-id="2177e-120">**Partition Options**</span><span class="sxs-lookup"><span data-stu-id="2177e-120">**Partition Options**</span></span>  
 <span data-ttu-id="2177e-121">可在“项目属性 - \<Article>”对话框的“属性”页，或在“添加筛选器”对话框中设置此选项。  </span><span class="sxs-lookup"><span data-stu-id="2177e-121">Set this option on the **Properties** page of the **Article Properties - \<Article>** dialog box, or in the **Add Filter** dialog box.</span></span> <span data-ttu-id="2177e-122">两个对话框都可在新建发布向导和“发布属性 - \<Publication>”对话框中获得。</span><span class="sxs-lookup"><span data-stu-id="2177e-122">Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2177e-123">通过“项目属性 - \<Article>”对话框可以为此选项指定在“添加筛选器”对话框中不可用的其他值。 </span><span class="sxs-lookup"><span data-stu-id="2177e-123">The **Article Properties - \<Article>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.</span></span>  
  
 <span data-ttu-id="2177e-124">**预计算分区**</span><span class="sxs-lookup"><span data-stu-id="2177e-124">**Precompute Partitions**</span></span>  
 <span data-ttu-id="2177e-125">如果发布中的项目符合一组要求，则此选项在默认情况下将设置为 **True** 。</span><span class="sxs-lookup"><span data-stu-id="2177e-125">This option is set to **True** by default if the articles in your publication adhere to a set of requirements.</span></span> <span data-ttu-id="2177e-126">有关这些要求的详细信息，请参阅[使用预计算分区优化参数化筛选器性能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-126">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="2177e-127">可在“发布属性 - \<Publication>”对话框的“订阅选项”页上修改此选项。 </span><span class="sxs-lookup"><span data-stu-id="2177e-127">Modify this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="2177e-128">**优化同步**</span><span class="sxs-lookup"><span data-stu-id="2177e-128">**Optimize Synchronization**</span></span>  
 <span data-ttu-id="2177e-129">仅当 **“预计算分区”** 设置为 **False** 时此选项才应设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="2177e-129">This option should be set to **True** only if **Precompute Partitions** is set to **False**.</span></span> <span data-ttu-id="2177e-130">可在“发布属性 - \<Publication>”对话框的“订阅选项”页上设置此选项。 </span><span class="sxs-lookup"><span data-stu-id="2177e-130">Set this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="2177e-131">有关如何使用新建发布向导和如何访问“发布属性 - \<Publication>”对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-131">For more information about using the New Publication Wizard and accessing the **Publication Properties - \<Publication>** dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a><span data-ttu-id="2177e-132">在“添加筛选器”或“编辑筛选器”对话框中设置分区选项。</span><span class="sxs-lookup"><span data-stu-id="2177e-132">To set Partition options in the Add Filter or Edit Filter dialog box</span></span>  
  
1.  <span data-ttu-id="2177e-133">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”对话框的“筛选行”页上，单击“添加”，然后单击“添加筛选器”。    </span><span class="sxs-lookup"><span data-stu-id="2177e-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="2177e-134">创建参数化筛选器。</span><span class="sxs-lookup"><span data-stu-id="2177e-134">Create a parameterized filter.</span></span> <span data-ttu-id="2177e-135">有关详细信息，请参阅 [定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-135">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="2177e-136">选择指示订阅服务器之间如何共享数据的选项：</span><span class="sxs-lookup"><span data-stu-id="2177e-136">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="2177e-137">**此表中的行将转到多个订阅**</span><span class="sxs-lookup"><span data-stu-id="2177e-137">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="2177e-138">**此表中的行将仅转到一个订阅**</span><span class="sxs-lookup"><span data-stu-id="2177e-138">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="2177e-139">如果选择 **“此表中的行将仅转到一个订阅”** ，则合并复制可以通过存储和处理较少的元数据来优化性能。</span><span class="sxs-lookup"><span data-stu-id="2177e-139">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="2177e-140">但是，必须确保在对数据分区时不能将行复制到多个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="2177e-140">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="2177e-141">有关详细信息，请参阅主题 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)中的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="2177e-141">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="2177e-142">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="2177e-142">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a><span data-ttu-id="2177e-143">在“项目属性 - \<Article>”对话框中设置分区选项</span><span class="sxs-lookup"><span data-stu-id="2177e-143">To set Partition Options in the Article Properties - \<Article> dialog box</span></span>  
  
1.  <span data-ttu-id="2177e-144">在新建发布向导或“发布属性 - \<Publication>”对话框的“项目”页上，选择一个表，然后单击“项目属性”。  </span><span class="sxs-lookup"><span data-stu-id="2177e-144">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="2177e-145">单击 **“设置突出显示的表项目的属性”** 或 **“设置所有表项目的属性”** 。</span><span class="sxs-lookup"><span data-stu-id="2177e-145">Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.</span></span>  
  
3.  <span data-ttu-id="2177e-146">在“项目属性 - \<Article>”对话框的“属性”选项卡的“目标对象”部分中，为“分区选项”指定以下值之一：   </span><span class="sxs-lookup"><span data-stu-id="2177e-146">In the **Destination Object** section of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify one of the following values for **Partition Options**:</span></span>  
  
    -   <span data-ttu-id="2177e-147">**重叠**</span><span class="sxs-lookup"><span data-stu-id="2177e-147">**Overlapping**</span></span>  
  
    -   <span data-ttu-id="2177e-148">**重叠，不允许分区外的数据更改**</span><span class="sxs-lookup"><span data-stu-id="2177e-148">**Overlapping, disallow out-of-partition data changes**</span></span>  
  
    -   <span data-ttu-id="2177e-149">**不重叠，一个订阅**</span><span class="sxs-lookup"><span data-stu-id="2177e-149">**Nonoverlapping, single subscription**</span></span>  
  
    -   <span data-ttu-id="2177e-150">**不重叠，由所有订阅共享**</span><span class="sxs-lookup"><span data-stu-id="2177e-150">**Nonoverlapping, shared between subscriptions**</span></span>  
  
     <span data-ttu-id="2177e-151">有关这些选项以及它们与 **“添加筛选器”** 和 **“编辑筛选器”** 对话框中选项的关系的详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="2177e-151">For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="2177e-152">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框 。</span><span class="sxs-lookup"><span data-stu-id="2177e-152">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-precompute-partitions"></a><span data-ttu-id="2177e-153">设置预计算分区</span><span class="sxs-lookup"><span data-stu-id="2177e-153">To set Precompute Partitions</span></span>  
  
1.  <span data-ttu-id="2177e-154">在“发布属性 - \<Publication>”对话框的“订阅选项”页上，为“预计算分区”选项选择值。  </span><span class="sxs-lookup"><span data-stu-id="2177e-154">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value for the **Precompute Partitions** option.</span></span> <span data-ttu-id="2177e-155">在以下情况下，则此属性为只读：</span><span class="sxs-lookup"><span data-stu-id="2177e-155">The property is read-only if:</span></span>  
  
    -   <span data-ttu-id="2177e-156">发布不满足对预计算分区的要求。</span><span class="sxs-lookup"><span data-stu-id="2177e-156">The publication does not meet the requirements for precomputed partitions.</span></span>  
  
    -   <span data-ttu-id="2177e-157">尚未为发布生成快照。</span><span class="sxs-lookup"><span data-stu-id="2177e-157">A snapshot has not yet been generated for the publication.</span></span> <span data-ttu-id="2177e-158">这种情况下，该选项会显示 **“创建快照时自动设置”** 值。</span><span class="sxs-lookup"><span data-stu-id="2177e-158">In this case, the option displays a value of **Set automatically when a snapshot is created**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a><span data-ttu-id="2177e-159">设置优化同步</span><span class="sxs-lookup"><span data-stu-id="2177e-159">To set Optimize Synchronization</span></span>  
  
1.  <span data-ttu-id="2177e-160">在 "**发布属性- \<Publication> \*\* " 对话框的 "**订阅选项**" 页上，为 "**优化同步\*\*" 选项选择值 " **True** "。</span><span class="sxs-lookup"><span data-stu-id="2177e-160">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Optimize Synchronization** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2177e-161">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2177e-161">Using Transact-SQL</span></span>  
 <span data-ttu-id="2177e-162">有关\*\* \@ keep_partition_changes**和** \@ use_partition_groups\*\*的筛选选项的定义，请参阅[sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2177e-162">For definitions of the filtering options for **\@keep_partition_changes** and **\@use_partition_groups**, see [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a><span data-ttu-id="2177e-163">创建新发布时指定合并筛选器的优化</span><span class="sxs-lookup"><span data-stu-id="2177e-163">To specify merge filter optimizations when creating a new publication</span></span>  
  
1.  <span data-ttu-id="2177e-164">在发布服务器上，对发布数据库执行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2177e-164">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="2177e-165">指定\*\* \@ 发布\*\*，并将的值指定 `true` 为以下参数之一：</span><span class="sxs-lookup"><span data-stu-id="2177e-165">Specify **\@publication** and a value of `true` for one the following parameters:</span></span>  
  
    -   <span data-ttu-id="2177e-166">\*\* \@ use_partition_groups\*\*：-最高性能优化，前提是这些文章符合预计算分区的要求。</span><span class="sxs-lookup"><span data-stu-id="2177e-166">**\@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions.</span></span> <span data-ttu-id="2177e-167">有关详细信息，请参阅[使用预计算分区优化参数化筛选器性能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-167">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="2177e-168">\*\* \@ keep_partition_changes\*\* -如果无法使用预计算分区，则使用此优化。</span><span class="sxs-lookup"><span data-stu-id="2177e-168">**\@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.</span></span>  
  
2.  <span data-ttu-id="2177e-169">为发布添加一个快照作业。</span><span class="sxs-lookup"><span data-stu-id="2177e-169">Add a snapshot job for the publication.</span></span> <span data-ttu-id="2177e-170">有关详细信息，请参阅[创建发布](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-170">For more information see [Create a Publication](create-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="2177e-171">在发布服务器上，对发布数据库执行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)，并指定以下参数：</span><span class="sxs-lookup"><span data-stu-id="2177e-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), specifying the following parameters:</span></span>  
  
    -   <span data-ttu-id="2177e-172">\*\* \@ 发布\*\*-步骤1中发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2177e-172">**\@publication** - the name of the publication from step 1.</span></span>  
  
    -   <span data-ttu-id="2177e-173">\*\* \@ 文章\*\*-项目的名称</span><span class="sxs-lookup"><span data-stu-id="2177e-173">**\@article** - a name for the article</span></span>  
  
    -   <span data-ttu-id="2177e-174">\*\* \@ source_object\*\* -要发布的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="2177e-174">**\@source_object** - the database object being published.</span></span>  
  
    -   <span data-ttu-id="2177e-175">\*\* \@ subset_filterclause\*\* -用于以水平方式筛选项目的参数化筛选器子句。</span><span class="sxs-lookup"><span data-stu-id="2177e-175">**\@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.</span></span>  
  
    -   <span data-ttu-id="2177e-176">\*\* \@ partition_options\*\* -已筛选项目的分区选项。</span><span class="sxs-lookup"><span data-stu-id="2177e-176">**\@partition_options** - the partition options for the filtered article.</span></span>  
  
4.  <span data-ttu-id="2177e-177">对发布中的每个项目重复步骤 3。</span><span class="sxs-lookup"><span data-stu-id="2177e-177">Repeat step 3 for each article in the publication.</span></span>  
  
5.  <span data-ttu-id="2177e-178">（可选）在发布服务器上，对发布数据库执行 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) 以在两个项目之间定义一个联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="2177e-178">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="2177e-179">有关详细信息，请参阅 [定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-179">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a><span data-ttu-id="2177e-180">查看和修改现有发布的合并筛选器行为</span><span class="sxs-lookup"><span data-stu-id="2177e-180">To view and modify merge filter behaviors for an existing publication</span></span>  
  
1.  <span data-ttu-id="2177e-181">在发布服务器上，对发布数据库 (可选) ，执行[sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，指定\*\* \@ 发布\*\*。</span><span class="sxs-lookup"><span data-stu-id="2177e-181">(Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication**.</span></span> <span data-ttu-id="2177e-182">请注意结果集中 **keep_partition_changes** 和 **use_partition_groups** 的值。</span><span class="sxs-lookup"><span data-stu-id="2177e-182">Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.</span></span>  
  
2.  <span data-ttu-id="2177e-183">（可选）在发布服务器上，对发布数据库执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2177e-183">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="2177e-184">为 " \*\* \@ 属性**" 指定**use_partition_groups\*\*的值，为 "值" 指定 `true` 或 `false` 。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="2177e-184">Specify a value of **use_partition_groups** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
3.  <span data-ttu-id="2177e-185">（可选）在发布服务器上，对发布数据库执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2177e-185">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="2177e-186">为 " \*\* \@ 属性**" 指定**keep_partition_changes\*\*的值，为 "值" 指定 `true` 或 `false` 。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="2177e-186">Specify a value of **keep_partition_changes** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2177e-187">启用**keep_partition_changes**时，必须首先禁用**use_partition_groups**并将\*\* \@ force_reinit_subscription**的值指定为**1\*\* 。</span><span class="sxs-lookup"><span data-stu-id="2177e-187">When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
4.  <span data-ttu-id="2177e-188">（可选）在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2177e-188">(Optional) At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2177e-189">为 " \*\* \@ 属性**" 指定**partition_options**的值，并为 " \*\* \@ 值**" 指定相应的值。</span><span class="sxs-lookup"><span data-stu-id="2177e-189">Specify a value of **partition_options** for **\@property** and the appropriate value for **\@value**.</span></span> <span data-ttu-id="2177e-190">有关以上筛选选项的定义，请参阅 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2177e-190">See [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) for definitions of these filtering options.</span></span>  
  
5.  <span data-ttu-id="2177e-191">（可选）启动快照代理以重新生成快照（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="2177e-191">(Optional) Start the Snapshot Agent to regenerate the snapshot if necessary.</span></span> <span data-ttu-id="2177e-192">有关哪些更改需要生成新快照的信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2177e-192">For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2177e-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2177e-193">See Also</span></span>  
 <span data-ttu-id="2177e-194">[在合并项目之间自动生成一组联接筛选器 &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="2177e-194">[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span></span>  
 <span data-ttu-id="2177e-195">[定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="2177e-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 [<span data-ttu-id="2177e-196">参数化行筛选器</span><span class="sxs-lookup"><span data-stu-id="2177e-196">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
