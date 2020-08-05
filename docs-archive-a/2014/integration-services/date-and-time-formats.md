---
title: 日期和时间格式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e6c461c0cfed6a776875831a46c94c70d895ba3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578966"
---
# <a name="date-and-time-formats"></a><span data-ttu-id="2df41-102">日期和时间格式</span><span class="sxs-lookup"><span data-stu-id="2df41-102">Date and Time Formats</span></span>
  <span data-ttu-id="2df41-103">快速分析提供一组快速、简单的数据分析例程。</span><span class="sxs-lookup"><span data-stu-id="2df41-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="2df41-104">快速分析支持下列日期和时间数据类型格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-104">Fast parse supports the following formats for date and time data types.</span></span>  
  
## <a name="date-data-types"></a><span data-ttu-id="2df41-105">日期数据类型</span><span class="sxs-lookup"><span data-stu-id="2df41-105">Date Data Types</span></span>  
 <span data-ttu-id="2df41-106">快速分析支持日期数据的下列字符串格式：</span><span class="sxs-lookup"><span data-stu-id="2df41-106">Fast parse supports the following string formats for date data:</span></span>  
  
-   <span data-ttu-id="2df41-107">包含前导空格的日期格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-107">Date formats that include leading white spaces.</span></span> <span data-ttu-id="2df41-108">例如，值“2004- 02-03”有效。</span><span class="sxs-lookup"><span data-stu-id="2df41-108">For example, the value " 2004- 02-03" is valid.</span></span>  
  
-   <span data-ttu-id="2df41-109">ISO 8601 格式，如下表中所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-109">ISO 8601 formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="2df41-110">格式</span><span class="sxs-lookup"><span data-stu-id="2df41-110">Format</span></span>|<span data-ttu-id="2df41-111">说明</span><span class="sxs-lookup"><span data-stu-id="2df41-111">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="2df41-112">YYYYMMDD</span><span class="sxs-lookup"><span data-stu-id="2df41-112">YYYYMMDD</span></span><br /><br /> <span data-ttu-id="2df41-113">YYYY-MM-DD</span><span class="sxs-lookup"><span data-stu-id="2df41-113">YYYY-MM-DD</span></span>|<span data-ttu-id="2df41-114">用四位数表示年、两位数表示月和两位数表示日的基本和扩展格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-114">Basic and extended formats for a four-digit year, a two-digit month, and a two-digit day.</span></span> <span data-ttu-id="2df41-115">在扩展格式中，日期部分以连字符 (-) 分隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-115">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="2df41-116">YYYY-MM</span><span class="sxs-lookup"><span data-stu-id="2df41-116">YYYY-MM</span></span>|<span data-ttu-id="2df41-117">用四位数表示年和两位数表示月的基本和扩展简化精度格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-117">Basic and extended reduced precision formats for a four-digit year and a two-digit month.</span></span> <span data-ttu-id="2df41-118">在扩展格式中，日期部分以连字符 (-) 分隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-118">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="2df41-119">YYYY</span><span class="sxs-lookup"><span data-stu-id="2df41-119">YYYY</span></span>|<span data-ttu-id="2df41-120">用四位数表示年的简化精度格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-120">Reduced precision format is a four-digit year.</span></span>|  
  
 <span data-ttu-id="2df41-121">快速分析不支持日期数据的下列格式：</span><span class="sxs-lookup"><span data-stu-id="2df41-121">Fast parse does not support the following formats for date data:</span></span>  
  
-   <span data-ttu-id="2df41-122">用字母表示的月份值。</span><span class="sxs-lookup"><span data-stu-id="2df41-122">Alphabetical month values.</span></span> <span data-ttu-id="2df41-123">例如，日期格式 Oct-31-2003 无效。</span><span class="sxs-lookup"><span data-stu-id="2df41-123">For example, the date format Oct-31-2003 is not valid.</span></span>  
  
