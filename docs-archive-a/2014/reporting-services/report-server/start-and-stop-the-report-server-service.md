---
title: 启动和停止报表服务器服务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- stopping Report Server service
- Report Server Windows service, starting
- Report Server service, starting
- starting Report Server service
ms.assetid: 6ec69ac3-27b0-472d-91e1-733af9078ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b751fd1a31830ffdc96cb296fa39d08e396c8c50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586327"
---
# <a name="start-and-stop-the-report-server-service"></a><span data-ttu-id="385d5-102">启动和停止报表服务器服务</span><span class="sxs-lookup"><span data-stu-id="385d5-102">Start and Stop the Report Server Service</span></span>
  <span data-ttu-id="385d5-103">报表服务器是作为包含报表服务器 Web 服务、报表管理器和后台处理应用程序的 Windows 服务来实现的。</span><span class="sxs-lookup"><span data-stu-id="385d5-103">A report server is implemented as a Windows service that contains the Report Server Web service, Report Manager, and a background processing application.</span></span> <span data-ttu-id="385d5-104">若要使用任何报表服务器功能，必须运行该服务。</span><span class="sxs-lookup"><span data-stu-id="385d5-104">The service must be running if you want to use any report server functionality.</span></span> <span data-ttu-id="385d5-105">停止该服务将停止所有报表服务器操作。</span><span class="sxs-lookup"><span data-stu-id="385d5-105">Stopping the service stops all report server operations.</span></span>  
  
 <span data-ttu-id="385d5-106">如果停止该服务，则对服务运行时应发生的计划报表和订阅处理的请求将添加到队列中。</span><span class="sxs-lookup"><span data-stu-id="385d5-106">While the service is stopped, requests for scheduled report and subscription processing that would have occurred had the service been running are added to the queue.</span></span> <span data-ttu-id="385d5-107">这是因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理运行的作业会创建该事件。</span><span class="sxs-lookup"><span data-stu-id="385d5-107">This is because jobs that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent create the events.</span></span> <span data-ttu-id="385d5-108">如果想要在关闭服务时避免积压操作，请注意要同时停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="385d5-108">If you want to avoid a backlog of operations while the service is off, consider stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent as well.</span></span>  
  
 <span data-ttu-id="385d5-109">可以使用多种工具来启动或停止报表服务器服务，包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器以及 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 中提供的服务工具。</span><span class="sxs-lookup"><span data-stu-id="385d5-109">You can use a variety of tools to start or stop the Report Server service, including the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, and the Services tool provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span>  
  
 <span data-ttu-id="385d5-110">如果要执行的操作不只是启动或停止服务（例如，更改服务帐户），则必须使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具。</span><span class="sxs-lookup"><span data-stu-id="385d5-110">If you are doing more than starting or stopping the service, such as changing the service account, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="385d5-111">如果使用其他工具更改服务帐户，可能会破坏 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="385d5-111">Using other tools to change the service account can break your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span> <span data-ttu-id="385d5-112">有关详细信息，请参阅 [配置报表服务器服务帐户（SSRS 配置管理器）](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="385d5-112">For more information, see [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="385d5-113">不能暂停和恢复服务。</span><span class="sxs-lookup"><span data-stu-id="385d5-113">You cannot pause and resume the service.</span></span> <span data-ttu-id="385d5-114">没有引导参数。</span><span class="sxs-lookup"><span data-stu-id="385d5-114">There are no start parameters.</span></span> <span data-ttu-id="385d5-115">虽然没有显式依赖关系，但若要在报表服务器上支持任何订阅或计划报表操作，则必须运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="385d5-115">Although there are no explicit dependencies, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be running if you support any subscriptions or scheduled report operations on the report server.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-the-reporting-services-configuration-tool"></a><span data-ttu-id="385d5-116">使用 Reporting Services 配置工具启动或停止服务</span><span class="sxs-lookup"><span data-stu-id="385d5-116">To start or stop the service using the Reporting Services Configuration tool</span></span>  
  
1.  <span data-ttu-id="385d5-117">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具并连接到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="385d5-117">Start [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server.</span></span>  
  
2.  <span data-ttu-id="385d5-118">在“报表服务器状态”页上，单击 **“停止”** 或 **“启动”**。</span><span class="sxs-lookup"><span data-stu-id="385d5-118">On the Report Server Status page, click **Stop** or **Start**.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-services-in-administrative-tools"></a><span data-ttu-id="385d5-119">使用管理工具中的服务启动或停止服务</span><span class="sxs-lookup"><span data-stu-id="385d5-119">To start or stop the service using Services in Administrative Tools</span></span>  
  
-   <span data-ttu-id="385d5-120">在“管理工具”中，打开“服务”，右键单击 **SQL Server Reporting Services (MSSQLSERVER)**，再单击 **“停止”** 或 **“重新启动”**。</span><span class="sxs-lookup"><span data-stu-id="385d5-120">In Administrative Tools, open Services, right-click **SQL Server Reporting Services (MSSQLSERVER)**, and click **Stop** or **Restart**.</span></span>  
  
 <span data-ttu-id="385d5-121">如果正在运行多个实例或报表服务器正在作为命名实例运行，请验证圆括号中的实例名称是否对应于您希望停止或重新启动的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="385d5-121">If you are running multiple instance or if the report server is running as a named instance, verify that the instance name in parentheses corresponds to the report server instance you want to stop or restart.</span></span>  
  
### <a name="to-start-or-stop-the-service-using-sql-server-configuration-manager"></a><span data-ttu-id="385d5-122">使用 SQL Server 配置管理器启动或停止服务。</span><span class="sxs-lookup"><span data-stu-id="385d5-122">To start or stop the service using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="385d5-123">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="385d5-123">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
2.  <span data-ttu-id="385d5-124">选择 SQL Server 服务，右键单击 **“SQL Server Reporting Services”**，再单击 **“停止”** 或 **“重新启动”**。</span><span class="sxs-lookup"><span data-stu-id="385d5-124">Select SQL Server Services, right-click **SQL Server Reporting Services**, and click **Stop** or **Restart**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385d5-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="385d5-125">See Also</span></span>  
 [<span data-ttu-id="385d5-126">Reporting Services Configuration Manager（本机模式）</span><span class="sxs-lookup"><span data-stu-id="385d5-126">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
