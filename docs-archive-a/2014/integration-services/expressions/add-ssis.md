---
title: + +（加）(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe1e8f2118e6328582cb24abfd44eef5f3b15f79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588675"
---
# <a name="-add-ssis"></a><span data-ttu-id="92700-102">+（加）(SSIS)</span><span class="sxs-lookup"><span data-stu-id="92700-102">+ (Add) (SSIS)</span></span>
  <span data-ttu-id="92700-103">将两个数值表达式相加。</span><span class="sxs-lookup"><span data-stu-id="92700-103">Adds two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92700-104">语法</span><span class="sxs-lookup"><span data-stu-id="92700-104">Syntax</span></span>  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="92700-105">参数</span><span class="sxs-lookup"><span data-stu-id="92700-105">Arguments</span></span>  
 <span data-ttu-id="92700-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="92700-106">*numeric_expression1, numeric_ expression2*</span></span>  
 <span data-ttu-id="92700-107">是数值数据类型的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="92700-107">Is any valid expression of a numeric data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="92700-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="92700-108">Result Types</span></span>  
 <span data-ttu-id="92700-109">由两个参数的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="92700-109">Determined by data types of the two arguments.</span></span> <span data-ttu-id="92700-110">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="92700-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92700-111">备注</span><span class="sxs-lookup"><span data-stu-id="92700-111">Remarks</span></span>  
 <span data-ttu-id="92700-112">如果任意一个操作数为 Null，则结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="92700-112">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="92700-113">表达式示例</span><span class="sxs-lookup"><span data-stu-id="92700-113">Expression Examples</span></span>  
 <span data-ttu-id="92700-114">此示例将数值相加。</span><span class="sxs-lookup"><span data-stu-id="92700-114">This example adds numeric literals.</span></span>  
  
```  
5 + 6.09 + 7.0  
```  
  
 <span data-ttu-id="92700-115">此示例将 **VacationHours** 和 **SickLeaveHours** 列中的值相加。</span><span class="sxs-lookup"><span data-stu-id="92700-115">This example adds values in the **VacationHours** and **SickLeaveHours** columns.</span></span>  
  
```  
VacationHours + SickLeaveHours  
```  
  
 <span data-ttu-id="92700-116">此示例将计算后的值添加到 **StandardCost** 列。</span><span class="sxs-lookup"><span data-stu-id="92700-116">This example adds a calculated value to the **StandardCost** column.</span></span> <span data-ttu-id="92700-117">变量 **Profit%** 必须用方括号括起来，因为该名称包含 % 字符。</span><span class="sxs-lookup"><span data-stu-id="92700-117">The variable **Profit%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="92700-118">有关详细信息，请参阅[标识符 (SSIS)](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="92700-118">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="92700-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92700-119">See Also</span></span>  
 <span data-ttu-id="92700-120">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="92700-120">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="92700-121">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="92700-121">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
