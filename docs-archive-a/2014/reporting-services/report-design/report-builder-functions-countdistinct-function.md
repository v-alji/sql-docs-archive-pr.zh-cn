---
title: CountDistinct 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 902c251e-e1e8-41d2-ac20-5bb6138ac410
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62fab53d4f26a874ac40e0a915c4242a41c72ce0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586425"
---
# <a name="countdistinct-function-report-builder-and-ssrs"></a><span data-ttu-id="6e8b7-102">CountDistinct 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6e8b7-102">CountDistinct Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6e8b7-103">返回在给定作用域上下文中计算的，由表达式指定的所有非重复的非 Null 值计数。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-103">Returns a count of all distinct non-null values specified by the expression, evaluated in the context of the given scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="6e8b7-104">语法</span><span class="sxs-lookup"><span data-stu-id="6e8b7-104">Syntax</span></span>  
  
```  
  
CountDistinct(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e8b7-105">parameters</span><span class="sxs-lookup"><span data-stu-id="6e8b7-105">Parameters</span></span>  
 <span data-ttu-id="6e8b7-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="6e8b7-106">*expression*</span></span>  
 <span data-ttu-id="6e8b7-107">(`Variant`) 要对其执行聚合的表达式。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-107">(`Variant`) The expression on which to perform the aggregation.</span></span>  
  
 <span data-ttu-id="6e8b7-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="6e8b7-108">*scope*</span></span>  
 <span data-ttu-id="6e8b7-109">(`String`) 可选。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-109">(`String`) Optional.</span></span> <span data-ttu-id="6e8b7-110">包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-110">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="6e8b7-111">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-111">If *scope* is not specified, the current scope is used.</span></span>  
  
 <span data-ttu-id="6e8b7-112">*递归*</span><span class="sxs-lookup"><span data-stu-id="6e8b7-112">*recursive*</span></span>  
 <span data-ttu-id="6e8b7-113">(**Enumerated Type**) 可选。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-113">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="6e8b7-114">`Simple`（默认值）或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-114">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="6e8b7-115">指定是否以递归方式执行聚合。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-115">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="6e8b7-116">返回类型</span><span class="sxs-lookup"><span data-stu-id="6e8b7-116">Return Type</span></span>  
 <span data-ttu-id="6e8b7-117">返回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-117">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e8b7-118">备注</span><span class="sxs-lookup"><span data-stu-id="6e8b7-118">Remarks</span></span>  
 <span data-ttu-id="6e8b7-119">*scope* 的值必须是字符串常量，不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-119">The value of *scope* must be a string constant and cannot be an expression.</span></span> <span data-ttu-id="6e8b7-120">对于外部聚合或未指定其他聚合的聚合， *scope* 必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-120">For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope.</span></span> <span data-ttu-id="6e8b7-121">对于聚合的聚合，嵌套聚合可以指定子作用域。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-121">For aggregates of aggregates, nested aggregates can specify a child scope.</span></span>  
  
 <span data-ttu-id="6e8b7-122">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="6e8b7-122">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="6e8b7-123">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-123">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="6e8b7-124">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-124">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="6e8b7-125">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-125">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="6e8b7-126">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-126">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="6e8b7-127">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-127">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="6e8b7-128">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-128">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="6e8b7-129">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-129">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e8b7-130">示例</span><span class="sxs-lookup"><span data-stu-id="6e8b7-130">Example</span></span>  
 <span data-ttu-id="6e8b7-131">下面的代码示例显示一个表达式，该表达式为默认作用域和父组作用域计算 `Size` 的唯一非 Null 值数。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-131">The following code example shows an expression that calculates the number of unique non-null values of `Size` for the default scope and for a parent group scope.</span></span> <span data-ttu-id="6e8b7-132">该表达式将添加至属于子组 `GroupbySubcategory`的行的某个单元格中。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-132">The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`.</span></span> <span data-ttu-id="6e8b7-133">父组是 `GroupbyCategory`。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-133">The parent group is `GroupbyCategory`.</span></span> <span data-ttu-id="6e8b7-134">该表达式显示 `GroupbySubcategory` （默认作用域）和 `GroupbyCategory` （父组作用域）的结果。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-134">The expression displays the results for `GroupbySubcategory` (the default scope) and then for `GroupbyCategory` (the parent group scope).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e8b7-135">表达式中不应包含实际的回车符和换行符；这些回车符和换行符包含在示例代码中是为了支持文档呈现器。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-135">Expressions should not contain actual carriage returns and line breaks; these are included in the example code to support documentation renderers.</span></span> <span data-ttu-id="6e8b7-136">如果您要复制以下示例，请删除每一行中的回车符。</span><span class="sxs-lookup"><span data-stu-id="6e8b7-136">If you copy the following example, remove carriage returns from each line.</span></span>  
  
```  
="Distinct count (Subcategory): " & CountDistinct(Fields!Size.Value) &   
"Distinct count (Category): " & CountDistinct(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e8b7-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e8b7-137">See Also</span></span>  
 <span data-ttu-id="6e8b7-138">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e8b7-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e8b7-139">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e8b7-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e8b7-140">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e8b7-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6e8b7-141">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6e8b7-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
