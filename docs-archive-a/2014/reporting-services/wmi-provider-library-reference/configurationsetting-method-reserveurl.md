---
title: ReserveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95a58938ada19b4e49f094e3d8d01b241f1a4286
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692195"
---
# <a name="reserveurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="acaeb-102">ReserveURL 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="acaeb-102">ReserveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="acaeb-103">为给定的应用程序添加一个 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="acaeb-103">Adds a URL reservation for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acaeb-104">语法</span><span class="sxs-lookup"><span data-stu-id="acaeb-104">Syntax</span></span>  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acaeb-105">parameters</span><span class="sxs-lookup"><span data-stu-id="acaeb-105">Parameters</span></span>  
 <span data-ttu-id="acaeb-106">*应用程序*</span><span class="sxs-lookup"><span data-stu-id="acaeb-106">*Application*</span></span>  
 <span data-ttu-id="acaeb-107">为其保留相应 URL 的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="acaeb-107">The name of application to reserve the URL for.</span></span>  
  
 <span data-ttu-id="acaeb-108">*URLString*</span><span class="sxs-lookup"><span data-stu-id="acaeb-108">*URLString*</span></span>  
 <span data-ttu-id="acaeb-109">预留的 URL。</span><span class="sxs-lookup"><span data-stu-id="acaeb-109">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="acaeb-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="acaeb-110">*lcid*</span></span>  
 <span data-ttu-id="acaeb-111">用于返回的错误消息的区域设置。</span><span class="sxs-lookup"><span data-stu-id="acaeb-111">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="acaeb-112">*错误*</span><span class="sxs-lookup"><span data-stu-id="acaeb-112">*Error*</span></span>  
 <span data-ttu-id="acaeb-113">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="acaeb-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="acaeb-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="acaeb-114">*HRESULT*</span></span>  
 <span data-ttu-id="acaeb-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="acaeb-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acaeb-116">返回值</span><span class="sxs-lookup"><span data-stu-id="acaeb-116">Return Value</span></span>  
 <span data-ttu-id="acaeb-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="acaeb-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="acaeb-118">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="acaeb-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acaeb-119">备注</span><span class="sxs-lookup"><span data-stu-id="acaeb-119">Remarks</span></span>  
 <span data-ttu-id="acaeb-120">*UrlString* 不包括虚拟路径名称。</span><span class="sxs-lookup"><span data-stu-id="acaeb-120">*UrlString* does not include the virtual directory name.</span></span> <span data-ttu-id="acaeb-121">可以使用 [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) 方法实现该目的。</span><span class="sxs-lookup"><span data-stu-id="acaeb-121">The [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="acaeb-122">针对当前 Windows 服务帐户创建 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="acaeb-122">URL reservations are created for the current windows service account.</span></span> <span data-ttu-id="acaeb-123">更改 Windows 服务帐户需要手动更新所有的 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="acaeb-123">Changing the windows service account requires updating all the URL reservations manually.</span></span>  
  
 <span data-ttu-id="acaeb-124">此方法将导致所有应用程序域进行硬回收。</span><span class="sxs-lookup"><span data-stu-id="acaeb-124">This method causes all application domains to hard recycle.</span></span> <span data-ttu-id="acaeb-125">此操作完成后，应用程序域将重新启动。</span><span class="sxs-lookup"><span data-stu-id="acaeb-125">Application domains are restarted after this operation is complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acaeb-126">要求</span><span class="sxs-lookup"><span data-stu-id="acaeb-126">Requirements</span></span>  
 <span data-ttu-id="acaeb-127">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acaeb-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acaeb-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="acaeb-128">See Also</span></span>  
 [<span data-ttu-id="acaeb-129">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="acaeb-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
