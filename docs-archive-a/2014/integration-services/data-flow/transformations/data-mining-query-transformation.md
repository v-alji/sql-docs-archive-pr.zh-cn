---
title: 数据挖掘查询转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 278fdc3b1abd38b63f01e967e28d11983a09e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577764"
---
# <a name="data-mining-query-transformation"></a><span data-ttu-id="f63ae-102">数据挖掘查询转换</span><span class="sxs-lookup"><span data-stu-id="f63ae-102">Data Mining Query Transformation</span></span>
  <span data-ttu-id="f63ae-103">数据挖掘查询转换针对数据挖掘模型执行预测查询。</span><span class="sxs-lookup"><span data-stu-id="f63ae-103">The Data Mining Query transformation performs prediction queries against data mining models.</span></span> <span data-ttu-id="f63ae-104">此转换包含用于创建数据挖掘扩展 (DMX) 查询的查询生成器。</span><span class="sxs-lookup"><span data-stu-id="f63ae-104">This transformation contains a query builder for creating Data Mining Extensions (DMX) queries.</span></span> <span data-ttu-id="f63ae-105">使用查询生成器可创建自定义语句来使用 DMX 语言针对现有挖掘模型计算转换输入数据。</span><span class="sxs-lookup"><span data-stu-id="f63ae-105">The query builder lets you create custom statements for evaluating the transformation input data against an existing mining model using the DMX language.</span></span> <span data-ttu-id="f63ae-106">有关详细信息，请参阅[数据挖掘扩展插件 (DMX) 参考](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="f63ae-106">For more information, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="f63ae-107">如果模型是使用同一数据挖掘结构构建的，那么一个转换可以执行多个预测查询。</span><span class="sxs-lookup"><span data-stu-id="f63ae-107">One transformation can execute multiple prediction queries if the models are built on the same data mining structure.</span></span> <span data-ttu-id="f63ae-108">有关详细信息，请参阅[数据挖掘查询接口](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)。</span><span class="sxs-lookup"><span data-stu-id="f63ae-108">For more information, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a><span data-ttu-id="f63ae-109">数据挖掘查询转换的配置</span><span class="sxs-lookup"><span data-stu-id="f63ae-109">Configuration of the Data Mining Query Transformation</span></span>  
 <span data-ttu-id="f63ae-110">数据挖掘查询转换使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 连接管理器来连接包含挖掘结构和挖掘模型的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f63ae-110">The Data Mining Query transformation uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models.</span></span> <span data-ttu-id="f63ae-111">有关详细信息，请参阅 [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f63ae-111">For more information, see [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="f63ae-112">此转换有一个输入和一个输出。</span><span class="sxs-lookup"><span data-stu-id="f63ae-112">This transformation has one input and one output.</span></span> <span data-ttu-id="f63ae-113">它不支持错误输出。</span><span class="sxs-lookup"><span data-stu-id="f63ae-113">It does not support an error output.</span></span>  
  
 <span data-ttu-id="f63ae-114">可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="f63ae-114">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f63ae-115">有关可在 **“数据挖掘查询转换编辑器”** 对话框中设置的属性的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="f63ae-115">For more information about the properties that you can set in the **Data Mining Query Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f63ae-116">数据挖掘查询转换编辑器（“挖掘模型”选项卡）</span><span class="sxs-lookup"><span data-stu-id="f63ae-116">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="f63ae-117">数据挖掘查询转换编辑器（“挖掘模型”选项卡）</span><span class="sxs-lookup"><span data-stu-id="f63ae-117">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 <span data-ttu-id="f63ae-118">**“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。</span><span class="sxs-lookup"><span data-stu-id="f63ae-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="f63ae-119">有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="f63ae-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="f63ae-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="f63ae-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="f63ae-121">转换自定义属性</span><span class="sxs-lookup"><span data-stu-id="f63ae-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="f63ae-122">有关如何设置属性的详细信息，请参阅 [设置数据流组件的属性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f63ae-122">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
