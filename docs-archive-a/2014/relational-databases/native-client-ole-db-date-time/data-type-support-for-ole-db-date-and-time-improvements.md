---
title: 针对 OLE DB 日期和时间改进的数据类型支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
author: rothja
ms.author: jroth
ms.openlocfilehash: 834583fdec63a8f613e623c239f9c3a1c9398950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692365"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a><span data-ttu-id="a08b7-102">针对 OLE DB 日期和时间改进的数据类型支持</span><span class="sxs-lookup"><span data-stu-id="a08b7-102">Data Type Support for OLE DB Date and Time Improvements</span></span>
  <span data-ttu-id="a08b7-103">本主题提供有关支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/时间数据类型的 OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) 类型的信息。</span><span class="sxs-lookup"><span data-stu-id="a08b7-103">This topic provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time data types.</span></span>  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="a08b7-104">行集和参数中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="a08b7-104">Data Type Mapping in Rowsets and Parameters</span></span>  
 <span data-ttu-id="a08b7-105">OLE DB 提供两种新数据类型来支持新服务器类型：DBTYPE_DBTIME2 和 DBTYPE_DBTIMESTAMPOFFSET。</span><span class="sxs-lookup"><span data-stu-id="a08b7-105">OLE DB provides two new data types to support the new server types: DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="a08b7-106">下表显示全部服务器类型映射：</span><span class="sxs-lookup"><span data-stu-id="a08b7-106">The following table shows the complete server type mapping:</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a08b7-107">数据类型</span><span class="sxs-lookup"><span data-stu-id="a08b7-107">data type</span></span>|<span data-ttu-id="a08b7-108">OLE DB 数据类型</span><span class="sxs-lookup"><span data-stu-id="a08b7-108">OLE DB data type</span></span>|<span data-ttu-id="a08b7-109">值</span><span class="sxs-lookup"><span data-stu-id="a08b7-109">Value</span></span>|  
