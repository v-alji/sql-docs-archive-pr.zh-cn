---
title: 调试业务逻辑处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b255407783b1e52a376e562ec910f8b123e42c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578134"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a><span data-ttu-id="da05d-102">调试业务逻辑处理程序（复制编程）</span><span class="sxs-lookup"><span data-stu-id="da05d-102">Debug a Business Logic Handler (Replication Programming)</span></span>
  <span data-ttu-id="da05d-103">在同步合并订阅时，可以使用业务逻辑处理程序调用自定义业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="da05d-103">Use a business logic handler to invoke custom business logic when a merge subscription is synchronized.</span></span> <span data-ttu-id="da05d-104">有关详细信息，请参阅[合并同步期间执行业务逻辑](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="da05d-104">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="da05d-105">合并复制协调器 (replrec.dll) 调用包含业务逻辑的托管代码程序集。</span><span class="sxs-lookup"><span data-stu-id="da05d-105">The Merge Replication Reconciler (replrec.dll) calls the managed code assembly containing the business logic.</span></span> <span data-ttu-id="da05d-106">在大多数情况下，replrec.dll 和自定义业务逻辑是在运行合并代理的计算机上执行的（对于请求订阅，在订阅服务器上执行；对于推送订阅，在分发服务器上执行）。</span><span class="sxs-lookup"><span data-stu-id="da05d-106">In most cases, replrec.dll and the custom business logic is executed on the computer where the Merge Agent runs (at the Subscriber for a pull subscription or at the Distributor for a push subscription).</span></span> <span data-ttu-id="da05d-107">在 Web 同步或 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 订阅服务器的情况下，协调器和自定义业务逻辑在 Web 服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="da05d-107">In the case of Web synchronization, or in the case of a [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscriber, the reconciler and the custom business logic is executed on the Web server.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a><span data-ttu-id="da05d-108">在本地计算机上调试业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="da05d-108">To debug a business logic handler on a local computer</span></span>  
  
1.  <span data-ttu-id="da05d-109">配置发布和分发，创建一个发布，然后创建该发布的一个订阅。</span><span class="sxs-lookup"><span data-stu-id="da05d-109">Configure publishing and distribution, create a publication, and create a subscription to the publication.</span></span> <span data-ttu-id="da05d-110">有关详细信息，请参阅[配置发布和分发](configure-publishing-and-distribution.md)和[创建发布](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="da05d-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [Create a Publication](publish/create-a-publication.md).</span></span>  
  
2.  <span data-ttu-id="da05d-111">创建和注册业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="da05d-111">Create and register a business logic handler.</span></span> <span data-ttu-id="da05d-112">有关详细信息，请参阅 [为合并项目实现业务逻辑处理程序](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="da05d-112">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="da05d-113">在以编程的方式同步启动合并代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 中创建一个复制管理对象 (RMO) 项目。</span><span class="sxs-lookup"><span data-stu-id="da05d-113">Create a Replication Management Objects (RMO) project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio that programmatically starts the Merge Agent synchronously.</span></span> <span data-ttu-id="da05d-114">有关详细信息，请参阅 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="da05d-114">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
4.  <span data-ttu-id="da05d-115">在业务逻辑处理程序代码中，于正在调试的方法中或类构造函数中设置一个断点。</span><span class="sxs-lookup"><span data-stu-id="da05d-115">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="da05d-116">有关可在业务逻辑处理程序中实现的方法的详细信息，请参阅 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 方法主题。</span><span class="sxs-lookup"><span data-stu-id="da05d-116">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
5.  <span data-ttu-id="da05d-117">在调试模式下生成业务逻辑处理程序，并将程序集和调试符号文件 (.pdb) 部署在步骤 1 中注册的位置。</span><span class="sxs-lookup"><span data-stu-id="da05d-117">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="da05d-118">若要简化调试，请创建一个同时包含业务逻辑处理程序项目和同步订阅的项目的 Visual Studio .NET 解决方案。</span><span class="sxs-lookup"><span data-stu-id="da05d-118">To simplify debugging, create a single Visual Studio .NET solution that contains both the business logic handler project and the project that synchronizes the subscription.</span></span> <span data-ttu-id="da05d-119">在这种情况下，请将同步项目设置为启动项目，并将生成环境配置为在调试过程中将业务逻辑程序集部署到步骤 1 中注册的位置。</span><span class="sxs-lookup"><span data-stu-id="da05d-119">In this case, set the synchronization project as the startup project, and configure the build environment to deploy the business logic assembly to the location registered in step 1 during debugging.</span></span>  
  
6.  <span data-ttu-id="da05d-120">对订阅数据库或发布数据库执行插入、更新或删除命令。</span><span class="sxs-lookup"><span data-stu-id="da05d-120">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="da05d-121">命令和执行位置取决于正在调试的方法。</span><span class="sxs-lookup"><span data-stu-id="da05d-121">The command and execution location depends on the method being debugged.</span></span>  
  
7.  <span data-ttu-id="da05d-122">在调试模式下启动步骤 3 中的项目以同步订阅。</span><span class="sxs-lookup"><span data-stu-id="da05d-122">Start the project from step 3 in debug mode to synchronize the subscription.</span></span>  
  
8.  <span data-ttu-id="da05d-123">假定未设置任何其他断点且复制了正确的命令，则执行将在到达业务逻辑处理程序中的断点时停止。</span><span class="sxs-lookup"><span data-stu-id="da05d-123">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a><span data-ttu-id="da05d-124">在 Web 服务器上使用 Web 同步或为 SQL Server Compact 订阅服务器调试业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="da05d-124">To debug a business logic handler on a Web server using Web synchronization, or for a SQL Server Compact Subscriber</span></span>  
  
1.  <span data-ttu-id="da05d-125">配置发布和分发，创建一个发布，然后创该发布的建一个请求订阅。</span><span class="sxs-lookup"><span data-stu-id="da05d-125">Configure publishing and distribution, create a publication, and create a pull subscription to the publication.</span></span> <span data-ttu-id="da05d-126">该发布必须支持 Web 同步或 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="da05d-126">The publication must support Web synchronization or [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
2.  <span data-ttu-id="da05d-127">创建和注册业务逻辑处理程序。</span><span class="sxs-lookup"><span data-stu-id="da05d-127">Create and register a business logic handler.</span></span> <span data-ttu-id="da05d-128">有关详细信息，请参阅 [为合并项目实现业务逻辑处理程序](implement-a-business-logic-handler-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="da05d-128">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="da05d-129">在业务逻辑处理程序代码中，于正在调试的方法中或类构造函数中设置一个断点。</span><span class="sxs-lookup"><span data-stu-id="da05d-129">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="da05d-130">有关可在业务逻辑处理程序中实现的方法的详细信息，请参阅 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> 方法主题。</span><span class="sxs-lookup"><span data-stu-id="da05d-130">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
4.  <span data-ttu-id="da05d-131">在调试模式下生成业务逻辑处理程序，并将程序集和调试符号文件 (.pdb) 部署在 Web 服务器上步骤 1 中注册的位置。</span><span class="sxs-lookup"><span data-stu-id="da05d-131">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) at the Web server in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="da05d-132">如果由于程序集正在使用而无法生成业务逻辑处理程序，则在 Web 服务器上，在命令提示符处键入命令 `iisreset` 以重置 Web 服务器。</span><span class="sxs-lookup"><span data-stu-id="da05d-132">If the business logic handler fails to build because the assembly is in use, type the command `iisreset` on the Web server at the command prompt to reset the Web server.</span></span>  
  
5.  <span data-ttu-id="da05d-133">在启用 Web 同步的情况下同步订阅。</span><span class="sxs-lookup"><span data-stu-id="da05d-133">Synchronize the subscription with Web synchronization enabled.</span></span> <span data-ttu-id="da05d-134">同步期间，Web 服务器将加载注册的程序集。</span><span class="sxs-lookup"><span data-stu-id="da05d-134">During synchronization, the Web server loads the registered assembly.</span></span>  
  
6.  <span data-ttu-id="da05d-135">使用 Visual Studio .NET 调试器，在 Web 服务器上附加到下列进程之一：</span><span class="sxs-lookup"><span data-stu-id="da05d-135">Using the Visual Studio .NET debugger, attach to the one of the following processes on the Web server:</span></span>  
  
    -   <span data-ttu-id="da05d-136">w3wp.exe - Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="da05d-136">w3wp.exe - Windows Server 2003.</span></span>  
  
    -   <span data-ttu-id="da05d-137">inetinfo.exe - Windows 2000 和 Windows XP。</span><span class="sxs-lookup"><span data-stu-id="da05d-137">inetinfo.exe - Windows 2000 and Windows XP.</span></span>  
  
7.  <span data-ttu-id="da05d-138">在 **“输出”** 窗口中，检查调试输出以验证注册程序集的符号是否正确加载。</span><span class="sxs-lookup"><span data-stu-id="da05d-138">In the **Output** window, check the debug output to verify that the symbols for the registered assembly loaded properly.</span></span> <span data-ttu-id="da05d-139">如果未加载符号，请确保在步骤 4 中复制了正确的 .pdb 文件，然后重复步骤 5。</span><span class="sxs-lookup"><span data-stu-id="da05d-139">If the symbols were not loaded, ensure that the correct .pdb file was copied in step 4, and repeat step 5.</span></span>  
  
8.  <span data-ttu-id="da05d-140">对订阅数据库或发布数据库执行插入、更新或删除命令。</span><span class="sxs-lookup"><span data-stu-id="da05d-140">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="da05d-141">命令和执行位置取决于正在调试的方法。</span><span class="sxs-lookup"><span data-stu-id="da05d-141">The command and execution location depends on the method being debugged.</span></span>  
  
9. <span data-ttu-id="da05d-142">使用 Visual Studio 调试器，附加到 w3wp.exe 进程。</span><span class="sxs-lookup"><span data-stu-id="da05d-142">Using the Visual Studio debugger, attach to the w3wp.exe process.</span></span>  
  
10. <span data-ttu-id="da05d-143">使用 Web 同步再次同步订阅。</span><span class="sxs-lookup"><span data-stu-id="da05d-143">Synchronize the subscription again, using Web synchronization.</span></span>  
  
11. <span data-ttu-id="da05d-144">假定未设置任何其他断点且复制了正确的命令，则执行将在到达业务逻辑处理程序中的断点时停止。</span><span class="sxs-lookup"><span data-stu-id="da05d-144">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da05d-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da05d-145">See Also</span></span>  
 [<span data-ttu-id="da05d-146">为合并项目实现业务逻辑处理程序</span><span class="sxs-lookup"><span data-stu-id="da05d-146">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
