---
title: AlwaysOn 可用性组 (SQL Server) 的 Transact-sql 语句概述 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff25fecf54cfdd1d9c03d1586f0272896542bfa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693481"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a><span data-ttu-id="f17f9-102">AlwaysOn 可用性组的 Transact-SQL 语句概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f17f9-102">Overview of Transact-SQL Statements for AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="f17f9-103">本主题介绍支持部署 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 以及创建和管理指定的可用性组、可用性副本和可用性数据库的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="f17f9-103">This topic introduces the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that support deploying [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and creating and managing an given availability group, availability replica and availability database.</span></span>  
  
  
##  <a name="create-endpoint"></a><a name="CreateEndpoint"></a><span data-ttu-id="f17f9-104">创建终结点</span><span class="sxs-lookup"><span data-stu-id="f17f9-104">CREATE ENDPOINT</span></span>  
 <span data-ttu-id="f17f9-105">[创建终结点 .。。对于 DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql)创建数据库镜像端点（如果服务器实例上不存在）。</span><span class="sxs-lookup"><span data-stu-id="f17f9-105">[CREATE ENDPOINT ... FOR DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) creates a database mirroring endpoint, if none exists on the server instance.</span></span> <span data-ttu-id="f17f9-106">要对其部署 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 或数据库镜像的每个服务器实例都需要一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f17f9-106">Every server instance on which you intend to deploy [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] or database mirroring requires a database mirroring endpoint.</span></span>  
  
 <span data-ttu-id="f17f9-107">在您对其创建端点的服务器实例上执行此语句。</span><span class="sxs-lookup"><span data-stu-id="f17f9-107">Execute this statement on the server instance on which you are creating the endpoint.</span></span> <span data-ttu-id="f17f9-108">仅能在给定的服务器实例上创建一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f17f9-108">You can create only one database mirroring endpoint on a given server instance.</span></span> <span data-ttu-id="f17f9-109">有关详细信息，请参阅 [数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f17f9-109">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
##  <a name="create-availability-group"></a><a name="CreateAG"></a><span data-ttu-id="f17f9-110">创建可用性组</span><span class="sxs-lookup"><span data-stu-id="f17f9-110">CREATE AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="f17f9-111">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) 可以创建新的可用性组，还可以创建可用性组侦听器（此为可选项）。</span><span class="sxs-lookup"><span data-stu-id="f17f9-111">[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) creates a new availability group and optionally an availability group listener.</span></span> <span data-ttu-id="f17f9-112">必须至少指定您的本地服务器实例，该实例将成为初始主副本。</span><span class="sxs-lookup"><span data-stu-id="f17f9-112">Minimally, you must specify your local server instance, which will become the initial primary replica.</span></span> <span data-ttu-id="f17f9-113">还可以选择指定最多四个辅助副本。</span><span class="sxs-lookup"><span data-stu-id="f17f9-113">Optionally, you can also specify up to four secondary replicas.</span></span>  
  
 <span data-ttu-id="f17f9-114">在要承载新可用性组的初始主副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上执行 CREATE AVAILABILITY GROUP。</span><span class="sxs-lookup"><span data-stu-id="f17f9-114">Execute CREATE AVAILABILITY GROUP on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that you want to host the initial primary replica of your new availability group.</span></span> <span data-ttu-id="f17f9-115">此服务器实例必须驻留在 Windows Server 故障转移群集的节点上 (WSFC)  (有关详细信息，请参阅[AlwaysOn 可用性组 &#40;SQL Server&#41;的先决条件、限制和建议](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="f17f9-115">This server instance must reside on a node of a Windows Server Failover Cluster (WSFC) (for more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="alter-availability-group"></a><a name="AlterAG"></a><span data-ttu-id="f17f9-116">更改可用性组</span><span class="sxs-lookup"><span data-stu-id="f17f9-116">ALTER AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="f17f9-117">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 支持更改现有可用性组或可用性组侦听器以便故障转移可用性组。</span><span class="sxs-lookup"><span data-stu-id="f17f9-117">[ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) supports changing an existing availability group or availability group listener and for failing over an availability group.</span></span>  
  
 <span data-ttu-id="f17f9-118">在承载当前主副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上执行 ALTER AVAILABILITY GROUP。</span><span class="sxs-lookup"><span data-stu-id="f17f9-118">Execute ALTER AVAILABILITY GROUP on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the current primary replica.</span></span>  
  
##  <a name="alter-database--set-hadr-"></a><a name="AlterDb"></a><span data-ttu-id="f17f9-119">更改数据库 .。。设置 HADR .。。</span><span class="sxs-lookup"><span data-stu-id="f17f9-119">ALTER DATABASE ... SET HADR ...</span></span>  
 <span data-ttu-id="f17f9-120">使用 ALTER DATABASE 语句的 [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) 子句的选项，您可以将辅助数据库联接到相应主数据库的可用性组、删除已联接的数据库、在已联接的数据库上挂起数据同步以及继续数据同步。</span><span class="sxs-lookup"><span data-stu-id="f17f9-120">The options of the [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) clause of the ALTER DATABASE statement enables you to join a secondary database to the availability group of the corresponding primary database, remove a joined database, and suspend data synchronization on a joined database, and resume data synchronization.</span></span>  
  
##  <a name="drop-availability-group"></a><a name="DropAG"></a><span data-ttu-id="f17f9-121">删除可用性组</span><span class="sxs-lookup"><span data-stu-id="f17f9-121">DROP AVAILABILITY GROUP</span></span>  
 <span data-ttu-id="f17f9-122">[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) 删除指定的可用性组及其所有副本。</span><span class="sxs-lookup"><span data-stu-id="f17f9-122">[DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) removes a specified availability group and all of its replicas.</span></span> <span data-ttu-id="f17f9-123">DROP AVAILABILITY GROUP 可以从 WSFC 故障转移群集的任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 节点上运行。</span><span class="sxs-lookup"><span data-stu-id="f17f9-123">DROP AVAILABILITY GROUP can be run from any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] node in the WSFC failover cluster.</span></span>  
  
##  <a name="restrictions-on-the-availability-group-transact-sql-statements"></a><a name="Restrictions"></a><span data-ttu-id="f17f9-124">对可用性组 Transact-sql 语句的限制</span><span class="sxs-lookup"><span data-stu-id="f17f9-124">Restrictions on the AVAILABILITY GROUP Transact-SQL Statements</span></span>  
 <span data-ttu-id="f17f9-125">CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP 和 DROP AVAILABILITY GROUP [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="f17f9-125">The CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and DROP AVAILABILITY GROUP [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements have the following limitations:</span></span>  
  
-   <span data-ttu-id="f17f9-126">执行这些语句需要在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上启用 HADR 服务，但 DROP AVAILABILITY GROUP 除外。</span><span class="sxs-lookup"><span data-stu-id="f17f9-126">With the exception of DROP AVAILABILITY GROUP, executing these statements requires that the HADR service is enabled on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f17f9-127">有关详细信息，请参阅[启用和禁用 AlwaysOn 可用性组 (SQL Server)](enable-and-disable-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f17f9-127">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f17f9-128">这些语句不能在事务或批处理中执行。</span><span class="sxs-lookup"><span data-stu-id="f17f9-128">These statements cannot be executed within transactions or batches.</span></span>  
  
-   <span data-ttu-id="f17f9-129">尽管这些语句可以最大程度地在失败后进行清除，但不能保证出现故障时回滚所有更改。</span><span class="sxs-lookup"><span data-stu-id="f17f9-129">Though they make a best effort to clean up after a failure, these statements do not guarantee that they will roll back all changes on failure.</span></span> <span data-ttu-id="f17f9-130">但是，系统应该能够完全处理并忽略部分故障。</span><span class="sxs-lookup"><span data-stu-id="f17f9-130">However, systems should be able cleanly handle and then ignore partial failures.</span></span>  
  
-   <span data-ttu-id="f17f9-131">这些语句不支持表达式或变量。</span><span class="sxs-lookup"><span data-stu-id="f17f9-131">These statements do not support expressions or variables.</span></span>  
  
-   <span data-ttu-id="f17f9-132">如果当另一个可用性组操作或恢复正在执行时执行 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，则该语句返回错误。</span><span class="sxs-lookup"><span data-stu-id="f17f9-132">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is executed while another availability group action or recovery is in process, the statement returns an error.</span></span> <span data-ttu-id="f17f9-133">等待该操作或恢复完成，然后重试该语句（根据需要）。</span><span class="sxs-lookup"><span data-stu-id="f17f9-133">Wait for the action or recovery to complete, and retry the statement, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17f9-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f17f9-134">See Also</span></span>  
 [<span data-ttu-id="f17f9-135">AlwaysOn 可用性组 &#40;SQL Server 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="f17f9-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
