---
title: 查询最近的邻域的空间数据 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 644b3e5cfdaeff7457639bc2da77260b64011735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590654"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a><span data-ttu-id="44b7e-102">为 Nearest Neighbor 查询空间数据</span><span class="sxs-lookup"><span data-stu-id="44b7e-102">Query Spatial Data for Nearest Neighbor</span></span>
  <span data-ttu-id="44b7e-103">Nearest Neighbor 查询是用于空间数据的常用查询。</span><span class="sxs-lookup"><span data-stu-id="44b7e-103">A common query used with spatial data is the Nearest Neighbor query.</span></span> <span data-ttu-id="44b7e-104">Nearest Neighbor 查询用于查找与特定的空间对象最接近的空间对象。</span><span class="sxs-lookup"><span data-stu-id="44b7e-104">Nearest Neighbor queries are used to find the closest spatial objects to a specific spatial object.</span></span> <span data-ttu-id="44b7e-105">例如，网站的存储区定位器必须时常查找与客户位置最接近的存储区位置。</span><span class="sxs-lookup"><span data-stu-id="44b7e-105">For example a store locater for a Web site often must find the closest store locations to a customer location.</span></span>  
  
 <span data-ttu-id="44b7e-106">可以用多种有效查询格式编写 Nearest Neighbor 查询，但是要使 Nearest Neighbor 查询使用空间索引，则必须使用下面的语法。</span><span class="sxs-lookup"><span data-stu-id="44b7e-106">A Nearest Neighbor query can be written in a variety of valid query formats, but for the Nearest Neighbor query to use a spatial index the following syntax must be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b7e-107">语法</span><span class="sxs-lookup"><span data-stu-id="44b7e-107">Syntax</span></span>  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a><span data-ttu-id="44b7e-108">Nearest Neighbor 查询和空间索引</span><span class="sxs-lookup"><span data-stu-id="44b7e-108">Nearest Neighbor Query and Spatial Indexes</span></span>  
 <span data-ttu-id="44b7e-109">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，使用 `TOP` 和 `ORDER BY` 子句对空间数据列执行 Nearest Neighbor 查询。</span><span class="sxs-lookup"><span data-stu-id="44b7e-109">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `TOP` and `ORDER BY` clauses are used to perform a Nearest Neighbor query on spatial data columns.</span></span> <span data-ttu-id="44b7e-110">对于空间列数据类型，`ORDER BY` 子句包含对 `STDistance()` 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="44b7e-110">The `ORDER BY` clause contains a call to the `STDistance()` method for the spatial column data type.</span></span> <span data-ttu-id="44b7e-111">`TOP` 子句指示针对该查询要返回的对象数。</span><span class="sxs-lookup"><span data-stu-id="44b7e-111">The `TOP` clause indicates the number of objects to return for the query.</span></span>  
  
 <span data-ttu-id="44b7e-112">为了使 Nearest Neighbor 查询使用空间索引，必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="44b7e-112">The following requirements must be met for a Nearest Neighbor query to use a spatial index:</span></span>  
  
1.  <span data-ttu-id="44b7e-113">空间索引必须存在于其中一个空间列上，并且 `STDistance()` 方法必须在 `WHERE` 和 `ORDER BY` 子句中使用该空间列。</span><span class="sxs-lookup"><span data-stu-id="44b7e-113">A spatial index must be present on one of the spatial columns and the `STDistance()` method must use that column in the `WHERE` and `ORDER BY` clauses.</span></span>  
  
2.  <span data-ttu-id="44b7e-114">`TOP` 子句不能包含 `PERCENT` 语句。</span><span class="sxs-lookup"><span data-stu-id="44b7e-114">The `TOP` clause cannot contain a `PERCENT` statement.</span></span>  
  
3.  <span data-ttu-id="44b7e-115">`WHERE` 子句必须包含 `STDistance()` 方法。</span><span class="sxs-lookup"><span data-stu-id="44b7e-115">The `WHERE` clause must contain a `STDistance()` method.</span></span>  
  
