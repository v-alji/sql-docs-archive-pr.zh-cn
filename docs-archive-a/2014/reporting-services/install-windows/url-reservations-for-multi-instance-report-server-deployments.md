---
title: 多实例报表服务器部署的 URL 保留项 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2e51813ca2c85d089864dc5d2516e21ed975de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577380"
---
# <a name="url-reservations-for-multi-instance-report-server-deployments--ssrs-configuration-manager"></a><span data-ttu-id="f087a-102">多实例报表服务器部署的 URL 预留（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="f087a-102">URL Reservations for Multi-Instance Report Server Deployments  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="f087a-103">如果将多个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例安装在同一台计算机上，则必须考虑如何为每个实例定义 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="f087a-103">If you install multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer, you must consider how you will define the URL reservations for each instance.</span></span> <span data-ttu-id="f087a-104">在每个实例中，报表服务器 Web 服务和报表管理器都必须至少有一个 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="f087a-104">Within each instance, the Report Server Web service and Report Manager must have at least one URL reservation each.</span></span> <span data-ttu-id="f087a-105">整组预留在 HTTP.SYS 中必须保持唯一。</span><span class="sxs-lookup"><span data-stu-id="f087a-105">The entire set of reservations must be unique in HTTP.SYS.</span></span>  
  
 <span data-ttu-id="f087a-106">在 URL 注册（发生在服务启动时）过程中会检测 URL 是否重复。</span><span class="sxs-lookup"><span data-stu-id="f087a-106">Duplicate URLs are detected during URL registration, which occurs when the service starts.</span></span> <span data-ttu-id="f087a-107">如果你创建的 URL 预留不唯一，那么，直到启动服务时，才会检测到名称冲突。</span><span class="sxs-lookup"><span data-stu-id="f087a-107">If you create URL reservations that are not unique, the name conflict might not be detected until you start the service.</span></span> <span data-ttu-id="f087a-108">因此，请确保遵循命名约定或规则以确保所有的值保持唯一。</span><span class="sxs-lookup"><span data-stu-id="f087a-108">For this reason, make sure that you follow naming conventions or rules to ensure all values are unique.</span></span>  
  
## <a name="default-naming-conventions"></a><span data-ttu-id="f087a-109">默认的命名约定</span><span class="sxs-lookup"><span data-stu-id="f087a-109">Default Naming Conventions</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f087a-110">安装到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命名实例中。</span><span class="sxs-lookup"><span data-stu-id="f087a-110">can be installed within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named instance.</span></span> <span data-ttu-id="f087a-111">当你在命名实例中安装或配置报表服务器时，实例名称会自动包括在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供的默认 URL 预留中的虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="f087a-111">When you install or configure a report server within a named instance, the instance name is automatically included in the virtual directory in the default URL reservation that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides.</span></span> <span data-ttu-id="f087a-112">下表显示了默认实例和命名实例的 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="f087a-112">The following table shows the URL reservations for a default instance and a named instance.</span></span>  
  
|<span data-ttu-id="f087a-113">SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="f087a-113">SQL Server Instance</span></span>|<span data-ttu-id="f087a-114">默认 URL 预留</span><span class="sxs-lookup"><span data-stu-id="f087a-114">Default URL Reservation</span></span>|  
|-------------------------|-----------------------------|  
|<span data-ttu-id="f087a-115">默认实例 (MSSQLServer)</span><span class="sxs-lookup"><span data-stu-id="f087a-115">Default (MSSQLServer)</span></span>|http://+:80/reportserver|  
|<span data-ttu-id="f087a-116">命名实例 (MynamedInstance)</span><span class="sxs-lookup"><span data-stu-id="f087a-116">Named (MynamedInstance)</span></span>|http://+:80/reportserver_MyNamedInstance|  
  
 <span data-ttu-id="f087a-117">对于命名实例，虚拟目录中包括实例名称。</span><span class="sxs-lookup"><span data-stu-id="f087a-117">For the named instance, the virtual directory includes the instance name.</span></span> <span data-ttu-id="f087a-118">默认实例和命名实例在同一个端口上侦听，但是唯一的虚拟目录名称确定了请求将由哪个报表服务器获取。</span><span class="sxs-lookup"><span data-stu-id="f087a-118">Both the default instance and the named instance listen on the same port, but the unique virtual directory names determine which report server gets the request.</span></span>  
  
 <span data-ttu-id="f087a-119">建议的最佳实践是使用虚拟目录名称来区分报表服务器实例，</span><span class="sxs-lookup"><span data-stu-id="f087a-119">Best practice recommendations are to use the virtual directory name to distinguish among the report server instance.</span></span> <span data-ttu-id="f087a-120">这样可在 URL 和目标实例之间提供清楚的对应关系，并确保应用程序名称在整个系统中保持唯一。</span><span class="sxs-lookup"><span data-stu-id="f087a-120">It provides a clear correspondence between a URL and the target instance, and ensures that the application names are unique across the whole system.</span></span>  
  
