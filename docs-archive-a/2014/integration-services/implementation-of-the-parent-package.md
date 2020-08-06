---
title: 父包的实现 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parent packages [Integration Services]
ms.assetid: d8f94830-fa27-4151-88df-cbdc6bf0fc80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b99a2607e73bbcd612b43be1bdb30324a37e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578315"
---
# <a name="implementation-of-the-parent-package"></a><span data-ttu-id="42cc8-102">父包的实现</span><span class="sxs-lookup"><span data-stu-id="42cc8-102">Implementation of the Parent Package</span></span>
  <span data-ttu-id="42cc8-103">负载平衡跨越多个服务器的 SSIS 包时，如果子包已经创建并部署且用来运行子包的远程 SQL Server 代理作业也创建之后，其下一个步骤是创建父包。</span><span class="sxs-lookup"><span data-stu-id="42cc8-103">When load balancing SSIS packages across various servers, the next step after the child packages have been created, deployed, and remote SQL Server Agent Jobs created to run them, is to create the parent package.</span></span> <span data-ttu-id="42cc8-104">父包将包含很多执行 SQL Server 代理作业任务，每个任务负责调用用于运行其中一个子包的不同的 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="42cc8-104">The parent package will contain many Execute SQL Server Agent Job tasks, each task responsible for calling a different SQL Server Agent job that runs one of the child packages.</span></span> <span data-ttu-id="42cc8-105">父包中的执行 SQL Server 代理作业任务又会运行各个 SQL Server 代理作业。</span><span class="sxs-lookup"><span data-stu-id="42cc8-105">The Execute SQL Server Agent Job tasks in the parent package in turn run the various SQL Server Agent jobs.</span></span> <span data-ttu-id="42cc8-106">父包中的每个任务都包含诸如信息，例如，如何连接到远程服务器以及服务器上运行什么作业等。</span><span class="sxs-lookup"><span data-stu-id="42cc8-106">Each task in the parent package contains information such as how to connect to the remote server and what job to run on that server.</span></span> <span data-ttu-id="42cc8-107">有关详细信息，请参阅 [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md)。</span><span class="sxs-lookup"><span data-stu-id="42cc8-107">For more information, see [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md).</span></span>  
  
 <span data-ttu-id="42cc8-108">若要标识执行子包的父包，请在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的解决方案资源管理器中右键单击该包，然后单击 **“入口点包”**。</span><span class="sxs-lookup"><span data-stu-id="42cc8-108">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
