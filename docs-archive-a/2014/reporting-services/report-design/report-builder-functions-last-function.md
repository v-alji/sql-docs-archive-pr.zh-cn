---
title: Last 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c343e72e476d4a717ca551eedeb0f02650479ca4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586413"
---
# <a name="last-function-report-builder-and-ssrs"></a><span data-ttu-id="c8060-102">Last 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c8060-102">Last Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c8060-103">返回指定表达式的给定作用域中的最后一个值。</span><span class="sxs-lookup"><span data-stu-id="c8060-103">Returns the last value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="c8060-104">语法</span><span class="sxs-lookup"><span data-stu-id="c8060-104">Syntax</span></span>  
  
```  
  
Last(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8060-105">parameters</span><span class="sxs-lookup"><span data-stu-id="c8060-105">Parameters</span></span>  
 <span data-ttu-id="c8060-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="c8060-106">*expression*</span></span>  
 <span data-ttu-id="c8060-107">（`Variant` 或 `Binary`）要对其执行聚合的表达式，例如，`=Fields!Fieldname.Value`。</span><span class="sxs-lookup"><span data-stu-id="c8060-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!Fieldname.Value`.</span></span>  
  
 <span data-ttu-id="c8060-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="c8060-108">*scope*</span></span>  
 <span data-ttu-id="c8060-109">(`String`)（可选）包含要对其应用该函数的报表项的数据集、数据区域或组的名称。</span><span class="sxs-lookup"><span data-stu-id="c8060-109">(`String`) (Optional) The name of a dataset, data region, or group that contains the report items to which to apply the function.</span></span> <span data-ttu-id="c8060-110">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="c8060-110">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="c8060-111">返回类型</span><span class="sxs-lookup"><span data-stu-id="c8060-111">Return Type</span></span>  
 <span data-ttu-id="c8060-112">视表达式的类型而定。</span><span class="sxs-lookup"><span data-stu-id="c8060-112">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8060-113">备注</span><span class="sxs-lookup"><span data-stu-id="c8060-113">Remarks</span></span>  
 <span data-ttu-id="c8060-114">在指定作用域中应用所有的排序和筛选后，`Last` 函数返回一组数据中的最后一个值。</span><span class="sxs-lookup"><span data-stu-id="c8060-114">The `Last` function returns the final value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="c8060-115">`Last` 函数只能用在当前作用域（默认）相关的组筛选表达式中。</span><span class="sxs-lookup"><span data-stu-id="c8060-115">The `Last` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="c8060-116">您还可以在页眉中使用 `Last` 函数，返回 `ReportItems` 集合中属于某页面的最后一个值，以便在页面中生成显示首项和尾项的字典样式标题。</span><span class="sxs-lookup"><span data-stu-id="c8060-116">You can also use `Last` in a page header to return the last value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="c8060-117">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="c8060-117">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="c8060-118">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="c8060-118">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="c8060-119">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="c8060-119">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="c8060-120">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="c8060-120">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="c8060-121">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="c8060-121">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="c8060-122">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="c8060-122">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="c8060-123">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="c8060-123">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="c8060-124">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="c8060-124">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="c8060-125">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="c8060-125">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="c8060-126">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="c8060-126">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="c8060-127">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c8060-127">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8060-128">示例</span><span class="sxs-lookup"><span data-stu-id="c8060-128">Example</span></span>  
 <span data-ttu-id="c8060-129">下面的代码示例返回数据区域 `Category` 组中的最后一个产品编号。</span><span class="sxs-lookup"><span data-stu-id="c8060-129">The following code example returns the last product number in the `Category` group of a data region.</span></span>  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8060-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8060-130">See Also</span></span>  
 <span data-ttu-id="c8060-131">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c8060-131">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c8060-132">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c8060-132">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c8060-133">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c8060-133">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c8060-134">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c8060-134">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
