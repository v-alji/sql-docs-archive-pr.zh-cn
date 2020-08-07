---
title: SQLDescribeParam |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: rothja
ms.author: jroth
ms.openlocfilehash: 05e14ccb0fadb4f1cf05f965c79cf8c05c71f93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588492"
---
# <a name="sqldescribeparam"></a><span data-ttu-id="c40a1-102">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="c40a1-102">SQLDescribeParam</span></span>
  <span data-ttu-id="c40a1-103">若要描述任何 SQL 语句的参数， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序会在对 [!INCLUDE[tsql](../../includes/tsql-md.md)] 准备好的 ODBC 语句句柄调用 SQLDescribeParam 时生成并执行 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="c40a1-103">To describe the parameters of any SQL statement, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver builds and executes a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement when SQLDescribeParam is called on a prepared ODBC statement handle.</span></span> <span data-ttu-id="c40a1-104">结果集的元数据确定预定义语句中的参数的特征。</span><span class="sxs-lookup"><span data-stu-id="c40a1-104">The metadata of the result set determines the characteristics of the parameters in the prepared statement.</span></span> <span data-ttu-id="c40a1-105">SQLDescribeParam 可以返回 SQLExecute 或 SQLExecDirect 可能返回的任何错误代码。</span><span class="sxs-lookup"><span data-stu-id="c40a1-105">SQLDescribeParam can return any error code that SQLExecute or SQLExecDirect might return.</span></span>  
  
 <span data-ttu-id="c40a1-106">从 "允许 SQLDescribeParam" 开始，数据库引擎中的改进 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可获取预期结果的更准确说明。</span><span class="sxs-lookup"><span data-stu-id="c40a1-106">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLDescribeParam to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="c40a1-107">更准确的结果可能与早期版本的 SQLDescribeParam 返回的值不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c40a1-107">These more accurate results may differ from the values returned by SQLDescribeParam in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c40a1-108">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-108">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="c40a1-109">此外 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， *ParameterSizePtr*现在还返回一个值，该值与[ODBC 规范](https://go.microsoft.com/fwlink/?LinkId=207044)中定义的相应参数标记的列或表达式的大小的定义一致。</span><span class="sxs-lookup"><span data-stu-id="c40a1-109">Also new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *ParameterSizePtr* now returns a value that aligns with the definition for the size, in characters, of the column or expression of the corresponding parameter marker as defined in the [ODBC specification](https://go.microsoft.com/fwlink/?LinkId=207044).</span></span> <span data-ttu-id="c40a1-110">在以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中， *ParameterSizePtr*可以是类型的相应值，也可以是为 `SQL_DESC_OCTET_LENGTH` 某一类型提供给 SQLBindParameter 的不相关的列大小值， (的值 `SQL_INTEGER` ，例如) 。</span><span class="sxs-lookup"><span data-stu-id="c40a1-110">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, *ParameterSizePtr* could be the corresponding value of `SQL_DESC_OCTET_LENGTH` for the type, or an irrelevant column size value that was supplied to SQLBindParameter for a type, the value of which should be ignored (`SQL_INTEGER`, for example).</span></span>  
  
 <span data-ttu-id="c40a1-111">在以下情况下，驱动程序不支持调用 SQLDescribeParam：</span><span class="sxs-lookup"><span data-stu-id="c40a1-111">The driver does not support calling SQLDescribeParam in the following situations:</span></span>  
  
