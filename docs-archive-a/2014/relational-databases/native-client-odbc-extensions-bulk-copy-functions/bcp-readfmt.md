---
title: bcp_readfmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: rothja
ms.author: jroth
ms.openlocfilehash: 37032ec276be8b914d73e834453cc5d87cdedbbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580248"
---
# <a name="bcp_readfmt"></a><span data-ttu-id="45cf2-102">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="45cf2-102">bcp_readfmt</span></span>
  <span data-ttu-id="45cf2-103">从指定的格式文件中读取数据文件格式定义。</span><span class="sxs-lookup"><span data-stu-id="45cf2-103">Reads a data file format definition from the specified format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cf2-104">语法</span><span class="sxs-lookup"><span data-stu-id="45cf2-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="45cf2-105">参数</span><span class="sxs-lookup"><span data-stu-id="45cf2-105">Arguments</span></span>  
 <span data-ttu-id="45cf2-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="45cf2-106">*hdbc*</span></span>  
 <span data-ttu-id="45cf2-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="45cf2-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="45cf2-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="45cf2-108">*szFormatFile*</span></span>  
 <span data-ttu-id="45cf2-109">包含数据文件的格式值的文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="45cf2-109">Is the path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="45cf2-110">返回</span><span class="sxs-lookup"><span data-stu-id="45cf2-110">Returns</span></span>  
 <span data-ttu-id="45cf2-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="45cf2-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45cf2-112">备注</span><span class="sxs-lookup"><span data-stu-id="45cf2-112">Remarks</span></span>  
 <span data-ttu-id="45cf2-113">`bcp_readfmt`读取格式值后，它将对[bcp_columns](bcp-columns.md)和[bcp_colfmt](bcp-colfmt.md)进行适当的调用。</span><span class="sxs-lookup"><span data-stu-id="45cf2-113">After `bcp_readfmt` reads the format values, it makes the appropriate calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span> <span data-ttu-id="45cf2-114">您无需分析格式文件和进行这些调用。</span><span class="sxs-lookup"><span data-stu-id="45cf2-114">There is no need for you to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="45cf2-115">若要保存格式化文件，请调用[bcp_writefmt](bcp-writefmt.md)。</span><span class="sxs-lookup"><span data-stu-id="45cf2-115">To persist a format file, call [bcp_writefmt](bcp-writefmt.md).</span></span> <span data-ttu-id="45cf2-116">对的调用 `bcp_readfmt` 可以引用保存的格式。</span><span class="sxs-lookup"><span data-stu-id="45cf2-116">Calls to `bcp_readfmt` can reference saved formats.</span></span> <span data-ttu-id="45cf2-117">有关详细信息，请参阅[bcp_init](bcp-init.md)。</span><span class="sxs-lookup"><span data-stu-id="45cf2-117">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="45cf2-118">此外，大容量复制实用工具 (**bcp**) 可以将用户定义的数据格式保存在可由引用的文件中 `bcp_readfmt` 。</span><span class="sxs-lookup"><span data-stu-id="45cf2-118">Alternately, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by `bcp_readfmt`.</span></span> <span data-ttu-id="45cf2-119">有关**bcp**实用工具和**bcp**数据格式文件的结构的详细信息，请参阅[批量导入和导出数据 &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="45cf2-119">For more information about the **bcp** utility and the structure of **bcp** data format files, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="45cf2-120">`BCPDELAYREADFMT` [Bcp_control](bcp-control.md)的*eOption*参数的值修改 bcp_readfmt 的行为。</span><span class="sxs-lookup"><span data-stu-id="45cf2-120">The `BCPDELAYREADFMT` value of the *eOption* parameter of [bcp_control](bcp-control.md) modifies the behavior of bcp_readfmt.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="45cf2-121">格式化文件必须由**bcp**实用工具版本4.2 或更高版本生成。</span><span class="sxs-lookup"><span data-stu-id="45cf2-121">The format file must have been produced by version 4.2 or later of the **bcp** utility.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45cf2-122">示例</span><span class="sxs-lookup"><span data-stu-id="45cf2-122">Example</span></span>  
  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="45cf2-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45cf2-123">See Also</span></span>  
 [<span data-ttu-id="45cf2-124">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="45cf2-124">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
