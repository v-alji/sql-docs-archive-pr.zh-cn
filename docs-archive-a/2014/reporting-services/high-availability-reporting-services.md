---
title: 高可用性 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfa0548bc526b007c4301572cd1a8e47a2851e18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591761"
---
# <a name="high-availability-reporting-services"></a><span data-ttu-id="1bcf6-102">高可用性 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="1bcf6-102">High Availability (Reporting Services)</span></span>
  <span data-ttu-id="1bcf6-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器是一种无状态服务器，它在两个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 关系数据库中存储应用程序数据、内容、属性和会话信息。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-103">A [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is a stateless server that stores application data, content, properties, and session information in two [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational databases.</span></span> <span data-ttu-id="1bcf6-104">因此，确保 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能的可用性的最佳做法是执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1bcf6-104">As such, the best way to ensure the availability of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality is to do the following:</span></span>  
  
-   <span data-ttu-id="1bcf6-105">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 的高可用性功能来最大化报表服务器数据库的正常运行时间。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-105">Use the high availability features of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] to maximize the uptime of the report server databases.</span></span> <span data-ttu-id="1bcf6-106">如果您将某个 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例配置为在故障转移群集中运行，则在创建报表服务器数据库时可选择该实例。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-106">If you configure a [!INCLUDE[ssDE](../includes/ssde-md.md)] instance to run in a failover cluster, you can select that instance when you create a report server database.</span></span>  
  
-   <span data-ttu-id="1bcf6-107">将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 用于 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 数据库并且在可能的情况下用于数据源。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-107">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] databases and for data sources, as possible.</span></span> <span data-ttu-id="1bcf6-108">有关详细信息，请参阅 [Reporting Services 与 AlwaysOn 可用性组 (SQL Server)](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-108">For more information, see [Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1bcf6-109">将多个报表服务器配置为在扩展部署下运行，其中所有服务器共享一个报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-109">Configure multiple report servers to run in a scale-out deployment, where all the servers share a single report server database.</span></span> <span data-ttu-id="1bcf6-110">如果在扩展部署中部署多个报表服务器实例（最好在不同的服务器上部署），将有助于在其中一个报表服务器实例出现故障时提供不间断的服务。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-110">Deploying multiple report server instances, preferably on different servers, in a scale-out deployment can help provide uninterrupted service in the event one of the report server instances goes down.</span></span>  
  
 <span data-ttu-id="1bcf6-111">扩展部署提供了一种共享数据库的方法。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-111">A scale-out deployment provides a way to share a database.</span></span> <span data-ttu-id="1bcf6-112">如果一台报表服务器出现故障，同一部署下的其他服务器还能继续工作。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-112">If one report server goes down, other servers in the same deployment will continue to work.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1bcf6-113">不能识别群集。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-113">is not cluster-aware.</span></span> <span data-ttu-id="1bcf6-114">扩展部署本身不提供负载平衡；它不会检测报表服务器上的处理负载，也不会将新的处理请求路由到最空闲的服务器。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-114">By itself, a scale-out deployment does not provide load balancing; it does not detect the processing loads on a report server and route new processing requests to the least busy server.</span></span> <span data-ttu-id="1bcf6-115">扩展部署不会重新路由在完成之前失败的处理请求。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-115">It does not re-route processing requests that failed before completion.</span></span> <span data-ttu-id="1bcf6-116">若要获取负载平衡功能，必须为承载报表服务器的 Web 服务器配置负载平衡，然后在扩展部署中对报表服务器进行配置以使它们共享同一个报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-116">To get load balancing features, you must configure load balancing for the Web servers that host the report servers, and then configure the report servers in a scale-out deployment so that they share the same report server database.</span></span>  
  
 <span data-ttu-id="1bcf6-117">报表服务器 Web 服务和 Windows 服务紧密集成，并作为一个报表服务器实例一起运行。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-117">The Report Server Web service and Windows service are tightly integrated and run together as a single report server instance.</span></span> <span data-ttu-id="1bcf6-118">您不能单独配置任一服务的可用性。</span><span class="sxs-lookup"><span data-stu-id="1bcf6-118">You cannot configure availability for one service separately from the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcf6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bcf6-119">See Also</span></span>  
 <span data-ttu-id="1bcf6-120">[高可用性解决方案 (SQL Server)](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1bcf6-120">[High Availability Solutions &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="1bcf6-121">配置本机模式报表服务器扩展部署（SSRS 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="1bcf6-121">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
