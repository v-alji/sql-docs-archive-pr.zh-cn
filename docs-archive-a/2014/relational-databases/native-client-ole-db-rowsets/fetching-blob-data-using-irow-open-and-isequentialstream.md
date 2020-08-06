---
title: 使用 IRow::Open 和 ISequentialStream 提取 BLOB 数据 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching BLOB data
- Open method
- ISequentialStream interface
- BLOBs, fetching
ms.assetid: 439b3976-84e7-4d11-8dba-f668adbc9159
author: rothja
ms.author: jroth
ms.openlocfilehash: ba70977bc6649d4830b2be8eec7cb146c12c70d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687831"
---
# <a name="fetching-blob-data-using-irowopen-and-isequentialstream"></a><span data-ttu-id="d29d9-102">使用 IRow::Open 和 ISequentialStream 提取 BLOB 数据</span><span class="sxs-lookup"><span data-stu-id="d29d9-102">Fetching BLOB Data Using IRow::Open and ISequentialStream</span></span>
  <span data-ttu-id="d29d9-103">IRow::Open 只支持打开 DBGUID_STREAM 和 DBGUID_NULL 对象类型\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d29d9-103">**IRow::Open** supports only DBGUID_STREAM and DBGUID_NULL type of objects to be opened.</span></span>  
  
 <span data-ttu-id="d29d9-104">以下函数使用 IRow::Open\*\*\*\* 和 ISequentialStream\*\*\*\* 提取大型数据。</span><span class="sxs-lookup"><span data-stu-id="d29d9-104">The following function uses **IRow::Open** and **ISequentialStream** to fetch large data.</span></span>  
  
```  
void InitializeAndExecuteCommand()  
{  
    ULONG iidx;  
    WCHAR* wCmdString=OLESTR("SELECT * FROM MyTable");  
    // Do the initialization, create the session, and set command text.  
    hr = pICommandText->Execute(NULL, IID_IRow, NULL,   
                         &cNumRows,(IUnknown **)&pIRow)))  
    //Get 1 column at a time.  
    for(ULONG i=1; i <= NoOfColumns; i++)  
      GetSequentialColumn(pIRow, iidx);  
    // Do the clean up.  
}  
HRESULT GetSequentialColumn(IRow* pUnkRow, ULONG iCol)  
{  
    HRESULT hr = NOERROR;  
    ULONG cbRead = 0;  
    ULONG cbTotal = 0;  
    ULONG cColumns = 0;  
    ULONG cReads = 0;  
    ISequentialStream* pIStream = NULL;  
    WCHAR* pBuffer[kMaxBuff]; //50 chars read by ISequentialStream::Read()  
    DBCOLUMNINFO* prgInfo;  
    OLECHAR* pColNames;  
    IColumnsInfo* pIColumnsInfo;  
    DBID columnid;  
    DBCOLUMNACCESS column;  
  
    hr = pUnkRow->QueryInterface(IID_IColumnsInfo,   
                            (void**) &pIColumnsInfo);  
    hr = pIColumnsInfo->GetColumnInfo(&cColumns, &prgInfo, &pColNames);  
    // Get Column ID.  
    columnid = (prgInfo + (iCol - 1))->columnid;  
    // Get sequential stream object by calling IRow::Open.  
    hr = pUnkRow->Open(NULL, &columnid, DBGUID_STREAM, 0,   
                    IID_ISequentialStream,(LPUNKNOWN *)&pIStream);  
    ZeroMemory(pBuffer, kMaxBuff * sizeof(WCHAR));  
    // Read 50 chars at a time until no more data.  
    do  
    {  
        hr = pIStream->Read(pBuffer, kMaxBuff, &cbRead);  
        cbTotal = cbTotal + cbRead;  
        // Process the data.  
    } while(cbRead > 0);  
// Do the clean up.  
    return hr;  
}  
```  
  
 <span data-ttu-id="d29d9-105">大型数据可使用 ISequentialStream\*\*\*\* 接口进行绑定或检索。</span><span class="sxs-lookup"><span data-stu-id="d29d9-105">Large data can be bound or retrieved by using the **ISequentialStream** interface.</span></span> <span data-ttu-id="d29d9-106">对于绑定列，状态标志指示是否通过设置 DBSTATUS_S_TRUNCATED 来截断数据。</span><span class="sxs-lookup"><span data-stu-id="d29d9-106">For bound columns, the status flag indicates if the data is truncated by setting DBSTATUS_S_TRUNCATED.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29d9-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d29d9-107">See Also</span></span>  
 [<span data-ttu-id="d29d9-108">使用 IRow 提取 BLOB 数据</span><span class="sxs-lookup"><span data-stu-id="d29d9-108">Fetching BLOB Data Using IRow</span></span>](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
  
