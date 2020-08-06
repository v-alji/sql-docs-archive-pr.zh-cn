---
title: 重命名 SQL Server 故障转移群集实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 397e36931e446861db0fcb899cad30e8c7b1ffc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586288"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a><span data-ttu-id="a64a0-102">重命名 SQL Server 故障转移群集实例</span><span class="sxs-lookup"><span data-stu-id="a64a0-102">Rename a SQL Server Failover Cluster Instance</span></span>
  <span data-ttu-id="a64a0-103">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例包括在故障转移群集中，则重命名虚拟服务器的过程不同于重命名独立实例的过程。</span><span class="sxs-lookup"><span data-stu-id="a64a0-103">When a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is part of a failover cluster, the process of renaming the virtual server differs from that of renaming a stand-alone instance.</span></span> <span data-ttu-id="a64a0-104">有关详细信息，请参阅 [重命名承载 SQL Server 独立实例的计算机](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a0-104">For more information, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="a64a0-105">虚拟服务器的名称始终与 SQL 网络名称（SQL 虚拟服务器的网络名称）相同。</span><span class="sxs-lookup"><span data-stu-id="a64a0-105">The name of the virtual server is always the same as the name of the SQL Network Name (the SQL Virtual Server Network Name).</span></span> <span data-ttu-id="a64a0-106">尽管您可以更改虚拟服务器的名称，但不能更改实例名。</span><span class="sxs-lookup"><span data-stu-id="a64a0-106">Although you can change the name of the virtual server, you cannot change the instance name.</span></span> <span data-ttu-id="a64a0-107">例如，您可以将名为 VS1\instance1 的虚拟服务器更改为其他名称（例如 SQL35\instance1），但是名称的实例部分 (instance1) 将保持不变。</span><span class="sxs-lookup"><span data-stu-id="a64a0-107">For example, you can change a virtual server named VS1\instance1 to some other name, such as SQL35\instance1, but the instance portion of the name, instance1, will remain unchanged.</span></span>  
  
 <span data-ttu-id="a64a0-108">开始重命名进程之前，请阅读下列各项。</span><span class="sxs-lookup"><span data-stu-id="a64a0-108">Before you begin the renaming process, review the items below.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a64a0-109">不支持对复制所涉及的服务器进行重命名。</span><span class="sxs-lookup"><span data-stu-id="a64a0-109">does not support renaming servers involved in replication, except in the case of using log shipping with replication.</span></span> <span data-ttu-id="a64a0-110">如果主服务器永久丢失连接，则可以重命名日志传送中的辅助服务器。</span><span class="sxs-lookup"><span data-stu-id="a64a0-110">The secondary server in log shipping can be renamed if the primary server is permanently lost.</span></span> <span data-ttu-id="a64a0-111">有关详细信息，请参阅[日志传送和复制 (SQL Server)](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a0-111">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a64a0-112">当您重命名被配置为使用数据库镜像的虚拟服务器时，必须在进行重命名操作之前先关闭数据库镜像，然后用新的虚拟服务器名称重新建立数据库镜像。</span><span class="sxs-lookup"><span data-stu-id="a64a0-112">When renaming a virtual server that is configured to use database mirroring, you must turn off database mirroring before the renaming operation, and then re-establish database mirroring with the new virtual server name.</span></span> <span data-ttu-id="a64a0-113">数据库镜像的元数据将不会自动更新来反映新的虚拟服务器名称。</span><span class="sxs-lookup"><span data-stu-id="a64a0-113">Metadata for database mirroring will not be updated automatically to reflect the new virtual server name.</span></span>  
  
### <a name="to-rename-a-virtual-server"></a><span data-ttu-id="a64a0-114">重命名虚拟服务器</span><span class="sxs-lookup"><span data-stu-id="a64a0-114">To rename a virtual server</span></span>  
  
1.  <span data-ttu-id="a64a0-115">使用群集管理器将 SQL 网络名称更改为新名称。</span><span class="sxs-lookup"><span data-stu-id="a64a0-115">Using Cluster Administrator, change the SQL Network Name to the new name.</span></span>  
  
2.  <span data-ttu-id="a64a0-116">使网络名称资源脱机。</span><span class="sxs-lookup"><span data-stu-id="a64a0-116">Take the network name resource offline.</span></span> <span data-ttu-id="a64a0-117">这将使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源和其他相关资源也脱机。</span><span class="sxs-lookup"><span data-stu-id="a64a0-117">This takes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource and other dependent resources offline as well.</span></span>  
  
3.  <span data-ttu-id="a64a0-118">使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源重新联机。</span><span class="sxs-lookup"><span data-stu-id="a64a0-118">Bring the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource back online.</span></span>  
  
## <a name="verify-the-renaming-operation"></a><span data-ttu-id="a64a0-119">验证重命名操作</span><span class="sxs-lookup"><span data-stu-id="a64a0-119">Verify the Renaming Operation</span></span>  
 <span data-ttu-id="a64a0-120">虚拟服务器被重命名之后，任何使用旧名称的连接现在都必须使用新名称来连接。</span><span class="sxs-lookup"><span data-stu-id="a64a0-120">After a virtual server has been renamed, any connections that used the old name must now connect using the new name.</span></span>  
  
 <span data-ttu-id="a64a0-121">若要验证重命名操作是否已完成，请从 `@@servername` 或 `sys.servers` 中选择信息。</span><span class="sxs-lookup"><span data-stu-id="a64a0-121">To verify that the renaming operation has completed, select information from either `@@servername` or `sys.servers`.</span></span> <span data-ttu-id="a64a0-122">`@@servername` 函数将返回新的虚拟服务器名称，`sys.servers` 表将显示新的虚拟服务器名称。</span><span class="sxs-lookup"><span data-stu-id="a64a0-122">The `@@servername` function will return the new virtual server name, and the `sys.servers` table will show the new virtual server name.</span></span> <span data-ttu-id="a64a0-123">若要验证故障转移过程是否能够使用新名称正常工作，用户还应尝试将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源故障转移到其他节点。</span><span class="sxs-lookup"><span data-stu-id="a64a0-123">To verify that the failover process is working correctly with the new name, the user should also try to fail the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource over to the other nodes.</span></span>  
  
 <span data-ttu-id="a64a0-124">对于从群集中任何节点进行的连接，都可以立即使用新名称。</span><span class="sxs-lookup"><span data-stu-id="a64a0-124">For connections from any node in the cluster, the new name can be used almost immediately.</span></span> <span data-ttu-id="a64a0-125">但是，对于从客户端计算机使用新名称进行的连接，则必须在新名称对该客户端计算机可见之后，才能使用新名称连接到服务器。</span><span class="sxs-lookup"><span data-stu-id="a64a0-125">However, for connections using the new name from a client computer, the new name cannot be used to connect to the server until the new name is visible to that client computer.</span></span> <span data-ttu-id="a64a0-126">根据网络配置，通过网络传播新名称所需的时间长度可能为几秒钟，也可能长至 3 到 5 分钟；旧的虚拟服务器名称在网络上不再可见也可能会需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="a64a0-126">The length of time required for the new name to be propagated across a network can be a few seconds, or as long as 3 to 5 minutes, depending on the network configuration; additional time may be required before the old virtual server name is no longer visible on the network.</span></span>  
  
 <span data-ttu-id="a64a0-127">若要最小化虚拟服务器重命名操作的网络传播延迟，请使用下列步骤：</span><span class="sxs-lookup"><span data-stu-id="a64a0-127">To minimize network propagation delay of a virtual server renaming operation, use the following steps:</span></span>  
  
#### <a name="to-minimize-network-propagation-delay"></a><span data-ttu-id="a64a0-128">最小化网络传播延迟</span><span class="sxs-lookup"><span data-stu-id="a64a0-128">To minimize network propagation delay</span></span>  
  
1.  <span data-ttu-id="a64a0-129">在服务器节点上从命令提示符发出下列命令：</span><span class="sxs-lookup"><span data-stu-id="a64a0-129">Issue the following commands from a command prompt on the server node:</span></span>  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a><span data-ttu-id="a64a0-130">在重命名操作之后的其他注意事项</span><span class="sxs-lookup"><span data-stu-id="a64a0-130">Additional considerations after the Renaming Operation</span></span>  
 <span data-ttu-id="a64a0-131">在重命名故障转移群集的网络名称后，需要按照下面的说明进行验证和操作，使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理和 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]在所有情况下都正常工作。</span><span class="sxs-lookup"><span data-stu-id="a64a0-131">After we rename the network name of failover cluster we need to verify and perform the following instructions to enable all scenarios in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a64a0-132">\*\* [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ：\*\* [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 使用 Windows 群集管理器工具更改故障转移群集实例的网络名称后，将来的升级或卸载操作可能会失败。</span><span class="sxs-lookup"><span data-stu-id="a64a0-132">**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** After you change the network name of a [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] failover cluster instance using Windows Cluster Administrator tool, the future upgrade or uninstall operation might fail.</span></span> <span data-ttu-id="a64a0-133">若要解决此问题，请按照[此](https://go.microsoft.com/fwlink/?LinkId=244002) (的解决方法部分中的说明更新**ClusterName**注册表项 https://go.microsoft.com/fwlink/?LinkId=244002) 。</span><span class="sxs-lookup"><span data-stu-id="a64a0-133">To resolve this issue update the **ClusterName** registry entry following the instructions in the resolution section of [this](https://go.microsoft.com/fwlink/?LinkId=244002) (https://go.microsoft.com/fwlink/?LinkId=244002).</span></span>  
  
 <span data-ttu-id="a64a0-134">\*\* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理服务：\*\* 验证和执行以下其他操作 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]代理服务：</span><span class="sxs-lookup"><span data-stu-id="a64a0-134">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:** Verify and perform the below additional actions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:</span></span>  
  
