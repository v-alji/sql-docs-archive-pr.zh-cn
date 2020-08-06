---
title: “管理分区向导”的 F1 帮助 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managepartition.getstart.f1
- sql12.swb.managepartition.selectoutput.f1
- sql12.swb.managepartition.partitionaction.f1
- sql12.swb.managepartition.switchout.f1
- sql12.swb.managepartition.summary.f1
- sql12.swb.managepartition.createjob.f1
- sql12.swb.managepartition.stagingtable.f1
- sql12.swb.managepartition.progress.f1
- sql12.swb.managepartition.switchin.f1
- sql12.swb.managepartition.selectswitchtables.f1
helpviewer_keywords:
- wizards [SQL Server Management Studio] See Manage Partition Wizard
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b3e774168e9a48a0a387c3474b29f96081d875
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687827"
---
# <a name="manage-partition-wizard-f1-help"></a><span data-ttu-id="a29ec-102">“管理分区向导”的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="a29ec-102">Manage Partition Wizard F1 Help</span></span>
  <span data-ttu-id="a29ec-103">使用 **管理分区向导** 可以通过分区切换或实现可调窗口应用场景来管理和修改现有已分区表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-103">Use the **Manage Partition Wizard** to manage and modify existing partitioned tables through partition switching or the implementation of a sliding window scenario.</span></span> <span data-ttu-id="a29ec-104">使用此向导，可以轻松管理分区，并可简化表中数据的定期迁入和迁出。</span><span class="sxs-lookup"><span data-stu-id="a29ec-104">This wizard can ease the management of your partitions and simplify the regular migration of data in and out of your tables.</span></span>  
  
### <a name="to-start-the-manage-partition-wizard"></a><span data-ttu-id="a29ec-105">启动管理分区向导</span><span class="sxs-lookup"><span data-stu-id="a29ec-105">To start the Manage Partition Wizard</span></span>  
  
