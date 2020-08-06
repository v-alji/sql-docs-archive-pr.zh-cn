---
title: 通过逻辑记录对相关行的更改进行分组 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ad76799c-4486-4b98-9705-005433041321
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 433e0edbe83d102e6002bd133f967f27a236f66e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576695"
---
# <a name="group-changes-to-related-rows-with-logical-records"></a><span data-ttu-id="b73b3-102">通过逻辑记录对相关行的更改进行分组</span><span class="sxs-lookup"><span data-stu-id="b73b3-102">Group Changes to Related Rows with Logical Records</span></span>
  
> [!NOTE]
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]

 <span data-ttu-id="b73b3-103">默认情况下，合并复制逐行处理数据更改。</span><span class="sxs-lookup"><span data-stu-id="b73b3-103">By default, merge replication processes data changes on a row-by-row basis.</span></span> <span data-ttu-id="b73b3-104">这适用于许多情况，但对于某些应用程序，需要将相关行作为一个单元进行处理。</span><span class="sxs-lookup"><span data-stu-id="b73b3-104">In many circumstances this is appropriate, but for some applications, it is essential that related rows be processed as a unit.</span></span> <span data-ttu-id="b73b3-105">合并复制的逻辑记录功能允许在不同表的相关行之间定义一种关系，以便将这些行作为一个单元进行处理。</span><span class="sxs-lookup"><span data-stu-id="b73b3-105">The logical records feature of merge replication allows you to define a relationship between related rows in different tables so that the rows are processed as a unit.</span></span>

