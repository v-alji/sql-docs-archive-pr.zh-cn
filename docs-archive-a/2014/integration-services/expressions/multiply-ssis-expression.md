---
title: '* *（乘）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16d8429a869b60be31a94244a2ce47d515770c6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581390"
---
# <a name="-multiply-ssis-expression"></a><span data-ttu-id="f249f-102">\*（乘）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f249f-102">\* (Multiply) (SSIS Expression)</span></span>
  <span data-ttu-id="f249f-103">将两个数值表达式相乘。</span><span class="sxs-lookup"><span data-stu-id="f249f-103">Multiplies two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f249f-104">语法</span><span class="sxs-lookup"><span data-stu-id="f249f-104">Syntax</span></span>  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f249f-105">参数</span><span class="sxs-lookup"><span data-stu-id="f249f-105">Arguments</span></span>  
 <span data-ttu-id="f249f-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="f249f-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="f249f-107">是数值数据类型的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="f249f-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="f249f-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f249f-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f249f-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="f249f-109">Result Types</span></span>  
 <span data-ttu-id="f249f-110">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="f249f-110">Determined by data types of the two arguments.</span></span> <span data-ttu-id="f249f-111">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f249f-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f249f-112">备注</span><span class="sxs-lookup"><span data-stu-id="f249f-112">Remarks</span></span>  
 <span data-ttu-id="f249f-113">如果任意一个操作数为 Null，则结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="f249f-113">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f249f-114">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f249f-114">Expression Examples</span></span>  
 <span data-ttu-id="f249f-115">以下示例将数值相乘。</span><span class="sxs-lookup"><span data-stu-id="f249f-115">This example multiplies numeric literals.</span></span>  
  
```  
5 * 6.09  
```  
  
 <span data-ttu-id="f249f-116">以下示例将 **ListPrice** 列中的值乘以 10%。</span><span class="sxs-lookup"><span data-stu-id="f249f-116">This example multiplies values in the **ListPrice** column by 10 percent.</span></span>  
  
```  
ListPrice * .10  
```  
  
 <span data-ttu-id="f249f-117">以下示例从 **ListPrice** 列减去表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="f249f-117">This example subtracts the result of an expression from the **ListPrice** column.</span></span> <span data-ttu-id="f249f-118">变量 **Discount%** 必须用括号括起来，因为该名称中包含字符 %。</span><span class="sxs-lookup"><span data-stu-id="f249f-118">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="f249f-119">有关详细信息，请参阅[标识符 (SSIS)](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="f249f-119">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="f249f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f249f-120">See Also</span></span>  
 <span data-ttu-id="f249f-121">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="f249f-121">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="f249f-122">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f249f-122">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
