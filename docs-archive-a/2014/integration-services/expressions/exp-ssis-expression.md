---
title: EXP（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 150c92355ab3e0d3a028c98defe2e2fa9a1bf8ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587482"
---
# <a name="exp-ssis-expression"></a><span data-ttu-id="18169-102">EXP（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="18169-102">EXP (SSIS Expression)</span></span>
  <span data-ttu-id="18169-103">返回数值表达式以 e 为基的指数。</span><span class="sxs-lookup"><span data-stu-id="18169-103">Returns the exponent to base e of a numeric expression.</span></span> <span data-ttu-id="18169-104">EXP 函数是对 LN 函数操作的补充，有时称为反对数。</span><span class="sxs-lookup"><span data-stu-id="18169-104">The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18169-105">语法</span><span class="sxs-lookup"><span data-stu-id="18169-105">Syntax</span></span>  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="18169-106">参数</span><span class="sxs-lookup"><span data-stu-id="18169-106">Arguments</span></span>  
 <span data-ttu-id="18169-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="18169-107">*numeric_expression*</span></span>  
 <span data-ttu-id="18169-108">有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="18169-108">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="18169-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="18169-109">Result Types</span></span>  
 <span data-ttu-id="18169-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="18169-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18169-111">备注</span><span class="sxs-lookup"><span data-stu-id="18169-111">Remarks</span></span>  
 <span data-ttu-id="18169-112">计算指数前数值表达式被转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="18169-112">The numeric expression is cast to the DT_R8 data type before the exponent is computed.</span></span> <span data-ttu-id="18169-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="18169-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="18169-114">返回结果始终为正数。</span><span class="sxs-lookup"><span data-stu-id="18169-114">The return result is always a positive number.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="18169-115">表达式示例</span><span class="sxs-lookup"><span data-stu-id="18169-115">Expression Examples</span></span>  
 <span data-ttu-id="18169-116">这些示例对正值、负值和零应用 EXP 函数。</span><span class="sxs-lookup"><span data-stu-id="18169-116">These examples apply the EXP function to positive and negative values and to zero.</span></span>  
  
```  
EXP(74)  
```  
  
 <span data-ttu-id="18169-117">返回 1.373382979540176E+32。</span><span class="sxs-lookup"><span data-stu-id="18169-117">Returns 1.373382979540176E+32.</span></span>  
  
```  
EXP(-27)  
```  
  
 <span data-ttu-id="18169-118">返回 1.879528816539083E-12。</span><span class="sxs-lookup"><span data-stu-id="18169-118">Returns 1.879528816539083E-12.</span></span>  
  
```  
EXP(0)  
```  
  
 <span data-ttu-id="18169-119">返回 1。</span><span class="sxs-lookup"><span data-stu-id="18169-119">Returns 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18169-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18169-120">See Also</span></span>  
 <span data-ttu-id="18169-121">[LOG（SSIS 表达式）](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="18169-121">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="18169-122">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="18169-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
