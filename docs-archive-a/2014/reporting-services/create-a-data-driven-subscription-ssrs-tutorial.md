---
title: 创建数据驱动订阅（SSRS 教程）| Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], tutorials
- walkthroughs [Reporting Services]
- data-driven subscriptions
ms.assetid: 79ab0572-43e9-4dc4-9b5a-cd8b627b8274
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53be7cf793d8fa38d177643c7f366115d4df8b7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691127"
---
# <a name="create-a-data-driven-subscription-ssrs-tutorial"></a><span data-ttu-id="02ee8-102">创建数据驱动订阅（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="02ee8-102">Create a Data-Driven Subscription (SSRS Tutorial)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="02ee8-103">提供数据驱动订阅功能，这样您便可根据动态订阅服务器数据自定义报表的分发。</span><span class="sxs-lookup"><span data-stu-id="02ee8-103">provides data-driven subscriptions so that you can customize the distribution of a report based on dynamic subscriber data.</span></span> <span data-ttu-id="02ee8-104">数据驱动订阅专门用于下列情况：</span><span class="sxs-lookup"><span data-stu-id="02ee8-104">Data-driven subscriptions are intended for the following kinds of scenarios:</span></span>  
  
-   <span data-ttu-id="02ee8-105">向大型收件人池分发报表，该池的成员身份可能随着分发的不同而有所变化。</span><span class="sxs-lookup"><span data-stu-id="02ee8-105">Distributing reports to a large recipient pool whose membership may change from one distribution to the next.</span></span> <span data-ttu-id="02ee8-106">例如，向当前的所有客户分发月报表。</span><span class="sxs-lookup"><span data-stu-id="02ee8-106">For example, distribute a monthly report to all current customers.</span></span>  
  
