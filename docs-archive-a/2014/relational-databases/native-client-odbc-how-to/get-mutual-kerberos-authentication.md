---
title: 获取相互的 Kerberos 身份验证 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 64149fd4-239b-40e4-91e2-f9011f7d9f66
author: rothja
ms.author: jroth
ms.openlocfilehash: 9845c4e0f33e67c835e57e513f47a100c75518d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692902"
---
# <a name="get-mutual-kerberos-authentication"></a><span data-ttu-id="424f7-102">获取 Kerberos 相互身份验证</span><span class="sxs-lookup"><span data-stu-id="424f7-102">Get Mutual Kerberos Authentication</span></span>
  <span data-ttu-id="424f7-103">此示例显示如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的 ODBC 获得 Kerberos 相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="424f7-103">This sample shows how to get mutual Kerberos authentication by using ODBC in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="424f7-104">此示例不适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前的任何 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="424f7-104">This sample will not work with any version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="424f7-105">有关详细信息，请参阅[客户端连接中的服务主体名称 &#40;SPN&#41; 支持](../native-client/features/service-principal-name-spn-support-in-client-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="424f7-105">For more information, see [Service Principal Name &#40;SPN&#41; Support in Client Connections](../native-client/features/service-principal-name-spn-support-in-client-connections.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="424f7-106">示例</span><span class="sxs-lookup"><span data-stu-id="424f7-106">Example</span></span>  
 <span data-ttu-id="424f7-107">如果您要将此示例构建为在 64 位操作系统上运行的 32 位应用程序并运行该示例，则必须使用 %windir%\SysWOW64\odbcad32.exe 中的 ODBC 管理器创建 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="424f7-107">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="424f7-108">此示例连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="424f7-108">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="424f7-109">若要连接到命名实例，请更改 ODBC 数据源的定义以使用以下格式指定实例：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="424f7-109">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="424f7-110">默认情况下，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 将安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="424f7-110">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="424f7-111">将“MyServer”更改为具有一个 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]（或更高版本）实例的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="424f7-111">Change "MyServer" to a machine name that has an instance of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later).</span></span>  
  
 <span data-ttu-id="424f7-112">此外，还必须指定一个客户提供的 SPN。</span><span class="sxs-lookup"><span data-stu-id="424f7-112">You will also have to specify a customer-provided SPN.</span></span> <span data-ttu-id="424f7-113">将“CP_SPN”更改为客户提供的 SPN。</span><span class="sxs-lookup"><span data-stu-id="424f7-113">Change " CP_SPN " to a customer-provided SPN.</span></span>  
  
 <span data-ttu-id="424f7-114">使用 /EHsc、/D "_UNICODE"、/D "UNICODE" 和 odbc32.lib 进行编译。</span><span class="sxs-lookup"><span data-stu-id="424f7-114">Compile with /EHsc, /D "_UNICODE", /D "UNICODE", and odbc32.lib.</span></span> <span data-ttu-id="424f7-115">请确保 INCLUDE 环境变量包含包含 sqlncli.msi 的目录。</span><span class="sxs-lookup"><span data-stu-id="424f7-115">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
```  
// compile with: /EHsc /D "_UNICODE" /D "UNICODE" odbc32.lib  
#define WIN32_LEAN_AND_MEAN  
#include <tchar.h>  
#include <windows.h>  
#include <stdio.h>  
#include <sql.h>  
#include <sqlext.h>  
  
#define _SQLNCLI_ODBC_  
#include <sqlncli.h>  
  
#define SUCCESS(x) (!((x) & 0xFFFE))  
  
#define CHKRC(stmt) do \  
                    { \  
                    rc = (stmt); \  
                    if (!SUCCESS(rc)) \  
                    throw (RETCODE) rc; \  
                    } while(0);  
  
void PrintError(SQLSMALLINT HandleType, SQLHANDLE Handle) {  
   RETCODE rc = SQL_SUCCESS;  
   SQLTCHAR szSqlState[6], szMessage[1024];  
   SQLSMALLINT i = 1, msgLen = 0;  
   SQLINTEGER NativeError;  
  
   do {  
      i = 1;  
      while (SQL_NO_DATA != (rc = SQLGetDiagRec(HandleType, Handle, i, szSqlState, &NativeError,   
         szMessage, sizeof(szMessage)/sizeof(SQLTCHAR), &msgLen)) && SUCCESS(rc)) {  
            _tprintf(_T("SQLState=%s, NativeError=%ld, Message=%s\r\n"), szSqlState, NativeError, szMessage);  
            i++;  
      }  
   }   
   while (SQL_NO_DATA != (rc = SQLMoreResults(Handle)) && SUCCESS(rc));  
}  
  
int _tmain(int argc, _TCHAR* argv[]) {  
   RETCODE rc = SQL_SUCCESS;  
   HENV henv = SQL_NULL_HENV;  
   HDBC hdbc = SQL_NULL_HDBC;  
   SQLHSTMT hstmt = SQL_NULL_HSTMT;  
   SQLTCHAR * pszConnection = _T("DRIVER={SQL Server Native Client 10.0};")  
      _T("Server=MyServer;")          // server with SQL Server 2008 (or later)  
      _T("Trusted_Connection=Yes;")  
      _T("ServerSPN=CP_SPN");    // customer-provided SPN  
  
   TCHAR szIntgAuthMethod[64];  
   SQLSMALLINT fMutuallyAuth = 0;  
  
   try {  
      CHKRC(SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HENV, &henv));  
      CHKRC(SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0));  
      CHKRC(SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc));  
      CHKRC(SQLDriverConnect( hdbc, NULL, pszConnection, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT));  
      CHKRC(SQLGetConnectAttr(hdbc, SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD, szIntgAuthMethod, sizeof(szIntgAuthMethod)/sizeof(szIntgAuthMethod[0]), NULL));  
      CHKRC(::SQLGetConnectAttrW(hdbc, SQL_COPT_SS_MUTUALLY_AUTHENTICATED, &fMutuallyAuth, SQL_IS_SMALLINT, NULL));  
  
      _tprintf(_T("Authentication method: %s\r\n"), szIntgAuthMethod);  
      _tprintf(_T("Mutually authenticated: %s\r\n"), fMutuallyAuth?_T("yes"):_T("no"));  
   }  
   catch (RETCODE retcode) {  
      rc = retcode;  
   }  
  
   if (!SUCCESS(rc)) {  
      if (hstmt)  
         PrintError(SQL_HANDLE_STMT, hstmt);  
      else if (hdbc)  
         PrintError(SQL_HANDLE_DBC, hdbc);  
      else if(henv)  
         PrintError(SQL_HANDLE_ENV, henv);  
   }  
  
   if (hstmt)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
   if (hdbc) {  
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
   }  
   if (henv)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
  
