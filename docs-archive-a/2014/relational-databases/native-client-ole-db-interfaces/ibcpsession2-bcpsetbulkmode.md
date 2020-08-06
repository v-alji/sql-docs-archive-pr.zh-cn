---
title: IBCPSession2::BCPSetBulkMode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
ms.assetid: babba19f-e67b-450c-b0e6-523a0f9d23ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 9605ff9b8effde1b4a77ba0d8554c719a8a8d1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590197"
---
# <a name="ibcpsession2bcpsetbulkmode"></a><span data-ttu-id="83ffc-102">IBCPSession2::BCPSetBulkMode</span><span class="sxs-lookup"><span data-stu-id="83ffc-102">IBCPSession2::BCPSetBulkMode</span></span>
  <span data-ttu-id="83ffc-103">IBCPSession2::BCPSetBulkMode 提供用于指定列格式的 [IBCPSession::BCPColFmt (OLE DB)](ibcpsession-bcpcolfmt-ole-db.md) 的替代方法。</span><span class="sxs-lookup"><span data-stu-id="83ffc-103">IBCPSession2::BCPSetBulkMode provides an alternative to [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) for specifying the column format.</span></span> <span data-ttu-id="83ffc-104">不同于设置单个列格式属性的 IBCPSession::BCPColFmt，IBCPSession2::BCPSetBulkMode 设置所有属性。</span><span class="sxs-lookup"><span data-stu-id="83ffc-104">Unlike IBCPSession::BCPColFmt, which sets individual column format attributes, IBCPSession2::BCPSetBulkMode sets all attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ffc-105">语法</span><span class="sxs-lookup"><span data-stu-id="83ffc-105">Syntax</span></span>  
  
