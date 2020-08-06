---
title: ^（位异或）（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- bitwise exclusive OR (^)
ms.assetid: 6ac53cab-29c4-4835-9f87-371b058b2f38
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d86c3d810e9e5572af93c97f82c2275db2c979b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588671"
---
# <a name="-bitwise-exclusive-or-ssis-expression"></a><span data-ttu-id="75d20-102">^（位异或）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="75d20-102">^ (Bitwise Exclusive OR) (SSIS Expression)</span></span>
  <span data-ttu-id="75d20-103">对两个整数值执行“位异或”运算。</span><span class="sxs-lookup"><span data-stu-id="75d20-103">Performs a bitwise exclusive OR operation of two integer values.</span></span> <span data-ttu-id="75d20-104">它会将第一个操作数的每一位与第二个操作数中对应的每一位进行比较。</span><span class="sxs-lookup"><span data-stu-id="75d20-104">It compares each bit of its first operand to the corresponding bit of its second operand.</span></span> <span data-ttu-id="75d20-105">如果一位是 0，另一对应位是 1，则相应结果位设置为 1。</span><span class="sxs-lookup"><span data-stu-id="75d20-105">If one bit is 0 and the other bit is 1, the corresponding result bit is set to 1.</span></span> <span data-ttu-id="75d20-106">如果两位都是 0 或两位都是 1，则相应结果位设置为 0。</span><span class="sxs-lookup"><span data-stu-id="75d20-106">If both bits are 0 or both bits are 1, the corresponding result bit is set to 0.</span></span>  
  
 <span data-ttu-id="75d20-107">两个条件必须都为有符号的整数数据类型，或都为无符号的整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="75d20-107">Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d20-108">语法</span><span class="sxs-lookup"><span data-stu-id="75d20-108">Syntax</span></span>  
  
```  
  
integer_expression1 ^ integer_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="75d20-109">参数</span><span class="sxs-lookup"><span data-stu-id="75d20-109">Arguments</span></span>  
 <span data-ttu-id="75d20-110">*integer_expression1、integer_expression2*</span><span class="sxs-lookup"><span data-stu-id="75d20-110">*integer_expression1, integer_expression2*</span></span>  
 <span data-ttu-id="75d20-111">是有符号或无符号整数数据类型的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="75d20-111">Is any valid expression of a signed or unsigned integer data type.</span></span> <span data-ttu-id="75d20-112">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="75d20-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="75d20-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="75d20-113">Result Types</span></span>  
 <span data-ttu-id="75d20-114">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="75d20-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="75d20-115">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="75d20-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75d20-116">备注</span><span class="sxs-lookup"><span data-stu-id="75d20-116">Remarks</span></span>  
 <span data-ttu-id="75d20-117">如果任一条件为 Null，则表达式的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="75d20-117">If either condition is null, the expression result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="75d20-118">表达式示例</span><span class="sxs-lookup"><span data-stu-id="75d20-118">Expression Examples</span></span>  
 <span data-ttu-id="75d20-119">此示例对变量 **NumberA** 和 **NumberB**执行“位异或”运算。</span><span class="sxs-lookup"><span data-stu-id="75d20-119">This example performs a bitwise exclusive OR operation between variables **NumberA** and **NumberB**.</span></span> <span data-ttu-id="75d20-120">**NumberA** 包含 3 (00000011)， **NumberB** 包含 7 (00000111)。</span><span class="sxs-lookup"><span data-stu-id="75d20-120">**NumberA** contains 3 (00000011) and **NumberB** contains 7 (00000111).</span></span>  
  
```  
@NumberA ^ @NumberB  
```  
  
 <span data-ttu-id="75d20-121">表达式计算结果为 4 (00000100)。</span><span class="sxs-lookup"><span data-stu-id="75d20-121">The expression evaluates to 4 (00000100).</span></span>  
  
 <span data-ttu-id="75d20-122">00000011</span><span class="sxs-lookup"><span data-stu-id="75d20-122">00000011</span></span>  
  
 <span data-ttu-id="75d20-123">00000111</span><span class="sxs-lookup"><span data-stu-id="75d20-123">00000111</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="75d20-124">00000100</span><span class="sxs-lookup"><span data-stu-id="75d20-124">00000100</span></span>  
  
 <span data-ttu-id="75d20-125">此示例对 **ReorderPoint** 和 **SafetyStockLevel** 列执行“位异或”运算。</span><span class="sxs-lookup"><span data-stu-id="75d20-125">This example performs a bitwise exclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.</span></span>  
  
```  
ReorderPoint ^ SafetyStockLevel  
```  
  
 <span data-ttu-id="75d20-126">如果 **ReorderPoint** 为 10，而 **SafetyStockLevel** 为 8，则表达式计算结果为 2 (00000010)。</span><span class="sxs-lookup"><span data-stu-id="75d20-126">If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 2 (00000010).</span></span>  
  
 <span data-ttu-id="75d20-127">00001010</span><span class="sxs-lookup"><span data-stu-id="75d20-127">00001010</span></span>  
  
 <span data-ttu-id="75d20-128">00001000</span><span class="sxs-lookup"><span data-stu-id="75d20-128">00001000</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="75d20-129">00000010</span><span class="sxs-lookup"><span data-stu-id="75d20-129">00000010</span></span>  
  
 <span data-ttu-id="75d20-130">此示例对两个整数执行“位异或”运算。</span><span class="sxs-lookup"><span data-stu-id="75d20-130">This example performs a bitwise exclusive OR operation between two integers.</span></span>  
  
```  
3 ^ 5   
```  
  
 <span data-ttu-id="75d20-131">表达式计算结果为 6 (00000110)。</span><span class="sxs-lookup"><span data-stu-id="75d20-131">The expression evaluates to 6 (00000110).</span></span>  
  
 <span data-ttu-id="75d20-132">00000011</span><span class="sxs-lookup"><span data-stu-id="75d20-132">00000011</span></span>  
  
 <span data-ttu-id="75d20-133">00000101</span><span class="sxs-lookup"><span data-stu-id="75d20-133">00000101</span></span>  
  
 ----------\-  
  
 <span data-ttu-id="75d20-134">00000110</span><span class="sxs-lookup"><span data-stu-id="75d20-134">00000110</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d20-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75d20-135">See Also</span></span>  
 <span data-ttu-id="75d20-136">[||（逻辑或）（SSIS 表达式）](logical-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="75d20-136">[&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;](logical-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="75d20-137">[|（位异或）（SSIS 表达式）](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="75d20-137">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="75d20-138">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="75d20-138">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="75d20-139">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="75d20-139">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
