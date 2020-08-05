---
title: '&lt;=（小于或等于）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 946c5630-dccf-4dae-9cfd-6ea823641ab2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1c0b5ef0a8467cedbc5e390b42f3307cceb7c75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580789"
---
# <a name="lt-less-than-or-equal-to-ssis-expression"></a><span data-ttu-id="5d7e4-102">&lt;=（小于或等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5d7e4-102">&lt;= (Less Than or Equal To) (SSIS Expression)</span></span>
  <span data-ttu-id="5d7e4-103">通过比较确定第一个表达式是否小于或等于第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-103">Performs a comparison to determine if the first expression is less than or equal to the second one.</span></span> <span data-ttu-id="5d7e4-104">在执行比较前表达式计算器会自动转换多种数据类型。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d7e4-105">该运算符不支持对使用 DT_TEXT、DT_NTEXT 或 DT_IMAGE 数据类型的表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-105">This operator does not support comparisons that use the DT_TEXT, DT_NTEXT, or DT_IMAGE data types.</span></span>  
  
 <span data-ttu-id="5d7e4-106">但是，某些数据类型要求表达式包括显式转换，才能成功进行计算。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-106">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="5d7e4-107">有关数据类型之间的合法转换的详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-107">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d7e4-108">此运算符的两个字符之间没有空格。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-108">There are no spaces between the two characters in this operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d7e4-109">语法</span><span class="sxs-lookup"><span data-stu-id="5d7e4-109">Syntax</span></span>  
  
```  
  
expression1 <= expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d7e4-110">参数</span><span class="sxs-lookup"><span data-stu-id="5d7e4-110">Arguments</span></span>  
 <span data-ttu-id="5d7e4-111">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="5d7e4-111">*expression1, expression2*</span></span>  
 <span data-ttu-id="5d7e4-112">为任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-112">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5d7e4-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="5d7e4-113">Result Types</span></span>  
 <span data-ttu-id="5d7e4-114">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="5d7e4-114">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d7e4-115">备注</span><span class="sxs-lookup"><span data-stu-id="5d7e4-115">Remarks</span></span>  
 <span data-ttu-id="5d7e4-116">如果比较中的任一表达式为空，则比较结果为空。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-116">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="5d7e4-117">如果两个表达式都为空，则结果为空。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-117">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="5d7e4-118">表达式集， *expression1* 和 *expression2*，必须遵守下列规则之一：</span><span class="sxs-lookup"><span data-stu-id="5d7e4-118">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="5d7e4-119">\**Numeric\*\*\*expression1* 和 *expression2* 必须为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-119">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="5d7e4-120">数据类型的交集必须为数值数据类型，该类型在表达式计算器执行隐式数值转换的规则中指定。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-120">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="5d7e4-121">两个数值数据类型的交集不能为空。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-121">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="5d7e4-122">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-122">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="5d7e4-123">**Character** ： *expression1* 和 *expression2* 的计算结果必须为 DT_STR 或 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-123">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="5d7e4-124">两个表达式的计算结果可以为不同的字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-124">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d7e4-125">字符串比较区分大小写、重音、假名和全半角。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-125">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="5d7e4-126">\**Date、Time 或 Date/Time\*\*\*expression1* 和 *expression2* 的计算结果必须为下列数据类型之一：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-126">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5d7e4-127">系统不支持对计算结果为时间数据类型的表达式和计算结果为日期或日期/时间数据类型的表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-127">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="5d7e4-128">否则系统会生成错误。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-128">The system generates an error.</span></span>  
  
     <span data-ttu-id="5d7e4-129">在对表达式进行比较时，系统会按照所列出的顺序应用下面的转换规则：</span><span class="sxs-lookup"><span data-stu-id="5d7e4-129">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="5d7e4-130">当两个表达式的计算结果为同一个数据类型时，则会执行该数据类型的比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-130">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="5d7e4-131">如果一个表达式是 DT_DBTIMESTAMPOFFSET 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMPOFFSET，并执行 DT_DBTIMESTAMPOFFSET 比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-131">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="5d7e4-132">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-132">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="5d7e4-133">如果一个表达式是 DT_DBTIMESTAMP2 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMP2，并执行 DT_DBTIMESTAMP2 比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-133">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="5d7e4-134">如果一个表达式是 DT_DBTIME2 数据类型，则另一个表达式会隐式转换为 DT_DBTIME2，并执行 DT_DBTIME2 比较。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-134">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="5d7e4-135">如果一个表达式是 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2 以外的类型，那么，在对表达式进行比较之前，会将它们转换为 DT_DBTIMESTAMP 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-135">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="5d7e4-136">在对表达式进行比较时，系统会进行如下假设：</span><span class="sxs-lookup"><span data-stu-id="5d7e4-136">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="5d7e4-137">如果每个表达式的数据类型都包含小数秒，则系统会假设对于小数秒位数最少的数据类型，用零填充其余位。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-137">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="5d7e4-138">如果每个表达式都是日期数据类型，但是只有一个表达式具有时区偏移量，系统会假设没有时区偏移量的日期数据类型采用的是协调世界时 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-138">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="5d7e4-139">有关数据类型的详细信息，请参阅 [Integration Services Data Types](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-139">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5d7e4-140">表达式示例</span><span class="sxs-lookup"><span data-stu-id="5d7e4-140">Expression Examples</span></span>  
 <span data-ttu-id="5d7e4-141">如果当前日期等于或晚于 2003 年 7 月 4 日，则此示例的计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-141">This example evaluates to TRUE if the current date is July 4, 2003 or later.</span></span> <span data-ttu-id="5d7e4-142">有关详细信息，请参阅 [GETDATE（SSIS 表达式）](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-142">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" <= GETDATE()  
```  
  
 <span data-ttu-id="5d7e4-143">如果 **ListPrice** 列中的值小于或等于 500，则此示例的计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-143">This example evaluates to TRUE if the value in the **ListPrice** column is less than or equal to 500.</span></span>  
  
```  
ListPrice <= 500  
```  
  
 <span data-ttu-id="5d7e4-144">此示例先计算变量 **LPrice** 的值，如果该值小于或等于 500，则示例的计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-144">This example evaluates the variable **LPrice** and evaluates to TRUE if the value is less than or equal to 500.</span></span> <span data-ttu-id="5d7e4-145">**LPrice** 的数据类型必须为数值以便分析表达式。</span><span class="sxs-lookup"><span data-stu-id="5d7e4-145">The data type of **LPrice** must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice <= 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d7e4-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d7e4-146">See Also</span></span>  
 <span data-ttu-id="5d7e4-147">[>（大于）（SSIS 表达式）](greater-than-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5d7e4-147">[&#62; &#40;Greater Than&#41; &#40;SSIS Expression&#41;](greater-than-ssis-expression.md) </span></span>  
 <span data-ttu-id="5d7e4-148">[>（小于）（SSIS 表达式）](less-than-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5d7e4-148">[&#60; &#40;Less Than&#41; &#40;SSIS Expression&#41;](less-than-ssis-expression.md) </span></span>  
 <span data-ttu-id="5d7e4-149">[>=（大于或等于）（SSIS 表达式）](greater-than-or-equal-to-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="5d7e4-149">[&#62;= &#40;Greater Than or Equal To&#41; &#40;SSIS Expression&#41;](greater-than-or-equal-to-ssis-expression.md) </span></span>  
 <span data-ttu-id="5d7e4-150">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="5d7e4-150">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="5d7e4-151">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5d7e4-151">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
