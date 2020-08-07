---
title: bcp_setbulkmode |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b7a68dfb3c868422b2e01cccf511a623d3afe52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587799"
---
# <a name="bcp_setbulkmode"></a><span data-ttu-id="17389-102">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="17389-102">bcp_setbulkmode</span></span>
  <span data-ttu-id="17389-103">bcp_setbulkmode 允许您在大容量复制操作中指定列格式，并在单个函数调用中设置所有列特性。</span><span class="sxs-lookup"><span data-stu-id="17389-103">bcp_setbulkmode lets you specify the column format in a bulk copy operation, setting all the column attributes in a single function call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17389-104">语法</span><span class="sxs-lookup"><span data-stu-id="17389-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC   
hdbc  
,  
   INT   
property  
,  
   void *   
pField  
,  
   INT   
cbField  
,  
   void *   
pRow  
,  
   INT   
cbRow  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="17389-105">自变量</span><span class="sxs-lookup"><span data-stu-id="17389-105">Arguments</span></span>  
 <span data-ttu-id="17389-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="17389-106">*hdbc*</span></span>  
 <span data-ttu-id="17389-107">支持大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="17389-107">The bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="17389-108">*property*</span><span class="sxs-lookup"><span data-stu-id="17389-108">*property*</span></span>  
 <span data-ttu-id="17389-109">类型为 BYTE 的常量。</span><span class="sxs-lookup"><span data-stu-id="17389-109">A constant of type BYTE.</span></span> <span data-ttu-id="17389-110">相关的常量列表，请参阅“备注”部分中的表。</span><span class="sxs-lookup"><span data-stu-id="17389-110">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="17389-111">pField\*\*</span><span class="sxs-lookup"><span data-stu-id="17389-111">*pField*</span></span>  
 <span data-ttu-id="17389-112">指向字段终止符值的指针。</span><span class="sxs-lookup"><span data-stu-id="17389-112">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="17389-113">*cbField*</span><span class="sxs-lookup"><span data-stu-id="17389-113">*cbField*</span></span>  
 <span data-ttu-id="17389-114">字段终止符值的长度 (以字节为单位) 。</span><span class="sxs-lookup"><span data-stu-id="17389-114">The length (in bytes) of the field terminator value.</span></span>  
  
 <span data-ttu-id="17389-115">*pRow*</span><span class="sxs-lookup"><span data-stu-id="17389-115">*pRow*</span></span>  
 <span data-ttu-id="17389-116">指向行终止符值的指针。</span><span class="sxs-lookup"><span data-stu-id="17389-116">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="17389-117">*cbRow*</span><span class="sxs-lookup"><span data-stu-id="17389-117">*cbRow*</span></span>  
 <span data-ttu-id="17389-118">行终止符值的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="17389-118">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="17389-119">返回</span><span class="sxs-lookup"><span data-stu-id="17389-119">Returns</span></span>  
 <span data-ttu-id="17389-120">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="17389-120">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17389-121">备注</span><span class="sxs-lookup"><span data-stu-id="17389-121">Remarks</span></span>  
 <span data-ttu-id="17389-122">bcp_setbulkmode 可用于从查询或表中大容量复制。</span><span class="sxs-lookup"><span data-stu-id="17389-122">bcp_setbulkmode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="17389-123">当 bcp_setbulkmode 用于大容量复制查询语句时，必须在使用 BCP_HINT 调用 bcp_control 之前调用它。</span><span class="sxs-lookup"><span data-stu-id="17389-123">When bcp_setbulkmode is used to bulk copy out a query statement, it must be called before calling bcp_control with BCP_HINT.</span></span>  
  
 <span data-ttu-id="17389-124">bcp_setbulkmode 是使用[bcp_setcolfmt](bcp-setcolfmt.md)和[bcp_columns](bcp-columns.md)的替代方法，只允许指定每个函数调用的一列的格式。</span><span class="sxs-lookup"><span data-stu-id="17389-124">bcp_setbulkmode is an alternative to using [bcp_setcolfmt](bcp-setcolfmt.md) and [bcp_columns](bcp-columns.md), which only let you specify the format of one column per function call.</span></span>  
  
 <span data-ttu-id="17389-125">下表列出了 property 参数的常量\*\*。</span><span class="sxs-lookup"><span data-stu-id="17389-125">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="17389-126">properties</span><span class="sxs-lookup"><span data-stu-id="17389-126">Property</span></span>|<span data-ttu-id="17389-127">说明</span><span class="sxs-lookup"><span data-stu-id="17389-127">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="17389-128">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="17389-128">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="17389-129">指定字符输出模式。</span><span class="sxs-lookup"><span data-stu-id="17389-129">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="17389-130">对应于 BCP.EXE 中的-c 选项，并对应于 `BCP_FMT_TYPE` 属性设置为的 bcp_setcolfmt `SQLCHARACTER` 。</span><span class="sxs-lookup"><span data-stu-id="17389-130">Corresponds to the -c option in BCP.EXE, and to bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="17389-131">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="17389-131">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="17389-132">指定 Unicode 输出模式。</span><span class="sxs-lookup"><span data-stu-id="17389-132">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="17389-133">与 BCP.EXE 和属性设置为的 bcp_setcolfmt 中的-w 选项相对应 `BCP_FMT_TYPE` `SQLNCHAR` 。</span><span class="sxs-lookup"><span data-stu-id="17389-133">Corresponds to the -w option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR`.</span></span>|  
|<span data-ttu-id="17389-134">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="17389-134">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="17389-135">指定对非字符类型使用本机类型，对字符类型使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="17389-135">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="17389-136">对应于 BCP.EXE 中的-N 选项， `BCP_FMT_TYPE` 如果列类型是字符串，则为属性设置为的 bcp_setcolfmt `SQLNCHAR` (默认值为; 如果不是字符串) ，则为。</span><span class="sxs-lookup"><span data-stu-id="17389-136">Corresponds to the -N option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR` if the column type is a string (default if not a string).</span></span>|  
|<span data-ttu-id="17389-137">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="17389-137">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="17389-138">指定本机数据库类型。</span><span class="sxs-lookup"><span data-stu-id="17389-138">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="17389-139">对应于 BCP.EXE 和 `BCP_FMT_TYPE` 属性设置为默认值的 bcp_setcolfmt 中的-n 选项。</span><span class="sxs-lookup"><span data-stu-id="17389-139">Corresponds to the -n option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to the default.</span></span>|  
  
 <span data-ttu-id="17389-140">不应将 bcp_setbulkmode 与包含 bcp_setcolfmt、bcp_control 和 bcp_readfmt 的函数调用序列一起使用。</span><span class="sxs-lookup"><span data-stu-id="17389-140">You should not use bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt.</span></span> <span data-ttu-id="17389-141">例如，不应 (BCPTEXTFILE) 和 bcp_setbulkmode 调用 bcp_control。</span><span class="sxs-lookup"><span data-stu-id="17389-141">For example, you should not call bcp_control(BCPTEXTFILE) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="17389-142">对于不与 bcp_setbulkmode 冲突的 bcp_control 选项，可以调用 bcp_control 和 bcp_setbulkmode。</span><span class="sxs-lookup"><span data-stu-id="17389-142">You can call bcp_control and bcp_setbulkmode for bcp_control options that do not conflict with bcp_setbulkmode.</span></span> <span data-ttu-id="17389-143">例如，可以 (BCPFIRST) 和 bcp_setbulkmode 调用 bcp_control。</span><span class="sxs-lookup"><span data-stu-id="17389-143">For example, you can call bcp_control(BCPFIRST) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="17389-144">如果尝试使用包含 bcp_setcolfmt、bcp_control 和 bcp_readfmt 的函数调用序列 bcp_setbulkmode，其中一个函数调用将返回序列错误失败。</span><span class="sxs-lookup"><span data-stu-id="17389-144">If you attempt to call bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="17389-145">如果选择更正失败，请调用 bcp_init 以重置所有设置并重新开始。</span><span class="sxs-lookup"><span data-stu-id="17389-145">If you choose to correct the failure, call bcp_init to reset all the settings and start over.</span></span>  
  
 <span data-ttu-id="17389-146">下表提供了会造成函数序列错误的函数调用的一些示例：</span><span class="sxs-lookup"><span data-stu-id="17389-146">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="17389-147">调用序列</span><span class="sxs-lookup"><span data-stu-id="17389-147">Call sequence</span></span>  
  
