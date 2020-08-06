---
title: 初始化订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8c9388138ddec275dc1abd2b75e0b0c7fc99de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578064"
---
# <a name="initialize-subscriptions"></a><span data-ttu-id="40895-102">初始化订阅</span><span class="sxs-lookup"><span data-stu-id="40895-102">Initialize Subscriptions</span></span>
  <span data-ttu-id="40895-103">必须先初始化订阅服务器，然后才能接收复制的数据。</span><span class="sxs-lookup"><span data-stu-id="40895-103">Subscribers must be initialized before they can begin receiving replicated data.</span></span> <span data-ttu-id="40895-104">订阅服务器可以没有初始的数据集，但对于复制的每个对象以及复制所需的任何元数据表和过程，必须要具有相应的架构。</span><span class="sxs-lookup"><span data-stu-id="40895-104">An initial dataset is not required, but the Subscriber must at least have the schema for each replicated object and any metadata tables and procedures required by replication.</span></span>  
  
## <a name="options"></a><span data-ttu-id="40895-105">选项</span><span class="sxs-lookup"><span data-stu-id="40895-105">Options</span></span>  
 <span data-ttu-id="40895-106">**订阅属性**</span><span class="sxs-lookup"><span data-stu-id="40895-106">**Subscription properties**</span></span>  
 <span data-ttu-id="40895-107">对于需要初始数据集的每个订阅服务器，请选中 **“初始化”** 列中的相应复选框。</span><span class="sxs-lookup"><span data-stu-id="40895-107">Select the check box in the **Initialize** column for each Subscriber that requires an initial data set.</span></span> <span data-ttu-id="40895-108">如果该复选框为清除状态，将只初始化复制元数据和过程。</span><span class="sxs-lookup"><span data-stu-id="40895-108">If the check box is cleared, only the replication metadata and procedures will be initialized.</span></span> <span data-ttu-id="40895-109">有关不使用快照初始化订阅的详细信息，请参阅[初始化事务订阅（不使用快照）](initialize-a-transactional-subscription-without-a-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="40895-109">For more information about initializing a subscription without a snapshot, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="40895-110">如果在 **“初始化时间”** 列的下拉列表框中选择 **“立即”** ，那么，合并代理或分发代理会在此向导完成后将快照文件传输到订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="40895-110">Select **Immediately** from the drop-down list box in the **Initialize When** column to have the Merge Agent or Distribution Agent transfer snapshot files to the Subscriber after this wizard is completed.</span></span> <span data-ttu-id="40895-111">如果选择 **“首先同步”** ，代理则会在下次计划运行的时候传输文件。</span><span class="sxs-lookup"><span data-stu-id="40895-111">Select **At first synchronization** to have the agent transfer the files the next time it is scheduled to run.</span></span> <span data-ttu-id="40895-112">“立即”选项不可用于对   的请求订阅[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="40895-112">The **Immediately** option is not available for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> <span data-ttu-id="40895-113">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]的实例上不能运行合并代理和分发代理，因此必须通过其他方法初始化订阅。</span><span class="sxs-lookup"><span data-stu-id="40895-113">The Merge Agent and Distribution Agent do not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]; therefore the subscription must be initialized through another method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40895-114">该向导可能会提示您连接到分发服务器，以启动分发代理或合并代理的相应作业。</span><span class="sxs-lookup"><span data-stu-id="40895-114">The wizard might prompt for a connection to the Distributor in order to start the appropriate job for the Distribution Agent or Merge Agent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40895-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40895-115">See Also</span></span>  
 <span data-ttu-id="40895-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="40895-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="40895-117">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="40895-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="40895-118">[初始化订阅](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="40895-118">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="40895-119">订阅发布</span><span class="sxs-lookup"><span data-stu-id="40895-119">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
