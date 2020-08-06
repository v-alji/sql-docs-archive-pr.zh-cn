---
title: " (Upgrade Advisor) Report Server 计算机上检测到过时的扩展插件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9da9c47285bf809fdf6c89d67e847304d7d29a81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590517"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a><span data-ttu-id="83c63-102">在报表服务器计算机上检测到过时的扩展插件（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="83c63-102">Obsolete extensions were detected on the report server computer (Upgrade Advisor)</span></span>
  <span data-ttu-id="83c63-103">升级顾问检测到当前版本中不再可用的一个或多个呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="83c63-103">Upgrade Advisor detected one or more rendering extensions that are no longer available in the current release.</span></span>  
  
||  
|-|  
|<span data-ttu-id="83c63-104">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="83c63-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="83c63-105">组件</span><span class="sxs-lookup"><span data-stu-id="83c63-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="83c63-106">说明</span><span class="sxs-lookup"><span data-stu-id="83c63-106">Description</span></span>  
 <span data-ttu-id="83c63-107">报表服务器配置为使用在此版本中不再支持的一个或多个扩展插件。</span><span class="sxs-lookup"><span data-stu-id="83c63-107">The report server is configured to use one or more extensions that have been discontinued in this release.</span></span> <span data-ttu-id="83c63-108">不再支持的扩展插件包括：</span><span class="sxs-lookup"><span data-stu-id="83c63-108">Discontinued extensions include:</span></span>  
  
-   <span data-ttu-id="83c63-109">HTML OWC 呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="83c63-109">HTML OWC rendering extension</span></span>  
  
-   <span data-ttu-id="83c63-110">HTML 3.2 呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="83c63-110">HTML 3.2 rendering extension</span></span>  
  
 <span data-ttu-id="83c63-111">升级可以继续，但是不支持的功能将不再可用于升级后的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="83c63-111">Upgrade can continue, but the unsupported functionality will no longer be available on the upgraded report server.</span></span>  
  
 <span data-ttu-id="83c63-112">直到您要求这些扩展插件，则在找到针对这些要求的替代解决方案前，不要升级。</span><span class="sxs-lookup"><span data-stu-id="83c63-112">If you require these extensions, do not upgrade until you find an alternate solution to these requirements.</span></span> <span data-ttu-id="83c63-113">您可能需要获取或生成一个提供相同或类似功能的自定义呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="83c63-113">You might need to obtain or build a custom rendering extension that provides the same or similar functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="83c63-114">纠正措施</span><span class="sxs-lookup"><span data-stu-id="83c63-114">Corrective Action</span></span>  
 <span data-ttu-id="83c63-115">评估 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中包含的当前功能集以确定支持的功能是否满足您的要求。</span><span class="sxs-lookup"><span data-stu-id="83c63-115">Evaluate the current set of features that are included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to determine whether supported functionality meets your requirements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c63-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="83c63-116">See Also</span></span>  
 [<span data-ttu-id="83c63-117">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="83c63-117">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
