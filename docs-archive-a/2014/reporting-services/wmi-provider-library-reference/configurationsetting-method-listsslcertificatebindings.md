---
title: ListSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56b19a138dc95b94a20183909dd444c90b158b26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581095"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="90688-102">ListSSLCertificateBindings 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="90688-102">ListSSLCertificateBindings Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="90688-103">返回计算机上已安装的 SSL 证书的列表。</span><span class="sxs-lookup"><span data-stu-id="90688-103">Returns a list of installed SSL certificates on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90688-104">语法</span><span class="sxs-lookup"><span data-stu-id="90688-104">Syntax</span></span>  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90688-105">参数</span><span class="sxs-lookup"><span data-stu-id="90688-105">Parameters</span></span>  
 <span data-ttu-id="90688-106">*LCID*</span><span class="sxs-lookup"><span data-stu-id="90688-106">*LCID*</span></span>  
 <span data-ttu-id="90688-107">用于返回的错误消息的区域设置。</span><span class="sxs-lookup"><span data-stu-id="90688-107">The locale to use for the error messages that are returned.</span></span>  
  
 <span data-ttu-id="90688-108">*Application[]*</span><span class="sxs-lookup"><span data-stu-id="90688-108">*Application[]*</span></span>  
 <span data-ttu-id="90688-109">[out] 具有证书绑定的应用程序。</span><span class="sxs-lookup"><span data-stu-id="90688-109">[out] The applications that have certificate bindings.</span></span>  
  
 <span data-ttu-id="90688-110">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="90688-110">*CertificateHash[]*</span></span>  
 <span data-ttu-id="90688-111">[out] 证书的哈希。</span><span class="sxs-lookup"><span data-stu-id="90688-111">[out] The hashes for the certificates.</span></span>  
  
 <span data-ttu-id="90688-112">*IPAddress[]*</span><span class="sxs-lookup"><span data-stu-id="90688-112">*IPAddress[]*</span></span>  
 <span data-ttu-id="90688-113">[out] 应用程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="90688-113">[out] The IP address for the applications.</span></span>  
  
 <span data-ttu-id="90688-114">*Port[]*</span><span class="sxs-lookup"><span data-stu-id="90688-114">*Port[]*</span></span>  
 <span data-ttu-id="90688-115">[out] 存储在 rsreportserver.config 中的绑定中的端口号。</span><span class="sxs-lookup"><span data-stu-id="90688-115">[out] The port number stored in the binding in rsreportserver.config.</span></span>  
  
 <span data-ttu-id="90688-116">*Errors[]*</span><span class="sxs-lookup"><span data-stu-id="90688-116">*Errors[]*</span></span>  
 <span data-ttu-id="90688-117">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="90688-117">[out] The descriptions for errors that occurred.</span></span>  
  
 <span data-ttu-id="90688-118">*长度*</span><span class="sxs-lookup"><span data-stu-id="90688-118">*Length*</span></span>  
 <span data-ttu-id="90688-119">[out] 该方法返回的数组长度。</span><span class="sxs-lookup"><span data-stu-id="90688-119">[out] The length of the array returned by the method.</span></span>  
  
 <span data-ttu-id="90688-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="90688-120">*HRESULT*</span></span>  
 <span data-ttu-id="90688-121">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="90688-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90688-122">返回值</span><span class="sxs-lookup"><span data-stu-id="90688-122">Return Value</span></span>  
 <span data-ttu-id="90688-123">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="90688-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="90688-124">值 0 指示方法调用已成功。</span><span class="sxs-lookup"><span data-stu-id="90688-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="90688-125">非零值指示已发生错误。</span><span class="sxs-lookup"><span data-stu-id="90688-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90688-126">备注</span><span class="sxs-lookup"><span data-stu-id="90688-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90688-127">要求</span><span class="sxs-lookup"><span data-stu-id="90688-127">Requirements</span></span>  
 <span data-ttu-id="90688-128">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90688-128">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90688-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90688-129">See Also</span></span>  
 [<span data-ttu-id="90688-130">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="90688-130">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
