---
title: 升级 SQL Server 故障转移群集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca08e83c362e714f234a60ee358df3bcb03ade93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586257"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a><span data-ttu-id="b2ae4-102">升级 SQL Server 故障转移群集</span><span class="sxs-lookup"><span data-stu-id="b2ae4-102">Upgrade a SQL Server Failover Cluster</span></span>
  <span data-ttu-id="b2ae4-103">在所有故障转移群集节点上，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 都支持[!INCLUDE[ssDE](../../../includes/ssde-md.md)]和 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 分别从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]  故障转移群集升级。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports upgrade of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all failover cluster nodes.</span></span>  
  
 <span data-ttu-id="b2ae4-104">支持详细信息如下所示：</span><span class="sxs-lookup"><span data-stu-id="b2ae4-104">Support details are as follows:</span></span>  
  
-   <span data-ttu-id="b2ae4-105">既支持通过用户界面进行升级，也支持从命令提示符进行升级。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-105">Upgrade is supported both through the user interface and from the command prompt.</span></span> <span data-ttu-id="b2ae4-106">有关详细信息，请参阅[升级 SQL Server 故障转移群集实例（安装程序）](upgrade-a-sql-server-failover-cluster-instance-setup.md)和[从命令提示符安装 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-106">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) and [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
-   <span data-ttu-id="b2ae4-107">从升级 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -可以从命令提示符在每个故障转移群集节点上运行升级，也可以使用安装程序 UI 来升级每个群集节点。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-107">Upgrading from [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] - You can run upgrade from the command prompt on each failover cluster node, or by using the Setup UI to upgrade each cluster node.</span></span> <span data-ttu-id="b2ae4-108">如果要升级的实例上不存在全文搜索和复制功能，则会自动安装它们，而不能选择忽略它们。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-108">If Full-text search and Replication features do not exist on the instance being upgraded, they will be installed automatically with no option to omit them.</span></span>  
  
-   <span data-ttu-id="b2ae4-109">Service Pack 安装 – 必须将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 和修补程序分别应用于所有节点上的 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-109">Service pack installation - you must apply [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service packs and patches to [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all nodes.</span></span>  
  
-   <span data-ttu-id="b2ae4-110">不支持以下方案：</span><span class="sxs-lookup"><span data-stu-id="b2ae4-110">The following scenarios are not supported:</span></span>  
  
    -   <span data-ttu-id="b2ae4-111">不能从独立的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例迁移到故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-111">You cannot migrate from a stand-alone instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to a failover cluster.</span></span>  
  
    -   <span data-ttu-id="b2ae4-112">向故障转移群集中添加功能。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-112">Add features to a failover cluster.</span></span> <span data-ttu-id="b2ae4-113">例如，不能向现在仅 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的故障转移群集中添加 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-113">For example, you cannot add the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to an existing [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-only failover cluster.</span></span>  
  
    -   <span data-ttu-id="b2ae4-114">不能将故障转移群集节点降级为独立的实例。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-114">You cannot downgrade a failover cluster node to a stand-alone instance.</span></span>  
  
-   <span data-ttu-id="b2ae4-115">有关详细信息，请参阅 [AlwaysOn 故障转移群集实例 (SQL Server)](always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-115">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="upgrading-a-ssnoversion-multi-subnet-failover-cluster"></a><span data-ttu-id="b2ae4-116">升级 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多子网故障转移群集</span><span class="sxs-lookup"><span data-stu-id="b2ae4-116">Upgrading a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="b2ae4-117">不能直接将非多子网 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集升级到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多子网故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-117">You cannot directly upgrade a non-multi-subnet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster.</span></span> <span data-ttu-id="b2ae4-118">有关详细信息，请参阅[升级 SQL Server 故障转移群集实例（安装程序）](upgrade-a-sql-server-failover-cluster-instance-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ae4-118">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ae4-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2ae4-119">See Also</span></span>  
 <span data-ttu-id="b2ae4-120">[支持的版本升级](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="b2ae4-120">[Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="b2ae4-121">[&#40;安装程序升级 SQL Server 故障转移群集实例&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="b2ae4-121">[Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="b2ae4-122">Install SQL Server 2014 from the Command Prompt</span><span class="sxs-lookup"><span data-stu-id="b2ae4-122">Install SQL Server 2014 from the Command Prompt</span></span>](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
