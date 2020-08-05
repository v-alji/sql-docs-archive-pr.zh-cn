---
title: bcp_init |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_init
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d48b2a07e425e0863084c700c4de93d2776739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580252"
---
# <a name="bcp_init"></a><span data-ttu-id="06ef0-102">bcp_init</span><span class="sxs-lookup"><span data-stu-id="06ef0-102">bcp_init</span></span>
  <span data-ttu-id="06ef0-103">初始化大容量复制操作。</span><span class="sxs-lookup"><span data-stu-id="06ef0-103">Initializes the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ef0-104">语法</span><span class="sxs-lookup"><span data-stu-id="06ef0-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_init (  
HDBC   
hdbc  
,  
LPCTSTR   
szTable  
,  
LPCTSTR   
szDataFile  
,  
LPCTSTR   
szErrorFile  
,  
INT   
eDirection  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="06ef0-105">参数</span><span class="sxs-lookup"><span data-stu-id="06ef0-105">Arguments</span></span>  
 <span data-ttu-id="06ef0-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="06ef0-106">*hdbc*</span></span>  
 <span data-ttu-id="06ef0-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="06ef0-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="06ef0-108">*szTable*</span><span class="sxs-lookup"><span data-stu-id="06ef0-108">*szTable*</span></span>  
 <span data-ttu-id="06ef0-109">要向内或向外复制的数据库表的名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-109">Is the name of the database table to be copied into or out of.</span></span> <span data-ttu-id="06ef0-110">该名称还可以包含数据库名称或所有者名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-110">This name can also include the database name or the owner name.</span></span> <span data-ttu-id="06ef0-111">例如， **gracie**， **pubs。标题**、 **gracie**和**标题**都是合法的表名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-111">For example, **pubs.gracie.titles**, **pubs..titles**, **gracie.titles**, and **titles** are all legal table names.</span></span>  
  
 <span data-ttu-id="06ef0-112">如果 DB_OUT *eDirection* ，则*szTable*也可以是数据库视图的名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-112">If *eDirection* is DB_OUT, *szTable* can also be the name of a database view.</span></span>  
  
 <span data-ttu-id="06ef0-113">如果 DB_OUT *eDirection* ，并且在调用[bcp_exec](bcp-exec.md)之前使用[bcp_control](bcp-control.md)指定了 SELECT 语句， **bcp_init**_szTable_必须设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="06ef0-113">If *eDirection* is DB_OUT and a SELECT statement is specified using [bcp_control](bcp-control.md) before [bcp_exec](bcp-exec.md) is called, **bcp_init**_szTable_ must be set to NULL.</span></span>  
  
 <span data-ttu-id="06ef0-114">*szDataFile*</span><span class="sxs-lookup"><span data-stu-id="06ef0-114">*szDataFile*</span></span>  
 <span data-ttu-id="06ef0-115">要向内或向外复制的用户文件的名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-115">Is the name of the user file to be copied into or out of.</span></span> <span data-ttu-id="06ef0-116">如果使用[bcp_sendrow](bcp-sendrow.md)从变量直接复制数据，请将*SZDATAFILE*设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="06ef0-116">If data is being copied directly from variables by using [bcp_sendrow](bcp-sendrow.md), set *szDataFile* to NULL.</span></span>  
  
 <span data-ttu-id="06ef0-117">*szErrorFile*</span><span class="sxs-lookup"><span data-stu-id="06ef0-117">*szErrorFile*</span></span>  
 <span data-ttu-id="06ef0-118">使用进度消息、错误消息，以及出于任何原因无法从用户文件复制到表的任何行的副本填充的错误文件的名称。</span><span class="sxs-lookup"><span data-stu-id="06ef0-118">Is the name of the error file to be filled with progress messages, error messages, and copies of any rows that, for any reason, could not be copied from a user file to a table.</span></span> <span data-ttu-id="06ef0-119">如果将 NULL 作为*szErrorFile*传递，则不会使用错误文件。</span><span class="sxs-lookup"><span data-stu-id="06ef0-119">If NULL is passed as *szErrorFile*, no error file is used.</span></span>  
  
 <span data-ttu-id="06ef0-120">*eDirection*</span><span class="sxs-lookup"><span data-stu-id="06ef0-120">*eDirection*</span></span>  
 <span data-ttu-id="06ef0-121">复制方向为 DB_IN 或 DB_OUT。</span><span class="sxs-lookup"><span data-stu-id="06ef0-121">Is the direction of the copy, either DB_IN or DB_OUT.</span></span> <span data-ttu-id="06ef0-122">DB_IN 指示从程序变量或用户文件复制到表中。</span><span class="sxs-lookup"><span data-stu-id="06ef0-122">DB_IN indicates a copy from program variables or a user file to a table.</span></span> <span data-ttu-id="06ef0-123">DB_OUT 指示从数据库表复制到用户文件中。</span><span class="sxs-lookup"><span data-stu-id="06ef0-123">DB_OUT indicates a copy from a database table to a user file.</span></span> <span data-ttu-id="06ef0-124">必须使用 DB_OUT 指定一个用户文件名。</span><span class="sxs-lookup"><span data-stu-id="06ef0-124">You must specify a user file name with DB_OUT.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="06ef0-125">返回</span><span class="sxs-lookup"><span data-stu-id="06ef0-125">Returns</span></span>  
 <span data-ttu-id="06ef0-126">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="06ef0-126">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06ef0-127">备注</span><span class="sxs-lookup"><span data-stu-id="06ef0-127">Remarks</span></span>  
 <span data-ttu-id="06ef0-128">调用任何其他大容量复制函数之前调用**bcp_init** 。</span><span class="sxs-lookup"><span data-stu-id="06ef0-128">Call **bcp_init** before calling any other bulk-copy function.</span></span> <span data-ttu-id="06ef0-129">**bcp_init**对工作站和之间的大容量数据复制执行必要的初始化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="06ef0-129">**bcp_init** performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="06ef0-130">**Bcp_init**函数必须与支持使用大容量复制函数的 ODBC 连接句柄一起提供。</span><span class="sxs-lookup"><span data-stu-id="06ef0-130">The **bcp_init** function must be provided with an ODBC connection handle enabled for use with bulk copy functions.</span></span> <span data-ttu-id="06ef0-131">若要启用句柄，请使用 SQLSetConnectAttr，将 SQL_COPT_SS_BCP [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)设置为在已分配但未连接的连接句柄上 SQL_BCP_ON。</span><span class="sxs-lookup"><span data-stu-id="06ef0-131">To enable the handle, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_BCP set to SQL_BCP_ON on an allocated, but not connected, connection handle.</span></span> <span data-ttu-id="06ef0-132">尝试对已连接的句柄分配属性将导致错误。</span><span class="sxs-lookup"><span data-stu-id="06ef0-132">Attempting to assign the attribute on a connected handle results in an error.</span></span>  
  
 <span data-ttu-id="06ef0-133">指定数据文件时， **bcp_init**会检查数据库源或目标表的结构，而不是数据文件。</span><span class="sxs-lookup"><span data-stu-id="06ef0-133">When a data file is specified, **bcp_init** examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="06ef0-134">**bcp_init**根据数据库表、视图或 SELECT 结果集中的每一列指定数据文件的数据格式值。</span><span class="sxs-lookup"><span data-stu-id="06ef0-134">**bcp_init** specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="06ef0-135">此指定包括每一列的数据类型、数据中是否存在长度或 Null 指示符和终止符字节字符串以及固定长度的数据类型的宽度。</span><span class="sxs-lookup"><span data-stu-id="06ef0-135">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="06ef0-136">**bcp_init**设置这些值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="06ef0-136">**bcp_init** sets these values as follows:</span></span>  
  
-   <span data-ttu-id="06ef0-137">指定的数据类型是数据库表、视图或 SELECT 结果集中的列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="06ef0-137">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="06ef0-138">数据类型由 sqlncli.h 中指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机数据类型枚举。</span><span class="sxs-lookup"><span data-stu-id="06ef0-138">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in sqlncli.h.</span></span> <span data-ttu-id="06ef0-139">数据自身采用它所在的计算机格式表示。</span><span class="sxs-lookup"><span data-stu-id="06ef0-139">Data itself is represented in its computer form.</span></span> <span data-ttu-id="06ef0-140">也就是说， **integer**数据类型列中的数据是根据创建数据文件的计算机上大或小字节序来表示的。</span><span class="sxs-lookup"><span data-stu-id="06ef0-140">That is, data from a column of **integer** data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="06ef0-141">如果数据库数据类型的长度是固定的，则该数据文件中的数据长度也是固定的。</span><span class="sxs-lookup"><span data-stu-id="06ef0-141">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="06ef0-142">处理数据的大容量复制函数 (例如， [bcp_exec](bcp-exec.md)) 分析数据文件中数据的长度应与数据库表、视图或 SELECT 列列表中指定的数据长度相同的数据行。</span><span class="sxs-lookup"><span data-stu-id="06ef0-142">Bulk-copy functions that process data (for example, [bcp_exec](bcp-exec.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="06ef0-143">例如，对于定义为\*\*char (13) \*\*的数据库列的数据，该文件中每行数据的数据必须由13个字符表示。</span><span class="sxs-lookup"><span data-stu-id="06ef0-143">For example, data for a database column defined as **char(13)** must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="06ef0-144">如果数据库列允许 Null 值，则可以使用 Null 指示符作为固定长度的数据的前缀。</span><span class="sxs-lookup"><span data-stu-id="06ef0-144">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="06ef0-145">定义终止符字节序列时，该终止符字节序列的长度设置为 0。</span><span class="sxs-lookup"><span data-stu-id="06ef0-145">When terminator-byte sequence is defined, the length of the terminator-byte sequence is set to 0.</span></span>  
  
-   <span data-ttu-id="06ef0-146">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制时，数据文件必须包含数据库表中的每列数据。</span><span class="sxs-lookup"><span data-stu-id="06ef0-146">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="06ef0-147">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制时，数据库表、视图或 SELECT 结果集中的所有列的数据均被复制到数据文件中。</span><span class="sxs-lookup"><span data-stu-id="06ef0-147">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="06ef0-148">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制时，数据文件中的列序号位置必须与数据库表中的列序号位置相同。</span><span class="sxs-lookup"><span data-stu-id="06ef0-148">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="06ef0-149">从复制时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， **bcp_exec**根据数据库表中列的序号位置放置数据。</span><span class="sxs-lookup"><span data-stu-id="06ef0-149">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp_exec** places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="06ef0-150">如果数据库数据类型的长度可变 (例如， \*\*varbinary (22) \*\*) 或者数据库列可以包含 null 值，则数据文件中的数据将以长度/空指示器为前缀。</span><span class="sxs-lookup"><span data-stu-id="06ef0-150">If a database data type is variable in length (for example, **varbinary(22)**) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="06ef0-151">指示符的宽度因数据类型和大容量复制的版本而异。</span><span class="sxs-lookup"><span data-stu-id="06ef0-151">The width of the indicator varies based on the data type and version of bulk copy.</span></span>  
  
 <span data-ttu-id="06ef0-152">若要更改为数据文件指定的数据格式值，请调用[bcp_columns](bcp-columns.md)和[bcp_colfmt](bcp-colfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-152">To change data format values specified for a data file, call [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
 <span data-ttu-id="06ef0-153">对于不包含索引的表，通过将数据库恢复模式设置为 SIMPLE 或 BULK_LOGGED 可以优化向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大容量复制。</span><span class="sxs-lookup"><span data-stu-id="06ef0-153">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database recovery model to SIMPLE or BULK_LOGGED.</span></span> <span data-ttu-id="06ef0-154">有关详细信息，请参阅批量导入和[更改数据库](/sql/t-sql/statements/alter-database-transact-sql)[中最小日志记录的先决条件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-154">For more information, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) and [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="06ef0-155">如果未使用任何数据文件，则必须调用[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)以指定每个列再的数据的格式和位置，然后使用 bcp_sendrow 将数据行复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中[bcp_sendrow](bcp-sendrow.md)。</span><span class="sxs-lookup"><span data-stu-id="06ef0-155">If no data file is used, you must call [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) to specify the format and location in memory of the data fsor each column, then copy data rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06ef0-156">示例</span><span class="sxs-lookup"><span data-stu-id="06ef0-156">Example</span></span>  
 <span data-ttu-id="06ef0-157">此示例显示如何将 ODBC bcp_init 函数用于格式化文件。</span><span class="sxs-lookup"><span data-stu-id="06ef0-157">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
 <span data-ttu-id="06ef0-158">编译并运行在 C++ 代码之前，您需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="06ef0-158">Before you compile and run the C++ code, you need to do the following:</span></span>  
  
-   <span data-ttu-id="06ef0-159">创建名为 Test 的 ODBC 数据源。</span><span class="sxs-lookup"><span data-stu-id="06ef0-159">Create an ODBC data source called Test.</span></span> <span data-ttu-id="06ef0-160">您可以将此数据源与任何数据库相关联。</span><span class="sxs-lookup"><span data-stu-id="06ef0-160">You can associate this data source with any database.</span></span>  
  
-   <span data-ttu-id="06ef0-161">对数据库运行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="06ef0-161">Run the following [!INCLUDE[tsql](../../includes/tsql-md.md)] on the database:</span></span>  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   <span data-ttu-id="06ef0-162">在您将在其中运行应用程序的目录中，添加名为 Bcpfmt.fmt 的文件，并将以下内容添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="06ef0-162">In the directory where you will run the application, add a file called Bcpfmt.fmt, and add this to the file:</span></span>  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   <span data-ttu-id="06ef0-163">在您将在其中运行应用程序的目录中，添加名为 Bcpodbc.bcp 的文件，并将以下内容添加到此文件中：</span><span class="sxs-lookup"><span data-stu-id="06ef0-163">In the directory where you will run the application, add a file called Bcpodbc.bcp, and add this to the file:</span></span>  
  
    ```  
    1  
    2  
    ```  
  
 <span data-ttu-id="06ef0-164">现在，您可以编译并运行此 C++ 代码了。</span><span class="sxs-lookup"><span data-stu-id="06ef0-164">Now you are ready to compile and run the C++ code.</span></span>  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
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
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
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
  
## <a name="see-also"></a><span data-ttu-id="06ef0-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06ef0-165">See Also</span></span>  
 [<span data-ttu-id="06ef0-166">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="06ef0-166">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
