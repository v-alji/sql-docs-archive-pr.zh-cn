---
title: 表达式中的运算符（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa8042df39e535425a05414c1e39ee6a12ff2f39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586431"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="a4b73-102">表达式中的运算符（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a4b73-102">Operators in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a4b73-103">运算符是一种符号，用来表示要应用到表达式中一个或多个字词的操作。</span><span class="sxs-lookup"><span data-stu-id="a4b73-103">An operator is a symbol that represents actions applied to one or more terms in an expression.</span></span> <span data-ttu-id="a4b73-104">表达式中支持下列类别的运算符：算术、比较、串联、逻辑或位，以及移位。</span><span class="sxs-lookup"><span data-stu-id="a4b73-104">The following categories of operators are supported in an expression: arithmetic, comparison, concatenation, logical or bitwise, and bit shift.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a><span data-ttu-id="a4b73-105">算术</span><span class="sxs-lookup"><span data-stu-id="a4b73-105">Arithmetic</span></span>  
 <span data-ttu-id="a4b73-106">算术运算符对表达式中的两个数值字词执行数学运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-106">Arithmetic operators perform mathematical operations on two numeric terms in an expression.</span></span>  
  
|<span data-ttu-id="a4b73-107">操作员</span><span class="sxs-lookup"><span data-stu-id="a4b73-107">Operator</span></span>|<span data-ttu-id="a4b73-108">说明</span><span class="sxs-lookup"><span data-stu-id="a4b73-108">Description</span></span>|  
|--------------|-----------------|  
|^|<span data-ttu-id="a4b73-109">以一个数字为底、另一数字为幂求值。</span><span class="sxs-lookup"><span data-stu-id="a4b73-109">Raises a number to the power of another number.</span></span>|  
|*|<span data-ttu-id="a4b73-110">使两个数字相乘。</span><span class="sxs-lookup"><span data-stu-id="a4b73-110">Multiplies two numbers.</span></span>|  
|/|<span data-ttu-id="a4b73-111">使两个数字相除，返回浮点结果。</span><span class="sxs-lookup"><span data-stu-id="a4b73-111">Divides two numbers and returns a floating-point result.</span></span>|  
|<span data-ttu-id="a4b73-112">\|使两个数字相除，返回整数结果。</span><span class="sxs-lookup"><span data-stu-id="a4b73-112">\|Divides two numbers and returns an integer result.</span></span>|  
|<span data-ttu-id="a4b73-113">Mod</span><span class="sxs-lookup"><span data-stu-id="a4b73-113">Mod</span></span>|<span data-ttu-id="a4b73-114">返回一个除法运算的整数余数。</span><span class="sxs-lookup"><span data-stu-id="a4b73-114">Returns the integer remainder of a division.</span></span> <span data-ttu-id="a4b73-115">例如，7 Mod 5 = 2，这是因为 7 除以 5，余数为 2。</span><span class="sxs-lookup"><span data-stu-id="a4b73-115">For example, 7 Mod 5 = 2 because the remainder of 7 divided by 5 is 2.</span></span>|  
|+|<span data-ttu-id="a4b73-116">将两个数相加。</span><span class="sxs-lookup"><span data-stu-id="a4b73-116">Adds two numbers together.</span></span>|  
|-|<span data-ttu-id="a4b73-117">返回两个数字之差或表示一个数值字词的负值。</span><span class="sxs-lookup"><span data-stu-id="a4b73-117">Returns the difference between two numbers or indicates the negative value of a numeric term.</span></span>|  
  
### <a name="comparison"></a><span data-ttu-id="a4b73-118">比较</span><span class="sxs-lookup"><span data-stu-id="a4b73-118">Comparison</span></span>  
 <span data-ttu-id="a4b73-119">比较运算符测试两个表达式是否相同。</span><span class="sxs-lookup"><span data-stu-id="a4b73-119">Comparison operators test whether two expressions are the same.</span></span>  
  
