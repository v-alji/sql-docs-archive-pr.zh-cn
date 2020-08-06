---
title: 第 3 课：验证订阅和测量滞后时间 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: rothja
ms.author: jroth
ms.openlocfilehash: e4893c054d25d131eb2f88f32291606b0b789af7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692844"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a><span data-ttu-id="7604d-102">第 3 课：验证订阅和测量滞后时间</span><span class="sxs-lookup"><span data-stu-id="7604d-102">Lesson 3: Validating the Subscription and Measuring Latency</span></span>
  <span data-ttu-id="7604d-103">在本课中，将使用跟踪令牌验证将更改复制到订阅服务器并确定滞后时间，即，发布服务器上所做的更改出现在订阅服务器中所需的时间。</span><span class="sxs-lookup"><span data-stu-id="7604d-103">In this lesson, you will use tracer tokens to verify that changes are being replicated to the Subscriber and to determine latency, the time it takes for a change made at the Publisher to appear to the Subscriber.</span></span> <span data-ttu-id="7604d-104">本课程要求已完成上一课， [第 2 课：创建事务发布的订阅](lesson-2-creating-a-subscription-to-the-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="7604d-104">This lesson requires that you have completed the previous lesson, [Lesson 2: Creating a Subscription to the Transactional Publication](lesson-2-creating-a-subscription-to-the-transactional-publication.md).</span></span>  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="7604d-105">插入跟踪令牌并查看有关令牌的信息</span><span class="sxs-lookup"><span data-stu-id="7604d-105">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="7604d-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中连接到发布服务器，展开服务器节点，右键单击 **“复制”** 文件夹，然后单击 **“启动复制监视器”**。</span><span class="sxs-lookup"><span data-stu-id="7604d-106">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand the server node, right-click the **Replication** folder, and then click **Launch Replication Monitor**.</span></span>  
  
     <span data-ttu-id="7604d-107">复制监视器启动。</span><span class="sxs-lookup"><span data-stu-id="7604d-107">Replication Monitor launches.</span></span>  
  
2.  <span data-ttu-id="7604d-108">在左窗格中展开发布服务器组，展开发布服务器实例，然后单击 **AdvWorksProductTrans** 发布。</span><span class="sxs-lookup"><span data-stu-id="7604d-108">Expand a Publisher group in the left pane, expand the Publisher instance, and then click the **AdvWorksProductTrans** publication.</span></span>  
  
3.  <span data-ttu-id="7604d-109">单击 **“跟踪令牌”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7604d-109">Click the **Tracer Tokens** tab.</span></span>  
  
4.  <span data-ttu-id="7604d-110">单击 **“插入跟踪器”**。</span><span class="sxs-lookup"><span data-stu-id="7604d-110">Click **Insert Tracer**.</span></span>  
  
5.  <span data-ttu-id="7604d-111">在以下列中查看跟踪令牌的运行时间： **“发布服务器到分发服务器”**、 **“分发服务器到订阅服务器”**、 **“总滞后时间”**。</span><span class="sxs-lookup"><span data-stu-id="7604d-111">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="7604d-112">值为 "**挂起**" 表示令牌尚未到达给定点。</span><span class="sxs-lookup"><span data-stu-id="7604d-112">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7604d-113">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7604d-113">Next Steps</span></span>  
 <span data-ttu-id="7604d-114">在本课中，您成功地使用跟踪令牌验证了正在将数据更改从发布服务器复制到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="7604d-114">In this lesson, you successfully used tracer tokens to validate that data changes are being replicated from the Publisher to the Subscriber.</span></span> <span data-ttu-id="7604d-115">您还可以在发布服务器的 **Product** 表中插入、更新或删除数据，并且可以在完成复制后，查询订阅服务器中的 **Product** 表以查看这些更改。</span><span class="sxs-lookup"><span data-stu-id="7604d-115">You can also insert, update, or delete data in the **Product** table at the Publisher and query the **Product** table at the Subscriber to view these changes after they are replicated.</span></span>  
  
 <span data-ttu-id="7604d-116">现在将完成“在连续连接的服务器之间复制数据”教程。</span><span class="sxs-lookup"><span data-stu-id="7604d-116">This completes the Replicating Data Between Continuously Connected Servers tutorial.</span></span> <span data-ttu-id="7604d-117">有关使用合并复制的类似教程，请参阅 [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="7604d-117">For a similar tutorial that uses merge replication, see [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7604d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7604d-118">See Also</span></span>  
 [<span data-ttu-id="7604d-119">为事务复制测量滞后时间和验证连接</span><span class="sxs-lookup"><span data-stu-id="7604d-119">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
