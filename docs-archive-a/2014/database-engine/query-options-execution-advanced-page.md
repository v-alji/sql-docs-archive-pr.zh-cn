---
title: 查询选项执行 (高级页) |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691859"
---
# <a name="query-options-execution-advanced-page"></a><span data-ttu-id="2f018-102">“查询选项”中的“执行”（“高级”页）</span><span class="sxs-lookup"><span data-stu-id="2f018-102">Query Options Execution (Advanced Page)</span></span>

  <span data-ttu-id="2f018-103">可以通过 **SET** 语句使用各种选项。</span><span class="sxs-lookup"><span data-stu-id="2f018-103">A variety of options are available using the **SET** statement.</span></span> <span data-ttu-id="2f018-104">使用此页可以指定用于运行 Microsoft SQL Server 查询的**SET**选项。</span><span class="sxs-lookup"><span data-stu-id="2f018-104">Use this page to specify a **SET** option to run Microsoft SQL Server queries.</span></span> <span data-ttu-id="2f018-105">有关其中每个选项的详细信息，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="2f018-105">For detailed information on each of these options, see SQL Server Books Online.</span></span>
  
<span data-ttu-id="2f018-106">**设置 NOCOUNT**不返回行数的计数，作为包含结果集的消息。</span><span class="sxs-lookup"><span data-stu-id="2f018-106">**SET NOCOUNT** Doesn't return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="2f018-107">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-107">This option is cleared by default.</span></span>

<span data-ttu-id="2f018-108">**设置 NOEXEC**不运行查询。</span><span class="sxs-lookup"><span data-stu-id="2f018-108">**SET NOEXEC** Doesn't run the query.</span></span> <span data-ttu-id="2f018-109">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-109">This option is cleared by default.</span></span>

<span data-ttu-id="2f018-110">**设置 PARSEONLY**检查每个查询的语法，但不运行查询。</span><span class="sxs-lookup"><span data-stu-id="2f018-110">**SET PARSEONLY** Checks the syntax of each query but Doesn't run the queries.</span></span> <span data-ttu-id="2f018-111">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-111">This option is cleared by default.</span></span>  

<span data-ttu-id="2f018-112">**设置 CONCAT_NULL_YIELDS_NULL**选中此复选框时，将现有值与连接的查询将 `NULL` 始终返回 `NULL` 作为结果。</span><span class="sxs-lookup"><span data-stu-id="2f018-112">**SET CONCAT_NULL_YIELDS_NULL** When this check box is selected, queries that concatenate an existing value with a `NULL`, always return a `NULL` as the result.</span></span> <span data-ttu-id="2f018-113">清除此复选框时，对于现有值与 `NULL` 相串联的查询，将返回该现有值。</span><span class="sxs-lookup"><span data-stu-id="2f018-113">When this check box is cleared, an existing value concatenated with a `NULL`, returns the existing value.</span></span> <span data-ttu-id="2f018-114">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="2f018-114">This option is selected by default.</span></span>

<span data-ttu-id="2f018-115">**设置 ARITHABORT**选中此复选框后，当 `INSERT` 、 `DELETE` 或 `UPDATE` 语句遇到算术错误 (溢出、被零除或在表达式计算期间) 域错误时，将终止查询或批处理。</span><span class="sxs-lookup"><span data-stu-id="2f018-115">**SET ARITHABORT** When this check box is selected, when an `INSERT`, `DELETE` or `UPDATE` statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="2f018-116">清除此复选框时，会在可能的情况下为该值提供 `NULL`，查询将继续进行，而结果中还会包含一条消息。</span><span class="sxs-lookup"><span data-stu-id="2f018-116">When this check box is cleared, a `NULL` is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="2f018-117">有关此行为的详细说明，请参阅联机丛书。</span><span class="sxs-lookup"><span data-stu-id="2f018-117">See Books Online for a more extensive description of this behavior.</span></span> <span data-ttu-id="2f018-118">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="2f018-118">This option is selected by default.</span></span>
  
<span data-ttu-id="2f018-119">**设置 SHOWPLAN_TEXT**选中此复选框时，将以文本形式返回每个查询的查询计划。</span><span class="sxs-lookup"><span data-stu-id="2f018-119">**SET SHOWPLAN_TEXT** When this check box is selected, the query plan is returned in text form with each query.</span></span> <span data-ttu-id="2f018-120">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-120">This option is cleared by default.</span></span>
  
<span data-ttu-id="2f018-121">**SET STATISTICS TIME** 选中此复选框时，将返回每个查询的时间统计信息。</span><span class="sxs-lookup"><span data-stu-id="2f018-121">**SET STATISTICS TIME** When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="2f018-122">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-122">This option is cleared by default.</span></span>
  
<span data-ttu-id="2f018-123">**设置统计 IO**选中此复选框时，将返回每个查询的输入/输出 (i/o) 的统计信息。</span><span class="sxs-lookup"><span data-stu-id="2f018-123">**SET STATISTICS IO** When this check box is selected, statistics regarding input/output (I/O) are returned with each query.</span></span> <span data-ttu-id="2f018-124">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-124">This option is cleared by default.</span></span>
  
