---
title: 配置运行状况策略（SQL Server 实用工具）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c5ee466dd2d5bac2ea64364bfc78de8f2f5bea10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578886"
---
# <a name="configure-health-policies-sql-server-utility"></a><span data-ttu-id="af994-102">配置运行状况策略（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="af994-102">Configure Health Policies (SQL Server Utility)</span></span>
  <span data-ttu-id="af994-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 实用工具仪表板，可以查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例和数据层应用程序的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具资源参数。</span><span class="sxs-lookup"><span data-stu-id="af994-103">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="af994-104">有关详细信息，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="af994-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="af994-105">若要查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具运行状况策略结果，请从 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]连接到实用工具控制点。</span><span class="sxs-lookup"><span data-stu-id="af994-105">To view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility health policy results, connect to a utility control point from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="af994-106">有关详细信息，请参阅 [使用实用工具资源管理器来管理 SQL Server 实用工具](use-utility-explorer-to-manage-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="af994-106">For more information, see [Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af994-107">可为数据层应用程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的托管实例配置实用工具运行状况策略。</span><span class="sxs-lookup"><span data-stu-id="af994-107">Utility health policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af994-108">可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中为所有数据层应用程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例全局定义运行状况策略；或者，可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中为每个数据层应用程序和每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 托管实例单独定义运行状况策略。</span><span class="sxs-lookup"><span data-stu-id="af994-108">Health policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
## <a name="monitoring-policies-for-data-tier-applications"></a><span data-ttu-id="af994-109">针对数据层应用程序的监视策略</span><span class="sxs-lookup"><span data-stu-id="af994-109">Monitoring Policies for Data-tier Applications</span></span>  
 <span data-ttu-id="af994-110">针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据层应用程序的使用过度和使用不足策略如下：</span><span class="sxs-lookup"><span data-stu-id="af994-110">Overutilization and underutilization policies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data-tier applications are as follows:</span></span>  
  
-   <span data-ttu-id="af994-111">数据层应用程序处理器使用率。</span><span class="sxs-lookup"><span data-stu-id="af994-111">Data-tier application processor utilization.</span></span>  
  
-   <span data-ttu-id="af994-112">用于数据库文件的数据层应用程序文件空间。</span><span class="sxs-lookup"><span data-stu-id="af994-112">Data-tier application file space for database files.</span></span>  
  
-   <span data-ttu-id="af994-113">用于存储卷的数据层应用程序文件空间。</span><span class="sxs-lookup"><span data-stu-id="af994-113">Data-tier application file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="af994-114">计算机处理器使用率。</span><span class="sxs-lookup"><span data-stu-id="af994-114">Computer processor utilization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af994-115">对于数据层应用程序，存储卷和处理器使用率为只读策略。</span><span class="sxs-lookup"><span data-stu-id="af994-115">Storage volume and processor utilization are read-only policies for data-tier applications.</span></span>  
  
 <span data-ttu-id="af994-116">有关查看或更改数据层应用程序的全局监视策略的详细信息，请参阅[实用工具管理（SQL Server 实用工具）](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="af994-116">For more information about viewing or changing global monitoring policies for data-tier applications, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="af994-117">有关查看或更改单独数据层应用程序的监视策略的详细信息，请参阅[已部署的数据层应用程序详细信息（SQL Server 实用工具）](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="af994-117">For more information about viewing or changing monitoring policies for individual data-tier applications, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a><span data-ttu-id="af994-118">针对 SQL Server 的托管实例的监视策略</span><span class="sxs-lookup"><span data-stu-id="af994-118">Monitoring Policies for Managed Instances of SQL Server</span></span>  
 <span data-ttu-id="af994-119">针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例的使用过度和使用不足策略如下：</span><span class="sxs-lookup"><span data-stu-id="af994-119">Overutilization and underutilization policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are as follows:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af994-120">实例处理器使用率。</span><span class="sxs-lookup"><span data-stu-id="af994-120">instance processor utilization.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af994-121">实例文件空间。</span><span class="sxs-lookup"><span data-stu-id="af994-121">instance file space for database files.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="af994-122">实例文件空间。</span><span class="sxs-lookup"><span data-stu-id="af994-122">instance file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="af994-123">计算机处理器使用率。</span><span class="sxs-lookup"><span data-stu-id="af994-123">Computer processor utilization.</span></span>  
  
 <span data-ttu-id="af994-124">有关查看或更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例的全局监视策略的详细信息，请参阅[实用工具管理（SQL Server 实用工具](../../database-engine/utility-administration-sql-server-utility.md)）。</span><span class="sxs-lookup"><span data-stu-id="af994-124">For more information about viewing or changing global monitoring policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="af994-125">有关查看或更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的单独托管实例的全局监视策略的详细信息，请参阅[托管实例详细信息（SQL Server 实用工具）](../../database-engine/managed-instance-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="af994-125">For more information about viewing or changing monitoring policies for individual managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af994-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af994-126">See Also</span></span>  
 <span data-ttu-id="af994-127">[SQL Server 实用工具的功能和任务](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="af994-127">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="af994-128">减少 CPU 使用策略中的干扰（SQL Server 实用工具）</span><span class="sxs-lookup"><span data-stu-id="af994-128">Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;</span></span>](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
