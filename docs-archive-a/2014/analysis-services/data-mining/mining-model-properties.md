---
title: 挖掘模型属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb086f4a978ca96de8e6fc99f889f718247629af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589353"
---
# <a name="mining-model-properties"></a><span data-ttu-id="7a94e-102">挖掘模型属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-102">Mining Model Properties</span></span>
  <span data-ttu-id="7a94e-103">挖掘模型具有以下几种属性：</span><span class="sxs-lookup"><span data-stu-id="7a94e-103">Mining models have the following kinds of properties:</span></span>  
  
-   <span data-ttu-id="7a94e-104">继承自挖掘结构的属性，这些属性定义了该模型使用的数据的数据类型和内容类型；</span><span class="sxs-lookup"><span data-stu-id="7a94e-104">Properties that are inherited from the mining structure that define the data type and content type of the data used by the model;</span></span>  
  
-   <span data-ttu-id="7a94e-105">与用于创建挖掘模型的算法相关的属性，包括任何客户参数；</span><span class="sxs-lookup"><span data-stu-id="7a94e-105">Properties that are related to the algorithm used to create the mining model, including any customer parameters;</span></span>  
  
-   <span data-ttu-id="7a94e-106">在该模型上定义用于定型模型的筛选器的属性。</span><span class="sxs-lookup"><span data-stu-id="7a94e-106">Properties that define a filter on the model used to train the model.</span></span>  
  
 <span data-ttu-id="7a94e-107">挖掘模型的属性最初在创建模型时定义；但是，您稍后可以更改大多数属性，包括算法参数、筛选器和列用法属性。</span><span class="sxs-lookup"><span data-stu-id="7a94e-107">The properties of a mining model are initially defined when you create the model; however, you can alter most properties later, including the algorithm parameters, filters, and column usage properties.</span></span> <span data-ttu-id="7a94e-108">可以使用数据挖掘设计器的 **“挖掘模型”** 选项卡或使用 AMO 或 XMLA 更改这些属性。</span><span class="sxs-lookup"><span data-stu-id="7a94e-108">You change properties by using the **Mining Models** tab of Data Mining Designer, or by using AMO or XMLA.</span></span>  
  
 <span data-ttu-id="7a94e-109">更改模型的任何属性时都必须重新处理该模型以使更改反映在模型中。</span><span class="sxs-lookup"><span data-stu-id="7a94e-109">Whenever you change any property of a model, you must reprocess the model for the changes to be reflected in the model.</span></span> <span data-ttu-id="7a94e-110">重新处理是必需的，即使更改只调用元数据（如添加列别名或说明）。</span><span class="sxs-lookup"><span data-stu-id="7a94e-110">Reprocessing is required even if the change only involves metadata, such as adding a column alias or description.</span></span>  
  
## <a name="properties-of-models"></a><span data-ttu-id="7a94e-111">模型的属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-111">Properties of Models</span></span>  
 <span data-ttu-id="7a94e-112">下表介绍特定于挖掘模型的属性。</span><span class="sxs-lookup"><span data-stu-id="7a94e-112">The following table describes the properties that are specific to mining models.</span></span> <span data-ttu-id="7a94e-113">此外，您还可以对挖掘模型中的各个列设置属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-113">Additionally, there are properties that you can set on individual columns in the mining</span></span>  
  
|<span data-ttu-id="7a94e-114">属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-114">Property</span></span>|<span data-ttu-id="7a94e-115">说明</span><span class="sxs-lookup"><span data-stu-id="7a94e-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7a94e-116">**算法**</span><span class="sxs-lookup"><span data-stu-id="7a94e-116">**Algorithm**</span></span>|<span data-ttu-id="7a94e-117">设置挖掘模型的算法类型。</span><span class="sxs-lookup"><span data-stu-id="7a94e-117">Sets the algorithm type for the mining model.</span></span>|  
|<span data-ttu-id="7a94e-118">**AlgorithmParameters**</span><span class="sxs-lookup"><span data-stu-id="7a94e-118">**AlgorithmParameters**</span></span>|<span data-ttu-id="7a94e-119">设置各个算法类型可用的算法参数的值。</span><span class="sxs-lookup"><span data-stu-id="7a94e-119">Sets values for algorithm parameters that are available for each algorithm type.</span></span>|  
|<span data-ttu-id="7a94e-120">**Filter**</span><span class="sxs-lookup"><span data-stu-id="7a94e-120">**Filter**</span></span>|<span data-ttu-id="7a94e-121">设置筛选器，以筛选用于定型和测试挖掘模型的数据。</span><span class="sxs-lookup"><span data-stu-id="7a94e-121">Sets a filter that is applied to the data that is used for training and testing the mining model.</span></span> <span data-ttu-id="7a94e-122">筛选器定义与挖掘模型存储在一起，并可在创建预测查询或测试模型的准确性时根据需要使用。</span><span class="sxs-lookup"><span data-stu-id="7a94e-122">The filter definition is stored with the model and can be used optionally when you create prediction queries, or when you test the accuracy of the model.</span></span><br /><br /> <span data-ttu-id="7a94e-123">定型模型时模型筛选器不是可选项。</span><span class="sxs-lookup"><span data-stu-id="7a94e-123">The model filter is not optional when training the model.</span></span>|  
|<span data-ttu-id="7a94e-124">**名称**</span><span class="sxs-lookup"><span data-stu-id="7a94e-124">**Name**</span></span>|<span data-ttu-id="7a94e-125">设置挖掘模型的名称。</span><span class="sxs-lookup"><span data-stu-id="7a94e-125">Sets the name of the mining model.</span></span>|  
|<span data-ttu-id="7a94e-126">**AllowDrillThrough**</span><span class="sxs-lookup"><span data-stu-id="7a94e-126">**AllowDrillThrough**</span></span>|<span data-ttu-id="7a94e-127">指定是否为挖掘模型启用钻取。</span><span class="sxs-lookup"><span data-stu-id="7a94e-127">Specifies whether drill through is enabled on the mining model.</span></span>|  
  
