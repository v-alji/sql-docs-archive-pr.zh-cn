---
title: 在 Report Server 站点 (升级顾问) 检测到 ISAPI 筛选器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bff1834ddf1b8f90787a47a8fd58a240d2b715d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693196"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a><span data-ttu-id="522a5-102">在报表服务器站点上检测到 ISAPI 筛选器（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="522a5-102">ISAPI filters detected on the report server site (Upgrade Advisor)</span></span>
  <span data-ttu-id="522a5-103">升级顾问检测到承载报表服务器和报表管理器虚拟目录的网站上存在一个或多个 ISAPI 筛选器。</span><span class="sxs-lookup"><span data-stu-id="522a5-103">Upgrade Advisor detected one or more ISAPI filters on the Web site that hosts the report server and Report Manager virtual directories.</span></span> <span data-ttu-id="522a5-104">在中不支持 ISAPI 筛选器 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="522a5-104">ISAPI filters are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
||  
|-|  
|<span data-ttu-id="522a5-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机.</span><span class="sxs-lookup"><span data-stu-id="522a5-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native .</span></span>|  
  
## <a name="component"></a><span data-ttu-id="522a5-106">组件</span><span class="sxs-lookup"><span data-stu-id="522a5-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="522a5-107">说明</span><span class="sxs-lookup"><span data-stu-id="522a5-107">Description</span></span>  
 <span data-ttu-id="522a5-108">升级之前，请验证 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 应用程序是否使用了网站上的 ISAPI 筛选器。</span><span class="sxs-lookup"><span data-stu-id="522a5-108">Before upgrading, verify whether the ISAPI filters on the Web site are used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications.</span></span> <span data-ttu-id="522a5-109">如果不需要 ISAPI 筛选器，您可以升级报表服务器。</span><span class="sxs-lookup"><span data-stu-id="522a5-109">If you do not require the ISAPI filter, you can upgrade the report server.</span></span> <span data-ttu-id="522a5-110">安装程序将创建默认 URL，并且不为在 IIS 中运行的 ISAPI 筛选器提供支持。</span><span class="sxs-lookup"><span data-stu-id="522a5-110">Setup will create the default URLs, without support for the ISAPI filter that runs in IIS.</span></span> <span data-ttu-id="522a5-111">如果需要 ISAPI 筛选器，则在找到承载 ISAPI 筛选器的其他方法（例如，使用 ISA Server 或继续在 IIS 中承载 ISAPI 筛选器）之前请不要进行升级。</span><span class="sxs-lookup"><span data-stu-id="522a5-111">If you require the ISAPI filter, do not upgrade until you find an alternative way of hosting the ISAPI filter (for example, using ISA Server or continuing to host the ISAPI filter in IIS).</span></span> <span data-ttu-id="522a5-112">在某些情况下，报表服务器支持 ASP.NET HTTPModules 作为 ISAPI 筛选器的替代项。</span><span class="sxs-lookup"><span data-stu-id="522a5-112">The report server supports ASP.NET HTTPModules as a replacement for ISAPI filters in certain scenarios.</span></span> <span data-ttu-id="522a5-113">有关详细信息，请参阅 MSDN 上的 ASP.NET 文档。</span><span class="sxs-lookup"><span data-stu-id="522a5-113">For more information, see the ASP.NET documentation on MSDN.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="522a5-114">纠正措施</span><span class="sxs-lookup"><span data-stu-id="522a5-114">Corrective Action</span></span>  
 <span data-ttu-id="522a5-115">评估并使用其他解决方案来承载部署所需的 ISAPI 筛选器。</span><span class="sxs-lookup"><span data-stu-id="522a5-115">Evaluate and use a separate solution for hosting ISAPI filters required by your deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522a5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="522a5-116">See Also</span></span>  
 [<span data-ttu-id="522a5-117">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="522a5-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