> [!NOTE]
>  <span data-ttu-id="b73b3-106">逻辑记录功能可以单独使用，也可以与联接筛选器一起使用。</span><span class="sxs-lookup"><span data-stu-id="b73b3-106">The logical records feature can be used alone or in conjunction with join filters.</span></span> <span data-ttu-id="b73b3-107">有关联接筛选器的详细信息，请参阅 [Join Filters](join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-107">For more information about join filters, see [Join Filters](join-filters.md).</span></span> <span data-ttu-id="b73b3-108">若要使用逻辑记录，发布的兼容级别不能低于 90RTM。</span><span class="sxs-lookup"><span data-stu-id="b73b3-108">To use logical records, the compatibility level of the publication must be at least 90RTM.</span></span>

 <span data-ttu-id="b73b3-109">请考虑以下三个相关的表：</span><span class="sxs-lookup"><span data-stu-id="b73b3-109">Consider these three related tables:</span></span>

 <span data-ttu-id="b73b3-110">![三个仅具有列名称的表逻辑记录](../media/logical-records-01.gif "三个仅具有列名称的表逻辑记录")</span><span class="sxs-lookup"><span data-stu-id="b73b3-110">![Three table logical record, with column names only](../media/logical-records-01.gif "Three table logical record, with column names only")</span></span>

 <span data-ttu-id="b73b3-111">在此关系中， **Customers** 表是父表，具有主键列 **CustID**。</span><span class="sxs-lookup"><span data-stu-id="b73b3-111">The **Customers** table is the parent table in this relationship and has a primary key column **CustID**.</span></span> <span data-ttu-id="b73b3-112">**Orders** 表具有主键列 **OrderID**和外键约束（ **CustID** 列）。该外键列引用 **Customers** 表中的 **CustID** 列。</span><span class="sxs-lookup"><span data-stu-id="b73b3-112">The **Orders** table has a primary key column **OrderID**, with a foreign key constraint on the **CustID** column that references the **CustID** column in the **Customers** table.</span></span> <span data-ttu-id="b73b3-113">同样， **OrderItems** 表具有主键列 **OrderItemID**和外键约束（ **OrderID** 列）。该外键列引用 **Orders** 表中的 **OrderID** 列。</span><span class="sxs-lookup"><span data-stu-id="b73b3-113">Similarly, the **OrderItems** table has a primary key column **OrderItemID**, with a foreign key constraint on the **OrderID** column that references the **OrderID** column in the **Orders** table.</span></span>

 <span data-ttu-id="b73b3-114">在此示例中，逻辑记录由 **Orders** 表中与单一 **CustID** 值相关的所有行和 **OrderItems** 表中与 **Orders** 表中的那些行相关的所有行组成。</span><span class="sxs-lookup"><span data-stu-id="b73b3-114">In this example, a logical record consists of all the rows in the **Orders** table that are related to a single **CustID** value and all of the rows in the **OrderItems** table that are related to those rows in the **Orders** table.</span></span> <span data-ttu-id="b73b3-115">此关系图显示了 Customer2 的逻辑记录中三个表的所有行：</span><span class="sxs-lookup"><span data-stu-id="b73b3-115">This diagram shows all the rows in the three tables that are in the logical record for Customer2:</span></span>

 <span data-ttu-id="b73b3-116">![三个具有值的表逻辑记录](../media/logical-records-02.gif "三个具有值的表逻辑记录")</span><span class="sxs-lookup"><span data-stu-id="b73b3-116">![Three table logical record with values](../media/logical-records-02.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="b73b3-117">若要定义项目之间的逻辑记录关系，请参阅 [定义合并表项目间的逻辑记录关系](../publish/define-a-logical-record-relationship-between-merge-table-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-117">To define a logical record relationship between articles, see [Define a Logical Record Relationship Between Merge Table Articles](../publish/define-a-logical-record-relationship-between-merge-table-articles.md).</span></span>

## <a name="benefits-of-logical-records"></a><span data-ttu-id="b73b3-118">逻辑记录的优点</span><span class="sxs-lookup"><span data-stu-id="b73b3-118">Benefits of Logical Records</span></span>
 <span data-ttu-id="b73b3-119">逻辑记录功能有两大优点：</span><span class="sxs-lookup"><span data-stu-id="b73b3-119">The logical records feature has two primary benefits:</span></span>

-   <span data-ttu-id="b73b3-120">将数据更改作为一个单元来应用。</span><span class="sxs-lookup"><span data-stu-id="b73b3-120">Application of data changes as a unit.</span></span>

-   <span data-ttu-id="b73b3-121">同时对多个表中的多个行检测和解决冲突。</span><span class="sxs-lookup"><span data-stu-id="b73b3-121">The detection and resolution of conflicts simultaneously on multiple rows from multiple tables.</span></span>

### <a name="the-application-of-changes-as-a-unit"></a><span data-ttu-id="b73b3-122">将更改作为一个单元来应用</span><span class="sxs-lookup"><span data-stu-id="b73b3-122">The Application of Changes As a Unit</span></span>
 <span data-ttu-id="b73b3-123">在合并处理中断的情况下（如删除连接），如果使用了逻辑记录，则已完成的部分相关复制更改就会回滚。</span><span class="sxs-lookup"><span data-stu-id="b73b3-123">If merge processing is interrupted, such as in the case of a dropped connection, the partially completed set of related replicated changes is rolled back if logical records are used.</span></span> <span data-ttu-id="b73b3-124">例如，订阅服务器添加一份 **OrderID** = 6 的新订单，并对应 **OrderID** = 6 在 **OrderItems** 表中添加两个分别为 **OrderItemID** = 10 和 **OrderItemID** = 11 的新行。</span><span class="sxs-lookup"><span data-stu-id="b73b3-124">For example, consider the case where a Subscriber adds a new order with **OrderID** = 6 and two new rows in the **OrderItems** table with **OrderItemID** = 10 and **OrderItemID** = 11 for **OrderID** = 6.</span></span>

 <span data-ttu-id="b73b3-125">![三个具有值的表逻辑记录](../media/logical-records-04.gif "三个具有值的表逻辑记录")</span><span class="sxs-lookup"><span data-stu-id="b73b3-125">![Three table logical record with values](../media/logical-records-04.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="b73b3-126">如果复制进程在 **OrderID** = 6 的 **Orders** 行完成之后、在 **OrderItems** 10 和 11 完成之前中断，并且未使用逻辑记录，则 **OrderID** = 6 的 **OrderTotal** 值就不会与 **OrderItems** 行的 **OrderAmount** 值的和一致。</span><span class="sxs-lookup"><span data-stu-id="b73b3-126">If the replication process is interrupted after the **Orders** row for **OrderID** = 6 is complete, but before the **OrderItems** 10 and 11 are completed, and logical records are not used, the **OrderTotal** value for **OrderID** = 6 will not be consistent with the sum of the **OrderAmount** values for the **OrderItems** rows.</span></span> <span data-ttu-id="b73b3-127">如果使用了逻辑记录，则在复制相关的 **OrderItems** 更改之后，才会提交 **OrderID** = 6 的 **Orders** 行。</span><span class="sxs-lookup"><span data-stu-id="b73b3-127">If logical records are used, the **Orders** row for **OrderID** = 6 is not committed until the related **OrderItems** changes are replicated.</span></span>

 <span data-ttu-id="b73b3-128">在不同的方案中，如果使用了逻辑记录，并且有人在合并进程应用更改时查询表，那么用户在复制更改完成前，看不到已复制的部分更改。</span><span class="sxs-lookup"><span data-stu-id="b73b3-128">In a different scenario, if logical records are used, and someone is querying tables when the merge process is applying changes, the user will not see the partially replicated changes until they are all complete.</span></span> <span data-ttu-id="b73b3-129">例如，复制进程上载了 **OrderID** = 6 的 Orders 行，而用户在复制进程复制 **OrderItems** 行之前查询表，那么 **OrderTotal** 值就不会与 **OrderAmount** 值的和相同。</span><span class="sxs-lookup"><span data-stu-id="b73b3-129">For example, the replication process has uploaded the Orders row for **OrderID** = 6, but a user queries the tables before the replication process has replicated the **OrderItems** rows, the **OrderTotal** value would not be the same as the sum of the **OrderAmount** values.</span></span> <span data-ttu-id="b73b3-130">如果使用了逻辑记录，则在 **OrderItems** 完成并且事务作为一个单元提交后，才会显示 **Orders** 行。</span><span class="sxs-lookup"><span data-stu-id="b73b3-130">If logical records are used, the **Orders** row would not be visible until the **OrderItems** rows are complete and the transaction has been committed as a unit.</span></span>

### <a name="the-application-of-conflict-handling-to-more-than-one-table"></a><span data-ttu-id="b73b3-131">对多个表应用冲突处理</span><span class="sxs-lookup"><span data-stu-id="b73b3-131">The Application of Conflict Handling to More Than One Table</span></span>
 <span data-ttu-id="b73b3-132">请考虑两台订阅服务器具有上述数据集的情况：</span><span class="sxs-lookup"><span data-stu-id="b73b3-132">Consider the case where two Subscribers have the data set above:</span></span>

-   <span data-ttu-id="b73b3-133">在第一台订阅服务器上，用户将 **OrderItemID** 5 的 **OrderAmount** 从 100 改为 150，并将 **OrderID** 3 的 **OrderTotal** 从 200 改为 250。</span><span class="sxs-lookup"><span data-stu-id="b73b3-133">A user at the first Subscriber changes the **OrderAmount** of **OrderItemID** 5 from 100 to 150 and the **OrderTotal** of **OrderID** 3 from 200 to 250.</span></span>

-   <span data-ttu-id="b73b3-134">在第二台订阅服务器上，用户将 **OrderItemID** 6 的 **OrderAmount** 从 25 改为 125，并将 **OrderID** 3 的 **OrderTotal** 从 200 改为 300。</span><span class="sxs-lookup"><span data-stu-id="b73b3-134">A user at the second Subscriber changes the **OrderAmount** of **OrderItemID** 6 from 25 to 125 and the **OrderTotal** of **OrderID** 3 from 200 to 300.</span></span>

 <span data-ttu-id="b73b3-135">如果不使用逻辑记录复制这些更改， **OrderTotal** 的不同值就会导致冲突，结果只能复制其中一个。</span><span class="sxs-lookup"><span data-stu-id="b73b3-135">If these changes are replicated without using logical records, the different **OrderTotal** values would result in a conflict and only one of them would be replicated.</span></span> <span data-ttu-id="b73b3-136">但 **OrderItems** 表中不冲突的更改将被复制，并且不会发生冲突，致使最终的 **OrderTotal** 值与 **OrderItems** 行的状态不一致。</span><span class="sxs-lookup"><span data-stu-id="b73b3-136">But the non-conflicting changes in the **OrderItems** table would be replicated without conflict, leaving the final **OrderTotal** values in an inconsistent state with respect to the **OrderItems** rows.</span></span> <span data-ttu-id="b73b3-137">如果在此方案中使用逻辑记录，则与落选的 **Orders** 表更改关联的 **OrderItems** 更改也会回滚，从而使最终的 **OrderTotal** 值成为 **OrderItems** 行的准确汇总。</span><span class="sxs-lookup"><span data-stu-id="b73b3-137">If logical records are used in this scenario, the **OrderItems** change associated with the losing **Orders** table change would also be rolled back, and the final **OrderTotal** value would be an accurate summary of the **OrderItems** rows.</span></span>

 <span data-ttu-id="b73b3-138">有关与逻辑记录的冲突检测和解决相关的选项的详细信息，请参阅[检测并解决逻辑记录中的冲突](advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-138">For more information about options related to conflict detection and resolution with logical records, see [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>

## <a name="considerations-for-using-logical-records"></a><span data-ttu-id="b73b3-139">使用逻辑记录的注意事项</span><span class="sxs-lookup"><span data-stu-id="b73b3-139">Considerations for Using Logical Records</span></span>
 <span data-ttu-id="b73b3-140">使用逻辑记录时，请注意下列事项。</span><span class="sxs-lookup"><span data-stu-id="b73b3-140">Keep the following considerations in mind when using logical records.</span></span>

### <a name="general-considerations"></a><span data-ttu-id="b73b3-141">一般注意事项</span><span class="sxs-lookup"><span data-stu-id="b73b3-141">General Considerations</span></span>

-   <span data-ttu-id="b73b3-142">建议在逻辑记录中保留尽可能少的表，建议最多为五个表。</span><span class="sxs-lookup"><span data-stu-id="b73b3-142">It is recommended that you keep the number of tables in a logical record as low as possible; five tables or less is recommended.</span></span>

-   <span data-ttu-id="b73b3-143">逻辑记录无法引用具有下列任一数据类型的列：</span><span class="sxs-lookup"><span data-stu-id="b73b3-143">Logical records cannot reference columns with any of the following data types:</span></span>

    -   <span data-ttu-id="b73b3-144">`varchar(max)` 和 `nvarchar(max)`</span><span class="sxs-lookup"><span data-stu-id="b73b3-144">`varchar(max)` and `nvarchar(max)`</span></span>

    -   `varbinary(max)`

    -   <span data-ttu-id="b73b3-145">`text` 和 `ntext`</span><span class="sxs-lookup"><span data-stu-id="b73b3-145">`text` and `ntext`</span></span>

    -   `image`

    -   `XML`

    -   `UDT`

-   <span data-ttu-id="b73b3-146">不能使用 CASCADE 选项定义已发布表中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="b73b3-146">Foreign key relationships in published tables cannot be defined with the CASCADE option.</span></span> <span data-ttu-id="b73b3-147">有关详细信息，请参阅 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 和 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-147">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>

-   <span data-ttu-id="b73b3-148">不能更新逻辑关系子句中使用的任何列。</span><span class="sxs-lookup"><span data-stu-id="b73b3-148">You cannot update any columns that are used in the logical relation clause.</span></span>

-   <span data-ttu-id="b73b3-149">逻辑记录中包含的项目不支持使用业务逻辑处理程序或自定义冲突解决程序的自定义冲突解决方法。</span><span class="sxs-lookup"><span data-stu-id="b73b3-149">Custom conflict resolution with business logic handlers or custom resolvers is not supported for articles that are included in a logical record.</span></span>

-   <span data-ttu-id="b73b3-150">如果在包含参数化筛选器的发布中使用逻辑记录，必须用每台订阅服务器分区的快照初始化相应的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="b73b3-150">If logical records are used in a publication that includes parameterized filters, you must initialize each Subscriber with a snapshot for its partition.</span></span> <span data-ttu-id="b73b3-151">如果用其他方法初始化订阅服务器，那么合并代理将会失败。</span><span class="sxs-lookup"><span data-stu-id="b73b3-151">If you initialize a Subscriber with another method, the Merge Agent will fail.</span></span> <span data-ttu-id="b73b3-152">有关详细信息，请参阅 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-152">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>

-   <span data-ttu-id="b73b3-153">包含逻辑记录的冲突不会显示在冲突查看器中。</span><span class="sxs-lookup"><span data-stu-id="b73b3-153">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="b73b3-154">若要查看有关这些冲突的信息，请使用复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="b73b3-154">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="b73b3-155">有关详细信息，请参阅[查看合并发布的冲突信息（复制 Transact-SQL 编程）](../view-conflict-information-for-merge-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-155">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>

### <a name="publication-settings"></a><span data-ttu-id="b73b3-156">发布设置</span><span class="sxs-lookup"><span data-stu-id="b73b3-156">Publication Settings</span></span>

-   <span data-ttu-id="b73b3-157">发布的兼容级别必须为 90RTM 或更大。</span><span class="sxs-lookup"><span data-stu-id="b73b3-157">The publication must have a compatibility level of 90RTM or greater.</span></span> <span data-ttu-id="b73b3-158">有关详细信息，请参阅[复制向后兼容性](../replication-backward-compatibility.md)中的“发布兼容级别”部分。</span><span class="sxs-lookup"><span data-stu-id="b73b3-158">For more information, see the "Publication Compatibility Level" section of [Replication Backward Compatibility](../replication-backward-compatibility.md).</span></span>

-   <span data-ttu-id="b73b3-159">发布必须使用本机快照模式。</span><span class="sxs-lookup"><span data-stu-id="b73b3-159">The publication must use native snapshot mode.</span></span> <span data-ttu-id="b73b3-160">这是默认设置，除非您要复制到不支持逻辑记录的 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b73b3-160">This is the default unless you are replicating to [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which does not support logical records.</span></span>

-   <span data-ttu-id="b73b3-161">发布不允许 Web 同步。</span><span class="sxs-lookup"><span data-stu-id="b73b3-161">The publication cannot allow Web synchronization.</span></span> <span data-ttu-id="b73b3-162">有关 Web 同步的详细信息，请参阅 [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-162">For more information about Web synchronization, see [Web Synchronization for Merge Replication](../web-synchronization-for-merge-replication.md).</span></span>

-   <span data-ttu-id="b73b3-163">若要在已筛选的发布上使用逻辑记录：</span><span class="sxs-lookup"><span data-stu-id="b73b3-163">In order to use logical records on a filtered publication:</span></span>

    -   <span data-ttu-id="b73b3-164">还必须使用预计算分区。</span><span class="sxs-lookup"><span data-stu-id="b73b3-164">Precomputed partitions must also be used.</span></span> <span data-ttu-id="b73b3-165">预计算分区的要求也适用于逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="b73b3-165">The requirements of precomputed partitions also apply to logical records.</span></span> <span data-ttu-id="b73b3-166">有关详细信息，请参阅[使用预计算分区优化参数化筛选器性能](parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-166">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>

    -   <span data-ttu-id="b73b3-167">不能使用不重叠的参数化筛选器。</span><span class="sxs-lookup"><span data-stu-id="b73b3-167">You cannot use nonoverlapping parameterized filters.</span></span> <span data-ttu-id="b73b3-168">有关详细信息，请参阅 [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md)的“设置‘分区选项’”部分。</span><span class="sxs-lookup"><span data-stu-id="b73b3-168">For more information, see the "Setting 'partition options'" section of [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>

-   <span data-ttu-id="b73b3-169">如果发布使用联接筛选器，则必须将逻辑记录关系中所涉及的所有联接筛选器的 **join unique key** 属性设置为 **true** 。</span><span class="sxs-lookup"><span data-stu-id="b73b3-169">If the publication uses join filters, the **join unique key** property must be set to **true** for all join filters that are involved in logical record relationships.</span></span> <span data-ttu-id="b73b3-170">有关详细信息，请参阅 [Join Filters](join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="b73b3-170">For more information, see [Join Filters](join-filters.md).</span></span>

### <a name="relationships-between-tables"></a><span data-ttu-id="b73b3-171">表之间的关系</span><span class="sxs-lookup"><span data-stu-id="b73b3-171">Relationships Between Tables</span></span>

-   <span data-ttu-id="b73b3-172">通过逻辑记录相关的表必须具有主键 - 外键关系。</span><span class="sxs-lookup"><span data-stu-id="b73b3-172">Tables related through logical records must have a primary key-foreign key relationship.</span></span>

-   <span data-ttu-id="b73b3-173">不能为外键约束设置 NOT FOR REPLICATION 选项。</span><span class="sxs-lookup"><span data-stu-id="b73b3-173">The NOT FOR REPLICATION option cannot be set for foreign key constraints.</span></span>

-   <span data-ttu-id="b73b3-174">子表只能有一个父表。</span><span class="sxs-lookup"><span data-stu-id="b73b3-174">Child tables can have only one parent table.</span></span>

     <span data-ttu-id="b73b3-175">例如，跟踪班级和学生的数据库的设计可能类似于下面的关系：</span><span class="sxs-lookup"><span data-stu-id="b73b3-175">For example, a database tracking classes and students might have a design similar to:</span></span>

     <span data-ttu-id="b73b3-176">![具有多个父表的子表](../media/logical-records-03.gif "具有多个父表的子表")</span><span class="sxs-lookup"><span data-stu-id="b73b3-176">![Child table with more than one parent table](../media/logical-records-03.gif "Child table with more than one parent table")</span></span>

     <span data-ttu-id="b73b3-177">在此关系中，不能使用一个逻辑记录表示三个表，因为 **ClassMembers** 中的行与单一主键行没有关联。</span><span class="sxs-lookup"><span data-stu-id="b73b3-177">You cannot use a logical record to represent the three tables in this relationship, because the rows in **ClassMembers** are not associated with a single primary key row.</span></span> <span data-ttu-id="b73b3-178">**Classes** 表和 **ClassMembers** 表仍可形成一个逻辑记录， **ClassMembers** 表和 **Students**表也可以，但三个表却不能。</span><span class="sxs-lookup"><span data-stu-id="b73b3-178">The tables **Classes** and **ClassMembers** could still form a logical record, as could the tables **ClassMembers** and **Students**, but not all three.</span></span>

-   <span data-ttu-id="b73b3-179">发布不能包含循环联接筛选器关系。</span><span class="sxs-lookup"><span data-stu-id="b73b3-179">The publication cannot contain circular join filter relationships.</span></span>

     <span data-ttu-id="b73b3-180">以 **Customers**、 **Orders**和 **OrderItems**这三个表为例，如果 **Orders** 表也有一个引用 **OrderItems** 表的外键约束，就不能使用逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="b73b3-180">Using the example with the tables **Customers**, **Orders**, and **OrderItems**, you could not use logical records if the **Orders** table also had a foreign key constraint that referenced the **OrderItems** table.</span></span>

## <a name="performance-implications-of-logical-records"></a><span data-ttu-id="b73b3-181">逻辑记录对性能的影响</span><span class="sxs-lookup"><span data-stu-id="b73b3-181">Performance implications of logical records</span></span>
 <span data-ttu-id="b73b3-182">逻辑记录功能确实会对性能造成负面影响。</span><span class="sxs-lookup"><span data-stu-id="b73b3-182">The logical record feature does come with a performance cost.</span></span> <span data-ttu-id="b73b3-183">如果不使用逻辑记录，复制代理可以同时处理给定项目的所有更改，并且因为更改是以逐行方式应用的，所以应用这些更改所需的锁定和事务日志要求很小。</span><span class="sxs-lookup"><span data-stu-id="b73b3-183">If logical records are not used, the replication agent can process all of the changes for a given article at the same time, and because the changes are applied in a row-by-row fashion, the locking and transaction log requirements necessary for applying the changes are minimal.</span></span>

 <span data-ttu-id="b73b3-184">如果使用逻辑记录，则合并代理必须一起处理每个整体逻辑记录的更改。</span><span class="sxs-lookup"><span data-stu-id="b73b3-184">If logical records are used, the Merge Agent must process the changes for each entire logical record together.</span></span> <span data-ttu-id="b73b3-185">这会影响合并代理复制行所需的时间。</span><span class="sxs-lookup"><span data-stu-id="b73b3-185">This has an effect on the amount of time it takes the Merge Agent to replicate the rows.</span></span> <span data-ttu-id="b73b3-186">此外，由于代理要为每个逻辑记录打开一个单独的事务，因此锁定要求就会增加。</span><span class="sxs-lookup"><span data-stu-id="b73b3-186">Additionally, because the agent opens a separate transaction for each logical record, locking requirements can increase.</span></span>

## <a name="see-also"></a><span data-ttu-id="b73b3-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b73b3-187">See Also</span></span>
 [<span data-ttu-id="b73b3-188">合并复制的项目选项</span><span class="sxs-lookup"><span data-stu-id="b73b3-188">Article Options for Merge Replication</span></span>](article-options-for-merge-replication.md)


