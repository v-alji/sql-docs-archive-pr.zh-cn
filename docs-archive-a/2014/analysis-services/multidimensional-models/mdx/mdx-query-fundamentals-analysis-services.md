---
title: MDX 查询基础 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a2a9a4f564bc33cc7a1b41a1a4c766c7a76a2cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589313"
---
# <a name="mdx-query-fundamentals-analysis-services"></a><span data-ttu-id="1411a-102">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1411a-102">MDX Query Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="1411a-103">通过使用多维表达式 (MDX)，您可以查询多维对象（如多维数据集）并返回包含多维数据集数据的多维单元集。</span><span class="sxs-lookup"><span data-stu-id="1411a-103">Multidimensional Expressions (MDX) lets you query multidimensional objects, such as cubes, and return multidimensional cellsets that contain the cube's data.</span></span> <span data-ttu-id="1411a-104">本主题及其子主题提供 MDX 查询的概述。</span><span class="sxs-lookup"><span data-stu-id="1411a-104">This topic and its subtopics provide an overview of MDX queries.</span></span>  
  
 <span data-ttu-id="1411a-105">下列主题介绍了 MDX 查询及其产生的单元集，还提供了有关基本 MDX 语法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="1411a-105">The following topics describe MDX queries and the cellsets they produce, and provide more detailed information about basic MDX syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1411a-106">有关与 MDX 查询和计算相关的性能问题的详细信息，请参阅[SQL Server 2005 Analysis Services 性能指南](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)中的 "编写有效的 MDX" 一节。</span><span class="sxs-lookup"><span data-stu-id="1411a-106">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1411a-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="1411a-107">In This Section</span></span>  
  
|<span data-ttu-id="1411a-108">主题</span><span class="sxs-lookup"><span data-stu-id="1411a-108">Topic</span></span>|<span data-ttu-id="1411a-109">说明</span><span class="sxs-lookup"><span data-stu-id="1411a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1411a-110">基本 MDX 查询 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-110">The Basic MDX Query &#40;MDX&#41;</span></span>](mdx-query-the-basic-query.md)|<span data-ttu-id="1411a-111">提供 MDX SELECT 语句的基本语法信息。</span><span class="sxs-lookup"><span data-stu-id="1411a-111">Provides basic syntax information for the MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="1411a-112">用查询轴和切片器轴限定查询 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-112">Restricting the Query with Query and Slicer Axes &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-restricting-the-query.md)|<span data-ttu-id="1411a-113">说明什么是查询轴和切片器轴，以及如何指定它们。</span><span class="sxs-lookup"><span data-stu-id="1411a-113">Describes what query and slicer axes are and how to specify them.</span></span>|  
|[<span data-ttu-id="1411a-114">在查询中建立多维数据集上下文 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-114">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)|<span data-ttu-id="1411a-115">介绍 MDX SELECT 语句中的 FROM 子句的用途。</span><span class="sxs-lookup"><span data-stu-id="1411a-115">Provides a description of the purpose of the FROM clause in an MDX SELECT statement.</span></span>|  
|[<span data-ttu-id="1411a-116">在 MDX 中生成命名集 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-116">Building Named Sets in MDX &#40;MDX&#41;</span></span>](mdx-named-sets-building-named-sets.md)|<span data-ttu-id="1411a-117">介绍 MDX 中的命名集的用途，以及在 MDX 查询中创建与使用命名集所需的技术。</span><span class="sxs-lookup"><span data-stu-id="1411a-117">Describes the purpose of named sets in MDX, and the techniques needed to create and use them in MDX queries.</span></span>|  
|[<span data-ttu-id="1411a-118">在 MDX 中生成计算成员 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-118">Building Calculated Members in MDX &#40;MDX&#41;</span></span>](mdx-calculated-members-building-calculated-members.md)|<span data-ttu-id="1411a-119">提供有关 MDX 中计算成员的信息，包括在 MDX 表达式中创建和使用计算成员所需的技术。</span><span class="sxs-lookup"><span data-stu-id="1411a-119">Provides information about calculated members in MDX, including the techniques needed to create and use them in MDX expressions.</span></span>|  
|[<span data-ttu-id="1411a-120">在 MDX 中生成单元格计算 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-120">Building Cell Calculations in MDX &#40;MDX&#41;</span></span>](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|<span data-ttu-id="1411a-121">详细介绍创建和使用计算单元的过程。</span><span class="sxs-lookup"><span data-stu-id="1411a-121">Details the process of creating and using calculated cells.</span></span>|  
|[<span data-ttu-id="1411a-122">创建和使用属性值 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-122">Creating and Using Property Values &#40;MDX&#41;</span></span>](../../creating-and-using-property-values-mdx.md)|<span data-ttu-id="1411a-123">详细介绍创建和使用维度、级别、成员和单元属性的过程。</span><span class="sxs-lookup"><span data-stu-id="1411a-123">Details the process of creating and using dimension, level, member, and cell properties.</span></span>|  
|[<span data-ttu-id="1411a-124">操作数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-124">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)|<span data-ttu-id="1411a-125">介绍使用钻取和汇总操作数据的基础知识，还介绍了 MDX 中的传递次序和求解次序。</span><span class="sxs-lookup"><span data-stu-id="1411a-125">Describes the basics behind manipulating data using drillthrough and rollup, and also describes pass order and solve order in MDX.</span></span>|  
|[<span data-ttu-id="1411a-126">修改数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-126">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)|<span data-ttu-id="1411a-127">介绍如何使用写回临时或永久更改多维数据。</span><span class="sxs-lookup"><span data-stu-id="1411a-127">Describes how to use writebacks to temporarily or permanently change multidimensional data.</span></span>|  
|[<span data-ttu-id="1411a-128">使用变量和参数 (MDX)</span><span class="sxs-lookup"><span data-stu-id="1411a-128">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="1411a-129">介绍如何在 MDX 查询中使用变量和参数。</span><span class="sxs-lookup"><span data-stu-id="1411a-129">Describes how to use variables and parameters within MDX queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1411a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1411a-130">See Also</span></span>  
 [<span data-ttu-id="1411a-131">多维表达式 (MDX) 参考</span><span class="sxs-lookup"><span data-stu-id="1411a-131">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
