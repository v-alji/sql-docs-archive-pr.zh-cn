---
title: Cast（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CAST function
- cast operator
- converting data types [Integration Services]
- data types [Integration Services], expressions
- data types [Integration Services], converting
ms.assetid: d4e915cc-1c7b-4b2e-93b0-13a8b0cb9242
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65d60eca4340b65b8a82855c3f2b29a6cda56e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691834"
---
# <a name="cast-ssis-expression"></a><span data-ttu-id="9fc61-102">Cast（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9fc61-102">Cast (SSIS Expression)</span></span>
  <span data-ttu-id="9fc61-103">将表达式从一种数据类型显式转换为另一种数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-103">Explicitly converts an expression from one data type to a different data type.</span></span> <span data-ttu-id="9fc61-104">转换运算符还可以用作截断运算符。</span><span class="sxs-lookup"><span data-stu-id="9fc61-104">The cast operator can also function as a truncation operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fc61-105">语法</span><span class="sxs-lookup"><span data-stu-id="9fc61-105">Syntax</span></span>

```

(type_spec) expression

```

## <a name="arguments"></a><span data-ttu-id="9fc61-106">参数</span><span class="sxs-lookup"><span data-stu-id="9fc61-106">Arguments</span></span>
 <span data-ttu-id="9fc61-107">*type_spec*是有效的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-107">*type_spec* Is a valid [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span>

 <span data-ttu-id="9fc61-108">*表达式*是有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="9fc61-108">*expression* Is a valid expression.</span></span>

## <a name="result-types"></a><span data-ttu-id="9fc61-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="9fc61-109">Result Types</span></span>
 <span data-ttu-id="9fc61-110">*type_spec*数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-110">The data type of *type_spec*.</span></span> <span data-ttu-id="9fc61-111">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9fc61-111">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="9fc61-112">备注</span><span class="sxs-lookup"><span data-stu-id="9fc61-112">Remarks</span></span>
 <span data-ttu-id="9fc61-113">以下关系图显示了合法的转换运算。</span><span class="sxs-lookup"><span data-stu-id="9fc61-113">The following diagram shows legal cast operations.</span></span>

 <span data-ttu-id="9fc61-114">![数据类型之间的合法转换和非法转换](../media/data-conversion.gif "数据类型之间的合法转换和非法转换")</span><span class="sxs-lookup"><span data-stu-id="9fc61-114">![Legal and not legal casts between data types](../media/data-conversion.gif "Legal and not legal casts between data types")</span></span>

 <span data-ttu-id="9fc61-115">转换为某些数据类型时需要参数。</span><span class="sxs-lookup"><span data-stu-id="9fc61-115">Casting to some data types requires parameters.</span></span> <span data-ttu-id="9fc61-116">下表列出了这些数据类型及其参数。</span><span class="sxs-lookup"><span data-stu-id="9fc61-116">The following table lists these data types and their parameters.</span></span>

