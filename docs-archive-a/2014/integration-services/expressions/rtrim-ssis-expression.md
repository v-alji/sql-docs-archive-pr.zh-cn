---
title: RTRIM（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 727c30fd72bfca5676b71f4ba42e936a9b926817
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689976"
---
# <a name="rtrim-ssis-expression"></a><span data-ttu-id="e34ed-102">RTRIM（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="e34ed-102">RTRIM (SSIS Expression)</span></span>
  <span data-ttu-id="e34ed-103">返回删除了尾随空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="e34ed-103">Returns a character expression after removing trailing spaces.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e34ed-104">RTRIM 不删除空格字符，如制表符或换行符字符。</span><span class="sxs-lookup"><span data-stu-id="e34ed-104">RTRIM does not remove white space characters such as the tab or line feed characters.</span></span> <span data-ttu-id="e34ed-105">Unicode 针对许多不同类型的空格提供了码位，但是该函数仅识别 Unicode 码位 0x0020。</span><span class="sxs-lookup"><span data-stu-id="e34ed-105">Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020.</span></span> <span data-ttu-id="e34ed-106">双字节字符集 (DBCS) 字符串转换为 Unicode 时，它们可能包含 0x0020 之外的空格字符，而该函数无法删除此类空格。</span><span class="sxs-lookup"><span data-stu-id="e34ed-106">When double-byte character set (DBCS) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces.</span></span> <span data-ttu-id="e34ed-107">若要删除所有类型的空格，您可以在基于脚本组件运行的脚本中使用 Microsoft Visual Basic .NET RTrim 方法。</span><span class="sxs-lookup"><span data-stu-id="e34ed-107">To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET RTrim method in a script run from the Script component.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34ed-108">语法</span><span class="sxs-lookup"><span data-stu-id="e34ed-108">Syntax</span></span>  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e34ed-109">参数</span><span class="sxs-lookup"><span data-stu-id="e34ed-109">Arguments</span></span>  
 <span data-ttu-id="e34ed-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="e34ed-110">*character_expression*</span></span>  
 <span data-ttu-id="e34ed-111">要从中删除空格的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="e34ed-111">Is a character expression from which to remove spaces.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e34ed-112">结果类型</span><span class="sxs-lookup"><span data-stu-id="e34ed-112">Result Types</span></span>  
 <span data-ttu-id="e34ed-113">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="e34ed-113">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e34ed-114">备注</span><span class="sxs-lookup"><span data-stu-id="e34ed-114">Remarks</span></span>  
 <span data-ttu-id="e34ed-115">RTRIM 只用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e34ed-115">RTRIM works only with the DT_WSTR data type.</span></span> <span data-ttu-id="e34ed-116">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 RTRIM 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e34ed-116">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before RTRIM performs its operation.</span></span> <span data-ttu-id="e34ed-117">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="e34ed-117">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="e34ed-118">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="e34ed-118">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="e34ed-119">如果该参数为空，则 RTRIM 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="e34ed-119">RTRIM returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e34ed-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="e34ed-120">Expression Examples</span></span>  
 <span data-ttu-id="e34ed-121">此示例删除字符串文字中的尾随空格。</span><span class="sxs-lookup"><span data-stu-id="e34ed-121">This example removes trailing spaces from a string literal.</span></span> <span data-ttu-id="e34ed-122">返回结果为“Hello”。</span><span class="sxs-lookup"><span data-stu-id="e34ed-122">The return result is "Hello".</span></span>  
  
```  
RTRIM("Hello   ")  
```  
  
 <span data-ttu-id="e34ed-123">此示例删除 **FirstName** 和 **LastName** 列的串联中的尾随空格。</span><span class="sxs-lookup"><span data-stu-id="e34ed-123">This example removes trailing spaces from a concatenation of the **FirstName** and **LastName** columns.</span></span>  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 <span data-ttu-id="e34ed-124">此示例删除 **FirstName** 变量中的尾随空格。</span><span class="sxs-lookup"><span data-stu-id="e34ed-124">This example removes trailing spaces from the **FirstName** variable.</span></span>  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e34ed-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e34ed-125">See Also</span></span>  
 <span data-ttu-id="e34ed-126">[LTRIM（SSIS 表达式）](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e34ed-126">[LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 <span data-ttu-id="e34ed-127">[TRIM（SSIS 表达式）](trim-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e34ed-127">[TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md) </span></span>  
 [<span data-ttu-id="e34ed-128">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="e34ed-128">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
