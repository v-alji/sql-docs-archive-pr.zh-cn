---
title: 使用 SQL Server 代理在远程服务器上平衡包的负载 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea7b132d8cf86d2f211da25989df937d0db34ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587892"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a><span data-ttu-id="fe4a8-102">使用 SQL Server 代理在远程服务器上平衡包的负载</span><span class="sxs-lookup"><span data-stu-id="fe4a8-102">Load-Balancing Packages on Remote Servers by Using SQL Server Agent</span></span>
  <span data-ttu-id="fe4a8-103">在必须运行很多包时，方便的做法是使用其他可用的服务器。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-103">When many packages have to be run, it is convenient to use other servers that are available.</span></span> <span data-ttu-id="fe4a8-104">这种当所有包都处于一个父包控制下时使用其他服务器来运行这些包的方法称为负载平衡。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-104">This method of using other servers to run packages when the packages are all under the control of one parent package is called load balancing.</span></span> <span data-ttu-id="fe4a8-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，负载均衡是必须由包的所有者构建的手动过程。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], load balancing is a manual procedure that must be architected by the owners of the packages.</span></span> <span data-ttu-id="fe4a8-106">服务器不自动执行负载平衡。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-106">Load balancing is not performed automatically by the servers.</span></span> <span data-ttu-id="fe4a8-107">而且，在远程服务器上运行的包必须是整个包，而不能是其他包中的单个任务。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-107">Also, the packages that are run on the remote servers must be whole packages, not individual tasks in other packages.</span></span>  
  
 <span data-ttu-id="fe4a8-108">负载平衡在以下情形下是有用的：</span><span class="sxs-lookup"><span data-stu-id="fe4a8-108">Load balancing is useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="fe4a8-109">包可以同时运行。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-109">Packages can run at the same time.</span></span>  
  
-   <span data-ttu-id="fe4a8-110">包很大，并且如果按顺序运行，其运行时间可能超过为处理所留出的时间。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-110">Packages are large and, if run sequentially, can run longer than the time allowed for processing.</span></span>  
  
 <span data-ttu-id="fe4a8-111">管理员和体系结构设计师可以确定使用其他服务器来执行处理是否有益于他们的处理过程。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-111">Administrators and architects can determine whether using additional servers for processing would benefit their processes.</span></span>  
  
## <a name="illustration-of-load-balancing"></a><span data-ttu-id="fe4a8-112">负载平衡的图例</span><span class="sxs-lookup"><span data-stu-id="fe4a8-112">Illustration of Load-Balancing</span></span>  
 <span data-ttu-id="fe4a8-113">以下关系图显示了服务器上的父包。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-113">The following diagram shows a parent package on a server.</span></span> <span data-ttu-id="fe4a8-114">父包包含多个“执行 SQL 作业代理”任务。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-114">The parent package contains multiple Execute SQL Job Agent tasks.</span></span> <span data-ttu-id="fe4a8-115">父包中的每项任务都会调用远程服务器上的 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-115">Each task in the parent package calls a SQL Server Agent on a remote server.</span></span> <span data-ttu-id="fe4a8-116">这些远程服务器包含 SQL Server 代理作业，而作业中包括调用该服务器上的包的步骤。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-116">Those remote servers contain SQL Server Agent jobs that include a step that calls a package on that server.</span></span>  
  
 <span data-ttu-id="fe4a8-117">![SSIS 负载均衡体系结构概览](../media/loadbalancingoverview.gif "SSIS 负载均衡体系结构概览")</span><span class="sxs-lookup"><span data-stu-id="fe4a8-117">![Overview of SSIS load balancing architecture](../media/loadbalancingoverview.gif "Overview of SSIS load balancing architecture")</span></span>  
  
 <span data-ttu-id="fe4a8-118">在此体系结构中的负载平衡所需的步骤不是新的概念。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-118">The steps required for load balancing in this architecture are not new concepts.</span></span> <span data-ttu-id="fe4a8-119">实际上，负载平衡是通过一种新的方式使用现有概念和通用 SSIS 对象实现的。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-119">Instead, load balancing is achieved by using existing concepts and common SSIS objects in a new way.</span></span>  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a><span data-ttu-id="fe4a8-120">使用 SQL Server 代理在远程实例上执行包</span><span class="sxs-lookup"><span data-stu-id="fe4a8-120">Execution of Packages on a Remote Instance by using SQL Server Agent</span></span>  
 <span data-ttu-id="fe4a8-121">在用于执行远程包的基本体系结构中，中心包驻留在控制其他远程包的 SQL Server 实例上。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-121">In the basic architecture for remote package execution, a central package resides on the instance of SQL Server that controls the other remote packages.</span></span> <span data-ttu-id="fe4a8-122">关系图显示了此中心包，它的名称是“SSIS Parent”。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-122">The diagram shows this central package, named the SSIS Parent.</span></span> <span data-ttu-id="fe4a8-123">驻留此父包的实例控制运行子包的 SQL Server 代理作业的执行。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-123">The instance where this parent package resides controls execution of the SQL Server Agent jobs that run the child packages.</span></span> <span data-ttu-id="fe4a8-124">子包不按受远程服务器上的 SQL Server 代理所控制的固定计划来运行。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-124">The child packages are not run according to a fixed schedule controlled by the SQL Server Agent on the remote server.</span></span> <span data-ttu-id="fe4a8-125">实际上，子包在被父包调用时由 SQL Server 代理启动，并运行于 SQL Server 代理所驻留的同一个 SQL Server 实例上。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-125">Instead, the child packages are started by the SQL Server Agent when called by the parent package and are run on the same instance of SQL Server on which the SQL Server Agent resides.</span></span>  
  
 <span data-ttu-id="fe4a8-126">必须先配置父包和子包并设置控制子包的 SQL Server 代理作业，然后才能通过使用 SQL Server 代理来运行远程包。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-126">Before you can run a remote package by using SQL Server Agent, you must configure the parent and child packages and set up the SQL Server Agent jobs that control the child packages.</span></span> <span data-ttu-id="fe4a8-127">以下部分提供了有关如何创建、配置、运行和维护在远程服务器上运行的包的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-127">The following sections provide more information about how to create, configure, run, and maintain packages that run on remote servers.</span></span> <span data-ttu-id="fe4a8-128">该过程有下面几个步骤：</span><span class="sxs-lookup"><span data-stu-id="fe4a8-128">There are several steps to this process:</span></span>  
  
