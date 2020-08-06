---
title: Analysis Services 多维数据)  (维度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- OLAP objects [Analysis Services], dimensions
- dimensions [Analysis Services]
- Analysis Services objects, dimensions
ms.assetid: 2b114135-2572-4479-8c81-3ccf0cfeb9f7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e0e15d4f74c2c6cec06edaf692199e48534c7e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692596"
---
# <a name="dimensions-analysis-services---multidimensional-data"></a><span data-ttu-id="dcb63-102">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="dcb63-102">Dimensions (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="dcb63-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度是多维数据集的基本组件。</span><span class="sxs-lookup"><span data-stu-id="dcb63-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="dcb63-104">维度可将和相关领域（如客户、商店或雇员）关联的数据与用户组织起来。</span><span class="sxs-lookup"><span data-stu-id="dcb63-104">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span> <span data-ttu-id="dcb63-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的维度包含与维度表中的列相对应的属性。</span><span class="sxs-lookup"><span data-stu-id="dcb63-105">Dimensions in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contain attributes that correspond to columns in dimension tables.</span></span> <span data-ttu-id="dcb63-106">这些属性显示为属性结构，并且可以组织成用户定义层次结构，或者可以基于基础维度表中的列定义为父子层次结构。</span><span class="sxs-lookup"><span data-stu-id="dcb63-106">These attributes appear as attribute hierarchies and can be organized into user-defined hierarchies, or can be defined as parent-child hierarchies based on columns in the underlying dimension table.</span></span> <span data-ttu-id="dcb63-107">层次结构用于组织多维数据集中包含的度量值。</span><span class="sxs-lookup"><span data-stu-id="dcb63-107">Hierarchies are used to organize measures that are contained in a cube.</span></span> <span data-ttu-id="dcb63-108">下列主题概述了维度、属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="dcb63-108">The following topics provide an overview of dimensions, attributes, and hierarchies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcb63-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="dcb63-109">In This Section</span></span>  
  
|<span data-ttu-id="dcb63-110">主题</span><span class="sxs-lookup"><span data-stu-id="dcb63-110">Topic</span></span>|<span data-ttu-id="dcb63-111">说明</span><span class="sxs-lookup"><span data-stu-id="dcb63-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dcb63-112">维度简介（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="dcb63-112">Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="dcb63-113">概述维度概念。</span><span class="sxs-lookup"><span data-stu-id="dcb63-113">Provides an overview of dimension concepts.</span></span>|  
|[<span data-ttu-id="dcb63-114">属性和属性层次结构</span><span class="sxs-lookup"><span data-stu-id="dcb63-114">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="dcb63-115">说明属性和属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="dcb63-115">Describes attributes and attribute hierarchies.</span></span>|  
|[<span data-ttu-id="dcb63-116">用户层次结构</span><span class="sxs-lookup"><span data-stu-id="dcb63-116">User Hierarchies</span></span>](user-hierarchies.md)|<span data-ttu-id="dcb63-117">说明用户定义的属性层次结构。</span><span class="sxs-lookup"><span data-stu-id="dcb63-117">Describes user-defined hierarchies of attributes.</span></span>|  
|[<span data-ttu-id="dcb63-118">启用写操作的维度</span><span class="sxs-lookup"><span data-stu-id="dcb63-118">Write-Enabled Dimensions</span></span>](write-enabled-dimensions.md)|<span data-ttu-id="dcb63-119">说明已启用写操作的维度。</span><span class="sxs-lookup"><span data-stu-id="dcb63-119">Describes write-enabled dimensions.</span></span>|  
|[<span data-ttu-id="dcb63-120">维度翻译</span><span class="sxs-lookup"><span data-stu-id="dcb63-120">Dimension Translations</span></span>](dimension-translations.md)|<span data-ttu-id="dcb63-121">说明维度元数据的翻译。</span><span class="sxs-lookup"><span data-stu-id="dcb63-121">Describes translations of dimension meta data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcb63-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcb63-122">See Also</span></span>  
 <span data-ttu-id="dcb63-123">[多维模型中的维度](../multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="dcb63-123">[Dimensions in Multidimensional Models](../multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="dcb63-124">多维数据集对象 &#40;Analysis Services 多维数据&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb63-124">Cube Objects &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
  
