---
title: 编程特定任务 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SQL Server Management Objects, tasks
- SMO [SQL Server], programming
- SMO [SQL Server], tasks
ms.assetid: a15949ef-88d9-4205-892e-0b66588b4fcc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 215e31cb4e88403f5936c987029203736bb1300a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588942"
---
# <a name="programming-specific-tasks"></a><span data-ttu-id="4cf96-102">编程特定的任务</span><span class="sxs-lookup"><span data-stu-id="4cf96-102">Programming Specific Tasks</span></span>
  <span data-ttu-id="4cf96-103">使用 SMO 对象的编程特定的任务包含一些复杂主题，只有具有特定函数的程序才需要这些主题，例如，备份、监视统计信息、复制、管理实例对象以及设置配置选项。</span><span class="sxs-lookup"><span data-stu-id="4cf96-103">Programming-specific tasks using SMO objects include complex subjects that would only be required by programs with a specific function, such as backing up, monitoring statistics, replication, managing instance objects, and setting configuration options.</span></span>  
  
|<span data-ttu-id="4cf96-104">主题</span><span class="sxs-lookup"><span data-stu-id="4cf96-104">Topic</span></span>|<span data-ttu-id="4cf96-105">说明</span><span class="sxs-lookup"><span data-stu-id="4cf96-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4cf96-106">在 SMO 中使用链接服务器</span><span class="sxs-lookup"><span data-stu-id="4cf96-106">Using Linked Servers in SMO</span></span>](using-linked-servers-in-smo.md)|<span data-ttu-id="4cf96-107">介绍 SMO 如何使用 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 对象以链接 OLE-DB 服务器。</span><span class="sxs-lookup"><span data-stu-id="4cf96-107">Describes how SMO uses the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object to link OLE-DB servers.</span></span>|  
|[<span data-ttu-id="4cf96-108">在 SMO 中配置 SQL Server</span><span class="sxs-lookup"><span data-stu-id="4cf96-108">Configuring SQL Server in SMO</span></span>](configuring-sql-server-in-smo.md)|<span data-ttu-id="4cf96-109">介绍如何在 SMO 中查看和修改 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的配置设置。</span><span class="sxs-lookup"><span data-stu-id="4cf96-109">Describes how to view and modify configuration settings for the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-110">使用表和索引分区</span><span class="sxs-lookup"><span data-stu-id="4cf96-110">Using Table and Index Partitioning</span></span>](using-table-and-index-partitioning.md)|<span data-ttu-id="4cf96-111">介绍如何在 SMO 中使用索引和表分区。</span><span class="sxs-lookup"><span data-stu-id="4cf96-111">Describes how to use index and table partitioning in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-112">使用文件组和文件存储数据</span><span class="sxs-lookup"><span data-stu-id="4cf96-112">Using Filegroups and Files to Store Data</span></span>](using-filegroups-and-files-to-store-data.md)|<span data-ttu-id="4cf96-113">介绍如何在 SMO 中使用文件组。</span><span class="sxs-lookup"><span data-stu-id="4cf96-113">Describes how to use file groups in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-114">使用 WMI 提供程序管理服务和网络设置</span><span class="sxs-lookup"><span data-stu-id="4cf96-114">Managing Services and Network Settings by Using WMI Provider</span></span>](managing-services-and-network-settings-by-using-wmi-provider.md)|<span data-ttu-id="4cf96-115">介绍使用 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 对象（该对象表示配置管理的 WMI 提供程序）对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例保持跟踪的若干方法。</span><span class="sxs-lookup"><span data-stu-id="4cf96-115">Describes several ways to keep track of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object that represents the WMI Provider for Configuration Management.</span></span>|  
|[<span data-ttu-id="4cf96-116">使用数据库对象</span><span class="sxs-lookup"><span data-stu-id="4cf96-116">Working with Database Objects</span></span>](creating-altering-and-removing-database-objects.md)|<span data-ttu-id="4cf96-117">介绍如何创建表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例中的对象的实例类。</span><span class="sxs-lookup"><span data-stu-id="4cf96-117">Describes how to create instance classes that represent objects on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4cf96-118">管理用户、角色和登录帐户</span><span class="sxs-lookup"><span data-stu-id="4cf96-118">Managing Users, Roles, and Logins</span></span>](managing-users-roles-and-logins.md)|<span data-ttu-id="4cf96-119">介绍如何在 SMO 中使用安全角色。</span><span class="sxs-lookup"><span data-stu-id="4cf96-119">Describes how to use security roles in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-120">授予、撤消和拒绝权限</span><span class="sxs-lookup"><span data-stu-id="4cf96-120">Granting, Revoking, and Denying Permissions</span></span>](granting-revoking-and-denying-permissions.md)|<span data-ttu-id="4cf96-121">介绍如何使用 SMO 对用户或角色成员授予、撤消和拒绝权限。</span><span class="sxs-lookup"><span data-stu-id="4cf96-121">Describes how to use the SMO to grant, revoke, and deny permissions to users or members of a role.</span></span>|  
|[<span data-ttu-id="4cf96-122">使用加密</span><span class="sxs-lookup"><span data-stu-id="4cf96-122">Using Encryption</span></span>](using-encryption.md)|<span data-ttu-id="4cf96-123">介绍如何在 SMO 中使用加密来保护数据。</span><span class="sxs-lookup"><span data-stu-id="4cf96-123">Describes how to protect data using encryption in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-124">在 SQL Server 代理中计划自动管理任务</span><span class="sxs-lookup"><span data-stu-id="4cf96-124">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>](../../../ssms/agent/sql-server-agent.md)|<span data-ttu-id="4cf96-125">介绍如何在 SMO 中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理以监视、报告和安排作业。</span><span class="sxs-lookup"><span data-stu-id="4cf96-125">Describes how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to monitor, report, and schedule jobs in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-126">备份和还原数据库和事务日志</span><span class="sxs-lookup"><span data-stu-id="4cf96-126">Backing Up and Restoring Databases and Transaction Logs</span></span>](backing-up-and-restoring-databases-and-transaction-logs.md)|<span data-ttu-id="4cf96-127">介绍如何在 SMO 中备份和还原数据库和事务日志。</span><span class="sxs-lookup"><span data-stu-id="4cf96-127">Describes how to back up and restore databases and transaction logs in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-128">脚本</span><span class="sxs-lookup"><span data-stu-id="4cf96-128">Scripting</span></span>](scripting.md)|<span data-ttu-id="4cf96-129">介绍如何在 SMO 中为对象编写脚本和发现对象之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="4cf96-129">Describes how to script objects and discover dependencies between objects in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-130">传输数据</span><span class="sxs-lookup"><span data-stu-id="4cf96-130">Transferring Data</span></span>](transferring-data.md)|<span data-ttu-id="4cf96-131">介绍如何在 SMO 中传输数据。</span><span class="sxs-lookup"><span data-stu-id="4cf96-131">Describes how to transfer data in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-132">使用数据库邮件</span><span class="sxs-lookup"><span data-stu-id="4cf96-132">Using Database Mail</span></span>](using-database-mail.md)|<span data-ttu-id="4cf96-133">介绍 SMO 如何利用电子邮件服务。</span><span class="sxs-lookup"><span data-stu-id="4cf96-133">Describes how SMO makes use of e-mail services.</span></span>|  
|[<span data-ttu-id="4cf96-134">管理 Service Broker</span><span class="sxs-lookup"><span data-stu-id="4cf96-134">Managing Service Broker</span></span>](managing-service-broker.md)|<span data-ttu-id="4cf96-135">介绍如何使用 SMO 设置 Service Broker。</span><span class="sxs-lookup"><span data-stu-id="4cf96-135">Describes how to set up Service Broker using SMO.</span></span>|  
|[<span data-ttu-id="4cf96-136">使用 XML 架构</span><span class="sxs-lookup"><span data-stu-id="4cf96-136">Using XML Schemas</span></span>](using-xml-schemas.md)|<span data-ttu-id="4cf96-137">介绍如何在 SMO 中使用 XML 数据类型。</span><span class="sxs-lookup"><span data-stu-id="4cf96-137">Describes how to use the XML data type in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-138">使用同义词</span><span class="sxs-lookup"><span data-stu-id="4cf96-138">Using Synonyms</span></span>](using-synonyms.md)|<span data-ttu-id="4cf96-139">介绍如何在 SMO 中创建同义词。</span><span class="sxs-lookup"><span data-stu-id="4cf96-139">Describes how to create synonyms in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-140">使用消息</span><span class="sxs-lookup"><span data-stu-id="4cf96-140">Using Messages</span></span>](using-messages.md)|<span data-ttu-id="4cf96-141">介绍如何使用系统消息，以及如何定义自己的用户定义消息。</span><span class="sxs-lookup"><span data-stu-id="4cf96-141">Describes how to use system messages, and how to define your own user-defined messages.</span></span>|  
|[<span data-ttu-id="4cf96-142">实现全文搜索</span><span class="sxs-lookup"><span data-stu-id="4cf96-142">Implementing Full-Text Search</span></span>](implementing-full-text-search.md)|<span data-ttu-id="4cf96-143">介绍如何在 SMO 中实现全文搜索目录和索引。</span><span class="sxs-lookup"><span data-stu-id="4cf96-143">Describes how to implement full-text search catalogs and indexes in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-144">实现端点</span><span class="sxs-lookup"><span data-stu-id="4cf96-144">Implementing Endpoints</span></span>](implementing-endpoints.md)|<span data-ttu-id="4cf96-145">介绍如何创建端点以处理用于数据库镜像、SOAP 请求和 Service Broker 的负载。</span><span class="sxs-lookup"><span data-stu-id="4cf96-145">Describes how to create endpoints to handle payloads for Database Mirroring, SOAP requests, and Service Broker.</span></span>|  
|[<span data-ttu-id="4cf96-146">创建和更新统计信息</span><span class="sxs-lookup"><span data-stu-id="4cf96-146">Creating and Updating Statistics</span></span>](../../statistics/statistics.md)|<span data-ttu-id="4cf96-147">介绍如何在 SMO 中设置和监视有关数据库的统计信息。</span><span class="sxs-lookup"><span data-stu-id="4cf96-147">Describes how to set up and monitor statistics on a database in SMO.</span></span>|  
|[<span data-ttu-id="4cf96-148">跟踪和重播事件</span><span class="sxs-lookup"><span data-stu-id="4cf96-148">Tracing and Replaying Events</span></span>](tracing-and-replaying-events.md)|<span data-ttu-id="4cf96-149">介绍如何使用 SMO 中的 `Trace` 和 `Replay` 对象以跟踪和重播事件。</span><span class="sxs-lookup"><span data-stu-id="4cf96-149">Describes how to use the `Trace` and `Replay` objects in SMO to trace and replay events.</span></span>|  
  
  
