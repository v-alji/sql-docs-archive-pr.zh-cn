---
title: '- （负号）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a2d8ba292f2d24633598ab080ddf75ded5e8bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691318"
---
# <a name="--negate-ssis-expression"></a><span data-ttu-id="877af-102">-（负号）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="877af-102">- (Negate) (SSIS Expression)</span></span>
  <span data-ttu-id="877af-103">对一个数值表达式求反。</span><span class="sxs-lookup"><span data-stu-id="877af-103">Negates a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877af-104">语法</span><span class="sxs-lookup"><span data-stu-id="877af-104">Syntax</span></span>  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="877af-105">参数</span><span class="sxs-lookup"><span data-stu-id="877af-105">Arguments</span></span>  
 <span data-ttu-id="877af-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="877af-106">*numeric_expression*</span></span>  
 <span data-ttu-id="877af-107">任何数值数据类型的有效表达式。</span><span class="sxs-lookup"><span data-stu-id="877af-107">Is any valid expression of any numeric data type.</span></span> <span data-ttu-id="877af-108">仅支持有符号数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="877af-108">Only signed numeric data types are supported.</span></span> <span data-ttu-id="877af-109">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="877af-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="877af-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="877af-110">Result Types</span></span>  
 <span data-ttu-id="877af-111">返回 *numeric_expression*的数据类型。</span><span class="sxs-lookup"><span data-stu-id="877af-111">Returns the data type of *numeric_expression*.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="877af-112">表达式示例</span><span class="sxs-lookup"><span data-stu-id="877af-112">Expression Examples</span></span>  
 <span data-ttu-id="877af-113">以下示例对 **Counter** 变量的值求反，并加上数值 50。</span><span class="sxs-lookup"><span data-stu-id="877af-113">This example negates the value of the **Counter** variable and adds the numeric literal 50.</span></span>  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a><span data-ttu-id="877af-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="877af-114">See Also</span></span>  
 <span data-ttu-id="877af-115">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="877af-115">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="877af-116">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="877af-116">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
