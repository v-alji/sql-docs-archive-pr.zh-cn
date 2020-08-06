---
title: 运算符（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 652f53ef639e63e4868dabeea3f49b9303336043
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691820"
---
# <a name="operators-ssis-expression"></a><span data-ttu-id="1f5fc-102">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-102">Operators (SSIS Expression)</span></span>
  <span data-ttu-id="1f5fc-103">本部分介绍了表达式语言提供的运算符和表达式计算器使用的运算符优先级及结合性。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-103">This section describes the operators the expression language provides and the operator precedence and associativity that the expression evaluator uses.</span></span>  
  
 <span data-ttu-id="1f5fc-104">下表列出了本部分中有关运算符的主题。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-104">The following table lists topics about operators in this section.</span></span>  
  
|<span data-ttu-id="1f5fc-105">操作员</span><span class="sxs-lookup"><span data-stu-id="1f5fc-105">Operator</span></span>|<span data-ttu-id="1f5fc-106">说明</span><span class="sxs-lookup"><span data-stu-id="1f5fc-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="1f5fc-107">Cast（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-107">Cast &#40;SSIS Expression&#41;</span></span>](cast-ssis-expression.md)|<span data-ttu-id="1f5fc-108">将表达式从一种数据类型转换为另外一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-108">Converts an expression from one data type to a different data type.</span></span>|  
|[<span data-ttu-id="1f5fc-109">()（括号）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-109">&#40;&#41; &#40;Parentheses&#41; &#40;SSIS Expression&#41;</span></span>](parentheses-ssis-expression.md)|<span data-ttu-id="1f5fc-110">标识表达式的计算顺序。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-110">Identifies the evaluation order of expressions.</span></span>|  
|[<span data-ttu-id="1f5fc-111">+（相加）(SSIS)</span><span class="sxs-lookup"><span data-stu-id="1f5fc-111">+ &#40;Add&#41; &#40;SSIS&#41;</span></span>](add-ssis.md)|<span data-ttu-id="1f5fc-112">将两个数值表达式相加。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-112">Adds two numeric expressions.</span></span>|  
|[<span data-ttu-id="1f5fc-113">+（连接）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-113">+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;</span></span>](concatenate-ssis-expression.md)|<span data-ttu-id="1f5fc-114">连接两个表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-114">Concatenates two expressions.</span></span>|  
|[<span data-ttu-id="1f5fc-115">-（相减）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-115">- &#40;Subtract&#41; &#40;SSIS Expression&#41;</span></span>](subtract-ssis-expression.md)|<span data-ttu-id="1f5fc-116">从第一个数值表达式的值中减去第二个数值表达式的值。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-116">Subtracts the second numeric expression from the first one.</span></span>|  
|[<span data-ttu-id="1f5fc-117">-（求反）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-117">- &#40;Negate&#41; &#40;SSIS Expression&#41;</span></span>](negate-ssis-expression.md)|<span data-ttu-id="1f5fc-118">对一个数值表达式求反。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-118">Negates a numeric expression.</span></span>|  
|[<span data-ttu-id="1f5fc-119">\*（相乘）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-119">&#42; &#40;Multiply&#41; &#40;SSIS Expression&#41;</span></span>](multiply-ssis-expression.md)|<span data-ttu-id="1f5fc-120">将两个数值表达式相乘。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-120">Multiplies two numeric expressions.</span></span>|  
|[<span data-ttu-id="1f5fc-121">除（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-121">Divide &#40;SSIS Expression&#41;</span></span>](divide-ssis-expression.md)|<span data-ttu-id="1f5fc-122">用第一个数值表达式除以第二个数值表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-122">Divides the first numeric expression by the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-123">（取模）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-123">&#40;Modulo&#41; &#40;SSIS Expression&#41;</span></span>](modulo-ssis-expression.md)|<span data-ttu-id="1f5fc-124">将第一个数据表达式的值除以第二个数据表达式的值后，提供整数余数。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-124">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-125">&#124;&#124; &#40;逻辑或&#41; &#40;SSIS 表达式&#41;</span><span class="sxs-lookup"><span data-stu-id="1f5fc-125">&#124;&#124; &#40;Logical OR&#41; &#40;SSIS Expression&#41;</span></span>](logical-or-ssis-expression.md)|<span data-ttu-id="1f5fc-126">执行“逻辑或”运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-126">Performs a logical OR operation.</span></span>|  
|[<span data-ttu-id="1f5fc-127">&&（逻辑 AND）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-127">&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;</span></span>](logical-and-ssis-expression.md)|<span data-ttu-id="1f5fc-128">执行“逻辑与”运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-128">Performs a logical AND operation.</span></span>|  
|[<span data-ttu-id="1f5fc-129">\!（逻辑非）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-129">\! &#40;Logical NOT&#41; &#40;SSIS Expression&#41;</span></span>](logical-not-ssis-expression.md)|<span data-ttu-id="1f5fc-130">对布尔操作数求反。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-130">Negates a Boolean operand.</span></span>|  
|[<span data-ttu-id="1f5fc-131">&#124;（位异或）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-131">&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-inclusive-or-ssis-expression.md)|<span data-ttu-id="1f5fc-132">对两个整数值执行“位或”运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-132">Performs a bitwise OR operation of two integer values.</span></span>|  
|[<span data-ttu-id="1f5fc-133">^（位异或）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-133">^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-exclusive-or-ssis-expression.md)|<span data-ttu-id="1f5fc-134">对两个整数值执行“位异或”运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-134">Performs a bitwise exclusive OR operation of two integer values.</span></span>|  
|[<span data-ttu-id="1f5fc-135">&（位与）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-135">& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-and-ssis-expression.md)|<span data-ttu-id="1f5fc-136">对两个整数值执行“位与”运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-136">Performs a bitwise AND operation of two integer values.</span></span>|  
|[<span data-ttu-id="1f5fc-137">~ &#40;按位 Not&#41; &#40;SSIS 表达式&#41;</span><span class="sxs-lookup"><span data-stu-id="1f5fc-137">~ &#40;Bitwise Not&#41; &#40;SSIS Expression&#41;</span></span>](bitwise-not-ssis-expression.md)|<span data-ttu-id="1f5fc-138">对整数执行位求反运算。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-138">Performs a bitwise negation of an integer.</span></span>|  
|[<span data-ttu-id="1f5fc-139">==（等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-139">== &#40;Equal&#41; &#40;SSIS Expression&#41;</span></span>](equal-ssis-expression.md)|<span data-ttu-id="1f5fc-140">执行比较来确定两个表达式是否相等。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-140">Performs a comparison to determine if two expressions are equal.</span></span>|  
|[<span data-ttu-id="1f5fc-141">\!=（不等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-141">\!= &#40;Unequal&#41; &#40;SSIS Expression&#41;</span></span>](unequal-ssis-expression.md)|<span data-ttu-id="1f5fc-142">通过比较来确定两个表达式是否不相等。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-142">Performs a comparison to determine if two expressions are not equal.</span></span>|  
|[<span data-ttu-id="1f5fc-143">>（大于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-143">&#62; &#40;Greater Than&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-ssis-expression.md)|<span data-ttu-id="1f5fc-144">通过比较来确定第一个表达式是否大于第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-144">Performs a comparison to determine if the first expression is greater than the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-145">>（小于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-145">&#60; &#40;Less Than&#41; &#40;SSIS Expression&#41;</span></span>](less-than-ssis-expression.md)|<span data-ttu-id="1f5fc-146">通过比较确定第一个表达式是否小于第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-146">Performs a comparison to determine if the first expression is less than the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-147">>=（大于或等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-147">&#62;= &#40;Greater Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-or-equal-to-ssis-expression.md)|<span data-ttu-id="1f5fc-148">执行比较来确定第一个表达式是否大于或等于第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-148">Performs a comparison to determine if the first expression is greater than or equal to the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-149"><=（小于或等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-149">&#60;= &#40;Less Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](less-than-or-equal-to-ssis-expression.md)|<span data-ttu-id="1f5fc-150">通过比较确定第一个表达式是否小于或等于第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-150">Performs a comparison to determine if the first expression is less than or equal to the second one.</span></span>|  
|[<span data-ttu-id="1f5fc-151">?:（条件）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1f5fc-151">? : &#40;Conditional&#41; &#40;SSIS Expression&#41;</span></span>](conditional-ssis-expression.md)|<span data-ttu-id="1f5fc-152">根据布尔表达式的计算结果，返回两个表达式之一。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-152">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span>|  
  
 <span data-ttu-id="1f5fc-153">有关优先级层次结构中各个运算符的位置的信息，请参阅 [Operator Precedence and Associativity](operator-precedence-and-associativity.md)。</span><span class="sxs-lookup"><span data-stu-id="1f5fc-153">For information about the placement of each operator in the precedence hierarchy, see [Operator Precedence and Associativity](operator-precedence-and-associativity.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5fc-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f5fc-154">See Also</span></span>  
 <span data-ttu-id="1f5fc-155">[函数（SSIS 表达式）](functions-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="1f5fc-155">[Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md) </span></span>  
 <span data-ttu-id="1f5fc-156">[高级 Integration Services 表达式的示例](examples-of-advanced-integration-services-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="1f5fc-156">[Examples of Advanced Integration Services Expressions](examples-of-advanced-integration-services-expressions.md) </span></span>  
 [<span data-ttu-id="1f5fc-157">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="1f5fc-157">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
