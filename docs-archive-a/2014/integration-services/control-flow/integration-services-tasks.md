---
title: Integration Services 任务 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580818"
---
# <a name="integration-services-tasks"></a><span data-ttu-id="7891c-102">Integration Services 任务</span><span class="sxs-lookup"><span data-stu-id="7891c-102">Integration Services Tasks</span></span>
  <span data-ttu-id="7891c-103">任务是一些控制流元素，它定义包控制流中执行的工作单元。</span><span class="sxs-lookup"><span data-stu-id="7891c-103">Tasks are control flow elements that define units of work that are performed in a package control flow.</span></span> <span data-ttu-id="7891c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包由一个或多个任务组成。</span><span class="sxs-lookup"><span data-stu-id="7891c-104">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package is made up of one or more tasks.</span></span> <span data-ttu-id="7891c-105">如果包中包含多个任务，则它们将按照优先约束在控制流中进行连接和排序。</span><span class="sxs-lookup"><span data-stu-id="7891c-105">If the package contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span>  
  
 <span data-ttu-id="7891c-106">您还可使用支持 COM 的编程语言（如 Visual Basic）或 .NET 编程语言（如 C#）编写自定义任务。</span><span class="sxs-lookup"><span data-stu-id="7891c-106">You can also write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span>  
  
 <span data-ttu-id="7891c-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中用于处理包的图形工具，可提供用于创建包控制流的设计界面，以及用于配置任务的自定义编辑器。</span><span class="sxs-lookup"><span data-stu-id="7891c-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the graphical tool in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] for working with packages, provides the design surface for creating package control flow, and provides custom editors for configuring tasks.</span></span> <span data-ttu-id="7891c-108">你还可以对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 对象模型进行编程，以便通过编程方式创建包。</span><span class="sxs-lookup"><span data-stu-id="7891c-108">You can also program the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to create packages programmatically.</span></span>  
  
