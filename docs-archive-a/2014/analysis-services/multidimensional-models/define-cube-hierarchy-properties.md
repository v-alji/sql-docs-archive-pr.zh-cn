---
title: 定义多维数据集层次结构属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687291"
---
# <a name="define-cube-hierarchy-properties"></a><span data-ttu-id="02719-102">定义多维数据集层次结构属性</span><span class="sxs-lookup"><span data-stu-id="02719-102">Define Cube Hierarchy Properties</span></span>
  <span data-ttu-id="02719-103">可以使用多维数据集层次结构属性，为基于同一数据库维度的多维数据集维度中的用户定义层次结构指定唯一的设置。</span><span class="sxs-lookup"><span data-stu-id="02719-103">Cube hierarchy properties enable you to specify unique settings for user-defined hierarchies in cube dimensions based on the same database dimension.</span></span> <span data-ttu-id="02719-104">下表介绍了多维数据集层次结构的属性。</span><span class="sxs-lookup"><span data-stu-id="02719-104">The following table describes the properties of a cube hierarchy.</span></span>  
  
|<span data-ttu-id="02719-105">属性</span><span class="sxs-lookup"><span data-stu-id="02719-105">Property</span></span>|<span data-ttu-id="02719-106">说明</span><span class="sxs-lookup"><span data-stu-id="02719-106">Description</span></span>|  
|--------------|-----------------|  
|`Enabled`|<span data-ttu-id="02719-107">确定是否针对多维数据集维度启用层次结构。</span><span class="sxs-lookup"><span data-stu-id="02719-107">Determines whether the hierarchy is enabled for the cube dimension.</span></span>|  
|`HierarchyID`|<span data-ttu-id="02719-108">包含层次结构的唯一标识符 (ID)。</span><span class="sxs-lookup"><span data-stu-id="02719-108">Contains the unique identifier (ID) of the hierarchy.</span></span>|  
|`OptimizedState`|<span data-ttu-id="02719-109">确定应用于层次结构的优化级别。</span><span class="sxs-lookup"><span data-stu-id="02719-109">Determines the level of optimization that is applied to the hierarchy.</span></span> <span data-ttu-id="02719-110">此属性可以有下列值：</span><span class="sxs-lookup"><span data-stu-id="02719-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="02719-111">`FullyOptimized`：实例为层次结构生成索引以提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="02719-111">`FullyOptimized`: The instance builds indexes for the hierarchy to improve query performance.</span></span> <span data-ttu-id="02719-112">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="02719-112">This is the default value.</span></span><br /><br /> <span data-ttu-id="02719-113">`NotOptimized`：实例不生成其他索引。</span><span class="sxs-lookup"><span data-stu-id="02719-113">`NotOptimized`: The instance does not build additional indexes.</span></span>|  
|`Visible`|<span data-ttu-id="02719-114">确定多维数据集层次结构的可见性。</span><span class="sxs-lookup"><span data-stu-id="02719-114">Determines the visibility of the cube hierarchy.</span></span> <span data-ttu-id="02719-115">默认值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="02719-115">The default value is `True`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02719-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02719-116">See Also</span></span>  
 [<span data-ttu-id="02719-117">用户层次结构</span><span class="sxs-lookup"><span data-stu-id="02719-117">User Hierarchies</span></span>](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
