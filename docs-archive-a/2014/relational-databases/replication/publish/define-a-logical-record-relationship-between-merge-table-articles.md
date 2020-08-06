---
title: 定义合并表项目间的逻辑记录关系 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60c92a237562704e5bc5d43717f863aa78a14b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693731"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a><span data-ttu-id="2e13b-102">定义合并表项目间的逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-102">Define a Logical Record Relationship Between Merge Table Articles</span></span>
  <span data-ttu-id="2e13b-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或复制管理对象 (RMO) 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定义合并表项目间的逻辑记录关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-103">This topic describes how to define a logical record relationship between merge table articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="2e13b-104">通过使用合并复制，您可以定义不同表中的相关行之间的关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-104">Merge replication allows you to define a relationship between related rows in different tables.</span></span> <span data-ttu-id="2e13b-105">然后就可以在同步过程中将这些行作为一个事务单元进行处理。</span><span class="sxs-lookup"><span data-stu-id="2e13b-105">These rows can then be processed as a transactional unit during synchronization.</span></span> <span data-ttu-id="2e13b-106">无论两个项目之间是否存在联接筛选器关系，都可以在这两个项目之间定义逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2e13b-106">A logical record can be defined between two articles whether or not they have a join filter relationship.</span></span> <span data-ttu-id="2e13b-107">有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](../merge/group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-107">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="2e13b-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2e13b-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e13b-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2e13b-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e13b-110">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2e13b-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="2e13b-111">**定义合并表项目间的逻辑记录关系，使用：**</span><span class="sxs-lookup"><span data-stu-id="2e13b-111">**To define a logical record relationship between merge table articles, using:**</span></span>  
  
     [<span data-ttu-id="2e13b-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e13b-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2e13b-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e13b-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="2e13b-114">复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2e13b-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e13b-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="2e13b-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2e13b-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2e13b-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2e13b-117">如果在初始化对发布的订阅后添加、修改或删除逻辑记录，必须在更改后生成新的快照并重新初始化所有订阅。</span><span class="sxs-lookup"><span data-stu-id="2e13b-117">If you add, modify, or delete a logical record after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="2e13b-118">有关属性更改要求的详细信息，请参阅[更改发布和项目属性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e13b-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e13b-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2e13b-120">可在“添加联接”对话框（在新建发布向导和“发布属性 - \<Publication>”对话框中可用）中定义逻辑记录。 </span><span class="sxs-lookup"><span data-stu-id="2e13b-120">Define logical records in the **Add Join** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2e13b-121">有关如何使用该向导和如何访问该对话框的详细信息，请参阅[创建发布](create-a-publication.md)和[查看和修改发布属性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-121">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="2e13b-122">仅当逻辑记录应用于合并发布中的联接筛选器且发布遵循使用预计算分区的要求时，才可以在 **“添加联接”** 对话框中定义逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2e13b-122">Logical records can be defined in the **Add Join** dialog box only if they are applied to a join filter in a merge publication, and the publication follows the requirements for using precomputed partitions.</span></span> <span data-ttu-id="2e13b-123">若要定义不应用于联接筛选器的逻辑记录并在逻辑记录级设置冲突检测和解决方法，必须使用存储过程。</span><span class="sxs-lookup"><span data-stu-id="2e13b-123">To define logical records that are not applied to join filters and to set conflict detection and resolution at the logical record level, you must use stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship"></a><span data-ttu-id="2e13b-124">定义逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-124">To define a logical record relationship</span></span>  
  
1.  <span data-ttu-id="2e13b-125">在新建发布向导的“筛选表行”页或“发布属性 - \<Publication>”对话框的“筛选行”页上，在“筛选的表”窗格中选择行筛选器。   </span><span class="sxs-lookup"><span data-stu-id="2e13b-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a row filter in the **Filtered Tables** pane.</span></span>  
  
     <span data-ttu-id="2e13b-126">逻辑记录关系与扩展行筛选器的联接筛选器相关联。</span><span class="sxs-lookup"><span data-stu-id="2e13b-126">A logical record relationship is associated with a join filter, which extends a row filter.</span></span> <span data-ttu-id="2e13b-127">因此，必须定义一个行筛选器，才能用联接来扩展该筛选器并应用逻辑记录关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-127">Therefore you must define a row filter before you can extend the filter with a join and apply a logical record relationship.</span></span> <span data-ttu-id="2e13b-128">定义一个联接筛选器后，可使用其他联接筛选器来扩展此联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="2e13b-128">After one join filter is defined, you can extend this join filter with another join filter.</span></span> <span data-ttu-id="2e13b-129">有关定义联接筛选器的详细信息，请参阅 [定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-129">For more information about defining join filters, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
2.  <span data-ttu-id="2e13b-130">单击 **“添加”** ，再单击 **“添加联接以扩展所选筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-130">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="2e13b-131">在 **“添加联接”** 对话框中定义一个联接筛选器，然后选中 **“逻辑记录”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="2e13b-131">Define a join filter in the **Add Join** dialog box, and then select the check box **Logical Record**.</span></span>  
  
4.  <span data-ttu-id="2e13b-132">如果处于“发布属性 - \<Publication>”对话框中，请单击“确定”以保存并关闭该对话框。 </span><span class="sxs-lookup"><span data-stu-id="2e13b-132">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-delete-a-logical-record-relationship"></a><span data-ttu-id="2e13b-133">删除逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-133">To delete a logical record relationship</span></span>  
  
-   <span data-ttu-id="2e13b-134">只删除逻辑记录关系，或者删除逻辑记录关系及其相关联的联接筛选器。</span><span class="sxs-lookup"><span data-stu-id="2e13b-134">Delete only the logical record relationship or delete the logical record relationship and the join filter associated with it.</span></span>  
  
     <span data-ttu-id="2e13b-135">只删除逻辑记录关系：</span><span class="sxs-lookup"><span data-stu-id="2e13b-135">To delete only the logical record relationship:</span></span>  
  
    1.  <span data-ttu-id="2e13b-136">在新建发布向导的“筛选行”页或“发布属性 - \<Publication>”对话框的“筛选行”页上，在“筛选的表”窗格中选择与逻辑记录关系关联的联接筛选器，然后单击“编辑”。    </span><span class="sxs-lookup"><span data-stu-id="2e13b-136">On the **Filter Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select the join filter associated with the logical record relationship in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="2e13b-137">在 **“编辑联接”** 对话框中，清除 **“逻辑记录”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="2e13b-137">In the **Edit Join** dialog box, clear the check box **Logical Record**.</span></span>  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="2e13b-138">删除逻辑记录关系及其相关联的联接筛选器：</span><span class="sxs-lookup"><span data-stu-id="2e13b-138">To delete the logical record relationship and join filter associated with it:</span></span>  
  
    -   <span data-ttu-id="2e13b-139">在新建发布向导或“发布属性 - \<Publication>”对话框的“筛选行”页上，在“筛选的表”窗格中选择筛选器，然后单击“删除”。   </span><span class="sxs-lookup"><span data-stu-id="2e13b-139">On the **Filter Rows** page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="2e13b-140">如果删除的联接筛选器自身是由其他联接扩展而成的，则也将删除那些联接。</span><span class="sxs-lookup"><span data-stu-id="2e13b-140">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2e13b-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e13b-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="2e13b-142">您可以使用复制存储过程以编程方式指定项目之间的逻辑记录关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-142">You can programmatically specify logical record relationships between articles using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="2e13b-143">在没有关联的联接筛选器的情况下定义逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-143">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="2e13b-144">如果发布包含已筛选的任何项目，则执行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，并注意结果集中的 **use_partition_groups** 值。</span><span class="sxs-lookup"><span data-stu-id="2e13b-144">If the publication contains any articles that are filtered, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), and note the value of **use_partition_groups** in the result set.</span></span>  
  
    -   <span data-ttu-id="2e13b-145">如果值为 **1**，则已使用预计算分区。</span><span class="sxs-lookup"><span data-stu-id="2e13b-145">If the value is **1**, then precomputed partitions are already being used.</span></span>  
  
    -   <span data-ttu-id="2e13b-146">如果值为 **0**，请在发布服务器上对发布数据库执行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-146">If the value is **0**, then execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="2e13b-147">将 **use_partition_groups** 的值指定为 **@property** 并将 **@value** 的值指定为 **@value**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-147">Specify a value of **use_partition_groups** for **@property** and a value of **true** for **@value**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2e13b-148">如果发布不支持预计算分区，则无法使用逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2e13b-148">If the publication does not support precomputed partitions, then logical records cannot be used.</span></span> <span data-ttu-id="2e13b-149">有关详细信息，请参阅[使用预计算分区优化参数化筛选器性能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)主题中的“使用预计算分区的要求”。</span><span class="sxs-lookup"><span data-stu-id="2e13b-149">For more information, see Requirements for Using Precomputed Partitions in the topic [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="2e13b-150">如果值为 NULL，则需要运行快照代理以生成发布的初始快照。</span><span class="sxs-lookup"><span data-stu-id="2e13b-150">If the value is NULL, then the Snapshot Agent needs to be run to generate the initial snapshot for the publication.</span></span>  
  
2.  <span data-ttu-id="2e13b-151">如果将包含逻辑记录的项目不存在，请在发布服务器上对发布数据库执行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-151">If the articles that will comprise the logical record do not exist, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="2e13b-152">为逻辑记录指定以下冲突检测和解决选项中的一项：</span><span class="sxs-lookup"><span data-stu-id="2e13b-152">Specify one of the following conflict detection and resolution options for the logical record:</span></span>  
  
    -   <span data-ttu-id="2e13b-153">若要检测并解决发生在逻辑记录的相关行之间的冲突，请将 **@value** 的值指定为 **@logical_record_level_conflict_detection** 和 **@logical_record_level_conflict_resolution**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-153">To detect and resolve conflicts that occur within related rows in the logic record, specify a value of **true** for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**.</span></span>  
  
    -   <span data-ttu-id="2e13b-154">若要使用标准行级或列级冲突检测和解决方法，请将值指定 `false` 为，并将默认值指定为 **@logical_record_level_conflict_detection** **@logical_record_level_conflict_resolution** 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-154">To use the standard row- or column-level conflict detection and resolution, specify a value of `false` for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**, which is the default.</span></span>  
  
3.  <span data-ttu-id="2e13b-155">为每个将包含逻辑记录的项目重复步骤 2。</span><span class="sxs-lookup"><span data-stu-id="2e13b-155">Repeat step 2 for each article that will comprise the logical record.</span></span> <span data-ttu-id="2e13b-156">您必须为逻辑记录中的每个项目使用相同的冲突检测和解决选项。</span><span class="sxs-lookup"><span data-stu-id="2e13b-156">You must use the same conflict detection and resolution option for each article in the logical record.</span></span> <span data-ttu-id="2e13b-157">有关详细信息，请参阅 [检测并解决逻辑记录中的冲突](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-157">For more information, see [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
4.  <span data-ttu-id="2e13b-158">在发布服务器上，对发布数据库执行 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-158">At the publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="2e13b-159">指定 **@publication** 、关系中一个项目的名称、的第二个项目的名称、的关系的名称 **@article** **@join_articlename** **@filtername** 、定义这两个项目之间的关系的子句、的 **@join_filterclause** 联接类型 **@join_unique_key** 和以下值之一 **@filter_type** ：</span><span class="sxs-lookup"><span data-stu-id="2e13b-159">Specify **@publication**, the name of one article in the relationship for **@article**, the name of the second article for **@join_articlename**, a name for the relationship for **@filtername**, a clause that defines the relationship between the two articles for **@join_filterclause**, the type of join for **@join_unique_key** and one of the following values for **@filter_type**:</span></span>  
  
    -   <span data-ttu-id="2e13b-160">**2** - 定义逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-160">**2** - Defines a logical relationship.</span></span>  
  
    -   <span data-ttu-id="2e13b-161">**3** - 定义与联接筛选器的逻辑关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-161">**3** - Defines a logical relationship with a join filter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e13b-162">如果未使用联接筛选器，则两个项目之间的关系方向并不重要。</span><span class="sxs-lookup"><span data-stu-id="2e13b-162">If a join filter is not used, the direction of the relationship between the two articles is not important.</span></span>  
  
5.  <span data-ttu-id="2e13b-163">为发布中剩余的每个逻辑记录关系重复步骤 2。</span><span class="sxs-lookup"><span data-stu-id="2e13b-163">Repeat step 2 for each remaining logical record relationship in the publication.</span></span>  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a><span data-ttu-id="2e13b-164">为逻辑记录更改冲突检测和解决方法</span><span class="sxs-lookup"><span data-stu-id="2e13b-164">To change conflict detection and resolution for logical records</span></span>  
  
1.  <span data-ttu-id="2e13b-165">检测和解决发生在逻辑记录中相关行之间的冲突：</span><span class="sxs-lookup"><span data-stu-id="2e13b-165">To detect and resolve conflicts that occur within related rows in the logical record:</span></span>  
  
    -   <span data-ttu-id="2e13b-166">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-166">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2e13b-167">将 **@property** 的值指定为 **@property** 并将 **@value** 的值指定为 **@value**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-167">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="2e13b-168">将 **1** 的值指定为 **@force_invalidate_snapshot** 和 **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-168">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="2e13b-169">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-169">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2e13b-170">将 **@property** 的值指定为 **@property** 并将 **@value** 的值指定为 **@value**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-170">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="2e13b-171">将 **1** 的值指定为 **@force_invalidate_snapshot** 和 **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-171">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="2e13b-172">使用标准行级或列级冲突检测和解决方法：</span><span class="sxs-lookup"><span data-stu-id="2e13b-172">To use the standard row-level or column-level conflict detection and resolution:</span></span>  
  
    -   <span data-ttu-id="2e13b-173">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-173">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2e13b-174">将的值指定**logical_record_level_conflict_detection**为 logical_record_level_conflict_detection **@property** ，并将的值指定 `false` 为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-174">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="2e13b-175">将 **1** 的值指定为 **@force_invalidate_snapshot** 和 **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-175">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="2e13b-176">在发布服务器上，对发布数据库执行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-176">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2e13b-177">将的值指定**logical_record_level_conflict_resolution**为 logical_record_level_conflict_resolution **@property** ，并将的值指定 `false` 为 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-177">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="2e13b-178">将 **1** 的值指定为 **@force_invalidate_snapshot** 和 **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="2e13b-178">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
#### <a name="to-remove-a-logical-record-relationship"></a><span data-ttu-id="2e13b-179">删除逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-179">To remove a logical record relationship</span></span>  
  
1.  <span data-ttu-id="2e13b-180">在发布服务器上，对发布数据库执行以下查询，以返回有关为指定的发布定义的所有逻辑记录关系的信息：</span><span class="sxs-lookup"><span data-stu-id="2e13b-180">At the Publisher on the publication database, execute the following query to return information about all logical record relationships defined for the specified publication:</span></span>  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     <span data-ttu-id="2e13b-181">注意在结果集 `filtername` 列中的被删除逻辑记录关系的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-181">Note the name of the logical record relationship being removed in the `filtername` column in the result set.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e13b-182">该查询返回的信息与 [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql)相同；然而，该系统存储过程仅返回有关逻辑记录关系（也是联接筛选器）的信息。</span><span class="sxs-lookup"><span data-stu-id="2e13b-182">This query returns the same information as [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql); however, this system stored procedure only returns information about logical record relationships that are also join filters.</span></span>  
  
2.  <span data-ttu-id="2e13b-183">在发布服务器上，对发布数据库执行 [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-183">At the Publisher on the publication database, execute [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql).</span></span> <span data-ttu-id="2e13b-184">指定 **@publication** 、的关系中的一个项目的名称 **@article** ，以及步骤1中的关系的名称 **@filtername** 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-184">Specify **@publication**, the name of one of the articles in the relationship for **@article**, and the name of the relationship from step 1 for **@filtername**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2e13b-185">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2e13b-185">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="2e13b-186">此示例对现有发布启用预计算分区，并创建包含 `SalesOrderHeader` 和 `SalesOrderDetail` 表的两个新项目的逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2e13b-186">This example enables precomputed partitions on an existing publication, and creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="2e13b-187">使用复制管理对象 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2e13b-187">Using Replication Management Objects (RMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e13b-188">利用合并复制，您可以指定在逻辑记录级跟踪和解决冲突，但使用 RMO 却无法设置这些选项。</span><span class="sxs-lookup"><span data-stu-id="2e13b-188">Merge replication allows you to specify that conflicts be tracked and resolved at the logical record level, but these options cannot be set using RMO.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="2e13b-189">在没有关联的联接筛选器的情况下定义逻辑记录关系</span><span class="sxs-lookup"><span data-stu-id="2e13b-189">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="2e13b-190">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 类创建与发布服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="2e13b-190">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="2e13b-191">创建 <xref:Microsoft.SqlServer.Replication.MergePublication> 类的实例，为发布设置 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 属性并将 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 属性设置为在步骤 1 中创建的连接。</span><span class="sxs-lookup"><span data-stu-id="2e13b-191">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="2e13b-192">调用 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法获取该对象的属性。</span><span class="sxs-lookup"><span data-stu-id="2e13b-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="2e13b-193">如果此方法返回 `false`，则说明步骤 2 中的发布属性定义不正确，或者此发布不存在。</span><span class="sxs-lookup"><span data-stu-id="2e13b-193">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="2e13b-194">如果 <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> 属性设置为 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>，请将其设为 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>。</span><span class="sxs-lookup"><span data-stu-id="2e13b-194">If the <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> property is set to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, set it to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.</span></span>  
  
5.  <span data-ttu-id="2e13b-195">如果要构成逻辑记录的项目不存在，请创建 <xref:Microsoft.SqlServer.Replication.MergeArticle> 类的一个实例，然后设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="2e13b-195">If the articles that are to comprise the logical record do not exist, create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="2e13b-196">将 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>设置为项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-196">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="2e13b-197">将 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>设置为发布的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-197">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="2e13b-198">（可选）如果对项目进行水平筛选，则将 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> 属性指定为行筛选器子句。</span><span class="sxs-lookup"><span data-stu-id="2e13b-198">(Optional) If the article is horizontally filtered, specify the row filter clause for the <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> property.</span></span> <span data-ttu-id="2e13b-199">使用此属性可指定静态行筛选器或参数化行筛选器。</span><span class="sxs-lookup"><span data-stu-id="2e13b-199">Use this property to specify a static or parameterized row filter.</span></span> <span data-ttu-id="2e13b-200">有关详细信息，请参阅 [参数化行筛选器](../merge/parameterized-filters-parameterized-row-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-200">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="2e13b-201">有关详细信息，请参阅 [定义项目](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-201">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
6.  <span data-ttu-id="2e13b-202">调用 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2e13b-202">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span>  
  
7.  <span data-ttu-id="2e13b-203">对构成逻辑记录的每个项目，重复执行步骤 5 和 6。</span><span class="sxs-lookup"><span data-stu-id="2e13b-203">Repeat steps 5 and 6 for each article comprising the logical record.</span></span>  
  
8.  <span data-ttu-id="2e13b-204">创建 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 类的一个实例以定义项目之间的逻辑记录关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-204">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> class to define the logical record relationship between articles.</span></span> <span data-ttu-id="2e13b-205">然后，设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="2e13b-205">Then, set the following properties:</span></span>  
  
    -   <span data-ttu-id="2e13b-206">将 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> 属性设置为逻辑记录关系中子项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-206">The name of the child article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="2e13b-207">将 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> 属性设置为逻辑记录关系中现有父项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-207">The name of the existing, parent article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="2e13b-208">将 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> 属性设置为逻辑记录关系的名称。</span><span class="sxs-lookup"><span data-stu-id="2e13b-208">A name for the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> property.</span></span>  
  
    -   <span data-ttu-id="2e13b-209">将 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> 属性设置为定义关系的表达式。</span><span class="sxs-lookup"><span data-stu-id="2e13b-209">The expression that defines the relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> property.</span></span>  
  
    -   <span data-ttu-id="2e13b-210">将 <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> 属性的值设置为 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-210">A value of <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> property.</span></span> <span data-ttu-id="2e13b-211">如果此逻辑记录关系同时也是一个联接筛选器，请将此属性的值指定为 <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> 。</span><span class="sxs-lookup"><span data-stu-id="2e13b-211">If the logical record relationship is also a join filter, specify a value of <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> for this property.</span></span> <span data-ttu-id="2e13b-212">有关详细信息，请参阅[通过逻辑记录对相关行的更改进行分组](../merge/group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="2e13b-212">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
9. <span data-ttu-id="2e13b-213">对表示此关系中的子项目的对象调用 <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2e13b-213">Call the <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> method on the object that represents the child article in the relationship.</span></span> <span data-ttu-id="2e13b-214">传递步骤 8 中的 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 对象以定义此关系。</span><span class="sxs-lookup"><span data-stu-id="2e13b-214">Pass the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> object from step 8 to define the relationship.</span></span>  
  
10. <span data-ttu-id="2e13b-215">对发布中的其余每个逻辑记录关系重复执行步骤 8 和 9。</span><span class="sxs-lookup"><span data-stu-id="2e13b-215">Repeat steps 8 and 9 for each remaining logical record relationship in the publication.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="2e13b-216">示例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="2e13b-216">Example (RMO)</span></span>  
 <span data-ttu-id="2e13b-217">此示例为 `SalesOrderHeader` 和 `SalesOrderDetail` 表创建一个由两个新项目构成的逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2e13b-217">This example creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a><span data-ttu-id="2e13b-218">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2e13b-218">See Also</span></span>  
 <span data-ttu-id="2e13b-219">[定义和修改合并项目间的联接筛选器](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="2e13b-219">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="2e13b-220">[定义和修改合并项目的参数化行筛选器](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="2e13b-220">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="2e13b-221">[定义和修改静态行筛选器](define-and-modify-a-static-row-filter.md) </span><span class="sxs-lookup"><span data-stu-id="2e13b-221">[Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) </span></span>  
 <span data-ttu-id="2e13b-222">[通过逻辑记录对相关行的更改进行分组](../merge/group-changes-to-related-rows-with-logical-records.md) </span><span class="sxs-lookup"><span data-stu-id="2e13b-222">[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md) </span></span>  
 <span data-ttu-id="2e13b-223">[使用预计算分区优化参数化筛选器的性能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="2e13b-223">[Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span></span>  
 [<span data-ttu-id="2e13b-224">通过逻辑记录对相关行的更改进行分组</span><span class="sxs-lookup"><span data-stu-id="2e13b-224">Group Changes to Related Rows with Logical Records</span></span>](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
