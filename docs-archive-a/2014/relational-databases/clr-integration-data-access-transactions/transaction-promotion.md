---
title: 事务升级 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
author: rothja
ms.author: jroth
ms.openlocfilehash: e78cbb3d2fc888e56c0b55780daf7b449fe6dc40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693982"
---
# <a name="transaction-promotion"></a><span data-ttu-id="23f6a-102">事务升级</span><span class="sxs-lookup"><span data-stu-id="23f6a-102">Transaction Promotion</span></span>
  <span data-ttu-id="23f6a-103">事务*升级*描述了可根据需要自动提升为完全可分发事务的轻型本地事务。</span><span class="sxs-lookup"><span data-stu-id="23f6a-103">Transaction *promotion* describes a lightweight, local transaction that can be automatically promoted to a fully distributable transaction as needed.</span></span> <span data-ttu-id="23f6a-104">当在服务器上的数据库事务内调用托管存储过程时，会在本地事务的上下文中运行公共语言运行时 (CLR) 代码。</span><span class="sxs-lookup"><span data-stu-id="23f6a-104">When a managed stored procedure is invoked within a database transaction on the server, the common language runtime (CLR) code is run in the context of a local transaction.</span></span>  <span data-ttu-id="23f6a-105">如果在数据库事务内打开到远程服务器的连接，则到远程服务器的连接会登记在分布式事务中，并且本地事务会自动升级为分布式事务。</span><span class="sxs-lookup"><span data-stu-id="23f6a-105">If a connection to a remote server is opened within a database transaction, the connection to the remote server is enlisted into the distributed transaction and the local transaction is automatically promoted to a distributed transaction.</span></span> <span data-ttu-id="23f6a-106">因此，通过将分布式事务的创建延迟到需要创建时才进行，事务升级可以将分布式事务的开销降至最低。</span><span class="sxs-lookup"><span data-stu-id="23f6a-106">So, transaction promotion minimizes the overhead of distributed transactions by deferring the creation of a distributed transaction until it is needed.</span></span> <span data-ttu-id="23f6a-107">如果已使用 `Enlist` 关键字启用了事务升级，则事务升级将自动进行，而不需要开发人员干预。</span><span class="sxs-lookup"><span data-stu-id="23f6a-107">Transaction promotion is automatic, if it has been enabled using the `Enlist` keyword, and does not require intervention from the developer.</span></span> <span data-ttu-id="23f6a-108">用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 .NET Framework 数据提供程序可为事务升级提供支持，这是通过 .NET Framework `System.Data.SqlClient` 命名空间中的类处理的。</span><span class="sxs-lookup"><span data-stu-id="23f6a-108">The .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides support for transaction promotion, handled through the classes in the .NET Framework `System.Data.SqlClient` namespace.</span></span>  
  
## <a name="the-enlist-keyword"></a><span data-ttu-id="23f6a-109">征用关键字</span><span class="sxs-lookup"><span data-stu-id="23f6a-109">The Enlist Keyword</span></span>  
 <span data-ttu-id="23f6a-110">`ConnectionString` 对象的 `SqlConnection` 属性支持 `Enlist` 关键字，该关键字指示 `System.Data.SqlClient` 是否检测事务上下文并在分布式事务中自动登记连接。</span><span class="sxs-lookup"><span data-stu-id="23f6a-110">The `ConnectionString` property of a `SqlConnection` object supports the `Enlist` keyword, which indicates whether `System.Data.SqlClient` detects transactional contexts and automatically enlists the connection in a distributed transaction.</span></span> <span data-ttu-id="23f6a-111">如果此关键字设置为 True（默认设置），则会在打开的线程的当前事务上下文中自动登记连接。</span><span class="sxs-lookup"><span data-stu-id="23f6a-111">If this keyword is set to true (the default), the connection is automatically enlisted in the current transaction context of the opening thread.</span></span> <span data-ttu-id="23f6a-112">如果此关键字设置为 False，则 SqlClient 连接不会与分布式事务交互。</span><span class="sxs-lookup"><span data-stu-id="23f6a-112">If this keyword is set to false, the SqlClient connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="23f6a-113">如果未在连接字符串中指定 `Enlist`，并且如果在打开相应连接时检测到一个分布式事务，则会在此分布式事务中自动登记此连接。</span><span class="sxs-lookup"><span data-stu-id="23f6a-113">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected at the time the connection is opened.</span></span>  
  
## <a name="distributed-transactions"></a><span data-ttu-id="23f6a-114">分布式事务</span><span class="sxs-lookup"><span data-stu-id="23f6a-114">Distributed Transactions</span></span>  
 <span data-ttu-id="23f6a-115">分布式事务通常会使用大量的系统资源。</span><span class="sxs-lookup"><span data-stu-id="23f6a-115">Distributed transactions typically consume significant system resources.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="23f6a-116">分布式事务处理协调器 (MS DTC) 会管理此类事务，并集成在这些事务中访问的所有资源管理器。</span><span class="sxs-lookup"><span data-stu-id="23f6a-116">Distributed Transaction Coordinator (MS DTC) manages such transactions, and integrates all of the resource managers accessed in these transactions.</span></span> <span data-ttu-id="23f6a-117">另一方面，事务升级是有效地将工作委托给简单 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事务的 `System.Transactions` 事务的特殊形式。</span><span class="sxs-lookup"><span data-stu-id="23f6a-117">Transaction promotion, on the other hand, is a special form of a `System.Transactions` transaction that effectively delegates the work to a simple [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> <span data-ttu-id="23f6a-118">`System.Transactions`、`System.Data.SqlClient` 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会对处理事务时涉及到的工作进行协调，并按照需要将其升级为完全分布式事务。</span><span class="sxs-lookup"><span data-stu-id="23f6a-118">`System.Transactions`, `System.Data.SqlClient`, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="23f6a-119">使用事务升级的优点在于：在打开一个具有活动 `TransactionScope` 事务的连接而未打开任何其他连接的情况下，该事务会以轻型事务的形式提交，而不是产生完全分布式事务的额外开销。</span><span class="sxs-lookup"><span data-stu-id="23f6a-119">The benefit of using transaction promotion is that when a connection is opened with an active `TransactionScope` transaction, and no other connections are opened, the transaction commits as a lightweight transaction, rather than incurring the additional overhead of a full distributed transaction.</span></span> <span data-ttu-id="23f6a-120">有关的详细信息 `TransactionScope` ，请参阅[使用 system.object](../native-client-ole-db-transactions/transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="23f6a-120">For more information about `TransactionScope`, see [Using System.Transactions](../native-client-ole-db-transactions/transactions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f6a-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23f6a-121">See Also</span></span>  
 [<span data-ttu-id="23f6a-122">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="23f6a-122">CLR Integration and Transactions</span></span>](clr-integration-and-transactions.md)  
  
  
