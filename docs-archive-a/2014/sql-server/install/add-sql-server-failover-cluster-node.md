---
title: 添加 SQL Server 故障转移群集节点 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e5035122-784f-40ee-8188-7f485a9ae3e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a4cad03db71b6736b7c590aabc7682eda04ec9a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586240"
---
# <a name="add-sql-server-failover-cluster-node"></a><span data-ttu-id="27875-102">添加 SQL Server 故障转移群集节点</span><span class="sxs-lookup"><span data-stu-id="27875-102">Add SQL Server Failover Cluster Node</span></span>
  <span data-ttu-id="27875-103">在安装操作完成之前，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序会验证您的计算机配置。</span><span class="sxs-lookup"><span data-stu-id="27875-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup validates your computer configuration before the Setup operation completes.</span></span> <span data-ttu-id="27875-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装过程中，系统配置检查器 (SCC) 会对将要安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机进行扫描。</span><span class="sxs-lookup"><span data-stu-id="27875-104">During [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, the System Configuration Checker (SCC) scans the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be installed.</span></span> <span data-ttu-id="27875-105">SCC 将检查阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装操作成功完成的条件。</span><span class="sxs-lookup"><span data-stu-id="27875-105">The SCC checks for conditions that prevent a successful [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup operation.</span></span> <span data-ttu-id="27875-106">在安装程序启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导之前，SCC 会检索每个项的状态。</span><span class="sxs-lookup"><span data-stu-id="27875-106">Before Setup starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, the SCC retrieves the status of each item.</span></span> <span data-ttu-id="27875-107">然后，将检索结果与所需条件进行比较并提供如何排除妨碍性问题的指导。</span><span class="sxs-lookup"><span data-stu-id="27875-107">It then compares the result with required conditions and provides guidance for removal of blocking issues.</span></span>  
  
 <span data-ttu-id="27875-108">系统配置检查将会生成一个报告，该报告包含有关每个执行规则的简短说明以及执行状态。</span><span class="sxs-lookup"><span data-stu-id="27875-108">The system configuration check generates a report which contains a short description for each executed rule, and the execution status.</span></span> <span data-ttu-id="27875-109">系统配置检查报告位于%programfiles%\Microsoft SQL Server\120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="27875-109">The system configuration check report is located at %programfiles%\Microsoft SQL Server\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
 <span data-ttu-id="27875-110">在执行安装操作之前，请查看以下主题：</span><span class="sxs-lookup"><span data-stu-id="27875-110">Before you run the setup operation, review the following topics:</span></span>  
  
1.  [<span data-ttu-id="27875-111">安装 SQL Server 2014 的硬件和软件要求</span><span class="sxs-lookup"><span data-stu-id="27875-111">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [<span data-ttu-id="27875-112">SQL Server 2014 各个版本支持的功能</span><span class="sxs-lookup"><span data-stu-id="27875-112">Features Supported by the Editions of SQL Server 2014</span></span>](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [<span data-ttu-id="27875-113">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="27875-113">Security Considerations for a SQL Server Installation</span></span>](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [<span data-ttu-id="27875-114">SQL Server 中的本地语言版本</span><span class="sxs-lookup"><span data-stu-id="27875-114">Local Language Versions in SQL Server</span></span>](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 <span data-ttu-id="27875-115">其他参考：</span><span class="sxs-lookup"><span data-stu-id="27875-115">Other references:</span></span>  
  
1.  [<span data-ttu-id="27875-116">支持的版本和版本升级</span><span class="sxs-lookup"><span data-stu-id="27875-116">Supported Version and Edition Upgrades</span></span>](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [<span data-ttu-id="27875-117">安装故障转移群集前的准备工作</span><span class="sxs-lookup"><span data-stu-id="27875-117">Before Installing Failover Clustering</span></span>](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a><span data-ttu-id="27875-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27875-118">See Also</span></span>  
 [<span data-ttu-id="27875-119">安装规则</span><span class="sxs-lookup"><span data-stu-id="27875-119">Install Rules</span></span>](../../../2014/sql-server/install/install-rules.md)  
  
  
