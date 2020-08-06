---
title: 从 ODBC)  (的程序变量进行大容量复制数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bulk copy [ODBC]
ms.assetid: 0c3f2d7c-4ff2-4887-adfd-1f488a27c21c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6e1c5294611b280aea8e67963613971f2690c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693836"
---
# <a name="bulk-copy-data-from-program-variables-odbc"></a><span data-ttu-id="fd98c-102">从程序变量大容量复制数据 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="fd98c-102">Bulk Copy Data from Program Variables (ODBC)</span></span>
  <span data-ttu-id="fd98c-103">此示例演示如何通过 `bcp_bind` 和 `bcp_sendrow` 使用大容量复制函数将数据从程序变量大容量复制到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fd98c-103">This sample shows how to use bulk copy functions to bulk copy data from program variables to SQL Server using `bcp_bind` and `bcp_sendrow`.</span></span> <span data-ttu-id="fd98c-104">（为简化此示例，已删除错误检查代码。）</span><span class="sxs-lookup"><span data-stu-id="fd98c-104">(Error-checking code is removed to simplify this example.)</span></span>  
  
 <span data-ttu-id="fd98c-105">此示例是面向 ODBC 3.0 版或更高版本开发的。</span><span class="sxs-lookup"><span data-stu-id="fd98c-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="fd98c-106">**安全说明**如果可能，请使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="fd98c-106">**Security Note** When possible, use Windows Authentication.</span></span> <span data-ttu-id="fd98c-107">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="fd98c-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="fd98c-108">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="fd98c-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="fd98c-109">如果必须保存凭据，应当用 [Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) 对它们加密。</span><span class="sxs-lookup"><span data-stu-id="fd98c-109">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
### <a name="to-use-bulk-copy-functions-directly-on-program-variables"></a><span data-ttu-id="fd98c-110">直接在程序变量上使用大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="fd98c-110">To use bulk copy functions directly on program variables</span></span>  
  
1.  <span data-ttu-id="fd98c-111">分配环境句柄和连接句柄。</span><span class="sxs-lookup"><span data-stu-id="fd98c-111">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="fd98c-112">设置 SQL_COPT_SS_BCP 和 SQL_BCP_ON 以启用大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="fd98c-112">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="fd98c-113">连接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fd98c-113">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="fd98c-114">调用[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以设置以下信息：</span><span class="sxs-lookup"><span data-stu-id="fd98c-114">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="fd98c-115">作为大容量复制的源或目标的表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="fd98c-115">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="fd98c-116">将数据文件的名称指定为 NULL。</span><span class="sxs-lookup"><span data-stu-id="fd98c-116">Specify NULL for the name of the data file.</span></span>  
  
    -   <span data-ttu-id="fd98c-117">用于接收任何大容量复制错误消息的数据文件的名称（如果不想要消息文件，则指定 NULL）。</span><span class="sxs-lookup"><span data-stu-id="fd98c-117">The name of an data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="fd98c-118">副本的方向：DB_IN 从应用程序到视图或表，或 DB_OUT 从表或视图到应用程序。</span><span class="sxs-lookup"><span data-stu-id="fd98c-118">The direction of the copy: DB_IN from the application to the view or table or DB_OUT to the application from the table or view.</span></span>  
  
5.  <span data-ttu-id="fd98c-119">为大容量复制中的每个列调用[bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) ，以将列绑定到程序变量。</span><span class="sxs-lookup"><span data-stu-id="fd98c-119">Call [bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for each column in the bulk copy to bind the column to a program variable.</span></span>  
  
6.  <span data-ttu-id="fd98c-120">使用数据填充程序变量，并调用[bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)发送一行数据。</span><span class="sxs-lookup"><span data-stu-id="fd98c-120">Fill the program variables with data, and call [bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) to send a row of data.</span></span>  
  
7.  <span data-ttu-id="fd98c-121">在发送若干行后，调用[bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)以检查已发送行的检查点。</span><span class="sxs-lookup"><span data-stu-id="fd98c-121">After several rows have been sent, call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) to checkpoint the rows already sent.</span></span> <span data-ttu-id="fd98c-122">最好至少为每1000行调用一次[bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) 。</span><span class="sxs-lookup"><span data-stu-id="fd98c-122">It is good practice to call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) at least once per 1000 rows.</span></span>  
  
