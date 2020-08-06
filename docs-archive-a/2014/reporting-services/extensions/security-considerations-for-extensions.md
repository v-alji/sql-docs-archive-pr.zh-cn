---
title: 扩展插件的安全注意事项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- extensions [Reporting Services], security
- permissions [Reporting Services], extensions
ms.assetid: 58cbdfeb-1105-4a7d-a3b8-b897ff95f367
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e7819f4d6de2003c9982d33ab00cfa0d4030aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591134"
---
# <a name="security-considerations-for-extensions"></a><span data-ttu-id="fe222-102">扩展插件的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="fe222-102">Security Considerations for Extensions</span></span>
  <span data-ttu-id="fe222-103">每种以公共语言运行时 (CLR) 为目标的应用程序都必须与 CLR 的安全系统进行交互。</span><span class="sxs-lookup"><span data-stu-id="fe222-103">Every application that targets the common language runtime (CLR) must interact with the CLR security system.</span></span> <span data-ttu-id="fe222-104">当此类应用程序运行时，CLR 将自动对它进行计算，然后向它提供一组权限。</span><span class="sxs-lookup"><span data-stu-id="fe222-104">When such an application runs, it is automatically evaluated and given a set of permissions by the CLR.</span></span> <span data-ttu-id="fe222-105">应用程序可能会继续运行，或者生成安全性异常，具体取决于应用程序所收到的权限。</span><span class="sxs-lookup"><span data-stu-id="fe222-105">Depending on the permissions that the application receives, it either continues running or generates a security exception.</span></span> <span data-ttu-id="fe222-106">针对特定报表服务器的安全策略配置文件中的本地安全设置和策略定义程序集接收的代码权限。</span><span class="sxs-lookup"><span data-stu-id="fe222-106">The local security settings and policies in the security policy configuration files for a particular report server define the code permissions that an assembly receives.</span></span>  
  
 <span data-ttu-id="fe222-107">在请求权限前，您需要知道扩展插件代码计划使用的资源和保护的操作，并且还需要知道哪些权限保护这些资源和操作。</span><span class="sxs-lookup"><span data-stu-id="fe222-107">Before requesting permissions, you need to be aware of the resources and protected operations your extension code is planning to use, and you also need to know which permissions protect those resources and operations.</span></span> <span data-ttu-id="fe222-108">此外，还需要跟踪扩展插件组件调用的所有类库方法访问的所有资源。</span><span class="sxs-lookup"><span data-stu-id="fe222-108">In addition, you need to keep track of any resources accessed by any class library methods that are called by the extension components.</span></span> <span data-ttu-id="fe222-109">有关详细信息，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 开发人员指南中的“请求权限”。</span><span class="sxs-lookup"><span data-stu-id="fe222-109">For more information, see "Requesting Permissions" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
 <span data-ttu-id="fe222-110">部署到报表服务器的扩展插件必须以完全信任方式运行，这意味着扩展插件需要是授予 FullTrust 权限集的代码组的一部分  。</span><span class="sxs-lookup"><span data-stu-id="fe222-110">Extensions deployed to a report server must run as fully trusted, meaning that your extension needs to be part of a code group that is granted the **FullTrust** permission set.</span></span> <span data-ttu-id="fe222-111">这还意味着根据为特定报表对其验证身份的用户，您的扩展插件可能还要具有对通过 CLR 提供的某些服务器资源和操作的访问权限。</span><span class="sxs-lookup"><span data-stu-id="fe222-111">This also means that your extension may have access to certain server resources and operations available through the CLR depending on the user that is being authenticated for a particular report.</span></span> <span data-ttu-id="fe222-112">有关详细信息，请参阅 [Reporting Services 中的代码访问安全性](secure-development/code-access-security-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe222-112">For more information about code groups and extensions, see [Code Access Security in Reporting Services](secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fe222-113">为其所有扩展插件强制 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 安全性。</span><span class="sxs-lookup"><span data-stu-id="fe222-113">enforces [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security for all of its extensions.</span></span>  
  
 <span data-ttu-id="fe222-114">以下条件适用于在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中部署数据处理、传递、呈现和安全扩展插件。</span><span class="sxs-lookup"><span data-stu-id="fe222-114">The following conditions apply to the deployment of data processing, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="fe222-115">只有本地管理员才具有部署某一扩展插件的权限。</span><span class="sxs-lookup"><span data-stu-id="fe222-115">Only the local administrator has permission to deploy an extension.</span></span>  
  
-   <span data-ttu-id="fe222-116">只有具有适当读取/写入权限的用户才能更改要扩展的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件的配置文件。</span><span class="sxs-lookup"><span data-stu-id="fe222-116">Only users with the appropriate read/write permissions can change the configuration files for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component that is being extended.</span></span>  
  
-   <span data-ttu-id="fe222-117">只有特权用户才有权编辑扩展插件的安全策略文件和为其启用代码访问安全性。</span><span class="sxs-lookup"><span data-stu-id="fe222-117">Only privileged users have permission to edit the security policy files and enable code access security for an extension.</span></span>  
  
 <span data-ttu-id="fe222-118">有关 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的代码访问安全性的详细信息，请参阅[安全开发 (Reporting Services)](secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe222-118">For more information about code access security in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md).</span></span>  
  
 <span data-ttu-id="fe222-119">有关 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 安全性的详细信息，请参阅 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 开发人员指南中的“.NET Framework 安全性”。</span><span class="sxs-lookup"><span data-stu-id="fe222-119">For more information about [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security, see ".NET Framework Security" in your [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
## <a name="initialization-of-extension-assemblies"></a><span data-ttu-id="fe222-120">扩展插件程序集的初始化</span><span class="sxs-lookup"><span data-stu-id="fe222-120">Initialization of Extension Assemblies</span></span>  
 <span data-ttu-id="fe222-121">在扩展插件由报表服务器首次加载到内存中时，它们使用服务帐户凭据，因为某些扩展插件程序集要求特定的权限来访问系统资源、读取配置文件和加载其他相关的程序集。</span><span class="sxs-lookup"><span data-stu-id="fe222-121">When extensions are first loaded into memory by the report server, they use the service account credentials, because some extension assemblies require specific permissions to access system resources, to read configuration files, and to load other, dependent assemblies.</span></span> <span data-ttu-id="fe222-122">但在已加载和初始化程序集后，对扩展插件程序集的所有后续调用都将使用当前登录的用户帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="fe222-122">After an assembly has been loaded and initialized, however, all subsequent calls to extension assemblies use the credentials of the user account that is currently logged on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe222-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe222-123">See Also</span></span>  
 <span data-ttu-id="fe222-124">[Reporting Services 扩展插件](reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fe222-124">[Reporting Services Extensions](reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="fe222-125">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="fe222-125">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
  
  
