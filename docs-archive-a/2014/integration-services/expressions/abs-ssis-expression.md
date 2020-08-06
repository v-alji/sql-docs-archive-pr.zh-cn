---
title: ABS（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f429dda94282646ef769a1c393f9fa54b56e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588677"
---
# <a name="abs-ssis-expression"></a><span data-ttu-id="0ee30-102">ABS（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0ee30-102">ABS (SSIS Expression)</span></span>
  <span data-ttu-id="0ee30-103">返回数值表达式的绝对值。</span><span class="sxs-lookup"><span data-stu-id="0ee30-103">Returns the absolute, positive value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee30-104">语法</span><span class="sxs-lookup"><span data-stu-id="0ee30-104">Syntax</span></span>  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ee30-105">参数</span><span class="sxs-lookup"><span data-stu-id="0ee30-105">Arguments</span></span>  
 <span data-ttu-id="0ee30-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="0ee30-106">*numeric_expression*</span></span>  
 <span data-ttu-id="0ee30-107">是有符号或无符号的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="0ee30-107">Is a signed or unsigned numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0ee30-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="0ee30-108">Result Types</span></span>  
 <span data-ttu-id="0ee30-109">提交给函数的数值表达式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0ee30-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ee30-110">备注</span><span class="sxs-lookup"><span data-stu-id="0ee30-110">Remarks</span></span>  
 <span data-ttu-id="0ee30-111">如果该参数为空，则 ABS 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="0ee30-111">ABS returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="0ee30-112">表达式示例</span><span class="sxs-lookup"><span data-stu-id="0ee30-112">Expression Examples</span></span>  
 <span data-ttu-id="0ee30-113">这些示例对一个正数和一个负数应用 ABS 函数。</span><span class="sxs-lookup"><span data-stu-id="0ee30-113">These examples apply the ABS function to a positive and a negative number.</span></span> <span data-ttu-id="0ee30-114">两者都返回 1.23。</span><span class="sxs-lookup"><span data-stu-id="0ee30-114">Both return 1.23.</span></span>  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 <span data-ttu-id="0ee30-115">此示例对将变量 **HighTemperature** 和 **LowTempature**的值相减的表达式应用 ABS 函数。</span><span class="sxs-lookup"><span data-stu-id="0ee30-115">This example applies the ABS function to an expression that subtracts values in the variables **HighTemperature** and **LowTempature**.</span></span>  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ee30-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ee30-116">See Also</span></span>  
 [<span data-ttu-id="0ee30-117">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="0ee30-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
