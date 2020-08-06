---
title: 高可用性支持 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3075b300061b3d87b12a7cb3c4363b5e218f34d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683020"
---
# <a name="high-availability-support"></a><span data-ttu-id="2c37a-102">高可用性支持</span><span class="sxs-lookup"><span data-stu-id="2c37a-102">High Availability Support</span></span>
  <span data-ttu-id="2c37a-103">Oracle CDC 服务是为高可用性而设计的。</span><span class="sxs-lookup"><span data-stu-id="2c37a-103">The CDC Service for Oracle is designed for high availability.</span></span> <span data-ttu-id="2c37a-104">下列功能为高可用性支持助一臂之力：</span><span class="sxs-lookup"><span data-stu-id="2c37a-104">The following features provide part of the high availability support:</span></span>  
  
-   <span data-ttu-id="2c37a-105">Oracle CDC 服务不占用任何文件资源（本地资源或其他资源）。</span><span class="sxs-lookup"><span data-stu-id="2c37a-105">The CDC Service for Oracle does not use any file resource (local or otherwise).</span></span> <span data-ttu-id="2c37a-106">其整个状态都存储于目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中。</span><span class="sxs-lookup"><span data-stu-id="2c37a-106">Its entire state is stored in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="2c37a-107">因此，如果运行该服务的计算机失败，可以轻松地在使用相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的其他计算机上启动该服务。</span><span class="sxs-lookup"><span data-stu-id="2c37a-107">This makes it easy to start the service on a different computer that uses the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance if the computer the service runs on fails.</span></span> <span data-ttu-id="2c37a-108">为了缩短恢复时间，长的或长时间运行的 Oracle 事务保存在目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的临时表中，从而无需在失败（或服务重新启动）后重新扫描许多 Oracle 事务日志。</span><span class="sxs-lookup"><span data-stu-id="2c37a-108">To reduce recovery time, long or long-running Oracle transactions are kept in a staging table in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], preventing the need to re-scan many Oracle transaction logs following a failure (or service restart).</span></span>  
  
-   <span data-ttu-id="2c37a-109">Oracle CDC 服务可以使用群集的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，因此，它可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例故障转移到其他群集节点后恢复。</span><span class="sxs-lookup"><span data-stu-id="2c37a-109">The CDC Service for Oracle can use clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances so it can recover after the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance fails over to another cluster node.</span></span> <span data-ttu-id="2c37a-110">Oracle CDC 服务计算机管理员仅需在创建 Oracle CDC 服务时指定与群集的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接信息。</span><span class="sxs-lookup"><span data-stu-id="2c37a-110">The Oracle CDC Service Computer Administrator only needs to specify the connection information to the clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance when creating an Oracle CDC Service.</span></span>  
  
-   <span data-ttu-id="2c37a-111">Oracle CDC 服务可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **AlwaysOn**数据库镜像功能。</span><span class="sxs-lookup"><span data-stu-id="2c37a-111">The CDC Service for Oracle can use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** database mirroring feature.</span></span> <span data-ttu-id="2c37a-112">此支持要求 MSXDBCDC 和所有 CDC 数据库都位于同一个可用性组中。</span><span class="sxs-lookup"><span data-stu-id="2c37a-112">This support requires that the MSXDBCDC and all the CDC databases are in the same availability group.</span></span> <span data-ttu-id="2c37a-113">它还要求 Oracle CDC 服务计算机管理员为可用性组指定适当的**AlwaysOn**连接信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (例如，连接属性 `Failover_Partner and Network=dbmssocn`) 。</span><span class="sxs-lookup"><span data-stu-id="2c37a-113">It also requires the Oracle CDC Service Computer Administrator to specify the appropriate **AlwaysOn** connection information to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] availability group (for example, the connection properties `Failover_Partner and Network=dbmssocn`).</span></span> <span data-ttu-id="2c37a-114">这允许 CDC 服务在故障转移后自动恢复在数据库的辅助副本上的处理。</span><span class="sxs-lookup"><span data-stu-id="2c37a-114">This allows the CDC service to automatically resume processing on a secondary replication of the databases following a failover.</span></span>  
  
-   <span data-ttu-id="2c37a-115">Oracle CDC 服务可以配置为 Windows 故障转移群集上的一般服务资源（可与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一起也可以独立于后者），从而可以轻松地故障转移和回退针对群集的 CDC 处理。</span><span class="sxs-lookup"><span data-stu-id="2c37a-115">The CDC Service for Oracle can be configured as a generic service resource on a Windows failover cluster (along with, or separate from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), making it simple to fail over and fall back CDC processing with the cluster.</span></span> <span data-ttu-id="2c37a-116">若要将某一 Oracle CDC 服务配置为某个故障转移群集中的资源，系统管理员必须将该 Oracle CDC 服务配置为该故障转移群集上各节点的一般服务资源。</span><span class="sxs-lookup"><span data-stu-id="2c37a-116">To configure the CDC Service for Oracle as a resource in a failover cluster, the system administrator must set the CDC Service for Oracle as a Generic Service Resource on each node on the failover cluster.</span></span>  
  
-   <span data-ttu-id="2c37a-117">Oracle CDC 服务支持 Oracle RAC，这允许其与 Oracle 数据库进行通信并且甚至在某一 Oracle RAC 节点停机时处理日志。</span><span class="sxs-lookup"><span data-stu-id="2c37a-117">The CDC Service for Oracle supports Oracle RAC, which allows it to communicate with the Oracle database and process logs even when one of the Oracle RAC nodes is down.</span></span>  
  
  
