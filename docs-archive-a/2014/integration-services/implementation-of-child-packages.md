---
title: 子包的实现 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4fa4fa7c523c55c595341c7aee6a530c5918a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688995"
---
# <a name="implementation-of-child-packages"></a><span data-ttu-id="c66e3-102">子包的实现</span><span class="sxs-lookup"><span data-stu-id="c66e3-102">Implementation of Child Packages</span></span>
  <span data-ttu-id="c66e3-103">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]来实现负载平衡时，子包将安装在其他服务器上，以利用可用的 CPU 或服务器时间。</span><span class="sxs-lookup"><span data-stu-id="c66e3-103">When you implement load balancing using [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], child packages are installed on other servers to take advantage of the available CPU or server time.</span></span> <span data-ttu-id="c66e3-104">若要创建和运行子包，需要执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c66e3-104">To create and run the child packages requires the following steps:</span></span>  
  
-   <span data-ttu-id="c66e3-105">设计子包。</span><span class="sxs-lookup"><span data-stu-id="c66e3-105">Designing the child packages.</span></span>  
  
-   <span data-ttu-id="c66e3-106">将包移动到远程服务器。</span><span class="sxs-lookup"><span data-stu-id="c66e3-106">Moving the packages to the remote server.</span></span>  
  
-   <span data-ttu-id="c66e3-107">在包含运行子包步骤的远程服务器上创建 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="c66e3-107">Creating a SQL Server Agent Job on the remote server that contains a step that runs the child package.</span></span>  
  
-   <span data-ttu-id="c66e3-108">测试并调试 SQL Server 代理作业和子包。</span><span class="sxs-lookup"><span data-stu-id="c66e3-108">Testing and debugging the SQL Server Agent Job and child packages.</span></span>  
  
 <span data-ttu-id="c66e3-109">设计子包时，包的设计不受限制，并且可以添加任何希望的功能。</span><span class="sxs-lookup"><span data-stu-id="c66e3-109">When you design the child packages, the packages have no limitations in their design, and you can put in any functionality you desire.</span></span> <span data-ttu-id="c66e3-110">但是，如果包要访问数据，则必须确保运行包的服务器能够访问该数据。</span><span class="sxs-lookup"><span data-stu-id="c66e3-110">However, if the package accesses data, you must ensure that the server that runs the package has access to the data.</span></span>  
  
 <span data-ttu-id="c66e3-111">若要标识执行子包的父包，请在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的解决方案资源管理器中右键单击该包，然后单击 **“入口点包”**。</span><span class="sxs-lookup"><span data-stu-id="c66e3-111">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="c66e3-112">设计完子包之后，下一个步骤是将它们部署在远程服务器上。</span><span class="sxs-lookup"><span data-stu-id="c66e3-112">After the child packages have been designed, the next step is to deploy them on the remote servers.</span></span>  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a><span data-ttu-id="c66e3-113">将子包移动到远程实例</span><span class="sxs-lookup"><span data-stu-id="c66e3-113">Moving the Child Package to the Remote Instance</span></span>  
 <span data-ttu-id="c66e3-114">将包移动到其他服务器的方式有多个。</span><span class="sxs-lookup"><span data-stu-id="c66e3-114">There are multiple ways to move packages to other servers.</span></span> <span data-ttu-id="c66e3-115">两个推荐的方法是：</span><span class="sxs-lookup"><span data-stu-id="c66e3-115">The two suggested methods are:</span></span>  
  
-   <span data-ttu-id="c66e3-116">通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]将包导出。</span><span class="sxs-lookup"><span data-stu-id="c66e3-116">Exporting packages by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="c66e3-117">先为包含要部署的包的项目生成部署实用工具，然后运行包安装向导将包安装到文件系统或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例，从而达到部署包的目的。</span><span class="sxs-lookup"><span data-stu-id="c66e3-117">Deploying packages by building a deployment utility for the project that contains the packages you want to deploy, and then running the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c66e3-118">有关详细信息，请参阅[包部署 &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="c66e3-118">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="c66e3-119">必须重复部署到希望使用的每个远程服务器。</span><span class="sxs-lookup"><span data-stu-id="c66e3-119">You must repeat the deployment to each remote server you want to use.</span></span>  
  
