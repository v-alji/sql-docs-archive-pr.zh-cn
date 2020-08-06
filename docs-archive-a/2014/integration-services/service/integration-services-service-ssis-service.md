---
title: Integration Services 服务（SSIS 服务）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b24f0f0d54009c50654904d606a208504f229c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694033"
---
# <a name="integration-services-service-ssis-service"></a><span data-ttu-id="a29a8-102">Integration Services 服务（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="a29a8-102">Integration Services Service (SSIS Service)</span></span>
  <span data-ttu-id="a29a8-103">本节中的主题论述 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="a29a8-103">The topics in this section discuss the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="a29a8-104">此服务不是创建、保存和运行集成服务包所必需的。</span><span class="sxs-lookup"><span data-stu-id="a29a8-104">This service is not required to create, save, and run Integration Services packages.</span></span> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="a29a8-105">支持 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务以便与 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="a29a8-105">supports the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a29a8-106">从开始 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将对象、设置和操作数据存储在 `SSISDB` [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用项目部署模型部署到服务器的项目的数据库中。</span><span class="sxs-lookup"><span data-stu-id="a29a8-106">Starting in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores objects, settings, and operational data in the `SSISDB` database for projects that you've deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model.</span></span> <span data-ttu-id="a29a8-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库引擎的实例，它承载该数据库。</span><span class="sxs-lookup"><span data-stu-id="a29a8-107">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, which is an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine, hosts the database.</span></span> <span data-ttu-id="a29a8-108">有关数据库的详细信息，请参阅 [SSIS 目录](../catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="a29a8-108">For more information about the database, see [SSIS Catalog](../catalog/ssis-catalog.md).</span></span> <span data-ttu-id="a29a8-109">有关将项目部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器的详细信息，请参阅 [将项目部署到 Integration Services 服务器](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a29a8-109">For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
## <a name="management-capabilities"></a><span data-ttu-id="a29a8-110">管理功能</span><span class="sxs-lookup"><span data-stu-id="a29a8-110">Management Capabilities</span></span>  
 <span data-ttu-id="a29a8-111">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务是用于管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="a29a8-111">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="a29a8-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务只在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中可用。</span><span class="sxs-lookup"><span data-stu-id="a29a8-112">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a29a8-113">运行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务可以提供下列管理功能：</span><span class="sxs-lookup"><span data-stu-id="a29a8-113">Running the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service provides the following management capabilities:</span></span>  
  
-   <span data-ttu-id="a29a8-114">启动远程和本地存储的包</span><span class="sxs-lookup"><span data-stu-id="a29a8-114">Starting remote and locally stored packages</span></span>  
  
-   <span data-ttu-id="a29a8-115">停止远程和本地运行的包</span><span class="sxs-lookup"><span data-stu-id="a29a8-115">Stopping remote and locally running packages</span></span>  
  
-   <span data-ttu-id="a29a8-116">监视远程和本地运行的包</span><span class="sxs-lookup"><span data-stu-id="a29a8-116">Monitoring remote and locally running packages</span></span>  
  
-   <span data-ttu-id="a29a8-117">导入和导出包</span><span class="sxs-lookup"><span data-stu-id="a29a8-117">Importing and exporting packages</span></span>  
  
-   <span data-ttu-id="a29a8-118">管理包存储</span><span class="sxs-lookup"><span data-stu-id="a29a8-118">Managing package storage</span></span>  
  
-   <span data-ttu-id="a29a8-119">自定义存储文件夹</span><span class="sxs-lookup"><span data-stu-id="a29a8-119">Customizing storage folders</span></span>  
  
-   <span data-ttu-id="a29a8-120">在服务停止时停止正在运行的包</span><span class="sxs-lookup"><span data-stu-id="a29a8-120">Stopping running packages when the service is stopped</span></span>  
  
-   <span data-ttu-id="a29a8-121">查看 Windows 事件日志</span><span class="sxs-lookup"><span data-stu-id="a29a8-121">Viewing the Windows Event log</span></span>  
  
-   <span data-ttu-id="a29a8-122">连接到多台 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器</span><span class="sxs-lookup"><span data-stu-id="a29a8-122">Connecting to multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servers</span></span>  
  
## <a name="startup-type-for-integration-services-service"></a><span data-ttu-id="a29a8-123">用于集成服务服务的启动类型</span><span class="sxs-lookup"><span data-stu-id="a29a8-123">Startup Type for Integration Services Service</span></span>  
 <span data-ttu-id="a29a8-124">在安装 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件时会安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服务。</span><span class="sxs-lookup"><span data-stu-id="a29a8-124">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is installed when you install the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a29a8-125">默认情况下， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务已启动，该服务的启动类型已设置为自动。</span><span class="sxs-lookup"><span data-stu-id="a29a8-125">By default, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span> <span data-ttu-id="a29a8-126">该服务必须运行，才能监视存储在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区中的包。</span><span class="sxs-lookup"><span data-stu-id="a29a8-126">The service must be running to monitor the packages that are stored in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span> <span data-ttu-id="a29a8-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 包存储区可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例中的 msdb 数据库，也可以是文件系统中指定的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a29a8-127">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store can be either the msdb database in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the designated folders in the file system.</span></span>  
  
 <span data-ttu-id="a29a8-128">如果只希望设计和执行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，则 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务不是必需的。</span><span class="sxs-lookup"><span data-stu-id="a29a8-128">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not required if you only want to design and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="a29a8-129">但是，若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]列出和监视包，则该服务是必需的。</span><span class="sxs-lookup"><span data-stu-id="a29a8-129">However, the service is required to list and monitor packages using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a29a8-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a29a8-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a29a8-131">设置 Integration Services 服务的属性</span><span class="sxs-lookup"><span data-stu-id="a29a8-131">Set the Properties of the Integration Services Service</span></span>](../set-the-properties-of-the-integration-services-service.md)  
  
-   [<span data-ttu-id="a29a8-132">查看 Integration Services 服务的事件</span><span class="sxs-lookup"><span data-stu-id="a29a8-132">View Events for the Integration Services Service</span></span>](../view-events-for-the-integration-services-service.md)  
  
  
