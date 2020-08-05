---
title: CreateSSLCertificateBinding 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b9a5f9394d655f7b0592ea688a46f3ac2b9c153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581123"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d2647-102">CreateSSLCertificateBinding 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d2647-102">CreateSSLCertificateBinding Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d2647-103">创建 SSL 证书绑定。</span><span class="sxs-lookup"><span data-stu-id="d2647-103">Creates an SSL Certificate binding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2647-104">语法</span><span class="sxs-lookup"><span data-stu-id="d2647-104">Syntax</span></span>  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2647-105">参数</span><span class="sxs-lookup"><span data-stu-id="d2647-105">Parameters</span></span>  
 <span data-ttu-id="d2647-106">*应用程序*</span><span class="sxs-lookup"><span data-stu-id="d2647-106">*Application*</span></span>  
 <span data-ttu-id="d2647-107">应为其创建证书绑定的应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="d2647-107">The name of application that the certificate binding should be created for.</span></span>  
  
 <span data-ttu-id="d2647-108">*CertificateHash*</span><span class="sxs-lookup"><span data-stu-id="d2647-108">*CertificateHash*</span></span>  
 <span data-ttu-id="d2647-109">证书的哈希。</span><span class="sxs-lookup"><span data-stu-id="d2647-109">The hash for the certificate.</span></span>  
  
 <span data-ttu-id="d2647-110">*IPAddress*</span><span class="sxs-lookup"><span data-stu-id="d2647-110">*IPAddress*</span></span>  
 <span data-ttu-id="d2647-111">应用程序的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d2647-111">The IP address for the application.</span></span>  
  
 <span data-ttu-id="d2647-112">端口 </span><span class="sxs-lookup"><span data-stu-id="d2647-112">*Port*</span></span>  
 <span data-ttu-id="d2647-113">与该绑定关联的 SSL 端口。</span><span class="sxs-lookup"><span data-stu-id="d2647-113">The SSL port associated with the binding.</span></span>  
  
 <span data-ttu-id="d2647-114">*Lcid*</span><span class="sxs-lookup"><span data-stu-id="d2647-114">*Lcid*</span></span>  
 <span data-ttu-id="d2647-115">用于返回的错误消息的区域设置。</span><span class="sxs-lookup"><span data-stu-id="d2647-115">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="d2647-116">*错误*</span><span class="sxs-lookup"><span data-stu-id="d2647-116">*Error*</span></span>  
 <span data-ttu-id="d2647-117">[out] 发生的错误的说明。</span><span class="sxs-lookup"><span data-stu-id="d2647-117">[out] The description of the errors that occurred.</span></span>  
  
 <span data-ttu-id="d2647-118">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="d2647-118">*HRESULT*</span></span>  
 <span data-ttu-id="d2647-119">[out] 指示调用是成功还是失败的值。</span><span class="sxs-lookup"><span data-stu-id="d2647-119">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2647-120">返回值</span><span class="sxs-lookup"><span data-stu-id="d2647-120">Return Value</span></span>  
 <span data-ttu-id="d2647-121">返回 *HRESULT* ，指示方法调用是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="d2647-121">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="d2647-122">值 0 指示方法调用已成功；错误代码指示调用未成功。</span><span class="sxs-lookup"><span data-stu-id="d2647-122">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2647-123">备注</span><span class="sxs-lookup"><span data-stu-id="d2647-123">Remarks</span></span>  
 <span data-ttu-id="d2647-124">此方法将向 rsreportserver.config 中为该应用程序添加一个绑定。</span><span class="sxs-lookup"><span data-stu-id="d2647-124">This method adds a binding to rsreportserver.config for the application.</span></span> <span data-ttu-id="d2647-125">如果某个绑定在 HTTP.SYS 中不存在，则会在其中创建它。</span><span class="sxs-lookup"><span data-stu-id="d2647-125">If a binding does not already exist in HTTP.SYS, it is created there.</span></span>  
  
 <span data-ttu-id="d2647-126">在创建绑定之前，该方法调用会检查指定应用程序的 Url 预留，以确定 SSL 证书绑定是否有效。</span><span class="sxs-lookup"><span data-stu-id="d2647-126">Before creating the binding, the method call examines the Url Reservations for the specified application to determine if the SSL Certificate Binding is valid.</span></span>  
  
 <span data-ttu-id="d2647-127">如果验证到存在以下情况，则会导致错误：</span><span class="sxs-lookup"><span data-stu-id="d2647-127">The following conditions are validated and can result in errors:</span></span>  
  
1.  <span data-ttu-id="d2647-128">证书不存在。</span><span class="sxs-lookup"><span data-stu-id="d2647-128">Certificate does not exist.</span></span>  
  
2.  <span data-ttu-id="d2647-129">指定的 IPAddress 与此计算机的 IPAddress 不对应。</span><span class="sxs-lookup"><span data-stu-id="d2647-129">The IPAddress specified does not correspond to an IPAddress of this computer.</span></span>  
  
3.  <span data-ttu-id="d2647-130">指定的 IPAddress 为 DHCP IPAddress（定期更改）- 请改用通配符 IP 地址 (0.0.0.0)。</span><span class="sxs-lookup"><span data-stu-id="d2647-130">The IPAddress specified is a DHCP IPAddress (changes periodically) - use the Wildcard IP address instead (0.0.0.0).</span></span>  
  
4.  <span data-ttu-id="d2647-131">指定的 IPAddress 与某个 URL 预留的 IP 地址不匹配，并且没有通配符或主机名 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="d2647-131">IPAddress specified does not match the IP address of a URL reservations AND neither a wildcard or host name URL reservation exist.</span></span>  
  
5.  <span data-ttu-id="d2647-132">指定某个主机名的 URL 预留已存在，但是该主机名与证书主机名不匹配。</span><span class="sxs-lookup"><span data-stu-id="d2647-132">A URL reservation that specifies a host name exists, but the host name does not match the certificate host name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2647-133">要求</span><span class="sxs-lookup"><span data-stu-id="d2647-133">Requirements</span></span>  
 <span data-ttu-id="d2647-134">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2647-134">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2647-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2647-135">See Also</span></span>  
 [<span data-ttu-id="d2647-136">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="d2647-136">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
