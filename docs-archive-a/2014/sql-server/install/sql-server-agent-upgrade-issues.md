---
title: SQL Server 代理升级问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server Agent
- SQL Server Agent, upgrades
ms.assetid: 77e303ff-febd-4103-ae5d-6e5b85bc8009
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac234a757510af5ebfac261ea6d3e7e57d2f426f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689718"
---
# <a name="sql-server-agent-upgrade-issues"></a><span data-ttu-id="7c972-102">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="7c972-102">SQL Server Agent Upgrade Issues</span></span>
  <span data-ttu-id="7c972-103">下面的主题介绍了可能会对升级产生影响的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理问题。</span><span class="sxs-lookup"><span data-stu-id="7c972-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent issues that might affect an upgrade.</span></span> <span data-ttu-id="7c972-104">这些主题介绍了您可以为减小这些更改对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境的影响而采取的措施。</span><span class="sxs-lookup"><span data-stu-id="7c972-104">The topics describe actions that you can take to help reduce the effect of these changes on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c972-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="7c972-105">In This Section</span></span>  
  
-   [<span data-ttu-id="7c972-106">数据库维护计划被取代</span><span class="sxs-lookup"><span data-stu-id="7c972-106">Database maintenance plans superseded</span></span>](../../../2014/sql-server/install/database-maintenance-plans-superseded.md)  
  
-   [<span data-ttu-id="7c972-107">只有 sysadmin 用户才能将作业步骤日志文件写入文件系统</span><span class="sxs-lookup"><span data-stu-id="7c972-107">Only sysadmin users can write job step log files to the file system</span></span>](../../../2014/sql-server/install/only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)  
  
-   [<span data-ttu-id="7c972-108">将所用的 xp_sqlagent_proxy_account 扩展存储过程替换为新存储过程</span><span class="sxs-lookup"><span data-stu-id="7c972-108">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>](../../../2014/sql-server/install/replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)  
  
-   [<span data-ttu-id="7c972-109">SQL Server 代理的日志传送操作类别导致升级失败</span><span class="sxs-lookup"><span data-stu-id="7c972-109">SQL Server Agent log shipping job category causes upgrade to fail</span></span>](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)  
  
-   [<span data-ttu-id="7c972-110">SQL Server 代理服务不能使用 SQL Server 身份验证</span><span class="sxs-lookup"><span data-stu-id="7c972-110">SQL Server Agent Service cannot use SQL Server Authentication</span></span>](../../../2014/sql-server/install/sql-server-agent-service-cannot-use-sql-server-authentication.md)  
  
-   [<span data-ttu-id="7c972-111">更新 SQL Server 代理作业步骤中的标记语法</span><span class="sxs-lookup"><span data-stu-id="7c972-111">Update token syntax in SQL Server Agent job steps</span></span>](../../../2014/sql-server/install/update-token-syntax-in-sql-server-agent-job-steps.md)  
  
-   [<span data-ttu-id="7c972-112">升级主服务器前先升级所有目标服务器</span><span class="sxs-lookup"><span data-stu-id="7c972-112">Upgrade all target servers before upgrading the master server</span></span>](../../../2014/sql-server/install/upgrade-all-target-servers-before-upgrading-the-master-server.md)  
  
-   [<span data-ttu-id="7c972-113">升级会将 SQL Server 代理用户的代理帐户更改为临时的 UpgradedProxyAccount</span><span class="sxs-lookup"><span data-stu-id="7c972-113">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c972-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c972-114">See Also</span></span>  
 <span data-ttu-id="7c972-115">[SQL Server 2014 升级顾问 &#91;新&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="7c972-115">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="7c972-116">解决升级问题</span><span class="sxs-lookup"><span data-stu-id="7c972-116">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
