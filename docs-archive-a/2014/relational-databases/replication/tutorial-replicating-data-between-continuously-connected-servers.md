---
title: 教程：在连续连接的服务器之间复制数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 415cac62112c1c1d2aa6c42ec189c2614ec03923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591228"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a><span data-ttu-id="cecab-102">教程：在连续连接的服务器之间复制数据</span><span class="sxs-lookup"><span data-stu-id="cecab-102">Tutorial: Replicating Data Between Continuously Connected Servers</span></span>
  <span data-ttu-id="cecab-103">复制是在连续连接的服务器之间实现数据移动的好方法。</span><span class="sxs-lookup"><span data-stu-id="cecab-103">Replication is a good solution to the problem of moving data between continuously connected servers.</span></span> <span data-ttu-id="cecab-104">使用复制向导可以轻松地配置和管理复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="cecab-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="cecab-105">本教程演示如何为连续连接的服务器配置复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="cecab-105">This tutorial shows you how to configure a replication topology for continuously connected servers.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="cecab-106">学习内容</span><span class="sxs-lookup"><span data-stu-id="cecab-106">What You Will Learn</span></span>  
 <span data-ttu-id="cecab-107">本教程将演示如何使用事务复制将数据从一个数据库发布到另一个数据库。</span><span class="sxs-lookup"><span data-stu-id="cecab-107">This tutorial will show you how to publish data from one database to another using transactional replication.</span></span> <span data-ttu-id="cecab-108">第一课介绍如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建发布。</span><span class="sxs-lookup"><span data-stu-id="cecab-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="cecab-109">后面几课演示如何创建和验证订阅，以及如何测量滞后时间。</span><span class="sxs-lookup"><span data-stu-id="cecab-109">Later lessons show how to create and validate a subscription and how to measure latency.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecab-110">要求</span><span class="sxs-lookup"><span data-stu-id="cecab-110">Requirements</span></span>  
 <span data-ttu-id="cecab-111">本教程适用于熟悉数据库基本操作但复制经验不足的用户。</span><span class="sxs-lookup"><span data-stu-id="cecab-111">This tutorial is intended for users who are familiar with basic database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="cecab-112">本教程要求你完成上一个教程， [准备用于复制的服务器](tutorial-preparing-the-server-for-replication.md)的学习。</span><span class="sxs-lookup"><span data-stu-id="cecab-112">This tutorial requires that you have completed the previous tutorial, [Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="cecab-113">若要使用本教程，系统中必须安装有下列组件：</span><span class="sxs-lookup"><span data-stu-id="cecab-113">To use this tutorial, your system must have the following components:</span></span>  
  
-   <span data-ttu-id="cecab-114">发布服务器（源）：</span><span class="sxs-lookup"><span data-stu-id="cecab-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="cecab-115">任意版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，但 Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) 或 [!INCLUDE[ssEW](../../includes/ssew-md.md)]除外。</span><span class="sxs-lookup"><span data-stu-id="cecab-115">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="cecab-116">这些版本不能充当复制发布服务器。</span><span class="sxs-lookup"><span data-stu-id="cecab-116">These editions cannot be replication Publishers.</span></span>  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] <span data-ttu-id="cecab-117">示例数据库。</span><span class="sxs-lookup"><span data-stu-id="cecab-117">sample database.</span></span> <span data-ttu-id="cecab-118">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="cecab-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="cecab-119">订阅服务器（目标）：</span><span class="sxs-lookup"><span data-stu-id="cecab-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="cecab-120">任意版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，但 [!INCLUDE[ssEW](../../includes/ssew-md.md)]除外。</span><span class="sxs-lookup"><span data-stu-id="cecab-120">Any edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="cecab-121">不能充当事务复制中的订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="cecab-121">cannot be a Subscriber in transactional replication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cecab-122">默认情况下，不在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 上安装复制。</span><span class="sxs-lookup"><span data-stu-id="cecab-122">Replication is not installed on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cecab-123">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，你必须使用作为**sysadmin**固定服务器角色成员的登录名连接到发布服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="cecab-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="cecab-124">**本教程的估计完成时间：30分钟。**</span><span class="sxs-lookup"><span data-stu-id="cecab-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="cecab-125">本教程中的课程</span><span class="sxs-lookup"><span data-stu-id="cecab-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="cecab-126">第 1 课：使用事务复制发布数据</span><span class="sxs-lookup"><span data-stu-id="cecab-126">Lesson 1: Publishing Data Using Transactional Replication</span></span>](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [<span data-ttu-id="cecab-127">第 2 课：创建事务发布的订阅</span><span class="sxs-lookup"><span data-stu-id="cecab-127">Lesson 2: Creating a Subscription to the Transactional Publication</span></span>](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [<span data-ttu-id="cecab-128">第 3 课：验证订阅和测量滞后时间</span><span class="sxs-lookup"><span data-stu-id="cecab-128">Lesson 3: Validating the Subscription and Measuring Latency</span></span>](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [<span data-ttu-id="cecab-129">开始教程</span><span class="sxs-lookup"><span data-stu-id="cecab-129">Start the Tutorial</span></span>](transactional/transactional-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="cecab-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cecab-130">See Also</span></span>  
 [<span data-ttu-id="cecab-131">复制编程概念</span><span class="sxs-lookup"><span data-stu-id="cecab-131">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
