---
title: 使用数字签名标识包的源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90c0e2e3db13ba4b228b70ccfffddbc2ff221774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694508"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a><span data-ttu-id="9fa9d-102">使用数字签名标识包的源</span><span class="sxs-lookup"><span data-stu-id="9fa9d-102">Identify the Source of Packages with Digital Signatures</span></span>
  <span data-ttu-id="9fa9d-103">可以使用数字证书对 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 进行签名以标识其来源。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be signed with a digital certificate to identify its source.</span></span> <span data-ttu-id="9fa9d-104">使用数字证书对包进行签名后，可以让 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 在加载包之前先检查数字签名。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-104">After a package has been signed with a digital certificate, you can have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the digital signature before loading the package.</span></span> <span data-ttu-id="9fa9d-105">若要让 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 能够检查签名，请在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 **dtexec** 实用工具 (dtexec.exe) 中设置一个选项，或设置一个可选的注册表值。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-105">To have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the signature, you set an option in either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in the **dtexec** utility (dtexec.exe), or set an optional registry value.</span></span>  
  
## <a name="signing-a-package-with-a-digital-certificate"></a><span data-ttu-id="9fa9d-106">使用数字证书对包进行签名</span><span class="sxs-lookup"><span data-stu-id="9fa9d-106">Signing a Package with a Digital Certificate</span></span>  
 <span data-ttu-id="9fa9d-107">必须首先获取或创建数字证书，才能使用该证书对包进行签名。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-107">Before you can sign a package with a digital certificate, you first have to obtain or create the certificate.</span></span> <span data-ttu-id="9fa9d-108">获取证书后，即可使用该证书对包进行签名。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-108">After you have the certificate, you can then use this certificate to sign the package.</span></span> <span data-ttu-id="9fa9d-109">有关如何获取证书以及如何使用该证书对包进行签名的详细信息，请参阅 [使用数字证书对包签名](../sign-a-package-by-using-a-digital-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-109">For more information about how to obtain a certificate and sign a package with that certificate, see [Sign a Package by Using a Digital Certificate](../sign-a-package-by-using-a-digital-certificate.md).</span></span>  
  
## <a name="setting-an-option-to-check-the-package-signature"></a><span data-ttu-id="9fa9d-110">设置选项以检查包的签名</span><span class="sxs-lookup"><span data-stu-id="9fa9d-110">Setting an Option to Check the Package Signature</span></span>  
 <span data-ttu-id="9fa9d-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 **dtexec** 实用工具都提供了用于将 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 配置为检查签名包的数字签名的选项。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-111">Both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and the **dtexec** utility have an option that configures [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of a signed package.</span></span> <span data-ttu-id="9fa9d-112">使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 还是 **dtexec** 实用工具取决于你是想检查所有包，还是只想检查特定的包：</span><span class="sxs-lookup"><span data-stu-id="9fa9d-112">Whether you use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or the **dtexec** utility depends on whether you want to check all packages or just specific ones:</span></span>  
  
-   <span data-ttu-id="9fa9d-113">若要在设计时加载包之前检查所有包的数字签名，请在 **中设置** “加载包时检查数字签名” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-113">To check the digital signature of all packages before loading the packages at design time, set the **Check digital signature when loading a package** option in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="9fa9d-114">此选项是针对 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中所有包的全局设置。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-114">This option is a global setting for all packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="9fa9d-115">有关详细信息，请参阅 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-115">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
-   <span data-ttu-id="9fa9d-116">若要检查个别包的数字签名，请在 `/VerifyS[igned]` 使用**dtexec**实用工具运行包时指定选项。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-116">To check the digital signature of an individual package, specify the `/VerifyS[igned]` option when you use the **dtexec** utility to run the package.</span></span> <span data-ttu-id="9fa9d-117">有关详细信息，请参阅 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-117">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a><span data-ttu-id="9fa9d-118">设置注册表值以检查包的签名</span><span class="sxs-lookup"><span data-stu-id="9fa9d-118">Setting a Registry Value to Check the Package Signature</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="9fa9d-119">还支持可选的注册表值**BlockedSignatureStates**，可以使用它来管理组织用于加载签名包和未签名包的策略。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-119">also supports an optional registry value, **BlockedSignatureStates**, that you can use to manage an organization's policy for loading signed and unsigned packages.</span></span> <span data-ttu-id="9fa9d-120">如果包未签名、签名无效或不可信，使用该注册表值将不允许加载该包。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-120">The registry value can prevent packages from loading if the packages are unsigned, or have invalid or untrusted signatures.</span></span> <span data-ttu-id="9fa9d-121">有关如何设置此注册表值的详细信息，请参阅 [通过设置注册表值实现签名策略](../implement-a-signing-policy-by-setting-a-registry-value.md)。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-121">For more information about how to set this registry value, see [Implement a Signing Policy by Setting a Registry Value](../implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9fa9d-122">可选的 **BlockedSignatureStates** 注册表值可指定比在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中或 **dtexec** 命令行中设置的数字签名选项限制性更强的设置。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-122">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or at the **dtexec** command line.</span></span> <span data-ttu-id="9fa9d-123">在这种情况下，限制性更强的注册表设置将覆盖其他设置。</span><span class="sxs-lookup"><span data-stu-id="9fa9d-123">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa9d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9fa9d-124">See Also</span></span>  
 <span data-ttu-id="9fa9d-125">[Integration Services &#40;SSIS&#41; 包](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="9fa9d-125">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="9fa9d-126">安全性概述 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="9fa9d-126">Security Overview &#40;Integration Services&#41;</span></span>](security-overview-integration-services.md)  
  
  
