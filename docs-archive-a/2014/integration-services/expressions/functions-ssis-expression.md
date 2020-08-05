---
title: 函数（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 298085a1e3b9c292c9289415a4cb8a3c5adabea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580797"
---
# <a name="functions-ssis-expression"></a><span data-ttu-id="ce409-102">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-102">Functions (SSIS Expression)</span></span>
  <span data-ttu-id="ce409-103">表达式语言包含一组用于表达式的函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-103">The expression language includes a set of functions for use in expressions.</span></span> <span data-ttu-id="ce409-104">表达式可以使用单个函数。但是，通常一个表达式可以通过运算符将多个函数组合起来，从而使用多个函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-104">An expression can use a single function, but typically an expression combines functions with operators and uses multiple functions.</span></span>  
  
 <span data-ttu-id="ce409-105">函数可以划分为以下几组：</span><span class="sxs-lookup"><span data-stu-id="ce409-105">The functions can be categorized into the following groups:</span></span>  
  
-   <span data-ttu-id="ce409-106">数学函数，根据作为参数提供给函数的数值输入值执行计算并返回数值。</span><span class="sxs-lookup"><span data-stu-id="ce409-106">Mathematical functions that perform calculations based on numeric input values provided as parameters to the functions and return numeric values.</span></span>  
  
-   <span data-ttu-id="ce409-107">字符串函数，对字符串或十六进制输入值执行操作，并返回字符串或数值。</span><span class="sxs-lookup"><span data-stu-id="ce409-107">String functions that perform operations on string or hexadecimal input values and return a string or numeric value.</span></span>  
  
-   <span data-ttu-id="ce409-108">日期和时间函数，对日期和时间值执行操作，并返回字符串、数值或日期和时间值。</span><span class="sxs-lookup"><span data-stu-id="ce409-108">Date and time functions that perform operations on date and time values and return string, numeric, or date and time values.</span></span>  
  
-   <span data-ttu-id="ce409-109">系统函数，返回有关表达式的信息。</span><span class="sxs-lookup"><span data-stu-id="ce409-109">System functions that return information about an expression.</span></span>  
  
 <span data-ttu-id="ce409-110">表达式语言提供了下列数学函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-110">The expression language provides the following mathematical functions.</span></span>  
  
