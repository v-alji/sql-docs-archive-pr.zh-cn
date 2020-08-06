---
title: RunningValue 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 168073a0409455041f4ebe3aa4c5dcfc8fa129a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586394"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a><span data-ttu-id="6df32-102">RunningValue 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6df32-102">RunningValue Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6df32-103">返回在给定作用域中计算的，由表达式指定的所有非 Null 数值的运行聚合。</span><span class="sxs-lookup"><span data-stu-id="6df32-103">Returns a running aggregate of all non-null numeric values specified by the expression, evaluated for the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="6df32-104">语法</span><span class="sxs-lookup"><span data-stu-id="6df32-104">Syntax</span></span>  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6df32-105">parameters</span><span class="sxs-lookup"><span data-stu-id="6df32-105">Parameters</span></span>  
 <span data-ttu-id="6df32-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="6df32-106">*expression*</span></span>  
 <span data-ttu-id="6df32-107">要对其执行聚合的表达式，例如， `[Quantity]`。</span><span class="sxs-lookup"><span data-stu-id="6df32-107">The expression on which to perform the aggregation, for example, `[Quantity]`.</span></span>  
  
 <span data-ttu-id="6df32-108">*函数*</span><span class="sxs-lookup"><span data-stu-id="6df32-108">*function*</span></span>  
 <span data-ttu-id="6df32-109">(`Enum`) 要应用于表达式的聚合函数的名称，例如，`Sum`。</span><span class="sxs-lookup"><span data-stu-id="6df32-109">(`Enum`) The name of the aggregate function to apply to the expression, for example, `Sum`.</span></span> <span data-ttu-id="6df32-110">此函数不能为 `RunningValue`、`RowNumber` 或 `Aggregate`。</span><span class="sxs-lookup"><span data-stu-id="6df32-110">This function cannot be `RunningValue`, `RowNumber`, or `Aggregate`.</span></span>  
  
 <span data-ttu-id="6df32-111">*作用域*</span><span class="sxs-lookup"><span data-stu-id="6df32-111">*scope*</span></span>  
 <span data-ttu-id="6df32-112">(`String`) 一个字符串常量，表示数据集、数据区域或组的名称，也可以为 Null（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`），它指定在其中计算聚合的上下文。</span><span class="sxs-lookup"><span data-stu-id="6df32-112">(`String`) A string constant that is the name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the aggregation.</span></span> <span data-ttu-id="6df32-113">`Nothing` 指定最外层的上下文，通常为报表数据集。</span><span class="sxs-lookup"><span data-stu-id="6df32-113">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="6df32-114">返回类型</span><span class="sxs-lookup"><span data-stu-id="6df32-114">Return Type</span></span>  
 <span data-ttu-id="6df32-115">由 *function* 参数中指定的聚合函数确定。</span><span class="sxs-lookup"><span data-stu-id="6df32-115">Determined by the aggregate function that is specified in the *function* parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df32-116">备注</span><span class="sxs-lookup"><span data-stu-id="6df32-116">Remarks</span></span>  
 <span data-ttu-id="6df32-117">作用域的每个新实例 `RunningValue` 的值都会重置为 0。</span><span class="sxs-lookup"><span data-stu-id="6df32-117">The value for `RunningValue` resets to 0 for each new instance of the scope.</span></span> <span data-ttu-id="6df32-118">如果指定组，则会在更改组表达式时重置该运行值。</span><span class="sxs-lookup"><span data-stu-id="6df32-118">If a group is specified, the running value is reset when the group expression changes.</span></span> <span data-ttu-id="6df32-119">如果指定数据区域，则会为该数据区域的每个新实例重置该运行值。</span><span class="sxs-lookup"><span data-stu-id="6df32-119">If a data region is specified, the running value is reset for each new instance of the data region.</span></span> <span data-ttu-id="6df32-120">如果指定数据集，则不会在整个数据集中重置该运行值。</span><span class="sxs-lookup"><span data-stu-id="6df32-120">If a dataset is specified, the running value is not reset throughout the entire dataset.</span></span>  
  
 <span data-ttu-id="6df32-121">`RunningValue` 不能在筛选器或排序表达式中使用。</span><span class="sxs-lookup"><span data-stu-id="6df32-121">`RunningValue` cannot be used in a filter or sort expression.</span></span>  
  
 <span data-ttu-id="6df32-122">为其计算运行值的数据集必须具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6df32-122">The set of data for which the running value is calculated must have the same data type.</span></span> <span data-ttu-id="6df32-123">若要将具有多个数值数据类型的数据转换为同一数据类型，请使用类似 `CInt`、`CDbl` 或 `CDec` 的转换函数。</span><span class="sxs-lookup"><span data-stu-id="6df32-123">To convert data that has multiple numeric data types to the same data type, use conversion functions like `CInt`, `CDbl` or `CDec`.</span></span> <span data-ttu-id="6df32-124">有关详细信息，请参阅 [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142)（类型转换函数）。</span><span class="sxs-lookup"><span data-stu-id="6df32-124">For more information, see [Type Conversion Functions](https://go.microsoft.com/fwlink/?LinkId=96142).</span></span>  
  
 <span data-ttu-id="6df32-125">*Scope* 不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="6df32-125">*Scope* cannot be an expression.</span></span>  
  
 <span data-ttu-id="6df32-126">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="6df32-126">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="6df32-127">嵌套聚合的作用域必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="6df32-127">Scope for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="6df32-128">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="6df32-128">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="6df32-129">嵌套聚合的作用域不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="6df32-129">Scope for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="6df32-130">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="6df32-130">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="6df32-131">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="6df32-131">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="6df32-132">若要计算行数的运行值，请使用 `RowNumber`。</span><span class="sxs-lookup"><span data-stu-id="6df32-132">To calculate the running value of the number of rows, use `RowNumber`.</span></span> <span data-ttu-id="6df32-133">有关详细信息，请参阅 [RowNumber 函数（报表生成器和 SSRS）](report-builder-functions-rownumber-function.md)。</span><span class="sxs-lookup"><span data-stu-id="6df32-133">For more information, see [RowNumber Function &#40;Report Builder and SSRS&#41;](report-builder-functions-rownumber-function.md).</span></span>  
  
 <span data-ttu-id="6df32-134">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="6df32-134">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="6df32-135">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6df32-135">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6df32-136">示例</span><span class="sxs-lookup"><span data-stu-id="6df32-136">Examples</span></span>  
 <span data-ttu-id="6df32-137">下面的代码示例提供了最外层作用域（数据集）中名为 `Cost` 的字段的运行总和。</span><span class="sxs-lookup"><span data-stu-id="6df32-137">The following code example provides a running sum of the field named `Cost` in the outermost scope, which is the dataset.</span></span>  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 <span data-ttu-id="6df32-138">下面的代码示例提供了名为 `Score` 的数据集中名为 `DataSet1`的字段的运行总和。</span><span class="sxs-lookup"><span data-stu-id="6df32-138">The following code example provides a running sum of the field named `Score` in the dataset named `DataSet1`.</span></span>  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 <span data-ttu-id="6df32-139">下面的代码示例提供了最外层作用域中名为 `Traffic Charges` 的字段的运行总和。</span><span class="sxs-lookup"><span data-stu-id="6df32-139">The following code example provides a running sum of the field named `Traffic Charges` in the outermost scope.</span></span>  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6df32-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6df32-140">See Also</span></span>  
 <span data-ttu-id="6df32-141">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6df32-141">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6df32-142">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6df32-142">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6df32-143">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6df32-143">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6df32-144">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6df32-144">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
