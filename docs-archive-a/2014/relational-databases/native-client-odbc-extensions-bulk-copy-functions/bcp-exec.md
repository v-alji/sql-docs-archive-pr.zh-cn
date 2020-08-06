---
title: bcp_exec |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: rothja
ms.author: jroth
ms.openlocfilehash: f925c6cb1e3a36f79ba4f560a06c5b6d499ece4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576724"
---
# <a name="bcp_exec"></a><span data-ttu-id="12dba-102">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="12dba-102">bcp_exec</span></span>
  <span data-ttu-id="12dba-103">执行数据库表和用户文件之间数据的完整大容量复制。</span><span class="sxs-lookup"><span data-stu-id="12dba-103">Executes a complete bulk copy of data between a database table and a user file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12dba-104">语法</span><span class="sxs-lookup"><span data-stu-id="12dba-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="12dba-105">参数</span><span class="sxs-lookup"><span data-stu-id="12dba-105">Arguments</span></span>  
 <span data-ttu-id="12dba-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="12dba-106">*hdbc*</span></span>  
 <span data-ttu-id="12dba-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="12dba-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="12dba-108">*pnRowsProcessed*</span><span class="sxs-lookup"><span data-stu-id="12dba-108">*pnRowsProcessed*</span></span>  
 <span data-ttu-id="12dba-109">指向 DBINT 的指针。</span><span class="sxs-lookup"><span data-stu-id="12dba-109">Is a pointer to a DBINT.</span></span> <span data-ttu-id="12dba-110">**Bcp_exec**函数用成功复制的行数填充此 DBINT。</span><span class="sxs-lookup"><span data-stu-id="12dba-110">The **bcp_exec** function fills this DBINT with the number of rows successfully copied.</span></span> <span data-ttu-id="12dba-111">如果*pnRowsProcessed*为 NULL，则**bcp_exec**将忽略它。</span><span class="sxs-lookup"><span data-stu-id="12dba-111">If *pnRowsProcessed* is NULL, it is ignored by **bcp_exec**.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="12dba-112">返回</span><span class="sxs-lookup"><span data-stu-id="12dba-112">Returns</span></span>  
 <span data-ttu-id="12dba-113">SUCCEED、SUCCEED_ASYNC 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="12dba-113">SUCCEED, SUCCEED_ASYNC, or FAIL.</span></span> <span data-ttu-id="12dba-114">如果复制所有行， **bcp_exec**函数将返回成功。</span><span class="sxs-lookup"><span data-stu-id="12dba-114">The **bcp_exec** function returns SUCCEED if all rows are copied.</span></span> <span data-ttu-id="12dba-115">如果异步大容量复制操作仍未完成， **bcp_exec**将返回 SUCCEED_ASYNC。</span><span class="sxs-lookup"><span data-stu-id="12dba-115">**bcp_exec** returns SUCCEED_ASYNC if an asynchronous bulk copy operation is still outstanding.</span></span> <span data-ttu-id="12dba-116">如果发生了完全失败，或者如果生成错误的行数达到使用[bcp_control](bcp-control.md)为 BCPMAXERRS 指定的值，则**bcp_exec**返回失败。</span><span class="sxs-lookup"><span data-stu-id="12dba-116">**bcp_exec** returns FAIL if a complete failure occurs, or if the number of rows generating errors reaches the value specified for BCPMAXERRS using [bcp_control](bcp-control.md).</span></span> <span data-ttu-id="12dba-117">BCPMAXERRS 默认为 10。</span><span class="sxs-lookup"><span data-stu-id="12dba-117">BCPMAXERRS defaults to 10.</span></span> <span data-ttu-id="12dba-118">BCPMAXERRS 选项只影响从数据文件读取行（并且不是已发送到服务器的行）时提供程序检测到的语法错误。</span><span class="sxs-lookup"><span data-stu-id="12dba-118">The BCPMAXERRS option affects only the syntax errors detected by the provider while reading the rows from the data file (and not the rows sent to the server).</span></span> <span data-ttu-id="12dba-119">服务器在检测到某一行有错误时将中止批处理。</span><span class="sxs-lookup"><span data-stu-id="12dba-119">Server aborts the batch when it detects an error with a row.</span></span> <span data-ttu-id="12dba-120">检查*pnRowsProcessed*参数是否已成功复制的行数。</span><span class="sxs-lookup"><span data-stu-id="12dba-120">Check the *pnRowsProcessed* parameter for the number of rows successfully copied.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12dba-121">备注</span><span class="sxs-lookup"><span data-stu-id="12dba-121">Remarks</span></span>  
 <span data-ttu-id="12dba-122">此函数将数据从用户文件复制到数据库表，或从用户文件复制到数据库表，具体取决于[bcp_init](bcp-init.md)中的*eDirection*参数的值。</span><span class="sxs-lookup"><span data-stu-id="12dba-122">This function copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter in [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="12dba-123">调用**bcp_exec**之前，请使用有效的用户文件名调用**bcp_init** 。</span><span class="sxs-lookup"><span data-stu-id="12dba-123">Before calling **bcp_exec**, call **bcp_init** with a valid user file name.</span></span> <span data-ttu-id="12dba-124">如果没有这样做，会导致错误。</span><span class="sxs-lookup"><span data-stu-id="12dba-124">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="12dba-125">**bcp_exec**是在任意时间长度中可能未完成的唯一大容量复制函数。</span><span class="sxs-lookup"><span data-stu-id="12dba-125">**bcp_exec** is the only bulk copy function that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="12dba-126">因此，它是支持异步模式的唯一大容量复制函数。</span><span class="sxs-lookup"><span data-stu-id="12dba-126">It is therefore the only bulk copy function that supports asynchronous mode.</span></span> <span data-ttu-id="12dba-127">若要设置异步模式，请在调用**bcp_exec**之前，使用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)将 SQL_ATTR_ASYNC_ENABLE 设置为 SQL_ASYNC_ENABLE_ON。</span><span class="sxs-lookup"><span data-stu-id="12dba-127">To set asynchronous mode, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON before calling **bcp_exec**.</span></span> <span data-ttu-id="12dba-128">若要测试完成，请调用具有相同参数的**bcp_exec** 。</span><span class="sxs-lookup"><span data-stu-id="12dba-128">To test for completion, call **bcp_exec** with the same parameters.</span></span> <span data-ttu-id="12dba-129">如果大容量复制尚未完成， **bcp_exec**将返回 SUCCEED_ASYNC。</span><span class="sxs-lookup"><span data-stu-id="12dba-129">If the bulk copy has not yet completed, **bcp_exec** returns SUCCEED_ASYNC.</span></span> <span data-ttu-id="12dba-130">它还会在*pnRowsProcessed*中返回已发送到服务器的行数的状态计数。</span><span class="sxs-lookup"><span data-stu-id="12dba-130">It also returns in *pnRowsProcessed* a status count of the number of rows that have been sent to the server.</span></span> <span data-ttu-id="12dba-131">发送到服务器的行直到到达批的末尾时才会提交。</span><span class="sxs-lookup"><span data-stu-id="12dba-131">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
 <span data-ttu-id="12dba-132">有关从开始大容量复制的重大更改的信息 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，请参阅[&#40;ODBC&#41;执行大容量复制操作](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="12dba-132">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12dba-133">示例</span><span class="sxs-lookup"><span data-stu-id="12dba-133">Example</span></span>  
 <span data-ttu-id="12dba-134">下面的示例演示如何使用**bcp_exec**：</span><span class="sxs-lookup"><span data-stu-id="12dba-134">The following example shows how to use **bcp_exec**:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="12dba-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12dba-135">See Also</span></span>  
 [<span data-ttu-id="12dba-136">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="12dba-136">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
