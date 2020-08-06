---
title: 表达式中的 Integration Services 数据类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], data types
- data types [Integration Services], expressions
ms.assetid: c296ad10-4080-4988-8c2c-2c250f7a1884
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b2921da7322c7511facacf3918368d8cd8f2fe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689994"
---
# <a name="integration-services-data-types-in-expressions"></a><span data-ttu-id="fca78-102">表达式中的 Integration Services 数据类型</span><span class="sxs-lookup"><span data-stu-id="fca78-102">Integration Services Data Types in Expressions</span></span>
  <span data-ttu-id="fca78-103">表达式计算器使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-103">The expression evaluator uses [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="fca78-104">当数据首次进入 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包的数据流中时，数据流引擎将所有列数据转换为 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型，因此，表达式使用的列数据已具有 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-104">When data first enters a data flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package, the data flow engine converts all column data to an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data type, and the column data that an expression uses already has an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="fca78-105">有条件拆分和派生列转换中使用的表达式可以引用列，因为它们是包含列数据的数据流的一部分。</span><span class="sxs-lookup"><span data-stu-id="fca78-105">Expressions used in the Conditional Split and the Derived Column transformations can reference columns because they are part of a data flow that includes column data.</span></span>

## <a name="variables"></a><span data-ttu-id="fca78-106">变量</span><span class="sxs-lookup"><span data-stu-id="fca78-106">Variables</span></span>
 <span data-ttu-id="fca78-107">表达式还可以使用变量。</span><span class="sxs-lookup"><span data-stu-id="fca78-107">Expressions can also use variables.</span></span> <span data-ttu-id="fca78-108">变量具有 Variant 数据类型，表达式计算器在计算表达式前会将变量的数据类型从 Variant 子类型转换为 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-108">Variables have a Variant data type and the expression evaluator converts the data type of a variable from a Variant subtype to an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data type before it evaluates the expression.</span></span> <span data-ttu-id="fca78-109">变量只能使用 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型的一个子集。</span><span class="sxs-lookup"><span data-stu-id="fca78-109">Variables can use only a subset of the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="fca78-110">例如，变量不能使用二进制大型对象块 (BLOB) 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-110">For example, a variable cannot use a Binary Large Object Block (BLOB) data type.</span></span>

 <span data-ttu-id="fca78-111">有关 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型和 Variant 数据类型到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型的映射的详细信息，请参阅 [集成服务数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fca78-111">For more information about [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types and the mapping of Variant data types to [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="literals"></a><span data-ttu-id="fca78-112">文字</span><span class="sxs-lookup"><span data-stu-id="fca78-112">Literals</span></span>
 <span data-ttu-id="fca78-113">此外，表达式还可以包含字符串、布尔值和数值。</span><span class="sxs-lookup"><span data-stu-id="fca78-113">In addition, expressions can include string, Boolean, and numeric literals.</span></span> <span data-ttu-id="fca78-114">有关将数值转换为数值 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型的详细信息，请参阅[文字 (SSIS)](numeric-string-and-boolean-literals.md)。</span><span class="sxs-lookup"><span data-stu-id="fca78-114">For more information about converting numeric literals to numeric [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types, see [Literals &#40;SSIS&#41;](numeric-string-and-boolean-literals.md).</span></span>

## <a name="implicit-data-conversion"></a><span data-ttu-id="fca78-115">隐式数据转换</span><span class="sxs-lookup"><span data-stu-id="fca78-115">Implicit Data Conversion</span></span>
 <span data-ttu-id="fca78-116">当表达式计算器自动将数据从一种数据类型转换为另一种数据类型时，将会发生数据类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="fca78-116">An implicit conversion of a data type occurs when the expression evaluator automatically converts the data from one data type to another.</span></span> <span data-ttu-id="fca78-117">例如，如果将 `smallint` 与 `int` 比较，则 `smallint` 便会在执行比较前被隐式转换为 `int`。</span><span class="sxs-lookup"><span data-stu-id="fca78-117">For example, if a `smallint` is compared to an `int`, the `smallint` is implicitly converted to `int` before the comparison is performed.</span></span>

 <span data-ttu-id="fca78-118">当参数和操作数具有不兼容的数据类型时，表达式计算器无法执行隐式数据转换。</span><span class="sxs-lookup"><span data-stu-id="fca78-118">The expression evaluator cannot perform implicit data conversion when the arguments and operands have incompatible data types.</span></span> <span data-ttu-id="fca78-119">此外，表达式计算器无法将任何值隐式转换为布尔值。</span><span class="sxs-lookup"><span data-stu-id="fca78-119">In addition, the expression evaluator cannot implicitly convert any value to a Boolean.</span></span> <span data-ttu-id="fca78-120">相反，参数和操作数必须借助于转换运算符显式转换。</span><span class="sxs-lookup"><span data-stu-id="fca78-120">Instead, the arguments and operands must be explicitly converted by using the cast operator.</span></span> <span data-ttu-id="fca78-121">有关详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="fca78-121">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>

 <span data-ttu-id="fca78-122">以下关系图显示了 BINARY 运算的隐式转换的结果类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-122">The following diagram shows the result type of implicit conversions of BINARY operations.</span></span> <span data-ttu-id="fca78-123">该表中列和行的交集为二元运算的结果类型，该运算中操作数的类型为左 (From) 和右 (To)。</span><span class="sxs-lookup"><span data-stu-id="fca78-123">The intersection of column and row in this table is the result type of a binary operation with operands of the left (From) and right (To) types.</span></span>

 <span data-ttu-id="fca78-124">![数据类型之间的隐式数据类型转换](../media/mw-dts-impl-conver-02.gif "数据类型之间的隐式数据类型转换")</span><span class="sxs-lookup"><span data-stu-id="fca78-124">![Implicit data type conversion between data types](../media/mw-dts-impl-conver-02.gif "Implicit data type conversion between data types")</span></span>

 <span data-ttu-id="fca78-125">有符号整数和无符号整数的交集是可能大于这两者中任何一个的有符号整数。</span><span class="sxs-lookup"><span data-stu-id="fca78-125">The intersection of a signed and an unsigned integer is a signed integer that is potentially larger than either argument.</span></span>

 <span data-ttu-id="fca78-126">操作数可对 String、Date、Boolean 以及其他数据类型进行比较。</span><span class="sxs-lookup"><span data-stu-id="fca78-126">Operators compare strings, dates, Booleans, and other data types.</span></span> <span data-ttu-id="fca78-127">在操作数比较两个值之前，表达式计算器会执行某些隐式转换。</span><span class="sxs-lookup"><span data-stu-id="fca78-127">Before an operator compares two values, the expression evaluator performs certain implicit conversions.</span></span> <span data-ttu-id="fca78-128">表达式计算器始终将字符串文字转换为 DT_WSTR 数据类型，将布尔值文字转换为 DT_BOOL 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-128">The expression evaluator always converts string literals to the DT_WSTR data type and converts Boolean literals to the DT_BOOL data type.</span></span> <span data-ttu-id="fca78-129">表达式计算器将引号引起来的所有值都解释为字符串。</span><span class="sxs-lookup"><span data-stu-id="fca78-129">The expression evaluator interprets all values enclosed in quotation marks as strings.</span></span> <span data-ttu-id="fca78-130">数值被转换为数值 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型的一种。</span><span class="sxs-lookup"><span data-stu-id="fca78-130">Numeric literals are converted to one of the numeric [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types.</span></span>

> [!NOTE]
>  <span data-ttu-id="fca78-131">布尔值是逻辑值而非数字。</span><span class="sxs-lookup"><span data-stu-id="fca78-131">Boolean values are logical values, not numbers.</span></span> <span data-ttu-id="fca78-132">虽然布尔值在某些环境中可能显示为数字，但它们并非以数字形式存储，而且不同的编程语言以不同的数值表示布尔值，.NET Framework 方法也是如此。</span><span class="sxs-lookup"><span data-stu-id="fca78-132">Although Boolean values may be displayed as numbers in some environments, they are not stored as numbers, and various programming languages represent Boolean values as numeric values differently, as do the .NET Framework methods.</span></span>
> 
>  <span data-ttu-id="fca78-133">例如，Visual Basic 中可用的转换函数将 `True` 转换为 -1；但是 .NET Framework 中的 `System.Convert.ToInt32` 方法将 `True` 转换为 +1。</span><span class="sxs-lookup"><span data-stu-id="fca78-133">For example, the conversion functions available in Visual Basic convert `True` to -1; however, the `System.Convert.ToInt32` method in the .NET Framework converts `True` to +1.</span></span> <span data-ttu-id="fca78-134">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 表达式语言将 `True` 转换为 -1。</span><span class="sxs-lookup"><span data-stu-id="fca78-134">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Expression Language converts `True` to -1.</span></span>
> 
>  <span data-ttu-id="fca78-135">若要避免错误或意外结果，不应编写依赖 `True` 和 `False` 为特定数值的代码。</span><span class="sxs-lookup"><span data-stu-id="fca78-135">To avoid errors or unexpected results, you should not write code that relies on particular numeric values for `True` and `False`.</span></span> <span data-ttu-id="fca78-136">如果可能，应将布尔变量的使用限制为与其设计意图对应的逻辑值。</span><span class="sxs-lookup"><span data-stu-id="fca78-136">Wherever possible, you should restrict usage of Boolean variables to the logical values for which they are designed.</span></span>

 <span data-ttu-id="fca78-137">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="fca78-137">For more information, see the following topics:</span></span>

-   [<span data-ttu-id="fca78-138">==（等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fca78-138">== &#40;Equal&#41; &#40;SSIS Expression&#41;</span></span>](equal-ssis-expression.md)

-   [<span data-ttu-id="fca78-139">！ =&#41; &#40;SSIS 表达式 &#40;不相等&#41;</span><span class="sxs-lookup"><span data-stu-id="fca78-139">!= &#40;Unequal&#41; &#40;SSIS Expression&#41;</span></span>](unequal-ssis-expression.md)

-   [<span data-ttu-id="fca78-140">>（大于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fca78-140">&#62; &#40;Greater Than&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-ssis-expression.md)

-   [<span data-ttu-id="fca78-141">>（小于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fca78-141">&#60; &#40;Less Than&#41; &#40;SSIS Expression&#41;</span></span>](less-than-ssis-expression.md)

-   [<span data-ttu-id="fca78-142">>=（大于或等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fca78-142">&#62;= &#40;Greater Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](greater-than-or-equal-to-ssis-expression.md)

-   [<span data-ttu-id="fca78-143"><=（小于或等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fca78-143">&#60;= &#40;Less Than or Equal To&#41; &#40;SSIS Expression&#41;</span></span>](less-than-or-equal-to-ssis-expression.md)

 <span data-ttu-id="fca78-144">使用单个参数的函数将返回与参数具有相同数据类型的结果，但下列情况除外：</span><span class="sxs-lookup"><span data-stu-id="fca78-144">A function that uses a single argument returns a result with the same data type as the argument, with the following exceptions:</span></span>

-   <span data-ttu-id="fca78-145">DAY、MONTH 和 YEAR 接受日期并返回一个整数 (DT_I4) 结果。</span><span class="sxs-lookup"><span data-stu-id="fca78-145">DAY, MONTH, and YEAR accept a date and return an integer (DT_I4) result.</span></span>

-   <span data-ttu-id="fca78-146">ISNULL 接受任意 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数据类型的表达式，并返回一个布尔值 (DT_BOOL) 结果。</span><span class="sxs-lookup"><span data-stu-id="fca78-146">ISNULL accepts an expression of any [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type and returns a Boolean (DT_BOOL) result.</span></span>

-   <span data-ttu-id="fca78-147">SQUARE 和 SQRT 接受数值表达式，并返回一个非整型数值 (DT_R8) 结果。</span><span class="sxs-lookup"><span data-stu-id="fca78-147">SQUARE and SQRT accept a numeric expression and return a non-integral numeric (DT_R8) result.</span></span>

 <span data-ttu-id="fca78-148">如果参数具有相同的数据类型，则结果即为该类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-148">If the arguments have the same data type, the result is of that type.</span></span> <span data-ttu-id="fca78-149">唯一的例外是，如果对两个 DT_DECIMAL 数据类型的值执行二进制操作，则它将返回 DT_NUMERIC 数据类型的结果。</span><span class="sxs-lookup"><span data-stu-id="fca78-149">The only exception is the result of a binary operation on two values with the DT_DECIMAL data type, which returns a result with the DT_NUMERIC data type.</span></span>

## <a name="requirements-for-data-used-in-expressions"></a><span data-ttu-id="fca78-150">表达式中的数据使用要求</span><span class="sxs-lookup"><span data-stu-id="fca78-150">Requirements for Data Used in Expressions</span></span>
 <span data-ttu-id="fca78-151">表达式计算器支持所有的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-151">The expression evaluator supports all [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="fca78-152">但是，根据运算或函数的不同，操作数和参数需要特定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-152">However, depending on the operation or the function, the operands and arguments require certain data types.</span></span> <span data-ttu-id="fca78-153">表达式计算器对表达式中使用的数据规定了下列数据类型要求：</span><span class="sxs-lookup"><span data-stu-id="fca78-153">The expression evaluator imposes the following data type requirements on data used in expressions:</span></span>

-   <span data-ttu-id="fca78-154">**“逻辑”** 运算中所用操作数的取值必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="fca78-154">Operands used in **logical** operations must evaluate to a Boolean.</span></span> <span data-ttu-id="fca78-155">例如，ColumnA > 1&&ColumnB < 2。</span><span class="sxs-lookup"><span data-stu-id="fca78-155">For example, ColumnA > 1&&ColumnB < 2.</span></span>

-   <span data-ttu-id="fca78-156">**“数学”** 运算中所用操作数的取值必须为数值。</span><span class="sxs-lookup"><span data-stu-id="fca78-156">Operands used in **mathematical** operations must evaluate to a numeric value.</span></span> <span data-ttu-id="fca78-157">例如，23.75 \* 4。</span><span class="sxs-lookup"><span data-stu-id="fca78-157">For example, 23.75 \* 4.</span></span>

-   <span data-ttu-id="fca78-158">用在比较运算（如逻辑运算和相等运算）中的操作数的计算结果必须为兼容的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-158">Operands used in comparison operations, such as logical and equality operations, must evaluate to compatible data types.</span></span>

     <span data-ttu-id="fca78-159">例如，如下示例中的表达式之一使用 DT_DBTIMESTAMPOFFSET 数据类型：</span><span class="sxs-lookup"><span data-stu-id="fca78-159">For example, one of the expressions in the following example uses the DT_DBTIMESTAMPOFFSET data type:</span></span>

     `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30" != (DT_DBDATE)"1999-10-12"`

     <span data-ttu-id="fca78-160">系统将表达式 `(DT_DBDATE)"1999-10-12"`转换为 DT_DBTIMESTAMPOFFSET。</span><span class="sxs-lookup"><span data-stu-id="fca78-160">The system converts the expression, `(DT_DBDATE)"1999-10-12"`, to DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="fca78-161">此示例的计算结果为 TRUE，因为转换后的表达式变成 "1999-10-12 00:00:00.000 +00:00"，这与另一个表达式 `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30"`的值不相等。</span><span class="sxs-lookup"><span data-stu-id="fca78-161">The example evaluates to TRUE because the converted expression becomes "1999-10-12 00:00:00.000 +00:00", which is not equal to the value of the other expression, `(DT_DBTIMESTAMPOFFSET,3) "1999-10-11 20:34:52.123 -3:30"`.</span></span>

-   <span data-ttu-id="fca78-162">传递给数学函数的参数的取值必须为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-162">Arguments passed to mathematical functions must evaluate to a numeric data type.</span></span> <span data-ttu-id="fca78-163">根据函数或运算的不同，可能需要特定的数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-163">Depending on the function or operation, a specific numeric data type may be required.</span></span> <span data-ttu-id="fca78-164">例如，HEX 函数需要有符号或无符号整数。</span><span class="sxs-lookup"><span data-stu-id="fca78-164">For example, the HEX function requires a signed or unsigned integer.</span></span>

-   <span data-ttu-id="fca78-165">传递给字符串函数的参数的取值必须为字符数据类型：DT_STR 或 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="fca78-165">Arguments passed to string functions must evaluate to a character data type: DT_STR or DT_WSTR.</span></span> <span data-ttu-id="fca78-166">例如，UPPER("flower")。</span><span class="sxs-lookup"><span data-stu-id="fca78-166">For example, UPPER("flower").</span></span> <span data-ttu-id="fca78-167">某些字符串函数（如 SUBSTRING）需要其他整数参数来作为字符串的起始位置和长度。</span><span class="sxs-lookup"><span data-stu-id="fca78-167">Some string functions, such as SUBSTRING, require additional integer arguments for the start position and the length of the string.</span></span>

-   <span data-ttu-id="fca78-168">传递给日期和时间函数的参数的取值必须为有效日期。</span><span class="sxs-lookup"><span data-stu-id="fca78-168">Arguments passed to date and time functions must evaluate to a valid date.</span></span> <span data-ttu-id="fca78-169">例如，DAY(GETDATE())。</span><span class="sxs-lookup"><span data-stu-id="fca78-169">For example, DAY(GETDATE()).</span></span> <span data-ttu-id="fca78-170">某些函数（如 DATEADD）需要其他整数参数来作为函数加到某个日期的天数。</span><span class="sxs-lookup"><span data-stu-id="fca78-170">Some functions, such as DATEADD, require an additional integer argument for the number of days the function adds to a date.</span></span>

 <span data-ttu-id="fca78-171">兼具无符号八字节整数和有符号整数的运算需要显式转换才能使结果格式清楚明了。</span><span class="sxs-lookup"><span data-stu-id="fca78-171">Operations that combine an unsigned eight-byte integer and a signed integer require an explicit cast to clarify the result format.</span></span> <span data-ttu-id="fca78-172">有关详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="fca78-172">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>

 <span data-ttu-id="fca78-173">许多运算和函数的结果具有预设的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-173">Results of many operations and functions have predetermined data types.</span></span> <span data-ttu-id="fca78-174">该类型可能是参数的数据类型，也可能是表达式计算器将结果转换到的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-174">This can be the data type of the argument or the data type to which the expression evaluator casts the result.</span></span> <span data-ttu-id="fca78-175">例如，逻辑或运算符 (||) 的计算结果始终为布尔值，ABS 函数的计算结果是参数的数值数据类型，乘法运算的结果是可完整保存结果的最小数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="fca78-175">For example, the result of a logical OR operator (||) is always a Boolean, the result of the ABS function is the numeric data type of the argument, and the result of multiplication is the smallest numeric data type that can hold the result without loss.</span></span> <span data-ttu-id="fca78-176">有关结果的数据类型的详细信息，请参阅[运算符（SSIS 表达式）](operators-ssis-expression.md)和[函数（SSIS 表达式）](functions-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="fca78-176">For more information about the data types of results, see [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) and [Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="fca78-177">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fca78-177">Related Tasks</span></span>
 [<span data-ttu-id="fca78-178">在数据流组件中使用表达式</span><span class="sxs-lookup"><span data-stu-id="fca78-178">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)

## <a name="related-content"></a><span data-ttu-id="fca78-179">相关内容</span><span class="sxs-lookup"><span data-stu-id="fca78-179">Related Content</span></span>

-   <span data-ttu-id="fca78-180">pragmaticworks.com 上的技术文章 [SSIS 表达式小抄表](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet3)。</span><span class="sxs-lookup"><span data-stu-id="fca78-180">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet3), on pragmaticworks.com</span></span>

-   <span data-ttu-id="fca78-181">social.technet.microsoft.com 上的技术文章 [SSIS 表达式示例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="fca78-181">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>


