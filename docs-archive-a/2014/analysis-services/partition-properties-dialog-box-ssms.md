---
title: " (SSMS) 的 \"分区属性\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionpropertiesdialog.f1
ms.assetid: dfb5b7a0-7543-4e5e-8a30-4b734606e157
author: minewiskan
ms.author: owend
ms.openlocfilehash: b606a39ef99e5313b526ab0210448e295c5f04cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682406"
---
# <a name="partition-properties-dialog-box-ssms"></a><span data-ttu-id="9f88e-102">“分区属性”对话框 (SSMS)</span><span class="sxs-lookup"><span data-stu-id="9f88e-102">Partition Properties Dialog Box (SSMS)</span></span>
  <span data-ttu-id="9f88e-103">在 SQL Server Management Studio 中，可以使用 **“分区属性”** 对话框设置 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的多维数据集的分区属性。</span><span class="sxs-lookup"><span data-stu-id="9f88e-103">Use the **Partition Properties** dialog box in SQL Server Management Studio to set the properties of a partition for a cube in an [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="9f88e-104">若要打开“分区属性”对话框，请在“对象资源管理器”中右键单击某个分区，再单击“属性”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9f88e-104">To open the **Partition Properties** dialog box, in **Object Explorer**, right-click a partition, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="9f88e-105">**“分区属性”** 对话框包含以下页：</span><span class="sxs-lookup"><span data-stu-id="9f88e-105">The **Partition Properties** dialog box contains the following pages:</span></span>  
  
## <a name="pages"></a><span data-ttu-id="9f88e-106">页数</span><span class="sxs-lookup"><span data-stu-id="9f88e-106">Pages</span></span>  
  
|<span data-ttu-id="9f88e-107">页</span><span class="sxs-lookup"><span data-stu-id="9f88e-107">Page</span></span>|<span data-ttu-id="9f88e-108">说明</span><span class="sxs-lookup"><span data-stu-id="9f88e-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9f88e-109">**选择**</span><span class="sxs-lookup"><span data-stu-id="9f88e-109">**Selection**</span></span>|<span data-ttu-id="9f88e-110">使用 **“选择”** 页，可以选择度量值组中的要显示或修改属性的分区。</span><span class="sxs-lookup"><span data-stu-id="9f88e-110">Use the **Selection** page to select the partition in the measure group for which you want to display or modify properties.</span></span> <span data-ttu-id="9f88e-111">有关此页的详细信息，请参阅[选择（“分区属性”对话框）(SSMS)](selection-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="9f88e-111">For more information about this page, see [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="9f88e-112">**常规**</span><span class="sxs-lookup"><span data-stu-id="9f88e-112">**General**</span></span>|<span data-ttu-id="9f88e-113">使用 **“常规”** 页，可以显示和修改在 **“选择”** 页中所选择的分区的常规属性。</span><span class="sxs-lookup"><span data-stu-id="9f88e-113">Use the **General** page to display and modify the general properties of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="9f88e-114">有关此页的详细信息，请参阅[常规（“分区属性”对话框）(SSMS)](general-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="9f88e-114">For more information about this page, see [General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="9f88e-115">**主动缓存**</span><span class="sxs-lookup"><span data-stu-id="9f88e-115">**Proactive Caching**</span></span>|<span data-ttu-id="9f88e-116">使用 **“主动缓存”** 页，可以显示和修改在 **“选择”** 页中所选择的分区的存储和主动缓存设置。</span><span class="sxs-lookup"><span data-stu-id="9f88e-116">Use the **Proactive Caching** page to display and modify the storage and proactive caching settings of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="9f88e-117">有关此页的详细信息，请参阅[主动缓存（“分区属性”对话框）(SSMS)](proactive-caching-partition-properties-dialog-box-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="9f88e-117">For more information about this page, see [Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="9f88e-118">**错误配置**</span><span class="sxs-lookup"><span data-stu-id="9f88e-118">**Error Configuration**</span></span>|<span data-ttu-id="9f88e-119">使用 **“错误配置”** 页，可以显示和修改用于处理在 **“选择”** 页中所选择的分区的错误配置设置。</span><span class="sxs-lookup"><span data-stu-id="9f88e-119">Use the **Error Configuration** page to display and modify the error configuration settings for processing the partition selected in the **Selection** page.</span></span> <span data-ttu-id="9f88e-120">有关此页的详细信息，请参阅[多维数据集、分区和维度处理的错误配置（SSAS - 多维）](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="9f88e-120">For more information about this page, see [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f88e-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f88e-121">See Also</span></span>  
 <span data-ttu-id="9f88e-122">[Analysis Services 多维数据 &#40;分区&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="9f88e-122">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="9f88e-123">[远程分区](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="9f88e-123">[Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span></span>  
 [<span data-ttu-id="9f88e-124">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="9f88e-124">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
