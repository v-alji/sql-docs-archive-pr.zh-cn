---
title: DATEDIFF（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33edf2a152f70bb8c5bbd1f69cb87354e099b246
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689534"
---
# <a name="datediff-ssis-expression"></a><span data-ttu-id="80e9b-102">DATEDIFF（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="80e9b-102">DATEDIFF (SSIS Expression)</span></span>
  <span data-ttu-id="80e9b-103">返回两个指定日期之间所跨的日期和时间边界的数目。</span><span class="sxs-lookup"><span data-stu-id="80e9b-103">Returns the number of date and time boundaries crossed between two specified dates.</span></span> <span data-ttu-id="80e9b-104">*datepart* 参数标识要比较的日期和时间边界。</span><span class="sxs-lookup"><span data-stu-id="80e9b-104">The *datepart* parameter identifies which date and time boundaries to compare.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e9b-105">语法</span><span class="sxs-lookup"><span data-stu-id="80e9b-105">Syntax</span></span>  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a><span data-ttu-id="80e9b-106">参数</span><span class="sxs-lookup"><span data-stu-id="80e9b-106">Arguments</span></span>  
 <span data-ttu-id="80e9b-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="80e9b-107">*datepart*</span></span>  
 <span data-ttu-id="80e9b-108">此参数指定对日期的哪一部分进行比较并为其返回值。</span><span class="sxs-lookup"><span data-stu-id="80e9b-108">Is the parameter that specifies which part of the date to compare and return a value for.</span></span>  
  
 <span data-ttu-id="80e9b-109">*startdate*</span><span class="sxs-lookup"><span data-stu-id="80e9b-109">*startdate*</span></span>  
 <span data-ttu-id="80e9b-110">此参数表示间隔的开始日期。</span><span class="sxs-lookup"><span data-stu-id="80e9b-110">Is the start date of the interval.</span></span>  
  
 <span data-ttu-id="80e9b-111">*endate*</span><span class="sxs-lookup"><span data-stu-id="80e9b-111">*endate*</span></span>  
 <span data-ttu-id="80e9b-112">此参数表示间隔的结束日期。</span><span class="sxs-lookup"><span data-stu-id="80e9b-112">Is the end date of the interval.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="80e9b-113">结果类型</span><span class="sxs-lookup"><span data-stu-id="80e9b-113">Result Types</span></span>  
 <span data-ttu-id="80e9b-114">DT_I4</span><span class="sxs-lookup"><span data-stu-id="80e9b-114">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e9b-115">备注</span><span class="sxs-lookup"><span data-stu-id="80e9b-115">Remarks</span></span>  
 <span data-ttu-id="80e9b-116">下表列出了表达式计算器可以识别的日期部分和缩写形式。</span><span class="sxs-lookup"><span data-stu-id="80e9b-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span>  
  
