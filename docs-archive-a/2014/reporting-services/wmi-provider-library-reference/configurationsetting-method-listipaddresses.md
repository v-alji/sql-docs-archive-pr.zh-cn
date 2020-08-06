---
title: ListIPAddresses 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 845f7ba7db02a0b860f966184463580733af0faf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581104"
---
# <a name="listipaddresses-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="75493-102">ListIPAddresses 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="75493-102">ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="75493-103">列出报表服务器计算机的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="75493-103">Lists the IP addresses for the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75493-104">语法</span><span class="sxs-lookup"><span data-stu-id="75493-104">Syntax</span></span>  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75493-105">参数</span><span class="sxs-lookup"><span data-stu-id="75493-105">Parameters</span></span>  
 <span data-ttu-id="75493-106">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="75493-106">*IPAddress[]*</span></span>  
 <span data-ttu-id="75493-107">[out] 计算机的 IP 地址列表。</span><span class="sxs-lookup"><span data-stu-id="75493-107">[out] The list of IP address for the computer.</span></span>  
  
 <span data-ttu-id="75493-108">*IPVersion[]*</span><span class="sxs-lookup"><span data-stu-id="75493-108">*IPVersion[]*</span></span>  
 <span data-ttu-id="75493-109">[out] IP 地址的版本。</span><span class="sxs-lookup"><span data-stu-id="75493-109">[out] The version for the IP addresses.</span></span>  
  
 <span data-ttu-id="75493-110">*IsDhcpEnabled[]*</span><span class="sxs-lookup"><span data-stu-id="75493-110">*IsDhcpEnabled[]*</span></span>  
 <span data-ttu-id="75493-111">[out] 指示 IP 地址是否已启用 DHCP。</span><span class="sxs-lookup"><span data-stu-id="75493-111">[out] Indicates whether the IP addresses are DHCP enabled.</span></span>  
  
 <span data-ttu-id="75493-112">*长度*</span><span class="sxs-lookup"><span data-stu-id="75493-112">*Length*</span></span>  
 <span data-ttu-id="75493-113">[out] 该方法返回的数组长度。</span><span class="sxs-lookup"><span data-stu-id="75493-113">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="75493-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="75493-114">*HRESULT*</span></span>  
 <span data-ttu-id="75493-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="75493-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75493-116">返回值</span><span class="sxs-lookup"><span data-stu-id="75493-116">Return Value</span></span>  
 <span data-ttu-id="75493-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="75493-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="75493-118">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="75493-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75493-119">备注</span><span class="sxs-lookup"><span data-stu-id="75493-119">Remarks</span></span>  
 <span data-ttu-id="75493-120">*IPVersion* 字符串为 V4、V6。</span><span class="sxs-lookup"><span data-stu-id="75493-120">*IPVersion* strings are V4, V6.</span></span>  
  
 <span data-ttu-id="75493-121">如果*IsDhcpEnabled*为 `True` ，则*IPAddress*为 dynamic。</span><span class="sxs-lookup"><span data-stu-id="75493-121">If *IsDhcpEnabled* is `True`, the *IPAddress* is dynamic.</span></span> <span data-ttu-id="75493-122">不应用于 SSL 绑定。</span><span class="sxs-lookup"><span data-stu-id="75493-122">It should not be used for SSL bindings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75493-123">要求</span><span class="sxs-lookup"><span data-stu-id="75493-123">Requirements</span></span>  
 <span data-ttu-id="75493-124">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75493-124">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75493-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75493-125">See Also</span></span>  
 [<span data-ttu-id="75493-126">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="75493-126">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
