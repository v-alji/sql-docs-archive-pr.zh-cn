---
title: LN（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c06d6e246cfa51f8e84eb93ab7eb73eab40c392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588662"
---
# <a name="ln-ssis-expression"></a><span data-ttu-id="0b648-102">LN（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0b648-102">LN (SSIS Expression)</span></span>
  <span data-ttu-id="0b648-103">返回数值表达式的自然对数。</span><span class="sxs-lookup"><span data-stu-id="0b648-103">Returns the natural logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b648-104">语法</span><span class="sxs-lookup"><span data-stu-id="0b648-104">Syntax</span></span>  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b648-105">参数</span><span class="sxs-lookup"><span data-stu-id="0b648-105">Arguments</span></span>  
 <span data-ttu-id="0b648-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="0b648-106">*numeric_expression*</span></span>  
 <span data-ttu-id="0b648-107">是有效的非零和非负数值表达式。</span><span class="sxs-lookup"><span data-stu-id="0b648-107">Is a valid non-zero and non-negative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0b648-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="0b648-108">Result Types</span></span>  
 <span data-ttu-id="0b648-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="0b648-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b648-110">备注</span><span class="sxs-lookup"><span data-stu-id="0b648-110">Remarks</span></span>  
 <span data-ttu-id="0b648-111">计算对数前，数值表达式被转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="0b648-111">The numeric expression is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="0b648-112">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0b648-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="0b648-113">如果 *numeric_expression* 的计算结果为 0 或负值，则返回结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="0b648-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="0b648-114">表达式示例</span><span class="sxs-lookup"><span data-stu-id="0b648-114">Expression Examples</span></span>  
 <span data-ttu-id="0b648-115">以下示例使用了一个数值。</span><span class="sxs-lookup"><span data-stu-id="0b648-115">This example uses a numeric literal.</span></span> <span data-ttu-id="0b648-116">该函数将返回值 3.737766961828337。</span><span class="sxs-lookup"><span data-stu-id="0b648-116">The function returns the value 3.737766961828337.</span></span>  
  
```  
LN(42)  
```  
  
 <span data-ttu-id="0b648-117">此示例使用列 **Length**。</span><span class="sxs-lookup"><span data-stu-id="0b648-117">This example uses the column **Length**.</span></span> <span data-ttu-id="0b648-118">如果列值为 53.99，则该函数返回 3.9887988442302。</span><span class="sxs-lookup"><span data-stu-id="0b648-118">If the column value is 53.99, the function returns 3.9887988442302.</span></span>  
  
```  
LN(Length)   
```  
  
 <span data-ttu-id="0b648-119">此示例使用变量 **Length**。</span><span class="sxs-lookup"><span data-stu-id="0b648-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="0b648-120">变量必须为数值数据类型，否则表达式必须包含到数值数据类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="0b648-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric data type.</span></span> <span data-ttu-id="0b648-121">如果 **Length** 为 234.567，则函数将返回 5.45774126708797。</span><span class="sxs-lookup"><span data-stu-id="0b648-121">If **Length** is 234.567, the function returns 5.45774126708797.</span></span>  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="0b648-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b648-122">See Also</span></span>  
 <span data-ttu-id="0b648-123">[LOG（SSIS 表达式）](log-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0b648-123">[LOG &#40;SSIS Expression&#41;](log-ssis-expression.md) </span></span>  
 [<span data-ttu-id="0b648-124">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0b648-124">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
