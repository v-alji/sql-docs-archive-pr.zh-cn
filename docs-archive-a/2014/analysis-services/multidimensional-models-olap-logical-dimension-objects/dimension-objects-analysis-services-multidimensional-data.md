---
title: Analysis Services 多维数据)  (维度对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02bb6a26b04a2fb79994e192c9c62a7cb362476c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591612"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="c915d-102">维度对象（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c915d-102">Dimension Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c915d-103">简单 <xref:Microsoft.AnalysisServices.Dimension> 对象由基本信息、属性和层次结构组成。</span><span class="sxs-lookup"><span data-stu-id="c915d-103">A simple <xref:Microsoft.AnalysisServices.Dimension> object is composed of basic information, attributes, and hierarchies.</span></span> <span data-ttu-id="c915d-104">基本信息包括维度的名称、维度的类型、数据源和存储模式等。</span><span class="sxs-lookup"><span data-stu-id="c915d-104">Basic information includes the name of the dimension, the type of the dimension, the data source, the storage mode, and others.</span></span> <span data-ttu-id="c915d-105">属性可定义维度中的实际数据。</span><span class="sxs-lookup"><span data-stu-id="c915d-105">Attributes define the actual data in the dimension.</span></span> <span data-ttu-id="c915d-106">属性可不必属于层次结构，但层次结构却要由属性生成。</span><span class="sxs-lookup"><span data-stu-id="c915d-106">Attributes do not necessarily belong to a hierarchy, but hierarchies are built from attributes.</span></span> <span data-ttu-id="c915d-107">层次结构不但可创建级别的有序列表，还可定义用户浏览维度的方式。</span><span class="sxs-lookup"><span data-stu-id="c915d-107">A hierarchy creates ordered lists of levels, and defines the ways a user can explore the dimension.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c915d-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="c915d-108">In This Section</span></span>  
 <span data-ttu-id="c915d-109">下列主题提供有关如何设计和实现维度对象的详细信息。</span><span class="sxs-lookup"><span data-stu-id="c915d-109">The following topics provide more information about how to design and implement dimension objects.</span></span>  
  
|<span data-ttu-id="c915d-110">主题</span><span class="sxs-lookup"><span data-stu-id="c915d-110">Topic</span></span>|<span data-ttu-id="c915d-111">说明</span><span class="sxs-lookup"><span data-stu-id="c915d-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c915d-112">维度（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c915d-112">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="c915d-113">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度是多维数据集的基本组件。</span><span class="sxs-lookup"><span data-stu-id="c915d-113">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dimensions are a fundamental component of cubes.</span></span> <span data-ttu-id="c915d-114">维度可将和相关领域（如客户、商店或雇员）关联的数据与用户组织起来。</span><span class="sxs-lookup"><span data-stu-id="c915d-114">Dimensions organize data with relation to an area of interest, such as customers, stores, or employees, to users.</span></span>|  
|[<span data-ttu-id="c915d-115">属性和属性层次结构</span><span class="sxs-lookup"><span data-stu-id="c915d-115">Attributes and Attribute Hierarchies</span></span>](attributes-and-attribute-hierarchies.md)|<span data-ttu-id="c915d-116">维度是属性的集合，这些属性绑定到数据源视图的表或视图中的一列或多列。</span><span class="sxs-lookup"><span data-stu-id="c915d-116">Dimensions are collections of attributes, which are bound to one or more columns in a table or view in the data source view.</span></span>|  
|[<span data-ttu-id="c915d-117">的维度设计器中，可以在“维度结构”视图的</span><span class="sxs-lookup"><span data-stu-id="c915d-117">Attribute Relationships</span></span>](attribute-relationships.md)|<span data-ttu-id="c915d-118">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，维度中的属性始终直接或间接与键属性相关。</span><span class="sxs-lookup"><span data-stu-id="c915d-118">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributes within a dimension are always related either directly or indirectly to the key attribute.</span></span> <span data-ttu-id="c915d-119">当您基于星型架构（在该架构中，所有维度属性都派生自同一关系表）定义维度时，维度的键属性和每个非键属性之间会自动定义属性关系。</span><span class="sxs-lookup"><span data-stu-id="c915d-119">When you define a dimension based on a star schema, which is where all dimension attributes are derived from the same relational table, an attribute relationship is automatically defined between the key attribute and each non-key attribute of the dimension.</span></span> <span data-ttu-id="c915d-120">当您基于雪花架构（在该架构中，维度属性派生自多个相关的表）定义维度时，会自动按如下方式定义属性关系：</span><span class="sxs-lookup"><span data-stu-id="c915d-120">When you define a dimension based on a snowflake schema, which is where dimension attributes are derived from multiple related tables, an attribute relationship is automatically defined as follows:</span></span><br /><br /> <span data-ttu-id="c915d-121">-在键属性与绑定到主维度表中的列的每个非键属性之间。</span><span class="sxs-lookup"><span data-stu-id="c915d-121">-   Between the key attribute and each non-key attribute bound to columns in the main dimension table.</span></span><br /><span data-ttu-id="c915d-122">-在键属性与绑定到辅助表中链接基础维度表的外键的属性之间。</span><span class="sxs-lookup"><span data-stu-id="c915d-122">-   Between the key attribute and the attribute bound to the foreign key in the secondary table that links the underlying dimension tables.</span></span><br /><span data-ttu-id="c915d-123">-在绑定到辅助表中的外键的属性与绑定到辅助表中的列的每个非键属性之间。</span><span class="sxs-lookup"><span data-stu-id="c915d-123">-   Between the attribute bound to foreign key in the secondary table and each non-key attribute bound to columns from the secondary table.</span></span>|  
  
  
