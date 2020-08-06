---
title: 升级顾问 (Reporting Services 升级问题) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 569afe735d68a724c0b4cc61ad2b7767088c2b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591091"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a><span data-ttu-id="64110-102">Reporting Services 升级问题（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="64110-102">Reporting Services Upgrade Issues (Upgrade Advisor)</span></span>
  <span data-ttu-id="64110-103">以下主题介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可能会影响升级到的问题 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="64110-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] issues that might affect your upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="64110-104">这些主题介绍你可以采取哪些措施来缓解这些更改对环境的影响。</span><span class="sxs-lookup"><span data-stu-id="64110-104">The topics describe actions that you can take to mitigate the effect of these changes on your environment.</span></span>  
  
 <span data-ttu-id="64110-105">升级顾问可分析报表服务器安装。</span><span class="sxs-lookup"><span data-stu-id="64110-105">Upgrade Advisor analyzes a report server installation.</span></span> <span data-ttu-id="64110-106">如果仅安装了客户端组件（例如，如果报表设计器是安装在计算机中的唯一 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件），则不会报告任何问题。</span><span class="sxs-lookup"><span data-stu-id="64110-106">If only client components are installed (for example, if Report Designer is the only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component installed on the computer), no issues will be reported.</span></span>  
  
 <span data-ttu-id="64110-107">根据安装的配置方式，您可能会遇到升级顾问未报告的其他问题。</span><span class="sxs-lookup"><span data-stu-id="64110-107">Depending on how you configured your installation, you may encounter additional issues that are not reported by Upgrade Advisor.</span></span> <span data-ttu-id="64110-108">这些问题不会阻止 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 升级成功，但是它们可能影响升级完成后报表和应用程序的运行方式。</span><span class="sxs-lookup"><span data-stu-id="64110-108">These issues do not prevent a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] upgrade from succeeding, but they may affect how reports and applications run after an upgrade is finished.</span></span> <span data-ttu-id="64110-109">若要了解这些问题，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“Reporting Services 的向后兼容性”。</span><span class="sxs-lookup"><span data-stu-id="64110-109">To learn about these issues, see "Reporting Services Backward Compatibility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="64110-110">如果无法使用安装程序升级 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装，你可以安装新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例并将现有安装迁移到新的实例。</span><span class="sxs-lookup"><span data-stu-id="64110-110">If you cannot use Setup to upgrade a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can install a new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance and migrate your existing installation to the new instance.</span></span> <span data-ttu-id="64110-111">有关详细信息，请参阅联机丛书中的 "升级和迁移 Reporting Services" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，[然后 Reporting Services 升级和迁移](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="64110-111">For more information, see "Upgrade and Migrate Reporting Services" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
 <span data-ttu-id="64110-112">以下主题介绍升级顾问报告的已知问题，并解释可以如何修改现有安装以顺利进行升级。</span><span class="sxs-lookup"><span data-stu-id="64110-112">The following topics describe known issues that are reported by Upgrade Advisor, and explain how you can modify your existing installation to allow an upgrade to occur.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64110-113">若要分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例，升级顾问必须安装在报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="64110-113">Upgrade Advisor must be installed on the report server to analyze an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="64110-114">不支持远程分析。</span><span class="sxs-lookup"><span data-stu-id="64110-114">does not support remote analysis.</span></span>  
>   
>  <span data-ttu-id="64110-115">有关详细信息，请参阅[安装升级顾问](../../../2014/sql-server/install/installing-upgrade-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="64110-115">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64110-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="64110-116">In This Section</span></span>  
  
-   [<span data-ttu-id="64110-117">Report Server 网站上的客户端证书 &#40;升级顾问&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-117">Client certificates on the report server web site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-118">在升级顾问 &#40;Report Server 上检测到自定义扩展&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-118">Custom extensions were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-119">在升级顾问 &#40;Report Server 上检测到自定义报表项&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-119">Custom report items were detected on the report server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-120">&#40;升级顾问未检测到 IIS 向后兼容组件&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-120">IIS backward compatibility components were not detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-121">&#40;升级顾问检测到 IP 地址限制&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-121">IP address restriction detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-122">在 Report Server 站点 &#40;升级顾问上检测到 ISAPI 筛选器&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-122">ISAPI filters detected on the report server site &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-123">在 Report Server 计算机 &#40;升级顾问上检测到过时的扩展&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-123">Obsolete extensions were detected on the report server computer &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-124">&#40;升级顾问&#41;未配置报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="64110-124">Report server database is not configured &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-125">SQL Server 2005 &#40;升级顾问检测到报表服务器 Web 服务组&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-125">SQL Server 2005 Report Server Web Service group detected &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-126">&#40;升级顾问指定虚拟目录&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-126">Virtual directories are unspecified &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-127">虚拟目录具有不受支持的身份验证方法 &#40;升级顾问&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-127">Virtual directory has unsupported authentication method &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-128">SQL Server Standard 和 Enterprise &#40;Upgrade Advisor 的 CPU 和内存限制的变化&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-128">Changes to CPU and memory limits for SQL Server Standard and Enterprise &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-129">SharePoint 场 &#40;升级顾问所需的域帐户&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-129">Domain accounts required for SharePoint farm &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-130">直接浏览到报表服务器 &#40;升级顾问&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-130">Direct Browsing to Report Server &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-131">Microsoft SharePoint 2007 安装 &#40;升级顾问&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-131">Microsoft SharePoint 2007 is Installed &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-132">Microsoft SQL Server Reporting Services SharePoint 共享服务是并行 &#40;升级顾问安装的&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-132">Microsoft SQL Server Reporting Services SharePoint Shared Service is Installed Side by Side &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-133">升级顾问 &#40;数据库引擎服务器排序规则不兼容&#41;</span><span class="sxs-lookup"><span data-stu-id="64110-133">Incompatible Database Engine Server Collation &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [<span data-ttu-id="64110-134">其他 Reporting Services 升级问题</span><span class="sxs-lookup"><span data-stu-id="64110-134">Other Reporting Services Upgrade Issues</span></span>](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