|<span data-ttu-id="9fc61-117">数据类型</span><span class="sxs-lookup"><span data-stu-id="9fc61-117">Data type</span></span>|<span data-ttu-id="9fc61-118">参数</span><span class="sxs-lookup"><span data-stu-id="9fc61-118">Parameter</span></span>|<span data-ttu-id="9fc61-119">示例</span><span class="sxs-lookup"><span data-stu-id="9fc61-119">Example</span></span>|
|---------------|---------------|-------------|
|<span data-ttu-id="9fc61-120">DT_STR</span><span class="sxs-lookup"><span data-stu-id="9fc61-120">DT_STR</span></span>|<span data-ttu-id="9fc61-121">*charcount*</span><span class="sxs-lookup"><span data-stu-id="9fc61-121">*charcount*</span></span><br /><br /> <span data-ttu-id="9fc61-122">*ansi*</span><span class="sxs-lookup"><span data-stu-id="9fc61-122">*codepage*</span></span>|<span data-ttu-id="9fc61-123">(DT_STR,30,1252) 将 30 个字节（即 30 个单字符）转换为使用 1252 代码页的 DT_STR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-123">(DT_STR,30,1252) casts 30 bytes, or 30 single characters, to the DT_STR data type using the 1252 code page.</span></span>|
|<span data-ttu-id="9fc61-124">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9fc61-124">DT_WSTR</span></span>|<span data-ttu-id="9fc61-125">*Charcount*</span><span class="sxs-lookup"><span data-stu-id="9fc61-125">*Charcount*</span></span>|<span data-ttu-id="9fc61-126">(DT_WSTR,20) 将 20 个字节对（即 20 个 Unicode 字符）转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-126">(DT_WSTR,20) casts 20 byte pairs, or 20 Unicode characters, to the DT_WSTR data type.</span></span>|
|<span data-ttu-id="9fc61-127">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="9fc61-127">DT_BYTES</span></span>|<span data-ttu-id="9fc61-128">*Bytecount*</span><span class="sxs-lookup"><span data-stu-id="9fc61-128">*Bytecount*</span></span>|<span data-ttu-id="9fc61-129">(DT_BYTES,50) 将 50 个字节的数据转换为 DT_BYTES 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-129">(DT_BYTES,50) casts 50 bytes to the DT_BYTES data type.</span></span>|
|<span data-ttu-id="9fc61-130">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="9fc61-130">DT_DECIMAL</span></span>|<span data-ttu-id="9fc61-131">*缩放*</span><span class="sxs-lookup"><span data-stu-id="9fc61-131">*Scale*</span></span>|<span data-ttu-id="9fc61-132">(DT_DECIMAL,2) 将数值转换为带 2 位小数的 DT_DECIMAL 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-132">(DT_DECIMAL,2) casts a numeric value to the DT_DECIMAL data type using a scale of 2.</span></span>|
|<span data-ttu-id="9fc61-133">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="9fc61-133">DT_NUMERIC</span></span>|<span data-ttu-id="9fc61-134">*精度*</span><span class="sxs-lookup"><span data-stu-id="9fc61-134">*Precision*</span></span><br /><br /> <span data-ttu-id="9fc61-135">*缩放*</span><span class="sxs-lookup"><span data-stu-id="9fc61-135">*Scale*</span></span>|<span data-ttu-id="9fc61-136">(DT_NUMERIC,10,3) 将数值转换为带 3 位小数且精度为 10 的 DT_NUMERIC 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-136">(DT_NUMERIC,10,3) casts a numeric value to the DT_NUMERIC data type using a precision of 10 and a scale of 3.</span></span>|
|<span data-ttu-id="9fc61-137">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="9fc61-137">DT_TEXT</span></span>|<span data-ttu-id="9fc61-138">*Ansi*</span><span class="sxs-lookup"><span data-stu-id="9fc61-138">*Codepage*</span></span>|<span data-ttu-id="9fc61-139">(DT_TEXT,1252) 将值转换为使用 1252 代码页的 DT_TEXT 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-139">(DT_TEXT,1252) casts a value to the DT_TEXT data type using the 1252 code page.</span></span>|

 <span data-ttu-id="9fc61-140">字符串和 DT_DATE 间相互转换时，将使用转换的区域设置。</span><span class="sxs-lookup"><span data-stu-id="9fc61-140">When a string is cast to a DT_DATE, or vice versa, the locale of the transformation is used.</span></span> <span data-ttu-id="9fc61-141">但是，无论区域设置首选项是否使用 YYYY-MM-DD 这一 ISO 格式，日期均采用该 ISO 格式。</span><span class="sxs-lookup"><span data-stu-id="9fc61-141">However, the date is in the ISO format of YYYY-MM-DD, regardless of whether the locale preference uses the ISO format.</span></span>

