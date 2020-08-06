---
title: 群集节点配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster node configuration
- cluster node configuration, Setup
ms.assetid: cc960cf3-3b55-44f3-961a-eac4ad05d3d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e6bf33bce3eb08994e0bd5529394e033673827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586193"
---
# <a name="cluster-node-configuration"></a><span data-ttu-id="27193-102">群集节点配置</span><span class="sxs-lookup"><span data-stu-id="27193-102">Cluster Node Configuration</span></span>
  <span data-ttu-id="27193-103">使用“群集节点配置”页可以在故障转移群集实例中添加或删除节点。若要安装或升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集，必须在故障转移群集的每个节点上运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="27193-103">Use the Cluster Node Configuration page to add or remove nodes from a failover cluster instance.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="27193-104">若要向现有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集添加节点，则必须在要添加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例的节点上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="27193-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27193-105">选项</span><span class="sxs-lookup"><span data-stu-id="27193-105">Options</span></span>  
 <span data-ttu-id="27193-106">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称\*\*-使用下拉列表选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要修改的故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="27193-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance Name** - Use the drop-down list to select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance to modify.</span></span>  
  
 <span data-ttu-id="27193-107">**此节点的名称** - 将使用运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序的计算机名称填充此字段。</span><span class="sxs-lookup"><span data-stu-id="27193-107">**Name of this node** - This field will be populated with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="27193-108">这就是将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例中添加或删除的故障转移群集节点。</span><span class="sxs-lookup"><span data-stu-id="27193-108">This is the failover cluster node that will be added to or removed from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
  