## <a name="listing-child-packages"></a><span data-ttu-id="42cc8-109">列出子包</span><span class="sxs-lookup"><span data-stu-id="42cc8-109">Listing Child Packages</span></span>  
 <span data-ttu-id="42cc8-110">如果将包含父包和子包的项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器，则可以查看由父包执行的子包的列表。</span><span class="sxs-lookup"><span data-stu-id="42cc8-110">If you deploy your project that contains a parent package and child package(s) to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can view a list of the child packages that are executed by the parent package.</span></span> <span data-ttu-id="42cc8-111">运行父包时， **中将自动生成父包** “概述” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]报表。</span><span class="sxs-lookup"><span data-stu-id="42cc8-111">When you run the parent package, an **Overview** report for the parent package is automatically generated in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="42cc8-112">该报表列出了由父包中包含的执行包任务执行的子包，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="42cc8-112">The report lists the child packages that were executed by the Execute Package task contained in the parent package, as shown in the following image.</span></span>  
  
 <span data-ttu-id="42cc8-113">![包含子包列表的概述报告](media/overviewreport-childpackagelisting.png "包含子包列表的概述报告")</span><span class="sxs-lookup"><span data-stu-id="42cc8-113">![Overview Report with list of child packages](media/overviewreport-childpackagelisting.png "Overview Report with list of child packages")</span></span>  
  
 <span data-ttu-id="42cc8-114">有关访问 **“概述”** 报表的信息，请参阅 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="42cc8-114">For information about accessing the **Overview** report, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="precedence-constraints-in-the-parent-package"></a><span data-ttu-id="42cc8-115">父包中的优先约束</span><span class="sxs-lookup"><span data-stu-id="42cc8-115">Precedence Constraints in the Parent Package</span></span>  
 <span data-ttu-id="42cc8-116">在父包中的执行 SQL Server 代理作业任务之间创建优先约束时，这些优先约束只控制 SQL Server 代理作业在远程服务器上的启动时间。</span><span class="sxs-lookup"><span data-stu-id="42cc8-116">When you create precedence constraints between the Execute SQL Server Agent Job tasks in the parent package, these precedence constraints control only the time that the SQL Server Agent jobs on the remote servers are started.</span></span> <span data-ttu-id="42cc8-117">优先约束无法接收关于从 SQL Server 代理作业的步骤中运行的子包成功或失败的信息。</span><span class="sxs-lookup"><span data-stu-id="42cc8-117">Precedence constraints cannot receive information regarding the success or failure of the child packages that are run from the steps of the SQL Server Agent jobs.</span></span>  
  
 <span data-ttu-id="42cc8-118">这意味着子包的成功或失败不会传播到父包，因为父包中执行 SQL Server 代理作业的单独功能是请求 SQL Server 代理作业运行该子包。</span><span class="sxs-lookup"><span data-stu-id="42cc8-118">This means that success or failure of a child package does not propagate to the parent, because the sole function of the Execute SQL Server Agent job in the parent package is to request the SQL Server Agent job to run the child package.</span></span> <span data-ttu-id="42cc8-119">成功调用 SQL Server 代理作业之后，父包将收到<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>的结果。</span><span class="sxs-lookup"><span data-stu-id="42cc8-119">After the SQL Server Agent job is called successfully, the parent package receives a result of <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>.</span></span>  
  
 <span data-ttu-id="42cc8-120">此方案中的失败只表示调用远程 SQL Server 代理作业任务已经失败。</span><span class="sxs-lookup"><span data-stu-id="42cc8-120">Failure in this scenario means only that there has been a failure in calling the remote SQL Server Agent Job task.</span></span> <span data-ttu-id="42cc8-121">可以发生该情况的一种情形是远程服务器已关闭且代理未响应。</span><span class="sxs-lookup"><span data-stu-id="42cc8-121">One situation where this can occur is when the remote server is down and the agent does not respond.</span></span> <span data-ttu-id="42cc8-122">但是，只要代理激发，父包就会成功完成其任务。</span><span class="sxs-lookup"><span data-stu-id="42cc8-122">However, as long as the agent fires, the parent package has successfully completed its task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42cc8-123">可以使用包含 **sp_start_job N'package_name'** 的 Transact-SQL 语句的执行 SQL 任务。</span><span class="sxs-lookup"><span data-stu-id="42cc8-123">You can use an Execute SQL Task that contains a Transact-SQL statement of **sp_start_job N'package_name'**.</span></span> <span data-ttu-id="42cc8-124">有关详细信息，请参阅 [sp_start_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42cc8-124">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="debugging-environment"></a><span data-ttu-id="42cc8-125">调试环境</span><span class="sxs-lookup"><span data-stu-id="42cc8-125">Debugging Environment</span></span>  
 <span data-ttu-id="42cc8-126">测试父包时，请在设计器的调试环境中通过使用“调试”/“启动调试”(F5) 来运行父包。</span><span class="sxs-lookup"><span data-stu-id="42cc8-126">When testing the parent package, use the debugging environment of the designer by running it using Debug / Start Debugging (F5).</span></span> <span data-ttu-id="42cc8-127">另外，还可以使用命令提示符实用工具 **dtexec**。</span><span class="sxs-lookup"><span data-stu-id="42cc8-127">Alternatively, you can use the command prompt utility, **dtexec**.</span></span> <span data-ttu-id="42cc8-128">有关详细信息，请参阅 [dtexec Utility](packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="42cc8-128">For more information, see [dtexec Utility](packages/dtexec-utility.md).</span></span>  
  
  
