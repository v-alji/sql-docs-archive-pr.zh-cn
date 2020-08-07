---
title: 查看群集仲裁 NodeWeight 设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef2176d4916e8affbb9ef89c9b26499289c520ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586255"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="7ee87-102">查看群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="7ee87-102">View Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="7ee87-103">本主题说明如何查看 Windows Server 故障转移群集 (WSFC) 群集中每个成员节点的 NodeWeight 设置。</span><span class="sxs-lookup"><span data-stu-id="7ee87-103">This topic describes how to view NodeWeight settings for each member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="7ee87-104">在仲裁投票期间，使用 NodeWeight 设置来支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例的灾难恢复和多子网方案。</span><span class="sxs-lookup"><span data-stu-id="7ee87-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="7ee87-105">**开始之前：** [先决条件](#Prerequisites)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="7ee87-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="7ee87-106">**若要查看仲裁 NodeWeight 设置，请使用：** [使用 Transact-SQL](#TsqlProcedure)、[使用 Powershell](#PowerShellProcedure)、[使用 Cluster.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="7ee87-106">**To view quorum NodeWeight settings using:** [Using Transact-SQL](#TsqlProcedure), [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7ee87-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="7ee87-107">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="7ee87-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="7ee87-108">Prerequisites</span></span>  
 <span data-ttu-id="7ee87-109">仅在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 或更高版本中支持此功能。</span><span class="sxs-lookup"><span data-stu-id="7ee87-109">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ee87-110">为了使用 NodeWeight 设置，必须将以下修补程序应用到 WSFC 群集中的所有服务器：</span><span class="sxs-lookup"><span data-stu-id="7ee87-110">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="7ee87-111">[KB2494036](https://support.microsoft.com/kb/2494036)：该修补程序用于配置在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 中没有仲裁投票的群集节点</span><span class="sxs-lookup"><span data-stu-id="7ee87-111">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7ee87-112">如果未安装此修补程序，本主题中的示例将为 NodeWeight 返回空或 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="7ee87-112">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7ee87-113">Security</span><span class="sxs-lookup"><span data-stu-id="7ee87-113">Security</span></span>  
 <span data-ttu-id="7ee87-114">用户必须是一个域帐户，该帐户是每个 WSFC 群集节点上本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="7ee87-114">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7ee87-115">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7ee87-115">Using Transact-SQL</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7ee87-116">查看 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="7ee87-116">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="7ee87-117">连接到群集中的任意 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="7ee87-117">Connect to any [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the cluster.</span></span>  
  
2.  <span data-ttu-id="7ee87-118">查询 [sys].[dm_hadr_cluster_members] 视图。</span><span class="sxs-lookup"><span data-stu-id="7ee87-118">Query the [sys].[dm_hadr_cluster_members] view.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="7ee87-119">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7ee87-119">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="7ee87-120">以下示例查询一个系统视图以返回该实例的群集中所有节点的值。</span><span class="sxs-lookup"><span data-stu-id="7ee87-120">The following example queries a system view to return values for all of the nodes in that instance's cluster.</span></span>  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="7ee87-121">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7ee87-121">Using Powershell</span></span>  
  
### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7ee87-122">查看 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="7ee87-122">To view NodeWeight settings</span></span>
  
1.  <span data-ttu-id="7ee87-123">通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7ee87-123">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="7ee87-124">导入 `FailoverClusters` 模块以启用群集 commandlet。</span><span class="sxs-lookup"><span data-stu-id="7ee87-124">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="7ee87-125">使用 `Get-ClusterNode` 对象以返回群集节点对象的集合。</span><span class="sxs-lookup"><span data-stu-id="7ee87-125">Use the `Get-ClusterNode` object to return a collection of cluster node objects.</span></span>  
  
4.  <span data-ttu-id="7ee87-126">以可读格式输出群集节点属性。</span><span class="sxs-lookup"><span data-stu-id="7ee87-126">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="7ee87-127">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="7ee87-127">Example (Powershell)</span></span>  
 <span data-ttu-id="7ee87-128">以下示例为名为“Cluster001”的群集输出一些节点属性。</span><span class="sxs-lookup"><span data-stu-id="7ee87-128">The following example output some of the node properties for the cluster called "Cluster001".</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="7ee87-129">使用 cluster.exe</span><span class="sxs-lookup"><span data-stu-id="7ee87-129">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ee87-130">在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 版本中不推荐使用 cluster.exe 实用工具。</span><span class="sxs-lookup"><span data-stu-id="7ee87-130">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="7ee87-131">在将来的开发工作中，请将 PowerShell 与故障转移群集结合使用。</span><span class="sxs-lookup"><span data-stu-id="7ee87-131">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="7ee87-132">在 Windows Server 的下一版本中，将删除 cluster.exe 实用工具。</span><span class="sxs-lookup"><span data-stu-id="7ee87-132">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="7ee87-133">有关详细信息，请参阅 [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)（为故障转移群集将 cluster.exe 命令映射到 Windows PowerShell Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="7ee87-133">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="7ee87-134">查看 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="7ee87-134">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="7ee87-135">通过 **“以管理员身份运行”** 启动提升的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="7ee87-135">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="7ee87-136">使用 **cluster.exe** 以返回节点状态和 NodeWeight 值</span><span class="sxs-lookup"><span data-stu-id="7ee87-136">Use **cluster.exe** to return node status and NodeWeight values</span></span>  
  
### <a name="example-clusterexe"></a><span data-ttu-id="7ee87-137">示例 (Cluster.exe)</span><span class="sxs-lookup"><span data-stu-id="7ee87-137">Example (Cluster.exe)</span></span>  
 <span data-ttu-id="7ee87-138">以下示例为名为“Cluster001”的群集输出一些节点属性。</span><span class="sxs-lookup"><span data-stu-id="7ee87-138">The following example outputs some of the node properties for the cluster called "Cluster001".</span></span>  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee87-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ee87-139">See Also</span></span>  
 <span data-ttu-id="7ee87-140">[WSFC 仲裁模式和投票配置 (SQL Server)](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7ee87-140">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="7ee87-141">[配置群集仲裁 NodeWeight 设置](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7ee87-141">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="7ee87-142">[sys.dm_hadr_cluster_members (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7ee87-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span></span>  
 <span data-ttu-id="7ee87-143">[Windows PowerShell 中按任务焦点列出的故障转移群集 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7ee87-143">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
