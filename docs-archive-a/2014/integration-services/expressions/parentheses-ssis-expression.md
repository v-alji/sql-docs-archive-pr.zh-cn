---
title: ()（括号）（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e390e10e485bd9cc22480300b6a9c33098bda8f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692998"
---
# <a name="-parentheses-ssis-expression"></a><span data-ttu-id="8a136-102">()（括号）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8a136-102">() (Parentheses) (SSIS Expression)</span></span>
  <span data-ttu-id="8a136-103">标识表达式的计算顺序。</span><span class="sxs-lookup"><span data-stu-id="8a136-103">Identifies the evaluation order of expressions.</span></span> <span data-ttu-id="8a136-104">包括在括号内的表达式具有最高的计算优先级。</span><span class="sxs-lookup"><span data-stu-id="8a136-104">Expressions enclosed in parentheses have the highest evaluation precedence.</span></span> <span data-ttu-id="8a136-105">包括在括号内的嵌套表达式按照从内到外的顺序计算。</span><span class="sxs-lookup"><span data-stu-id="8a136-105">Nested expressions enclosed in parentheses are evaluated in inner-to-outer order.</span></span>  
  
 <span data-ttu-id="8a136-106">括号还可用来使复杂的表达式变得更易理解。</span><span class="sxs-lookup"><span data-stu-id="8a136-106">Parentheses are also used to make complex expressions easier to understand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a136-107">语法</span><span class="sxs-lookup"><span data-stu-id="8a136-107">Syntax</span></span>  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a136-108">参数</span><span class="sxs-lookup"><span data-stu-id="8a136-108">Arguments</span></span>  
 <span data-ttu-id="8a136-109">*expression*</span><span class="sxs-lookup"><span data-stu-id="8a136-109">*expression*</span></span>  
 <span data-ttu-id="8a136-110">为任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="8a136-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8a136-111">结果类型</span><span class="sxs-lookup"><span data-stu-id="8a136-111">Result Types</span></span>  
 <span data-ttu-id="8a136-112">*expression*的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8a136-112">The data type of *expression*.</span></span> <span data-ttu-id="8a136-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8a136-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="8a136-114">表达式示例</span><span class="sxs-lookup"><span data-stu-id="8a136-114">Expression Examples</span></span>  
 <span data-ttu-id="8a136-115">该示例显示如何使用括号修改运算符优先顺序。</span><span class="sxs-lookup"><span data-stu-id="8a136-115">This example shows how the use of parenthesis modifies the precedence of operators.</span></span> <span data-ttu-id="8a136-116">第一个表达式取值为 100，而第二个则取值为 31。</span><span class="sxs-lookup"><span data-stu-id="8a136-116">The first expression evaluates to 100, whereas the second one evaluates to 31.</span></span>  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a136-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a136-117">See Also</span></span>  
 <span data-ttu-id="8a136-118">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="8a136-118">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="8a136-119">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="8a136-119">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
