---
title: LOG（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0de84c1a92f94507bcc69c47cc4d9b6cda50a4f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588658"
---
# <a name="log-ssis-expression"></a><span data-ttu-id="bcd12-102">LOG（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="bcd12-102">LOG (SSIS Expression)</span></span>
  <span data-ttu-id="bcd12-103">返回数值表达式以 10 为底的对数。</span><span class="sxs-lookup"><span data-stu-id="bcd12-103">Returns the base-10 logarithm of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd12-104">语法</span><span class="sxs-lookup"><span data-stu-id="bcd12-104">Syntax</span></span>  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="bcd12-105">参数</span><span class="sxs-lookup"><span data-stu-id="bcd12-105">Arguments</span></span>  
 <span data-ttu-id="bcd12-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="bcd12-106">*numeric_expression*</span></span>  
 <span data-ttu-id="bcd12-107">非零或非负数值的有效表达式。</span><span class="sxs-lookup"><span data-stu-id="bcd12-107">Is a valid nonzero or nonnegative numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="bcd12-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="bcd12-108">Result Types</span></span>  
 <span data-ttu-id="bcd12-109">DT_R8</span><span class="sxs-lookup"><span data-stu-id="bcd12-109">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcd12-110">备注</span><span class="sxs-lookup"><span data-stu-id="bcd12-110">Remarks</span></span>  
 <span data-ttu-id="bcd12-111">计算对数前， *数值表达式* 被转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="bcd12-111">The *numeric expression* is cast to the DT_R8 data type before the logarithm is computed.</span></span> <span data-ttu-id="bcd12-112">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="bcd12-112">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="bcd12-113">如果 *numeric_expression* 的计算结果为 0 或负值，则返回结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="bcd12-113">If *numeric_expression* evaluates to zero or a negative value, the return result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="bcd12-114">表达式示例</span><span class="sxs-lookup"><span data-stu-id="bcd12-114">Expression Examples</span></span>  
 <span data-ttu-id="bcd12-115">以下示例使用了一个数值。</span><span class="sxs-lookup"><span data-stu-id="bcd12-115">This example uses a numeric literal.</span></span> <span data-ttu-id="bcd12-116">该函数将返回值 1.988291341907488。</span><span class="sxs-lookup"><span data-stu-id="bcd12-116">The function returns the value 1.988291341907488.</span></span>  
  
```  
LOG(97.34)  
```  
  
 <span data-ttu-id="bcd12-117">此示例使用列 **Length**。</span><span class="sxs-lookup"><span data-stu-id="bcd12-117">This example uses the column **Length**.</span></span> <span data-ttu-id="bcd12-118">如果列为 101.24，则函数返回 2.005352136486217。</span><span class="sxs-lookup"><span data-stu-id="bcd12-118">If the column is 101.24, the function returns 2.005352136486217.</span></span>  
  
```  
LOG(Length)   
```  
  
 <span data-ttu-id="bcd12-119">此示例使用变量 **Length**。</span><span class="sxs-lookup"><span data-stu-id="bcd12-119">This example uses the variable **Length**.</span></span> <span data-ttu-id="bcd12-120">变量必须为数值数据类型，或者表达式必须包含到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数值数据类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="bcd12-120">The variable must have a numeric data type or the expression must include an explicit cast to a numeric [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type.</span></span> <span data-ttu-id="bcd12-121">如果 **Length** 为 234.567，则函数将返回 2.370266913465859。</span><span class="sxs-lookup"><span data-stu-id="bcd12-121">If **Length** is 234.567, the function returns 2.370266913465859.</span></span>  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a><span data-ttu-id="bcd12-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcd12-122">See Also</span></span>  
 <span data-ttu-id="bcd12-123">[EXP（SSIS 表达式）](exp-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="bcd12-123">[EXP &#40;SSIS Expression&#41;](exp-ssis-expression.md) </span></span>  
 <span data-ttu-id="bcd12-124">[LN（SSIS 表达式）](ln-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="bcd12-124">[LN &#40;SSIS Expression&#41;](ln-ssis-expression.md) </span></span>  
 [<span data-ttu-id="bcd12-125">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="bcd12-125">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
