---
title: RIGHT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RIGHT function
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2584ee33ecbf0436c4e3dc6e92b957e60ae396ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689980"
---
# <a name="right-ssis-expression"></a><span data-ttu-id="abb12-102">RIGHT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="abb12-102">RIGHT (SSIS Expression)</span></span>
  <span data-ttu-id="abb12-103">返回从给定字符表达式最右侧开始的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="abb12-103">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb12-104">语法</span><span class="sxs-lookup"><span data-stu-id="abb12-104">Syntax</span></span>  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="abb12-105">参数</span><span class="sxs-lookup"><span data-stu-id="abb12-105">Arguments</span></span>  
 <span data-ttu-id="abb12-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="abb12-106">*character_expression*</span></span>  
 <span data-ttu-id="abb12-107">是从中提取字符的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="abb12-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="abb12-108">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="abb12-108">*integer_expression*</span></span>  
 <span data-ttu-id="abb12-109">指示要返回的字符数的整数表达式。</span><span class="sxs-lookup"><span data-stu-id="abb12-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="abb12-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="abb12-110">Result Types</span></span>  
 <span data-ttu-id="abb12-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="abb12-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abb12-112">备注</span><span class="sxs-lookup"><span data-stu-id="abb12-112">Remarks</span></span>  
 <span data-ttu-id="abb12-113">如果 integer_expression 大于 character_expression 的长度，则该函数将返回 character_expression    。</span><span class="sxs-lookup"><span data-stu-id="abb12-113">If *integer_expression* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="abb12-114">如果 integer_expression 为 0，则该函数返回零长度的字符串  。</span><span class="sxs-lookup"><span data-stu-id="abb12-114">If *integer_expression* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="abb12-115">如果 integer_expression 为负数，则该函数返回一个错误  。</span><span class="sxs-lookup"><span data-stu-id="abb12-115">If *integer_expression* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="abb12-116">integer_expression 参数可使用变量和列  。</span><span class="sxs-lookup"><span data-stu-id="abb12-116">The *integer_expression* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="abb12-117">RIGHT 只能用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="abb12-117">RIGHT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="abb12-118">如果 character_expression  参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 RIGHT 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="abb12-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RIGHT performs its operation.</span></span> <span data-ttu-id="abb12-119">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="abb12-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="abb12-120">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="abb12-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="abb12-121">如果任一参数为 Null，则 RIGHT 返回的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="abb12-121">RIGHT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="abb12-122">表达式示例</span><span class="sxs-lookup"><span data-stu-id="abb12-122">Expression Examples</span></span>  
 <span data-ttu-id="abb12-123">以下示例使用字符串文字。</span><span class="sxs-lookup"><span data-stu-id="abb12-123">The following example uses a string literal.</span></span> <span data-ttu-id="abb12-124">返回结果为 `"Bike"`。</span><span class="sxs-lookup"><span data-stu-id="abb12-124">The return result is `"Bike"`.</span></span>  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 <span data-ttu-id="abb12-125">以下示例从 `Times` 列返回在 `Name` 变量中指定的最右边字符数。</span><span class="sxs-lookup"><span data-stu-id="abb12-125">The following example returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="abb12-126">如果 `Name` 为 `Touring Front Wheel` 且 `Times` 为 5，则返回结果为 `"Wheel"`。</span><span class="sxs-lookup"><span data-stu-id="abb12-126">If `Name` is `Touring Front Wheel` and `Times` is 5, the return result is `"Wheel"`.</span></span>  
  
```  
RIGHT(Name, @Times)  
```  
  
 <span data-ttu-id="abb12-127">以下示例也从 `Times` 列中返回在 `Name` 变量中指定的最右边字符数。</span><span class="sxs-lookup"><span data-stu-id="abb12-127">The following example also returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column.</span></span> <span data-ttu-id="abb12-128">`Times` 有非整数数据类型，而表达式包含到 DT_I2 数据类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="abb12-128">`Times` has a noninteger data type and the expression includes an explicit cast to the DT_I2 data type.</span></span> <span data-ttu-id="abb12-129">如果 `Name` 为 `Touring Front Wheel` ，并且 `Times` 为 `4.32`，返回结果将是 `"heel"` ，因为 RIGHT 函数将值 4.32 转换为 4，然后返回最右边的四个字符。</span><span class="sxs-lookup"><span data-stu-id="abb12-129">If `Name` is `Touring Front Wheel` and `Times` is `4.32`, the return result is `"heel"` because the RIGHT function converts the value of 4.32 to 4, and then returns the rightmost four characters.</span></span>  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="abb12-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abb12-130">See Also</span></span>  
 <span data-ttu-id="abb12-131">[LEFT（SSIS 表达式）](left-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="abb12-131">[LEFT &#40;SSIS Expression&#41;](left-ssis-expression.md) </span></span>  
 [<span data-ttu-id="abb12-132">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="abb12-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
