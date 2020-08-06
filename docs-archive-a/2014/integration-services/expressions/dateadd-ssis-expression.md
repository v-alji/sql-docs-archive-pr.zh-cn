---
title: DATEADD（SSIS 表达式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9feb288318bdf9705928cb930f175f5c170c384e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691825"
---
# <a name="dateadd-ssis-expression"></a><span data-ttu-id="428ce-102">DATEADD（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="428ce-102">DATEADD (SSIS Expression)</span></span>
  <span data-ttu-id="428ce-103">将表示日期或时间间隔的数值与日期中指定的日期部分相加后，返回一个新的 DT_DBTIMESTAMP 值。</span><span class="sxs-lookup"><span data-stu-id="428ce-103">Returns a new DT_DBTIMESTAMP value after adding a number that represents a date or time interval to the specified datepart in a date.</span></span> <span data-ttu-id="428ce-104">number 参数的值必须为整数，而 date 参数的取值必须为有效日期。</span><span class="sxs-lookup"><span data-stu-id="428ce-104">The number parameter must evaluate to an integer, and the date parameter must evaluate to a valid date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428ce-105">语法</span><span class="sxs-lookup"><span data-stu-id="428ce-105">Syntax</span></span>  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="428ce-106">参数</span><span class="sxs-lookup"><span data-stu-id="428ce-106">Arguments</span></span>  
 <span data-ttu-id="428ce-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="428ce-107">*datepart*</span></span>  
 <span data-ttu-id="428ce-108">指定要与数值相加的日期部分的参数。</span><span class="sxs-lookup"><span data-stu-id="428ce-108">Is the parameter that specifies which part of the date to add a number to.</span></span>  
  
 <span data-ttu-id="428ce-109">*数字*</span><span class="sxs-lookup"><span data-stu-id="428ce-109">*number*</span></span>  
 <span data-ttu-id="428ce-110">用于与 datepart  相加的值。</span><span class="sxs-lookup"><span data-stu-id="428ce-110">Is the value used to increment *datepart*.</span></span> <span data-ttu-id="428ce-111">该值必须是分析表达式时已知的整数值。</span><span class="sxs-lookup"><span data-stu-id="428ce-111">The value must be an integer value that is known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="428ce-112">*date*</span><span class="sxs-lookup"><span data-stu-id="428ce-112">*date*</span></span>  
 <span data-ttu-id="428ce-113">返回有效日期或日期格式的字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="428ce-113">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="428ce-114">结果类型</span><span class="sxs-lookup"><span data-stu-id="428ce-114">Result Types</span></span>  
 <span data-ttu-id="428ce-115">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="428ce-115">DT_DBTIMESTAMP</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="428ce-116">备注</span><span class="sxs-lookup"><span data-stu-id="428ce-116">Remarks</span></span>  
 <span data-ttu-id="428ce-117">下表列出了表达式计算器可以识别的日期部分和缩写形式。</span><span class="sxs-lookup"><span data-stu-id="428ce-117">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="428ce-118">日期部分名称不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="428ce-118">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="428ce-119">datepart</span><span class="sxs-lookup"><span data-stu-id="428ce-119">Datepart</span></span>|<span data-ttu-id="428ce-120">缩写形式</span><span class="sxs-lookup"><span data-stu-id="428ce-120">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="428ce-121">年龄</span><span class="sxs-lookup"><span data-stu-id="428ce-121">Year</span></span>|<span data-ttu-id="428ce-122">yy、yyyy</span><span class="sxs-lookup"><span data-stu-id="428ce-122">yy, yyyy</span></span>|  
