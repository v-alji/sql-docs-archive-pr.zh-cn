---
title: 查看日志传送报告 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- viewing log shipping reports
- displaying log shipping reports
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], viewing reports
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d6c372a9b1f9af9e5948732e3bfb9384362f545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591527"
---
# <a name="view-the-log-shipping-report-sql-server-management-studio"></a><span data-ttu-id="d8ac3-102">查看日志传送报告 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d8ac3-102">View the Log Shipping Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d8ac3-103">本主题说明如何在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中查看事务日志传送状态报告。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-103">This topic explains how to view the Transaction Log Shipping Status report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d8ac3-104">您可以在监视服务器、主服务器或辅助服务器中运行状态报告。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-104">You can run a status report at a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="d8ac3-105">若要查看有关日志传送配置的最完整的信息，请在监视服务器实例上查看此报告。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-105">To see the  most complete information about your log shipping configuration, view the report at the monitor server instance.</span></span>  
  
 <span data-ttu-id="d8ac3-106">该报告显示所有其状态可从您连接到的服务器实例获得的日志传送活动的状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-106">The report displays the status of any log shipping activity whose status is available from the server instance to which you are connected.</span></span> <span data-ttu-id="d8ac3-107">如果该服务器实例涉及不同角色（例如，用作一个数据库的监视服务器，同时用作另一个数据库的辅助服务器）的多种配置，则显示的结果包含每个角色的各项配置信息。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-107">If that server instance is involved in multiple configurations in different roles (such as serving as a monitor for one database and a secondary for another database), the displayed results contain the information of every configuration from the perspective of each role.</span></span> <span data-ttu-id="d8ac3-108">如果存储过程能够针对给定的日志传送配置连接到监视服务器实例，则报告将显示此配置的其他状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-108">If the stored procedure can connect to the monitor server instance for a given log shipping configuration, the report displays additional status for that configuration.</span></span>  
  
 <span data-ttu-id="d8ac3-109">对于当前服务器实例执行的每个角色，您都可以查看以下信息：</span><span class="sxs-lookup"><span data-stu-id="d8ac3-109">For each role performed by the current server instance, you can view the following information:</span></span>  
  
|<span data-ttu-id="d8ac3-110">角色</span><span class="sxs-lookup"><span data-stu-id="d8ac3-110">Role</span></span>|<span data-ttu-id="d8ac3-111">显示的信息</span><span class="sxs-lookup"><span data-stu-id="d8ac3-111">Information displayed</span></span>|  
|----------|---------------------------|  
|<span data-ttu-id="d8ac3-112">监视</span><span class="sxs-lookup"><span data-stu-id="d8ac3-112">Monitor</span></span>|<span data-ttu-id="d8ac3-113">将此服务器实例用作其监视服务器的每台主服务器和辅助服务器的名称和状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-113">The name and status of every primary server and secondary server that uses this server instance as its monitor server.</span></span>|  
|<span data-ttu-id="d8ac3-114">主</span><span class="sxs-lookup"><span data-stu-id="d8ac3-114">Primary</span></span>|<span data-ttu-id="d8ac3-115">对于每个主数据库，当前服务器实例（作为主服务器）的状态和名称以及主数据库名称。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-115">For each primary database, the status and name of the current server instance (as the primary server), along with the primary database name.</span></span> <span data-ttu-id="d8ac3-116">报告将显示备份作业（存储在本地主服务器上）的状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-116">The report displays the status of the backup job (which is stored locally on the primary server).</span></span><br /><br /> <span data-ttu-id="d8ac3-117">报告还包含用于显示每台对应辅助服务器的行。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-117">The report also contains a row for each of the corresponding secondary servers.</span></span> <span data-ttu-id="d8ac3-118">如果配置使用监视服务器且存储过程可以连接到此监视服务器，这些行将显示最近日志备份的复制状态和还原状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-118">If the configuration uses a monitor server and the stored procedure can connect to the monitor, these rows display the copy status and restore status for the most recent log backup.</span></span>|  
|<span data-ttu-id="d8ac3-119">辅助副本</span><span class="sxs-lookup"><span data-stu-id="d8ac3-119">Secondary</span></span>|<span data-ttu-id="d8ac3-120">对于每个辅助数据库，当前服务器实例（作为辅助服务器）的状态和名称以及辅助数据库名称。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-120">For each secondary database, the status and name of the current server instance (as the secondary server), along with the secondary database name.</span></span><br /><br /> <span data-ttu-id="d8ac3-121">报告将显示辅助服务器上复制和还原作业的状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-121">The report displays the status of the copy and restore jobs at the secondary server.</span></span><br /><br /> <span data-ttu-id="d8ac3-122">报告还包含用于显示对应主服务器的行。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-122">The report also contains a row for the corresponding primary server.</span></span> <span data-ttu-id="d8ac3-123">如果配置使用监视服务器且存储过程可以连接到此监视服务器，此行将显示最近日志备份的状态。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-123">If the configuration uses a monitor server and the stored procedure can connect to the monitor, this row displays the status of the most recent log backup.</span></span>|  
  
 <span data-ttu-id="d8ac3-124">所显示的信息取决于服务器实例是监视服务器、主服务器还是辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-124">The information displayed depends on whether the server instance is a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="d8ac3-125">如果没有提供信息，则对应单元格显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-125">If information is not available, the corresponding cells are grayed out.</span></span>  
  
 <span data-ttu-id="d8ac3-126">此报告调用 **sp_help_log_shipping_monitor** 来获取数据。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-126">The report calls **sp_help_log_shipping_monitor** to get the data.</span></span> <span data-ttu-id="d8ac3-127">有关所需权限的信息，请参阅 [sp_help_log_shipping_monitor (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-127">For information about the required permissions, see [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql).</span></span>  
  
### <a name="to-display-the-transaction-log-shipping-status-report-on-a-server-instance"></a><span data-ttu-id="d8ac3-128">显示服务器实例上的事务日志传送状态报告</span><span class="sxs-lookup"><span data-stu-id="d8ac3-128">To display the Transaction Log Shipping Status report on a server instance</span></span>  
  
1.  <span data-ttu-id="d8ac3-129">连接到监视服务器、主服务器或辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-129">Connect to a monitor server, primary server, or secondary server.</span></span>  
  
2.  <span data-ttu-id="d8ac3-130">在对象资源管理器中，右键单击服务器实例，依次指向“报表”和“标准报表”。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-130">Right-click the server instance in Object Explorer, point to **Reports**, and point to **Standard Reports**.</span></span>  
  
3.  <span data-ttu-id="d8ac3-131">单击 **“事务日志传送状态”** 。</span><span class="sxs-lookup"><span data-stu-id="d8ac3-131">Click **Transaction Log Shipping Status**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ac3-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8ac3-132">See Also</span></span>  
 [<span data-ttu-id="d8ac3-133">监视日志传送 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d8ac3-133">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
  
