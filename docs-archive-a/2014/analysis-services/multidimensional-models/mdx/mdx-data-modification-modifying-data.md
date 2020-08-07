---
title: " (MDX) 修改数据 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01df67471753922e3e7db39c56a9ed50aae900dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587623"
---
# <a name="modifying-data-mdx"></a><span data-ttu-id="c4324-102">修改数据 (MDX)</span><span class="sxs-lookup"><span data-stu-id="c4324-102">Modifying Data (MDX)</span></span>
  <span data-ttu-id="c4324-103">除了使用多维表达式 (MDX) 检索和处理维度数据和多维数据集数据以外，还可以使用 MDX 更新或“写回”\*\* 维度数据和多维数据集数据。</span><span class="sxs-lookup"><span data-stu-id="c4324-103">Besides using Multidimensional Expressions (MDX) to retrieve and handle data from dimensions and cubes, you can use MDX to update or *writeback* dimension and cube data.</span></span> <span data-ttu-id="c4324-104">这些更新可以是暂时的，例如对于推测分析或“假设”分析；也可以是永久的，例如当必须基于数据分析进行更改时。</span><span class="sxs-lookup"><span data-stu-id="c4324-104">These updates can be temporary, as with speculative, or "what if", analysis, or permanent, as when changes must occur based upon data analysis.</span></span>  
  
 <span data-ttu-id="c4324-105">数据的更新可以发生在维度级别或多维数据集级别：</span><span class="sxs-lookup"><span data-stu-id="c4324-105">Updates to data can occur at the dimension or cube level:</span></span>  
  
 <span data-ttu-id="c4324-106">**维度写回**</span><span class="sxs-lookup"><span data-stu-id="c4324-106">**Dimension writebacks**</span></span>  
 <span data-ttu-id="c4324-107">可以使用 [ALTER CUBE 语句 (MDX)](/sql/mdx/mdx-data-definition-alter-cube) 语句更改允许写操作的维度的数据，使用 [REFRESH CUBE 语句 (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) 反映属性值的删除、创建和更新。</span><span class="sxs-lookup"><span data-stu-id="c4324-107">You use the [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) statement to change a write-enabled dimension's data and the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to reflect the deletion, creation, and updating of attribute values.</span></span> <span data-ttu-id="c4324-108">还可以使用 ALTER CUBE 语句执行复杂的操作，如删除层次结构中的整个子树以及提升已删除成员的子级。</span><span class="sxs-lookup"><span data-stu-id="c4324-108">You can also use the ALTER CUBE statement to perform complex operations, such as deleting a whole sub-tree in a hierarchy and promoting the children of a deleted member.</span></span>  
  
 <span data-ttu-id="c4324-109">**多维数据集写回**</span><span class="sxs-lookup"><span data-stu-id="c4324-109">**Cube writebacks**</span></span>  
 <span data-ttu-id="c4324-110">可以使用 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) 语句更新启用写操作的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="c4324-110">You use the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement to make updates to a write-enabled cube.</span></span> <span data-ttu-id="c4324-111">UPDATE CUBE 语句允许您用特定的值更新元组。</span><span class="sxs-lookup"><span data-stu-id="c4324-111">The UPDATE CUBE statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="c4324-112">可以通过 [REFRESH CUBE 语句 (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) 用来自服务器的更新数据刷新客户端会话中的数据。</span><span class="sxs-lookup"><span data-stu-id="c4324-112">You use the [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) to refresh data in a client session with updated data from the server.</span></span>  
  
 <span data-ttu-id="c4324-113">有关详细信息，请参阅[使用多维数据集写回 (MDX)](mdx-data-modification-using-cube-writebacks.md)。</span><span class="sxs-lookup"><span data-stu-id="c4324-113">For more information, see [Using Cube Writebacks &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4324-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4324-114">See Also</span></span>  
 [<span data-ttu-id="c4324-115">MDX 查询基础知识 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c4324-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
