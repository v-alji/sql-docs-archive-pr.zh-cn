---
title: Level 函数（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dedbf00ce8330242c95e9592f649d95171f0987a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586412"
---
# <a name="level-function-report-builder-and-ssrs"></a><span data-ttu-id="ef013-102">Level 函数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ef013-102">Level Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ef013-103">返回在递归层次结构中的当前深度级别。</span><span class="sxs-lookup"><span data-stu-id="ef013-103">Returns the current level of depth in a recursive hierarchy.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="ef013-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef013-104">Syntax</span></span>  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef013-105">parameters</span><span class="sxs-lookup"><span data-stu-id="ef013-105">Parameters</span></span>  
 <span data-ttu-id="ef013-106">*作用域*</span><span class="sxs-lookup"><span data-stu-id="ef013-106">*scope*</span></span>  
 <span data-ttu-id="ef013-107">(`String`)（可选）。</span><span class="sxs-lookup"><span data-stu-id="ef013-107">(`String`) (Optional).</span></span> <span data-ttu-id="ef013-108">包含要对其应用聚合函数的报表项的数据集、组或数据区域的名称。</span><span class="sxs-lookup"><span data-stu-id="ef013-108">The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="ef013-109">如果未指定 *scope* ，则使用当前作用域。</span><span class="sxs-lookup"><span data-stu-id="ef013-109">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="ef013-110">返回类型</span><span class="sxs-lookup"><span data-stu-id="ef013-110">Return Type</span></span>  
 <span data-ttu-id="ef013-111">返回 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="ef013-111">Returns an `Integer`.</span></span> <span data-ttu-id="ef013-112">如果*作用域*指定数据集或数据区域，或指定非递归分组 (即，不包含 `Parent` 元素) 的分组，则 `Level` 返回0。</span><span class="sxs-lookup"><span data-stu-id="ef013-112">If *scope* specifies a dataset or data region, or specifies a nonrecursive grouping (that is, a grouping with no `Parent` element), `Level` returns 0.</span></span> <span data-ttu-id="ef013-113">如果省略 *scope* ，则返回当前作用域的级别。</span><span class="sxs-lookup"><span data-stu-id="ef013-113">If *scope* is omitted, it returns the level of the current scope.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef013-114">备注</span><span class="sxs-lookup"><span data-stu-id="ef013-114">Remarks</span></span>  
 <span data-ttu-id="ef013-115">`Level` 函数返回的值从 0 开始；即，层次结构中的第一级为 0。</span><span class="sxs-lookup"><span data-stu-id="ef013-115">The value returned by the `Level` function is zero based; that is, the first level in a hierarchy is 0.</span></span>  
  
 <span data-ttu-id="ef013-116">`Level` 函数可用于为递归层次结构（如雇员列表）提供缩进格式。</span><span class="sxs-lookup"><span data-stu-id="ef013-116">The `Level` function can be used to provide indentation in a recursive hierarchy, such as an employee list.</span></span>  
  
 <span data-ttu-id="ef013-117">有关递归层次结构的详细信息，请参阅[创建递归层次结构组（报表生成器和 SSRS）](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ef013-117">For more information about recursive hierarchies, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef013-118">示例</span><span class="sxs-lookup"><span data-stu-id="ef013-118">Example</span></span>  
 <span data-ttu-id="ef013-119">下面的代码示例提供了 Employees 组中行的级别：</span><span class="sxs-lookup"><span data-stu-id="ef013-119">The following code example provides the level of row in the Employees group:</span></span>  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef013-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef013-120">See Also</span></span>  
 <span data-ttu-id="ef013-121">[在报表中使用表达式（报表生成器和 SSRS）](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef013-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ef013-122">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef013-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ef013-123">[表达式中的数据类型（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef013-123">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ef013-124">总计、聚合和内置集合的表达式作用域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ef013-124">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
