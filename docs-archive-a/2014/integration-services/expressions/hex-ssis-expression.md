---
title: HEX（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- hexadecimal data
- HEX function
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 640ae38ec5d2cd5ffb448e9aebde5ba5ceba2684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691823"
---
# <a name="hex-ssis-expression"></a><span data-ttu-id="5c8cc-102">HEX（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5c8cc-102">HEX (SSIS Expression)</span></span>
  <span data-ttu-id="5c8cc-103">返回一个表示整数的十六进制值的字符串。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-103">Returns a string representing the hexadecimal value of an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8cc-104">语法</span><span class="sxs-lookup"><span data-stu-id="5c8cc-104">Syntax</span></span>  
  
```  
  
HEX(integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="5c8cc-105">参数</span><span class="sxs-lookup"><span data-stu-id="5c8cc-105">Arguments</span></span>  
 <span data-ttu-id="5c8cc-106">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="5c8cc-106">*integer_expression*</span></span>  
 <span data-ttu-id="5c8cc-107">有符号或无符号整数。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-107">Is a signed or unsigned integer.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5c8cc-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="5c8cc-108">Result Types</span></span>  
 <span data-ttu-id="5c8cc-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="5c8cc-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c8cc-110">备注</span><span class="sxs-lookup"><span data-stu-id="5c8cc-110">Remarks</span></span>  
 <span data-ttu-id="5c8cc-111">如果 integer_expression 为 Null，则 HEX 返回 Null  。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-111">HEX returns null if *integer_expression* is null.</span></span>  
  
 <span data-ttu-id="5c8cc-112">integer_expression 参数的计算结果必须为整数  。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-112">The *integer_expression* argument must evaluate to an integer.</span></span> <span data-ttu-id="5c8cc-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="5c8cc-114">返回结果不包含限定符，如 0x 前缀。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-114">The return result does not include qualifiers such as the 0x prefix.</span></span> <span data-ttu-id="5c8cc-115">若要包含前缀，请使用 +（连接）运算符。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-115">To include a prefix, use the + (Concatenate) operator.</span></span> <span data-ttu-id="5c8cc-116">有关详细信息，请参阅 [+（连接）（SSIS 表达式）](concatenate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-116">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="5c8cc-117">HEX 计数法中的字符 A - F 显示为大写字符。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-117">The letters A - F, used in HEX notations, appear as uppercase characters.</span></span>  
  
 <span data-ttu-id="5c8cc-118">产生的整数数据类型的字符串的长度如下所示：</span><span class="sxs-lookup"><span data-stu-id="5c8cc-118">The length of the resulting string for integer data types is as follows:</span></span>  
  
-   <span data-ttu-id="5c8cc-119">DT_I1 和 DT_UI1 返回最大长度为 2 的字符串。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-119">DT_I1 and DT_UI1 return a string with a maximum length of 2.</span></span>  
  
-   <span data-ttu-id="5c8cc-120">DT_I2 和 DT_UI2 返回最大长度为 4 的字符串。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-120">DT_I2 and DT_UI2 return a string with a maximum length of 4.</span></span>  
  
-   <span data-ttu-id="5c8cc-121">DT_I4 和 DT_UI4 返回最大长度为 8 的字符串。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-121">DT_I4 and DT_UI4 return a string with a maximum length of 8.</span></span>  
  
-   <span data-ttu-id="5c8cc-122">DT_I8 和 DT_UI8 返回最大长度为 16 的字符串。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-122">DT_I8 and DT_UI8 return a string with a maximum length of 16.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="5c8cc-123">表达式示例</span><span class="sxs-lookup"><span data-stu-id="5c8cc-123">Expression Examples</span></span>  
 <span data-ttu-id="5c8cc-124">以下示例使用了一个数值。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-124">This example uses a numeric literal.</span></span> <span data-ttu-id="5c8cc-125">该函数将返回值 190。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-125">The function returns the value 190.</span></span>  
  
```  
HEX(400)   
```  
  
 <span data-ttu-id="5c8cc-126">以下示例使用了 **ReorderPoint** 列。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-126">This example uses the **ReorderPoint** column.</span></span> <span data-ttu-id="5c8cc-127">列数据类型为 `smallint`。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-127">The column data type is `smallint`.</span></span> <span data-ttu-id="5c8cc-128">如果 **ReorderPoint** 为 750，则函数返回 2EE。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-128">If **ReorderPoint** is 750, the function returns 2EE.</span></span>  
  
```  
HEX(ReorderPoint)   
```  
  
 <span data-ttu-id="5c8cc-129">以下示例使用了系统变量 **LocaleID**。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-129">This example uses **LocaleID**, a system variable.</span></span> <span data-ttu-id="5c8cc-130">如果 **LocaleID** 为 1033，则函数返回 409。</span><span class="sxs-lookup"><span data-stu-id="5c8cc-130">If **LocaleID** is 1033, the function returns 409.</span></span>  
  
```  
HEX(@LocaleID)  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c8cc-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c8cc-131">See Also</span></span>  
 [<span data-ttu-id="5c8cc-132">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="5c8cc-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
