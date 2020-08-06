---
title: RowNumber 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f3d16188138c2f268305fddb092d56be870a3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586396"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a><span data-ttu-id="42c49-102">RowNumber 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="42c49-102">RowNumber Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="42c49-103">返回指定作用域内行数的运行计数。</span><span class="sxs-lookup"><span data-stu-id="42c49-103">Returns a running count of the number of rows for the specified scope.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="42c49-104">语法</span><span class="sxs-lookup"><span data-stu-id="42c49-104">Syntax</span></span>  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42c49-105">parameters</span><span class="sxs-lookup"><span data-stu-id="42c49-105">Parameters</span></span>  
 <span data-ttu-id="42c49-106">*作用域*</span><span class="sxs-lookup"><span data-stu-id="42c49-106">*scope*</span></span>  
 <span data-ttu-id="42c49-107">(`String`) 数据集、数据区域或组的名称，也可以为 Null（在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中为 `Nothing`），它指定在其中计算行数的上下文。</span><span class="sxs-lookup"><span data-stu-id="42c49-107">(`String`) The name of a dataset, data region, or group, or null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), that specifies the context in which to evaluate the number of rows.</span></span> <span data-ttu-id="42c49-108">`Nothing` 指定最外层的上下文，通常为报表数据集。</span><span class="sxs-lookup"><span data-stu-id="42c49-108">`Nothing` specifies the outermost context, usually the report dataset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c49-109">备注</span><span class="sxs-lookup"><span data-stu-id="42c49-109">Remarks</span></span>  
 <span data-ttu-id="42c49-110">`RowNumber`返回指定范围内的行数的运行值，正如[RunningValue](report-builder-functions-runningvalue-function.md)返回聚合函数的运行值一样。</span><span class="sxs-lookup"><span data-stu-id="42c49-110">`RowNumber` returns a running value of the count of rows within the specified scope, just as [RunningValue](report-builder-functions-runningvalue-function.md) returns the running value of an aggregate function.</span></span> <span data-ttu-id="42c49-111">指定作用域时，需要指定何时将行计数重新设置为 1。</span><span class="sxs-lookup"><span data-stu-id="42c49-111">When you specify a scope, you specify when to reset the row count to 1.</span></span>  
  
 <span data-ttu-id="42c49-112">*scope* 不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="42c49-112">*scope* cannot be an expression.</span></span> <span data-ttu-id="42c49-113">*scope* 必须是包含作用域。</span><span class="sxs-lookup"><span data-stu-id="42c49-113">*scope* must be a containing scope.</span></span> <span data-ttu-id="42c49-114">典型的从最外层到最内层包容的作用域是报表数据集、数据区域、行组或列组。</span><span class="sxs-lookup"><span data-stu-id="42c49-114">Typical scopes, from the outermost to the innermost containment, are report dataset, data region, row groups or column groups.</span></span>  
  
 <span data-ttu-id="42c49-115">若要在列间递增值，请指定一个为列组名称的作用域。</span><span class="sxs-lookup"><span data-stu-id="42c49-115">To increment values across columns, specify a scope that is the name of a column group.</span></span> <span data-ttu-id="42c49-116">若要沿行递增值，请指定一个为行组名称的作用域。</span><span class="sxs-lookup"><span data-stu-id="42c49-116">To increment numbers down rows, specify a scope that is the name of a row group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42c49-117">不能包括指定一个表达式中同时具有行组和列组的聚合。</span><span class="sxs-lookup"><span data-stu-id="42c49-117">Including aggregates that specify both a row group and a column group in a single expression is not supported.</span></span>  
  
 <span data-ttu-id="42c49-118">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="42c49-118">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="42c49-119">代码示例</span><span class="sxs-lookup"><span data-stu-id="42c49-119">Code Example</span></span>  
 <span data-ttu-id="42c49-120">以下表达式可用于 Tablix 数据区域详细信息行的 `BackgroundColor` 属性，以改变每个组的详细信息行的颜色（始终从白色开始）。</span><span class="sxs-lookup"><span data-stu-id="42c49-120">The following is an expression that you can use for the `BackgroundColor` property of a Tablix data region detail row to alternate the color of detail rows for each group, always beginning with White.</span></span>  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a><span data-ttu-id="42c49-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42c49-121">See Also</span></span>  
 <span data-ttu-id="42c49-122">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42c49-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="42c49-123">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42c49-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="42c49-124">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="42c49-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="42c49-125">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="42c49-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
