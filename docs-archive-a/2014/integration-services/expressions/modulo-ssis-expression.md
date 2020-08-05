---
title: （取模）（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e23152fca9c9f2c7c3ac11490a56b03d1a1f9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581393"
---
# <a name="modulo-ssis-expression"></a><span data-ttu-id="778a1-102">（取模）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="778a1-102">(Modulo) (SSIS Expression)</span></span>
  <span data-ttu-id="778a1-103">将第一个数据表达式的值除以第二个数据表达式的值后，提供整数余数。</span><span class="sxs-lookup"><span data-stu-id="778a1-103">Provides the integer remainder after dividing the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="778a1-104">语法</span><span class="sxs-lookup"><span data-stu-id="778a1-104">Syntax</span></span>  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="778a1-105">参数</span><span class="sxs-lookup"><span data-stu-id="778a1-105">Arguments</span></span>  
 <span data-ttu-id="778a1-106">*被除数*</span><span class="sxs-lookup"><span data-stu-id="778a1-106">*dividend*</span></span>  
 <span data-ttu-id="778a1-107">被除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="778a1-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="778a1-108">*dividend* 可以是任意有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="778a1-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="778a1-109">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="778a1-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md)</span></span>  
  
 <span data-ttu-id="778a1-110">*除数*</span><span class="sxs-lookup"><span data-stu-id="778a1-110">*divisor*</span></span>  
 <span data-ttu-id="778a1-111">除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="778a1-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="778a1-112">*divisor* 可以是除 0 之外的任意有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="778a1-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="778a1-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="778a1-113">Result Types</span></span>  
 <span data-ttu-id="778a1-114">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="778a1-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="778a1-115">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="778a1-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="778a1-116">备注</span><span class="sxs-lookup"><span data-stu-id="778a1-116">Remarks</span></span>  
 <span data-ttu-id="778a1-117">两个表达式的计算结果必须为有符号或无符号整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="778a1-117">Both expressions must evaluate to signed or unsigned integer data types.</span></span>  
  
 <span data-ttu-id="778a1-118">如果任意一个操作数为 Null，则结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="778a1-118">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="778a1-119">不可对零取模。</span><span class="sxs-lookup"><span data-stu-id="778a1-119">Modulo zero is not legal.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="778a1-120">表达式示例</span><span class="sxs-lookup"><span data-stu-id="778a1-120">Expression Examples</span></span>  
 <span data-ttu-id="778a1-121">以下示例对两个数值取模。</span><span class="sxs-lookup"><span data-stu-id="778a1-121">This example computes the modulus from two numeric literals.</span></span> <span data-ttu-id="778a1-122">结果为 3。</span><span class="sxs-lookup"><span data-stu-id="778a1-122">The result is 3.</span></span>  
  
```  
42 % 13  
```  
  
 <span data-ttu-id="778a1-123">以下示例对 **SalesQuota** 列和一个数值文字取模。</span><span class="sxs-lookup"><span data-stu-id="778a1-123">This example computes the modulus from the **SalesQuota** column and a numeric literal.</span></span>  
  
```  
SalesQuota % 12  
```  
  
 <span data-ttu-id="778a1-124">以下示例对两个数值变量 **Sales$** 和 **Month**取模。</span><span class="sxs-lookup"><span data-stu-id="778a1-124">This example computes the modulus from two numeric variables **Sales$** and **Month**.</span></span> <span data-ttu-id="778a1-125">变量 **Sales$** 的名称包含 $ 字符，所以必须括在括号内。</span><span class="sxs-lookup"><span data-stu-id="778a1-125">The variable **Sales$** must be enclosed in brackets because the name includes the $ character.</span></span> <span data-ttu-id="778a1-126">有关详细信息，请参阅[标识符 (SSIS)](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="778a1-126">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
@[Sales$] % @Month  
```  
  
 <span data-ttu-id="778a1-127">以下示例使用取模运算符确定 **Value** 变量的值为偶数还是奇数，并使用条件运算符返回对结果进行说明的字符串。</span><span class="sxs-lookup"><span data-stu-id="778a1-127">This example uses the modulo operator to determine if the value of the **Value** variable is even or odd, and uses the conditional operator to return a string that describes the result.</span></span> <span data-ttu-id="778a1-128">有关详细信息，请参阅 [?：（条件）（SSIS 表达式）](conditional-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="778a1-128">For more information, see [? : &#40;Conditional&#41; &#40;SSIS Expression&#41;](conditional-ssis-expression.md).</span></span>  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a><span data-ttu-id="778a1-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="778a1-129">See Also</span></span>  
 <span data-ttu-id="778a1-130">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="778a1-130">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="778a1-131">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="778a1-131">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
