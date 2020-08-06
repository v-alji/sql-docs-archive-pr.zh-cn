---
title: SQL Server 故障转移群集安装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c0e75a7c-85c5-423c-a218-77247bf071aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d11b892bc3ae3dccfbab5bef01feca325056945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586286"
---
# <a name="sql-server-failover-cluster-installation"></a><span data-ttu-id="72968-102">SQL Server 故障转移群集安装</span><span class="sxs-lookup"><span data-stu-id="72968-102">SQL Server Failover Cluster Installation</span></span>
  <span data-ttu-id="72968-103">若要安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集，您必须通过运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序来创建并配置一个故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="72968-103">To install a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must create and configure a failover cluster instance by running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
## <a name="installing-a-failover-cluster"></a><span data-ttu-id="72968-104">安装故障转移群集</span><span class="sxs-lookup"><span data-stu-id="72968-104">Installing a Failover Cluster</span></span>  
 <span data-ttu-id="72968-105">若要安装故障转移群集，您必须使用具有本地管理员权限的域帐户，拥有作为服务登录的权限，并且拥有在故障转移群集的所有节点上作为操作系统的一部分进行操作的权限。</span><span class="sxs-lookup"><span data-stu-id="72968-105">To install a failover cluster, you must use a domain account with local administrator rights, permission to log on as a service, and to act as part of the operating system on all nodes in the failover cluster.</span></span> <span data-ttu-id="72968-106">若要通过使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序来安装故障转移群集，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="72968-106">To install a failover cluster by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program, follow these steps:</span></span>  
  
