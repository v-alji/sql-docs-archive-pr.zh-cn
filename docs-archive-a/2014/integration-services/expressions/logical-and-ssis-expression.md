---
title: '&amp;&amp;（逻辑与）（SSIS 表达式）| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8d973d7d4e86f88f7ae88c820ed4e4a5c1ce526f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688071"
---
# <a name="ampamp-logical-and-ssis-expression"></a><span data-ttu-id="9a924-102">&amp;&amp;（逻辑与）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9a924-102">&amp;&amp; (Logical AND) (SSIS Expression)</span></span>
  <span data-ttu-id="9a924-103">执行“逻辑与”运算。</span><span class="sxs-lookup"><span data-stu-id="9a924-103">Performs a logical AND operation.</span></span> <span data-ttu-id="9a924-104">如果所有条件都为 TRUE，则表达式计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="9a924-104">The expression evaluates to TRUE if all conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a924-105">语法</span><span class="sxs-lookup"><span data-stu-id="9a924-105">Syntax</span></span>  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a924-106">参数</span><span class="sxs-lookup"><span data-stu-id="9a924-106">Arguments</span></span>  
 <span data-ttu-id="9a924-107">*boolean _expression1、boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="9a924-107">*boolean _expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="9a924-108">计算结果为 TRUE、FALSE 或 NULL 的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="9a924-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a924-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="9a924-109">Result Types</span></span>  
 <span data-ttu-id="9a924-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="9a924-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a924-111">备注</span><span class="sxs-lookup"><span data-stu-id="9a924-111">Remarks</span></span>  
 <span data-ttu-id="9a924-112">下表显示 && 运算符的结果。</span><span class="sxs-lookup"><span data-stu-id="9a924-112">The following table shows the result of the && operator.</span></span>  
  
|<span data-ttu-id="9a924-113">结果</span><span class="sxs-lookup"><span data-stu-id="9a924-113">Result</span></span>|<span data-ttu-id="9a924-114">表达式</span><span class="sxs-lookup"><span data-stu-id="9a924-114">Expression</span></span>|<span data-ttu-id="9a924-115">表达式</span><span class="sxs-lookup"><span data-stu-id="9a924-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="9a924-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="9a924-116">TRUE</span></span>|<span data-ttu-id="9a924-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="9a924-117">TRUE</span></span>|<span data-ttu-id="9a924-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="9a924-118">TRUE</span></span>|  
|<span data-ttu-id="9a924-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-119">FALSE</span></span>|<span data-ttu-id="9a924-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="9a924-120">TRUE</span></span>|<span data-ttu-id="9a924-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-121">FALSE</span></span>|  
|<span data-ttu-id="9a924-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-122">FALSE</span></span>|<span data-ttu-id="9a924-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-123">FALSE</span></span>|<span data-ttu-id="9a924-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-124">FALSE</span></span>|  
|<span data-ttu-id="9a924-125">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-125">NULL</span></span>|<span data-ttu-id="9a924-126">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-126">NULL</span></span>|<span data-ttu-id="9a924-127">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-127">NULL</span></span>|  
|<span data-ttu-id="9a924-128">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-128">NULL</span></span>|<span data-ttu-id="9a924-129">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-129">NULL</span></span>|<span data-ttu-id="9a924-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="9a924-130">TRUE</span></span>|  
|<span data-ttu-id="9a924-131">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-131">FALSE</span></span>|<span data-ttu-id="9a924-132">Null</span><span class="sxs-lookup"><span data-stu-id="9a924-132">NULL</span></span>|<span data-ttu-id="9a924-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="9a924-133">FALSE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="9a924-134">表达式示例</span><span class="sxs-lookup"><span data-stu-id="9a924-134">Expression Examples</span></span>  
 <span data-ttu-id="9a924-135">该示例使用 **StandardCost** 和 **ListPrice** 列。</span><span class="sxs-lookup"><span data-stu-id="9a924-135">This example uses the **StandardCost** and the **ListPrice** columns.</span></span> <span data-ttu-id="9a924-136">如果 **StandardCost** 列的值小于 300，并且 **ListPrice** 列的值大于 500，则该示例计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="9a924-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 <span data-ttu-id="9a924-137">此示例使用变量 **SPrice** 和 **LPrice** ，而不是文字。</span><span class="sxs-lookup"><span data-stu-id="9a924-137">This example uses the variables **SPrice** and **LPrice** instead of literals.</span></span>  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a924-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a924-138">See Also</span></span>  
 <span data-ttu-id="9a924-139">[&（位与）（SSIS 表达式）](bitwise-and-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9a924-139">[& &#40;Bitwise AND&#41; &#40;SSIS Expression&#41;](bitwise-and-ssis-expression.md) </span></span>  
 <span data-ttu-id="9a924-140">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="9a924-140">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="9a924-141">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9a924-141">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
