---
title: " (ODBC) 记录长时间运行的查询 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
author: rothja
ms.author: jroth
ms.openlocfilehash: f73dbf6fe8fc4b3dfbbbc0012d14a58614b218dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693297"
---
# <a name="log-long-running-queries-odbc"></a><span data-ttu-id="72310-102">记录长时间运行的查询 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="72310-102">Log Long-Running Queries (ODBC)</span></span>
  <span data-ttu-id="72310-103">此示例显示用于记录长时间运行查询的特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驱动程序的选项。</span><span class="sxs-lookup"><span data-stu-id="72310-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to log long-running queries.</span></span> <span data-ttu-id="72310-104">此示例在运行时将创建 Odbcqry.log，其中包含执行时间超过应用程序所设定间隔的查询的列表。</span><span class="sxs-lookup"><span data-stu-id="72310-104">When run, this sample creates Odbcqry.log, which contains a list of queries whose execution exceeds an interval set by the application.</span></span> <span data-ttu-id="72310-105">IA64 平台不支持此示例。</span><span class="sxs-lookup"><span data-stu-id="72310-105">This sample is not supported on IA64.</span></span> <span data-ttu-id="72310-106">此示例是面向 ODBC 3.0 版或更高版本开发的。</span><span class="sxs-lookup"><span data-stu-id="72310-106">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="72310-107">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="72310-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="72310-108">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="72310-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="72310-109">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="72310-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="72310-110">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="72310-110">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a><span data-ttu-id="72310-111">使用 ODBC 管理器记录长时间运行的查询</span><span class="sxs-lookup"><span data-stu-id="72310-111">To log long-running queries using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="72310-112">在 "**控制面板**" 中，双击 "**管理工具**"，然后双击 " \*\* (ODBC) \*\*中的" 数据源 "。</span><span class="sxs-lookup"><span data-stu-id="72310-112">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="72310-113">（或者，也可以从命令提示符处运行 odbcad32.exe。）</span><span class="sxs-lookup"><span data-stu-id="72310-113">(Alternatively, you can run odbcad32.exe from the command prompt.)</span></span>  
  
2.  <span data-ttu-id="72310-114">单击 "**用户 dsn**"、"**系统 dsn**" 或 "**文件 dsn** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="72310-114">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="72310-115">单击要记录其长时间运行的查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="72310-115">Click the data source for which to log long-running queries.</span></span>  
  
4.  <span data-ttu-id="72310-116">单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="72310-116">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="72310-117">在 Microsoft SQL Server 配置 DSN 向导 "中，导航到具有 **" 将长时间运行的查询保存到日志文件**"的页面。</span><span class="sxs-lookup"><span data-stu-id="72310-117">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Save long-running queries to the log file**.</span></span>  
  
6.  <span data-ttu-id="72310-118">选择 **"将长时间运行的查询保存到日志文件"**。</span><span class="sxs-lookup"><span data-stu-id="72310-118">Select **Save long-running queries to the log file**.</span></span> <span data-ttu-id="72310-119">在该框中，放置应记录长时间运行的查询的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="72310-119">In the box, place the name of the file where the long-running queries should be logged.</span></span> <span data-ttu-id="72310-120">还可以单击 "**浏览**"，浏览文件系统中的查询日志。</span><span class="sxs-lookup"><span data-stu-id="72310-120">Optionally, click **Browse** to browse the file system for the query log.</span></span>  
  
7.  <span data-ttu-id="72310-121">在\*\*长查询时间 (毫秒) \*\*中，设置查询超时间隔（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="72310-121">Set a query time-out interval, in milliseconds, in the **Long query time (milliseconds)** box.</span></span>  
  
### <a name="to-log-long-running-queries-data-programmatically"></a><span data-ttu-id="72310-122">以编程方式记录长时间运行的查询数据</span><span class="sxs-lookup"><span data-stu-id="72310-122">To log long-running queries data programmatically</span></span>  
  
1.  <span data-ttu-id="72310-123">调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_QUERY_LOG 以及长时间运行的查询日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="72310-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_LOG and the full path and file name of the long-running query log file.</span></span> <span data-ttu-id="72310-124">例如：</span><span class="sxs-lookup"><span data-stu-id="72310-124">For example:</span></span>  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  <span data-ttu-id="72310-125">调用 SQL_COPT_SS_PERF_QUERY_INTERVAL [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)并将其设置为超时间隔（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="72310-125">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_INTERVAL and set to the time-out interval, in milliseconds.</span></span>  
  
3.  <span data-ttu-id="72310-126">通过 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_START 调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，开始记录长时间运行的查询。</span><span class="sxs-lookup"><span data-stu-id="72310-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_START to start logging long-running queries.</span></span>  
  
4.  <span data-ttu-id="72310-127">通过 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_STOP 调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以停止记录长时间运行的查询。</span><span class="sxs-lookup"><span data-stu-id="72310-127">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_STOP to stop logging long-running queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72310-128">示例</span><span class="sxs-lookup"><span data-stu-id="72310-128">Example</span></span>  
 <span data-ttu-id="72310-129">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="72310-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="72310-130"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="72310-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="72310-131">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="72310-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="72310-132">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="72310-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="72310-133">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="72310-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="72310-134">默认情况下，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="72310-134">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="72310-135">使用 odbc32.lib 进行编译。</span><span class="sxs-lookup"><span data-stu-id="72310-135">Compile with odbc32.lib.</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
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
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="72310-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72310-136">See Also</span></span>  
 [<span data-ttu-id="72310-137">分析 ODBC 驱动程序性能操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="72310-137">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
  
