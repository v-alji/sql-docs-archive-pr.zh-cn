---
title: 在简单示例中使用查询轴和切片器轴 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 324f082fd6659592e56af65680bd4aa623c625d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588726"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a><span data-ttu-id="34ebe-102">在简单示例中使用查询轴和切片器轴 (MDX)</span><span class="sxs-lookup"><span data-stu-id="34ebe-102">Using Query and Slicer Axes in a Simple Example (MDX)</span></span>
  <span data-ttu-id="34ebe-103">本主题中提供的简单示例说明了指定和使用查询轴和切片器轴的基本操作。</span><span class="sxs-lookup"><span data-stu-id="34ebe-103">The simple example presented in this topic illustrates the basics of specifying and using query and slicer axes.</span></span>  
  
## <a name="the-cube"></a><span data-ttu-id="34ebe-104">多维数据集</span><span class="sxs-lookup"><span data-stu-id="34ebe-104">The Cube</span></span>  
 <span data-ttu-id="34ebe-105">名为 TestCube 的多维数据集有两个维度，分别为 Route 和 Time。</span><span class="sxs-lookup"><span data-stu-id="34ebe-105">A cube, named TestCube, has two simple dimensions named Route and Time.</span></span> <span data-ttu-id="34ebe-106">每个维度都只有一个用户层次结构，分别为 Route 和 Time。</span><span class="sxs-lookup"><span data-stu-id="34ebe-106">Each dimension has only one user hierarchy, named Route and Time respectively.</span></span> <span data-ttu-id="34ebe-107">因为多维数据集的度量值是 Measures 维度的一部分，所以此多维数据集总共有三个维度。</span><span class="sxs-lookup"><span data-stu-id="34ebe-107">Because the measures of the cube are part of the Measures dimension, this cube has three dimensions in all.</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="34ebe-108">查询</span><span class="sxs-lookup"><span data-stu-id="34ebe-108">The Query</span></span>  
 <span data-ttu-id="34ebe-109">查询要提供一个矩阵，可以在该矩阵内跨路线和时间比较 Packages 度量值。</span><span class="sxs-lookup"><span data-stu-id="34ebe-109">The query is to provide a matrix in which the Packages measure can be compared across routes and times.</span></span>  
  
 <span data-ttu-id="34ebe-110">在下面的 MDX 查询示例中，Route 和 Time 层次结构为查询轴，Measures 维度为切片器轴。</span><span class="sxs-lookup"><span data-stu-id="34ebe-110">In the following MDX query example, the Route and Time hierarchies are the query axes, and the Measures dimension is the slicer axis.</span></span> <span data-ttu-id="34ebe-111">[Members](/sql/mdx/members-set-mdx) 函数指明 MDX 将使用层次结构或级别的成员来构造一个集。</span><span class="sxs-lookup"><span data-stu-id="34ebe-111">The [Members](/sql/mdx/members-set-mdx) function indicates that MDX will use the members of the hierarchy or level to construct a set.</span></span> <span data-ttu-id="34ebe-112">使用 `Members` 函数意味着不必在 MDX 查询中显式声明特定层次结构或级别的每个成员。</span><span class="sxs-lookup"><span data-stu-id="34ebe-112">The use of the `Members` function means that you do not have to explicitly state each member of a specific hierarchy or level in an MDX query.</span></span>  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a><span data-ttu-id="34ebe-113">结果</span><span class="sxs-lookup"><span data-stu-id="34ebe-113">The Results</span></span>  
 <span data-ttu-id="34ebe-114">结果是一个网格，标识 COLUMNS 和 ROWS 轴维度的每个交点处 Packages 度量值的值。</span><span class="sxs-lookup"><span data-stu-id="34ebe-114">The result is a grid that identifies the value of the Packages measure at each intersection of the COLUMNS and ROWS axis dimensions.</span></span> <span data-ttu-id="34ebe-115">下表显示了此网格。</span><span class="sxs-lookup"><span data-stu-id="34ebe-115">The following table shows how this grid would look.</span></span>  
  
||<span data-ttu-id="34ebe-116">air</span><span class="sxs-lookup"><span data-stu-id="34ebe-116">air</span></span>|<span data-ttu-id="34ebe-117">sea</span><span class="sxs-lookup"><span data-stu-id="34ebe-117">sea</span></span>|  
|-|---------|---------|  
|<span data-ttu-id="34ebe-118">第一季度</span><span class="sxs-lookup"><span data-stu-id="34ebe-118">1st quarter</span></span>|<span data-ttu-id="34ebe-119">60</span><span class="sxs-lookup"><span data-stu-id="34ebe-119">60</span></span>|<span data-ttu-id="34ebe-120">50</span><span class="sxs-lookup"><span data-stu-id="34ebe-120">50</span></span>|  
|<span data-ttu-id="34ebe-121">第二季度</span><span class="sxs-lookup"><span data-stu-id="34ebe-121">2nd quarter</span></span>|<span data-ttu-id="34ebe-122">45</span><span class="sxs-lookup"><span data-stu-id="34ebe-122">45</span></span>|<span data-ttu-id="34ebe-123">45</span><span class="sxs-lookup"><span data-stu-id="34ebe-123">45</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34ebe-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34ebe-124">See Also</span></span>  
 <span data-ttu-id="34ebe-125">[&#40;MDX&#41;指定查询轴的内容](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span><span class="sxs-lookup"><span data-stu-id="34ebe-125">[Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md) </span></span>  
 [<span data-ttu-id="34ebe-126">指定切片器轴的内容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="34ebe-126">Specifying the Contents of a Slicer Axis &#40;MDX&#41;</span></span>](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
