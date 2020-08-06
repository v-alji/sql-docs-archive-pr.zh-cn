---
title: CODEPOINT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf05cc0838763ba9e22707af57892133d449da07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577753"
---
# <a name="codepoint-ssis-expression"></a><span data-ttu-id="8dfc2-102">CODEPOINT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8dfc2-102">CODEPOINT (SSIS Expression)</span></span>
  <span data-ttu-id="8dfc2-103">返回字符表达式中最左侧字符的 Unicode 码位。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-103">Returns the Unicode code point of the leftmost character of a character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dfc2-104">语法</span><span class="sxs-lookup"><span data-stu-id="8dfc2-104">Syntax</span></span>  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="8dfc2-105">参数</span><span class="sxs-lookup"><span data-stu-id="8dfc2-105">Arguments</span></span>  
 <span data-ttu-id="8dfc2-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="8dfc2-106">*character_expression*</span></span>  
 <span data-ttu-id="8dfc2-107">要对其最左侧字符进行计算的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-107">Is a character expression whose leftmost character will be evaluated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8dfc2-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="8dfc2-108">Result Types</span></span>  
 <span data-ttu-id="8dfc2-109">DT_UI2</span><span class="sxs-lookup"><span data-stu-id="8dfc2-109">DT_UI2</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dfc2-110">备注</span><span class="sxs-lookup"><span data-stu-id="8dfc2-110">Remarks</span></span>  
 <span data-ttu-id="8dfc2-111">*character_expression* 必须具有 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-111">*character_expression* must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="8dfc2-112">如果 *character_expression* 为 NULL 或为空字符串，则 CODEPOINT 返回的结果为 NULL。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-112">CODEPOINT returns a null result if *character_expression* is null or an empty string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8dfc2-113">表达式示例</span><span class="sxs-lookup"><span data-stu-id="8dfc2-113">Expression Examples</span></span>  
 <span data-ttu-id="8dfc2-114">此示例使用一个字符串文字。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-114">This example uses a string literal.</span></span> <span data-ttu-id="8dfc2-115">返回结果为 M 的 Unicode 码位 77。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-115">The return result is 77, the Unicode code point for M.</span></span>  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 <span data-ttu-id="8dfc2-116">此示例使用一个变量。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-116">This example uses a variable.</span></span> <span data-ttu-id="8dfc2-117">如果 **Name** 为 Touring Front Wheel，则返回结果为 T 的 Unicode 码位 84。</span><span class="sxs-lookup"><span data-stu-id="8dfc2-117">If **Name** is Touring Front Wheel, the return result is 84, the Unicode code point for T.</span></span>  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dfc2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8dfc2-118">See Also</span></span>  
 [<span data-ttu-id="8dfc2-119">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8dfc2-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
