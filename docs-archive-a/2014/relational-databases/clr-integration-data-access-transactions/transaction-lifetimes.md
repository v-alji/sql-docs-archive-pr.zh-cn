---
title: 事务生存期 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c00050ee323cade7493d44c4c296ba4ce6811e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693985"
---
# <a name="transaction-lifetimes"></a><span data-ttu-id="d99ec-102">事务生存期</span><span class="sxs-lookup"><span data-stu-id="d99ec-102">Transaction Lifetimes</span></span>
  <span data-ttu-id="d99ec-103">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程中启动的事务与在托管代码中启动的事务之间存在一个重大区别：公共语言运行时 (CLR) 代码在进入或退出 CLR 调用时不能使事务状态取消均衡。</span><span class="sxs-lookup"><span data-stu-id="d99ec-103">There is an important difference between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and those started in managed code: common language runtime (CLR) code cannot unbalance the transaction state on entry or exit of a CLR invocation.</span></span> <span data-ttu-id="d99ec-104">注意此区别的以下含义：</span><span class="sxs-lookup"><span data-stu-id="d99ec-104">Be aware of the following implications of this difference:</span></span>  
  
-   <span data-ttu-id="d99ec-105">必须提交或回滚在 CLR 框架内启动的事务，否则在退出该框架时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将产生错误。</span><span class="sxs-lookup"><span data-stu-id="d99ec-105">A transaction started inside a CLR frame must be committed or rolled back, or else [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generates an error when the frame is exited.</span></span>  
  
-   <span data-ttu-id="d99ec-106">在 CLR 代码内不能提交或回滚外部事务。</span><span class="sxs-lookup"><span data-stu-id="d99ec-106">An outer transaction cannot be committed or rolled back inside the CLR code.</span></span>  
  
-   <span data-ttu-id="d99ec-107">尝试提交不在同一过程中启动的事务将导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="d99ec-107">An attempt to commit a transaction not started in the same procedure causes a run-time error.</span></span>  
  
-   <span data-ttu-id="d99ec-108">如果尝试回滚不是在同一过程中启动的事务，则会导致事务停止响应 (以防发生任何其他副作用的操作) 。</span><span class="sxs-lookup"><span data-stu-id="d99ec-108">An attempt to roll back a transaction not started in the same procedure causes the transaction to stop responding (preventing any other side-effecting operation from happening).</span></span> <span data-ttu-id="d99ec-109">事务将断开连接，直到 CLR 代码离开作用域。</span><span class="sxs-lookup"><span data-stu-id="d99ec-109">The transaction discontinues until the CLR code goes out of scope.</span></span> <span data-ttu-id="d99ec-110">请注意当您在过程内检测到错误并想确保终止整个事务时，这可能很有用。</span><span class="sxs-lookup"><span data-stu-id="d99ec-110">Note that this can be useful when you detect an error inside your procedure and want to make sure the whole transaction terminates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99ec-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d99ec-111">See Also</span></span>  
 [<span data-ttu-id="d99ec-112">CLR 集成和事务</span><span class="sxs-lookup"><span data-stu-id="d99ec-112">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
