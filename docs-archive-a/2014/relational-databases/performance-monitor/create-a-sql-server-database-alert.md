---
title: 创建 SQL Server 数据库警报 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fd0cc926412d64f7686744ee60840a32473d2386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692864"
---
# <a name="create-a-sql-server-database-alert"></a><span data-ttu-id="bdeac-102">创建 SQL Server 数据库警报</span><span class="sxs-lookup"><span data-stu-id="bdeac-102">Create a SQL Server Database Alert</span></span>
  <span data-ttu-id="bdeac-103">可以使用系统监视器创建一个在达到系统监视器计数器的阈值时发出的警报。</span><span class="sxs-lookup"><span data-stu-id="bdeac-103">You can use System Monitor to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span> <span data-ttu-id="bdeac-104">系统监视器将启动一个应用程序（例如，为处理警报情况而编写的自定义应用程序）来响应警报。</span><span class="sxs-lookup"><span data-stu-id="bdeac-104">In response to the alert, System Monitor launches an application, such as a custom application written to handle the alert condition.</span></span> <span data-ttu-id="bdeac-105">例如，可以创建一个在死锁数超过特定值时发出的警报。</span><span class="sxs-lookup"><span data-stu-id="bdeac-105">For example, you could create an alert that is raised when the number of deadlocks exceeds a specific value.</span></span>  
  
 <span data-ttu-id="bdeac-106">此外，还可以通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来定义警报。</span><span class="sxs-lookup"><span data-stu-id="bdeac-106">Alerts also can be defined by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="bdeac-107">有关详细信息，请参阅 [“警报”](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="bdeac-107">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
 <span data-ttu-id="bdeac-108">有关使用系统监视器设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库警报的详细信息，请参阅[设置 SQL Server 数据库警报 (Windows)](../performance/set-up-a-sql-server-database-alert-windows.md)。</span><span class="sxs-lookup"><span data-stu-id="bdeac-108">For more information about using System Monitor to set up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database alert, see [Set Up a SQL Server Database Alert &#40;Windows&#41;](../performance/set-up-a-sql-server-database-alert-windows.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdeac-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdeac-109">See Also</span></span>  
 <span data-ttu-id="bdeac-110">[sp_add_alert (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bdeac-110">[sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql) </span></span>  
 [<span data-ttu-id="bdeac-111">sys.sysperfinfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bdeac-111">sys.sysperfinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql)  
  
  
