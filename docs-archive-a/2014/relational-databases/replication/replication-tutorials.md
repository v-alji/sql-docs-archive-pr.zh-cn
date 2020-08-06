---
title: 复制教程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4d70abd6c58b3eb0fa4a53e2806ab1b3fbe9245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577514"
---
# <a name="replication-tutorials"></a><span data-ttu-id="bdf85-102">复制教程</span><span class="sxs-lookup"><span data-stu-id="bdf85-102">Replication Tutorials</span></span>
  <span data-ttu-id="bdf85-103">在复制教程中，您将学习如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]安装和运行复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="bdf85-103">Replication includes tutorials that you can use to learn how to set up and run replication topologies using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="bdf85-104">在复制教程中，“发布服务器”是指包含将要复制的源数据的服务器，“订阅服务器”是指目标服务器。</span><span class="sxs-lookup"><span data-stu-id="bdf85-104">In the replication tutorials, "Publisher" refers to the server that contains that source data being replicated and "Subscriber" refers to the destination server.</span></span> <span data-ttu-id="bdf85-105">发布服务器和订阅服务器可以共享同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，但这不是必须的。</span><span class="sxs-lookup"><span data-stu-id="bdf85-105">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="bdf85-106">有关详细信息，请参阅 [复制发布模型概述](publish/replication-publishing-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf85-106">For more information, see [Replication Publishing Model Overview](publish/replication-publishing-model-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdf85-107">这些教程中列举的大多数任务都能够以编程方式执行。</span><span class="sxs-lookup"><span data-stu-id="bdf85-107">Most of the tasks shown in these tutorials can be performed programmatically.</span></span> <span data-ttu-id="bdf85-108">有关详细信息，请参阅[开发人员指南 &#40;复制&#41;](concepts/replication-developer-documentation.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf85-108">For more information, see [Developer's Guide &#40;Replication&#41;](concepts/replication-developer-documentation.md).</span></span>  
  
## <a name="replication-tutorials"></a><span data-ttu-id="bdf85-109">复制教程</span><span class="sxs-lookup"><span data-stu-id="bdf85-109">Replication Tutorials</span></span>  
 [<span data-ttu-id="bdf85-110">准备用于复制的服务器</span><span class="sxs-lookup"><span data-stu-id="bdf85-110">Preparing the Server for Replication</span></span>](tutorial-preparing-the-server-for-replication.md)  
 <span data-ttu-id="bdf85-111">学习如何准备服务器以便以最少的权限运行复制。</span><span class="sxs-lookup"><span data-stu-id="bdf85-111">Learn how to prepare servers so that replication can be run with least privileges.</span></span> <span data-ttu-id="bdf85-112">开始其他复制教程之前，必须先完成本教程。</span><span class="sxs-lookup"><span data-stu-id="bdf85-112">You must complete this tutorial before the other replication tutorials.</span></span>  
  
 [<span data-ttu-id="bdf85-113">在连续连接的服务器之间复制数据</span><span class="sxs-lookup"><span data-stu-id="bdf85-113">Replicating Data Between Continuously Connected Servers</span></span>](tutorial-replicating-data-between-continuously-connected-servers.md)  
 <span data-ttu-id="bdf85-114">学习如何使用事务复制在完全连接的服务器之间复制数据。</span><span class="sxs-lookup"><span data-stu-id="bdf85-114">Learn how to use transactional replication to replicate data between fully connected servers.</span></span>  
  
 [<span data-ttu-id="bdf85-115">使用移动客户端复制数据</span><span class="sxs-lookup"><span data-stu-id="bdf85-115">Replicating Data with Mobile Clients</span></span>](tutorial-replicating-data-with-mobile-clients.md)  
 <span data-ttu-id="bdf85-116">学习如何使用合并复制在服务器与仅偶尔连接的一个或多个客户端之间交换数据。</span><span class="sxs-lookup"><span data-stu-id="bdf85-116">Learn how to use merge replication to exchange data between a server and one or more clients that are only occasionally connected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf85-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdf85-117">See Also</span></span>  
 [<span data-ttu-id="bdf85-118">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="bdf85-118">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
