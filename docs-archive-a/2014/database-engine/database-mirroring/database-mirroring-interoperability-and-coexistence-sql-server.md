---
title: 数据库镜像：互操作性和共存 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], interoperability and coexistence
- Database Engine [SQL Server], high availability
ms.assetid: 89fef397-e0cf-4e08-b598-25b8d4170523
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 057392842974c3342fc57d0ec113f8b1bb58b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580882"
---
# <a name="database-mirroring-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="9975e-102">数据库镜像：互操作性和共存 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9975e-102">Database Mirroring: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="9975e-103">数据库镜像可以与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的下列功能或组件一起使用：</span><span class="sxs-lookup"><span data-stu-id="9975e-103">Database mirroring can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="9975e-104">AlwaysOn 故障转移群集实例（SQL Server 故障转移群集）</span><span class="sxs-lookup"><span data-stu-id="9975e-104">AlwaysOn Failover Cluster Instances (SQL Server Failover Clustering)</span></span>](database-mirroring-and-sql-server-failover-cluster-instances.md)  
  
-   [<span data-ttu-id="9975e-105">变更数据捕获（和更改跟踪）</span><span class="sxs-lookup"><span data-stu-id="9975e-105">Change data capture (and change tracking)</span></span>](../../relational-databases/track-changes/change-data-capture-and-other-sql-server-features.md)  
  
-   [<span data-ttu-id="9975e-106">数据库快照</span><span class="sxs-lookup"><span data-stu-id="9975e-106">Database snapshots</span></span>](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
-   [<span data-ttu-id="9975e-107">全文目录</span><span class="sxs-lookup"><span data-stu-id="9975e-107">Full-text catalogs</span></span>](database-mirroring-and-full-text-catalogs-sql-server.md)  
  
-   [<span data-ttu-id="9975e-108">日志传送</span><span class="sxs-lookup"><span data-stu-id="9975e-108">Log shipping</span></span>](database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="9975e-109">复制</span><span class="sxs-lookup"><span data-stu-id="9975e-109">Replication</span></span>](database-mirroring-and-replication-sql-server.md)  
  
 <span data-ttu-id="9975e-110">数据库镜像与以下功能不能共存：</span><span class="sxs-lookup"><span data-stu-id="9975e-110">Database mirroring does not interoperate with the following:</span></span>  
  
-   <span data-ttu-id="9975e-111">跨数据库事务/分布式事务</span><span class="sxs-lookup"><span data-stu-id="9975e-111">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="9975e-112">有关不支持此类事务原因的信息，请参阅[数据库镜像或 AlwaysOn 可用性组 (SQL Server) 不支持跨数据库事务](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="9975e-112">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9975e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9975e-113">See Also</span></span>  
 [<span data-ttu-id="9975e-114">数据库镜像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9975e-114">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
