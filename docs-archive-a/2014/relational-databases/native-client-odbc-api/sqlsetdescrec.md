---
title: SQLSetDescRec |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescRec function
ms.assetid: 203d02a2-aa09-462b-a489-a2cdd6f6023b
author: rothja
ms.author: jroth
ms.openlocfilehash: f2a6c8084f092040a3fd4cccee50d6a3b940cc45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590743"
---
# <a name="sqlsetdescrec"></a><span data-ttu-id="5c819-102">SQLSetDescRec</span><span class="sxs-lookup"><span data-stu-id="5c819-102">SQLSetDescRec</span></span>
  <span data-ttu-id="5c819-103">本主题讨论特定于 Native Client 的 SQLSetDescRec 功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5c819-103">This topic discusses SQLSetDescRec functionality that is specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="sqlsetdescrec-and-table-valued-parameters"></a><span data-ttu-id="5c819-104">SQLSetDescRec 和表值参数</span><span class="sxs-lookup"><span data-stu-id="5c819-104">SQLSetDescRec and Table-Valued Parameters</span></span>  
 <span data-ttu-id="5c819-105">SQLSetDescRec 可用于为表值参数和表值参数列设置描述符字段。</span><span class="sxs-lookup"><span data-stu-id="5c819-105">SQLSetDescRec can be used to set descriptor fields for table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="5c819-106">表值参数列仅在将描述符标头字段 SQL_SOPT_SS_PARAM_FOCUS 设置为特定记录（其 SQL_DESC_TYPE 设置为 SQL_SS_TABLE）的序数时可用。</span><span class="sxs-lookup"><span data-stu-id="5c819-106">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="5c819-107">有关 SQL_SOPT_SS_PARAM_FOCUS 的详细信息，请参阅[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="5c819-107">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="5c819-108">下表介绍了参数和描述符字段之间的映射。</span><span class="sxs-lookup"><span data-stu-id="5c819-108">The following table describes the mapping between parameters and descriptor fields.</span></span>  
  
|<span data-ttu-id="5c819-109">参数</span><span class="sxs-lookup"><span data-stu-id="5c819-109">Parameter</span></span>|<span data-ttu-id="5c819-110">非表值参数类型的相关属性，包括表值参数列</span><span class="sxs-lookup"><span data-stu-id="5c819-110">Related attribute for non-table-valued parameter types, including table-valued parameter columns</span></span>|<span data-ttu-id="5c819-111">表值参数的相关属性</span><span class="sxs-lookup"><span data-stu-id="5c819-111">Related attribute for table-valued parameters</span></span>|  
|---------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------|  
|<span data-ttu-id="5c819-112">*Type*</span><span class="sxs-lookup"><span data-stu-id="5c819-112">*Type*</span></span>|<span data-ttu-id="5c819-113">SQL_DESC_TYPE</span><span class="sxs-lookup"><span data-stu-id="5c819-113">SQL_DESC_TYPE</span></span>|<span data-ttu-id="5c819-114">SQL_SS_TABLE</span><span class="sxs-lookup"><span data-stu-id="5c819-114">SQL_SS_TABLE</span></span>|  
|<span data-ttu-id="5c819-115">*类型*</span><span class="sxs-lookup"><span data-stu-id="5c819-115">*SubType*</span></span>|<span data-ttu-id="5c819-116">忽略</span><span class="sxs-lookup"><span data-stu-id="5c819-116">Ignored</span></span>|<span data-ttu-id="5c819-117">对于 SQL_DATETIME 或 SQL_INTERVAL 类型的记录，请将它设置为 SQL_DESC_DATETIME_INTERVAL_CODE。</span><span class="sxs-lookup"><span data-stu-id="5c819-117">For records of type SQL_DATETIME or SQL_INTERVAL, set this to SQL_DESC_DATETIME_INTERVAL_CODE.</span></span>|  
|<span data-ttu-id="5c819-118">*长度*</span><span class="sxs-lookup"><span data-stu-id="5c819-118">*Length*</span></span>|<span data-ttu-id="5c819-119">SQL_DESC_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5c819-119">SQL_DESC_OCTET_LENGTH</span></span>|<span data-ttu-id="5c819-120">表值参数类型名称的长度。</span><span class="sxs-lookup"><span data-stu-id="5c819-120">The length of the table-valued parameter type name.</span></span> <span data-ttu-id="5c819-121">如果类型名称是以 null 结束，则它可为 SQL_NTS；如果不需要表值参数类型名称，则为零。</span><span class="sxs-lookup"><span data-stu-id="5c819-121">This can be SQL_NTS if the type name is null terminated, or zero if the table-valued parameter type name is not required.</span></span>|  
|<span data-ttu-id="5c819-122">*精度*</span><span class="sxs-lookup"><span data-stu-id="5c819-122">*Precision*</span></span>|<span data-ttu-id="5c819-123">SQL_DESC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5c819-123">SQL_DESC_PRECISION</span></span>|<span data-ttu-id="5c819-124">SQL_DESC_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="5c819-124">SQL_DESC_ARRAY_SIZE</span></span>|  
|<span data-ttu-id="5c819-125">*缩放*</span><span class="sxs-lookup"><span data-stu-id="5c819-125">*Scale*</span></span>|<span data-ttu-id="5c819-126">SQL_DESC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5c819-126">SQL_DESC_SCALE</span></span>|<span data-ttu-id="5c819-127">未使用。</span><span class="sxs-lookup"><span data-stu-id="5c819-127">Unused.</span></span> <span data-ttu-id="5c819-128">此参数应为零。</span><span class="sxs-lookup"><span data-stu-id="5c819-128">This parameter should be zero.</span></span>|  
|<span data-ttu-id="5c819-129">*DataPtr*</span><span class="sxs-lookup"><span data-stu-id="5c819-129">*DataPtr*</span></span>|<span data-ttu-id="5c819-130">APD 中的 SQL_DESC_DATA_PTR</span><span class="sxs-lookup"><span data-stu-id="5c819-130">SQL_DESC_DATA_PTR in APD</span></span>|<span data-ttu-id="5c819-131">SQL_CA_SS_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5c819-131">SQL_CA_SS_TYPE_NAME</span></span><br /><br /> <span data-ttu-id="5c819-132">对于存储过程调用，此参数是可选的。如果不需要此参数，则可以指定为 NULL。</span><span class="sxs-lookup"><span data-stu-id="5c819-132">This parameter is optional for stored procedure calls, and NULL can be specified if it is not required.</span></span> <span data-ttu-id="5c819-133">对于非过程调用的 SQL 语句，必须指定此参数。</span><span class="sxs-lookup"><span data-stu-id="5c819-133">This parameter must be specified for SQL statements that are not procedure calls.</span></span><br /><br /> <span data-ttu-id="5c819-134">*DataPtr*还充当唯一值，应用程序可在使用可变行绑定时用于标识此表值参数。</span><span class="sxs-lookup"><span data-stu-id="5c819-134">*DataPtr* also serves as a unique value that the application can use to identify this table-valued parameter when variable row binding is used.</span></span>|  
|<span data-ttu-id="5c819-135">*StringLengthPtr*</span><span class="sxs-lookup"><span data-stu-id="5c819-135">*StringLengthPtr*</span></span>|<span data-ttu-id="5c819-136">SQL_DESC_OCTET_LENGTH_PTR</span><span class="sxs-lookup"><span data-stu-id="5c819-136">SQL_DESC_OCTET_LENGTH_PTR</span></span>|<span data-ttu-id="5c819-137">SQL_DESC_OCTET_LENGTH_PTR</span><span class="sxs-lookup"><span data-stu-id="5c819-137">SQL_DESC_OCTET_LENGTH_PTR</span></span><br /><br /> <span data-ttu-id="5c819-138">对于表值参数，它是要传输的行数或 SQL_DATA_AT_EXEC。</span><span class="sxs-lookup"><span data-stu-id="5c819-138">For a table-valued parameter, this is the number of rows to transfer or SQL_DATA_AT_EXEC.</span></span> <span data-ttu-id="5c819-139">这是一个指向值的指针，该值包含要与 SQLExecDirect 传输的行数。</span><span class="sxs-lookup"><span data-stu-id="5c819-139">This is a pointer to a value that holds the number of rows to transfer with SQLExecDirect.</span></span>|  
|<span data-ttu-id="5c819-140">*IndicatorPtr*</span><span class="sxs-lookup"><span data-stu-id="5c819-140">*IndicatorPtr*</span></span>|<span data-ttu-id="5c819-141">SQL_DESC_INDICATOR_PTR</span><span class="sxs-lookup"><span data-stu-id="5c819-141">SQL_DESC_INDICATOR_PTR</span></span>|<span data-ttu-id="5c819-142">SQL_DESC_INDICATOR_PTR</span><span class="sxs-lookup"><span data-stu-id="5c819-142">SQL_DESC_INDICATOR_PTR</span></span>|  
  
 <span data-ttu-id="5c819-143">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5c819-143">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlsetdescrec-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="5c819-144">SQLSetDescRec 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="5c819-144">SQLSetDescRec Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="5c819-145">日期/时间类型所允许的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="5c819-145">The values allowed for date/time types are as follows:</span></span>  
  
||<span data-ttu-id="5c819-146">*Type*</span><span class="sxs-lookup"><span data-stu-id="5c819-146">*Type*</span></span>|<span data-ttu-id="5c819-147">*类型*</span><span class="sxs-lookup"><span data-stu-id="5c819-147">*SubType*</span></span>|<span data-ttu-id="5c819-148">*长度*</span><span class="sxs-lookup"><span data-stu-id="5c819-148">*Length*</span></span>|<span data-ttu-id="5c819-149">*精度*</span><span class="sxs-lookup"><span data-stu-id="5c819-149">*Precision*</span></span>|<span data-ttu-id="5c819-150">*缩放*</span><span class="sxs-lookup"><span data-stu-id="5c819-150">*Scale*</span></span>|  
|-|------------|---------------|--------------|-----------------|-------------|  
|<span data-ttu-id="5c819-151">datetime</span><span class="sxs-lookup"><span data-stu-id="5c819-151">datetime</span></span>|<span data-ttu-id="5c819-152">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="5c819-152">SQL_DATETIME</span></span>|<span data-ttu-id="5c819-153">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="5c819-153">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="5c819-154">4</span><span class="sxs-lookup"><span data-stu-id="5c819-154">4</span></span>|<span data-ttu-id="5c819-155">3</span><span class="sxs-lookup"><span data-stu-id="5c819-155">3</span></span>|<span data-ttu-id="5c819-156">3</span><span class="sxs-lookup"><span data-stu-id="5c819-156">3</span></span>|  
|<span data-ttu-id="5c819-157">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="5c819-157">smalldatetime</span></span>|<span data-ttu-id="5c819-158">SQL_SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="5c819-158">SQL_SQL_DATETIME</span></span>|<span data-ttu-id="5c819-159">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="5c819-159">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="5c819-160">8</span><span class="sxs-lookup"><span data-stu-id="5c819-160">8</span></span>|<span data-ttu-id="5c819-161">0</span><span class="sxs-lookup"><span data-stu-id="5c819-161">0</span></span>|<span data-ttu-id="5c819-162">0</span><span class="sxs-lookup"><span data-stu-id="5c819-162">0</span></span>|  
|<span data-ttu-id="5c819-163">date</span><span class="sxs-lookup"><span data-stu-id="5c819-163">date</span></span>|<span data-ttu-id="5c819-164">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="5c819-164">SQL_DATETIME</span></span>|<span data-ttu-id="5c819-165">SQL_CODE_DATE</span><span class="sxs-lookup"><span data-stu-id="5c819-165">SQL_CODE_DATE</span></span>|<span data-ttu-id="5c819-166">6</span><span class="sxs-lookup"><span data-stu-id="5c819-166">6</span></span>|<span data-ttu-id="5c819-167">0</span><span class="sxs-lookup"><span data-stu-id="5c819-167">0</span></span>|<span data-ttu-id="5c819-168">0</span><span class="sxs-lookup"><span data-stu-id="5c819-168">0</span></span>|  
|<span data-ttu-id="5c819-169">time</span><span class="sxs-lookup"><span data-stu-id="5c819-169">time</span></span>|<span data-ttu-id="5c819-170">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="5c819-170">SQL_SS_TIME2</span></span>|<span data-ttu-id="5c819-171">0</span><span class="sxs-lookup"><span data-stu-id="5c819-171">0</span></span>|<span data-ttu-id="5c819-172">10</span><span class="sxs-lookup"><span data-stu-id="5c819-172">10</span></span>|<span data-ttu-id="5c819-173">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-173">0..7</span></span>|<span data-ttu-id="5c819-174">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-174">0..7</span></span>|  
|<span data-ttu-id="5c819-175">datetime2</span><span class="sxs-lookup"><span data-stu-id="5c819-175">datetime2</span></span>|<span data-ttu-id="5c819-176">SQL_DATETIME</span><span class="sxs-lookup"><span data-stu-id="5c819-176">SQL_DATETIME</span></span>|<span data-ttu-id="5c819-177">SQL_CODE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="5c819-177">SQL_CODE_TIMESTAMP</span></span>|<span data-ttu-id="5c819-178">16</span><span class="sxs-lookup"><span data-stu-id="5c819-178">16</span></span>|<span data-ttu-id="5c819-179">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-179">0..7</span></span>|<span data-ttu-id="5c819-180">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-180">0..7</span></span>|  
|<span data-ttu-id="5c819-181">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="5c819-181">datetimeoffset</span></span>|<span data-ttu-id="5c819-182">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="5c819-182">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="5c819-183">0</span><span class="sxs-lookup"><span data-stu-id="5c819-183">0</span></span>|<span data-ttu-id="5c819-184">20</span><span class="sxs-lookup"><span data-stu-id="5c819-184">20</span></span>|<span data-ttu-id="5c819-185">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-185">0..7</span></span>|<span data-ttu-id="5c819-186">0..7</span><span class="sxs-lookup"><span data-stu-id="5c819-186">0..7</span></span>|  
  
 <span data-ttu-id="5c819-187">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5c819-187">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlsetdescrec-support-for-large-clr-udts"></a><span data-ttu-id="5c819-188">SQLSetDescRec 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="5c819-188">SQLSetDescRec Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="5c819-189">`SQLSetDescRec` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="5c819-189">`SQLSetDescRec` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="5c819-190">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="5c819-190">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c819-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c819-191">See Also</span></span>  
 <span data-ttu-id="5c819-192">[SQLSetDescRec](https://go.microsoft.com/fwlink/?LinkId=80704) </span><span class="sxs-lookup"><span data-stu-id="5c819-192">[SQLSetDescRec](https://go.microsoft.com/fwlink/?LinkId=80704) </span></span>  
 [<span data-ttu-id="5c819-193">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="5c819-193">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  