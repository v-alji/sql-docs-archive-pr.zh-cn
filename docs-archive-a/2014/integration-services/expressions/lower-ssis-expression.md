---
title: LOWER（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting uppercase to lowercase
- LOWER function
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 180be8f3cfb5a15eb0fcd6ddd3d63b09fe874af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581394"
---
# <a name="lower-ssis-expression"></a><span data-ttu-id="8d370-102">LOWER（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8d370-102">LOWER (SSIS Expression)</span></span>
  <span data-ttu-id="8d370-103">返回将大写字符转换为小写字符后得到的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="8d370-103">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d370-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d370-104">Syntax</span></span>  
  
```  
  
LOWER(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d370-105">参数</span><span class="sxs-lookup"><span data-stu-id="8d370-105">Arguments</span></span>  
 <span data-ttu-id="8d370-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="8d370-106">*character_expression*</span></span>  
 <span data-ttu-id="8d370-107">是要转换为小写字符的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="8d370-107">Is a character expression to convert to lowercase characters.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8d370-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="8d370-108">Result Types</span></span>  
 <span data-ttu-id="8d370-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="8d370-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d370-110">备注</span><span class="sxs-lookup"><span data-stu-id="8d370-110">Remarks</span></span>  
 <span data-ttu-id="8d370-111">LOWER 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8d370-111">LOWER works only with the DT_WSTR data type.</span></span> <span data-ttu-id="8d370-112">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 LOWER 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8d370-112">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LOWER performs its operation.</span></span> <span data-ttu-id="8d370-113">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8d370-113">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="8d370-114">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="8d370-114">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="8d370-115">如果该参数为空，则 LOWER 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="8d370-115">LOWER returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8d370-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="8d370-116">Expression Examples</span></span>  
 <span data-ttu-id="8d370-117">此示例将字符串文字转换为小写字符。</span><span class="sxs-lookup"><span data-stu-id="8d370-117">This example converts a string literal to lowercase characters.</span></span> <span data-ttu-id="8d370-118">返回结果为“new york”。</span><span class="sxs-lookup"><span data-stu-id="8d370-118">The return result is "new york".</span></span>  
  
```  
LOWER("New York")  
```  
  
 <span data-ttu-id="8d370-119">此示例将 **Color** 输入列中除第一个字符外的所有字符转换为小写字符。</span><span class="sxs-lookup"><span data-stu-id="8d370-119">This example converts all characters from the **Color** input column, except the first character, to lowercase characters.</span></span> <span data-ttu-id="8d370-120">如果 Color 为 YELLOW，则返回结果为“Yellow”。</span><span class="sxs-lookup"><span data-stu-id="8d370-120">If Color is YELLOW, the return result is "Yellow".</span></span> <span data-ttu-id="8d370-121">有关详细信息，请参阅 [SUBSTRING（SSIS 表达式）](substring-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="8d370-121">For more information, see [SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md).</span></span>  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 <span data-ttu-id="8d370-122">此示例将 **CityName** 变量中的值转换为小写字符。</span><span class="sxs-lookup"><span data-stu-id="8d370-122">This example converts the value in the **CityName** variable to lowercase characters.</span></span>  
  
```  
LOWER(@CityName)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d370-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d370-123">See Also</span></span>  
 <span data-ttu-id="8d370-124">[UPPER（SSIS 表达式）](upper-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="8d370-124">[UPPER &#40;SSIS Expression&#41;](upper-ssis-expression.md) </span></span>  
 [<span data-ttu-id="8d370-125">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8d370-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
