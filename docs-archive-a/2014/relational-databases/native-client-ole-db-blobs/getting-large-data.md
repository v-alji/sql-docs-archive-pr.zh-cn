---
title: 获取大型数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- DBPROP_ACCESSORDER property
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: a31c5632-96aa-483f-a307-004c5149fbc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 38602df026d2e752a758672dde23a59a26ad4917
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693801"
---
# <a name="getting-large-data"></a><span data-ttu-id="683a9-102">获取大型数据</span><span class="sxs-lookup"><span data-stu-id="683a9-102">Getting Large Data</span></span>
  <span data-ttu-id="683a9-103">通常，使用者应该隔离用来创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 OLE DB 提供程序存储对象的代码，该代码用于处理未通过**ISequentialStream**接口指针引用的数据。</span><span class="sxs-lookup"><span data-stu-id="683a9-103">In general, consumers should isolate code that creates a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider storage object from other code that handles data not referenced through an **ISequentialStream** interface pointer.</span></span>  
  
 <span data-ttu-id="683a9-104">本主题涉及可用于以下函数的功能：</span><span class="sxs-lookup"><span data-stu-id="683a9-104">This topic refers to functionality available with the following functions:</span></span>  
  
-   <span data-ttu-id="683a9-105">IRowset:GetData</span><span class="sxs-lookup"><span data-stu-id="683a9-105">IRowset:GetData</span></span>  
  
-   <span data-ttu-id="683a9-106">IRow::GetColumns</span><span class="sxs-lookup"><span data-stu-id="683a9-106">IRow::GetColumns</span></span>  
  
-   <span data-ttu-id="683a9-107">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="683a9-107">ICommand::Execute</span></span>  
  
 <span data-ttu-id="683a9-108">如果行集属性组) 中 (的 DBPROP_ACCESSORDER 属性设置为 DBPROPVAL_AO_SEQUENTIAL 或 DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS 的值之一，则使用者应该只在调用**GetNextRows**方法时提取单行数据，因为 BLOB 数据不会被缓冲。</span><span class="sxs-lookup"><span data-stu-id="683a9-108">If the DBPROP_ACCESSORDER property (in the rowset property group) is set to either of the values DBPROPVAL_AO_SEQUENTIAL or DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS, the consumer should fetch only a single row of data in a call to the **GetNextRows** method because BLOB data is not buffered.</span></span> <span data-ttu-id="683a9-109">如果 DBPROP_ACCESSORDER 的值设置为 DBPROPVAL_AO_RANDOM，则使用者可以在 GetNextRows 中提取多行数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="683a9-109">If the value of DBPROP_ACCESSORDER is set to DBPROPVAL_AO_RANDOM, the consumer can fetch multiple rows of data in **GetNextRows**.</span></span>  
  
 <span data-ttu-id="683a9-110">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者请求之前，Native Client OLE DB 提供程序不会从检索大数据 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="683a9-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not retrieve large data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until requested to do so by the consumer.</span></span> <span data-ttu-id="683a9-111">使用者应在一个取值函数中绑定所有短 (Short) 数据，然后根据需要使用一个或多个临时取值函数检索大型数据值。</span><span class="sxs-lookup"><span data-stu-id="683a9-111">The consumer should bind all short data in one accessor, and then use one or more temporary accessors to retrieve large data values as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="683a9-112">示例</span><span class="sxs-lookup"><span data-stu-id="683a9-112">Example</span></span>  
 <span data-ttu-id="683a9-113">本示例从单一列中检索大型数据值：</span><span class="sxs-lookup"><span data-stu-id="683a9-113">This example retrieves a large data value from a single column:</span></span>  
  
```  
HRESULT GetUnboundData  
    (  
    IRowset* pIRowset,  
    HROW hRow,  
    ULONG nCol,   
    BYTE* pUnboundData  
    )  
    {  
    UINT                cbRow = sizeof(IUnknown*) + sizeof(ULONG);  
    BYTE*               pRow = new BYTE[cbRow];  
  
    DBOBJECT            dbobject;  
  
    IAccessor*          pIAccessor = NULL;  
    HACCESSOR           haccessor;  
  
    DBBINDING           dbbinding;  
    ULONG               ulbindstatus;  
  
    ULONG               dwStatus;  
    ISequentialStream*  pISequentialStream;  
    ULONG               cbRead;  
  
    HRESULT             hr;  
  
    // Set up the DBOBJECT structure.  
    dbobject.dwFlags = STGM_READ;  
    dbobject.iid = IID_ISequentialStream;  
  
    // Create the DBBINDING, requesting a storage-object pointer from  
    // The SQL Server Native Client OLE DB provider.  
    dbbinding.iOrdinal = nCol;  
    dbbinding.obValue = 0;  
    dbbinding.obStatus = sizeof(IUnknown*);  
    dbbinding.obLength = 0;  
    dbbinding.pTypeInfo = NULL;  
    dbbinding.pObject = &dbobject;  
    dbbinding.pBindExt = NULL;  
    dbbinding.dwPart = DBPART_VALUE | DBPART_STATUS;  
    dbbinding.dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
    dbbinding.eParamIO = DBPARAMIO_NOTPARAM;  
    dbbinding.cbMaxLen = 0;  
    dbbinding.dwFlags = 0;  
    dbbinding.wType = DBTYPE_IUNKNOWN;  
    dbbinding.bPrecision = 0;  
    dbbinding.bScale = 0;  
  
    if (FAILED(hr = pIRowset->  
        QueryInterface(IID_IAccessor, (void**) &pIAccessor)))  
        {  
        // Process QueryInterface failure.  
        return (hr);  
        }  
  
    // Create the accessor.  
    if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA, 1,  
        &dbbinding, 0, &haccessor, &ulbindstatus)))  
        {  
        // Process error from CreateAccessor.  
        pIAccessor->Release();  
        return (hr);  
        }  
  
    // Read and process BLOCK_SIZE bytes at a time.  
    if (SUCCEEDED(hr = pIRowset->GetData(hRow, haccessor, pRow)))  
        {  
        dwStatus = *((ULONG*) (pRow + dbbinding.obStatus));  
  
        if (dwStatus == DBSTATUS_S_ISNULL)  
            {  
            // Process NULL data  
            }  
        else if (dwStatus == DBSTATUS_S_OK)  
            {  
            pISequentialStream = *((ISequentialStream**)   
                (pRow + dbbinding.obValue));  
  
            do  
                {  
                if (SUCCEEDED(hr =  
                    pISequentialStream->Read(pUnboundData,  
                    BLOCK_SIZE, &cbRead)))  
                    {  
                    pUnboundData += cbRead;  
                    }  
                }  
            while (SUCCEEDED(hr) && cbRead >= BLOCK_SIZE);  
  
            pISequentialStream->Release();  
            }  
        }  
    else  
        {  
        // Process error from GetData.  
        }  
  
    pIAccessor->ReleaseAccessor(haccessor, NULL);  
    pIAccessor->Release();  
    delete [] pRow;  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="683a9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="683a9-114">See Also</span></span>  
 <span data-ttu-id="683a9-115">[Blob 和 OLE 对象](blobs-and-ole-objects.md) </span><span class="sxs-lookup"><span data-stu-id="683a9-115">[BLOBs and OLE Objects](blobs-and-ole-objects.md) </span></span>  
 [<span data-ttu-id="683a9-116">使用大值类型</span><span class="sxs-lookup"><span data-stu-id="683a9-116">Using Large Value Types</span></span>](../native-client/features/using-large-value-types.md)  
  
  
