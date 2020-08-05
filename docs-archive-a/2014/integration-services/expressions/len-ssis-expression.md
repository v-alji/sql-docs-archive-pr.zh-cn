---
title: LEN（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8863864168295a3a9a924df588312ee65b6f7fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580791"
---
# <a name="len-ssis-expression"></a><span data-ttu-id="0790c-102">LEN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0790c-102">LEN (SSIS Expression)</span></span>
  <span data-ttu-id="0790c-103">返回字符表达式中的字符数。</span><span class="sxs-lookup"><span data-stu-id="0790c-103">Returns the number of characters in a character expression.</span></span> <span data-ttu-id="0790c-104">如果字符串中包含前导空格和尾随空格，则函数会将它们包含在计数内。</span><span class="sxs-lookup"><span data-stu-id="0790c-104">If the string includes leading and trailing blanks, the function includes them in the count.</span></span> <span data-ttu-id="0790c-105">LEN 对相同的单字节和双字节字符串返回相同的值。</span><span class="sxs-lookup"><span data-stu-id="0790c-105">LEN returns identical values for the same string of single and double byte characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0790c-106">语法</span><span class="sxs-lookup"><span data-stu-id="0790c-106">Syntax</span></span>  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="0790c-107">参数</span><span class="sxs-lookup"><span data-stu-id="0790c-107">Arguments</span></span>  
 <span data-ttu-id="0790c-108">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="0790c-108">*character_expression*</span></span>  
 <span data-ttu-id="0790c-109">要处理的表达式。</span><span class="sxs-lookup"><span data-stu-id="0790c-109">Is the expression to evaluate.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0790c-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="0790c-110">Result Types</span></span>  
 <span data-ttu-id="0790c-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="0790c-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0790c-112">备注</span><span class="sxs-lookup"><span data-stu-id="0790c-112">Remarks</span></span>  
 <span data-ttu-id="0790c-113">*character_expression* 参数可以是 DT_WSTR、DT_TEXT、DT_NTEXT 或 DT_IMAGE 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0790c-113">The *character_expression* argument can be a DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="0790c-114">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0790c-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="0790c-115">如果 *character_expression* 是字符串文字或包含 DT_STR 数据类型的数据列，则在执行 LEN 操作前，该参数将隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0790c-115">If *character_expression* is a string literal or a data column with the DT_STR data type, it is implicitly cast to the DT_WSTR data type before LEN performs its operation.</span></span> <span data-ttu-id="0790c-116">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0790c-116">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="0790c-117">有关详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="0790c-117">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="0790c-118">如果传递给 LEN 函数的参数包含二进制大型对象块 (BLOB) 数据类型，如 DT_TEXT、DT_NTEXT 或 DT_IMAGE，则该函数将返回字节计数。</span><span class="sxs-lookup"><span data-stu-id="0790c-118">If the argument passed to the LEN function has a Binary Large Object Block (BLOB) data type, such as DT_TEXT, DT_NTEXT, or DT_IMAGE, the function returns a byte count.</span></span>  
  
 <span data-ttu-id="0790c-119">如果参数为 Null，LEN 将返回 Null 结果。</span><span class="sxs-lookup"><span data-stu-id="0790c-119">LEN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="0790c-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="0790c-120">Expression Examples</span></span>  
 <span data-ttu-id="0790c-121">以下示例将返回字符串文字的长度。</span><span class="sxs-lookup"><span data-stu-id="0790c-121">This example returns the length of a string literal.</span></span> <span data-ttu-id="0790c-122">返回结果为 12。</span><span class="sxs-lookup"><span data-stu-id="0790c-122">The return result is 12.</span></span>  
  
```  
LEN("Ball Bearing")  
```  
  
 <span data-ttu-id="0790c-123">以下示例将返回 **FirstName** 和 **LastName** 列中的值之间的长度差。</span><span class="sxs-lookup"><span data-stu-id="0790c-123">This example returns the difference between the length of values in the **FirstName** and **LastName** columns.</span></span>  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 <span data-ttu-id="0790c-124">返回使用系统变量 **MachineName**的计算机名称的长度。</span><span class="sxs-lookup"><span data-stu-id="0790c-124">Returns the length of a computer name using the System variable **MachineName**.</span></span>  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="0790c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0790c-125">See Also</span></span>  
 [<span data-ttu-id="0790c-126">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0790c-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
