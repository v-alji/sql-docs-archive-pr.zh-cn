---
title: 对 ODBC 日期和时间改进的数据类型支持 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], data type support
- ODBC, date/time improvements
ms.assetid: 8e0d9ba2-3ec1-4680-86e3-b2590ba8e2e9
author: rothja
ms.author: jroth
ms.openlocfilehash: df0877a17ad8e2310db5c6e3ab4acd0c14d05611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586639"
---
# <a name="data-type-support-for-odbc-date-and-time-improvements"></a><span data-ttu-id="cae2a-102">针对 ODBC 日期/时间改进的数据类型支持</span><span class="sxs-lookup"><span data-stu-id="cae2a-102">Data Type Support for ODBC Date and Time Improvements</span></span>
  <span data-ttu-id="cae2a-103">本主题提供有关支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型的 ODBC 类型的信息。</span><span class="sxs-lookup"><span data-stu-id="cae2a-103">This topic provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
## <a name="data-type-mapping-in-parameters-and-resultsets"></a><span data-ttu-id="cae2a-104">参数和结果集中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="cae2a-104">Data Type Mapping in Parameters and Resultsets</span></span>  
 <span data-ttu-id="cae2a-105">除了 ODBC 数据类型（SQL_TYPE_TIMESTAMP 和 SQL_TIMESTAMP）以外，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 中还添加了两种新数据类型以公开新的服务器类型：</span><span class="sxs-lookup"><span data-stu-id="cae2a-105">In addition to the ODBC data types (SQL_TYPE_TIMESTAMP and SQL_TIMESTAMP), two new data types were added in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC to expose the new server types:</span></span>  
  
-   <span data-ttu-id="cae2a-106">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="cae2a-106">SQL_SS_TIME2</span></span>  
  
-   <span data-ttu-id="cae2a-107">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-107">SQL_SS_TIMESTAMPOFFSET</span></span>  
  
 <span data-ttu-id="cae2a-108">下表显示完整的服务器类型映射。</span><span class="sxs-lookup"><span data-stu-id="cae2a-108">The following table shows the complete server-type mapping.</span></span> <span data-ttu-id="cae2a-109">注意，该表的某些单元格包含两个条目；在这些情况下，第一个是针对 ODBC 3.0 的值，第二个是针对 ODBC 2.0 的值。</span><span class="sxs-lookup"><span data-stu-id="cae2a-109">Notice that some cells of the table contain two entries; in these cases, the first is the ODBC 3.0 value and the second is the ODBC 2.0 value.</span></span>  
  
