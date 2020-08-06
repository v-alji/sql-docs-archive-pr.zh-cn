---
title: " (MDX) 操作数据 |Microsoft Docs"
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a1de8b9a3431d79573cd916fa7273b6d8fa7f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587059"
---
# <a name="manipulating-data-mdx"></a><span data-ttu-id="184bb-102">操作数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="184bb-102">Manipulating Data (MDX)</span></span>

<span data-ttu-id="184bb-103">多维表达式 (MDX) 可用于以多种方式处理数据。</span><span class="sxs-lookup"><span data-stu-id="184bb-103">Multidimensional Expressions (MDX) can be used to manipulate the data in a variety of ways.</span></span> <span data-ttu-id="184bb-104">本文中列出的文章介绍了 MDX 语言中数据操作的一些更高级的概念。</span><span class="sxs-lookup"><span data-stu-id="184bb-104">The article listed in this article cover some of the more advanced concepts of data manipulation in the MDX language.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="184bb-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="184bb-105">In This Section</span></span>

|<span data-ttu-id="184bb-106">主题</span><span class="sxs-lookup"><span data-stu-id="184bb-106">Topic</span></span>|<span data-ttu-id="184bb-107">说明</span><span class="sxs-lookup"><span data-stu-id="184bb-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="184bb-108">使用 DRILLTHROUGH 检索源数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="184bb-108">Using DRILLTHROUGH to Retrieve Source Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|<span data-ttu-id="184bb-109">介绍如何使用 MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) 语句检索适用于多维数据源中的某个单元的源数据行集。</span><span class="sxs-lookup"><span data-stu-id="184bb-109">Discusses the use of the MDX [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) statement to retrieve the rowsets of source data applicable to a cell in a multidimensional data source</span></span>|  
|[<span data-ttu-id="184bb-110">使用 RollupChildren 函数 (MDX)</span><span class="sxs-lookup"><span data-stu-id="184bb-110">Working with the RollupChildren Function &#40;MDX&#41;</span></span>](mdx-data-manipulation-rollupchildren-function.md)|<span data-ttu-id="184bb-111">讨论 MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)的影响</span><span class="sxs-lookup"><span data-stu-id="184bb-111">Discusses the impact of the MDX [RollupChildren](/sql/mdx/rollupchildren-mdx)</span></span>
|[<span data-ttu-id="184bb-112">理解传递顺序和求解次序 (MDX)</span><span class="sxs-lookup"><span data-stu-id="184bb-112">Understanding Pass Order and Solve Order &#40;MDX&#41;</span></span>](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|<span data-ttu-id="184bb-113">详细说明求解次序的概念，并介绍了此功能如何影响 MDX 表达式、语句和脚本。</span><span class="sxs-lookup"><span data-stu-id="184bb-113">Details the concepts of solve order, and how this feature affects MDX expressions, statements, and scripts.</span></span>|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a><span data-ttu-id="184bb-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="184bb-114">See Also</span></span>

[<span data-ttu-id="184bb-115">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="184bb-115">MDX Query Fundamentals (Analysis Services)</span></span>](mdx-query-fundamentals-analysis-services.md)
