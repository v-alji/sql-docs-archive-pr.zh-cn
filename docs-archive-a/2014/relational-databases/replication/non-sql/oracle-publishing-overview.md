---
title: Oracle 发布概述 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b59b12dfcba1472cb6f9d6ecfc51a7df8104fb0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588975"
---
# <a name="oracle-publishing-overview"></a><span data-ttu-id="58dad-102">Oracle Publishing Overview</span><span class="sxs-lookup"><span data-stu-id="58dad-102">Oracle Publishing Overview</span></span>
  <span data-ttu-id="58dad-103">从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 开始，可以在复制拓扑中加入 Oracle 发布服务器（自 Oracle 9i 版起）。</span><span class="sxs-lookup"><span data-stu-id="58dad-103">Beginning with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you can include Oracle Publishers in your replication topology, starting with Oracle version 9i.</span></span> <span data-ttu-id="58dad-104">可在支持 Oracle 的任何硬件和操作系统上部署发布服务器。</span><span class="sxs-lookup"><span data-stu-id="58dad-104">Publishing servers can be deployed on any Oracle supported hardware and operating system.</span></span> <span data-ttu-id="58dad-105">该功能建立在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照复制和事务性复制的坚实基础上，提供了相似的性能和可用性。</span><span class="sxs-lookup"><span data-stu-id="58dad-105">The feature is built on the well-established foundation of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot replication and transactional replication, providing similar performance and usability.</span></span>  
  
 <span data-ttu-id="58dad-106">不推荐使用 Oracle 发布。</span><span class="sxs-lookup"><span data-stu-id="58dad-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="58dad-107">不推荐异类复制到非 SQL Server 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="58dad-107">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="58dad-108">若要移动数据，请创建使用变更数据捕获和 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]的解决方案。</span><span class="sxs-lookup"><span data-stu-id="58dad-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a><span data-ttu-id="58dad-109">Oracle 的快照复制</span><span class="sxs-lookup"><span data-stu-id="58dad-109">Snapshot Replication for Oracle</span></span>  
 <span data-ttu-id="58dad-110">Oracle 快照发布与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照发布在实现方式上类似。</span><span class="sxs-lookup"><span data-stu-id="58dad-110">Oracle snapshot publications are implemented in a manner similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot publications.</span></span> <span data-ttu-id="58dad-111">对 Oracle 发布运行快照代理时，该代理将连接到 Oracle 发布服务器，并处理发布中的每个表。</span><span class="sxs-lookup"><span data-stu-id="58dad-111">When the Snapshot Agent runs for an Oracle publication, it connects to the Oracle Publisher and processes each table in the publication.</span></span> <span data-ttu-id="58dad-112">处理每个表时，代理将检索表行并创建架构脚本，然后将该脚本存储在发布的快照共享中。</span><span class="sxs-lookup"><span data-stu-id="58dad-112">When processing each table, the agent retrieves the table rows and creates schema scripts, which are then stored on the publication's snapshot share.</span></span> <span data-ttu-id="58dad-113">每次运行快照代理时都会创建整个数据集，因此在事务复制中出现更改跟踪触发器时，不会将它们添加到 Oracle 表中。</span><span class="sxs-lookup"><span data-stu-id="58dad-113">The entire set of data is created each time the Snapshot Agent runs, so change tracking triggers are not added to the Oracle tables as they are with transactional replication.</span></span> <span data-ttu-id="58dad-114">快照复制是迁移数据的一种便利方法，可以将对发布系统的影响降到最低。</span><span class="sxs-lookup"><span data-stu-id="58dad-114">Snapshot replication provides a convenient way to migrate data with minimal impact on the publishing system.</span></span>  
  
## <a name="transactional-replication-for-oracle"></a><span data-ttu-id="58dad-115">Oracle 事务复制</span><span class="sxs-lookup"><span data-stu-id="58dad-115">Transactional Replication for Oracle</span></span>  
 <span data-ttu-id="58dad-116">Oracle 事务发布是通过使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的事务发布体系结构来实现的；但更改却是通过结合使用 Oracle 数据库上的数据库触发器和日志读取器代理来跟踪的。</span><span class="sxs-lookup"><span data-stu-id="58dad-116">Oracle transactional publications are implemented using the transactional publishing architecture of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; however, changes are tracked using a combination of database triggers on the Oracle database and the Log Reader Agent.</span></span> <span data-ttu-id="58dad-117">Oracle 事务发布的订阅服务器使用快照复制自动进行初始化；在以后发生更改时，将通过日志读取器代理对这些更改进行跟踪，并将更改传递到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="58dad-117">Subscribers to an Oracle transactional publication are automatically initialized using snapshot replication; subsequent changes are tracked and delivered to Subscribers as they occur via the Log Reader Agent.</span></span>  
  
 <span data-ttu-id="58dad-118">创建 Oracle 发布时，将为 Oracle 数据库中所有已发布的表创建触发器和跟踪表。</span><span class="sxs-lookup"><span data-stu-id="58dad-118">When an Oracle publication is created, triggers and tracking tables are created for each published table within the Oracle database.</span></span> <span data-ttu-id="58dad-119">对发布的表进行数据更改时，将激发这些表的数据库触发器，并在复制跟踪表中为修改的每一行插入信息。</span><span class="sxs-lookup"><span data-stu-id="58dad-119">When data changes are made to the published tables, the database triggers on the tables fire and insert information into the replication tracking tables for each modified row.</span></span> <span data-ttu-id="58dad-120">然后， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上的日志读取器代理将数据更改信息从跟踪表移动到分发服务器上的分发数据库中。</span><span class="sxs-lookup"><span data-stu-id="58dad-120">The Log Reader Agent on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor then moves the data change information from the tracking tables to the distribution database on the Distributor.</span></span> <span data-ttu-id="58dad-121">最后，与在标准事务复制中一样，分发代理将更改从分发服务器移动到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="58dad-121">Finally, as in standard transactional replication, the Distribution Agent moves changes from the Distributor to the Subscribers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dad-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58dad-122">See Also</span></span>  
 <span data-ttu-id="58dad-123">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="58dad-123">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="58dad-124">[有关 Oracle 发布的术语词汇表](glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="58dad-124">[Glossary of Terms for Oracle Publishing](glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="58dad-125">异类数据库复制</span><span class="sxs-lookup"><span data-stu-id="58dad-125">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
