---
title: REPLICATE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REPLICATE function
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9502df5bc20c6ad85f1f98fb57fe6b3cf431cc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689982"
---
# <a name="replicate-ssis-expression"></a><span data-ttu-id="ca4df-102">REPLICATE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ca4df-102">REPLICATE (SSIS Expression)</span></span>
  <span data-ttu-id="ca4df-103">返回多次复制后的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ca4df-103">Returns a character expression that is replicated a number of times.</span></span> <span data-ttu-id="ca4df-104">*times* 参数的计算结果必须为整数。</span><span class="sxs-lookup"><span data-stu-id="ca4df-104">The *times* argument must evaluate to an integer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca4df-105">REPLICATE 函数经常使用长字符串，因此更有可能受到对表达式长度 4000 个字符的限制。</span><span class="sxs-lookup"><span data-stu-id="ca4df-105">The REPLICATE function frequently uses long strings, and therefore is more likely to incur the 4000-character limit on expression length.</span></span> <span data-ttu-id="ca4df-106">如果某表达式的计算结果具有 Integration Services 数据类型 DT_WSTR 或 DT_STR，则该表达式将被在 4000 个字符处截断。</span><span class="sxs-lookup"><span data-stu-id="ca4df-106">If the evaluation result of an expression has the Integration Services data type DT_WSTR or DT_STR, the expression will be truncated at 4000 characters.</span></span> <span data-ttu-id="ca4df-107">如果子表达式的结果类型为 DT_STR 或 DT_WSTR，则该子表达式将同样被截断为 4000 个字符，与总体表达式结果类型无关。</span><span class="sxs-lookup"><span data-stu-id="ca4df-107">If the result type of a sub-expression is DT_STR or DT_WSTR, that sub-expression likewise will be truncated to 4000 characters, regardless of the overall expression result type.</span></span> <span data-ttu-id="ca4df-108">可以适当处理截断的结果，否则会导致警告或错误。</span><span class="sxs-lookup"><span data-stu-id="ca4df-108">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="ca4df-109">有关详细信息，请参阅[语法 (SSIS)](syntax-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="ca4df-109">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4df-110">语法</span><span class="sxs-lookup"><span data-stu-id="ca4df-110">Syntax</span></span>  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca4df-111">参数</span><span class="sxs-lookup"><span data-stu-id="ca4df-111">Arguments</span></span>  
 <span data-ttu-id="ca4df-112">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="ca4df-112">*character_expression*</span></span>  
 <span data-ttu-id="ca4df-113">要复制的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="ca4df-113">Is a character expression to replicate.</span></span>  
  
 <span data-ttu-id="ca4df-114">*times*</span><span class="sxs-lookup"><span data-stu-id="ca4df-114">*times*</span></span>  
 <span data-ttu-id="ca4df-115">指定 character_expression 复制次数的整数表达式  。</span><span class="sxs-lookup"><span data-stu-id="ca4df-115">Is an integer expression that specifies the number of times *character_expression* is replicated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ca4df-116">结果类型</span><span class="sxs-lookup"><span data-stu-id="ca4df-116">Result Types</span></span>  
 <span data-ttu-id="ca4df-117">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="ca4df-117">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca4df-118">备注</span><span class="sxs-lookup"><span data-stu-id="ca4df-118">Remarks</span></span>  
 <span data-ttu-id="ca4df-119">如果 times 为 0，则该函数返回零长度的字符串  。</span><span class="sxs-lookup"><span data-stu-id="ca4df-119">If *times* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="ca4df-120">如果 *times* 为负数，则该函数返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="ca4df-120">If *times* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="ca4df-121">*times* 参数还可以使用变量和列。</span><span class="sxs-lookup"><span data-stu-id="ca4df-121">The *times* argument can also use variables and columns.</span></span>  
  
 <span data-ttu-id="ca4df-122">REPLICATE 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ca4df-122">REPLICATE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="ca4df-123">如果 character_expression 参数是字符串文字或数据类型为 DT_STR 的数据列，则它在 REPLICATE 执行操作前隐式转换为 DT_WSTR 数据类型  。</span><span class="sxs-lookup"><span data-stu-id="ca4df-123">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before REPLICATE performs its operation.</span></span> <span data-ttu-id="ca4df-124">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ca4df-124">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="ca4df-125">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="ca4df-125">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="ca4df-126">如果有一个参数为空，REPLICATE 将返回空结果。</span><span class="sxs-lookup"><span data-stu-id="ca4df-126">REPLICATE returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ca4df-127">表达式示例</span><span class="sxs-lookup"><span data-stu-id="ca4df-127">Expression Examples</span></span>  
 <span data-ttu-id="ca4df-128">以下示例将一个字符串文字复制了三次。</span><span class="sxs-lookup"><span data-stu-id="ca4df-128">This example replicates a string literal three times.</span></span> <span data-ttu-id="ca4df-129">返回结果为“Mountain BikeMountain BikeMountain Bike”。</span><span class="sxs-lookup"><span data-stu-id="ca4df-129">The return result is "Mountain BikeMountain BikeMountain Bike".</span></span>  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 <span data-ttu-id="ca4df-130">以下示例将复制 **Name** 列中的值，复制次数为 **Times** 变量中的值。</span><span class="sxs-lookup"><span data-stu-id="ca4df-130">This example replicates values in the **Name** column by the value in the **Times** variable.</span></span> <span data-ttu-id="ca4df-131">如果 **Times** 为 3， **Name** 为 Touring Front Wheel，则返回结果为 Touring Front WheelTouring Front WheelTouring Front Wheel。</span><span class="sxs-lookup"><span data-stu-id="ca4df-131">If **Times** is 3 and **Name** is Touring Front Wheel, the return result is Touring Front WheelTouring Front WheelTouring Front Wheel.</span></span>  
  
```  
REPLICATE(Name, @Times)  
```  
  
 <span data-ttu-id="ca4df-132">以下示例将复制 **Name** 变量中的值，复制次数为 **Times** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="ca4df-132">This example replicates the value in the **Name** variable by the value in the **Times** column.</span></span> <span data-ttu-id="ca4df-133">**Times** 是非整数数据类型，而表达式包含了一个到整数数据类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="ca4df-133">**Times** has a non-integer data type and the expression includes an explicit cast to an integer data type.</span></span> <span data-ttu-id="ca4df-134">如果 **Name** 包含 Helmet， **Times** 为 2，则返回结果为“HelmetHelmet”。</span><span class="sxs-lookup"><span data-stu-id="ca4df-134">If **Name** contains Helmet and **Times** is 2, the return result is "HelmetHelmet".</span></span>  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca4df-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca4df-135">See Also</span></span>  
 [<span data-ttu-id="ca4df-136">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="ca4df-136">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
