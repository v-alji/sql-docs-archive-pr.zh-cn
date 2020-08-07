---
title: bcp_writefmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_writefmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_writefmt function
ms.assetid: cb4c1d37-667d-4bcd-b13c-eb638bcc9b69
author: rothja
ms.author: jroth
ms.openlocfilehash: 13785469e0b02f63f14d28f0db87e77df3a15cfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587796"
---
# <a name="bcp_writefmt"></a><span data-ttu-id="decff-102">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="decff-102">bcp_writefmt</span></span>
  <span data-ttu-id="decff-103">创建一个格式化文件，它包含对当前大容量复制数据文件的格式的说明。</span><span class="sxs-lookup"><span data-stu-id="decff-103">Creates a format file containing a description of the format of the current bulk copy data file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="decff-104">语法</span><span class="sxs-lookup"><span data-stu-id="decff-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_writefmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="decff-105">自变量</span><span class="sxs-lookup"><span data-stu-id="decff-105">Arguments</span></span>  
 <span data-ttu-id="decff-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="decff-106">*hdbc*</span></span>  
 <span data-ttu-id="decff-107">是启用大容量复制的 ODBC 连接句柄。</span><span class="sxs-lookup"><span data-stu-id="decff-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="decff-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="decff-108">*szFormatFile*</span></span>  
 <span data-ttu-id="decff-109">接收数据文件格式值的用户文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="decff-109">Is the path and file name of the user file to receive format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="decff-110">返回</span><span class="sxs-lookup"><span data-stu-id="decff-110">Returns</span></span>  
 <span data-ttu-id="decff-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="decff-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="decff-112">备注</span><span class="sxs-lookup"><span data-stu-id="decff-112">Remarks</span></span>  
 <span data-ttu-id="decff-113">格式化文件指定大容量复制所创建的数据文件的数据格式。</span><span class="sxs-lookup"><span data-stu-id="decff-113">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="decff-114">对[bcp_columns](bcp-columns.md)和[bcp_colfmt](bcp-colfmt.md)的调用定义数据文件的格式。</span><span class="sxs-lookup"><span data-stu-id="decff-114">Calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md) define the format of the data file.</span></span> <span data-ttu-id="decff-115">**bcp_writefmt**在*szformatfile 所*引用的文件中保存此定义。</span><span class="sxs-lookup"><span data-stu-id="decff-115">**bcp_writefmt** saves this definition in the file referenced by *szFormatFile*.</span></span> <span data-ttu-id="decff-116">有关详细信息，请参阅[bcp_init](bcp-init.md)。</span><span class="sxs-lookup"><span data-stu-id="decff-116">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="decff-117">有关**bcp**数据格式文件的结构的详细信息，请参阅[使用 Bcp 实用工具导入和导出大容量数据 &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="decff-117">For more information about the structure of **bcp** data format files, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).</span></span>  
  
 <span data-ttu-id="decff-118">若要加载已保存的格式化文件，请使用[bcp_readfmt](bcp-readfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="decff-118">To load a saved format file, use [bcp_readfmt](bcp-readfmt.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="decff-119">仅在版本7.0 和更高版本分发的**bcp**实用工具版本中支持**bcp_writefmt**生成的格式化文件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="decff-119">The format file produced by **bcp_writefmt** is supported only by versions of the **bcp** utility distributed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="decff-120">示例</span><span class="sxs-lookup"><span data-stu-id="decff-120">Example</span></span>  
  
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
   _T("myErrors"),    DB_OUT) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_columns(hdbc, 3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
bcp_colfmt(hdbc, 1, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 1);  
bcp_colfmt(hdbc, 2, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 2);  
bcp_colfmt(hdbc, 3, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 3);  
  
if (bcp_writefmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   printf_s("%ld rows copied from SQL Server\n", nRowsProcessed);  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="decff-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="decff-121">See Also</span></span>  
 [<span data-ttu-id="decff-122">大容量复制函数</span><span class="sxs-lookup"><span data-stu-id="decff-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
