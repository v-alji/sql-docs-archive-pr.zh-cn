---
title: '!=（不等于）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- unequal operator (!=)
- '!= (not equal to)'
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be3eadbac77d76a2b3aac9555d9f40cb56e38949
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689951"
---
# <a name="-unequal-ssis-expression"></a><span data-ttu-id="c88bf-102">!=（不等于）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c88bf-102">!= (Unequal) (SSIS Expression)</span></span>
  <span data-ttu-id="c88bf-103">执行比较操作以确定具有兼容数据类型的两个表达式是否不相等。</span><span class="sxs-lookup"><span data-stu-id="c88bf-103">Performs a comparison to determine if two expressions with compatible data types are not equal.</span></span> <span data-ttu-id="c88bf-104">在执行比较前表达式计算器会自动转换多种数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
 <span data-ttu-id="c88bf-105">但是，某些数据类型要求表达式包括显式转换，才能成功进行计算。</span><span class="sxs-lookup"><span data-stu-id="c88bf-105">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="c88bf-106">有关数据类型之间的合法转换的详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-106">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c88bf-107">语法</span><span class="sxs-lookup"><span data-stu-id="c88bf-107">Syntax</span></span>  
  
```  
  
expression1 != expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c88bf-108">参数</span><span class="sxs-lookup"><span data-stu-id="c88bf-108">Arguments</span></span>  
 <span data-ttu-id="c88bf-109">*expression1、expression2*</span><span class="sxs-lookup"><span data-stu-id="c88bf-109">*expression1, expression2*</span></span>  
 <span data-ttu-id="c88bf-110">为任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="c88bf-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c88bf-111">结果类型</span><span class="sxs-lookup"><span data-stu-id="c88bf-111">Result Types</span></span>  
 <span data-ttu-id="c88bf-112">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="c88bf-112">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c88bf-113">备注</span><span class="sxs-lookup"><span data-stu-id="c88bf-113">Remarks</span></span>  
 <span data-ttu-id="c88bf-114">如果比较中的任一表达式为空，则比较结果为空。</span><span class="sxs-lookup"><span data-stu-id="c88bf-114">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="c88bf-115">如果两个表达式都为空，则结果为空。</span><span class="sxs-lookup"><span data-stu-id="c88bf-115">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="c88bf-116">表达式集， *expression1* 和 *expression2*，必须遵守下列规则之一：</span><span class="sxs-lookup"><span data-stu-id="c88bf-116">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="c88bf-117">\**Numeric\*\*\*expression1* 和 *expression2* 必须为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-117">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="c88bf-118">数据类型的交集必须为数值数据类型，此类型在表达式计算器隐式数值转换的有关规则中指定。</span><span class="sxs-lookup"><span data-stu-id="c88bf-118">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="c88bf-119">两个数值数据类型的交集不能为空。</span><span class="sxs-lookup"><span data-stu-id="c88bf-119">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="c88bf-120">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-120">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="c88bf-121">**Character** ： *expression1* 和 *expression2* 的计算结果必须为 DT_STR 或 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-121">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="c88bf-122">两个表达式的计算结果可以为不同的字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-122">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c88bf-123">字符串比较区分大小写、重音、假名和全半角。</span><span class="sxs-lookup"><span data-stu-id="c88bf-123">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="c88bf-124">\**Date、Time 或 Date/Time\*\*\*expression1* 和 *expression2* 的计算结果必须为下列数据类型之一：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="c88bf-124">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c88bf-125">系统不支持对计算结果为时间数据类型的表达式和计算结果为日期或日期/时间数据类型的表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="c88bf-125">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="c88bf-126">否则系统会生成错误。</span><span class="sxs-lookup"><span data-stu-id="c88bf-126">The system generates an error.</span></span>  
  
     <span data-ttu-id="c88bf-127">在对表达式进行比较时，系统会按照所列出的顺序应用下面的转换规则：</span><span class="sxs-lookup"><span data-stu-id="c88bf-127">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="c88bf-128">当两个表达式的计算结果为同一个数据类型时，则会执行该数据类型的比较。</span><span class="sxs-lookup"><span data-stu-id="c88bf-128">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="c88bf-129">如果一个表达式是 DT_DBTIMESTAMPOFFSET 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMPOFFSET，并执行 DT_DBTIMESTAMPOFFSET 比较。</span><span class="sxs-lookup"><span data-stu-id="c88bf-129">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="c88bf-130">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="c88bf-131">如果一个表达式是 DT_DBTIMESTAMP2 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMP2，并执行 DT_DBTIMESTAMP2 比较。</span><span class="sxs-lookup"><span data-stu-id="c88bf-131">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="c88bf-132">如果一个表达式是 DT_DBTIME2 数据类型，则另一个表达式会隐式转换为 DT_DBTIME2，并执行 DT_DBTIME2 比较。</span><span class="sxs-lookup"><span data-stu-id="c88bf-132">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="c88bf-133">如果一个表达式是 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2 以外的类型，那么，在对表达式进行比较之前，会将它们转换为 DT_DBTIMESTAMP 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-133">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="c88bf-134">在对表达式进行比较时，系统会进行如下假设：</span><span class="sxs-lookup"><span data-stu-id="c88bf-134">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="c88bf-135">如果每个表达式的数据类型都包含小数秒，则系统会假设对于小数秒位数最少的数据类型，用零填充其余位。</span><span class="sxs-lookup"><span data-stu-id="c88bf-135">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="c88bf-136">如果每个表达式都是日期数据类型，但是只有一个表达式具有时区偏移量，系统会假设没有时区偏移量的日期数据类型采用的是协调世界时 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-136">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="c88bf-137">\**Logical\*\*\*expression1* 和 *expression2* 的计算结果必须为布尔值。</span><span class="sxs-lookup"><span data-stu-id="c88bf-137">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="c88bf-138">**GUID** ： *expression1* 和 *expression2* 的计算结果必须为 DT_GUID 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-138">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="c88bf-139">**Binary** ： *expression1* 和 *expression2* 的计算结果必须为 DT_BYTES 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c88bf-139">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="c88bf-140">**BLOB** ： *expression1* 和 *expression2* 的计算结果必须为同一 BLOB（二进制大型对象块）数据类型：DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="c88bf-140">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="c88bf-141">有关数据类型的详细信息，请参阅 [Integration Services Data Types](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-141">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c88bf-142">表达式示例</span><span class="sxs-lookup"><span data-stu-id="c88bf-142">Expression Examples</span></span>  
 <span data-ttu-id="c88bf-143">仅在当前日期不是 2003 年 7 月 4 日时，此示例的计算结果才为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c88bf-143">This example evaluates to TRUE only if the current date is not July 4, 2003.</span></span> <span data-ttu-id="c88bf-144">有关详细信息，请参阅 [GETDATE（SSIS 表达式）](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c88bf-144">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 <span data-ttu-id="c88bf-145">以下示例中，如果 **ListPrice** 列中的值不是 500，则此表达式的计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c88bf-145">This example evaluates to TRUE if the value in the **ListPrice** column is not 500.</span></span>  
  
```  
ListPrice != 500  
```  
  
 <span data-ttu-id="c88bf-146">此示例使用了变量 **LPrice**。</span><span class="sxs-lookup"><span data-stu-id="c88bf-146">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="c88bf-147">如果 **LPrice** 的值不为 500，则此示例的计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c88bf-147">It evaluates to TRUE if the value of **LPrice** is not 500.</span></span> <span data-ttu-id="c88bf-148">该变量的数据类型必须为数值以便分析表达式。</span><span class="sxs-lookup"><span data-stu-id="c88bf-148">The data type on the variable must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice != 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="c88bf-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c88bf-149">See Also</span></span>  
 <span data-ttu-id="c88bf-150">[==（等于）（SSIS 表达式）](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c88bf-150">[== &#40;Equal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="c88bf-151">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="c88bf-151">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="c88bf-152">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c88bf-152">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
