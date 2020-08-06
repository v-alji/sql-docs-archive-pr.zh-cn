---
title: SQLBindCol |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d0ca1b0fbad144117e409019d8d2247bbf918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693857"
---
# <a name="sqlbindcol"></a><span data-ttu-id="97cb8-102">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="97cb8-102">SQLBindCol</span></span>
  <span data-ttu-id="97cb8-103">作为一般规则，请考虑使用**SQLBindCol**导致数据转换的含义。</span><span class="sxs-lookup"><span data-stu-id="97cb8-103">As a general rule, consider the implications of using **SQLBindCol** to cause data conversion.</span></span> <span data-ttu-id="97cb8-104">绑定转换是客户端进程，所以，举例来说，检索绑定到字符列的浮点值将导致应用程序在提取行时执行浮点到字符的转换。</span><span class="sxs-lookup"><span data-stu-id="97cb8-104">Binding conversions are client processes, so, for example, retrieving a floating-point value bound to a character column causes the driver to perform the float-to-character conversion locally when a row is fetched.</span></span> <span data-ttu-id="97cb8-105">可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT 函数将数据转换的开销转给服务器。</span><span class="sxs-lookup"><span data-stu-id="97cb8-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT function can be used to place the cost of data conversion on the server.</span></span>  
  
 <span data-ttu-id="97cb8-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例可以对执行的单个语句返回多个结果行集。</span><span class="sxs-lookup"><span data-stu-id="97cb8-106">An instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can return multiple sets of result rows on a single statement execution.</span></span> <span data-ttu-id="97cb8-107">每个结果集都必须单独绑定。</span><span class="sxs-lookup"><span data-stu-id="97cb8-107">Each result set must be bound separately.</span></span> <span data-ttu-id="97cb8-108">有关多个结果集的绑定的详细信息，请参阅[SQLMoreResults](sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="97cb8-108">For more information about binding for multiple result sets, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="97cb8-109">开发人员可以使用 TargetType 值将列绑定到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的 C *TargetType*数据类型 `SQL_C_BINARY` 。</span><span class="sxs-lookup"><span data-stu-id="97cb8-109">The developer can bind columns to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types using the *TargetType* value `SQL_C_BINARY`.</span></span> <span data-ttu-id="97cb8-110">不可移植绑定到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定类型的列。</span><span class="sxs-lookup"><span data-stu-id="97cb8-110">Columns bound to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific types are not portable.</span></span> <span data-ttu-id="97cb8-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的已定义 ODBC C 数据类型与 DB-Library 的类型定义匹配，移植应用程序的 DB-Library 开发人员可能需要利用此功能。</span><span class="sxs-lookup"><span data-stu-id="97cb8-111">The defined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific ODBC C data types match the type definitions for DB-Library, and DB-Library developers porting applications may want to take advantage of this feature.</span></span>  
  
 <span data-ttu-id="97cb8-112">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序，报告数据截断是一种开销高昂的过程。</span><span class="sxs-lookup"><span data-stu-id="97cb8-112">Reporting data truncation is an expensive process for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="97cb8-113">通过确保所有绑定数据缓冲区的宽度足以返回数据，可以避免截断。</span><span class="sxs-lookup"><span data-stu-id="97cb8-113">You can avoid truncation by ensuring that all bound data buffers are wide enough to return data.</span></span> <span data-ttu-id="97cb8-114">对于字符数据，在使用字符串终止的默认驱动程序行为时，该宽度应该包括字符串终止符所占的空间。</span><span class="sxs-lookup"><span data-stu-id="97cb8-114">For character data, the width should include space for a string terminator when the default driver behavior for string termination is used.</span></span> <span data-ttu-id="97cb8-115">例如，如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*char (5) \*\*列绑定到五个字符的数组，则每个提取的值都将导致截断。</span><span class="sxs-lookup"><span data-stu-id="97cb8-115">For example, binding a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** column to an array of five characters results in truncation for every value fetched.</span></span> <span data-ttu-id="97cb8-116">将同一列绑定到六个字符的数组可以提供一个用于存储空终止符的字符元素，这样即避免了截断。</span><span class="sxs-lookup"><span data-stu-id="97cb8-116">Binding the same column to an array of six characters avoids the truncation by providing a character element in which to store the null terminator.</span></span> <span data-ttu-id="97cb8-117">[SQLGetData](sqlgetdata.md)可用于在不截断的情况下有效地检索长字符和二进制数据。</span><span class="sxs-lookup"><span data-stu-id="97cb8-117">[SQLGetData](sqlgetdata.md) can be used to efficiently retrieve long character and binary data without truncation.</span></span>  
  
 <span data-ttu-id="97cb8-118">对于大值数据类型，如果用户提供的缓冲区不够大，无法保存列的整个值， `SQL_SUCCESS_WITH_INFO` 则返回，并返回 "字符串数据;发出右截断 "警告。</span><span class="sxs-lookup"><span data-stu-id="97cb8-118">For large value data types, if the user supplied buffer isn't large enough to hold the entire value of the column, `SQL_SUCCESS_WITH_INFO` is returned and the "string data; right truncation" warning is issued.</span></span> <span data-ttu-id="97cb8-119">`StrLen_or_IndPtr` 参数将包含存储在缓冲区中的字符/字节数。</span><span class="sxs-lookup"><span data-stu-id="97cb8-119">The `StrLen_or_IndPtr` argument will contain the number of chars/bytes stored in the buffer.</span></span>  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="97cb8-120">SQLBindCol 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="97cb8-120">SQLBindCol Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="97cb8-121">日期/时间类型的结果列值按[从 SQL 到 C 的转换](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述进行转换。请注意，若要将 time 和 datetimeoffset 列检索为其相应的结构 (`SQL_SS_TIME2_STRUCT` 和**SQL_SS_TIMESTAMPOFFSET_STRUCT**) ，则必须将*TargetType*指定为 `SQL_C_DEFAULT` 或 `SQL_C_BINARY` 。</span><span class="sxs-lookup"><span data-stu-id="97cb8-121">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Note that to retrieve time and datetimeoffset columns as their corresponding structures (`SQL_SS_TIME2_STRUCT` and **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* must be specified as `SQL_C_DEFAULT` or `SQL_C_BINARY`.</span></span>  
  
 <span data-ttu-id="97cb8-122">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="97cb8-122">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a><span data-ttu-id="97cb8-123">SQLBindCol 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="97cb8-123">SQLBindCol Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="97cb8-124">**SQLBindCol**支持 (udt) 的大型 CLR 用户定义类型。</span><span class="sxs-lookup"><span data-stu-id="97cb8-124">**SQLBindCol** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="97cb8-125">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="97cb8-125">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cb8-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97cb8-126">See Also</span></span>  
 <span data-ttu-id="97cb8-127">[SQLBindCol 函数](https://go.microsoft.com/fwlink/?LinkId=59327) </span><span class="sxs-lookup"><span data-stu-id="97cb8-127">[SQLBindCol Function](https://go.microsoft.com/fwlink/?LinkId=59327) </span></span>  
 [<span data-ttu-id="97cb8-128">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="97cb8-128">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
