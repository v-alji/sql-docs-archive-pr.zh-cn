---
title: 列分布 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
ms.openlocfilehash: 29aad33535c4cc4d9baf4c453249ce3b51595e78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591667"
---
# <a name="column-distributions-data-mining"></a><span data-ttu-id="fb65b-102">列分布（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="fb65b-102">Column Distributions (Data Mining)</span></span>
  <span data-ttu-id="fb65b-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以在挖掘结构中定义列分布，以影响在创建挖掘模型时算法如何处理这些列中的数据。</span><span class="sxs-lookup"><span data-stu-id="fb65b-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="fb65b-104">对于某些算法，如果已知列中包含常用的值分布，则在处理模型之前定义任意连续列的分布将非常有用。</span><span class="sxs-lookup"><span data-stu-id="fb65b-104">For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values.</span></span> <span data-ttu-id="fb65b-105">如果不定义分布，则由于算法据以解释数据的信息较少，生成的挖掘模型产生的预测可能不如定义了分布时产生的预测精确。</span><span class="sxs-lookup"><span data-stu-id="fb65b-105">If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.</span></span>

 <span data-ttu-id="fb65b-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中可用的算法支持下列分布类型：</span><span class="sxs-lookup"><span data-stu-id="fb65b-106">The algorithms that are available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support the following distribution types:</span></span>

 <span data-ttu-id="fb65b-107">`Normal`连续列的值构成具有正态分布的直方图。</span><span class="sxs-lookup"><span data-stu-id="fb65b-107">`Normal` The values for the continuous column form a histogram with a normal distribution.</span></span>

 <span data-ttu-id="fb65b-108">![具有正态分布的直方图](../media/normal-distribution.gif "具有正态分布的直方图")</span><span class="sxs-lookup"><span data-stu-id="fb65b-108">![Histogram with normal distribution](../media/normal-distribution.gif "Histogram with normal distribution")</span></span>

 <span data-ttu-id="fb65b-109">`Log Normal`连续列的值构成一个直方图，其中曲线在高端高端延长，并沿低端向下倾斜。</span><span class="sxs-lookup"><span data-stu-id="fb65b-109">`Log Normal` The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.</span></span>

 <span data-ttu-id="fb65b-110">![具有日志正态分布的直方图](../media/log-normal-distribution.gif "具有日志正态分布的直方图")</span><span class="sxs-lookup"><span data-stu-id="fb65b-110">![Histogram with log normal distribution](../media/log-normal-distribution.gif "Histogram with log normal distribution")</span></span>

 <span data-ttu-id="fb65b-111">`Uniform`连续列的值构成平面曲线，其中所有值都有可能出现。</span><span class="sxs-lookup"><span data-stu-id="fb65b-111">`Uniform` The values for the continuous column form a flat curve, in which all values are equally likely.</span></span>

 <span data-ttu-id="fb65b-112">![具有均匀分布的直方图](../media/uniform-distribution.gif "具有均匀分布的直方图")</span><span class="sxs-lookup"><span data-stu-id="fb65b-112">![Histogram with uniform distribution](../media/uniform-distribution.gif "Histogram with uniform distribution")</span></span>

 <span data-ttu-id="fb65b-113">有关 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的算法的详细信息，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fb65b-113">For more information about the algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb65b-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb65b-114">See Also</span></span>
 <span data-ttu-id="fb65b-115">[&#40;数据挖掘&#41;](content-types-data-mining.md) [挖掘结构的内容类型 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) [离散化方法 &#40;数据挖掘&#41;](discretization-methods-data-mining.md)分布式 &#40;[DMX](/sql/dmx/distributions-dmx)&#41;[挖掘结构列](mining-structure-columns.md)</span><span class="sxs-lookup"><span data-stu-id="fb65b-115">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md) [Distributions &#40;DMX&#41;](/sql/dmx/distributions-dmx) [Mining Structure Columns](mining-structure-columns.md)</span></span>


