---
title: " (升级顾问) 检测到 IP 地址限制 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2028e59e91d42bfdced2d18fa6ce129dfb108302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689721"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a><span data-ttu-id="01154-102">检测到 IP 地址限制（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="01154-102">IP address restriction detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="01154-103">升级顾问已检测到承载报表服务器或报表管理器虚拟目录的 IIS 网站上存在一个或多个 IP 地址限制。</span><span class="sxs-lookup"><span data-stu-id="01154-103">Upgrade Advisor detected one or more IP address restrictions on the IIS Web site that hosts the report server or Report Manager virtual directories.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="01154-104">不为 IP 地址限制提供本机支持。</span><span class="sxs-lookup"><span data-stu-id="01154-104">does not provide native support for IP address restrictions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="01154-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机.</span><span class="sxs-lookup"><span data-stu-id="01154-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="01154-106">组件</span><span class="sxs-lookup"><span data-stu-id="01154-106">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="01154-107">说明</span><span class="sxs-lookup"><span data-stu-id="01154-107">Description</span></span>  
 <span data-ttu-id="01154-108">安装程序不能针对升级后的报表服务器创建的 URL 定义 IP 地址限制。</span><span class="sxs-lookup"><span data-stu-id="01154-108">Setup cannot define IP address restrictions on URLs created for an upgraded report server.</span></span> <span data-ttu-id="01154-109">升级可以继续，但不会针对 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 定义 IP 地址限制。</span><span class="sxs-lookup"><span data-stu-id="01154-109">Upgrade can continue, but IP address restrictions will not be defined on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="01154-110">纠正措施</span><span class="sxs-lookup"><span data-stu-id="01154-110">Corrective Action</span></span>  
 <span data-ttu-id="01154-111">升级后，使用 ISA Server、防火墙软件或其他解决方案允许或排除从特定 IP 地址到报表服务器的请求。</span><span class="sxs-lookup"><span data-stu-id="01154-111">After upgrade, use ISA Server, your firewall software, or another solution to allow or exclude requests from specific IP addresses to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01154-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="01154-112">See Also</span></span>  
 [<span data-ttu-id="01154-113">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="01154-113">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
