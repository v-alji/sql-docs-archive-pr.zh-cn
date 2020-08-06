---
title: '- （减）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 79c47689baf47c33952c6b208ac622e9920d05fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689961"
---
# <a name="--subtract-ssis-expression"></a><span data-ttu-id="1d3b1-102">-（减）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1d3b1-102">- (Subtract) (SSIS Expression)</span></span>
  <span data-ttu-id="1d3b1-103">从第一个数值表达式的值中减去第二个数值表达式的值。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-103">Subtracts the second numeric expression from the first one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d3b1-104">语法</span><span class="sxs-lookup"><span data-stu-id="1d3b1-104">Syntax</span></span>  
  
```  
  
numeric_expression1 - numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1d3b1-105">参数</span><span class="sxs-lookup"><span data-stu-id="1d3b1-105">Arguments</span></span>  
 <span data-ttu-id="1d3b1-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="1d3b1-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="1d3b1-107">是数值数据类型的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="1d3b1-108">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1d3b1-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="1d3b1-109">Result Types</span></span>  
 <span data-ttu-id="1d3b1-110">由两个参数的数据类型决定。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-110">Determined by the data types of the two arguments.</span></span> <span data-ttu-id="1d3b1-111">有关详细信息，请参阅 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d3b1-112">备注</span><span class="sxs-lookup"><span data-stu-id="1d3b1-112">Remarks</span></span>  
 <span data-ttu-id="1d3b1-113">用括号将减法一元表达式括起来，以便确保按正确顺序对该表达式进行求值。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-113">Enclose the minus unary expression in parenthesis to ensure that the expression is evaluated in the correct order</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d3b1-114">备注</span><span class="sxs-lookup"><span data-stu-id="1d3b1-114">Remarks</span></span>  
 <span data-ttu-id="1d3b1-115">如果任意一个操作数为 Null，则结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-115">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="1d3b1-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="1d3b1-116">Expression Examples</span></span>  
 <span data-ttu-id="1d3b1-117">此示例将数值相减。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-117">This example subtracts numeric literals.</span></span>  
  
```  
5 - 6.09  
```  
  
 <span data-ttu-id="1d3b1-118">此示例从 **ListPrice** 列中的值中减去 **StandardCost** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-118">This example subtracts the value in the **StandardCost** column from the value in the **ListPrice** column.</span></span>  
  
```  
ListPrice - StandardCost  
```  
  
 <span data-ttu-id="1d3b1-119">此示例从 **ListPrice** 列中减去计算后的值。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-119">This example subtracts a calculated value from the **ListPrice** column.</span></span> <span data-ttu-id="1d3b1-120">变量 **Discount%** 必须用括号括起来，因为该名称中包含字符 %。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-120">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="1d3b1-121">有关详细信息，请参阅[标识符 (SSIS)](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3b1-121">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d3b1-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d3b1-122">See Also</span></span>  
 <span data-ttu-id="1d3b1-123">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="1d3b1-123">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="1d3b1-124">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="1d3b1-124">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
