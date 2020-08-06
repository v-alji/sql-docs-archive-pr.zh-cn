---
title: 设置分区写回 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], writeback
- partitions [Analysis Services], write-enabled
- writeback [Analysis Services], partitions
ms.assetid: 38bb09cc-2652-4971-8373-0cf468cdc7a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: eaea005bf919545e5d63be481eb3478b286c16d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587051"
---
# <a name="set-partition-writeback"></a><span data-ttu-id="05ac2-102">设置分区写回</span><span class="sxs-lookup"><span data-stu-id="05ac2-102">Set Partition Writeback</span></span>
  <span data-ttu-id="05ac2-103">如果对度量值组执行写启用操作，则最终用户可在浏览多维数据集数据时对其进行更改，所做的更改保存在一个称为“写回表”的单独表中，而不是多维数据集数据或源数据中。</span><span class="sxs-lookup"><span data-stu-id="05ac2-103">If you write-enable a measure group, end users can change cube data while they browse it, where changes are saved in a separate table called a writeback table, not in the cube data or source data.</span></span> <span data-ttu-id="05ac2-104">浏览已启用写操作的分区的最终用户将看到对该分区在这个写回表中所做的全部更改的实际结果。</span><span class="sxs-lookup"><span data-stu-id="05ac2-104">End users who browse a write-enabled partition see the net effect of all changes in the writeback table for the partition.</span></span>  
  
 <span data-ttu-id="05ac2-105">可以浏览或删除写回数据。</span><span class="sxs-lookup"><span data-stu-id="05ac2-105">You can browse or delete writeback data.</span></span> <span data-ttu-id="05ac2-106">还可以将写回数据转换为分区。</span><span class="sxs-lookup"><span data-stu-id="05ac2-106">You can also convert writeback data to a partition.</span></span> <span data-ttu-id="05ac2-107">在已启用写操作的分区上，可使用多维数据集角色授予用户和用户组读/写权限，并限制对分区中特定单元或单元组的访问。</span><span class="sxs-lookup"><span data-stu-id="05ac2-107">On a write-enabled partition, you can use cube roles to grant read/write access to users and groups of users, and to limit access to specific cells or groups of cells in the partition.</span></span>  
  
 <span data-ttu-id="05ac2-108">有关写回的一个简短视频简介，请参阅 [向 Analysis Services 的 Excel 2010 写回](https://go.microsoft.com/fwlink/p/?LinkId=394951)。</span><span class="sxs-lookup"><span data-stu-id="05ac2-108">For a short video introduction to writeback, see [Excel 2010 Writeback to Analysis Services](https://go.microsoft.com/fwlink/p/?LinkId=394951).</span></span> <span data-ttu-id="05ac2-109">关于此功能的更详细探讨，请参阅博客文章系列 [使用 Analysis Services 生成写回应用程序（博客）](https://go.microsoft.com/fwlink/?LinkId=394977)。</span><span class="sxs-lookup"><span data-stu-id="05ac2-109">A more detailed exploration of this feature is available through this blog post series, [Building a Writeback Application with Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05ac2-110">仅对 SQL Server 关系数据库和数据市场支持写回，并且写回仅适用于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多维模型。</span><span class="sxs-lookup"><span data-stu-id="05ac2-110">Writeback is supported for SQL Server relational databases and data marts only, and only for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional models.</span></span>  
  
## <a name="how-to-write-enable-a-partition"></a><span data-ttu-id="05ac2-111">如何对分区执行写启用</span><span class="sxs-lookup"><span data-stu-id="05ac2-111">How to write-enable a partition</span></span>  
 <span data-ttu-id="05ac2-112">通过在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的多维数据集设计器中对分区本身执行写启用操作，可以对分区的度量值组执行写启用。</span><span class="sxs-lookup"><span data-stu-id="05ac2-112">You can write-enable a partition's measure groups by write-enabling the partition itself in Cube Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="05ac2-113">在多维数据集设计器中的“分区”选项卡上，右键单击一个分区，然后选择“写回设置”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="05ac2-113">In Cube Designer, in the Partitions tab, right-click a partition and choose **Writeback Settings**.</span></span>  
  
-   <span data-ttu-id="05ac2-114">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，展开“数据库”|“多维数据集”|“度量值组”，然后右键单击“写回”并选择“启用写回”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="05ac2-114">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], expand the database | cube | measure group, and then right-click **Writeback** and choose **Enable Writeback**.</span></span>  
  
 <span data-ttu-id="05ac2-115">只有使用 SUM 聚合的度量值才支持写回。</span><span class="sxs-lookup"><span data-stu-id="05ac2-115">Writeback is only supported for measures that use the SUM aggregation.</span></span> <span data-ttu-id="05ac2-116">在 AdventureWorks 示例数据库中，可以使用 Sales Targets 度量值组测试写回行为。</span><span class="sxs-lookup"><span data-stu-id="05ac2-116">In the AdventureWorks sample database, you can use the Sales Targets measure group to test writeback behaviors.</span></span>  
  
 <span data-ttu-id="05ac2-117">启用分区的写功能时，请指定用于存储写回表的表名称和数据源。</span><span class="sxs-lookup"><span data-stu-id="05ac2-117">When you write-enable a partition, you specify a table name and a data source for storing the write-back table.</span></span> <span data-ttu-id="05ac2-118">度量值组的任何后续更改都将记录在此表中。</span><span class="sxs-lookup"><span data-stu-id="05ac2-118">Any subsequent changes to the measure group are recorded in this table.</span></span>  
  
