---
title: 配置数据库引擎实例 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591593"
---
# <a name="configure-database-engine-instances-sql-server"></a><span data-ttu-id="0014a-102">配置数据库引擎实例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0014a-102">Configure Database Engine Instances (SQL Server)</span></span>
  <span data-ttu-id="0014a-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的每个实例都必须经过配置，以符合为该实例所承载的数据库所定义的性能和可用性要求。</span><span class="sxs-lookup"><span data-stu-id="0014a-103">Each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance.</span></span> <span data-ttu-id="0014a-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 包括一些配置选项，这些选项控制资源使用情况等行为和诸如审核或触发器递归等功能的可用性。</span><span class="sxs-lookup"><span data-stu-id="0014a-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.</span></span>  
  
## <a name="instance-configuration"></a><span data-ttu-id="0014a-105">Instance Configuration</span><span class="sxs-lookup"><span data-stu-id="0014a-105">Instance Configuration</span></span>  
 <span data-ttu-id="0014a-106">将一个数据库部署到生产中时，通常使用一个服务级别协议 (SLA) 来定义一些方面，比如需要的数据库性能级别和数据库可用性级别。</span><span class="sxs-lookup"><span data-stu-id="0014a-106">When a database is deployed into production there is often a service level agreement (SLA) defining areas such as the levels of performance required from the database and the required availability level of the database.</span></span> <span data-ttu-id="0014a-107">SLA 的条款通常会促进实例的配置要求的形成。</span><span class="sxs-lookup"><span data-stu-id="0014a-107">The terms of the SLA typically drive configuration requirements for the instance.</span></span>  
  
 <span data-ttu-id="0014a-108">实例通常在安装后即进行配置。</span><span class="sxs-lookup"><span data-stu-id="0014a-108">An instance is usually configured immediately after it has been installed.</span></span> <span data-ttu-id="0014a-109">初始配置通常由计划部署到实例的数据库类型的 SLA 要求确定。</span><span class="sxs-lookup"><span data-stu-id="0014a-109">The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance.</span></span> <span data-ttu-id="0014a-110">完成部署数据库后，数据库管理员将监视实例性能，如果性能指标表明实例未达到 SLA 要求，则根据需要调整配置设置。</span><span class="sxs-lookup"><span data-stu-id="0014a-110">After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.</span></span>  
  
## <a name="configuration-tasks"></a><span data-ttu-id="0014a-111">配置任务</span><span class="sxs-lookup"><span data-stu-id="0014a-111">Configuration Tasks</span></span>  
  
|<span data-ttu-id="0014a-112">任务说明</span><span class="sxs-lookup"><span data-stu-id="0014a-112">Task Description</span></span>|<span data-ttu-id="0014a-113">主题</span><span class="sxs-lookup"><span data-stu-id="0014a-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0014a-114">说明各种实例配置选项以及如何查看或更改这些选项。</span><span class="sxs-lookup"><span data-stu-id="0014a-114">Describes the various instance configuration options and how to view or change these options.</span></span>|[<span data-ttu-id="0014a-115">服务器配置选项 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0014a-115">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)|  
|<span data-ttu-id="0014a-116">说明如何查看和配置实例中新的数据文件和日志文件的默认位置。</span><span class="sxs-lookup"><span data-stu-id="0014a-116">Describes how to view and configure the default locations of new data and log files in the instance.</span></span>|[<span data-ttu-id="0014a-117">查看或更改数据文件和日志文件的默认位置 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0014a-117">View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|<span data-ttu-id="0014a-118">说明如何将 SQL Server 配置为使用软件 NUMA。</span><span class="sxs-lookup"><span data-stu-id="0014a-118">Describes how to configure SQL Server to use soft-NUMA.</span></span>|[<span data-ttu-id="0014a-119">将 SQL Server 配置为使用软件 NUMA &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0014a-119">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)|  
|<span data-ttu-id="0014a-120">说明如何将 TCP/IP 端口映射到非一致性内存访问 (NUMA) 节点关联。</span><span class="sxs-lookup"><span data-stu-id="0014a-120">Describes how to map a TCP/IP port to non-uniform memory access (NUMA) node affinity.</span></span>|[<span data-ttu-id="0014a-121">将 TCP IP 端口映射到 NUMA 节点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0014a-121">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|<span data-ttu-id="0014a-122">说明如何启用 Windows“锁定内存页”策略。</span><span class="sxs-lookup"><span data-stu-id="0014a-122">Describes how to enable the Windows Lock Pages In Memory policy.</span></span> <span data-ttu-id="0014a-123">此策略将确定哪些帐户可以使用进程将数据保留在物理内存中，从而阻止系统将数据分页到磁盘的虚拟内存中。</span><span class="sxs-lookup"><span data-stu-id="0014a-123">This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>|[<span data-ttu-id="0014a-124">启用“锁定内存页”选项 (Windows)</span><span class="sxs-lookup"><span data-stu-id="0014a-124">Enable the Lock Pages in Memory Option &#40;Windows&#41;</span></span>](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0014a-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0014a-125">See Also</span></span>  
 [<span data-ttu-id="0014a-126">数据库引擎实例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0014a-126">Database Engine Instances &#40;SQL Server&#41;</span></span>](database-engine-instances-sql-server.md)  
  
  
