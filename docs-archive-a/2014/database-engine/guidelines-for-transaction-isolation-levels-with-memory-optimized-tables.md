---
title: 具有内存优化表的事务隔离级别的准则 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 834c5950a8f8b0ddf8854d06c6fb1073a264fc22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690033"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a><span data-ttu-id="9622f-102">内存优化表事务隔离级别准则</span><span class="sxs-lookup"><span data-stu-id="9622f-102">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>
  <span data-ttu-id="9622f-103">在许多情况下，必须指定事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="9622f-103">In many scenarios, you must specify the transaction isolation level.</span></span> <span data-ttu-id="9622f-104">内存优化表的事务隔离不同于基于磁盘的表。</span><span class="sxs-lookup"><span data-stu-id="9622f-104">Transaction isolation for memory-optimized tables differs from disk-based tables.</span></span>  
  
 <span data-ttu-id="9622f-105">对于指定事务隔离级别的要求：</span><span class="sxs-lookup"><span data-stu-id="9622f-105">Requirements for specifying transaction isolation level:</span></span>  
  
-   <span data-ttu-id="9622f-106">对于包含本机编译存储过程内容的原子块，TRANSACTION ISOLATION LEVEL 为必需选项。</span><span class="sxs-lookup"><span data-stu-id="9622f-106">TRANSACTION ISOLATION LEVEL is a required option for the ATOMIC block comprising the content of a natively compiled stored procedure.</span></span>  
  