```  
bcp_init("table", DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, "select ...");  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, "select ...");  
bcp_readfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a><span data-ttu-id="17389-148">示例</span><span class="sxs-lookup"><span data-stu-id="17389-148">Example</span></span>  
 <span data-ttu-id="17389-149">下面的示例使用 bcp_setbulkmode 的不同设置创建了四个文件。</span><span class="sxs-lookup"><span data-stu-id="17389-149">The following sample creates four files using different settings of bcp_setbulkmode.</span></span>  
  
```  
// compile with: sqlncli11.lib odbc32.lib  
  
#include <windows.h>  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlext.h>  
#include "sqlncli.h"  
  
// Global variables  
SQLHENV g_hEnv = NULL;  
SQLHDBC g_hDbc = NULL;  
  
void ODBCCleanUp() {  
   if (g_hDbc) {  
      SQLDisconnect(g_hDbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, g_hDbc);  
      g_hDbc = NULL;  
   }  
   if (g_hEnv) {  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      g_hEnv = NULL;  
   }  
}  
  
BOOL MakeODBCConnection(TCHAR * pszServer) {  
   TCHAR szConnectionString[500];  
   TCHAR szOutConnectionString[500];  
   SQLSMALLINT iLen;  
   SQLRETURN rc;  
  
   _sntprintf_s(szConnectionString, 500, TEXT("DRIVER={SQL Server Native Client 11.0};Server=%s;Trusted_connection=yes;"), pszServer);  
   rc = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE,&g_hEnv);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_ENV...) failed\n");  
      return false;  
   }  
   rc = SQLSetEnvAttr(g_hEnv,SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_UINTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetEnvAttr failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   rc = SQLAllocHandle( SQL_HANDLE_DBC, g_hEnv , &g_hDbc);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_DBC...) failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   // Enable BCP  
   rc = SQLSetConnectAttr(g_hDbc, SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON, SQL_IS_INTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetConnectAttr(.. SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON ...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // connecting ...  
   rc = SQLDriverConnect(g_hDbc,NULL, (SQLTCHAR*)szConnectionString, SQL_NTS, (SQLTCHAR*)szOutConnectionString, 500, &iLen, SQL_DRIVER_NOPROMPT);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLDriverConnect(SQL_HANDLE_DBC...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   return true;  
}  
  
BOOL BCPSetBulkMode(TCHAR * pszServer, TCHAR * pszQureryOut, char BCPType, TCHAR * pszDataFile) {  
   SQLRETURN rc;  
  
   if (!MakeODBCConnection(pszServer))  
      return false;  
   rc = bcp_init(g_hDbc, NULL, pszDataFile, NULL, DB_OUT);   // bcp init for queryout  
   if (SUCCEED != rc) {  
      printf("bcp_init failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if (BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if (BCPType == 'w') {   // bcp -w   
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               ODBCCleanUp();  
               return false;  
            }  
            rc = bcp_setbulkmode(g_hDbc, bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (SUCCEED != rc) {  
               printf("bcp_setbulkmode failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // set queryout TSQL statement  
            rc = bcp_control(g_hDbc, BCPHINTS , pszQureryOut);  
            if (SUCCEED != rc) {  
               printf("bcp_control(..BCP_OPTION_HINTS..) failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBINT nRowsInserted = 0;  
            rc = bcp_exec(g_hDbc, &nRowsInserted);  
            if (SUCCEED != rc) {  
               printf("bcp_exec failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            ODBCCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', TEXT("bcpc.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', TEXT("bcpw.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', TEXT("bcpn.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', TEXT("bcp_N.dat"));  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="17389-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17389-150">See Also</span></span>  
 [<span data-ttu-id="17389-151">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="17389-151">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
