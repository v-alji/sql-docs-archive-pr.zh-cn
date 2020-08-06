---
title: DATEPART（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aed7146c74c6738ba979f422bd65b7e1b539e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689532"
---
# <a name="datepart-ssis-expression"></a><span data-ttu-id="c96ef-102">DATEPART（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c96ef-102">DATEPART (SSIS Expression)</span></span>
  <span data-ttu-id="c96ef-103">返回一个表示日期的日期部分的整数。</span><span class="sxs-lookup"><span data-stu-id="c96ef-103">Returns an integer representing a datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96ef-104">语法</span><span class="sxs-lookup"><span data-stu-id="c96ef-104">Syntax</span></span>  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c96ef-105">参数</span><span class="sxs-lookup"><span data-stu-id="c96ef-105">Arguments</span></span>  
 <span data-ttu-id="c96ef-106">*datepart*</span><span class="sxs-lookup"><span data-stu-id="c96ef-106">*datepart*</span></span>  
 <span data-ttu-id="c96ef-107">此参数指定需要对日期中的哪一部分返回新值。</span><span class="sxs-lookup"><span data-stu-id="c96ef-107">Is the parameter that specifies for which part of the date to return a new value.</span></span>  
  
 <span data-ttu-id="c96ef-108">*date*</span><span class="sxs-lookup"><span data-stu-id="c96ef-108">*date*</span></span>  
 <span data-ttu-id="c96ef-109">返回有效日期或日期格式的字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="c96ef-109">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c96ef-110">结果类型</span><span class="sxs-lookup"><span data-stu-id="c96ef-110">Result Types</span></span>  
 <span data-ttu-id="c96ef-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="c96ef-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c96ef-112">备注</span><span class="sxs-lookup"><span data-stu-id="c96ef-112">Remarks</span></span>  
 <span data-ttu-id="c96ef-113">如果此参数为空，则 DATEPART 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="c96ef-113">DATEPART returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="c96ef-114">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="c96ef-114">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="c96ef-115">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c96ef-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="c96ef-116">下表列出了表达式计算器可以识别的日期部分和缩写形式。</span><span class="sxs-lookup"><span data-stu-id="c96ef-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="c96ef-117">日期部分名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c96ef-117">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="c96ef-118">datepart</span><span class="sxs-lookup"><span data-stu-id="c96ef-118">Datepart</span></span>|<span data-ttu-id="c96ef-119">缩写形式</span><span class="sxs-lookup"><span data-stu-id="c96ef-119">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="c96ef-120">年龄</span><span class="sxs-lookup"><span data-stu-id="c96ef-120">Year</span></span>|<span data-ttu-id="c96ef-121">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="c96ef-121">yy, yyyy</span></span>|  
|<span data-ttu-id="c96ef-122">季度</span><span class="sxs-lookup"><span data-stu-id="c96ef-122">Quarter</span></span>|<span data-ttu-id="c96ef-123">qq、q</span><span class="sxs-lookup"><span data-stu-id="c96ef-123">qq, q</span></span>|  
|<span data-ttu-id="c96ef-124">月份</span><span class="sxs-lookup"><span data-stu-id="c96ef-124">Month</span></span>|<span data-ttu-id="c96ef-125">mm、m</span><span class="sxs-lookup"><span data-stu-id="c96ef-125">mm, m</span></span>|  
|<span data-ttu-id="c96ef-126">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="c96ef-126">Dayofyear</span></span>|<span data-ttu-id="c96ef-127">dy、y</span><span class="sxs-lookup"><span data-stu-id="c96ef-127">dy, y</span></span>|  
|<span data-ttu-id="c96ef-128">日期</span><span class="sxs-lookup"><span data-stu-id="c96ef-128">Day</span></span>|<span data-ttu-id="c96ef-129">dd、d</span><span class="sxs-lookup"><span data-stu-id="c96ef-129">dd, d</span></span>|  
|<span data-ttu-id="c96ef-130">Week</span><span class="sxs-lookup"><span data-stu-id="c96ef-130">Week</span></span>|<span data-ttu-id="c96ef-131">wk、ww</span><span class="sxs-lookup"><span data-stu-id="c96ef-131">wk, ww</span></span>|  
|<span data-ttu-id="c96ef-132">星期</span><span class="sxs-lookup"><span data-stu-id="c96ef-132">Weekday</span></span>|<span data-ttu-id="c96ef-133">dw</span><span class="sxs-lookup"><span data-stu-id="c96ef-133">dw</span></span>|  
|<span data-ttu-id="c96ef-134">Hour</span><span class="sxs-lookup"><span data-stu-id="c96ef-134">Hour</span></span>|<span data-ttu-id="c96ef-135">Hh</span><span class="sxs-lookup"><span data-stu-id="c96ef-135">Hh</span></span>|  
|<span data-ttu-id="c96ef-136">Minute</span><span class="sxs-lookup"><span data-stu-id="c96ef-136">Minute</span></span>|<span data-ttu-id="c96ef-137">mi、n</span><span class="sxs-lookup"><span data-stu-id="c96ef-137">mi, n</span></span>|  
|<span data-ttu-id="c96ef-138">秒</span><span class="sxs-lookup"><span data-stu-id="c96ef-138">Second</span></span>|<span data-ttu-id="c96ef-139">ss、s</span><span class="sxs-lookup"><span data-stu-id="c96ef-139">ss, s</span></span>|  
|<span data-ttu-id="c96ef-140">Millisecond</span><span class="sxs-lookup"><span data-stu-id="c96ef-140">Millisecond</span></span>|<span data-ttu-id="c96ef-141">Ms</span><span class="sxs-lookup"><span data-stu-id="c96ef-141">Ms</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="c96ef-142">SSIS 表达式示例</span><span class="sxs-lookup"><span data-stu-id="c96ef-142">SSIS Expression Examples</span></span>  
 <span data-ttu-id="c96ef-143">此示例返回表示日期文字中的月的整数。</span><span class="sxs-lookup"><span data-stu-id="c96ef-143">This example returns the integer that represents the month in a date literal.</span></span> <span data-ttu-id="c96ef-144">如果日期是“mm/dd/yyyy”格式，则此示例返回 11。</span><span class="sxs-lookup"><span data-stu-id="c96ef-144">If the date is in mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 <span data-ttu-id="c96ef-145">此示例返回 **ModifiedDate** 列中表示天的整数。</span><span class="sxs-lookup"><span data-stu-id="c96ef-145">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 <span data-ttu-id="c96ef-146">此示例返回当前日期中表示年的整数。</span><span class="sxs-lookup"><span data-stu-id="c96ef-146">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="c96ef-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c96ef-147">See Also</span></span>  
 <span data-ttu-id="c96ef-148">[DATEADD（SSIS 表达式）](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c96ef-148">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="c96ef-149">[DATEDIFF（SSIS 表达式）](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c96ef-149">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="c96ef-150">[DAY（SSIS 表达式）](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c96ef-150">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="c96ef-151">[MONTH（SSIS 表达式）](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c96ef-151">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="c96ef-152">[YEAR（SSIS 表达式）](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c96ef-152">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="c96ef-153">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="c96ef-153">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