4.  <span data-ttu-id="44b7e-116">如果 `WHERE` 子句中有多个谓词，则必须使用 `AND` 连词将包含 `STDistance()` 方法的谓词连接到其他谓词。</span><span class="sxs-lookup"><span data-stu-id="44b7e-116">If there are multiple predicates in the `WHERE` clause then the predicate containing `STDistance()` method must be connected by an `AND` conjunction to the other predicates.</span></span> <span data-ttu-id="44b7e-117">`STDistance()` 方法不能是 `WHERE` 子句的可选部分。</span><span class="sxs-lookup"><span data-stu-id="44b7e-117">The `STDistance()` method cannot be in an optional part of the `WHERE` clause.</span></span>  
  
5.  <span data-ttu-id="44b7e-118">`ORDER BY` 子句中的第一个表达式必须使用 `STDistance()` 方法。</span><span class="sxs-lookup"><span data-stu-id="44b7e-118">The first expression in the `ORDER BY` clause must use the `STDistance()` method.</span></span>  
  
6.  <span data-ttu-id="44b7e-119">`ORDER BY` 子句中第一个 `STDistance()` 表达式的排序顺序必须是 `ASC`。</span><span class="sxs-lookup"><span data-stu-id="44b7e-119">Sort order for the first `STDistance()` expression in the `ORDER BY` clause must be `ASC`.</span></span>  
  
7.  <span data-ttu-id="44b7e-120">必须筛选掉 `STDistance` 返回 `NULL` 的所有行。</span><span class="sxs-lookup"><span data-stu-id="44b7e-120">All the rows for which `STDistance` returns `NULL` must be filtered out.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="44b7e-121">将 `geography` 或 `geometry` 数据类型作为参数的方法将返回 `NULL`，前提是 SRID 对于这些数据类型不同。</span><span class="sxs-lookup"><span data-stu-id="44b7e-121">Methods that take `geography` or `geometry` data types as arguments will return `NULL` if the SRIDs are not the same for the types.</span></span>  
  
 <span data-ttu-id="44b7e-122">建议将新的空间索引分割用于在 Nearest Neighbor 查询中使用的索引。</span><span class="sxs-lookup"><span data-stu-id="44b7e-122">It is recommended that the new spatial index tessellations be used for indexes used in Nearest Neighbor queries.</span></span> <span data-ttu-id="44b7e-123">有关空间索引分割的详细信息，请参阅 [空间数据 (SQL Server)](spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="44b7e-123">For more information on spatial index tessellations, see [Spatial Data &#40;SQL Server&#41;](spatial-data-sql-server.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b7e-124">示例</span><span class="sxs-lookup"><span data-stu-id="44b7e-124">Example</span></span>  
 <span data-ttu-id="44b7e-125">下面的代码示例显示可以使用空间索引的 Nearest Neighbor 查询。</span><span class="sxs-lookup"><span data-stu-id="44b7e-125">The following code example shows a Nearest Neighbor query that can use a spatial index.</span></span> <span data-ttu-id="44b7e-126">该示例使用 `Person.Address` 数据库中的 `AdventureWorks2012` 表。</span><span class="sxs-lookup"><span data-stu-id="44b7e-126">The example uses the `Person.Address` table in `AdventureWorks2012` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="44b7e-127">在 SpatialLocation 列上创建一个空间索引，以便了解 Nearest Neighbor 查询如何使用空间索引。</span><span class="sxs-lookup"><span data-stu-id="44b7e-127">Create a spatial index on the column SpatialLocation to see how a Nearest Neighbor query uses a spatial index.</span></span> <span data-ttu-id="44b7e-128">有关创建空间索引的详细信息，请参阅 [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="44b7e-128">For more information on creating spatial indexes, see [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b7e-129">示例</span><span class="sxs-lookup"><span data-stu-id="44b7e-129">Example</span></span>  
 <span data-ttu-id="44b7e-130">下面的代码示例显示不能使用空间索引的 Nearest Neighbor 查询。</span><span class="sxs-lookup"><span data-stu-id="44b7e-130">The following code example shows a Nearest Neighbor query that cannot use a spatial index.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="44b7e-131">该查询缺少在语法部分中指定的窗体中使用 `STDistance()` 的 `WHERE` 子句，因此它无法使用空间索引。</span><span class="sxs-lookup"><span data-stu-id="44b7e-131">The query lacks a `WHERE` clause that uses `STDistance()` in a form specified in the syntax section so the query cannot use a spatial index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b7e-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44b7e-132">See Also</span></span>  
 [<span data-ttu-id="44b7e-133">空间数据 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="44b7e-133">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
