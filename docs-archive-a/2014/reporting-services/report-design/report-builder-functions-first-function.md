---
title: First 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0914520-30c5-4d63-9b59-8d9342ed63b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cd8578a1d9a17030d603457d4eaadf107316bdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586416"
---
# <a name="first-function-report-builder-and-ssrs"></a><span data-ttu-id="05088-102">First 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="05088-102">First Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="05088-103">返回指定表达式的给定作用域中的第一个值。</span><span class="sxs-lookup"><span data-stu-id="05088-103">Returns the first value in the given scope of the specified expression.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="05088-104">语法</span><span class="sxs-lookup"><span data-stu-id="05088-104">Syntax</span></span>  
  
```  
  
First(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05088-105">parameters</span><span class="sxs-lookup"><span data-stu-id="05088-105">Parameters</span></span>  
 <span data-ttu-id="05088-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="05088-106">*expression*</span></span>  
 <span data-ttu-id="05088-107">（`Variant` 或 `Binary`）要对其执行聚合的表达式，例如，`=Fields!FieldName.Value`。</span><span class="sxs-lookup"><span data-stu-id="05088-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.</span></span>  
  
 <span data-ttu-id="05088-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="05088-108">*scope*</span></span>  
 <span data-ttu-id="05088-109">(`String`) 可选。</span><span class="sxs-lookup"><span data-stu-id="05088-109">(`String`) Optional.</span></span> <span data-ttu-id="05088-110">包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="05088-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="05088-111">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="05088-111">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="05088-112">返回类型</span><span class="sxs-lookup"><span data-stu-id="05088-112">Return Type</span></span>  
 <span data-ttu-id="05088-113">视表达式的类型而定。</span><span class="sxs-lookup"><span data-stu-id="05088-113">Determined by the type of expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05088-114">备注</span><span class="sxs-lookup"><span data-stu-id="05088-114">Remarks</span></span>  
 <span data-ttu-id="05088-115">`First` 函数返回在指定作用域中应用所有排序和筛选后的一组数据的第一个值。</span><span class="sxs-lookup"><span data-stu-id="05088-115">The `First` function returns the first value in a set of data after all sorting and filtering have been applied at the specified scope.</span></span>  
  
 <span data-ttu-id="05088-116">`First` 函数只能用在当前作用域（默认）相关的组筛选表达式中。</span><span class="sxs-lookup"><span data-stu-id="05088-116">The `First` function cannot be used in group filter expressions with anything except the current (default) scope.</span></span>  
  
 <span data-ttu-id="05088-117">您还可以在页眉中使用 `First` 函数，返回 `ReportItems` 集合中属于某页面的第一个值，以便在页面中生成显示首项和尾项的字典样式标题。</span><span class="sxs-lookup"><span data-stu-id="05088-117">You can also use `First` in a page header to return the first value from the `ReportItems` collection for a page in order to produce dictionary-style headings that display the first and last entries on a page.</span></span>  
  
 <span data-ttu-id="05088-118">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="05088-118">The value of *scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="05088-119">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="05088-119">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="05088-120">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="05088-120">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="05088-121">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="05088-121">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="05088-122">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="05088-122">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="05088-123">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="05088-123">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="05088-124">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="05088-124">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="05088-125">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="05088-125">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="05088-126">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="05088-126">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="05088-127">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="05088-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="05088-128">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="05088-128">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05088-129">示例</span><span class="sxs-lookup"><span data-stu-id="05088-129">Example</span></span>  
 <span data-ttu-id="05088-130">下面的代码示例返回数据区域 `Category` 组中的第一个产品编号：</span><span class="sxs-lookup"><span data-stu-id="05088-130">The following code example returns the first product number in the `Category` group of a data region:</span></span>  
  
```  
=First(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a><span data-ttu-id="05088-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05088-131">See Also</span></span>  
 <span data-ttu-id="05088-132">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="05088-132">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="05088-133">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="05088-133">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="05088-134">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="05088-134">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="05088-135">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="05088-135">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