-   <span data-ttu-id="fe4a8-129">创建子包并将它们安装在远程服务器上。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-129">Creating the child packages and installing them on remote servers.</span></span>  
  
-   <span data-ttu-id="fe4a8-130">在将运行包的远程实例上创建 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-130">Creating the SQL Server Agent jobs on the remote instances that will run the packages.</span></span>  
  
-   <span data-ttu-id="fe4a8-131">创建父包。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-131">Creating the parent package.</span></span>  
  
-   <span data-ttu-id="fe4a8-132">确定子包的日志记录方案。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-132">Determine the logging scenario for the child packages.</span></span>  
  
 <span data-ttu-id="fe4a8-133">下表提供的链接所指向的主题可引导您完成此过程。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-133">The following table provides links to topics that guide you through the process.</span></span>  
  
|<span data-ttu-id="fe4a8-134">主题</span><span class="sxs-lookup"><span data-stu-id="fe4a8-134">Topic</span></span>|<span data-ttu-id="fe4a8-135">说明</span><span class="sxs-lookup"><span data-stu-id="fe4a8-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fe4a8-136">子包的实现</span><span class="sxs-lookup"><span data-stu-id="fe4a8-136">Implementation of Child Packages</span></span>](../implementation-of-child-packages.md)|<span data-ttu-id="fe4a8-137">介绍包的安装以及将要运行这些包的 SQL Server 代理作业的创建。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-137">Describes the installation of packages, and creation of the SQL Server Agent jobs to run the packages.</span></span>|  
|[<span data-ttu-id="fe4a8-138">父包的实现</span><span class="sxs-lookup"><span data-stu-id="fe4a8-138">Implementation of the Parent Package</span></span>](../implementation-of-the-parent-package.md)|<span data-ttu-id="fe4a8-139">介绍如何创建包含很多“执行 SQL Server 代理作业”任务的父包。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-139">Describes the creation of the parent package that contains many Execute SQL Server Agent Job tasks.</span></span> <span data-ttu-id="fe4a8-140">每个任务各自运行一个子包。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-140">Each task runs one of the child packages.</span></span>|  
|[<span data-ttu-id="fe4a8-141">远程服务器上的负载平衡包的日志记录</span><span class="sxs-lookup"><span data-stu-id="fe4a8-141">Logging for Load Balanced Packages on Remote Servers</span></span>](../logging-for-load-balanced-packages-on-remote-servers.md)|<span data-ttu-id="fe4a8-142">介绍远程包的日志记录方案。</span><span class="sxs-lookup"><span data-stu-id="fe4a8-142">Describes the logging scenario for the remote packages.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="fe4a8-143">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="fe4a8-143">Related Tasks</span></span>  
 [<span data-ttu-id="fe4a8-144">使用 SQL Server 代理安排包</span><span class="sxs-lookup"><span data-stu-id="fe4a8-144">Schedule a Package by using SQL Server Agent</span></span>](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
