---
title: 查看和停止在 Integration Services 服务器上运行的包 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e63839d4ab5d8d50f7d86eea05c8d58107d6799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590266"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a><span data-ttu-id="aefe8-102">查看和停止在 Integration Services 服务器上运行的包</span><span class="sxs-lookup"><span data-stu-id="aefe8-102">Viewing and Stopping Packages Running on the Integration Services Server</span></span>
  <span data-ttu-id="aefe8-103">`SSISDB` 数据库在对用户不可见的内部表中存储执行历史记录。</span><span class="sxs-lookup"><span data-stu-id="aefe8-103">The `SSISDB` database stores execution history in internal tables that are not visible to users.</span></span> <span data-ttu-id="aefe8-104">不过，它通过您可以查询的公共视图公开您所需的信息。</span><span class="sxs-lookup"><span data-stu-id="aefe8-104">However it exposes the information that you need through public views that you can query.</span></span> <span data-ttu-id="aefe8-105">它还提供存储过程，您可以调用这些存储过程以执行与包相关的常见任务。</span><span class="sxs-lookup"><span data-stu-id="aefe8-105">It also provides stored procedures that you can call to perform common tasks related to packages.</span></span>  
  
 <span data-ttu-id="aefe8-106">通常，您在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的服务器上管理 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]对象。</span><span class="sxs-lookup"><span data-stu-id="aefe8-106">Typically you manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects on the server in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="aefe8-107">不过，您还可以查询数据库视图和直接调用存储过程，或者编写调用托管 API 的自定义代码。</span><span class="sxs-lookup"><span data-stu-id="aefe8-107">However you can also query the database views and call the stored procedures directly, or write custom code that calls the managed API.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="aefe8-108">和托管 API 查询视图并调用存储过程以便执行其许多任务。</span><span class="sxs-lookup"><span data-stu-id="aefe8-108">and the managed API query the views and call the stored procedures to perform many of their tasks.</span></span> <span data-ttu-id="aefe8-109">例如，您可以查看当前正在服务器上运行的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的列表，并且在需要时请求包停止运行。</span><span class="sxs-lookup"><span data-stu-id="aefe8-109">For example, you can view the list of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that are currently running on the server, and request packages to stop if you have to.</span></span>  
  
## <a name="viewing-the-list-of-running-packages"></a><span data-ttu-id="aefe8-110">查看正在运行的包的列表</span><span class="sxs-lookup"><span data-stu-id="aefe8-110">Viewing the List of Running Packages</span></span>  
 <span data-ttu-id="aefe8-111">您可以在 **“活动操作”** 对话框中查看当前正在服务器上运行的包的列表。</span><span class="sxs-lookup"><span data-stu-id="aefe8-111">You can view the list of packages that are currently running on the server in the **Active Operations** dialog box.</span></span> <span data-ttu-id="aefe8-112">有关详细信息，请参阅 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-112">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="aefe8-113">有关可用于查看正在运行的包列表的其他方法的信息，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="aefe8-113">For information about the other methods that you can use to view the list of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="aefe8-114">access</span><span class="sxs-lookup"><span data-stu-id="aefe8-114">access</span></span>  
 <span data-ttu-id="aefe8-115">若要查看正在服务器上运行的包的列表，请为其状态为 2 的包查询视图 [catalog.executions（SSISDB 数据库）](/sql/integration-services/system-views/catalog-executions-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-115">To view the list of packages that are running on the server, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) for packages that have a status of 2.</span></span>  
  
 <span data-ttu-id="aefe8-116">通过托管 API 以编程方式访问</span><span class="sxs-lookup"><span data-stu-id="aefe8-116">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="aefe8-117">请参阅 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空间及其类。</span><span class="sxs-lookup"><span data-stu-id="aefe8-117">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="stopping-a-running-package"></a><span data-ttu-id="aefe8-118">停止正在运行的包</span><span class="sxs-lookup"><span data-stu-id="aefe8-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="aefe8-119">您可以在 **“活动操作”** 对话框中请求正在运行的包停止。</span><span class="sxs-lookup"><span data-stu-id="aefe8-119">You can request a running package to stop in the **Active Operations** dialog box.</span></span> <span data-ttu-id="aefe8-120">有关详细信息，请参阅 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-120">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="aefe8-121">有关可用于停止正在运行的包的其他方法的信息，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="aefe8-121">For information about the other methods that you can use to stop a running package, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="aefe8-122">access</span><span class="sxs-lookup"><span data-stu-id="aefe8-122">access</span></span>  
 <span data-ttu-id="aefe8-123">若要停止正在服务器上运行的包，请调用存储过程 [catalog.stop_operation（SSISDB 数据库）](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-123">To stop a package that is running on the server, call the stored procedure, [catalog.stop_operation &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).</span></span>  
  
 <span data-ttu-id="aefe8-124">通过托管 API 以编程方式访问</span><span class="sxs-lookup"><span data-stu-id="aefe8-124">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="aefe8-125">请参阅 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空间及其类。</span><span class="sxs-lookup"><span data-stu-id="aefe8-125">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a><span data-ttu-id="aefe8-126">查看已运行的包的历史记录</span><span class="sxs-lookup"><span data-stu-id="aefe8-126">Viewing the History of Packages That Have Run</span></span>  
 <span data-ttu-id="aefe8-127">若要查看在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中已运行的包的历史记录，请使用 **“全部执行”** 报表。</span><span class="sxs-lookup"><span data-stu-id="aefe8-127">To view the history of packages that have run in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], use the **All Executions** report.</span></span> <span data-ttu-id="aefe8-128">有关“全部执行”  报表和其他标准报表的详细信息，请参阅 [Integration Services 服务器的报告](../../2014/integration-services/reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-128">For more information on the **All Executions** report and other standard reports, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="aefe8-129">有关可用于查看正在运行的包的历史记录的其他方法的信息，请参阅以下主题。</span><span class="sxs-lookup"><span data-stu-id="aefe8-129">For information about the other methods that you can use to view the history of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="aefe8-130">access</span><span class="sxs-lookup"><span data-stu-id="aefe8-130">access</span></span>  
 <span data-ttu-id="aefe8-131">若要查看与已运行的包有关的信息，请查询视图 [catalog.executions（SSISDB 数据库）](/sql/integration-services/system-views/catalog-executions-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="aefe8-131">To view information about packages that have run, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).</span></span>  
  
 <span data-ttu-id="aefe8-132">通过托管 API 以编程方式访问</span><span class="sxs-lookup"><span data-stu-id="aefe8-132">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="aefe8-133">请参阅 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空间及其类。</span><span class="sxs-lookup"><span data-stu-id="aefe8-133">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefe8-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aefe8-134">See Also</span></span>  
 <span data-ttu-id="aefe8-135">[项目和包的执行](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="aefe8-135">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="aefe8-136">包执行的疑难解答报告</span><span class="sxs-lookup"><span data-stu-id="aefe8-136">Troubleshooting Reports for Package Execution</span></span>](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
