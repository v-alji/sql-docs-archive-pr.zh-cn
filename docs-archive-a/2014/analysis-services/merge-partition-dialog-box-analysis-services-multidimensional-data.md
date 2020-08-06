---
title: Analysis Services 多维数据) 的 "合并分区" 对话框 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589939"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="1b83d-102">“合并分区”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="1b83d-102">Merge Partition Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="1b83d-103">可以使用 **SQL Server Management Studio** 中的 **“合并分区”** 对话框合并多维数据中的度量值组的分区。</span><span class="sxs-lookup"><span data-stu-id="1b83d-103">Use the **Merge Partition** dialog box in **SQL Server Management Studio** to merge partitions for a measure group in a cube.</span></span> <span data-ttu-id="1b83d-104">通过在**对象资源管理器**中右键单击分区文件夹或某个分区并从上下文菜单中选择“合并分区”\*\*\*\*，可以显示“合并分区”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="1b83d-104">You can display the **Merge Partition** dialog box by right-clicking the Partitions folder or a partition in **Object Explorer** and selecting **Merge Partitions** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b83d-105">选项</span><span class="sxs-lookup"><span data-stu-id="1b83d-105">Options</span></span>  
 <span data-ttu-id="1b83d-106">**Server**</span><span class="sxs-lookup"><span data-stu-id="1b83d-106">**Server**</span></span>  
 <span data-ttu-id="1b83d-107">选择包含目标分区的 Analysis Services 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="1b83d-107">Select the name of the Analysis Services instance that contains the target partition.</span></span>  
  
 <span data-ttu-id="1b83d-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="1b83d-108">**Name**</span></span>  
 <span data-ttu-id="1b83d-109">选择要用作目标分区的现有分区的名称。</span><span class="sxs-lookup"><span data-stu-id="1b83d-109">Select the name of an existing partition to use as the target partition.</span></span>  
  
 <span data-ttu-id="1b83d-110">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="1b83d-110">**Folder**</span></span>  
 <span data-ttu-id="1b83d-111">如果在“名称”中选择的分区不使用 Analysis Services 实例的默认文件夹，则显示包含目标分区的文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="1b83d-111">Displays the name of the folder that contains the target partition, if the partition selected in Name does not use the default folder for the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="1b83d-112">**源分区**</span><span class="sxs-lookup"><span data-stu-id="1b83d-112">**Source Partitions**</span></span>  
 <span data-ttu-id="1b83d-113">显示包含可以合并到目标分区中的源分区的网格。</span><span class="sxs-lookup"><span data-stu-id="1b83d-113">Displays a grind containing the source partitions that can be merged into the target partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b83d-114">只能合并同一度量值组中共享相同聚合设计的分区。</span><span class="sxs-lookup"><span data-stu-id="1b83d-114">Only partitions in the same measure group that share the same aggregation design can be merged.</span></span>  
  
 <span data-ttu-id="1b83d-115">该网格包含以下列：</span><span class="sxs-lookup"><span data-stu-id="1b83d-115">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="1b83d-116">列</span><span class="sxs-lookup"><span data-stu-id="1b83d-116">Column</span></span>|<span data-ttu-id="1b83d-117">说明</span><span class="sxs-lookup"><span data-stu-id="1b83d-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1b83d-118">**合并**</span><span class="sxs-lookup"><span data-stu-id="1b83d-118">**Merge**</span></span>|<span data-ttu-id="1b83d-119">选择此选项可以将源分区合并到目标分区中。</span><span class="sxs-lookup"><span data-stu-id="1b83d-119">Select to merge the source partition into the target partition.</span></span>|  
|<span data-ttu-id="1b83d-120">**分区名称**</span><span class="sxs-lookup"><span data-stu-id="1b83d-120">**Partition Name**</span></span>|<span data-ttu-id="1b83d-121">显示源分区的名称。</span><span class="sxs-lookup"><span data-stu-id="1b83d-121">Displays the name of the source partition.</span></span>|  
|<span data-ttu-id="1b83d-122">**上次处理时间**</span><span class="sxs-lookup"><span data-stu-id="1b83d-122">**Last Processed**</span></span>|<span data-ttu-id="1b83d-123">显示上次处理源分区的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="1b83d-123">Displays the date and time at which the source partition was last processed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b83d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b83d-124">See Also</span></span>  
 <span data-ttu-id="1b83d-125">[Analysis Services 多维数据 &#40;分区&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1b83d-125">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="1b83d-126">在 Analysis Services 中合并分区（SSAS - 多维）</span><span class="sxs-lookup"><span data-stu-id="1b83d-126">Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;</span></span>](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
