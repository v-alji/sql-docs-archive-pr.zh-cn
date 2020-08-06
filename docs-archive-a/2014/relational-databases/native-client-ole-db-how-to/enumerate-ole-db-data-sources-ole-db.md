---
title: 枚举 OLE DB 数据源 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB]
ms.assetid: ba240060-3237-4fb8-b2fb-b87fda2b1e7a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1173feef8de657c43563b40bec763f81d630014e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692900"
---
# <a name="enumerate-ole-db-data-sources-ole-db"></a><span data-ttu-id="f77ef-102">枚举 OLE DB 数据源 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="f77ef-102">Enumerate OLE DB Data Sources (OLE DB)</span></span>
  <span data-ttu-id="f77ef-103">此示例显示如何使用枚举器对象列出可用数据源。</span><span class="sxs-lookup"><span data-stu-id="f77ef-103">This sample shows how to use the enumerator object to list the data sources available.</span></span>  
  
 <span data-ttu-id="f77ef-104">若要列出对 SQLOLEDB 枚举器可见的数据源，使用者将调用[ISourcesRowset：： GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312)方法。</span><span class="sxs-lookup"><span data-stu-id="f77ef-104">To list the data sources visible to the SQLOLEDB enumerator, the consumer calls the [ISourcesRowset::GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312) method.</span></span> <span data-ttu-id="f77ef-105">此方法返回与当前可见数据源有关的信息的行集。</span><span class="sxs-lookup"><span data-stu-id="f77ef-105">This method returns a rowset of information about the currently visible data sources.</span></span>  
  
 <span data-ttu-id="f77ef-106">根据所使用的网络库，将搜索相应的域以找到数据源。</span><span class="sxs-lookup"><span data-stu-id="f77ef-106">Depending on the network library used, the appropriate domain is searched for the data sources.</span></span> <span data-ttu-id="f77ef-107">对于命名管道，将搜索客户端登录到的域。</span><span class="sxs-lookup"><span data-stu-id="f77ef-107">For named pipes, it is the domain to which the client is logged on.</span></span> <span data-ttu-id="f77ef-108">对于 AppleTalk，将搜索默认区域。</span><span class="sxs-lookup"><span data-stu-id="f77ef-108">For AppleTalk, it is the default zone.</span></span> <span data-ttu-id="f77ef-109">对于 SPX/IPX，将搜索在平构数据库中找到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装的列表。</span><span class="sxs-lookup"><span data-stu-id="f77ef-109">For SPX/IPX, it is the list of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found in the bindery.</span></span> <span data-ttu-id="f77ef-110">对于 Banyan VINES，将搜索在本地网络中找到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="f77ef-110">For Banyan VINES, it is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found on the local network.</span></span> <span data-ttu-id="f77ef-111">不支持多协议和 TCP/IP 套接字。</span><span class="sxs-lookup"><span data-stu-id="f77ef-111">Multiprotocol and TCP/IP sockets are not supported.</span></span>  
  
 <span data-ttu-id="f77ef-112">在开关服务器时，可能需要几分钟来更新这些域中的信息。</span><span class="sxs-lookup"><span data-stu-id="f77ef-112">When the server is turned off or on, it can take few minutes to update the information in these domains.</span></span>  
  
 <span data-ttu-id="f77ef-113">此示例要求使用 AdventureWorks 示例数据库，其可从 [Microsoft SQL Server 示例和社区项目](https://go.microsoft.com/fwlink/?LinkID=85384)主页下载。</span><span class="sxs-lookup"><span data-stu-id="f77ef-113">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f77ef-114">请尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f77ef-114">When possible, use Windows Authentication.</span></span> <span data-ttu-id="f77ef-115">如果 Windows 身份验证不可用，请在运行时提示用户输入其凭据。</span><span class="sxs-lookup"><span data-stu-id="f77ef-115">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="f77ef-116">不要将凭据存储在一个文件中。</span><span class="sxs-lookup"><span data-stu-id="f77ef-116">Avoid storing credentials in a file.</span></span> <span data-ttu-id="f77ef-117">如果必须保存凭据，则应通过[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)对其进行加密。</span><span class="sxs-lookup"><span data-stu-id="f77ef-117">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-enumerate-ole-db-data-sources"></a><span data-ttu-id="f77ef-118">枚举 OLE DB 数据源</span><span class="sxs-lookup"><span data-stu-id="f77ef-118">To enumerate OLE DB data sources</span></span>  
  
1.  <span data-ttu-id="f77ef-119">通过调用 `ISourceRowset::GetSourcesRowset` 检索数据源的行集。</span><span class="sxs-lookup"><span data-stu-id="f77ef-119">Retrieve the source rowset by calling `ISourceRowset::GetSourcesRowset`.</span></span>  
  
2.  <span data-ttu-id="f77ef-120">通过调用 `GetColumnInfo::IColumnInfo` 查找枚举器行集的说明。</span><span class="sxs-lookup"><span data-stu-id="f77ef-120">Find the description of the enumerators rowset by calling `GetColumnInfo::IColumnInfo`.</span></span>  
  
3.  <span data-ttu-id="f77ef-121">根据列信息创建绑定结构。</span><span class="sxs-lookup"><span data-stu-id="f77ef-121">Create the binding structures from the column information.</span></span>  
  
4.  <span data-ttu-id="f77ef-122">通过调用 `IAccessor::CreateAccessor` 创建行集取值函数。</span><span class="sxs-lookup"><span data-stu-id="f77ef-122">Create the rowset accessor by calling `IAccessor::CreateAccessor`.</span></span>  
  
5.  <span data-ttu-id="f77ef-123">通过调用 `IRowset::GetNextRows` 提取行。</span><span class="sxs-lookup"><span data-stu-id="f77ef-123">Fetch the rows by calling `IRowset::GetNextRows`.</span></span>  
  
6.  <span data-ttu-id="f77ef-124">通过调用 `IRowset::GetData` 从行集中该行的副本检索数据，然后处理这些数据。</span><span class="sxs-lookup"><span data-stu-id="f77ef-124">Retrieve data from the rowset's copy of the row by calling `IRowset::GetData`, and process it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77ef-125">示例</span><span class="sxs-lookup"><span data-stu-id="f77ef-125">Example</span></span>  
 <span data-ttu-id="f77ef-126">使用 ole32.lib 编译并执行以下 C++ 代码列表。</span><span class="sxs-lookup"><span data-stu-id="f77ef-126">Compile with ole32.lib and execute the following C++ code listing.</span></span> <span data-ttu-id="f77ef-127">此应用程序连接到您的计算机上默认的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f77ef-127">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f77ef-128">在某些 Windows 操作系统上，您需要将 (localhost) 或 (local) 更改为您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="f77ef-128">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="f77ef-129">若要连接到命名实例，请将连接字符串从 L"(local)" 更改为 L"(local)\\\name"，其中 name 是命名实例。</span><span class="sxs-lookup"><span data-stu-id="f77ef-129">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="f77ef-130">默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 安装在命名实例中。</span><span class="sxs-lookup"><span data-stu-id="f77ef-130">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="f77ef-131">请确保 INCLUDE 环境变量包含包含 sqlncli.msi 的目录。</span><span class="sxs-lookup"><span data-stu-id="f77ef-131">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
```  
// compile with: ole32.lib  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <windows.h>  
#include <stddef.h>  
#include <oledb.h>  
#include <oledberr.h>  
#include <sqlncli.h>  
#include <stdio.h>  
  
#define NUMROWS_CHUNK  5  
  
// AdjustLen supports binding on four-byte boundaries.  
_inline DBLENGTH AdjustLen(DBLENGTH cb) {   
   return ( (cb + 3) & ~3 );  
}  
  
// Get the characteristics of the rowset (the IColumnsInfo interface).  
HRESULT GetColumnInfo ( IRowset* pIRowset,   
                        DBORDINAL* pnCols,   
                        DBCOLUMNINFO** ppColumnsInfo,  
                        OLECHAR** ppColumnStrings ) {  
   IColumnsInfo* pIColumnsInfo;  
   HRESULT hr;  
  
   *pnCols = 0;  
   if (FAILED(pIRowset->QueryInterface(IID_IColumnsInfo, (void**) &pIColumnsInfo)))  
      return (E_FAIL);  
  
   hr = pIColumnsInfo->GetColumnInfo(pnCols, ppColumnsInfo, ppColumnStrings);  
  
   if (FAILED(hr)) {}   /* Process error */   
  
   pIColumnsInfo->Release();  
   return (hr);  
}  
  
// Create binding structures from column information. Binding structures  
// will be used to create an accessor that allows row value retrieval.  
void CreateDBBindings ( DBORDINAL nCols,   
                        DBCOLUMNINFO* pColumnsInfo,   
                        DBBINDING** ppDBBindings,  
                        BYTE** ppRowValues ) {  
   ULONG nCol;  
   DBLENGTH cbRow = 0;  
   DBLENGTH cbCol;  
   DBBINDING* pDBBindings;  
   BYTE* pRowValues;  
  
   pDBBindings = new DBBINDING[nCols];  
   if (!(pDBBindings /* = new DBBINDING[nCols] */ ))  
      return;  
  
   for ( nCol = 0 ; nCol < nCols ; nCol++ ) {  
      pDBBindings[nCol].iOrdinal = nCol + 1;  
      pDBBindings[nCol].pTypeInfo = NULL;  
      pDBBindings[nCol].pObject = NULL;  
      pDBBindings[nCol].pBindExt = NULL;  
      pDBBindings[nCol].dwPart = DBPART_VALUE;  
      pDBBindings[nCol].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pDBBindings[nCol].eParamIO = DBPARAMIO_NOTPARAM;  
      pDBBindings[nCol].dwFlags = 0;  
      pDBBindings[nCol].wType = pColumnsInfo[nCol].wType;  
      pDBBindings[nCol].bPrecision = pColumnsInfo[nCol].bPrecision;  
      pDBBindings[nCol].bScale = pColumnsInfo[nCol].bScale;  
  
      cbCol = pColumnsInfo[nCol].ulColumnSize;  
  
      switch (pColumnsInfo[nCol].wType) {  
      case DBTYPE_STR: {  
            cbCol += 1;  
            break;  
         }  
  
      case DBTYPE_WSTR: {  
            cbCol = (cbCol + 1) * sizeof(WCHAR);  
            break;  
         }  
  
      default:  
         break;  
      }  
  
      pDBBindings[nCol].obValue = cbRow;  
      pDBBindings[nCol].cbMaxLen = cbCol;  
      cbRow += AdjustLen(cbCol);  
   }  
  
   pRowValues = new BYTE[cbRow];  
   *ppDBBindings = pDBBindings;  
   *ppRowValues = pRowValues;  
}  
  
int main() {  
   ISourcesRowset* pISourceRowset = NULL;      
   IRowset* pIRowset = NULL;          
   IAccessor* pIAccessor = NULL;  
   DBBINDING* pDBBindings = NULL;              
  
   HROW* pRows = new HROW[500];      
   HACCESSOR hAccessorRetrieve = NULL;          
   ULONG DSSeqNumber = 0;  
  
   HRESULT hr;  
   DBORDINAL nCols;  
   DBCOLUMNINFO* pColumnsInfo = NULL;  
   OLECHAR* pColumnStrings = NULL;  
   DBBINDSTATUS* pDBBindStatus = NULL;  
  
   BYTE* pRowValues = NULL;  
   DBCOUNTITEM cRowsObtained;  
   ULONG iRow;  
   char* pMultiByte = NULL;  
   short* psSourceType = NULL;  
   BYTE* pDatasource = NULL;  
  
   if (!pRows)  
      return (0);  
  
   // Initialize COM library.  
   CoInitialize(NULL);  
  
   // Initialize the enumerator.  
   if (FAILED(CoCreateInstance(CLSID_SQLNCLI11_ENUMERATOR,   
                               NULL,  
                               CLSCTX_INPROC_SERVER,   
                               IID_ISourcesRowset,   
                               (void**)&pISourceRowset))) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Retrieve the source rowset.  
   hr = pISourceRowset->GetSourcesRowset(NULL, IID_IRowset, 0, NULL, (IUnknown**)&pIRowset);  
  
   pISourceRowset->Release();  
   if (FAILED(hr)) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Get the description of the enumerator's rowset.  
   if (FAILED(hr = GetColumnInfo(pIRowset, &nCols, &pColumnsInfo, &pColumnStrings))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the binding structures.  
   CreateDBBindings(nCols, pColumnsInfo, &pDBBindings, &pRowValues);  
   pDBBindStatus = new DBBINDSTATUS[nCols];  
  
   if (sizeof(TCHAR) != sizeof(WCHAR))  
      pMultiByte = new char[pDBBindings[0].cbMaxLen];  
  
   if (FAILED(pIRowset->QueryInterface(IID_IAccessor, (void**)&pIAccessor))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the rowset accessor.  
   if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,   
                                              nCols,  
                                              pDBBindings,   
                                              0,   
                                              &hAccessorRetrieve,   
                                              pDBBindStatus))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Process all the rows, NUMROWS_CHUNK rows at a time.  
   while (SUCCEEDED(hr)) {  
      hr = pIRowset->GetNextRows(NULL, 0, NUMROWS_CHUNK, &cRowsObtained, &pRows);  
      if( FAILED(hr)) {  
         // process error  
      }  
      if (cRowsObtained == 0 || FAILED(hr))  
         break;  
  
      for (iRow = 0 ; iRow < cRowsObtained ; iRow++) {  
         // Get the rowset data.  
         if (SUCCEEDED(hr = pIRowset->GetData(pRows[iRow], hAccessorRetrieve, pRowValues))) {  
            psSourceType = (short *)(pRowValues + pDBBindings[3].obValue);  
  
            if (*psSourceType == DBSOURCETYPE_DATASOURCE) {  
               DSSeqNumber = DSSeqNumber + 1;   // Data source counter.  
               pDatasource = (pRowValues + pDBBindings[0].obValue);  
  
               if ( sizeof(TCHAR) != sizeof(WCHAR) ) {  
                  WideCharToMultiByte(CP_ACP,   
                                      0,  
                                      (WCHAR*)pDatasource,   
                                      -1,   
                                      pMultiByte,  
                                      static_cast<int>(pDBBindings[0].cbMaxLen),   
                                      NULL,   
                                      NULL);  
  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pMultiByte );  
               }  
               else {  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pDatasource );  
               }  
            }  
         }  
      }  
      pIRowset->ReleaseRows(cRowsObtained, pRows, NULL, NULL, NULL);  
   }  
  
   // Release COM library.  
   CoUninitialize();  
  
SAFE_EXIT:  
   // Do the clean-up.  
   return TRUE;  
}  
```  
  
  
