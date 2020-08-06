---
title: 群集网络配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 17ab563817a3b9b476dfd566f4a7f2beda98ca26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586198"
---
# <a name="cluster-network-configuration"></a><span data-ttu-id="3fdc0-102">群集网络配置</span><span class="sxs-lookup"><span data-stu-id="3fdc0-102">Cluster Network Configuration</span></span>
  <span data-ttu-id="3fdc0-103">使用 **“群集网络选择”** 页可为故障转移群集实例指定网络资源。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-103">Use the **Cluster Network Selection** page to specify the network resources for your failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3fdc0-104">选项</span><span class="sxs-lookup"><span data-stu-id="3fdc0-104">Options</span></span>  
 <span data-ttu-id="3fdc0-105">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集网络名称\*\*-这是用于在网络上标识故障转移群集实例的名称。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-105">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Network Name** - This is the name used to identify your failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="3fdc0-106">**网络设置** - 指定故障转移群集实例的 IP 类型和 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-106">**Network Settings** - Specify the IP type and IP address for your failover cluster instance.</span></span>  
  
 <span data-ttu-id="3fdc0-107">在“添加节点”和“删除节点”操作期间， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集的现有 IP 地址的只读列表。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-107">During the Add Node and Remove Node operations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a read-only list of the existing IP addresses for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="3fdc0-108">集成安装：</span><span class="sxs-lookup"><span data-stu-id="3fdc0-108">Integrated Install:</span></span>  
  
    -   <span data-ttu-id="3fdc0-109">如果您要添加一个节点，此节点支持由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集的现有节点支持的同一组网络子网，则不能添加其他 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-109">If you are adding a node that supports an identical set of network subnets supported by the existing nodes of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP addresses can be added.</span></span> <span data-ttu-id="3fdc0-110">依赖关系设置保持不变。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-110">The dependency setting remains unchanged.</span></span>  
  
    -   <span data-ttu-id="3fdc0-111">如果您要添加一个节点，此节点支持由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集上的现有节点支持的子网的一个子集，则不能添加其他 IP 地址资源。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-111">If you are adding a node that supports a subset of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP address resources can be added.</span></span> <span data-ttu-id="3fdc0-112">IP 地址资源依赖关系设置为 OR，以反映指定的所有 IP 地址并非在所有群集节点上都有效。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-112">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="3fdc0-113">如果您要添加一个节点，此节点除了支持由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集中的现有节点已经支持的子网之外，还支持其他子网，则您可以选择添加新的有效 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-113">If you are adding a node that supports subnets in addition to the subnets already supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you have the option of adding new valid IP addresses.</span></span> <span data-ttu-id="3fdc0-114">如果指定了新的 IP 地址，则 IP 地址资源依赖关系设置为 OR，以反映指定的所有 IP 地址并非在所有群集节点上都有效。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-114">If new IP addresses are specified, the IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="3fdc0-115">如果您要添加一个节点，此节点支持其他网络子网，但不支持由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集中的现有节点支持的子网，则您需要添加其他 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-115">If you are adding a node that supports additional network subnets, but supports none of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are required to add additional IP addresses.</span></span> <span data-ttu-id="3fdc0-116">IP 地址资源依赖关系设置为 OR，以反映指定的所有 IP 地址并非在所有群集节点上都有效。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-116">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
-   <span data-ttu-id="3fdc0-117">高级安装：在安装过程的“完成”步骤中，为故障转移群集实例的所有节点和子网指定 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-117">Advanced Install: During the Complete step of the installation, specify the IP address for all the nodes and subnets for your failover cluster instance.</span></span> <span data-ttu-id="3fdc0-118">您可以为一个多子网故障转移群集指定多个 IP 地址，但每个子网只支持一个 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-118">You can specify multiple IP addresses for a multi-subnet failover cluster, but only one IP address per subnet is supported.</span></span> <span data-ttu-id="3fdc0-119">准备好的每个节点应至少是一个 IP 地址的所有者。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-119">Every prepared node should be an owner of at least one IP address.</span></span> <span data-ttu-id="3fdc0-120">如果您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集中有多个子网，系统将提示您将 IP 地址资源依赖关系设置为 OR。删除节点：</span><span class="sxs-lookup"><span data-stu-id="3fdc0-120">If you have multiple subnets in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are prompted to set the IP address resource dependency to OR.Remove Node:</span></span>  
  
    -   <span data-ttu-id="3fdc0-121">如果在所有剩余节点上都支持剩下的 IP 地址，系统会提示您将 IP 地址资源依赖关系设置为 AND。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-121">If the remaining IP addresses are supported on all the remaining nodes, you are prompted to set the IP address resource dependencyto AND.</span></span>  
  
    -   <span data-ttu-id="3fdc0-122">如果并非在所有剩余节点上都支持剩下的 IP 地址，则 IP 地址资源依赖关系保留为 OR。</span><span class="sxs-lookup"><span data-stu-id="3fdc0-122">If the remaining IP addresses are not supported on all the remaining nodes, the IP address resource dependency is left as OR.</span></span>  
  
  
