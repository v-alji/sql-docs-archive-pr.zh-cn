---
title: 开发人员&#39;指南 (复制) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9651aec1f02d19ea3494abf242f75049a4f33f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691693"
---
# <a name="developer39s-guide-replication"></a><span data-ttu-id="10fd0-102">开发人员&#39;指南 (复制) </span><span class="sxs-lookup"><span data-stu-id="10fd0-102">Developer&#39;s Guide (Replication)</span></span>
  <span data-ttu-id="10fd0-103">如果能够以编程方式配置、维护和监视复制拓扑，则不仅可以简化重复性的复制任务，而且还可以改善基于复制的应用程序的用户体验。</span><span class="sxs-lookup"><span data-stu-id="10fd0-103">The ability to programmatically configure, maintain, and monitor a replication topology enables you to both simplify repeated replication tasks and improve the user experience for your replication-based applications.</span></span> <span data-ttu-id="10fd0-104">通过复制编程，最终用户可以获得自定义的复制功能，既无须熟悉复制存储过程和复制代理可执行文件，也无须使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 实现的复制用户界面。</span><span class="sxs-lookup"><span data-stu-id="10fd0-104">By programming replication, your end-users can be provided with customized replication functionalities without having to be familiar with replication stored procedures and replication agent executables or having to using the replication user interface implemented by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="10fd0-105">在下面的应用场景中，您的应用程序可从对复制服务的编程访问中获益：</span><span class="sxs-lookup"><span data-stu-id="10fd0-105">The following are scenarios in which your applications might benefit from programmatic access to replication services:</span></span>  
  
-   <span data-ttu-id="10fd0-106">向现有最终用户应用程序添加复制功能，如当用户单击按钮时同步请求订阅。</span><span class="sxs-lookup"><span data-stu-id="10fd0-106">Adding replication functionalities to an existing end-user application, such as synchronizing a pull subscription when the user clicks a button.</span></span>   
-   <span data-ttu-id="10fd0-107">为远程管理复制创建基于 Web 的用户接口。</span><span class="sxs-lookup"><span data-stu-id="10fd0-107">Creating a Web-based user interface for remotely administering replication.</span></span>    
-   <span data-ttu-id="10fd0-108">创建仅公开部分管理功能的自定义用户接口，可用于从单个位置远程管理多个复制拓扑，或组合管理功能与同步功能。</span><span class="sxs-lookup"><span data-stu-id="10fd0-108">Creating a custom user interface that exposes only a subset of administration functionality, can be used to remotely administer multiple replication topologies from a single location, or that combine administration and synchronization functionalities.</span></span>    
-   <span data-ttu-id="10fd0-109">通过添加对发布、订阅的状态或对分发服务器执行监视的功能来改进现有监视工具。</span><span class="sxs-lookup"><span data-stu-id="10fd0-109">Improving an existing monitoring tool by adding the ability to monitor the status of a publication, subscription, or at the Distributor.</span></span>    
-   <span data-ttu-id="10fd0-110">创建自定义应用程序，以管理订阅或与 Oracle 发布服务器同步订阅。</span><span class="sxs-lookup"><span data-stu-id="10fd0-110">Creating a custom application to administer or synchronize subscriptions to an Oracle publisher.</span></span>    
-   <span data-ttu-id="10fd0-111">编写同步合并订阅时执行的自定义业务规则。</span><span class="sxs-lookup"><span data-stu-id="10fd0-111">Writing customized business rules that are executed when a merge subscription is synchronized.</span></span>    
-   <span data-ttu-id="10fd0-112">生成可在配置新订阅服务器时重复运行的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本。</span><span class="sxs-lookup"><span data-stu-id="10fd0-112">Generating [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts that can be run repeated when configuring new Subscribers.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="10fd0-113">不但允许您以编程方式控制复制代理，还使您能够以编程方式管理和监视复制拓扑。</span><span class="sxs-lookup"><span data-stu-id="10fd0-113">enables you to programmatically control replication agents and to programmatically administer and monitor a replication topology.</span></span> <span data-ttu-id="10fd0-114">若要了解有关复制编程的详细信息，请参阅[复制编程概念](replication-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="10fd0-114">To learn more about programming replication, see [Replication Programming Concepts](replication-programming-concepts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10fd0-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="10fd0-115">In This Section</span></span>  
 [<span data-ttu-id="10fd0-116">复制编程概念</span><span class="sxs-lookup"><span data-stu-id="10fd0-116">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
 <span data-ttu-id="10fd0-117">介绍开发使用复制的应用程序的计划步骤。</span><span class="sxs-lookup"><span data-stu-id="10fd0-117">Describes the planning steps to develop an application that uses replication.</span></span>  
  
 [<span data-ttu-id="10fd0-118">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="10fd0-118">Replication System Stored Procedures Concepts</span></span>](replication-system-stored-procedures-concepts.md)  
 <span data-ttu-id="10fd0-119">介绍如何在复制拓扑中使用系统存储过程来提供编程访问。</span><span class="sxs-lookup"><span data-stu-id="10fd0-119">Describes how system stored procedures can be used to proivide programmatic access in a replication topology.</span></span>  
  
 [<span data-ttu-id="10fd0-120">复制管理对象概念</span><span class="sxs-lookup"><span data-stu-id="10fd0-120">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)  
 <span data-ttu-id="10fd0-121">解释使用复制管理对象 (RMO) 的相关概念。</span><span class="sxs-lookup"><span data-stu-id="10fd0-121">Explains the concepts for using Replication Management Objects (RMO).</span></span> <span data-ttu-id="10fd0-122">复制管理对象是一个封装了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的复制功能的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="10fd0-122">This is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="10fd0-123">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="10fd0-123">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)  
 <span data-ttu-id="10fd0-124">介绍如何使用复制代理可执行文件。</span><span class="sxs-lookup"><span data-stu-id="10fd0-124">Describes the use of Replication Agent Executable files.</span></span>  

  
  
