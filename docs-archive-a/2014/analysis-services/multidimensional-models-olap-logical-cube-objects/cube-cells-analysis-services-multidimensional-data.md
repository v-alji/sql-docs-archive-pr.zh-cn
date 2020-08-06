---
title: 多维数据集单元 (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b55e940f75319a965fb1441520a7e16ce7ab2f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578513"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a><span data-ttu-id="f7c34-102">多维数据集单元（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="f7c34-102">Cube Cells (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f7c34-103">多维数据集由单元组成，单元按度量值组和维度进行组织。</span><span class="sxs-lookup"><span data-stu-id="f7c34-103">A cube is composed of cells, organized by measure groups and dimensions.</span></span> <span data-ttu-id="f7c34-104">单元表示多维数据集中来自多维数据集内每个维度的一个成员的唯一逻辑交集。</span><span class="sxs-lookup"><span data-stu-id="f7c34-104">A cell represents the unique logical intersection in a cube of one member from every dimension in the cube.</span></span> <span data-ttu-id="f7c34-105">例如，以下关系图说明的多维数据集包含了一个有两个度量值的度量值组，它们通过三个名为“源”、“路线”和“时间”的维度组织在一起。</span><span class="sxs-lookup"><span data-stu-id="f7c34-105">For example, the cube described by the following diagram contains one measure group that has two measures, organized along three dimensions named Source, Route, and Time.</span></span>  
  
 <span data-ttu-id="f7c34-106">![标识单个单元的多维数据集关系图](../../analysis-services/dev-guide/media/as-cubeintro5.gif "标识单个单元的多维数据集关系图")</span><span class="sxs-lookup"><span data-stu-id="f7c34-106">![Cube diagram identifying a single cell](../../analysis-services/dev-guide/media/as-cubeintro5.gif "Cube diagram identifying a single cell")</span></span>  
  
 <span data-ttu-id="f7c34-107">此关系图中的单个带阴影的单元是下列成员的交集：</span><span class="sxs-lookup"><span data-stu-id="f7c34-107">The single shaded cell in this diagram is the intersection of the following members:</span></span>  
  
-   <span data-ttu-id="f7c34-108">“路线”维度的空运成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-108">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-109">“源”维度的非洲成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-109">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-110">“时间”维度的第四季度成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-110">The 4th quarter member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-111">包度量值。</span><span class="sxs-lookup"><span data-stu-id="f7c34-111">The Packages measure.</span></span>  
  
## <a name="leaf-and-nonleaf-cells"></a><span data-ttu-id="f7c34-112">叶和非叶单元</span><span class="sxs-lookup"><span data-stu-id="f7c34-112">Leaf and Nonleaf Cells</span></span>  
 <span data-ttu-id="f7c34-113">可以用几种方式获得多维数据集中的单元的值。</span><span class="sxs-lookup"><span data-stu-id="f7c34-113">The value for a cell in a cube can be obtained in one of several ways.</span></span> <span data-ttu-id="f7c34-114">在上面的示例中，可以从多维数据集的事实数据表中直接检索单元中的值，因为用于标识该单元的所有成员均为*叶成员*。</span><span class="sxs-lookup"><span data-stu-id="f7c34-114">In the previous example, the value in the cell can be directly retrieved from the fact table of the cube, because all the members used to identify that cell are *leaf members*.</span></span> <span data-ttu-id="f7c34-115">从层次结构上看，叶成员没有子成员，并且通常引用维度表中的单个记录。</span><span class="sxs-lookup"><span data-stu-id="f7c34-115">A leaf member has no child members, hierarchically speaking, and typically references a single record in a dimension table.</span></span> <span data-ttu-id="f7c34-116">这种形式的单元格称为*叶单元格*。</span><span class="sxs-lookup"><span data-stu-id="f7c34-116">This kind of cell is referred to as a *leaf cell*.</span></span>  
  
 <span data-ttu-id="f7c34-117">但是，还可以使用*非叶成员*识别单元。</span><span class="sxs-lookup"><span data-stu-id="f7c34-117">However, a cell can also be identified by using *nonleaf members*.</span></span> <span data-ttu-id="f7c34-118">非叶成员是有一个或多个子成员的成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-118">A nonleaf member is a member that has one or more child members.</span></span> <span data-ttu-id="f7c34-119">在这种情况下，通常基于与非叶成员关联的子成员的聚合派生单元的值。</span><span class="sxs-lookup"><span data-stu-id="f7c34-119">In this case, the value of the cell is typically derived from the aggregation of child members associated with the nonleaf member.</span></span> <span data-ttu-id="f7c34-120">例如，下列成员和维度的交集是指其值由聚合提供的单元：</span><span class="sxs-lookup"><span data-stu-id="f7c34-120">For example, the intersection of the following members and dimensions refers to a cell whose value is supplied by aggregation:</span></span>  
  
-   <span data-ttu-id="f7c34-121">“路线”维度的空运成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-121">The air member of the Route dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-122">“源”维度的非洲成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-122">The Africa member of the Source dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-123">“时间”维度的下半年成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-123">The 2nd half member of the Time dimension.</span></span>  
  
-   <span data-ttu-id="f7c34-124">包成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-124">The Packages member.</span></span>  
  
 <span data-ttu-id="f7c34-125">“时间”维度的下半年成员是非叶成员。</span><span class="sxs-lookup"><span data-stu-id="f7c34-125">The 2nd half member of the Time dimension is a nonleaf member.</span></span> <span data-ttu-id="f7c34-126">因此，与它关联的所有值必须都是聚合值，如以下关系图所示。</span><span class="sxs-lookup"><span data-stu-id="f7c34-126">Therefore, all of values associated with it must be aggregated values, as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="f7c34-127">![“下半年”成员的“第三季度”和“第四季度”单元](../../analysis-services/dev-guide/media/as-cubeintro6.gif "“下半年”成员的“第三季度”和“第四季度”单元")</span><span class="sxs-lookup"><span data-stu-id="f7c34-127">![3rd and 4th quarter cells for 2nd half member](../../analysis-services/dev-guide/media/as-cubeintro6.gif "3rd and 4th quarter cells for 2nd half member")</span></span>  
  
 <span data-ttu-id="f7c34-128">假定“第三季度”和“第四季度”成员的聚合就是汇总，则指定单元的值是 400，即上面关系图中所有带阴影叶单元的总和。</span><span class="sxs-lookup"><span data-stu-id="f7c34-128">Assuming the aggregations for the 3rd quarter and 4th quarter members are summations, the value of the specified cell is 400, which is the total of all of the leaf cells shaded in the previous diagram.</span></span> <span data-ttu-id="f7c34-129">由于该单元的值是从其他单元的聚合派生的，因此指定的单元格被视为*非叶单元*。</span><span class="sxs-lookup"><span data-stu-id="f7c34-129">Because the value of the cell is derived from the aggregation of other cells, the specified cell is considered a *nonleaf cell*.</span></span>  
  
 <span data-ttu-id="f7c34-130">除了自定义成员以外，为使用自定义汇总和成员组的成员所派生的单元值将以相似方式进行处理。</span><span class="sxs-lookup"><span data-stu-id="f7c34-130">The cell values derived for members that use custom rollups and member groups, in addition to custom members, are handled similarly.</span></span> <span data-ttu-id="f7c34-131">但是，为计算成员而派生的单元值将完全基于用来定义计算成员的多维表达式 (MDX)；在某些情况下，可能不涉及实际的单元数据。</span><span class="sxs-lookup"><span data-stu-id="f7c34-131">However, cell values derived for calculated members are based completely on the Multidimensional Expressions (MDX) expression used to define the calculated member; in some cases, there may be no actual cell data involved.</span></span> <span data-ttu-id="f7c34-132">有关详细信息，请参阅[父子维度中的自定义汇总运算符](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)、[定义自定义成员公式](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)和[计算](../multidimensional-models-olap-logical-cube-objects/calculations.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c34-132">For more information, see [Custom Rollup Operators in Parent-Child Dimensions](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md), [Define Custom Member Formulas](../multidimensional-models/attribute-properties-define-custom-member-formulas.md), and [Calculations](../multidimensional-models-olap-logical-cube-objects/calculations.md).</span></span>  
  
## <a name="empty-cells"></a><span data-ttu-id="f7c34-133">空单元</span><span class="sxs-lookup"><span data-stu-id="f7c34-133">Empty Cells</span></span>  
 <span data-ttu-id="f7c34-134">并不是多维数据集中的每个单元都必须要包含值；多维数据集中可以有没有数据的交集。</span><span class="sxs-lookup"><span data-stu-id="f7c34-134">It is not required that every cell in a cube contain a value; there can be intersections in a cube that have no data.</span></span> <span data-ttu-id="f7c34-135">这些称为空单元的交集经常出现在多维数据集中，因为并非多维数据集中带有度量值的维度属性的每个交集都在事实数据表中包含一个相应的记录。</span><span class="sxs-lookup"><span data-stu-id="f7c34-135">These intersections, called empty cells, frequently occur in cubes because not every intersection of a dimension attribute with a measure within a cube contains a corresponding record in a fact table.</span></span> <span data-ttu-id="f7c34-136">多维数据集中的空单元格与多维数据集中的单元总数的比值经常称为多维数据集的*稀疏度*。</span><span class="sxs-lookup"><span data-stu-id="f7c34-136">The ratio of empty cells in a cube to the total number of cells in a cube is frequently referred to as the *sparsity* of a cube.</span></span>  
  
 <span data-ttu-id="f7c34-137">例如，下列关系图中所示的多维数据集的结构与本主题中的其他示例类似。</span><span class="sxs-lookup"><span data-stu-id="f7c34-137">For example, the structure of the cube shown in the following diagram is similar to other examples in this topic.</span></span> <span data-ttu-id="f7c34-138">但是，在本示例中，在第三季度没有到非洲的空运或者在第四季度没有到澳大利亚的空运。</span><span class="sxs-lookup"><span data-stu-id="f7c34-138">However, in this example, there were no air shipments to Africa for the third quarter or to Australia for the fourth quarter.</span></span> <span data-ttu-id="f7c34-139">由于事实数据表中无数据支持这些维度和度量值的交集，所以这些交集的单元为空。</span><span class="sxs-lookup"><span data-stu-id="f7c34-139">There is no data in the fact table to support the intersections of those dimensions and measures; therefore the cells at those intersections are empty.</span></span>  
  
 <span data-ttu-id="f7c34-140">![标识空单元的多维数据集关系图](../../analysis-services/dev-guide/media/as-cubeintro7.gif "标识空单元的多维数据集关系图")</span><span class="sxs-lookup"><span data-stu-id="f7c34-140">![Cube diagram identifying empty cells](../../analysis-services/dev-guide/media/as-cubeintro7.gif "Cube diagram identifying empty cells")</span></span>  
  
 <span data-ttu-id="f7c34-141">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，空单元格是具有特殊质量的单元格。</span><span class="sxs-lookup"><span data-stu-id="f7c34-141">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an empty cell is a cell that has special qualities.</span></span> <span data-ttu-id="f7c34-142">因为空单元可扭曲交叉联接、计数等的结果，因此为了进行计算，许多 MDX 函数都提供了忽略空单元的功能。</span><span class="sxs-lookup"><span data-stu-id="f7c34-142">Because empty cells can skew the results of crossjoins, counts, and so on, many MDX functions supply the ability to ignore empty cells for the purposes of calculation.</span></span> <span data-ttu-id="f7c34-143">有关详细信息，请参阅 mdx [&#41; 引用 &#40;多维表达式](/sql/mdx/multidimensional-expressions-mdx-reference)和[Mdx 中的重要概念 &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c34-143">For more information, see [Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference), and [Key Concepts in MDX &#40;Analysis Services&#41;](../multidimensional-models/key-concepts-in-mdx-analysis-services.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="f7c34-144">安全性</span><span class="sxs-lookup"><span data-stu-id="f7c34-144">Security</span></span>  
 <span data-ttu-id="f7c34-145">对单元数据的访问是在角色级别通过 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 来进行管理的，并且可以使用 MDX 表达式进行严格控制。</span><span class="sxs-lookup"><span data-stu-id="f7c34-145">Access to cell data is managed in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] at the role level, and can be finely controlled by using MDX expressions.</span></span> <span data-ttu-id="f7c34-146">有关详细信息，请参阅[授予对维度数据的自定义访问权限 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)，并[授予对单元数据的自定义访问 &#40;Analysis Services ](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)&#41;。</span><span class="sxs-lookup"><span data-stu-id="f7c34-146">For more information, see [Grant custom access to dimension data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md), and [Grant custom access to cell data &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c34-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7c34-147">See Also</span></span>  
 <span data-ttu-id="f7c34-148">[多维数据集存储 &#40;Analysis Services 多维数据&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f7c34-148">[Cube Storage &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f7c34-149">聚合和聚合设计</span><span class="sxs-lookup"><span data-stu-id="f7c34-149">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
