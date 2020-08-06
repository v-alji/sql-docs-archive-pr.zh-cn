---
title: 编辑或删除分区 (Analysis Services-多维) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying partitions
- partitions [Analysis Services], modifying
ms.assetid: fb7a64ca-d021-4926-b92d-83476fbc40a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e611ac51ce4a6495225d8e8e7ce05b0c0a83b40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590391"
---
# <a name="edit-or-delete-partitions-analyisis-services---multidimensional"></a><span data-ttu-id="99b37-102">编辑或删除分区（Analysis Services - 多维）</span><span class="sxs-lookup"><span data-stu-id="99b37-102">Edit or Delete Partitions (Analyisis Services - Multidimensional)</span></span>
  <span data-ttu-id="99b37-103">多维数据集分区可在 **中使用多维数据集设计器中的** “分区” [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]选项卡来修改。</span><span class="sxs-lookup"><span data-stu-id="99b37-103">Cube partitions are modified using the **Partitions** tab in Cube Designer in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="99b37-104">**“分区”** 选项卡列出了多维数据集中的所有度量值组的分区。</span><span class="sxs-lookup"><span data-stu-id="99b37-104">The **Partitions** tab lists the partitions for all of the measure groups in a cube.</span></span> <span data-ttu-id="99b37-105">它还列出了已启用写回的写回分区。</span><span class="sxs-lookup"><span data-stu-id="99b37-105">It also lists the writeback partitions that have writeback enabled.</span></span>

 <span data-ttu-id="99b37-106">若要编辑任何度量值组的分区，请在 "**分区**" 选项卡上展开度量值组。度量值组的分区按序号以表的形式列出，下表中列出了这些列。</span><span class="sxs-lookup"><span data-stu-id="99b37-106">To edit the partitions for any measure group, expand the measure group on the **Partitions** tab. Partitions for a measure group are listed by ordinal number in a table format with the columns listed in the following table.</span></span>

 <span data-ttu-id="99b37-107">必须在源多维数据集中编辑链接度量值组的设置。</span><span class="sxs-lookup"><span data-stu-id="99b37-107">Settings for a linked measure group must be edited in the source cube.</span></span>

 <span data-ttu-id="99b37-108">当您将源分区合并到目标分区时，将自动删除分区。</span><span class="sxs-lookup"><span data-stu-id="99b37-108">Deleting partitions occurs automatically when you merge a source partition into a destination partition.</span></span> <span data-ttu-id="99b37-109">合并后将删除被指定为“源”的分区。</span><span class="sxs-lookup"><span data-stu-id="99b37-109">The partition specified as the Source is deleted after the merge is completed.</span></span> <span data-ttu-id="99b37-110">您也可以在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中或在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]中的“分区”选项卡中手动删除分区。</span><span class="sxs-lookup"><span data-stu-id="99b37-110">You can also delete partitions manually in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or in the Partitions tab in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="99b37-111">右键单击并选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="99b37-111">Right-click and choose **Delete**.</span></span> <span data-ttu-id="99b37-112">请记住，删除分区时也会同时删除数据和聚合。</span><span class="sxs-lookup"><span data-stu-id="99b37-112">Remember that deleting a partition also deletes data and aggregations.</span></span> <span data-ttu-id="99b37-113">作为预防措施，请确保您具有数据库的近期备份版本，以备您在以后需要撤消此步骤时使用。</span><span class="sxs-lookup"><span data-stu-id="99b37-113">As a precaution, make sure you have a recent back up of the database in case you need to reverse this step later.</span></span>

