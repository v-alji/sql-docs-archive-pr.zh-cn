---
title: POWER（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1f5742f482ae52620ec11d95b84cb3d06199fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587479"
---
# <a name="power-ssis-expression"></a><span data-ttu-id="f5835-102">POWER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5835-102">POWER (SSIS Expression)</span></span>
  <span data-ttu-id="f5835-103">返回对数值表达式进行幂运算的结果。</span><span class="sxs-lookup"><span data-stu-id="f5835-103">Returns the result of raising a numeric expression to a power.</span></span> <span data-ttu-id="f5835-104">Power 参数的计算结果必须为整数。</span><span class="sxs-lookup"><span data-stu-id="f5835-104">The power parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5835-105">语法</span><span class="sxs-lookup"><span data-stu-id="f5835-105">Syntax</span></span>  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5835-106">参数</span><span class="sxs-lookup"><span data-stu-id="f5835-106">Arguments</span></span>  
 <span data-ttu-id="f5835-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="f5835-107">*numeric_expression*</span></span>  
 <span data-ttu-id="f5835-108">有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5835-108">Is a valid numeric expression.</span></span>  
  
 <span data-ttu-id="f5835-109">*power*</span><span class="sxs-lookup"><span data-stu-id="f5835-109">*power*</span></span>  
 <span data-ttu-id="f5835-110">有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5835-110">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f5835-111">结果类型</span><span class="sxs-lookup"><span data-stu-id="f5835-111">Result Types</span></span>  
 <span data-ttu-id="f5835-112">DT_R8</span><span class="sxs-lookup"><span data-stu-id="f5835-112">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5835-113">备注</span><span class="sxs-lookup"><span data-stu-id="f5835-113">Remarks</span></span>  
 <span data-ttu-id="f5835-114">执行幂运算前， *numeric_expression* 和 *power* 参数会转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5835-114">The *numeric_expression* and *power* arguments are cast to the DT_R8 data type before the power is computed.</span></span> <span data-ttu-id="f5835-115">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f5835-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="f5835-116">如果 *numeric_expression* 的计算结果为零，并且 *power* 为负，则表达式计算器将返回错误，并将返回结果设置为 Null。</span><span class="sxs-lookup"><span data-stu-id="f5835-116">If *numeric_expression* evaluates to zero and *power* is negative, the expression evaluator returns an error and sets the return result to null.</span></span>  
  
 <span data-ttu-id="f5835-117">如果 *numeric_expression* 或 *power* 的计算结果不确定，则返回结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="f5835-117">If *numeric_expression* or *power* evaluate to indeterminate results, the return result is null.</span></span>  
  
 <span data-ttu-id="f5835-118">*power* 参数可以是小数。</span><span class="sxs-lookup"><span data-stu-id="f5835-118">The *power* argument can be a fraction.</span></span> <span data-ttu-id="f5835-119">例如，可以使用 0.5 作为幂值。</span><span class="sxs-lookup"><span data-stu-id="f5835-119">For example, you can use the value 0.5 as the power.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f5835-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f5835-120">Expression Examples</span></span>  
 <span data-ttu-id="f5835-121">以下示例使用了一个数值。</span><span class="sxs-lookup"><span data-stu-id="f5835-121">This example uses a numeric literal.</span></span> <span data-ttu-id="f5835-122">该函数计算 4 的 3 次幂，返回 64。</span><span class="sxs-lookup"><span data-stu-id="f5835-122">The function raises 4 to the power of 3 and returns 64.</span></span>  
  
```  
POWER(4,3)  
```  
  
 <span data-ttu-id="f5835-123">以下示例使用了 **Length** 列和 **DimensionCount** 变量。</span><span class="sxs-lookup"><span data-stu-id="f5835-123">This example uses the **Length** column and the **DimensionCount** variable.</span></span> <span data-ttu-id="f5835-124">如果 **Length** 为 8， **DimensionCount** 为 2，则返回结果为 64。</span><span class="sxs-lookup"><span data-stu-id="f5835-124">If **Length** is 8, and **DimensionCount** is 2, the return result is 64.</span></span>  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a><span data-ttu-id="f5835-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5835-125">See Also</span></span>  
 [<span data-ttu-id="f5835-126">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5835-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
