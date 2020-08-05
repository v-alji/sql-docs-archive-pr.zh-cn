---
title: bcp_moretext |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: rothja
ms.author: jroth
ms.openlocfilehash: 00c0eb1c8739e94380b12034cebc70d8e22b79c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580251"
---
# <a name="bcp_moretext"></a><span data-ttu-id="32fab-102">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="32fab-102">bcp_moretext</span></span>
  <span data-ttu-id="32fab-103">将部分较长的可变长度数据类型值发送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="32fab-103">Sends part of a long, variable-length data type value to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32fab-104">语法</span><span class="sxs-lookup"><span data-stu-id="32fab-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="32fab-105">参数</span><span class="sxs-lookup"><span data-stu-id="32fab-105">Arguments</span></span>  
 <span data-ttu-id="32fab-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="32fab-106">*hdbc*</span></span>  
 <span data-ttu-id="32fab-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="32fab-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="32fab-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="32fab-108">*cbData*</span></span>  
 <span data-ttu-id="32fab-109">要从*pData*引用的数据复制到 SQL Server 的数据字节数。</span><span class="sxs-lookup"><span data-stu-id="32fab-109">Is the number of bytes of data being copied to SQL Server from the data referenced by *pData*.</span></span> <span data-ttu-id="32fab-110">SQL_NULL_DATA 的值指示为 NULL。</span><span class="sxs-lookup"><span data-stu-id="32fab-110">A value of SQL_NULL_DATA indicates NULL.</span></span>  
  
 <span data-ttu-id="32fab-111">*pData*</span><span class="sxs-lookup"><span data-stu-id="32fab-111">*pData*</span></span>  
 <span data-ttu-id="32fab-112">指向要发送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的受支持的较长可变长度数据块区的指针。</span><span class="sxs-lookup"><span data-stu-id="32fab-112">Is a pointer to the supported, long, variable-length data chunk to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="returns"></a><span data-ttu-id="32fab-113">返回</span><span class="sxs-lookup"><span data-stu-id="32fab-113">Returns</span></span>  
 <span data-ttu-id="32fab-114">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="32fab-114">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32fab-115">备注</span><span class="sxs-lookup"><span data-stu-id="32fab-115">Remarks</span></span>  
 <span data-ttu-id="32fab-116">此函数可与[bcp_bind](bcp-bind.md)和[bcp_sendrow](bcp-sendrow.md)结合使用，以便将长度可变的长数据值复制到多个较小的块区中 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="32fab-116">This function can be used in conjunction with [bcp_bind](bcp-bind.md) and [bcp_sendrow](bcp-sendrow.md) to copy long, variable-length data values to SQL Server in a number of smaller chunks.</span></span> <span data-ttu-id="32fab-117">**bcp_moretext**可用于具有以下 SQL Server 数据类型的列： `text` 、 `ntext` 、、、、 `image` `varchar(max)` `nvarchar(max)` `varbinary(max)` 、用户定义类型 (UDT) 和 XML。</span><span class="sxs-lookup"><span data-stu-id="32fab-117">**bcp_moretext** can be used with columns that have the following SQL Server data types: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, user-defined type (UDT), and XML.</span></span> <span data-ttu-id="32fab-118">**bcp_moretext**不支持数据转换，则提供的数据必须与目标列的数据类型匹配。</span><span class="sxs-lookup"><span data-stu-id="32fab-118">**bcp_moretext** does not support data conversions, the data supplied must match the data type of the target column.</span></span>  
  
 <span data-ttu-id="32fab-119">如果使用**bcp_moretext**支持的数据类型的非 null *pData*参数调用**bcp_bind** ，则 `bcp_sendrow` 将发送整个数据值，而不考虑长度。</span><span class="sxs-lookup"><span data-stu-id="32fab-119">If **bcp_bind** is called with a nonNULL *pData* parameter for data types that are supported by **bcp_moretext**, `bcp_sendrow` sends the entire data value, regardless of length.</span></span> <span data-ttu-id="32fab-120">但是，如果**bcp_bind**具有用于支持的数据类型的 NULL *pData*参数，则在成功返回后，可使用**bcp_moretext**立即复制数据， `bcp_sendrow` 指示已处理包含数据的所有绑定列。</span><span class="sxs-lookup"><span data-stu-id="32fab-120">If, however, **bcp_bind** has a NULL *pData* parameter for supported data types, **bcp_moretext** can be used to copy data immediately after a successful return from `bcp_sendrow` indicating that any bound columns with data present have been processed.</span></span>  
  
 <span data-ttu-id="32fab-121">如果使用**bcp_moretext**在一行中发送一种受支持的数据类型列，则还必须使用它来发送该行中所有其他支持的数据类型列。</span><span class="sxs-lookup"><span data-stu-id="32fab-121">If you use **bcp_moretext** to send one supported data type column in a row, you must also use it to send all other supported data type columns in the row.</span></span> <span data-ttu-id="32fab-122">不可以跳过任何列。</span><span class="sxs-lookup"><span data-stu-id="32fab-122">No columns may be skipped.</span></span> <span data-ttu-id="32fab-123">支持的数据类型为 SQLTEXT、SQLNTEXT、SQLIMAGE、SQLUDT 和 SQLXML。</span><span class="sxs-lookup"><span data-stu-id="32fab-123">Supported data types are SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT and SQLXML.</span></span> <span data-ttu-id="32fab-124">如果列分别为 varchar(max)、nvarchar(max) 或 varbinary(max)，则 SQLCHARACTER、SQLVARCHAR、SQNCHAR、SQLBINARY 和 SQLVARBINARY 也属于此类别。</span><span class="sxs-lookup"><span data-stu-id="32fab-124">SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY and SQLVARBINARY also fall into this category if the column is a varchar(max), nvarchar(max) or varbinary(max), respectively.</span></span>  
  
 <span data-ttu-id="32fab-125">调用**bcp_bind**或[bcp_collen](bcp-collen.md)会设置要复制到 SQL Server 列的所有数据部分的总长度。</span><span class="sxs-lookup"><span data-stu-id="32fab-125">Calling either **bcp_bind** or [bcp_collen](bcp-collen.md) sets the total length of all data parts to be copied to the SQL Server column.</span></span> <span data-ttu-id="32fab-126">尝试发送的字节数 SQL Server 超过调用**bcp_bind**中指定的字节数，或 `bcp_collen` 生成错误。</span><span class="sxs-lookup"><span data-stu-id="32fab-126">An attempt to send SQL Server more bytes than specified in the call to **bcp_bind** or `bcp_collen` generates an error.</span></span> <span data-ttu-id="32fab-127">例如，在以下应用程序中会出现此错误：一个应用程序，该应用程序 `bcp_collen` 将 SQL Server 列的可用数据的长度设置 `text` 为4500，然后调用**bcp_moretext**五次，同时指示每个调用的数据缓冲区长度为1000字节长。</span><span class="sxs-lookup"><span data-stu-id="32fab-127">This error would arise, for example, in an application which used `bcp_collen` to set the length of available data for an SQL Server `text` column to 4500, then called **bcp_moretext** five times while indicating on each call that the data buffer length was 1000 bytes long.</span></span>  
  
 <span data-ttu-id="32fab-128">如果复制的行包含多个长、可变长度的列， **bcp_moretext**首先会将其数据发送到最低的按序号编号列，后跟下一个最低的按序号编号列，依此类推。</span><span class="sxs-lookup"><span data-stu-id="32fab-128">If a copied row contains more than one long, variable-length column, **bcp_moretext** first sends its data to the lowest ordinally numbered column, followed by the next lowest ordinally numbered column, and so on.</span></span> <span data-ttu-id="32fab-129">正确设置所需的数据的总长度很重要。</span><span class="sxs-lookup"><span data-stu-id="32fab-129">Correct setting of the total length of expected data is important.</span></span> <span data-ttu-id="32fab-130">无法在长度设置之外发出已通过大容量复制接收某列的所有数据的信号。</span><span class="sxs-lookup"><span data-stu-id="32fab-130">There is no way to signal, outside of the length setting, that all data for a column has been received by bulk copy.</span></span>  
  
 <span data-ttu-id="32fab-131">当 `var(max)` 使用 bcp_sendrow 和 bcp_moretext 将值发送到服务器时，无需调用 bcp_collen 来设置列长度。</span><span class="sxs-lookup"><span data-stu-id="32fab-131">When `var(max)` values are sent to the server using bcp_sendrow and bcp_moretext, it is not necessary to call bcp_collen to set the column length.</span></span> <span data-ttu-id="32fab-132">相反，对于这些类型，将通过调用长度为零的 bcp_sendrow 终止值。</span><span class="sxs-lookup"><span data-stu-id="32fab-132">Instead, for these types only, the value is terminated by calling bcp_sendrow with a length of zero.</span></span>  
  
 <span data-ttu-id="32fab-133">应用程序通常会 `bcp_sendrow` 在循环中调用并**bcp_moretext** ，以发送多行数据。</span><span class="sxs-lookup"><span data-stu-id="32fab-133">An application normally calls `bcp_sendrow` and **bcp_moretext** within loops to send a number of rows of data.</span></span> <span data-ttu-id="32fab-134">下面概述了如何为包含两列的表执行此 `text` 操作：</span><span class="sxs-lookup"><span data-stu-id="32fab-134">Here's an outline of how to do this for a table containing two `text` columns:</span></span>  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a><span data-ttu-id="32fab-135">示例</span><span class="sxs-lookup"><span data-stu-id="32fab-135">Example</span></span>  
 <span data-ttu-id="32fab-136">此示例演示如何将**bcp_moretext**与**bcp_bind**和结合使用 `bcp_sendrow` ：</span><span class="sxs-lookup"><span data-stu-id="32fab-136">This example shows how to use **bcp_moretext** with **bcp_bind** and `bcp_sendrow`:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
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
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="32fab-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32fab-137">See Also</span></span>  
 [<span data-ttu-id="32fab-138">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="32fab-138">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
