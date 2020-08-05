---
title: IMDEmbedded 接口 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 9dba8c68-4bef-4c2b-815c-c286f1a1939b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 331f8c33f7748e6591acd6d6ecda7a03ef7d8137
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580426"
---
# <a name="imdembedded-interface"></a><span data-ttu-id="62863-102">IMDEmbedded 接口</span><span class="sxs-lookup"><span data-stu-id="62863-102">IMDEmbedded Interface</span></span>
  <span data-ttu-id="62863-103">IMDEmbedded 接口是用于管理嵌入的 PowerPivot 数据库或表格模型数据库的公共接口。</span><span class="sxs-lookup"><span data-stu-id="62863-103">The IMDEmbedded interface is a public interface used to manage an embedded PowerPivot database or a tabular model database.</span></span> <span data-ttu-id="62863-104">此接口继承自 `IPersistStream` 接口。</span><span class="sxs-lookup"><span data-stu-id="62863-104">The interface inherits from the `IPersistStream` interface.</span></span> <span data-ttu-id="62863-105">此接口允许以下操作：</span><span class="sxs-lookup"><span data-stu-id="62863-105">The interface allows for the following operations:</span></span>  
  
-   <span data-ttu-id="62863-106">获取对容器文档中嵌入流的标识符。</span><span class="sxs-lookup"><span data-stu-id="62863-106">Get an identifier to the embedded stream in the container document.</span></span>  
  
-   <span data-ttu-id="62863-107">设置包含文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="62863-107">Set the URL of the containing document.</span></span>  
  
-   <span data-ttu-id="62863-108">设置一个标志，以便指示嵌入应用程序是否处于宿主环境中。</span><span class="sxs-lookup"><span data-stu-id="62863-108">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
-   <span data-ttu-id="62863-109">设置嵌入应用程序使用的临时文件的路径。</span><span class="sxs-lookup"><span data-stu-id="62863-109">Set the path to temporary files used by the embedding application.</span></span>  
  
-   <span data-ttu-id="62863-110">取消当前嵌入的操作。</span><span class="sxs-lookup"><span data-stu-id="62863-110">Cancel the current embedded operation.</span></span>  
  
-   <span data-ttu-id="62863-111">获取用于保存嵌入对象的流的估计大小 (以字节为单位) 。</span><span class="sxs-lookup"><span data-stu-id="62863-111">Get the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="62863-112">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-112">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="62863-113">验证嵌入的数据库自上次保存后是否已更改。</span><span class="sxs-lookup"><span data-stu-id="62863-113">Verify if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="62863-114">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-114">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="62863-115">将嵌入的数据库加载到本地或进程内引擎。</span><span class="sxs-lookup"><span data-stu-id="62863-115">Load the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="62863-116">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-116">Inherited from `IPersistStream`.</span></span>  
  
-   <span data-ttu-id="62863-117">将本地或进程内数据库保存到容器文档中的嵌入流。</span><span class="sxs-lookup"><span data-stu-id="62863-117">Save the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="62863-118">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-118">Inherited from `IPersistStream`.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="62863-119">参考</span><span class="sxs-lookup"><span data-stu-id="62863-119">Reference</span></span>  
 <span data-ttu-id="62863-120">以下参考文档介绍了 `IMDEmbedded` **msmd.h**头文件中显示的接口。</span><span class="sxs-lookup"><span data-stu-id="62863-120">The following reference documents the `IMDEmbedded` interface as presented in **msmd.h** header file.</span></span>  
  
