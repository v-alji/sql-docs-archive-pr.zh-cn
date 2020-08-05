---
title: " (SSAS 表格) 创建和管理工作区数据库中的分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3824dd4763e516dc5e8e34a9ec815d3969f4eb79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580402"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="99a08-102">创建和管理工作区数据库中的分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="99a08-102">Create and Manage Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="99a08-103">分区将表分成多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="99a08-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="99a08-104">然后，可单独处理（刷新）每个分区，也可与其他分区并行处理每个分区。</span><span class="sxs-lookup"><span data-stu-id="99a08-104">Each partition can then be processed (Refreshed) independently or in parallel with other partitions.</span></span> <span data-ttu-id="99a08-105">分区可以提高大型数据库的可扩展性和可管理性。</span><span class="sxs-lookup"><span data-stu-id="99a08-105">Partitions can improve scalability and manageability of large databases.</span></span> <span data-ttu-id="99a08-106">默认情况下，每个表都具有一个包含所有列的分区。</span><span class="sxs-lookup"><span data-stu-id="99a08-106">By default, each table has one partition that includes all columns.</span></span> <span data-ttu-id="99a08-107">本主题中的任务说明如何使用中的 "**分区管理器**" 对话框在模型工作区数据库中创建和管理分区。[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a08-107">Tasks in this topic describe how to create and manage partitions in the model workspace database by using the **Partition Manager** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span></span>  
  
 <span data-ttu-id="99a08-108">在将模型部署到其他 Analysis Services 实例后，数据库管理员可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]在（已部署）模型中创建和管理分区。</span><span class="sxs-lookup"><span data-stu-id="99a08-108">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="99a08-109">有关详细信息，请参阅[创建和管理表格模型分区（SSAS 表格）](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="99a08-109">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="99a08-110">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="99a08-110">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="99a08-111">创建新分区</span><span class="sxs-lookup"><span data-stu-id="99a08-111">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="99a08-112">复制分区</span><span class="sxs-lookup"><span data-stu-id="99a08-112">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="99a08-113">删除分区</span><span class="sxs-lookup"><span data-stu-id="99a08-113">To delete a partition</span></span>](#bkmk_delete)  
  
> [!NOTE]  
>  <span data-ttu-id="99a08-114">使用“分区管理器”对话框不能在模型工作区数据库中合并分区。</span><span class="sxs-lookup"><span data-stu-id="99a08-114">You cannot merge partitions in the model workspace database by using the Partition Manager dialog box.</span></span> <span data-ttu-id="99a08-115">通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，仅能在已部署的模型中合并分区。</span><span class="sxs-lookup"><span data-stu-id="99a08-115">Partitions can be merged in a deployed model only by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="99a08-116">任务</span><span class="sxs-lookup"><span data-stu-id="99a08-116">Tasks</span></span>  
 <span data-ttu-id="99a08-117">若要创建和管理分区，您将使用 **“分区管理器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="99a08-117">To create and manage partitions, you will use the **Partitions Manager** dialog box.</span></span> <span data-ttu-id="99a08-118">若要查看 **“分区管理器”** 对话框，请在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“表”** 菜单，然后单击 **“分区”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-118">To view the **Partitions Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="99a08-119">创建新分区</span><span class="sxs-lookup"><span data-stu-id="99a08-119">To create a new partition</span></span>  
  
1.  <span data-ttu-id="99a08-120">在模型设计器中，选择要为其定义分区的表。</span><span class="sxs-lookup"><span data-stu-id="99a08-120">In the model designer, select the table for which you want to define a partition.</span></span>  
  
2.  <span data-ttu-id="99a08-121">单击 **“表”** 菜单，然后单击 **“分区”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-121">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="99a08-122">在 **“分区管理器”** 的 **“表”** 列表框中，验证或选择要分区的表，然后单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-122">In **Partition Manager**, in the **Table** listbox, verify or select the table you want to partition, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="99a08-123">在 **“分区名称”** 中，键入分区的名称。</span><span class="sxs-lookup"><span data-stu-id="99a08-123">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="99a08-124">默认情况下，对于每个新建分区，默认分区的名称将为递增式编号。</span><span class="sxs-lookup"><span data-stu-id="99a08-124">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
5.  <span data-ttu-id="99a08-125">通过使用表预览模式或使用通过查询编辑器模式创建的 SQL 查询，您可以选择包含在分区中的行和列。</span><span class="sxs-lookup"><span data-stu-id="99a08-125">You can select the rows and columns to be included in the partition by using Table Preview mode or by using a SQL query created using Query Editor mode.</span></span>  
  
     <span data-ttu-id="99a08-126">若要使用表预览模式（默认），请单击预览窗口右上角附近的“表预览”按钮。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="99a08-126">To use Table Preview mode (default), click the **Table Preview** button near the upper-right corner of the preview window.</span></span> <span data-ttu-id="99a08-127">通过选中列名称旁边的复选框，选择要包含在分区中的列。</span><span class="sxs-lookup"><span data-stu-id="99a08-127">Select the columns you want to include in the partition by selecting the checkbox next to the column name.</span></span> <span data-ttu-id="99a08-128">若要筛选行，右键单击一个单元值，然后单击 **“按所选的单元值筛选”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-128">To filter rows, right click a cell value, and click **Filter by Selected Cell Value**.</span></span>  
  
     <span data-ttu-id="99a08-129">若要使用 SQL 语句，请单击预览窗口右上角附近的“查询编辑器”按钮，然后将 SQL 查询语句键入或粘贴到查询窗口中。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="99a08-129">To use a SQL statement, click the **Query Editor** button near the upper-right corner of the preview window, then type or paste a SQL query statement into the query window.</span></span> <span data-ttu-id="99a08-130">若要验证您的语句，请单击 **“验证”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-130">To validate your statement, click **Validate**.</span></span> <span data-ttu-id="99a08-131">若要使用查询设计器，请单击 **“设计”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-131">To use the Query Designer, click **Design**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="99a08-132">复制分区</span><span class="sxs-lookup"><span data-stu-id="99a08-132">To copy a partition</span></span>  
  
1.  <span data-ttu-id="99a08-133">在 **“分区管理器”** 的 **“表”** 列表框中，验证或选择包含要复制的分区的表。</span><span class="sxs-lookup"><span data-stu-id="99a08-133">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to copy.</span></span>  
  
2.  <span data-ttu-id="99a08-134">在 **“分区”** 列表中，选择要复制的分区，然后单击 **“复制”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-134">In the **Partitions** list, select the partition you want to copy and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="99a08-135">在 **“分区名称”** 中，键入分区的新名称。</span><span class="sxs-lookup"><span data-stu-id="99a08-135">In **Partition Name**, type a new name for the partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="99a08-136">删除分区</span><span class="sxs-lookup"><span data-stu-id="99a08-136">To delete a partition</span></span>  
  
1.  <span data-ttu-id="99a08-137">在 **“分区管理器”** 的 **“表”** 列表框中，验证或选择包含要删除的分区的表。</span><span class="sxs-lookup"><span data-stu-id="99a08-137">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to delete.</span></span>  
  
2.  <span data-ttu-id="99a08-138">在 **“分区”** 列表中，选择要删除的分区，然后单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="99a08-138">In the **Partitions** list, select the partition you want to delete and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a08-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99a08-139">See Also</span></span>  
 <span data-ttu-id="99a08-140">[&#40;SSAS 表格&#41;分区](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="99a08-140">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="99a08-141">&#40;SSAS 表格中处理工作区数据库中的分区&#41;</span><span class="sxs-lookup"><span data-stu-id="99a08-141">Process Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
