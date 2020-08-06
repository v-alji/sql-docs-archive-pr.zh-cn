---
title: "\"分配聚合设计\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc4f7a0847373360a79ddda366ad7aa3f02c5de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579412"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6110f-102">“分配聚合设计”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="6110f-102">Assign Aggregation Design Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6110f-103">可以使用 **中的** “分配聚合设计” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框，为一个或多个目标分区分配聚合设计。</span><span class="sxs-lookup"><span data-stu-id="6110f-103">Use the **Assign Aggregation Design** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to assign aggregation designs to one or more destination partitions.</span></span> <span data-ttu-id="6110f-104">你可以通过在**对象资源管理器**中右键单击某个分区或聚合设计，然后选择“分配聚合设计”，来显示“分配聚合设计”对话框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6110f-104">You can display the **Assign Aggregation Design** dialog box by right-clicking a partition or aggregation design in **Object Explorer** and selecting **Assign Aggregation Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6110f-105">选项</span><span class="sxs-lookup"><span data-stu-id="6110f-105">Options</span></span>  
  
|<span data-ttu-id="6110f-106">术语</span><span class="sxs-lookup"><span data-stu-id="6110f-106">Term</span></span>|<span data-ttu-id="6110f-107">定义</span><span class="sxs-lookup"><span data-stu-id="6110f-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="6110f-108">**聚合设计**</span><span class="sxs-lookup"><span data-stu-id="6110f-108">**Aggregation designs**</span></span>|<span data-ttu-id="6110f-109">选择要分配到一个或多个目标分区的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="6110f-109">Select an aggregation design to assign to one or more destination partitions.</span></span>|  
|<span data-ttu-id="6110f-110">**目标分区**</span><span class="sxs-lookup"><span data-stu-id="6110f-110">**Destination partitions**</span></span>|<span data-ttu-id="6110f-111">选择要向其分配聚合设计的分区。</span><span class="sxs-lookup"><span data-stu-id="6110f-111">Select the partitions to which to assign the aggregation design.</span></span> <span data-ttu-id="6110f-112">以下网格用于指定目标分区：</span><span class="sxs-lookup"><span data-stu-id="6110f-112">The following grid is used to specify destination partitions:</span></span><br /><br /> <span data-ttu-id="6110f-113">\<check box>：选中或清除列标题中的复选框，以包括或排除所有列出的分区作为目标分区。</span><span class="sxs-lookup"><span data-stu-id="6110f-113">\<check box>: Select or clear the check box in the column header to include or exclude all listed partitions as destination partitions.</span></span> <span data-ttu-id="6110f-114">选中或清除分区旁的复选框，可以包括或排除该分区作为目标分区。</span><span class="sxs-lookup"><span data-stu-id="6110f-114">Select or clear a check box next to a partition to include or exclude that partition as a destination partition.</span></span><br /><br /> <span data-ttu-id="6110f-115">**分区**：显示分区的名称。</span><span class="sxs-lookup"><span data-stu-id="6110f-115">**Partition**: Displays the name of the partition.</span></span><br /><br /> <span data-ttu-id="6110f-116">**源**：显示分区的源表或查询。</span><span class="sxs-lookup"><span data-stu-id="6110f-116">**Source**: Displays the source table or query for the partition.</span></span><br /><br /> <span data-ttu-id="6110f-117">**聚合设计**：显示分区的现有聚合设计的名称。</span><span class="sxs-lookup"><span data-stu-id="6110f-117">**Aggregation Design**: Displays the name of the existing aggregation design for the partition.</span></span>|  
|<span data-ttu-id="6110f-118">**隐藏包含聚合设计的分区**</span><span class="sxs-lookup"><span data-stu-id="6110f-118">**Hide partitions with aggregation designs**</span></span>|<span data-ttu-id="6110f-119">选择以仅显示未分配聚合设计的分区。</span><span class="sxs-lookup"><span data-stu-id="6110f-119">Select to show only the partitions that do not have aggregation designs assigned to them.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6110f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6110f-120">See Also</span></span>  
 [<span data-ttu-id="6110f-121">聚合和聚合设计</span><span class="sxs-lookup"><span data-stu-id="6110f-121">Aggregations and Aggregation Designs</span></span>](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
