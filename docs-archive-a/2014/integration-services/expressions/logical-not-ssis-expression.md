---
title: '! （逻辑非）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bbf313930575e864f1556952425567fca96db15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581395"
---
# <a name="-logical-not-ssis-expression"></a><span data-ttu-id="f6886-103">!</span><span class="sxs-lookup"><span data-stu-id="f6886-103">!</span></span> <span data-ttu-id="f6886-104">（逻辑非）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f6886-104">(Logical Not) (SSIS Expression)</span></span>
  <span data-ttu-id="f6886-105">对布尔操作数求反。</span><span class="sxs-lookup"><span data-stu-id="f6886-105">Negates a Boolean operand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6886-106">此 !</span><span class="sxs-lookup"><span data-stu-id="f6886-106">The !</span></span> <span data-ttu-id="f6886-107">运算符不能与其他运算符一起使用。</span><span class="sxs-lookup"><span data-stu-id="f6886-107">operator cannot be used in conjunction with other operators.</span></span> <span data-ttu-id="f6886-108">例如，不能将 !</span><span class="sxs-lookup"><span data-stu-id="f6886-108">For example, you cannot combine the !</span></span> <span data-ttu-id="f6886-109">和 > 运算符组合为 !>.</span><span class="sxs-lookup"><span data-stu-id="f6886-109">and the > operators into the !>.</span></span> <span data-ttu-id="f6886-110">运算符。</span><span class="sxs-lookup"><span data-stu-id="f6886-110">operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6886-111">语法</span><span class="sxs-lookup"><span data-stu-id="f6886-111">Syntax</span></span>  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6886-112">参数</span><span class="sxs-lookup"><span data-stu-id="f6886-112">Arguments</span></span>  
 <span data-ttu-id="f6886-113">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="f6886-113">*boolean_expression*</span></span>  
 <span data-ttu-id="f6886-114">计算结果为布尔值的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="f6886-114">Is any valid expression that evaluates to a Boolean.</span></span> <span data-ttu-id="f6886-115">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f6886-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f6886-116">结果类型</span><span class="sxs-lookup"><span data-stu-id="f6886-116">Result Types</span></span>  
 <span data-ttu-id="f6886-117">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="f6886-117">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6886-118">备注</span><span class="sxs-lookup"><span data-stu-id="f6886-118">Remarks</span></span>  
 <span data-ttu-id="f6886-119">下表显示了 !</span><span class="sxs-lookup"><span data-stu-id="f6886-119">The following table shows the result of the !</span></span> <span data-ttu-id="f6886-120">操作所需的后续步骤。</span><span class="sxs-lookup"><span data-stu-id="f6886-120">operation.</span></span>  
  
|<span data-ttu-id="f6886-121">原始布尔表达式</span><span class="sxs-lookup"><span data-stu-id="f6886-121">Original Boolean expression</span></span>|<span data-ttu-id="f6886-122">应用 !</span><span class="sxs-lookup"><span data-stu-id="f6886-122">After applying the !</span></span> <span data-ttu-id="f6886-123">运算符后的表达式</span><span class="sxs-lookup"><span data-stu-id="f6886-123">operator</span></span>|  
|---------------------------------|------------------------------------|  
|<span data-ttu-id="f6886-124">TRUE</span><span class="sxs-lookup"><span data-stu-id="f6886-124">TRUE</span></span>|<span data-ttu-id="f6886-125">FALSE</span><span class="sxs-lookup"><span data-stu-id="f6886-125">FALSE</span></span>|  
|<span data-ttu-id="f6886-126">Null</span><span class="sxs-lookup"><span data-stu-id="f6886-126">NULL</span></span>|<span data-ttu-id="f6886-127">Null</span><span class="sxs-lookup"><span data-stu-id="f6886-127">NULL</span></span>|  
|<span data-ttu-id="f6886-128">FALSE</span><span class="sxs-lookup"><span data-stu-id="f6886-128">FALSE</span></span>|<span data-ttu-id="f6886-129">TRUE</span><span class="sxs-lookup"><span data-stu-id="f6886-129">TRUE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="f6886-130">表达式示例</span><span class="sxs-lookup"><span data-stu-id="f6886-130">Expression Examples</span></span>  
 <span data-ttu-id="f6886-131">以下示例中，如果 **Color** 列的值为“red”，则计算结果为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="f6886-131">This example evaluates to FALSE if the **Color** column value is "red".</span></span>  
  
```  
!(Color == "red")  
```  
  
 <span data-ttu-id="f6886-132">在以下示例中，如果 **MonthNumber** 变量的值和代表当前月份的整数相同，则计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="f6886-132">This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month.</span></span> <span data-ttu-id="f6886-133">有关详细信息，请参阅 [MONTH（SSIS 表达式）](month-ssis-expression.md)和 [GETDATE（SSIS 表达式）](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="f6886-133">For more information, see [MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) and [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6886-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6886-134">See Also</span></span>  
 <span data-ttu-id="f6886-135">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="f6886-135">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="f6886-136">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="f6886-136">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