### <a name="source-file-pxoembeddeddataidl"></a><span data-ttu-id="62863-121">源文件：PXOEmbeddedData.idl</span><span class="sxs-lookup"><span data-stu-id="62863-121">Source file: PXOEmbeddedData.idl</span></span>  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a><span data-ttu-id="62863-122">IMDEmbeddedData::GetStreamIdentifier</span><span class="sxs-lookup"><span data-stu-id="62863-122">IMDEmbeddedData::GetStreamIdentifier</span></span>  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-123">说明</span><span class="sxs-lookup"><span data-stu-id="62863-123">Description</span></span>  
 <span data-ttu-id="62863-124">获取宿主应用程序使用的针对容器文档中嵌入流的标识符。</span><span class="sxs-lookup"><span data-stu-id="62863-124">Gets the identifier used by the host application to the embedded stream in the container document.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-125">参数</span><span class="sxs-lookup"><span data-stu-id="62863-125">Parameters</span></span>  
 <span data-ttu-id="62863-126">*out_pbstrStreamId*</span><span class="sxs-lookup"><span data-stu-id="62863-126">*out_pbstrStreamId*</span></span>  
 <span data-ttu-id="62863-127">指定流标识符的位置。</span><span class="sxs-lookup"><span data-stu-id="62863-127">Specifies the location of the stream identifier.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-128">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-128">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-129">流标识符已成功返回。</span><span class="sxs-lookup"><span data-stu-id="62863-129">The stream identifier was successfully returned.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="62863-130">没有流标识符。</span><span class="sxs-lookup"><span data-stu-id="62863-130">There is no stream identifier.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-131">在访问流标识符时出现错误。</span><span class="sxs-lookup"><span data-stu-id="62863-131">An error occurred accessing the stream identifier.</span></span>  
  
#### <a name="remarks"></a><span data-ttu-id="62863-132">备注</span><span class="sxs-lookup"><span data-stu-id="62863-132">Remarks</span></span>  
 <span data-ttu-id="62863-133">为了确认当前连接是否包含嵌入数据库，用户应从 OLE DB 连接属性查看 DBPROP_MSMD_EMBEDDED_DATA 属性的值。</span><span class="sxs-lookup"><span data-stu-id="62863-133">To verify if the current connection contains an embedded database, the user should check the value of the DBPROP_MSMD_EMBEDDED_DATA property from the OLE DB connection properties.</span></span>  
  
 <span data-ttu-id="62863-134">DBPROP_MSMD_EMBEDDED_DATA 的可能值包括：</span><span class="sxs-lookup"><span data-stu-id="62863-134">The possible values for DBPROP_MSMD_EMBEDDED_DATA are:</span></span>  
  
|<span data-ttu-id="62863-135">名称</span><span class="sxs-lookup"><span data-stu-id="62863-135">Name</span></span>|<span data-ttu-id="62863-136">值</span><span class="sxs-lookup"><span data-stu-id="62863-136">Value</span></span>|<span data-ttu-id="62863-137">定义</span><span class="sxs-lookup"><span data-stu-id="62863-137">Definition</span></span>|  
|----------|-----------|----------------|  
|<span data-ttu-id="62863-138">DBPROPVAL_EMBED_NONE</span><span class="sxs-lookup"><span data-stu-id="62863-138">DBPROPVAL_EMBED_NONE</span></span>|<span data-ttu-id="62863-139">0x00</span><span class="sxs-lookup"><span data-stu-id="62863-139">0x00</span></span>|<span data-ttu-id="62863-140">没有可用的嵌入数据库</span><span class="sxs-lookup"><span data-stu-id="62863-140">No embedded database available</span></span>|  
|<span data-ttu-id="62863-141">DBPROPVAL_EMBED_EMBEDDED</span><span class="sxs-lookup"><span data-stu-id="62863-141">DBPROPVAL_EMBED_EMBEDDED</span></span>|<span data-ttu-id="62863-142">0x01</span><span class="sxs-lookup"><span data-stu-id="62863-142">0x01</span></span>|<span data-ttu-id="62863-143">当前应用程序包含嵌入数据库</span><span class="sxs-lookup"><span data-stu-id="62863-143">The current application contains the embedded database</span></span>|  
|<span data-ttu-id="62863-144">DBPROPVAL_EMBED_LINKED</span><span class="sxs-lookup"><span data-stu-id="62863-144">DBPROPVAL_EMBED_LINKED</span></span>|<span data-ttu-id="62863-145">0x02</span><span class="sxs-lookup"><span data-stu-id="62863-145">0x02</span></span>|<span data-ttu-id="62863-146">嵌入数据库在远程应用程序（例如 SharePoint Server）中承载</span><span class="sxs-lookup"><span data-stu-id="62863-146">The embedded database is hosted in a remote application (i.e. SharePoint Server)</span></span>|  
  
