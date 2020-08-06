---
title: 修改资源运行状况策略定义（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.UTILITY.ADMINISTRATION.F1
ms.assetid: 27bec0b6-92e9-448e-8c70-fe36802cf128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d2651a2dd0b4994a6dacaad6c01d3f1ec68c98e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586664"
---
# <a name="modify-a-resource-health-policy-definition-sql-server-utility"></a><span data-ttu-id="437f6-102">修改资源运行状况策略定义（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="437f6-102">Modify a Resource Health Policy Definition (SQL Server Utility)</span></span>
  <span data-ttu-id="437f6-103">本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中修改资源使用情况策略定义。</span><span class="sxs-lookup"><span data-stu-id="437f6-103">This topic describes how to modify a resource health policy definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="437f6-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中修改资源使用情况策略之前，必须先创建一个实用工具控制点 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="437f6-104">Before you modify a resource utilization policy in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="437f6-105">有关详细信息，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="437f6-105">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="437f6-106">可以为数据层应用程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的托管实例配置实用工具资源使用情况策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-106">Utility resource utilization policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="437f6-107">可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中为所有数据层应用程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例全局定义资源使用情况策略；也可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中为每个数据层应用程序和每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 托管实例单独定义资源使用情况策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-107">Resource utilization policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="437f6-108">您还可以实现全局策略，并且用它们自己的策略定义配置单独的数据层应用程序或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例。</span><span class="sxs-lookup"><span data-stu-id="437f6-108">You can also implement global policies and have individual data-tier applications or managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configured with their own policy definitions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="437f6-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="437f6-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="modify-global-resource-utilization-policies-in-a-sql-server-utility"></a><span data-ttu-id="437f6-110">在 SQL Server 实用工具中修改全局资源使用情况策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-110">Modify global resource utilization policies in a SQL Server Utility.</span></span>  
  
1.  <span data-ttu-id="437f6-111">连接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 UCP。</span><span class="sxs-lookup"><span data-stu-id="437f6-111">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="437f6-112">在实用工具资源管理器导航窗格中，单击 **“实用工具管理”** 以便查看或修改全局监视策略，然后在实用工具资源管理器内容窗格中单击 **“策略”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="437f6-112">In the Utility Explorer navigation pane, click **Utility Administration** to view or modify global monitoring policies, then click the **Policy** tab in the Utility Explorer content pane.</span></span>  
  
3.  <span data-ttu-id="437f6-113">在实用工具资源管理器内容窗格中，通过单击箭头或策略说明，选择“设置全局数据层监视策略”或“设置全局托管的实例监视策略”。</span><span class="sxs-lookup"><span data-stu-id="437f6-113">In the Utility Explorer content pane, select **Set global data-tier monitoring policies** or **Set global managed instance monitoring policies** by clicking on the arrow or the policy description.</span></span>  
  
4.  <span data-ttu-id="437f6-114">使用策略说明右侧的控件可以设置使用过度或使用不足策略阈值。</span><span class="sxs-lookup"><span data-stu-id="437f6-114">Use the controls on the right side of the policy descriptions to set underutilization or overutilization policy thresholds.</span></span>  
  
5.  <span data-ttu-id="437f6-115">根据需要使用“应用” 、“放弃” 或“还原默认设置”  按钮。</span><span class="sxs-lookup"><span data-stu-id="437f6-115">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="437f6-116">策略更改可能需要最多 15 分钟的时间，以便传播回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具面板和列表视图详细信息。</span><span class="sxs-lookup"><span data-stu-id="437f6-116">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
6.  <span data-ttu-id="437f6-117">若要刷新数据，请在实用工具资源管理器导航窗格中右键单击“实用工具管理”节点，然后选择“刷新”。</span><span class="sxs-lookup"><span data-stu-id="437f6-117">To refresh data, right-click on the **Utility Administration** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
#### <a name="modify-resource-health-policy-definitions-for-an-individual-data-tier-application-or-an-individual-managed-instance-of-sql-server-in-a-sql-server-utility"></a><span data-ttu-id="437f6-118">在 SQL Server 实用工具中为单独的数据层应用程序或 SQL Server 的单独托管实例修改资源运行状况策略定义。</span><span class="sxs-lookup"><span data-stu-id="437f6-118">Modify resource health policy definitions for an individual data-tier application or an individual managed instance of SQL Server in a SQL Server Utility</span></span>  
  
1.  <span data-ttu-id="437f6-119">连接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 UCP。</span><span class="sxs-lookup"><span data-stu-id="437f6-119">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="437f6-120">在实用工具资源管理器导航窗格中，单击“已部署的数据层应用程序”或者单击“托管实例”，以便查看或修改用于单独数据层应用程序或托管实例的监视策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-120">In the Utility Explorer navigation pane, click **Deployed Date-tier Applications**, or click **Managed Instances**, to view or modify monitoring policies for an individual data-tier application or managed instance.</span></span>  
  
3.  <span data-ttu-id="437f6-121">在实用工具资源管理器内容窗格列表视图中，单击数据层应用程序或你要修改其策略的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例名称，然后单击“策略详细信息”选项卡。</span><span class="sxs-lookup"><span data-stu-id="437f6-121">In the Utility Explorer content pane list view, click the data-tier application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name whose policies you would like to modify, then click on the **Policy Details** tab.</span></span>  
  
4.  <span data-ttu-id="437f6-122">通过单击箭头或策略说明，选择要查看或修改的策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-122">Select the policy to view or modify by clicking on the arrow or the policy description.</span></span> <span data-ttu-id="437f6-123">默认情况下将选择全局策略。</span><span class="sxs-lookup"><span data-stu-id="437f6-123">Global policies are selected by default.</span></span>  
  
5.  <span data-ttu-id="437f6-124">选择单选按钮“覆盖全局策略”可覆盖全局策略，并为指定的数据层应用程序实现单独的策略定义。</span><span class="sxs-lookup"><span data-stu-id="437f6-124">Select the radio button to **Override the global policy** to override global policies and implement an individual policy definition for the specified data-tier application.</span></span>  
  
6.  <span data-ttu-id="437f6-125">使用策略说明右侧的控件可以设置使用过度或使用不足策略阈值。</span><span class="sxs-lookup"><span data-stu-id="437f6-125">Use the controls on the right side of the policy description to set underutilization or overutilization policy thresholds.</span></span>  
  
7.  <span data-ttu-id="437f6-126">根据需要使用“应用” 、“放弃” 或“还原默认设置”  按钮。</span><span class="sxs-lookup"><span data-stu-id="437f6-126">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="437f6-127">策略更改可能需要最多 15 分钟的时间，以便传播回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具面板和列表视图详细信息。</span><span class="sxs-lookup"><span data-stu-id="437f6-127">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
8.  <span data-ttu-id="437f6-128">若要刷新数据，请在实用工具资源管理器导航窗格中右键单击“已部署的数据层应用程序”节点，然后选择“刷新”。</span><span class="sxs-lookup"><span data-stu-id="437f6-128">To refresh data, right-click on the **Deployed Data-tier Applications** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437f6-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="437f6-129">See Also</span></span>  
 <span data-ttu-id="437f6-130">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="437f6-130">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="437f6-131">查看资源运行状况策略结果（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="437f6-131">View Resource Health Policy Results &#40;SQL Server Utility&#41;</span></span>](view-resource-health-policy-results-sql-server-utility.md)  
  
  
