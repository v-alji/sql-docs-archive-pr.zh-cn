---
title: 控制事务持久性 | Microsoft Docs
ms.custom: ''
ms.date: 05/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- delayed durability
- Lazy Commit
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f37bcaf8719f4a2f3b1e7fbca1cf332717bd936e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580739"
---
# <a name="control-transaction-durability"></a><span data-ttu-id="8598c-102">控制事务持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-102">Control Transaction Durability</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8598c-103">事务提交可以是完全持久、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 默认设置或延迟的持久（也称作迟缓提交）。</span><span class="sxs-lookup"><span data-stu-id="8598c-103">transaction commits can be either fully durable, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default, or delayed durable (also known as lazy commit).</span></span>  
  
 <span data-ttu-id="8598c-104">完全持久事务提交是同步的，仅在事务的日志记录写入磁盘后报告提交成功，并将控制权归还客户端。</span><span class="sxs-lookup"><span data-stu-id="8598c-104">Fully durable transaction commits are synchronous and report a commit as successful and return control to the client only after the log records for the transaction are written to disk.</span></span> <span data-ttu-id="8598c-105">延迟持久事务提交是异步的，并在事务的日志记录写入磁盘之前报告提交成功。</span><span class="sxs-lookup"><span data-stu-id="8598c-105">Delayed durable transaction commits are asynchronous and report a commit as successful before the log records for the transaction are written to disk.</span></span> <span data-ttu-id="8598c-106">事务要成为持久事务，必须将事务日志条目写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-106">Writing the transaction log entries to disk is required for a transaction to be durable.</span></span> <span data-ttu-id="8598c-107">当事务日志条目刷新到磁盘时，延迟持久事务成为持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-107">Delayed durable transactions become durable when the transaction log entries are flushed to disk.</span></span>  
  
 <span data-ttu-id="8598c-108">本主题详细说明延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-108">This topic details delayed durable transactions.</span></span>  
  
## <a name="full-vs-delayed-transaction-durability"></a><span data-ttu-id="8598c-109">完全与延迟事务持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-109">Full vs. Delayed Transaction Durability</span></span>  
 <span data-ttu-id="8598c-110">完全和延迟事务持续性各有其优缺点。</span><span class="sxs-lookup"><span data-stu-id="8598c-110">Both full and delayed transaction durability have their advantages and disadvantages.</span></span> <span data-ttu-id="8598c-111">一个应用程序可能同时包含完全和延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-111">An application can have a mix of fully and delayed durable transactions.</span></span> <span data-ttu-id="8598c-112">您应该仔细考虑业务需求以及每个应用程序如何满足这些需求。</span><span class="sxs-lookup"><span data-stu-id="8598c-112">You should carefully consider your business needs and how each fits into those needs.</span></span>  
  
### <a name="full-transaction-durability"></a><span data-ttu-id="8598c-113">完全事务持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-113">Full transaction durability</span></span>  
 <span data-ttu-id="8598c-114">完全持久事务在将控制权归还给客户端之前将事务日志写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-114">Fully durable transactions write the transaction log to disk before returning control to the client.</span></span> <span data-ttu-id="8598c-115">只要存在以下情况，就应使用完全持久事务：</span><span class="sxs-lookup"><span data-stu-id="8598c-115">You should use fully durable transactions whenever:</span></span>  
  
