---
title: "\"计划\" 页 (报表管理器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ef19d96e-9f00-4434-950e-152dda9c1ced
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02e31bc25473aad23ecd2654f74ee3e837e65b65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580573"
---
# <a name="schedules-page-report-manager"></a><span data-ttu-id="4198c-102">“计划”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="4198c-102">Schedules Page (Report Manager)</span></span>
  <span data-ttu-id="4198c-103">使用“计划”页可以创建、修改、删除、暂停或恢复共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-103">Use the Schedules page to create, modify, delete, pause, or resume shared schedules.</span></span> <span data-ttu-id="4198c-104">共享计划是一个指定计划。您可以独立于报表、订阅以及其他需要计划信息的进程来创建和管理共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-104">A shared schedule is a named schedule that you can create and manage separately from reports, subscriptions, and other processes that consume schedule information.</span></span> <span data-ttu-id="4198c-105">用户可以选择您提供的共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-105">Users can select shared schedules that you provide.</span></span>  
  
 <span data-ttu-id="4198c-106">要删除、暂停或恢复共享计划，请选中您要修改的共享计划旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="4198c-106">To delete, pause, or resume a shared schedule, select the check box next to the shared schedule that you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4198c-107">并非在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的每个版本中均提供此功能。</span><span class="sxs-lookup"><span data-stu-id="4198c-107">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4198c-108">有关各个版本支持的功能列表 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2014 的各个[版本支持的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="4198c-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="4198c-109">导航</span><span class="sxs-lookup"><span data-stu-id="4198c-109">Navigation</span></span>  
 <span data-ttu-id="4198c-110">使用以下过程导航到用户界面 (UI) 中的这一位置。</span><span class="sxs-lookup"><span data-stu-id="4198c-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-schedules-page"></a><span data-ttu-id="4198c-111">打开“计划”页</span><span class="sxs-lookup"><span data-stu-id="4198c-111">To open the Schedules page</span></span>  
  
1.  <span data-ttu-id="4198c-112">打开报表管理器。</span><span class="sxs-lookup"><span data-stu-id="4198c-112">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="4198c-113">在页面顶部的右角，单击 **“站点设置”**。</span><span class="sxs-lookup"><span data-stu-id="4198c-113">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="4198c-114">这会打开该站点的“常规属性”页。</span><span class="sxs-lookup"><span data-stu-id="4198c-114">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="4198c-115">选择 **“计划”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4198c-115">Select the **Schedules** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4198c-116">选项</span><span class="sxs-lookup"><span data-stu-id="4198c-116">Options</span></span>  
 <span data-ttu-id="4198c-117">**新建计划**</span><span class="sxs-lookup"><span data-stu-id="4198c-117">**New Schedule**</span></span>  
 <span data-ttu-id="4198c-118">单击此选项可打开用于指定频率信息的“计划”页。</span><span class="sxs-lookup"><span data-stu-id="4198c-118">Click to open the Scheduling page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="4198c-119">**删除**</span><span class="sxs-lookup"><span data-stu-id="4198c-119">**Delete**</span></span>  
 <span data-ttu-id="4198c-120">单击此选项可删除共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-120">Click to remove a shared schedule.</span></span>  
  
 <span data-ttu-id="4198c-121">**暂停**</span><span class="sxs-lookup"><span data-stu-id="4198c-121">**Pause**</span></span>  
 <span data-ttu-id="4198c-122">单击此选项可暂时停止运行共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-122">Click to stop a shared schedule from running temporarily.</span></span> <span data-ttu-id="4198c-123">暂停计划将导致订阅和其他计划进程停止运行。</span><span class="sxs-lookup"><span data-stu-id="4198c-123">Pausing a schedule prevents subscriptions and other scheduled processes from running.</span></span>  
  
 <span data-ttu-id="4198c-124">**恢复**</span><span class="sxs-lookup"><span data-stu-id="4198c-124">**Resume**</span></span>  
 <span data-ttu-id="4198c-125">单击此选项可恢复已暂停的共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-125">Click to reinstate a shared schedule.</span></span> <span data-ttu-id="4198c-126">在暂停计划期间计划运行的进程将会失效，且不可恢复。</span><span class="sxs-lookup"><span data-stu-id="4198c-126">Lapsed processes that were scheduled to run while the schedule was paused are not made up.</span></span>  
  
 <span data-ttu-id="4198c-127">**计划**</span><span class="sxs-lookup"><span data-stu-id="4198c-127">**Schedule**</span></span>  
 <span data-ttu-id="4198c-128">显示当前定义的共享计划。</span><span class="sxs-lookup"><span data-stu-id="4198c-128">Shows the shared schedules that are currently defined.</span></span> <span data-ttu-id="4198c-129">单击共享计划可以查看或编辑其频率信息。</span><span class="sxs-lookup"><span data-stu-id="4198c-129">Click a shared schedule to view or edit frequency information.</span></span>  
  
 <span data-ttu-id="4198c-130">**创建者**</span><span class="sxs-lookup"><span data-stu-id="4198c-130">**Creator**</span></span>  
 <span data-ttu-id="4198c-131">显示创建共享计划的用户名。</span><span class="sxs-lookup"><span data-stu-id="4198c-131">Shows the name of the user who created the shared schedule.</span></span>  
  
 <span data-ttu-id="4198c-132">**上次运行时间和下次运行时间**</span><span class="sxs-lookup"><span data-stu-id="4198c-132">**Last Run, Next Run**</span></span>  
 <span data-ttu-id="4198c-133">显示共享计划的上次运行时间和下次运行时间。</span><span class="sxs-lookup"><span data-stu-id="4198c-133">Shows when the shared schedule was last run and when it will run next.</span></span>  
  
 <span data-ttu-id="4198c-134">**Status**</span><span class="sxs-lookup"><span data-stu-id="4198c-134">**Status**</span></span>  
 <span data-ttu-id="4198c-135">显示共享计划的状态是已暂停还是活动。</span><span class="sxs-lookup"><span data-stu-id="4198c-135">Shows whether a shared schedule is paused or active.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4198c-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4198c-136">See Also</span></span>  
 <span data-ttu-id="4198c-137">[创建、修改和删除计划](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="4198c-137">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="4198c-138">报表管理器的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="4198c-138">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
