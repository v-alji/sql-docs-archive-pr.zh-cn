---
title: 运算符优先级和结合性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90ec23f9e961cbe4df291b9670c09e51d5d8704b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690761"
---
# <a name="operator-precedence-and-associativity"></a><span data-ttu-id="0f70f-102">运算符优先级和结合性</span><span class="sxs-lookup"><span data-stu-id="0f70f-102">Operator Precedence and Associativity</span></span>
  <span data-ttu-id="0f70f-103">表达式计算器支持的运算符集中的每个运算符在优先级层次结构中具有指定的优先级，并包含计算方向。</span><span class="sxs-lookup"><span data-stu-id="0f70f-103">Each operator in the set of operators that the expression evaluator supports has a designated precedence in the precedence hierarchy and includes a direction in which it is evaluated.</span></span> <span data-ttu-id="0f70f-104">运算符的计算方向就是运算符结合性。</span><span class="sxs-lookup"><span data-stu-id="0f70f-104">The direction of evaluation for an operator is operator associativity.</span></span> <span data-ttu-id="0f70f-105">具有高优先级的运算符先于低优先级的运算符进行计算。</span><span class="sxs-lookup"><span data-stu-id="0f70f-105">Operators with higher precedence are evaluated before operators with lower precedence.</span></span> <span data-ttu-id="0f70f-106">如果复杂的表达式有多个运算符，则运算符优先级将确定执行操作的顺序。</span><span class="sxs-lookup"><span data-stu-id="0f70f-106">If a complex expression has multiple operators, operator precedence determines the order in which the operations are performed.</span></span> <span data-ttu-id="0f70f-107">执行顺序可能对结果值有明显的影响。</span><span class="sxs-lookup"><span data-stu-id="0f70f-107">The order of execution can significantly affect the resulting value.</span></span> <span data-ttu-id="0f70f-108">某些运算符具有相等的优先级。</span><span class="sxs-lookup"><span data-stu-id="0f70f-108">Some operators have equal precedence.</span></span> <span data-ttu-id="0f70f-109">如果表达式包含多个具有相等的优先级的运算符，则按照从左到右或从右到左的方向进行运算。</span><span class="sxs-lookup"><span data-stu-id="0f70f-109">If an expression contains multiple operators of equal precedence, the operators are evaluated directionally, from left to right or right to left.</span></span>  
  
 <span data-ttu-id="0f70f-110">下表按从高到低的顺序列出了运算符的优先级。</span><span class="sxs-lookup"><span data-stu-id="0f70f-110">The following table lists the precedence of operators in order of high to low.</span></span> <span data-ttu-id="0f70f-111">同一层上的运算符具有相等的优先级。</span><span class="sxs-lookup"><span data-stu-id="0f70f-111">Operators at the same level have equal precedence.</span></span>  
  
