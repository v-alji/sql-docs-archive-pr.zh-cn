---
title: Union 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c80926be53254ec512b2189c4b67e8cd5885733f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586389"
---
# <a name="union-function-report-builder-and-ssrs"></a><span data-ttu-id="f1ba7-102">Union 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f1ba7-102">Union Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f1ba7-103">返回在给定作用域中计算的、由表达式指定的所有非 Null 数值的联合。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-103">Returns the union of all the non-null numeric values specified by the expression, evaluated in the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="f1ba7-104">语法</span><span class="sxs-lookup"><span data-stu-id="f1ba7-104">Syntax</span></span>  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1ba7-105">parameters</span><span class="sxs-lookup"><span data-stu-id="f1ba7-105">Parameters</span></span>  
 <span data-ttu-id="f1ba7-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="f1ba7-106">*expression*</span></span>  
 <span data-ttu-id="f1ba7-107">（`SqlGeometry` 或 `SqlGeography`）要对其执行聚合的表达式。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-107">(`SqlGeometry` or `SqlGeography`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="f1ba7-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="f1ba7-108">*scope*</span></span>  
 <span data-ttu-id="f1ba7-109">(`String`) 可选。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-109">(`String`) Optional.</span></span> <span data-ttu-id="f1ba7-110">包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="f1ba7-111">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="f1ba7-112">*递归*</span><span class="sxs-lookup"><span data-stu-id="f1ba7-112">*recursive*</span></span>  
 <span data-ttu-id="f1ba7-113">(**Enumerated Type**) 可选。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="f1ba7-114">`Simple`（默认值）或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="f1ba7-115">指定是否以递归方式执行聚合。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return"></a><span data-ttu-id="f1ba7-116">返回</span><span class="sxs-lookup"><span data-stu-id="f1ba7-116">Return</span></span>  
 <span data-ttu-id="f1ba7-117">`SqlGeometry`基于表达式类型返回或的空间对象 `SqlGeography` 。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-117">Returns a spatial object, either `SqlGeometry` or `SqlGeography`, based on the expression type.</span></span> <span data-ttu-id="f1ba7-118">有关 `SqlGeometry` 和 `SqlGeography` 空间数据类型的详细信息，请参阅[空间数据类型概述](../../relational-databases/spatial/spatial-data-types-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-118">For more information about `SqlGeometry` and `SqlGeography` spatial data types, see [Spatial Data Types Overview](../../relational-databases/spatial/spatial-data-types-overview.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1ba7-119">备注</span><span class="sxs-lookup"><span data-stu-id="f1ba7-119">Remarks</span></span>  
 <span data-ttu-id="f1ba7-120">表达式中指定的数据集必须具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-120">The set of data specified in the expression must have the same data type.</span></span>  
  
 <span data-ttu-id="f1ba7-121">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-121">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="f1ba7-122">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-122">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="f1ba7-123">不支持数据集作用域。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-123">Dataset scopes are not supported.</span></span> <span data-ttu-id="f1ba7-124">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="f1ba7-125">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="f1ba7-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="f1ba7-126">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="f1ba7-127">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="f1ba7-128">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="f1ba7-129">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="f1ba7-130">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="f1ba7-131">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="f1ba7-132">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ba7-133">示例</span><span class="sxs-lookup"><span data-stu-id="f1ba7-133">Example</span></span>  
 <span data-ttu-id="f1ba7-134">下表说明 `SqlGeometry` 表达式和 `Union` 结果表达式的示例，它们以空间数据的 WKT（熟知文本）格式显示。</span><span class="sxs-lookup"><span data-stu-id="f1ba7-134">The following table shows examples of `SqlGeometry` expressions and `Union` result expression, shown in WKT (Well Known Text) format for spatial data.</span></span>  
  
|<span data-ttu-id="f1ba7-135">具有空间数据的字段</span><span class="sxs-lookup"><span data-stu-id="f1ba7-135">Field with spatial data</span></span>|<span data-ttu-id="f1ba7-136">示例</span><span class="sxs-lookup"><span data-stu-id="f1ba7-136">Example</span></span>|<span data-ttu-id="f1ba7-137">UNION 结果</span><span class="sxs-lookup"><span data-stu-id="f1ba7-137">Union result</span></span>|  
|-----------------------------|-------------|------------------|  
|<span data-ttu-id="f1ba7-138">[PointLocation]</span><span class="sxs-lookup"><span data-stu-id="f1ba7-138">[PointLocation]</span></span>|<span data-ttu-id="f1ba7-139">POINT(1 2)</span><span class="sxs-lookup"><span data-stu-id="f1ba7-139">POINT(1 2)</span></span><br /><br /> <span data-ttu-id="f1ba7-140">POINT(3 4)</span><span class="sxs-lookup"><span data-stu-id="f1ba7-140">POINT(3 4)</span></span>|<span data-ttu-id="f1ba7-141">MULTIPOINT((1 2), (3 4))</span><span class="sxs-lookup"><span data-stu-id="f1ba7-141">MULTIPOINT((1 2), (3 4))</span></span>|  
|<span data-ttu-id="f1ba7-142">[PathDefinition]</span><span class="sxs-lookup"><span data-stu-id="f1ba7-142">[PathDefinition]</span></span>|<span data-ttu-id="f1ba7-143">LINESTRING(1 2, 3 4)</span><span class="sxs-lookup"><span data-stu-id="f1ba7-143">LINESTRING(1 2, 3 4)</span></span><br /><br /> <span data-ttu-id="f1ba7-144">LINESTRING(5 6, 7 8)</span><span class="sxs-lookup"><span data-stu-id="f1ba7-144">LINESTRING(5 6, 7 8)</span></span>|<span data-ttu-id="f1ba7-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span><span class="sxs-lookup"><span data-stu-id="f1ba7-145">MULTILINESTRING((7 8, 5 6), (3 4, 1 2))</span></span>|  
|<span data-ttu-id="f1ba7-146">[PolygonDefinition]</span><span class="sxs-lookup"><span data-stu-id="f1ba7-146">[PolygonDefinition]</span></span>|<span data-ttu-id="f1ba7-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span><span class="sxs-lookup"><span data-stu-id="f1ba7-147">POLYGON((1 2, 3 4, 5 2, 1 2))</span></span><br /><br /> <span data-ttu-id="f1ba7-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span><span class="sxs-lookup"><span data-stu-id="f1ba7-148">POLYGON((-1 2, -3 4, -5 2, -1 2))</span></span>|<span data-ttu-id="f1ba7-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span><span class="sxs-lookup"><span data-stu-id="f1ba7-149">MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))</span></span>|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1ba7-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1ba7-150">See Also</span></span>  
 <span data-ttu-id="f1ba7-151">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f1ba7-151">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f1ba7-152">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f1ba7-152">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f1ba7-153">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f1ba7-153">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f1ba7-154">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f1ba7-154">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
