---
title: 除（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4541cd4601047770d1bf361077b1c474219e8833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578955"
---
# <a name="divide-ssis-expression"></a><span data-ttu-id="f5c2d-102">除（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5c2d-102">Divide (SSIS Expression)</span></span>
  <span data-ttu-id="f5c2d-103">用第一个数值表达式除以第二个数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-103">Divides the first numeric expression by the second one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c2d-104">语法</span><span class="sxs-lookup"><span data-stu-id="f5c2d-104">Syntax</span></span>  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5c2d-105">参数</span><span class="sxs-lookup"><span data-stu-id="f5c2d-105">Arguments</span></span>  
 <span data-ttu-id="f5c2d-106">*被除数*</span><span class="sxs-lookup"><span data-stu-id="f5c2d-106">*dividend*</span></span>  
 <span data-ttu-id="f5c2d-107">被除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-107">Is the numeric expression to divide.</span></span> <span data-ttu-id="f5c2d-108">*dividend* 可以是任意有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-108">*dividend* can be any valid numeric expression.</span></span> <span data-ttu-id="f5c2d-109">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="f5c2d-110">*除数*</span><span class="sxs-lookup"><span data-stu-id="f5c2d-110">*divisor*</span></span>  
 <span data-ttu-id="f5c2d-111">除数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-111">Is the numeric expression to divide the dividend by.</span></span> <span data-ttu-id="f5c2d-112">*divisor* 可以是除 0 之外的任意有效的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-112">*divisor* can be any valid numeric expression except zero.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f5c2d-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="f5c2d-113">Result Types</span></span>  
 <span data-ttu-id="f5c2d-114">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-114">Determined by data types of the two arguments.</span></span> <span data-ttu-id="f5c2d-115">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-115">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c2d-116">备注</span><span class="sxs-lookup"><span data-stu-id="f5c2d-116">Remarks</span></span>  
 <span data-ttu-id="f5c2d-117">如果任意一个操作数为 Null，则结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-117">If either operand is null, the result is null.</span></span>  
  
 <span data-ttu-id="f5c2d-118">被零除是非法的。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-118">Dividing by zero is not legal.</span></span> <span data-ttu-id="f5c2d-119">根据 *divisor* 子表达式的计算方法，会出现下列错误之一：</span><span class="sxs-lookup"><span data-stu-id="f5c2d-119">Depending on how the *divisor* subexpression is evaluated, one of following errors occurs:</span></span>  
  
-   <span data-ttu-id="f5c2d-120">如果计算结果为零的 *divisor* 子表达式是常量，则错误将在设计时发生，导致表达式验证失败。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-120">If the *divisor* subexpression that evaluates to zero is a constant, the error appears at design time, causing the expression to fail validation.</span></span>  
  
-   <span data-ttu-id="f5c2d-121">如果计算结果为零的 *divisor* 子表达式包含变量（但不是输入列），则在包运行前此表达式所属组件的预执行验证将失败。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-121">If the *divisor* subexpression that evaluates to zero contains variables, but no input columns, the component to which the expression belongs fails the pre-execution validation that occurs before the package runs.</span></span>  
  
-   <span data-ttu-id="f5c2d-122">如果计算结果为零的 *divisor* 子表达式包含输入列，则错误将在运行时发生，并根据数据流组件的错误流规则来处理错误。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-122">If the *divisor* subexpression that evaluates to zero contains input columns, the error appears at run time and is handled according to the error flow rules of the data flow component.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f5c2d-123">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f5c2d-123">Expression Examples</span></span>  
 <span data-ttu-id="f5c2d-124">此示例将两个数值相除。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-124">This example divides two numeric literals.</span></span>  
  
```  
25 / 5  
```  
  
 <span data-ttu-id="f5c2d-125">此示例用 **ListPrice** 列中的值除以 **StandardCost** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="f5c2d-125">This example divides values in the **ListPrice** column by values in the **StandardCost** column.</span></span>  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5c2d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5c2d-126">See Also</span></span>  
 <span data-ttu-id="f5c2d-127">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="f5c2d-127">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="f5c2d-128">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f5c2d-128">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
