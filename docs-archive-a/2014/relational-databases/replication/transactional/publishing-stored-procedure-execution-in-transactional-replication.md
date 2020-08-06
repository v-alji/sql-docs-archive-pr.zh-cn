---
title: 在事务复制中发布存储过程执行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], stored procedures and
- transactional replication, publishing stored procedure execution
ms.assetid: f4686f6f-c224-4f07-a7cb-92f4dd483158
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fb5c40db46772cabcb5d1df19e03aced749e1c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692341"
---
# <a name="publishing-stored-procedure-execution-in-transactional-replication"></a><span data-ttu-id="dbfd7-102">在事务复制中发布存储过程执行</span><span class="sxs-lookup"><span data-stu-id="dbfd7-102">Publishing Stored Procedure Execution in Transactional Replication</span></span>
  <span data-ttu-id="dbfd7-103">如果在发布服务器上执行一个或多个存储过程并影响已发布的表，请考虑将这些存储过程作为存储过程执行项目包括在发布中。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-103">If you have one or more stored procedures that execute at the Publisher and affect published tables, consider including those stored procedures in your publication as stored procedure execution articles.</span></span> <span data-ttu-id="dbfd7-104">初始化订阅时，过程定义（CREATE PROCEDURE 语句）将被复制到订阅服务器上；当在发布服务器上执行过程时，复制将在订阅服务器上执行相应的过程。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-104">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span> <span data-ttu-id="dbfd7-105">在执行大量批处理操作的情况下，这可以显著提高性能，因为这仅复制此过程执行而不需要为每一行复制各种更改。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-105">This can provide significantly better performance for cases where large batch operations are performed, because only the procedure execution is replicated, bypassing the need to replicate the individual changes for each row.</span></span> <span data-ttu-id="dbfd7-106">例如，假设在发布数据库中创建下面的存储过程：</span><span class="sxs-lookup"><span data-stu-id="dbfd7-106">For example, assume you create the following stored procedure in the publication database:</span></span>  
  
```  
CREATE PROC give_raise AS  
UPDATE EMPLOYEES SET salary = salary * 1.10  
```  
  
 <span data-ttu-id="dbfd7-107">此过程用于为贵公司的 10,000 名雇员每人增加 10% 的薪水。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-107">This procedure gives each of the 10,000 employees in your company a 10 percent pay increase.</span></span> <span data-ttu-id="dbfd7-108">在发布服务器上执行此存储过程时，它会更新每位雇员的薪水。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-108">When you execute this stored procedure at the Publisher, it updates the salary for each employee.</span></span> <span data-ttu-id="dbfd7-109">若没有复制存储过程执行，此更新将被作为一个大型的、多步骤事务发送到订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="dbfd7-109">Without the replication of stored procedure execution, the update would be sent to Subscribers as a large, multi-step transaction:</span></span>  
  
```  
BEGIN TRAN  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 1'  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 2'  
```  
  
 <span data-ttu-id="dbfd7-110">如此重复进行 10,000 次更新。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-110">And this repeats for 10,000 updates.</span></span>  
  
 <span data-ttu-id="dbfd7-111">如果复制存储过程执行，则复制将仅发送在订阅服务器上执行存储过程的命令，而不会将所有更新都写入分发数据库并随后通过网络将它们发送到订阅服务器：</span><span class="sxs-lookup"><span data-stu-id="dbfd7-111">With the replication of stored procedure execution, replication sends only the command to execute the stored procedure at the Subscriber, rather than writing all the updates to the distribution database and then sending them over the network to the Subscriber:</span></span>  
  