1.  <span data-ttu-id="72968-107">若要安装、配置和维护 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集，请使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="72968-107">To install, configure, and maintain a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
    -   <span data-ttu-id="72968-108">确定创建故障转移群集实例（如群集磁盘资源、IP 地址和网络名称）和可用于故障转移的节点所需的信息。</span><span class="sxs-lookup"><span data-stu-id="72968-108">Identify the information you need to create your failover cluster instance (for example, cluster disk resource, IP addresses, and network name) and the nodes available for failover.</span></span> <span data-ttu-id="72968-109">更多相关信息：</span><span class="sxs-lookup"><span data-stu-id="72968-109">For more information:</span></span>  
  
        -   [<span data-ttu-id="72968-110">安装故障转移群集前的准备工作</span><span class="sxs-lookup"><span data-stu-id="72968-110">Before Installing Failover Clustering</span></span>](before-installing-failover-clustering.md)  
  
        -   [<span data-ttu-id="72968-111">安装 SQL Server 的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="72968-111">Security Considerations for a SQL Server Installation</span></span>](../../install/security-considerations-for-a-sql-server-installation.md)  
  
    -   <span data-ttu-id="72968-112">必须在运行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序之前完成这些配置步骤，可使用 Windows 群集管理器来执行操作。必须为要配置的各个故障转移群集实例设置一个 WSFC 组。</span><span class="sxs-lookup"><span data-stu-id="72968-112">The configuration steps must take place before you run the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program; use the Windows Cluster Administrator to carry them out. You must have one WSFC group for each failover cluster instance you want to configure.</span></span>  
  
    -   <span data-ttu-id="72968-113">您必须确保您的系统满足最低要求。</span><span class="sxs-lookup"><span data-stu-id="72968-113">You must ensure that your system meets minimum requirements.</span></span> <span data-ttu-id="72968-114">有关 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集的具体要求的详细信息，请参阅 [安装故障转移群集前的准备工作](before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="72968-114">For more information on specific requirements for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, see [Before Installing Failover Clustering](before-installing-failover-clustering.md).</span></span>  
  
2.  <span data-ttu-id="72968-115">在故障转移群集配置中添加或删除节点而不影响其他群集节点。</span><span class="sxs-lookup"><span data-stu-id="72968-115">Add or remove nodes from a failover cluster configuration without affecting the other cluster nodes.</span></span> <span data-ttu-id="72968-116">有关详细信息，请参阅[在 SQL Server 故障转移群集中添加或删除节点（安装程序）](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="72968-116">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
    -   <span data-ttu-id="72968-117">故障转移群集中的所有节点都必须属于同一平台（可以是 32 位或 64 位平台），并且必须运行相同版本的操作系统。</span><span class="sxs-lookup"><span data-stu-id="72968-117">All nodes in a failover cluster must be of the same platform, either 32-bit or 64-bit, and must run the same operating system edition and version.</span></span> <span data-ttu-id="72968-118">而且，64 位 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本必须安装在运行 64 位版本的 Windows 操作系统的 64 位硬件上。</span><span class="sxs-lookup"><span data-stu-id="72968-118">Also, 64-bit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] editions must be installed on 64-bit hardware running the 64-bit versions of Windows operating systems.</span></span> <span data-ttu-id="72968-119">此版本中不对故障转移群集提供 WOW64 支持。</span><span class="sxs-lookup"><span data-stu-id="72968-119">There is no WOW64 support for failover clustering in this release.</span></span>  
  
3.  <span data-ttu-id="72968-120">为每个故障转移群集实例指定多个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="72968-120">Specify multiple IP addresses for each failover cluster instance.</span></span> <span data-ttu-id="72968-121">您可以为每个子网指定多个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="72968-121">You can specify mutiple IP addresses for each subnet.</span></span> <span data-ttu-id="72968-122">如果多个 IP 地址在同一子网上， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序会将依赖关系设置为 AND。</span><span class="sxs-lookup"><span data-stu-id="72968-122">If the mutiple IP addresses are on the same subnet, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup sets the dependency to AND.</span></span> <span data-ttu-id="72968-123">如果您正在创建跨多个子网的群集节点，则 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装程序将依赖关系设置为 OR。</span><span class="sxs-lookup"><span data-stu-id="72968-123">If you are clustering nodes across multiple subnets, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup sets the dependency to OR.</span></span>  
  
## <a name="ssnoversion-failover-cluster-installation-options"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="72968-124">故障转移群集安装选项</span><span class="sxs-lookup"><span data-stu-id="72968-124">Failover Cluster Installation options</span></span>  
  
##### <a name="option-1-integrated-installation-with-add-node"></a><span data-ttu-id="72968-125">选项 1：带“添加节点”功能的集成安装</span><span class="sxs-lookup"><span data-stu-id="72968-125">Option 1: Integrated installation with Add Node</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="72968-126">集成故障转移群集安装包括两个步骤：</span><span class="sxs-lookup"><span data-stu-id="72968-126">integrated failover cluster installation consists of two steps:</span></span>  
  
1.  <span data-ttu-id="72968-127">创建并配置单节点 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="72968-127">Create and configure a single-node [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="72968-128">在成功配置完该节点时，您将拥有一个功能齐全的故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="72968-128">At the completion of a successful configuration of the node, you have a fully functional failover cluster instance.</span></span> <span data-ttu-id="72968-129">此时，由于故障转移群集内仅有一个节点，因此它不具备高可用性。</span><span class="sxs-lookup"><span data-stu-id="72968-129">At this time it does not have high-availability because there is only one node in the failover cluster.</span></span>  
  
2.  <span data-ttu-id="72968-130">在要添加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集中的每个节点上，运行带“添加节点”功能的安装程序以添加该节点。</span><span class="sxs-lookup"><span data-stu-id="72968-130">On each node to be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, run Setup with Add Node functionality to add that node.</span></span>  
  
##### <a name="option-2-advancedenterprise-installation"></a><span data-ttu-id="72968-131">选项 2：高级/企业安装</span><span class="sxs-lookup"><span data-stu-id="72968-131">Option 2: Advanced/Enterprise installation</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="72968-132">高级/企业故障转移群集安装包括两个步骤：</span><span class="sxs-lookup"><span data-stu-id="72968-132">Advanced/Enterprise failover cluster installation consists of two steps:</span></span>  
  
1.  <span data-ttu-id="72968-133">在将要成为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集一部分的每个节点上，运行带“准备故障转移群集”功能的安装程序。</span><span class="sxs-lookup"><span data-stu-id="72968-133">On each node that will be part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, run Setup with Prepare Failover Cluster functionality.</span></span> <span data-ttu-id="72968-134">此步骤将准备好节点使其可以加入群集，但在此步骤结束时不会有可工作的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="72968-134">This step prepares the nodes ready to be clustered, but there is no operational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance at the end of this step.</span></span>  
  
2.  <span data-ttu-id="72968-135">在准备好节点以便加入群集后，使用“完成故障转移群集”功能在拥有共享磁盘的节点上运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="72968-135">After the nodes are prepared for clustering, run Setup on the node that owns the shared disk with the Complete Failover Cluster functionality.</span></span> <span data-ttu-id="72968-136">此步骤将配置并完成故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="72968-136">This step configures and completes the failover cluster instance.</span></span> <span data-ttu-id="72968-137">此步骤结束时，您将有一个可以工作的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="72968-137">At the end of this step, you will have an operational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72968-138">两种安装选项都允许多节点 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集安装。</span><span class="sxs-lookup"><span data-stu-id="72968-138">Either installation option allows for multi-node [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster installation.</span></span> <span data-ttu-id="72968-139">在创建了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集后，“添加节点”功能可用于在任一安装选项下添加更多节点。</span><span class="sxs-lookup"><span data-stu-id="72968-139">Add Node can be used to add additional nodes for either option after a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster has been created.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72968-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装位置的操作系统驱动器号在添加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集的所有节点上必须匹配。</span><span class="sxs-lookup"><span data-stu-id="72968-140">The operating system drive letter for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] install locations must match on all the nodes added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
#### <a name="ip-address-configuration-during-setup"></a><span data-ttu-id="72968-141">在安装过程中配置 IP 地址</span><span class="sxs-lookup"><span data-stu-id="72968-141">IP Address Configuration During Setup</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="72968-142">安装程序在以下操作期间允许您设置或更改 IP 资源依赖关系设置：</span><span class="sxs-lookup"><span data-stu-id="72968-142">Setup lets you set or change the IP resource dependency settings during the following actions:</span></span>  
  
-   <span data-ttu-id="72968-143">集成安装 - [创建新的 SQL Server 故障转移群集（安装程序）](create-a-new-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="72968-143">Integrated Install - [Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="72968-144">CompleteFailoverCluster（高级安装） - [创建新的 SQL Server 故障转移群集（安装程序）](create-a-new-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="72968-144">CompleteFailoverCluster (Advanced Install) - [Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="72968-145">添加节点 - [在 SQL Server 故障转移群集中添加或删除节点（安装程序）](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="72968-145">Add Node - [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="72968-146">删除节点 - [在 SQL Server 故障转移群集中添加或删除节点（安装程序）](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="72968-146">Remove Node - [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="72968-147">**注意** 支持 IPV6 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="72968-147">**Note** IPV6 IP addresses are supported.</span></span>  <span data-ttu-id="72968-148">如果您同时配置 IPV4 和 IPV6，将像对待不同的子网那样处理它们，IPV6 首先联机。</span><span class="sxs-lookup"><span data-stu-id="72968-148">If you configure both IPV4 and IPV6 there are treated like different subnets, and IPV6 is expected to come online first.</span></span>  
  
##### <a name="ssnoversion-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="72968-149">多子网故障转移群集</span><span class="sxs-lookup"><span data-stu-id="72968-149">Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="72968-150">当群集上的节点位于不同子网时，您可以设置 OR 依赖关系。</span><span class="sxs-lookup"><span data-stu-id="72968-150">You can set OR dependencies when the nodes on the cluster are on different subnets.</span></span> <span data-ttu-id="72968-151">但是， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多子网故障转移群集中的每个节点必须是至少一个指定的 IP 地址的可能所有者。</span><span class="sxs-lookup"><span data-stu-id="72968-151">However, each node in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster must be a possible owner of at least one of IP address specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72968-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72968-152">See Also</span></span>  
 <span data-ttu-id="72968-153">[安装故障转移群集之前](before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="72968-153">[Before Installing Failover Clustering](before-installing-failover-clustering.md) </span></span>  
 <span data-ttu-id="72968-154">[创建新的 SQL Server 故障转移群集（安装程序）](create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="72968-154">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="72968-155">[从命令提示符安装 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="72968-155">[Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="72968-156">升级 SQL Server 故障转移群集</span><span class="sxs-lookup"><span data-stu-id="72968-156">Upgrade a SQL Server Failover Cluster</span></span>](../windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
