---
title: " (ODBC) 处理返回代码和输出参数 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- return codes [ODBC]
- output parameters [ODBC]
ms.assetid: 102ae1d0-973d-4e12-992c-d844bf05160d
author: rothja
ms.author: jroth
ms.openlocfilehash: b119d43806dafa68fe049595d94e909a5a1bb896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586627"
---
# <a name="process-return-codes-and-output-parameters-odbc"></a><span data-ttu-id="a4f3a-102">处理返回代码和输出参数 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a4f3a-102">Process Return Codes and Output Parameters (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a4f3a-103">存储过程可具有整数返回代码和输出参数。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-103">stored procedures can have integer return codes and output parameters.</span></span> <span data-ttu-id="a4f3a-104">返回代码和输出参数在服务器的最后一个数据包中发送，在[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)返回 SQL_NO_DATA 之前，这些参数对应用程序不可用。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-104">The return codes and output parameters are sent in the last packet from the server and are not available to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="a4f3a-105">如果在存储过程中返回错误，请调用 SQLMoreResults 以转到下一个结果，直到返回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-105">If an error is returned from a stored procedure, call SQLMoreResults to advance to the next result until SQL_NO_DATA is returned.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4f3a-106">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="a4f3a-107">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="a4f3a-108">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="a4f3a-109">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-process-return-codes-and-output-parameters"></a><span data-ttu-id="a4f3a-110">处理返回代码和输出参数</span><span class="sxs-lookup"><span data-stu-id="a4f3a-110">To process return codes and output parameters</span></span>  
  
1.  <span data-ttu-id="a4f3a-111">构造使用 ODBC CALL 转义序列的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-111">Construct an SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="a4f3a-112">该语句应当对每个输入、输入/输出和输出参数以及过程返回值（如果有）使用参数标记。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-112">The statement should use parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
2.  <span data-ttu-id="a4f3a-113">为每个输入、输入/输出和输出参数调用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) ，并为过程返回值调用，如果有任何)  (。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-113">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="a4f3a-114">用 `SQLExecDirect` 执行语句。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-114">Execute the statement with `SQLExecDirect`.</span></span>  
  
4.  <span data-ttu-id="a4f3a-115">直到 `SQLFetch` 或 `SQLFetchScroll` 在处理最后一个结果集时返回 SQL_NO_DATA 或直到 `SQLMoreResults` 返回 SQL_NO_DATA，才处理结果集。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-115">Process result sets until `SQLFetch` or `SQLFetchScroll` returns SQL_NO_DATA while processing the last result set or until `SQLMoreResults` returns SQL_NO_DATA.</span></span> <span data-ttu-id="a4f3a-116">这时，将以返回的数据值填充绑定到返回代码和输出参数的变量。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-116">At this point, the variables bound to the return code and output parameters are filled with returned data values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f3a-117">示例</span><span class="sxs-lookup"><span data-stu-id="a4f3a-117">Example</span></span>  
 <span data-ttu-id="a4f3a-118">此示例显示如何处理返回代码和输出参数。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-118">This sample shows processing a return code and output parameter.</span></span> <span data-ttu-id="a4f3a-119">IA64 平台不支持此示例。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-119">This sample is not supported on IA64.</span></span> <span data-ttu-id="a4f3a-120">此示例是面向 ODBC 3.0 版或更高版本开发的。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-120">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="a4f3a-121">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-121">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="a4f3a-122"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-122">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="a4f3a-123">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-123">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="a4f3a-124">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-124">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="a4f3a-125">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-125">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="a4f3a-126">默认情况下，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-126">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="a4f3a-127">第一 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 代码列表创建此示例使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-127">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a stored procedure used by this sample.</span></span>  
  
 <span data-ttu-id="a4f3a-128">使用 odbc32.lib 编译第二个 (C++) 代码列表。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-128">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="a4f3a-129">然后，执行该程序。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-129">Then, execute the program.</span></span>  
  
 <span data-ttu-id="a4f3a-130">第三个 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 代码列表删除此示例使用的存储过程。</span><span class="sxs-lookup"><span data-stu-id="a4f3a-130">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the stored procedure used by this sample.</span></span>  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'TestParm')  
   DROP PROCEDURE TestParm  
GO  
  
CREATE PROCEDURE TestParm   
@OutParm int OUTPUT   
AS  
SELECT Name FROM Purchasing.Vendor  
SELECT @OutParm = 88  
RETURN 99  
go  
```  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 255  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   // SQLBindParameter variables.  
   SWORD sParm1 = 0, sParm2 = 1;  
   SQLLEN cbParm1 = SQL_NTS;  
   SQLLEN cbParm2 = SQL_NTS;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Create the SQL Server DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the return code to variable sParm1.  
   retcode = SQLBindParameter(hstmt1, 1, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm1, 0, &cbParm1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the output parameter to variable sParm2.  
   retcode = SQLBindParameter(hstmt1, 2, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm2, 0, &cbParm2);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.   
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"{? = call TestParm(?)}", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Show parameters are not filled.  
   printf("Before result sets cleared: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA )  
      ;  
  
   // Show parameters are now filled.  
   printf("After result sets drained: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clean up.   
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
DROP PROCEDURE TestParm  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4f3a-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4f3a-131">See Also</span></span>  
 [<span data-ttu-id="a4f3a-132">运行存储过程操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="a4f3a-132">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
