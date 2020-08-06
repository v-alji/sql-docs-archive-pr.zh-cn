---
title: FLOOR（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b638c9a7215d120c562e416cdecee463f031ad2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585902"
---
# <a name="floor-ssis-expression"></a><span data-ttu-id="f4b21-102">FLOOR（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f4b21-102">FLOOR (SSIS Expression)</span></span>
  <span data-ttu-id="f4b21-103">返回小于或等于数值表达式的最大整数。</span><span class="sxs-lookup"><span data-stu-id="f4b21-103">Returns the largest integer that is less than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b21-104">语法</span><span class="sxs-lookup"><span data-stu-id="f4b21-104">Syntax</span></span>  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4b21-105">参数</span><span class="sxs-lookup"><span data-stu-id="f4b21-105">Arguments</span></span>  
 <span data-ttu-id="f4b21-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="f4b21-106">*numeric_expression*</span></span>  
 <span data-ttu-id="f4b21-107">有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f4b21-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f4b21-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="f4b21-108">Result Types</span></span>  
 <span data-ttu-id="f4b21-109">参数表达式的数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="f4b21-109">The numeric data type of the argument expression.</span></span> <span data-ttu-id="f4b21-110">结果是与 *numeric_expression*数据类型相同的计算所得值的整数部分。</span><span class="sxs-lookup"><span data-stu-id="f4b21-110">The result is the integer portion of the calculated value in the same data type as *numeric_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4b21-111">备注</span><span class="sxs-lookup"><span data-stu-id="f4b21-111">Remarks</span></span>  
 <span data-ttu-id="f4b21-112">如果该参数为空，则 FLOOR 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="f4b21-112">FLOOR returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f4b21-113">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f4b21-113">Expression Examples</span></span>  
 <span data-ttu-id="f4b21-114">这些示例对正数、负数和零值应用 FLOOR 函数。</span><span class="sxs-lookup"><span data-stu-id="f4b21-114">These examples apply the FLOOR function to positive, negative, and zero values.</span></span>  
  
```  
FLOOR(123.45)  
```  
  
 <span data-ttu-id="f4b21-115">返回 123.00</span><span class="sxs-lookup"><span data-stu-id="f4b21-115">Returns 123.00</span></span>  
  
```  
FLOOR(-123.45)  
```  
  
 <span data-ttu-id="f4b21-116">返回 -124.00</span><span class="sxs-lookup"><span data-stu-id="f4b21-116">Returns -124.00</span></span>  
  
```  
FLOOR(0.00)  
```  
  
 <span data-ttu-id="f4b21-117">返回 0.00</span><span class="sxs-lookup"><span data-stu-id="f4b21-117">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b21-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4b21-118">See Also</span></span>  
 <span data-ttu-id="f4b21-119">[CEILING（SSIS 表达式）](ceiling-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="f4b21-119">[CEILING &#40;SSIS Expression&#41;](ceiling-ssis-expression.md) </span></span>  
 [<span data-ttu-id="f4b21-120">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f4b21-120">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
