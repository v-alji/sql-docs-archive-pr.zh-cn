---
title: 挖掘结构列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0caebfaef9b80be2d8fb5586a061dcccd31981f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589343"
---
# <a name="mining-structure-columns"></a><span data-ttu-id="a7a3d-102">挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="a7a3d-102">Mining Structure Columns</span></span>
  <span data-ttu-id="a7a3d-103">创建挖掘结构时，通过选择外部数据的列，然后指定如何将数据用于建模来定义挖掘结构中的列。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-103">You define the columns in a mining structure when you create the mining structure, by choosing columns of external data and then specifying how the data is to be used for modeling.</span></span> <span data-ttu-id="a7a3d-104">因此，挖掘结构列不仅仅是数据源的数据副本：它们定义挖掘模型要如何使用数据源的数据。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-104">Therefore, mining structure columns are more than copies of data from a data source: they define how the data from the source is to be used by the mining model.</span></span> <span data-ttu-id="a7a3d-105">您可以分配确定数据如何离散化的属性以及说明数据值如何分布的属性。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-105">You can assign properties that determine how the data is discretized, properties that describe how the data values are distributed</span></span>  
  
 <span data-ttu-id="a7a3d-106">挖掘结构列设计得很灵活且可扩展，这是因为用于生成挖掘模型的每种算法可以使用该结构中的不同列来解释数据。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-106">Mining structure columns are designed to be flexible and extensible, because each algorithm that you use to build a mining model may use different columns from the structure to interpret the data.</span></span> <span data-ttu-id="a7a3d-107">不需要为每个模型提供一个数据集，您可以使用单个挖掘结构并使用其中的列来自定义每个模型的数据。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-107">Rather than have one set of data for each model, you can use a single mining structure and use the columns in it to customize the data for each model.</span></span>  
  
## <a name="defining-mining-structure-columns"></a><span data-ttu-id="a7a3d-108">定义挖掘结构列</span><span class="sxs-lookup"><span data-stu-id="a7a3d-108">Defining Mining Structure Columns</span></span>  
 <span data-ttu-id="a7a3d-109">定义结构列的基本数据类型和内容类型是从用于创建该结构的数据源中派生的。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-109">The basic data types and content types that define structure columns are derived from the data source that you use to create the structure.</span></span> <span data-ttu-id="a7a3d-110">可以更改挖掘结构中的这些设置，还可以设置建模标志以及为连续列设置分发。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-110">You can change these settings within the mining structure, and you can also set modeling flags and set the distribution for continuous columns.</span></span>  
  
 <span data-ttu-id="a7a3d-111">挖掘结构列的定义必须包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="a7a3d-111">The definition of a mining structure column must contain the following information:</span></span>  
  
-   <span data-ttu-id="a7a3d-112">**ID**：列的唯一名称，通常与名称相同。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-112">**ID**: The unique name of the column, often the same as the name.</span></span> <span data-ttu-id="a7a3d-113">在创建挖掘结构后将不能更改它，但是可以更改名称。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-113">This cannot be changed after you create the mining structure, whereas the name can be changed.</span></span>  
  
-   <span data-ttu-id="a7a3d-114">**名称**：列的名称或别名。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-114">**Name**: A name or alias for the column.</span></span>  
  
-   <span data-ttu-id="a7a3d-115">**内容**：一个说明数据是离散的还是连续的枚举。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-115">**Content**: An enumeration that describes whether the data is discrete or continuous.</span></span>  
  
-   <span data-ttu-id="a7a3d-116">**类型**：一个指示一般数据类型的枚举。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-116">**Type**: An enumeration that indicates the general data type.</span></span>  
  
-   <span data-ttu-id="a7a3d-117">**分布**：一个说明值的预期分布的枚举。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-117">**Distribution**: An enumeration that describes the expected distribution of values.</span></span> <span data-ttu-id="a7a3d-118">如果该列为连续列，则包含分发。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-118">A distribution is included if the column is continuous.</span></span>  
  
-   <span data-ttu-id="a7a3d-119">**建模标志**：一个指示如何处理缺失值等等的枚举。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-119">**Modeling flags**: An enumeration that indicates how to handle missing values and so forth.</span></span> <span data-ttu-id="a7a3d-120">还可以对挖掘模型定义建模标志，但是模型标志不同于对结构列使用的标志。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-120">Modeling flags can also be defined on the mining model, but the model flags are different than the flags used on structure columns.</span></span>  
  
