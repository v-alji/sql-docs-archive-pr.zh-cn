---
title: TRIM（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 42cef8a816f399e39ac99061f34c394156bde45f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689954"
---
# <a name="trim-ssis-expression"></a><span data-ttu-id="018a4-102">TRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="018a4-102">TRIM (SSIS Expression)</span></span>
  <span data-ttu-id="018a4-103">返回删除了前导空格和尾随空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="018a4-103">Returns a character expression after removing leading and trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="018a4-104">TRIM 不删除空格字符，如制表符或换行符字符。</span><span class="sxs-lookup"><span data-stu-id="018a4-104">TRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="018a4-105">Unicode 针对许多不同类型的空格提供了码位，但是该函数仅识别 Unicode 码位 0x0020。</span><span class="sxs-lookup"><span data-stu-id="018a4-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="018a4-106">双字节字符集 (DBCS) 字符串转换为 Unicode 时，它们可能包含 0x0020 之外的空格字符，而该函数无法删除此类空格。</span><span class="sxs-lookup"><span data-stu-id="018a4-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="018a4-107">若要删除所有类型的空格，您可以在基于脚本组件运行的脚本中使用 Microsoft Visual Basic .NET Trim 方法。</span><span class="sxs-lookup"><span data-stu-id="018a4-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET Trim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="018a4-108">语法</span><span class="sxs-lookup"><span data-stu-id="018a4-108">Syntax</span></span>  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="018a4-109">参数</span><span class="sxs-lookup"><span data-stu-id="018a4-109">Arguments</span></span>  
 <span data-ttu-id="018a4-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="018a4-110">*character_expression*</span></span>  
 <span data-ttu-id="018a4-111">要从中删除空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="018a4-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="018a4-112">结果类型</span><span class="sxs-lookup"><span data-stu-id="018a4-112">Result Types</span></span>  
 <span data-ttu-id="018a4-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="018a4-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="018a4-114">备注</span><span class="sxs-lookup"><span data-stu-id="018a4-114">Remarks</span></span>  
 <span data-ttu-id="018a4-115">如果该参数为空，则 TRIM 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="018a4-115">TRIM returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="018a4-116">TRIM 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="018a4-116">TRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="018a4-117">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 TRIM 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="018a4-117">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before TRIM performs its operation.</span></span> <span data-ttu-id="018a4-118">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="018a4-118">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="018a4-119">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="018a4-119">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="018a4-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="018a4-120">Expression Examples</span></span>  
 <span data-ttu-id="018a4-121">此示例删除字符串文字中的前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="018a4-121">This example removes leading and trailing spaces from a string literal.</span></span> <span data-ttu-id="018a4-122">返回结果为“New York”。</span><span class="sxs-lookup"><span data-stu-id="018a4-122">The return result is "New York".</span></span>  
  
```  
TRIM("   New York   ")  
```  
  
 <span data-ttu-id="018a4-123">此示例删除 **FirstName** 和 **LastName** 列的串联结果中的前导空格和尾随空格。</span><span class="sxs-lookup"><span data-stu-id="018a4-123">This example removes leading and trailing spaces from the result of concatenating the **FirstName** and **LastName** columns.</span></span> <span data-ttu-id="018a4-124">**FirstName** 和 **LastName** 之间的空字符串不会被删除。</span><span class="sxs-lookup"><span data-stu-id="018a4-124">The empty string between **FirstName** and **LastName** is not removed.</span></span>  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="018a4-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="018a4-125">See Also</span></span>  
 <span data-ttu-id="018a4-126">[LTRIM（SSIS 表达式）](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="018a4-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="018a4-127">[RTRIM（SSIS 表达式）](rtrim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="018a4-127">[RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="018a4-128">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="018a4-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
