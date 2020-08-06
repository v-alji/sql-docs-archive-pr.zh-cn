---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6afa81a05eea37bc67cd2e9ac2433b6c82f35b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576805"
---
# <a name="mssqlserver_1205"></a><span data-ttu-id="dadf1-102">MSSQLSERVER_1205</span><span class="sxs-lookup"><span data-stu-id="dadf1-102">MSSQLSERVER_1205</span></span>
    
## <a name="details"></a><span data-ttu-id="dadf1-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="dadf1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dadf1-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="dadf1-104">Product Name</span></span>|<span data-ttu-id="dadf1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="dadf1-105">SQL Server</span></span>|  
|<span data-ttu-id="dadf1-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="dadf1-106">Event ID</span></span>|<span data-ttu-id="dadf1-107">1205</span><span class="sxs-lookup"><span data-stu-id="dadf1-107">1205</span></span>|  
|<span data-ttu-id="dadf1-108">事件源</span><span class="sxs-lookup"><span data-stu-id="dadf1-108">Event Source</span></span>|<span data-ttu-id="dadf1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="dadf1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="dadf1-110">组件</span><span class="sxs-lookup"><span data-stu-id="dadf1-110">Component</span></span>|<span data-ttu-id="dadf1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="dadf1-111">SQLEngine</span></span>|  
|<span data-ttu-id="dadf1-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="dadf1-112">Symbolic Name</span></span>|<span data-ttu-id="dadf1-113">LK_VICTIM</span><span class="sxs-lookup"><span data-stu-id="dadf1-113">LK_VICTIM</span></span>|  
|<span data-ttu-id="dadf1-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="dadf1-114">Message Text</span></span>|<span data-ttu-id="dadf1-115">事务(进程 ID %d)与另一个进程被死锁在 %.\*ls 资源上，并且已被选作死锁牺牲品。</span><span class="sxs-lookup"><span data-stu-id="dadf1-115">Transaction (Process ID %d) was deadlocked on %.\*ls resources with another process and has been chosen as the deadlock victim.</span></span> <span data-ttu-id="dadf1-116">重新运行该事务。</span><span class="sxs-lookup"><span data-stu-id="dadf1-116">Rerun the transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dadf1-117">说明</span><span class="sxs-lookup"><span data-stu-id="dadf1-117">Explanation</span></span>  
 <span data-ttu-id="dadf1-118">在单独的事务上以相互冲突的顺序访问资源，从而导致死锁。</span><span class="sxs-lookup"><span data-stu-id="dadf1-118">Resources are accessed in conflicting order on separate transactions, causing a deadlock.</span></span> <span data-ttu-id="dadf1-119">例如：</span><span class="sxs-lookup"><span data-stu-id="dadf1-119">For example:</span></span>  
  
-   <span data-ttu-id="dadf1-120">Transaction1 更新 **Table1.Row1**，而 Transaction2 更新 **Table2.Row2**。</span><span class="sxs-lookup"><span data-stu-id="dadf1-120">Transaction1 updates **Table1.Row1**, while Transaction2 updates **Table2.Row2**.</span></span>  
  
-   <span data-ttu-id="dadf1-121">Transaction1 尝试更新 **Table2.Row2**，但因 Transaction2 尚未提交而被阻止。</span><span class="sxs-lookup"><span data-stu-id="dadf1-121">Transaction1 tries to update **Table2.Row2** but is blocked because Transaction2 has not yet committed.</span></span>  
  
-   <span data-ttu-id="dadf1-122">Transaction2 现在尝试更新 **Table1.Row1**，但因 Transaction1 尚未提交而被阻止。</span><span class="sxs-lookup"><span data-stu-id="dadf1-122">Transaction2 now tries to update **Table1.Row1** but is blocked because Transaction1 has not committed.</span></span>  
  
-   <span data-ttu-id="dadf1-123">之所以出现死锁，是因为 Transaction1 在等待 Transaction2 完成，但 Transaction2 在等待 Transaction1 完成。</span><span class="sxs-lookup"><span data-stu-id="dadf1-123">A deadlock occurs because Transaction1 is waiting for Transaction2 to complete, but Transaction2 is waiting for Transaction1 to complete.</span></span>  
  
 <span data-ttu-id="dadf1-124">系统将检测到此死锁并将选择其中一个作为“受害者”的事务，并将发出此消息，回滚受害者的事务。</span><span class="sxs-lookup"><span data-stu-id="dadf1-124">The system will detect this deadlock and will choose one of the transactions involved as a 'victim' and will issue this message, rolling back the victim's transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dadf1-125">用户操作</span><span class="sxs-lookup"><span data-stu-id="dadf1-125">User Action</span></span>  
 <span data-ttu-id="dadf1-126">重新执行事务。</span><span class="sxs-lookup"><span data-stu-id="dadf1-126">Execute the transaction again.</span></span> <span data-ttu-id="dadf1-127">您还可以修订应用程序以避免死锁。</span><span class="sxs-lookup"><span data-stu-id="dadf1-127">You can also revise the application to avoid deadlocks.</span></span> <span data-ttu-id="dadf1-128">可以重试被选作牺牲品的事务，而且很可能成功，具体取决于同时执行的操作。</span><span class="sxs-lookup"><span data-stu-id="dadf1-128">The transaction that was chosen as a victim can be retried and will likely succeed, depending on what operations are being executed simultaneously.</span></span>  
  
 <span data-ttu-id="dadf1-129">为防止或避免出现死锁，请考虑让所有的事务按相同顺序（先访问 **Table1**，然后访问 **Table2**）访问行；这样，虽然可能会出现阻止，但不会出现死锁。</span><span class="sxs-lookup"><span data-stu-id="dadf1-129">To prevent or avoid deadlocks from occurring, consider having all transactions access rows in the same order (**Table1**, then **Table2**); this way, although blocking might occur, a deadlock will not occur.</span></span>  
  
  
