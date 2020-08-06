---
title: 教程：准备用于复制的服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1f036ff2a111ee6b5f97655b9bebaf34391a436
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591230"
---
# <a name="tutorial-preparing-the-server-for-replication"></a><span data-ttu-id="8a712-102">教程：准备用于复制的服务器</span><span class="sxs-lookup"><span data-stu-id="8a712-102">Tutorial: Preparing the Server for Replication</span></span>
  <span data-ttu-id="8a712-103">在配置复制拓扑之前，制定安全计划是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="8a712-103">It is important to plan for security before you configure your replication topology.</span></span> <span data-ttu-id="8a712-104">本教程向您介绍如何更好地保护复制拓扑以及如何配置分发，这是复制数据的第一步。</span><span class="sxs-lookup"><span data-stu-id="8a712-104">This tutorial shows you how to better secure a replication topology as well as how to configure distribution, which is the first step in replicating data.</span></span> <span data-ttu-id="8a712-105">开始其他教程之前，必须先完成本教程。</span><span class="sxs-lookup"><span data-stu-id="8a712-105">You must complete this tutorial before any of the others.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a712-106">若要在服务器之间安全地复制数据，你应该实施 [复制安全最佳实践](security/replication-security-best-practices.md)中提出的所有建议。</span><span class="sxs-lookup"><span data-stu-id="8a712-106">To replicate data securely between servers, you should implement all of the recommendations in [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="8a712-107">学习内容</span><span class="sxs-lookup"><span data-stu-id="8a712-107">What You Will Learn</span></span>  
 <span data-ttu-id="8a712-108">在本教程中，您将了解如何准备服务器以便用最少的特权安全地运行复制。</span><span class="sxs-lookup"><span data-stu-id="8a712-108">In this tutorial you will learn how to prepare a server so that replication can run securely with least privileges.</span></span> <span data-ttu-id="8a712-109">第一课介绍如何创建用于运行复制代理的 Windows 服务帐户。</span><span class="sxs-lookup"><span data-stu-id="8a712-109">The first lesson shows how to create the Windows service accounts used to run replication agents.</span></span> <span data-ttu-id="8a712-110">第二课介绍如何配置用于生成和存储发布快照的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a712-110">The second lesson shows how to configure the folder used to generate and store publication snapshots.</span></span> <span data-ttu-id="8a712-111">第三课介绍如何配置分发以及如何设置权限。</span><span class="sxs-lookup"><span data-stu-id="8a712-111">The third lesson shows how to configure distribution and set permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a712-112">要求</span><span class="sxs-lookup"><span data-stu-id="8a712-112">Requirements</span></span>  
 <span data-ttu-id="8a712-113">本教程适用于熟悉基本数据库操作，但对复制认识有限的用户。</span><span class="sxs-lookup"><span data-stu-id="8a712-113">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to replication.</span></span>  
  
 <span data-ttu-id="8a712-114">若要使用本教程，系统中必须安装下列组件：</span><span class="sxs-lookup"><span data-stu-id="8a712-114">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] <span data-ttu-id="8a712-115">数据库的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a712-115">with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="8a712-116">为了增强安全性，默认情况下不会安装示例数据库。</span><span class="sxs-lookup"><span data-stu-id="8a712-116">To enhance security, the sample databases are not installed by default.</span></span>  
  
 <span data-ttu-id="8a712-117">**本教程的估计完成时间：30分钟。**</span><span class="sxs-lookup"><span data-stu-id="8a712-117">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="8a712-118">本教程中的课程</span><span class="sxs-lookup"><span data-stu-id="8a712-118">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="8a712-119">第 1 课：为复制创建 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="8a712-119">Lesson 1: Creating Windows Accounts for Replication</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [<span data-ttu-id="8a712-120">第 2 课：准备快照文件夹</span><span class="sxs-lookup"><span data-stu-id="8a712-120">Lesson 2: Preparing the Snapshot Folder</span></span>](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [<span data-ttu-id="8a712-121">第 3 课：配置分发</span><span class="sxs-lookup"><span data-stu-id="8a712-121">Lesson 3: Configuring Distribution</span></span>](lesson-3-configuring-distribution.md)  
  
 [<span data-ttu-id="8a712-122">开始教程</span><span class="sxs-lookup"><span data-stu-id="8a712-122">Start the Tutorial</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a712-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a712-123">See Also</span></span>  
 <span data-ttu-id="8a712-124">[“配置分发”](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="8a712-124">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="8a712-125">SQL Server 复制安全性</span><span class="sxs-lookup"><span data-stu-id="8a712-125">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