## <a name="properties-of-model-columns"></a><span data-ttu-id="7a94e-128">模型列的属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-128">Properties of Model Columns</span></span>  
 <span data-ttu-id="7a94e-129">可以为挖掘模型中的各个列设置以下特定于数据挖掘的属性。</span><span class="sxs-lookup"><span data-stu-id="7a94e-129">You can set the following data mining-specific properties for each column in a mining model.</span></span> <span data-ttu-id="7a94e-130">针对挖掘模型中的各个列，可以将这些属性设置为不同的值。</span><span class="sxs-lookup"><span data-stu-id="7a94e-130">You can set these properties to a different value for each mining model in a mining structure.</span></span>  
  
|<span data-ttu-id="7a94e-131">属性</span><span class="sxs-lookup"><span data-stu-id="7a94e-131">Property</span></span>|<span data-ttu-id="7a94e-132">说明</span><span class="sxs-lookup"><span data-stu-id="7a94e-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7a94e-133">**说明**</span><span class="sxs-lookup"><span data-stu-id="7a94e-133">**Description**</span></span>|<span data-ttu-id="7a94e-134">说明挖掘列的目的。</span><span class="sxs-lookup"><span data-stu-id="7a94e-134">Describes the purpose of the mining column.</span></span>|  
|<span data-ttu-id="7a94e-135">**名称**</span><span class="sxs-lookup"><span data-stu-id="7a94e-135">**Name**</span></span>|<span data-ttu-id="7a94e-136">设置挖掘模型列的名称。</span><span class="sxs-lookup"><span data-stu-id="7a94e-136">Sets the name of the mining model column.</span></span> <span data-ttu-id="7a94e-137">可以键入一个新名称，以便为挖掘模型列提供一个别名。</span><span class="sxs-lookup"><span data-stu-id="7a94e-137">You can type a new name, to provide an alias for the mining model column.</span></span>|  
|<span data-ttu-id="7a94e-138">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="7a94e-138">**ModelingFlags**</span></span>|<span data-ttu-id="7a94e-139">设置列的任意特定于算法的标志。</span><span class="sxs-lookup"><span data-stu-id="7a94e-139">Sets any algorithm-specific flags for the column.</span></span>|  
|<span data-ttu-id="7a94e-140">**SourceColumnID**</span><span class="sxs-lookup"><span data-stu-id="7a94e-140">**SourceColumnID**</span></span>|<span data-ttu-id="7a94e-141">指示模型列所基于的挖掘结构列的名称。</span><span class="sxs-lookup"><span data-stu-id="7a94e-141">Indicates the name of the mining structure column on which the model column is based.</span></span><br /><br /> <span data-ttu-id="7a94e-142">此属性是只读的。</span><span class="sxs-lookup"><span data-stu-id="7a94e-142">This property is read-only.</span></span>|  
|<span data-ttu-id="7a94e-143">**使用情况**</span><span class="sxs-lookup"><span data-stu-id="7a94e-143">**Usage**</span></span>|<span data-ttu-id="7a94e-144">设置挖掘模型如何使用列。</span><span class="sxs-lookup"><span data-stu-id="7a94e-144">Sets how the column will be used by the mining model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a94e-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a94e-145">See Also</span></span>  
 <span data-ttu-id="7a94e-146">[挖掘模型列](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-146">[Mining Model Columns](mining-model-columns.md) </span></span>  
 <span data-ttu-id="7a94e-147">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7a94e-148">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-148">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="7a94e-149">[更改挖掘模型的属性](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-149">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="7a94e-150">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-150">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="7a94e-151">[创建关系挖掘结构](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="7a94e-151">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 [<span data-ttu-id="7a94e-152">为模型列创建别名</span><span class="sxs-lookup"><span data-stu-id="7a94e-152">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
  