-   <span data-ttu-id="8598c-116">系统无法承受任何数据丢失。</span><span class="sxs-lookup"><span data-stu-id="8598c-116">Your system cannot tolerate any data loss.</span></span>   
    <span data-ttu-id="8598c-117">有关可能在何种情况下会丢失一些数据的信息，请参阅 [在什么情况下会丢失数据？](#when-can-i-lose-data) 部分。</span><span class="sxs-lookup"><span data-stu-id="8598c-117">See the section [When can I lose data?](#when-can-i-lose-data) for information on when you can lose some of your data.</span></span>  
  
-   <span data-ttu-id="8598c-118">造成瓶颈的原因不是事务日志写入延迟。</span><span class="sxs-lookup"><span data-stu-id="8598c-118">The bottleneck is not due to transaction log write latency.</span></span>  
  
 <span data-ttu-id="8598c-119">通过在内存中保留事务日志记录并批量写入事务日志，延迟事务持续性可以缩短延迟，因而减少了所需的 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="8598c-119">Delayed transaction durability reduces the latency due to log I/O by keeping the transaction log records in memory and writing to the transaction log in batches, thus requiring fewer I/O operations.</span></span> <span data-ttu-id="8598c-120">延迟事务持续性可能会减少日志 I/O 争用，从而减少系统中的等待。</span><span class="sxs-lookup"><span data-stu-id="8598c-120">Delayed transaction durability potentially reduces log I/O contention, thus reducing waits in the system.</span></span>  
  
 <span data-ttu-id="8598c-121">**完全事务持续性保证**</span><span class="sxs-lookup"><span data-stu-id="8598c-121">**Full Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="8598c-122">事务提交成功后，该事务所做的更改就对系统中的其他事务可见。</span><span class="sxs-lookup"><span data-stu-id="8598c-122">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span> <span data-ttu-id="8598c-123">有关详细信息，请参阅主题[事务隔离级别](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="8598c-123">See the topic [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for more information.</span></span>  
  
-   <span data-ttu-id="8598c-124">提交并不保证持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-124">Durability is guaranteed on commit.</span></span> <span data-ttu-id="8598c-125">在事务提交成功并将控制权归还给客户端之前，对应的日志记录会保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-125">Corresponding log records are persisted to disk before the transaction commit succeeds and returns control to the client.</span></span>  
  
### <a name="delayed-transaction-durability"></a><span data-ttu-id="8598c-126">延迟事务持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-126">Delayed transaction durability</span></span>  
 <span data-ttu-id="8598c-127">延迟事务持续性使用向磁盘的异步日志写入来实现。</span><span class="sxs-lookup"><span data-stu-id="8598c-127">Delayed transaction durability is accomplished using asynchronous log writes to disk.</span></span> <span data-ttu-id="8598c-128">事务日志记录保留在缓冲区中并在缓冲区充满或发生缓冲区刷新事件时写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-128">Transaction log records are kept in a buffer and written to disk when the buffer fills or a buffer flushing event takes place.</span></span> <span data-ttu-id="8598c-129">延迟事务持续性可能会减少系统中的延迟和争用，因为：</span><span class="sxs-lookup"><span data-stu-id="8598c-129">Delayed transaction durability reduces both latency and contention within the system because:</span></span>  
  
-   <span data-ttu-id="8598c-130">事务提交处理不会等待日志 IO 完成就将控制权归还给客户端。</span><span class="sxs-lookup"><span data-stu-id="8598c-130">The transaction commit processing does not wait for log IO to finish and return control to the client.</span></span>  
  
-   <span data-ttu-id="8598c-131">并发事务争用日志 IO 的可能性更小；日志缓冲区现在可以更大的区块刷新到磁盘，从而减少争用和提高吞吐量。</span><span class="sxs-lookup"><span data-stu-id="8598c-131">Concurrent transactions are less likely to contend for log IO; instead, the log buffer can be flushed to disk in larger chunks, reducing contention, and increasing throughput.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8598c-132">如果并发度很高，特别是如果填充日志缓冲区的速度比刷新缓冲区的速度快，仍然可能发生日志 I/O 争用。</span><span class="sxs-lookup"><span data-stu-id="8598c-132">You may still have log I/O contention if there is a high degree of concurrency, particularly if you fill up the log buffer faster than you flush it.</span></span>  
  
 <span data-ttu-id="8598c-133">**何时使用延迟事务持续性**</span><span class="sxs-lookup"><span data-stu-id="8598c-133">**When to use delayed transaction durability**</span></span>  
  
 <span data-ttu-id="8598c-134">适合使用延迟事务持续性的部分情况如下：</span><span class="sxs-lookup"><span data-stu-id="8598c-134">Some of the cases in which you could benefit from using delayed transaction durability are:</span></span>  
  
 <span data-ttu-id="8598c-135">**可容忍丢失部分数据。** </span><span class="sxs-lookup"><span data-stu-id="8598c-135">**You can tolerate some data loss.**</span></span>  
 <span data-ttu-id="8598c-136">如果可以容忍一定的数据丢失，例如只要有大部分数据即可，个别记录不是非常重要，就值得考虑延迟持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-136">If you can tolerate some data loss, for example, where individual records are not critical as long as you have most of the data, then delayed durability may be worth considering.</span></span> <span data-ttu-id="8598c-137">如果无法容忍任何数据丢失，则不要使用延迟事务持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-137">If you cannot tolerate any data loss, do not use delayed transaction durability.</span></span>  
  
 <span data-ttu-id="8598c-138">**在事务日志写入时遭遇瓶颈。** </span><span class="sxs-lookup"><span data-stu-id="8598c-138">**You are experiencing a bottleneck on transaction log writes.**</span></span>  
 <span data-ttu-id="8598c-139">如果性能问题是由于事务日志写入延迟造成的，则应用程序可能适合使用延迟事务持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-139">If your performance issues are due to latency in transaction log writes, your application will likely benefit from using delayed transaction durability.</span></span>  
  
 <span data-ttu-id="8598c-140">**工作负荷的争用率很高。** </span><span class="sxs-lookup"><span data-stu-id="8598c-140">**Your workloads have a high contention rate.**</span></span>  
 <span data-ttu-id="8598c-141">如果系统工作负载争用级别很高，则会花费大量时间等待锁释放。</span><span class="sxs-lookup"><span data-stu-id="8598c-141">If your system has workloads with a high contention level much time is lost waiting for locks to be released.</span></span> <span data-ttu-id="8598c-142">延迟事务持续性会缩短提交时间，因此能够更快地释放锁，从而实现更大的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="8598c-142">Delayed transaction durability reduces commit time and thus releases locks faster which results in higher throughput.</span></span>  
  
 <span data-ttu-id="8598c-143">**延迟事务持续性保证**</span><span class="sxs-lookup"><span data-stu-id="8598c-143">**Delayed Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="8598c-144">事务提交成功后，该事务所做的更改就对系统中的其他事务可见。</span><span class="sxs-lookup"><span data-stu-id="8598c-144">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span>  
  
-   <span data-ttu-id="8598c-145">事务持续性只能通过将内存中事务日志刷新到磁盘来保证。</span><span class="sxs-lookup"><span data-stu-id="8598c-145">Transaction durability is guaranteed only following a flush of the in-memory transaction log to disk.</span></span> <span data-ttu-id="8598c-146">内存中事务日志在以下情况下刷新到磁盘：</span><span class="sxs-lookup"><span data-stu-id="8598c-146">The in-memory transaction log is flushed to disk when:</span></span>  
  
    -   <span data-ttu-id="8598c-147">同一个数据库中完全持久的事务在数据库中做出更改并成功提交。</span><span class="sxs-lookup"><span data-stu-id="8598c-147">A fully durable transaction in the same database makes a change in the database and successfully commits.</span></span>  
  
    -   <span data-ttu-id="8598c-148">用户成功执行系统存储过程 `sp_flush_log` 。</span><span class="sxs-lookup"><span data-stu-id="8598c-148">The user executes the system stored procedure `sp_flush_log` successfully.</span></span>  
  
    -   <span data-ttu-id="8598c-149">内存中事务日志缓冲区填充并自动刷新到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-149">The in-memory transaction log buffer fills up and automatically flushes to disk.</span></span>  
  
     <span data-ttu-id="8598c-150">如果完全持久的事务或 sp_flush_log 成功提交，则之前提交的所有延迟持续性事务都已成为持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-150">If a fully durable transaction or sp_flush_log successfully commit, all previously committed delayed durability transactions have been made durable.</span></span>  
  
 <span data-ttu-id="8598c-151">日志可定期刷新到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-151">The log may be flushed to disk periodically.</span></span> <span data-ttu-id="8598c-152">但是，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不提供除持久事务和 sp_flush_log 以外的任何持久保证。</span><span class="sxs-lookup"><span data-stu-id="8598c-152">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not provide any durability guarantees other than durable transactions and sp_flush_log.</span></span>  
  
## <a name="how-to-control-transaction-durability"></a><span data-ttu-id="8598c-153">如何控制事务持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-153">How to control transaction durability</span></span>  
  
### <a name="database-level-control"></a><span data-ttu-id="8598c-154">数据库级别控制</span><span class="sxs-lookup"><span data-stu-id="8598c-154">Database level control</span></span>  
 <span data-ttu-id="8598c-155">您作为 DBA，可以控制用户是否可通过以下语句对数据库使用延迟事务持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-155">You, the DBA, can control whether users can use delayed transaction durability on a database with the following statement.</span></span> <span data-ttu-id="8598c-156">您必须使用 ALTER DATABASE 来设置延迟持续性设置。</span><span class="sxs-lookup"><span data-stu-id="8598c-156">You must set the delayed durability setting with ALTER DATABASE.</span></span>  
  
```sql  
ALTER DATABASE ... SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
```  
  
 `DISABLED`  
 <span data-ttu-id="8598c-157">[默认] 使用此设置时，不管提交级别设置如何 (DELAYED_DURABILITY=[ON | OFF])，对数据库提交的所有事务都是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-157">[default] With this setting, all transactions that commit on the database are fully durable, regardless of the commit level setting (DELAYED_DURABILITY=[ON | OFF]).</span></span> <span data-ttu-id="8598c-158">无需更改和重新编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="8598c-158">There is no need for stored procedure change and recompilation.</span></span> <span data-ttu-id="8598c-159">这样能确保任何数据都不会因延迟持续性面临风险。</span><span class="sxs-lookup"><span data-stu-id="8598c-159">This allows you to ensure that no data is ever put at risk by delayed durability.</span></span>  
  
 `ALLOWED`  
 <span data-ttu-id="8598c-160">使用此设置时，每个事务的持续性都在事务级别确定 - DELAYED_DURABILITY = { OFF | ON }。</span><span class="sxs-lookup"><span data-stu-id="8598c-160">With this setting, each transaction's durability is determined at the transaction level - DELAYED_DURABILITY = { *OFF* | ON }.</span></span> <span data-ttu-id="8598c-161">有关详细信息，请参阅[原子块级别控制-本机编译存储过程](#atomic-block-level-control---natively-compiled-stored-procedures)和[提交级别控制-transact-sql](#commit-level-control---t-sql) 。</span><span class="sxs-lookup"><span data-stu-id="8598c-161">See [Atomic block level control - Natively Compiled Stored Procedures](#atomic-block-level-control---natively-compiled-stored-procedures) and [COMMIT level control - Transact-SQL](#commit-level-control---t-sql) for more information.</span></span>  
  
 `FORCED`  
 <span data-ttu-id="8598c-162">使用此设置，对数据库提交的每个事务都是延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-162">With this setting, every transaction that commits on the database is delayed durable.</span></span> <span data-ttu-id="8598c-163">无论事务指定完全持久 (DELAYED_DURABILITY = OFF) 还是不进行任何指定，事务都是延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-163">Whether the transaction specifies fully durable (DELAYED_DURABILITY = OFF) or makes no specification, the transaction is delayed durable.</span></span> <span data-ttu-id="8598c-164">当数据库适合使用延迟事务持续性，并且您不希望更改任何应用程序代码时，此设置很有用。</span><span class="sxs-lookup"><span data-stu-id="8598c-164">This setting is useful when delayed transaction durability is useful for a database and you do not want to change any application code.</span></span>  
  
### <a name="atomic-block-level-control---natively-compiled-stored-procedures"></a><span data-ttu-id="8598c-165"> 原子块级别控制 - 本机编译存储过程</span><span class="sxs-lookup"><span data-stu-id="8598c-165">Atomic block level control - Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="8598c-166">下面的代码面向原子块内部。</span><span class="sxs-lookup"><span data-stu-id="8598c-166">The following code goes inside the atomic block.</span></span>  
  
```sql  
DELAYED_DURABILITY = { OFF | ON }  
```  
  
 `OFF`  
 <span data-ttu-id="8598c-167">[默认] 事务是完全持久事务，除非数据库选项 DELAYED_DURABLITY = FORCED 有效（在这种情况下，提交是异步的，因而是延迟持久事务）。</span><span class="sxs-lookup"><span data-stu-id="8598c-167">[default] The transaction is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the commit is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="8598c-168">有关详细信息，请参阅 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="8598c-168">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="8598c-169">事务是延迟持久事务，除非数据库选项 DELAYED_DURABLITY = DISABLED 有效（在这种情况下，提交是同步的，因而是完全持久事务）。</span><span class="sxs-lookup"><span data-stu-id="8598c-169">The transaction is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the commit is synchronous and thus fully durable.</span></span>  <span data-ttu-id="8598c-170">有关详细信息，请参阅 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="8598c-170">See [Database level control](#database-level-control) for more information.</span></span>  
  
 <span data-ttu-id="8598c-171">**示例代码：**</span><span class="sxs-lookup"><span data-stu-id="8598c-171">**Example Code:**</span></span>  
  
```sql  
CREATE PROCEDURE <procedureName> ...  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    DELAYED_DURABILITY = ON,  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English'  
    ...  
)  
END  
```  
  
### <a name="table-1-durability-in-atomic-blocks"></a><span data-ttu-id="8598c-172">表 1：原子块中的持续性</span><span class="sxs-lookup"><span data-stu-id="8598c-172">Table 1: Durability in Atomic Blocks</span></span>  
  
|<span data-ttu-id="8598c-173">原子块持续性选项</span><span class="sxs-lookup"><span data-stu-id="8598c-173">Atomic block durability option</span></span>|<span data-ttu-id="8598c-174">没有现有事务</span><span class="sxs-lookup"><span data-stu-id="8598c-174">No existing transaction</span></span>|<span data-ttu-id="8598c-175">事务正在进行（完全或延迟持久）</span><span class="sxs-lookup"><span data-stu-id="8598c-175">Transaction in process (fully or delayed durable)</span></span>|  
|------------------------------------|-----------------------------|---------------------------------------------------------|  
|`DELAYED_DURABILITY = OFF`|<span data-ttu-id="8598c-176">原子块启动新的完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-176">Atomic block starts a new fully durable transaction.</span></span>|<span data-ttu-id="8598c-177">原子块在现有事务中创建一个保存点，然后开始新事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-177">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
|`DELAYED_DURABILITY = ON`|<span data-ttu-id="8598c-178">原子块启动新的延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-178">Atomic block starts a new delayed durable transaction.</span></span>|<span data-ttu-id="8598c-179">原子块在现有事务中创建一个保存点，然后开始新事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-179">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
  
### <a name="commit-level-control---t-sql"></a><span data-ttu-id="8598c-180">提交级别控制- (T-sql) </span><span class="sxs-lookup"><span data-stu-id="8598c-180">COMMIT level control - (T-SQL)</span></span>
 <span data-ttu-id="8598c-181">COMMIT 语法已扩展，您可以强制实施延迟事务持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-181">The COMMIT syntax is extended so you can force delayed transaction durability.</span></span> <span data-ttu-id="8598c-182">如果 DELAYED_DURABILITY 在数据库级别设置为 DISABLED 或 FORCED（请参阅上文），则忽略此 COMMIT 选项。</span><span class="sxs-lookup"><span data-stu-id="8598c-182">If DELAYED_DURABILITY is DISABLED or FORCED at the database level (see above) this COMMIT option is ignored.</span></span>  
  
```sql  
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
  
```  
  
 `OFF`  
 <span data-ttu-id="8598c-183">[默认] 事务 COMMIT 是完全持久事务，除非数据库选项 DELAYED_DURABLITY = FORCED 有效（在这种情况下，提交是异步的，因而是延迟持久事务）。</span><span class="sxs-lookup"><span data-stu-id="8598c-183">[default] The transaction COMMIT is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the COMMIT is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="8598c-184">有关详细信息，请参阅 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="8598c-184">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="8598c-185">事务 COMMIT 是延迟持久事务，除非数据库选项 DELAYED_DURABLITY = DISABLED 有效（在这种情况下，提交是同步的，因而是完全持久事务）。</span><span class="sxs-lookup"><span data-stu-id="8598c-185">The transaction COMMIT is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the COMMIT is synchronous and thus fully durable.</span></span> <span data-ttu-id="8598c-186">有关详细信息，请参阅 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="8598c-186">See [Database level control](#database-level-control) for more information.</span></span>  
  
### <a name="summary-of-options-and-their-interactions"></a><span data-ttu-id="8598c-187">各个选项及其交互的总结</span><span class="sxs-lookup"><span data-stu-id="8598c-187">Summary of options and their interactions</span></span>  
 <span data-ttu-id="8598c-188">此表总结了数据库级别延迟持续性设置与提交级别设置之间的交互。</span><span class="sxs-lookup"><span data-stu-id="8598c-188">This table summarizes the interactions between database level delayed durability settings and commit level settings.</span></span> <span data-ttu-id="8598c-189">数据库级别设置始终优先于提交级别设置。</span><span class="sxs-lookup"><span data-stu-id="8598c-189">Database level settings always take precedence over commit level settings.</span></span>  
  
|<span data-ttu-id="8598c-190">提交设置/数据库设置</span><span class="sxs-lookup"><span data-stu-id="8598c-190">COMMIT setting/Database setting</span></span>|<span data-ttu-id="8598c-191">DELAYED_DURABILITY = DISABLED</span><span class="sxs-lookup"><span data-stu-id="8598c-191">DELAYED_DURABILITY = DISABLED</span></span>|<span data-ttu-id="8598c-192">DELAYED_DURABILITY = ALLOWED</span><span class="sxs-lookup"><span data-stu-id="8598c-192">DELAYED_DURABILITY = ALLOWED</span></span>|<span data-ttu-id="8598c-193">DELAYED_DURABILITY = FORCED</span><span class="sxs-lookup"><span data-stu-id="8598c-193">DELAYED_DURABILITY = FORCED</span></span>|  
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|  
|<span data-ttu-id="8598c-194">`DELAYED_DURABILITY = OFF` 数据库级事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-194">`DELAYED_DURABILITY = OFF` Database level transactions.</span></span>|<span data-ttu-id="8598c-195">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-195">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-196">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-196">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-197">事务是延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-197">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="8598c-198">`DELAYED_DURABILITY = ON` 数据库级事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-198">`DELAYED_DURABILITY = ON` Database level transactions.</span></span>|<span data-ttu-id="8598c-199">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-199">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-200">事务是延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-200">Transaction is delayed durable.</span></span>|<span data-ttu-id="8598c-201">事务是延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-201">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="8598c-202">`DELAYED_DURABILITY = OFF` 跨数据库或分布式事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-202">`DELAYED_DURABILITY = OFF` Cross database or distributed transaction.</span></span>|<span data-ttu-id="8598c-203">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-203">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-204">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-204">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-205">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-205">Transaction is fully durable.</span></span>|  
|<span data-ttu-id="8598c-206">`DELAYED_DURABILITY = ON` 跨数据库或分布式事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-206">`DELAYED_DURABILITY = ON` Cross database or distributed transaction.</span></span>|<span data-ttu-id="8598c-207">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-207">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-208">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-208">Transaction is fully durable.</span></span>|<span data-ttu-id="8598c-209">事务是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-209">Transaction is fully durable.</span></span>|  
  
## <a name="how-to-force-a-transaction-log-flush"></a><span data-ttu-id="8598c-210">如何强制执行事务日志刷新</span><span class="sxs-lookup"><span data-stu-id="8598c-210">How to force a transaction log flush</span></span>  
 <span data-ttu-id="8598c-211">有两种方法可以强制将事务日志刷新到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-211">There are two means to force flush the transaction log to disk.</span></span>  
  
-   <span data-ttu-id="8598c-212">执行任何可改变相应数据库的完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-212">Execute any fully durable transaction that alters the same database.</span></span> <span data-ttu-id="8598c-213">这会强制将之前提交的所有延迟持续性事务的日志记录刷新到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-213">This forces a flush of the log records of all preceding committed delayed durability transactions to disk.</span></span>  
  
-   <span data-ttu-id="8598c-214">执行系统存储过程 `sp_flush_log`。</span><span class="sxs-lookup"><span data-stu-id="8598c-214">Execute the system stored procedure `sp_flush_log`.</span></span> <span data-ttu-id="8598c-215">此过程会强制将之前提交的所有延迟持久事务的日志记录刷新到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-215">This procedure forces a flush of the log records of all preceding committed delayed durable transactions to disk.</span></span> <span data-ttu-id="8598c-216">有关详细信息，请参阅 [sys.sp_flush_log (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8598c-216">For more information see [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql).</span></span>  
  
##  <a name="delayed-durability-and-other-sql-server-features"></a><span data-ttu-id="8598c-217">延迟持续性和其他 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="8598c-217">Delayed durability and other SQL Server features</span></span>  
 <span data-ttu-id="8598c-218">**更改跟踪和更改数据捕获**</span><span class="sxs-lookup"><span data-stu-id="8598c-218">**Change tracking and change data capture**</span></span>  
 <span data-ttu-id="8598c-219">具有更改跟踪属性的所有事务都是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-219">All transactions with change tracking are fully durable.</span></span> <span data-ttu-id="8598c-220">如果一个事务对支持更改跟踪的表执行了任何写入操作，则该事务具有更改跟踪属性。</span><span class="sxs-lookup"><span data-stu-id="8598c-220">A transaction has the change tracking property if it does any write operations to tables that are enabled for change tracking.</span></span> <span data-ttu-id="8598c-221">使用变更数据捕获 (CDC) 的数据库不支持使用延迟的持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-221">The use of delayed durability is not supported for databases which use change data capture (CDC).</span></span>   
  
 <span data-ttu-id="8598c-222">**崩溃恢复**</span><span class="sxs-lookup"><span data-stu-id="8598c-222">**Crash recovery**</span></span>  
 <span data-ttu-id="8598c-223">一致性可得到保证，但已提交的延迟持久事务的一些更改可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="8598c-223">Consistency is guaranteed, but some changes from delayed durable transactions that have committed may be lost.</span></span>  
  
 <span data-ttu-id="8598c-224">**跨数据库和 DTC**</span><span class="sxs-lookup"><span data-stu-id="8598c-224">**Cross-database and DTC**</span></span>  
 <span data-ttu-id="8598c-225">如果事务跨数据库或是分布式事务，则无论数据库或事务提交设置如何，它都是完全持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-225">If a transaction is cross-database or distributed, if is fully durable, regardless of any database or transaction commit setting.</span></span>  
  
 <span data-ttu-id="8598c-226">**AlwaysOn 可用性组和镜像**</span><span class="sxs-lookup"><span data-stu-id="8598c-226">**Always On Availability Groups and Mirroring**</span></span>  
 <span data-ttu-id="8598c-227">延迟持久事务并不能保证主数据库或任何辅助数据库的持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-227">Delayed durable transactions do not guarantee any durability on either the primary or any of the secondaries.</span></span> <span data-ttu-id="8598c-228">此外，它们也不保证了解辅助数据库的事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-228">In addition, they do not guarantee any knowledge about the transaction at the secondary.</span></span> <span data-ttu-id="8598c-229">提交后，在从同步辅助数据接收到任何确认之前，控制权就会归还客户端。</span><span class="sxs-lookup"><span data-stu-id="8598c-229">After commit, control is returned to the client before any acknowledgement is received from any synchronous secondary.</span></span>  
  
 <span data-ttu-id="8598c-230">**故障转移群集**</span><span class="sxs-lookup"><span data-stu-id="8598c-230">**Failover clustering**</span></span>  
 <span data-ttu-id="8598c-231">某些延迟持久事务写入可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="8598c-231">Some delayed durable transaction writes might be lost.</span></span>  
  
 <span data-ttu-id="8598c-232">**事务复制**</span><span class="sxs-lookup"><span data-stu-id="8598c-232">**Transaction Replication**</span></span>  
 <span data-ttu-id="8598c-233">事务复制不支持延迟持久事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-233">Delayed durable transactions is not supported with Transactional Replication.</span></span>  
  
 <span data-ttu-id="8598c-234">**日志传送**</span><span class="sxs-lookup"><span data-stu-id="8598c-234">**Log shipping**</span></span>  
 <span data-ttu-id="8598c-235">传送的日志中仅包含已成为持久事务的事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-235">Only transactions that have been made durable are included in the log that is shipped.</span></span>  
  
 <span data-ttu-id="8598c-236">**日志备份**</span><span class="sxs-lookup"><span data-stu-id="8598c-236">**Log Backup**</span></span>  
 <span data-ttu-id="8598c-237">备份中仅包含已成为持久事务的事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-237">Only transactions that have been made durable are included in the backup.</span></span>  
  
## <a name="when-can-i-lose-data"></a><span data-ttu-id="8598c-238">在什么情况下会丢失数据？</span><span class="sxs-lookup"><span data-stu-id="8598c-238">When can I lose data?</span></span>  
 <span data-ttu-id="8598c-239">如果你对表实施延迟持续性，则应了解某些情况会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="8598c-239">If you implement delayed durability on any of your tables, you should understand that certain circumstances can lead to data loss.</span></span> <span data-ttu-id="8598c-240">如果无法容忍任何数据丢失，则不要对表使用延迟持续性。</span><span class="sxs-lookup"><span data-stu-id="8598c-240">If you cannot tolerate any data loss, you should not use delayed durability on your tables.</span></span>  
  
### <a name="catastrophic-events"></a><span data-ttu-id="8598c-241">灾难性事件</span><span class="sxs-lookup"><span data-stu-id="8598c-241">Catastrophic events</span></span>  
 <span data-ttu-id="8598c-242">发生灾难性事件（如服务器崩溃）时，将丢失已提交但未保存到磁盘的所有事务的数据。</span><span class="sxs-lookup"><span data-stu-id="8598c-242">In the case of a catastrophic event, like a server crash, you will lose the data for all committed transactions that have not been saved to disk.</span></span> <span data-ttu-id="8598c-243">根据数据库中的任何表（持久内存优化或基于磁盘）执行完全持久的事务时，或调用 `sp_flush_log` 时，延迟的持久事务保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="8598c-243">Delayed durable transactions are saved to disk whenever a fully durable transaction is executed against any table (durable memory-optimized or disk-based) in the database, or `sp_flush_log` is called.</span></span> <span data-ttu-id="8598c-244">如果你在使用延迟的持久事务，那么你可能想要在数据库中创建一个小型表，你可定期更新该表或调用 `sp_flush_log` ，以保存所有未完成的已提交事务。</span><span class="sxs-lookup"><span data-stu-id="8598c-244">If you are using delayed durable transactions, you may want to create a small table in the database that you can periodically update or periodically call `sp_flush_log` to save all outstanding committed transactions.</span></span> <span data-ttu-id="8598c-245">事务日志还会在变满时刷新，但这难以预测，也无法进行控制。</span><span class="sxs-lookup"><span data-stu-id="8598c-245">The transaction log also flushes whenever it becomes full, but that is hard to predict and impossible to control.</span></span>  
  
### <a name="sql-server-shutdown-and-restart"></a><span data-ttu-id="8598c-246">SQL Server 关闭并重新启动</span><span class="sxs-lookup"><span data-stu-id="8598c-246">SQL Server shutdown and restart</span></span>  
 <span data-ttu-id="8598c-247">对于延迟的持久性， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的意外关闭和预期关闭/重新启动没有区别。</span><span class="sxs-lookup"><span data-stu-id="8598c-247">For delayed durability, there is no difference between an unexpected shutdown and an expected shutdown/restart of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8598c-248">与灾难性事件类似，应制定针对数据丢失的计划。</span><span class="sxs-lookup"><span data-stu-id="8598c-248">Like catastrophic events, you should plan for data loss.</span></span> <span data-ttu-id="8598c-249">在进行计划的关闭/重新启动时，一些尚未写入磁盘的事务可能会首先保存到磁盘，但不应对其进行计划。</span><span class="sxs-lookup"><span data-stu-id="8598c-249">In a planned shutdown/restart some transactions that have not been written to disk may first be saved to disk, but you should not plan on it.</span></span> <span data-ttu-id="8598c-250">虽然计划了关闭/重启，但无论是否计划，都会像灾难性事件一样丢失数据。</span><span class="sxs-lookup"><span data-stu-id="8598c-250">Plan as though a shutdown/restart, whether planned or unplanned, loses the data the same as a catastrophic event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8598c-251">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8598c-251">See Also</span></span>  
 <span data-ttu-id="8598c-252">[事务隔离级别](../../database-engine/transaction-isolation-levels.md) </span><span class="sxs-lookup"><span data-stu-id="8598c-252">[Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) </span></span>  
 [<span data-ttu-id="8598c-253">内存优化表事务隔离级别准则</span><span class="sxs-lookup"><span data-stu-id="8598c-253">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)  
  
  
