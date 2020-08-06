---
title: '||（逻辑或）（SSIS 表达式） | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 72d4a1c7b54856675f0faa7f5f58452cb8bca450
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688072"
---
# <a name="-logical-or-ssis-expression"></a><span data-ttu-id="08283-102">||（逻辑或）（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="08283-102">|| (Logical OR) (SSIS Expression)</span></span>
  <span data-ttu-id="08283-103">执行“逻辑或”运算。</span><span class="sxs-lookup"><span data-stu-id="08283-103">Performs a logical OR operation.</span></span> <span data-ttu-id="08283-104">如果条件之一或两个条件都为 TRUE，则表达式计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="08283-104">The expression evaluates to TRUE if one or both conditions are TRUE.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08283-105">语法</span><span class="sxs-lookup"><span data-stu-id="08283-105">Syntax</span></span>  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a><span data-ttu-id="08283-106">参数</span><span class="sxs-lookup"><span data-stu-id="08283-106">Arguments</span></span>  
 <span data-ttu-id="08283-107">*boolean_expression1、boolean_expression2*</span><span class="sxs-lookup"><span data-stu-id="08283-107">*boolean_expression1, boolean_expression2*</span></span>  
 <span data-ttu-id="08283-108">计算结果为 TRUE、FALSE 或 NULL 的任意有效表达式。</span><span class="sxs-lookup"><span data-stu-id="08283-108">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="08283-109">结果类型</span><span class="sxs-lookup"><span data-stu-id="08283-109">Result Types</span></span>  
 <span data-ttu-id="08283-110">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="08283-110">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08283-111">备注</span><span class="sxs-lookup"><span data-stu-id="08283-111">Remarks</span></span>  
 <span data-ttu-id="08283-112">下表显示了 || 运算符的结果。</span><span class="sxs-lookup"><span data-stu-id="08283-112">The following table shows the result of the || operator.</span></span>  
  
|<span data-ttu-id="08283-113">结果</span><span class="sxs-lookup"><span data-stu-id="08283-113">Result</span></span>|<span data-ttu-id="08283-114">表达式</span><span class="sxs-lookup"><span data-stu-id="08283-114">Expression</span></span>|<span data-ttu-id="08283-115">表达式</span><span class="sxs-lookup"><span data-stu-id="08283-115">Expression</span></span>|  
|------------|----------------|----------------|  
|<span data-ttu-id="08283-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-116">TRUE</span></span>|<span data-ttu-id="08283-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-117">TRUE</span></span>|<span data-ttu-id="08283-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-118">TRUE</span></span>|  
|<span data-ttu-id="08283-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-119">TRUE</span></span>|<span data-ttu-id="08283-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-120">TRUE</span></span>|<span data-ttu-id="08283-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="08283-121">FALSE</span></span>|  
|<span data-ttu-id="08283-122">FALSE</span><span class="sxs-lookup"><span data-stu-id="08283-122">FALSE</span></span>|<span data-ttu-id="08283-123">FALSE</span><span class="sxs-lookup"><span data-stu-id="08283-123">FALSE</span></span>|<span data-ttu-id="08283-124">FALSE</span><span class="sxs-lookup"><span data-stu-id="08283-124">FALSE</span></span>|  
|<span data-ttu-id="08283-125">Null</span><span class="sxs-lookup"><span data-stu-id="08283-125">NULL</span></span>|<span data-ttu-id="08283-126">Null</span><span class="sxs-lookup"><span data-stu-id="08283-126">NULL</span></span>|<span data-ttu-id="08283-127">Null</span><span class="sxs-lookup"><span data-stu-id="08283-127">NULL</span></span>|  
|<span data-ttu-id="08283-128">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-128">TRUE</span></span>|<span data-ttu-id="08283-129">Null</span><span class="sxs-lookup"><span data-stu-id="08283-129">NULL</span></span>|<span data-ttu-id="08283-130">TRUE</span><span class="sxs-lookup"><span data-stu-id="08283-130">TRUE</span></span>|  
|<span data-ttu-id="08283-131">Null</span><span class="sxs-lookup"><span data-stu-id="08283-131">NULL</span></span>|<span data-ttu-id="08283-132">Null</span><span class="sxs-lookup"><span data-stu-id="08283-132">NULL</span></span>|<span data-ttu-id="08283-133">FALSE</span><span class="sxs-lookup"><span data-stu-id="08283-133">FALSE</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="08283-134">SSIS 表达式示例</span><span class="sxs-lookup"><span data-stu-id="08283-134">SSIS Expression Examples</span></span>  
 <span data-ttu-id="08283-135">该示例使用 **StandardCost** 和 **ListPrice** 列。</span><span class="sxs-lookup"><span data-stu-id="08283-135">This example uses the **StandardCost** and **ListPrice** columns.</span></span> <span data-ttu-id="08283-136">如果 **StandardCost** 列的值小于 300 或者 **ListPrice** 列的值大于 500，则该示例计算结果为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="08283-136">The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 or the **ListPrice** column is greater than 500.</span></span>  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 <span data-ttu-id="08283-137">该示例使用变量 **SPrice** 和 **LPrice** ，而不是数值。</span><span class="sxs-lookup"><span data-stu-id="08283-137">This example uses the variables **SPrice** and **LPrice** instead of numeric literals.</span></span>  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a><span data-ttu-id="08283-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08283-138">See Also</span></span>  
 <span data-ttu-id="08283-139">[|（位异或）（SSIS 表达式）](bitwise-inclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="08283-139">[&#124; &#40;Bitwise Inclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-inclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="08283-140">[^（位异或）（SSIS 表达式）](bitwise-exclusive-or-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="08283-140">[^ &#40;Bitwise Exclusive OR&#41; &#40;SSIS Expression&#41;](bitwise-exclusive-or-ssis-expression.md) </span></span>  
 <span data-ttu-id="08283-141">[运算符优先级和结合性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="08283-141">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="08283-142">运算符（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="08283-142">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
