---
title: 升级后日志传送不会运行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2af60743cb2cbf9bf455397fe052c4e81f5a06d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591101"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a><span data-ttu-id="09fa3-102">日志传送在升级后将无法运行</span><span class="sxs-lookup"><span data-stu-id="09fa3-102">Log shipping will not run after upgrading</span></span>
  <span data-ttu-id="09fa3-103">升级顾问已检测您正在使用日志传送。</span><span class="sxs-lookup"><span data-stu-id="09fa3-103">Upgrade Advisor has detected that you are using log shipping.</span></span> [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] <span data-ttu-id="09fa3-104">的日志传送与 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的日志传送不兼容，因此不能直接升级。</span><span class="sxs-lookup"><span data-stu-id="09fa3-104">log shipping is incompatible with log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and cannot be upgraded directly.</span></span> <span data-ttu-id="09fa3-105">升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或存储过程重新配置日志传送。</span><span class="sxs-lookup"><span data-stu-id="09fa3-105">After upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fa3-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09fa3-106">See Also</span></span>  
 <span data-ttu-id="09fa3-107">[SQL Server 代理日志传送作业类别导致升级失败](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="09fa3-107">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 <span data-ttu-id="09fa3-108">[升级会将 SQL Server 代理用户代理帐户更改为临时 UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="09fa3-108">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 <span data-ttu-id="09fa3-109">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="09fa3-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="09fa3-110">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="09fa3-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