## <a name="custom-naming-conventions"></a><span data-ttu-id="f087a-121">自定义命名约定</span><span class="sxs-lookup"><span data-stu-id="f087a-121">Custom Naming Conventions</span></span>  
 <span data-ttu-id="f087a-122">尽管建议使用实例名称，但是你可以使用 URL 语法和自己的命名约定来满足 URL 预留的唯一名称约束。</span><span class="sxs-lookup"><span data-stu-id="f087a-122">Although using the instance name is recommended, you can use the URL syntax and your own naming conventions to meet the unique name constraints for URL reservations.</span></span> <span data-ttu-id="f087a-123">下面的示例说明了用来为每个实例创建唯一 URL 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="f087a-123">The following examples illustrate different approaches for creating unique URLs for each instance.</span></span>  
  
|<span data-ttu-id="f087a-124">报表服务器的默认实例 (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="f087a-124">Report Server default instance (MSSQLSERVER)</span></span>|<span data-ttu-id="f087a-125">ReportServer_MyNamedInstance</span><span class="sxs-lookup"><span data-stu-id="f087a-125">ReportServer_MyNamedInstance</span></span>|<span data-ttu-id="f087a-126">唯一性</span><span class="sxs-lookup"><span data-stu-id="f087a-126">Uniqueness</span></span>|  
|----------------------------------------------------|-----------------------------------|----------------|  
|http://+:80/reportserver|http://+:8888/reportserver|<span data-ttu-id="f087a-127">每个实例都在一个不同的端口上侦听。</span><span class="sxs-lookup"><span data-stu-id="f087a-127">Each instance listens on a different port.</span></span>|  
|`http://www.contoso.com/reportserver`|`http://SRVR-46/reportserver`|<span data-ttu-id="f087a-128">每个实例都对应不同的服务器名称（完全限定域名和计算机名称）。</span><span class="sxs-lookup"><span data-stu-id="f087a-128">Each instance responds to different server names (fully qualified domain name, and machine name).</span></span>|  
  
## <a name="uniqueness-requirements"></a><span data-ttu-id="f087a-129">唯一性要求</span><span class="sxs-lookup"><span data-stu-id="f087a-129">Uniqueness Requirements</span></span>  
 <span data-ttu-id="f087a-130">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用的基础技术对于唯一名称施加了一定的要求。</span><span class="sxs-lookup"><span data-stu-id="f087a-130">The underlying technologies used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] impose requirements around unique names.</span></span> <span data-ttu-id="f087a-131">HTTP.SYS 要求其存储库中的所有 URL 保持唯一。</span><span class="sxs-lookup"><span data-stu-id="f087a-131">HTTP.SYS requires that all URLs within its repository be unique.</span></span> <span data-ttu-id="f087a-132">您可以通过改变端口、主机名或虚拟目录名称来创建唯一的 URL。</span><span class="sxs-lookup"><span data-stu-id="f087a-132">You can vary the port, host name, or virtual directory name to create a unique URL.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="f087a-133">要求同一个进程内的应用程序标识保持唯一。</span><span class="sxs-lookup"><span data-stu-id="f087a-133">requires that application identities be unique within the same process.</span></span> <span data-ttu-id="f087a-134">此要求会影响虚拟目录名称。</span><span class="sxs-lookup"><span data-stu-id="f087a-134">This requirement affects the virtual directory names.</span></span> <span data-ttu-id="f087a-135">它规定您不能在同一个报表服务器实例中复制虚拟目录名称。</span><span class="sxs-lookup"><span data-stu-id="f087a-135">It specifies that you cannot duplicate a virtual directory name within the same report server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f087a-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f087a-136">See Also</span></span>  
 <span data-ttu-id="f087a-137">[配置报表服务器 URL（SSRS 配置管理器）](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f087a-137">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="f087a-138">配置 URL（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="f087a-138">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](configure-a-url-ssrs-configuration-manager.md)  
  
  
