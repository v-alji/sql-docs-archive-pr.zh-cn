---
title: 升级 SQL Server 管理工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- management tools, upgrading
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
author: stevestein
ms.author: sstein
ms.openlocfilehash: b6424d27a2bc7ecfc60ed01ce144e92802fdaea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580338"
---
# <a name="upgrade-sql-server-management-tools"></a><span data-ttu-id="88260-102">升级 SQL Server 管理工具</span><span class="sxs-lookup"><span data-stu-id="88260-102">Upgrade SQL Server Management Tools</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="88260-103">支持从 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本进行升级。</span><span class="sxs-lookup"><span data-stu-id="88260-103">supports upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later.</span></span> <span data-ttu-id="88260-104">本主题介绍对升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理工具和管理组件（如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、数据库邮件、维护计划、XPStar 和 XPWeb）的支持及其行为。</span><span class="sxs-lookup"><span data-stu-id="88260-104">This topic documents support and behavior for upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools and management components such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Database Mail, Maintenance Plans, XPStar, and XPWeb.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="88260-105">对于本地安装，必须以管理员身份运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="88260-105">For local installations, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup as an administrator.</span></span> <span data-ttu-id="88260-106">如果从远程共享位置运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序，必须使用对该远程共享位置具有读取和执行权限的域帐户。</span><span class="sxs-lookup"><span data-stu-id="88260-106">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="88260-107">已知升级问题</span><span class="sxs-lookup"><span data-stu-id="88260-107">Known Upgrade Issues</span></span>  
 <span data-ttu-id="88260-108">在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，请考虑以下问题：</span><span class="sxs-lookup"><span data-stu-id="88260-108">Consider the following issues before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
### <a name="for-all-upgrade-scenarios"></a><span data-ttu-id="88260-109">对于所有升级方案：</span><span class="sxs-lookup"><span data-stu-id="88260-109">For all upgrade scenarios:</span></span>  
  
-   <span data-ttu-id="88260-110">在升级 MSX 服务器之前，应先对所有 TSX 服务器进行升级。</span><span class="sxs-lookup"><span data-stu-id="88260-110">All TSX servers should be upgraded before the MSX server is upgraded.</span></span> <span data-ttu-id="88260-111">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的 MSX/TSX 的详细信息，请参阅 [企业范围的自动化管理](../../ssms/agent/automated-administration-across-an-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="88260-111">For more information about MSX/TSX in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md).</span></span>  
  
-   <span data-ttu-id="88260-112">必须同时升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的所有组件。</span><span class="sxs-lookup"><span data-stu-id="88260-112">All components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be upgraded at the same time.</span></span> <span data-ttu-id="88260-113">[!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件的版本号在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]实例中必须相同。</span><span class="sxs-lookup"><span data-stu-id="88260-113">Version numbers of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components must be the same in an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="88260-114">在升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时可以向 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的现有安装添加组件。</span><span class="sxs-lookup"><span data-stu-id="88260-114">You can add components to an existing installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the time that you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="88260-115">有关详细信息，请参阅[使用安装向导升级到 SQL Server 2014 &#40;安装&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="88260-115">For more information, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="88260-116">客户端工具（如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问、sqlcmd 和 osql）不升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88260-116">Client Tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, sqlcmd, and osql are not upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="88260-117">相反，客户端工具与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本中的工具并行运行。</span><span class="sxs-lookup"><span data-stu-id="88260-117">Instead, Client Tools run side-by-side with tools from previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="88260-118">支持从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端工具导入设置。</span><span class="sxs-lookup"><span data-stu-id="88260-118">supports importing settings from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Tools.</span></span>  
  
-   <span data-ttu-id="88260-119">在升级期间，从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的身份验证将从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证更新为 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="88260-119">Authentication from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be updated from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to Windows Authentication during upgrade.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="88260-120">中不支持 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="88260-120">Authentication is not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="88260-121">在升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的过程中将保留有关作业和警报的数据。</span><span class="sxs-lookup"><span data-stu-id="88260-121">Data for jobs and alerts will be preserved during upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="88260-122">如果在要升级的实例中正在使用 SQLMail，则在升级之后将支持并启用关联的 XP。</span><span class="sxs-lookup"><span data-stu-id="88260-122">If SQLMail is being used in the instance to be upgraded, associated XPs will be supported and enabled after the upgrade.</span></span> <span data-ttu-id="88260-123">否则，将关闭它们。</span><span class="sxs-lookup"><span data-stu-id="88260-123">Otherwise, they will be off.</span></span>  
  
-   <span data-ttu-id="88260-124">数据库邮件（也称为 SQLiMail）将与 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]组件一起升级。</span><span class="sxs-lookup"><span data-stu-id="88260-124">Database Mail, also known as SQLiMail, will be upgraded with the [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="88260-125">默认情况下，数据库邮件在升级之后将会关闭。</span><span class="sxs-lookup"><span data-stu-id="88260-125">By default, Database Mail will be off after upgrade.</span></span> <span data-ttu-id="88260-126">升级之后，任何架构更新都应该与更新脚本进行协调。</span><span class="sxs-lookup"><span data-stu-id="88260-126">Any schema updates should be reconciled with an update script after upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88260-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="88260-127">See Also</span></span>  
 <span data-ttu-id="88260-128">[支持的版本升级](supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="88260-128">[Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="88260-129">[向后兼容性](../../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="88260-129">[Backward Compatibility](../../getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="88260-130">使用安装向导 &#40;安装程序升级到 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="88260-130">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