## <a name="browse-writeback-data-in-a-partition"></a><span data-ttu-id="05ac2-119">浏览分区中的写回数据</span><span class="sxs-lookup"><span data-stu-id="05ac2-119">Browse writeback data in a partition</span></span>  
 <span data-ttu-id="05ac2-120">可以在“浏览数据”对话框中浏览多维数据集的写回表的内容，在多维数据集设计器的“分区”选项卡上右键单击启用了写操作的分区即可访问该对话框。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="05ac2-120">You can browse the contents of a cube's writeback table in the **Browse Data** dialog box, which you can access by right-clicking a write-enabled partition on the **Partitions** tab in Cube Designer.</span></span>  
  
## <a name="delete-writeback-data-or-disable-writeback"></a><span data-ttu-id="05ac2-121">删除写回数据或禁用写回</span><span class="sxs-lookup"><span data-stu-id="05ac2-121">Delete writeback data or disable writeback</span></span>  
 <span data-ttu-id="05ac2-122">删除写回数据将清除写回缓存；在删除数据后，其他写回工作将立即在干净状态下执行。</span><span class="sxs-lookup"><span data-stu-id="05ac2-122">Deleting writeback data clears the writeback cache; as soon as that data is deleted, additional writeback work is performed on a clean slate.</span></span> <span data-ttu-id="05ac2-123">禁用某个多维数据集分区的写回仅仅是关闭该分区的写回。</span><span class="sxs-lookup"><span data-stu-id="05ac2-123">Disabling writeback for a cube partition simply turns off writeback for that partition.</span></span>  
  
## <a name="convert-writeback-data-to-a-partition"></a><span data-ttu-id="05ac2-124">将写回数据转换到分区</span><span class="sxs-lookup"><span data-stu-id="05ac2-124">Convert writeback data to a partition</span></span>  
 <span data-ttu-id="05ac2-125">可以将分区写回表中的数据转换为分区。</span><span class="sxs-lookup"><span data-stu-id="05ac2-125">You can convert the data in a partition's writeback table to a partition.</span></span> <span data-ttu-id="05ac2-126">此过程使得写回表成为新分区的事实数据表。</span><span class="sxs-lookup"><span data-stu-id="05ac2-126">This procedure causes the writeback table to become the new partition's fact table.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="05ac2-127">不正确地使用分区可导致多维数据集数据不准确。</span><span class="sxs-lookup"><span data-stu-id="05ac2-127">Incorrect use of partitions can result in inaccurate cube data.</span></span> <span data-ttu-id="05ac2-128">有关详细信息，请参阅 [创建和管理本地分区 (Analysis Services)](create-and-manage-a-local-partition-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="05ac2-128">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
 <span data-ttu-id="05ac2-129">将写回数据表转换为分区还会对分区禁用写功能。</span><span class="sxs-lookup"><span data-stu-id="05ac2-129">Converting the writeback data table to a partition also write-disables the partition.</span></span> <span data-ttu-id="05ac2-130">分区单元的所有无限制读/写策略和读/写权限都将禁用，而且最终用户将无法更改显示的多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="05ac2-130">All unrestricted read/write policies and read/write permissions for the partition's cells are disabled, and end users will not be able to change displayed cube data.</span></span> <span data-ttu-id="05ac2-131">（被禁用无限制读/写策略或读/写权限的最终用户仍然能够浏览多维数据集。）读取权限和有条件读取权限不受影响。</span><span class="sxs-lookup"><span data-stu-id="05ac2-131">(End users with disabled unrestricted read/write policies or disabled read/write permissions will still be able to browse the cube.) Read and read-contingent permissions are not affected.</span></span>  
  
 <span data-ttu-id="05ac2-132">若要将写回数据转换为分区，请使用“转换到分区”对话框，可以通过右键单击 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中可写入的分区的写回表来访问该对话框。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="05ac2-132">To convert writeback data to a partition, use the **Convert to Partition** dialog box, which is accessed by right-clicking the writeback table for a write-enabled partition in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="05ac2-133">您将指定分区的名称，并指定是在以后为分区设计聚合，还是在创建分区时为其设计聚合。</span><span class="sxs-lookup"><span data-stu-id="05ac2-133">You specify a name for the partition and whether to design the aggregation for the partition later or at the same time that you create it.</span></span> <span data-ttu-id="05ac2-134">若要在选择分区时创建聚合，则必须选择复制现有分区中的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="05ac2-134">To create the aggregation at the same time you choose the partition, you must choose to copy the aggregation design from an existing partition.</span></span> <span data-ttu-id="05ac2-135">这通常（但不必须）是当前的写回分区。</span><span class="sxs-lookup"><span data-stu-id="05ac2-135">This is normally, but not necessarily, the current writeback partition.</span></span> <span data-ttu-id="05ac2-136">还可以选择在创建分区时对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="05ac2-136">You can also choose to process the partition at the same time that you create it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ac2-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05ac2-137">See Also</span></span>  
 <span data-ttu-id="05ac2-138">[启用写入的分区](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="05ac2-138">[Write-Enabled Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span></span>  
 <span data-ttu-id="05ac2-139">[在 Excel 2010 中启用以单元级别写回到 OLAP 多维数据集](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span><span class="sxs-lookup"><span data-stu-id="05ac2-139">[Enabling Write-back to an OLAP Cube at Cell Level in Excel 2010](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span></span>  
 [<span data-ttu-id="05ac2-140">启用 Analysis Services 写回并使用它保护数据项</span><span class="sxs-lookup"><span data-stu-id="05ac2-140">Enabling and Securing Data Entry with Analysis Services Writeback</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=394953)  
  
  