```  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a><span data-ttu-id="83ffc-106">参数</span><span class="sxs-lookup"><span data-stu-id="83ffc-106">Arguments</span></span>  
 <span data-ttu-id="83ffc-107">*property*</span><span class="sxs-lookup"><span data-stu-id="83ffc-107">*property*</span></span>  
 <span data-ttu-id="83ffc-108">类型为 BYTE 的常量。</span><span class="sxs-lookup"><span data-stu-id="83ffc-108">A constant of type BYTE.</span></span> <span data-ttu-id="83ffc-109">相关的常量列表，请参阅“备注”部分中的表。</span><span class="sxs-lookup"><span data-stu-id="83ffc-109">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="83ffc-110">pField\*\*</span><span class="sxs-lookup"><span data-stu-id="83ffc-110">*pField*</span></span>  
 <span data-ttu-id="83ffc-111">指向字段终止符值的指针。</span><span class="sxs-lookup"><span data-stu-id="83ffc-111">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="83ffc-112">cbField</span><span class="sxs-lookup"><span data-stu-id="83ffc-112">cbField</span></span>  
 <span data-ttu-id="83ffc-113">字段终止符值的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="83ffc-113">The length in bytes of the field terminator value.</span></span>  
  
 <span data-ttu-id="83ffc-114">pRow</span><span class="sxs-lookup"><span data-stu-id="83ffc-114">pRow</span></span>  
 <span data-ttu-id="83ffc-115">指向行终止符值的指针。</span><span class="sxs-lookup"><span data-stu-id="83ffc-115">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="83ffc-116">cbRow</span><span class="sxs-lookup"><span data-stu-id="83ffc-116">cbRow</span></span>  
 <span data-ttu-id="83ffc-117">行终止符值的长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="83ffc-117">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="83ffc-118">返回</span><span class="sxs-lookup"><span data-stu-id="83ffc-118">Returns</span></span>  
 <span data-ttu-id="83ffc-119">IBCPSession2::BCPSetBulkMode 可以返回以下值之一：</span><span class="sxs-lookup"><span data-stu-id="83ffc-119">IBCPSession2::BCPSetBulkMode can return one of the following:</span></span>  
  
|||  
|-|-|  
|`S_OK`|<span data-ttu-id="83ffc-120">方法成功。</span><span class="sxs-lookup"><span data-stu-id="83ffc-120">The method succeeded.</span></span>|  
|`E_FAIL`|<span data-ttu-id="83ffc-121">出现访问接口特定的错误；要获取详细信息，请使用 ISQLServerErrorInfo 接口。</span><span class="sxs-lookup"><span data-stu-id="83ffc-121">A provider specific error occurred, for detailed information use the ISQLServerErrorInfo interface.</span></span>|  
|`E_UNEXPECTED`|<span data-ttu-id="83ffc-122">意外调用了该方法。</span><span class="sxs-lookup"><span data-stu-id="83ffc-122">The call to the method was unexpected.</span></span> <span data-ttu-id="83ffc-123">例如，在 `IBCPSession2::BCPInit` 调用 IBCPSession2：： BCPSetBulkMode 之前，未调用方法。</span><span class="sxs-lookup"><span data-stu-id="83ffc-123">For example, the `IBCPSession2::BCPInit` method was not called before calling IBCPSession2::BCPSetBulkMode.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="83ffc-124">参数无效。</span><span class="sxs-lookup"><span data-stu-id="83ffc-124">The argument was invalid.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="83ffc-125">内存不足错误。</span><span class="sxs-lookup"><span data-stu-id="83ffc-125">Out of memory error.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ffc-126">备注</span><span class="sxs-lookup"><span data-stu-id="83ffc-126">Remarks</span></span>  
 <span data-ttu-id="83ffc-127">可以使用 IBCPSession2::BCPSetBulkMode 从查询或表中创建大容量复制。</span><span class="sxs-lookup"><span data-stu-id="83ffc-127">IBCPSession2::BCPSetBulkMode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="83ffc-128">使用 IBCPSession2::BCPSetBulkMode 向外大容量复制查询语句时，必须先调用该方法，再调用 `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` 来指定查询语句。</span><span class="sxs-lookup"><span data-stu-id="83ffc-128">When IBCPSession2::BCPSetBulkMode is used to bulk copy out of a query statement, it must be called before calling `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` to specify the query statement.</span></span>  
  
 <span data-ttu-id="83ffc-129">应该避免在单个命令文本内将 RPC 调用语法与批查询语法结合使用（例如 `{rpc func};SELECT * from Tbl`）。</span><span class="sxs-lookup"><span data-stu-id="83ffc-129">You should avoid combining RPC call syntax with batch query syntax (`{rpc func};SELECT * from Tbl`, for example) in a single command text.</span></span>  <span data-ttu-id="83ffc-130">这将导致 ICommandPrepare::Prepare 返回错误，并阻止你检索元数据。</span><span class="sxs-lookup"><span data-stu-id="83ffc-130">This will cause ICommandPrepare::Prepare to return an error and prevent you from retrieving metadata.</span></span> <span data-ttu-id="83ffc-131">如果需要在单个命令文本内结合执行存储过程和批查询，请使用 ODBC CALL 语法（例如 `{call func}; SELECT * from Tbl`）。</span><span class="sxs-lookup"><span data-stu-id="83ffc-131">Use ODBC CALL syntax (`{call func}; SELECT * from Tbl`, for example) if you need to combine stored procedure execution and batch query in a single command text.</span></span>  
  
 <span data-ttu-id="83ffc-132">下表列出了 property 参数的常量\*\*。</span><span class="sxs-lookup"><span data-stu-id="83ffc-132">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="83ffc-133">属性</span><span class="sxs-lookup"><span data-stu-id="83ffc-133">Property</span></span>|<span data-ttu-id="83ffc-134">说明</span><span class="sxs-lookup"><span data-stu-id="83ffc-134">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="83ffc-135">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="83ffc-135">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="83ffc-136">指定字符输出模式。</span><span class="sxs-lookup"><span data-stu-id="83ffc-136">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="83ffc-137">与 BCP.EXE 中的-c 选项对应，并与*eUserDataType*属性设置为的 IBCPSession：： BCPColFmt 相对应 `BCP_TYPE_SQLCHARACTER` 。</span><span class="sxs-lookup"><span data-stu-id="83ffc-137">Corresponds to the -c option in BCP.EXE, and to IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="83ffc-138">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="83ffc-138">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="83ffc-139">指定 Unicode 输出模式。</span><span class="sxs-lookup"><span data-stu-id="83ffc-139">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="83ffc-140">对应于 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-w 选项，并将*eUserDataType*属性设置为 `BCP_TYPE_SQLNCHAR` 。</span><span class="sxs-lookup"><span data-stu-id="83ffc-140">Corresponds to the -w option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR`.</span></span>|  
