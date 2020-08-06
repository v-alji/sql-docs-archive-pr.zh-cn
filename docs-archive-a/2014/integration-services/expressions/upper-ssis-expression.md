---
title: UPPER（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181e231d735a8e98cd2bce10c692e35668a686f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689950"
---
# <a name="upper-ssis-expression"></a><span data-ttu-id="25585-102">UPPER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="25585-102">UPPER (SSIS Expression)</span></span>
  <span data-ttu-id="25585-103">返回将小写字符转换为大写字符后得到的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="25585-103">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25585-104">语法</span><span class="sxs-lookup"><span data-stu-id="25585-104">Syntax</span></span>  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="25585-105">参数</span><span class="sxs-lookup"><span data-stu-id="25585-105">Arguments</span></span>  
 <span data-ttu-id="25585-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="25585-106">*character_expression*</span></span>  
 <span data-ttu-id="25585-107">要转换为大写字符的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="25585-107">Is a character expression to convert to uppercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="25585-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="25585-108">Result Types</span></span>  
 <span data-ttu-id="25585-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="25585-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25585-110">备注</span><span class="sxs-lookup"><span data-stu-id="25585-110">Remarks</span></span>  
 <span data-ttu-id="25585-111">UPPER 只能用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="25585-111">UPPER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="25585-112">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 UPPER 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="25585-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before UPPER performs its operation.</span></span> <span data-ttu-id="25585-113">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="25585-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="25585-114">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="25585-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="25585-115">如果参数为空，UPPER 将返回空结果。</span><span class="sxs-lookup"><span data-stu-id="25585-115">UPPER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="25585-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="25585-116">Expression Examples</span></span>  
 <span data-ttu-id="25585-117">以下示例将字符串文字转换为大写字符。</span><span class="sxs-lookup"><span data-stu-id="25585-117">This example converts a string literal to uppercase characters.</span></span> <span data-ttu-id="25585-118">返回结果为“HELLO”。</span><span class="sxs-lookup"><span data-stu-id="25585-118">The return result is "HELLO".</span></span>  
  
```  
UPPER("hello")  
```  
  
 <span data-ttu-id="25585-119">以下示例将 **FirstName** 列中的第一个字符转换为大写字符。</span><span class="sxs-lookup"><span data-stu-id="25585-119">This example converts the first character in the **FirstName** column to an uppercase character.</span></span> <span data-ttu-id="25585-120">如果 **FirstName** 为 anna，则返回结果为“A”。</span><span class="sxs-lookup"><span data-stu-id="25585-120">If **FirstName** is anna, the return result is "A".</span></span> <span data-ttu-id="25585-121">有关详细信息，请参阅 [SUBSTRING（SSIS 表达式）](substring-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="25585-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 <span data-ttu-id="25585-122">以下示例将 **PostalCode** 变量中的值转换为大写字符。</span><span class="sxs-lookup"><span data-stu-id="25585-122">This example converts the value in the **PostalCode** variable to uppercase characters.</span></span> <span data-ttu-id="25585-123">如果 **PostalCode** 为 k4b1s2，则返回结果为“K4B1S2”。</span><span class="sxs-lookup"><span data-stu-id="25585-123">If **PostalCode** is k4b1s2, the return result is "K4B1S2".</span></span>  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a><span data-ttu-id="25585-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25585-124">See Also</span></span>  
 <span data-ttu-id="25585-125">[LOWER（SSIS 表达式）](lower-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="25585-125">[LOWER &#40;SSIS Expression&#41;](lower-ssis-expression.md) </span></span>  
 [<span data-ttu-id="25585-126">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="25585-126">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
