---
title: 更改报表服务器上的时区和时钟设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 566e421cd120010ea32f6936853e4319ec2efa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692657"
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a><span data-ttu-id="d20fe-102">更改报表服务器上的时区和时钟设置</span><span class="sxs-lookup"><span data-stu-id="d20fe-102">Change Time Zones and Clock Settings on a Report Server</span></span>
  <span data-ttu-id="d20fe-103">报表服务器始终使用其所在计算机的本地时间。</span><span class="sxs-lookup"><span data-stu-id="d20fe-103">A report server always uses the local time of the computer on which it is installed.</span></span> <span data-ttu-id="d20fe-104">您不能将它配置为使用其他时区。</span><span class="sxs-lookup"><span data-stu-id="d20fe-104">You cannot configure it to use a different time zone.</span></span> <span data-ttu-id="d20fe-105">如果客户端应用程序指向位于其他时区中的报表服务器，则将按该报表服务器所在时区的时间来执行计划操作。</span><span class="sxs-lookup"><span data-stu-id="d20fe-105">If a client application points to a report server in a different time zone, the report server time zone is used to execute a scheduled operation.</span></span> <span data-ttu-id="d20fe-106">在报表管理器和 SharePoint 管理页中，每个计划页上都标有时区，这样您可以确切知道执行计划操作的时间。</span><span class="sxs-lookup"><span data-stu-id="d20fe-106">In Report Manager and SharePoint management pages, the time zone is indicated on each scheduling page so that you know exactly when a scheduled operation will occur.</span></span> <span data-ttu-id="d20fe-107">例如，用于创建自定义计划的页将注明“时间用 (UTC-08:00) 太平洋时间（美国和加拿大）来表示”。</span><span class="sxs-lookup"><span data-stu-id="d20fe-107">For example, the page for creating custom schedules will note "Times are expressed in (UTC-08:00) Pacific time (US and Canada)."</span></span>  
  
## <a name="changing-the-time-zone-native-mode"></a><span data-ttu-id="d20fe-108">更改时区（本机模式）</span><span class="sxs-lookup"><span data-stu-id="d20fe-108">Changing the Time Zone (Native Mode)</span></span>  
 <span data-ttu-id="d20fe-109">如果更改承载报表服务器的计算机的时区，必须重新启动报表服务器服务才能使时区更改生效。</span><span class="sxs-lookup"><span data-stu-id="d20fe-109">If you change the time zone on a computer hosting a report server, you must restart the Report Server service in order for the time zone change to take effect.</span></span>  
  
 <span data-ttu-id="d20fe-110">现有报表历史记录快照的时间戳值将新的时区设置同步。</span><span class="sxs-lookup"><span data-stu-id="d20fe-110">Timestamp values of existing report history snapshots are synchronized to the new time zone setting.</span></span> <span data-ttu-id="d20fe-111">如果您在上午 9:00 生成了报表历史记录快照，然后向前调整一个时区，那么所生成快照的时间戳就会从上午 9:00 变为</span><span class="sxs-lookup"><span data-stu-id="d20fe-111">If you generated a report history snapshot at 9:00 A.M., and then reset the time zone ahead one time zone, the timestamp on the generated snapshot will change from 9:00 A.M.</span></span> <span data-ttu-id="d20fe-112">上午 10:00。</span><span class="sxs-lookup"><span data-stu-id="d20fe-112">to 10:00 A.M.</span></span>  
  
 <span data-ttu-id="d20fe-113">除非将计划映射到新的时区，否则这些计划将仍然保留现有设置。</span><span class="sxs-lookup"><span data-stu-id="d20fe-113">Schedules retain existing settings, except that they are mapped to the new time zone.</span></span> <span data-ttu-id="d20fe-114">例如，如果某个计划将在</span><span class="sxs-lookup"><span data-stu-id="d20fe-114">For example, if a schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="d20fe-115">太平洋标准时间的凌晨 2:00 运行，而您将时区更改为澳大利亚东部标准时间，则该计划将在澳大利亚东部</span><span class="sxs-lookup"><span data-stu-id="d20fe-115">Pacific Standard Time and you change the time zone to East Australia Standard Time, the schedule runs at 2:00 A.M.</span></span> <span data-ttu-id="d20fe-116">标准时间的凌晨 2:00 运行。</span><span class="sxs-lookup"><span data-stu-id="d20fe-116">East Australia Standard Time.</span></span>  
  
 <span data-ttu-id="d20fe-117">属性时间戳值（如创建文件夹或链接报表项的时间）与新的时区设置不同步。</span><span class="sxs-lookup"><span data-stu-id="d20fe-117">Property timestamp values (for example, the time at which a folder or linked report item is created) are not synchronized to a new time zone setting.</span></span> <span data-ttu-id="d20fe-118">如果您在 6 月 25 日上午 9:00 创建了一个项，然后重置了时区或时钟，则时间戳将仍然是 6 月 25 日上午 9:00。</span><span class="sxs-lookup"><span data-stu-id="d20fe-118">If you create an item on June 25 at 9:00 A.M., and then reset the time zone or clock, the timestamp remains June 25 at 9:00 A.M.</span></span>  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a><span data-ttu-id="d20fe-119">更改时区（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="d20fe-119">Changing the Time Zone (SharePoint Mode)</span></span>  
 <span data-ttu-id="d20fe-120">针对 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的时区配置作为 SharePoint 区域设置的一部分进行管理。</span><span class="sxs-lookup"><span data-stu-id="d20fe-120">The time zone configuration for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is managed as part of the SharePoint regional settings.</span></span> <span data-ttu-id="d20fe-121">有关详细信息，请参阅[区域设置 (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d20fe-121">For more information, see [Regional settings (SharePoint Server 2010 (https://technet.microsoft.com/library/cc824907.aspx)](https://technet.microsoft.com/library/cc824907.aspx).</span></span>  
  
## <a name="changing-the-clock-settings"></a><span data-ttu-id="d20fe-122">更改时钟设置</span><span class="sxs-lookup"><span data-stu-id="d20fe-122">Changing the Clock Settings</span></span>  
 <span data-ttu-id="d20fe-123">更改计算机时钟对现有时间戳值没有影响（例如，如果您将时钟拨快一小时，报表历史记录快照的时间戳不会改变）。</span><span class="sxs-lookup"><span data-stu-id="d20fe-123">Changing the computer clock has no effect on existing timestamp values (for example, if you move the clock forward an hour, the timestamps of report history snapshots do not change).</span></span> <span data-ttu-id="d20fe-124">计划和传递处理器可能需要 10 秒钟的延迟才会使用新的设置。</span><span class="sxs-lookup"><span data-stu-id="d20fe-124">There may be a delay of 10 seconds before the Scheduling and Delivery Processor uses the new setting.</span></span> <span data-ttu-id="d20fe-125">如果您修改了配置文件中的轮询间隔设置，实际延迟时间可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="d20fe-125">The actual delay may vary if you modified polling interval settings in the configuration files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20fe-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d20fe-126">See Also</span></span>  
 <span data-ttu-id="d20fe-127">[启动和停止报表服务器服务](../report-server/start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="d20fe-127">[Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md) </span></span>  
 [<span data-ttu-id="d20fe-128">计划</span><span class="sxs-lookup"><span data-stu-id="d20fe-128">Schedules</span></span>](schedules.md)  
  
  
