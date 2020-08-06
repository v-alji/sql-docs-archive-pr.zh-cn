---
title: '? :（条件）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e607f9ed495184ef47ac2e4f1139b9a9566055ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590928"
---
# <a name="--conditional-ssis-expression"></a><span data-ttu-id="f5ce6-103">?</span><span class="sxs-lookup"><span data-stu-id="f5ce6-103">?</span></span> <span data-ttu-id="f5ce6-104">:（条件）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5ce6-104">: (Conditional) (SSIS Expression)</span></span>
  <span data-ttu-id="f5ce6-105">根据布尔表达式的计算结果，返回两个表达式之一。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-105">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span> <span data-ttu-id="f5ce6-106">如果布尔表达式的计算结果为 TRUE，则计算第一个表达式，结果为该表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-106">If the Boolean expression evaluates to TRUE, then the first expression is evaluated and the result is the expression result.</span></span> <span data-ttu-id="f5ce6-107">如果布尔表达式的计算结果为 FALSE，则计算第二个表达式，结果为该表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-107">If the Boolean expression evaluates to FALSE then the second expression is evaluated and its result is the expression result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ce6-108">语法</span><span class="sxs-lookup"><span data-stu-id="f5ce6-108">Syntax</span></span>  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5ce6-109">参数</span><span class="sxs-lookup"><span data-stu-id="f5ce6-109">Arguments</span></span>  
 <span data-ttu-id="f5ce6-110">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="f5ce6-110">*boolean_expression*</span></span>  
 <span data-ttu-id="f5ce6-111">计算结果为 TRUE、FALSE 或 NULL 的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-111">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
 <span data-ttu-id="f5ce6-112">*expression1*</span><span class="sxs-lookup"><span data-stu-id="f5ce6-112">*expression1*</span></span>  
 <span data-ttu-id="f5ce6-113">为任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-113">Is any valid expression.</span></span>  
  
 <span data-ttu-id="f5ce6-114">*expression2*</span><span class="sxs-lookup"><span data-stu-id="f5ce6-114">*expression2*</span></span>  
 <span data-ttu-id="f5ce6-115">为任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-115">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f5ce6-116">结果类型</span><span class="sxs-lookup"><span data-stu-id="f5ce6-116">Result Types</span></span>  
 <span data-ttu-id="f5ce6-117">*expression1* 或 *expression2*的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-117">The data type of *expression1* or *expression2*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5ce6-118">备注</span><span class="sxs-lookup"><span data-stu-id="f5ce6-118">Remarks</span></span>  
 <span data-ttu-id="f5ce6-119">如果 *boolean_expression* 的计算结果为 NULL，则表达式结果为 NULL。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-119">If the *boolean_expression* evaluates to NULL, the expression result is NULL.</span></span> <span data-ttu-id="f5ce6-120">如果选择的表达式（ *expression1* 或 *expression2* ）为 NULL，则结果为 NULL。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-120">If a selected expression, either *expression1* or *expression2* is NULL, the result is NULL.</span></span> <span data-ttu-id="f5ce6-121">如果选择的表达式不为 NULL，但未选择的表达式为 NULL，则结果为所选表达式的值。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-121">If a selected expression is not NULL, but the one not selected is NULL, the result is the value of the selected expression.</span></span>  
  
 <span data-ttu-id="f5ce6-122">如果 *expression1* 和 *expression2* 的数据类型相同，则结果便为该数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-122">If *expression1* and *expression2* have the same data type, the result is that data type.</span></span> <span data-ttu-id="f5ce6-123">对于结果类型适用于下列附加规则：</span><span class="sxs-lookup"><span data-stu-id="f5ce6-123">The following additional rules apply to result types:</span></span>  
  
-   <span data-ttu-id="f5ce6-124">DT_TEXT 数据类型要求 *expression1* 和 *expression2* 具有相同的代码页。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-124">The DT_TEXT data type requires that *expression1* and *expression2* have the same code page.</span></span>  
  
-   <span data-ttu-id="f5ce6-125">DT_BYTES 数据类型的结果长度是较长参数的长度。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-125">The length of a result with the DT_BYTES data type is the length of the longer argument.</span></span>  
  
 <span data-ttu-id="f5ce6-126">表达式集（ *expression1* 和 *expression2*）的计算结果必须为有效的数据类型而且必须遵循下列规则之一：</span><span class="sxs-lookup"><span data-stu-id="f5ce6-126">The expression set, *expression1* and *expression2*, must evaluate to valid data types and follow one of these rules:</span></span>  
  
