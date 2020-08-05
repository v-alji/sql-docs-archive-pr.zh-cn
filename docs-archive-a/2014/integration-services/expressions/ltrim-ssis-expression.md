---
title: LTRIM（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 678d9d93eb1dcd7649d2085b651a08418bbcd6a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581392"
---
# <a name="ltrim-ssis-expression"></a><span data-ttu-id="fe4b9-102">LTRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fe4b9-102">LTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="fe4b9-103">返回删除了前导空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-103">Returns a character expression after removing leading spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe4b9-104">LTRIM 不删除空格字符，如制表符或换行符。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-104">LTRIM does not remove white-space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="fe4b9-105">Unicode 针对许多不同类型的空格提供了码位，但是该函数仅识别 Unicode 码位 0x0020。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="fe4b9-106">双字节字符集 (DBCS) 字符串转换为 Unicode 时，它们可能包含 0x0020 之外的空格字符，而该函数无法删除此类空格。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="fe4b9-107">若要删除所有类型的空格，可以在从脚本组件运行的脚本中使用 Microsoft Visual Basic .NET LTrim 方法。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET LTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4b9-108">语法</span><span class="sxs-lookup"><span data-stu-id="fe4b9-108">Syntax</span></span>  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe4b9-109">参数</span><span class="sxs-lookup"><span data-stu-id="fe4b9-109">Arguments</span></span>  
 <span data-ttu-id="fe4b9-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="fe4b9-110">*character_expression*</span></span>  
 <span data-ttu-id="fe4b9-111">要从中删除空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fe4b9-112">结果类型</span><span class="sxs-lookup"><span data-stu-id="fe4b9-112">Result Types</span></span>  
 <span data-ttu-id="fe4b9-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="fe4b9-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe4b9-114">备注</span><span class="sxs-lookup"><span data-stu-id="fe4b9-114">Remarks</span></span>  
 <span data-ttu-id="fe4b9-115">LTRIM 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-115">LTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="fe4b9-116">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 LTRIM 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LTRIM performs its operation.</span></span> <span data-ttu-id="fe4b9-117">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="fe4b9-118">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="fe4b9-119">如果参数为空，LTRIM 将返回空结果。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-119">LTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="fe4b9-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="fe4b9-120">Expression Examples</span></span>  
 <span data-ttu-id="fe4b9-121">以下示例将删除字符串文字中的前导空格。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-121">This example removes leading spaces from a string literal.</span></span> <span data-ttu-id="fe4b9-122">返回结果为“Hello”。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-122">The return result is "Hello".</span></span>  
  
```  
LTRIM("    Hello")  
```  
  
 <span data-ttu-id="fe4b9-123">以下示例将删除 **FirstName** 列中的前导空格。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-123">This example removes leading spaces from the **FirstName** column.</span></span>  
  
```  
LTRIM(FirstName)  
```  
  
 <span data-ttu-id="fe4b9-124">以下示例将删除 **FirstName** 变量中的前导空格。</span><span class="sxs-lookup"><span data-stu-id="fe4b9-124">This example removes leading spaces from the **FirstName** variable.</span></span>  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe4b9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe4b9-125">See Also</span></span>  
 <span data-ttu-id="fe4b9-126">[RTRIM（SSIS 表达式）](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fe4b9-126">[RTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="fe4b9-127">[TRIM（SSIS 表达式）](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fe4b9-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="fe4b9-128">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="fe4b9-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
