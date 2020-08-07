---
title: RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a32989e8ce8986b785e829d8cc7fcf58fbbf240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587708"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="05cf6-102">RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="05cf6-102">RemoveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="05cf6-103">删除为报表服务器保留的 URL。</span><span class="sxs-lookup"><span data-stu-id="05cf6-103">Removes a URL reserved for the report server.</span></span> <span data-ttu-id="05cf6-104">如果需要删除多个 URL，则必须逐个调用此 API 来完成操作。</span><span class="sxs-lookup"><span data-stu-id="05cf6-104">If there are multiple URLs that need to be removed, this must be done one by one calling this API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05cf6-105">语法</span><span class="sxs-lookup"><span data-stu-id="05cf6-105">Syntax</span></span>  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05cf6-106">参数</span><span class="sxs-lookup"><span data-stu-id="05cf6-106">Parameters</span></span>  
 <span data-ttu-id="05cf6-107">*应用程序*</span><span class="sxs-lookup"><span data-stu-id="05cf6-107">*Application*</span></span>  
 <span data-ttu-id="05cf6-108">要为其删除预留的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="05cf6-108">The name of application for which to remove the reservation.</span></span>  
  
 <span data-ttu-id="05cf6-109">*URLString*</span><span class="sxs-lookup"><span data-stu-id="05cf6-109">*URLString*</span></span>  
 <span data-ttu-id="05cf6-110">预留的 URL。</span><span class="sxs-lookup"><span data-stu-id="05cf6-110">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="05cf6-111">*lcid*</span><span class="sxs-lookup"><span data-stu-id="05cf6-111">*lcid*</span></span>  
 <span data-ttu-id="05cf6-112">用于返回的错误消息的区域设置。</span><span class="sxs-lookup"><span data-stu-id="05cf6-112">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="05cf6-113">*错误*</span><span class="sxs-lookup"><span data-stu-id="05cf6-113">*Error*</span></span>  
 <span data-ttu-id="05cf6-114">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="05cf6-114">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="05cf6-115">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="05cf6-115">*HRESULT*</span></span>  
 <span data-ttu-id="05cf6-116">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="05cf6-116">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05cf6-117">返回值</span><span class="sxs-lookup"><span data-stu-id="05cf6-117">Return Value</span></span>  
 <span data-ttu-id="05cf6-118">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="05cf6-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="05cf6-119">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="05cf6-119">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05cf6-120">备注</span><span class="sxs-lookup"><span data-stu-id="05cf6-120">Remarks</span></span>  
 <span data-ttu-id="05cf6-121">UrlString 不包括虚拟目录名 - [SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) 是为实现该目的所提供的方法  。</span><span class="sxs-lookup"><span data-stu-id="05cf6-121">*UrlString* does not include the Virtual Directory name - the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="05cf6-122">在调用 [ReserveURL](configurationsetting-method-reserveurl.md) 方法之前，必须为 *Application* 参数的 VirtualDirectory 配置属性提供一个值。</span><span class="sxs-lookup"><span data-stu-id="05cf6-122">Before calling the [ReserveURL](configurationsetting-method-reserveurl.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter.</span></span> <span data-ttu-id="05cf6-123">使用 [SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting )](configurationsetting-method-setvirtualdirectory.md) 方法设置 VirtualDirectory 属性。</span><span class="sxs-lookup"><span data-stu-id="05cf6-123">Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method to set the VirtualDirectory property.</span></span>  
  
 <span data-ttu-id="05cf6-124">如果 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供了 SSL 证书，但是没有其他 URL 需要它，则将删除它。</span><span class="sxs-lookup"><span data-stu-id="05cf6-124">If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and no other URLs need it, it is removed.</span></span>  
  
 <span data-ttu-id="05cf6-125">此方法会导致所有非配置应用程序域在执行此操作时进行硬回收并停止；应用程序域将在此操作完成后重新启动。</span><span class="sxs-lookup"><span data-stu-id="05cf6-125">This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05cf6-126">要求</span><span class="sxs-lookup"><span data-stu-id="05cf6-126">Requirements</span></span>  
 <span data-ttu-id="05cf6-127">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05cf6-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05cf6-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05cf6-128">See Also</span></span>  
 [<span data-ttu-id="05cf6-129">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="05cf6-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