|<span data-ttu-id="a4b73-120">操作员</span><span class="sxs-lookup"><span data-stu-id="a4b73-120">Operator</span></span>|<span data-ttu-id="a4b73-121">说明</span><span class="sxs-lookup"><span data-stu-id="a4b73-121">Description</span></span>|  
|--------------|-----------------|  
|<|<span data-ttu-id="a4b73-122">小于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-122">Less than.</span></span>|  
|\<=|<span data-ttu-id="a4b73-123">小于等于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-123">Less than or equal to.</span></span>|  
|>|<span data-ttu-id="a4b73-124">大于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-124">Greater than.</span></span>|  
|>=|<span data-ttu-id="a4b73-125">大于等于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-125">Greater than or equal to.</span></span>|  
|=|<span data-ttu-id="a4b73-126">等于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-126">Equal to.</span></span>|  
|<>|<span data-ttu-id="a4b73-127">不等于。</span><span class="sxs-lookup"><span data-stu-id="a4b73-127">Not equal to.</span></span>|  
|<span data-ttu-id="a4b73-128">Like</span><span class="sxs-lookup"><span data-stu-id="a4b73-128">Like</span></span>|<span data-ttu-id="a4b73-129">确定特定字符串是否与指定模式相匹配。</span><span class="sxs-lookup"><span data-stu-id="a4b73-129">Determines whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="a4b73-130">模式可以包含常规字符和通配符。</span><span class="sxs-lookup"><span data-stu-id="a4b73-130">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="a4b73-131">模式匹配过程中，常规字符必须与字符串中指定的字符完全匹配。</span><span class="sxs-lookup"><span data-stu-id="a4b73-131">During pattern matching, regular characters must exactly match the characters specified in the character string.</span></span> <span data-ttu-id="a4b73-132">但是，通配符可以与字符串的任意部分相匹配。</span><span class="sxs-lookup"><span data-stu-id="a4b73-132">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="a4b73-133">与使用 = 和 != 字符串比较运算符相比，使用通配符可使 LIKE 运算符更加灵活。</span><span class="sxs-lookup"><span data-stu-id="a4b73-133">Using wildcard characters makes the LIKE operator more flexible than using the = and != string comparison operators.</span></span><br /><br /> <span data-ttu-id="a4b73-134">下面列出了可以用作通配符的字符：</span><span class="sxs-lookup"><span data-stu-id="a4b73-134">The following lists characters that can be used as wildcards:</span></span><br /><br /> <span data-ttu-id="a4b73-135">**%**：零个或多个字符的任意字符串。</span><span class="sxs-lookup"><span data-stu-id="a4b73-135">**%**: Any string of zero or more characters.</span></span><br /><br /> <span data-ttu-id="a4b73-136">**_**：任何单个字符。</span><span class="sxs-lookup"><span data-stu-id="a4b73-136">**_**: Any single character.</span></span><br /><br /> <span data-ttu-id="a4b73-137">**[]**：指定范围内的任何单个字符 (例如，[a-f] ) 或 set (例如，[aeiou] ) 。</span><span class="sxs-lookup"><span data-stu-id="a4b73-137">**[ ]**: Any single character within the specified range (for example, [a-f]) or set (for example, [aeiou]).</span></span><br /><br /> <span data-ttu-id="a4b73-138">**[^]**：不在指定范围内的任何单个字符 (例如，[^ a-f] ) 或 set (例如，[^ aeiou] ) 。</span><span class="sxs-lookup"><span data-stu-id="a4b73-138">**[^]**: Any single character not within the specified range (for example, [^a-f]) or set (for example, [^aeiou]).</span></span>|  
|<span data-ttu-id="a4b73-139">Is</span><span class="sxs-lookup"><span data-stu-id="a4b73-139">Is</span></span>|<span data-ttu-id="a4b73-140">比较两个对象引用。</span><span class="sxs-lookup"><span data-stu-id="a4b73-140">Compares two object references.</span></span>|  
  
### <a name="string-concatenation"></a><span data-ttu-id="a4b73-141">字符串串联</span><span class="sxs-lookup"><span data-stu-id="a4b73-141">String Concatenation</span></span>  
 <span data-ttu-id="a4b73-142">字符串串联将第二个字符串追加到表达式中的第一个字符串。</span><span class="sxs-lookup"><span data-stu-id="a4b73-142">String concatenation appends the second string to the first string in an expression.</span></span> <span data-ttu-id="a4b73-143">对于其他字符串运算，使用内置函数。</span><span class="sxs-lookup"><span data-stu-id="a4b73-143">For other string operations, use built-in functions.</span></span>  
  
|<span data-ttu-id="a4b73-144">操作员</span><span class="sxs-lookup"><span data-stu-id="a4b73-144">Operator</span></span>|<span data-ttu-id="a4b73-145">说明</span><span class="sxs-lookup"><span data-stu-id="a4b73-145">Description</span></span>|  
|--------------|-----------------|  
|&|<span data-ttu-id="a4b73-146">串联两个字符串</span><span class="sxs-lookup"><span data-stu-id="a4b73-146">Concatenates two strings</span></span>|  
|+|<span data-ttu-id="a4b73-147">串联两个字符串</span><span class="sxs-lookup"><span data-stu-id="a4b73-147">Concatenates two strings</span></span>|  
  
