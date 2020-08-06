---
title: 使用格式化文件 (ODBC) 进行大容量复制 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
author: rothja
ms.author: jroth
ms.openlocfilehash: 19959d5f1da7243275c60560963d577446f809b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693837"
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a><span data-ttu-id="e13d7-102">使用格式化文件执行大容量复制 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e13d7-102">Bulk Copy by Using a Format File (ODBC)</span></span>
  <span data-ttu-id="e13d7-103">此示例显示如何将 ODBC bcp_init 函数用于格式化文件。</span><span class="sxs-lookup"><span data-stu-id="e13d7-103">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a><span data-ttu-id="e13d7-104">使用格式化文件执行大容量复制</span><span class="sxs-lookup"><span data-stu-id="e13d7-104">To bulk copy by using a format file</span></span>  
  
1.  <span data-ttu-id="e13d7-105">分配环境句柄和连接句柄。</span><span class="sxs-lookup"><span data-stu-id="e13d7-105">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="e13d7-106">设置 SQL_COPT_SS_BCP 和 SQL_BCP_ON 以启用大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="e13d7-106">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="e13d7-107">连接到 Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e13d7-107">Connect to Microsoft SQL Server.</span></span>  
  
4.  <span data-ttu-id="e13d7-108">调用[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以设置以下信息：</span><span class="sxs-lookup"><span data-stu-id="e13d7-108">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="e13d7-109">作为大容量复制的源或目标的表或视图的名称。</span><span class="sxs-lookup"><span data-stu-id="e13d7-109">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="e13d7-110">包含要复制到数据库中的数据的数据文件的名称，或者当从数据库中复制时接收数据的数据文件的名称。</span><span class="sxs-lookup"><span data-stu-id="e13d7-110">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="e13d7-111">接收任何大容量复制错误消息的数据文件的名称（如果您不需要消息文件，请指定 NULL）。</span><span class="sxs-lookup"><span data-stu-id="e13d7-111">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="e13d7-112">复制方向：DB_IN 表示从文件复制到表或视图。</span><span class="sxs-lookup"><span data-stu-id="e13d7-112">The direction of the copy: DB_IN from the file to the table or view.</span></span>  
  
5.  <span data-ttu-id="e13d7-113">调用[bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)读取用于描述大容量复制操作要使用的数据文件的格式化文件。</span><span class="sxs-lookup"><span data-stu-id="e13d7-113">Call [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) to read the format file describing the data file to be used by the bulk copy operation.</span></span>  
  
6.  <span data-ttu-id="e13d7-114">调用[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="e13d7-114">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e13d7-115">示例</span><span class="sxs-lookup"><span data-stu-id="e13d7-115">Example</span></span>  
 <span data-ttu-id="e13d7-116">IA64 平台不支持此示例。</span><span class="sxs-lookup"><span data-stu-id="e13d7-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="e13d7-117">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="e13d7-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="e13d7-118"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="e13d7-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="e13d7-119">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="e13d7-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="e13d7-120">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e13d7-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e13d7-121">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="e13d7-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="e13d7-122">默认情况下，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="e13d7-122">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="e13d7-123">执行第一个 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 代码列表，以创建该示例将使用的表。</span><span class="sxs-lookup"><span data-stu-id="e13d7-123">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="e13d7-124">复制第二个代码列表，并将其粘贴到名为 Bcpfmt.fmt 的文件中。</span><span class="sxs-lookup"><span data-stu-id="e13d7-124">Copy the second code listing and paste it into a file called Bcpfmt.fmt.</span></span> <span data-ttu-id="e13d7-125">表中的每一列均由制表符分隔。</span><span class="sxs-lookup"><span data-stu-id="e13d7-125">Each column in the table is separated by a tab character.</span></span>  
  
 <span data-ttu-id="e13d7-126">复制第三个代码列表，并将其粘贴到名为 Bcpodbc.bcp 的文件中。</span><span class="sxs-lookup"><span data-stu-id="e13d7-126">Copy the third code listing and paste it into a file called Bcpodbc.bcp.</span></span> <span data-ttu-id="e13d7-127">文件中每个回车符之前都有一个制表符。</span><span class="sxs-lookup"><span data-stu-id="e13d7-127">A tab character precedes each carriage return in the file.</span></span>  
  
 <span data-ttu-id="e13d7-128">使用 odbc32.lib 和 odbcbcp.lib 编译第四个 (C++) 代码列表。</span><span class="sxs-lookup"><span data-stu-id="e13d7-128">Compile the fourth (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="e13d7-129">如果用 MSBuild.exe 生成示例，请先将 Bcpfmt.fmt 和 Bcpodbc.bcp 从项目目录复制到 .exe 文件所在的目录，然后调用 .exe。</span><span class="sxs-lookup"><span data-stu-id="e13d7-129">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="e13d7-130">执行第五个 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 代码列表，以删除该示例使用的表。</span><span class="sxs-lookup"><span data-stu-id="e13d7-130">Execute the fifth ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```sql
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
```  
  
```cpp
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
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
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```sql
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e13d7-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e13d7-131">See Also</span></span>  
 <span data-ttu-id="e13d7-132">[SQL Server ODBC 驱动程序的大容量复制操作指南主题 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="e13d7-132">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="e13d7-133">使用数据文件和格式化文件</span><span class="sxs-lookup"><span data-stu-id="e13d7-133">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
