---
title: 处理生成消息的语句 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: rothja
ms.author: jroth
ms.openlocfilehash: c26376eabb756d356dd71fb3bd8284a6b11dced7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688903"
---
# <a name="processing-statements-that-generate-messages"></a><span data-ttu-id="83398-102">处理生成消息的语句</span><span class="sxs-lookup"><span data-stu-id="83398-102">Processing Statements That Generate Messages</span></span>
  <span data-ttu-id="83398-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] SET 语句选项 STATISTICS TIME 和 STATISTICS IO 用于获取有助于诊断长时间运行的查询的信息。</span><span class="sxs-lookup"><span data-stu-id="83398-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement options STATISTICS TIME and STATISTICS IO are used to get information that aids in diagnosing long-running queries.</span></span> <span data-ttu-id="83398-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本还支持用于分析查询计划的 SHOWPLAN 选项。</span><span class="sxs-lookup"><span data-stu-id="83398-104">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also support the SHOWPLAN option for analyzing query plans.</span></span> <span data-ttu-id="83398-105">ODBC 应用程序可通过执行以下语句设置这些选项：</span><span class="sxs-lookup"><span data-stu-id="83398-105">An ODBC application can set these options by executing the following statements:</span></span>  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 <span data-ttu-id="83398-106">当 SET STATISTICS TIME 或 SET 显示计划处于开启状态时， **SQLExecute**和**SQLExecDirect**将返回 SQL_SUCCESS_WITH_INFO，此时，应用程序可以通过调用**SQLGetDiagRec**来检索显示计划或统计信息时间输出，直到返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="83398-106">When SET STATISTICS TIME or SET SHOWPLAN are ON, **SQLExecute** and **SQLExecDirect** return SQL_SUCCESS_WITH_INFO, and, at that point, the application can retrieve the SHOWPLAN or STATISTICS TIME output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="83398-107">SHOWPLAN 数据的每一行均按以下格式返回：</span><span class="sxs-lookup"><span data-stu-id="83398-107">Each line of SHOWPLAN data comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="83398-108">7.0 版将 SHOWPLAN 选项替换为 SHOWPLAN_ALL 和 SHOWPLAN_TEXT，后两个选项均将输出作为结果集（而不是一组消息）返回。</span><span class="sxs-lookup"><span data-stu-id="83398-108">version 7.0 replaced the SHOWPLAN option with SHOWPLAN_ALL and SHOWPLAN_TEXT, both of which return output as a result set, not a set of messages.</span></span>  
  
 <span data-ttu-id="83398-109">STATISTICS TIME 的每一行均按以下格式返回：</span><span class="sxs-lookup"><span data-stu-id="83398-109">Each line of STATISTICS TIME comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 <span data-ttu-id="83398-110">在到达结果集的末尾之前，SET STATISTICS IO 的输出不可用。</span><span class="sxs-lookup"><span data-stu-id="83398-110">The output of SET STATISTICS IO is not available until the end of a result set.</span></span> <span data-ttu-id="83398-111">若要获取统计信息 IO 输出，应用程序会在**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)返回 SQL_NO_DATA 时调用**SQLGetDiagRec** 。</span><span class="sxs-lookup"><span data-stu-id="83398-111">To get STATISTICS IO output, the application calls **SQLGetDiagRec** at the time **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="83398-112">STATISTICS IO 的输出按以下格式返回：</span><span class="sxs-lookup"><span data-stu-id="83398-112">The output of STATISTICS IO comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a><span data-ttu-id="83398-113">使用 DBCC 语句</span><span class="sxs-lookup"><span data-stu-id="83398-113">Using DBCC Statements</span></span>  
 <span data-ttu-id="83398-114">DBCC 语句将其数据作为消息（而不是结果集）返回。</span><span class="sxs-lookup"><span data-stu-id="83398-114">DBCC statements return their data as messages, not result sets.</span></span> <span data-ttu-id="83398-115">**SQLExecDirect**或**SQLExecute**返回 SQL_SUCCESS_WITH_INFO，应用程序将通过调用**SQLGetDiagRec**来检索输出，直到返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="83398-115">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and the application retrieves the output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="83398-116">例如，下面的语句返回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="83398-116">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 <span data-ttu-id="83398-117">对**SQLGetDiagRec**的调用返回：</span><span class="sxs-lookup"><span data-stu-id="83398-117">Calls to **SQLGetDiagRec** return:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a><span data-ttu-id="83398-118">使用 PRINT 和 RAISERROR 语句</span><span class="sxs-lookup"><span data-stu-id="83398-118">Using PRINT and RAISERROR Statements</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="83398-119">PRINT 和 RAISERROR 语句还通过调用**SQLGetDiagRec**返回数据。</span><span class="sxs-lookup"><span data-stu-id="83398-119">PRINT and RAISERROR statements also return data by calling **SQLGetDiagRec**.</span></span> <span data-ttu-id="83398-120">PRINT 语句使 SQL 语句执行返回 SQL_SUCCESS_WITH_INFO，并对**SQLGetDiagRec**的后续调用返回*SQLState* 01000。</span><span class="sxs-lookup"><span data-stu-id="83398-120">PRINT statements cause the SQL statement execution to return SQL_SUCCESS_WITH_INFO, and a subsequent call to **SQLGetDiagRec** returns a *SQLState* of 01000.</span></span> <span data-ttu-id="83398-121">严重性为 10 或更低的 RAISERROR 在行为上与 PRINT 相同。</span><span class="sxs-lookup"><span data-stu-id="83398-121">A RAISERROR with a severity of ten or lower behaves the same as PRINT.</span></span> <span data-ttu-id="83398-122">严重性为11或更高的 RAISERROR 导致 execute 返回 SQL_ERROR，对**SQLGetDiagRec**的后续调用会返回*SQLState* 42000。</span><span class="sxs-lookup"><span data-stu-id="83398-122">A RAISERROR with a severity of 11 or higher causes the execute to return SQL_ERROR, and a subsequent call to **SQLGetDiagRec** returns *SQLState* 42000.</span></span> <span data-ttu-id="83398-123">例如，下面的语句返回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="83398-123">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 <span data-ttu-id="83398-124">调用**SQLGetDiagRec**将返回：</span><span class="sxs-lookup"><span data-stu-id="83398-124">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 <span data-ttu-id="83398-125">下面的语句返回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="83398-125">The following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 <span data-ttu-id="83398-126">调用**SQLGetDiagRec**将返回：</span><span class="sxs-lookup"><span data-stu-id="83398-126">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 <span data-ttu-id="83398-127">下面的语句返回 SQL_ERROR：</span><span class="sxs-lookup"><span data-stu-id="83398-127">The following statement returns SQL_ERROR:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 <span data-ttu-id="83398-128">调用**SQLGetDiagRec**将返回：</span><span class="sxs-lookup"><span data-stu-id="83398-128">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 <span data-ttu-id="83398-129">在结果集中包含 PRINT 或 RAISERROR 语句的输出时，调用**SQLGetDiagRec**的时间是至关重要的。</span><span class="sxs-lookup"><span data-stu-id="83398-129">The timing of calling **SQLGetDiagRec** is critical when output from PRINT or RAISERROR statements is included in a result set.</span></span> <span data-ttu-id="83398-130">若**要检索**PRINT 或 RAISERROR 输出，必须在接收 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 的语句之后立即调用。</span><span class="sxs-lookup"><span data-stu-id="83398-130">The call to **SQLGetDiagRec** to retrieve the PRINT or RAISERROR output must be made immediately after the statement that receives SQL_ERROR or SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="83398-131">当仅执行一个 SQL 语句时（如上述示例中所示），这非常简单。</span><span class="sxs-lookup"><span data-stu-id="83398-131">This is straightforward when only a single SQL statement is executed, as in the examples above.</span></span> <span data-ttu-id="83398-132">在这些情况下，对**SQLExecDirect**或**SQLExecute**的调用将返回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO，然后可以调用**SQLGetDiagRec** 。</span><span class="sxs-lookup"><span data-stu-id="83398-132">In these cases, the call to **SQLExecDirect** or **SQLExecute** returns SQL_ERROR or SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** can then be called.</span></span> <span data-ttu-id="83398-133">当编写循环代码以处理一批 SQL 语句的输出或者当执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程时，这要复杂一些。</span><span class="sxs-lookup"><span data-stu-id="83398-133">It is less straightforward when coding loops to handle the output of a batch of SQL statements or when executing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="83398-134">在这种情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为在批处理或存储过程中执行的每个 SELECT 语句返回一个结果集。</span><span class="sxs-lookup"><span data-stu-id="83398-134">In this case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns a result set for every SELECT statement executed in a batch or stored procedure.</span></span> <span data-ttu-id="83398-135">如果批处理或过程包含 PRINT 或 RAISERROR 语句，它们的输出将与 SELECT 语句结果集交叉。</span><span class="sxs-lookup"><span data-stu-id="83398-135">If the batch or procedure contains PRINT or RAISERROR statements, the output for these is interleaved with the SELECT statement result sets.</span></span> <span data-ttu-id="83398-136">如果批处理或过程中的第一条语句是 PRINT 或 RAISERROR，则**SQLExecute**或**SQLExecDirect**返回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，应用程序需要调用**SQLGetDiagRec** ，直到它返回 SQL_NO_DATA 检索打印或 RAISERROR 信息。</span><span class="sxs-lookup"><span data-stu-id="83398-136">If the first statement in the batch or procedure is a PRINT or RAISERROR, the **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, and the application needs to call **SQLGetDiagRec** until it returns SQL_NO_DATA to retrieve the PRINT or RAISERROR information.</span></span>  
  
 <span data-ttu-id="83398-137">如果 PRINT 或 RAISERROR 语句出现在 (如 SELECT 语句) 的 SQL 语句之后，则在包含错误的结果集上[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)位置时，将返回 PRINT 或 RAISERROR 信息。</span><span class="sxs-lookup"><span data-stu-id="83398-137">If the PRINT or RAISERROR statement comes after an SQL statement (such as a SELECT statement), then the PRINT or RAISERROR information is returned when [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)positions on the result set containing the error.</span></span> <span data-ttu-id="83398-138">**SQLMoreResults**根据消息的严重性返回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="83398-138">**SQLMoreResults** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR depending on the severity of the message.</span></span> <span data-ttu-id="83398-139">消息是通过调用**SQLGetDiagRec**来检索的，直到返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="83398-139">Messages are retrieved by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83398-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83398-140">See Also</span></span>  
 [<span data-ttu-id="83398-141">处理错误和消息</span><span class="sxs-lookup"><span data-stu-id="83398-141">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
