---
title: ListSSLCertificates 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6a5ced8371817adc44bbbc89400dc83e0dfccef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581092"
---
# <a name="listsslcertificates-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="c1246-102">ListSSLCertificates 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="c1246-102">ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="c1246-103">返回报表服务器计算机上证书的列表。</span><span class="sxs-lookup"><span data-stu-id="c1246-103">Returns a list of certificates on the report server computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1246-104">语法</span><span class="sxs-lookup"><span data-stu-id="c1246-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1246-105">parameters</span><span class="sxs-lookup"><span data-stu-id="c1246-105">Parameters</span></span>  
 <span data-ttu-id="c1246-106">*CertificateHash[]*</span><span class="sxs-lookup"><span data-stu-id="c1246-106">*CertificateHash[]*</span></span>  
 <span data-ttu-id="c1246-107">[out] 证书哈希。</span><span class="sxs-lookup"><span data-stu-id="c1246-107">[out] The certificate hashes.</span></span>  
  
 <span data-ttu-id="c1246-108">*CertName[]*</span><span class="sxs-lookup"><span data-stu-id="c1246-108">*CertName[]*</span></span>  
 <span data-ttu-id="c1246-109">[out] 证书名称。</span><span class="sxs-lookup"><span data-stu-id="c1246-109">[out] Names of the certificate.</span></span>  
  
 <span data-ttu-id="c1246-110">*HostName[]*</span><span class="sxs-lookup"><span data-stu-id="c1246-110">*HostName[]*</span></span>  
 <span data-ttu-id="c1246-111">[out] 证书的主机名。</span><span class="sxs-lookup"><span data-stu-id="c1246-111">[out] The host names for the certificates.</span></span>  
  
 <span data-ttu-id="c1246-112">*长度*</span><span class="sxs-lookup"><span data-stu-id="c1246-112">*Length*</span></span>  
 <span data-ttu-id="c1246-113">[out] 表示 *CertificateHash*、 *CertName* 和 *HostName* 数组的长度。</span><span class="sxs-lookup"><span data-stu-id="c1246-113">[out] Represents the length of the *CertificateHash*, *CertName* and *HostName* arrays.</span></span>  
  
 <span data-ttu-id="c1246-114">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="c1246-114">*HRESULT*</span></span>  
 <span data-ttu-id="c1246-115">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="c1246-115">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1246-116">返回值</span><span class="sxs-lookup"><span data-stu-id="c1246-116">Return Value</span></span>  
 <span data-ttu-id="c1246-117">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="c1246-117">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="c1246-118">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="c1246-118">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1246-119">备注</span><span class="sxs-lookup"><span data-stu-id="c1246-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1246-120">要求</span><span class="sxs-lookup"><span data-stu-id="c1246-120">Requirements</span></span>  
 <span data-ttu-id="c1246-121">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1246-121">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1246-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1246-122">See Also</span></span>  
 [<span data-ttu-id="c1246-123">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="c1246-123">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
