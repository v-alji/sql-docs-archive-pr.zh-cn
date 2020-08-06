---
title: 作业属性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4d309ba78a21114cf51c48f0a5c5b3b2f7c2500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689747"
---
# <a name="job-properties-management-studio"></a><span data-ttu-id="6b9aa-102">作业属性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6b9aa-102">Job Properties (Management Studio)</span></span>
  <span data-ttu-id="6b9aa-103">使用“作业属性”  页可以在取消正在执行的报表或订阅之前查看相关信息。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-103">Use the **Job Properties** page to view information about an in-progress report or subscription before you cancel it.</span></span>  
  
 <span data-ttu-id="6b9aa-104">若要打开此页，请启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，连接到报表服务器，然后打开 **“作业”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-104">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, and open the **Jobs** folder.</span></span> <span data-ttu-id="6b9aa-105">右键单击正在运行的作业，然后单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-105">Right-click a job that is running, and then click **Properties**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6b9aa-106">在具有高级服务的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中不支持此功能。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-106">This feature is not supported in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services.</span></span> <span data-ttu-id="6b9aa-107">运行 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]时，将不会显示该页。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-107">The page does not appear when you are running [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="6b9aa-108">任务</span><span class="sxs-lookup"><span data-stu-id="6b9aa-108">Tasks</span></span>  
 <span data-ttu-id="6b9aa-109">必须刷新该页以检索有关报表服务器上当前正在运行的作业的信息，才能查看有关作业的信息：</span><span class="sxs-lookup"><span data-stu-id="6b9aa-109">Before you can view information about a job, refresh the page to retrieve information about jobs that are currently running on the report server:</span></span>  
  
1.  <span data-ttu-id="6b9aa-110">打开报表服务器文件夹。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-110">Open the report server folder.</span></span>  
  
2.  <span data-ttu-id="6b9aa-111">右键单击“作业”，再单击“刷新”   。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-111">Right-click **Jobs**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="6b9aa-112">如果列出了某个作业，请右键单击它，再单击“属性”  。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-112">If a job is listed, right-click the job, and then click **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6b9aa-113">选项</span><span class="sxs-lookup"><span data-stu-id="6b9aa-113">Options</span></span>  
 <span data-ttu-id="6b9aa-114">**作业 ID**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-114">**Job ID**</span></span>  
 <span data-ttu-id="6b9aa-115">分配给正在处理的作业的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-115">A GUID that is assigned to a job while it is processing.</span></span> <span data-ttu-id="6b9aa-116">该值是在每次运行报表或订阅时随机生成的。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-116">The value is randomly generated each time a report or subscription runs.</span></span>  
  
 <span data-ttu-id="6b9aa-117">**作业状态**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-117">**Job Status**</span></span>  
 <span data-ttu-id="6b9aa-118">有效值为 **“新”** 和 **“正在运行”** 。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-118">Valid values are **New** and **Running**.</span></span> <span data-ttu-id="6b9aa-119">当作业开始时，状态始终为 **“新”** 。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-119">Status is always **New** when the job begins.</span></span> <span data-ttu-id="6b9aa-120">在 60 秒之后，状态会改为 **“正在运行”** 。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-120">After 60 seconds, status changes to **Running**.</span></span> <span data-ttu-id="6b9aa-121">必须刷新该页才能看到变化。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-121">You must refresh the page to pick up the change.</span></span>  
  
 <span data-ttu-id="6b9aa-122">**作业类型**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-122">**Job Type**</span></span>  
 <span data-ttu-id="6b9aa-123">有效值为 **User** 和 **System**。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-123">Valid values are **User** and **System**.</span></span> <span data-ttu-id="6b9aa-124">用户作业是由单个用户启动的任何作业。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-124">A user job is any job that is initiated by an individual user.</span></span> <span data-ttu-id="6b9aa-125">这包括按需运行报表、手动生成报表历史记录快照或手动创建报表执行快照。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-125">This includes running a report on-demand, manually generating a report history snapshot, or manually creating a report execution snapshot.</span></span> <span data-ttu-id="6b9aa-126">正在处理的标准订阅也是用户作业。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-126">An in-progress standard subscription is also a user job.</span></span> <span data-ttu-id="6b9aa-127">系统作业是指由报表服务器启动的作业。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-127">A system job is one that is initiated by the report server.</span></span> <span data-ttu-id="6b9aa-128">系统作业包括由计划触发的报表处理。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-128">System jobs include report processing that is triggered by a schedule.</span></span>  
  
 <span data-ttu-id="6b9aa-129">**作业操作**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-129">**Job Action**</span></span>  
 <span data-ttu-id="6b9aa-130">对于报表，此列显示正在处理哪些报表执行进程。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-130">For reports, this column shows which report execution processes are underway.</span></span> <span data-ttu-id="6b9aa-131">此值始终为 **“呈现”** 。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-131">This value is always **Render**.</span></span>  
  
 <span data-ttu-id="6b9aa-132">**作业说明**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-132">**Job Description**</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="6b9aa-133">默认情况下不提供作业说明。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-133">does not provide job descriptions by default.</span></span>  
  
 <span data-ttu-id="6b9aa-134">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-134">**Server Name**</span></span>  
 <span data-ttu-id="6b9aa-135">显示正在处理该作业的报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-135">Shows the name of the report server that is processing the job.</span></span> <span data-ttu-id="6b9aa-136">如果您配置了扩展部署，则此值将表明哪台服务器正在处理该作业。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-136">If you configured a scale-out deployment, this value will show which server is processing the job.</span></span>  
  
 <span data-ttu-id="6b9aa-137">**报表名称**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-137">**Report Name**</span></span>  
 <span data-ttu-id="6b9aa-138">显示报表的名称。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-138">Shows the name of the report.</span></span> <span data-ttu-id="6b9aa-139">订阅通过其各自的说明进行标识。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-139">Subscriptions are identified by their descriptions.</span></span>  
  
 <span data-ttu-id="6b9aa-140">**报表路径**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-140">**Report Path**</span></span>  
 <span data-ttu-id="6b9aa-141">显示报表在报表服务器文件夹层次结构中的路径。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-141">Shows the path of the report in the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="6b9aa-142">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-142">**Start Time**</span></span>  
 <span data-ttu-id="6b9aa-143">显示进程的开始时间。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-143">Shows when the process started.</span></span>  
  
 <span data-ttu-id="6b9aa-144">**用户名**</span><span class="sxs-lookup"><span data-stu-id="6b9aa-144">**User Name**</span></span>  
 <span data-ttu-id="6b9aa-145">对于由用户启动的进程，此列显示用户名。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-145">For processes initiated by a user, this column shows the name of the user.</span></span> <span data-ttu-id="6b9aa-146">对于系统作业，这是报表服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="6b9aa-146">For system jobs, this is the name of the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9aa-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b9aa-147">See Also</span></span>  
 <span data-ttu-id="6b9aa-148">[Management Studio 中报表服务器的 F1 帮助](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="6b9aa-148">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="6b9aa-149">[在 Management Studio 中连接到报表服务器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="6b9aa-149">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="6b9aa-150">管理运行中的进程</span><span class="sxs-lookup"><span data-stu-id="6b9aa-150">Manage a Running Process</span></span>](../subscriptions/manage-a-running-process.md)  
  
  
