---
title: 在故障转移群集中设置 FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29541bbcfd323a85a3fa751f60904fd1a26e1199
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682891"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="bdf23-102">在故障转移群集中设置 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="bdf23-102">Set Up FILESTREAM on a Failover Cluster</span></span>
  <span data-ttu-id="bdf23-103">本主题说明了如何在故障转移群集中启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="bdf23-103">This topic describes how to enable FILESTREAM on a failover cluster.</span></span> <span data-ttu-id="bdf23-104">在尝试执行此过程之前，您应该先了解 [故障转移群集](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) 并启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="bdf23-104">Before you try this procedure, you should understand [failover clustering](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) and have FILESTREAM enabled.</span></span> <span data-ttu-id="bdf23-105">有关如何启用 FILESTREAM 的信息，请参阅 [启用和配置 FILESTREAM](enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf23-105">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="bdf23-106">在故障转移群集中设置 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="bdf23-106">To set up FILESTREAM on a failover cluster</span></span>  
  
1.  <span data-ttu-id="bdf23-107">为故障转移群集设置主节点。</span><span class="sxs-lookup"><span data-stu-id="bdf23-107">Set up the primary node for the failover cluster.</span></span>  
  
     <span data-ttu-id="bdf23-108">在设置完成后，使用 **“SQL Server  配置管理器”** 在主节点上启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="bdf23-108">After the setup finishes, enable FILESTREAM on the primary node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="bdf23-109">这将启用需要 Windows 管理员特权的设置。</span><span class="sxs-lookup"><span data-stu-id="bdf23-109">This enables the settings that require Windows Admin privileges.</span></span> <span data-ttu-id="bdf23-110">如果需要远程访问，请选择 **“允许远程客户端针对 FILESTREAM 数据启用流访问”** 。</span><span class="sxs-lookup"><span data-stu-id="bdf23-110">If remote access is required, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span> <span data-ttu-id="bdf23-111">这会创建一个文件共享群集资源。</span><span class="sxs-lookup"><span data-stu-id="bdf23-111">This will create a file-share cluster resource.</span></span>  
  
2.  <span data-ttu-id="bdf23-112">设置被动节点。</span><span class="sxs-lookup"><span data-stu-id="bdf23-112">Set up a passive node.</span></span>  
  
     <span data-ttu-id="bdf23-113">在设置完成后，使用 **“SQL Server 配置管理器”** 在被动节点上启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="bdf23-113">After the setup finishes, enable FILESTREAM on the passive node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="bdf23-114">在群集的所有节点中，为 **“Windows 共享名”** 指定的名称必须是相同的。</span><span class="sxs-lookup"><span data-stu-id="bdf23-114">The name that you specify for **Windows Share Name** must be the same across all nodes in the cluster.</span></span>  
  
3.  <span data-ttu-id="bdf23-115">若要添加更多的被动节点，请重复步骤 2。</span><span class="sxs-lookup"><span data-stu-id="bdf23-115">To add more passive nodes, repeat step 2.</span></span>  
  
4.  <span data-ttu-id="bdf23-116">在添加了所有节点后，在每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上执行 sp_configure 存储过程以完成该过程。</span><span class="sxs-lookup"><span data-stu-id="bdf23-116">After all the nodes are added, complete the process by executing the sp_configure stored procedure on each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="bdf23-117">若要随时在群集中添加并启用其他节点，您可以重复步骤 2、3 和 4。</span><span class="sxs-lookup"><span data-stu-id="bdf23-117">To add and enable additional nodes to the cluster at any time, you can repeat steps 2, 3, and 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf23-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdf23-118">See Also</span></span>  
 <span data-ttu-id="bdf23-119">[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdf23-119">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="bdf23-120">[创建新的 SQL Server 故障转移群集（安装程序）](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="bdf23-120">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="bdf23-121">[删除 SQL Server 故障转移群集实例（安装程序）](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="bdf23-121">[Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="bdf23-122">在 SQL Server 故障转移群集中添加或删除节点（安装程序）</span><span class="sxs-lookup"><span data-stu-id="bdf23-122">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
