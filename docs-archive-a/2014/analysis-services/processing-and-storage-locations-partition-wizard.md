---
title: " (分区向导) 的处理和存储位置 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00ab88bac184f57bd2b4dcfdb8d00909a85ece4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693514"
---
# <a name="processing-and-storage-locations-partition-wizard"></a><span data-ttu-id="a0e30-102">处理位置和存储位置（分区向导）</span><span class="sxs-lookup"><span data-stu-id="a0e30-102">Processing and Storage Locations (Partition Wizard)</span></span>
  <span data-ttu-id="a0e30-103">可以使用 **“处理位置和存储位置”** 页，指定拥有分区的多维数据集的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例以及存储分区数据的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a0e30-103">Use the **Processing and Storage Locations** page to specify the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance of the cube that owns the partition, as well as the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that stores the data for the partition.</span></span> <span data-ttu-id="a0e30-104">通过指定远程 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例或指定默认存储位置之外的其他存储位置，可以将分区定义为远程分区。</span><span class="sxs-lookup"><span data-stu-id="a0e30-104">You can define a partition as a remote partition by specifying either a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a storage location other than the default storage location.</span></span> <span data-ttu-id="a0e30-105">有关远程分区的详细信息，请参阅 [远程分区](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e30-105">For more information about remote partitions, see [Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).</span></span>  
  
## <a name="processing-location-options"></a><span data-ttu-id="a0e30-106">处理位置选项</span><span class="sxs-lookup"><span data-stu-id="a0e30-106">Processing location Options</span></span>  
 <span data-ttu-id="a0e30-107">**当前服务器实例**</span><span class="sxs-lookup"><span data-stu-id="a0e30-107">**Current server instance**</span></span>  
 <span data-ttu-id="a0e30-108">将当前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例设置为负责处理该分区。</span><span class="sxs-lookup"><span data-stu-id="a0e30-108">Makes the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
 <span data-ttu-id="a0e30-109">**远程 Analysis Services 数据源**</span><span class="sxs-lookup"><span data-stu-id="a0e30-109">**Remote Analysis Services data source**</span></span>  
 <span data-ttu-id="a0e30-110">设置一个远程 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例来负责处理此分区。</span><span class="sxs-lookup"><span data-stu-id="a0e30-110">Makes a remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing this partition.</span></span>  
  
 <span data-ttu-id="a0e30-111">从下拉列表中，选择代表负责处理该分区的远程 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的数据源。</span><span class="sxs-lookup"><span data-stu-id="a0e30-111">From the dropdown list, select the data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that will be responsible for processing the partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0e30-112">如果在所选择的数据源中为 `Initial Catalog` 连接字符串属性设置的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库无效，或者在 `Initial Catalog` 连接字符串属性中指定的数据库不支持远程分区（换句话说，为指定数据库的 `MasterDatasourceID` 属性设置的值无效），则将发生错误。</span><span class="sxs-lookup"><span data-stu-id="a0e30-112">An error occurs if you select a data source in which the `Initial Catalog` connection string property is not set to a valid [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, or if the database specified in the `Initial Catalog` connection string property does not support remote partitions (in other words, the `MasterDatasourceID` property of the specified database is not set to a valid value).</span></span>  
  
 <span data-ttu-id="a0e30-113">**新建**</span><span class="sxs-lookup"><span data-stu-id="a0e30-113">**New**</span></span>  
 <span data-ttu-id="a0e30-114">创建一个新的数据源，代表负责处理该分区的远程 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a0e30-114">Creates a new data source representing the remote [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance responsible for processing the partition.</span></span>  
  
## <a name="storage-location-options"></a><span data-ttu-id="a0e30-115">存储位置选项</span><span class="sxs-lookup"><span data-stu-id="a0e30-115">Storage location Options</span></span>  
 <span data-ttu-id="a0e30-116">**默认服务器位置**</span><span class="sxs-lookup"><span data-stu-id="a0e30-116">**Default server location**</span></span>  
 <span data-ttu-id="a0e30-117">将当前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的数据文件夹设置为分区的聚合和索引数据的存储位置。</span><span class="sxs-lookup"><span data-stu-id="a0e30-117">Makes the data folder of the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="a0e30-118">**指定的文件夹**</span><span class="sxs-lookup"><span data-stu-id="a0e30-118">**Specified folder**</span></span>  
 <span data-ttu-id="a0e30-119">指定分区的聚合和索引数据的存储位置。</span><span class="sxs-lookup"><span data-stu-id="a0e30-119">Specifies the storage location of the aggregation and indexing data for the partition.</span></span>  
  
 <span data-ttu-id="a0e30-120">**...**</span><span class="sxs-lookup"><span data-stu-id="a0e30-120">**...**</span></span>  
 <span data-ttu-id="a0e30-121">显示“查找远程文件夹”\*\*\*\* 对话框，在该对话框中可以为“指定的文件夹”\*\*\*\* 选择文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0e30-121">Displays the **Browse for Remote Folder** dialog box in which you can select a folder for **Specified folder**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e30-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0e30-122">See Also</span></span>  
 <span data-ttu-id="a0e30-123">[分区向导的 F1 帮助 &#40;Analysis Services 多维数据&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a0e30-123">[Partition Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a0e30-124">[Analysis Services 多维数据 &#40;分区&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a0e30-124">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a0e30-125">"查找远程文件夹" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="a0e30-125">Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  
