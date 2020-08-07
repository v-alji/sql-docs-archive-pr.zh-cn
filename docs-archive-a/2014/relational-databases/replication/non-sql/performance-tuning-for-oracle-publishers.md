---
title: Oracle 发布服务器性能优化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], performance tuning
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 83d660eee839d525fa0bdabf88a313da0ed44244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576637"
---
# <a name="performance-tuning-for-oracle-publishers"></a><span data-ttu-id="c4fa0-102">Oracle 发布服务器性能优化</span><span class="sxs-lookup"><span data-stu-id="c4fa0-102">Performance Tuning for Oracle Publishers</span></span>
  <span data-ttu-id="c4fa0-103">Oracle 发布体系结构与 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 发布体系结构类似。因此，Oracle 复制性能优化的第一步要求遵循 [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md)中提供的一般优化建议。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-103">The Oracle publishing architecture is similar to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publishing architecture; therefore the first step in tuning Oracle replication for performance requires following the general tuning recommendations found in [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md).</span></span>  
  
 <span data-ttu-id="c4fa0-104">此外，还有两个与 Oracle 发布服务器性能有关的选项：</span><span class="sxs-lookup"><span data-stu-id="c4fa0-104">In addition there are two options for Oracle Publishers that are performance related:</span></span>  
  
-   <span data-ttu-id="c4fa0-105">指定适当的发布选项：Oracle 或 Oracle 网关。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-105">Specifying the appropriate publishing option: Oracle or Oracle Gateway.</span></span>  
  
-   <span data-ttu-id="c4fa0-106">配置事务集作业，使其按照适当的时间间隔处理发布服务器上的更改。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-106">Configuring the transaction set job to process changes on the Publisher at an appropriate interval.</span></span>  
  
## <a name="specifying-the-appropriate-publishing-option"></a><span data-ttu-id="c4fa0-107">指定适当的发布选项</span><span class="sxs-lookup"><span data-stu-id="c4fa0-107">Specifying the Appropriate Publishing Option</span></span>  
 <span data-ttu-id="c4fa0-108">“Oracle Gateway”选项的性能优于“Oracle Complete”选项；但是，此选项不能用于在多个事务发布中发布同一个表。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-108">The Oracle Gateway option provides improved performance over the Oracle Complete option; however, this option cannot be used to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="c4fa0-109">一个表最多只能出现在一个事务发布中，但可以出现在任意多个快照发布中。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-109">A table can appear in at most one transactional publication and any number of snapshot publications.</span></span> <span data-ttu-id="c4fa0-110">如果需要在多个事务发布中发布同一个表，请选择“Oracle Complete”选项。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-110">If you need to publish the same table in multiple transactional publications, choose the Oracle Complete option.</span></span> <span data-ttu-id="c4fa0-111">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器上标识 Oracle 发布服务器时，请指定此选项。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-111">Specify this option when identifying the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="c4fa0-112">有关详细信息，请参阅 [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-112">For more information, see [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
## <a name="configuring-the-transaction-set-job"></a><span data-ttu-id="c4fa0-113">配置事务集作业</span><span class="sxs-lookup"><span data-stu-id="c4fa0-113">Configuring the Transaction Set Job</span></span>  
 <span data-ttu-id="c4fa0-114">对已发布 Oracle 表所做的更改在称为“事务集”的组中处理。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-114">Changes to published Oracle tables are processed in groups called transaction sets.</span></span> <span data-ttu-id="c4fa0-115">为了确保事务的一致性，每个事务集都作为单一事务在分发数据库上提交。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-115">To ensure transactional consistency, each transaction set is committed as a single transaction at the distribution database.</span></span> <span data-ttu-id="c4fa0-116">如果事务集变得过大，则无法作为单一的事务进行有效处理。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-116">If the transaction set becomes too large, it cannot be processed efficiently as a single transaction.</span></span>  
  
 <span data-ttu-id="c4fa0-117">默认情况下，事务集只由日志读取器代理来创建。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-117">By default, transaction sets are created only by the Log Reader Agent.</span></span> <span data-ttu-id="c4fa0-118">在大量更改活动过程中，如果日志读取器代理没有运行，或无法从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分发服务器连接到 Oracle 发布服务器，则事务集可能会变得异常大而难以处理。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-118">If, during periods of high change activity, the Log Reader Agent does not run or cannot connect from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher, transaction sets can become unmanageably large.</span></span> <span data-ttu-id="c4fa0-119">若要避免此问题，请确保即便在日志读取器代理没有运行或无法连接到 Oracle 发布服务器情况下，仍定期创建事务集。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-119">To prevent this problem, ensure that transaction sets are created at regular intervals, even if the Log Reader Agent does not run or cannot connect to the Oracle Publisher.</span></span>  
  
 <span data-ttu-id="c4fa0-120">可以使用 Xactset 作业（一种通过复制安装的 Oracle 数据库作业）来创建事务集，它所采用的机制与日志读取器代理创建事务集所用的机制相同。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-120">Transaction sets can be created with the Xactset job (an Oracle database job installed by replication), which uses the same mechanism that the Log Reader Agent does to create sets.</span></span> <span data-ttu-id="c4fa0-121">每次该作业运行时，都会创建新的事务集。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-121">Each time the job runs, a new transaction set is created.</span></span> <span data-ttu-id="c4fa0-122">日志读取器代理下一次运行时，代理将处理已创建的所有事务集。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-122">The next time that the Log Reader Agent runs, the agent processes any sets that have been created.</span></span> <span data-ttu-id="c4fa0-123">如果在处理完所有现有事务集后，仍然存在挂起更改，则日志读取器代理将创建和处理一个或多个额外的事务集。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-123">If there are still pending changes after all existing transaction sets have been processed, the Log Reader Agent creates and processes one or more additional transaction sets.</span></span>  
  
 <span data-ttu-id="c4fa0-124">若要配置事务集作业，请参阅[为 Oracle 发布服务器配置事务集作业（复制 Transact-SQL 编程）](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fa0-124">To configure the transaction set job, see [Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fa0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4fa0-125">See Also</span></span>  
 <span data-ttu-id="c4fa0-126">[配置 Oracle 发布服务器](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="c4fa0-126">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="c4fa0-127">Oracle 发布概述</span><span class="sxs-lookup"><span data-stu-id="c4fa0-127">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