<span data-ttu-id="2f018-125">**SET TRANSACTION ISOLATION LEVEL** 默认情况下，将设置 READ COMMITTED 事务隔离级别。</span><span class="sxs-lookup"><span data-stu-id="2f018-125">**SET TRANSACTION ISOLATION LEVEL** The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="2f018-126">有关详细信息，请参阅 [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f018-126">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="2f018-127">快照事务隔离级别不可用。</span><span class="sxs-lookup"><span data-stu-id="2f018-127">SNAPSHOT transaction isolation level isn't available.</span></span> <span data-ttu-id="2f018-128">若要使用 SNAPSHOT 隔离，请添加以下 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="2f018-128">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

<span data-ttu-id="2f018-129">**SET DEADLOCK PRIORITY** 如果使用默认值 **“正常”** ，则允许在发生死锁时每个查询具有相同的优先级。</span><span class="sxs-lookup"><span data-stu-id="2f018-129">**SET DEADLOCK PRIORITY** The default value of **Normal** allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="2f018-130">如果希望此查询在任何死锁冲突中都靠后考虑，并且选作要终止的查询，请从下拉列表中选择优先级“低”。</span><span class="sxs-lookup"><span data-stu-id="2f018-130">Select the priority Low from the drop-down list, if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>

<span data-ttu-id="2f018-131">**设置锁定超时**默认值为-1，表示一直持有锁，直到事务完成。</span><span class="sxs-lookup"><span data-stu-id="2f018-131">**SET LOCK TIMEOUT** The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="2f018-132">值为 0 时表示根本不等待，一遇到锁就返回信息。</span><span class="sxs-lookup"><span data-stu-id="2f018-132">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="2f018-133">如果事务的锁的保留时间必须长于此时间，请提供一个大于 0 毫秒的值以终止事务。</span><span class="sxs-lookup"><span data-stu-id="2f018-133">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>

<span data-ttu-id="2f018-134">**设置 QUERY_GOVERNOR_COST_LIMIT**使用 "**查询调控器开销限制**" 选项指定查询可以运行的时间段上限。</span><span class="sxs-lookup"><span data-stu-id="2f018-134">**SET QUERY_GOVERNOR_COST_LIMIT** Use the **query governor cost limit** option to specify an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="2f018-135">查询开销是指在特定硬件配置中完成查询所需的估计占用时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="2f018-135">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="2f018-136">默认设置 0 表示不限制查询运行时间的长度。</span><span class="sxs-lookup"><span data-stu-id="2f018-136">The default setting of 0 indicates no limit to the length of time a query will run</span></span>

<span data-ttu-id="2f018-137">**取消提供程序消息标头**选中此复选框时，将不显示提供程序 (的状态消息，如 OLE DB 提供程序) 。</span><span class="sxs-lookup"><span data-stu-id="2f018-137">**Suppress provider message headers** When this check box is selected, status messages from the provider (such as the OLE DB provider) aren't displayed.</span></span> <span data-ttu-id="2f018-138">默认情况下，此复选框为选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-138">This check box is selected by default.</span></span> <span data-ttu-id="2f018-139">在排除可能在提供程序级别上失败的查询故障时，清除此复选框可查看提供程序消息。</span><span class="sxs-lookup"><span data-stu-id="2f018-139">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>

<span data-ttu-id="2f018-140">**执行查询后断开连接** 选中此复选框时，查询完成后会终止与 SQL Server 之间的连接。</span><span class="sxs-lookup"><span data-stu-id="2f018-140">**Disconnect after the query executes** When this check box is selected, the connection to SQL Server is terminated after the query completes.</span></span> <span data-ttu-id="2f018-141">默认情况下，此选项处于未选中状态。</span><span class="sxs-lookup"><span data-stu-id="2f018-141">This option is cleared by default.</span></span>

<span data-ttu-id="2f018-142">**显示完成时间**允许您在查询结果之后或在 "消息" 选项卡中打印查询执行完成的时间。</span><span class="sxs-lookup"><span data-stu-id="2f018-142">**Show completion time** Allows you to print the time at which the query execution completed either after the query results or in the messages tab.</span></span>

<span data-ttu-id="2f018-143">**用于 VBS enclaves for Always Encrypted 的证明协议**允许你为基于虚拟化的安全 (VBS) enclaves 使用安全 enclaves 的始终加密使用的协议设置证明协议。</span><span class="sxs-lookup"><span data-stu-id="2f018-143">**Attestation protocol for VBS enclaves for Always Encrypted** Allows you to set an attestation protocol for Virtualization Based Security (VBS) enclaves used by always Encrypted with secure enclaves.</span></span>

<span data-ttu-id="2f018-144">当前支持的认证协议为：</span><span class="sxs-lookup"><span data-stu-id="2f018-144">The current supported attestation protocols are:</span></span>

* <span data-ttu-id="2f018-145">主机保护者服务-使用 Windows 主机保护者服务的证明协议 (HGS) 。</span><span class="sxs-lookup"><span data-stu-id="2f018-145">Host Guardian Service - an attestation protocol using Windows Host Guardian Service (HGS).</span></span>

<span data-ttu-id="2f018-146">有关详细信息，请参阅[具有 secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions)和[secure Enclave 证明](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation)的 Always Encrypted。</span><span class="sxs-lookup"><span data-stu-id="2f018-146">For more information, see [Always Encrypted with secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) and [Secure Enclave Attestation](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).</span></span>

<span data-ttu-id="2f018-147">**重置为默认值** 将此页上的所有值重置为原始默认值。</span><span class="sxs-lookup"><span data-stu-id="2f018-147">**Reset to Default** Resets all values on this page to the original default values.</span></span>