> [!NOTE]
>  <span data-ttu-id="99b37-114">或者，您也可以使用可自动执行生成、合并和删除分区任务的 XMLA 脚本。</span><span class="sxs-lookup"><span data-stu-id="99b37-114">Alternatively, you can use XMLA scripts that automate tasks for building, merging, and deleting partitions.</span></span> <span data-ttu-id="99b37-115">XMLA 脚本可在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中或在作为计划任务运行的自定义 SSIS 包中创建和执行。</span><span class="sxs-lookup"><span data-stu-id="99b37-115">XMLA script can be created and executed in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], or in custom SSIS packages that runs as a scheduled task.</span></span> <span data-ttu-id="99b37-116">有关详细信息，请参阅 [Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="99b37-116">For more information, see [Automate Analysis Services Administrative Tasks with SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).</span></span>

## <a name="partition-source"></a><span data-ttu-id="99b37-117">分区源</span><span class="sxs-lookup"><span data-stu-id="99b37-117">Partition source</span></span>
 <span data-ttu-id="99b37-118">为分区指定源表或命名查询。</span><span class="sxs-lookup"><span data-stu-id="99b37-118">Specifies the source table or named query for the partition.</span></span> <span data-ttu-id="99b37-119">若要更改源表，请单击该单元，再单击浏览 (**...**) 按钮。</span><span class="sxs-lookup"><span data-stu-id="99b37-119">To change the source table, click the cell and then click the browse (**...**) button.</span></span>

 <span data-ttu-id="99b37-120">![“分区”窗格中的源列](../media/ssas-partitionsource.png "“分区”窗格中的源列")</span><span class="sxs-lookup"><span data-stu-id="99b37-120">![Source column in Partition pane](../media/ssas-partitionsource.png "Source column in Partition pane")</span></span>

 <span data-ttu-id="99b37-121">如果分区基于一个查询，则单击浏览 (**...**) 按钮来编辑该查询。</span><span class="sxs-lookup"><span data-stu-id="99b37-121">If the partition is based on a query, click the browse (**...**) button to edit the query.</span></span> <span data-ttu-id="99b37-122">这将编辑分区的 **“源”** 属性。</span><span class="sxs-lookup"><span data-stu-id="99b37-122">This edits the **Source** property for the partition.</span></span> <span data-ttu-id="99b37-123">有关详细信息，请参阅[将分区源更改为使用不同的事实数据表](change-a-partition-source-to-use-a-different-fact-table.md)。</span><span class="sxs-lookup"><span data-stu-id="99b37-123">For more information, see [Change a partition source to use a different fact table](change-a-partition-source-to-use-a-different-fact-table.md).</span></span>

 <span data-ttu-id="99b37-124">您可以指定数据源视图中与初始源表（在用于检索数据的外部数据源中）具有相同结构的表。</span><span class="sxs-lookup"><span data-stu-id="99b37-124">You can specify a table in the data source view that has the same structure as the original source table (in the external data source from which the data is retrieved).</span></span> <span data-ttu-id="99b37-125">源可位于多维数据集数据库的任意数据源或数据源视图中。</span><span class="sxs-lookup"><span data-stu-id="99b37-125">The source can be in any of the data sources or data source views of the cube database.</span></span>

## <a name="storage-settings"></a><span data-ttu-id="99b37-126">存储设置</span><span class="sxs-lookup"><span data-stu-id="99b37-126">Storage settings</span></span>
 <span data-ttu-id="99b37-127">在多维数据集设计器中的“分区”选项卡上，可以单击 **“存储设置”** 为 MOLAP 、ROLAP 或 HOLAP 存储选择一个标准设置，也可以为存储模式和主动缓存配置自定义设置。</span><span class="sxs-lookup"><span data-stu-id="99b37-127">In Cube Designer, on the Partitions tab, you can click **Storage Settings** to pick one of the standard settings for MOLAP, ROLAP, or HOLAP storage, or to configure custom settings for the storage mode and proactive caching.</span></span> <span data-ttu-id="99b37-128">默认选择是 MOLAP，因为它能够提供最佳查询性能。</span><span class="sxs-lookup"><span data-stu-id="99b37-128">The default is MOLAP because it delivers the fastest query performance.</span></span> <span data-ttu-id="99b37-129">有关每个设置的详细信息，请参阅[设置分区存储（Analysis Services - 多维）](set-partition-storage-analysis-services-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="99b37-129">For more information about each setting, see [Set Partition Storage &#40;Analysis Services - Multidimensional&#41;](set-partition-storage-analysis-services-multidimensional.md).</span></span>

 <span data-ttu-id="99b37-130">可以为多维数据集中每个度量值组的每一个分区分别配置存储。</span><span class="sxs-lookup"><span data-stu-id="99b37-130">Storage can be configured separately for each partition of each measure group in a cube.</span></span> <span data-ttu-id="99b37-131">也可以为多维数据集或度量值组配置默认存储设置。</span><span class="sxs-lookup"><span data-stu-id="99b37-131">You can also configure the default storage settings for a cube or measure group.</span></span> <span data-ttu-id="99b37-132">存储是在多维数据集向导中的 **“分区”** 选项卡中进行配置的。</span><span class="sxs-lookup"><span data-stu-id="99b37-132">Storage is configured on the **Partitions** tab in the Cube Wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="99b37-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99b37-133">See Also</span></span>
 <span data-ttu-id="99b37-134">在 Analysis Services&#41;[SSAS-多维 Analysis Services 中](merge-partitions-in-analysis-services-ssas-multidimensional.md)[创建和管理本地分区 &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [设计聚合 &#40;&#40;多维&#41;](designing-aggregations-analysis-services-multidimensional.md)合并分区</span><span class="sxs-lookup"><span data-stu-id="99b37-134">[Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md) [Designing Aggregations &#40;Analysis Services - Multidimensional&#41;](designing-aggregations-analysis-services-multidimensional.md) [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](merge-partitions-in-analysis-services-ssas-multidimensional.md)</span></span>


