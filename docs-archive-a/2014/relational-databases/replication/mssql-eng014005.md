---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d820fd26cceee72b0d08204d6f6ce73a76508e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577558"
---
# <a name="mssql_eng014005"></a><span data-ttu-id="c467e-102">MSSQL_ENG014005</span><span class="sxs-lookup"><span data-stu-id="c467e-102">MSSQL_ENG014005</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c467e-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="c467e-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c467e-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c467e-104">Product Name</span></span>|<span data-ttu-id="c467e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c467e-105">SQL Server</span></span>|  
|<span data-ttu-id="c467e-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c467e-106">Event ID</span></span>|<span data-ttu-id="c467e-107">14005</span><span class="sxs-lookup"><span data-stu-id="c467e-107">14005</span></span>|  
|<span data-ttu-id="c467e-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c467e-108">Event Source</span></span>|<span data-ttu-id="c467e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c467e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c467e-110">组件</span><span class="sxs-lookup"><span data-stu-id="c467e-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c467e-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="c467e-111">Symbolic Name</span></span>||  
|<span data-ttu-id="c467e-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="c467e-112">Message Text</span></span>|<span data-ttu-id="c467e-113">无法删除发布。</span><span class="sxs-lookup"><span data-stu-id="c467e-113">Could not drop publication.</span></span> <span data-ttu-id="c467e-114">该发布已有订阅。</span><span class="sxs-lookup"><span data-stu-id="c467e-114">A subscription exists to it.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c467e-115">说明</span><span class="sxs-lookup"><span data-stu-id="c467e-115">Explanation</span></span>  
 <span data-ttu-id="c467e-116">您试图删除带有关联的订阅的发布。</span><span class="sxs-lookup"><span data-stu-id="c467e-116">You have tried to drop a publication which has one or more associated subscriptions.</span></span> <span data-ttu-id="c467e-117">只有发布不具有相关联的订阅时才可删除它。</span><span class="sxs-lookup"><span data-stu-id="c467e-117">A publication can only be dropped if there are no associated subscriptions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c467e-118">用户操作</span><span class="sxs-lookup"><span data-stu-id="c467e-118">User Action</span></span>  
 <span data-ttu-id="c467e-119">删除发布前请先删除订阅。</span><span class="sxs-lookup"><span data-stu-id="c467e-119">Drop the subscriptions before dropping the publication.</span></span> <span data-ttu-id="c467e-120">如果用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 删除发布，它会提供选项使您可以在删除发布前自动删除所有相关联的订阅。</span><span class="sxs-lookup"><span data-stu-id="c467e-120">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to drop the publication, it will give you the option to automatically drop all associated subscriptions before dropping the publication.</span></span> <span data-ttu-id="c467e-121">如果用存储过程，则必须首先显式删除订阅。</span><span class="sxs-lookup"><span data-stu-id="c467e-121">If you use stored procedures, you must explicitly drop the subscriptions first.</span></span> <span data-ttu-id="c467e-122">有关详细信息，请参阅 [Delete a Push Subscription](delete-a-push-subscription.md) 和 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c467e-122">For more information, see [Delete a Push Subscription](delete-a-push-subscription.md) and [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="c467e-123">如果看起来发布不存在订阅或者在创建发布时看到此错误，则说明可能存在以前删除时未完全清除的订阅。</span><span class="sxs-lookup"><span data-stu-id="c467e-123">If no subscriptions appear to exist for the publication or if you see this error when you create a publication, you might have a previous subscription that was not completely cleaned up when it was removed.</span></span> <span data-ttu-id="c467e-124">对数据库执行 [sp_removedbreplication (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，以删除所有与复制相关的对象和设置。</span><span class="sxs-lookup"><span data-stu-id="c467e-124">Execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) on the database to remove all objects and settings related to replication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c467e-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c467e-125">See Also</span></span>  
 [<span data-ttu-id="c467e-126">错误和事件参考（复制）</span><span class="sxs-lookup"><span data-stu-id="c467e-126">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
