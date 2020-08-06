---
title: SIGN（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a34992b0029cd378274e38ce4e37fcd313d2b788
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689974"
---
# <a name="sign-ssis-expression"></a><span data-ttu-id="49e00-102">SIGN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="49e00-102">SIGN (SSIS Expression)</span></span>
  <span data-ttu-id="49e00-103">返回数值表达式的符号：正号 (+1)、负号 (-1) 或零 (0)。</span><span class="sxs-lookup"><span data-stu-id="49e00-103">Returns the positive (+1), negative (-1), or zero (0) sign of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e00-104">语法</span><span class="sxs-lookup"><span data-stu-id="49e00-104">Syntax</span></span>  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="49e00-105">参数</span><span class="sxs-lookup"><span data-stu-id="49e00-105">Arguments</span></span>  
 <span data-ttu-id="49e00-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="49e00-106">*numeric_expression*</span></span>  
 <span data-ttu-id="49e00-107">是一个有效的有符号数值表达式。</span><span class="sxs-lookup"><span data-stu-id="49e00-107">Is a valid signed numeric expression.</span></span> <span data-ttu-id="49e00-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="49e00-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="49e00-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="49e00-109">Result Types</span></span>  
 <span data-ttu-id="49e00-110">DT_I4</span><span class="sxs-lookup"><span data-stu-id="49e00-110">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49e00-111">备注</span><span class="sxs-lookup"><span data-stu-id="49e00-111">Remarks</span></span>  
 <span data-ttu-id="49e00-112">如果该参数为空，SIGN 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="49e00-112">SIGN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="49e00-113">表达式示例</span><span class="sxs-lookup"><span data-stu-id="49e00-113">Expression Examples</span></span>  
 <span data-ttu-id="49e00-114">此示例返回数值的符号。</span><span class="sxs-lookup"><span data-stu-id="49e00-114">This example returns the sign of a numeric literal.</span></span> <span data-ttu-id="49e00-115">返回结果为 -1。</span><span class="sxs-lookup"><span data-stu-id="49e00-115">The return result is -1.</span></span>  
  
```  
SIGN(-123.45)  
```  
  
 <span data-ttu-id="49e00-116">此示例返回从 **DealerPrice** 列减去 **StandardCost** 列的结果的符号。</span><span class="sxs-lookup"><span data-stu-id="49e00-116">This example returns the sign of the result of subtracting the **StandardCost** column from the **DealerPrice** column.</span></span>  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a><span data-ttu-id="49e00-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49e00-117">See Also</span></span>  
 [<span data-ttu-id="49e00-118">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="49e00-118">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
