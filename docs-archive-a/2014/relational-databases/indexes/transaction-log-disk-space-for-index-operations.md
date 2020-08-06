---
title: 索引操作的事务日志磁盘空间 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index disk space [SQL Server]
- space [SQL Server], indexes
- transaction logs [SQL Server], disk space
- disk space [SQL Server], transaction logs
- space [SQL Server], transaction logs
ms.assetid: 4f8a4922-4507-4072-be67-c690528d5c3b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c34c9ff7a9494496d6c60d5920184c0ce86131d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692917"
---
# <a name="transaction-log-disk-space-for-index-operations"></a><span data-ttu-id="564b8-102">索引操作的事务日志磁盘空间</span><span class="sxs-lookup"><span data-stu-id="564b8-102">Transaction Log Disk Space for Index Operations</span></span>
  <span data-ttu-id="564b8-103">大规模索引操作可以产生大量数据负载，从而导致事务日志的空间很快被占满。</span><span class="sxs-lookup"><span data-stu-id="564b8-103">Large-scale index operations can generate large data loads that can cause the transaction log to fill quickly.</span></span> <span data-ttu-id="564b8-104">若要确保索引操作能够回滚，不能在完成索引操作之前截断事务日志，但可以在索引操作期间备份日志。</span><span class="sxs-lookup"><span data-stu-id="564b8-104">To make sure that the index operation can be rolled back, the transaction log cannot be truncated until the index operation has completed; however, the log can be backed up during the index operation.</span></span> <span data-ttu-id="564b8-105">因此，事务日志必须具有足够的空间，以存储索引操作期间的索引操作事务和任何并发用户事务。</span><span class="sxs-lookup"><span data-stu-id="564b8-105">Therefore, the transaction log must have sufficient room to store both the index operation transactions and any concurrent user transactions for the duration of the index operation.</span></span> <span data-ttu-id="564b8-106">这对脱机索引操作和联机索引操作都适用。</span><span class="sxs-lookup"><span data-stu-id="564b8-106">This is true for both offline and online index operations.</span></span> <span data-ttu-id="564b8-107">因为在脱机索引操作期间不能访问基础表，所以用户事务可能很少，日志的增长速度不快。</span><span class="sxs-lookup"><span data-stu-id="564b8-107">Because the underlying tables cannot be accessed during an offline index operation, there may be few user transactions and the log may not grow as quickly.</span></span> <span data-ttu-id="564b8-108">联机索引操作不能防止并发用户活动，因此，大规模联机索引操作与大量的并发用户事务相结合可能会导致事务日志不断增长，而不会提供截断日志的选项。</span><span class="sxs-lookup"><span data-stu-id="564b8-108">Online index operations do not prevent concurrent user activity, therefore, large-scale online index operations combined with significant concurrent user transactions can cause continuous growth of the transaction log without an option to truncate the log.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="564b8-109">建议</span><span class="sxs-lookup"><span data-stu-id="564b8-109">Recommendations</span></span>  
 <span data-ttu-id="564b8-110">运行大规模索引操作时，请考虑下列建议：</span><span class="sxs-lookup"><span data-stu-id="564b8-110">When you run large-scale index operations, consider the following recommendations:</span></span>  
  
1.  <span data-ttu-id="564b8-111">确保在联机运行大规模索引操作之前备份并截断事务日志，并且日志中具有足够的空间来存储计划的索引事务和用户事务。</span><span class="sxs-lookup"><span data-stu-id="564b8-111">Make sure the transaction log has been backed up and truncated before running large-scale index operations online, and that the log has sufficient space to store the projected index and user transactions.</span></span>  
  
2.  <span data-ttu-id="564b8-112">考虑将索引操作的 SORT_IN_TEMPDB 选项设置为 ON。</span><span class="sxs-lookup"><span data-stu-id="564b8-112">Consider setting the SORT_IN_TEMPDB option to ON for the index operation.</span></span> <span data-ttu-id="564b8-113">这将把索引事务与并发用户事务分开。</span><span class="sxs-lookup"><span data-stu-id="564b8-113">This separates the index transactions from the concurrent user transactions.</span></span> <span data-ttu-id="564b8-114">索引事务将存储在 **tempdb** 事务日志中，而并发用户事务将存储在用户数据库的事务日志中。</span><span class="sxs-lookup"><span data-stu-id="564b8-114">The index transactions will be stored in the **tempdb** transaction log, and the concurrent user transactions will be stored in the transaction log of the user database.</span></span> <span data-ttu-id="564b8-115">这允许在索引操作期间截断用户数据库中的事务日志（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="564b8-115">This allows for the transaction log of the user database to be truncated during the index operation if it is required.</span></span> <span data-ttu-id="564b8-116">此外，如果 **tempdb** 日志与用户数据库日志不在同一磁盘上，两个日志将不会争用同一磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="564b8-116">Additionally, if the **tempdb** log is not on the same disk as the user database log, the two logs are not competing for the same disk space.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="564b8-117">验证 **tempdb** 数据库和事务日志具有足够的空间来处理索引操作。</span><span class="sxs-lookup"><span data-stu-id="564b8-117">Verify that the **tempdb** database and transaction log have sufficient disk space to handle the index operation.</span></span> <span data-ttu-id="564b8-118">不能在索引操作完成之前截断 **tempdb** 事务日志。</span><span class="sxs-lookup"><span data-stu-id="564b8-118">The **tempdb** transaction log cannot be truncated until the index operation is completed.</span></span>  
  
3.  <span data-ttu-id="564b8-119">使用数据库恢复模型，它允许对索引操作做最小的日志记录。</span><span class="sxs-lookup"><span data-stu-id="564b8-119">Use a database recovery model that allows for minimal logging of the index operation.</span></span> <span data-ttu-id="564b8-120">这可以减少日志的大小，并防止日志占满日志空间。</span><span class="sxs-lookup"><span data-stu-id="564b8-120">This may reduce the size of the log and prevent the log from filling the log space.</span></span>  
  
4.  <span data-ttu-id="564b8-121">不要在显式事务中执行联机索引操作。</span><span class="sxs-lookup"><span data-stu-id="564b8-121">Do not run the online index operation in an explicit transaction.</span></span> <span data-ttu-id="564b8-122">在显式事务结束之前不会截断日志。</span><span class="sxs-lookup"><span data-stu-id="564b8-122">The log will not be truncated until the explicit transaction ends.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="564b8-123">相关内容</span><span class="sxs-lookup"><span data-stu-id="564b8-123">Related Content</span></span>  
 [<span data-ttu-id="564b8-124">索引 DDL 操作的磁盘空间要求</span><span class="sxs-lookup"><span data-stu-id="564b8-124">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="564b8-125">索引磁盘空间示例</span><span class="sxs-lookup"><span data-stu-id="564b8-125">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
  
