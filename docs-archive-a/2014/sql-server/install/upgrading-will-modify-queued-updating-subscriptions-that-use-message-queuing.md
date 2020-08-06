---
title: 升级将修改使用消息队列的排队更新订阅 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694222"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a><span data-ttu-id="17097-102">升级将修改使用消息队列的排队更新订阅</span><span class="sxs-lookup"><span data-stu-id="17097-102">Upgrading will modify queued updating subscriptions that use Message Queuing</span></span>
  <span data-ttu-id="17097-103">升级顾问检测到您可能有一个或多个使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 消息队列（又称为 MSMQ）的排队更新订阅。</span><span class="sxs-lookup"><span data-stu-id="17097-103">Upgrade Advisor detected that you might have one or more queued updating subscriptions that use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="17097-104">复制不再支持消息队列；因此，将对订阅进行修改以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 队列。</span><span class="sxs-lookup"><span data-stu-id="17097-104">Replication no longer supports Message Queuing; therefore, the subscriptions will be modified to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span>  
  
 <span data-ttu-id="17097-105">只允许使用**sql**值。</span><span class="sxs-lookup"><span data-stu-id="17097-105">Only a value of **sql** is allowed.</span></span> <span data-ttu-id="17097-106">在升级期间，将修改使用消息队列的现有发布从而可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 队列。</span><span class="sxs-lookup"><span data-stu-id="17097-106">Existing publications that use Message Queuing are modified during upgrade to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="17097-107">如果某些应用程序依赖于使用消息队列的排队更新，将必须重写这些应用程序以适应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 队列。</span><span class="sxs-lookup"><span data-stu-id="17097-107">If you have applications that depend on queued updating using Message Queuing, these applications will have to be rewritten to accommodate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="17097-108">有关排队更新订阅的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“事务复制的可更新订阅”。</span><span class="sxs-lookup"><span data-stu-id="17097-108">For more information about queued updating subscriptions, see "Updatable Subscriptions for Transactional Replication" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="17097-109">如果在升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时消息队列服务处于运行之中，则升级过程将删除现有的消息队列订阅队列。</span><span class="sxs-lookup"><span data-stu-id="17097-109">Upgrade will remove the existing Message Queuing subscription queues if the Message Queuing service is running while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being upgraded.</span></span>  
  
 <span data-ttu-id="17097-110">如果未运行消息队列服务，请在升级完成后手动删除这些队列。</span><span class="sxs-lookup"><span data-stu-id="17097-110">If the Message Queuing service is not running, remove the queues manually after upgrade is complete.</span></span> <span data-ttu-id="17097-111">有关如何删除队列的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="17097-111">For more information about how to remove queues, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17097-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17097-112">See Also</span></span>  
 [<span data-ttu-id="17097-113">复制升级问题</span><span class="sxs-lookup"><span data-stu-id="17097-113">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