|<span data-ttu-id="428ce-123">季度</span><span class="sxs-lookup"><span data-stu-id="428ce-123">Quarter</span></span>|<span data-ttu-id="428ce-124">qq、q</span><span class="sxs-lookup"><span data-stu-id="428ce-124">qq, q</span></span>|  
|<span data-ttu-id="428ce-125">月份</span><span class="sxs-lookup"><span data-stu-id="428ce-125">Month</span></span>|<span data-ttu-id="428ce-126">mm、m</span><span class="sxs-lookup"><span data-stu-id="428ce-126">mm, m</span></span>|  
|<span data-ttu-id="428ce-127">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="428ce-127">Dayofyear</span></span>|<span data-ttu-id="428ce-128">dy、y</span><span class="sxs-lookup"><span data-stu-id="428ce-128">dy, y</span></span>|  
|<span data-ttu-id="428ce-129">日期</span><span class="sxs-lookup"><span data-stu-id="428ce-129">Day</span></span>|<span data-ttu-id="428ce-130">dd、d</span><span class="sxs-lookup"><span data-stu-id="428ce-130">dd, d</span></span>|  
|<span data-ttu-id="428ce-131">Week</span><span class="sxs-lookup"><span data-stu-id="428ce-131">Week</span></span>|<span data-ttu-id="428ce-132">wk、ww</span><span class="sxs-lookup"><span data-stu-id="428ce-132">wk, ww</span></span>|  
|<span data-ttu-id="428ce-133">星期</span><span class="sxs-lookup"><span data-stu-id="428ce-133">Weekday</span></span>|<span data-ttu-id="428ce-134">dw、w</span><span class="sxs-lookup"><span data-stu-id="428ce-134">dw, w</span></span>|  
|<span data-ttu-id="428ce-135">Hour</span><span class="sxs-lookup"><span data-stu-id="428ce-135">Hour</span></span>|<span data-ttu-id="428ce-136">Hh</span><span class="sxs-lookup"><span data-stu-id="428ce-136">Hh</span></span>|  
|<span data-ttu-id="428ce-137">Minute</span><span class="sxs-lookup"><span data-stu-id="428ce-137">Minute</span></span>|<span data-ttu-id="428ce-138">mi、n</span><span class="sxs-lookup"><span data-stu-id="428ce-138">mi, n</span></span>|  
|<span data-ttu-id="428ce-139">秒</span><span class="sxs-lookup"><span data-stu-id="428ce-139">Second</span></span>|<span data-ttu-id="428ce-140">ss、s</span><span class="sxs-lookup"><span data-stu-id="428ce-140">ss, s</span></span>|  
|<span data-ttu-id="428ce-141">Millisecond</span><span class="sxs-lookup"><span data-stu-id="428ce-141">Millisecond</span></span>|<span data-ttu-id="428ce-142">Ms</span><span class="sxs-lookup"><span data-stu-id="428ce-142">Ms</span></span>|  
  
 <span data-ttu-id="428ce-143">分拆表达式时必须提供 *number* 参数。</span><span class="sxs-lookup"><span data-stu-id="428ce-143">The *number* argument must be available when the expression is parsed.</span></span> <span data-ttu-id="428ce-144">该参数可以是常量，也可以是变量。</span><span class="sxs-lookup"><span data-stu-id="428ce-144">The argument can be a constant or a variable.</span></span> <span data-ttu-id="428ce-145">由于分析表达式时列值是未知的，因此不能使用列值。</span><span class="sxs-lookup"><span data-stu-id="428ce-145">You cannot use column values because the values are not known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="428ce-146">*datepart* 参数必须用英文引号括起来。</span><span class="sxs-lookup"><span data-stu-id="428ce-146">The *datepart* argument must be enclosed by quotation marks.</span></span>  
  
 <span data-ttu-id="428ce-147">日期文字必须显式转换为日期数据类型之一。</span><span class="sxs-lookup"><span data-stu-id="428ce-147">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="428ce-148">有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="428ce-148">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="428ce-149">如果参数为空，则 DATEADD 返回空结果。</span><span class="sxs-lookup"><span data-stu-id="428ce-149">DATEADD returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="428ce-150">如果日期无效，日期或时间单元不是字符串，或者增量不是静态整数，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="428ce-150">Errors occur if a date is invalid, if the date or time unit is not a string, or if the increment is not a static integer.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="428ce-151">SSIS 表达式示例</span><span class="sxs-lookup"><span data-stu-id="428ce-151">SSIS Expression Examples</span></span>  
 <span data-ttu-id="428ce-152">以下示例将当前日期加上一个月。</span><span class="sxs-lookup"><span data-stu-id="428ce-152">This example adds one month to the current date.</span></span>  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 <span data-ttu-id="428ce-153">以下示例将 **ModifiedDate** 列中的日期加上 21 天。</span><span class="sxs-lookup"><span data-stu-id="428ce-153">This example adds 21 days to the dates in the **ModifiedDate** column.</span></span>  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 <span data-ttu-id="428ce-154">以下示例将文字日期加上 2 年。</span><span class="sxs-lookup"><span data-stu-id="428ce-154">This example adds 2 years to a literal date.</span></span>  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a><span data-ttu-id="428ce-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="428ce-155">See Also</span></span>  
 <span data-ttu-id="428ce-156">[DATEDIFF（SSIS 表达式）](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="428ce-156">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="428ce-157">[DATEPART（SSIS 表达式）](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="428ce-157">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="428ce-158">[DAY（SSIS 表达式）](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="428ce-158">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="428ce-159">[MONTH（SSIS 表达式）](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="428ce-159">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="428ce-160">[YEAR（SSIS 表达式）](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="428ce-160">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="428ce-161">函数（SSIS 表达式）</span><span class="sxs-lookup"><span data-stu-id="428ce-161">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