-   <span data-ttu-id="a64a0-135">如果 SQL 代理配置为事件转发，请修复注册表设置。</span><span class="sxs-lookup"><span data-stu-id="a64a0-135">Fix the registry settings if SQL Agent is configured for event forwarding.</span></span> <span data-ttu-id="a64a0-136">有关详细信息，请参阅[指定事件转发服务器 (SQL Server Management Studio)](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a0-136">For more information, see [Designate an Events Forwarding Server &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="a64a0-137">在重命名计算机/群集网络名称后修复主服务器 (MSX) 和目标服务器 (TSX) 实例名称。</span><span class="sxs-lookup"><span data-stu-id="a64a0-137">Fix the master server (MSX) and target servers (TSX) instance names when machines / cluster network name is renamed.</span></span> <span data-ttu-id="a64a0-138">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a64a0-138">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="a64a0-139">将多台目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="a64a0-139">Defect Multiple Target Servers from a Master Server</span></span>](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [<span data-ttu-id="a64a0-140">创建多服务器环境</span><span class="sxs-lookup"><span data-stu-id="a64a0-140">Create a Multiserver Environment</span></span>](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   <span data-ttu-id="a64a0-141">重新配置日志传送以便更新的服务器名称用于备份和还原日志。</span><span class="sxs-lookup"><span data-stu-id="a64a0-141">Reconfigure the Log Shipping so that updated server name is used to backup and restore logs.</span></span> <span data-ttu-id="a64a0-142">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="a64a0-142">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="a64a0-143">配置日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a64a0-143">Configure Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [<span data-ttu-id="a64a0-144">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a64a0-144">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   <span data-ttu-id="a64a0-145">更新依赖于服务器的名称的 Jobsteps。</span><span class="sxs-lookup"><span data-stu-id="a64a0-145">Update the Jobsteps that depend on server name.</span></span> <span data-ttu-id="a64a0-146">有关详细信息，请参阅 [Manage Job Steps](../../../ssms/agent/manage-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="a64a0-146">For more information, see [Manage Job Steps](../../../ssms/agent/manage-job-steps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64a0-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a64a0-147">See Also</span></span>  
 [<span data-ttu-id="a64a0-148">重命名承载 SQL Server 独立实例的计算机</span><span class="sxs-lookup"><span data-stu-id="a64a0-148">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
