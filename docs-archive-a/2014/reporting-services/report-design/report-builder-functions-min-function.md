---
title: Min 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa1ee96f-9fc4-4775-b9d4-c6187dc37e27
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 82bb852eeb334a0c7bde3e157f0035db766039da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586409"
---
# <a name="min-function-report-builder-and-ssrs"></a><span data-ttu-id="74d93-102">Min 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="74d93-102">Min Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="74d93-103">返回在给定作用域上下文中由表达式指定的所有非 Null 数值的最小值。</span><span class="sxs-lookup"><span data-stu-id="74d93-103">Returns the minimum value of all non-null numeric values specified by the expression, in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="74d93-104">语法</span><span class="sxs-lookup"><span data-stu-id="74d93-104">Syntax</span></span>  
  
```  
  
Min(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74d93-105">parameters</span><span class="sxs-lookup"><span data-stu-id="74d93-105">Parameters</span></span>  
 <span data-ttu-id="74d93-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="74d93-106">*expression*</span></span>  
 <span data-ttu-id="74d93-107">(`Variant`) 要对其执行聚合的表达式。</span><span class="sxs-lookup"><span data-stu-id="74d93-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="74d93-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="74d93-108">*scope*</span></span>  
 <span data-ttu-id="74d93-109">(`String`) 可选。</span><span class="sxs-lookup"><span data-stu-id="74d93-109">(`String`) Optional.</span></span> <span data-ttu-id="74d93-110">包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="74d93-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="74d93-111">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="74d93-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="74d93-112">*递归*</span><span class="sxs-lookup"><span data-stu-id="74d93-112">*recursive*</span></span>  
 <span data-ttu-id="74d93-113">(**Enumerated Type**) 可选。</span><span class="sxs-lookup"><span data-stu-id="74d93-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="74d93-114">`Simple`（默认值）或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="74d93-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="74d93-115">指定是否以递归方式执行聚合。</span><span class="sxs-lookup"><span data-stu-id="74d93-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="74d93-116">返回类型</span><span class="sxs-lookup"><span data-stu-id="74d93-116">Return Type</span></span>  
 <span data-ttu-id="74d93-117">视表达式的类型而定。</span><span class="sxs-lookup"><span data-stu-id="74d93-117">Determined by the type of the expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74d93-118">备注</span><span class="sxs-lookup"><span data-stu-id="74d93-118">Remarks</span></span>  
 <span data-ttu-id="74d93-119">表达式中指定的数据集必须具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="74d93-119">The set of data specified in the expression must have the same data type.</span></span> <span data-ttu-id="74d93-120">若要将具有多个数值数据类型的数据转换为同一数据类型，请使用类似 `CInt`、`CDbl` 或 `CDec` 的转换函数。</span><span class="sxs-lookup"><span data-stu-id="74d93-120">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="74d93-121">有关详细信息，请参阅 [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142)（类型转换函数）。</span><span class="sxs-lookup"><span data-stu-id="74d93-121">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="74d93-122">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="74d93-122">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="74d93-123">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="74d93-123">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="74d93-124">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="74d93-124">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="74d93-125">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="74d93-125">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="74d93-126">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="74d93-126">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="74d93-127">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="74d93-127">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="74d93-128">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="74d93-128">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="74d93-129">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="74d93-129">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="74d93-130">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="74d93-130">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="74d93-131">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="74d93-131">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="74d93-132">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="74d93-132">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d93-133">示例</span><span class="sxs-lookup"><span data-stu-id="74d93-133">Example</span></span>  
 <span data-ttu-id="74d93-134">下面的代码示例提供当前作用域中的最小总数。</span><span class="sxs-lookup"><span data-stu-id="74d93-134">The following code example provides the lowest total in the current scope.</span></span>  
  
```  
=Min(Fields!OrderTotal.Value)  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d93-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74d93-135">See Also</span></span>  
 <span data-ttu-id="74d93-136">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="74d93-136">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="74d93-137">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="74d93-137">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="74d93-138">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="74d93-138">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="74d93-139">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="74d93-139">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
