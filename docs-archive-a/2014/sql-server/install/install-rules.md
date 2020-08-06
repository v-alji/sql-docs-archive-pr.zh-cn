---
title: 安装规则 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SCC
- System Configuration Check, Setup
helpviewer_keywords:
- System Configuration Check page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, System Configuration Check page
- SCC [SQL Server]
ms.assetid: 168c0445-5651-42fc-91f4-d9f27d9e2281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3d9fe413174613cadc9277e5c7f21695a4021c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692139"
---
# <a name="install-rules"></a><span data-ttu-id="ee54b-102">安装规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-102">Install Rules</span></span>
  <span data-ttu-id="ee54b-103">在安装操作完成之前，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序会验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="ee54b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="ee54b-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中，系统配置检查器 (SCC) 会对将要安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机进行扫描。</span><span class="sxs-lookup"><span data-stu-id="ee54b-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="ee54b-105">SCC 将检查阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装操作成功完成的条件。</span><span class="sxs-lookup"><span data-stu-id="ee54b-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="ee54b-106">在安装程序启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导之前，SCC 会检索每个项的状态。</span><span class="sxs-lookup"><span data-stu-id="ee54b-106">Before Setup starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="ee54b-107">然后，将检索结果与所需条件进行比较并提供如何排除妨碍性问题的指导。</span><span class="sxs-lookup"><span data-stu-id="ee54b-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="ee54b-108">系统配置检查将会生成一个报告，该报告包含有关每个执行规则的简短说明以及执行状态。</span><span class="sxs-lookup"><span data-stu-id="ee54b-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="ee54b-109">系统配置检查报告位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="ee54b-109">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="ee54b-110">在执行安装操作之前，请查看以下主题：</span><span class="sxs-lookup"><span data-stu-id="ee54b-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="ee54b-111">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="ee54b-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="ee54b-112">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="ee54b-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="ee54b-113">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="ee54b-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="ee54b-114">SQL Server 中的本地语言版本</span><span class="sxs-lookup"><span data-stu-id="ee54b-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="ee54b-115">其他参考：</span><span class="sxs-lookup"><span data-stu-id="ee54b-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="ee54b-116">支持的版本和版本升级</span><span class="sxs-lookup"><span data-stu-id="ee54b-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="ee54b-117">安装故障转移群集前的准备工作</span><span class="sxs-lookup"><span data-stu-id="ee54b-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a><span data-ttu-id="ee54b-118">其他规则主题</span><span class="sxs-lookup"><span data-stu-id="ee54b-118">Additional Rule topics</span></span>  
 <span data-ttu-id="ee54b-119">有关方案特定的安装规则，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="ee54b-119">See the following topics for scenario-specific Setup rules:</span></span>  
  
-   [<span data-ttu-id="ee54b-120">安装规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-120">Installation Rules</span></span>](../../../2014/sql-server/install/installation-rules.md)  
  
-   [<span data-ttu-id="ee54b-121">功能规则 &#40;升级&#41;</span><span class="sxs-lookup"><span data-stu-id="ee54b-121">Feature Rules &#40;Upgrade&#41;</span></span>](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [<span data-ttu-id="ee54b-122">版本升级规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-122">Edition Upgrade Rules</span></span>](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [<span data-ttu-id="ee54b-123">卸载规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-123">Uninstallation rules</span></span>](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [<span data-ttu-id="ee54b-124">准备映像规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-124">Prepare Image Rules</span></span>](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [<span data-ttu-id="ee54b-125">完成映像规则</span><span class="sxs-lookup"><span data-stu-id="ee54b-125">Complete Image Rules</span></span>](../../../2014/sql-server/install/complete-image-rules.md)  
  
  
