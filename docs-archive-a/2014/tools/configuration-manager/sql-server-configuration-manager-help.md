---
title: SQL Server 配置管理器帮助 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10a6d6052fe109892f975774a1ed65b818ef0581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692046"
---
# <a name="sql-server-configuration-manager-help"></a><span data-ttu-id="85b6f-102">SQL Server 配置管理器帮助</span><span class="sxs-lookup"><span data-stu-id="85b6f-102">SQL Server Configuration Manager Help</span></span>
  <span data-ttu-id="85b6f-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务和网络连接。</span><span class="sxs-lookup"><span data-stu-id="85b6f-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and configure network connectivity.</span></span> <span data-ttu-id="85b6f-104">若要创建或管理数据库对象、配置安全性以及编写 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="85b6f-104">To create or manage database objects, configure security, and write [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="85b6f-105">有关 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="85b6f-105">For more information about [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="85b6f-106">本节包含了按 F1 后看到的有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中各对话框的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="85b6f-106">This section contains the F1 Help topics for the dialogs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85b6f-107">配置管理器无法配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="85b6f-107">Configuration Manager cannot configure versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="services"></a><span data-ttu-id="85b6f-108">服务</span><span class="sxs-lookup"><span data-stu-id="85b6f-108">Services</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85b6f-109">配置管理器管理与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]相关的服务。</span><span class="sxs-lookup"><span data-stu-id="85b6f-109">Configuration Manager manages services that are related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="85b6f-110">尽管其中许多任务可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 服务对话框来完成，但值得注意的是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器还可以对其管理的服务执行更多的操作（例如，在服务帐户更改后应用正确的权限）。</span><span class="sxs-lookup"><span data-stu-id="85b6f-110">Although many of these tasks can be accomplished using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Services dialog, is important to note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager performs additional operations on the services it manages, such as applying the correct permissions when the service account is changed.</span></span> <span data-ttu-id="85b6f-111">使用标准的 Windows 服务对话框配置任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务都可能会造成服务无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="85b6f-111">Using the normal Windows Services dialog to configure any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services might cause the service to malfunction.</span></span>  
  
 <span data-ttu-id="85b6f-112">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以完成下列服务任务：</span><span class="sxs-lookup"><span data-stu-id="85b6f-112">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks for services:</span></span>  
  
-   <span data-ttu-id="85b6f-113">启动、停止和暂停服务</span><span class="sxs-lookup"><span data-stu-id="85b6f-113">Start, stop, and pause services</span></span>  
  
-   <span data-ttu-id="85b6f-114">将服务配置为自动启动或手动启动，禁用服务，或者更改其他服务设置</span><span class="sxs-lookup"><span data-stu-id="85b6f-114">Configure services to start automatically or manually, disable the services, or change other service settings</span></span>  
  
-   <span data-ttu-id="85b6f-115">更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务所使用的帐户的密码</span><span class="sxs-lookup"><span data-stu-id="85b6f-115">Change the passwords for the accounts used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services</span></span>  
  
-   <span data-ttu-id="85b6f-116">使用跟踪标志（命令行参数）启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b6f-116">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using trace flags (command line parameters)</span></span>  
  
-   <span data-ttu-id="85b6f-117">查看服务的属性</span><span class="sxs-lookup"><span data-stu-id="85b6f-117">View the properties of services</span></span>  
  
## <a name="sql-server-network-configuration"></a><span data-ttu-id="85b6f-118">SQL Server 网络配置</span><span class="sxs-lookup"><span data-stu-id="85b6f-118">SQL Server Network Configuration</span></span>  
 <span data-ttu-id="85b6f-119">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以完成下列与此计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务相关的任务：</span><span class="sxs-lookup"><span data-stu-id="85b6f-119">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services on this computer:</span></span>  
  
-   <span data-ttu-id="85b6f-120">启用或禁用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络协议</span><span class="sxs-lookup"><span data-stu-id="85b6f-120">Enable or disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
-   <span data-ttu-id="85b6f-121">配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络协议</span><span class="sxs-lookup"><span data-stu-id="85b6f-121">Configure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network protocol</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85b6f-122">有关如何配置协议和连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的简短教程，请参阅 [教程：数据库引擎入门](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="85b6f-122">For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).</span></span>  
  
## <a name="sql-server-native-client-configuration"></a><span data-ttu-id="85b6f-123">SQL Server Native Client 配置</span><span class="sxs-lookup"><span data-stu-id="85b6f-123">SQL Server Native Client Configuration</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="85b6f-124">客户端通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 网络库连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85b6f-124">clients connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client network library.</span></span> <span data-ttu-id="85b6f-125">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以完成下列与此计算机上的客户端应用程序相关的任务：</span><span class="sxs-lookup"><span data-stu-id="85b6f-125">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for the following tasks related to client applications on this computer:</span></span>  
  
-   <span data-ttu-id="85b6f-126">对于此计算机上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端应用程序，指定连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时的协议顺序。</span><span class="sxs-lookup"><span data-stu-id="85b6f-126">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications on this computer, specify the protocol order, when connecting to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="85b6f-127">配置客户端连接协议。</span><span class="sxs-lookup"><span data-stu-id="85b6f-127">Configure client connection protocols.</span></span>  
  
-   <span data-ttu-id="85b6f-128">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端应用程序，创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的别名，使客户端能够使用自定义连接字符串进行连接。</span><span class="sxs-lookup"><span data-stu-id="85b6f-128">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client applications, create aliases for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so that clients can connect using a custom connection string.</span></span>  
  
 <span data-ttu-id="85b6f-129">有关这些任务的详细信息，请参阅每个任务的 F1 帮助。</span><span class="sxs-lookup"><span data-stu-id="85b6f-129">For more information about each of these tasks, see F1 help for each task.</span></span>  
  
#### <a name="to-open-sql-server-configuration-manager"></a><span data-ttu-id="85b6f-130">打开 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="85b6f-130">To open SQL Server Configuration Manager</span></span>  
  
-   <span data-ttu-id="85b6f-131">在“开始”\*\*\*\* 菜单上，依次指向“所有程序”\*\*\*\*、“Microsoft SQL Server”\*\*\*\*（版本）、“配置工具”\*\*\*\*，然后单击“SQL Server 配置管理器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85b6f-131">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server** (version), point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b6f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85b6f-132">See Also</span></span>  
 <span data-ttu-id="85b6f-133">[SQL Server 服务](../../../2014/tools/configuration-manager/sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="85b6f-133">[SQL Server Services](../../../2014/tools/configuration-manager/sql-server-services.md) </span></span>  
 <span data-ttu-id="85b6f-134">[SQL Server 网络配置](sql-server-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="85b6f-134">[SQL Server Network Configuration](sql-server-network-configuration.md) </span></span>  
 <span data-ttu-id="85b6f-135">[SQL Native Client 11.0 配置](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="85b6f-135">[SQL Native Client 11.0 Configuration](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md) </span></span>  
 [<span data-ttu-id="85b6f-136">选择网络协议</span><span class="sxs-lookup"><span data-stu-id="85b6f-136">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