## <a name="creating-the-sql-server-agent-jobs"></a><span data-ttu-id="c66e3-120">创建 SQL Server 代理作业</span><span class="sxs-lookup"><span data-stu-id="c66e3-120">Creating the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="c66e3-121">子包已经部署到多个服务器之后，请在包含子包的每个服务器上创建 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="c66e3-121">After the child packages have been deployed to the various servers, create a SQL Server Agent job on each server that contains a child package.</span></span> <span data-ttu-id="c66e3-122">SQL Server 代理作业包含调用作业代理时运行子包的步骤。</span><span class="sxs-lookup"><span data-stu-id="c66e3-122">The SQL Server Agent job contains a step that runs the child package when the job agent is called.</span></span> <span data-ttu-id="c66e3-123">SQL Server 代理作业不是已调度作业；它们只在父包调用它们时才会运行子包。</span><span class="sxs-lookup"><span data-stu-id="c66e3-123">The SQL Server Agent jobs are not scheduled jobs; they run the child packages only when they are called by the parent package.</span></span> <span data-ttu-id="c66e3-124">返回到父包的作业成功或失败的通知反映 SQL Server 代理作业成功或失败，以及是否成功调用了代理作业，而不是反映子包的成功或失败或它是否已执行。</span><span class="sxs-lookup"><span data-stu-id="c66e3-124">Notification of success or failure of the job back to the parent package reflects the success or failure of the SQL Server Agent job and whether it was called successfully, not the success or failure of the child package or whether it was executed.</span></span>  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a><span data-ttu-id="c66e3-125">调试 SQL Server 代理作业和子包</span><span class="sxs-lookup"><span data-stu-id="c66e3-125">Debugging the SQL Server Agent Jobs and Child Packages</span></span>  
 <span data-ttu-id="c66e3-126">通过使用下列方法之一，可以测试 SQL Server 代理作业及其子包：</span><span class="sxs-lookup"><span data-stu-id="c66e3-126">You can test the SQL Server Agent jobs and their child packages by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="c66e3-127">在 SSIS 设计器中运行每个子包，方法是单击 "**调试**开始" （  /  **不调试**）。</span><span class="sxs-lookup"><span data-stu-id="c66e3-127">Running each child package in SSIS Designer, by clicking **Debug** / **Start Without Debugging**.</span></span>  
  
-   <span data-ttu-id="c66e3-128">通过使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]在远程计算机上运行单个 SQL Server 代理作业，以确保包运行。</span><span class="sxs-lookup"><span data-stu-id="c66e3-128">Running the individual SQL Server Agent job on the remote computer by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to make sure that the package runs.</span></span>  
  
 <span data-ttu-id="c66e3-129">有关如何对从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理作业运行的包进行故障排除的信息，请参阅 [支持知识库中的](https://support.microsoft.com/kb/918760) An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step [!INCLUDE[msCoName](../includes/msconame-md.md)] （从 SQL Server 代理作业步骤调用 SSIS 包时 SSIS 包不运行）。</span><span class="sxs-lookup"><span data-stu-id="c66e3-129">For information about how to troubleshoot packages that you run from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs, see [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760) in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Support Knowledge Base.</span></span>  
  
 <span data-ttu-id="c66e3-130">SQL Server 代理检查代理的子系统访问权，并在每次运行作业步骤时将访问权授予代理。</span><span class="sxs-lookup"><span data-stu-id="c66e3-130">The SQL Server Agent checks subsystem access for a proxy and gives access to the proxy every time the job step runs.</span></span>  
  
 <span data-ttu-id="c66e3-131">可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中创建代理。</span><span class="sxs-lookup"><span data-stu-id="c66e3-131">You can create a proxy in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c66e3-132">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c66e3-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c66e3-133">使用 SQL Server Management Studio 在 SSIS 服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="c66e3-133">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="c66e3-134">相关内容</span><span class="sxs-lookup"><span data-stu-id="c66e3-134">Related Content</span></span>  
  
-   <span data-ttu-id="c66e3-135">Andyleonard 上的博客文章[SSIS：访问父包中的变量](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="c66e3-135">Blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), on andyleonard.blog.</span></span>  
  
-   <span data-ttu-id="c66e3-136">文章：[执行包任务](../integration-services/control-flow/execute-package-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c66e3-136">Article, [Execute Package Task](../integration-services/control-flow/execute-package-task.md).</span></span>  
  
  