|<span data-ttu-id="0f70f-112">运算符</span><span class="sxs-lookup"><span data-stu-id="0f70f-112">Operator symbol</span></span>|<span data-ttu-id="0f70f-113">运算类型</span><span class="sxs-lookup"><span data-stu-id="0f70f-113">Type of Operation</span></span>|<span data-ttu-id="0f70f-114">结合性</span><span class="sxs-lookup"><span data-stu-id="0f70f-114">Associativity</span></span>|  
|---------------------|-----------------------|-------------------|  
|<span data-ttu-id="0f70f-115">( )</span><span class="sxs-lookup"><span data-stu-id="0f70f-115">( )</span></span>|<span data-ttu-id="0f70f-116">表达式</span><span class="sxs-lookup"><span data-stu-id="0f70f-116">Expression</span></span>|<span data-ttu-id="0f70f-117">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-117">Left to right</span></span>|  
|<span data-ttu-id="0f70f-118">-, !, ~</span><span class="sxs-lookup"><span data-stu-id="0f70f-118">-, !, ~</span></span>|<span data-ttu-id="0f70f-119">一元</span><span class="sxs-lookup"><span data-stu-id="0f70f-119">Unary</span></span>|<span data-ttu-id="0f70f-120">从右到左</span><span class="sxs-lookup"><span data-stu-id="0f70f-120">Right to left</span></span>|  
|<span data-ttu-id="0f70f-121">casts</span><span class="sxs-lookup"><span data-stu-id="0f70f-121">casts</span></span>|<span data-ttu-id="0f70f-122">一元</span><span class="sxs-lookup"><span data-stu-id="0f70f-122">Unary</span></span>|<span data-ttu-id="0f70f-123">从右到左</span><span class="sxs-lookup"><span data-stu-id="0f70f-123">Right to left</span></span>|  
|<span data-ttu-id="0f70f-124">\*, / ,%</span><span class="sxs-lookup"><span data-stu-id="0f70f-124">\*, / ,%</span></span>|<span data-ttu-id="0f70f-125">乘法性的</span><span class="sxs-lookup"><span data-stu-id="0f70f-125">Multiplicative</span></span>|<span data-ttu-id="0f70f-126">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-126">Left to right</span></span>|  
|<span data-ttu-id="0f70f-127">+, -</span><span class="sxs-lookup"><span data-stu-id="0f70f-127">+, -</span></span>|<span data-ttu-id="0f70f-128">累加性</span><span class="sxs-lookup"><span data-stu-id="0f70f-128">Additive</span></span>|<span data-ttu-id="0f70f-129">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-129">Left to right</span></span>|  
|<span data-ttu-id="0f70f-130">\<, >, \<=, >=</span><span class="sxs-lookup"><span data-stu-id="0f70f-130">\<, >, \<=, >=</span></span>|<span data-ttu-id="0f70f-131">关系</span><span class="sxs-lookup"><span data-stu-id="0f70f-131">Relational</span></span>|<span data-ttu-id="0f70f-132">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-132">Left to right</span></span>|  
|<span data-ttu-id="0f70f-133">==, !=</span><span class="sxs-lookup"><span data-stu-id="0f70f-133">==, !=</span></span>|<span data-ttu-id="0f70f-134">等式</span><span class="sxs-lookup"><span data-stu-id="0f70f-134">Equality</span></span>|<span data-ttu-id="0f70f-135">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-135">Left to right</span></span>|  
|&|<span data-ttu-id="0f70f-136">位与</span><span class="sxs-lookup"><span data-stu-id="0f70f-136">Bitwise AND</span></span>|<span data-ttu-id="0f70f-137">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-137">Left to right</span></span>|  
|^|<span data-ttu-id="0f70f-138">位异或</span><span class="sxs-lookup"><span data-stu-id="0f70f-138">Bitwise exclusive OR</span></span>|<span data-ttu-id="0f70f-139">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-139">Left to right</span></span>|  
|<span data-ttu-id="0f70f-140">&#124;</span><span class="sxs-lookup"><span data-stu-id="0f70f-140">&#124;</span></span>|<span data-ttu-id="0f70f-141">位或</span><span class="sxs-lookup"><span data-stu-id="0f70f-141">Bitwise inclusive OR</span></span>|<span data-ttu-id="0f70f-142">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-142">Left to right</span></span>|  
|&&|<span data-ttu-id="0f70f-143">逻辑与</span><span class="sxs-lookup"><span data-stu-id="0f70f-143">Logical AND</span></span>|<span data-ttu-id="0f70f-144">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-144">Left to right</span></span>|  
|<span data-ttu-id="0f70f-145">&#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="0f70f-145">&#124;&#124;</span></span>|<span data-ttu-id="0f70f-146">逻辑或</span><span class="sxs-lookup"><span data-stu-id="0f70f-146">Logical OR</span></span>|<span data-ttu-id="0f70f-147">从左到右</span><span class="sxs-lookup"><span data-stu-id="0f70f-147">Left to right</span></span>|  
|<span data-ttu-id="0f70f-148">?</span><span class="sxs-lookup"><span data-stu-id="0f70f-148">?</span></span> <span data-ttu-id="0f70f-149">解码的字符：</span><span class="sxs-lookup"><span data-stu-id="0f70f-149">:</span></span>|<span data-ttu-id="0f70f-150">条件表达式</span><span class="sxs-lookup"><span data-stu-id="0f70f-150">Conditional expression</span></span>|<span data-ttu-id="0f70f-151">从右到左</span><span class="sxs-lookup"><span data-stu-id="0f70f-151">Right to left</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f70f-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f70f-152">See Also</span></span>  
 [<span data-ttu-id="0f70f-153">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0f70f-153">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
