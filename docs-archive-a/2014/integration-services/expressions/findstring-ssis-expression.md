---
title: FINDSTRING（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72f2ff21cb179ce565e60c6550b8ecc2618a5adb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581396"
---
# <a name="findstring-ssis-expression"></a><span data-ttu-id="7b3df-102">FINDSTRING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7b3df-102">FINDSTRING (SSIS Expression)</span></span>
  <span data-ttu-id="7b3df-103">返回一个字符串的指定出现在字符表达式中的位置。</span><span class="sxs-lookup"><span data-stu-id="7b3df-103">Returns the location of the specified occurrence of a string within a character expression.</span></span> <span data-ttu-id="7b3df-104">返回结果是该出现的索引（索引从 1 开始）。</span><span class="sxs-lookup"><span data-stu-id="7b3df-104">The return result is the one-based index of the occurrence.</span></span> <span data-ttu-id="7b3df-105">字符串参数的取值必须为字符表达式，而 occurrence 参数的取值必须为整数。</span><span class="sxs-lookup"><span data-stu-id="7b3df-105">The string parameter must evaluate to a character expression, and the occurrence parameter must evaluate to an integer.</span></span> <span data-ttu-id="7b3df-106">如果找不到字符串，则返回值是 0。</span><span class="sxs-lookup"><span data-stu-id="7b3df-106">If the string is not found, the return value is 0.</span></span> <span data-ttu-id="7b3df-107">如果字符串的出现次数少于所指定的 occurrence 参数，则返回值为 0。</span><span class="sxs-lookup"><span data-stu-id="7b3df-107">If the string occurs fewer times than the occurrence argument specifies, the return value is 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3df-108">语法</span><span class="sxs-lookup"><span data-stu-id="7b3df-108">Syntax</span></span>  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b3df-109">参数</span><span class="sxs-lookup"><span data-stu-id="7b3df-109">Arguments</span></span>  
 <span data-ttu-id="7b3df-110">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="7b3df-110">*character_expression*</span></span>  
 <span data-ttu-id="7b3df-111">是要在其中进行搜索的字符串。</span><span class="sxs-lookup"><span data-stu-id="7b3df-111">Is the character string to search in.</span></span>  
  
 <span data-ttu-id="7b3df-112">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="7b3df-112">*searchstring*</span></span>  
 <span data-ttu-id="7b3df-113">是要搜索的字符串。</span><span class="sxs-lookup"><span data-stu-id="7b3df-113">Is the character string to search for.</span></span>  
  
 <span data-ttu-id="7b3df-114">*occurrence*</span><span class="sxs-lookup"><span data-stu-id="7b3df-114">*occurrence*</span></span>  
 <span data-ttu-id="7b3df-115">有符号或无符号的整数，用以指定要报告的 *searchstring* 的匹配项。</span><span class="sxs-lookup"><span data-stu-id="7b3df-115">Is a signed or unsigned integer specifying which occurrence of *searchstring* to report.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7b3df-116">结果类型</span><span class="sxs-lookup"><span data-stu-id="7b3df-116">Result Types</span></span>  
 <span data-ttu-id="7b3df-117">DT_I4</span><span class="sxs-lookup"><span data-stu-id="7b3df-117">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b3df-118">备注</span><span class="sxs-lookup"><span data-stu-id="7b3df-118">Remarks</span></span>  
 <span data-ttu-id="7b3df-119">FINDSTRING 只能处理 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="7b3df-119">FINDSTRING works only with the DT_WSTR data type.</span></span>  <span data-ttu-id="7b3df-120">如果*character_expression* 和 *searchstring* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它们在 FINDSTRING 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="7b3df-120">*character_expression* and *searchstring* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before FINDSTRING performs its operation.</span></span> <span data-ttu-id="7b3df-121">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="7b3df-121">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="7b3df-122">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="7b3df-122">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="7b3df-123">如果 *character_expression* 或 *searchstring* 为 null，则 FINDSTRING 返回 null。</span><span class="sxs-lookup"><span data-stu-id="7b3df-123">FINDSTRING returns null if either *character_expression* or *searchstring* are null.</span></span>  
  
 <span data-ttu-id="7b3df-124">在 *occurrence* 参数中使用值 1 将获得第一次出现的索引，使用 2 将获得第二次出现的索引，依此类推。</span><span class="sxs-lookup"><span data-stu-id="7b3df-124">Use a value of 1 in the *occurrence* argument to get the index of the first occurrence, 2 for the second occurrence and so forth.</span></span>  
  
 <span data-ttu-id="7b3df-125">*occurrence* 必须为值大于 0 的整数。</span><span class="sxs-lookup"><span data-stu-id="7b3df-125">The *occurrence* must be an integer with a value greater than 0.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7b3df-126">表达式示例</span><span class="sxs-lookup"><span data-stu-id="7b3df-126">Expression Examples</span></span>  
 <span data-ttu-id="7b3df-127">此示例使用一个字符串文字。</span><span class="sxs-lookup"><span data-stu-id="7b3df-127">This example uses a string literal.</span></span> <span data-ttu-id="7b3df-128">它返回值 11。</span><span class="sxs-lookup"><span data-stu-id="7b3df-128">It returns the value 11.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 <span data-ttu-id="7b3df-129">此示例使用一个字符串文字。</span><span class="sxs-lookup"><span data-stu-id="7b3df-129">This example uses a string literal.</span></span> <span data-ttu-id="7b3df-130">由于字符串“NY”只出现两次，所以返回结果是 0。</span><span class="sxs-lookup"><span data-stu-id="7b3df-130">Because the string "NY" occurs only two times, the return result is 0.</span></span>  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 <span data-ttu-id="7b3df-131">此示例使用 **Name** 列。</span><span class="sxs-lookup"><span data-stu-id="7b3df-131">This example uses the **Name** column.</span></span> <span data-ttu-id="7b3df-132">它返回 **Name** 列中值 n 的位置。</span><span class="sxs-lookup"><span data-stu-id="7b3df-132">It returns the location of the value n in the **Name** column.</span></span> <span data-ttu-id="7b3df-133">返回结果因 **Name**中值的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="7b3df-133">The return result varies depending on the value in **Name**.</span></span> <span data-ttu-id="7b3df-134">如果 **Name** 包含 Anderson，则函数返回 8。</span><span class="sxs-lookup"><span data-stu-id="7b3df-134">If **Name** contains Anderson, the function returns 8.</span></span>  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 <span data-ttu-id="7b3df-135">此示例使用 **Name** 和 **Size** 列。</span><span class="sxs-lookup"><span data-stu-id="7b3df-135">This example uses the **Name** and **Size** columns.</span></span> <span data-ttu-id="7b3df-136">它返回 **Name** 列中 **Size** 值的最左侧字符的位置。</span><span class="sxs-lookup"><span data-stu-id="7b3df-136">It returns the location of the leftmost character of the **Size** value in the **Name** column.</span></span> <span data-ttu-id="7b3df-137">返回结果因列值的不同而不同。</span><span class="sxs-lookup"><span data-stu-id="7b3df-137">The return result varies depending on column values.</span></span> <span data-ttu-id="7b3df-138">如果 **Name** 包含 Mountain,500Red,42，且 **Size** 包含 42，则返回结果为 17。</span><span class="sxs-lookup"><span data-stu-id="7b3df-138">If **Name** contains Mountain,500Red,42 and **Size** contains 42, the return result is 17.</span></span>  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a><span data-ttu-id="7b3df-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7b3df-139">See Also</span></span>  
 <span data-ttu-id="7b3df-140">[REPLACE（SSIS 表达式）](replace-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7b3df-140">[REPLACE &#40;SSIS Expression&#41;](replace-ssis-expression.md) </span></span>  
 [<span data-ttu-id="7b3df-141">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7b3df-141">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