> [!NOTE]
>  <span data-ttu-id="9fc61-142">若要将字符串转换为 DT_DATE 以外的日期数据类型，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9fc61-142">To convert a string to a date data type other than DT_DATE, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="9fc61-143">如果代码页为多字节字符代码页，则字节数和字符数可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="9fc61-143">If the code page is a multibyte character code page, the number of bytes and characters may differ.</span></span> <span data-ttu-id="9fc61-144">将具有相同的 *charcount* 值的 DT_WSTR 转换为 DT_STR 时，可能导致转换后的字符串的最后字符被截断。</span><span class="sxs-lookup"><span data-stu-id="9fc61-144">Casting from a DT_WSTR to a DT_STR with the same *charcount* value may cause truncation of the final characters in the converted string.</span></span> <span data-ttu-id="9fc61-145">如果在目标表的列中有足够的存储区，则可设置 *charcount* 参数的值以反映多字节代码页所需的字节数。</span><span class="sxs-lookup"><span data-stu-id="9fc61-145">If sufficient storage is available in the column of the destination table, set the value of the *charcount* parameter to reflect the number of bytes that the multibyte code page requires.</span></span> <span data-ttu-id="9fc61-146">例如，如果将字符数据转换为使用 936 代码页的 DT_STR 数据类型，则应将 *charcount* 的值设置为希望数据包含的字符数的两倍；如果要转换使用 UTF-8 代码页字符数据，则应将 *charcount* 值设置为四倍以上。</span><span class="sxs-lookup"><span data-stu-id="9fc61-146">For example, if you cast character data to a DT_STR data type using the 936 code page, you should set *charcount* to a value up to two times greater than the number of characters that you expect the data to contain; if you cast character data using the UTF-8 code page, you should set *charcount* to a value up to four times greater.</span></span>

 <span data-ttu-id="9fc61-147">有关日期数据类型结构的详细信息，请参阅 [Integration Services Data Types](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9fc61-147">For more information about the structure of date data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

## <a name="ssis-expression-examples"></a><span data-ttu-id="9fc61-148">SSIS 表达式示例</span><span class="sxs-lookup"><span data-stu-id="9fc61-148">SSIS Expression Examples</span></span>
 <span data-ttu-id="9fc61-149">以下示例将一个数值转换为整数。</span><span class="sxs-lookup"><span data-stu-id="9fc61-149">This example casts a numeric value to an integer.</span></span>

```
(DT_I4) 3.57
```

 <span data-ttu-id="9fc61-150">以下示例将整数转换为使用 1252 代码页的字符串。</span><span class="sxs-lookup"><span data-stu-id="9fc61-150">This example casts an integer to a character string using the 1252 code page.</span></span>

```
(DT_STR,1,1252)5
```

 <span data-ttu-id="9fc61-151">以下示例将三字符字符串转换为双字节字符。</span><span class="sxs-lookup"><span data-stu-id="9fc61-151">This example casts a three-character string to double-byte characters.</span></span>

```
(DT_WSTR,3)"Cat"
```

 <span data-ttu-id="9fc61-152">以下示例将整数转换为带两位小数的十进制数。</span><span class="sxs-lookup"><span data-stu-id="9fc61-152">This example casts an integer to a decimal with a scale of two.</span></span>

```
(DT_DECIMAl,2)500
```

 <span data-ttu-id="9fc61-153">此示例将整数转换为带 3 位小数且精度为 7 的数值。</span><span class="sxs-lookup"><span data-stu-id="9fc61-153">This example casts an integer to a numeric with a precision of seven and scale of three.</span></span>

```
(DT_NUMERIC,7,3)4000
```

 <span data-ttu-id="9fc61-154">以下示例将 **FirstName** 列中的值（定义为 **nvarchar** 数据类型且长度 50）转换为使用 1252 代码页的字符串。</span><span class="sxs-lookup"><span data-stu-id="9fc61-154">This example casts values in the **FirstName** column, defined with an **nvarchar** data type and a length of 50, to a character string using the 1252 code page.</span></span>

```
(DT_STR,50,1252)FirstName
```

 <span data-ttu-id="9fc61-155">本示例将类型为 DT_DBDATE 的 **DateFirstPurchase** 列中的值转换为长度为 20 的 Unicode 字符串。</span><span class="sxs-lookup"><span data-stu-id="9fc61-155">This example casts values in the **DateFirstPurchase** column of type DT_DBDATE, to a Unicode character string with a length of 20.</span></span>

```
(DT_WSTR,20)DateFirstPurchase
```

 <span data-ttu-id="9fc61-156">以下示例将字符串文字“True”转换为布尔值。</span><span class="sxs-lookup"><span data-stu-id="9fc61-156">This example casts the string literal "True" to a Boolean.</span></span>

```
(DT_BOOL)"True"
```

 <span data-ttu-id="9fc61-157">下面的示例将字符串文字转换为 DT_DBDATE。</span><span class="sxs-lookup"><span data-stu-id="9fc61-157">This example casts a string literal to DT_DBDATE.</span></span>

```
(DT_DBDATE) "1999-10-11"
```

 <span data-ttu-id="9fc61-158">下面的示例将字符串文字转换为使用 5 位小数秒的 DT_DBTIME2 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-158">This example casts a string literal to the DT_DBTIME2 data type that uses 5 digits for fractional seconds.</span></span> <span data-ttu-id="9fc61-159">（对于 DT_DBTIME2 数据类型可以指定 0 到 7 位小数秒。）</span><span class="sxs-lookup"><span data-stu-id="9fc61-159">(The DT_DBTIME2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIME2, 5) "16:34:52.12345"
```

 <span data-ttu-id="9fc61-160">下面的示例将字符串文字转换为使用 4 位小数秒的 DT_DBTIMESTAMP2 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-160">This example casts a string literal to the DT_DBTIMESTAMP2 data type that uses 4 digits for fractional seconds.</span></span> <span data-ttu-id="9fc61-161">（对于 DT_DBTIMESTAMP2 数据类型可以指定 0 到 7 位小数秒。）</span><span class="sxs-lookup"><span data-stu-id="9fc61-161">(The DT_DBTIMESTAMP2 data type can have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMP2, 4) "1999-10-11 16:34:52.1234"
```

 <span data-ttu-id="9fc61-162">下面的示例将字符串文字转换为使用 7 位小数秒的 DT_DBTIMESTAMPOFFSET 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9fc61-162">This example casts a string literal to the DT_DBTIMESTAMPOFFSET data type that uses 7 digits for fractional seconds.</span></span> <span data-ttu-id="9fc61-163">（对于 DT_DBTIMESTAMPOFFSET 数据类型可以指定 0 到 7 位小数秒。）</span><span class="sxs-lookup"><span data-stu-id="9fc61-163">(The DT_DBTIMESTAMPOFFSET data typecan have between 0 and 7 digits specified for fractional seconds.)</span></span>

```
(DT_DBTIMESTAMPOFFSET, 7) "1999-10-11 16:34:52.1234567 + 5:35"
```

## <a name="see-also"></a><span data-ttu-id="9fc61-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fc61-164">See Also</span></span>
 <span data-ttu-id="9fc61-165">[运算符优先级和关联](operator-precedence-and-associativity.md)[运算符 &#40;ssis 表达式&#41;](operators-ssis-expression.md) [Integration Services &#40;Ssis&#41;](integration-services-ssis-expressions.md)表达式[中的数据类型](integration-services-data-types-in-expressions.md)Integration Services 表达式</span><span class="sxs-lookup"><span data-stu-id="9fc61-165">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)</span></span>


