---
title: SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b4a29b3379fc1d312af42a1f5b1296ee35dcf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692180"
---
# <a name="setservicestate-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="0627b-102">SetServiceState 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="0627b-102">SetServiceState Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="0627b-103">打开和关闭报表服务器 Windows 服务和 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="0627b-103">Turns the Report Server Windows and Web services on and off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0627b-104">语法</span><span class="sxs-lookup"><span data-stu-id="0627b-104">Syntax</span></span>  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0627b-105">parameters</span><span class="sxs-lookup"><span data-stu-id="0627b-105">Parameters</span></span>  
 <span data-ttu-id="0627b-106">*EnableWindowsService*</span><span class="sxs-lookup"><span data-stu-id="0627b-106">*EnableWindowsService*</span></span>  
 <span data-ttu-id="0627b-107">指示 Windows 服务状态的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0627b-107">A `Boolean` value indicating the state of the Windows service.</span></span> <span data-ttu-id="0627b-108">如果值为 `true`，则会启动报表服务器 Windows 服务；如果值为 `false`，则会停止该 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="0627b-108">A value of `true` starts the Report Server Windows service; a value of `false` stops the Windows service.</span></span>  
  
 <span data-ttu-id="0627b-109">*EnableWebService*</span><span class="sxs-lookup"><span data-stu-id="0627b-109">*EnableWebService*</span></span>  
 <span data-ttu-id="0627b-110">`Boolean`指示 Web 服务状态的值 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0627b-110">A `Boolean` value indicating the state of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web service.</span></span> <span data-ttu-id="0627b-111">如果值为 `true`，则会启动报表服务器 Web 服务；如果值为 `false`，则会停止该 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="0627b-111">A value of `true` starts the Report Server Web service; a value of `false` stops the Web service</span></span>  
  
 <span data-ttu-id="0627b-112">*EnableReportManager*</span><span class="sxs-lookup"><span data-stu-id="0627b-112">*EnableReportManager*</span></span>  
 <span data-ttu-id="0627b-113">指示所需的报表管理器状态的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0627b-113">A `Boolean` value indicating the desired state of the Report manager.</span></span>  
  
 <span data-ttu-id="0627b-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="0627b-114">*HRESULT*</span></span>  
 <span data-ttu-id="0627b-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="0627b-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0627b-116">返回值</span><span class="sxs-lookup"><span data-stu-id="0627b-116">Return Value</span></span>  
 <span data-ttu-id="0627b-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="0627b-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="0627b-118">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="0627b-118">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="0627b-119">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="0627b-119">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0627b-120">备注</span><span class="sxs-lookup"><span data-stu-id="0627b-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0627b-121">要求</span><span class="sxs-lookup"><span data-stu-id="0627b-121">Requirements</span></span>  
 <span data-ttu-id="0627b-122">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0627b-122">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0627b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0627b-123">See Also</span></span>  
 [<span data-ttu-id="0627b-124">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="0627b-124">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