-   <span data-ttu-id="a29ec-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，选择数据库，右键单击要在其中创建分区的表，指向“存储”，然后单击“管理分区”。</span><span class="sxs-lookup"><span data-stu-id="a29ec-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the database, right-click the table on which you want to create partitions, point to **Storage**, and then click **Manage Partition**.</span></span>  
  
     <span data-ttu-id="a29ec-107">`Note`如果 "**管理分区**" 不可用，则可能是因为选择的表不包含分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-107">`Note` If **Manage Partition** is unavailable, you may have selected a table that does not contain partitions.</span></span> <span data-ttu-id="a29ec-108">在 **“存储”** 子菜单上单击 **“创建分区”** ，然后使用 **创建分区向导** 在表中创建分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-108">Click **Create Partition** on the **Storage** submenu and use the **Create Partition Wizard** to create partitions in your table.</span></span>  
  
 <span data-ttu-id="a29ec-109">有关分区和索引的一般信息，请参阅 [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="a29ec-109">For general information about partitions and indexes, see [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="a29ec-110">本节提供使用 **“管理分区向导”** 管理、修改和实现分区时所需的信息。</span><span class="sxs-lookup"><span data-stu-id="a29ec-110">This section provides the information that is required to manage, modify, and implement partitions using the **Manage Partition Wizard**.</span></span>  
  
##  <a name="in-this-section"></a><a name="Top"></a> <span data-ttu-id="a29ec-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="a29ec-111">In This Section</span></span>  
 <span data-ttu-id="a29ec-112">以下章节提供关于 **“管理分区向导”** 页的帮助。</span><span class="sxs-lookup"><span data-stu-id="a29ec-112">The following sections provide help on the pages of the **Manage Partition Wizard**.</span></span>  
  
 [<span data-ttu-id="a29ec-113">管理分区向导（“选择分区操作”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-113">Manage Partition Wizard (Select Partition Action Page)</span></span>](#SelectPartitionAction)  
  
 [<span data-ttu-id="a29ec-114">管理分区向导（切入页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-114">Manage Partition Wizard (Switch In Page)</span></span>](#SwitchIn)  
  
 [<span data-ttu-id="a29ec-115">管理分区向导（切出页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-115">Manage Partition Wizard (Switch Out Page)</span></span>](#SwitchOut)  
  
 [<span data-ttu-id="a29ec-116">管理分区向导（“选择临时表选项”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-116">Manage Partition Wizard (Select Staging Table Options Page)</span></span>](#StagingTableOptions)  
  
 [<span data-ttu-id="a29ec-117">管理分区向导（“选择输出选项”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-117">Manage Partition Wizard (Select Output Option Page)</span></span>](#OutputOption)  
  
 [<span data-ttu-id="a29ec-118">管理分区向导（“新建作业计划”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-118">Manage Partition Wizard (New Job Schedule Page)</span></span>](#NewJob)  
  
 [<span data-ttu-id="a29ec-119">管理分区向导（“摘要”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-119">Manage Partition Wizard (Summary Page)</span></span>](#Summary)  
  
 [<span data-ttu-id="a29ec-120">管理分区向导（“进度”页）</span><span class="sxs-lookup"><span data-stu-id="a29ec-120">Manage Partition Wizard (Progress Page)</span></span>](#Progress)  
  
##  <a name="select-partition-action-page"></a><a name="SelectPartitionAction"></a> <span data-ttu-id="a29ec-121">选择分区操作页面</span><span class="sxs-lookup"><span data-stu-id="a29ec-121">Select Partition Action Page</span></span>  
 <span data-ttu-id="a29ec-122">使用 **“选择分区操作”** 页可以选择要对分区执行的操作。</span><span class="sxs-lookup"><span data-stu-id="a29ec-122">Use the **Select Partition Action** page to choose the action you want to perform on your partition.</span></span>  
  
### <a name="create-a-staging-table"></a><span data-ttu-id="a29ec-123">创建临时表</span><span class="sxs-lookup"><span data-stu-id="a29ec-123">Create a Staging Table</span></span>  
 <span data-ttu-id="a29ec-124">如果您有一个定期迁入迁出数据的已分区表，则分区切换是常见分区任务；例如，您有一个存储当前季度数据的已分区表，必须在每季度末移入新数据并归档旧数据。</span><span class="sxs-lookup"><span data-stu-id="a29ec-124">Partition switching is a common partitioning task if you have a partitioned table that you migrate data into and out of on a regular basis; for example, you have a partitioned table that stores current quarterly data, and you must move in new data and archive older data at the end of each quarter.</span></span>  
  
 <span data-ttu-id="a29ec-125">该向导使用相同的分区列、表、列结构和索引来设计临时表，并将新表存储在源分区所在的文件组中。</span><span class="sxs-lookup"><span data-stu-id="a29ec-125">The wizard designs the staging table with the same partitioning column, table and column structure, and indexes, and stores the new table in the filegroup where your source partition is located.</span></span>  
  
 <span data-ttu-id="a29ec-126">若要创建临时表以切入或切出分区数据，请选择 **“为分区切换创建临时表”** 。</span><span class="sxs-lookup"><span data-stu-id="a29ec-126">To create a staging table to switch in or switch out partition data, select **Create a staging table for partition switching**.</span></span>  
  
### <a name="sliding-window-scenario"></a><span data-ttu-id="a29ec-127">滑动窗口应用场景</span><span class="sxs-lookup"><span data-stu-id="a29ec-127">Sliding Window Scenario</span></span>  
 <span data-ttu-id="a29ec-128">若要管理滑动窗口应用场景中的分区，请选择“管理滑动窗口应用场景中的分区数据”。</span><span class="sxs-lookup"><span data-stu-id="a29ec-128">To manage your partitions in a sliding-window scenario, select **Manage partitioned data in a sliding window scenario**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a29ec-129">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a29ec-129">UI element list</span></span>  
 <span data-ttu-id="a29ec-130">**“为分区切换创建临时表”**</span><span class="sxs-lookup"><span data-stu-id="a29ec-130">**Create a staging table for partition switching**</span></span>  
 <span data-ttu-id="a29ec-131">为切入和切出现有已分区表的数据创建临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-131">Creates a staging table for the data you are switching in or switching out of the existing partitioned table.</span></span>  
  
 <span data-ttu-id="a29ec-132">**切出分区**</span><span class="sxs-lookup"><span data-stu-id="a29ec-132">**Switch out partition**</span></span>  
 <span data-ttu-id="a29ec-133">在从表中删除分区时提供选项。</span><span class="sxs-lookup"><span data-stu-id="a29ec-133">Provides options when removing a partition from the table.</span></span>  
  
 <span data-ttu-id="a29ec-134">**切入分区**</span><span class="sxs-lookup"><span data-stu-id="a29ec-134">**Switch in partition**</span></span>  
 <span data-ttu-id="a29ec-135">在向表中添加分区时提供选项。</span><span class="sxs-lookup"><span data-stu-id="a29ec-135">Provides options when adding a partition to the table.</span></span>  
  
 <span data-ttu-id="a29ec-136">**管理滑动窗口应用场景中的分区数据**</span><span class="sxs-lookup"><span data-stu-id="a29ec-136">**Manage partitioned data in a sliding window scenario**</span></span>  
 <span data-ttu-id="a29ec-137">将空分区追加到可用于切入数据的现有表中。</span><span class="sxs-lookup"><span data-stu-id="a29ec-137">Appends an empty partition to the existing table that can be used for switching in data.</span></span> <span data-ttu-id="a29ec-138">向导当前支持切入上一个分区和切出第一个分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-138">The wizard currently supports switching into the last partition and switching out the first partition.</span></span>  
  
 <span data-ttu-id="a29ec-139">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-139">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-in-options-page"></a><a name="SwitchIn"></a> <span data-ttu-id="a29ec-140">选择分区切入选项页</span><span class="sxs-lookup"><span data-stu-id="a29ec-140">Select Partition Switching-In Options Page</span></span>  
 <span data-ttu-id="a29ec-141">使用“选择分区切入选项”页可以选择要切入到已分区表中的临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-141">Use the **Select Partition Switching-In options** page to select the staging table you are switching into the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a29ec-142">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a29ec-142">UI element list</span></span>  
 <span data-ttu-id="a29ec-143">**显示所有分区**</span><span class="sxs-lookup"><span data-stu-id="a29ec-143">**Show All Partitions**</span></span>  
 <span data-ttu-id="a29ec-144">选择此选项可以显示所有分区，包括当前位于已分区表的分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-144">Select to show all partitions, including the partitions currently in the partitioned table.</span></span>  
  
 <span data-ttu-id="a29ec-145">**分区网格**</span><span class="sxs-lookup"><span data-stu-id="a29ec-145">**Partition grid**</span></span>  
 <span data-ttu-id="a29ec-146">显示所选分区的分区名称、“左边界”、“右边界”、“文件组”和“行计数”。</span><span class="sxs-lookup"><span data-stu-id="a29ec-146">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="a29ec-147">**切入表**</span><span class="sxs-lookup"><span data-stu-id="a29ec-147">**Switch in table**</span></span>  
 <span data-ttu-id="a29ec-148">选择包含您要添加到您的已分区表的分区的临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-148">Select the staging table that contains the partition that you want to add to your partitioned table.</span></span> <span data-ttu-id="a29ec-149">必须先创建此临时表，然后才能使用“管理分区向导”来切入分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-149">You must create this staging table before you switch-in partitions with the **Manage PartitionsWizard**.</span></span>  
  
 <span data-ttu-id="a29ec-150">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-150">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-out-options-page"></a><a name="SwitchOut"></a> <span data-ttu-id="a29ec-151">选择分区切出选项页</span><span class="sxs-lookup"><span data-stu-id="a29ec-151">Select Partition Switching-Out Options Page</span></span>  
 <span data-ttu-id="a29ec-152">使用“选择分区切出选项”页可以选择用于保存要从已分区表中切出的分区数据的分区和临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-152">Use the **Select Partition Switching-Out options** page to select the partition and the staging table to hold the partitioned data that you are switching out of the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a29ec-153">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a29ec-153">UI element list</span></span>  
 <span data-ttu-id="a29ec-154">**分区网格**</span><span class="sxs-lookup"><span data-stu-id="a29ec-154">**Partition grid**</span></span>  
 <span data-ttu-id="a29ec-155">显示所选分区的分区名称、“左边界”、“右边界”、“文件组”和“行计数”。</span><span class="sxs-lookup"><span data-stu-id="a29ec-155">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="a29ec-156">**切出表**</span><span class="sxs-lookup"><span data-stu-id="a29ec-156">**Switch out table**</span></span>  
 <span data-ttu-id="a29ec-157">选择要将您的数据切出到的新表或现有表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-157">Choose a new table or an existing table to switch-out your data to.</span></span>  
  
 <span data-ttu-id="a29ec-158">**新建**</span><span class="sxs-lookup"><span data-stu-id="a29ec-158">**New**</span></span>  
 <span data-ttu-id="a29ec-159">输入要用于从当前源表切出的分区的临时表的新名称。</span><span class="sxs-lookup"><span data-stu-id="a29ec-159">Enter a new name for the staging table you want to use for the partition to switch out of the current source table.</span></span>  
  
 <span data-ttu-id="a29ec-160">**现有**</span><span class="sxs-lookup"><span data-stu-id="a29ec-160">**Existing**</span></span>  
 <span data-ttu-id="a29ec-161">选择要用于从当前源表切出的分区的现有临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-161">Select an existing staging table you want to use for the partition you want to switch out of the current source table.</span></span> <span data-ttu-id="a29ec-162">如果现有表包含数据，这些数据将被您切出的数据覆盖。</span><span class="sxs-lookup"><span data-stu-id="a29ec-162">If the existing table contains data, this data will be overwritten with the data you are switching out.</span></span>  
  
 <span data-ttu-id="a29ec-163">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-the-staging-table-options-page"></a><a name="StagingTableOptions"></a> <span data-ttu-id="a29ec-164">选择临时表选项页</span><span class="sxs-lookup"><span data-stu-id="a29ec-164">Select the Staging Table Options Page</span></span>  
 <span data-ttu-id="a29ec-165">使用 **“选择临时表选项”** 页可以创建用于切换已分区数据的临时表。</span><span class="sxs-lookup"><span data-stu-id="a29ec-165">Use the **Select the Staging Table Options** page to create the staging table you want to use for switching your partitioned data.</span></span>  
  
 <span data-ttu-id="a29ec-166">临时表必须与源表所在的选定分区位于同一文件组中。</span><span class="sxs-lookup"><span data-stu-id="a29ec-166">Staging tables must reside in the same filegroup of the selected partition where the source table is located.</span></span> <span data-ttu-id="a29ec-167">临时表必须镜像源表与目标表的设计。</span><span class="sxs-lookup"><span data-stu-id="a29ec-167">The staging table must mirror the design of both the source table and the destination table.</span></span>  
  
 <span data-ttu-id="a29ec-168">您可以在位于源分区的临时表中创建相同的索引。</span><span class="sxs-lookup"><span data-stu-id="a29ec-168">You can also create the same indexes in the staging table that exist in the source partition.</span></span> <span data-ttu-id="a29ec-169">临时表会自动基于源分区的元素包含约束。</span><span class="sxs-lookup"><span data-stu-id="a29ec-169">The staging table automatically contains a constraint based on the elements of the source partition.</span></span> <span data-ttu-id="a29ec-170">此约束通常根据源分区的边界值生成。</span><span class="sxs-lookup"><span data-stu-id="a29ec-170">This constraint is typically generated from the boundary value of the source partition.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a29ec-171">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a29ec-171">UI element list</span></span>  
 <span data-ttu-id="a29ec-172">**临时表名**</span><span class="sxs-lookup"><span data-stu-id="a29ec-172">**Staging table name**</span></span>  
 <span data-ttu-id="a29ec-173">为临时表创建名称，或接受编辑框中显示的默认名称。</span><span class="sxs-lookup"><span data-stu-id="a29ec-173">Create a name for the staging table or accept the default name displayed in the edit box.</span></span>  
  
 <span data-ttu-id="a29ec-174">**切换分区**</span><span class="sxs-lookup"><span data-stu-id="a29ec-174">**Switch partition**</span></span>  
 <span data-ttu-id="a29ec-175">选择您要从当前表中切换出的源分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-175">Select the source partition that you want to switch out of the current table.</span></span>  
  
 <span data-ttu-id="a29ec-176">**新建边界值**</span><span class="sxs-lookup"><span data-stu-id="a29ec-176">**New boundary value**</span></span>  
 <span data-ttu-id="a29ec-177">为临时表中的分区选择或输入所需边界值。</span><span class="sxs-lookup"><span data-stu-id="a29ec-177">Select or enter the boundary value you want for the partition in the staging table.</span></span>  
  
 <span data-ttu-id="a29ec-178">**文件组**</span><span class="sxs-lookup"><span data-stu-id="a29ec-178">**Filegroup**</span></span>  
 <span data-ttu-id="a29ec-179">为新表选择文件组。</span><span class="sxs-lookup"><span data-stu-id="a29ec-179">Select a filegroup for the new table.</span></span>  
  
 <span data-ttu-id="a29ec-180">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-180">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-output-option-page"></a><a name="OutputOption"></a> <span data-ttu-id="a29ec-181">选择输出选项页</span><span class="sxs-lookup"><span data-stu-id="a29ec-181">Select Output Option Page</span></span>  
 <span data-ttu-id="a29ec-182">使用 **“选择输出选项”** 页，以指定您想要如何完成对分区的修改。</span><span class="sxs-lookup"><span data-stu-id="a29ec-182">Use the **Select Output Option** page to specify how you want to complete the modifications to your partitions.</span></span>  
  
### <a name="create-script"></a><span data-ttu-id="a29ec-183">创建脚本</span><span class="sxs-lookup"><span data-stu-id="a29ec-183">Create Script</span></span>  
 <span data-ttu-id="a29ec-184">当向导完成时，它会在查询编辑器中创建脚本以修改表中的分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-184">When the wizard finishes, it creates a script in Query Editor to modify partitions in the table.</span></span> <span data-ttu-id="a29ec-185">如果要查看脚本，请选择 **“创建脚本”** ，然后手动执行脚本。</span><span class="sxs-lookup"><span data-stu-id="a29ec-185">Select **Create Script** if you want to review the script, and then execute the script manually.</span></span>  
  
 <span data-ttu-id="a29ec-186">**将脚本保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a29ec-186">**Script to file**</span></span>  
 <span data-ttu-id="a29ec-187">将脚本生成到 .sql 文件中。</span><span class="sxs-lookup"><span data-stu-id="a29ec-187">Generate the script to a .sql file.</span></span> <span data-ttu-id="a29ec-188">指定 **Unicode** 或 **“ANSI 文本”** 。</span><span class="sxs-lookup"><span data-stu-id="a29ec-188">Specify either **Unicode** or **ANSI text**.</span></span> <span data-ttu-id="a29ec-189">若要指定文件的名称和位置，请单击 **“浏览”** 。</span><span class="sxs-lookup"><span data-stu-id="a29ec-189">To specify a name and location for the file, click **Browse**.</span></span>  
  
 <span data-ttu-id="a29ec-190">**将脚本保存到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="a29ec-190">**Script to Clipboard**</span></span>  
 <span data-ttu-id="a29ec-191">将脚本保存到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="a29ec-191">Save the script to the Clipboard.</span></span>  
  
 <span data-ttu-id="a29ec-192">**将脚本保存到“新建查询”窗口**</span><span class="sxs-lookup"><span data-stu-id="a29ec-192">**Script to New Query Window**</span></span>  
 <span data-ttu-id="a29ec-193">将脚本生成到查询编辑器窗口。</span><span class="sxs-lookup"><span data-stu-id="a29ec-193">Generate the script to a Query Editor window.</span></span> <span data-ttu-id="a29ec-194">如果没有打开编辑器窗口，则将打开一个新的编辑器窗口作为脚本的目标。</span><span class="sxs-lookup"><span data-stu-id="a29ec-194">If no editor window is open, a new editor window opens as the target for the script.</span></span>  
  
### <a name="run-immediately"></a><span data-ttu-id="a29ec-195">立即运行</span><span class="sxs-lookup"><span data-stu-id="a29ec-195">Run Immediately</span></span>  
 <span data-ttu-id="a29ec-196">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="a29ec-196">**Run immediately**</span></span>  
 <span data-ttu-id="a29ec-197">当单击“下一步”或“完成”时，令向导完成对分区的修改。</span><span class="sxs-lookup"><span data-stu-id="a29ec-197">Have the wizard finish modifications to the partitions when you click **Next** or **Finish**.</span></span>  
  
### <a name="schedule"></a><span data-ttu-id="a29ec-198">计划</span><span class="sxs-lookup"><span data-stu-id="a29ec-198">Schedule</span></span>  
 <span data-ttu-id="a29ec-199">选中此项可以在计划的日期和时间修改表分区。</span><span class="sxs-lookup"><span data-stu-id="a29ec-199">Select to modify the table partitions at a scheduled date and time.</span></span>  
  
 <span data-ttu-id="a29ec-200">**更改计划**</span><span class="sxs-lookup"><span data-stu-id="a29ec-200">**Change schedule**</span></span>  
 <span data-ttu-id="a29ec-201">打开“新建作业计划”对话框，你可以在此对话框中选择、更改或查看计划作业的属性。</span><span class="sxs-lookup"><span data-stu-id="a29ec-201">Opens the **New Job Schedule** dialog box, where you can select, change, or view the properties of the scheduled job.</span></span>  
  
 <span data-ttu-id="a29ec-202">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-202">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="new-job-schedule-page"></a><a name="NewJob"></a> <span data-ttu-id="a29ec-203">新建作业计划页</span><span class="sxs-lookup"><span data-stu-id="a29ec-203">New Job Schedule Page</span></span>  
 <span data-ttu-id="a29ec-204">使用 **“新建作业计划”** 页可以查看和更改计划的属性。</span><span class="sxs-lookup"><span data-stu-id="a29ec-204">Use the **New Job Schedule** page to view and change the properties of the schedule.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a29ec-205">选项</span><span class="sxs-lookup"><span data-stu-id="a29ec-205">Options</span></span>  
 <span data-ttu-id="a29ec-206">为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业选择所需的计划类型。</span><span class="sxs-lookup"><span data-stu-id="a29ec-206">Select the type of schedule you want for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
 <span data-ttu-id="a29ec-207">**名称**</span><span class="sxs-lookup"><span data-stu-id="a29ec-207">**Name**</span></span>  
 <span data-ttu-id="a29ec-208">为计划键入一个新名称。</span><span class="sxs-lookup"><span data-stu-id="a29ec-208">Type a new name for the schedule.</span></span>  
  
 <span data-ttu-id="a29ec-209">**计划中的作业**</span><span class="sxs-lookup"><span data-stu-id="a29ec-209">**Jobs in schedule**</span></span>  
 <span data-ttu-id="a29ec-210">查看使用此计划的现有作业。</span><span class="sxs-lookup"><span data-stu-id="a29ec-210">View the existing jobs that use the schedule.</span></span>  
  
 <span data-ttu-id="a29ec-211">**计划类型**</span><span class="sxs-lookup"><span data-stu-id="a29ec-211">**Schedule type**</span></span>  
 <span data-ttu-id="a29ec-212">选择计划的类型。</span><span class="sxs-lookup"><span data-stu-id="a29ec-212">Select the type of schedule.</span></span>  
  
 <span data-ttu-id="a29ec-213">**已启用**</span><span class="sxs-lookup"><span data-stu-id="a29ec-213">**Enabled**</span></span>  
 <span data-ttu-id="a29ec-214">启用或禁用计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-214">Enable or disable the schedule.</span></span>  
  
### <a name="recurring-schedule-types-options"></a><span data-ttu-id="a29ec-215">重复执行计划类型选项</span><span class="sxs-lookup"><span data-stu-id="a29ec-215">Recurring Schedule Types Options</span></span>  
 <span data-ttu-id="a29ec-216">选择已计划作业的频率。</span><span class="sxs-lookup"><span data-stu-id="a29ec-216">Select the frequency of the scheduled job.</span></span>  
  
 <span data-ttu-id="a29ec-217">**执行**</span><span class="sxs-lookup"><span data-stu-id="a29ec-217">**Occurs**</span></span>  
 <span data-ttu-id="a29ec-218">选择重复执行计划的间隔。</span><span class="sxs-lookup"><span data-stu-id="a29ec-218">Select the interval at which the schedule recurs.</span></span>  
  
 <span data-ttu-id="a29ec-219">**执行间隔**</span><span class="sxs-lookup"><span data-stu-id="a29ec-219">**Recurs every**</span></span>  
 <span data-ttu-id="a29ec-220">选择重复执行计划的间隔天数或星期数。</span><span class="sxs-lookup"><span data-stu-id="a29ec-220">Select the number of days or weeks between recurrences of the schedule.</span></span> <span data-ttu-id="a29ec-221">此选项对于每月计划不可用。</span><span class="sxs-lookup"><span data-stu-id="a29ec-221">This option is not available for monthly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-222">**星期一**</span><span class="sxs-lookup"><span data-stu-id="a29ec-222">**Monday**</span></span>  
 <span data-ttu-id="a29ec-223">设置作业在特定的星期一发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-223">Set the job to occur on a Monday.</span></span> <span data-ttu-id="a29ec-224">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-224">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-225">**星期二**</span><span class="sxs-lookup"><span data-stu-id="a29ec-225">**Tuesday**</span></span>  
 <span data-ttu-id="a29ec-226">设置作业在特定的星期二发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-226">Set the job to occur on a Tuesday.</span></span> <span data-ttu-id="a29ec-227">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-227">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-228">**星期三**</span><span class="sxs-lookup"><span data-stu-id="a29ec-228">**Wednesday**</span></span>  
 <span data-ttu-id="a29ec-229">设置作业在特定的星期三发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-229">Set the job to occur on a Wednesday.</span></span> <span data-ttu-id="a29ec-230">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-230">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-231">**星期四**</span><span class="sxs-lookup"><span data-stu-id="a29ec-231">**Thursday**</span></span>  
 <span data-ttu-id="a29ec-232">设置作业在特定的星期四发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-232">Set the job to occur on a Thursday.</span></span> <span data-ttu-id="a29ec-233">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-233">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-234">**星期五**</span><span class="sxs-lookup"><span data-stu-id="a29ec-234">**Friday**</span></span>  
 <span data-ttu-id="a29ec-235">设置作业在特定的星期五发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-235">Set the job to occur on a Friday.</span></span> <span data-ttu-id="a29ec-236">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-236">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-237">**星期六**</span><span class="sxs-lookup"><span data-stu-id="a29ec-237">**Saturday**</span></span>  
 <span data-ttu-id="a29ec-238">设置作业在特定的星期六发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-238">Set the job to occur on a Saturday.</span></span> <span data-ttu-id="a29ec-239">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-239">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-240">**星期日**</span><span class="sxs-lookup"><span data-stu-id="a29ec-240">**Sunday**</span></span>  
 <span data-ttu-id="a29ec-241">设置作业在特定的星期日发生。</span><span class="sxs-lookup"><span data-stu-id="a29ec-241">Set the job to occur on a Sunday.</span></span> <span data-ttu-id="a29ec-242">只用于每周计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-242">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-243">**Day**</span><span class="sxs-lookup"><span data-stu-id="a29ec-243">**Day**</span></span>  
 <span data-ttu-id="a29ec-244">选择每月中执行此计划的日期。</span><span class="sxs-lookup"><span data-stu-id="a29ec-244">Select the day of the month the schedule occurs.</span></span> <span data-ttu-id="a29ec-245">只用于每月计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-245">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-246">**每**</span><span class="sxs-lookup"><span data-stu-id="a29ec-246">**of every**</span></span>  
 <span data-ttu-id="a29ec-247">选择两次计划间隔的月数。</span><span class="sxs-lookup"><span data-stu-id="a29ec-247">Select the number of months between occurrences of the schedule.</span></span> <span data-ttu-id="a29ec-248">只用于每月计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-248">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-249">**“应用程序池:”**</span><span class="sxs-lookup"><span data-stu-id="a29ec-249">**The**</span></span>  
 <span data-ttu-id="a29ec-250">为某月内特定一周的特定一天指定计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-250">Specify a schedule for a specific day of the week on a specific week within the month.</span></span> <span data-ttu-id="a29ec-251">只用于每月计划。</span><span class="sxs-lookup"><span data-stu-id="a29ec-251">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="a29ec-252">**执行一次，时间为**</span><span class="sxs-lookup"><span data-stu-id="a29ec-252">**Occurs once at**</span></span>  
 <span data-ttu-id="a29ec-253">设置每天执行作业的时间。</span><span class="sxs-lookup"><span data-stu-id="a29ec-253">Set the time for a job to occur daily.</span></span>  
  
 <span data-ttu-id="a29ec-254">**执行间隔**</span><span class="sxs-lookup"><span data-stu-id="a29ec-254">**Occurs every**</span></span>  
 <span data-ttu-id="a29ec-255">设置作业两次发生之间的时间间隔（小时或分钟）。</span><span class="sxs-lookup"><span data-stu-id="a29ec-255">Set the number of hours or minutes between occurrences.</span></span>  
  
 <span data-ttu-id="a29ec-256">**开始日期**</span><span class="sxs-lookup"><span data-stu-id="a29ec-256">**Start date**</span></span>  
 <span data-ttu-id="a29ec-257">设置此计划开始生效的日期。</span><span class="sxs-lookup"><span data-stu-id="a29ec-257">Set the date when this schedule will become effective.</span></span>  
  
 <span data-ttu-id="a29ec-258">**结束日期**</span><span class="sxs-lookup"><span data-stu-id="a29ec-258">**End date**</span></span>  
 <span data-ttu-id="a29ec-259">设置计划的失效日期。</span><span class="sxs-lookup"><span data-stu-id="a29ec-259">Set the date when the schedule will no longer be effective.</span></span>  
  
 <span data-ttu-id="a29ec-260">**无结束日期**</span><span class="sxs-lookup"><span data-stu-id="a29ec-260">**No end date**</span></span>  
 <span data-ttu-id="a29ec-261">指定计划将无限期地保持有效。</span><span class="sxs-lookup"><span data-stu-id="a29ec-261">Specify that the schedule will remain effective indefinitely.</span></span>  
  
### <a name="one-time-schedule-types-options"></a><span data-ttu-id="a29ec-262">一次性计划类型选项</span><span class="sxs-lookup"><span data-stu-id="a29ec-262">One Time Schedule Types Options</span></span>  
 <span data-ttu-id="a29ec-263">如果计划某个作业运行一次，您必须选择一个将来的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="a29ec-263">If you schedule a job to run once, you must select a date and time in the future.</span></span>  
  
 <span data-ttu-id="a29ec-264">**Date**</span><span class="sxs-lookup"><span data-stu-id="a29ec-264">**Date**</span></span>  
 <span data-ttu-id="a29ec-265">选择作业的计划运行日期。</span><span class="sxs-lookup"><span data-stu-id="a29ec-265">Select the date for the job to run.</span></span>  
  
 <span data-ttu-id="a29ec-266">**时间**</span><span class="sxs-lookup"><span data-stu-id="a29ec-266">**Time**</span></span>  
 <span data-ttu-id="a29ec-267">选择作业的计划运行时间。</span><span class="sxs-lookup"><span data-stu-id="a29ec-267">Select the time for the job to run.</span></span>  
  
 <span data-ttu-id="a29ec-268">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-268">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="a29ec-269">摘要页</span><span class="sxs-lookup"><span data-stu-id="a29ec-269">Summary Page</span></span>  
 <span data-ttu-id="a29ec-270">使用 **“摘要”** 可检查您在前面的页中选择的选项。</span><span class="sxs-lookup"><span data-stu-id="a29ec-270">Use the **Summary** page to review the options that you have selected on the previous pages.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a29ec-271">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="a29ec-271">UI element list</span></span>  
 <span data-ttu-id="a29ec-272">**检查所做选择**</span><span class="sxs-lookup"><span data-stu-id="a29ec-272">**Review your selections**</span></span>  
 <span data-ttu-id="a29ec-273">显示您在向导的每一页中所做的选择。</span><span class="sxs-lookup"><span data-stu-id="a29ec-273">Displays the selections you have made for each page of the wizard.</span></span> <span data-ttu-id="a29ec-274">单击节点可展开和查看以前选择的选项。</span><span class="sxs-lookup"><span data-stu-id="a29ec-274">Click a node to expand and view your previously selected options.</span></span>  
  
 <span data-ttu-id="a29ec-275">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-275">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="a29ec-276">“进度”页</span><span class="sxs-lookup"><span data-stu-id="a29ec-276">Progress Page</span></span>  
 <span data-ttu-id="a29ec-277">使用 **“进度”** 页可以监视有关 **“管理分区向导”** 操作的状态信息。</span><span class="sxs-lookup"><span data-stu-id="a29ec-277">Use the **Progress** page to monitor status information about the actions of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="a29ec-278">根据在向导中选择的选项， **“进度”** 页可能会包含一个操作或多个操作。</span><span class="sxs-lookup"><span data-stu-id="a29ec-278">Depending on the options that you selected in the wizard, the **Progress** page might contain one or more actions.</span></span> <span data-ttu-id="a29ec-279">最上面的方框显示向导的总体状态和向导已接收到的状态、错误和警告消息数。</span><span class="sxs-lookup"><span data-stu-id="a29ec-279">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a29ec-280">选项</span><span class="sxs-lookup"><span data-stu-id="a29ec-280">Options</span></span>  
 <span data-ttu-id="a29ec-281">**详细信息**</span><span class="sxs-lookup"><span data-stu-id="a29ec-281">**Details**</span></span>  
 <span data-ttu-id="a29ec-282">提供向导执行的操作所返回的操作、状态和所有消息。</span><span class="sxs-lookup"><span data-stu-id="a29ec-282">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
 <span data-ttu-id="a29ec-283">**Action**</span><span class="sxs-lookup"><span data-stu-id="a29ec-283">**Action**</span></span>  
 <span data-ttu-id="a29ec-284">指定每个操作的类型和名称。</span><span class="sxs-lookup"><span data-stu-id="a29ec-284">Specifies the type and name of each action.</span></span>  
  
 <span data-ttu-id="a29ec-285">**Status**</span><span class="sxs-lookup"><span data-stu-id="a29ec-285">**Status**</span></span>  
 <span data-ttu-id="a29ec-286">指示向导操作作为一个整体返回的值是“成功”还是“失败”。</span><span class="sxs-lookup"><span data-stu-id="a29ec-286">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
 <span data-ttu-id="a29ec-287">**消息**</span><span class="sxs-lookup"><span data-stu-id="a29ec-287">**Message**</span></span>  
 <span data-ttu-id="a29ec-288">提供从该进程中返回的任何错误或警告消息。</span><span class="sxs-lookup"><span data-stu-id="a29ec-288">Provides any error or warning messages that are returned from the process.</span></span>  
  
 <span data-ttu-id="a29ec-289">**Stop**</span><span class="sxs-lookup"><span data-stu-id="a29ec-289">**Stop**</span></span>  
 <span data-ttu-id="a29ec-290">停止向导的操作。</span><span class="sxs-lookup"><span data-stu-id="a29ec-290">Stop the action of the wizard.</span></span>  
  
 <span data-ttu-id="a29ec-291">**Report**</span><span class="sxs-lookup"><span data-stu-id="a29ec-291">**Report**</span></span>  
 <span data-ttu-id="a29ec-292">创建一个包含“管理分区向导”的结果的报告。</span><span class="sxs-lookup"><span data-stu-id="a29ec-292">Create a report that contains the results of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="a29ec-293">选项包括：</span><span class="sxs-lookup"><span data-stu-id="a29ec-293">The options are:</span></span>  
  
-   <span data-ttu-id="a29ec-294">**查看报告**</span><span class="sxs-lookup"><span data-stu-id="a29ec-294">**View Report**</span></span>  
  
-   <span data-ttu-id="a29ec-295">**将报告保存到文件**</span><span class="sxs-lookup"><span data-stu-id="a29ec-295">**Save Report to File**</span></span>  
  
-   <span data-ttu-id="a29ec-296">**将报告复制到剪贴板**</span><span class="sxs-lookup"><span data-stu-id="a29ec-296">**Copy Report to Clipboard**</span></span>  
  
-   <span data-ttu-id="a29ec-297">**“将报告作为电子邮件发送”**</span><span class="sxs-lookup"><span data-stu-id="a29ec-297">**Send Report as Email**</span></span>  
  
 <span data-ttu-id="a29ec-298">**查看报告**</span><span class="sxs-lookup"><span data-stu-id="a29ec-298">**View Report**</span></span>  
 <span data-ttu-id="a29ec-299">打开“查看报告”对话框。</span><span class="sxs-lookup"><span data-stu-id="a29ec-299">Open the **View Report** dialog box.</span></span> <span data-ttu-id="a29ec-300">此对话框包含 **管理分区向导**进度的文本报告。</span><span class="sxs-lookup"><span data-stu-id="a29ec-300">This dialog box contains a text report of the progress of the **Manage Partition Wizard**.</span></span>  
  
 <span data-ttu-id="a29ec-301">**关闭**</span><span class="sxs-lookup"><span data-stu-id="a29ec-301">**Close**</span></span>  
 <span data-ttu-id="a29ec-302">关闭向导。</span><span class="sxs-lookup"><span data-stu-id="a29ec-302">Close the wizard.</span></span>  
  
 <span data-ttu-id="a29ec-303">![用于返回页首链接的箭头图标](../../2014-toc/media/uparrow16x16.gif "用于返回页首链接的箭头图标") [本部分](#Top)</span><span class="sxs-lookup"><span data-stu-id="a29ec-303">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29ec-304">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a29ec-304">See Also</span></span>  
 [<span data-ttu-id="a29ec-305">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="a29ec-305">Partitioned Tables and Indexes</span></span>](partitioned-tables-and-indexes.md)  
  
  