-   <span data-ttu-id="2df41-124">不明确的格式，如 DD-MM-YYYY 和 MM-DD-YYYY。</span><span class="sxs-lookup"><span data-stu-id="2df41-124">Ambiguous formats such as DD-MM-YYYY and MM-DD-YYYY.</span></span> <span data-ttu-id="2df41-125">例如，日期 03-04-1995 和 04-03-1995 都无效。</span><span class="sxs-lookup"><span data-stu-id="2df41-125">For example, the dates 03-04-1995 and 04-03-1995 are not valid.</span></span>  
  
-   <span data-ttu-id="2df41-126">用四位数表示日历年和三位数表示一年中的第几天的基本和扩展截断格式，YYYYDDD 和 YYYY-DDD。</span><span class="sxs-lookup"><span data-stu-id="2df41-126">Basic and extended truncated formats for a four-digit calendar year and a three-digit day within a year, YYYYDDD and YYYY-DDD.</span></span>  
  
-   <span data-ttu-id="2df41-127">用四位数表示年、用两位数表示一年中第几周和一位数表示一周中星期几的基本和扩展格式，YYYYWwwD 和 YYYY-Www-D。</span><span class="sxs-lookup"><span data-stu-id="2df41-127">Basic and extended formats for a four-digit year, a two-digit number for the week of the year, and a one-digit number for the day of the week, YYYYWwwD and YYYY-Www-D</span></span>  
  
-   <span data-ttu-id="2df41-128">年和周日期的基本与扩展截断格式是用四位数表示年和两位数表示周，YYYWww 和 YYYY-Www。</span><span class="sxs-lookup"><span data-stu-id="2df41-128">Basic and extended truncated formats for a year and week date are a four-digit year and a two-digit number for the week, YYYWww and YYYY-Www</span></span>  
  
 <span data-ttu-id="2df41-129">快速分析将数据输出为 DT_DBDATE。</span><span class="sxs-lookup"><span data-stu-id="2df41-129">Fast parse outputs the data as DT_DBDATE.</span></span> <span data-ttu-id="2df41-130">对截断格式的日期值进行填充。</span><span class="sxs-lookup"><span data-stu-id="2df41-130">Date values in truncated formats are padded.</span></span> <span data-ttu-id="2df41-131">例如，YYYY 变为 YYYY0101。</span><span class="sxs-lookup"><span data-stu-id="2df41-131">For example, YYYY becomes YYYY0101.</span></span>  
  
 <span data-ttu-id="2df41-132">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2df41-132">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="time-data-type"></a><span data-ttu-id="2df41-133">时间数据类型</span><span class="sxs-lookup"><span data-stu-id="2df41-133">Time Data Type</span></span>  
 <span data-ttu-id="2df41-134">快速分析支持时间数据的下列字符串格式：</span><span class="sxs-lookup"><span data-stu-id="2df41-134">Fast parse supports the following string formats for time data:</span></span>  
  
-   <span data-ttu-id="2df41-135">包含前导空格的时间格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-135">Time formats that include leading white spaces.</span></span> <span data-ttu-id="2df41-136">例如，值“ 10:24”有效。</span><span class="sxs-lookup"><span data-stu-id="2df41-136">For example, the value " 10:24" is valid.</span></span>  
  
-   <span data-ttu-id="2df41-137">24 小时制格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-137">24-hour format.</span></span> <span data-ttu-id="2df41-138">快速分析不支持 AM 和 PM 表示法。</span><span class="sxs-lookup"><span data-stu-id="2df41-138">Fast parse does not support the AM and PM notation.</span></span>  
  
