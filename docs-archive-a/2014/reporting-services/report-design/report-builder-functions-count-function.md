---
title: Count 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3617e64d804b6b0f3d9522b5a089f418a942568a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590047"
---
# <a name="count-function-report-builder-and-ssrs"></a><span data-ttu-id="469d0-102">Count 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="469d0-102">Count Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="469d0-103">返回在给定作用域上下文中计算的，由表达式指定的非 Null 值的计数。</span><span class="sxs-lookup"><span data-stu-id="469d0-103">Returns a count of non-null values specified by the expression, evaluated in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="469d0-104">语法</span><span class="sxs-lookup"><span data-stu-id="469d0-104">Syntax</span></span>  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="469d0-105">parameters</span><span class="sxs-lookup"><span data-stu-id="469d0-105">Parameters</span></span>  
 <span data-ttu-id="469d0-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="469d0-106">*expression*</span></span>  
 <span data-ttu-id="469d0-107">（`Variant` 或 `Binary`）要对其执行聚合的表达式，例如，`=Fields!FieldName.Value`。</span><span class="sxs-lookup"><span data-stu-id="469d0-107">(`Variant` or `Binary`) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.</span></span>  
  
 <span data-ttu-id="469d0-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="469d0-108">*scope*</span></span>  
 <span data-ttu-id="469d0-109">(`String`) 包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="469d0-109">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="469d0-110">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="469d0-110">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="469d0-111">*递归*</span><span class="sxs-lookup"><span data-stu-id="469d0-111">*recursive*</span></span>  
 <span data-ttu-id="469d0-112">(**Enumerated Type**) 可选。</span><span class="sxs-lookup"><span data-stu-id="469d0-112">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="469d0-113">`Simple`（默认值）或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="469d0-113">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="469d0-114">指定是否以递归方式执行聚合。</span><span class="sxs-lookup"><span data-stu-id="469d0-114">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="469d0-115">返回类型</span><span class="sxs-lookup"><span data-stu-id="469d0-115">Return Type</span></span>  
 <span data-ttu-id="469d0-116">返回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="469d0-116">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="469d0-117">备注</span><span class="sxs-lookup"><span data-stu-id="469d0-117">Remarks</span></span>  
 <span data-ttu-id="469d0-118">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="469d0-118">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="469d0-119">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="469d0-119">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="469d0-120">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="469d0-120">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="469d0-121">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="469d0-121">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="469d0-122">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="469d0-122">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="469d0-123">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="469d0-123">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="469d0-124">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="469d0-124">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="469d0-125">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="469d0-125">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="469d0-126">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="469d0-126">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="469d0-127">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="469d0-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="469d0-128">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="469d0-128">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="469d0-129">示例</span><span class="sxs-lookup"><span data-stu-id="469d0-129">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="469d0-130">说明</span><span class="sxs-lookup"><span data-stu-id="469d0-130">Description</span></span>  
 <span data-ttu-id="469d0-131">下面的代码示例显示一个表达式，该表达式为默认作用域和父组作用域计算 `Size` 的非 Null 值数。</span><span class="sxs-lookup"><span data-stu-id="469d0-131">The following code example shows an expression that calculates the number of non-null values of `Size` for the default scope and for a parent group scope.</span></span> <span data-ttu-id="469d0-132">该表达式将添加至属于子组 `GroupbySubcategory`的行的某个单元格中。</span><span class="sxs-lookup"><span data-stu-id="469d0-132">The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`.</span></span> <span data-ttu-id="469d0-133">父组是 `GroupbyCategory`。</span><span class="sxs-lookup"><span data-stu-id="469d0-133">The parent group is `GroupbyCategory`.</span></span> <span data-ttu-id="469d0-134">该表达式显示 `GroupbySubcategory` （默认作用域）和 `GroupbyCategory` （父组作用域）的结果。</span><span class="sxs-lookup"><span data-stu-id="469d0-134">The expression displays the results for `GroupbySubcategory` (the default scope) and then for `GroupbyCategory` (the parent group scope).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="469d0-135">表达式中不应包含实际的回车符和换行符；这些回车符和换行符包含在示例中是为了支持文档呈现器。</span><span class="sxs-lookup"><span data-stu-id="469d0-135">Expressions should not contain actual carriage returns and line breaks; these are included in the example to support documentation renderers.</span></span> <span data-ttu-id="469d0-136">如果您要复制以下示例，请删除每一行中的回车符。</span><span class="sxs-lookup"><span data-stu-id="469d0-136">If you copy the following example, remove carriage returns from each line.</span></span>  
  
## <a name="code"></a><span data-ttu-id="469d0-137">代码</span><span class="sxs-lookup"><span data-stu-id="469d0-137">Code</span></span>  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="469d0-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="469d0-138">See Also</span></span>  
 <span data-ttu-id="469d0-139">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="469d0-139">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="469d0-140">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="469d0-140">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="469d0-141">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="469d0-141">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="469d0-142">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="469d0-142">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
