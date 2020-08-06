---
title: 群集节点配置 (完成) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cc1f8ce4574580746e20c478b23e40485c3e6ecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586200"
---
# <a name="cluster-node-configuration-complete"></a><span data-ttu-id="e927f-102">群集节点配置(完成)</span><span class="sxs-lookup"><span data-stu-id="e927f-102">Cluster Node Configuration (Complete)</span></span>
  <span data-ttu-id="e927f-103">使用“群集节点配置(完成)”页可以指定已准备好建立群集的现有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。若要安装或升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集，必须在故障转移群集的每个节点上运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="e927f-103">Use the Cluster Node Configuration (Complete) page to specify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that has been prepared for clustering.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="e927f-104">若要向现有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集添加节点，则必须在要添加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例的节点上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序。</span><span class="sxs-lookup"><span data-stu-id="e927f-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e927f-105">选项</span><span class="sxs-lookup"><span data-stu-id="e927f-105">Options</span></span>  
 <span data-ttu-id="e927f-106">下拉框中有以下选项：</span><span class="sxs-lookup"><span data-stu-id="e927f-106">From the drop-down boxes:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e927f-107">实例名称-选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集的实例名称。</span><span class="sxs-lookup"><span data-stu-id="e927f-107">instance name - Select the instance name for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="e927f-108">此节点的名称-此字段预填充了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行安装程序的计算机名称。</span><span class="sxs-lookup"><span data-stu-id="e927f-108">Name of this node - This field is pre-populated with the computer name where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e927f-109">故障转移群集网络名称-未预填充此字段。</span><span class="sxs-lookup"><span data-stu-id="e927f-109">Failover Cluster Network Name - This field is not pre-populated.</span></span> <span data-ttu-id="e927f-110">为新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例指定网络名称，</span><span class="sxs-lookup"><span data-stu-id="e927f-110">Specify the network name for the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="e927f-111">该名称用来在网络上标识故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="e927f-111">This is the name that identifies the failover cluster instance on the network.</span></span>  
  
  
