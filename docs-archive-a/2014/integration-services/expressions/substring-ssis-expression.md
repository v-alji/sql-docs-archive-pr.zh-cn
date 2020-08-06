---
title: SUBSTRING（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba53676bc6d13ed34892f48fca3b70372cb30604
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689963"
---
# <a name="substring-ssis-expression"></a><span data-ttu-id="06bc1-102">SUBSTRING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="06bc1-102">SUBSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="06bc1-103">返回字符表达式的一部分，该部分从指定位置开始并具有指定长度。</span><span class="sxs-lookup"><span data-stu-id="06bc1-103">Returns the part of a character expression that starts at the specified position and has the specified length.</span></span> <span data-ttu-id="06bc1-104">*position* 参数和 *length* 参数的取值必须为整数。</span><span class="sxs-lookup"><span data-stu-id="06bc1-104">The *position* parameter and the *length* parameter must evaluate to integers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bc1-105">语法</span><span class="sxs-lookup"><span data-stu-id="06bc1-105">Syntax</span></span>  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="06bc1-106">参数</span><span class="sxs-lookup"><span data-stu-id="06bc1-106">Arguments</span></span>  
 <span data-ttu-id="06bc1-107">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="06bc1-107">*character_expression*</span></span>  
 <span data-ttu-id="06bc1-108">是从中提取字符的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="06bc1-108">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="06bc1-109">*position*</span><span class="sxs-lookup"><span data-stu-id="06bc1-109">*position*</span></span>  
 <span data-ttu-id="06bc1-110">是一个指定子字符串开始位置的整数。</span><span class="sxs-lookup"><span data-stu-id="06bc1-110">Is an integer that specifies where the substring begins.</span></span>  
  
 <span data-ttu-id="06bc1-111">*length*</span><span class="sxs-lookup"><span data-stu-id="06bc1-111">*length*</span></span>  
 <span data-ttu-id="06bc1-112">是一个用字符个数指定子字符串长度的整数。</span><span class="sxs-lookup"><span data-stu-id="06bc1-112">Is an integer that specifies the length of the substring as number of characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="06bc1-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="06bc1-113">Result Types</span></span>  
 <span data-ttu-id="06bc1-114">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="06bc1-114">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06bc1-115">备注</span><span class="sxs-lookup"><span data-stu-id="06bc1-115">Remarks</span></span>  
 <span data-ttu-id="06bc1-116">SUBSTRING 使用从 1 开始的索引。</span><span class="sxs-lookup"><span data-stu-id="06bc1-116">SUBSTRING uses a one-based index.</span></span> <span data-ttu-id="06bc1-117">如果 *position* 为 1，则子字符串从 *character_expression*的第一个字符开始。</span><span class="sxs-lookup"><span data-stu-id="06bc1-117">If *position* is 1, the substring begins with the first character in *character_expression*.</span></span>  
  
 <span data-ttu-id="06bc1-118">SUBSTRING 只能处理 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="06bc1-118">SUBSTRING works only with the DT_WSTR data type.</span></span> <span data-ttu-id="06bc1-119">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 SUBSTRING 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="06bc1-119">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before SUBSTRING performs its operation.</span></span> <span data-ttu-id="06bc1-120">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="06bc1-120">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="06bc1-121">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="06bc1-121">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="06bc1-122">如果此参数为空，则 SUBSTRING 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="06bc1-122">SUBSTRING returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="06bc1-123">表达式中的所有参数都可以使用变量和列。</span><span class="sxs-lookup"><span data-stu-id="06bc1-123">All arguments in the expression can use variables and columns.</span></span>  
  
 <span data-ttu-id="06bc1-124">*length* 参数可以超过字符串长度。</span><span class="sxs-lookup"><span data-stu-id="06bc1-124">The *length* argument can exceed the length of the string.</span></span> <span data-ttu-id="06bc1-125">在这种情况下，函数将返回字符串的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="06bc1-125">In that case, the function returns the remainder of the string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="06bc1-126">表达式示例</span><span class="sxs-lookup"><span data-stu-id="06bc1-126">Expression Examples</span></span>  
 <span data-ttu-id="06bc1-127">此示例从字符串文字的第 4 个字符开始返回两个字符。</span><span class="sxs-lookup"><span data-stu-id="06bc1-127">This example returns two characters, beginning with character 4, from a string literal.</span></span> <span data-ttu-id="06bc1-128">返回结果为“ph”。</span><span class="sxs-lookup"><span data-stu-id="06bc1-128">The return result is "ph".</span></span>  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 <span data-ttu-id="06bc1-129">此示例从第四个字符开始返回字符串文字的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="06bc1-129">This example returns the remainder of a string literal, beginning at the fourth character.</span></span> <span data-ttu-id="06bc1-130">返回结果为“phant”。</span><span class="sxs-lookup"><span data-stu-id="06bc1-130">The return result is "phant".</span></span> <span data-ttu-id="06bc1-131">*length* 参数超过字符串长度不是错误。</span><span class="sxs-lookup"><span data-stu-id="06bc1-131">It is not an error for the *length* argument to exceed the length of the string.</span></span>  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 <span data-ttu-id="06bc1-132">此示例返回 **MiddleName** 列的第一个字母。</span><span class="sxs-lookup"><span data-stu-id="06bc1-132">This example returns the first letter from the **MiddleName** column.</span></span>  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 <span data-ttu-id="06bc1-133">此示例使用参数 *position* 和 *length* 中的变量。</span><span class="sxs-lookup"><span data-stu-id="06bc1-133">This example uses variables in the *position* and *length* arguments.</span></span> <span data-ttu-id="06bc1-134">如果 **Start** 为 1 而 **Length** 为 5，则函数返回 **Name** 列的头五个字符。</span><span class="sxs-lookup"><span data-stu-id="06bc1-134">If **Start** is 1 and **Length** is 5, the function returns the first five characters in the **Name** column.</span></span>  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 <span data-ttu-id="06bc1-135">此示例从 **PostalCode** 变量的第六个字符开始返回最后四个字符。</span><span class="sxs-lookup"><span data-stu-id="06bc1-135">This example returns the last four characters from the **PostalCode** variable beginning at the sixth character.</span></span>  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 <span data-ttu-id="06bc1-136">此示例从字符串文字中返回一个零长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="06bc1-136">This example returns a zero-length string from a string literal.</span></span>  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="06bc1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06bc1-137">See Also</span></span>  
 [<span data-ttu-id="06bc1-138">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="06bc1-138">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