-   <span data-ttu-id="9622f-107">由于在跨容器事务中使用隔离级别存在限制，因此在解释型 [!INCLUDE[tsql](../includes/tsql-md.md)] 中使用内存优化表时通常必须随附一个表提示，以指定用于访问该表的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="9622f-107">Because of restrictions on isolation level use in cross-container transactions, uses of memory-optimized tables in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] must often be accompanied by a table hint specifying the isolation level used to access the table.</span></span> <span data-ttu-id="9622f-108">有关隔离级别提示和跨容器事务的详细信息，请参阅[事务隔离级别](../../2014/database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9622f-108">For more information about isolation level hints and cross-container transactions, see [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="9622f-109">必须显式声明所需的事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="9622f-109">The desired transaction isolation level must be explicitly declared.</span></span> <span data-ttu-id="9622f-110">无法使用锁提示（如 XLOCK）来保证事务中特定行或表的隔离。</span><span class="sxs-lookup"><span data-stu-id="9622f-110">It is not possible to use locking hints (such as XLOCK) to guarantee the isolation of certain rows or tables in the transaction.</span></span>  
  
-   <span data-ttu-id="9622f-111">访问数据库的应用程序应实现重试逻辑，以处理由于注定事务终止冲突、验证失败和提交依赖关系失败所导致的错误。</span><span class="sxs-lookup"><span data-stu-id="9622f-111">The application accessing the database should implement retry logic to deal with errors resulting from transaction-dooming conflicts, validation failures, and commit-dependency failures.</span></span> <span data-ttu-id="9622f-112">请注意，即使对于只读事务，也可能会发生提交依赖关系失败。</span><span class="sxs-lookup"><span data-stu-id="9622f-112">Note that commit dependency failures can occur even with read-only transactions.</span></span>  
  
-   <span data-ttu-id="9622f-113">对于内存优化表，应避免长时间运行的事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-113">Long-running transactions should be avoided with memory-optimized tables.</span></span> <span data-ttu-id="9622f-114">这类事务会增加冲突的可能性，使后续事务终止。</span><span class="sxs-lookup"><span data-stu-id="9622f-114">Such transactions increase the likelihood of conflicts and subsequent transaction terminations.</span></span> <span data-ttu-id="9622f-115">长时间运行的事务还会延迟垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="9622f-115">A long-running transaction also defers garbage collection.</span></span> <span data-ttu-id="9622f-116">一个事务的运行时间越长，内存中 OLTP 保留最近删除的行版本的时间就越长，这可能会降低新事务的查找性能。</span><span class="sxs-lookup"><span data-stu-id="9622f-116">The longer a transaction runs, the longer In-Memory OLTP keeps recently deleted row versions, which can decrease lookup performance for new transactions.</span></span>  
  
 <span data-ttu-id="9622f-117">基于磁盘的表通常依赖于锁定和阻塞来实现事务隔离。</span><span class="sxs-lookup"><span data-stu-id="9622f-117">Disk-based tables typically rely on locking and blocking for transaction isolation.</span></span> <span data-ttu-id="9622f-118">而内存优化表依赖于多版本控制和冲突检测来确保隔离。</span><span class="sxs-lookup"><span data-stu-id="9622f-118">Memory-optimized tables rely on multi-versioning and conflict detection to guarantee isolation.</span></span> <span data-ttu-id="9622f-119">有关详细信息，请参阅[内存优化表的事务](../relational-databases/in-memory-oltp/memory-optimized-tables.md)中的冲突检测、验证和提交依赖项检查部分。</span><span class="sxs-lookup"><span data-stu-id="9622f-119">For details, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="9622f-120">基于磁盘的表允许隔离级别 SNAPSHOT 和 READ_COMMITTED_SNAPSHOT 进行多版本控制。</span><span class="sxs-lookup"><span data-stu-id="9622f-120">Disk-based tables do allow multi-versioning with the isolation levels SNAPSHOT and READ_COMMITTED_SNAPSHOT.</span></span> <span data-ttu-id="9622f-121">对于内存优化表，所有隔离级别都是基于多版本的，包括 REPEATABLE READ 和 SERIALIZABLE。</span><span class="sxs-lookup"><span data-stu-id="9622f-121">For memory-optimized tables all isolation levels are multi-version based, including REPEATABLE READ and SERIALIZABLE.</span></span>  
  
## <a name="types-of-transactions"></a><span data-ttu-id="9622f-122">事务的类型</span><span class="sxs-lookup"><span data-stu-id="9622f-122">Types of Transactions</span></span>  
 <span data-ttu-id="9622f-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的每个查询都运行在事务的上下文中。</span><span class="sxs-lookup"><span data-stu-id="9622f-123">Every query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] runs in the context of a transaction.</span></span>  
  
 <span data-ttu-id="9622f-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中有三种事务类型：</span><span class="sxs-lookup"><span data-stu-id="9622f-124">There are three types of transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="9622f-125">自动提交事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-125">Autocommit transactions.</span></span> <span data-ttu-id="9622f-126">如果没有活动的事务上下文，且在会话中未将隐式事务设置为 ON，则每个查询都有自己的事务上下文。</span><span class="sxs-lookup"><span data-stu-id="9622f-126">If there is no active transaction context and implicit transactions are not set to ON in the session, each query has its own transaction context.</span></span> <span data-ttu-id="9622f-127">事务在语句开始执行时启动，在语句结束时完成。</span><span class="sxs-lookup"><span data-stu-id="9622f-127">The transaction starts when the statement starts execution, and completes when the statement finishes.</span></span>  
  
-   <span data-ttu-id="9622f-128">显式事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-128">Explicit transactions.</span></span> <span data-ttu-id="9622f-129">用户通过显式的 BEGIN TRAN 或 BEGIN ATOMIC 启动事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-129">The user starts the transaction through an explicit BEGIN TRAN or BEGIN ATOMIC.</span></span> <span data-ttu-id="9622f-130">事务跟随在相应的 COMMIT 和 ROLLBACK 或 END（如果是原子块）后完成。</span><span class="sxs-lookup"><span data-stu-id="9622f-130">The transaction is completed following the corresponding COMMIT and ROLLBACK or END (in the case of an atomic block).</span></span>  
  
-   <span data-ttu-id="9622f-131">隐式事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-131">Implicit transactions.</span></span> <span data-ttu-id="9622f-132">选项 IMPLICIT_TRANSACTIONS 设为 ON 时，每当用户执行一条语句且没有活动的事务上下文时，就会隐式启动事务。</span><span class="sxs-lookup"><span data-stu-id="9622f-132">When the option IMPLICIT_TRANSACTIONS is set to ON, a transaction is started implicitly whenever the user executes a statement and there is no active transaction context.</span></span> <span data-ttu-id="9622f-133">该事务通过显式的 COMMIT 和 ROLLBACK 完成。</span><span class="sxs-lookup"><span data-stu-id="9622f-133">The transaction is completed through an explicit COMMIT and ROLLBACK.</span></span>  
  
## <a name="baseline-read-committed-isolation"></a><span data-ttu-id="9622f-134">基准 READ COMMITTED 隔离</span><span class="sxs-lookup"><span data-stu-id="9622f-134">Baseline READ COMMITTED Isolation</span></span>  
 <span data-ttu-id="9622f-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的默认隔离级别为 READ COMMITTED。</span><span class="sxs-lookup"><span data-stu-id="9622f-135">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9622f-136">隔离级别 READ COMMITTED 确保事务不会看到来自当前事务外的更改的任何未提交数据。</span><span class="sxs-lookup"><span data-stu-id="9622f-136">The isolation level READ COMMITTED guarantees that transactions do not see any uncommitted data from changes outside the current transaction.</span></span> <span data-ttu-id="9622f-137">换言之，事务只读取已提交到数据库或已由当前事务更改的数据。</span><span class="sxs-lookup"><span data-stu-id="9622f-137">In other words, the transaction only reads data which has either been committed to the database, or has been changed by the current transaction.</span></span>  
  
 <span data-ttu-id="9622f-138">内存优化表支持的所有隔离级别都可提供已提交读保障。</span><span class="sxs-lookup"><span data-stu-id="9622f-138">All isolation levels supported for memory-optimized tables provide the read committed guarantee.</span></span> <span data-ttu-id="9622f-139">因此，如果事务不需要更严格的保障，则可使用内存优化表支持的任一隔离级别。</span><span class="sxs-lookup"><span data-stu-id="9622f-139">Therefore, if the transaction does not require stronger guarantees, you can use any of the isolation levels supported for memory-optimized tables.</span></span> <span data-ttu-id="9622f-140">与其他隔离级别相比，SNAPSHOT 使用的系统资源最少。</span><span class="sxs-lookup"><span data-stu-id="9622f-140">SNAPSHOT uses the fewest system resources, compared to other isolation levels.</span></span>  
  
 <span data-ttu-id="9622f-141">SNAPSHOT 隔离级别提供的保障（内存优化表支持的最低隔离级别）包括 READ COMMITTED 保障。</span><span class="sxs-lookup"><span data-stu-id="9622f-141">The guarantee provided by the SNAPSHOT isolation level (the lowest level of isolation supported for memory-optimized tables) includes the guarantees of READ COMMITTED.</span></span> <span data-ttu-id="9622f-142">事务中的每条语句都读取相同、一致的数据库版本。</span><span class="sxs-lookup"><span data-stu-id="9622f-142">Every statement in the transaction reads the same, consistent version of the database.</span></span> <span data-ttu-id="9622f-143">不仅该事务读取的所有行都提交到数据库，而且所有读取操作都会看到由同一组事务所作更改的集合。</span><span class="sxs-lookup"><span data-stu-id="9622f-143">Not only are all the rows read by the transaction committed to the database, also all the read operations see the set of changes made by the same set of transactions.</span></span>  
  
 <span data-ttu-id="9622f-144">**准则**：如果只需要已提交读隔离，请将快照隔离用于本机编译的存储过程，并通过解释的访问内存优化表 [!INCLUDE[tsql](../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9622f-144">**Guideline**: If only the READ COMMITTED isolation guarantee is required, use SNAPSHOT isolation with natively compiled stored procedures and for accessing memory-optimized tables through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9622f-145">对于自动提交事务，隔离级别 READ COMMITTED 会隐式映射到内存优化表的 SNAPSHOT。</span><span class="sxs-lookup"><span data-stu-id="9622f-145">For autocommit transactions, the isolation level READ COMMITTED is implicitly mapped to SNAPSHOT for memory-optimized tables.</span></span> <span data-ttu-id="9622f-146">因此，如果 TRANSACTION ISOLATION LEVEL 会话设置设为 READ COMMITTED，则在访问内存优化表时无需通过表提示指定隔离级别。</span><span class="sxs-lookup"><span data-stu-id="9622f-146">Therefore, if the TRANSACTION ISOLATION LEVEL session setting is set to READ COMMITTED, it is not necessary to specify the isolation level through a table hint when accessing memory-optimized tables.</span></span>  
  
 <span data-ttu-id="9622f-147">下面的自动提交事务示例介绍内存优化表 Customers 与常规表 [Order History] 之间的联接（作为即席批处理的一部分）：</span><span class="sxs-lookup"><span data-stu-id="9622f-147">The following autocommit transaction example shows a join between a memory-optimized table Customers and a regular table [Order History], as part of an ad hoc batch:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 <span data-ttu-id="9622f-148">下面的显式或隐式事务示例介绍同一联接，但这次是在显式用户事务中。</span><span class="sxs-lookup"><span data-stu-id="9622f-148">The following explicit or implicit transactions example shows the same join, but this time in an explicit user transaction.</span></span> <span data-ttu-id="9622f-149">内存优化表 Customers 在快照隔离下访问（如表提示 WITH (SNAPSHOT) 所示），而常规表 [Order History] 在已提交读隔离下访问：</span><span class="sxs-lookup"><span data-stu-id="9622f-149">The memory-optimized table Customers is accessed under snapshot isolation, as indicated through the table hint WITH (SNAPSHOT), and the regular table [Order History] is accessed under read committed isolation:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a><span data-ttu-id="9622f-150">操作差异</span><span class="sxs-lookup"><span data-stu-id="9622f-150">Operational Differences</span></span>  
 <span data-ttu-id="9622f-151">除已提交读保障外，使用基于磁盘的表的应用程序可能还依赖另外两个关键实现细节。</span><span class="sxs-lookup"><span data-stu-id="9622f-151">Besides the read committed guarantee, there are also two key implementation details that applications using disk-based tables may rely on.</span></span> <span data-ttu-id="9622f-152">在将使用 READ COMMITTED 隔离访问的基于磁盘的表转换为使用 SNAPSHOT 隔离访问的内存优化表时，需注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="9622f-152">Be aware of the following when converting a disk-based table that is accessed using READ COMMITTED isolation to a memory-optimized table that is accessed using SNAPSHOT isolation:</span></span>  
  
-   <span data-ttu-id="9622f-153">基于磁盘的表的 READ COMMITTED 隔离级别的实现（假定 READ_COMMITTED_SNAPSHOT 为 OFF）使用锁来防止读取器与编写器之间的冲突。</span><span class="sxs-lookup"><span data-stu-id="9622f-153">The implementation of the READ COMMITTED isolation level for disk-based tables (assuming READ_COMMITTED_SNAPSHOT is OFF) uses locks to prevent conflicts between readers and writers.</span></span> <span data-ttu-id="9622f-154">编写器开始更新行时，会获取一个锁，且直到事务提交后才释放锁。</span><span class="sxs-lookup"><span data-stu-id="9622f-154">When a writer starts updating a row, it takes a lock and does not release the lock until the transaction is committed.</span></span> <span data-ttu-id="9622f-155">所有读取操作被阻塞并等待写入事务提交。</span><span class="sxs-lookup"><span data-stu-id="9622f-155">Any read operations are blocked and will wait for the write transaction to commit.</span></span>  
  
     <span data-ttu-id="9622f-156">某些应用程序可能会假定读取器总是等待编写器提交，特别是当应用程序层中的两个事务之间没有任何同步时。</span><span class="sxs-lookup"><span data-stu-id="9622f-156">Some applications may assume readers always wait for writers to commit, particularly if there is any synchronization between the two transactions in the application tier.</span></span>  
  
     <span data-ttu-id="9622f-157">**指导原则：** 应用程序不能依赖阻止行为。</span><span class="sxs-lookup"><span data-stu-id="9622f-157">**Guideline:** Applications cannot rely on blocking behavior.</span></span> <span data-ttu-id="9622f-158">如果应用程序需要并发事务之间的同步，则可以通过[sp_getapplock &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql)，在应用层或数据库层中实现此类逻辑。</span><span class="sxs-lookup"><span data-stu-id="9622f-158">If an application needs synchronization between concurrent transactions, such logic can be implemented in the application tier or in the database tier, through [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span></span>  
  
-   <span data-ttu-id="9622f-159">在使用 READ COMMITTED 隔离的事务中，每条语句都会看到数据库中各行的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9622f-159">In transactions that use READ COMMITTED isolation, each statement sees the most recent version of the rows in the database.</span></span> <span data-ttu-id="9622f-160">因此，后续语句看到的是数据库状态的更改。</span><span class="sxs-lookup"><span data-stu-id="9622f-160">Therefore, subsequent statements see changes in the state of the database.</span></span>  
  
     <span data-ttu-id="9622f-161">采用这一假设的应用程序模式的一个示例：使用 WHILE 循环轮询表，直至发现新行为止。</span><span class="sxs-lookup"><span data-stu-id="9622f-161">Polling a table using a WHILE loop until a new row has been found is an example of an application pattern that uses this assumption.</span></span> <span data-ttu-id="9622f-162">该循环每次迭代时，查询将看到数据库中的最新更新。</span><span class="sxs-lookup"><span data-stu-id="9622f-162">With each iteration of the loop, the query will see the latest updates in the database.</span></span>  
  
     <span data-ttu-id="9622f-163">**指导原则：** 如果应用程序需要轮询内存优化表以获取写入到表中的最新行，请将轮询循环移出事务的作用域之外。</span><span class="sxs-lookup"><span data-stu-id="9622f-163">**Guideline:** If an application needs to poll a memory-optimized table to obtain the most recent rows written to the table, move the polling loop outside the scope of the transaction.</span></span>  
  
     <span data-ttu-id="9622f-164">下面的示例介绍采用这一假设的应用程序模式。</span><span class="sxs-lookup"><span data-stu-id="9622f-164">The following is an example application pattern that uses this assumption.</span></span> <span data-ttu-id="9622f-165">使用 WHILE 循环轮询表，直至发现新行。</span><span class="sxs-lookup"><span data-stu-id="9622f-165">Polling a table using a WHILE loop until a new row is found.</span></span> <span data-ttu-id="9622f-166">在每次循环迭代中，查询将访问数据库中的最新更新。</span><span class="sxs-lookup"><span data-stu-id="9622f-166">In each loop iteration, the query will access the latest updates in the database.</span></span>  
  
 <span data-ttu-id="9622f-167">下面的示例脚本轮询表 t1，直至该表中出现行为止。</span><span class="sxs-lookup"><span data-stu-id="9622f-167">The following example script polls a table t1 until it has a row.</span></span> <span data-ttu-id="9622f-168">之后，其从该表中移除一行，以作进一步处理。</span><span class="sxs-lookup"><span data-stu-id="9622f-168">It then removes a single row from the table for further processing.</span></span>  
  
 <span data-ttu-id="9622f-169">注意，需要将轮询逻辑放在事务范围之外，因为其使用快照隔离访问表 t1。</span><span class="sxs-lookup"><span data-stu-id="9622f-169">Notice that the polling logic needs to be outside the scope of the transaction, as it is using snapshot isolation to access table t1.</span></span> <span data-ttu-id="9622f-170">在事务范围内使用轮询逻辑会产生一个需要长时间运行的事务，这是个糟糕的做法。</span><span class="sxs-lookup"><span data-stu-id="9622f-170">Using polling logic inside the scope of a transaction would create a long-running transaction, which is a bad practice.</span></span>  
  
```sql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a><span data-ttu-id="9622f-171">锁定表提示</span><span class="sxs-lookup"><span data-stu-id="9622f-171">Locking Table Hints</span></span>  
 <span data-ttu-id="9622f-172"> (表提示的锁定提示[&#40;transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql-table)) 例如，HOLDLOCK 和 XLOCK 可以与基于磁盘的表一起使用，以获得 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 超过指定隔离级别所需的锁。</span><span class="sxs-lookup"><span data-stu-id="9622f-172">Locking hints ([Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) such as HOLDLOCK and XLOCK can be used with disk-based tables to have [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] take more locks than are required for the specified isolation level.</span></span>  
  
 <span data-ttu-id="9622f-173">内存优化表不使用锁。</span><span class="sxs-lookup"><span data-stu-id="9622f-173">Memory-optimized tables do not use locks.</span></span> <span data-ttu-id="9622f-174">可以使用更高的隔离级别（如 REPEATABLE READ 和 SERIALIZABLE）声明所需的保障。</span><span class="sxs-lookup"><span data-stu-id="9622f-174">Higher isolation levels such as REPEATABLE READ and SERIALIZABLE can be used to declare the desired guarantees.</span></span>  
  
 <span data-ttu-id="9622f-175">不支持锁定提示。</span><span class="sxs-lookup"><span data-stu-id="9622f-175">Locking hints are not supported.</span></span> <span data-ttu-id="9622f-176">改为通过事务隔离级别声明所需的保障。</span><span class="sxs-lookup"><span data-stu-id="9622f-176">Instead, declare the required guarantees through the transaction isolation levels.</span></span> <span data-ttu-id="9622f-177">（支持 NOLOCK 是因为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 不对内存优化表使用锁。</span><span class="sxs-lookup"><span data-stu-id="9622f-177">(NOLOCK is supported because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not take locks on memory-optimized tables.</span></span> <span data-ttu-id="9622f-178">请注意，与基于磁盘的表不同，NOLOCK 对于内存优化表并不暗示 READ UNCOMMITTED 行为。）</span><span class="sxs-lookup"><span data-stu-id="9622f-178">Note that, in contrast to disk-based tables, NOLOCK does not imply READ UNCOMMITTED behavior for memory-optimized tables.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9622f-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9622f-179">See Also</span></span>  
 <span data-ttu-id="9622f-180">[了解内存优化表上的事务](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="9622f-180">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="9622f-181">[内存优化表上的事务重试逻辑指南](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="9622f-181">[Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="9622f-182">事务隔离级别</span><span class="sxs-lookup"><span data-stu-id="9622f-182">Transaction Isolation Levels</span></span>](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
