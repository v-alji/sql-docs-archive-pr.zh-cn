---
title: 功能规则 (升级) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 653b15db-a984-4b4b-b224-81b0285b099b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0527c1ba26fed86a6c1a3d3a2ea7c11b096474f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588880"
---
# <a name="feature-rules-upgrade"></a><span data-ttu-id="021d0-102">功能规则（升级）</span><span class="sxs-lookup"><span data-stu-id="021d0-102">Feature Rules (Upgrade)</span></span>
  <span data-ttu-id="021d0-103">在安装操作完成之前，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序会验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="021d0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="021d0-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间，系统会扫描将安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机，并检查是否有妨碍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 成功安装的任何情况。</span><span class="sxs-lookup"><span data-stu-id="021d0-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the system scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed and checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="021d0-105">在安装程序启动升级向导之前，系统会检索每一项的状态。</span><span class="sxs-lookup"><span data-stu-id="021d0-105">Before Setup starts the upgrade wizard, it retrieves the status of each item.</span></span> <span data-ttu-id="021d0-106">然后，将检索结果与所需条件进行比较并提供如何排除妨碍性问题的指导。</span><span class="sxs-lookup"><span data-stu-id="021d0-106">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="021d0-107">系统配置检查将会生成一个报告，该报告包含有关每个执行规则的简短说明以及执行状态。</span><span class="sxs-lookup"><span data-stu-id="021d0-107">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="021d0-108">系统配置检查报告位于% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="021d0-108">The system configuration check report is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="021d0-109">在执行安装操作之前，请查看以下主题：</span><span class="sxs-lookup"><span data-stu-id="021d0-109">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="021d0-110">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="021d0-110">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="021d0-111">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="021d0-111">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="021d0-112">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="021d0-112">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="021d0-113">SQL Server 中的本地语言版本</span><span class="sxs-lookup"><span data-stu-id="021d0-113">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="021d0-114">其他参考：</span><span class="sxs-lookup"><span data-stu-id="021d0-114">Other references:</span></span>  
  
1.  [<span data-ttu-id="021d0-115">支持的版本和版本升级</span><span class="sxs-lookup"><span data-stu-id="021d0-115">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="021d0-116">安装故障转移群集前的准备工作</span><span class="sxs-lookup"><span data-stu-id="021d0-116">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a><span data-ttu-id="021d0-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="021d0-117">See Also</span></span>  
 [<span data-ttu-id="021d0-118">安装规则</span><span class="sxs-lookup"><span data-stu-id="021d0-118">Install Rules</span></span>](../../../2014/sql-server/install/install-rules.md)  
  
  
