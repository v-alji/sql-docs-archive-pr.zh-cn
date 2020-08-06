---
title: 数据挖掘) 的数据类型 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9027ff3928f40d43f16bb31b52e0c1d52e072847
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591657"
---
# <a name="data-types-data-mining"></a><span data-ttu-id="3c01c-102">数据类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="3c01c-102">Data Types (Data Mining)</span></span>
  <span data-ttu-id="3c01c-103">在中创建挖掘模型或挖掘结构时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，必须为挖掘结构中的每个列定义数据类型。</span><span class="sxs-lookup"><span data-stu-id="3c01c-103">When you create a mining model or a mining structure in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must define the data types for each of the columns in the mining structure.</span></span> <span data-ttu-id="3c01c-104">数据类型告知数据挖掘引擎数据源中的数据是数值还是文本以及应如何处理数据。</span><span class="sxs-lookup"><span data-stu-id="3c01c-104">The data type tells the data mining engine whether the data in the data source is numerical or text, and how the data should be processed.</span></span> <span data-ttu-id="3c01c-105">例如，如果数据源中包含数值数据，则可以指定是将数字作为整数处理还是使用小数位数来处理。</span><span class="sxs-lookup"><span data-stu-id="3c01c-105">For example, if your source data contains numerical data, you can specify whether the numbers be treated as integers or by using decimal places.</span></span>  
  
 <span data-ttu-id="3c01c-106">每种数据类型支持一种或多种内容类型。</span><span class="sxs-lookup"><span data-stu-id="3c01c-106">Each data type supports one or more content types.</span></span> <span data-ttu-id="3c01c-107">通过设置内容类型，您可以自定义在挖掘模型中如何处理或计算列中的数据。</span><span class="sxs-lookup"><span data-stu-id="3c01c-107">By setting the content type, you can customize the way that data in the column is processed or calculated in the mining model.</span></span>  
  
 <span data-ttu-id="3c01c-108">例如，如果列中有数值数据，您可以选择将其作为数值数据类型或文本数据类型来处理。</span><span class="sxs-lookup"><span data-stu-id="3c01c-108">For example, if you have numeric data in a column, you can choose to handle it either as a numeric or text data type.</span></span> <span data-ttu-id="3c01c-109">如果选择数值数据类型，则可以设置几种不同的内容类型：可以使数字离散化或者将数字作为连续值处理。</span><span class="sxs-lookup"><span data-stu-id="3c01c-109">If you choose the numeric data type, you can set several different content types: you can discretize the numbers, or handle them as continuous values.</span></span> <span data-ttu-id="3c01c-110">有关所有内容类型列表的信息，请参阅 [内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="3c01c-110">For a list of all the content types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3c01c-111">支持挖掘结构列的以下数据类型：</span><span class="sxs-lookup"><span data-stu-id="3c01c-111">supports the following data types for mining structure columns:</span></span>  
  
|<span data-ttu-id="3c01c-112">数据类型</span><span class="sxs-lookup"><span data-stu-id="3c01c-112">Data Type</span></span>|<span data-ttu-id="3c01c-113">支持的内容类型</span><span class="sxs-lookup"><span data-stu-id="3c01c-113">Supported Content Types</span></span>|  
|---------------|-----------------------------|  
|`Text`|<span data-ttu-id="3c01c-114">Cyclical、Discrete、Discretized、Key Sequence、Ordered 和 Sequence</span><span class="sxs-lookup"><span data-stu-id="3c01c-114">Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence</span></span>|  
|`Long`|<span data-ttu-id="3c01c-115">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence 和 Time</span><span class="sxs-lookup"><span data-stu-id="3c01c-115">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="3c01c-116">Classified</span><span class="sxs-lookup"><span data-stu-id="3c01c-116">Classified</span></span>|  
|`Boolean`|<span data-ttu-id="3c01c-117">Cyclical、Discrete 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="3c01c-117">Cyclical, Discrete, Ordered</span></span>|  
|`Double`|<span data-ttu-id="3c01c-118">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence 和 Time</span><span class="sxs-lookup"><span data-stu-id="3c01c-118">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="3c01c-119">Classified</span><span class="sxs-lookup"><span data-stu-id="3c01c-119">Classified</span></span>|  
|`Date`|<span data-ttu-id="3c01c-120">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="3c01c-120">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3c01c-121">只有第三方算法支持 Time 和 Sequence 内容类型。</span><span class="sxs-lookup"><span data-stu-id="3c01c-121">The Time and Sequence content types are only supported by third-party algorithms.</span></span> <span data-ttu-id="3c01c-122">支持 Cyclical 和 Ordered 内容类型，但大多数算法将它们视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="3c01c-122">The Cyclical and Ordered content types are supported, but most algorithms treat them as discrete values and do not perform special processing.</span></span>  
  
## <a name="specifying-a-data-type"></a><span data-ttu-id="3c01c-123">指定数据类型</span><span class="sxs-lookup"><span data-stu-id="3c01c-123">Specifying a Data Type</span></span>  
 <span data-ttu-id="3c01c-124">如果直接使用数据挖掘扩展插件 (DMX) 创建挖掘模型，则可以在定义该模型时定义每一列的数据类型，同时 Analysis Services 将创建对应的包含指定数据类型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="3c01c-124">If you create the mining model directly by using Data Mining Extensions (DMX), you can define the data type for each column as you define the model, and Analysis Services will create the corresponding mining structure with the specified data types at the same time.</span></span> <span data-ttu-id="3c01c-125">如果通过使用向导创建挖掘模型或挖掘结构，Analysis Services 将建议一种数据类型，或者您可以从列表中选择一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="3c01c-125">If you create the mining model or mining structure by using a wizard, Analysis Services will suggest a data type, or you can choose a data type from a list.</span></span>  
  
## <a name="changing-a-data-type"></a><span data-ttu-id="3c01c-126">更改数据类型</span><span class="sxs-lookup"><span data-stu-id="3c01c-126">Changing a Data Type</span></span>  
 <span data-ttu-id="3c01c-127">如果更改某一列的数据类型，则必须始终重新处理挖掘结构以及基于该结构的所有挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="3c01c-127">If you change the data type of a column, you must always reprocess the mining structure and any mining models that are based on that structure.</span></span> <span data-ttu-id="3c01c-128">有时候，如果更改数据类型，则可能无法再在特定的模型中使用该列。</span><span class="sxs-lookup"><span data-stu-id="3c01c-128">Sometimes if you change the data type, that column can no longer be used in a particular model.</span></span> <span data-ttu-id="3c01c-129">在这种情况下，Analysis Services 将在您重新处理该模型时引发一个错误，或者将处理该模型但忽略该特定列。</span><span class="sxs-lookup"><span data-stu-id="3c01c-129">In that case, Analysis Services will either raise an error when you reprocess the model, or will process the model but leave out that particular column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c01c-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c01c-130">See Also</span></span>  
 <span data-ttu-id="3c01c-131">[内容类型 &#40;数据挖掘&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3c01c-131">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="3c01c-132">[内容类型 &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="3c01c-132">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="3c01c-133">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3c01c-133">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3c01c-134">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3c01c-134">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3c01c-135">[DMX&#41;的数据类型 &#40;](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="3c01c-135">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="3c01c-136">[挖掘模型列](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="3c01c-136">[Mining Model Columns](mining-model-columns.md) </span></span>  
 [<span data-ttu-id="3c01c-137">挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="3c01c-137">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