|<span data-ttu-id="83ffc-141">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="83ffc-141">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="83ffc-142">指定对非字符类型使用本机类型，对字符类型使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="83ffc-142">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="83ffc-143">与*eUserDataType*属性设置为（ `BCP_TYPE_SQLNCHAR` 如果列类型为字符串，或者 `BCP_TYPE_DEFAULT` 如果不是字符串）的 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-N 选项对应。</span><span class="sxs-lookup"><span data-stu-id="83ffc-143">Corresponds to the -N option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR` if the column type is a string or `BCP_TYPE_DEFAULT` if not a string.</span></span>|  
|<span data-ttu-id="83ffc-144">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="83ffc-144">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="83ffc-145">指定本机数据库类型。</span><span class="sxs-lookup"><span data-stu-id="83ffc-145">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="83ffc-146">对应于 BCP.EXE 和 IBCPSession：： BCPColFmt 中的-n 选项，并将*eUserDataType*属性设置为 `BCP_TYPE_DEFAULT` 。</span><span class="sxs-lookup"><span data-stu-id="83ffc-146">Corresponds to the -n option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_DEFAULT`.</span></span>|  
  
 <span data-ttu-id="83ffc-147">可以调用 IBCPSession::BCPControl 和针对 IBCPSession::BCPControl 的 IBCPSession2::BCPSetBulkMode 选项，这些选项不会与 IBCPSession2::BCPSetBulkMode 冲突。</span><span class="sxs-lookup"><span data-stu-id="83ffc-147">You can call IBCPSession::BCPControl and IBCPSession2::BCPSetBulkMode for IBCPSession::BCPControl options that do not conflict with IBCPSession2::BCPSetBulkMode.</span></span> <span data-ttu-id="83ffc-148">例如，可以调用 IBCPSession：： BCPControl `BCP_OPTION_FIRST` 和 IBCPSession2：： BCPSetBulkMode。</span><span class="sxs-lookup"><span data-stu-id="83ffc-148">For example, you can call IBCPSession::BCPControl with `BCP_OPTION_FIRST` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="83ffc-149">不能将 IBCPSession：： BCPControl 与 `BCP_OPTION_TEXTFILE` 和 IBCPSession2：： BCPSetBulkMode 一起调用。</span><span class="sxs-lookup"><span data-stu-id="83ffc-149">You cannot call IBCPSession::BCPControl with `BCP_OPTION_TEXTFILE` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="83ffc-150">如果尝试使用包含 IBCPSession::BCPColFmt、IBCPSession::BCPControl 和 IBCPSession::BCPReadFmt 的函数调用序列来调用 IBCPSession2::BCPSetBulkMode，则其中一个函数调用将返回序列错误故障。</span><span class="sxs-lookup"><span data-stu-id="83ffc-150">If you attempt to call IBCPSession2::BCPSetBulkMode with a sequence of function calls that includes IBCPSession::BCPColFmt, IBCPSession::BCPControl, and IBCPSession::BCPReadFmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="83ffc-151">如果选择更正错误，请调用 IBCPSession::BCPInit 重置设置，然后重新开始。</span><span class="sxs-lookup"><span data-stu-id="83ffc-151">If you choose to correct the failure, call IBCPSession::BCPInit to reset the settings and start over.</span></span>  
  
 <span data-ttu-id="83ffc-152">下表提供了会造成函数序列错误的函数调用的一些示例：</span><span class="sxs-lookup"><span data-stu-id="83ffc-152">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="83ffc-153">调用序列</span><span class="sxs-lookup"><span data-stu-id="83ffc-153">Call sequence</span></span>  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a><span data-ttu-id="83ffc-154">示例</span><span class="sxs-lookup"><span data-stu-id="83ffc-154">Example</span></span>  
 <span data-ttu-id="83ffc-155">下面的示例使用 IBCPSession2::BCPSetBulkMode 的不同设置创建了四个文件。</span><span class="sxs-lookup"><span data-stu-id="83ffc-155">The following sample creates four files using different settings of IBCPSession2::BCPSetBulkMode.</span></span>  
  
```  
  
// compile with: sqlncli11.lib oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "sqlncli.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(SQLNCLI_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
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
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
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
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="83ffc-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83ffc-156">See Also</span></span>  
 [<span data-ttu-id="83ffc-157">IBCPSession2 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="83ffc-157">IBCPSession2 &#40;OLE DB&#41;</span></span>](ibcpsession2-ole-db.md)  
  
  