|<span data-ttu-id="cae2a-110">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-110">SQL Server data type</span></span>|<span data-ttu-id="cae2a-111">SQL 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-111">SQL data type</span></span>|<span data-ttu-id="cae2a-112">值</span><span class="sxs-lookup"><span data-stu-id="cae2a-112">Value</span></span>|  
|--------------------------|-------------------|-----------|  
|<span data-ttu-id="cae2a-113">datetime</span><span class="sxs-lookup"><span data-stu-id="cae2a-113">Datetime</span></span>|<span data-ttu-id="cae2a-114">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-114">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-115">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-115">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-116">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-116">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="cae2a-117">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-117">11 (sqlext.h)</span></span>|  
|<span data-ttu-id="cae2a-118">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="cae2a-118">Smalldatetime</span></span>|<span data-ttu-id="cae2a-119">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-119">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-120">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-120">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-121">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-121">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="cae2a-122">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-122">11 (sqlext.h)</span></span>|  
|<span data-ttu-id="cae2a-123">Date</span><span class="sxs-lookup"><span data-stu-id="cae2a-123">Date</span></span>|<span data-ttu-id="cae2a-124">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-124">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="cae2a-125">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-125">SQL_DATE</span></span>|<span data-ttu-id="cae2a-126">91 (sql .h) </span><span class="sxs-lookup"><span data-stu-id="cae2a-126">91 (sql.h)</span></span><br /><br /> <span data-ttu-id="cae2a-127">9 (sqltypes.h) </span><span class="sxs-lookup"><span data-stu-id="cae2a-127">9 (sqlext.h)</span></span>|  
|<span data-ttu-id="cae2a-128">时间</span><span class="sxs-lookup"><span data-stu-id="cae2a-128">Time</span></span>|<span data-ttu-id="cae2a-129">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="cae2a-129">SQL_SS_TIME2</span></span>|<span data-ttu-id="cae2a-130">-154 (SQLNCLI.MSI) </span><span class="sxs-lookup"><span data-stu-id="cae2a-130">-154 (SQLNCLI.h)</span></span>|  
|<span data-ttu-id="cae2a-131">DatetimeOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-131">DatetimeOFFSET</span></span>|<span data-ttu-id="cae2a-132">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-132">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="cae2a-133">-155 (SQLNCLI.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-133">-155 (SQLNCLI.h)</span></span>|  
|<span data-ttu-id="cae2a-134">Datetime2</span><span class="sxs-lookup"><span data-stu-id="cae2a-134">Datetime2</span></span>|<span data-ttu-id="cae2a-135">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-135">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-136">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-136">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-137">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-137">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="cae2a-138">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-138">11 (sqlext.h)</span></span>|  
  
 <span data-ttu-id="cae2a-139">下表列出了相应的结构和 ODBC C 类型。</span><span class="sxs-lookup"><span data-stu-id="cae2a-139">The following table lists the corresponding structures and ODBC C types.</span></span> <span data-ttu-id="cae2a-140">由于 ODBC 不允许驱动程序定义的 C 类型，因此将 SQL_C_BINARY 作为二进制结构用于 time 和 datetimeoffset。</span><span class="sxs-lookup"><span data-stu-id="cae2a-140">Because ODBC does not permit driver defined C types, SQL_C_BINARY is used for time and datetimeoffset as binary structures.</span></span>  
  
|<span data-ttu-id="cae2a-141">SQL 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-141">SQL data type</span></span>|<span data-ttu-id="cae2a-142">内存布局</span><span class="sxs-lookup"><span data-stu-id="cae2a-142">Memory layout</span></span>|<span data-ttu-id="cae2a-143">默认 C 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-143">Default C data type</span></span>|<span data-ttu-id="cae2a-144">值 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-144">Value (sqlext.h)</span></span>|  
|-------------------|-------------------|-------------------------|------------------------|  
|<span data-ttu-id="cae2a-145">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-145">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-146">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-146">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-147">SQL_TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-147">SQL_TIMESTAMP_STRUCT</span></span><br /><br /> <span data-ttu-id="cae2a-148">TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-148">TIMESTAMP_STRUCT</span></span>|<span data-ttu-id="cae2a-149">SQL_C_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-149">SQL_C_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-150">SQL_C_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-150">SQL_C_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-151">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-151">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-152">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-152">SQL_TIMESTAMP</span></span>|  
|<span data-ttu-id="cae2a-153">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-153">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="cae2a-154">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-154">SQL_DATE</span></span>|<span data-ttu-id="cae2a-155">SQL_DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-155">SQL_DATE_STRUCT</span></span><br /><br /> <span data-ttu-id="cae2a-156">DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-156">DATE_STRUCT</span></span>|<span data-ttu-id="cae2a-157">SQL_C_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-157">SQL_C_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="cae2a-158">SQL_C_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-158">SQL_C_DATE</span></span>|<span data-ttu-id="cae2a-159">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-159">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="cae2a-160">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-160">SQL_DATE</span></span>|  
|<span data-ttu-id="cae2a-161">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="cae2a-161">SQL_SS_TIME2</span></span>|<span data-ttu-id="cae2a-162">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-162">SQL_SS_TIME2_STRUCT</span></span>|<span data-ttu-id="cae2a-163">SQL_C_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="cae2a-163">SQL_C_SS_TIME2</span></span><br /><br /> <span data-ttu-id="cae2a-164">SQL_C_BINARY（ODBC 3.5 和更早版本）</span><span class="sxs-lookup"><span data-stu-id="cae2a-164">SQL_C_BINARY (ODBC 3.5 and earlier)</span></span>|<span data-ttu-id="cae2a-165">0x4000 (sqlncli.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-165">0x4000 (sqlncli.h)</span></span><br /><br /> <span data-ttu-id="cae2a-166">SQL_BINARY (-2)</span><span class="sxs-lookup"><span data-stu-id="cae2a-166">SQL_BINARY (-2)</span></span>|  
|<span data-ttu-id="cae2a-167">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-167">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="cae2a-168">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-168">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>|<span data-ttu-id="cae2a-169">SQL_C_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-169">SQL_C_SS_TIMESTAMPOFFSET</span></span><br /><br /> <span data-ttu-id="cae2a-170">SQL_C_BINARY（ODBC 3.5 和更早版本）</span><span class="sxs-lookup"><span data-stu-id="cae2a-170">SQL_C_BINARY (ODBC 3.5 and earlier)</span></span>|<span data-ttu-id="cae2a-171">0x4001 (sqlncli.h)</span><span class="sxs-lookup"><span data-stu-id="cae2a-171">0x4001 (sqlncli.h)</span></span><br /><br /> <span data-ttu-id="cae2a-172">SQL_BINARY (-2)</span><span class="sxs-lookup"><span data-stu-id="cae2a-172">SQL_BINARY (-2)</span></span>|  
  
 <span data-ttu-id="cae2a-173">指定 SQL_C_BINARY 绑定时，将执行对齐检查，并对不正确的对齐报错。</span><span class="sxs-lookup"><span data-stu-id="cae2a-173">When SQL_C_BINARY binding is specified, alignment checking will be performed and an error reported for incorrect alignment.</span></span> <span data-ttu-id="cae2a-174">该错误的 SQLSTATE 将是 IM016，并显示消息“结构对齐不正确”。</span><span class="sxs-lookup"><span data-stu-id="cae2a-174">The SQLSTATE for this error will be IM016, with the message "Incorrect structure alignment".</span></span>  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="cae2a-175">数据格式：字符串和文字</span><span class="sxs-lookup"><span data-stu-id="cae2a-175">Data Formats: Strings and Literals</span></span>  
 <span data-ttu-id="cae2a-176">下表显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型、ODBC 数据类型和 ODBC 字符串文字之间的映射。</span><span class="sxs-lookup"><span data-stu-id="cae2a-176">The following table shows the mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, ODBC data types, and the ODBC string literals.</span></span>  
  
|<span data-ttu-id="cae2a-177">SQL Server 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-177">SQL Server data type</span></span>|<span data-ttu-id="cae2a-178">ODBC 数据类型</span><span class="sxs-lookup"><span data-stu-id="cae2a-178">ODBC data type</span></span>|<span data-ttu-id="cae2a-179">客户端转换的字符串格式</span><span class="sxs-lookup"><span data-stu-id="cae2a-179">String format for client conversions</span></span>|  
|--------------------------|--------------------|------------------------------------------|  
|<span data-ttu-id="cae2a-180">datetime</span><span class="sxs-lookup"><span data-stu-id="cae2a-180">Datetime</span></span>|<span data-ttu-id="cae2a-181">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-181">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-182">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-182">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-183">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="cae2a-183">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cae2a-184">对于 Datetime 最多支持三位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="cae2a-184">supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="cae2a-185">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="cae2a-185">Smalldatetime</span></span>|<span data-ttu-id="cae2a-186">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-186">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-187">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-187">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-188">'yyyy-mm-dd hh:hh:ss'</span><span class="sxs-lookup"><span data-stu-id="cae2a-188">'yyyy-mm-dd hh:hh:ss'</span></span><br /><br /> <span data-ttu-id="cae2a-189">此数据类型精确到 1 分钟。</span><span class="sxs-lookup"><span data-stu-id="cae2a-189">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="cae2a-190">秒部分在输出中将为零，在输入中由服务器进行四舍五入。</span><span class="sxs-lookup"><span data-stu-id="cae2a-190">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="cae2a-191">Date</span><span class="sxs-lookup"><span data-stu-id="cae2a-191">Date</span></span>|<span data-ttu-id="cae2a-192">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-192">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="cae2a-193">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="cae2a-193">SQL_DATE</span></span>|<span data-ttu-id="cae2a-194">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="cae2a-194">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="cae2a-195">时间</span><span class="sxs-lookup"><span data-stu-id="cae2a-195">Time</span></span>|<span data-ttu-id="cae2a-196">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="cae2a-196">SQL_SS_TIME2</span></span>|<span data-ttu-id="cae2a-197">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="cae2a-197">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="cae2a-198">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="cae2a-198">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="cae2a-199">Datetime2</span><span class="sxs-lookup"><span data-stu-id="cae2a-199">Datetime2</span></span>|<span data-ttu-id="cae2a-200">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-200">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="cae2a-201">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="cae2a-201">SQL_TIMESTAMP</span></span>|<span data-ttu-id="cae2a-202">"yyyy-mm-dd hh： mm： ss [. 维]"</span><span class="sxs-lookup"><span data-stu-id="cae2a-202">'yyyy-mm-dd hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="cae2a-203">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="cae2a-203">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="cae2a-204">DatetimeOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-204">DatetimeOFFSET</span></span>|<span data-ttu-id="cae2a-205">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="cae2a-205">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="cae2a-206">'yyyy-mm-dd hh:mm:ss[.9999999] +/- hh:mm'</span><span class="sxs-lookup"><span data-stu-id="cae2a-206">'yyyy-mm-dd hh:mm:ss[.9999999] +/- hh:mm'</span></span><br /><br /> <span data-ttu-id="cae2a-207">可以选择指定最多达到七位数字的秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="cae2a-207">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="cae2a-208">日期/时间文字的 ODBC 转义序列没有更改。</span><span class="sxs-lookup"><span data-stu-id="cae2a-208">There are no changes to the ODBC escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="cae2a-209">结果中秒的小数部分始终使用点 (.)，而不是冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="cae2a-209">Fractional seconds in results always use a dot (.), rather than a colon (:).</span></span>  
  
 <span data-ttu-id="cae2a-210">返回到应用程序的字符串值始终与给定列的长度相同。</span><span class="sxs-lookup"><span data-stu-id="cae2a-210">String values returned to applications are always the same length for a given column.</span></span> <span data-ttu-id="cae2a-211">年、月、日、小时、分钟和秒部分将以前置零填充至其最大宽度，并且 datetime 值中的日期和时间之间有一个空格。</span><span class="sxs-lookup"><span data-stu-id="cae2a-211">Year, month, day, hour, minute, and second components are padded with leading zeros to their maximum width, and there is one space between date and time in datetime values.</span></span> <span data-ttu-id="cae2a-212">在 datetimeoffset 值的时间和时区偏移量之间也有一个空格。</span><span class="sxs-lookup"><span data-stu-id="cae2a-212">There is also one space between the time and timezone offset in a datetimeoffset value.</span></span> <span data-ttu-id="cae2a-213">时区偏移量前面始终有一个符号；如果偏移量是零，则该符号是加号 (+)。</span><span class="sxs-lookup"><span data-stu-id="cae2a-213">A timezone offset is always preceded by a sign; when the offset is zero, this sign is a plus (+).</span></span> <span data-ttu-id="cae2a-214">如有必要，秒的小数部分将填充尾随零，直到达到列的定义精度。</span><span class="sxs-lookup"><span data-stu-id="cae2a-214">Fractional seconds are padded with trailing zeros if necessary, up to the defined precision for the column.</span></span> <span data-ttu-id="cae2a-215">对于 datetime 列，秒的小数部分有三位数。</span><span class="sxs-lookup"><span data-stu-id="cae2a-215">For datetime columns, there are three fractional seconds digits.</span></span> <span data-ttu-id="cae2a-216">对于 smalldatetime 列，秒部分没有小数位，并且秒将始终是零。</span><span class="sxs-lookup"><span data-stu-id="cae2a-216">For smalldatetime columns, there are no fractional seconds' digits, and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="cae2a-217">空字符串不是有效的日期/时间文字，它不表示 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="cae2a-217">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="cae2a-218">将空字符串转换到日期/时间值的尝试将导致 SQLState 22018 错误并显示消息“为转换指定的字符值无效。”。</span><span class="sxs-lookup"><span data-stu-id="cae2a-218">An attempt to convert an empty string to a date/time value will result in SQLState 22018 error and the message "Invalid character value for cast specification".</span></span>  
  
 <span data-ttu-id="cae2a-219">从字符串参数进行转换应当得到相同格式的字符串，不过，包含零小时和零分钟的时区的符号可以是加号或减号，并且允许秒的小数部分的尾随零最多可达 9 位数。</span><span class="sxs-lookup"><span data-stu-id="cae2a-219">Conversions from string parameters will expect strings in the same format, with the exceptions that the sign of a timezone with zero hours and zero minutes can be either plus or minus, and trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="cae2a-220">可以使用小数点结束时间部分，不带秒小数部分。</span><span class="sxs-lookup"><span data-stu-id="cae2a-220">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="cae2a-221">当前，驱动程序允许标点字符前后有额外的空白，并且时间和时区偏移量之间的空格是可选的。</span><span class="sxs-lookup"><span data-stu-id="cae2a-221">Currently, the driver allows additional white space around punctuation characters and the space between time and timezone offset is optional.</span></span> <span data-ttu-id="cae2a-222">但是，这可能在未来版本中更改；应用程序不应当依赖于当前行为。</span><span class="sxs-lookup"><span data-stu-id="cae2a-222">However, this might change in a future release; applications should not rely on the current behavior.</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="cae2a-223">数据格式：数据结构</span><span class="sxs-lookup"><span data-stu-id="cae2a-223">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="cae2a-224">在下面描述的结构中，ODBC 指定了来自公历的以下约束：</span><span class="sxs-lookup"><span data-stu-id="cae2a-224">In the structures described below, ODBC specifies the following constraints, which are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="cae2a-225">“月”范围为从 1 到 12。</span><span class="sxs-lookup"><span data-stu-id="cae2a-225">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="cae2a-226">“日”字段范围为 1 到所在月包含的天数，必须与“年”和“月”字段一致，考虑闰年。</span><span class="sxs-lookup"><span data-stu-id="cae2a-226">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="cae2a-227">“小时”范围为从 0 到 23。</span><span class="sxs-lookup"><span data-stu-id="cae2a-227">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="cae2a-228">“分钟”范围为从 0 到 59。</span><span class="sxs-lookup"><span data-stu-id="cae2a-228">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="cae2a-229">秒范围是 0 到 61.9(n)。</span><span class="sxs-lookup"><span data-stu-id="cae2a-229">Seconds range is 0 through 61.9(n).</span></span> <span data-ttu-id="cae2a-230">这允许最多两个闰秒以便与恒星时间保持同步。</span><span class="sxs-lookup"><span data-stu-id="cae2a-230">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
     <span data-ttu-id="cae2a-231">注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允许闰秒，因此大于 59 的秒值将导致服务器错误。</span><span class="sxs-lookup"><span data-stu-id="cae2a-231">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow leap seconds, so second values greater than 59 will cause a server error.</span></span>  
  
 <span data-ttu-id="cae2a-232">以下现有 ODBC 结构的实现已修改，以支持新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="cae2a-232">Implementations for the following existing ODBC structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="cae2a-233">不过未更改定义。</span><span class="sxs-lookup"><span data-stu-id="cae2a-233">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="cae2a-234">DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-234">DATE_STRUCT</span></span>  
  
-   <span data-ttu-id="cae2a-235">TIME_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-235">TIME_STRUCT</span></span>  
  
-   <span data-ttu-id="cae2a-236">TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-236">TIMESTAMP_STRUCT</span></span>  
  
 <span data-ttu-id="cae2a-237">还有两个新结构：</span><span class="sxs-lookup"><span data-stu-id="cae2a-237">There are also two new structs:</span></span>  
  
-   <span data-ttu-id="cae2a-238">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-238">SQL_SS_TIME2_STRUCT</span></span>  
  
-   <span data-ttu-id="cae2a-239">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-239">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>  
  
### <a name="sql_ss_time2_struct"></a><span data-ttu-id="cae2a-240">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-240">SQL_SS_TIME2_STRUCT</span></span>  
 <span data-ttu-id="cae2a-241">此结构在 32 位和 64 位操作系统中都填充到 12 个字节。</span><span class="sxs-lookup"><span data-stu-id="cae2a-241">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagSS_TIME2_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
} SQL_SS_TIME2_STRUCT;  
```  
  
### <a name="sql_ss_timestampoffset_struct"></a><span data-ttu-id="cae2a-242">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="cae2a-242">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>  
  
```  
typedef struct tagSS_TIMESTAMPOFFSET_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
   SQLSMALLINT timezone_hour;  
   SQLSMALLINT timezone_minute;  
} SQL_SS_TIMESTAMPOFFSET_STRUCT;  
```  
  
 <span data-ttu-id="cae2a-243">如果 `timezone_hour` 是负数，则 `timezone_minute` 必须是负数或零。</span><span class="sxs-lookup"><span data-stu-id="cae2a-243">If the `timezone_hour` is negative, the `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="cae2a-244">如果 `timezone_hour` 是正数，则 `timezone_minute` 必须是正数或零。</span><span class="sxs-lookup"><span data-stu-id="cae2a-244">If the `timezone_hour` is positive, the `timezone_minute` must be positive or zero.</span></span> <span data-ttu-id="cae2a-245">如果 `timezone_hour` 是零，则 `timezone_minute` 可能是 -59 到 +59 范围内的任何值。</span><span class="sxs-lookup"><span data-stu-id="cae2a-245">If the `timezone_hour` is zero, the s`timezone_minute` may have any value in the range -59 through +59.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae2a-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cae2a-246">See Also</span></span>  
 [<span data-ttu-id="cae2a-247">ODBC&#41;&#40;的日期和时间改进</span><span class="sxs-lookup"><span data-stu-id="cae2a-247">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
