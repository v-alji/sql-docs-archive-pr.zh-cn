---
title: ~（位非）（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588663"
---
# <a name="-bitwise-not-ssis-expression"></a><span data-ttu-id="dfdfd-102">~ （位非）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="dfdfd-102">~ (Bitwise Not) (SSIS Expression)</span></span>
  <span data-ttu-id="dfdfd-103">对整数执行位求反运算。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-103">Performs a bitwise negation of an integer.</span></span> <span data-ttu-id="dfdfd-104">此运算符可应用于有符号和无符号整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-104">This operator can be applied to signed and unsigned integer data types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdfd-105">语法</span><span class="sxs-lookup"><span data-stu-id="dfdfd-105">Syntax</span></span>  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="dfdfd-106">参数</span><span class="sxs-lookup"><span data-stu-id="dfdfd-106">Arguments</span></span>  
 <span data-ttu-id="dfdfd-107">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="dfdfd-107">*integer_expression*</span></span>  
 <span data-ttu-id="dfdfd-108">整数数据类型的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-108">Is any valid expression of an integer data type.</span></span> <span data-ttu-id="dfdfd-109">integer  _expression  是一个整数，该整数转换为二进制数以进行位运算。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-109">*integer*_*expression* is an integer that is transformed into a binary number for the bitwise operation.</span></span> <span data-ttu-id="dfdfd-110">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dfdfd-111">结果类型</span><span class="sxs-lookup"><span data-stu-id="dfdfd-111">Result Types</span></span>  
 <span data-ttu-id="dfdfd-112">返回 integer_expression  数据类型。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-112">Returns the data type of *integer_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfdfd-113">备注</span><span class="sxs-lookup"><span data-stu-id="dfdfd-113">Remarks</span></span>  
 <span data-ttu-id="dfdfd-114">无</span><span class="sxs-lookup"><span data-stu-id="dfdfd-114">None</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="dfdfd-115">表达式示例</span><span class="sxs-lookup"><span data-stu-id="dfdfd-115">Expression Examples</span></span>  
 <span data-ttu-id="dfdfd-116">以下示例对数值 170 (0000 0000 1010 1010) 执行位 ~（非）运算。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-116">This example performs a bitwise ~ (NOT) operation on the number 170 (0000 0000 1010 1010).</span></span> <span data-ttu-id="dfdfd-117">该数值是一个有符号整数。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-117">The number is a signed integer.</span></span>  
  
```  
  
~ 170  
```  
  
 <span data-ttu-id="dfdfd-118">表达式的计算结果为 -170 (1111111101010101)。</span><span class="sxs-lookup"><span data-stu-id="dfdfd-118">The expression evaluates to -170 (1111111101010101).</span></span>  
  
 <span data-ttu-id="dfdfd-119">0000000010101010</span><span class="sxs-lookup"><span data-stu-id="dfdfd-119">0000000010101010</span></span>  
  
 ---------------------\-  
  
 <span data-ttu-id="dfdfd-120">1111111101010101</span><span class="sxs-lookup"><span data-stu-id="dfdfd-120">1111111101010101</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdfd-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dfdfd-121">See Also</span></span>  
 <span data-ttu-id="dfdfd-122">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="dfdfd-122">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="dfdfd-123">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="dfdfd-123">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
