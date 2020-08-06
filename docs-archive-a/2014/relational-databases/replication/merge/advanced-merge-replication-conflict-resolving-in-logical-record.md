---
title: 检测并解决逻辑记录中的冲突 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logical records [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: f2e55040-ca69-4ccf-97d1-c362e1633f26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f9822cd153af67538a36a894de0ec1b4716e54cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576708"
---
# <a name="detecting-and-resolving-conflicts-in-logical-records"></a><span data-ttu-id="2518f-102">Detecting and Resolving Conflicts in Logical Records</span><span class="sxs-lookup"><span data-stu-id="2518f-102">Detecting and Resolving Conflicts in Logical Records</span></span>
  <span data-ttu-id="2518f-103">本主题介绍使用逻辑记录时冲突检测和冲突解决方法的各种可能组合。</span><span class="sxs-lookup"><span data-stu-id="2518f-103">This topic covers the various combinations of conflict detection and conflict resolution approaches possible when using logical records.</span></span> <span data-ttu-id="2518f-104">多个节点更改同一数据，或者合并复制遇到某些类型的错误（如复制更改时违反了约束）时，合并复制中会出现冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-104">A conflict in merge replication occurs when more than one node changes the same data, or merge replication encounters certain types of errors, such as a constraint violation, when replicating changes.</span></span> <span data-ttu-id="2518f-105">有关冲突检测和解决的详细信息，请参阅 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="2518f-105">For more information about conflict detection and resolution, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>

 <span data-ttu-id="2518f-106">若要指定项目的冲突跟踪和解决方法级别，请参阅 [为合并项目指定冲突跟踪和解决方法级别](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)。</span><span class="sxs-lookup"><span data-stu-id="2518f-106">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>

## <a name="conflict-detection"></a><span data-ttu-id="2518f-107">冲突检测</span><span class="sxs-lookup"><span data-stu-id="2518f-107">Conflict Detection</span></span>
 <span data-ttu-id="2518f-108">检测逻辑记录中的冲突的方法由两个项目属性决定： **column_tracking** 和 **logical_record_level_conflict_detection**。</span><span class="sxs-lookup"><span data-stu-id="2518f-108">The way in which conflicts are detected for logical records is determined by two article properties: **column_tracking** and **logical_record_level_conflict_detection**.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="2518f-109">及更高版本还支持逻辑记录级检测。</span><span class="sxs-lookup"><span data-stu-id="2518f-109">and later versions also support logical record-level detection.</span></span>

 <span data-ttu-id="2518f-110">**logical_record_level_conflict_detection** 项目属性可以设置为 TRUE 或 FALSE。</span><span class="sxs-lookup"><span data-stu-id="2518f-110">The **logical_record_level_conflict_detection** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="2518f-111">应只对顶级父项目设置此值，子项目将忽略此值。</span><span class="sxs-lookup"><span data-stu-id="2518f-111">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="2518f-112">如果此值为 FALSE，则合并复制如同在早期版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中一样，只根据项目的 **column_tracking** 属性值检测冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-112">If this value is FALSE, merge replication detects conflicts as in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], based solely on the value of the **column_tracking** property for the article.</span></span> <span data-ttu-id="2518f-113">如果此值为 TRUE，合并复制将忽略项目的 **column_tracking** 属性，并且当逻辑记录中的任何位置发生更改时，将检测冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-113">If this value is TRUE, merge replication will ignore the **column_tracking** property of the article, and detect a conflict if changes are made anywhere in the logical record.</span></span> <span data-ttu-id="2518f-114">例如，考虑以下方案：</span><span class="sxs-lookup"><span data-stu-id="2518f-114">For example, consider this scenario:</span></span>

 <span data-ttu-id="2518f-115">![三个具有值的表逻辑记录](../media/logical-records-05.gif "三个具有值的表逻辑记录")</span><span class="sxs-lookup"><span data-stu-id="2518f-115">![Three table logical record with values](../media/logical-records-05.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="2518f-116">如果两个用户更改 **Customers**、 **Orders**或 **OrderItems** 表中 Customer2 逻辑记录的任何值，将检测冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-116">A conflict is detected if two users change any values for the Customer2 logical record in the **Customers**, **Orders**, or **OrderItems** tables.</span></span> <span data-ttu-id="2518f-117">此示例通过使用 UPDATE 语句所做的更改检测冲突，但还可以通过使用 INSERT 或 DELETE 语句所做的更改来检测冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-117">This example involves changes made via an UPDATE statement, but the conflict can also be detected by changes made with INSERT or DELETE statements.</span></span>

## <a name="conflict-resolution"></a><span data-ttu-id="2518f-118">冲突解决</span><span class="sxs-lookup"><span data-stu-id="2518f-118">Conflict Resolution</span></span>
 <span data-ttu-id="2518f-119">默认情况下，合并复制使用基于优先级的逻辑来解决冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-119">By default, merge replication uses priority-based logic to resolve conflicts.</span></span> <span data-ttu-id="2518f-120">如果在两个订阅服务器数据库中做了冲突更改，则对具有较高订阅优先级的订阅服务器所做的更改入选，如果优先级相同，则第一个到达发布服务器的更改入选。</span><span class="sxs-lookup"><span data-stu-id="2518f-120">If a conflicting change is made in two Subscriber databases, the change for the Subscriber with the higher subscription priority wins, or if the priority is the same, the first change to reach the Publisher wins.</span></span> <span data-ttu-id="2518f-121">通过行级和列级检测，整个入选行将始终覆盖落选行。</span><span class="sxs-lookup"><span data-stu-id="2518f-121">With row-level and column-level detection, the entire winning row always overwrites the losing row.</span></span>

 <span data-ttu-id="2518f-122">**logical_record_level_conflict_resolution** 项目属性可以设置为 TRUE 或 FALSE。</span><span class="sxs-lookup"><span data-stu-id="2518f-122">The **logical_record_level_conflict_resolution** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="2518f-123">应只对顶级父项目设置此值，子项目将忽略此值。</span><span class="sxs-lookup"><span data-stu-id="2518f-123">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="2518f-124">如果此值为 TRUE，则整个入选逻辑记录将覆盖未入选的逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2518f-124">If the value is TRUE, the entire winning logical record overwrites the losing logical record.</span></span> <span data-ttu-id="2518f-125">如果此值为 FALSE，则各个入选行可以来自不同的订阅服务器或发布服务器。</span><span class="sxs-lookup"><span data-stu-id="2518f-125">If it is FALSE, individual winning rows can come from different Subscribers or Publishers.</span></span> <span data-ttu-id="2518f-126">例如，订阅服务器 A 可以在 **Orders** 表的某行中入选冲突，而订阅服务器 B 可以在 **OrderItems** 表的相关行中入选冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-126">For example, Subscriber A could win a conflict on a row from the **Orders** table, and Subscriber B could win on a related row from the **OrderItems** table.</span></span> <span data-ttu-id="2518f-127">结果是包含订阅服务器 A 中的 **Orders** 行和订阅服务器 B 中的 **OrderItems** 行的逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2518f-127">The result is a logical record with the **Orders** row from Subscriber A and the **OrderItems** row from Subscriber B.</span></span>

## <a name="interaction-of-conflict-resolution-and-detection-settings"></a><span data-ttu-id="2518f-128">冲突解决和检测设置的交互</span><span class="sxs-lookup"><span data-stu-id="2518f-128">Interaction of Conflict Resolution and Detection Settings</span></span>
 <span data-ttu-id="2518f-129">冲突结果取决于冲突检测和解决设置的交互。</span><span class="sxs-lookup"><span data-stu-id="2518f-129">The outcome of conflicts depends on the interaction of conflict detection and resolution settings.</span></span> <span data-ttu-id="2518f-130">在下面的示例中，假定使用的是基于优先级的冲突解决方法。</span><span class="sxs-lookup"><span data-stu-id="2518f-130">For the examples below, it is assumed that the priority-based conflict resolution is being used.</span></span> <span data-ttu-id="2518f-131">使用逻辑记录时，可以选择下列组合：</span><span class="sxs-lookup"><span data-stu-id="2518f-131">When using logical records, the possibilities are:</span></span>

-   <span data-ttu-id="2518f-132">行级或列级检测，行级解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-132">Row or column level detection, row level resolution</span></span>

-   <span data-ttu-id="2518f-133">列级检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-133">Column level detection, logical record resolution</span></span>

-   <span data-ttu-id="2518f-134">行级检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-134">Row level detection, logical record resolution</span></span>

-   <span data-ttu-id="2518f-135">逻辑记录检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-135">Logical record detection, logical record resolution</span></span>

### <a name="row-or-column-level-detection-row-level-resolution"></a><span data-ttu-id="2518f-136">行级或列级检测，行级解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-136">Row or Column Level Detection, Row Level Resolution</span></span>
 <span data-ttu-id="2518f-137">在此示例中，发布配置方式如下：</span><span class="sxs-lookup"><span data-stu-id="2518f-137">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="2518f-138">**column_tracking** 为 TRUE 或 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-138">**column_tracking** is TRUE or FALSE</span></span>

-   <span data-ttu-id="2518f-139">**logical_record_level_conflict_detection** 为 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-139">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="2518f-140">**logical_record_level_conflict_resolution** 为 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-140">**logical_record_level_conflict_resolution** is FALSE</span></span>

 <span data-ttu-id="2518f-141">这种情况下，检测的级别为行级或列级，而解决方法的级别为行级。</span><span class="sxs-lookup"><span data-stu-id="2518f-141">In this case, detection is at the row or column level and resolution is at the row level.</span></span> <span data-ttu-id="2518f-142">使用这些设置可以利用使所有逻辑记录的更改按单元复制的优点，但不包括逻辑记录级的冲突检测或解决方法。</span><span class="sxs-lookup"><span data-stu-id="2518f-142">These settings are used to take advantage of having all changes to a logical record replicate as a unit, but without conflict detection or resolution at the logical record level.</span></span>

### <a name="column-level-detection-logical-record-resolution"></a><span data-ttu-id="2518f-143">列级检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-143">Column Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="2518f-144">在此示例中，发布配置方式如下：</span><span class="sxs-lookup"><span data-stu-id="2518f-144">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="2518f-145">**column_tracking** 为 TRUE</span><span class="sxs-lookup"><span data-stu-id="2518f-145">**column_tracking** is TRUE</span></span>

-   <span data-ttu-id="2518f-146">**logical_record_level_conflict_detection** 为 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-146">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="2518f-147">**logical_record_level_conflict_resolution** 为 TRUE</span><span class="sxs-lookup"><span data-stu-id="2518f-147">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="2518f-148">发布服务器和订阅服务器以同一个数据集开始，并在 **orders** 表和 **customers** 表之间定义逻辑记录。</span><span class="sxs-lookup"><span data-stu-id="2518f-148">A Publisher and Subscriber start with the same data set, and a logical record is defined between the **orders** and **customers** tables.</span></span> <span data-ttu-id="2518f-149">发布服务器会更改 **customers** 表中的 **custcol1** 列和 **orders** 表中的 **ordercol1** 。</span><span class="sxs-lookup"><span data-stu-id="2518f-149">The Publisher changes the **custcol1** column in the **customers** table and the **ordercol1** in the **orders** table.</span></span> <span data-ttu-id="2518f-150">订阅服务器会更改 **customers** 表中同一行的 **custcol1** 和 **orders** 表中同一行的 **ordercol2** 列。</span><span class="sxs-lookup"><span data-stu-id="2518f-150">The Subscriber changes **custcol1** in the same row of the **customers** table and the **ordercol2** column in the same row of the **orders** table.</span></span> <span data-ttu-id="2518f-151">对 **customer** 表中的同一列进行更改会导致冲突，但对 **orders** 表进行更改不会导致冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-151">The changes to the same column in the **customer** table result in a conflict, but the changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="2518f-152">由于是在逻辑记录级解决冲突，因此在复制处理期间，发布服务器上所做的入选更改将替换订阅服务器表中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2518f-152">Because the conflicts are resolved at the logical record level, the winning changes made at the Publisher replace the changes made in the Subscriber tables during replication processing.</span></span>

 <span data-ttu-id="2518f-153">![显示对相关行所做更改的一系列表](../media/logical-records-06.gif "显示对相关行所做更改的一系列表")</span><span class="sxs-lookup"><span data-stu-id="2518f-153">![Series of tables showing changes to related rows](../media/logical-records-06.gif "Series of tables showing changes to related rows")</span></span>

### <a name="row-level-detection-logical-record-resolution"></a><span data-ttu-id="2518f-154">行级检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-154">Row Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="2518f-155">在此示例中，发布配置方式如下：</span><span class="sxs-lookup"><span data-stu-id="2518f-155">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="2518f-156">**column_tracking** 为 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-156">**column_tracking** is FALSE</span></span>

-   <span data-ttu-id="2518f-157">**logical_record_level_conflict_detection** 为 FALSE</span><span class="sxs-lookup"><span data-stu-id="2518f-157">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="2518f-158">**logical_record_level_conflict_resolution** 为 TRUE</span><span class="sxs-lookup"><span data-stu-id="2518f-158">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="2518f-159">发布服务器和订阅服务器以相同的数据集开始。</span><span class="sxs-lookup"><span data-stu-id="2518f-159">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="2518f-160">发布服务器会更改 **customers** 表中的 **custcol1** 列。</span><span class="sxs-lookup"><span data-stu-id="2518f-160">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="2518f-161">订阅服务器会更改 **customers** 表中的 **custcol2** 和 **orders** 表中的 **ordercol2** 列。</span><span class="sxs-lookup"><span data-stu-id="2518f-161">The Subscriber changes **custcol2** in the **customers** table and the **ordercol2** column in the **orders** table.</span></span> <span data-ttu-id="2518f-162">对 **customers** 表中的同一行进行更改会导致冲突，但订阅服务器对 **orders** 表进行更改不会导致冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-162">The changes to the same row in the **customers** table result in a conflict, but the Subscriber changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="2518f-163">由于是在逻辑记录级解决冲突，因此在同步过程中，发布服务器上所做的入选更改将替换订阅服务器表中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2518f-163">Because the conflicts are resolved at the logical record level, during synchronization the winning changes made at the Publisher replace the changes made in the Subscriber tables.</span></span>

 <span data-ttu-id="2518f-164">![显示对相关行所做更改的一系列表](../media/logical-records-07.gif "显示对相关行所做更改的一系列表")</span><span class="sxs-lookup"><span data-stu-id="2518f-164">![Series of tables showing changes to related rows](../media/logical-records-07.gif "Series of tables showing changes to related rows")</span></span>

### <a name="logical-record-detection-logical-record-resolution"></a><span data-ttu-id="2518f-165">逻辑记录检测，逻辑记录解决方法</span><span class="sxs-lookup"><span data-stu-id="2518f-165">Logical Record Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="2518f-166">在此示例中，发布配置方式如下：</span><span class="sxs-lookup"><span data-stu-id="2518f-166">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="2518f-167">**logical_record_level_conflict_detection** 为 TRUE</span><span class="sxs-lookup"><span data-stu-id="2518f-167">**logical_record_level_conflict_detection** is TRUE</span></span>

-   <span data-ttu-id="2518f-168">**logical_record_level_conflict_resolution** 为 TRUE</span><span class="sxs-lookup"><span data-stu-id="2518f-168">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="2518f-169">发布服务器和订阅服务器以相同的数据集开始。</span><span class="sxs-lookup"><span data-stu-id="2518f-169">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="2518f-170">发布服务器会更改 **customers** 表中的 **custcol1** 列。</span><span class="sxs-lookup"><span data-stu-id="2518f-170">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="2518f-171">订阅服务器会更改 **orders** 表中的 **ordercol1** 列。</span><span class="sxs-lookup"><span data-stu-id="2518f-171">The Subscriber changes the **ordercol1** column in the **orders** table.</span></span> <span data-ttu-id="2518f-172">对同一行或列未进行更改，但由于在 **custid**=1 的同一逻辑记录中做了更改，因此这些更改将在逻辑记录级被检测为冲突。</span><span class="sxs-lookup"><span data-stu-id="2518f-172">There are no changes to the same row or columns, but because the changes are made in the same logical record for **custid**=1, the changes are detected as a conflict at the logical record level.</span></span>

 <span data-ttu-id="2518f-173">由于还是在逻辑记录级解决冲突，因此在同步过程中，发布服务器上所做的入选更改将替换订阅服务器表中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2518f-173">Because the conflicts are also resolved at the logical record level, during synchronization the winning change made at the Publisher replaces the change made in the Subscriber tables.</span></span>

 <span data-ttu-id="2518f-174">![显示对相关行所做更改的一系列表](../media/logical-records-08.gif "显示对相关行所做更改的一系列表")</span><span class="sxs-lookup"><span data-stu-id="2518f-174">![Series of tables showing changes to related rows](../media/logical-records-08.gif "Series of tables showing changes to related rows")</span></span>

## <a name="see-also"></a><span data-ttu-id="2518f-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2518f-175">See Also</span></span>
 [<span data-ttu-id="2518f-176">通过逻辑记录对相关行的更改进行分组</span><span class="sxs-lookup"><span data-stu-id="2518f-176">Group Changes to Related Rows with Logical Records</span></span>](group-changes-to-related-rows-with-logical-records.md)