-   <span data-ttu-id="02ee8-107">根据预定义的条件向特定的收件人组分发报表。</span><span class="sxs-lookup"><span data-stu-id="02ee8-107">Distributing reports to a specific group of recipients based on predefined criteria.</span></span> <span data-ttu-id="02ee8-108">例如，向某个组织中的前十位销售经理分发销售业绩报表。</span><span class="sxs-lookup"><span data-stu-id="02ee8-108">For example, send a sales performance report to the top ten sales managers in an organization.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="02ee8-109">学习内容</span><span class="sxs-lookup"><span data-stu-id="02ee8-109">What You Will Learn</span></span>  
 <span data-ttu-id="02ee8-110">本教程通过简单的示例对概念进行解释，为您演示如何使用数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="02ee8-110">This tutorial shows you how to use data-driven subscriptions using a simple example to illustrate the concepts.</span></span>  
  
 <span data-ttu-id="02ee8-111">本教程分为三课：</span><span class="sxs-lookup"><span data-stu-id="02ee8-111">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="02ee8-112">第 1 课：创建示例订阅服务器数据库</span><span class="sxs-lookup"><span data-stu-id="02ee8-112">Lesson 1: Creating a Sample Subscriber Database</span></span>](lesson-1-creating-a-sample-subscriber-database.md)  
 <span data-ttu-id="02ee8-113">在这一课中，您将学习如何创建包含订阅服务器信息的本地 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="02ee8-113">In this lesson you will learn how to create a local [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains subscriber information.</span></span>  
  
 [<span data-ttu-id="02ee8-114">第 2 课：修改报表数据源属性</span><span class="sxs-lookup"><span data-stu-id="02ee8-114">Lesson 2: Modifying the Report Data Source Properties</span></span>](lesson-2-modifying-the-report-data-source-properties.md)  
 <span data-ttu-id="02ee8-115">在这一课中，您将学习如何修改报表数据源属性以便能够以无人参与的方式运行报表。</span><span class="sxs-lookup"><span data-stu-id="02ee8-115">In this lesson, you will learn how to modify report data source properties so that the report can run unattended.</span></span> <span data-ttu-id="02ee8-116">无人参与的处理要求存储凭据。</span><span class="sxs-lookup"><span data-stu-id="02ee8-116">Unattended processing requires stored credentials.</span></span> <span data-ttu-id="02ee8-117">您还将修改报表数据集以便包括订阅服务器数据提供的参数。</span><span class="sxs-lookup"><span data-stu-id="02ee8-117">You will also modify the report dataset to include a parameter that is supplied by the subscriber data.</span></span>  
  
 [<span data-ttu-id="02ee8-118">第 3 课：定义数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="02ee8-118">Lesson 3: Defining a Data-Driven Subscription</span></span>](lesson-3-defining-a-data-driven-subscription.md)  
 <span data-ttu-id="02ee8-119">在这一课中，您将学习如何定义数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="02ee8-119">In this lesson you will learn how to define a data-driven subscription.</span></span> <span data-ttu-id="02ee8-120">这一课引导您完成数据驱动订阅向导中的每一页。</span><span class="sxs-lookup"><span data-stu-id="02ee8-120">This lesson guides you through each page in the Data-Driven Subscription Wizard.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02ee8-121">要求</span><span class="sxs-lookup"><span data-stu-id="02ee8-121">Requirements</span></span>  
 <span data-ttu-id="02ee8-122">数据驱动订阅通常由报表服务器管理员创建和维护。</span><span class="sxs-lookup"><span data-stu-id="02ee8-122">Data-driven subscriptions are typically created and maintained by report server administrators.</span></span> <span data-ttu-id="02ee8-123">要创建数据驱动订阅，必须要具备生成查询的专业技术，了解包含订阅服务器数据的数据源，同时还要拥有对报表服务器的提升权限。</span><span class="sxs-lookup"><span data-stu-id="02ee8-123">The ability to create data-driven subscriptions requires expertise in building queries, knowledge of data sources that contain subscriber data, and elevated permissions on a report server.</span></span>  
  
 <span data-ttu-id="02ee8-124">本教程将使用教程[创建基本表报表中创建的报表 &#40;SSRS 教程&#41;](create-a-basic-table-report-ssrs-tutorial.md)和数据来自[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ee8-124">The tutorial will use the report created in the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md) and data from [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]</span></span>  
  
 <span data-ttu-id="02ee8-125">若要使用本教程，您的系统必须安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="02ee8-125">Your system must have the following installed to use this tutorial:</span></span>  
  
-   <span data-ttu-id="02ee8-126">支持数据驱动订阅的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="02ee8-126">An edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that supports data-driven subscriptions.</span></span> <span data-ttu-id="02ee8-127">有关详细信息，请参阅[SQL Server 2014 的版本和组件](../sql-server/editions-and-components-of-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="02ee8-127">For more information, see [Editions and Components of SQL Server 2014](../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
-   <span data-ttu-id="02ee8-128">必须在本机模式下运行报表服务器。</span><span class="sxs-lookup"><span data-stu-id="02ee8-128">The report server must be running in native mode.</span></span> <span data-ttu-id="02ee8-129">本教程中介绍的用户界面基于本机模式报表服务器。</span><span class="sxs-lookup"><span data-stu-id="02ee8-129">The user interface described in this tutorial is based on a native mode report server.</span></span> <span data-ttu-id="02ee8-130">在 SharePoint 模式报表服务器上支持订阅，但用户界面将不同于在本教程中介绍的用户界面。</span><span class="sxs-lookup"><span data-stu-id="02ee8-130">Subscriptions are supported on SharePoint mode report servers but the user interface will be different than what is described in this tutorial.</span></span>  
  
-   <span data-ttu-id="02ee8-131">必须运行 SQL Server 代理服务。</span><span class="sxs-lookup"><span data-stu-id="02ee8-131">SQL Server Agent service must be running.</span></span>  
  
-   <span data-ttu-id="02ee8-132">包含参数的报表。</span><span class="sxs-lookup"><span data-stu-id="02ee8-132">A report that includes parameters.</span></span> <span data-ttu-id="02ee8-133">本教程以使用教程 `Sales Orders` 创建基本表报表（SSRS 教程） [创建基本表报表（SSRS 教程）](create-a-basic-table-report-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="02ee8-133">This tutorial assumes the sample report, `Sales Orders` you create using the tutorial [Create a Basic Table Report &#40;SSRS Tutorial&#41;](create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
-   <span data-ttu-id="02ee8-134">向示例报表提供数据的 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="02ee8-134">The [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database, which provides data to the sample report.</span></span>  
  
-   <span data-ttu-id="02ee8-135">包括管理同一个示例报表中所有订阅任务的角色分配。</span><span class="sxs-lookup"><span data-stu-id="02ee8-135">A role assignment that includes the Manage all subscriptions task on the sample report.</span></span> <span data-ttu-id="02ee8-136">定义数据驱动订阅时需要执行该任务。</span><span class="sxs-lookup"><span data-stu-id="02ee8-136">This task is required for defining a data-driven subscription.</span></span> <span data-ttu-id="02ee8-137">如果您是计算机管理员，则本地管理员的默认角色分配将提供创建数据驱动订阅所必需的权限。</span><span class="sxs-lookup"><span data-stu-id="02ee8-137">If you are an administrator on the computer, the default role assignment for local administrators provides the permissions necessary for creating data-driven subscriptions.</span></span> <span data-ttu-id="02ee8-138">有关详细信息，请参阅 [授予对本机模式报表服务器的权限](security/granting-permissions-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="02ee8-138">For more information, see [Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md).</span></span>  
  
-   <span data-ttu-id="02ee8-139">您具有写入权限的共享文件夹。</span><span class="sxs-lookup"><span data-stu-id="02ee8-139">A shared folder for which you have write permissions.</span></span> <span data-ttu-id="02ee8-140">共享文件夹必须可以通过网络连接进行访问。</span><span class="sxs-lookup"><span data-stu-id="02ee8-140">The shared folder must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="02ee8-141">**学完本教程的估计时间：** 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="02ee8-141">**Estimated time to complete the tutorial:** 30 minutes.</span></span> <span data-ttu-id="02ee8-142">如果您还没有完成基本报表教程，则还需要 30 分钟。</span><span class="sxs-lookup"><span data-stu-id="02ee8-142">An additional 30 minutes if you have not completed the basic report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ee8-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02ee8-143">See Also</span></span>  
 <span data-ttu-id="02ee8-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="02ee8-144">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="02ee8-145">创建基本表报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="02ee8-145">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
