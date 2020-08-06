---
title: " (升级顾问) ，未检测到 IIS 向后兼容组件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a5aad54a01b3840e121c6a63de0ea26f35921fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590525"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a><span data-ttu-id="70127-102">未检测到 IIS 向后兼容组件（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="70127-102">IIS backward compatibility components were not detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="70127-103">升级顾问未检测到用于为安装程序提供所需信息以创建新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 的 IIS 组件和设置。</span><span class="sxs-lookup"><span data-stu-id="70127-103">Upgrade Advisor did not detect IIS components and settings that provide information used by Setup to create new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLS.</span></span>  
  
||  
|-|  
|<span data-ttu-id="70127-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="70127-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="70127-105">组件</span><span class="sxs-lookup"><span data-stu-id="70127-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="70127-106">说明</span><span class="sxs-lookup"><span data-stu-id="70127-106">Description</span></span>  
 <span data-ttu-id="70127-107">IIS 包括了可提供报表服务器和报表管理器虚拟目录相关信息的组件，而这些组件未安装在报表服务器计算机上。</span><span class="sxs-lookup"><span data-stu-id="70127-107">IIS includes components that provide information about the report server and Report Manager virtual directories, and those components are not installed on the report server computer.</span></span> <span data-ttu-id="70127-108">升级可继续进行，但升级操作不会重新创建报表服务器或报表管理器的 URL。</span><span class="sxs-lookup"><span data-stu-id="70127-108">Upgrade can continue, but URLs for the report server or Report Manager will not be recreated by upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="70127-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="70127-109">Corrective Action</span></span>  
 <span data-ttu-id="70127-110">升级完成后，请使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具为报表服务器或报表管理器设置 URL。</span><span class="sxs-lookup"><span data-stu-id="70127-110">After upgrade finishes, use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to set the URLs for report server or Report Manager.</span></span> <span data-ttu-id="70127-111">使用 IIS 管理器删除不再需要的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="70127-111">Use IIS Manager to remove the virtual directories you no longer need.</span></span>  
  
 <span data-ttu-id="70127-112">有关详细信息，请参阅联机丛书中[的配置 URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="70127-112">For more information, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70127-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70127-113">See Also</span></span>  
 [<span data-ttu-id="70127-114">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="70127-114">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