|<span data-ttu-id="ce409-111">函数</span><span class="sxs-lookup"><span data-stu-id="ce409-111">Function</span></span>|<span data-ttu-id="ce409-112">说明</span><span class="sxs-lookup"><span data-stu-id="ce409-112">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ce409-113">ABS（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-113">ABS &#40;SSIS Expression&#41;</span></span>](abs-ssis-expression.md)|<span data-ttu-id="ce409-114">返回数值表达式的绝对值。</span><span class="sxs-lookup"><span data-stu-id="ce409-114">Returns the absolute, positive value of a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-115">EXP（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-115">EXP &#40;SSIS Expression&#41;</span></span>](exp-ssis-expression.md)|<span data-ttu-id="ce409-116">返回指定表达式以 e 为底的指数。</span><span class="sxs-lookup"><span data-stu-id="ce409-116">Returns the exponent to base e of the specified expression.</span></span>|  
|[<span data-ttu-id="ce409-117">CEILING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-117">CEILING &#40;SSIS Expression&#41;</span></span>](ceiling-ssis-expression.md)|<span data-ttu-id="ce409-118">返回大于或等于数值表达式的最小整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-118">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-119">FLOOR（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-119">FLOOR &#40;SSIS Expression&#41;</span></span>](floor-ssis-expression.md)|<span data-ttu-id="ce409-120">返回小于或等于数值表达式的最大整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-120">Returns the largest integer that is less than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-121">LN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-121">LN &#40;SSIS Expression&#41;</span></span>](ln-ssis-expression.md)|<span data-ttu-id="ce409-122">返回数值表达式的自然对数。</span><span class="sxs-lookup"><span data-stu-id="ce409-122">Returns the natural logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-123">LOG（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-123">LOG &#40;SSIS Expression&#41;</span></span>](log-ssis-expression.md)|<span data-ttu-id="ce409-124">返回数值表达式以 10 为底的对数。</span><span class="sxs-lookup"><span data-stu-id="ce409-124">Returns the base-10 logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-125">POWER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-125">POWER &#40;SSIS Expression&#41;</span></span>](power-ssis-expression.md)|<span data-ttu-id="ce409-126">返回对数值表达式进行幂运算的结果。</span><span class="sxs-lookup"><span data-stu-id="ce409-126">Returns the result of raising a numeric expression to a power.</span></span>|  
|[<span data-ttu-id="ce409-127">ROUND（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-127">ROUND &#40;SSIS Expression&#41;</span></span>](round-ssis-expression.md)|<span data-ttu-id="ce409-128">返回舍入到指定长度或精度的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-128">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="ce409-129">。</span><span class="sxs-lookup"><span data-stu-id="ce409-129">.</span></span>|  
|[<span data-ttu-id="ce409-130">SIGN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-130">SIGN &#40;SSIS Expression&#41;</span></span>](sign-ssis-expression.md)|<span data-ttu-id="ce409-131">返回数值表达式的正号 (+)、负号 (-) 或零 (0)。</span><span class="sxs-lookup"><span data-stu-id="ce409-131">Returns the positive (+), negative (-), or zero (0) sign of a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-132">SQUARE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-132">SQUARE &#40;SSIS Expression&#41;</span></span>](square-ssis-expression.md)|<span data-ttu-id="ce409-133">返回数值表达式的平方。</span><span class="sxs-lookup"><span data-stu-id="ce409-133">Returns the square of a numeric expression.</span></span>|  
|[<span data-ttu-id="ce409-134">SQRT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-134">SQRT &#40;SSIS Expression&#41;</span></span>](sqrt-ssis-expression.md)|<span data-ttu-id="ce409-135">返回数值表达式的平方根。</span><span class="sxs-lookup"><span data-stu-id="ce409-135">Returns the square root of a numeric expression.</span></span>|  
  
 <span data-ttu-id="ce409-136">表达式计算器提供了下列字符串函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-136">The expression evaluator provides the following string functions.</span></span>  
  
|<span data-ttu-id="ce409-137">函数</span><span class="sxs-lookup"><span data-stu-id="ce409-137">Function</span></span>|<span data-ttu-id="ce409-138">说明</span><span class="sxs-lookup"><span data-stu-id="ce409-138">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ce409-139">CODEPOINT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-139">CODEPOINT &#40;SSIS Expression&#41;</span></span>](codepoint-ssis-expression.md)|<span data-ttu-id="ce409-140">返回字符表达式最左端字符的 Unicode 代码值。</span><span class="sxs-lookup"><span data-stu-id="ce409-140">Returns the Unicode code value of the leftmost character of a character expression.</span></span>|  
|[<span data-ttu-id="ce409-141">FINDSTRING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-141">FINDSTRING &#40;SSIS Expression&#41;</span></span>](findstring-ssis-expression.md)|<span data-ttu-id="ce409-142">返回表达式中指定出现的字符串从 1 开始的索引。</span><span class="sxs-lookup"><span data-stu-id="ce409-142">Returns the one-based index of the specified occurrence of a character string within an expression.</span></span>|  
|[<span data-ttu-id="ce409-143">HEX（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-143">HEX &#40;SSIS Expression&#41;</span></span>](hex-ssis-expression.md)|<span data-ttu-id="ce409-144">返回一个表示整数的十六进制值的字符串。</span><span class="sxs-lookup"><span data-stu-id="ce409-144">Returns a string representing the hexadecimal value of an integer.</span></span>|  
|[<span data-ttu-id="ce409-145">LEN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-145">LEN &#40;SSIS Expression&#41;</span></span>](len-ssis-expression.md)|<span data-ttu-id="ce409-146">返回字符表达式中的字符数。</span><span class="sxs-lookup"><span data-stu-id="ce409-146">Returns the number of characters in a character expression.</span></span>|  
|[<span data-ttu-id="ce409-147">LEFT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-147">LEFT &#40;SSIS Expression&#41;</span></span>](left-ssis-expression.md)|<span data-ttu-id="ce409-148">返回从给定字符表达式最左侧开始的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="ce409-148">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="ce409-149">LOWER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-149">LOWER &#40;SSIS Expression&#41;</span></span>](lower-ssis-expression.md)|<span data-ttu-id="ce409-150">返回将大写字符转换为小写字符后得到的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-150">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>|  
|[<span data-ttu-id="ce409-151">LTRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-151">LTRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="ce409-152">返回删除了前导空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-152">Returns a character expression after removing leading spaces.</span></span>|  
|[<span data-ttu-id="ce409-153">REPLACE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-153">REPLACE &#40;SSIS Expression&#41;</span></span>](replace-ssis-expression.md)|<span data-ttu-id="ce409-154">返回用不同字符串或空字符串替换表达式中字符串后的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-154">Returns a character expression after replacing a string within the expression with either a different string or an empty string.</span></span>|  
|[<span data-ttu-id="ce409-155">REPLICATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-155">REPLICATE &#40;SSIS Expression&#41;</span></span>](replicate-ssis-expression.md)|<span data-ttu-id="ce409-156">返回复制了指定次数后的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-156">Returns a character expression, replicated a specified number of times.</span></span>|  
|[<span data-ttu-id="ce409-157">REVERSE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-157">REVERSE &#40;SSIS Expression&#41;</span></span>](reverse-ssis-expression.md)|<span data-ttu-id="ce409-158">按相反顺序返回字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-158">Returns a character expression in reverse order.</span></span>|  
|[<span data-ttu-id="ce409-159">RIGHT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-159">RIGHT &#40;SSIS Expression&#41;</span></span>](right-ssis-expression.md)|<span data-ttu-id="ce409-160">返回从给定字符表达式最右侧开始的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="ce409-160">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="ce409-161">RTRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-161">RTRIM &#40;SSIS Expression&#41;</span></span>](rtrim-ssis-expression.md)|<span data-ttu-id="ce409-162">返回删除了尾随空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-162">Returns a character expression after removing trailing spaces.</span></span>|  
|[<span data-ttu-id="ce409-163">SUBSTRING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-163">SUBSTRING &#40;SSIS Expression&#41;</span></span>](substring-ssis-expression.md)|<span data-ttu-id="ce409-164">返回字符表达式的一部分。</span><span class="sxs-lookup"><span data-stu-id="ce409-164">Returns a part of a character expression.</span></span>|  
|[<span data-ttu-id="ce409-165">TRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-165">TRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="ce409-166">返回删除了前导空格和尾随空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-166">Returns a character expression after removing leading and trailing spaces.</span></span>|  
|[<span data-ttu-id="ce409-167">UPPER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-167">UPPER &#40;SSIS Expression&#41;</span></span>](upper-ssis-expression.md)|<span data-ttu-id="ce409-168">返回将小写字符转换为大写字符后得到的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ce409-168">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>|  
  
 <span data-ttu-id="ce409-169">表达式计算器提供了下列日期和时间函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-169">The expression evaluator provides the following date and time functions.</span></span>  
  
|<span data-ttu-id="ce409-170">函数</span><span class="sxs-lookup"><span data-stu-id="ce409-170">Function</span></span>|<span data-ttu-id="ce409-171">说明</span><span class="sxs-lookup"><span data-stu-id="ce409-171">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ce409-172">DATEADD（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-172">DATEADD &#40;SSIS Expression&#41;</span></span>](dateadd-ssis-expression.md)|<span data-ttu-id="ce409-173">通过将指定日期与一个日期或时间间隔相加，返回一个新的 DT_DBTIMESTAMP 值。</span><span class="sxs-lookup"><span data-stu-id="ce409-173">Returns a new DT_DBTIMESTAMP value by adding a date or time interval to a specified date.</span></span>|  
|[<span data-ttu-id="ce409-174">DATEDIFF（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-174">DATEDIFF &#40;SSIS Expression&#41;</span></span>](datediff-ssis-expression.md)|<span data-ttu-id="ce409-175">返回两个指定日期之间所跨的日期和时间边界的数目。</span><span class="sxs-lookup"><span data-stu-id="ce409-175">Returns the number of date and time boundaries crossed between two specified dates.</span></span>|  
|[<span data-ttu-id="ce409-176">DATEPART（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-176">DATEPART &#40;SSIS Expression&#41;</span></span>](datepart-ssis-expression.md)|<span data-ttu-id="ce409-177">返回一个表示日期的日期部分的整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-177">Returns an integer representing a datepart of a date.</span></span>|  
|[<span data-ttu-id="ce409-178">DAY（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-178">DAY &#40;SSIS Expression&#41;</span></span>](day-ssis-expression.md)|<span data-ttu-id="ce409-179">返回表示指定日期的“日”的整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-179">Returns an integer that represents the day of the specified date.</span></span>|  
|[<span data-ttu-id="ce409-180">GETDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-180">GETDATE &#40;SSIS Expression&#41;</span></span>](getdate-ssis-expression.md)|<span data-ttu-id="ce409-181">返回系统的当前日期。</span><span class="sxs-lookup"><span data-stu-id="ce409-181">Returns the current date of the system.</span></span>|  
|[<span data-ttu-id="ce409-182">GETUTCDATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-182">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](getutcdate-ssis-expression.md)|<span data-ttu-id="ce409-183">返回以 UTC 时间（协调世界时或格林尼治标准时间）表示的系统当前日期。</span><span class="sxs-lookup"><span data-stu-id="ce409-183">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time).</span></span>|  
|[<span data-ttu-id="ce409-184">MONTH（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-184">MONTH &#40;SSIS Expression&#41;</span></span>](month-ssis-expression.md)|<span data-ttu-id="ce409-185">返回表示指定日期的月份的整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-185">Returns an integer that represents the month of the specified date.</span></span>|  
|[<span data-ttu-id="ce409-186">YEAR（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-186">YEAR &#40;SSIS Expression&#41;</span></span>](year-ssis-expression.md)|<span data-ttu-id="ce409-187">返回表示指定日期的年份的整数。</span><span class="sxs-lookup"><span data-stu-id="ce409-187">Returns an integer that represents the year of the specified date.</span></span>|  
  
 <span data-ttu-id="ce409-188">表达式计算器提供了下列空函数。</span><span class="sxs-lookup"><span data-stu-id="ce409-188">The expression evaluator provides the following null functions.</span></span>  
  
|<span data-ttu-id="ce409-189">函数</span><span class="sxs-lookup"><span data-stu-id="ce409-189">Function</span></span>|<span data-ttu-id="ce409-190">说明</span><span class="sxs-lookup"><span data-stu-id="ce409-190">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="ce409-191">ISNULL（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-191">ISNULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="ce409-192">根据表达式是否为空，返回一个布尔值结果。</span><span class="sxs-lookup"><span data-stu-id="ce409-192">Returns a Boolean result based on whether an expression is null.</span></span>|  
|[<span data-ttu-id="ce409-193">NULL（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ce409-193">NULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="ce409-194">返回请求的数据类型的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="ce409-194">Returns a null value of a requested data type.</span></span>|  
  
 <span data-ttu-id="ce409-195">表达式名称以大写字符显示，但表达式名称并不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ce409-195">Expression names are shown in uppercase characters, but expression names are not case-sensitive.</span></span> <span data-ttu-id="ce409-196">例如，使用“null”和使用“NULL”的作用是一样的。</span><span class="sxs-lookup"><span data-stu-id="ce409-196">For example, using "null" works as well as using "NULL".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce409-197">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce409-197">See Also</span></span>  
 <span data-ttu-id="ce409-198">[运算符（SSIS 表达式）](operators-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="ce409-198">[Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) </span></span>  
 <span data-ttu-id="ce409-199">[高级 Integration Services 表达式的示例](examples-of-advanced-integration-services-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ce409-199">[Examples of Advanced Integration Services Expressions](examples-of-advanced-integration-services-expressions.md) </span></span>  
 [<span data-ttu-id="ce409-200">Integration Services (SSIS) 表达式</span><span class="sxs-lookup"><span data-stu-id="ce409-200">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
