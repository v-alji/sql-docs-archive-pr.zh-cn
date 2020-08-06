---
title: "\"增量更新\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590416"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="225db-102">“增量更新”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="225db-102">Incremental Update Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="225db-103">可以使用 **和** 中的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] “增量更新” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框，定义在增量更新度量值组和分区时使用的设置。</span><span class="sxs-lookup"><span data-stu-id="225db-103">Use the **Incremental Update** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to define the settings that are used when measure groups and partitions are incrementally updated.</span></span> <span data-ttu-id="225db-104">通过在 **“处理”** 对话框的 **“对象列表”** 网格的 **“设置”** 列中单击 **“配置”** ，可以显示 **“增量更新”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="225db-104">You can display the **Incremental Update** dialog box by clicking **Configure** in the **Settings** column of the **Object list** grid in the **Process** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="225db-105">选项</span><span class="sxs-lookup"><span data-stu-id="225db-105">Options</span></span>  
  
|<span data-ttu-id="225db-106">术语</span><span class="sxs-lookup"><span data-stu-id="225db-106">Term</span></span>|<span data-ttu-id="225db-107">定义</span><span class="sxs-lookup"><span data-stu-id="225db-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="225db-108">**度量值组**</span><span class="sxs-lookup"><span data-stu-id="225db-108">**Measure Group**</span></span>|<span data-ttu-id="225db-109">选择要增量更新的度量值组。</span><span class="sxs-lookup"><span data-stu-id="225db-109">Select the measure group to incrementally update.</span></span><br /><br /> <span data-ttu-id="225db-110">注意：只有在增量更新多维数据集时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-110">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="225db-111">如果是增量更新度量值组或分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-111">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="225db-112">分区</span><span class="sxs-lookup"><span data-stu-id="225db-112">**Partition**</span></span>|<span data-ttu-id="225db-113">选择要更新的分区。</span><span class="sxs-lookup"><span data-stu-id="225db-113">Select the partition to update.</span></span><br /><br /> <span data-ttu-id="225db-114">注意：只有在增量更新多维数据集时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-114">Note: This option is enabled only if you are incrementally updating a cube.</span></span> <span data-ttu-id="225db-115">如果是增量更新度量值组或分区，则将禁用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-115">If you are incrementally updating a measure group or partition, this option is disabled.</span></span>|  
|<span data-ttu-id="225db-116">**表**</span><span class="sxs-lookup"><span data-stu-id="225db-116">**Table**</span></span>|<span data-ttu-id="225db-117">单击此项可以更新表中的对象。</span><span class="sxs-lookup"><span data-stu-id="225db-117">Click to update the object from a table.</span></span>|  
|<span data-ttu-id="225db-118">**数据源或视图**</span><span class="sxs-lookup"><span data-stu-id="225db-118">**Data source or view**</span></span>|<span data-ttu-id="225db-119">选择源表所在的数据源或数据源视图。</span><span class="sxs-lookup"><span data-stu-id="225db-119">Select the data source or data source view in which the source table is located.</span></span><br /><br /> <span data-ttu-id="225db-120">注意：只有在选择了“表” \*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-120">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="225db-121">**表架构和名称**</span><span class="sxs-lookup"><span data-stu-id="225db-121">**Table schema and name**</span></span>|<span data-ttu-id="225db-122">选择用于检索数据以增量更新多维数据集、度量值组或分区的源表。</span><span class="sxs-lookup"><span data-stu-id="225db-122">Select the source table used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="225db-123">注意：只有在选择了“表” \*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-123">Note: This option is enabled only if **Table** is selected.</span></span>|  
|<span data-ttu-id="225db-124">**查询**</span><span class="sxs-lookup"><span data-stu-id="225db-124">**Query**</span></span>|<span data-ttu-id="225db-125">单击此项可以更新查询中的对象。</span><span class="sxs-lookup"><span data-stu-id="225db-125">Click to update the object from a query.</span></span>|  
|<span data-ttu-id="225db-126">**数据源**</span><span class="sxs-lookup"><span data-stu-id="225db-126">**Data Source**</span></span>|<span data-ttu-id="225db-127">选择要查询的表所在的数据源。</span><span class="sxs-lookup"><span data-stu-id="225db-127">Select the data source in which the tables to be queried are located.</span></span><br /><br /> <span data-ttu-id="225db-128">注意：只有在选择了“查询” \*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-128">Note: This option is enabled only if **Query** is selected.</span></span>|  
|<span data-ttu-id="225db-129">**查询文本**</span><span class="sxs-lookup"><span data-stu-id="225db-129">**Text of the query**</span></span>|<span data-ttu-id="225db-130">键入用于检索数据以增量更新多维数据集、度量值组或分区的查询文本。</span><span class="sxs-lookup"><span data-stu-id="225db-130">Type the text of the query used to retrieve data for incrementally updating the cube, measure group, or partition.</span></span><br /><br /> <span data-ttu-id="225db-131">注意：只有在选择了“查询” \*\*\*\* 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="225db-131">Note: This option is enabled only if **Query** is selected.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="225db-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="225db-132">See Also</span></span>  
 <span data-ttu-id="225db-133">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="225db-133">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="225db-134">"处理" 对话框 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="225db-134">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
