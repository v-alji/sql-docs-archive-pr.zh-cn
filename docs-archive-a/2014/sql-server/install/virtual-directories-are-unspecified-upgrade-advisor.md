---
title: 虚拟目录未指定 (升级顾问) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e20c48d0bf58d28cb2894baa26c2e11db26fab96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586107"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a><span data-ttu-id="4fe84-102">未指定虚拟目录（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="4fe84-102">Virtual directories are unspecified (Upgrade Advisor)</span></span>
  <span data-ttu-id="4fe84-103">升级顾问检测不到报表服务器 Web 服务或报表管理器的虚拟目录设置。</span><span class="sxs-lookup"><span data-stu-id="4fe84-103">Upgrade Advisor did not detect virtual directory settings for the Report Server Web service or Report Manager.</span></span> <span data-ttu-id="4fe84-104">升级完成后，你必须使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器为报表服务器配置 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="4fe84-104">After upgrade completes, you must configure URL reservations for the report server by using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
||  
|-|  
|<span data-ttu-id="4fe84-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="4fe84-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="4fe84-106">组件</span><span class="sxs-lookup"><span data-stu-id="4fe84-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4fe84-107">说明</span><span class="sxs-lookup"><span data-stu-id="4fe84-107">Description</span></span>  
 <span data-ttu-id="4fe84-108">升级 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装包括为报表服务器 Web 服务和报表管理器保留新的 URL。</span><span class="sxs-lookup"><span data-stu-id="4fe84-108">Upgrading a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation includes reserving new URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="4fe84-109">升级顾问检测不到要升级实例的报表服务器或报表管理器的虚拟目录，因此升级进程信息不足，无法为升级后的报表服务器创建 URL 预留。</span><span class="sxs-lookup"><span data-stu-id="4fe84-109">Upgrade Advisor did not detect virtual directories for the report server or Report Manager for the instance to be upgraded, and therefore the upgrade process has insufficient information to create URL reservations for the upgraded report server.</span></span> <span data-ttu-id="4fe84-110">升级可以继续，但在升级的安装后，报表服务器或报表管理器虚拟目录将是未定义的。</span><span class="sxs-lookup"><span data-stu-id="4fe84-110">Upgrade can continue, but the report server or Report Manager virtual directory will be undefined after the upgraded installation.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="4fe84-111">纠正措施</span><span class="sxs-lookup"><span data-stu-id="4fe84-111">Corrective Action</span></span>  
 <span data-ttu-id="4fe84-112">升级完成后，请使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器为报表服务器和报表管理器设置 URL。</span><span class="sxs-lookup"><span data-stu-id="4fe84-112">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to set the URLs for report server and Report Manager.</span></span> <span data-ttu-id="4fe84-113">使用 IIS 管理器删除不再需要的所有虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="4fe84-113">Use IIS Manager to remove any virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="4fe84-114">有关详细信息，请参阅联机丛书中[的配置 URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4fe84-114">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe84-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fe84-115">See Also</span></span>  
 [<span data-ttu-id="4fe84-116">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="4fe84-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
