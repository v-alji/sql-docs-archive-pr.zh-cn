---
title: SQLPutData |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: 31da9c21f9e4323a492a25629a979c66a4f7d365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590757"
---
# <a name="sqlputdata"></a><span data-ttu-id="2b005-102">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="2b005-102">SQLPutData</span></span>
  <span data-ttu-id="2b005-103">当使用 SQLPutData 向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 6.0 SQL Server (400) 4.21 发送超过65535个字节的数据 (时，以下限制适用于) SQL_LONGVARCHAR () SQL_WLONGVARCHAR () SQL_LONGVARBINARY () `text` `ntext` `image` 列：</span><span class="sxs-lookup"><span data-stu-id="2b005-103">The following restrictions apply when using SQLPutData to send more than 65,535 bytes of data (for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 4.21a) or 400 KB of data (for SQL Server version 6.0 and later) for a SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) or SQL_LONGVARBINARY (`image`) column:</span></span>  
  
-   <span data-ttu-id="2b005-104">引用的参数可以是 INSERT 语句中的*insert_value* 。</span><span class="sxs-lookup"><span data-stu-id="2b005-104">The referenced parameter can be the *insert_value* in an INSERT statement.</span></span>  
  
-   <span data-ttu-id="2b005-105">引用的参数可以是 UPDATE 语句的 SET 子句中的*表达式*。</span><span class="sxs-lookup"><span data-stu-id="2b005-105">The referenced parameter can be an *expression* in the SET clause of an UPDATE statement.</span></span>  
  
 <span data-ttu-id="2b005-106">当使用版本6.5 或更低版本时，取消将向运行的服务器提供块数据的 SQLPutData 调用序列将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 导致列值的部分更新。</span><span class="sxs-lookup"><span data-stu-id="2b005-106">Canceling a sequence of SQLPutData calls that provide data in blocks to a server running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] causes a partial update of the column's value when using version 6.5 or earlier.</span></span> <span data-ttu-id="2b005-107">`text` `ntext` `image` 调用 SQLCancel 时引用的、或列被设置为中间占位符值。</span><span class="sxs-lookup"><span data-stu-id="2b005-107">The `text`, `ntext`, or `image` column that was referenced when SQLCancel was called is set to an intermediate placeholder value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b005-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序不支持连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 版和更低版本。</span><span class="sxs-lookup"><span data-stu-id="2b005-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 and earlier.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="2b005-109">诊断</span><span class="sxs-lookup"><span data-stu-id="2b005-109">Diagnostics</span></span>  
 <span data-ttu-id="2b005-110">对于 SQLPutData，有一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 特定的 SQLSTATE：</span><span class="sxs-lookup"><span data-stu-id="2b005-110">There is one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client specific SQLSTATE for SQLPutData:</span></span>  
  
|<span data-ttu-id="2b005-111">SQLSTATE</span><span class="sxs-lookup"><span data-stu-id="2b005-111">SQLSTATE</span></span>|<span data-ttu-id="2b005-112">错误</span><span class="sxs-lookup"><span data-stu-id="2b005-112">Error</span></span>|<span data-ttu-id="2b005-113">说明</span><span class="sxs-lookup"><span data-stu-id="2b005-113">Description</span></span>|  
|--------------|-----------|-----------------|  
|<span data-ttu-id="2b005-114">22026</span><span class="sxs-lookup"><span data-stu-id="2b005-114">22026</span></span>|<span data-ttu-id="2b005-115">字符串数据，长度不匹配</span><span class="sxs-lookup"><span data-stu-id="2b005-115">String data, length mismatch</span></span>|<span data-ttu-id="2b005-116">如果应用程序已指定要发送的数据的长度（以字节为单位），例如，使用 SQL_LEN_DATA_AT_EXEC (*n*) 其中*n*大于0，则应用程序通过 SQLPutData 指定的字节总数必须与指定的长度匹配。</span><span class="sxs-lookup"><span data-stu-id="2b005-116">If the length of data in bytes to be sent has been specified by an application, for example, with SQL_LEN_DATA_AT_EXEC(*n*) where *n* is greater than 0, the total number of bytes given by the application via SQLPutData must match the specified length.</span></span>|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a><span data-ttu-id="2b005-117">SQLPutData 和表值参数</span><span class="sxs-lookup"><span data-stu-id="2b005-117">SQLPutData and Table-Valued Parameters</span></span>  
 <span data-ttu-id="2b005-118">使用带有表值参数的可变行绑定时，应用程序将使用 SQLPutData。</span><span class="sxs-lookup"><span data-stu-id="2b005-118">SQLPutData is used by an application when using variable row binding with table-valued parameters.</span></span> <span data-ttu-id="2b005-119">*StrLen_Or_Ind*参数指示它已准备好供驱动程序为表值参数数据的下一行或多行收集数据，或者没有更多的可用行：</span><span class="sxs-lookup"><span data-stu-id="2b005-119">The *StrLen_Or_Ind* parameter indicates that it is ready for the driver to collect data for the next row or rows of table-valued parameter data, or that no more rows are available:</span></span>  
  
