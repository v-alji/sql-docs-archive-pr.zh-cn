---
title: 向报表添加仪表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7125080d95e9c7b882df8d715cce5c6cf8aa6344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692281"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="b892c-102">向报表添加仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b892c-102">Add a Gauge to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b892c-103">如果要以可视化格式汇总数据，则可使用仪表数据区域。</span><span class="sxs-lookup"><span data-stu-id="b892c-103">When you want to summarize data in a visual format, you can use a Gauge data region.</span></span> <span data-ttu-id="b892c-104">将仪表数据区域添加到设计图面后，可以将报表数据集字段拖到仪表的数据窗格中。</span><span class="sxs-lookup"><span data-stu-id="b892c-104">After you add a Gauge data region to the design surface, you can drag report dataset fields to a data pane on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-gauge-to-your-report"></a><span data-ttu-id="b892c-105">向报表添加仪表</span><span class="sxs-lookup"><span data-stu-id="b892c-105">To add a gauge to your report</span></span>  
  
1.  <span data-ttu-id="b892c-106">创建一个报表或打开现有报表。</span><span class="sxs-lookup"><span data-stu-id="b892c-106">Create a report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="b892c-107">在“插入”选项卡上，双击“仪表”。</span><span class="sxs-lookup"><span data-stu-id="b892c-107">On the Insert tab, double-click Gauge.</span></span> <span data-ttu-id="b892c-108">**“选择仪表类型”** 对话框即会打开。</span><span class="sxs-lookup"><span data-stu-id="b892c-108">The **Select Gauge Type** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b892c-109">选择要添加的仪表类型。</span><span class="sxs-lookup"><span data-stu-id="b892c-109">Select the type of gauge you want to add.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="b892c-110">与图表不同的是，仪表只有两个类型：线性和径向。</span><span class="sxs-lookup"><span data-stu-id="b892c-110">Unlike Chart, Gauge has only two types: linear and radial.</span></span> <span data-ttu-id="b892c-111">**“选择仪表类型”** 对话框中的可用仪表是这两类仪表的模板。</span><span class="sxs-lookup"><span data-stu-id="b892c-111">The available gauges in the **Select a Gauge Type** dialog box are templates for these two types of gauges.</span></span> <span data-ttu-id="b892c-112">因此，在将仪表添加到报表后不能更改仪表类型。</span><span class="sxs-lookup"><span data-stu-id="b892c-112">For this reason, you cannot change the gauge type after you add the gauge to your report.</span></span> <span data-ttu-id="b892c-113">必须通过删除并重新添加仪表来更改仪表类型。</span><span class="sxs-lookup"><span data-stu-id="b892c-113">You must delete and re-add a gauge to change its type.</span></span>  
  
     <span data-ttu-id="b892c-114">如果报表没有数据源和数据集，则 **“数据源属性”** 对话框即会打开并引导您完成创建数据源和数据集的步骤。</span><span class="sxs-lookup"><span data-stu-id="b892c-114">If the report has no data source and dataset the **Data Source Properties** dialog box opens and takes you through the steps to create both.</span></span> <span data-ttu-id="b892c-115">有关详细信息，请参阅[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b892c-115">For more information see, [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="b892c-116">如果报表具有数据源但没有数据集，则 **“数据集属性”** 对话框即会打开并引导您完成创建一个数据集的步骤。</span><span class="sxs-lookup"><span data-stu-id="b892c-116">If the report has a data source, but no dataset the **Dataset Properties** dialog box opens and takes you through the steps to create one.</span></span> <span data-ttu-id="b892c-117">有关详细信息，请参阅 [创建共享数据集或嵌入数据集（报表生成器和 SSRS）](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b892c-117">For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="b892c-118">单击仪表以显示数据窗格。</span><span class="sxs-lookup"><span data-stu-id="b892c-118">Click the gauge to display the data pane.</span></span> <span data-ttu-id="b892c-119">默认情况下，仪表的指针和值一一对应。</span><span class="sxs-lookup"><span data-stu-id="b892c-119">By default, a gauge has one pointer corresponding to one value.</span></span> <span data-ttu-id="b892c-120">您可以添加其他指针。</span><span class="sxs-lookup"><span data-stu-id="b892c-120">You can add additional pointers.</span></span>  
  
5.  <span data-ttu-id="b892c-121">将数据集中的一个字段添加到数据字段放置区。</span><span class="sxs-lookup"><span data-stu-id="b892c-121">Add one field from the dataset to the data field drop-zone.</span></span> <span data-ttu-id="b892c-122">您只能添加一个字段。</span><span class="sxs-lookup"><span data-stu-id="b892c-122">You can add only one field.</span></span> <span data-ttu-id="b892c-123">如果要显示多个字段，必须添加其他指针，每个字段一个指针。</span><span class="sxs-lookup"><span data-stu-id="b892c-123">If you want to display multiple fields, you must add additional pointers, one for each field.</span></span>  
  
     <span data-ttu-id="b892c-124">右键单击仪表刻度，然后选择“刻度属性”  。</span><span class="sxs-lookup"><span data-stu-id="b892c-124">Right-click the gauge scale, and select **Scale Properties**.</span></span> <span data-ttu-id="b892c-125">为刻度的 **“最小值”** 和 **“最大值”** 分别键入一个值。</span><span class="sxs-lookup"><span data-stu-id="b892c-125">Type a value for the **Minimum** and **Maximum** of the scale.</span></span> <span data-ttu-id="b892c-126">有关详细信息，请参阅[设置仪表的最小值或最大值（报表生成器和 SSRS）](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b892c-126">For more information, see [Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b892c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b892c-127">See Also</span></span>  
 <span data-ttu-id="b892c-128">[嵌套数据区域（报表生成器和 SSRS）](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b892c-128">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b892c-129">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="b892c-129">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
