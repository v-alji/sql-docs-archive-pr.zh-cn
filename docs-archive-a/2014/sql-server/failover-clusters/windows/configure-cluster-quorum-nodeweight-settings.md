---
title: 配置群集仲裁 NodeWeight 设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e469d5fc0fc030304a7cf2f1bdd894eb578aa056
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586270"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="aed48-102">配置群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="aed48-102">Configure Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="aed48-103">本主题说明如何配置 Windows Server 故障转移群集 (WSFC) 群集中成员节点的 NodeWeight 设置。</span><span class="sxs-lookup"><span data-stu-id="aed48-103">This topic describes how to configure NodeWeight settings for a member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="aed48-104">在仲裁投票期间，使用 NodeWeight 设置来支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例的灾难恢复和多子网方案。</span><span class="sxs-lookup"><span data-stu-id="aed48-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="aed48-105">**开始之前：** [先决条件](#Prerequisites)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="aed48-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="aed48-106">**若要查看仲裁 NodeWeight 设置，请使用：** [使用 PowerShell](#PowerShellProcedure)、[使用 Cluster.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="aed48-106">**To view quorum NodeWeight settings using:** [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
-   [<span data-ttu-id="aed48-107">相关内容</span><span class="sxs-lookup"><span data-stu-id="aed48-107">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="aed48-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="aed48-108">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="aed48-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="aed48-109">Prerequisites</span></span>  
 <span data-ttu-id="aed48-110">仅在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 或更高版本中支持此功能。</span><span class="sxs-lookup"><span data-stu-id="aed48-110">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aed48-111">为了使用 NodeWeight 设置，必须将以下修补程序应用到 WSFC 群集中的所有服务器：</span><span class="sxs-lookup"><span data-stu-id="aed48-111">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="aed48-112">[KB2494036](https://support.microsoft.com/kb/2494036)：该修补程序用于配置在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 中没有仲裁投票的群集节点</span><span class="sxs-lookup"><span data-stu-id="aed48-112">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="aed48-113">如果未安装此修补程序，本主题中的示例将为 NodeWeight 返回空或 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="aed48-113">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="aed48-114">Security</span><span class="sxs-lookup"><span data-stu-id="aed48-114">Security</span></span>  
 <span data-ttu-id="aed48-115">用户必须是一个域帐户，该帐户是每个 WSFC 群集节点上本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="aed48-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="aed48-116">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aed48-116">Using Powershell</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="aed48-117">配置 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="aed48-117">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="aed48-118">通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="aed48-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="aed48-119">导入 `FailoverClusters` 模块以启用群集 commandlet。</span><span class="sxs-lookup"><span data-stu-id="aed48-119">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="aed48-120">使用 `Get-ClusterNode` 对象以设置群集中每个节点的 `NodeWeight` 属性。</span><span class="sxs-lookup"><span data-stu-id="aed48-120">Use the `Get-ClusterNode` object to set the `NodeWeight` property for each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="aed48-121">以可读格式输出群集节点属性。</span><span class="sxs-lookup"><span data-stu-id="aed48-121">Output the cluster node properties in a readable format.</span></span>  
  
 <span data-ttu-id="aed48-122">下面的示例更改 NodeWeight 设置以删除“AlwaysOnSrv1”节点的仲裁投票，然后输出群集中所有节点的设置。</span><span class="sxs-lookup"><span data-stu-id="aed48-122">The following example changes the NodeWeight setting to remove the quorum vote for the "AlwaysOnSrv1" node, and then outputs the settings for all nodes in the cluster.</span></span>
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a><span data-ttu-id="aed48-123">使用 Cluster.exe</span><span class="sxs-lookup"><span data-stu-id="aed48-123">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aed48-124">在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 版本中不推荐使用 cluster.exe 实用工具。</span><span class="sxs-lookup"><span data-stu-id="aed48-124">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="aed48-125">在将来的开发工作中，请将 PowerShell 与故障转移群集结合使用。</span><span class="sxs-lookup"><span data-stu-id="aed48-125">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="aed48-126">在 Windows Server 的下一版本中，将删除 cluster.exe 实用工具。</span><span class="sxs-lookup"><span data-stu-id="aed48-126">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="aed48-127">有关详细信息，请参阅 [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)（为故障转移群集将 cluster.exe 命令映射到 Windows PowerShell Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="aed48-127">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="aed48-128">配置 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="aed48-128">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="aed48-129">通过 **“以管理员身份运行”** 启动提升的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="aed48-129">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="aed48-130">使用 **cluster.exe** 以设置 `NodeWeight` 值。</span><span class="sxs-lookup"><span data-stu-id="aed48-130">Use **cluster.exe** to set `NodeWeight` values.</span></span>  

 <span data-ttu-id="aed48-131">下面的示例更改 NodeWeight 值以删除“Cluster001”群集中“AlwaysOnSrv1”节点的仲裁投票。</span><span class="sxs-lookup"><span data-stu-id="aed48-131">The following example changes the NodeWeight value to remove the quorum vote of the "AlwaysOnSrv1" node in the "Cluster001" cluster.</span></span>  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="aed48-132">相关内容</span><span class="sxs-lookup"><span data-stu-id="aed48-132">Related Content</span></span>  
  
-   <span data-ttu-id="aed48-133">[查看故障转移群集的事件和日志](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aed48-133">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="aed48-134">Get-ClusterLog 故障转移群集 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aed48-134">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="aed48-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aed48-135">See Also</span></span>  
 <span data-ttu-id="aed48-136">[WSFC 仲裁模式和投票配置 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="aed48-136">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="aed48-137">[查看群集仲裁 NodeWeight 设置](view-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="aed48-137">[View Cluster Quorum NodeWeight Settings](view-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="aed48-138">[Windows PowerShell 中按任务焦点列出的故障转移群集 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="aed48-138">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
