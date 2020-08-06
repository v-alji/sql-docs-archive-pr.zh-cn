---
title: SQLBindParameter |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e50886457c4c20110880cc5b75ec594fd3eaba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590776"
---
# <a name="sqlbindparameter"></a><span data-ttu-id="658ae-102">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="658ae-102">SQLBindParameter</span></span>
  <span data-ttu-id="658ae-103">`SQLBindParameter`当用于为 Native Client ODBC 驱动程序提供数据时，可以消除数据转换的负担 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，从而提高应用程序的客户端和服务器组件的性能。</span><span class="sxs-lookup"><span data-stu-id="658ae-103">`SQLBindParameter` can eliminate the burden of data conversion when used to provide data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, resulting in significant performance gains for both the client and server components of applications.</span></span> <span data-ttu-id="658ae-104">其他好处包括在插入或更新近似数字数据类型时减少精度损失。</span><span class="sxs-lookup"><span data-stu-id="658ae-104">Other benefits include reduced loss of precision when inserting or updating approximate numeric data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="658ae-105">在将 `char` 和 `wchar` 类型数据插入某一图像列时，将使用要传入的数据的大小，而非转换为二进制格式后的数据大小。</span><span class="sxs-lookup"><span data-stu-id="658ae-105">When inserting `char` and `wchar` type data into an image column, the size of the data being passed in is used, as opposed to the size of the data after conversion to a binary format.</span></span>  
  
 <span data-ttu-id="658ae-106">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序在某一参数数组的单个数组元素上遇到错误，则该驱动程序将继续为其余数组元素执行语句。</span><span class="sxs-lookup"><span data-stu-id="658ae-106">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters an error on a single array element of an array of parameters, the driver continues to execute the statement for the remaining array elements.</span></span> <span data-ttu-id="658ae-107">如果该应用程序为语句绑定了某一由参数状态元素构成的数组，则可以从该数组确定生成错误的参数行。</span><span class="sxs-lookup"><span data-stu-id="658ae-107">If the application has bound an array of parameter status elements for the statement, the rows of parameters generating errors can be determined from the array.</span></span>  
  
 <span data-ttu-id="658ae-108">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序，则在绑定输入参数时指定 SQL_PARAM_INPUT。</span><span class="sxs-lookup"><span data-stu-id="658ae-108">When using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, specify SQL_PARAM_INPUT when binding input parameters.</span></span> <span data-ttu-id="658ae-109">在绑定用 OUTPUT 关键字定义的存储过程参数时，只指定 SQL_PARAM_OUTPUT 或 SQL_PARAM_INPUT_OUTPUT。</span><span class="sxs-lookup"><span data-stu-id="658ae-109">Only specify SQL_PARAM_OUTPUT or SQL_PARAM_INPUT_OUTPUT when binding stored procedure parameters defined with the OUTPUT keyword.</span></span>  
  
 <span data-ttu-id="658ae-110">[SQLRowCount](sqlrowcount.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果绑定参数数组的数组元素导致语句执行出错，则 Native Client ODBC 驱动程序的 SQLRowCount 不可靠。</span><span class="sxs-lookup"><span data-stu-id="658ae-110">[SQLRowCount](sqlrowcount.md) is unreliable with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver if an array element of a bound-parameter array causes an error in statement execution.</span></span> <span data-ttu-id="658ae-111">ODBC 语句属性 SQL_ATTR_PARAMS_PROCESSED_PTR 报告在发生错误前已处理的行数。</span><span class="sxs-lookup"><span data-stu-id="658ae-111">The ODBC statement attribute SQL_ATTR_PARAMS_PROCESSED_PTR reports the number of rows processed before the error occurs.</span></span> <span data-ttu-id="658ae-112">然后，如有必要，该应用程序将遍历其参数状态数组，以便发现成功执行的语句数目。</span><span class="sxs-lookup"><span data-stu-id="658ae-112">The application can then traverse its parameter status array to discover the number of statements successfully executed, if necessary.</span></span>  
  
## <a name="binding-parameters-for-sql-character-types"></a><span data-ttu-id="658ae-113">SQL 字符类型的绑定参数</span><span class="sxs-lookup"><span data-stu-id="658ae-113">Binding Parameters for SQL Character Types</span></span>  
 <span data-ttu-id="658ae-114">如果传入的 SQL 数据类型为字符类型，则*ColumnSize*是 (不是字节) 的字符大小。</span><span class="sxs-lookup"><span data-stu-id="658ae-114">If the SQL data type passed in is a character type, *ColumnSize* is the size in characters (not bytes).</span></span> <span data-ttu-id="658ae-115">如果数据字符串的长度大于8000，则应将*ColumnSize*设置为 `SQL_SS_LENGTH_UNLIMITED` ，以指示对 SQL 类型的大小没有限制。</span><span class="sxs-lookup"><span data-stu-id="658ae-115">If the length of the data string in bytes is greater than 8000, *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED`, indicating that there is no limit to the size of the SQL type.</span></span>  
  
 <span data-ttu-id="658ae-116">例如，如果 SQL 数据类型为，则 `SQL_WVARCHAR` *ColumnSize*不应大于4000。</span><span class="sxs-lookup"><span data-stu-id="658ae-116">For instance, if the SQL data type is `SQL_WVARCHAR`, *ColumnSize* should not be greater than 4000.</span></span> <span data-ttu-id="658ae-117">如果实际数据长度大于4000，则应将*ColumnSize*设置为， `SQL_SS_LENGTH_UNLIMITED` 以便 `nvarchar(max)` 驱动程序使用。</span><span class="sxs-lookup"><span data-stu-id="658ae-117">If the actual data length is greater than 4000, then *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED` so that `nvarchar(max)` will be used by driver.</span></span>  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a><span data-ttu-id="658ae-118">SQLBindParameter 和表值参数</span><span class="sxs-lookup"><span data-stu-id="658ae-118">SQLBindParameter and Table-Valued Parameters</span></span>  
 <span data-ttu-id="658ae-119">与其他参数类型一样，表值参数由 SQLBindParameter 绑定。</span><span class="sxs-lookup"><span data-stu-id="658ae-119">Like other parameter types, table-valued parameters are bound by SQLBindParameter.</span></span>  
  
 <span data-ttu-id="658ae-120">在已绑定某一表值参数后，也绑定其列。</span><span class="sxs-lookup"><span data-stu-id="658ae-120">After a table-valued parameter has been bound, its columns are also bound.</span></span> <span data-ttu-id="658ae-121">若要绑定列，请调用[SQLSetStmtAttr](sqlsetstmtattr.md) ，将 SQL_SOPT_SS_PARAM_FOCUS 设置为表值参数的序号。</span><span class="sxs-lookup"><span data-stu-id="658ae-121">To bind the columns, you call [SQLSetStmtAttr](sqlsetstmtattr.md) to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="658ae-122">然后，为表值参数中的每一列调用 SQLBindParameter。</span><span class="sxs-lookup"><span data-stu-id="658ae-122">Then, call SQLBindParameter for each column in the table-valued parameter.</span></span> <span data-ttu-id="658ae-123">若要返回到顶级参数绑定，请将 SQL_SOPT_SS_PARAM_FOCUS 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="658ae-123">To return to the top-level parameter bindings, set SQL_SOPT_SS_PARAM_FOCUS to 0.</span></span>  
  
 <span data-ttu-id="658ae-124">有关将参数映射到表值参数的描述符字段的信息，请参阅[表值参数和列值的绑定和数据传输](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)。</span><span class="sxs-lookup"><span data-stu-id="658ae-124">For information about mapping parameters to descriptor fields for table-valued parameters, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="658ae-125">有关表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="658ae-125">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="658ae-126">SQLBindParameter 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="658ae-126">SQLBindParameter Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="658ae-127">日期/时间类型的参数值按[从 C 转换到 SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)中所述的方式进行转换。</span><span class="sxs-lookup"><span data-stu-id="658ae-127">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span> <span data-ttu-id="658ae-128">请注意，类型为的参数 `time` `datetimeoffset` 必须将*ValueType*指定为， `SQL_C_DEFAULT` `SQL_C_BINARY` 如果使用 (和) 其相应的结构，则为 `SQL_SS_TIME2_STRUCT` `SQL_SS_TIMESTAMPOFFSET_STRUCT` 。</span><span class="sxs-lookup"><span data-stu-id="658ae-128">Note that parameters of type `time` and `datetimeoffset` must have *ValueType* specified as `SQL_C_DEFAULT` or `SQL_C_BINARY` if their corresponding structures (`SQL_SS_TIME2_STRUCT` and `SQL_SS_TIMESTAMPOFFSET_STRUCT`) are used.</span></span>  
  
 <span data-ttu-id="658ae-129">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="658ae-129">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a><span data-ttu-id="658ae-130">SQLBindParameter 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="658ae-130">SQLBindParameter Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="658ae-131">`SQLBindParameter` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="658ae-131">`SQLBindParameter` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="658ae-132">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="658ae-132">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658ae-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="658ae-133">See Also</span></span>  
 <span data-ttu-id="658ae-134">[ODBC API 实现细节](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="658ae-134">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="658ae-135">SQLBindParameter 函数</span><span class="sxs-lookup"><span data-stu-id="658ae-135">SQLBindParameter Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