```  
EXEC give_raise  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbfd7-112">存储过程复制并非适用于所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-112">Stored procedure replication is not appropriate for all applications.</span></span> <span data-ttu-id="dbfd7-113">如果对某个项目进行水平筛选，以致发布服务器上存在不同于订阅服务器的行集，那么在这两个服务器上执行同一个存储过程将返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-113">If an article is filtered horizontally, so that there are different sets of rows at the Publisher than at the Subscriber, executing the same stored procedure at both returns different results.</span></span> <span data-ttu-id="dbfd7-114">与此类似，如果某个更新基于另一个未复制表的子查询，那么在发布服务器和订阅服务器上同时执行相同的存储过程将返回不同的结果。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-114">Similarly, if an update is based on a subquery of another, nonreplicated table, executing the same stored procedure at both the Publisher and Subscriber returns different results.</span></span>  
  
 <span data-ttu-id="dbfd7-115">**发布存储过程的执行**</span><span class="sxs-lookup"><span data-stu-id="dbfd7-115">**To publish the execution of a stored procedure**</span></span>  
  
-   <span data-ttu-id="dbfd7-116">SQL Server Management Studio：[在事务发布中发布存储过程的执行 (SQL Server Management Studio)](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="dbfd7-116">SQL Server Management Studio: [Publish the Execution of a Stored Procedure in a Transactional Publication &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="dbfd7-117">复制 Transact-sql 编程：执行[sp_addarticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) ，并将参数的值指定为 "serializable proc exec" (推荐) 或 "proc exec" **@type** 。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-117">Replication Transact-SQL Programming: execute [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and specify a value of 'serializable proc exec' (recommended) or 'proc exec' for the parameter **@type**.</span></span> <span data-ttu-id="dbfd7-118">有关如何定义项目的详细信息，请参阅[定义项目](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-118">For more information about defining articles, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="modifying-the-procedure-at-the-subscriber"></a><span data-ttu-id="dbfd7-119">在订阅服务器上修改过程</span><span class="sxs-lookup"><span data-stu-id="dbfd7-119">Modifying the Procedure at the Subscriber</span></span>  
 <span data-ttu-id="dbfd7-120">默认情况下，发布服务器上的存储过程定义会传播到每个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-120">By default, the stored procedure definition at the Publisher is propagated to each Subscriber.</span></span> <span data-ttu-id="dbfd7-121">但是，还可以在订阅服务器上修改存储过程。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-121">However, you can also modify the stored procedure at the Subscriber.</span></span> <span data-ttu-id="dbfd7-122">这有助于在发布服务器和订阅服务器上执行不同的逻辑。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-122">This is useful if you want different logic to be executed at the Publisher and Subscriber.</span></span> <span data-ttu-id="dbfd7-123">例如，假设发布服务器上的存储过程 **sp_big_delete**有两个作用：从复制的表 **big_table1** 中删除 1,000,000 行；更新未复制的表 **big_table2**。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-123">For example, consider **sp_big_delete**, a stored procedure at the Publisher that has two functions: it deletes 1,000,000 rows from the replicated table **big_table1** and updates the nonreplicated table **big_table2**.</span></span> <span data-ttu-id="dbfd7-124">为了减少对网络资源的需求，应通过发布 **sp_big_delete**将 1 百万行删除作为一个存储过程进行传播。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-124">To reduce the demand on network resources, you should propagate the 1 million row delete as a stored procedure by publishing **sp_big_delete**.</span></span> <span data-ttu-id="dbfd7-125">在订阅服务器上，您可以修改 **sp_big_delete** 只删除 1 百万行且不对 **big_table2**执行后续更新。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-125">At the Subscriber, you can modify **sp_big_delete** to delete only the 1 million rows and not perform the subsequent update to **big_table2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbfd7-126">默认情况下，发布服务器上使用 ALTER PROCEDURE 进行的任何更改都会传播到订阅服务器上。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-126">By default, any changes made using ALTER PROCEDURE at the Publisher are propagated to the Subscriber.</span></span> <span data-ttu-id="dbfd7-127">为避免出现这种情况，在执行 ALTER PROCEDURE 之前禁用架构更改的传播。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-127">To prevent this, disable the propagation of schema changes before executing ALTER PROCEDURE.</span></span> <span data-ttu-id="dbfd7-128">有关架构更改的信息，请参阅[对发布数据库进行架构更改](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-128">For information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="types-of-stored-procedure-execution-articles"></a><span data-ttu-id="dbfd7-129">存储过程执行项目的类型</span><span class="sxs-lookup"><span data-stu-id="dbfd7-129">Types of Stored Procedure Execution Articles</span></span>  
 <span data-ttu-id="dbfd7-130">发布存储过程的执行有两种不同方式：可序列化过程执行项目和过程执行项目。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-130">There are two different ways in which the execution of a stored procedure can be published: serializable procedure execution article and procedure execution article.</span></span>  
  
-   <span data-ttu-id="dbfd7-131">建议使用可序列化选项，因为仅当过程在可序列化事务的上下文内执行时，才能复制过程执行。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-131">The serializable option is recommended because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="dbfd7-132">如果存储过程从可序列化事务外部执行，则对已发布的表中数据的更改将作为一系列 DML 语句被复制。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-132">If the stored procedure is executed from outside a serializable transaction, changes to data in published tables are replicated as a series of DML statements.</span></span> <span data-ttu-id="dbfd7-133">此行为有助于使订阅服务器上的数据与发布服务器上的数据一致。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-133">This behavior contributes to making data at the Subscriber consistent with data at the Publisher.</span></span> <span data-ttu-id="dbfd7-134">这对批处理操作（例如大量的清除操作）尤其有用。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-134">This is especially useful for batch operations, such as large cleanup operations.</span></span>  
  
-   <span data-ttu-id="dbfd7-135">通过使用过程执行选项，可以将执行复制到所有订阅服务器，无论存储过程中的单个语句是否成功。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-135">With the procedure execution option, it is possible that execution could be replicated to all Subscribers regardless of whether individual statements in the stored procedure were successful.</span></span> <span data-ttu-id="dbfd7-136">此外，由于存储过程引起的数据更改可能在多个事务内发生，因此订阅服务器上的数据可能不能与发布服务器上的数据一致。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-136">Furthermore, because changes made to data by the stored procedure can occur within multiple transactions, data at the Subscribers might not be consistent with data at the Publisher.</span></span> <span data-ttu-id="dbfd7-137">若要解决这些问题，要求订阅服务器为只读，并且您使用的是大于未提读书的隔离级别。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-137">To address these issues, it is required that Subscribers are read-only and that you use an isolation level greater than read uncommitted.</span></span> <span data-ttu-id="dbfd7-138">如果使用未提交读，则已发布表中的数据更改将复制为一系列 DML 语句。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-138">If you use read uncommitted, changes to data in published tables are replicated as a series of DML statements.</span></span>  
  
 <span data-ttu-id="dbfd7-139">下面的示例说明了建议将过程复制设置为可序列化过程项目的原因。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-139">The following example illustrates why it is recommended that you set up replication of procedures as serializable procedure articles.</span></span>  
  
```  
BEGIN TRANSACTION T1  
SELECT @var = max(col1) FROM tableA  
UPDATE tableA SET col2 = <value>   
   WHERE col1 = @var   
  
