---
title: Previous 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3891deec3f152cdf46da77a7f2d11d38387c5c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586402"
---
# <a name="previous-function-report-builder-and-ssrs"></a><span data-ttu-id="76f0e-102">Previous 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="76f0e-102">Previous Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="76f0e-103">返回指定作用域内某项的前一个实例的值或该实例的指定聚合值。</span><span class="sxs-lookup"><span data-stu-id="76f0e-103">Returns the value or the specified aggregate value for the previous instance of an item within the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="76f0e-104">语法</span><span class="sxs-lookup"><span data-stu-id="76f0e-104">Syntax</span></span>  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76f0e-105">parameters</span><span class="sxs-lookup"><span data-stu-id="76f0e-105">Parameters</span></span>  
 <span data-ttu-id="76f0e-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="76f0e-106">*expression*</span></span>  
 <span data-ttu-id="76f0e-107">（`Variant` 或 `Binary`）用于标识数据和检索以前值的表达式，例如 `Fields!Fieldname.Value` 或 `Sum(Fields!Fieldname.Value)`。</span><span class="sxs-lookup"><span data-stu-id="76f0e-107">(`Variant` or `Binary`) The expression to use to identify the data and for which to retrieve the previous value, for example, `Fields!Fieldname.Value` or `Sum(Fields!Fieldname.Value)`.</span></span>  
  
 <span data-ttu-id="76f0e-108">*作用域*</span><span class="sxs-lookup"><span data-stu-id="76f0e-108">*scope*</span></span>  
 <span data-ttu-id="76f0e-109">(`String`) 可选。</span><span class="sxs-lookup"><span data-stu-id="76f0e-109">(`String`) Optional.</span></span> <span data-ttu-id="76f0e-110">组或数据区域的名称，或者为 null (`Nothing` 在) 中， [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 指定要从中检索*expression*指定的以前值的作用域。</span><span class="sxs-lookup"><span data-stu-id="76f0e-110">The name of a group or data region, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the scope from which to retrieve the previous value specified by *expression*.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="76f0e-111">返回类型</span><span class="sxs-lookup"><span data-stu-id="76f0e-111">Return Type</span></span>  
 <span data-ttu-id="76f0e-112">返回 `Variant` 或 `Binary`。</span><span class="sxs-lookup"><span data-stu-id="76f0e-112">Returns a `Variant` or `Binary`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76f0e-113">备注</span><span class="sxs-lookup"><span data-stu-id="76f0e-113">Remarks</span></span>  
 <span data-ttu-id="76f0e-114">`Previous` 函数返回在应用所有排序和筛选之后，指定作用域内计算的表达式的前一个值。</span><span class="sxs-lookup"><span data-stu-id="76f0e-114">The `Previous` function returns the previous value for the expression evaluated in the specified scope after all sorting and filtering have been applied.</span></span>  
  
 <span data-ttu-id="76f0e-115">如果*expression*不包含聚合，则 `Previous` 函数默认为报表项的当前作用域。</span><span class="sxs-lookup"><span data-stu-id="76f0e-115">If *expression* does not contain an aggregate, the `Previous` function defaults to the current scope for the report item.</span></span>  
  
 <span data-ttu-id="76f0e-116">在详细信息组中，使用 `Previous` 可以在详细信息行的前一实例中指定字段引用的值。</span><span class="sxs-lookup"><span data-stu-id="76f0e-116">In a details group, use `Previous` to specify the value of a field reference in the previous instance of the detail row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76f0e-117">`Previous`函数只支持详细信息组中的字段引用。</span><span class="sxs-lookup"><span data-stu-id="76f0e-117">The `Previous` function only supports field references in the details group.</span></span> <span data-ttu-id="76f0e-118">例如，在详细信息组的文本框中， `=Previous(Fields!Quantity.Value)` 将返回上一行中 `Quantity` 字段的数据。</span><span class="sxs-lookup"><span data-stu-id="76f0e-118">For example, in a text box in the details group, `=Previous(Fields!Quantity.Value)` returns the data for the field `Quantity` from the previous row.</span></span> <span data-ttu-id="76f0e-119">在第一行中，此表达式返回一个 Null（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="76f0e-119">In the first row, this expression returns a null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  
  
 <span data-ttu-id="76f0e-120">如果*expression*包含使用默认作用域的聚合函数，则 `Previous` 聚合聚合函数调用中指定的作用域的前一个实例内的数据。</span><span class="sxs-lookup"><span data-stu-id="76f0e-120">If *expression* contains an aggregate function that uses a default scope, `Previous` aggregates the data within the previous instance of the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="76f0e-121">如果*expression*包含指定非默认作用域的聚合函数，则该函数的*作用域*参数 `Previous` 必须是聚合函数调用中指定的作用域的包含作用域。</span><span class="sxs-lookup"><span data-stu-id="76f0e-121">If *expression* contains an aggregate function that specifies a scope other than the default, the *scope* parameter for the `Previous` function must be a containing scope for the scope specified in the aggregate function call.</span></span>  
  
 <span data-ttu-id="76f0e-122">`Level` `InScope` `Aggregate` `Previous` 在*expression*参数中不能使用函数、和。</span><span class="sxs-lookup"><span data-stu-id="76f0e-122">The functions `Level`, `InScope`, `Aggregate` and `Previous` cannot be used in the *expression*parameter.</span></span> <span data-ttu-id="76f0e-123">不支持将 *recursive* 参数指定给任何聚合函数。</span><span class="sxs-lookup"><span data-stu-id="76f0e-123">Specifying the *recursive* parameter for any aggregate function is not supported.</span></span>  
  
 <span data-ttu-id="76f0e-124">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="76f0e-124">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76f0e-125">示例</span><span class="sxs-lookup"><span data-stu-id="76f0e-125">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="76f0e-126">说明</span><span class="sxs-lookup"><span data-stu-id="76f0e-126">Description</span></span>  
 <span data-ttu-id="76f0e-127">下面的代码示例置于数据区域的默认数据行时，提供上一行中 `LineTotal` 字段的值。</span><span class="sxs-lookup"><span data-stu-id="76f0e-127">The following code example, when placed in the default data row of a data region, provides the value for the field `LineTotal` in the previous row.</span></span>  
  
### <a name="code"></a><span data-ttu-id="76f0e-128">代码</span><span class="sxs-lookup"><span data-stu-id="76f0e-128">Code</span></span>  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a><span data-ttu-id="76f0e-129">说明</span><span class="sxs-lookup"><span data-stu-id="76f0e-129">Description</span></span>  
 <span data-ttu-id="76f0e-130">下面的示例显示一个表达式，该表达式计算某月特定天的销售额和上一年该月该天的销售额的总和。</span><span class="sxs-lookup"><span data-stu-id="76f0e-130">The following example shows an expression that calculates the sum of sales on a specific day of the month and the previous value for that day of the month in a previous year.</span></span> <span data-ttu-id="76f0e-131">该表达式将添加至属于子组 `GroupbyDay`的行的某个单元格中。</span><span class="sxs-lookup"><span data-stu-id="76f0e-131">The expression is added to a cell in a row that belongs to the child group `GroupbyDay`.</span></span> <span data-ttu-id="76f0e-132">它的父组是 `GroupbyMonth`，该父组的父组是 `GroupbyYear`。</span><span class="sxs-lookup"><span data-stu-id="76f0e-132">Its parent group is `GroupbyMonth`, which has a parent group `GroupbyYear`.</span></span> <span data-ttu-id="76f0e-133">该表达式显示 GroupbyDay（默认作用域）和 `GroupbyYear` （父组 `GroupbyMonth`的父组）的结果。</span><span class="sxs-lookup"><span data-stu-id="76f0e-133">The expression displays the results for GroupbyDay (the default scope) and then for `GroupbyYear` (the parent of the parent group `GroupbyMonth`).</span></span>  
  
 <span data-ttu-id="76f0e-134">例如，对于具有名为 `Year`的父组的数据区域，其子组名为 `Month`，子组的子组名为 `Day` （3 个嵌套级别）。</span><span class="sxs-lookup"><span data-stu-id="76f0e-134">For example, for a data region with a parent group named `Year`, its child group named `Month`, and its child group named `Day` (3 nested levels).</span></span> <span data-ttu-id="76f0e-135">与组 `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` 关联的行中的表达式 `Day` 返回上一年同一月同一天的销售额值。</span><span class="sxs-lookup"><span data-stu-id="76f0e-135">The expression `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in a row associated with the group `Day` returns the sales value for the same day and month for the previous year.</span></span>  
  
### <a name="code"></a><span data-ttu-id="76f0e-136">代码</span><span class="sxs-lookup"><span data-stu-id="76f0e-136">Code</span></span>  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a><span data-ttu-id="76f0e-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76f0e-137">See Also</span></span>  
 <span data-ttu-id="76f0e-138">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76f0e-138">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="76f0e-139">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76f0e-139">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="76f0e-140">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76f0e-140">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="76f0e-141">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="76f0e-141">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
