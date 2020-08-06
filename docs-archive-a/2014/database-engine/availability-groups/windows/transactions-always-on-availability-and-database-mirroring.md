---
title: 数据库镜像不支持跨数据库事务或 AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- cross-database transactions [SQL Server]
- transactions [database mirroring]
- Availability Groups [SQL Server], interoperability
- troubleshooting [SQL Server], cross-database transactions
ms.assetid: 9f7ed895-ad65-43e3-ba08-00d7bff1456d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0e23e073375c8f00317003635df8ec0b69883cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693479"
---
# <a name="cross-database-transactions-not-supported-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="9f7aa-102">数据库镜像或 AlwaysOn 可用性组不支持跨数据库事务 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9f7aa-102">Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="9f7aa-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]或数据库镜像不支持跨数据库事务和分布式事务。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-103">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] or by database mirroring.</span></span> <span data-ttu-id="9f7aa-104">这是因为以下原因无法保证事务的原子性/完整性：</span><span class="sxs-lookup"><span data-stu-id="9f7aa-104">This is because transaction atomicity/integrity cannot be guaranteed for the following reasons:</span></span>  
  
-   <span data-ttu-id="9f7aa-105">对于跨数据库事务：每个数据库独立提交。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-105">For cross-database transactions: Each database commits independently.</span></span> <span data-ttu-id="9f7aa-106">因此，即使对于单个可用性组中的数据库，在一个数据库提交事务后、但是在另一个数据库提交前可能发生故障转移。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-106">Therefore, even for databases in a single availability group, a failover could occur after one database commits a transaction but before the other database does.</span></span> <span data-ttu-id="9f7aa-107">对于数据库镜像，此问题很复杂，因为在故障转移后，镜像数据库所在的服务器实例通常不同于其他数据库的服务器实例，即使在两个相同伙伴之间对两个数据库进行镜像，也无法保证两个数据库同时进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-107">For database mirroring this issue is compounded because after a failover, the mirrored database is typically on a different server instance from the other database, and  even if both databases are mirrored between the same two partners, there is no guarantee that both databases will fail over at the same time.</span></span>  
  
-   <span data-ttu-id="9f7aa-108">对于分布式事务：故障转移后，新主体服务器/主副本无法连接到前一个主体服务器/主副本的分布式事务处理协调器。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-108">For distributed transactions: After a failover, the new principal server/primary replica is unable to connect to the distributed transaction coordinator on the previous principal server/primary replica.</span></span> <span data-ttu-id="9f7aa-109">因此，新主体服务器/主副本无法获取事务状态。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-109">Therefore, the new principal server/primary replica cannot obtain the transaction status.</span></span>  
  
 <span data-ttu-id="9f7aa-110">以下数据库镜像示例说明了如何可能出现逻辑上的不一致。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-110">The following database mirroring example illustrates how a logical inconsistency could occur.</span></span> <span data-ttu-id="9f7aa-111">在此示例中，应用程序使用跨数据库事务插入两行数据：将其中一行插入镜像数据库 A 中的表，将另一行插入另一个数据库 B 中的表。数据库 A 在具有自动故障转移功能的高安全性模式下进行镜像。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-111">In this example, an application uses a cross-database transaction to insert two rows of data: one row is inserted into a table in a mirrored database, A, and the other row is inserted into a table in another database, B. Database A is being mirrored in high-safety mode with automatic failover.</span></span> <span data-ttu-id="9f7aa-112">提交事务时，数据库 A 不可用，镜像会话将故障自动转移到数据库 A 的镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-112">While the transaction is being committed, database A becomes unavailable, and the mirroring session automatically fails over to the mirror of database A.</span></span>  
  
 <span data-ttu-id="9f7aa-113">故障转移之后，跨数据库事务可能会在数据库 B 上成功提交，但不可能会在故障转移的数据库中成功提交。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-113">After the failover, the cross-database transaction might be successfully committed on database B but not on the failed-over database.</span></span> <span data-ttu-id="9f7aa-114">如果在发生故障之前，数据库 A 的原始主体服务器未能将跨数据库事务的日志发送到镜像服务器，则可能会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-114">This would occur if the original principal server for database A had not sent the log for the cross-database transaction to the mirror server before the failure.</span></span> <span data-ttu-id="9f7aa-115">故障转移之后，该事务将不存在于新的主体服务器上。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-115">After the failover, that transaction would not exist on the new principal server.</span></span> <span data-ttu-id="9f7aa-116">数据库 A 和数据库 B 出现不一致，因为在数据库 B 中插入的数据保持完好无损，而在数据库 A 中插入的数据已经丢失。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-116">Databases A and B would become inconsistent, because the data inserted in database B remains intact, but the data inserted in database A has been lost.</span></span>  
  
 <span data-ttu-id="9f7aa-117">使用 MS DTC 事务时可能会出现类似的情况。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-117">A similar scenario can occur while using a MS DTC transaction.</span></span> <span data-ttu-id="9f7aa-118">例如，故障转移后，新主体将访问 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-118">For example, after failover, the new principal contacts MS DTC.</span></span> <span data-ttu-id="9f7aa-119">但是 MS DTC 不能识别新的主体服务器，因而会终止被认为已在其他数据库中提交了的、所有“准备提交”的事务。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-119">But MS DTC has no knowledge of the new principal server, and it terminates any transactions that are "preparing to commit," which are considered committed in other databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f7aa-120">将数据库镜像或可用性组与 DTC 搭配使用不会导致 SQL Server 安装失去支持。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-120">Using Database Mirroring or Availability Groups together with DTC does not result in an unsupported SQL Server installation.</span></span> <span data-ttu-id="9f7aa-121">但是，如果数据库为数据库镜像会话或可用性组的一部分，且在数据库中使用了 DTC，则仅当支持问题与将数据库镜像或可用性组与 DTC 搭配使用无关时将由 Microsoft 组织调查。</span><span class="sxs-lookup"><span data-stu-id="9f7aa-121">If, however, a database is part of a Database Mirroring session or an Availability Group and DTC is also used in the database, support issues will be investigated by Microsoft only if unrelated to the combined use of Database Mirroring or Availability Groups with DTC.</span></span>  
  
  