#### <a name="source"></a><span data-ttu-id="62863-147">源</span><span class="sxs-lookup"><span data-stu-id="62863-147">Source</span></span>  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a><span data-ttu-id="62863-148">IMDEmbeddedData::SetContainerURL</span><span class="sxs-lookup"><span data-stu-id="62863-148">IMDEmbeddedData::SetContainerURL</span></span>  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-149">说明</span><span class="sxs-lookup"><span data-stu-id="62863-149">Description</span></span>  
 <span data-ttu-id="62863-150">设置包含嵌入流的文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="62863-150">Sets the URL for the file containing the embedded stream.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-151">参数</span><span class="sxs-lookup"><span data-stu-id="62863-151">Parameters</span></span>  
 <span data-ttu-id="62863-152">*in_bstrURL*</span><span class="sxs-lookup"><span data-stu-id="62863-152">*in_bstrURL*</span></span>  
 <span data-ttu-id="62863-153">指定包含文档的 URL。</span><span class="sxs-lookup"><span data-stu-id="62863-153">Specifies the URL for the containing document.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-154">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-154">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-155">容器 URL 已成功设置。</span><span class="sxs-lookup"><span data-stu-id="62863-155">The container URL was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-156">在设置容器 URL 时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-156">An error occurred while setting the container URL.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="62863-157">源</span><span class="sxs-lookup"><span data-stu-id="62863-157">Source</span></span>  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a><span data-ttu-id="62863-158">IMDEmbeddedData::SetHosted</span><span class="sxs-lookup"><span data-stu-id="62863-158">IMDEmbeddedData::SetHosted</span></span>  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-159">说明</span><span class="sxs-lookup"><span data-stu-id="62863-159">Description</span></span>  
 <span data-ttu-id="62863-160">设置一个标志，以便指示嵌入应用程序是否处于宿主环境中。</span><span class="sxs-lookup"><span data-stu-id="62863-160">Set a flag to indicate if the embedding application is in a hosted environment.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-161">参数</span><span class="sxs-lookup"><span data-stu-id="62863-161">Parameters</span></span>  
 <span data-ttu-id="62863-162">*in_ftHosted*</span><span class="sxs-lookup"><span data-stu-id="62863-162">*in_ftHosted*</span></span>  
 <span data-ttu-id="62863-163">如果调用方在服务应用程序（例如 IIS）中承载，则为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="62863-163">TRUE if caller is in a hosted in a service application (like IIS).</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-164">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-164">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-165">该标志已成功设置。</span><span class="sxs-lookup"><span data-stu-id="62863-165">The flag was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-166">在设置标志时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-166">An error occurred while setting the flag.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="62863-167">源</span><span class="sxs-lookup"><span data-stu-id="62863-167">Source</span></span>  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a><span data-ttu-id="62863-168">IMDEmbeddedData::SetTempDirPath</span><span class="sxs-lookup"><span data-stu-id="62863-168">IMDEmbeddedData::SetTempDirPath</span></span>  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-169">说明</span><span class="sxs-lookup"><span data-stu-id="62863-169">Description</span></span>  
 <span data-ttu-id="62863-170">设置嵌入应用程序使用的临时文件的路径。</span><span class="sxs-lookup"><span data-stu-id="62863-170">Set the path to temporary files used by the embedding application.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-171">参数</span><span class="sxs-lookup"><span data-stu-id="62863-171">Parameters</span></span>  
 <span data-ttu-id="62863-172">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="62863-172">*in_bstrPath*</span></span>  
 <span data-ttu-id="62863-173">宿主应用程序用于临时文件的路径。</span><span class="sxs-lookup"><span data-stu-id="62863-173">The path used by the host application for temporary files.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-174">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-174">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-175">临时文件目录已成功设置。</span><span class="sxs-lookup"><span data-stu-id="62863-175">The temporary file directory was successfully set.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-176">在设置路径时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-176">An error occurred while setting the path.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="62863-177">源</span><span class="sxs-lookup"><span data-stu-id="62863-177">Source</span></span>  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a><span data-ttu-id="62863-178">IMDEmbeddedData::Cancel</span><span class="sxs-lookup"><span data-stu-id="62863-178">IMDEmbeddedData::Cancel</span></span>  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-179">说明</span><span class="sxs-lookup"><span data-stu-id="62863-179">Description</span></span>  
 <span data-ttu-id="62863-180">取消当前嵌入的数据库操作</span><span class="sxs-lookup"><span data-stu-id="62863-180">Cancels the current embedded database operation</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-181">参数</span><span class="sxs-lookup"><span data-stu-id="62863-181">Parameters</span></span>  
 <span data-ttu-id="62863-182">无。</span><span class="sxs-lookup"><span data-stu-id="62863-182">None.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-183">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-183">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-184">操作已成功取消。</span><span class="sxs-lookup"><span data-stu-id="62863-184">The operation was successfully cancelled.</span></span>  
  
 `DB_E_CANTCANCEL`  
 <span data-ttu-id="62863-185">当前没有正在进行中的可取消操作。</span><span class="sxs-lookup"><span data-stu-id="62863-185">No cancellable operation is currently in progress.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-186">在取消嵌入的操作时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-186">An error occurred while cancelling the embedded operation.</span></span>  
  
