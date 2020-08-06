---
title: RemoveSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d42d17d9c92f2e100a7800e607536ff6c7eab891
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691541"
---
# <a name="removesslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="84ef6-102">RemoveSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="84ef6-102">RemoveSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="84ef6-103">删除 SSL 证书绑定。</span><span class="sxs-lookup"><span data-stu-id="84ef6-103">Removes an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ef6-104">语法</span><span class="sxs-lookup"><span data-stu-id="84ef6-104">Syntax</span></span>  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84ef6-105">参数</span><span class="sxs-lookup"><span data-stu-id="84ef6-105">Parameters</span></span>  
 <span data-ttu-id="84ef6-106">*应用程序*</span><span class="sxs-lookup"><span data-stu-id="84ef6-106">*Application*</span></span>  
 <span data-ttu-id="84ef6-107">应为其删除证书绑定的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="84ef6-107">The name of application for which the certificate binding should be removed.</span></span>  
  
 <span data-ttu-id="84ef6-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="84ef6-108">*CertificateHash*</span></span>  
 <span data-ttu-id="84ef6-109">证书的哈希。</span><span class="sxs-lookup"><span data-stu-id="84ef6-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="84ef6-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="84ef6-110">*IPAddress*</span></span>  
 <span data-ttu-id="84ef6-111">应用程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="84ef6-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="84ef6-112">端口 </span><span class="sxs-lookup"><span data-stu-id="84ef6-112">*Port*</span></span>  
 <span data-ttu-id="84ef6-113">与该绑定关联的 SSL 端口。</span><span class="sxs-lookup"><span data-stu-id="84ef6-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="84ef6-114">*lcid*</span><span class="sxs-lookup"><span data-stu-id="84ef6-114">*lcid*</span></span>  
 <span data-ttu-id="84ef6-115">用于返回的错误消息的区域设置。</span><span class="sxs-lookup"><span data-stu-id="84ef6-115">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="84ef6-116">*错误*</span><span class="sxs-lookup"><span data-stu-id="84ef6-116">*Error*</span></span>  
 <span data-ttu-id="84ef6-117">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="84ef6-117">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="84ef6-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="84ef6-118">*HRESULT*</span></span>  
 <span data-ttu-id="84ef6-119">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="84ef6-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84ef6-120">返回值</span><span class="sxs-lookup"><span data-stu-id="84ef6-120">Return Value</span></span>  
 <span data-ttu-id="84ef6-121">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="84ef6-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="84ef6-122">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="84ef6-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84ef6-123">备注</span><span class="sxs-lookup"><span data-stu-id="84ef6-123">Remarks</span></span>  
 <span data-ttu-id="84ef6-124">此方法可以从 rsreportserver.config 文件中删除特定的绑定，也可以选择从 HTTP.SYS 中删除特定的绑定。</span><span class="sxs-lookup"><span data-stu-id="84ef6-124">This method removes the specific binding from the rsreportserver.config file and optionally HTTP.SYS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ef6-125">要求</span><span class="sxs-lookup"><span data-stu-id="84ef6-125">Requirements</span></span>  
 <span data-ttu-id="84ef6-126">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ef6-126">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ef6-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84ef6-127">See Also</span></span>  
 [<span data-ttu-id="84ef6-128">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="84ef6-128">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
