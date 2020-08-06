---
title: " (XMLA) 管理事务 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
author: minewiskan
ms.author: owend
ms.openlocfilehash: bff1c60addd25b222905e33bc33e77dd85e88803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590415"
---
# <a name="managing-transactions-xmla"></a><span data-ttu-id="0534c-102">管理事务 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="0534c-102">Managing Transactions (XMLA)</span></span>
  <span data-ttu-id="0534c-103">每个 XML for Analysis (XMLA) 命令发送到实例，该实例在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 当前隐式或显式会话的事务上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="0534c-103">Every XML for Analysis (XMLA) command sent to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs within the context of a transaction on the current implicit or explicit session.</span></span> <span data-ttu-id="0534c-104">若要管理这些事务中的每一个，请使用[BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla)、 [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)和[RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla)命令。</span><span class="sxs-lookup"><span data-stu-id="0534c-104">To manage each of these transactions, you use the [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), and [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) commands.</span></span> <span data-ttu-id="0534c-105">通过使用这些命令，可创建隐式或显式事务，更改事务引用计数以及启动、提交或回滚事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-105">By using these commands, you can create implicit or explicit transactions, change the transaction reference count, as well as start, commit, or roll back transactions.</span></span>  
  
## <a name="implicit-and-explicit-transactions"></a><span data-ttu-id="0534c-106">隐式和显式事务</span><span class="sxs-lookup"><span data-stu-id="0534c-106">Implicit and Explicit Transactions</span></span>  
 <span data-ttu-id="0534c-107">事务可以是隐式的或显式的：</span><span class="sxs-lookup"><span data-stu-id="0534c-107">A transaction is either implicit or explicit:</span></span>  
  
 <span data-ttu-id="0534c-108">**隐式事务**</span><span class="sxs-lookup"><span data-stu-id="0534c-108">**Implicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="0534c-109">如果命令未指定事务的开始，则为 XMLA 命令创建*隐式*事务 `BeginTransaction` 。</span><span class="sxs-lookup"><span data-stu-id="0534c-109">creates an *implicit* transaction for an XMLA command if the `BeginTransaction` command does not specify the start of a transaction.</span></span> <span data-ttu-id="0534c-110">如果此命令成功，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将始终提交隐式事务，如果此命令失败，则将回滚隐式事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] always commits an implicit transaction if the command succeeds, and rolls back an implicit transaction if the command fails.</span></span>  
  
 <span data-ttu-id="0534c-111">**显式事务**</span><span class="sxs-lookup"><span data-stu-id="0534c-111">**Explicit transaction**</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="0534c-112">如果命令启动事务，则创建*显式*事务 `BeginTransaction` 。</span><span class="sxs-lookup"><span data-stu-id="0534c-112">creates an *explicit* transaction if the `BeginTransaction` command starts of a transaction.</span></span> <span data-ttu-id="0534c-113">但是，如果发送 `CommitTransaction` 命令，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 仅提交显式事务，如果发送 `RollbackTransaction` 命令，则将回滚显式事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-113">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] only commits an explicit transaction if a `CommitTransaction` command is sent, and rolls back an explicit transaction if a `RollbackTransaction` command is sent.</span></span>  
  
 <span data-ttu-id="0534c-114">此外，如果在活动事务完成之前，当前事务结束，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将同时回滚隐式事务和显式事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-114">In addition, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rolls back both implicit and explicit transactions if the current session ends before the active transaction completes.</span></span>  
  
## <a name="transactions-and-reference-counts"></a><span data-ttu-id="0534c-115">事务和引用计数</span><span class="sxs-lookup"><span data-stu-id="0534c-115">Transactions and Reference Counts</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0534c-116">可继续每个会话的事务引用计数。</span><span class="sxs-lookup"><span data-stu-id="0534c-116">maintains a transaction reference count for each session.</span></span> <span data-ttu-id="0534c-117">但是，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 不支持嵌套事务，因为仅为每个会话维持一个活动事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-117">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not support nested transactions in that only one active transaction is maintained per session.</span></span> <span data-ttu-id="0534c-118">如果当前会话没有活动事务，则事务引用计数将设置为零。</span><span class="sxs-lookup"><span data-stu-id="0534c-118">If the current session does not have an active transaction, the transaction reference count is set to zero.</span></span>  
  
 <span data-ttu-id="0534c-119">换言之，每个 `BeginTransaction` 命令使引用计数按 1 递增，而每个 `CommitTransaction` 命令使引用计数按 1 递减。</span><span class="sxs-lookup"><span data-stu-id="0534c-119">In other words, each `BeginTransaction` command increments the reference count by one, while each `CommitTransaction` command decrements the reference count by one.</span></span> <span data-ttu-id="0534c-120">如果 `CommitTransaction` 命令将事务计数设置为零，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将提交该事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-120">If a `CommitTransaction` command sets the transaction count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the transaction.</span></span>  
  
 <span data-ttu-id="0534c-121">但是，无论事务引用计数的当前值如何，`RollbackTransaction` 命令都将回滚活动事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-121">However, the `RollbackTransaction` command rolls back the active transaction regardless of the current value of the transaction reference count.</span></span> <span data-ttu-id="0534c-122">换言之，不管已发送多少 `RollbackTransaction` 命令或 `BeginTransaction` 命令，单个 `CommitTransaction` 命令都将回滚活动事务，并将事务引用计数设置为零。</span><span class="sxs-lookup"><span data-stu-id="0534c-122">In other words, a single `RollbackTransaction` command rolls back the active transaction, no matter how many `BeginTransaction` commands or `CommitTransaction` commands were sent, and sets the transaction reference count to zero.</span></span>  
  
