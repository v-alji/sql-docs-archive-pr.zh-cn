---
title: CLR 集成和事务 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693988"
---
# <a name="clr-integration-and-transactions"></a><span data-ttu-id="709cd-102">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="709cd-102">CLR Integration and Transactions</span></span>
  <span data-ttu-id="709cd-103">`System.Transactions` 命名空间提供与 ADO.NET 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公共语言运行时 (CLR) 集成完全集成的新事务框架。</span><span class="sxs-lookup"><span data-stu-id="709cd-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="709cd-104">`System.Transactions` 与 ADO.NET 配合工作，以扩展和简化托管应用程序中本地事务和分布式事务的使用。</span><span class="sxs-lookup"><span data-stu-id="709cd-104">`System.Transactions` and ADO.NET work together to extend and simplify the use of local and distributed transactions in managed applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="709cd-105">CLR 用户定义过程 (UDP) 不能与运行此过程的同一服务器建立连接（即环回连接），并且不能在同一事务中登记。</span><span class="sxs-lookup"><span data-stu-id="709cd-105">A CLR user-defined procedure (UDP) cannot establish a connection to the same server it is running on (a loopback connection) and enlist in the same transaction.</span></span> <span data-ttu-id="709cd-106">如果尝试上述操作，连接尝试将被阻止，并且无法将控制权传递回 UDP。</span><span class="sxs-lookup"><span data-stu-id="709cd-106">If this is attempted, the connection attempt will be blocked and control will not be passed back to the UDP.</span></span> <span data-ttu-id="709cd-107">这将导致 UDP 发生超时错误（消息 1206）。</span><span class="sxs-lookup"><span data-stu-id="709cd-107">This will result in a timeout error (Msg 1206) on the UDP.</span></span>  
  
 <span data-ttu-id="709cd-108">有关事务和 .NET Framework 的详细信息，请参阅 .NET Framework SDK 中的“执行事务”和“利用事务”。</span><span class="sxs-lookup"><span data-stu-id="709cd-108">For more information about transactions and the .NET Framework, see "Performing Transactions" and "Leveraging Transactions" in the .NET Framework SDK.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="709cd-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="709cd-109">In This Section</span></span>  
 [<span data-ttu-id="709cd-110">事务升级</span><span class="sxs-lookup"><span data-stu-id="709cd-110">Transaction Promotion</span></span>](transaction-promotion.md)  
 <span data-ttu-id="709cd-111">介绍提升事务的功能以及如何使用此功能。</span><span class="sxs-lookup"><span data-stu-id="709cd-111">Describes the ability to promote transactions, and how to use this feature.</span></span>  
  
 [<span data-ttu-id="709cd-112">访问当前事务</span><span class="sxs-lookup"><span data-stu-id="709cd-112">Accessing the Current Transaction</span></span>](accessing-the-current-transaction.md)  
 <span data-ttu-id="709cd-113">介绍如何访问当前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上以进程内方式运行的事务。</span><span class="sxs-lookup"><span data-stu-id="709cd-113">Describes how to access a transaction currently running in-process on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="709cd-114">使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="709cd-114">Using System.Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="709cd-115">介绍如何在托管应用程序中使用 `System.Transactions` 应用程序编程接口 (API)。</span><span class="sxs-lookup"><span data-stu-id="709cd-115">Describes how to use the `System.Transactions` application programming interface (API) in your managed application.</span></span>  
  
 [<span data-ttu-id="709cd-116">事务生存期</span><span class="sxs-lookup"><span data-stu-id="709cd-116">Transaction Lifetimes</span></span>](transaction-lifetimes.md)  
 <span data-ttu-id="709cd-117">介绍分别在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程和 CLR 应用程序中启动的事务生存期的差异。</span><span class="sxs-lookup"><span data-stu-id="709cd-117">Describes the difference in lifetime between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and transactions started in CLR applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709cd-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="709cd-118">See Also</span></span>  
 [<span data-ttu-id="709cd-119">从 CLR 数据库对象进行数据访问</span><span class="sxs-lookup"><span data-stu-id="709cd-119">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
