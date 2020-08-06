---
title: 查看 Integration Services 服务的事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a513c8fc917da2987f3619c8eb9011e1170f7dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589753"
---
# <a name="view-events-for-the-integration-services-service"></a><span data-ttu-id="b6295-102">查看 Integration Services 服务的事件</span><span class="sxs-lookup"><span data-stu-id="b6295-102">View Events for the Integration Services Service</span></span>
  <span data-ttu-id="b6295-103">可以使用以下两个工具来查看 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的事件：</span><span class="sxs-lookup"><span data-stu-id="b6295-103">There are two tools in which you can view events for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service:</span></span>  
  
-   <span data-ttu-id="b6295-104">**中的** “日志文件查看器” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对话框。</span><span class="sxs-lookup"><span data-stu-id="b6295-104">The **Log File Viewer** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b6295-105">**“日志文件查看器”** 对话框包括导出、筛选和搜索日志的选项。</span><span class="sxs-lookup"><span data-stu-id="b6295-105">The **Log File Viewer** dialog box includes options to export, filter, and search the log.</span></span> <span data-ttu-id="b6295-106">有关“日志文件查看器”\*\*\*\* 中选项的详细信息，请参阅[日志文件查看器 F1 帮助](../relational-databases/logs/log-file-viewer-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="b6295-106">For more information about the options in the **Log File Viewer**, see [Log File Viewer F1 Help](../relational-databases/logs/log-file-viewer-f1-help.md).</span></span>  
  
-   <span data-ttu-id="b6295-107">Windows 事件查看器。</span><span class="sxs-lookup"><span data-stu-id="b6295-107">The Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="b6295-108">有关由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务记录的事件的说明，请参阅 [由 Integration Services 服务记录的事件](service/events-logged-by-the-integration-services-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b6295-108">For descriptions of the events logged by the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, see [Events Logged by the Integration Services Service](service/events-logged-by-the-integration-services-service.md).</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="b6295-109">在 SQL Server Management Studio 中查看 Integration Services 的服务事件</span><span class="sxs-lookup"><span data-stu-id="b6295-109">To view service events for Integration Services in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="b6295-110">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6295-110">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b6295-111">在 **“文件”** 菜单上，单击 **“连接对象资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="b6295-111">On the **File** menu, click **Connect Object Explorer**.</span></span>  
  
3.  <span data-ttu-id="b6295-112">在 **“连接到服务器”** 对话框中，选择 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器类型，选择或找到要连接到的服务器，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="b6295-112">In the **Connect to Server** dialog box, select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server type, select or locate the server to connect to, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="b6295-113">在对象资源管理器中，右键单击 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]，再单击“查看日志”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6295-113">In Object Explorer, right-click [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and click **View Logs**.</span></span>  
  
5.  <span data-ttu-id="b6295-114">若要查看 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 事件，请选择 **SQL Server Integration Services**。</span><span class="sxs-lookup"><span data-stu-id="b6295-114">To view [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] events, select **SQL Server Integration Services**.</span></span> <span data-ttu-id="b6295-115">如果选择或清除 **SQL Server Integration Services** 选项，则会同时选择或清除 **“NT 事件”** 选项。</span><span class="sxs-lookup"><span data-stu-id="b6295-115">The **NT Events** option is automatically selected and cleared with the **SQL Server Integration Services** option.</span></span>  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a><span data-ttu-id="b6295-116">在 Windows 事件查看器中查看 Integration Services 的服务事件</span><span class="sxs-lookup"><span data-stu-id="b6295-116">To view service events for Integration Services in Windows Event Viewer</span></span>  
  
1.  <span data-ttu-id="b6295-117">在 **“控制面板”** 中，如果使用的是经典视图，请单击 **“管理工具”**；如果使用的是分类视图，请单击 **“性能和维护”** ，再单击 **“管理工具”**。</span><span class="sxs-lookup"><span data-stu-id="b6295-117">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="b6295-118">单击 **“事件查看器”**。</span><span class="sxs-lookup"><span data-stu-id="b6295-118">Click **Event Viewer**.</span></span>  
  
3.  <span data-ttu-id="b6295-119">在 **“事件查看器”** 对话框中，单击 **“应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="b6295-119">In the **Event Viewer** dialog box, click **Application**.</span></span>  
  
4.  <span data-ttu-id="b6295-120">在“应用程序”\*\*\*\* 管理单元中，找到“源”\*\*\*\* 列中具有值 **SQLISService** 的项，右键单击该项，再单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6295-120">In the **Application** snap-in, locate an entry in the **Source** column that has the value **SQLISService**, right-click the entry, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b6295-121">可以选择单击向上键或向下键来显示上一个事件或下一个事件。</span><span class="sxs-lookup"><span data-stu-id="b6295-121">Optionally, click the up or down arrow to show the previous or next event.</span></span>  
  
6.  <span data-ttu-id="b6295-122">可以选择单击“复制到剪贴板”图标来复制事件信息。</span><span class="sxs-lookup"><span data-stu-id="b6295-122">Optionally, click the Copy to Clipboard icon to copy the event information.</span></span>  
  
7.  <span data-ttu-id="b6295-123">选择使用字节或字来显示事件数据。</span><span class="sxs-lookup"><span data-stu-id="b6295-123">Choose to display event data using bytes or words.</span></span>  
  
8.  <span data-ttu-id="b6295-124">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b6295-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b6295-125">在 **“文件”** 菜单上，单击 **“退出”** 关闭 **“事件查看器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b6295-125">On the **File** menu, click **Exit** to close the **Event Viewer** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6295-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6295-126">See Also</span></span>  
 <span data-ttu-id="b6295-127">[管理 Integration Services 服务](../../2014/integration-services/manage-the-integration-services-service.md) </span><span class="sxs-lookup"><span data-stu-id="b6295-127">[Manage the Integration Services Service](../../2014/integration-services/manage-the-integration-services-service.md) </span></span>  
 [<span data-ttu-id="b6295-128">添加数据流性能计数器的日志</span><span class="sxs-lookup"><span data-stu-id="b6295-128">Add a Log for Data Flow Performance Counters</span></span>](performance/performance-counters.md)  
  
  
