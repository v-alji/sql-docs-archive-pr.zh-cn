---
title: 从故障转移群集实例故障中恢复 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60db4c2e480b094c18d0a8071e947a38cdc779d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693214"
---
# <a name="recover-from-failover-cluster-instance-failure"></a><span data-ttu-id="f22a9-102">从故障转移群集实例故障中恢复</span><span class="sxs-lookup"><span data-stu-id="f22a9-102">Recover from Failover Cluster Instance Failure</span></span>
  <span data-ttu-id="f22a9-103">本主题说明在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中发生故障转移后如何使用故障转移群集管理器管理单元从群集故障中恢复。</span><span class="sxs-lookup"><span data-stu-id="f22a9-103">This topic describes how to recover from cluster failures by using the Failover Cluster Manager snap-in after a failover occurs in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="f22a9-104">故障转移群集管理器管理单元是用于 Windows Server 故障转移群集 (WSFC) 服务的群集管理应用程序。</span><span class="sxs-lookup"><span data-stu-id="f22a9-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Serer Failover Clustering (WSFC) service.</span></span>  
  
-   [<span data-ttu-id="f22a9-105">从无法修复的故障中恢复</span><span class="sxs-lookup"><span data-stu-id="f22a9-105">Recover from an irreparable failure</span></span>](#Scenario1)  
  
-   [<span data-ttu-id="f22a9-106">从软件故障中恢复</span><span class="sxs-lookup"><span data-stu-id="f22a9-106">Recover from a software failure</span></span>](#Scenario2)  
  
##  <a name="recover-from-an-irreparable-failure"></a><a name="Scenario1"></a> <span data-ttu-id="f22a9-107">从无法修复的故障中恢复</span><span class="sxs-lookup"><span data-stu-id="f22a9-107">Recover from an irreparable failure</span></span>  
 <span data-ttu-id="f22a9-108">使用以下步骤从无法修复的故障中恢复。</span><span class="sxs-lookup"><span data-stu-id="f22a9-108">Use the following steps to recover from an irreparable failure.</span></span> <span data-ttu-id="f22a9-109">例如，该故障可能是由磁盘控制器或操作系统的故障引起的。</span><span class="sxs-lookup"><span data-stu-id="f22a9-109">The failure could be caused, for example, by the failure of a disk controller or the operating system.</span></span> <span data-ttu-id="f22a9-110">在此情况中，故障是由两节点的群集中节点 1 的硬件故障造成的。</span><span class="sxs-lookup"><span data-stu-id="f22a9-110">In this case, failure is caused by hardware failure in Node 1 of a two-node cluster.</span></span>  
  
1.  <span data-ttu-id="f22a9-111">节点 1 失败后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI 故障转移到节点 2。</span><span class="sxs-lookup"><span data-stu-id="f22a9-111">After Node 1 fails, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="f22a9-112">从 FCI 中逐出节点 1。</span><span class="sxs-lookup"><span data-stu-id="f22a9-112">Evict Node 1 from the FCI.</span></span> <span data-ttu-id="f22a9-113">为此，从节点 2 打开“故障转移群集管理”器管理单元，右键单击节点 1，单击“移动操作”\*\*\*\*，然后单击“逐出节点”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f22a9-113">To do this, from Node 2, open the Failover Cluster Manager snap-in, right-click Node1, click **Move Actions**, and then click **Evict Node**.</span></span>  
  
3.  <span data-ttu-id="f22a9-114">验证节点 1 是否已从群集定义中逐出。</span><span class="sxs-lookup"><span data-stu-id="f22a9-114">Verify that Node 1 has been evicted from the cluster definition.</span></span>  
  
4.  <span data-ttu-id="f22a9-115">安装新的硬件，以替换节点 1 中发生故障的硬件。</span><span class="sxs-lookup"><span data-stu-id="f22a9-115">Install new hardware to replace the failed hardware in Node 1.</span></span>  
  
5.  <span data-ttu-id="f22a9-116">使用故障转移群集管理器管理单元将节点 1 添加到现有群集。</span><span class="sxs-lookup"><span data-stu-id="f22a9-116">Using the Failover Cluster Manager snap-in, add Node 1 to the existing cluster.</span></span> <span data-ttu-id="f22a9-117">有关详细信息，请参阅 [安装故障转移群集前的准备工作](../install/before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="f22a9-117">For more information, see [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
6.  <span data-ttu-id="f22a9-118">确保所有群集节点上的管理员帐户都相同。</span><span class="sxs-lookup"><span data-stu-id="f22a9-118">Ensure that the administrator accounts are the same on all cluster nodes.</span></span>  
  
7.  <span data-ttu-id="f22a9-119">运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序以将节点 1 添加到 FCI。</span><span class="sxs-lookup"><span data-stu-id="f22a9-119">Run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to add Node 1 to the FCI.</span></span> <span data-ttu-id="f22a9-120">有关详细信息，请参阅[在 SQL Server 故障转移群集中添加或删除节点 &#40;安装程序&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="f22a9-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
##  <a name="recover-from-a-reparable-failure"></a><a name="Scenario2"></a> <span data-ttu-id="f22a9-121">从可修复的故障中恢复</span><span class="sxs-lookup"><span data-stu-id="f22a9-121">Recover from a reparable failure</span></span>  
 <span data-ttu-id="f22a9-122">使用以下步骤从可修复的故障中恢复。</span><span class="sxs-lookup"><span data-stu-id="f22a9-122">Us the following steps to recover from a reparable failure.</span></span> <span data-ttu-id="f22a9-123">在此情况中，故障由节点 1 关闭或脱机引起，但并非无法挽回。</span><span class="sxs-lookup"><span data-stu-id="f22a9-123">In this case, failure is caused by Node 1 being down or offline but not irretrievably broken.</span></span> <span data-ttu-id="f22a9-124">这可能由操作系统故障、硬件故障或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例本身的故障引起。</span><span class="sxs-lookup"><span data-stu-id="f22a9-124">This could be caused by an operating system failure, hardware failure, or failure in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance itself.</span></span>  
  
1.  <span data-ttu-id="f22a9-125">节点 1 失败后，FCI 故障转移到节点 2。</span><span class="sxs-lookup"><span data-stu-id="f22a9-125">After Node 1 fails, the FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="f22a9-126">解决节点 1 的问题。</span><span class="sxs-lookup"><span data-stu-id="f22a9-126">Resolve the problem with Node 1.</span></span>  
  
3.  <span data-ttu-id="f22a9-127">确保所有节点处于联机状态且 WSFC 服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="f22a9-127">Ensure that all nodes are online and the WSFC service is working.</span></span>  
  
4.  <span data-ttu-id="f22a9-128">将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移到恢复的节点。</span><span class="sxs-lookup"><span data-stu-id="f22a9-128">Fail over [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the recovered node.</span></span>  
  
  
