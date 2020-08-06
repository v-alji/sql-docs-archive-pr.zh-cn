---
title: 分配句柄并连接到 SQL Server (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: rothja
ms.author: jroth
ms.openlocfilehash: 615a6dbe966b4c681e9cd4285ff55864d7a13370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693840"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a><span data-ttu-id="8b014-102">分配句柄并连接到 SQL Server (ODBC)</span><span class="sxs-lookup"><span data-stu-id="8b014-102">Allocate Handles and Connect to SQL Server (ODBC)</span></span>
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a><span data-ttu-id="8b014-103">分配句柄并连接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b014-103">To allocate handles and connect to SQL Server</span></span>  
  
1.  <span data-ttu-id="8b014-104">包含 ODBC 头文件 Sql.h、Sqlext.h、Sqltypes.h。</span><span class="sxs-lookup"><span data-stu-id="8b014-104">Include the ODBC header files Sql.h, Sqlext.h, Sqltypes.h.</span></span>  
  
2.  <span data-ttu-id="8b014-105">包含特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驱动程序的头文件 Odbcss.h。</span><span class="sxs-lookup"><span data-stu-id="8b014-105">Include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver-specific header file, Odbcss.h.</span></span>  
  
3.  <span data-ttu-id="8b014-106">使用[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) `HandleType` SQL_HANDLE_ENV 的调用 SQLALLOCHANDLE 来初始化 ODBC 并分配环境句柄。</span><span class="sxs-lookup"><span data-stu-id="8b014-106">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_ENV to initialize ODBC and allocate an environment handle.</span></span>  
  
4.  <span data-ttu-id="8b014-107">调用[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) `Attribute` 并将设置为 SQL_ATTR_ODBC_VERSION，并 `ValuePtr` 将设置为 SQL_OV_ODBC3，以指示应用程序将使用 ODBC 1.x 格式函数调用。</span><span class="sxs-lookup"><span data-stu-id="8b014-107">Call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with `Attribute` set to SQL_ATTR_ODBC_VERSION and `ValuePtr` set to SQL_OV_ODBC3 to indicate the application will use ODBC 3.x-format function calls.</span></span>  
  
5.  <span data-ttu-id="8b014-108">也可以调用[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)来设置其他环境选项，或调用[SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)来获取环境选项。</span><span class="sxs-lookup"><span data-stu-id="8b014-108">Optionally, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) to set other environment options, or call [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) to get environment options.</span></span>  
  
6.  <span data-ttu-id="8b014-109">使用[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) `HandleType` SQL_HANDLE_DBC 的调用 SQLAllocHandle 来分配连接句柄。</span><span class="sxs-lookup"><span data-stu-id="8b014-109">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_DBC to allocate a connection handle.</span></span>  
  
7.  <span data-ttu-id="8b014-110">也可以调用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)来设置连接选项，或调用[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)来获取连接选项。</span><span class="sxs-lookup"><span data-stu-id="8b014-110">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set connection options, or call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) to get connection options.</span></span>  
  
8.  <span data-ttu-id="8b014-111">调用 SQLConnect，以使用现有数据源连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8b014-111">Call SQLConnect to use an existing data source to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="8b014-112">或</span><span class="sxs-lookup"><span data-stu-id="8b014-112">Or</span></span>  
  
     <span data-ttu-id="8b014-113">调用[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)以使用连接字符串连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8b014-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) to use a connection string to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="8b014-114">最小的完整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接字符串采用以下两种格式之一：</span><span class="sxs-lookup"><span data-stu-id="8b014-114">A minimum complete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection string has one of two forms:</span></span>  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     <span data-ttu-id="8b014-115">如果连接字符串不完整，`SQLDriverConnect` 可能会提示提供所需的信息。</span><span class="sxs-lookup"><span data-stu-id="8b014-115">If the connection string is not complete, `SQLDriverConnect` can prompt for the required information.</span></span> <span data-ttu-id="8b014-116">这是由为*DriverCompletion*参数指定的值控制的。</span><span class="sxs-lookup"><span data-stu-id="8b014-116">This is controlled by the value specified for the *DriverCompletion* parameter.</span></span>  
  
     <span data-ttu-id="8b014-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="8b014-117">\- or -</span></span>  
  
     <span data-ttu-id="8b014-118">多次调用[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)以生成连接字符串并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8b014-118">Call [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) multiple times in an iterative fashion to build the connection string and connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="8b014-119">也可以调用[SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)来获取数据源的驱动程序属性和行为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8b014-119">Optionally, call [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) to get driver attributes and behavior for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span>  
  
10. <span data-ttu-id="8b014-120">分配并使用语句。</span><span class="sxs-lookup"><span data-stu-id="8b014-120">Allocate and use statements.</span></span>  
  
11. <span data-ttu-id="8b014-121">调用 SQLDisconnect 断开连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并使连接句柄可用于新连接。</span><span class="sxs-lookup"><span data-stu-id="8b014-121">Call SQLDisconnect to disconnect from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and make the connection handle available for a new connection.</span></span>  
  
12. <span data-ttu-id="8b014-122">使用[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) `HandleType` SQL_HANDLE_DBC 的调用 SQLFreeHandle 来释放连接句柄。</span><span class="sxs-lookup"><span data-stu-id="8b014-122">Call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) with a `HandleType` of SQL_HANDLE_DBC to free the connection handle.</span></span>  
  
13. <span data-ttu-id="8b014-123">调用 `SQLFreeHandle` 并在调用时将 `HandleType` 设为 SQL_HANDLE_ENV 以释放环境句柄。</span><span class="sxs-lookup"><span data-stu-id="8b014-123">Call `SQLFreeHandle` with a `HandleType` of SQL_HANDLE_ENV to free the environment handle.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8b014-124">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="8b014-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="8b014-125">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="8b014-125">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="8b014-126">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="8b014-126">Avoid storing credentials in a file.</span></span> <span data-ttu-id="8b014-127">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="8b014-127">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b014-128">示例</span><span class="sxs-lookup"><span data-stu-id="8b014-128">Example</span></span>  
 <span data-ttu-id="8b014-129">本示例说明了如何调用 `SQLDriverConnect` 以连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，而无需使用现有 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="8b014-129">This example shows a call to `SQLDriverConnect` to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without requiring an existing ODBC data source.</span></span> <span data-ttu-id="8b014-130">通过将不完整的连接字符串传递给 `SQLDriverConnect`，它使 ODBC 驱动程序提示用户输入所缺的信息。</span><span class="sxs-lookup"><span data-stu-id="8b014-130">By passing an incomplete connection string to `SQLDriverConnect`, it causes the ODBC driver to prompt the user to enter the missing information.</span></span>  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
