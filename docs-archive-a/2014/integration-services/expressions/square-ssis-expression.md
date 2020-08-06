---
title: SQUARE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09955e708aae707a88aa7821d2a72651a3a44d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689968"
---
# <a name="square-ssis-expression"></a><span data-ttu-id="c44ea-102">SQUARE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c44ea-102">SQUARE (SSIS Expression)</span></span>
  <span data-ttu-id="c44ea-103">返回数值表达式的平方。</span><span class="sxs-lookup"><span data-stu-id="c44ea-103">Returns the square of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c44ea-104">语法</span><span class="sxs-lookup"><span data-stu-id="c44ea-104">Syntax</span></span>  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c44ea-105">参数</span><span class="sxs-lookup"><span data-stu-id="c44ea-105">Arguments</span></span>  
 <span data-ttu-id="c44ea-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="c44ea-106">*numeric_expression*</span></span>  
 <span data-ttu-id="c44ea-107">是任意数值数据类型的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="c44ea-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="c44ea-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c44ea-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c44ea-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="c44ea-109">Result Types</span></span>  
 <span data-ttu-id="c44ea-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="c44ea-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c44ea-111">备注</span><span class="sxs-lookup"><span data-stu-id="c44ea-111">Remarks</span></span>  
 <span data-ttu-id="c44ea-112">如果参数为空，SQUARE 将返回空结果。</span><span class="sxs-lookup"><span data-stu-id="c44ea-112">SQUARE returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="c44ea-113">执行 SQUARE 操作前，参数会转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="c44ea-113">The argument is cast to the DT_R8 data type before the square operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c44ea-114">表达式示例</span><span class="sxs-lookup"><span data-stu-id="c44ea-114">Expression Examples</span></span>  
 <span data-ttu-id="c44ea-115">此示例返回 12 的平方。</span><span class="sxs-lookup"><span data-stu-id="c44ea-115">This example returns the square of 12.</span></span> <span data-ttu-id="c44ea-116">返回结果为 144。</span><span class="sxs-lookup"><span data-stu-id="c44ea-116">The return result is 144.</span></span>  
  
```  
SQUARE(12)  
```  
  
 <span data-ttu-id="c44ea-117">以下示例返回两列值相减所得结果的平方。</span><span class="sxs-lookup"><span data-stu-id="c44ea-117">This example returns the square of the result of subtracting values in two columns.</span></span> <span data-ttu-id="c44ea-118">如果 **Value1** 包含 12， **Value2** 包含 4，则 SQUARE 函数返回 64。</span><span class="sxs-lookup"><span data-stu-id="c44ea-118">If **Value1** contains 12 and **Value2** contains 4, the SQUARE function returns 64.</span></span>  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 <span data-ttu-id="c44ea-119">以下示例通过对两个变量应用 SQUARE 函数，然后计算其结果相加值的平方根，返回直角三角形斜边的长度。</span><span class="sxs-lookup"><span data-stu-id="c44ea-119">This example returns the length of the third side of a right angle triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="c44ea-120">如果 **Side1** 包含3， **Side2** 包含4，则 SQRT 函数返回 5。</span><span class="sxs-lookup"><span data-stu-id="c44ea-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c44ea-121">在表达式中，变量名始终包含前缀 \@。</span><span class="sxs-lookup"><span data-stu-id="c44ea-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44ea-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c44ea-122">See Also</span></span>  
 [<span data-ttu-id="c44ea-123">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c44ea-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
