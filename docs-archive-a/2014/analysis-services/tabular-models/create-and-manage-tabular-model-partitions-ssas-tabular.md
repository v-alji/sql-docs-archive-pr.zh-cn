---
title: " (SSAS 表格) 创建和管理表格模型分区 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58c408c712d6ac4b6bd590bd0f8c895dc1a88700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589224"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="cdf9e-102">创建和管理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="cdf9e-102">Create and Manage Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="cdf9e-103">分区将表分成多个逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="cdf9e-104">然后，每个分区可独立于其他分区进行处理（刷新）。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="cdf9e-105">在已部署的模型中将重复在模型创作过程中为模型定义的分区。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-105">Partitions defined for a model during model authoring are duplicated in a deployed model.</span></span> <span data-ttu-id="cdf9e-106">部署完成后，您可以通过使用 **中的** “分区” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对话框或使用脚本来管理这些分区。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-106">Once deployed, you can manage those partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by using a script.</span></span> <span data-ttu-id="cdf9e-107">本主题中提供的任务介绍如何为已部署的模型创建和管理分区。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-107">Tasks provided in this topic describe how to create and manage partitions for a deployed model.</span></span>  
  
 <span data-ttu-id="cdf9e-108">本主题包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="cdf9e-108">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="cdf9e-109">创建新分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-109">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="cdf9e-110">复制分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-110">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="cdf9e-111">合并两个或更多分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-111">To merge two or more partitions</span></span>](#bkmk_merge)  
  
-   [<span data-ttu-id="cdf9e-112">删除分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-112">To delete a partition</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="cdf9e-113">任务</span><span class="sxs-lookup"><span data-stu-id="cdf9e-113">Tasks</span></span>  
 <span data-ttu-id="cdf9e-114">若要为已部署的表格模型数据库创建和管理分区，您可以使用 **中的** “分区” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]对话框。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-114">To create and manage partitions for a deployed tabular model database, you will use the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cdf9e-115">若要查看“分区”对话框，请在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中右键单击某一表，然后单击“分区”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="cdf9e-115">To view the **Partitions** dialog box, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on a table, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="cdf9e-116">创建新分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-116">To create a new partition</span></span>  
  
1.  <span data-ttu-id="cdf9e-117">在 **“分区”** 对话框中，单击 **“新建”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-117">In the **Partitions** dialog box, click the **New** button.</span></span>  
  
2.  <span data-ttu-id="cdf9e-118">在 **“分区名称”** 中，键入分区的名称。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-118">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="cdf9e-119">默认情况下，对于每个新建分区，默认分区的名称将为递增式编号。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-119">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
3.  <span data-ttu-id="cdf9e-120">在 **“SQL 语句”** 中，将定义您想要在分区中包含的列和任何子句的 SQL 查询语句键入或粘贴到查询窗口中。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-120">In **SQL Statement**, type or paste a SQL query statement that defines the columns and any clauses you want to include in the partition into the query window.</span></span>  
  
4.  <span data-ttu-id="cdf9e-121">若要验证语句，请单击 **“检查语法”**。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-121">To validate the statement, click **Check Syntax**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="cdf9e-122">复制分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-122">To copy a partition</span></span>  
  
1.  <span data-ttu-id="cdf9e-123">在 **“分区”** 对话框的 **“分区”** 列表中，选择您要复制的分区，然后单击 **“复制”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-123">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to copy, and then click the **Copy** button.</span></span>  
  
2.  <span data-ttu-id="cdf9e-124">在 **“分区名称”** 中，键入分区的新名称。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-124">In **Partition Name**, type a new name for the partition.</span></span>  
  
3.  <span data-ttu-id="cdf9e-125">在 **“SQL 语句”**，编辑 SQL 查询语句。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-125">In **SQL Statement**, edit the SQL query statement.</span></span>  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> <span data-ttu-id="cdf9e-126">合并两个或更多分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-126">To merge two or more partitions</span></span>  
  
-   <span data-ttu-id="cdf9e-127">在 "**分区**" 对话框的 "**分区**" 列表中，使用 Ctrl + 单击选择要合并的分区，然后单击 "**合并**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-127">In the **Partitions** dialog box, in the **Partitions** list, use Ctrl+click to select the partitions you want to merge, and then click the **Merge** button.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cdf9e-128">合并分区不会更新分区元数据。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-128">Merging partitions does not update the partition metadata.</span></span> <span data-ttu-id="cdf9e-129">管理员必须为所得分区更改 SQL 语句，以确保处理操作处理合并分区中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-129">Administrators must alter the SQL Statement for the resulting partition to make sure processing operations process all data in the merged partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="cdf9e-130">删除分区</span><span class="sxs-lookup"><span data-stu-id="cdf9e-130">To delete a partition</span></span>  
  
-   <span data-ttu-id="cdf9e-131">在 **“分区”** 对话框的 **“分区”** 列表中，选择您要删除的分区，然后单击 **“删除”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cdf9e-131">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to delete, and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf9e-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdf9e-132">See Also</span></span>  
 <span data-ttu-id="cdf9e-133">[&#40;SSAS 表格&#41;的表格模型分区](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="cdf9e-133">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="cdf9e-134">处理表格模型分区（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="cdf9e-134">Process Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](process-tabular-model-partitions-ssas-tabular.md)  
  
  
