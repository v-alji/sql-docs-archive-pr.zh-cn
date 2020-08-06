---
title: 可更新订阅 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 447114152365e098420f46d4b7e880e8f2907864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688806"
---
# <a name="updatable-subscriptions"></a><span data-ttu-id="0f96d-102">可更新订阅</span><span class="sxs-lookup"><span data-stu-id="0f96d-102">Updatable Subscriptions</span></span>
  <span data-ttu-id="0f96d-103">如果使用的是事务复制，应将复制的数据视为只读数据；不过，可以使用可更新的订阅，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 订阅服务器上修改复制的数据。</span><span class="sxs-lookup"><span data-stu-id="0f96d-103">With transactional replication, replicated data should be treated as read-only; however, you can modify replicated data at a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber by using updatable subscriptions.</span></span> <span data-ttu-id="0f96d-104">如果需要在订阅服务器上修改数据，请根据您的要求选择下列选项之一。</span><span class="sxs-lookup"><span data-stu-id="0f96d-104">If you need to modify data at the Subscriber, choose one of the following options depending on your requirements.</span></span>  
  
|<span data-ttu-id="0f96d-105">可更新订阅类型</span><span class="sxs-lookup"><span data-stu-id="0f96d-105">Updatable Subscription Type</span></span>|<span data-ttu-id="0f96d-106">要求</span><span class="sxs-lookup"><span data-stu-id="0f96d-106">Requirements</span></span>|  
|---------------------------------|------------------|  
|<span data-ttu-id="0f96d-107">立即更新</span><span class="sxs-lookup"><span data-stu-id="0f96d-107">Immediate Updating</span></span>|<span data-ttu-id="0f96d-108">必须连接发布服务器和订阅服务器才能更新订阅服务器上的数据。</span><span class="sxs-lookup"><span data-stu-id="0f96d-108">Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>|  
|<span data-ttu-id="0f96d-109">排队更新</span><span class="sxs-lookup"><span data-stu-id="0f96d-109">Queued Updating</span></span>|<span data-ttu-id="0f96d-110">不必连接发布服务器和订阅服务器即可更新订阅服务器上的数据。</span><span class="sxs-lookup"><span data-stu-id="0f96d-110">Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="0f96d-111">可以在脱机状态下进行更新，之后还可以在发布服务器与订阅服务器之间同步更新。</span><span class="sxs-lookup"><span data-stu-id="0f96d-111">Updates can be made while offline, and later synchronized between the Publisher and Subscriber.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="0f96d-112">选项</span><span class="sxs-lookup"><span data-stu-id="0f96d-112">Options</span></span>  
 <span data-ttu-id="0f96d-113">**复制订阅服务器更改**</span><span class="sxs-lookup"><span data-stu-id="0f96d-113">**Replicate Subscriber changes**</span></span>  
 <span data-ttu-id="0f96d-114">对于每个应该能够进行更新的订阅服务器，选中 **“复制”** 列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="0f96d-114">Select the check box in the **Replicate** column for each Subscriber that should be able to make updates.</span></span> <span data-ttu-id="0f96d-115">对于能够进行更新的订阅服务器，请从 **“在发布服务器提交”** 列的下拉列表框中选择相应的选项：</span><span class="sxs-lookup"><span data-stu-id="0f96d-115">For those Subscribers that can make updates, select the appropriate option from the drop-down list box in the **Commit at Publisher** column:</span></span>  
  
-   <span data-ttu-id="0f96d-116">对于立即更新订阅，请选择 **“同时提交更改”** 。</span><span class="sxs-lookup"><span data-stu-id="0f96d-116">Select **Simultaneously commit changes** for an immediate updating subscription.</span></span>  
  
-   <span data-ttu-id="0f96d-117">对于排队更新订阅，请选择 **“对更改进行排队并在可能时提交”** 。</span><span class="sxs-lookup"><span data-stu-id="0f96d-117">Select **Queue changes and commit when possible** for a queued updating subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f96d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f96d-118">See Also</span></span>  
 <span data-ttu-id="0f96d-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0f96d-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="0f96d-120">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="0f96d-120">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="0f96d-121">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="0f96d-121">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="0f96d-122">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="0f96d-122">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
