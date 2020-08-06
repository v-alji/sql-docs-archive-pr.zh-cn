---
title: SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7f45181f3f6a791f5cb64a7519285b6d2a87dd36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692178"
---
# <a name="setvirtualdirectory-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="9737a-102">SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="9737a-102">SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="9737a-103">设置给定应用程序的虚拟目录的名称。</span><span class="sxs-lookup"><span data-stu-id="9737a-103">Sets the name of the virtual directory for a given application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9737a-104">语法</span><span class="sxs-lookup"><span data-stu-id="9737a-104">Syntax</span></span>  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9737a-105">parameters</span><span class="sxs-lookup"><span data-stu-id="9737a-105">Parameters</span></span>  
 <span data-ttu-id="9737a-106">*应用程序*</span><span class="sxs-lookup"><span data-stu-id="9737a-106">*Application*</span></span>  
 <span data-ttu-id="9737a-107">要为其设置虚拟目录的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="9737a-107">The name of application for which to set the virtual directory.</span></span>  
  
 <span data-ttu-id="9737a-108">*VirtualDirectory*</span><span class="sxs-lookup"><span data-stu-id="9737a-108">*VirtualDirectory*</span></span>  
 <span data-ttu-id="9737a-109">虚拟目录的名称。</span><span class="sxs-lookup"><span data-stu-id="9737a-109">The name of the virtual directory.</span></span>  
  
 <span data-ttu-id="9737a-110">*lcid*</span><span class="sxs-lookup"><span data-stu-id="9737a-110">*lcid*</span></span>  
 <span data-ttu-id="9737a-111">虚拟目录的区域设置 ID。</span><span class="sxs-lookup"><span data-stu-id="9737a-111">The locale id for the virtual directory.</span></span>  
  
 <span data-ttu-id="9737a-112">*错误*</span><span class="sxs-lookup"><span data-stu-id="9737a-112">*Error*</span></span>  
 <span data-ttu-id="9737a-113">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="9737a-113">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="9737a-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="9737a-114">*HRESULT*</span></span>  
 <span data-ttu-id="9737a-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="9737a-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9737a-116">返回值</span><span class="sxs-lookup"><span data-stu-id="9737a-116">Return Value</span></span>  
 <span data-ttu-id="9737a-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="9737a-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="9737a-118">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="9737a-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9737a-119">备注</span><span class="sxs-lookup"><span data-stu-id="9737a-119">Remarks</span></span>  
 <span data-ttu-id="9737a-120">一个应用程序只能有一个虚拟目录名用于所有的 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="9737a-120">An application can have only one virtual directory name for all URL reservations.</span></span>  
  
 <span data-ttu-id="9737a-121">VirtualDirectory 必须符合虚拟目录的命名约定。</span><span class="sxs-lookup"><span data-stu-id="9737a-121">VirtualDirectory must conform to naming conventions for virtual directories.</span></span> <span data-ttu-id="9737a-122">VirtualDirectory 必须不能为空字符串或者空白。</span><span class="sxs-lookup"><span data-stu-id="9737a-122">VirtualDirectory must not be empty string or blank.</span></span>  
  
 <span data-ttu-id="9737a-123">更新 \Configuration\URLReservations\Application\VirtualDirectory 元素的值。</span><span class="sxs-lookup"><span data-stu-id="9737a-123">Updates the value of the \Configuration\URLReservations\Application\VirtualDirectory element.</span></span> <span data-ttu-id="9737a-124">即使尚未创建 URL 预留，也能成功。</span><span class="sxs-lookup"><span data-stu-id="9737a-124">Succeeds even if no URL reservations have been created yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9737a-125">要求</span><span class="sxs-lookup"><span data-stu-id="9737a-125">Requirements</span></span>  
 <span data-ttu-id="9737a-126">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9737a-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9737a-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9737a-127">See Also</span></span>  
 [<span data-ttu-id="9737a-128">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="9737a-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