-   <span data-ttu-id="2df41-139">ISO 8601 时间格式，如下表中所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-139">ISO 8601 time formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="2df41-140">格式</span><span class="sxs-lookup"><span data-stu-id="2df41-140">Format</span></span>|<span data-ttu-id="2df41-141">说明</span><span class="sxs-lookup"><span data-stu-id="2df41-141">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="2df41-142">HHMISS</span><span class="sxs-lookup"><span data-stu-id="2df41-142">HHMISS</span></span><br /><br /> <span data-ttu-id="2df41-143">HH:MI:SS</span><span class="sxs-lookup"><span data-stu-id="2df41-143">HH:MI:SS</span></span>|<span data-ttu-id="2df41-144">用两位数表示小时、两位数表示分钟和两位数表示秒的基本和扩展格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-144">Basic and extended formats for a two-digit hour, a two-digit minute, and a two-digit second.</span></span> <span data-ttu-id="2df41-145">在扩展格式中，时间部分以冒号 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-145">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="2df41-146">HHMI</span><span class="sxs-lookup"><span data-stu-id="2df41-146">HHMI</span></span><br /><br /> <span data-ttu-id="2df41-147">HH:MI</span><span class="sxs-lookup"><span data-stu-id="2df41-147">HH:MI</span></span>|<span data-ttu-id="2df41-148">用两位数表示小时和两位数表示分钟的基本和扩展截断格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-148">Basic and extended truncated format for a two-digit hour and a two-digit minute.</span></span> <span data-ttu-id="2df41-149">在扩展格式中，时间部分以冒号 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-149">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="2df41-150">HH</span><span class="sxs-lookup"><span data-stu-id="2df41-150">HH</span></span>|<span data-ttu-id="2df41-151">用两位数表示小时的截断格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-151">Truncated format for a two-digit hour.</span></span>|  
    |<span data-ttu-id="2df41-152">00:00:00</span><span class="sxs-lookup"><span data-stu-id="2df41-152">00:00:00</span></span><br /><br /> <span data-ttu-id="2df41-153">000000</span><span class="sxs-lookup"><span data-stu-id="2df41-153">000000</span></span><br /><br /> <span data-ttu-id="2df41-154">0000</span><span class="sxs-lookup"><span data-stu-id="2df41-154">0000</span></span><br /><br /> <span data-ttu-id="2df41-155">00</span><span class="sxs-lookup"><span data-stu-id="2df41-155">00</span></span><br /><br /> <span data-ttu-id="2df41-156">240000</span><span class="sxs-lookup"><span data-stu-id="2df41-156">240000</span></span><br /><br /> <span data-ttu-id="2df41-157">24:00:00</span><span class="sxs-lookup"><span data-stu-id="2df41-157">24:00:00</span></span><br /><br /> <span data-ttu-id="2df41-158">2400</span><span class="sxs-lookup"><span data-stu-id="2df41-158">2400</span></span><br /><br /> <span data-ttu-id="2df41-159">24</span><span class="sxs-lookup"><span data-stu-id="2df41-159">24</span></span>|<span data-ttu-id="2df41-160">午夜的格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-160">The format for midnight.</span></span>|  
  
