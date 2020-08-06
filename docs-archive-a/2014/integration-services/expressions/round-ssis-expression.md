---
title: ROUND（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d77045787eafbc3dd402db9982d8d7a98190bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689977"
---
# <a name="round-ssis-expression"></a><span data-ttu-id="daf87-102">ROUND（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="daf87-102">ROUND (SSIS Expression)</span></span>
  <span data-ttu-id="daf87-103">返回舍入到指定长度或精度的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="daf87-103">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="daf87-104">length 参数的取值必须为整数。</span><span class="sxs-lookup"><span data-stu-id="daf87-104">The length parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf87-105">语法</span><span class="sxs-lookup"><span data-stu-id="daf87-105">Syntax</span></span>  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="daf87-106">参数</span><span class="sxs-lookup"><span data-stu-id="daf87-106">Arguments</span></span>  
 <span data-ttu-id="daf87-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="daf87-107">*numeric_expression*</span></span>  
 <span data-ttu-id="daf87-108">是有效的数值类型的表达式。</span><span class="sxs-lookup"><span data-stu-id="daf87-108">Is an expression of a valid numeric type.</span></span> <span data-ttu-id="daf87-109">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="daf87-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="daf87-110">*length*</span><span class="sxs-lookup"><span data-stu-id="daf87-110">*length*</span></span>  
 <span data-ttu-id="daf87-111">是整数表达式。</span><span class="sxs-lookup"><span data-stu-id="daf87-111">Is an integer expression.</span></span> <span data-ttu-id="daf87-112">它是 *numeric_expression* 的舍入精度。</span><span class="sxs-lookup"><span data-stu-id="daf87-112">It is the precision to which *numeric_expression* is rounded.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="daf87-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="daf87-113">Result Types</span></span>  
 <span data-ttu-id="daf87-114">与 *numeric*_*expression.* 相同的类型。</span><span class="sxs-lookup"><span data-stu-id="daf87-114">The same type as *numeric*_*expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daf87-115">备注</span><span class="sxs-lookup"><span data-stu-id="daf87-115">Remarks</span></span>  
 <span data-ttu-id="daf87-116">*length* 参数的取值必须为正整数或零。</span><span class="sxs-lookup"><span data-stu-id="daf87-116">The *length* argument must evaluate to a positive integer or zero.</span></span>  
  
 <span data-ttu-id="daf87-117">如果该参数为空，则 ROUND 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="daf87-117">ROUND returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="daf87-118">表达式示例</span><span class="sxs-lookup"><span data-stu-id="daf87-118">Expression Examples</span></span>  
 <span data-ttu-id="daf87-119">下面的示例对数值进行舍入操作，使其精确到小数点后 3 位。</span><span class="sxs-lookup"><span data-stu-id="daf87-119">These examples round numeric literals to a length of three.</span></span> <span data-ttu-id="daf87-120">第一个返回结果为 137.1570，第二个为 137.1580。</span><span class="sxs-lookup"><span data-stu-id="daf87-120">The first return result is 137.1570, the second 137.1580.</span></span>  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a><span data-ttu-id="daf87-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="daf87-121">See Also</span></span>  
 [<span data-ttu-id="daf87-122">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="daf87-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
