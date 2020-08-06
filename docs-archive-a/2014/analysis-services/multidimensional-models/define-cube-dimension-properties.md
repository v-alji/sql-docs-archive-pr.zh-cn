---
title: 定义多维数据集维度属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9c58cf6a2f55e57c9faa65ddec72fe1bda6000c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577885"
---
# <a name="define-cube-dimension-properties"></a><span data-ttu-id="64894-102">定义多维数据集维度属性</span><span class="sxs-lookup"><span data-stu-id="64894-102">Define Cube Dimension Properties</span></span>
  <span data-ttu-id="64894-103">多维数据集维度是多维数据集中的数据库维度实例。</span><span class="sxs-lookup"><span data-stu-id="64894-103">A cube dimension is an instance of a database dimension within a cube.</span></span> <span data-ttu-id="64894-104">一个数据库维度可用于多个多维数据集，多个多维数据集维度可基于单个数据库维度。</span><span class="sxs-lookup"><span data-stu-id="64894-104">A database dimension can be used in multiple cubes, and multiple cube dimensions can be based on a single database dimension.</span></span> <span data-ttu-id="64894-105">下表说明了多维数据集维度的属性。</span><span class="sxs-lookup"><span data-stu-id="64894-105">The following table describes the properties of a cube dimension.</span></span>  
  
|<span data-ttu-id="64894-106">属性</span><span class="sxs-lookup"><span data-stu-id="64894-106">Property</span></span>|<span data-ttu-id="64894-107">说明</span><span class="sxs-lookup"><span data-stu-id="64894-107">Description</span></span>|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|<span data-ttu-id="64894-108">控制聚合设计器如何设计聚合 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="64894-108">Controls how aggregations are designed by the Aggregation Designer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="64894-109">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="64894-109">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="64894-110">**完全**：多维数据集的每个聚合都必须包括所有成员。</span><span class="sxs-lookup"><span data-stu-id="64894-110">**Full**: Every aggregation for the cube must include the All member.</span></span><br /><br /> <span data-ttu-id="64894-111">**无**：多维数据集的任何聚合都不能包括所有成员。</span><span class="sxs-lookup"><span data-stu-id="64894-111">**None**: No aggregation for the cube can include the All member.</span></span> <span data-ttu-id="64894-112">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="64894-112">This is the default value.</span></span><br /><br /> <span data-ttu-id="64894-113">**无限制**：对聚合设计器不作限制。</span><span class="sxs-lookup"><span data-stu-id="64894-113">**Unrestricted**: No restrictions are placed on the Aggregation Designer.</span></span><br /><br /> <span data-ttu-id="64894-114">**默认值**：与“无限制”功能相同。</span><span class="sxs-lookup"><span data-stu-id="64894-114">**Default**: The same functionality as Unrestricted.</span></span>|  
|`Description`|<span data-ttu-id="64894-115">为该级别提供一个说明性名称。</span><span class="sxs-lookup"><span data-stu-id="64894-115">Provides a descriptive name for the level.</span></span>|  
|`DimensionID`|<span data-ttu-id="64894-116">包含数据库维度的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="64894-116">Contains the unique identifier (ID) of the database dimension.</span></span>|  
|`HierarchyUniqueNameStyle`|<span data-ttu-id="64894-117">确定如何为包含在多维数据集维度中的层次结构生成唯一名称。</span><span class="sxs-lookup"><span data-stu-id="64894-117">Determines how unique names are generated for hierarchies that are contained within the cube dimension.</span></span> <span data-ttu-id="64894-118">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="64894-118">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="64894-119">`IncludeDimensionName`：包括维度的名称，将其作为层次结构名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="64894-119">`IncludeDimensionName`: The name of the dimension is included as part of the name of the hierarchy.</span></span> <span data-ttu-id="64894-120">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="64894-120">This is the default value.</span></span><br /><br /> <span data-ttu-id="64894-121">`ExcludeDimensionName`：维度的名称不作为层次结构名称的一部分。</span><span class="sxs-lookup"><span data-stu-id="64894-121">`ExcludeDimensionName`: The name of the dimension is not included as part of the name of the hierarchy.</span></span>|  
|`ID`|<span data-ttu-id="64894-122">包含多维数据集维度的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="64894-122">Contains the unique identifier of the cube dimension.</span></span>|  
|`MemberUniqueNameStyle`|<span data-ttu-id="64894-123">确定如何为包含在多维数据集维度中的层次结构的成员生成唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="64894-123">Determines how unique names are generated for members of hierarchies contained within the cube dimension.</span></span> <span data-ttu-id="64894-124">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="64894-124">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="64894-125">`Native`：[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 自动确定成员的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="64894-125">`Native`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically determines the unique names of members.</span></span> <span data-ttu-id="64894-126">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="64894-126">This is the default value.</span></span><br /><br /> <span data-ttu-id="64894-127">`NamePath`：[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将生成由每个级别的名称和成员的标题组成的复合名称。</span><span class="sxs-lookup"><span data-stu-id="64894-127">`NamePath`: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates a compound name consisting of the name of each level and the caption of the member.</span></span>|  
|`Name`|<span data-ttu-id="64894-128">包含多维数据集维度的友好名称。</span><span class="sxs-lookup"><span data-stu-id="64894-128">Contains the friendly name of the cube dimension.</span></span> <span data-ttu-id="64894-129">默认情况下，多维数据集维度与数据库维度同名，除非已经定义了另一个同名的多维数据集维度。</span><span class="sxs-lookup"><span data-stu-id="64894-129">By default, the name of a cube dimension is the same as the name of the database dimension, unless another cube dimension of the same name is already defined.</span></span>|  
|`Visible`|<span data-ttu-id="64894-130">确定多维数据集维度是否是可见的。</span><span class="sxs-lookup"><span data-stu-id="64894-130">Determines whether the cube dimension is visible.</span></span> <span data-ttu-id="64894-131">默认值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="64894-131">The default value is `True`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64894-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64894-132">See Also</span></span>  
 [<span data-ttu-id="64894-133">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="64894-133">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