-   <span data-ttu-id="2df41-161">指定时区的时间格式，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-161">Time formats that specify a time zone, as listed in the following table:.</span></span>  
  
    |<span data-ttu-id="2df41-162">格式</span><span class="sxs-lookup"><span data-stu-id="2df41-162">Format</span></span>|<span data-ttu-id="2df41-163">说明</span><span class="sxs-lookup"><span data-stu-id="2df41-163">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="2df41-164">+HH:MI</span><span class="sxs-lookup"><span data-stu-id="2df41-164">+HH:MI</span></span><br /><br /> <span data-ttu-id="2df41-165">+HHMI</span><span class="sxs-lookup"><span data-stu-id="2df41-165">+HHMI</span></span>|<span data-ttu-id="2df41-166">指示为得出本地时间而在协调世界时 (UTC) 基础上加上的小时和分钟数的基本和扩展格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-166">Basic and extended formats that indicate the number of hours and minutes that are added to Coordinated Universal Time (UTC) to obtain the local time.</span></span>|  
    |<span data-ttu-id="2df41-167">-HH:MI</span><span class="sxs-lookup"><span data-stu-id="2df41-167">-HH:MI</span></span><br /><br /> <span data-ttu-id="2df41-168">-HHMI</span><span class="sxs-lookup"><span data-stu-id="2df41-168">-HHMI</span></span>|<span data-ttu-id="2df41-169">指示为得出本地时间而从 UTC 减去的小时和分钟数的基本和扩展格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-169">Basic and extended formats that indicate the number of hours and minutes that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="2df41-170">+HH</span><span class="sxs-lookup"><span data-stu-id="2df41-170">+HH</span></span>|<span data-ttu-id="2df41-171">指示为得出本地时间而在 UTC 基础上加上的小时数的截断格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-171">Truncated format that indicates the number of hours that are added to UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="2df41-172">-HH</span><span class="sxs-lookup"><span data-stu-id="2df41-172">-HH</span></span>|<span data-ttu-id="2df41-173">指示为得出本地时间而从 UTC 减去的小时数的截断格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-173">Truncated format that indicates the number of hours that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="2df41-174">Z</span><span class="sxs-lookup"><span data-stu-id="2df41-174">Z</span></span>|<span data-ttu-id="2df41-175">值为 0 表示采用 UTC 表示时间。</span><span class="sxs-lookup"><span data-stu-id="2df41-175">A value of 0 that indicates the time is represented in UTC.</span></span>|  
  
     <span data-ttu-id="2df41-176">所有时间和日期/时间数据的格式都可以包括时区元素。</span><span class="sxs-lookup"><span data-stu-id="2df41-176">The formats for all time and date/time data can include a time zone element.</span></span> <span data-ttu-id="2df41-177">不过，如果数据的类型不是 DT_DBTIMESTAMPOFFSET，系统将忽略该时区值。</span><span class="sxs-lookup"><span data-stu-id="2df41-177">However, the system ignores the time zone value except when the data is of type DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="2df41-178">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2df41-178">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
     <span data-ttu-id="2df41-179">在包括时区元素的格式中，时间元素和时区元素之间没有空格，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-179">In formats that include a time zone element, there is no space between the time element and the time zone element, as shown in the following example:</span></span>  
  
     <span data-ttu-id="2df41-180">HH:MI:SS[+HH:MI]</span><span class="sxs-lookup"><span data-stu-id="2df41-180">HH:MI:SS[+HH:MI]</span></span>  
  
     <span data-ttu-id="2df41-181">上例中的括号表明时区值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2df41-181">The brackets in the previous example indicate that the time zone value is optional.</span></span>  
  
