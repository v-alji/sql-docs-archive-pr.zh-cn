---
title: LEFT（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f21d134988414c7d8579d720877feec45383270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589762"
---
# <a name="left-ssis-expression"></a><span data-ttu-id="733b9-102">LEFT（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="733b9-102">LEFT (SSIS Expression)</span></span>
  <span data-ttu-id="733b9-103">返回从给定字符表达式最左侧开始的指定数量的字符。</span><span class="sxs-lookup"><span data-stu-id="733b9-103">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733b9-104">语法</span><span class="sxs-lookup"><span data-stu-id="733b9-104">Syntax</span></span>  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a><span data-ttu-id="733b9-105">参数</span><span class="sxs-lookup"><span data-stu-id="733b9-105">Arguments</span></span>  
 <span data-ttu-id="733b9-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="733b9-106">*character_expression*</span></span>  
 <span data-ttu-id="733b9-107">是从中提取字符的字符表达式。</span><span class="sxs-lookup"><span data-stu-id="733b9-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="733b9-108">*数字*</span><span class="sxs-lookup"><span data-stu-id="733b9-108">*number*</span></span>  
 <span data-ttu-id="733b9-109">指示要返回的字符数的整数表达式。</span><span class="sxs-lookup"><span data-stu-id="733b9-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="733b9-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="733b9-110">Result Types</span></span>  
 <span data-ttu-id="733b9-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="733b9-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="733b9-112">备注</span><span class="sxs-lookup"><span data-stu-id="733b9-112">Remarks</span></span>  
 <span data-ttu-id="733b9-113">如果 *number* 大于 *character_expression*的长度，则该函数将返回 *character_expression*。</span><span class="sxs-lookup"><span data-stu-id="733b9-113">If *number* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="733b9-114">如果 *number* 为 0，则该函数返回零长度的字符串。</span><span class="sxs-lookup"><span data-stu-id="733b9-114">If *number* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="733b9-115">如果 *number* 为负数，则该函数返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="733b9-115">If *number* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="733b9-116">*number* 参数可使用变量和列。</span><span class="sxs-lookup"><span data-stu-id="733b9-116">The *number* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="733b9-117">LEFT 只可用于 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="733b9-117">LEFT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="733b9-118">如果 *character_expression* 参数是字符串文字或数据类型为 DT_STR 的数据列，则在 LEFT 执行操作前将隐式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="733b9-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LEFT performs its operation.</span></span> <span data-ttu-id="733b9-119">其他数据类型必须显式转换为 DT_WSTR 数据类型。</span><span class="sxs-lookup"><span data-stu-id="733b9-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="733b9-120">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)和[转换（SSIS 表达式）](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="733b9-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="733b9-121">如果任一参数为 Null ，则 LEFT 返回的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="733b9-121">LEFT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="733b9-122">表达式示例</span><span class="sxs-lookup"><span data-stu-id="733b9-122">Expression Examples</span></span>  
 <span data-ttu-id="733b9-123">以下示例使用字符串文字。</span><span class="sxs-lookup"><span data-stu-id="733b9-123">The following example uses a string literal.</span></span> <span data-ttu-id="733b9-124">返回结果为 `"Mountain"`。</span><span class="sxs-lookup"><span data-stu-id="733b9-124">The return result is `"Mountain"`.</span></span>  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a><span data-ttu-id="733b9-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="733b9-125">See Also</span></span>  
 <span data-ttu-id="733b9-126">[RIGHT（SSIS 表达式）](right-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="733b9-126">[RIGHT &#40;SSIS Expression&#41;](right-ssis-expression.md) </span></span>  
 [<span data-ttu-id="733b9-127">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="733b9-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