## <a name="types-of-tasks"></a><span data-ttu-id="7891c-109">任务的类型</span><span class="sxs-lookup"><span data-stu-id="7891c-109">Types of Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="7891c-110">中包括下列类型的任务。</span><span class="sxs-lookup"><span data-stu-id="7891c-110">includes the following types of tasks.</span></span>  
  
 <span data-ttu-id="7891c-111">数据流任务</span><span class="sxs-lookup"><span data-stu-id="7891c-111">Data Flow Task</span></span>  
 <span data-ttu-id="7891c-112">数据流任务用于运行数据流以提取数据、应用列级转换和加载数据。</span><span class="sxs-lookup"><span data-stu-id="7891c-112">The task that runs data flows to extract data, apply column level transformations, and load data.</span></span>  
  
 <span data-ttu-id="7891c-113">数据准备任务</span><span class="sxs-lookup"><span data-stu-id="7891c-113">Data Preparation Tasks</span></span>  
 <span data-ttu-id="7891c-114">这些任务执行以下过程：复制文件和目录；下载文件和数据；运行 Web 方法；对 XML 文档应用操作以及对数据进行事件探查以便清除。</span><span class="sxs-lookup"><span data-stu-id="7891c-114">These tasks do the following processes: copy files and directories; download files and data; run Web methods; apply operations to XML documents; and profile data for cleansing.</span></span>  
  
 <span data-ttu-id="7891c-115">工作流任务</span><span class="sxs-lookup"><span data-stu-id="7891c-115">Workflow Tasks</span></span>  
 <span data-ttu-id="7891c-116">工作流任务与其他进程通信以运行包、程序或批处理文件，在包之间发送和接收消息，发送电子邮件，读取 Windows Management Instrumentation (WMI) 数据和监视 WMI 事件。</span><span class="sxs-lookup"><span data-stu-id="7891c-116">The tasks that communicate with other processes to run packages, run programs or batch files, send and receive messages between packages, send e-mail messages, read Windows Management Instrumentation (WMI) data, and watch for WMI events.</span></span>  
  
 <span data-ttu-id="7891c-117">SQL Server 任务</span><span class="sxs-lookup"><span data-stu-id="7891c-117">SQL Server Tasks</span></span>  
 <span data-ttu-id="7891c-118">SQL Server 任务用于访问、复制、插入、删除和修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象和数据。</span><span class="sxs-lookup"><span data-stu-id="7891c-118">The tasks that access, copy, insert, delete, and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and data.</span></span>  
  
 <span data-ttu-id="7891c-119">脚本任务</span><span class="sxs-lookup"><span data-stu-id="7891c-119">Scripting Tasks</span></span>  
 <span data-ttu-id="7891c-120">脚本任务通过使用脚本来扩展包功能。</span><span class="sxs-lookup"><span data-stu-id="7891c-120">The tasks that extend package functionality by using scripts.</span></span>  
  
 <span data-ttu-id="7891c-121">Analysis Services 任务</span><span class="sxs-lookup"><span data-stu-id="7891c-121">Analysis Services Tasks</span></span>  
 <span data-ttu-id="7891c-122">该任务用于创建、修改、删除和处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="7891c-122">The tasks that create, modify, delete, and process [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="7891c-123">维护任务</span><span class="sxs-lookup"><span data-stu-id="7891c-123">Maintenance Tasks</span></span>  
 <span data-ttu-id="7891c-124">维护任务用于执行管理功能，如备份和收缩 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库、重新生成和重新组织索引以及运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="7891c-124">The tasks that perform administrative functions such as backing up and shrinking [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, rebuilding and reorganizing indexes, and running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="7891c-125">自定义任务</span><span class="sxs-lookup"><span data-stu-id="7891c-125">Custom Tasks</span></span>  
 <span data-ttu-id="7891c-126">此外，您还可以使用支持 COM 的编程语言（如 Visual Basic）或 .NET 编程语言（如 C#）编写自定义任务。</span><span class="sxs-lookup"><span data-stu-id="7891c-126">Additionally, you can write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span> <span data-ttu-id="7891c-127">如果希望在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中访问自定义任务，那么你可以为该任务创建和注册一个用户接口。</span><span class="sxs-lookup"><span data-stu-id="7891c-127">If you want to access your custom task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can create and register a user interface for the task.</span></span> <span data-ttu-id="7891c-128">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-128">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="configuration-of-tasks"></a><span data-ttu-id="7891c-129">任务的配置</span><span class="sxs-lookup"><span data-stu-id="7891c-129">Configuration of Tasks</span></span>  
 <span data-ttu-id="7891c-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包可以只包含单个任务，如在包运行时删除数据库表中记录的执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="7891c-130">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can contain a single task, such as an Execute SQL task that deletes records in a database table when the package runs.</span></span> <span data-ttu-id="7891c-131">但是，包通常包含多个任务，而且每个任务都被设置为在包控制流上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="7891c-131">However, packages typically contain several tasks, and each task is set to run within the context of the package control flow.</span></span> <span data-ttu-id="7891c-132">事件处理程序是为响应运行时事件而运行的工作流，该程序中也可包含任务。</span><span class="sxs-lookup"><span data-stu-id="7891c-132">Event handlers, which are workflows that run in response to run-time events, can also have tasks.</span></span>  
  
 <span data-ttu-id="7891c-133">有关使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器向包添加任务的详细信息，请参阅 [在控制流中添加或删除任务或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-133">For more information about adding a task to a package using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>  
  
 <span data-ttu-id="7891c-134">有关如何以编程方式向包中添加任务的详细信息，请参阅 [以编程方式添加任务](../building-packages-programmatically/adding-tasks-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-134">For more information about adding a task to a package programmatically, see [Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md).</span></span>  
  
 <span data-ttu-id="7891c-135">对于每个任务，可以使用 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器为每个任务提供的自定义对话框单独配置，也可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中包含的“属性”窗口进行配置。</span><span class="sxs-lookup"><span data-stu-id="7891c-135">Each task can be configured individually using the custom dialog boxes for each task that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, or the Properties window included in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="7891c-136">一个包中可以包含多个相同类型的任务（如六个执行 SQL 任务），对每个任务可进行不同的配置。</span><span class="sxs-lookup"><span data-stu-id="7891c-136">A package can include multiple tasks of the same type-for example, six Execute SQL tasks-and each task can be configured differently.</span></span> <span data-ttu-id="7891c-137">有关详细信息，请参阅 [设置任务或容器的属性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-137">For more information, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="tasks-connections-and-groups"></a><span data-ttu-id="7891c-138">任务连接和组</span><span class="sxs-lookup"><span data-stu-id="7891c-138">Tasks Connections and Groups</span></span>  
 <span data-ttu-id="7891c-139">如果连接和分组任务中包含多个任务，则它们将被按照优先约束在控制流中进行连接和排序。</span><span class="sxs-lookup"><span data-stu-id="7891c-139">If the task contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span> <span data-ttu-id="7891c-140">有关详细信息，请参阅 [优先约束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-140">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="7891c-141">任务可被分组到一起作为一个工作单元执行，也可在循环中重复执行。</span><span class="sxs-lookup"><span data-stu-id="7891c-141">Tasks can be grouped together and performed as a single unit of work, or repeated in a loop.</span></span> <span data-ttu-id="7891c-142">有关详细信息，请参阅 [Foreach Loop Container](foreach-loop-container.md)、 [For Loop Container](for-loop-container.md)和 [Sequence Container](sequence-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7891c-142">For more information, see [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md), and [Sequence Container](sequence-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7891c-143">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="7891c-143">Related Tasks</span></span>  
 [<span data-ttu-id="7891c-144">在控制流中添加或删除任务或容器</span><span class="sxs-lookup"><span data-stu-id="7891c-144">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