-   <span data-ttu-id="c40a1-112">在 SQLExecDirect 为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 包含 from 子句的 UPDATE 或 DELETE 语句之后。</span><span class="sxs-lookup"><span data-stu-id="c40a1-112">After SQLExecDirect for any [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE or DELETE statements containing the FROM clause.</span></span>  
  
-   <span data-ttu-id="c40a1-113">对于 HAVING 子句中包含参数或与 SUM 函数的结果相比较的任何 ODBC 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c40a1-113">For any ODBC or [!INCLUDE[tsql](../../includes/tsql-md.md)] statement containing a parameter in a HAVING clause, or compared to the result of a SUM function.</span></span>  
  
-   <span data-ttu-id="c40a1-114">对于依赖于包含参数的子查询的任何 ODBC 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="c40a1-114">For any ODBC or [!INCLUDE[tsql](../../includes/tsql-md.md)] statement depending on a subquery containing parameters.</span></span>  
  
-   <span data-ttu-id="c40a1-115">对于在比较和类似表达式中包含参数标记或包含限定谓词的 ODBC SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="c40a1-115">For ODBC SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate.</span></span>  
  
-   <span data-ttu-id="c40a1-116">对于其参数之一为函数参数的任何查询。</span><span class="sxs-lookup"><span data-stu-id="c40a1-116">For any queries where one of the parameters is a parameter to a function.</span></span>  
  
-   <span data-ttu-id="c40a1-117">当命令中有 (/\* \* /) 的注释时 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c40a1-117">When there are comments (/\* \*/) in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="c40a1-118">在处理一批 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时，驱动程序也不支持在批处理中第一个语句后的语句中的参数标记上调用 SQLDescribeParam。</span><span class="sxs-lookup"><span data-stu-id="c40a1-118">When processing a batch of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the driver also does not support calling SQLDescribeParam for parameter markers in statements after the first statement in the batch.</span></span>  
  
 <span data-ttu-id="c40a1-119">当描述已准备的存储过程的参数时，SQLDescribeParam 将使用系统存储过程[sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql)来检索参数特征。</span><span class="sxs-lookup"><span data-stu-id="c40a1-119">When describing the parameters of prepared stored procedures, SQLDescribeParam uses the system stored procedure [sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql) to retrieve parameter characteristics.</span></span> <span data-ttu-id="c40a1-120">sp_sproc_columns 可以报告当前用户数据库中的存储过程的数据。</span><span class="sxs-lookup"><span data-stu-id="c40a1-120">sp_sproc_columns can report data for stored procedures within the current user database.</span></span> <span data-ttu-id="c40a1-121">准备完全限定的存储过程名称可使 SQLDescribeParam 跨数据库执行。</span><span class="sxs-lookup"><span data-stu-id="c40a1-121">Preparing a fully qualified stored procedure name allows SQLDescribeParam to execute across databases.</span></span> <span data-ttu-id="c40a1-122">例如，可以在任何数据库中准备和执行系统存储过程[sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c40a1-122">For example, the system stored procedure [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) can be prepared and executed in any database as:</span></span>  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 <span data-ttu-id="c40a1-123">成功完成后执行 SQLDescribeParam 将返回连接到任何数据库时的空行集 `master` 。</span><span class="sxs-lookup"><span data-stu-id="c40a1-123">Executing SQLDescribeParam after successful preparation returns an empty row set when connected to any database but `master`.</span></span> <span data-ttu-id="c40a1-124">如下所示的相同调用会导致 SQLDescribeParam 成功，而不考虑当前用户数据库：</span><span class="sxs-lookup"><span data-stu-id="c40a1-124">The same call, prepared as follows, causes SQLDescribeParam to succeed regardless of the current user database:</span></span>  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 <span data-ttu-id="c40a1-125">对于大值数据类型，在*DataTypePtr*中返回的值为 SQL_VARCHAR、SQL_VARBINARY 或 SQL_NVARCHAR。</span><span class="sxs-lookup"><span data-stu-id="c40a1-125">For large value data types, the value returned in *DataTypePtr* is SQL_VARCHAR, SQL_VARBINARY, or SQL_NVARCHAR.</span></span> <span data-ttu-id="c40a1-126">若要指示大值数据类型参数的大小为 "无限制"，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驱动程序将*ParameterSizePtr*设置为0。</span><span class="sxs-lookup"><span data-stu-id="c40a1-126">To indicate that the size of the large value data type parameter is "unlimited," the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sets *ParameterSizePtr* to 0.</span></span> <span data-ttu-id="c40a1-127">将返回标准 `varchar` 参数的实际大小值。</span><span class="sxs-lookup"><span data-stu-id="c40a1-127">Actual size values are returned for standard `varchar` parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c40a1-128">对于 SQL_VARCHAR、SQL_VARBINARY 或 SQL_WVARCHAR 参数，如果参数绑定有最大大小，则返回该参数的绑定大小，而非“无限制”。</span><span class="sxs-lookup"><span data-stu-id="c40a1-128">If the parameter has already been bound with a maximum size for the SQL_VARCHAR, SQL_VARBINARY, or SQL_WVARCHAR parameters, the bound size of the parameter is returned, not "unlimited."</span></span>  
  
 <span data-ttu-id="c40a1-129">若要绑定大小“无限制”的输入参数，必须使用执行时数据。</span><span class="sxs-lookup"><span data-stu-id="c40a1-129">To bind an "unlimited" size input parameter, data-at-execution must be used.</span></span> <span data-ttu-id="c40a1-130">不能绑定 "无限制" 大小的输出参数 (没有用于从 output 参数流式处理数据的方法，例如[SQLGetData](sqlgetdata.md)对结果集) 。</span><span class="sxs-lookup"><span data-stu-id="c40a1-130">It is not possible to bind an "unlimited" size output parameter (there is no method for streaming data from an output parameter, like [SQLGetData](sqlgetdata.md) does for result sets).</span></span>  
  
 <span data-ttu-id="c40a1-131">对于输出参数，必须绑定一个缓冲区，如果值过大，则填充此缓冲区，并返回 SQL_SUCCESS_WITH_INFO 消息和“字符串数据；右端被截断”的警告。</span><span class="sxs-lookup"><span data-stu-id="c40a1-131">For output parameters, a buffer must be bound and if the value is too large, the buffer is filled and a SQL_SUCCESS_WITH_INFO message and is returned along with the "string data; right truncation" warning.</span></span> <span data-ttu-id="c40a1-132">随后将放弃截断的数据。</span><span class="sxs-lookup"><span data-stu-id="c40a1-132">The data that was truncated is then discarded.</span></span>  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a><span data-ttu-id="c40a1-133">SQLDescribeParam 和表值函数</span><span class="sxs-lookup"><span data-stu-id="c40a1-133">SQLDescribeParam and Table-Valued Parameters</span></span>  
 <span data-ttu-id="c40a1-134">应用程序可以使用 SQLDescribeParam 检索预定义语句的表值参数信息。</span><span class="sxs-lookup"><span data-stu-id="c40a1-134">An application can retrieve table-valued parameter information for a prepared statement with SQLDescribeParam.</span></span> <span data-ttu-id="c40a1-135">有关详细信息，请参阅[预定义语句的表值参数元数据](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-135">For more information, see [Table-Valued Parameter Metadata for Prepared Statements](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).</span></span>  
  
 <span data-ttu-id="c40a1-136">有关通常情况下的表值参数的详细信息，请参阅[ODBC&#41;&#40;表值参数](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-136">For more information about table-valued parameters in general, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="c40a1-137">SQLDescribeParam 对日期和时间增强功能的支持</span><span class="sxs-lookup"><span data-stu-id="c40a1-137">SQLDescribeParam Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="c40a1-138">日期/时间类型返回以下值：</span><span class="sxs-lookup"><span data-stu-id="c40a1-138">The values returned for date/time types are as follows:</span></span>  
  
||<span data-ttu-id="c40a1-139">*DataTypePtr*</span><span class="sxs-lookup"><span data-stu-id="c40a1-139">*DataTypePtr*</span></span>|<span data-ttu-id="c40a1-140">*ParameterSizePtr*</span><span class="sxs-lookup"><span data-stu-id="c40a1-140">*ParameterSizePtr*</span></span>|<span data-ttu-id="c40a1-141">*DecimalDigitsPtr*</span><span class="sxs-lookup"><span data-stu-id="c40a1-141">*DecimalDigitsPtr*</span></span>|  
|-|-------------------|------------------------|------------------------|  
|<span data-ttu-id="c40a1-142">datetime</span><span class="sxs-lookup"><span data-stu-id="c40a1-142">datetime</span></span>|<span data-ttu-id="c40a1-143">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c40a1-143">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c40a1-144">23</span><span class="sxs-lookup"><span data-stu-id="c40a1-144">23</span></span>|<span data-ttu-id="c40a1-145">3</span><span class="sxs-lookup"><span data-stu-id="c40a1-145">3</span></span>|  
|<span data-ttu-id="c40a1-146">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="c40a1-146">smalldatetime</span></span>|<span data-ttu-id="c40a1-147">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c40a1-147">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c40a1-148">16</span><span class="sxs-lookup"><span data-stu-id="c40a1-148">16</span></span>|<span data-ttu-id="c40a1-149">0</span><span class="sxs-lookup"><span data-stu-id="c40a1-149">0</span></span>|  
|<span data-ttu-id="c40a1-150">date</span><span class="sxs-lookup"><span data-stu-id="c40a1-150">date</span></span>|<span data-ttu-id="c40a1-151">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="c40a1-151">SQL_TYPE_DATE</span></span>|<span data-ttu-id="c40a1-152">10</span><span class="sxs-lookup"><span data-stu-id="c40a1-152">10</span></span>|<span data-ttu-id="c40a1-153">0</span><span class="sxs-lookup"><span data-stu-id="c40a1-153">0</span></span>|  
|<span data-ttu-id="c40a1-154">time</span><span class="sxs-lookup"><span data-stu-id="c40a1-154">time</span></span>|<span data-ttu-id="c40a1-155">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="c40a1-155">SQL_SS_TIME2</span></span>|<span data-ttu-id="c40a1-156">8, 10..16</span><span class="sxs-lookup"><span data-stu-id="c40a1-156">8, 10..16</span></span>|<span data-ttu-id="c40a1-157">0..7</span><span class="sxs-lookup"><span data-stu-id="c40a1-157">0..7</span></span>|  
|<span data-ttu-id="c40a1-158">datetime2</span><span class="sxs-lookup"><span data-stu-id="c40a1-158">datetime2</span></span>|<span data-ttu-id="c40a1-159">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c40a1-159">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c40a1-160">19、21..27</span><span class="sxs-lookup"><span data-stu-id="c40a1-160">19, 21..27</span></span>|<span data-ttu-id="c40a1-161">0..7</span><span class="sxs-lookup"><span data-stu-id="c40a1-161">0..7</span></span>|  
|<span data-ttu-id="c40a1-162">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="c40a1-162">datetimeoffset</span></span>|<span data-ttu-id="c40a1-163">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="c40a1-163">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="c40a1-164">26、28..34</span><span class="sxs-lookup"><span data-stu-id="c40a1-164">26, 28..34</span></span>|<span data-ttu-id="c40a1-165">0..7</span><span class="sxs-lookup"><span data-stu-id="c40a1-165">0..7</span></span>|  
  
 <span data-ttu-id="c40a1-166">有关详细信息，请参阅[ODBC&#41;&#40;日期和时间改进](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-166">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a><span data-ttu-id="c40a1-167">SQLDescribeParam 对大型 CLR UDT 的支持</span><span class="sxs-lookup"><span data-stu-id="c40a1-167">SQLDescribeParam Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="c40a1-168">`SQLDescribeParam` 支持大型 CLR 用户定义类型 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-168">`SQLDescribeParam` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="c40a1-169">有关详细信息，请参阅[&#40;ODBC&#41;的大型 CLR 用户定义类型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c40a1-169">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40a1-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c40a1-170">See Also</span></span>  
 <span data-ttu-id="c40a1-171">[SQLDescribeParam 函数](https://go.microsoft.com/fwlink/?LinkId=59339) </span><span class="sxs-lookup"><span data-stu-id="c40a1-171">[SQLDescribeParam Function](https://go.microsoft.com/fwlink/?LinkId=59339) </span></span>  
 [<span data-ttu-id="c40a1-172">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="c40a1-172">ODBC API Implementation Details</span></span>](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
