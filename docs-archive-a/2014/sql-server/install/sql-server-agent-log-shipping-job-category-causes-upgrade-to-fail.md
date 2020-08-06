---
title: SQL Server 代理日志传送作业类别导致升级失败 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694227"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a><span data-ttu-id="fb5f7-102">SQL Server 代理的日志传送作业类别导致升级失败</span><span class="sxs-lookup"><span data-stu-id="fb5f7-102">SQL Server Agent log shipping job category causes upgrade to fail</span></span>
  <span data-ttu-id="fb5f7-103">如果存在名为“日志传送”的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业类别，升级过程将失败。</span><span class="sxs-lookup"><span data-stu-id="fb5f7-103">The upgrade process will fail if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category named Log Shipping exists.</span></span>  
  
## <a name="component"></a><span data-ttu-id="fb5f7-104">组件</span><span class="sxs-lookup"><span data-stu-id="fb5f7-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fb5f7-105">代理</span><span class="sxs-lookup"><span data-stu-id="fb5f7-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb5f7-106">说明</span><span class="sxs-lookup"><span data-stu-id="fb5f7-106">Description</span></span>  
 <span data-ttu-id="fb5f7-107">存在名为“日志传送”的系统作业类别。</span><span class="sxs-lookup"><span data-stu-id="fb5f7-107">There is a system job category named Log Shipping.</span></span> <span data-ttu-id="fb5f7-108">如果要进行升级的安装已包含用户创建的名为“日志传送”的作业类别，则必须先重命名该作业类别，然后才可进行升级；否则，升级过程将失败。</span><span class="sxs-lookup"><span data-stu-id="fb5f7-108">If an installation that is being upgraded already contains a user-created job category named Log Shipping, you must rename the job category before you upgrade; otherwise, the upgrade process will fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5f7-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb5f7-109">See Also</span></span>  
 <span data-ttu-id="fb5f7-110">[日志传送在升级后将不运行](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span><span class="sxs-lookup"><span data-stu-id="fb5f7-110">[Log shipping will not run after upgrading](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span></span>  
 <span data-ttu-id="fb5f7-111">[升级会将 SQL Server 代理用户代理帐户更改为临时 UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="fb5f7-111">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 [<span data-ttu-id="fb5f7-112">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="fb5f7-112">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
