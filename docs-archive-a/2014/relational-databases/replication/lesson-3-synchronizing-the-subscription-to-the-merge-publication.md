---
title: 第 3 课：同步合并发布订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
author: rothja
ms.author: jroth
ms.openlocfilehash: bf0256c69d69d1236869fa83285bf4dbf5c462da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692845"
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a><span data-ttu-id="4c742-102">第 3 课：使订阅与合并发布同步</span><span class="sxs-lookup"><span data-stu-id="4c742-102">Lesson 3: Synchronizing the Subscription to the Merge Publication</span></span>
  <span data-ttu-id="4c742-103">在本课中，您将使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]启动合并代理以初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4c742-103">In this lesson, you will start the Merge Agent to initialize the subscription using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4c742-104">您还将使用此过程与发布服务器同步。</span><span class="sxs-lookup"><span data-stu-id="4c742-104">You also use this procedure to synchronize with the Publisher.</span></span> <span data-ttu-id="4c742-105">本课程要求已完成上一课， [第 2 课：创建合并发布订阅](lesson-2-creating-a-subscription-to-the-merge-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="4c742-105">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Merge Publication](lesson-2-creating-a-subscription-to-the-merge-publication.md).</span></span>  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a><span data-ttu-id="4c742-106">启动同步并初始化订阅</span><span class="sxs-lookup"><span data-stu-id="4c742-106">To start synchronization and initialize the subscription</span></span>  
  
1.  <span data-ttu-id="4c742-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到订阅服务器，展开服务器节点，然后展开 **“复制”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="4c742-107">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, and then expand the **Replication** folder.</span></span>  
  
2.  <span data-ttu-id="4c742-108">在 **“本地订阅”** 文件夹中，右键单击 **SalesOrdersReplica** 数据库中的订阅，再单击 **“查看同步状态”**。</span><span class="sxs-lookup"><span data-stu-id="4c742-108">In the **Local Subscriptions** folder, right-click the subscription in the **SalesOrdersReplica** database, and then click **View Synchronization Status**.</span></span>  
  
3.  <span data-ttu-id="4c742-109">单击 **“启动”** 以初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4c742-109">Click **Start** to initialize the subscription.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4c742-110">后续步骤</span><span class="sxs-lookup"><span data-stu-id="4c742-110">Next Steps</span></span>  
 <span data-ttu-id="4c742-111">您已成功运行合并代理来启动同步并初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="4c742-111">You have successfully run the Merge Agent to start synchronization and initialize the subscription.</span></span> <span data-ttu-id="4c742-112">您还可以在发布服务器或订阅服务器的 **SalesOrderHeader** 或 **SalesOrderDetail** 表中插入、更新或删除数据，当网络连接可用时重复此过程以在发布服务器和订阅服务器之间同步数据，然后在其他服务器上查询 **SalesOrderHeader** 或 **SalesOrderDetail** 表以查看复制的更改。</span><span class="sxs-lookup"><span data-stu-id="4c742-112">You can also insert, update, or delete data in the **SalesOrderHeader** or **SalesOrderDetail** tables at the Publisher or Subscriber, repeat this procedure when network connectivity is available to synchronize data between the Publisher and the Subscriber, and then query the **SalesOrderHeader** or **SalesOrderDetail** tables at the other server to view the replicated changes.</span></span>  
  
 <span data-ttu-id="4c742-113">这样就完成了“涉及移动客户端的数据复制”教程。</span><span class="sxs-lookup"><span data-stu-id="4c742-113">This completes the Replicating Data with Mobile Clients tutorial.</span></span> <span data-ttu-id="4c742-114">有关使用事务复制的类似教程，请参阅 [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="4c742-114">For a similar tutorial that uses transactional replication, see [Tutorial: Replicating Data Between Continuously Connected Servers](tutorial-replicating-data-between-continuously-connected-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c742-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4c742-115">See Also</span></span>  
 <span data-ttu-id="4c742-116">[使用快照初始化订阅](initialize-a-subscription-with-a-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="4c742-116">[Initialize a Subscription with a Snapshot](initialize-a-subscription-with-a-snapshot.md) </span></span>  
 <span data-ttu-id="4c742-117">[同步数据](synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="4c742-117">[Synchronize Data](synchronize-data.md) </span></span>  
 [<span data-ttu-id="4c742-118">同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="4c742-118">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)  
  
  