|<span data-ttu-id="80e9b-117">datepart</span><span class="sxs-lookup"><span data-stu-id="80e9b-117">Datepart</span></span>|<span data-ttu-id="80e9b-118">缩写形式</span><span class="sxs-lookup"><span data-stu-id="80e9b-118">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="80e9b-119">年龄</span><span class="sxs-lookup"><span data-stu-id="80e9b-119">Year</span></span>|<span data-ttu-id="80e9b-120">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="80e9b-120">yy, yyyy</span></span>|  
|<span data-ttu-id="80e9b-121">季度</span><span class="sxs-lookup"><span data-stu-id="80e9b-121">Quarter</span></span>|<span data-ttu-id="80e9b-122">qq、q</span><span class="sxs-lookup"><span data-stu-id="80e9b-122">qq, q</span></span>|  
|<span data-ttu-id="80e9b-123">月份</span><span class="sxs-lookup"><span data-stu-id="80e9b-123">Month</span></span>|<span data-ttu-id="80e9b-124">mm、m</span><span class="sxs-lookup"><span data-stu-id="80e9b-124">mm, m</span></span>|  
|<span data-ttu-id="80e9b-125">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="80e9b-125">Dayofyear</span></span>|<span data-ttu-id="80e9b-126">dy、y</span><span class="sxs-lookup"><span data-stu-id="80e9b-126">dy, y</span></span>|  
|<span data-ttu-id="80e9b-127">日期</span><span class="sxs-lookup"><span data-stu-id="80e9b-127">Day</span></span>|<span data-ttu-id="80e9b-128">dd、d</span><span class="sxs-lookup"><span data-stu-id="80e9b-128">dd, d</span></span>|  
|<span data-ttu-id="80e9b-129">Week</span><span class="sxs-lookup"><span data-stu-id="80e9b-129">Week</span></span>|<span data-ttu-id="80e9b-130">wk、ww</span><span class="sxs-lookup"><span data-stu-id="80e9b-130">wk, ww</span></span>|  
|<span data-ttu-id="80e9b-131">星期</span><span class="sxs-lookup"><span data-stu-id="80e9b-131">Weekday</span></span>|<span data-ttu-id="80e9b-132">dw、w</span><span class="sxs-lookup"><span data-stu-id="80e9b-132">dw, w</span></span>|  
|<span data-ttu-id="80e9b-133">Hour</span><span class="sxs-lookup"><span data-stu-id="80e9b-133">Hour</span></span>|<span data-ttu-id="80e9b-134">Hh</span><span class="sxs-lookup"><span data-stu-id="80e9b-134">Hh</span></span>|  
|<span data-ttu-id="80e9b-135">Minute</span><span class="sxs-lookup"><span data-stu-id="80e9b-135">Minute</span></span>|<span data-ttu-id="80e9b-136">mi、n</span><span class="sxs-lookup"><span data-stu-id="80e9b-136">mi, n</span></span>|  
|<span data-ttu-id="80e9b-137">秒</span><span class="sxs-lookup"><span data-stu-id="80e9b-137">Second</span></span>|<span data-ttu-id="80e9b-138">ss、s</span><span class="sxs-lookup"><span data-stu-id="80e9b-138">ss, s</span></span>|  
|<span data-ttu-id="80e9b-139">Millisecond</span><span class="sxs-lookup"><span data-stu-id="80e9b-139">Millisecond</span></span>|<span data-ttu-id="80e9b-140">Ms</span><span class="sxs-lookup"><span data-stu-id="80e9b-140">Ms</span></span>|  
  
 <span data-ttu-id="80e9b-141">如果任何参数为空，则 DATEDIFF 返回的结果为空。</span><span class="sxs-lookup"><span data-stu-id="80e9b-141">DATEDIFF returns a null result if any argument is null.</span></span>  
  
 <span data-ttu-id="80e9b-142">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="80e9b-142">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="80e9b-143">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="80e9b-143">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="80e9b-144">如果日期无效、日期或时间单元不是字符串、开始日期不是日期或结束日期不是日期，都将发生错误。</span><span class="sxs-lookup"><span data-stu-id="80e9b-144">An error occurs if a date is not valid, if the date or time unit is not a string, if the start date is not a date, or if the end date is not a date.</span></span>  
  
 <span data-ttu-id="80e9b-145">如果结束日期早于开始日期，则此函数返回负数。</span><span class="sxs-lookup"><span data-stu-id="80e9b-145">If the end date is earlier than the start date, the function returns a negative number.</span></span> <span data-ttu-id="80e9b-146">如果开始日期等于结束日期或两者在同一间隔内，则此函数返回零。</span><span class="sxs-lookup"><span data-stu-id="80e9b-146">If the start and end dates are equal or fall within the same interval, the function returns zero.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="80e9b-147">SSIS 表达式示例</span><span class="sxs-lookup"><span data-stu-id="80e9b-147">SSIS Expression Examples</span></span>  
 <span data-ttu-id="80e9b-148">此示例计算两个日期文字之间的天数。</span><span class="sxs-lookup"><span data-stu-id="80e9b-148">This example calculates the number of days between two date literals.</span></span> <span data-ttu-id="80e9b-149">如果日期是“mm/dd/yyyy”格式，此函数返回 7。</span><span class="sxs-lookup"><span data-stu-id="80e9b-149">If the date is in "mm/dd/yyyy" format, the function returns 7.</span></span>  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 <span data-ttu-id="80e9b-150">此示例返回一个日期文字与当前日期之间的月数。</span><span class="sxs-lookup"><span data-stu-id="80e9b-150">This example returns the number of months between a date literal and the current date.</span></span>  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 <span data-ttu-id="80e9b-151">此示例返回 **ModifiedDate** 列中的日期与 **YearEndDate** 变量之间的周数。</span><span class="sxs-lookup"><span data-stu-id="80e9b-151">This example returns the number of weeks between the date in the **ModifiedDate** column and the **YearEndDate** variable.</span></span> <span data-ttu-id="80e9b-152">如果**YearEndDate**的 `date` 数据类型为，则不需要显式强制转换。</span><span class="sxs-lookup"><span data-stu-id="80e9b-152">If **YearEndDate** has a `date` data type, no explicit casting is required.</span></span>  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a><span data-ttu-id="80e9b-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="80e9b-153">See Also</span></span>  
 <span data-ttu-id="80e9b-154">[DATEADD（SSIS 表达式）](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="80e9b-154">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="80e9b-155">[DATEPART（SSIS 表达式）](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="80e9b-155">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="80e9b-156">[DAY（SSIS 表达式）](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="80e9b-156">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="80e9b-157">[MONTH（SSIS 表达式）](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="80e9b-157">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="80e9b-158">[YEAR（SSIS 表达式）](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="80e9b-158">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="80e9b-159">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="80e9b-159">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
