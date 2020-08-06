---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688829"
---
# <a name="mssql_eng020598"></a><span data-ttu-id="a16ef-102">MSSQL_ENG020598</span><span class="sxs-lookup"><span data-stu-id="a16ef-102">MSSQL_ENG020598</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a16ef-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="a16ef-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a16ef-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="a16ef-104">Product Name</span></span>|<span data-ttu-id="a16ef-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a16ef-105">SQL Server</span></span>|  
|<span data-ttu-id="a16ef-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="a16ef-106">Event ID</span></span>|<span data-ttu-id="a16ef-107">20598</span><span class="sxs-lookup"><span data-stu-id="a16ef-107">20598</span></span>|  
|<span data-ttu-id="a16ef-108">事件源</span><span class="sxs-lookup"><span data-stu-id="a16ef-108">Event Source</span></span>|<span data-ttu-id="a16ef-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a16ef-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a16ef-110">组件</span><span class="sxs-lookup"><span data-stu-id="a16ef-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a16ef-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="a16ef-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a16ef-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="a16ef-112">Message Text</span></span>|<span data-ttu-id="a16ef-113">应用复制的命令时在订阅服务器上找不到该行。</span><span class="sxs-lookup"><span data-stu-id="a16ef-113">The row was not found at the Subscriber when applying the replicated command.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a16ef-114">说明</span><span class="sxs-lookup"><span data-stu-id="a16ef-114">Explanation</span></span>  
 <span data-ttu-id="a16ef-115">如果分发代理尝试更新订阅服务器上的行，但该行已删除或该行的主键已更改，则事务性复制中会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="a16ef-115">This error is raised in transactional replication if the Distribution Agent attempts to update a row at the Subscriber, but the row has been deleted or the primary key of the row has been changed.</span></span> <span data-ttu-id="a16ef-116">默认情况下，事务发布的订阅服务器应视为只读，因为更改不会传播回发布服务器。</span><span class="sxs-lookup"><span data-stu-id="a16ef-116">By default, Subscribers to transactional publications should be treated as read-only, because changes are not propagated back to the Publisher.</span></span> <span data-ttu-id="a16ef-117">对于事务性复制，只有使用可更新订阅或对等复制，才能在订阅服务器上进行用户更改。</span><span class="sxs-lookup"><span data-stu-id="a16ef-117">For transactional replication, user changes should be made at the Subscriber only if updatable subscriptions or peer-to-peer replication is used.</span></span> <span data-ttu-id="a16ef-118">有关这些选项的信息，请参阅 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) 和 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ef-118">For information about these options, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) and [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a16ef-119">用户操作</span><span class="sxs-lookup"><span data-stu-id="a16ef-119">User Action</span></span>  
 <span data-ttu-id="a16ef-120">**解决此问题：**</span><span class="sxs-lookup"><span data-stu-id="a16ef-120">**To resolve this problem:**</span></span>  
  
1.  <span data-ttu-id="a16ef-121">如果在确定错误源的同时复制必须继续，请为分发代理指定参数 **-SkipErrors 20598** 。</span><span class="sxs-lookup"><span data-stu-id="a16ef-121">If replication must continue while you identify the source of the error, specify the parameter **-SkipErrors 20598** for the Distribution Agent.</span></span> <span data-ttu-id="a16ef-122">这样可以使代理跳过导致错误 20598 的更改，同时还可以复制其他更改。</span><span class="sxs-lookup"><span data-stu-id="a16ef-122">This allows the agent to skip changes that result in error 20598, while allowing other changes to be replicated.</span></span>  
  
2.  <span data-ttu-id="a16ef-123">标识订阅服务器上已删除的行，或主键与发布服务器上的相应行的主键不同的行。</span><span class="sxs-lookup"><span data-stu-id="a16ef-123">Identify which rows at the Subscriber have been deleted or have a different primary key than the corresponding rows at the Publisher.</span></span> <span data-ttu-id="a16ef-124">可以使用 [tablediff Utility](../../tools/tablediff-utility.md) 来确定发布服务器和订阅服务器中不同的行。</span><span class="sxs-lookup"><span data-stu-id="a16ef-124">You can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span> <span data-ttu-id="a16ef-125">有关如何将此实用工具与复制数据库配合使用的信息，请参阅[比较所复制表的差异（复制编程）](administration/compare-replicated-tables-for-differences-replication-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ef-125">For information about using this utility with replicated databases, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).</span></span>  
  
3.  <span data-ttu-id="a16ef-126">使用 **tablediff** 实用工具或其他方法更正订阅服务器上的行。</span><span class="sxs-lookup"><span data-stu-id="a16ef-126">Correct the rows at the Subscriber using the **tablediff** utility or another method.</span></span>  
  
4.  <span data-ttu-id="a16ef-127">（可选）删除 **-SkipErrors** 参数。</span><span class="sxs-lookup"><span data-stu-id="a16ef-127">(Optional) Remove the **-SkipErrors** parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16ef-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a16ef-128">See Also</span></span>  
 [<span data-ttu-id="a16ef-129">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="a16ef-129">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
