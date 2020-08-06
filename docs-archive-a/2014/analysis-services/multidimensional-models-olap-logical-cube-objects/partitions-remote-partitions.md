---
title: 远程分区 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32fdf05d061d4e1c1da6ec0ef9179ecd12bda172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690193"
---
# <a name="remote-partitions"></a><span data-ttu-id="21613-102">远程分区</span><span class="sxs-lookup"><span data-stu-id="21613-102">Remote Partitions</span></span>
  <span data-ttu-id="21613-103">远程分区的数据存储在 Microsoft 的不同实例上，而不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 包含分区和其父多维数据集的定义 (元数据) 的实例。</span><span class="sxs-lookup"><span data-stu-id="21613-103">The data of a remote partition is stored on a different instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] than the instance that contains the definitions (metadata) of the partition and its parent cube.</span></span> <span data-ttu-id="21613-104">远程分区在对其以及其父多维数据集进行定义的同一 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中进行管理。</span><span class="sxs-lookup"><span data-stu-id="21613-104">A remote partition is administered on the same instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube are defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21613-105">若要存储远程分区，计算机必须安装的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，并且该实例与定义该分区的实例运行相同的 Service Pack 级别。</span><span class="sxs-lookup"><span data-stu-id="21613-105">To store a remote partition, the computer must have an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installed and be running the same service pack level as the instance where the partition was defined.</span></span> <span data-ttu-id="21613-106">在更早版本的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上的远程分区不支持。</span><span class="sxs-lookup"><span data-stu-id="21613-106">Remote partitions on instances of an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are not supported.</span></span>  
  
 <span data-ttu-id="21613-107">如果度量值组中包括多个远程分区，则多维数据集的内存和 CPU 使用率会分散给度量值组内的所有分区。</span><span class="sxs-lookup"><span data-stu-id="21613-107">When remote partitions are included in a measure group, the memory and CPU utilization of the cube is distributed across all the partitions in the measure group.</span></span> <span data-ttu-id="21613-108">例如，当处理远程分区（单独处理或作为其父多维数据集的一部分加以处理）时，该分区的内存和 CPU 使用率的大部分都发生在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 远程实例中。</span><span class="sxs-lookup"><span data-stu-id="21613-108">For example, when a remote partition is processed, either alone or as part of parent cube processing, most of the memory and CPU utilization for that partition occurs on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21613-109">包含远程分区的多维数据集可以包含启用写入操作的维度，但这可能会影响该多维数据集的性能。</span><span class="sxs-lookup"><span data-stu-id="21613-109">A cube that contains remote partitions can contain write-enabled dimensions; however, this may affect performance for the cube.</span></span> <span data-ttu-id="21613-110">有关启用了写功能的维度的详细信息，请参阅[启用写功能的维度](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="21613-110">For more information about write-enabled dimensions, see [Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
## <a name="storage-modes-for-remote-partitions"></a><span data-ttu-id="21613-111">远程分区的存储模式</span><span class="sxs-lookup"><span data-stu-id="21613-111">Storage Modes for Remote Partitions</span></span>  
 <span data-ttu-id="21613-112">远程分区可以使用本地分区所使用的任何存储类型：多维 OLAP (MOLAP)、混合 OLAP (HOLAP) 或关系 OLAP (ROLAP)。</span><span class="sxs-lookup"><span data-stu-id="21613-112">Remote partitions may use any of the storage types used by local partitions: multidimensional OLAP (MOLAP), hybrid OLAP (HOLAP), or relational OLAP (ROLAP).</span></span> <span data-ttu-id="21613-113">远程分区还可以使用主动缓存。</span><span class="sxs-lookup"><span data-stu-id="21613-113">Remote partitions may also use proactive caching.</span></span> <span data-ttu-id="21613-114">根据远程分区的存储模式，下列数据将存储到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的远程实例中。</span><span class="sxs-lookup"><span data-stu-id="21613-114">Depending on the storage mode of a remote partition, the following data is stored on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21613-115">存储类型</span><span class="sxs-lookup"><span data-stu-id="21613-115">Storage Type</span></span>|<span data-ttu-id="21613-116">数据</span><span class="sxs-lookup"><span data-stu-id="21613-116">Data</span></span>|  
|<span data-ttu-id="21613-117">MOLAP</span><span class="sxs-lookup"><span data-stu-id="21613-117">MOLAP</span></span>|<span data-ttu-id="21613-118">分区的聚合和分区源数据的副本</span><span class="sxs-lookup"><span data-stu-id="21613-118">The partition's aggregations and a copy of the partition's source data</span></span>|  
|<span data-ttu-id="21613-119">HOLAP</span><span class="sxs-lookup"><span data-stu-id="21613-119">HOLAP</span></span>|<span data-ttu-id="21613-120">分区聚合</span><span class="sxs-lookup"><span data-stu-id="21613-120">The partitions aggregations</span></span>|  
|<span data-ttu-id="21613-121">ROLAP</span><span class="sxs-lookup"><span data-stu-id="21613-121">ROLAP</span></span>|<span data-ttu-id="21613-122">无分区数据</span><span class="sxs-lookup"><span data-stu-id="21613-122">No partition data</span></span>|  
  
 <span data-ttu-id="21613-123">如果度量值组包含的多个 MOLAP 或 HOLAP 分区存储在多个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例中，则多维数据集会将数据分散到这些 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的度量值组数据中。</span><span class="sxs-lookup"><span data-stu-id="21613-123">If a measure group contains multiple MOLAP or HOLAP partitions stored on multiple instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cube distributes the data in the measure group data among those instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="merging-remote-partitions"></a><span data-ttu-id="21613-124">合并远程分区</span><span class="sxs-lookup"><span data-stu-id="21613-124">Merging Remote Partitions</span></span>  
 <span data-ttu-id="21613-125">远程分区只能与存储在同一个 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 远程实例上的其他远程分区进行合并。</span><span class="sxs-lookup"><span data-stu-id="21613-125">Remote partitions can be merged only with other remote partitions that are stored on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="21613-126">有关合并分区的详细信息，请参阅[Analysis Services &#40;SSAS-多维&#41;中的合并分区](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="21613-126">For more information about merging partitions, see [Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md).</span></span>  
  
## <a name="archiving-and-restoring-remote-partitions"></a><span data-ttu-id="21613-127">存档和还原远程分区</span><span class="sxs-lookup"><span data-stu-id="21613-127">Archiving and Restoring Remote Partitions</span></span>  
 <span data-ttu-id="21613-128">存档或还原存储远程分区的数据库时，远程分区中的数据也随之一起存档或还原。</span><span class="sxs-lookup"><span data-stu-id="21613-128">Data in remote partitions can be archived or restored when the database that stores the remote partition is archived or restored.</span></span> <span data-ttu-id="21613-129">如果还原了数据库而没有还原远程分区，则必须先处理此远程分区，然后才能使用该分区中的数据。</span><span class="sxs-lookup"><span data-stu-id="21613-129">If you restore a database without restoring a remote partition, you must process the remote partition before you can use the data in the partition.</span></span> <span data-ttu-id="21613-130">有关存档和还原数据库的详细信息，请参阅[Analysis Services 数据库的备份和还原](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="21613-130">For more information about archiving and restoring databases, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21613-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21613-131">See Also</span></span>  
 <span data-ttu-id="21613-132">[创建和管理远程分区 &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="21613-132">[Create and Manage a Remote Partition &#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) </span></span>  
 [<span data-ttu-id="21613-133">处理 Analysis Services 对象</span><span class="sxs-lookup"><span data-stu-id="21613-133">Processing Analysis Services Objects</span></span>](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