#### <a name="source"></a><span data-ttu-id="62863-187">源</span><span class="sxs-lookup"><span data-stu-id="62863-187">Source</span></span>  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a><span data-ttu-id="62863-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span><span class="sxs-lookup"><span data-stu-id="62863-188">IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)</span></span>  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-189">说明</span><span class="sxs-lookup"><span data-stu-id="62863-189">Description</span></span>  
 <span data-ttu-id="62863-190">获取流的估计大小（以字节为单位）以便保存嵌入的对象。</span><span class="sxs-lookup"><span data-stu-id="62863-190">Gets the estimated size (in bytes) of the stream to save the embedded object.</span></span> <span data-ttu-id="62863-191">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-191">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-192">参数</span><span class="sxs-lookup"><span data-stu-id="62863-192">Parameters</span></span>  
 <span data-ttu-id="62863-193">*in_bstrPath*</span><span class="sxs-lookup"><span data-stu-id="62863-193">*in_bstrPath*</span></span>  
 <span data-ttu-id="62863-194">嵌入的数据库图像的估计大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="62863-194">The estimated size (in bytes) of the embedded database image.</span></span>  
  
#### <a name="return-value"></a><span data-ttu-id="62863-195">返回值</span><span class="sxs-lookup"><span data-stu-id="62863-195">Return Value</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-196">该大小已成功获取。</span><span class="sxs-lookup"><span data-stu-id="62863-196">The size was successfully obtained.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-197">在获取大小时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-197">An error occurred while obtaining the size.</span></span>  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a><span data-ttu-id="62863-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span><span class="sxs-lookup"><span data-stu-id="62863-198">IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)</span></span>  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-199">说明</span><span class="sxs-lookup"><span data-stu-id="62863-199">Description</span></span>  
 <span data-ttu-id="62863-200">确认自上次保存后嵌入的数据库是否已更改。</span><span class="sxs-lookup"><span data-stu-id="62863-200">Verifies if the embedded database has changed since it was last saved.</span></span> <span data-ttu-id="62863-201">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-201">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-202">参数</span><span class="sxs-lookup"><span data-stu-id="62863-202">Parameters</span></span>  
 <span data-ttu-id="62863-203">无</span><span class="sxs-lookup"><span data-stu-id="62863-203">none</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="62863-204">返回值 (s) </span><span class="sxs-lookup"><span data-stu-id="62863-204">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-205">自上次保存后数据库已更改。</span><span class="sxs-lookup"><span data-stu-id="62863-205">The database has changed since it was last saved.</span></span>  
  
 `S_FALSE`  
 <span data-ttu-id="62863-206">自上次保存后数据库未更改。</span><span class="sxs-lookup"><span data-stu-id="62863-206">The database has not changed since it was last saved.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-207">在获取数据库状态时出错。</span><span class="sxs-lookup"><span data-stu-id="62863-207">An error occurred while obtaining the database state.</span></span>  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a><span data-ttu-id="62863-208">IMDEmbeddedData::Load (IPersistStream::Load)</span><span class="sxs-lookup"><span data-stu-id="62863-208">IMDEmbeddedData::Load (IPersistStream::Load)</span></span>  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-209">说明</span><span class="sxs-lookup"><span data-stu-id="62863-209">Description</span></span>  
 <span data-ttu-id="62863-210">将嵌入的数据库加载到本地或进程内引擎。</span><span class="sxs-lookup"><span data-stu-id="62863-210">Loads the embedded database to the local or in-process engine.</span></span> <span data-ttu-id="62863-211">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-211">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-212">参数</span><span class="sxs-lookup"><span data-stu-id="62863-212">Parameters</span></span>  
 <span data-ttu-id="62863-213">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="62863-213">*in_pStm*</span></span>  
 <span data-ttu-id="62863-214">指向从其加载嵌入的数据库的流接口的指针。</span><span class="sxs-lookup"><span data-stu-id="62863-214">A pointer to a stream interface from where to load the embedded database.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="62863-215">返回值 (s) </span><span class="sxs-lookup"><span data-stu-id="62863-215">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-216">数据库已成功加载。</span><span class="sxs-lookup"><span data-stu-id="62863-216">The database was successfully loaded.</span></span>  
  
 `E_OUTOFMEMORY`  
 <span data-ttu-id="62863-217">没有足够的内存可用来加载数据库。</span><span class="sxs-lookup"><span data-stu-id="62863-217">Not enough memory to load the database.</span></span>  
  
 `E_FAIL`  
 <span data-ttu-id="62863-218">在加载数据库时出错，不同于 `E_OUTOFMEMORY`。</span><span class="sxs-lookup"><span data-stu-id="62863-218">An error occurred while loading the database, different than `E_OUTOFMEMORY`.</span></span>  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a><span data-ttu-id="62863-219">IMDEmbeddedData::Save (IPersistStream::Save)</span><span class="sxs-lookup"><span data-stu-id="62863-219">IMDEmbeddedData::Save (IPersistStream::Save)</span></span>  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a><span data-ttu-id="62863-220">说明</span><span class="sxs-lookup"><span data-stu-id="62863-220">Description</span></span>  
 <span data-ttu-id="62863-221">将本地或进程内数据库保存到容器文档中的嵌入流中。</span><span class="sxs-lookup"><span data-stu-id="62863-221">Saves the local or in-process database to the embedded stream in the container document.</span></span> <span data-ttu-id="62863-222">从 `IPersistStream` 继承。</span><span class="sxs-lookup"><span data-stu-id="62863-222">Inherited from `IPersistStream`.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="62863-223">参数</span><span class="sxs-lookup"><span data-stu-id="62863-223">Parameters</span></span>  
 <span data-ttu-id="62863-224">*in_pStm*</span><span class="sxs-lookup"><span data-stu-id="62863-224">*in_pStm*</span></span>  
 <span data-ttu-id="62863-225">指向将嵌入的数据库保存到的流接口的指针。</span><span class="sxs-lookup"><span data-stu-id="62863-225">A pointer to a stream interface to where to save the embedded database.</span></span>  
  
 <span data-ttu-id="62863-226">*in_fClearDirty*</span><span class="sxs-lookup"><span data-stu-id="62863-226">*in_fClearDirty*</span></span>  
 <span data-ttu-id="62863-227">一个标志，该标志指示在此操作后是否应清除脏标志。</span><span class="sxs-lookup"><span data-stu-id="62863-227">A flag that indicates whether the dirty flag should be cleared after this operation.</span></span>  
  
#### <a name="return-values"></a><span data-ttu-id="62863-228">返回值 (s) </span><span class="sxs-lookup"><span data-stu-id="62863-228">Return Value(s)</span></span>  
 `S_OK`  
 <span data-ttu-id="62863-229">数据库已成功保存。</span><span class="sxs-lookup"><span data-stu-id="62863-229">The database was successfully saved.</span></span>  
  
 `STG_E_CANTSAVE`  
 <span data-ttu-id="62863-230">在保存数据库时出错，不同于 `STG_E_MEDIUMFULL`。</span><span class="sxs-lookup"><span data-stu-id="62863-230">An error occurred while saving the database, different than `STG_E_MEDIUMFULL`.</span></span>  
  
 `STG_E_MEDIUMFULL`  
 <span data-ttu-id="62863-231">因为在存储设备上没有剩余空间，所以该数据库无法保存。</span><span class="sxs-lookup"><span data-stu-id="62863-231">The database could not be saved because there is no space left on the storage device.</span></span>  
  
  
