---
title: 聚合函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fcc65f1e60c29ba9ea6a4206b419eb0b13edb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587193"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a><span data-ttu-id="cd5f8-102">Aggregate 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="cd5f8-102">Aggregate Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cd5f8-103">按照数据访问接口的定义返回指定表达式的自定义聚合。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-103">Returns a custom aggregate of the specified expression, as defined by the data provider.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="cd5f8-104">语法</span><span class="sxs-lookup"><span data-stu-id="cd5f8-104">Syntax</span></span>  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd5f8-105">parameters</span><span class="sxs-lookup"><span data-stu-id="cd5f8-105">Parameters</span></span>  
 <span data-ttu-id="cd5f8-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="cd5f8-106">*expression*</span></span>  
 <span data-ttu-id="cd5f8-107">要对其执行聚合的表达式。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-107">The expression on which to perform the aggregation.</span></span> <span data-ttu-id="cd5f8-108">该表达式必须是简单字段引用表达式。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-108">The expression must be a simple field reference.</span></span>  
  
 <span data-ttu-id="cd5f8-109">*作用域*</span><span class="sxs-lookup"><span data-stu-id="cd5f8-109">*scope*</span></span>  
 <span data-ttu-id="cd5f8-110">(`String`) 包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-110">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="cd5f8-111">*Scope* 必须是字符串常量，且不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-111">*Scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="cd5f8-112">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-112">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="cd5f8-113">返回类型</span><span class="sxs-lookup"><span data-stu-id="cd5f8-113">Return Type</span></span>  
 <span data-ttu-id="cd5f8-114">返回类型视数据访问接口而定。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-114">Return type is determined by the data provider.</span></span> <span data-ttu-id="cd5f8-115">如果数据访问接口不支持此函数或数据不可用，则返回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-115">Returns `Nothing` if the data provider does not support this function or data is not available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd5f8-116">备注</span><span class="sxs-lookup"><span data-stu-id="cd5f8-116">Remarks</span></span>  
 <span data-ttu-id="cd5f8-117">`Aggregate` 函数提供一种方式来使用对外部数据源计算的聚合。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-117">The `Aggregate` function provides a way to use aggregates that are calculated on the external data source.</span></span> <span data-ttu-id="cd5f8-118">是否支持此功能由数据扩展插件决定。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-118">Support for this feature is determined by the data extension.</span></span> <span data-ttu-id="cd5f8-119">例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据处理扩展插件从 MDX 查询中检索平展行集。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-119">For example, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension retrieves flattened rowsets from an MDX query.</span></span> <span data-ttu-id="cd5f8-120">结果集中的某些行可能包含在数据源服务器上计算的聚合值。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-120">Some rows in the result set can contain aggregate values calculated on the data source server.</span></span> <span data-ttu-id="cd5f8-121">这些聚合值称为“服务器聚合”  。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-121">These are known as *server aggregates*.</span></span> <span data-ttu-id="cd5f8-122">若要在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的图形查询设计器中查看服务器聚合，可以使用工具栏上的 **“显示聚合”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-122">To view server aggregates in the graphical query designer for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the **Show Aggregate** button on the toolbar.</span></span> <span data-ttu-id="cd5f8-123">有关详细信息，请参阅 [Analysis Services MDX 查询设计器用户界面（报表生成器）](../analysis-services-mdx-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-123">For more information, see [Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="cd5f8-124">在 Tablix 数据区域的详细信息行中显示聚合和详细信息数据集值的组合时，服务器聚合通常不会包括在内，因为它们不是详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-124">When you display the combination of aggregate and detail dataset values on detail rows of a Tablix data region, server aggregates would not typically be included because they are not detail data.</span></span> <span data-ttu-id="cd5f8-125">但是，您可能希望显示从该数据集中检索到的所有值，并自定义聚合数据的计算方式和显示方式。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-125">However, you may want to display all values retrieved for the dataset and customize the way aggregate data is calculated and displayed.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="cd5f8-126">将检测在报表的表达式中使用 `Aggregate` 函数的情况，以便确定是否在详细信息行显示服务器聚合。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-126">detects the use of the `Aggregate` function in expressions in your report in order to determine whether to display server aggregates on detail rows.</span></span> <span data-ttu-id="cd5f8-127">如果在数据区域中的表达式中包含 `Aggregate`，服务器聚合只能出现在组总计行或总计行中，而不会出现在详细信息行中。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-127">If you include `Aggregate` in an expression in a data region, server aggregates can only appear on group total or grand total rows, not on detail rows.</span></span> <span data-ttu-id="cd5f8-128">如果您希望在详细信息行中显示服务器聚合，请不要使用 `Aggregate` 函数。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-128">If you want to display server aggregates on detail rows, do not use the `Aggregate` function.</span></span>  
  
 <span data-ttu-id="cd5f8-129">可以通过更改 **“将小计行解释为详细信息”** 选项（位于 **“数据集属性”** 对话框）的值，来更改此默认行为。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-129">You can change this default behavior by changing the value of the **Interpret subtotals as details** option on the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="cd5f8-130">此选项设置为 `True` 时，包括服务器聚合在内的所有数据都会显示为详细信息数据。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-130">When this option is set to `True`, all data, including server aggregates, appears as detail data.</span></span> <span data-ttu-id="cd5f8-131">当设置为 `False` 时，服务器聚合显示为总计。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-131">When set to `False`, server aggregates appear as totals.</span></span> <span data-ttu-id="cd5f8-132">此属性的设置影响链接到此数据集的所有数据区域。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-132">The setting for this property affects all data regions that are linked to this dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd5f8-133">引用 `Aggregate` 的报表项所包含的所有组都必须具有其组表达式的简单字段引用，例如，`[FieldName]`。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-133">All containing groups for the report item that references `Aggregate` must have simple field references for their group expressions, for example, `[FieldName]`.</span></span> <span data-ttu-id="cd5f8-134">您不能在使用复杂组表达式的数据区域中使用 `Aggregate`。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-134">You cannot use `Aggregate` in a data region that uses complex group expressions.</span></span> <span data-ttu-id="cd5f8-135">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据处理扩展插件，查询必须包括 `LevelProperty` 类型（不是 `MemberProperty` 类型）的 MDX 字段，才能支持使用 `Aggregate` 函数的聚合。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-135">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension, your query must include MDX fields of type `LevelProperty` (not `MemberProperty`) to support aggregation using the `Aggregate`function.</span></span>  
  
 <span data-ttu-id="cd5f8-136">*Expression* 可以包含对嵌套聚合函数的调用，但具有以下例外和条件：</span><span class="sxs-lookup"><span data-stu-id="cd5f8-136">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="cd5f8-137">嵌套聚合的*Scope* 必须与外部聚合的作用域相同，或者包含在外部聚合的作用域中。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-137">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="cd5f8-138">对于表达式中的所有非重复作用域，一个作用域必须相对所有其他作用域处于子关系中。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-138">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="cd5f8-139">嵌套聚合的*Scope* 不能为数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-139">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="cd5f8-140">*表达式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函数。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-140">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="cd5f8-141">*Expression* 不得包含用于指定 *recursive*的嵌套聚合。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-141">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="cd5f8-142">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-142">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="cd5f8-143">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-143">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a><span data-ttu-id="cd5f8-144">比较 Aggregate 函数和 Sum 函数</span><span class="sxs-lookup"><span data-stu-id="cd5f8-144">Comparing the Aggregate and Sum Functions</span></span>  
 <span data-ttu-id="cd5f8-145">`Aggregate` 函数不同于数值聚合函数（例如 `Sum`），区别在于 `Aggregate` 函数会返回由数据访问接口或数据处理扩展插件计算的值，</span><span class="sxs-lookup"><span data-stu-id="cd5f8-145">The `Aggregate` function differs from numeric aggregate functions like `Sum` in that the `Aggregate` function returns a value that is calculated by the data provider or data processing extension.</span></span> <span data-ttu-id="cd5f8-146">数值聚合函数（如） `Sum` 从由*scope*参数确定的数据集中的一组数据返回一个值。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-146">Numeric aggregate functions like `Sum` return a value that is calculated by the report processor on a set of data from the dataset that is determined by the *scope* parameter.</span></span> <span data-ttu-id="cd5f8-147">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)中列出的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-147">For more information, see the aggregate functions listed in [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd5f8-148">示例</span><span class="sxs-lookup"><span data-stu-id="cd5f8-148">Example</span></span>  
 <span data-ttu-id="cd5f8-149">下面的代码示例显示检索字段 `LineTotal`的服务器聚合的表达式。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-149">The following code example shows an expression that retrieves a server aggregate for the field `LineTotal`.</span></span> <span data-ttu-id="cd5f8-150">该表达式将添加至属于组 `GroupbyOrder`的行的某个单元格中。</span><span class="sxs-lookup"><span data-stu-id="cd5f8-150">The expression is added to a cell in a row that belongs to the group `GroupbyOrder`.</span></span>  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd5f8-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd5f8-151">See Also</span></span>  
 <span data-ttu-id="cd5f8-152">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f8-152">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd5f8-153">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f8-153">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd5f8-154">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd5f8-154">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cd5f8-155">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="cd5f8-155">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
