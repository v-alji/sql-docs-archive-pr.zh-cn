---
title: " (ODBC) 的配置文件驱动程序性能数据 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: rothja
ms.author: jroth
ms.openlocfilehash: 3575cfd304d526bdb25eee6a2578d67c6bb67bc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688898"
---
# <a name="profile-driver-performance-data-odbc"></a><span data-ttu-id="63be6-102">配置驱动程序性能数据 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="63be6-102">Profile Driver Performance Data (ODBC)</span></span>
  <span data-ttu-id="63be6-103">此示例显示用于记录性能统计信息的特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驱动程序的选项；</span><span class="sxs-lookup"><span data-stu-id="63be6-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to record performance statistics.</span></span> <span data-ttu-id="63be6-104">其中创建了一个文件：odbcperf.log。此示例显示如何直接从 SQLPERF 数据结构（SQLPERF 结构在 Odbcss.h 中定义）创建性能数据日志文件和显示性能数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-104">The sample creates one file: odbcperf.log.This sample shows both the creation of a performance data log file and displaying performance data directly from the SQLPERF data structure (The SQLPERF structure is defined in Odbcss.h.).</span></span> <span data-ttu-id="63be6-105">此示例是面向 ODBC 3.0 版或更高版本开发的。</span><span class="sxs-lookup"><span data-stu-id="63be6-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63be6-106">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="63be6-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="63be6-107">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="63be6-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="63be6-108">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="63be6-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="63be6-109">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="63be6-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a><span data-ttu-id="63be6-110">使用 ODBC 管理器记录驱动程序性能数据</span><span class="sxs-lookup"><span data-stu-id="63be6-110">To log driver performance data using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="63be6-111">在 "**控制面板**" 中，双击 "**管理工具**"，然后双击 " \*\* (ODBC) \*\*中的" 数据源 "。</span><span class="sxs-lookup"><span data-stu-id="63be6-111">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="63be6-112">或者，可以调用 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="63be6-112">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="63be6-113">单击 "**用户 dsn**"、"**系统 dsn**" 或 "**文件 dsn** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="63be6-113">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="63be6-114">单击要记录其性能的数据源。</span><span class="sxs-lookup"><span data-stu-id="63be6-114">Click the data source for which to log performance.</span></span>  
  
4.  <span data-ttu-id="63be6-115">单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="63be6-115">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="63be6-116">在 Microsoft SQL Server 配置 DSN 向导 "中，导航到日志文件中包含" 将**ODBC 驱动程序统计信息记录到**"的页。</span><span class="sxs-lookup"><span data-stu-id="63be6-116">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Log ODBC driver statistics to the log file**.</span></span>  
  
6.  <span data-ttu-id="63be6-117">选择 **"将 ODBC 驱动程序统计信息记录到日志文件"**。</span><span class="sxs-lookup"><span data-stu-id="63be6-117">Select **Log ODBC driver statistics to the log file**.</span></span> <span data-ttu-id="63be6-118">在该框中，放置应记录统计信息的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="63be6-118">In the box, place the name of the file where the statistics should be logged.</span></span> <span data-ttu-id="63be6-119">还可以单击 "**浏览**"，浏览文件系统中的统计信息日志。</span><span class="sxs-lookup"><span data-stu-id="63be6-119">Optionally, click **Browse** to browse the file system for the statistics log.</span></span>  
  
### <a name="to-log-driver-performance-data-programmatically"></a><span data-ttu-id="63be6-120">通过编程方式记录驱动程序性能数据</span><span class="sxs-lookup"><span data-stu-id="63be6-120">To log driver performance data programmatically</span></span>  
  
1.  <span data-ttu-id="63be6-121">调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_DATA_LOG 以及性能数据日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="63be6-121">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA_LOG and the full path and file name of the performance data log file.</span></span> <span data-ttu-id="63be6-122">例如：</span><span class="sxs-lookup"><span data-stu-id="63be6-122">For example:</span></span>  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  <span data-ttu-id="63be6-123">通过 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_START 调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，开始记录性能数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start logging performance data.</span></span>  
  
3.  <span data-ttu-id="63be6-124">（可选）使用 SQL_COPT_SS_LOG_NOW 调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，并将其写入性能数据日志文件中的制表符分隔记录。</span><span class="sxs-lookup"><span data-stu-id="63be6-124">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_LOG_NOW and NULL to write a tab-delimited record of performance data to the performance data log file.</span></span> <span data-ttu-id="63be6-125">此操作可以在应用程序运行时执行多次。</span><span class="sxs-lookup"><span data-stu-id="63be6-125">This can be done multiple times as the application runs.</span></span>  
  
4.  <span data-ttu-id="63be6-126">调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_DATA 和 SQL_PERF_STOP 以停止记录性能数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a><span data-ttu-id="63be6-127">将驱动程序性能数据拖到某一应用程序中</span><span class="sxs-lookup"><span data-stu-id="63be6-127">To pull driver performance data into an application</span></span>  
  
1.  <span data-ttu-id="63be6-128">通过 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_START 调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，开始分析性能数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-128">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start profiling performance data.</span></span>  
  
2.  <span data-ttu-id="63be6-129">使用 SQL_COPT_SS_PERF_DATA 和指向 SQLPERF 结构的指针的地址调用[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="63be6-129">Call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) with SQL_COPT_SS_PERF_DATA and the address of a pointer to a SQLPERF structure.</span></span> <span data-ttu-id="63be6-130">第一个此类调用将设置一个指针，该指针指向包含当前性能数据的有效 SQLPERF 结构的地址。</span><span class="sxs-lookup"><span data-stu-id="63be6-130">The first such call sets the pointer to the address of a valid SQLPERF structure that contains current performance data.</span></span> <span data-ttu-id="63be6-131">驱动程序并不连续刷新该性能结构中的数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-131">The driver does not continually refresh the data in the performance structure.</span></span> <span data-ttu-id="63be6-132">应用程序必须在需要刷新具有更高当前性能数据的结构时，重复调用[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="63be6-132">The application must repeat the call to [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) any time it needs to refresh the structure with more current performance data.</span></span>  
  
3.  <span data-ttu-id="63be6-133">调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) SQL_COPT_SS_PERF_DATA 和 SQL_PERF_STOP 以停止记录性能数据。</span><span class="sxs-lookup"><span data-stu-id="63be6-133">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63be6-134">示例</span><span class="sxs-lookup"><span data-stu-id="63be6-134">Example</span></span>  
 <span data-ttu-id="63be6-135">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="63be6-135">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="63be6-136"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="63be6-136">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="63be6-137">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="63be6-137">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="63be6-138">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="63be6-138">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="63be6-139">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="63be6-139">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="63be6-140">默认情况下，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="63be6-140">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="63be6-141">使用 odbc32.lib 进行编译。</span><span class="sxs-lookup"><span data-stu-id="63be6-141">Compile with odbc32.lib.</span></span>  
  
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
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="63be6-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63be6-142">See Also</span></span>  
 <span data-ttu-id="63be6-143">[分析 ODBC 驱动程序性能操作指南主题 &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="63be6-143">[Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md) </span></span>  
 [<span data-ttu-id="63be6-144">ODBC 驱动程序性能事件探查</span><span class="sxs-lookup"><span data-stu-id="63be6-144">Profiling ODBC Driver Performance</span></span>](../native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
