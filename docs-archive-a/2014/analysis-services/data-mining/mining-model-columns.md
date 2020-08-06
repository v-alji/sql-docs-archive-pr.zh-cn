---
title: 挖掘模型列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f936f3f4e0b8f65326e9a6e84f75e6f4e82657f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689677"
---
# <a name="mining-model-columns"></a><span data-ttu-id="c3575-102">挖掘模型列</span><span class="sxs-lookup"><span data-stu-id="c3575-102">Mining Model Columns</span></span>
  <span data-ttu-id="c3575-103">数据挖掘模型为挖掘结构表示的数据应用挖掘模型算法。</span><span class="sxs-lookup"><span data-stu-id="c3575-103">A data mining model applies a mining model algorithm to the data that is represented by a mining structure.</span></span> <span data-ttu-id="c3575-104">如挖掘结构一样，挖掘模型也包含列。</span><span class="sxs-lookup"><span data-stu-id="c3575-104">Like the mining structure, the mining model contains columns.</span></span> <span data-ttu-id="c3575-105">挖掘模型包含在挖掘结构之内，继承由挖掘结构定义的所有属性值。</span><span class="sxs-lookup"><span data-stu-id="c3575-105">A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure.</span></span> <span data-ttu-id="c3575-106">该模型可以使用挖掘结构包含的所有列，或使用其中一部分列。</span><span class="sxs-lookup"><span data-stu-id="c3575-106">The model can use all the columns that the mining structure contains or a subset of the columns.</span></span>  
  
 <span data-ttu-id="c3575-107">您还可以为挖掘模型列定义另外两条信息：用法和建模标志。</span><span class="sxs-lookup"><span data-stu-id="c3575-107">You can define two additional pieces of information on a mining model column: usage, and modeling flags.</span></span>  
  
-   <span data-ttu-id="c3575-108">**用法** 是一个属性，它定义模型如何使用列。</span><span class="sxs-lookup"><span data-stu-id="c3575-108">**Usage** is a property that defines how the model uses the column.</span></span> <span data-ttu-id="c3575-109">列可用作输入列、键列或可预测列。</span><span class="sxs-lookup"><span data-stu-id="c3575-109">Columns can be used as input columns, key columns, or predictable columns.</span></span>  
  
-   <span data-ttu-id="c3575-110">**建模标志** 为算法提供有关事例表中定义的数据的附加信息，以便算法可以生成更精确的模型。</span><span class="sxs-lookup"><span data-stu-id="c3575-110">**Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model.</span></span> <span data-ttu-id="c3575-111">可以使用数据挖掘扩展插件 (DMX) 语言以编程的方式定义建模标志，也可以在 **的** 数据挖掘设计器 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中定义建模标志。</span><span class="sxs-lookup"><span data-stu-id="c3575-111">You can define modeling flags programmatically by using the Data Mining Extensions (DMX) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="c3575-112">下面介绍了可以为挖掘模型列定义的建模标志。</span><span class="sxs-lookup"><span data-stu-id="c3575-112">The following list describes the modeling flags that you can define on a mining model column.</span></span>  
  
 `MODEL_EXISTENCE_ONLY`  
 <span data-ttu-id="c3575-113">指示属性的存在比属性列中的值更为重要。</span><span class="sxs-lookup"><span data-stu-id="c3575-113">Indicates that the presence of the attribute is more important than the values that are in the attribute column.</span></span> <span data-ttu-id="c3575-114">例如，假定一个事例表包含与特定用户相关联的一系列订单项。</span><span class="sxs-lookup"><span data-stu-id="c3575-114">For example, consider a case table that contains a list of order items that are associated with a particular customer.</span></span> <span data-ttu-id="c3575-115">表数据包括产品类型、ID 和每项的费用。</span><span class="sxs-lookup"><span data-stu-id="c3575-115">The table data includes the product type, ID, and cost of each item.</span></span> <span data-ttu-id="c3575-116">对于建模来说，客户购买了某特定订单项这个事实可能比订单项本身的费用更重要。</span><span class="sxs-lookup"><span data-stu-id="c3575-116">For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself.</span></span> <span data-ttu-id="c3575-117">在这种情况下，费用列应标记为 `MODEL_EXISTENCE_ONLY`。</span><span class="sxs-lookup"><span data-stu-id="c3575-117">In this case, the cost column should be marked as `MODEL_EXISTENCE_ONLY`.</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="c3575-118">指示该算法可以在回归算法的回归公式中使用指定列。</span><span class="sxs-lookup"><span data-stu-id="c3575-118">Indicates that the algorithm can use the specified column in the regression formula of regression algorithms.</span></span> <span data-ttu-id="c3575-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 时序算法支持该标志。</span><span class="sxs-lookup"><span data-stu-id="c3575-119">This flag is supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithms.</span></span>  
  
 <span data-ttu-id="c3575-120">有关使用 DMX 以编程方式设置用法属性和定义建模标志的详细信息，请参阅 [CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c3575-120">For more information about setting the usage property and defining modeling flags programmatically with DMX, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span> <span data-ttu-id="c3575-121">有关在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设置用法属性和定义建模标志的详细信息，请参阅 [移动数据挖掘对象](moving-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="c3575-121">For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Moving Data Mining Objects](moving-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3575-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3575-122">See Also</span></span>  
 <span data-ttu-id="c3575-123">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c3575-123">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c3575-124">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c3575-124">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c3575-125">[更改挖掘模型的属性](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="c3575-125">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="c3575-126">[从挖掘模型中排除列](exclude-a-column-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="c3575-126">[Exclude a Column from a Mining Model](exclude-a-column-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="c3575-127">挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="c3575-127">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