-   <span data-ttu-id="2b005-120">大于 0 的值指示可以使用下一组行值。</span><span class="sxs-lookup"><span data-stu-id="2b005-120">A value greater than 0 indicates that the next set of row values is available.</span></span>  
  
-   <span data-ttu-id="2b005-121">0 值指示已没有更多的行要发送。</span><span class="sxs-lookup"><span data-stu-id="2b005-121">A value of 0 indicates that there are no more rows to be sent.</span></span>  
  
-   <span data-ttu-id="2b005-122">任何小于 0 的值则会出错，导致记录一个诊断记录，该记录包含 SQLState HY090 和消息“字符串或缓冲区长度无效”。</span><span class="sxs-lookup"><span data-stu-id="2b005-122">Any value less than 0 is an error and results in a diagnostic record being logged with SQLState HY090 and the messaage "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="2b005-123">*DataPtr*参数将被忽略，但必须设置为非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2b005-123">The *DataPtr* parameter is ignored, but must be set to a non-NULL value.</span></span> <span data-ttu-id="2b005-124">有关详细信息，请参阅有关[表值参数和列值的绑定和数据传输](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)中的变量 TVP 行绑定部分。</span><span class="sxs-lookup"><span data-stu-id="2b005-124">For more information, see the section on Variable TVP row binding in [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="2b005-125">如果*StrLen_Or_Ind*包含除 SQL_DEFAULT_PARAM 以外的任何值或介于0和 SQL_PARAMSET_SIZE (，即 SQLBindParameter) 的*ColumnSize*参数，则为错误。</span><span class="sxs-lookup"><span data-stu-id="2b005-125">If *StrLen_Or_Ind* has any value other than SQL_DEFAULT_PARAM or a number between 0 and the SQL_PARAMSET_SIZE (that is, the *ColumnSize* parameter of SQLBindParameter), it is an error.</span></span> <span data-ttu-id="2b005-126">此错误导致 SQLPutData 返回 SQL_ERROR：SQLSTATE=HY090，“字符串或缓冲区长度无效”。</span><span class="sxs-lookup"><span data-stu-id="2b005-126">This error causes SQLPutData to return SQL_ERROR: SQLSTATE=HY090, "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="2b005-127">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2b005-127">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="2b005-128">SQLPutData 对增强的日期和时间功能的支持</span><span class="sxs-lookup"><span data-stu-id="2b005-128">SQLPutData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="2b005-129">日期/时间类型的参数值按[从 C 转换到 SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)中所述的方式进行转换。</span><span class="sxs-lookup"><span data-stu-id="2b005-129">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span>  
  
 <span data-ttu-id="2b005-130">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2b005-130">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a><span data-ttu-id="2b005-131">SQLPutData 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="2b005-131">SQLPutData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="2b005-132">`SQLPutData` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="2b005-132">`SQLPutData` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="2b005-133">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="2b005-133">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b005-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b005-134">See Also</span></span>  
 <span data-ttu-id="2b005-135">[SQLPutData 函数](https://go.microsoft.com/fwlink/?LinkId=59365) </span><span class="sxs-lookup"><span data-stu-id="2b005-135">[SQLPutData Function](https://go.microsoft.com/fwlink/?LinkId=59365) </span></span>  
 [<span data-ttu-id="2b005-136">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="2b005-136">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
