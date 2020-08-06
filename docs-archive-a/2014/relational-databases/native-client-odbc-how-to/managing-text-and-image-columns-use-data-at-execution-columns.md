---
title: 在 ODBC)  (使用执行时数据列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data-at-execution
ms.assetid: 4eae58d1-03d4-40ca-8aa1-9b3ea10a38cf
author: rothja
ms.author: jroth
ms.openlocfilehash: 68690208b690f94909100132c966eb59d11e4652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692384"
---
# <a name="use-data-at-execution-columns-odbc"></a><span data-ttu-id="db537-102">如用执行时数据列 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="db537-102">Use Data-at-Execution Columns (ODBC)</span></span>
    
### <a name="to-use-data-at-execution-text-ntext-or-image-columns"></a><span data-ttu-id="db537-103">使用作为执行时数据的 text、ntext 或 image 列</span><span class="sxs-lookup"><span data-stu-id="db537-103">To use data-at-execution text, ntext, or image columns</span></span>  
  
1.  <span data-ttu-id="db537-104">对于每个执行时数据列，请将特殊值放到以前通过 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) 绑定的缓冲区中：</span><span class="sxs-lookup"><span data-stu-id="db537-104">For each data-at-execution column, put special values into the buffers previously bound by [SQLBindCol](../native-client-odbc-api/sqlbindcol.md):</span></span>  
  
    -   <span data-ttu-id="db537-105">对于最后一个参数，请使用 SQL_LEN_DATA_AT_EXEC(length)，其中，length 是以字节为单位的 text、ntext 或 image 列数据的总计长度。</span><span class="sxs-lookup"><span data-stu-id="db537-105">For the last parameter, use SQL_LEN_DATA_AT_EXEC(length) where length is the total length of the text, ntext, or image column data in bytes.</span></span>  
  
    -   <span data-ttu-id="db537-106">对于第四个参数，请放入程序定义的列标识符。</span><span class="sxs-lookup"><span data-stu-id="db537-106">For the fourth parameter, put a program-defined column identifier.</span></span>  
  
2.  <span data-ttu-id="db537-107">调用 [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) 将返回 SQL_NEED_DATA，该值指示执行时数据列已经可供处理。</span><span class="sxs-lookup"><span data-stu-id="db537-107">Calling [SQLSetPos](https://go.microsoft.com/fwlink/?LinkId=58407) returns SQL_NEED_DATA, which indicates that data-at-execution columns are ready for processing.</span></span>  
  
3.  <span data-ttu-id="db537-108">对于每个执行时数据列：</span><span class="sxs-lookup"><span data-stu-id="db537-108">For each data-at-execution column:</span></span>  
  
    -   <span data-ttu-id="db537-109">调用 [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 以获得列数组指针。</span><span class="sxs-lookup"><span data-stu-id="db537-109">Call [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) to get the column array pointer.</span></span> <span data-ttu-id="db537-110">如果存在另一个执行时数据列，它将返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="db537-110">It will return SQL_NEED_DATA if there is another data-at-execution column.</span></span>  
  
    -   <span data-ttu-id="db537-111">调用 [SQLPutData](../native-client-odbc-api/sqlputdata.md) 一次或多次以发送列数据，直到 length 已发送。</span><span class="sxs-lookup"><span data-stu-id="db537-111">Call [SQLPutData](../native-client-odbc-api/sqlputdata.md) one or more times to send the column data, until length is sent.</span></span>  
  
4.  <span data-ttu-id="db537-112">调用 [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 以指示最后一个执行时数据列的所有数据已发送。</span><span class="sxs-lookup"><span data-stu-id="db537-112">Call [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) to indicate that all the data for the final data-at-execution column is sent.</span></span> <span data-ttu-id="db537-113">它不会返回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="db537-113">It will not return SQL_NEED_DATA.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db537-114">示例</span><span class="sxs-lookup"><span data-stu-id="db537-114">Example</span></span>  
 <span data-ttu-id="db537-115">此示例显示如何使用 SQLGetData 读取 SQL_LONG 变量字符数据。</span><span class="sxs-lookup"><span data-stu-id="db537-115">The sample shows how to read a SQL_LONG variable character data using SQLGetData.</span></span> <span data-ttu-id="db537-116">IA64 平台不支持此示例。</span><span class="sxs-lookup"><span data-stu-id="db537-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="db537-117">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="db537-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="db537-118"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="db537-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="db537-119">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="db537-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="db537-120">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="db537-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="db537-121">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="db537-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="db537-122">默认情况下，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="db537-122">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="db537-123">执行第一个 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 代码列表，以创建该示例使用的表。</span><span class="sxs-lookup"><span data-stu-id="db537-123">Execute the first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to create the table used by the sample.</span></span>  
  
 <span data-ttu-id="db537-124">使用 odbc32.lib 编译第二个 (C++) 代码列表。</span><span class="sxs-lookup"><span data-stu-id="db537-124">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="db537-125">然后，执行该程序。</span><span class="sxs-lookup"><span data-stu-id="db537-125">Then execute the program.</span></span>  
  
 <span data-ttu-id="db537-126">执行第三个 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 代码列表，以删除该示例使用的表。</span><span class="sxs-lookup"><span data-stu-id="db537-126">Execute the third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to delete the table used by the sample.</span></span>  
  
```  
use AdventureWorks  
CREATE TABLE emp3 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
INSERT INTO emp3 (NAME, AGE, Memo1) VALUES   ('Name1', '12', 'This is the first employee')  
INSERT INTO emp3 (NAME, AGE, Memo1) VALUES   ('Name2', '18', 'This is the second employee')  
```  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define BUFFERSIZE  450  
  
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
};  
  
int main() {  
   RETCODE retcode;  
   SWORD cntr;  
  
   // SQLGetData variables.  
   UCHAR Data[BUFFERSIZE];  
   SDWORD cbBatch = (SDWORD)sizeof(Data)-1;  
   SQLLEN cbTxtSize;  
  
   // Clear data array.  
   for (cntr = 0 ; cntr < BUFFERSIZE ; cntr++)  
      Data[cntr] = 0x00;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
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
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle; prepare, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT Memo1 FROM emp3", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get first row.  
   retcode = SQLFetch(hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLFetch(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get the SQL_LONG column.  
   cntr = 1;  
   while ( (retcode = SQLGetData(hstmt1, 1, SQL_C_CHAR, Data, cbBatch, &cbTxtSize)) != SQL_NO_DATA) {  
      printf("GetData iteration %d, pcbValue = %d,\n", cntr++, cbTxtSize);  
      printf("Data = %s\n\n", Data);  
  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("GetData(hstmt1) Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }   
  
   // Clean up  
   //SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'emp3')  
     DROP TABLE emp3  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="db537-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db537-127">See Also</span></span>  
 [<span data-ttu-id="db537-128">管理文本和图像列操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="db537-128">Managing text and image Columns How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/managing-text-and-image-columns-how-to-topics-odbc.md)  
  
  
