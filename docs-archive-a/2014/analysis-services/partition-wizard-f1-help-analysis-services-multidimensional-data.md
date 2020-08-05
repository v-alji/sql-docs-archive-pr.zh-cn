---
title: 分区向导的 F1 帮助 (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Partition Wizard
ms.assetid: 3b6d7053-aeef-4d9e-af70-f5b40256e859
author: minewiskan
ms.author: owend
ms.openlocfilehash: fa8c0e94c2b18ffbd1228752bd7cb4ad4f684acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579838"
---
# <a name="partition-wizard-f1-help-analysis-services---multidimensional-data"></a><span data-ttu-id="f6ac3-102">分区向导的 F1 帮助（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f6ac3-102">Partition Wizard F1 Help (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f6ac3-103">可以使用分区向导为多维数据集中的度量值组定义分区。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-103">You can use the Partition Wizard to define partitions for a measure group in a cube.</span></span> <span data-ttu-id="f6ac3-104">默认情况下，会对多维数据集中每个度量值组定义单个分区。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-104">By default, a single partition is defined for each measure group in a cube.</span></span> <span data-ttu-id="f6ac3-105">不过，如果是大型分区，这样将会降低访问和处理性能。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-105">Access and processing performance, however, can degrade for large partitions.</span></span> <span data-ttu-id="f6ac3-106">通过创建多个分区，使每个分区都包含度量值组的一部分数据，这样可以提高该度量值组的访问和处理性能。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-106">By creating multiple partitions, each containing a portion of the data for a measure group, you can improve the access and processing performance for that measure group.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f6ac3-107">如果将“指定源信息”\*\*\*\* 或“限制行”\*\*\*\* 页中的重复行包括在内，则创建的分区可能包含错误数据。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-107">It is possible to create partitions that may contain incorrect data by including duplicate rows in the **Specify Source Information** or **Restrict Rows** pages.</span></span>  
  
 <span data-ttu-id="f6ac3-108">分区向导可引导您完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="f6ac3-108">The Partition Wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="f6ac3-109">选择分区的数据源视图。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-109">Selecting the data source view for the partition.</span></span>  
  
-   <span data-ttu-id="f6ac3-110">为分区中所包括的记录创建筛选器。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-110">Creating a filter for the records included in the partition.</span></span>  
  
-   <span data-ttu-id="f6ac3-111">设置处理和存储位置。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-111">Setting the processing and storage locations.</span></span>  
  
-   <span data-ttu-id="f6ac3-112">命名并保存分区。</span><span class="sxs-lookup"><span data-stu-id="f6ac3-112">Naming and saving the partition.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6ac3-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="f6ac3-113">In This Section</span></span>  
  
-   [<span data-ttu-id="f6ac3-114">&#40;分区向导指定源信息&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ac3-114">Specify Source Information &#40;Partition Wizard&#41;</span></span>](specify-source-information-partition-wizard.md)  
  
-   [<span data-ttu-id="f6ac3-115">限制行 &#40;分区向导&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ac3-115">Restrict Rows &#40;Partition Wizard&#41;</span></span>](restrict-rows-partition-wizard.md)  
  
-   [<span data-ttu-id="f6ac3-116">&#40;分区向导处理和存储位置&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ac3-116">Processing and Storage Locations &#40;Partition Wizard&#41;</span></span>](processing-and-storage-locations-partition-wizard.md)  
  
-   [<span data-ttu-id="f6ac3-117">完成向导 &#40;分区向导 "&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ac3-117">Completing the Wizard &#40;Partition Wizard&#41;</span></span>](completing-the-wizard-partition-wizard.md)  
  
-   [<span data-ttu-id="f6ac3-118">"查找远程文件夹" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ac3-118">Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6ac3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6ac3-119">See Also</span></span>  
 [<span data-ttu-id="f6ac3-120">分区（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f6ac3-120">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
