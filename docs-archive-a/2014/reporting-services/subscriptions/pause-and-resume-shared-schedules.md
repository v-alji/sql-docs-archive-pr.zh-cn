---
title: 暂停和恢复共享计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f525a15b07b79b5c0d37f9a88ed9483b351af326
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587161"
---
# <a name="pause-and-resume-shared-schedules"></a><span data-ttu-id="aba4b-102">暂停和恢复共享计划</span><span class="sxs-lookup"><span data-stu-id="aba4b-102">Pause and Resume Shared Schedules</span></span>
  <span data-ttu-id="aba4b-103">您可以暂停和恢复正在使用的共享计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-103">You can pause and resume a shared schedule that is in use.</span></span> <span data-ttu-id="aba4b-104">通过暂停共享计划，可以暂时冻结用于触发报表处理和订阅的计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-104">Pausing a shared schedule provides a way to temporarily freeze a schedule that is used to trigger report processing and subscriptions.</span></span> <span data-ttu-id="aba4b-105">您只能暂停和恢复共享计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-105">Only shared schedules can be paused and resumed.</span></span> <span data-ttu-id="aba4b-106">不能暂停报表特定计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-106">You cannot pause report-specific schedules.</span></span>  
  
 <span data-ttu-id="aba4b-107">您不能暂停和恢复正在进行的报表处理。</span><span class="sxs-lookup"><span data-stu-id="aba4b-107">You cannot pause and resume report processing that is in progress.</span></span> <span data-ttu-id="aba4b-108">您只能暂停和恢复处于 SQL Server 代理服务计划队列中的计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-108">You can only pause and resume schedules that are in the scheduling queue of SQL Server Agent service.</span></span> <span data-ttu-id="aba4b-109">正在进行的作业不在计划引擎的管理范围内。</span><span class="sxs-lookup"><span data-stu-id="aba4b-109">A job that is in progress is outside the scope of the scheduling engine.</span></span> <span data-ttu-id="aba4b-110">有关详细信息，请参阅 [管理运行中的进程](manage-a-running-process.md)</span><span class="sxs-lookup"><span data-stu-id="aba4b-110">For more information, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="aba4b-111">暂停共享计划时，可以取消将要发生的任何操作。</span><span class="sxs-lookup"><span data-stu-id="aba4b-111">While a shared schedule is paused, any operations that would have occurred are allowed to lapse.</span></span> <span data-ttu-id="aba4b-112">恢复共享计划后，报表和订阅处理将使用服务器的本地时间，在计划的下一次执行时间进行。</span><span class="sxs-lookup"><span data-stu-id="aba4b-112">After you resume a shared schedule, report and subscription processing occurs at the next scheduled time, using the local time of the server.</span></span> <span data-ttu-id="aba4b-113">假如未暂停计划，本机模式报表服务器或 SharePoint 服务应用程序不会虚构出一些本来将要发生的计划操作。</span><span class="sxs-lookup"><span data-stu-id="aba4b-113">The native mode report server or SharePoint service applications, do not make up scheduled operations that would have occurred had the schedule not been paused.</span></span>  
  
 <span data-ttu-id="aba4b-114">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="aba4b-114">In this Topic:</span></span>  
  