8.  <span data-ttu-id="fd98c-123">发送完所有行后，调用[bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)以完成操作。</span><span class="sxs-lookup"><span data-stu-id="fd98c-123">After all rows have been sent, call [bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) to complete the operation.</span></span>  
  
 <span data-ttu-id="fd98c-124">在大容量复制操作期间，可以通过调用[bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)和[bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)，改变程序变量的位置和长度。</span><span class="sxs-lookup"><span data-stu-id="fd98c-124">You can vary the location and length of program variables during a bulk copy operation by calling [bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) and [bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md).</span></span> <span data-ttu-id="fd98c-125">使用[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)设置各种大容量复制选项。</span><span class="sxs-lookup"><span data-stu-id="fd98c-125">Use [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) to set various bulk copy options.</span></span> <span data-ttu-id="fd98c-126">使用[bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)将 `text` `ntext` 段中的、和数据发送 `image` 到服务器。</span><span class="sxs-lookup"><span data-stu-id="fd98c-126">Use [bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) to send `text`, `ntext`, and `image` data in segments to the server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd98c-127">示例</span><span class="sxs-lookup"><span data-stu-id="fd98c-127">Example</span></span>  
 <span data-ttu-id="fd98c-128">IA64 平台不支持此示例。</span><span class="sxs-lookup"><span data-stu-id="fd98c-128">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="fd98c-129">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="fd98c-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="fd98c-130"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="fd98c-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="fd98c-131">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="fd98c-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="fd98c-132">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="fd98c-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="fd98c-133">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="fd98c-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="fd98c-134">默认情况下，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="fd98c-134">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="fd98c-135">执行第一个 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 代码列表，以创建该示例将使用的表。</span><span class="sxs-lookup"><span data-stu-id="fd98c-135">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create tables that the sample will use.</span></span>  
  
 <span data-ttu-id="fd98c-136">使用 odbc32.lib 和 odbcbcp.lib 编译第二个 (C++) 代码列表。</span><span class="sxs-lookup"><span data-stu-id="fd98c-136">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="fd98c-137">如果用 MSBuild.exe 生成示例，请先将 Bcpfmt.fmt 和 Bcpodbc.bcp 从项目目录复制到 .exe 文件所在的目录，然后调用 .exe。</span><span class="sxs-lookup"><span data-stu-id="fd98c-137">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="fd98c-138">执行第三个 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 代码列表，以删除该示例使用的表。</span><span class="sxs-lookup"><span data-stu-id="fd98c-138">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the tables that the sample used.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
  
CREATE TABLE BCPSource (cola int PRIMARY KEY, colb CHAR(10) NULL)  
INSERT INTO BCPSource (cola, colb) VALUES (1, 'aaa')  
INSERT INTO BCPSource (cola, colb) VALUES (2, 'bbb')  
CREATE TABLE BCPTarget (cola int PRIMARY KEY, colb CHAR(10) NULL)  
```  
  
```  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC, hdbc2 = SQL_NULL_HDBC;  
SQLHSTMT hstmt2 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt2 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (hdbc2 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc2);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // BCP variables.  
   char *terminator = "\0";  
  
   // bcp_done takes a different format return code because it returns number of rows bulk copied  
   // after the last bcp_batch call.  
   DBINT cRowsDone = 0;  
  
   // Set up separate return code for bcp_sendrow so it is not using the same retcode as SQLFetch.  
   RETCODE SendRet;  
  
   // Column variables.  cbCola and cbColb must be defined right before Cola and szColb because   
   // they are used as bulk copy indicator variables.  
   struct ColaData {  
      int cbCola;  
      SQLINTEGER Cola;  
   } ColaInst;  
  
   struct ColbData {  
      int cbColb;  
      SQLCHAR szColb[11];  
   } ColbInst;  
  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // sample uses Integrated Security, create the SQL Server DSN using Windows NT authentication  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "AdventureWorks..BCPTarget", NULL, NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the program variables for the bulk copy.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColaInst.cbCola, 4, SQL_VARLEN_DATA, NULL, (INT)NULL, SQLINT4, 1);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Could normally use strlen to calculate the bcp_bind cbTerm parameter, but this terminator   
   // is a null byte (\0), which gives strlen a value of 0. Explicitly give cbTerm a value of 1.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColbInst.cbColb, 4, 11, (UCHAR*)terminator, 1, SQLCHARACTER, 2);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate second ODBC connection handle so bulk copy and cursor operations do not conflict.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc2, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate ODBC statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
SQLLEN lDataLengthA;  
SQLLEN lDataLengthB;  
  
   // Bind the SELECT statement to the same program variables bound to the bulk copy operation.  
   retcode = SQLBindCol(hstmt2, 1, SQL_C_SLONG, &ColaInst.Cola, 0, &lDataLengthA);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLBindCol(hstmt2, 2, SQL_C_CHAR, &ColbInst.szColb, 11, &lDataLengthB);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute SELECT statement to build a cursor containing data to be bulk copied to new table.  
   retcode = SQLExecDirect(hstmt2, (UCHAR*)"SELECT * FROM BCPSource", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
   // Go into a loop fetching rows from the cursor until each row is fetched. Because the   
   // bcp_bind calls and SQLBindCol calls each reference the same variables, each fetch fills   
   // the variables used by bcp_sendrow, so all you have to do to send the data to SQL Server is   
   // to call bcp_sendrow.  
   while ( (retcode = SQLFetch(hstmt2) ) != SQL_NO_DATA) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLFetch Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
  
      ColaInst.cbCola = (int)lDataLengthA;  
      ColbInst.cbColb = (int)lDataLengthB;  
  
     if ( (SendRet = bcp_sendrow(hdbc1) ) != SUCCEED ) {  
         printf("bcp_sendrow(hdbc1) Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Signal the end of the bulk copy operation.  
   cRowsDone = bcp_done(hdbc1);  
   if ( (cRowsDone == -1) ) {  
      printf("bcp_done(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied after last bcp_batch call = %d.\n", cRowsDone);  
  
   // Cleanup.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLDisconnect(hdbc2);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd98c-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd98c-139">See Also</span></span>  
 <span data-ttu-id="fd98c-140">[SQL Server ODBC 驱动程序的大容量复制操作指南主题 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="fd98c-140">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="fd98c-141">从程序变量执行大容量复制</span><span class="sxs-lookup"><span data-stu-id="fd98c-141">Bulk Copying from Program Variables</span></span>](../../native-client-odbc-bulk-copy-operations/bulk-copying-from-program-variables.md)  
  
  
