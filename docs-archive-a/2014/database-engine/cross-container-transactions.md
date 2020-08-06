---
title: 跨容器事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28437f0903459616a574e713c0f138e8bb459870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586949"
---
# <a name="cross-container-transactions"></a><span data-ttu-id="90286-102">交叉容器事务</span><span class="sxs-lookup"><span data-stu-id="90286-102">Cross-Container Transactions</span></span>
  <span data-ttu-id="90286-103">交叉容器事务是隐式或显式用户事务，这些事务包含对本机编译存储过程的调用或对内存优化表的操作。</span><span class="sxs-lookup"><span data-stu-id="90286-103">Cross-container transactions are either implicit or explicit user transactions that include calls to natively-compiled stored procedures or operations on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="90286-104">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，对存储过程的调用不会启动事务。</span><span class="sxs-lookup"><span data-stu-id="90286-104">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], calls to stored procedures do not initiate a transaction.</span></span> <span data-ttu-id="90286-105">在自动提交模式下执行本机编译过程（不在用户事务的上下文中）不被视为交叉容器事务。</span><span class="sxs-lookup"><span data-stu-id="90286-105">Executions of natively compiled procedures in autocommit mode (not in the context of a user transaction) are not considered cross-container transactions.</span></span>  
  
 <span data-ttu-id="90286-106">引用内存优化表的任何解释型查询都被视为交叉容器事务的一部分，而无论是从显式或隐式事务中执行，还是在自动提交模式下执行。</span><span class="sxs-lookup"><span data-stu-id="90286-106">Any interpreted query that references memory-optimized tables is considered a part of a cross-container transaction, whether executed from an explicit or implicit transaction or in auto-commit mode.</span></span>  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a><span data-ttu-id="90286-107">单个操作的隔离</span><span class="sxs-lookup"><span data-stu-id="90286-107">Isolation of Individual Operations</span></span>  
 <span data-ttu-id="90286-108">每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事务都有一个隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-108">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] transaction has an isolation level.</span></span> <span data-ttu-id="90286-109">默认隔离级别为 Read Committed。</span><span class="sxs-lookup"><span data-stu-id="90286-109">The default isolation level is Read Committed.</span></span> <span data-ttu-id="90286-110">若要使用不同的隔离级别，可以使用 "[设置事务隔离级别 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)设置隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-110">To use a different isolation level, you can set the isolation level using [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="90286-111">内存优化表和基于磁盘的表上的操作常常需要采用不同的隔离级别执行。</span><span class="sxs-lookup"><span data-stu-id="90286-111">It is often necessary to perform operations on memory-optimized tables at a different isolation level than operations on disk-based tables.</span></span> <span data-ttu-id="90286-112">在事务中，可为一组语句或单个读取操作设置不同的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-112">In a transaction, it is possible to set a different isolation level for a collection of statements or for an individual read operation.</span></span>  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a><span data-ttu-id="90286-113">指定单个操作的隔离级别</span><span class="sxs-lookup"><span data-stu-id="90286-113">Specifying the Isolation Level of Individual Operations</span></span>  
 <span data-ttu-id="90286-114">若要为事务中的一组语句设置不同的隔离级别，可以使用 `SET TRANSACTION ISOLATION LEVEL`。</span><span class="sxs-lookup"><span data-stu-id="90286-114">To set a different isolation level for a set of statements in a transaction, you can use `SET TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="90286-115">下面的事务示例使用可序列化隔离级别作为默认级别。</span><span class="sxs-lookup"><span data-stu-id="90286-115">The following example of a transaction uses the serializable isolation level as default.</span></span> <span data-ttu-id="90286-116">对 t3、t2 和 t1 的插入和选择操作在“可重复读”隔离级别下执行。</span><span class="sxs-lookup"><span data-stu-id="90286-116">The insert and select operations on t3, t2, and t1 are executed under repeatable read isolation.</span></span>  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 <span data-ttu-id="90286-117">若要为各个读取操作分别设置不同于事务默认级别的隔离级别，可以使用表提示（例如，可序列化）。</span><span class="sxs-lookup"><span data-stu-id="90286-117">To set an isolation level for individual read operations that is different from the transaction default, you can use a table hint (for example, serializable).</span></span> <span data-ttu-id="90286-118">每个选择操作对应于一个读取操作，每个更新操作和每个删除操作对应于一个读取操作，因为始终需要先读取行才能进行更新或删除。</span><span class="sxs-lookup"><span data-stu-id="90286-118">Every select corresponds to a read operation and every update and every delete corresponds to a read, because the row always needs to be read before it can be updated or deleted.</span></span> <span data-ttu-id="90286-119">插入操作没有隔离级别，因为在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中始终要隔离写操作。</span><span class="sxs-lookup"><span data-stu-id="90286-119">Insert operations do not have an isolation level, because writes are always isolated in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="90286-120">在下面的示例中，事务的默认隔离级别是“已提交读”，但在可序列化隔离级别下访问表 t1，在快照隔离级别下访问表 t2。</span><span class="sxs-lookup"><span data-stu-id="90286-120">In the following example, the default isolation level for the transaction is read committed, but table t1 is accessed under serializable and t2 under snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a><span data-ttu-id="90286-121">单个操作的隔离语义</span><span class="sxs-lookup"><span data-stu-id="90286-121">Isolation Semantics for Individual Operations</span></span>  
 <span data-ttu-id="90286-122">可序列化事务 T 在完全隔离下执行。</span><span class="sxs-lookup"><span data-stu-id="90286-122">A serializable transaction T is executed in complete isolation.</span></span> <span data-ttu-id="90286-123">此事务执行时，就好像其他每个事务要么都在 T 启动之前提交，要么都在 T 提交之后启动。</span><span class="sxs-lookup"><span data-stu-id="90286-123">It is as if every other transaction has either committed before T started, or is started after T committed.</span></span> <span data-ttu-id="90286-124">当一个事务中的不同操作具有不同隔离级别时，情况会变得更加复杂。</span><span class="sxs-lookup"><span data-stu-id="90286-124">It becomes more complex when different operations in a transaction have different isolation levels.</span></span>  
  
 <span data-ttu-id="90286-125">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [&#40;transact-sql&#41;的 "设置事务隔离级别](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)" 中说明了中的事务隔离级别的一般语义以及锁定的含义。</span><span class="sxs-lookup"><span data-stu-id="90286-125">The general semantics of the transaction isolation levels in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], along with the implications on locking, is explained in [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="90286-126">对于不同操作可能具有不同隔离级别的交叉容器事务，您需要理解各个读取操作的隔离语义。</span><span class="sxs-lookup"><span data-stu-id="90286-126">For cross-container transactions where different operations may have different isolation levels, you need to understand the semantics of isolation of individual read operations.</span></span> <span data-ttu-id="90286-127">将始终对写操作进行隔离。</span><span class="sxs-lookup"><span data-stu-id="90286-127">Write operations are always isolated.</span></span> <span data-ttu-id="90286-128">不同事务中的写操作不能相互影响。</span><span class="sxs-lookup"><span data-stu-id="90286-128">Writes in different transactions cannot impact each other.</span></span>  
  
 <span data-ttu-id="90286-129">数据读取操作返回很多符合筛选条件的行。</span><span class="sxs-lookup"><span data-stu-id="90286-129">A data read operation returns a number of rows that satisfy a filter condition.</span></span>  
  
 <span data-ttu-id="90286-130">读取作为事务的一部分执行。可以在中理解读取操作的隔离级别，</span><span class="sxs-lookup"><span data-stu-id="90286-130">Reads are performed as part of a transaction T. Isolation levels for read operations can be understood in terms of,</span></span>  
  
 <span data-ttu-id="90286-131">提交状态</span><span class="sxs-lookup"><span data-stu-id="90286-131">Commit Status</span></span>  
 <span data-ttu-id="90286-132">提交状态指数据读取是否能够提交。</span><span class="sxs-lookup"><span data-stu-id="90286-132">Commit status refers to whether the data read is guaranteed to be committed.</span></span>  
  
 <span data-ttu-id="90286-133">（事务）一致性</span><span class="sxs-lookup"><span data-stu-id="90286-133">(Transactional) Consistency</span></span>  
 <span data-ttu-id="90286-134">一组读取操作的事务一致性是指行版本读取是否都能保证包括来自完全相同的一组事务的更新。</span><span class="sxs-lookup"><span data-stu-id="90286-134">Transactional consistency for a set of reads refers to whether the row versions read are all guaranteed to include updates from precisely the same set of transactions.</span></span>  
  
 <span data-ttu-id="90286-135">系统提供给事务 T 的有关数据读取的稳定性保证。</span><span class="sxs-lookup"><span data-stu-id="90286-135">Stability guarantees the system gives to transaction T about the data read.</span></span>  
 <span data-ttu-id="90286-136">稳定性是指事务的读取是否可重复。</span><span class="sxs-lookup"><span data-stu-id="90286-136">Stability refers to whether the transaction's reads are repeatable.</span></span> <span data-ttu-id="90286-137">也就是，重复读取操作是否始终返回相同的行和行版本？</span><span class="sxs-lookup"><span data-stu-id="90286-137">That is, if the reads were repeated would they return the same rows and row versions?</span></span>  
  
 <span data-ttu-id="90286-138">特定保证是指事务的逻辑结束时间。</span><span class="sxs-lookup"><span data-stu-id="90286-138">Certain guarantees refer to the logical end time of the transaction.</span></span> <span data-ttu-id="90286-139">一般情况下，逻辑结束时间是将事务提交到数据库的时间。</span><span class="sxs-lookup"><span data-stu-id="90286-139">In general, the logical end time is the time the transaction is committed to the database.</span></span> <span data-ttu-id="90286-140">如果事务访问内存优化表，则从技术上看，逻辑结束时间就是验证阶段的开始时间。</span><span class="sxs-lookup"><span data-stu-id="90286-140">If memory-optimized tables are accessed by the transaction, the logical end time is technically the beginning of the validation phase.</span></span> <span data-ttu-id="90286-141"> (有关详细信息，请参阅[内存优化表](../relational-databases/in-memory-oltp/memory-optimized-tables.md)中的事务的事务生存期讨论。</span><span class="sxs-lookup"><span data-stu-id="90286-141">(For more information, see the transaction lifetime discussion in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="90286-142">无论隔离级别如何，事务 (T) 始终能看到自身的更新：</span><span class="sxs-lookup"><span data-stu-id="90286-142">Regardless of isolation level, a transaction (T) always sees its own updates:</span></span>  
  
 <span data-ttu-id="90286-143">READ UNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="90286-143">READ UNCOMMITTED</span></span>  
 <span data-ttu-id="90286-144">数据读取可能未提交、不一致或不稳定。</span><span class="sxs-lookup"><span data-stu-id="90286-144">The data read may neither be committed, consistent, or stable.</span></span> <span data-ttu-id="90286-145">不过，它将包含由 T 执行的更早的写操作。</span><span class="sxs-lookup"><span data-stu-id="90286-145">However, it will include earlier write operations done by T.</span></span>  
  
 <span data-ttu-id="90286-146">READ COMMITTED</span><span class="sxs-lookup"><span data-stu-id="90286-146">READ COMMITTED</span></span>  
 <span data-ttu-id="90286-147">将提交数据读取。</span><span class="sxs-lookup"><span data-stu-id="90286-147">The data read will be committed.</span></span>  
  
 <span data-ttu-id="90286-148">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="90286-148">SNAPSHOT</span></span>  
 <span data-ttu-id="90286-149">由 T 在快照隔离下执行的所有读取操作都具有相同的逻辑读取时间，即事务开始的时间。</span><span class="sxs-lookup"><span data-stu-id="90286-149">All read operations performed by T under snapshot isolation have the same logical read time, which is the beginning of the transaction.</span></span> <span data-ttu-id="90286-150">从该逻辑读取时间起，可以保证数据读取得到提交并保持一致。</span><span class="sxs-lookup"><span data-stu-id="90286-150">The data read is guaranteed to be committed and consistent as of the logical read time.</span></span> <span data-ttu-id="90286-151">从原始读取时间起，重复执行的读取操作可以保证返回相同的结果。</span><span class="sxs-lookup"><span data-stu-id="90286-151">Repeating a read as of the original read time is guaranteed to return the same result.</span></span>  
  
 <span data-ttu-id="90286-152">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="90286-152">REPEATABLE READ</span></span>  
 <span data-ttu-id="90286-153">到事务的逻辑结束时间，可以保证数据读取得到提交并保持稳定。</span><span class="sxs-lookup"><span data-stu-id="90286-153">The data read is guaranteed to be committed and stable up to the logical end time of the transaction.</span></span>  
  
 <span data-ttu-id="90286-154">SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="90286-154">SERIALIZABLE</span></span>  
 <span data-ttu-id="90286-155">对于所有由 T 执行的可序列化读取操作，都保证可重复读取和虚拟化一致性的所有保证。规避方法意味着扫描操作仅返回由 T 写入的其他行，但不返回其他事务写入的行。</span><span class="sxs-lookup"><span data-stu-id="90286-155">All guarantees of REPEATABLE READ plus phantom avoidance and transactional consistency with respect to all serializable read operations performed by T. Phantom avoidance means that the scan operation can only return additional rows that were written by T, but no rows that were written by other transactions.</span></span>  
  
 <span data-ttu-id="90286-156">请考虑以下事务：</span><span class="sxs-lookup"><span data-stu-id="90286-156">Consider the following transaction,</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 <span data-ttu-id="90286-157">此事务在“已提交读”隔离级别下删除 t3 的所有行，在可序列化隔离级别下将所有行从 t1 复制到 t3，然后将 t1 和 t3 进行比较。</span><span class="sxs-lookup"><span data-stu-id="90286-157">This transaction deletes all rows from t3 under read committed isolation, copies all rows from t1 to t3 under serializable isolation, and then compares t1 and t3.</span></span> <span data-ttu-id="90286-158">t3 表在清空后可能添加了一些行 [不在 t1 中]。</span><span class="sxs-lookup"><span data-stu-id="90286-158">Some rows [not in t1] may have been added to t3 since the table was emptied.</span></span> <span data-ttu-id="90286-159">由于 t1 副本是可序列化的，因此该表中没有添加任何行。</span><span class="sxs-lookup"><span data-stu-id="90286-159">No rows were added to t1 as the copy was serializable.</span></span>  
  
 <span data-ttu-id="90286-160">虽然在事务结束时从 t1 读取在语法上属于“已提交读”隔离级别，但在效果上是可序列化隔离级别，原因是事务中之前在可序列化隔离下执行过相同的读操作：可序列化性保证随后在事务中任何较晚时刻执行读操作都会返回相同的行。</span><span class="sxs-lookup"><span data-stu-id="90286-160">Although the read from t1 at the end of the transaction is syntactically read committed, it is effectively serializable, because the same read was performed earlier in the transaction under serializable isolation: serializability guarantees that if the read is performed at any later point in the transaction, the same rows are returned.</span></span>  
  
## <a name="cross-container-transactions-and-isolation-levels"></a><span data-ttu-id="90286-161">交叉容器事务和隔离级别</span><span class="sxs-lookup"><span data-stu-id="90286-161">Cross-Container Transactions and Isolation Levels</span></span>  
 <span data-ttu-id="90286-162">可将交叉容器事务视为具有两个方面：基于磁盘的方面（对于基于磁盘的表的操作）和内存优化的方面（对于内存优化的表的操作）。</span><span class="sxs-lookup"><span data-stu-id="90286-162">A cross-container transaction can be seen as having two sides: a disk-based side (for operations on disk-based tables) and a memory-optimized side (for operations on memory-optimized tables).</span></span> <span data-ttu-id="90286-163">这两方面可以有不同的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-163">These two sides may have different isolation levels.</span></span> <span data-ttu-id="90286-164">实际上，每个方面的各个读取操作可以分别有不同的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-164">In fact, individual read operations on each side may have different isolation levels.</span></span>  
  
 <span data-ttu-id="90286-165">给定事务 T 的基于磁盘的方面在满足以下条件之一的情况下达到特定隔离级别 X：</span><span class="sxs-lookup"><span data-stu-id="90286-165">The disk-based side of a given transaction T reaches a certain isolation level X if one of the following conditions is met:</span></span>  
  
-   <span data-ttu-id="90286-166">它以 X 开始。也就是说，会话默认值为 X，原因是执行了 `SET TRANSACTION ISOLATION LEVEL` ，或者它是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 默认值。</span><span class="sxs-lookup"><span data-stu-id="90286-166">It starts in X. That is, the session default was X, either because you executed `SET TRANSACTION ISOLATION LEVEL`, or it is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default.</span></span>  
  
-   <span data-ttu-id="90286-167">在该事务执行期间，默认隔离级别通过 `SET TRANSACTION ISOLATION LEVEL` 更改为 X。</span><span class="sxs-lookup"><span data-stu-id="90286-167">During the transaction, the default isolation level is changed to X using `SET TRANSACTION ISOLATION LEVEL`.</span></span>  
  
-   <span data-ttu-id="90286-168">对基于磁盘的表的读取操作通过语法 `WITH (X)` 在隔离级别 X 下执行。</span><span class="sxs-lookup"><span data-stu-id="90286-168">A read operation on a disk-based table is executed under isolation level X, using the syntax `WITH (X)`.</span></span>  
  
 <span data-ttu-id="90286-169">如果在 T 执行期间，在隔离级别 Y 下对内存优化的表或任何本机编译的存储过程执行任何读取操作，则 T 的内存优化的方面达到隔离级别 Y。</span><span class="sxs-lookup"><span data-stu-id="90286-169">The memory-optimized side of T reaches an isolation level Y if during execution of T, any read operation on a memory-optimized table or any natively compiled stored procedure is executed under isolation level Y.</span></span>  
  
 <span data-ttu-id="90286-170">请以下面的事务为例。</span><span class="sxs-lookup"><span data-stu-id="90286-170">Consider the following transaction as an example.</span></span> <span data-ttu-id="90286-171">在此，t1 和 t2 是基于磁盘的表，而 t3 和 t4 是内存优化表。</span><span class="sxs-lookup"><span data-stu-id="90286-171">Here, t1 and t2 are disk-based tables and t3 and t4 are memory-optimized tables.</span></span>  
  
 <span data-ttu-id="90286-172">该事务基于磁盘的方面由于在“已提交读”隔离级别启动，因此达到该隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-172">The disk-based side of the transaction reaches the isolation level read committed, because it starts in that level.</span></span> <span data-ttu-id="90286-173">基于磁盘的方面还达到“可重复读”级别，因为第一个读取操作是在该隔离级别下执行的。</span><span class="sxs-lookup"><span data-stu-id="90286-173">The disk-based side also reaches repeatable read, because the first read operation is executed under that isolation level.</span></span> <span data-ttu-id="90286-174">事务结束处的删除操作在“已提交读”隔离级别执行，因此不会引入新的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-174">The delete at the end of the transaction is executed under read committed isolation level, and so does not introduce a new isolation level.</span></span>  
  
 <span data-ttu-id="90286-175">该事务的内存优化的方面可达到以下两个级别之一：如果 condition1 为 true，则达到可序列化级别；如果 condition1 为 false，则内存优化的方面只达到快照隔离级别。</span><span class="sxs-lookup"><span data-stu-id="90286-175">The memory-optimized side of the transaction can reach one of two levels: if condition1 is true, it reaches serializable, while if it is false, the memory-optimized side reaches only snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a><span data-ttu-id="90286-176">交叉容器事务所支持的隔离级别</span><span class="sxs-lookup"><span data-stu-id="90286-176">Supported Isolation Levels for Cross-Container Transactions</span></span>  
 <span data-ttu-id="90286-177">对于交叉容器事务中为内存优化表上的操作所应用的隔离级别，存在一定的限制。</span><span class="sxs-lookup"><span data-stu-id="90286-177">There are limitations on the isolation levels used with operations on memory-optimized tables in cross-container transactions.</span></span>  
  
 <span data-ttu-id="90286-178">内存优化表支持隔离级别 SNAPSHOT、REPEATABLE READ 和 SERIALIZABLE。</span><span class="sxs-lookup"><span data-stu-id="90286-178">Memory-optimized tables support the isolation levels SNAPSHOT, REPEATABLE READ, and SERIALIZABLE.</span></span> <span data-ttu-id="90286-179">对于自动提交事务，内存优化表支持隔离级别 READ COMMITTED。</span><span class="sxs-lookup"><span data-stu-id="90286-179">For autocommit transactions, memory-optimized tables support the isolation level READ COMMITTED.</span></span>  
  
 <span data-ttu-id="90286-180">支持以下方案：</span><span class="sxs-lookup"><span data-stu-id="90286-180">The following scenarios are supported:</span></span>  
  
-   <span data-ttu-id="90286-181">READ UNCOMMITTED、READ COMMITTED 和 READ_COMMITTED_SNAPSHOT 交叉容器事务可以在 SNAPSHOT、REPEATABLE READ 和 SERIALIZABLE 隔离级别下访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="90286-181">READ UNCOMMITTED, READ COMMITTED, and READ_COMMITTED_SNAPSHOT cross-container transactions can access memory-optimized tables under SNAPSHOT, REPEATABLE READ, and SERIALIZABLE isolation.</span></span> <span data-ttu-id="90286-182">READ COMMITTED 保证对该事务的保留；由该事务读取的所有行都已提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="90286-182">The READ COMMITTED guarantee holds for the transaction; all rows read by the transaction have been committed to the database.</span></span>  
  
-   <span data-ttu-id="90286-183">REPEATABLE READ 和 SERIALIZABLE 事务可以在 SNAPSHOT 隔离级别下访问内存优化表。</span><span class="sxs-lookup"><span data-stu-id="90286-183">REPEATABLE READ and SERIALIZABLE transactions can access memory-optimized tables under SNAPSHOT isolation.</span></span>  
  
## <a name="read-only-cross-container-transactions"></a><span data-ttu-id="90286-184">只读交叉容器事务</span><span class="sxs-lookup"><span data-stu-id="90286-184">Read-only Cross-Container Transactions</span></span>  
 <span data-ttu-id="90286-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中大多数只读事务将在提交时回滚。</span><span class="sxs-lookup"><span data-stu-id="90286-185">Most read-only transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are rolled back at commit time.</span></span> <span data-ttu-id="90286-186">由于没有要提交到数据库的更改，系统直接释放该事务所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="90286-186">Because there are no changes to commit to the database, the system simply frees the resources used by the transaction.</span></span> <span data-ttu-id="90286-187">对于基于磁盘的只读事务，此时会释放由该事务持有的所有锁。</span><span class="sxs-lookup"><span data-stu-id="90286-187">For read-only disk-based transactions, all locks taken by the transaction are released at this time.</span></span> <span data-ttu-id="90286-188">对于只占用一个本机编译过程执行的只读内存优化事务，不会执行验证。</span><span class="sxs-lookup"><span data-stu-id="90286-188">For read-only memory-optimized transactions that span a single natively compiled procedure execution, no validation is performed.</span></span>  
  
 <span data-ttu-id="90286-189">该事务结束时，自动提交模式下的交叉容器只读事务直接回滚。</span><span class="sxs-lookup"><span data-stu-id="90286-189">Cross-container, read-only transactions in autocommit mode are simply rolled back at the end of the transaction.</span></span> <span data-ttu-id="90286-190">不执行任何验证。</span><span class="sxs-lookup"><span data-stu-id="90286-190">No validation is performed.</span></span>  
  
 <span data-ttu-id="90286-191">如果显式或隐式交叉容器只读事务在 REPEATABLE READ 或 SERIALIZABLE 隔离级别下访问内存优化表，则该事务在提交时执行验证。</span><span class="sxs-lookup"><span data-stu-id="90286-191">Explicit or implicit cross-container, read-only transactions perform validation at commit time if the transaction accesses memory-optimized tables under REPEATABLE READ or SERIALIZABLE isolation.</span></span> <span data-ttu-id="90286-192">有关验证的详细信息，请参阅[内存优化表的事务](../relational-databases/in-memory-oltp/memory-optimized-tables.md)中的冲突检测、验证和提交依赖项检查部分。</span><span class="sxs-lookup"><span data-stu-id="90286-192">For details about validation see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90286-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90286-193">See Also</span></span>  
 <span data-ttu-id="90286-194">[了解内存优化表上的事务](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="90286-194">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="90286-195">[具有内存优化表的事务隔离级别的准则](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="90286-195">[Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="90286-196">内存优化表事务重试逻辑准则</span><span class="sxs-lookup"><span data-stu-id="90286-196">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
