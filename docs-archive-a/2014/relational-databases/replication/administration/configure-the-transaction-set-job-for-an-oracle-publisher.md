---
title: 为 Oracle 发布服务器配置事务集作业 (复制 Transact-sql 编程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693783"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a><span data-ttu-id="cd645-102">为 Oracle 发布服务器配置事务集作业（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="cd645-102">Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="cd645-103">**Xactset** 作业是在发布服务器上运行的复制创建的 Oracle 数据库作业，用于在日志读取器代理未与发布服务器连接时创建事务集。</span><span class="sxs-lookup"><span data-stu-id="cd645-103">The **Xactset** job is an Oracle database job created by replication that runs at an Oracle Publisher to create transaction sets when the Log Reader Agent is not connected to the Publisher.</span></span> <span data-ttu-id="cd645-104">您可以使用复制存储过程以编程方式从分发服务器启用和配置此作业。</span><span class="sxs-lookup"><span data-stu-id="cd645-104">You can enable and configure this job from the Distributor programmatically using replication stored procedures.</span></span> <span data-ttu-id="cd645-105">有关详细信息，请参阅 [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)（Oracle 发布服务器的性能优化）。</span><span class="sxs-lookup"><span data-stu-id="cd645-105">For more information, see [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
### <a name="to-enable-the-transaction-set-job"></a><span data-ttu-id="cd645-106">启用事务集作业</span><span class="sxs-lookup"><span data-stu-id="cd645-106">To enable the transaction set job</span></span>  
  
1.  <span data-ttu-id="cd645-107">在 Oracle 分发服务器上，将 **job_queue_processes** 初始化参数设置为一个足够大的值以允许 Xactset 作业运行。</span><span class="sxs-lookup"><span data-stu-id="cd645-107">At the Oracle Publisher, set the **job_queue_processes** initialization parameter to a sufficient value to allow the Xactset job run.</span></span> <span data-ttu-id="cd645-108">有关此参数的详细信息，请参阅 Oracle 发布服务器的数据库文档。</span><span class="sxs-lookup"><span data-stu-id="cd645-108">For more information about this parameter, see the database documentation for the Oracle Publisher.</span></span>  
  
2.  <span data-ttu-id="cd645-109">在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-109">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-110">为\*\* \@ 发布服务器**指定 Oracle 发布服务器的名称，将的值指定 `xactsetbatching` 为** \@ propertyname**，并将值 `enabled` 指定** \@ \*\*为。</span><span class="sxs-lookup"><span data-stu-id="cd645-110">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetbatching` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="cd645-111">在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-111">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-112">为 " \*\* \@ 发布服务器**" 指定 Oracle 发布服务器的名称，将 "值" 指定 `xactsetjobinterval` 为** \@ propertyname\*\*，并为 "值" \*\* \@ \*\*指定值 "时间间隔"。</span><span class="sxs-lookup"><span data-stu-id="cd645-112">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjobinterval` for **\@propertyname**, and the job interval, in minutes, for **\@propertyvalue**.</span></span>  
  
4.  <span data-ttu-id="cd645-113">在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-113">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-114">为\*\* \@ 发布服务器**指定 Oracle 发布服务器的名称，将的值指定 `xactsetjob` 为** \@ propertyname**，并将值 `enabled` 指定** \@ \*\*为。</span><span class="sxs-lookup"><span data-stu-id="cd645-114">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
### <a name="to-configure-the-transaction-set-job"></a><span data-ttu-id="cd645-115">配置事务集作业</span><span class="sxs-lookup"><span data-stu-id="cd645-115">To configure the transaction set job</span></span>  
  
1.  <span data-ttu-id="cd645-116">（可选）在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-116">(Optional) At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-117">为 \@publisher 指定 Oracle 发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="cd645-117">Specify the name of the Oracle Publisher for **\@publisher**.</span></span> <span data-ttu-id="cd645-118">这将返回发布服务器上的 **Xactset** 作业的属性。</span><span class="sxs-lookup"><span data-stu-id="cd645-118">This returns properties of the **Xactset** job at the Publisher.</span></span>  
  
2.  <span data-ttu-id="cd645-119">在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-119">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-120">为\*\* \@ 发布服务器**指定 Oracle 发布服务器的名称，为** \@ propertyname**设置的 Xactset 作业属性的名称，并为** \@ propertyvalue\*\*指定新设置。</span><span class="sxs-lookup"><span data-stu-id="cd645-120">Specify the name of the Oracle Publisher for **\@publisher**, the name of the Xactset job property being set for **\@propertyname**, and new setting for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="cd645-121">（可选）对于每个要设置的 Xactset 作业属性重复步骤 2。</span><span class="sxs-lookup"><span data-stu-id="cd645-121">(Optional) Repeat step 2 for each Xactset job property being set.</span></span> <span data-ttu-id="cd645-122">更改属性时 `xactsetjobinterval` ，必须在 Oracle 发布服务器上重新启动作业，以使新的时间间隔生效。</span><span class="sxs-lookup"><span data-stu-id="cd645-122">When changing the `xactsetjobinterval` property, you must restart the job on the Oracle Publisher for the new interval to take effect.</span></span>  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a><span data-ttu-id="cd645-123">查看事务集作业的属性</span><span class="sxs-lookup"><span data-stu-id="cd645-123">To view properties of the transaction set job</span></span>  
  
1.  <span data-ttu-id="cd645-124">在分发服务器上，执行 [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-124">At the Distributor, execute [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql).</span></span> <span data-ttu-id="cd645-125">为 \@publisher 指定 Oracle 发布服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="cd645-125">Specify the name of the Oracle Publisher for **\@publisher**.</span></span>  
  
### <a name="to-disable-the-transaction-set-job"></a><span data-ttu-id="cd645-126">禁用事务集作业</span><span class="sxs-lookup"><span data-stu-id="cd645-126">To disable the transaction set job</span></span>  
  
1.  <span data-ttu-id="cd645-127">在分发服务器上，执行 [sp_publisherproperty (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cd645-127">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="cd645-128">为\*\* \@ 发布服务器**指定 Oracle 发布服务器的名称，将的值指定 `xactsetjob` 为** \@ propertyname**，并将值 `disabled` 指定** \@ \*\*为。</span><span class="sxs-lookup"><span data-stu-id="cd645-128">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `disabled` for **\@propertyvalue**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd645-129">示例</span><span class="sxs-lookup"><span data-stu-id="cd645-129">Example</span></span>  
 <span data-ttu-id="cd645-130">以下示例将启用 `Xactset` 作业并将运行间隔设置为三分钟。</span><span class="sxs-lookup"><span data-stu-id="cd645-130">The following example enables the `Xactset` job and sets an interval of three minutes between runs.</span></span>  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a><span data-ttu-id="cd645-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd645-131">See Also</span></span>  
 <span data-ttu-id="cd645-132">[Oracle 发布服务器的性能优化](../non-sql/performance-tuning-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="cd645-132">[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="cd645-133">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="cd645-133">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
