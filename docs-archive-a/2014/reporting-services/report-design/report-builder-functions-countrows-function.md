---
title: CountRows 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d5311dfc5dfcb89449a4039fdac4100fc5a3b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586421"
---
# <a name="countrows-function-report-builder-and-ssrs"></a><span data-ttu-id="34476-102">CountRows 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="34476-102">CountRows Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="34476-103">返回指定作用域内的行数，包括含有 Null 值的行。</span><span class="sxs-lookup"><span data-stu-id="34476-103">Returns the number of rows in the specified scope, including rows with null values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="34476-104">语法</span><span class="sxs-lookup"><span data-stu-id="34476-104">Syntax</span></span>  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34476-105">parameters</span><span class="sxs-lookup"><span data-stu-id="34476-105">Parameters</span></span>  
 <span data-ttu-id="34476-106">*作用域*</span><span class="sxs-lookup"><span data-stu-id="34476-106">*scope*</span></span>  
 <span data-ttu-id="34476-107">(`String`) 包含要计数报表项的数据集、数据区域或组的名称。</span><span class="sxs-lookup"><span data-stu-id="34476-107">(`String`) The name of a dataset, data region, or group that contains the report items to count.</span></span>  
  
 <span data-ttu-id="34476-108">*递归*</span><span class="sxs-lookup"><span data-stu-id="34476-108">*recursive*</span></span>  
 <span data-ttu-id="34476-109">(**Enumerated Type**) 可选。</span><span class="sxs-lookup"><span data-stu-id="34476-109">(**Enumerated Type**) Optional.</span></span> <span data-ttu-id="34476-110">`Simple`（默认值）或 `RdlRecursive`。</span><span class="sxs-lookup"><span data-stu-id="34476-110">`Simple` (default) or `RdlRecursive`.</span></span> <span data-ttu-id="34476-111">指定是否以递归方式执行聚合。</span><span class="sxs-lookup"><span data-stu-id="34476-111">Specifies whether to perform the aggregation recursively.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="34476-112">返回类型</span><span class="sxs-lookup"><span data-stu-id="34476-112">Return Type</span></span>  
 <span data-ttu-id="34476-113">返回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="34476-113">Returns an `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34476-114">备注</span><span class="sxs-lookup"><span data-stu-id="34476-114">Remarks</span></span>  
 <span data-ttu-id="34476-115">`CountRows` 计数指定作用域内的所有行，其中包括具有 Null 值的行。</span><span class="sxs-lookup"><span data-stu-id="34476-115">`CountRows` counts all rows in the specified scope, including rows that have null values.</span></span>  
  
 <span data-ttu-id="34476-116">*scope* 的值不能是表达式，并且必须引用当前作用域或包含作用域。</span><span class="sxs-lookup"><span data-stu-id="34476-116">The value of *scope* cannot be an expression and must refer to the current scope or a containing scope.</span></span>  
  
 <span data-ttu-id="34476-117">有关详细信息，请参阅[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)和[总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="34476-117">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="34476-118">有关递归聚合的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34476-118">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34476-119">示例</span><span class="sxs-lookup"><span data-stu-id="34476-119">Example</span></span>  
 <span data-ttu-id="34476-120">下面的代码示例显示一个表达式，该表达式计算名为 `GroupbyCategory` 的行组中的行数（基于表达式 `[Category]`）。</span><span class="sxs-lookup"><span data-stu-id="34476-120">The following code example shows an expression that calculates the number of rows in a row group named `GroupbyCategory` (based on the expression `[Category]`).</span></span>  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## <a name="see-also"></a><span data-ttu-id="34476-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34476-121">See Also</span></span>  
 <span data-ttu-id="34476-122">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34476-122">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34476-123">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34476-123">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34476-124">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34476-124">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="34476-125">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="34476-125">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