|-----------------------------------------|----------------------|-----------|  
|<span data-ttu-id="a08b7-110">datetime</span><span class="sxs-lookup"><span data-stu-id="a08b7-110">datetime</span></span>|<span data-ttu-id="a08b7-111">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-111">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-112">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="a08b7-112">135 (oledb.h)</span></span>|  
|<span data-ttu-id="a08b7-113">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="a08b7-113">smalldatetime</span></span>|<span data-ttu-id="a08b7-114">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-114">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-115">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="a08b7-115">135 (oledb.h)</span></span>|  
|<span data-ttu-id="a08b7-116">date</span><span class="sxs-lookup"><span data-stu-id="a08b7-116">date</span></span>|<span data-ttu-id="a08b7-117">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="a08b7-117">DBTYPE_DBDATE</span></span>|<span data-ttu-id="a08b7-118">133 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="a08b7-118">133 (oledb.h)</span></span>|  
|<span data-ttu-id="a08b7-119">time</span><span class="sxs-lookup"><span data-stu-id="a08b7-119">time</span></span>|<span data-ttu-id="a08b7-120">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="a08b7-120">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="a08b7-121">145 (sqlncli.msi) </span><span class="sxs-lookup"><span data-stu-id="a08b7-121">145 (sqlncli.h)</span></span>|  
|<span data-ttu-id="a08b7-122">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="a08b7-122">datetimeoffset</span></span>|<span data-ttu-id="a08b7-123">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="a08b7-123">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="a08b7-124">146 (sqlncli.msi) </span><span class="sxs-lookup"><span data-stu-id="a08b7-124">146 (sqlncli.h)</span></span>|  
|<span data-ttu-id="a08b7-125">datetime2</span><span class="sxs-lookup"><span data-stu-id="a08b7-125">datetime2</span></span>|<span data-ttu-id="a08b7-126">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-126">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-127">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="a08b7-127">135 (oledb.h)</span></span>|  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="a08b7-128">数据格式：字符串和文字</span><span class="sxs-lookup"><span data-stu-id="a08b7-128">Data Formats: Strings and Literals</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a08b7-129">数据类型</span><span class="sxs-lookup"><span data-stu-id="a08b7-129">data type</span></span>|<span data-ttu-id="a08b7-130">OLE DB 数据类型</span><span class="sxs-lookup"><span data-stu-id="a08b7-130">OLE DB data type</span></span>|<span data-ttu-id="a08b7-131">客户端转换的字符串格式</span><span class="sxs-lookup"><span data-stu-id="a08b7-131">String format for client conversions</span></span>|  
|-----------------------------------------|----------------------|------------------------------------------|  
|<span data-ttu-id="a08b7-132">datetime</span><span class="sxs-lookup"><span data-stu-id="a08b7-132">datetime</span></span>|<span data-ttu-id="a08b7-133">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-133">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-134">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="a08b7-134">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a08b7-135">对于 Datetime 最多支持三位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-135">supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="a08b7-136">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="a08b7-136">smalldatetime</span></span>|<span data-ttu-id="a08b7-137">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-137">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-138">'yyyy-mm-dd hh:mm:ss'</span><span class="sxs-lookup"><span data-stu-id="a08b7-138">'yyyy-mm-dd hh:mm:ss'</span></span><br /><br /> <span data-ttu-id="a08b7-139">此数据类型精确到 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="a08b7-139">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="a08b7-140">秒部分在输出中将为零，在输入中由服务器进行四舍五入。</span><span class="sxs-lookup"><span data-stu-id="a08b7-140">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="a08b7-141">date</span><span class="sxs-lookup"><span data-stu-id="a08b7-141">date</span></span>|<span data-ttu-id="a08b7-142">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="a08b7-142">DBTYPE_DBDATE</span></span>|<span data-ttu-id="a08b7-143">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="a08b7-143">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="a08b7-144">time</span><span class="sxs-lookup"><span data-stu-id="a08b7-144">time</span></span>|<span data-ttu-id="a08b7-145">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="a08b7-145">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="a08b7-146">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="a08b7-146">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="a08b7-147">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-147">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="a08b7-148">datetime2</span><span class="sxs-lookup"><span data-stu-id="a08b7-148">datetime2</span></span>|<span data-ttu-id="a08b7-149">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-149">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span><span class="sxs-lookup"><span data-stu-id="a08b7-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span></span><br /><br /> <span data-ttu-id="a08b7-151">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-151">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="a08b7-152">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="a08b7-152">datetimeoffset</span></span>|<span data-ttu-id="a08b7-153">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="a08b7-153">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="a08b7-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span><span class="sxs-lookup"><span data-stu-id="a08b7-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span></span><br /><br /> <span data-ttu-id="a08b7-155">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-155">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="a08b7-156">日期/时间文字的转义序列没有更改。</span><span class="sxs-lookup"><span data-stu-id="a08b7-156">There are no changes to the escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="a08b7-157">结果中秒的小数部分使用点 (.)，而不是冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="a08b7-157">Fractional seconds in results use a dot (.) rather than a colon (:).</span></span>  
  
 <span data-ttu-id="a08b7-158">返回给应用程序的字符串值长度始终与给定列的长度相同。</span><span class="sxs-lookup"><span data-stu-id="a08b7-158">String values returned to applications will always be the same length for a given column.</span></span> <span data-ttu-id="a08b7-159">将使用前导零将年、月、日、小时、分钟和秒部分填充到最大长度。</span><span class="sxs-lookup"><span data-stu-id="a08b7-159">Year, month, day, hour, minute, and second components will be padded with leading zeros to their maximum width.</span></span> <span data-ttu-id="a08b7-160">在日期和时间之间只有一个空格，时间和时区偏移量之间也只有一个空格。</span><span class="sxs-lookup"><span data-stu-id="a08b7-160">There will be exactly one space between date and time and exactly one space between the time and timezone offset.</span></span> <span data-ttu-id="a08b7-161">时区偏移量始终带符号。</span><span class="sxs-lookup"><span data-stu-id="a08b7-161">A timezone offset will always be preceded by a sign.</span></span> <span data-ttu-id="a08b7-162">偏移量为零时，此符号将为正号 (+)。</span><span class="sxs-lookup"><span data-stu-id="a08b7-162">This sign will be a plus (+) when the offset is zero.</span></span> <span data-ttu-id="a08b7-163">符号和偏移量值之间没有空格。</span><span class="sxs-lookup"><span data-stu-id="a08b7-163">There will be no white space between the sign and the offset value.</span></span> <span data-ttu-id="a08b7-164">必要时将使用尾随零将秒小数部分填充到列的定义精度，但是不会填充更多的零。</span><span class="sxs-lookup"><span data-stu-id="a08b7-164">Fractional seconds will be padded with trailing zeros, if necessary, up to the defined precision for the column, but no further.</span></span> <span data-ttu-id="a08b7-165">对于 datetime 列，秒小数部分有三位数字。</span><span class="sxs-lookup"><span data-stu-id="a08b7-165">For datetime columns, there will be three fractional seconds digits.</span></span> <span data-ttu-id="a08b7-166">对于 smalldatetime 列，没有秒小数部分，秒始终为零。</span><span class="sxs-lookup"><span data-stu-id="a08b7-166">For smalldatetime columns, there will be no fractional seconds digits and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="a08b7-167">从应用程序提供的字符串值转换将更为灵活，允许各个组成部分值小于最大长度。</span><span class="sxs-lookup"><span data-stu-id="a08b7-167">Conversions from string values provided by the application will be more flexible and will allow component values less than maximum width.</span></span> <span data-ttu-id="a08b7-168">年可以包含 1-4 位数字。</span><span class="sxs-lookup"><span data-stu-id="a08b7-168">Years can be 1-4 digits.</span></span> <span data-ttu-id="a08b7-169">月、日、小时、分钟和秒可以包含 1 位或 2 位数字。</span><span class="sxs-lookup"><span data-stu-id="a08b7-169">Months, days, hours, minutes, and seconds can be 1 or 2 digits.</span></span> <span data-ttu-id="a08b7-170">日期/时间和时间/时区偏移量之间可以有任意多的空格。</span><span class="sxs-lookup"><span data-stu-id="a08b7-170">There can be arbitrary white space between date/time and time/timezone offsets.</span></span> <span data-ttu-id="a08b7-171">零小时零分钟的偏移量符号可以为正号，也可以为负号。</span><span class="sxs-lookup"><span data-stu-id="a08b7-171">The sign of an offset with zero hours and zero minutes can be plus or minus.</span></span> <span data-ttu-id="a08b7-172">可以为秒小数部分填充尾随零，使之最多达到 9 位数字。</span><span class="sxs-lookup"><span data-stu-id="a08b7-172">Trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="a08b7-173">可以使用小数点结束时间部分，不带秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-173">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="a08b7-174">空字符串不是有效的日期/时间文字，它不表示 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a08b7-174">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="a08b7-175">尝试将空字符串转换为日期/时间值将导致具有 SQLState 22018 和消息“为转换指定的字符值无效”的错误。</span><span class="sxs-lookup"><span data-stu-id="a08b7-175">An attempt to convert an empty string to a date/time value will result in errors with SQLState 22018 and the message "Invalid character value for cast specification".</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="a08b7-176">数据格式：数据结构</span><span class="sxs-lookup"><span data-stu-id="a08b7-176">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="a08b7-177">在以下所述的 OLE DB 特定结构中，OLE DB 遵守与 ODBC 相同的约束。</span><span class="sxs-lookup"><span data-stu-id="a08b7-177">In the OLE DB-specific structures described below, OLE DB conforms to the same constraints as ODBC.</span></span> <span data-ttu-id="a08b7-178">这些值取自公历：</span><span class="sxs-lookup"><span data-stu-id="a08b7-178">These are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="a08b7-179">“月”范围为从 1 到 12。</span><span class="sxs-lookup"><span data-stu-id="a08b7-179">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="a08b7-180">“日”字段范围为 1 到所在月包含的天数，必须与“年”和“月”字段一致，考虑闰年。</span><span class="sxs-lookup"><span data-stu-id="a08b7-180">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="a08b7-181">“小时”范围为从 0 到 23。</span><span class="sxs-lookup"><span data-stu-id="a08b7-181">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="a08b7-182">“分钟”范围为从 0 到 59。</span><span class="sxs-lookup"><span data-stu-id="a08b7-182">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="a08b7-183">秒范围是 0 到 59。</span><span class="sxs-lookup"><span data-stu-id="a08b7-183">Seconds range from 0 through 59.</span></span> <span data-ttu-id="a08b7-184">这允许最多两个闰秒以便与恒星时间保持同步。</span><span class="sxs-lookup"><span data-stu-id="a08b7-184">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
 <span data-ttu-id="a08b7-185">已对以下现有 OLE DB 结构的实现进行了修改，以支持新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="a08b7-185">Implementations for the following existing OLE DB structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="a08b7-186">不过未更改定义。</span><span class="sxs-lookup"><span data-stu-id="a08b7-186">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="a08b7-187">DBTYPE_DATE（这是自动化 DATE 类型。</span><span class="sxs-lookup"><span data-stu-id="a08b7-187">DBTYPE_DATE (This is an automation DATE type.</span></span> <span data-ttu-id="a08b7-188">它在内部表示为 `double`。</span><span class="sxs-lookup"><span data-stu-id="a08b7-188">It is internally represented as a `double`..</span></span> <span data-ttu-id="a08b7-189">整数部分是自 1899 年 12 月 30 日以来的天数，小数部分是不足一天的部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-189">The whole part is the number of days since December 30, 1899 and the fractional part is the fraction of a day.</span></span> <span data-ttu-id="a08b7-190">此类型的精确度为 1 秒，因此具有有效的 0 刻度。）</span><span class="sxs-lookup"><span data-stu-id="a08b7-190">This type has an accuracy of 1 second, so has an effective scale of 0.)</span></span>  
  
-   <span data-ttu-id="a08b7-191">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="a08b7-191">DBTYPE_DBDATE</span></span>  
  
-   <span data-ttu-id="a08b7-192">DBTYPE_DBTIME</span><span class="sxs-lookup"><span data-stu-id="a08b7-192">DBTYPE_DBTIME</span></span>  
  
-   <span data-ttu-id="a08b7-193">DBTYPE_DBTIMESTAMP（小数字段由 OLE DB 定义为秒的十亿分之一（纳秒），范围为 0-999,999,999）</span><span class="sxs-lookup"><span data-stu-id="a08b7-193">DBTYPE_DBTIMESTAMP (the fraction field is defined by OLE DB as the number of billionths of a second (nanoseconds) and ranges from 0-999,999,999)</span></span>  
  
-   <span data-ttu-id="a08b7-194">DBTYPE_FILETIME</span><span class="sxs-lookup"><span data-stu-id="a08b7-194">DBTYPE_FILETIME</span></span>  
  
### <a name="dbtype_dbtime2"></a><span data-ttu-id="a08b7-195">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="a08b7-195">DBTYPE_DBTIME2</span></span>  
 <span data-ttu-id="a08b7-196">此结构在 32 位和 64 位操作系统中都填充到 12 个字节。</span><span class="sxs-lookup"><span data-stu-id="a08b7-196">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype_-dbtimestampoffset"></a><span data-ttu-id="a08b7-197">DBTYPE_ DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="a08b7-197">DBTYPE_ DBTIMESTAMPOFFSET</span></span>  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 <span data-ttu-id="a08b7-198">如果 `timezone_hour` 为负数，`timezone_minute` 必须为负数或零。</span><span class="sxs-lookup"><span data-stu-id="a08b7-198">If `timezone_hour` is negative, `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="a08b7-199">如果 `timezone_hour` 为正数，`timezone minute` 必须为正数或零。</span><span class="sxs-lookup"><span data-stu-id="a08b7-199">If `timezone_hour` is positive, `timezone minute` must be positive or zero.</span></span> <span data-ttu-id="a08b7-200">如果 `timezone_hour` 是零，`timezone minute` 可以取 -59 到 +59 之间的值。</span><span class="sxs-lookup"><span data-stu-id="a08b7-200">If `timezone_hour` is zero, `timezone minute` can hold a value between -59 and +59.</span></span>  
  
### <a name="ssvariant"></a><span data-ttu-id="a08b7-201">SSVARIANT</span><span class="sxs-lookup"><span data-stu-id="a08b7-201">SSVARIANT</span></span>  
 <span data-ttu-id="a08b7-202">此结构现在包括新结构 DBTYPE_DBTIME2 和 DBTYPE_DBTIMESTAMPOFFSET，并为相应类型添加了秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="a08b7-202">This struct now includes the new structures, DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET, and adds fractional seconds scale for appropriate types.</span></span>  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 <span data-ttu-id="a08b7-203">此外，将按以下方式对与 SSVARIANT 类型编码（该编码确定枚举的类型）关联的枚举进行了扩展：</span><span class="sxs-lookup"><span data-stu-id="a08b7-203">In addition, the enum associated with SSVARIANT type encoding, which determines the type of the enum, will be extended as follows:</span></span>  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 <span data-ttu-id="a08b7-204">如果将基础架构更新为使用 `sql_variant` 而非 `datetime`，则使用 `datetime2` 并依赖于 `datetime` 的受限制精度的应用程序在迁移到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 时，必须对它们进行更新。</span><span class="sxs-lookup"><span data-stu-id="a08b7-204">Applications migrating to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client that use `sql_variant` and rely on the limited precision of `datetime` will have to be updated if the underlying schema is updated to use `datetime2` rather than `datetime`.</span></span>  
  
 <span data-ttu-id="a08b7-205">还通过添加以下内容，对 SSVARIANT 的访问宏进行了扩展：</span><span class="sxs-lookup"><span data-stu-id="a08b7-205">The access macros for SSVARIANT have also been extended with the addition of the following:</span></span>  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a><span data-ttu-id="a08b7-206">ITableDefinition::CreateTable 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="a08b7-206">Data Type Mapping in ITableDefinition::CreateTable</span></span>  
 <span data-ttu-id="a08b7-207">以下类型映射用于 ITableDefinition::CreateTable 所使用的 DBCOLUMNDESC 结构：</span><span class="sxs-lookup"><span data-stu-id="a08b7-207">The following type mapping is used with DBCOLUMNDESC structures used by ITableDefinition::CreateTable:</span></span>  
  
|<span data-ttu-id="a08b7-208">OLE DB 数据类型 (wType\*\*)</span><span class="sxs-lookup"><span data-stu-id="a08b7-208">OLE DB data type (*wType*)</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a08b7-209">数据类型</span><span class="sxs-lookup"><span data-stu-id="a08b7-209">data type</span></span>|<span data-ttu-id="a08b7-210">注释</span><span class="sxs-lookup"><span data-stu-id="a08b7-210">Notes</span></span>|  
|----------------------------------|-----------------------------------------|-----------|  
|<span data-ttu-id="a08b7-211">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="a08b7-211">DBTYPE_DBDATE</span></span>|<span data-ttu-id="a08b7-212">date</span><span class="sxs-lookup"><span data-stu-id="a08b7-212">date</span></span>||  
|<span data-ttu-id="a08b7-213">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a08b7-213">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="a08b7-214">`datetime2`(p)</span><span class="sxs-lookup"><span data-stu-id="a08b7-214">`datetime2`(p)</span></span>|<span data-ttu-id="a08b7-215">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序检查 DBCOLUMDESC *bScale*成员，以确定秒的小数部分精度。</span><span class="sxs-lookup"><span data-stu-id="a08b7-215">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="a08b7-216">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="a08b7-216">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="a08b7-217">`time`(p)</span><span class="sxs-lookup"><span data-stu-id="a08b7-217">`time`(p)</span></span>|<span data-ttu-id="a08b7-218">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序检查 DBCOLUMDESC *bScale*成员，以确定秒的小数部分精度。</span><span class="sxs-lookup"><span data-stu-id="a08b7-218">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="a08b7-219">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="a08b7-219">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="a08b7-220">`datetimeoffset`(p)</span><span class="sxs-lookup"><span data-stu-id="a08b7-220">`datetimeoffset`(p)</span></span>|<span data-ttu-id="a08b7-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序检查 DBCOLUMDESC *bScale*成员，以确定秒的小数部分精度。</span><span class="sxs-lookup"><span data-stu-id="a08b7-221">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
  
 <span data-ttu-id="a08b7-222">当应用程序在*wType*中指定 DBTYPE_DBTIMESTAMP 时，它可以 `datetime2` 通过在*pwszTypeName*中提供类型名称来替代到的映射。</span><span class="sxs-lookup"><span data-stu-id="a08b7-222">When an application specifies DBTYPE_DBTIMESTAMP in *wType*, it can override the mapping to `datetime2` by supplying a type name in *pwszTypeName*.</span></span> <span data-ttu-id="a08b7-223">如果 `datetime` 指定了，则*bScale*必须为3。</span><span class="sxs-lookup"><span data-stu-id="a08b7-223">If `datetime` is specified, *bScale* must be 3.</span></span> <span data-ttu-id="a08b7-224">如果 `smalldatetime` 指定了，则*bScale*必须为0。</span><span class="sxs-lookup"><span data-stu-id="a08b7-224">If `smalldatetime` is specified, *bScale* must be 0.</span></span> <span data-ttu-id="a08b7-225">如果*bScale*与*wType*和*pwszTypeName*不一致，将返回 DB_E_BADSCALE。</span><span class="sxs-lookup"><span data-stu-id="a08b7-225">If *bScale* is not consistent with *wType* and *pwszTypeName*,DB_E_BADSCALE is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08b7-226">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a08b7-226">See Also</span></span>  
 [<span data-ttu-id="a08b7-227">日期和时间改进 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a08b7-227">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
