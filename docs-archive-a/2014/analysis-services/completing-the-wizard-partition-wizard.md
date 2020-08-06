---
title: 完成向导 (分区向导) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60be28170e8f8ec156d1c37149ddbc04b64bf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579240"
---
# <a name="completing-the-wizard-partition-wizard"></a><span data-ttu-id="45fd3-102">完成向导（分区向导）</span><span class="sxs-lookup"><span data-stu-id="45fd3-102">Completing the Wizard (Partition Wizard)</span></span>
  <span data-ttu-id="45fd3-103">可以使用 **“完成向导”** 页，对分区进行命名，为分区定义聚合设计，以及根据需要在完成分区向导后部署并处理分区。</span><span class="sxs-lookup"><span data-stu-id="45fd3-103">Use the **Completing the Wizard** page to name the partition, define the aggregation design for your partition, and optionally deploy and process the partition after completing the Partition Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="45fd3-104">选项</span><span class="sxs-lookup"><span data-stu-id="45fd3-104">Options</span></span>  
 <span data-ttu-id="45fd3-105">**名称**</span><span class="sxs-lookup"><span data-stu-id="45fd3-105">**Name**</span></span>  
 <span data-ttu-id="45fd3-106">为新分区键入名称。</span><span class="sxs-lookup"><span data-stu-id="45fd3-106">Type the name for the new partition.</span></span> <span data-ttu-id="45fd3-107">如果使用多个表，请输入用于同表名进行组合的前缀以创建各个分区名称。</span><span class="sxs-lookup"><span data-stu-id="45fd3-107">If you are working with multiple tables, enter the prefix that will be combined with the table name to create each partition name.</span></span>  
  
 <span data-ttu-id="45fd3-108">**聚合选项**</span><span class="sxs-lookup"><span data-stu-id="45fd3-108">**Aggregation options**</span></span>  
 <span data-ttu-id="45fd3-109">为分区指定聚合选项。</span><span class="sxs-lookup"><span data-stu-id="45fd3-109">Specifies the aggregation option for the partition.</span></span>  
  
 <span data-ttu-id="45fd3-110">下表列出了可用的聚合选项：</span><span class="sxs-lookup"><span data-stu-id="45fd3-110">The following table lists the aggregation options that are available.</span></span>  
  
|<span data-ttu-id="45fd3-111">选项</span><span class="sxs-lookup"><span data-stu-id="45fd3-111">Option</span></span>|<span data-ttu-id="45fd3-112">说明</span><span class="sxs-lookup"><span data-stu-id="45fd3-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="45fd3-113">**立即为分区设计聚合**</span><span class="sxs-lookup"><span data-stu-id="45fd3-113">**Design aggregations for the partition now**</span></span>|<span data-ttu-id="45fd3-114">在分区向导创建新分区之后，为新分区设计聚合。</span><span class="sxs-lookup"><span data-stu-id="45fd3-114">Designs aggregations for the new partition after the Partition Wizard creates the new partition.</span></span> <span data-ttu-id="45fd3-115">如果选择此选项，则在分区向导中单击 **“完成”** 后将启动聚合设计向导。</span><span class="sxs-lookup"><span data-stu-id="45fd3-115">Selecting this option starts the Aggregation Design Wizard after you click **Finish** in the Partition Wizard.</span></span> <span data-ttu-id="45fd3-116">有关聚合设计向导的详细信息，请参阅 [聚合设计向导 F1 帮助](aggregation-design-wizard-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="45fd3-116">For more information about the Aggregation Design Wizard, see [Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="45fd3-117">**稍后设计聚合**</span><span class="sxs-lookup"><span data-stu-id="45fd3-117">**Design the aggregations later**</span></span>|<span data-ttu-id="45fd3-118">此时只创建分区，而不设计聚合。</span><span class="sxs-lookup"><span data-stu-id="45fd3-118">Creates the partition without designing aggregations at this time.</span></span>|  
|<span data-ttu-id="45fd3-119">**从现有分区复制聚合设计**</span><span class="sxs-lookup"><span data-stu-id="45fd3-119">**Copy the aggregation design from an existing partition**</span></span>|<span data-ttu-id="45fd3-120">将聚合设计从度量值组中的现有分区复制到新分区。</span><span class="sxs-lookup"><span data-stu-id="45fd3-120">Copies the aggregation design from an existing partition in the measure group to the new partition.</span></span> <span data-ttu-id="45fd3-121">单击此项后， **“复制来源”** 选项即会可用。</span><span class="sxs-lookup"><span data-stu-id="45fd3-121">Clicking this option makes the **Copy from** option available.</span></span> <span data-ttu-id="45fd3-122">使用 **“复制来源”** 选项可以选择要从中复制聚合设计的分区。</span><span class="sxs-lookup"><span data-stu-id="45fd3-122">Use the **Copy from** option to select the partition from which to copy the aggregation design.</span></span><br /><br /> <span data-ttu-id="45fd3-123">请注意，将来可以合并的分区必须具有相同的表结构和聚合设计。</span><span class="sxs-lookup"><span data-stu-id="45fd3-123">Note that partitions that may be merged in the future must have the same table structure and aggregation design.</span></span> <span data-ttu-id="45fd3-124">若要将新分区与度量值组中的现有分区合并，则应将现有分区的聚合设计复制到新分区中。</span><span class="sxs-lookup"><span data-stu-id="45fd3-124">If you might merge the new partition with an existing partition in the measure group, you should copy the aggregation design of the existing partition into the new partition.</span></span>|  
  
 <span data-ttu-id="45fd3-125">**立即部署并处理**</span><span class="sxs-lookup"><span data-stu-id="45fd3-125">**Deploy and Process Now**</span></span>  
 <span data-ttu-id="45fd3-126">向“处理位置和存储位置”\*\*\*\* 页上指定的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例部署分区并对分区进行处理。</span><span class="sxs-lookup"><span data-stu-id="45fd3-126">Deploys and processes the partition to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance specified on the **Processing and Storage Locations** page.</span></span> <span data-ttu-id="45fd3-127">在此页上单击 **“完成”** 之后，向导将部署并处理分区。</span><span class="sxs-lookup"><span data-stu-id="45fd3-127">The wizard deploys and processes the partition after you click **Finish** on this page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fd3-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45fd3-128">See Also</span></span>  
 [<span data-ttu-id="45fd3-129">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="45fd3-129">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