-   [<span data-ttu-id="aba4b-115">暂停和恢复共享计划（本机模式）</span><span class="sxs-lookup"><span data-stu-id="aba4b-115">Pause and Resume Shared Schedules (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="aba4b-116">暂停和恢复共享计划（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="aba4b-116">Pause and Resume Shared Schedules (SharePoint mode)</span></span>](#bkmk_sharepoint)  
  
##  <a name="pause-and-resume-shared-schedules-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="aba4b-117">暂停和恢复共享计划（本机模式）</span><span class="sxs-lookup"><span data-stu-id="aba4b-117">Pause and Resume Shared Schedules (Native Mode)</span></span>  
 <span data-ttu-id="aba4b-118">要暂停和恢复共享计划，请使用报表管理器中的“计划”页。</span><span class="sxs-lookup"><span data-stu-id="aba4b-118">To pause and resume a shared schedule, use the Schedules page in Report Manager.</span></span> <span data-ttu-id="aba4b-119">不能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]；它没有提供用于暂停和恢复计划的选项。</span><span class="sxs-lookup"><span data-stu-id="aba4b-119">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]; it does not provide options for pausing and resuming schedules.</span></span> <span data-ttu-id="aba4b-120">有关详细信息，请参阅 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="aba4b-120">For more information, see [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md).</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="aba4b-121">暂停或恢复共享计划</span><span class="sxs-lookup"><span data-stu-id="aba4b-121">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="aba4b-122">从报表管理器单击 **“站点设置”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-122">From Report Manager Click, **Site Settings**.</span></span>  
  
2.  <span data-ttu-id="aba4b-123">单击 **“计划”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-123">Click **Schedules**.</span></span>  
  
3.  <span data-ttu-id="aba4b-124">选择计划，在功能区中单击 **“暂停”** 或 **“恢复”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-124">Select the schedule, and click **Pause** or **Resume** in the ribbon.</span></span> <span data-ttu-id="aba4b-125">如果计划当前已暂停， **“状态”** 列将包含 **“已暂停”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-125">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
##  <a name="pause-and-resume-shared-schedules-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="aba4b-126">暂停和恢复共享计划（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="aba4b-126">Pause and Resume Shared Schedules (SharePoint mode)</span></span>  
 <span data-ttu-id="aba4b-127">要暂停和恢复共享计划，请使用“站点设置”页或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="aba4b-127">To pause and resume a shared schedule, use the Site Settings page or PowerShell.</span></span> <span data-ttu-id="aba4b-128">针对每个 SharePoint 站点管理计划。</span><span class="sxs-lookup"><span data-stu-id="aba4b-128">Schedules are managed per SharePoint site.</span></span>  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a><span data-ttu-id="aba4b-129">暂停或恢复共享计划</span><span class="sxs-lookup"><span data-stu-id="aba4b-129">To pause or resume a shared schedule</span></span>  
  
1.  <span data-ttu-id="aba4b-130">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-130">Click **Site Actions**.</span></span>  
  
2.  <span data-ttu-id="aba4b-131">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-131">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="aba4b-132">在 Reporting Services 部分中，单击 **“管理共享计划”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-132">In the Reporting Services section, click **Manage Shared Schedules**.</span></span>  
  
4.  <span data-ttu-id="aba4b-133">选择计划，并单击 **“暂停所选计划”** 或 **“运行所选计划”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-133">Select the schedule, and click **Pause Selected Schedules** or **Run Selected Schedules**.</span></span> <span data-ttu-id="aba4b-134">如果计划当前已暂停， **“状态”** 列将包含 **“已暂停”** 。</span><span class="sxs-lookup"><span data-stu-id="aba4b-134">If a Schedule is currently paused, the **Status** column will contain **Paused**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba4b-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aba4b-135">See Also</span></span>  
 <span data-ttu-id="aba4b-136">[“计划”](schedules.md) </span><span class="sxs-lookup"><span data-stu-id="aba4b-136">[Schedules](schedules.md) </span></span>  
 <span data-ttu-id="aba4b-137">[创建、修改和删除计划](create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="aba4b-137">[Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="aba4b-138">[更改报表服务器上的时区和时钟设置](change-time-zones-and-clock-settings-on-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="aba4b-138">[Change Time Zones and Clock Settings on a Report Server](change-time-zones-and-clock-settings-on-a-report-server.md) </span></span>  
 [<span data-ttu-id="aba4b-139">管理运行中的进程</span><span class="sxs-lookup"><span data-stu-id="aba4b-139">Manage a Running Process</span></span>](manage-a-running-process.md)  
  
  
