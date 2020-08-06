---
title: CEILING（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591487"
---
# <a name="ceiling-ssis-expression"></a><span data-ttu-id="7ec05-102">CEILING（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7ec05-102">CEILING (SSIS Expression)</span></span>
  <span data-ttu-id="7ec05-103">返回大于或等于数值表达式的最小整数。</span><span class="sxs-lookup"><span data-stu-id="7ec05-103">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec05-104">语法</span><span class="sxs-lookup"><span data-stu-id="7ec05-104">Syntax</span></span>  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ec05-105">参数</span><span class="sxs-lookup"><span data-stu-id="7ec05-105">Arguments</span></span>  
 <span data-ttu-id="7ec05-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="7ec05-106">*numeric_expression*</span></span>  
 <span data-ttu-id="7ec05-107">有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="7ec05-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7ec05-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="7ec05-108">Result Types</span></span>  
 <span data-ttu-id="7ec05-109">提交给函数的数值表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="7ec05-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ec05-110">备注</span><span class="sxs-lookup"><span data-stu-id="7ec05-110">Remarks</span></span>  
 <span data-ttu-id="7ec05-111">如果参数为空，则 CEILING 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="7ec05-111">CEILING returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="7ec05-112">表达式示例</span><span class="sxs-lookup"><span data-stu-id="7ec05-112">Expression Examples</span></span>  
 <span data-ttu-id="7ec05-113">这些示例对正值、负值和零值应用 CEILING 函数。</span><span class="sxs-lookup"><span data-stu-id="7ec05-113">These examples apply the CEILING function to positive, negative, and zero values.</span></span>  
  
```  
CEILING(123.74)  
```  
  
 <span data-ttu-id="7ec05-114">返回 124.00</span><span class="sxs-lookup"><span data-stu-id="7ec05-114">Returns 124.00</span></span>  
  
```  
CEILING(-124.27)  
```  
  
 <span data-ttu-id="7ec05-115">返回 -124.00</span><span class="sxs-lookup"><span data-stu-id="7ec05-115">Returns -124.00</span></span>  
  
```  
CEILING(0.00)  
```  
  
 <span data-ttu-id="7ec05-116">返回 0.00</span><span class="sxs-lookup"><span data-stu-id="7ec05-116">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec05-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ec05-117">See Also</span></span>  
 <span data-ttu-id="7ec05-118">[FLOOR（SSIS 表达式）](floor-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="7ec05-118">[FLOOR &#40;SSIS Expression&#41;](floor-ssis-expression.md) </span></span>  
 [<span data-ttu-id="7ec05-119">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="7ec05-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
