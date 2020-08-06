---
title: SQRT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9efa3f8da2e5280692aa65a25610211aba2fa40f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689970"
---
# <a name="sqrt-ssis-expression"></a><span data-ttu-id="5ef8e-102">SQRT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5ef8e-102">SQRT (SSIS Expression)</span></span>
  <span data-ttu-id="5ef8e-103">返回数值表达式的平方根。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-103">Returns the square root of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef8e-104">语法</span><span class="sxs-lookup"><span data-stu-id="5ef8e-104">Syntax</span></span>  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ef8e-105">参数</span><span class="sxs-lookup"><span data-stu-id="5ef8e-105">Arguments</span></span>  
 <span data-ttu-id="5ef8e-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="5ef8e-106">*numeric_expression*</span></span>  
 <span data-ttu-id="5ef8e-107">是任意数值数据类型的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-107">Is a numeric expression of any numeric data type.</span></span> <span data-ttu-id="5ef8e-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5ef8e-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="5ef8e-109">Result Types</span></span>  
 <span data-ttu-id="5ef8e-110">DT_R8</span><span class="sxs-lookup"><span data-stu-id="5ef8e-110">DT_R8</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef8e-111">备注</span><span class="sxs-lookup"><span data-stu-id="5ef8e-111">Remarks</span></span>  
 <span data-ttu-id="5ef8e-112">如果参数为空，则 SQRT 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-112">SQRT returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="5ef8e-113">如果参数是负值，则 SQRT 失败。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-113">SQRT fails if the argument is a negative value.</span></span>  
  
 <span data-ttu-id="5ef8e-114">进行平方根操作前，该参数被转换为 DT_R8 数据类型。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-114">The argument is cast to the DT_R8 data type before the square root operation.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5ef8e-115">表达式示例</span><span class="sxs-lookup"><span data-stu-id="5ef8e-115">Expression Examples</span></span>  
 <span data-ttu-id="5ef8e-116">此示例返回数值的平方根。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-116">This example returns the square root of a numeric literal.</span></span> <span data-ttu-id="5ef8e-117">返回结果为 12。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-117">The return result is 12.</span></span>  
  
```  
SQRT(144)  
```  
  
 <span data-ttu-id="5ef8e-118">此示例返回表达式（ **Value1** 列和 **Value2** 列的值相减的结果）的平方根。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-118">This example returns the square root of an expression, the result of subtracting values in the **Value1** and **Value2** columns.</span></span>  
  
```  
SQRT(Value1 - Value2)  
```  
  
 <span data-ttu-id="5ef8e-119">此示例通过对两个变量应用 SQUARE 函数然后计算其和的平方根，返回直角三角形第三边的长度。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-119">This example returns the length of the third side of a right triangle by applying the SQUARE function to two variables and then calculating the square root of their sum.</span></span> <span data-ttu-id="5ef8e-120">如果 **Side1** 包含3， **Side2** 包含4，则 SQRT 函数返回 5。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-120">If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.</span></span>  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  <span data-ttu-id="5ef8e-121">在表达式中，变量名始终包含前缀 \@。</span><span class="sxs-lookup"><span data-stu-id="5ef8e-121">In expressions, variable names always include the \@ prefix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef8e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ef8e-122">See Also</span></span>  
 [<span data-ttu-id="5ef8e-123">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5ef8e-123">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