-   <span data-ttu-id="2df41-182">包含小数的时间格式，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-182">Time formats that include a decimal fraction, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="2df41-183">格式</span><span class="sxs-lookup"><span data-stu-id="2df41-183">Format</span></span>|<span data-ttu-id="2df41-184">说明</span><span class="sxs-lookup"><span data-stu-id="2df41-184">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="2df41-185">HH[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="2df41-185">HH[.nnnnnnn]</span></span>|<span data-ttu-id="2df41-186">n 是介于 0 和 9999999 之间的值，表示小时的小数部分。</span><span class="sxs-lookup"><span data-stu-id="2df41-186">n is a value between 0 and 9999999 that represents a fraction of hours.</span></span> <span data-ttu-id="2df41-187">方括号表明该值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2df41-187">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="2df41-188">例如，值 12.750 表示 12:45。</span><span class="sxs-lookup"><span data-stu-id="2df41-188">For example, the value 12.750 indicates 12:45.</span></span>|  
    |<span data-ttu-id="2df41-189">HHMI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="2df41-189">HHMI[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="2df41-190">HH:MI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="2df41-190">HH:MI[.nnnnnnn]</span></span>|<span data-ttu-id="2df41-191">n 是介于 0 和 9999999 之间的值，表示分钟的小数部分。</span><span class="sxs-lookup"><span data-stu-id="2df41-191">n is a value between 0 and 9999999 that represents a fraction of minutes.</span></span> <span data-ttu-id="2df41-192">方括号表明该值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2df41-192">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="2df41-193">例如，值 1220.500 表示 12:20:30。</span><span class="sxs-lookup"><span data-stu-id="2df41-193">For example, the value 1220.500 indicates 12:20:30.</span></span>|  
    |<span data-ttu-id="2df41-194">HHMISS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="2df41-194">HHMISS[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="2df41-195">HH:MI:SS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="2df41-195">HH:MI:SS[.nnnnnnn]</span></span>|<span data-ttu-id="2df41-196">n 是介于 0 和 9999999 之间的值，表示秒的小数部分。</span><span class="sxs-lookup"><span data-stu-id="2df41-196">n is a value between 0 and 9999999 that represents a fraction of seconds.</span></span> <span data-ttu-id="2df41-197">方括号表明该值是可选的。</span><span class="sxs-lookup"><span data-stu-id="2df41-197">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="2df41-198">例如，值 122040.250 表示 12:20:40.15。</span><span class="sxs-lookup"><span data-stu-id="2df41-198">For example, the value 122040.250 indicates 12:20:40.15.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="2df41-199">上表中时间格式的小数分隔符可以是小数点或逗号。</span><span class="sxs-lookup"><span data-stu-id="2df41-199">The fraction separator for the time formats in the previous table can be a decimal or a comma.</span></span>  
  
-   <span data-ttu-id="2df41-200">包括闰秒的时间值，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="2df41-200">Time values that include a leap second, as shown in the following examples:</span></span>  
  
     <span data-ttu-id="2df41-201">23:59:60[.0000000]</span><span class="sxs-lookup"><span data-stu-id="2df41-201">23:59:60[.0000000]</span></span>  
  
     <span data-ttu-id="2df41-202">235960[.0000000]</span><span class="sxs-lookup"><span data-stu-id="2df41-202">235960[.0000000]</span></span>  
  
 <span data-ttu-id="2df41-203">快速分析将字符串输出为 DT_DBTIME 和 DT_DBTIME2。</span><span class="sxs-lookup"><span data-stu-id="2df41-203">Fast parse outputs the strings as DT_DBTIME and DT_DBTIME2.</span></span> <span data-ttu-id="2df41-204">对截断格式的时间值进行填充。</span><span class="sxs-lookup"><span data-stu-id="2df41-204">Time values in truncated formats are padded.</span></span> <span data-ttu-id="2df41-205">例如，HH:MI 变为 HH:MM:00.000。</span><span class="sxs-lookup"><span data-stu-id="2df41-205">For example, HH:MI becomes HH:MM:00.000.</span></span>  
  
 <span data-ttu-id="2df41-206">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2df41-206">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="datetime-data-type"></a><span data-ttu-id="2df41-207">日期/时间数据类型</span><span class="sxs-lookup"><span data-stu-id="2df41-207">Date/Time Data Type</span></span>  
 <span data-ttu-id="2df41-208">快速分析支持日期/时间数据的下列字符串格式：</span><span class="sxs-lookup"><span data-stu-id="2df41-208">Fast parse supports the following string formats for date/time data:</span></span>  
  
-   <span data-ttu-id="2df41-209">包含前导空格的格式。</span><span class="sxs-lookup"><span data-stu-id="2df41-209">Formats that include leading white spaces.</span></span> <span data-ttu-id="2df41-210">例如，值“  2003-01-10T203910”有效。</span><span class="sxs-lookup"><span data-stu-id="2df41-210">For example, the value "  2003-01-10T203910" is valid.</span></span>  
  
-   <span data-ttu-id="2df41-211">以大写字母 T 分隔的有效日期格式与有效时间格式以及有效时区格式的组合，例如 YYYYMMDDT[HHMISS][+HH:MI]。</span><span class="sxs-lookup"><span data-stu-id="2df41-211">Combinations of valid date formats and valid time formats separated by an uppercase T, and valid time zone formats, such as YYYYMMDDT[HHMISS][+HH:MI].</span></span> <span data-ttu-id="2df41-212">时间和时区值不是必需的。</span><span class="sxs-lookup"><span data-stu-id="2df41-212">The time and time zone values are not required.</span></span> <span data-ttu-id="2df41-213">例如，“2003-10-14”有效。</span><span class="sxs-lookup"><span data-stu-id="2df41-213">For example, "2003-10-14" is valid.</span></span>  
  
 <span data-ttu-id="2df41-214">快速分析不支持时间间隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-214">Fast parse does not support time intervals.</span></span> <span data-ttu-id="2df41-215">例如，无法分析起始和结束日期和时间以 YYYYMMDDThhmmss/YYYYMMDDThhmmss 格式标识的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="2df41-215">For example, a time interval identified by a start and end date and time in the format YYYYMMDDThhmmss/YYYYMMDDThhmmss cannot be parsed.</span></span>  
  
 <span data-ttu-id="2df41-216">快速分析将字符串输出为 DT_DATE、DT_DBTIMESTAMP、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET。</span><span class="sxs-lookup"><span data-stu-id="2df41-216">Fast parse outputs the strings as DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="2df41-217">对截断格式的日期/时间值进行填充。</span><span class="sxs-lookup"><span data-stu-id="2df41-217">Date/time values in truncated formats are padded.</span></span> <span data-ttu-id="2df41-218">下表列出为缺少的日期和时间部分添加的值。</span><span class="sxs-lookup"><span data-stu-id="2df41-218">The following table lists the values that are added for missing date and time parts.</span></span>  
  
|<span data-ttu-id="2df41-219">日期/时间部分</span><span class="sxs-lookup"><span data-stu-id="2df41-219">Date/Time part</span></span>|<span data-ttu-id="2df41-220">填充</span><span class="sxs-lookup"><span data-stu-id="2df41-220">Padding</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="2df41-221">秒</span><span class="sxs-lookup"><span data-stu-id="2df41-221">Seconds</span></span>|<span data-ttu-id="2df41-222">添加 00。</span><span class="sxs-lookup"><span data-stu-id="2df41-222">Add 00.</span></span>|  
|<span data-ttu-id="2df41-223">分钟数</span><span class="sxs-lookup"><span data-stu-id="2df41-223">Minutes</span></span>|<span data-ttu-id="2df41-224">添加 00:00。</span><span class="sxs-lookup"><span data-stu-id="2df41-224">Add 00:00.</span></span>|  
|<span data-ttu-id="2df41-225">小时</span><span class="sxs-lookup"><span data-stu-id="2df41-225">Hour</span></span>|<span data-ttu-id="2df41-226">添加 00:00:00。</span><span class="sxs-lookup"><span data-stu-id="2df41-226">Add 00:00:00.</span></span>|  
|<span data-ttu-id="2df41-227">天</span><span class="sxs-lookup"><span data-stu-id="2df41-227">Day</span></span>|<span data-ttu-id="2df41-228">添加 01，表示一个月中的第几天。</span><span class="sxs-lookup"><span data-stu-id="2df41-228">Add 01 for the day of the month.</span></span>|  
|<span data-ttu-id="2df41-229">月份</span><span class="sxs-lookup"><span data-stu-id="2df41-229">Month</span></span>|<span data-ttu-id="2df41-230">添加 01，表示一年中的第几个月。</span><span class="sxs-lookup"><span data-stu-id="2df41-230">Add 01 for the month of the year.</span></span>|  
  
 <span data-ttu-id="2df41-231">有关详细信息，请参阅 [Integration Services 数据类型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2df41-231">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
  
