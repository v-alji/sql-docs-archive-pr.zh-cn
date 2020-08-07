---
title: 用查询轴和切片器轴 (MDX) 来限制查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed4d50aa40d2915c60f887e64cdc3ef8a6d52c5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690817"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a><span data-ttu-id="fab8e-102">用查询轴和切片器轴限定查询 (MDX)</span><span class="sxs-lookup"><span data-stu-id="fab8e-102">Restricting the Query with Query and Slicer Axes (MDX)</span></span>
  <span data-ttu-id="fab8e-103">在设计多维表达式 (MDX) SELECT 语句时，应用程序通常检查多维数据集并将层次结构集分为两个子集：</span><span class="sxs-lookup"><span data-stu-id="fab8e-103">When formulating a Multidimensional Expressions (MDX) SELECT statement, an application typically examines a cube and divides the set of hierarchies into two subsets:</span></span>  
  
-   <span data-ttu-id="fab8e-104">**查询轴**-从中检索多个成员的数据的一组层次结构。</span><span class="sxs-lookup"><span data-stu-id="fab8e-104">**Query axes**-the set of hierarchies from which data is retrieved for multiple members.</span></span> <span data-ttu-id="fab8e-105">有关查询轴的详细信息，请参阅[指定查询轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="fab8e-105">For more information about query axes, see [Specifying the Contents of a Query Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).</span></span>  
  
-   <span data-ttu-id="fab8e-106">**切片器轴**-从中检索单个成员的数据的一组层次结构。</span><span class="sxs-lookup"><span data-stu-id="fab8e-106">**Slicer axis**-the set of hierarchies from which data is retrieved for a single member.</span></span> <span data-ttu-id="fab8e-107">有关切片器轴的详细信息，请参阅[指定切片器轴的内容 (MDX)](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。</span><span class="sxs-lookup"><span data-stu-id="fab8e-107">For more information about the slicer axis, see [Specifying the Contents of a Slicer Axis &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).</span></span>  
  
 <span data-ttu-id="fab8e-108">由于查询轴和切片器轴可以从要查询的多维数据集的多个层次结构中构造，因此这些术语可用于将要查询的多维数据集所使用的层次结构与在由 MDX 查询所返回的多维数据集中创建的层次结构区分开。</span><span class="sxs-lookup"><span data-stu-id="fab8e-108">Because query and slicer axes can be constructed from multiple hierarchies of the cube to be queried, these terms are used to differentiate the hierarchies used by the cube that is to be queried from the hierarchies created in the cube returned by an MDX query.</span></span>  
  
 <span data-ttu-id="fab8e-109">若要查看使用查询轴和切片器轴的简单示例，请参阅[在简单示例中使用查询轴和切片器轴 (MDX)](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)。</span><span class="sxs-lookup"><span data-stu-id="fab8e-109">To see a simple example using query and slicer axes, see [Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab8e-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fab8e-110">See Also</span></span>  
 <span data-ttu-id="fab8e-111">[使用成员、元组和集 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="fab8e-111">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 [<span data-ttu-id="fab8e-112">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="fab8e-112">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
