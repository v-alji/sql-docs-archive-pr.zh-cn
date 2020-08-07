---
title: 使用性能对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7c1fe3f4a7d9a5fec901f84d8e913e49a4dbd1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588229"
---
# <a name="use-performance-objects"></a><span data-ttu-id="e9d5a-102">使用性能对象</span><span class="sxs-lookup"><span data-stu-id="e9d5a-102">Use Performance Objects</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9d5a-103">代理包括用于监视服务执行情况的性能对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-103">Agent includes performance objects and counters to monitor how the service is performing.</span></span> <span data-ttu-id="e9d5a-104">这些性能对象使您可以使用性能监视器（一个 Windows 工具）来识别 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务在后台的运行情况。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-104">These performance objects allow you to use Performance Monitor, a Windows tool, to identify what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is doing in the background.</span></span> <span data-ttu-id="e9d5a-105">例如，您可以通过识别 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务当前运行的活动作业数量来找出那些锁定的作业。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-105">For example, you can identify how many active jobs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is currently running to identify those jobs that are blocked.</span></span>  
  
 <span data-ttu-id="e9d5a-106">计算机上安装的每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都拥有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务性能对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects and counters exist for each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is installed on a computer.</span></span> <span data-ttu-id="e9d5a-107">性能对象是根据每个对象所代表的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例来命名的。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-107">Performance objects are named according to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that each object represents.</span></span>  
  
 <span data-ttu-id="e9d5a-108">下表显示了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务性能对象的命名方式：</span><span class="sxs-lookup"><span data-stu-id="e9d5a-108">The following table shows how the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects are named:</span></span>  
  
|<span data-ttu-id="e9d5a-109">实例类型</span><span class="sxs-lookup"><span data-stu-id="e9d5a-109">Instance type</span></span>|<span data-ttu-id="e9d5a-110">对象名称</span><span class="sxs-lookup"><span data-stu-id="e9d5a-110">Object name</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="e9d5a-111">默认值</span><span class="sxs-lookup"><span data-stu-id="e9d5a-111">Default</span></span>|<span data-ttu-id="e9d5a-112">**SQLAgent：对象** **：计数器**</span><span class="sxs-lookup"><span data-stu-id="e9d5a-112">**SQLAgent:** *object*:*counter*</span></span>|  
|<span data-ttu-id="e9d5a-113">名为</span><span class="sxs-lookup"><span data-stu-id="e9d5a-113">Named</span></span>|<span data-ttu-id="e9d5a-114">**SQLAgent$**</span><span class="sxs-lookup"><span data-stu-id="e9d5a-114">**SQLAgent$**</span></span><br /> <span data-ttu-id="e9d5a-115">***instance_name* ：** *对象*：*计数器*</span><span class="sxs-lookup"><span data-stu-id="e9d5a-115">***instance_name* :** *object*:*counter*</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e9d5a-116">包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的下列性能对象。</span><span class="sxs-lookup"><span data-stu-id="e9d5a-116">includes the following performance objects for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
|<span data-ttu-id="e9d5a-117">对象名称</span><span class="sxs-lookup"><span data-stu-id="e9d5a-117">Object name</span></span>|<span data-ttu-id="e9d5a-118">说明</span><span class="sxs-lookup"><span data-stu-id="e9d5a-118">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="e9d5a-119">SQLAgent:Jobs</span><span class="sxs-lookup"><span data-stu-id="e9d5a-119">SQLAgent:Jobs</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|<span data-ttu-id="e9d5a-120">已启动作业的相关性能信息、成功率和当前状态</span><span class="sxs-lookup"><span data-stu-id="e9d5a-120">Performance information about jobs that have been started, success rates, and current status</span></span>|  
|[<span data-ttu-id="e9d5a-121">SQLAgent:JobSteps</span><span class="sxs-lookup"><span data-stu-id="e9d5a-121">SQLAgent:JobSteps</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|<span data-ttu-id="e9d5a-122">作业步骤的相关状态信息</span><span class="sxs-lookup"><span data-stu-id="e9d5a-122">Status information about job steps</span></span>|  
|[<span data-ttu-id="e9d5a-123">SQLAgent:Alerts</span><span class="sxs-lookup"><span data-stu-id="e9d5a-123">SQLAgent:Alerts</span></span>](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|<span data-ttu-id="e9d5a-124">警报和通知数的相关信息</span><span class="sxs-lookup"><span data-stu-id="e9d5a-124">Information about number of alerts and notifications</span></span>|  
|[<span data-ttu-id="e9d5a-125">SQLAgent:Statistics</span><span class="sxs-lookup"><span data-stu-id="e9d5a-125">SQLAgent:Statistics</span></span>](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|<span data-ttu-id="e9d5a-126">常规性能信息</span><span class="sxs-lookup"><span data-stu-id="e9d5a-126">General performance information</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9d5a-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9d5a-127">See Also</span></span>  
 <span data-ttu-id="e9d5a-128">[监视和优化性能](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span><span class="sxs-lookup"><span data-stu-id="e9d5a-128">[Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span></span>  
 [<span data-ttu-id="e9d5a-129">启动系统监视器 (Windows)</span><span class="sxs-lookup"><span data-stu-id="e9d5a-129">Start System Monitor &#40;Windows&#41;</span></span>](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
