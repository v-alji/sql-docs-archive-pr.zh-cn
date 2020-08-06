---
title: 取消报表服务器作业 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0ef8ada32aab4ac368871da711d0fe63fff7620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692249"
---
# <a name="cancel-report-server-jobs-management-studio"></a><span data-ttu-id="3111b-102">取消报表服务器作业 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3111b-102">Cancel Report Server Jobs (Management Studio)</span></span>
  <span data-ttu-id="3111b-103">使用“取消报表服务器作业”  对话框可以查看或取消正在执行的报表。</span><span class="sxs-lookup"><span data-stu-id="3111b-103">Use the **Cancel Report Server Jobs** dialog box to view or cancel in-progress reports.</span></span> <span data-ttu-id="3111b-104">此对话框显示报表服务器上当前运行的所有作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-104">This dialog box shows all jobs that are currently running on the report server.</span></span> <span data-ttu-id="3111b-105">尽管不能暂停或重新启动当前正在处理的作业，但是可以取消需要很长时间才能完成的所有作业或单个作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-105">Although you cannot pause or restart jobs that are currently processing, you can cancel all jobs or individual jobs if they are taking too long to complete.</span></span>  
  
 <span data-ttu-id="3111b-106">可以取消用户作业和系统作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-106">You can cancel user jobs and system jobs.</span></span>  
  
-   <span data-ttu-id="3111b-107">用户作业是由单个用户启动的任何作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-107">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="3111b-108">这包括按需运行报表、手动创建报表历史记录快照或手动创建报表执行快照。</span><span class="sxs-lookup"><span data-stu-id="3111b-108">This includes running a report on-demand, manually creating a report history snapshot, or manually creating report execution snapshot.</span></span> <span data-ttu-id="3111b-109">正在处理的标准订阅也是用户作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-109">An in-progress standard subscription is also a user job.</span></span>  
  
-   <span data-ttu-id="3111b-110">系统作业是指由报表服务器启动的作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-110">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="3111b-111">系统作业包括计划的报表处理。</span><span class="sxs-lookup"><span data-stu-id="3111b-111">System jobs include scheduled report processing.</span></span>  
  
 <span data-ttu-id="3111b-112">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器，右键单击“作业”，再单击“取消所有作业”   。</span><span class="sxs-lookup"><span data-stu-id="3111b-112">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click **Jobs**, and then click **Cancel All Jobs**.</span></span> <span data-ttu-id="3111b-113">还可以打开“作业”，右键单击报表服务器上正在运行的作业，然后选择“取消作业”   。</span><span class="sxs-lookup"><span data-stu-id="3111b-113">You can also open **Jobs**, right-click a job that is running on the report server, and select **Cancel Job(s)**.</span></span>  
  
 <span data-ttu-id="3111b-114">在取消作业之前，可以查看其属性来确定作业的开始时间。</span><span class="sxs-lookup"><span data-stu-id="3111b-114">Before cancelling a job, you can view its properties to determine when the job started.</span></span> <span data-ttu-id="3111b-115">有关详细信息，请参阅[作业属性 (Management Studio)](job-properties-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="3111b-115">For more information, see [Job Properties &#40;Management Studio&#41;](job-properties-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3111b-116">在具有高级服务的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="3111b-116">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="3111b-117">运行 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]时，将不会显示该页。</span><span class="sxs-lookup"><span data-stu-id="3111b-117">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="3111b-118">选项</span><span class="sxs-lookup"><span data-stu-id="3111b-118">Options</span></span>  
 <span data-ttu-id="3111b-119">**名称**</span><span class="sxs-lookup"><span data-stu-id="3111b-119">**Name**</span></span>  
 <span data-ttu-id="3111b-120">显示报表的名称。</span><span class="sxs-lookup"><span data-stu-id="3111b-120">Shows the name of the report.</span></span> <span data-ttu-id="3111b-121">订阅通过其各自的说明进行标识。</span><span class="sxs-lookup"><span data-stu-id="3111b-121">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="3111b-122">类型 </span><span class="sxs-lookup"><span data-stu-id="3111b-122">**Type**</span></span>  
 <span data-ttu-id="3111b-123">有效值为 **User** 和 **System**。</span><span class="sxs-lookup"><span data-stu-id="3111b-123">Valid values are **User** and **System**.</span></span>  
  
 <span data-ttu-id="3111b-124">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="3111b-124">**Start Time**</span></span>  
 <span data-ttu-id="3111b-125">显示作业的开始时间。</span><span class="sxs-lookup"><span data-stu-id="3111b-125">Shows when the job started.</span></span>  
  
 <span data-ttu-id="3111b-126">**用户名**</span><span class="sxs-lookup"><span data-stu-id="3111b-126">**User Name**</span></span>  
 <span data-ttu-id="3111b-127">对于由用户启动的作业，此列显示用户名。</span><span class="sxs-lookup"><span data-stu-id="3111b-127">For jobs that are initiated by a user, this column shows the name of the user.</span></span>  
  
 <span data-ttu-id="3111b-128">**Status**</span><span class="sxs-lookup"><span data-stu-id="3111b-128">**Status**</span></span>  
 <span data-ttu-id="3111b-129">显示作业的状态。</span><span class="sxs-lookup"><span data-stu-id="3111b-129">Shows the status of the job.</span></span> <span data-ttu-id="3111b-130">有效值为 **“新”** 和 **“正在运行”** 。</span><span class="sxs-lookup"><span data-stu-id="3111b-130">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="3111b-131">当作业开始时，状态始终为 **“新”** 。</span><span class="sxs-lookup"><span data-stu-id="3111b-131">Status is always **New** when the job begins.</span></span> <span data-ttu-id="3111b-132">在 60 秒之后，状态会改为 **“正在运行”** 。</span><span class="sxs-lookup"><span data-stu-id="3111b-132">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="3111b-133">必须刷新该页才能看到变化。</span><span class="sxs-lookup"><span data-stu-id="3111b-133">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="3111b-134">**确定**</span><span class="sxs-lookup"><span data-stu-id="3111b-134">**OK**</span></span>  
 <span data-ttu-id="3111b-135">取消一个或多个作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-135">Cancel a single job or multiple jobs.</span></span> <span data-ttu-id="3111b-136">作业会立即取消，并且不能恢复。</span><span class="sxs-lookup"><span data-stu-id="3111b-136">The jobs are cancelled immediately and cannot be resumed.</span></span> <span data-ttu-id="3111b-137">如果错误地取消了某个作业，则必须再次请求报表或订阅功能以启动新作业。</span><span class="sxs-lookup"><span data-stu-id="3111b-137">If you mistakenly cancel a job, you must request the report or subscription again to start a new job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3111b-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3111b-138">See Also</span></span>  
 <span data-ttu-id="3111b-139">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="3111b-139">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="3111b-140">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="3111b-140">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="3111b-141">管理运行中的进程</span><span class="sxs-lookup"><span data-stu-id="3111b-141">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