-   <span data-ttu-id="a7a3d-121">**绑定**：指定源数据的属性。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-121">**Bindings**: Properties that specify the source data.</span></span>  
  
 <span data-ttu-id="a7a3d-122">第三方算法还可以包含可以为挖掘结构列定义的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-122">Third-party algorithms may also include custom properties that can be defined on the mining structure column.</span></span>  
  
 <span data-ttu-id="a7a3d-123">有关数据挖掘结构和数据挖掘模型的详细信息，请参阅 [挖掘结构（Analysis Services - 数据挖掘）](mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-123">For more information about the data mining structure and the data mining model, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="a7a3d-124">相关内容</span><span class="sxs-lookup"><span data-stu-id="a7a3d-124">Related Content</span></span>  
 <span data-ttu-id="a7a3d-125">有关如何定义和使用挖掘结构列的详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a7a3d-125">See the following topics for more information about how to define and use mining structure columns.</span></span>  
  
|<span data-ttu-id="a7a3d-126">主题</span><span class="sxs-lookup"><span data-stu-id="a7a3d-126">Topic</span></span>|<span data-ttu-id="a7a3d-127">链接</span><span class="sxs-lookup"><span data-stu-id="a7a3d-127">Links</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="a7a3d-128">介绍可用于定义挖掘结构列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-128">Describes the data types that you can use to define a mining structure column.</span></span>|[<span data-ttu-id="a7a3d-129">数据类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-129">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)|  
|<span data-ttu-id="a7a3d-130">说明挖掘结构列中包含的每个数据类型可用的内容类型。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-130">Describes the content types that are available for each type of data that is contained in a mining structure column.</span></span> <span data-ttu-id="a7a3d-131">内容类型依赖于数据类型。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-131">Content types are dependent on data type.</span></span> <span data-ttu-id="a7a3d-132">内容类型在模型级别上分配，确定模型如何使用列数据。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-132">The content type is assigned at the model level, and determines how the column data is used by the model.</span></span>|[<span data-ttu-id="a7a3d-133">内容类型（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-133">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)|  
|<span data-ttu-id="a7a3d-134">介绍嵌套表的概念，并说明如何将嵌套表作为挖掘结构列添加到数据源。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-134">Introduces the concept of nested tables, and explains how nested tables can be added to the data source as mining structure columns.</span></span>|[<span data-ttu-id="a7a3d-135">已分类列（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-135">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="a7a3d-136">列出和说明可以对挖掘结构列设置的分布属性，以指定列中值的预期分布。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-136">Lists and explains the distribution properties that you can set on a mining structure column to specify the expected distribution of values in the column.</span></span>|[<span data-ttu-id="a7a3d-137">列分布（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-137">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)|  
|<span data-ttu-id="a7a3d-138">说明离散化的概念（有时称为“装箱”\*\*），并说明 Analysis Services 提供的将连续数值数据离散化的方法。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-138">Explains the concept of discretization (sometimes referred to as *binning*) and describes the methods that Analysis Services provides for discretizing continuous numeric data.</span></span>|[<span data-ttu-id="a7a3d-139">离散化方法（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-139">Discretization Methods &#40;Data Mining&#41;</span></span>](discretization-methods-data-mining.md)|  
|<span data-ttu-id="a7a3d-140">说明可对挖掘结构列设置的建模标志。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-140">Describes the modeling flags that you can set on a mining structure column.</span></span>|[<span data-ttu-id="a7a3d-141">建模标志（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-141">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="a7a3d-142">说明已分类列，可以使用这种特殊列类型将一个挖掘结构列与另一个挖掘结构列关联。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-142">Describes classified columns, which are a special type of column that you can use to relate one mining structure column to another.</span></span>|[<span data-ttu-id="a7a3d-143">已分类列（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a7a3d-143">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="a7a3d-144">了解如何添加和修改挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="a7a3d-144">Learn to add and modify mining structure columns.</span></span>|[<span data-ttu-id="a7a3d-145">挖掘结构任务和操作指南</span><span class="sxs-lookup"><span data-stu-id="a7a3d-145">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a><span data-ttu-id="a7a3d-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7a3d-146">See Also</span></span>  
 <span data-ttu-id="a7a3d-147">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a7a3d-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="a7a3d-148">挖掘模型列</span><span class="sxs-lookup"><span data-stu-id="a7a3d-148">Mining Model Columns</span></span>](mining-model-columns.md)  
  
  
