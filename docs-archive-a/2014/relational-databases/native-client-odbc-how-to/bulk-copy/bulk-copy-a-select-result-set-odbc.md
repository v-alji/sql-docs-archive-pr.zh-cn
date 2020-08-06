---
title: 大容量复制 SELECT 结果集 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC]
- bulk copy [ODBC], data files
- bulk copy [ODBC], about bulk copy
ms.assetid: 63d5a87b-4d5f-449b-8c77-9f9cc6b190d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 6476d603a61b9dee0a8a71cb3ec1fa865d1156f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693838"
---
# <a name="bulk-copy-a-select-result-set-odbc"></a><span data-ttu-id="ef71d-102">大容量复制 SELECT 结果集 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="ef71d-102">Bulk Copy a SELECT Result Set (ODBC)</span></span>
  <span data-ttu-id="ef71d-103">此示例显示如何使用大容量复制函数向外大容量复制 SELECT 语句的结果集。</span><span class="sxs-lookup"><span data-stu-id="ef71d-103">This sample shows how to use bulk copy functions to bulk copy out the result set of a SELECT statement.</span></span> <span data-ttu-id="ef71d-104">此示例是面向 ODBC 3.0 版或更高版本开发的。</span><span class="sxs-lookup"><span data-stu-id="ef71d-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ef71d-105">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="ef71d-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="ef71d-106">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="ef71d-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="ef71d-107">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="ef71d-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="ef71d-108">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="ef71d-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-bulk-copy-out-the-result-set-of-a-select-statement"></a><span data-ttu-id="ef71d-109">向外大容量复制 SELECT 语句的结果集</span><span class="sxs-lookup"><span data-stu-id="ef71d-109">To bulk copy out the result set of a SELECT statement</span></span>  
  
1.  <span data-ttu-id="ef71d-110">分配环境句柄和连接句柄。</span><span class="sxs-lookup"><span data-stu-id="ef71d-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="ef71d-111">设置 SQL_COPT_SS_BCP 和 SQL_BCP_ON 以启用大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="ef71d-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="ef71d-112">连接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ef71d-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="ef71d-113">调用[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以设置以下信息：</span><span class="sxs-lookup"><span data-stu-id="ef71d-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="ef71d-114">对于*szTable*参数，请指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="ef71d-114">Specify NULL for the *szTable* parameter.</span></span>  
  
    -   <span data-ttu-id="ef71d-115">接收结果集数据的数据文件的名称。</span><span class="sxs-lookup"><span data-stu-id="ef71d-115">The name of the data file that receives result set data.</span></span>  
  
    -   <span data-ttu-id="ef71d-116">接收任何大容量复制错误消息的数据文件的名称（如果您不需要消息文件，请指定 NULL）。</span><span class="sxs-lookup"><span data-stu-id="ef71d-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="ef71d-117">复制方向：DB_OUT。</span><span class="sxs-lookup"><span data-stu-id="ef71d-117">The direction of the copy: DB_OUT.</span></span>  
  
5.  <span data-ttu-id="ef71d-118">调用[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)，将 eOption 设置为 BCPHINTS，并在 iValue 中放置一个指向包含 SELECT 语句的 SQLTCHAR 数组的指针。</span><span class="sxs-lookup"><span data-stu-id="ef71d-118">Call [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md), set eOption to BCPHINTS and place in iValue a pointer to a SQLTCHAR array containing the SELECT statement.</span></span>  
  
6.  <span data-ttu-id="ef71d-119">调用[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)执行大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="ef71d-119">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="ef71d-120">按以上步骤操作时文件是以本机格式创建的。</span><span class="sxs-lookup"><span data-stu-id="ef71d-120">When using these steps the file is created in native format.</span></span> <span data-ttu-id="ef71d-121">您可以使用[bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)将数据值转换为其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="ef71d-121">You can convert the data values to other data types by using [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md).</span></span> <span data-ttu-id="ef71d-122">有关详细信息，请参阅[创建大容量复制格式化文件 &#40;ODBC&#41;](create-a-bulk-copy-format-file-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="ef71d-122">For more information, see [Create a Bulk Copy Format File &#40;ODBC&#41;](create-a-bulk-copy-format-file-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef71d-123">示例</span><span class="sxs-lookup"><span data-stu-id="ef71d-123">Example</span></span>  
 <span data-ttu-id="ef71d-124">需要一个名为 AdventureWorks 的 ODBC 数据源，其默认数据库是 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="ef71d-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="ef71d-125"> (可以从[Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载 AdventureWorks 示例数据库。 ) 此数据源必须基于操作系统提供的 ODBC 驱动程序， (驱动程序名称为 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="ef71d-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="ef71d-126">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="ef71d-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="ef71d-127">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="ef71d-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="ef71d-128">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="ef71d-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="ef71d-129">默认情况下，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="ef71d-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="ef71d-130">使用 odbc32.lib 和 odbcbcp.lib 进行编译。</span><span class="sxs-lookup"><span data-stu-id="ef71d-130">Compile with odbc32.lib and odbcbcp.lib.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 256  
  
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
  
   // Bulk copy variables.  
   SDWORD cRows;  
   SQLTCHAR szBCPQuery[] = "SELECT BirthDate FROM HumanResources.Employee";  
  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and then connect.  
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
  
   // Sample use Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, NULL, "BCPODBC.bcp", "BCPERROR.out", DB_OUT);  
   // The test is for the bulk copy return of SUCCEED, not the ODBC return of SQL_SUCCESS.  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Specify the query to use.  
   retcode = bcp_control(hdbc1, BCPHINTS, (void *)szBCPQuery);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_control(hdbc1) Failed\n\n");  
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
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef71d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef71d-131">See Also</span></span>  
 [<span data-ttu-id="ef71d-132">SQL Server ODBC 驱动程序的大容量复制操作指南主题 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="ef71d-132">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
  