## <a name="beginning-a-transaction"></a><span data-ttu-id="0534c-123">开始事务</span><span class="sxs-lookup"><span data-stu-id="0534c-123">Beginning a Transaction</span></span>  
 <span data-ttu-id="0534c-124">`BeginTransaction` 命令可在当前会话上开始显式事务，并按 1 递增当前会话的事务引用计数。</span><span class="sxs-lookup"><span data-stu-id="0534c-124">The `BeginTransaction` command begins an explicit transaction on the current session and increments the transaction reference count for the current session by one.</span></span> <span data-ttu-id="0534c-125">所有后续命令都将视为位于活动事务中，直至发送足够的 `CommitTransaction` 命令来提交活动事务，或发送单个 `RollbackTransaction` 命令来回滚活动事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-125">All subsequent commands are considered to be within the active transaction, until either enough `CommitTransaction` commands are sent to commit the active transaction or a single `RollbackTransaction` command is sent to roll back the active transaction.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="0534c-126">提交事务</span><span class="sxs-lookup"><span data-stu-id="0534c-126">Committing a Transaction</span></span>  
 <span data-ttu-id="0534c-127">`CommitTransaction` 命令可提交对当前会话运行 `BeginTransaction` 命令后运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="0534c-127">The `CommitTransaction` command commits the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="0534c-128">每个 `CommitTransaction` 命令都会减少会话上活动事务的引用计数。</span><span class="sxs-lookup"><span data-stu-id="0534c-128">Each `CommitTransaction` command decrements the reference count for active transactions on a session.</span></span> <span data-ttu-id="0534c-129">如果 `CommitTransaction` 命令将引用计数设置为零，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将提交活动事务。</span><span class="sxs-lookup"><span data-stu-id="0534c-129">If a `CommitTransaction` command sets the reference count to zero, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] commits the active transaction.</span></span> <span data-ttu-id="0534c-130">如果不存在活动事务（换言之，当前会话的事务引用计数已设置为零），则 `CommitTransaction` 命令将导致出错。</span><span class="sxs-lookup"><span data-stu-id="0534c-130">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `CommitTransaction` command results in an error.</span></span>  
  
## <a name="rolling-back-a-transaction"></a><span data-ttu-id="0534c-131">回滚事务</span><span class="sxs-lookup"><span data-stu-id="0534c-131">Rolling Back a Transaction</span></span>  
 <span data-ttu-id="0534c-132">`RollbackTransaction` 命令可回滚对当前会话运行 `BeginTransaction` 命令后运行的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="0534c-132">The `RollbackTransaction` command rolls back the results of commands that are run after the `BeginTransaction` command was run on the current session.</span></span> <span data-ttu-id="0534c-133">无论当前事务引用计数如何，`RollbackTransaction` 命令都将回滚活动事务，并将事务引用计数设置为零。</span><span class="sxs-lookup"><span data-stu-id="0534c-133">The `RollbackTransaction` command rolls back the active transaction, regardless of the current transaction reference count, and sets the transaction reference count to zero.</span></span> <span data-ttu-id="0534c-134">如果不存在活动事务（换言之，当前会话的事务引用计数已设置为零），则 `RollbackTransaction` 命令将导致出错。</span><span class="sxs-lookup"><span data-stu-id="0534c-134">If there is no active transaction (in other words, the transaction reference count for the current session is already set to zero), a `RollbackTransaction` command results in an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0534c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0534c-135">See Also</span></span>  
 [<span data-ttu-id="0534c-136">在 Analysis Services 中使用 XMLA 开发</span><span class="sxs-lookup"><span data-stu-id="0534c-136">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
