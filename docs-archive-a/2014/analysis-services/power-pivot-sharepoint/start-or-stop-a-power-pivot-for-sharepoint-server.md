---
title: 启动或停止 PowerPivot for SharePoint 服务器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41c38f8f96fcbc9175cf0f52dafd8b28a83e5497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587010"
---
# <a name="start-or-stop-a-powerpivot-for-sharepoint-server"></a><span data-ttu-id="c363a-102">启动或停止 PowerPivot for SharePoint 服务器</span><span class="sxs-lookup"><span data-stu-id="c363a-102">Start or Stop a PowerPivot for SharePoint Server</span></span>
  <span data-ttu-id="c363a-103">PowerPivot 系统服务和 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 实例在同一台本地应用程序服务器上一起运行，以支持 SharePoint 场中的协调请求和数据处理。</span><span class="sxs-lookup"><span data-stu-id="c363a-103">PowerPivot System Service and an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance operate together on the same local application server to support coordinated request and data processing in a SharePoint farm.</span></span>  
  
 <span data-ttu-id="c363a-104">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="c363a-104">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="c363a-105">服务依赖关系</span><span class="sxs-lookup"><span data-stu-id="c363a-105">Service Dependencies</span></span>](#dependencies)  
  
 [<span data-ttu-id="c363a-106">启动或停止服务</span><span class="sxs-lookup"><span data-stu-id="c363a-106">Start or Stop the Services</span></span>](#startstop)  
  
 [<span data-ttu-id="c363a-107">停止 PowerPivot 服务器的影响</span><span class="sxs-lookup"><span data-stu-id="c363a-107">Effects of Stopping a PowerPivot Server</span></span>](#effects)  
  
##  <a name="service-dependencies"></a><a name="dependencies"></a><span data-ttu-id="c363a-108">服务依赖关系</span><span class="sxs-lookup"><span data-stu-id="c363a-108">Service Dependencies</span></span>  
 <span data-ttu-id="c363a-109">PowerPivot 系统服务依赖本地 Analysis Services 服务器实例，它们一起安装在同一物理服务器上。</span><span class="sxs-lookup"><span data-stu-id="c363a-109">The PowerPivot System Service has a dependency on the local Analysis Services server instance that is installed with it on the same physical server.</span></span> <span data-ttu-id="c363a-110">如果停止 PowerPivot 系统服务，也必须手动停止本地 Analysis Services 服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c363a-110">If you stop the PowerPivot System Service, you must also manually stop the local Analysis Services server instance.</span></span> <span data-ttu-id="c363a-111">如果一个服务正在运行而其他服务器实例未运行，则您将遇到针对 PowerPivot 数据处理的请求分配错误。</span><span class="sxs-lookup"><span data-stu-id="c363a-111">If one service is running without the other, you will encounter request allocation errors for PowerPivot data processing.</span></span>  
  
 <span data-ttu-id="c363a-112">只有在您诊断或解决问题时，Analysis Services 服务器才应单独运行。</span><span class="sxs-lookup"><span data-stu-id="c363a-112">The Analysis Services server should only be run by itself if you are diagnosing or troubleshooting a problem.</span></span> <span data-ttu-id="c363a-113">在所有其他情况下，该服务器都需要在同一服务器上本地运行的 PowerPivot 系统服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-113">In all other cases, the server requires the PowerPivot System Service that runs locally on the same server.</span></span>  
  
##  <a name="start-or-stop-the-services"></a><a name="startstop"></a><span data-ttu-id="c363a-114">启动或停止服务</span><span class="sxs-lookup"><span data-stu-id="c363a-114">Start or Stop the Services</span></span>  
 <span data-ttu-id="c363a-115">始终使用管理中心来启动或停止 PowerPivot 系统服务或 Analysis Services 服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c363a-115">Always use Central Administration to start or stop the PowerPivot System Service or Analysis Services server instance.</span></span> <span data-ttu-id="c363a-116">通过管理中心，您可以从同一页一起启动或停止服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-116">Central Administration allows you to start or stop the services together from the same page.</span></span> <span data-ttu-id="c363a-117">此外，管理中心使用称作 **“一个或多个服务已启动或停止”** 的计时器作业来重新启动它认为应运行的服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-117">In addition, Central Administration uses a timer job called **One or more services have started or stopped** to restart services that it thinks should be running.</span></span> <span data-ttu-id="c363a-118">如果您使用非 SharePoint 工具停止 PowerPivot 系统服务或 Analysis Services，则在该计时器作业运行时这些服务将重新启动。</span><span class="sxs-lookup"><span data-stu-id="c363a-118">If you stop the PowerPivot System Service or Analysis Services using a non-SharePoint tool, the services will be restarted when the timer job runs.</span></span>  
  
 <span data-ttu-id="c363a-119">启动和停止服务是一种应用于物理服务实例的操作。</span><span class="sxs-lookup"><span data-stu-id="c363a-119">Starting and stopping services is an action that applies to a physical service instance.</span></span> <span data-ttu-id="c363a-120">如果场中还有其他 PowerPivot for SharePoint 服务器，场中的其他服务器将继续接受对 PowerPivot 数据的请求。</span><span class="sxs-lookup"><span data-stu-id="c363a-120">If you have additional PowerPivot for SharePoint servers in the farm, the other servers within the farm will continue to accept requests for PowerPivot data.</span></span>  
  
 <span data-ttu-id="c363a-121">不能同时启动或停止场内的所有物理服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-121">You cannot start or stop all physical services simultaneously across the farm.</span></span> <span data-ttu-id="c363a-122">必须选择每个服务器，然后启动或停止特定服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-122">You must select each server and then start or stop a particular service.</span></span>  
  
 <span data-ttu-id="c363a-123">不能启动、暂停或停止特定 Web 应用程序的 PowerPivot 系统服务，但可以从默认连接列表中删除服务，使其不可用。</span><span class="sxs-lookup"><span data-stu-id="c363a-123">You cannot start, pause, or stop a PowerPivot System Service for a specific Web application, but you can remove a service from the default connection list to make it unavailable.</span></span> <span data-ttu-id="c363a-124">有关详细信息，请参阅[将 PowerPivot 服务应用程序连接到管理中心中的 SharePoint Web 应用程序](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="c363a-124">For more information, see [Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="c363a-125">在管理中心的 **“系统设置”** 中，单击 **“管理服务器上的服务”**。</span><span class="sxs-lookup"><span data-stu-id="c363a-125">In Central Administration, in **System Settings**, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="c363a-126">在本页顶部的“服务器”中，单击下箭头，然后单击 **“更改服务器”**。</span><span class="sxs-lookup"><span data-stu-id="c363a-126">At the top of the page, in Server, click the down arrow, and then click **Change Server**.</span></span>  
  
3.  <span data-ttu-id="c363a-127">选择具有您要启动或停止的 PowerPivot 系统服务或 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]实例的 SharePoint 服务器。</span><span class="sxs-lookup"><span data-stu-id="c363a-127">Select the SharePoint server that has the PowerPivot System Service or [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance that you want to start or stop.</span></span>  
  
4.  <span data-ttu-id="c363a-128">选择服务，然后单击该操作。</span><span class="sxs-lookup"><span data-stu-id="c363a-128">Select the service, and then click the action.</span></span> <span data-ttu-id="c363a-129">记住要成对启动或停止服务。</span><span class="sxs-lookup"><span data-stu-id="c363a-129">Remember to start or stop the services as a pair.</span></span> <span data-ttu-id="c363a-130">如果您启动或停止 PowerPivot 系统服务，请务必还要启动或停止在同一台计算机上运行的 Analysis Services 服务器实例。</span><span class="sxs-lookup"><span data-stu-id="c363a-130">If you start or stop the PowerPivot System Service, be sure to also start or stop the Analysis Services server instance that runs on the same computer.</span></span>  
  
##  <a name="effects-of-stopping-a-powerpivot-server"></a><a name="effects"></a><span data-ttu-id="c363a-131">停止 PowerPivot 服务器的影响</span><span class="sxs-lookup"><span data-stu-id="c363a-131">Effects of Stopping a PowerPivot Server</span></span>  
 <span data-ttu-id="c363a-132">下表介绍了在 SharePoint 服务器上停止 PowerPivot 系统服务和 Analysis Services 服务的影响。</span><span class="sxs-lookup"><span data-stu-id="c363a-132">The following table describes the effects of stopping the PowerPivot System Service and Analysis Services service on a SharePoint server.</span></span>  
  
|<span data-ttu-id="c363a-133">影响的对象</span><span class="sxs-lookup"><span data-stu-id="c363a-133">Effect on</span></span>|<span data-ttu-id="c363a-134">说明</span><span class="sxs-lookup"><span data-stu-id="c363a-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c363a-135">现有查询</span><span class="sxs-lookup"><span data-stu-id="c363a-135">Existing queries</span></span>|<span data-ttu-id="c363a-136">Analysis Services 服务器上正在进行中的查询将立即停止。</span><span class="sxs-lookup"><span data-stu-id="c363a-136">Queries that are in progress on an Analysis Services server will stop immediately.</span></span> <span data-ttu-id="c363a-137">用户将收到“找不到数据”或“找不到数据源连接”错误。</span><span class="sxs-lookup"><span data-stu-id="c363a-137">The user will get a data not found or data source connection not found error.</span></span>|  
|<span data-ttu-id="c363a-138">当前正在进行处理的现有数据刷新作业</span><span class="sxs-lookup"><span data-stu-id="c363a-138">Existing data refresh jobs that are currently processing</span></span>|<span data-ttu-id="c363a-139">当前 Analysis Services 服务器上正在进行中的作业将立即停止。</span><span class="sxs-lookup"><span data-stu-id="c363a-139">Jobs that are in progress on the current Analysis Services server will stop immediately.</span></span> <span data-ttu-id="c363a-140">数据刷新操作将失败，而且将在数据刷新历史记录中记录一个错误。</span><span class="sxs-lookup"><span data-stu-id="c363a-140">Data refresh will fail and an error will be logged to data refresh history.</span></span><br /><br /> <span data-ttu-id="c363a-141">在停止服务之前，您可以使用 SharePoint 管理中心的”检查作业状态“页查看当前作业的状态。</span><span class="sxs-lookup"><span data-stu-id="c363a-141">You can view the status of current jobs before you stop the service by using the Check job status page in SharePoint Central Administration.</span></span><br /><br /> <span data-ttu-id="c363a-142">尽管可以知道哪些作业当前正在处理，但没有办法通过查看队列本身来了解是否有其他作业将要启动。</span><span class="sxs-lookup"><span data-stu-id="c363a-142">While it is possible to know which jobs are currently processing, there is no way to view the queue itself to see whether other jobs are about to start.</span></span>|  
|<span data-ttu-id="c363a-143">队列中的现有数据刷新请求</span><span class="sxs-lookup"><span data-stu-id="c363a-143">Existing data refresh requests in the queue</span></span>|<span data-ttu-id="c363a-144">在计划的整个执行过程中，计划的数据刷新请求将一直保留在处理队列中（也就是说，计划的数据刷新请求将一直保持在队列中，直到下一次启动）。</span><span class="sxs-lookup"><span data-stu-id="c363a-144">Scheduled data refresh requests will remain in the processing queue for a complete cycle of the schedule (that is, it stays in the queue until the next start time).</span></span> <span data-ttu-id="c363a-145">如果到那时 PowerPivot 系统服务没有重新启动，数据刷新请求将被删除，并且将记录一个错误。</span><span class="sxs-lookup"><span data-stu-id="c363a-145">If the PowerPivot System Service is not restarted by then, the data refresh request will be dropped and an error will be logged.</span></span>|  
|<span data-ttu-id="c363a-146">新的查询或数据刷新请求</span><span class="sxs-lookup"><span data-stu-id="c363a-146">New requests for queries or data refresh</span></span>|<span data-ttu-id="c363a-147">如果您要停止场中的唯一一个 PowerPivot for SharePoint 服务器，新的 PowerPivot 数据请求将不被处理，而且数据请求将导致“找不到数据”错误。</span><span class="sxs-lookup"><span data-stu-id="c363a-147">If you are stopping the only PowerPivot for SharePoint server in the farm, new requests for PowerPivot data will not be handled and a request for data will result in a data not found error.</span></span><br /><br /> <span data-ttu-id="c363a-148">如果有其他 PowerPivot for SharePoint 服务器，请求将转到其中的一个可用服务器。</span><span class="sxs-lookup"><span data-stu-id="c363a-148">If you have additional PowerPivot for SharePoint servers, the request will go to one of the available servers.</span></span>|  
|<span data-ttu-id="c363a-149">使用情况数据</span><span class="sxs-lookup"><span data-stu-id="c363a-149">Usage data</span></span>|<span data-ttu-id="c363a-150">服务停止时将不会收集使用情况数据。</span><span class="sxs-lookup"><span data-stu-id="c363a-150">Usage data will not be collected while the services are stopped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c363a-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c363a-151">See Also</span></span>  
 [<span data-ttu-id="c363a-152">配置 PowerPivot 服务帐户</span><span class="sxs-lookup"><span data-stu-id="c363a-152">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