-   <span data-ttu-id="f5ce6-127">\**Numeric\*\*\*expression1* 和 *expression2* 必须为数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-127">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="f5ce6-128">数据类型的交集必须为数值数据类型，该类型在表达式计算器执行隐式数值转换的规则中指定。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-128">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="f5ce6-129">两个数值数据类型的交集不能为空。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-129">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="f5ce6-130">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="f5ce6-131">\**字符串\*\*\*expression1* 和 *expression2* 必须为字符串数据类型：DT_STR 或 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-131">**String** Both *expression1* and *expression2* must be a string data type: DT_STR or DT_WSTR.</span></span> <span data-ttu-id="f5ce6-132">两个表达式的计算结果可以为不同的字符串数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-132">The two expressions can evaluate to different string data types.</span></span> <span data-ttu-id="f5ce6-133">结果为 DT_WSTR 数据类型，其长度为较长参数的长度。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-133">The result has the DT_WSTR data type with a length of the longer argument.</span></span>  
  
-   <span data-ttu-id="f5ce6-134">\**Date、Time 或 Date/Time\*\*\*expression1* 和 *expression2* 的计算结果必须为下列数据类型之一：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-134">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f5ce6-135">系统不支持对计算结果为时间数据类型的表达式和计算结果为日期或日期/时间数据类型的表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-135">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="f5ce6-136">否则系统会生成错误。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-136">The system generates an error.</span></span>  
  
     <span data-ttu-id="f5ce6-137">在对表达式进行比较时，系统会按照所列出的顺序应用下面的转换规则：</span><span class="sxs-lookup"><span data-stu-id="f5ce6-137">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="f5ce6-138">当两个表达式的计算结果为同一个数据类型时，则会执行该数据类型的比较。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-138">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="f5ce6-139">如果一个表达式是 DT_DBTIMESTAMPOFFSET 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMPOFFSET，并执行 DT_DBTIMESTAMPOFFSET 比较。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-139">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="f5ce6-140">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-140">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="f5ce6-141">如果一个表达式是 DT_DBTIMESTAMP2 数据类型，则另一个表达式会隐式转换为 DT_DBTIMESTAMP2，并执行 DT_DBTIMESTAMP2 比较。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-141">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="f5ce6-142">如果一个表达式是 DT_DBTIME2 数据类型，则另一个表达式会隐式转换为 DT_DBTIME2，并执行 DT_DBTIME2 比较。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-142">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="f5ce6-143">如果一个表达式是 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2 以外的类型，那么，在对表达式进行比较之前，会将它们转换为 DT_DBTIMESTAMP 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-143">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="f5ce6-144">在对表达式进行比较时，系统会进行如下假设：</span><span class="sxs-lookup"><span data-stu-id="f5ce6-144">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="f5ce6-145">如果每个表达式的数据类型都包含小数秒，则系统会假设对于小数秒位数最少的数据类型，用零填充其余位。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-145">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="f5ce6-146">如果每个表达式都是日期数据类型，但是只有一个表达式具有时区偏移量，系统会假设没有时区偏移量的日期数据类型采用的是协调世界时 (UTC)。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-146">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="f5ce6-147">有关数据类型的详细信息，请参阅 [Integration Services Data Types](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-147">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f5ce6-148">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f5ce6-148">Expression Examples</span></span>  
 <span data-ttu-id="f5ce6-149">以下示例显示根据条件计算结果为 `savannah` 或 `unknown`的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-149">This example shows an expression that conditionally evaluates to `savannah` or `unknown`.</span></span>  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 <span data-ttu-id="f5ce6-150">以下示例显示引用 **ListPrice** 列的表达式。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-150">This example shows an expression that references a **ListPrice** column.</span></span> <span data-ttu-id="f5ce6-151">**ListPrice** 具有 DT_CY 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-151">**ListPrice** has the DT_CY data type.</span></span> <span data-ttu-id="f5ce6-152">表达式根据条件将 **ListPrice** 乘以 0.2 或 0.1。</span><span class="sxs-lookup"><span data-stu-id="f5ce6-152">The expression conditionally multiplies **ListPrice** by .2 or .1.</span></span>  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5ce6-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5ce6-153">See Also</span></span>  
 <span data-ttu-id="f5ce6-154">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="f5ce6-154">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="f5ce6-155">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5ce6-155">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
