---
title: 分区处理目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579666"
---
# <a name="partition-processing-destination"></a><span data-ttu-id="78de4-102">分区处理目标</span><span class="sxs-lookup"><span data-stu-id="78de4-102">Partition Processing Destination</span></span>
  <span data-ttu-id="78de4-103">分区处理目标加载并处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 分区。</span><span class="sxs-lookup"><span data-stu-id="78de4-103">The Partition Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] partition.</span></span> <span data-ttu-id="78de4-104">有关分区的详细信息，请参阅[分区（Analysis Services - 多维数据）](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data)。</span><span class="sxs-lookup"><span data-stu-id="78de4-104">For more information about partitions, see [Partitions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="78de4-105">分区处理目标包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="78de4-105">The Partition Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="78de4-106">用于执行增量处理、完全处理或更新处理的选项。</span><span class="sxs-lookup"><span data-stu-id="78de4-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="78de4-107">用于指定处理是忽略错误，还是在发生指定数量的错误后停止的错误配置。</span><span class="sxs-lookup"><span data-stu-id="78de4-107">Error configuration, to specify whether processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="78de4-108">输入列到分区列的映射。</span><span class="sxs-lookup"><span data-stu-id="78de4-108">Mapping of input columns to partition columns.</span></span>  
  
 <span data-ttu-id="78de4-109">有关处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的详细信息，请参阅[处理选项和设置 (Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="78de4-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78de4-110">此处所述的任何不适用于 Analysis Services 表格模型。</span><span class="sxs-lookup"><span data-stu-id="78de4-110">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="78de4-111">你无法将输入列映射到表格模型的分区列。</span><span class="sxs-lookup"><span data-stu-id="78de4-111">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="78de4-112">您可以改用 [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) 处理分区。</span><span class="sxs-lookup"><span data-stu-id="78de4-112">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="configuration-of-the-partition-processing-destination"></a><span data-ttu-id="78de4-113">分区处理目标的配置</span><span class="sxs-lookup"><span data-stu-id="78de4-113">Configuration of the Partition Processing Destination</span></span>  
 <span data-ttu-id="78de4-114">分区处理目标使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或包含目标所处理的多维数据集和分区的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="78de4-114">The Partition Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the cubes and partitions the destination processes.</span></span> <span data-ttu-id="78de4-115">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="78de4-115">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="78de4-116">此目标有一个输入。</span><span class="sxs-lookup"><span data-stu-id="78de4-116">This destination has one input.</span></span> <span data-ttu-id="78de4-117">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="78de4-117">It does not support an error output.</span></span>  
  
 <span data-ttu-id="78de4-118">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="78de4-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="78de4-119">有关可在 **“分区处理目标编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="78de4-119">For more information about the properties that you can set in the Partition Processing **Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="78de4-120">分区处理目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="78de4-120">Partition Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="78de4-121">分区处理目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="78de4-121">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../partition-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="78de4-122">分区处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="78de4-122">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../partition-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="78de4-123">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="78de4-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="78de4-124">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="78de4-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="78de4-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="78de4-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="78de4-126">分区处理目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="78de4-126">Partition Processing Destination Custom Properties</span></span>](partition-processing-destination-custom-properties.md)  
  
 <span data-ttu-id="78de4-127">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="78de4-127">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
