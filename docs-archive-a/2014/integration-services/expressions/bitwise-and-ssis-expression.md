---
title: '&amp;（位算符 AND）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbf3c8ffcef079e25c82478947bc3b92a6b4be93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588670"
---
# <a name="amp-bitwise-and-ssis-expression"></a><span data-ttu-id="4c3bc-102">&amp;（位算符 AND）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="4c3bc-102">&amp; (Bitwise AND) (SSIS Expression)</span></span>
  <span data-ttu-id="4c3bc-103">对两个整数值执行“位与”运算。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-103">Performs a bitwise AND operation of two integer values.</span></span> <span data-ttu-id="4c3bc-104">它会将第一个操作数的每一位与第二个操作数中对应的每一位进行比较。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="4c3bc-105">如果两位都是 1，则相应的结果位设置为 1。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-105">If both bits are 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="4c3bc-106">否则，相应的结果位设置为 0。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-106">Otherwise, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="4c3bc-107">两个条件都必须是有符号整数类型，或者都必须是无符号整数类型。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-107">Both conditions must be a signed integer type or both conditions must be an unsigned integer type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c3bc-108">语法</span><span class="sxs-lookup"><span data-stu-id="4c3bc-108">Syntax</span></span>  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c3bc-109">参数</span><span class="sxs-lookup"><span data-stu-id="4c3bc-109">Arguments</span></span>  
 <span data-ttu-id="4c3bc-110">*integer_expression1、integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="4c3bc-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="4c3bc-111">是有符号或无符号整数数据类型的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="4c3bc-112">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4c3bc-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="4c3bc-113">Result Types</span></span>  
 <span data-ttu-id="4c3bc-114">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="4c3bc-115">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c3bc-116">备注</span><span class="sxs-lookup"><span data-stu-id="4c3bc-116">Remarks</span></span>  
 <span data-ttu-id="4c3bc-117">如果任一条件为 Null，则表达式的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="4c3bc-118">表达式示例</span><span class="sxs-lookup"><span data-stu-id="4c3bc-118">Expression Examples</span></span>  
 <span data-ttu-id="4c3bc-119">此示例对 **NumberA** 和 **NumberB**列执行“位与”运算。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-119">This example performs a bitwise AND operation between the columns **NumberA** and **NumberB**.</span></span> <span data-ttu-id="4c3bc-120">**NumberA** 列包含 3 (0000011)， **NumberB** 列包含 7 (00000111)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-120">**NumberA** contains 3 (0000011) and column **NumberB** contains 7 (00000111).</span></span>  
  
```  
NumberA & NumberB  
```  
  
 <span data-ttu-id="4c3bc-121">表达式计算结果为 3 (00000011)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-121">The expression evaluates to 3 (00000011).</span></span>  
  
 <span data-ttu-id="4c3bc-122">00000011</span><span class="sxs-lookup"><span data-stu-id="4c3bc-122">00000011</span></span>  
  
 <span data-ttu-id="4c3bc-123">00000111</span><span class="sxs-lookup"><span data-stu-id="4c3bc-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4c3bc-124">00000011</span><span class="sxs-lookup"><span data-stu-id="4c3bc-124">00000011</span></span>  
  
 <span data-ttu-id="4c3bc-125">此示例对 **ReorderPoint** 和 **SafetyStockLevel** 列执行“位与”运算。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-125">This example performs a bitwise AND operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 <span data-ttu-id="4c3bc-126">如果 **ReorderPoint** 为 10，而 **SafetyStockLevel** 为 8，则表达式计算结果为 8 (00001000)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 8 (00001000).</span></span>  
  
 <span data-ttu-id="4c3bc-127">00001010</span><span class="sxs-lookup"><span data-stu-id="4c3bc-127">00001010</span></span>  
  
 <span data-ttu-id="4c3bc-128">00001000</span><span class="sxs-lookup"><span data-stu-id="4c3bc-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4c3bc-129">00001000</span><span class="sxs-lookup"><span data-stu-id="4c3bc-129">00001000</span></span>  
  
 <span data-ttu-id="4c3bc-130">此示例对两个整数执行“位与”运算。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-130">This example performs a bitwise AND operation between two integers.</span></span>  
  
```  
3 & 5   
```  
  
 <span data-ttu-id="4c3bc-131">表达式计算结果为 1 (00000001)。</span><span class="sxs-lookup"><span data-stu-id="4c3bc-131">The expression evaluates to 1(00000001).</span></span>  
  
 <span data-ttu-id="4c3bc-132">00000011</span><span class="sxs-lookup"><span data-stu-id="4c3bc-132">00000011</span></span>  
  
 <span data-ttu-id="4c3bc-133">00000101</span><span class="sxs-lookup"><span data-stu-id="4c3bc-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="4c3bc-134">00000001</span><span class="sxs-lookup"><span data-stu-id="4c3bc-134">00000001</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3bc-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c3bc-135">See Also</span></span>  
 <span data-ttu-id="4c3bc-136">[&&（逻辑 AND）（SSIS 表达式）](logical-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="4c3bc-136">[&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;](logical-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="4c3bc-137">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="4c3bc-137">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="4c3bc-138">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="4c3bc-138">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
