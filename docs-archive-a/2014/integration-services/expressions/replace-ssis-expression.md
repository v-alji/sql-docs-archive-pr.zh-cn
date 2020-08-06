---
title: REPLACE（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e483ba6c9c72cb777f2955929a717c6c2e17a8c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689985"
---
# <a name="replace-ssis-expression"></a><span data-ttu-id="9d46f-102">REPLACE（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9d46f-102">REPLACE (SSIS Expression)</span></span>
  <span data-ttu-id="9d46f-103">将表达式中的一个字符串替换为另一个字符串或空字符串后，返回一个字符表达式。</span><span class="sxs-lookup"><span data-stu-id="9d46f-103">Returns a character expression after replacing a character string within the expression with either a different character string or an empty string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d46f-104">REPLACE 函数经常使用长字符串。</span><span class="sxs-lookup"><span data-stu-id="9d46f-104">The REPLACE function frequently uses long strings.</span></span> <span data-ttu-id="9d46f-105">可以适当处理截断的结果，否则会导致警告或错误。</span><span class="sxs-lookup"><span data-stu-id="9d46f-105">The consequences of truncation can be handled gracefully or cause a warning or an error.</span></span> <span data-ttu-id="9d46f-106">有关详细信息，请参阅[语法 (SSIS)](syntax-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="9d46f-106">For more information, see [Syntax &#40;SSIS&#41;](syntax-ssis.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d46f-107">语法</span><span class="sxs-lookup"><span data-stu-id="9d46f-107">Syntax</span></span>  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d46f-108">参数</span><span class="sxs-lookup"><span data-stu-id="9d46f-108">Arguments</span></span>  
 <span data-ttu-id="9d46f-109">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="9d46f-109">*character_expression*</span></span>  
 <span data-ttu-id="9d46f-110">是函数要搜索的有效字符表达式。</span><span class="sxs-lookup"><span data-stu-id="9d46f-110">Is a valid character expression that the function searches.</span></span>  
  
 <span data-ttu-id="9d46f-111">*searchstring*</span><span class="sxs-lookup"><span data-stu-id="9d46f-111">*searchstring*</span></span>  
 <span data-ttu-id="9d46f-112">是函数尝试定位的有效字符表达式。</span><span class="sxs-lookup"><span data-stu-id="9d46f-112">Is a valid character expression that the function attempts to locate.</span></span>  
  
 <span data-ttu-id="9d46f-113">*replacementstring*</span><span class="sxs-lookup"><span data-stu-id="9d46f-113">*replacementstring*</span></span>  
 <span data-ttu-id="9d46f-114">是用作替换表达式的有效字符表达式。</span><span class="sxs-lookup"><span data-stu-id="9d46f-114">Is a valid character expression that is the replacement expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9d46f-115">结果类型</span><span class="sxs-lookup"><span data-stu-id="9d46f-115">Result Types</span></span>  
 <span data-ttu-id="9d46f-116">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="9d46f-116">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d46f-117">备注</span><span class="sxs-lookup"><span data-stu-id="9d46f-117">Remarks</span></span>  
 <span data-ttu-id="9d46f-118">*searchstring* 的长度一定不能为零。</span><span class="sxs-lookup"><span data-stu-id="9d46f-118">The length of *searchstring* must not be zero.</span></span>  
  
 <span data-ttu-id="9d46f-119">*replacementstring* 的长度可以为零。</span><span class="sxs-lookup"><span data-stu-id="9d46f-119">The length of *replacementstring* may be zero.</span></span>  
  
 <span data-ttu-id="9d46f-120">*searchstring* 和 *replacementstring* 参数可以使用变量和列。</span><span class="sxs-lookup"><span data-stu-id="9d46f-120">The *searchstring* and *replacementstring* arguments can use variables and columns.</span></span>  
  
 <span data-ttu-id="9d46f-121">REPLACE 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d46f-121">REPLACE works only with the DT_WSTR data type.</span></span> <span data-ttu-id="9d46f-122">如果*character_expression1、character_expression2* 和 *character_expression3* 参数是字符串文字或数据类型为 DT_STR 的数据列，则它们在 REPLACE 执行操作前隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d46f-122">*character_expression1, character_expression2,* and *character_expression3* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before REPLACE performs its operation.</span></span> <span data-ttu-id="9d46f-123">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="9d46f-123">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="9d46f-124">有关详细信息，请参阅[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="9d46f-124">For more information, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="9d46f-125">如果任何参数值为空，则 REPLACE 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="9d46f-125">REPLACE returns a null result if any argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9d46f-126">表达式示例</span><span class="sxs-lookup"><span data-stu-id="9d46f-126">Expression Examples</span></span>  
 <span data-ttu-id="9d46f-127">此示例使用一个字符串文字。</span><span class="sxs-lookup"><span data-stu-id="9d46f-127">This example uses a string literal.</span></span> <span data-ttu-id="9d46f-128">返回结果为“All Terrain Bike”。</span><span class="sxs-lookup"><span data-stu-id="9d46f-128">The return result is "All Terrain Bike".</span></span>  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 <span data-ttu-id="9d46f-129">此示例删除 **Product** 列中的字符串“Bike”。</span><span class="sxs-lookup"><span data-stu-id="9d46f-129">This example removes the string "Bike" from the **Product** column.</span></span>  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 <span data-ttu-id="9d46f-130">此示例替换 **DaysToManufacture** 列中的值。</span><span class="sxs-lookup"><span data-stu-id="9d46f-130">This example replaces values in the **DaysToManufacture** column.</span></span> <span data-ttu-id="9d46f-131">该列具有整数数据类型，且表达式包含将 **DaysToManufacture** 转换为 DT_WSTR 数据类型的转换。</span><span class="sxs-lookup"><span data-stu-id="9d46f-131">The column has an integer data type and the expression includes casting **DaysToManufacture** to the DT_WSTR data type.</span></span>  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d46f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d46f-132">See Also</span></span>  
 <span data-ttu-id="9d46f-133">[SUBSTRING（SSIS 表达式）](substring-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9d46f-133">[SUBSTRING &#40;SSIS Expression&#41;](substring-ssis-expression.md) </span></span>  
 [<span data-ttu-id="9d46f-134">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="9d46f-134">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
