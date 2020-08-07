---
title: Integration Services (SSIS) 服务器 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0da83cdac269499dfbde7a6387a4af4690c83ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587983"
---
# <a name="integration-services-ssis-server"></a><span data-ttu-id="f1f5b-102">Integration Services (SSIS) 服务器</span><span class="sxs-lookup"><span data-stu-id="f1f5b-102">Integration Services (SSIS) Server</span></span>
  <span data-ttu-id="f1f5b-103">当您在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中设计和测试包后，可将包含包的项目部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="f1f5b-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器是承载 `SSISDB` 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-104">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database.</span></span> <span data-ttu-id="f1f5b-105">该数据库存储以下对象：包、项目、参数、权限、服务器属性和操作历史记录。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-105">The database stores the following objects: packages, projects, parameters, permissions, server properties, and operational history.</span></span>  
  
 <span data-ttu-id="f1f5b-106">`SSISDB` 数据库在您可以查询的公共视图中公开对象信息。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-106">The `SSISDB` database exposes the object information in public views that you can query.</span></span> <span data-ttu-id="f1f5b-107">数据库还提供存储过程，您可以调用这些存储过程以管理该对象。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-107">The database also provides stored procedures that you can call to manage the objects.</span></span>  
  
 <span data-ttu-id="f1f5b-108">在您可以将项目部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器之前，需要创建 `SSISDB` 目录。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-108">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you need to create the `SSISDB` catalog.</span></span>  
  
 <span data-ttu-id="f1f5b-109">若要大致了解 SSISDB 目录功能，请参阅 [SSIS 目录](ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-109">For an overview of the SSISDB catalog functionality, see [SSIS Catalog](ssis-catalog.md).</span></span>  
  
## <a name="high-availability"></a><span data-ttu-id="f1f5b-110">高可用性</span><span class="sxs-lookup"><span data-stu-id="f1f5b-110">High Availability</span></span>  
 <span data-ttu-id="f1f5b-111">像其他用户数据库一样，`SSISDB` 数据库不支持数据库镜像和复制。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-111">Like other user databases, the `SSISDB` database does support database mirroring and replication.</span></span> <span data-ttu-id="f1f5b-112">若要详细了解镜像和复制，请参阅[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-112">For more information about mirroring and replication, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="f1f5b-113">还可以通过利用 SSIS 和 AlwaysOn 可用性组，提供 SSISDB 及其内容的高可用性。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-113">You can also provide high-availability of SSISDB and its contents by making use of SSIS and AlwaysOn Availability Groups.</span></span> <span data-ttu-id="f1f5b-114">有关详细信息，请参阅 blogs.msdn.com 上 Matt Masson 的博客文章 [SSIS 与 AlwaysOn 一起使用](https://go.microsoft.com/fwlink/?LinkId=255873)。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-114">For more information, see this blog post by Matt Masson, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
##  <a name="integration-services-server-in-sql-server-management-studio"></a><a name="ssms"></a><span data-ttu-id="f1f5b-115">SQL Server Management Studio 中的 Integration Services 服务器</span><span class="sxs-lookup"><span data-stu-id="f1f5b-115">Integration Services Server in SQL Server Management Studio</span></span>  
 <span data-ttu-id="f1f5b-116">在您连接到承载 `SSISDB` 数据库的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例时，您将在对象资源管理器中看到下列对象：</span><span class="sxs-lookup"><span data-stu-id="f1f5b-116">When you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database, you see the following objects in Object Explorer:</span></span>  
  
-   <span data-ttu-id="f1f5b-117">**SSISDB 数据库**</span><span class="sxs-lookup"><span data-stu-id="f1f5b-117">**SSISDB Database**</span></span>  
  
     <span data-ttu-id="f1f5b-118">该 `SSISDB` 数据库显示在对象浏览器中的 "**数据库**" 节点下。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-118">The `SSISDB` database appears under the **Databases** node in Object Explore.</span></span> <span data-ttu-id="f1f5b-119">您可以查询视图和调用存储过程，这些存储过程既管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器，也管理在该服务器上存储的对象。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-119">You can query the views and call the stored procedures that manage the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server and the objects that are stored on the server.</span></span>  
  
-   <span data-ttu-id="f1f5b-120">**Integration Services 目录**</span><span class="sxs-lookup"><span data-stu-id="f1f5b-120">**Integration Services Catalogs**</span></span>  
  
     <span data-ttu-id="f1f5b-121">在 **“Integration Services 目录”** 节点下，有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目和环境的文件夹。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-121">Under the **Integration Services Catalogs** node there are folders for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects and environments.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f1f5b-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f1f5b-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f1f5b-123">创建 SSIS 目录</span><span class="sxs-lookup"><span data-stu-id="f1f5b-123">Create the SSIS Catalog</span></span>](../create-the-ssis-catalog.md)  
  
-   [<span data-ttu-id="f1f5b-124">查看 Integration Services 服务器上的包列表</span><span class="sxs-lookup"><span data-stu-id="f1f5b-124">View the List of Packages on the Integration Services Server</span></span>](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [<span data-ttu-id="f1f5b-125">Deploy Projects to Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="f1f5b-125">Deploy Projects to Integration Services Server</span></span>](../deploy-projects-to-integration-services-server.md)  
  
-   [<span data-ttu-id="f1f5b-126">使用 SQL Server Management Studio 在 SSIS 服务器上运行包</span><span class="sxs-lookup"><span data-stu-id="f1f5b-126">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="f1f5b-127">相关内容</span><span class="sxs-lookup"><span data-stu-id="f1f5b-127">Related Content</span></span>  
 <span data-ttu-id="f1f5b-128">blogs.msdn.com 上的博客文章 [SSIS 与 AlwaysOn 一起使用](https://go.microsoft.com/fwlink/?LinkId=255873)。</span><span class="sxs-lookup"><span data-stu-id="f1f5b-128">Blog entry, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
  
