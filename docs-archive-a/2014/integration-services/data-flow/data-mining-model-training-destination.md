---
title: 数据挖掘模型定型目标 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e101a7e374f16b12b3a5aa30a49dbecd2632f06f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587529"
---
# <a name="data-mining-model-training-destination"></a><span data-ttu-id="98eb0-102">数据挖掘模型定型目标</span><span class="sxs-lookup"><span data-stu-id="98eb0-102">Data Mining Model Training Destination</span></span>
  <span data-ttu-id="98eb0-103">数据挖掘模型定型目标将该目标接收到的数据通过数据挖掘模型算法传递，从而为数据挖掘模型定型。</span><span class="sxs-lookup"><span data-stu-id="98eb0-103">The Data Mining Model Training destination trains data mining models by passing the data that the destination receives through the data mining model algorithms.</span></span> <span data-ttu-id="98eb0-104">如果模型是在同一数据结构上生成的，则一个目标可为多个数据挖掘模型定型。</span><span class="sxs-lookup"><span data-stu-id="98eb0-104">Multiple data mining models can be trained by one destination if the models are built on the same data mining structure.</span></span> <span data-ttu-id="98eb0-105">有关详细信息，请参阅 [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) 和 [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns)。</span><span class="sxs-lookup"><span data-stu-id="98eb0-105">For more information, see [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) and [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).</span></span>  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a><span data-ttu-id="98eb0-106">数据挖掘模型定型目标的配置</span><span class="sxs-lookup"><span data-stu-id="98eb0-106">Configuration of the Data Mining Model Training Destination</span></span>  
 <span data-ttu-id="98eb0-107">如果目标结构以及在该结构上生成的模型的事例级别列具有内容类型 KEY TIME 或 KEY SEQUENCE，则输入数据必须基于此列排序。</span><span class="sxs-lookup"><span data-stu-id="98eb0-107">If a case level column of the target structure and the models built on the structure has the content type KEY TIME or KEY SEQUENCE, the input data must be sorted on that column.</span></span> <span data-ttu-id="98eb0-108">例如，用 Microsoft 时序算法生成的模型使用内容类型 KEY TIME。</span><span class="sxs-lookup"><span data-stu-id="98eb0-108">For example, models built using the Microsoft Time Series algorithm use the content type KEY TIME.</span></span> <span data-ttu-id="98eb0-109">如果输入数据未排序，则对模型的处理可能失败。</span><span class="sxs-lookup"><span data-stu-id="98eb0-109">If input data is not sorted, the processing of the model may fail.</span></span> <span data-ttu-id="98eb0-110">如果数据需要排序，您可以事先在数据流中使用排序转换对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="98eb0-110">If the data requires sorting, you can use a Sort transformation earlier in the data flow to sort the data.</span></span> <span data-ttu-id="98eb0-111">此要求不适用于具有 KEY 内容类型的列。</span><span class="sxs-lookup"><span data-stu-id="98eb0-111">This requirement does not apply to columns with the KEY content type.</span></span> <span data-ttu-id="98eb0-112">有关详细信息，请参阅[内容类型（数据挖掘）](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining)和[排序转换](transformations/sort-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="98eb0-112">For more information, see [Content Types &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) and [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98eb0-113">数据挖掘模型定型目标的输入必须经过排序。</span><span class="sxs-lookup"><span data-stu-id="98eb0-113">The input to the Data Mining Model training destination must be sorted.</span></span> <span data-ttu-id="98eb0-114">若要对数据进行排序，您可以将数据挖掘模型定型目标的排序目标上游包括到该数据流中。</span><span class="sxs-lookup"><span data-stu-id="98eb0-114">To sort the data, you can include a Sort destination upstream from the Data Mining Model Training destination in the data flow.</span></span> <span data-ttu-id="98eb0-115">有关详细信息，请参阅 [Sort Transformation](transformations/sort-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="98eb0-115">For more information, see [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
 <span data-ttu-id="98eb0-116">此目标有一个输入，没有输出。</span><span class="sxs-lookup"><span data-stu-id="98eb0-116">This destination has one input and no output.</span></span>  
  
 <span data-ttu-id="98eb0-117">数据挖掘模型定型目标使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器连接到包含挖掘结构以及目标为其定型的挖掘模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="98eb0-117">The Data Mining Model Training destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models that the destination trains.</span></span> <span data-ttu-id="98eb0-118">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="98eb0-118">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="98eb0-119">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="98eb0-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="98eb0-120">有关可以在 **“数据挖掘模型定型编辑器”** 对话框中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="98eb0-120">For more information about the properties that you can set in the **Data Mining Model Training Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="98eb0-121">数据挖掘模型定型编辑器（“连接”选项卡）</span><span class="sxs-lookup"><span data-stu-id="98eb0-121">Data Mining Model Training Editor &#40;Connection Tab&#41;</span></span>](../data-mining-model-training-editor-connection-tab.md)  
  
-   [<span data-ttu-id="98eb0-122">数据挖掘模型定型编辑器（“列”选项卡）</span><span class="sxs-lookup"><span data-stu-id="98eb0-122">Data Mining Model Training Editor &#40;Columns Tab&#41;</span></span>](../data-mining-model-training-editor-columns-tab.md)  
  
 <span data-ttu-id="98eb0-123">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="98eb0-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="98eb0-124">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="98eb0-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="98eb0-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="98eb0-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="98eb0-126">数据挖掘模型定型目标自定义属性</span><span class="sxs-lookup"><span data-stu-id="98eb0-126">Data Mining Model Training Destination Custom Properties</span></span>](data-mining-model-training-destination-custom-properties.md)  
  
 <span data-ttu-id="98eb0-127">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="98eb0-127">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