BEGIN TRANSACTION T2  
INSERT tableA VALUES <values>  
COMMIT TRANSACTION T2  
```  
  
 <span data-ttu-id="dbfd7-140">在前面的示例中，假设事务 T1 中的 SELECT 出现在事务 T2 中的 INSERT 之前。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-140">In the previous example, it is assumed that the SELECT in transaction T1 happens before the INSERT in transaction T2.</span></span>  
  
 <span data-ttu-id="dbfd7-141">如果该过程不在可序列化事务内执行（隔离级别设置为 SERIALIZABLE），则允许事务 T2 在 T1 中 SELECT 语句范围内插入新行，且在 T1 之前提交。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-141">If the procedure is not executed within a serializable transaction (with isolation level set to SERIALIZABLE), transaction T2 will be allowed to insert a new row within the range of the SELECT statement in T1 and it will commit before T1.</span></span> <span data-ttu-id="dbfd7-142">这还意味着在订阅服务器上先应用 T2，后应用 T1。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-142">This also means that it will be applied at the Subscriber before T1.</span></span> <span data-ttu-id="dbfd7-143">在订阅服务器上应用 T1 时，SELECT 返回的值可能与发布服务器上的值不同，且可能导致与 UPDATE 不同的结果。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-143">When T1 is applied at the Subscriber, the SELECT can potentially return a different value than at the Publisher and can result in a different outcome from the UPDATE.</span></span>  
  
 <span data-ttu-id="dbfd7-144">如果在可序列化事务中执行该过程，将不允许将事务 T2 插入到 T2 中的 SELECT 语句所包括的范围内。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-144">If the procedure is executed within a serializable transaction, transaction T2 will not be allowed to insert within the range covered by the SELECT statement in T2.</span></span> <span data-ttu-id="dbfd7-145">T2 将被阻塞，直到 T1 提交可以确保与订阅服务器上的结果相同。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-145">It will be blocked until T1 commits ensuring the same results at the Subscriber.</span></span>  
  
 <span data-ttu-id="dbfd7-146">在可序列化事务中执行过程时控制锁的时间将更长，并可能导致并发减少。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-146">Locks will be held longer when you execute the procedure within a serializable transaction and may result in reduced concurrency.</span></span>  
  
## <a name="the-xact_abort-setting"></a><span data-ttu-id="dbfd7-147">XACT_ABORT 设置</span><span class="sxs-lookup"><span data-stu-id="dbfd7-147">The XACT_ABORT Setting</span></span>  
 <span data-ttu-id="dbfd7-148">在复制存储过程执行时，执行此存储过程的会话设置应将 XACT_ABORT 指定为 ON。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-148">When replicating stored procedure execution, the setting for the session executing the stored procedure should specify XACT_ABORT ON.</span></span> <span data-ttu-id="dbfd7-149">如果 XACT_ABORT 设置为 OFF，在发布服务器上执行此过程时将出现错误，并且订阅服务器上也会出现相同的错误，这将导致分发代理失败。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-149">If XACT_ABORT is set to OFF, and an error occurs during execution of the procedure at the Publisher, the same error will occur at the Subscriber, causing the Distribution Agent to fail.</span></span> <span data-ttu-id="dbfd7-150">将 XACT_ABORT 指定为 ON 可确保在发布服务器上执行时遇到的任何错误会使整个执行回滚，从而避免分发代理失败。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-150">Specifying XACT_ABORT ON ensures that any errors encountered during execution at the Publisher cause the entire execution to be rolled back, avoiding the Distribution Agent failure.</span></span> <span data-ttu-id="dbfd7-151">有关如何设置 XACT_ABORT 的详细信息，请参阅 [SET XACT_ABORT (Transact-SQL)](/sql/t-sql/statements/set-xact-abort-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-151">For more information about setting XACT_ABORT, see [SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql).</span></span>  
  
 <span data-ttu-id="dbfd7-152">如果需要将 XACT_ABORT 设置为 OFF，请指定分发代理的 **-SkipErrors** 参数。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-152">If you require a setting of XACT_ABORT OFF, specify the **-SkipErrors** parameter for the Distribution Agent.</span></span> <span data-ttu-id="dbfd7-153">这使得代理即使在遇到错误的情况下也会继续在订阅服务器上应用更改。</span><span class="sxs-lookup"><span data-stu-id="dbfd7-153">This allows the agent to continue applying changes at the Subscriber even if an error is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfd7-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbfd7-154">See Also</span></span>  
 [<span data-ttu-id="dbfd7-155">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="dbfd7-155">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
