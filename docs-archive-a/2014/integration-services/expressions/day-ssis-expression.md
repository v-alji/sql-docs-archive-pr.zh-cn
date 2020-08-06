---
title: DAY（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b7acac3f3949cbbd07adbe6382ea3d875f94cb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689530"
---
# <a name="day-ssis-expression"></a><span data-ttu-id="626e2-102">DAY（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="626e2-102">DAY (SSIS Expression)</span></span>
  <span data-ttu-id="626e2-103">返回一个整数，表示日期的“日”日期部分。</span><span class="sxs-lookup"><span data-stu-id="626e2-103">Returns an integer that represents the day datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="626e2-104">语法</span><span class="sxs-lookup"><span data-stu-id="626e2-104">Syntax</span></span>  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="626e2-105">参数</span><span class="sxs-lookup"><span data-stu-id="626e2-105">Arguments</span></span>  
 <span data-ttu-id="626e2-106">*date*</span><span class="sxs-lookup"><span data-stu-id="626e2-106">*date*</span></span>  
 <span data-ttu-id="626e2-107">返回有效日期或日期格式的字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="626e2-107">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="626e2-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="626e2-108">Result Types</span></span>  
 <span data-ttu-id="626e2-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="626e2-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="626e2-110">备注</span><span class="sxs-lookup"><span data-stu-id="626e2-110">Remarks</span></span>  
 <span data-ttu-id="626e2-111">如果参数为空，则 DAY 将返回空结果。</span><span class="sxs-lookup"><span data-stu-id="626e2-111">DAY returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="626e2-112">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="626e2-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="626e2-113">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="626e2-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="626e2-114">在日期文本显式转换为以下日期数据类型之一时，表达式验证失败：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="626e2-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="626e2-115">与 DATEPART("Day", date) 相比，DAY 函数效果相同，但更简洁。</span><span class="sxs-lookup"><span data-stu-id="626e2-115">Using the DAY function is briefer but equivalent to using DATEPART("Day", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="626e2-116">表达式示例</span><span class="sxs-lookup"><span data-stu-id="626e2-116">Expression Examples</span></span>  
 <span data-ttu-id="626e2-117">以下示例返回日期文字中的日期数字。</span><span class="sxs-lookup"><span data-stu-id="626e2-117">This example returns the number of the day in a date literal.</span></span> <span data-ttu-id="626e2-118">如果日期格式是“mm/dd/yyyy”格式，则此示例将返回 23。</span><span class="sxs-lookup"><span data-stu-id="626e2-118">If the date format is in "mm/dd/yyyy" format, this example returns 23.</span></span>  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="626e2-119">此示例返回 **ModifiedDate** 列中表示天的整数。</span><span class="sxs-lookup"><span data-stu-id="626e2-119">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DAY(ModifiedDate)  
```  
  
 <span data-ttu-id="626e2-120">以下示例返回表示当前日期的“日”部分的整数。</span><span class="sxs-lookup"><span data-stu-id="626e2-120">This example returns the integer that represents the day of the current date.</span></span>  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="626e2-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="626e2-121">See Also</span></span>  
 <span data-ttu-id="626e2-122">[DATEADD（SSIS 表达式）](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="626e2-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="626e2-123">[DATEDIFF（SSIS 表达式）](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="626e2-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="626e2-124">[DATEPART（SSIS 表达式）](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="626e2-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="626e2-125">[MONTH（SSIS 表达式）](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="626e2-125">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="626e2-126">[YEAR（SSIS 表达式）](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="626e2-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="626e2-127">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="626e2-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