### <a name="logical-and-bitwise"></a><span data-ttu-id="a4b73-148">逻辑和位</span><span class="sxs-lookup"><span data-stu-id="a4b73-148">Logical and Bitwise</span></span>  
 <span data-ttu-id="a4b73-149">逻辑运算符和位运算符在表达式中的两个整数字词之间执行逻辑操作。</span><span class="sxs-lookup"><span data-stu-id="a4b73-149">Logical and bitwise operators perform logical manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="a4b73-150">操作员</span><span class="sxs-lookup"><span data-stu-id="a4b73-150">Operator</span></span>|<span data-ttu-id="a4b73-151">说明</span><span class="sxs-lookup"><span data-stu-id="a4b73-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a4b73-152">And</span><span class="sxs-lookup"><span data-stu-id="a4b73-152">And</span></span>|<span data-ttu-id="a4b73-153">对两个布尔表达式执行逻辑与运算，或对两个数值表达式执行位与运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-153">Performs a logical conjunction on two Boolean expressions, or bitwise conjunction on two numeric expressions.</span></span>|  
|<span data-ttu-id="a4b73-154">Not</span><span class="sxs-lookup"><span data-stu-id="a4b73-154">Not</span></span>|<span data-ttu-id="a4b73-155">对布尔表达式执行逻辑非运算，或对数值表达式执行位求反运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-155">Performs logical negation on a Boolean expression, or bitwise negation on a numeric expression.</span></span>|  
|<span data-ttu-id="a4b73-156">或</span><span class="sxs-lookup"><span data-stu-id="a4b73-156">Or</span></span>|<span data-ttu-id="a4b73-157">对两个布尔表达式执行逻辑或运算，或对两个数值执行位或运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-157">Performs a logical disjunction on two Boolean expressions, or bitwise disjunction on two numeric values.</span></span>|  
|<span data-ttu-id="a4b73-158">Xor</span><span class="sxs-lookup"><span data-stu-id="a4b73-158">Xor</span></span>|<span data-ttu-id="a4b73-159">对两个布尔表达式执行逻辑异运算，或对两个数值表达式执行位异运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-159">Performs a logical exclusion operation on two Boolean expressions, or a bitwise exclusion on two numeric expressions.</span></span>|  
|<span data-ttu-id="a4b73-160">AndAlso</span><span class="sxs-lookup"><span data-stu-id="a4b73-160">AndAlso</span></span>|<span data-ttu-id="a4b73-161">对两个表达式执行逻辑与运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-161">Performs logical conjunction on two expressions.</span></span>|  
|<span data-ttu-id="a4b73-162">OrElse</span><span class="sxs-lookup"><span data-stu-id="a4b73-162">OrElse</span></span>|<span data-ttu-id="a4b73-163">对两个表达式执行逻辑或运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-163">Performs logical disjunction on two expressions.</span></span>|  
  
### <a name="bit-shift"></a><span data-ttu-id="a4b73-164">移位</span><span class="sxs-lookup"><span data-stu-id="a4b73-164">Bit Shift</span></span>  
 <span data-ttu-id="a4b73-165">位运算符在表达式中的两个整数字词之间执行位操作。</span><span class="sxs-lookup"><span data-stu-id="a4b73-165">Bitwise operators perform bit manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="a4b73-166">操作员</span><span class="sxs-lookup"><span data-stu-id="a4b73-166">Operator</span></span>|<span data-ttu-id="a4b73-167">说明</span><span class="sxs-lookup"><span data-stu-id="a4b73-167">Description</span></span>|  
|--------------|-----------------|  
|<\<|<span data-ttu-id="a4b73-168">对位模式执行算术左移位运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-168">Performs an arithmetic left-shift on a bit pattern.</span></span>|  
|>>|<span data-ttu-id="a4b73-169">对位模式执行算术右移位运算。</span><span class="sxs-lookup"><span data-stu-id="a4b73-169">Performs an arithmetic right-shift on a bit pattern.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4b73-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4b73-170">See Also</span></span>  
 <span data-ttu-id="a4b73-171">[“表达式”对话框](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="a4b73-171">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="a4b73-172">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4b73-172">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4b73-173">[表达式示例（报表生成器和 SSRS）](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4b73-173">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4b73-174">[表达式中的数据类型（报表生成器和 SSRS）](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4b73-174">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a4b73-175">“表达式”对话框（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="a4b73-175">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
