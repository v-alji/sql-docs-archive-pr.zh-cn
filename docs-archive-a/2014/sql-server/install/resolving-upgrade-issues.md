---
title: 解决升级问题 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591088"
---
# <a name="resolving-upgrade-issues"></a><span data-ttu-id="5980b-102">解决升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-102">Resolving Upgrade Issues</span></span>
  <span data-ttu-id="5980b-103">本节主题介绍可以检测到的升级问题以及虽然检测不到但可能会对升级和升级后的使用造成影响的问题。</span><span class="sxs-lookup"><span data-stu-id="5980b-103">The topics in this section describe upgrade issues that can be detected as well as those that cannot be detected, but that might affect the upgrade or post-upgrade experience.</span></span> <span data-ttu-id="5980b-104">这些问题按 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件编排。</span><span class="sxs-lookup"><span data-stu-id="5980b-104">The issues are organized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5980b-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="5980b-105">In This Section</span></span>  
  
-   [<span data-ttu-id="5980b-106">最新的升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-106">Late-Breaking Upgrade Issues</span></span>](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [<span data-ttu-id="5980b-107">数据库引擎升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-107">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [<span data-ttu-id="5980b-108">全文搜索升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-108">Full-Text Search Upgrade Issues</span></span>](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [<span data-ttu-id="5980b-109">复制升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-109">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [<span data-ttu-id="5980b-110">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="5980b-110">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [<span data-ttu-id="5980b-111">SQL Server 代理升级问题</span><span class="sxs-lookup"><span data-stu-id="5980b-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a><span data-ttu-id="5980b-112">阻止升级的问题</span><span class="sxs-lookup"><span data-stu-id="5980b-112">Issues That Prevent Upgrading</span></span>  
 <span data-ttu-id="5980b-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的之前版本中的一些配置或设置可阻止您升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5980b-113">A few configurations or settings in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5980b-114">如果在您安装 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 时安装程序检测到这些问题，则安装程序停止升级过程，并请求您运行升级顾问和修复阻碍升级的所有问题。</span><span class="sxs-lookup"><span data-stu-id="5980b-114">If Setup detects these issues when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Setup stops the upgrade process and requests that you run Upgrade Advisor and fix any blocking issues.</span></span>  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 <span data-ttu-id="5980b-115">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 升级报表中列出了以下任务，则在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之前必须执行相应的所需操作：</span><span class="sxs-lookup"><span data-stu-id="5980b-115">If the following tasks are listed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] upgrade report, you must perform the required actions before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
-   [<span data-ttu-id="5980b-116">分离数据库 ID 32767</span><span class="sxs-lookup"><span data-stu-id="5980b-116">Detach database ID 32767</span></span>](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [<span data-ttu-id="5980b-117">重命名与固定服务器角色名称匹配的登录名</span><span class="sxs-lookup"><span data-stu-id="5980b-117">Rename logins matching fixed server role names</span></span>](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [<span data-ttu-id="5980b-118">重命名用户 sys</span><span class="sxs-lookup"><span data-stu-id="5980b-118">Rename user sys</span></span>](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [<span data-ttu-id="5980b-119">使用 sp_rename 重命名重复的索引名称</span><span class="sxs-lookup"><span data-stu-id="5980b-119">Use sp_rename to rename duplicate index name</span></span>](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a><span data-ttu-id="5980b-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5980b-120">See Also</span></span>  
 [<span data-ttu-id="5980b-121">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="5980b-121">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
