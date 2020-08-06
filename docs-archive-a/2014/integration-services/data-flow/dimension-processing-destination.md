---
title: 维度处理目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61cde87ac4fa5fcb1352491d787674447dd404b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579686"
---
# <a name="dimension-processing-destination"></a><span data-ttu-id="35af9-102">维度处理目标</span><span class="sxs-lookup"><span data-stu-id="35af9-102">Dimension Processing Destination</span></span>
  <span data-ttu-id="35af9-103">维度处理目标加载并处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 维度。</span><span class="sxs-lookup"><span data-stu-id="35af9-103">The Dimension Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimension.</span></span> <span data-ttu-id="35af9-104">有关维度的详细信息，请参阅[维度（Analysis Services - 多维数据）](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data)。</span><span class="sxs-lookup"><span data-stu-id="35af9-104">For more information about dimensions, see [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="35af9-105">维度处理目标包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="35af9-105">The Dimension Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="35af9-106">用于执行增量处理、完全处理或更新处理的选项。</span><span class="sxs-lookup"><span data-stu-id="35af9-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="35af9-107">用于指定维度处理是忽略错误还是在发生指定数量的错误后停止的错误配置。</span><span class="sxs-lookup"><span data-stu-id="35af9-107">Error configuration, to specify whether dimension processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="35af9-108">输入列到维度表中列的映射。</span><span class="sxs-lookup"><span data-stu-id="35af9-108">Mapping of input columns to columns in dimension tables.</span></span>  
  
 <span data-ttu-id="35af9-109">有关处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象的详细信息，请参阅[处理选项和设置 (Analysis Services)](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="35af9-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
## <a name="configuration-of-the-dimension-processing-destination"></a><span data-ttu-id="35af9-110">维度处理目标的配置</span><span class="sxs-lookup"><span data-stu-id="35af9-110">Configuration of the Dimension Processing Destination</span></span>  
 <span data-ttu-id="35af9-111">维度处理目标使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器连接到包含目标所处理的维度的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="35af9-111">The Dimension Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the dimensions the destination processes.</span></span> <span data-ttu-id="35af9-112">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="35af9-112">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="35af9-113">此目标有一个输入。</span><span class="sxs-lookup"><span data-stu-id="35af9-113">This destination has one input.</span></span> <span data-ttu-id="35af9-114">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="35af9-114">It does not support an error output.</span></span>  
  
 <span data-ttu-id="35af9-115">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="35af9-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="35af9-116">有关可在 **“维度处理目标编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="35af9-116">For more information about the properties that you can set in the **Dimension Processing Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="35af9-117">维度处理目标编辑器（“连接管理器”页）</span><span class="sxs-lookup"><span data-stu-id="35af9-117">Dimension Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="35af9-118">维度处理目标编辑器（“映射”页）</span><span class="sxs-lookup"><span data-stu-id="35af9-118">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../dimension-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="35af9-119">维度处理目标编辑器（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="35af9-119">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../dimension-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="35af9-120">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="35af9-120">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="35af9-121">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="35af9-121">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="35af9-122">Common Properties</span><span class="sxs-lookup"><span data-stu-id="35af9-122">Common Properties</span></span>](../common-properties.md)  
  
 <span data-ttu-id="35af9-123">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="35af9-123">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35af9-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="35af9-124">See Also</span></span>  
 <span data-ttu-id="35af9-125">[数据流](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="35af9-125">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="35af9-126">Integration Services 转换</span><span class="sxs-lookup"><span data-stu-id="35af9-126">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
