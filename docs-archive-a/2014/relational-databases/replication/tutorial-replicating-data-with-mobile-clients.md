---
title: 教程：使用移动客户端复制数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdf8be7cb0da11f0aa1022ba656d50c10826ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591226"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a><span data-ttu-id="828eb-102">教程：使用移动客户端复制数据</span><span class="sxs-lookup"><span data-stu-id="828eb-102">Tutorial: Replicating Data with Mobile Clients</span></span>
  <span data-ttu-id="828eb-103">复制是解决中央服务器和偶尔连接的移动客户端之间的数据移动问题的好方法。</span><span class="sxs-lookup"><span data-stu-id="828eb-103">Replication is a good solution to the problem of moving data between a central server and mobile clients that are only occasionally connected.</span></span> <span data-ttu-id="828eb-104">使用复制向导可以轻松地配置和管理复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="828eb-104">Using replication's wizards, you can easily configure and administer a replication topology.</span></span> <span data-ttu-id="828eb-105">本教程演示如何为移动客户端配置复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="828eb-105">This tutorial shows you how to configure a replication topology for mobile clients.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="828eb-106">学习内容</span><span class="sxs-lookup"><span data-stu-id="828eb-106">What You Will Learn</span></span>  
 <span data-ttu-id="828eb-107">在本教程中，您将使用合并复制将数据从中央数据库发布到一个或多个移动用户，以便每个用户都能获得唯一筛选的数据子集。</span><span class="sxs-lookup"><span data-stu-id="828eb-107">In this tutorial you will use merge replication to publish data from a central database to one or more mobile users so that each user gets a uniquely filtered subset of the data.</span></span> <span data-ttu-id="828eb-108">第一课介绍如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 创建发布。</span><span class="sxs-lookup"><span data-stu-id="828eb-108">The first lesson shows how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a publication.</span></span> <span data-ttu-id="828eb-109">后面几课演示如何创建和同步订阅。</span><span class="sxs-lookup"><span data-stu-id="828eb-109">Later lessons show how to create and synchronize a subscription.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="828eb-110">要求</span><span class="sxs-lookup"><span data-stu-id="828eb-110">Requirements</span></span>  
 <span data-ttu-id="828eb-111">本教程适用于熟悉数据库基本操作但复制经验不足的用户。</span><span class="sxs-lookup"><span data-stu-id="828eb-111">This tutorial is intended for users familiar with fundamental database operations, but who have limited experience with replication.</span></span> <span data-ttu-id="828eb-112">在开始本教程的学习之前，必须已完成 [教程：准备用于复制的服务器](tutorial-preparing-the-server-for-replication.md)的学习。</span><span class="sxs-lookup"><span data-stu-id="828eb-112">Before you start this tutorial, you must complete [Tutorial: Preparing the Server for Replication](tutorial-preparing-the-server-for-replication.md).</span></span>  
  
 <span data-ttu-id="828eb-113">若要使用本教程，系统中必须安装下列组件：</span><span class="sxs-lookup"><span data-stu-id="828eb-113">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   <span data-ttu-id="828eb-114">发布服务器（源）：</span><span class="sxs-lookup"><span data-stu-id="828eb-114">At the Publisher server (source):</span></span>  
  
    -   <span data-ttu-id="828eb-115">任意版本的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，但 Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) 或 [!INCLUDE[ssEW](../../includes/ssew-md.md)]除外。</span><span class="sxs-lookup"><span data-stu-id="828eb-115">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) or [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="828eb-116">这些版本不能充当复制发布服务器。</span><span class="sxs-lookup"><span data-stu-id="828eb-116">These editions cannot be a replication Publisher.</span></span>  
  
    -   <span data-ttu-id="828eb-117">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="828eb-117">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="828eb-118">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="828eb-118">To enhance security, the sample databases are not installed by default.</span></span>  
  
-   <span data-ttu-id="828eb-119">订阅服务器（目标）：</span><span class="sxs-lookup"><span data-stu-id="828eb-119">Subscriber server (destination):</span></span>  
  
    -   <span data-ttu-id="828eb-120">任意版本的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，但 [!INCLUDE[ssEW](../../includes/ssew-md.md)]除外。</span><span class="sxs-lookup"><span data-stu-id="828eb-120">Any edition of [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], except for [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> [!INCLUDE[ssEW](../../includes/ssew-md.md)] <span data-ttu-id="828eb-121">本教程中创建的发布不支持。</span><span class="sxs-lookup"><span data-stu-id="828eb-121">is not supported by the publication created in this tutorial.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="828eb-122">默认情况下，不在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]上安装复制。</span><span class="sxs-lookup"><span data-stu-id="828eb-122">Replication is not installed by default on [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="828eb-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，必须使用属于 sysadmin 固定服务器角色成员的登录名连接到发布服务器和订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="828eb-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you must connect to the Publisher and Subscriber using a login that is a member of the sysadmin fixed server role.</span></span>  
  
 <span data-ttu-id="828eb-124">**本教程的估计完成时间：30分钟。**</span><span class="sxs-lookup"><span data-stu-id="828eb-124">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="828eb-125">本教程中的课程</span><span class="sxs-lookup"><span data-stu-id="828eb-125">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="828eb-126">第 1 课：使用合并复制发布数据</span><span class="sxs-lookup"><span data-stu-id="828eb-126">Lesson 1: Publishing Data Using Merge Replication</span></span>](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [<span data-ttu-id="828eb-127">第 2 课：创建合并发布订阅</span><span class="sxs-lookup"><span data-stu-id="828eb-127">Lesson 2: Creating a Subscription to the Merge Publication</span></span>](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [<span data-ttu-id="828eb-128">开始教程</span><span class="sxs-lookup"><span data-stu-id="828eb-128">Start the Tutorial</span></span>](merge/merge-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="828eb-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="828eb-129">See Also</span></span>  
 [<span data-ttu-id="828eb-130">复制编程概念</span><span class="sxs-lookup"><span data-stu-id="828eb-130">Replication Programming Concepts</span></span>](concepts/replication-programming-concepts.md)  
  
  
