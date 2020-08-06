---
title: 查看资源运行状况策略结果（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4ab30ad0e87782f8187370a53747be4cf5d313d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689879"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a><span data-ttu-id="12e9c-102">查看资源运行状况策略结果（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="12e9c-102">View Resource Health Policy Results (SQL Server Utility)</span></span>
  <span data-ttu-id="12e9c-103">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的实用工具仪表板，可以查看 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的托管实例和数据层应用程序的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实用工具资源参数。</span><span class="sxs-lookup"><span data-stu-id="12e9c-103">Use the Utility dashboard in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="12e9c-104">有关详细信息，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="12e9c-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a><span data-ttu-id="12e9c-105">查看 SQL Server 实用工具的资源运行状况策略结果</span><span class="sxs-lookup"><span data-stu-id="12e9c-105">View SQL Server Utility resource health policy results.</span></span>  
  
1.  <span data-ttu-id="12e9c-106">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS) 中，单击“视图”，然后单击“实用工具资源管理器”以便查看实用工具资源管理器导航窗格。</span><span class="sxs-lookup"><span data-stu-id="12e9c-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS), click **View**, then click **Utility Explorer** to view the Utility Explorer navigation pane.</span></span> <span data-ttu-id="12e9c-107">若要查看内容窗格，请单击 **“视图”** ，然后单击 **“实用工具资源管理器内容”** 。</span><span class="sxs-lookup"><span data-stu-id="12e9c-107">To view the content pane, click **View**, then click **Utility Explorer Content**.</span></span>  
  
2.  <span data-ttu-id="12e9c-108">在导航窗格中，单击 ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")“连接到实用工具”。</span><span class="sxs-lookup"><span data-stu-id="12e9c-108">In the navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span> <span data-ttu-id="12e9c-109">如果尚未创建实用工具控制点 (UCP)，或者尚未将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例或者数据层应用程序注册到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实用工具中，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="12e9c-109">If you have not created a utility control point (UCP) or if you have not enrolled instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or data-tier applications into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
3.  <span data-ttu-id="12e9c-110">单击 UCP 节点可以查看 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的托管实例和数据层应用程序的摘要数据（右键单击可以刷新）。</span><span class="sxs-lookup"><span data-stu-id="12e9c-110">Click the UCP node to view summary data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="12e9c-111">面板数据将显示在内容窗格中。</span><span class="sxs-lookup"><span data-stu-id="12e9c-111">Dashboard data is displayed in the content pane.</span></span>  
  
4.  <span data-ttu-id="12e9c-112">单击“托管实例”节点可以查看 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的托管实例的列表视图数据（右键单击可以刷新）。</span><span class="sxs-lookup"><span data-stu-id="12e9c-112">Click the **Managed Instances** node to view list view data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (right-click to refresh).</span></span> <span data-ttu-id="12e9c-113">列表视图数据将显示在内容窗格中。</span><span class="sxs-lookup"><span data-stu-id="12e9c-113">List view data is displayed in the content pane.</span></span>  
  
5.  <span data-ttu-id="12e9c-114">单击“已部署的数据层应用程序”节点可查看数据层应用程序的列表视图（右键单击可刷新）。</span><span class="sxs-lookup"><span data-stu-id="12e9c-114">Click the **Deployed Data-tier Applications** node to view list view data for data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="12e9c-115">列表视图数据将显示在内容窗格中。</span><span class="sxs-lookup"><span data-stu-id="12e9c-115">List view data is displayed in the content pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e9c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12e9c-116">See Also</span></span>  
 <span data-ttu-id="12e9c-117">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="12e9c-117">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="12e9c-118">[减少 CPU 使用策略中的干扰（SQL Server 实用工具）](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="12e9c-118">[Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span></span>  
 <span data-ttu-id="12e9c-119">[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="12e9c-119">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="12e9c-120">[托管实例详细信息（SQL Server 实用工具）](../../database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="12e9c-120">[Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="12e9c-121">实用工具管理（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="12e9c-121">Utility Administration &#40;SQL Server Utility&#41;</span></span>](../../database-engine/utility-administration-sql-server-utility.md)  
  
  
