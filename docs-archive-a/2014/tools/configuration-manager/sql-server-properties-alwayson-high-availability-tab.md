---
title: " (AlwaysOn 高可用性选项卡) SQL Server 属性 |Microsoft Docs"
description: 了解如何在 SQL Server 2014 中打开或关闭 AlwaysOn 可用性组功能。 查看服务器实例必须满足此功能的先决条件。
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 3939b40a334746e9ee96441338e2e50791987103
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690987"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a><span data-ttu-id="b184f-104">SQL Server 属性（“AlwaysOn 高可用性”选项卡）</span><span class="sxs-lookup"><span data-stu-id="b184f-104">SQL Server Properties (AlwaysOn High Availability Tab)</span></span>
  <span data-ttu-id="b184f-105">使用 \*\*\*\* 配置管理器的 **“SQL Server 属性”** 对话框中的“AlwaysOn 高可用性” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 选项卡，可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中启用或禁用“AlwaysOn 可用性组”功能。</span><span class="sxs-lookup"><span data-stu-id="b184f-105">Use the **AlwaysOn High Availability** tab of the **SQL Server Properties** dialog box in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to enable or disable the AlwaysOn Availability Groups feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b184f-106">启用 AlwaysOn 可用性组是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将可用性组用作高可用性和灾难恢复解决方案的一个先决条件。</span><span class="sxs-lookup"><span data-stu-id="b184f-106">Enabling AlwaysOn Availability Groups is a prerequisite for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use availability groups as a high availability and disaster recovery solution.</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="b184f-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="b184f-107">Prerequisites</span></span>  
 <span data-ttu-id="b184f-108">若要启用 AlwaysOn 可用性组，服务器实例必须满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="b184f-108">To be enabled for AlwaysOn Availability Groups, a server instance must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="b184f-109">该服务器实例必须驻留在 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="b184f-109">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="b184f-110">若要位于同一个可用性组中，实例必须位于同一个 WSFC 群集中。</span><span class="sxs-lookup"><span data-stu-id="b184f-110">To be in the same availability group, instances must be in the same WSFC cluster.</span></span> <span data-ttu-id="b184f-111">可用性组无法跨越多个 WSFC 群集。</span><span class="sxs-lookup"><span data-stu-id="b184f-111">An availability group cannot span WSFC clusters.</span></span>  
  
-   <span data-ttu-id="b184f-112">服务器实例必须正在运行支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="b184f-112">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
-   <span data-ttu-id="b184f-113">一次仅为一个服务器实例启用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b184f-113">Enable AlwaysOn Availability Groups for only one server instance at a time.</span></span> <span data-ttu-id="b184f-114">在启用 AlwaysOn 可用性组之后，一直等待，直到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务已重新启动，然后才启用下一个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="b184f-114">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has restarted before you enable the next server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b184f-115">有关功能支持的信息和有关 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]其他先决条件、局限性和建议的信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b184f-115">For information about feature support and for information about additional prerequisites, restrictions, and recommendations for [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
## <a name="dialog-options"></a><span data-ttu-id="b184f-116">对话框选项</span><span class="sxs-lookup"><span data-stu-id="b184f-116">Dialog Options</span></span>  
 <span data-ttu-id="b184f-117">**Windows 故障转移群集名称**</span><span class="sxs-lookup"><span data-stu-id="b184f-117">**Windows failover cluster name**</span></span>  
 <span data-ttu-id="b184f-118">显示本地计算机在其中作为一个节点的 WSFC 群集的名称。</span><span class="sxs-lookup"><span data-stu-id="b184f-118">Displays the name of the WSFC cluster in which the local computer is a node.</span></span>  
  
 <span data-ttu-id="b184f-119">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="b184f-119">**Enable AlwaysOn Availability Groups**</span></span>  
 <span data-ttu-id="b184f-120">使用此复选框可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的这一实例上启用或禁用 AlwaysOn 可用性组，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b184f-120">Use this check box to enable or disable AlwaysOn Availability Groups on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as follows:</span></span>  
  
-   <span data-ttu-id="b184f-121">如果此复选框为空，则当前禁用 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b184f-121">If this check box is empty, AlwaysOn Availability Groups is currently disabled.</span></span> <span data-ttu-id="b184f-122">若要启用 AlwaysOn 可用性组，请选中此复选框，单击 **“确定”**，然后手动重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="b184f-122">To enable AlwaysOn Availability Groups, select this check box, click **OK**, and manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="b184f-123">如果已选中此复选框，则当前启用了 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="b184f-123">If this check box is already selected, AlwaysOn Availability Groups is currently enabled.</span></span> <span data-ttu-id="b184f-124">若要禁用 AlwaysOn 可用性组，请取消选中此复选框，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="b184f-124">To disable AlwaysOn Availability Groups, uncheck the check box and click **OK**.</span></span> <span data-ttu-id="b184f-125">这会导致服务器实例重新启动。</span><span class="sxs-lookup"><span data-stu-id="b184f-125">This causes the server instance to restart.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="b184f-126">在启用 AlwaysOn 可用性组之后，应从服务器实例中删除任何本地化可用性副本。</span><span class="sxs-lookup"><span data-stu-id="b184f-126">After disabling AlwaysOn Availability Groups, you should remove any local availability replicas from the server instance.</span></span> <span data-ttu-id="b184f-127">如果您删除了给定可用性组的最后一个副本，则还应删除此组。</span><span class="sxs-lookup"><span data-stu-id="b184f-127">If you remove the last replica of a given availability group, you should also remove the group.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b184f-128">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="b184f-128">UI element list</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b184f-129">有关在禁用 AlwaysOn 可用性组后如何进行操作的详细信息以及如何创建和配置可用性组的信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b184f-129">For more information about follow up after you disable AlwaysOn Availability Groups and for information about how to create and configure availability groups, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
