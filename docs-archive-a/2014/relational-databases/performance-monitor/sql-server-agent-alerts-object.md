---
title: SQL Server 代理 - Alerts 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9aa6fa871730af8cf129b3ea6b0aa4f1853d7e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579544"
---
# <a name="sql-server-agent-alerts-object"></a><span data-ttu-id="f113f-102">SQL Server 代理中的 Alerts 对象</span><span class="sxs-lookup"><span data-stu-id="f113f-102">SQL Server Agent, Alerts Object</span></span>
  <span data-ttu-id="f113f-103">SQL Server 代理中的 **Alerts** 性能对象包含性能计数器，可报告有关 SQL Server 代理警报的信息。</span><span class="sxs-lookup"><span data-stu-id="f113f-103">The SQL Server Agent **Alerts** performance object contains performance counters that report information about SQL Server Agent alerts.</span></span> <span data-ttu-id="f113f-104">下表列出了此对象包含的计数器。</span><span class="sxs-lookup"><span data-stu-id="f113f-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="f113f-105">下表介绍了 **SQLAgent:Alerts** 计数器。</span><span class="sxs-lookup"><span data-stu-id="f113f-105">The table below contains the **SQLAgent:Alerts** counters.</span></span>  
  
|<span data-ttu-id="f113f-106">名称</span><span class="sxs-lookup"><span data-stu-id="f113f-106">Name</span></span>|<span data-ttu-id="f113f-107">说明</span><span class="sxs-lookup"><span data-stu-id="f113f-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="f113f-108">**Activated alerts**</span><span class="sxs-lookup"><span data-stu-id="f113f-108">**Activated alerts**</span></span>|<span data-ttu-id="f113f-109">此计数器可报告自上次 SQL Server 代理重新启动以来 SQL Server 代理已经激活的警报总数。</span><span class="sxs-lookup"><span data-stu-id="f113f-109">This counter reports the total number of alerts that SQL Server Agent has activated since the last time that SQL Server Agent restarted.</span></span>|  
|<span data-ttu-id="f113f-110">**Alerts activated/minute**</span><span class="sxs-lookup"><span data-stu-id="f113f-110">**Alerts activated/minute**</span></span>|<span data-ttu-id="f113f-111">此计数器可报告上一分钟内 SQL Server 代理激活的警报数。</span><span class="sxs-lookup"><span data-stu-id="f113f-111">This counter reports the number of alerts that SQL Server Agent activated within the last minute.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f113f-112">用户必须是 **sysadmin** 固定服务器角色的成员，才能使用此 SQL Server 代理对象。</span><span class="sxs-lookup"><span data-stu-id="f113f-112">To use this SQL Server Agent object, users must be a member of the **sysadmin** fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f113f-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f113f-113">See Also</span></span>  
 <span data-ttu-id="f113f-114">[Alerts](../../ssms/agent/alerts.md) </span><span class="sxs-lookup"><span data-stu-id="f113f-114">[Alerts](../../ssms/agent/alerts.md) </span></span>  
 <span data-ttu-id="f113f-115">[使用性能对象](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f113f-115">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="f113f-116">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="f113f-116">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
