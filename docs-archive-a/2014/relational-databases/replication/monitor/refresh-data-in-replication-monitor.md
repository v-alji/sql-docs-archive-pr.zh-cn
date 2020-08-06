---
title: 刷新复制监视器中的数据 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2f097dea21b06540293e9b60b7de9315323b4168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693753"
---
# <a name="refresh-data-in-replication-monitor"></a><span data-ttu-id="85542-102">刷新复制监视器中的数据</span><span class="sxs-lookup"><span data-stu-id="85542-102">Refresh Data in Replication Monitor</span></span>
  <span data-ttu-id="85542-103">在复制监视器中，可以自动或手动刷新主窗口和详细信息窗口（从主窗口启动的那些窗口）。</span><span class="sxs-lookup"><span data-stu-id="85542-103">In Replication Monitor, the main window and detail windows (those windows launched from the main window) can be refreshed automatically or manually.</span></span> <span data-ttu-id="85542-104">若要手动刷新窗口，请按 F5 键。</span><span class="sxs-lookup"><span data-stu-id="85542-104">To refresh a window manually, press F5.</span></span> <span data-ttu-id="85542-105">默认情况下，主窗口每五分钟自动刷新一次。每个发布服务器的刷新速率均可以自定义。</span><span class="sxs-lookup"><span data-stu-id="85542-105">By default, the main window is refreshed automatically every five seconds; the rate can be customized for each Publisher.</span></span>  
  
 <span data-ttu-id="85542-106">从缓存查询复制监视器中显示的数据。有关缓存和刷新复制监视器之间的关系的信息，请参阅[缓存、刷新和复制监视器性能](caching-refresh-and-replication-monitor-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="85542-106">The data displayed in Replication Monitor is queried from a cache; for information about the relationship between the cache and refreshing Replication Monitor, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span> <span data-ttu-id="85542-107">有关启动复制监视器的信息，请参阅[启动复制监视器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="85542-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a><span data-ttu-id="85542-108">设置复制监视器的刷新选项</span><span class="sxs-lookup"><span data-stu-id="85542-108">To set refresh options for Replication Monitor</span></span>  
  
1.  <span data-ttu-id="85542-109">右键单击复制监视器左窗格中的发布服务器，然后单击 **“发布服务器设置”** 。</span><span class="sxs-lookup"><span data-stu-id="85542-109">Right-click a Publisher in the left pane of Replication Monitor, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="85542-110">在 **“发布服务器设置”** 对话框中，设置 **“自动刷新”** 和 **“刷新速率”** 选项。</span><span class="sxs-lookup"><span data-stu-id="85542-110">In the **Publisher Settings** dialog box, set the **Auto refresh** and **Refresh rate** options.</span></span> <span data-ttu-id="85542-111">**“自动刷新”** 设置会影响复制监视器的主窗口。</span><span class="sxs-lookup"><span data-stu-id="85542-111">The **Auto refresh** setting affects the main window in Replication Monitor.</span></span> <span data-ttu-id="85542-112">**“刷新速率”** 设置也会影响任何设置为自动刷新的详细信息窗口，对该设置的更改仅影响以后打开的详细信息窗口。</span><span class="sxs-lookup"><span data-stu-id="85542-112">The **Refresh rate** setting also affects any detail windows that are set to refresh automatically (changes to the setting only affect the detail windows opened after the change).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a><span data-ttu-id="85542-113">指定详细信息窗口应自动刷新</span><span class="sxs-lookup"><span data-stu-id="85542-113">To specify that a detail window should automatically refresh</span></span>  
  
1.  <span data-ttu-id="85542-114">打开复制监视器中的详细信息窗口。</span><span class="sxs-lookup"><span data-stu-id="85542-114">Open a detail window in Replication Monitor.</span></span> <span data-ttu-id="85542-115">例如：</span><span class="sxs-lookup"><span data-stu-id="85542-115">For example:</span></span>  
  
    1.  <span data-ttu-id="85542-116">在左窗格中展开发布服务器组，再展开其中的一个发布服务器，然后单击其中的一个发布。</span><span class="sxs-lookup"><span data-stu-id="85542-116">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
    2.  <span data-ttu-id="85542-117">单击 **“所有订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="85542-117">Click the **All Subscriptions** tab.</span></span>  
  
    3.  <span data-ttu-id="85542-118">右键单击订阅，然后单击 **“查看详细信息”** 。</span><span class="sxs-lookup"><span data-stu-id="85542-118">Right-click a subscription, and then click **View Details**.</span></span>  
  
2.  <span data-ttu-id="85542-119">在“订阅 \<SubscriptionName>”详细信息窗口中，单击“操作”，然后单击“自动刷新”  。</span><span class="sxs-lookup"><span data-stu-id="85542-119">In the **Subscription \<SubscriptionName>** detail window, click **Action**, and then click **Auto Refresh**.</span></span> <span data-ttu-id="85542-120">刷新速率由 **“发布服务器设置”** 对话框中的 **“刷新速率”** 设置决定。</span><span class="sxs-lookup"><span data-stu-id="85542-120">The refresh rate is determined by the **Refresh rate** setting in the **Publisher Settings** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85542-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85542-121">See Also</span></span>  
 [<span data-ttu-id="85542-122">监视复制</span><span class="sxs-lookup"><span data-stu-id="85542-122">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
